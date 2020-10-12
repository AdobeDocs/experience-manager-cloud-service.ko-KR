---
title: AEM 프로젝트 구조
description: Adobe Experience Manager Cloud Service에 배포할 패키지 구조를 정의하는 방법에 대해 알아보십시오.
translation-type: tm+mt
source-git-commit: 1a282bdaca02f47d7936222da8522e74831a4572
workflow-type: tm+mt
source-wordcount: '2828'
ht-degree: 2%

---


# AEM 프로젝트 구조

>[!TIP]
>
>이 문서는 이러한 학습 및 개념을 바탕으로 하므로 기본 [AEM Project Tranype 사용](https://docs.adobe.com/content/help/ko-KR/experience-manager-core-components/using/developing/archetype/overview.html)및 [FileVault Content Maven 플러그인에](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/vlt-mavenplugin.html) 익숙해지십시오.

이 문서에서는 불변의 컨텐츠와 불변의 컨텐츠 분리를 존중하여 Adobe Experience Manager Maven 프로젝트에 필요한 변경 사항을 설명하고, 상충되는 배포가 없도록 종속성을 설정하고, 배포 가능한 구조로 패키지되어 있다는 점을 확인하여 AEM과 호환되는 Cloud Service으로 변경 사항을 설명합니다.

AEM 애플리케이션 배포는 단일 AEM 패키지로 구성되어야 합니다. 이 패키지에는 코드, 구성 및 지원 기준 컨텐츠를 포함하여 애플리케이션에서 작동하는 모든 것을 구성하는 하위 패키지가 들어 있어야 합니다.

AEM에는 **컨텐츠** 와 **코드****분리가 필요하며, 이는 단일 컨텐츠 패키지** **** `/apps` 를 및 런타임 쓰기 가능 영역(예: `/content`, `/conf``/home`, or anything `/apps`) of the repository. 대신, 응용 프로그램은 AEM에 배포하기 위해 코드와 컨텐트를 개별 패키지로 구분해야 합니다.

이 문서에 요약된 패키지 구조는 로컬 개발 배포 및 AEM Cloud Service 배포 **모두** 호환됩니다.

>[!TIP]
>
>이 문서에 요약된 구성은 [AEM Project Maven Tranype 24 이상에서 제공됩니다](https://github.com/adobe/aem-project-archetype/releases).

## 저장소의 변경 가능 영역과 불변경 영역 {#mutable-vs-immutable}

`/apps` 및 `/libs`**는 AEM이 시작된 후(예: 런타임 시) 변경(만들기, 업데이트, 삭제)할 수 없으므로 AEM에서 변경할 수 없는 영역으로 간주됩니다.** 런타임 시 변경할 수 없는 영역을 변경하려고 하면 오류가 발생합니다.

Everything else in the repository, `/content`, `/conf`, `/var`, `/etc`, `/oak:index`, `/system`, `/tmp`, etc. are all **mutable** areas, meaning they can be changed at runtime.

>[!WARNING]
>
>이전 버전의 AEM에서와 마찬가지로 수정해서는 `/libs` 안 됩니다. AEM 제품 코드만 다음 위치에 배포할 수 있습니다 `/libs`.

### Oak Indexes {#oak-indexes}

Oak 색인(`/oak:index`)은 Cloud Service 배포 프로세스로 AEM에서 특별히 관리합니다. 이는 Cloud Manager가 새 인덱스가 배포되고 완전히 다시 인덱싱될 때까지 기다렸다가 새 코드 이미지로 전환해야 하기 때문입니다.

이러한 이유로 Oak 색인은 런타임 시 변경할 수 있지만, 변경 가능한 패키지를 설치하기 전에 설치할 수 있도록 코드로 배포해야 합니다. 따라서 `/oak:index` 구성은 코드 패키지의 일부이며 아래 [설명에](#recommended-package-structure)따라 컨텐츠 패키지의 일부가 아닙니다.

>[!TIP]
>
>AEM에서 Cloud Service으로 색인 지정에 대한 자세한 내용은 [컨텐츠 검색 및 색인 문서를 참조하십시오](/help/operations/indexing.md).

## 권장 패키지 구조 {#recommended-package-structure}

![Experience Manager 프로젝트 패키지 구조](assets/content-package-organization.png)

이 다이어그램은 권장 프로젝트 구조 및 패키지 배포 객체에 대한 개요를 제공합니다.

권장되는 애플리케이션 배포 구조는 다음과 같습니다.

### 코드 패키지/OSGi 번들

+ OSGi 번들 Jar 파일이 생성되어 모든 프로젝트에 직접 포함됩니다.

+ 패키지에 배포되는 모든 코드가 `ui.apps` 포함되어 있습니다. 이 코드는 배포 대상 `/apps`뿐입니다. 패키지의 일반적인 요소는 `ui.apps` 포함되지만 이에 국한되지 않습니다.
   + [구성 요소 정의 및 HTL](https://docs.adobe.com/content/help/ko-KR/experience-manager-htl/using/overview.html) 스크립트
      + `/apps/my-app/components`
   + JavaScript 및 CSS(클라이언트 라이브러리 [를 통해](/help/implementing/developing/introduction/clientlibs.md))
      + `/apps/my-app/clientlibs`
   + [오버레이](/help/implementing/developing/introduction/overlays.md) / `/libs`
      + `/apps/cq`, `/apps/dam/`, 등이 됩니다.
   + 대체 컨텍스트 인식 구성
      + `/apps/settings`
   + ACL(권한)
      + 모든 `rep:policy` 경로 `/apps`

+ 패키지 `ui.config` 에 모든 [OSGi 구성이 포함되어 있습니다](/help/implementing/deploying/configuring-osgi.md).
   + 실행 모드별 OSGi 구성 정의를 포함하는 조직 폴더
      + `/apps/my-app/osgiconfig`
   + Cloud Service 배포 대상으로 모든 대상 AEM에 적용되는 기본 OSGi 구성이 포함된 공통 OSGi 구성 폴더
      + `/apps/my-app/osgiconfig/config`
   + Cloud Service 배포 대상으로 모든 대상 AEM에 적용되는 기본 OSGi 구성이 포함된 모드 특정 OSGi 구성 폴더 실행
      + `/apps/my-app/osgiconfig/config.<author|publish>.<dev|stage|prod>`
   + Repo Init OSGi 구성 스크립트
      + [Repo Init](#repo-init) 는 논리적으로 AEM 애플리케이션의 일부인 컨텐츠를 배포하는 데 권장되는 방법입니다. Repo Init OSGi 구성은 위에서 설명한 바와 같이 적절한 `config.<runmode>` 폴더에 배치되어야 하며 다음을 정의하는 데 사용해야 합니다.
         + 기준 컨텐츠 구조
         + 사용자
         + 서비스 사용자
         + 그룹
         + ACL(권한)

### 콘텐츠 패키지

+ 이 `ui.content` 패키지에는 모든 컨텐츠와 구성이 들어 있습니다. 컨텐트 패키지에는 `ui.apps` 또 `ui.config` 는 패키지에 들어 있지 않은 모든 노드 정의, 즉 `/apps` 또는 `/oak:index`안에 없는 모든 노드 정의가 들어 있습니다. 패키지의 일반적인 요소는 `ui.content` 포함되지만 이에 국한되지 않습니다.
   + 컨텍스트 인식 구성
      + `/conf`
   + 필수, 복잡한 컨텐츠 구조(예: Report Init에 정의된 기준 요소 컨텐츠 구조를 기반으로 구축되고 확장되는 컨텐츠 빌드아웃)
      + `/content`, `/content/dam`, 등이 됩니다.
   + 관리 태깅 분류
      + `/content/cq:tags`
   + 기존 etc 노드(이상적, 비/etc 위치로 마이그레이션)
      + `/etc`

### 컨테이너 패키지

+ 패키지 `all` 는 배포 가능한 객체, OSGI 번들 Jar 파일, 패키지 `ui.apps``ui.config` `ui.content` 및 패키지를 포함하는 컨테이너 패키지입니다. 이 `all` 패키지에는 **컨텐츠 또는 코드가** 없어야 하지만, 모든 배포를 하위 패키지 또는 OSGi 번들 Jar 파일에 저장소로 위임할 수 있습니다.

   이제 패키지가 구성 대신 Maven [FileVault Package Maven 플러그인의 임베드 구성을](#embeddeds)사용하여 `<subPackages>` 포함됩니다.

   복잡한 Experience Manager 배포의 경우 AEM의 특정 사이트 또는 테넌트를 나타내는 여러 개의 `ui.apps``ui.config` `ui.content` 프로젝트/패키지를 생성하는 것이 좋습니다. 이 작업이 수행되면 변경 가능한 컨텐츠와 변경 불가능한 컨텐츠 간의 분할이 충족되는지 확인하고 필요한 컨텐츠 패키지와 OSGi 번들 Jar 파일이 `all` 컨테이너 컨텐츠 패키지에 하위 패키지로 포함됩니다.

   예를 들어 복잡한 배포 컨텐츠 패키지 구조는 다음과 같이 표시될 수 있습니다.

   + `all` 컨텐츠 패키지에는 단일 배포 아티팩트를 만들기 위해 다음 패키지가 포함됩니다.
      + `common.ui.apps` 사이트 A와 사이트 B **에서 모두** 필요한 코드를 배포합니다.
      + `site-a.core` 사이트 A에 필요한 OSGi 번들 JAR
      + `site-a.ui.apps` 사이트 A에 필요한 배포 코드
      + `site-a.ui.config` 사이트 A에 필요한 OSGi 구성 배포
      + `site-a.ui.content` 사이트 A에 필요한 컨텐트 및 구성 배포
      + `site-b.core` 사이트 B에 필요한 OSGi 번들 JAR
      + `site-b.ui.apps` 사이트 B에 필요한 코드 배포
      + `site-b.ui.config` 사이트 B에 필요한 OSGi 구성 배포
      + `site-b.ui.content` 사이트 B에 필요한 컨텐트 및 구성 배포

### 기타 응용 프로그램 패키지{#extra-application-packages}

자체 코드와 콘텐츠 패키지로 구성된 다른 AEM 프로젝트를 AEM 배포에서 사용하는 경우 해당 컨테이너 패키지는 프로젝트 `all` 패키지에 포함되어야 합니다.

예를 들어 2개의 공급업체 AEM 애플리케이션이 포함된 AEM 프로젝트는 다음과 같이 보일 수 있습니다.

+ `all` 컨텐츠 패키지에는 단일 배포 아티팩트를 만들기 위해 다음 패키지가 포함됩니다.
   + `core` AEM 애플리케이션에서 OSGi 번들 Jar 필요
   + `ui.apps` aem 응용 프로그램에 필요한 코드 배포
   + `ui.config` aem 애플리케이션에서 필요한 OSGi 구성 배포
   + `ui.content` aem 응용 프로그램에 필요한 컨텐츠 및 구성 배포
   + `vendor-x.all` 공급업체 X 애플리케이션에서 필요한 모든 것(코드 및 컨텐츠)을 배포합니다.
   + `vendor-y.all` 공급업체 Y 애플리케이션에서 필요한 모든 것(코드 및 컨텐츠)을 배포합니다.

## 패키지 유형 {#package-types}

패키지는 선언된 패키지 유형으로 표시됩니다.

+ 컨테이너 패키지는 `packageType` 로 설정해야 합니다 `container`.
+ 코드(변경할 수 없음) 패키지는 `packageType` 로 설정해야 합니다 `application`.
+ 컨텐츠(mutable) 패키지는 `packageType` 로 설정해야 합니다 `content`.

자세한 내용은 [Apache Jackrabbit FileVault - Package Maven 플러그인 설명서](https://jackrabbit.apache.org/filevault-package-maven-plugin/package-mojo.html#packageType) 및 [아래의 FileVault Maven 구성 조각을](#marking-packages-for-deployment-by-adoube-cloud-manager) 참조하십시오.

>[!TIP]
>
>전체 코드 [에 대한 자세한 내용은 아래의 POM XML 코드 조각](#xml-package-types) 섹션을 참조하십시오.

## Adobe Cloud Manager에서 배포용 패키지 표시 {#marking-packages-for-deployment-by-adoube-cloud-manager}

기본적으로 Adobe Cloud Manager는 Maven 빌드에서 생성된 모든 패키지를 회수하지만 컨테이너(`all`) 패키지는 모든 코드 및 컨텐츠 패키지를 포함하는 단일 배포 아티팩트이므로 컨테이너( **) 패키지만 배포되도록**`all`해야 합니다. 이를 위해 Maven 빌드가 생성하는 다른 패키지는 의 FileVault 컨텐츠 패키지 마비안 플러그인 구성으로 표시되어야 합니다 `<properties><cloudManagerTarget>none</cloudManageTarget></properties>`.

>[!TIP]
>
>전체 코드 [에 대한 자세한 내용은 아래의 POM XML 코드 조각](#pom-xml-snippets) 섹션을 참조하십시오.

## 보고서 초기화{#repo-init}

Repo Init는 폴더 트리와 같은 공통 노드 구조부터 사용자, 서비스 사용자, 그룹 및 ACL 정의에 이르기까지 JCR 구조를 정의하는 지침 또는 스크립트를 제공합니다.

Repo Init의 주요 이점은 스크립트에서 정의한 모든 작업을 수행할 수 있는 암시적 권한을 가지고 있으며, 배포 라이프사이클에서 일찍 호출되어 시간 코드가 실행될 때까지 모든 필수 JCR 구조가 존재함을 보장합니다.

Repo Init는 스크립트로 프로젝트에서 라이브로 스크립트를 작성하는 동안 다음과 같은 mutable 구조를 정의하는 데 사용할 수 있으며 사용해야 합니다. `ui.config`

+ 기준 컨텐츠 구조
+ 서비스 사용자
+ 사용자
+ 그룹
+ ACL

Repo Init 스크립트는 `scripts` `RepositoryInitializer` OSGi 출하 시 구성의 항목으로 저장되므로 실행 모드를 통해 암시적으로 타깃팅할 수 있으므로 AEM 작성자 및 AEM 게시 서비스의 Repo Init 스크립트 또는 환경(Dev, Stage 및 Prod) 간에도 차이가 날 수 있습니다.

Repo Init OSGi 구성은 다중 행을 지원하므로 [`.config` OSGi 구성 형식](https://sling.apache.org/documentation/bundles/configuration-installer-factory.html#configuration-files-config-1) 으로 작성할 수 있습니다. 이는 OSGi 구성을 정의하는 데 사용하는 모범 사례 [`.cfg.json` 에 대한 예외입니다](https://sling.apache.org/documentation/bundles/configuration-installer-factory.html#configuration-files-cfgjson-1).

사용자 및 그룹을 정의할 때는 그룹만 애플리케이션의 일부로 간주되며, 이 경우 기능에 대한 필수 요소만 여기에서 정의해야 합니다. 조직 사용자 및 그룹은 AEM에서 런타임 시 정의되어야 합니다.예를 들어, 사용자 정의 워크플로우가 지정된 그룹에 작업을 할당하는 경우, AEM 응용 프로그램에서 Repo Init를 통해 해당 그룹이 정의되어야 하지만, 그룹화가 &quot;Wendy&#39;s Team&quot; 및 &quot;Sean&#39;s Team&quot;과 같은 단순한 조직일 경우, 이러한 작업은 AEM에서 런타임 시 가장 잘 정의되고 관리됩니다.

>[!TIP]
>
>Repo Init 스크립트 *는* 인라인 `scripts` 필드에 정의해야 하며 `references` 구성은 작동하지 않습니다.

Repo Init 스크립트의 전체 용어는 [Apache Sling Repo Init 설명서에서 확인할 수 있습니다](https://sling.apache.org/documentation/bundles/repository-initialization.html#the-repoinit-repository-initialization-language).

>[!TIP]
>
>전체 코드 [조각에 대한 자세한 내용은 아래 Repo Init Snippets](#snippet-repo-init) 섹션을 참조하십시오.

## 저장소 구조 패키지 {#repository-structure-package}

코드 패키지를 사용하려면 FileVault Maven 플러그인의 구성을 구성하여 구조적 의존의 정확성을 `<repositoryStructurePackage>` 적용하는 것이 필요합니다(한 코드 패키지가 다른 코드 패키지에 설치되지 않도록 하기). 프로젝트에 사용할 저장소 구조 패키지를 [직접 만들 수 있습니다](repository-structure-package.md).

이는 코드 **패키지에만** 필요하며, 이는 표시된 패키지를 의미합니다 `<packageType>application</packageType>`.

응용 프로그램에 대한 저장소 구조 패키지를 생성하는 방법을 알아보려면 저장소 구조 패키지 [개발을 참조하십시오](repository-structure-package.md).

컨텐츠 패키지(`<packageType>content</packageType>`)에는 이 저장소 구조 패키지가 **필요하지** 않습니다.

>[!TIP]
>
>전체 코드 [에 대한 자세한 내용은 아래의 POM XML 코드 조각](#xml-repository-structure-package) 섹션을 참조하십시오.

## 컨테이너 패키지에 하위 패키지 포함{#embeddeds}

컨텐츠 또는 코드 패키지는 특수 &quot;사이드 카&quot; 폴더에 저장되며 FileVault Maven 플러그인의 `<embeddeds>` 구성을 사용하여 AEM 작성자, AEM 게시 또는 둘 다에 설치되도록 타깃팅할 수 있습니다. 구성은 `<subPackages>` 사용하지 않아야 합니다.

일반적인 활용 사례는 다음과 같습니다.

+ AEM 작성자 사용자와 AEM 게시 사용자 간에 다른 ACL/권한
+ AEM 작성자에서만 활동을 지원하는 데 사용되는 구성
+ 백오피스 시스템과의 통합과 같은 코드, AEM 작성자에서만 실행

![패키지 포함](assets/embeddeds.png)

AEM 작성자, AEM 게시 또는 둘 다를 대상으로 하기 위해 패키지는 특수 폴더 위치의 `all` 컨테이너 패키지에 다음 형식으로 포함됩니다.

`/apps/<app-name>-packages/(content|application|container)/install(.author|.publish)?`

이 폴더 구조 분류:

+ 첫 번째 수준 폴더는 **여야** 합니다 `/apps`.
+ 두 번째 수준 폴더는 폴더 이름에 대한 `-packages` 게시물이 고정된 응용 프로그램을 나타냅니다. 대부분의 경우 모든 하위 패키지가 포함된 단일 2차 수준 폴더만 있을 수 있지만 응용 프로그램의 논리 구조를 가장 잘 나타내는 2차 수준 폴더를 만들 수 있습니다.
   + `/apps/my-app-packages`
   + `/apps/my-other-app-packages`
   + `/apps/vendor-packages`

   >[!WARNING]
   >
   >계약에 따라, 하위 패키지 포함 폴더의 이름은 접미사를 붙여넣습니다 `-packages`. 이렇게 하면 배포 코드와 컨텐츠 패키지가 파괴적이고 반복적인 설치 비헤이비어가 발생하는 하위 패키지의 대상 폴더 **를 배포하지** 않습니다 `/apps/<app-name>/...` .

+ 세 번째 수준 폴더는 다음 중 하나여야 합니다.
   `application`, `content` 또는 `container`
   + 이 `application` 폴더에는 코드 패키지가 들어 있습니다.
   + 폴더에는 콘텐트 패키지가 `content` 들어 있습니다.
   + 이 `container` 폴더에는 AEM 응용 프로그램에서 포함할 수 있는 [추가 응용 프로그램 패키지가](#extra-application-packages) 들어 있습니다.
이 폴더 이름은 포함된 패키지의 [패키지 유형에](#package-types) 해당합니다.
+ 4단계 폴더에는 하위 패키지가 들어 있으며 다음 중 하나여야 합니다.
   + `install` aem 작성자 및 AEM **게시 모두에** 설치하려면
   + `install.author` aem **작성자에만** 설치
   + `install.publish` aem **게시에만** 설치할 수 있습니다. `install.author` 참고: 타깃은 지원되 `install.publish` 는 대상입니다. 다른 실행 모드 **는 지원되지 않습니다** .

예를 들어 AEM 작성자 및 게시 특정 패키지가 포함된 배포는 다음과 같이 표시될 수 있습니다.

+ `all` 컨테이너 패키지에는 단일 배포 아티팩트를 만들기 위해 다음 패키지가 포함됩니다.
   + `ui.apps` aem 작성자 및 AEM 게시 모두에 배포 코드 포함 `/apps/my-app-packages/application/install`
   + `ui.apps.author` 배포 코드를 AEM 제작자에게만 배포 `/apps/my-app-packages/application/install.author`
   + `ui.content` aem 작성자 및 AEM 게시 모두에 컨텐츠 및 구성 배포 `/apps/my-app-packages/content/install`
   + `ui.content.publish` aem 게시에만 컨텐츠 및 구성 배포 시 임베드됨 `/apps/my-app-packages/content/install.publish`

>[!TIP]
>
>전체 코드 [에 대한 자세한 내용은 아래의 POM XML 코드 조각](#xml-embeddeds) 섹션을 참조하십시오.

### 컨테이너 패키지의 필터 정의 {#container-package-filter-definition}

컨테이너 패키지에 코드 및 컨텐츠 하위 패키지가 포함되어 있기 때문에 내장된 대상 경로를 컨테이너 프로젝트의 `filter.xml` 에 추가하여 내장 패키지가 내장된 컨테이너 패키지에 포함되도록 해야 합니다.

배포할 하위 패키지가 포함된 2차 수준 폴더의 `<filter root="/apps/<my-app>-packages"/>` 항목을 추가하면 됩니다.

>[!TIP]
>
>전체 코드 [에 대한 자세한 내용은 아래의 POM XML 코드 조각](#xml-container-package-filters) 섹션을 참조하십시오.

## 타사 패키지 포함 {#embedding-3rd-party-packages}

모든 패키지는 [Adobe의 공용 Maven 아티팩트 저장소](https://repo.adobe.com/nexus/content/groups/public/com/adobe/) 또는 액세스 가능한 공용, 참조 가능한 타사 Maven 아티팩트 저장소를 통해 사용할 수 있어야 합니다.

타사 패키지가 **Adobe의 공용 Maven 아티팩트 저장소에**&#x200B;있는 경우 Adobe Cloud Manager가 아티팩트를 해결하는 데 더 이상 구성할 필요가 없습니다.

타사 패키지가 **공개 타사 Maven 아티팩트 저장소에**&#x200B;있는 경우 이 리포지토리는 프로젝트의 `pom.xml` 저장소에 등록되어 위에 [설명한 방법 다음에 포함되어야 합니다](#embeddeds).

타사 응용 프로그램/커넥터를 프로젝트 컨테이너( `all``all`) 패키지의 컨테이너로 포함시켜야 합니다.

Maven 종속성을 추가하는 것은 표준 Maven 사례를 따르고, 타사 객체(코드 및 컨텐츠 패키지)를 포함하는 것은 위에 [요약되어 있습니다](#embedding-3rd-party-packages).

>[!TIP]
>
>전체 코드 [에 대한 자세한 내용은 아래의 POM XML 코드 조각](#xml-3rd-party-maven-repositories) 섹션을 참조하십시오.

## 패키지 간 `ui.apps` 패키지 `ui.content` 종속성 {#package-dependencies}

패키지를 제대로 설치하려면 패키지 간 종속성을 설정하는 것이 좋습니다.

일반 규칙은 가변 컨텐츠(`ui.content`)를 포함하는 패키지로, 변경 가능한 컨텐츠의 렌더링 및 사용을 지원하는 불변의 코드(`ui.apps`)에 따라 달라져야 합니다.

이 일반 규칙의 주목할 만한 예외는 불변량 코드 패키지(`ui.apps` 또는 기타)가 OSGi 번들만을 __포함하는__ 경우입니다. 이 경우 AEM 패키지는 종속성이 선언되지 않습니다. 이는 OSGi 번들을 __포함하고 있는__ 불변성 코드 패키지는 AEM 패키지 관리자에 등록되어 있지 않으므로, 이에 따라 모든 AEM 패키지에는 불만족스러운 종속성이 있으며 설치되지 않기 때문입니다.

>[!TIP]
>
>전체 코드 [에 대한 자세한 내용은 아래의 POM XML 코드 조각](#xml-package-dependencies) 섹션을 참조하십시오.

컨텐츠 패키지 종속성에 대한 일반적인 패턴은 다음과 같습니다.

### 단순 배포 패키지 종속성 {#simple-deployment-package-dependencies}

단순 케이스는 가변 `ui.content` 컨텐츠 패키지를 변경할 수 없는 코드 패키지에 따라 `ui.apps` 설정합니다.

+ `all` 종속성이 없습니다.
   + `ui.apps` 종속성이 없습니다.
   + `ui.content` 에 따라 `ui.apps`

### 복잡한 배포 패키지 종속성 {#complex-deploxment-package-dependencies}

복잡한 배포는 간단한 사례에 따라 확장되며 해당 변경 가능한 컨텐츠와 불변경 코드 패키지 간의 종속성을 설정합니다. 필요에 따라 변경할 수 없는 코드 패키지에도 종속성을 설정할 수 있습니다.

+ `all` 종속성이 없습니다.
   + `common.ui.apps.common` 종속성이 없습니다.
   + `site-a.ui.apps` 에 따라 `common.ui.apps`
   + `site-a.ui.content` 에 따라 `site-a.ui.apps`
   + `site-b.ui.apps` 에 따라 `common.ui.apps`
   + `site-b.ui.content` 에 따라 `site-b.ui.apps`

## 로컬 개발 및 배포 {#local-development-and-deployment}

이 문서에 나와 있는 프로젝트 구조와 조직은 **완벽하게 호환되는** 로컬 개발 AEM 인스턴스입니다.

## POM XML 조각 {#pom-xml-snippets}

다음은 Maven 프로젝트에 추가하여 위 권장 사항에 맞게 Maven `pom.xml` 구성 조각을 추가할 수 있는 Maven 구성 조각입니다.

### 패키지 유형 {#xml-package-types}

하위 패키지로 배포된 코드 및 컨텐츠 패키지는 포함된 내용에 따라 **애플리케이션** 또는 **컨텐츠**&#x200B;패키지 유형을 선언해야 합니다.

#### 컨테이너 패키지 유형 {#container-package-types}

컨테이너 프로젝트 `all/pom.xml` 에서 **a를 선언하지 않습니다** `<packageType>`.

#### 코드(불변수) 패키지 유형 {#immutable-package-types}

코드 패키지는 로 설정해야 `packageType` 합니다 `application`.

에서 `ui.apps/pom.xml`플러그인 선언의 `<packageType>application</packageType>` `filevault-package-maven-plugin` 빌드 구성 지시문은 해당 패키지 유형을 선언합니다.

```xml
...
<build>
  <plugins>
    <plugin>
      <groupId>org.apache.jackrabbit</groupId>
      <artifactId>filevault-package-maven-plugin</artifactId>
      <extensions>true</extensions>
      <configuration>
        <group>${project.groupId}</group>
        <name>my-app.ui.apps</name>
        <packageType>application</packageType>
        <accessControlHandling>merge</accessControlHandling>
        <properties>
          <cloudManagerTarget>none</cloudManagerTarget>
        </properties>
      </configuration>
    </plugin>
    ...
```

#### 컨텐트(가변) 패키지 유형 {#mutable-package-types}

콘텐츠 패키지는 `packageType` 로 설정해야 합니다 `content`.

에서 `ui.content/pom.xml`플러그인 선언의 `<packageType>content</packageType>` build configuration directive `filevault-package-maven-plugin` 는 패키지 유형을 선언합니다.

```xml
...
<build>
  <plugins>
    <plugin>
      <groupId>org.apache.jackrabbit</groupId>
      <artifactId>filevault-package-maven-plugin</artifactId>
      <extensions>true</extensions>
      <configuration>
        <group>${project.groupId}</group>
        <name>my-app.ui.content</name>
        <packageType>content</packageType>
        <accessControlHandling>merge</accessControlHandling>
        <properties>
          <cloudManagerTarget>none</cloudManagerTarget>
        </properties>
      </configuration>
    </plugin>
    ...
```

### Adobe Cloud Manager 배포에 대한 패키지 표시 {#cloud-manager-target}

컨테이너( **) 프로젝트를 제외한** 모든 프로젝트에서`all`패키지를 생성하는 모든 프로젝트 `<cloudManagerTarget>none</cloudManagerTarget>` 에서 플러그인 선언 `<properties>` 의 `filevault-package-maven-plugin` 구성에 **추가하여 Adobe 클라우드 관리자가 배포하지** 않도록 합니다. 컨테이너(`all`) 패키지는 Cloud Manager를 통해 배포되는 단일 패키지여야 하며, 이 패키지에는 모든 필수 코드와 콘텐츠 패키지가 포함됩니다.

```xml
...
<build>
  <plugins>
    <plugin>
      <groupId>org.apache.jackrabbit</groupId>
      <artifactId>filevault-package-maven-plugin</artifactId>
      <extensions>true</extensions>
      <configuration>
        ...
        <properties>
          <cloudManagerTarget>none</cloudManagerTarget>
        </properties>
      </configuration>
    </plugin>
    ...
```

### 보고서 초기화{#snippet-repo-init}

Repo Init 스크립트가 포함된 Repo Init 스크립트는 속성을 통해 OSGi 팩토리 구성에 `RepositoryInitializer` 정의됩니다 `scripts` . 이러한 스크립트는 OSGi 구성 내에서 정의되므로 일반적인 `../config.<runmode>` 폴더 의미 체계를 사용하여 실행 모드로 쉽게 범위를 지정할 수 있습니다.

스크립트는 일반적으로 여러 줄의 선언이므로 JSON 기반 `.config` `.cfg.json` 형식보다 파일에서 정의하는 것이 더 쉽습니다.

`/apps/my-app/config.author/org.apache.sling.jcr.repoinit.RepositoryInitializer-author.config`

```plain
scripts=["
    create service user my-data-reader-service

    set ACL on /var/my-data
        allow jcr:read for my-data-reader-service
    end

    create path (sling:Folder) /conf/my-app/settings
"]
```

OSGi `scripts` 속성은 Apache Sling의 [Repo Init 언어로 정의된 지시어를 포함합니다](https://sling.apache.org/documentation/bundles/repository-initialization.html#the-repoinit-repository-initialization-language).

### 저장소 구조 패키지 {#xml-repository-structure-package}

코드 패키지 `ui.apps/pom.xml` 를 선언하는 다른 `pom.xml` 저장소 구조 패키지(`<packageType>application</packageType>`)에서 다음 저장소 구조 패키지 구성을 FileVault Maven 플러그인에 추가합니다. 프로젝트에 사용할 저장소 구조 패키지를 [직접 만들 수 있습니다](repository-structure-package.md).

```xml
...
<build>
  <plugins>
    <plugin>
      <groupId>org.apache.jackrabbit</groupId>
      <artifactId>filevault-package-maven-plugin</artifactId>
      <extensions>true</extensions>
      <configuration>
        ...
        <repositoryStructurePackages>
          <repositoryStructurePackage>
              <groupId>${project.groupId}</groupId>
              <artifactId>ui.apps.structure</artifactId>
              <version>${project.version}</version>
          </repositoryStructurePackage>
        </repositoryStructurePackages>
      </configuration>
    </plugin>
    ...
```

### 컨테이너 패키지에 하위 패키지 포함 {#xml-embeddeds}

에서 `all/pom.xml`다음 `<embeddeds>` 지시문을 플러그인 `filevault-package-maven-plugin` 선언에 추가합니다. 구성 **은** `<subPackages>` 사용하지 마십시오. 이 구성 `/etc/packages` 에 `/apps/my-app-packages/<application|content|container>/install(.author|.publish)?`가 아닌 하위 패키지가 포함됩니다.

```xml
...
<plugin>
  <groupId>org.apache.jackrabbit</groupId>
  <artifactId>filevault-package-maven-plugin</artifactId>
  <extensions>true</extensions>
  <configuration>
      ...
      <embeddeds>

          <!-- Include the application's ui.apps and ui.content packages -->
          <!-- Ensure the artifactIds are correct -->

          <!-- OSGi Bundle Jar file that deploys to BOTH AEM Author and AEM Publish -->
          <embedded>
              <groupId>${project.groupId}</groupId>
              <artifactId>my-app.core</artifactId>
              <type>jar</type>
              <target>/apps/my-app-packages/application/install</target>
          </embedded>

          <!-- Code package that deploys to BOTH AEM Author and AEM Publish -->
          <embedded>
              <groupId>${project.groupId}</groupId>
              <artifactId>my-app.ui.apps</artifactId>
              <type>zip</type>
              <target>/apps/my-app-packages/application/install</target>
          </embedded>

           <!-- OSGi configuration code package that deploys to BOTH AEM Author and AEM Publish -->
          <embedded>
              <groupId>${project.groupId}</groupId>
              <artifactId>my-app.ui.config</artifactId>
              <type>zip</type>
              <target>/apps/my-app-packages/application/install</target>
          </embedded>

          <!-- Code package that deploys ONLY to AEM Author -->
          <embedded>
              <groupId>${project.groupId}</groupId>
              <artifactId>my-app.ui.apps.author</artifactId>
              <type>zip</type>
              <target>/apps/my-app-packages/application/install.author</target>
          </embedded>

          <!-- Content package that deploys to BOTH AEM Author and AEM Publish -->
          <embedded>
              <groupId>${project.groupId}</groupId>
              <artifactId>my-app.ui.content</artifactId>
              <type>zip</type>
              <target>/apps/my-app-packages/content/install</target>
          </embedded>

          <!-- Content package that deploys ONLY to AEM Publish -->
          <embedded>
              <groupId>${project.groupId}</groupId>
              <artifactId>my-app.ui.content.publish-only</artifactId>
              <type>zip</type>
              <target>/apps/my-app-packages/content/install.publish</target>
          </embedded>

          <!-- Include any other extra packages  -->
          <embedded>
              <groupId>com.vendor.x</groupId>
              <artifactId>vendor.plug-in.all</artifactId>
              <type>zip</type>
              <target>/apps/vendor-packages/container/install</target>
          </embedded>
      <embeddeds>
  </configuration>
</plugin>
...
```

### 컨테이너 패키지의 필터 정의 {#xml-container-package-filters}

프로젝트의 ( `all``filter.xml` )에 배포할 하위 패키지가 포함된`all/src/main/content/jcr_root/META-INF/vault/definition/filter.xml`폴더 **를** 포함시킵니다 `-packages` .

```xml
<filter root="/apps/my-app-packages"/>
```

포함 대상 `/apps/*-packages` 에 여러 개를 사용하는 경우 모두 여기에서 열거되어야 합니다.

### 타사 마웬 저장소 {#xml-3rd-party-maven-repositories}

>[!WARNING]
>
>추가적인 Maven 리포지토리가 종속성에 대해 확인되면 더 많은 Maven 저장소를 추가하면 빌드 시간이 연장될 수 있습니다.

원자로 프로젝트의 지침에 필요한 타사 공용 Maven 리포지토리 지시문을 `pom.xml`추가합니다. 전체 `<repository>` 구성은 타사 저장소 공급자로부터 사용할 수 있어야 합니다.

```xml
<repositories>
  ...
  <repository>
      <id>3rd-party-repository</id>
      <name>Public 3rd Party Repository</name>
      <url>https://repo.3rdparty.example.com/...</url>
      <releases>
          <enabled>true</enabled>
          <updatePolicy>never</updatePolicy>
      </releases>
      <snapshots>
          <enabled>false</enabled>
      </snapshots>
  </repository>
  ...
</repositories>
```

### 패키지 간 `ui.apps` 패키지 `ui.content` 종속성 {#xml-package-dependencies}

에서 `ui.content/pom.xml`다음 `<dependencies>` 지시문을 플러그인 `filevault-package-maven-plugin` 선언에 추가합니다.

```xml
...
<plugin>
  <groupId>org.apache.jackrabbit</groupId>
  <artifactId>filevault-package-maven-plugin</artifactId>
  <extensions>true</extensions>
  <configuration>
      ...
      <dependencies>
        <!-- Declare the content package dependency in the ui.content/pom.xml on the ui.apps project -->
        <dependency>
            <groupId${project.groupId}</groupId>
            <artifactId>my-app.ui.apps</artifactId>
            <version>${project.version}</version>
        </dependency>
      </dependencies>
    ...
  </configuration>
</plugin>
...
```

### 컨테이너 프로젝트의 Target 폴더 정리 {#xml-clean-container-package}

추가 `all/pom.xml` 에서 Maven 빌드 전에 대상 디렉토리를 정리할 `maven-clean-plugin` 플러그인을 추가합니다.

```xml
<plugins>
  ...
  <plugin>
    <artifactId>maven-clean-plugin</artifactId>
    <executions>
      <execution>
        <id>auto-clean</id>
        <!-- Run at the beginning of the build rather than the default, which is after the build is done -->
        <phase>initialize</phase>
        <goals>
          <goal>clean</goal>
        </goals>
      </execution>
    </executions>
  </plugin>
  ...
</plugins>
```

## 추가 리소스 {#additional-resources}

+ [Maven을 사용한 패키지 관리](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/vlt-mavenplugin.html)
+ [FileVault 컨텐츠 패키지 Maven 플러그인](http://jackrabbit.apache.org/filevault-package-maven-plugin/)