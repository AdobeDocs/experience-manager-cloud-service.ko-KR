---
title: AEM as a Cloud Service용 실제 사용 모니터링
description: 클라이언트측 데이터 수집을 모니터링할 수 있는 자동화된 서비스인 RUM(Real Use Monitoring)에 대해 알아봅니다.
exl-id: 91fe9454-3dde-476a-843e-0e64f6f73aaf
feature: Administering
role: Admin
source-git-commit: ed52bac52618e23b9bcbe7c6767501c6711aff00
workflow-type: tm+mt
source-wordcount: '1012'
ht-degree: 1%

---

# AEM as a Cloud Service에 대한 실시간 모니터링 서비스 사용 {#real-use-monitoring-service-for-aem-as-a-cloud-service}

>[!NOTE]
>
>클라이언트측 데이터 수집인 Real Use Monitoring 서비스는 자동화된 서비스입니다. 고객 설정은 필요하지 않습니다.

>[!INFO]
>
>클라이언트측 모니터링은 AEM(Adobe Experience Manager) Cloud Service 버전이 **2024.5.16461** 이상인 고객에게만 작동합니다.

## 개요 {#overview}

RUM(Real Use Monitoring) 서비스는 웹 사이트 또는 애플리케이션에서 클라이언트측 트래픽을 실시간으로 모니터링하는 성능 모니터링 기술입니다. 이 서비스는 사용자 자신보다 웹 사이트 참여를 모니터링하여 성능을 최적화하는 데 핵심적인 지표 및 데이터 수집에 중점을 둡니다. RUM을 사용하면 요청이 브라우저에 다시 제공될 때까지 URL을 시작하는 즉시 주요 성능 지표가 추적됩니다.

## Real Use Monitoring Service를 통해 혜택을 얻을 수 있는 사람은 누구입니까? {#who-can-benefit-from-rum-service}

AEM은 고객 및 Adobe이 최종 사용자가 AEM 사이트와 상호 작용하는 방법을 이해할 수 있도록 지원하는 Real Use Monitoring을 개발했습니다. Real Use Monitoring은 성능 문제를 진단하고 실험의 효과를 측정합니다. 실제 사용 모니터링은 샘플링을 통해 방문자의 개인 정보를 보존하며 - 모든 페이지 보기의 일부만 모니터링되며 - PII(개인 식별 정보)는 수집되지 않습니다.

## 모니터링 서비스 및 개인 정보 보호 실제 사용 {#rum-service-and-privacy}

AEM의 Real Use Monitoring 서비스는 방문자 개인 정보를 유지하고 데이터 수집을 최소화합니다. 방문자는 방문 중이거나 Adobe 가능한 사이트가 개인 정보를 수집하지 않음을 의미합니다.

사이트 운영자는 이 기능을 통해 모니터링을 활성화하는 데 추가 옵트인이 필요하지 않습니다. 최종 사용자가 RUM 활성화를 위해 수락할 추가 팝업 또는 동의 양식이 없습니다.

## Real Use 모니터링 서비스 데이터 샘플링 {#rum-service-data-sampling}

기존 웹 분석 솔루션은 모든 단일 방문자에 대한 데이터를 수집하려고 합니다. AEM의 RUM(Real Use Monitoring) 서비스는 극히 일부 페이지 보기의 정보만 캡처합니다. 서비스는 분석을 대체하는 것이 아니라 샘플링되고 익명화되어야 합니다. 기본적으로 페이지는 1:100 샘플링 비율을 가집니다. 사이트 운영자는 현재 샘플링 속도를 높이거나 낮출 수 없습니다. 총 트래픽을 정확하게 추정하기 위해 100개의 페이지 보기마다 데이터가 1에서 수집되므로 전체 트래픽에 대한 신뢰할 수 있는 근사치를 제공합니다.

데이터 수집 여부의 판단으로 페이지 보기 단위로 페이지 보기에서 이루어지며, 여러 페이지 간 상호 작용을 추적하는 것이 사실상 불가능해진다. 기본적으로 RUM에는 방문자 또는 세션에 대한 개념이 없으며 페이지 보기에만 해당됩니다.

## 어떤 데이터가 수집됩니까? {#what-data-is-being-collected}

Real Use Monitoring 서비스는 개인 식별 정보의 수집을 방지하기 위해 설계되었습니다. RUM에서 수집한 전체 정보 집합은 아래에 나와 있습니다.

* 방문 중인 사이트의 호스트 이름(예: `experienceleague.adobe.com`)
* 페이지를 표시하는 데 사용되는 광범위한 사용자 에이전트 유형 및 운영 체제(예: `desktop:windows` 또는 `mobile:ios`)
* 데이터 수집 시간(예: `2021-06-26 06:00:02.596000 UTC (in order to preserve privacy, we round all minutes to the previous hour, so that only seconds and milliseconds are tracked)`)
* 방문 중인 페이지의 URL(예: `https://experienceleague.adobe.com/docs`)
* 레퍼러 URL(사용자가 링크를 따라간 경우, 현재 페이지에 연결된 페이지의 URL)
* `2Ac6`과(와) 유사한 형식으로 임의로 생성된 페이지 보기의 ID
* 샘플링 속도의 가중치 또는 역입니다(예: `100`). 즉, 100개 페이지 중 하나만 기록됩니다
* 페이지를 로드하는 순서에 있는 특정 이벤트의 체크포인트 또는 이름입니다. 또는 방문자로서 상호 작용
* 위에서 언급한 체크포인트에 대해 사용자가 상호 작용하는 DOM 요소의 소스 또는 식별자입니다. 예를 들어 이미지일 수 있습니다
* 위에서 언급한 체크포인트에 대해 사용자가 상호 작용하는 대상 또는 외부 페이지 또는 리소스에 대한 링크입니다. 예를 들어`https://blog.adobe.com/jp/publish/2022/06/29/media_162fb947c7219d0537cce36adf22315d64fb86e94.png`
* 방문자의 경험 품질을 설명하는 가장 큰 LCP(Contentable Paint), FID(First Input Delay), CLS(Cumulative Layout Shift) 및 TTFB(Time To First Byte)를 포함하는 CWV(Core Web Vitals) 성능 지표입니다.

