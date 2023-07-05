---
title: 자산 보기에서 보고서 관리
description: 자산 보기의 보고서 섹션에 있는 데이터에 액세스하여 제품 및 기능 사용을 평가하고 주요 성공 지표에 대한 통찰력을 도출합니다.
exl-id: c7155459-05d9-4a95-a91f-a1fa6ae9d9a4
source-git-commit: df82681338f8ca1a34df6118cbddc6642aa8d4b5
workflow-type: tm+mt
source-wordcount: '814'
ht-degree: 75%

---

# 보고서 관리 {#manage-reports}

>[!CONTEXTUALHELP]
>id="assets_reports"
>title="보고서"
>abstract="자산 보고는 관리자가 Adobe Experience Manager Assets 보기 환경의 활동을 조회할 수 있도록 해 줍니다. 이 데이터는 사용자가 콘텐츠 및 제품과 상호 작용하는 방법에 대한 유용한 정보를 제공합니다. 관리자 제품 프로필에 할당된 모든 사용자는 Insights 대시보드에 액세스하거나 사용자 정의 보고서를 만들 수 있습니다."

자산 보고는 관리자가 Adobe Experience Manager Assets 보기 환경의 활동을 조회할 수 있도록 해 줍니다. 이 데이터는 사용자가 콘텐츠 및 제품과 상호 작용하는 방법에 대한 유용한 정보를 제공합니다.

## 보고서 액세스 {#access-reports}

자산 보기 관리자 제품 프로필에 할당된 모든 사용자는 Insights 대시보드에 액세스하거나 자산 보기에서 사용자 정의 보고서를 만들 수 있습니다.

## 인사이트 보기 {#view-live-statistics}

에셋 보기를 사용하면 인사이트 대시보드를 사용하여 에셋 보기 환경에 대한 실시간 데이터를 볼 수 있습니다. 지난 30일 동안 또는 지난 12개월 동안의 실시간 이벤트 지표를 볼 수 있습니다.

![자산 선택 시 도구 모음 옵션](assets/assets-essentials-live-statistics.png)

자동 생성된 다음과 같은 차트를 보려면 왼쪽 탐색 창에 있는 **[!UICONTROL 인사이트]**&#x200B;를 클릭하십시오.

* **다운로드**: 지난 30일 또는 12개월 동안 자산 보기 환경에서 다운로드한 자산 수를 선 차트로 표시합니다.

* **업로드**: 지난 30일 또는 12개월 동안 자산 보기 환경에 업로드된 자산 수를 선 차트로 표시합니다.

* **상위 검색**: 지난 30일 또는 12개월 동안 Assets 보기 환경 내에서 검색한 검색어 횟수와 함께 표 형식으로 표시된 검색어를 표시합니다.

<!--

* **Storage usage**: The storage usage, in gigabytes (GB), for the Assets view environment, for the last 30 days or 12 months represented using a bar chart.

-->

## 다운로드 보고서 만들기 {#create-download-report}

다운로드 보고서를 만들려면 다음 단계를 수행합니다.

1. **[!UICONTROL 설정]** > **[!UICONTROL 보고서]**&#x200B;로 이동한 다음 **[!UICONTROL 보고서 만들기]**&#x200B;를 클릭합니다.

1. [!UICONTROL 구성] 탭에서 보고서 유형을 **[!UICONTROL 다운로드]**&#x200B;로 지정합니다.

1. 보고서에 대한 제목 및 설명(선택 사항)을 지정합니다.

1. **[!UICONTROL 폴더 경로 선택]** 필드를 사용하여 보고서를 실행할 자산을 구성하는 폴더 경로를 선택합니다.

1. 보고서의 날짜 간격을 선택합니다.

   >[!NOTE]
   >
   > 에셋 보기는 모든 현지 시간대를 UTC(협정 세계시)로 변환합니다.

1. [!UICONTROL 열] 탭에서 보고서에 표시해야 하는 열 이름을 선택합니다.

1. **[!UICONTROL 만들기]**&#x200B;를 클릭합니다.

   ![보고서 다운로드](assets/download-reports-config.png)

다음 표에서는 보고서에 추가할 수 있는 모든 열의 사용에 대해 설명합니다.

