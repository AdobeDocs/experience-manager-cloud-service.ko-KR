---
title: 콘텐츠 검색 및 색인 지정
description: 콘텐츠 검색 및 색인 지정
exl-id: 4fe5375c-1c84-44e7-9f78-1ac18fc6ea6b
source-git-commit: eae25dc48a7cd5d257e23b515f497588a13917ea
workflow-type: tm+mt
source-wordcount: '1780'
ht-degree: 2%

---

# 콘텐츠 검색 및 색인 지정 {#indexing}

## AEM as a Cloud Service {#changes-in-aem-as-a-cloud-service} 의 변경 사항

AEM as a Cloud Service을 통해 Adobe은 AEM 인스턴스 중심의 모델에서 Cloud Manager의 CI/CD 파이프라인에 의해 구동되는 n-x AEM 컨테이너가 있는 서비스 기반 보기로 이동하고 있습니다. 단일 AEM 인스턴스에서 인덱스를 구성하고 유지 관리하는 대신 배포 전에 인덱스 구성을 지정해야 합니다. 프로덕션의 구성 변경은 분명히 CI/CD 정책을 위반하는 것입니다. 인덱스 변경 내용은 시스템 안정성 및 성능에 영향을 줄 수 있으므로 테스트 및 재색인화를 지정하지 않은 경우 프로덕션으로 가져오기 전에 적용됩니다.

다음은 AEM 6.5 및 이전 버전과 비교하여 주요 변경 사항 목록입니다.

1. 사용자는 더 이상 색인을 디버그, 구성 또는 유지 관리하기 위해 단일 AEM 인스턴스의 색인 관리자에 액세스할 수 없습니다. 로컬 개발 및 온-프레미스 배포에만 사용됩니다.

1. 사용자는 단일 AEM 인스턴스에서 인덱스를 변경하지 않으며 더 이상 일관성 검사 또는 재색인에 대해 걱정할 필요가 없습니다.

1. 일반적으로 Cloud Manager CI/CD 파이프라인의 품질 게이트웨이를 우회하지 않고 프로덕션의 비즈니스 KPI에 영향을 주지 않기 위해 프로덕션으로 이동하기 전에 인덱스 변경이 시작됩니다.

1. 런타임 시 고객이 검색 및 색인 지정 항목에 대한 전체적인 보기를 제공하기 위해 프로덕션의 검색 성능을 포함한 모든 관련 지표를 사용할 수 있습니다.

1. 고객은 필요에 따라 경고를 설정할 수 있습니다.

1. SRE는 시스템 상태24/7 모니터링하며 필요에 따라 가능한 한 빨리 조치를 취할 것입니다.

1. 색인 구성은 배포를 통해 변경됩니다. 색인 정의 변경 사항은 다른 컨텐츠 변경 사항과 같이 구성됩니다.

