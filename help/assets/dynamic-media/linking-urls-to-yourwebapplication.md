---
title: 웹 애플리케이션에 URL 연결
description: Dynamic Media에서 웹 애플리케이션에 URL을 연결하는 방법을 알아봅니다.
contentOwner: Rick Brough
feature: Publishing,Upload,Viewer Presets,Image Presets,Video
role: User
exl-id: 3cd3f4d5-ebf0-4318-9a0d-1ea69453d57b
source-git-commit: 36ab36ba7e14962eba3947865545b8a3f29f6bbc
workflow-type: tm+mt
source-wordcount: '1281'
ht-degree: 5%

---

# 웹 애플리케이션에 URL 연결 {#linking-urls-to-your-web-application}

웹 사이트 및 애플리케이션은 URL 호출을 통해 Dynamic Media 서비스에 액세스합니다. 에셋을 게시하면 Dynamic Media는 에셋을 참조하는 URL 문자열을 활성화합니다. 테스트를 위해 이러한 URL을 웹 브라우저에 붙여넣을 수 있습니다.

Adobe Experience Manager을 WCM으로 사용하여 *not*&#x200B;하는 경우에만 URL에 연결합니다. 링크 - 대 포함 - 은 비디오 플레이어를 팝업 또는 모달 창으로 전달하려는 경우에 사용됩니다. Experience Manager을 WCM으로 사용하는 경우 [에셋을 페이지에서 바로 추가](adding-dynamic-media-assets-to-pages.md)합니다.

이러한 URL 문자열을 웹 페이지 및 애플리케이션에 배치하려면 Dynamic Media에서 복사하십시오.

>[!NOTE]
>
>URL 문자열은 자산의 동적 변환에만 사용할 수 있습니다. 현재 Dynamic Media 서버가 아닌 DAM에 있는 정적 에셋에 사용할 수 없습니다. 정적인 렌디션에 대해서는 URL 버튼이 나타나지 않습니다.

[웹 페이지에 비디오 또는 이미지 뷰어 포함](embed-code.md)도 참조하세요.

[웹 응용 프로그램에 YouTube URL 연결](video.md)도 참조하세요.

[응답형 사이트에 최적화된 이미지 제공](responsive-site.md)도 참조하세요.

