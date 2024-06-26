---
title: Cloud Service 콘텐츠 요청 이해
description: Adobe에서 컨텐츠 요청 라이선스를 구입한 경우 Adobe Experience Cloud as a Service가 측정하는 컨텐츠 요청 유형과 조직의 분석 보고 도구와의 차이에 대해 알아봅니다.
exl-id: 3666328a-79a7-4dd7-b952-38bb60f0967d
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: a1b0d37b2f2f4e58b491651cb8e6504a6909393e
workflow-type: tm+mt
source-wordcount: '1381'
ht-degree: 10%

---

# Cloud Service 컨텐츠 요청

## 소개 {#introduction}

콘텐츠 요청은 페이지 보기(예: 페이지 및 경험 조각)를 통해 HTML 형식으로 또는 API 호출을 통해 JSON 형식(Headless 방식으로)으로 콘텐츠 또는 데이터를 전달하기 위해 AEM Sites(AEM Sites용 Edge Delivery Services과 관련하여 포함) 또는 고객 제공 캐싱 시스템(예: 콘텐츠 전달 네트워크)으로 들어오는 요청입니다. 콘텐츠 요청은 페이지 보기 또는 5개의 API 호출로 계산되며, 콘텐츠 요청을 수신하기 위한 첫 번째 캐싱 시스템의 인그레스에서 측정됩니다. 특정 HTTP 요청은 콘텐츠 요청 계산을 위해 포함되거나 제외됩니다. 포함 및 제외된 HTTP 요청과 그 기술 정의에 대한 전체 목록은 설명서에서 확인할 수 있습니다.

## Cloud Service 콘텐츠 요청 이해 {#understanding-cloud-service-content-requests}

기본 제공 CDN을 사용하는 고객의 경우 Cloud Service 컨텐츠 요청은 서버측 데이터 수집을 통해 측정됩니다. 이 컬렉션은 CDN 로그 분석을 통해 활성화됩니다. 컨텐츠 요청은 AEM as a Cloud Service CDN에서 시작되는 로그 파일의 자동화된 분석을 통해 Adobe Experience Manager as a Cloud Service의 에지에서 서버측에서 자동으로 수집됩니다. 이 작업은 HTML을 반환하는 요청을 격리하여 수행됩니다 `(text/html)` 또는 JSON `(application/json)` 는 CDN의 콘텐츠이며, 아래에 설명된 여러 포함 및 제외 규칙을 기반으로 합니다. 콘텐츠 요청은 CDN 캐시에서 처리 중인 반환된 콘텐츠 또는 CDN(AEM dispatchers)의 소스로 돌아가는 콘텐츠와는 독립적으로 발생합니다.

자체 CDN을 사용하는 고객의 경우 클라이언트측 컬렉션은 상호 작용을 보다 정확하게 반영하여 을 통해 웹 사이트 참여에 대한 신뢰할 수 있는 측정을 보장합니다 [실시간 사용 모니터링](/help/sites-cloud/administering/real-use-monitoring-for-aem-as-a-cloud-service.md) 서비스. 이를 통해 고객은 페이지 트래픽 및 성능에 대한 고급 통찰력을 얻을 수 있습니다. 모든 고객에게 유익하지만 사용자 상호 작용의 대표적인 반영을 제공하여 클라이언트 측의 페이지 보기 수를 캡처하여 웹 사이트 참여에 대한 신뢰할 수 있는 측정을 보장합니다.

AEM as a Cloud Service을 기반으로 자체 CDN을 가져오는 고객의 경우 서버측 보고는 라이선스가 부여된 콘텐츠 요청과 비교하는 데 사용할 수 없는 숫자를 생성합니다. 포함 [실시간 사용 모니터링](/help/sites-cloud/administering/real-use-monitoring-for-aem-as-a-cloud-service.md), Adobe은 웹 사이트 참여에 대한 신뢰할 수 있는 측정을 반영할 수 있습니다.


### Cloud Service 컨텐츠 요청 분산 {#content-requests-variances}

콘텐츠 요청은 다음 표에 요약된 바와 같이 조직의 Analytics 보고 도구 내에 차이를 가질 수 있습니다. 일반적으로, *금지* 클라이언트측 계측을 통해 데이터를 수집하는 analytics 도구를 사용하여 특정 사이트에 대한 콘텐츠 요청 수를 보고합니다. 이는 종종 트리거되는 사용자 동의에 따라 결정되므로 트래픽의 상당 부분이 누락되기 때문입니다. Analytics 도구는 로그 파일에 서버측에서 데이터를 수집하거나, AEM as a Cloud Service을 기반으로 자체 CDN을 추가하는 고객을 위한 CDN 보고서를 더 나은 개수를 제공합니다. 페이지 보기 수 및 관련 성능에 대한 보고의 경우 [Adobe RUM 데이터 서비스](/help/sites-cloud/administering/real-use-monitoring-for-aem-as-a-cloud-service.md) 는 Adobe 권장 옵션입니다.

