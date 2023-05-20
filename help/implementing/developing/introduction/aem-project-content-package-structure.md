---
title: AEM 프로젝트 구조
description: Adobe Experience Manager Cloud Service에 배포할 패키지 구조를 정의하는 방법에 대해 알아봅니다.
exl-id: 38f05723-5dad-417f-81ed-78a09880512a
source-git-commit: 47910a27118a11a8add6cbcba6a614c6314ffe2a
workflow-type: tm+mt
source-wordcount: '2931'
ht-degree: 12%

---

# AEM 프로젝트 구조

>[!TIP]
>
>기본 사항 숙지 [AEM Project Archetype](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html)및 [FileVault Content Maven 플러그인](/help/implementing/developing/tools/maven-plugin.md) 이 문서는 이러한 학습과 개념을 기반으로 합니다.

이 문서에서는 변경 가능한 컨텐츠와 변경할 수 없는 컨텐츠 분리를 사용하여 Adobe Experience Manager AEM Maven 프로젝트에 필요한 변경 사항을 as a Cloud Service으로 호환되도록 설명하고, 상충되는 배포가 없도록 종속성을 설정하고, 배포 가능한 구조로 패키지되어 있다는 점을 설명합니다.

AEM 애플리케이션 배포는 단일 AEM 패키지로 구성되어야 합니다. 이 패키지에는 코드, 구성 및 지원하는 모든 기본 콘텐츠를 포함하여 애플리케이션이 기능하는 데 필요한 모든 것을 구성하는 하위 패키지가 포함되어야 합니다.

AEM은 **콘텐츠** 및 **코드**- 단일 콘텐츠 패키지를 의미합니다. **할 수 없음** 배포 대상 **모두** `/apps` 런타임 쓰기 가능 영역(예: `/content`, `/conf`, `/home`또는 기타 `/apps`)을 참조하십시오. Instead, the application must separate code and content into discrete packages for deployment into AEM.

The package structure outlined in this document is compatible with **both** local development deployments and AEM Cloud Service deployments.

