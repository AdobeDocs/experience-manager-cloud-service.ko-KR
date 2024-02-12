---
title: Cloud Service 콘텐츠 요청 이해
description: Adobe에서 컨텐츠 요청 라이선스를 구입한 경우 Adobe Experience Cloud as a Service가 측정하는 컨텐츠 요청 유형과 조직의 분석 보고 도구와의 차이에 대해 알아봅니다.
exl-id: 3666328a-79a7-4dd7-b952-38bb60f0967d
source-git-commit: 13a2aad1fc8080fb0d5060fcc31c9b71f1a833ca
workflow-type: tm+mt
source-wordcount: '2682'
ht-degree: 5%

---

# Cloud Service 컨텐츠 요청

## 소개 {#introduction}

Cloud Service 컨텐츠 요청은 서버측 데이터 수집을 통해 측정됩니다. 컬렉션은 CDN 로그 분석을 통해 활성화됩니다.

>[!NOTE]
>또한 제한된 수의 [얼리 어답터 고객](/help/release-notes/release-notes-cloud/release-notes-current.md#sites-early-adopter), 클라이언트측 컬렉션도 RUM(Real User Monitoring) 측정을 통해 활성화될 수 있습니다. 다음에서 설명서를 참조하여 자세한 내용을 알 수 있습니다. [이 문서](#real-user-monitoring-for-aem-as-a-cloud-service).

## Cloud Service 콘텐츠 요청 이해 {#understaing-cloud-service-content-requests}

컨텐츠 요청은 AEM as a Cloud Service CDN에서 시작되는 로그 파일의 자동화된 분석을 통해 Adobe Experience Manager as a Cloud Service의 에지에서 서버측에서 자동으로 수집됩니다. 이 작업은 HTML을 반환하는 요청을 격리하여 수행됩니다 `(text/html)` 또는 JSON `(application /Json)` 아래에 설명된 여러 포함 및 제외 규칙을 기반으로 하는 CDN의 콘텐츠. 콘텐츠 요청은 CDN 캐시에서 처리 중인 반환된 콘텐츠 또는 CDN(AEM dispatchers)의 소스로 돌아가는 콘텐츠와는 독립적으로 발생합니다.

클라이언트측 컬렉션인 RUM(Real User Monitoring) 데이터 서비스 는 사용자 상호 작용을 보다 정확하게 반영하여 웹 사이트 참여에 대한 신뢰할 수 있는 측정을 보장합니다. 이를 통해 고객은 페이지 트래픽 및 성능에 대한 고급 통찰력을 얻을 수 있습니다. 이는 Adobe 관리 CDN 또는 Adobe이 아닌 관리 CDN을 사용하는 두 고객 모두에게 유용합니다. 또한 이제 Adobe이 아닌 관리 CDN을 사용하는 고객에 대해 자동 트래픽 보고를 활성화할 수 있으므로 트래픽 보고서를 Adobe과 공유할 필요가 없습니다.

AEM as a Cloud Service을 기반으로 자체 CDN을 가져오는 고객의 경우 서버측 보고는 라이선스가 부여된 콘텐츠 요청과 비교하는 데 사용할 수 없는 숫자를 생성합니다. 이러한 수치는 외부 CDN의 끝에서 고객이 측정해야 합니다. 이러한 고객, 클라이언트측 보고 및 관련 성능, [Adobe RUM 데이터 서비스](#real-user-monitoring-for-aem-as-a-cloud-service) 는 Adobe 권장 옵션입니다. 다음을 참조하십시오. [릴리스 정보](/help/release-notes/release-notes-cloud/release-notes-current.md#sites-early-adopter) 을 참조하십시오.

## 서버측 컬렉션 {#serverside-collection}

검색 인덱스나 서비스를 새로 고치기 위해 사이트를 정기적으로 방문하는 잘 알려진 서비스를 포함하여 잘 알려진 봇을 제외하는 규칙이 있습니다.

### Cloud Service 컨텐츠 요청 분산 {#content-requests-variances}

콘텐츠 요청은 다음 표에 요약된 바와 같이 조직의 Analytics 보고 도구와 차이가 있을 수 있습니다. 일반적으로, *금지* 클라이언트측 계측을 통해 데이터를 수집하는 analytics 도구를 사용하여 특정 사이트에 대한 콘텐츠 요청 수를 보고합니다. 이는 종종 트리거되는 사용자 동의에 의존하기 때문에 트래픽의 상당한 부분이 누락되기 때문입니다. Analytics 도구는 로그 파일에 서버측에서 데이터를 수집하거나, AEM as a Cloud Service을 기반으로 자체 CDN을 추가하는 고객을 위한 CDN 보고서를 더 나은 개수를 제공합니다. 페이지 보기 수 및 관련 성능에 대한 보고를 위해 Adobe RUM 데이터 서비스 가 Adobe 권장 옵션입니다.

| 차이가 나는 이유 | 설명 |
|---|---|
| 최종 사용자 동의 | 클라이언트측 계기에 의존하는 Analytics 도구는 종종 트리거되는 사용자 동의에 따라 다릅니다. 이는 추적되지 않는 트래픽의 대부분을 나타낼 수 있습니다. 콘텐츠 요청을 직접 측정하려는 고객의 경우 데이터 서버측 또는 CDN 보고서를 수집하는 분석 도구에 의존하는 것이 좋습니다. |
| 태그 지정 | AEM(Adobe Experience Manager) 콘텐츠 요청으로 추적되는 모든 페이지 또는 API 호출에 Analytics 추적 태그가 지정되지 않을 수 있습니다. |
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
| AEM as a Cloud Service NewRelic 모니터링 | 제외됨 | AEM as a Cloud Service 전역 모니터링. |
| 고객이 Cloud Service 프로그램을 모니터링할 수 있는 URL | 제외됨 | 외부 가용성을 모니터링하는 권장 URL입니다.<br><br>`/system/probes/health` |
| AEM as a Cloud Service Pod 준비 서비스 | 제외됨 | 사용자 에이전트: skyline-service-warmup/1.* |
| 잘 알려진 검색 엔진, 소셜 네트워크 및 HTTP 라이브러리(Fastly에서 태그 지정) | 제외됨 | 검색 인덱스 또는 서비스를 새로 고치기 위해 사이트를 정기적으로 방문하는 잘 알려진 서비스:<br><br>예:<br>· AddSearchBot<br>· ArefsBot<br>· Applebot<br>· Jeeves Corporate Spider에게 문의<br>· 빙보트<br>· BingView<br>· BLEXBot<br>· 기본 제공<br>· Bytespider<br>· CrawlerKengo<br>· Facebookexternalhit<br>· Google AdsBot<br>· Google AdsBot Mobile<br>· Googlebot<br>· Googlebot Mobile<br>· lmspider<br>· LucidWorks<br>· MJ12bot<br>· 핑돔<br>· Pinterest<br>· SemrushBot<br>· 사이트 개선<br>· StashBot<br>· StatusCake<br>· YandexBot |
| Commerce integration framework 호출 제외 | 제외됨 | Commerce integration framework에 전달되는 AEM에 대한 요청입니다(URL은 다음으로 시작). `/api/graphql`- 이중 계산을 방지하기 위해 Cloud Service에 대해 청구할 수 없습니다. |
| 제외 `manifest.json` | 제외됨 | 매니페스트는 API 호출이 아닙니다. 데스크톱이나 휴대폰에 웹 사이트를 설치하는 방법에 대한 정보를 제공하기 위해 여기에 있습니다. Adobe은 JSON 요청을에 계산해서는 안 됩니다. `/etc.clientlibs/*/manifest.json` |
| 제외 `favicon.ico` | 제외됨 | 반환된 콘텐츠는 HTML 또는 JSON이 아니어야 하지만 SAML 인증 흐름과 같은 일부 시나리오에서 favicons를 HTML으로 반환할 수 있으므로 계산에서 명시적으로 제외됨을 관찰하고 있습니다. |

## 클라이언트측 컬렉션 {#cliendside-collection}

### AEM as a Cloud Service을 위한 실제 사용자 모니터링 서비스 {#real-user-monitoring-service-for-aem-as-a-cloud-service}

>[!INFO]
>
>이 기능은 얼리어답터 프로그램에서만 사용할 수 있습니다.
>AEM Cloud Service 버전을 사용해야 합니다. **2023.11.14227** RUM 데이터 서비스를 활성화하기 위한 이상입니다.

### 개요 {#overview}

RUM(Real User Monitoring)은 웹 사이트 또는 애플리케이션의 디지털 사용자 경험을 실시간으로 캡처하고 분석하는 일종의 성능 모니터링 기술입니다. 웹 애플리케이션의 실시간 성능에 대한 가시성을 제공하며 최종 사용자 경험을 정확하게 파악할 수 있습니다.

RUM(Real User Monitoring)은 URL 시작부터 요청이 다시 브라우저로 제공될 때까지 주요 성능 지표에 대한 심층적인 통찰력을 제공합니다. 이러한 모든 통찰력은 개발자가 최종 사용자가 쉽게 사용할 수 있도록 애플리케이션을 향상시키는 데 도움이 됩니다.

### 누가 실제 사용자 모니터링 서비스를 활용할 수 있습니까? {#who-can-benefit-from-rum-service}

RUM 데이터 서비스는 Adobe의 CDN을 활용하든 자체 CDN을 활용하든 모든 고객에게 유용합니다. 사용자 상호 작용을 보다 정확하게 반영하여 클라이언트측 페이지 보기 수를 반영하여 웹 사이트 참여를 안정적으로 측정할 수 있습니다.

특히 Adobe CDN 사용자의 경우 클라이언트측 페이지 보기 수와 서버측 CDN 로그를 직접 비교하기 위해 사용자 상호 작용을 정확하게 추적합니다.

자체 CDN을 사용하는 고객의 경우 이제 Adobe이 이러한 페이지 보기를 직접 통합하여 별도의 보고서가 필요 없으므로 간소화된 트래픽 보고의 이점을 얻을 수 있습니다.

또한 모든 고객은 페이지 성능에 대한 깊은 통찰력을 얻어 디지털 경험을 효과적으로 최적화할 수 있습니다.

### Real User Monitoring Service 작동 방식 이해 {#understand-how-the-rum-service-works}

Adobe Experience Manager은 RUM(Real User Monitoring)을 사용하여 고객 및 Adobe이 Adobe Experience Manager 기반 사이트와 방문자가 상호 작용하는 방법을 이해하고, 성능 문제를 진단하고, 실험의 효과를 측정할 수 있도록 합니다. RUM은 샘플링을 통해 방문자의 개인 정보를 보존하며 - 모든 페이지 보기의 일부만 모니터링됩니다 - 모든 개인 식별 정보(PII)를 신중하게 제외합니다.

### Real User Monitoring Service 및 개인 정보 {#rum-service-and-privacy}

Adobe Experience Manager의 Real User Monitoring은 방문자 개인 정보를 보존하고 데이터 수집을 최소화하도록 설계되었습니다. 이는 방문자인 경우 방문 중인 사이트에서 개인 정보를 수집하지 않거나 Adobe이 사용할 수 없음을 의미합니다.

사이트 운영자는 이 기능을 통해 모니터링을 활성화하는 데 추가 옵트인이 필요하지 않음을 의미합니다. 따라서 최종 사용자가 RUM 모니터링 활성화에 동의하는 추가 팝업은 없습니다.

### Real User Monitoring 서비스 데이터 샘플링 {#rum-service-data-sampling}

기존 웹 분석 솔루션은 모든 단일 방문자에 대한 데이터를 수집하려고 합니다. Adobe Experience Manager의 실제 사용자 모니터링은 극히 일부 페이지 보기에서 정보만 캡처합니다. RUM(Real User Monitoring)은 Analytics를 대체하는 것이 아니라 샘플링하고 익명화하기 위한 것입니다. 기본적으로 페이지는 1:100 샘플링 비율을 갖습니다. 사이트 운영자는 오늘을 기준으로 샘플링 속도를 늘리거나 줄이도록 이 숫자를 구성할 수 없습니다. 총 트래픽을 정확하게 추정하기 위해 100개의 페이지 보기마다 하나의 세부 데이터를 취합하여 전체 트래픽에 대한 신뢰할 수 있는 근사치를 제공합니다.&quot;

데이터 수집 여부는 페이지 보기 단위로 페이지 보기에서 결정되므로 여러 페이지 간 상호 작용을 추적하는 것이 사실상 불가능해진다. RUM에는 방문, 방문자 또는 세션에 대한 개념이 없으며 페이지 보기에만 해당됩니다. 이것은 계획적인 것이다.

### 수집 중인 데이터 {#what-data-is-being-collected}

RUM(Real User Monitoring)은 개인 식별 정보가 수집되는 것을 방지하기 위해 설계되었습니다. Adobe Experience Manager의 Real User Monitoring에서 수집할 수 있는 전체 정보 세트는 다음과 같습니다.

* 방문 중인 사이트의 호스트 이름(예: ) `experienceleague.adobe.com`
* 페이지를 표시하는 데 사용되는 광범위한 사용자 에이전트 유형(예: 데스크탑 또는 모바일)
* 다음과 같은 데이터 수집 시간: `2021-06-26 06:00:02.596000 UTC (in order to preserve privacy, we round all minutes to the previous hour, so that only seconds and milliseconds are tracked)`
* 방문 중인 페이지의 URL(예: ): `https://experienceleague.adobe.com/docs`
* 레퍼러 URL(사용자가 링크를 따라간 경우, 현재 페이지에 연결된 페이지의 URL)
* 다음과 유사한 형식으로 임의로 생성된 페이지 보기의 ID입니다. `2Ac6`
* 샘플링 속도의 가중치 또는 역입니다. 예: `100`. 즉, 100개 중 한 개의 페이지 보기만 기록됩니다
* 체크포인트 또는 페이지를 로드하거나 방문자로서 상호 작용하는 순서에 따른 특정 이벤트의 이름
* 위에서 언급한 체크포인트에 대해 사용자가 상호 작용하는 DOM 요소의 소스 또는 식별자입니다. 예를 들어 이미지일 수 있습니다
* 위에서 언급한 체크포인트에 대해 사용자가 상호 작용하는 대상 또는 외부 페이지 또는 리소스에 대한 링크입니다. 예를 들어`https://blog.adobe.com/jp/publish/2022/06/29/media_162fb947c7219d0537cce36adf22315d64fb86e94.png`
* 방문자의 체감 품질을 설명하는 핵심 웹 바이탈(CWV) 성능 지표, 가장 큰 컨텐츠 페인트(LCP), 첫 번째 입력 지연(FID) 및 누적 레이아웃 이동(CLS)입니다.

### Real User Monitoring Service 설정 방법 {#how-to-set-up-the-rum-service}

* 얼리 어답터 프로그램에 참여하려면 다음으로 이메일을 보내주십시오. `aemcs-rum-adopter@adobe.com`, Adobe ID과 연결된 이메일 주소에서 프로덕션, 스테이징 및 개발 환경의 도메인 이름과 함께 그러면 Adobe 제품 팀에서 실제 사용자 모니터링(RUM) 데이터 서비스를 활성화합니다.
* 이 작업이 완료되면 Adobe의 제품 팀이 고객 공동 작업 채널을 만듭니다.
* Adobe의 제품 팀이 페이지 보기 수 및 를 볼 수 있는 도메인 키 및 데이터 대시보드 URL을 제공하기 위해 연락할 것입니다. [핵심 웹 바이탈(CWV)](https://web.dev/vitals/) 클라이언트측 RUM(Real User Monitoring) 컬렉션에서 수집한 지표.
* 그런 다음 도메인 키를 사용하여 데이터 대시보드 URL에 액세스하고 지표를 보는 방법에 대해 안내합니다.

### 실제 사용자 모니터링 서비스 데이터가 사용되는 방식 {#how-rum-service-data-is-being-used}

RUM 데이터는 다음 목적에 유용합니다.

* 고객 사이트의 성능 병목 현상을 파악하고 해결하기 위한 방법
* 자체 CDN을 사용하는 고객을 위한 페이지 보기 수를 포함하는 간소화된 자동 트래픽 보고로, Adobe과 트래픽 보고서를 공유할 필요가 없습니다.
* Adobe Experience Manager이 호환성을 높이기 위해 동일한 페이지에서 다른 스크립트(예: 분석, 타기팅 또는 외부 라이브러리)와 상호 작용하는 방법을 이해합니다.

### 페이지 보기 수 및 성능 지표의 제한 사항 및 차이 이해 {#limitations-and-understanding-variance-in-page-views-and-performance-metrics}

이 데이터를 분석할 때 RUM(Real User Monitoring)에서 보고하는 페이지 보기 및 기타 성능 지표에 차이가 있을 수도 있고 없을 수도 있습니다. 이러한 분산은 실시간, 클라이언트측 모니터링에 내재된 여러 가지 요인에 기인할 수 있습니다. 고객이 RUM 데이터를 해석할 때 유의해야 할 주요 고려 사항은 다음과 같습니다.

1. **추적기 차단**

   * 추적기 차단기 또는 개인 정보 보호 확장을 사용하는 최종 사용자는 추적 스크립트의 실행을 제한하므로 RUM(Real User Monitoring)의 데이터 수집을 방해할 수 있습니다. 이 제한 사항으로 인해 페이지 보기 수와 사용자 상호 작용이 제대로 보고되지 않아 실제 사이트 활동과 RUM에서 캡처한 데이터 간에 불일치가 발생할 수 있습니다.

1. **API/JSON 호출 캡처의 제한 사항**

   * RUM 데이터 서비스는 클라이언트측 경험에 중점을 두며 현재 백엔드 API 또는 JSON 호출을 캡처하지 않습니다. RUM(Real User Monitoring) 데이터에서 이러한 호출을 제외하면 CDN Analytics에서 측정한 콘텐츠 요청에서 차이가 발생합니다.

### FAQ {#faq}

1. **모니터링에 포함하거나 제외할 경로를 구성하려면 어떻게 해야 합니까?**

   고객은 다음 변수를 사용하여 Cloud Manager의 구성 내에서 환경 변수를 설정하여 모니터링할 URL을 포함하거나 제외하도록 경로를 구성할 수 있습니다. `AEM_WEBVITALS_EXCLUDE` 및 `AEM_WEBVITALS_INCLUDE_PATHS`

   기본적으로 &#39;include&#39; 설정은 &#39;/content&#39;를 타깃팅하도록 구성되어 있습니다. 여기서 구성해야 하는 경로는 브라우저에 표시되는 URL 경로가 아니라 시스템 내의 콘텐츠 경로입니다. 이러한 구분은 특정 요구 사항에 맞게 구성을 정확하게 설정하고 사용자 지정하는 데 중요합니다.

1. **Adobe은 상호 작용이 고객 관리 CDN에 도달하기 전에 또는 상호 작용이 고객 관리 CDN에 도달하는 시점에 모든 페이지 보기를 추적할 수 있습니까?**

   예.

1. **고객이 RUM 데이터 서비스 스크립트를 Dynatrace와 같은 서드파티 시스템과 통합할 수 있습니까?**

   예.

1. **다음 페인트에 대한 상호 작용&quot;, &quot;첫 번째 바이트에 대한 시간&quot; 및 &quot;첫 번째 만족도 페인트&quot; 웹 바이탈 지표가 수집됩니까?**

   다음 페인트에 대한 상호 작용(INP) 및 첫 번째 바이트에 대한 시간(TTFB)이 수집됩니다.  지금은 첫 번째 컨텐트가 수집되지 않습니다.
