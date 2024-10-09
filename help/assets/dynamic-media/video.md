---
title: Dynamic Media의 비디오
description: Dynamic Media에서 비디오로 작업하는 방법을 알아봅니다. 비디오 인코딩, YouTube에 비디오 게시, 비디오 보고서 보기 및 비디오에 자막 또는 챕터 마커 추가에 대한 모범 사례를 검토하십시오.
contentOwner: Rick Brough
feature: Video Profiles,Best Practices
role: User
exl-id: 0d5fbb3e-b763-415f-8c69-ea36445f882b
source-git-commit: 7a370ee0ab77046d128ae260af2575d50e655254
workflow-type: tm+mt
source-wordcount: '10490'
ht-degree: 2%

---

# 비디오 {#video}

이 섹션에서는 Dynamic Media에서 비디오 작업에 대해 설명합니다.

## 빠른 시작: 비디오 {#quick-start-videos}

다음 단계별 워크플로 설명은 Dynamic Media에서 응용 비디오 세트를 빠르게 시작하고 실행하는 데 도움이 되도록 설계되었습니다. 각 단계 후에는 추가 정보를 찾을 수 있는 주제 머리글에 대한 상호 참조가 있습니다.

>[!NOTE]
>
>Dynamic Media에서 비디오로 작업하기 전에 Adobe Experience Manager 관리자가 이미 Dynamic Media Cloud Service을 활성화하고 구성했는지 확인하십시오.
>
>* Dynamic Media 구성 및 [Dynamic Media 문제 해결](/help/assets/dynamic-media/troubleshoot-dm.md)에서 [Dynamic Media Cloud Service 구성](/help/assets/dynamic-media/config-dm.md#configuring-dynamic-media-cloud-services)을 참조하십시오.
>

1. 다음을 수행하여 **Dynamic Media 비디오를 업로드**:

   * 나만의 비디오 인코딩 프로필을 만듭니다. 또는 Dynamic Media과 함께 제공되는 사전 정의된 _응용 비디오 인코딩_ 프로필을 사용하면 됩니다.

      * [비디오 인코딩 프로필을 만듭니다](/help/assets/dynamic-media/video-profiles.md#creating-a-video-encoding-profile-for-adaptive-streaming).
      * [비디오 인코딩 모범 사례](#best-practices-for-encoding-videos)에 대해 자세히 알아보세요.

   * 기본 소스 비디오를 업로드할 하나 이상의 폴더에 비디오 처리 프로필을 연결합니다.

      * [폴더에 비디오 프로필 적용](/help/assets/dynamic-media/video-profiles.md#applying-a-video-profile-to-folders).
      * [디지털 자산 구성](/help/assets/organize-assets.md)에 대해 자세히 알아보세요.

   * 기본 소스 비디오를 지정된 폴더에 업로드합니다. 추가되면 비디오가 폴더에 할당된 비디오 처리 프로필에 따라 인코딩됩니다.

      * Dynamic Media은 최대 길이가 30분이고 최소 해상도가 25 x 25보다 큰 주로 짧은 형식의 비디오를 지원합니다.
      * 각각 최대 15GB의 비디오 파일을 업로드할 수 있습니다.
      * [비디오를 업로드](/help/assets/manage-video-assets.md#upload-and-preview-video-assets).
      * [지원되는 입력 파일 형식](/help/assets/file-format-support.md)에 대해 자세히 알아보세요.

   * 에셋 또는 워크플로 보기에서 [비디오 인코딩이 어떻게 진행 중인지 모니터링](#monitoring-video-encoding-and-youtube-publishing-progress).

1. 다음을 수행하여 **Dynamic Media 비디오를 관리**:

   * 비디오 자산 구성, 검색 및 검색

      * [디지털 자산 구성](/help/assets/organize-assets.md)
      * [비디오 자산 검색](/help/assets/search-assets.md#custompredicates) 또는 [자산 검색](/help/assets/manage-digital-assets.md#search-assets)

   * 비디오 자산 미리 보기 및 게시

      * 소스 비디오와 비디오의 인코딩된 렌디션을 관련 썸네일과 함께 봅니다.
        [비디오 미리 보기](/help/assets/manage-video-assets.md#upload-and-preview-video-assets) 또는 [에셋 미리 보기](/help/assets/dynamic-media/previewing-assets.md)
        [비디오 표현물 관리](/help/assets/manage-digital-assets.md#managing-renditions)

      * [뷰어 사전 설정 관리](/help/assets/dynamic-media/managing-viewer-presets.md)
      * [자산 게시](/help/assets/dynamic-media/publishing-dynamicmedia-assets.md)

   * 비디오 메타데이터 작업

      * 제목, 설명, 태그 및 사용자 지정 메타데이터 필드와 같은 비디오의 속성을 편집합니다.
        [비디오 속성 편집](/help/assets/manage-digital-assets.md#editing-properties)

      * [디지털 에셋용 메타데이터 관리](/help/assets/manage-metadata.md)
      * [메타데이터 스키마](/help/assets/metadata-schemas.md)

   * 비디오 검토, 승인 및 주석 달기, 전체 버전 제어 유지

      * [비디오에 주석 달기](/help/assets/manage-video-assets.md#annotate-video-assets) 또는 [자산에 주석 달기](/help/assets/manage-digital-assets.md#annotating)

      * [버전 만들기](/help/assets/manage-digital-assets.md#asset-versioning)
      * [자산에 대한 워크플로우 시작](/help/assets/manage-digital-assets.md#starting-a-workflow-on-an-asset)

      * [폴더 자산 검토](/help/assets/bulk-approval.md)
      * [프로젝트](/help/sites-cloud/authoring/projects/overview.md)

1. 다음 중 하나를 수행하여 **Dynamic Media 비디오 Publish**:

   * Experience Manager을 WCM(웹 컨텐츠 관리) 시스템으로 사용하는 경우 웹 페이지에 직접 비디오를 추가할 수 있습니다.

      * [웹 페이지에 비디오를 추가](/help/assets/dynamic-media/adding-dynamic-media-assets-to-pages.md).

   * 서드파티 WCM 시스템을 사용하는 경우 웹 페이지에 비디오를 연결하거나 포함할 수 있습니다.

      * URL을 사용하여 비디오 통합:
        [웹 응용 프로그램에 URL 연결](/help/assets/dynamic-media/linking-urls-to-yourwebapplication.md).

      * 웹 페이지에서 포함 코드를 사용하여 비디오 통합:
        [웹 페이지에 비디오 뷰어를 포함합니다](/help/assets/dynamic-media/embed-code.md).

   * [비디오 보고서 생성](#viewing-video-reports).

   * [비디오에 여러 캡션 및 오디오 트랙을 추가](#about-msma)합니다.

## Dynamic Media에서 비디오 작업 {#working-with-video-in-dynamic-media}

Dynamic Media의 비디오는 데스크톱, 태블릿 및 모바일 장치를 포함하여 여러 화면에서 스트리밍하기 위한 고품질 응용 비디오를 쉽게 게시할 수 있는 종단간 솔루션입니다. 응용 비디오 세트는 다른 비트율 및 형식(예: 400kbps, 800kbps 및 1000kbps)으로 인코딩된 동일한 비디오 버전을 그룹화합니다. 데스크탑 컴퓨터 또는 모바일 장치가 사용 가능한 대역폭을 감지합니다.

예를 들어 iOS 모바일 장치에서 3G, 4G 또는 Wi-Fi와 같은 대역폭을 감지합니다. 그런 다음, 그것은 응용 비디오 세트 내의 다양한 비디오 비트 레이트 중에서 올바른 인코딩된 비디오를 자동으로 선택한다. 비디오는 데스크탑, 모바일 디바이스 또는 태블릿으로 스트리밍됩니다.

또한 데스크탑이나 모바일 장치에서 네트워크 상태가 변경되면 비디오 품질이 자동으로 동적으로 전환됩니다. 또한 고객이 데스크탑에서 전체 화면 모드로 전환하면 응용 비디오 세트가 더 나은 해상도를 사용하여 응답하므로 고객의 시청 경험이 향상됩니다. 응용 비디오 세트를 사용하면 여러 화면 및 장치에서 Dynamic Media 비디오를 재생하는 고객에게 최상의 시청 환경을 제공할 수 있습니다.

비디오 플레이어가 재생할 인코딩된 비디오나 재생 중 선택할 비디오를 결정하는 데 사용하는 논리는 다음 알고리즘을 기반으로 합니다.

1. 비디오 플레이어는 플레이어 자체에서 &quot;초기 비트율&quot;에 대해 설정된 값에 가장 가까운 비트율에 따라 초기 비디오 조각을 로드합니다.
1. 다음 기준을 사용하여 대역폭 속도에 대한 변경 사항에 따라 비디오 플레이어 스위치를 전환합니다.

   1. 플레이어는 추정된 대역폭보다 낮거나 같은 가장 높은 대역폭 스트림을 선택한다.
   1. 플레이어는 가용 대역폭의 80%만을 고려한다. 다만 전환하고 있다면 과대평가를 피하고 곧바로 다시 전환하는 것이 70%에 그쳐 더 보수적이다.

알고리즘에 대한 자세한 기술 정보는 [https://android.googlesource.com/platform/frameworks/av/+/master/media/libstagefright/httplive/LiveSession.cpp](https://android.googlesource.com/platform/frameworks/av/+/master/media/libstagefright/httplive/LiveSession.cpp)을(를) 참조하십시오.

단일 비디오 및 응용 비디오 세트를 관리할 때 지원되는 비디오 세트는 다음과 같습니다.

* 지원되는 다양한 비디오 형식 및 오디오 형식의 비디오를 업로드합니다. 여러 화면에서 재생할 MP4 H.264 형식으로 비디오 인코딩. 미리 정의된 응용 비디오 사전 설정, 단일 비디오 인코딩 사전 설정 또는 자체 인코딩을 사용자 지정하여 비디오의 품질과 크기를 제어할 수 있습니다.

   * 응용 비디오 세트가 생성되면 MP4 비디오가 포함됩니다.
   * **참고**: 기본/원본 비디오가 응용 비디오 집합에 추가되지 않았습니다.

* 모든 HTML5 비디오 뷰어에서 비디오 캡션 기능.
* 전체 메타데이터 지원을 통해 비디오를 구성, 탐색 및 검색하여 비디오 자산을 효율적으로 관리할 수 있습니다.
* 웹 및 데스크탑, 태블릿 및 모바일 장치에 응용 비디오 세트를 제공합니다.

응용 비디오 스트리밍은 다양한 iOS 플랫폼에서 지원됩니다. [Dynamic Media 뷰어 참조 안내서](https://experienceleague.adobe.com/en/docs/dynamic-media-developer-resources/library/viewers-aem-assets-dmc/video/c-html5-video-reference)를 참조하세요.

<!-- OUTDATED 2/28/22 BASED ON CQDOC-18692 Dynamic Media supports mobile video playback for MP4 H.264 video. You can find BlackBerry&reg; devices that support this video format at the following: [Supported video formats on BlackBerry&reg;](https://support.blackberry.com/kb/articleDetail?ArticleNumber=000005482).

OUTDATED 2/28/22 BASED ON CQDOC-18692 You can find Windows&reg; devices that support this video format at the following [Supported video formats on Windows&reg; Phone](https://docs.microsoft.com/en-us/windows/uwp/audio-video-camera/supported-codecs). -->

* 다음을 포함한 Dynamic Media 비디오 뷰어 사전 설정을 사용하여 비디오를 재생합니다.

   * 단일 비디오 뷰어.
   * 비디오 및 이미지 컨텐츠를 모두 결합하는 혼합 미디어 뷰어입니다.

* 브랜딩 요구 사항을 충족하도록 비디오 플레이어를 구성합니다.
* 간단한 URL 또는 포함 코드를 사용하여 비디오를 웹 사이트, 모바일 사이트 또는 모바일 애플리케이션에 통합합니다.

<!-- GIVES a 404 See [Dynamic video playback](https://s7d9.scene7.com/s7/uvideo.jsp?asset=GeoRetail/Mop_AVS&config=GeoRetail/Universal_Video1&stageSize=640,480) sample. -->

[Dynamic Media 뷰어 참조 안내서](https://experienceleague.adobe.com/en/docs/dynamic-media-developer-resources)에서 [Experience Manager Assets 및 Dynamic Media Classic용 뷰어](https://experienceleague.adobe.com/en/docs/dynamic-media-developer-resources/library/viewers-aem-assets-dmc/c-html5-s7-aem-asset-viewers#viewers-aem-assets-dmc) 및 [Experience Manager Assets 전용 뷰어](https://experienceleague.adobe.com/en/docs/dynamic-media-developer-resources/library/viewers-for-aem-assets-only/c-html5-aem-asset-viewers#viewers-for-aem-assets-only)도 참조하세요.

## 우수 사례: HTML5 비디오 뷰어 사용 {#best-practice-using-the-html-video-viewer}

Dynamic Media HTML5 비디오 뷰어 사전 설정은 강력한 비디오 플레이어입니다. 이를 사용하여 HTML5 비디오 재생과 관련된 많은 일반적인 문제 및 모바일 장치와 관련된 문제를 방지할 수 있습니다. 예를 들어, 적응형 비트율 스트리밍 전달이 부족하고 데스크탑 브라우저에 도달이 제한된 경우입니다.

플레이어의 디자인 측면에서는 표준 웹 개발 도구를 사용하여 비디오 플레이어의 기능을 디자인할 수 있습니다. 예를 들어 HTML 5와 CSS를 사용하여 단추, 컨트롤 및 사용자 지정 포스터 이미지 배경을 디자인하여 사용자 지정된 모양으로 고객에게 다가갈 수 있습니다.

뷰어의 재생 측에서는 브라우저의 비디오 기능을 자동으로 감지합니다. 그런 다음 HLS 또는 DASH(적응형 비디오 스트리밍이라고도 함)를 사용하여 비디오를 서비스한다. 또는 이러한 전달 방법이 없는 경우 대신 HTML5 progressive가 사용됩니다.

>[!NOTE]
>
>비디오에 DASH를 사용하려면 먼저 Adobe 기술 지원 팀에서 계정에서 활성화해야 합니다. [계정에서 DASH 사용](#enable-dash)을 참조하세요.

HTML5 및 CSS를 사용하여 재생 구성 요소를 디자인하는 기능을 단일 플레이어에 결합할 수 있습니다. 임베드된 재생이 있을 수 있으며, 브라우저의 기능에 따라 적응형 및 점진적 스트리밍을 사용할 수 있습니다. 이 모든 기능을 사용하면 리치 미디어 콘텐츠의 범위를 데스크탑 및 모바일 사용자 모두로 확장하고 간소화된 비디오 경험을 보장할 수 있습니다.

[Experience Manager Assets 뷰어 참조 안내서](https://experienceleague.adobe.com/en/docs/dynamic-media-developer-resources)에서 [Dynamic Media 전용 뷰어](https://experienceleague.adobe.com/en/docs/dynamic-media-developer-resources/library/viewers-for-aem-assets-only/c-html5-aem-asset-viewers#viewers-for-aem-assets-only)도 참조하세요.


### HTML5 비디오 뷰어를 사용하여 데스크탑 컴퓨터 및 모바일 장치에서 비디오 재생 {#playback-of-video-on-desktop-computers-and-mobile-devices-using-the-html-video-viewer}

데스크탑 및 모바일 응용 비디오 스트리밍의 경우, 비트 전송률 전환에 사용되는 비디오는 응용 비디오 세트의 모든 MP4 비디오를 기반으로 합니다.

비디오 재생은 HLS 또는 DASH 또는 점진적 비디오 다운로드를 사용하여 발생합니다. 6.0, 6.1 및 6.2와 같은 이전 버전의 Experience Manager에서 비디오는 HTTP를 통해 스트리밍되었습니다.

그러나 6.3 Experience Manager 등에서는 DM 게이트웨이 서비스 URL도 항상 HTTPS를 사용하기 때문에 이제 HTTPS(즉, HLS 또는 DASH)를 통해 비디오가 스트리밍됩니다. 이 기본 동작에는 고객에게 영향을 주지 않습니다. 브라우저가 지원하는 경우 비디오 스트리밍은 항상 HTTPS를 통해 발생합니다. 다음 표를 참조하십시오.

따라서

* HTTPS 비디오 스트리밍이 있는 HTTPS 웹 사이트가 있는 경우 스트리밍이 좋습니다.
* HTTPS 비디오 스트리밍이 있는 HTTP 웹 사이트가 있는 경우 스트리밍은 문제가 없으며 웹 브라우저에서 혼합 콘텐츠 문제가 발생하지 않습니다.

DASH는 국제 표준이고 HLS는 Apple 표준입니다. 둘 다 응용 비디오 스트리밍에 사용됩니다. 또한 두 기술 모두 네트워크 대역폭 용량에 따라 자동으로 재생을 조정합니다. 또한 고객이 나머지 비디오가 다운로드될 때까지 기다릴 필요 없이 비디오의 어느 지점으로든 &quot;검색&quot;할 수 있습니다.

점진적 비디오는 사용자의 데스크탑 시스템 또는 모바일 디바이스에 로컬로 비디오를 다운로드 및 저장하여 전달됩니다.

다음 표에서는 [Dynamic Media HTML5 비디오 뷰어](https://experienceleague.adobe.com/en/docs/dynamic-media-developer-resources/library/viewers-for-aem-assets-only/interactive-video/c-html5-aem-int-video#interactive-video)를 사용하는 데스크톱 컴퓨터 및 모바일 장치에서 비디오의 장치, 브라우저 및 재생 방법에 대해 설명합니다.

<table>
 <tbody>
  <tr>
   <td><strong>장치</strong></td>
   <td><strong>브라우저</strong></td>
   <td><strong>비디오 재생 모드</strong></td>
  </tr>
  <tr>
   <td>데스크탑</td>
   <td>Internet Explorer 9 및 10</td>
   <td>점진적 다운로드.</td>
  </tr>
  <tr>
   <td>데스크탑</td>
   <td>Internet Explorer 11+</td>
   <td>Windows® 8 및 Windows® 10의 경우 - DASH 또는 HLS가 요청될 때마다 HTTPS를 강제 사용합니다. 알려진 제한 사항: DASH 또는 HLS의 HTTP가 이 브라우저/운영 체제 조합에서 작동하지 않습니다.<br /> <br /> Windows® 7 - 점진적 다운로드. HTTP와 HTTPS 프로토콜에 표준 논리를 사용합니다.</td>
  </tr>
  <tr>
   <td>데스크탑</td>
   <td>Firefox 23-44</td>
   <td>점진적 다운로드.</td>
  </tr>
  <tr>
   <td>데스크탑</td>
   <td>Firefox 45 이상</td>
   <td>HLS 또는 DASH* 적응형 비트율 스트리밍</td>
  </tr>
  <tr>
   <td>데스크탑</td>
   <td>Chrome</td>
   <td>HLS 또는 DASH* 적응형 비트율 스트리밍</td>
  </tr>
  <tr>
   <td>데스크탑</td>
   <td>Safari(Mac)</td>
   <td>HLS 적응형 비트율 스트리밍</td>
  </tr>
  <tr>
   <td>모바일</td>
   <td>Chrome(Android™ 6 이하)</td>
   <td>점진적 다운로드.</td>
  </tr>
  <tr>
   <td>모바일</td>
   <td>Chrome(Android™ 7 이상)</td>
   <td>HLS 또는 DASH* 적응형 비트율 스트리밍/td&gt;
  </tr>
  <tr>
   <td>모바일</td>
   <td>Android™ (기본 브라우저)</td>
   <td>점진적 다운로드.</td>
  </tr>
  <tr>
   <td>모바일</td>
   <td>Safari(iOS)</td>
   <td>HLS 적응형 비트율 스트리밍</td>
  </tr>
  <tr>
   <td>모바일</td>
   <td>Chrome(iOS)</td>
   <td>HLS 적응형 비트율 스트리밍</td>
  </tr>
 </tbody>
</table>

>[!IMPORTANT]
>
>비디오에 DASH를 사용하려면 먼저 Adobe 기술 지원 팀에서 계정에서 활성화해야 합니다. [계정에서 DASH 사용](#enable-dash)을 참조하세요.

<!--  THIS LINE WAS REMOVED FROM THE TABLE ABOVE ON FEB 28, 2022 BASED ON CQDOC 18692 -RSB <tr>
   <td>Mobile</td>
   <td>BlackBerry&reg;</td>
   <td>HLS or DASH</td>
  </tr>
 -->

## Dynamic Media 비디오 솔루션의 아키텍처 {#architecture-of-dynamic-media-video-solution}

다음 그래픽은 DMGateway(Dynamic Media 하이브리드 모드)를 통해 업로드 및 인코딩되고 공개적으로 사용할 수 있도록 된 비디오의 전체 작성 워크플로를 보여 줍니다.

![chlimage_1-427](assets/chlimage_1-427.png)

## 비디오용 하이브리드 게시 아키텍처 {#hybrid-publishing-architecture-for-videos}

![chlimage_1-428](assets/chlimage_1-428.png)

## 비디오 인코딩 모범 사례 {#best-practices-for-encoding-videos}

Dynamic Media을 사용하도록 설정하고 비디오 Cloud Service을 설정한 경우 **Dynamic Media 비디오 인코딩** 워크플로우가 비디오를 인코딩합니다. This workflow captures workflow process history and failure information. Dynamic Media을 사용하도록 설정하고 비디오 Cloud Service을 설정한 경우 비디오를 업로드할 때 **[!UICONTROL Dynamic Media 인코딩 비디오]** 워크플로가 자동으로 적용됩니다. (Dynamic Media을 사용하지 않는 경우 **[!UICONTROL DAM 자산 업데이트]** 워크플로우가 적용됩니다.)

다음은 소스 비디오 파일을 인코딩하기 위한 모범 사례 팁입니다.

<!-- For advice about video encoding, see the following:

* [Streaming 101: The Basics — Codecs, Bandwidth, Data Rate, and Resolution](https://www.adobe.com/go/learn_s7_streaming101_en).
* [Video Encoding Basics](https://www.adobe.com/go/learn_s7_encoding_en). -->

### Source 비디오 파일 {#source-video-files}

비디오 파일을 인코딩할 때 가능한 한 높은 품질의 소스 비디오 파일을 사용하십시오. 이전에 인코딩된 비디오 파일은 이미 압축되어 있으므로 이 파일을 사용하지 마십시오. 이후에 인코딩하면 품질이 낮은 비디오가 만들어집니다.

* Dynamic Media은 최대 길이가 30분이고 최소 해상도가 25 x 25보다 큰 주로 짧은 형식의 비디오를 지원합니다.
* 각각 최대 15GB인 기본 소스 비디오 파일을 업로드할 수 있습니다.

다음 표에서는 소스 비디오 파일을 인코딩하기 전에 권장되는 크기, 종횡비 및 최소 비트율에 대해 설명합니다.

| 크기 | 종횡비 | 최소 비트 전송률 |
|--- |--- |--- |
| 1024 X 768 | 4:3 | 대부분의 비디오에 대해 4,500kbps입니다. |
| 1280 X 720 | 16:9 | 비디오의 움직임 양에 따라 3000 - 6000kbps입니다. |
| 1920 X 1080 | 16:9 | 비디오의 움직임 양에 따라 6000 - 8000kbps입니다. |

### 파일의 메타데이터 가져오기 {#obtaining-a-file-s-metadata}

비디오용 편집 도구를 사용하거나 메타데이터를 가져오도록 설계된 애플리케이션을 사용하여 파일의 메타데이터를 보면 파일의 메타데이터를 가져올 수 있습니다. 다음은 타사 애플리케이션인 MediaInfo를 사용하여 비디오 파일의 메타데이터를 가져오는 지침입니다.

1. [MediaInfo 다운로드](https://mediaarea.net/en/MediaInfo/Download)(으)로 이동합니다.
1. GUI 버전에 대한 설치 프로그램을 선택하고 다운로드한 다음 설치 지침을 따릅니다.
1. 설치 후 비디오 파일(Windows®에만 해당)을 마우스 오른쪽 단추로 클릭하고 MediaInfo를 선택하거나, MediaInfo를 열고 비디오 파일을 응용 프로그램으로 드래그합니다. 너비, 높이 및 fps를 포함하여 비디오 파일과 연결된 모든 메타데이터가 표시됩니다.

### 종횡비 {#aspect-ratio}

기본 소스 비디오 파일에 대한 비디오 인코딩 사전 설정을 선택하거나 만들 때 사전 설정의 종횡비가 동일한지 확인하십시오. 이 방법은 기본 소스 비디오 파일과의 일관성을 보장합니다. 가로 세로 비율은 비디오 높이에 대한 너비의 비율입니다.

비디오 파일의 종횡비를 결정하려면 파일의 메타데이터를 가져옵니다. 파일의 폭과 높이를 확인합니다(위의 파일 메타데이터 가져오기 참조). 그런 다음 이 공식을 사용하여 종횡비를 결정합니다.

width/height = 종횡비

다음 테이블에서는 공식 결과가 공통 종횡비 선택으로 변환되는 방법을 설명합니다.

| 공식 결과 | 종횡비 |
|--- |--- |
| 1.33 | 4:3 |
| 0.75 | 3:4 |
| 1.78 | 16:9 |
| 0.56 | 9:16 |

예를 들어 1440 너비 x 1080 높이의 비디오에는 1440/1080 또는 1.33의 종횡비가 있습니다. 이 경우 비디오 파일을 인코딩할 종횡비가 4:3인 비디오 인코딩 사전 설정을 선택합니다.

### 비트율 {#bitrate}

비트율은 비디오 재생의 1초를 구성하도록 인코딩된 데이터의 양입니다. 비트율은 초당 킬로비트(Kbps)로 측정됩니다.

>[!NOTE]
>
>모든 코덱은 손실 압축을 사용하기 때문에 비트율은 비디오 품질에서 가장 중요한 요소입니다. 손실 압축을 사용하면 비디오 파일을 압축할수록 품질이 저하됩니다. 이러한 이유로 다른 모든 특성(해상도, 프레임 속도 및 코덱)은 동일하며 비트율이 낮을수록 압축 파일의 품질이 떨어집니다.

비트율 인코딩을 선택할 때 선택할 수 있는 두 가지 유형이 있습니다.

* **[!UICONTROL 상수 비트 전송률 인코딩]**(CBR) - CBR 인코딩 중에 비트 전송률 또는 초당 비트 수가 인코딩 프로세스 전체에서 동일하게 유지됩니다. CBR 인코딩은 전체 비디오에 대해 사용자 설정에 대한 설정된 데이터 속도를 유지합니다. 또한 CBR 인코딩은 품질을 위해 미디어 파일을 최적화하지 않지만 저장 공간을 절약합니다.
전체 비디오에서 비디오에 유사한 동작 수준이 포함되어 있는 경우 CBR을 사용합니다. CBR은 비디오 컨텐츠를 스트리밍하는 데 가장 일반적으로 사용됩니다. [사용자 지정 추가된 비디오 인코딩 매개 변수 사용](/help/assets/dynamic-media/video-profiles.md#using-custom-added-video-encoding-parameters)도 참조하세요.

* **[!UICONTROL 가변 비트율 인코딩]**(VBR) - VBR 인코딩은 압축기에 필요한 데이터를 기반으로 사용자가 설정한 상한으로 데이터 속도를 낮춥니다. 이 기능은 VBR 인코딩 프로세스 중에 미디어 파일의 비트율이 미디어 파일의 비트율 요구 사항에 따라 동적으로 증가하거나 감소함을 의미합니다.
VBR을 인코딩하는 데 시간이 더 오래 걸리지만 가장 유리한 결과를 생성합니다. 미디어 파일의 품질이 우수합니다. VBR은 비디오 컨텐츠의 HTTP 점진적 전달에 가장 일반적으로 사용됩니다.

VBR 및 CRB는 언제 사용합니까?
VBR 대 CBR을 선택할 때는 거의 항상 미디어 파일에 VBR을 사용하는 것이 좋습니다. VBR은 경쟁사 비트레이트로 고품질 파일을 제공합니다. VBR을 사용하는 경우 2회 인코딩 시 를 사용하고 최대 비트율을 대상 비디오 비트율의 1.5배로 설정해야 합니다.

비디오 인코딩 사전 설정을 선택할 때는 대상 사용자의 연결 속도를 고려해야 합니다. 데이터 속도가 해당 속도의 80%인 사전 설정을 선택합니다. 예를 들어 대상 사용자의 연결 속도가 1000Kbps이면 비디오 데이터 속도가 800Kbps인 사전 설정이 가장 좋습니다.

이 표에서는 일반적인 연결 속도의 데이터 속도를 설명합니다.

| 속도(Kbps) | 연결 유형 |
|--- |--- |
| 256 | 전화 접속 연결. |
| 800 | 일반적인 모바일 연결입니다. 이 연결의 경우 3G 경험에 대해 400에서 최대 800 범위의 데이터 속도를 타깃팅하십시오. |
| 2000 | 일반적인 광대역 데스크탑 연결. 이 연결의 경우 800-2000Kbps 범위에서 데이터 전송률을 타겟팅하고 대부분의 타겟은 평균 1200-1500Kbps입니다. |
| 5000 | 일반적인 고속 광대역 연결입니다. 대부분의 소비자는 이 속도로 비디오를 전송할 수 없으므로 이 상위 범위의 인코딩은 권장되지 않습니다. |

### 해결 방법 {#resolution}

**해상도**&#x200B;에서는 비디오 파일의 높이와 너비를 픽셀 단위로 설명합니다. 대부분의 소스 비디오는 고해상도로 저장됩니다(예: 1920 x 1080). 스트리밍을 위해 소스 비디오는 더 작은 해상도(640 x 480 이하)로 압축된다.

해상도 및 데이터 속도는 비디오 품질을 결정하는 두 가지 통합 연결 요소입니다. 동일한 비디오 품질을 유지하려면 비디오 파일의 픽셀 수가 많을수록(해상도가 높을수록) 데이터 전송률이 높아야 합니다. 예를 들어 320 x 240 해상도 및 640 x 480 해상도 비디오 파일의 프레임당 픽셀 수를 생각해 보십시오.

| 해결 방법 | 프레임당 픽셀 |
|--- |--- |
| 320 x 240 | 76,800 |
| 640 x 480 | 307,200 |

640 x 480 파일은 프레임당 픽셀 수가 4배 더 많습니다. 이러한 두 가지 예제 해상도에 대해 동일한 데이터 전송률을 달성하려면 640 x 480 파일에 4배의 압축을 적용하여 비디오의 품질을 낮출 수 있습니다. 따라서 비디오 데이터 속도가 250Kbps이면 320x240 해상도에서는 고화질을 볼 수 있지만 640x480 해상도에서는 고화질을 볼 수 없습니다.

일반적으로 높은 데이터 전송률을 사용할수록 비디오가 더 잘 나타나며, 높은 해상도를 사용할수록 낮은 해상도와 비교하여 보기 품질을 유지해야 하는 데이터 전송률이 높아집니다.

해상도와 데이터 속도는 연결되어 있으므로 비디오를 인코딩할 때는 두 가지 옵션이 있습니다.

* 데이터 전송률을 선택한 다음 선택한 데이터 전송률에 잘 맞는 가장 높은 해상도로 인코딩하십시오.
* 해상도를 선택한 다음 선택한 해상도로 고품질 비디오를 구현하는 데 필요한 데이터 속도로 인코딩합니다.

기본 소스 비디오 파일에 대한 비디오 인코딩 사전 설정을 선택(또는 생성)할 때 다음 표를 사용하여 올바른 해상도를 타겟팅합니다.

| 해결 방법 | 높이(픽셀) | 화면 크기 |
|--- |--- |--- |
| 240p | 240 | 작은 화면 |
| 300p | 300 | 일반적으로 모바일 장치용 작은 화면 |
| 360p | 360 | 작은 화면 |
| 480p | 480 | Medium 화면 |
| 720p | 720 | 대형 화면 |
| 1080p | 1080 | HD 대형 화면 |

### Fps(초당 프레임) {#fps-frames-per-second}

미국과 일본에서는 대부분의 비디오가 29.97fps로 촬영되며, 유럽에서는 대부분의 비디오가 25fps로 촬영됩니다. 필름은 24fps로 촬영됩니다.

기본 소스 비디오 파일의 fps 속도와 일치하는 비디오 인코딩 사전 설정을 선택합니다. 예를 들어 기본 소스 비디오가 25fps인 경우 25fps의 인코딩 사전 설정을 선택합니다. 기본적으로 모든 사용자 지정 인코딩은 기본 소스 비디오 파일의 fps를 사용합니다. 따라서 비디오 인코딩 사전 설정을 만들 때 fps 설정을 명시적으로 지정할 필요가 없습니다.

### 비디오 인코딩 차원 {#video-encoding-dimensions}

최적의 결과를 얻으려면 소스 비디오가 모든 인코딩된 비디오의 전체 배수가 되도록 인코딩 차원을 선택하십시오.

이 비율을 계산하려면 소스 너비를 인코딩된 너비로 나누어 너비 비율을 가져옵니다. 그런 다음 인코딩된 높이로 소스 높이를 나누어 높이 비율을 가져옵니다.

결과 비율이 전체 정수인 경우 비디오의 크기가 최적으로 조정됨을 의미합니다. 결과 비율이 전체 정수가 아닌 경우 남은 픽셀 아티팩트를 디스플레이에 남겨 비디오 품질에 영향을 줍니다. 이 효과는 비디오에 텍스트가 있을 때 가장 두드러집니다.

예를 들어 소스 비디오가 1920 x 1080이라고 가정합니다. 다음 표에서 세 개의 인코딩된 비디오는 사용할 최적의 인코딩 설정을 제공합니다.

| 비디오 유형 | 너비 x 높이 | 폭 비율 | 높이 비율 |
|--- |--- |--- |--- |
| 소스 | 1920 x 1080 | 1 | 1 |
| 인코딩됨 | 960 x 540 | 2 | 2 |
| 인코딩됨 | 640 x 360 | 3 | 3 |
| 인코딩됨 | 480 x 270 | 4 | 4 |

### 인코딩된 비디오 파일 형식 {#encoded-video-file-format}

Dynamic Media에서는 MP4 H.264 비디오 인코딩 사전 설정을 사용하는 것이 좋습니다. MP4 파일은 H.264 비디오 코덱을 사용하기 때문에 고품질의 비디오를 제공하지만 압축된 파일 크기입니다.

## 비디오 보고서 보기 {#viewing-video-reports}

>[!NOTE]
>
>비디오 보고서는 Dynamic Media - 하이브리드 모드를 실행하는 경우에만 사용할 수 있습니다.

비디오 보고서에는 *게시된* 개별 및 집계 비디오가 예상대로 작동하는지 모니터링하는 데 도움이 되는 몇 가지 집계 지표가 지정된 기간 동안 표시됩니다. 전체 웹 사이트에 게시된 모든 비디오에 대해 다음 상위 지표 데이터가 집계됩니다.

* 비디오 시작
* 완료율
* 비디오의 평균 시간
* 비디오의 총 시간
* 방문당 비디오

총 비디오 시작에 따라 웹 사이트에서 가장 많이 본 비디오를 추적할 수 있도록 모든 *게시된* 비디오의 표도 나열됩니다.

목록에서 비디오 이름을 선택하면 비디오의 대상 유지(드롭다운) 보고서가 선 차트 형태로 표시됩니다. 이 차트는 비디오 재생 중 주어진 시간 동안의 보기 수를 표시합니다. 비디오를 재생하면 세로 막대가 플레이어의 시간 표시기와 동기화되어 추적됩니다. 라인 차트 데이터의 드롭은 대상이 비관심에서 이탈하는 위치를 나타냅니다.

비디오가 Adobe Experience Manager Dynamic Media 외부에서 인코딩된 경우 대상 유지 (드롭오프) 차트 및 테이블의 재생 비율 데이터를 사용할 수 없습니다.

>[!NOTE]
>
>추적 및 보고 데이터는 전적으로 Dynamic Media의 자체 비디오 플레이어 및 관련 비디오 플레이어 사전 설정 사용을 기반으로 합니다. 따라서 다른 비디오 플레이어가 재생하는 비디오를 추적하고 보고할 수 없습니다.

기본적으로 비디오 보고서를 처음 입력할 때 보고서에는 현재 월의 첫 번째 날짜부터 시작하여 현재 월의 날짜로 끝나는 비디오 데이터가 표시됩니다. 그러나 고유한 날짜 범위를 지정하여 기본 날짜 범위를 재정의할 수 있습니다. 다음 번에 비디오 보고서에서 지정한 날짜 범위가 사용됩니다.

비디오 보고서가 올바르게 작동하려면 Dynamic Media Cloud Service이 구성될 때 보고서 세트 ID가 자동으로 만들어집니다. 동시에 보고서 세트 ID는 Publish 서버에 푸시되므로 에셋을 미리 볼 때 URL 복사 기능에 사용할 수 있습니다. 그러나 이 기능을 사용하려면 Publish 서버가 이미 설정되어 있어야 합니다. Publish 서버가 설정되지 않은 경우에도 을 게시하여 비디오 보고서를 볼 수 있습니다. 그러나 Dynamic Media 클라우드 구성으로 돌아가 **[!UICONTROL 확인]**&#x200B;을 선택해야 합니다.

**비디오 보고서를 보려면:**

1. Experience Manager의 왼쪽 상단 모서리에서 Experience Manager 로고를 선택합니다. 왼쪽 레일에서 **[!UICONTROL 도구]**(망치 아이콘) > **[!UICONTROL Assets]** > **[!UICONTROL 비디오 보고서]**(으)로 이동합니다.
1. 비디오 보고서 페이지에서 다음 중 하나를 수행합니다.

   * 오른쪽 상단 모서리에서 **[!UICONTROL 비디오 보고서 새로 고침]** 아이콘을 선택합니다.
보고서의 종료 날짜가 현재 날짜인 경우에만 새로 고침 을 사용할 수 있습니다. 이 기능을 사용하면 마지막으로 보고서를 실행한 이후 발생한 비디오 추적을 볼 수 있습니다.

   * 오른쪽 상단 모서리에서 **[!UICONTROL 날짜 선택기]** 아이콘을 선택합니다.
비디오 데이터를 표시할 시작 및 종료 날짜 범위를 지정한 다음 **[!UICONTROL 보고서 실행]**&#x200B;을 선택합니다.

   [최상위 지표] 그룹 상자는 사이트에서 모든 *게시된* 비디오에 대한 다양한 집계 측정을 식별합니다.

1. 가장 많이 게시된 비디오를 나열하는 표에서 비디오를 재생할 비디오 이름을 선택하고 비디오의 대상 유지(드롭오프) 보고서도 확인합니다.

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


## Dynamic Media 계정에서 DASH, 다중 캡션 및 다중 오디오 트랙, AI 생성 캡션 지원 활성화 {#enable-dash}

Dynamic Media에서 다음에 대한 지원을 활성화할 수 있습니다.

* 대시
* 다중 캡션 및 오디오 트랙
* AI 생성 캡션(제한된 가용성)

Adobe 고객 지원 사례를 만들고 제출하여.

위의 세 가지 기능 중 하나를 활성화하면 모든 기능이 활성화됩니다. 따라서 DASH만 활성화하려는 경우 실제로 위에 나열된 세 가지 기능을 모두 활성화합니다.

| 기능 | 설명 |
| --- | --- |
| 대시 | DASH(Digital Adaptive Streaming over HTTP)는 비디오 스트리밍에 대한 국제 표준이며 다양한 비디오 뷰어에서 널리 채택됩니다. 계정에서 DASH가 활성화되면 적응형 비디오 스트리밍을 위해 DASH 또는 HLS 중에서 선택할 수 있는 옵션이 제공됩니다. 또는 뷰어 사전 설정에서 재생 유형으로 **[!UICONTROL 자동]**&#x200B;이(가) 선택된 경우 플레이어 간에 자동 전환으로 둘 다 선택할 수 있습니다.<br>계정에서 DASH를 활성화하면 다음과 같은 몇 가지 주요 이점이 있습니다.<br>·적응형 비트 전송률 스트리밍을 위한 DASH 스트림 비디오 패키지. 이러한 방식은 전달의 효율성을 높이는 결과를 초래한다. 적응형 스트리밍은 고객에게 최상의 시청 환경을 제공합니다.<br>·브라우저가 HLS와 DASH 스트리밍 사이의 Dynamic Media 플레이어 스위치를 사용하여 스트리밍을 최적화하여 최상의 서비스 품질을 보장합니다. Safari 브라우저를 사용하면 비디오 플레이어가 HLS로 자동 전환됩니다.<br>·비디오 뷰어 사전 설정을 편집하여 선호하는 스트리밍 방법(HLS 또는 DASH)을 구성할 수 있습니다.<br>·최적화된 비디오 인코딩으로 DASH 기능을 사용하도록 설정하는 동안 추가 저장소를 사용하지 않도록 합니다. 비디오 저장 비용을 최적화하기 위해 HLS 및 DASH 둘 모두에 대해 단일 비디오 인코딩 세트가 생성된다.<br>·고객이 비디오 게재를 더 쉽게 이용할 수 있도록 지원합니다.<br>·API를 통해 스트리밍 URL도 가져옵니다. |
| 다중 캡션 및 오디오 트랙 | 여러 캡션 및 오디오 트랙 지원을 자동으로 활성화할 수 있습니다. 활성화한 후 업로드하는 모든 후속 비디오는 비디오에 다중 캡션 및 오디오 트랙을 추가하는 지원이 포함된 새로운 백엔드 아키텍처로 처리됩니다. |
| AI 생성 캡션(제한된 가용성) | AI에서 제공하는 비디오의 캡션을 만듭니다. AI를 사용하여 비디오 트랜스크립트를 만들고 캡션으로 변환합니다. 타임라인도 정의되었습니다. |

>[!IMPORTANT]
>
>Dynamic Media 계정에서 여러 캡션 및 오디오 트랙 지원을 사용하도록 *이전*&#x200B;에 업로드한 모든 비디오가 [다시 처리되어야 합니다](/help/assets/dynamic-media/about-image-video-profiles.md#reprocessing-assets). 이 비디오 재처리 단계는 여러 캡션 및 오디오 트랙 기능을 사용할 수 있도록 필요합니다. 비디오 URL은 재처리 후에도 계속 정상적으로 작동하고 재생됩니다.

**Dynamic Media 계정에서 DASH, 다중 캡션 및 다중 오디오 트랙과 AI 생성 캡션 지원을 활성화하려면:**

1. [Admin Console을 사용하여 새 지원 사례 만들기를 시작합니다](https://helpx.adobe.com/kr/enterprise/using/support-for-experience-cloud.html).
1. 지원 사례를 생성하려면 다음 정보를 제공하면서 지침을 따르십시오.

   * 기본 담당자 이름, 이메일, 전화.
   * Cloud Service 환경(프로그램 ID 및 환경 ID)입니다.
   * Dynamic Media 회사 계정 이름.
   * Dynamic Media 지역: 북미(NA), 아시아 태평양(APAC) 또는 유럽-중동-아시아(EMEA).
   * DASH, 다중 캡션 및 다중 오디오 트랙, 그리고 AEM as a Cloud Service의 Dynamic Media 계정에서 AI 생성 캡션(제한된 가용성)을 지원하도록 지정합니다.

1. Adobe 고객 지원에서 요청을 제출한 순서에 따라 사용자를 고객 대기 목록에 추가합니다.
1. Adobe이 요청을 처리할 준비가 되면 고객 지원 센터에서 연락하여 지원 대상 날짜를 조정하고 설정합니다.
1. Adobe 고객 지원 센터에서 완료 후 알려 줍니다.
1. 이제 다음 중 하나를 수행합니다.

   * 평소대로 [비디오 뷰어 사전 설정](/help/assets/dynamic-media/managing-viewer-presets.md#creating-a-new-viewer-preset)을 만듭니다.
   * 평소대로 [비디오 프로필](/help/assets/dynamic-media/video-profiles.md)을 만듭니다.
   * 비디오에 [여러 캡션 및 오디오 트랙을 추가](#add-msma)합니다.


<!-- HIDDEN AS OF OCTOBER 7, 2024 AS PER EMAIL REQUEST FROM RIYA MIDHA ON SAME DATE 

## About multiple caption and audio track support for videos in Dynamic Media{#about-msma}

With multiple caption and audio track capability in Dynamic Media, you can easily add multiple captions and audio tracks to a primary video. This capability means that your videos are accessible to a global audience. You can customize a single, published primary video to a global audience in multiple languages and adhere with accessibility guidelines for different geographical regions. Authors can also manage the captions and audio tracks from a single tab in the user interface.

   ![Captions and audio tracks tab in Dynamic Media along with a table showing uploaded .VTT caption files and uploaded .MP3 audio track files for a video.](/help/assets/dynamic-media/assets/msma-caption-audiotracks-tab2.png)


Some of the use cases to consider for adding multiple captions and audio tracks to your primary video include the following:


| Type | Use case | 
| --- | --- |
| Captions | Multiple language support<br>Descriptive text for accessibility |
|Audio tracks | Multiple language support<br>Commentary tracks<br>Descriptive audio |


All [video formats supported in Dynamic Media](/help/assets/file-format-support.md) and all Dynamic Media video viewers-except the Dynamic Media Video_360 viewer-are supported for use with multiple captions and audio tracks.

Multi-caption and multi-audio track capability is available for your Dynamic Media account by way of a feature toggle that must be enabled (turned on) by Adobe Customer Support.

### Add multiple captions and audio tracks to your video {#add-msma}

Before you add multiple caption and audio tracks to your video, be sure you already have the following in-place:

* Dynamic Media is set up in an AEM environment.
* A [Dynamic Media Video profile is applied to the folder where your videos are ingested](/help/assets/dynamic-media/video-profiles.md#applying-a-video-profile-to-folders).
* [Multi-caption, and multi-audio track is enabled on your Dynamic Media account](/help/assets/dynamic-media/video.md#enable-dash).

Added captions and captions are supported with WebVTT and Adobe VTT formats. And, added audio track files are supported with MP3 format.

>[!IMPORTANT]
>
>Any videos that you uploaded before enabling multiple caption and audio track support on your Dynamic Media account, [must be reprocessed](/help/assets/dynamic-media/about-image-video-profiles.md#reprocessing-assets). This video reprocessing step is necessary so that multiple caption and audio track capability is available to them. The video URLs continue to work and play as usual, after reprocessing.

**To add multiple captions and audio tracks to your video:**

1. [Upload your primary video to a folder](/help/assets/manage-video-assets.md#upload-and-preview-video-assets) that already has a video profile assigned to it.
1. Navigate to the uploaded video asset that you want to add multiple caption and audio tracks.
1. In asset selection mode, either from the List View or the Card View, select the video asset.
1. On the toolbar, select the Properties icon (a circle with an "i" in it). 

   ![Asset properties button.](/help/assets/dynamic-media/assets/msma-selectedasset-propertiesbutton.png)*Selected video asset in Card View.*

1. On the video's Properties page, select the **[!UICONTROL Captions & Audio Tracks]** tab.


   >[!TIP]
   >If you do not see the [!UICONTROL Captions & Audio Tracks] tab, it means either one of two things:
   >* The folder in which the selected video resides does not have a video profile assigned to it. In which case, see [Apply a video profile to the folder](/help/assets/dynamic-media/video-profiles.md#applying-video-profiles-to-specific-folders)
   >* Or, Dynamic Media must reprocess the video. In which case, see [Reprocess Dynamic Media assets in a folder](/help/assets/dynamic-media/about-image-video-profiles.md#reprocessing-assets).

    When you have completed either one of the above tasks, return to these steps.

   ![Asset properties](/help/assets/dynamic-media/assets/msma-audiotracks.png)*Captions and audio tracks tab on the video's Properties page.*

1. (Optional) To add one or more caption files to a video, do the following:

    * Select **[!UICONTROL Upload Captions]**.
    * Navigate to, and select, one or more `.vtt` (Video Text Tracks) files and open them.
    * For captions to be visible on the media player, you must add required details (metadata) about each caption file that you uploaded. Select the pencil icon to the right of a caption file name. In the Edit Caption dialog box, enter the following required details about the file, then select **[!UICONTROL Save]**. Repeat this process for each caption file that you uploaded:


    | Caption metadata | Description | 
    | --- | --- | 
    Filename | The default filename is derived from the original filename. The filename can be changed only while uploading and cannot be changed later. Filename character requirements are the same as for AEM Assets.<br>The same filename cannot be used for additional caption files and audio track files. |
    | Language | Select the language of the caption. |
    | Type | Select the type of caption that you are using.<br>**Subtitle** - The caption text displayed with the video that translates or transcribes the dialogue.<br>**Caption** - The caption text includes background noises and speaker identification. It also includes other relevant details alongside the translation or transcription of dialogue. This functionality makes the content more accessible to individuals who are deaf or hard of hearing. |
    | Label | The text that is displayed for the caption's name in the **[!UICONTROL Select audio or caption]** pop-up list in the media player. The label is what a customer sees that corresponds to a subtitle or caption track. For example, English (CC). |

    You can change or edit caption metadata later, if necessary. When the video is published, these details are reflected on public URLs in published videos.

1. (Optional) To add one or more audio tracks to a video, do the following:

    * Select **[!UICONTROL Upload Audio Tracks]**.
    * Navigate to, and select, one or more .mp3 files and open them.
    * To make audio tracks visible in the **[!UICONTROL Select audio or caption]** pop-up list on the media player, add the required details for each audio track file. Ensure you include all necessary information for proper display. Select the pencil icon to the right of an audio track file name. In the Edit Audio Track dialog box, enter the following required details, then select **[!UICONTROL Save]**. Repeat this process for each audio track file that you uploaded.

    | Audio Track metadata | Description |
    | --- | --- |
    | Filename | The default filename is derived from the original filename. The filename can be changed only while uploading and cannot be changed later. Filename character requirements are the same as for AEM Assets.<br>The same filename cannot be used for additional audio track files or caption files.| 
    | Language | Select the language of the audio track. |
    | Type | Select the type of audio track that you are using.<br>**Original** - The audio track originally attached to the video and represented as `[Original]` in the label with English language selected by default. While **[!UICONTROL Label]** and **[!UICONTROL Language]** can be changed in the **[!UICONTROL Edit Audio Track]** dialog box, it defaults to the original values if the primary video is reprocessed.<br>**Standard** - An add-on audio track for a language other than the original.<br>**Audio description** - An audio track that also includes a descriptive narration of non-verbal actions and gestures in the video, making content more accessible for individuals who are visually impaired. |
    | Label | The text that is displayed as the audio track's name in the **[!UICONTROL Select audio or caption]** pop-up list in the media player. The label is what a customer sees that corresponds to an audio track. For example, `English [Original]`. The label of audio attached to a video is set to `[Original]` by default. |

    You can change or edit this audio track metadata later, if necessary. When the video is published, these details are reflected on public URLs in published videos.

1. In the upper-right corner of the page, from the **[!UICONTROL Save & Close]** drop-down list, select **[!UICONTROL Save]**. The files are uploaded and metadata processing begins, as seen in the Status column of the interface.

    >[!NOTE]
    >
    >Based on the caching settings of your instance, the metadata processing can take several minutes before it is reflected in preview and in published URLs.

1. (Optional) If you selected **[!UICONTROL Save & Close]** in the previous step, instead of selecting **[!UICONTROL Save]**, you can still view the processing status of the uploaded files. See [View the lifecycle status of uploaded caption and audio track files](/help/assets/dynamic-media/video.md#lifecycle-status-video).

1. (Optional) Preview the video before publishing to ensure the captions and audio work as expected. See [Preview a video that has multiple captions and audio tracks](/help/assets/dynamic-media/video.md#preview-video-audio-subtitle).

1. Publish the video. See [Publish assets](/help/assets/dynamic-media/publishing-dynamicmedia-assets.md). -->



## Dynamic Media의 비디오에 대한 여러 캡션 및 오디오 트랙 지원 정보{#about-msma}

Dynamic Media의 여러 캡션 및 오디오 트랙 기능을 사용하면 여러 오디오 트랙을 쉽게 추가할 수 있습니다. 자신의 `.vtt`(비디오 텍스트 트랙) 파일 또는 AI가 생성한 캡션 파일을 사용하여 여러 캡션 파일을 추가할 수도 있습니다. Dynamic Media의 AI 생성 캡션은 정확하고 동기화된 자막을 자동으로 생성하여 비디오 접근성과 참여를 향상시키도록 설계되었습니다. 이 기술은 고급 AI 알고리즘을 사용하여 음성 콘텐츠를 텍스트로 변환한 다음 비디오에 캡션으로 표시됩니다. 이 기술의 몇 가지 주요 기능은 다음과 같습니다.

* **자동 트랜스크립션:** AI 시스템은 음성 단어를 텍스트로 실시간으로 트랜스크립션하여 캡션이 빠르고 정확하게 생성되도록 합니다.
* **다국어 지원:** 캡션은 60개 이상의 언어로 자동으로 배달되므로 글로벌 대상자에게 쉽게 연결할 수 있습니다.
* **향상된 액세스 가능성:** 캡션을 제공하면 청각 장애가 있거나 난청인 뷰어 또는 사운드가 꺼진 상태에서 비디오를 보려는 사용자가 비디오에 보다 쉽게 액세스할 수 있습니다.
* **향상된 참여:** 캡션을 사용하면 특히 소음이 많은 환경에서 또는 뷰어의 기본 언어가 비디오의 언어와 다를 때 뷰어의 주의를 집중하고 이해력을 향상시킬 수 있습니다.

이러한 기능을 통해 AI 기반 캡션은 비디오 콘텐츠의 접근성 및 참여를 향상시키려는 콘텐츠 크리에이터에게 유용한 도구가 됩니다.

![Dynamic Media의 캡션 및 오디오 트랙 탭과 업로드된 .VTT 캡션 파일 및 비디오용 .MP3 오디오 트랙 파일을 보여 주는 표를 함께 제공합니다.](/help/assets/dynamic-media/assets/msma-caption-audiotracks-tab2.png)

기본 비디오에 여러 캡션 및 오디오 트랙을 추가하는 데 고려할 사용 사례는 다음과 같습니다.

| 유형 | 사용 사례 |
|--- |--- |
| **캡션** | 다중 언어 지원 |
|  | 접근성을 위한 설명 텍스트 |
| **오디오 트랙** | 다중 언어 지원 |
|  | 주석 트랙 |
|  | 설명 오디오 |

Dynamic Media *Video_360* 뷰어를 제외한 Dynamic Media](/help/assets/file-format-support.md) 및 모든 Dynamic Media 비디오 뷰어에서 지원되는 모든 [비디오 형식 및 여러 캡션 및 오디오 트랙과 함께 사용할 수 있습니다.

다중 캡션 및 다중 오디오 추적 기능은 고객 지원 Adobe에서 활성화(켜기)해야 하는 기능 전환을 통해 Dynamic Media 계정에 사용할 수 있습니다.

### 비디오에 여러 캡션 및 오디오 트랙 추가 {#add-msma}

비디오에 여러 캡션 및 오디오 트랙을 추가하기 전에 이미 다음 캡션 및 오디오 트랙이 있는지 확인하십시오.

* Dynamic Media은 AEM 환경에 설정됩니다.
* [Dynamic Media 비디오 프로필이 비디오가 수집되는 폴더에 적용됩니다](/help/assets/dynamic-media/video-profiles.md#applying-a-video-profile-to-folders).
* [다중 캡션/오디오 트랙 및 AI 생성 캡션이 Dynamic Media 계정에 활성화되어 있습니다](#enable-dash).

추가된 캡션은 WebVTT 및 Adobe VTT 형식으로 지원됩니다. 또한 추가된 오디오 트랙 파일은 MP3 포맷으로 지원됩니다.

>[!IMPORTANT]
>
>Dynamic Media 계정에서 여러 캡션/오디오 트랙 지원 또는 AI 생성 캡션을 사용하도록 *이전*&#x200B;에 업로드된 비디오의 경우 [다시 처리해야 합니다](/help/assets/dynamic-media/about-image-video-profiles.md#reprocessing-assets). 이 재처리 단계에서는 이러한 비디오가 여러 캡션/오디오 트랙 및 AI가 생성한 캡션 기능을 사용할 수 있도록 합니다. 재처리 후에도 비디오 URL은 평소대로 계속 작동하고 재생됩니다.

**비디오에 여러 캡션 및 오디오 트랙을 추가하려면:**

1. [이미 비디오 프로필이 할당된 폴더에 기본 비디오를 업로드](/help/assets/manage-video-assets.md#upload-and-preview-video-assets)합니다.
1. 여러 캡션 및 오디오 트랙을 추가하려는 업로드된 비디오 자산으로 이동합니다.
1. 에셋 선택 모드의 목록 보기 또는 카드 보기에서 비디오 에셋을 선택합니다.
1. 도구 모음에서 속성 아이콘(안에 &quot;i&quot;가 있는 원)을 클릭합니다.
   ![선택한 비디오 자산에 비디오 썸네일 이미지 위에 체크 표시가 있고 도구 모음에 속성 보기가 강조 표시되어 있습니다.](/help/assets/dynamic-media/assets/msma-selectedasset-propertiesbutton.png)*카드 보기에서 선택한 비디오 자산입니다.*
1. 비디오의 속성 페이지에서 **[!UICONTROL 캡션 및 오디오 트랙]** 탭을 선택합니다.

   >[!TIP]
   >**[!UICONTROL 캡션 및 오디오 트랙]** 탭이 표시되지 않으면 다음 두 가지 중 하나를 의미합니다.
   >
   >* 선택한 비디오가 있는 폴더에 비디오 프로필이 할당되어 있지 않습니다. 이 경우 [폴더에 비디오 프로필 적용](/help/assets/dynamic-media/video-profiles.md#applying-video-profiles-to-specific-folders)을 참조하세요.
   >* 또는 Dynamic Media에서 비디오를 재처리해야 합니다. 이 경우 [폴더에서 Dynamic Media 자산 재처리](/help/assets/dynamic-media/about-image-video-profiles.md#reprocessing-assets)를 참조하십시오.
   >
   >위의 작업 중 하나를 완료했으면 다음 단계로 돌아갑니다.

   속성 페이지의 ![캡션 및 오디오 트랙 탭](/help/assets/dynamic-media/assets/msma-audiotracks.png)
   *비디오의 속성 페이지에 있는 캡션 및 오디오 트랙 탭*

1. 비디오에 하나 이상의 오디오 트랙을 추가하려면 다음을 수행하십시오.
   1. **[!UICONTROL 오디오 트랙 업로드]**&#x200B;를 선택합니다.
   1. 하나 이상의 .mp3 파일로 이동하여 선택한 다음 엽니다.
   1. 미디어 플레이어의 **[!UICONTROL 오디오 또는 캡션 선택]** 팝업 목록에 오디오 트랙을 표시하려면 각 오디오 트랙 파일에 대한 필수 세부 정보를 추가해야 합니다. 이렇게 하면 모든 오디오 트랙이 올바르게 나열되고 액세스할 수 있습니다. 오디오 트랙 파일 이름 오른쪽에 있는 연필 아이콘을 선택합니다. **오디오 트랙 편집** 대화 상자에 다음과 같은 필수 세부 정보를 입력하십시오.

      | 오디오 트랙 메타데이터 | 설명 |
      |--- |--- |
      | 파일 이름 | 기본 파일 이름은 원래 파일 이름에서 파생됩니다. 파일 이름은 업로드 중에만 변경할 수 있으며 나중에 변경할 수 없습니다. 파일 이름 문자 요구 사항은 AEM Assets의 요구 사항과 동일합니다.<br>추가 오디오 트랙 파일 또는 캡션 파일에 같은 파일 이름을 사용할 수 없습니다. |
      | 언어 | 오디오 트랙의 올바른 언어를 선택합니다. |
      | 유형 | 사용 중인 오디오 트랙 유형을 선택합니다.<br>**원본** - 비디오에 원래 첨부되고 기본적으로 `English` 언어가 선택된 레이블에 `[Original]`(으)로 표시되는 오디오 트랙입니다. **[!UICONTROL 오디오 트랙 편집]** 대화 상자에서 **[!UICONTROL Label]** 및 **[!UICONTROL Language]**&#x200B;을(를) 변경할 수 있지만 기본 비디오가 다시 처리되는 경우에는 기본값이 원래 값으로 설정됩니다.<br>**표준** - 원본이 아닌 언어에 대한 추가 기능 오디오 트랙입니다.<br>**오디오 설명** - 비디오 내의 비언어적 동작 및 제스처에 대한 설명 설명을 포함하는 오디오 트랙으로, 시각 장애가 있는 개인이 콘텐츠에 더 쉽게 액세스할 수 있습니다. |
      | 레이블 | 미디어 플레이어의 **[!UICONTROL 오디오 또는 캡션 선택]** 팝업 목록에서 오디오 트랙 이름으로 표시되는 텍스트입니다. 레이블은 오디오 트랙에 해당하는 것으로, 고객에게 표시됩니다. 예, `English [Original]`. 비디오에 첨부된 오디오의 레이블은 기본적으로 `[Original]`(으)로 설정됩니다. |

      필요한 경우 나중에 이 오디오 트랙 메타데이터를 변경하거나 편집할 수 있습니다. 비디오가 게시되면 이러한 세부 사항이 게시된 비디오의 공개 URL에 반영됩니다.

   1. 페이지의 오른쪽 상단 근처에 있는 **[!UICONTROL 저장 및 닫기]** 드롭다운에서 **[!UICONTROL 저장]**&#x200B;을 클릭합니다.
   1. 다음 중 하나를 수행하십시오.
      * 업로드하는 각 오디오 트랙 파일에 대해 이 프로세스를 반복합니다.
      * 다음 단계로 계속하여 비디오에 캡션을 추가합니다.

1. 비디오에 하나 이상의 캡션 파일을 추가하려면 다음 사용 사례 중 시나리오에 가장 적합한 사용 사례를 선택합니다.

   |  | 사용 사례 | 사용할 캡션 만들기 옵션 |
   | --- | --- | --- |
   | **옵션 1** | 사용하려는 언어로 된 기존 캡션 파일이 있습니다.<br>아래의 **옵션 1**&#x200B;을 참조하세요. | **[!UICONTROL 파일 업로드]** |
   | **옵션 2** | AI가 여러 언어로 캡션 파일을 생성했으면 합니다.<br>아래의 **옵션 2**&#x200B;를 참조하세요. | **[!UICONTROL 오디오 트랙 변환]** |
   | **옵션 3** | 캡션 파일(`.vtt`)의 텍스트를 수정하고 다시 업로드하여 이전 `.vtt` 파일을 바꾼 다음 AI가 수정된 파일을 번역하도록 해야 합니다.<br>아래의 **옵션 3**&#x200B;을 참조하세요. | **[!UICONTROL 캡션 번역]** |

   ![캡션 만들기 옵션](/help/assets/dynamic-media/assets/msma-createcaption.png)
   *캡션 만들기 드롭다운 메뉴에는 파일 업로드, 오디오 트랙 변환, 캡션 번역 등 세 가지 옵션이 있습니다.*

+++**옵션 1:** *사용하려는 언어로 된 기존 캡션 파일이 있습니다.*(**[!UICONTROL 파일 업로드]** 옵션)

   1. 페이지 오른쪽 상단 근처에 있는 **[!UICONTROL 캡션 만들기]** > **[!UICONTROL 파일 업로드]**&#x200B;를 클릭합니다.
   1. 기존 `.vtt`개 파일 중 하나 이상으로 이동하여 선택한 다음 엽니다.
   1. 미디어 플레이어에 캡션을 표시하려면 *반드시*&#x200B;업로드하는 *각각* 캡션 파일에 대한 필수 세부 정보를 추가해야 합니다. 캡션 파일 이름 오른쪽에 있는 연필 아이콘을 선택합니다. **캡션 편집** 대화 상자에 파일에 대한 다음 필수 정보를 입력하십시오.

      | 캡션 메타데이터 | 설명 |
      |--- |--- |
      | 파일 이름 | 기본 파일 이름은 원래 파일 이름에서 파생됩니다. 파일 이름은 업로드 중에만 변경할 수 있으며 나중에 변경할 수 없습니다. 파일 이름 문자 요구 사항은 AEM Assets의 요구 사항과 동일합니다.<br>추가 캡션 파일 및 오디오 트랙 파일에 같은 파일 이름을 사용할 수 없습니다. |
      | 언어 | 캡션의 언어를 선택합니다. 캡션 파일이 처리된 후에는 이 언어 필드를 편집할 수 없습니다(흐리게 표시됨). |
      | 유형 | 사용 중인 캡션 유형을 선택합니다.<br>**자막** - 대화 상자를 변환하거나 기록하는 비디오와 함께 표시되는 캡션 텍스트입니다.<br>**캡션** - 캡션 텍스트에는 대화 상자 번역 또는 트랜스크립션과 함께 배경 소음, 스피커 차별화 및 기타 관련 세부 정보가 포함되어 있어 청각 장애가 있거나 난청인 개인의 접근성을 향상시킵니다. |
      | 레이블 | 미디어 플레이어의 **[!UICONTROL 오디오 또는 캡션 선택]** 팝업 목록에서 캡션 이름에 대해 표시되는 텍스트입니다. 레이블은 자막 또는 캡션 트랙에 해당하는 것으로, 고객에게 표시됩니다. 예: `English (CC)` |

      필요한 경우 나중에 캡션 메타데이터를 변경하거나 편집할 수 있습니다. 비디오가 게시되면 이러한 세부 사항이 게시된 비디오의 공개 URL에 반영됩니다.

   1. 페이지의 오른쪽 상단 근처에 있는 **[!UICONTROL 저장 및 닫기]** 드롭다운에서 **[!UICONTROL 저장]**&#x200B;을 클릭합니다. 인터페이스의 **Status** 열에 표시된 대로 파일이 업로드되고 메타데이터 처리가 시작됩니다.

      >[!NOTE]
      >
      >인스턴스의 캐싱 설정에 따라 메타데이터 처리가 미리보기 및 게시된 URL에 반영되기까지 몇 분 정도 걸릴 수 있습니다.

   1. 이전 단계에서 **[!UICONTROL 저장]**&#x200B;을 선택하는 대신 **[!UICONTROL 저장 및 닫기]**&#x200B;를 선택한 경우에도 업로드된 파일의 처리 상태를 볼 수 있습니다. [업로드된 캡션 및 오디오 추적 파일의 주기 상태 보기](#lifecycle-status-video)를 참조하세요.
   1. 8단계로 진행합니다.

+++

+++**옵션 2:** *AI가 여러 언어로 캡션 파일을 생성하기를 원합니다*(**[!UICONTROL 오디오 트랙 변환]** 옵션)

   1. 페이지의 오른쪽 상단 모서리에서 **[!UICONTROL 캡션 만들기]** > **[!UICONTROL 오디오 트랙 변환]**&#x200B;을 클릭합니다.

      ![오디오 트랙 변환 대화 상자](/help/assets/dynamic-media/assets/msma-convertaudiotracks.png)
      *오디오 트랙 변환 대화 상자는 AI를 사용하여 여러 언어로 캡션 파일을 생성합니다.*

   1. **오디오 트랙 변환** 대화 상자에서 다음 옵션을 설정합니다.

      | 옵션 | 설명 |
      |--- |--- |
      | 변환할 오디오 트랙 | 드롭다운 목록에서 AI를 사용하여 캡션을 생성할 업로드된 오디오 트랙 파일을 선택합니다. |
      | 출력 언어 | 드롭다운 목록에서 캡션 파일을 표시할 언어를 하나 이상 선택합니다.<br>선택한 언어를 제거하려면 **X**&#x200B;을 클릭하세요.<br>비디오를 재생하는 동안 여기에서 선택한 순서대로 미디어 플레이어에 언어 목록이 나타납니다. |

   1. **[!UICONTROL 완료]**&#x200B;를 클릭합니다.
   1. 페이지의 오른쪽 상단 근처에 있는 **[!UICONTROL 저장 및 닫기]** 드롭다운에서 **[!UICONTROL 저장]**&#x200B;을 클릭합니다.
   1. **[!UICONTROL 캡션 및 오디오 트랙]** 탭을 다시 클릭합니다. 인터페이스의 **Status** 열에 표시되는 것과 같이 캡션 파일이 하나 이상 만들어지고 처리가 시작됩니다. [업로드된 캡션 및 오디오 추적 파일의 주기 상태 보기](#lifecycle-status-video)도 참조하세요.

      >[!NOTE]
      >
      >인스턴스의 캐싱 설정에 따라 메타데이터 처리가 미리보기 및 게시된 URL에 반영되기까지 몇 분 정도 걸릴 수 있습니다.

   1. (선택 사항) 캡션 파일 이름 오른쪽에 있는 연필 아이콘을 선택합니다. **캡션 편집** 대화 상자에서 파일에 대한 다음 세부 정보를 편집할 수 있습니다.

      | 캡션 메타데이터 | 설명 |
      | --- | --- |
      | 유형 | 사용 중인 캡션 유형을 선택합니다.<br>**자막** - 대화 상자를 변환하거나 기록하는 비디오와 함께 표시되는 캡션 텍스트입니다.<br>**캡션** - 캡션 텍스트에 배경 소리와 스피커 차별화가 포함됩니다. 대화 상자의 번역이나 트랜스크립션과 함께 기타 관련 정보도 포함됩니다. 이러한 접근 방식은 청각장애가 있거나 난청인 개인에게 콘텐츠에 더 쉽게 접근할 수 있도록 한다. |
      | 레이블 | 미디어 플레이어의 **[!UICONTROL 오디오 또는 캡션 선택]** 팝업 목록에서 캡션 이름에 대해 표시되는 텍스트입니다. 레이블은 자막 또는 캡션 트랙에 해당하는 것으로, 고객에게 표시됩니다. 예: `English (CC)` |

      필요한 경우 나중에 특정 캡션 메타데이터를 변경하거나 편집할 수 있습니다. 비디오가 게시되면 이러한 메타데이터 세부 사항이 게시된 비디오의 공개 URL에 반영됩니다.
   1. 8단계로 진행합니다.

+++

+++**옵션 3:** *캡션 파일(`.vtt`)의 텍스트를 수정하고, 다시 업로드하여 이전 `.vtt` 파일을 바꾼 다음 AI가 수정된 파일을 번역하도록 해야 함*(**[!UICONTROL 캡션 번역]** 옵션)

   1. **[!UICONTROL 캡션 만들기]** > **[!UICONTROL 캡션 번역]**&#x200B;을 클릭합니다. 이 옵션은 하나 이상의 캡션 파일이 이미 추가되고 처리된 경우에 사용할 수 있습니다.

      ![캡션 번역 대화 상자](/help/assets/dynamic-media/assets/msma-translate-captions.png)
      *캡션 번역 대화 상자를 통해 기존 캡션 파일을 사용하여 AI가 여러 언어로 새 캡션 파일을 생성하도록 할 수 있습니다.*

   1. **캡션 번역** 대화 상자에서 다음 옵션을 설정합니다.

      | 옵션 | 설명 |
      |--- |--- |
      | 번역할 캡션 | 드롭다운 목록에서 AI를 사용하여 캡션을 생성할 캡션 파일을 선택합니다. |
      | 출력 언어 | 드롭다운 목록에서 캡션 파일을 표시할 언어를 하나 이상 선택합니다.<br>선택한 언어를 제거하려면 **X**&#x200B;을 클릭하세요.<br>비디오를 재생하는 동안 여기에서 선택한 순서대로 미디어 플레이어에 언어 목록이 나타납니다. |

   1. **[!UICONTROL 완료]**&#x200B;를 클릭합니다.
   1. 페이지의 오른쪽 상단 근처에 있는 **[!UICONTROL 저장 및 닫기]** 드롭다운에서 **[!UICONTROL 저장]**&#x200B;을 클릭합니다.
   1. **[!UICONTROL 캡션 및 오디오 트랙]** 탭을 다시 클릭합니다. 인터페이스의 **Status** 열에 표시되는 것과 같이 캡션 파일이 하나 이상 만들어지고 처리가 시작됩니다. [업로드된 캡션 및 오디오 추적 파일의 주기 상태 보기](#lifecycle-status-video)도 참조하세요.

      >[!NOTE]
      >
      >인스턴스의 캐싱 설정에 따라 메타데이터 처리가 미리보기 및 게시된 URL에 반영되기까지 몇 분 정도 걸릴 수 있습니다.

   1. (선택 사항) 캡션 파일 이름 오른쪽에 있는 연필 아이콘을 선택합니다. **캡션 편집** 대화 상자에서 파일에 대한 다음 세부 정보를 편집할 수 있습니다.

      | 캡션 메타데이터 | 설명 |
      | --- | --- |
      | 유형 | 사용 중인 캡션 유형을 선택합니다.<br>**자막** - 대화 상자를 변환하거나 기록하는 비디오와 함께 표시되는 캡션 텍스트입니다.<br>**캡션** - 캡션 텍스트에는 배경 소음, 스피커 차별성도 포함됩니다. 대화 상자의 번역이나 트랜스크립션과 함께 기타 관련 정보도 포함됩니다. 이러한 접근 방식은 청각장애가 있거나 난청인 개인에게 콘텐츠에 더 쉽게 접근할 수 있도록 한다. |
      | 레이블 | 미디어 플레이어의 **[!UICONTROL 오디오 또는 캡션 선택]** 팝업 목록에서 캡션 이름에 대해 표시되는 텍스트입니다. 레이블은 자막 또는 캡션 트랙에 해당하는 것으로, 고객에게 표시됩니다. 예: `English (CC)` |

      필요한 경우 나중에 특정 캡션 메타데이터를 변경하거나 편집할 수 있습니다. 비디오가 게시되면 이러한 메타데이터 세부 사항이 게시된 비디오의 공개 URL에 반영됩니다.

   1. 8단계로 진행합니다.

+++

1. (선택 사항) 게시 전에 비디오를 미리 보고 캡션 및 오디오가 예상대로 작동하는지 확인합니다. [여러 캡션 및 오디오 트랙이 있는 비디오 미리 보기](#preview-video-audio-subtitle)를 참조하세요.
1. Publish 비디오입니다. [Publish 자산](publishing-dynamicmedia-assets.md)을 참조하세요.

#### 이미 게시된 비디오에 캡션 및 오디오 트랙 파일 추가 정보

추가 캡션 또는 오디오 트랙 파일을 게시된 비디오에 업로드한 후 해당 파일은 준비 후 `Processed` 상태가 됩니다. 그런 다음 Dynamic Media에서 비디오를 미리 보고 새 파일을 보거나 들을 수 있습니다.

그러나 미리 보기 후에 새로 추가된 캡션 또는 오디오 트랙 파일도 게시하려면 비디오를 다시 *게시*&#x200B;해야 합니다. 게시 후 캡션 또는 오디오를 공개 Dynamic Media URL에서 사용할 수 있게 됩니다.

>[!NOTE]
>
>인스턴스의 캐싱 설정에 따라 메타데이터 업데이트가 미리보기 및 게시된 URL에 반영되기까지 몇 분 정도 걸릴 수 있습니다.

즉시 게시하도록 Dynamic Media을 구성한 시나리오에서는 추가 캡션 또는 오디오 파일을 업로드하면 캡션 또는 오디오 파일 업로드 후 비디오 게시가 즉시 트리거됩니다.

>[!CAUTION]
>
>게시 또는 게시 취소된 비디오에 캡션 파일 또는 오디오 파일을 업로드할 때 비디오를 [*재처리*](/help/assets/dynamic-media/about-image-video-profiles.md#reprocessing-assets)&#x200B;하면 파일이 삭제됩니다. 비디오의 원본 오디오만 그대로 유지됩니다. 이러한 경우 캡션 파일 및 오디오 트랙 파일을 비디오에 다시 업로드해야 합니다.

#### 기존 URL이 있는 비디오에 캡션 수정자가 있는 여러 캡션 추가

Dynamic Media에서는 URL 수정자를 통해 비디오가 포함된 단일 캡션의 추가를 지원합니다. [비디오에 캡션 추가](#adding-captions-to-video)를 참조하십시오.

여러 캡션 변경 사항은 게시된 비디오에 대한 URL 수정자를 통해 추가된 캡션보다 우선합니다.

**캡션 수정자가 있는 기존 URL이 있는 비디오에 여러 캡션을 추가하려면:**

1. 수정자로 이미 추가된 캡션 파일을 비디오에 업로드하면 파일을 명시적으로 관리할 수 있습니다.
1. 필요에 따라 추가 캡션 파일을 업로드합니다.
1. 평소대로 비디오를 Publish 합니다.
이제 캡션 수정자가 있는 기존 URL에서 여러 캡션을 로드할 수 있습니다.

### 업로드된 캡션 및 오디오 추적 파일의 라이프사이클 상태 보기 {#lifecycle-status-video}

기본 비디오에 업로드된 모든 캡션 또는 오디오 트랙 파일의 라이프사이클 상태를 관찰할 수 있습니다. **속성**&#x200B;의 **캡션 및 오디오 트랙** 탭에서 수행할 수 있습니다.

**비디오의 라이프사이클 상태를 보려면:**

1. 라이프사이클 상태를 보려는 비디오 자산으로 이동합니다.
1. 에셋 선택 모드의 목록 보기 또는 카드 보기에서 비디오 에셋을 선택합니다.
1. 도구 모음에서 속성 아이콘(안에 &quot;i&quot;가 있는 원)을 선택합니다.
1. 속성 페이지에서 **[!UICONTROL 캡션 및 오디오 트랙]** 탭을 선택합니다. 상태 열에서 각 캡션 또는 오디오 파일의 상태를 확인합니다.

| 캡션 또는 오디오 추적 상태 | 설명 |
| --- | --- |
| 처리 중 | 새 캡션 또는 오디오 트랙 파일을 추가하고 저장하면 &quot;처리 중&quot; 상태가 됩니다. Dynamic Media은 스트리밍 매니페스트를 기본 비디오에 연결하여 파일을 처리합니다. |
| 처리됨 | 처리가 완료되면 캡션 또는 오디오 트랙 파일 또는 기본 비디오와 연결된 원본 오디오 트랙이 &quot;처리됨&quot; 상태로 나타납니다. 비디오를 라이브로 게시하는 *이전*&#x200B;에 &quot;처리됨&quot;으로 표시되는 캡션 및 오디오 트랙 파일을 미리 볼 수 있습니다. |
| 게시됨 | &quot;게시됨&quot; 상태는 기본 비디오에 대해 &quot;게시됨&quot;과 유사한 상태를 나타냅니다. Assets은 기본 비디오가 게시될 때 게시되며 공개 Dynamic Media URL에서 사용할 수 있습니다. |
| 실패 | &quot;실패&quot; 상태는 캡션 또는 오디오 트랙 파일 처리가 완료되지 않았음을 의미합니다. 캡션 또는 오디오 트랙 파일을 삭제하고 다시 업로드하십시오. |
| 게시 취소됨 | 게시된 기본 비디오가 명시적으로 게시 취소되면 비디오에 추가한 캡션 또는 오디오 트랙 파일도 게시 취소됩니다. |

![캡션 및 오디오 트랙 필드에 강조 표시된 상태 열입니다.](/help/assets/dynamic-media/assets/msma-lifecycle-status.png)*업로드된 각 캡션 및 오디오 추적 파일의 주기 상태입니다.*

### 여러 오디오 트랙이 있는 비디오의 기본 오디오 설정

기본적으로 비디오의 원본 오디오가 재생되는 기본 오디오로 설정됩니다.

그러나 업로드된 모든 오디오 트랙 파일은 비디오가 뷰어에 로드된 후 재생할 기본 오디오로 설정할 수 있습니다. 속성 사용자 인터페이스의 **캡션 및 오디오 트랙** 탭에서 `Default` 레이블이 비디오 재생을 위한 오디오 트랙 파일의 오른쪽에 적용됩니다.

>[!NOTE]
>
>기본 오디오 재생은 다음 브라우저에 설정된 내용에 따라 달라질 수 있습니다.
>
>* Chrome - 비디오에 설정된 기본 오디오가 재생됩니다.
>* Safari - Safari에 기본 언어가 설정되어 있으면, 비디오의 매니페스트와 함께 사용할 수 있는 경우 설정된 기본 언어로 오디오가 재생됩니다. 그렇지 않으면 비디오 속성의 일부로 설정된 기본 오디오가 재생됩니다.

**오디오 트랙이 여러 개인 비디오의 기본 오디오를 설정하려면:**

1. 기본 오디오 트랙을 설정할 비디오 자산으로 이동합니다.
1. 에셋 선택 모드의 목록 보기 또는 카드 보기에서 비디오 에셋을 선택합니다.
1. 도구 모음에서 속성 아이콘(안에 &quot;i&quot;가 있는 원)을 선택합니다.
1. 속성 페이지에서 **[!UICONTROL 캡션 및 오디오 트랙]** 탭을 선택합니다.
1. **오디오 트랙** 제목 아래에서 비디오의 기본값으로 설정할 오디오 트랙 파일을 선택합니다.
1. **[!UICONTROL 기본값으로 설정]**을 선택합니다.
**기본값으로 설정** 대화 상자에서 **[!UICONTROL 바꾸기]**&#x200B;를 선택합니다.

   ![선택한 오디오 트랙 파일 이름이 있고 &quot;기본값으로 설정&quot; 단추가 강조 표시된 오디오 트랙 머리글입니다.](/help/assets/dynamic-media/assets/msma-defaultaudiotrack.png)*비디오에 대한 기본 오디오 트랙을 설정하는 중입니다.*

1. 오른쪽 상단 모서리에서 **[!UICONTROL 저장 및 닫기]**&#x200B;를 선택합니다.
1. Publish 비디오입니다. [Publish 자산](publishing-dynamicmedia-assets.md)을 참조하세요.

### 여러 캡션 및 오디오 트랙이 있는 비디오 미리 보기 {#preview-video-audio-subtitle}

캡션 파일 및 오디오 트랙 파일이 비디오에 업로드되고 처리된 후 Dynamic Media 비디오 뷰어를 사용하여 다른 모든 트랙을 미리 볼 수 있습니다. 이렇게 하면 비디오가 고객에게 어떤 모습과 소리로 들리는지 확인하고 예상대로 작동하는지 확인하는 데 도움이 됩니다.

비디오가 만족스러우면 다음 방법 중 하나를 사용하여 [게시](publishing-dynamicmedia-assets.md)할 수 있습니다.

[웹 페이지에 비디오 또는 이미지 뷰어 포함](/help/assets/dynamic-media/embed-code.md)을 참조하십시오.
[웹 응용 프로그램에 URL 연결](/help/assets/dynamic-media/linking-urls-to-yourwebapplication.md)을 참조하십시오. 대화형 콘텐츠에 상대 URL이 있는 링크, 특히 Experience Manager Sites 페이지에 대한 링크가 있는 경우에는 URL 기반 연결 방법이 불가능합니다.
[페이지에 Dynamic Media Assets 추가](/help/assets/dynamic-media/adding-dynamic-media-assets-to-pages.md)를 참조하십시오.

>[!NOTE]
>
>기본 Experience Manager 미리 보기 탭에는 여러 캡션 및 오디오 트랙이 표시되지 않습니다. 그 이유는 해당 트랙이 Dynamic Media과 연결되어 있으며 Dynamic Media 뷰어 미리 보기를 통해서만 볼 수 있기 때문입니다.

**여러 캡션 및 오디오 트랙이 있는 비디오를 미리 보려면:**

1. **[!UICONTROL Assets]**&#x200B;에서 여러 캡션 및 오디오 트랙을 추가한 기존 비디오로 이동합니다.
1. 비디오 자산을 미리보기 모드에서 열 수 있도록 클릭합니다.
1. 미리 보기 페이지에서 페이지의 왼쪽 상단 근처에 있는 드롭다운 목록을 선택한 다음 **[!UICONTROL 뷰어]**&#x200B;를 선택합니다.

   ![뷰어 옵션을 표시하는 드롭다운 목록입니다.](/help/assets/dynamic-media/assets/msma-selectviewers.png)

1. 뷰어 목록에서 비디오 미리 보기에 사용할 뷰어를 선택합니다. 예를 들어, 다음 스크린샷은 **[!UICONTROL 비디오]** 뷰어가 선택되어 있는 것을 보여 줍니다.

   ![뷰어 드롭다운 목록에서 비디오 뷰어를 선택합니다.](/help/assets/dynamic-media/assets/msma-dmviewerselected.png)

1. 오른쪽 하단 모서리 근처에서 볼륨 아이콘 왼쪽에 있는 말풍선 아이콘을 선택한 다음 들으려는 오디오나 캡션을 선택하거나 또는 둘 다 표시합니다. 필요한 경우 캡션 아래에서 **[!UICONTROL 끄기]**&#x200B;를 클릭하여 캡션 표시를 비활성화할 수 있습니다.

   ![비디오 뷰어의 오디오 및 캡션 팝업 목록입니다.](/help/assets/dynamic-media/assets/msma-selectaudiosubtitle.png)*비디오 재생을 위한 오디오 및 캡션을 선택하는 사용자의 시뮬레이션.*

1. 재생을 시작하려면 비디오의 **[!UICONTROL 재생]** 단추를 선택하십시오.
왼쪽 아래에 있는 **[!UICONTROL URL]** 및 **[!UICONTROL 포함]** 단추를 참고하십시오. 이 단추를 사용하여 각각 [비디오의 URL을 웹 응용 프로그램에 연결](/help/assets/dynamic-media/linking-urls-to-yourwebapplication.md)하거나 [비디오를 웹 페이지에 포함](/help/assets/dynamic-media/embed-code.md)합니다.
1. 미리 보기 페이지의 오른쪽 상단 모서리에서 **[!UICONTROL 닫기]**&#x200B;를 선택합니다.

### 비디오에서 캡션 또는 오디오 트랙 파일 삭제

비디오에서 캡션 또는 오디오 트랙 파일을 삭제할 수 있습니다. 게시된 캡션 또는 오디오 트랙 파일의 삭제는 비디오의 게시된 URL에 자동으로 반영됩니다.

기본 비디오에서 추출한 원본 오디오 트랙은 삭제할 수 없습니다.

**비디오에서 캡션 또는 오디오 트랙 파일을 삭제하려면:**

1. 기본 오디오 트랙을 설정할 비디오 자산으로 이동합니다.
1. 에셋 선택 모드의 목록 보기 또는 카드 보기에서 비디오 에셋을 선택합니다.
1. 도구 모음에서 속성 아이콘(안에 &quot;i&quot;가 있는 원)을 선택합니다.
1. 속성 페이지에서 **[!UICONTROL 캡션 및 오디오 트랙]** 탭을 선택합니다.
1. 다음 중 하나를 수행합니다.

   * 캡션 - **캡션** 제목 아래에서 비디오에서 삭제할 캡션 파일을 하나 이상 선택한 다음 **[!UICONTROL 삭제]**&#x200B;를 클릭합니다.
   * 오디오 트랙 - **오디오 트랙** 제목 아래에서 비디오에서 삭제할 오디오 트랙 파일을 하나 이상 선택한 다음 **[!UICONTROL 삭제]**&#x200B;를 클릭합니다.

1. 삭제 대화 상자에서 **[!UICONTROL 확인]**&#x200B;을 클릭합니다.
1. Publish 비디오입니다.

### 비디오에 업로드된 캡션 또는 오디오 트랙 파일 다운로드

비디오용으로 업로드한 모든 캡션 또는 오디오 트랙 파일을 다운로드할 수 있습니다. 선택한 모든 파일을 `.zip`(으)로 다운로드하거나 각 파일에 대해 별도의 다운로드 폴더를 만들 수 있습니다.

기본 비디오 파일에서 추출한 원본 오디오 트랙을 다운로드할 수 없습니다.

**사용 사례:** `.vtt` 파일에서 오류가 발견되면 캡션 파일을 다운로드해야 합니다. 잘못된 `.vtt` 파일을 다운로드하여 일반 텍스트 편집기에서 열고 수정하기만 하면 됩니다. `.vtt` 파일을 저장한 후 다시 업로드하십시오. 그런 다음 **[!UICONTROL 캡션 번역]** 옵션을 사용하여 수정된 `.vtt` 파일을 다시 번역합니다.

**비디오에 업로드된 캡션 또는 오디오 트랙 파일을 다운로드하려면:**

1. 기본 오디오 트랙을 설정할 비디오 자산으로 이동합니다.
1. 에셋 선택 모드의 목록 보기 또는 카드 보기에서 비디오 에셋을 선택합니다.
1. 도구 모음에서 속성 아이콘(안에 &quot;i&quot;가 있는 원)을 선택합니다.
1. 속성 페이지에서 **[!UICONTROL 캡션 및 오디오 트랙]** 탭을 선택합니다.
1. 다음 중 하나를 수행합니다.

   * 캡션 - **캡션** 제목 아래에서 비디오에서 다운로드할 캡션 파일을 하나 이상 선택한 다음 **[!UICONTROL 다운로드]**&#x200B;를 선택합니다.
   * 오디오 트랙 - **오디오 트랙** 제목 아래에서 비디오에서 다운로드할 오디오 트랙 파일을 하나 이상 선택한 다음 **[!UICONTROL 다운로드]**&#x200B;를 선택합니다.

1. 다운로드 대화 상자에서 다음 옵션을 설정합니다.

   | 옵션 | 설명 |
   |--- |--- |
   | 다른 이름으로 저장 | 다른 이름으로 저장 텍스트 필드에 지정된 기본 파일 이름을 사용하거나 고유한 이름을 지정합니다. |
   | 각 에셋에 대해 별도의 폴더 만들기 | 다운로드하도록 선택한 각 캡션 파일 또는 오디오 트랙 파일에 대한 폴더를 만듭니다. |
   | 이메일 | 기본 이메일 프로그램을 사용하여 .zip 파일을 지정된 이메일 주소로 전송합니다. |
   | 자산 | 다운로드하는 파일의 수와 선택한 모든 파일의 전체 크기를 지정합니다. 이 옵션을 선택 해제하면 **[!UICONTROL 다운로드]** 버튼이 흐려지고 꺼져서 파일을 다운로드할 수 없습니다. |

1. **[!UICONTROL 다운로드]**&#x200B;를 선택합니다.
1. Publish 비디오입니다. [Publish 자산](publishing-dynamicmedia-assets.md)을 참조하세요.

<!-- ## About AI-generated captions for videos in Dynamic Media

AI-powered captions in Dynamic Media are designed to enhance video accessibility and engagement by automatically generating accurate and synchronized subtitles. This technology uses advanced AI algorithms to transcribe spoken content into text, which is then displayed as captions on the video. Here are some key features.

* **Automatic Transcription:** The AI system transcribes spoken words from an existing audio file into text in real-time, ensuring that captions are generated quickly and accurately.
* **Multilingual Support:** It supports more than 60 languages, making it easier to reach a global audience. You can even translate your existing captions to different languages.
* **Enhanced Accessibility:** By providing captions, videos become more accessible to viewers who are deaf or hard of hearing, as well as those who prefer to watch videos with the sound off.
* **Improved Engagement:** Captions can help retain viewer attention and improve comprehension, especially in noisy environments or when the viewer's native language is different from the video's language.

These features in Dynamic Media make AI-powered video aptions a valuable tool for content creators looking to enhance their video content's accessibility and engagement. -->

## 비디오에 폐쇄 캡션 추가 {#adding-captions-to-video}

>[!IMPORTANT]
>
>Adobe은 Dynamic Media 계정에서 [여러 캡션 및 오디오 추적 기능을 활성화](#enable-dash)할 것을 권장합니다. 이렇게 하면 최신 Dynamic Media 백엔드 아키텍처와 캡션, 캡션 및 오디오 트랙을 비디오에 추가하는 간소화된 워크플로우를 활용할 수 있습니다.

단일 비디오 또는 응용 비디오 세트에 자막 기능을 추가하여 비디오를 글로벌 시장으로 확장할 수 있습니다. 폐쇄 캡션을 추가하면 오디오를 더빙하거나 원어민을 사용하여 각 언어의 오디오를 다시 녹음할 필요가 없습니다. 이 비디오는 녹화된 언어로 재생됩니다. 외국어 캡션이 표시되므로 다른 언어를 사용하는 사람도 오디오 부분을 이해할 수 있습니다.

또한 자막 기능을 통해 귀가 들리지 않거나 난청인 사람의 접근성을 높일 수 있습니다.

>[!NOTE]
>
>사용하는 비디오 플레이어는 폐쇄 캡션 표시를 지원해야 합니다.

[Dynamic Media의 접근성](/help/assets/dynamic-media/accessibility-dm.md)도 참조하세요.

Dynamic Media은 캡션 파일을 JSON(JavaScript 개체 표기법) 형식으로 변환할 수 있습니다. 이 전환은 JSON 텍스트를 웹 페이지에 숨김이나 비디오의 전체 트랜스크립트로 포함할 수 있음을 의미합니다. 그런 다음 검색 엔진은 콘텐츠를 크롤링/색인화하여 비디오를 보다 쉽게 검색하고 고객에게 비디오 콘텐츠에 대한 자세한 내용을 제공할 수 있습니다.

URL에서 JSON 함수를 사용하는 방법에 대한 자세한 내용은 [정적(이미지가 아닌) 콘텐츠 제공](https://experienceleague.adobe.com/en/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/c-serving-static-nonimage-contents#image-serving-api)을 참조하십시오.

**비디오에 캡션을 추가하려면:**

1. 서드파티 애플리케이션 또는 서비스를 사용하여 비디오 캡션 파일을 만듭니다.

   만드는 파일이 WebVTT(Web Video Text Track) 표준을 따르는지 확인합니다. 캡션 파일 이름 확장명은 `.vtt`입니다. WebVTT 캡션 표준에 대한 자세한 내용을 볼 수 있습니다.

   [WebVTT: 웹 비디오 텍스트 트랙 형식](https://w3c.github.io/webvtt/)을 참조하세요.

   Dynamic Media 외부에서 WebVTT 캡션 파일을 작성하는 데 사용할 수 있는 무료 및 고급 도구와 서비스를 모두 제공하는 많은 웹 사이트가 있습니다. <!-- THE FOLLOWING LINK IS NO LONGER LIVE. CHECKED DECEMBER 13, 2023 For example, to create a simple video caption file with no styling, you can use the following free online caption authoring and editing tool: -->

   <!-- [WebVTT Caption Maker](https://testdrive-archive.azurewebsites.net/Graphics/CaptionMaker/Default.html)

   For best results, use the tool in Internet Explorer 9 or above, Google Chrome, or Safari.

   In the tool, in the **[!UICONTROL Enter URL of video file]** field, paste the copied URL of your video file and then select **[!UICONTROL Load]**. See [Obtain a URL for an Asset](/help/assets/dynamic-media/linking-urls-to-yourwebapplication.md#obtaining-a-url-for-an-asset) to get the URL to the video file itself which you can then paste into the **[!UICONTROL Enter URL of video file field]**. Internet Explorer, Chrome, or Safari can then natively play back the video.-->

사이트의 화면 지침을 따라 WebVTT 파일을 작성하고 저장합니다. 완료되면 캡션 파일 내용을 복사하여 일반 텍스트 편집기에 붙여넣고 VTT 파일 확장명으로 저장합니다.

>[!NOTE]
>
>여러 언어로 비디오 캡션을 전체적으로 지원하려면 WebVTT 표준을 사용하려면 지원하려는 각 언어에 대해 별도의 `.vtt`개의 파일 및 호출을 만들어야 합니다.

일반적으로 캡션 `.vtt` 파일의 이름을 비디오 파일과 같은 이름으로 지정하고 언어 로케일(예: -EN, -FR 또는 -DE)과 함께 추가합니다. 이렇게 하면 기존 WCM 시스템을 사용하여 비디오 URL 생성을 자동화하는 데 도움이 될 수 있습니다.

1. Experience Manager에서 WebVTT 캡션 파일을 DAM에 업로드합니다.
1. 업로드한 캡션 파일과 연결하려면 *게시됨* 비디오 자산으로 이동합니다.

   Remember that URLs are only available to copy *after* you have first *published* the assets.

   [Publish 자산](/help/assets/dynamic-media/publishing-dynamicmedia-assets.md)을 참조하세요.

1. 다음 중 하나를 수행하십시오.

   * 팝업 비디오 뷰어 환경을 보려면 **[!UICONTROL URL]** 단추를 클릭하십시오. URL 대화 상자에서 을 선택하고 URL을 클립보드로 복사한 다음 URL을 지나 단순 텍스트 편집기로 이동합니다. 복사한 비디오의 URL을 다음 구문과 함께 추가합니다.

     `&caption=<server_path>/is/content/<path_to_caption.vtt_file,1>`

     캡션 경로의 끝에 `,1`을(를) 메모하십시오. 경로에서 VTT 파일 이름 확장자 바로 다음에 있는 `,1` 또는 `,0`(으)로 각각 설정하여 비디오 플레이어 막대에서 자막 버튼을 선택적으로 활성화(켜기)하거나 비활성화(끄기)할 수 있습니다.

   * 포함된 비디오 뷰어 환경을 보려면 **[!UICONTROL 포함 코드]**&#x200B;를 선택하세요. 포함 코드 대화 상자에서 을 선택하고 포함 코드를 클립보드에 복사한 다음 코드를 간단한 텍스트 편집기에 붙여넣습니다. 복사된 포함 코드를 다음 구문과 함께 추가합니다.

     `videoViewer.setParam("caption","<path_to_caption.vtt_file,1>");`

     캡션 경로의 끝에 `,1`을(를) 메모하십시오. 경로에서 VTT 파일 이름 확장자 바로 다음에 있는 `,1` 또는 `,0`(으)로 각각 설정하여 비디오 플레이어 막대에서 자막 버튼을 선택적으로 활성화(켜기)하거나 비활성화(끄기)할 수 있습니다.

## 비디오에 챕터 마커 추가 {#adding-chapter-markers-to-video}

장 마커를 단일 비디오나 응용 비디오 세트에 추가하여 긴 형식의 비디오를 더 쉽게 보고 탐색할 수 있습니다. 사용자가 비디오를 재생할 때 비디오 타임라인에서 챕터 마커를 선택할 수 있습니다(비디오 스크러버라고도 함). 관심 영역으로 쉽게 이동하거나 새로운 콘텐츠, 교육 및 데모에 바로 이동할 수 있습니다.

>[!NOTE]
>
>사용되는 비디오 플레이어는 챕터 마커 사용을 지원해야 합니다. Dynamic Media 비디오 플레이어는 챕터 마커를 지원하지만 서드파티 비디오 플레이어를 사용하면 지원하지 않을 수 있습니다.

<!-- OBSOLETE CONTENT OBSOLETE CONTENT If desired, you can create and brand your own custom video viewer with chapters instead of using a video viewer preset. For instructions on creating your own HTML5 viewer with chapter navigation, in the Adobe Scene7 Viewer SDK for HTML5 guide, reference the heading "Customizing Behavior Using Modifiers" under the classes `s7sdk.video.VideoPlayer` and `s7sdk.video.VideoScrubber`. The Adobe Scene7 Viewer SDK is available as a download from [Adobe Developer Connection](https://help.adobe.com/en_US/scene7/using/WSef8d5860223939e2-43dedf7012b792fc1d5-8000.html). -->

캡션을 만드는 것과 같은 방법으로 비디오에 대한 챕터 목록을 만듭니다. 즉, WebVTT 파일을 만듭니다. 그러나 이 파일은 WebVTT 캡션 파일과 별개여야 합니다. 캡션과 챕터를 하나의 WebVTT 파일로 결합할 수 없습니다.

다음 샘플을 장 탐색으로 WebVTT 파일을 만드는 데 사용하는 형식의 예로 사용할 수 있습니다.

### 비디오 챕터 탐색이 있는 WebVTT 파일 {#webvtt-file-with-video-chapter-navigation}

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

위의 예에서 `Chapter 1`은(는) 큐 식별자이며 선택 사항입니다. `00:00:000 --> 01:04:364`의 큐 시간은 챕터의 시작 시간과 종료 시간을 `00:00:000` 형식으로 지정합니다. 마지막 세 자릿수는 밀리초이며 선호하는 경우 `000`(으)로 남길 수 있습니다. `The bicycle store behind it all`의 챕터 제목은 챕터 내용에 대한 실제 설명입니다. 사용자가 타임라인의 시각적 큐 포인트 위에 마우스 포인터를 놓으면 큐 식별자, 시작 큐 시간 및 챕터 제목이 모두 비디오 플레이어의 팝업에 나타납니다.

HTML5 비디오 뷰어를 사용하고 있으므로, 만든 챕터 파일이 WebVTT(Web Video Text Tracks) 표준을 따르는지 확인하십시오. 챕터 파일 이름 확장명은 `.vtt`입니다. WebVTT 캡션 표준에 대한 자세한 내용을 볼 수 있습니다.

[WebVTT: 웹 비디오 텍스트 트랙 형식](https://w3c.github.io/webvtt/)을 참조하세요.

**비디오에 챕터 마커를 추가하려면:**

1. 챕터 제목 텍스트에서 문자 렌디션에 문제가 발생하지 않도록 `.vtt` 파일을 UTF8 인코딩으로 저장합니다.

   일반적으로 챕터 VTT 파일의 이름을 비디오 파일과 같은 이름으로 지정하고 챕터와 함께 추가합니다. 이렇게 하면 기존 WCM 시스템을 사용하여 비디오 URL 생성을 자동화하는 데 도움이 될 수 있습니다.
1. Experience Manager에서 WebVTT 챕터 파일을 업로드합니다.

   [자산 업로드](/help/assets/manage-digital-assets.md#uploading-assets)를 참조하세요.

1. 다음 중 하나를 수행하십시오.

   <table>
     <tbody>
      <tr>
       <td>팝업 비디오 뷰어 환경을 위해</td>
       <td>
       <ol>
       <li>업로드한 챕터 파일과 연결하려면 <i>게시된 </i>비디오 자산으로 이동합니다. Remember that URLs are only available to copy <i>after</i> you have first <i>published</i> the assets. <a href="/help/assets/dynamic-media/publishing-dynamicmedia-assets.md">Assets 게시</a>를 참조하십시오.</li>
       <li>드롭다운 메뉴에서 <strong>뷰어</strong>을(를) 선택합니다.</li>
       <li>왼쪽 레일에서 비디오 뷰어 사전 설정 이름을 선택합니다. 비디오 미리보기가 별도의 페이지로 열립니다.</li>
       <li>왼쪽 레일의 하단에서 <strong>URL</strong> 단추를 클릭합니다.</li>
       <li>URL 대화 상자에서 을 선택하고 URL을 클립보드에 복사한 다음 URL을 지나 단순 텍스트 편집기로 이동합니다.</li>
       <li>복사한 비디오의 URL을 장 파일에 복사한 URL과 연결할 수 있도록 다음 구문을 추가합니다.<br /> <br /> <code>&navigation=<<i>full_copied_URL_path_to_chapter_file</i>.vtt></code><br /> </li>
       </ol> </td>
      </tr>
      <tr>
       <td>포함된 비디오 뷰어 환경의 경우 <br /> </td>
       <td>
       <ol>
       <li>업로드한 챕터 파일과 연결하려면 <i>게시된 </i>비디오 자산으로 이동합니다. Remember that URLs are only available to copy <i>after</i> you have first <i>published</i> the assets. <a href="/help/assets/dynamic-media/publishing-dynamicmedia-assets.md">Assets 게시</a>를 참조하십시오.</li>
       <li>드롭다운 메뉴에서 <strong>뷰어</strong>을(를) 선택합니다.</li>
       <li>왼쪽 레일에서 비디오 뷰어 사전 설정 이름을 선택합니다. 비디오 미리보기가 별도의 페이지로 열립니다.</li>
       <li>왼쪽 레일의 하단에서 <strong>포함</strong>을 선택합니다.</li>
       <li>[코드 포함] 대화 상자에서 을 선택하고 전체 코드를 클립보드에 복사한 다음 단순 텍스트 편집기에 붙여넣습니다.</li>
       <li>비디오의 포함 코드를 다음 구문과 함께 추가하면 복사한 URL을 챕터 파일에 연결할 수 있습니다.<br /> <br /> <code>videoViewer.setParam("navigation","&lt;<i>full_copied_URL_path_to_chapter_file</i>.vtt>"</code></li>
       </ol> </td>
      </tr>
     </tbody>
   </table>



## 비디오 썸네일 기본 정보 {#about-video-thumbnails}

비디오 썸네일은 고객에게 비디오를 나타내는 이미지 에셋 또는 비디오 프레임의 축소된 버전입니다. 썸네일은 고객이 비디오를 선택하도록 유도하는 역할을 해야 합니다.

Experience Manager의 모든 비디오에는 연결된 썸네일이 있어야 합니다. 기본적으로 Experience Manager에 비디오를 업로드할 때 첫 번째 프레임이 썸네일로 사용됩니다. 그러나 브랜딩 목적이나 시각적 검색을 위해 썸네일을 사용자 지정할 수 있습니다. 비디오 썸네일을 사용자 지정하면 비디오를 재생하고 사용할 프레임에서 일시 정지할 수 있습니다. 또는 이미 업로드하고 Digital Asset Manager에서 *게시*&#x200B;한 이미지 자산을 선택할 수 있습니다.

비디오에 대한 썸네일을 변경하면 비디오를 다시 처리할 때 Asset compute 서비스를 통해 썸네일 생성이 건너뜁니다.

비디오 축소판을 사용자 지정하는 기능은 비디오가 있는 폴더에 비디오 프로필을 적용한 후에만 사용할 수 있습니다.

### 사용자 지정 비디오 썸네일 추가 {#adding-a-custom-video-thumbnail}

1. 다음을 이미 수행했는지 확인합니다.

   * 비디오 자산에 대한 폴더를 만들었습니다.
   * [폴더에 비디오 프로필을 적용함](/help/assets/dynamic-media/video-profiles.md#applying-a-video-profile-to-folders).

   * [비디오를 폴더에 업로드했습니다](/help/assets/manage-video-assets.md#upload-and-preview-video-assets).

1. 썸네일 이미지를 변경하고자 하는 업로드된 비디오 자산으로 이동합니다.
1. 자산 선택 모드에서 **[!UICONTROL 목록 보기]** 또는 **[!UICONTROL 카드 보기]**&#x200B;에서 비디오 자산을 선택합니다.
1. 도구 모음에서 **[!UICONTROL 속성]** 아이콘(안에 &quot;i&quot;가 있는 원)을 선택합니다.
1. 비디오의 속성 페이지에서 **[!UICONTROL 썸네일 변경]**&#x200B;을 선택합니다.
1. 썸네일 변경 페이지에서 다음 중 하나를 수행합니다.

   * 비디오의 프레임을 새 썸네일로 사용하려면 다음 작업을 수행하십시오.

      * 도구 모음에서 **[!UICONTROL 비디오에서 프레임 선택]** 옵션을 클릭합니다.
      * 재생 버튼을 선택한 다음 비디오의 새 썸네일로 캡처할 프레임에서 일시 중지 버튼을 선택합니다.

   * 이미지 자산을 새 썸네일로 사용하려면 다음을 수행하십시오.

      * 도구 모음에서 **[!UICONTROL Assets에서 썸네일 선택]**&#x200B;을 선택합니다.
      * **[!UICONTROL 썸네일 선택]**&#x200B;을 선택합니다.
      * 사용할 이전에 업로드되고 게시된 이미지 자산으로 이동합니다. 에셋의 크기가 자동으로 조정되어 비디오의 썸네일 이미지로 사용됩니다.
      * 이미지 자산을 선택한 다음 **[!UICONTROL 선택]**&#x200B;을 선택합니다.

1. 썸네일 변경 페이지에서 **[!UICONTROL 변경 내용 저장]**&#x200B;을 선택합니다.
1. 비디오의 속성 페이지의 오른쪽 상단 모서리에서 **[!UICONTROL 저장 및 닫기]**&#x200B;를 선택합니다.



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

   If you configured new default time intervals, or you uploaded a new video to replace the existing video, you need to have Dynamic Media regenerate the thumbnails.

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

1. On the lower-right panel, in the Properties tab, double-select `thumbnailtime`.
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

## Dynamic Media 자산에 대한 Dynamic Media URL 변경

기본 뷰어는 Dynamic Media에서 처리된 비디오를 재생할 수 있습니다. 매니페스트 URL에 직접 액세스하고 사용자 지정 뷰어를 사용하여 재생할 수도 있습니다. 다음은 비디오에 대한 매니페스트 URL을 가져오기 위한 API입니다.

### getVideoManifestURI API 정보

`getVideoManifestURI`API는 c`q-scene7-api:com.day.cq.dam.scene7.api`을(를) 통해 노출되며 다음 매니페스트 URL을 생성하는 데 사용할 수 있습니다.

```java
/**   
* Returns the manifest url for videos 
* @param resource video resource 
* @param manifestType type of video streaming manifest being requested 
* @param onlyIfPublished return a manifest only if the video is published 
* @return the manifest url for videos 
* 
* @throws Exception 
*/
@Nullable 
String getVideoManifestURI(Resource resource, ManifestType manifestType, boolean onlyIfPublished) throws Exception;
```

#### getVideoManifestURI API 매개 변수

이 API는 다음 세 가지 매개 변수를 사용합니다.

| 매개변수 | 설명 |
| --- | --- |
| `resource` | Dynamic Media이 수집한 비디오에 해당하는 리소스입니다. |
| `manifestType` | `ManifestType.DASH` 또는 `ManifestType.HLS`일 수 있습니다. |
| `onlyIfPublished` | 매니페스트 URI가 게시 및 게재 계층에서 사용할 수 있는 경우에만 생성되는 경우 true로 설정합니다. |

위의 메서드를 사용하여 비디오에 대한 매니페스트 URL을 가져오려면 [비디오 인코딩 프로필](/help/assets/dynamic-media/video-profiles.md#creating-a-video-encoding-profile-for-adaptive-streaming)을 &quot;비디오 업로드&quot; 폴더에 추가하십시오. Dynamic Media은 폴더에 할당된 비디오 인코딩 파일에 있는 인코딩을 기반으로 이러한 비디오를 처리합니다. 이제 업로드된 비디오에 대한 매니페스트 URL을 가져오기 위해 위의 API를 호출할 수 있습니다.

### 오류 시나리오

오류가 있으면 API가 null을 반환합니다. 예외는 Experience Manager 오류 로그에 기록됩니다. 이렇게 기록된 모든 오류는 `Could not generate Video Manifest URI`(으)로 시작됩니다. 다음 시나리오에서 이러한 오류가 발생할 수 있습니다.

* `IllegalArgumentException`이(가) 다음 중 하나에 대해 기록됩니다.

   * 전달된 `resource` 매개 변수가 null입니다.
   * 전달된 `resource` 매개 변수가 비디오가 아닙니다.
   * 전달된 `manifestType` 매개 변수가 null입니다.
   * `onlyIfPublished` 매개 변수는 true로 전달되지만 비디오가 게시되지 않습니다.
   * Dynamic Media의 응용 비디오 세트를 사용하여 비디오가 수집되지 않았습니다.

* Dynamic Media에 연결하는 데 문제가 있으면 `IOException`이(가) 기록됩니다.
* 비디오가 DASH 형식을 사용하여 처리되지 않은 동안 전달된 `manifestType` 매개 변수가 `ManifestType.DASH`이면 `UnsupportedOperationException`이(가) 기록됩니다.

<!-- THE REMAINING SECTION IS FOR 6.5 ONLY 

The following is an example of the above API using servlets written in *HTTPWhiteBoard* specification. Select each tab for the code syntax.

>[!BEGINTABS]

>[!TAB Add dependency in pom.xml]

+++**Add dependency in pom.xml** 

```java
dependency> 
     <groupId>com.day.cq.dam</groupId> 
     <artifactId>cq-scene7-api</artifactId> 
     <version>5.12.64</version> 
     <scope>provided</scope> 
</dependency> 
```

+++

>[!TAB Sample servlet]

+++**Sample servlet** 

```java
@Component
        service = Servlet.class 
) 
@HttpWhiteboardServletPattern(value = ManifestServlet.SERVLET_PATTERN) 
@HttpWhiteboardContextSelect(value = Constants.SERVLET_CONTEXT_SELECTOR) 
public class ManifestServlet extends HttpServlet { 

   private static final Logger LOGGER = LoggerFactory.getLogger(ManifestServlet.class); 

   private final ObjectMapper objectMapper; 

    @Reference 
    private Scene7Service scene7Service; 

   public static final String SERVLET_PATTERN = Constants.VIDEO_API_PREFIX + "/manifestUrl"; 

   public ManifestServlet() {
         this.objectMapper = new ObjectMapper(); 
         objectMapper.setSerializationInclusion(JsonInclude.Include.NON_NULL); 
   }

   @Override 

   protected void doGet(HttpServletRequest request, HttpServletResponse response) throws IOException {
        final ResourceResolver resolver = getResourceResolver(request); 
        String assetPath = request.getParameter("assetPath"); 
        String manifest = request.getParameter("manifestType"); 
        String onlyIfPublished = request.getParameter("onlyIfPublished"); 
        Resource resource = resolver.getResource(assetPath); 
        response.setCharacterEncoding(StandardCharsets.UTF_8.toString()); 
        response.setContentType("application/json"); 
        if(resource == null) { 
            LOGGER.info("could not retrieve the resource from JCR"); 
            error("could not retrieve the resource from JCR", response); 
            return; 
        }

        String manifestUri = null; 

        try{ 
            ManifestType manifestType =  ManifestType.DASH; 
            if(manifest != null) { 
                manifestType = ManifestType.valueOf(manifest); 
            } 
            manifestUri = scene7Service.getVideoManifestURI(resource, manifestType, onlyIfPublished != null); 
            objectMapper.writeValue(response.getWriter(), new ManifestUrl(manifestUri)); 
            response.setContentType("application/json"); 
        } catch (Exception e) { 
            LOGGER.error(e.getMessage(), e); 
            error(String.format("Unable to get the manifest url for %s. %s", assetPath, e.getMessage()), response); 
        } 
    } 

    private ResourceResolver getResourceResolver(HttpServletRequest request) { 
        Object rr = request.getAttribute(AuthenticationSupport.REQUEST_ATTRIBUTE_RESOLVER); 
        if (!(rr instanceof ResourceResolver)) { 
            throw new IllegalStateException( 
                    "The request does not seem to have been created via Apache Sling's authentication mechanism."); 
        } else { 
            return (ResourceResolver) rr; 
        } 
    } 

    private void error(String errorMessage, HttpServletResponse response) throws IOException { 
        ManifestUrl errorManifest = new ManifestUrl(null); 
        errorManifest.setErrorMessage(errorMessage); 
        response.setStatus(HttpServletResponse.SC_INTERNAL_SERVER_ERROR); 
        objectMapper.writeValue(response.getWriter(), errorManifest); 
    } 
} 
```

+++

>[!TAB Response Class for servlet]

+++**Response Class for servlet** 

```java
public class ManifestUrl extends VideoResponse { 
     String manifestUrl; 
     public ManifestUrl(String manifestUrl) { 
         this.manifestUrl = manifestUrl; 
     } 
     public String getManifestUrl() { 
         return manifestUrl; 
     } 
} 

public abstract class VideoResponse { 
     String errorString; 

     public String getErrorString() { 
         return errorString; 
     } 

     public void setErrorMessage(String errorString) { 
         this.errorString = errorString; 
     } 
} 
```

+++

>[!TAB Constants file referenced in servlet]

+++**Constants file referenced in servlet** 

```java
public final class Constants { 

     private Constants() { 
     } 

     public static final String VIDEO_API_PREFIX = "/dynamicmedia/video"; 
     public static final String SERVLET_CONTEXT_SELECTOR = "(" + HttpWhiteboardConstants.HTTP_WHITEBOARD_CONTEXT_NAME + "=" + 
             DMSampleApiHttpContext.CONTEXT_NAME + ")"; 

 } 
```

+++

>[!TAB ServletContext]

+++**ServletContext** 

Mount the above servlet using a `servletContext`. The following is an example of `servletContext`. 

```java
public class DMSampleApiHttpContext extends ServletContextHelper { 

 public static final String CONTEXT_NAME = "com.adobe.dmSample"; 
 public static final String CONTEXT_PATH = "/dmSample"; 

 private final MimeTypeService mimeTypeService; 

 private final AuthenticationSupport authenticationSupport; 

 /** 
  * Constructs a new context that will use the given dependencies. 
  * 
  * @param mimeTypeService Used when providing mime type of requests. 
  * @param authenticationSupport Used to authenticate requests with sling. 
  */ 
 @Activate 
 public DMSampleApiHttpContext(@Reference final MimeTypeService mimeTypeService, 
                               @Reference final AuthenticationSupport authenticationSupport) { 
     this.mimeTypeService = mimeTypeService; 
     this.authenticationSupport = authenticationSupport; 
 } 

 // ---------- HttpContext interface ---------------------------------------- 
 /** 
  * Returns the MIME type as resolved by the <code>MimeTypeService</code> or 
  * <code>null</code> if the service is not available. 
  */ 
 @Override 
 public String getMimeType(String name) { 
     MimeTypeService mtservice = mimeTypeService; 
     if (mtservice != null) { 
         return mtservice.getMimeType(name); 
     } 
     return null; 
 } 

 /** 
  * Returns the real context path that is used to mount this context. 
  * @param req servlet request 
  * @return the context path 
  */ 
 public static String getRealContextPath(HttpServletRequest req) { 
     final String path = req.getContextPath(); 
     if (path.equals(CONTEXT_PATH)) { 
         return ""; 
     } 
     return path.substring(CONTEXT_PATH.length()); 
 } 

 /** 
  * Returns a request wrapper that transforms the context path back to the original one 
  * @param req request 
  * @return the request wrapper 
  */ 
 public static HttpServletRequest createContextPathAdapterRequest(HttpServletRequest req) { 
     return new HttpServletRequestWrapper(req) { 

         @Override 
         public String getContextPath() { 
             return getRealContextPath((HttpServletRequest) getRequest()); 
         } 

     }; 

 } 

 /** 
  * Always returns <code>null</code> because resources are all provided 
  * through individual endpoint implementations. 
  */ 
 @Override 
 public URL getResource(String name) { 
     return null; 
 } 

 /** 
  * Tries to authenticate the request using the 
  * <code>SlingAuthenticator</code>. If the authenticator or the Repository 
  * is missing this method returns <code>false</code> and sends a 503/SERVICE 
  * UNAVAILABLE status back to the client. 
  */ 
 @Override 
 public boolean handleSecurity(HttpServletRequest request, 
                               HttpServletResponse response) throws IOException { 

     final AuthenticationSupport authenticator = this.authenticationSupport; 
     if (authenticator != null) { 
         return authenticator.handleSecurity(createContextPathAdapterRequest(request), response); 
     } 

     // send 503/SERVICE UNAVAILABLE, flush to ensure delivery 
     response.sendError(HttpServletResponse.SC_SERVICE_UNAVAILABLE, 
             "AuthenticationSupport service missing. Cannot authenticate request."); 
     response.flushBuffer(); 

     // terminate this request now 
     return false; 
 } 
}
```

+++

>[!ENDTABS]



### Use the sample servlet

You invoke the servlet by performing a `GET` operation at `/dmSample/dynamicmedia/video/manifestUrl`. The following query parameters are passed: 

| Query parameter | Description |
| --- | --- |
| `assetPath` | Mandatory. The path to the video for which `manifestUrl` is generated. |
| `manifestType` | Optional. Parameter can be DASH or HLS. If it is not passed, it defaults to DASH. |
| `onlyIfPublished` | Optional. If passed, the `manifestUrl` is returned only if the video is published.  |

In this example, let us assume the following setup: 

* The company is `samplecompany`.
* The authoring instance is `http://sample-aem-author.com`.
* The folder `/content/dam/video-example` has a video encoding profile applied to it. 
* The video `scenery.mp4` is uploaded to the folder `/content/dam/video-example`.

You can invoke the servlet in following ways: 
     
| Type | Description |
| :--- | --- |
| HLS | `http://sample-aem-author.com/dmSample/dynamicmedia/video/manifestUrl?manifestType=HLS&assetPath=/content/dam/video-example/scenery.mp4`<br><br>In case DASH delivery is enabled:<br>`{"manifestUrl":"https://s7d1.scene7.com/is/content/samplecompany/scenery-AVS.m3u8?packagedStreaming=true"}`<br><br>In case DASH delivery is disabled:<br>`{"manifestUrl":"https://s7d1.scene7.com/is/content/samplecompany/scenery-AVS.m3u8"}` |
| DASH | `http://sample-aem-author.com/dmSample/dynamicmedia/video/manifestUrl?manifestType=DASH&assetPath=/content/dam/video-example/scenery.mp4`<br><br>In case DASH delivery is enabled:<br>`{"manifestUrl":"https://s7d1.scene7.com/is/content/samplecompany/scenery-AVS.mpd"}`<br><br>In case DASH delivery is disabled:<br>`{}` |
| Error: asset path is wrong | `http://sample-aem-author.com/dmSample/dynamicmedia/video/manifestUrl?manifestType=DASH&assetPath=/content/dam/video-example/scennnnnnery.mp4`<br><br>`{"errorString":"could not retrieve the resource from JCR"}` |

-->





