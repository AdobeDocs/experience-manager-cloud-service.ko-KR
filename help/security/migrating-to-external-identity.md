---
title: 외부 ID 및 동적 그룹 멤버십으로 마이그레이션
description: AEM as a Cloud Service에서 로컬 사용자 및 그룹을 동적 그룹 멤버십이 있는 외부 ID 모델로 마이그레이션하기 위한 기술 안내서
solution: Experience Manager Sites
feature: Security
role: Developer, Admin
source-git-commit: bb4b60523f60b1285c5f2fd2e49f6cc8cff24324
workflow-type: tm+mt
source-wordcount: '2232'
ht-degree: 1%

---

# 외부 ID 및 동적 그룹 멤버십으로 마이그레이션 {#migrating-to-external-identity}

## 개요 {#overview}

AEM as a Cloud Service에서 [데이터 동기화](/help/sites-cloud/authoring/personalization/user-and-group-sync-for-publish-tier.md#data-synchronization)를 사용하도록 설정하면 SAML 인증 처리기가 사용자 및 그룹 생성을 관리할 때 동적 그룹 구성원이 있는 외부 ID로 자동으로 마이그레이션되도록 구성할 수 있습니다. 프로젝트에서 사용자 지정 코드를 사용하여 사용자 또는 그룹을 만드는 경우 로컬 사용자 및 그룹이 아닌 외부 사용자 및 그룹을 만들도록 업데이트해야 합니다.

### 외부 사용자 및 그룹이 필요한 이유 {#why-external-required}

동적 그룹 멤버십을 사용하여 로컬 사용자 및 그룹에서 외부 ID로 마이그레이션하는 것은 다음과 같은 몇 가지 중요한 이유에 따라 중요합니다.

**성능 최적화:**

* **저장소 쓰기 감소**: 기존 로컬 그룹 구성원 자격을 사용하려면 그룹 노드의 단일 다중 값 속성에서 저장소에 대한 구성원 관계를 써야 합니다. 동적 그룹 멤버십을 사용하면 모든 그룹 주체가 포함된 단일 `rep:externalPrincipalNames` 속성이 있으므로 그룹 노드를 동기화할 필요가 없습니다
* **빠른 동기화**: 게시 계층 노드에서 사용자를 동기화할 때 동적 그룹 구성원이 있는 외부 사용자는 기존 그룹 구성원이 있는 로컬 사용자에 비해 데이터 전송 및 쓰기 작업이 크게 적게 필요합니다
* **확장성**: 사용자 및 그룹 수가 많은 시스템은 저장소 오버헤드가 크게 줄어듭니다. 동적 그룹 멤버십은 매우 큰 그룹에서도 효율적으로 확장됩니다.

이 문서에서는 다음에 대한 기술 지침을 제공합니다.

* 외부 ID 모델 이해
* 사용자 지정 코드를 수정하여 외부 사용자 및 그룹 만들기
* 기존 로컬 사용자 및 그룹을 외부 ID 모델로 마이그레이션

## 외부 ID 이해 {#understanding-external-identity}

### 외부 사용자 {#external-users}

외부 사용자는 외부 ID 공급자에 연결된 `rep:externalId` 속성으로 식별됩니다. 형식은 다음과 같습니다.

```
userId;idpName
```

예: `john.doe;saml-idp`.

>[!NOTE]
>
> `idpName`은(는) 인증 처리기 구성에 정의된 Oak Identity Provider(Idp)의 이름을 나타냅니다. SAML 통합의 경우 SAML 인증 처리기의 `idpIdentifier` 특성에 설정된 값입니다.

**키 속성:**

* `rep:externalId`: 사용자를 외부로 표시하는 필수 속성(예: `john.doe;saml-idp`)
* `rep:externalPrincipalNames`: 동적 멤버십에 대한 외부 그룹 주체가 포함된 다중 값 속성
* `rep:lastSynced`: 마지막 동기화 타임스탬프
* `rep:lastDynamicSync`: 마지막 동적 그룹 구성원 동기화의 타임스탬프

### 외부 그룹 {#external-groups}

외부 그룹도 `rep:externalId` 속성으로 식별되며 사용자 이름 형식을 사용합니다.

```
groupId;idpName
```

예를 들어`content-authors;saml-idp`

### 동적 그룹 멤버십 {#dynamic-group-membership}

동적 그룹 멤버십은 저장소에 저장된 직접적인 사용자-그룹 관계 대신 사용자 노드의 `rep:externalPrincipalNames` 속성을 사용합니다. 사용자에게 외부 그룹의 ID와 일치하는 외부 사용자 이름이 있으면 자동으로 해당 그룹의 구성원이 됩니다. 자세한 내용은 [Apache Oak 설명서](https://jackrabbit.apache.org/oak/docs/security/authentication/external/dynamic.html)를 참조하십시오.

**이점:**

* 저장소 쓰기 감소(사용자를 그룹에서 추가/제거할 때 그룹 멤버십 노드가 수정되지 않음)
* 게시 계층 노드 간 동기화 속도 향상
* 확장 가능한 그룹 멤버십 관리
* 데이터 동기화 요구 사항과 호환

## 서비스 사용자 구성 {#service-user-configuration}

외부 사용자 및 그룹을 만들거나 수정하는 모든 작업은 **및** 속성에서 기본 보호를 무시하도록 올바르게 구성된 `rep:externalId`서비스 사용자`rep:externalPrincipalNames`를 사용하여 수행해야 합니다.

### 서비스 사용자가 필요한 이유 {#why-is-a-service-user-required}

기본적으로 Oak 보안은 일반 세션에서 다음과 같은 보호된 속성을 수정하지 못하도록 합니다.

* `rep:externalId` - 사용자/그룹을 외부로 표시합니다.
* `rep:externalPrincipalNames` - 동적 그룹 구성원 자격 주체를 저장합니다.

올바르게 구성된 서비스 사용자만 이러한 속성을 수정할 수 있습니다.

### 서비스 사용자 구성 및 매핑 {#service-user-configuration-mapping}

외부 ID를 관리하도록 서비스 사용자를 설정하려면 세 가지 조정된 구성이 필요합니다.

1. `repoinit`을(를) 통해 서비스 사용자 만들기
2. `ExternalPrincipal` 보호 구성
3. 서비스 사용자를 애플리케이션 번들에 매핑합니다.

이러한 단계에 대한 자세한 설명은 아래를 참조하십시오.

#### 1단계: Repoinit를 통해 서비스 사용자 만들기 {#create-the-serviice-user-via-repoinit}

이 단계에서는 `repoinit` 스크립트를 사용하여 필요한 권한을 가진 서비스 사용자를 만드는 방법에 대해 자세히 설명합니다.

**구성 파일:** `org.apache.sling.jcr.repoinit.RepositoryInitializer~group-provisioner.cfg.json`

**예제 위치:** `ui.config/src/main/content/jcr_root/apps/yourproject/osgiconfig/config.publish/`

```json
{
  "scripts": [
    "create service user group-provisioner with path system/yourproject",
    "set ACL for group-provisioner\n  allow jcr:read,jcr:readAccessControl,jcr:modifyAccessControl,rep:userManagement,rep:write on /home/users\n  allow jcr:read,jcr:readAccessControl,jcr:modifyAccessControl,rep:userManagement,rep:write on /home/groups\nend"
  ]
}
```

**권한 개요**

* `jcr:read`: 사용자 및 그룹 읽기
* `jcr:readAccessControl`: ACL 읽기
* `jcr:modifyAccessControl`: ACL 수정(속성 설정에 필요)
* `rep:userManagement`: 사용자/그룹 만들기 및 관리
* `rep:write`: `rep:externalId` 및 `rep:externalPrincipalNames`을(를) 포함하는 쓰기 속성

>[!NOTE]
>
>서비스 사용자를 다른 시스템 사용자와 구성할 수 있도록 `/home/users/system/yourproject` 아래에 서비스 사용자가 만들어집니다.

#### 2단계: ExternalPrincipal 보호 구성 {#configure-externalprincipal-protection}

다음은 외부 ID 속성에 적용되는 보호를 무시할 수 있도록 서비스 사용자를 화이트리스트에 추가하는 예제 구성입니다.

**구성 파일 이름:** `org.apache.jackrabbit.oak.spi.security.authentication.external.impl.principal.ExternalPrincipalConfiguration.cfg.json`

**예제 위치:** `ui.config/src/main/content/jcr_root/apps/yourproject/osgiconfig/config.publish/`

```json
{
  "protectExternalIdentities": "Warn",
  "systemPrincipalNames": [
    "group-provisioner",
    "saml-migration-service"
  ]
}
```

**구성 속성:**

* `protectExternalIdentities`: 외부 ID 속성에 대한 보호 수준을 제어합니다.
   * `"Strict"`: 화이트리스트에 있는 시스템 주체만 외부 속성을 수정할 수 있습니다. 프로덕션에 권장되는 수준입니다.
   * `"Warn"`: 경고를 기록하지만 수정할 수 있습니다. 개발/테스트에 유용합니다.
   * `"None"`: 보호가 없습니다. 권장되지 않음.
* `systemPrincipalNames`: `rep:externalId` 및 `rep:externalPrincipalNames`을(를) 수정할 수 있는 서비스 사용자 이름 목록입니다. 외부 ID(예: `group-provisioner`, `saml-migration-service`)를 관리해야 하는 모든 서비스 사용자를 포함하십시오.

>[!IMPORTANT]
>
>`systemPrincipalNames`의 서비스 사용자 이름은 repoinit 스크립트에서 만든 서비스 사용자 ID와 정확히 일치해야 합니다.

#### 3단계: 서비스 사용자 매핑 {#service-user-mapping}

코드에서 사용할 수 있도록 서비스 사용자를 애플리케이션 번들에 매핑합니다.

**구성 파일:** `org.apache.sling.serviceusermapping.impl.ServiceUserMapperImpl.amended~group-provisioner.cfg.json`

**위치:** `ui.config/src/main/content/jcr_root/apps/yourproject/osgiconfig/config.publish/`

```json
{
  "user.mapping": [
    "yourproject.core:group-provisioner=[group-provisioner]"
  ]
}
```

**매핑 형식:**

* `yourproject.core`: 기호 번들 이름(`pom.xml` `<Bundle-SymbolicName>`에 있음)
* `group-provisioner`(`=` 이전): 코드에서 사용할 하위 서비스 이름
* `[group-provisioner]`(`=` 이후): repoinit에서 만든 실제 서비스 사용자 ID

### 코드에서 서비스 사용자 사용 {#using-the-service-user-in-code}

세션을 열어 마이그레이션 또는 사용자/그룹 만들기 작업을 수행할 때는 서비스 사용자를 사용해야 합니다.

```java
import org.apache.sling.jcr.api.SlingRepository;

@Reference
private SlingRepository repository;

// Login as the service user
Session serviceSession = repository.loginService("group-provisioner", null);

try {
    UserManager userManager = ((JackrabbitSession) serviceSession).getUserManager();
    // Perform operations...
    serviceSession.save();
} finally {
    if (serviceSession != null && serviceSession.isLive()) {
        serviceSession.logout();
    }
}
```

>[!IMPORTANT]
>
>적절한 서비스 사용자 구성이 없으면 권한 오류가 발생하여 `rep:externalId` 또는 `rep:externalPrincipalNames` 설정 시도가 실패합니다. 마이그레이션을 시도하기 전에 서비스 사용자가 `ExternalPrincipal` 구성에서 올바르게 구성되었는지 확인하십시오.

## 전체 구성 예 {#complete-configuration-example}

세 가지 구성을 함께 보여주는 전체 작업 예는 아래에 나와 있습니다.

### 파일 구조 {#file-structure}

```
ui.config/src/main/content/jcr_root/apps/yourproject/osgiconfig/
└── config.publish/
    ├── org.apache.sling.jcr.repoinit.RepositoryInitializer~group-provisioner.cfg.json
    ├── org.apache.jackrabbit.oak.spi.security.authentication.external.impl.principal.ExternalPrincipalConfiguration.cfg.json
    └── org.apache.sling.serviceusermapping.impl.ServiceUserMapperImpl.amended~group-provisioner.cfg.json
```

### 사용자 지정 코드 수정 {#modifying-custom-code}

#### 외부 사용자 만들기 {#creating-external-users}

**이전(로컬 사용자):**

```java
UserManager userManager = ((JackrabbitSession) session).getUserManager();
User user = userManager.createUser(userId, password);
```

**후(외부 사용자):**

```java
import org.apache.jackrabbit.oak.spi.security.authentication.external.ExternalIdentityRef;

UserManager userManager = ((JackrabbitSession) session).getUserManager();
ValueFactory valueFactory = session.getValueFactory();

// Create user with principal
Principal userPrincipal = new Principal() {
    @Override
    public String getName() {
        return userId;
    }
};

User user = userManager.createUser(userId, null, userPrincipal, null);

// Set rep:externalId
ExternalIdentityRef externalRef = new ExternalIdentityRef(userId, idpName);
String externalId = externalRef.getString(); // Format: userId;idpName
user.setProperty("rep:externalId", valueFactory.createValue(externalId));

// Set sync timestamps to far future (workaround for OAK-12079)
// Set to 10 years in the future to prevent premature cleanup of external group memberships
// See: https://issues.apache.org/jira/browse/OAK-12079
java.util.Calendar future = java.util.Calendar.getInstance();
future.add(java.util.Calendar.YEAR, 10);
user.setProperty("rep:lastSynced", valueFactory.createValue(future));
user.setProperty("rep:lastDynamicSync", valueFactory.createValue(future));

session.save();
```

#### 외부 그룹 만들기 {#creating-external-groups}

**이전(로컬 그룹):**

```java
UserManager userManager = ((JackrabbitSession) session).getUserManager();
Group group = userManager.createGroup(groupId);
```

**후(외부 그룹):**

```java
import org.apache.jackrabbit.oak.spi.security.authentication.external.ExternalIdentityRef;

UserManager userManager = ((JackrabbitSession) session).getUserManager();
ValueFactory valueFactory = session.getValueFactory();

// Create group with principal
Principal groupPrincipal = new Principal() {
    @Override
    public String getName() {
        return groupId;
    }
};

Group group = userManager.createGroup(groupPrincipal);

// Set rep:externalId
ExternalIdentityRef externalRef = new ExternalIdentityRef(groupId, idpName);
String externalId = externalRef.getString(); // Format: groupId;idpName
group.setProperty("rep:externalId", valueFactory.createValue(externalId));

session.save();
```

#### 동적 그룹 멤버십 할당 {#assigning-dynamic-membership}

**이전(직접 멤버십):**

```java
Group group = (Group) userManager.getAuthorizable(groupId);
User user = (User) userManager.getAuthorizable(userId);
group.addMember(user);
```

**이후(동적 구성원):**

```java
User user = (User) userManager.getAuthorizable(userId);
ValueFactory valueFactory = session.getValueFactory();

// Get existing external principal names
Value[] existingValues = user.getProperty("rep:externalPrincipalNames");
List<String> principalNames = new ArrayList<>();

if (existingValues != null) {
    for (Value value : existingValues) {
        principalNames.add(value.getString());
    }
}

// Add new principal name (format: groupId;idpName)
String dynamicGroupPrincipal = groupId + ";" + idpName;
if (!principalNames.contains(dynamicGroupPrincipal)) {
    principalNames.add(dynamicGroupPrincipal);
    
    // Create new Value array
    Value[] newValues = new Value[principalNames.size()];
    for (int i = 0; i < principalNames.size(); i++) {
        newValues[i] = valueFactory.createValue(principalNames.get(i));
    }
    
    // Set the property
    user.setProperty("rep:externalPrincipalNames", newValues);
    
    // Update sync timestamps to far future (workaround for OAK-12079)
    // Set to 10 years in the future to prevent premature cleanup of external group memberships
    // See: https://issues.apache.org/jira/browse/OAK-12079
    java.util.Calendar future = java.util.Calendar.getInstance();
    future.add(java.util.Calendar.YEAR, 10);
    user.setProperty("rep:lastDynamicSync", valueFactory.createValue(future));
    user.setProperty("rep:lastSynced", valueFactory.createValue(future));
}

session.save();
```

## 마이그레이션 프로세스 {#migration-process}

데이터 동기화 서비스를 활성화하기 전에 사용자 지정 코드가 업데이트된 경우 기존 로컬 사용자 및 그룹을 외부 ID로 마이그레이션할 필요가 없습니다.

로컬 사용자 및 그룹이 저장소에서 이미 지속되고 환경이 활발히 사용되는 경우, 중단이나 불일치를 방지하기 위해 다음과 같이 다단계 마이그레이션을 수행하는 것이 좋습니다.

>[!IMPORTANT]
>
>`group-provisioner` 및 `rep:externalId` 속성에 대한 보호를 무시할 수 있는 권한이 부여된 올바르게 구성된 서비스 사용자(예: `rep:externalPrincipalNames`)를 사용하여 모든 마이그레이션 단계를 실행해야 합니다. 자세한 내용은 [서비스 사용자 구성](#service-user-configuration)을 참조하세요.

### 1단계: 외부 그룹 구조 만들기 {#step-1-create-external-group-structure}

마이그레이션해야 하는 각 로컬 그룹의 경우:

1. 사용자 이름이 `<localGroupId>;<idpName>`인 해당 외부 그룹을 만드십시오. 외부 그룹을 로컬 그룹과 연결하는 데 도움이 되는 명명 규칙 사용
1. 값이 `rep:externalId`인 외부 그룹의 `<localGroupId>;<idpName>` 속성을 설정합니다.
1. 외부 그룹을 원래 로컬 그룹의 멤버로 추가합니다.

**유효성 검사**

* 모든 로컬 그룹에 해당 외부 그룹이 있는지 확인하여 결과를 검증할 수 있습니다. 또한 모든 외부 그룹은 해당 로컬 그룹에 속합니다.

**예제 서블릿 끝점:**

```java
@SlingServletPaths("/bin/migration/step1")
public class MigrationStep1Servlet extends SlingAllMethodsServlet {
    
    @Override
    protected void doPost(SlingHttpServletRequest request, 
                          SlingHttpServletResponse response) {
        String groupPath = request.getParameter("groupPath");
        String idpName = request.getParameter("idpName");

        // Check if the caller is authorized to run the servlet
        isAuthorizedCaller(request, response);

        // Get local group
        Authorizable localGroupAuth = userManager.getAuthorizableByPath(groupPath);
        Group localGroup = (Group) localGroupAuth;
        String localGroupId = localGroup.getID();
        
        // Create external group
        String externalGroupPrincipalName = localGroupId + ";" + idpName;
        // The function createExternalGroup performs the following steps:
        // 1. Creates a new external group with the given principal name (format: "<localGroupId>;<idpName>").
        // 2. Sets the 'rep:externalId' property on the group to mark it as an external group (value: "<localGroupId>;<idpName>").
        // 3. Sets the 'rep:principalName' property for the group if required.
        // 4. Assigns any other required group metadata, such as a title or description, if needed.
        // 5. Persists the new group node in the repository at the appropriate path under /home/groups.
        // 6. Returns the created Group object so it can be used for further operations, such as membership assignment.
        Group externalGroup = createExternalGroup(externalGroupPrincipalName, localGroupId, idpName);
        
        // Add external group to local group
        localGroup.addMember(externalGroup);
        
        session.save();
    }
}
```

**사용량:**

```bash
curl -X POST "http://localhost:4503/bin/migration/step1?groupPath=/home/groups/c/content-authors&idpName=saml-idp"
```

### 2단계: 사용자 전환 및 동적 멤버십 할당 {#step-2-convert-users-and-assign-dynamic-membership}

로컬 그룹의 멤버인 각 사용자에 대해 다음을 수행합니다.

1. `rep:externalId`집합이 있는지 확인합니다(필요한 경우 외부 사용자로 전환).
1. 각 그룹 구성원에 대해 해당 외부 그룹 주체를 `rep:externalPrincipalNames`에 추가하십시오.
1. 동기화 타임스탬프를 업데이트합니다.

>[!IMPORTANT]
>
>이 프로세스 중에 &quot;모든 사용자&quot;와 같은 시스템 그룹을 건너뜁니다.

**예제 서블릿 끝점:**

```java
@SlingServletPaths("/bin/migration/step2")
public class MigrationStep2Servlet extends SlingAllMethodsServlet {
    
    @Override
    protected void doPost(SlingHttpServletRequest request, 
                          SlingHttpServletResponse response) {
        String userId = request.getParameter("userId");
        String idpName = request.getParameter("idpName");
        
        // Check if the caller is authorized to run the servlet
        isAuthorizedCaller(request, response);

        // Login as the service user
        Session serviceSession = repository.loginService("group-provisioner", null);

        try {
            UserManager userManager = ((JackrabbitSession) serviceSession).getUserManager();
            User user = (User) userManager.getAuthorizable(userId);
            
            // Ensure user has rep:externalId
            Value[] externalIdValues = user.getProperty("rep:externalId");
            if (externalIdValues == null || externalIdValues.length == 0) {
                ExternalIdentityRef externalRef = new ExternalIdentityRef(userId, idpName);
                user.setProperty("rep:externalId", 
                            valueFactory.createValue(externalRef.getString()));
            }
            
            // Get all group memberships
            Iterator<Group> groupIterator = user.declaredMemberOf();
            List<String> principalNames = new ArrayList<>();
            
            while (groupIterator.hasNext()) {
                Group group = groupIterator.next();
                String groupId = group.getID();
                
                // Skip system groups
                if ("everyone".equals(groupId)) {
                    continue;
                }
                
                // Add dynamic group principal
                String dynamicGroupPrincipal = groupId + ";" + idpName;
                principalNames.add(dynamicGroupPrincipal);
            }
            
            // Set rep:externalPrincipalNames
            if (!principalNames.isEmpty()) {
                Value[] newValues = new Value[principalNames.size()];
                for (int i = 0; i < principalNames.size(); i++) {
                    newValues[i] = valueFactory.createValue(principalNames.get(i));
                }
                user.setProperty("rep:externalPrincipalNames", newValues);
            }
            
            // Update timestamps to far future (workaround for OAK-12079)
            // Set to 10 years in the future to prevent premature cleanup of external group memberships
            // See: https://issues.apache.org/jira/browse/OAK-12079
            java.util.Calendar future = java.util.Calendar.getInstance();
            future.add(java.util.Calendar.YEAR, 10);
            user.setProperty("rep:lastDynamicSync", valueFactory.createValue(future));
            user.setProperty("rep:lastSynced", valueFactory.createValue(future));
        
        // Perform operations...
        serviceSession.save();
    } finally {
        if (serviceSession != null && serviceSession.isLive()) {
            serviceSession.logout();
        }
}    }
}
```

**사용량:**

```bash
curl -X POST "http://localhost:4503/bin/migration/step2?userId=john.doe&idpName=saml-idp"
```

**유효성 검사**

모든 사용자가 모든 외부 그룹의 `rep:externalId`을(를) 가진 `rep:externalPrincipalName` 및 `principalName` 특성을 가지고 있는지 확인하여 유효성을 검사할 수 있습니다. 사용자가 외부 그룹의 로컬 그룹 *및*&#x200B;에 속해 있습니다.

### 3단계: 직접 사용자 멤버십 제거 {#step-3-remove-direct-user-memberships}

사용자에게 동적 그룹 멤버십이 구성된 후:

1. 로컬 그룹에서 직접 사용자 멤버십 제거
1. 그룹 간 멤버십(외부 그룹 멤버십 포함) 유지

**예제 서블릿 끝점:**

```java
@SlingServletPaths("/bin/migration/step3")
public class MigrationStep3Servlet extends SlingAllMethodsServlet {
    
    @Override
    protected void doPost(SlingHttpServletRequest request, 
                          SlingHttpServletResponse response) {

        // Check if the caller is authorized to run the servlet
        isAuthorizedCaller(request, response);

        String groupPath = request.getParameter("groupPath");
        
        Authorizable localGroupAuth = userManager.getAuthorizableByPath(groupPath);
        Group localGroup = (Group) localGroupAuth;
        
        // Process each member
        Iterator<Authorizable> members = localGroup.getDeclaredMembers();
        
        while (members.hasNext()) {
            Authorizable member = members.next();
            
            // Remove only user members, keep group members
            if (!member.isGroup()) {
                localGroup.removeMember(member);
            }
        }
        
        session.save();
    }
}
```

**사용량:**

```bash
curl -X POST "http://localhost:4503/bin/migration/step3?groupPath=/home/groups/c/content-authors"
```

**유효성 검사**

* 모든 로컬 그룹에 해당 외부 그룹만 포함되어 있는지 또는 다른 그룹만 멤버로 포함되어 있는지 확인하여 이를 확인할 수 있습니다.


## 마이그레이션 워크플로 {#migration-workflow}

### 마이그레이션 전 검사 목록 {#pre-migration-checklist}

* [ ] **서비스 사용자 구성**: 적절한 사용 권한을 가진 서비스 사용자(예: `group-provisioner`)를 만들고 구성합니다
* [ ] **ExternalPrincipal 구성 확인**: 서비스 사용자가 `rep:externalId` 및 `rep:externalPrincipalNames`에서 보호를 무시하도록 구성되었는지 확인하십시오.
* [ ] **서비스 사용자 권한 테스트**: 서비스 사용자가 개발에서 외부 ID 속성을 설정할 수 있는지 확인하십시오.
* [ ] 사용자 또는 그룹을 만드는 모든 사용자 지정 코드를 식별합니다
* [ ] 외부 ID 모델을 사용하도록 사용자 지정 코드를 검토하고 업데이트합니다.
* [ ] 테스트 업데이트 코드를 개발 환경에서
* [ ] 마이그레이션할 기존의 모든 로컬 사용자 및 그룹 인벤토리
* [ 하위 환경의 ] 마이그레이션 프로세스 테스트

### 실행 단계 {#execution-steps}

1. **업데이트된 코드 배포**: 사용자 지정 코드 변경 내용을 배포하여 외부 사용자/그룹을 만듭니다.

1. **외부 그룹 만들기**(각 로컬 그룹에 대해):

   ```bash
   curl -X POST "http://localhost:4503/bin/migration/step1?groupPath=/home/groups/g/my-group&idpName=saml-idp"
   ```

1. **사용자 마이그레이션**(각 사용자에 대해):

   ```bash
   curl -X POST "http://localhost:4503/bin/migration/step2?userId=username&idpName=saml-idp"
   ```

1. **정리**(마이그레이션된 각 그룹의 경우):

   ```bash
   curl -X POST "http://localhost:4503/bin/migration/step3?groupPath=/home/groups/g/my-group"
   ```

1. **확인**: 사용자 그룹 멤버십을 확인하고 액세스 권한을 테스트하십시오.

1. **데이터 동기화 활성화**: 기능을 활성화하려면 고객 지원 센터에 문의하십시오

### 마이그레이션 후 유효성 검사 {#post-migration-validation}

마이그레이션 확인:

1. **사용자 속성 확인**:

   사용자 노드에서 다음 항목이 있는지 확인합니다.

   * `rep:externalId`: 형식은 `userId;idpName`이어야 합니다.
   * `rep:externalPrincipalNames`: `groupId;idpName` 형식의 그룹 보안 주체 배열
   * `rep:lastSynced`: 타임스탬프가 먼 미래(마이그레이션 날짜로부터 약 10년)로 설정됨
   * `rep:lastDynamicSync`: 타임스탬프가 먼 미래(마이그레이션 날짜로부터 약 10년)로 설정됨

   **참고**: 타임스탬프는 OAK-12079에 대한 해결 방법으로 의도적으로 먼 미래 날짜로 설정됩니다. 이는 예상된 비헤이비어입니다.

1. **그룹 속성 확인**:

   로컬 그룹 노드에서 다음을 확인합니다.

   * `groupId;idpName` 형식의 외부 그룹 구성원
   * 직접 사용자 구성원 없음(3단계 이후에만)

1. **사용자 로그인 테스트**: 사용자가 로그인할 수 있고 올바른 사용 권한이 있는지 확인하십시오.

1. **액세스 제어 테스트**: 사용자가 CUG/ACL로 보호된 콘텐츠에 액세스할 수 있는지 확인

## 문제 해결 {#troubleshooting}

### 일반 문제 {#common-issues}

**문제: `rep:externalId` 또는`rep:externalPrincipalNames`**&#x200B;을(를) 설정할 때 권한 오류 발생

**오류 메시지:**

* `javax.jcr.AccessDeniedException: Access denied`
* `OakAccess0000: Access denied`
* `Cannot set property 'rep:externalId'`

**솔루션**: 외부 ID 속성에 대한 보호를 무시할 수 있는 권한이 부여된 올바르게 구성된 서비스 사용자를 사용하여 세션을 열어야 합니다.

**해결 단계:**

1. **서비스 사용자가 있는지 확인**: repoinit를 통해 서비스 사용자(예: `group-provisioner`)가 만들어졌는지 확인
1. **서비스 사용자 매핑 확인**: 서블릿 또는 서비스가 `repository.loginService("group-provisioner", null)`을(를) 사용하고 있는지 확인
1. **ExternalPrincipal 구성 확인**: `org.apache.jackrabbit.oak.spi.security.authentication.external.impl.principal.ExternalPrincipalConfiguration`이(가) 올바르게 구성되었는지 확인
1. **서비스 사용자 권한 확인**: 서비스 사용자에게 `rep:write` 및 `rep:userManagement`에 대한 `/home/users` 및 `/home/groups` 권한이 필요합니다.

전체 설치 지침은 [서비스 사용자 구성](#service-user-configuration)을 참조하세요.

**문제:`OakConstraint0072: Property 'rep:externalPrincipalNames' requires 'rep:externalId' to be present`**

**솔루션**: `rep:externalId`을(를) 설정하기 전에 사용자에게 `rep:externalPrincipalNames`을(를) 설정해야 합니다. 먼저 2단계에서 사용자를 외부 사용자로 변환해야 합니다.

**문제: 사용자가 마이그레이션 후 그룹 멤버십을 잃음**

**솔루션**: 다음을 확인하십시오.

* 올바른 사용자 이름 형식(`groupId;idpName`)으로 외부 그룹을 만들었습니다.
* 외부 그룹이 로컬 그룹의 구성원으로 추가되었습니다(1단계).
* 사용자가 `rep:externalPrincipalNames`에서 올바른 외부 사용자 이름을 가지고 있습니다(2단계).
* 3단계 정리는 1단계와 2단계가 완료된 후에만 수행되었다

**문제: 사용자 로그인 후 외부 그룹 멤버십이 예기치 않게 제거됩니다(OAK-12079)**

**문제**: Oak 버그 [OAK-12079](https://issues.apache.org/jira/browse/OAK-12079)&#x200B;(으)로 인해 Oak 동기화 메커니즘이 `rep:lastSynced` 및 `rep:lastDynamicSync` 타임스탬프를 기반으로 외부 그룹 멤버십을 조기에 정리할 수 있습니다.

**솔루션**: `rep:lastSynced` 및 `rep:lastDynamicSync` 타임스탬프를 현재 시간 대신 먼 미래 날짜(지금부터 10년 후)로 설정합니다. 이렇게 하면 동기화 정리 프로세스에서 외부 그룹 멤버십을 제거할 수 없습니다.

**구현:**

```java
// Workaround for OAK-12079
// Set to 10 years in the future to prevent premature cleanup
// See: https://issues.apache.org/jira/browse/OAK-12079
java.util.Calendar future = java.util.Calendar.getInstance();
future.add(java.util.Calendar.YEAR, 10);
user.setProperty("rep:lastSynced", valueFactory.createValue(future));
user.setProperty("rep:lastDynamicSync", valueFactory.createValue(future));
```

**작동 이유**: Oak 동기화 논리는 타임스탬프를 먼 미래 날짜로 설정함으로써 이러한 사용자를 &quot;최근에 동기화됨&quot;으로 취급하고 외부 사용자 이름 및 그룹 멤버십을 제거하는 정리 프로세스를 트리거하지 않습니다.

**참고**: 향후 Oak 릴리스에서 OAK-12079이 해결될 때까지 일시적으로 해결 가능한 해결 방법입니다. 이 문서의 모든 코드 예제에는 이미 이 해결 방법이 포함되어 있습니다.

**문제: 시스템 그룹 &quot;everyone&quot;에서 오류가 발생합니다**

**솔루션**: 사용자 마이그레이션 중에 항상 &quot;모든 사용자&quot; 시스템 그룹을 건너뜁니다(2단계). 이 그룹은 AEM에서 자동으로 관리합니다.

### 롤백 프로시저 {#rollback-procedure}

마이그레이션에 문제가 발생하는 경우:

1. 마이그레이션 프로세스 중지
1. 중요한 데이터가 영향을 받은 경우 백업에서 복원
1. 코드에서 변경 사항을 롤백하여 동적 그룹 멤버십이 있는 외부 사용자 및 그룹을 생성합니다.
1. 마이그레이션을 다시 시도하기 전에 문제를 검토하고 수정하십시오.

## 모범 사례 {#best-practices}

* **철저하게 테스트**: 프로덕션 전에 개발 및 스테이징 환경에서 항상 마이그레이션을 테스트하십시오.
* **일괄 처리**: 대규모 사용자 기준의 경우 시간 초과 문제를 방지하기 위해 마이그레이션을 일괄로 처리하십시오
* **성능 모니터링**: 마이그레이션하는 동안 리포지토리 성능을 확인하십시오.
* **감사 추적 유지**: 문제 해결을 위한 모든 마이그레이션 작업을 기록하십시오.
* **서비스 사용자 권한**: 마이그레이션 서블릿에서 필요한 권한이 있는 적절한 서비스 사용자를 사용하도록 하십시오. `rep:externalId` 및 `rep:externalPrincipalNames` 속성에 대한 보호를 무시하려면 ExternalPrincipal 구성에서 서비스 사용자를 구성해야 합니다.
* **Idempotent 작업**: 마이그레이션 코드를 안전하게 다시 실행할 수 있도록 디자인합니다.
* **각 단계에서 유효성 검사**: 계속하기 전에 각 마이그레이션 단계 후 결과를 확인하십시오.

## 마이그레이션 서블릿 보호 {#securing-migration-servlets}

마이그레이션 서블릿에는 사용자 및 그룹을 만들고 수정할 수 있는 높은 권한이 있습니다. 무단 액세스를 방지하기 위해 이러한 엔드포인트에 대한 액세스를 제한하는 것이 중요합니다.

### 권장 방법: IMS 기술 계정 인증 {#recommended-approach-ims-technical-account}

권장 접근 방법은 Adobe IMS 통합을 사용하여 이러한 서블릿을 보호하여 승인된 기술 계정만 액세스할 수 있도록 하는 것입니다.

#### 1단계: AEM Developer Console에서 기술 계정 만들기 {#create-a-technical-account-in-aem-developer-console}

1. [Experience Manager](https://experience.adobe.com/)&#x200B;(으)로 이동한 다음 **Cloud Manager**
1. 프로그램을 선택한 다음 기술 계정을 만들 환경을 클릭합니다
1. 환경의 줄임표 메뉴에서 **Developer Console**&#x200B;를 클릭합니다
1. AEM Developer Console에서 **통합** 탭으로 이동합니다.
1. **새 기술 계정 만들기**&#x200B;를 클릭합니다
1. 통합의 이름(예: &quot;마이그레이션 서비스 계정&quot;)을 제공합니다.
1. **만들기**&#x200B;를 클릭합니다.
1. 생성된 통합에서 다음 값을 확인합니다.
   * **클라이언트 ID**
   * **클라이언트 암호**
   * **기술 계정 ID**(서블릿에 액세스하는 사용자 ID - 형식: `XXXXXXXXXXXXXXXXXXXXXXXX@techacct.adobe.com`)

자세한 지침은 [서버측 API에 대한 액세스 토큰 생성](/help/implementing/developing/introduction/generating-access-tokens-for-server-side-apis.md)을 참조하십시오.

호출자가 인증되었는지 확인하는 샘플 코드:

```
    private boolean isAuthorizedCaller(SlingHttpServletRequest request, 
                                       SlingHttpServletResponse response) {

        Session session = request.getResourceResolver().adaptTo(Session.class);
        String callerId = session != null ? session.getUserID() : null;
               
        if (!ALLOWED_TECHNICAL_ACCOUNT.equals(callerId)) {
            LOG.warn("Unauthorized access attempt by user: '{}' (expected: '{}')", callerId,   ALLOWED_TECHNICAL_ACCOUNT);
            response.setStatus(SlingHttpServletResponse.SC_FORBIDDEN);
            return false;
        }
        
        return true;
    }
```

### 심층 방어: IP 기반 제한 사항 {#defense-in-depth-ip-based-restrictions}

추가적인 보안 계층으로 IP 주소로 마이그레이션 종단점에 대한 액세스를 제한하도록 CDN 규칙을 구성할 수 있습니다. 이 기능은 알려진 인프라에서 마이그레이션을 실행할 때 유용합니다.

>[!NOTE]
>
>IP 제한만으로는 충분하지 않습니다. 위에서 설명한 대로 항상 인증 확인과 결합하십시오.

### 보안 체크리스트 {#security-checklist}

프로덕션에 마이그레이션 서블릿을 배포하기 전:

* [ ] AEM Developer Console에서 IMS 통합 만들기
* [ ] 기술 계정 ID의 유효성을 검사하도록 서블릿 구성
* [ ] 개발/스테이징 환경에서 인증 흐름 테스트
* [ ] CDN 수준에서 추가 IP 기반 제한 고려
* [ ] 마이그레이션이 완료된 후 마이그레이션 서블릿을 비활성화하거나 제거할 계획입니다.
* [ ] 마이그레이션 끝점에 대한 모든 액세스 감사 및 로그

>[!IMPORTANT]
>
>마이그레이션이 완료되면 잠재적인 보안 위험을 제거하기 위해 배포에서 마이그레이션 서블릿을 비활성화하거나 제거하는 것이 좋습니다.

## 추가 리소스 {#additional-resources}

* [게시 계층에 대한 사용자 및 그룹 동기화](/help/sites-cloud/authoring/personalization/user-and-group-sync-for-publish-tier.md)
* [SAML 2.0 인증 처리기](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/authentication/saml-2-0.html)
* [외부 Id 공급자](https://jackrabbit.apache.org/oak/docs/security/authentication/externalloginmodule.html)
* [동적 그룹 구성원](https://jackrabbit.apache.org/oak/docs/security/authentication/external/dynamic.html)
