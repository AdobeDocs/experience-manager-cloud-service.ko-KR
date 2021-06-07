---
title: ' [!DNL Assets]에 대한 개발자 참조'
description: '[!DNL Assets] APIs and developer reference content lets you manage assets, including binary files, metadata, renditions, comments, and [!DNL Content Fragments].'
contentOwner: AG
feature: API,자산 HTTP API
role: Developer,Architect,Administrator
exl-id: c75ff177-b74e-436b-9e29-86e257be87fb
source-git-commit: a446efacb91f1a620d227b9413761dd857089c96
workflow-type: tm+mt
source-wordcount: '1420'
ht-degree: 2%

---

# [!DNL Adobe Experience Manager Assets] 개발자 사용 사례, API 및 참조 자료  {#assets-cloud-service-apis}

이 문서에는 [!DNL Assets] as a [!DNL Cloud Service] 개발자를 위한 권장 사항, 참조 자료 및 리소스가 포함되어 있습니다. 여기에는 새 자산 업로드 모듈, API 참조 및 사후 처리 워크플로우에서 제공하는 지원에 대한 정보가 포함됩니다.

## [!DNL Experience Manager Assets] API 및 작업  {#use-cases-and-apis}

[!DNL Assets] as a [!DNL Cloud Service] 는 프로그래밍 방식으로 디지털 자산과 상호 작용하는 여러 API를 제공합니다. 각 API는 아래 표에 설명된 대로 특정 사용 사례를 지원합니다. [!DNL Assets] 사용자 인터페이스, [!DNL Experience Manager] 데스크탑 앱 및 [!DNL Adobe Asset Link]는 모든 작업 또는 일부를 지원합니다.

>[!CAUTION]
>
>일부 API는 계속 존재하지만 적극적으로 지원되지 않습니다(×로 표시됨). 가능한 한 이러한 API를 사용하지 마십시오.

| 지원 수준 | 설명 |
| ------------- | --------------------------- |
| ✓ | 지원됨 |
| × | 지원되지 않음. 사용하지 마십시오. |
| - | 사용할 수 없음 |

