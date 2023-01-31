---
title: 빠른 보기를 사용하여 맞춤형 팝업 제작
description: 제품 정보와 함께 팝업 창이 표시되어 구매를 유도하는 전자 상거래 경험에서 기본 Quickview가 어떻게 사용되는지 알아봅니다. 팝업 창에 표시할 사용자 지정 콘텐츠를 트리거할 수 있습니다.
contentOwner: Rick Brough
feature: Interactive Images,Interactive Videos,Carousel Banners
role: Admin,User
exl-id: c2bc6ec8-d46e-4681-ac3e-3337b9e6ae5c
source-git-commit: 35caac30887f17077d82f3370f1948e33d7f1530
workflow-type: tm+mt
source-wordcount: '1002'
ht-degree: 2%

---

# 빠른 보기를 사용하여 맞춤형 팝업 제작 {#using-quickviews-to-create-custom-pop-ups}

기본 Quickview는 전자 상거래 경험에서 사용되어 제품 정보와 함께 팝업이 표시되어 구매를 유도합니다. 그러나 사용자 정의 컨텐츠를 트리거하여 팝업에 표시할 수 있습니다. 사용하는 뷰어에 따라 고객은 핫스팟이나 축소판 이미지 또는 이미지 맵을 선택하여 정보나 관련 컨텐츠를 볼 수 있습니다.

빠른 보기는 Dynamic Media의 다음 뷰어에서 지원됩니다.

* 대화형 이미지(선택 가능한 핫스팟)
* 대화형 비디오(비디오 재생 중 선택 가능한 축소판 이미지)
* 회전 배너(선택 가능한 핫스팟이나 이미지 맵)

각 뷰어의 기능은 다르지만, 빠른 보기를 만드는 프로세스는 지원되는 세 뷰어 모두에서 동일합니다.

**빠른 보기를 사용하여 사용자 지정 팝업을 만들려면 다음을 수행하십시오.**

1. 업로드된 자산에 대한 빠른 보기를 만듭니다.

   일반적으로 사용 중인 뷰어와 함께 사용할 자산을 편집하는 것과 동시에 빠른 보기를 만듭니다.

   <table>
    <tbody>
    <tr>
    <td><strong>사용 중인 뷰어</strong></td>
    <td><strong>빠른 보기를 만들려면 다음 단계를 완료하십시오</strong></td>
    </tr>
    <tr>
    <td>대화형 이미지</td>
    <td><a href="/help/assets/dynamic-media/interactive-images.md#adding-hotspots-to-an-image-banner" target="_blank">이미지 배너에 핫스팟 추가</a>.</td>
    </tr>
    <tr>
    <td>대화형 비디오</td>
    <td><a href="/help/assets/dynamic-media/interactive-videos.md#adding-interactivity-to-your-video" target="_blank">비디오에 인터랙티브한 추가</a>.</td>
    </tr>
    <tr>
    <td>회전 배너</td>
    <td><a href="/help/assets/dynamic-media/carousel-banners.md#adding-hotspots-or-image-maps-to-an-image-banner" target="_blank">배너에 핫스팟 또는 이미지 맵 추가</a>.<br /> </td>
    </tr>
    </tbody>
   </table>

1. 웹 사이트 내에서 뷰어를 통합하기 위한 뷰어 포함 코드 가져오기.

   <table>
    <tbody>
    <tr>
    <td><strong>사용 중인 뷰어</strong><br /> </td>
    <td><strong>뷰어를 웹 사이트와 통합하려면 다음 단계를 완료하십시오</strong></td>
    </tr>
    <tr>
    <td>대화형 이미지</td>
    <td><a href="/help/assets/dynamic-media/interactive-images.md#integrating-an-interactive-image-with-your-website" target="_blank">웹 사이트와 대화형 이미지 통합</a>.<br /> </td>
    </tr>
    <tr>
    <td>대화형 비디오<br /> </td>
    <td><a href="/help/assets/dynamic-media/interactive-videos.md#integrating-an-interactive-video-with-your-website" target="_blank">웹 사이트와 대화형 비디오 통합</a>.<br /> </td>
    </tr>
    <tr>
    <td>회전 배너</td>
    <td><a href="/help/assets/dynamic-media/carousel-banners.md#adding-a-carousel-banner-to-your-website-page" target="_blank">웹 사이트 페이지에 회전 배너 추가</a>.<br /> </td>
    </tr>
    </tbody>
   </table>

1. 사용하는 뷰어는 Quickview를 사용하는 방법을 알고 있어야 합니다.

   뷰어는 `QuickViewActive`.

   **예**
