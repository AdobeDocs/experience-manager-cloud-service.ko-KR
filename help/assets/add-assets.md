---
title: 디지털 자산에 [!DNL Adobe Experience Manager].
description: 디지털 자산에 [!DNL Adobe Experience Manager] 로서의 [!DNL Cloud Service].
feature: Asset Management,Upload
role: User,Admin
exl-id: 0e624245-f52e-4082-be21-13cc29869b64
source-git-commit: bc46064093c22d8902a673e76fdb53c626a5cbb0
workflow-type: tm+mt
source-wordcount: '3064'
ht-degree: 1%

---

# 에 디지털 자산 추가 [!DNL Adobe Experience Manager] 로서의 [!DNL Cloud Service] [!DNL Assets] {#add-assets-to-experience-manager}

[!DNL Adobe Experience Manager Assets] 에서는 많은 소스에서 다양한 유형의 디지털 자산을 허용합니다. 바이너리와 생성된 표현물을 저장하며, 다양한 작업 과정과 [!DNL Adobe Sensei] 서비스를 사용하면 여러 면에 있는 많은 채널을 통해 배포할 수 있습니다.

[!DNL Adobe Experience Manager] 리치 메타데이터, 스마트 태그, 렌디션 및 기타 DAM(Digital Asset Management) 서비스를 사용하여 업로드된 디지털 파일의 바이너리 컨텐츠를 보강합니다. 로컬 폴더 또는 네트워크 드라이브에서 이미지, 문서, 원시 이미지 파일 등의 다양한 유형의 파일을 [!DNL Experience Manager Assets].

가장 일반적으로 사용되는 브라우저 업로드 외에도, 자산에 자산을 추가하는 다른 방법 [!DNL Experience Manager] 리포지토리에는 Adobe Asset Link와 같은 데스크탑 클라이언트를 포함하여 [!DNL Experience Manager] 고객이 만들 데스크탑 앱, 업로드 및 수집 스크립트 및 다음과 같이 추가된 자동화된 수집 통합 [!DNL Experience Manager] 확장.

에서 바이너리 파일을 업로드하고 관리할 수 있습니다. [!DNL Experience Manager]에서 가장 일반적으로 사용되는 파일 형식은 메타데이터 추출 또는 미리 보기/변환 생성과 같은 추가 서비스를 지원합니다. 을(를) 참조하십시오. [지원되는 파일 형식](file-format-support.md) 자세한 내용

