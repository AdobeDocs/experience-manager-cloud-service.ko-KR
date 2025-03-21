---
title: Content Hub에서 자산 통찰력 보기
description: ' [!DNL Content Hub]에서 자산 통찰력을 보는 방법 알아보기'
role: User
exl-id: 29cbe017-856d-486b-acf3-aa47dbd90f3f
source-git-commit: 188f60887a1904fbe4c69f644f6751ca7c9f1cc3
workflow-type: tm+mt
source-wordcount: '352'
ht-degree: 26%

---

# [!DNL Content Hub]의 Assets Insights {#assets-insights}

<table>
    <tr>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>새로 만들기</i></sup> <a href="/help/assets/dynamic-media/dm-prime-ultimate.md"><b>Dynamic Media Prime 및 Ultimate</b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>새로 만들기</i></sup> <a href="/help/assets/assets-ultimate-overview.md"><b>AEM Assets Ultimate</b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>새로 만들기</i></sup> <a href="/help/assets/integrate-aem-assets-edge-delivery-services.md"><b>Edge Delivery Services과 AEM Assets 통합</b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>새로 만들기</i></sup> <a href="/help/assets/aem-assets-view-ui-extensibility.md"><b>UI 확장성</b></a>
        </td>
          <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>새로 만들기</i></sup> <a href="/help/assets/dynamic-media/enable-dynamic-media-prime-and-ultimate.md"><b>Dynamic Media Prime 및 Ultimate 사용</b></a>
        </td>
    </tr>
    <tr>
        <td>
            <a href="/help/assets/search-best-practices.md"><b>모범 사례 검색</b></a>
        </td>
        <td>
            <a href="/help/assets/metadata-best-practices.md"><b>메타데이터 모범 사례</b></a>
        </td>
        <td>
            <a href="/help/assets/product-overview.md"><b>Content Hub</b></a>
        </td>
        <td>
            <a href="/help/assets/dynamic-media-open-apis-overview.md"><b>OpenAPI 기능이 포함된 Dynamic Media</b></a>
        </td>
        <td>
            <a href="https://developer.adobe.com/experience-cloud/experience-manager-apis/"><b>AEM Assets 개발자 설명서</b></a>
        </td>
    </tr>
</table>

![Assets 인사이트](assets/asset-insights-banner.jpg)

>[!AVAILABILITY]
>
>Content Hub 안내서가 이제 PDF 포맷으로 제공됩니다. 전체 안내서를 다운로드하고 Adobe Acrobat AI 어시스턴트를 사용하여 쿼리에 답변합니다.
>
>[!BADGE Content Hub 안내서 PDF]{type=Informative url="https://helpx.adobe.com/kr/content/dam/help/en/experience-manager/aem-assets/content-hub.pdf"}

[!DNL Content Hub]는 자산에 대한 귀중한 인사이트를 제공하여 마케팅 관련자들이 자주 직면하는 일반적인 문제인 마케팅 캠페인, 채널 및 다양한 지역에서 사용되는 자산 사용 통계를 해결합니다. 자산의 성과와 인기를 명확하게 이해함으로써 사용자 경험 향상에 필수적인 실행 가능한 인사이트를 제공합니다.

## 사전 요구 사항 {#prerequisites}

[Content Hub 사용자](deploy-content-hub.md#onboard-content-hub-users)는 이 문서에 언급된 작업을 수행할 수 있습니다.

## 업로드된 에셋에 대한 통계 보기{#view-statistics-for-uploaded-assets}

**[!UICONTROL 인사이트]** 탭으로 이동하여 업로드된 에셋 및 컬렉션의 통계를 볼 수 있습니다. 연간, 월별 및 일별 에셋 업로드 보기를 사용하여 에셋의 업로드 내역을 추적합니다.

![자산 통계 업로드](assets/assets-insights.jpg)

<!-- You can track the upload history of your assets over the past 30 days or gain a more comprehensive view with data spanning the last 12 months. This feature enables you to evaluate the upload count of assets.  -->

<!-- Go to the **[!UICONTROL [!DNL Insights]]** tab.

2. Select the desired time frame to view the statistics; you can opt for either last 30 days or last 12 months.

Data for the selected time frame is displayed, including the upload count for the specified duration. -->

## 상세 통계 분석 보기{#view-detailed-statistical-analysis}

Content Hub을 사용하면 파일 형식, 캠페인, 채널 및 지역에 따라 에셋 수의 통계를 볼 수 있습니다. 정보에 입각한 의사 결정 및 전략 계획을 용이하게 하는 자산 배포에 대한 중요한 통찰력을 얻을 수 있습니다.

표에는 여러 에셋 수 및 저장소 내의 해당 백분율을 포함하여 이에 대한 자세한 개요가 나와 있습니다. 열 크기를 조정하고 에셋 이름, 개수 및 백분율별로 에셋을 정렬할 수 있습니다.

파이 차트는 파일 형식별 에셋의 총 수를 시각적으로 나타내며 개별 에셋 수와 해당 백분율을 명확하게 보여 줍니다.

자산 유형 통계별 ![자산 개수](assets/insights-categorial-view.jpg)

다음을 볼 수도 있습니다.

* **일 및 월별 활성 사용자**: 선 그래프로 표시된 일별 또는 월별 활성 사용자 수입니다.
* **[!UICONTROL 캠페인별 Assets]**: 캠페인을 기반으로 한 에셋 수 및 해당 백분율.
* **[!UICONTROL 채널별 Assets]**: 사용된 채널을 기반으로 하는 에셋 수 및 해당 백분율.
* **[!UICONTROL 지역별 Assets]**: 에셋 사용 지역을 기반으로 하는 에셋 수 및 각각의 백분율.
