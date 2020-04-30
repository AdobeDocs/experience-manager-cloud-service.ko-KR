---
title: AEM 프로젝트 구조
description: Adobe Experience Manager Cloud Service에 배포할 패키지 구조를 정의하는 방법에 대해 학습합니다.
translation-type: tm+mt
source-git-commit: 57a5b6b80097938dd63a73734676ff374db3ecce

---


# AEM 프로젝트 구조

>[!TIP]
>
>이 문서가 이러한 학습 및 개념을 바탕으로 [작성되므로 AEM Project Tranype의](https://docs.adobe.com/content/help/ko-KR/experience-manager-core-components/using/developing/archetype/overview.html)기본 기능과 [FileVault Content Maven 플러그인에](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/vlt-mavenplugin.html) 익숙해지십시오.

이 문서에서는 변경 가능하고 변경할 수 없는 컨텐츠의 분리를 존중하여 Adobe Experience Manager Maven 프로젝트에서 AEM Cloud Service와 호환하는 데 필요한 변경 사항에 대해 설명합니다.필수 종속성이 충돌하지 않고 결정적 배포를 만들기 위해 설정되었습니다.그리고 그것들은 배치 가능한 구조로 포장되어 있습니다.

AEM 애플리케이션 배포는 단일 AEM 패키지로 구성되어야 합니다. 이 패키지는 다시 코드, 구성 및 지원 기준 컨텐츠를 포함하여 애플리케이션에서 작동하는 데 필요한 모든 것을 구성하는 하위 패키지를 포함해야 합니다.

AEM에서는 **컨텐츠와** **코드를**&#x200B;분리해야 **합니다. 즉, 단일 컨텐츠 패키지가** 두 영역에 **** `/apps` 모두 배포할 수 없습니다(예: 런타임 쓰기 가능 영역).보관소의 `/content``/conf`, `/home`또는 기타 사항 `/apps`)에 대한 정보를 표시합니다. 대신 AEM에 배포하려면 애플리케이션에서 코드와 컨텐츠를 개별 패키지로 분리해야 합니다.

이 문서에 설명된 패키지 구조는 로컬 개발 배포 및 AEM Cloud 서비스 **배포와 모두** 호환됩니다.

>[!TIP]
>
>이 문서에 요약된 구성은 AEM Project Maven [Tranype 21 이상에서](https://github.com/adobe/aem-project-archetype/releases)제공됩니다.

## 저장소의 변경 가능 영역과 불변경 영역 {#mutable-vs-immutable}

`/apps` 및 AEM은 AEM이 시작된 후(예: 런타임 시) 변경(생성, 업데이트, 삭제) `/libs` **** 할 수 없으므로 변경할 수 없는 영역으로 간주됩니다. 실행 시 변경할 수 없는 영역을 변경하려고 하면 실패합니다.

저장소의 다른 모든 것, `/content``/conf`, `/var``/etc`, `/oak:index``/system`, `/tmp`,등 는 모두 **변경 가능한** 영역이므로 런타임 시 변경할 수 있습니다.

>[!WARNING]
>
> 이전 버전의 AEM에서와 마찬가지로 수정해서는 `/libs` 안 됩니다. AEM 제품 코드만 다음 위치에 배포할 수 `/libs`있습니다.

## 권장 패키지 구조 {#recommended-package-structure}

![Experience Manager 프로젝트 패키지 구조](assets/content-package-organization.png)

이 다이어그램은 권장 프로젝트 구조 및 패키지 배포 객체에 대한 개요를 제공합니다.

권장되는 애플리케이션 배포 구조는 다음과 같습니다.

+ 패키지 또는 코드 `ui.apps` 패키지에는 배포할 모든 코드가 들어 있으며 `/apps`배포만 포함됩니다. 패키지의 일반적인 요소에는 다음이 포함되지만 이에 국한되지 않습니다. `ui.apps`
   + OSGi 번들
      + `/apps/my-app/install`
   + OSGi 구성
      + `/apps/my-app/config`
   + HTL 스크립트
      + `/apps/my-app/components`
   + JavaScript 및 CSS(클라이언트 라이브러리 사용)
      + `/apps/my-app/clientlibs`
   + /libs 오버레이
      + `/apps/cq`, `/apps/dam/`, 등이 됩니다.
   + 대체 컨텍스트 인식 구성
      + `/apps/settings`
   + ACL(권한)
      + 임의 `rep:policy` 경로 `/apps`
   + Repo Init OSGi 구성 지침(및 관련 스크립트)
      + [Repo Init](#repo-init) 는 AEM 애플리케이션의 논리적으로 구성 가능한 컨텐츠를 배포하는 데 권장되는 방법입니다. Repo Init를 사용하여 다음을 정의해야 합니다.
         + 기본 컨텐츠 구조
            + `/conf/my-app`
            + `/content/my-app`
            + `/content/dam/my-app`
         + 사용자
         + 서비스 사용자
         + 그룹
         + ACL(권한)
            + 모든 `rep:policy` 경로(변경 가능 또는 변경 불가능)
+ 패키지 또는 컨텐츠 `ui.content` 패키지에 모든 컨텐츠와 구성이 포함되어 있습니다. 패키지의 일반적인 요소에는 다음이 포함되지만 이에 국한되지 않습니다. `ui.content`
   + 컨텍스트 인식 구성
      + `/conf`
   + 필수, 복잡한 컨텐츠 구조(예: Report Init에 정의된 기준선 컨텐츠 구조를 기반으로 구축되어 확장되는 컨텐츠 빌드아웃입니다.
      + `/content`, `/content/dam`, 등이 됩니다.
   + 관리 태깅 분류
      + `/content/cq:tags`
   + Oak 인덱스
      + `/oak:index`
   + 기타 레거시 노드
      + `/etc`
+ 패키지는 `all` 포함 패키지만 `ui.apps` 및 `ui.content` 패키지를 포함하는 컨테이너 패키지입니다. 패키지에 `all` 자체 컨텐츠가 **** 없어야 하지만, 모든 배포를 하위 패키지에 위임해야 합니다.

   이제 패키지는 [구성이 아닌 Maven FileVault Package](#embeddeds)Maven 플러그인의 임베드 구성을 `<subPackages>` 사용하여 포함됩니다.

   복잡한 Experience Manager 배포의 경우 AEM의 특정 사이트 또는 테넌트를 나타내는 여러 `ui.apps` 및 `ui.content` 프로젝트/패키지를 생성하는 것이 좋습니다. 이 작업이 수행되면 변경 가능한 컨텐츠와 변경 불가능한 컨텐츠 간의 분할이 준수되고 필요한 컨텐츠 패키지가 `all` 컨테이너 컨텐츠 패키지에 하위 패키지로 추가됩니다.

   예를 들어 복잡한 배포 컨텐츠 패키지 구조는 다음과 같을 수 있습니다.

   + `all` 컨텐츠 패키지에는 단일 배포 아티팩트를 만들기 위해 다음 패키지가 포함됩니다.
      + `ui.apps.common` 사이트 A와 사이트 B **에서** 모두 필요로 하는 코드를 배포합니다.
      + `ui.apps.site-a` 사이트 A에 필요한 배포 코드
      + `ui.content.site-a` 사이트 A에 필요한 컨텐트 및 구성 배포
      + `ui.apps.site-b` 사이트 B에 필요한 코드 배포
      + `ui.content.site-b` 사이트 B에 필요한 컨텐트 및 구성 배포

## 패키지 유형 {#package-types}

패키지는 선언된 패키지 유형으로 표시됩니다.

+ 컨테이너 패키지에는 `packageType` 집합이 없어야 합니다.
+ 코드(변경할 수 없음) 패키지는 `packageType` 로 설정해야 합니다 `application`.
+ 컨텐츠(변경 가능) 패키지는 로 `packageType` 설정해야 합니다 `content`.

자세한 내용은 [아래의 Apache Jackrabbit FileVault - Package Maven 플러그인 설명서](https://jackrabbit.apache.org/filevault-package-maven-plugin/package-mojo.html#packageType) 및 [FileVault Maven 구성 조각을](#marking-packages-for-deployment-by-adoube-cloud-manager) 참조하십시오.

>[!TIP]
>
>전체 코드 [조각에 대한 자세한 내용은](#xml-package-types) 아래의 POM XML 코드 조각 섹션을 참조하십시오.

## Adobe Cloud Manager에서 배포용 패키지 표시 {#marking-packages-for-deployment-by-adoube-cloud-manager}

기본적으로 Adobe Cloud Manager는 Maven 빌드에서 생성된 모든 패키지를 회수하지만 컨테이너(`all`) 패키지는 모든 코드 및 컨텐츠 패키지가 포함된 단일 배포 아티팩트이므로 컨테이너( **) 패키지만**`all`배포해야 합니다. 이를 위해 Maven 빌드가 생성하는 다른 패키지는 의 FileVault 컨텐츠 패키지 Maven 플러그인 구성으로 표시되어야 합니다 `<properties><cloudManagerTarget>none</cloudManageTarget></properties>`.

>[!TIP]
>
>전체 코드 [조각에 대한 자세한 내용은](#pom-xml-snippets) 아래의 POM XML 코드 조각 섹션을 참조하십시오.

## 보고서 초기화{#repo-init}

Repo Init는 폴더 트리와 같은 공통 노드 구조에서 사용자, 서비스 사용자, 그룹 및 ACL 정의에 이르기까지 JCR 구조를 정의하는 지침 또는 스크립트를 제공합니다.

Repo Init의 주요 이점은 스크립트에 의해 정의된 모든 작업을 수행할 수 있는 암시적 권한이 있으며 배포 라이프사이클의 초기에 호출되어 시간 코드가 실행될 때까지 모든 필수 JCR 구조가 존재함을 보장한다는 것입니다.

Repo Init 스크립트는 프로젝트에서 스크립트로 라이브되지만, 다음과 같은 변경 가능한 구조를 정의하는 데 사용할 수 있으며 사용해야 합니다. `ui.apps`

+ 기본 컨텐츠 구조
   + Examples: `/content/my-app`, `/content/dam/my-app`, `/conf/my-app/settings`
+ 서비스 사용자
+ 사용자
+ 그룹
+ ACL

Repo Init 스크립트는 OSGi 팩토리 구성의 `scripts` 항목으로 저장되므로 `RepositoryInitializer` 런타임 모드를 통해 암시적으로 타깃팅할 수 있으므로 AEM Author 및 AEM Publish Services의 Repo Init 스크립트 또는 Envs(Dev, Stage 및 Prod) 간 차이점을 확인할 수 있습니다.

사용자 및 그룹을 정의할 때 그룹만 애플리케이션의 일부로 간주되며, 이 경우 해당 기능에 대한 필수 구성 요소가 여기에 정의되어 있어야 합니다. 조직 사용자 및 그룹은 AEM에서 런타임 시 여전히 정의되어 있어야 합니다.예를 들어, 사용자 지정 워크플로가 지정된 그룹에 작업을 할당하는 경우, AEM 애플리케이션에서 Repo Init를 통해 해당 그룹이 정의되어야 하지만, 그룹화가 &quot;Wendy&#39;s Team&quot; 및 &quot;Sean&#39;s Team&quot;과 같은 단순한 조직일 경우, 이것이 AEM에서 런타임 시 가장 잘 정의되고 관리됩니다.

>[!TIP]
>
>Repo Init 스크립트를 인라인 *필드에 정의해야* 하며 `scripts` `references` 구성이 작동하지 않습니다.

Repo Init 스크립트의 전체 어휘는 Apache Sling Repo [Init 문서에서](https://sling.apache.org/documentation/bundles/repository-initialization.html#the-repoinit-repository-initialization-language)사용할 수 있습니다.

>[!TIP]
>
>전체 코드 [조각에 대한 자세한 내용은](#snippet-repo-init) 아래 Repo Init Snippets 섹션을 참조하십시오.

## 저장소 구조 패키지 {#repository-structure-package}

코드 패키지를 사용하려면 FileVault Maven 플러그인의 구성을 구성하여 구조적 종속성이 정확하도록 `<repositoryStructurePackage>` 강제 적용합니다(한 코드 패키지가 다른 코드 패키지에 설치되지 않도록 하기). 프로젝트에 [대한 저장소 구조 패키지를 직접](repository-structure-package.md)만들 수 있습니다.

이는 코드 패키지에 **대해서만 필요합니다** . 즉, 표시된 모든 패키지를 의미합니다 `<packageType>application</packageType>`.

응용 프로그램에 대한 저장소 구조 패키지를 생성하는 방법에 대한 자세한 내용은 저장소 구조 [패키지 개발을 참조하십시오](repository-structure-package.md).

컨텐츠 패키지(`<packageType>content</packageType>`)에는 이 저장소 구조 패키지가 **필요하지 않습니다** .

>[!TIP]
>
>전체 코드 [조각에 대한 자세한 내용은](#xml-repository-structure-package) 아래의 POM XML 코드 조각 섹션을 참조하십시오.

## 컨테이너 패키지에 하위 패키지 포함{#embeddeds}

콘텐츠 또는 코드 패키지는 특수 &quot;측면&quot; 폴더에 배치되며 FileVault Maven 플러그인의 `<embeddeds>` 구성을 사용하여 AEM 작성자, AEM 게시 또는 둘 다에 설치되도록 타깃팅할 수 있습니다. 구성은 `<subPackages>` 사용하지 마십시오.

일반적인 사용 사례는 다음과 같습니다.

+ AEM 작성자 사용자와 AEM 게시 사용자 간에 다른 ACL/권한
+ AEM 작성자의 활동만 지원하는 데 사용되는 구성
+ 백오피스 시스템과의 통합과 같은 코드, AEM 작성자에서만 실행

![패키지 포함](assets/embeddeds.png)

AEM 작성자, AEM 게시 또는 둘 다를 타깃팅하기 위해 패키지는 특수 폴더 위치의 `all` 컨테이너 패키지에 다음 형식으로 포함됩니다.

`/apps/<app-name>-packages/(content|application)/install(.author|.publish)?`

이 폴더 구조 분류:

+ 첫 번째 수준 폴더는 **반드시** 있어야 합니다 `/apps`.
+ 두 번째 수준 폴더는 폴더 이름에 대한 `-packages` 게시물을 고정한 응용 프로그램을 나타냅니다. 대부분의 경우 모든 하위 패키지가 아래에 포함된 단일 2차 수준 폴더만 있을 수 있지만, 애플리케이션의 논리적 구조를 가장 잘 나타내는 2차 수준 폴더를 만들 수 있습니다.
   + `/apps/my-app-packages`
   + `/apps/my-other-app-packages`
   + `/apps/vendor-packages`
   >[!WARNING]
   >
   >규칙에 따라, 하위 패키지 포함 폴더의 이름은 `-packages`의 접미어로 지정됩니다. 이렇게 하면 배포 코드 및 컨텐츠 패키지가 파괴적이고 반복적인 설치 동작을 **일으키는 하위 패키지의 대상 폴더를 배포하지** 않습니다 `/apps/<app-name>/...` .

+ 세 번째 수준 폴더는 다음 중 하나여야 합니다.
   `application` 또는 `content`
   + 이 `application` 폴더에는 코드 패키지가 들어 있습니다.
   + 폴더 `content` 금메달리스트 콘텐츠 패키지이 폴더 이름은 이 폴더에 포함된 패키지의 [패키지 유형에](#package-types) 해당해야 합니다.
+ 4단계 폴더에는 하위 패키지가 들어 있으며 다음 중 하나여야 합니다.
   + `install` aem 작성자 및 AEM **게시 모두에** 설치하려면
   + `install.author` to **only** install on AEM author
   + `install.publish` to **only** install on AEM publishNote that only `install.author` and `install.publish` are supported targets. 다른 실행 모드는 **지원되지 않습니다** .

예를 들어, AEM 작성자 및 게시 특정 패키지가 포함된 배포는 다음과 같을 수 있습니다.

+ `all` 컨테이너 패키지에는 단일 배포 아티팩트를 만들기 위해 다음 패키지가 포함됩니다.
   + `ui.apps` 임베드된 코드를 AEM 작성자 및 AEM 게시 모두에 `/apps/my-app-packages/application/install` 배포
   + `ui.apps.author` 배포 코드에 포함된 코드를 AEM `/apps/my-app-packages/application/install.author` 작성자만 배포
   + `ui.content` 내장 컨텐츠 및 구성을 `/apps/my-app-packages/content/install` AEM 작성자 및 AEM 게시 모두에 배포
   + `ui.content.publish` 컨텐츠 및 구성을 `/apps/my-app-packages/content/install.publish` 배포 AEM 게시에만 포함

>[!TIP]
>
>전체 코드 [조각에 대한 자세한 내용은](#xml-embeddeds) 아래의 POM XML 코드 조각 섹션을 참조하십시오.

### 컨테이너 패키지의 필터 정의 {#container-package-filter-definition}

컨테이너 패키지에 코드와 컨텐츠 하위 패키지가 포함되어 있기 때문에 내장 대상 경로를 컨테이너 프로젝트의 컨테이너 패키지에 `filter.xml` 추가해야 내장 패키지가 빌드될 때 컨테이너 패키지에 포함됩니다.

배포할 하위 패키지가 들어 있는 2차 수준 폴더의 항목을 추가하면 됩니다. `<filter root="/apps/<my-app>-packages"/>`

>[!TIP]
>
>전체 코드 [조각에 대한 자세한 내용은](#xml-container-package-filters) 아래의 POM XML 코드 조각 섹션을 참조하십시오.

## 타사 패키지 임베드 {#embedding-3rd-party-packages}

모든 패키지는 Adobe의 공개 [Maven 아티팩트 저장소](https://repo.adobe.com/nexus/content/groups/public/com/adobe/) 또는 액세스 가능한 공개, 참조 타사 Maven 아티팩트 저장소를 통해 사용할 수 있어야 합니다.

타사 패키지가 Adobe의 공용 **Maven 아티팩트 저장소에**&#x200B;있는 경우 Adobe Cloud Manager가 아티팩트를 해결하는 데 더 이상 구성할 필요가 없습니다.

타사 패키지가 **공개 타사 Maven 아티팩트 저장소에**&#x200B;있는 경우, 이 리포지토리는 프로젝트의 `pom.xml` 등록 후 위에 [요약된 방법 다음에 포함되어야 합니다](#embeddeds). 타사 응용 프로그램/커넥터에서 코드 및 컨텐츠 패키지를 모두 필요로 하는 경우, 각각은 컨테이너(`all`) 패키지의 올바른 위치에 포함되어야 합니다.

Maven 종속성을 추가하는 것은 표준 Maven 사례를 따르고, 타사 객체(코드 및 컨텐츠 패키지)를 임베드하는 방법은 위에 [요약되어](#embedding-3rd-party-packages)있습니다.

>[!TIP]
>
>전체 코드 [조각에 대한 자세한 내용은](#xml-3rd-party-maven-repositories) 아래의 POM XML 코드 조각 섹션을 참조하십시오.

## 패키지에서 생성된 패키지 간의 `ui.apps` 패키지 `ui.content` 종속성 {#package-dependencies}

패키지를 제대로 설치하려면 패키지 간 종속성을 설정하는 것이 좋습니다.

일반 규칙은 변경 가능한 컨텐츠가 포함된 패키지입니다(`ui.content`). 변경 가능한 컨텐츠의 렌더링 및 사용을 지원하는 변경 불가능한 컨텐츠(`ui.apps`)에 따라 달라져야 합니다.

>[!TIP]
>
>전체 코드 [조각에 대한 자세한 내용은](#xml-package-dependencies) 아래의 POM XML 코드 조각 섹션을 참조하십시오.

컨텐츠 패키지 종속성에 대한 일반적인 패턴은 다음과 같습니다.

### 단순 배포 패키지 종속성 {#simple-deployment-package-dependencies}

간단한 사례는 변경 가능한 `ui.content` 컨텐츠 패키지를 변경할 수 없는 `ui.apps` 코드 패키지에 따라 다르게 설정합니다.

+ `all` 종속성 없음
   + `ui.apps` 종속성 없음
   + `ui.content` 종속됨 `ui.apps`

### 복잡한 배포 패키지 종속성 {#complex-deploxment-package-dependencies}

복잡한 배포는 간단한 경우에 따라 확장되며 해당 변경 가능한 컨텐츠와 불변경 코드 패키지 간의 종속성을 설정합니다. 필요에 따라 변경할 수 없는 코드 패키지 간에 종속성을 설정할 수도 있습니다.

+ `all` 종속성 없음
   + `ui.apps.common` 종속성 없음
   + `ui.apps.site-a` 종속됨 `ui.apps.common`
   + `ui.content.site-a` 종속됨 `ui.apps.site-a`
   + `ui.apps.site-b` 종속됨 `ui.apps.common`
   + `ui.content.site-b` 종속됨 `ui.apps.site-b`

## 로컬 개발 및 배포 {#local-development-and-deployment}

이 문서에 설명된 프로젝트 구조 및 구성은 **완벽하게 호환되는** 로컬 개발 AEM 인스턴스입니다.

## POM XML 조각 {#pom-xml-snippets}

다음은 위의 권장 사항에 맞게 Maven 프로젝트에 추가할 수 있는 Maven `pom.xml` 구성 조각입니다.

### 패키지 유형 {#xml-package-types}

하위 패키지로 배포된 코드 및 컨텐츠 패키지는 포함된 내용에 따라 **애플리케이션** 또는 **컨텐츠의**&#x200B;패키지 유형을 선언해야 합니다.

#### 컨테이너 패키지 유형 {#container-package-types}

컨테이너 `all/pom.xml` 프로젝트는 **을 선언하지 않습니다** `<packageType>`.

#### 코드(변경할 수 없음) 패키지 유형 {#immutable-package-types}

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
        <name>${my-app.ui.apps}</name>
        <packageType>application</packageType>
        <accessControlHandling>merge</accessControlHandling>
        <properties>
          <cloudManagerTarget>none</cloudManagerTarget>
        </properties>
      </configuration>
    </plugin>
    ...
```

#### 컨텐츠(가변) 패키지 유형 {#mutable-package-types}

컨텐츠 패키지는 로 `packageType` 설정해야 합니다 `content`.

에서 `ui.content/pom.xml`plugin 선언의 `<packageType>content</packageType>` build configuration directive of the `filevault-package-maven-plugin` plugin declaration 선언에는 패키지 유형이 선언됩니다.

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
        <name>${my-app.ui.content}</name>
        <packageType>content</packageType>
        <accessControlHandling>merge</accessControlHandling>
        <properties>
          <cloudManagerTarget>none</cloudManagerTarget>
        </properties>
      </configuration>
    </plugin>
    ...
```

### Adobe Cloud Manager 배포를 위한 패키지 표시 {#cloud-manager-target}

컨테이너( **) 프로젝트를** 제외한`all`모든 프로젝트에서 플러그인 선언의 `<cloudManagerTarget>none</cloudManagerTarget>` 구성에 `<properties>` 플러그인을 추가하여 Adobe Cloud Manager에 의해 배포되지 `filevault-package-maven-plugin` **** 않도록 합니다. TheE container (`all`) 패키지는 Cloud Manager를 통해 배포되는 단일 패키지로, 모든 필수 코드와 콘텐츠 패키지를 포함합니다.

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

Repo Init 스크립트가 포함된 Repo Init 스크립트는 `RepositoryInitializer` `scripts` 속성을 통해 OSGi 팩토리 구성에 정의됩니다. 이러한 스크립트는 OSGi 구성 내에서 정의되므로 일반적인 `../config.<runmode>` 폴더 의미 체계를 사용하여 런타임 모드로 쉽게 범위가 지정될 수 있습니다.

스크립트는 일반적으로 여러 줄 선언이므로 XML 기반 `.config` `sling:OsgiConfig` 형식보다 파일에서 정의하는 것이 쉽습니다.

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

OSGi `scripts` 속성은 Apache Sling의 Repo [Init 언어로](https://sling.apache.org/documentation/bundles/repository-initialization.html#the-repoinit-repository-initialization-language)정의된 지시어를 포함합니다.

### 저장소 구조 패키지 {#xml-repository-structure-package}

코드 패키지( `ui.apps/pom.xml` )를 선언하는 `pom.xml` 및 기타`<packageType>application</packageType>`파일에서 다음 저장소 구조 패키지 구성을 FileVault Maven 플러그인에 추가합니다. 프로젝트에 [대한 저장소 구조 패키지를 직접](repository-structure-package.md)만들 수 있습니다.

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

에서 `all/pom.xml`다음 `<embeddeds>` 지시문을 `filevault-package-maven-plugin` 플러그인 선언에 추가합니다. 이 구성 요소에는 **구성 대신 하위 패키지가 포함되므로** `<subPackages>` 구성을 사용하지 마십시오 `/etc/packages` `/apps/my-app-packages/<application|content>/install(.author|.publish)?`.

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

          <!-- Code package that deploys to BOTH AEM Author and AEM Publish -->
          <embedded>
              <groupId>${project.groupId}</groupId>
              <artifactId>my-app.ui.apps</artifactId>
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

          <!-- Include any other extra packages such as AEM WCM Core Components -->
          <embedded>
              <groupId>com.adobe.cq</groupId>
              <!-- Not to be confused; WCM Core Components' Code package's artifact is named `.content` -->
              <artifactId>core.wcm.components.content</artifactId>
              <type>zip</type>
              <target>/apps/vendor-packages/application/install</target>
          </embedded>

          <embedded>
              <groupId>com.adobe.cq</groupId>
              <!-- Not to be confused; WCM Core Components' Content package's artifact is named `.conf` -->
              <artifactId>core.wcm.components.conf</artifactId>
              <type>zip</type>
              <target>/apps/vendor-packages/content/install</target>
          </embedded>
      <embeddeds>
  </configuration>
</plugin>
...
```

### 컨테이너 패키지의 필터 정의 {#xml-container-package-filters}

프로젝트의 `all` ( `filter.xml` )에 배포할 하위 패키지가 포함된`all/src/main/content/jcr_root/META-INF/vault/definition/filter.xml`폴더를 **** 포함시킵니다 `-packages` .

```xml
<filter root="/apps/my-app-packages"/>
```

임베드 대상에 여러 `/apps/*-packages` 개가 사용되는 경우 모두 여기에서 열거되어야 합니다.

### 타사 마웬 저장소 {#xml-3rd-party-maven-repositories}

>[!WARNING]
> 추가적인 Maven 저장소가 세부 설정을 확인하므로 더 많은 Maven 저장소를 추가하면 빌드 시간이 연장될 수 있습니다.

원자로 프로젝트의 `pom.xml`경우 필요한 타사 공개 Maven 리포지토리 지시를 추가합니다. 전체 `<repository>` 구성은 타사 저장소 공급자에서 사용할 수 있어야 합니다.

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

### 패키지에서 생성된 패키지 간의 `ui.apps` 패키지 `ui.content` 종속성 {#xml-package-dependencies}

에서 `ui.content/pom.xml`다음 `<dependencies>` 지시문을 `filevault-package-maven-plugin` 플러그인 선언에 추가합니다.

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

### 컨테이너 프로젝트의 대상 폴더 정리 {#xml-clean-container-package}

에서 Maven 빌드 전에 대상 디렉토리를 정리할 `all/pom.xml` `maven-clean-plugin` 플러그인을 추가합니다.

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

+ [Maven을 사용하여 패키지 관리](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/vlt-mavenplugin.html)
+ [FileVault 컨텐츠 패키지 Maven 플러그인](http://jackrabbit.apache.org/filevault-package-maven-plugin/)