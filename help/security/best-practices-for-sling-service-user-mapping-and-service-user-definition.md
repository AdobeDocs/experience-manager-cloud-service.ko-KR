---
title: Sling 서비스 사용자 매핑 및 서비스 사용자 정의에 대한 우수 사례
description: 슬링 서비스 사용자 매핑 및 서비스 사용자 정의에 대한 모범 사례에 대해 알아봅니다
source-git-commit: b6f7b6996b377ecfa372742ce1ad22139547ebdd
workflow-type: tm+mt
source-wordcount: '1884'
ht-degree: 0%

---


# Sling 서비스 사용자 매핑 및 서비스 사용자 정의에 대한 우수 사례 {#best-practices-for-sling-service-user-mapping-and-service-user-definition}

## 서비스 사용자 매핑 {#service-user-mapping}

서비스에서 해당 시스템 사용자에게 매핑을 추가하려면 `ServiceUserMapper` 서비스. 이러한 모듈형을 유지하기 위해 Sling &quot;수정&quot; 메커니즘을 사용하여 이러한 구성을 제공할 수 있습니다(참조) [슬링-](https://issues.apache.org/jira/browse/SLING-3578) 을 참조하십시오. 번들과 함께 이러한 구성을 설치하는 권장 방법은 다음 예제에 설명된 대로 빠른 시작 프로비저닝 모델에 추가하는 것입니다.

```
org.apache.sling.serviceusermapping.impl.ServiceUserMapperImpl.amended-my-mapping
    user.default=""
    user.mapping=[
        "com.adobe.cq.my-bundle:my-subservice\=[content-writer-service]",
        "com.adobe.cq.my-bundle:my-subservice-different-task\="[myfeature-configuration-writer-service,content-reader-service]"
    ]
```

### 매핑 형식 {#mapping-format}

AEM 6.4 이후 매핑 형식은 다음과 같이 정의됩니다.

>[!NOTE]
>
>다음 `userName` 는 더 이상 사용되지 않으며 더 이상 사용해서는 안 됩니다.

```
bundleId [:subserviceName] = userName | [principalNames]   
```

`bundleId` 및 `subserviceName` 서비스를 식별하고, `userName/principalNames` 서비스 사용자 식별 및 `principalNames` 는 쉼표로 구분된 목록입니다.

또한 `principalNames` 는 기본적으로 id와 동일한 서비스 사용자 계정 이름 목록입니다.


**우수 사례**

* 다른 작업에 대한 하위 서비스 이름 - 번들의 서비스가 다른 작업을 수행하는 경우 식별하는 것이 좋습니다. `subserviceNames` 작업별로 그룹화
* 지정된 서비스가 다른 작업을 수행하는 경우(예: 에셋 콘텐츠를 읽고 의 하위 트리 아래에 있는 정보를 업데이트하는 경우) `/var`)에서 공통 항목을 통합하는 것처럼 개별 작업을 반영하는 다양한 서비스 주도자를 집계하여 이를 반영하는 것이 좋습니다 `dam-reader-service` 특정 기능 포함 `assetreport-writer-service`
* 각 서비스는 매우 구체적이고 제한된 작업 집합에 이상적으로 연결되어 있습니다
* 을 사용한 새 형식 `[one,or,multiple,principalNames]` 는 AEM 6.4부터 서비스 사용자 매핑을 정의하는 데 권장되는 방법입니다.

다음은 형식을 변경하는 이유와 Adobe이 단일 userID에 대해서만 버전 매핑 대신 형식을 사용할 것을 권장하는 이유 목록입니다.

* 고객의 특수 요구 사항과 일반적인 작업을 결합하여 서비스 사용자를 재사용할 수 있는 기능
* 권한 설정의 중복 방지
* 특정 서비스가 실제로 수행하는 효과적인 권한(및 작업)에 대한 이해 향상
* 서비스 사용자의 명시적 그룹 구성원이 필요하지 않습니다. 그룹 권한 변경에 따라 문제가 발생할 수 있습니다.
* 성능 향상 및 확장성

## 매핑 해결 및 서비스 로그인 {#mapping-resolution-and-service-login}

### 서비스 매핑 확인 {#service-mapping-resolution}

아래에 설명된 서비스 매핑을 해결하기 위한 호출 시퀀스:

1. 활성 검색 `principalNames` 지정된 항목에 대한 매핑 `bundleId` 및 `subserviceName`
1. `principalNames` 에 대한 매핑 `bundleId` 및 null `subserviceName`
1. `userName` 에 대한 매핑 `bundleId` 및 `subserviceName`
1. `userName` 매핑 대상 `bundleId` 및 null `subserviceName`
1. 기본 매핑
1. 기본 사용자

