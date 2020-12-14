---
title: Eclipse용 AEM 개발자 도구
description: Eclipse용 AEM 개발자 도구
translation-type: tm+mt
source-git-commit: c40d668cb6dcf5c3e2d09504b547457306a99c85
workflow-type: tm+mt
source-wordcount: '1182'
ht-degree: 2%

---


# Eclipse용 AEM 개발자 도구{#aem-developer-tools-for-eclipse}

![](assets/eclipse-logo.png)

## 개요 {#overview}

AEM Developer Tools for Eclipse는 Apache License 2 아래에 릴리스된 Apache Sling](https://sling.apache.org/documentation/development/ide-tooling.html)용 [Eclipse 플러그인을 기반으로 하는 Eclipse 플러그인입니다.

AEM 개발을 쉽게 하는 여러 기능을 제공합니다.

* Eclipse Server Connector를 통해 AEM 인스턴스와 매끄럽게 통합
* 컨텐츠 및 OSGi 번들 모두에 대한 동기화
* 코드 핫 스와핑 기능을 사용한 디버깅 지원
* 특정 프로젝트 제작 마법사를 통한 간단한 AEM 프로젝트 부트스트랩
* 간편한 JCR 속성 편집

## 요구 사항 {#requirements}

AEM 개발자 도구를 사용하기 전에 다음을 수행해야 합니다.

* 기업 Java 개발자용 [Eclipse IDE](https://www.eclipse.org/downloads/packages/)를 다운로드하여 설치합니다.
* [Eclipse FAQ](https://wiki.eclipse.org/FAQ_How_do_I_increase_the_heap_size_available_to_Eclipse)에 설명된 대로 `eclipse.ini` 구성 파일을 편집하여 Eclipse 설치를 최소 1GB의 더미 메모리가 있는지 확인합니다.

>[!NOTE]
>
>macOS의 경우 **Eclipse.app**&#x200B;을 마우스 오른쪽 단추로 클릭한 다음 **패키지 내용 표시**&#x200B;를 선택하여 `eclipse.ini`**.**

## Eclipse용 AEM 개발자 도구 설치 방법 {#how-to-install-the-aem-developer-tools-for-eclipse}

위의 [요구 사항](#requirements)을 충족하면 다음과 같이 플러그인을 설치할 수 있습니다.

1. [AEM 개발자 도구 웹 사이트를 엽니다.](https://eclipse.adobe.com/aem/dev-tools/)

1. **설치 링크**&#x200B;를 복사합니다.

   또는 설치 링크를 사용하는 대신 아카이브를 다운로드할 수 있습니다. 이렇게 하면 오프라인 설치가 가능하지만 이 방법으로 자동 업데이트 알림이 누락됩니다.

1. Eclipse에서 **도움말** 메뉴를 엽니다.
1. **새 소프트웨어 설치**&#x200B;를 클릭합니다.
1. **추가...를 클릭합니다.**.
1. **이름**&#x200B;에 `AEM Developer Tools`를 입력합니다.
1. **위치**&#x200B;에서 설치 URL을 복사합니다.
1. **추가**&#x200B;를 클릭합니다.
1. **AEM** 및 **Sling** 플러그인을 모두 선택합니다.
1. **다음**&#x200B;을 클릭합니다.
1. **설치 세부 사항** 창에서 **다음**&#x200B;을 다시 클릭합니다.
1. 라이센스 계약에 동의하고 **마침**&#x200B;을 클릭합니다.
1. Eclipse를 다시 시작하려면 **RestartNow**&#x200B;를 클릭합니다.

## AEM 원근 {#the-aem-perspective}

Eclipse a Perspective에서는 윈도우 내에서 사용할 수 있는 작업 및 보기를 결정하고 Eclipse의 리소스와 작업 지향 상호 작용을 활성화합니다. 원근법에 대한 자세한 내용은 [Eclipse 설명서를 참조하십시오.](https://help.eclipse.org)

AEM Development Tools for Eclipse는 AEM 프로젝트 및 인스턴스를 완벽하게 제어할 수 있는 AEM Perspective를 제공합니다. AEM 원근을 열려면 다음을 수행합니다.

1. Eclipse 메뉴 모음에서 **Window** -> **Perspective** -> **원근 열기** -> **기타**&#x200B;을 선택합니다.
1. 대화 상자에서 **AEM**&#x200B;을 선택하고 **열기**&#x200B;를 클릭합니다.

![Eclipse의 AEM 관점](assets/eclipse-aem-perspective.png)

## 샘플 다중 모듈 프로젝트 {#sample-multi-module-project}

AEM Developer Tools for Eclipse는 Eclipse에서 프로젝트 설정을 신속하게 시작할 수 있을 뿐만 아니라 여러 AEM 기능에 대한 모범 사례 가이드 역할을 하는 다양한 모듈 방식의 샘플 프로젝트를 제공합니다. [프로젝트 원형에 대한 자세한 내용을 살펴보십시오](https://github.com/Adobe-Marketing-Cloud/aem-project-archetype).

다음 단계에 따라 샘플 프로젝트를 만듭니다.

1. **파일** > **새로 만들기** > **프로젝트** 메뉴에서 **AEM** 섹션으로 이동하여 **AEM 샘플 다중 모듈 프로젝트**&#x200B;를 선택합니다.

   ![AEM 샘플 다중 모듈 프로젝트](assets/aem-sample-project.png)

1. **다음**&#x200B;을 클릭합니다.

   >[!NOTE]
   >
   >m2eclipse가 원형 카탈로그를 스캔해야 하기 때문에 이 단계는 잠시 걸릴 수 있습니다.

1. 메뉴에서 `com.adobe.granite.archetypes : sample-project-archetype : <highest-number>`을 선택한 다음 **다음**&#x200B;을 클릭합니다.

   ![원형 버전 선택](assets/select-archetype.png)

1. 샘플 프로젝트에 대해 다음 필드를 제공합니다.

   * **이름**
   * **그룹 ID**
   * **아티팩트 ID**
   * **appId**  - 이 값을 설정하려면 고급  **** 옵션을 확장해야 할 수 있습니다.
   * **appTitle**  - 이 값을 설정하려면 고급  **** 옵션을 확장해야 할 수 있습니다.
   * **패키지**  - 이 값을 설정하려면 고급  **** 옵션을 확장해야 합니다.

   ![원형 속성 정의](assets/archetype-properties.png)

1. **다음**&#x200B;을 클릭합니다.

1. 그런 다음 Eclipse가 연결할 AEM 서버를 구성합니다.

   디버거 기능을 사용하려면 디버그 모드에서 AEM을 시작해야 합니다. 이 단계는 명령줄에 다음을 추가하여 수행할 수 있습니다.

   ```text
       -nofork -agentlib:jdwp=transport=dt_socket,server=y,suspend=n,address=10123
   ```

   ![AEM 서버에 연결](assets/connect-server.png)

1. **완료**&#x200B;를 클릭합니다. 프로젝트 구조가 만들어집니다.

   >[!NOTE]
   >
   >새로 설치하는 경우(특히, 다중 종속 항목을 다운로드하지 않은 경우) 오류가 있는 프로젝트를 만들 수 있습니다. 이 경우 [잘못된 프로젝트 정의 확인](#resolving-invalid-project-definition)에 설명된 절차를 따르십시오.

## 기존 프로젝트 {#how-to-import-existing-projects} 가져오기 방법

**새 프로젝트** 기능을 사용하여 올바른 구조를 만들 수 있습니다.

1. 지침에 따라 [샘플 다중 모듈 프로젝트](#sample-multi-module-project)를 만들면 다음 프로젝트를 만들어 문제 분리를 올바르게 수행할 수 있습니다.

   * `PROJECT.ui.apps` ( `/apps` 및  `/etc` 컨텐츠)
   * `PROJECT.ui.content` 에  `/content` 대해
   * `PROJECT.core` Java 번들(Java 코드를 추가하는 즉시 이러한 번들 포함)
   * `PROJECT.it.launcher` 통합 테스트 `PROJECT.it.tests` 에 대해

1. `PROJECT.ui.apps` 프로젝트의 컨텐츠를 패키지의 `apps` 및 `etc` 폴더로 바꿉니다.

   1. 프로젝트 탐색기 패널에서 `PROJECT.ui.apps` > `src` > `main` > `content` > `jcr_root` > `apps`를 펼칩니다.
   1. `apps` 폴더를 마우스 오른쪽 단추로 클릭하고 **다음 위치에 표시** > **시스템 탐색기**&#x200B;를 선택합니다.
   1. 콘텐트 패키지의 `apps` 및 `etc` 폴더를 삭제하고 `apps` 및 `etc` 폴더에 배치합니다.
   1. Eclipse에서 `PROJECT.ui.apps` 프로젝트를 마우스 오른쪽 버튼으로 클릭하고 **새로 고침**&#x200B;을 선택합니다.

1. 그런 다음 `PROJECT.ui.content`에도 동일하게 수행하고 해당 콘텐트 폴더를 패키지 중 하나로 바꿉니다.

   1. 프로젝트 탐색기 패널에서 `PROJECT.ui.content` > `src` > `main` > `content` > `jcr_root` > `content`를 펼칩니다.
   1. 더 깊은 콘텐트 폴더를 마우스 오른쪽 단추로 클릭하고 **다음 위치에 표시** -> **시스템 탐색기**&#x200B;를 선택합니다.
   1. 이제 볼 콘텐트 폴더를 삭제하고 콘텐트 패키지의 콘텐트 폴더를 여기에 배치합니다.
   1. Eclipse에서 `PROJECT.ui.content` 프로젝트를 마우스 오른쪽 버튼으로 클릭하고 **새로 고침**&#x200B;을 선택합니다.

1. 이제 이 두 프로젝트의 `filter.xml` 파일을 업데이트하여 콘텐츠 패키지의 컨텐츠와 일치시켜야 합니다. 이렇게 하려면 별도의 텍스트/코드 편집기에서 컨텐츠 패키지의 `META-INF/vault/filter.xml` 파일을 엽니다.

   * 다음은 `filter.xml` 파일이 어떻게 표시되는지 보여주는 예입니다.

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

1. 두 프로젝트로 분할된 패키지의 내용에 대해서는 이러한 필터 규칙을 두 개의 프로젝트로 분할하고 그에 따라 두 프로젝트의 `filter.xml` 파일을 업데이트해야 합니다.

   1. Eclipse에서 `PROJECT.ui.apps/src/main/content/META-INF/filter.xml`을(를) 엽니다.
   1. `<workspaceFilter>` 요소의 내용을 `/apps` 및 `/etc`로 시작하는 패키지의 규칙으로 바꿉니다.
      * 예:

         ```xml
         <?xml version="1.0" encoding="UTF-8"?>
         <workspaceFilter version="1.0">
            <filter root="/apps/foo"/>
            <filter root="/apps/foundation/components/bar"/>
            <filter root="/etc/designs/foo"/>
         </workspaceFilter>
         ```
   1. 그런 다음 `PROJECT.ui.content/src/main/content/META-INF/filter.xml`을(를) 엽니다.
   1. 규칙을 `/content`으로 시작하는 패키지의 규칙으로 바꿉니다.
      * 예:

         ```xml
         <?xml version="1.0" encoding="UTF-8"?>
         <workspaceFilter version="1.0">
            <filter root="/content/foo"/>
            <filter root="/content/dam/foo"/>
            <filter root="/content/usergenerated/content/foo"/>
         </workspaceFilter>
         ```


1. 모든 변경 내용을 저장해야 합니다. 이제 해당 새 컨텐츠를 AEM 인스턴스와 동기화할 수 있습니다.

1. [서버] 패널에서 연결이 시작되었는지, 시작하지 않았는지 확인합니다.
1. **정리 및 게시** 아이콘을 클릭합니다.

작업이 완료되면 패키지가 인스턴스에서 실행되고 저장되면 변경 내용이 자동으로 인스턴스에 동기화됩니다.

프로젝트에서 패키지를 다시 빌드하려면 `PROJECT.ui.apps` 또는 `PROJECT.ui.content`을 마우스 오른쪽 단추로 클릭하고 **Run As** -> **Maven Install**&#x200B;을 선택합니다.

이제 패키지가 포함된 대상 폴더(예:`PROJECT.ui.apps-0.0.1-SNAPSHOT.zip`).

## 문제 해결 {#troubleshooting}

### 잘못된 프로젝트 정의 {#resolving-invalid-project-definition} 해결

잘못된 종속성 및 프로젝트 정의를 해결하려면 다음과 같이 하십시오.

1. 생성된 프로젝트를 모두 선택합니다.
1. 마우스 오른쪽 버튼을 클릭합니다.
1. 컨텍스트 메뉴에서 **Maven** -> **프로젝트 업데이트**&#x200B;를 선택합니다.
1. **스냅샷/릴리스 업데이트 강제 적용**&#x200B;을 선택합니다.
1. **확인**&#x200B;을 클릭합니다.

Eclipse는 필요한 종속성을 다운로드합니다. 잠시 시간이 걸릴 수 있습니다.

## 추가 정보 {#more-information}

Eclipse 웹 사이트용 공식 Apache Sling IDE 툴은 다음과 같은 유용한 정보를 제공합니다.

* Eclipse용 [**Apache Sling IDE 도구** 사용 안내서](https://sling.apache.org/documentation/development/ide-tooling.html)에서 이 설명서는 AEM 개발 도구에서 지원하는 전체 개념, 서버 통합 및 배포 기능을 안내합니다.
* [문제 해결 섹션](https://sling.apache.org/documentation/development/ide-tooling.html#troubleshooting).
* [알려진 문제 목록](https://sling.apache.org/documentation/development/ide-tooling.html#known-issues).

다음 공식 [Eclipse](https://eclipse.org/) 설명서는 환경을 설정하는 데 도움이 될 수 있습니다.

* [Eclipse 시작하기](https://eclipse.org/users/)
* [Eclipse Luna Help System](https://help.eclipse.org/luna/index.jsp)
* [Maven 통합(m2eclipse)](https://www.eclipse.org/m2e/)
