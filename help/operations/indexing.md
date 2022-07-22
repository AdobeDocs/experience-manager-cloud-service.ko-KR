---
title: 콘텐츠 검색 및 색인 지정
description: 콘텐츠 검색 및 색인 지정
exl-id: 4fe5375c-1c84-44e7-9f78-1ac18fc6ea6b
source-git-commit: 1544358f9a706574d8944fa92422240c46d62d2f
workflow-type: tm+mt
source-wordcount: '2253'
ht-degree: 88%

---

# 콘텐츠 검색 및 색인 지정 {#indexing}

## AEM as a Cloud Service의 변경 내용 {#changes-in-aem-as-a-cloud-service}

AEM as a Cloud Service를 통해 Adobe는 AEM 인스턴스 중심 모델에서 Cloud Manager의 CI/CD 파이프라인 기반 n-x AEM 컨테이너를 사용하는 서비스 중심 보기로 이전하는 중입니다. 단일 AEM 인스턴스의 색인을 구성 및 유지하는 대신 배포 전 색인 구성을 지정해야 합니다. 프로덕션의 구성을 변경하면 CI/CD 정책을 위반하게 됩니다. 프로덕션으로 가져오기 전에 지정, 테스트 및 색인 재지정을 하지 않은 경우 시스템 안정성과 성능에 영향을 줄 수 있기 때문에 색인 변경에도 똑같이 적용됩니다.

다음은 AEM 6.5 및 이전 버전과 비교한 주요 변경 사항 목록입니다.

1. 사용자는 색인 지정을 디버그, 구성 또는 유지하기 위해 단일 AEM 인스턴스의 색인 관리자에 액세스할 권한이 더 이상 없습니다. 로컬 개발 및 온프레미스 배포에 대해서만 사용됩니다.

1. 사용자는 단일 AEM 인스턴스의 색인을 변경하지 못하거나 일관성 확인 또는 색인 재지정에 대해 더 이상 걱정하지 않아도 됩니다.

1. 일반적으로 프로덕션 진행 전 색인 변경을 초기화해 Cloud Manager CI/CD 파이프라인의 품질 게이트웨이를 피하지 않도록 하고 프로덕션의 비즈니스 KPI에 영향을 주지 않도록 합니다.

1. 검색과 색인 지정의 주제에 대한 거시적으로 볼 수 있도록 런타임 시 프로덕션의 검색 성능 등 모든 관련 지수를 고객이 사용할 수 있습니다.

1. 고객은 자신들의 필요에 따라 알람을 설정할 수 있습니다.

1. SRE는 시스템 상태를 연중무휴 모니터링하며 필요할 때 가능한 빨리 조치를 취합니다.

1. 색인 구성은 배포를 통해 변경됩니다. 색인 정의 변경은 다른 콘텐츠 변경과 같은 방식으로 구성됩니다.

