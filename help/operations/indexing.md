---
title: 컨텐츠 검색 및 인덱싱
description: '컨텐츠 검색 및 인덱싱 '
translation-type: tm+mt
source-git-commit: 99dce041a6d7554785fd43eb82c671643e903f23

---


# 컨텐츠 검색 및 인덱싱 {#indexing}

## 클라우드 서비스로 AEM의 변경 사항 {#changes-in-aem-as-a-cloud-service}

AEM을 클라우드 서비스로 사용하는 Adobe는 AEM 인스턴스 중심 모델에서 클라우드 관리자에서 CI/CD 파이프라인을 기반으로 하는 n-x AEM 컨테이너가 있는 서비스 기반 보기로 전환하고 있습니다. 단일 AEM 인스턴스에서 인덱스를 구성하고 유지 관리하는 대신 배포 전에 인덱스 구성을 지정해야 합니다. 제작 과정의 구성 변경은 분명히 CI/CD 정책을 위반하는 것이다. 색인 변경도 마찬가지입니다. 이렇게 하면 시스템 안정성 및 성능에 영향을 줄 수 있습니다. 단, 지정하지 않은 경우 테스트를 거쳐 다시 인덱싱한 다음 프로덕션으로 가져올 수 있습니다.

다음은 AEM 6.5 및 이전 버전과 비교하여 주요 변경 사항 목록입니다.

1. 사용자는 더 이상 색인을 디버깅, 구성 또는 유지 관리할 단일 AEM 인스턴스의 인덱스 관리자에 액세스할 수 없습니다. 로컬 개발 및 사전 배포 시에만 사용됩니다.

1. 사용자는 단일 AEM 인스턴스에서 색인을 변경하지 않으며, 더 이상 일관성 검사 또는 재색인에 대해 걱정할 필요가 없습니다.

1. 일반적으로, Cloud Manager CI/CD 파이프라인의 품질 게이트웨이를 우회하지 않고 프로덕션의 비즈니스 KPI에 영향을 주지 않기 위해 색인 변경 사항이 먼저 시작됩니다.

1. 검색 및 인덱싱 항목에 대한 전체적인 보기를 제공하기 위해 제작 시 검색 성능을 비롯한 모든 관련 지표를 런타임 시 고객에게 제공할 수 있습니다.

1. 고객은 필요에 따라 경고를 설정할 수 있습니다.

1. SRE는 24시간 연중무휴 시스템 상태를 모니터링하고 필요에 따라 신속하게 조치를 취할 것입니다.

1. 색인 구성은 배포를 통해 변경됩니다. 색인 정의 변경 사항은 다른 컨텐츠 변경 사항과 같이 구성됩니다.

