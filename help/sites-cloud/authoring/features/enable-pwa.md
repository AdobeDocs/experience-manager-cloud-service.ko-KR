---
title: 점진적 웹 앱 기능 활성화
description: 컨텐츠 작성자는 AEM Sites을 사용하여 코딩 대신 간단한 구성을 통해 모든 사이트에 점진적 웹 앱 기능을 활성화할 수 있습니다.
hide: true
hidefromtoc: true
translation-type: tm+mt
source-git-commit: 8fa74c2c575409659f482c669c4939a623ef6707
workflow-type: tm+mt
source-wordcount: '2032'
ht-degree: 0%

---


# 점진적 웹 앱 기능 활성화 {#enabling-pwa}

이제 컨텐츠 작성자는 간단한 구성을 통해 AEM Sites에서 만든 경험에 대한 점진적 웹 앱(PWA) 기능을 활성화할 수 있습니다.

>[!CAUTION]
>
>이 기능은 다음과 같은 고급 기능을 필요로 합니다.
>
>* PWA 지식
>* 사이트 및 컨텐츠 구조에 대한 지식
>* 캐싱 전략 이해
>* 개발 팀의 지원

>
>
이 기능을 사용하기 전에 개발 팀과 이 문제를 논의하여 프로젝트에 활용할 수 있는 최상의 방법을 정의하는 것이 좋습니다.

>[!NOTE]
>
>이 문서에 설명된 기능은 AEM의 [2021년 3월 릴리스를 Cloud Service으로 사용할 수 있도록 예정되어 있습니다.](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap.html)

## 소개 {#introduction}

