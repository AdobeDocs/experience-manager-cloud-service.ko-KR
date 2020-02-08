---
title: Adobe Analytics 및 Adobe Launch와 Dynamic Media Viewer 통합
description: Dynamic Media Viewers 5.13 릴리스와 함께 Adobe Launch용 Dynamic Media Viewers 확장을 사용하면 Dynamic Media, Adobe Analytics 및 Adobe Launch 고객은 Adobe Launch 구성에서 Dynamic Media Viewer에 고유한 이벤트 및 데이터를 사용할 수 있습니다.
translation-type: tm+mt
source-git-commit: 6224d193adfb87bd9b080f48937e0af1f03386d6

---


# Adobe Analytics 및 Adobe Launch와 Dynamic Media Viewer 통합 {#integrating-dynamic-media-viewers-with-adobe-analytics-and-adobe-launch}

## Adobe Analytics 및 Adobe Launch와 Dynamic Media Viewers 통합이란 무엇입니까? {#what-is-dynamic-media-viewers-integration-with-adobe-analytics-and-adobe-launch}

The new *Dynamic Media Viewers* extension for Adobe Launch, along with the recent release of Dynamic Media Viewers 5.13, lets customers of Dynamic Media, Adobe Analytics, and Adobe Launch to use events and data specific for the Dynamic Media Viewers in their Adobe Launch configuration.

이 통합은 Adobe Analytics를 사용하여 웹 사이트에서 Dynamic Media Viewer의 사용을 추적할 수 있음을 의미합니다. 동시에, Adobe 또는 타사에서 제공하는 기타 Launch 확장 기능과 함께 뷰어에서 노출한 이벤트와 데이터를 사용할 수 있습니다.

