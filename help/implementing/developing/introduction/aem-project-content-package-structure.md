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
>이 문서가 이러한 학습 및 개념을 바탕으로 작성되므로 기본 [AEM Project Tranype 사용](https://docs.adobe.com/content/help/ko-KR/experience-manager-core-components/using/developing/archetype/overview.html) 및 [FileVault Content Maven 플러그인](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/vlt-mavenplugin.html)에 익숙해지십시오.

이 문서에서는 Adobe Experience Manager Maven 프로젝트가 변경 및 변경 불가능한 컨텐츠의 분할을 준수하도록 하고, 상충성이 없는 배포 생성을 위해 종속성을 설정하며, 배포 가능한 구조로 패키징되도록 하여 Cloud Service으로 호환하는 데 필요한 변경 사항에 대해 설명합니다.

AEM 애플리케이션 배포는 단일 AEM 패키지로 구성되어야 합니다. 따라서 이 패키지에는 코드, 구성 및 지원 기본 컨텐츠를 포함하여 응용 프로그램에서 기능에 필요한 모든 것을 구성하는 하위 패키지가 들어 있어야 합니다.

AEM에는 **content** 및 **code**&#x200B;이(가) 구분되어야 합니다. 즉, 단일 컨텐츠 패키지 **가****`/apps` 및 런타임 쓰기 가능 영역(예:저장소의 `/content`, `/conf`, `/home` 또는 `/apps`이 아닌 것.** 대신 AEM으로 배포하려면 애플리케이션의 코드와 컨텐츠를 개별 패키지로 분리해야 합니다.

이 문서에 요약된 패키지 구조는 **로컬 개발 배포 및 AEM Cloud Service 배포과 호환됩니다.**

>[!TIP]
>
>이 문서에 요약된 구성은 [AEM Project Maven Tranype 24 이상](https://github.com/adobe/aem-project-archetype/releases)에서 제공합니다.

## 변경 가능 영역과 저장소의 변경 불가능한 영역 {#mutable-vs-immutable}

`/apps` 및 `/libs`**는 AEM이 시작된 후(예: 런타임 시) 변경(만들기, 업데이트, 삭제)할 수 없으므로 AEM에서 변경할 수 없는 영역으로 간주됩니다.** 런타임 시 변경할 수 없는 영역을 변경하려고 하면 오류가 발생합니다.

저장소의 다른 모든 것, `/content`, `/conf`, `/var`, `/etc`, `/oak:index`, `/system`, `/tmp` 등. 은 모두 **mutable** 영역입니다. 즉, 런타임 시 변경할 수 있습니다.

>[!WARNING]
>
>이전 버전의 AEM에서와 마찬가지로 `/libs`은(는) 수정할 수 없습니다. AEM 제품 코드만 `/libs`에 배포할 수 있습니다.

### Oak 인덱스 {#oak-indexes}

Oak 인덱스(`/oak:index`)는 Cloud Service 배포 프로세스로 AEM에서 특히 관리됩니다. 이는 새 코드 이미지로 전환하기 전에 Cloud Manager가 새 인덱스가 배포되고 완전히 다시 색인화될 때까지 기다려야 하기 때문입니다.

이러한 이유로 Oak 색인은 런타임 시 변경할 수 있지만 변경 가능한 패키지를 설치하기 전에 설치할 수 있도록 Oak 인덱스를 코드로 배포해야 합니다. 따라서 `/oak:index` 구성은 코드 패키지의 일부이며 아래 설명된 바와 같이 [컨텐트 패키지의 일부가 아닙니다.](#recommended-package-structure)

>[!TIP]
>
>AEM에서 Cloud Service으로 색인화에 대한 자세한 내용은 [컨텐트 검색 및 인덱싱](/help/operations/indexing.md) 문서를 참조하십시오.

## 권장 패키지 구조 {#recommended-package-structure}

![Experience Manager 프로젝트 패키지 구조](assets/content-package-organization.png)

이 다이어그램은 권장 프로젝트 구조 및 패키지 배포 아티팩트에 대한 개요를 제공합니다.

권장되는 애플리케이션 배포 구조는 다음과 같습니다.

### 코드 패키지/OSGi 번들

+ OSGi 번들 Jar 파일이 생성되어 모든 프로젝트에 직접 포함됩니다.

+ `ui.apps` 패키지에는 배포할 모든 코드가 들어 있으며 `/apps`에만 배포됩니다. `ui.apps` 패키지의 일반적인 요소에는 다음이 포함되지만 이에 국한되지 않습니다.
   + [구성 요소 정의 및 ](https://docs.adobe.com/content/help/ko-KR/experience-manager-htl/using/overview.html) HTLscripts
      + `/apps/my-app/components`
   + JavaScript 및 CSS([클라이언트 라이브러리](/help/implementing/developing/introduction/clientlibs.md)를 통해)
      + `/apps/my-app/clientlibs`
   + [](/help/implementing/developing/introduction/overlays.md) 오버레이  `/libs`
      + `/apps/cq`, `/apps/dam/`, 등이 됩니다.
   + 대체 컨텍스트 인식 구성
      + `/apps/settings`
   + ACL(권한)
      + `/apps` 아래의 모든 경로에 대한 `rep:policy`

+ `ui.config` 패키지에는 모든 [OSGi 구성](/help/implementing/deploying/configuring-osgi.md)이 들어 있습니다.
   + 실행 모드 특정 OSGi 구성 정의를 포함하는 조직 폴더
      + `/apps/my-app/osgiconfig`
   + Cloud Service 배포 대상으로 모든 대상 AEM에 적용되는 기본 OSGi 구성을 포함하는 공통 OSGi 구성 폴더
      + `/apps/my-app/osgiconfig/config`
   + Cloud Service 배포 대상으로 모든 대상 AEM에 적용되는 기본 OSGi 구성이 포함된 모드별 OSGi 구성 폴더를 실행합니다.
      + `/apps/my-app/osgiconfig/config.<author|publish>.<dev|stage|prod>`
   + Repo Init OSGi 구성 스크립트
      + [Repo ](#repo-init) Initiative는 AEM 애플리케이션의 논리적으로 구성(변경할 수 있음) 컨텐츠를 배포하는 데 권장되는 방법을 제공합니다. Repo Init OSGi 구성은 위에서 설명한 바와 같이 적절한 `config.<runmode>` 폴더에 위치해야 하며 다음을 정의하는 데 사용해야 합니다.
         + 기본 컨텐츠 구조
         + 사용자
         + 서비스 사용자
         + 그룹
         + ACL(권한)

### 콘텐츠 패키지

+ `ui.content` 패키지에는 모든 내용 및 구성이 들어 있습니다. 컨텐트 패키지에는 `ui.apps` 또는 `ui.config` 패키지에 없는 모든 노드 정의가 들어 있고, 즉 `/apps` 또는 `/oak:index`에 없는 모든 노드 정의가 들어 있습니다. `ui.content` 패키지의 일반적인 요소에는 다음이 포함되지만 이에 국한되지 않습니다.
   + 컨텍스트 인식 구성
      + `/conf`
   + 필수, 복잡한 컨텐츠 구조(예: Repo Init에 정의된 기준 요소 컨텐츠 구조를 기반으로 구축되어 이전 Baseline 컨텐츠 구조를 확장하는 컨텐츠 빌드아웃)
      + `/content`, `/content/dam`, 등이 됩니다.
   + 관리 분류 체계
      + `/content/cq:tags`
   + 기존 etc 노드(이상적, 비-etc 위치로 마이그레이션)
      + `/etc`

### 컨테이너 패키지

+ `all` 패키지는 배포 가능한 객체, OSGI 번들 Jar 파일, `ui.apps`, `ui.config` 및 `ui.content` 패키지만 포함하는 컨테이너 패키지입니다. `all` 패키지에는 **내용 또는 코드**&#x200B;가 없어야 하며, 모든 배포를 하위 패키지 또는 OSGi 번들 Jar 파일에 위임할 수 있습니다.

   이제 패키지는 `<subPackages>` 구성 대신 Maben [FileVault 패키지 Maven 플러그인의 임베드 구성](#embeddeds)을 사용하여 포함됩니다.

   복잡한 Experience Manager 배포의 경우 AEM의 특정 사이트 또는 테넌트를 나타내는 여러 개의 `ui.apps`, `ui.config` 및 `ui.content` 프로젝트/패키지를 생성하는 것이 좋습니다. 이 작업이 수행되면 변경 가능한 컨텐츠와 변경 불가능한 컨텐츠 간의 분할이 충족되는지 확인하고 필요한 컨텐츠 패키지와 OSGi 번들 Jar 파일이 `all` 컨테이너 컨텐츠 패키지에 하위 패키지로 포함되어 있는지 확인합니다.

   예를 들어 복잡한 배포 컨텐츠 패키지 구조는 다음과 같을 수 있습니다.

   + `all` 컨텐츠 패키지에는 단일 배포 아티팩트를 만들기 위해 다음 패키지가 포함됩니다.
      + `common.ui.apps` 사이트 A와  **** 사이트 B에서 필요한 코드를 배포합니다.
      + `site-a.core` 사이트 A에 필요한 OSGi 번들 Jar
      + `site-a.ui.apps` 사이트 A에 필요한 배포 코드
      + `site-a.ui.config` 사이트 A에 필요한 OSGi 구성 배포
      + `site-a.ui.content` 사이트 A에 필요한 컨텐트 및 구성 배포
      + `site-b.core` 사이트 B에 필요한 OSGi 번들 Jar
      + `site-b.ui.apps` 사이트 B에 필요한 코드 배포
      + `site-b.ui.config` 사이트 B에 필요한 OSGi 구성 배포
      + `site-b.ui.content` 사이트 B에 필요한 컨텐트 및 구성 배포

### 추가 응용 프로그램 패키지{#extra-application-packages}

자체 코드와 컨텐츠 패키지로 구성된 다른 AEM 프로젝트를 AEM 배포에서 사용하는 경우 해당 컨테이너 패키지를 프로젝트의 `all` 패키지에 포함해야 합니다.

예를 들어 2개의 공급업체 AEM 애플리케이션을 포함하는 AEM 프로젝트는 다음과 같이 보일 수 있습니다.

+ `all` 컨텐츠 패키지에는 단일 배포 아티팩트를 만들기 위해 다음 패키지가 포함됩니다.
   + `core` AEM 응용 프로그램에 필요한 OSGi 번들 Jar
   + `ui.apps` aem 응용 프로그램에 필요한 코드를 배포합니다.
   + `ui.config` aem 응용 프로그램에 필요한 OSGi 구성 배포
   + `ui.content` aem 응용 프로그램에 필요한 컨텐트 및 구성 배포
   + `vendor-x.all` 공급업체 X 애플리케이션에서 필요한 모든 것(코드 및 컨텐츠)을 배포합니다.
   + `vendor-y.all` 공급업체 Y 애플리케이션에서 필요한 모든 것(코드 및 컨텐츠)을 배포합니다.

## 패키지 유형 {#package-types}

패키지는 선언된 패키지 유형으로 표시됩니다.

+ 컨테이너 패키지는 `packageType`을 `container`로 설정해야 합니다.
+ 코드(변경할 수 없음) 패키지는 `packageType`을 `application`로 설정해야 합니다.
+ 내용(변경 가능) 패키지는 `packageType`을 `content`로 설정해야 합니다.

자세한 내용은 [Apache Jackrabbit FileVault - Package Maven 플러그인 설명서](https://jackrabbit.apache.org/filevault-package-maven-plugin/package-mojo.html#packageType) 및 아래의 [FileVault Maven 구성 조각](#marking-packages-for-deployment-by-adoube-cloud-manager)을 참조하십시오.

>[!TIP]
>
>전체 조각을 보려면 아래의 [POM XML 코드 조각](#xml-package-types) 섹션을 참조하십시오.

## Adobe Cloud Manager {#marking-packages-for-deployment-by-adoube-cloud-manager}에 의해 배포용으로 패키지 표시

기본적으로 Adobe Cloud Manager는 Maven 빌드에서 생성된 모든 패키지를 회수하지만 컨테이너(`all`) 패키지는 모든 코드와 콘텐츠 패키지를 포함하는 단일 배포 아티팩트이므로 컨테이너(`all`)만 **이(가) 배포되도록 해야 합니다.** 이를 위해 Maven 빌드가 생성하는 다른 패키지는 `<properties><cloudManagerTarget>none</cloudManageTarget></properties>`의 FileVault 콘텐츠 패키지 Maven 플러그인 구성으로 표시되어야 합니다.

>[!TIP]
>
>전체 조각을 보려면 아래의 [POM XML 코드 조각](#pom-xml-snippets) 섹션을 참조하십시오.

## 보고서 초기화{#repo-init}

Repo Init는 폴더 트리와 같은 공통 노드 구조부터 사용자, 서비스 사용자, 그룹 및 ACL 정의까지 JCR 구조를 정의하는 지침 또는 스크립트를 제공합니다.

Repo Init의 주요 이점은 스크립트에서 정의한 모든 작업을 수행할 수 있는 암시적 권한이 있으며, 배포 주기 초기에 호출되어 시간 코드가 실행될 때까지 모든 필수 JCR 구조가 존재함을 보장합니다.

Repo Init 스크립트는 `ui.config` 프로젝트에서 스크립트로 라이브되지만 다음과 같은 변경 가능한 구조를 정의하는 데 사용할 수 있으며 사용해야 합니다.

+ 기본 컨텐츠 구조
+ 서비스 사용자
+ 사용자
+ 그룹
+ ACL

Repo Init 스크립트는 `RepositoryInitializer` OSGi 팩토리 구성의 `scripts` 항목으로 저장되므로 실행 모드를 통해 암시적으로 타깃팅할 수 있으므로 AEM 작성자 및 AEM 게시 서비스의 Report Init 스크립트 또는 환경(Dev, Stage 및 Prod) 간에도 차이가 있을 수 있습니다.

Repo Init OSGi 구성은 [`.config` OSGi 구성 형식](https://sling.apache.org/documentation/bundles/configuration-installer-factory.html#configuration-files-config-1)에 가장 잘 기록되며, 이는 [`.cfg.json`를 사용하여 OSGi 구성을 정의하는 모범 사례에 대한 예외입니다](https://sling.apache.org/documentation/bundles/configuration-installer-factory.html#configuration-files-cfgjson-1).

사용자 및 그룹을 정의할 때 그룹만 애플리케이션의 일부로 간주되며, 이 경우 기능에 대한 필수 구성 요소가 여기에 정의되어 있어야 합니다. 조직 사용자 및 그룹은 AEM에서 런타임 시 여전히 정의되어 있어야 합니다.예를 들어 사용자 정의 워크플로우가 명명된 그룹에 작업을 할당하는 경우, AEM 응용 프로그램에서 Repo Init를 통해 해당 그룹이 정의되어야 하지만, 그룹화가 &quot;Wendy&#39;s Team&quot; 및 &quot;Sean&#39;s Team&quot;과 같은 단순한 조직일 경우 이 작업은 AEM에서 런타임에 가장 잘 정의되고 관리됩니다.

>[!TIP]
>
>보고서 초기화 스크립트 *는 인라인 `scripts` 필드에*&#x200B;을(를) 정의해야 하며 `references` 구성이 작동하지 않습니다.

Repo Init 스크립트의 전체 용어는 [Apache Sling Repo Init 설명서](https://sling.apache.org/documentation/bundles/repository-initialization.html#the-repoinit-repository-initialization-language)에서 사용할 수 있습니다.

>[!TIP]
>
>전체 조각을 보려면 아래의 [Repo Init Snippets](#snippet-repo-init) 섹션을 참조하십시오.

## 저장소 구조 패키지 {#repository-structure-package}

코드 패키지는 구조 의존성을 정확하게 적용하는 `<repositoryStructurePackage>`을 참조하도록 FileVault Maven 플러그인의 구성을 구성해야 합니다(한 코드 패키지가 다른 코드 패키지에 설치되지 않도록 확인). [프로젝트](repository-structure-package.md)에 대해 자신의 저장소 구조 패키지를 만들 수 있습니다.

이것은 **코드 패키지에 대해서만 필수**&#x200B;이며, 이것은 `<packageType>application</packageType>`로 표시된 패키지를 의미합니다.

응용 프로그램에 대한 저장소 구조 패키지를 만드는 방법에 대해 알아보려면 [저장소 구조 패키지 개발](repository-structure-package.md)을 참조하십시오.

콘텐츠 패키지(`<packageType>content</packageType>`) **이(가) 이 저장소 구조 패키지가 필요하지 않습니다.**

>[!TIP]
>
>전체 조각을 보려면 아래의 [POM XML 코드 조각](#xml-repository-structure-package) 섹션을 참조하십시오.

## 컨테이너 패키지에 하위 패키지 포함{#embeddeds}

내용 또는 코드 패키지는 특수 &quot;사이드 카&quot; 폴더에 저장되며 FileVault Maven 플러그인의 `<embeddeds>` 구성을 사용하여 AEM 작성자, AEM 게시 또는 둘 다에 설치되도록 타깃팅할 수 있습니다. `<subPackages>` 구성은 사용하지 않아야 합니다.

일반적인 활용 사례는 다음과 같습니다.

+ AEM 작성자 사용자와 AEM 게시 사용자 간에 다른 ACL/권한
+ AEM 작성자의 활동만 지원하는 데 사용되는 구성
+ 백오피스 시스템과의 통합과 같은 코드(AEM 작성자에서만 실행)

![패키지 포함](assets/embeddeds.png)

AEM 작성자, AEM 게시 또는 둘 다를 대상으로 하려면 패키지가 다음 형식으로 `all` 컨테이너 패키지에 포함된 특수 폴더-위치:

`/apps/<app-name>-packages/(content|application|container)/install(.author|.publish)?`

이 폴더 구조 분류:

+ 1차 수준 폴더 **은(는)** `/apps`여야 합니다.
+ 2차 수준 폴더는 폴더 이름에 대해 `-packages` 이후 고정을 가진 응용 프로그램을 나타냅니다. 대부분의 경우 모든 하위 패키지가 포함된 단일 2단계 폴더만 있을 수 있지만 응용 프로그램의 논리 구조를 가장 잘 나타내는 2차 수준 폴더를 만들 수 있습니다.
   + `/apps/my-app-packages`
   + `/apps/my-other-app-packages`
   + `/apps/vendor-packages`

   >[!WARNING]
   >
   >규칙에 따라 하위 패키지 포함 폴더의 이름은 `-packages`의 접미어로 지정됩니다. 이렇게 하면 배포 코드와 콘텐츠 패키지가 **이(가) 하위 패키지 `/apps/<app-name>/...`의 대상 폴더를 배포하지 않고 파괴적 및 순환 설치 비헤이비어가 발생합니다.**

+ 3차 수준 폴더는 다음 중 하나여야 합니다.
   `application`,  `content` or  `container`
   + `application` 폴더에는 코드 패키지가 들어 있습니다.
   + `content` 폴더에는 콘텐트 패키지가 들어 있습니다.
   + `container` 폴더에는 AEM 응용 프로그램에서 포함할 수 있는 [추가 응용 프로그램 패키지](#extra-application-packages)이 있습니다.
이 폴더 이름은 포함된 패키지의 [패키지 유형](#package-types)에 해당합니다.
+ 4번째 수준 폴더에는 하위 패키지가 들어 있으며 다음 중 하나여야 합니다.
   + `install` AEM 작성자 및 AEM  **** 게시 모두에 설치하려면
   + `install.author` aem  **** 제작자에게만 설치
   + `install.publish` 를  **** AEM 게시에만 설치하려면 지원되 `install.author` 는 타겟만  `install.publish` 참조하십시오. 다른 실행 모드 **은(는)**&#x200B;이(가) 지원되지 않습니다.

예를 들어 AEM 작성자 및 게시 특정 패키지가 포함된 배포는 다음과 같을 수 있습니다.

+ `all` 컨테이너 패키지에는 단일 배포 아티팩트를 만들기 위해 다음 패키지가 포함됩니다.
   + `ui.apps` aem  `/apps/my-app-packages/application/install` 작성자 및 AEM 게시에 배포 코드 포함
   + `ui.apps.author` 배포 코드를 AEM  `/apps/my-app-packages/application/install.author` 제작자에게만 포함
   + `ui.content` 컨텐츠를  `/apps/my-app-packages/content/install` 배포하고 구성을 AEM 작성자 및 AEM 게시에 포함함
   + `ui.content.publish` 컨텐츠를  `/apps/my-app-packages/content/install.publish` 배포하고 구성을 AEM 게시에만 포함

>[!TIP]
>
>전체 조각을 보려면 아래의 [POM XML 코드 조각](#xml-embeddeds) 섹션을 참조하십시오.

### 컨테이너 패키지의 필터 정의 {#container-package-filter-definition}

코드 및 컨텐츠 하위 패키지를 컨테이너 패키지에 포함하기 때문에 포함된 대상 경로를 컨테이너 프로젝트의 `filter.xml`에 추가하여 내장 패키지를 빌드할 때 컨테이너 패키지에 포함시켜야 합니다.

배포할 하위 패키지가 포함된 2차 수준 폴더의 `<filter root="/apps/<my-app>-packages"/>` 항목을 추가하면 됩니다.

>[!TIP]
>
>전체 조각을 보려면 아래의 [POM XML 코드 조각](#xml-container-package-filters) 섹션을 참조하십시오.

## 타사 패키지 포함 {#embedding-3rd-party-packages}

모든 패키지는 [Adobe의 공용 Maven 아티팩트 저장소](https://repo.adobe.com/nexus/content/groups/public/com/adobe/) 또는 액세스 가능한 공개 타사 Maven 아티팩트 저장소를 통해 사용할 수 있어야 합니다.

타사 패키지가 **Adobe의 공용 Maven 아티팩트 저장소**&#x200B;에 있는 경우 Adobe Cloud Manager에서 아티팩트를 해결하는 데 더 이상 구성할 필요가 없습니다.

타사 패키지가 **공개 제3자 마벤 아티팩트 저장소**&#x200B;에 있는 경우 이 리포지토리는 프로젝트의 `pom.xml`에 등록되어](#embeddeds)위에 요약된 [메서드 다음에 포함되어야 합니다.

타사 응용 프로그램/커넥터는 `all` 패키지를 프로젝트의 컨테이너(`all`) 패키지의 컨테이너로 사용하여 포함시켜야 합니다.

Maven 종속성을 추가하는 것은 표준 Maven 사례를 따르고, 제3자 가공물(코드 및 컨텐츠 패키지)을 포함하는 것은 [위에 요약된 ](#embedding-3rd-party-packages)입니다.

>[!TIP]
>
>전체 조각을 보려면 아래의 [POM XML 코드 조각](#xml-3rd-party-maven-repositories) 섹션을 참조하십시오.

## `ui.content` 패키지의 `ui.apps` 패키지 종속성{#package-dependencies}

패키지를 제대로 설치하려면 패키지 간 종속성을 설정하는 것이 좋습니다.

일반 규칙은 변경 가능한 컨텐츠(`ui.content`)를 포함하는 패키지로, 변경 가능한 컨텐츠의 렌더링 및 사용을 지원하는 변경할 수 없는 코드(`ui.apps`)에 따라 달라야 합니다.

이 일반 규칙의 주목할 만한 예외는 변경할 수 없는 코드 패키지(`ui.apps` 또는 기타 모든 패키지), __만 OSGi 번들을 포함하는 경우입니다.__ 이 경우 AEM 패키지는 종속성을 선언하지 않아야 합니다. 이는 변경할 수 없는 코드 패키지 __만 OSGi 번들을 포함하는__&#x200B;만 AEM Package Manager에 등록되어 있지 않기 때문에 그에 따라 AEM 패키지가 충족되지 않은 종속성을 가지며 설치하지 못합니다.

>[!TIP]
>
>전체 조각을 보려면 아래의 [POM XML 코드 조각](#xml-package-dependencies) 섹션을 참조하십시오.

컨텐츠 패키지 종속성에 대한 일반적인 패턴은 다음과 같습니다.

### 단순 배포 패키지 종속성 {#simple-deployment-package-dependencies}

단순 케이스는 `ui.apps` 불변경 코드 패키지에 종속되도록 `ui.content` 변경 가능한 컨텐츠 패키지를 설정합니다.

+ `all` 종속성이 없습니다.
   + `ui.apps` 종속성이 없습니다.
   + `ui.content` 에 따라  `ui.apps`

### 복잡한 배포 패키지 종속성 {#complex-deploxment-package-dependencies}

복잡한 배포는 간단한 사례에 따라 확대되며 해당 변경 가능한 컨텐츠와 불변경 코드 패키지 간의 종속성을 설정합니다. 필요에 따라 변경할 수 없는 코드 패키지에도 종속성을 설정할 수 있습니다.

+ `all` 종속성이 없습니다.
   + `common.ui.apps.common` 종속성이 없습니다.
   + `site-a.ui.apps` 에 따라  `common.ui.apps`
   + `site-a.ui.content` 에 따라  `site-a.ui.apps`
   + `site-b.ui.apps` 에 따라  `common.ui.apps`
   + `site-b.ui.content` 에 따라  `site-b.ui.apps`

## 로컬 개발 및 배포 {#local-development-and-deployment}

이 문서에 요약된 프로젝트 구조 및 구성은 **완전히 호환되는** 로컬 개발 AEM 인스턴스입니다.

## POM XML 조각 {#pom-xml-snippets}

다음은 위의 권장 사항에 맞게 Maven 프로젝트에 추가할 수 있는 Maven `pom.xml` 구성 조각입니다.

### 패키지 유형 {#xml-package-types}

하위 패키지로 배포되는 코드 및 내용 패키지는 포함된 내용에 따라 **application** 또는 **content**&#x200B;의 패키지 유형을 선언해야 합니다.

#### 컨테이너 패키지 유형 {#container-package-types}

`all/pom.xml` 프로젝트 **이(가)**&#x200B;를 선언하지 않습니다.`<packageType>`

#### 코드(변경할 수 없음) 패키지 유형 {#immutable-package-types}

코드 패키지는 `packageType`을 `application`로 설정해야 합니다.

`ui.apps/pom.xml`에서 `filevault-package-maven-plugin` 플러그인 선언의 `<packageType>application</packageType>` 빌드 구성 지시문은 해당 패키지 유형을 선언합니다.

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

#### 내용(변경 가능) 패키지 유형 {#mutable-package-types}

콘텐츠 패키지는 `packageType`을 `content`로 설정해야 합니다.

`ui.content/pom.xml`에서 `filevault-package-maven-plugin` 플러그인 선언의 `<packageType>content</packageType>` 빌드 구성 지시문이 해당 패키지 유형을 선언합니다.

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

패키지를 생성하는 모든 프로젝트에서 컨테이너(`all`) 프로젝트에 대해 **을(를) 제외한**&#x200B;은(는) `filevault-package-maven-plugin` 플러그인 선언의 `<properties>` 구성에 `<cloudManagerTarget>none</cloudManagerTarget>`을(를) 추가하여 **이(가) Adobe Cloud Manager에 의해 배포되지 않도록 합니다.** 컨테이너(`all`) 패키지는 Cloud Manager를 통해 배포되는 단일 패키지여야 하며, 이 패키지에는 필요한 모든 코드와 콘텐츠 패키지가 포함됩니다.

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

Repo Init 스크립트가 포함된 Repo Init 스크립트는 `scripts` 속성을 통해 `RepositoryInitializer` OSGi 팩토리 구성에 정의됩니다. 이러한 스크립트는 OSGi 구성에 정의되어 있으므로 일반적인 `../config.<runmode>` 폴더 의미 체계를 사용하여 실행 모드로 쉽게 범위를 지정할 수 있습니다.

스크립트는 일반적으로 여러 줄의 선언이므로 JSON 기반 `.cfg.json` 형식보다 `.config` 파일에서 스크립트를 정의하는 것이 더 쉽습니다.

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

`scripts` OSGi 속성에는 [Apache Sling의 Repo Init 언어](https://sling.apache.org/documentation/bundles/repository-initialization.html#the-repoinit-repository-initialization-language)에 의해 정의된 지시어가 포함되어 있습니다.

### 저장소 구조 패키지 {#xml-repository-structure-package}

`ui.apps/pom.xml` 및 코드 패키지(`<packageType>application</packageType>`)를 선언하는 다른 `pom.xml`에서 다음 저장소 구조 패키지 구성을 FileVault Maven 플러그인에 추가합니다. [프로젝트](repository-structure-package.md)에 대해 자신의 저장소 구조 패키지를 만들 수 있습니다.

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

`all/pom.xml`에서 다음 `<embeddeds>` 지시문을 `filevault-package-maven-plugin` 플러그인 선언에 추가합니다. **은(는) `/apps/my-app-packages/<application|content|container>/install(.author|.publish)?`이 아닌 `/etc/packages`에 하위 패키지를 포함하므로 `<subPackages>` 구성을 사용하지 마십시오.**

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

`all` 프로젝트의 `filter.xml`(`all/src/main/content/jcr_root/META-INF/vault/definition/filter.xml`)에서 배포할 하위 패키지가 들어 있는 **include** 폴더:`-packages`

```xml
<filter root="/apps/my-app-packages"/>
```

포함 대상에 여러 개의 `/apps/*-packages`이(가) 사용된 경우 모두 여기에서 열거되어야 합니다.

### 제3자 마벤 저장소 {#xml-3rd-party-maven-repositories}

>[!WARNING]
>
>추가 메이벤 리포지토리가 종속성에 대해 확인되므로 더 많은 메이벤 저장소를 추가하면 빌드 시간이 연장될 수 있습니다.

원자로 프로젝트의 `pom.xml`에 필요한 제3자 공용 Maven 리포지토리 지시문을 추가합니다. 전체 `<repository>` 구성은 타사 저장소 공급자에서 사용할 수 있어야 합니다.

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

### `ui.content` 패키지의 `ui.apps` 패키지 종속성{#xml-package-dependencies}

`ui.content/pom.xml`에서 다음 `<dependencies>` 지시문을 `filevault-package-maven-plugin` 플러그인 선언에 추가합니다.

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

### 컨테이너 프로젝트의 Target 폴더 {#xml-clean-container-package} 정리

`all/pom.xml`에서 Maven 빌드 전에 대상 디렉토리를 지울 `maven-clean-plugin` 플러그인을 추가합니다.

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