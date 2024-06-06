---
title: AEM에 대한 실시간 사용 모니터링 as a Cloud Service
description: RUM(Real Use Monitoring)을 사용하여 웹 사이트 또는 애플리케이션의 디지털 사용자 경험을 실시간으로 캡처하고 분석하는 방법에 대해 알아봅니다.
source-git-commit: a15f973c21044e16751401bd0ffb256a4d0fb17d
workflow-type: tm+mt
source-wordcount: '1409'
ht-degree: 0%

---


>[!NOTE]
>다음을 발표하게 되어 기쁩니다. [GA 롤아웃](/help/release-notes/release-notes-cloud/release-notes-current.md#real-use-monitoring) Real Use Monitoring 서비스의 경우 클라이언트측 데이터 수집입니다. 자동화된 서비스이며 고객 설정이 필요하지 않습니다.

# AEM에 대한 실시간 모니터링 서비스 as a Cloud Service 사용 {#real-use-monitoring-service-for-aem-as-a-cloud-service}

>[!INFO]
>
>클라이언트측 모니터링은 AEM Cloud Service 버전이 있는 고객에게만 작동합니다 **2024.5.16461** 이상.

## 개요 {#overview}

RUM(Real Use Monitoring) 서비스는 웹 사이트 또는 애플리케이션의 디지털 사용자 경험을 실시간으로 캡처하고 분석하는 성능 모니터링 기술입니다. 웹 애플리케이션의 실시간 성능에 대한 가시성을 제공하고 최종 사용자 경험에 대한 보다 심층적인 통찰력을 제공합니다. &#39;실사용 모니터링&#39;이 &#39;실사용 모니터링&#39;으로 새롭게 브랜딩된 것은 이용자 자신보다 웹사이트 참여를 모니터링해 성능을 최적화하는 데 중점을 두는 서비스의 진정한 본질을 더 잘 반영한다는 점이다.

RUM을 사용하면 URL을 시작한 후 요청이 다시 브라우저로 제공될 때까지 주요 성능 지표를 바로 추적하므로, 개발자는 이 모든 작업을 통해 최종 사용자가 쉽게 사용할 수 있도록 애플리케이션을 향상시킬 수 있습니다.

## 누가 실시간 모니터링 서비스를 활용할 수 있습니까? {#who-can-benefit-from-rum-service}

Real Use Monitoring 서비스는 모든 고객에게 유용합니다. 이는 사용자 상호 작용의 대표적인 반영을 제공하여 클라이언트측 페이지 보기 수를 캡처하여 웹 사이트 참여에 대한 신뢰할 수 있는 측정을 보장합니다.

모든 Adobe 고객을 위해 이 서비스는 사용자 상호 작용에 대한 중요한 통찰력을 제공합니다. 자체 CDN을 사용하는 고객은 트래픽 보고의 간소화를 활용할 수 있습니다. 이제 Adobe이 데이터 수집을 직접 통합하므로 갱신 주기 동안 별도의 보고서가 필요하지 않습니다.

Adobe의 Early Adopter RUM Explorer 시각화 도구를 사용하여 웹 사이트 참여에 대한 유용한 통찰력을 얻고 웹 사이트의 잠재력을 최대한 활용하시겠습니까? 이 도구는 클릭 수에 대한 지표, CWV(Core Web Vitals), 전환 및 고객 여정 맵을 포함하여 페이지 성능에 대한 통찰력을 제공할 수 있습니다. 이러한 강력한 통찰력을 사용하여 디지털 경험을 세밀하게 조정하여 사용자의 요구 사항을 보다 효과적으로 충족할 수 있습니다. 자세히 알아보고 액세스 권한을 얻으려면 다음 주소로 이메일을 보내주십시오. `rum-explorer@adobe.com`.

## Real Use Monitoring Service 작동 방식 이해 {#understand-how-the-rum-service-works}

Adobe Experience Manager은 RUM(Real Use Monitoring)을 사용하여 고객 및 Adobe이 Adobe Experience Manager 사이트와 상호 작용하는 방법을 이해하고, 성능 문제를 진단하며, 실험의 효과를 측정할 수 있도록 합니다. RUM은 샘플링을 통해 방문자의 개인 정보를 보존하며 - 모든 페이지 보기의 일부만 모니터링되며 - PII(개인 식별 정보)는 수집되지 않습니다.

## 모니터링 서비스 및 개인 정보 보호 실제 사용 {#rum-service-and-privacy}

Adobe Experience Manager의 Real Use Monitoring 서비스는 방문자 개인 정보를 보존하고 데이터 수집을 최소화하도록 설계되었습니다. 이는 방문자인 경우 방문 중인 사이트에서 개인 정보가 수집되지 않거나 Adobe이 사용할 수 없음을 의미합니다.

사이트 운영자는 이 기능을 통해 모니터링을 활성화하는 데 추가 옵트인이 필요하지 않습니다. 최종 사용자가 RUM 활성화를 위해 수락할 추가 팝업 또는 동의 양식이 없습니다.

## 실시간 사용 모니터링 서비스 데이터 샘플링 {#rum-service-data-sampling}

기존 웹 분석 솔루션은 모든 단일 방문자에 대한 데이터를 수집하려고 합니다. Adobe Experience Manager의 RUM 서비스는 극히 일부 페이지 보기에서 정보만 캡처합니다. 서비스는 분석을 대체하는 것이 아니라 샘플링되고 익명화되어야 합니다. 기본적으로 페이지는 1:100 샘플링 비율을 가집니다. 사이트 운영자는 현재 샘플링 속도를 높이거나 낮출 수 없습니다. 총 트래픽을 정확하게 추정하기 위해 100개의 페이지 보기마다 데이터가 1에서 수집되므로 전체 트래픽에 대한 신뢰할 수 있는 근사치를 제공합니다.

데이터 수집 여부는 페이지 보기 단위로 페이지 보기에서 결정되므로 여러 페이지 간 상호 작용을 추적하는 것이 사실상 불가능해진다. 기본적으로 RUM에는 방문자 또는 세션에 대한 개념이 없으며 페이지 보기에만 해당됩니다.

## 수집 중인 데이터 {#what-data-is-being-collected}

Real Use Monitoring 서비스는 개인 식별 정보의 수집을 방지하기 위해 설계되었습니다. RUM에서 수집할 수 있는 전체 정보 세트는 다음과 같습니다.

* 방문 중인 사이트의 호스트 이름(예: ) `experienceleague.adobe.com`
* 페이지를 표시하는 데 사용되는 광범위한 사용자 에이전트 유형 및 운영 체제(예: ): `desktop:windows` 또는 `mobile:ios`
* 다음과 같은 데이터 수집 시간: `2021-06-26 06:00:02.596000 UTC (in order to preserve privacy, we round all minutes to the previous hour, so that only seconds and milliseconds are tracked)`
* 방문 중인 페이지의 URL(예: ): `https://experienceleague.adobe.com/docs`
* 레퍼러 URL(사용자가 링크를 따라간 경우, 현재 페이지에 연결된 페이지의 URL)
* 다음과 유사한 형식으로 임의로 생성된 페이지 보기의 ID입니다. `2Ac6`
* 샘플링 속도의 가중치 또는 역입니다. 예: `100`. 즉, 100개 중 한 개의 페이지 보기만 기록됩니다
* 체크포인트 또는 페이지를 로드하거나 방문자로서 상호 작용하는 순서에 따른 특정 이벤트의 이름
* 위에서 언급한 체크포인트에 대해 사용자가 상호 작용하는 DOM 요소의 소스 또는 식별자입니다. 예를 들어 이미지일 수 있습니다
* 위에서 언급한 체크포인트에 대해 사용자가 상호 작용하는 대상 또는 외부 페이지 또는 리소스에 대한 링크입니다. 예를 들어`https://blog.adobe.com/jp/publish/2022/06/29/media_162fb947c7219d0537cce36adf22315d64fb86e94.png`
* 방문자의 경험 품질을 설명하는 가장 큰 LCP(Contentable Paint), FID(First Input Delay), CLS(Cumulative Layout Shift) 및 TTFB(Time To First Byte)를 포함하는 CWV(Core Web Vitals) 성능 지표입니다.

## 고객의 실제 사용 모니터링 작동 방식 {#how-rum-works-for-a-customer}

Real Use Monitoring은 클라이언트측 트래픽을 자동으로 모니터링하여 중요한 통찰력을 제공합니다. 이 서비스는 기존 설정에 완벽하게 통합되므로 Adobe 고객은 추가 단계를 수행하지 않아도 됩니다. GA(General Availability) 롤아웃을 사용하면 이 새로운 기능을 자동으로 활용할 수 있습니다.

<!-- Alexandru: hiding temporarily, until we figure out where this needs to be linked to 

If you wish to leverage more insights with this new feature to optimize your digital experiences effortlessly, please see here (link to Row 99). -->

## 실제 사용 모니터링 서비스 데이터가 사용되는 방식 {#how-rum-service-data-is-being-used}

RUM 데이터는 다음 목적에 유용합니다.

* 고객 사이트의 성능 병목 현상을 파악하고 해결하기 위한 방법
* 페이지 보기 수를 포함하는 자동화된 트래픽 조회를 간소화할 수 있습니다.
* Adobe Experience Manager이 호환성을 높이기 위해 동일한 페이지에서 다른 스크립트(예: 분석, 타기팅 또는 외부 라이브러리)와 상호 작용하는 방법을 이해합니다.

## 페이지 보기 수 및 성능 지표의 제한 사항 및 차이 이해 {#limitations-and-understanding-variance-in-page-views-and-performance-metrics}

RUM 데이터를 분석할 때 페이지 보기 수 및 기타 성능 지표에 차이가 있을 수 있습니다. 이러한 분산은 실시간, 클라이언트측 모니터링에 내재된 여러 가지 요인에 기인할 수 있습니다. 고객이 RUM 데이터를 해석할 때 유의해야 할 주요 고려 사항은 다음과 같습니다.

1. **추적기 차단기**

   * 추적기 차단기 또는 개인 정보 보호 확장을 사용하는 최종 사용자는 이러한 도구가 추적 스크립트의 실행을 제한하므로 RUM 데이터 수집을 방해할 수 있습니다. 이 제한 사항으로 인해 페이지 보기 수와 사용자 상호 작용이 제대로 보고되지 않아 실제 사이트 활동과 RUM으로 캡처된 데이터 간에 불일치가 발생할 수 있습니다.

1. **Headless API/JSON 호출 캡처의 제한 사항**

   * RUM 데이터 서비스는 클라이언트측 경험에 중점을 두며, 현재 비AEM Headless 앱에서 생성된 백엔드 API 또는 JSON 호출을 캡처하지 않습니다. RUM 서비스 데이터에서 이러한 호출을 제외하면 CDN Analytics에서 측정한 콘텐츠 요청에서 차이가 발생합니다.

## FAQ {#faq}


1. **고객이 RUM 서비스 스크립트를 Dynatrace과 같은 서드파티 시스템과 통합할 수 있습니까?**

   예.

1. **다음 페인트에 대한 상호 작용&quot;, &quot;첫 번째 바이트에 대한 시간&quot; 및 &quot;첫 번째 만족도 페인트&quot; 웹 바이탈 지표가 수집됩니까?**

   다음 페인트에 대한 상호 작용(INP) 및 첫 번째 바이트에 대한 시간(TTFB)이 수집됩니다.  지금은 첫 번째 컨텐트가 수집되지 않습니다.

1. **다음 `/.rum` 내 사이트에서 경로가 차단되었습니다. 어떻게 수정해야 합니까?**

   다음 `/.rum` rum 컬렉션이 작동하려면 경로가 필요합니다.  AEMas a Cloud Service 의 일부로 Adobe이 제공하는 항목 앞에 CDN이 있는 경우 `/.rum` 경로는 AEM 콘텐츠의 나머지 부분과 동일한 AEM 원점으로 전달됩니다.

1. **RUM 수집은 계약 목적의 콘텐츠 요청에 포함됩니까?**

   RUM 라이브러리 또는 RUM 컬렉션은 콘텐츠 요청으로 계산되지 않으며, 보고된 페이지 보기 수 또는 API 호출 수를 증가시키지 않습니다. 또한 AEM as a Cloud Service으로 기본 제공 CDN을 사용하는 고객의 경우 [서버측 컬렉션](#serverside-collection) 는 콘텐츠 요청의 기초입니다.

1. **어떻게 옵트아웃할 수 있습니까?**

상당한 이점과 디지털 경험을 최적화할 수 있도록 해 주는 RUM(Real Use Monitoring)을 사용하는 것이 좋습니다. 웹 사이트 성능을 개선하는 데 도움이 되는 유용한 통찰력을 제공할 수 있습니다. 이 서비스는 매끄럽도록 설계되었으며 웹 사이트 성능에 영향을 주지 않습니다.

옵트아웃은 이러한 통찰력을 놓친다는 것을 의미합니다. 그러나 문제가 발생하면 Adobe 지원 센터에 문의하십시오.
