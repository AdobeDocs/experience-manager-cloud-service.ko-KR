---
title: AEM as a Cloud Service용 실제 사용 모니터링
description: RUM(Real Use Monitoring)을 사용하여 웹 사이트 또는 애플리케이션 의 디지털 사용자 경험 경험을 실시간으로 캡처하고 분석하는 방법을 알아봅니다.
exl-id: 91fe9454-3dde-476a-843e-0e64f6f73aaf
feature: Administering
role: Admin
source-git-commit: 9a8adf777008b7a601abc8760cee67ec3c1816c6
workflow-type: tm+mt
source-wordcount: '1301'
ht-degree: 0%

---

# Cloud Service형 AEM를 위한 실제 사용 모니터링 서비스 {#real-use-monitoring-service-for-aem-as-a-cloud-service}

>[!NOTE]
>
>데이터 클라이언트측 컬렉션인 Real Use Monitoring 서비스는 자동화된 서비스입니다. 고객 설정이 필요하지 않습니다.

>[!INFO]
>
>클라이언트 쪽 모니터링은 버전 **2024.5.16461** 이상을 사용하는 고객AEM Cloud Service 대해서만 작동합니다.

## 개요 {#overview}

RUM(Real Use Monitoring) 서비스는 웹 사이트 또는 애플리케이션 의 디지털 사용자 경험을 실시간으로 캡처하고 분석하는 성능 모니터링 기술입니다. 웹 애플리케이션의 실시간 성능에 대한 가시성을 제공하고 최종 사용자 경험에 대한 심층적인 인사이트 제공합니다. 이 서비스는 사용자 자체보다는 웹 사이트 참여를 모니터링하여 성능을 최적화하는 데 중점을 둡니다.

RUM을 사용하면 URL 시작부터 요청이 브라우저에 다시 제공될 때까지 주요 성능 지표를 바로 추적할 수 있습니다. 개발자가 최종 사용자가 쉽게 사용할 수 있도록 애플리케이션 기능을 향상시키는 데 도움이 됩니다.

>[!INFO]
>
>&quot;Real User Monitoring&quot;은 서비스의 진정한 본질을 더 잘 반영하기 위해 &quot;Real Use Monitoring&quot;으로 리브랜딩되었습니다.

## 실제 사용 모니터링 서비스의 혜택을 받을 수 있는 사람은 누구입니까? {#who-can-benefit-from-rum-service}

실제 사용 모니터링 서비스는 모든 고객에게 유용합니다. 사용자 상호 작용의 대표적인 반영을 제공하여 클라이언트측 페이지 조회수를 캡처하여 웹 사이트 참여 신뢰할 수 있는 측정 보장합니다.

모든 Adobe Systems 고객에게 이 서비스는 사용자 상호 작용에 대한 귀중한 통찰력을 제공합니다. 자체 CDN을 사용하는 고객은 이제 Adobe Systems가 데이터 수집을 직접 통합하므로 갱신 주기 동안 별도의 보고서가 필요하지 않으므로 간소화된 트래픽 보고의 이점을 누릴 수 있습니다.

## 실제 사용 모니터링 서비스의 작동 방식 이해 {#understand-how-the-rum-service-works}

Adobe Experience Manager(AEM)는 RUM(Real Use Monitoring)을 사용하여 고객과 Adobe Systems 방문자가 AEM 사이트와 상호 작용하는 방식을 이해할 수 있도록 지원합니다. 성능 문제를 진단하고 실험의 효과를 측정 하는 데 도움이됩니다. RUM은 샘플링을 통해 방문자의 개인 정보를 보호하며 모든 페이지 뷰의 작은 부분만 모니터링되며 개인 식별 정보(PII)는 수집되지 않습니다.

## 실제 사용 모니터링 서비스 및 개인 정보 보호 {#rum-service-and-privacy}

AEM의 실제 사용 모니터링 서비스는 방문자의 개인 정보를 보호하고 데이터 수집 작업을 최소화하도록 설계되었습니다. 방문자란 귀하가 방문 중이거나 Adobe Systems 에서 사용할 수 있도록 한 사이트가 어떠한 개인 정보도 수집하지 않는다는 것을 의미합니다.

