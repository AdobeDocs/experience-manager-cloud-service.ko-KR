---
title: 콘텐츠 검색 및 색인 지정
description: 콘텐츠 검색 및 색인 지정
translation-type: tm+mt
source-git-commit: 0789eb6ea2fb128d7b6b87cffd44a92187535642
workflow-type: tm+mt
source-wordcount: '1474'
ht-degree: 2%

---


# 콘텐츠 검색 및 색인 지정 {#indexing}

## Changes in AEM as a Cloud Service {#changes-in-aem-as-a-cloud-service}

AEM을 Cloud Service으로 사용하는 Adobe은 Cloud Manager에서 CI/CD 파이프라인을 기반으로 하는 n-x AEM 컨테이너가 있는 서비스 기반 보기로 AEM 인스턴스 중심의 모델에서 옮겨가고 있습니다. 단일 AEM 인스턴스에서 인덱스를 구성 및 유지 관리하는 대신 배포 전에 색인 구성을 지정해야 합니다. 제작 과정의 구성 변화는 분명히 CI/CD 정책을 위반하는 것이다. 색인 변경 사항도 마찬가지입니다. 색인 변경 작업은 지정된 테스트 및 재색인이 없는 경우 시스템 안정성 및 성능에 영향을 줄 수 있기 때문에 프로덕션으로 가져오기 전에 적용됩니다.

다음은 AEM 6.5 및 이전 버전과 비교하여 주요 변경 사항 목록입니다.

1. 사용자는 더 이상 색인을 디버깅, 구성 또는 유지 관리할 단일 AEM 인스턴스의 인덱스 관리자에 액세스할 수 없습니다. 로컬 개발 및 On-Prem 배포에만 사용됩니다.

1. 사용자는 단일 AEM 인스턴스의 색인을 변경하지 않으며 더 이상 일관성 검사 또는 재색인에 대해 걱정할 필요가 없습니다.

1. 일반적으로, Cloud Manager CI/CD 파이프라인의 품질 게이트웨이를 우회하지 않고 프로덕션의 비즈니스 KPI에 영향을 주지 않기 위해 색인 변경 사항이 먼저 시작됩니다.

1. 검색 및 색인 항목에 대한 전체적인 보기를 제공하기 위해 제작 과정의 검색 성과를 비롯한 모든 관련 지표를 런타임 시 고객이 사용할 수 있습니다.

1. 고객은 필요에 따라 경고를 설정할 수 있습니다.

1. SRE는 24시간 연중무휴 시스템 상태를 모니터링하며 필요한 조치나 이른 시간에 조치를 취할 것입니다.

1. 색인 구성은 배포를 통해 변경됩니다. 색인 정의 변경 사항은 다른 컨텐츠 변경 사항과 같이 구성됩니다.

