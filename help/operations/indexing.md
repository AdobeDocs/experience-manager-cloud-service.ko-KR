---
title: 콘텐츠 검색 및 색인 지정
description: 콘텐츠 검색 및 색인 지정
exl-id: 4fe5375c-1c84-44e7-9f78-1ac18fc6ea6b
source-git-commit: 16afabcd80f9014684a5d3428a65d8b2c41c69c8
workflow-type: tm+mt
source-wordcount: '1829'
ht-degree: 2%

---

# 콘텐츠 검색 및 색인 지정 {#indexing}

## AEM에서 Cloud Service {#changes-in-aem-as-a-cloud-service}으로 변경

Cloud Service으로 AEM을 사용하는 Adobe은 Cloud Manager에서 CI/CD 파이프라인을 통해 제어되는 n-x AEM Containers를 사용하여 AEM 인스턴스 중심의 모델에서 서비스 기반의 보기로 전환하고 있습니다. 단일 AEM 인스턴스에서 인덱스를 구성하고 유지 관리하는 대신 배포 전에 색인 구성을 지정해야 합니다. 제작 과정의 구성 변화는 분명히 CI/CD 정책을 위반하는 것이다. 색인 변경 사항에도 동일하게 적용됩니다. 왜냐하면 색인 변경 사항은 프로덕션으로 가져오기 전에 테스트 및 재색인을 지정하지 않은 경우 시스템 안정성과 성능에 영향을 줄 수 있기 때문입니다.

다음은 AEM 6.5 및 이전 버전과 비교하여 주요 변경 사항 목록입니다.

1. 사용자는 더 이상 색인을 디버깅, 구성 또는 유지 관리할 단일 AEM 인스턴스의 색인 관리자에 액세스할 수 없습니다. 로컬 개발 및 On-Prem 배포에만 사용됩니다.

1. 사용자는 단일 AEM 인스턴스에서 색인을 변경하지 않으며, 일관성 확인 또는 재색인에 대해 더 이상 걱정할 필요가 없습니다.

1. 일반적으로, Cloud Manager CI/CD 파이프라인의 품질 게이트웨이를 우회하지 않고 제작 중인 비즈니스 KPI에 영향을 주지 않기 위해 제작 전에 색인 변경이 시작됩니다.

1. 검색 및 색인 항목에 대한 전체적인 보기를 제공하기 위해 제작 시 검색 성능을 비롯한 모든 관련 지표를 런타임에 고객에게 제공할 수 있습니다.

1. 고객은 필요에 따라 경고를 설정할 수 있습니다.

1. SRE는 24/7로 시스템 상태를 모니터링하고 필요에 따라 가능한 한 빨리 조치를 취할 것입니다.

1. 색인 구성은 배포를 통해 변경됩니다. 색인 정의 변경 사항은 다른 컨텐츠 변경과 같이 구성됩니다.

