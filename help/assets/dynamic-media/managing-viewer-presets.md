---
title: 뷰어 사전 설정 관리
description: Dynamic Media에서 뷰어 사전 설정을 만들고 관리하는 방법을 알아봅니다.
contentOwner: Rick Brough
feature: Viewer Presets,Viewers
role: User
exl-id: da2e1a10-f54b-440e-b70c-f04ad4caeac1
source-git-commit: f6162dcbc5b7937d55922e8c963a402697110329
workflow-type: tm+mt
source-wordcount: '4326'
ht-degree: 8%

---

# 뷰어 사전 설정 관리{#managing-viewer-presets}

뷰어 사전 설정은 사용자가 컴퓨터 화면 및 모바일 장치에서 리치 미디어 에셋을 보는 방법을 결정하는 설정 컬렉션입니다. 관리자는 뷰어 사전 설정을 만들 수 있습니다. 설정은 뷰어 구성 옵션 배열에 사용할 수 있습니다. 예를 들어 뷰어 표시 크기나 확대/축소 동작을 변경할 수 있습니다.

<!-- OBSOLETE SDK withdrawn from public view. Available internally only at `http://staging.scene7.com/s7sdk/3.8/docs/jsdoc/symbols/_s7sdk.html` 

For instructions on creating and customizing your own HTML5 viewer presets, see the *Adobe Scene7 HTML5 Viewer SDK*. The SDK is available on the IS publish server embedded in the SDK itself. Each library version has its own SDK documentation included.