>[!TIP]
>
>이 문서에 설명된 구성은 [AEM Project Maven Archetype 24 이상](https://github.com/adobe/aem-project-archetype/releases).

## 저장소의 변경 가능한 영역과 변경 불가능한 영역 비교 {#mutable-vs-immutable}

`/apps` 및 `/libs`**는 AEM이 시작된 후(예: 런타임 시) 변경(만들기, 업데이트, 삭제)할 수 없으므로 AEM에서 변경할 수 없는 영역으로 간주됩니다.** 런타임 시 변경할 수 없는 영역을 변경하려고 하면 오류가 발생합니다.

저장소에 있는 모든 항목 `/content`, `/conf`, `/var`, `/etc`, `/oak:index`, `/system`, `/tmp`등 모두 **변하기 쉬워** 즉, 런타임 시 변경할 수 있습니다.

>[!WARNING]
>
>이전 버전의 AEM에서와 마찬가지로 `/libs` 수정해서는 안 됩니다. AEM 제품 코드만 `/libs`.

### Oak 색인 {#oak-indexes}

Oak 색인(`/oak:index`)는 특히 AEM as a Cloud Service 배포 프로세스에 의해 관리됩니다. Cloud Manager는 새 코드 이미지로 전환하기 전에 새 색인이 배포되고 완전히 다시 색인화될 때까지 기다려야 하기 때문입니다.

따라서 Oak 색인은 런타임에 변경할 수 있지만, 변경 가능한 패키지를 설치하기 전에 설치할 수 있도록 코드로 배포해야 합니다. 따라서 `/oak:index` 구성은 콘텐츠 패키지의 일부가 아니라 코드 패키지의 일부입니다 [아래에 기술한 바와 같이](#recommended-package-structure).

>[!TIP]
>
>AEM as a Cloud Service 색인화에 대한 자세한 내용은 문서를 참조하십시오. [콘텐츠 검색 및 색인화](/help/operations/indexing.md).

## 권장 패키지 구조 {#recommended-package-structure}

![Experience Manager 프로젝트 패키지 구조](assets/content-package-organization.png)

이 다이어그램은 권장 프로젝트 구조 및 패키지 배포 아티팩트에 대한 개요를 제공합니다.

권장되는 애플리케이션 배포 구조는 다음과 같습니다.

### 코드 패키지/OSGi 번들

+ OSGi 번들 Jar 파일이 생성되며 모든 프로젝트에 직접 포함됩니다.

+ 다음 `ui.apps` 패키지에는 배포할 모든 코드가 포함되어 있으며 `/apps`. 의 일반적인 요소 `ui.apps` 패키지에는 다음이 포함되지만 이에 국한되지 않습니다.
   + [구성 요소 정의 및 HTL](https://experienceleague.adobe.com/docs/experience-manager-htl/using/overview.html?lang=ko-KR) 스크립트
      + `/apps/my-app/components`
   + JavaScript 및 CSS(를 통해 [클라이언트 라이브러리](/help/implementing/developing/introduction/clientlibs.md))
      + `/apps/my-app/clientlibs`
   + [오버레이](/help/implementing/developing/introduction/overlays.md) / `/libs`
      + `/apps/cq`, `/apps/dam/`등
   + 대체 컨텍스트 인식 구성
      + `/apps/settings`
   + ACL(권한)
      + 임의 `rep:policy` 모든 경로 `/apps`
   + [미리 컴파일된 번들형 스크립트](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/precompiled-bundled-scripts.html)

>[!NOTE]
>
>모든 환경에 동일한 코드를 배포해야 합니다. 이는 스테이징 환경에서 신뢰도 검증이 프로덕션에 포함될 수 있도록 하기 위해 필요합니다. 자세한 내용은 다음 섹션 을 참조하십시오 [실행 모드](/help/implementing/deploying/overview.md#runmodes).


### 컨텐츠 패키지

+ 다음 `ui.content` 패키지에는 모든 콘텐츠 및 구성이 포함됩니다. 콘텐츠 패키지에는에 없는 모든 노드 정의가 포함되어 있습니다 `ui.apps` 또는 `ui.config` 패키지 또는 다른 말로 다음에 없는 모든 `/apps` 또는 `/oak:index`. 의 일반적인 요소 `ui.content` 패키지에는 다음이 포함되지만 이에 국한되지 않습니다.
   + 컨텍스트 인식 구성
      + `/conf`
   + 필요한 복잡한 콘텐츠 구조(예: 저장소 초기화에 정의된 기준 콘텐츠 구조를 기반으로 하고 이를 지나 확장하는 콘텐츠 빌드-아웃)
      + `/content`, `/content/dam`등
   + 관리되는 태그 지정 분류
      + `/content/cq:tags`
   + 레거시 etc 노드(이상적으로는 비/etc 위치로 마이그레이션함)
      + `/etc`

### 컨테이너 패키지

+ 다음 `all` 패키지는 배포 가능한 아티팩트, OSGI 번들 Jar 파일, `ui.apps`, `ui.config` 및 `ui.content` embed로 패키지 다음 `all` 패키지에는 다음이 없어야 합니다. **모든 콘텐츠 또는 코드** 모든 배포를 하위 패키지 또는 OSGi 번들 Jar 파일로 리포지토리에 위임합니다.

   이제 Maven을 사용하여 패키지가 포함됩니다 [FileVault 패키지 Maven 플러그인의 임베디드 구성](#embeddeds), 대신 `<subPackages>` 구성.

   복잡한 Experience Manager 배포의 경우 여러 개를 만드는 것이 바람직할 수 있습니다 `ui.apps`, `ui.config` 및 `ui.content` AEM의 특정 사이트 또는 테넌트를 나타내는 프로젝트/패키지 이 작업을 수행하는 경우 변경할 수 있는 콘텐츠와 변경할 수 없는 콘텐츠 간의 분할이 준수되는지 확인하고 필수 콘텐츠 패키지와 OSGi 번들 Jar 파일이 의 하위 패키지로 임베드되는지 확인하십시오. `all` 컨테이너 컨텐츠 패키지.

   예를 들어 복잡한 배포 콘텐츠 패키지 구조는 다음과 같을 수 있습니다.

   + `all` 콘텐츠 패키지는 단일 배포 아티팩트를 만들기 위해 다음 패키지를 임베드합니다
      + `common.ui.apps` 에 필요한 코드 배포 **모두** 사이트 A 및 사이트 B
      + `site-a.core` 사이트 A에 필요한 OSGi 번들 Jar
      + `site-a.ui.apps` 사이트 A에 필요한 코드 배포
      + `site-a.ui.config` 사이트 A에 필요한 OSGi 구성 배포
      + `site-a.ui.content` 사이트 A에 필요한 콘텐츠 및 구성 배포
      + `site-b.core` 사이트 B에 필요한 OSGi 번들 Jar
      + `site-b.ui.apps` 사이트 B에 필요한 코드 배포
      + `site-b.ui.config` 사이트 B에 필요한 OSGi 구성 배포
      + `site-b.ui.content` 사이트 B에 필요한 콘텐츠 및 구성 배포

+ 다음 `ui.config` 패키지에 모두 포함 [OSGi 구성](/help/implementing/deploying/configuring-osgi.md):
   + 코드로 간주되며 OSGi 번들에 속하지만 일반 콘텐츠 노드는 포함되지 않습니다. 따라서 컨테이너 패키지로 표시됩니다
   + 실행 모드별 OSGi 구성 정의가 포함된 조직 폴더
      + `/apps/my-app/osgiconfig`
   + 모든 대상 AEM as a Cloud Service 배포 대상에 적용되는 기본 OSGi 구성이 포함된 일반 OSGi 구성 폴더
      + `/apps/my-app/osgiconfig/config`
   + 모든 대상 AEM as a Cloud Service 배포 대상에 적용되는 기본 OSGi 구성을 포함하는 모드별 OSGi 구성 폴더를 실행합니다.
      + `/apps/my-app/osgiconfig/config.<author|publish>.<dev|stage|prod>`
   + 저장소 초기화 OSGi 구성 스크립트
      + [초기 보고서](#repo-init) 는 논리적으로 AEM 애플리케이션의 일부인 콘텐츠를 배포(변경 가능)하는 데 권장되는 방법입니다. 저장소 초기 OSGi 구성은 적절한 위치에 있어야 합니다. `config.<runmode>` 위에 요약된 폴더이며 다음을 정의하는 데 사용됩니다.
         + 기준선 콘텐츠 구조
         + 사용자
         + 서비스 사용자
         + 그룹
         + ACL(권한)

### 추가 응용 프로그램 패키지{#extra-application-packages}

자체 코드 및 컨텐츠 패키지로 구성된 다른 AEM 프로젝트를 AEM 배포에서 사용하는 경우 해당 컨테이너 패키지는 프로젝트의 `all` 패키지.

예를 들어, 2개의 공급업체 AEM 애플리케이션을 포함하는 AEM 프로젝트는 다음과 같을 수 있습니다.

+ `all` 콘텐츠 패키지는 단일 배포 아티팩트를 만들기 위해 다음 패키지를 임베드합니다
   + `core` AEM 애플리케이션에 필요한 OSGi 번들 Jar
   + `ui.apps` AEM 애플리케이션에 필요한 코드 배포
   + `ui.config` AEM 애플리케이션에 필요한 OSGi 구성 배포
   + `ui.content` AEM 애플리케이션에 필요한 콘텐츠 및 구성 배포
   + `vendor-x.all` 공급업체 X 애플리케이션에 필요한 모든 것(코드 및 컨텐츠) 배포
   + `vendor-y.all` 공급업체 Y 애플리케이션에 필요한 모든 것(코드 및 컨텐츠) 배포

## 패키지 유형 {#package-types}

패키지는 선언된 패키지 유형으로 표시됩니다. 패키지 유형은 패키지의 목적 및 배포를 명확하게 하는 데 도움이 됩니다.

+ 컨테이너 패키지는 다음을 설정해야 합니다. `packageType` 끝 `container`. 컨테이너 패키지에는 일반 노드가 없어야 합니다. OSGi 번들, 구성 및 하위 패키지만 허용됩니다. AEM as a Cloud Service 컨테이너는 사용할 수 없습니다. [후크 설치](https://jackrabbit.apache.org/filevault/installhooks.html).
+ 코드(변경할 수 없음) 패키지는 `packageType` 끝 `application`.
+ 콘텐츠(변경 가능) 패키지는 `packageType` 끝 `content`.


자세한 내용은 [Apache Jackrabbit FileVault - Package Maven Plugin 설명서](https://jackrabbit.apache.org/filevault-package-maven-plugin/package-mojo.html#packageType), [Apache Jackrabbit 패키지 유형](https://jackrabbit.apache.org/filevault/packagetypes.html)및 [FileVault Maven 구성 코드 조각](#marking-packages-for-deployment-by-adoube-cloud-manager) 아래요.

>[!TIP]
>
>다음을 참조하십시오. [POM XML 조각](#xml-package-types) 전체 스니펫을 보려면 아래 섹션을 참조하십시오.

## Adobe Cloud Manager에서 배포할 패키지 표시 {#marking-packages-for-deployment-by-adoube-cloud-manager}

By default, Adobe Cloud Manager harvests all packages produced by the Maven build, however since the container (`all`) package is the singular deployment artifact that contains all code and content packages, we must ensure **only** the  container (`all`) package is deployed. To ensure this, other Packages the Maven build generates must be marked with the FileVault Content Package Maven Plug-In configuration of `<properties><cloudManagerTarget>none</cloudManageTarget></properties>`.

>[!TIP]
>
>다음을 참조하십시오. [POM XML 조각](#pom-xml-snippets) 전체 스니펫을 보려면 아래 섹션을 참조하십시오.

## 초기 보고서{#repo-init}

Repo Init는 폴더 트리와 같은 일반적인 노드 구조에서 사용자, 서비스 사용자, 그룹 및 ACL 정의에 이르기까지 JCR 구조를 정의하는 지침 또는 스크립트를 제공합니다.

Repo Init의 주요 이점은 스크립트로 정의된 모든 작업을 수행할 수 있는 암시적 권한이 있고 배포 수명 주기 초기에 호출되어 코드가 실행될 때까지 모든 필수 JCR 구조가 존재한다는 것입니다.

Repo Init 스크립트 자체는 `ui.config` 프로젝트 를 스크립트로, 다음과 같은 변경 가능한 구조를 정의하는 데 사용할 수 있으며 사용해야 합니다.

+ 기준선 콘텐츠 구조
+ 서비스 사용자
+ 사용자
+ 그룹
+ ACL

저장소 초기화 스크립트는 다음과 같이 저장됩니다. `scripts` 다음의 항목 `RepositoryInitializer` OSGi 팩토리 구성이므로 실행 모드에 의해 암시적으로 타깃팅될 수 있으므로 AEM 작성자와 AEM Publish 서비스의 Repo Init 스크립트 간 또는 환경(개발, 스테이지 및 프로덕션) 간의 차이점을 허용할 수 있습니다.

저장소 초기 OSGi 구성은 다음에서 가장 잘 작성됩니다. [`.config` OSGi 구성 형식](https://sling.apache.org/documentation/bundles/configuration-installer-factory.html#configuration-files-config-1) 여러 줄을 지원하므로 를 사용하는 우수 사례에 대해 예외입니다 [`.cfg.json` OSGi 구성을 정의하려면](https://sling.apache.org/documentation/bundles/configuration-installer-factory.html#configuration-files-cfgjson-1).

사용자 및 그룹을 정의할 때 그룹만 응용 프로그램의 일부로 간주되며 여기에 해당 기능에 대한 필수 요소를 정의해야 합니다. 조직 사용자 및 그룹은 AEM의 런타임 시 계속 정의해야 합니다. 예를 들어, 사용자 정의 워크플로가 이름이 지정된 그룹에 작업을 할당하는 경우 해당 그룹은 AEM 애플리케이션에서 Repo Init를 통해 정의해야 하지만, 그룹화가 &quot;Wendy&#39;s Team&quot; 및 &quot;Sean&#39;s Team&quot;과 같은 단순한 조직인 경우 AEM에서 런타임 시 가장 잘 정의되고 관리되어야 합니다.

>[!TIP]
>
>저장소 초기화 스크립트 *필수* 인라인으로 정의되어야 합니다. `scripts` 필드 및 `references` 구성이 작동하지 않습니다.

Repo Init 스크립트에 대한 전체 어휘는 [Apache Sling 보고서 초기화 설명서](https://sling.apache.org/documentation/bundles/repository-initialization.html#the-repoinit-repository-initialization-language).

>[!TIP]
>
>다음을 참조하십시오. [저장소 초기 코드 조각](#snippet-repo-init) 전체 스니펫을 보려면 아래 섹션을 참조하십시오.

## 저장소 구조 패키지 {#repository-structure-package}

코드 패키지를 참조하려면 FileVault Maven 플러그인의 구성을 구성해야 합니다. `<repositoryStructurePackage>` 이를 통해 구조적 종속성을 수정할 수 있습니다(한 코드 패키지가 다른 코드 패키지에 설치되지 않도록 함). 다음을 수행할 수 있습니다. [프로젝트에 대한 고유한 저장소 구조 패키지 만들기](repository-structure-package.md).

This is **only required** for Code packages, meaning any Package marked with `<packageType>application</packageType>`.

애플리케이션에 대한 저장소 구조 패키지를 만드는 방법에 대해 알아보려면 다음을 참조하십시오. [저장소 구조 패키지 개발](repository-structure-package.md).

콘텐츠 패키지(`<packageType>content</packageType>`) **금지** 이 저장소 구조 패키지가 필요합니다.

>[!TIP]
>
>다음을 참조하십시오. [POM XML 조각](#xml-repository-structure-package) 전체 스니펫을 보려면 아래 섹션을 참조하십시오.

## 컨테이너 패키지에 하위 패키지 임베드{#embeddeds}

AEM AEM 컨텐츠 또는 코드 패키지는 특별한 &quot;side-car&quot; 폴더에 배치되며 FileVault Maven 플러그인의 `<embeddeds>` 구성. 다음 사항에 주의하십시오. `<subPackages>` 구성을 사용하면 안 됩니다.

일반적인 사용 사례는 다음과 같습니다.

+ AEM 작성자 사용자와 AEM 게시 사용자 간에 다른 ACL/권한
+ AEM 작성자에서만 활동을 지원하는 데 사용되는 구성
+ 백오피스 시스템과의 통합과 같은 코드는 AEM 작성자에서만 실행해야 합니다.

![패키지 포함](assets/embeddeds.png)

AEM 작성자, AEM 게시 또는 둘 다를 타깃팅하기 위해 패키지는 `all` 다음 형식의 특수 폴더 위치에 있는 컨테이너 패키지:

`/apps/<app-name>-packages/(content|application|container)/install(.author|.publish)?`

이 폴더 구조 분류:

+ 첫 번째 수준 폴더 **은(는) 다음과 같아야 합니다.** `/apps`.
+ 두 번째 수준 폴더는 `-packages` 폴더 이름에 대한 사후 수정되었습니다. 모든 하위 패키지가 임베드되는 두 번째 수준 폴더는 하나만 있는 경우가 많지만 두 번째 수준 폴더를 여러 개 만들어 애플리케이션의 논리 구조를 가장 잘 나타낼 수 있습니다.
   + `/apps/my-app-packages`
   + `/apps/my-other-app-packages`
   + `/apps/vendor-packages`

   >[!WARNING]
   >
   >By convention, sub-package embedded folders are named with the suffix of `-packages`. This ensures that the deployment code and content packages are **not** deployed the target folder(s) of any sub-package `/apps/<app-name>/...`  which results in destructive and cyclic installation behavior.

+ 세 번째 수준 폴더는 다음 중 하나여야 합니다
   `application`, `content` 또는 `container`
   + 다음 `application` 폴더에 코드 패키지가 있음
   + 다음 `content` 폴더에 컨텐츠 패키지가 보관됨
   + 다음 `container` 폴더에 모든 저장 [추가 애플리케이션 패키지](#extra-application-packages) AEM 애플리케이션에 포함될 수 있습니다.
이 폴더 이름은 [패키지 유형](#package-types) 포함된 패키지 중
+ The 4th-level folder contains the sub-packages, and must be one of:
   + `install` to install on **both** AEM author and AEM publish
   + `install.author` to **only** install on AEM author
   + `install.publish` 끝 **전용** AEM 게시에서 설치 참고 `install.author` 및 `install.publish` 는 지원되는 타겟입니다. Other run modes **are not** supported.

예를 들어 AEM 작성자 및 게시 특정 패키지를 포함하는 배포는 다음과 같을 수 있습니다.

+ `all` 컨테이너 패키지는 단일 배포 아티팩트를 만들기 위해 다음 패키지를 임베드합니다
   + `ui.apps` 임베드됨 `/apps/my-app-packages/application/install` AEM 작성자 및 AEM 게시 모두에 코드 배포
   + `ui.apps.author` 임베드됨 `/apps/my-app-packages/application/install.author` AEM 작성자에게만 코드 배포
   + `ui.content` 임베드됨 `/apps/my-app-packages/content/install` AEM 작성자 및 AEM 게시 모두에 콘텐츠 및 구성 배포
   + `ui.content.publish` 임베드됨 `/apps/my-app-packages/content/install.publish` AEM 게시에만 콘텐츠 및 구성 배포

>[!TIP]
>
>다음을 참조하십시오. [POM XML 조각](#xml-embeddeds) 전체 스니펫을 보려면 아래 섹션을 참조하십시오.

### 컨테이너 패키지의 필터 정의 {#container-package-filter-definition}

컨테이너 패키지에 코드 및 컨텐츠 하위 패키지가 포함되어 있으므로 포함된 대상 경로를 컨테이너 프로젝트의 `filter.xml` 빌드할 때 임베드된 패키지가 컨테이너 패키지에 포함되도록 할 수 있습니다.

간단히 추가 `<filter root="/apps/<my-app>-packages"/>` 배포할 하위 패키지가 포함된 모든 두 번째 수준 폴더의 항목입니다.

>[!TIP]
>
>다음을 참조하십시오. [POM XML 조각](#xml-container-package-filters) 전체 스니펫을 보려면 아래 섹션을 참조하십시오.

## 서드파티 패키지 포함 {#embedding-3rd-party-packages}

모든 패키지는 다음을 통해 사용할 수 있어야 합니다. [Adobe의 공개 Maven 아티팩트 저장소](https://repo1.maven.org/maven2/com/adobe/) 또는 액세스 가능한 공개, 참조 가능한 타사 Maven 아티팩트 리포지토리입니다.

If the 3rd party packages are in **Adobe&#39;s public Maven artifact repository**, no further configuration is needed for Adobe Cloud Manager to resolve the artifacts.

If the 3rd party packages are in a **public 3rd party Maven artifact repository**, this repository must be registered in the project&#39;s `pom.xml` and embedded following the method [outlined above](#embeddeds).

서드파티 애플리케이션/커넥터는 를 사용하여 임베드해야 합니다. `all` 프로젝트 컨테이너의 컨테이너로 패키지(`all`) 패키지.

Maven 종속성 추가는 표준 Maven 사례를 따르며 타사 아티팩트(코드 및 콘텐츠 패키지) 포함은 다음과 같습니다 [윤곽선 표시](#embedding-3rd-party-packages).

>[!TIP]
>
>다음을 참조하십시오. [POM XML 조각](#xml-3rd-party-maven-repositories) 전체 스니펫을 보려면 아래 섹션을 참조하십시오.

## 간의 패키지 종속성 `ui.apps` 출처: `ui.content` 패키지 {#package-dependencies}

패키지를 제대로 설치하려면 패키지 간 종속성을 설정하는 것이 좋습니다.

일반 규칙은 변경 가능한 콘텐츠(`ui.content`)는 변경할 수 없는 코드( )에 따라 다릅니다.`ui.apps`) 변경 가능한 콘텐츠의 렌더링 및 사용을 지원합니다.

이 일반 규칙에서 주목할 만한 예외는 변경할 수 없는 코드 패키지(`ui.apps` 또는 기타), __전용__ osgI 번들을 포함합니다. 이 경우 어떤 AEM 패키지도 종속성을 선언해서는 안 됩니다. 이것은 변경할 수 없는 코드 패키지이기 때문입니다 __전용__ 포함된 OSGi 번들이 AEM에 등록되지 않음 [패키지 관리자,](/help/implementing/developing/tools/package-manager.md) 따라서 종속된 모든 AEM 패키지는 충족되지 않은 종속성을 가지므로 설치하지 못합니다.

>[!TIP]
>
>다음을 참조하십시오. [POM XML 조각](#xml-package-dependencies) 전체 스니펫을 보려면 아래 섹션을 참조하십시오.

콘텐츠 패키지 종속성에 대한 일반적인 패턴은 다음과 같습니다.

### 간단한 배포 패키지 종속성 {#simple-deployment-package-dependencies}

간단한 대/소문자는 `ui.content` 에 따라 콘텐츠 패키지를 변경할 수 있음 `ui.apps` 변경할 수 없는 코드 패키지.

+ `all` 에 종속성 없음
   + `ui.apps` 에 종속성 없음
   + `ui.content` 다음에 종속: `ui.apps`

### 복잡한 배포 패키지 종속성 {#complex-deploxment-package-dependencies}

복잡한 배포는 간단한 사례에서 확장되며, 변경 가능한 해당 콘텐츠와 변경 불가능한 코드 패키지 간에 종속성을 설정합니다. 필요에 따라 변경할 수 없는 코드 패키지 간에도 종속성을 설정할 수 있습니다.

+ `all` 에 종속성 없음
   + `common.ui.apps.common` 에 종속성 없음
   + `site-a.ui.apps` 다음에 종속: `common.ui.apps`
   + `site-a.ui.content` 다음에 종속: `site-a.ui.apps`
   + `site-b.ui.apps` 다음에 종속: `common.ui.apps`
   + `site-b.ui.content` 다음에 종속: `site-b.ui.apps`

## 로컬 개발 및 배포 {#local-development-and-deployment}

이 문서에 설명된 프로젝트 구조 및 조직은 다음과 같습니다 **완전하게 호환되** 로컬 개발 AEM 인스턴스.

## POM XML 조각 {#pom-xml-snippets}

다음은 Maven입니다 `pom.xml` 위의 권장 사항에 맞게 Maven 프로젝트에 추가할 수 있는 구성 조각.

### 패키지 유형 {#xml-package-types}

Code and content packages, which are deployed as sub-packages, must declare a package type of **application** or **content**, depending on what they contain.

#### 컨테이너 패키지 유형 {#container-package-types}

컨테이너 `all/pom.xml` 프로젝트 **다음이 아님** 선언하기 `<packageType>`.

#### 코드(변경할 수 없음) 패키지 유형 {#immutable-package-types}

코드 패키지는 다음을 설정해야 합니다 `packageType` 끝 `application`.

다음에서 `ui.apps/pom.xml`, `<packageType>application</packageType>` 의 구성 지시문 작성 `filevault-package-maven-plugin` plugin 선언은 패키지 유형을 선언합니다.

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

#### 콘텐츠(변경 가능) 패키지 유형 {#mutable-package-types}

컨텐츠 패키지는 다음을 설정해야 합니다. `packageType` 끝 `content`.

다음에서 `ui.content/pom.xml`, `<packageType>content</packageType>` 의 구성 지시문 작성 `filevault-package-maven-plugin` plugin 선언은 패키지 유형을 선언합니다.

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

### Adobe Cloud Manager 배포를 위한 패키지 표시 {#cloud-manager-target}

In every project generating a Package, **except** for the container (`all`) project, add `<cloudManagerTarget>none</cloudManagerTarget>` to the `<properties>` configuration of the `filevault-package-maven-plugin` plug-in declaration to ensure they **are not** deployed by Adobe Cloud Manager. 컨테이너(`all`) 패키지는 필요한 모든 코드 및 컨텐츠 패키지를 임베드하는 Cloud Manager를 통해 배포된 단일 패키지여야 합니다.

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

### 초기 보고서{#snippet-repo-init}

Repo Init 스크립트가 포함된 Repo Init 스크립트는 `RepositoryInitializer` 를 통한 OSGi 공장 구성 `scripts` 속성. 이러한 스크립트는 OSGi 구성 내에서 정의되므로 일반적인 방법을 사용하여 실행 모드에 따라 쉽게 범위가 지정될 수 있습니다 `../config.<runmode>` 폴더 의미 체계.

스크립트는 일반적으로 여러 줄 선언이므로 `.config` JSON 기반 이외의 파일 `.cfg.json` 포맷.

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

다음 `scripts` OSGi 속성에는 [Apache Sling의 보고서 초기화 언어](https://sling.apache.org/documentation/bundles/repository-initialization.html#the-repoinit-repository-initialization-language).

### 저장소 구조 패키지 {#xml-repository-structure-package}

다음에서 `ui.apps/pom.xml` 및 기타 `pom.xml` 코드 패키지를 선언합니다(`<packageType>application</packageType>`)에서 FileVault Maven 플러그인에 다음 저장소 구조 패키지 구성을 추가합니다. 다음을 수행할 수 있습니다. [프로젝트에 대한 고유한 저장소 구조 패키지 만들기](repository-structure-package.md).

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

### 컨테이너 패키지에 하위 패키지 임베드 {#xml-embeddeds}

다음에서 `all/pom.xml`를 클릭하고 다음을 추가합니다 `<embeddeds>` 에 대한 지시문 `filevault-package-maven-plugin` plugin 선언. 기억해, **금지** 사용 `<subPackages>` 다음과 같은 구성의 하위 패키지가 포함됨 `/etc/packages` 보다 `/apps/my-app-packages/<application|content|container>/install(.author|.publish)?`.

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

In the `all` project&#39;s `filter.xml` (`all/src/main/content/jcr_root/META-INF/vault/definition/filter.xml`), **include** any `-packages` folders that contain sub-packages to deploy:

```xml
<filter root="/apps/my-app-packages"/>
```

여러 개인 경우 `/apps/*-packages` 임베드된 타겟에서 사용된 경우 여기에서 모두 열거되어야 합니다.

### 타사 Maven 저장소 {#xml-3rd-party-maven-repositories}

>[!WARNING]
>
>추가적인 Maven 저장소에 종속성이 있는지 확인되므로 Maven 저장소를 추가하면 Maven 빌드 시간이 연장될 수 있습니다.

원자로 프로젝트에서 `pom.xml`필요한 타사 공개 Maven 저장소 지시문을 추가합니다. 전체 `<repository>` 구성은 서드파티 저장소 공급자에서 사용할 수 있어야 합니다.

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

### 간의 패키지 종속성 `ui.apps` 출처: `ui.content` 패키지 {#xml-package-dependencies}

다음에서 `ui.content/pom.xml`를 클릭하고 다음을 추가합니다 `<dependencies>` 에 대한 지시문 `filevault-package-maven-plugin` plugin 선언.

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

다음에서 `all/pom.xml` 추가 `maven-clean-plugin` Maven 빌드 전에 대상 디렉터리를 정리하는 플러그인입니다.

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

+ [Maven을 사용한 패키지 관리](/help/implementing/developing/tools/maven-plugin.md)
+ [FileVault Content Package Maven 플러그인](https://jackrabbit.apache.org/filevault-package-maven-plugin/)
