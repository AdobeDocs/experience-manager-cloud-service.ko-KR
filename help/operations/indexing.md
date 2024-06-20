---
title: 콘텐츠 검색 및 색인화
description: AEM as a Cloud Service으로 콘텐츠 검색 및 색인화에 대해 알아봅니다.
exl-id: 4fe5375c-1c84-44e7-9f78-1ac18fc6ea6b
feature: Operations
role: Admin
source-git-commit: 65e67225a6a91d871218c12c4696dd281787cd58
workflow-type: tm+mt
source-wordcount: '2449'
ht-degree: 29%

---

# 콘텐츠 검색 및 색인화 {#indexing}

## AEM as a Cloud Service의 변경 내용 {#changes-in-aem-as-a-cloud-service}

AEM as a Cloud Service를 통해 Adobe는 AEM 인스턴스 중심 모델에서 Cloud Manager의 CI/CD 파이프라인 기반 n-x AEM 컨테이너를 사용하는 서비스 중심 보기로 이전하는 중입니다. 단일 AEM 인스턴스의 색인을 구성 및 유지하는 대신 배포 전 색인 구성을 지정해야 합니다. 프로덕션의 구성을 변경하면 CI/CD 정책을 위반하게 됩니다. 프로덕션으로 가져오기 전에 지정, 테스트 및 색인 재지정을 하지 않은 경우 시스템 안정성과 성능에 영향을 줄 수 있기 때문에 색인 변경에도 똑같이 적용됩니다.

다음은 AEM 6.5 및 이전 버전과 비교한 주요 변경 사항 목록입니다.

