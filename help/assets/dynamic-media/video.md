---
title: Dynamic Media의 비디오
description: 비디오 인코딩, YouTube에 비디오 게시, 비디오 보고서 보기, 비디오에 자막, 자막 또는 장 마커 추가 등과 같은 Dynamic Media에서 비디오를 사용하여 작업하는 방법을 알아봅니다.
feature: Video Profiles
role: User
exl-id: 0d5fbb3e-b763-415f-8c69-ea36445f882b
source-git-commit: 22718edcfb6d233a1316fcf2546e685b57609e8c
workflow-type: tm+mt
source-wordcount: '9349'
ht-degree: 4%

---

# 비디오 {#video}

이 섹션에서는 Dynamic Media에서 비디오 작업을 설명합니다.

## 빠른 시작: 비디오 {#quick-start-videos}

다음 단계별 워크플로우 설명은 Dynamic Media의 응용 비디오 세트를 빠르게 설정 및 실행하는 데 도움이 되도록 설계되었습니다. 각 단계 후에는 자세한 정보를 찾을 수 있는 주제 제목에 대한 상호 참조가 있습니다.

>[!NOTE]
>
>Dynamic Media에서 비디오를 사용하기 전에 Adobe Experience Manager 관리자가 이미 Dynamic Media Cloud Services을 활성화 및 구성했는지 확인하십시오.
>
>* 자세한 내용은 [Dynamic Media Cloud Services 구성](/help/assets/dynamic-media/config-dm.md#configuring-dynamic-media-cloud-services) Dynamic Media 구성 및 [Dynamic Media 문제 해결](/help/assets/dynamic-media/troubleshoot-dm.md).
>


1. **Dynamic Media 비디오 업로드** 다음을 수행하십시오.

   * 자신만의 비디오 인코딩 프로필을 만듭니다. 또는 사전 정의된 _응용 비디오 인코딩_ Dynamic Media과 함께 제공되는 프로필입니다.

      * [비디오 인코딩 프로필 만들기](/help/assets/dynamic-media/video-profiles.md#creating-a-video-encoding-profile-for-adaptive-streaming).
      * 추가 정보 [비디오 인코딩에 대한 우수 사례](#best-practices-for-encoding-videos).
   * 비디오 처리 프로필을 기본 소스 비디오를 업로드할 하나 이상의 폴더에 연결합니다.

      * [폴더에 비디오 프로필 적용](/help/assets/dynamic-media/video-profiles.md#applying-a-video-profile-to-folders).
      * 추가 정보 [디지털 자산 구성](/help/assets/organize-assets.md).
   * 기본 소스 비디오를 폴더에 업로드합니다. 폴더에 비디오를 추가하면 폴더에 할당한 비디오 처리 프로필에 따라 인코딩됩니다.

      * Dynamic Media은 주로 최대 30분 길이의 짧은 비디오와 25x 25보다 큰 최소 해상도를 지원합니다.
      * 각각 최대 15GB의 비디오 파일을 업로드할 수 있습니다.
      * [비디오 업로드](/help/assets/manage-video-assets.md#upload-and-preview-video-assets).
      * 추가 정보 [지원되는 입력 파일 형식](/help/assets/file-format-support.md).
   * 모니터링 방법 [비디오 인코딩이 진행 중입니다.](#monitoring-video-encoding-and-youtube-publishing-progress) 자산 또는 워크플로우 보기에서 선택합니다.




1. **Dynamic Media 비디오 관리** 다음을 수행하여 다음을 수행합니다.

   * 비디오 자산 구성, 탐색 및 검색

      * [디지털 자산 구성](/help/assets/organize-assets.md)
      * [비디오 자산 검색](/help/assets/search-assets.md#custompredicates) 또는 [자산 검색](/help/assets/manage-digital-assets.md#search-assets)
   * 비디오 자산 미리 보기 및 게시

      * 관련 축소판과 함께 비디오의 소스 비디오 및 인코딩된 표현물을 봅니다.
         [비디오 미리 보기](/help/assets/manage-video-assets.md#upload-and-preview-video-assets) 또는 [자산 미리 보기](/help/assets/dynamic-media/previewing-assets.md)
         [비디오 표현물 관리](/help/assets/manage-digital-assets.md#managing-renditions)

      * [뷰어 사전 설정 관리](/help/assets/dynamic-media/managing-viewer-presets.md)
      * [자산 게시](/help/assets/dynamic-media/publishing-dynamicmedia-assets.md)
   * 비디오 메타데이터 작업

      * 제목, 설명 및 태그, 사용자 지정 메타데이터 필드와 같은 비디오의 속성을 편집합니다.
         [비디오 속성 편집](/help/assets/manage-digital-assets.md#editing-properties)

      * [디지털 자산에 대한 메타데이터 관리](/help/assets/manage-metadata.md)
      * [메타데이터 스키마](/help/assets/metadata-schemas.md)
   * 비디오 검토, 승인 및 주석 달기, 전체 버전 제어 유지

      * [비디오에 주석 달기](/help/assets/manage-video-assets.md#annotate-video-assets) 또는 [자산에 주석 달기](/help/assets/manage-digital-assets.md#annotating)

      * [버전 만들기](/help/assets/manage-digital-assets.md#asset-versioning)
      * [자산에서 워크플로우 시작](/help/assets/manage-digital-assets.md#starting-a-workflow-on-an-asset)

      * [폴더 자산 검토](/help/assets/bulk-approval.md)
      * [프로젝트](/help/sites-cloud/authoring/projects/overview.md)




1. **Dynamic Media 비디오 게시** 다음 중 하나를 수행하여 다음을 수행합니다.

   * WCM(웹 컨텐츠 관리) 시스템으로 Experience Manager을 사용하는 경우 웹 페이지에 비디오를 직접 추가할 수 있습니다.

      * [웹 페이지에 비디오 추가](/help/assets/dynamic-media/adding-dynamic-media-assets-to-pages.md).
   * 타사 웹 컨텐츠 관리 시스템을 사용하는 경우 웹 페이지에 비디오를 링크하거나 포함할 수 있습니다.

      * URL을 사용하여 비디오 통합:
         [웹 애플리케이션에 URL 연결](/help/assets/dynamic-media/linking-urls-to-yourwebapplication.md).

      * 웹 페이지에서 포함 코드를 사용하여 비디오 통합:
         [웹 페이지에 비디오 뷰어 포함](/help/assets/dynamic-media/embed-code.md).
   * [YouTube에 비디오 게시](#publishing-videos-to-youtube).
   * [비디오 보고서 생성](#viewing-video-reports).

   * [비디오에 캡션 추가](#adding-captions-to-video).



## Dynamic Media에서 비디오를 사용한 작업 {#working-with-video-in-dynamic-media}

Dynamic Media의 비디오는 데스크탑, 태블릿 및 모바일 장치를 포함하여 여러 화면에서 스트리밍을 위한 고품질 적응형 비디오를 쉽게 게시할 수 있도록 하는 종단 간 솔루션입니다. 응용 비디오 세트는 다른 비트율 및 형식(예: 400kbps, 800kbps 및 1000kbps)으로 인코딩된 동일한 비디오 버전을 그룹화합니다. 데스크탑 컴퓨터 또는 모바일 장치가 사용 가능한 대역폭을 감지합니다.

예를 들어 iOS 모바일 장치에서 3G, 4G 또는 Wi-Fi와 같은 대역폭을 감지합니다. 그런 다음 응용 비디오 세트 내의 다양한 비디오 비트 전송률 중에서 올바른 인코딩된 비디오를 자동으로 선택합니다. 비디오는 데스크탑, 모바일 장치 또는 태블릿으로 스트리밍됩니다.

또한 데스크탑 또는 모바일 장치에서 네트워크 조건이 변경되면 자동으로 비디오 품질이 전환됩니다. 또한 고객이 데스크탑에서 전체 화면 모드로 전환하면 더 나은 해상도를 사용하여 응용 비디오 세트가 응답하여 고객의 보기 환경을 향상시킵니다. 응용 비디오 세트 사용은 고객이 여러 화면 및 장치에서 Dynamic Media 비디오를 재생할 수 있는 최상의 재생 기능을 제공합니다.

비디오 플레이어에서 재생할 인코딩된 비디오 또는 재생 중에 선택할 인코딩된 비디오를 결정하는 데 사용하는 로직은 다음 알고리즘을 기반으로 합니다.

1. 비디오 플레이어는 플레이어 자체에서 &quot;초기 비트율&quot;에 대해 설정된 값에 가장 가까운 비트율을 기반으로 초기 비디오 조각을 로드합니다.
1. 비디오 플레이어는 다음 기준을 사용하여 대역폭 속도 변경 사항을 기반으로 전환합니다.

   1. 플레이어가 예상 대역폭보다 작거나 같은 가장 높은 대역폭 스트림을 선택합니다.
   1. 플레이어는 사용 가능한 대역폭의 80%만 고려합니다. 그러나, 만약 그것이 전환하고 있다면, 그것은 단지 70%에서 더 보수적인데, 그것은 과대평가하고 즉시 다시 돌아서는 것을 피한다.

알고리즘에 대한 자세한 기술 정보는 [https://android.googlesource.com/platform/frameworks/av/+/master/media/libstagefright/httplive/LiveSession.cpp](https://android.googlesource.com/platform/frameworks/av/+/master/media/libstagefright/httplive/LiveSession.cpp)

단일 비디오 및 응용 비디오 세트를 관리하는 경우 다음과 같이 지원됩니다.

* 지원되는 다양한 비디오 형식 및 오디오 포맷의 비디오를 업로드하고 여러 화면에서 재생되도록 비디오를 MP4 H.264 형식으로 인코딩합니다. 사전 정의된 응용 비디오 사전 설정, 단일 비디오 인코딩 사전 설정을 사용하거나 자체 인코딩을 사용자 지정하여 비디오의 품질과 크기를 제어할 수 있습니다.

   * 응용 비디오 세트가 생성되면 MP4 비디오가 포함됩니다.
   * **참고**: 기본/소스 비디오는 응용 비디오 세트에 추가되지 않습니다.

* 모든 HTML 5 비디오 뷰어의 비디오 캡션.
* 비디오 자산을 효율적으로 관리하기 위해 전체 메타데이터 지원을 사용하여 비디오를 구성, 탐색 및 검색할 수 있습니다.
* 응용 비디오 세트를 웹 및 데스크톱, 태블릿 및 모바일 장치에 제공합니다.

응용 비디오 스트리밍은 다양한 iOS 플랫폼에서 지원됩니다. 자세한 내용은 [Dynamic Media 뷰어 참조 안내서](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-aem-assets-dmc/video/c-html5-video-reference.html).

<!-- OUTDATED 2/28/22 BASED ON CQDOC-18692 Dynamic Media supports mobile video playback for MP4 H.264 video. You can find BlackBerry® devices that support this video format at the following: [Supported video formats on BlackBerry®](https://support.blackberry.com/kb/articleDetail?ArticleNumber=000005482).

OUTDATED 2/28/22 BASED ON CQDOC-18692 You can find Windows® devices that support this video format at the following [Supported video formats on Windows® Phone](https://docs.microsoft.com/en-us/windows/uwp/audio-video-camera/supported-codecs). -->

* 다음을 포함하여 Dynamic Media 비디오 뷰어 사전 설정을 사용하여 비디오를 재생합니다.

   * 단일 비디오 뷰어입니다.
   * 비디오와 이미지 컨텐츠를 모두 결합하는 혼합 미디어 뷰어입니다.

* 브랜딩 요구 사항을 충족하도록 비디오 플레이어를 구성합니다.
* 간단한 URL 또는 포함 코드와 함께 웹 사이트, 모바일 사이트 또는 모바일 애플리케이션에 비디오를 통합합니다.

자세한 내용은 [다이내믹 비디오 재생](https://s7d9.scene7.com/s7/uvideo.jsp?asset=GeoRetail/Mop_AVS&amp;config=GeoRetail/Universal_Video1&amp;stageSize=640,480) 샘플.

참조 - [Experience Manager Assets 및 Dynamic Media Classic용 뷰어](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-aem-assets-dmc/c-html5-s7-aem-asset-viewers.html#viewers-aem-assets-dmc) 및 [Experience Manager Assets 전용 뷰어](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-for-aem-assets-only/c-html5-aem-asset-viewers.html#viewers-for-aem-assets-only) 에서 [Dynamic Media 뷰어 참조 안내서](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources.html).

## 우수 사례: HTML 5 비디오 뷰어 사용 {#best-practice-using-the-html-video-viewer}

Dynamic Media HTML5 비디오 뷰어 사전 설정은 강력한 비디오 플레이어입니다. HTML5 비디오 재생과 관련된 많은 일반적인 문제와 모바일 장치와 관련된 문제를 방지하기 위해 이 매개 변수를 사용할 수 있습니다. 예를 들어 적용형 스트리밍 게재가 부족하고 데스크탑 브라우저가 제한적입니다.

플레이어의 디자인 측면에서는 표준 웹 개발 도구를 사용하여 비디오 플레이어의 기능을 디자인할 수 있습니다. 예를 들어 HTML5 및 CSS를 사용하여 단추, 컨트롤 및 사용자 지정 포스터 이미지 배경을 디자인하여 고객에게 맞춤형 모양을 만들어 줄 수 있습니다.

뷰어의 재생 측에서 브라우저의 비디오 기능을 자동으로 감지합니다. 그런 다음 응용 비디오 스트리밍이라고도 하는 HLS(HTTP Live Streaming)를 사용하여 비디오를 제공합니다. 또는 이러한 배달 방법이 없으면 HTML 5 프로그레시브가 대신 사용됩니다.

HTML 5 및 CSS를 사용하여 재생 구성 요소를 디자인하는 기능을 단일 플레이어로 결합할 수 있습니다. 포함된 재생을 가질 수 있으며 브라우저의 기능에 따라 적응형 및 점진적 스트리밍을 사용할 수 있습니다. 이 모든 기능은 데스크탑 및 모바일 사용자 모두에게 리치 미디어 콘텐츠의 범위를 확장하고 간소화된 비디오 경험을 제공할 수 있음을 의미합니다.

참조 - [Experience Manager Assets 전용 뷰어](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-for-aem-assets-only/c-html5-aem-asset-viewers.html#viewers-for-aem-assets-only) 에서 [Dynamic Media 뷰어 참조 안내서](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources.html).

### HTML 5 비디오 뷰어를 사용하여 데스크탑 컴퓨터 및 모바일 장치에서 비디오 재생 {#playback-of-video-on-desktop-computers-and-mobile-devices-using-the-html-video-viewer}

데스크탑 및 모바일 적응형 비디오 스트리밍의 경우 비트율 전환에 사용되는 비디오는 응용 비디오 세트의 모든 MP4 비디오를 기반으로 합니다.

비디오 재생은 HLS 또는 점진적 비디오 다운로드를 사용하여 발생합니다. 6.0, 6.1 및 6.2와 같은 이전 버전의 Experience Manager에서는 비디오가 HTTP를 통해 스트리밍되었습니다.

그러나 Experience Manager 6.3 이상에서는 DM 게이트웨이 서비스 URL이 항상 HTTPS를 사용하므로 비디오가 HTTPS(즉, HLS)를 통해 스트리밍됩니다. 이 기본 동작에는 고객이 영향을 주지 않습니다. 즉, 비디오 스트리밍은 브라우저가 지원하지 않는 한 항상 HTTPS를 통해 발생합니다. (다음 표를 참조하십시오.) 따라서,

* HTTPS 비디오 스트리밍이 있는 HTTPS 웹 사이트가 있는 경우 스트리밍이 좋습니다.
* HTTPS 비디오 스트리밍이 있는 HTTP 웹 사이트가 있는 경우 스트리밍이 문제가 해결되고 웹 브라우저에서 혼합 콘텐츠 문제가 발생하지 않습니다.

HLS는 네트워크 대역폭 용량에 따라 재생을 자동으로 조정하는 응용 비디오 스트리밍을 위한 Apple 표준입니다. 또한 고객이 나머지 비디오가 다운로드될 때까지 기다릴 필요 없이 비디오의 모든 지점을 &quot;찾기&quot;할 수 있습니다.

점진적 비디오는 사용자의 데스크탑 시스템 또는 모바일 장치에 로컬로 비디오를 다운로드하여 저장하여 전달됩니다.

다음 표에서는 [Dynamic Media HTML5 비디오 뷰어](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-for-aem-assets-only/interactive-video/c-html5-aem-int-video.html#interactive-video).

<table>
 <tbody>
  <tr>
   <td><strong>장치</strong></td>
   <td><strong>브라우저</strong></td>
   <td><strong>비디오 재생 모드</strong></td>
  </tr>
  <tr>
   <td>데스크톱</td>
   <td>Internet Explorer 9 및 10</td>
   <td>점진적 다운로드.</td>
  </tr>
  <tr>
   <td>데스크톱</td>
   <td>Internet Explorer 11+</td>
   <td>Windows® 8 및 Windows® 10의 경우 - HLS가 요청될 때마다 HTTPS를 강제로 사용합니다. 알려진 제한 사항: HLS의 HTTP가 이 브라우저/운영 체제 조합에서 작동하지 않습니다<br /> <br /> Windows® 7 - 점진적 다운로드의 경우. HTTP 및 HTTPS 프로토콜을 선택하는 표준 로직을 사용합니다.</td>
  </tr>
  <tr>
   <td>데스크톱</td>
   <td>Firefox 23-44</td>
   <td>점진적 다운로드.</td>
  </tr>
  <tr>
   <td>데스크톱</td>
   <td>Firefox 45 이상</td>
   <td>HLS</td>
  </tr>
  <tr>
   <td>데스크톱</td>
   <td>Chrome</td>
   <td>HLS</td>
  </tr>
  <tr>
   <td>데스크톱</td>
   <td>Safari(Mac)</td>
   <td>HLS</td>
  </tr>
  <tr>
   <td>모바일</td>
   <td>Chrome(Android™ 6 이하)</td>
   <td>점진적 다운로드.</td>
  </tr>
  <tr>
   <td>모바일</td>
   <td>Chrome(Android™ 7 이상)</td>
   <td>HLS</td>
  </tr>
  <tr>
   <td>모바일</td>
   <td>Android™(기본 브라우저)</td>
   <td>점진적 다운로드.</td>
  </tr>
  <tr>
   <td>모바일</td>
   <td>Safari(iOS)</td>
   <td>HLS</td>
  </tr>
  <tr>
   <td>모바일</td>
   <td>Chrome(iOS)</td>
   <td>HLS</td>
  </tr>
 </tbody>
</table>

<!--  THIS LINE WAS REMOVED FROM THE TABLE ABOVE ON FEB 28, 2022 BASED ON CQDOC 18692 -RSB <tr>
   <td>Mobile</td>
   <td>BlackBerry®</td>
   <td>HLS</td>
  </tr>
 -->

## Dynamic Media 비디오 솔루션 아키텍처 {#architecture-of-dynamic-media-video-solution}

다음 그래픽은 DMGateway(Dynamic Media Hybrid 모드)를 통해 업로드 및 인코딩되고 공개 소비에 사용할 수 있는 비디오의 전체 작성 워크플로우를 보여줍니다.

![chlimage_1-427](assets/chlimage_1-427.png)

## 비디오용 하이브리드 게시 아키텍처 {#hybrid-publishing-architecture-for-videos}

![chlimage_1-428](assets/chlimage_1-428.png)

## 비디오 인코딩 우수 사례 {#best-practices-for-encoding-videos}

다음 **Dynamic Media 인코딩 비디오** Dynamic Media을 활성화하고 비디오 Cloud Services을 설정한 경우 워크플로우가 비디오를 인코딩합니다. This workflow captures workflow process history and failure information. 자세한 내용은 [비디오 인코딩 및 YouTube 게시 진행 모니터링](#monitoring-video-encoding-and-youtube-publishing-progress). Dynamic Media을 활성화하고 비디오 Cloud Services을 설정한 경우, **[!UICONTROL Dynamic Media 인코딩 비디오]** 워크플로우는 비디오를 업로드할 때 자동으로 적용됩니다. (Dynamic Media을 사용하지 않는 경우, **[!UICONTROL DAM 자산 업데이트]** 워크플로우가 적용됩니다.)

다음은 소스 비디오 파일을 인코딩하기 위한 우수 사례 팁입니다.

<!-- For advice about video encoding, see the following:

* [Streaming 101: The Basics — Codecs, Bandwidth, Data Rate, and Resolution](https://www.adobe.com/go/learn_s7_streaming101_en).
* [Video Encoding Basics](https://www.adobe.com/go/learn_s7_encoding_en). -->

### 소스 비디오 파일 {#source-video-files}

비디오 파일을 인코딩할 때 가능한 가장 높은 품질의 소스 비디오 파일을 사용하십시오. 이전에 인코딩된 비디오 파일은 이미 압축되었으므로 해당 파일을 사용하지 마십시오. 또한 인코딩을 통해 하위 품질의 비디오가 생성됩니다.

* Dynamic Media은 주로 최대 30분 길이의 짧은 비디오와 25x 25보다 큰 최소 해상도를 지원합니다.
* 각각 최대 15GB의 기본 소스 비디오 파일을 업로드할 수 있습니다.

다음 표에서는 소스 비디오 파일을 인코딩하기 전에 사용해야 하는 권장 크기, 종횡비 및 최소 비트 전송률에 대해 설명합니다.

| 크기 | 종횡비 | 최소 비트 전송률 |
|--- |--- |--- |
| 1024 X 768 | 4:3 | 대부분의 비디오에는 4500kbps입니다. |
| 1280 X 720 | 16:9 | 3000 - 6000kbps(비디오의 동작 양에 따라 다름) |
| 1920 X 1080 | 16:9 | 6000 - 8000kbps(비디오의 동작 양에 따라 다름) |

### 파일의 메타데이터 가져오기 {#obtaining-a-file-s-metadata}

비디오 편집 도구를 사용하여 파일의 메타데이터를 보거나 메타데이터를 얻기 위해 디자인된 응용 프로그램을 사용하여 파일의 메타데이터를 가져올 수 있습니다. 다음은 타사 응용 프로그램인 MediaInfo를 사용하여 비디오 파일의 메타데이터를 가져오는 방법에 대한 지침입니다.

1. 이동 [MediaInfo 다운로드](https://mediaarea.net/en/MediaInfo/Download).
1. GUI 버전에 대한 설치 프로그램을 선택하여 다운로드하고 설치 지침을 따르십시오.
1. 설치 후 비디오 파일(Windows®만 해당)을 마우스 오른쪽 단추로 클릭하고 MediaInfo를 선택하거나 MediaInfo를 열고 비디오 파일을 응용 프로그램으로 드래그합니다. 너비, 높이, fps 등 비디오 파일과 관련된 모든 메타데이터가 표시됩니다.

### 종횡비 {#aspect-ratio}

기본 소스 비디오 파일에 대한 비디오 인코딩 사전 설정을 선택하거나 만들 때는 사전 설정이 기본 소스 비디오 파일과 동일한 종횡비인지 확인하십시오. 종횡비는 비디오 높이에 대한 너비의 비율입니다.

비디오 파일의 종횡비를 결정하려면 파일의 메타데이터를 가져와서 파일의 폭과 높이를 확인합니다(위의 파일 메타데이터 가져오기 참조). 다음 공식을 사용하여 종횡비를 확인합니다.

너비/높이 = 종횡비

다음 표에서는 공식 결과가 일반적인 종횡비 선택 사항으로 변환되는 방법을 설명합니다.

| 수식 결과 | 종횡비 |
|--- |--- |
| 1.33 | 4:3 |
| 0.75 | 3:4 |
| 1.78 | 16:9 |
| 0.56 | 9:16 |

예를 들어, 1440 너비 x 1080 높이의 비디오에는 1440/1080 또는 1.33의 종횡비가 있습니다. 이 경우 4:3 종횡비가 있는 비디오 인코딩 사전 설정을 선택하여 비디오 파일을 인코딩합니다.

### 비트율 {#bitrate}

비트율은 비디오 재생 1초를 구성하기 위해 인코딩된 데이터의 양입니다. 비트율은 초당 킬로비트(Kbps)로 측정됩니다.

>[!NOTE]
>
>모든 코덱에서는 손실 압축을 사용하므로 비디오 품질에서 비트율이 가장 중요합니다. 손실 압축을 사용하면 비디오 파일을 압축할수록 품질이 더 저하됩니다. 따라서 다른 모든 특성(해상도, 프레임 속도 및 코덱은)은 비트율이 낮을수록 압축 파일의 품질이 낮습니다.

비트율 인코딩을 선택할 때 두 가지 유형을 선택할 수 있습니다.

* **[!UICONTROL 상수 비트율 인코딩]** (CBR) - CBR 인코딩 중에 비트율 또는 초당 비트 수가 인코딩 프로세스 전체에서 동일하게 유지됩니다. CBR 인코딩은 전체 비디오에서 설정에 설정된 데이터 속도를 유지합니다. 또한 CBR 인코딩은 품질을 위해 미디어 파일을 최적화하지는 않지만 저장 공간에 저장합니다.
비디오가 전체 비디오 전체에서 유사한 동작 수준을 포함하는 경우 CBR을 사용합니다. CBR은 비디오 컨텐츠를 스트리밍하는 데 가장 일반적으로 사용됩니다. 참조 - [사용자가 추가한 비디오 인코딩 매개 변수 사용](/help/assets/dynamic-media/video-profiles.md#using-custom-added-video-encoding-parameters).

* **[!UICONTROL 변수 비트율 인코딩]** (VBR) - VBR 인코딩은 압축기에 필요한 데이터를 기준으로 사용자가 설정한 상한과 데이터 속도를 조절합니다. 이 기능은 VBR 인코딩 프로세스 중에 미디어 파일의 비트율이 미디어 파일 비트율 요구 사항에 따라 동적으로 증가 또는 감소함을 의미합니다.
VBR은 인코딩하는 데 더 오래 걸리지만 가장 유리한 결과를 생성합니다. 미디어 파일의 품질이 우수합니다. VBR은 비디오 컨텐츠의 http 점진적 게재에 가장 일반적으로 사용됩니다.

VBR 대 CRB는 언제 사용합니까?
VBR과 CBR을 선택할 때는 미디어 파일에 VBR을 사용하는 것이 좋습니다. VBR은 경쟁적 비트율로 고품질의 파일을 제공합니다. VBR을 사용하는 경우 2단계 인코딩에 사용하고 최대 비트율을 대상 비디오 비트율의 1.5배로 설정하십시오.

비디오 인코딩 사전 설정을 선택하는 경우 대상 최종 사용자의 연결 속도를 고려해야 합니다. 해당 속도의 80%인 데이터 비율이 있는 사전 설정을 선택합니다. 예를 들어 대상 최종 사용자의 연결 속도가 1000Kbps인 경우 가장 좋은 사전 설정은 비디오 데이터 속도가 800Kbps인 사전 설정입니다.

이 표에서는 일반적인 연결 속도의 데이터 속도를 설명합니다.

| 속도(Kbps) | 연결 유형 |
|--- |--- |
| 256년 | 전화 접속 연결입니다. |
| 800 | 일반적인 모바일 연결. 이 연결의 경우 3G 경험에 대해 400~최대 800 범위의 데이터 전송률을 타깃팅하십시오. |
| 2000년 | 일반 광대역 데스크탑 연결. 이 연결의 경우 평균 1200-1500Kbps로 800-2000Kbps 범위의 데이터 속도를 타깃팅합니다. |
| 5000 | 일반적인 고속 광대역 연결 대부분의 소비자는 이 속도로 비디오를 전달할 수 없으므로 이 상위 범위의 인코딩을 사용하지 않는 것이 좋습니다. |

### 해결 {#resolution}

**해결 방법** 비디오 파일의 높이 및 너비를 픽셀 단위로 설명합니다. 대부분의 소스 비디오는 고해상도(예: 1920 x 1080)로 저장됩니다. 스트리밍을 위해 소스 비디오는 더 작은 해상도(640 x 480 이하)로 압축됩니다.

해상도 및 데이터 전송률은 비디오 품질을 결정하는 두 가지 통합 연결 요소입니다. 동일한 비디오 품질을 유지하려면 비디오 파일의 픽셀 수가 많을수록 해상도가 높을수록 데이터 속도가 빨라야 합니다. 예를 들어, 320 x 240 해상도와 640 x 480 해상도 비디오 파일에서 프레임당 픽셀 수를 고려해 보십시오.

| 해결 | 프레임당 픽셀 수 |
|--- |--- |
| 320 x 240 | 76,800 |
| 640 x 480 | 307,200 |

640 x 480 파일은 프레임당 4배 더 많은 픽셀을 가지고 있습니다. 이러한 두 가지 예제 해상도에 대해 동일한 데이터 속도를 구현하려면 640 x 480 파일에 4배 압축을 적용하여 비디오 품질을 줄일 수 있습니다. 따라서, 비디오 데이터 속도가 250Kbps이면 320 x 240 해상도로 고품질로 볼 수 있지만, 640 x 480 해상도에서는 볼 수 없습니다.

일반적으로 데이터 속도가 높을수록 비디오가 더 잘 표시되고 해상도가 높을수록 보기 품질을 유지해야 하는 데이터 비율이 높습니다(해상도가 낮은 경우와 비교).

해상도와 데이터 전송률이 연결되어 있으므로 비디오를 인코딩할 때 두 가지 옵션이 있습니다.

* 데이터 비율을 선택한 다음 선택한 데이터 속도에 적합한 최고 해상도로 인코딩합니다.
* 해상도를 선택한 다음 선택한 해상도로 고품질의 비디오를 구현하는 데 필요한 데이터 속도로 인코딩하십시오.

기본 소스 비디오 파일에 대한 비디오 인코딩 사전 설정을 선택(또는 생성)할 때 이 표를 사용하여 올바른 해상도를 타깃팅하십시오.

| 해결 | 높이(픽셀) | 화면 크기 |
|--- |--- |--- |
| 240p | 240년 | 작은 화면 |
| 300p | 300 | 일반적으로 모바일 장치용 작은 화면 |
| 360p | 360 | 작은 화면 |
| 480p | 480 | 미디어 화면 |
| 720p | 720년 | 대형 화면 |
| 1080p | 1080년 | HD 대형 화면 |

### Fps(초당 프레임 수) {#fps-frames-per-second}

미국 및 일본에서는 대부분의 비디오가 초당 29.97프레임(fps)으로 촬영됩니다. 유럽에서는 대부분의 비디오가 25fps로 촬영됩니다. 필름은 24fps로 촬영됩니다.

기본 소스 비디오 파일의 fps 속도와 일치하는 비디오 인코딩 사전 설정을 선택합니다. 예를 들어 기본 소스 비디오가 25fps인 경우 25fps로 인코딩 사전 설정을 선택합니다. 기본적으로 모든 사용자 지정 인코딩은 기본 소스 비디오 파일의 fps를 사용합니다. 따라서 비디오 인코딩 사전 설정을 만들 때 fps 설정을 명시적으로 지정할 필요가 없습니다.

### 비디오 인코딩 차원 {#video-encoding-dimensions}

최적의 결과를 얻으려면 인코딩 차원을 선택하면 소스 비디오가 인코딩된 모든 비디오의 전체 배수입니다.

이 비율을 계산하려면 소스 너비를 인코딩된 너비로 나누어 너비 비율을 가져옵니다. 그런 다음 소스 높이를 인코딩된 높이로 나눈 뒤 높이 비율을 얻습니다.

결과 비율이 전체 정수인 경우 비디오 크기가 최적으로 조절됩니다. 결과 비율이 정수가 아닌 경우, 나머지 픽셀 가공물을 화면에 남겨 두면 비디오 품질에 영향을 줍니다. 이 효과는 비디오에 텍스트가 있을 때 가장 잘 보입니다.

예를 들어 소스 비디오가 1920 x 1080이라고 가정합니다. 다음 표에서 세 개의 인코딩된 비디오는 사용할 최적의 인코딩 설정을 제공합니다.

| 비디오 유형 | 너비 x 높이 | 폭 비율 | 높이 비율 |
|--- |--- |--- |--- |
| 소스 | 1920x1080 | 1 | 1 |
| 인코딩됨 | 960 x 540 | 2 | 2개 |
| 인코딩됨 | 640 x 360 | 3 | 3 |
| 인코딩됨 | 480 x 270 | 4 | 4 |

### 인코딩된 비디오 파일 형식 {#encoded-video-file-format}

Dynamic Media에서는 MP4 H.264 비디오 인코딩 사전 설정을 사용하는 것이 좋습니다. MP4 파일은 H.264 비디오 코덱을 사용하기 때문에 고품질의 비디오를 제공하지만 압축된 파일 크기로 제공합니다.

## YouTube에 비디오 게시 {#publishing-videos-to-youtube}

Experience Manager Assets에서 관리하는 비디오 자산을 이전에 만든 YouTube 채널에 직접 게시할 수 있습니다.

비디오 자산을 YouTube에 게시하려면 태그를 사용하여 Experience Manager Assets의 비디오 자산에 태그를 지정합니다. 이러한 태그를 YouTube 채널과 연관시킵니다. 비디오 자산의 태그가 YouTube 채널의 태그와 일치하면 비디오가 YouTube에 게시됩니다. YouTube에 게시는 연결된 태그가 사용되는 한 비디오의 일반 게시와 함께 발생합니다.

YouTube은 자체 인코딩을 수행합니다. 따라서 Experience Manager에 업로드된 원본 비디오 파일은 Dynamic Media의 인코딩이 만들어진 비디오 변환 대신 YouTube에 게시됩니다. Dynamic Media을 사용하여 비디오를 처리할 필요는 없지만 재생에 뷰어 사전 설정이 필요한 경우 처리할 필요가 있습니다.

비디오 처리 프로필을 건너뛰고 YouTube에 바로 게시할 경우 Experience Manager 자산의 비디오 자산이 볼 수 있는 축소판을 가져오지 않음을 의미합니다. 또한 인코딩되지 않은 비디오는 Dynamic Media 자산 유형에서 작동하지 않습니다.

YouTube 서버에 비디오 자산을 게시하려면 YouTube을 사용하여 안전하고 안전한 서버 간 확인을 위해 다음 작업을 완료해야 합니다.

1. [Google Cloud 설정 구성](#configuring-google-cloud-settings)
1. [YouTube 채널 만들기](#creating-a-youtube-channel)
1. [게시할 태그 추가](#adding-tags-for-publishing)
1. [Experience Manager에서 YouTube 설정](#setting-up-youtube-in-aem)
1. [(선택 사항) 업로드된 비디오에 대한 기본 YouTube 속성 설정을 자동화합니다](#optional-automating-the-setting-of-default-youtube-properties-for-your-uploaded-videos)
1. [YouTube 채널에 비디오 게시](#publishing-videos-to-your-youtube-channel)
1. [(선택 사항) YouTube에서 게시된 비디오를 확인합니다](/help/assets/dynamic-media/video.md#optional-verifying-the-published-video-on-youtube)
1. [웹 애플리케이션에 YouTube URL 연결](#linking-youtube-urls-to-your-web-application)

다음을 수행할 수도 있습니다 [YouTube에서 제거할 비디오 게시 취소](#unpublishing-videos-to-remove-them-from-youtube).

### Google Cloud 설정 구성 {#configuring-google-cloud-settings}

YouTube에 게시하려면 Google 계정이 필요합니다. GMAIL 계정이 있는 경우 이미 Google 계정이 있습니다. Google 계정이 없는 경우 쉽게 만들 수 있습니다. 비디오 자산을 YouTube에 게시하려면 자격 증명이 필요하므로 계정이 필요합니다. <!-- hidden March 3 2022 If you have an account already created, then skip this task and proceed directly to [Create a YouTube channel](#creating-a-youtube-channel). -->

Google Cloud와 YouTube에 사용된 Google 계정에 사용된 계정이 동일할 필요가 없습니다.

Google은 사용자 인터페이스를 주기적으로 변경합니다. 따라서 YouTube에 비디오를 게시하는 단계는 아래에 설명된 것과 약간 다를 수 있습니다. 이 주의 사항은 비디오가 업로드되었는지를 확인하려고 할 때도 YouTube에 적용됩니다.

>[!NOTE]
>
>다음 단계는 작성 시 정확했다. 그러나 Google은 예고 없이 주기적으로 클라우드 웹 페이지를 업데이트합니다. 따라서 일부 구성 옵션의 이름은 Google 사용자 인터페이스에서 단계에 사용된 이름과 약간 다르게 지정할 수 있습니다.

**Google Cloud 설정을 구성하려면:**

1. Google 계정을 만듭니다.
   [https://accounts.google.com/signup/v2?service=mail&amp;flowName=GlifWebSignIn&amp;flowEntry=SignUp](https://accounts.google.com/signup/v2?service=mail&amp;flowName=GlifWebSignIn&amp;flowEntry=SignUp)

   이미 Google 계정이 있는 경우 다음 단계로 건너뛸 수 있습니다.

1. 이동 [https://cloud.google.com/](https://cloud.google.com/).
1. 설정 **[!UICONTROL Google Cloud]** 페이지 오른쪽 상단 모서리에서 을(를) 선택합니다. **[!UICONTROL 콘솔]**.

   필요한 경우 **[!UICONTROL 로그인]** Google 계정 자격 증명을 사용하여 확인 **[!UICONTROL 콘솔]** 선택 사항입니다.

1. 설정 **[!UICONTROL 대시보드]** 페이지, 오른쪽 **[!UICONTROL Google Cloud Platform]**&#x200B;에서 을(를) 선택합니다. **[!UICONTROL 프로젝트]** 드롭다운 목록을 클릭하여 **[!UICONTROL 프로젝트 선택]** 대화 상자
1. 에서 **[!UICONTROL 프로젝트 선택]** 대화 상자, 선택 **[!UICONTROL 새 프로젝트]**.
1. 에서 **[!UICONTROL 새 프로젝트]** 대화 상자, **[!UICONTROL 프로젝트 이름]** 필드에서 새 프로젝트의 이름을 입력합니다.

   프로젝트 ID는 프로젝트 이름을 기반으로 합니다. 따라서 프로젝트 이름을 신중하게 선택합니다. 만든 후에는 변경할 수 없습니다. 또한 나중에 Experience Manager에서 YouTube을 설정할 때 동일한 프로젝트 ID를 다시 입력해야 합니다. 그러므로, 그것을 적으세요.

1. **[!UICONTROL 만들기]**&#x200B;를 선택합니다.

1. 다음 중 하나를 수행합니다.

   * 프로젝트의 대시보드에서 **[!UICONTROL 시작하기]** 카드, 선택 **[!UICONTROL API 탐색 및 활성화]**.
   * 프로젝트의 대시보드에서 **[!UICONTROL API]** 카드, 선택 **[!UICONTROL API 개요로 이동]**.

1. 위쪽 중간 **[!UICONTROL API 및 서비스]** 페이지를 선택하고 **[!UICONTROL API 및 서비스 활성화]**.<!-- NEXT STEP BELOW IS STEP 10 -->
1. 설정 **[!UICONTROL API 라이브러리]** 페이지, 왼쪽, 아래 **[!UICONTROL 카테고리]**, 선택 **[!UICONTROL YouTube]**. 페이지의 오른쪽에서 을 선택합니다 **[!UICONTROL YouTube]**.
1. 설정 **[!UICONTROL YouTube]** 페이지를 선택하고 **[!UICONTROL YouTube 데이터 API v3]**.
1. 설정 **[!UICONTROL YouTube 데이터 API v3]** 페이지를 선택하고 **[!UICONTROL 관리]**.

   ![6_5_googleaccount-api-manage](assets/6_5_googleaccount-apis-manage.png)

1. API를 사용하려면 자격 증명이 필요합니다. 필요한 경우 **[!UICONTROL API 및 서비스]** 페이지를 선택하고 **[!UICONTROL 자격 증명]**.
1. 설정 **[!UICONTROL 자격 증명]** 페이지 상단 근처에 있는 를 선택합니다. **[!UICONTROL 자격 증명 만들기]**&#x200B;를 선택하고 을 선택합니다. **[!UICONTROL OAuth 클라이언트 ID]**.
1. 설정 **[!UICONTROL OAuth 클라이언트 ID 만들기]** 페이지, **[!UICONTROL 애플리케이션 유형]** 드롭다운 목록에서 **[!UICONTROL 웹 애플리케이션]**.

   ![6_5_googleaccount-apis-applicationtype](/help/assets/dynamic-media/assets/6_5_googleaccount-apis-applicationtype.png)

1. 다음 중 하나를 수행하십시오.

   * 에서 **[!UICONTROL 이름]** 필드에서 OAuth 2.0 클라이언트의 고유 이름을 입력합니다.
   * Google이 이미 **[!UICONTROL 이름]** 필드.

1. 아래에 **[!UICONTROL 인증된 JavaScript 원본]** 제목, 선택 **[!UICONTROL URI 추가]**.

   ![6_5_googleaccount-apis-name-authorizations](/help/assets/dynamic-media/assets/6_5_googleaccount-apis-nameauthorizations.png)

1. 에서 **[!UICONTROL URI]** 텍스트 필드에 다음 경로를 입력하고 경로에 고유한 도메인과 포트 번호를 대체한 다음 키를 누릅니다 **[!UICONTROL Enter 키]** 목록에 경로를 추가하려면 다음을 수행합니다.

   `https://<servername.domain>:<port_number>`

   예, `https://1a2b3c.mycompany.com:4321`

   >[!NOTE]
   >
   >위의 URI 경로 예제는 가설 및 설명 목적으로만 사용됩니다.

1. 아래에 **[!UICONTROL 허가된 리디렉션 URI]** 제목을 선택하고 URI 추가를 선택합니다.
1. 에서 **[!UICONTROL URI]** 텍스트 필드에 다음 경로를 입력하고 경로에 고유한 도메인과 포트 번호를 대체한 다음 키를 누릅니다 **[!UICONTROL Enter 키]** 목록에 경로를 추가하려면 다음을 수행합니다.

   `https://<servername.domain>:<port_number>/etc/cloudservices/youtube.youtubecredentialcallback.json`

   예, `https://1a2b3c.mycompany.com:4321/etc/cloudservices/youtube.youtubecredentialcallback.json`

   >[!NOTE]
   >
   >위의 URI 경로 예제는 가설 및 설명 목적으로만 사용됩니다.

1. 아래쪽으로 **[!UICONTROL OAuth 클라이언트 ID 만들기]** 페이지를 선택하고 **[!UICONTROL 만들기]**.
1. 설정 **[!UICONTROL OAuth 클라이언트가 생성됨]** 대화 상자에서 다음을 수행합니다.

   * (선택 사항) **[!UICONTROL 클라이언트 ID]** 및 **[!UICONTROL 클라이언트 암호]** 필드를 작성하고 저장합니다.
   * 선택 **[!UICONTROL JSON 다운로드]**&#x200B;를 입력한 다음 JSON 파일을 저장합니다.

   나중에 Adobe Experience Manager에서 YouTube을 설정할 때 이 다운로드한 JSON 파일이 필요합니다.

   ![6_5_googleaccount-apis-oauthclientcreated](/help/assets/dynamic-media/assets/6_5_googleaccount-apis-oauthclientcreated.png)

1. 설정 **[!UICONTROL OAuth 클라이언트가 생성됨]** 대화 상자, 선택 **[!UICONTROL 확인]**.
1. Google 계정에서 로그아웃합니다. 이제 YouTube 채널을 만듭니다.

### YouTube 채널 만들기 {#creating-a-youtube-channel}

YouTube에 비디오를 게시하려면 하나 이상의 채널이 있어야 합니다. YouTube 채널을 이미 만든 경우 이 작업을 건너뛰고 로 이동할 수 있습니다. [게시할 태그 추가](/help/assets/dynamic-media/video.md#adding-tags-for-publishing).

>[!CAUTION]
>
>YouTube에서 이미 하나 이상의 채널을 설정했는지 확인하십시오 *이전* Experience Manager의 YouTube 설정에서 채널을 추가합니다( [Experience Manager에서 YouTube 설정](#setting-up-youtube-in-aem) 아래에 표시됩니다. 채널 설정을 수행하지 않으면 기존 채널에 대해 경고가 표시되지 않습니다. 그러나 채널을 추가할 때는 Google 확인이 계속 발생하지만, 비디오를 전송할 채널을 선택하는 옵션은 없습니다.

**YouTube 채널을 만들려면:**

1. 이동 [https://www.youtube.com](https://www.youtube.com/) Google 계정 자격 증명을 사용하여 로그인합니다.
1. YouTube 페이지의 오른쪽 위 모서리에서 프로필 사진을 선택한 후(단색 원 내에 문자로 표시될 수도 있음) **[!UICONTROL YouTube 설정]** (라운드 톱니바퀴 아이콘).
1. 개요 페이지의 추가 기능 제목 아래에서 을 선택합니다 **[!UICONTROL 내 채널을 모두 보거나 채널을 만듭니다]**.
1. 채널 페이지에서 **[!UICONTROL 새 채널 만들기]**.
1. 브랜드 계정 페이지의 브랜드 계정 이름 필드에 비디오 자산을 게시하려는 회사 이름 또는 다른 채널 이름을 입력한 다음 을 선택합니다 **[!UICONTROL 만들기]**.

   여기에 입력하는 이름을 기억하십시오. Experience Manager에서 YouTube을 설정해야 할 경우에는 다시 입력해야 합니다.

1. (선택 사항) 필요한 경우 채널을 더 추가합니다.

   이제 게시할 태그를 추가합니다.

### 게시할 태그 추가 {#adding-tags-for-publishing}

비디오를 YouTube에 게시하려면 Experience Manager은 태그를 하나 이상의 YouTube 채널에 연결합니다. 게시할 태그를 추가하려면 [태그 관리](/help/sites-cloud/authoring/features/tags.md).

또는 Experience Manager에서 기본 태그를 사용하려는 경우 이 작업을 건너뛰고 로 이동할 수 있습니다. [Experience Manager에서 YouTube 설정](#setting-up-youtube-in-aem).

>[!NOTE]
>
>Cloud Service이 구성된 후에는 이 시점에서 YouTube 게시 복제 에이전트를 활성화하는 데 다른 구성이 필요하지 않습니다. Cloud Service 구성이 저장될 때 활성화되었기 때문입니다.

<!-- ### Enabling the YouTube Publish replication agent {#enabling-the-youtube-publish-replication-agent}

After you enable the YouTube Publish replication agent, if you want to test the connection to the Google Cloud account, select **[!UICONTROL Test Connection]**. A browser tab displays the connection results. If you have added YouTube Channels, then a listing of those is displayed as part of the test.

1. In the upper-left corner of Experience Manager, select the Experience Manager logo, then in the left rail, navigate to **[!UICONTROL Tools]** > **[!UICONTROL Deployment]** > **[!UICONTROL Replication]** > **[!UICONTROL Agents on Author]**.
1. On the Agents of Author page, select **[!UICONTROL YouTube Publish (youtube)]**.
1. On the toolbar, to the right of Settings, select **[!UICONTROL Edit]**.
1. Select the **[!UICONTROL Enabled]** checkbox to turn on the replication agent.
1. Select **[!UICONTROL OK]**. -->

### Experience Manager에서 YouTube 설정 {#setting-up-youtube-in-aem}

Experience Manager 6.4부터 Experience Manager에서 YouTube 게시를 설정하는 새로운 터치 사용자 인터페이스 방법이 도입되었습니다. 사용 중인 Experience Manager의 설치된 인스턴스에 따라 다음 중 하나를 수행합니다.

* 6.4 이전 Experience Manager에서 YouTube을 구성하려면 다음을 참조하십시오 [6.4 이전 Experience Manager에서 YouTube 설정](/help/assets/dynamic-media/video.md#setting-up-youtube-in-aem-before).
* Experience Manager 6.4 이상에서 YouTube을 구성하려면 다음을 참조하십시오 [Experience Manager 6.4 이상에서 YouTube 설정](#setting-up-youtube-in-aem-and-later).

#### Experience Manager 6.4 이상에서 YouTube 설정 {#setting-up-youtube-in-aem-and-later}

1. 관리자로 Dynamic Media 인스턴스에 로그인해야 합니다.
1. Experience Manager의 왼쪽 위 모서리에서 Experience Manager 로고를 선택한 다음 왼쪽 레일에서 로 이동합니다. **[!UICONTROL 도구]**(망치 아이콘) > **[!UICONTROL Cloud Services]** > **[!UICONTROL YouTube 게시 구성]**.
1. 선택 **[!UICONTROL 글로벌]** (선택하지 마십시오.)

1. 글로벌 페이지의 오른쪽 위 모서리 근처에 있는 를 선택합니다. **[!UICONTROL 만들기]**.
1. On the Create YouTube Configuration page, under Google Cloud Platform Settings, in the **[!UICONTROL Application Name]** field, enter the Google Project ID.

   처음에 Google Cloud 설정을 구성할 때 프로젝트 ID를 지정했습니다.
YouTube 구성 만들기 페이지를 열어 둡니다. 곧 다시 돌아오실 겁니다

   ![6_5_youtubepublish-createyoutubeconfiguration](assets/6_5_youtubepublish-createyoutubeconfiguration.png)

1. 일반 텍스트 편집기를 사용하여 작업에서 이전에 다운로드하여 저장한 JSON 파일을 엽니다 [Google Cloud 설정 구성](/help/assets/dynamic-media/video.md#configuring-google-cloud-settings).
1. 전체 JSON 텍스트를 선택하고 복사합니다.
1. Return to the YouTube Account Settings dialog box. In the **[!UICONTROL JSON Config]** field, paste the JSON text.
1. 페이지의 오른쪽 위 모서리 근처에 있는 를 선택합니다. **[!UICONTROL 저장]**.

   이제 Experience Manager에서 YouTube 채널을 설정합니다.

1. 선택 **[!UICONTROL 채널 추가]**.
1. 채널 이름 필드에 작업에서 만든 채널의 이름을 입력합니다 **[!UICONTROL YouTube에 하나 이상의 채널 추가]** 더 일찍

   원하는 경우 설명을 선택적으로 추가할 수 있습니다.

1. 선택 **[!UICONTROL 추가]**.
1. YouTube/Google 확인이 표시됩니다. Google Cloud 계정에 아직 로그인하지 않은 경우 이 단계를 건너뜁니다.

   * Google 프로젝트 ID 및 위의 JSON 텍스트와 연결된 Google 사용자 이름 및 암호를 입력합니다.
   * 계정에 두 개 이상의 항목이 표시되는 채널 수에 따라 다릅니다. 채널을 선택합니다. 전자 메일 주소를 선택하지 마십시오; 채널이 아닙니다.
   * 다음 페이지에서 **[!UICONTROL 수락]** 이 채널에 대한 액세스를 허용합니다.

1. 선택 **[!UICONTROL 허용]**.

   이제 게시할 태그를 설정합니다.

1. **[!UICONTROL 게시할 태그 설정]** - Cloud Services > YouTube 페이지에서 연필 아이콘을 선택하여 사용할 태그 목록을 편집합니다.
1. Experience Manager에서 사용 가능한 태그 목록을 표시하려면 드롭다운 목록 아이콘(거꾸로 있는 삽입 기호)을 선택합니다.
1. 태그를 추가하려면 하나 이상의 태그를 선택합니다.

   추가한 태그를 삭제하려면 태그를 선택하고 을(를) 선택합니다 **[!UICONTROL X]**.

1. 원하는 태그 추가를 마치면 를 선택합니다 **[!UICONTROL 저장]**.

   이제 비디오를 YouTube 채널에 게시합니다.

#### 6.4 이전 Experience Manager에서 YouTube 설정 {#setting-up-youtube-in-aem-before}

1. 관리자로 Dynamic Media 인스턴스에 로그인해야 합니다.

1. Experience Manager의 왼쪽 위 모서리에서 Experience Manager 로고를 선택한 다음 왼쪽 레일에서 로 이동합니다. **[!UICONTROL 도구]** (망치 아이콘) > **[!UICONTROL 배포]** > **[!UICONTROL Cloud Services]**.
1. 타사 서비스 머리글 아래에 있는 YouTube을 선택합니다 **[!UICONTROL 지금 구성]**.
1. 구성 만들기 대화 상자의 각 필드에 제목(필수)과 이름(선택 사항)을 입력합니다.
1. **[!UICONTROL 만들기]**&#x200B;를 선택합니다.
1. In the YouTube Account Settings dialog box, in the **[!UICONTROL Application Name]** field, enter the Google Project ID.

   처음에 프로젝트 ID를 지정한 경우 [구성된 Google Cloud 설정](/help/assets/dynamic-media/video.md#configuring-google-cloud-settings) 더 일찍
YouTube 계정 설정 대화 상자를 열어 둡니다. 곧 다시 돌아오실 겁니다

1. 일반 텍스트 편집기를 사용하여 Google Cloud 설정 구성 작업에서 이전에 다운로드하여 저장한 JSON 파일을 엽니다.
1. 전체 JSON 텍스트를 선택하고 복사합니다.
1. YouTube 계정 설정 대화 상자로 돌아갑니다. 에서 **[!UICONTROL JSON 구성]** 필드에 JSON 텍스트를 붙여넣습니다.
1. 선택 **[!UICONTROL 확인]**.

   이제 Experience Manager에서 YouTube 채널을 설정합니다.

1. 오른쪽 **[!UICONTROL 사용 가능한 채널]**, 선택 **+** (더하기 기호 아이콘).
1. In the YouTube Channel Settings dialog box, in the Title field, enter the name of the channel that you created in the task **[!UICONTROL Adding one or more channels to YouTube]** earlier.

   원하는 경우 설명을 선택적으로 추가할 수 있습니다.

1. 선택 **[!UICONTROL 확인]**.
1. YouTube/Google 확인이 표시됩니다. Google Cloud 계정에 아직 로그인하지 않은 경우 이 단계를 건너뜁니다.

   * Google 프로젝트 ID 및 위의 JSON 텍스트와 연결된 Google 사용자 이름 및 암호를 입력합니다.
   * 계정에 두 개 이상의 항목이 표시되는 채널 수에 따라 다릅니다. 채널을 선택합니다. 전자 메일 주소를 선택하지 마십시오; 채널이 아닙니다.
   * 다음 페이지에서 **[!UICONTROL 수락]** 이 채널에 대한 액세스를 허용합니다.

1. 선택 **[!UICONTROL 허용]**.

   이제 게시할 태그를 설정합니다.

1. **[!UICONTROL 게시할 태그 설정]** - Cloud Services > YouTube 페이지에서 연필 아이콘을 선택하여 사용할 태그 목록을 편집합니다.
1. Experience Manager에서 사용 가능한 태그 목록을 표시하려면 드롭다운 목록 아이콘(거꾸로 있는 삽입 기호)을 선택합니다.
1. 태그를 추가하려면 하나 이상의 태그를 선택합니다.

   추가한 태그를 삭제하려면 태그를 선택하고 을(를) 선택합니다 **X**.

1. 원하는 태그 추가를 마치면 를 선택합니다 **[!UICONTROL 확인]**.

   이제 비디오를 YouTube 채널에 게시합니다.

### (선택 사항) 업로드된 비디오에 대한 기본 YouTube 속성 설정을 자동화합니다 {#optional-automating-the-setting-of-default-youtube-properties-for-your-uploaded-videos}

선택적으로 비디오 업로드 시 YouTube 속성 설정을 자동화할 수 있습니다. Experience Manager에서 메타데이터 처리 프로필을 만듭니다.

To create the metadata processing profile, you are first going to copy values from the **[!UICONTROL Field Label]**, **[!UICONTROL Map to property]**, and **[!UICONTROL Choices]** fields, all found in Metadata Schemas for video. Then, you build your YouTube video metadata processing profile by adding those values to it.

**업로드한 비디오에 대한 기본 YouTube 속성 설정을 자동화하는 방법은 다음과 같습니다.**

1. Experience Manager의 왼쪽 위 모서리에서 Experience Manager 로고를 선택한 다음 왼쪽 레일에서 로 이동합니다. **[!UICONTROL 도구]** (망치 아이콘) > **[!UICONTROL 자산]** > **[!UICONTROL 메타데이터 스키마]**.
1. 선택 **[!UICONTROL 기본]**. (선택 상자에 &quot;기본값&quot; 왼쪽에 선택 표시를 추가하지 마십시오.)
1. 설정 **[!UICONTROL 기본]** 페이지의 왼쪽에 있는 상자를 선택합니다. **[!UICONTROL 비디오]**&#x200B;를 선택하고 을 선택합니다. **[!UICONTROL 편집]**.
1. 메타데이터 스키마 편집기 페이지에서 **[!UICONTROL 고급]** 탭.
1. YouTube 게시 제목 아래에서 을 선택합니다 **[!UICONTROL YouTube 카테고리]**.
1. 페이지 오른쪽의 아래에서 **[!UICONTROL 설정]** 탭에서 다음을 수행합니다.

   * 에서 **[!UICONTROL 속성에 매핑]** 텍스트 필드에서 값을 선택하고 복사합니다.
복사한 값을 열려 있는 텍스트 편집기에 붙여넣습니다. 메타데이터 처리 프로필을 만들 때 나중에 이 값이 필요합니다. 텍스트 편집기를 열어 둡니다.

   * 아래 **[!UICONTROL 선택 사항]**을(를) 선택하고 사용할 기본값(예: 사용자 및 블로그 또는 과학 및 기술)을 복사합니다.
복사한 값을 열려 있는 텍스트 편집기에 붙여넣습니다. 메타데이터 처리 프로필을 만들 때 나중에 이 값이 필요합니다. 텍스트 편집기를 열어 둡니다.

1. YouTube 게시 제목 아래에서 을 선택합니다 **[!UICONTROL YouTube 개인 정보]**.
1. 페이지 오른쪽의 아래에서 **[!UICONTROL 설정]** 탭에서 다음을 수행합니다.

   * 에서 **[!UICONTROL 속성에 매핑]** 텍스트 필드에서 값을 선택하고 복사합니다.
복사한 값을 열려 있는 텍스트 편집기에 붙여넣습니다. 메타데이터 처리 프로필을 만들 때 나중에 이 값이 필요합니다. 텍스트 편집기를 열어 둡니다.

   * 아래 **[!UICONTROL 선택 사항]**을(를) 선택하고 사용할 기본값을 복사합니다. 선택 사항은 두 쌍으로 그룹화됩니다. 쌍의 맨 아래 필드는 공용, 비상장 또는 개인 등의 복사할 기본값입니다.
복사한 값을 열려 있는 텍스트 편집기에 붙여넣습니다. 메타데이터 처리 프로필을 만들 때 나중에 이 값이 필요합니다. 텍스트 편집기를 열어 둡니다.

1. [메타데이터 스키마 편집기] 페이지의 오른쪽 위 모서리 근처에 있는 **[!UICONTROL 취소]**.
1. Experience Manager의 왼쪽 위 모서리에서 Experience Manager 로고를 선택한 다음 왼쪽 레일에서 를 선택합니다 **[!UICONTROL 도구]** (망치 아이콘) > **[!UICONTROL 자산]** > **[!UICONTROL 메타데이터 프로필]**.

1. 페이지의 오른쪽 위 모서리 근처에 있는 메타데이터 프로필 페이지에서 을 선택합니다 **[!UICONTROL 만들기]**.
1. 메타데이터 프로필 추가 대화 상자의 **[!UICONTROL 프로필 제목]** 텍스트 필드에 이름을 입력합니다 `YouTube Video` 을(를) 선택합니다. **[!UICONTROL 만들기]**.
1. 메타데이터 프로필 편집기 페이지에서 **[!UICONTROL 고급]** 탭.
1. 다음을 수행하여 복사된 YouTube 게시 값을 프로필에 추가합니다.

   * 페이지의 오른쪽에서 을(를) 선택합니다. **[!UICONTROL 양식 작성]** 탭.
   * (선택 사항) 레이블이 지정된 구성 요소를 드래그합니다. **[!UICONTROL 섹션 헤더]** 왼쪽에 놓고 양식 영역에 놓습니다.
   * (선택 사항) 선택 **[!UICONTROL 필드 레이블]** 를 클릭하여 구성 요소를 선택합니다.
   * (선택 사항) 페이지의 오른쪽의 설정 탭의 필드 레이블 텍스트 필드에 를 입력합니다 `YouTube Publishing`.
   * 을(를) 선택합니다 **[!UICONTROL 양식 작성]** 탭을 클릭한 다음 레이블이 지정된 구성 요소를 드래그합니다. **[!UICONTROL 다중 값 텍스트]** 아래에 놓고 **[!UICONTROL YouTube 게시]** 만든 제목.

   * 구성 요소를 선택하려면 **[!UICONTROL 필드 레이블]**.
   * 페이지 오른쪽의 설정 탭에서 이전에 복사한 YouTube 게시 값(필드 레이블 값 및 속성 값에 매핑)을 양식의 해당 필드에 붙여 넣습니다. 선택 사항 값을 기본값 필드에 붙여넣습니다.

1. 다음을 수행하여 복사된 YouTube 개인 정보 보호 값을 프로필에 추가합니다.

   * 페이지의 오른쪽에서 을(를) 선택합니다. **[!UICONTROL 양식 작성]** 탭.
   * (선택 사항) 레이블이 지정된 구성 요소를 드래그합니다. **[!UICONTROL 섹션 헤더]** 왼쪽에 놓고 양식 영역에 놓습니다.
   * (선택 사항) 선택 **[!UICONTROL 필드 레이블]** 를 클릭하여 구성 요소를 선택합니다.
   * (선택 사항) 페이지의 오른쪽의 설정 탭의 필드 레이블 텍스트 필드에 를 입력합니다 `YouTube Privacy`.
   * 을(를) 선택합니다 **[!UICONTROL 양식 작성]** 탭을 클릭한 다음 레이블이 지정된 구성 요소를 드래그합니다. **[!UICONTROL 다중 값 텍스트]** 아래에 놓고 **[!UICONTROL YouTube 개인 정보]** 만든 제목.

   * 구성 요소를 선택하려면 **[!UICONTROL 필드 레이블]**.
   * 페이지 오른쪽의 설정 탭에서 이전에 복사한 YouTube 게시 값(필드 레이블 값 및 속성 값에 매핑)을 양식의 해당 필드에 붙여 넣습니다. 선택 사항 값을 기본값 필드에 붙여넣습니다.

1. 페이지의 오른쪽 위 모서리 근처에 있는 를 선택합니다. **[!UICONTROL 저장]**.
1. 비디오를 업로드할 폴더에 YouTube 게시 메타데이터 프로필을 적용합니다. 메타데이터 프로필과 비디오 프로필 세트가 모두 있어야 합니다.

   See [Metadata Profiles](/help/assets/metadata-profiles.md) and [Video Profiles](/help/assets/dynamic-media/video-profiles.md).

### YouTube 채널에 비디오 게시 {#publishing-videos-to-your-youtube-channel}

이제 이전에 비디오 자산에 추가한 태그를 연결합니다. 이 프로세스를 통해 Experience Manager은 YouTube 채널에 게시할 자산을 알 수 있습니다.

>[!NOTE]
>
>즉시 게시해도 YouTube에 자동으로 게시되지 않습니다. When Dynamic Media is set up, there are two publish options to choose from: **[!UICONTROL Immediately]** or **[!UICONTROL Upon Activation]**.
>
>**[!UICONTROL 즉시 게시]** 은(는) 업로드된 자산이 IPS와 동기화된 후에 게재 시스템에 자동으로 게시됨을 의미합니다. Dynamic Media에게 이는 사실이지만 YouTube에게는 그렇지 않습니다. YouTube에 게시하려면 Experience Manager 작성자를 통해 게시해야 합니다.

>[!NOTE]
YouTube에서 컨텐츠를 게시하기 위해 Experience Manager은 **[!UICONTROL YouTube에 게시]** 작업 과정: 진행 상황을 모니터링하고 실패 정보를 볼 수 있습니다.
자세한 내용은 [비디오 인코딩 및 YouTube 게시 진행 모니터링](#monitoring-video-encoding-and-youtube-publishing-progress).
자세한 진행 정보를 보려면 복제 중인 YouTube 로그를 모니터링할 수 있습니다. 그러나 이러한 모니터링에는 관리자 액세스 권한이 필요합니다.

**비디오를 YouTube 채널에 게시하려면:**

1. Experience Manager에서 YouTube 채널에 게시할 비디오 자산으로 이동합니다.
1. 비디오 자산(응용 비디오 세트)을 선택합니다.
1. 도구 모음에서 를 선택합니다 **[!UICONTROL 속성]**.
1. 기본 탭의 메타데이터 제목 아래에서 을 선택합니다. **[!UICONTROL 선택 대화 상자 열기]** 태그 필드의 오른쪽에 있습니다.
1. 태그 선택 페이지에서 사용할 태그로 이동한 다음, 태그를 하나 이상 선택합니다.

   태그는 YouTube 채널과 연결되어 있어야 합니다.

1. 페이지의 오른쪽 위 모서리에서 을(를) 선택합니다 **[!UICONTROL 선택]**.
1. 비디오 속성 페이지의 오른쪽 위 모서리에서 을(를) 선택합니다 **[!UICONTROL 저장 후 닫기]**.
1. 도구 모음에서 를 선택합니다 **[!UICONTROL 빠른 게시]**.

   참조 - [Experience Manager Sites에서 게시 관리 사용](https://experienceleague.adobe.com/docs/experience-manager-learn/sites/page-authoring/publication-management-feature-video-use.html#page-authoring).

   YouTube 채널에서 게시된 비디오를 선택적으로 확인할 수 있습니다.

### (선택 사항) YouTube에서 게시된 비디오를 확인합니다 {#optional-verifying-the-published-video-on-youtube}

선택적으로 YouTube 게시(또는 게시 취소)의 진행 상황을 모니터링할 수 있습니다.

자세한 내용은 [비디오 인코딩 및 YouTube 게시 진행 모니터링](#monitoring-video-encoding-and-youtube-publishing-progress).

게시 시간은 기본 소스 비디오의 형식, 파일 크기 및 업로드 트래픽이 포함된 여러 요인에 따라 크게 달라질 수 있습니다. 게시 프로세스는 몇 분에서 몇 시간 정도 걸릴 수 있습니다. 또한 고해상도 포맷이 훨씬 느리게 렌더링됩니다. 예를 들어 720p와 1080p는 480p보다 오래 걸립니다.

8시간 후에도 여전히 **[!UICONTROL 업로드됨(처리 중입니다. 잠시 기다려 주십시오.)]**&#x200B;사이트에서 비디오를 제거하고 다시 업로드해 보십시오.

### 웹 애플리케이션에 YouTube URL 연결 {#linking-youtube-urls-to-your-web-application}

비디오를 게시한 후 Dynamic Media에서 생성한 YouTube URL 문자열을 가져올 수 있습니다. YouTube URL을 복사하면 클립보드에 로드되므로 웹 사이트 또는 애플리케이션의 페이지에 필요에 따라 붙여넣을 수 있습니다.

>[!NOTE]
YouTube URL은 비디오 자산을 YouTube에 게시하기 전까지 복사할 수 없습니다.

YouTube URL을 웹 애플리케이션에 연결하려면

1. 로 이동합니다 *YouTube 게시됨* 복사할 URL이 있는 비디오 자산을 선택한 다음 선택합니다.

   YouTube URL은 복사에만 사용할 수 있습니다 *after* 먼저 *게시됨* 비디오 자산을 YouTube에 추가합니다.

1. 도구 모음에서 를 선택합니다 **[!UICONTROL 속성]**.
1. 을(를) 선택합니다 **[!UICONTROL 고급]** 탭.
1. YouTube 게시 제목 아래의 YouTube URL 목록에서 URL 텍스트를 선택하고 웹 브라우저에 복사하여 자산을 미리 보거나 웹 컨텐츠 페이지에 추가합니다.

### YouTube에서 제거할 수 있도록 비디오 게시 취소 {#unpublishing-videos-to-remove-them-from-youtube}

Experience Manager에서 비디오 자산 게시를 취소하면 비디오가 YouTube에서 제거됩니다.

>[!CAUTION]
YouTube 내에서 직접 비디오를 제거하는 경우, Experience Manager은 이를 인식하지 못하고 비디오가 YouTube에 아직 게시되어 있는 것처럼 계속 동작합니다. 항상 Experience Manager 방식으로 YouTube에서 비디오 자산 게시를 취소합니다.

>[!NOTE]
YouTube에서 컨텐츠를 제거하려면 Experience Manager은 **[!UICONTROL YouTube에서 게시 취소]** 작업 과정: 진행 상황을 모니터링하고 실패 정보를 볼 수 있습니다.
자세한 내용은 [비디오 인코딩 및 YouTube 게시 진행 모니터링](#monitoring-video-encoding-and-youtube-publishing-progress).

**YouTube에서 제거할 비디오 게시를 취소하려면,**

1. YouTube 채널에서 게시를 취소하려는 비디오 자산으로 이동합니다.
1. 자산 선택 모드에서 하나 이상의 게시된 비디오 자산을 선택합니다.
1. 도구 모음에서 를 선택합니다 **[!UICONTROL 게시 관리]**. 필요한 경우 세 점 아이콘(`. . .`) 를 클릭하여 **[!UICONTROL 게시 관리]**.
1. 게시 관리 페이지에서 을 선택합니다 **[!UICONTROL 게시 취소]**.
1. 페이지의 오른쪽 위 모서리에서 을(를) 선택합니다 **[!UICONTROL 다음]**.
1. 페이지의 오른쪽 위 모서리에서 을(를) 선택합니다 **[!UICONTROL 게시 취소]**.

## 비디오 인코딩 및 YouTube 게시 진행 모니터링 {#monitoring-video-encoding-and-youtube-publishing-progress}

새 비디오를 비디오 인코딩이 적용된 폴더에 업로드하거나 YouTube에 비디오를 게시하면 비디오 인코딩/Youtube 게시가 진행 중(또는 실패)을 모니터링합니다. 실제 YouTube 게시 진행 상태는 로그 방식으로만 사용할 수 있습니다. 그러나 실패 또는 성공 여부는 다음 절차에 설명된 다른 방법으로 나열되어 있습니다. 또한 YouTube 게시 워크플로우 또는 비디오 인코딩이 완료되거나 중단되면 이메일 알림을 받게 됩니다.

### 진행 상태 모니터링 {#monitoring-progress}

실패한 인코딩/YouTube 게시를 포함하여 진행 상황을 모니터링할 수 있습니다.

1. 자산 폴더에서 비디오 인코딩 진행 상태 보기:

   * 카드 보기에서 자산에 비디오 인코딩 진행 상태가 백분율로 표시됩니다. 오류가 있으면 이 정보가 자산에도 표시됩니다.

   ![chlimage_1-429](assets/chlimage_1-429.png)

   * 목록 보기에서 비디오 인코딩 진행 상태는 **[!UICONTROL 처리 상태]** 열. If there is an error, this message displays in that same column.

   ![chlimage_1-430](assets/chlimage_1-430.png)

   This column does not display by default. 열을 활성화하려면 **[!UICONTROL 설정 보기]** 보기 드롭다운 메뉴에서 를 추가하고 **[!UICONTROL 처리 상태]** 열 및 선택 **[!UICONTROL 업데이트]**.

   ![chlimage_1-431](/help/assets/dynamic-media/assets/chlimage_1-431.png)

1. 자산 세부 정보에서 진행 상황을 봅니다. 자산을 선택하는 경우, 드롭다운 메뉴를 열고 을 선택합니다 **[!UICONTROL 타임라인]**. 인코딩 또는 YouTube 게시과 같은 워크플로우 활동으로 범위를 좁히려면 **[!UICONTROL 워크플로우]**.

   ![chlimage_1-432](assets/chlimage_1-432.png)

   인코딩과 같은 모든 워크플로우 정보가 타임라인에 표시됩니다. YouTube 게시의 경우 워크플로우 타임라인에는 YouTube 채널의 이름과 YouTube 비디오 URL도 포함되어 있습니다. 또한 게시가 완료된 후 워크플로우 타임라인에 오류 알림이 표시됩니다.

   >[!NOTE]
   의 여러 워크플로우 구성으로 인해 실패/오류 메시지를 최종적으로 기록하는 데 시간이 오래 걸릴 수 있습니다 **[!UICONTROL 다시 시도]**, **[!UICONTROL 다시 시도 지연]**, 및 **[!UICONTROL timeout]** 변환 전: [https://localhost:4502/system/console/configMgr](https://localhost:4502/system/console/configMgr), 예:
   * Apache Sling 작업 큐 구성
   * Adobe Granite Workflow 외부 프로세스 작업 처리기
   * Granite 워크플로우 시간 초과 큐

   을 조정할 수 있습니다 **[!UICONTROL 다시 시도]**, **[!UICONTROL 다시 시도 지연]**, 및 **[!UICONTROL timeout]** 이러한 구성의 속성.

1. For workflows in progress, see Workflow Instances available from **[!UICONTROL Tools]** > **[!UICONTROL Workflow]** > **[!UICONTROL Instances]**.

   >[!NOTE]
   에 액세스하려면 관리 권한이 필요합니다 **[!UICONTROL 도구]** 메뉴 아래의 제품에서 사용할 수 있습니다.

   ![chlimage_1-433](assets/chlimage_1-433.png)

   인스턴스를 선택하고 을(를) 선택합니다 **[!UICONTROL 기록 열기]**.

   ![chlimage_1-434](/help/assets/dynamic-media/assets/chlimage_1-434.png)

   워크플로우 인스턴스 영역에서 워크플로우를 일시 중단, 종료 또는 변경할 수도 있습니다. 자세한 내용은 [워크플로우 관리](/help/sites-cloud/authoring/workflows/overview.md) 추가 정보.

1. For failed jobs, see Workflow Failures available from **[!UICONTROL Tools]** > **[!UICONTROL Workflow]** > **[!UICONTROL Failures]**. The **[!UICONTROL Workflow Failure]** lists all failed workflow activities.

   >[!NOTE]
   에 액세스하려면 관리 권한이 필요합니다 **[!UICONTROL 도구]** 메뉴 아래의 제품에서 사용할 수 있습니다.

   ![chlimage_1-435](assets/chlimage_1-435.png)

   >[!NOTE]
   의 여러 워크플로우 구성으로 인해 오류 메시지가 최종적으로 기록되는 데 시간이 오래 걸릴 수 있습니다 **[!UICONTROL 다시 시도]**, **[!UICONTROL 다시 시도 지연]**, 및 **[!UICONTROL timeout]** 변환 전: [https://localhost:4502/system/console/configMgr](https://localhost:4502/system/console/configMgr), 예:
   * Apache Sling 작업 큐 구성
   * Adobe Granite Workflow 외부 프로세스 작업 처리기
   * Granite 워크플로우 시간 초과 큐

   을 조정할 수 있습니다 **[!UICONTROL 다시 시도]**, **[!UICONTROL 다시 시도 지연]**, 및 **[!UICONTROL timeout]** 이러한 구성의 속성.

1. For completed workflows, see Workflow Archive available from **[!UICONTROL Tools]** > **[!UICONTROL Workflow]** > **[!UICONTROL Archive]**. The **[!UICONTROL Workflow Archive]** lists all completed workflow activities.

   >[!NOTE]
   에 액세스하려면 관리 권한이 필요합니다 **[!UICONTROL 도구]** 메뉴 아래의 제품에서 사용할 수 있습니다.

   ![chlimage_1-436](assets/chlimage_1-436.png)

1. 중단되거나 실패한 워크플로우 작업에 대한 이메일 알림을 받게 됩니다. 관리자가 이러한 이메일 알림을 구성할 수 있습니다. 자세한 내용은 [이메일 알림 구성](#configuring-e-mail-notifications).

<!-- EMAIL NOT AVAILABLE IN SKYLINE

#### Configuring e-mail notifications {#configuring-e-mail-notifications}

>[!NOTE]
>
>You may need administrative rights to access the **[!UICONTROL Tools]** menu.

How you configure notification depends on whether you want notifications for YouTube publishing jobs.

* For encoding jobs, you can access the configuration page for all Experience Manager workflow email notifications at **[!UICONTROL Tools]** > **[!UICONTROL Operations]** > **[!UICONTROL Web Console]** and by searching for **[!UICONTROL Day CQ Workflow Email Notification Service]**. You can select or clear the check boxes for **[!UICONTROL Notify on Abort]** or **[!UICONTROL Notify on Complete]** accordingly.

For YouTube publishing jobs, do the following:

1. In Experience Manager, navigate to **[!UICONTROL Tools]** > **[!UICONTROL Workflow]** > **[!UICONTROL Models]**.
1. On the Workflow Models page, select **[!UICONTROL Publish to YouTube]**, then select **[!UICONTROL Edit]** on the toolbar.
1. Near the upper-right corner of the Publish to YouTube workflow page, select **[!UICONTROL Edit]**.
1. Hover the mouse pointer on the YouTube Upload component, then select once to display the inline toolbar.

   ![6_5_publishtoyoutubeworkflow](assets/6_5_publishtoyoutubeworkflow.png)

1. On the inline toolbar, select the Configuration icon (wrench). Select the **[!UICONTROL Arguments]** tab.

   ![6_5_publishtoyoutubeworkflow-configurationicon](assets/6_5_publishtoyoutubeworkflow-configurationicon.png)

1. In the YouTube Upload Process - Step Properties dialog box, select the **[!UICONTROL Arguments]** tab.

   ![6_5_publishtoyoutubeworkflow-arguments-tab](assets/6_5_publishtoyoutubeworkflow-arguments-tab.png)

1. You can select or clear the following check boxes:

    * Publish Start
    * Publish Failure
    * Publish Completion - includes information on channels and URLs

   Clearing a check box means that you will not receive the specified email notification from the YouTube Publish workflow.

   >[!NOTE]
   >
   >These emails are specific to YouTube and are in addition to the generic workflow email notifications. As a result, you may receive two sets of email notification - the generic notification available in the **[!UICONTROL Day CQ Workflow Email Notification Service]** and one specific to YouTube depending on your configuration settings.

1. When you are finished, near the upper-right corner of the dialog box, select the **[!UICONTROL Done]** icon (check mark).
1. On the Publish to YouTube workflow page, near the upper-right corner, select **[!UICONTROL Sync]**.

-->

## 비디오 보고서 보기 {#viewing-video-reports}

>[!NOTE]
비디오 보고서는 Dynamic Media - 하이브리드 모드를 실행하는 경우에만 사용할 수 있습니다.

비디오 보고서에는 해당 지표를 모니터링하는 데 도움이 되도록 지정된 기간 동안의 몇 가지 집계 지표가 표시됩니다 *게시됨* 개별 및 집계 비디오가 예상대로 작동하는지 확인합니다. 다음 상위 지표 데이터는 전체 웹 사이트에서 게시된 모든 비디오에 대해 집계됩니다.

* 비디오 시작
* 완료율
* 비디오의 평균 시간
* 비디오의 총 시간
* 방문당 비디오 수

테이블 *게시됨* 비디오도 나열되므로 총 비디오 시작을 기반으로 웹 사이트에서 가장 많이 본 비디오를 추적할 수 있습니다.

목록에서 비디오 이름을 선택하면 비디오의 대상 유지(드롭다운) 보고서가 라인 차트 형태로 표시됩니다. 차트는 비디오 재생 중 지정된 시간 동안의 보기 수를 표시합니다. 비디오를 재생하면 세로 막대가 플레이어의 시간 표시기와 동기식으로 추적합니다. 라인 차트 데이터의 드롭은 대상이 관심 영역에서 이탈하는 위치를 나타냅니다.

비디오가 Adobe Experience Manager Dynamic Media 외부에 인코딩된 경우 대상 유지(드롭다운) 차트와 테이블의 재생 비율 데이터를 사용할 수 없습니다.

>[!NOTE]
추적 및 보고 데이터는 Dynamic Media의 자체 비디오 플레이어 및 관련 비디오 플레이어 사전 설정의 사용만을 기반으로 합니다. 따라서 다른 비디오 플레이어로 재생되는 비디오를 추적하고 보고할 수 없습니다.

기본적으로 비디오 보고서를 처음 입력할 때 이 보고서는 현재 달 1일에 시작하여 현재 월의 날짜로 끝나는 비디오 데이터를 표시합니다. 그러나 고유한 날짜 범위를 지정하여 기본 날짜 범위를 무시할 수 있습니다. 다음에 비디오 보고서를 입력할 때 지정한 날짜 범위가 사용됩니다.

비디오 보고서가 올바르게 작동하려면 Dynamic Media Cloud Services이 구성되면 보고서 세트 ID가 자동으로 생성됩니다. 동시에 보고서 세트 ID가 게시 서버로 푸시되어 자산을 미리 볼 때 URL 복사 기능에 사용할 수 있습니다. 그러나 이 기능을 사용하려면 게시 서버를 이미 설정해야 합니다. 게시 서버가 설정되지 않은 경우에는 여전히 게시하여 비디오 보고서를 볼 수 있습니다. 그러나 Dynamic Media 클라우드 구성으로 돌아가 다음을 선택해야 합니다 **[!UICONTROL 확인]**.

**비디오 보고서를 보려면 다음을 수행하십시오.**

1. Experience Manager의 왼쪽 위 모서리에서 Experience Manager 로고를 선택한 다음 왼쪽 레일에서 로 이동합니다. **[!UICONTROL 도구]** (망치 아이콘) > **[!UICONTROL 자산]** > **[!UICONTROL 비디오 보고서]**.
1. 비디오 보고서 페이지에서 다음 중 하나를 수행합니다.

   * 오른쪽 상단 모서리에서 을(를) 선택합니다. **[!UICONTROL 비디오 보고서 새로 고침]** 아이콘.
보고서의 종료 날짜가 현재 날짜인 경우에만 새로 고침을 사용합니다. 이 기능을 사용하면 보고서를 마지막으로 실행한 이후 발생한 비디오 추적을 볼 수 있습니다.

   * 오른쪽 상단 모서리에서 을(를) 선택합니다. **[!UICONTROL 날짜 선택기]** 아이콘.
비디오 데이터를 저장할 시작 날짜 범위와 종료 날짜 범위를 지정한 다음 을 선택합니다 **[!UICONTROL 보고서 실행]**.

   상위 지표 그룹 상자는 모든 지표에 대한 다양한 집계 측정을 식별합니다 *게시됨* 사이트 전체에서 비디오를 업로드합니다.

1. 게시된 상위 비디오를 나열하는 테이블에서 비디오를 재생할 비디오 이름을 선택하고 비디오의 대상 유지(드롭다운) 보고서를 볼 수도 있습니다.

<!-- OBSOLETE CONTENT OBSOLETE CONTENT - SDK ONLY AVAILABLE INTERNALLY NOW 
### Viewing video reports based on a video viewer that you created using the Dynamic Media HTML5 Viewer SDK {#viewing-video-reports-based-on-a-video-viewer-that-you-created-using-the-scene-hmtl-viewer-sdk}

If you are using an out-of-box video viewer provided by Dynamic Media, or if you created a custom viewer preset based off of an out-of-box video viewer, then no additional steps are required to view video reports. However, if you have created your own video viewer based off the Dynamic Media HTML5 Viewer SDK, then use the following steps to ensure the your video viewer is sending tracking events to Dynamic Media Video Reports.

Use the Dynamic Media Viewers Reference and the Dynamic Media HTML5 Viewers SDK to create your own video viewers.

See [Dynamic Media Viewers Reference Guide](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/home.html).

Download the Scene7 HTML Viewer SDK from Adobe Developer Connection.

See [Adobe Developer Connection](https://help.adobe.com/en_US/scene7/using/WSef8d5860223939e2-43dedf7012b792fc1d5-8000.html).

**To view Video Reports based on a video viewer that you created using the Dynamic Media HTML5 Viewer SDK:**

1. Navigate to any published video asset.
1. Near the upper-left corner of the asset's page, from the drop-down list, select **[!UICONTROL Viewers]**.
1. Select any video viewer preset and copy the embed code.
1. In the embed code, find the line with the following:

   `videoViewer.setParam("config2", "<value>");`

   The `config2` parameter enables tracking in HTML5 Viewers. It is also a company-specific preset that contains the configuration information for Video Reporting, and for customer-specific Adobe Analytics configurations.

   The correct value for the config2 parameter is found in both the **[!UICONTROL Embed Code]** and in the copy **[!UICONTROL URL]** function. In the URL from the copy **[!UICONTROL URL]** command, the parameter to look for is `&config2=<value>` . The value is almost always `companypreset`, but in some instances it can also be `companypreset-1`, `companypreset-2`, and so forth.

1. In your custom video viewer code, add AppMeasurementBridge .jsp to the viewer page by doing the following:

    * First, determine if you need the `&preset` parameter.
      If the `config2` parameter is `companypreset`, you do *not *need `&preset=parameter`.
      If `config2` is anything else, set the preset parameter the same as the `config2` parameter. For example, if `config2=companypreset-2`, add `&param2=companypreset-2` to the AppMeasurmentBridge.jsp URL.

    * Then, add the AppMeasurementBridge.jsp script:
      `<script language="javascript" type="text/javascript" src="https://s7d1.scene7.com/s7viewers/AppMeasurementBridge.jsp?company=robindallas&preset=companypreset-2"></script>`

1. Create the TrackingManager component by doing the following:

    * After calling `s7sdk.Utils.init();` create a TrackingManager instance to track events by adding the following:
      `var trackingManager = new s7sdk.TrackingManager();`

    * Connect components to TrackingManager by doing the following:
      In the `s7sdk.Event.SDK_READY` event handler, attach the component you want to track to the TrackingManager.
      For example, if the component is `videoPlayer`, add
      `trackingManager.attach(videoPlayer);`
      to attach the component to the trackingManager. To track multiple viewers on a page, use multiple tracking mangaer components.

    * Create the AppMeasurementBridge object by adding the following:

      ```
      var appMeasurementBridge = new AppMeasurementBridge(); appMeasurementBridge.setVideoPlayer(videoPlayer);
      ```

    * Add the tracking function by adding the following:

      ```
      trackingManager.setCallback(appMeasurementBridge.track,
       appMeasurementBridge);
      ```

   The appMeasurementBridge object has a built-in track function. OBSOLETE However, you can provide your own to support multiple tracking systems or other functionality.

   For more information, see *Using the TrackingManager Component* in the *Scene7 HTML5 Viewer SDK User Guide* available for download from [Adobe Developer Connection](https://help.adobe.com/en_US/scene7/using/WSef8d5860223939e2-43dedf7012b792fc1d5-8000.html).
 -->

## 비디오에 자막 또는 자막 추가 {#adding-captions-to-video}

단일 비디오나 응용 비디오 세트에 자막을 추가하여 비디오의 범위를 글로벌 마켓플레이스로 확장할 수 있습니다. 자막을 추가하면 오디오를 다시 녹음할 필요가 없거나, 각 다른 언어의 오디오를 다시 녹음하기 위해 기본 스피커를 사용할 필요가 없습니다. 비디오는 녹음된 언어로 재생됩니다. 외국어 자막이 나타나므로 다른 언어를 사용하는 사람들이 오디오 부분을 계속 이해할 수 있습니다.

또한 자막은 청각 장애나 난청인 사람들에게 더 많은 접근성을 가능하게 해줍니다.

>[!NOTE]
사용하는 비디오 플레이어는 닫힌 캡션 표시를 지원해야 합니다.

참조 - [Dynamic Media의 접근성](/help/assets/dynamic-media/accessibility-dm.md).

Dynamic Media은 캡션 파일을 JSON(JavaScript 개체 표기법) 형식으로 변환할 수 있습니다. 이 전환은 JSON 텍스트를 비디오의 숨겨진 완전한 텍스트 로 웹 페이지에 포함할 수 있음을 의미합니다. 그런 다음 검색 엔진은 컨텐츠를 크롤링하거나 색인화하여 비디오를 보다 손쉽게 검색할 수 있게 만들고 고객에게 비디오 컨텐츠에 대한 자세한 정보를 제공할 수 있습니다.

자세한 내용은 [정적(비이미지) 콘텐츠 제공](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/c-serving-static-nonimage-contents.html#image-serving-api) 를 참조하십시오.

**비디오에 캡션 또는 자막을 추가하려면**

1. 타사 응용 프로그램 또는 서비스를 사용하여 비디오 캡션/자막 파일을 만듭니다.

   만드는 파일이 WebVTT(Web Video Text Tracks) 표준을 따르는지 확인합니다. 캡션 파일 이름 확장명은 .VTT입니다. WebVTT 캡션 표준에 대한 자세한 정보를 확인할 수 있습니다.

   자세한 내용은 [WebVTT: 웹 비디오 텍스트 트랙 형식](https://w3c.github.io/webvtt/).

   Dynamic Media 외부에서 캡션/자막 파일을 작성하는 데 사용할 수 있는 무료 및 프리미엄 도구와 서비스가 모두 있습니다. 예를 들어 스타일이 없는 간단한 비디오 캡션 파일을 만들려면 다음과 같은 무료 온라인 캡션 작성 및 편집 도구를 사용할 수 있습니다.

   [WebVTT 캡션 작성기](https://testdrive-archive.azurewebsites.net/Graphics/CaptionMaker/Default.html)

   최상의 결과를 얻으려면 Internet Explorer 9 이상, Google Chrome 또는 Safari에서 도구를 사용하십시오.

   도구에서 **[!UICONTROL 비디오 파일의 URL 입력]** 필드에서 복사한 비디오 파일의 URL을 붙여넣은 다음 를 선택합니다 **[!UICONTROL 로드]**. 자세한 내용은 [자산의 URL 가져오기](/help/assets/dynamic-media/linking-urls-to-yourwebapplication.md#obtaining-a-url-for-an-asset) 비디오 파일 자체에 URL을 붙여 넣을 수 있습니다. **[!UICONTROL 비디오 파일 필드의 URL 입력]**. Internet Explorer, Chrome, or Safari can then natively play back the video.

   이제 사이트에서 화면의 지침에 따라 WebVTT 파일을 작성하고 저장합니다. 완료되면 캡션 파일 내용을 복사하여 일반 텍스트 편집기에 붙여넣은 다음 VTT 파일 확장자로 저장합니다.

   >[!NOTE]
   여러 언어로 비디오 자막을 글로벌 지원하려면 WebVTT 표준을 사용하려면 지원할 각 언어에 대해 별도의 .vtt 파일과 호출을 만들어야 합니다.

   일반적으로 캡션 VTT 파일의 이름을 비디오 파일과 같은 이름으로 지정하고 -EN 또는 -FR 또는 -DE와 같은 언어 로케일에 추가하려고 합니다. 이렇게 하면 기존 웹 컨텐츠 관리 시스템을 사용하여 비디오 URL의 생성을 자동화하는 데 도움이 됩니다.

1. Experience Manager에서 WebVTT 캡션 파일을 DAM에 업로드합니다.
1. 로 이동합니다 *게시됨* 업로드한 캡션 파일과 연결할 비디오 자산입니다.

   URL은 복사에만 사용할 수 있습니다 *after* 먼저 *게시됨* 자산.

   자세한 내용은 [자산 게시](/help/assets/dynamic-media/publishing-dynamicmedia-assets.md).

1. 다음 중 하나를 수행하십시오.

   * 팝업 비디오 뷰어 환경의 경우 **[!UICONTROL URL]**. URL 대화 상자에서 URL을 선택하여 클립보드에 복사한 다음 URL을 단순 텍스트 편집기에 복사합니다. 비디오의 복사된 URL을 다음 구문과 함께 추가합니다.

      `&caption=<server_path>/is/content/<path_to_caption.vtt_file,1>`

      참고 사항 `,1` 캡션 경로의 끝입니다. 경로에서 VTT 파일 이름 확장자 바로 다음에 를 설정하여 비디오 플레이어 모음에서 닫힌 캡션 단추를 활성화(켜기) 또는 비활성화(끄기)할 수도 있습니다 `,1` 또는 `,0`각각 입니다.

   * 포함된 비디오 뷰어 환경의 경우 를 선택합니다. **[!UICONTROL 포함 코드]**. 포함 코드 대화 상자에서 를 선택하고 포함 코드를 클립보드에 복사한 다음 단순 텍스트 편집기에 붙여넣습니다. 복사된 포함 코드를 다음 구문과 함께 추가합니다.

      `videoViewer.setParam("caption","<path_to_caption.vtt_file,1>");`

      참고 사항 `,1` 캡션 경로의 끝입니다. 경로에서 VTT 파일 이름 확장자 바로 다음에 를 설정하여 비디오 플레이어 모음에서 닫힌 캡션 단추를 활성화(켜기) 또는 비활성화(끄기)할 수도 있습니다 `,1` 또는 `,0`각각 입니다.

## 비디오에 장 마커 추가 {#adding-chapter-markers-to-video}

장 마커를 단일 비디오나 응용 비디오 세트에 추가하여 긴 양식 비디오를 더 쉽게 보고 탐색할 수 있습니다. 사용자가 비디오를 재생하면 비디오 타임라인에서 장 마커(비디오 스크러버라고도 함)를 선택할 수 있습니다. 관심 영역으로 쉽게 이동하거나 새로운 컨텐츠, 교육 및 데모로 바로 이동할 수 있습니다.

>[!NOTE]
사용되는 비디오 플레이어는 장 마커 사용을 지원해야 합니다. Dynamic Media 비디오 플레이어는 장 마커를 지원하지만 타사 비디오 플레이어를 사용하지 않을 수 있습니다.

<!-- OBSOLETE CONTENT OBSOLETE CONTENT If desired, you can create and brand your own custom video viewer with chapters instead of using a video viewer preset. For instructions on creating your own HTML5 viewer with chapter navigation, in the Adobe Scene7 Viewer SDK for HTML5 guide, reference the heading “Customizing Behavior Using Modifiers” under the classes `s7sdk.video.VideoPlayer` and `s7sdk.video.VideoScrubber`. The Adobe Scene7 Viewer SDK is available as a download from [Adobe Developer Connection](https://help.adobe.com/en_US/scene7/using/WSef8d5860223939e2-43dedf7012b792fc1d5-8000.html). -->

캡션을 만드는 것과 거의 동일한 방식으로 비디오에 대한 장 목록을 만듭니다. 즉, WebVTT 파일을 만듭니다. 그러나 이 파일은 WebVTT 캡션 파일과 분리되어야 합니다. 캡션과 장을 하나의 WebVTT 파일에 결합할 수 없습니다.

다음 샘플을 사용하여 장 탐색 기능을 사용하여 WebVTT 파일을 만들 수 있습니다.

### 비디오 장 탐색 기능이 있는 WebVTT 파일 {#webvtt-file-with-video-chapter-navigation}

```xml {.line-numbers}
WEBVTT
Chapter 1
00:00.000 --> 01:04.364
The bicycle store behind it all.
Chapter 2
01:04.364 --> 02:00.944
Creative Cloud.
Chapter 3
02:00.944 --> 03:02.937
Ease of management for a working solution.
Chapter 4
03:02.937 --> 03:35.000
Cost-efficient access to rapidly evolving technology.
```

위의 예에서 `Chapter 1` 는 큐 식별자이며, 선택 사항입니다. 의 큐 시간 `00:00:000 --> 01:04:364` 장의 시작 시간과 종료 시간을 지정합니다. `00:00:000` 형식 지정 마지막 세 자리는 밀리초이며 그대로 둘 수 있습니다 `000`를 설정하는 것이 좋습니다. 의 장 제목 `The bicycle store behind it all` 는 장의 내용에 대한 실제 설명입니다. 사용자가 타임라인의 시각적 큐 포인트 위로 마우스 포인터를 가져가면 큐 식별자, 시작 큐 시간 및 장 제목이 모두 비디오 플레이어의 팝업에 나타납니다.

HTML5 비디오 뷰어를 사용하고 있으므로 만드는 장 파일이 WebVTT(Web Video Text Tracks) 표준을 따르는지 확인합니다. 장 파일 이름 확장명은 .VTT입니다. WebVTT 캡션 표준에 대한 자세한 정보를 확인할 수 있습니다.

자세한 내용은 [WebVTT: 웹 비디오 텍스트 트랙 형식](https://w3c.github.io/webvtt/).

**비디오에 장 마커를 추가하려면**

1. 장 제목 텍스트에서 문자 변환과 관련된 문제를 방지하려면 VTT 파일을 UTF8 인코딩으로 저장합니다.

   일반적으로 VTT 장의 이름을 비디오 파일과 같은 이름으로 지정하고 장에 추가하려고 합니다. 이렇게 하면 기존 웹 컨텐츠 관리 시스템을 사용하여 비디오 URL의 생성을 자동화하는 데 도움이 됩니다.
1. Experience Manager에서 WebVTT 장 파일을 업로드합니다.

   자세한 내용은 [자산 업로드](/help/assets/manage-digital-assets.md#uploading-assets).

1. 다음 중 하나를 수행하십시오.

   <table>
     <tbody>
      <tr>
       <td>팝업 비디오 뷰어 경험의 경우</td>
       <td>
       <ol>
       <li>로 이동합니다 <i>게시됨 </i>업로드한 장 파일과 연결할 비디오 자산입니다. Remember that URLs are only available to copy <i>after</i> you have first <i>published</i> the assets. 자세한 내용은 <a href="/help/assets/dynamic-media/publishing-dynamicmedia-assets.md">자산 게시.</a></li>
       <li>드롭다운 메뉴에서 을(를) 선택한 다음 <strong>뷰어</strong>.</li>
       <li>왼쪽 레일에서 비디오 뷰어 사전 설정 이름을 선택합니다. 비디오 미리 보기가 별도의 페이지에 열립니다.</li>
       <li>왼쪽 레일의 하단에서 을 선택합니다 <strong>URL</strong>.</li>
       <li>URL 대화 상자에서 URL을 선택하여 클립보드에 복사한 다음 URL을 단순 텍스트 편집기에 복사합니다.</li>
       <li>복사한 비디오의 URL을 다음 구문과 함께 추가하면 복사한 URL과 장 파일에 연결할 수 있습니다.<br /> <br /> <code>&navigation=<<i>full_copied_URL_path_to_chapter_file</i>.vtt></code><br /> </li>
       </ol> </td>
      </tr>
      <tr>
       <td>포함된 비디오 뷰어 경험의 경우<br /> </td>
       <td>
       <ol>
       <li>로 이동합니다 <i>게시됨 </i>업로드한 장 파일과 연결할 비디오 자산입니다. URL은 복사에만 사용할 수 있습니다 <i>after</i> 먼저 <i>게시됨</i> 자산. 자세한 내용은 <a href="/help/assets/dynamic-media/publishing-dynamicmedia-assets.md">자산 게시.</a></li>
       <li>드롭다운 메뉴에서 을(를) 선택한 다음 <strong>뷰어</strong>.</li>
       <li>왼쪽 레일에서 비디오 뷰어 사전 설정 이름을 선택합니다. 비디오 미리 보기가 별도의 페이지에 열립니다.</li>
       <li>왼쪽 레일의 하단에서 을 선택합니다 <strong>포함</strong>.</li>
       <li>포함 코드 대화 상자에서 를 선택하고 전체 코드를 클립보드에 복사한 다음 단순 텍스트 편집기에 붙여넣습니다.</li>
       <li>비디오의 포함 코드를 다음 구문과 추가하므로 복사한 URL과 장 파일에 연결할 수 있습니다.<br /> <br /> <code>videoViewer.setParam("navigation","&lt;<i>full_copied_URL_path_to_chapter_file</i>.vtt>"</code></li>
       </ol> </td>
      </tr>
     </tbody>
   </table>

<!--

## About video thumbnails {#about-video-thumbnails}

A video thumbnail is a reduced-size version of a video frame or an image asset representing the video to the customer. The thumbnail should serve to encourage a customer to select the video.

All videos in Experience Manager must have an associated thumbnail; you cannot delete a thumbnail without replacing it. By default, when you upload a video to Experience Manager, the first frame is used as the thumbnail. However, you can customize the thumbnail for branding purposes or visual search, for example. When you customize a video thumbnail, you can either play the video and pause on the frame you want to use, or you can select an image asset that you have already uploaded and *published* in your digital asset manager.

Note that a custom video thumbnail image that you select from a video is not extracted and saved in the DAM as a separate and distinct asset. However, a custom video thumbnail that you select from an existing image asset is saved to the JCR. The path of the selected asset gets stored under the video asset's node as in the following example path:

`/content/dam/*<folder_name*>/<*video_name*>/jcr:content/manualThumbnail`

The ability to customize a video thumbnail is only available after you have applied a video profile to the folder where the video is located.

### Adding a custom video thumbnail {#adding-a-custom-video-thumbnail}

1. Be sure you have already done the following:

    * Created a folder for your video assets.
    * [Applied a video profile to the folder](/help/assets/dynamic-media/video-profiles.md#applying-a-video-profile-to-folders).

    * [Uploaded your videos to the folder](/help/assets/manage-video-assets.md#upload-and-preview-video-assets).

1. Navigate to an uploaded video asset whose thumbnail image you want to change.
1. In asset selection mode either from **[!UICONTROL List View]** or **[!UICONTROL Card View]**, select the video asset.
1. On the toolbar, select the **[!UICONTROL Properties** icon (a circle with an "i" in it).
1. On the video's Properties page, select **[!UICONTROL Change Thumbnail]**.
1. On the Change Thumbnail page, do one of the following:

    * To use a frame from the video as the new thumbnail:

        * On the toolbar, select **[!UICONTROL Select Frame from video]**.
        * Select the Play button, then select the Pause button on the frame you want to capture as the video's new thumbnail.

    * To use an image asset as the new thumbnail:

        * On the toolbar, select **[!UICONTROL Select Thumbnail from Assets]**.
        * Select **[!UICONTROL Select Thumbnail]**.
        * Navigate to a previously uploaded and published image asset you want to use. Note that the asset will automatically be resized to serve as a thumbnail image for the video.
        * Select the image asset, then select **[!UICONTROL Select]**.

1. On the Change Thumbnail page, select **[!UICONTROL Save Change]**.
1. On the video's Properties page, in the upper-right corner, select **[!UICONTROL Save & Close]**.

-->

<!--

## About video thumbnails in Dynamic Media Hybrid mode{#about-video-thumbnails-in-dynamic-media-hybrid-mode}

You can choose from one of ten thumbnail images automatically generated by Dynamic Media to add to your video. The video player displays your selected thumbnail when a video asset is used with the Dynamic Media component in the authoring environment of Experience Manager Sites, Experience Manager Mobile, or Experience Manager Screens. The thumbnail serves as a static picture that best represents the contents of your entire video and further encourages users to select the Play button.

Based on the total time of the video, Dynamic Media captures ten (default) thumbnail images at 1%, 11%, 21%, 31%, 41%, 51%, 61%, 71%, 81%, and 91% into the video. The ten thumbnails persist meaning that if you decide to choose a different thumbnail later on, you do not need to regenerate the series. You preview the ten thumbnail images and then select the one you want to use with your video. If you want to change to default you can use CRXDE Lite to configure the time interval that thumbnail images are generated. For example, if you only wanted to generate a series of four evenly spaced thumbnail images from your video, you can configure the interval time at 24%, 49%, 74%, and 99%.

Ideally, you can add a video thumbnail anytime after you upload your video but before you publish the video on your website.

If you prefer, you can choose to upload a custom thumbnail to represent your video instead of using a thumbnail generated by Dynamic Media. For example, you could create a custom thumbnail image that has the title of your video, an eye-catching opening image, or a very specific image captured from your video. The custom video thumbnail image that you upload should have a maximum resolution of 1280 x 720 pixels (minimum width of 640 pixels) and be no larger than 2MB.

See also [About video thumbnails](/help/assets/dynamic-media/video.md#about-video-thumbnails-in-dynamic-media-scene-mode).

-->

<!--

### Adding a video thumbnail {#adding-a-video-thumbnail}

1. Navigate to an uploaded video asset that you want to add a video thumbnail.
1. In asset selection mode either from the List View or the Card View, select the video asset.
1. On the toolbar, select the **[!UICONTROL View Properties]** icon (a circle with an "i" in it).
1. On the video's Properties page, select **[!UICONTROL Change Thumbnail]**.
1. On the Change Thumbnail page, on the toolbar, select **[!UICONTROL Select Frame]**.

   Dynamic Media generates a series thumbnail images from your video, based on the default time interval or time interval you customized.

1. Preview the generated thumbnail images, then select the one you want to add to your video.
1. Select **[!UICONTROL Save Change]**.

   The video's thumbnail image is updated to use the thumbnail you selected. If you later decide to change the thumbnail image, you can return to the **[!UICONTROL Change Thumbnail]** page and select a new one.

   If you configured new default time intervals, or you uploaded a new video to replace the existing video, you will need to have Dynamic Media regenerate the thumbnails.

   See [Configuring the default time interval that video thumbnails are generated](#configuring-the-default-time-interval-that-video-thumbnails-are-generated).

-->

<!--

#### Configuring the default time interval that video thumbnails are generated {#configuring-the-default-time-interval-that-video-thumbnails-are-generated}

When you configure and save the new default time interval, your change automatically applies only to videos that you upload in the future. It does not automatically apply the new default to videos that you previously uploaded. For existing videos, you must regenerate the thumbnails.

See [Adding a video thumbnail](#adding-a-video-thumbnail).

**To configure the default time interval that video thumbnails are generated,**

1. In Experience Manager, navigate to **[!UICONTROL Tools]** > **[!UICONTROL General]** > **[!UICONTROL CRXDE Lite]**.

1. In the CRXDE Lite page, in the directory panel on the left, navigate t `o etc/dam/imageserver/configuration/jcr:content/settings.`

   if the directory panel is not visible, you may need to select the >> icon to the left of the Home tab.

1. On the lower-right panel, in the Properties tab, double-tap `thumbnailtime`.
1. In the Edit thumbnailtime dialog box, use the text fields to enter interval values as percentages.

    * Select the plus sign (+) icon to add one or more interval value fields. You may need to scroll to the bottom of the dialog box to see the icon.
    * Select the minus sign (-) icon to the right of an interval value field to delete it from the list.
    * Select the up arrow icon and the down arrow icon to reorder the interval values.

1. Select **[!UICONTROL OK]** to return to the Properties tab.
1. Near the upper-left corner of the CRXDE Lite page, select **[!UICONTROL Save All]**, then select the Back Home icon in the upper-left corner to return to Experience Manager.

   See [Adding a video thumbnail](#adding-a-video-thumbnail).

-->

<!--

### Adding a custom video thumbnail {#adding-a-custom-video-thumbnail-1}

These steps apply only to Dynamic Media running in Hybrid mode.

T**o add a custom video thumbnail**,

1. Navigate to an uploaded video asset that you want to add a custom video thumbnail.
1. In asset selection mode either from the List View or the Card View, select the video asset.
1. On the toolbar, select the **[!UICONTROL View Properties]** icon (a circle with an "i" in it).
1. On the video's Properties page, select **[!UICONTROL Change Thumbnail]**.
1. On the Change Thumbnail page, on the toolbar, select **[!UICONTROL Upload New Thumbnail]**.
1. Navigate to a thumbnail image you want to use, select it, then select **[!UICONTROL Open]** to begin uploading the image into Experience Manager. Following the upload, be sure you publish the image.
1. After you have successfully uploaded and published the image, in the Change Thumbnail page, select **[!UICONTROL Save Changes]**.

   The custom thumbnail is added to your video.

-->