## 고객의 실제 사용 모니터링 작동 방식 {#how-rum-works-for-a-customer}

Real Use Monitoring은 클라이언트측 트래픽을 자동으로 모니터링합니다. 이 서비스는 기존 설정에 완벽하게 통합되므로 Adobe 고객은 추가 단계를 수행하지 않아도 됩니다. RUM(Real Use Monitoring)이 GA(General Availability) 인 경우 이 새로운 기능을 자동으로 활용할 수 있습니다. Real Use Monitoring 서비스는 시각화 도구를 통해 오늘날 어떤 지표도 노출하지 않습니다. 당사는 이 기능을 최대한 빨리 제공하기 위해 노력하고 있습니다.

<!-- Alexandru: hiding temporarily, until we figure out where this needs to be linked to 

If you wish to leverage more insights with this new feature to optimize your digital experiences effortlessly, please see here (link to Row 99). -->

## Adobe에서 실시간 사용 모니터링을 사용하는 방법 {#how-rum-data-is-being-used}

실제 사용 모니터링 데이터는 다음 용도로 사용됩니다.

* 고객 사이트의 성능 병목 현상을 파악하고 해결하기 위한 방법
* AEM이 동일한 페이지에서 다른 스크립트(예: 분석, 타기팅 또는 외부 라이브러리)와 상호 작용하여 호환성을 높이는 방법을 이해합니다.
<!--
## Limitations and understanding variance in page views and performance metrics {#limitations-and-understanding-variance-in-page-views-and-performance-metrics}

Here are key considerations for customers to keep in mind when interpreting their RUM data:

1. **Tracker blockers**

   * End-users employing tracker blockers or privacy extensions can impede RUM data collection, as these tools restrict the tracking scripts' execution. This restriction may lead to underreported page views and user interactions, creating a discrepancy between actual site activity and the data captured by RUM.

1. **Limitations in capturing headless API/JSON calls**

   * RUM data service focuses on the client-side experience and doesn't capture the backend API or JSON calls made from a non-AEM headless app at this time. The exclusion of these calls from RUM service data creates variances from the content requests measured by CDN Analytics.
-->

## FAQ {#faq}

<!-- REMOVED THIS FAQ AS PER EMAIL REQUEST FROM SHWETA DUA, SEPTEMBER 4, 2024 TO THE DL-AEM-DOCS GROUP 
1. **Can customers integrate the RUM service scripts with third-party systems like Dynatrace?**

   Yes.
-->

1. **다음 페인트에 대한 상호 작용, 첫 번째 바이트에 대한 시간 및 첫 번째 만족도 페인트 지표가 수집되고 있습니까?**

   다음 페인트에 대한 상호 작용(INP) 및 첫 번째 바이트에 대한 시간(TTFB)이 수집됩니다.  지금은 첫 번째 컨텐트가 수집되지 않습니다.

1. **내 사이트에서 `/.rum` 경로가 차단되어 있습니다. 어떻게 수정해야 합니까?**

   RUM 컬렉션을 사용하려면 `/.rum` 경로가 필요합니다. Adobe의 AEM as a Cloud Service 앞에서 CDN을 사용하는 경우 `/.rum` 경로가 다른 AEM 콘텐츠와 동일한 AEM 원본으로 전달되는지 확인하십시오. 그리고 어떤 식으로든 조정되지 않았는지 확인하십시오.

1. **RUM 수집은 계약 목적으로 콘텐츠 요청에 포함됩니까?**

   RUM 라이브러리 및 RUM 컬렉션은 콘텐츠 요청으로 계산되지 않고 보고된 페이지 보기 수 또는 API 호출 수를 증가시키지 않습니다. 또한 AEM as a Cloud Service에서 기본 제공 CDN을 사용하는 고객의 경우 [서버측 컬렉션](#serverside-collection)이 콘텐츠 요청의 기본입니다.

1. **어떻게 옵트아웃할 수 있습니까?**

   Adobe은 상당한 이점으로 인해 RUM(Real Use Monitoring) 사용을 권장하며 Adobe이 웹 사이트 성능을 개선하여 디지털 경험을 최적화하는 데 도움이 될 수 있도록 할 것입니다. 이 서비스는 원활하도록 설계되었으며 웹 사이트의 성능에 영향을 주지 않습니다.

   옵트아웃은 웹 사이트의 트래픽 참여를 개선할 기회를 놓치는 것을 의미할 수 있습니다. 그러나 문제가 발생하면 Adobe 지원 센터에 문의하십시오.
