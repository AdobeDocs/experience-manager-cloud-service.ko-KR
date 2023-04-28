---
title: 사용 및 공유에 대한 보고서
description: 의 자산에 대한 보고서 [!DNL Adobe Experience Manager Assets] 디지털 자산의 사용, 활동 및 공유를 이해하는 데 도움이 됩니다.
contentOwner: AG
feature: Asset Reports,Asset Management
role: Admin,User
exl-id: ef617b01-0019-4379-8d58-c03215d7e28f
source-git-commit: 8bdd89f0be5fe7c9d4f6ba891d7d108286f823bb
workflow-type: tm+mt
source-wordcount: '918'
ht-degree: 10%

---

# 에셋 보고서 {#asset-reports}

자산 보고를 사용하여 [!DNL Adobe Experience Manager Assets] 배포. 사용 [!DNL Assets], 디지털 자산에 대한 다양한 보고서를 생성할 수 있습니다. 이 보고서는 시스템의 사용, 사용자가 자산과 상호 작용하는 방법 및 어떤 자산인지에 대한 유용한 정보를 제공합니다 <!-- downloaded and --> 공유.

보고서에서 정보를 사용하여 주요 성공 지표를 도출하여 [!DNL Assets] 엔터프라이즈 및 고객별

다음 [!DNL Assets] 보고 프레임워크 사용 [!DNL Sling] 주문 방식으로 보고서 요청을 비동기식으로 처리하는 작업입니다. 대형 저장소에 대해 확장 가능합니다. 비동기 보고서 처리는 보고서가 생성되는 효율과 속도를 높입니다.

보고서 관리 인터페이스는 직관적이며, 보관된 보고서에 액세스하고 보고서 실행 상태(성공, 실패 및 큐)를 볼 수 있는 세분화된 옵션과 컨트롤을 제공합니다.

보고서가 생성되면 을 통해 알림을 받습니다 <!-- through an email (optional) and --> 받은 편지함 알림. 이전에 생성한 모든 보고서가 표시되는 보고서 목록 페이지에서 보고서를 보거나, 다운로드하거나, 삭제할 수 있습니다.

## 보고서 생성 {#generate-reports}

[!DNL Experience Manager Assets] 는 다음과 같은 표준 보고서를 생성합니다.

* 업로드
* 다운로드
* 만료
* 수정
* 게시
* [!DNL Brand Portal] 페이지를
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

[!DNL Adobe Experience Manager] 관리자는 구현을 위해 이러한 보고서를 쉽게 생성하고 사용자 지정할 수 있습니다. 관리자는 다음 단계에 따라 보고서를 생성할 수 있습니다.

1. in [!DNL Experience Manager] 인터페이스, **[!UICONTROL 도구]** > **[!UICONTROL 자산]** > **[!UICONTROL 보고서]**.

   ![자산 보고서를 탐색하는 도구 페이지](assets/navigation.png)

1. 설정 [!UICONTROL 자산 보고서] 페이지를 클릭한 다음 **[!UICONTROL 만들기]** 를 클릭합니다.
1. 에서 **[!UICONTROL 보고서 만들기]** 페이지에서 만들려는 보고서를 선택하고 **[!UICONTROL 다음]**.

   ![보고서 유형 선택](assets/choose_report.png)

1. 제목, 설명, 축소판 및 폴더 경로와 같은 보고서 세부 정보를 구성합니다. 기본적으로 폴더 경로는 다음과 같습니다 `/content/dam`. 특정 폴더에서 보고서를 실행할 다른 경로를 지정할 수 있습니다.

   ![보고서 세부 사항을 추가하는 페이지](assets/report_configuration.png)

   보고서의 날짜 범위를 선택합니다. 지금 또는 미래 날짜 및 시간에 보고서를 생성하도록 선택할 수 있습니다.

   >[!NOTE]
   >
   >나중에 보고서를 예약하도록 선택하는 경우 날짜 및 시간 필드에 날짜와 시간을 지정해야 합니다. 값을 지정하지 않으면 보고서 엔진은 값을 즉시 생성할 보고서로 처리합니다.

   구성 필드는 만드는 보고서 유형에 따라 다를 수 있습니다. 예: **[!UICONTROL 디스크 사용]** 보고서는 자산에 사용되는 디스크 공간을 계산할 때 자산 표현물을 포함하는 옵션을 제공합니다. 디스크 사용 계산을 위해 하위 폴더에 자산을 포함하거나 제외하도록 선택할 수 있습니다.

   >[!NOTE]
   >
   >The **[!UICONTROL Disk Usage]** report does not include date range fields because it indicates current disk space usage only.

   ![디스크 사용량 보고서 세부 정보 페이지](assets/disk_usage_configuration.png)

   를 만들 때 **[!UICONTROL 파일]** 보고서에서 하위 폴더를 포함/제외할 수 있습니다. 그러나 이 보고서에 대한 자산 표현물은 포함할 수 없습니다.

   ![파일 보고서의 세부 정보 페이지](assets/files_report.png)

   The **[!UICONTROL Link Share]** report displays URLs to assets that are shared with external users from within [!DNL Assets]. <!-- It includes email ids of the user who shared the assets, emails ids of users with which the assets are shared, share date, and expiration date for the link. --> The columns are not customizable.

   다음 **[!UICONTROL 링크 공유]** 보고서에는 아래에 표시되는 공유 URL만 게시하므로 하위 폴더 및 표현물에 대한 옵션이 포함되지 않습니다 `/var/dam/share`.

   ![링크 공유 보고서의 세부 사항 페이지](assets/link_share.png)

