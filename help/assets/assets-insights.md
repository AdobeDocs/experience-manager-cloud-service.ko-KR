---
title: Assets Insights
description: 서드파티 웹 사이트, 마케팅 캠페인 및 Adobe의 크리에이티브 솔루션에서 사용되는 이미지의 사용자 등급 및 사용 통계를 추적합니다.
contentOwner: AG
feature: Asset Insights, Asset Reports
role: User, Leader
exl-id: e268453b-e7c0-4aa4-bd29-2686edb5f99a
source-git-commit: ab2cf8007546f538ce54ff3e0b92bb0ef399c758
workflow-type: tm+mt
source-wordcount: '901'
ht-degree: 13%

---

# Assets Insights {#asset-insights}

| 버전 | 문서 링크 |
| -------- | ---------------------------- |
| AEM 6.5 | [여기 클릭](https://experienceleague.adobe.com/docs/experience-manager-65/assets/managing/asset-insights.html?lang=en) |
| AEM as a Cloud Service | 이 문서 |

Assets Insights 기능을 사용하면 타사 웹 사이트, 마케팅 캠페인 및 Adobe의 광고 솔루션에서 사용되는 이미지의 사용자 등급 및 사용 통계를 추적할 수 있습니다. 이는 이미지의 성능 및 인기에 대한 통찰력을 제공하는 데 도움이 됩니다.

Assets Insights는 이미지에 대한 등급, 클릭 횟수 및 노출 횟수(이미지가 웹 사이트에 로드되는 횟수) 등 사용자 활동 세부 정보를 캡처합니다. 이러한 통계를 기반으로 이미지에 점수를 할당합니다. 점수 및 성과 통계를 사용하여 카탈로그, 마케팅 캠페인 등에 포함할 인기 있는 이미지를 선택할 수 있습니다. 이러한 통계를 기반으로 아카이브 및 라이선스 갱신 정책을 수립할 수도 있습니다.

Assets Insights가 웹 사이트의 이미지에 대한 사용 통계를 캡처하도록 하려면 웹 사이트 코드에 이미지에 대한 포함 코드를 포함해야 합니다.

Assets Insights에서 에셋에 대한 사용 통계를 표시하도록 하려면 먼저 보고 데이터를 가져올 기능을 구성합니다 [!DNL Adobe Analytics]. 자세한 내용은 [자산 통찰력 구성](#configure-asset-insights). 이 기능을 사용하려면 를 구입하십시오. [!DNL Adobe Analytics] 별도로 라이센스 부여

>[!NOTE]
>
>인사이트는 이미지에 대해서만 지원되고 제공됩니다.

## 이미지에 대한 통계 보기 {#viewing-statistics-for-an-image}

메타데이터 페이지에서 Assets Insights 점수를 볼 수 있습니다.

1. Assets 사용자 인터페이스에서 이미지를 선택한 다음 를 클릭합니다. **[!UICONTROL 속성]** 을 클릭합니다.
1. Properties 페이지에서 **[!UICONTROL Insights]**.
1. 에서 에셋에 대한 사용 세부 사항을 검토합니다. **[!UICONTROL Insights]** 탭. 다음 **[!UICONTROL 점수]** 섹션은 에셋의 총 에셋 사용 및 성능 저장에 대해 설명합니다.

   사용 점수는 다양한 솔루션에서 에셋이 사용된 횟수를 설명합니다.

   다음 **[!UICONTROL 노출 횟수]** score는 웹 사이트에 자산이 로드된 횟수입니다. 아래에 표시된 번호 **[!UICONTROL 클릭수]** 는 에셋을 클릭한 횟수입니다.

1. 리뷰 **[!UICONTROL 사용 통계]** 섹션이 에셋이 속한 엔티티와 최근에 사용한 크리에이티브 솔루션에 대해 알아봅니다. 사용량이 많을수록 해당 자산이 사용자들 사이에서 인기를 끌 가능성도 커진다. 사용 데이터는 다음 헤드 아래에 표시됩니다.

   * **[!UICONTROL 자산]**: 에셋이 컬렉션 또는 복합 에셋에 포함된 횟수입니다.
   * **[!UICONTROL 웹 및 모바일]**: 자산이 웹 사이트 및 앱에 포함된 횟수입니다.
   * **[!UICONTROL 소셜]**: 자산이 다른 솔루션에서 사용된 횟수(예: ) [!DNL Adobe Campaign].
   * **[!UICONTROL 이메일]**: 이메일 캠페인에서 에셋이 사용된 횟수입니다.

   ![usage_statistics](assets/usage_statistics.png)

   >[!NOTE]
   >
   >Assets Insights 기능은 일반적으로 솔루션 데이터를 가져올 수 있기 때문입니다. [!DNL Adobe Analytics] 주기적으로 솔루션 섹션은 가장 최근 데이터를 표시하지 않을 수 있습니다. 데이터가 표시되는 기간은 Assets Insights에서 Analytics 데이터를 검색하기 위해 실행하는 가져오기 작업의 일정에 따라 다릅니다.

1. To view performance statistics for the asset graphically over a period of time, select period in the **[!UICONTROL Performance Statistics]** section. Details, including clicks and impressions are displayed as trend lines of a graph.

   ![chlimage_1-3](assets/chlimage_1-3.jpeg)

   >[!NOTE]
   >
   >솔루션 섹션의 데이터와 달리 성능 통계 섹션에는 가장 최근 데이터가 표시됩니다.

1. 웹 사이트에 포함하여 성능 데이터를 가져오는 에셋에 대한 포함 코드를 얻으려면 다음을 클릭합니다. **[!UICONTROL 포함 코드 가져오기]** 자산 썸네일 아래에 있습니다. <!-- For more information on how to include your Embed code in third-party web pages, see [Using Page Tracker and Embed code in web pages](/help/assets/use-page-tracker.md). -->

   ![chlimage_1-98](assets/chlimage_1-98.png)

## 이미지에 대한 집계 통계 보기 {#viewing-aggregate-statistics-for-images}

You can view scores of all assets within a folder simultaneously using **[!UICONTROL Insights View]**.

1. 자산 사용자 인터페이스에서 인사이트를 보려는 자산이 포함된 폴더로 이동합니다.
1. 다음을 클릭합니다. **[!UICONTROL 레이아웃]** 도구 모음에서 옵션을 선택한 다음 **[!UICONTROL 인사이트 보기]**.
1. 페이지에 에셋에 대한 사용 점수가 표시됩니다. 다양한 에셋의 등급을 비교하고 통찰력을 도출합니다.

<!-- TBD: Commenting as Web Console is not available. Document the appropriate OSGi config method if available in CS.

## Schedule background job {#scheduling-background-job}

Assets Insights fetches usage data for assets from Adobe Analytics report suites in a periodic manner. By default, Assets Insights runs a background job every 24 hours at 2 AM to the fetch data. However, you can modify both the frequency and the time by configuring the **[!UICONTROL Adobe CQ DAM Asset Performance Report Sync Job]** service from the web console.

1. Click the [!DNL Experience Manager] logo, and go to **[!UICONTROL Tools]** > **[!UICONTROL Operations]** > **[!UICONTROL Web Console]**.
1. Open the **[!UICONTROL Adobe CQ DAM Asset Performance Report Sync Job]** service configuration.

   ![chlimage_1-99](assets/chlimage_1-99.png)

1. Specify the desired scheduler frequency and the start time for the job in the property scheduler expression. Save the changes.
-->

## 자산 통찰력 구성 {#configure-asset-insights}

[!DNL Experience Manager Assets] 에서 서드파티 웹 사이트에서 사용하는 디지털 자산에 대한 사용 데이터를 가져옵니다. [!DNL Adobe Analytics]. Assets Insights에서 이 데이터를 검색하고 인사이트를 생성할 수 있도록 하려면 먼저 와 통합하도록 기능을 구성하십시오 [!DNL Adobe Analytics].

>[!NOTE]
>
>인사이트는 이미지만 지원되고 제공됩니다.

1. 위치 [!DNL Experience Manager], 클릭 **[!UICONTROL 도구]** > **[!UICONTROL 에셋]**.

   ![chlimage_1-73](assets/chlimage_1-73.png)

1. Click the **[!UICONTROL Insights Configuration]** card.

1. Analytics 웹 서비스 액세스 정보를 보려면 **[!UICONTROL 분석]** > **[!UICONTROL 관리자]** > **[!UICONTROL 관리 도구]** > **[!UICONTROL 회사 설정]** > **[!UICONTROL 웹 서비스]** 및 복사 **[!UICONTROL 공유 암호]** 키.

   마법사에서 **[!UICONTROL 데이터 센터]**&#x200B;및 의 표시 이름을 입력합니다. **[!UICONTROL 회사]**, 웹 서비스 **[!UICONTROL 사용자 이름]**&#x200B;을(를) 클릭하고 **[!UICONTROL 공유 암호]** 키.

   클릭 **[!UICONTROL 인증]**.

   ![에서 자산 통찰력에 대한 Adobe Analytics 구성 [!DNL Experience Manager]](assets/analytics-insight-config.png)

   *그림: 의 자산 통찰력에 대한 Adobe Analytics 구성[!DNL Experience Manager]*

1. 인증에 성공하면 드롭다운에 보고서 세트 가 나열됩니다. Adobe Analytics 선택 **[!UICONTROL 보고서 세트]** Assets Insights에서 데이터를 가져올 수 있는 위치에 대해 설명합니다. 클릭 **[!UICONTROL 추가]**.

1. 다음 이후 [!DNL Experience Manager] 보고서 세트를 설정하고 **[!UICONTROL 완료]**.

자세한 내용은 [Adobe Analytics 웹 서비스](https://experienceleague.adobe.com/docs/analytics/admin/company-settings/web-services-admin.html#api-access-information).

### 페이지 추적기 {#page-tracker}

Adobe Analytics 계정을 구성하면 페이지 추적기 코드가 생성됩니다. Assets Insights를 활성화하여 [!DNL Experience Manager] 서드파티 웹 사이트에서 사용되는 자산은 웹 사이트 코드에 페이지 추적기 코드를 포함합니다. 자산의 페이지 추적기 유틸리티를 사용하여 페이지 추적기 코드를 생성합니다. <!--  For more information on how to include your Page Tracker code in third-party web pages, see [Using Page Tracker and Embed code in web pages](/help/assets/use-page-tracker.md). -->

1. 위치 [!DNL Experience Manager], 클릭 **[!UICONTROL 도구]** > **[!UICONTROL 에셋]**.

   ![chlimage_1-73](assets/chlimage_1-73.png)

1. From the **[!UICONTROL Navigation]** page, click the **[!UICONTROL Insights Page Tracker]** card.
1. 클릭 **[!UICONTROL 다운로드]** 페이지 추적기 코드를 다운로드하려면 다음을 수행하십시오.

<!--
Add page tracker code, CQDOC-18045, 30/07/2021
-->
다음 샘플 코드 조각은 샘플 웹 페이지에 포함된 페이지 추적기 코드를 표시합니다.

```xml
 <head>
            <script type="text/javascript" src="http://localhost:4502/xxxx/etc.clientlibs/dam/clientlibs/sitecatalyst/appmeasurement.js"></script>
            <script type="text/javascript" src="http://localhost:4502/xxxx/etc.clientlibs/dam/clientlibs/foundation/assetinsights/pagetracker.js"></script>
            <script type="text/javascript">
                                assetAnalytics.attrTrackable = 'trackable';
                assetAnalytics.defaultTrackable = false;
                assetAnalytics.attrAssetID = 'aem-asset-id';
                assetAnalytics.assetImpressionPollInterval = 200; // interval in millis
                assetAnalytics.charsLimitForGET = 2000; // bytes
                assetAnalytics.dispatcher.init("assetstesting","abc.net","bee","list1","eVar3","event8","event7");
            </script>

 </head>
```



<!--

## Using demo package for Assets Insights {#using-demo-package-for-asset-insights}

Using the demo package, you can enable Adobe Assets Insights to capture data from and generate insights for a sample web page.

1. Configure Assets Insights using the instructions in [Configure Assets Insights](#configure-asset-insights).
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
