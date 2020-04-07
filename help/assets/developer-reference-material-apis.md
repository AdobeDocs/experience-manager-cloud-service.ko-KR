---
title: '클라우드 서비스로 Adobe Experience Manager의 디지털 에셋 관리를 위한 에셋 API '
description: 자산 API를 사용하면 이진, 메타데이터, 변환, 주석 및 컨텐츠 조각을 비롯한 에셋을 관리하는 기본 CRUD(Create-Read-Update-Delete) 작업을 수행할 수 있습니다.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 26833f59f21efa4de33969b7ae2e782fe5db8a14

---


# Assets as a Cloud Service APIs {#assets-cloud-service-apis}

<!-- 
Give a list of and overview of all reference information available.
* New upload method
* Javadocs
* Assets HTTP API documented at [https://helpx.adobe.com/experience-manager/6-5/assets/using/mac-api-assets.html](https://helpx.adobe.com/experience-manager/6-5/assets/using/mac-api-assets.html)

-->

## 자산 업로드 {#asset-upload-technical}

클라우드 서비스인 Experience Manager는 저장소에 자산을 업로드하는 새로운 방법을 제공합니다. 바이너리 클라우드 스토리지에 직접 이진 업로드가 가능합니다. 이 섹션에서는 기술 개요를 제공합니다.

### 직접 이진 업로드 개요 {#overview-binary-upload}

이진 파일을 업로드하는 상위 수준 알고리즘은 다음과 같습니다.

1. AEM에 새 바이너리를 업로드할 의도를 알리는 HTTP 요청을 제출합니다.
1. 초기화 요청에서 제공하는 하나 이상의 URI에 바이너리의 컨텐츠를 게시합니다.
1. HTTP 요청을 제출하여 바이너리의 내용이 성공적으로 업로드되었음을 서버에 알립니다.

![직접 바이너리 업로드 프로토콜 개요](assets/add-assets-technical.png)

AEM의 이전 버전과 비교할 때 중요한 차이점은 다음과 같습니다.

* 바이너리는 AEM을 통해 이동하지 않습니다. 이 AEM은 이제 배포용으로 구성된 바이너리 클라우드 스토리지를 사용하여 업로드 프로세스를 조정할 수 있습니다
* 바이너리 클라우드 스토리지는 업로드 종단점을 클라이언트에 더 가까이 가져다 주는 컨텐츠 전달 네트워크(CDN, Edge Network)에 의해 앞에 배치되므로 분산된 팀이 자산을 업로드하는 경우 업로드 성능 및 사용자 경험을 향상시킬 수 있습니다

이 접근 방식은 자산 업로드를 보다 확장 가능하고 성능 면에서 처리할 수 있어야 합니다.

> !![NOTE]
이 방법을 구현하는 클라이언트 코드를 검토하려면 오픈 소스 [aem-upload 라이브러리를 참조하십시오.](https://github.com/adobe/aem-upload)

### 업로드 시작 {#initiate-upload}

첫 번째 단계는 자산을 만들거나 업데이트해야 하는 폴더에 HTTP POST 요청을 제출하는 것입니다.선택기를 `.initiateUpload.json` 포함하여 요청이 바이너리 업로드를 시작함을 나타냅니다. 예를 들어 자산을 만들어야 하는 폴더의 경로는 `/assets/folder`다음과 같습니다.

```
POST https://[aem_server]/content/dam/assets/folder.initiateUpload.json
````

요청 본문의 콘텐츠 유형은 `application/x-www-form-urlencoded` 양식 데이터여야 하며 다음 필드를 포함해야 합니다.

* `(string) fileName`: 필수. 인스턴스에 나타날 자산의 이름입니다.
* `(number) fileSize`: 필수. 업로드할 바이너리의 총 길이(바이트)입니다.

각 바이너리에 필수 필드가 포함된 경우 단일 요청을 사용하여 여러 바이너리에 대한 업로드를 시작할 수 있습니다. 성공하면 요청은 `201` 상태 코드와 JSON 데이터가 포함된 본문으로 응답합니다.

```
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

* `completeURI` (문자열):바이너리 업로드를 마치면 이 URI를 호출합니다. URI는 절대 또는 상대 URI일 수 있으며 클라이언트는 둘 중 하나를 처리할 수 있어야 합니다. 즉, 값은 `"https://author.acme.com/content/dam.completeUpload.json"` 전체 업로드가 `"/content/dam.completeUpload.json"` 가능하거나 [전체 업로드를](#complete-upload)참조하십시오.
* `folderPath` (문자열):바이너리가 업로드되는 폴더의 전체 경로입니다.
* `(files)` (배열):길이 및 순서가 시작 요청에 제공된 이진 정보 목록의 길이 및 순서와 일치하는 요소 목록입니다.
* `fileName` (문자열):시작 요청에 제공된 해당 바이너리의 이름입니다. 이 값은 전체 요청에 포함되어야 합니다.
* `mimeType` (문자열):시작 요청에서 제공되는 해당 바이너리의 MIME 유형입니다. 이 값은 전체 요청에 포함되어야 합니다.
* `uploadToken` (문자열):해당 바이너리에 대한 업로드 토큰입니다. 이 값은 전체 요청에 포함되어야 합니다.
* `uploadURIs` (배열):값이 바이너리의 컨텐츠를 업로드해야 하는 전체 URI인 문자열 목록입니다(바이너리 [업로드 참조](#upload-binary)).
* `minPartSize` (숫자):둘 이상의 URI가 있는 경우 uploadURI 중 하나에 제공할 수 있는 데이터의 최소 길이(바이트)입니다.
* `maxPartSize` (숫자):둘 이상의 URI가 있는 경우 uploadURI 중 하나에 제공할 수 있는 데이터의 최대 길이(바이트)입니다.

### 이진 업로드 {#upload-binary}

업로드를 시작하는 출력에는 하나 이상의 업로드 URI 값이 포함됩니다. 두 개 이상의 URI가 제공되는 경우 바이너리를 각 URI로 순서대로 &quot;분할&quot;하고 각 부분을 POST로 분할하는 것이 클라이언트의 책임입니다. 모든 URI를 사용해야 하며 각 부분은 최소 크기보다 크고 시작 응답에 지정된 최대 크기보다 작아야 합니다. 이러한 요청은 바이너리의 업로드를 가속화하기 위해 CDN 에지 노드에 의해 앞에 표시됩니다.

이를 실현하는 한 가지 잠재적 방법은 API에서 제공하는 업로드 URI의 수를 기반으로 부품 크기를 계산하는 것입니다. 이진 파일의 전체 크기가 20,000바이트이고 업로드 URI의 수는 2라고 가정하는 예:

* 전체 크기를 URI 수로 나누어 부품 크기를 계산합니다.20,000 / 2 = 10,000
* POST 바이트 범위 0-9,999의 바이너리를 업로드 URI 목록의 첫 번째 URI로
* POST 바이트 범위 10,000-19,999의 바이너리를 업로드 URI 목록의 두 번째 URI로

성공하면 서버가 각 요청에 응답하고 `201` 상태 코드를 사용합니다.

### 업로드 완료 {#complete-upload}

바이너리의 모든 부분이 업로드되면 최종 단계는 초기화 데이터로 제공된 전체 URI에 HTTP POST 요청을 제출하는 것입니다. 요청 본문의 컨텐츠 유형은 다음 필드를 포함하는 응용 프로그램/`x-www-form-urlencoded` 양식 데이터여야 합니다.

* `(string) fileName`: 필수. 초기화 데이터에 의해 제공된 자산의 이름입니다.
* `(string) mimeType`: 필수. 초기화 데이터에 의해 제공된 바이너리의 HTTP 컨텐츠 유형입니다.
* `(string) uploadToken`: 필수. 초기화 데이터에 의해 제공된 대로 이진 파일에 대한 토큰 업로드
* `(bool) createVersion`: 선택 사항입니다. true이고 지정된 이름의 자산이 이미 존재하는 경우, 인스턴스는 자산의 새 버전을 만듭니다.
* `(string) versionLabel`: 선택 사항입니다. 새 버전이 만들어지면 버전과 연결될 레이블입니다.
* `(string) versionComment`: 선택 사항입니다. 새 버전이 만들어지면 버전과 연결된 댓글입니다.
* `(bool) replace`:선택 사항:true이고 지정된 이름의 자산이 이미 존재하는 경우, 인스턴스는 자산을 삭제한 다음 자산을 다시 만듭니다.

>!![NOTE]
>
> 자산이 이미 존재하며 createVersion이나 바꾸기가 지정되지 않은 경우, 인스턴스는 자산의 현재 버전을 새 바이너리로 업데이트합니다.

시작 프로세스와 마찬가지로 전체 요청 데이터에는 둘 이상의 파일에 대한 정보가 포함될 수 있습니다.

이진 업로드 프로세스는 파일에 대해 전체 URL을 호출할 때까지 수행되지 않습니다. 파일의 바이너리가 전체적으로 업로드되더라도 업로드 프로세스가 완료될 때까지 에셋이 인스턴스별로 처리되지 않습니다.

성공하면 서버가 `200` 상태 코드로 응답합니다.

### 오픈 소스 업로드 라이브러리 {#open-source-upload-library}

업로드 알고리즘에 대해 자세히 알아보거나 자신만의 업로드 스크립트 및 도구를 만들기 위해 Adobe는 오픈 소스 라이브러리 및 도구를 시작점으로 제공합니다.

* [소스 aem 업로드 라이브러리 열기](https://github.com/adobe/aem-upload)
* [오픈 소스 명령줄 툴](https://github.com/adobe/aio-cli-plugin-aem)

### 사용되지 않는 자산 업로드 API {#deprecated-asset-upload-api}

<!-- #ENGCHECK review / update the list of deprecated APIs below -->

>[!NOTE]
Experience Manager를 클라우드 서비스로 사용하는 경우 새로운 업로드 API만 지원됩니다. Experience Manager 6.5의 API는 더 이상 사용되지 않습니다.

자산 또는 표현물(모든 이진 업로드)의 업로드 또는 업데이트와 관련된 메서드는 다음 API에서 더 이상 사용되지 않습니다.

* [AEM Assets HTTP API](mac-api-assets.md)
* `AssetManager` Java API, 좋아요 `AssetManager.createAsset(..)`

>[!MORELIKETHIS]
* [소스 aem 업로드 라이브러리 열기](https://github.com/adobe/aem-upload)
* [오픈 소스 명령줄 툴](https://github.com/adobe/aio-cli-plugin-aem)


## 자산 처리 및 사후 처리 워크플로우 {#post-processing-workflows}

대부분의 자산 처리는 **[!UICONTROL 자산 마이크로서비스별]** 처리 프로필 구성을 기반으로 [](asset-microservices-configure-and-use.md#get-started-using-asset-microservices)실행되며 개발자 익스텐션이 필요하지 않습니다.

사후 처리 워크플로우 구성의 경우 확장 기능이 있는 표준 AEM 워크플로우(예: 사용자 정의 단계를 사용할 수 있음). 자산 사후 처리 워크플로우에서 사용할 수 있는 워크플로우 단계를 이해하려면 다음 하위 섹션을 검토하십시오.

### 사후 처리 워크플로우의 워크플로우 단계 {#post-processing-workflows-steps}

>[!NOTE]
이 섹션은 대부분 이전 버전의 AEM에서 클라우드 서비스로 업데이트되는 고객에게 적용됩니다.

Adobe Experience Manager를 클라우드 서비스로 도입한 새로운 배포 모델로 인해, 자산 마이크로 서비스 도입 전에 워크플로우에서 사용된 특정 워크플로우 단계가 더 이상 지원되지 않을 수 있습니다. `DAM Update Asset` 이러한 구성 요소 대부분은 보다 간단하게 에셋 마이크로 서비스를 구성하고 사용할 수 있도록 대체되었습니다.

다음은 AEM에서 클라우드 서비스로 제공되는 기술 워크플로우 모델 및 지원 수준입니다.

### 지원되는 워크플로우 단계 {#supported-workflow-steps}

다음 워크플로우 단계는 클라우드 서비스에서 지원됩니다.

* `com.day.cq.dam.similaritysearch.internal.workflow.process.AutoTagAssetProcess`
* `com.day.cq.dam.core.impl.process.CreateAssetLanguageCopyProcess`
* `com.day.cq.wcm.workflow.process.CreateVersionProcess`
* `com.day.cq.dam.similaritysearch.internal.workflow.smarttags.StartTrainingProcess`
* `com.day.cq.dam.similaritysearch.internal.workflow.smarttags.TransferTrainingDataProcess`
* `com.day.cq.dam.core.impl.process.TranslateAssetLanguageCopyProcess`
* `com.day.cq.dam.core.impl.process.UpdateAssetLanguageCopyProcess`
* `com.adobe.cq.workflow.replication.impl.ReplicationWorkflowProcess`
* `com.day.cq.dam.core.impl.process.DamUpdateAssetWorkflowCompletedProcess`

### 지원되지 않거나 대체된 모델 {#unsupported-replaced-models}

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