웹 페이지에서 대화형 이미지에 다음 샘플 포함 코드를 사용했다고 가정해 봅시다.

   ![chlimage_1-291](assets/chlimage_1-291.png)

   핸들러가 를 사용하여 뷰어에 로드됩니다 `setHandlers`:

   `*viewerInstance*.setHandlers({ *handler 1*, *handler 2*}, ...`

   **위의 샘플 포함 코드 예를 사용하면 다음 코드가 있습니다.**

   ```xml {.line-numbers}
   s7interactiveimageviewer.setHandlers({
       quickViewActivate": function(inData) {
           var sku=inData.sku;
           var genericVariable1=inData.genericVariable1;
           var genericVariable2=inData.genericVariable2;
          loadQuickView(sku,genericVariable1,genericVariable2);
       }
   })
   ```

   추가 정보 `setHandlers()` 메서드를 사용합니다.

   * 대화형 이미지 뷰어 - [제비](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-for-aem-assets-only/interactive-images/jsapi-interactive-image/r-html5-aem-int-image-viewer-javascriptapiref-sethandlers.html)
   * 대화형 비디오 뷰어 - [제비](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-for-aem-assets-only/interactive-video/jsapi-interactive-video/r-html5-aem-int-video-javascriptapiref-sethandlers.html)

1. 이제 를 구성합니다 `quickViewActivate` 핸들러.

   다음 `quickViewActivate` 처리기는 뷰어의 Quickview를 제어합니다. 처리기에는 Quickview에 사용할 변수 목록과 함수 호출이 포함되어 있습니다. 포함 코드는 Quickview에 설정된 SKU 변수에 대한 매핑을 제공합니다. 이것은 또한 샘플을 만든다 `loadQuickView` 함수 호출.

   **변수 매핑**
웹 페이지에서 사용할 변수를 SKU 값 및 빠른 보기에 포함된 일반 변수에 매핑합니다.

   `var *variable1*= inData.*quickviewVariable*`

   제공된 포함 코드에는 SKU 변수에 대한 샘플 매핑이 있습니다.

   `var sku=inData.sku`

   다음과 같이 Quickview의 다른 변수를에 매핑합니다.

   ```xml {.line-numbers}
   var <i>variable2</i>= inData.<i>quickviewVariable2</i>
    var <i>variable3</i>= inData.<i>quickviewVariable3</i>
   ```

   **함수 호출**
또한 처리기에서는 Quickview가 작동하려면 함수 호출이 필요합니다. 함수는 호스트 페이지에서 액세스할 수 있다고 가정합니다. 포함 코드는 샘플 함수 호출을 제공합니다.

   `loadQuickView(sku)`

   샘플 함수 호출에서는 함수를 가정합니다 `loadQuickView()` 존재하며 액세스할 수 있습니다.

   추가 정보 `quickViewActivate` 메서드를 사용합니다.

   * 대화형 이미지 뷰어 - [이벤트 콜백](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-for-aem-assets-only/interactive-images/c-html5-aem-interactive-image-event-callbacks.html)
   * 대화형 비디오 뷰어 - [이벤트 콜백](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-for-aem-assets-only/interactive-video/c-html5-aem-int-video-event-callbacks.html)
   * 대화형 비디오 뷰어에서 대화형 데이터 지원 - [대화형 데이터 지원](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-for-aem-assets-only/interactive-video/c-html5-aem-int-video-int-data-support.html)

1. 다음을 수행합니다.

   * 포함 코드의 setHandlers 섹션의 주석을 해제합니다.
   * Quickview에 포함된 모든 추가 변수를 매핑합니다.

      * 업데이트 `loadQuickView(sku,*var1*,*var2*)` 변수를 더 추가할 경우 를 호출합니다.
   * 간단한 만들기 `loadQuickView` () 함수를 뷰어 외부에서 페이지에 추가합니다.

      예를 들어, 다음은 SKU 값을 브라우저 콘솔에 씁니다.

   ```xml {.line-numbers}
   function loadQuickView(sku){
       console.log ("quickview sku value is " + sku);
   }
   ```

   * 테스트 HTML 페이지를 웹 서버에 업로드하고 엽니다.

      빠른 보기의 변수가 매핑됩니다. 함수 호출이 있습니다. 브라우저 콘솔은 변수 값을 브라우저 콘솔에 기록합니다. 제공된 샘플 함수를 사용하여 이 작업을 수행합니다.



1. 이제 함수를 사용하여 Quickview에서 간단한 팝업을 호출할 수 있습니다. 다음 예제에서는 `DIV` 팝업에 사용됩니다.
1. 팝업 스타일 지정 `DIV` 아래와 같이 변경하는 것을 의미합니다. 원하는 대로 스타일을 추가합니다.

   ```xml {.line-numbers}
   <style type="text/css">
       #quickview_div{
           position: absolute;
           z-index: 99999999;
           display: none;
       }
   </style>
   ```

