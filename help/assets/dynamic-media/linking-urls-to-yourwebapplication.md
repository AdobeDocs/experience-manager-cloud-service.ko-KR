---
title: URL을 웹 애플리케이션에 연결
description: 다이내믹 미디어에서 웹 애플리케이션에 URL을 연결하는 방법
translation-type: tm+mt
source-git-commit: c240f9aa465b019fa77cc471f865db1f4ab45532
workflow-type: tm+mt
source-wordcount: '1271'
ht-degree: 1%

---


# URL을 웹 애플리케이션에 연결 {#linking-urls-to-your-web-application}

웹 사이트와 애플리케이션은 URL 호출을 통해 Dynamic Media 서비스에 액세스합니다. 자산을 게시하면, Dynamic Media는 자산을 참조하는 URL 문자열을 활성화합니다. 이러한 URL을 웹 브라우저에 붙여넣어 테스트할 수 있습니다.

AEM을 WCM으로 사용하지 *않는* 경우에만 URL에 연결합니다. 연결 대 포함-은 비디오 플레이어를 팝업 또는 모달 창으로 제공하려는 경우에 사용됩니다. AEM을 WCM으로 사용하는 경우 [자산을 페이지에 직접 추가합니다.](adding-dynamic-media-assets-to-pages.md)

웹 페이지 및 응용 프로그램에 이러한 URL 문자열을 배치하려면 Dynamic Media에서 복사합니다.

>[!NOTE]
>
>URL 문자열은 자산의 동적 변환에만 사용할 수 있습니다. 현재 동적 미디어 서버가 아닌 DAM에 있는 정적 자산에는 사용할 수 없습니다. 정적인 변환에는 URL 단추가 표시되지 않습니다.

See also [Embedding the Video or Image Viewer on a Web Page](embed-code.md).

See also [Linking YouTube URLs to your Web Application](video.md).

See also [Delivering Optimized Images for a Responsive Site](responsive-site.md).