1. 클릭 **[!UICONTROL 다음]** 를 클릭합니다.

1. 에서 **[!UICONTROL 열 구성]** 페이지, 기본적으로 보고서에 일부 열이 나타나도록 선택됩니다. 열을 더 선택할 수 있습니다. 보고서에서 제외할 열 선택을 취소합니다.

   ![보고서 열 선택 또는 취소](assets/configure_columns.png)

   사용자 지정 열 이름 또는 속성 경로를 표시하려면 `jcr:content` 노드 아래에 있어야 합니다. 또는 속성 경로 선택기를 통해 추가합니다.

   ![보고서 열 선택 또는 취소](assets/custom_columns.png)

1. 클릭 **[!UICONTROL 만들기]** 를 클릭합니다. 보고서 생성이 시작되었음을 알리는 메시지가 표시됩니다.
1. 설정 [!UICONTROL 자산 보고서] 페이지, 보고서 생성 상태는 보고서 작업의 현재 상태를 기반으로 합니다(예: ) [!UICONTROL 성공], [!UICONTROL 실패], [!UICONTROL 큐에 있음], 또는 [!UICONTROL 예약됨]. 알림 받은 편지함에 동일한 상태가 표시됩니다.보고서 페이지를 보려면 보고서 링크를 클릭하십시오. 또는 보고서를 선택하고 을(를) 클릭합니다 **[!UICONTROL 보기]** 를 클릭합니다.

   ![생성된 보고서](assets/report_page.png)

   클릭 **[!UICONTROL 다운로드]** 를 클릭하여 보고서를 CSV 형식으로 다운로드합니다.

   >[!NOTE]
   >
   >지난 360일 동안 생성된 이벤트를 기반으로 보고서를 생성할 수 있습니다. Experience Manager은 30일 동안 사용자 ID 데이터를 유지합니다.

## 보고서에 사용자 지정 열 추가 {#add-custom-columns}

다음 보고서에 사용자 지정 열을 추가하여 사용자 지정 요구 사항에 대한 더 많은 데이터를 표시할 수 있습니다.

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
* [!DNL Brand Portal] 페이지를
* 파일

이러한 보고서에 사용자 지정 열을 추가하려면 다음 단계를 수행합니다.

1. 에서 [!DNL Manager interface]를 클릭합니다. **[!UICONTROL 도구]** > **[!UICONTROL 자산]** > **[!UICONTROL 보고서]**.
1. 설정 [!UICONTROL 자산 보고서] 페이지를 클릭한 다음 **[!UICONTROL 만들기]** 를 클릭합니다.

1. 에서 **[!UICONTROL 보고서 만들기]** 페이지에서 만들 보고서를 선택합니다. **[!UICONTROL 다음]**&#x200B;을 클릭합니다.

1. 제목, 설명, 축소판, 폴더 경로 및 날짜 범위와 같은 보고서 세부 정보를 해당하는 대로 구성합니다. **[!UICONTROL 다음]**&#x200B;을 클릭합니다.

1. 다음 목록에서 해당 정보를 선택합니다 **[!UICONTROL 기본 열]**. To display a custom column, specify the name of the column under **[!UICONTROL Custom Columns]**.

   ![보고서의 사용자 지정 열에 대한 이름을 지정합니다](assets/custom_columns-1.png)

1. 아래에 속성 경로를 추가합니다. `jcr:content` property path 선택기를 사용하여 CRXDE에 노드를 추가합니다. 또는 속성 경로 필드에 경로를 입력합니다.

   ![jcr:content의 경로에서 속성 경로를 매핑합니다](assets/property_picker.png)

   사용자 지정 열을 추가하려면 **[!UICONTROL 추가]** 위의 단계를 반복합니다.

1. 클릭 **[!UICONTROL 만들기]** 를 클릭합니다. 보고서 생성이 시작되었음을 알리는 메시지가 표시됩니다.

<!-- TBD: How to configure purge now? Is it using OSGi configurations?

## Configure purging service {#configure-purging-service}

To remove reports that you no longer require, configure the DAM Report Purge service from the web console to purge existing reports based on their quantity and age.

1. Access the web console (configuration manager) from `https://[aem_server]:[port]/system/console/configMgr`.
1. Open the **[!UICONTROL DAM Report Purge Service]** configuration.
1. Specify the frequency (time interval) for the purging service in the `scheduler.expression.name` field. You can also configure the age and the quantity threshold for reports.
1. Save the changes.
-->

## 문제 해결 정보 {#tips-troubleshoot}

* 만약 [!UICONTROL 디스크 사용량 보고서] 는 생성되지 않으며 [!DNL Dynamic Media]를 눌러 모든 자산이 올바르게 처리되는지 확인합니다. 해결하려면 자산을 재처리하고 보고서를 다시 생성합니다.

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

* [에셋 번역](translate-assets.md)
* [Assets HTTP API](mac-api-assets.md)
* [자산 지원 파일 형식](file-format-support.md)
* [에셋 검색](search-assets.md)
* [연결된 자산](use-assets-across-connected-assets-instances.md)
* [메타데이터 스키마](metadata-schemas.md)
* [에셋 다운로드](download-assets-from-aem.md)
* [메타데이터 관리](manage-metadata.md)
* [검색 패싯](search-facets.md)
* [컬렉션 관리](manage-collections.md)
* [벌크 메타데이터 가져오기](metadata-import-export.md)
