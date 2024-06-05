---
title: Eclipse용 AEM 개발자 도구
description: Apache Sling용 Eclipse 플러그인을 기반으로 하는 Eclipse 플러그인인 AEM Developer Tools for Eclipse를 사용하는 방법에 대해 알아봅니다.
exl-id: 7f9c0f99-e230-440a-8bc9-a0ab7465e3bf
feature: Developing
role: Admin, Architect, Developer
source-git-commit: 646ca4f4a441bf1565558002dcd6f96d3e228563
workflow-type: tm+mt
source-wordcount: '1138'
ht-degree: 2%

---

# Eclipse용 AEM 개발자 도구{#aem-developer-tools-for-eclipse}

![Eclipse용 Experience Manager 개발자 도구 로고](assets/eclipse-logo.png)

## 개요 {#overview}

_Eclipse용 Experience Manager 개발자 도구_ 는 을 기반으로 하는 Eclipse 플러그인입니다. [Apache Sling용 Eclipse 플러그인](https://sling.apache.org/documentation/development/ide-tooling.html) apache 라이센스 2에 따라 릴리스되었습니다.

AEM 개발을 쉽게 만드는 몇 가지 기능을 제공합니다.

* Eclipse Server Connector를 통해 AEM 인스턴스와 원활하게 통합
* 콘텐츠 및 OSGi 번들 모두에 대한 동기화
* 코드 핫 스왑 기능으로 디버깅 지원
* 특정 프로젝트 만들기 마법사를 통한 AEM 프로젝트 단순 Bootstrap
* JCR 속성의 간편한 편집

## 요구 사항 {#requirements}

AEM 개발자 도구를 사용하기 전에 다음을 수행해야 합니다.

* 다운로드 및 설치 [Enterprise Java™ 개발자용 Eclipse IDE](https://www.eclipse.org/downloads/packages/).
* Eclipse 설치를 구성하여 를 편집하여 1GB 이상의 힙 메모리가 있는지 확인합니다. `eclipse.ini` 에 설명된 대로 구성 파일 [Eclipse FAQ](https://wiki.eclipse.org/FAQ_How_do_I_increase_the_heap_size_available_to_Eclipse).

>[!NOTE]
>
>macOS에서 마우스 오른쪽 단추를 클릭해야 합니다. **Eclipse.app**&#x200B;을 선택한 다음 을 선택합니다 **패키지 내용 표시** 를 찾으려면 `eclipse.ini`**.**

## Eclipse용 AEM 개발자 도구를 설치하는 방법 {#how-to-install-the-aem-developer-tools-for-eclipse}

다음을 완료했을 때 [요구 사항](#requirements) 위에서 다음과 같이 플러그인을 설치할 수 있습니다.

1. 를 엽니다. [AEM 개발자 도구 웹 사이트](https://eclipse.adobe.com/com.adobe.granite.ide.p2update-1.3.0.zip). <!-- RB: OLD URL was (https://eclipse.adobe.com/aem/dev-tools/) This URL is generating a 404 error in the experience-manager-cloud-service.en LinkCheckExl report . The website appears to be dead; no redirects at all. Clicking "Installation Link" does not do anything. Only the link "Download archive" works. The "Online Documentation" link just takes you to the AEM Docs home page. Not sure if this topic is still needed?? -->

1. 다음을 복사합니다. **설치 링크**.

   또는 설치 링크를 사용하는 대신 아카이브를 다운로드할 수 있습니다. 이 방법을 사용하면 오프라인 설치가 가능하지만 이러한 방식으로 자동 업데이트 알림 누락을 받지 않습니다.

1. Eclipse에서 **도움말** 메뉴 아래의 제품에서 사용할 수 있습니다.
1. 클릭 **새 소프트웨어 설치**.
1. 클릭 **추가...**.
1. 다음에서 **이름** 필드, 입력 `AEM Developer Tools`.
1. 다음에서 **위치** 필드에서 설치 URL을 복사합니다.
1. 클릭 **추가**.
1. 둘 다 확인 **AEM** 및 **슬링** plugins.
1. **다음**&#x200B;을 클릭합니다.
1. 다음에서 **설치 세부 정보** 창에서 다음을 클릭: **다음** 다시.
1. 사용권 계약에 동의하고 **완료**.
1. 클릭 **지금 다시 시작** Eclipse를 다시 시작합니다.

## AEM 관점 {#the-aem-perspective}

Eclipse에서 관점은 창 내에서 사용할 수 있는 작업 및 보기를 결정하고 Eclipse의 리소스와 작업 지향 상호 작용을 가능하게 합니다. 원근법에 대한 자세한 내용은 [Eclipse 문서.](https://help.eclipse.org/latest/index.jsp)

_Eclipse용 Experience Manager 개발 도구_ AEM 프로젝트 및 인스턴스를 완벽하게 제어할 수 있는 AEM Perspective를 제공합니다. AEM Perspective를 열려면

1. Eclipse 메뉴 모음에서 를 선택합니다. **창** > **원근감** > **원근감 열기** > **기타**.
1. 선택 **AEM** 대화 상자에서 다음을 클릭합니다. **열기**.

![Eclipse의 AEM 관점](assets/eclipse-aem-perspective.png)

## 샘플 다중 모듈 프로젝트 {#sample-multi-module-project}

다음 _Eclipse용 Experience Manager 개발자 도구_ 에는 Eclipse의 프로젝트 설정을 빠르게 시작하는 데 도움이 되는 샘플 다중 모듈 프로젝트가 함께 제공됩니다. 또한 여러 AEM 기능에 대한 모범 사례 안내서 역할을 합니다. [Project Archetype에 대해 자세히 알아보기](https://github.com/adobe/aem-project-archetype).

다음 단계에 따라 샘플 프로젝트를 만듭니다.

1. 다음에서 **파일** > **신규** > **프로젝트** 메뉴, 다음 위치로 이동 **AEM** 섹션 및 선택 **AEM 샘플 다중 모듈 프로젝트**.

   ![AEM 샘플 다중 모듈 프로젝트](assets/aem-sample-project.png)

1. **다음**&#x200B;을 클릭합니다.

   >[!NOTE]
   >
   >m2eclipse는 Archetype 카탈로그를 스캔해야 하므로 이 단계는 잠시 걸릴 수 있습니다.

1. 선택 `com.adobe.granite.archetypes : sample-project-archetype : <highest-number>` 메뉴에서 을(를) 클릭한 다음 **다음**.

   ![Archetype 버전 선택](assets/select-archetype.png)

1. 샘플 프로젝트에 대해 다음 필드를 제공합니다.

   * **이름**
   * **그룹 ID**
   * **아티팩트 Id**
   * **appId** - 를 확장해야 할 수 있습니다. **고급** 옵션을 사용하여 이 값을 설정합니다.
   * **appTitle** - 를 확장해야 할 수 있습니다. **고급** 옵션을 사용하여 이 값을 설정합니다.
   * **패키지** - 를 확장해야 할 수 있습니다. **고급** 옵션을 사용하여 이 값을 설정합니다.

   ![Archetype 속성 정의](assets/archetype-properties.png)

1. **다음**&#x200B;을 클릭합니다.

1. 그런 다음 Eclipse가 연결할 AEM 서버를 구성합니다.

   디버거 기능을 사용하려면 명령줄에 다음을 추가하여 수행할 수 있는 디버그 모드에서 AEM을 시작해야 합니다.

   ```text
       -nofork -agentlib:jdwp=transport=dt_socket,server=y,suspend=n,address=10123
   ```

   ![AEM 서버에 연결](assets/connect-server.png)

1. 클릭 **완료**. 프로젝트 구조가 생성됩니다.

   >[!NOTE]
   >
   >새로 설치 시(특히, Maven 종속성이 다운로드되지 않은 경우) 프로젝트가 오류와 함께 생성될 수 있습니다. 이 경우 다음에 설명된 절차를 따르십시오. [잘못된 프로젝트 정의 해결 중](#resolving-invalid-project-definition).

## 기존 프로젝트를 가져오는 방법 {#how-to-import-existing-projects}

다음을 사용할 수 있습니다. **새 프로젝트** 사용자에게 적합한 구조를 만드는 기능:

1. 지침에 따라 [샘플 다중 모듈 프로젝트](#sample-multi-module-project) 또한 다음과 같은 프로젝트를 통해 문제를 건강하게 분리할 수 있습니다.

   * `PROJECT.ui.apps` 대상 `/apps` 및 `/etc` 콘텐츠
   * `PROJECT.ui.content` 대상 `/content` 작성됨
   * `PROJECT.core` Java™ 번들의 경우(Java™ 코드를 추가하려는 경우 흥미로워집니다.)
   * `PROJECT.it.launcher` 및 `PROJECT.it.tests` 통합 테스트용

1. 의 콘텐츠 바꾸기 `PROJECT.ui.apps` 이 포함된 프로젝트 `apps` 및 `etc` 패키지의 폴더:

   1. 프로젝트 탐색기 패널에서 를 펼칩니다. `PROJECT.ui.apps` > `src` > `main` > `content` > `jcr_root` > `apps`.
   1. 마우스 오른쪽 단추 클릭 `apps` 폴더 및 선택 **표시 위치** > **시스템 탐색기**.
   1. 삭제 `apps` 및 `etc` 이제 보고 여기에 배치해야 하는 폴더 `apps` 및 `etc` 콘텐츠 패키지의 폴더입니다.
   1. Eclipse에서 `PROJECT.ui.apps` 프로젝트 및 선택 **새로 고침**.

1. 그런 다음 동일한 작업을 수행합니다 `PROJECT.ui.content` 콘텐츠 폴더를 다음 패키지 중 하나로 바꿉니다.

   1. 프로젝트 탐색기 패널에서 를 펼칩니다. `PROJECT.ui.content` > `src` > `main` > `content` > `jcr_root` > `content`.
   1. 더 깊은 콘텐츠 폴더를 마우스 오른쪽 단추로 클릭하고 **표시 위치** > **시스템 탐색기**.
   1. 이제 표시되어야 하는 콘텐츠 폴더를 삭제하고 콘텐츠 패키지의 콘텐츠 폴더를 여기에 배치합니다.
   1. Eclipse에서 `PROJECT.ui.content` 프로젝트 및 선택 **새로 고침**.

1. 이제 다음을 업데이트해야 합니다. `filter.xml` 콘텐츠 패키지의 콘텐츠에 해당하는 이 두 프로젝트의 파일입니다. 이를 위해 를 엽니다. `META-INF/vault/filter.xml` 별도의 텍스트/코드 편집기에 있는 콘텐츠 패키지의 파일입니다.

   * 다음은 을(를) 사용하는 방법의 예입니다 `filter.xml` 파일은 다음과 같이 표시될 수 있습니다.

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <workspaceFilter version="1.0">
       <filter root="/apps/foo"/>
       <filter root="/apps/foundation/components/bar"/>
       <filter root="/etc/designs/foo"/>
       <filter root="/content/foo"/>
       <filter root="/content/dam/foo"/>
       <filter root="/content/usergenerated/content/foo"/>
   </workspaceFilter>
   ```

1. 두 개의 프로젝트로 분할된 패키지의 콘텐츠도 이러한 필터 규칙을 두 개로 분할하고 적절하게 업데이트해야 합니다. `filter.xml` 두 프로젝트의 파일입니다.

   1. Eclipse에서 열기 `PROJECT.ui.apps/src/main/content/META-INF/filter.xml`.
   1. 의 콘텐츠 바꾸기 `<workspaceFilter>` 로 시작하는 패키지 규칙이 있는 요소 `/apps` 및 `/etc`
      * 예:

        ```xml
        <?xml version="1.0" encoding="UTF-8"?>
        <workspaceFilter version="1.0">
           <filter root="/apps/foo"/>
           <filter root="/apps/foundation/components/bar"/>
           <filter root="/etc/designs/foo"/>
        </workspaceFilter>
        ```

   1. 그런 다음 열기 `PROJECT.ui.content/src/main/content/META-INF/filter.xml`.
   1. 다음으로 시작하는 패키지로 규칙을 바꿉니다. `/content`.
      * 예:

        ```xml
        <?xml version="1.0" encoding="UTF-8"?>
        <workspaceFilter version="1.0">
           <filter root="/content/foo"/>
           <filter root="/content/dam/foo"/>
           <filter root="/content/usergenerated/content/foo"/>
        </workspaceFilter>
        ```

1. 모든 변경 사항을 저장해야 합니다. 이제 해당 새 콘텐츠를 AEM 인스턴스와 동기화할 수 있습니다.

1. 서버 패널에서 연결이 시작되었는지 확인하고 시작되지 않은 경우 시작합니다.
1. 다음을 클릭합니다. **정리 및 게시** 아이콘.

완료되면 인스턴스에서 패키지를 실행해야 하며 저장 시 모든 변경 사항이 인스턴스에 자동으로 동기화됩니다.

프로젝트에서 패키지를 다시 빌드하려면 를 마우스 오른쪽 단추로 클릭합니다. `PROJECT.ui.apps` 또는 `PROJECT.ui.content` 및 선택 **다음으로 실행** > **Maven 설치**.

이제 내부에 패키지를 사용하여 타겟 폴더를 만듭니다(예: `PROJECT.ui.apps-0.0.1-SNAPSHOT.zip`).

## 문제 해결 {#troubleshooting}

### 잘못된 프로젝트 정의 해결 중 {#resolving-invalid-project-definition}

잘못된 종속성 및 프로젝트 정의를 해결하려면 다음과 같이 진행합니다.

1. 생성된 모든 프로젝트를 선택합니다.
1. 마우스 오른쪽 버튼을 클릭합니다.
1. 컨텍스트 메뉴에서 을(를) 선택합니다 **Maven** > **프로젝트 업데이트**.
1. 확인 **스냅샷/릴리스 강제 업데이트**.
1. **확인**&#x200B;을 클릭합니다.

Eclipse는 필요한 종속성을 다운로드합니다. 잠시 기다려 주십시오.

## 추가 정보 {#more-information}

Eclipse용 공식 Apache Sling IDE 툴링 웹사이트는 다음과 같은 유용한 정보를 제공합니다.

* 다음 [**Eclipse용 Apache Sling IDE 도구** 사용 안내서](https://sling.apache.org/documentation/development/ide-tooling.html), 이 설명서는 AEM 개발 도구에서 지원하는 전체 개념, 서버 통합 및 배포 기능을 안내합니다.
* 다음 [문제 해결 섹션](https://sling.apache.org/documentation/development/ide-tooling.html#troubleshooting).
* 다음 [알려진 문제 목록](https://sling.apache.org/documentation/development/ide-tooling.html#known-issues).

다음의 관리 [Eclipse](https://www.eclipse.org/) 설명서는 환경을 설정하는 데 도움이 될 수 있습니다.

* [Eclipse 시작하기](https://eclipseide.org/getting-started/)
* [이클립스 루나 도움말](https://help.eclipse.org/latest/index.jsp)
* [Maven 통합(m2eclipse)](https://www.eclipse.org/m2e/)