### SlingRepository - 서비스 로그인 {#slingrepository-servicelogin}

서비스를 가져오기 위한 시퀀스 `Session/ResourceResolver` 는 다음과 같이 작동합니다.

1. 에서 사용자 이름 가져오기 `ServiceUserMapper` => 아래 설명된 대로 저장소 사전 인증 로그인
1. 에서 사용자 ID 검색 `ServiceUserMapper`
1. 현재 사용자 ID에 대해 더 이상 사용되지 않는 1ServiceUserConfiguration`이 있는지 확인
1. 사용자 ID로 기본 Sling 서비스 로그인(예: 시퀀스 `createAdministrativeSession` 및 서비스 사용자 id에 대한 가장)

주도자 이름이 있는 새 매핑을 사용하면 다음과 같은 간소화된 저장소 로그인이 가능합니다.

* 주체 이름 집합은 을 채우는 데 사용할 유효 주체로 처리됩니다. `Subject`
* 따라서 저장소 로그인을 사전 인증할 수 있습니다.
* 그룹 멤버십 확인 없음

  >[!NOTE]
  >
  >서비스 사용자에 대해 필요한 모든 권한을 선언해야 합니다. &#39;everyone&#39; 및 기타 그룹 권한은 더 이상 상속되지 않습니다.

* 서비스를 받기 위한 추가 관리자 로그인 없음-`Session/ResourceResolver` 이 생성됩니다.

### 더 이상 사용되지 않는 ServiceUserConfiguration {#deprecated-serviceUserConfiguration}

매핑에서 단일 사용자 이름을 지정하는 것은 기존 사용자 이름과 동일합니다 `ServiceUserConfiguration.simpleSubjectPopulation`. 새 형식을 사용하여에서 제공하는 해결 방법 `ServiceUserConfiguration` 은 서비스 사용자 매핑에 직접 반영할 수 있습니다. 다음 `ServiceUserConfiguration` 따라서 AEM에 대해 더 이상 사용되지 않으며 기존의 모든 사용법은 대체됩니다.

## 서비스 사용자 {#service-users}

### 기존 서비스 사용자 재사용 {#reusing-existing-service-users}

다음 조건이 충족되는 경우 기존 서비스 사용자를 다시 사용하는 것이 좋습니다.

* 요구 사항이 기존 서비스 사용자의 의도와 일치해야 합니다.
* 서비스는 기존 공통 서비스 사용자가 다루는 공통 작업을 수행해야 합니다. 이 경우 중복을 도입하는 대신 서비스 사용자를 다시 사용하는 것이 좋습니다
* 서비스는 기존 서비스 사용자가 다루는 특정 작업을 필요로 합니다. 확실하지 않은 경우 이를 담당하는 기능 팀에 문의하십시오.

다음과 같은 경우 기존 서비스 사용자를 다시 사용하지 마십시오.

* 관련 없는 방식으로 권한을 수정해야 제대로 작동합니다
* 제공된 권한의 작은 하위 집합만 필요하며 실제 일치이기 때문이 아니라 기능이 작동하므로 재사용하고자 하는 경우
* 만약 그것의 이름이 당신이 필요로 하는 것과 완전히 다른 의도를 나타낸다면. 특정 서비스를 소유한 기능 팀이 권한을 변경하여 기능을 중단시킬 수 있으므로 작동하므로 문제가 발생할 수 있습니다.

### 서비스 사용자 만들기 {#creating-a-service-user}

AEM의 기존 서비스 사용자가 사용 사례에 적용할 수 없는지 확인하고 해당 RTC 문제가 승인되면 계속 진행하여 새 사용자를 기본 콘텐츠에 추가할 수 있습니다. 확장된 보안 팀의 구성원이 RTC 투표에 참여하는 것이 이상적이므로 적절한 이해 관계자도 참여하도록 하십시오.

**명명 규칙**

AEM 보안 팀은 새 서비스 사용자에게 일관성을 추가하고 가독성과 유지 관리를 개선하기 위해 서비스 사용자를 위한 다음과 같은 명명 규칙을 정의했습니다.

서비스 사용자 이름은 대시로 구분된 3개의 요소로 구성됩니다 **&#39;-&#39;**:

1. 서비스 작업에 의해 타겟팅되는 논리적 엔티티/기능(변경될 수 있는 경로 요소를 피함)
1. 서비스가 수행할 작업
1. 후행 **&#39;서비스&#39;** 사용자가 서비스 사용자인 id와 주체 이름에서 쉽게 찾을 수 있습니다

**우수 사례**

* 서로 다른 엔티티/피쳐를 혼합하지 마십시오. 서비스에 서로 다른 요구 사항이 있는 경우 개별 서비스 사용자로 분할하고 매핑에서 집계합니다
* 서비스 사용자당 하나의 잘 정의된 작업으로 제한합니다. 너무 많거나 관련이 없는 권한을 부여하게 되는 경우 분할
* 서비스의 실제 필요성을 파악하는 데 시간을 할애합니다.
* 편리하고 의미 있고 설명력이 있는 서비스 사용자 이름을 찾는 데 시간을 투자하십시오.
* 피드백 및 검토 요청: 기능에 익숙하지 않은 개발자는 의도를 읽고 이해할 수 있어야 합니다. 그들은 미래에 그것을 고치거나 유지하는 임무를 받을 수도 있다.

마지막에 서비스 사용자 이름이 표시됩니다.

* 사용 방법 및 재사용할 수 있는 경우:

   * 매우 일반적임: `content-writer-service`. 서비스가 모든 콘텐츠를 읽을 수도 있어야 하는 경우 집계에서 다시 사용해도 안전합니다.
   * 매우 구체적임: `asset-linkshare-service`. 서비스가 실제로 에셋의 링크 공유를 수행하지 않는 한 다시 사용해도 안전하지 않습니다.

* 기능 세트 및 권한 설정의 모습은 다음과 같습니다.

   * 논리적 엔티티는 권한 설정과 일치해야 합니다.

      * A `content-foo-service` 은 콘텐츠에 대한 작업에만 연결해야 합니다. 구성 또는 사용자와 같은 다른 엔티티에서 작동하도록 권한을 부여하는 것은 잘못될 수 있습니다
      * 다음과 같은 특정 서비스 `personalization-foo-service` 특정 권한도 함께 제공됩니다. 모든 콘텐츠에 대한 권한을 부여하는 것으로 끝나는 경우 더 이상 특정되지 않습니다. 이를 이름에 반영하거나 집계에서 일반 사용자를 다시 사용합니다
      * 과 같은 기능별 서비스 `msm-xyz-service` 에는 msm 관련 권한만 있어야 합니다. 커뮤니티 구성 또는 화면 사용자 관리와 같은 관련 없는 기능에 대한 권한을 확장하지 마십시오.

   * 작업은 다음 권한과 일치해야 합니다.

      * A `foo-reader-service` 일반 항목만 읽을 수 있어야 합니다. 쓰기 권한 부여 안 함
      * A `foo-writer-service` 쓰기 작업을 수행해야 할 수 있습니다. 그러나 액세스 제어 컨텐츠를 읽기/수정할 수 있는 권한은 부여해서는 안 됩니다
      * A `foo-replicator-service` 은(는) 다음을 가질 수 있습니다. `crx:replicate` 부여됨.

**예**

의 예 `configuration-reader-service`:

* 이 이름은 DM 통합 구성과 같이 특정 기능의 구성이 아닌 일반적인 구성을 지칭함을 나타냅니다. 이러한 통합의 구성을 읽는 데 특별히 타겟팅된 서비스 사용자의 이름은 보다 적절합니다 `dmconfig-reader-service` 또는 `s7config-reader-service`

  >[!NOTE]
  >
  >이름 지정에 경로 정보가 포함되어 있지 않습니다. 다음에서 구성이 이동되었습니다. `/etc` 끝 `/conf`.

* task-element는 해당 사용자에게 바인딩된 서비스가 읽기 작업만 수행함을 나타냅니다.

의 예 `userproperties-copy-service`:

* 이 서비스 사용자에게 바인딩된 서비스는 프로필 또는 환경 설정과 같은 사용자/그룹 속성에서 작동합니다.
* 특히 다음과 같은 이름과 대조하여 해당 정보를 복사하는 것이 목표입니다. `userproperties-writer-service` 모든 종류의 쓰기 작업이 포함됩니다. 따라서 이러한 복사 작업에 대한 권한 설정에서는 한 위치에 항목을 추가하고 다른 위치에 항목을 제거할 수만 있습니다.

**권한 설정에 대한 우수 사례**

* 서비스 사용자에 대해 항상 사용자 기반 액세스 제어 설정을 사용하십시오. 자세한 내용은 아래 예를 참조하십시오.

   * 서비스 사용자 및 해당 권한을 Skyline에서 변경할 수 없는 애플리케이션 콘텐츠로 표시할 수 있도록 허용
   * 경로 및 트리 구조를 만들 필요가 없음

* 권한만 부여하고 거부할 수 없음
* 권한 제한

   * 필요한 최소 권한 집합만 부여
   * 자세한 내용은 [항목에 권한 매핑](https://jackrabbit.apache.org/oak/docs/security/privilege/mappingtoitems.html) 및 [API 호출을 권한에 매핑](https://jackrabbit.apache.org/oak/docs/security/privilege/mappingtoprivileges.html) 설명서
   * 다음에 대한 권한 부여 안 함 `jcr:all`. 그것은 최소 세트가 아닐 가능성이 가장 높다.

* 범위 축소

   * 기능별 하위 트리에 액세스 제어 정책 배치
   * 분산 항목의 경우: 범위를 제한하려면 제한 사용(참조) [설명서](http://jackrabbit.apache.org/oak/docs/security/authorization/restriction.html) 기본 제공 제한 사항 목록의 경우).

* 일관성 보장

   * 서비스 사용자 이름에 사용한 엔티티 및 작업과 일관된 권한을 만듭니다.
   * 관련 없는 권한을 추가하지 마십시오. 예를 들어, `workflow-administration-service` 다음 위치에서 사용자 관리 작업을 수행할 수 있는 권한 부여 `/home/users/screens` 또는 s7-config를 읽도록 두십시오.

* 완성도

   * 서비스에 설계된 작업을 수행하는 데 필요한 모든 권한이 있는지 확인하십시오. 서비스는 고객 환경에서도 즉시 작동해야 합니다.
   * 고객에게 권한 설정을 확장하도록 요구하지 않음(예: 아래) `/apps`)

* 권한 설정의 중복 방지

   * 일반 서비스 사용자 재사용
   * 추가로 필요한 특정 권한을 제공하는 기능별 서비스 사용자로 이들을 집계합니다

* 권한 설정을 다른 기능으로 분할하지 마십시오. 이렇게 해야 하는 이유는 서비스 사용자가 잘 정의되지 않았거나 너무 많은 다른 작업을 수행함을 나타냅니다
* 다음과 같은 이유로 서비스 사용자를 그룹에 배치하지 마십시오.

   * 서비스 사용자의 구현 세부 사항을 &#39;공개&#39; 그룹과 혼합합니다
   * 권한 변경에 대한 제어 부족(회귀 및 권한 에스컬레이션이 발생하기 쉬움)
   * 로그인 및 평가 성능
   * 사용자 기반 ac-setup에서 작동하지 않음

* 예측 가능한 경로가 없는 사용자 홈 노드(또는 포함된 하위 트리)에 대한 액세스는 home(`userId`). sling 저장소 초기화 보기 [설명서](https://sling.apache.org/documentation/bundles/repository-initialization.html) 을 참조하십시오.
* RTC: 기존 서비스 사용자의 권한을 변경하고 보안 팀에서 검토하도록 하는 경우 전용 RTC 문제를 만듭니다.

**저장소 초기화로 생성**

항상 사용 `repo-init` 서비스 사용자와 해당 권한 설정을 정의하고 빠른 시작 기능 모델의 올바른 섹션에 두 옵션을 모두 배치하려면 다음을 수행하십시오.

**우수 사례**

* 항상 사용 `repo-init` 서비스 사용자를 만들려면
* 항상 서비스 사용자 생성을 위한 중간 경로 지정
* AEM의 모든 기본 제공 서비스 사용자는 아래에 위치해야 합니다. `system/cq:services/internal`
* 기능별로 그룹 서비스 사용자의 중간 상대 경로에 추가로 추가됩니다. `system/cq:services/internal/<your-feature>`
* 고객 정의 서비스 사용자는 아래에 있어야 합니다. `system/cq:services/<customer-intermediate-rel-path>` 내부 트리 아래에 절대 위치하지 않음
* 사용 **강제 경로 사용** 대신 **경로 포함** 사용자가 이미 존재하고 사용자 기반 인증을 지원하는 새 위치로 이동해야 하는 경우.

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

### 서비스 사용자 및 권한 정리 {#cleanup-service-users-and-permissions}

다음 repo init 명령을 사용하여 사용하지 않는 서비스 사용자와 해당 권한을 정리할 수 있습니다.

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

서비스 사용자와 해당 권한 설정에 대한 서버측 테스트를 작성하는 것이 중요합니다. 이렇게 하면 설정이 실제로 작동하는지 확인할 수 있을 뿐만 아니라 액세스 제어 콘텐츠 또는 서비스 사용자를 변경할 때 회귀 및 의도하지 않은 실수를 발견하는 데 도움이 됩니다.

다음 `com.adobe.granite.testing.clients` library는 서비스 사용자가 SST를 쉽게 작성할 수 있도록 하는 많은 유틸리티를 제공합니다.