See also [Uploading Assets](/help/assets/manage-digital-assets.md#uploading-assets).

## 자산에 대한 URL 얻기 {#obtaining-a-url-for-an-asset}

이미지 사전 설정 또는 뷰어 사전 설정으로 생성된 URL 문자열을 얻을 수 있습니다. URL을 복사하면 클립보드로 이동하므로 웹 사이트 또는 애플리케이션의 페이지에 필요에 따라 붙여넣을 수 있습니다.

>[!NOTE]
>
>선택한 자산을 게시해야만 URL을 복사할 수 있습니다. 또한 뷰어 사전 설정 또는 이미지 사전 설정도 게시해야 합니다.
>
>자산 [게시를 참조하십시오](publishing-dynamicmedia-assets.md).
>
>See [Publishing Viewer Presets](managing-viewer-presets.md#publishing-viewer-presets).
>
>See [Publishing Image Presets](managing-image-presets.md#publishing-image-presets).

URL 문자열을 얻는 방법에는 여러 가지가 있습니다. 그러나 아래 단계에는 사용할 수 있는 방법이 하나만 표시됩니다.

**자산에 대한 URL을 얻으려면**

1. 복사하려는 이미지 사전 설정 URL 또는 뷰어 사전 설정 URL의 *게시된* 자산으로 이동하고 자산을 눌러 엽니다.

   URL은 자산을 처음 *게시한* 후에만 *복사할 수* 있습니다. 또한 뷰어 사전 설정 또는 이미지 사전 설정도 게시해야 합니다.

   자산 [게시를 참조하십시오](publishing-dynamicmedia-assets.md).

   See [Publishing Viewer Presets](managing-viewer-presets.md#publishing-viewer-presets).

   See [Publishing Image Presets](managing-image-presets.md#publishing-image-presets).

1. 선택한 자산에 따라 다음 중 하나를 수행합니다.

   * 이미지를 선택한 경우 드롭다운 메뉴에서 표현물을 **[!UICONTROL 누릅니다]**.

      [ **[!UICONTROL 동적]** ] 머리글 아래에서 사전 설정 이름을 눌러 오른쪽 프레임에서 해당 변환을 봅니다. 동적 제목을 보려면 표현물 목록을 스크롤해야 할 수도 있습니다.

      왼쪽 레일 하단에서 **[!UICONTROL URL을 누릅니다]**.

      ![chlimage_1-270](assets/chlimage_1-270.png)

   * 스핀 세트, 이미지 세트, 회전판 세트 또는 비디오를 선택한 경우 드롭다운 메뉴에서 **[!UICONTROL 뷰어를 누릅니다]**.

      왼쪽 레일에서 뷰어 사전 설정 이름을 누릅니다. 세트 또는 비디오의 미리 보기가 별도의 페이지에서 열립니다.

      왼쪽 레일의 맨 아래에 있는 **[!UICONTROL URL을 누릅니다]**.

      ![chlimage_1-271](assets/chlimage_1-271.png)

1. 텍스트를 선택하여 웹 브라우저에 복사하여 자산을 미리 보거나 웹 컨텐츠 페이지에 추가합니다.

   URL 창을 종료하려면 **[!UICONTROL X를]** 누르거나 **[!UICONTROL 닫기를 누릅니다]**.

## 정적 자산에 대한 URL 얻기 {#obtaining-a-url-for-a-static-asset}

Dynamic Media는 정적 자산 전달을 지원하며, 이는 단순히 이미지와 비디오를 넘어 추가 자산입니다. 배달을 위해 지원되는 정적 자산 형식은 다음과 같습니다.

* 3D 파일
* 애니메이션 GIF
* 오디오 파일
* CSS
* JavaScript(회사가 자체 도메인으로 구성된 경우)
* PDF
* SVG
* XML
* ZIP

**정적 자산에 대한 URL을 얻으려면**

1. 복사할 URL이 있는 *게시된 정적 자산으로 이동하고 자산을 눌러 엽니다.

   URL은 정적 자산을 처음 *게시한* 후에만 *복사할 수* 있습니다.

   자산 [게시를 참조하십시오](publishing-dynamicmedia-assets.md).

1. 게시된 정적 자산의 URL을 얻으려면 다음 방법 중 하나를 사용하십시오.

   * `The URL of the published static is the following:`

      * `https://*<server_name>*/is/content/*<company_name>*/*<static_asset_filename>*.*<extension>*`

         예, `https://aem.com/is/content/adobe/image.gif`.
   * 자산 **[!UICONTROL > 동적 표현물]**&#x200B;을 누른 다음 정적 자산의 동적 변환을 누르고 URL을 복사합니다.

      복사된 URL을 경로 대신 경로 `is/content` 에서 사용하도록 변경합니다 `is/image/`.


## 게시된 비디오 변환에 대한 비디오 URL 얻기 {#obtaining-a-video-url-for-a-published-video-rendition}

1. AEM에서 **[!UICONTROL 도구 > 배포 > 클라우드 > Cloud Services으로 이동합니다]**.
1. Cloud Services **[!UICONTROL 페이지에서]** Dynamic Media Cloud Services **[!UICONTROL 제목으로 아래로 스크롤한 다음 구성]** 표시를 **[!UICONTROL 누릅니다]**.
1. 사용 **[!UICONTROL 가능한 구성]**&#x200B;아래에서 원하는 구성 이름을 누릅니다.

1. [ **[!UICONTROL Dynamic Media 클라우드 설정]** ] 페이지의 **[!UICONTROL 비디오 서비스 URL]**&#x200B;아래에서 전체 URL 경로를 복사합니다. 나중에 단계에 복사한 URL 경로가 필요합니다.

   예를 들어 URL 경로는 다음과 유사하게 나타날 수 있습니다.

   `https://s7athens.macromedia.com:9090/DMGateway/`

   (위 경로는 그림 용도로만 사용됩니다.복사하는 실제 경로가 아닙니다.)

1. [ **[!UICONTROL 등록 ID]]**&#x200B;아래에서 ID의 마지막 부분에 있는 고객 이름을 복사합니다.

   예를 들어 등록 ID가 `87654321|MyCompany`있는 경우 고객 이름이 `MyCompany`됩니다.

1. 페이지의 왼쪽 위 모서리 근처에 있는 **[!UICONTROL Cloud Services]**&#x200B;을 탭한 다음 AEM 아이콘을 탭하고 **[!UICONTROL 일반 > CRXDE Lite으로 이동합니다]**.
1. JCR(Java Content Repository)에서 전체 비디오 변환 경로를 복사합니다.

   예를 들어 비디오의 변환 경로는 다음과 유사하게 나타날 수 있습니다.

   `/_renditions_/0bd/0bd28743-a616-4fe6-92aa-6eae7c2112f/avs/Momentum_1080-0x720-2600k.mp4`

   (위 경로는 그림 용도로만 사용됩니다.복사하는 실제 경로가 아닙니다.)

1. 복사한 정보를 다음 순서로 배열하여 전체 URL 경로를 형성합니다.

   `<Video_Service_URL>/public/<Customer_name_from_Registration_ID>/<Video_rendition_path>`

   예를 들어 위의 단계에서 예제 경로와 예제 고객 이름을 사용하면 전체 경로가 다음과 같이 표시됩니다.

   `https://s7athens.macromedia.com:9090/DMGateway/public/MyCompany/_renditions_/0bd/0bd28743-a616-4fe6-92aa-6eae7c2112ff/avs/Momentum_1080-0x720-2600k.mp4`

   게시된 비디오 변환에 대한 전체 비디오 URL입니다.

## 응용 스트리밍(HLS)을 위한 비디오 URL 얻기 {#obtaining-a-video-url-for-adaptive-streaming-hls}

1. AEM에서 **[!UICONTROL 도구 > 배포 > 클라우드 > Cloud Services으로 이동합니다]**.
1. Cloud Services **[!UICONTROL 페이지에서]** Dynamic Media Cloud Services **[!UICONTROL 제목으로 아래로 스크롤한 다음 구성]** 표시를 **[!UICONTROL 누릅니다]**.
1. 사용 **[!UICONTROL 가능한 구성]**&#x200B;아래에서 원하는 구성 이름을 누릅니다.
1. [ **[!UICONTROL 다이내믹 미디어 Cloud Services 설정]** ] 페이지에서 다음을 수행합니다.

   * 비디오 **[!UICONTROL 서비스 URL]**&#x200B;아래에서 전체 URL 경로를 복사합니다. 이 단계 후반부에 복사된 URL 경로가 필요합니다. 예를 들어 URL 경로는 다음과 유사하게 나타날 수 있습니다.

   `https://gateway-na.assetsadobe.com/DMGateway/`

   (위 경로는 그림 용도로만 사용됩니다.복사하는 실제 경로가 아닙니다.)

   * [ **[!UICONTROL 등록 ID]]**&#x200B;아래에서 ID의 마지막 부분에 있는 고객 이름을 복사합니다. 이 단계에서 나중에 복사된 고객 이름이 필요합니다.

      예를 들어 등록 ID가 `87654321|demoCo`있는 경우 복사한 고객 이름이 됩니다 `demoCo`.


1. 사용 중인 비디오 전달 프로토콜을 기반으로 각 프로토콜 선택기를 복사합니다. 이 단계 후반부에 복사된 프로토콜 선택기가 필요합니다.

   <table>
    <tbody>
      <tr>
      <td><strong>사용 중인 비디오 전달 프로토콜</strong></td>
      <td><strong>사용할 프로토콜 선택기</strong></td>
      </tr>
      <tr>
      <td><p>HTTP</p> <p>HTTP(비보안 비디오 전달)를 사용하는 경우 이전에 복사한 비디오 서비스 URL 값 <code>https</code><code>http</code> 에서 변경하십시오.</p> </td>
      <td><code>public/</code></td>
      </tr>
      <tr>
      <td>HTTPS</td>
      <td><code>public-ssl/</code></td>
      </tr>
    </tbody>
   </table>

1. Dynamic Media에서 처리하는 대로 AEM의 전체 비디오 자산 경로를 복사합니다. 이 비디오 자산 경로는 이 단계 후반부에서 복사해야 합니다.

   예:

   `/content/dam/marketing/MyVideo.mp4`

1. 이전에 복사한 모든 조각을 결합하여 다음 순서로 문자열을 생성합니다.

   &lt; `video service URL`>&lt; `protocol selector`>&lt; `customer name`>&lt; `video asset path`>

   예를 들어, 이러한 단계의 예에서 복사한 정보를 사용하면 다음과 같이 문자열이 나타납니다.

   `https://gateway-na.assetsadobe.com/DMGateway/public-ssl/demoCo/content/dam/marketing/MyVideo.mp4`

1. 문자열 끝 `.m3u8` 에 추가하여 URL을 완료합니다. 예를 들어 이전 단계의 문자열 `.m3u8` 에 추가하면 전체 URL 경로가 다음과 같이 표시됩니다.

   `https://gateway-na.assetsadobe.com/DMGateway/public-ssl/demoCo/content/dam/marketing/MyVideo.mp4.m3u8`

## HTTP/2를 사용하여 다이내믹 미디어 에셋 전달 {#using-http-to-deliver-your-dynamic-media-assets}

HTTP/2는 브라우저와 서버의 통신 방식을 향상시키는 업데이트된 새로운 웹 프로토콜입니다. 정보를 빠르게 전송할 수 있고 필요한 처리 능력을 줄일 수 있습니다. HTTP/2를 통해 다이내믹 미디어 에셋을 전달할 수 있으므로 응답 및 로드 시간이 향상됩니다.

Dynamic Media 계정 [으로 HTTP/2 사용을 시작하는 방법에 대한 자세한 내용은 HTTP2 컨텐츠](http2faq.md) 배달을 참조하십시오.
