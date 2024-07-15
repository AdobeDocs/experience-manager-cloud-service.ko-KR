---
title: 디지털 자산을  [!DNL Adobe Experience Manager]에 추가합니다.
description: 디지털 자산을  [!DNL Adobe Experience Manager] as a [!DNL Cloud Service]에 추가하십시오.
feature: Asset Ingestion, Asset Management, Asset Processing, Upload
role: User, Admin
exl-id: 0e624245-f52e-4082-be21-13cc29869b64
source-git-commit: ab2cf8007546f538ce54ff3e0b92bb0ef399c758
workflow-type: tm+mt
source-wordcount: '3144'
ht-degree: 9%

---

# 디지털 자산을 [!DNL Adobe Experience Manager]에 [!DNL Cloud Service] [!DNL Assets](으)로 추가 {#add-assets-to-experience-manager}

[!DNL Adobe Experience Manager Assets]은(는) 다양한 소스의 다양한 디지털 에셋을 허용합니다. 바이너리와 생성된 렌디션을 저장하고, 다양한 워크플로우 및 [!DNL Adobe Sensei] 서비스를 사용하여 에셋 처리를 수행할 수 있으며, 여러 표면에 걸쳐 다양한 채널을 통해 배포할 수 있습니다.

[!DNL Adobe Experience Manager]은(는) 풍부한 메타데이터, 스마트 태그, 렌디션 및 기타 DAM(디지털 에셋 관리) 서비스를 통해 업로드된 디지털 파일의 바이너리 콘텐츠를 강화합니다. 로컬 폴더 또는 네트워크 드라이브에서 [!DNL Experience Manager Assets](으)로 이미지, 문서 및 원시 이미지 파일과 같은 다양한 유형의 파일을 업로드할 수 있습니다.

가장 일반적으로 사용되는 브라우저 업로드 외에 다른 방법으로 [!DNL Experience Manager] 저장소에 에셋을 추가할 수 있습니다. 이러한 다른 방법에는 Asset Link Adobe 또는 [!DNL Experience Manager] 데스크톱 앱과 같은 데스크톱 클라이언트, 고객이 만들 업로드 및 수집 스크립트, [!DNL Experience Manager] 확장으로 추가된 자동화된 수집 통합 등이 있습니다.

[!DNL Experience Manager]에서 모든 이진 파일을 업로드하고 관리할 수 있지만, 가장 일반적으로 사용되는 파일 형식은 메타데이터 추출 또는 미리 보기/렌디션 생성과 같은 추가 서비스를 지원합니다. 자세한 내용은 [지원되는 파일 형식](file-format-support.md)을 참조하십시오.

