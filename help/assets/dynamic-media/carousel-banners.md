---
title: 회전 배너
description: Dynamic Media에서 캐러셀 배너를 사용하여 작업하는 방법을 알아봅니다.
translation-type: tm+mt
source-git-commit: f5627a6e885a556700fbf56c4c63f0f4d6a89da0
workflow-type: tm+mt
source-wordcount: '4576'
ht-degree: 0%

---


# 회전 배너{#carousel-banners}

Carousel 배너를 통해 마케터는 인터랙티브한 회전 프로모션 컨텐츠를 손쉽게 제작하여 모든 화면에 전달할 수 있으므로 전환율을 높일 수 있습니다.

홍보 배너에 포함된 컨텐츠를 만들고 수정하는 것은 시간이 많이 걸릴 수 있으므로 새 컨텐츠를 신속하게 게시하거나 보다 대상화된 컨텐츠를 만들 수 있는 기능을 제한할 수 있습니다. 회전판 배너를 사용하면 회전 배너를 빠르게 만들거나 수정할 수 있고 제품 세부 사항 또는 관련 리소스에 핫스팟 링크와 같은 인터랙티브한 요소를 추가할 수 있습니다. 모든 화면에 컨텐츠를 전달할 수 있으므로 새로운 홍보 컨텐츠를 보다 신속하게 출시할 수 있습니다.

캐러셀 배너는 **[!UICONTROL CAROUSELSET]**&#x200B;이라는 단어와 함께 배너에 의해 지정됩니다.

![chlimage_1-438](assets/chlimage_1-438.png)

웹 사이트에서 캐러셀 배너는 다음과 같이 표시됩니다.

![chlimage_1-439](assets/chlimage_1-439.png)

여기에서 숫자를 클릭하여 이미지를 탐색할 수 있습니다. 또한 사용자 정의할 수 있는 시간 간격에 따라 슬라이드가 자동으로 회전합니다. 회전판 배너에 추가하는 이미지는 핫스팟과 이미지 맵을 모두 지원합니다. 사용자는 하이퍼링크를 누르거나 탐색하거나 빠른 보기 창에 액세스할 수 있습니다.

이 예에서는 사용자가 이미지 맵을 탭하거나 클릭했으며 장갑을 위해 빠른 보기 창에 액세스했습니다.

![chlimage_1-440](assets/chlimage_1-440.png)

## 회전판 배너가 만들어지는 방법 보기 {#watch-how-carousel-banners-are-created}