1. 팝업 배치 `DIV` HTML 페이지 본문 아래에 표시됩니다.

   요소 중 하나는 사용자가 Quickview를 호출할 때 SKU 값으로 업데이트된 ID로 설정됩니다. 또한 팝업이 표시된 후 팝업을 다시 숨기기 위한 간단한 단추도 포함되어 있습니다.

   ```xml {.line-numbers}
   <div id="quickview_div" >
       <table>
           <tr><td><input id="btnClosePopup" type="button" value="Close"        onclick='document.getElementById("quickview_div").style.display="none"' /><br /></td></tr>
           <tr><td>SKU</td><td><input type="text" id="txtSku" name="txtSku"></td></tr>
       </table>
   </div>
   ```

1. 팝업 창에서 SKU 값을 업데이트하려면 함수를 추가합니다. 5단계에서 만든 단순 함수를 다음과 같이 대체하여 팝업 창을 표시합니다.

   ```xml {.line-numbers}
   <script type="text/javascript">
       function loadQuickView(sku){
           document.getElementById("txtSku").setAttribute("value",sku); // write sku value
           document.getElementById("quickview_div").style.display="block"; // show popup
       }
   </script>
   ```

1. 테스트 HTML 페이지를 웹 서버에 업로드하고 엽니다. 뷰어에 팝업이 표시됩니다 `DIV` 사용자가 빠른 보기를 호출하는 경우.
1. **전체 화면 모드로 사용자 지정 팝업 창을 표시하는 방법**

   대화형 비디오 뷰어와 같은 일부 뷰어는 전체 화면 모드로 표시를 지원합니다. 그러나 이전 단계에서 설명한 대로 팝업을 사용하면 전체 화면 모드에 있는 동안 뷰어 뒤에 표시됩니다.

   팝업 창을 표준 및 전체 화면 모드로 표시하려면 팝업 창을 뷰어 컨테이너에 첨부합니다. 이 경우 두 번째 처리기 메서드를 사용하고 `initComplete`.

   다음 `initComplete` 뷰어가 초기화되면 처리기가 호출됩니다.

   ```xml {.line-numbers}
   "initComplete":function() { code block }
   ```

   추가 정보 `init()` 메서드를 사용합니다.

   * 대화형 이미지 뷰어 - [init](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-for-aem-assets-only/interactive-images/jsapi-interactive-image/r-html5-aem-int-image-viewer-javascriptapiref-init.html)
   * 대화형 비디오 뷰어 - [init](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-for-aem-assets-only/interactive-video/jsapi-interactive-video/r-html5-aem-int-video-javascriptapiref-init.html)

1. 이전 단계에 설명된 팝업을 뷰어에 연결하려면 다음 코드를 사용하십시오.

   ```xml {.line-numbers}
   "initComplete":function() {
       var popup = document.getElementById('quickview_div');
       popup.parentNode.removeChild(popup);
       var sdkContainerId = s7interactivevideoviewer.getComponent("container").getInnerContainerId();
       var inner_container = document.getElementById(sdkContainerId);
       inner_container.appendChild(popup);
   }
   ```

   위의 코드에서 다음을 수행했습니다.

   * 사용자 지정 팝업 창을 식별했습니다.
   * DOM에서 제거했습니다.
   * 뷰어 컨테이너를 식별했습니다.
   * 뷰어 컨테이너에 팝업을 첨부했습니다.

1. 전체 setHandlers 코드는 다음과 비슷합니다(대화형 비디오 뷰어가 사용됨).

   ```xml {.line-numbers}
   s7interactivevideoviewer.setHandlers({
       "quickViewActivate": function(inData) {
           var sku=inData.sku;
           loadQuickView(sku);
   
       },
       "initComplete":function() {
           var popup = document.getElementById('quickview_div'); // get custom quick view container
           popup.parentNode.removeChild(popup); // remove it from current DOM
           var sdkContainerId = s7interactivevideoviewer.getComponent("container").getInnerContainerId();
           var inner_container = document.getElementById(sdkContainerId);
           inner_container.appendChild(popup);
       }
   });
   ```

1. 핸들러가 로드되면 뷰어를 초기화합니다.

   `*viewerInstance.*init()`

   **예**
이 예에서는 대화형 이미지 뷰어를 사용합니다.

   `s7interactiveimageviewer.init()`

   뷰어를 호스트 페이지에 포함시킨 후에는 뷰어 인스턴스가 만들어졌는지 확인하십시오. 또한, `init()`.