업로드된 에셋에 대해 추가 처리를 수행하도록 선택할 수도 있습니다. 에셋이 업로드되는 폴더에 여러 에셋 처리 프로필을 구성하여 특정 메타데이터, 렌디션 또는 이미지 처리 서비스를 추가할 수 있습니다. [업로드할 때 자산 처리](#process-when-uploaded)를 참조하세요.

[!DNL Assets]에서 제공하는 업로드 방법은 다음과 같습니다. Adobe은 업로드 옵션을 사용하기 전에 사용 사례와 업로드 옵션의 적용 가능성을 이해하는 것을 권장합니다.

| 업로드 방법 | 사용 시기 | 기본 담당자 |
|---------------------|----------------|-----------------|
| [Assets 콘솔 사용자 인터페이스](#upload-assets) | 가끔 업로드, 누르기 및 끌기, 찾기 업로드. 를 사용하여 많은 에셋을 업로드하지 마십시오. | 모든 사용자 |
| [API 업로드](#upload-using-apis) | 업로드 중 다이내믹 의사 결정용. | 개발자 |
| [[!DNL Experience Manager] 데스크탑 앱](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html) | 낮은 볼륨 에셋 수집이지만 마이그레이션용은 아닙니다. | 관리자, 마케터 |
| [[!DNL Adobe Asset Link]](https://helpx.adobe.com/kr/enterprise/using/adobe-asset-link.html) | 크리에이티브 및 마케터가 지원되는 [!DNL Creative Cloud] 데스크톱 앱 내에서 자산에 대해 작업할 때 유용합니다. | 크리에이티브, 마케터 |
| [일괄 에셋 수집기](#asset-bulk-ingestor) | 대규모 마이그레이션 및 경우에 따라 대량으로 수집하는 경우에 권장됩니다. 지원되는 데이터 저장소에만 해당됩니다. | 관리자, 개발자 |

## 자산 업로드 {#upload-assets}

<!-- #ENGCHECK do we support pausing? I couldn't get pause to show with 1.5GB upload.... If not, this should be removed#

   You can pause the uploading of large assets (greater than 500 MB) and resume it later from the same page. Select the **[!UICONTROL Pause]** icon beside progress bar that appears when an upload starts.

   The size above which an asset is considered a large asset is configurable. For example, you can configure the system to consider assets above 1000 MB (instead of 500 MB) as large assets. In this case, **[!UICONTROL Pause]** appears on the progress bar when assets of size greater than 1000 MB are uploaded.

   The [!UICONTROL Pause] option does not show if a file greater than 1000 MB is uploaded with a file less than 1000 MB. However, if you cancel the less than 1000 MB file upload, the **[!UICONTROL Pause]** option appears.

   To modify the size limit, configure the `chunkUploadMinFileSize` property of the `fileupload` node in the CRX repository.

   When you click the **[!UICONTROL Pause]** icon, it toggles to a **[!UICONTROL Play]** icon. To resume uploading, click **[!UICONTROL Play]** option.
-->

<!-- #ENGCHECK do we support pausing? I couldn't get pause to show with 1.5GB upload.... If not, this should be removed#
   The ability to resume uploading is especially helpful in low-bandwidth scenarios and network glitches, where it takes a long time to upload a large asset. You can pause the upload operation and continue later when the situation improves. When you resume, uploading starts from the point where you paused it.
-->

<!-- #ENGCHECK assuming this is not relevant? remove after confirming#
   During the upload operation, [!DNL Experience Manager] saves the portions of the asset being uploaded as chunks of data in the CRX repository. When the upload completes, [!DNL Experience Manager] consolidates these chunks into a single block of data in the repository.

   To configure the cleanup task for the unfinished chunk upload jobs, go to `https://[aem_server]:[port]/system/console/configMgr/org.apache.sling.servlets.post.impl.helper.ChunkCleanUpTask`.
-->

파일(또는 여러 파일)을 업로드하려면 바탕 화면에서 선택하고 사용자 인터페이스(웹 브라우저)를 대상 폴더로 드래그하면 됩니다. 또는 사용자 인터페이스에서 업로드를 시작할 수 있습니다.

>[!IMPORTANT]
>
>파일 이름이 100자보다 큰 Experience Manager에 업로드하는 Assets을 Dynamic Media에서 사용할 때 이름이 단축됩니다.
>
>파일 이름의 처음 100자는 그대로 사용되고, 나머지 문자는 영숫자 문자열로 대체됩니다. 이 이름 변경 방법은 Dynamic Media에서 자산을 사용할 때 고유한 이름을 보장합니다. 또한 Dynamic Media에서 허용되는 최대 에셋 파일 이름 길이를 수용하기 위한 것입니다.


1. [!DNL Assets] 사용자 인터페이스에서 디지털 자산을 추가할 위치로 이동합니다.
1. 에셋을 업로드하려면 다음 중 하나를 수행하십시오.

   * 도구 모음에서 **[!UICONTROL 만들기]** > **[!UICONTROL 파일]**&#x200B;을 클릭합니다. 필요한 경우 제공된 대화 상자에서 파일 이름을 변경할 수 있습니다.
   * HTML5를 지원하는 브라우저에서 [!DNL Assets] 사용자 인터페이스에서 직접 자산을 끌어 옵니다. 파일 이름을 바꾸는 대화 상자가 표시되지 않습니다.

   ![create_menu](assets/create_menu.png)

   여러 파일을 선택하려면 `Ctrl` 또는 `Command` 키를 선택하고 파일 선택 대화 상자에서 자산을 선택합니다. iPad을 사용하는 경우 한 번에 하나의 파일만 선택할 수 있습니다.

1. 진행 중인 업로드를 취소하려면 진행률 표시줄 옆의 닫기(`X`)를 클릭합니다. 업로드 작업을 취소하면 [!DNL Assets]이(가) 부분적으로 업로드된 에셋 부분을 삭제합니다.
파일을 업로드하기 전에 업로드 작업을 취소하면 [!DNL Assets]에서 현재 파일의 업로드를 중지하고 콘텐츠를 새로 고칩니다. 그러나 이미 업로드된 파일은 삭제되지 않습니다.

1. [!DNL Assets]의 업로드 진행 대화 상자에 업로드한 파일과 업로드에 실패한 파일의 수가 표시됩니다.
또한 [!DNL Assets] 사용자 인터페이스에는 업로드한 가장 최근 에셋 또는 처음 만든 폴더가 표시됩니다.

>[!NOTE]
>
>중첩된 폴더 계층을 업로드하려면 [자산 일괄 업로드](#bulk-upload)를 참조하십시오.

<!-- #ENGCHECK I'm assuming this is no longer relevant.... If yes, this should be removed#

### Serial uploads {#serialuploads}

Uploading numerous assets in bulk consumes significant I/O resources, which may adversely impact the performance of [!DNL Assets]. In particular, if you have a slow internet connection, the time to upload drastically increases due to a spike in disk I/O. Moreover, your web browser may introduce additional restrictions to the number of POST requests [!DNL Assets] can handle for concurrent asset uploads. As a result, the upload operation fails or terminate prematurely. In other words, [!DNL Assets] may miss some files while ingesting a bunch of files or altogether fail to ingest any file.

To overcome this situation, [!DNL Assets] ingests one asset at a time (serial upload) during a bulk upload operation, instead of the concurrently ingesting all the assets.

Serial uploading of assets is enabled by default. To disable the feature and allow concurrent uploading, overlay the `fileupload` node in CRX-DE and set the value of the `parallelUploads` property to `true`.

### Streamed uploads {#streamed-uploads}

If you upload many assets to [!DNL Experience Manager], the I/O requests to server increase drastically, which reduces the upload efficiency and can even cause some upload task to time out. [!DNL Assets] supports streamed uploading of assets. Streamed uploading reduces the disk I/O during the upload operation by avoiding asset storage in a temporary folder on the server before copying it to the repository. Instead, the data is transferred directly to the repository. This way, the time to upload large assets and the possibility of timeouts is reduced. Streamed upload is enabled by default in [!DNL Assets].

>[!NOTE]
>
>Streaming upload is disabled for [!DNL Experience Manager] running on JEE server with servlet-api version lower than 3.1.
-->

### 기존 에셋에 대한 업로드 처리 {#handling-upload-existing-file}

기존 에셋과 동일한 경로(동일한 이름 및 동일한 위치)로 에셋을 업로드할 수 있습니다. 그러나 다음 옵션이 포함된 경고 대화 상자가 표시됩니다.

* 기존 에셋 바꾸기: 기존 에셋을 바꾸는 경우, 에셋에 대한 메타데이터와 기존 에셋에 대해 이전에 수정한 모든 사항(예: 주석 및 자르기)이 삭제됩니다.

  >[!NOTE]
  >
  >에셋이 잠겨 있거나 체크 아웃된 경우 에셋 바꾸기 옵션을 사용할 수 없습니다.

* 다른 버전 만들기: 기존 에셋의 새 버전이 저장소에 생성됩니다. [!UICONTROL 타임라인]에서 두 버전을 볼 수 있으며 필요한 경우 기존 버전으로 되돌릴 수 있습니다.
* 둘 다 유지: 두 에셋을 모두 유지하도록 선택하면 새 에셋의 이름이 변경됩니다.

[!DNL Assets]에서 중복 자산을 유지하려면 **[!UICONTROL 보관]**&#x200B;을 클릭하세요. 업로드한 중복 에셋을 삭제하려면 **[!UICONTROL 삭제]**&#x200B;를 클릭합니다.

### 파일 이름 처리 및 금지된 문자 {#filename-handling}

[!DNL Experience Manager Assets]을(를) 사용하면 해당 파일 이름에 금지된 문자가 있는 자산을 업로드할 수 없습니다. 허용되지 않는 문자 또는 그 이상의 문자가 들어 있는 파일 이름을 사용하여 에셋을 업로드하려고 하면 [!DNL Assets]에 경고 메시지가 표시되고, 이러한 문자를 제거하거나 허용되는 이름으로 업로드할 때까지 업로드를 중지합니다.

조직의 특정 파일 이름 지정 규칙에 맞게 [!UICONTROL Assets 업로드] 대화 상자를 사용하면 업로드하는 파일의 긴 이름을 지정할 수 있습니다. 공백으로 구분된 다음 문자는 지원되지 않습니다.

* 자산 이름에 잘못된 문자: `* / : [ \\ ] | # % { } ? &`
* 자산 폴더 이름에 잘못된 문자: `* / : [ \\ ] | # % { } ? \" . ^ ; + & \t`

## 자산 일괄 업로드 {#bulk-upload}

일괄 에셋 수집기는 많은 에셋을 효율적으로 처리할 수 있습니다. 그러나 대규모 수집은 광범위한 파일 덤프나 일상적인 마이그레이션이 아닙니다. 대규모 수집이 비즈니스 목적에 맞고 효율적인 의미 있는 프로젝트가 되도록 하려면 마이그레이션을 계획하고 자산 조직을 조정하십시오. 모든 수집은 서로 다르므로 일반화하는 대신 세부 저장소 구성 및 비즈니스 요구 사항을 고려합니다. 다음은 일괄 수집을 계획하고 실행하는 몇 가지 중요한 제안입니다.

* 에셋 조정: DAM에 필요하지 않은 에셋을 제거합니다. 사용되지 않거나, 더 이상 사용되지 않거나, 중복된 에셋을 제거하는 것이 좋습니다. 이러한 하우스키핑은 전송된 데이터와 수집된 자산을 줄여 수집 속도를 높입니다.
* 에셋 구성: 파일 크기, 파일 형식, 사용 사례 또는 우선 순위별로 콘텐츠를 논리적 순서로 구성하는 것이 좋습니다. 일반적으로 큰 복잡한 파일은 처리가 더 많이 필요합니다. 파일 크기 필터링 옵션(아래에 설명)을 사용하여 큰 파일을 별도로 수집하는 것도 고려해 볼 수 있습니다.
* 시차를 두는 수집: 수집을 여러 일괄 수집 프로젝트로 나누는 것을 고려하십시오. q를 사용하면 콘텐츠를 더 빨리 보고 필요에 따라 수집을 업데이트할 수 있습니다. 예를 들어 사용량이 적은 시간 동안 또는 점진적으로 여러 청크로 처리 집약적인 에셋을 수집할 수 있습니다. 그러나 한 번에 많은 처리가 필요하지 않은 더 작고 간단한 에셋을 수집할 수 있습니다.

더 많은 수의 파일을 업로드하려면 다음 방법 중 하나를 사용하십시오. [사용 사례 및 메서드](#upload-methods-comparison)도 참조하세요.

* [자산 업로드 API](developer-reference-material-apis.md#asset-upload): 필요한 경우 API를 사용하는 사용자 지정 업로드 스크립트나 도구를 사용하여 자산의 추가 처리를 추가합니다(예: 메타데이터 번역 또는 파일 이름 바꾸기).
* [[!DNL Experience Manager] 데스크톱 앱](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html): 로컬 파일 시스템에서 에셋을 업로드하는 크리에이티브 전문가 및 마케터에게 유용합니다. 로컬에서 사용할 수 있는 중첩된 폴더를 업로드하는 데 사용합니다.
* [일괄 수집 도구](#asset-bulk-ingestor): [!DNL Experience Manager]을(를) 배포할 때 가끔 또는 처음에 대량의 자산을 수집하는 데 사용합니다.

### 일괄 에셋 가져오기 도구 {#asset-bulk-ingestor}

이 도구는 Azure 또는 S3 데이터 저장소에서 대규모 에셋을 수집하는 데 사용할 관리자 그룹에만 제공됩니다. 구성 및 수집에 대한 자세한 내용은 비디오를 참조하십시오.

>[!VIDEO](https://video.tv.adobe.com/v/329680/?quality=12&learn=on)

다음 이미지는 데이터 저장소에서 Experience Manager으로 에셋을 수집할 때의 다양한 단계를 보여줍니다.

![일괄 수집 도구](assets/bulk-ingestion.png)

**전제 조건**

이 기능을 사용하려면 Azure 또는 AWS의 외부 저장소 계정이나 버킷이 필요합니다.

>[!NOTE]
>
>저장소 계정 컨테이너 또는 버킷을 비공개로 만들고 승인된 요청으로부터의 연결만 수락합니다. 그러나 인그레스 네트워크 연결에 대한 추가 제한 사항은 지원되지 않습니다.

>[!NOTE]
>
>외부 저장소 계정의 파일/폴더 이름 규칙은 일괄 가져오기 도구와 다를 수 있습니다. 허용되지 않는/이스케이프 처리된 이름에 대한 자세한 내용은 [일괄 가져오기 중 파일 이름 처리](#filename-handling-bulkimport)를 참조하십시오.


### 일괄 가져오기 도구 구성 {#configure-bulk-ingestor-tool}

일괄 가져오기 도구를 구성하려면 다음 단계를 수행합니다.

1. **[!UICONTROL 도구]** > **[!UICONTROL Assets]** > **[!UICONTROL 일괄 가져오기]**&#x200B;로 이동합니다. **[!UICONTROL 만들기]** 옵션을 선택하십시오.

1. **[!UICONTROL 제목]** 필드에 대량 가져오기 구성의 제목을 지정합니다.

1. **[!UICONTROL Source 가져오기]** 드롭다운 목록에서 데이터 원본 유형을 선택합니다.

1. 데이터 소스와의 연결을 만드는 데 사용할 값을 제공합니다. 예를 들어 **Azure Blob 저장소**&#x200B;를 데이터 소스로 선택하는 경우 Azure 저장소 계정, Azure Blob 컨테이너 및 Azure 액세스 키의 값을 지정하십시오.

1. 드롭다운 목록에서 필요한 인증 모드를 선택합니다. **Azure 액세스 키**&#x200B;에서는 Azure 저장소 계정에 대한 전체 액세스를 제공하는 반면, **Azure SAS 토큰**&#x200B;에서는 관리자가 권한 및 만료 정책을 사용하여 토큰의 기능을 제한할 수 있습니다.

1. **[!UICONTROL 소스 폴더]** 필드에 데이터 소스의 자산이 포함된 루트 폴더의 이름을 입력합니다.

1. (선택 사항) **[!UICONTROL 최소 크기별 필터링]** 필드의 수집 프로세스에 에셋을 포함할 최소 파일 크기(MB)를 제공합니다.

1. (선택 사항) 자산의 최대 파일 크기(MB)를 제공하여 **[!UICONTROL 최대 크기로 필터링]** 필드의 수집 프로세스에 자산을 포함시킵니다.

1. (선택 사항) **[!UICONTROL MIME 유형 제외]** 필드에서 수집에서 제외할 MIME 유형의 쉼표로 구분된 목록을 지정합니다. 예, `image/jpeg, image/.*, video/mp4`. [지원되는 모든 파일 형식](/help/assets/file-format-support.md)을 참조하세요.

1. **[!UICONTROL MIME 유형 포함]** 필드의 수집에서 포함할 MIME 유형의 쉼표로 구분된 목록을 지정하십시오. [지원되는 모든 파일 형식](/help/assets/file-format-support.md)을 참조하세요.

1. 파일을 [!DNL Experience Manager](으)로 가져온 후 원본 데이터 저장소에서 원본 파일을 삭제하려면 **[!UICONTROL 가져온 후 원본 파일 삭제]** 옵션을 선택하십시오.

1. **[!UICONTROL 가져오기 모드]**&#x200B;를 선택합니다. **건너뛰기**, **바꾸기** 또는 **버전 만들기**&#x200B;를 선택합니다. 건너뛰기 모드가 기본값이며 이 모드에서는 에셋이 이미 있는 경우 수집기가 건너뜁니다. [바꾸기 및 버전 만들기 옵션](#handling-upload-existing-file)의 의미를 확인합니다.

1. **[!UICONTROL 자산 대상 폴더]** 필드를 사용하여 자산을 가져올 수 있는 DAM에 위치를 정의하려면 경로를 지정합니다. 예: `/content/dam/imported_assets`

1. (선택 사항) **[!UICONTROL 메타데이터 파일]** 필드에서 가져올 메타데이터 파일(CSV 형식으로 제공)을 지정합니다. 소스 Blob 위치에 CSV 파일을 지정하고 일괄 가져오기 도구를 구성하는 동안 경로를 참조하십시오. 이 필드에서 참조되는 CSV 파일 형식은 [자산 메타데이터를 일괄로 가져오기 및 내보내기](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/admin/metadata-import-export.html)할 때 CSV 파일 형식과 동일합니다. **가져오기 후 소스 파일 삭제** 옵션을 선택한 경우 **제외** 또는 **MIME 유형 포함** 또는 **경로/파일별 필터링** 필드를 사용하여 CSV 파일을 필터링하십시오. 정규 표현식을 사용하여 이러한 필드의 CSV 파일을 필터링할 수 있습니다.

1. 구성을 저장하려면 **[!UICONTROL 저장]**&#x200B;을 클릭하세요.

### 일괄 가져오기 도구 구성 관리 {#manage-bulk-import-configuration}

일괄 가져오기 도구 구성을 만든 후 Experience Manager 인스턴스로 에셋을 일괄 수집하기 전에 구성을 평가하는 작업을 수행할 수 있습니다. 일괄 가져오기 도구 구성을 관리하는 사용 가능한 옵션을 보려면 **[!UICONTROL 도구]** > **[!UICONTROL Assets]** > **[!UICONTROL 일괄 가져오기]**&#x200B;에서 사용 가능한 구성을 선택하십시오.

### 구성 편집 {#edit-configuration}

구성 세부 정보를 편집하려면 구성을 선택한 다음 **[!UICONTROL 편집]**&#x200B;을 클릭합니다. 편집 작업을 수행하는 동안에는 구성 및 가져오기 데이터 소스의 제목을 편집할 수 없습니다.

### 구성 삭제 {#delete-configuration}

대량 가져오기 구성을 삭제하려면 구성을 선택하고 **[!UICONTROL 삭제]**&#x200B;를 클릭하십시오.

### 데이터 소스에 대한 연결 확인 {#validate-connection}

데이터 원본에 대한 연결의 유효성을 검사하려면 구성을 선택한 다음 **[!UICONTROL 확인]**&#x200B;을 클릭합니다. 연결에 성공하면 Experience Manager에 다음 메시지가 표시됩니다.

![일괄 가져오기 성공 메시지](assets/bulk-import-success-message.png)

### 대량 가져오기 작업에 대한 테스트 실행 호출 {#invoke-test-run-bulk-import}

구성을 선택하고 **[!UICONTROL 시험 실행]**&#x200B;을 클릭하여 일괄 가져오기 작업에 대한 테스트 실행을 호출합니다. Experience Manager은 일괄 가져오기 작업에 대한 다음 세부 정보를 표시합니다.

![시험 실행 결과](assets/dry-assets-result.png)

### 일괄 가져오기 도중 파일 이름 처리 {#filename-handling-bulkimport}

자산이나 폴더를 대량으로 가져올 때 [!DNL Experience Manager Assets]는 가져오기 소스에 존재하는 전체 구조를 가져옵니다. [!DNL Experience Manager]는 자산 및 폴더 이름의 특수 문자에 대해 내장된 규칙을 따르므로 이러한 파일 이름을 정리해야 합니다. 폴더 이름과 자산 이름 모두 사용자가 정의한 제목은 변경되지 않으며 `jcr:title`에 저장됩니다.

일괄 가져오기 도중 [!DNL Experience Manager]는 자산과 폴더를 다시 가져오는 것을 방지하기 위해 기존 폴더를 찾고, 가져오기가 수행되는 상위 폴더에 적용된 정리 규칙도 확인합니다. 정리 규칙이 상위 폴더에 적용되면 가져오기 소스에도 동일한 규칙이 적용됩니다. 새로운 가져오기의 경우 자산 및 폴더의 파일 이름을 관리하기 위해 다음과 같은 정리 규칙이 적용됩니다.

**일괄 가져오기에서 허용되지 않는 이름**

파일 및 폴더 이름에는 다음 문자를 사용할 수 없습니다.

* 제어 및 전용 사용 문자(0x00 ~ 0x1F, \u0081, \uE000)
* 점(.)으로 끝나는 파일 또는 폴더 이름

이름이 이러한 조건과 일치하는 파일 또는 폴더는 가져오기 프로세스 중에 건너뛰고 실패로 표시됩니다.

**일괄 가져오기에서 자산 이름 처리**

자산 파일 이름의 경우 JCR 이름 및 경로는 API `JcrUtil.escapeIllegalJcrChars`을(를) 사용하여 정리됩니다.

* 유니코드 문자는 변경되지 않음
* 특수 문자를 URL 이스케이프 코드로 바꿉니다. 예를 들어 `new%asset.png`이(가) `new%25asset.png`(으)로 업데이트되었습니다.

  ```
                  URL escape code   
  
  "               %22
  %               %25
  '               %27
  *               %2A
  /               %2F
  :               %3A
  [               %5B
  \n              %0A
  \r              %0D
  \t              %09
  ]               %5D
  |               %7C
  ```

**일괄 가져오기에서 폴더 이름 처리**

폴더 파일 이름의 경우 JCR 이름 및 경로는 API `DamUtil.getSanitizedFolderName`을(를) 사용하여 정리됩니다.

* 대문자는 소문자로 변환됨
* 유니코드 문자는 변경되지 않음
* 예를들어, `new folder`이(가) `new-folder`(으)로 업데이트되었습니다.

  ```
  "                           
  #                         
  %                           
  &                          
  *                           
  +                          
  .                           
  :                           
  ;                          
  ?                          
  [                           
  ]                           
  ^                         
  {                         
  }                         
  |                           
  /         It is used for split folder in cloud storage and is pre-handled, no conversion here.
  \         Not allowed in Azure, allowed in AWS.
  \t
  space     It is the space character.
  ```

<!-- 
[!DNL Experience Manager Assets] manages the forbidden characters in the filenames while you upload assets or folders. [!DNL Experience Manager] updates only the node names in the DAM repository. However, the `title` of the asset or folder remains unchanged.

Following are the file naming conventions that are applied while uploading assets or folders in [!DNL Experience Manager Assets]:

| Characters &Dagger; | When occurring in file names | When occurring in folder names | Example |
|---|---|---|---|
| `. / : [ ] | *` | Replaced with `-` (hyphen). | Replaced with `-` (hyphen). A `.` (dot) in the filename extension is retained as is. | Replaced with `-` (hyphen). | `myimage.jpg` remains as is and `my.image.jpg` changes to `my-image.jpg`. |
| `% ; # , + ? ^ { } "` and whitespaces | Whitespaces are retained | Replaced with `-` (hyphen). | `My Folder.` changes to `my-folder-`. |
| `# % { } ? & .` | Replaced with `-` (hyphen). | NA. | `#My New File.` changes to `-My New File-`. |
| Uppercase characters | Casing is retained as is. | Changed to lowercase characters. | `My New Folder` changes to `my-new-folder`. |
| Lppercase characters | Casing is retained as is. | Casing is retained as is. | NA. |

&Dagger; The list of characters is a whitespace-separated list.
-->

#### 1회 또는 반복 일괄 가져오기 예약 {#schedule-bulk-import}

일회성 일괄 가져오기 또는 반복 일괄 가져오기를 예약하려면 다음 단계를 실행합니다.

1. 대량 가져오기 구성을 만듭니다.
1. 구성을 선택하고 도구 모음에서 **[!UICONTROL 일정]**&#x200B;을 선택합니다.
1. 일회성 수집을 설정하거나 매시간, 매일 또는 매주 단위로 일정을 예약합니다. **[!UICONTROL 제출]**&#x200B;을 클릭합니다.

   ![일괄 수집기 작업 예약](assets/bulk-ingest-schedule1.png)


#### Assets 대상 폴더 보기 {#view-assets-target-folder}

일괄 가져오기 작업을 실행한 후 자산을 가져오는 Assets 대상 위치를 보려면 구성을 선택한 다음 **[!UICONTROL Assets 보기]**&#x200B;를 클릭합니다.

#### 일괄 가져오기 도구 실행 {#run-bulk-import-tool}

[일괄 가져오기 도구를 구성](#configure-bulk-ingestor-tool)하고 선택적으로 [일괄 가져오기 도구 구성을 관리](#manage-bulk-import-configuration)한 후 구성 작업을 실행하여 자산의 일괄 수집을 시작할 수 있습니다.

일괄 가져오기 프로세스를 시작하려면 **[!UICONTROL 도구]** > **[!UICONTROL Assets]** > **[!UICONTROL 일괄 가져오기]**(으)로 이동하고 [일괄 가져오기 구성](#configure-bulk-ingestor-tool)을 선택한 다음 **[!UICONTROL 실행]**&#x200B;을 클릭합니다. 확인하려면 **[!UICONTROL 실행]**&#x200B;을 다시 클릭하세요.

Experience Manager은 작업이 성공적으로 완료되면 작업 상태를 **처리 중** 및 **성공**(으)로 업데이트합니다. 가져온 자산을 Experience Manager에서 보려면 **Assets 보기**&#x200B;를 클릭하십시오.

작업이 진행 중이면 구성을 선택하고 **중지**&#x200B;를 클릭하여 일괄 수집 프로세스를 중지할 수도 있습니다. 프로세스를 다시 시작하려면 **실행**&#x200B;을 다시 클릭하세요. **시험 실행**&#x200B;을 클릭하여 아직 가져오기 보류 중인 자산의 세부 정보를 알 수도 있습니다.

#### 실행 후 작업 관리 {#manage-jobs-after-execution}

Experience Manager을 사용하면 대량 가져오기 작업의 내역을 볼 수 있습니다. 작업 내역은 작업 상태, 작업 생성자, 로그와 함께 시작 날짜 및 시간, 생성 날짜 및 시간, 완료 날짜 및 시간 등의 기타 세부 정보로 구성됩니다.

구성에 대한 작업 기록에 액세스하려면 구성을 선택하고 **[!UICONTROL 작업 기록]**&#x200B;을 클릭합니다. 작업을 선택하고 **열기**&#x200B;를 클릭합니다.

![일괄 수집기 작업 예약](assets/job-history-bulk-import.png)

Experience Manager에 작업 내역이 표시됩니다. 대량 가져오기 작업 기록 페이지에서 **삭제**&#x200B;를 클릭하여 대량 가져오기 구성에 대한 해당 작업을 삭제할 수도 있습니다.


## 데스크탑 클라이언트를 사용하여 에셋 업로드 {#upload-assets-desktop-clients}

[!DNL Experience Manager]은(는) 웹 브라우저 사용자 인터페이스 외에도 데스크톱에서 다른 클라이언트를 지원합니다. 또한 웹 브라우저로 이동할 필요 없이 업로드 환경을 제공합니다.

* [[!DNL Adobe Asset Link]](https://helpx.adobe.com/kr/enterprise/using/adobe-asset-link.html)은(는) Adobe Photoshop, Adobe Illustrator 및 Adobe InDesign 데스크톱 응용 프로그램의 [!DNL Experience Manager]에서 자산에 대한 액세스를 제공합니다. 이러한 데스크톱 응용 프로그램 내에서 Asset Link Adobe 인터페이스에서 현재 열려 있는 문서를 [!DNL Experience Manager]에 직접 업로드할 수 있습니다.
* [[!DNL Experience Manager] 데스크톱 앱](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html)은(는) 파일 형식이나 자산을 처리하는 기본 응용 프로그램에 관계없이 데스크톱에서 자산 작업을 간소화합니다. 브라우저 업로드는 플랫 파일 목록 업로드만 지원하므로 로컬 파일 시스템에서 중첩된 폴더 계층의 파일을 업로드하는 것이 유용합니다.

## 업로드 시 에셋 처리 {#process-when-uploaded}

업로드된 에셋에 대해 추가 처리를 수행하려면 업로드 폴더에 처리 프로필을 적용할 수 있습니다. 프로필은 [!DNL Assets] 폴더의 **[!UICONTROL 속성]** 페이지에서 사용할 수 있습니다. 확장이 없거나 잘못된 디지털 자산은 원하는 대로 처리되지 않습니다. 예를 들어 이러한 에셋을 업로드할 때 아무것도 발생하지 않거나 잘못된 처리 프로필이 에셋에 적용될 수 있습니다. 사용자는 DAM에 이진 파일을 저장할 수 있습니다.

![처리 프로필 추가 옵션이 있는 자산 폴더의 속성](assets/assets-folder-properties.png)

다음 탭을 사용할 수 있습니다.

* [메타데이터 프로필](metadata-profiles.md)을 사용하면 해당 폴더에 업로드된 자산에 기본 메타데이터 속성을 적용할 수 있습니다.
* [처리 프로필](asset-microservices-configure-and-use.md)을 사용하면 기본적으로 가능한 것보다 더 많은 렌디션을 생성할 수 있습니다.

또한 배포에서 [!DNL Dynamic Media]을(를) 사용하도록 설정한 경우 다음 탭을 사용할 수 있습니다.

* [[!DNL Dynamic Media] 이미지 프로필](dynamic-media/image-profiles.md)을 통해 업로드된 에셋에 특정 자르기(**[!UICONTROL 스마트 자르기]** 및 픽셀 자르기) 및 선명하게 하기 구성을 적용할 수 있습니다.
* [[!DNL Dynamic Media] 비디오 프로필](dynamic-media/video-profiles.md)을 사용하면 특정 비디오 인코딩 프로필(해상도, 형식, 매개 변수)을 적용할 수 있습니다.

>[!NOTE]
>
>[!DNL Dynamic Media] 자르기 및 자산에 대한 기타 작업은 원본에 영향을 주지 않습니다. 즉, 업로드한 작업은 원본에 영향을 주지 않습니다. 대신 에셋을 전달할 때 자르거나 변형할 수 있는 매개 변수를 제공합니다.

처리 프로필이 할당된 폴더의 경우 프로필 이름이 카드 보기의 썸네일에 표시됩니다. 목록 보기에서 **[!UICONTROL 처리 프로필]** 열에 프로필 이름이 나타납니다.

## API를 사용하여 에셋 업로드 또는 수집 {#upload-using-apis}

업로드 API 및 프로토콜에 대한 기술적 세부 정보와 오픈 소스 SDK 및 샘플 클라이언트에 대한 링크는 개발자 참조의 [자산 업로드](developer-reference-material-apis.md#asset-upload) 섹션에 제공됩니다.

## 팁, 모범 사례 및 제한 사항 {#tips-limitations}

* 다이렉트 이진 업로드는 자산을 업로드하는 새로운 방법입니다. [!DNL Experience Manager] 사용자 인터페이스, [!DNL Adobe Asset Link] 및 [!DNL Experience Manager] 데스크톱 앱과 같은 제품 기능 및 클라이언트에서 기본적으로 지원됩니다. 고객 기술 팀에서 사용자 정의하거나 확장하는 모든 사용자 지정 코드는 새로운 업로드 API 및 프로토콜을 사용해야 합니다.

* Adobe은 [!DNL Experience Manager Assets]의 각 폴더에 1000개 이하의 자산을 추가할 것을 권장합니다. 이렇게 하면 &quot;이 디렉터리에 1000개 이상의 항목이 있습니다. 업로드 및 새 폴더 생성이 지연될 수 있습니다.&quot; 폴더에 에셋을 더 추가할 수 있지만 이러한 폴더에 대한 탐색 속도가 느려지는 등의 성능 문제가 발생할 수 있습니다.

* [!UICONTROL 이름 충돌] 대화 상자에서 **[!UICONTROL 바꾸기]**&#x200B;을(를) 선택하면 새 자산에 대한 자산 ID가 다시 생성됩니다. 이 ID는 이전 에셋의 ID와 다릅니다. [Assets Insights](/help/assets/assets-insights.md)가 [!DNL Adobe Analytics]을(를) 사용하여 노출 또는 클릭을 추적할 수 있도록 설정된 경우 재생성된 자산 ID는 [!DNL Analytics]의 자산에 대해 캡처된 데이터를 무효화합니다.

* 일부 업로드 방법을 사용해도 파일 이름에 [금지된 문자](#filename-handling)가 포함된 에셋의 업로드가 중지되지 않습니다. 문자가 `-` 기호로 대체되었습니다.

* 브라우저를 사용하여 에셋을 업로드하면 중첩된 폴더 계층이 아닌 플랫 파일 목록만 지원됩니다. 중첩된 폴더 내의 모든 자산을 업로드하려면 [데스크톱 앱](#upload-assets-desktop-clients)을 사용하는 것이 좋습니다.

* 일괄 가져오기 메서드는 전체 폴더 구조를 데이터 소스에 있는 그대로 가져옵니다. 그러나 [!DNL Experience Manager]에는 비어 있지 않은 폴더만 만들어집니다.


<!-- TBD: Link to file name handling in DA docs when it is documented. 
-->

**추가 참조**

* [자산 번역](translate-assets.md)
* [Assets HTTP API](mac-api-assets.md)
* [자산이 지원되는 파일 형식](file-format-support.md)
* [자산 검색](search-assets.md)
* [연결된 자산](use-assets-across-connected-assets-instances.md)
* [자산 보고서](asset-reports.md)
* [메타데이터 스키마](metadata-schemas.md)
* [자산 다운로드](download-assets-from-aem.md)
* [메타데이터 관리](manage-metadata.md)
* [검색 패싯](search-facets.md)
* [컬렉션 관리](manage-collections.md)
* [일괄 메타데이터 가져오기](metadata-import-export.md)
* [AEM 및 Dynamic Media에 자산 게시](/help/assets/publish-assets-to-aem-and-dm.md)

>[!MORELIKETHIS]
>
>* [[!DNL Adobe Experience Manager] 데스크탑 앱](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/introduction.html)
>* [정보 [!DNL Adobe Asset Link]](https://www.adobe.com/kr/creativecloud/business/enterprise/adobe-asset-link.html)
>* [[!DNL Adobe Asset Link] 설명서](https://helpx.adobe.com/kr/enterprise/using/adobe-asset-link.html)
>* [자산 업로드에 대한 기술 참조](developer-reference-material-apis.md#asset-upload)
