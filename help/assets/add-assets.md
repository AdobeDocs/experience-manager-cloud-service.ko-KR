---
title: 디지털 자산을  [!DNL Adobe Experience Manager]에 추가합니다.
description: 디지털 자산을  [!DNL Adobe Experience Manager] 에  [!DNL Cloud Service]으로 추가합니다.
translation-type: tm+mt
source-git-commit: a81fe4a2c7d3c4e0471a961fb51249ac03f27e9c
workflow-type: tm+mt
source-wordcount: '2017'
ht-degree: 1%

---


# Adobe Experience Manager {#add-assets-to-experience-manager}에 디지털 에셋 추가

[!DNL Adobe Experience Manager] 리치 메타데이터, 스마트 태그, 표현물 및 기타 DAM(Digital Asset Management) 서비스를 사용하여 업로드된 디지털 파일의 이진 컨텐츠를 더욱 풍부하게 볼 수 있습니다. 로컬 폴더 또는 네트워크 드라이브에서 이미지, 문서 및 Raw 이미지 파일과 같은 다양한 유형의 파일을 [!DNL Experience Manager Assets]으로 업로드할 수 있습니다.

여러 업로드 방법이 제공됩니다. 가장 일반적으로 사용되는 브라우저 업로드 외에도, Adobe 에셋 링크 또는 [!DNL Experience Manager] 데스크탑 앱과 같은 데스크탑 클라이언트, 고객이 만드는 업로드 및 통합 스크립트, 자동 통합 통합 기능이 [!DNL Experience Manager] 익스텐션으로 추가되는 것을 포함하여 [!DNL Experience Manager] 저장소에 에셋을 추가하는 다른 방법이 있습니다.

여기에서 최종 사용자를 위한 업로드 방법에 중점을 두고 [!DNL Experience Manager] API 및 SDK를 사용하여 자산 업로드 및 수집의 기술적 측면을 설명하는 문서에 대한 링크를 제공합니다.

[!DNL Experience Manager]에서 모든 이진 파일을 업로드 및 관리할 수 있지만 가장 일반적으로 사용되는 파일 포맷은 메타데이터 추출 또는 미리 보기/변환 생성과 같은 추가 서비스를 지원합니다. 자세한 내용은 [지원되는 파일 형식](file-format-support.md)을 참조하십시오.

