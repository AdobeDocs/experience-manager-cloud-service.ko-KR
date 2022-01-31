---
title: 점진적 웹 앱 기능 활성화
description: AEM Sites을 사용하면 컨텐츠 작성자가 코딩 대신 간단한 구성을 통해 모든 사이트에 점진적 웹 앱 기능을 사용할 수 있습니다.
exl-id: 1552a4ce-137a-4208-b7f6-2fc06db8dc39
source-git-commit: 3910b47c5d25679d03409380d91afaa6ff5ab265
workflow-type: tm+mt
source-wordcount: '2004'
ht-degree: 0%

---

# 점진적 웹 앱 기능 활성화 {#enabling-pwa}

이제 컨텐츠 작성자는 간단한 구성을 통해 AEM Sites에서 만든 경험을 위해 점진적 웹 앱(PWA) 기능을 활성화할 수 있습니다.

>[!CAUTION]
>
>이 기능은 다음을 필요로 하는 고급 기능입니다.
>
>* PWA 지식
>* 사이트 및 컨텐츠 구조에 대한 지식
>* 캐싱 전략 이해
>* 개발 팀의 지원

>
>이 기능을 사용하기 전에 개발 팀과 함께 이를 논의하여 프로젝트에 활용할 수 있는 최상의 방법을 정의하는 것이 좋습니다.

## 소개 {#introduction}

