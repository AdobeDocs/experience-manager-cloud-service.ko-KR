---
title: AEM as a Cloud Service에 대한 운영 원격 측정
description: 클라이언트측 데이터 수집을 모니터링할 수 있는 자동화된 서비스인 운영 원격 분석에 대해 알아봅니다.
exl-id: 91fe9454-3dde-476a-843e-0e64f6f73aaf
feature: Administering
role: Admin
source-git-commit: 100a8cd1a27cd8f0677ed001def0b1e0e7b20ed3
workflow-type: tm+mt
source-wordcount: '1134'
ht-degree: 1%

---

# AEM as a Cloud Service용 운영 원격 분석 서비스 {#real-use-monitoring-service-for-aem-as-a-cloud-service}

>[!NOTE]
>
>클라이언트측 데이터 수집인 운영 원격 분석 서비스는 자동화된 서비스입니다. 고객 설정은 필요하지 않습니다.

>[!INFO]
>
>클라이언트측 모니터링은 AEM(Adobe Experience Manager) Cloud Service 버전 **2024.5.16461** 이상인 고객에게만 작동합니다.

## 개요 {#overview}

Operational Telemetry 서비스는 웹 사이트 또는 애플리케이션에서 클라이언트측 트래픽을 실시간으로 모니터링하는 성능 모니터링 기술입니다. 이 서비스는 사용자 자신보다 웹 사이트 참여를 모니터링하여 성능을 최적화하는 데 핵심적인 지표 및 데이터 수집에 중점을 둡니다. 운영 원격 분석을 사용하면 요청이 다시 브라우저로 제공될 때까지 URL의 시작부터 주요 성능 지표가 바로 추적됩니다.

## Operational Telemetry 서비스를 통해 혜택을 얻을 수 있는 사람은 누구입니까? {#who-can-benefit-from-operational-telemetry-service}

운영 원격 분석을 통해 고객과 Adobe은 최종 사용자가 AEM 사이트와 상호 작용하는 방식을 이해할 수 있습니다. 운영 원격 분석은 제한된 데이터 수집 및 샘플링을 통해 방문자의 개인 정보를 보존합니다. 모든 페이지 보기의 일부만 모니터링됩니다.

## 운영 원격 분석 서비스 데이터 샘플링 {#operational-telemetry-service-data-sampling}

기존 웹 분석 솔루션은 모든 단일 방문자에 대한 데이터를 수집하려고 합니다. AEM의 Operational Telemetry 서비스는 극히 일부 페이지 보기에서 정보만 캡처합니다. 서비스는 분석을 대체하는 것이 아니라 샘플링되고 익명화되어야 합니다. 기본적으로 페이지는 샘플링 비율이 1:100입니다. 사이트 운영자는 현재 샘플링 속도를 높이거나 낮출 수 없습니다. 총 트래픽을 정확하게 추정하기 위해 100개의 페이지 보기마다 데이터가 1에서 수집되므로 전체 트래픽에 대한 신뢰할 수 있는 근사치를 제공합니다.

데이터 수집 여부의 판단으로 페이지 보기 단위로 페이지 보기에서 이루어지며, 여러 페이지 간 상호 작용을 추적하는 것이 사실상 불가능해진다. 기본적으로 Operational Telemetry에는 방문자 또는 세션에 대한 개념이 없으며 페이지 보기 횟수만 있습니다.

## 어떤 데이터가 수집됩니까? {#what-data-is-being-collected}

