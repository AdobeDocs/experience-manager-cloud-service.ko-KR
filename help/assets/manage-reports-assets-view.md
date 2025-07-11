---
title: Assets 보기에서 태그 관리
description: Assets 보기의 보고서 섹션에 있는 데이터에 액세스하여 제품 및 기능 사용을 평가하고 주요 성공 지표에 대한 통찰력을 도출합니다.
exl-id: 26d0289e-445a-4b8e-a5a1-b02beedbc3f1
feature: Asset Insights, Asset Reports
role: User, Admin, Developer
hide: true
hidefromtoc: true
source-git-commit: 8aae8b2219e60f0a9220aa34b53bb3c8e19232c1
workflow-type: tm+mt
source-wordcount: '1504'
ht-degree: 86%

---

# 보고서 관리 {#manage-reports}

에셋 보고는 관리자가 Adobe Experience Manager Assets 보기 환경의 활동을 볼 수 있도록 합니다. 이 데이터는 사용자가 콘텐츠 및 제품과 상호 작용하는 방법에 대한 유용한 정보를 제공합니다. 모든 사용자는 인사이트 대시보드에 액세스할 수 있으며 관리자 제품 프로필에 할당된 사용자는 사용자 정의 보고서를 만들 수 있습니다.

## 보고서 액세스 {#access-reports}

AEM 관리자 제품 프로필에 할당된 모든 사용자는 Insights 대시보드에 액세스하거나 Assets 보기에서 사용자 정의 보고서를 만들 수 있습니다.

보고서에 액세스하려면 **[!UICONTROL 설정]** 아래의 **[!UICONTROL 보고서]**&#x200B;로 이동합니다.

![보고서](assets/reports.png)

<!--
In the **[!UICONTROL Reports]** screen, various components are shown in the tabular format which includes the following:

* **Title**: Title of the report
* **Type**: Determines whether the report is uploaded or downloaded to the repository
* **Description**: Provide details of the report that was given during uploading/downloading the report
* **Status**: Determines whether the report is completed, under progress, or deleted.
* **Author**: Provides email of the author who has uploaded/downloaded the report.
* **Created**: Gives information of the date when the report was generated.
-->

## 보고서 만들기 {#create-report}

AEM Assets 보기 환경은 보고서 대시보드를 통해 포괄적인 보고 기능을 제공합니다. 이 기능을 통해 사용자는 지정된 기간(일회성부터 매일, 매주, 매월 또는 매년까지) 내에서 자산 업로드 및 다운로드에 대한 세부 정보를 보여 주는 CSV 보고서를 생성하고 다운로드할 수 있습니다.

**보고서를 만들려면 다음 작업을 수행하십시오.**