업로드된 자산에 대한 추가 처리를 수행하도록 선택할 수도 있습니다. 특정 메타데이터, 표현물 또는 이미지 처리 서비스를 추가하기 위해 자산이 업로드되는 폴더에 많은 자산 처리 프로필을 구성할 수 있습니다. 자세한 내용은 [업로드 시 자산 처리](#process-when-uploaded).

[!DNL Assets] 다음 업로드 방법을 제공합니다. Adobe은 업로드 옵션을 사용하기 전에 사용 사례 및 적용 가능성을 이해할 것을 권장합니다.

| 업로드 메서드 | 사용 시기? | 기본 성향 |
|---------------------|----------------|-----------------|
| [Assets 콘솔 사용자 인터페이스](#upload-assets) | 가끔씩 업로드, 간편한 누르기 및 드래그, 파인더 업로드. 을 사용하여 많은 자산을 업로드하지 마십시오. | 모든 사용자 |
| [API 업로드](#upload-using-apis) | 업로드 중 동적 의사 결정 | 개발자 |
| [[!DNL Experience Manager] 데스크탑 앱](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html) | 낮은 볼륨 자산 수집이지만 마이그레이션이 아닙니다. | 관리자, 마케터 |
| [[!DNL Adobe Asset Link]](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/adobe-asset-link.ug.html) | 크리에이티브 및 마케터가 지원되는 내에서 자산을 사용할 때 유용합니다 [!DNL Creative Cloud] 데스크탑 앱. | 크리에이티브, 마케터 |
| [자산 일괄 수집](#asset-bulk-ingestor) | 대규모 마이그레이션 및 종종 대량 섭취에 권장됩니다. 지원되는 데이터 저장소에 대해서만 가능합니다. | 관리자, 개발자 |

## 에셋 업로드 {#upload-assets}

<!-- #ENGCHECK do we support pausing? I couldn't get pause to show with 1.5GB upload.... If not, this should be removed#

   You can pause the uploading of large assets (greater than 500 MB) and resume it later from the same page. Tap the **[!UICONTROL Pause]** icon beside progress bar that appears when an upload starts.

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

파일(또는 여러 파일)을 업로드하려면 바탕 화면에서 파일을 선택하고 사용자 인터페이스(웹 브라우저)를 대상 폴더로 드래그합니다. 또는 사용자 인터페이스에서 업로드를 시작할 수 있습니다.

1. 에서 [!DNL Assets] 사용자 인터페이스에서 디지털 자산을 추가할 위치로 이동합니다.
1. 자산을 업로드하려면 다음 중 하나를 수행합니다.

   * 도구 모음에서 **[!UICONTROL 만들기]** > **[!UICONTROL 파일]**. 필요한 경우 제공된 대화 상자에서 파일의 이름을 변경할 수 있습니다.
   * HTML5를 지원하는 브라우저에서 자산을 직접 [!DNL Assets] 사용자 인터페이스. 파일 이름을 바꿀 대화 상자가 표시되지 않습니다.

   ![create_menu](assets/create_menu.png)

   여러 파일을 선택하려면 `Ctrl` 또는 `Command` 키를 누르고 파일 선택기 대화 상자에서 자산을 선택합니다. iPad을 사용하는 경우 한 번에 하나의 파일만 선택할 수 있습니다.

1. 진행 중인 업로드를 취소하려면 닫기(`X`)을 클릭하여 제품에서 사용할 수 있습니다. 업로드 작업을 취소하면 [!DNL Assets] 자산의 부분적으로 업로드된 부분을 삭제합니다.
파일을 업로드하기 전에 업로드 작업을 취소하면 [!DNL Assets] 현재 파일 업로드를 중지하고 컨텐츠를 새로 고칩니다. 그러나 이미 업로드된 파일은 삭제되지 않습니다.

1. 의 업로드 진행 대화 상자 [!DNL Assets] 업로드에 성공한 파일 수와 업로드에 실패한 파일을 표시합니다.
또한 [!DNL Assets] 사용자 인터페이스에는 업로드한 가장 최근 자산 또는 처음 만든 폴더가 표시됩니다.

>[!NOTE]
>
>중첩된 폴더 계층을 업로드하려면 다음을 참조하십시오 [자산 일괄 업로드](#bulk-upload).

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

### 자산이 이미 있을 때 업로드 처리 {#handling-upload-existing-file}

기존 자산과 경로(이름과 위치)가 동일한 자산을 업로드할 수 있습니다. 그러나 다음 옵션과 함께 경고 대화 상자가 표시됩니다.

* 기존 자산 바꾸기: 기존 자산을 바꿀 경우, 자산의 메타데이터 및 기존 자산에 대한 이전 수정(예: 주석, 자르기 등)이 삭제됩니다.

   >[!NOTE]
   >
   >자산이 잠겨 있거나 체크 아웃된 경우에는 자산을 바꾸는 옵션을 사용할 수 없습니다.

* 다른 버전 만들기: 저장소에 기존 자산의 새 버전이 만들어집니다. 에서 두 버전을 볼 수 있습니다 [!UICONTROL 타임라인] 필요한 경우 이전 기존 버전으로 되돌릴 수 있습니다.
* 둘 다 유지: 두 자산을 모두 유지하도록 선택하면 새 자산의 이름이 바뀝니다.

중복 자산을 [!DNL Assets]를 클릭합니다. **[!UICONTROL 유지]**. 업로드한 중복 자산을 삭제하려면 **[!UICONTROL 삭제]**.

### 파일 이름 처리 및 금지된 문자 {#filename-handling}

[!DNL Experience Manager Assets] 파일 이름에 사용할 수 없는 문자가 있는 자산을 업로드하지 못하도록 합니다. 허용되지 않는 문자 이상을 포함하는 파일 이름이 있는 자산을 업로드하려고 하면, [!DNL Assets] 경고 메시지를 표시하고 이러한 문자를 제거하거나 허용되는 이름으로 업로드할 때까지 업로드를 중지합니다.

조직에 대한 특정 파일 이름 지정 규칙에 맞추기 위해 [!UICONTROL 자산 업로드] 대화 상자에서는 업로드하는 파일의 긴 이름을 지정할 수 있습니다. 다음(공백으로 구분된 목록) 문자는 지원되지 않습니다.

* 자산 이름에 잘못된 문자: `* / : [ \\ ] | # % { } ? &`
* 자산 폴더 이름에 잘못된 문자가 있습니다. `* / : [ \\ ] | # % { } ? \" . ^ ; + & \t`

## 자산 일괄 업로드 {#bulk-upload}

벌크 자산 수집기는 매우 많은 수의 자산을 효율적으로 처리할 수 있습니다. 그러나 대규모 수집은 광범위한 파일 덤프나 간편한 마이그레이션이 아닙니다. 비즈니스 목적을 지원하고 효율성을 제공하는 의미 있는 프로젝트로 대규모 수집하려면 마이그레이션을 계획하고 자산 조직을 조정하십시오. 모든 수집은 일반화하지 않고, 미묘한 저장소 구성 및 비즈니스 요구 사항을 고려합니다. 다음은 대량 수집을 계획 및 실행하기 위한 몇 가지 중요한 제안입니다.

* 자산 조정: DAM에서 필요하지 않은 자산을 제거합니다. 사용되지 않거나, 사용되지 않거나, 중복 자산을 제거하는 것이 좋습니다. 이렇게 하면 전송된 데이터 및 수집된 자산이 감소하여 더 빠른 수집이 발생합니다.
* 자산 구성: 파일 크기, 파일 형식, 사용 사례 또는 우선 순위와 같이 논리적 순서로 컨텐츠를 구성하는 것이 좋습니다. 일반적으로 크기가 큰 복잡한 파일은 더 많은 처리가 필요합니다. 아래 설명된 파일 크기 필터링 옵션을 사용하여 큰 파일을 별도로 수집하는 것을 고려할 수도 있습니다.
* 스테이징 처리: 수집을 여러 대량 수집 프로젝트로 분류해 보십시오. 이렇게 하면 컨텐츠를 더 빨리 보고 필요에 따라 수집을 업데이트할 수 있습니다. 예를 들어, 비스파이크 시간 동안 처리 집약적인 자산을 수집하거나 여러 청크로 점진적으로 수집할 수 있습니다. 그러나 한 번에 많은 처리가 필요하지 않은 작고 간단한 자산을 처리할 수 있습니다.

더 많은 파일을 업로드하려면 다음 방법 중 하나를 사용합니다. 또한 [사용 사례 및 방법](#upload-methods-comparison)

* [자산 업로드 API](developer-reference-material-apis.md#asset-upload): 필요한 경우 API를 활용하는 사용자 지정 업로드 스크립트 또는 도구를 사용하여 자산을 추가로 처리(예: 메타데이터 번역 또는 파일 이름 변경)합니다.
* [[!DNL Experience Manager] 데스크탑 앱](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html): 로컬 파일 시스템에서 자산을 업로드하는 크리에이티브 전문가 및 마케터에게 유용합니다. 로컬에서 사용할 수 있는 중첩된 폴더를 업로드하려면 이 파일을 사용합니다.
* [일괄 수집 도구](#asset-bulk-ingestor): 배포 시 가끔 또는 처음에 대량의 자산을 수집하는 데 사용합니다 [!DNL Experience Manager].

### 자산 벌크 가져오기 도구 {#asset-bulk-ingestor}

이 도구는 Azure 또는 S3 데이터 저장소에서 자산을 대량으로 수집하기 위해 관리자 그룹에만 제공됩니다. 구성 및 통합에 대한 비디오 개요를 참조하십시오.

>[!VIDEO](https://video.tv.adobe.com/v/329680/?quality=12&learn=on)

다음 이미지는 데이터 저장소에서 Experience Manager에 자산을 수집할 때 다양한 단계를 보여줍니다.

![대량 수집 도구](assets/bulk-ingestion.png)

**전제 조건**

이 기능을 사용하려면 Azure 또는 AWS의 외부 저장소 계정 또는 버킷이 필요합니다.

>[!NOTE]
>
>저장소 계정 컨테이너 또는 버킷을 비공개로 만들고 승인된 요청에서만 연결을 허용합니다. 그러나 송신 네트워크 연결에 대한 추가 제한 사항은 지원되지 않습니다.

>[!NOTE]
>
>외부 저장소 계정에는 벌크 가져오기 도구와 다른 파일/폴더 이름 규칙이 있을 수 있습니다. 자세한 내용은 [벌크 가져오기 중 파일 이름 처리](#filename-handling-bulkimport) 허용되지 않거나 이스케이프 처리된 이름에 대한 자세한 내용을 참조하십시오.


### 대량 가져오기 도구 구성 {#configure-bulk-ingestor-tool}

대량 가져오기 도구를 구성하려면 다음 단계를 수행합니다.

1. 다음으로 이동 **[!UICONTROL 도구]** > **[!UICONTROL 자산]** > **[!UICONTROL 벌크 가져오기]**. 을(를) 선택합니다 **[!UICONTROL 만들기]** 선택 사항입니다.

1. 에서 벌크 가져오기 구성의 제목을 지정합니다 **[!UICONTROL 제목]** 필드.

1. 에서 데이터 소스 유형을 선택합니다 **[!UICONTROL 원본 가져오기]** 드롭다운 목록.

1. 데이터 소스와의 연결을 만들 값을 제공합니다. 예를 들어 **Azure Blob 저장소** 데이터 소스로 Azure 저장소 계정, Azure blob 컨테이너 및 Azure 액세스 키의 값을 지정합니다.

1. 드롭다운 목록에서 필요한 인증 모드를 선택합니다. **Azure 액세스 키** 는 Azure 저장소 계정에 대한 전체 액세스 권한을 제공하는 반면, **Azure SAS 토큰** 관리자는 권한 및 만료 정책을 사용하여 토큰의 기능을 제한할 수 있습니다.

1. 의 데이터 소스에 있는 자산이 들어 있는 루트 폴더의 이름을 입력합니다 **[!UICONTROL 소스 폴더]** 필드.

1. (선택 사항) 자산의 최소 파일 크기를 MB로 제공하여 자산의 수집 프로세스를 **[!UICONTROL 최소 크기별 필터링]** 필드.

1. (선택 사항) 자산의 최대 파일 크기를 MB로 제공하여 자산의 수집 프로세스에 **[!UICONTROL 최대 크기로 필터링]** 필드.

1. (선택 사항) 의 수집에서 제외할 MIME 유형의 쉼표로 구분된 목록을 지정합니다. **[!UICONTROL MIME 유형 제외]** 필드. 예, `image/jpeg, image/.*, video/mp4`. 자세한 내용은 [모든 지원되는 파일 형식](/help/assets/file-format-support.md).

1. 의 수집에서 포함할 MIME 유형의 쉼표로 구분된 목록을 지정합니다. **[!UICONTROL MIME 유형 포함]** 필드. 자세한 내용은 [모든 지원되는 파일 형식](/help/assets/file-format-support.md).

1. 을(를) 선택합니다 **[!UICONTROL 가져온 후 소스 파일 삭제]** 파일을 가져온 후 소스 데이터 저장소에서 원본 파일을 삭제하는 옵션 [!DNL Experience Manager].

1. 을(를) 선택합니다 **[!UICONTROL 가져오기 모드]**. 선택 **건너뛰기**, **바꾸기**, 또는 **버전 만들기**. 건너뛰기 모드는 기본값이며 이 모드에서는 자산이 이미 존재하는 경우 수집기가 자산을 가져오기 위해 건너뜁니다. 의 의미 보기 [버전 바꾸기 및 만들기 옵션](#handling-upload-existing-file).

1. DAM에서 을 사용하여 자산을 가져올 위치를 정의할 경로를 지정합니다. **[!UICONTROL 자산 Target 폴더]** 필드. (예: `/content/dam/imported_assets`)

1. (선택 사항) CSV 형식으로 제공되는 가져올 메타데이터 파일을 **[!UICONTROL 메타데이터 파일]** 필드. 소스 Blob 위치에 CSV 파일을 지정하고 벌크 가져오기 도구를 구성하는 동안 경로를 참조하십시오. 이 필드에서 참조되는 CSV 파일 형식은 CSV 파일 형식 및 [자산 메타데이터 일괄적으로 가져오기 및 내보내기](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/assets/admin/metadata-import-export.html). 을(를) 선택하는 경우 **가져온 후 소스 파일 삭제** 옵션을 선택하는 경우 **제외** 또는 **MIME 유형 포함** 또는 **경로/파일별 필터링** 필드. 정규 표현식을 사용하여 이러한 필드에 있는 CSV 파일을 필터링할 수 있습니다.

1. 클릭 **[!UICONTROL 저장]** 구성을 저장합니다.

### 대량 가져오기 도구 구성 관리 {#manage-bulk-import-configuration}

벌크 가져오기 도구 구성을 만든 후 자산을 Experience Manager 인스턴스에 일괄 수집하기 전에 구성을 평가하는 작업을 수행할 수 있습니다. 에서 사용할 수 있는 구성을 선택합니다. **[!UICONTROL 도구]** > **[!UICONTROL 자산]** > **[!UICONTROL 벌크 가져오기]** 대량 가져오기 도구 구성을 관리하는 사용 가능한 옵션을 보려면

### 구성 편집 {#edit-configuration}

구성을 선택하고 을(를) 클릭합니다 **[!UICONTROL 편집]** 구성 세부 사항을 수정하려면 편집 작업을 수행하는 동안에는 구성 및 데이터 소스 가져오기 제목을 편집할 수 없습니다.

### 구성 삭제 {#delete-configuration}

구성을 선택하고 을(를) 클릭합니다 **[!UICONTROL 삭제]** 대량 가져오기 구성을 삭제하려면

### 데이터 소스에 대한 연결 유효성 검사 {#validate-connection}

구성을 선택하고 을(를) 클릭합니다 **[!UICONTROL check]** 데이터 소스에 대한 연결의 유효성을 검사하려면 연결에 성공하면 Experience Manager에 다음 메시지가 표시됩니다.

![대량 가져오기 성공 메시지](assets/bulk-import-success-message.png)

### 대량 가져오기 작업에 대한 테스트 실행 호출 {#invoke-test-run-bulk-import}

구성을 선택하고 을(를) 클릭합니다 **[!UICONTROL 연습 실행]** 대량 가져오기 작업에 대한 테스트 실행을 호출하려면 Experience Manager은 대량 가져오기 작업에 대한 다음 세부 정보를 표시합니다.

![시험 실행 결과](assets/dry-assets-result.png)

### 벌크 가져오기 중 파일 이름 처리 {#filename-handling-bulkimport}

자산 또는 폴더를 일괄적으로 가져오는 경우 [!DNL Experience Manager Assets] 가져오기 소스에 있는 모든 구조를 가져옵니다. [!DNL Experience Manager] 에서는 자산 및 폴더 이름에 특수 문자의 기본 제공 규칙을 따르므로 이러한 파일 이름은 정리해야 합니다. 폴더 이름과 자산 이름 모두에 대해 사용자가 정의한 제목은 변경되지 않고 그대로 유지되며 `jcr:title`.

벌크 가져오기 중에 [!DNL Experience Manager] 기존 폴더를 찾아 자산 및 폴더를 다시 가져오지 않고 가져오기가 발생하는 상위 폴더에 적용된 기밀 정보 처리 규칙을 확인합니다. 상위 폴더에 정리 규칙이 적용되는 경우 가져오기 원본에 동일한 규칙이 적용됩니다. 새 가져오기의 경우 자산 및 폴더의 파일 이름을 관리하기 위해 다음 정리 규칙이 적용됩니다.

**대량 가져오기에서 허용되지 않는 이름**

파일 및 폴더 이름에는 다음 문자를 사용할 수 없습니다.

* 제어 및 개인 사용 문자(0x00~0x1F, \u0081, \uE000)
* 점(.)으로 끝나는 파일 또는 폴더 이름

가져오기 프로세스 중에 이러한 조건과 일치하는 이름을 가진 파일 또는 폴더를 건너뛰고 실패로 표시됩니다.

**일괄 가져오기에서 자산 이름 처리**

자산 파일 이름의 경우 JCR 이름 및 경로는 API를 사용하여 정리됩니다. `JcrUtil.escapeIllegalJcrChars`.

* 유니코드 문자는 변경되지 않습니다
* 특수 문자를 URL 이스케이프 코드로 바꿉니다(예: ). `new%asset.png` 업데이트됨: `new%25asset.png`:

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

**벌크 가져오기에서 폴더 이름 처리**

폴더 파일 이름의 경우 JCR 이름 및 경로는 API를 사용하여 정리됩니다. `JcrUtil.createValidName`.

* 대문자는 소문자로 변환됩니다
* 유니코드 문자는 변경되지 않습니다
* 특수 문자를 대시(&#39;-&#39;)로 바꿉니다. 예를 들면 다음과 같습니다. `new asset.png` 업데이트됨: `new-asset.png`:

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

#### 1회 또는 반복 대량 가져오기를 예약합니다. {#schedule-bulk-import}

1회 또는 반복 대량 가져오기를 예약하려면 다음 단계를 실행합니다.

1. 대량 가져오기 구성을 만듭니다.
1. 구성을 선택하고 을(를) 선택합니다 **[!UICONTROL 예약]** 를 클릭합니다.
1. 1회 수집을 설정하거나 시간별, 일별 또는 주별 일정을 예약합니다. 클릭 **[!UICONTROL 제출]**.

   ![일괄 수집 또는 작업 예약](assets/bulk-ingest-schedule1.png)


#### 자산 대상 폴더 보기 {#view-assets-target-folder}

구성을 선택하고 을(를) 클릭합니다 **[!UICONTROL 자산 보기]** 일괄 가져오기 작업을 실행한 후 자산을 가져올 자산 대상 위치를 보려면

#### 대량 가져오기 도구 실행 {#run-bulk-import-tool}

후 [대량 가져오기 도구 구성](#configure-bulk-ingestor-tool) 원할 경우 [대량 가져오기 도구 구성 관리](#manage-bulk-import-configuration)구성 작업을 실행하여 자산의 일괄 수집을 시작할 수 있습니다.

다음으로 이동 **[!UICONTROL 도구]** > **[!UICONTROL 자산]** > **[!UICONTROL 벌크 가져오기]**&#x200B;에서 을(를) 선택합니다. [대량 가져오기 구성](#configure-bulk-ingestor-tool) 을(를) 클릭합니다. **[!UICONTROL 실행]** 일괄 임포트 프로세스를 시작합니다. 클릭 **[!UICONTROL 실행]** 다시 확인합니다.

Experience Manager은 작업 상태를 **처리 중** 및 **성공** 그 일이 성공적으로 완성되었을 때. 클릭 **자산 보기** Experience Manager에서 가져온 자산을 보려면

작업이 진행 중인 경우 구성을 선택하고 **정지** 일괄 수집 프로세스를 중지합니다. 클릭 **실행** 프로세스를 다시 시작합니다. 을 클릭할 수도 있습니다 **연습 실행** 가져오기로 아직 보류 중인 자산의 세부 사항을 알 수 있습니다.

#### 실행 후 작업 관리 {#manage-jobs-after-execution}

Experience Manager을 사용하면 벌크 가져오기 작업의 내역을 볼 수 있습니다. 작업 기록은 작업 상태, 작업 생성자, 로그와 시작 날짜 및 시간, 생성 날짜 및 시간, 완료 날짜 및 시간 등의 기타 세부 정보로 구성됩니다.

구성에 대한 작업 기록에 액세스하려면 구성을 선택하고 **[!UICONTROL 작업 내역]**. 작업을 선택하고 **열기**.

![일괄 수집 또는 작업 예약](assets/job-history-bulk-import.png)

Experience Manager에 작업 기록이 표시됩니다. [대량 가져오기 작업 내역] 페이지에서 **삭제** 대량 가져오기 구성에 대한 해당 작업을 삭제하려면


## 데스크탑 클라이언트를 사용하여 자산 업로드 {#upload-assets-desktop-clients}

웹 브라우저 사용자 인터페이스 외에도 [!DNL Experience Manager] 데스크탑에서 다른 클라이언트를 지원합니다. 또한 웹 브라우저로 이동할 필요 없이 업로드 경험을 제공합니다.

* [[!DNL Adobe Asset Link]](https://helpx.adobe.com/kr/enterprise/using/adobe-asset-link.html) 에서 자산에 대한 액세스 권한을 제공합니다. [!DNL Experience Manager] Adobe Photoshop, Adobe Illustrator 및 Adobe InDesign 데스크탑 애플리케이션에서 사용할 수 있습니다. 현재 열려 있는 문서를 [!DNL Experience Manager] 이러한 데스크탑 애플리케이션 내에서 Asset Link 사용자 인터페이스에서 직접 액세스할 수 있습니다.
* [[!DNL Experience Manager] 데스크탑 앱](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html) 파일을 처리하는 기본 애플리케이션이나 파일 유형에 관계없이 데스크탑에서 자산 작업을 간소화합니다. 브라우저 업로드는 플랫 파일 목록만 업로드할 수 있으므로 로컬 파일 시스템에서 중첩 폴더 계층 구조에 있는 파일을 업로드하는 데 특히 유용합니다.

## 업로드할 때 자산 처리 {#process-when-uploaded}

업로드된 자산에 대해 추가 처리를 수행하기 위해 업로드 폴더에 처리 프로필을 적용할 수 있습니다. 프로필은 **[!UICONTROL 속성]** 의 폴더 페이지 [!DNL Assets]. 확장이 없거나 잘못된 확장이 있는 디지털 자산은 원하는 대로 처리되지 않습니다. 예를 들어 이러한 자산을 업로드할 때 아무 일도 발생하지 않거나 잘못된 처리 프로필이 자산에 적용될 수 있습니다. 사용자는 여전히 DAM에 이진 파일을 저장할 수 있습니다.

![처리 프로필 추가 옵션이 있는 자산 폴더의 속성](assets/assets-folder-properties.png)

다음 탭을 사용할 수 있습니다.

* [메타데이터 프로필](metadata-profiles.md) 기본 메타데이터 속성을 해당 폴더에 업로드된 자산에 적용할 수 있습니다.
* [처리 프로필](asset-microservices-configure-and-use.md) 기본적으로 가능한 것보다 더 많은 표현물을 생성할 수 있습니다.

추가로, [!DNL Dynamic Media] 이 활성화되어 있으면 다음 탭을 사용할 수 있습니다.

* [[!DNL Dynamic Media] 이미지 프로필](dynamic-media/image-profiles.md) 특정 자르기를 적용할 수 있습니다(**[!UICONTROL 스마트 자르기]** 업로드된 자산에 대한 구성 선명하게 하기( 및 픽셀 자르기) 및
* [[!DNL Dynamic Media] 비디오 프로필](dynamic-media/video-profiles.md) 특정 비디오 인코딩 프로필(해상도, 형식, 매개 변수)을 적용할 수 있습니다.

>[!NOTE]
>
>[!DNL Dynamic Media] 자르기와 자산에 대한 다른 작업은 원본에 영향을 주지 않습니다. 즉, 업로드된 원본이 변경되지 않습니다. 대신 자산을 전달할 때 자르거나 변형하는 매개 변수를 제공합니다.

처리 프로필이 할당된 폴더의 경우 카드 보기의 축소판에 프로필 이름이 나타납니다. 목록 보기에서 프로필 이름이 **[!UICONTROL 처리 프로필]** 열.

## API를 사용하여 자산 업로드 또는 수집 {#upload-using-apis}

업로드 API 및 프로토콜에 대한 기술 세부 사항, 오픈 소스 SDK 및 샘플 클라이언트에 대한 링크가 제공됩니다. [자산 업로드](developer-reference-material-apis.md#asset-upload) 개발자 참조 섹션.

## 팁, 모범 사례 및 제한 사항 {#tips-limitations}

* 직접 이진 업로드는 자산을 업로드하는 새로운 방법입니다. 기본적으로 다음과 같은 제품 기능과 클라이언트가 지원합니다 [!DNL Experience Manager] 사용자 인터페이스, [!DNL Adobe Asset Link], 및 [!DNL Experience Manager] 데스크탑 앱. 고객 기술 팀이 사용자 지정하거나 확장하는 모든 사용자 지정 코드는 새 업로드 API 및 프로토콜을 사용해야 합니다.

* Adobe은 의 각 폴더에 1000개 이하의 자산을 추가할 것을 권장합니다 [!DNL Experience Manager Assets]. 폴더에 자산을 더 추가할 수 있지만, 해당 폴더에 대한 탐색 속도가 느려지는 등의 성능 문제가 발생할 수 있습니다.

* 선택 시 **[!UICONTROL 바꾸기]** 에서 [!UICONTROL 이름 충돌] 대화 상자에서 새 자산에 대해 자산 ID가 다시 생성됩니다. 이 ID는 이전 자산의 ID와 다릅니다. If [자산 통찰력](/help/assets/assets-insights.md) 노출 횟수 또는 클릭 수를 추적하기 위해 활성화됨 [!DNL Adobe Analytics]재생성된 자산 ID는 자산에서 캡처된 데이터를 무효화합니다. [!DNL Analytics].

* 일부 업로드 방법에서는 [금지된 문자](#filename-handling) 파일 이름에서 볼 수 있습니다. 문자가 `-` 기호.

* 브라우저를 사용하여 자산을 업로드하면 플랫 파일 목록만 지원되며 중첩된 폴더 계층은 지원하지 않습니다. 중첩된 폴더 내의 모든 자산을 업로드하려면 를 사용하는 것이 좋습니다 [데스크탑 앱](#upload-assets-desktop-clients).

* 벌크 가져오기 방법은 데이터 소스에 있는 전체 폴더 구조를 가져옵니다. 그러나 비어 있지 않은 폴더만 [!DNL Experience Manager].


<!-- TBD: Link to file name handling in DA docs when it is documented. 
-->

>[!MORELIKETHIS]
>
>* [[!DNL Adobe Experience Manager] 데스크탑 앱](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/introduction.html)
>* [ [!DNL Adobe Asset Link] 정보](https://www.adobe.com/kr/creativecloud/business/enterprise/adobe-asset-link.html)
>* [[!DNL Adobe Asset Link] 설명서](https://helpx.adobe.com/enterprise/using/adobe-asset-link.html)
>* [자산 업로드에 대한 기술 참조](developer-reference-material-apis.md#asset-upload)