| 사용 사례 | [aem-upload](https://github.com/adobe/aem-upload) | [AEM / Sling / ](https://docs.adobe.com/content/help/en/experience-manager-cloud-service-javadoc/index.html) JCRJava API | [Asset compute 서비스](https://experienceleague.adobe.com/docs/asset-compute/using/extend/understand-extensibility.html) | [[!DNL Assets] HTTP API](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/assets/admin/mac-api-assets.html#create-an-asset) | Sling [GET](https://sling.apache.org/documentation/bundles/rendering-content-default-get-servlets.html) / [POST](https://sling.apache.org/documentation/bundles/manipulating-content-the-slingpostservlet-servlets-post.html) 서블릿 | [GraphQL](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/graphql/overview.html) _(미리 보기)_ |
| ----------------|:---:|:---:|:---:|:---:|:---:|:---:|
| **원본 이진** |  |  |  |  |  |  |
| 원본 만들기 | ✓ | × | - | × | × | - |
| 원본 읽기 | - | × | ✓ | ✓ | ✓ | - |
| 원본 업데이트 | ✓ | × | ✓ | × | × | - |
| 원본 삭제 | - | ✓ | - | ✓ | ✓ | - |
| 원본 복사 | - | ✓ | - | ✓ | ✓ | - |
| 원래 이동 | - | ✓ | - | ✓ | ✓ | - |
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

## 자산 업로드 {#asset-upload}

[!DNL Experience Manager]에서 [!DNL Cloud Service] HTTP API를 사용하여 자산을 클라우드 저장소에 직접 업로드할 수 있습니다. 이진 파일을 업로드하는 단계는 다음과 같습니다. [!DNL Experience Manager] JVM이 아닌 외부 애플리케이션에서 이러한 단계를 실행합니다.

1. [HTTP 요청을 제출합니다](#initiate-upload). 새 바이너리를 업로드하려면 [!DNL Experience Manage]에 대한 배포를 알려 줍니다.
1. [상기 초기화 요청](#upload-binary) 에서 제공하는 하나 이상의 URI에 상기 바이너리의 컨텐츠를 POST.
1. [HTTP 요청](#complete-upload) 을 제출하여 바이너리의 콘텐츠가 성공적으로 업로드되었음을 서버에 알립니다.

![직접 이진 업로드 프로토콜 개요](assets/add-assets-technical.png)

>[!IMPORTANT]
[!DNL Experience Manager] JVM이 아닌 외부 애플리케이션에서 위의 단계를 실행합니다.

이 접근 방법에서는 자산 업로드를 보다 확장 가능하고 성능적으로 처리할 수 있습니다. [!DNL Experience Manager] 6.5와 비교한 차이점은 다음과 같습니다.

* 바이너리는 [!DNL Experience Manager]을 통과하지 않습니다. 이 바이너리는 이제 배포에 대해 구성된 이진 클라우드 저장소로 업로드 프로세스를 조정합니다.
* 이진 클라우드 저장소는 CDN(Content Delivery Network) 또는 Edge 네트워크에서 작동합니다. CDN은 클라이언트에 가까운 업로드 끝점을 선택합니다. 특히 지리적으로 분산된 팀의 경우, 데이터가 가까운 종단점으로 더 짧은 거리를 이동하는 경우 업로드 성능 및 사용자 경험이 향상됩니다.

>[!NOTE]
오픈 소스 [aem-upload 라이브러리](https://github.com/adobe/aem-upload)에서 이 접근 방식을 구현하려면 클라이언트 코드 를 참조하십시오.

### 업로드 시작 {#initiate-upload}

원하는 폴더에 HTTP POST 요청을 제출합니다. 자산이 이 폴더에서 만들어지거나 업데이트됩니다. 선택기 `.initiateUpload.json`을(를) 포함하여 요청이 바이너리 파일의 업로드를 시작한다는 것을 나타냅니다. 예를 들어 자산을 만들어야 하는 폴더의 경로는 `/assets/folder`입니다. POST 요청은 `POST https://[aem_server]:[port]/content/dam/assets/folder.initiateUpload.json`입니다.

요청 본문의 컨텐츠 유형은 `application/x-www-form-urlencoded` 양식 데이터여야 하며, 다음 필드를 포함합니다.

* `(string) fileName`: 필수. [!DNL Experience Manager]에 표시되는 자산의 이름입니다.
* `(number) fileSize`: 필수. 업로드되는 자산의 파일 크기(바이트)입니다.

각 바이너리에 필수 필드가 포함된 한 단일 요청을 사용하여 여러 바이너리에 대한 업로드를 시작할 수 있습니다. 성공하면 요청이 `201` 상태 코드와 JSON 데이터가 포함된 본문으로 응답합니다.

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

* `completeURI` (문자열):바이너리의 업로드를 마치면 이 URI를 호출합니다. URI는 절대 또는 상대 URI일 수 있으며 클라이언트는 둘 중 하나를 처리할 수 있어야 합니다. 즉, 값은 `"https://author.acme.com/content/dam.completeUpload.json"` 또는 `"/content/dam.completeUpload.json"`완료 업로드](#complete-upload)를 참조하십시오.[
* `folderPath` (문자열):바이너리가 업로드된 폴더의 전체 경로입니다.
* `(files)` (배열):시작 요청에서 제공된 이진 정보 목록의 길이 및 순서와 일치하는 요소의 목록입니다.
* `fileName` (문자열):시작 요청에서 제공된 해당 바이너리의 이름입니다. 이 값은 전체 요청에 포함해야 합니다.
* `mimeType` (문자열):시작 요청에서 제공된 해당 바이너리의 MIME 유형입니다. 이 값은 전체 요청에 포함해야 합니다.
* `uploadToken` (문자열):해당 바이너리에 대한 업로드 토큰. 이 값은 전체 요청에 포함해야 합니다.
* `uploadURIs` (배열):값이 전체 URI인 문자열 목록으로서, 바이너리 컨텐츠를 업로드해야 합니다( [이진 업로드](#upload-binary) 참조).
* `minPartSize` (숫자):둘 이상의 URI가 있는  `uploadURIs`경우 모든 URI에 제공할 수 있는 데이터의 최소 길이(바이트)입니다.
* `maxPartSize` (숫자):둘 이상의 URI가 있는  `uploadURIs`경우 모든 URI에 제공할 수 있는 데이터의 최대 길이(바이트)입니다.

### 이진 {#upload-binary} 업로드

업로드 시작 출력에는 하나 이상의 업로드 URI 값이 포함됩니다. 두 개 이상의 URI가 제공되면 클라이언트는 바이너리를 부품으로 분할하고 각 부품의 POST 요청을 순서대로 각 URI에 요청합니다. 모든 URI를 사용합니다. 각 부품의 크기가 시작 응답에 지정된 최소 및 최대 크기 내에 있는지 확인합니다. CDN 에지 노드는 요청된 바이너리 업로드 속도를 높이는 데 도움이 됩니다.

API에서 제공하는 업로드 URI 수에 따라 부품 크기를 계산하는 것이 이를 수행하는 가능한 방법입니다. 예를 들어 바이너리의 총 크기는 20,000바이트이고 업로드 URI 수는 2라고 가정합니다. 그런 다음 다음 단계를 수행합니다.

* 총 크기를 URI 수로 나누어 부품 크기 계산:20,000 / 2 = 10,000.
* POST 바이트 범위는 바이너리의 0-9,999이며 업로드 URI 목록의 첫 번째 URI입니다.
* 업로드 URI 목록의 두 번째 URI에 대한 POST 바이트 범위는 10,000 - 19,999입니다.

업로드가 성공적으로 수행되면 서버는 `201` 상태 코드로 각 요청에 응답합니다.

### 업로드 완료 {#complete-upload}

이진 파일의 모든 부분을 업로드한 후 HTTP POST 요청을 시작 데이터에서 제공한 전체 URI에 제출합니다. 요청 본문의 콘텐츠 유형은 `application/x-www-form-urlencoded` 양식 데이터여야 하며, 다음 필드를 포함합니다.

| 필드 | 유형 | 필수 여부 | 설명 |
|---|---|---|---|
| `fileName` | 문자열 | 필수 | 초기화 데이터에서 제공한 자산의 이름입니다. |
| `mimeType` | 문자열 | 필수 | 시작 데이터에서 제공한 바이너리의 HTTP 컨텐츠 유형입니다. |
| `uploadToken` | 문자열 | 필수 | 시작 데이터에서 제공한 대로 바이너리에 대한 업로드 토큰. |
| `createVersion` | 부울 | 선택 사항입니다 | `True` 과 지정된 이름의 자산이 있으면 [!DNL Experience Manager] 에서는 자산의 새 버전을 만듭니다. |
| `versionLabel` | 문자열 | 선택 사항입니다 | 새 버전이 만들어지면 자산의 새 버전과 연결된 레이블 . |
| `versionComment` | 문자열 | 선택 사항입니다 | 새 버전을 만들면 버전과 연관된 주석이 됩니다. |
| `replace` | 부울 | 선택 사항입니다 | `True` 과 지정된 이름의 자산이 있는 경우 [!DNL Experience Manager] 은 자산을 삭제한 다음 다시 만듭니다. |

>[!NOTE]
자산이 있고 `createVersion` 및 `replace`이 지정되지 않은 경우 [!DNL Experience Manager] 는 자산의 현재 버전을 새 바이너리로 업데이트합니다.

시작 프로세스처럼 전체 요청 데이터에는 두 개 이상의 파일에 대한 정보가 포함될 수 있습니다.

파일에 대한 전체 URL이 호출될 때까지 바이너리를 업로드하는 프로세스가 수행되지 않습니다. 업로드 프로세스가 완료되면 자산이 처리됩니다. 자산의 이진 파일이 완전히 업로드되었지만 업로드 프로세스가 완료되지 않은 경우에도 처리가 시작되지 않습니다.

성공하면 서버가 `200` 상태 코드로 응답합니다.

### 오픈 소스 업로드 라이브러리 {#open-source-upload-library}

업로드 알고리즘에 대해 자세히 알아보고 또는 업로드 스크립트와 도구를 직접 빌드하기 위해 Adobe은 오픈 소스 라이브러리 및 도구를 제공합니다.

* [오픈 소스 aem-upload 라이브러리](https://github.com/adobe/aem-upload).
* [오픈 소스 명령줄 도구](https://github.com/adobe/aio-cli-plugin-aem).

### 자산 업로드 API 삭제 {#deprecated-asset-upload-api}

<!-- #ENGCHECK review / update the list of deprecated APIs below. -->

새 업로드 방법은 [!DNL Adobe Experience Manager]에 대해서만 [!DNL Cloud Service] 로서 지원됩니다. [!DNL Adobe Experience Manager] 6.5의 API는 더 이상 사용되지 않습니다. 자산 또는 표현물 업로드 또는 업데이트와 관련된 메서드(모든 이진 업로드)는 다음 API에서 더 이상 사용되지 않습니다.

* [자산 Experience Manager HTTP API](mac-api-assets.md)
* `AssetManager` 와 같은 Java API  `AssetManager.createAsset(..)`

>[!MORELIKETHIS]
* [오픈 소스 aem-upload 라이브러리](https://github.com/adobe/aem-upload).
* [오픈 소스 명령줄 도구](https://github.com/adobe/aio-cli-plugin-aem).


## 자산 처리 및 사후 처리 워크플로우 {#post-processing-workflows}

[!DNL Experience Manager]에서 자산 처리는 [자산 마이크로서비스](asset-microservices-configure-and-use.md#get-started-using-asset-microservices)를 사용하는 **[!UICONTROL 처리 프로필]** 구성을 기반으로 합니다. 처리할 때는 개발자 확장이 필요하지 않습니다.

사후 처리 워크플로우 구성의 경우 사용자 지정 단계와 함께 확장이 있는 표준 워크플로우를 사용합니다.

## 사후 처리 워크플로우에서 워크플로우 단계 지원 {#post-processing-workflows-steps}

이전 버전의 [!DNL Experience Manager]에서 업그레이드하는 고객은 자산 마이크로서비스를 사용하여 자산을 처리할 수 있습니다. 클라우드 기반의 자산 마이크로서비스 는 구성 및 사용이 훨씬 간단합니다. 이전 버전의 [!UICONTROL DAM 자산 업데이트] 워크플로우에서 사용되는 몇 가지 워크플로우 단계는 지원되지 않습니다.

[!DNL Experience Manager] 는 다음  [!DNL Cloud Service] 워크플로우 단계를 지원합니다.

* `com.day.cq.dam.similaritysearch.internal.workflow.process.AutoTagAssetProcess`
* `com.day.cq.dam.core.impl.process.CreateAssetLanguageCopyProcess`
* `com.day.cq.wcm.workflow.process.CreateVersionProcess`
* `com.day.cq.dam.similaritysearch.internal.workflow.smarttags.StartTrainingProcess`
* `com.day.cq.dam.similaritysearch.internal.workflow.smarttags.TransferTrainingDataProcess`
* `com.day.cq.dam.core.impl.process.TranslateAssetLanguageCopyProcess`
* `com.day.cq.dam.core.impl.process.UpdateAssetLanguageCopyProcess`
* `com.adobe.cq.workflow.replication.impl.ReplicationWorkflowProcess`
* `com.day.cq.dam.core.impl.process.DamUpdateAssetWorkflowCompletedProcess`

다음 기술 워크플로우 모델은 자산 마이크로서비스로 대체되거나 지원되지 않습니다.

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
* [[!DNL Experience Cloud] as a [!DNL Cloud Service] SDK](/help/implementing/developing/introduction/aem-as-a-cloud-service-sdk.md).