Operational Telemetry 서비스는 데이터 수집을 최소화하도록 설계되었습니다. Operational Telemetry에서 수집한 전체 정보 집합은 다음과 같습니다.

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
* 방문자의 체감 품질을 설명하는 [핵심 웹 바이탈(CWV)](https://web.dev/articles/lcp) 성능 지표 [가장 큰 LCP(Contentable Paint)](https://web.dev/articles/lcp), [다음 페인트에 대한 상호 작용(INP)](https://web.dev/articles/inp) 및 [CLS(Cumulative Layout Shift)](https://web.dev/articles/cls).

## 고객을 위한 운영 원격 분석 작동 방식 {#how-operational-telemetry-works-for-a-customer}

운영 원격 분석에서는 클라이언트측 트래픽을 자동으로 모니터링합니다. 이 서비스는 기존 설정에 원활하게 통합되므로 Adobe 고객은 추가 단계를 수행하지 않아도 됩니다. 운영 원격 분석 서비스를 일반적으로 사용할 수 있게 되면 이 새로운 기능을 자동으로 활용할 수 있습니다. Operational Telemetry service는 현재 모니터링할 고객 대면 지표를 노출하지 않습니다. 당사는 이 기능을 최대한 빨리 제공하기 위해 노력하고 있습니다.

<!-- Alexandru: hiding temporarily, until we figure out where this needs to be linked to 

If you wish to leverage more insights with this new feature to optimize your digital experiences effortlessly, please see here (link to Row 99). -->

## Adobe에서 운영 원격 분석을 사용하는 방법 {#how-operational-telemetry-data-is-being-used}

운영 원격 분석 데이터는 다음 용도로 사용됩니다.

* 고객 사이트의 성능 병목 현상을 파악하고 해결하기 위한 방법
* AEM이 동일한 페이지에서 다른 스크립트(예: 분석, 타기팅 또는 외부 라이브러리)와 상호 작용하여 호환성을 높이는 방법을 이해합니다.
<!--
## Limitations and understanding variance in page views and performance metrics {#limitations-and-understanding-variance-in-page-views-and-performance-metrics}

Here are key considerations for customers to keep in mind when interpreting their Operational Telemetry data:

1. **Tracker blockers**

   * End-users employing tracker blockers or privacy extensions can impede Operational Telemetry data collection, as these tools restrict the tracking scripts' execution. This restriction may lead to underreported page views and user interactions, creating a discrepancy between actual site activity and the data captured by Operational Telemetry.

1. **Limitations in capturing headless API/JSON calls**

   * Operational Telemetry data service focuses on the client-side experience and doesn't capture the backend API or JSON calls made from a non-AEM headless app at this time. The exclusion of these calls from Operational Telemetry service data creates variances from the content requests measured by CDN Analytics.
-->

## FAQ {#faq}

<!-- REMOVED THIS FAQ AS PER EMAIL REQUEST FROM SHWETA DUA, SEPTEMBER 4, 2024 TO THE DL-AEM-DOCS GROUP 
1. **Can customers integrate the Operational Telemetry service scripts with third-party systems like Dynatrace?**

   Yes.
-->

1. **다음 페인트에 대한 상호 작용, 첫 번째 바이트에 대한 시간 및 첫 번째 만족도 페인트 지표가 수집되고 있습니까?**

   다음 페인트에 대한 상호 작용(INP) 및 첫 번째 바이트에 대한 시간(TTFB)이 수집됩니다.  지금은 첫 번째 컨텐트가 수집되지 않습니다.

1. **내 사이트에서 `/.rum` 경로가 차단되어 있습니다. 어떻게 수정해야 합니까?**

   작동 원격 분석 수집이 작동하려면 `/.rum` 경로가 필요합니다. Adobe의 AEM as a Cloud Service 앞에서 CDN을 사용하는 경우 `/.rum` 경로가 다른 AEM 콘텐츠와 동일한 AEM 원본으로 전달되는지 확인하십시오. 그리고 어떤 식으로든 조정되지 않았는지 확인하십시오. 또는 `rum.hlx.page`Cloud Manager의 환경 변수 [을(를) ](/help/implementing/cloud-manager/environment-variables.md#add-variables) 값으로 설정`AEM_OPTEL_EXTERNAL`하여 운영 원격 분석에 사용할 호스트를 `true`(으)로 변경할 수 있습니다. 나중에 동일한 도메인 요청으로 다시 변경하려면 해당 환경 변수를 다시 제거합니다.

1. **계약 목적으로 운영 원격 분석 수집이 콘텐츠 요청에 포함됩니까?**

   운영 원격 분석 라이브러리 및 운영 원격 분석 수집은 콘텐츠 요청으로 계산되지 않으며 보고된 페이지 보기 수 또는 API 호출 수를 증가시키지 않습니다. 또한 AEM as a Cloud Service에서 기본 제공 CDN을 사용하는 고객의 경우 [서버측 컬렉션](#serverside-collection)이 콘텐츠 요청의 기본입니다.

1. **작동 원격 분석을 사용하지 않도록 설정하려면 어떻게 해야 합니까?**

   Adobe은 운영 원격 분석 을 사용할 것을 권장합니다. 그 이유는 운영 원격 분석의 상당한 이점과 Adobe이 웹 사이트 성능을 향상시켜 디지털 경험을 최적화하는 데 도움이 될 것입니다. 이 서비스는 원활하도록 설계되었으며 웹 사이트의 성능에 영향을 주지 않습니다.

   옵트아웃은 웹 사이트의 트래픽 참여를 개선할 기회를 놓치는 것을 의미할 수 있습니다. 그러나 문제가 발생하면 [Cloud Manager에서 ](/help/implementing/cloud-manager/environment-variables.md#add-variables)(이)라는 환경 변수를 `AEM_OPTEL_DISABLED` 값으로 설정하여 작동 원격 분석을 사용하지 않도록 설정할 수 있습니다. `true` 나중에 운영 원격 분석을 다시 활성화하려면 해당 환경 변수를 다시 제거하십시오.

1. **Nonce로 콘텐츠 보안 정책을 사용할 수 있습니까?**

   운영 원격 분석 지원에는 임시 항목으로 CSP(콘텐츠 보안 정책)를 지원하는 실험 기능이 포함되어 있습니다. 이 기능은 [Cloud Manager에서 환경 변수 ](/help/implementing/cloud-manager/environment-variables.md#add-variables)을(를) 값 `AEM_OPTEL_NONCE`(으)로 설정하여 활성화할 수 있습니다. `true` 나중에 이 기능을 다시 사용하지 않도록 설정하려면 해당 환경 변수를 다시 제거하면 됩니다.

   이 기능에 문제가 발생하면 Adobe 지원 센터에 문의하십시오.

1. **특정 페이지에 대해서만 작동 원격 분석을 사용하도록 설정하려면 어떻게 해야 합니까?**

   기본적으로 저장소의 `/content` 폴더 아래에 있는 모든 페이지에 대해 작동 원격 분석이 사용됩니다. [Cloud Manager에서 환경 변수 설정](/help/implementing/cloud-manager/environment-variables.md#add-variables)(이름: `AEM_OPTEL_INCLUDED_PATHS`)을 저장소의 쉼표로 구분된 경로 목록으로 설정하면 해당 페이지에만 작동 원격 분석이 사용됩니다. 또한 `AEM_OPTEL_EXCLUDED_PATHS`을(를) 제외할 저장소의 경로 목록으로 설정할 수 있습니다. 이러한 두 가지 설정을 결합하면 요구 사항에 운영 원격 분석 포함을 조정할 수 있습니다.