업로드된 자산에 대해 추가 처리를 하도록 선택할 수도 있습니다. 특정 메타데이터, 변환 또는 이미지 처리 서비스를 추가하기 위해 자산을 업로드할 폴더에 다양한 자산 처리 프로필을 구성할 수 있습니다. 업로드 시 [자산 처리를 참조하십시오](#process-when-uploaded).

>[!NOTE]
>
>[!DNL Experience Manager] as a  [!DNL Cloud Service] 는 새로운 자산 업로드 방법(직접 이진 업로드)을 활용합니다. 기본적으로 [!DNL Experience Manager] 사용자 인터페이스, [!DNL Adobe Asset Link], [!DNL Experience Manager] 데스크탑 앱과 같은 즉시 사용 가능한 제품 기능과 클라이언트에서 지원되므로 최종 사용자에게 투명하게 표시됩니다.
>
>고객 기술 팀이 사용자 정의하거나 확장한 코드를 업로드하려면 새로운 업로드 API 및 프로토콜을 사용해야 합니다.

[!DNL Cloud Service]인 자산은 다음 업로드 방법을 제공합니다. Adobe은 업로드 옵션을 사용하기 전에 업로드 옵션의 사용 사례와 적용 가능성을 이해하는 것이 좋습니다.

| 업로드 방법 | 언제 사용합니까? | 기본 페르소나 |
|---------------------|----------------|-----------------|
| [자산 콘솔 사용자 인터페이스](#upload-assets) | 가끔 업로드, 간편한 누르기 및 드래그, 파인더 업로드. 많은 수의 자산을 업로드하는 데 사용하지 마십시오. | 모든 사용자 |
| [API 업로드](#upload-using-apis) | 업로드하는 동안 다이내믹한 결정을 내릴 수 있습니다. | 개발자 |
| [[!DNL Experience Manager] 데스크탑 앱](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html) | 볼륨 자산 수집이 낮지만 마이그레이션이 아닙니다. | 관리자, 마케터 |
| [[!DNL Adobe Asset Link]](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/adobe-asset-link.ug.html) | 크리에이티브 및 마케터가 지원되는 [!DNL Creative Cloud] 데스크탑 앱 내에서 자산을 작업하는 경우에 유용합니다. | 크리에이티브, 마케터 |
| [자산 일괄 인제스트 또는](#asset-bulk-ingestor) | 대규모 마이그레이션 및 때때로 대량 인제스트 시 권장됩니다. 지원되는 데이터 저장소에 대해서만 가능합니다. | 관리자, 개발자 |

## 자산 업로드 {#upload-assets}

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

파일(또는 여러 파일)을 업로드하려면 데스크톱에서 해당 파일을 선택하고 사용자 인터페이스(웹 브라우저)를 대상 폴더로 드래그할 수 있습니다. 또는 사용자 인터페이스에서 업로드를 시작할 수 있습니다.

1. [!DNL Assets] 사용자 인터페이스에서 디지털 자산을 추가할 위치로 이동합니다.
1. 자산을 업로드하려면 다음 중 하나를 수행합니다.

   * 도구 모음에서 **[!UICONTROL 만들기]** > **[!UICONTROL 파일]**&#x200B;을 클릭합니다. 필요한 경우 표시된 대화 상자에서 파일의 이름을 변경할 수 있습니다.
   * HTML5를 지원하는 브라우저에서 자산을 [!DNL Assets] 사용자 인터페이스에서 바로 드래그합니다. 파일 이름을 변경하는 대화 상자가 표시되지 않습니다.

   ![create_menu](assets/create_menu.png)

   여러 파일을 선택하려면 `Ctrl` 또는 `Command` 키를 선택하고 파일 선택기 대화 상자에서 에셋을 선택합니다. iPad를 사용하는 경우 한 번에 하나의 파일만 선택할 수 있습니다.

1. 진행 중인 업로드를 취소하려면 진행률 표시줄 옆에 있는 닫기(`X`)를 클릭합니다. 업로드 작업을 취소하면 [!DNL Assets]은 자산의 부분적으로 업로드된 부분을 삭제합니다.
파일이 업로드되기 전에 업로드 작업을 취소하면 [!DNL Assets] 현재 파일 업로드를 중지하고 콘텐트를 새로 고칩니다. 하지만 이미 업로드된 파일은 삭제되지 않습니다.

1. [!DNL Assets]의 업로드 진행 대화 상자에는 업로드된 파일의 수와 업로드하지 못한 파일이 표시됩니다.
또한 [!DNL Assets] 사용자 인터페이스는 업로드한 가장 최근의 에셋 또는 처음 만든 폴더를 표시합니다.

>[!NOTE]
>
>중첩된 폴더 계층을 업로드하려면 [일괄 업로드 에셋](#bulk-upload)을 참조하십시오.

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

### 자산이 이미 {#handling-upload-existing-file} 있을 때 업로드 처리

기존 자산의 경로(이름과 위치)가 동일한 자산을 업로드할 수 있습니다. 그러나 다음 옵션과 함께 경고 대화 상자가 표시됩니다.

* 기존 자산 바꾸기:기존 자산을 교체할 경우, 기존 자산에 대한 메타데이터와 기존 자산에 대한 이전 수정(예: 주석, 자르기 등)이 삭제됩니다.
* 다른 버전 만들기:저장소에 기존 자산의 새 버전이 만들어집니다. [!UICONTROL 타임라인]에서 두 버전을 볼 수 있으며 필요한 경우 이전에 기존 버전으로 되돌릴 수 있습니다.
* 둘 다 유지:두 자산을 모두 유지하도록 선택하면 새 자산의 이름이 이름에 추가된 숫자 `1`로 바뀝니다.

>[!NOTE]
>
>[!UICONTROL 이름 충돌] 대화 상자에서 **[!UICONTROL 바꾸기]**&#x200B;를 선택하면 새 자산에 대해 자산 ID가 다시 생성됩니다. 이 ID는 이전 자산의 ID와 다릅니다.
>
>에셋 인사이트가 [!DNL Adobe Analytics]으로 노출 또는 클릭을 추적하도록 활성화된 경우 재생성된 에셋 ID는 [!DNL Analytics]에서 에셋에 대해 캡처된 데이터를 무효화합니다.

[!DNL Assets]에 중복된 자산을 유지하려면 **[!UICONTROL 유지]**&#x200B;를 클릭합니다. 업로드한 중복 자산을 삭제하려면 **[!UICONTROL 삭제]**&#x200B;를 클릭합니다.

### 파일 이름 처리 및 금지된 문자 {#filename-handling}

[!DNL Experience Manager Assets] 파일 이름에 금지된 문자가 포함된 에셋을 업로드하지 못하도록 합니다. 허용되지 않은 문자 이상이 포함된 파일 이름의 자산을 업로드하려고 하면, [!DNL Assets]은 경고 메시지를 표시하고 이러한 문자를 제거하거나 허용되는 이름으로 업로드할 때까지 업로드를 중지합니다. 일부 업로드 메서드는 파일 이름에 금지된 문자가 있는 에셋을 업로드하는 것을 막지 않지만, 문자를 `-`으로 바꿉니다.

조직에 대한 특정 파일 이름 지정 규칙에 맞도록 [!UICONTROL 자산 업로드] 대화 상자를 사용하여 업로드하는 파일의 긴 이름을 지정할 수 있습니다. 다음(공백으로 구분된 목록) 문자는 지원되지 않습니다.

* 자산 파일 이름 `* / : [ \\ ] | # % { } ? &`에 대한 잘못된 문자가 있습니다.
* 자산 폴더 이름 `* / : [ \\ ] | # % { } ? \" . ^ ; + & \t`에 대한 잘못된 문자가 있습니다.

## 자산 일괄 업로드 {#bulk-upload}

벌크 자산 인제스트는 매우 많은 수의 자산을 효율적으로 처리할 수 있습니다. 그러나 대규모 수집은 광범위한 파일 덤프 또는 캐주얼 마이그레이션이 아닙니다. 대규모 인제스트는 비즈니스 목적에 부합하고 효율적인 효과적인 프로젝트이므로 마이그레이션을 계획하고 자산 조직을 조정하십시오. 모든 인제션은 생성하는 대신 미묘한 리포지토리 구성 및 비즈니스 요구에 영향을 주는 다른 방식으로 다릅니다. 다음은 대량 수집을 계획 및 실행하기 위한 몇 가지 중요한 제안입니다.

* 자산 조정:DAM에 필요하지 않은 에셋을 제거합니다. 사용하지 않거나 오래된 자산 또는 중복된 자산을 제거하는 것이 좋습니다. 이렇게 하면 데이터 전송 및 인제스트된 에셋이 줄어들어 인제션이 빨라집니다.
* 자산 구성:파일 크기, 파일 형식, 사용 사례 또는 우선 순위와 같이 적절한 순서로 컨텐츠를 구성하는 것이 좋습니다. 일반적으로 복잡한 대용량 파일은 더 많은 처리가 필요합니다. 파일 크기 필터링 옵션(아래 설명됨)을 사용하여 대용량 파일을 별도로 인제스트하는 것도 좋습니다.
* 스테이지 인제션:통합 문제를 여러 일괄 통합 프로젝트로 나누는 것이 좋습니다. 이렇게 하면 컨텐츠를 더 빨리 보고 필요에 따라 질문을 업데이트할 수 있습니다. 예를 들어 사용량이 적은 시간 동안 처리량이 많은 에셋을 인제스트하거나 여러 청크에서 서서히 인제스트할 수 있습니다. 하지만 한 번에 많은 처리를 요구하지 않는 작고 간단한 자산을 인제스트할 수 있습니다.

많은 수의 파일을 업로드하려면 다음 방법 중 하나를 사용합니다. 또한 [사용 사례 및 메서드](#upload-methods-comparison)를 참조하십시오.

* [자산 업로드 API](developer-reference-material-apis.md#asset-upload-technical):필요한 경우 API를 활용하여 자산의 추가 처리(예: 메타데이터를 번역하거나 파일 이름 변경)를 추가하는 사용자 정의 업로드 스크립트 또는 도구를 사용합니다.
* [[!DNL Experience Manager] 데스크탑 앱](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html):로컬 파일 시스템에서 에셋을 업로드하는 크리에이티브 전문가 및 마케터에게 유용합니다. 로컬에서 사용할 수 있는 중첩된 폴더를 업로드하는 데 사용합니다.
* [일괄 처리 도구](#asset-bulk-ingestor):배포 시 가끔 또는 초기에 대량의 자산을 수집하기 위해 사용합니다 [!DNL Experience Manager].

### 에셋 벌크 인제스트 또는 도구 {#asset-bulk-ingestor}

도구는 Azure 또는 S3 데이터 저장소에서 자산을 대량으로 수집하기 위해 사용할 수 있도록 관리자 그룹에만 제공됩니다. 구성 및 섭취 관련 비디오 개요를 참조하십시오.

>[!VIDEO](https://video.tv.adobe.com/v/329680/?quality=12&learn=on)

도구를 구성하려면 다음 단계를 수행합니다.

1. **[!UICONTROL 도구]** > **[!UICONTROL 자산]** > **[!UICONTROL 대량 가져오기]**&#x200B;로 이동합니다. **[!UICONTROL 만들기]** 옵션을 선택합니다.

![대량 가져오기 구성](assets/bulk-import-config.png)

1. [!UICONTROL 벌크 가져오기 구성] 페이지에서 필요한 값을 제공합니다.

   * [!UICONTROL 제목]:설명이 포함된 제목입니다.
   * [!UICONTROL 가져오기 소스]:해당 데이터 소스를 선택합니다.
   * [!UICONTROL 최소 크기별 필터]:에셋의 최소 파일 크기(MB)를 제공합니다.
   * [!UICONTROL 최대 크기별 필터]:에셋의 최대 파일 크기(MB)를 제공합니다.
   * [!UICONTROL MIME 유형 제외]:통합 대상에서 제외할 MIME 유형의 쉼표로 구분된 목록. 예, `image/jpeg, image/.*, video/mp4`.
   * [!UICONTROL MIME 유형 포함]:통합 시 포함할 MIME 유형의 쉼표로 구분된 목록. [지원되는 모든 파일 형식](/help/assets/file-format-support.md)을 참조하십시오.
   * [!UICONTROL 가져오기 모드]:건너뛰기, 바꾸기 또는 버전 만들기를 선택합니다. 건너뛰기 모드는 기본값이며 이 모드에서는 자산이 이미 존재하는 경우 인제스트나 가져오기 작업을 건너뜁니다. [바꾸기 및 버전 옵션](#handling-upload-existing-file)의 의미를 참조하십시오.
   * [!UICONTROL 자산 Target 폴더]:에셋을 가져올 DAM의 폴더를 가져옵니다. 예, `/content/dam/imported_assets`

1. 만들어진 인제스트나 구성을 삭제, 수정, 실행 및 더 많은 작업을 수행할 수 있습니다. 일괄 가져오기 인제스트나 구성을 선택하면 도구 모음에서 다음 옵션을 사용할 수 있습니다.

   * [!UICONTROL 편집]:선택한 구성을 편집합니다.
   * [!UICONTROL 삭제]:선택한 구성을 삭제합니다.
   * [!UICONTROL 확인]:데이터 저장소에 대한 연결을 확인합니다.
   * [!UICONTROL 드라이 런]:일괄 수주에 대한 테스트 실행을 호출합니다.
   * [!UICONTROL 실행]:선택한 구성을 실행합니다.
   * [!UICONTROL 중지]:활성 구성을 종료합니다.
   * [!UICONTROL 일정]:자산을 인제스트하려면 1회 또는 반복 일정을 설정합니다.
   * [!UICONTROL 작업 상태]:진행 중인 가져오기 작업에 사용되거나 완료된 작업에 사용될 경우 구성 상태를 확인합니다.
   * [!UICONTROL 작업 내역]:작업의 이전 인스턴스입니다.
   * [!UICONTROL 자산 보기]:대상 폴더가 있는 경우 대상 폴더를 봅니다.

   ![인제스트 또는 구성을 위한 툴바 옵션](assets/bulk-ingest-toolbar-options.png)

1회 또는 반복 대량 가져오기를 예약하려면 다음 단계를 수행합니다.

1. 대량 가져오기 구성을 만듭니다.
1. 구성을 선택하고 도구 모음에서 **[!UICONTROL 예약]**&#x200B;을 선택합니다.
1. 1회 수거를 설정하거나 시간별, 일별 또는 주별 일정을 예약합니다. **[!UICONTROL 제출]**&#x200B;을 클릭합니다.

   ![일괄 인제스트 또는 작업 예약](assets/bulk-ingest-schedule1.png)

## 데스크톱 클라이언트 {#upload-assets-desktop-clients}을(를) 사용하여 에셋 업로드

웹 브라우저 사용자 인터페이스 외에도 [!DNL Experience Manager]은 데스크탑의 다른 클라이언트를 지원합니다. 또한 웹 브라우저로 이동할 필요 없이 업로드 환경을 제공합니다.

* [[!DNL Adobe Asset Link]](https://helpx.adobe.com/kr/enterprise/using/adobe-asset-link.html) Adobe Photoshop, Adobe Illustrator 및 Adobe InDesign 데스크탑 애플리케이션 [!DNL Experience Manager] 에서 에셋에 액세스할 수 있습니다. 이러한 데스크톱 응용 프로그램 내에서 Adobe Asset Link 사용자 인터페이스에서 바로 현재 열려 있는 문서를 [!DNL Experience Manager]에 업로드할 수 있습니다.
* [[!DNL Experience Manager] 데스크탑 ](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html) 앱을 사용하면 파일 유형이나 이를 처리하는 기본 애플리케이션에 상관없이 데스크탑에서 에셋을 사용한 작업을 간소화할 수 있습니다. 브라우저 업로드는 플랫 파일 목록 업로드만 지원하기 때문에 로컬 파일 시스템에서 중첩된 폴더 계층 구조의 파일을 업로드하는 것이 특히 유용합니다.

## 업로드 시 자산 처리 {#process-when-uploaded}

업로드된 자산에 대한 추가 처리를 수행하려면 업로드 폴더에 처리 프로필을 적용할 수 있습니다. 프로필은 [!DNL Assets]에 있는 폴더의 **[!UICONTROL 속성]** 페이지에서 사용할 수 있습니다. 확장자가 없거나 확장이 잘못된 디지털 자산은 원하는 대로 처리되지 않습니다. 예를 들어, 이러한 자산을 업로드할 때 아무런 반응이 없거나 잘못된 처리 프로필이 자산에 적용될 수 있습니다. 사용자는 DAM에 이진 파일을 저장할 수 있습니다.

![처리 프로필을 추가하는 옵션이 있는 자산 폴더의 속성](assets/assets-folder-properties.png)

다음 탭을 사용할 수 있습니다.

* [메타데이터 ](metadata-profiles.md) 프로필을 사용하면 해당 폴더에 업로드된 자산에 기본 메타데이터 속성을 적용할 수 있습니다.
* [처리 ](asset-microservices-configure-and-use.md) 프로필을 사용하여 기본적으로 가능한 것보다 많은 변환을 생성할 수 있습니다.

또한 배포에서 [!DNL Dynamic Media]이(가) 활성화된 경우 다음 탭을 사용할 수 있습니다.

* [[!DNL Dynamic Media] 이미지 ](dynamic-media/image-profiles.md) 프로필을 사용하면 특정 자르기(**[!UICONTROL 스마트 자르기]** 및 픽셀 자르기)와 선명하게 하기 구성을 업로드된 자산에 적용할 수 있습니다.
* [[!DNL Dynamic Media] 비디오 ](dynamic-media/video-profiles.md) 프로필을 사용하면 특정 비디오 인코딩 프로필(해상도, 형식, 매개 변수)을 적용할 수 있습니다.

>[!NOTE]
>
>[!DNL Dynamic Media] 자산에서 자르기 및 기타 작업은 원본을 훼손하지 않습니다. 즉, 작업이 업로드된 원본을 변경하지 않습니다. 대신 에셋을 전달할 때 자르거나 변형할 매개 변수를 제공합니다.

처리 프로필이 할당된 폴더의 경우 카드 보기의 축소판에 프로필 이름이 나타납니다. 목록 보기에서 프로필 이름이 **[!UICONTROL 처리 프로필]** 열에 나타납니다.

## API {#upload-using-apis}를 사용하여 에셋 업로드 또는 인제스트

업로드 API 및 프로토콜의 기술 세부 사항, 오픈 소스 SDK 및 샘플 클라이언트에 대한 링크는 개발자 참조의 [asset upload](developer-reference-material-apis.md#asset-upload-technical) 섹션에 제공됩니다.

>[!MORELIKETHIS]
>
>* [[!DNL Adobe Experience Manager] 데스크탑 앱](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/introduction.html)
>* [정보 [!DNL Adobe Asset Link]](https://www.adobe.com/kr/creativecloud/business/enterprise/adobe-asset-link.html)
>* [[!DNL Adobe Asset Link] 설명서](https://helpx.adobe.com/enterprise/using/adobe-asset-link.html)
>* [자산 업로드를 위한 기술 참조](developer-reference-material-apis.md#asset-upload-technical)

