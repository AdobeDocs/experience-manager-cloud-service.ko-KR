---
title: ' [!DNL Assets]에 대한 개발자 참조'
description: '[!DNL Assets] APIs and developer reference content lets you manage assets, including binary files, metadata, renditions, comments, and [!DNL Content Fragments].'
contentOwner: AG
translation-type: tm+mt
source-git-commit: 77b4d9f07626419ddab3a7363b06c382447ec982
workflow-type: tm+mt
source-wordcount: '1400'
ht-degree: 3%

---


# [!DNL Adobe Experience Manager Assets] API 및 개발자 참조 자료  {#assets-cloud-service-apis}

이 문서에서는 [!DNL Assets](으)로 개발자를 위한 권장 사항, 참조 자료 및 리소스를 제공합니다. [!DNL Cloud Service] 여기에는 새로운 에셋 업로드 모듈, API 참조 및 사후 처리 워크플로우에서 제공되는 지원에 대한 정보가 포함되어 있습니다.

## [!DNL Experience Manager Assets] API 및 작업  {#use-cases-and-apis}

[!DNL Assets] as a는  [!DNL Cloud Service] 프로그래밍 방식으로 디지털 자산과 상호 작용할 수 있는 여러 API를 제공합니다. 각 API는 아래 표에 설명된 대로 특정 사용 사례를 지원합니다. [!DNL Assets] 사용자 인터페이스, [!DNL Experience Manager] 데스크톱 앱 및 [!DNL Adobe Asset Link]은 모든 작업 또는 일부를 지원합니다.

>[!CAUTION]
>
>일부 API는 계속 존재하지만 적극적으로 지원되지 않습니다(×로 표시). 사용할 수 없습니다.

| 지원 수준 | 설명 |
| ------------- | --------------------------- |
| ✓ | 지원됨 |
| × | 지원되지 않음. 사용하지 마십시오. |
| - | 사용할 수 없음 |