| 차이가 나는 이유 | 설명 |
|---|---|
| 최종 사용자 동의 | 클라이언트측 계기에 의존하는 Analytics 도구는 종종 트리거되는 사용자 동의에 따라 다릅니다. 이는 추적되지 않는 트래픽의 대부분을 나타낼 수 있습니다. 콘텐츠 요청을 직접 측정하려는 고객의 경우 데이터 서버측 또는 CDN 보고서를 수집하는 분석 도구에 의존하는 것이 좋습니다. |
| 태그 지정 | Adobe Experience Manager 콘텐츠 요청으로 추적되는 모든 페이지 또는 API 호출에 Analytics 추적 태그가 지정되지 않을 수 있습니다. |
| 태그 관리 규칙 | 태그 관리 규칙 설정으로 인해 페이지에 다양한 데이터 수집 구성이 발생할 수 있으며, 이로 인해 콘텐츠 요청 추적과 일부 불일치가 발생할 수 있습니다. |
| 봇 | AEM에서 사전 식별 및 제거하지 않은 알려지지 않은 봇으로 인해 추적 불일치가 발생할 수 있습니다. |
| 보고서 세트 | 동일한 AEM 인스턴스 및 도메인에 속한 페이지는 데이터를 서로 다른 Analytics 보고서 세트로 전송할 수 있습니다. |
| 서드파티 모니터링 및 보안 도구 | 모니터링 및 보안 검색 도구는 Analytics 보고서에서 추적되지 않는 AEM에 대한 콘텐츠 요청을 생성할 수 있습니다. |
| API 액세스 | 페이지 또는 Adobe Experience Manager API에 프로그래밍 방식으로 액세스하면 Analytics 보고서에서 추적되지 않는 AEM에 대한 컨텐츠 요청을 생성할 수 있습니다. |
| 프리페치 요청 | 프리페치 서비스를 사용하여 페이지를 미리 로드하여 속도를 높이면 콘텐츠 요청 트래픽이 크게 증가할 수 있습니다. |
| DDOS | Adobe은 DDOS 공격의 트래픽을 자동으로 감지하고 필터링하려고 시도하지만 가능한 모든 DDOS 공격을 감지한다는 보장은 없습니다. |
| 트래픽 차단 | 브라우저에서 추적기 차단을 사용하면 일부 요청이 추적되지 않도록 옵트아웃할 수 있습니다. |
| 방화벽 | 방화벽이 Analytics 추적을 차단할 수 있습니다. 이 시나리오는 회사 방화벽에서 더 자주 발생합니다. |

참조: [라이선스 대시보드](/help/implementing/cloud-manager/license-dashboard.md).

## 서버측 컬렉션 규칙 {#serverside-collection}

검색 인덱스나 서비스를 새로 고치기 위해 사이트를 정기적으로 방문하는 잘 알려진 서비스를 포함하여 잘 알려진 봇을 제외하는 규칙이 있습니다.

### 포함된 콘텐츠 요청 유형 {#included-content-requests}