사이트 운영자는 이 기능을 통해 모니터링을 활성화하기 위해 추가 옵트인(opt-in)이 필요하지 않습니다. 최종 사용자가 RUM을 활성화하기 위해 수락할 수 있는 추가 팝업 또는 동의 양식은 없습니다.

## 실제 사용 모니터링 서비스 데이터 샘플링 {#rum-service-data-sampling}

기존의 웹 분석 솔루션은 모든 단일 방문자에 대한 데이터를 수집하려고 합니다. AEM의 RUM 서비스는 페이지 보기의 작은 부분에서만 정보를 캡처합니다. 이 서비스는 분석 대신 샘플링 및 익명화됩니다. 기본적으로 페이지의 샘플링 비율은 1:100입니다. 사이트 운영자는 현재 샘플링 속도를 높이거나 낮출 수 없습니다. 총 트래픽을 정확하게 추정하기 위해 100개의 페이지 뷰마다 1에서 데이터가 수집되어 전체 트래픽에 대한 신뢰할 수 있는 근사치를 제공합니다.

데이터 수집 여부에 대한 결정은 페이지 조회수를 기준으로 페이지 조회수로 이루어지며 여러 페이지 간의 상호 작용을 추적하는 것이 사실상 불가능합니다. 기본적으로 RUM에는 방문자 또는 세션 개념이 없으며 페이지 뷰 수만 있습니다.

## 수집되는 데이터 {#what-data-is-being-collected}

실제 사용 모니터링 서비스는 개인 식별 정보의 컬렉션 수집을 방지하도록 설계되었습니다. RUM에서 수집하는 전체 정보는 다음과 같습니다.

