---
title: 뷰어 사전 설정 관리
description: 뷰어 사전 설정을 만들고 관리하는 방법
translation-type: tm+mt
source-git-commit: 6224d193adfb87bd9b080f48937e0af1f03386d6

---


# Managing Viewer Presets{#managing-viewer-presets}

뷰어 사전 설정은 사용자가 컴퓨터 화면 및 모바일 장치에서 리치 미디어 자산을 보는 방법을 결정하는 설정 모음입니다. 관리자는 뷰어 사전 설정을 만들 수 있습니다. 일련의 뷰어 구성 옵션에 대해 설정을 사용할 수 있습니다. 예를 들어 뷰어 표시 크기 또는 확대/축소 동작을 변경할 수 있습니다.

<!-- SDK withdrawn from public view. Available internally only at `http://staging.scene7.com/s7sdk/3.8/docs/jsdoc/symbols/_s7sdk.html` 

For instructions on creating and customizing your own HTML5 viewer presets, see the *Adobe Scene7 HTML5 Viewer SDK*. The SDK is available on the IS publish server embedded in the SDK itself. Each library version has its own SDK documentation included.

Path: `<scene7_domain>/s7sdk/<library_version>/docs/jsdocs/index.html`.
For example, 3.5 SDK: [https://s7d1.scene7.com/s7sdk/3.5/docs/jsdoc/index.html](https://s7d1.scene7.com/s7sdk/3.5/docs/jsdoc/index.html)

-->

Adobe 뷰어 [참조 안내서를 참조하십시오](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/library/home.html).

이 섹션에서는 뷰어 사전 설정을 만들고, 편집하고, 관리하는 방법에 대해 설명합니다. 미리 볼 때마다 자산에 뷰어 사전 설정을 적용할 수 있습니다. See [Applying Viewer Presets](#applying-a-viewer-preset-to-an-asset).

>[!NOTE]
>
>사전 *정의된 즉시 사용 가능한 뷰어 사전 설정을* 편집할 수 있는 시나리오는 지원되지 않습니다. 기본 뷰어 사전 설정을 편집하려고 하면 새 이름을 사용하여 뷰어 사전 설정을 저장하라는 메시지가 표시됩니다.

## 뷰어를 위한 키보드 액세스 가능성 {#keyboard-accessibility-for-viewers}

모든 기본 뷰어는 키보드 접근성을 지원합니다.

키보드 액세스 [가능성 및 탐색](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/library/c-keyboard-accessibility.html)참조

## Managing Viewer Presets {#managing-viewer-presets-1}

AEM에서 **[!UICONTROL 도구(망치 아이콘)> 자산 > 뷰어 사전 설정을 탭하여 뷰어 사전 설정을 추가, 편집, 삭제, 게시, 게시 취소 및 미리 볼 수** 있습니다 ****.

![6_5_tools-assets-viewerpresets](assets/6_5_tools-assets-viewerpresets.png)

>[!NOTE]
>
>기본적으로 자산의 세부 사항 보기에서 뷰어를 선택하면 15개의 뷰어 사전 설정이 표시됩니다. 이 제한을 늘릴 수 있습니다. 표시되는 [뷰어 사전 설정 수 증가를](#increasing-the-number-of-viewer-presets-that-display)참조하십시오.

### 반응형 디자인 웹 페이지를 위한 뷰어 지원 {#viewer-support-for-responsive-designed-web-pages}

웹 페이지마다 요구 사항이 다릅니다. 예를 들어 HTML5 뷰어를 별도의 브라우저 창에서 여는 링크를 제공하는 웹 페이지를 원할 수 있습니다. 다른 경우 호스팅 페이지에 HTML5 뷰어를 직접 포함해야 할 수 있습니다. 후자의 경우 웹 페이지에 정적 레이아웃이 있을 수 있습니다. 또는 &quot;반응형&quot;일 수 있으며 서로 다른 장치 또는 서로 다른 브라우저 창 크기에 대해 다르게 표시됩니다. 이러한 요구 사항을 충족하기 위해 Dynamic Media와 함께 제공되는 미리 정의된 즉시 사용 가능한 모든 HTML5 뷰어는 정적 웹 페이지와 반응형 디자인 웹 페이지를 모두 지원합니다.

반응형 [뷰어를 웹 페이지에](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/image-serving-api/image-serving-api/responsive-static-image-library/c-about-responsive-static-image-library.html) 임베드하는 방법에 대한 자세한 내용은 Scene7 이미지 제공 API 도움말의 ** 응답형 이미지 라이브러리를 참조하십시오.

>[!NOTE]
>
>처음 사용하기 전에 모든 기본 뷰어를 게시해야 합니다.
>See [Publishing Viewer Presets.](#publishing-viewer-presets)

### 뷰어 사전 설정 시스템 호환성 {#viewer-preset-system-compatibility}

Dynamic Media와 함께 제공되는 모든 기본 뷰어 사전 설정은 다음 시스템과 완벽하게 호환됩니다.

* 데스크탑
* Apple iPhone
* Apple iPad
* Android Smartphone
* Android 태블릿
* 비디오의 경우 Blackberry 및 Windows Phone에 대해 MP4 재생에 [대한](https://developer.blackberry.com/devzone/develop/supported_media/bb_media_support_at_a_glance.html#kba1328730952678) 추가 지원이 [제공됩니다](https://msdn.microsoft.com/library/windows/apps/ff462087%28v=vs.105%29.aspx).

### 뷰어 사전 설정을 위한 리치 미디어 유형 {#rich-media-types-for-viewer-presets}

관리자는 새 뷰어 사전 설정을 만들 때 다음과 같은 리치 미디어 유형을 추가하고 사용자 정의할 수 있습니다.

<table>
 <tbody>
  <tr>
   <td><strong>회전 메뉴 세트</strong><br /> </td>
   <td><p>핫스팟, 이미지 맵 또는 둘 다 여러 개의 이미지에 추가됩니다. 고객은 이미지를 왼쪽 또는 오른쪽으로 이동한 다음 이미지의 핫스팟을 클릭하여 자세한 내용을 확인하거나 웹 사이트의 카테고리, 홈 또는 랜딩 페이지에서 직접 구매할 수 있습니다.</p> </td>
  </tr>
  <tr>
   <td><strong>플라이아웃 확대/축소</strong></td>
   <td><p>원본 이미지 옆에 확대된 영역의 두 번째 이미지를 표시합니다. 사용할 컨트롤이 없습니다. 사용자가 보려는 영역 위로 선택 항목을 이동합니다.</p> <p>이 뷰어에 대한 전체 대역폭 사용을 결정할 때는 뷰어에서 기본 이미지와 플라이아웃 이미지가 모두 제공된다는 점을 고려하십시오. 기본 이미지 크기(스테이지 너비 및 높이)와 확대/축소 비율이 플라이아웃 이미지 크기를 결정합니다. 플라이아웃 파일 크기가 너무 커지지 않게 하려면 다음 두 값의 균형을 조정합니다.큰 주 이미지 크기가 있는 경우 [확대/축소 비율] 값을 낮춥니다. (플라이아웃 너비 및 플라이아웃 높이는 플라이아웃 창의 크기를 결정하지만 뷰어에 제공되는 플라이아웃 이미지의 크기는 아닙니다.)</p> <p>예를 들어 기본 이미지 크기가 350 x 350픽셀이고 확대/축소 인수가 3인 경우 결과 플라이아웃 이미지는 1050 x 1050픽셀입니다. 기본 이미지 크기가 300 x 300 픽셀이고 확대/축소 인수가 4인 경우 플라이아웃 이미지는 1200 x 1200 픽셀입니다. JPEG 품질 설정(권장 설정은 80-90 사이)에 따라 파일 크기를 크게 줄일 수 있습니다. 기본 이미지의 크기에 따라 권장되는 확대/축소 요소는 2.5에서 4입니다.</p> </td>
  </tr>
  <tr>
   <td><strong>인라인 확대/축소</strong></td>
   <td>원본 뷰어 내에서 확대된 영역의 이미지를 표시합니다. 사용할 컨트롤이 없습니다. 즉, 사용자가 보려는 영역 위로 선택 영역을 이동합니다.</td>
  </tr>
  <tr>
   <td><strong>이미지 집합</strong></td>
   <td>이미지 세트 뷰어에서 축소판 이미지를 클릭하여 항목의 서로 다른 보기 또는 색상 변형을 볼 수 있습니다. 또한 이 뷰어는 이미지를 자세히 검사하기 위한 확대/축소 도구를 제공합니다.</td>
  </tr>
  <tr>
   <td><strong>대화형 이미지</strong></td>
   <td>핫스팟은 고객이 추가 세부 사항을 확인하거나 웹 사이트의 카테고리, 홈 또는 랜딩 페이지에서 직접 구매할 수 있는 이미지의 일부에 추가됩니다.</td>
  </tr>
  <tr>
   <td><strong>대화형 비디오</strong></td>
   <td>축소판은 고객이 추가 세부 사항을 확인하거나 웹 사이트의 카테고리, 홈 또는 랜딩 페이지에서 직접 구매할 수 있는 비디오의 타임라인 세그먼트에 추가됩니다.</td>
  </tr>
  <tr>
   <td><strong>혼합 미디어</strong></td>
   <td>하나의 뷰어에 서로 다른 유형의 미디어를 표시합니다. 스핀 세트, 이미지 세트, 이미지 및 비디오를 포함할 수 있습니다.</td>
  </tr>
  <tr>
   <td><strong>파노라마 이미지</strong></td>
   <td><p>파노라마 이미지 및 PanoramicVR 뷰어는 구형 파노라마 이미지를 렌더링하여 회의실, 속성, 위치 또는 조경의 360° 보기 경험을 제공합니다.</p> <p>업로드된 이미지가 구형 파노라마를 적용하려면 다음 중 하나 또는 둘 다를 가져야 합니다.</p>
    <ul>
     <li>2:1 종횡비.</li>
     <li>키워드 <code>equirectangular</code>또는 <code>spherical</code> 및 <code>panorama</code>및 <code>spherical </code>및 <code>panoramic</code>및 태그 <a href="/help/sites-cloud/authoring/features/tags.md">사용을 참조하십시오</a>.</li>
    </ul> <p>종횡비와 키워드 기준은 모두 자산 세부 사항 페이지 및 "파노라마 미디어" WCM 구성 요소의 파노라마 에셋에 적용됩니다.</p></td>
  </tr>
  <tr>
   <td><strong>회전 집합</strong></td>
   <td>사용자가 개체를 전환하여 서로 다른 측면 및 각도를 검사할 수 있도록 이미지의 여러 보기를 제공합니다.</td>
  </tr>
  <tr>
   <td><strong>360 비디오</strong></td>
   <td><p>360/VR 비디오 뷰어를 사용하여 등장방형 비디오를 렌더링하여 회의실, 속성, 위치, 가로 또는 의료 절차의 몰입형 시청 경험을 제공할 수 있습니다.</p> <p>평면 디스플레이에서 재생하는 동안 사용자는 보기 각도를 제어할 수 있습니다.모바일 디바이스에서 재생하면 일반적으로 내장된 자이로스코프 컨트롤을 활용할 수 있습니다.</p> <p>뷰어에는 360개의 비디오 에셋 전달에 대한 기본 지원이 포함되어 있습니다. 기본적으로 보거나 재생하는 데 추가 구성이 필요하지 않습니다. .mp4, .mkv 및 .mov와 같은 표준 비디오 익스텐션을 사용하여 360개의 비디오를 제공할 수 있습니다. 가장 일반적인 코덱은 H.264입니다.</p> </td>
  </tr>
  <tr>
   <td><strong>비디오</strong></td>
   <td><p>점진적 또는 적응형 비트 전송률 스트리밍을 사용하여 비디오를 재생합니다. 적응형 비트 전송률 스트리밍은 디바이스 및 대역폭 검색을 자동으로 수행하여 올바른 포맷의 비디오를 제공합니다.</p> </td>
  </tr>
  <tr>
   <td><strong>세로 확대/축소</strong></td>
   <td><p>세로 확대/축소 뷰어를 사용하면 제품 이미지 보기 환경을 최대화하여 사용자에게 최상의 제품 표현을 제공할 수 있습니다. 색상 견본의 수직 위치는 다음과 같습니다.</p>
    <ul>
     <li>견본이 "접힌 항목 위"에 있는지 확인합니다.<br/> 가로 색상 견본을 사용하면 사용자의 데스크탑 화면 크기에 따라 사용자가 페이지를 스크롤할 때까지 색상 견본을 볼 수 없었습니다. 뷰어에 견본을 세로로 배치하면 사용자의 화면 크기와 상관없이 견본이 표시되도록 할 수 있습니다.</li>
     <li>기본 이미지 크기를 최대화합니다.<br /> 가로 색상 견본을 사용하면 페이지의 공간을 예약하여 표시되는지 확인해야 합니다. 이렇게 하면 기본 이미지의 크기가 줄어듭니다. 그러나 세로 견본 레이아웃에서는 이 공간을 할당할 필요가 없습니다. 따라서 기본 이미지 크기를 최대화할 수 있습니다.</li>
    </ul> </td>
  </tr>
  <tr>
   <td><strong>확대/축소</strong></td>
   <td>사용자가 영역을 클릭하여 확대할 수 있습니다. 사용자는 컨트롤을 클릭하여 이미지를 확대, 축소 및 기본 크기로 재설정할 수 있습니다.</td>
  </tr>
 </tbody>
</table>

### 기본 뷰어 사전 설정 목록 {#list-of-out-of-the-box-viewer-presets}

다음 표에서는 Dynamic Media와 함께 제공되는 미리 정의된 모든 뷰어 사전 설정을 식별합니다.

뷰어 참조 [라이브러리 예](https://marketing.adobe.com/resources/help/en_US/s7/vlist/vlist.html) 및 라이브 데모를 [참조하십시오](https://landing.adobe.com/en/na/dynamic-media/ctir-2755/live-demos.html).

뷰어용 지원되는 웹 브라우저 및 운영 체제 버전에 대한 자세한 내용은 뷰어 릴리스 정보를 검토할 수 있습니다.

뷰어 참조 안내서의 목차 &quot;뷰어 릴리스 노트&quot; [를 참조하십시오](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/library/home.html).

>[!NOTE]
>
>Dynamic Media의 모든 기본 뷰어 사전 설정은 이미 활성화(설정)되었지만 게시해야 합니다.
>See [Publishing Viewer Presets](#publishing-viewer-presets).
>
>만들고 추가하는 모든 새로운 뷰어 사전 설정은 활성화 및 *게시되어야 합니다.
>뷰어 [사전 설정 활성화 또는 비활성화](#activating-or-deactivating-viewer-presets) 및 뷰어 사전 [설정을 참조하십시오](#publishing-viewer-presets).

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
   <td>Flyout_Zoom</td>
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
   <td>Flyout_Zoom</td>
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
   <td>파노라마 이미지</td>
   <td>Panoramic_Image</td>
   <td><code>html5_panoramicimage.css</code></td>
  </tr>
  <tr>
   <td>PanoramicImageVR</td>
   <td>Panoramic_Image</td>
   <td><code>html5_panoramicimage.css</code></td>
  </tr>
  <tr>
   <td>Shopperable_Banner</td>
   <td>Interactive_Image</td>
   <td><code>html5_interactiveimage.css</code></td>
  </tr>
  <tr>
   <td>Shopperable_Video_dark</td>
   <td>Interactive_Video</td>
   <td><code>html5_interactivevideoviewer_dark.css</code></td>
  </tr>
  <tr>
   <td>Shopperable_Video_light</td>
   <td>Interactive_Video</td>
   <td><code>html5_interactivevideovewer_light.css</code></td>
  </tr>
  <tr>
   <td>회전 집합(_D)</td>
   <td>회전_집합</td>
   <td><code>html5_spinviewer_dark.css</code></td>
  </tr>
  <tr>
   <td>회전 집합(_L)</td>
   <td>회전_집합</td>
   <td><code>html5_spinviewer_light.css</code></td>
  </tr>
  <tr>
   <td><p>비디오</p> <p>(자막 지원 포함)</p> </td>
   <td>비디오</td>
   <td><code>html5_videoviewer.css</code></td>
  </tr>
  <tr>
   <td><p>Video360_social</p> <p>(기본 비디오 재생 컨트롤 포함, 비디오 렌더링은 스테레오 모드로 수행되고, 수동 POV 제어가 꺼져 있지만 POS(Girropose Control)는 켜지고, 소셜 미디어 기능은 작동하지 않음)</p> </td>
   <td>Video_360</td>
   <td><code>html5_video360viewersocial.css</code></td>
  </tr>
  <tr>
   <td><p>Video360VR</p> <p>(가상 현실 안경을 사용하는 최종 사용자를 위해 설계되었습니다. 기본 비디오 재생 컨트롤 및 소셜 미디어 기능 포함)</p> </td>
   <td>Video_360</td>
   <td><code>html5_video360viewer.css</code></td>
  </tr>
  <tr>
   <td><p>Video_social</p> <p>(자막 및 소셜 미디어 지원 포함)</p> </td>
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

다음 표는 iOS, Android 2.x 및 Android 3.x 장치에서 지원되는 모바일 뷰어 제스처를 나타냅니다.

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
   <td><p><strong>탭하기</strong></p> </td>
   <td><p>플라이아웃 창 표시</p> </td>
   <td><p>사용자 인터페이스를 표시하거나 숨깁니다.</p> </td>
   <td><p>사용자 인터페이스를 표시하거나 숨깁니다.</p> </td>
  </tr>
  <tr>
   <td><p><strong>두 번 누르기</strong></p> </td>
   <td><p>적용되지 않음</p> </td>
   <td><p>확대 또는 재설정</p> </td>
   <td><p>확대 또는 재설정</p> </td>
  </tr>
  <tr>
   <td><p><strong>핀치 열기</strong></p> </td>
   <td><p>적용되지 않음</p> </td>
   <td><p>확대(iOS 및 Android 3x만 해당)</p> </td>
   <td><p>확대(iOS 및 Android 3x만 해당)</p> </td>
  </tr>
  <tr>
   <td><p><strong>핀치 닫기</strong></p> </td>
   <td><p>적용되지 않음</p> </td>
   <td><p>축소(iOS 및 Android 3x만 해당)</p> </td>
   <td><p>축소(iOS 및 Android 3x만 해당)</p> </td>
  </tr>
  <tr>
   <td><p><strong>밀기</strong></p> </td>
   <td><p>견본 막대를 스크롤합니다.</p> </td>
   <td><p>이미지 스크롤</p> </td>
   <td><p>회전</p> </td>
  </tr>
  <tr>
   <td><p><strong>영화</strong></p> </td>
   <td><p>견본 막대를 스크롤합니다.</p> </td>
   <td><p>이미지 스크롤</p> </td>
   <td><p>회전</p> </td>
  </tr>
 </tbody>
</table>

## 표시되는 뷰어 사전 설정 수 증가 {#increasing-the-number-of-viewer-presets-that-display}

AEM은 세부 사항 보기 > 뷰어에서 자산을 볼 때 다양한 뷰어 사전 **[!UICONTROL 설정을 보여줍니다]**. 표시되는 뷰어 수를 늘리거나 줄일 수 있습니다.

**표시되는 뷰어 사전 설정 수를 늘리려면**

1. CRXDE Lite(https://localhost:4502/crx/de)로[이동합니다](https://localhost:4502/crx/de).
1. 뷰어 사전 설정 목록 노드로 이동합니다. `/libs/dam/gui/coral/content/commons/sidepanels/viewerpresets/viewerpresetslist`

   ![chlimage_1-221](/help/assets/dynamic-media/assets/chlimage_1-221.png)

1. limit **[!UICONTROL 속성에서]** 기본적으로 15로 ****&#x200B;설정된 값을 원하는 수로 변경합니다.
1. 뷰어 사전 설정 데이터 소스 탐색( `/libs/dam/gui/coral/content/commons/sidepanels/viewerpresets/viewerpresetslist/datasource`

   ![chlimage_1-222](/help/assets/dynamic-media/assets/chlimage_1-222.png)

1. limit 속성에서 숫자를 원하는 숫자로 변경합니다(예: `{empty requestPathInfo.selectors[1] ? "20" : requestPathInfo.selectors[1]}`
1. 모두 **[!UICONTROL 저장을 누릅니다]**.

## 뷰어 사전 설정 만들기 {#creating-a-new-viewer-preset}

뷰어 사전 설정을 만들면 다양한 설정을 적용하여 자산을 보고 상호 작용할 수 있습니다. 그러나 새 뷰어 사전 설정을 만들 필요는 없습니다. 원하는 경우 AEM 자산에 이미 포함되어 있는 기본 즉시 사용 가능한 뷰어 사전 설정을 사용할 수 있습니다.

새 뷰어 사전 설정을 만들기로 선택한 경우, 저장한 후 뷰어 사전 설정 페이지에서 뷰어 상태가 자동으로 활성화( **[!UICONTROL 켜기로]**&#x200B;설정)됩니다. 이 상태는 Dynamic Media 구성 요소 및 대화형 미디어 구성 요소에서 그리고 이미지나 비디오를 미리 볼 때마다 표시됨을 의미합니다.

일부 뷰어 사전 설정에는 뷰어의 사용 및 전체 동작에 영향을 줄 수 있는 전용 설정이 있습니다. 만들고 있는 뷰어 사전 설정에 따라 이러한 특별한 고려 사항을 알고 싶을 수 있습니다.

대화형 [뷰어 사전 설정을](#special-considerations-for-creating-an-interactive-viewer-preset)만들기 위한 특수 고려 사항을 참조하십시오.

회전판 [배너 뷰어 사전 설정을](#special-considerations-for-creating-a-carousel-banner-viewer-preset)만들기 위한 특수 고려 사항을 참조하십시오.

**뷰어 사전 설정을 만들려면**

1. AEM의 왼쪽 위 모서리에서 AEM 로고를 누른 다음 왼쪽 레일에서 **[!UICONTROL 도구** (망치 아이콘) **[!UICONTROL > 자산 > 뷰어 사전 설정을 누릅니다**.

   ![6_5_viewerpresets](assets/6_5_viewerpresets.png)

1. [뷰어 사전 설정] 페이지의 도구 모음에서 만들기를 **[!UICONTROL 누릅니다]**.
1. [!UICONTROL **새 뷰어 사전 설정** ] 대화 상자의 [ **[!UICONTROL 사전 설정 이름]** ] 필드에 새 사전 설정의 이름을 입력합니다. 이름을 신중하게 선택합니다. 만들기를 탭한 후에는 편집할 수 없습니다 ****.

   이러한 단계 후반부에서 사전 설정을 저장할 때 [사전 설정 제목] 열 머리글 아래의 [뷰어 사전 설정] 페이지에 해당 이름이 나타납니다.

1. 리치 미디어 유형 드롭다운 메뉴에서 만들 뷰어 사전 설정 유형을 선택한 다음 페이지의 오른쪽 위 모서리에서 만들기를 **[!UICONTROL 누릅니다]**.

   뷰어 [사전 설정에 대한 리치 미디어 유형을 참조하십시오](#rich-media-types-for-viewer-presets).

1. 뷰어 사전 설정 편집기 페이지에서 모양 **[!UICONTROL 탭을]** 누릅니다.
1. 다음 중 하나를 수행하십시오.

   * 선택한 **[!UICONTROL 유형]** 풀다운 메뉴에서 시각적 디자인을 사용자 정의할 구성 요소를 선택합니다. 또는 뷰어에서 시각적 요소를 탭하거나 클릭하여 구성할 요소를 선택할 수 있습니다.

      시각적 편집기를 사용하면 특정 속성이 스타일에 어떤 영향을 주는지 확인할 수 있습니다. 편집기의 왼쪽에 있는 샘플을 사용하여 뷰어에 미치는 영향을 즉시 확인할 수 있도록 속성을 설정하거나 조정할 수 있습니다.

      각 뷰어 사전 설정 유형에 대한 CSS 스타일 속성은 뷰어 참조 안내서의 &quot;뷰어 사용자 정의&quot; *`<viewer name>`* 도움말 항목에 [설명되어 있습니다](https://marketing.adobe.com/resources/help/en_US/s7/viewers_ref/). 예를 들어 해당 유형의 뷰어 사전 설정을 만드는 경우 `Mixed_Media`각 [속성의 목록과 설명은 혼합 미디어 뷰어](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/library/viewers-aem-assets-dmc/mixed-media/customing-mixed-media/c-html5-mixedmedia-viewer-customizingviewer.html) 사용자 지정을 참조하십시오.

   * 별도의 CSS 파일에서 스타일 설정을 정의한 경우 CSS 파일을 AEM 자산에 업로드할 수 있습니다. 선택한 **[!UICONTROL 유형]** 풀다운 메뉴 아래에 있는 CSS **[!UICONTROL 가져오기를 탭하여]** 업로드된 CSS 파일을 찾아 뷰어 사전 설정과 연결할 수 있습니다(시각적 편집기를 위로 스크롤해야 할 수 있음).

      CSS 파일을 가져올 때 시각적 편집기는 CSS가 올바른 뷰어 마커를 사용하는지 확인합니다. 예를 들어 확대/축소 뷰어를 만드는 경우 가져오는 모든 CSS 규칙은 상위 뷰어 요소에 `.s7mixedmediaviewer` 정의된 뷰어 클래스 이름을 사용하여 정의해야 합니다.

      지정된 뷰어에 대한 CSS 마커를 적절히 정의하는 한 임의의 수제 CSS를 가져올 수 있습니다. (CSS 마커는 뷰어 참조 안내서의 *&lt;뷰어 이름>* 뷰어&quot; 도움말 항목에 [설명되어 있습니다](https://marketing.adobe.com/resources/help/en_US/s7/viewers_ref/). 예를 들어 확대/축소 뷰어용 CSS 마커에 대해 읽으려면 확대/축소 뷰어 [사용자 지정을 참조하십시오](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/library/viewers-aem-assets-dmc/zoom/customizing-zoom/c-html5-20-zoom-viewer-customizingviewer.html). 그러나 시각적 편집기가 일부 CSS 값을 이해하지 못할 수도 있습니다. 이러한 경우 시각적 편집기는 CSS가 계속 작동할 수 있도록 오류를 무시하려고 합니다.
   >[!NOTE]
   >
   >CSS를 Raw 형식으로 직접 편집하려면 선택한 **[!UICONTROL 유형 풀다운 메뉴]** 아래에 있는 CSS 표시/숨기기를 누릅니다(보려면 시각적 편집기를 위로 스크롤해야 할 수 있음).
   >시각적 편집기와 마찬가지로 CSS에서 직접 속성을 변경하면 뷰어 샘플에 어떤 영향이 있는지 즉시 확인할 수 있습니다. 시각적 편집기에서 동일한 속성이 동시에 자동으로 업데이트됩니다. 따라서 Raw CSS 편집기 또는 시각적 편집기를 사용하거나 두 가지 모두를 함께 사용할 수 있습니다.

   >[!NOTE]
   >
   >단추 아트웍의 경우 2x 이미지를 선택하고 고해상도 아트웍을 업로드합니다. 인터랙티브한 이미지와 쇼퍼블 배너를 사용하여 작업할 때 즉시 사용 가능한 다양한 핫스팟 단추에서 선택할 수도 있습니다.

1. (선택 사항) [뷰어 사전 설정 편집] 페이지 상단 근처에서 **[!UICONTROL 데스크톱]**, **[!UICONTROL 태블릿]**&#x200B;또는 **[!UICONTROL 전화를]** 눌러다양한 장치 및 화면 유형에 대해 시각적 스타일을 고유하게 정의합니다.
1. [뷰어 사전 설정 편집기] 페이지에서 [동작] **[!UICONTROL 탭을]** 누릅니다. 또는 뷰어에서 시각적 요소를 탭하거나 클릭하여 구성할 요소를 선택할 수 있습니다.
1. 선택한 **[!UICONTROL 유형]** 풀다운 메뉴에서 동작을 변경할 구성 요소를 선택합니다.

   시각적 편집기의 많은 구성 요소에는 관련된 자세한 설명이 있습니다. 이러한 설명은 구성 요소를 확장하여 연결된 매개 변수를 표시할 때 파란색 상자 내에 표시됩니다.

   일부 뷰어 유형에는 IS 명령 텍스트 필드에서 이미지 제공 명령을 지정할 수 있는 구성 **[!UICONTROL 요소가]** 있습니다. 사용할 수 있는 명령 목록은 이미지 제공 API [참조를 참조하십시오](https://marketing.adobe.com/resources/help/en_US/s7/is_ir_api/image_serving_api_ref.html).

   >[!NOTE]
   >
   >**휴대폰 또는 태블릿과 같은 터치 장치를 사용하는 경우...**
   >
   >
   >텍스트 필드에 값을 입력한 후 사용자 인터페이스의 다른 부분을 눌러 변경 내용을 제출하고 가상 키보드를 닫습니다. Enter 키를 누르면 작업이 발생하지 않습니다.

1. Near the upper-right corner of the page, tap **[!UICONTROL Save]**.
1. 새 뷰어 사전 설정을 게시합니다. 웹 사이트에서 사전 설정을 사용하려면 먼저 사전 설정을 게시해야 합니다.

   See [Publishing Viewer Presets](#publishing-viewer-presets).

### 대화형 뷰어 사전 설정을 만들기 위한 특수 고려 사항 {#special-considerations-for-creating-an-interactive-viewer-preset}

**패널의 이미지 축소판의 표시 모드 정보**

대화형 비디오 뷰어 사전 설정을 만들거나 편집할 때 [동작] 탭 아래의 [선택한 구성 요소] `InteractiveSwatches` 풀다운 **[!UICONTROL 메뉴에서 선택할 때 사용할]** 표시 모드 **[!UICONTROL 설정 중 하나를]** 선택할 수있습니다. 선택한 표시 모드는 비디오가 재생되는 동안 축소판이 표시되는 방법과 시기에 영향을 줍니다. 디스플레이 모드( `segment`기본값) 또는 디스플레이 모드를 선택할 `continuous` 수 있습니다.

<table>
 <tbody>
  <tr>
   <td><strong>표시 모드</strong></td>
   <td><strong>설명</strong></td>
  </tr>
  <tr>
   <td>세그먼트</td>
   <td><p><code>Segment </code>은 사용자가 직접 만든 기본 대화형 비디오 뷰어 사전 설정 <code>Shoppable_Video_light</code> 및 대화형 비디오 뷰어 사전 설정에 대한 기본 표시 모드입니다. <code>Shoppable_Video_dark</code></p> <p>이 모드에서는 표시 패널에 표시되는 스팟 수보다 비디오 세그먼트에 할당된 축소판이 적으면 다음 또는 이전 하위 세그먼트의 축소판을 <i>가져와서 패널의 빈 지점을 채우지 </i>않습니다. 즉, 특정 비디오 세그먼트에 지정된 색상 견본의 표시는 유지됩니다.</p> </td>
  </tr>
  <tr>
   <td>연속</td>
   <td><p>표시 <code>continuous </code>모드에서는 세그먼트에 있는 축소판 수가 패널에 표시되는 수보다 적은 경우 마지막 축소판이 표시되는 경우 뷰어는 다음 세그먼트나 이전 세그먼트의 축소판 표시를 자동으로 포함합니다.</p> <p>이 항목의 <a href="/help/assets/dynamic-media/interactive-videos.md">비디오는</a> <code>continuous </code>표시 모드의 예입니다.</p> </td>
  </tr>
 </tbody>
</table>

**대화형 비디오 뷰어의 자동 스크롤 동작 정보**

대화형 비디오 뷰어에서 축소판의 자동 스크롤 동작은 선택한 표시 모드와 독립적으로 작동합니다.

대화형 비디오 뷰어 사전 설정을 만들거나 편집할 때 [동작] 탭에서 [자동 스크롤]에 액세스합니다. 동작 탭의 선택한 구성 요소 **[!UICONTROL 드롭다운]** 메뉴에서 대화형 견본을 **[!UICONTROL 누릅니다]**. 자동 스크롤 확인란은 IS 명령 텍스트 필드 아래에 나열됩니다.

뷰어 **[!UICONTROL 사전 설정에서 자동 스크롤]** (확인란 지우기)을 비활성화하는 경우 사용자가 비디오를 재생하는 동안 패널에는 비디오 전체 길이에 대한 첫 번째 축소판 이미지만 표시됩니다. 그러나 원하는 경우 위/아래 화살표 아이콘을 사용하여 축소판을 수동으로 스크롤할 수 있습니다.

뷰어 사전 설정에서 자동 **[!UICONTROL 스크롤을]** 활성화(선택)하면 비디오 재생 중에 비디오 세그먼트에 할당된 축소판 이미지가 세그먼트 시작 시 보기로 스크롤됩니다. 하지만 세그먼트 내 특정 축소판이 그 전후의 다른 축소판보다 두 배 이상 표시되는 경우가 있습니다. 이 동작은 세그먼트에 있는 축소판 수가 패널에 표시되는 수보다 크고 균일하게 구분되지 않기 때문에 발생합니다.

예를 들어 30초 분량의 비디오 세그먼트가 있다고 가정해 보겠습니다. 30초 동안 표시할 총 9개의 축소판이 있습니다. 브라우저 크기는 표시 패널에 표시되는 4개의 축소판 위치가 있는 방식으로 조정됩니다. 30초 비디오 시간 세그먼트는 세 개의 하위 세그먼트로 분할됩니다. 다음 표는 지정된 시간 하위 세그먼트에 대해 축소판이 표시되는 분류를 보여줍니다.

| **비디오 하위 세그먼트** | **하위 세그먼트 시간(초)** | **패널에 표시되는 축소판** |
|---|---|---|
| 1 | 0-10 | 1, 2, 3, 4 |
| 2 | 10-20 | 4, 5, 6, 7 |
| 3 | 20-30 | 6, 7, 8, 9 |

비디오 하위 세그먼트 3은 할당된 축소판을 초과하지 않습니다. 또한 다른 축소판의 두 배만큼 축소판이 패널에 표시됩니다.

사용 가능한 위치 수를 기반으로 패널에 표시되는 축소판 수에 대해 뷰어가 사용하는 논리는 다음과 같습니다.

* 하위 세그먼트 수 = 다음 하위 세그먼트로 반올림됩니다(브라우저 창 크기에 따라 축소판 수/축소판 패널에 표시되는 슬롯 수).
위의 표에서 예제 사용, 9 축소판 / 4 슬롯 = 2.25;뷰어 논리는 최대 3개의 하위 세그먼트를 반올림합니다.

* 축소판 수 = 다음 축소판(축소판 수 / 비디오 하위 세그먼트 수)까지 둥글게 표시됩니다.
위의 표에 나와 있는 예제 사용, 9 축소판 / 3 비디오 하위 세그먼트 = 3 축소판.

* 하위 세그먼트 지속 시간 = 총 비디오 지속 시간/비디오 하위 세그먼트 수.
위의 표에서 예제를 사용하여 30초 / 3개의 비디오 하위 세그먼트 = 10초 각 비디오 하위 세그먼트를 표시합니다.

#### 회전판 배너 뷰어 사전 설정을 만들기 위한 특수 고려 사항 {#special-considerations-for-creating-a-carousel-banner-viewer-preset}

회전판 배너 뷰어 사전 설정을 만들 때 다음과 같이 핫스팟 스타일을 변경할 수 있습니다.

|  | **설명** | **작업** |
|---|---|---|
| **[!UICONTROL 핫스팟 아이콘]** | 핫스팟에 사용되는 아이콘 변경 | 핫스팟 아이콘 이미지를 변경하려면 모양 **[!UICONTROL 탭의 선택한 구성]** 요소에서 **[!UICONTROL ImageMap]**&#x200B;효과를 **[!UICONTROL 누릅니다]**. 아이콘 **[!UICONTROL 아래에서]****[!UICONTROL 배경을]** 선택하고 **[!UICONTROL 이미지]** 필드에서원하는 배경 이미지로 이동합니다. |

## 뷰어 사전 설정 활성화 또는 비활성화 {#activating-or-deactivating-viewer-presets}

사용자 인터페이스에서 사용할 수 있는 뷰어 사전 설정은 작성자 모드에서 활성 상태인 설정에 따라 달라집니다. 기본적으로 뷰어 사전 설정은 만든 후 &quot;켜기&quot;입니다. 사전 설정을 끌 경우 [작성] 모드에서는 표시되지 않습니다. 사전 설정이 게시된 경우 켜거나 끌 때 관계없이 항상 게시됩니다. 목록이 너무 복잡하거나 뷰어 사전 설정을 사용할 수 없도록 하려는 경우 뷰어 사전 설정을 비활성화할 수 있습니다.

**뷰어 사전 설정을 활성화하거나 비활성화하려면**

1. AEM의 왼쪽 위 모서리에서 AEM 로고를 누른 다음 왼쪽 레일에서 **[!UICONTROL 도구** (망치 아이콘)> 자산 > 뷰어 사전 설정을 **[!UICONTROL 누릅니다]**.
1. 뷰어 사전 설정 페이지의 상태 **[!UICONTROL 열]** 머리글에서 토글을 눌러 뷰어 사전 설정을 활성화하거나 비활성화합니다.

   활성화되는 뷰어 사전 설정은 파란색 상자 내에 토글이 오른쪽에 표시됩니다.비활성화된 뷰어 사전 설정은 연한 회색 상자 안에 있는 왼쪽에 표시됩니다.

## 뷰어 사전 설정 게시 {#publishing-viewer-presets}

뷰어 사전 설정의 상태를 활성화(또는 &quot;켜기&quot;)하는 것은 Dynamic Media 구성 요소, 대화형 미디어 구성 요소 및 자산을 볼 때마다 해당 사전 설정이 표시된다는 것을 의미합니다.

그러나 뷰어 사전 설정이 있는 에셋을 제공하려면 뷰어 사전 설정도 게시해야 합니다.* 자산에 대한 URL 또는 포함 코드를 얻으려면 모든 뷰어 사전 설정이 활성화되고 *게시되어야 합니다. Dynamic Media와 함께 제공되는 모든 기본 뷰어 사전 설정을 활성화하고 게시해야 합니다. 만들고 추가하는 사용자 정의 뷰어 사전 설정은 자동 활성화되지만 게시되어야 합니다.

뷰어 [사전 설정 활성화 또는 비활성화를 참조하십시오](#activating-or-deactivating-viewer-presets).

자산 미리 [보기를 참조하십시오](/help/assets/dynamic-media/previewing-assets.md).

**뷰어 사전 설정을 게시하려면**

1. AEM의 왼쪽 위 모서리에서 AEM 로고를 누른 다음 왼쪽 레일에서 **[!UICONTROL 도구** (망치 아이콘)> 자산 > 뷰어 사전 설정을 **[!UICONTROL 누릅니다]**.
1. 게시할 뷰어 사전 설정을 하나 이상 선택합니다.
1. 도구 모음에서 게시 **[!UICONTROL 아이콘을 누릅니다]** .

## 뷰어 사전 설정 정렬 {#sorting-viewer-presets}

1. AEM의 왼쪽 위 모서리에서 AEM 로고를 누른 다음 왼쪽 레일에서 **[!UICONTROL 도구** (망치 아이콘)> 자산 > 뷰어 사전 설정을 **[!UICONTROL 누릅니다]**.
1. 사전 **[!UICONTROL 설정 제목]**, **[!UICONTROL 유형]**, **[!UICONTROL 게시됨]**&#x200B;또는 **** 상태를 클릭하여 해당 열 제목을 기준으로 정렬합니다. 예를 들어 **[!UICONTROL 유형을]** 클릭하여 뷰어 사전 설정 유형을 알파벳 순 또는 역알파벳 순으로 정렬합니다.

## 뷰어 사전 설정 편집 {#editing-viewer-presets}

사전 *정의된 즉시 사용 가능한 뷰어 사전 설정을* 편집할 수 있는 시나리오는 지원되지 않습니다. 기본 뷰어 사전 설정을 편집하는 경우 새 이름으로 저장하라는 메시지가 표시됩니다.

**뷰어 사전 설정을 편집하려면**

1. AEM의 왼쪽 위 모서리에서 AEM 로고를 누른 다음 왼쪽 레일에서 **[!UICONTROL 도구** (망치 아이콘)> 자산 > 뷰어 사전 설정을 **[!UICONTROL 누릅니다]**.
1. 뷰어 사전 설정 제목 왼쪽에 있는 상자를 선택하여 사전 설정을 선택합니다.
1. 도구 모음에서 편집을 **[!UICONTROL 누릅니다]**.
1. [뷰어 **[!UICONTROL 사전 설정 편집기]** ] 페이지에서 [모양] 및 [비헤이비어] **[!UICONTROL 탭에 있는 옵션을 사용하여 뷰어 사전]** 설정을 **[!UICONTROL 변경합니다]** .

   [ **[!UICONTROL 뷰어 사전 설정]** 편집기] 페이지의 왼쪽 위 모서리 근처에 있는 [모양 ** 탭에서]**&#x200B;데스크톱 **[!UICONTROL , 태블릿]**&#x200B;또는 Phone **** 을 눌러 자산의 프레젠테이션 모드를 변경합니다.

1. 페이지의 오른쪽 위 모서리 근처에 다음 중 하나를 수행합니다.

   * 저장을 **[!UICONTROL 눌러]** 변경 사항을 저장하고 뷰어 사전 설정 페이지로 돌아갑니다.
   * 취소를 **[!UICONTROL 눌러]** 변경한 내용을 취소하고 뷰어 사전 설정 페이지로 돌아갑니다.

## 사용자 정의 뷰어 사전 설정 삭제 {#deleting-custom-viewer-presets}

만들고 Dynamic Media에 추가한 뷰어 사전 설정을 삭제할 수 있습니다.

**사용자 정의 뷰어 사전 설정을 삭제하려면**

1. AEM의 왼쪽 위 모서리에서 AEM 로고를 누른 다음 왼쪽 레일에서 도구(망치 아이콘) **[!UICONTROL > 자산]** > 뷰어 사전 설정을 **[!UICONTROL 누릅니다]**.
1. 뷰어 사전 설정 페이지에서 사전 설정 제목을 선택한 다음 휴지통 **[!UICONTROL 아이콘을 누릅니다]** .
1. 삭제를 **[!UICONTROL 누릅니다]**.

## 자산에 뷰어 사전 설정 적용 {#applying-a-viewer-preset-to-an-asset}

자산과 선택한 뷰어를 모두 이미 게시한 경우 뷰어 **[!UICONTROL 사전 설정을]** 선택한 **[!UICONTROL 후]** URL 및 포함단추가 표시됩니다.

**자산에 뷰어 사전 설정을 적용하려면**

1. 자산을 열고 페이지의 왼쪽 위 모서리 근처에 있는 드롭다운 메뉴를 누른 다음 뷰어를 **[!UICONTROL 선택합니다]**.

   >[!NOTE]
   >
   >자산과 선택한 뷰어를 모두 이미 게시한 경우 뷰어 **[!UICONTROL 사전 설정을]** 선택한 **[!UICONTROL 후]** URL 및 포함단추가 표시됩니다.

1. 왼쪽 창에서 뷰어 사전 설정을 선택하여 자산에 적용합니다.

   URL을 [복사하여 다른 사용자와 공유할](/help/assets/dynamic-media/linking-urls-to-yourwebapplication.md) 수 있습니다.

## 뷰어 사전 설정을 사용하여 에셋 제공 {#delivering-assets-with-viewer-presets}

뷰어 사전 설정에 대한 URL을 가져오려면 웹 응용 [프로그램에](/help/assets/dynamic-media/linking-urls-to-yourwebapplication.md)URL 연결을 참조하십시오. 웹 [페이지에 비디오 뷰어 포함을 참조하십시오](/help/assets/dynamic-media/embed-code.md).

AEM을 WCM으로 사용하는 경우 페이지에서 직접 뷰어 사전 설정을 사용하여 자산을 추가할 수 있습니다. See [Adding Dynamic Media Assets to Pages](/help/assets/dynamic-media/adding-dynamic-media-assets-to-pages.md).