1. [블루-그린 배포 모델](#index-management-using-blue-green-deployments) 2개의 인덱스 세트가 소개되면서 AEM의 Cloud Service에서 높은 수준의 데이터가 제공됩니다.이전 버전에 대해 세트(파란색)를 설정하고 새 버전에 대해 세트(녹색)를 선택합니다.

1. 고객은 Cloud Manager 빌드 페이지에서 색인 작업이 완료되었는지 확인하고 새 버전이 트래픽을 받을 준비가 되면 알림을 받게 됩니다.

1. 제한 사항:현재 Cloud Service의 인덱스 관리는 lucene 유형의 색인에만 지원됩니다.

## 사용 방법 {#how-to-use}

색인을 정의하는 것은 다음 3가지 사용 사례 중 하나로 구성될 수 있습니다.

1. 새 고객 색인 정의 추가
1. 기존 색인 정의를 업데이트하는 중입니다. 이는 기존 색인 정의의 새 버전을 추가하는 것을 의미합니다
1. 중복되거나 사용되지 않는 기존 인덱스를 제거합니다.

위의 두 포인트 1 및 2의 경우, 각각의 Cloud Manager 릴리스 일정에 사용자 지정 코드 베이스의 일부로 새 색인 정의를 만들어야 합니다. 자세한 내용은 [Cloud Service 문서로 AEM에 배포를 참조하십시오](/help/implementing/deploying/overview.md).

### 새 색인 정의 준비 중 {#preparing-the-new-index-definition}

>[!NOTE]
>
>기본 색인을 사용자 지정하는 경우(예: `damAssetLucene-6`) *Cloud Service 환경*&#x200B;에서 최신 기본 색인 정의를 복사하고 사용자 지정을 맨 위에 추가하십시오. 이렇게 하면 필요한 구성이 실수로 제거되지 않습니다. 예를 들어 `/oak:index/damAssetLucene-6/tika` 아래의 `tika` 노드는 필수 노드이며 사용자 지정된 인덱스의 일부여야 하며 클라우드 SDK에 존재하지 않습니다.

다음 이름 지정 패턴을 따라 실제 색인 정의를 포함하는 새 인덱스 정의 패키지를 준비해야 합니다.

`<indexName>[-<productVersion>]-custom-<customVersion>`

그러면 `ui.apps/src/main/content/jcr_root` 아래로 이동해야 합니다. 현재 하위 루트 폴더는 지원되지 않습니다.

위 샘플의 패키지는 `com.adobe.granite:new-index-content:zip:1.0.0-SNAPSHOT`으로 빌드됩니다.

>[!NOTE]
>
>색인 정의를 포함하는 모든 콘텐츠 패키지는 `/META-INF/vault/properties.xml`에 있는 콘텐츠 패키지의 속성 파일에 다음 속성을 설정해야 합니다.
>
>`noIntermediateSaves=true`

### 인덱스 정의 배포 {#deploying-index-definitions}

>[!NOTE]
>
>`<packageType>application</packageType>`의 모듈에 `oak:index`를 추가할 수 없는 Jackrabbit Filevault Maven 패키지 플러그인 버전 **1.1.0**&#x200B;에 알려진 문제가 있습니다. 이 문제를 해결하려면 버전 **1.0.4**&#x200B;을 사용하십시오.

이제 색인 정의는 사용자 지정 및 버전으로 표시됩니다.

* 인덱스 정의 자체(예: `/oak:index/ntBaseLucene-custom-1`)

따라서 색인을 배포하려면 Git 및 Cloud Manager 배포 프로세스를 통해 인덱스 정의(`/oak:index/definitionname`)를 `ui.apps`로 전달해야 합니다.

새 색인 정의가 추가되면 새 응용 프로그램을 Cloud Manager를 통해 배포해야 합니다. 배포 시 작성자와 게시를 위해 각각 MongoDB 및 Azure 세그먼트 저장소에 인덱스 정의를 추가(필요한 경우 병합)하고 각각 병합해야 하는 2개의 작업이 시작됩니다. Blue-Green 스위치가 실행되기 전에 기본 리포지토리는 새 인덱스 정의로 재인덱싱됩니다.

>[!TIP]
>
>AEM의 필수 패키지 구조에 대한 Cloud Service에 대한 자세한 내용은 [AEM 프로젝트 구조 문서를 참조하십시오.](/help/implementing/developing/introduction/aem-project-content-package-structure.md)

## 파랑-녹색 배포를 사용하는 색인 관리 {#index-management-using-blue-green-deployments}

### 색인 관리란 무엇입니까 {#what-is-index-management}

색인 관리는 인덱스를 추가, 제거 및 변경하는 것입니다. 인덱스의 *정의*&#x200B;를 변경하는 것은 빠르지만 변경 사항을 적용(&quot;색인 작성&quot; 또는 기존 인덱스의 경우 &quot;다시 인덱싱&quot;이라고 함)하려면 시간이 필요합니다. 즉각적인 것은 아닙니다.데이터를 인덱싱하려면 저장소를 스캔해야 합니다.

### 파랑-녹색 배포란 무엇입니까 {#what-is-blue-green-deployment}

블루-그린 배포를 통해 다운타임을 줄일 수 있습니다. 또한 다운타임 없이 업그레이드할 수 있으며 빠른 롤백 기능을 제공합니다. 응용 프로그램의 이전 버전(파란색)은 응용 프로그램의 새 버전(녹색)과 동시에 실행됩니다.

### 읽기 전용 및 읽기 쓰기 영역 {#read-only-and-read-write-areas}

저장소의 특정 영역(저장소의 읽기 전용 부분)은 이전 버전(파란색)과 응용 프로그램의 새로운(녹색) 버전에서 다를 수 있습니다. 저장소의 읽기 전용 영역은 일반적으로 &quot;`/app`&quot; 및 &quot;`/libs`&quot;입니다. 다음 예에서 이탤릭체는 읽기 전용 영역을 표시하는 데 사용되지만, 굵은 기울임체는 읽기 쓰기 영역에 사용됩니다.

* **/**
* */apps(읽기 전용)*
* **/content**
* */libs(읽기 전용)*
* **/oak:index**
* **/oak:index/acme**
* **/jcr:system**
* **/system**
* **/var**

저장소의 읽기-쓰기 영역은 응용 프로그램의 모든 버전 간에 공유되지만 각 응용 프로그램 버전에 대해서는 `/apps` 및 `/libs` 특정 세트가 있습니다.

### 블루-그린 배포 없이 색인 관리 {#index-management-without-blue-green-deployment}

개발 중에 또는 사내 설치를 사용할 때 런타임에 색인을 추가, 제거 또는 변경할 수 있습니다. 색인은 제공되는 즉시 사용됩니다. 인덱스가 아직 이전 버전의 응용 프로그램에서 사용되지 않는 경우 일반적으로 예약된 다운타임 동안 인덱스가 만들어집니다. 색인을 제거하거나 기존 색인을 변경할 때도 마찬가지입니다. 색인을 제거하면 해당 색인이 제거되는 즉시 사용할 수 없게 됩니다.

### 파랑-녹색 배포를 사용하는 색인 관리 {#index-management-with-blue-green-deployment}

청록색 배포로 다운타임이 없습니다. 그러나 색인 관리의 경우 특정 버전의 응용 프로그램에서만 색인을 사용해야 합니다. 예를 들어 응용 프로그램 버전 2에서 인덱스를 추가할 때 아직 응용 프로그램 버전 1에서 사용하지 않도록 하려면 사용하지 마십시오. 반대로 색인이 제거되면 다음과 같은 상황이 발생합니다.버전 1에서는 버전 2에서 삭제된 색인이 계속 필요합니다. 색인 정의를 변경할 때 이전 버전의 인덱스는 버전 1에만 사용하고 새 버전의 인덱스는 버전 2에만 사용할 수 있도록 합니다.

다음 표는 5개의 인덱스 정의를 보여 줍니다.index `cqPageLucene`은(는) 두 버전 모두에서 사용되지만 인덱스 `damAssetLucene-custom-1`은(는) 버전 2에서만 사용됩니다.

>[!NOTE]
>
>`<indexName>-custom-<customerVersionNumber>` 는 이 항목을 기존 색인의 교체로 표시하는 Cloud Service의 경우 필요합니다.

| 색인 | 기본 색인 | 버전 1에서 사용 | 버전 2에서 사용 |
|---|---|---|---|
| /oak:index/damAssetLucene | 예 | 예 | 아니오 |
| /oak:index/damAssetLucene-custom-1 | 예(사용자 정의) | 아니오 | 예 |
| /oak:index/acme.product-custom-1 | 아니오 | 예 | 아니오 |
| /oak:index/acme.product-custom-2 | 아니오 | 아니오 | 예 |
| /oak:index/cqPageLucene | 예 | 예 | 예 |

색인이 변경될 때마다 버전 번호가 증가합니다. 사용자 정의 인덱스 이름이 제품 자체의 인덱스 이름과 충돌하지 않도록 하려면 사용자 정의 인덱스와 기본 인덱스의 변경 사항은 `-custom-<number>`로 끝나야 합니다.

### 기본 색인 변경 사항 {#changes-to-out-of-the-box-indexes}

Adobe이 &quot;damAssetLucene&quot; 또는 &quot;cqPageLucene&quot;과 같은 기본 색인을 변경했으면, `damAssetLucene-2` 또는 `cqPageLucene-2`이라는 새 인덱스가 만들어지거나, 인덱스가 이미 사용자 정의된 경우, 사용자 지정된 색인 정의는 아래와 같이 기본 색인의 변경 사항과 병합됩니다. 변경 내용 병합은 자동으로 수행됩니다. 즉, 기본 색인이 변경되면 아무 작업도 수행할 필요가 없습니다. 하지만 나중에 색인을 다시 사용자 지정할 수 있습니다.

| 색인 | 기본 색인 | 버전 2에서 사용 | 버전 3에서 사용 |
|---|---|---|---|
| /oak:index/damAssetLucene-custom-1 | 예(사용자 정의) | 예 | 아니오 |
| /oak:index/damAssetLucene-2-custom-1 | 예(damAssetLucene-custom-1 및 damAssetLucene-2에서 자동으로 병합) | 아니오 | 예 |
| /oak:index/cqPageLucene | 예 | 예 | 아니오 |
| /oak:index/cqPageLucene-2 | 예 | 아니오 | 예 |

### 현재 제한 사항 {#current-limitations}

인덱스 관리는 현재 `lucene` 유형의 색인에만 지원됩니다.

### 인덱스 {#adding-an-index} 추가

응용 프로그램의 새 버전 이상에서 사용할 `/oak:index/acme.product-custom-1`이라는 인덱스를 추가하려면 다음과 같이 인덱스를 구성해야 합니다.

`acme.product-1-custom-1`

이 작업은 색인 이름에 사용자 지정 식별자를 미리 대기시킨 다음 점(**`.`**)을 추가합니다. 식별자의 길이는 2자에서 5자 사이여야 합니다.

위와 같이, 이렇게 하면 인덱스가 응용 프로그램의 새 버전에서만 사용됩니다.

### 인덱스 {#changing-an-index} 변경

기존 색인이 변경되면 변경된 색인 정의와 함께 새 인덱스를 추가해야 합니다. 예를 들어 기존 인덱스 `/oak:index/acme.product-custom-1`이(가) 변경되었다고 가정합니다. 이전 인덱스는 `/oak:index/acme.product-custom-1` 아래에 저장되고 새 인덱스는 `/oak:index/acme.product-custom-2` 아래에 저장됩니다.

이전 버전의 응용 프로그램은 다음 구성을 사용합니다.

`/oak:index/acme.product-custom-1`

응용 프로그램의 새 버전에서는 다음(변경된) 구성을 사용합니다.

`/oak:index/acme.product-custom-2`

>[!NOTE]
>
>Cloud Service의 인덱스 정의가 로컬 개발 인스턴스의 인덱스 정의와 완전히 일치하지 않을 수 있습니다. 개발 인스턴스에는 Tika 구성이 없지만 Cloud Service 인스턴스에는 Tika 구성이 있습니다. Tika 구성을 사용하여 인덱스를 사용자 지정하는 경우 Tika 구성을 유지하십시오.

### 변경 {#undoing-a-change} 취소

경우에 따라 색인 정의의 변경 사항을 되돌려야 합니다. 그 이유는 실수로 변경되었거나 더 이상 변경이 필요하지 않기 때문일 수 있습니다. 예를 들어 인덱스 정의 `damAssetLucene-8-custom-3`이(가) 실수로 만들어졌고 이미 배포되었습니다. 그 때문에 이전 색인 정의 `damAssetLucene-8-custom-2`으로 되돌릴 수 있습니다. 이렇게 하려면 이전 인덱스 `damAssetLucene-8-custom-2`의 정의가 포함된 `damAssetLucene-8-custom-4`이라는 새 인덱스를 추가해야 합니다.

### 인덱스 {#removing-an-index} 제거

다음은 사용자 정의 색인에만 적용됩니다. 제품 색인은 AEM에서 사용되므로 제거할 수 없습니다.

응용 프로그램의 이후 버전에서 인덱스를 제거하려는 경우 새 이름으로 빈 인덱스(사용되지 않고 데이터를 포함하지 않는 빈 인덱스)를 정의할 수 있습니다. 이 예제의 목적을 위해 이름을 `/oak:index/acme.product-custom-3`으로 지정할 수 있습니다. 인덱스 `/oak:index/acme.product-custom-2`을 대체합니다. 시스템에서 `/oak:index/acme.product-custom-2`을(를) 제거했으면 빈 인덱스 `/oak:index/acme.product-custom-3`도 제거할 수 있습니다. 이러한 빈 인덱스의 예는 다음과 같습니다.

```xml
<acme.product-custom-3
        jcr:primaryType="oak:QueryIndexDefinition"
        async="async"
        compatVersion="2"
        includedPaths="/dummy"
        queryPaths="/dummy"
        type="lucene">
        <indexRules jcr:primaryType="nt:unstructured">
            <rep:root jcr:primaryType="nt:unstructured">
                <properties jcr:primaryType="nt:unstructured">
                    <dummy
                        jcr:primaryType="nt:unstructured"
                        name="dummy"
                        propertyIndex="{Boolean}true"/>
                </properties>
            </rep:root>
        </indexRules>
    </acme.product-custom-3>
```

기본 색인을 사용자 지정할 필요가 없는 경우 기본 색인 정의를 복사해야 합니다. 예를 들어 이미 `damAssetLucene-8-custom-3`을(를) 배포했지만 더 이상 사용자 정의가 필요하지 않고 기본 `damAssetLucene-8` 인덱스로 다시 전환하려는 경우 `damAssetLucene-8`의 인덱스 정의가 포함된 `damAssetLucene-8-custom-4` 인덱스를 추가해야 합니다.

### 인덱스 가용성 및 내결함성 {#index-availability-and-fault-tolerance}

색인 손상이나 그러한 예상치 못한 이벤트의 경우 중요한 기능에 대한 중복 인덱스를 만드는 것이 좋습니다(위에 언급된 색인에 대한 이름 지정 규칙 준수).