1. **보고서**&#x200B;로 이동하고 **보고서 만들기**(오른쪽 상단)를 클릭합니다. **보고서 만들기** 대화 상자에 아래와 같은 필드가 표시됩니다.
   ![보고서 만들기](/help/assets/assets/executed-reports1.svg)

   **구성 탭:**

   1. **보고서 유형:** [!UICONTROL 업로드], [!UICONTROL 다운로드] 또는 [Dynamic Media 게재 보고서](#dynamic-media-delivery-reports) 유형 중에서 선택합니다.
   1. **제목:** 보고서에 제목을 추가합니다.
   1. **설명:** 원하는 경우 보고서에 설명을 추가합니다.
   1. **폴더 경로 선택:** 특정 폴더 내에서 업로드 및 다운로드된 자산에 대한 보고서를 생성할 폴더 경로를 선택합니다. 예를 들어 폴더에 업로드된 자산에 대한 보고서가 필요하다면 해당 폴더의 경로를 지정합니다.
   1. **날짜 간격 선택:** 폴더 내에서의 업로드 또는 다운로드 활동을 조회하려면 날짜 범위를 선택합니다.

   <br>

   >[!NOTE]
   >
   > Assets 보기는 모든 현지 시간대를 UTC(협정 세계시)로 변환합니다.

   **열 탭:** 보고서에 표시할 열 이름을 선택합니다. 다음 테이블에서는 모든 열의 사용에 대해 설명합니다.

   <table>
    <tbody>
     <tr>
      <th><strong>열 이름</strong></th>
      <th><strong>설명</strong></th>
      <th><strong>보고서 유형</strong></th>
     </tr>
     <tr>
      <td>제목</td>
      <td>자산의 제목입니다.</td>
      <td>업로드 및 다운로드</td>
     </tr>
     <tr>
      <td>경로</td>
      <td>Assets 보기에서 자산을 사용할 수 있는 폴더 경로입니다.</td>
      <td>업로드, 다운로드 및 Dynamic Media 게재</td>
     </tr>
     <tr>
      <td>MIME 유형</td>
      <td>자산에 대한 MIME 유형입니다.</td>
      <td>업로드 및 다운로드</td>
     </tr>
     <tr>
      <td>크기</td>
      <td>자산의 크기입니다(바이트).</td>
      <td>업로드 및 다운로드</td>
     </tr>
     <tr>
      <td>다운로드한 사람</td>
      <td>자산을 다운로드한 사용자의 이메일 ID입니다.</td>
      <td>다운로드</td>
     </tr>
     <tr>
      <td>다운로드 날짜</td>
      <td>자산 다운로드 작업이 수행되는 날짜입니다.</td>
      <td>다운로드</td>
     </tr>
     <tr>
      <td>작성자</td>
      <td>자산의 작성자입니다.</td>
      <td>업로드 및 다운로드</td>
     </tr>
     <tr>
      <td>만든 날짜</td>
      <td>자산이 Assets 보기에 업로드되는 날짜입니다.</td>
      <td>업로드 및 다운로드</td>
     </tr>
     <tr>
      <td>수정한 날짜</td>
      <td>자산을 마지막으로 수정한 날짜입니다.</td>
      <td>업로드 및 다운로드</td>
     </tr>
     <tr>
      <td>만료됨</td>
      <td>자산의 만료 상태입니다.</td>
      <td>업로드 및 다운로드</td>
     </tr>
     <tr>
      <td>사용자 이름으로 다운로드됨</td>
      <td>자산을 다운로드한 사용자의 이름입니다.</td>
      <td>다운로드</td>
     </tr> 
     <tr>
      <td>레퍼러</td>
      <td>자산이 게재되거나 포함되는 URL</td>
      <td>Dynamic Media 게재</td>
     </tr>  
     <tr>
      <td>히트 수</td>
      <td>자산이 게재되는 횟수 (게재 횟수)</td>
      <td>Dynamic Media 게재</td>
     </tr>          
    </tbody>
   </table>

## Dynamic Media 게재 보고서 {#dynamic-media-delivery-reports}

자산 수준 게재 카운트, 레퍼러 정보, AEM Assets의 자산 경로 및 고유 자산 ID와 함께 Dynamic Media를 통해 게재된 자산에 대한 게재 인사이트를 확인할 수 있습니다. Dynamic Media를 통해 게재된 AEM Assets 저장소의 모든 자산 또는 AEM Assets 내 특정 폴더 계층 구조의 모든 자산에 대한 보고서를 생성할 수 있습니다. 또한 Dynamic Media 게재 보고서 인사이트는 게재된 자산의 ROI를 측정하고, 채널 성과를 측정하고, 자산에 대해 정보에 입각한 자산 관리 작업을 수행하는 데 도움이 됩니다.

<!--
>[!NOTE]
> 
>To get early access to the Dynamic Media Delivery Report on your Dynamic Media account, [create and submit an Adobe Customer Support case](https://helpx.adobe.com/kr/enterprise/using/support-for-experience-cloud.html).
-->

### 사전 요구 사항 {#prereqs-dynamic-media-delivery-reports}

이 보고서를 만들고 사용하려면 Dynamic Media 라이선스가 있어야 합니다.

>[!IMPORTANT]
> 
>* Dynamic Media를 통해 게재된 자산에 대한 보고서가 제공됩니다.
>* 보고서는 처음 100만 개 행에 대해 생성됩니다. 이 한도 내의 모든 파일을 캡처하려면 더 작은 폴더에 대한 레퍼러 열을 포함하는 방안을 고려해 보십시오.
>* 지난 3개월간의 보고서만 생성할 수 있습니다.

### Dynamic Media 게재 보고서 만들기{#create-dynamic-media-delivery-report}

1. [보고서 만들기](#create-report)에 언급된 단계에 따라 Dynamic Media 게재 보고서를 만드십시오.

1. **[!UICONTROL 보고서 유형]** 드롭다운 목록에서 **[!UICONTROL Dynamic Media 게재]**&#x200B;를 선택합니다.

   ![Dynamic Media 게재 보고서 드롭다운](assets/dynamic-media-delivery-report-option.png)


1. **[!UICONTROL 열]** 탭에서 **[!UICONTROL 레퍼러]** 열을 선택하여 보고서에 포함할 수 있습니다.

   ![레퍼러](assets/referrer.png)

   다운로드한 보고서의 모든 열은 읽기 전용입니다. 단, **레퍼러** 열은 보고서에 포함하거나 제외하도록 수정할 수 있습니다. <!--Choosing a referrer displays the number of visitors received from each referred report that directs traffic to the site. It offers insights into the sources of traffic and the origin of the visitors. Such insights help measure ROI of delivered assets, measure channel performance, and help take informed asset management tasks for assets.-->

### Dynamic Media 게재 보고서에서 수행되는 작업 {#actions-performed-dynamic-media-delivery-reports}

보고서를 생성한 후에는 다음과 같은 작업을 수행할 수 있습니다.

* **[!UICONTROL 삭제]**: 선택한 보고서를 삭제할 수 있습니다.
* **[!UICONTROL CSV 다운로드]**: 선택한 보고서를 CSV 형식으로 다운로드할 수 있습니다. 다운로드한 보고서는 이름, 경로, DynamicMediaID, 레퍼러, 히트 수 열로 구성됩니다.
   * **레퍼러** 열에는 자산이 게재되거나 포함되는 URL이 나열됩니다.

   * **히트 수** 열에는 자산이 게재된 횟수(게재 횟수)가 나열됩니다.

CSV 형식의 Dynamic Media 게재 보고서를 삭제하거나 다운로드하려면 [기존 보고서 조회 및 다운로드](#View-and-download-existing-report)를 참조하십시오.

![Dynamic Media 게재 보고서에 다운로드된 CSV](assets/csv-dynamic-media-delivery-report.png)


## 기존 보고서 조회 및 다운로드 {#View-and-download-existing-report}

기존 보고서는 **실행된 보고서** 탭에 표시됩니다. **보고서**&#x200B;를 클릭하고 **실행된 보고서**&#x200B;를 선택하여 다운로드할 준비가 되었음을 나타내는 **완료됨** 상태의 생성된 모든 보고서를 조회합니다. CSV 형식으로 보고서를 다운로드하거나 보고서를 삭제하려면 해당 보고서 행을 선택하십시오. 그런 다음 **CSV 다운로드** 또는 **삭제**&#x200B;를 선택합니다.
![기존 보고서 조회 및 다운로드](/help/assets/assets/view-download-existing-report.png)


## 보고서 예약 {#schedule-report}

AEM Assets 보기 UI에서 **보고서 예약**&#x200B;은(는) 매일, 주별, 월별 또는 연도별과 같이 지정된 향후 간격으로 보고서를 자동으로 생성합니다. 이 기능은 반복되는 보고 요구 사항을 간소화하고 시기적절한 데이터 업데이트를 보장하는 데 도움이 됩니다. 반면 **보고서 만들기** 기능은 지난 날짜에 대한 보고서를 생성합니다. 완료된 보고서는 **실행된 보고서**&#x200B;에 나열되고, 예정된 보고서는 **예약된 보고서**&#x200B;에서 찾을 수 있습니다.

보고서를 예약하려면 다음 단계를 수행하십시오.

1. 왼쪽 창에서 보고서를 클릭한 다음 보고서 만들기(오른쪽 상단)를 클릭합니다.
1. 보고서 대화 상자에 아래와 같은 정보가 표시됩니다.
   1. **보고서 유형:** 업로드와 다운로드 유형 중에서 선택합니다.
   1. **제목:** 보고서에 제목을 추가합니다.
   1. **설명**: 원하는 경우 보고서에 설명을 추가합니다.
   1. **폴더 경로 선택:** 나중에 특정 폴더에 업로드되거나 해당 폴더에서 다운로드될 자산에 대한 보고서를 생성하려면 폴더 경로를 선택합니다.
   1. **보고서 예약** 토글: 나중에 또는 반복해서 실행되도록 보고서를 예약합니다.

      ![보고서 예약](/help/assets/assets/schedule-reports1.svg)

   1. **빈도 선택:** 보고서 생성 간격(예: 매일, 매주, 매월, 매년 또는 한 번)을 지정하고, 보고서를 실행할 날짜와 시간을 설정하고, 반복 실행 종료 일자를 설정합니다. 일회성 보고서의 경우에는 AEM 환경에서 선택한 활동 유형에 대한 보고서의 날짜 범위를 선택합니다. 예를 들어 특정 월의 10일부터 29일(미래 날짜)까지 다운로드된 자산에 대한 보고서가 필요하다면 **날짜 간격 선택** 필드에서 해당 날짜를 선택합니다.

   >[!NOTE]
   >
   > Assets 보기는 모든 현지 시간대를 UTC(협정 세계시)로 변환합니다.

## 예약된 보고서 보기 {#view-scheduled-reports}

예약된 보고서는 **예약된 보고서** 탭에 체계적으로 정리되고 표시됩니다. 각각의 예약된 보고서에 대해 완료된 보고서는 모두 단일 보고서 폴더에 저장됩니다. 완료된 보고서를 보려면 ![축소 확장](/help/assets/assets/expand-icon1.svg)을 클릭하십시오. 예를 들어 일일 보고서를 예약한 경우 완료된 보고서는 모두 하나의 폴더에 그룹화됩니다. 이러한 구성은 보고서의 탐색과 검색 과정을 모두 간소화해 줍니다. 예약된 보고서를 보려면 **보고서**&#x200B;를 클릭한 다음 **예약된 보고서**&#x200B;를 클릭합니다. 모든 예약된 보고서는 진행 중 또는 완료됨 상태로 표시됩니다. 완료된 보고서를 다운로드할 준비가 되었습니다.\
![예약된 보고서](/help/assets/assets/scheduled-reports-tab.png)

## 예약된 보고서 편집 및 취소 {#edit-cancel-scheduled-reports}

1. **예약된 보고서** 탭으로 이동합니다.
1. 보고서 행을 선택합니다.
1. **편집**&#x200B;을 클릭합니다.
1. **예약 취소**&#x200B;를 클릭한 다음 **확인**&#x200B;을 클릭하면 예약된 보고서가 취소됩니다. 취소된 보고서의 경우 다음번 실행 시간은 비워지고 상태가 취소됨으로 표시됩니다.
   ![예약된 보고서 편집 및 취소](/help/assets/assets/cancel-edit-scheduled-reports.png)

### 예약 재개 {#resume-schedule}

취소된 예약을 재개하려면 보고서 행을 선택하고 **예약 재개**&#x200B;를 클릭합니다. 재개하면 다음 런타임 항목이 다시 표시되고 상태가 진행 중으로 표시됩니다.
![예약 재개](/help/assets/assets/resume-schedule.png)

>[!NOTE]
>
> 예약된 종료일 전에 취소된 보고서를 재개하는 경우 취소일부터 재개일까지의 보고서가 자동으로 생성됩니다.

## 인사이트 보기 {#view-live-statistics}

Assets 보기를 사용하면 [인사이트] 대시보드를 사용하여 Assets 보기 환경에 대한 실시간 데이터를 볼 수 있습니다. 지난 30일 동안 또는 지난 12개월 동안의 실시간 이벤트 지표를 볼 수 있습니다.

<!--![Toolbar options when you select an asset](assets/assets-view-live-statistics.png)-->

자동 생성된 다음과 같은 차트를 보려면 왼쪽 탐색 창에 있는 **[!UICONTROL 인사이트]**&#x200B;를 클릭하십시오.

* **다운로드**: 지난 30일 또는 12개월 동안 Assets 보기 환경에서 다운로드한 에셋 수를 선 그래프로 표시합니다.
  ![인사이트-다운로드](/help/assets/assets/insights-downloads2341.svg)

* **업로드**: 지난 30일 또는 12개월 동안 Assets 보기 환경에 업로드된 에셋 수를 선 그래프로 표시합니다.
  ![인사이트 업로드](/help/assets/assets/insights-uplods2.svg)
<!--* **Asset Count by Size**: The division of count of assets based on their range of various sizes from 0 MB to 100 GB.

* **Storage usage**: The storage usage, in bytes, for the Assets view environment represented using a bar chart.
![insights-uploads](/help/assets/assets/insights-storage-usage1.svg)
<!--* **Delivery**: The graph depicts the count of assets as the delivery dates.-->

<!--* **Asset Count by Asset Type**: Represents count of various MIME types of the available assets. For example, application/zip, image/png, video/mp4, application/postscripte.-->

* **인기 검색어**: 지난 30일 또는 12개월 동안 Assets 보기 환경에서 해당 용어가 검색된 횟수와 함께 가장 많이 검색된 용어를 표 형식으로 표시합니다.
  ![인사이트 업로드](/help/assets/assets/insights-top-search.svg)
  <!--
   ![Insights](assets/insights1.png)
   ![Insights](assets/insights2.png)
   -->
* **크기별 자산 수:** 자산 보기 환경의 총 자산 수를 다양한 크기 범위로 세그먼트화하고 도넛 차트로 표시되는 각 크기 범위의 자산 수와 비율을 강조 표시합니다.
  ![인사이트-크기별-자산-수](/help/assets/assets/insights-assets-count-by-size.svg)
* **자산 유형별 자산 수:** Assets 보기 환경의 총 자산 수를 세그먼트화하며, 파일 유형에 따라 자산의 수와 비율을 강조 표시합니다. 도넛 차트로 표시됩니다.
  ![인사이트-크기별-자산-수](/help/assets/assets/insights-assest-count-by-asset-type1.svg)