[점진적 웹 앱(PWA)](https://developer.mozilla.org/en-US/docs/Web/Progressive_web_apps) AEM Sites를 사용자의 컴퓨터에 로컬로 저장하고 오프라인으로 액세스할 수 있도록 하여 앱과 유사한 몰입형 경험을 활성화합니다. 인터넷 연결이 끊겼더라도 이동 중에 사이트를 검색할 수 있습니다. PWA을 사용하면 네트워크가 손실되거나 불안정하더라도 원활한 경험을 제공할 수 있습니다.

컨텐츠 작성자는 사이트를 다시 코딩하는 대신 PWA 속성을 [페이지 속성](/help/sites-cloud/authoring/fundamentals/page-properties.md) 구현합니다.

* 이 구성은 저장 또는 게시되면 [매니페스트 파일](https://developer.mozilla.org/en-US/docs/Web/Manifest) 및 [서비스 작업자](https://developer.mozilla.org/en-US/docs/Web/API/Service_Worker_API) 사이트에서 PWA 기능을 활성화합니다.
* 또한 Sling 매핑은 애플리케이션 루트에서 서비스 작업자가 제공되어 앱 내에서 오프라인 기능을 허용하는 프록시 컨텐츠를 사용할 수 있도록 유지됩니다.

PWA을 사용하면 사이트의 로컬 복사본을 가지고 있으므로 인터넷에 연결하지 않고도 앱과 같은 경험을 제공합니다.

>[!NOTE]
>
>점진적 웹 앱은 로컬 앱 설치 및 기타 기능에 대한 진화된 기술 및 지원 [사용하는 브라우저에 따라 다릅니다.](https://developer.mozilla.org/en-US/docs/Web/Progressive_web_apps/Installable_PWAs#Summary)

## 전제 조건 {#prerequisites}

사이트에 PWA 기능을 사용하려면 프로젝트 환경에 두 가지 요구 사항이 있습니다.

1. [핵심 구성 요소 사용](#adjust-components) 이 기능을 활용하다
1. [디스패처 조정](#adjust-dispatcher) 필요한 파일을 표시하는 규칙

다음은 작성자가 개발 팀과 협력해야 하는 기술적 단계입니다. 이러한 단계는 사이트당 한 번만 필요합니다.

### 핵심 구성 요소 사용 {#adjust-components}

코어 구성 요소 릴리스 2.15.0 이상은 AEM 사이트의 PWA 기능을 완전히 지원합니다. AEMaaCS는 항상 최신 버전의 핵심 구성 요소를 포함하므로 즉시 사용 가능한 PWA 기능을 활용할 수 있습니다. AEMaaCS 프로젝트는 이 요구 사항을 자동으로 충족합니다.

>[!NOTE]
>
>Adobe은 사용자 지정 구성 요소나 구성 요소에 PWA 기능을 사용하지 않는 것이 좋습니다 [핵심 구성 요소에서 확장.](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/customizing.html)
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

### 디스패처 조정 {#adjust-dispatcher}

PWA 기능은 을 생성하고 사용합니다 `/content/<sitename>/manifest.webmanifest` 파일. 기본적으로 [디스패처](/help/implementing/dispatcher/overview.md) 은 이러한 파일을 표시하지 않습니다. 이러한 파일을 표시하려면 개발자가 다음 구성을 사이트 프로젝트에 추가해야 합니다.

```text
File location: [project directory]/dispatcher/src/conf.dispatcher.d/filters/filters.any >

# Allow webmanifest files
/0102 { /type "allow" /extension "webmanifest" /path "/content/*/manifest" }
```

프로젝트에 따라 rewrite 규칙에 다른 유형의 확장을 포함할 수 있습니다. 다음 `webmanifest` 확장은 요청을 숨기고 리디렉션하는 규칙을 도입했을 때 rewrite 조건에 포함하는 데 유용할 수 있습니다 `/content/<projectName>`.

```text
RewriteCond %{REQUEST_URI} (.html|.jpe?g|.png|.svg|.webmanifest)$
```

## 사이트에 대한 PWA 활성화 {#enabling-pwa-for-your-site}

사용 [전제 조건](#prerequisites) met, 컨텐츠 작성자가 사이트에 PWA 기능을 활성화하는 것은 매우 쉽습니다. 다음은 이 작업을 수행하는 방법에 대한 기본 개요입니다. 개별 옵션은 섹션에 자세히 설명되어 있습니다 [세부 옵션.](#detailed-options)

1. AEM에 로그인합니다.
1. 기본 메뉴에서 을(를) 탭하거나 클릭합니다 **탐색** -> **Sites**.
1. 사이트 프로젝트를 선택하고 탭하거나 클릭합니다 [**속성**](/help/sites-cloud/authoring/fundamentals/page-properties.md) 또는 핫키 를 사용합니다 `p`.
1. 을(를) 선택합니다 **Progressive Web App** 탭하고 해당 속성을 구성합니다. 최소한 다음을 수행할 수 있습니다.
   1. 옵션을 선택합니다 **PWA 활성화**.
   1. 을(를) 정의합니다 **시작 URL**.

      ![PWA(점진적 웹 앱) 사용](../assets/pwa-enable.png)

   1. 512x512 png 아이콘을 DAM에 업로드하고 이를 앱의 아이콘으로 참조합니다.

      ![PWA 정의 아이콘](../assets/pwa-icon.png)

   1. 서비스 작업자가 오프라인으로 전환할 경로를 구성합니다. 일반적인 경로는 다음과 같습니다.
      * `/content/<sitename>`
      * `/content/experiencefragements/<sitename>`
      * `/content/dam/<sitename>`
      * 모든 타사 글꼴 참조
      * `/etc/clientlibs/<sitename>`

      ![PWA 오프라인 경로 정의](../assets/pwa-offline.png)


1. 탭 또는 클릭 **저장 및 닫기**.

이제 사이트가 구성되었으며 다음 작업을 수행할 수 있습니다 [로컬 앱으로 설치합니다.](#using-pwa-enabled-site)

## PWA 지원 사이트 사용 {#using-pwa-enabled-site}

이제 [PWA을 지원하도록 사이트를 구성했습니다.](#enabling-pwa-for-your-site) 직접 체험하실 수 있습니다.

1. 에서 사이트에 액세스 [지원되는 브라우저입니다.](https://developer.mozilla.org/en-US/docs/Web/Progressive_web_apps/Installable_PWAs#Summary)
1. 브라우저의 주소 표시줄에 사이트를 로컬 앱으로 설치할 수 있음을 나타내는 새 아이콘이 표시됩니다.
   * 브라우저에 따라 아이콘이 다를 수 있으며, 브라우저에도 로컬 앱으로 설치할 수 있음을 나타내는 알림(예: 배너 또는 대화 상자)이 표시될 수 있습니다.
1. 앱을 설치합니다.
1. 앱이 장치의 홈 화면에 설치됩니다.
1. 앱을 열고 페이지를 탐색한 다음 오프라인에서 사용할 수 있는지 확인합니다.

## 세부 옵션 {#detailed-options}

다음 섹션에서는 다음 경우에 사용할 수 있는 옵션에 대해 자세히 설명합니다 [PWA 사이트 구성](#enabling-pwa-for-your-site)

### 설치 가능한 경험 구성 {#configure-installable-experience}

이러한 설정을 사용하면 방문자의 홈 화면에서 사이트를 설치하고 오프라인에서 사용할 수 있도록 함으로써 사이트가 기본 앱처럼 작동할 수 있습니다.

* **PWA 활성화** - 사이트에 대한 PWA을 활성화하는 주요 토글입니다.
* **시작 URL** - 다음 [기본 시작 URL](https://developer.mozilla.org/en-US/docs/Web/Manifest/start_url) 사용자가 로컬로 설치된 앱을 로드할 때 앱이 열립니다.
   * 이는 컨텐츠 구조의 모든 경로가 될 수 있습니다.
   * 루트가 될 필요가 없으며 앱에 대한 전용 시작 페이지이기도 합니다.
   * 이 URL이 상대적인 경우 매니페스트 URL이 기본 URL로 사용되어 문제를 해결합니다.
   * 비워 두면 이 기능은 웹 앱이 설치된 웹 페이지의 주소를 사용합니다.
   * 값을 설정하는 것이 좋습니다.
* **표시 모드** - PWA 지원 앱은 여전히 브라우저를 통해 전달된 AEM 사이트입니다. [이러한 표시 옵션](https://developer.mozilla.org/en-US/docs/Web/Manifest/display) 브라우저를 숨기거나 로컬 장치에서 사용자에게 표시하는 방법을 정의합니다.
   * **독립형** - 브라우저가 사용자로부터 완전히 숨겨져 있으며, 기본 앱처럼 표시됩니다. 기본값이 됩니다.
      * 이 옵션을 사용하면 브라우저의 탐색 컨트롤을 사용하지 않고 사이트 페이지에서 링크 및 구성 요소를 사용하여 컨텐츠를 완전히 통해 앱 탐색을 수행할 수 있어야 합니다.
   * **브라우저** - 사이트를 방문할 때와 동일하게 브라우저가 표시됩니다.
   * **최소 UI** - 브라우저가 대부분 기본 앱처럼 숨겨져 있지만 기본 탐색 컨트롤은 노출됩니다.
   * **전체 화면** - 브라우저가 기본 앱처럼 완전히 숨겨져 있지만 전체 화면 모드로 렌더링됩니다.
      * 이 옵션을 사용하면 브라우저의 탐색 컨트롤을 사용하지 않고 사이트 페이지에서 링크 및 구성 요소를 사용하여 컨텐츠를 완전히 통해 앱 탐색을 수행할 수 있어야 합니다.
* **화면 방향** - 로컬 앱으로서 PWA은 처리 방법을 알아야 합니다 [장치 방향.](https://developer.mozilla.org/en-US/docs/Web/Manifest/orientation)
   * **임의** - 사용자의 장치 방향을 조정합니다. 기본값이 됩니다.
   * **세로** - 이렇게 하면 사용자의 장치 방향과 관계없이 앱이 세로 레이아웃으로 열립니다.
   * **가로** - 이렇게 하면 사용자의 장치 방향과 관계없이 앱이 가로 레이아웃으로 열립니다.
* **테마 색상** - 다음을 정의합니다 [앱의 색상](https://developer.mozilla.org/en-US/docs/Web/Manifest/theme_color) 로컬 사용자의 운영 체제에서 기본 UI 도구 모음 및 탐색 컨트롤을 표시하는 방식에 영향을 줍니다. 브라우저에 따라 다른 앱 프레젠테이션 요소에 영향을 줄 수 있습니다.
   * 색상 웰 팝업을 사용하여 색상을 선택합니다.
   * 색상은 16진수 또는 RGB 값으로 정의할 수도 있습니다.
* **배경색** - 다음을 정의합니다 [앱의 배경색,](https://developer.mozilla.org/en-US/docs/Web/Manifest/background_color) 이 값은 앱이 로드될 때 표시됩니다.
   * 색상 웰 팝업을 사용하여 색상을 선택합니다.
   * 색상은 16진수 또는 RGB 값으로 정의할 수도 있습니다.
   * 특정 브라우저 [자동으로 시작 화면 작성](https://developer.mozilla.org/en-US/docs/Web/Manifest#Splash_screens) 앱 이름, 배경색 및 아이콘에서 다음을 수행합니다.
* **아이콘** - 다음을 정의합니다 [아이콘](https://developer.mozilla.org/en-US/docs/Web/Manifest/icons) 사용자의 장치에 있는 앱을 나타냅니다.
   * 아이콘은 크기가 512x512픽셀인 png 파일이어야 합니다.
   * 아이콘은 [DAM에 저장됩니다.](/help/assets/overview.md)

### 캐시 관리(고급) {#offline-configuration}

이러한 설정은 이 사이트의 일부를 오프라인으로 사용할 수 있도록 하며 방문자의 장치에서 로컬로 사용할 수 있도록 합니다. 이를 통해 웹 앱의 캐시를 제어하여 네트워크 요청을 최적화하고 오프라인 경험을 지원할 수 있습니다.

* **컨텐츠 새로 고침 빈도 및 캐싱 전략** - 이 설정은 PWA의 캐싱 모델을 정의합니다.
   * **적당히** - [이 설정](https://web.dev/stale-while-revalidate/) 는 대부분의 사이트에 대해 해당되며 기본값은 입니다.
      * 이 설정을 사용하면 사용자가 처음 본 컨텐츠가 캐시에서 로드되고 사용자가 해당 컨텐츠를 사용하는 동안 캐시의 나머지 컨텐츠의 유효성을 다시 검사합니다.
   * **자주** &quot; 이는 경매장과 같이 업데이트가 매우 빨리 필요한 사이트의 경우입니다.&quot;
      * 이 설정을 사용하면 앱이 먼저 네트워크를 통해 최신 콘텐츠를 검색하며, 사용할 수 없는 경우 로컬 캐시에 다시 저장됩니다.
   * **거의 없음** - 참조 페이지와 같이 거의 정적이 되는 사이트의 경우입니다.
      * 이 설정을 사용하면 앱이 먼저 캐시에서 콘텐츠를 찾고, 사용할 수 없는 경우 다시 네트워크로 폴백하여 검색합니다.
* **파일 사전 캐싱** - AEM에서 호스팅되는 이러한 파일은 서비스 작업자가 설치될 때와 사용되기 전에 로컬 브라우저 캐시에 저장됩니다. 이렇게 하면 오프라인 상태일 때 웹 앱이 완전히 작동할 수 있습니다.
* **경로 포함** - 정의된 경로에 대한 네트워크 요청은 가로채지고, 캐시된 컨텐츠는 구성된 내용에 따라 반환됩니다 **컨텐츠 새로 고침 빈도 및 캐싱 전략**.
* **캐시 제외** - 이러한 파일은 **파일 사전 캐싱** 및 **경로 포함**.

>[!TIP]
>
>개발자 팀에는 오프라인 구성을 설정하는 방법에 대한 중요한 입력이 있을 수 있습니다.

## 제한 사항 및 Recommendations {#limitations-recommendations}

AEM Sites에 일부 PWA 기능을 사용할 수 있는 것은 아닙니다. 다음은 몇 가지 주목할 만한 제한 사항입니다.

* 사용자가 앱을 사용하지 않는 경우 페이지가 자동으로 동기화되거나 업데이트되지 않습니다.

또한 Adobe은 PWA을 구현할 때 다음과 같은 권장 사항을 제공합니다.

### 사전 캐싱할 리소스 수를 최소화합니다. {#minimize-precache}

Adobe은 페이지 수를 사전 캐시로 제한하도록 권장합니다.

* 포함 라이브러리를 사용하여 사전 캐싱 시 관리할 항목 수를 줄입니다.
* 이미지 변형 수를 사전 캐시로 제한합니다.

### 프로젝트 스크립트 및 스타일시트가 안정화된 후 PWA을 활성화합니다. {#pwa-stabilized}

클라이언트 라이브러리는 다음 패턴을 관찰하는 캐시 선택기의 추가와 함께 전달됩니다 `lc-<checksumHash>-lc`. 라이브러리 변경을 구성하는 파일(및 종속성) 중 하나가 변경될 때마다 이 선택기가 변경됩니다. 서비스 작업자가 미리 캐싱할 클라이언트 라이브러리를 나열하고 새 버전을 참조하려는 경우 항목을 수동으로 검색하고 업데이트합니다. 따라서 프로젝트 스크립트 및 스타일시트가 안정화된 후 사이트를 PWA으로 구성하는 것이 좋습니다.

### 이미지 변형 수를 최소화합니다. {#minimize-variations}

AEM 코어 구성 요소의 이미지 구성 요소 는 가져올 최고의 렌디션의 프런트엔드 중 하나를 결정합니다. 이 메커니즘에는 해당 리소스의 마지막 수정 시간에 해당하는 타임스탬프도 포함됩니다. 이 메커니즘은 PWA 사전 캐시의 구성을 복잡하게 합니다.

사전 캐시를 구성할 때는 가져올 수 있는 모든 경로 변형을 나열해야 합니다. 이러한 변형은 품질 및 폭과 같은 매개 변수로 구성됩니다. 이러한 변형의 수를 최대 3개(작은, 중간, 큰)로 줄이는 것이 좋습니다. 의 컨텐츠 정책 대화 상자를 통해 이 작업을 수행할 수 있습니다 [이미지 구성 요소.](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/components/image.html)

신중하게 구성하지 않으면 메모리 및 네트워크 사용량이 PWA 성능에 심각한 영향을 줄 수 있습니다. 또한 50개의 이미지를 미리 캐시하고 이미지당 3개의 너비를 보유하려는 경우 사이트를 유지 관리하는 사용자는 페이지 속성의 PWA 사전 캐시 섹션에서 최대 150개의 항목 목록을 유지 관리해야 합니다.

또한 Adobe에서는 프로젝트 이미지 사용이 안정화된 후 사이트를 PWA으로 구성할 것을 권장합니다.