1. AEM as a Cloud Service의 높은 수준에서 [Blue-Green 배포 모델](#index-management-using-blue-green-deployments) 두 개의 인덱스 세트가 존재합니다.이전 버전(파란색)에 대해 한 세트, 새 버전에 대해 한 세트(녹색)를 설정합니다.

1. 고객은 Cloud Manager 빌드 페이지에서 색인 작업이 완료되었는지 확인하고 새 버전에서 트래픽을 받을 준비가 되면 알림을 받게 됩니다.

1. 제한 사항:현재 AEM as a Cloud Service의 인덱스 관리는 lucene 유형의 색인에만 지원됩니다.

## 사용 방법 {#how-to-use}

인덱스를 정의하는 것은 다음 세 가지 사용 사례 중 하나일 수 있습니다.

1. 새 고객 색인 정의 추가
1. 기존 인덱스 정의를 업데이트하는 중입니다. 이는 기존 인덱스 정의의 새 버전을 추가하는 것을 의미합니다
1. 중복되거나 사용되지 않는 기존 인덱스를 제거하는 중입니다.

위의 두 지점 모두에 대해, 각각의 Cloud Manager 릴리스 일정에서 사용자 지정 코드 베이스의 일부로 새 인덱스 정의를 생성해야 합니다. 자세한 내용은 [AEM as a Cloud Service 설명서](/help/implementing/deploying/overview.md)를 참조하십시오.

### 새 인덱스 정의 준비 중 {#preparing-the-new-index-definition}

>[!NOTE]
>
>기본 인덱스(예: `damAssetLucene-6`)를 사용자 지정하는 경우 *Cloud Service 환경*&#x200B;에서 최신 인덱스 정의를 기본 제공 복사하여 맨 위에 사용자 지정 항목을 추가하면 필요한 구성이 실수로 제거되지 않습니다. 예를 들어 `/oak:index/damAssetLucene-6/tika` 아래의 `tika` 노드는 필수 노드이며 사용자 지정된 색인의 일부여야 하며, Cloud SDK에 존재하지 않습니다.

다음 이름 지정 패턴에 따라 실제 인덱스 정의가 포함된 새 인덱스 정의 패키지를 준비해야 합니다.

`<indexName>[-<productVersion>]-custom-<customVersion>`

이 작업은 `ui.apps/src/main/content/jcr_root` 아래에 와야 합니다. 현재는 하위 루트 폴더가 지원되지 않습니다.

위의 샘플의 패키지는 `com.adobe.granite:new-index-content:zip:1.0.0-SNAPSHOT`로 빌드됩니다.

>[!NOTE]
>
>인덱스 정의를 포함하는 컨텐츠 패키지는 컨텐츠 패키지의 속성 파일에 `/META-INF/vault/properties.xml`에 있는 다음 속성을 설정해야 합니다.
>
>`noIntermediateSaves=true`

### 인덱스 정의 배포 {#deploying-index-definitions}

>[!NOTE]
>
>Jackrabbit Filerabbit Maven 패키지 플러그인 버전 **1.1.0**&#x200B;에 대해 알려진 문제로, `<packageType>application</packageType>`의 모듈에 `oak:index`를 추가할 수 없습니다. 이 문제를 해결하려면 버전 **1.0.4**&#x200B;을 사용하십시오.

이제 색인 정의가 사용자 정의 및 버전이 지정됨으로 표시됩니다.

* 인덱스 정의 자체(예: `/oak:index/ntBaseLucene-custom-1`)

따라서 인덱스를 배포하려면 Git 및 Cloud Manager 배포 프로세스를 통해 `ui.apps` 를(를) 통해 인덱스 정의(`/oak:index/definitionname`)를 전달해야 합니다.

새 인덱스 정의를 추가하면 Cloud Manager를 통해 새 애플리케이션을 배포해야 합니다. 배포 시 작성자와 게시를 위해 각각 MongoDB 및 Azure 세그먼트 저장소에 인덱스 정의를 추가(및 필요한 경우 병합)할 책임이 있는 두 개의 작업이 시작됩니다. Blue-Green 스위치가 수행되기 전에 기본 리포지토리는 새 인덱스 정의로 다시 인덱싱됩니다.

>[!TIP]
>
>AEM as a Cloud Service에 필요한 패키지 구조에 대한 자세한 내용은 [AEM 프로젝트 구조 문서를 참조하십시오.](/help/implementing/developing/introduction/aem-project-content-package-structure.md)

## 파랑-녹색 배포를 사용한 색인 관리 {#index-management-using-blue-green-deployments}

### 인덱스 관리란 무엇입니까? {#what-is-index-management}

인덱스 관리는 인덱스를 추가, 제거 및 변경하는 것입니다. 인덱스의 *정의*&#x200B;를 변경하는 것은 빠르지만 변경(종종 &quot;색인 작성&quot;이라고 함) 또는 기존 인덱스의 경우 &quot;다시 인덱싱&quot;이라고 함)을 적용하려면 시간이 필요합니다. 순간적이지 않습니다.데이터를 인덱싱하려면 리포지토리를 검사해야 합니다.

### 파랑-녹색 배포란 무엇입니까? {#what-is-blue-green-deployment}

블루-그린 배포를 통해 다운타임을 줄일 수 있습니다. 또한 다운타임 없이 업그레이드할 수 있으며 빠른 롤백 기능을 제공합니다. 애플리케이션의 이전 버전(파란색)은 새 애플리케이션 버전(녹색)과 동시에 실행됩니다.

### 읽기 전용 및 읽기-쓰기 영역 {#read-only-and-read-write-areas}

저장소의 특정 영역(리포지토리의 읽기 전용 부분)은 이전 버전(파란색)과 새로운 애플리케이션(녹색) 버전에서 다를 수 있습니다. 저장소의 읽기 전용 영역은 일반적으로 &quot;`/app`&quot; 및 &quot;`/libs`&quot;입니다. 다음 예제에서는 기울임꼴은 읽기 전용 영역을 표시하는 데 사용되고 읽기-쓰기 영역에는 굵게 사용됩니다.

* **/**
* */apps(읽기 전용)*
* **/content**
* */libs(읽기 전용)*
* **/oak:index**
* **/oak:index/acme입니다.**
* **/jcr:system**
* **/system**
* **/var**

저장소의 읽기-쓰기 영역은 응용 프로그램의 모든 버전 간에 공유되지만 각 응용 프로그램 버전에 대해 특정 `/apps` 및 `/libs` 세트가 있습니다.

### 파란색-녹색 배포가 없는 인덱스 관리 {#index-management-without-blue-green-deployment}

개발 중 또는 온-프레미스 설치를 사용할 때 런타임 시 인덱스를 추가, 제거 또는 변경할 수 있습니다. 색인은 가능한 한 빨리 사용됩니다. 인덱스가 아직 이전 버전의 응용 프로그램에서 사용되어야 하는 경우에는 일반적으로 예약된 다운타임에 인덱스를 만듭니다. 인덱스를 제거하거나 기존 인덱스를 변경할 때에도 같은 현상이 발생합니다. 인덱스를 제거하면 제거되는 즉시 사용할 수 없게 됩니다.

### 파랑-녹색 배포가 있는 인덱스 관리 {#index-management-with-blue-green-deployment}

청록 배포로 다운타임이 발생하지 않습니다. 그러나 인덱스 관리를 위해서는 특정 버전의 응용 프로그램에서만 인덱스를 사용해야 합니다. 예를 들어 애플리케이션 버전 2에서 인덱스를 추가할 때 아직 애플리케이션 버전 1에서 사용하지 않도록 설정할 수 있습니다. 반대는 인덱스가 제거될 때 발생합니다.버전 1에서는 버전 2에서 제거된 인덱스가 계속 필요합니다. 인덱스 정의를 변경할 때 인덱스의 이전 버전은 버전 1에만 사용하고 새로운 버전의 인덱스는 버전 2에만 사용하려는 것입니다.

다음 표에는 5개의 인덱스 정의가 나와 있습니다.index `cqPageLucene`은 두 버전에서 사용되지만 index `damAssetLucene-custom-1`은 버전 2에서만 사용됩니다.

>[!NOTE]
>
>`<indexName>-custom-<customerVersionNumber>` 는 AEM을 기존 색인의 교체로 표시할 Cloud Service으로 사용해야 합니다.

| 색인 | 기본 인덱스 | 버전 1에서 사용 | 버전 2에서 사용 |
|---|---|---|---|
| /oak:index/damAssetLucene | 예 | 예 | 아니오 |
| /oak:index/damAssetLucene-custom-1 | 예(사용자 지정) | 아니오 | 예 |
| /oak:index/acme.product-custom-1 | 아니오 | 예 | 아니오 |
| /oak:index/acme.product-custom-2 | 아니오 | 아니오 | 예 |
| /oak:index/cqPageLucene | 예 | 예 | 예 |

색인이 변경될 때마다 버전 번호가 증가합니다. 사용자 지정 인덱스 이름이 제품 자체의 인덱스 이름과 충돌하는 것을 방지하려면 사용자 지정 인덱스 및 기본 제공 인덱스에 대한 변경 사항은 `-custom-<number>`로 끝나야 합니다.

### 기본 인덱스 {#changes-to-out-of-the-box-indexes} 변경

Adobe이 &quot;damAssetLucene&quot; 또는 &quot;cqPageLucene&quot;과 같은 기본 인덱스를 변경하고 나면 `damAssetLucene-2` 또는 `cqPageLucene-2`이라는 새 인덱스가 만들어지거나, 인덱스가 이미 사용자 지정된 경우 사용자 지정된 인덱스 정의가 아래와 같이 기본 색인의 변경 사항과 병합됩니다. 변경 내용의 병합은 자동으로 수행됩니다. 즉, 기본 인덱스가 변경되는 경우 아무 작업도 수행할 필요가 없습니다. 그러나 나중에 인덱스를 다시 사용자 지정할 수 있습니다.

| 색인 | 기본 인덱스 | 버전 2에서 사용 | 버전 3에서 사용 |
|---|---|---|---|
| /oak:index/damAssetLucene-custom-1 | 예(사용자 지정) | 예 | 아니오 |
| /oak:index/damAssetLucene-2-custom-1 | 예(damAssetLucene-custom-1 및 damAssetLucene-2에서 자동으로 병합됨) | 아니오 | 예 |
| /oak:index/cqPageLucene | 예 | 예 | 아니오 |
| /oak:index/cqPageLucene-2 | 예 | 아니오 | 예 |

### 현재 제한 사항 {#current-limitations}

인덱스 관리는 현재 `lucene` 유형의 인덱스에만 지원됩니다.

### 인덱스 {#adding-an-index} 추가

응용 프로그램의 새 버전에서 사용할 `/oak:index/acme.product-custom-1` 인덱스를 추가하려면 다음과 같이 인덱스를 구성해야 합니다.

`acme.product-1-custom-1`

이 작업은 인덱스 이름에 사용자 지정 식별자를 미리 적용한 후 점(**`.`**)을 추가합니다. 식별자의 길이는 2자에서 5자 사이여야 합니다.

위와 같이, 이렇게 하면 인덱스가 새로운 버전의 응용 프로그램에서만 사용됩니다.

### 인덱스 {#changing-an-index} 변경

기존 인덱스를 변경하면 변경된 인덱스 정의로 새 인덱스를 추가해야 합니다. 예를 들어 기존 인덱스 `/oak:index/acme.product-custom-1`이 변경되었다고 가정하십시오. 이전 색인은 `/oak:index/acme.product-custom-1` 아래에 저장되고 새 색인은 `/oak:index/acme.product-custom-2` 아래에 저장됩니다.

이전 버전의 응용 프로그램은 다음 구성을 사용합니다.

`/oak:index/acme.product-custom-1`

응용 프로그램의 새 버전에서는 다음(변경된) 구성을 사용합니다.

`/oak:index/acme.product-custom-2`

>[!NOTE]
>
>AEM as a Cloud Service의 인덱스 정의가 로컬 개발 인스턴스의 인덱스 정의와 완전히 일치하지 않을 수 있습니다. 개발 인스턴스에는 Tika 구성이 없고, AEM as a Cloud Service 인스턴스에는 Tika 구성이 있습니다. Tika 구성을 사용하여 인덱스를 사용자 지정하는 경우 Tika 구성을 유지하십시오.

### 변경 취소 {#undoing-a-change}

경우에 따라 인덱스 정의의 변경 사항을 되돌려야 합니다. 이유는 실수로 변경했거나 변경이 더 이상 필요하지 않기 때문일 수 있습니다. 예를 들어 인덱스 정의 `damAssetLucene-8-custom-3`이(가) 실수로 생성되었으며 이미 배포되었습니다. 이러한 이유로 이전 인덱스 정의 `damAssetLucene-8-custom-2`로 되돌릴 수 있습니다. 이렇게 하려면 이전 인덱스 `damAssetLucene-8-custom-2`의 정의를 포함하는 새 인덱스 `damAssetLucene-8-custom-4`를 추가해야 합니다.

### 인덱스 {#removing-an-index} 제거

다음은 사용자 지정 색인에만 적용됩니다. 제품 색인은 AEM에서 사용하므로 제거할 수 없습니다.

이후 버전의 응용 프로그램에서 인덱스를 제거할 경우 새 이름으로 빈 인덱스(사용되지 않고 데이터를 포함하지 않는 빈 인덱스)를 정의할 수 있습니다. 이 예제의 목적을 위해 이름을 `/oak:index/acme.product-custom-3`으로 지정할 수 있습니다. 이렇게 하면 색인 `/oak:index/acme.product-custom-2`이 교체됩니다. 시스템에 의해 `/oak:index/acme.product-custom-2`이 제거되면 빈 인덱스 `/oak:index/acme.product-custom-3`도 제거할 수 있습니다. 이러한 빈 인덱스의 예는 다음과 같습니다.

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

기본 인덱스의 사용자 지정이 더 이상 필요하지 않으면 기본 인덱스 정의를 복사해야 합니다. 예를 들어 `damAssetLucene-8-custom-3`을 이미 배포했지만 더 이상 사용자 지정 항목이 필요하지 않고 기본 `damAssetLucene-8` 인덱스로 다시 전환하려면 `damAssetLucene-8`의 인덱스 정의를 포함하는 `damAssetLucene-8-custom-4` 인덱스를 추가해야 합니다.