| 요청 유형 | 콘텐츠 요청 | 설명 |
| --- | --- | --- |
| HTTP 코드 100-299 | 포함됨 | 이는 모든 콘텐츠 또는 일부 콘텐츠를 제공하는 일반 요청입니다. |
| 자동화를 위한 HTTP 라이브러리 | 포함됨 | 예:<br>· Amazon CloudFront<br>· Apache Http 클라이언트<br>· 비동기 Http 클라이언트<br>· Axios<br>· 아쥬레우스<br>· 컬<br>· GitHub 노드 가져오기<br>· 폭풍<br>· Go-http-client<br>· Headless Chrome<br>· Java™ 클라이언트<br>· 저지<br>· 노드 포함<br>· okhttp<br>· Python 요청<br>· Reactor Netty<br>· 위젯<br>· WinHttp |
| 모니터링 및 상태 확인 도구 | 포함됨 | 사이트의 특정 측면을 모니터링하기 위해 고객이 설정합니다. 가용성 또는 실제 사용자 성능 등을 예로 들 수 있습니다. 사용 `/system/probes/health` 끝점이며 사이트의 실제 HTML 페이지는 아닙니다.<br>예:<br>· Amazon-Route53-Health-Check-Service<br>· EyeMonIT_bot_version_0.1_[(https://www.eyemon.it/)](https://www.eyemon.it/)<br>· Investics-Site24x7<br>· Mozilla/5.0+(호환 가능, UptimeRobot/2.0; [https://uptimerobot.com/](https://uptimerobot.com/))<br>· ThousandEyes-Dragonfly-x1<br>· OmtrBot/1.0<br>· WebMon/2.0.0 |
| `<link rel="prefetch">` 요청 | 포함됨 | 다음 페이지 로드 속도를 높이기 위해 고객은 사용자가 링크를 클릭하기 전에 이미 캐시에 있도록 브라우저에서 페이지 세트를 로드하도록 할 수 있습니다. *정신: 이렇게 하면 트래픽이 크게 증가합니다*- 프리페치된 페이지 수에 따라 다릅니다. |
| Adobe Analytics 또는 Google Analytics 보고를 차단하는 트래픽 | 포함됨 | 사이트 방문자는 Google Analytics 또는 Adobe Analytics의 정확성에 영향을 주는 개인 정보 보호 소프트웨어(광고 차단기 등)를 설치하는 것이 더 일반적입니다. AEM as a Cloud Service은 클라이언트측이 아닌 Adobe 운영 인프라의 첫 번째 진입점에 대한 요청을 계산합니다. |

참조: [라이선스 대시보드](/help/implementing/cloud-manager/license-dashboard.md).

### 제외된 콘텐츠 요청 유형 {#excluded-content-request}

| 요청 유형 | 콘텐츠 요청 | 설명 |
| --- | --- | --- |
| HTTP 코드 500+ | 제외됨 | AEM as a Cloud Service 또는 고객 사용자 지정 코드에서 문제가 발생하면 방문자에게 오류가 반환되었습니다. |
| HTTP 코드 400-499 | 제외됨 | 콘텐츠가 없거나(404) 다른 콘텐츠 또는 요청 관련 문제가 있으면 방문자에게 오류가 반환됩니다. |
| HTTP 코드 300-399 | 제외됨 | 서버에서 변경된 사항이 있는지 확인하거나 요청을 다른 리소스로 리디렉션하는 좋은 요청입니다. 여기에는 콘텐츠 자체가 포함되어 있지 않으므로 청구할 수 없습니다. |
| /libs/*로 이동하는 요청 | 제외됨 | 청구할 수 없는 CSRF 토큰과 같은 AEM 내부 JSON 요청. |
| DDOS 공격의 트래픽 | 제외됨 | DDOS 보호. AEM은 일부 DDOS 공격을 자동으로 탐지하여 차단합니다. 감지된 경우 DDOS 공격은 청구할 수 없습니다. |
| AEM as a Cloud Service New Relic 모니터링 | 제외됨 | AEM as a Cloud Service 전역 모니터링. |
| 고객이 Cloud Service 프로그램을 모니터링할 수 있는 URL | 제외됨 | 외부 가용성을 모니터링하는 권장 URL입니다.<br><br>`/system/probes/health` |
| AEM as a Cloud Service Pod 준비 서비스 | 제외됨 |
| 요원: 스카이라인-서비스-웜업/1* |
| 잘 알려진 검색 엔진, 소셜 네트워크 및 HTTP 라이브러리(Fastly에서 태그 지정) | 제외됨 | 검색 인덱스 또는 서비스를 새로 고치기 위해 사이트를 정기적으로 방문하는 잘 알려진 서비스:<br><br>예:<br>· AddSearchBot<br>· ArefsBot<br>· Applebot<br>· Jeeves Corporate Spider에게 문의<br>· 빙보트<br>· BingView<br>· BLEXBot<br>· 기본 제공<br>· Bytespider<br>· CrawlerKengo<br>· Facebookexternalhit<br>· Google AdsBot<br>· Google AdsBot Mobile<br>· Googlebot<br>· Googlebot Mobile<br>· lmspider<br>· LucidWorks<br>· MJ12bot<br>· 핑돔<br>· Pinterest<br>· SemrushBot<br>· 사이트 개선<br>· StashBot<br>· StatusCake<br>· YandexBot |
| Commerce integration framework 호출 제외 | 제외됨 | Commerce integration framework에 전달되는 AEM에 대한 요청입니다(URL은 다음으로 시작). `/api/graphql`- 이중 계산을 방지하기 위해 Cloud Service에 대해 청구할 수 없습니다. |
| 제외 `manifest.json` | 제외됨 | 매니페스트는 API 호출이 아닙니다. 데스크톱이나 휴대폰에 웹 사이트를 설치하는 방법에 대한 정보를 제공하기 위해 여기에 있습니다. Adobe은 JSON 요청을에 계산해서는 안 됩니다. `/etc.clientlibs/*/manifest.json` |
| 제외 `favicon.ico` | 제외됨 | 반환된 콘텐츠는 HTML 또는 JSON이 아니어야 하지만 SAML 인증 흐름과 같은 일부 시나리오에서 favicons를 HTML으로 반환할 수 있으므로 계산에서 명시적으로 제외됨을 관찰하고 있습니다. |