[Assets 업로드](/help/assets/manage-digital-assets.md#uploading-assets)도 참조하세요.

## 에셋에 대한 URL 얻기 {#obtaining-a-url-for-an-asset}

이미지 사전 설정 또는 뷰어 사전 설정에서 생성된 URL 문자열을 가져올 수 있습니다. URL을 복사하면 클립보드에 로드되므로 웹 사이트 또는 응용 프로그램의 페이지에 필요에 따라 붙여넣을 수 있습니다.

>[!NOTE]
>
>선택한 자산을 게시하기 전에는 URL을 복사할 수 없습니다. 또한 뷰어 사전 설정 또는 이미지 사전 설정도 게시해야 합니다.
>
>[Assets 게시](publishing-dynamicmedia-assets.md)를 참조하십시오.
>
>[뷰어 사전 설정 게시](managing-viewer-presets.md#publishing-viewer-presets)를 참조하십시오.
>
>[이미지 사전 설정 게시](managing-image-presets.md#publishing-image-presets)를 참조하십시오.

URL 문자열을 가져오는 방법에는 여러 가지가 있습니다. 그러나 아래 단계에서는 사용할 수 있는 한 가지 방법만 보여 줍니다.

**에셋의 URL을 얻으려면:**

1. 복사할 이미지 사전 설정 URL 또는 뷰어 사전 설정 URL이 있는 *게시됨* 자산으로 이동한 다음 열 자산을 선택합니다.

   Remember that URLs are only available to copy *after* you have first *published* the assets. In addition, the viewer preset or image preset must also be published.

   [Assets 게시](publishing-dynamicmedia-assets.md)를 참조하십시오.

   [뷰어 사전 설정 게시](managing-viewer-presets.md#publishing-viewer-presets)를 참조하십시오.

   [이미지 사전 설정 게시](managing-image-presets.md#publishing-image-presets)를 참조하십시오.

1. 선택한 에셋을 기반으로 다음 중 하나를 수행합니다.

   * 이미지를 선택한 경우 드롭다운 메뉴에서 **[!UICONTROL 표현물]**&#x200B;을 선택합니다.

     **[!UICONTROL 동적]** 제목 아래에서 사전 설정 이름을 선택하여 올바른 프레임에서 해당 렌디션을 봅니다. 필요한 경우 렌디션 목록을 스크롤하여 동적 머리글을 확인합니다.

     왼쪽 레일의 맨 아래에서 **[!UICONTROL URL]**&#x200B;을(를) 선택합니다.

     ![chlimage_1-270](assets/chlimage_1-270.png)

   * 회전 집합, 이미지 집합, 회전 메뉴 집합 또는 비디오를 선택한 경우, 드롭다운 메뉴에서 **[!UICONTROL 뷰어]**&#x200B;를 선택합니다.

     왼쪽 레일에서 뷰어 사전 설정 이름을 선택합니다. 세트나 비디오의 미리 보기가 별도의 페이지에서 열립니다.

     왼쪽 레일의 하단에서 **[!UICONTROL URL]**&#x200B;을(를) 선택합니다.

     ![chlimage_1-271](assets/chlimage_1-271.png)

1. 에셋을 미리 보거나 웹 콘텐츠 페이지에 추가하려면 를 선택하고 텍스트를 웹 브라우저에 복사합니다.

   URL 창을 종료하려면 **[!UICONTROL X]**&#x200B;을(를) 선택하거나 **[!UICONTROL 닫기]**&#x200B;를 선택합니다.

## 정적 자산에 대한 URL 얻기 {#obtaining-a-url-for-a-static-asset}

Dynamic Media는 이미지 및 비디오 이상의 다른 에셋인 정적 에셋의 전달을 지원합니다. 게재에 지원되는 정적 에셋 포맷은 다음과 같습니다.

* 3D 파일
* 애니메이션 GIF
* 오디오 파일
* CSS
* JavaScript(회사가 자체 도메인으로 구성된 경우)
* PDF
* SVG
* XML
* ZIP

**정적 자산의 URL을 얻으려면:**

1. URL을 복사할 *게시된* 정적 자산으로 이동한 다음 열 자산을 선택합니다.

   URL은 *after*&#x200B;를 복사하는 데만 사용할 수 있습니다. 먼저 정적 자산을 *게시*&#x200B;했습니다.

   [Assets 게시](publishing-dynamicmedia-assets.md)를 참조하십시오.

1. 게시된 정적 자산의 URL을 가져오려면 다음 방법 중 하나를 사용하십시오.

   * `The URL of the published static is the following:`

      * `https://*<server_name>*/is/content/*<company_name>*/*<static_asset_filename>*.*<extension>*`

        예: `https://aem.com/is/content/adobe/image.gif`

   * **[!UICONTROL 자산]** > **[!UICONTROL 동적 렌디션]**&#x200B;을 선택한 다음 정적 자산의 동적 렌디션을 선택하고 URL을 복사합니다.

     `is/image/` 대신 경로의 `is/content`을(를) 사용하도록 복사된 URL을 변경하십시오.

## 게시된 비디오 렌디션에 대한 비디오 URL 가져오기 {#obtaining-a-video-url-for-a-published-video-rendition}

1. Experience Manager에서 **[!UICONTROL 도구]** > **[!UICONTROL 배포]** > **[!UICONTROL 클라우드]** > **[!UICONTROL 클라우드 서비스]**&#x200B;로 이동합니다.
1. **[!UICONTROL 클라우드 서비스]** 페이지에서 **[!UICONTROL Dynamic Media 클라우드 서비스]** 제목까지 아래로 스크롤한 다음 **[!UICONTROL 구성 표시]**&#x200B;를 선택합니다.
1. **[!UICONTROL 사용 가능한 구성]**&#x200B;에서 원하는 구성의 이름을 선택합니다.

1. **[!UICONTROL Dynamic Media 클라우드 설정]** 페이지의 **[!UICONTROL 비디오 서비스 URL]**&#x200B;에서 전체 URL 경로를 복사합니다. 복사한 URL 경로는 이 단계의 후반부에 필요합니다.

   예를 들어 URL 경로는 다음과 유사하게 나타날 수 있습니다.

   `https://s7athens.macromedia.com:9090/DMGateway/`

   (위의 경로는 설명 목적으로만 사용되며 복사하는 실제 경로가 아닙니다.)

1. Under **[!UICONTROL Registration ID]**, copy the customer name found in the last part of the ID.

   예를 들어 등록 ID가 `87654321|MyCompany`이면 고객 이름은 `MyCompany`이 됩니다.

1. 페이지의 왼쪽 상단 모서리에서 **[!UICONTROL 클라우드 서비스]**&#x200B;를 선택한 다음 Experience Manager 아이콘을 선택하고 **[!UICONTROL 일반]** > **[!UICONTROL CRXDE Lite]**(으)로 이동합니다.
1. JCR(Java™ Content Repository)에서 전체 비디오 렌디션 경로를 복사합니다.

   예를 들어 비디오의 렌디션 경로가 다음과 유사하게 나타날 수 있습니다.

   `/_renditions_/0bd/0bd28743-a616-4fe6-92aa-6eae7c2112f/avs/Momentum_1080-0x720-2600k.mp4`

   (위의 경로는 설명 목적으로만 사용되며 복사하는 실제 경로가 아닙니다.)

1. 전체 URL 경로를 생성하려면 복사된 정보를 다음 순서로 정렬하십시오.

   `<Video_Service_URL>/public/<Customer_name_from_Registration_ID>/<Video_rendition_path>`

   예를 들어 위의 단계에서 경로 예와 고객 이름 예를 사용하면 전체 경로가 다음과 같이 표시됩니다.

   `https://s7athens.macromedia.com:9090/DMGateway/public/MyCompany/_renditions_/0bd/0bd28743-a616-4fe6-92aa-6eae7c2112ff/avs/Momentum_1080-0x720-2600k.mp4`

   이 경로는 게시된 비디오 렌디션의 전체 비디오 URL입니다.

## 적응형 비트율 스트리밍을 위한 비디오 URL 얻기(HLS) {#obtaining-a-video-url-for-adaptive-streaming-hls}

1. Experience Manager에서 **[!UICONTROL 도구]** > **[!UICONTROL 배포]** > **[!UICONTROL 클라우드]** > **[!UICONTROL 클라우드 서비스]**&#x200B;로 이동합니다.
1. **[!UICONTROL 클라우드 서비스]** 페이지에서 **[!UICONTROL Dynamic Media 클라우드 서비스]** 제목까지 아래로 스크롤한 다음 **[!UICONTROL 구성 표시]**&#x200B;를 선택합니다.
1. **[!UICONTROL 사용 가능한 구성]**&#x200B;에서 원하는 구성의 이름을 선택합니다.
1. **[!UICONTROL Dynamic Media 클라우드 서비스 설정]** 페이지에서 다음을 수행합니다.

   * **[!UICONTROL 비디오 서비스 URL]**&#x200B;에서 전체 URL 경로를 복사합니다. 이 단계의 후반부에 복사한 URL 경로가 필요합니다. 예를 들어 URL 경로는 다음과 유사하게 나타날 수 있습니다.

   `https://gateway-na.assetsadobe.com/DMGateway/`

   (위의 경로는 설명 목적으로만 사용되며 복사하는 실제 경로가 아닙니다.)

   * **[!UICONTROL 등록 ID]**&#x200B;에서 ID의 마지막 부분에 있는 고객 이름을 복사합니다. 이 단계의 후반부에 복사한 고객 이름이 필요합니다.

     예를 들어 등록 ID가 `87654321|demoCo`인 경우 복사한 고객 이름은 `demoCo`입니다.

1. 사용 중인 비디오 제공 프로토콜을 기반으로 각 프로토콜 선택기를 복사합니다. 이 단계의 후반부에 복사된 프로토콜 선택기가 필요합니다.

   <table>
    <tbody>
      <tr>
      <td><strong>사용 중인 비디오 게재 프로토콜</strong></td>
      <td><strong>사용할 프로토콜 선택기</strong></td>
      </tr>
      <tr>
      <td><p>HTTP</p> <p>HTTP(비보안 비디오 게재)를 사용하는 경우 이전에 복사한 비디오 서비스 URL 값에서 <code>https</code>을(를) <code>http</code>(으)로 변경하십시오.</p> </td>
      <td><code>public/</code></td>
      </tr>
      <tr>
      <td>HTTPS</td>
      <td><code>public-ssl/</code></td>
      </tr>
    </tbody>
   </table>

1. Dynamic Media에서 처리한 대로 Experience Manager에서 전체 비디오 자산 경로를 복사합니다. 이 복사한 비디오 자산 경로는 이 단계의 후반부에 필요합니다.

   예:

   `/content/dam/marketing/MyVideo.mp4`

1. 이전에 복사한 모든 조각을 결합하여 다음 순서로 문자열을 만듭니다.

   &lt; `video service URL`>&lt; `protocol selector`>&lt; `customer name`>&lt; `video asset path`>

   예를 들어 이 단계의 예제에서 복사한 정보를 사용하면 문자열은 다음과 같이 나타납니다.

   `https://gateway-na.assetsadobe.com/DMGateway/public-ssl/demoCo/content/dam/marketing/MyVideo.mp4`

1. 문자열 끝에 `.m3u8`을(를) 추가하여 URL을 완료합니다. 예를 들어 이전 단계의 문자열에 `.m3u8`을(를) 추가하면 전체 URL 경로가 다음과 같이 표시됩니다.

   `https://gateway-na.assetsadobe.com/DMGateway/public-ssl/demoCo/content/dam/marketing/MyVideo.mp4.m3u8`

## HTTP/2를 사용하여 Dynamic Media 자산 전달 {#using-http-to-deliver-your-dynamic-media-assets}

HTTP/2는 새로운 업데이트된 웹 프로토콜로서 브라우저와 서버의 통신 방식을 개선합니다. 정보 전송 속도를 높이고 필요한 처리 능력을 줄일 수 있습니다. 이제 Dynamic Media 에셋의 전달이 HTTP/2를 통해 가능해져 응답 및 로드 시간이 향상됩니다.

Dynamic Media 계정으로 HTTP/2를 사용하는 방법에 대한 자세한 내용은 [HTTP2 컨텐츠 배달](http2faq.md)을 참조하십시오.