<table>
    <tbody>
     <tr>
      <th><strong>열 이름</strong></th>
      <th><strong>설명</strong></th>
     </tr>
     <tr>
      <td>제목</td>
      <td>자산의 제목입니다.</td>
     </tr>
     <tr>
      <td>경로</td>
      <td>에셋 보기에서 에셋을 사용할 수 있는 폴더 경로입니다.</td>
     </tr>
     <tr>
      <td>MIME 유형</td>
      <td>자산에 대한 MIME 유형입니다.</td>
     </tr>
     <tr>
      <td>크기</td>
      <td>자산의 크기입니다(바이트).</td>
     </tr>
     <tr>
      <td>다운로드한 사람</td>
      <td>자산을 다운로드한 사용자의 이메일 ID입니다.</td>
     </tr>
     <tr>
      <td>다운로드 날짜</td>
      <td>자산 다운로드 작업이 수행되는 날짜입니다.</td>
     </tr>
     <tr>
      <td>작성자</td>
      <td>자산의 작성자입니다.</td>
     </tr>
     <tr>
      <td>만든 날짜</td>
      <td>에셋이 에셋 보기에 업로드되는 날짜입니다.</td>
     </tr>
     <tr>
      <td>수정한 날짜</td>
      <td>자산을 마지막으로 수정한 날짜입니다.</td>
     </tr>
     <tr>
      <td>만료됨</td>
      <td>자산의 만료 상태입니다.</td>
     </tr>
     <tr>
      <td>사용자 이름으로 다운로드됨</td>
      <td>자산을 다운로드한 사용자의 이름입니다.</td>
     </tr>           
    </tbody>
   </table>

## 업로드 보고서 만들기 {#create-upload-report}

업로드 보고서를 만들려면 다음 작업을 수행하십시오.

1. **[!UICONTROL 설정]** > **[!UICONTROL 보고서]**&#x200B;로 이동한 다음 **[!UICONTROL 보고서 만들기]**&#x200B;를 클릭합니다.

1. [!UICONTROL 구성] 탭에서 보고서 유형을 **[!UICONTROL 업로드]**&#x200B;로 지정합니다.

1. 보고서에 대한 제목 및 설명(선택 사항)을 지정합니다.

1. **[!UICONTROL 폴더 경로 선택]** 필드를 사용하여 보고서를 실행할 자산을 구성하는 폴더 경로를 선택합니다.

1. 보고서의 날짜 간격을 선택합니다.

1. [!UICONTROL 열] 탭에서 보고서에 표시해야 하는 열 이름을 선택합니다.

1. **[!UICONTROL 만들기]**&#x200B;를 클릭합니다.

   ![보고서 업로드](assets/upload-reports-config.png)

다음 표에서는 보고서에 추가할 수 있는 모든 열의 사용에 대해 설명합니다.

<table>
    <tbody>
     <tr>
      <th><strong>열 이름</strong></th>
      <th><strong>설명</strong></th>
     </tr>
     <tr>
      <td>제목</td>
      <td>자산의 제목입니다.</td>
     </tr>
     <tr>
      <td>경로</td>
      <td>에셋 보기에서 에셋을 사용할 수 있는 폴더 경로입니다.</td>
     </tr>
     <tr>
      <td>MIME 유형</td>
      <td>자산에 대한 MIME 유형입니다.</td>
     </tr>
     <tr>
      <td>크기</td>
      <td>자산의 크기입니다.</td>
     </tr>
     <tr>
      <td>작성자</td>
      <td>자산의 작성자입니다.</td>
     </tr>
     <tr>
      <td>만든 날짜</td>
      <td>에셋이 에셋 보기에 업로드되는 날짜입니다.</td>
     </tr>
     <tr>
      <td>수정한 날짜</td>
      <td>자산을 마지막으로 수정한 날짜입니다.</td>
     </tr>
     <tr>
      <td>만료됨</td>
      <td>자산의 만료 상태입니다.</td>
     </tr>              
    </tbody>
   </table>

## 기존 보고서 보기 {#view-report-list}

[보고서 생성](#create-download-report) 후 기존 보고서 목록을 보고 선택하여 CSV 형식으로 다운로드하거나 삭제할 수 있습니다.

보고서 목록을 보려면 **[!UICONTROL 설정]** > **[!UICONTROL 보고서]**&#x200B;로 이동합니다.

각 보고서에 대해 보고서 제목, 보고서 유형, 보고서를 만들 때 지정된 설명, 보고서 상태, 보고서를 만든 작성자의 이메일 ID 및 보고서 생성 날짜를 볼 수 있습니다.

보고서의 `Completed ` 상태는 보고서를 다운로드할 준비가 되었음을 나타냅니다.

![보고서 목록](assets/list-of-reports.png)


## CSV 보고서 다운로드 {#download-csv-report}

보고서를 CSV 형식으로 다운로드하려면 다음 작업을 수행하십시오.

1. **[!UICONTROL 설정]** > **[!UICONTROL 보고서]**&#x200B;로 이동합니다.

1. 보고서를 선택하고 **[!UICONTROL CSV 다운로드]**&#x200B;를 클릭합니다.

선택한 보고서가 CSV 형식으로 다운로드됩니다. CSV 보고서에 표시되는 열은 [보고서를 생성](#create-download-report)할 때 선택한 열에 따라 다릅니다.

## 보고서 삭제 {#delete-report}

보고서를 삭제하려면 다음 작업을 수행하십시오.

1. **[!UICONTROL 설정]** > **[!UICONTROL 보고서]**&#x200B;로 이동합니다.

1. 보고서를 선택하고 **[!UICONTROL 삭제]**&#x200B;를 클릭합니다.

1. 삭제를 확인하려면 **[!UICONTROL 삭제]**&#x200B;를 다시 클릭합니다.