* 방문 중인 사이트의 호스트 이름입니다. 예: `experienceleague.adobe.com`
* 페이지 표시에 사용되는 광범위한 사용자 에이전트 유형 및 운영 체제(예: `desktop:windows` 또는 `mobile:ios`
* 다음과 같은 데이터 수집 시간: `2021-06-26 06:00:02.596000 UTC (in order to preserve privacy, we round all minutes to the previous hour, so that only seconds and milliseconds are tracked)`
* 인스턴스에 대해 방문 중인 페이지의 URL: `https://experienceleague.adobe.com/docs`
* 레퍼러 URL(사용자가 링크 뒤에 오는 경우 현재 페이지에 연결된 페이지의 URL)
* 다음과 유사한 포맷으로 임의로 생성된 페이지 조회수 ID: `2Ac6`
* 가중치 또는 샘플링 속도의 역수(예: `100`)입니다. 이는 100개의 페이지 보기 중 하나만 기록됨을 의미합니다
* 페이지 로드 시퀀스에 있는 특정 이벤트의 체크포인트 또는 이름입니다. 또는 방문자로 상호 작용
* 사용자 사용자가 위에서 언급한 체크포인트 항목과 상호 작용하는 DOM 요소의 소스 또는 식별자입니다. 인스턴스의 경우 이미지일 수 있습니다
* 사용자가 위에서 언급한 체크포인트에 대해 상호 작용하는 외부 페이지 또는 리소스에 대한 타겟 또는 링크입니다. 예를 들어`https://blog.adobe.com/jp/publish/2022/06/29/media_162fb947c7219d0537cce36adf22315d64fb86e94.png`
* 방문자의 경험 품질을 설명하는 LCP(Largest Contentful Paint), FID(First Input Delay), CLS(Cumulative 레이아웃 Shift) 및 TTFB(Time To First Byte)를 포함한 CWV(Core Web Vitals) 성능 지표입니다.

## Real Use Monitoring이 고객에게 제공되는 방식 {#how-rum-works-for-a-customer}

Real Use Monitoring은 클라이언트측 트래픽 자동으로 모니터링하여 귀중한 통찰력을 제공합니다. Adobe Systems 고객은 이 서비스가 기존 설정에 원활하게 통합되므로 추가 단계를 수행할 필요가 없습니다. GA(일반 공급) 롤아웃 기능을 사용하면 이 새로운 기능의 이점을 자동으로 활용할 수 있습니다.

<!-- Alexandru: hiding temporarily, until we figure out where this needs to be linked to 

If you wish to leverage more insights with this new feature to optimize your digital experiences effortlessly, please see here (link to Row 99). -->

## 실제 사용 모니터링 서비스 데이터 사용 방법 {#how-rum-service-data-is-being-used}

RUM 데이터는 다음과 같은 목적에 유용합니다.

* 고객 사이트의 성능 병목 현상을 식별하고 해결하려면
* 페이지 보기를 포함하는 자동화된 트래픽 조회를 능률화하기 위해
* AEM이 동일한 페이지에서 다른 스크립트(예: 분석, 타겟팅 또는 외부 라이브러리)와 상호 작용하여 호환성을 높이는 방법을 이해합니다.

## 제한 사항 및 페이지 보기 및 성능 지표의 분산 이해 {#limitations-and-understanding-variance-in-page-views-and-performance-metrics}

RUM 데이터를 분석할 때 페이지 보기 및 기타 성능 지표에 차이가 있을 수 있습니다. 이러한 차이는 실시간 클라이언트측 모니터링에 내재된 몇 가지 요인에 기인할 수 있습니다. 고객이 RUM 데이터를 해석할 때 염두에 두어야 할 주요 고려 사항은 다음과 같습니다.

1. **트래커 차단기**

   * 추적기 차단기 또는 개인 정보 보호 확장 프로그램을 사용하는 최종 사용자는 이러한 도구가 추적 스크립트의 실행을 제한하기 때문에 RUM 데이터 수집 작업을 방해할 수 있습니다. 이러한 제한은 과소 보고된 페이지 보기 및 사용자 상호작용으로 리드 실제 사이트 활동과 RUM에서 캡처한 데이터 간에 불일치를 일으킬 수 있습니다.

1. **헤드리스 API/JSON 호출 캡처의 제한 사항**

   * RUM 데이터 서비스는 클라이언트측 경험에 중점을 두며 현재 AEM가 아닌 헤드리스 앱에서 수행된 백엔드 API 또는 JSON 호출을 캡처하지 않습니다. RUM 서비스 데이터에서 이러한 호출을 제외하면 CDN Analytics로 측정된 컨텐츠 요청에서 차이가 발생합니다.

## FAQ {#faq}


1. **고객이 RUM 서비스 스크립트를 좋아요 Dynatrace와 같은 서드파티 시스템과 통합할 수 있습니까?**

   예.

1. **&quot;다음 페인트까지의 상호 작용&quot;, &quot;첫 번째 바이트까지의 시간&quot; 및 &quot;첫 번째 콘텐츠가 포함된 페인트&quot; 웹 바이탈 메트릭이 수집되고 있습니까?**

   INP(Interaction to Next Paint) 및 TTFB(Time To First Byte)가 수집됩니다.  이때 첫 번째 콘텐츠가 포함된 페인트는 수집되지 않습니다.

1. **내 사이트에서 경로가 `/.rum` 차단되었습니다. 어떻게 수정해야 합니까?**

   RUM 컬렉션가 작동하려면 경로가 `/.rum` 필요합니다. Adobe Systems에서 Cloud Service로 AEM의 일부로 제공하는 항목 앞에 CDN이 있는 경우 경로가 `/.rum` AEM 컨텐츠의 나머지 부분과 동일한 AEM 원본으로 전달되는지 확인합니다. 그리고 어떤 식으로든 조정되지 않았는지 확인하십시오.

1. **RUM 컬렉션은 계약 목적상 컨텐츠 요청에 포함됩니까?**

   RUM 라이브러리 및 RUM 컬렉션은 컨텐츠 요청으로 계산되지 않으며 보고된 페이지 보기 또는 API 호출 수를 늘리지 않습니다. 또한 AEM를 Cloud Service [로 사용하여 기본 CDN을 사용하는 고객의 경우 컨텐츠 요청의 기본이 서버측 컬렉션](#serverside-collection) .

1. **옵트아웃하려면 어떻게 해야 하나요?**

   Adobe Systems RUM(Real Use Monitoring)의 상당한 이점과 디지털 경험을 최적화할 수 있기 때문에 RUM(Real Use Monitoring)을 사용할 것을 권장합니다. 웹 사이트 성능을 개선하는 데 도움이 될 수 있는 귀중한 통찰력을 제공할 수 있습니다. 이 서비스는 매끄럽게 설계되었으며 웹 사이트의 성능에 영향을 미치지 않습니다.

   옵트아웃은 이러한 인사이트를 놓치는 것을 의미합니다. 그러나 문제가 발생하면 Adobe Systems 지원 센터에 문의하십시오.
