---
title: 자산 통찰력
description: 자산 인사이트 기능을 사용하여 타사 웹 사이트, 마케팅 캠페인 및 Adobe의 크리에이티브 솔루션에 사용되는 이미지의 사용자 등급과 사용 통계를 추적하는 방법을 알아봅니다.
contentOwner: AG
translation-type: tm+mt
source-git-commit: ce22a7ba95942881b90a4f3f22d89bcd35b5e559
workflow-type: tm+mt
source-wordcount: '799'
ht-degree: 1%

---


# 자산 통찰력 {#asset-insights}

자산 통찰력은 타사 웹 사이트, 마케팅 캠페인 및 Adobe의 크리에이티브 솔루션에 사용되는 이미지의 사용자 등급과 사용 통계를 추적합니다. 이 플러그인을 사용하면 이미지의 성능과 인기에 대한 통찰력을 얻을 수 있습니다.

자산 통찰력은 이미지가 평가된 횟수, 클릭 횟수 및 노출 횟수(웹 사이트에서 이미지가 로드되는 횟수)와 같은 사용자 활동 세부 사항을 캡처합니다. 이러한 통계에 따라 이미지에 점수를 지정합니다. 점수 및 성능 통계를 사용하여 카탈로그, 마케팅 캠페인 등에 포함할 인기 있는 이미지를 선택할 수 있습니다. 이러한 통계를 바탕으로 보관 및 라이선스 갱신 정책을 수립할 수도 있습니다.

자산 통찰력이 웹 사이트의 이미지에 대한 사용 통계를 캡처하려면 웹 사이트 코드에 이미지의 포함 코드를 포함해야 합니다.