[점진적 웹 앱(PWA)](https://developer.mozilla.org/en-US/docs/Web/Progressive_web_apps) 을 사용하면 AEM 사이트에 매력적인 앱과 같은 경험을 통해 로컬에 사용자 시스템에 저장하고 오프라인으로 액세스할 수 있습니다. 이동 중에도 인터넷 연결을 끊더라도 사용자가 사이트를 검색할 수 있습니다. PWA은 네트워크가 손실되거나 불안정하더라도 완벽한 경험을 제공합니다.

컨텐츠 작성자는 사이트를 다시 코딩할 필요 없이 사이트의 [페이지 속성](/help/sites-cloud/authoring/fundamentals/page-properties.md)에서 PWA 속성을 추가 탭으로 구성할 수 있습니다.

* 이 구성은 저장 또는 게시할 때 사이트에서 PWA 기능을 활성화하는 [매니페스트 파일](https://developer.mozilla.org/en-US/docs/Web/Manifest) 및 [서비스 작업자](https://developer.mozilla.org/en-US/docs/Web/API/Service_Worker_API)를 기록하는 이벤트 핸들러를 트리거합니다.
* 또한 서비스 워커가 응용 프로그램 루트에서 제공되어 앱 내에서 오프라인 기능을 허용하는 콘텐츠를 프록시할 수 있도록 하도록 하기 위해 슬링 매핑도 유지됩니다.

사용자는 PWA을 통해 로컬 사이트 사본을 볼 수 있으므로 인터넷에 연결하지 않고도 앱과 같은 경험을 할 수 있습니다.

>[!NOTE]
>
>점진적 웹 앱은 진화하는 기술이며 로컬 앱 설치에 대한 지원과 기타 기능 [은 사용하는 브라우저에 따라 다릅니다.](https://developer.mozilla.org/en-US/docs/Web/Progressive_web_apps/Installable_PWAs#Summary)

## 전제 조건 {#prerequisites}

사이트에 PWA 기능을 사용하려면 프로젝트 환경에 다음과 같은 두 가지 요구 사항이 있습니다.

1. [핵심 ](#adjust-components) 구성 요소를 사용하여 이 기능 활용
1. [필요한 ](#adjust-dispatcher) 파일을 표시하도록 디스패처 규칙을 조정합니다.

이러한 단계는 작성자가 개발 팀과 협력해야 하는 기술적 단계입니다. 이러한 단계는 사이트당 한 번만 필요합니다.

### 코어 구성 요소 사용 {#adjust-components}

핵심 구성 요소 릴리스 2.15.0 이상 버전은 AEM 사이트의 PWA 기능을 완벽하게 지원합니다. AEMaaCS는 항상 최신 버전의 핵심 구성 요소를 포함하므로 즉시 PWA 기능을 활용할 수 있습니다. AEM AaCS 프로젝트는 자동으로 이 요구 사항을 충족합니다.

>[!NOTE]
>
>Adobe에서는 추가 구성 요소에서 확장되지 않은 [사용자 지정 구성 요소 또는 구성 요소에 PWA 기능을 사용하는 것이 권장되지 않습니다.](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/customizing.html)
<!--
Your components need to include the [manifest files](https://developer.mozilla.org/en-US/docs/Web/Manifest) and [service worker,](https://developer.mozilla.org/en-US/docs/Web/API/Service_Worker_API) which supports the PWA features.

 To do this, the developer will need to add the following link to the `customheaderlibs.html` file of your page component.

```xml
<link rel="manifest" href="/content/<projectName>/manifest.webmanifest" crossorigin="use-credentials"/>
```

The developer will also need to add the following link to the `customfooterlibs.html` file of your page component.

```xml
<script>
        // Check that service workers are supported
        if ('serviceWorker' in navigator) {
            // Use the window load event to make sure the page load performs well
            window.addEventListener('load', () => {
                let serviceWorker = '/<projectName>sw.js';
                navigator.serviceWorker.register(serviceWorker);
            });
        }
</script>
```
-->

### 디스패처 {#adjust-dispatcher} 조정

PWA 기능은 `/content/<sitename>/manifest.webmanifest` 파일을 생성하고 사용합니다. 기본적으로 [디스패처](/help/implementing/dispatcher/overview.md)는 이러한 파일을 표시하지 않습니다. 이러한 파일을 표시하려면 개발자가 사이트 프로젝트에 다음 구성을 추가해야 합니다.

```text
File location: [project directory]/dispatcher/src/conf.dispatcher.d/filters/filters.any >

# Allow webmanifest files
/0102 { /type "allow" /extension "webmanifest" /path "/content/*/manifest" }
```

프로젝트에 따라 다시 작성 규칙에 서로 다른 유형의 확장을 포함할 수 있습니다. `webmanifest` 확장은 요청을 숨기거나 `/content/<projectName>`로 리디렉션하는 규칙을 소개할 때 다시 작성 조건에 포함하는 데 유용합니다.

```text
RewriteCond %{REQUEST_URI} (.html|.jpe?g|.png|.svg|.webmanifest)$
```

## 사이트 {#enabling-pwa-for-your-site}에 대한 PWA 활성화

[사전 요구 사항](#prerequisites)이 충족되면 컨텐츠 작성자가 사이트에 PWA 기능을 활성화할 수 있습니다. 다음은 이 작업을 수행하는 방법에 대한 기본 개요입니다. 개별 옵션은 섹션 [세부 옵션](#detailed-options)에 자세히 설명되어 있습니다.

1. AEM에 로그인합니다.
1. 주 메뉴에서 **탐색** -> **사이트**&#x200B;를 탭하거나 클릭합니다.
1. 사이트 프로젝트를 선택하고 [**속성**](/help/sites-cloud/authoring/fundamentals/page-properties.md)&#x200B;을 탭하거나 클릭하거나 핫키 `p`를 사용합니다.
1. **점진적 웹 앱** 탭을 선택하고 해당 속성을 구성합니다. 최소한 다음을 수행합니다.
   1. **PWA 활성화** 옵션을 선택합니다.
   1. **시작 URL**&#x200B;을 정의합니다.

      ![PWA(점진적 웹 앱) 사용](../assets/pwa-enable.png)

   1. 512x512 png 아이콘을 DAM에 업로드하고 이를 앱의 아이콘으로 참조합니다.

      ![PWA 정의 아이콘](../assets/pwa-icon.png)

   1. 서비스 워커가 오프라인으로 전환할 경로를 구성합니다. 일반적인 경로는 다음과 같습니다.
      * `/content/<sitename>`
      * `/content/experiencefragements/<sitename>`
      * `/content/dam/<sitename>`
      * 타사 글꼴 참조
      * `/etc/clientlibs/<sitename>`

      ![PWA 오프라인 경로 정의](../assets/pwa-offline.png)


1. **저장 및 닫기**&#x200B;를 탭하거나 클릭합니다.

사이트가 구성되었으며 [이(가) 로컬 앱으로 설치할 수 있습니다.](#using-pwa-enabled-site)

## PWA 사용 사이트 {#using-pwa-enabled-site} 사용

이제 [이(가) PWA을 지원하도록 사이트를 구성했으므로](#enabling-pwa-for-your-site)을(를) 직접 경험할 수 있습니다.

1. [지원되는 브라우저에서 사이트에 액세스합니다.](https://developer.mozilla.org/en-US/docs/Web/Progressive_web_apps/Installable_PWAs#Summary)
1. 브라우저의 주소 표시줄에 사이트를 로컬 앱으로 설치할 수 있음을 나타내는 새 아이콘이 표시됩니다.
   * 브라우저에 따라 아이콘이 달라질 수 있으며, 브라우저에는 로컬 앱으로 설치할 수 있다는 알림(배너 또는 대화 상자 등)이 표시될 수도 있습니다.
1. 앱을 설치합니다.
1. 앱이 장치의 홈 화면에 설치됩니다.
1. 앱을 열고 페이지를 탐색한 다음 오프라인에서 사용할 수 있는지 확인합니다.

## 세부 옵션 {#detailed-options}

다음 섹션에서는 [PWA에 대한 사이트를 구성할 때 사용할 수 있는 옵션에 대해 자세히 설명합니다.](#enabling-pwa-for-your-site)

### 설치 가능한 환경 구성 {#configure-installable-experience}

이러한 설정을 통해 사이트는 방문자의 홈 화면에서 설치 가능을 설정함으로써 기본 앱처럼 작동할 수 있습니다.

* **PWA**  활성화 - 사이트에 대한 PWA을 활성화하는 기본 토글입니다.
* **시작 URL** - 사용자가  [로컬로 설치된 앱을 로드할 때 앱이 열리는 기본 ](https://developer.mozilla.org/en-US/docs/Web/Manifest/start_url) 시작 URL입니다.
   * 콘텐츠 구조의 모든 경로가 될 수 있습니다.
   * 루트가 될 필요가 없으며 앱에 대한 전용 시작 페이지인 경우가 있습니다.
   * 이 URL이 상대적이면 매니페스트 URL이 문제를 해결하기 위해 기본 URL로 사용됩니다.
   * 비워 두면 앱이 설치된 웹 페이지의 주소가 사용됩니다.
   * 값을 설정하는 것이 좋습니다.
* **표시 모드**  - PWA이 활성화된 앱은 여전히 브라우저를 통해 제공되는 AEM 사이트입니다. [이러한 표시 ](https://developer.mozilla.org/en-US/docs/Web/Manifest/display) 옵션은 로컬 장치의 사용자에게 브라우저 숨김 또는 표시 방법을 정의합니다.
   * **독립 실행형**  - 브라우저가 사용자로부터 완전히 숨겨져 있으며 기본 앱처럼 표시됩니다. 기본값입니다.
      * 이 옵션을 사용하면 브라우저의 내비게이션 컨트롤을 사용하지 않고도 사이트의 페이지에 있는 링크 및 구성 요소를 사용하여 컨텐츠를 통해 앱 내비게이션을 완전히 수행할 수 있어야 합니다.
   * **브라우저**  - 일반적으로 사이트를 방문할 때와 같이 브라우저가 나타납니다.
   * **최소 UI**  - 브라우저는 대부분 기본 앱과 같이 숨겨지지만 기본 탐색 컨트롤은 노출됩니다.
   * **전체 화면**  - 브라우저는 기본 앱처럼 완전히 숨겨져 있지만 전체 화면 모드로 렌더링됩니다.
      * 이 옵션을 사용하면 브라우저의 내비게이션 컨트롤을 사용하지 않고도 사이트의 페이지에 있는 링크 및 구성 요소를 사용하여 컨텐츠를 통해 앱 내비게이션을 완전히 수행할 수 있어야 합니다.
* **화면 방향**  - 로컬 앱인 PWA은  [장치 방향을 처리하는 방법을 알아야 합니다.](https://developer.mozilla.org/en-US/docs/Web/Manifest/orientation)
   * **임의**  - 앱이 사용자 장치의 방향에 따라 조정됩니다. 기본값입니다.
   * **세로**  - 이로 인해 사용자 장치의 방향에 관계 없이 앱이 세로 레이아웃에서 열립니다.
   * **가로**  - 이로 인해 사용자 장치의 방향에 관계 없이 앱이 가로 레이아웃으로 열립니다.
* **테마 색상**  - 로컬 사용자의 운영 체제에서 기본 UI  [도구 ](https://developer.mozilla.org/en-US/docs/Web/Manifest/theme_color) 모음 및 내비게이션 컨트롤을 표시하는 방법에 영향을 주는 애플리케이션의 색상을 정의합니다. 브라우저에 따라 다른 앱 프레젠테이션 요소에 영향을 줄 수 있습니다.
   * 색상 웰 팝업을 사용하여 색상을 선택합니다.
   * 색상은 16진수 또는 RGB 값으로 정의할 수도 있습니다.
* **배경색**  - 앱이 로드될 때 표시되는  [앱의 ](https://developer.mozilla.org/en-US/docs/Web/Manifest/background_color) 배경색을 정의합니다.
   * 색상 웰 팝업을 사용하여 색상을 선택합니다.
   * 색상은 16진수 또는 RGB 값으로 정의할 수도 있습니다.
   * 특정 브라우저 [에서는 앱 이름, 배경색 및 아이콘에서 시작 화면을 자동으로](https://developer.mozilla.org/en-US/docs/Web/Manifest#Splash_screens)만듭니다.
* **아이콘**  - 사용자 [의 장치](https://developer.mozilla.org/en-US/docs/Web/Manifest/icons) 에 있는앱을 나타내는 아이콘을 정의합니다.
   * 아이콘은 크기가 512x512픽셀인 png 파일이어야 합니다.
   * 아이콘은 [DAM에 저장되어 있어야 합니다.](/help/assets/overview.md)

### 캐시 관리(고급) {#offline-configuration}

이러한 설정을 사용하면 이 사이트의 일부를 오프라인으로 사용할 수 있으며 방문자의 장치에서 로컬로 사용할 수 있습니다. 따라서 웹 앱의 캐시를 제어하여 네트워크 요청을 최적화하고 오프라인 경험을 지원할 수 있습니다.

* **컨텐츠 새로 고침의 캐싱 전략**  및 빈도 - 이 설정은 PWA에 대한 캐싱 모델을 정의합니다.
   * **적당히**   [- ](https://web.dev/stale-while-revalidate/) 이설정은 대부분의 사이트에서 사용되며 기본값입니다.
      * 이 설정을 사용하면 사용자가 처음 본 콘텐트가 캐시에서 로드되며 사용자가 해당 콘텐트를 사용하는 동안 캐시에 있는 나머지 콘텐트의 유효성을 다시 확인합니다.
   * **자주**  - 경매 사이트와 같이 업데이트가 매우 빨리 필요한 사이트에는 이러한 문제가 있습니다.
      * 이 설정을 사용하면 앱이 먼저 네트워크를 통해 최신 콘텐츠를 검색하고, 사용하지 못할 경우 로컬 캐시로 돌아갑니다.
   * **드물게** - 참조 페이지와 같이 거의 정적인 사이트에 해당됩니다.
      * 이 설정을 사용하면 앱은 먼저 캐시에서 콘텐츠를 검색하고, 사용할 수 없는 경우 다시 네트워크로 가져와 검색합니다.
* **파일 사전 캐싱**  - AEM에서 호스팅되는 파일은 서비스 워커가 설치되고 사용되기 전에 로컬 브라우저 캐시에 저장됩니다. 이렇게 하면 오프라인에서는 웹 앱이 완전히 기능할 수 있습니다.
* **경로 포함**  - 정의된 경로에 대한 네트워크 요청은 차단되고 캐시된 컨텐츠는 구성된  **캐싱 전략 및 컨텐츠 새로 고침 빈도에 따라 반환됩니다**.
* **캐시 제외**  - 이러한 파일은 파일  **사전** 캐시 및  **경로** 포함에 있는 설정에 관계없이 캐시되지 않습니다.

>[!TIP]
>
>개발자 팀은 오프라인 구성을 설정하는 방법에 대한 중요한 의견을 가지고 있을 수 있습니다.

## 제한 사항 및 Recommendations {#limitations-recommendations}

일부 PWA 기능은 AEM Sites에 사용할 수 없습니다. 몇 가지 주목할 만한 제한 사항입니다.

* 사용자가 앱을 사용하지 않는 경우 페이지가 자동으로 동기화되거나 업데이트되지 않습니다.

또한 PWA을 구현할 때 Adobe에서 다음 권장 사항을 만듭니다.

### 사전 캐시할 리소스 수를 최소화합니다.{#minimize-precache}

Adobe은 페이지 수를 사전 캐시로 제한할 것을 권장합니다.

* 라이브러리를 포함하여 사전 캐싱 시 관리할 항목 수를 줄입니다.
* 이미지 변형 수를 사전 캐시로 제한합니다.

### 프로젝트 스크립트 및 스타일시트가 안정화된 후 PWA을 활성화합니다.{#pwa-stabilized}

클라이언트 라이브러리는 다음 패턴 `lc-<checksumHash>-lc`을 준수하는 캐시 선택기가 추가된 상태로 제공됩니다. 라이브러리를 구성하는 파일(및 종속성) 중 하나가 변경될 때마다 이 선택기가 변경됩니다. 서비스 근로자가 미리 캐싱할 클라이언트-라이브러리를 나열하고 새 버전을 참조하려는 경우 수동으로 항목을 검색하고 업데이트합니다. 따라서 프로젝트 스크립트 및 스타일 시트가 안정화된 후 사이트를 PWA으로 구성하는 것이 좋습니다.

### 이미지 변형 수를 최소화할 수 있습니다.{#minimize-variations}

AEM 코어 구성 요소의 이미지 구성 요소는 가져올 최상의 변환의 프런트 엔드를 결정합니다. 이 메커니즘에는 해당 리소스의 마지막 수정 시간에 해당하는 타임스탬프도 포함됩니다. 이 메커니즘은 PWA 사전 캐시 구성을 복잡하게 합니다.

사전 캐시를 구성할 때 사용자는 가져올 수 있는 모든 경로 변형을 나열해야 합니다. 이러한 변형은 품질과 폭과 같은 매개 변수로 구성됩니다. 이러한 변형의 수를 최대 3개(소형, 중간, 큼)로 줄이는 것이 좋습니다. 이 작업은 [이미지 구성 요소의 콘텐츠 정책 대화 상자를 통해 수행할 수 있습니다.](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/components/image.html)

신중하게 구성하지 않으면 메모리 및 네트워크 사용이 PWA 성능에 심각한 영향을 줄 수 있습니다. 이미지를 50개, 이미지당 3개 폭을 미리 캐시하려는 경우 사이트를 유지 관리하는 사용자는 페이지 속성의 PWA 사전 캐시 섹션에 최대 150개 항목 목록을 유지 관리해야 합니다.

또한 Adobe에서는 이미지 작업이 안정화된 후 사이트를 PWA으로 구성할 것을 권장합니다.