1. AEM의 Cloud Service에서 [블루-그린 배포 모델](#index-management-using-blue-green-deployments) 도입과 함께 세 가지 인덱스 세트가 존재합니다. 한 세트는 이전 버전(파란색)으로, 한 세트는 새 버전(녹색)으로 설정되어 있습니다.

1. 고객은 Cloud Manager 빌드 페이지에서 색인 작업이 완료되었는지 확인하고 새 버전이 트래픽을 받을 준비가 되면 알림을 받게 됩니다.

1. 제한 사항: 현재 AEM의 Cloud Service 색인 관리는 lucene 유형의 색인에서만 지원됩니다.

<!-- ## Sizing Considerations {#sizing-considerations}

AEM as a Cloud Service comes with a default capacity model to provide sufficient performance for average web applications. This "average" measure relates to the repository size and even more relevant to the indexing size. If we have reasons to believe that we need extended capacity for a specific customer project, an evaluation with SREs and Engineering will take place to determine the required capacity settings.

AS NOTE: the above is internal for now.

-->

## 사용 방법 {#how-to-use}

색인을 정의하는 것은 3가지 사용 사례들로 구성될 수 있습니다.

1. 새 고객 색인 정의 추가
1. 기존 색인 정의를 업데이트하는 중입니다. 이는 기존 색인 정의의 새 버전을 추가하는 것을 의미합니다
1. 중복되거나 사용되지 않는 기존 인덱스를 제거합니다.

위의 두 점 모두 1과 2의 경우, 각각의 Cloud Manager 릴리스 일정에 사용자 지정 코드 베이스의 일부로 새 색인 정의를 만들어야 합니다. 자세한 내용은 AEM에 [배포 설명서를 참조하십시오](/help/implementing/deploying/overview.md).

### 새 색인 정의 준비 {#preparing-the-new-index-definition}

이 이름 지정 패턴 다음에 실제 색인 정의를 포함하는 새 인덱스 정의 패키지를 준비해야 합니다.

`<indexName>[-<productVersion>]-custom-<customVersion>`

그리고 그 다음 그 밑으로 내려가야 `ui.apps/src/main/content/jcr_root`합니다. 현재 하위 루트 폴더는 지원되지 않습니다.

<!-- need to review and link info on naming convention from https://wiki.corp.adobe.com/display/WEM/Merging+Customer+and+OOTB+Index+Changes?focusedCommentId=1784917629#comment-1784917629 -->

위 샘플의 패키지는 `com.adobe.granite:new-index-content:zip:1.0.0-SNAPSHOT`

### 인덱스 정의 배포 {#deploying-index-definitions}

>[!NOTE]
>
>Jackrabbit Filevault Maven Package Plugin 버전 **1.1.0** 과 관련하여 알려진 문제가 있으며, 이 문제로 인해 모듈 `oak:index` 에 추가할 수 없습니다 `<packageType>application</packageType>`. 이 문제를 해결하려면 버전 **1.0.4를 사용하십시오**.

이제 색인 정의는 사용자 지정 및 버전으로 표시됩니다.

* 인덱스 정의 자체(예: `/oak:index/ntBaseLucene-custom-1`)

따라서 색인을 배포하려면 Git 및 Cloud Manager 배포 프로세스를 통해 색인 정의(`/oak:index/definitionname`) `ui.apps` 를 전달해야 합니다.

새로운 색인 정의가 추가되면 새 응용 프로그램을 Cloud Manager를 통해 배포해야 합니다. 배포 시 작성자와 게시를 위해 각각 MongoDB와 Azure 세그먼트 저장소에 인덱스 정의를 추가(필요한 경우 병합)할 책임이 있는 두 개의 작업이 시작됩니다. Blue-Green 스위치가 실행되기 전에 기본 리포지토리는 새로운 인덱스 정의로 재인덱싱됩니다.

>[!TIP]
>
>AEM에 Cloud Service으로 필요한 패키지 구조에 대한 자세한 내용은 [AEM 프로젝트 구조를 참조하십시오.](/help/implementing/developing/introduction/aem-project-content-package-structure.md)

## 블루-그린 배포를 사용한 색인 관리 {#index-management-using-blue-green-deployments}

### 색인 관리란? {#what-is-index-management}

색인 관리는 색인을 추가, 제거 및 변경하는 것입니다. 인덱스의 *정의를* 변경하는 것은 빠르지만 변경 사항을 적용(종종 &quot;색인 작성&quot;이라고 함) 또는 기존 인덱스의 경우 &quot;다시 인덱싱&quot;을 수행하려면 시간이 필요합니다. 이것은 즉각적이지 않다: 데이터를 인덱싱하려면 리포지토리를 스캔해야 합니다.

### 블루 그린 배포란? {#what-is-blue-green-deployment}

블루-그린 배포를 통해 다운타임을 줄일 수 있습니다. 또한 다운타임을 제로 업그레이드할 수 있으며 빠른 롤백을 제공합니다. 응용 프로그램의 이전 버전(파란색)은 응용 프로그램의 새 버전(녹색)과 동시에 실행됩니다.

### 읽기 전용 및 읽기-쓰기 영역 {#read-only-and-read-write-areas}

저장소의 특정 영역(저장소의 읽기 전용 부분)은 이전 버전(파란색)과 새로운 애플리케이션 버전에서 다를 수 있습니다. 저장소의 읽기 전용 영역은 일반적으로 &quot;`/app`&quot; 및 &quot;`/libs`&quot;입니다. 다음 예에서 이탤릭체는 읽기 전용 영역을 표시하는 데 사용되지만, 굵은 기울임체는 읽기 쓰기 영역에 사용됩니다.

* **/**
* */apps(읽기 전용)*
* **/content**
* */libs(읽기 전용)*
* **/oak:index**
* **/oak:index/acme.**
* **/jcr:system**
* **/system**
* **/var**

저장소의 읽기-쓰기 영역은 응용 프로그램의 모든 버전 간에 공유되지만 응용 프로그램의 각 버전에 대해서는 특정 `/apps` 및 `/libs`세트가 있습니다.

### 블루-그린 배포를 통한 색인 관리 {#index-management-without-blue-green-deployment}

개발 중에 또는 사내 설치 시 런타임 시 색인을 추가, 제거 또는 변경할 수 있습니다. 색인은 제공되는 즉시 사용됩니다. 인덱스가 아직 이전 버전의 애플리케이션에서 사용되지 않도록 되어 있는 경우 일반적으로 예약된 다운타임 동안 인덱스가 만들어집니다. 색인을 제거하거나 기존 색인을 변경할 때도 마찬가지입니다. 색인을 제거하면 해당 색인이 제거되는 즉시 사용할 수 없게 됩니다.

### 블루 그린 배포를 통한 색인 관리 {#index-management-with-blue-green-deployment}

블루-그린 배포를 통해 다운타임이 발생하지 않습니다. 그러나 색인 관리의 경우, 이렇게 하려면 인덱스가 특정 버전의 응용 프로그램에서만 사용되어야 합니다. 예를 들어 응용 프로그램 버전 2에서 인덱스를 추가할 때 응용 프로그램 버전 1에서 아직 사용하지 않도록 설정할 수 있습니다. 반대는 색인을 제거할 때의 경우입니다. 버전 1에서는 버전 2에서 제거된 색인이 여전히 필요합니다. 색인 정의를 변경할 때 이전 버전의 색인은 버전 1에서만 사용하고 새 버전의 색인은 버전 2에서만 사용할 수 있도록 하려고 합니다.

다음 표는 5개의 인덱스 정의를 보여 줍니다. index `cqPageLucene` 는 두 버전 모두에서 사용되지만 index `damAssetLucene-custom-1` 는 버전 2에서만 사용됩니다.

>[!NOTE]
>
>`<indexName>-custom-<customerVersionNumber>` 는 이 값을 기존 색인의 교체로 표시할 Cloud Service으로 AEM에 필요합니다.

| 색인 | 기본 색인 | 버전 1에서 사용 | 버전 2에서 사용 |
|---|---|---|---|
| /oak:index/damAssetLucene | 예 | 예 | 아니오 |
| /oak:index/damAssetLucene-custom-1 | 예(사용자 정의) | 아니오 | 예 |
| /oak:index/acme.product-custom-1 | 아니오 | 예 | 아니오 |
| /oak:index/acme.product-custom-2 | 아니오 | 아니오 | 예 |
| /oak:index/cqPageLucene | 예 | 예 | 예 |

색인이 변경될 때마다 버전 번호가 증가합니다. 사용자 정의 색인 이름이 제품 자체의 색인 이름, 사용자 정의 색인 및 기본 색인의 변경 사항과 충돌하는 것을 방지하려면 다음으로 끝나야 합니다 `-custom-<number>`.

### 기본 색인에 대한 변경 사항 {#changes-to-out-of-the-box-indexes}

Adobe이 &quot;damAssetLucene&quot; 또는 &quot;cqPageLucene&quot;과 같은 기본 색인, 이름이 `damAssetLucene-2` `cqPageLucene-2` 지정되거나 새로 만들어진 새로운 색인, 또는 인덱스가 이미 사용자 정의된 경우 사용자 지정된 인덱스 정의가 아래와 같이 기본 색인 변경 사항과 병합됩니다. 변경 내용 병합은 자동으로 수행됩니다. 즉, 기본 색인이 변경되면 아무 작업도 수행할 필요가 없습니다. 하지만 나중에 색인을 다시 사용자 지정할 수 있습니다.

| 색인 | 기본 색인 | 버전 2에서 사용 | 버전 3에서 사용 |
|---|---|---|---|
| /oak:index/damAssetLucene-custom-1 | 예(사용자 정의) | 예 | 아니오 |
| /oak:index/damAssetLucene-2-custom-1 | 예(damAssetLucene-custom-1 및 damAssetLucene-2에서 자동 병합) | 아니오 | 예 |
| /oak:index/cqPageLucene | 예 | 예 | 아니오 |
| /oak:index/cqPageLucene-2 | 예 | 아니오 | 예 |

### 제한 사항 {#limitations}

인덱스 관리는 현재 유형 색인에만 지원됩니다 `lucene`.

### 색인 제거 {#removing-an-index}

응용 프로그램의 이후 버전에서 인덱스를 제거하려는 경우 새 이름으로 빈 인덱스(인덱싱할 데이터가 없는 인덱스)를 정의할 수 있습니다. 예를 들어 이름을 지정할 수 있습니다 `/oak:index/acme.product-custom-3`. 색인이 바뀝니다 `/oak:index/acme.product-custom-2`. 시스템에서 `/oak:index/acme.product-custom-2` 제거되면 빈 색인도 제거할 `/oak:index/acme.product-custom-3` 수 있습니다.

### 색인 추가 {#adding-an-index}

응용 프로그램의 새 버전 이상에서 사용할 &quot;/oak:index/acme.product-custom-1&quot;이라는 인덱스를 추가하려면 다음과 같이 인덱스를 구성해야 합니다.

`acme.product-1-custom-1`

이 작업은 사용자 지정 식별자를 인덱스 이름에 사전 보류 중인 다음 점(**`.`**)으로 작동합니다. 식별자의 길이는 2자에서 5자 사이여야 합니다.

위와 같이, 이렇게 하면 인덱스가 응용 프로그램의 새 버전에서만 사용됩니다.

### 색인 변경 {#changing-an-index}

기존 색인이 변경되면 변경된 색인 정의와 함께 새 색인을 추가해야 합니다. 예를 들어 기존 인덱스 &quot;/oak:index/acme.product-custom-1&quot;이 변경되었다고 가정합니다. 이전 색인은 아래에 `/oak:index/acme.product-custom-1`저장되고 새 색인은 아래에 저장됩니다 `/oak:index/acme.product-custom-2`.

이전 버전의 응용 프로그램은 다음 구성을 사용합니다.

`/oak:index/acme.product-custom-1`

응용 프로그램의 새 버전에서는 다음(변경된) 구성을 사용합니다.

`/oak:index/acme.product-custom-2`
