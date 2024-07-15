---
title: 사용 및 공유에 대한 보고서
description: 디지털 자산의 사용, 활동 및 공유를 이해하는 데 도움이 되는  [!DNL Adobe Experience Manager Assets] 의 자산에 대한 보고서입니다.
contentOwner: AG
feature: Asset Reports, Asset Management
role: Admin, User
exl-id: ef617b01-0019-4379-8d58-c03215d7e28f
source-git-commit: ab2cf8007546f538ce54ff3e0b92bb0ef399c758
workflow-type: tm+mt
source-wordcount: '942'
ht-degree: 9%

---

# 자산 보고서 {#asset-reports}

| 버전 | 문서 링크 |
| -------- | ---------------------------- |
| AEM 6.5 | [여기 클릭](https://experienceleague.adobe.com/docs/experience-manager-65/assets/administer/asset-reports.html?lang=en) |
| AEM as a Cloud Service | 이 문서 |

자산 보고를 통해 [!DNL Adobe Experience Manager Assets] 배포의 유틸리티를 평가할 수 있습니다. [!DNL Assets]을(를) 사용하면 디지털 자산에 대한 다양한 보고서를 생성할 수 있습니다. 보고서는 시스템의 사용, 사용자가 에셋과 상호 작용하는 방법, <!-- downloaded and -->에서 공유하는 에셋에 대한 유용한 정보를 제공합니다.

보고서의 정보를 사용하여 기업 내 및 고객에 의한 [!DNL Assets]의 채택률을 측정하기 위한 주요 성공 지표를 도출할 수 있습니다.

[!DNL Assets] 보고 프레임워크는 [!DNL Sling] 작업을 사용하여 순서대로 보고서 요청을 비동기적으로 처리합니다. 대형 저장소에 대해 확장 가능합니다. 비동기 보고서 처리를 통해 보고서가 생성되는 효율성과 속도가 향상됩니다.

보고서 관리 인터페이스는 직관적이고, 보관된 보고서에 액세스하고 보고서 실행 상태(성공, 실패 및 대기 중)를 보기 위한 세분화된 옵션 및 제어를 포함합니다.

보고서가 생성되면 <!-- through an email (optional) and -->을(를) 통해 받은 편지함 알림이 표시됩니다. 이전에 생성된 모든 보고서가 표시되는 보고서 목록 페이지에서 보고서를 보거나, 다운로드하거나, 삭제할 수 있습니다.

## 보고서 생성 {#generate-reports}

[!DNL Experience Manager Assets]은(는) 다음 표준 보고서를 생성합니다.

* 업로드
* 다운로드
* 만료
* 수정
* 게시
* [!DNL Brand Portal] 게시
* 디스크 사용량
* 파일
* 공유 링크

<!-- Removed download report.
* Upload
* Download
* Expiration
* Modification
* Publish
* [!DNL Brand Portal] publish
* Disk Usage
* Files
* Link Share
-->

[!DNL Adobe Experience Manager] 관리자는 사용자의 구현을 위해 이러한 보고서를 쉽게 생성하고 사용자 지정할 수 있습니다. 관리자는 다음 단계에 따라 보고서를 생성할 수 있습니다.

1. [!DNL Experience Manager] 인터페이스에서 **[!UICONTROL 도구]** > **[!UICONTROL Assets]** > **[!UICONTROL 보고서]**&#x200B;를 클릭합니다.

   자산 보고서를 탐색할 ![도구 페이지](assets/navigation.png)

1. [!UICONTROL 자산 보고서] 페이지의 도구 모음에서 **[!UICONTROL 만들기]**&#x200B;를 클릭합니다.
1. **[!UICONTROL 보고서 만들기]** 페이지에서 만들려는 보고서를 선택하고 **[!UICONTROL 다음]**&#x200B;을 클릭합니다.

   ![보고서 유형 선택](assets/choose_report.png)

1. 제목, 설명, 썸네일 및 폴더 경로 등 보고서 세부 사항을 구성합니다. 기본적으로 폴더 경로는 `/content/dam`입니다. 특정 폴더에서 보고서를 실행할 다른 경로를 지정할 수 있습니다.

   ![보고서 세부 정보를 추가할 페이지](assets/report_configuration.png)

   보고서의 날짜 범위를 선택합니다. 지금 또는 미래 날짜 및 시간에 보고서를 생성하도록 선택할 수 있습니다.

   >[!NOTE]
   >
   >보고서를 나중에 예약하도록 선택하는 경우 날짜 및 시간 필드에 날짜 및 시간을 지정해야 합니다. 값을 지정하지 않으면 보고서 엔진은 값을 즉시 생성할 보고서로 처리합니다.

   구성 필드는 사용자가 만드는 보고서 유형에 따라 다를 수 있습니다. 예를 들어, **[!UICONTROL 디스크 사용]** 보고서는 에셋에서 사용하는 디스크 공간을 계산할 때 에셋 변환을 포함하는 옵션을 제공합니다. 디스크 사용량 계산을 위해 하위 폴더에 자산을 포함하거나 제외하도록 선택할 수 있습니다.

   >[!NOTE]
   >
   >The **[!UICONTROL Disk Usage]** report does not include date range fields because it indicates current disk space usage only.

   ![디스크 사용량 보고서의 세부 정보 페이지](assets/disk_usage_configuration.png)

   **[!UICONTROL 파일]** 보고서를 만들 때 하위 폴더를 포함/제외할 수 있습니다. 그러나 이 보고서에 대한 에셋 렌디션은 포함할 수 없습니다.

   ![파일 보고서의 세부 정보 페이지](assets/files_report.png)

   **[!UICONTROL 링크 공유]** 보고서에 [!DNL Assets] 내에서 외부 사용자와 공유되는 자산의 URL이 표시됩니다. <!-- It includes email ids of the user who shared the assets, emails ids of users with which the assets are shared, share date, and expiration date for the link. --> 열을 사용자 지정할 수 없습니다.

   **[!UICONTROL 링크 공유]** 보고서는 `/var/dam/share` 아래에 표시되는 공유 URL만 게시하므로 하위 폴더 및 변환에 대한 옵션을 포함하지 않습니다.

   ![링크 공유 보고서의 세부 정보 페이지](assets/link_share.png)

1. 도구 모음에서 **[!UICONTROL 다음]**&#x200B;을 클릭합니다.

1. **[!UICONTROL 열 구성]** 페이지에서 기본적으로 보고서에 표시할 일부 열이 선택되어 있습니다. 열을 더 선택할 수 있습니다. 보고서에서 제외할 열 선택을 취소합니다.

   ![보고서 열 선택 또는 취소](assets/configure_columns.png)

   사용자 지정 열 이름 또는 속성 경로를 표시하려면 CRX의 `jcr:content` 노드 아래에서 에셋 바이너리에 대한 속성을 구성하십시오. 또는 속성 경로 선택기를 통해 추가합니다.

   ![보고서 열 선택 또는 취소](assets/custom_columns.png)

1. 도구 모음에서 **[!UICONTROL 만들기]**&#x200B;를 클릭합니다. 보고서 생성이 시작되었음을 알리는 메시지가 표시됩니다.
1. [!UICONTROL 자산 보고서] 페이지에서 보고서 생성 상태는 보고서 작업의 현재 상태(예: [!UICONTROL 성공], [!UICONTROL 실패], [!UICONTROL 큐에 있음] 또는 [!UICONTROL 예약됨])를 기반으로 합니다. 받은 편지함에도 동일한 상태가 나타납니다.보고서 페이지를 보려면 보고서 링크를 클릭하십시오. 또는 보고서를 선택하고 도구 모음에서 **[!UICONTROL 보기]**&#x200B;를 클릭합니다.

   <!--![A generated report](assets/report_page.png)-->
   ![생성된 보고서 상태](assets/report-status.JPG)

   도구 모음에서 **[!UICONTROL 다운로드]**&#x200B;를 클릭하여 보고서를 CSV 형식으로 다운로드합니다.

   >[!NOTE]
   >
   >지난 360일 동안 생성된 이벤트를 기반으로 보고서를 생성할 수 있습니다. Experience Manager은 30일 동안 사용자 ID 데이터를 유지합니다.

## 보고서에 사용자 정의 열 추가 {#add-custom-columns}

다음 보고서에 사용자 정의 열을 추가하여 사용자 정의 요구 사항에 더 많은 데이터를 표시할 수 있습니다.

<!-- Remove download report.
* Upload
* Download
* Expiration
* Modification
* Publish
* [!DNL Brand Portal] publish
* Files
-->

* 업로드
* 만료
* 수정
* 게시
* [!DNL Brand Portal] 게시
* 파일

이러한 보고서에 사용자 정의 열을 추가하려면 다음 단계를 수행합니다.

1. [!DNL Manager interface]에서 **[!UICONTROL 도구]** > **[!UICONTROL Assets]** > **[!UICONTROL 보고서]**&#x200B;를 클릭합니다.
1. [!UICONTROL 자산 보고서] 페이지의 도구 모음에서 **[!UICONTROL 만들기]**&#x200B;를 클릭합니다.

1. **[!UICONTROL 보고서 만들기]** 페이지에서 만들 보고서를 선택하십시오. **[!UICONTROL 다음]**&#x200B;을 클릭합니다.

1. 제목, 설명, 썸네일, 폴더 경로 및 날짜 범위 등 보고서 세부 사항을 적절히 구성합니다. **[!UICONTROL 다음]**&#x200B;을 클릭합니다.

1. **[!UICONTROL 기본 열]** 목록에서 해당 정보를 선택하십시오. 사용자 지정 열을 표시하려면 **[!UICONTROL 사용자 지정 열]** 아래에 열 이름을 지정하십시오.

   ![보고서의 사용자 지정 열 이름 지정](assets/custom_columns-1.png)

1. 속성 경로 선택기를 사용하여 CRXDE의 `jcr:content` 노드 아래에 속성 경로를 추가합니다. 또는 속성 경로 필드에 경로를 입력합니다.

   ![jcr:content의 경로에서 속성 경로 매핑](assets/property_picker.png)

   사용자 지정 열을 더 추가하려면 **[!UICONTROL 추가]**&#x200B;를 클릭하고 위의 단계를 반복합니다.

1. 도구 모음에서 **[!UICONTROL 만들기]**&#x200B;를 클릭합니다. 보고서 생성이 시작되었음을 알리는 메시지가 표시됩니다.

<!-- TBD: How to configure purge now? Is it using OSGi configurations?

## Configure purging service {#configure-purging-service}

To remove reports that you no longer require, configure the DAM Report Purge service from the web console to purge existing reports based on their quantity and age.

1. Access the web console (configuration manager) from `https://[aem_server]:[port]/system/console/configMgr`.
1. Open the **[!UICONTROL DAM Report Purge Service]** configuration.
1. Specify the frequency (time interval) for the purging service in the `scheduler.expression.name` field. You can also configure the age and the quantity threshold for reports.
1. Save the changes.
-->

## 문제 해결 정보 {#tips-troubleshoot}

* [!UICONTROL 디스크 사용 보고서]가 생성되지 않고 [!DNL Dynamic Media]을(를) 사용 중인 경우 모든 자산이 올바르게 처리되었는지 확인하십시오. 해결하려면 에셋을 재처리하고 보고서를 다시 생성합니다.

<!-- These notes were present in generate report section above. Removing commented text from in between the instructions to preserve the numbering of the ordered list.

TBD: How do enable this in CS now? Is it done using some OSGi config now?
   >[!NOTE]
   >
   >Before you can generate an **[!UICONTROL Asset Downloaded]** report, ensure that the Asset Download service is enabled. From the web console (`https://[aem_server]:[port]/system/console/configMgr`), open the **[!UICONTROL Day CQ DAM Event Recorder]** configuration, and select the **[!UICONTROL Asset Downloaded (DOWNLOADED)]** option in Event Types if not already selected.
-->

<!-- Removed download report.
   >[!NOTE]
   >
   >By default, the Content Fragments and link shares are included in the asset [!UICONTROL Download] report. Select the appropriate option to create a report of link shares or to exclude Content Fragments from the download report.

   >[!NOTE]
   >
   >The [!UICONTROL Download] report displays details of only those assets which are downloaded after selecting individually or are downloaded using Quick Action. However, it does not include the details of the assets that are inside a downloaded folder.
-->

**추가 참조**

* [자산 번역](translate-assets.md)
* [Assets HTTP API](mac-api-assets.md)
* [자산이 지원되는 파일 형식](file-format-support.md)
* [자산 검색](search-assets.md)
* [연결된 자산](use-assets-across-connected-assets-instances.md)
* [메타데이터 스키마](metadata-schemas.md)
* [자산 다운로드](download-assets-from-aem.md)
* [메타데이터 관리](manage-metadata.md)
* [검색 패싯](search-facets.md)
* [컬렉션 관리](manage-collections.md)
* [일괄 메타데이터 가져오기](metadata-import-export.md)
* [AEM 및 Dynamic Media에 자산 게시](/help/assets/publish-assets-to-aem-and-dm.md)