| 사용 사례 | [aem 업로드](https://github.com/adobe/aem-upload) | [AEM / Sling / ](https://docs.adobe.com/content/help/en/experience-manager-cloud-service-javadoc/index.html) JCRJava API | [Asset compute 서비스](https://experienceleague.adobe.com/docs/asset-compute/using/extend/understand-extensibility.html) | [[!DNL Assets] HTTP API](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/assets/admin/mac-api-assets.html#create-an-asset) | [GET](https://sling.apache.org/documentation/bundles/rendering-content-default-get-servlets.html) / [POST](https://sling.apache.org/documentation/bundles/manipulating-content-the-slingpostservlet-servlets-post.html) 서블릿 | [GraphQL](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/graphql/overview.html) _(미리 보기)_ |
| ----------------|:---:|:---:|:---:|:---:|:---:|:---:|
| **원본 이진** |  |  |  |  |  |  |
| 원본 만들기 | ✓ | × | - | × | × | - |
| 원본 읽기 | - | × | ✓ | ✓ | ✓ | - |
| 원본 업데이트 | ✓ | × | ✓ | × | × | - |
| 원본 삭제 | - | ✓ | - | ✓ | ✓ | - |
| 원본 복사 | - | ✓ | - | ✓ | ✓ | - |
| 원본 이동 | - | ✓ | - | ✓ | ✓ | - |
| **메타데이터** |  |  |  |  |  |  |
| 메타데이터 만들기 | - | ✓ | ✓ | ✓ | ✓ | - |
| 메타데이터 읽기 | - | ✓ | - | ✓ | ✓ | - |
| 메타데이터 업데이트 | - | ✓ | ✓ | ✓ | ✓ | - |
| 메타데이터 삭제 | - | ✓ | ✓ | ✓ | ✓ | - |
| 메타데이터 복사 | - | ✓ | - | ✓ | ✓ | - |
| 메타데이터 이동 | - | ✓ | - | ✓ | ✓ | - |
| **컨텐츠 조각(CF)** |  |  |  |  |  |  |
| CF 만들기 | - | ✓ | - | ✓ | - | - |
| CF 읽기 | - | ✓ | - | ✓ | - | ✓ |
| CF 업데이트 | - | ✓ | - | ✓ | - | - |
| CF 삭제 | - | ✓ | - | ✓ | - | - |
| CF 복사 | - | ✓ | - | ✓ | - | - |
| CF 이동 | - | ✓ | - | ✓ | - | - |
| **버전** |  |  |  |  |  |  |
| 버전 만들기 | ✓ | ✓ | - | - | - | - |
| 버전 읽기 | - | ✓ | - | - | - | - |
| 버전 삭제 | - | ✓ | - | - | - | - |
| **폴더** |  |  |  |  |  |  |
| 폴더 만들기 | ✓ | ✓ | - | ✓ | - | - |
| 폴더 읽기 | - | ✓ | - | ✓ | - | - |
| 폴더 삭제 | ✓ | ✓ | - | ✓ | - | - |
| 폴더 복사 | ✓ | ✓ | - | ✓ | - | - |
| 폴더 이동 | ✓ | ✓ | - | ✓ | - | - |

## 자산 업로드 {#asset-upload-technical}

[!DNL Experience Manager] as a [!DNL Cloud Service] 는 자산을 저장소에 업로드하는 새로운 방법을 제공합니다. 사용자는 HTTP API를 사용하여 자산을 클라우드 스토리지에 직접 업로드할 수 있습니다. 이진 파일을 업로드하는 단계는 다음과 같습니다.

1. [HTTP 요청을 제출합니다](#initiate-upload). 새 바이너리를 업로드하려는 의도를 [!DNL Experience Manage]r 배포에 알려줍니다.
1. [초기화 요청에서 제공하는 ](#upload-binary) 하나 이상의 URI에 바이너리의 컨텐츠를 POST합니다.
1. [HTTP 요청을 ](#complete-upload) 제출하여 바이너리의 내용이 성공적으로 업로드되었음을 서버에 알립니다.

![직접 이진 업로드 프로토콜 개요](assets/add-assets-technical.png)

이 접근 방식에서는 자산 업로드를 보다 확장 가능하고 성능적으로 처리할 수 있습니다. [!DNL Experience Manager] 6.5와 비교할 때의 차이점은 다음과 같습니다.

* 바이너리는 배포를 위해 구성된 이진 클라우드 스토리지를 사용하여 업로드 프로세스를 조정하는 데 사용되는 [!DNL Experience Manager]을(를) 거치지 않습니다.
* 이진 클라우드 스토리지는 CDN(Content Delivery Network) 또는 Edge 네트워크와 연동됩니다. CDN은 클라이언트에 가까운 업로드 끝점을 선택합니다. 특히 지리적으로 분산된 팀의 경우 데이터가 가까운 종단점으로 이동하는 경우 업로드 성능과 사용자 경험이 향상됩니다.

>[!NOTE]
오픈 소스 [aem-upload 라이브러리](https://github.com/adobe/aem-upload)에서 이 방법을 구현하려면 클라이언트 코드를 참조하십시오.

### 업로드 시작 {#initiate-upload}

HTTP POST 요청을 원하는 폴더에 제출합니다. 이 폴더에 에셋이 생성되거나 업데이트됩니다. 요청이 이진 파일의 업로드를 시작함을 나타내는 `.initiateUpload.json` 선택기를 포함합니다. 예를 들어 자산을 만들어야 하는 폴더의 경로는 `/assets/folder`입니다. POST 요청은 `POST https://[aem_server]:[port]/content/dam/assets/folder.initiateUpload.json`입니다.

요청 본문의 콘텐츠 유형은 다음 필드를 포함하는 `application/x-www-form-urlencoded` 양식 데이터여야 합니다.

* `(string) fileName`: 필수. [!DNL Experience Manager]에 나타나는 자산의 이름입니다.
* `(number) fileSize`: 필수. 업로드되는 자산의 파일 크기(바이트)입니다.

각 바이너리에 필수 필드가 포함되어 있으면 단일 요청을 사용하여 여러 바이너리에 대한 업로드를 시작할 수 있습니다. 성공하면 요청이 `201` 상태 코드와 JSON 데이터가 포함된 본문으로 응답합니다.

```json
{
    "completeURI": "(string)",
    "folderPath": (string)",
    "files": [
        {
            "fileName": "(string)",
            "mimeType": "(string)",
            "uploadToken": "(string)",
            "uploadURIs": [
                "(string)"
            ]
        }
    ]
}
```

* `completeURI` (문자열):이진 업로드를 마치면 이 URI를 호출합니다. URI는 절대 또는 상대 URI일 수 있으며 클라이언트는 둘 중 하나를 처리할 수 있어야 합니다. 즉, 값은 `"https://author.acme.com/content/dam.completeUpload.json"` 또는 `"/content/dam.completeUpload.json"`전체 업로드](#complete-upload)를 참조하십시오.[
* `folderPath` (문자열):바이너리가 업로드된 폴더의 전체 경로입니다.
* `(files)` (배열):시작 요청에 제공된 이진 정보 목록의 길이와 순서가 일치하는 요소 목록입니다.
* `fileName` (문자열):시작 요청에 제공된 해당 바이너리의 이름입니다. 이 값은 전체 요청에 포함되어야 합니다.
* `mimeType` (문자열):시작 요청에 제공된 해당 바이너리의 MIME 유형입니다. 이 값은 전체 요청에 포함되어야 합니다.
* `uploadToken` (문자열):해당 바이너리에 대한 업로드 토큰입니다. 이 값은 전체 요청에 포함되어야 합니다.
* `uploadURIs` (배열):값이 바이너리의 콘텐츠를 업로드해야 하는 전체 URI인 문자열 목록입니다(이진  [업로드](#upload-binary) 참조).
* `minPartSize` (숫자):둘 이상의 URI가 있는 경우 uploadURI 중 하나에 제공할 수 있는 데이터의 최소 길이(바이트)입니다.
* `maxPartSize` (숫자):둘 이상의 URI가 있는 경우 uploadURI 중 하나에 제공할 수 있는 데이터의 최대 길이(바이트)입니다.

### 이진 {#upload-binary} 업로드

업로드를 시작하는 출력에는 하나 이상의 업로드 URI 값이 포함됩니다. 두 개 이상의 URI가 제공되면 클라이언트는 바이너리를 부품으로 분할하고 각 URI에 대한 POST 요청을 순서대로 수행합니다. 모든 URI 사용 각 부품의 크기가 시작 응답에 지정된 최소 및 최대 크기 내에 있는지 확인합니다. CDN 에지 노드를 사용하면 바이너리의 요청된 업로드 속도를 높일 수 있습니다.

이 작업을 수행하는 가능한 방법은 API에서 제공하는 업로드 URI 수를 기준으로 부품 크기를 계산하는 것입니다. 예를 들어 바이너리의 전체 크기는 20,000바이트입니다. 업로드 URI 수는 2라고 가정합니다. 그런 다음 다음 다음 단계를 수행합니다.

* 전체 크기를 URI 수로 나누어 부품 크기를 계산합니다.20,000 / 2 = 10,000.
* 업로드 URI 목록의 첫 번째 URI에 대한 바이너리의 POST 바이트 범위 0-9,999입니다.
* 업로드 URI 목록의 두 번째 URI로 바이너리의 POST 바이트 범위 10,000 - 19,999를 지정합니다.

업로드가 성공하면 서버가 `201` 상태 코드로 각 요청에 응답합니다.

### 업로드 완료 {#complete-upload}

이진 파일의 모든 부분이 업로드된 후 HTTP POST 요청을 시작 데이터가 제공하는 전체 URI에 제출합니다. 요청 본문의 콘텐츠 유형은 다음 필드를 포함하는 `application/x-www-form-urlencoded` 양식 데이터여야 합니다.

| 필드 | 유형 | 필수 또는 아님 | 설명 |
|---|---|---|---|
| `fileName` | 문자열 | 필수 | 초기화 데이터에 의해 제공된 자산의 이름입니다. |
| `mimeType` | 문자열 | 필수 | 초기화 데이터에 의해 제공된 바이너리의 HTTP 컨텐츠 유형입니다. |
| `uploadToken` | 문자열 | 필수 | 초기화 데이터에 의해 제공된 대로 바이너리에 대한 토큰을 업로드합니다. |
| `createVersion` | 부울 | 선택 사항입니다 | `True` 및 지정된 이름의 자산이 있으면 [!DNL Experience Manager]은 자산의 새 버전을 만듭니다. |
| `versionLabel` | 문자열 | 선택 사항입니다 | 새 버전이 만들어진 경우 자산의 새 버전과 연결된 레이블입니다. |
| `versionComment` | 문자열 | 선택 사항입니다 | 새 버전이 만들어지면 버전과 연결된 댓글이 표시됩니다. |
| `replace` | 부울 | 선택 사항입니다 | `True` 및 지정된 이름의 자산이 있는 경우 [!DNL Experience Manager]은 자산을 삭제한 다음 다시 만듭니다. |

>[!NOTE]
자산이 존재하고 `createVersion` 또는 `replace`이 지정되지 않은 경우 [!DNL Experience Manager]는 자산의 현재 버전을 새 바이너리로 업데이트합니다.

시작 프로세스와 마찬가지로 전체 요청 데이터에는 둘 이상의 파일에 대한 정보가 포함될 수 있습니다.

이진 업로드 프로세스는 해당 파일에 대해 전체 URL을 호출할 때까지 수행되지 않습니다. 업로드 프로세스가 완료된 후 자산이 처리됩니다. 자산의 이진 파일이 완전히 업로드되었지만 업로드 프로세스가 완료되지 않은 경우에도 처리가 시작되지 않습니다.

성공하면 서버가 `200` 상태 코드로 응답합니다.

### 오픈 소스 업로드 라이브러리 {#open-source-upload-library}

업로드 알고리즘에 대해 자세히 알아보거나 자신만의 업로드 스크립트 및 도구를 만들기 위해 Adobe은 오픈 소스 라이브러리 및 도구를 제공합니다.

* [오픈 소스 aem-upload 라이브러리](https://github.com/adobe/aem-upload).
* [오픈 소스 명령줄 툴](https://github.com/adobe/aio-cli-plugin-aem).

### 사용되지 않는 에셋 업로드 API {#deprecated-asset-upload-api}

<!-- #ENGCHECK review / update the list of deprecated APIs below. -->

새 업로드 메서드는 [!DNL Adobe Experience Manager]에 대해서만 [!DNL Cloud Service](으)로 지원됩니다. [!DNL Adobe Experience Manager] 6.5의 API는 더 이상 사용되지 않습니다. 자산 또는 표현물(모든 이진 업로드)의 업로드 또는 업데이트와 관련된 메서드는 다음 API에서 더 이상 사용되지 않습니다.

* [Experience Manager 에셋 HTTP API](mac-api-assets.md)
* `AssetManager` Java API, 좋아요  `AssetManager.createAsset(..)`

>[!MORELIKETHIS]
* [오픈 소스 aem-upload 라이브러리](https://github.com/adobe/aem-upload).
* [오픈 소스 명령줄 툴](https://github.com/adobe/aio-cli-plugin-aem).


## 자산 처리 및 사후 처리 워크플로 {#post-processing-workflows}

[!DNL Experience Manager]에서 자산 처리는 [에셋 마이크로서비스](asset-microservices-configure-and-use.md#get-started-using-asset-microservices)를 사용하는 **[!UICONTROL 처리 프로필]** 구성을 기반으로 합니다. 처리에 개발자 확장이 필요하지 않습니다.

사후 처리 워크플로우 구성의 경우 사용자 정의 단계에 따라 확장 기능이 있는 표준 워크플로우를 사용합니다.

## 사후 처리 작업 과정에서 워크플로우 단계 지원 {#post-processing-workflows-steps}

이전 버전의 [!DNL Experience Manager]에서 업그레이드하는 고객은 에셋 마이크로서비스를 사용하여 에셋을 처리할 수 있습니다. 클라우드 기반의 자산 마이크로 서비스는 구성 및 사용이 훨씬 간단합니다. 이전 버전의 [!UICONTROL DAM 자산 업데이트] 워크플로우에서 사용된 몇 가지 워크플로우 단계는 지원되지 않습니다.

[!DNL Experience Manager] 을  [!DNL Cloud Service] 사용하여 다음 워크플로우 단계를 지원합니다.

* `com.day.cq.dam.similaritysearch.internal.workflow.process.AutoTagAssetProcess`
* `com.day.cq.dam.core.impl.process.CreateAssetLanguageCopyProcess`
* `com.day.cq.wcm.workflow.process.CreateVersionProcess`
* `com.day.cq.dam.similaritysearch.internal.workflow.smarttags.StartTrainingProcess`
* `com.day.cq.dam.similaritysearch.internal.workflow.smarttags.TransferTrainingDataProcess`
* `com.day.cq.dam.core.impl.process.TranslateAssetLanguageCopyProcess`
* `com.day.cq.dam.core.impl.process.UpdateAssetLanguageCopyProcess`
* `com.adobe.cq.workflow.replication.impl.ReplicationWorkflowProcess`
* `com.day.cq.dam.core.impl.process.DamUpdateAssetWorkflowCompletedProcess`

다음 기술 워크플로우 모델은 자산 마이크로 서비스로 대체되거나 지원되지 않습니다.

* `com.day.cq.dam.core.impl.process.DamMetadataWritebackWorkflowCompletedProcess`
* `com.day.cq.dam.core.process.DeleteImagePreviewProcess`
* `com.day.cq.dam.s7dam.common.process.DMEncodeVideoWorkflowCompletedProcess`
* `com.day.cq.dam.core.process.GateKeeperProcess`
* `com.day.cq.dam.core.process.AssetOffloadingProcess`
* `com.day.cq.dam.core.process.MetadataProcessorProcess`
* `com.day.cq.dam.core.process.XMPWritebackProcess`
* `com.adobe.cq.dam.dm.process.workflow.DMImageProcess`
* `com.day.cq.dam.s7dam.common.process.S7VideoThumbnailProcess`
* `com.day.cq.dam.scene7.impl.process.Scene7UploadProcess`
* `com.day.cq.dam.s7dam.common.process.VideoProxyServiceProcess`
* `com.day.cq.dam.s7dam.common.process.VideoThumbnailDownloadProcess`
* `com.day.cq.dam.s7dam.common.process.VideoUserUploadedThumbnailProcess`
* `com.day.cq.dam.core.process.CreatePdfPreviewProcess`
* `com.day.cq.dam.core.process.CreateWebEnabledImageProcess`
* `com.day.cq.dam.video.FFMpegThumbnailProcess`
* `com.day.cq.dam.core.process.ThumbnailProcess`
* `com.day.cq.dam.cameraraw.process.CameraRawHandlingProcess`
* `com.day.cq.dam.core.process.CommandLineProcess`
* `com.day.cq.dam.pdfrasterizer.process.PdfRasterizerHandlingProcess`
* `com.day.cq.dam.core.process.AddPropertyWorkflowProcess`
* `com.day.cq.dam.core.process.CreateSubAssetsProcess`
* `com.day.cq.dam.core.process.DownloadAssetProcess`
* `com.day.cq.dam.word.process.ExtractImagesProcess`
* `com.day.cq.dam.word.process.ExtractPlainProcess`
* `com.day.cq.dam.video.FFMpegTranscodeProcess`
* `com.day.cq.dam.ids.impl.process.IDSJobProcess`
* `com.day.cq.dam.indd.process.INDDMediaExtractProcess`
* `com.day.cq.dam.indd.process.INDDPageExtractProcess`
* `com.day.cq.dam.core.impl.lightbox.LightboxUpdateAssetProcess`
* `com.day.cq.dam.pim.impl.sourcing.upload.process.ProductAssetsUploadProcess`
* `com.day.cq.dam.core.process.ScheduledPublishBPProcess`
* `com.day.cq.dam.core.process.ScheduledUnPublishBPProcess`
* `com.day.cq.dam.core.process.SendDownloadAssetEmailProcess`
* `com.day.cq.dam.core.impl.process.SendTransientWorkflowCompletedEmailProcess`

<!-- PPTX source: slide in add-assets.md - overview of direct binary upload section of 
https://adobe-my.sharepoint.com/personal/gklebus_adobe_com/_layouts/15/guestaccess.aspx?guestaccesstoken=jexDC5ZnepXSt6dTPciH66TzckS1BPEfdaZuSgHugL8%3D&docid=2_1ec37f0bd4cc74354b4f481cd420e07fc&rev=1&e=CdgElS
-->

>[!MORELIKETHIS]
* [Experience Cloud [!DNL Cloud Service] 를 SDK로 사용합니다](/help/implementing/developing/introduction/aem-as-a-cloud-service-sdk.md).

