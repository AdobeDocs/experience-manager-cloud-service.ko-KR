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

AEM Developer Tools for Eclipse는 Apache License 2에서 릴리스된 Apache Sling용 [Eclipse 플러그인을](https://sling.apache.org/documentation/development/ide-tooling.html) 기반으로 하는 Eclipse 플러그인입니다.

AEM 개발을 쉽게 해주는 다양한 기능을 제공합니다.

* Eclipse Server Connector를 통해 AEM 인스턴스와의 완벽한 통합
* 컨텐츠 및 OSGi 번들 모두에 대한 동기화
* 코드 핫 스와핑 기능을 사용한 디버깅 지원
* 특정 프로젝트 제작 마법사를 통한 간단한 AEM 프로젝트 부트스트랩
* 간편한 JCR 속성 편집

## 요구 사항 {#requirements}

AEM 개발자 도구를 사용하기 전에 다음을 수행해야 합니다.

* 기업 Java 개발자용 [Eclipse IDE를 다운로드하여 설치합니다](https://www.eclipse.org/downloads/packages/).
* Eclipse FAQ에 설명된 대로 구성 파일을 편집하여 최소 1GB의 `eclipse.ini` heap 메모리를 갖도록 Eclipse 설치 [를 구성합니다](https://wiki.eclipse.org/FAQ_How_do_I_increase_the_heap_size_available_to_Eclipse).

>[!NOTE]
>
>macOS에서 Eclipse.app을 마우스 오른쪽 버튼으로 **클릭한** 다음 패키지 내용 **표시** 를 선택하여 `eclipse.ini`**찾아보십시오.**

## Eclipse용 AEM 개발자 도구 설치 방법 {#how-to-install-the-aem-developer-tools-for-eclipse}

위의 [요구](#requirements) 사항을 충족하면 다음과 같이 플러그인을 설치할 수 있습니다.

1. AEM [Developer Tools 웹 사이트를 엽니다.](https://eclipse.adobe.com/aem/dev-tools/)

1. 설치 **링크를 복사합니다**.

   설치 링크를 사용하는 대신 아카이브를 다운로드할 수도 있습니다. 오프라인 설치를 허용하지만 이 방법으로 자동 업데이트 알림을 받지 못할 것입니다.

1. Eclipse에서 **도움말** 메뉴를 엽니다.
1. 새 소프트웨어 **설치를 클릭합니다**.
1. Click **Add...**.
1. 이름 **에** 입력합니다 `AEM Developer Tools`.
1. 위치 **에서** 설치 URL을 복사합니다.
1. **추가**&#x200B;를 클릭합니다.
1. AEM **및 Sling** 플러그인을 모두 **** 확인합니다.
1. **다음**&#x200B;을 클릭합니다.
1. [ **설치 세부** 정보] 창에서 [ **다음]을 다시** 클릭합니다.
1. 사용권 계약에 동의하고 **마침을 클릭합니다**.
1. Eclipse **를** 다시 시작하려면 RestartNow를 클릭합니다.

## AEM 원근 {#the-aem-perspective}

Eclipse a Perspective는 창 내에서 사용할 수 있는 작업 및 뷰를 결정하며 Eclipse의 리소스와 작업 중심의 상호 작용을 활성화합니다. 원근법에 대한 자세한 내용은 [Eclipse 설명서를 참조하십시오.](https://help.eclipse.org)

AEM Development Tools for Eclipse는 AEM 프로젝트 및 인스턴스를 완벽하게 제어할 수 있는 AEM Perspective를 제공합니다. AEM 원근감을 열려면

1. Eclipse 메뉴 막대에서 **창** -> **원근** -> 원근 **열기** -> ****&#x200B;기타Twitter를 선택합니다.
1. 대화 상자에서 **AEM** 를 선택하고 [열기]를 **클릭합니다**.

![Eclipse의 AEM 관점](assets/eclipse-aem-perspective.png)

## 샘플 멀티 모듈 프로젝트 {#sample-multi-module-project}

AEM Developer Tools for Eclipse는 Eclipse에서 프로젝트 설정을 신속하게 시작할 수 있도록 돕는 샘플 멀티 모듈 프로젝트뿐만 아니라 여러 AEM 기능에 대한 모범 사례 가이드도 제공합니다. [프로젝트 원형에 대한 자세한 내용을 살펴보십시오](https://github.com/Adobe-Marketing-Cloud/aem-project-archetype).

다음 단계에 따라 샘플 프로젝트를 만듭니다.

1. [ **파일** ] > [새 **** ] > **프로젝트****] 메뉴에서** AEM 섹션을 탐색하고AEM 샘플 다중 모듈 프로젝트 ****&#x200B;를 선택합니다.

   ![AEM 샘플 멀티 모듈 프로젝트](assets/aem-sample-project.png)

1. **다음**&#x200B;을 클릭합니다.

   >[!NOTE]
   >
   >m2eclipse가 원형 카탈로그를 스캔해야 하기 때문에 이 단계는 다소 걸릴 수 있습니다.

1. 메뉴 `com.adobe.granite.archetypes : sample-project-archetype : <highest-number>` 에서 선택한 다음 **다음을 클릭합니다**.

   ![원형 버전 선택](assets/select-archetype.png)

1. 샘플 프로젝트에 대해 다음 필드를 제공하십시오.

   * **이름**
   * **그룹 ID**
   * **아티팩트 ID**
   * **appId** - 이 값을 설정하려면 **고급** 옵션을 확장해야 합니다.
   * **appTitle** - 이 값을 설정하려면 **고급** 옵션을 확장해야 합니다.
   * **패키지** - 이 값을 설정하려면 **고급** 옵션을 확장해야 합니다.

   ![원형 속성 정의](assets/archetype-properties.png)

1. **다음**&#x200B;을 클릭합니다.

1. 그런 다음 Eclipse가 연결할 AEM 서버를 구성합니다.

   디버거 기능을 사용하려면 디버그 모드에서 AEM을 시작해야 합니다. 이 경우 명령줄에 다음을 추가하여 수행할 수 있습니다.

   ```text
       -nofork -agentlib:jdwp=transport=dt_socket,server=y,suspend=n,address=10123
   ```

   ![AEM 서버에 연결](assets/connect-server.png)

1. 마침을 **클릭합니다**. 프로젝트 구조가 만들어집니다.

   >[!NOTE]
   >
   >새로 설치하는 경우(특히, 다중 종속 항목을 다운로드하지 않은 경우) 오류가 있는 프로젝트를 만들 수 있습니다. 이 경우 잘못된 프로젝트 정의 [해결에 설명된 절차를 따르십시오](#resolving-invalid-project-definition).

## 기존 프로젝트를 가져오는 방법 {#how-to-import-existing-projects}

새 프로젝트 **기능을 사용하여** 적합한 구조를 만들 수 있습니다.

1. 지침에 따라 [샘플 멀티 모듈 프로젝트를](#sample-multi-module-project) 만들면 다음과 같은 프로젝트를 만들어 문제를 자체적으로 해결할 수 있습니다.

   * `PROJECT.ui.apps` for `/apps` and `/etc` content
   * `PROJECT.ui.content` for `/content` that
   * `PROJECT.core` for Java bundles (these will be interest as when you want to add Java code)
   * `PROJECT.it.launcher` 및 통합 테스트 `PROJECT.it.tests` 에 대해

1. 프로젝트의 컨텐츠를 `PROJECT.ui.apps` 패키지의 `apps` 및 `etc` 폴더로 바꿉니다.

   1. 프로젝트 탐색기 패널에서 펼치기 `PROJECT.ui.apps` > `src` > `main` > `content` > `jcr_root` > `apps`>를 클릭합니다.
   1. 폴더를 마우스 오른쪽 단추로 클릭하고 `apps` 표시 위치 **>** 시스템 탐색기 **를**&#x200B;선택합니다.
   1. 이제 `apps` 볼 수 있는 및 `etc` 폴더를 삭제하고 콘텐트 패키지의 `apps` 및 `etc` 폴더를 여기에 배치합니다.
   1. Eclipse에서 프로젝트를 마우스 오른쪽 버튼으로 클릭하고 새로 고침 `PROJECT.ui.apps` 을 선택합니다 ****.

1. 그런 다음 해당 콘텐트 폴더를 패키지 `PROJECT.ui.content` 중 하나로 바꿉니다.

   1. 프로젝트 탐색기 패널에서 펼치기 `PROJECT.ui.content` > `src` > `main` > `content` > `jcr_root` > `content`>를 클릭합니다.
   1. 더 깊은 콘텐트 폴더를 마우스 오른쪽 단추로 클릭하고 **표시 위치** -> **시스템 탐색기를 선택합니다**.
   1. 이제 볼 콘텐트 폴더를 삭제하고 콘텐트 패키지의 콘텐트 폴더를 여기에 배치합니다.
   1. Eclipse에서 프로젝트를 마우스 오른쪽 버튼으로 클릭하고 새로 고침 `PROJECT.ui.content` 을 선택합니다 ****.

1. 이제 컨텐츠 패키지의 컨텐츠에 해당하려면 이 두 프로젝트의 `filter.xml` 파일을 업데이트해야 합니다. 이를 위해 컨텐츠 패키지의 `META-INF/vault/filter.xml` 파일을 별도의 텍스트/코드 편집기에서 엽니다.

   * 다음은 `filter.xml` 파일이 표시되는 방법의 예입니다.

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

1. 두 개의 프로젝트로 분할된 패키지의 내용에 대해서는 이러한 필터 규칙을 두 개의 프로젝트로 분할하고 그에 따라 두 프로젝트의 `filter.xml` 파일을 업데이트해야 합니다.

   1. Eclipse에서 엽니다 `PROJECT.ui.apps/src/main/content/META-INF/filter.xml`.
   1. 요소의 컨텐츠를 `<workspaceFilter>` `/apps` 패키지의 규칙으로 대체하며 `/etc`
      * 예:

         ```xml
         <?xml version="1.0" encoding="UTF-8"?>
         <workspaceFilter version="1.0">
            <filter root="/apps/foo"/>
            <filter root="/apps/foundation/components/bar"/>
            <filter root="/etc/designs/foo"/>
         </workspaceFilter>
         ```
   1. 그런 다음 엽니다 `PROJECT.ui.content/src/main/content/META-INF/filter.xml`.
   1. 규칙이 다음으로 시작되는 패키지의 규칙으로 대체됩니다 `/content`.
      * 예:

         ```xml
         <?xml version="1.0" encoding="UTF-8"?>
         <workspaceFilter version="1.0">
            <filter root="/content/foo"/>
            <filter root="/content/dam/foo"/>
            <filter root="/content/usergenerated/content/foo"/>
         </workspaceFilter>
         ```


1. 모든 변경 내용을 저장하세요. 이제 해당 새 컨텐츠를 AEM 인스턴스와 동기화할 수 있습니다.

1. 서버 패널에서 연결이 시작되었는지, 시작하지 않았는지 확인합니다.
1. 정리 **및 게시** 아이콘을 클릭합니다.

완료되면 인스턴스에서 패키지가 실행되고 저장되면 변경 내용이 자동으로 인스턴스에 동기화됩니다.

프로젝트에서 패키지를 다시 빌드하려면 또는 을 마우스 오른쪽 단추로 클릭하고 [다른 이름으로 `PROJECT.ui.apps` 실행] -> [ `PROJECT.ui.content` 마웬 **설치]를** 선택합니다 ****.

이제 패키지가 포함된 대상 폴더가 있습니다(예: `PROJECT.ui.apps-0.0.1-SNAPSHOT.zip`).

## 문제 해결 {#troubleshooting}

### 잘못된 프로젝트 정의 해결 {#resolving-invalid-project-definition}

잘못된 종속성 및 프로젝트 정의를 해결하려면 다음을 수행합니다.

1. 만든 프로젝트를 모두 선택합니다.
1. 마우스 오른쪽 버튼을 클릭합니다.
1. 컨텍스트 메뉴에서 Maven **** -> 프로젝트 **업데이트를 선택합니다**.
1. 스냅샷/ **릴리스의 강제 업데이트를 확인합니다**.
1. **확인**&#x200B;을 클릭합니다.

Eclipse는 필요한 종속성을 다운로드합니다. 시간이 좀 걸릴 수 있습니다.

## More information {#more-information}

Eclipse 웹 사이트를 위한 공식 Apache Sling IDE 도구 모음에서는 다음과 같은 유용한 정보를 제공합니다.

* Eclipse [**사용 안내서용** Apache Sling IDE 도구](https://sling.apache.org/documentation/development/ide-tooling.html), 이 설명서는 AEM 개발 도구에서 지원하는 전체 개념, 서버 통합 및 배포 기능을 안내합니다.
* 문제 [해결 섹션](https://sling.apache.org/documentation/development/ide-tooling.html#troubleshooting).
* 알려진 문제 [목록](https://sling.apache.org/documentation/development/ide-tooling.html#known-issues).

다음의 공식 [Eclipse](https://eclipse.org/) 설명서는 환경을 설정하는 데 도움이 됩니다.

* [Eclipse 시작하기](https://eclipse.org/users/)
* [Eclipse Luna Help System](https://help.eclipse.org/luna/index.jsp)
* [Maven 통합(m2eclipse)](https://www.eclipse.org/m2e/)