1. Blue-Green 배포 모델이 [](#index-management-using-blue-green-deployments) 도입됨에 따라 AEM에서 클라우드 서비스로 높은 수준의 AEM에는 다음과 같은 두 가지 인덱스 세트가 존재합니다.이전 버전 세트(파란색)와 새 버전 세트(녹색)에 대해 설정된 세트

사용되는 인덱스의 버전은 `useIfExist` 플래그를 통해 색인 정의에 플래그를 사용하여 구성됩니다. 인덱스는 한 버전의 응용 프로그램(예: 파란색 또는 녹색만 해당)에서만 사용하거나 두 버전 모두에서 사용할 수 있습니다. 자세한 설명서는 블루-그린 배포를 [사용하는 색인 관리에서 사용할 수 있습니다](#index-management-using-blue-green-deployments).

1. 고객은 Cloud Manager 빌드 페이지에서 색인 작업이 완료되었는지 확인하고 새 버전이 트래픽을 받을 준비가 되면 알림을 받게 됩니다.

1. 제한 사항:현재, 클라우드 서비스로 AEM에서 인덱스 관리는 lucene 유형의 색인에만 지원됩니다.

<!-- ## Sizing Considerations {#sizing-considerations}

AEM as a Cloud Service comes with a default capacity model to provide sufficient performance for average web applications. This "average" measure relates to the repository size and even more relevant to the indexing size. If we have reasons to believe that we need extended capacity for a specific customer project, an evaluation with SREs and Engineering will take place to determine the required capacity settings. 

AS NOTE: the above is internal for now.

-->

## 사용 방법 {#how-to-use}

색인을 정의하면 세 가지 사용 사례들 중 하나로 구성됩니다.

1. 새 고객 색인 정의 추가
1. 기존 인덱스 정의를 업데이트하는 중입니다. 이는 기존 인덱스 정의의 새 버전을 추가하는 것을 의미합니다
1. 중복되거나 사용되지 않는 기존 인덱스를 제거합니다.

위의 두 포인트 1 및 2의 경우, 각각의 Cloud Manager 릴리스 일정에 사용자 지정 코드 베이스의 일부로 새 색인 정의를 만들어야 합니다. 자세한 내용은 클라우드 서비스로 [AEM에 배포 설명서를](/help/implementing/deploying/overview.md)참조하십시오.

### 새 색인 정의 준비 {#preparing-the-new-index-definition}

이 이름 지정 패턴 다음에 실제 색인 정의를 포함하는 새 인덱스 정의 패키지를 준비해야 합니다.

`<indexName>[-<productVersion>]-custom-<customVersion>`

그 다음 `ui.content/src/main/content/jcr_root`밑으로 들어가야겠네요 현재 하위 루트 폴더는 지원되지 않습니다.

<!-- need to review and link info on naming convention from https://wiki.corp.adobe.com/display/WEM/Merging+Customer+and+OOTB+Index+Changes?focusedCommentId=1784917629#comment-1784917629 -->

위 샘플의 패키지는 로 `com.adobe.granite:new-index-content:zip:1.0.0-SNAPSHOT`빌드됩니다.

### 색인 정의 배포 {#deploying-index-definitions}

이제 색인 정의가 사용자 정의 및 버전 관리로 표시됩니다.

* 가변 컨텐츠인 색인 정의 자체(예: `/oak:index/ntBaseLucene-custom-1`)

따라서 인덱스를 배포하려면 일반적으로 Git 및 Cloud Manager 배포 프로세스를 통해`/oak:index/definitionname`변경 가능한 패키지를 **통해**&#x200B;색인 정의( `ui.content` )를 전달해야 합니다.

새 인덱스 정의가 추가되면 Cloud Manager를 통해 새 애플리케이션을 배포해야 합니다. 배포 시 작성자와 게시를 위해 각각 MongoDB 및 Azure 세그먼트 저장소에 인덱스 정의를 추가(필요한 경우 병합)할 책임이 있는 두 개의 작업이 시작됩니다. Blue-Green 스위치를 실행하기 전에 기본 리포지토리는 새 인덱스 정의로 다시 색인화됩니다.

## 블루 그린 배포를 사용한 색인 관리 {#index-management-using-blue-green-deployments}

### 색인 관리란? {#what-is-index-management}

색인 관리는 인덱스를 추가, 제거 및 변경하는 것입니다. 인덱스의 *정의를* 변경하는 것은 빠르지만 변경 사항(&quot;색인 작성&quot;이라고도 함) 또는 기존 인덱스의 경우 &quot;다시 인덱싱&quot;이라고 함)을 적용하려면 시간이 필요합니다. 이것은 즉각적이지 않다:데이터를 인덱싱하려면 저장소를 스캔해야 합니다.

### 친환경 배포 소개 {#what-is-blue-green-deployment}

블루 그린 배포를 통해 다운타임을 줄일 수 있습니다. 또한 다운타임 없이 업그레이드할 수 있으며 신속한 롤백 기능을 제공합니다. 애플리케이션의 이전 버전(파란색)은 애플리케이션의 새 버전(녹색)과 동시에 실행됩니다.

### 읽기 전용 및 읽기 쓰기 영역 {#read-only-and-read-write-areas}

저장소의 특정 영역(저장소의 읽기 전용 부분)은 이전 버전(파란색)과 새로운 버전의 애플리케이션에서 다를 수 있습니다. 저장소의 읽기 전용 영역은 일반적으로 &quot;`/app`&quot; 및 &quot;`/libs`&quot;입니다. 다음 예에서는 기울임꼴로 읽기 전용 영역을 표시하는 데 사용되고 읽기/쓰기 영역에는 굵은 기울임체가 사용됩니다.

* **/**
* */apps(읽기 전용)*
* **/컨텐츠**
* */libs(읽기 전용)*
* **/oak:index**
* **/oak:index/acme**
* **/jcr:system**
* **/system**
* **/var**

저장소의 읽기-쓰기 영역은 응용 프로그램의 모든 버전 간에 공유되지만 응용 프로그램의 각 버전에 대해서는 특정 `/apps` 및 `/libs`세트가 있습니다.

### 블루 그린 배포 없이 색인 관리 {#index-management-without-blue-green-deployment}

개발 중에 또는 온-프레미스 설치를 사용하는 경우 런타임 시 인덱스를 추가, 제거 또는 변경할 수 있습니다. 색인은 사용 가능한 즉시 사용됩니다. 인덱스가 아직 이전 버전의 응용 프로그램에서 사용되지 않는 경우, 일반적으로 예정된 다운타임에 인덱스가 만들어집니다. 색인을 제거하거나 기존 색인을 변경할 때도 마찬가지입니다. 색인을 제거하면 해당 색인이 제거되는 즉시 사용할 수 없게 됩니다.

### 블루 그린 배포를 통한 색인 관리 {#index-management-with-blue-green-deployment}

청록색 배포로 다운타임이 없습니다. 그러나 색인 관리의 경우, 이렇게 하려면 특정 버전의 응용 프로그램에서만 인덱스가 사용되어야 합니다. 예를 들어 응용 프로그램 버전 2에서 인덱스를 추가할 때 아직 응용 프로그램 버전 1에서 사용하지 않도록 설정할 수 있습니다. 반대는 색인이 제거될 때의 경우입니다.버전 2에서 제거된 색인은 버전 1에서 계속 필요합니다. 색인 정의를 변경할 때 이전 버전의 색인은 버전 1에만 사용하고 새 버전의 색인은 버전 2에만 사용할 수 있습니다.

다음 표는 5개의 인덱스 정의를 보여 줍니다.index `cqPageLucene` 는 두 버전 모두에서 사용되지만 색인은 버전 2에서만 `damAssetLucene-custom-1` 사용됩니다.


> [!NOTE]
> `<indexName>-custom-<customerVersionNumber>` 은 AEM을 클라우드 서비스로 사용하여 기존 색인의 교체로 표시해야 합니다.

| 색인 | 기본 색인 | 버전 1에서 사용 | 버전 2에서 사용 |
|---|---|---|---|
| /oak:index/damAssetLucene | 예 | 예 | 아니오 |
| /oak:index/damAssetLucene-custom-1 | 예(사용자 정의) | 아니오 | 예 |
| /oak:index/acmeProduct-custom-1 | 아니오 | 예 | 아니오 |
| /oak:index/acmeProduct-custom-2 | 아니오 | 아니오 | 예 |
| /oak:index/cqPageLucene | 예 | 예 | 예 |

버전 번호는 인덱스가 변경될 때마다 증가합니다. 사용자 정의 인덱스 이름이 제품 자체의 인덱스 이름과 충돌하지 않도록 하려면 사용자 정의 색인 및 기본 색인에 대한 변경 사항을 다음으로 종료해야 합니다 `-custom-<number>`.

### 기본 색인에 대한 변경 사항 {#changes-to-out-of-the-box-indexes}

Adobe가 이름이 `damAssetLucene-2` `cqPageLucene-2` 지정되거나 만들어진 새로운 색인 &quot;damAssetLucene&quot; 또는 &quot;cqPageLucene&quot;과 같은 기본 색인을 변경하기만 하면, 또는 인덱스가 이미 사용자 정의된 경우, 사용자 지정된 색인 정의가 아래와 같이 기본 색인의 변경 사항과 병합됩니다. 변경 내용 병합은 자동으로 수행됩니다. 즉, 기본 색인이 변경되면 아무 작업도 할 필요가 없습니다. 하지만 나중에 다시 색인을 사용자 지정할 수 있습니다.

| 색인 | 기본 색인 | 버전 2에서 사용 | 버전 3에서 사용 |
|---|---|---|---|
| /oak:index/damAssetLucene-custom-1 | 예(사용자 정의) | 예 | 아니오 |
| /oak:index/damAssetLucene-2-custom-1 | 예(damAssetLucene-custom-1 및 damAssetLucene-2에서 자동으로 병합) | 아니오 | 예 |
| /oak:index/cqPageLucene | 예 | 예 | 아니오 |
| /oak:index/cqPageLucene-2 | 예 | 아니오 | 예 |

### 제한 사항 {#limitations}

인덱스 관리는 현재 유형의 `lucene`색인에만 지원됩니다.

### 색인 제거 {#removing-an-index}

응용 프로그램의 이후 버전에서 인덱스를 제거하려는 경우 새 이름으로 빈 인덱스(인덱스할 데이터가 없는 인덱스)를 정의할 수 있습니다. 예를 들어 이름을 지정할 수 `/oak:index/acmeProduct-custom-3`있습니다. 인덱스를 대체합니다 `/oak:index/acmeProduct-custom-2`. 시스템에서 `/oak:index/acmeProduct-custom-2` 제거되면 빈 인덱스도 제거할 `/oak:index/acmeProduct-custom-3` 수 있습니다.

### 색인 추가 {#adding-an-index}

응용 프로그램의 새 버전 이상에서 사용할 &quot;/oak:index/acmeProduct-custom-1&quot;이라는 인덱스를 추가하려면 다음과 같이 인덱스를 구성해야 합니다.

`/oak:index/acmeProduct-custom-1`

위와 같이, 이렇게 하면 인덱스가 새로운 버전의 응용 프로그램에서만 사용됩니다.

### 색인 변경 {#changing-an-index}

기존 색인이 변경되면 변경된 색인 정의와 함께 새 색인을 추가해야 합니다. 예를 들어 기존 인덱스 &quot;/oak:index/acmeProduct-custom-1&quot;이 변경되었다고 가정합니다. 이전 인덱스는 아래에 저장되고 `/oak:index/acmeProduct-custom-1`새 인덱스는 아래에 저장됩니다 `/oak:index/acmeProduct-custom-2`.

이전 버전의 응용 프로그램은 다음 구성을 사용합니다.

`/oak:index/acmeProduct-custom-1`

응용 프로그램의 새 버전에서는 다음과 같은(변경된) 구성을 사용합니다.

`/oak:index/acmeProduct-custom-2`