1. 사용자는 색인화를 디버그, 구성 또는 유지하기 위해 단일 AEM 인스턴스의 색인 관리자에 액세스할 권한이 더 이상 없습니다. 로컬 개발 및 온프레미스 배포에 대해서만 사용됩니다.
1. 사용자는 단일 AEM 인스턴스의 색인을 변경하지 못하거나 일관성 검사 또는 색인 재지정에 대해 더 이상 걱정하지 않아도 됩니다.
1. 일반적으로 프로덕션 진행 전에 색인 변경을 시작하여 Cloud Manager CI/CD 파이프라인의 품질 게이트웨이를 피하지 않고 프로덕션의 비즈니스 KPI에 영향을 주지 않습니다.
1. 고객은 런타임에 프로덕션의 검색 성능을 포함하여 모든 관련 지표를 사용하여 검색 및 색인화의 주제에 대한 거시적인 보기를 제공할 수 있습니다.
1. 고객은 필요에 따라 경고를 설정할 수 있습니다.
1. SRE는 시스템 상태를 연중무휴 모니터링하고 가능한 한 빨리 조치를 취합니다.
1. 색인 구성은 배포를 통해 변경됩니다. 색인 정의 변경은 다른 콘텐츠 변경과 같은 방식으로 구성됩니다.
1. AEM의 도입으로 높은 수준의 as a Cloud Service [순환 배포 모델](#index-management-using-rolling-deployments), 두 세트의 색인이 존재합니다. 한 세트는 이전 버전이고, 다른 한 세트는 새 버전입니다.
1. 고객은 Cloud Manager 빌드 페이지에서 인덱싱 작업이 완료되었는지 여부를 확인할 수 있으며 새 버전이 트래픽을 가져올 수 있게 되면 알림을 받습니다.

제한 사항:

* 현재 AEM as a Cloud Service의 색인 관리는 `lucene` 색인 유형만 지원됩니다.
* 표준 분석기 (즉, 제품과 함께 제공되는 분석기)만 지원됩니다. 사용자 정의 분석기는 지원되지 않습니다.
* 내부적으로 다른 색인을 구성하고 쿼리에 사용할 수 있습니다. 예를 들어 `damAssetLucene` 색인에 대해 작성된 Skyline의 쿼리는 이 색인의 Elasticsearch 버전에 대해 실행됩니다. 이 차이는 일반적으로 애플리케이션과 사용자에게는 표시되지 않지만 다음과 같은 특정 도구에는 표시됩니다. `explain` 기능이 다른 색인을 보고합니다. Lucene 색인과 Elastic 색인의 차이에 대해서는 [Apache Jackrabbit Oak의 Elastic 설명서](https://jackrabbit.apache.org/oak/docs/query/elastic.html)를 참조하십시오. 고객은 Elasticsearch 색인을 직접 구성할 필요가 없으며 구성할 수도 없습니다.
* 유사한 피쳐 벡터로 검색(`useInSimilarity = true`)은 지원되지 않습니다.

>[!TIP]
>
>고급 검색 및 색인화 기능에 대한 자세한 설명을 포함하여 Oak 색인화 및 쿼리에 대한 자세한 내용은 [Apache Oak 설명서](https://jackrabbit.apache.org/oak/docs/query/query.html).


## 사용 방법 {#how-to-use}

색인 정의는 다음과 같이 세 가지 주요 사용 사례로 분류할 수 있습니다.

1. **추가** 새로운 사용자 정의 색인 정의.
2. **업데이트** 새 버전을 추가하여 기존 색인 정의.
3. **제거** 더 이상 필요하지 않은 색인 정의.

위의 1번과 2번은 해당 Cloud Manager 릴리스 일정에서 사용자 지정 코드 기반의 일부로 색인 정의를 생성해야 합니다. 자세한 내용은 [AEM에 as a Cloud Service 배포](/help/implementing/deploying/overview.md) 설명서를 참조하십시오.

## 색인 이름 {#index-names}

색인 정의는 다음 범주 중 하나에 속할 수 있습니다.

1. 기본 제공(OOTB) 색인. 예: `/oak:index/cqPageLucene-2` 또는 `/oak:index/damAssetLucene-8`.

2. OOTB 인덱스 사용자 정의. 이러한 경고는 다음을 추가하여 나타냅니다. `-custom-` 뒤에 숫자 식별자가 옵니다. 예: `/oak:index/damAssetLucene-8-custom-1`.

3. 완전히 맞춤화된 색인: 완전히 새로운 색인을 처음부터 만들 수 있습니다. 이름 충돌을 방지하려면 이름에 접두사가 있어야 합니다. 예: `/oak:index/acme.product-1-custom-2`: 여기서 접두사는 입니다. `acme.`

>[!NOTE]
>
>에서 새 색인 소개 `dam:Asset` nodetype(특히 전체 텍스트 인덱스)이 OOTB 제품 기능과 충돌하여 기능 및 성능 문제가 발생할 수 있으므로 권장하지 않습니다. 일반적으로 현재 항목에 추가 속성을 추가합니다. `damAssetLucene-*` index version은에서 쿼리를 색인화하는 가장 적절한 방법입니다 `dam:Asset` nodetype(이러한 변경 사항은 이후에 릴리스되는 경우 색인의 새 제품 버전에 자동으로 병합됩니다.) 확실하지 않은 경우 Adobe 지원 센터에 문의하여 조언을 구하십시오.

## 새 색인 정의 준비 {#preparing-the-new-index-definition}

>[!NOTE]
>
>기본 제공 인덱스를 맞춤화하는 경우, 예를 들어 `damAssetLucene-8`에서 최신 기본 제공 인덱스 정의를 복사합니다. *Cloud Service 환경* crx DE 패키지 관리자 사용(`/crx/packmgr/`). 이름 바꾸기 `damAssetLucene-8-custom-1` (또는 이상) 및 XML 파일 내에 사용자 정의를 추가합니다. 이렇게 하면 필요한 구성이 실수로 제거되지 않도록 할 수 있습니다. 예를 들어 `tika` 노드 `/oak:index/damAssetLucene-8/tika` 는 AEM Cloud Service 환경에 배포된 사용자 지정 색인에 필요하지만 로컬 AEM SDK에는 없습니다.

OOTB 인덱스의 사용자 정의를 위해 이 이름 지정 패턴을 따르는 실제 인덱스 정의가 포함된 새 패키지를 준비합니다.

`<indexName>-<productVersion>-custom-<customVersion>`

완전히 맞춤화된 색인의 경우 이 이름 지정 패턴을 따르는 색인 정의가 포함된 새 색인 정의 패키지를 준비합니다.

`<prefix>.<indexName>-<productVersion>-custom-<customVersion>`

<!-- Alexandru: temporarily drafting this statement due to CQDOC-17701

The package from the above sample is built as `com.adobe.granite:new-index-content:zip:1.0.0-SNAPSHOT`. -->

>[!NOTE]
>
>색인 정의가 포함된 모든 콘텐츠 패키지는에 다음 속성이 설정되어 있어야 합니다. `properties.xml` 콘텐츠 패키지의 파일입니다. `properties.xml` 는 기본적으로 새 패키지에서 생성되며 다음 위치에 있습니다. `<package_name>/META-INF/vault/properties.xml`:
>
> * `noIntermediateSaves=true`
>
> * `allowIndexDefinitions=true`

## 사용자 정의 색인 정의 배포 {#deploying-custom-index-definitions}

맞춤화된 버전의 기본 제공 색인의 배포를 보여 주기 위해 `damAssetLucene-8`에 단계별 안내서를 제공합니다. 이 예제에서는 이름을 로 바꿉니다. `damAssetLucene-8-custom-1`. 그런 다음 프로세스는 다음과 같습니다.

1. 에서 업데이트된 색인 이름으로 새 폴더를 만듭니다. `ui.apps` 디렉터리:
   * 예: `ui.apps/src/main/content/jcr_root/_oak_index/damAssetLucene-8-custom-1/`

2. 구성 파일 추가 `.content.xml` 생성된 폴더 내에 있는 사용자 지정 구성을 사용하여 다음은 사용자 지정의 예입니다. 파일 이름: `ui.apps/src/main/content/jcr_root/_oak_index/damAssetLucene-8-custom-1/.content.xml`

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <jcr:root xmlns:jcr="http://www.jcp.org/jcr/1.0" xmlns:dam="http://www.day.com/dam/1.0" xmlns:nt="http://www.jcp.org/jcr/nt/1.0" xmlns:oak="http://jackrabbit.apache.org/oak/ns/1.0" xmlns:rep="internal"
       jcr:mixinTypes="[rep:AccessControllable]"
       jcr:primaryType="oak:QueryIndexDefinition"
       async="[async,nrt]"
       compatVersion="{Long}2"
       evaluatePathRestrictions="{Boolean}true"
       includedPaths="[/content/dam]"
       maxFieldLength="{Long}100000"
       type="lucene">
       <facets
           jcr:primaryType="nt:unstructured"
           secure="statistical"
           topChildren="100"/>
       <indexRules jcr:primaryType="nt:unstructured">
           <dam:Asset jcr:primaryType="nt:unstructured">
               <properties jcr:primaryType="nt:unstructured">
                   <cqTags
                       jcr:primaryType="nt:unstructured"
                       name="jcr:content/metadata/cq:tags"
                       nodeScopeIndex="{Boolean}true"
                       propertyIndex="{Boolean}true"
                       useInSpellcheck="{Boolean}true"
                       useInSuggest="{Boolean}true"/>
               </properties>
           </dam:Asset>
       </indexRules>
       <tika jcr:primaryType="nt:folder">
           <config.xml jcr:primaryType="nt:file"/>
       </tika>
   </jcr:root>
   ```

3. 의 FileVault 필터에 항목 추가 `ui.apps/src/main/content/META-INF/vault/filter.xml`:

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <workspaceFilter version="1.0">
       ...
       <filter root="/oak:index/damAssetLucene-8-custom-1"/> 
   </workspaceFilter>
   ```

4. 에서 Apache Tika에 대한 구성 파일을 추가합니다. `ui.apps/src/main/content/jcr_root/_oak_index/damAssetLucene-8-custom-1/tika/config.xml`:

   ```xml
   <properties>
       <detectors>
           <detector class="org.apache.tika.detect.TypeDetector"/>
       </detectors>
       <parsers>
           <parser class="org.apache.tika.parser.DefaultParser">
           <mime>text/plain</mime>
           </parser>
       </parsers>
       <service-loader initializableProblemHandler="ignore" dynamic="true"/>
   </properties>
   ```

5. 구성이 다음에 제공된 지침을 준수하는지 확인합니다. [프로젝트 구성](#project-configuration) 섹션. 그에 따라 필요한 적응을 수행합니다.

## 프로젝트 구성

버전 >= 를 사용하는 것이 좋습니다. `1.3.2` 잭래빗의 `filevault-package-maven-plugin`. 이를 프로젝트에 통합하는 단계는 다음과 같습니다.

1. 최상위 수준에서 버전 업데이트 `pom.xml`:

   ```xml
   <plugin>
       <groupId>org.apache.jackrabbit</groupId>
           <artifactId>filevault-package-maven-plugin</artifactId>
           ...
           <version>1.3.2</version>
       ...
   </plugin>
   ```

2. 최상위 수준에 다음 추가 `pom.xml`:

   ```xml
   <jackrabbit-packagetype>
       <options>   
           <immutableRootNodeNames>apps,libs,oak:index</immutableRootNodeNames>
       </options>
   </jackrabbit-packagetype>
   ```

   다음은 프로젝트의 최상위 수준 샘플입니다 `pom.xml` 위에 언급된 구성을 가진 파일이 포함되었습니다.

   파일 이름: `pom.xml`

   ```xml
   <plugin>
       <groupId>org.apache.jackrabbit</groupId>
           <artifactId>filevault-package-maven-plugin</artifactId>
           ...
           <version>1.3.2</version>
           <configuration>
               ...
               <validatorsSettings>
                   <jackrabbit-packagetype>
                       <options>
                           <immutableRootNodeNames>apps,libs,oak:index</immutableRootNodeNames>
                       </options>
                   </jackrabbit-packagetype>
                   ...
               ...
   </plugin>
   ```

3. 위치 `ui.apps/pom.xml` 및 `ui.apps.structure/pom.xml` 다음을 활성화해야 합니다. `allowIndexDefinitions` 및 `noIntermediateSaves` 의 옵션 `filevault-package-maven-plugin`. 활성화 중 `allowIndexDefinitions` 은 사용자 정의 색인 정의를 허용하지만 `noIntermediateSaves` 구성이 올바르게 추가되었는지 확인합니다.

   파일 이름: `ui.apps/pom.xml` 및 `ui.apps.structure/pom.xml`

   ```xml
   <plugin>
       <groupId>org.apache.jackrabbit</groupId>
           <artifactId>filevault-package-maven-plugin</artifactId>
           <configuration>
               <allowIndexDefinitions>true</allowIndexDefinitions>
               <properties>
                   <cloudManagerTarget>none</cloudManagerTarget>
                   <noIntermediateSaves>true</noIntermediateSaves>
               </properties>
       ...
   </plugin>
   ```

4. 필터 추가 `/oak:index` 위치: `ui.apps.structure/pom.xml`:

   ```xml
   <filters>
       ...
       <filter><root>/oak:index</root></filter>
   </filters>
   ```

새 색인 정의를 추가한 후 Cloud Manager를 사용하여 새 애플리케이션을 배포합니다. 이 배포는 두 개의 작업을 시작하고, 각각 작성 및 게시를 위해 MongoDB 및 Azure 세그먼트 저장소에 인덱스 정의를 추가(및 필요한 경우 병합)합니다. 전환 전에 기본 저장소는 업데이트된 색인 정의로 리인덱싱됩니다.

>[!TIP]
>
>AEMas a Cloud Service 의 필수 패키지 구조에 대한 자세한 내용은 [AEM 프로젝트 구조](/help/implementing/developing/introduction/aem-project-content-package-structure.md).

## 순환 배포를 사용한 색인 관리 {#index-management-using-rolling-deployments}

### 색인 관리 개요 {#what-is-index-management}

색인 관리는 색인을 추가, 삭제 및 변경하는 것을 의미합니다. 색인의 *정의* 변경은 빠르게 진행되지만 변경(“색인 작성”, 기존 색인의 경우, “색인 재지정”) 적용은 시간이 소요됩니다. 즉시 확인할 수 없으며 저장소에서 데이터를 색인화하기 위해 스캔해야 합니다.

### 롤링 배포 개요 {#what-are-rolling-deployments}

연속 배포를 통해 가동 중지 시간을 줄일 수 있습니다. 또한 무중단 업그레이드가 가능하며 빠른 롤백을 제공합니다. 애플리케이션의 이전 버전은 애플리케이션의 새 버전과 동시에 실행됩니다.

### 읽기 전용 및 읽기-쓰기 영역 {#read-only-and-read-write-areas}

저장소의 특정 영역(저장소의 읽기 전용 부분)은 애플리케이션의 이전 버전과 새 버전에서 다를 수 있습니다. 저장소의 읽기 전용 영역은 일반적으로 다음과 같습니다 `/app` 및 `/libs`. 다음의 예처럼 이탤릭체는 읽기 전용 영역을 표시할 때, 볼드체는 읽기-쓰기 영역에 사용됩니다.

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

### 순환 배포를 통한 색인 관리 {#index-management-without-rolling-deployments}

개발 중에 또는 온프레미스 설치를 사용할 때 런타임 시 색인을 추가, 제거 또는 변경할 수 있습니다. 색인은 사용 가능한 경우 사용됩니다. 색인이 애플리케이션의 이전 버전에서 아직 사용되지 않는 경우 색인은 일반적으로 예약된 가동 중지 시간 동안 작성됩니다. 색인 삭제나 기존의 색인 변경 시에도 마찬가지입니다. 색인을 삭제하면 삭제할 때 사용할 수 없게 됩니다.

### 연속 배포를 통한 색인 관리 {#index-management-with-rolling-deployments}

연속 배포를 사용하면 중단 시간이 없습니다. 업데이트하는 동안 잠시 동안 애플리케이션의 이전 버전(예: 버전 1)과 새 버전(버전 2)이 동일한 저장소에서 동시에 실행됩니다. 버전 1에서 특정 색인을 사용해야 하는 경우 이 색인을 버전 2에서 제거해야 합니다. 색인은 나중에(예: 버전 3에서) 제거해야 하며, 이 시점에서 애플리케이션의 버전 1이 더 이상 실행되지 않는 것이 보장됩니다. 또한 애플리케이션은 버전 2가 수행되고 버전 2의 색인이 사용 가능한 상태여도 버전 1이 잘 작동되는 것처럼 작성되어야 합니다.

새 버전으로 업그레이드가 완료되면 이전 버전은 시스템에서 수집된 불필요한 정보가 될 수 있습니다. 이전 색인은 롤백의 속도를 높이기 위해(롤백이 필요한 경우) 잠시 동안 남아 있을 수 있습니다.

다음 테이블은 다섯 개의 색인 정의를 나타냅니다. 색인 `cqPageLucene`는 두 버전 모두에서 사용되지만 색인 `damAssetLucene-custom-1`은 버전 2에서만 사용됩니다.

>[!NOTE]
>
>다음 `<indexName>-custom-<customerVersionNumber>` 기존 색인의 대체로 표시하기 위해 AEM as a Cloud Service에 필요합니다.

| 색인 | 기본 제공 색인 | 버전 1에서 사용 | 버전 2에서 사용 |
|---|---|---|---|
| /oak:index/damAssetLucene | 예 | 예 | 아니요 |
| /oak:index/damAssetLucene-custom-1 | 예 (맞춤화) | 아니요 | 예 |
| /oak:index/acme.product-custom-1 | 아니요 | 예 | 아니요 |
| /oak:index/acme.product-custom-2 | 아니요 | 아니요 | 예 |
| /oak:index/cqPageLucene | 예 | 예 | 예 |

버전 번호는 색인이 변경될 때마다 증가합니다. 사용자 정의 색인 이름이 제품 자체의 색인 이름과 충돌하는 것을 방지하려면 사용자 정의 색인 및 기본 제공 색인에 대한 변경 사항으로 끝나야 합니다 `-custom-<number>`.

### 기본 제공 색인 변경 {#changes-to-out-of-the-box-indexes}

Adobe이 &quot;damAssetLucene&quot; 또는 &quot;cqPageLucene&quot; 같은 기본 제공 색인을 변경하면 이라는 이름의 새 색인 `damAssetLucene-2` 또는 `cqPageLucene-2` 이(가) 만들어졌습니다. 또는 색인이 이미 맞춤화된 경우 맞춤화된 색인 정의가 아래와 같이 기본 제공 색인의 변경 사항과 병합됩니다. 변경 사항의 병합은 자동으로 진행됩니다. 즉, 기본 제공 색인이 변경되는 경우에는 아무 작업도 수행하지 않아도 됩니다. 하지만 나중에 색인을 다시 맞춤화할 수 있습니다.

| 색인 | 기본 제공 색인 | 버전 2에서 사용 | 버전 3에서 사용 |
|---|---|---|---|
| /oak:index/damAssetLucene-custom-1 | 예 (맞춤화) | 예 | 아니요 |
| /oak:index/damAssetLucene-2-custom-1 | 예 (damAssetLucene-custom-1과 damAssetLucene-2에서 자동으로 병합) | 아니요 | 예 |
| /oak:index/cqPageLucene | 예 | 예 | 아니요 |
| /oak:index/cqPageLucene-2 | 예 | 아니요 | 예 |

### 현재 제한 사항 {#current-limitations}

색인 관리는 색인 유형만 지원됩니다. `lucene`, 포함 `compatVersion` 을 로 설정 `2`. 내부적으로 다른 색인을 구성하고 쿼리에 사용할 수 있습니다(예: Elasticsearch 색인). 다음에 대해 작성된 쿼리 `damAssetLucene` 색인은 AEM as a Cloud Service에서 실제로 이 색인의 Elasticsearch 버전에 대해 실행될 수 있습니다. 이러한 차이는 애플리케이션 사용자에게는 표시되지 않지만 다음과 같은 특정 도구는 표시되지 않습니다. `explain` 기능이 다른 색인을 보고합니다. Lucene 색인과 Elasticsearch 색인의 차이에 대해서는 다음을 참조하십시오. [apache Jackrabbit Oak의 Elasticsearch 설명서](https://jackrabbit.apache.org/oak/docs/query/elastic.html). 고객은 Elasticsearch 색인을 직접 구성할 수 없으며 구성할 필요가 없습니다.

기본 제공 분석기 (즉, 제품과 함께 제공되는 분석기)만 지원됩니다. 사용자 정의 분석기는 지원되지 않습니다.

최상의 운영 성능을 위해서는 인덱스가 너무 커서는 안 됩니다. 모든 인덱스의 총 크기를 안내서로 사용할 수 있습니다. 사용자 정의 색인이 추가된 후 이 크기가 100% 이상 증가하고 개발 환경에서 표준 색인을 조정한 경우 사용자 정의 색인 정의를 조정해야 합니다. AEM as a Cloud Service으로 인해 시스템 안정성과 성능에 부정적인 영향을 주는 인덱스가 배포되지 않을 수 있습니다.

### 색인 추가 {#adding-an-index}

이라는 이름의 완전히 맞춤화된 색인을 추가하려면 `/oak:index/acme.product-custom-1`: 애플리케이션의 새 버전 이상에서 사용하려면 다음과 같이 색인을 구성해야 합니다.

`acme.product-1-custom-1`

이 구성은 색인 이름에 사용자 지정 식별자를 앞에 추가하고 뒤에 점(**`.`**). 식별자는 2~5자 사이여야 합니다.

위와 같이 이 구성은 색인이 애플리케이션의 새 버전에서만 사용되도록 합니다.

### 색인 변경 {#changing-an-index}

기존 색인을 변경할 때 새 색인을 변경된 색인 정의와 함께 추가해야 합니다. 기존 색인 `/oak:index/acme.product-custom-1`이 변경되는 경우로 예를 들어 보겠습니다. 기존 색인은 `/oak:index/acme.product-custom-1`에 저장되며 새 색인은 `/oak:index/acme.product-custom-2`에 저장됩니다.

애플리케이션의 기존 버전은 다음의 구성을 사용합니다.

`/oak:index/acme.product-custom-1`

애플리케이션의 새 버전은 (변경된) 다음 구성을 사용합니다.

`/oak:index/acme.product-custom-2`

>[!NOTE]
>
>AEM as a Cloud Service에 대한 색인 정의는 로컬 개발 인스턴스에 대한 색인 정의와 완전히 일치하지 않을 수 있습니다. 개발 인스턴스에는 Tika 구성이 없지만 AEM as a Cloud Service 인스턴스에는 있습니다. Tika 구성을 사용하여 색인을 사용자 정의하는 경우 Tika 구성을 유지합니다.

### 변경 실행 취소 {#undoing-a-change}

색인 정의에서 수정을 실행 취소해야 하는 경우가 가끔 있습니다. 이는 의도치 않은 오류로 인해 발생하거나 더 이상 수정할 필요가 없습니다. 예를 들어 색인 정의를 사용합니다 `damAssetLucene-8-custom-3,` 가 잘못 생성되어 이미 배포되었습니다. 따라서 이전 색인 정의로 되돌아갈 수 있습니다. `damAssetLucene-8-custom-2.` 이를 수행하려면 라는 이름의 새 색인을 도입해야 합니다 `damAssetLucene-8-custom-4` 이전 색인의 정의를 통합합니다. `damAssetLucene-8-custom-2.`

### 색인 삭제 {#removing-an-index}

다음은 사용자 정의에만 적용됩니다. 제품 색인은 AEM에서 사용되고 있어 삭제되지 않을 수 있습니다.

애플리케이션의 최신 버전에서 색인이 제거되면 새 이름의 빈 색인(사용되지 않으며 데이터를 포함하지 않는 빈 색인)을 정의할 수 있습니다. 이 예제에서는 이름을 지정할 수 있습니다 `/oak:index/acme.product-custom-3`. 이 이름은 색인을 대체합니다 `/oak:index/acme.product-custom-2`. 다음 이후 `/oak:index/acme.product-custom-2` 빈 색인, 시스템에 의해 제거됩니다. `/oak:index/acme.product-custom-3` 그런 다음 제거할 수 있습니다. 이 같은 빈 색인의 예는 다음과 같습니다.

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

기본 제공 색인의 맞춤화가 더 이상 필요하지 않은 경우 기본 제공 색인 정의를 복사해야 합니다. 예를 들어 이미 `damAssetLucene-8-custom-3`을 배포했지만 더 이상 맞춤화가 필요하지 않고 기본 `damAssetLucene-8` 색인으로 다시 바꾸고 싶다면 `damAssetLucene-8`의 색인 정의가 포함된 색인 `damAssetLucene-8-custom-4`를 추가해야 합니다.

## 색인 및 쿼리 최적화 {#index-query-optimizations}

Apache Jackrabbit Oak는 유연한 색인 구성을 통해 효율적으로 검색 쿼리를 처리할 수 있도록 해 줍니다. 색인은 특히 대형 저장소에서 중요합니다. 모든 쿼리가 적절한 색인에 의해 지원되는지 확인하십시오. 적절한 색인이 없는 쿼리는 수천 개의 노드를 읽을 수 있으며 이는 경고로 기록됩니다.

다음을 참조하십시오 [이 문서](query-and-indexing-best-practices.md) 쿼리 및 색인을 최적화하는 방법에 대한 정보를 제공합니다.