1. [파란색-녹색 배포 모델](#index-management-using-blue-green-deployments)을 도입해 AEM as a Cloud Service의 고레벨에는 두 세트의 색인이 존재합니다. 한 세트는 이전 버전(파란색), 다른 한 세트는 새 버전(녹색)입니다.

1. 고객은 Cloud Manager 빌드 페이지에서 색인 지정 작업이 완료되었는지 여부를 확인할 수 있으며 새 버전이 트래픽을 가져올 수 있게 되면 알림을 받게 됩니다.

1. 제한 사항:
* 현재 AEM as a Cloud Service의 색인 관리는 `lucene` 색인 유형만 지원됩니다.
* 표준 분석기만 지원됩니다(제품으로 제공되는 분석기). 사용자 정의 분석기는 지원되지 않습니다.
* 내부적으로 다른 색인을 구성하고 쿼리에 사용할 수 있습니다. 예를 들어, `damAssetLucene` 색인에 대해 작성된 Skyline의 쿼리는 이 색인의 Elasticsearch 버전에 대해 실행됩니다. 이 차이는 일반적으로 애플리케이션과 사용자에게는 표시되지 않지만 `explain` 기능과 같은 특정 도구에서는 다른 색인임을 보고합니다. Lucene 색인과 Elastic 색인의 차이에 대해서는 [Apache Jackrabbit Oak의 Elastic 설명서](https://jackrabbit.apache.org/oak/docs/query/elastic.html)를 참조하십시오. 고객은 Elasticsearch 색인을 직접 구성할 필요가 없으며 구성할 수 없습니다.

## 사용 방법 {#how-to-use}

색인 정의는 다음의 세 가지 사용 사례로 구성될 수 있습니다.

1. 새 고객 색인 정의 추가.
1. 기존의 색인 정의 업데이트. 기존의 색인 정의에 대한 새 버전이 추가된다는 의미입니다.
1. 중복 또는 사용하지 않는 기존의 색인 삭제.

위의 1번과 2번은 각각 Cloud Manager 릴리스 일정에서 사용자 정의 코드 기반의 일부로 새 색인 정의를 생성해야 합니다. 자세한 내용은 [AEM as a Cloud Service에 배포 설명서](/help/implementing/deploying/overview.md)를 참조하십시오.

## 색인 이름 {#index-names}

색인 정의는 다음 중 하나일 수 있습니다.

1. 기본 제공 색인. 예: `/oak:index/cqPageLucene-2`
1. 기본 제공 색인의 사용자 정의. 이러한 사용자 정의는 고객이 정의합니다. 예: `/oak:index/cqPageLucene-2-custom-1`
1. 완전히 맞춤화된 색인. 예: `/oak:index/acme.product-1-custom-2`. 이름 지정에서 충돌하지 않도록 완전히 맞춤화된 색인에는 접두사(예: `acme.`)를 사용해야 합니다.

기본 제공 색인의 사용자 정의와 완전히 맞춤화된 색인에는 모두 `-custom-`이 포함되어야 합니다. 완전히 맞춤화된 색인만 접두사로 시작합니다.

## 새 색인 정의 준비 {#preparing-the-new-index-definition}

>[!NOTE]
>
>기본 인덱스를 사용자 지정하는 경우(예: ) `damAssetLucene-6`에서 최신 기본 인덱스 정의를 복사하십시오 *Cloud Service 환경* crx DE 패키지 관리자 사용(`/crx/packmgr/`). 그 다음 `damAssetLucene-6-custom-1`과 같이 구성의 이름을 바꾸고 상단에 사용자 정의를 추가합니다. 이렇게 하면 필요한 구성이 실수로 지워지지 않도록 할 수 있습니다. 예를 들어 `/oak:index/damAssetLucene-6/tika`의 `tika` 노드는 클라우드 서비스의 맞춤화된 색인에 필요합니다. Cloud SDK에는 없습니다.

이 이름 지정 패턴에 따라 실제 색인 정의가 포함된 새 색인 정의 패키지를 준비해야 합니다.

`<indexName>[-<productVersion>]-custom-<customVersion>`

그런 후 `ui.apps/src/main/content/jcr_root`로 전환해야 합니다. 사용자 지정 및 사용자 지정 인덱스 정의는 모두 아래에 저장해야 합니다 `/oak:index`.

기존 색인(기본 제공 색인)이 유지되고 있는 것과 같이 패키지의 필터를 설정해야 합니다. 파일에서 `ui.apps/src/main/content/META-INF/vault/filter.xml`, 각 사용자 지정(또는 사용자 지정) 인덱스를 나열해야 합니다(예: ). `<filter root="/oak:index/damAssetLucene-6-custom-1"/>`. 인덱스 버전을 나중에 변경하면 필터를 조정해야 합니다.

위 샘플의 패키지는 `com.adobe.granite:new-index-content:zip:1.0.0-SNAPSHOT`(으)로 작성됩니다.

>[!NOTE]
>
>색인 정의가 포함된 모든 콘텐츠 패키지는 `/META-INF/vault/properties.xml`에 있는 콘텐츠 패키지의 속성 파일에 다음 속성으로 설정되어야 합니다.
>
>`noIntermediateSaves=true`

## 색인 정의 배포 {#deploying-index-definitions}

색인 정의는 사용자 정의 및 버전이 지정됨으로 표시됩니다.

* 색인 정의 자체(예: `/oak:index/ntBaseLucene-custom-1`)

사용자 지정 또는 사용자 지정 인덱스를 배포하려면 인덱스 정의(`/oak:index/definitionname`)을 전달해야 합니다. `ui.apps` Git 및 Cloud Manager 배포 프로세스를 통해 다음을 수행할 수 있습니다. FileVault 필터에서(예: ) `ui.apps/src/main/content/META-INF/vault/filter.xml`, 각 사용자 지정 및 사용자 지정 인덱스를 개별적으로 나열하십시오(예: ) `<filter root="/oak:index/damAssetLucene-7-custom-1"/>`. 사용자 지정/사용자 지정된 인덱스 정의 자체가 파일에 저장됩니다 `ui.apps/src/main/content/jcr_root/_oak_index/damAssetLucene-7-custom-1/.content.xml`를 채울 수 있습니다.

```xml
<?xml version="1.0" encoding="UTF-8"?>
<jcr:root xmlns:oak="http://jackrabbit.apache.org/oak/ns/1.0" xmlns:dam="http://www.day.com/dam/1.0" xmlns:jcr="http://www.jcp.org/jcr/1.0" xmlns:nt="http://www.jcp.org/jcr/nt/1.0" xmlns:rep="internal"
        jcr:primaryType="oak:QueryIndexDefinition"
        async="[async,nrt]"
        compatVersion="{Long}2"
        ...
        </indexRules>
        <tika jcr:primaryType="nt:unstructured">
            <config.xml jcr:primaryType="nt:file"/>
        </tika>
</jcr:root>
```

위의 예에는 Apache Tika에 대한 구성이 포함되어 있습니다. Tika 구성 파일은 `ui.apps/src/main/content/jcr_root/_oak_index/damAssetLucene-7-custom-1/tika/config.xml`.

### 프로젝트 구성

사용되는 Jackrabbit Filerabbit Maven 패키지 플러그인의 버전에 따라 프로젝트에서의 몇 가지 추가 구성이 필요합니다. Jackrabbit Filerabbit Maven 패키지 플러그인 버전을 사용할 때 **1.1.6** 또는 그 이상인 경우 `pom.xml` 는 다음에 대한 플러그인 구성에 다음 섹션을 포함해야 합니다. `filevault-package-maven-plugin`, in `configuration/validatorsSettings` (바로 그 전에) `jackrabbit-nodetypes`):

```xml
<jackrabbit-packagetype>
    <options>
        <immutableRootNodeNames>apps,libs,oak:index</immutableRootNodeNames>
    </options>
</jackrabbit-packagetype>
```

또한 이 경우 `vault-validation` 버전을 최신 버전으로 업그레이드해야 합니다.

```xml
<dependency>
    <groupId>org.apache.jackrabbit.vault</groupId>
    <artifactId>vault-validation</artifactId>
    <version>3.5.6</version>
</dependency>
```

그런 다음 `ui.apps.structure/pom.xml` 및 `ui.apps/pom.xml`, 의 구성 `filevault-package-maven-plugin` 다음을 수행해야 함 `allowIndexDefinitions` 뿐만 아니라 `noIntermediateSaves` 활성화되었습니다. 옵션 `noIntermediateSaves` 인덱스 구성이 자동으로 추가되도록 합니다.

```xml
<groupId>org.apache.jackrabbit</groupId>
    <artifactId>filevault-package-maven-plugin</artifactId>
    <configuration>
        <allowIndexDefinitions>true</allowIndexDefinitions>
        <properties>
            <cloudManagerTarget>none</cloudManagerTarget>
            <noIntermediateSaves>true</noIntermediateSaves>
        </properties>
    ...
```

in `ui.apps.structure/pom.xml`, `filters` 이 플러그인의 섹션은 다음과 같이 필터 루트를 포함해야 합니다.

```xml
<filter><root>/oak:index</root></filter>
```

새 색인 정의가 추가되면 새 애플리케이션이 Cloud Manager를 통해 배포되어야 합니다. 배포되면 두 개의 작업이 시작되어 색인 정의를 MongoDB와 Azure Segment Store에 추가(필요한 경우 병합)해 각각 작성 및 게시할 수 있게 됩니다. 파란색-녹색 변환이 일어나기 전에 기본 저장소가 새 색인 정의로 다시 지정됩니다.

>[!TIP]
>
>AEM as a Cloud Service의 필수 패키지 구조에 대한 자세한 정보는 [AEM 프로젝트 구조](/help/implementing/developing/introduction/aem-project-content-package-structure.md)를 참조하십시오.

## 파란색-녹색 배포를 사용해 색인 관리 {#index-management-using-blue-green-deployments}

### 색인 관리 개요 {#what-is-index-management}

색인 관리는 색인을 추가, 삭제 및 변경하는 것을 의미합니다. 색인의 *정의* 변경은 빠르게 진행되지만 변경(“색인 작성”, 기존 색인의 경우, “색인 재지정”) 적용은 시간이 소요됩니다. 즉시 확인할 수 없으며 저장소에서 데이터를 색인 지정하기 위해 스캔해야 합니다.

### 파란색-녹색 배포 개요 {#what-is-blue-green-deployment}

파란색-녹색 배포를 통해 중단 시간을 줄일 수 있습니다. 또한 무중단 업그레이드가 가능하며 빠른 롤백을 제공합니다. 애플리케이션의 이전 버전(파란색)이 애플리케이션의 새 버전(녹색)과 동시에 구동됩니다.

### 읽기 전용 및 읽기-쓰기 영역 {#read-only-and-read-write-areas}

저장소의 특정 영역(저장소의 읽기 전용 영역)은 애플리케이션의 이전(파란색)과 새(녹색) 버전에서 다를 수 있습니다. 저장소의 읽기 전용 영역은 일반적으로 “`/app`” 및 “`/libs`”입니다. 다음의 예처럼 이탤릭체는 읽기 전용 영역을 표시할 때, 볼드체는 읽기-쓰기 영역에 사용됩니다.

* **/**
* */apps (읽기 전용)*
* **/content**
* */libs (읽기 전용)*
* **/oak:index**
* **/oak:index/acme.**
* **/jcr:system**
* **/system**
* **/var**

저장소의 읽기-쓰기 영역은 애플리케이션의 모든 버전에서 공유되지만 애플리케이션의 각 버전에 대해 `/apps` 및 `/libs`의 특정 세트가 있습니다.

### 파란색-녹색 배포 없이 색인 관리 {#index-management-without-blue-green-deployment}

개발 중 또는 온프레미스 설치를 사용하면 런타임 시 색인을 추가, 삭제 또는 변경할 수 있습니다. 색인은 사용 가능한 상태가 되면 바로 사용됩니다. 색인이 애플리케이션의 이전 버전에서 사용 지원이 안 되는 경우 일반적으로 예약된 중단 시간 동안 색인이 작성됩니다. 색인 삭제나 기존의 색인 변경 시에도 마찬가지입니다. 색인을 삭제하면 삭제하는 즉시 사용할 수 없게 됩니다.

### 파란색-녹색 배포로 색인 관리 {#index-management-with-blue-green-deployment}

파란색-녹색 배포를 사용하면 중단 시간이 없습니다. 업그레이드 시 잠시 동안 애플리케이션의 이전 버전(예: 버전 1)과 새 버전(버전 2)이 동일한 저장소에서 동시에 실행됩니다. 버전 1이 특정 색인을 사용해야 하는 경우 이 색인을 버전 2에서 삭제해야 합니다. 이 색인을 이후, 예를 들어 버전 3에서 삭제해야 하는데 이는 애플리케이션의 버전 1이 더 이상 수행되지 않는 지점입니다. 또한 애플리케이션은 버전 2가 수행되고 버전 2의 색인이 사용 가능한 상태여도 버전 1이 잘 작동되는 것처럼 작성되어야 합니다.

새 버전으로 업그레이드가 완료된 후, 이전 버전은 시스템에서 수집된 불필요한 정보가 될 수 있습니다. 이전 색인은 롤백의 속도를 높이기 위해(롤백이 필요한 경우) 잠시 동안 남아 있을 수 있습니다.

다음 테이블은 다섯 개의 색인 정의를 나타냅니다. 색인 `cqPageLucene`는 두 버전 모두에서 사용되지만 색인 `damAssetLucene-custom-1`은 버전 2에서만 사용됩니다.

>[!NOTE]
>
>기존의 색인에 대한 대체로 표시하기 위해 AEM as a Cloud Service에 `<indexName>-custom-<customerVersionNumber>`가 필요합니다.

| 색인 | 기본 제공 색인 | 버전 1에서 사용 | 버전 2에서 사용 |
|---|---|---|---|
| /oak:index/damAssetLucene | 예 | 예 | 아니요 |
| /oak:index/damAssetLucene-custom-1 | 예 (맞춤화) | 아니요 | 예 |
| /oak:index/acme.product-custom-1 | 아니요 | 예 | 아니요 |
| /oak:index/acme.product-custom-2 | 아니요 | 아니요 | 예 |
| /oak:index/cqPageLucene | 예 | 예 | 예 |

버전 번호는 색인이 변경될 때마다 증가합니다. 사용자 정의 색인 이름이 제품 자체의 색인 이름과 충돌하는 것을 방지하기 위해 사용자 정의 색인과 기본 제공 색인이 `-custom-<number>`(으)로 끝나야 합니다.

### 기본 제공 색인 변경 {#changes-to-out-of-the-box-indexes}

Adobe에서 “damAssetLucene” 또는 “cqPageLucene” 같은 기본 제공 색인을 변경하면 `damAssetLucene-2` 또는 `cqPageLucene-2`라는 이름의 새로운 색인이 생성되거나 색인이 이미 맞춤화된 경우 맞춤화된 색인 정의가 아래와 같이 기본 제공 색인의 변경 사항과 병합됩니다. 변경 사항의 병합은 자동으로 진행됩니다. 기본 제공 색인을 변경한 경우 다른 작업을 수행하지 않아도 된다는 의미입니다. 하지만 나중에 색인을 다시 맞춤화할 수 있습니다.

| 색인 | 기본 제공 색인 | 버전 2에서 사용 | 버전 3에서 사용 |
|---|---|---|---|
| /oak:index/damAssetLucene-custom-1 | 예 (맞춤화) | 예 | 아니요 |
| /oak:index/damAssetLucene-2-custom-1 | 예 (damAssetLucene-custom-1과 damAssetLucene-2에서 자동으로 병합) | 아니요 | 예 |
| /oak:index/cqPageLucene | 예 | 예 | 아니요 |
| /oak:index/cqPageLucene-2 | 예 | 아니요 | 예 |

### 현재 제한 사항 {#current-limitations}

현재 색인 관리는 `lucene` 색인 유형만 지원됩니다. 내부적으로 다른 색인을 구성하고 쿼리에 사용할 수 있습니다. 예: 탄력적인 색인.

### 색인 추가 {#adding-an-index}

애플리케이션의 새 버전 이상에서 사용할 수 있도록 `/oak:index/acme.product-custom-1`이라는 이름의 완전히 맞춤화된 색인을 추가하려면 다음과 같이 색인을 구성해야 합니다.

`acme.product-1-custom-1`

색인 이름 앞에 사용자 정의 식별자를 추가하고 뒤에 점(**`.`**)을 넣으면 작동합니다. 식별자는 2~5자 사이여야 합니다.

위와 같이, 색인이 애플리케이션의 새 버전에서 사용할 때에만 사용되는지를 확인합니다.

### 색인 변경 {#changing-an-index}

기존 색인을 변경할 때 새 색인은 변경된 색인 정의에 추가해야 합니다. 기존 색인 `/oak:index/acme.product-custom-1`이 변경되는 경우로 예를 들어 보겠습니다. 기존 색인은 `/oak:index/acme.product-custom-1`에 저장되며 새 색인은 `/oak:index/acme.product-custom-2`에 저장됩니다.

애플리케이션의 기존 버전은 다음의 구성을 사용합니다.

`/oak:index/acme.product-custom-1`

애플리케이션의 새 버전은 (변경된) 다음 구성을 사용합니다.

`/oak:index/acme.product-custom-2`

>[!NOTE]
>
>AEM as a Cloud Service에 대한 색인 정의는 로컬 개발 인스턴스에 대한 색인 정의와 완전히 일치하지 않을 수 있습니다. 개발 인스턴스에는 Tika 구성이 없지만 AEM as a Cloud Service 인스턴스에는 있습니다. Tika 구성이 있는 색인을 맞춤화하는 경우 Tika 구성을 유지하시기 바랍니다.

### 변경 실행 취소 {#undoing-a-change}

때로는 색인 정의의 변경 사항을 되돌려야 할 필요가 있습니다. 실수로 변경이 되었거나 더 이상 변경이 필요하지 않은 경우가 있을 수 있습니다. 색인 정의 `damAssetLucene-8-custom-3`이 실수로 생성된 후 이미 배포된 경우를 예로 들어보겠습니다. 이런 경우에는 이전의 색인 정의 `damAssetLucene-8-custom-2`를 되돌리고 싶을 것입니다. 그러면 이전 색인의 정의 `damAssetLucene-8-custom-2`가 포함된 `damAssetLucene-8-custom-4`라는 이름의 새 색인을 추가해야 합니다.

### 색인 삭제 {#removing-an-index}

다음은 사용자 정의에만 적용됩니다. 제품 색인은 AEM에서 사용되고 있어 삭제되지 않을 수 있습니다.

애플리케이션의 최신 버전에서 색인이 삭제되면 새 이름의 빈 색인(사용되지 않았으며 어떤 데이터도 포함되지 않은 빈 색인)을 정의할 수 있습니다. 이 예의 경우 이름을 `/oak:index/acme.product-custom-3`으로 할 수 있습니다. 이렇게 하면 색인 `/oak:index/acme.product-custom-2`를 대체할 수 있습니다. 시스템에서 `/oak:index/acme.product-custom-2`가 삭제되면 빈 색인 `/oak:index/acme.product-custom-3`도 삭제할 수 있습니다. 이 같은 빈 색인의 예는 다음과 같습니다.

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

기본 제공 색인의 맞춤화가 더 이상 필요하지 않은 경우 기본 제공 색인 정의를 복사해야 합니다. 예를 들어, 이미 `damAssetLucene-8-custom-3`을 배포했지만 더 이상 맞춤화가 필요하지 않고 기본 `damAssetLucene-8` 색인으로 다시 바꾸고 싶다면 `damAssetLucene-8`의 색인 정의가 포함된 색인 `damAssetLucene-8-custom-4`를 추가해야 합니다.

## 인덱스 및 쿼리 최적화 {#index-query-optimizations}

Apache Jackrabbit Oak는 유연한 색인 구성을 통해 효율적으로 검색 쿼리를 처리할 수 있도록 해 줍니다. 색인은 특히 대형 저장소에서 중요합니다. 모든 쿼리가 적절한 색인에 의해 지원되는지 확인하십시오. 적절한 색인 없는 쿼리는 수천 개의 노드를 읽을 수 있어 경고로 기록됩니다.

자세한 내용은 [이 문서](query-and-indexing-best-practices.md) 쿼리 및 인덱스를 최적화하는 방법에 대한 자세한 정보.
