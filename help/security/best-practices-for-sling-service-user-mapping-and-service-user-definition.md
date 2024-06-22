---
title: Sling 서비스 사용자 매핑 및 서비스 사용자 정의의 모범 사례
description: Sling 서비스 사용자 매핑 및 서비스 사용자 정의의 모범 사례에 대해 알아봅니다.
exl-id: 72f0dcbf-b4e6-4a73-8232-3574a212ac19
feature: Security
role: Admin
source-git-commit: f28f212574dda0ece2cedb56a714d381e5bd7d3c
workflow-type: tm+mt
source-wordcount: '1884'
ht-degree: 99%

---

# Sling 서비스 사용자 매핑 및 서비스 사용자 정의의 모범 사례 {#best-practices-for-sling-service-user-mapping-and-service-user-definition}

## 서비스 사용자 매핑 {#service-user-mapping}

서비스의 매핑을 해당 시스템 사용자에게 추가하려면 `ServiceUserMapper` 서비스에 대한 공장 구성을 만들어야 합니다. 이 모듈식을 유지하기 위해 Sling “수정” 메커니즘을 사용하여 이러한 구성을 제공할 수 있습니다(자세한 내용은 [SLING-3578](https://issues.apache.org/jira/browse/SLING-3578) 참조). 번들과 함께 이러한 구성을 설치하는 권장 방법은 다음 예에 설명된 대로 빠른 시작 프로비저닝 모델에 추가하는 것입니다.

```
org.apache.sling.serviceusermapping.impl.ServiceUserMapperImpl.amended-my-mapping
    user.default=""
    user.mapping=[
        "com.adobe.cq.my-bundle:my-subservice\=[content-writer-service]",
        "com.adobe.cq.my-bundle:my-subservice-different-task\="[myfeature-configuration-writer-service,content-reader-service]"
    ]
```

### 매핑 형식 {#mapping-format}

AEM 6.4부터 매핑 형식은 다음과 같이 정의됩니다.

>[!NOTE]
>
>`userName`은 삭제되었으므로 더 이상 사용해서는 안 됩니다.

```
bundleId [:subserviceName] = userName | [principalNames]   
```

`bundleId` 및 `subserviceName`은 서비스를 식별하고, `userName/principalNames`는 서비스 사용자를 식별하며, `principalNames`는 쉼표로 구분된 목록입니다.

또한 `principalNames`는 기본적으로 ID와 동일한 서비스 사용자 주체 이름 목록입니다.


**우수 사례**

* 작업별 하위 서비스 이름 - 번들의 서비스가 다른 작업을 수행하는 경우 `subserviceNames`를 식별하여 작업별로 그룹화하는 것이 좋습니다.
* 특정 서비스가 다양한 작업(예: `/var` 하위 트리 아래의 자산 콘텐츠 읽기 및 정보 업데이트)을 수행하는 경우, 기능별 `assetreport-writer-service`로 공통 `dam-reader-service`를 집계하는 등 개별 작업을 반영하는 다양한 서비스 주체를 집계하여 이를 반영하는 것이 좋습니다.
* 각 서비스를 매우 구체적이고 제한된 작업 집합에 바인딩하는 것이 이상적입니다.
* `[one,or,multiple,principalNames]`를 사용한 새로운 형식은 AEM 6.4부터 서비스 사용자 매핑을 정의하는 데 권장되는 방법입니다.

다음은 형식을 변경하는 이유와 Adobe에서 단일 사용자 ID에 대해서만 버전 매핑 대신 형식을 사용하도록 권장하는 이유의 목록입니다.

* 고객의 특별한 요구와 공통 작업을 결합하여 서비스 사용자 재사용 가능
* 권한 설정 중복 방지
* 특정 서비스가 실제로 수행하는 유효 권한(및 작업)을 더 효과적으로 이해
* 서비스 사용자의 명시적인 그룹 멤버십이 필요하지 않음. 그룹 멤버십의 경우 그룹 권한이 변경되면 까다로운 부작용이 발생할 수 있음
* 성능 개선 및 확장성

## 매핑 결정 및 서비스 로그인 {#mapping-resolution-and-service-login}

### 서비스 매핑 결정 {#service-mapping-resolution}

아래에 설명된 서비스 매핑을 해결하기 위한 호출 시퀀스는 다음과 같습니다.

1. 주어진 `bundleId` 및 `subserviceName`에 대한 활성 `principalNames` 매핑 검색
1. `bundleId` 및 null `subserviceName`에 대한 `principalNames` 매핑
1. `bundleId` 및 `subserviceName`에 대한 `userName` 매핑
1. `bundleId` 및 null `subserviceName`에 대한 `userName` 매핑
1. 기본 매핑
1. 기본 사용자

### SlingRepository - 서비스 로그인 {#slingrepository-servicelogin}

서비스 `Session/ResourceResolver`를 받는 시퀀스는 다음과 같이 작동합니다.

1. 아래 설명에 따라 `ServiceUserMapper` => pre-auth 저장소 로그인에서 주체 이름을 가져옵니다.
1. `ServiceUserMapper`에서 사용자 ID를 가져옵니다.
1. 현재 사용자 ID에 대해 더 이상 사용되지 않는 1ServiceUserConfiguration`을 확인합니다.
1. 사용자 ID를 사용하여 기본 Sling 서비스 로그인을 수행합니다(예: 서비스 사용자 ID의 `createAdministrativeSession` 및 가장 시퀀스).

주체 이름을 사용한 새로운 매핑을 통해 다음과 같은 단순화된 저장소 로그인이 생성됩니다.

* 주체 이름 세트는 `Subject`를 채우는 데 사용되는 유효한 주체로 처리됩니다.
* 결과적으로 저장소 로그인이 사전 인증될 수 있습니다.
* 그룹 멤버십 결정이 없습니다.

  >[!NOTE]
  >
  >서비스 사용자에 대해 필요한 모든 권한을 선언해야 합니다. &#39;모든 사람&#39; 및 기타 그룹 권한은 더 이상 상속되지 않습니다.

* service-`Session/ResourceResolver`를 만들기 위해 추가로 관리자 로그인을 할 필요가 없습니다.

### 더 이상 사용되지 않는 ServiceUserConfiguration {#deprecated-serviceUserConfiguration}

매핑에서 단일 사용자 이름을 지정하는 것은 기존 `ServiceUserConfiguration.simpleSubjectPopulation`과 동일합니다. 새로운 형식을 사용하면 `ServiceUserConfiguration`으로 제공되는 해결 방법을 서비스 사용자 매핑에 직접 반영할 수 있습니다. `ServiceUserConfiguration`은 AEM에서 더 이상 사용되지 않으며 모든 기존 사용법이 대체되었습니다.

## 서비스 사용자 {#service-users}

### 기존 서비스 사용자 재사용 {#reusing-existing-service-users}

다음 조건이 충족되면 기존 서비스 사용자를 재사용하는 것이 좋습니다.

* 요구 사항이 기존 서비스 사용자의 의도와 일치합니다.
* 서비스에서 기존 일반 서비스 사용자가 담당하는 일반 작업을 수행해야 합니다. 이 경우 중복 생성보다는 서비스 사용자를 재사용할 것을 권장합니다.
* 서비스에 기존 서비스 사용자가 담당하는 특정 작업이 필요합니다. 이에 대해 확실하지 않은 경우 해당 기능을 담당하는 기능 팀에 문의하십시오.

다음과 같은 경우 기존 서비스 사용자를 재사용하지 마십시오.

* 서비스가 작동하게 하려면 관련 없는 방식으로 서비스의 권한을 수정해야 합니다.
* 서비스에서 제공되는 권한의 작은 하위 집합만 필요하며, 재사용하는 이유가 서비스 사용자가 실제 일치하기 때문이 아니라 기능이 작동하게 하기 위함입니다.
* 이름이 나타내는 의도가 필요한 바와 완전히 다릅니다. 단순히 작동 가능하다는 이유로 선택하면 특정 서비스를 소유한 기능 팀이 권한을 변경하고 기능을 중단할 수 있으므로 문제가 발생할 수 있습니다.

### 서비스 사용자 만들기 {#creating-a-service-user}

AEM의 기존 서비스 사용자가 사용 사례에 적용 가능하지 않고 해당 RTC 문제가 승인되었음을 확인했으면 계속해서 기본 콘텐츠에 새 사용자를 추가할 수 있습니다. 확장된 보안 팀의 멤버가 RTC 투표에 참여하는 것이 이상적인 만큼, 적절한 관련자들도 관여하도록 하십시오.

**명명 규칙**

AEM 보안 팀은 서비스 사용자가 새로운 서비스 사용자에게 일관성을 더하고 가독성과 유지 관리성을 향상할 수 있도록 다음과 같은 명명 규칙을 정의했습니다.

서비스 사용자 이름은 대시(**&#39;-&#39;**)로 구분된 3개의 요소로 구성됩니다.

1. 서비스 작업의 대상이 되는 논리적 엔티티/기능(변경 가능성이 있는 경로 요소 방지)
1. 서비스가 수행할 작업
1. 사용자가 서비스 사용자인지 ID와 주체 이름으로 쉽게 식별할 수 있도록 하는 후행 **&#39;service&#39;**

**모범 사례**

* 서로 다른 엔티티/기능을 혼합하지 않습니다. 서비스에 다른 요구 사항이 있는 경우 개별 서비스 사용자로 분할하고 매핑에서 집계합니다.
* 서비스 사용자당 하나의 잘 정의된 작업으로 제한합니다. 너무 많거나 관련 없는 권한을 부여하게 되는 경우 분할합니다.
* 시간을 투자하여 서비스의 실제 필요성을 파악합니다.
* 시간을 투자하여 적절하고 의미 있으며 바로 이해 가능한 서비스 사용자 이름을 모색합니다.
* 피드백 및 검토를 요청합니다. 기능에 익숙하지 않은 개발자도 그 의도를 읽고 이해할 수 있어야 합니다. 이러한 개발자가 향후에 기능을 수정하거나 유지 관리하는 임무를 담당하게 될 수 있습니다.

결과적으로 서비스 사용자 이름에는 다음이 담겨 있어야 합니다.

* 사용 목적 및 재사용 가능 여부:

   * 매우 일반적인 이름: `content-writer-service`. 서비스에서 모든 콘텐츠를 읽을 수 있어야 하는 경우 집계에서 재사용해도 안전합니다.
   * 매우 구체적인 이름: `asset-linkshare-service`. 서비스에서 실제로 자산의 링크 공유를 수행하지 않는 한 재사용하기에 안전하지 않습니다.

* 기능 세트 및 권한 설정의 형태는 다음과 같습니다.

   * 논리적 엔티티가 권한 설정과 일치해야 합니다.

      * `content-foo-service`는 콘텐츠에 대한 작업에만 연결되어야 합니다. 여기에 구성이나 사용자와 같은 다른 엔티티에서 작동할 수 있는 권한을 부여해서는 안 됩니다.
      * `personalization-foo-service`와 같은 특정 서비스에는 특정 권한도 수반되어야 합니다. 모든 콘텐츠에 대한 권한을 부여하게 된다면 더 이상 구체적이지 않게 됩니다. 이를 이름에 반영하거나 집계에서 일반 사용자를 재사용하십시오.
      * `msm-xyz-service`와 같은 기능별 서비스에는 msm 관련 권한만 있어야 합니다. 커뮤니티 구성 관리 또는 사용자 화면 관리와 같은 관련 없는 기능으로 권한을 확장하지 마십시오.

   * 작업은 권한과 일치해야 합니다.

      * `foo-reader-service`는 일반 항목만 읽을 수 있어야 합니다. 쓰기 권한을 부여하지 마십시오.
      * `foo-writer-service`는 쓰기 작업을 수행할 것으로 예상할 수 있습니다. 그러나 액세스 제어 콘텐츠를 읽거나 수정할 수 있는 권한을 부여해서는 안 됩니다.
      * `foo-replicator-service`는 `crx:replicate`가 부여되었을 것으로 예상할 수 있습니다.

**예**

`configuration-reader-service`의 예:

* 이 이름은 DM 통합 구성과 같은 특정 기능의 구성이 아니라 일반적인 구성을 의미함을 나타냅니다. 그러한 통합의 구성을 읽는 것을 구체적인 목표로 하는 서비스 사용자의 이름은 `dmconfig-reader-service` 또는 `s7config-reader-service`와 같이 지정해야 합니다.

  >[!NOTE]
  >
  >명명에는 경로 정보가 포함되지 않습니다. 구성은 `/etc`에서 `/conf`로 이동되었습니다.

* task-element는 해당 사용자에게 바인딩된 서비스가 읽기 작업만 수행함을 나타냅니다.

`userproperties-copy-service`의 예:

* 이 서비스 사용자에게 바인딩된 서비스는 프로필이나 환경 설정과 같은 사용자/그룹 속성에서 작동합니다.
* 모든 종류의 쓰기 작업이 포함되는 `userproperties-writer-service`와 같은 이름과 달리, 해당 정보를 복사하는 것이 구체적인 목표입니다. 따라서 이러한 복사 작업에 대한 권한 설정은 한 위치에서 항목을 추가하고 다른 위치에서 항목을 제거하는 것만 허용할 수 있습니다.

**권한 설정에 대한 모범 사례**

* 서비스 사용자에 대해 항상 주체 기반 액세스 제어 설정을 사용합니다. 자세한 내용은 아래 예제를 참조하십시오.

   * Skyline에서 서비스 사용자 및 해당 권한을 변경할 수 없는 애플리케이션 콘텐츠로 표시하도록 허용합니다.
   * 경로와 트리 구조를 만들 필요는 없습니다.

* 권한을 부여하기만 하고 거부하지 않습니다.
* 권한을 제한합니다.

   * 필요한 최소한의 권한만 부여합니다.
   * 자세한 내용은 [항목에 권한 매핑](https://jackrabbit.apache.org/oak/docs/security/privilege/mappingtoitems.html) 및 [권한에 API 호출 매핑](https://jackrabbit.apache.org/oak/docs/security/privilege/mappingtoprivileges.html) 설명서를 참조하십시오.
   * `jcr:all`에 대한 권한을 부여하지 않습니다. 최소한도의 세트가 아닐 가능성이 높습니다.

* 범위를 축소합니다.

   * 기능별 하위 트리에 액세스 제어 정책을 배치합니다.
   * 배포된 항목의 경우: 제한을 사용하여 범위를 제한합니다(기본 제공 제한 목록은 [설명서](https://jackrabbit.apache.org/oak/docs/security/authorization/restriction.html) 참조).

* 일관성을 보장합니다.

   * 서비스 사용자 이름에 사용한 엔티티 및 작업과 일치하는 권한을 만듭니다.
   * 관련 없는 권한을 추가하지 않습니다. 예를 들어 `workflow-administration-service`에 `/home/users/screens`에서 사용자 관리 작업을 수행할 수 있는 권한을 부여하거나 s7-config를 읽도록 허용하는 것은 이상할 것입니다.

* 완전성을 유지합니다.

   * 서비스에 설계된 작업을 수행하는 데 필요한 모든 권한이 있도록 합니다. 서비스는 고객 환경에서도 즉시 작동해야 합니다.
   * 고객에게 권한 설정을 확장할 것을 기대하거나 요청하지 않습니다(예: 아래 `/apps`).

* 권한 설정 중복을 방지합니다.

   * 공통 서비스 사용자를 재사용합니다.
   * 추가로 필요한 특정 권한을 제공하는 기능별 서비스 사용자와 함께 집계합니다.

* 여러 기능에 걸쳐 권한 설정을 분할하지 않습니다. 그렇게 해야 한다는 것은 서비스 사용자가 효과적으로 정의되지 않았거나 수행하는 작업이 너무 많다는 의미입니다.
* 서비스 사용자를 그룹에 배치하지 않습니다. 이유는 다음과 같습니다.

   * 서비스 사용자의 구현 세부 정보가 &#39;공개&#39; 그룹과 섞입니다.
   * 권한 변경에 대한 통제력이 떨어집니다(회귀 및 권한 상승이 발생하기 쉬움).
   * 로그인 및 평가 성능에 문제가 생깁니다.
   * 주체 기반 ac-setup에서 작동하지 않습니다.

* 예측 가능한 경로가 없는 사용자 홈 노드(또는 그 안에 포함된 모든 하위 트리)에 대한 액세스는 홈(`userId`)을 사용하여 repo init에서 달성됩니다. 자세한 내용은 Sling repo init [설명서](https://sling.apache.org/documentation/bundles/repository-initialization.html)를 참조하십시오.
* RTC: 기존 서비스 사용자의 권한을 변경하는 경우 전용 RTC 문제를 만들고 보안 팀의 검토를 받도록 하십시오.

**저장소 초기화를 통한 만들기**

서비스 사용자와 해당 권한 설정을 정의하려면 항상 `repo-init`을 사용하고 빠른 시작 기능 모델의 올바른 섹션에 두 가지를 모두 배치하십시오.

**모범 사례**

* 서비스 사용자를 만드는 데 항상 `repo-init`을 사용합니다.
* 서비스 사용자 만들기에서 항상 중간 경로를 지정합니다.
* AEM에 대한 모든 기본 제공 서비스 사용자는 `system/cq:services/internal` 아래에 위치해야 합니다.
* 또한 기능별로 그룹 서비스 사용자의 중간 상대 경로에 `system/cq:services/internal/<your-feature>`를 추가합니다.
* 고객 정의 서비스 사용자는 `system/cq:services/<customer-intermediate-rel-path>` 아래에 위치해야 하며 내부 트리 아래에 위치해서는 안 됩니다.
* 사용자가 이미 존재하여 사용 주체 기반 인증을 지원하는 새 위치로 이동해야 하는 경우 **with path** 대신 **with forced path**&#x200B;를 사용합니다.

**예**

```
create service user my-new-feature-readcomment-service with path system/cq:services/internal/myfeature
set principal ACL for my-new-feature-readcomment-service
    allow rep:readProperties on /content/myFeature restriction(rep:itemNames,commentTitle,commentDate,commentTxt)
end
```

```
create service user my-existing-feature-addcomment-service with forced path system/cq:services/internal/myfeature
set principal ACL for my-existing-feature-addcomment-service
    allow jcr:addChildNodes,rep:addProperties on /content/myfeature restrictions(rep:glob,*/comments/*)
end
```

```
create service user myfeature-ims-service with path system/cq:services/internal/myfeature
set principal ACL for myfeature-ims-service
    allow jcr:read on home(myfeature-ims-service)
end
```

### 정리 서비스 사용자 및 권한 {#cleanup-service-users-and-permissions}

다음 repo init 명령을 사용하여 사용하지 않는 서비스 사용자 및 권한을 정리할 수 있습니다.

```
# Remove the principal-based access control policy for principal my-feature-service
delete principal ACL for my-feature-service

# Remove all resource-based access control entries (ACEs) for principal my-feature-service
delete ACL for my-feature-service

# Disable the service user
disable service user my-feature-service : "My feature is no longer used"

# Remove the service user
delete service my-feature-service 
```

### 서비스 사용자 테스트 {#testing-service-users}

서비스 사용자 및 권한 설정에 대한 서버측 테스트를 작성하는 것이 중요합니다. 이를 통해 설정이 실제로 작동하는지 확인할 수 있을 뿐만 아니라 액세스 제어 콘텐츠 또는 서비스 사용자를 변경할 때 회귀 및 의도하지 않은 실수를 발견할 수 있습니다.

`com.adobe.granite.testing.clients` 라이브러리는 서비스 사용자를 위한 SST를 쉽게 작성할 수 있는 많은 유틸리티를 제공합니다.
