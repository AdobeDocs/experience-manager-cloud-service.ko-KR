---
title: Cloud Service 콘텐츠 요청 이해
description: Adobe에서 컨텐츠 요청 라이선스를 구입한 경우 Adobe Experience Cloud as a Service가 측정하는 컨텐츠 요청 유형과 조직의 분석 보고 도구에 대한 차이점에 대해 알아봅니다.
exl-id: 3666328a-79a7-4dd7-b952-38bb60f0967d
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Developer
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '1918'
ht-degree: 2%

---

# Cloud Service 콘텐츠 요청 이해

## 소개 {#introduction}

콘텐츠 요청에는 AEM Sites에 전송된 요청이 포함됩니다. 이러한 요청은 Edge Delivery Services 또는 CDN(Content Delivery Network)과 같은 고객 제공 캐싱 시스템을 통해 라우팅될 수 있습니다. 이러한 요청은 구조화된 데이터를 HTML 또는 JSON 형식으로 제공하며 Headless 방식으로 API를 통해 페이지 보기(예: 페이지 및 경험 조각) 또는 JSON 반환을 지원합니다.

시스템은 사용자가 HTML 또는 JSON을 사용하여 페이지를 볼 때 콘텐츠 요청을 계산합니다. 첫 번째 캐싱 시스템이 요청을 수신하는 지점에서 요청을 측정합니다. 특정 HTTP 요청은 콘텐츠 요청 계산을 위해 포함되거나 제외됩니다. HTTP [포함된 콘텐츠 요청](#included-content-requests) 및 [제외된 콘텐츠 요청](#excluded-content-request)의 전체 목록을 확인하십시오.

>[!NOTE]
>
>콘텐츠 요청 보기에 표시된 데이터는 24시간마다 새로 고쳐집니다.

## Cloud Service 콘텐츠 요청 정보 {#understanding-cloud-service-content-requests}

*페이지 요청*&#x200B;은(는) 기본 페이지 경험을 렌더링하는 데 필요한 핵심 구조화된 콘텐츠(예: HTML 또는 JSON)를 검색하는 HTTP 요청을 참조합니다. 이미지 또는 스크립트와 같은 에셋에 대한 요청은 포함되지 않습니다.

기본 제공 CDN을 사용하는 고객의 경우 AEM as a Cloud Service은 서버측 수준에서 측정한 대로 콘텐츠 요청을 계산합니다. 이 측정은 자동으로 수행되며 클라이언트측 분석 추적에 의존하지 않습니다.

AEM(Adobe Experience Manager) as a Cloud Service은 AEM 인스턴스에서 생성되고 CDN에서 수신된 응답 유형을 기반으로 콘텐츠 요청을 식별합니다. 특히 HTML(`text/html`) 또는 JSON(`application/json`)을 반환하는 요청이 카운트됩니다. 이러한 형식은 일반적으로 기존 사이트 렌더링 또는 Headless 전달을 위한 기본 페이지 콘텐츠를 제공합니다.

JavaScript 파일, CSS 스타일 시트 및 이미지와 같은 정적 자산에 대한 요청은 콘텐츠 요청으로 계산되지 않습니다.

>[!NOTE]
>API 요청이 페이지 수준 콘텐츠 역할을 하는 HTML 또는 JSON을 반환하는 경우(예를 들어 Headless 게재에서) 컨텍스트에 따라 콘텐츠 요청으로 카운트될 수 있습니다.

응답이 CDN 캐시에서 제공되었는지 또는 원본 AEM 환경으로 전달되었는지 여부에 관계없이 컨텐츠 요청이 측정됩니다.

<!-- REMOVED AS PER EMAIL REQUEST FROM SHWETA DUA, JULY 30, 2024 TO RICK BROUGH AND ALEXANDRU SARCHIZ   For customers employing their own CDN, client-side collection offers a more precise reflection of interactions, ensuring a reliable measure of website engagement via the [Real Use Monitoring](/help/sites-cloud/administering/real-use-monitoring-for-aem-as-a-cloud-service.md) service. This gives customers advanced insights into their page traffic and performance. While it is beneficial for all customers, it offers a representative reflection of user interactions, ensuring a reliable measure of website engagement by capturing the number of page views from the client side. 

For customers that bring their own CDN on top of AEM as a Cloud Service, server-side reporting results in numbers that cannot be used to compare with the licensed content requests. With the [Real Use Monitoring](/help/sites-cloud/administering/real-use-monitoring-for-aem-as-a-cloud-service.md), Adobe can reflect a reliable measure of website engagement. -->

### Cloud Service 콘텐츠 요청 분산 {#content-requests-variances}

콘텐츠 요청은 다음 표에 요약된 바와 같이 조직의 분석 보고 도구 내에 차이를 가질 수 있습니다. 일반적으로 클라이언트측 계측을 사용하는 분석 도구를 사용하여 사이트에 대한 콘텐츠 요청 수를 보고하지 마십시오. 이러한 도구는 활성화하려는 사용자 동의에 의존하기 때문에 트래픽의 많은 부분을 놓치는 경우가 많습니다. Analytics 도구는 로그 파일에 서버측에서 데이터를 수집하거나, AEM as a Cloud Service에 자체 CDN을 추가하는 고객을 위한 CDN 보고서를 더 나은 개수를 제공합니다.

| 차이가 나는 이유 | 설명 |
|---|---|
| 최종 사용자 동의 | 클라이언트측 계기에 의존하는 Analytics 도구는 종종 트리거되는 사용자 동의에 따라 다릅니다. 이 워크플로우는 추적되지 않는 트래픽의 대부분을 나타낼 수 있습니다. Adobe 컨텐츠 요청을 자체적으로 측정하려는 고객의 경우 Analytics 도구를 사용하여 서버측 또는 CDN 보고서에서 데이터를 수집하는 것이 좋습니다. |
| 태그 지정 | Adobe Experience Manager 콘텐츠 요청으로 추적되는 모든 페이지 또는 API 호출에 Analytics 추적 태그가 지정되지 않을 수 있습니다. |
| 태그 관리 규칙 | 태그 관리 규칙 설정으로 인해 페이지에 다양한 데이터 수집 구성이 발생할 수 있으며, 이로 인해 콘텐츠 요청 추적과 일부 불일치가 발생할 수 있습니다. |
| 봇 | AEM에서 사전 식별 및 제거하지 않은 알 수 없는 봇으로 인해 추적 불일치가 발생할 수 있습니다. |
| 보고서 세트 | 동일한 AEM 인스턴스 내의 페이지는 다른 분석 보고서 세트에 보고할 수 있습니다. 이 프로세스는 구성에 따라 여러 세트에 데이터를 분할할 수 있습니다. |
| 서드파티 모니터링 및 보안 도구 | 모니터링 및 보안 검색 도구(예: 가동 시간 검사기 또는 취약점 스캐너)는 페이지를 요청하여 분석 보고서에 표시되지 않는 서버측 콘텐츠 요청을 생성할 수 있습니다. |
| API 액세스 | API를 통해 AEM 페이지 또는 콘텐츠에 대한 요청(예: Adobe Experience Manager as a Headless CMS을 통해)은 여전히 콘텐츠 요청으로 계산되지만 분석 추적을 트리거하지 않습니다. |
| 프리페치 요청 | 프리페치(예: 서비스 작업자 또는 Edge 함수 사용)는 페이지를 미리 요청하여 트래픽 볼륨을 증가시킬 수 있습니다. 이러한 요청은 서버측에서 계산되지만 클라이언트측 분석 코드는 실행되지 않습니다. |
| DDOS | Adobe은 필터링을 사용하여 많은 DDoS 공격을 감지하고 차단합니다. 그러나 일부 공격 요청은 필터가 적용되기 전에 콘텐츠 요청으로 계속 카운트될 수 있습니다. |
| 트래픽 차단 | 브라우저 내 개인 정보 보호 기능 또는 회사 방화벽이 분석 스크립트를 로드할 수 없도록 차단할 수 있습니다. 이러한 사용자는 여전히 서버측 콘텐츠 요청을 생성합니다. |
| 방화벽 | 회사 또는 지역 방화벽으로 인해 분석 호출이 Adobe 서버에 도달하지 못하여 분석에서 보고가 부족한 반면 서버측 수는 영향을 받지 않을 수 있습니다. |

라이선스 제한에 대한 콘텐츠 요청 사용량을 보고 추적하는 방법에 대한 자세한 내용은 [라이선스 대시보드](/help/implementing/cloud-manager/license-dashboard.md)를 참조하십시오.

## 서버측 컬렉션 규칙 {#serverside-collection}

AEM as a Cloud Service은 콘텐츠 요청을 계산하기 위해 서버측 수집 규칙을 적용합니다. 이러한 규칙은 잘 알려진 보트 (예: 검색 엔진 크롤러)와 사이트를 정기적으로 ping하는 모니터링 서비스 세트를 제외합니다. 이 제외 목록에 없는 기타 가상 또는 모니터링 유형 트래픽은 청구 가능한 콘텐츠 요청으로 계산됩니다.

다음 표는 포함된 콘텐츠 요청과 제외된 콘텐츠 요청의 유형을 나열하며 각각에 대한 간단한 설명을 제공합니다.

### 포함된 콘텐츠 요청 유형 {#included-content-requests}

>[!NOTE]
>API 요청이 HTML 응답을 반환하는 경우 사용 컨텍스트에 따라 콘텐츠 요청으로 분류될 수 있습니다. 비 UI 데이터를 반환하는 API 요청은 일반적으로 제외됩니다.

| 요청 유형 | 콘텐츠 요청 | 설명 |
| --- | --- | --- |
| HTTP 코드 100-299 | 포함됨 | HTML 또는 JSON 콘텐츠의 전체 또는 일부를 반환하는 성공적인 요청을 포함합니다.<br>HTTP 코드 206: 이러한 요청은 전체 콘텐츠의 일부만 전달합니다. 예를 들어, 비디오 또는 큰 이미지가 여기에 해당합니다. 부분 콘텐츠 요청은 페이지 콘텐츠를 렌더링하는 데 사용되는 HTML 또는 JSON 응답의 일부를 전달할 때 포함됩니다. |
| 자동화를 위한 HTTP 라이브러리 | 포함됨 | 페이지 콘텐츠를 검색하는 도구 또는 라이브러리에서 만든 요청입니다. 예: <br>· Amazon CloudFront<br>· Apache Http 클라이언트<br>· 비동기 HTTP 클라이언트<br>· Axios<br>· Azureus<br>· Curl<br>· GitHub 노드 가져오기<br>· Guzzle<br>· Go-http-client<br>· Headless Chrome<br>· Java™ 클라이언트<br>· Jersey<br>· Node Oembed<br>· okhttp<br>· Python 요청<br>· Reactor Netty<br>· Wget<br>· WinHTTP<br>· Fast HTTP<br> gitHub 노드 가져오기<br>· Reactor Netty |
| 모니터링 및 상태 확인 도구 | 포함됨 | 페이지의 상태 또는 가용성을 모니터링하는 데 사용되는 요청입니다.<br>제외된 콘텐츠 요청의 [유형](#excluded-content-request)을 참조하세요.<br>예:<br>· `Amazon-Route53-Health-Check-Service`<br>· EyeMonIT_bot_version_0.1_[(https://eyemonit.com/)](https://eyemonit.com/)<br>· Investis-Site24x7<br>· Mozilla/5.0+(호환 가능; UptimeRobot/2.0; [https://uptimerobot.com/](https://uptimerobot.com/))<br>· ThousandEyes-Dragonfly-x1<br>· OmtrBot/1.0<br>· WebMon/2.0.0 |
| `<link rel="prefetch">`개 요청 | 포함됨 | 고객이 콘텐츠를 미리 로드하거나 미리 가져오면(예: `<link rel="prefetch">` 사용) 시스템에서 해당 서버측 요청을 계산합니다. 미리 가져온 페이지 수에 따라 이 접근 방식으로 트래픽이 증가할 수 있습니다. |
| Adobe Analytics 또는 Google Analytics 보고를 차단하는 트래픽 | 포함됨 | 사이트 방문자에게 Google Analytics 또는 Adobe Analytics의 정확도에 영향을 주는 개인 정보 보호 소프트웨어(광고 차단기 등)가 설치된 경우가 더 일반적입니다. AEM as a Cloud Service은 클라이언트측이 아닌 Adobe 운영 인프라의 첫 번째 진입점에 대한 요청을 계산합니다. |

[라이선스 대시보드](/help/implementing/cloud-manager/license-dashboard.md)도 참조하세요.

### 제외된 콘텐츠 요청 유형 {#excluded-content-request}

| 요청 유형 | 콘텐츠 요청 | 설명 |
| --- | --- | --- |
| HTTP 코드 500+ | 제외됨 | AEM as a Cloud Service 또는 고객 사용자 지정 코드에서 문제가 발생하면 방문자에게 오류가 반환되었습니다. |
| HTTP 코드 400-499 | 제외됨 | 콘텐츠가 없거나(404) 다른 콘텐츠 또는 요청 관련 문제가 있으면 방문자에게 오류가 반환됩니다. |
| HTTP 코드 300-399 | 제외됨 | 서버에서 변경된 사항이 있는지 확인하거나 요청을 다른 리소스로 리디렉션하는 좋은 요청입니다. 여기에는 콘텐츠 자체가 포함되어 있지 않으므로 청구할 수 없습니다. |
| `/libs/`(으)로 이동하는 요청* | 제외됨 | 청구할 수 없는 CSRF 토큰과 같은 AEM 내부 JSON 요청. |
| DDOS 공격의 트래픽 | 제외됨 | DDOS 보호. AEM은 일부 DDOS 공격을 자동으로 감지하여 차단합니다. 감지된 경우 DDOS 공격은 청구할 수 없습니다. |
| AEM as a Cloud Service New Relic 모니터링 | 제외됨 | AEM as a Cloud Service 글로벌 모니터링. |
| 고객이 Cloud Service 프로그램을 모니터링할 수 있는 URL | 제외됨 | Adobe은 URL을 사용하여 외부에서 가용성 또는 상태 검사를 모니터링할 것을 권장합니다.<br><br>`/system/probes/health` |
| AEM as a Cloud Service Pod 준비 서비스 | 제외됨 |
| 요원: 스카이라인-서비스-웜업/1* |
| 잘 알려진 검색 엔진, 소셜 네트워크 및 HTTP 라이브러리(Fastly에서 태그 지정) | 제외됨 | 검색 인덱스 또는 서비스를 새로 고치기 위해 사이트를 정기적으로 방문하는 잘 알려진 서비스:<br><br>예:<br>· AddSearchBot<br>· AhrefsBot<br>· Applebot<br>· Jeeves Corporate Spider에 문의<br>· Bingbot<br>· BingPreview<br>· BLEXBot<br>· BuiltWith<br>· Bytespider<br>· CrawlerKengo<br>· Facebookexternalhit<br>· Google AdsBot<br>· Google AdsBot Mobile<br>· Googlebot Mobile<br>· lmspider<br>· LucidWorks<br>· <br>· Pinterest`MJ12bot`<br>· SemrushBot<br>· SiteImprove<br>· StashBot<br>· StatusCake<br>· YandexBot<br>· ContentKing<br>· Claudebot<br> |
| Commerce integration framework 호출 제외 | 제외됨 | AEM에 수행된 요청이 Commerce integration framework(URL은 `/api/graphql`(으)로 시작)로 전달되므로 두 번 계산되지 않습니다. Cloud Service에 대해서는 청구할 수 없습니다. |
| `manifest.json` 제외 | 제외됨 | 매니페스트가 API 호출이 아닙니다. 데스크탑 또는 휴대 전화에 웹 사이트를 설치하는 방법에 대한 정보를 제공하기 위해 여기에 있습니다. Adobe은 `/etc.clientlibs/*/manifest.json`에 대한 JSON 요청을 계산해서는 안 됩니다. |
| `favicon.ico` 제외 | 제외됨 | 반환된 콘텐츠가 HTML 또는 JSON이 아니어야 하지만 SAML 인증 흐름과 같은 특정 시나리오에서는 favicons를 HTML으로 반환하는 것으로 관찰되었습니다. 따라서 favicons는 카운트에서 명시적으로 제외됩니다. |
| XF(경험 조각) - 동일한 도메인 재사용 | 제외됨 | 동일한 도메인에 호스팅된 페이지의 XF 경로(예: `/content/experience-fragments/...`)에 대한 요청(요청 호스트와 일치하는 Referer 헤더로 식별됨).<br><br> 예: 동일한 도메인에서 배너 또는 카드에 대한 XF를 가져오는 `aem.customer.com`의 홈 페이지.<br><br>· URL이 /content/experience-fragments/...<br>· Referer 도메인이 `request_x_forwarded_host`<br><br>**와(과) 일치합니다. 참고:** 경험 조각 경로를 사용자 지정하는 경우(예: `/XFrags/...` 또는 `/content/experience-fragments/` 외부의 경로를 사용하는 경우) 요청은 제외되지 않으며 동일한 도메인인 경우에도 카운트될 수 있습니다. 제외 논리가 올바르게 적용되도록 Adobe의 표준 XF 경로 구조를 사용하는 것이 좋습니다. |

## 콘텐츠 요청 관리 {#managing-content-requests}

위의 섹션 [Cloud Service 콘텐츠 요청의 분산](#content-requests-variances)에서 언급했듯이 콘텐츠 요청은 여러 가지 이유로 인해 예상보다 높을 수 있습니다. 공통 스레드는 CDN에 도달하는 트래픽입니다.  라이선스 예산에 맞게 콘텐츠 요청을 모니터링하고 관리하는 것은 AEM 고객으로서 유용할 수 있습니다.  콘텐츠 요청 관리는 일반적으로 구현 기술과 [트래픽 필터 규칙](/help/security/traffic-filter-rules-including-waf.md)의 조합입니다.

### 콘텐츠 요청을 관리하는 구현 기술 {#implementation-techniques-to-manage-crs}

* 페이지를 찾을 수 없음 응답이 HTTP 상태 404로 전달되는지 확인합니다.  상태 200으로 반환되면 콘텐츠 요청에 포함됩니다.
* 상태 검사 또는 모니터링 도구를 /systems/probes/health URL로 라우팅하거나 컨텐츠 요청이 발생하지 않도록 GET 대신 HEAD 메서드를 사용하십시오.
* 사이트와 통합한 모든 사용자 정의 검색 크롤러에 대한 AEM 라이선스 비용과 콘텐츠의 신선도에 대한 요구 사항의 균형을 맞추십시오.  지나치게 공격적인 크롤러는 많은 콘텐츠 요청을 소비할 수 있습니다.
* 리디렉션을 클라이언트측(JavaScript 리디렉션을 사용하는 상태 200)이 아닌 서버측(상태 301 또는 302)으로 처리하여 두 개의 별도 콘텐츠 요청을 방지합니다.
* 페이지를 렌더링하기 위해 로드될 수 있는 AEM의 JSON 응답인 API 호출을 결합하거나 줄입니다.

### 콘텐츠 요청을 관리하는 트래픽 필터 규칙 {#traffic-filter-rules-to-manage-crs}

* 일반적인 봇 패턴은 빈 사용자 에이전트를 사용하는 것입니다.  구현 및 트래픽 패턴을 검토하여 빈 사용자 에이전트가 유용한지 여부를 확인해야 합니다.  이 트래픽을 차단하려면 [구문](/help/security/traffic-filter-rules-including-waf.md#rules-syntax)을(를) 사용하는 것이 좋습니다.

```
trafficFilters:
  rules:
    - name: block-missing-user-agent
      when:
        anyOf:
          - { reqHeader: user-agent, exists: false }
          - { reqHeader: user-agent, equals: '' }
      action: block
```

* 어떤 봇들은 어느 날 사이트를 매우 심하게 강타하고 그 다음 날 사라집니다.  이렇게 하면 특정 IP 주소 또는 사용자 에이전트를 차단하려는 시도가 좌절될 수 있습니다.  일반적인 접근 방식 중 하나는 [비율 제한 규칙](/help/security/traffic-filter-rules-including-waf.md#rate-limit-rules)을 도입하는 것입니다.  [예제](/help/security/traffic-filter-rules-including-waf.md#ratelimiting-examples)를 검토하고 빠른 요청 속도를 위해 허용 한도와 일치하는 규칙을 만드십시오.  일반 속도 제한으로 허용할 수 있는 예외를 보려면 [조건 구조](/help/security/traffic-filter-rules-including-waf.md#condition-structure) 구문을 검토하십시오.