Path: `<scene7_domain>/s7sdk/<library_version>/docs/jsdocs/index.html`.
For example, 3.5 SDK: [https://s7d1.scene7.com/s7sdk/3.5/docs/jsdoc/index.html](https://s7d1.scene7.com/s7sdk/3.5/docs/jsdoc/index.html)

-->

다음 항목도 참조하십시오. [Dynamic Media 뷰어 참조 안내서](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources.html).

이 섹션에서는 뷰어 사전 설정을 만들고, 편집하고, 관리하는 방법에 대해 설명합니다. 자산을 미리 볼 때마다 뷰어 사전 설정을 적용할 수 있습니다. 다음을 참조하십시오 [뷰어 사전 설정 적용](#applying-a-viewer-preset-to-an-asset).

>[!NOTE]
>
>모두 편집 *사전 정의된 기본 뷰어 사전 설정* 은(는) 지원되지 않는 시나리오입니다. 기본 뷰어 사전 설정을 편집하려고 하면 새 이름을 사용하여 뷰어 사전 설정을 저장하라는 메시지가 표시됩니다.

## 뷰어를 위한 키보드 접근성 {#keyboard-accessibility-for-viewers}

모든 기본 뷰어는 키보드 접근성을 지원합니다.

참조: [키보드 접근성 및 탐색](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/c-keyboard-accessibility.html).

## 뷰어 사전 설정 관리 {#managing-viewer-presets-1}

로 이동하여 Adobe Experience Manager에서 뷰어 사전 설정을 추가, 편집, 삭제, 게시, 게시 취소 및 미리 볼 수 있습니다. **[!UICONTROL 도구]** (망치 아이콘) > **[!UICONTROL 에셋] > [!UICONTROL 뷰어 사전 설정]**.

![6_5_tools-assets-viewerpresets](assets/6_5_tools-assets-viewerpresets.png)

>[!NOTE]
>
>에셋의 세부 사항 보기에서 뷰어 를 선택하면 기본적으로 15개의 뷰어 사전 설정이 표시됩니다. You can increase this limit. 다음을 참조하십시오 [표시되는 뷰어 사전 설정 수 늘리기](#increasing-the-number-of-viewer-presets-that-display).

### 응답형 디자인 웹 페이지에 대한 뷰어 지원 {#viewer-support-for-responsive-designed-web-pages}

웹 페이지마다 요구 사항이 다릅니다. 예를 들어 별도의 브라우저 창에서 HTML 5 뷰어를 여는 링크를 제공하는 웹 페이지를 원하는 경우가 있습니다. 다른 경우에는 호스팅 페이지에 HTML5 뷰어를 직접 임베드해야 합니다. 후자의 경우 웹 페이지에는 정적 레이아웃이 있습니다. 또는 &quot;응답형&quot;이며 디바이스마다 또는 브라우저 창 크기마다 다르게 표시됩니다. 이러한 요구 사항을 수용하기 위해 Dynamic Media과 함께 제공되는 사전 정의된 모든 기본 제공 HTML5 뷰어는 정적 웹 페이지와 반응형 디자인 웹 페이지를 모두 지원합니다.

다음을 참조하십시오 [응답형 정적 이미지 라이브러리](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/responsive-static-image-library/c-about-responsive-static-image-library.html#about-responsive-image-library) 다음에서 *Dynamic Media 이미지 제공 및 렌더링 API 도움말* 반응형 뷰어를 웹 페이지에 임베드하는 방법에 대한 자세한 내용.

>[!NOTE]
>
>처음 사용하기 전에 모든 기본 뷰어를 게시하십시오.
>다음을 참조하십시오 [뷰어 사전 설정 게시](#publishing-viewer-presets).

### 뷰어 사전 설정 시스템 호환성  {#viewer-preset-system-compatibility}

Dynamic Media과 함께 제공되는 모든 기본 뷰어 사전 설정은 다음 시스템과 완전히 호환됩니다.

* 데스크탑
* Apple iPhone
* Apple iPad
* Android™ 스마트폰
* Android™ 태블릿
<!-- OUTDATED 2/25/22 * For video, extra support for MP4 playback is provided for [BlackBerry&reg;](https://developer.blackberry.com/devzone/develop/supported_media/bb_media_support_at_a_glance.html#kba1328730952678) and [Windows&reg; Phone](https://docs.microsoft.com/en-us/windows/uwp/audio-video-camera/supported-codecs). -->

### 뷰어 사전 설정에 대한 리치 미디어 유형 {#rich-media-types-for-viewer-presets}

관리자는 뷰어 사전 설정을 만들 때 다음 리치 미디어 유형을 추가하고 사용자 지정할 수 있습니다.

<table>
 <tbody>
  <tr>
   <td><strong>회전 메뉴 세트</strong><br /> </td>
   <td><p>핫스팟, 이미지 맵 또는 두 이미지 모두 둘 이상의 일련의 이미지에 추가됩니다. 고객은 이미지를 왼쪽 또는 오른쪽으로 패닝한 다음 이미지에 대한 핫스팟을 선택하여 자세한 내용을 확인하거나 웹 사이트의 랜딩, 카테고리 또는 홈페이지에서 바로 구매할 수 있습니다.</p> </td>
  </tr>
    <tr>
   <td><strong>차원</strong><br /> </td>
   <td><p>카메라를 회전, 팬, 확대/축소 또는 다시 가운데로 돌릴 수 있는 3D 장면을 표시합니다.</p> </td>
  </tr>
  <tr>
   <td><strong>플라이아웃 확대/축소</strong></td>
   <td><p>확대/축소된 영역의 두 번째 이미지를 원본 이미지 옆에 표시합니다. 사용할 컨트롤이 없습니다. 사용자가 보려는 영역 위로 선택 항목을 이동합니다.</p> <p>이 뷰어에 대한 전체 대역폭 사용을 결정할 때 기본 이미지와 플라이아웃 이미지가 모두 뷰어에서 제공된다고 가정해 보십시오. 기본 이미지 크기(스테이지 너비 및 높이)와 확대/축소 비율이 플라이아웃 이미지 크기를 결정합니다. 플라이아웃 파일 크기가 너무 커지지 않도록 하려면 다음 두 값의 균형을 맞추십시오. 기본 이미지 크기가 큰 경우 확대/축소 비율 값을 낮추십시오. [플라이아웃 폭] 및 [플라이아웃 높이]는 플라이아웃 창의 크기를 결정하지만 뷰어에 제공되는 플라이아웃 이미지의 크기는 결정하지 않습니다.</p> <p>예를 들어 기본 이미지 크기가 350 x 350픽셀이고 [확대/축소 비율]이 3인 경우 결과 플라이아웃 이미지는 1050 x 1050픽셀입니다. 기본 이미지 크기가 300 x 300픽셀이고 [확대/축소 비율]이 4인 경우 플라이아웃 이미지는 1200 x 1200픽셀입니다. JPEG 품질 설정(권장 설정은 80~90 사이)에 따라 파일 크기를 크게 줄일 수 있습니다. 권장 확대/축소 요소는 기본 이미지의 크기에 따라 2.5에서 4입니다.</p> </td>
  </tr>
  <tr>
   <td><strong>인라인 확대/축소</strong></td>
   <td>원본 뷰어 내에서 확대/축소된 영역의 이미지를 표시합니다. 사용할 컨트롤이 없습니다. 즉, 사용자가 보려는 영역 위로 선택 영역을 이동합니다.</td>
  </tr>
  <tr>
   <td><strong>이미지 집합</strong></td>
   <td>이미지 세트 뷰어에서 사용자는 썸네일 이미지를 선택하여 항목의 다양한 보기 또는 색상 변형을 볼 수 있습니다. 또한 이 뷰어에는 이미지를 자세히 검사하기 위한 확대/축소 도구도 제공됩니다.</td>
  </tr>
  <tr>
   <td><strong>대화형 이미지</strong></td>
   <td>핫스팟은 고객이 더 자세한 정보를 확인하거나 웹 사이트의 랜딩, 카테고리 또는 홈페이지에서 바로 구매할 수 있도록 선택할 수 있는 이미지 부분에 추가됩니다.</td>
  </tr>
  <tr>
   <td><strong>대화형 비디오</strong></td>
   <td>썸네일은 고객이 더 자세한 내용을 확인하거나 웹 사이트의 랜딩, 카테고리 또는 홈페이지에서 바로 구매할 수 있도록 비디오의 타임라인 세그먼트에 추가됩니다.</td>
  </tr>
  <tr>
   <td><strong>혼합 미디어</strong></td>
   <td>하나의 뷰어에 서로 다른 유형의 미디어를 표시합니다. 스핀 세트, 이미지 세트, 이미지 및 비디오를 포함할 수 있습니다.</td>
  </tr>
  <tr>
   <td><strong>파노라마 이미지</strong></td>
   <td><p>파노라마 이미지 및 PanoramicVR 뷰어는 구형의 파노라마 이미지를 렌더링하여 사용자가 공간, 속성, 위치 또는 풍경을 360° 뷰잉할 수 있도록 합니다.</p> <p>업로드된 이미지가 구면 파노라마로 적합하려면 다음 중 하나 또는 둘 다 있어야 합니다.</p>
    <ul>
     <li>종횡비는 2:1입니다.</li>
     <li>키워드로 태그 지정됨 <code>equirectangular</code>, 또는 <code>spherical</code> 및 <code>panorama</code>, 또는 <code>spherical </code>및 <code>panoramic</code>. 다음을 참조하십시오 <a href="/help/sites-cloud/authoring/sites-console/tags.md">태그 사용</a>.</li>
    </ul> <p>종횡비와 키워드 기준은 모두 자산 세부 사항 페이지 및 "파노라마 미디어" WCM 구성 요소의 파노라마 자산에 적용됩니다.</p></td>
  </tr>
    <tr>
   <td><strong>스마트 자르기 비디오</strong><br /> </td>
   <td><p>이 뷰어를 사용하여 모든 비디오에서 초점을 자동으로 감지하고 자를 수 있습니다.</p> </td>
  </tr>
  <tr>
   <td><strong>회전 집합</strong></td>
   <td>사용자가 개체를 돌려 서로 다른 변과 각도를 검사할 수 있도록 이미지에 대한 여러 보기를 제공합니다.</td>
  </tr>
  <tr>
   <td><strong>360 비디오</strong></td>
   <td><p>360/VR 비디오 뷰어를 사용하여 공간, 속성, 위치, 풍경 또는 의료 시술을 몰입감 있게 시청할 수 있도록 동일 사각형 비디오를 렌더링합니다.</p> <p>평면 디스플레이에서 재생하는 동안 사용자는 시야각을 제어할 수 있습니다. 모바일 장치에서 재생은 내장된 자이로스코프 컨트롤을 사용합니다.</p> <p>뷰어에는 360개의 비디오 자산 전달에 대한 기본 지원이 포함되어 있습니다. 기본적으로 보거나 재생하기 위해 추가 구성은 필요하지 않습니다. .mp4, .mkv 및 .mov 와 같은 표준 비디오 확장명을 사용하여 360 비디오를 제공합니다. 가장 일반적인 코덱은 H.264입니다.</p> </td>
  </tr>
  <tr>
   <td><strong>비디오</strong></td>
   <td><p>점진적 또는 적응형 비트율 스트리밍을 사용하여 비디오를 재생합니다. 적응형 비트율 스트리밍은 적합한 품질의 비디오를 적합한 포맷으로 제공하기 위해 장치 및 대역폭 검색을 자동으로 수행합니다.</p> </td>
  </tr>
  <tr>
   <td><strong>세로 확대/축소</strong></td>
   <td><p>수직 확대/축소 뷰어를 사용하면 제품 이미지 보기 경험을 최대화하여 사용자에게 제품을 가장 잘 표현할 수 있습니다. 견본의 세로 위치는 다음과 같습니다.</p>
    <ul>
     <li>견본이 "접힌 부분 위에" 있는지 확인합니다.<br/> 수평 견본의 경우 사용자의 데스크탑 화면 크기에 따라 사용자가 페이지를 아래로 스크롤할 때까지 견본이 표시되지 않습니다. 견본을 뷰어에서 세로로 배치하면 사용자의 화면 크기에 상관없이 볼 수 있습니다.</li>
     <li>기본 이미지 크기를 최대화합니다.<br /> 수평 견본을 사용할 경우 페이지가 보이도록 공간을 예약해야 합니다. 이 위치 지정은 기본 이미지의 크기를 줄였습니다. 그러나 수직 견본 레이아웃에서는 이 공간을 할당할 필요가 없습니다. 따라서 기본 이미지 크기를 최대화할 수 있습니다.</li>
    </ul> </td>
  </tr>
  <tr>
   <td><strong>확대/축소</strong></td>
   <td>사용자가 영역을 선택하여 확대할 수 있습니다. 사용자는 이미지를 확대 및 축소하고 기본 크기로 재설정할 컨트롤을 선택할 수 있습니다.</td>
  </tr>
 </tbody>
</table>

### 즉시 사용 가능한 뷰어 사전 설정 목록 {#list-of-out-of-the-box-viewer-presets}

다음 표는 Dynamic Media과 함께 제공되는 사전 정의된 모든 기본 뷰어 사전 설정을 식별합니다.

참조: [라이브 데모](https://landing.adobe.com/en/na/dynamic-media/ctir-2755/live-demos.html).

뷰어에 대해 지원되는 웹 브라우저 및 운영 체제 버전에 대한 자세한 내용은 뷰어 릴리스 정보 를 참조하십시오.

의 목차에서 &quot;뷰어 릴리스 정보&quot;를 참조하십시오. [뷰어 참조 안내서](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources.html).

>[!NOTE]
>
>Dynamic Media의 모든 기본 뷰어 사전 설정은 활성화(설정)되지만 게시해야 합니다.
>다음을 참조하십시오 [뷰어 사전 설정 게시](#publishing-viewer-presets).
>
>만들고 추가하는 새 뷰어 사전 설정은 모두 활성화 *와 *게시되어야 합니다.
>다음을 참조하십시오 [뷰어 사전 설정 활성화 또는 비활성화](#activating-or-deactivating-viewer-presets) 및 [뷰어 사전 설정 게시](#publishing-viewer-presets).

<table>
 <tbody>
  <tr>
   <td><strong>뷰어 사전 설정 제목</strong></td>
   <td><strong>유형</strong></td>
   <td><strong>CSS 파일 이름</strong><br /> </td>
  </tr>
  <tr>
   <td>Carousel_Dotted_dark</td>
   <td>Carousel_Set</td>
   <td><code>html5_carouselviewer_dotted_dark.css</code></td>
  </tr>
  <tr>
   <td>Carousel_Dotted_light</td>
   <td>Carousel_Set</td>
   <td><code>html5_carouselviewer_dotted_light.css</code></td>
  </tr>
  <tr>
   <td>Carousel_Numeric_dark</td>
   <td>Carousel_Set</td>
   <td><code>html5_carouselviewer_numeric_dark.css</code></td>
  </tr>
  <tr>
   <td>Carousel_Numeric_light</td>
   <td>Carousel_Set</td>
   <td><code>html5_carouselviewer_numeric_light.css</code></td>
  </tr>
  <tr>
   <td>플라이아웃</td>
   <td>플라이아웃 확대/축소</td>
   <td><code>html5_flyoutviewer.css</code></td>
  </tr>
  <tr>
   <td>ImageSet_dark</td>
   <td>이미지 집합</td>
   <td><code>html5_zoomviewer_dark.css</code></td>
  </tr>
  <tr>
   <td>ImageSet_light</td>
   <td>이미지 집합</td>
   <td><code>html5_zoomviewer_light.css</code></td>
  </tr>
  <tr>
   <td>InlineMixedMedia_dark</td>
   <td>Mixed_Media</td>
   <td><code>html5_inlinemixedmediaviewer_dark.css</code></td>
  </tr>
  <tr>
   <td>InlineMixedMedia_light</td>
   <td>Mixed_Media</td>
   <td><code>html5_inlinemixedmediaviewer_light.css</code></td>
  </tr>
  <tr>
   <td>InlineZoom</td>
   <td>플라이아웃 확대/축소</td>
   <td><code>html5_inlinezoomviewer.css</code></td>
  </tr>
  <tr>
   <td>MixedMedia_dark</td>
   <td>Mixed_Media</td>
   <td><code>html5_mixedmediaviewer_dark.css</code></td>
  </tr>
  <tr>
   <td>MixedMedia_light</td>
   <td>Mixed_Media</td>
   <td><code>html5_mixedmediaviewer_light.css</code></td>
  </tr>
  <tr>
   <td>PanoramicImage</td>
   <td>Panoramic_Image</td>
   <td><code>html5_panoramicimage.css</code></td>
  </tr>
  <tr>
   <td>파노라마 이미지 VR</td>
   <td>Panoramic_Image</td>
   <td><code>html5_panoramicimage.css</code></td>
  </tr>
  <tr>
   <td>Shopable_Banner</td>
   <td>Interactive_Image</td>
   <td><code>html5_interactiveimage.css</code></td>
  </tr>
  <tr>
   <td>Shoppable_Video_dark</td>
   <td>Interactive_Video</td>
   <td><code>html5_interactivevideoviewer_dark.css</code></td>
  </tr>
  <tr>
   <td>Shoppable_Video_light</td>
   <td>Interactive_Video</td>
   <td><code>html5_interactivevideovewer_light.css</code></td>
  </tr>
  <tr>
   <td>회전 집합 어둡게</td>
   <td>회전 집합</td>
   <td><code>html5_spinviewer_dark.css</code></td>
  </tr>
  <tr>
   <td>SpinSet_light</td>
   <td>회전 집합</td>
   <td><code>html5_spinviewer_light.css</code></td>
  </tr>
  <tr>
   <td><p>비디오</p> <p>(자막 지원 포함)</p> </td>
   <td>비디오</td>
   <td><code>html5_videoviewer.css</code></td>
  </tr>
  <tr>
   <td><p>Video360_social</p> <p>(기본 비디오 재생 컨트롤, 비디오 렌더링은 스테레오 모드에서 수행되며, 수동 POV 컨트롤은 꺼져 있지만 자이로스코프 컨트롤은 켜져 있으며 소셜 미디어 기능이 없음)</p> </td>
   <td>비디오_360</td>
   <td><code>html5_video360viewersocial.css</code></td>
  </tr>
  <tr>
   <td><p>Video360VR</p> <p>(가상 현실 안경을 사용하는 최종 사용자를 위해 설계되었습니다. 기본 비디오 재생 컨트롤 및 소셜 미디어 기능 포함)</p> </td>
   <td>비디오_360</td>
   <td><code>html5_video360viewer.css</code></td>
  </tr>
  <tr>
   <td><p>비디오 소셜</p> <p>(자막 및 소셜 미디어에 대한 지원 포함)</p> </td>
   <td>비디오</td>
   <td><code>html5_videoviewersocial.css</code></td>
  </tr>
  <tr>
   <td>Zoom_dark<br /> </td>
   <td>확대/축소<br /> </td>
   <td><code>html5_basiczoomviewer_dark.css</code></td>
  </tr>
  <tr>
   <td>Zoom_light<br /> </td>
   <td>확대/축소</td>
   <td><code>html5_basiczoomviewer_light.css</code></td>
  </tr>
  <tr>
   <td>ZoomVertical_dark<br /> </td>
   <td>Vertical_Zoom</td>
   <td><code>html5_zoomverticalviewer_dark.css</code></td>
  </tr>
  <tr>
   <td>ZoomVertical_light</td>
   <td>Vertical_Zoom</td>
   <td><code>html5_zoomverticalviewer_light.css</code></td>
  </tr>
 </tbody>
</table>

### 지원되는 모바일 뷰어 제스처 매트릭스 {#supported-mobile-viewers-gestures-matrix}

다음 표에서는 iOS, Android™ 2.x 및 Android™ 3.x 장치에서 지원되는 모바일 뷰어 제스처를 식별합니다.

<table>
 <tbody>
  <tr>
   <td><strong>제스처</strong></td>
   <td><strong>플라이아웃 확대/축소</strong></td>
   <td><strong>확대/축소</strong></td>
   <td><strong>회전</strong></td>
  </tr>
  <tr>
   <td><p><strong>드래그</strong></p> </td>
   <td><p>팬</p> </td>
   <td><p>팬</p> </td>
   <td><p>팬</p> </td>
  </tr>
  <tr>
   <td><p><strong>선택</strong></p> </td>
   <td><p>플라이아웃 창 표시</p> </td>
   <td><p>사용자 인터페이스를 표시하거나 숨깁니다.</p> </td>
   <td><p>사용자 인터페이스를 표시하거나 숨깁니다.</p> </td>
  </tr>
  <tr>
   <td><p><strong>두 번 선택</strong></p> </td>
   <td><p>적용되지 않음</p> </td>
   <td><p>확대 또는 재설정</p> </td>
   <td><p>확대 또는 재설정</p> </td>
  </tr>
  <tr>
   <td><p><strong>핀치 오픈</strong></p> </td>
   <td><p>적용되지 않음</p> </td>
   <td><p>확대(iOS 및 Android™ 3x만 해당)</p> </td>
   <td><p>확대(iOS 및 Android™ 3x만 해당)</p> </td>
  </tr>
  <tr>
   <td><p><strong>핀치 클로즈</strong></p> </td>
   <td><p>적용되지 않음</p> </td>
   <td><p>축소(iOS 및 Android™ 3x만 해당)</p> </td>
   <td><p>축소(iOS 및 Android™ 3x만 해당)</p> </td>
  </tr>
  <tr>
   <td><p><strong>살짝 밀기</strong></p> </td>
   <td><p>견본 막대 스크롤</p> </td>
   <td><p>이미지 스크롤</p> </td>
   <td><p>회전</p> </td>
  </tr>
  <tr>
   <td><p><strong>긋기</strong></p> </td>
   <td><p>견본 막대 스크롤</p> </td>
   <td><p>이미지 스크롤</p> </td>
   <td><p>회전</p> </td>
  </tr>
 </tbody>
</table>

## 표시되는 뷰어 사전 설정 수 늘리기 {#increasing-the-number-of-viewer-presets-that-display}

Experience Manager은에서 에셋을 볼 때 매우 다양한 뷰어 사전 설정을 보여 줍니다. **[!UICONTROL 세부 사항 보기]** > **[!UICONTROL 뷰어]**. 표시되는 뷰어의 수를 늘리거나 줄일 수 있습니다.

**표시되는 뷰어 사전 설정 수를 늘리려면 다음을 수행합니다.**

1. CRXDE Lite([https://localhost:4502/crx/de](https://localhost:4502/crx/de)).
1. 다음에서 뷰어 사전 설정 나열 노드로 이동합니다. `/libs/dam/gui/coral/content/commons/sidepanels/viewerpresets/viewerpresetslist`

   ![chlimage_1-221](/help/assets/dynamic-media/assets/chlimage_1-221.png)

1. In the **[!UICONTROL limit]** property, change the **[!UICONTROL Value]**, which is set to 15 by default, to the desired number.
1. 다음에서 뷰어 사전 설정 데이터 소스로 이동합니다. `/libs/dam/gui/coral/content/commons/sidepanels/viewerpresets/viewerpresetslist/datasource`

   ![chlimage_1-222](/help/assets/dynamic-media/assets/chlimage_1-222.png)

1. limit 속성에서 숫자를 원하는 숫자로 변경합니다(예: ). `{empty requestPathInfo.selectors[1] ? "20" : requestPathInfo.selectors[1]}`
1. 선택 **[!UICONTROL 모두 저장]**.

## 뷰어 사전 설정 만들기 {#creating-a-new-viewer-preset}

뷰어 사전 설정을 만들면 다양한 설정을 적용하여 에셋을 보고 상호 작용할 수 있습니다. 그러나 뷰어 사전 설정을 만들 필요는 없습니다. 원하는 경우 Experience Manager Assets과 함께 이미 제공되는 기본 기본 뷰어 사전 설정을 사용할 수 있습니다.

뷰어 사전 설정을 만들도록 선택하면 저장한 후 뷰어의 상태가 자동으로 활성화됩니다( 로 설정) **[!UICONTROL 날짜]**)을 클릭하여 검색할 수 있습니다. 이 상태는 Dynamic Media 구성 요소 및 대화형 미디어 구성 요소에서 그리고 이미지나 비디오를 미리 볼 때마다 표시됨을 의미합니다.

일부 뷰어 사전 설정에는 뷰어의 사용 및 전체 동작에 영향을 줄 수 있는 전용 설정이 있습니다. 사용자가 만드는 뷰어 사전 설정에 따라 이러한 특별한 고려 사항을 알고 있어야 합니다.

다음을 참조하십시오 [대화형 뷰어 사전 설정 만들기에 대한 특수 고려 사항](#special-considerations-for-creating-an-interactive-viewer-preset).

다음을 참조하십시오 [회전 메뉴 배너 뷰어 사전 설정 만들기에 대한 특수 고려 사항](#special-considerations-for-creating-a-carousel-banner-viewer-preset).

**뷰어 사전 설정을 만들려면 다음 작업을 수행하십시오.**

1. Experience Manager의 왼쪽 상단 모서리에서 Experience Manager 로고를 선택한 다음 왼쪽 레일에서 **[!UICONTROL 도구]** (망치 아이콘) > **[!UICONTROL 에셋]** > **[!UICONTROL 뷰어 사전 설정]**.

   ![6_5_viewerpresets](assets/6_5_viewerpresets.png)

1. 뷰어 사전 설정 페이지의 도구 모음에서 를 선택합니다 **[!UICONTROL 만들기]**.
1. 다음에서 **[!UICONTROL 새 뷰어 사전 설정]** 대화 상자, **[!UICONTROL 사전 설정 이름]** 필드에 새 사전 설정의 이름을 입력합니다. 이름을 신중하게 선택하십시오. 선택한 후에는 편집할 수 없습니다 **[!UICONTROL 만들기]**.

   이 단계의 후반부에 사전 설정을 저장하면 이 이름이 [사전 설정 제목] 열 머리글 아래의 [뷰어 사전 설정] 페이지에 표시됩니다.

1. 리치 미디어 유형 드롭다운 메뉴에서 만들려는 뷰어 사전 설정 유형을 선택한 다음 페이지의 오른쪽 상단 모서리에서 을(를) 선택합니다 **[!UICONTROL 만들기]**.

   다음을 참조하십시오 [뷰어 사전 설정에 대한 리치 미디어 유형](#rich-media-types-for-viewer-presets).

1. 뷰어 사전 설정 편집기 페이지에서 **[!UICONTROL 모양]** 탭.
1. 다음 중 하나를 수행하십시오.

   * 다음에서 **[!UICONTROL 선택한 유형]** 풀다운 메뉴에서 시각적 디자인을 사용자 지정할 구성 요소를 선택합니다. 또는 뷰어에서 시각적 요소를 선택하여 구성할 수 있습니다.

     시각적 편집기를 사용하면 특정 속성이 스타일에 어떤 영향을 미치는지 확인할 수 있습니다. 편집기 왼쪽에 있는 샘플을 사용하여 뷰어에 미치는 영향을 즉시 확인할 수 있도록 모든 속성을 설정하거나 조정합니다.

     각 뷰어 사전 설정 유형에 대한 CSS 스타일 속성은 &quot;사용자 지정&quot;에 설명되어 있습니다. *`<viewer name>`* 의 &quot;뷰어&quot; 도움말 항목 [뷰어 참조 안내서](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources.html). 예를 들어 유형의 뷰어 사전 설정을 만드는 경우 `Mixed_Media`, 참조 [혼합 미디어 뷰어 사용자 지정](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-aem-assets-dmc/mixed-media/customing-mixed-media/c-html5-mixedmedia-viewer-customizingviewer.html) 각 속성의 목록 및 설명.

   * 별도의 CSS 파일에 스타일 설정을 정의한 경우 CSS 파일을 Experience Manager Assets에 업로드할 수 있습니다. 업로드된 CSS 파일을 찾아 뷰어 사전 설정과 연결하려면 을 선택합니다. **[!UICONTROL CSS 가져오기]** 아래 **[!UICONTROL 선택한 유형]** 풀다운 메뉴(필요한 경우 시각적 편집기를 위로 스크롤하여 확인).

     CSS 파일을 가져올 때 시각적 편집기는 CSS가 올바른 뷰어 마커를 사용하는지 확인합니다. 예를 들어 확대/축소 뷰어를 만드는 경우 가져오는 모든 CSS 규칙은 뷰어 클래스 이름을 사용하여 정의해야 합니다 `.s7mixedmediaviewer` 상위 뷰어 요소에 정의됩니다.

     지정된 뷰어에 대한 CSS 마커를 올바르게 정의하는 한 임의의 수제 CSS를 가져올 수 있습니다. (CSS 마커는 &quot;사용자 정의&quot;에 설명되어 있습니다. *&lt;viewer name=&quot;&quot;>* 의 &quot;뷰어&quot; 도움말 항목 [뷰어 참조 안내서](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources.html). 예를 들어 [확대/축소 뷰어]에 대한 CSS 마커를 읽으려면 다음을 참조하십시오. [확대/축소 뷰어 사용자 지정](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-aem-assets-dmc/zoom/customizing-zoom/c-html5-20-zoom-viewer-customizingviewer.html).) 그러나 시각적 편집기가 일부 CSS 값을 이해하지 못할 수 있습니다. 이러한 경우 시각적 편집기는 CSS가 여전히 작동할 수 있도록 오류를 재정의하려고 합니다.

   >[!NOTE]
   >
   >원시 양식에서 CSS를 직접 편집하려면 다음을 선택합니다. **[!UICONTROL CSS 표시/숨기기]** 선택한 유형 풀다운 메뉴 아래에서 필요한 경우 시각적 편집기를 위로 스크롤하여 봅니다.
   >시각적 편집기와 마찬가지로 CSS에서 속성을 직접 변경하면 뷰어 샘플에 어떤 영향을 미치는지 즉시 확인할 수 있습니다. 또한 동일한 속성은 시각적 편집기에서 동시에 자동으로 업데이트됩니다. 따라서 원시 CSS 편집기 또는 시각적 편집기를 사용하거나 두 편집기를 서로 교환하여 사용할 수 있습니다.

   >[!NOTE]
   >
   >단추 아트워크의 경우 2x 이미지를 선택하고 고해상도 아트 작품을 업로드합니다. 대화형 이미지 및 구매 가능한 배너를 사용하여 작업할 때 다양한 기본 핫스팟 단추 중에서 선택할 수도 있습니다.

1. (선택 사항) 뷰어 사전 설정 편집 페이지 상단 근처에서 을 선택합니다 **[!UICONTROL 데스크탑]**, **[!UICONTROL 태블릿]**, 또는 **[!UICONTROL 전화]** 서로 다른 장치 및 화면 유형에 대한 시각적 스타일을 고유하게 정의합니다.
1. 뷰어 사전 설정 편집기 페이지에서 **[!UICONTROL 비헤이비어]** 탭. 또는 뷰어에서 시각적 요소를 선택하여 구성할 수 있습니다.
예: *VideoPlayer* 입력, 아래 **[!UICONTROL 수정자]** > **[!UICONTROL 재생]**, 다음 세 가지 적응형 비트율 스트리밍 옵션 중 하나를 선택할 수 있습니다.

   * **[!UICONTROL 대시]** - 비디오가 DASH로만 스트리밍됩니다. 그러나 Safari/iOS 장치에서 다음을 선택해야 합니다. **[!UICONTROL hls]** 를 유형으로 사용하십시오.
   * **[!UICONTROL hls]** - 비디오는 HLS로만 스트리밍됩니다.
   * **[!UICONTROL auto]** - 우수 사례 DASH 및 HLS 스트림의 생성은 저장 최적화된 것이다. 따라서 Adobe은 항상 을 선택할 것을 권장합니다. **[!UICONTROL auto]** 를 재생 유형으로 사용하십시오. 비디오는 다음과 같이 대시, hls 또는 점진적으로 스트리밍됩니다.
      * 브라우저가 DASH를 지원하는 경우 먼저 DASH 스트리밍이 사용됩니다.
      * 브라우저가 DASH를 지원하지 않으면 HLS 스트리밍이 두 번째로 사용됩니다.
      * 브라우저가 DASH 또는 HLS를 지원하지 않으면 마지막으로 점진적 재생이 사용됩니다.

   >[!NOTE]
   >
   >을(를) 보고 사용하려면 **[!UICONTROL 대시]** 옵션은 먼저 계정에 대한 기술 지원 Adobe에서 활성화해야 합니다. 다음을 참조하십시오 [계정에서 DASH 활성화](/help/assets/dynamic-media/video.md#enable-dash).

1. From the **[!UICONTROL Selected Type]** pull-down menu, select a component whose behaviors you want to change.

   시각적 편집기의 많은 구성 요소에는 시각적 편집기와 관련된 자세한 설명이 있습니다. 이러한 설명은 컴포넌트를 확장하여 연관된 매개변수를 표시할 때 파란색 상자 내에 나타납니다.

   Some Viewer types have components that let you specify Image Serving commands in an **[!UICONTROL IS Command]** text field. For a list of commands you can use, see the [Image Serving API Reference](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/c-is-home.html).

   >[!NOTE]
   >
   >**휴대폰 또는 태블릿과 같은 터치 장치를 사용하는 경우...**
   >
   >
   >텍스트 필드에 값을 입력한 후 사용자 인터페이스의 다른 위치를 선택하여 변경 사항을 제출하고 가상 키보드를 닫습니다. 다음을 선택하는 경우 **[!UICONTROL 입력]**, 아무 작업도 수행되지 않습니다.

1. 페이지의 오른쪽 상단 모서리 근처에서 을 선택합니다. **[!UICONTROL 저장]**.
1. 새 뷰어 사전 설정을 게시합니다. 웹 사이트에서 결과 URL을 사용할 수 있도록 사전 설정을 게시해야 합니다.

   다음을 참조하십시오 [뷰어 사전 설정 게시](#publishing-viewer-presets).

   >[!IMPORTANT]
   >
   >적응형 비트율 스트리밍 프로필을 사용하는 이전 비디오의 경우 URL은 HLS 스트리밍을 사용할 때까지 평소대로 계속 재생됩니다 [비디오 자산 재처리](/help/assets/dynamic-media/about-image-video-profiles.md#reprocessing-assets). 재처리 후에도 동일한 URL이 계속 작동하지만 현재는 *모두* DASH 및 HLS 스트리밍이 활성화되었습니다.

### 대화형 뷰어 사전 설정 만들기에 대한 특수 고려 사항 {#special-considerations-for-creating-an-interactive-viewer-preset}

**패널의 이미지 썸네일에 대한 표시 모드 정보:**

대화형 비디오 뷰어 사전 설정을 만들거나 편집할 때 사용할 디스플레이 모드 설정을 선택할 수 있습니다. 이 선택은 다음을 선택할 때 수행됩니다. `InteractiveSwatches` 다음에서 **[!UICONTROL 선택한 구성 요소]** 아래 풀다운 메뉴 **[!UICONTROL 비헤이비어]** 탭. 선택하는 표시 모드는 비디오가 재생되는 동안 썸네일이 표시되는 방법과 시기에 영향을 줍니다. You can choose either a `segment`Display mode (default) or a `continuous` Display mode.

<table>
 <tbody>
  <tr>
   <td><strong>표시 모드</strong></td>
   <td><strong>설명</strong></td>
  </tr>
  <tr>
   <td>세그먼트</td>
   <td><p><code>Segment </code>는 곧바로 사용할 수 있는 대화형 비디오 뷰어 사전 설정의 기본 표시 모드입니다 <code>Shoppable_Video_light</code> 및 <code>Shoppable_Video_dark</code> 직접 만드는 모든 대화형 비디오 뷰어 사전 설정.</p> <p>이 모드에서 비디오 세그먼트에 할당된 썸네일이 디스플레이 패널에 표시되는 스팟 수보다 적다고 가정합니다. 이러한 경우 다음 또는 이전 하위 세그먼트의 축소판은 다음과 같습니다 <i>아님 </i>을(를) 가져와서 패널의 빈 공간을 채웁니다. 즉, 특정 비디오 세그먼트에 지정된 견본의 표시를 유지합니다.</p> </td>
  </tr>
  <tr>
   <td>연속</td>
   <td><p>위치 <code>continuous </code>디스플레이 모드에서 세그먼트의 썸네일 수가 패널에 표시되는 수보다 적다고 가정합니다. 이러한 경우 뷰어에는 마지막 썸네일이 표시되는 다음 세그먼트 또는 이전 세그먼트의 썸네일 표시가 자동으로 포함됩니다.</p> <p>다음 <a href="/help/assets/dynamic-media/interactive-videos.md">이 항목의 비디오</a> 의 예입니다. <code>continuous </code>표시 모드.</p> </td>
  </tr>
 </tbody>
</table>

**대화형 비디오 뷰어의 자동 스크롤 동작 정보:**

대화형 비디오 뷰어에서 썸네일의 자동 스크롤 동작은 선택한 표시 모드와 독립적으로 작동합니다.

When you create or edit an interactive video viewer preset, you access Auto Scroll from the Behavior tab. 비헤이비어 탭의 **[!UICONTROL 선택한 구성 요소]** 드롭다운 메뉴에서 다음을 선택합니다. **[!UICONTROL 대화형 견본]**. The Auto Scroll check box is listed below the IS Command text field.

If you disable **[!UICONTROL Auto Scroll]** (clear the check box) in the viewer preset, during video playback by the user, the panel only displays the first thumbnail image for the entire length of the video. However, a user can manually scroll through the thumbnails using the up and down arrow icons, if desired.

When you enable (select) **[!UICONTROL Auto Scroll]** in the viewer preset, during video playback, thumbnail images assigned to a video segment scroll into view at the start of a segment. There are instances, however, where certain thumbnails within a segment display twice as long as other thumbnails before or after it. This behavior occurs because the number of thumbnails in a segment is greater than the number that are visible in the panel, and are not evenly divisible.

예를 들어 30초 길이의 비디오 세그먼트가 한 개 있다고 가정해 보겠습니다. 그리고 30초 동안 표시할 축소판은 총 9개입니다. 브라우저의 크기는 디스플레이 패널에 4개의 썸네일 위치가 표시되는 방식으로 조정됩니다. 30초 길이의 비디오 시간 세그먼트는 3개의 서브 세그먼트로 나뉜다. 다음 표는 지정된 시간 하위 세그먼트에 대해 표시되는 썸네일의 분류를 보여 줍니다.

| **비디오 하위 세그먼트** | **하위 세그먼트 시간(초)** | **패널에 표시되는 축소판** |
|---|---|---|
| 1 | 0-10 | 1, 2, 3, 4 |
| 2 | 10-20 | 4, 5, 6, 7 |
| 3 | 20-30 | 6, 7, 8, 9 |

비디오 하위 세그먼트 3은 할당된 축소판 이후로는 확장되지 않습니다. 축소판 4, 6 및 7은 다른 축소판보다 두 배 더 패널에서 볼 수 있습니다.

사용 가능한 위치의 수를 기준으로 패널에 표시되는 썸네일의 수에 대해 뷰어가 사용하는 논리는 다음과 같습니다.

* 하위 세그먼트 수 = 다음 하위 세그먼트로 반올림됩니다(썸네일 수 / 브라우저 창 크기에 따라 썸네일 패널에 표시되는 슬롯 수).
위 표의 예를 사용하여, 9개의 썸네일 / 4개의 슬롯 = 2.25입니다. 뷰어 로직은 이 썸네일을 3개의 하위 세그먼트로 반올림합니다.

* 썸네일 수 = 다음 썸네일로 반올림합니다(썸네일 수 / 비디오 하위 세그먼트 수).
위 표의 예를 사용하여 9개의 썸네일 / 3개의 비디오 하위 세그먼트 = 3개의 썸네일을 표시합니다.

* 하위 세그먼트 기간 = 총 비디오 기간 / 비디오 하위 세그먼트 수.
위 표의 예를 사용하여, 30초 / 3개의 비디오 하위 세그먼트 = 각 비디오 하위 세그먼트의 10초 표시.

#### 회전 메뉴 배너 뷰어 사전 설정 만들기에 대한 특수 고려 사항 {#special-considerations-for-creating-a-carousel-banner-viewer-preset}

회전 메뉴 배너 뷰어 사전 설정을 만들 때 핫스팟의 스타일을 변경하면 다음과 같이 변경할 수 있습니다.

| | **설명** | **작업** |
|---|---|---|
| **[!UICONTROL 핫스팟 아이콘]** | 핫스팟에 사용되는 아이콘 변경 | 핫스팟 아이콘 이미지를 변경하려면 **[!UICONTROL 모양]** 탭, 위치 **[!UICONTROL 선택한 구성 요소]**, 선택 **[!UICONTROL 이미지 맵 효과]**. 아래 **[!UICONTROL 아이콘]**, 선택 **[!UICONTROL 배경]** 및 **[!UICONTROL 이미지]** 필드는 원하는 배경 이미지로 이동합니다. |

## 뷰어 사전 설정 활성화 또는 비활성화 {#activating-or-deactivating-viewer-presets}

사용자 인터페이스에서 사용할 수 있는 뷰어 사전 설정은 작성자 모드에서 활성화된 뷰어 사전 설정에 따라 다릅니다. 기본적으로 뷰어 사전 설정은 만든 후에 &quot;켜짐&quot;입니다. 사전 설정을 끄면 작성자 모드에 표시되지 않습니다. 사전 설정이 게시되면 설정/해제 여부에 관계없이 항상 게시됩니다. 목록이 너무 비현실적이거나 뷰어 사전 설정을 사용할 수 없게 하려는 경우 뷰어 사전 설정을 비활성화하십시오.

**뷰어 사전 설정을 활성화하거나 비활성화하려면 다음을 수행하십시오.**

1. Experience Manager의 왼쪽 상단 모서리에서 Experience Manager 로고를 선택한 다음 왼쪽 레일에서 을 선택합니다. **[!UICONTROL 도구]** (망치 아이콘) > **[!UICONTROL 에셋]** > **[!UICONTROL 뷰어 사전 설정]**.
1. 뷰어 사전 설정 페이지의 **[!UICONTROL 시/도]** 열 머리글에서 토글을 선택하여 뷰어 사전 설정을 활성화하거나 비활성화합니다.

   활성화된 뷰어 사전 설정은 파란색 상자 안의 오른쪽에 토글이 표시되고, 비활성화된 뷰어 사전 설정은 밝은 회색 상자 안의 왼쪽에 토글이 표시됩니다.

## 뷰어 사전 설정 게시 {#publishing-viewer-presets}

뷰어 사전 설정 상태를 활성화(또는 &quot;켜기&quot;)하면 Dynamic Media 구성 요소 및 대화형 미디어 구성 요소와 에셋을 볼 때마다 뷰어 사전 설정이 표시됨을 의미합니다.

단, 종료 *게재* 뷰어 사전 설정이 있는 에셋은 뷰어 사전 설정도 게시해야 합니다. 모든 뷰어 사전 설정을 활성화해야 함 *및* 에셋에 대한 URL 또는 포함 코드를 얻기 위해 게시됩니다. Dynamic Media과 함께 제공되는 모든 기본 뷰어 사전 설정을 활성화하고 게시합니다. Custom viewer presets that you create and add are auto-activated, but must also be published.

다음을 참조하십시오 [뷰어 사전 설정 활성화 또는 비활성화](#activating-or-deactivating-viewer-presets).

참조: [자산 미리 보기](/help/assets/dynamic-media/previewing-assets.md).

**뷰어 사전 설정을 게시하려면:**

1. Experience Manager의 왼쪽 상단 모서리에서 Experience Manager 로고를 선택한 다음 왼쪽 레일에서 을 선택합니다. **[!UICONTROL 도구]** (망치 아이콘) > **[!UICONTROL 에셋] > [!UICONTROL 뷰어 사전 설정]**.
1. 게시하려는 뷰어 사전 설정을 하나 이상 선택합니다.
1. 도구 모음에서 **[!UICONTROL 게시]** 아이콘.

## 뷰어 사전 설정 정렬 {#sorting-viewer-presets}

1. Experience Manager의 왼쪽 상단 모서리에서 Experience Manager 로고를 선택한 다음 왼쪽 레일에서 을 선택합니다. **[!UICONTROL 도구]** (망치 아이콘) > **[!UICONTROL 에셋] > [!UICONTROL 뷰어 사전 설정]**.
1. 선택 **[!UICONTROL 사전 설정 제목]**, **[!UICONTROL 유형]**, **[!UICONTROL 게시됨]**, 또는 **[!UICONTROL 시/도]** 열 머리글별로 정렬합니다. 예를 들어 을 선택합니다. **[!UICONTROL 유형]**  뷰어 사전 설정 유형을 알파벳순 또는 역알파벳순으로 정렬합니다.

## 뷰어 사전 설정 편집 {#editing-viewer-presets}

모두 편집 *사전 정의된 기본 뷰어 사전 설정* 은(는) 지원되지 않는 시나리오입니다. 기본 뷰어 사전 설정을 편집하는 경우 새 이름으로 저장하라는 메시지가 표시됩니다.

**뷰어 사전 설정을 편집하려면:**

1. Experience Manager의 왼쪽 상단 모서리에서 Experience Manager 로고를 선택한 다음 왼쪽 레일에서 을 선택합니다. **[!UICONTROL 도구]** (망치 아이콘) > **[!UICONTROL 자산]** > **[!UICONTROL 뷰어 사전 설정]**.
1. 뷰어 사전 설정 제목 왼쪽의 상자를 선택하여 사전 설정을 선택합니다.
1. 도구 모음에서 를 선택합니다. **[!UICONTROL 편집]**.
1. 다음에서 **[!UICONTROL 뷰어 사전 설정 편집기]** 페이지에서 다음에 있는 옵션을 사용하여 뷰어 사전 설정을 변경합니다. **[!UICONTROL 모양]** 및 **[!UICONTROL 비헤이비어]** 탭.

   다음에서 **[!UICONTROL 모양]** Viewer Preset Editor 페이지의 왼쪽 위 모서리 근처에서 탭을 선택하고 **[!UICONTROL 데스크탑]**, **[!UICONTROL 태블릿]**, 또는 **[!UICONTROL 전화]** 에셋의 프레젠테이션 모드를 변경합니다.

1. 페이지의 오른쪽 상단 모서리 근처에서 다음 중 하나를 수행합니다.

   * 선택 **[!UICONTROL 저장]** 변경 사항을 저장하고 [뷰어 사전 설정] 페이지로 돌아갑니다.
   * 선택 **[!UICONTROL 취소]** 변경한 내용을 취소하고 [뷰어 사전 설정] 페이지로 돌아가려면

## 사용자 정의 뷰어 사전 설정 삭제 {#deleting-custom-viewer-presets}

만들어 Dynamic Media에 추가한 뷰어 사전 설정을 삭제할 수 있습니다.

**사용자 지정 뷰어 사전 설정을 삭제하려면:**

1. Experience Manager의 왼쪽 상단 모서리에서 Experience Manager 로고를 선택한 다음 왼쪽 레일에서 을 선택합니다. **[!UICONTROL 도구]** (망치 아이콘) > **[!UICONTROL 에셋] > [!UICONTROL 뷰어 사전 설정]**.
1. 뷰어 사전 설정 페이지에서 사전 설정 제목 을 선택한 다음 **[!UICONTROL 휴지통]** 아이콘.
1. **[!UICONTROL 삭제]**&#x200B;를 선택합니다.

## 자산에 뷰어 사전 설정 적용 {#applying-a-viewer-preset-to-an-asset}

If you have already published both the asset and the selected viewer, the **[!UICONTROL URL]** and **[!UICONTROL Embed]** buttons appear after you select a viewer preset.

**뷰어 사전 설정을 자산에 적용하려면 다음을 수행합니다.**

1. 에셋을 열고 페이지의 왼쪽 상단 모서리 근처에서 드롭다운 메뉴를 선택한 다음 를 선택합니다 **[!UICONTROL 뷰어]**.

   >[!NOTE]
   >
   >If you have already published both the asset and the selected viewer, the **[!UICONTROL URL]** and **[!UICONTROL Embed]** buttons appear after you select a viewer preset.

1. 에셋에 적용하려면 왼쪽 창에서 뷰어 사전 설정을 선택합니다.

   다음을 수행할 수 있습니다. [공유할 URL 복사](/help/assets/dynamic-media/linking-urls-to-yourwebapplication.md) (다른 사용자와 함께)

## 뷰어 사전 설정으로 자산 전달 {#delivering-assets-with-viewer-presets}

뷰어 사전 설정에 대한 URL을 가져오려면 다음을 참조하십시오. [웹 애플리케이션에 URL 연결](/help/assets/dynamic-media/linking-urls-to-yourwebapplication.md). 참조: [웹 페이지에 비디오 뷰어 포함](/help/assets/dynamic-media/embed-code.md).

Experience Manager을 WCM으로 사용하는 경우 페이지에서 바로 뷰어 사전 설정을 사용하여 에셋을 추가할 수 있습니다. 다음을 참조하십시오 [페이지에 Dynamic Media 에셋 추가](/help/assets/dynamic-media/adding-dynamic-media-assets-to-pages.md).