익스텐션에 [대한 자세한 내용은](https://docs.adobe.com/content/help/en/launch/using/extensions-ref/overview.html) Experience Platform 시작 사용 안내서의 Adobe 익스텐션을 참조하십시오.

**** 본 문서를 읽어야 하는 사람:사이트 관리자, AEM 플랫폼의 개발자 및 운영

### 통합의 제한 사항 {#limitations-of-the-integration}

* Dynamic Media 뷰어에 대한 Adobe Launch 통합은 AEM 작성자 노드에서 작동하지 않습니다. WCM 페이지가 게시될 때까지 추적 내용을 볼 수 없습니다.
* Dynamic Media 뷰어에 대한 Adobe Launch 통합은 &quot;팝업&quot; 작업 모드에서 지원되지 않습니다. 이 모드에서는 자산 세부 사항 페이지의 &quot;URL&quot; 단추를 사용하여 뷰어 URL을 얻을 수 있습니다.
* Adobe Launch 통합을 이전 뷰어 Analytics 통합(매개 변수 방식)과 동시에 사용할 수 `config2=` 없습니다.
* 비디오 추적에 대한 지원은 추적 개요에 설명된 바와 같이 핵심 재생 추적으로만 [제한됩니다](https://docs.adobe.com/content/help/en/media-analytics/using/sdk-implement/track-av-playback/track-core-overview.html). 특히 QoS, 광고, 장/세그먼트 또는 오류 추적은 지원되지 않습니다.
* 데이터 요소에 대한 저장소 지속 시간 구성은 다이내믹 미디어 뷰어 *확장을 사용하는 데이터 요소에 대해 지원되지* 않습니다. 스토리지 지속 시간을 없음으로 설정해야 **[!UICONTROL 합니다]**.

### 통합에 대한 활용 사례 {#use-cases-for-the-integration}

Adobe Launch와의 통합에 대한 주요 사용 사례는 AEM Assets와 AEM Sites를 모두 사용하는 고객입니다. 이러한 시나리오에서는 AEM 작성자 노드와 Adobe Launch 간의 표준 통합을 설정한 다음 사이트 인스턴스를 Adobe Launch 속성에 연결할 수 있습니다. 그런 다음 사이트 페이지에 추가된 Dynamic Media WCM 구성 요소는 뷰어의 데이터 및 이벤트를 추적합니다.

AEM [Sites의 Dynamic Media 뷰어 추적을 참조하십시오](https://wiki.corp.adobe.com/display/~oufimtse/Dynamic+Media+Viewers+integration+with+Adobe+Launch#DynamicMediaViewersintegrationwithAdobeLaunch-TrackingDynamicMediaViewersinAEMSites).

통합이 지원하는 보조 사용 사례는 AEM Assets만 사용하는 고객 또는 Dynamic Media Classic입니다. 이러한 경우 뷰어에 대한 포함 코드를 입수하여 웹 사이트 페이지에 추가합니다. 그런 다음 Adobe Launch에서 Adobe Launch 라이브러리 제작 URL을 가져와 수동으로 웹 페이지 코드에 추가합니다.

포함 [코드를](https://wiki.corp.adobe.com/display/~oufimtse/Dynamic+Media+Viewers+integration+with+Adobe+Launch#DynamicMediaViewersintegrationwithAdobeLaunch-TrackingDynamicMediaViewersusingEmbedcode)사용하여 Dynamic Media 뷰어 추적 정보를 참조하십시오.

## 통합에서 데이터 및 이벤트 추적 작동 방식 {#how-data-and-event-tracking-works-in-the-integration}

통합은 두 가지 개별 및 독립적인 다이내믹 미디어 뷰어 추적 유형을 활용합니다.Adobe *Analytics* 및 *Adobe Analytics for Audio and Video*.

### Adobe Analytics를 사용한 추적 정보 {#about-tracking-using-adobe-analytics}

Adobe Analytics를 사용하면 최종 사용자가 웹 사이트에서 Dynamic Media Viewer와 상호 작용할 때 수행되는 동작을 추적할 수 있습니다. 또한 Adobe Analytics를 사용하여 뷰어별 데이터를 추적할 수 있습니다. 예를 들어 자산 이름, 발생한 모든 확대/축소 작업, 비디오 재생 작업 등과 함께 보기 로드 이벤트를 추적하고 기록할 수 있습니다.

Adobe Launch에서 데이터 요소 및 *규칙* 개념은 *함께* Adobe Analytics 추적을 활성화합니다.

#### Adobe Launch의 데이터 요소 정보 {#about-data-elements-in-adobe-launch}

Adobe Launch의 데이터 요소는 값이 정적으로 정의되거나 웹 페이지 또는 다이내믹 미디어 뷰어 데이터의 상태에 따라 동적으로 계산되는 명명된 속성입니다.

데이터 요소 정의에 사용할 수 있는 옵션은 Adobe Launch 속성에 설치된 확장 목록에 따라 다릅니다. &quot;코어&quot; 익스텐션은 사전 설치되어 있으며 모든 구성에서 즉시 사용할 수 있습니다. 이 &quot;코어&quot; 익스텐션을 사용하면 쿠키, JavaScript 코드, 쿼리 문자열 및 기타 많은 소스에서 나오는 데이터 요소를 정의할 수 있습니다.

Adobe Analytics를 추적하려면 익스텐션 설치 및 설정에 설명된 대로 몇 가지 추가 [익스텐션을](#installing-and-setup-of-extensions)설치해야 합니다. Dynamic Media Viewers 익스텐션은 Dynamic Viewer 이벤트의 인수인 데이터 요소를 정의하는 기능을 추가합니다. 예를 들어, 뷰어가 로드 시 보고한 뷰어 유형 또는 자산 이름, 최종 사용자가 확대/축소할 때 보고되는 확대/축소 수준 등을 참조할 수 있습니다.

Dynamic Media Viewer 확장은 자동으로 데이터 요소의 값을 최신 상태로 유지합니다.

데이터 요소를 정의한 후에는 데이터 요소 선택기 위젯을 사용하여 Adobe Launch UI의 다른 위치에서 데이터 요소를 사용할 수 있습니다. 특히, 다이내믹 미디어 뷰어 추적의 목적으로 정의된 데이터 요소는 규칙의 Adobe Analytics 확장 프로그램의 변수 설정 동작에서 참조됩니다(아래 참조).

자세한 [내용은 Experience Platform](https://docs.adobe.com/content/help/en/launch/using/reference/manage-resources/data-elements.html) 시작 사용 안내서의 데이터 요소를 참조하십시오.

#### Adobe Launch의 규칙 정보 {#about-rules-in-adobe-launch}

Adobe Launch의 규칙은 규칙을 구성하는 다음 세 가지 영역을 정의하는 독립적인 구성입니다.이벤트 *,*&#x200B;조건 *및*&#x200B;작업 **:

* *이벤트* (if)는 Adobe Launch에 규칙을 트리거할 시기를 알려줍니다.
* *조건* (if)은 규칙을 트리거할 때 허용하거나 허용하지 않을 추가 제한 사항을 Adobe Launch에 알립니다.
* *작업* (그런 다음) 규칙이 트리거될 때 수행할 작업을 Adobe Launch에 알려줍니다.

이벤트, 조건 및 작업 섹션에서 사용할 수 있는 옵션은 Adobe Launch 속성에 설치된 확장 프로그램에 따라 다릅니다. Core *익스텐션은* 사전 설치되어 있으며 모든 구성에서 즉시 사용할 수 있습니다. 익스텐션은 포커스 변경, 키 누르기, 양식 제출 등을 포함하는 기본적인 브라우저 수준 작업과 같은 이벤트에 대한 여러 옵션을 제공합니다. 또한 쿠키 값, 브라우저 유형 등과 같은 조건에 대한 옵션도 포함되어 있습니다. 작업의 경우 사용자 지정 코드 옵션만 사용할 수 있습니다.

Adobe Analytics 추적을 수행하려면 확장 설치 및 설정에 설명된 대로 몇 가지 추가 [익스텐션이](#installing-and-setup-of-extensions)설치되어 있어야 합니다. 구체적으로:

* Dynamic Media Viewers 익스텐션은 지원되는 이벤트 목록을 뷰어 로드, 에셋 교체, 확대 및 비디오 재생과 같은 Dynamic Media 뷰어별 이벤트로 확장합니다.
* Adobe Analytics 확장 기능은 추적 서버로 데이터를 전송하는 데 필요한 두 가지 작업으로 지원되는 작업 목록을 확장합니다.변수 *설정* 및 *보내기 비콘*.

Dynamic Media 뷰어를 추적하려면 다음과 같은 유형을 사용할 수 있습니다.

* Dynamic Media Viewers 확장, 코어 확장 또는 기타 확장 프로그램의 이벤트입니다.
* 규칙 정의의 조건. 또는 조건 영역을 비워 둘 수 있습니다.

작업 섹션에서 변수 설정 *작업이 필요합니다* . 이 작업은 Adobe Analytics에서 추적 변수를 데이터로 채우는 방법을 알려줍니다. 동시에 변수 설정 *작업은* 추적 서버로 아무 것도 전송하지 않습니다.

변수 *설정* 작업 뒤에 비콘 보내기 *작업이* 와야 합니다. 비콘 *보내기* 작업은 실제로 데이터를 분석 추적 서버로 보냅니다. 변수 *설정* 및 *비콘*&#x200B;전송은 모두 Adobe Analytics 익스텐션에서 가져옵니다.

자세한 [내용은](https://docs.adobe.com/content/help/en/launch/using/reference/manage-resources/rules.html) Experience Platform 시작 사용 안내서의 규칙을 참조하십시오.

#### 샘플 구성 {#sample-configuration}

Adobe Launch 내의 다음 샘플 구성은 뷰어 로드 시 자산 이름을 추적하는 방법을 보여줍니다.

1. 데이터 **[!UICONTROL 요소]** 탭에서 다이내믹 미디어 뷰어 `AssetName` 확장의 이벤트 매개 변수를 참조하는 데이터 요소를 `asset` `LOAD` 정의합니다.

   ![image2019-11](assets/image2019-11.png)

1. 규칙 **[!UICONTROL 탭에서]** 규칙 TrackAssetOnLoad를 *정의합니다*.

   이 규칙에서 이벤트 **[!UICONTROL 필드는]** 다이내믹 미디어 뷰어 **[!UICONTROL 확장의]** LOAD 이벤트를 사용합니다.

   ![image2019-22](assets/image2019-22.png)

1. 작업 구성에는 Adobe Analytics 확장 프로그램의 두 가지 작업 유형이 있습니다.

   *선택한*&#x200B;분석 변수를 데이터 요소 값에 매핑하는 변수를 `AssetName` 설정합니다.

   *추적 정보를* Adobe Analytics로 보내는 비콘 전송.

   ![image2019-3](assets/image2019-3.png)

1. 결과 규칙 구성은 다음과 같습니다.

   ![image2019-4](assets/image2019-4.png)

### 오디오 및 비디오용 Adobe Analytics 정보 {#about-adobe-analytics-for-audio-and-video}

Experience Cloud 계정이 오디오 및 비디오용 Adobe Analytics를 사용하도록 구독되면 Dynamic Media 뷰어 *확장 설정에서 비디오 추적을 활성화하기에 충분합니다* . 비디오 지표는 Adobe Analytics에서 사용할 수 있게 됩니다. 비디오 추적은 Adobe Media Analytics for Audio 및 Video 익스텐션에 따라 달라집니다.

확장 [설치 및 설정을 참조하십시오](#installing-and-setup-of-extensions).

현재 비디오 추적에 대한 지원은 추적 개요에 설명된 바와 같이 &quot;핵심 재생&quot; 추적으로만 [제한됩니다](https://docs.adobe.com/content/help/en/media-analytics/using/sdk-implement/track-av-playback/track-core-overview.html). 특히 QoS, 광고, 장/세그먼트 또는 오류 추적은 지원되지 않습니다.

## Dynamic Media 뷰어 확장 사용 {#using-the-dynamic-media-viewers-extension}

통합에 [대한 사용 사례에서](#use-cases-for-the-integration)언급했듯이 AEM Sites의 새로운 Adobe Launch 통합과 포함 코드를 사용하여 Dynamic Media 뷰어를 추적할 수 있습니다.

### AEM Sites의 Dynamic Media 뷰어 추적 {#tracking-dynamic-media-viewers-in-aem-sites}

AEM Sites에서 Dynamic Media 뷰어를 추적하려면 모든 [통합 조각](#configuring-all-the-integration-pieces) 구성 섹션에 나열된 모든 단계를 수행해야 합니다. 특히 IMS 구성과 Adobe Launch Cloud 구성을 만들어야 합니다.

적절한 구성을 따르면, Dynamic Media에서 지원하는 WCM 구성 요소를 사용하여 사이트 페이지에 추가하는 모든 Dynamic Media 뷰어는 Adobe Analytics 또는 비디오용 Adobe Analytics에 자동으로 데이터를 추적하거나 둘 다에 데이터를 추적합니다.

Adobe [Sites를 사용하여 페이지에 Dynamic Media 자산 추가를 참조하십시오](/help/assets/dynamic-media/adding-dynamic-media-assets-to-pages.md).

### 포함 코드를 사용하여 Dynamic Media 뷰어 추적 {#tracking-dynamic-media-viewers-using-embed-code}

AEM Sites를 사용하지 않거나 AEM Sites 외부의 웹 페이지에 Dynamic Media 뷰어를 포함시키지 않는 고객 또는 둘 다 Adobe Launch 통합을 계속 사용할 수 있습니다.

Adobe Analytics 구성 및 Adobe [Launch 구성](#configuring-adobe-analytics-for-the-integration) 섹션에서 구성 [단계를 완료해야](#configuring-adobe-launch-for-the-integration) 합니다. 그러나 AEM 관련 구성 단계는 필요하지 않습니다.

적절한 구성을 따라 Dynamic Media 뷰어를 사용하여 웹 페이지에 Adobe Launch 지원을 추가할 수 있습니다.

Adobe [Launch](https://docs.adobe.com/content/help/en/launch/using/implement/configure/implement-the-launch-install-code.html) 라이브러리 포함 코드 사용 방법에 대한 자세한 내용은 론치 포함 코드 추가를 참조하십시오.

AEM [Dynamic Media의 포함 코드 기능을 사용하는](/help/assets/dynamic-media/embed-code.md) 방법에 대한 자세한 내용은 웹 페이지에 비디오 또는 이미지 뷰어 포함을 참조하십시오.

**포함 코드를 사용하여 Dynamic Media 뷰어를 추적하려면**

1. Dynamic Media 뷰어를 포함할 웹 페이지를 준비하십시오.
1. Adobe Launch에 먼저 로그인하여 Adobe Launch 라이브러리에 대한 포함 코드를 얻습니다(Adobe Launch [구성 참조](#configuring-adobe-launch-for-the-integration)).
1. 속성을 **[!UICONTROL 클릭한]**&#x200B;다음 환경 **[!UICONTROL 탭을]** 클릭합니다.
1. 웹 페이지의 환경과 관련된 환경 수준을 선택합니다. 그런 다음 설치 **[!UICONTROL 열에서]** 상자 아이콘을 클릭합니다.
1. **[!UICONTROL 웹 설치 지침]** 대화 상자에서 전체 Adobe Launch 라이브러리 임베드 코드를 주변 `<script/>` 태그와 함께 복사합니다.

## Dynamic Media 뷰어 확장 참조 안내서 {#reference-guide-for-the-dynamic-media-viewers-extension}

### Dynamic Media 뷰어 구성 정보 {#about-the-dynamic-media-viewers-configuration}

Dynamic Media Viewer 익스텐션은 아래 조건이 모두 충족되는 경우 Adobe Launch 라이브러리와 자동으로 통합됩니다.

* Adobe Launch 라이브러리 전역 개체( `_satellite`)가 페이지에 있습니다.
* Dynamic Media Viewers 확장 기능은 에서 `_dmviewers_v001()` 정의됩니다 `_satellite`.

* `config2=` 뷰어 매개 변수가 지정되지 않았습니다. 즉, 뷰어는 레거시 Analytics 통합을 사용하지 않습니다.

또한 뷰어의 구성에서 매개 변수를 지정하여 뷰어에서 Adobe Launch 통합을 명시적으로 비활성화할 수 있는 옵션이 `launch=0` 있습니다. 이 매개 변수의 기본값은 `1`입니다.

### Dynamic Media 뷰어 확장 구성 {#configuring-the-dynamic-media-viewers-extension}

다이내믹 미디어 뷰어 확장의 유일한 구성 옵션은 오디오 및 비디오용 **[!UICONTROL Adobe Media Analytics 활성화입니다]**.

이 옵션을 선택(활성화 또는 &quot;켜기&quot;)하고 Adobe Media Analytics for Audio 및 Video 익스텐션이 설치 및 올바르게 구성된 경우 비디오 재생 지표가 Adobe Analytics for Audio 및 Video 솔루션으로 전송됩니다. 이 옵션을 비활성화하면 비디오 추적이 꺼집니다.

Adobe Media Analytics for Audio 및 Video 익스텐션을 설치하지 *않고* 이 옵션을 활성화하면 옵션이 적용되지 않습니다.

![image2019-7-22_12-4-23](assets/image2019-7-22_12-4-23.png)

### 다이내믹 미디어 뷰어 확장의 데이터 요소 정보 {#about-data-elements-in-the-dynamic-media-viewers-extension}

Dynamic Media Viewers 확장에서 제공하는 데이터 요소 유형은 데이터 요소 **[!UICONTROL 유형]** 드롭다운 **[!UICONTROL 목록의 뷰어]** 이벤트뿐입니다.

이 옵션을 선택하면 데이터 요소 편집기가 두 개의 필드가 있는 양식을 렌더링합니다.

* **[!UICONTROL DM 뷰어 이벤트 데이터 유형]** - 인수가 있는 Dynamic Media Viewers 익스텐션에서 지원하는 모든 뷰어 이벤트와 특수 COMMON **[!UICONTROL 항목을 식별하는 드롭다운]** 목록입니다. COMMON **[!UICONTROL 항목은]** 뷰어에서 보낸 모든 유형의 이벤트에 공통으로 사용되는 이벤트 매개 변수 목록을 나타냅니다.
* **[!UICONTROL 추적 매개 변수]** - 선택한 Dynamic Media 뷰어 이벤트의 인수입니다.

![image2019-7-22_12-5-46](assets/image2019-7-22_12-5-46.png)

각 뷰어 [유형별로 지원되는 이벤트 목록은 Dynamic Media Viewers 참조 안내서를](https://marketing.adobe.com/resources/help/en_US/s7/viewers_ref/c_html5_s7_aem_asset_viewers.html) 참조하십시오.특정 뷰어 섹션으로 이동한 다음 Adobe Analytics 추적 하위 섹션 지원을 클릭합니다. 현재 Dynamic Media 뷰어 참조 안내서는 이벤트 인수를 문서화하지 않습니다.

이제 다이내믹 미디어 뷰어 데이터 요소의 라이프사이클을 *고려해 보겠습니다*. 이러한 데이터 요소의 값은 페이지에서 해당 Dynamic Media 뷰어 이벤트가 발생한 후에 채워집니다. 예를 들어 데이터 요소가 LOAD **[!UICONTROL 이벤트와 그 &quot;]** asset&quot; 인수를 가리키면 뷰어가 LOAD 이벤트를 처음 실행한 후 해당 데이터 요소의 값이 유효한 데이터를 받게 됩니다. 데이터 요소가 ZOOM 이벤트와 **[!UICONTROL 해당]** &quot;scale&quot; 인수를 가리키면 뷰어가 처음으로 ZOOM **[!UICONTROL 이벤트를 보낼 때까지 해당 데이터 요소의]** 값은 비어있게 됩니다.

마찬가지로 뷰어가 페이지에서 해당 이벤트를 전송하면 데이터 요소 값이 자동으로 업데이트됩니다. 값 업데이트는 특정 이벤트가 규칙 구성에 지정되지 않은 경우에도 발생합니다. 예를 들어 ZOOM **[!UICONTROL 이벤트의 &quot;scale&quot; 매개 변수에 데이터 요소]** ZoomScale이 **[!UICONTROL 정의되지만 규칙 구성에 있는 유일한 규칙은 LOAD 이벤트에 의해 트리거되는]** 경우 사용자가 뷰어 내에서 확대/축소를 **[!UICONTROL 실행할 때마다]** ZoomScale의값이 계속 업데이트됩니다.

모든 Dynamic Media 뷰어는 웹 페이지에 고유한 식별자를 가집니다. 데이터 요소는 값 자체와 값을 채운 뷰어를 추적합니다. 즉, 동일한 페이지에 여러 명의 뷰어가 있고 LOAD **[!UICONTROL 이벤트]** 및 그 &quot;자산&quot; 인수를 가리키는 AssetName **[!UICONTROL 데이터 요소가]** 있는 경우 **[!UICONTROL AssetName 데이터 요소는 페이지에서 로드된 각 뷰어와]** 연결된 에셋 이름 컬렉션을유지합니다.

데이터 요소에서 반환하는 정확한 값은 컨텍스트에 따라 다릅니다. Dynamic Media 뷰어 이벤트에 의해 트리거된 규칙에서 데이터 요소가 요청되면 규칙을 시작한 뷰어에 대해 데이터 요소 값이 반환됩니다. 그리고, 데이터 요소가 다른 Adobe Launch 확장의 이벤트에 의해 트리거된 규칙에서 요청되는 경우 데이터 요소의 값은 이 데이터 요소를 마지막으로 업데이트한 뷰어의 값입니다.

**다음 샘플 설정을**&#x200B;고려하십시오.

* 두 개의 Dynamic Media 확대/축소 뷰어가 있는 웹 페이지;viewer1 *및* viewer2로 **&#x200B;참조할 것입니다.

* **[!UICONTROL ZoomScale]** 데이터 요소는 ZOOM **[!UICONTROL 이벤트와 그 &quot;]** scale&quot; 인수를 가리킵니다.
* **[!UICONTROL TrackPan]** 규칙(다음 포함):

   * Dynamic Media Viewer PAN **[!UICONTROL 이벤트를]** 트리거로 사용합니다.
   * ZoomScale 데이터 **[!UICONTROL 요소의 값을]** Adobe Analytics로 전송합니다.

* 
   * **[!UICONTROL TrackKey]** 규칙(다음 포함):

   * 코어 Adobe Launch 확장의 키 누르기 이벤트를 트리거로 사용합니다.
   * ZoomScale 데이터 **[!UICONTROL 요소의 값을]** Adobe Analytics로 전송합니다.

이제 최종 사용자가 두 뷰어와 함께 웹 페이지를 로드한다고 가정합니다. Viewer1 *에서* 50% 크기로 확대됩니다.그런 다음 *viewer2에서* 25% 크기로 확대됩니다. viewer1 *에서*&#x200B;이미지를 이동시키고 마지막으로 키보드의 키를 누릅니다.

최종 사용자의 활동이 Adobe Analytics에 대해 수행되는 추적 호출의 결과는 다음과 같습니다.

* 첫 번째 호출은 사용자가 **[!UICONTROL viewer1에서]** 이동할 때 TrackPan *규칙이 트리거되기 때문에 발생합니다*. 데이터 요소는 규칙이 **[!UICONTROL viewer1에]** 의해 트리거되었음을 알고 해당 비율 ** 값을 가져오기 때문에 이 호출은 ZoomScale 데이터 요소의 값으로 50%를 전송합니다.
* 두 번째 호출은 사용자가 **[!UICONTROL 키보드에서]** 키를 눌렀을 때 TrackKey 규칙이 트리거되기 때문에 발생합니다. 규칙이 뷰어에 의해 트리거되지 않았기 때문에 **[!UICONTROL 이]** 호출은 ZoomScale 데이터 요소의 값으로 25%를 전송합니다. 따라서 데이터 요소는 최신 값을 반환합니다.

위에 설정된 샘플 세트는 데이터 요소 값의 수명 또한 영향을 줍니다. Dynamic Media Viewer에서 관리하는 데이터 요소의 값은 뷰어 자체가 웹 페이지에서 삭제된 후에도 Adobe Launch 라이브러리 코드에 저장됩니다. 즉, 비 Dynamic Media Viewer 확장 프로그램에서 트리거되는 규칙이 있고 이러한 데이터 요소를 참조하는 경우 뷰어가 더 이상 웹 페이지에 없더라도 데이터 요소는 마지막으로 알려진 값을 반환합니다.

어떤 경우든, Dynamic Media 뷰어를 기반으로 하는 데이터 요소의 값은 로컬 저장소 또는 서버에 저장되지 않습니다.대신 클라이언트측 Adobe Launch 라이브러리에만 보관됩니다. 이러한 데이터 요소의 값은 웹 페이지가 다시 로드되면 사라집니다.

일반적으로 데이터 요소 편집기는 [저장소 기간 선택을](https://docs.adobe.com/content/help/en/launch/using/reference/manage-resources/data-elements.html#create-a-data-element)지원합니다. 그러나 Dynamic Media Viewers 확장 기능을 사용하는 데이터 요소는 [없음]의 저장 기간 옵션만 **[!UICONTROL 지원합니다]**. 사용자 인터페이스에서 다른 값을 설정할 수 있지만 이 경우에는 데이터 요소 동작이 정의되지 않습니다. 확장자는 데이터 요소의 값을 직접 관리합니다.전체 뷰어 수명 주기 동안 뷰어 이벤트 인수의 값을 유지하는 데이터 요소입니다.

### 다이내믹 미디어 뷰어 확장의 규칙 정보 {#about-rules-in-the-dynamic-media-viewers-extension}

규칙 편집기에서 확장 프로그램은 이벤트 편집기에 대한 새 구성 옵션을 추가합니다. 또한 에서는 미리 구성된 데이터 요소를 사용하는 대신 작업 편집기에서 이벤트 매개 변수를 간단한 옵션으로 수동으로 참조하는 옵션을 제공합니다.

#### 이벤트 편집기 정보 {#about-the-events-editor}

이벤트 편집기에서 다이내믹 미디어 뷰어 익스텐션은 뷰어 이벤트라는 새 **[!UICONTROL 이벤트]** 유형을 **[!UICONTROL 추가합니다]**.

이 옵션을 선택하면 이벤트 편집기가 드롭다운 **[!UICONTROL Dynamic Media 뷰어 이벤트를]**&#x200B;렌더링하여 Dynamic Media 뷰어에서 지원하는 사용 가능한 모든 이벤트를 나열합니다.

![image2019-8-2_15-13-1](assets/image2019-8-2_15-13-1.png)

#### 작업 편집기 정보 {#about-the-actions-editor}

다이내믹 미디어 뷰어 익스텐션을 사용하면 다이내믹 미디어 뷰어의 이벤트 매개 변수를 사용하여 Adobe Analytics 확장의 변수 설정 편집기에 있는 분석 변수에 매핑할 수 있습니다.

이를 위한 가장 간단한 방법은 다음 2단계 프로세스를 완료하는 것입니다.

* 먼저 하나 이상의 데이터 요소를 정의합니다. 여기서 각 데이터 요소는 다이내믹 미디어 뷰어 이벤트의 매개 변수를 나타냅니다.
* 마지막으로, Adobe Analytics 확장의 변수 설정 편집기에서 데이터 요소 선택기 아이콘(세 개의 누적 디스크)을 클릭하여 데이터 요소 선택 대화 상자를 연 다음 데이터 요소에서 데이터 요소를 선택합니다.

![image2019-7-10_20-41-52](assets/image2019-7-10_20-41-52.png)

그러나 대체 방법을 사용하고 데이터 요소 생성을 무시할 수 있습니다. 퍼센트(%) 기호로 둘러싸인 Analytics 변수 할당의 **[!UICONTROL 값]** 입력 필드에 이벤트 인수의 정규화된 이름을 입력하여 Dynamic Media Viewer 이벤트의 인수를 직접 참조할 수 있습니다. 예,

`%event.detail.dm.LOAD.asset%`

![image2019-7-12_19-2-35](assets/image2019-7-12_19-2-35.png)

데이터 요소 사용과 직접 이벤트 인수 참조 간에는 중요한 차이가 있습니다. 데이터 요소의 경우, 변수 설정 작업을 트리거하는 이벤트가 중요하지 않으며, 규칙을 트리거하는 이벤트는 Dynamic Viewer와 관련되지 않을 수 있습니다(예: 코어 확장의 웹 페이지에서 마우스 클릭처럼). 그러나 직접 인수를 사용할 때는 규칙을 트리거하는 이벤트가 참조하는 이벤트 인수와 일치하는지 확인해야 합니다.

예를 들어, Dynamic Media Viewer 확장의 LOAD 이벤트에 의해 규칙이 트리거되는 `%event.detail.dm.LOAD.asset%` 경우 **** 참조는 올바른 자산 이름을 반환합니다. 그러나 다른 이벤트에 대해 빈 값을 반환합니다.

다음 표에는 Dynamic Media Viewer 이벤트와 지원되는 인수가 나와 있습니다.

<table>
 <tbody>
  <tr>
   <td>뷰어 이벤트 이름</td>
   <td>인수 참조</td>
  </tr>
  <tr>
   <td><code>COMMON</code></td>
   <td><code>%event.detail.dm.objID%</code></td>
  </tr>
  <tr>
   <td> </td>
   <td><code>%event.detail.dm.compClass%</code></td>
  </tr>
  <tr>
   <td> </td>
   <td><code>%event.detail.dm.instName%</code></td>
  </tr>
  <tr>
   <td> </td>
   <td><code>%event.detail.dm.timeStamp%</code></td>
  </tr>
  <tr>
   <td><code>BANNER</code> </td>
   <td><code>%event.detail.dm.BANNER.asset%</code></td>
  </tr>
  <tr>
   <td> </td>
   <td><code>%event.detail.dm.BANNER.frame%</code></td>
  </tr>
  <tr>
   <td> </td>
   <td><code>%event.detail.dm.BANNER.label%</code></td>
  </tr>
  <tr>
   <td><code>HREF</code></td>
   <td><code>%event.detail.dm.HREF.rollover%</code></td>
  </tr>
  <tr>
   <td><code>ITEM</code></td>
   <td><code>%event.detail.dm.ITEM.rollover%</code></td>
  </tr>
  <tr>
   <td><code>LOAD</code></td>
   <td><code>%event.detail.dm.LOAD.applicationname%</code></td>
  </tr>
  <tr>
   <td><strong> </strong></td>
   <td><code>%event.detail.dm.LOAD.asset%</code></td>
  </tr>
  <tr>
   <td><strong> </strong></td>
   <td><code>%event.detail.dm.LOAD.company%</code></td>
  </tr>
  <tr>
   <td><strong> </strong></td>
   <td><code>%event.detail.dm.LOAD.sdkversion%</code></td>
  </tr>
  <tr>
   <td><strong> </strong></td>
   <td><code>%event.detail.dm.LOAD.viewertype%</code></td>
  </tr>
  <tr>
   <td><strong> </strong></td>
   <td><code>%event.detail.dm.LOAD.viewerversion%</code></td>
  </tr>
  <tr>
   <td><code>METADATA</code></td>
   <td><code>%event.detail.dm.METADATA.length%</code></td>
  </tr>
  <tr>
   <td> </td>
   <td><code>%event.detail.dm.METADATA.type%</code></td>
  </tr>
  <tr>
   <td><code>MILESTONE</code></td>
   <td><code>%event.detail.dm.MILESTONE.milestone%</code></td>
  </tr>
  <tr>
   <td><code>PAGE</code></td>
   <td><code>%event.detail.dm.PAGE.frame%</code></td>
  </tr>
  <tr>
   <td> </td>
   <td><code>%event.detail.dm.PAGE.label%</code></td>
  </tr>
  <tr>
   <td><code>PAUSE</code></td>
   <td><code>%event.detail.dm.PAUSE.timestamp%</code></td>
  </tr>
  <tr>
   <td><code>PLAY</code></td>
   <td><code>%event.detail.dm.PLAY.timestamp%</code></td>
  </tr>
  <tr>
   <td><code>SPIN</code></td>
   <td><code>%event.detail.dm.SPIN.framenumber%</code></td>
  </tr>
  <tr>
   <td><code>STOP</code></td>
   <td><code>%event.detail.dm.STOP.timestamp%</code></td>
  </tr>
  <tr>
   <td><code>SWAP</code></td>
   <td><code>%event.detail.dm.SWAP.asset%</code></td>
  </tr>
  <tr>
   <td><code>SWATCH</code></td>
   <td><code>%event.detail.dm.SWATCH.frame%</code></td>
  </tr>
  <tr>
   <td> </td>
   <td><code>%event.detail.dm.SWATCH.label%</code></td>
  </tr>
  <tr>
   <td><code>TARG</code></td>
   <td><code>%event.detail.dm.TARG.frame%</code></td>
  </tr>
  <tr>
   <td> </td>
   <td><code>%event.detail.dm.TARG.label%</code></td>
  </tr>
  <tr>
   <td><code>ZOOM</code></td>
   <td><code>%event.detail.dm.ZOOM.scale%</code></td>
  </tr>
 </tbody>
</table>

## 모든 통합 부분 구성 {#configuring-all-the-integration-pieces}

**시작하기 전에**

아직 완료하지 않은 경우, Adobe에서는 이 섹션 이전에 모든 설명서를 철저히 검토하여 통합 내용을 파악할 것을 권장합니다.

이 섹션에서는 Dynamic Media 뷰어를 Adobe Analytics 및 오디오 및 비디오용 Adobe Analytics와 통합하는 데 필요한 구성 단계를 설명합니다. Adobe Launch에서 다른 목적으로 Dynamic Media Viewers 익스텐션을 사용할 수 있지만, 이러한 시나리오는 이 설명서에서 다루지 않습니다.

다음 Adobe 제품에서 통합을 구성합니다.

* Adobe Analytics - 추적 변수 및 보고서를 구성합니다.
* Adobe Launch - 속성, 하나 이상의 규칙 및 하나 이상의 데이터 요소를 정의하여 뷰어 추적을 활성화합니다.

또한 이 통합 솔루션이 AEM Sites와 함께 사용되는 경우 다음 구성도 수행해야 합니다.

* Adobe I/O 콘솔 - Adobe Launch에 대한 통합이 생성됩니다.
* AEM 작성자 노드 - IMS 구성 및 Adobe Launch 클라우드 구성

구성의 일부로 Adobe Analytics 및 Adobe Launch가 이미 활성화된 Adobe Experience Cloud의 회사에 액세스할 수 있는지 확인하십시오.

## 통합을 위한 Adobe Analytics 구성 {#configuring-adobe-analytics-for-the-integration}

Adobe Analytics를 구성한 후 통합에 대해 다음 사항이 설정됩니다.

* 보고서 세트가 제자리에 있고 선택됩니다.
* Analytics 변수를 사용하여 추적 데이터를 수신할 수 있습니다.
* 보고서는 Adobe Analytics 내에서 수집된 데이터를 보는 데 사용할 수 있습니다.

Analytics [구현 안내서를 참조하십시오](https://docs.adobe.com/content/help/en/analytics/implementation/home.html).

**통합을**&#x200B;위해 Adobe Analytics를 구성하려면:

1. 먼저 Experience Cloud [홈 페이지에서](https://exc-home.experiencecloud.adobe.com/exc-home/home.html#/)Adobe Analytics에 액세스하십시오. 메뉴 모음에서 페이지의 오른쪽 위 모서리 근처에 있는 솔루션 아이콘(3 x 3 점 표)을 클릭한 다음 Analytics를 **[!UICONTROL 클릭합니다]**.

   ![2019-07-22_18-08-47](assets/2019-07-22_18-08-47.png)

   이제 보고서 세트를 선택합니다.

### 보고서 세트 선택 {#selecting-a-report-suite}

1. Adobe Analytics 페이지의 오른쪽 위 모서리, 검색 보고서 **[!UICONTROL 필드]** 오른쪽의 드롭다운 목록에서 올바른 보고서 세트를 선택합니다. 사용할 수 있는 보고서 세트가 여러 개 있고 사용할 보고서 세트가 확실하지 않은 경우 사용할 보고서 세트를 선택하는 데 도움이 되는 Adobe Analytics 관리자에게 문의하십시오.

   아래 그림에서 사용자가 DynamicMediaViewersExtensionDoc라는 *보고서* 세트를 만들어 드롭다운 목록에서 선택했습니다. 보고서 세트 이름은 일러스트레이션 용도로만 사용됩니다.최종적으로 선택하는 보고서 세트의 이름은 달라집니다.

   사용할 수 있는 보고서 세트가 없는 경우, 사용자나 Adobe Analytics 관리자가 보고서 세트를 먼저 만들어야 구성을 계속 진행할 수 있습니다.

   보고서 [및 보고서 세트](https://docs.adobe.com/content/help/en/analytics/implementation/analytics-basics/ref-reports-report-suites.html) 및 [보고서 세트](https://docs.adobe.com/content/help/en/analytics/admin/admin-console/create-report-suite.html)만들기를 참조하십시오.

   Adobe Analytics에서 보고서 세트는 관리 > 보고서 **[!UICONTROL 세트에서 관리됩니다]**.

   ![2019-07-22_18-09-49](assets/2019-07-22_18-09-49.png)

   이제 Adobe Analytics 변수를 설정합니다.

### Adobe Analytics 변수 설정 {#setting-up-adobe-analytics-variables}

1. 이제 웹 페이지에서 Dynamic Media 뷰어 동작을 추적하는 데 사용할 Adobe Analytics 변수를 하나 이상 지정합니다.

   Adobe Analytics에서 지원하는 모든 유형의 변수를 사용할 수 있습니다. 변수 유형(사용자 지정 트래픽 [prop], 전환 eVar 등)에 대한 결정은 [Analytics]구현의 특정 요구 사항에 의해 결정되어야 합니다.

   prop [및 eVar 개요를 참조하십시오](https://docs.adobe.com/content/help/en/analytics/implementation/analytics-basics/traffic-props-evars/props-evars.html).

   이 문서의 목적을 위해, 웹 페이지에서 작업이 발생한 후 몇 분 이내에 Analytics 보고서에서 사용할 수 있게 되므로 사용자 지정 트래픽(prop) 변수만 사용됩니다.

   새 사용자 지정 트래픽 변수를 활성화하려면 Adobe Analytics의 도구 모음에서 관리 **[!UICONTROL > 보고서 세트를 클릭합니다]**.

1. 보고서 **[!UICONTROL 세트 관리자]** 페이지에서 올바른 보고서를 선택한 다음 도구 모음에서 설정 편집 > 트래픽 **[!UICONTROL > 트래픽 변수를 클릭합니다]**.
1. 여기에서 사용하지 않은 변수를 선택하고, 보기 자산(prop 30) **[!UICONTROL 을]**&#x200B;설명형 이름으로 지정하고, 활성화 열에서 콤보 상자를 &quot;사용&quot;으로 변경합니다.

   다음 스크린샷은 뷰어에서 사용하는 자산 이름을 추적하는 사용자 지정 트래픽 변수( **[!UICONTROL prop]** 30)의 예입니다.

   ![image2019-6-26_23-6-59](/help/assets/dynamic-media/assets/image2019-6-26_23-6-59.png)

1. 변수 목록 하단에서 저장을 **[!UICONTROL 클릭합니다]**.

### 보고서 설정 {#setting-up-a-report}

1. 일반적으로 Adobe Analytics에서 보고서를 설정하는 것은 특정 프로젝트 요구 사항에 의해 수행됩니다. 따라서 세부 보고서 설정은 이 통합의 범위를 벗어납니다.

   그러나 Adobe Analytics 변수 설정에서 사용자 지정 트래픽 변수를 설정한 후 Adobe Analytics에서 사용자 지정 트래픽 보고서를 자동으로 사용할 **[수 있게 되는 것을 알기에 충분합니다](#setting-up-adobe-analytics-variables)**.

   예를 들어 뷰어 자산(prop 30) **[!UICONTROL 에 대한]** 보고서는 사용자 지정 트래픽 > 사용자 지정 트래픽 21-30 > 뷰어 **[!UICONTROL 자산(prop 30)]**&#x200B;아래의 보고서 메뉴에서 사용할 수 있습니다.

   뷰어 자산(prop 30) **** 작성 후 바로 이 보고서를 방문하면 데이터가 표시되지 않습니다.이 경우 통합에서 필요합니다.

   ![image2019-6-26_23-12-49](/help/assets/dynamic-media/assets/image2019-6-26_23-12-49.png)

## 통합을 위해 Adobe Launch 구성 {#configuring-adobe-launch-for-the-integration}

Adobe Launch를 구성한 후 통합에 대해 다음 사항이 설정됩니다.

* 모든 구성을 함께 유지할 새 속성을 만듭니다.
* 익스텐션의 설치 및 설정 속성에 설치된 모든 익스텐션의 클라이언트측 코드는 라이브러리로 컴파일됩니다. 이 라이브러리는 나중에 웹 페이지에서 사용됩니다.
* 데이터 요소 및 규칙 구성을 참조하십시오. 이 구성은 Dynamic Media 뷰어에서 캡처할 데이터, 추적 로직을 트리거할 시기 및 Adobe Analytics에서 뷰어 데이터를 보낼 위치를 정의합니다.
* 라이브러리 게시.

**통합을**&#x200B;위해 Adobe Launch를 구성하려면:

1. 먼저 Experience Cloud [홈 페이지에서](https://exc-home.experiencecloud.adobe.com/exc-home/home.html#/)Adobe Launch에 액세스합니다. 메뉴 모음에서 페이지의 오른쪽 위 모서리 근처에 있는 솔루션 아이콘(세 개 점 표)을 클릭한 다음 시작을 **[!UICONTROL 클릭합니다]**.

   Adobe Launch를 직접 [열 수도 있습니다](https://launch.adobe.com/).

   ![image2019-7-8_15-38-44](assets/image2019-7-8_15-38-44.png)

### Adobe Launch에서 속성 만들기 {#creating-a-property-in-adobe-launch}

Adobe Launch의 속성은 모든 설정을 함께 유지하는 명명된 구성입니다. 구성 설정의 라이브러리가 생성되고 다른 환경 수준(개발, 스테이징 및 프로덕션)에 게시됩니다.

속성 [만들기를 참조하십시오](https://docs.adobe.com/content/help/en/launch/using/implement/configure/create-a-property.html).

1. Adobe Launch에서 새 **[!UICONTROL 속성을 클릭합니다]**.
1. 속성 **[!UICONTROL 만들기]** 대화 상자의 이름 **[!UICONTROL 필드에]** 웹 사이트의 제목과 같은 수사적 이름을 입력합니다. 예, `DynamicMediaViewersProp.`
1. 도메인 **[!UICONTROL 필드에]** 웹 사이트의 도메인을 입력합니다.
1. 고급 **[!UICONTROL 옵션]** 드롭다운에서 **[!UICONTROL 사용하려는 확장 프로그램(이 경우 Dynamic Media Viewers)]** 이 *아직 릴리스되지 않은 경우 익스텐션 개발을 위해 구성을 활성화합니다*.

   ![image2019-7-8_16-3-47](assets/image2019-7-8_16-3-47.png)

1. **[!UICONTROL 저장]**&#x200B;을 클릭합니다.

   새로 만든 속성을 클릭한 다음 Extension *설치 및*&#x200B;설정으로 진행합니다.

### 확장 기능 설치 및 설정 {#installing-and-setup-of-extensions}

Adobe Launch에서 사용할 수 있는 모든 익스텐션이 확장 > **[!UICONTROL 카탈로그 아래에 나열됩니다]**.

확장을 설치하려면 [설치]를 **[!UICONTROL 클릭합니다]**. 필요한 경우 일회성 확장 구성을 수행한 다음 저장을 **[!UICONTROL 클릭합니다]**.

필요한 경우 다음 익스텐션을 설치하고 구성해야 합니다.

* (필수) *Experience Cloud ID 서비스* 확장

추가 구성은 필요하지 않습니다. 제안된 값을 수락하십시오. 완료되면 [저장]을 클릭해야 **[!UICONTROL 합니다]**.

Experience [Cloud ID 서비스 확장을 참조하십시오](https://docs.adobe.com/content/help/en/launch/using/extensions-ref/adobe-extension/id-service-extension/overview.html).

* (필수) *Adobe Analytics* 확장

이 확장을 구성하려면 먼저 Adobe Analytics의 관리 > 보고서 세트 아래의 보고서 세트 **[!UICONTROL ID]**&#x200B;열 **[!UICONTROL 헤더 아래에]** 있는보고서 세트 ID가필요합니다.

(데모용으로만 DynamicMediaViewersExtensionDoc 보고서 **[!UICONTROL 세트의]** 보고서 세트 ID가 다음 스크린샷에서 사용됩니다. 이 ID는 이전에 보고서 세트 [선택에서 만들어](#selecting-a-report-suite) 사용되었습니다.)

![image2019-7-8_16-45-34](assets/image2019-7-8_16-45-34.png)

확장 설치 페이지에서 개발 보고서 세트 **[!UICONTROL 필드, 스테이징 보고서 세트]** 필드 및 **[!UICONTROL 프로덕션 보고서 세트]** **** 필드에 보고서 세트ID를입력합니다.

![image2019-7-8_16-47-40](assets/image2019-7-8_16-47-40.png)

*비디오 추적을 사용하려는 경우에만 다음 항목을 구성합니다.*

확장 **[!UICONTROL 설치]** 페이지에서 일반을 **[!UICONTROL 확장한]**&#x200B;다음 추적 서버를 지정합니다. 추적 서버는 프로비저닝 이메일에서 얻은 `<trackingNamespace>.sc.omtrdc.net`정보를 `<trackingNamespace>` 나타내는 템플릿을 따릅니다.

**[!UICONTROL 저장]**&#x200B;을 클릭합니다.

Adobe [Analytics 확장을 참조하십시오](https://docs.adobe.com/content/help/en/launch/using/extensions-ref/adobe-extension/analytics-extension/overview.html).

* (선택 사항입니다. 비디오 추적이 필요한 경우에만 필요) 오디오 및 *비디오용 Adobe Media Analytics* 확장

추적 서버 필드를 채웁니다. Adobe Media Analytics for *Audio 및 Video* Extension의 추적 서버는 Adobe Analytics에 사용된 추적 서버와 다릅니다. 이 템플릿에는 제공 이메일의 정보가 `<trackingNamespace>.hb.omtrdc.net`포함되어 `<trackingNamespace>` 있는 템플릿이 따릅니다.

다른 모든 필드는 선택 사항입니다.

Adobe [Media Analytics for Audio 및 Video Extension을 참조하십시오](https://docs.adobe.com/content/help/en/launch/using/extensions-ref/adobe-extension/media-analytics-extension/overview.html).

* (필수) *다이내믹 미디어 뷰어* 확장

비디오용 **[!UICONTROL Adobe Analytics]** 활성화를 선택하여 비디오 하트비트 추적을 활성화(켜기)합니다.

이 작성 시 Dynamic Media *Viewers* 익스텐션은 Adobe Launch 속성을 개발용으로 만든 경우에만 사용할 수 있습니다.

Adobe [Launch에서 속성 만들기를 참조하십시오](#creating-a-property-in-adobe-launch).

익스텐션이 설치되고 설정되면 다음의 5개의 익스텐션(비디오를 추적하지 않는 경우 4개)이 [확장] > [설치됨] 영역에 나열됩니다.

![image2019-7-22_12-7-36](assets/image2019-7-22_12-7-36.png)

### 데이터 요소 및 규칙 설정 {#setting-up-data-elements-and-rules}

Adobe Launch에서 Dynamic Media 뷰어 추적에 필요한 데이터 요소 및 규칙을 만듭니다.

Adobe [Launch와의 추적 개요를 보려면 통합에서](#how-data-and-event-tracking-works-in-the-integration) 데이터 및 이벤트 추적이 작동하는 방식을 참조하십시오.

뷰어 [로드 시 자산 이름을 추적하는 방법을 보여주는 Adobe Launch의 샘플 구성에 대한 샘플 구성을](#sample-configuration) 참조하십시오.

익스텐션의 [기능에 대한 자세한 내용은 Dynamic Media Viewers 확장](#configuring-the-dynamic-media-viewers-extension) 구성을 참조하십시오.

### 라이브러리 게시 {#publishing-a-library}

Adobe Launch 구성(속성, 확장, 규칙 및 데이터 요소 설정 포함)을 변경하려면 해당 변경 사항을 *게시해야* 합니다. Adobe Launch에서 게시는 속성 구성 아래의 게시 탭에서 수행됩니다.

Adobe Launch에는 여러 개발 환경, 하나의 스테이징 환경 및 하나의 프로덕션 환경이 있을 수 있습니다. 기본적으로 AEM의 Adobe Launch Cloud 구성은 AEM 작성자 노드를 Adobe Launch의 스테이지 환경으로, AEM 게시 노드를 Adobe Launch의 프로덕션 환경에 가리킵니다. 이 정렬은 기본 AEM 설정에서 Adobe Launch 라이브러리를 스테이징 환경에 게시하여 AEM 작성자에서 사용한 다음 프로덕션 환경에 게시하여 AEM 게시에서 사용할 수 있도록 해야 합니다.

Adobe [Launch](https://docs.adobe.com/content/help/en/launch/using/reference/publish/environments.html) 환경에 대한 자세한 내용은 환경을 참조하십시오.

라이브러리 게시에는 다음 두 단계가 포함됩니다.

* 필요한 모든 변경 사항(새 내용 및 업데이트)을 라이브러리에 포함하여 새 라이브러리를 추가하고 만듭니다.
* 다른 환경 수준(개발에서 스테이징 및 프로덕션으로)을 통해 라이브러리 이동

#### 새 라이브러리 추가 및 작성 {#adding-and-building-a-new-library}

1. Adobe Launch에서 게시 탭을 처음 열면 라이브러리 목록이 비어 있습니다.

   왼쪽 열에서 새 라이브러리 **[!UICONTROL 추가를 클릭합니다]**.

   ![image2019-7-15_14-43-17](assets/image2019-7-15_14-43-17.png)

1. [새 라이브러리 만들기] 페이지의 [ **[!UICONTROL 이름]** ] 필드에 새 라이브러리에 대해 설명하는 이름을 입력합니다. 예,

   *DynamicMediaViewersLib*

   환경 드롭다운 목록에서 환경 수준을 선택합니다. 처음에는 개발 수준만 선택할 수 있습니다. 페이지의 왼쪽 아래에 있는 [변경된 모든 리소스 **[!UICONTROL 추가]를 클릭합니다]**.

   ![image2019-7-15_14-49-41](assets/image2019-7-15_14-49-41.png)

1. 페이지의 오른쪽 위 모서리 근처에 있는 개발용으로 **[!UICONTROL 저장 및 빌드를 클릭합니다]**.

   몇 분 안에 라이브러리가 만들어지고 사용할 준비가 되었습니다.

   ![image2019-7-15_15-3-34](assets/image2019-7-15_15-3-34.png)

   >[!NOTE]
   >
   >다음에 Adobe Launch 구성을 변경할 때 **[!UICONTROL 속성]** 구성 아래의 게시 **[!UICONTROL 탭으로 이동한]** 다음이전에 만든 라이브러리를 클릭합니다.
   >
   >
   >라이브러리 게시 화면에서 변경된 **[!UICONTROL 모든 리소스 추가를]**&#x200B;클릭한 다음 **[!UICONTROL 개발용으로 저장 및 빌드를 클릭합니다]**.

#### 환경 수준에서 라이브러리 이동 {#moving-a-library-up-through-environment-levels}

1. 새 라이브러리가 추가되면 처음에는 개발 환경에 배치됩니다. [제출됨] 열에 해당하는 [스테이징] 환경 수준으로 이동하려면 라이브러리의 드롭다운 메뉴에서 [승인을 위해 **[!UICONTROL 제출]을 클릭합니다]**.

   ![image2019-7-15_15-52-37](assets/image2019-7-15_15-52-37.png)

1. 확인 대화 상자에서 제출을 **[!UICONTROL 클릭합니다]**.

   라이브러리가 [제출됨] 열로 이동한 후 라이브러리의 드롭다운 메뉴에서 [스테이징에 대한 **[!UICONTROL 빌드]를 클릭합니다]**.

   ![image2019-7-15_15-54-37](assets/image2019-7-15_15-54-37.png)

1. 유사한 절차에 따라 라이브러리를 스테이징 환경에서 프로덕션 환경(게시된 열)으로 이동합니다.

   먼저 드롭다운 메뉴에서 게시를 **[!UICONTROL 승인합니다]**.

   ![image2019-7-15_16-7-39](assets/image2019-7-15_16-7-39.png)

1. 드롭다운 메뉴에서 제작 및 제작 **[!UICONTROL 게시를 클릭합니다]**.

   ![image2019-7-15_16-8-9](assets/image2019-7-15_16-8-9.png)

   Adobe [Launch](https://docs.adobe.com/content/help/en/launch/using/reference/publish/overview.html) 게시 프로세스에 대한 자세한 내용은 게시를 참조하십시오.

## 통합을 위해 Adobe Experience Manager 구성 {#configuring-adobe-experience-manager-for-the-integration}

<!-- Prerequisites lost below should be verified by Sasha -->

전제 조건:

* AEM은 작성자 및 게시 인스턴스를 모두 실행합니다.
* AEM 작성자 노드는 Dynamic Media에서 설정됩니다. <!-- Scene7 run mode (dynamicmedia_s7) -->
* Dynamic Media WCM 구성 요소는 AEM Sites에서 활성화됩니다.

AEM 구성은 다음 두 가지 주요 단계로 구성됩니다.

* AEM IMS 구성.
* Adobe Launch Cloud 구성

### AEM IMS 구성. {#configuring-aem-ims}

1. AEM 작성기에서 도구 아이콘(망치)을 클릭한 다음 보안 > **[!UICONTROL Adobe IMS 구성을 클릭합니다]**.

   ![2019-07-25_11-52-58](assets/2019-07-25_11-52-58.png)

1. Adobe IMC 구성 페이지의 왼쪽 위 모퉁이에서 만들기를 **[!UICONTROL 클릭합니다]**.
1. Adobe IMS **[!UICONTROL 기술 계정 구성]** 페이지의 클라우드 솔루션 **[!UICONTROL 드롭다운 목록에서 Adobe]** Launch를 **[!UICONTROL 클릭합니다]**.
1. 새 **[!UICONTROL 인증서를]**&#x200B;만든 다음 텍스트 필드에 인증서에 대한 의미 있는 값을 입력합니다. 예를 들어 AdobeLaunchIMSCert *와 같습니다*. 인증서 **[!UICONTROL 만들기를 클릭합니다]**.

   다음 정보 메시지가 표시됩니다.

   *유효한 액세스 토큰을 검색하려면 새 인증서의 공개 키를 Adobe I/O!*&#x200B;기술 계정에 추가해야 합니다.

   Click **[!UICONTROL OK]** to dismiss the Info dialog box.

   ![2019-07-25_12-09-24](assets/2019-07-25_12-09-24.png)

1. 공개 **[!UICONTROL 키 다운로드를]** 클릭하여 공개 키 파일(`*.crt`)을 로컬 시스템에 다운로드합니다.

   >[!NOTE]
   >
   >이때 Adobe IMS 기술 ***계정 구성*** 페이지를 **[!UICONTROL 엽니다]** .페이지를 닫지 ***말고*** 다음을 ***클릭하지*** 마십시오. 이 페이지는 나중에 단계에서 다시 표시됩니다.

   ![2019-07-25_12-52-24](assets/2019-07-25_12-52-24.png)

1. 새 브라우저 탭에서 Adobe I/O [콘솔로 이동합니다](https://console.adobe.io/integrations).

1. Adobe **[!UICONTROL I/O 콘솔 통합]** 페이지의 오른쪽 위 모서리에서 새 통합을 **[!UICONTROL 클릭합니다]**.
1. 새 **[!UICONTROL 통합]** 만들기 대화 상자에서 API **[!UICONTROL 라디오]** 단추에 대한 액세스를 선택한 다음 계속을 **[!UICONTROL 클릭합니다]**.

   ![2019-07-25_13-04-20](assets/2019-07-25_13-04-20.png)

1. 두 번째 **[!UICONTROL 통합]** 만들기 페이지에서 Experience Platform Launch API **[!UICONTROL 라디오 단추를 활성화(켜기)]** 합니다. 페이지의 오른쪽 아래 모서리에서 계속을 **[!UICONTROL 클릭합니다]**.

   ![2019-07-25_13-13-54](assets/2019-07-25_13-13-54.png)

1. 세 번째 **[!UICONTROL 통합]** 만들기 페이지에서 다음을 수행합니다.

   * 이름 **[!UICONTROL 필드에]** 수사적 이름을 입력합니다. 예: DynamicMediaViewers *IO*.

   * 설명 **[!UICONTROL 필드에]** 통합에 대한 설명을 입력합니다.

   * 공개 **[!UICONTROL 키 인증서]** 영역에서 이전에 다운로드한 공개 키 파일(`*.crt`)을 업로드합니다.

   * Experience **[!UICONTROL Platform Launch API에 대한 역할 선택]** 머리글에서 관리를 **[!UICONTROL 선택합니다]**.

   * Experience **[!UICONTROL Platform Launch API용 제품 프로필 선택]** 머리글에서 Launch - &lt;your_company_name> **[!UICONTROL 이라는 제품 프로필을 선택합니다]**.
   ![2019-07-25_13-49-18](assets/2019-07-25_13-49-18.png)

1. 통합 **[!UICONTROL 만들기를 클릭합니다]**.
1. 통합 **[!UICONTROL 생성]** 페이지에서 계속을 클릭하여 통합 **[!UICONTROL 세부 사항을]**&#x200B;확인합니다.

   ![2019-07-25_14-16-33](assets/2019-07-25_14-16-33.png)

1. 다음과 유사한 통합 세부 정보 페이지가 나타납니다.

   >[!NOTE]
   >
   >***이 통합 세부 정보 페이지를***&#x200B;열어 두십시오. 개요 및 JWT **[!UICONTROL 탭의 다양한]** 정보가 **** 즉시 필요합니다.

   ![2019-07-25_14-35-30](assets/2019-07-25_14-35-30.png)
   _통합 세부 정보 페이지_

1. 이전에 열어둔 **[!UICONTROL Adobe IMS 기술 계정 구성]** 페이지로 돌아갑니다. 페이지의 오른쪽 위 모서리에서 다음을 클릭하여 **[!UICONTROL Adobe]** IMS 기술 **[!UICONTROL 계정]** 구성 **[!UICONTROL 창에서 계정]** 페이지를엽니다.

   (실수로 페이지를 이전에 닫은 경우 AEM 작성자로 돌아간 다음 도구 > 보안 **[!UICONTROL > Adobe IMS 구성을 클릭합니다]**. **[!UICONTROL 만들기]**&#x200B;를 클릭합니다. 클라우드 **[!UICONTROL 솔루션]** 드롭다운 목록에서 Adobe Launch를 **[!UICONTROL 선택합니다]**. 인증서 **[!UICONTROL 드롭다운]** 목록에서 이전에 만든 인증서의 이름을 선택합니다.

   ![2019-07-25_20-57-50](assets/2019-07-25_20-57-50.png)
   _Adobe IMS 기술 계정 구성 - 인증서 페이지_

1. 계정 **[!UICONTROL 페이지에는]** 이전 단계의 통합 세부 사항 페이지에서 입력한 정보를 사용하여 작성해야 하는 5개의 필드가 있습니다.

   ![2019-07-25_20-42-45](assets/2019-07-25_20-42-45.png)
   _Adobe IMS 기술 계정 구성 - 계정 페이지_

1. 계정 **[!UICONTROL 페이지에서]** 다음 필드를 입력합니다.

   * **[!UICONTROL 제목]** - 설명 계정 제목을 입력합니다.
   * **[!UICONTROL 인증]** 서버 - 이전에 열었던 통합 세부 사항 페이지로 돌아갑니다. Click the **[!UICONTROL JWT]** tab. 경로 없이 아래 강조 표시된 대로 서버 이름을 복사합니다.
   계정 **[!UICONTROL 페이지로 돌아가서]** 해당 필드에 이름을 붙여 넣습니다.
예를 들어 `https://ims-na1.adobelogin.com/`(예제 서버 이름은 일러스트레이션 용도로만 사용)

   ![2019-07-25_15-01-53](assets/2019-07-25_15-01-53.png)
   _통합 세부 정보 페이지 - JWT 탭_

1. **[!UICONTROL API 키]** - 통합 세부 사항 페이지로 돌아갑니다. 개요 **[!UICONTROL 탭을 클릭한]** 다음 API 키(클라이언트 ID) **[!UICONTROL 필드 오른쪽에]** 있는 복사를 **[!UICONTROL 클릭합니다]**.

   계정 **[!UICONTROL 페이지로 돌아가서]** 해당 필드에 키를 붙여 넣습니다.

   ![2019-07-25_14-35-333](assets/2019-07-25_14-35-333.png)
   _통합 세부 정보 페이지_

1. **[!UICONTROL 클라이언트 암호]**- 통합 세부 사항 페이지로 돌아갑니다. 개요 **[!UICONTROL 탭에서]** 클라이언트 암호 **[!UICONTROL 검색을 클릭합니다]**. 클라이언트 암호 **[!UICONTROL 필드 오른쪽에서 복사를]** 클릭합니다 ****.

   계정 **[!UICONTROL 페이지로 돌아가서]** 해당 필드에 키를 붙여 넣습니다.

1. **[!UICONTROL 페이로드]** - 통합 세부 사항 페이지로 돌아갑니다. JWT **[!UICONTROL 탭의]** JWT 페이로드 필드에서 전체 JSON 개체 코드를 복사합니다.

   계정 **[!UICONTROL 페이지로 돌아가서]** 코드를 각 필드에 붙여 넣습니다.

   ![2019-07-25_21-59-12](assets/2019-07-25_21-59-12.png)
   _통합 세부 정보 페이지 - JWT 탭_

   모든 필드가 채워진 계정 페이지는 다음과 비슷하게 표시됩니다.

   ![2019-07-25_22-08-30](assets/2019-07-25_22-08-30.png)

1. 계정 페이지의 오른쪽 위 모서리 **[!UICONTROL 근처에]** 있는 만들기를 **[!UICONTROL 클릭합니다]**.

   AEM IMS가 구성된 경우 이제 Adobe IMS 구성 아래에 새 **[!UICONTROL IMSAccount가 나열됩니다]**.

   ![image2019-7-15_14-17-54](assets/image2019-7-15_14-17-54.png)

## 통합을 위해 Adobe Launch Cloud 구성 {#configuring-adobe-launch-cloud-for-the-integration}

1. AEM 작성자의 왼쪽 위 모서리에서 도구 아이콘(망치)을 클릭한 다음 클라우드 서비스 **[!UICONTROL > Adobe Launch 구성을 클릭합니다]**.

   ![2019-07-26_12-10-38](assets/2019-07-26_12-10-38.png)

1. Adobe **[!UICONTROL Launch 구성]** 페이지의 왼쪽 패널에서 Adobe Launch 구성을 적용할 AEM 사이트를 선택합니다.

   일러스트레이션만을 위해 아래 스크린샷에서 **[!UICONTROL We.]** Retail 사이트가 선택됩니다.

   ![2019-07-26_12-20-06](assets/2019-07-26_12-20-06.png)

1. 페이지의 왼쪽 위 모서리 근처에 있는 만들기를 **[!UICONTROL 클릭합니다]**.
1. Adobe **[!UICONTROL Launch 구성]** 만들기 **[!UICONTROL 창의 일반 페이지(1/3페이지)에서]** 다음필드를 채웁니다.

   * **[!UICONTROL 제목]** - 설명 구성 제목을 입력합니다. 예, `We.Retail Launch cloud configuration`.

   * **[!UICONTROL 연결된 Adobe IMS 구성]** - AEM IMS 구성에서 이전에 만든 [IMS 구성을 선택합니다.](#configuring-aem-ims).

   * **[!UICONTROL 회사]** - **[!UICONTROL 회사]** 드롭다운 목록에서 Experience Cloud 회사를 선택합니다. 목록이 자동으로 채워집니다.

   * **[!UICONTROL 속성]** - 속성 드롭다운 목록에서 이전에 만든 Adobe Launch 속성을 선택합니다. 목록이 자동으로 채워집니다.
   모든 필드를 완료한 후 **[!UICONTROL 일반]** 페이지는 다음과 비슷합니다.

   ![image2019-7-15_14-34-23](assets/image2019-7-15_14-34-23.png)

1. 왼쪽 위 모서리 근처에 있는 [다음]을 **[!UICONTROL 클릭합니다]**.
1. Adobe **[!UICONTROL Launch]** 구성 만들기 **[!UICONTROL 창의 스테이징 페이지(2/3 페이지)]** 에서다음 필드를 채웁니다.

   라이브러리 **[!UICONTROL URI]** 필드에서 Adobe Launch 라이브러리의 스테이징 버전 위치를 확인합니다. AEM이 이 필드를 자동으로 채웁니다.

   일러스트레이션 목적으로만 이 단계에서는 Adobe CDN에 배포된 Adobe Launch 라이브러리를 사용합니다.

   >[!NOTE]
   >
   >자동 채워진 라이브러리 URI(Uniform Resource Identifier)의 형식이 아닌지 확인하십시오. 필요한 경우 URI가 프로토콜 상대 URI를 나타내도록 수정합니다. 즉, 이중 슬래시에서 시작됩니다.
   >
   >
   >예: `//assets.adobetm.com/launch-xxxx`.

   스테이징 **[!UICONTROL 페이지는]** 다음과 유사해야 합니다. [라이브러리 비동기식으로 **[!UICONTROL 보관]** 및 **[!UICONTROL 로드]** ] 옵션은 ***설정되지*** 않습니다.

   ![image2019-7-15_15-21-8](assets/image2019-7-15_15-21-8.png)

1. 오른쪽 위 모서리 근처에 있는 [다음]을 **[!UICONTROL 클릭합니다]**.
1. Adobe **[!UICONTROL Launch 구성]** 만들기 **[!UICONTROL 창의 프로덕션 페이지(3/3 페이지)에서]** 필요한 경우 자동 채워진 프로덕션 URI를 이전 스테이징 페이지에서 수행한 것과 유사한 방식으로 **[!UICONTROL 수정합니다]** .
1. 오른쪽 위 모서리 근처에 있는 만들기를 **[!UICONTROL 클릭합니다]**.

   이제 새 Adobe Launch Cloud 구성이 만들어져 웹 사이트 옆에 나열됩니다.

1. 새 Adobe Launch Cloud 구성을 선택합니다(구성 제목을 선택하면 구성 제목 왼쪽에 확인 표시가 나타납니다). 도구 모음에서 게시를 **[!UICONTROL 클릭합니다]**.

   ![image2019-7-15_15-47-6](assets/image2019-7-15_15-47-6.png)

현재 AEM 작성자는 Dynamic Media Viewer와 Adobe Launch의 통합을 지원하지 않습니다.

하지만 AEM 게시 노드에서 지원됩니다. AEM 게시에서는 Adobe Launch 클라우드 구성의 기본 설정을 사용하여 Adobe Launch의 프로덕션 환경을 사용합니다. 따라서 테스트 중에 매번 개발 환경에서 프로덕션 환경으로 Adobe Launch 라이브러리 업데이트를 푸시해야 합니다.

위의 AEM 게시용 Adobe Launch Cloud 구성에서 Adobe Launch 라이브러리의 개발 또는 스테이징 URL을 지정하여 이 제한 사항을 해결할 수 있습니다. 이렇게 하면 AEM 게시 노드가 Adobe Launch 라이브러리의 개발 또는 스테이징 버전을 사용하게 됩니다.

Adobe [Launch Cloud 구성 설정에 대한 자세한](https://helpx.adobe.com/experience-manager/using/aem_launch_adobeio_integration.html) 내용은 Adobe I/O를 통해 AEM과 Adobe Launch 통합을 참조하십시오.