회전판 배너가 만들어지는 방법](https://s7d5.scene7.com/s7viewers/html5/VideoViewer.html?videoserverurl=https://s7d5.scene7.com/is/content/&amp;emailurl=https://s7d5.scene7.com/s7/emailFriend&amp;serverUrl=https://s7d5.scene7.com/is/image/&amp;config=Scene7SharedAssets/Universal_HTML5_Video_social&amp;contenturl=https://s7d5.scene7.com/skins/&amp;asset=S7tutorials/InteractiveCarouselBanner)에 대한 10분 및 33초 연습을 보십시오. [ 캐러셀 배너를 미리 보고 편집 및 전달하는 방법도 알아봅니다.

>[!NOTE]
>
>캐러셀 배너를 만들거나 편집할 수 있으려면 관리자가 아닌 사용자를 **[!UICONTROL dam-users]** 그룹에 추가해야 합니다. 만들거나 편집하는 데 문제가 있는 경우 **d[!UICONTROL am-users]** 그룹에 추가할 수 있는 시스템 관리자를 참조하십시오.

## 빠른 시작:회전판 배너 {#quick-start-carousel-banners}

빠르게 시작하기

1. [핫스팟 및 이미지 맵 변수](#identifying-hotspot-and-image-map-variables)  식별(Adobe Experience Manager 자산 + Dynamic Media을 사용하는 고객에게만 해당)

   기존 빠른 보기 구현에서 사용하는 동적 변수를 식별하여 시작합니다. 이렇게 하면 Experience Manager 에셋의 회전판 배너 생성 프로세스 중에 핫스팟과 이미지 맵 데이터를 올바르게 입력할 수 있습니다.

<!-- LEAVE; COMMERCE BEING ADDED AGAIN IN THE FUTURE

   >[!NOTE]
   >
   >If you are an AEM Sites or Ecommerce customer, you can use the built-in feature to navigate to product pages and lookup the existing skus in the product catalog. You do not need to manually enter hotspot or image map variables.
   >
   >
   >If you are an AEM Assets and Dynamic Media customer, you will manually enter data for hotspots and image maps, and then integrate the published URL or Embed code with your third-party content management system.

-->

1. 선택 사항:[필요에 따라 회전판 집합 뷰어 사전 설정](/help/assets/dynamic-media/managing-viewer-presets.md)을 만듭니다.

   관리자인 경우 자체 Carousel 뷰어 사전 설정을 만들어 Carousel의 비헤이비어와 모양을 사용자 정의할 수 있습니다. 주요 이점은 여러 Carousel에 이 사용자 정의 뷰어 사전 설정을 다시 사용할 수 있다는 것입니다. 그러나 사용자는 Carousel을 작성하는 동안 Carousel의 비헤이비어와 모양을 원하는 대로 직접 사용자 정의할 수 있습니다. 이 방법은 지정된 Carousel에 대한 특정 디자인을 원할 때 사용하는 것이 좋습니다.

1. [이미지 배너를 업로드합니다](#uploading-image-banners).

   대화형 이미지를 만들 이미지 배너를 업로드합니다.

1. [회전판 세트를 만듭니다](#creating-carousel-sets).

   Carousel Set에서 사용자는 배너 이미지, 핫스팟 또는 이미지 맵을 통해 관련 콘텐츠에 액세스합니다.

   자산에 회전판 세트를 만들려면 **[!UICONTROL 만들기]**&#x200B;를 누른 다음 **[!UICONTROL 회전판 세트]**&#x200B;를 선택합니다. 슬라이드에 에셋을 추가하고 **[!UICONTROL 저장]**&#x200B;을 누릅니다. 또한 편집기 내에서 직접 Carousel의 모양과 동작을 편집할 수도 있습니다.

1. [이미지 배너에 핫스팟 또는 이미지 맵을 추가합니다.](#adding-hotspots-or-image-maps-to-an-image-banner)

   이미지 배너에 하나 이상의 핫스팟 또는 이미지 맵을 추가합니다. 그런 다음 각 항목을 링크, 빠른 보기 또는 경험 조각과 같은 작업에 연결합니다. 핫스팟 또는 이미지 맵을 추가한 후에는 캐러셀 세트를 게시하여 이 작업을 마칩니다. 게시를 사용하면 웹 사이트 랜딩 페이지를 복사하고 적용하는 데 사용할 수 있는 포함 코드가 만들어집니다.

   회전판 배너 미리 보기를 참조하십시오. [(선택 사항)](#optional-previewing-carousel-banners) - 선택 사항입니다. 원하는 경우 Carousel 세트의 표현을 보고 상호 작용을 테스트할 수 있습니다.

1. [회전판 배너를 게시합니다](#publishing-carousel-banners).

   모든 자산과 마찬가지로 회전판 세트를 게시합니다. 자산에서 회전판 세트로 이동하여 선택하고 **[!UICONTROL 게시]**&#x200B;를 누릅니다. 회전판 세트를 게시하면 URL 및 포함 문자열이 활성화됩니다.

1. 다음 중 하나를 수행하십시오.

   * [회전판 배너를 웹 사이트 페이지에 ](#adding-a-carousel-banner-to-your-website-page)추가회전판 배너 URL을 추가하거나 웹 사이트 페이지에 복사한 코드를 포함할 수 있습니다.

      * [회전판 배너를 기존 빠른 보기와 통합합니다](#integrating-the-carousel-banner-with-an-existing-quickview). 제3자 웹 컨텐츠 관리 시스템을 사용하는 경우 새 캐러셀 배너를 웹 사이트의 기존 빠른 보기 구현과 통합해야 합니다.
   * [Experience ](/help/assets/dynamic-media/adding-dynamic-media-assets-to-pages.md) Manager에서 웹 사이트에 캐러셀 배너 추가Experience Manager 사이트 고객의 경우 Interactive Media 구성 요소를 사용하여 Experience Manager의 페이지에 직접 캐러셀 세트를 추가할 수 있습니다.


회전판 세트를 편집해야 하는 경우 [회전판 세트 편집을 참조하십시오.](#editing-carousel-sets) 또한 회전판 세트 속성을 보고 편집할  [수 있습니다](/help/assets/manage-digital-assets.md#editing-properties).

## 핫스팟 및 이미지 맵 변수 식별 {#identifying-hotspot-and-image-map-variables}

기존 빠른 보기 구현에서 사용하는 동적 변수를 식별하여 시작합니다. 이렇게 하면 Experience Manager 자산에서 회전판 세트 생성 프로세스 동안 핫스팟 또는 이미지 맵 데이터를 올바르게 입력할 수 있습니다.

핫스팟 또는 이미지 맵을 배너 이미지에 추가하면 각 핫스팟 또는 이미지 맵에 SKU 및 선택적 추가 변수를 할당합니다. 이러한 변수는 나중에 빠른 보기 컨텐츠와 핫스팟 또는 이미지 맵을 일치시키는 데 사용됩니다.

<!-- LEAVE; COMMERCE BEING ADDED LATER

>[!NOTE]
>
>If you are an AEM Sites and/or AEM Ecommerce customer, skip this step. You do not need to manually identify hotspot or image map variables; you can use the integration with Ecommerce for product integration. See information on [setting up eCommerce](/help/sites-cloud/administering/generic.md). In addition, you can use the Interactive component and add it to your web page.
>
>If you are an AEM Assets or Media customer, you publish the URL or Embed code and then integrate with your third-party content management system and identify hotspots and image maps manually.

-->

핫스팟 또는 이미지 맵 데이터와 연결할 변수의 수와 유형을 올바르게 식별해야 합니다. 배너 이미지에 추가된 각 핫스팟 또는 이미지 맵에는 기존 백엔드 시스템에서 해당 제품을 분명하게 식별할 수 있는 충분한 정보가 포함되어 있어야 합니다. 동시에 각 핫스팟 또는 이미지 맵에 필요한 데이터보다 많은 데이터가 포함되어 있지 않아야 합니다. 그 이유는 데이터 입력 프로세스가 지나치게 복잡하거나 진행 중인 핫스팟 또는 이미지 맵 관리를 더 오류 발생 가능성이 높기 때문입니다.

핫스팟 또는 이미지 맵 데이터에 사용할 변수 세트를 식별하는 다른 방법이 있습니다.

기존 빠른 보기 구현을 담당하는 IT 전문가와의 충분한 지식이 있을 수 있습니다. 시스템에서 빠른 보기를 식별하는 최소 데이터 세트가 무엇인지 알 수 있습니다. 그러나 프런트 엔드 코드의 기존 동작을 간단하게 분석할 수 있습니다.

대부분의 빠른 보기 구현은 다음 패러다임을 사용합니다.

* 사용자는 웹 사이트에서 사용자 인터페이스 요소를 활성화합니다. 예를 들어 **[!UICONTROL 빠른 보기]** 단추를 누릅니다.
* 필요한 경우 웹 사이트에서 빠른 보기 데이터 또는 컨텐츠를 로드하기 위해 Ajax 요청을 백엔드로 보냅니다.
* [빠른 보기] 데이터는 웹 페이지에서 렌더링할 준비를 위해 컨텐츠로 변환됩니다.
* 마지막으로 프런트 엔드 코드는 이러한 컨텐츠를 화면에 시각적으로 렌더링합니다.

그러면 빠른 보기 기능이 구현된 기존 웹 사이트의 다양한 영역을 방문하는 방법이 됩니다. 그런 다음 빠른 보기를 트리거하고 웹 페이지에서 보낸 Ajax URL을 캡처하여 빠른 보기 데이터 또는 컨텐츠를 로드합니다.

일반적으로 전문적인 디버깅 도구를 사용할 필요가 없습니다. 최신 웹 브라우저는 적절한 작업을 수행하는 웹 관리자를 제공합니다. 다음은 웹 관리자를 포함하는 웹 브라우저의 몇 가지 예입니다.

* Google Chrome에서 나가는 HTTP 요청을 모두 보려면 F12(Windows) 또는 Command-Option-I(Mac)를 눌러 개발자 도구 패널을 엽니다. 네트워크 탭을 누릅니다.
* Firefox에서는 F12(Windows) 또는 Command-Option-I(Mac)를 눌러 Firebug 플러그인을 활성화할 수 있습니다. [네트워크] 탭을 사용하거나 내장된 검사기 도구 및 [네트워크] 탭을 사용합니다.

브라우저에서 네트워크 모니터링이 켜져 있으면 페이지의 빠른 보기를 트리거합니다.

이제 네트워크 로그에서 빠른 보기 Ajax URL을 찾아 기록된 URL을 복사하여 향후 분석을 수행할 수 있습니다. 일반적으로 [빠른 보기]를 트리거할 때 서버로 전송되는 요청이 많습니다. 일반적으로 빠른 보기 Ajax URL은 목록에서 첫 번째 URL 중 하나입니다. 복잡한 쿼리 문자열 부분이나 경로가 있으며 응답 MIME 유형은 `text/html`, `text/xml` 또는 `text/javascript`입니다.

이 프로세스 중에 제품 카테고리 및 유형이 다른 웹 사이트의 여러 영역을 방문하는 것이 중요합니다. 빠른 보기 URL에는 지정된 웹 사이트 카테고리에 공통인 부분이 있지만 웹 사이트의 다른 영역을 방문하는 경우에만 변경되기 때문입니다.

가장 간단한 경우 빠른 보기 URL에서 변수 부분만 제품 SKU입니다. 이 경우 SKU 값은 배너 이미지에 핫스팟 또는 이미지 맵을 추가하는 데 필요한 유일한 데이터 조각입니다.

그러나 복잡한 경우 빠른 보기 URL에는 카테고리 ID, 색상 코드, 크기 코드 등 SKU 외에도 다양한 요소가 있습니다. 이러한 경우 모든 요소는 회전식 배너 기능의 핫스팟 또는 이미지 맵 데이터 정의에 있는 별도의 변수입니다.

빠른 보기 URL 및 결과 핫스팟 또는 이미지 맵 변수의 다음 예를 생각해 보십시오.

<table>
 <tbody>
  <tr>
   <td>쿼리 문자열에 있는 단일 SKU입니다.</td>
   <td><p>기록된 빠른 보기 URL에는 다음이 포함됩니다.</p>
    <ul>
     <li><p><code>https://server/json?productId=866558&amp;source=100</code></p> </li>
     <li><p><code>https://server/json?productId=1196184&amp;source=100</code></p> </li>
     <li><p><code>https://server/json?productId=1081492&amp;source=100</code></p> </li>
     <li><p><code>https://server/json?productId=1898294&amp;source=100</code></p> </li>
    </ul> <p>URL에 있는 유일한 변수 부분은 <code>productId=</code> 쿼리 문자열 매개 변수의 값이며 SKU 값입니다. 따라서 핫스팟 또는 이미지 맵에는 <code>866558,</code> <code>1196184,</code> <code>1081492,</code> <code>1898294.</code></p> </td>
  </tr>
  <tr>
   <td>URL 경로에 있는 단일 SKU입니다.</td>
   <td><p>기록된 빠른 보기 URL에는 다음이 포함됩니다.</p>
    <ul>
     <li><p><code>https://server/product/6422350843</code></p> </li>
     <li><p><code>https://server/product/1607745002</code></p> </li>
     <li><p><code>https://server/product/0086724882</code></p> </li>
    </ul> <p>변수 부분은 경로의 마지막 부분에 있으며 이 부분은 핫스팟/이미지 맵의 SKU 값이 됩니다.<strong><code>6422350843</code>, <code>1607745002,</code> </strong><code>0086724882.</code></p> </td>
  </tr>
  <tr>
   <td>쿼리 문자열에서 SKU 및 카테고리 ID.</td>
   <td><p>기록된 빠른 보기 URL에는 다음이 포함됩니다.</p>
    <ul>
     <li><p><code>https://server/quickView/product/?category=1100004&amp;prodId=305466</code></p> </li>
     <li><p><code>https://server/quickView/product/?category=1100004&amp;prodId=310181</code></p> </li>
     <li><p><code>https://server/quickView/product/?category=1740148&amp;prodId=308706</code></p> </li>
    </ul> <p>이 경우 URL에는 2개의 다양한 부분이 있습니다. SKU는 <code>prodId</code> 매개 변수에 저장되고 카테고리 ID는 <code>category=</code> 매개 변수에 저장됩니다.</p> <p>이와 같이 핫스팟/이미지 맵 정의는 쌍입니다. 즉, SKU 값과 <code>categoryId</code>이라는 추가 변수입니다. 결과 쌍은 다음과 같습니다.</p>
    <ul>
     <li><p>SKU는 <strong><code>305466</code></strong>이고 <code>categoryId</code>은 <code>1100004</code>입니다.</p> </li>
     <li><p>SKU는 <strong><code>310181</code></strong>이고 <code>categoryId</code>은 <strong><code>1100004</code></strong>입니다.</p> </li>
     <li><p>SKU는 <strong><code>308706</code></strong>이고 <code>categoryId</code>은 <strong><code>1740148</code></strong>입니다.</p> </li>
    </ul> </td>
  </tr>
 </tbody>
</table>

## 이미지 배너 업로드 중 {#uploading-image-banners}

사용할 이미지를 이미 업로드한 경우 다음 단계로 진행합니다. [캐러셀 세트 만들기](#creating-carousel-sets). Carousel에서 사용되는 이미지는 Dynamic Media이 활성화된 후에 업로드해야 합니다.

이미지 배너를 업로드하려면 [자산 업로드](/help/assets/manage-digital-assets.md)를 참조하십시오.

## 회전판 세트 만들기 {#creating-carousel-sets}

>[!NOTE]
>
>캐러셀 배너를 만들거나 편집할 수 있으려면 관리자가 아닌 사용자를 **[!UICONTROL dam-users]** 그룹에 추가해야 합니다. 만들거나 편집하는 데 문제가 있는 경우 **[!UICONTROL dam-users]** 그룹에 추가할 수 있는 시스템 관리자를 참조하십시오.

**회전판 세트를 만들려면**

1. 자산에서 회전판 세트를 만들 폴더로 이동하고 **[!UICONTROL 만들기 > 회전판 세트]**&#x200B;를 누릅니다.
1. 회전판 배너 편집기 페이지에서 **[!UICONTROL 탭하여 자산 선택기]**&#x200B;를 열고 첫 번째 슬라이드의 이미지를 선택합니다.

   회전판 배너 편집기 페이지에서 다음 중 하나를 수행합니다.

   * 페이지의 왼쪽 위 모서리 근처에 있는 **[!UICONTROL 슬라이드 추가]** 아이콘을 탭합니다.

   * 페이지 가운데 근처에 있는 **[!UICONTROL 탭하여 자산 선택기]**&#x200B;를 엽니다.
   회전판 세트에 포함할 자산을 탭하여 선택합니다. 선택한 자산에 확인 표시 아이콘이 표시됩니다. 완료되면 페이지의 오른쪽 위 모서리 근처에 있는 **[!UICONTROL 선택]**&#x200B;을 탭합니다.

   자산 선택기를 사용하여 키워드를 입력하고 **[!UICONTROL Return]**&#x200B;을 탭하거나 클릭하여 자산을 검색할 수 있습니다. 필터를 적용하여 검색 결과를 세분화할 수도 있습니다. 경로, 컬렉션, 파일 유형 및 태그별로 필터링할 수 있습니다. 필터를 선택한 다음 도구 모음에서 **[!UICONTROL 필터]** 아이콘을 누릅니다. 보기 아이콘을 탭하고 **[!UICONTROL 열 보기]**, **[!UICONTROL 카드 보기]** 또는 **[!UICONTROL 목록 보기]**&#x200B;를 선택하여 보기를 변경합니다.

   자세한 내용은 [선택기 작업](/help/assets/dynamic-media/working-with-selectors.md)을 참조하십시오.

1. 회전판 세트에서 회전할 모든 이미지를 추가할 때까지 슬라이드를 계속 추가합니다.
1. (선택 사항) 다음 중 하나를 수행합니다.

   * 필요한 경우 슬라이드 목록을 드래그하여 이미지 순서를 변경합니다.
   * 이미지를 삭제하려면 이미지를 선택한 다음 도구 모음에서 **[!UICONTROL 슬라이드 삭제]**&#x200B;를 누릅니다.

   * 사전 설정을 적용하려면 페이지의 오른쪽 위 모서리 근처에 있는 사전 설정 드롭다운 목록을 탭한 다음, 세트에 한 번에 적용할 사전 설정을 선택합니다.
   슬라이드를 삭제하려면 슬라이드를 탭하거나 클릭하고 도구 모음에서 **[!UICONTROL 슬라이드 삭제]**&#x200B;를 탭하거나 클릭합니다. 슬라이드를 이동하려면 순서 변경 아이콘을 누른 상태에서 원하는 위치로 이동합니다.

1. 슬라이드에서 이미지를 추가한 후 이미지에 핫스팟, 이미지 맵 또는 둘 다를 추가할 수 있습니다. [핫스팟 또는 이미지 맵](#adding-hotspots-or-image-maps-to-an-image-banner) 추가를 참조하십시오.
1. 동작 및 모양 탭을 탭하거나 클릭하고 캐러셀 배너의 모양 또는 특정 구성 요소의 작동 방식을 조정하여 회전 메뉴 세트의 시각적 디자인과 동작을 변경할 수 있습니다. 뷰어 편집기를 사용하는 방법에 대한 자세한 내용은 [뷰어 사전 설정 관리](/help/assets/dynamic-media/viewer-presets.md)를 참조하십시오.

   >[!NOTE]
   >
   >회전판 배너의 경우 다음을 조정할 수 있습니다.
   >    * 이미지가 표시되는 지속 시간입니다. 기본적으로 각 이미지는 9초 동안 표시됩니다.
   >    * 애니메이션. 기본적으로 각 슬라이드 전환은 페이드입니다. 슬라이드 전환으로 변경할 수 있습니다.
   >    * 단추의 스타일입니다. 사용자는 각 도트 또는 숫자를 눌러 배너를 통해 회전할 수 있습니다. 세트 표시기 단추가 표시되는 위치와 숫자 또는 점선 스타일인 경우 단추 크기를 변경할 수 있습니다.
   >    * 이미지 맵의 밝은 영역 스타일이나 핫스팟에 사용된 아이콘을 변경합니다.
   >    * 뷰어 사전 설정을 편집하기 전에 사전 설정을 기반으로 할 스타일을 선택합니다. 스타일을 선택하지 않으면 뷰어 사전 설정을 편집하기 시작하면 다른 사전 설정으로 변경하면 변경 사항이 모두 손실됩니다.


   회전판 배너의 모양을 미리 볼 수도 있습니다. [(선택 사항) 회전판 배너 미리 보기](#optional-previewing-carousel-banners)를 참조하십시오.

1. 완료되면 **[!UICONTROL 저장]**&#x200B;을 누릅니다.

## 이미지 배너 {#adding-hotspots-or-image-maps-to-an-image-banner}에 핫스팟 또는 이미지 맵 추가

회전판 세트 편집기를 사용하여 배너에 핫스팟 또는 이미지 맵을 추가할 수 있습니다.

핫스팟 또는 이미지 맵을 추가할 때 빠른 보기 팝업 표시, 하이퍼링크 또는 경험 조각으로 정의할 수 있습니다.

[경험 조각](/help/sites-cloud/authoring/fundamentals/experience-fragments.md)을 참조하십시오.

>[!NOTE]
>
>Carousel 배너의 소셜 미디어 공유 도구는 경험 조각에 뷰어를 포함할 때 지원되지 않습니다.
>
>이 문제를 해결하려면 소셜 미디어 공유 도구가 없는 뷰어 사전 설정을 사용하거나 만들 수 있습니다. 이러한 뷰어 사전 설정을 사용하여 경험 조각에 성공적으로 포함할 수 있습니다.

이미지에 핫스팟 또는 이미지 맵을 추가할 때 작업을 저장해야 합니다. 현재 작성/편집 세션 동안 페이지의 오른쪽 위 모서리 근처에 있는 실행 취소 및 재실행 옵션이 지원됩니다.

캐러셀 배너 만들기를 완료하면 선택적으로 [미리 보기]를 사용하여 캐러셀 배너가 고객에게 어떻게 표시되는지 확인할 수 있습니다.

[(선택 사항) 회전판 배너 미리 보기를 참조하십시오.](#optional-previewing-carousel-banners)

>[!NOTE]
>
>[대화형 이미지](/help/assets/dynamic-media/interactive-images.md) 또는 캐러셀 배너의 이미지에 핫스팟을 추가하면 핫스팟 정보가 이미지의 위치를 기준으로 동일한 메타데이터 위치에 저장됩니다. 이 점은 대화형 이미지나 회전 배너인지 여부에 관계없이 적용됩니다. 이 기능은 두 뷰어 모두에서 정의된 핫스팟 데이터와 함께 동일한 이미지를 쉽게 재사용할 수 있음을 의미합니다.
그러나 회전판 배너는 핫스팟도 포함될 수 있는 이미지에서 이미지 맵을 지원합니다.대화형 이미지는 그렇지 않습니다. 동일한 이미지를 사용하는 대화형 이미지 또는 회전 배너를 만들려는 경우 이 팁을 염두에 두십시오. 대신 동일한 이미지의 개별 사본을 사용하여 대화형 이미지 및 회전 배너를 만드는 것이 좋습니다.

>[!NOTE]
핫스팟이 있는 대화형 이미지를 편집하고 이미지를 자르면 핫스팟이 제거됩니다.

<!-- See also [Adding Image Maps](/help/assets/image-maps.md). -->

**이미지 배너에 핫스팟 또는 이미지 맵을 추가하려면**

1. 자산에서 대화형으로 만들 회전판 세트로 이동합니다.
1. 회전판 세트를 선택하고 **[!UICONTROL 편집]**&#x200B;을 누릅니다. 회전판 뷰어 편집기가 열립니다.
1. 대화형으로 만들 슬라이드를 선택합니다.
1. 페이지의 왼쪽 위 모서리 근처에 있는 **[!UICONTROL 핫스팟]** 또는 **[!UICONTROL 이미지 맵]**&#x200B;을 탭합니다.
1. 다음 중 하나를 수행합니다.

   * 핫스팟:이미지에서 핫스팟을 표시할 위치를 누릅니다.
   * 이미지 맵의 경우:이미지에서 클릭하고 왼쪽 위에서 오른쪽 아래로 드래그하여 이미지 맵 영역을 만듭니다. 모퉁이를 드래그하여 이미지 맵의 크기를 조정할 수 있습니다.

   필요한 경우 핫스팟 또는 이미지 맵을 새 위치로 드래그합니다. 또는 키보드 화살표 키를 사용하여 선택한 핫스팟의 위치를 제어합니다. 필요에 따라 핫스팟 또는 이미지 맵을 더 추가합니다.

   핫스팟 또는 이미지 맵을 삭제하려면 **[!UICONTROL 작업]** 탭을 누릅니다. **[!UICONTROL 맵 및 핫스팟]** 머리글 아래의 **[!UICONTROL 선택한 유형]** 드롭다운 목록에서 제거할 핫스팟 또는 이미지 맵의 이름을 선택합니다. 메뉴 옆에 있는 **[!UICONTROL 휴지통]** 아이콘을 누른 다음 **[!UICONTROL 삭제]**&#x200B;를 누릅니다.

1. 이름 텍스트 필드에 핫스팟 또는 이미지 맵의 이름을 입력합니다. 이 이름은 **[!UICONTROL 맵 및 핫스팟]** 드롭다운 목록에도 나타납니다. 이름을 입력하면 나중에 핫스팟 또는 이미지 맵을 변경하기로 결정하는 경우 핫스팟이나 이미지 맵을 쉽게 식별할 수 있습니다.
1. **[!UICONTROL 작업]** 탭에서 다음 중 하나를 수행합니다.

   * **[!UICONTROL 빠른 보기]**&#x200B;를 누릅니다.

      * Experience Manager 사이트 <!-- and Ecommerce--> 고객인 경우 제품 피커 아이콘(확대경)을 눌러 제품 선택 페이지를 엽니다. 회전판 배너 편집기로 돌아가려면 사용할 제품을 누른 다음 페이지의 오른쪽 상단에 있는 확인 표시를 누릅니다.
      * Experience Manager 사이트 <!-- or Ecommerce --> 고객이 아닌 경우:

         * 변수를 정의합니다. [핫스팟 변수 확인](#identifying-hotspot-and-image-map-variables)을 참조하십시오.
         * 그런 다음 SKU 값을 직접 입력합니다. SKU 값 텍스트 필드에 제공하는 각 고유 제품 또는 서비스에 대한 고유 식별자인 제품의 SKU(Stock Keeping Unit)를 입력합니다. 입력한 SKU 값은 시스템이 탭한 핫스팟을 특정 SKU의 [빠른 보기]와 연관시키는 것을 알 수 있도록 빠른 보기 템플릿의 변수 부분을 자동으로 채웁니다.
         * (선택 사항) 제품을 추가로 식별하기 위해 사용해야 하는 다른 변수가 빠른 보기에 있는 경우 **[!UICONTROL 일반 변수 추가]**&#x200B;를 탭합니다. 텍스트 필드에서 추가 변수를 지정합니다. 예를 들어 category=Mens는 추가된 변수입니다.

         * 자세한 내용은 [선택기 작업](/help/assets/dynamic-media/working-with-selectors.md)을 참조하십시오.
   * **[!UICONTROL 하이퍼링크]**&#x200B;를 누릅니다.

      * AEM Sites 고객인 경우 사이트 선택기 아이콘(폴더)을 탭하여 URL로 이동합니다.

         >[!NOTE]
         인터랙티브한 컨텐츠에 상대 URL, 특히 AEM Sites 페이지로 연결되는 링크가 있는 경우에는 URL 기반 연결 방법을 사용할 수 없습니다.

      * 독립형 고객인 경우 href 텍스트 필드에 연결된 웹 페이지의 전체 URL 경로를 지정합니다.

   링크를 새 브라우저 탭에서 열지(권장 기본값), 아니면 동일한 탭에서 열지 지정합니다.

   자세한 내용은 [선택기 작업](/help/assets/dynamic-media/working-with-selectors.md)을 참조하십시오.

   * **[!UICONTROL 경험 조각]**&#x200B;을 탭합니다.

      * AEM Sites 고객인 경우 검색 아이콘(확대경)을 눌러 경험 조각 페이지를 엽니다. 핫스팟 관리 페이지로 돌아가려면 사용할 경험 조각을 탭하거나 클릭한 다음 페이지의 오른쪽 위 모서리에서 선택을 탭합니다.
[경험 조각](/help/sites-cloud/authoring/fundamentals/experience-fragments.md)을 참조하십시오.

      * 배너에 나타나는 경험 조각의 폭과 높이를 지정합니다.

         >[!NOTE]
         Carousel 배너의 소셜 미디어 공유 도구는 경험 조각에 뷰어를 포함할 때 지원되지 않습니다.
         이 문제를 해결하려면 소셜 미디어 공유 도구가 없는 뷰어 사전 설정을 사용하거나 만들 수 있습니다. 이러한 뷰어 사전 설정을 사용하여 경험 조각에 성공적으로 포함할 수 있습니다.
   ![experience_fragment-carousselbanner](assets/experience_fragment-carouselbanner.png)

   회전판 배너의 모양을 미리 볼 수도 있습니다. [(선택 사항) 회전판 배너 미리 보기](#optional-previewing-carousel-banners)를 참조하십시오.

1. **[!UICONTROL 저장]**&#x200B;을 누릅니다.
1. 회전판 세트를 게시합니다. 게시를 사용하면 웹 사이트 페이지에서 사용할 수 있는 포함 코드 또는 URL이 만들어집니다. Experience Manager 사이트 고객인 경우 회전판 세트를 웹 페이지에 직접 추가합니다.

   [자산 게시](/help/assets/dynamic-media/publishing-dynamicmedia-assets.md)를 참조하십시오.

   웹 사이트 랜딩 페이지에 설정된 회전판 추가](#adding-a-carousel-banner-to-your-website-page)를 참조하십시오.[

## 회전판 편집 세트 {#editing-carousel-sets}

>[!NOTE]
캐러셀 배너를 만들거나 편집할 수 있으려면 관리자가 아닌 사용자를 **[!UICONTROL dam-users]** 그룹에 추가해야 합니다. 만들거나 편집하는 데 문제가 있는 경우 **[!UICONTROL dam-users]** 그룹에 추가할 수 있는 시스템 관리자를 참조하십시오.

다음과 같은 회전판 세트에서 다양한 편집 작업을 수행할 수 있습니다.

* 슬라이드 세트를 회전판 세트에 추가합니다. [선택기 작업](/help/assets/dynamic-media/working-with-selectors.md)을 참조하십시오.
* 회전판 세트에서 슬라이드의 순서를 변경합니다.
* 회전판 세트에서 자산을 삭제합니다.
* 뷰어 사전 설정을 적용합니다.
* 회전판 세트를 삭제합니다.
* 핫스팟 및 이미지 맵을 추가하거나 편집합니다. [선택기 작업](/help/assets/dynamic-media/working-with-selectors.md)을 참조하십시오.

**회전판 세트를 편집하려면**

1. 다음 중 하나를 수행합니다.

   * 회전판 세트 에셋을 마우스로 가리킨 다음 **[!UICONTROL 편집]**(연필 아이콘)을 누릅니다.
   * 회전판 세트 자산 위로 마우스를 가져간 다음 **[!UICONTROL 선택]**(확인 표시 아이콘)을 누른 다음 도구 모음에서 **[!UICONTROL 편집]**&#x200B;을 누릅니다.

   * 회전판 세트 자산을 탭한 다음, 페이지의 왼쪽 위 모서리에서 **[!UICONTROL 편집]** (연필 아이콘)을 탭합니다.

1. 회전판 세트를 편집하려면 다음 중 하나를 수행합니다.

   * 슬라이드를 추가하려면 **[!UICONTROL 슬라이드 추가]** 아이콘을 누른 다음 해당 슬라이드에 추가할 자산으로 이동한 다음 확인 표시를 누르거나 클릭합니다.
   * 슬라이드를 다시 정렬하려면 슬라이드를 새 위치로 드래그합니다(항목을 이동하려면 순서 변경 아이콘 선택).
   * 핫스팟 또는 이미지 맵을 추가하려면 핫스팟 또는 이미지 맵 아이콘을 클릭하고 [핫스팟 및 이미지 맵 추가](#adding-hotspots-or-image-maps-to-an-image-banner)를 참조하십시오.
   * 회전판 세트의 모양이나 동작을 편집하려면 **[!UICONTROL 모양]** 탭 또는 **[!UICONTROL 동작]** 탭을 누른 다음 원하는 옵션을 설정합니다.
   * 핫스팟 또는 이미지 맵을 편집하려면 해당 슬라이드에서 핫스팟 또는 이미지 맵을 선택합니다. **[!UICONTROL 액션]** 탭에서 변경합니다.
   * 슬라이드를 삭제하려면 슬라이드를 선택한 다음 도구 모음에서 **[!UICONTROL 슬라이드 삭제]**&#x200B;를 누릅니다.
   * 사전 설정을 적용하려면 페이지의 오른쪽 위 모서리 근처에 있는 **[!UICONTROL 사전 설정]** 드롭다운 목록을 누른 다음 뷰어 사전 설정을 선택합니다.
   * 전체 캐러셀 세트를 삭제하려면 캐러셀 세트로 이동하여 선택한 다음 **[!UICONTROL 삭제]**&#x200B;를 누릅니다.

   >[!NOTE]
   핫스팟이 있는 대화형 이미지를 편집하고 이미지를 자르면 핫스팟이 제거됩니다.

## (선택 사항) 회전판 배너 미리 보기 {#optional-previewing-carousel-banners}

미리 보기를 사용하여 고객의 Carousel 배너의 모양을 확인하고 Carousel 배너 핫스팟 및 이미지 맵을 테스트하여 예상대로 작동하는지 확인할 수 있습니다.

캐러셀 배너가 마음에 들면 게시할 수 있습니다.
[웹 페이지에 비디오 또는 이미지 뷰어 포함](/help/assets/dynamic-media/embed-code.md)을 참조하십시오.
[웹 응용 프로그램에 URL 연결](/help/assets/dynamic-media/linking-urls-to-yourwebapplication.md)을 참조하십시오. 인터랙티브한 컨텐츠에 상대 URL, 특히 AEM Sites 페이지로 연결되는 링크가 있는 경우에는 URL 기반 연결 방법을 사용할 수 없습니다.
[페이지에 Dynamic Media 자산 추가를 참조하십시오.](/help/assets/dynamic-media/adding-dynamic-media-assets-to-pages.md)

캐러셀 편집기(기본 설정 메서드) 또는 **[!UICONTROL 뷰어]** 목록에서 캐러셀 배너를 미리 볼 수 있습니다.

**캐러셀 배너를 미리 보려면**

1. **[!UICONTROL 자산]**&#x200B;에서 만든 기존 캐러셀 배너를 탐색하고 탭하여 엽니다.
1. **[!UICONTROL 편집]**&#x200B;을 누릅니다.
1. 도구 모음 오른쪽 모서리의 뷰어 사전 설정 목록에서 회전식 배너를 미리 볼 뷰어를 선택합니다.

   ![experience_fragment-carousselbanner-viewerdropdown](assets/experience_fragment-carouselbanner-viewerdropdown.png)

1. **[!UICONTROL 미리 보기]**&#x200B;를 누릅니다.
1. 연결된 동작을 테스트하려면 이미지의 핫스팟 또는 이미지 맵을 누릅니다.

**뷰어 목록에서 캐러셀 배너를 미리 보려면**

1. **[!UICONTROL 자산]**&#x200B;에서 만든 기존 캐러셀 배너를 탐색하고 탭하여 엽니다.
1. 미리 보기 페이지의 왼쪽 위 모서리 근처에 있는 콘텐츠 아이콘을 클릭합니다.
1. 페이지 왼쪽에 있는 패널의 **[!UICONTROL 뷰어]** 목록에서 사용하려는 회전식 배너 뷰어 사전 설정의 이름을 누릅니다.
1. 연결된 동작을 테스트하려면 이미지의 핫스팟 또는 이미지 맵을 누릅니다.

## 회전판 배너 게시 중 {#publishing-carousel-banners}

회전판을 게시하여 사용합니다. 회전판 세트를 게시하면 URL 및 포함 코드가 활성화됩니다. 또한 확장 가능한 성능 전달을 위해 CDN과 통합된 Dynamic Media 클라우드에 Carousel을 게시합니다.

>[!NOTE]
회전판 배너의 핫스팟이 있는 기존 대화형 이미지를 사용하는 경우 회전판 배너를 게시한 후 대화형 이미지를 별도로 게시해야 합니다.
또한 회전판 배너에서 사용 중인 이전에 게시된 대화형 이미지를 수정하는 경우 해당 변경 사항이 캐러셀 배너에 반영되기 전에 대화형 이미지를 게시해야 합니다.

회전판 배너를 게시하는 방법에 대한 자세한 내용은 [Dynamic Media 자산 게시](/help/assets/dynamic-media/publishing-dynamicmedia-assets.md)를 참조하십시오.

## 웹 사이트 페이지에 회전판 배너 추가 {#adding-a-carousel-banner-to-your-website-page}

배너 이미지를 업로드하여 캐러셀, 추가된 핫스팟 또는 이미지 맵 또는 둘 다를 배너에 만듭니다. 회전판 세트를 게시했습니다. 이제 기존 웹 사이트 페이지에 추가할 준비가 되었습니다.

>[!NOTE]
AEM Sites 고객인 경우 Interactive Media 구성 요소를 페이지로 드래그하여 회전판 배너를 페이지에 직접 추가할 수 있습니다. [페이지에 Dynamic Media 자산 추가를 참조하십시오.](/help/assets/dynamic-media/adding-dynamic-media-assets-to-pages.md)

그러나 독립 실행형 Experience Manager 자산 고객의 경우 이 주제의 설명에 따라 캐러셀 배너를 웹 사이트 랜딩 페이지에 수동으로 추가할 수 있습니다.

1. 게시된 Carousel 세트의 포함 코드를 복사합니다.
[웹 페이지에 비디오 또는 이미지 뷰어 포함](/help/assets/dynamic-media/embed-code.md)을 참조하십시오.

1. Experience Manager 자산에서 복사한 포함 코드를 웹 페이지에 추가합니다.
복사한 포함 코드는 응답형으로 작동하므로 페이지의 포함 영역에 자동으로 일치합니다.

## 회전판 배너를 기존 빠른 보기 {#integrating-the-carousel-banner-with-an-existing-quickview}와 통합

참고:이 단계는 독립 실행형 AEM Assets 고객인 경우에만 적용됩니다.

이 프로세스의 마지막 단계는 캐러셀 배너를 웹 사이트의 기존 빠른 보기 구현과 통합하는 것입니다. 모든 빠른 보기 구현은 고유하며 일반적으로 프런트 엔드 IT 담당자의 지원을 필요로 하는 특정 접근 방식이 필요합니다.

기존 빠른 보기 구현은 일반적으로 웹 페이지에서 다음 순서로 발생하는 관련 간 작업 체인을 나타냅니다.

1. 사용자는 웹 사이트의 사용자 인터페이스에서 요소를 트리거합니다.
1. 프런트 엔드 코드는 1단계에서 트리거된 사용자 인터페이스 요소를 기반으로 빠른 보기 URL을 가져옵니다.
1. 프런트 엔드 코드는 2단계에서 얻은 URL을 사용하여 Ajax 요청을 전송합니다.
1. 백엔드 로직은 해당 빠른 보기 데이터 또는 컨텐츠를 프런트 엔드 코드로 다시 반환합니다.
1. 프런트 엔드 코드는 빠른 보기 데이터 또는 컨텐츠를 로드합니다.
1. 선택적으로, 프런트 엔드 코드는 로드된 빠른 보기 데이터를 HTML 표현으로 변환합니다.
1. 프런트 엔드 코드는 모달 대화 상자나 패널을 표시하고 최종 사용자를 위해 화면에 HTML 컨텐츠를 렌더링합니다.

이러한 호출은 임의의 단계에서 웹 페이지 로직에서 호출할 수 있는 독립 공개 API 호출을 나타내지 않습니다. 대신, 이전 단계의 마지막 단계(콜백)에서 모든 다음 단계가 숨겨지는 연쇄 호출입니다.

캐러셀 배너가 1단계와 2단계를 부분적으로 바꾸는 동시에 사용자가 캐러셀 배너 내에서 핫스팟 또는 이미지 맵을 클릭하면 이러한 사용자 상호 작용이 뷰어에 의해 처리됩니다. 뷰어는 이전에 추가한 모든 핫스팟 또는 이미지 맵 데이터를 포함하는 웹 페이지에 이벤트를 반환합니다.

이러한 이벤트 핸들러에서 프런트 엔드 코드는 다음을 수행합니다.

* 캐러셀 배너에서 방출되는 이벤트를 수신합니다.
* 핫스팟 또는 이미지 맵 데이터를 기반으로 빠른 보기 URL을 구성합니다.
* 백엔드 보기에서 빠른 보기를 로드하고 화면에 표시하여 표시합니다.

AEM Assets에서 반환한 포함 코드에는 이미 댓글이 달린 즉시 사용할 수 있는 이벤트 핸들러가 있습니다.

따라서 코드의 주석을 해제하고 더미 핸들러 본문을 특정 웹 페이지에 맞는 코드로 교체해야 합니다.

빠른 보기 URL을 구성하는 프로세스는 앞서 설명한 핫스팟 및 이미지 맵 변수를 식별하는 데 사용되는 프로세스와 반대됩니다.

[핫스팟 및 이미지 맵 변수 확인](#identifying-hotspot-and-image-map-variables)을 참조하십시오.

빠른 보기 URL을 트리거하고 빠른 보기 패널을 활성화하는 마지막 단계는 대부분 IT 부서의 프런트 엔드 IT 담당자의 지원이 필요합니다. 바로 사용할 수 있는 빠른 보기 URL을 사용하여 적절한 단계에서 빠른 보기 구현을 정확하게 트리거하는 방법을 잘 알고 있습니다.

## 빠른 보기를 사용하여 사용자 정의 팝업 창 {#using-quickviews-to-create-custom-pop-ups} 만들기

[빠른 보기를 사용하여 사용자 정의 팝업 창 만들기](/help/assets/dynamic-media/custom-pop-ups.md)를 참조하십시오.