자산 통찰력이 자산에 대한 사용 통계를 표시하도록 하려면 먼저 Adobe Analytics에서 보고 데이터를 가져오기 위한 기능을 구성합니다. 자세한 내용은 [자산 인사이트 구성](#configure-asset-insights)을 참조하십시오.

>[!NOTE]
>
>인사이트는 이미지만 지원되고 제공됩니다.

## 이미지 {#viewing-statistics-for-an-image} 통계 보기

메타데이터 페이지에서 자산 통찰력 점수를 볼 수 있습니다.

1. 자산 사용자 인터페이스(UI)에서 이미지를 선택한 다음 도구 모음에서 **[!UICONTROL 속성]**&#x200B;을 탭합니다.
1. 속성 페이지에서 **[!UICONTROL 인사이트]**&#x200B;를 누릅니다.
1. **[!UICONTROL 인사이트]** 탭에서 자산의 사용 세부 정보를 검토하십시오. **[!UICONTROL 점수]** 섹션에서는 자산의 총 자산 사용 및 성능 포인트에 대해 설명합니다.

   사용 점수는 다양한 솔루션에서 자산이 사용되는 횟수를 설명합니다.

   **[!UICONTROL 노출 횟수]** 점수는 웹 사이트에서 자산이 로드되는 횟수입니다. **[!UICONTROL 클릭]** 아래에 표시되는 숫자는 자산을 클릭한 횟수입니다.

1. **[!UICONTROL 사용 통계]** 섹션을 검토하여 자산이 속한 엔터티와 최근에 사용한 크리에이티브 솔루션을 확인합니다. 사용량이 많을수록 사용자 간에 자산이 인기 있을 가능성이 높습니다. 사용 데이터는 다음 헤드에 표시됩니다.

   * **[!UICONTROL 자산]**:자산이 컬렉션 또는 복합 자산의 일부인 횟수입니다.
   * **[!UICONTROL 웹 및 모바일]**:자산이 웹 사이트 및 앱의 일부인 횟수입니다.
   * **[!UICONTROL 소셜]**:Adobe Social, Adobe Campaign 같은 솔루션에 자산이 사용된 횟수입니다.
   * **[!UICONTROL 이메일]**:이메일 캠페인에서 자산이 사용된 횟수입니다.

   ![usage_statistics](assets/usage_statistics.png)

   >[!NOTE]
   >
   >자산 통찰력 기능은 일반적으로 Adobe Analytics에서 정기적으로 솔루션 데이터를 가져오기 때문에 솔루션 섹션에 가장 최근 데이터가 표시되지 않을 수 있습니다. 데이터가 표시되는 기간은 자산 통찰력이 Analytics 데이터를 검색하기 위해 실행하는 가져오기 작업의 예약에 따라 다릅니다.

1. 일정 기간 동안 자산에 대한 성능 통계를 그래픽으로 보려면 **[!UICONTROL 성과 통계]** 섹션에서 기간을 선택합니다. 클릭 및 노출 수를 비롯한 세부 사항은 그래프의 트렌드 라인으로 표시됩니다.

   ![chlimage_1-3](assets/chlimage_1-3.jpeg)

   >[!NOTE]
   >
   >솔루션 섹션의 데이터와 달리 성능 통계 섹션에는 최신 데이터가 표시됩니다.

1. 성능 데이터를 가져오기 위해 웹 사이트에 포함하는 자산의 포함 코드를 가져오려면 자산 축소판 아래에 있는 **[!UICONTROL 포함 코드 가져오기]**&#x200B;를 탭/클릭합니다.<!-- For more information on how to include your Embed code in third-party web pages, see [Using Page Tracker and Embed code in web pages](/help/assets/use-page-tracker.md). -->

   ![chlimage_1-98](assets/chlimage_1-98.png)

## {#viewing-aggregate-statistics-for-images} 이미지에 대한 집계 통계 보기

**[!UICONTROL 인사이트 보기]**&#x200B;를 사용하여 폴더 내의 모든 자산의 점수를 동시에 볼 수 있습니다.

1. 자산 UI에서 인사이트를 보려는 자산이 들어 있는 폴더로 이동합니다.
1. 도구 모음에서 레이아웃 아이콘을 탭/클릭한 다음 **[!UICONTROL 인사이트 보기]**&#x200B;를 선택합니다.
1. 이 페이지에는 자산의 사용 점수가 표시됩니다. 다양한 자산의 등급을 비교하고 인사이트를 도출할 수 있습니다.

<!-- TBD: Commenting as Web Console is not available. Document the appropriate OSGi config method if available in CS.

## Schedule background job {#scheduling-background-job}

Asset Insights fetches usage data for assets from Adobe Analytics report suites in a periodic manner. By default, Asset Insights runs a background job every 24 hours at 2 AM to the fetch data. However, you can modify both the frequency and the time by configuring the **[!UICONTROL Adobe CQ DAM Asset Performance Report Sync Job]** service from the web console.

1. Click the [!DNL Experience Manager] logo, and go to **[!UICONTROL Tools]** &gt; **[!UICONTROL Operations]** &gt; **[!UICONTROL Web Console]**.
1. Open the **[!UICONTROL Adobe CQ DAM Asset Performance Report Sync Job]** service configuration.

   ![chlimage_1-99](assets/chlimage_1-99.png)

1. Specify the desired scheduler frequency and the start time for the job in the property scheduler expression. Save the changes.
-->

## 자산 인사이트 구성 {#configure-asset-insights}

[!DNL Experience Manager Assets] 타사 웹 사이트에서 사용되는 디지털 자산에 대한 사용 데이터를 가져옵니다 [!DNL Adobe Analytics]. 자산 인사이트에서 이 데이터를 검색하고 인사이트를 생성하려면 먼저 [!DNL Adobe Analytics]과(와) 통합되도록 기능을 구성하십시오.

>[!NOTE]
>
>인사이트는 이미지만 지원되고 제공됩니다.

1. [!DNL Experience Manager]에서 **[!UICONTROL 도구]** > **[!UICONTROL 자산]**&#x200B;을 클릭합니다.

   ![chlimage_1-72](assets/chlimage_1-72.png)

1. **[!UICONTROL 인사이트 구성]** 카드를 클릭합니다.
1. 마법사에서 데이터 센터를 선택하고 조직의 이름, 사용자 이름 및 공유 암호를 비롯한 자격 증명을 제공합니다.

   ![자산 통찰력에 대한 Adobe Analytics 구성  [!DNL Experience Manager]](assets/insights_config2.png)

   *그림:자산 통찰력에 대한 Adobe Analytics 구성[!DNL Experience Manager]*

1. **[!UICONTROL 인증]**&#x200B;을 클릭/탭합니다. [!DNL Experience Manager] 자격 증명을 인증한 후 **[!UICONTROL 보고서 세트]** 목록에서 자산 통찰력을 가져올 Adobe Analytics 보고서 세트를 선택합니다. **[!UICONTROL 추가]**&#x200B;를 클릭합니다.
1. [!DNL Experience Manager]이 보고서 세트를 설정한 후 **[!UICONTROL Done]**&#x200B;을 탭합니다.

### 페이지 추적기 {#page-tracker}

Adobe Analytics 계정을 구성하면 페이지 추적기 코드가 자동으로 생성됩니다. 자산 통찰력이 타사 웹 사이트에서 사용되는 [!DNL Experience Manager] 자산을 추적하도록 하려면 웹 사이트 코드에 페이지 추적기 코드를 포함시키십시오. 자산의 페이지 추적기 유틸리티를 사용하여 페이지 추적기 코드를 생성합니다.<!--  For more information on how to include your Page Tracker code in third-party web pages, see [Using Page Tracker and Embed code in web pages](/help/assets/use-page-tracker.md). -->

1. [!DNL Experience Manager]에서 **[!UICONTROL 도구]** > **[!UICONTROL 자산]**&#x200B;을 클릭합니다.

   ![chlimage_1-73](assets/chlimage_1-73.png)

1. **[!UICONTROL 내비게이션]** 페이지에서 **[!UICONTROL 인사이트 페이지 추적기]** 카드를 클릭합니다.
1. 페이지 추적기 코드를 다운로드하려면 **[!UICONTROL 다운로드]**&#x200B;를 클릭합니다.

<!--

## Using demo package for Asset Insights {#using-demo-package-for-asset-insights}

Using the demo package, you can enable Adobe Asset Insights to capture data from and generate insights for a sample web page.

1. Configure Asset Insights using the instructions in [Configure Asset Insights](#configure-asset-insights).
1. Download the sample [!DNL Experience Manager Assets] package from below and install the package from CRXDE package manager.

   [Get File](assets/insightsdemo.zip)

1. Download the ZIP file containing the sample web page from below and extract on your local file system.

   [Get File](assets/demosite.zip)

1. Click the web page to open it in the web browser.

   >[!CAUTION]
   >
   >Web Page is configured to load asset from the localhost server . In case your server is running somewhere else change server address from localhost to server address in the HTML content of the web page.

   >[!NOTE]
   >
   >The external web page can be in [!DNL Experience Manager] itself.

-->
