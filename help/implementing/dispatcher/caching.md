---
title: AEM as a Cloud Service에서 캐싱
description: AEM as a Cloud Service 캐싱의 기본 사항에 대해 알아봅니다.
feature: Dispatcher
exl-id: 4206abd1-d669-4f7d-8ff4-8980d12be9d6
role: Admin
source-git-commit: 0e328d013f3c5b9b965010e4e410b6fda2de042e
workflow-type: tm+mt
source-wordcount: '2894'
ht-degree: 1%

---

# 소개 {#intro}

트래픽은 CDN을 통해 Dispatcher를 포함한 모듈을 지원하는 Apache 웹 서버 계층으로 전달됩니다. 성능을 향상시키기 위해 Dispatcher는 주로 게시 노드에서 처리를 제한하는 캐시로 사용됩니다.
규칙을 Dispatcher 구성에 적용하여 기본 캐시 만료 설정을 수정할 수 있으며 이로 인해 CDN에서 캐싱이 발생합니다. Dispatcher는 다음과 같은 경우 결과 캐시 만료 헤더도 준수합니다. `enableTTL` 는 Dispatcher 구성에서 활성화되므로 다시 게시되는 콘텐츠 외부에서도 특정 콘텐츠를 새로 고침한다는 것을 의미합니다.

이 페이지에서는 Dispatcher 캐시가 무효화되는 방식과 클라이언트측 라이브러리와 관련된 브라우저 수준에서 캐싱이 작동하는 방식에 대해서도 설명합니다.

## 캐싱 {#caching}

### HTML/텍스트 {#html-text}

* 기본적으로 를 기반으로 5분 동안 브라우저에서 캐시됩니다. `cache-control` apache 계층에서 내보낸 헤더입니다. CDN도 이 값을 준수합니다.
* 다음을 정의하여 기본 HTML/텍스트 캐싱 설정을 비활성화할 수 있습니다. `DISABLE_DEFAULT_CACHING` 의 변수 `global.vars`:

```
Define DISABLE_DEFAULT_CACHING
```

이 방법은 예를 들어 비즈니스 로직에서 연령 헤더를 미세 조정해야 하는 경우(역일을 기준으로 한 값 포함) 기본적으로 연령 헤더가 0으로 설정되어 있기 때문에 유용합니다. 그 말은, **기본 캐싱을 해제할 때 주의하십시오.**

* 를 정의하여 모든 HTML/텍스트 컨텐츠에 대해 재정의할 수 있습니다. `EXPIRATION_TIME` 의 변수 `global.vars` AEM as a Cloud Service SDK Dispatcher 도구 사용.
* 다음 Apache를 사용하여 CDN 및 브라우저 캐시를 독립적으로 제어하는 등 보다 세분화된 수준에서 재정의할 수 있습니다 `mod_headers` 지시문:

  ```
  <LocationMatch "^/content/.*\.(html)$">
       Header set Cache-Control "max-age=200"
       Header set Surrogate-Control "max-age=3600"
       Header set Age 0
  </LocationMatch>
  ```

  >[!NOTE]
  >Surrogate-Control 헤더는 Adobe 관리 CDN에 적용됩니다. 를 사용하는 경우 [고객 관리 CDN](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/content-delivery/cdn.html#point-to-point-CDN): CDN 공급자에 따라 다른 헤더가 필요할 수 있습니다.

  전역 캐시 제어 헤더나 넓은 정규식과 일치하는 유사한 캐시 헤더를 설정할 때 주의해서 사용해야 하는 콘텐츠에 해당 헤더가 적용되지 않도록 합니다. 규칙이 세분화된 방식으로 적용되도록 하려면 여러 지시문을 사용하는 것이 좋습니다. 이를 통해 AEM은 Dispatcher 설명서에 설명된 대로 Dispatcher에서 캐시할 수 없다고 감지한 항목에 적용되었음을 감지하는 경우 캐시 헤더를 as a Cloud Service으로 제거합니다. AEM에서 항상 캐싱 헤더를 적용하도록 하려면 다음을 추가할 수 있습니다. **`always`** 옵션은 다음과 같습니다.

  ```
  <LocationMatch "^/content/.*\.(html)$">
       Header unset Cache-Control
       Header unset Expires
       Header always set Cache-Control "max-age=200"
       Header set Age 0
  </LocationMatch>
  ```

  아래에 파일이 있는지 확인합니다 `src/conf.dispatcher.d/cache` 에는 (기본 구성에 있는) 다음 규칙이 있습니다.

  ```
  /0000
  { /glob "*" /type "allow" }
  ```

* 특정 콘텐츠가 캐시되지 않도록 하려면 **CDN에서**, Cache-Control 헤더를 로 설정합니다. *비공개*. 예를 들어, 다음은 라는 디렉터리에 있는 html 콘텐츠를 금지합니다 **secure** 이 CDN에서 캐시되는 경우:

  ```
     <LocationMatch "/content/secure/.*\.(html)$">.  // replace with the right regex
     Header unset Cache-Control
     Header unset Expires
     Header always set Cache-Control "private"
    </LocationMatch>
  ```

* 전용으로 설정된 HTML 콘텐츠는 CDN에서 캐시되지 않지만 다음과 같은 경우 Dispatcher에서 캐시될 수 있습니다. [권한 구분 캐싱](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/permissions-cache.html?lang=ko-KR) 권한이 있는 사용자만 콘텐츠를 제공할 수 있도록 가 구성되어 있습니다.

  >[!NOTE]
  >다음을 포함한 기타 방법 [Dispatcher-ttl AEM ACS Commons 프로젝트](https://adobe-consulting-services.github.io/acs-aem-commons/features/dispatcher-ttl/)는 값을 성공적으로 재정의하지 않습니다.

  >[!NOTE]
  >Dispatcher는 자체 콘텐츠에 따라 콘텐츠를 계속 캐시할 수 있습니다 [캐싱 규칙](https://experienceleague.adobe.com/docs/experience-cloud-kcs/kbarticles/KA-17497.html). 콘텐츠를 정말로 비공개로 만들려면 Dispatcher에서 캐시되지 않았는지 확인하십시오.

### 클라이언트측 라이브러리(js,css) {#client-side-libraries}

* AEM 클라이언트 측 라이브러리 프레임워크를 사용하는 경우 모든 변경 사항이 고유한 경로를 가진 새 파일로 매니페스트되므로 브라우저에서 무기한 캐시할 수 있는 방식으로 JavaScript 및 CSS 코드가 생성됩니다. 즉, 클라이언트 라이브러리를 참조하는 HTML은 필요에 따라 생성되므로 고객은 게시된 대로 새로운 콘텐츠를 경험할 수 있습니다. cache-control은 &quot;immutable&quot; 또는 &quot;immutable&quot; 값을 준수하지 않는 오래된 브라우저의 경우 30일로 설정됩니다.
* 섹션 보기 [클라이언트 측 라이브러리 및 버전 일관성](#content-consistency) 추가 세부 정보.

### 이미지 및 Blob 저장소에 저장될 만큼 큰 모든 콘텐츠 {#images}

2022년 5월 중순 이후에 만든 프로그램(특히, 65000보다 높은 프로그램 ID의 경우)의 기본 동작은 기본적으로 캐시하는 반면 요청의 인증 컨텍스트도 준수합니다. 이전 프로그램(프로그램 ID가 65000보다 작거나 같음)은 기본적으로 Blob 콘텐츠를 캐시하지 않습니다.

두 경우 모두 Apache를 사용하여 Apache/Dispatcher 계층에서 보다 세분화된 수준에서 캐싱 헤더를 재정의할 수 있습니다 `mod_headers` 지시문, 예:

```
   <LocationMatch "^/content/.*\.(jpeg|jpg)$">
     Header set Cache-Control "max-age=222"
     Header set Age 0
   </LocationMatch>
```

Dispatcher 레이어에서 캐싱 헤더를 수정할 때 너무 광범위하게 캐시하지 않도록 주의하십시오. HTML/텍스트 섹션에서 토론을 참조하십시오 [위](#html-text). 또한 캐시되지 않고 비공개로 유지되어야 하는 에셋이 `LocationMatch` 지시문 필터.

Blob 저장소에 저장된 JCR 리소스(16KB보다 큼)는 일반적으로 AEM에서 302 리디렉션으로 제공됩니다. 이러한 리디렉션은 이전되고 CDN이 뒤따르며 콘텐츠는 Blob 저장소에서 직접 전달됩니다. 이러한 응답에 대해 제한된 헤더 세트만 사용자 정의할 수 있습니다. 예: 사용자 정의 `Content-Disposition` 다음과 같이 dispatcher 지시문을 사용해야 합니다.

```
<LocationMatch "\.(?i:pdf)$">
  ForceType application/pdf
  Header set Content-Disposition inline
  </LocationMatch>
```

Blob 응답에서 사용자 지정할 수 있는 헤더 목록은 다음과 같습니다.

```
content-security-policy
x-frame-options
x-xss-protection
x-content-type-options
x-robots-tag
access-control-allow-origin
content-disposition
permissions-policy
referrer-policy
x-vhost
content-disposition
cache-control
vary
```

#### 새로운 기본 캐싱 동작 {#new-caching-behavior}

AEM 계층은 캐시 헤더가 이미 설정되었는지 여부와 요청 유형의 값에 따라 캐시 헤더를 설정합니다. 캐시 제어 헤더가 설정되지 않은 경우 공개 컨텐츠가 캐시되고 인증된 트래픽이 비공개로 설정됩니다. 캐시 제어 헤더가 설정되면 캐시 헤더는 그대로 유지됩니다.

| 캐시 제어 헤더가 있습니까? | 요청 유형 | AEM은 캐시 헤더를 로 설정합니다. |
|------------------------------|---------------|------------------------------------------------|
| 아니요 | 공용 | Cache-Control: public, max-age=600, 변경 불가 |
| 아니요 | 인증됨 | Cache-Control: private, max-age=600, 변경 불가 |
| 예 | 임의 | 변경되지 않음 |

권장되지는 않지만 Cloud Manager 환경 변수를 설정하여 새 기본 동작을 이전 동작(65000보다 작거나 같은 프로그램 ID)에 따라 변경할 수 있습니다 `AEM_BLOB_ENABLE_CACHING_HEADERS` false로 변경합니다.

#### 이전 기본 캐싱 동작 {#old-caching-behavior}

AEM 레이어는 기본적으로 Blob 콘텐츠를 캐시하지 않습니다.

>[!NOTE]
>Cloud Manager 환경 변수 AEM_BLOB_ENABLE_CACHING_HEADERS를 true로 설정하여 이전 기본 동작을 새 동작(65000보다 높은 프로그램 ID)과 일치하도록 변경합니다. 프로그램이 이미 라이브 상태인 경우 변경 후 컨텐츠가 예상대로 작동하는지 확인하십시오.

이제 private으로 표시된 Blob 저장소의 이미지는 를 사용하여 Dispatcher에서 캐시할 수 없습니다. [권한 구분 캐싱](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/permissions-cache.html?lang=ko-KR). 이 이미지는 항상 AEM 원본에서 요청되며 사용자에게 권한이 부여된 경우 제공됩니다.

>[!NOTE]
>다음을 포함한 기타 방법 [dispatcher-ttl AEM ACS Commons 프로젝트](https://adobe-consulting-services.github.io/acs-aem-commons/features/dispatcher-ttl/), 값을 재정의하지 않습니다.

### 노드 저장소의 기타 콘텐츠 파일 형식 {#other-content}

* 기본 캐싱 없음
* 기본값은 로 설정할 수 없습니다. `EXPIRATION_TIME` html/text 파일 유형에 사용되는 변수입니다
* 적절한 정규 표현식을 지정하여 html/text 섹션에 설명된 것과 동일한 LocationMatch 전략으로 캐시 만료를 설정할 수 있습니다

### 추가 최적화 {#further-optimizations}

* 사용하지 않음 `User-Agent` 의 일부로 `Vary` 머리글입니다. 이전 버전의 기본 Dispatcher 설정(Archetype 버전 28 이전)에 포함되어 있으며 Adobe은 아래 단계를 사용하여 제거할 것을 권장합니다.
   * 에서 vhost 파일 찾기 `<Project Root>/dispatcher/src/conf.d/available_vhosts/*.vhost`
   * 다음 줄을 제거하거나 주석 처리합니다. `Header append Vary User-Agent env=!dont-vary` 읽기 전용인 default.vhost를 제외한 모든 vhost 파일에서
* 사용 `Surrogate-Control` 브라우저 캐싱과 독립적으로 CDN 캐싱을 제어하는 헤더
* 적용 고려 [`stale-while-revalidate`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Cache-Control#stale-while-revalidate) 및 [`stale-if-error`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Cache-Control#stale-if-error) 는 배경 새로 고침을 허용하고 캐시 누락을 방지하여 콘텐츠를 빠르고 새로 고침하도록 지시합니다.
   * 이러한 지시문을 적용하는 방법은 여러 가지가 있지만 30분을 추가한다 `stale-while-revalidate` 모든 캐시 제어 헤더에는 시작점이 적절합니다.
* 몇 가지 예는 고유한 캐싱 규칙을 설정할 때 안내서로 사용할 수 있는 다양한 콘텐츠 유형에 대해 설명합니다. 특정 설정 및 요구 사항을 신중하게 고려하고 테스트하십시오.

   * 12시간 동안 가변 클라이언트 라이브러리 리소스를 캐시하고 12시간 후 백그라운드 새로 고침을 수행합니다.

     ```
     <LocationMatch "^/etc\.clientlibs/.*\.(?i:json|png|gif|webp|jpe?g|svg)$">
        Header set Cache-Control "max-age=43200,stale-while-revalidate=43200,stale-if-error=43200,public" "expr=%{REQUEST_STATUS} < 400"
        Header set Age 0
     </LocationMatch>
     ```

   * 변경 불가능한 클라이언트 라이브러리 리소스를 장기간(30일) 캐시하고 백그라운드 새로 고침을 통해 MISS를 방지합니다.

     ```
     <LocationMatch "^/etc\.clientlibs/.*\.(?i:js|css|ttf|woff2)$">
        Header set Cache-Control "max-age=2592000,stale-while-revalidate=43200,stale-if-error=43200,public,immutable" "expr=%{REQUEST_STATUS} < 400"
        Header set Age 0
     </LocationMatch>
     ```

   * 브라우저에서 1시간, CDN에서 12시간 동안 백그라운드 새로 고침으로 5분 동안 HTML 페이지를 캐시합니다. 캐시 제어 헤더가 항상 추가되므로 /content/* 아래의 일치하는 html 페이지가 public이 되도록 하는 것이 중요합니다. 그렇지 않은 경우 보다 구체적인 정규 표현식을 사용하는 것이 좋습니다.

     ```
     <LocationMatch "^/content/.*\.html$">
        Header unset Cache-Control
        Header always set Cache-Control "max-age=300,stale-while-revalidate=3600" "expr=%{REQUEST_STATUS} < 400"
        Header always set Surrogate-Control "stale-while-revalidate=43200,stale-if-error=43200" "expr=%{REQUEST_STATUS} < 400"
        Header set Age 0
     </LocationMatch>
     ```

   * Content services/Sling 모델 익스포터 json 응답을 5분 동안 캐시합니다. 백그라운드 새로 고침은 브라우저에서 1시간, CDN에서 12시간 동안 수행합니다.

     ```
     <LocationMatch "^/content/.*\.model\.json$">
        Header set Cache-Control "max-age=300,stale-while-revalidate=3600" "expr=%{REQUEST_STATUS} < 400"
        Header set Surrogate-Control "stale-while-revalidate=43200,stale-if-error=43200" "expr=%{REQUEST_STATUS} < 400"
        Header set Age 0
     </LocationMatch>
     ```

   * 기록 누락을 방지하기 위해 핵심 이미지 구성 요소에서 변경할 수 없는 URL을 장기간(30일) 캐시합니다.

     ```
     <LocationMatch "^/content/.*\.coreimg.*\.(?i:jpe?g|png|gif|svg)$">
        Header set Cache-Control "max-age=2592000,stale-while-revalidate=43200,stale-if-error=43200,public,immutable" "expr=%{REQUEST_STATUS} < 400"
        Header set Age 0
     </LocationMatch>
     ```

   * DAM에서 변경 가능한 리소스(예: 이미지 및 비디오)를 24시간 동안 캐시하고 12시간 후 백그라운드 새로 고침을 통해 MISS를 방지할 수 있습니다.

     ```
     <LocationMatch "^/content/dam/.*\.(?i:jpe?g|gif|js|mov|mp4|png|svg|txt|zip|ico|webp|pdf)$">
        Header set Cache-Control "max-age=43200,stale-while-revalidate=43200,stale-if-error=43200" "expr=%{REQUEST_STATUS} < 400"
        Header set Age 0
     </LocationMatch>
     ```

### CDN 캐시 적중률 분석 중 {#analyze-chr}

다음을 참조하십시오. [캐시 적중률 분석 자습서](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/caching/cdn-cache-hit-ratio-analysis.html) 대시보드를 사용하여 CDN 로그를 다운로드하고 사이트의 캐시 해시 비율을 분석하는 방법에 대한 정보입니다.

### HEAD 요청 동작 {#request-behavior}

Adobe CDN에서 다음과 같은 리소스에 대한 HEAD 요청을 받는 경우 **아님** 캐시되면 요청이 변환되어 Dispatcher 및/또는 AEM 인스턴스에 의해 GET 요청으로 수신됩니다. 응답을 캐시할 수 있는 경우 후속 HEAD 요청이 CDN에서 제공됩니다. 응답을 캐시할 수 없는 경우 후속 HEAD 요청은 다음에 의존하는 시간 동안 Dispatcher 또는 AEM 인스턴스 또는 둘 다에 전달됩니다. `Cache-Control` TTL

### 마케팅 캠페인 매개변수 {#marketing-parameters}

웹 사이트 URL에는 캠페인의 성공을 추적하는 데 사용되는 마케팅 캠페인 매개 변수가 자주 포함됩니다.

2023년 10월 이후에 생성된 환경의 경우, CDN은 더 나은 캐시 요청을 위해 일반적인 마케팅 관련 쿼리 매개 변수, 특히 다음 정규 표현식 패턴과 일치하는 매개 변수를 제거합니다.

```
^(utm_.*|gclid|gdftrk|_ga|mc_.*|trk_.*|dm_i|_ke|sc_.*|fbclid)$
```

이 동작을 비활성화하려면 지원 티켓을 제출하십시오.

2023년 10월 이전에 생성된 환경의 경우 Dispatcher 구성을 `ignoreUrlParams` 다음으로 속성: [여기에 문서화됨](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html#ignoring-url-parameters).

마케팅 매개 변수를 무시할 수 있는 방법에는 두 가지가 있습니다. (첫 번째 플러그인이 쿼리 매개 변수를 통해 캐시 무효화를 무시하는 것이 좋습니다.)

1. 모든 매개 변수를 무시하고 사용된 매개 변수를 선택적으로 허용합니다.
다음 예에서만 `page` 및 `product` 매개 변수는 무시되지 않으며 요청은 게시자에게 전달됩니다.

```
/ignoreUrlParams {
   /0001 { /glob "*" /type "allow" }
   /0002 { /glob "page" /type "deny" }
   /0003 { /glob "product" /type "deny" }
}
```

1. 마케팅 매개 변수를 제외한 모든 매개 변수를 허용합니다. 파일 [marketing_query_parameters.any](https://github.com/adobe/aem-project-archetype/blob/develop/src/main/archetype/dispatcher.cloud/src/conf.dispatcher.d/cache/marketing_query_parameters.any) 는 무시할 일반적으로 사용되는 마케팅 매개 변수의 목록을 정의합니다. Adobe은 이 파일을 업데이트하지 않습니다. 사용자가 마케팅 공급자에 따라 확장할 수 있습니다.

```
/ignoreUrlParams {
   /0001 { /glob "*" /type "deny" }
   $include "../cache/marketing_query_parameters.any"
}
```


## 디스패처 캐시 무효화 {#disp}

일반적으로 Dispatcher 캐시를 무효화할 필요는 없습니다. 대신 콘텐츠가 다시 게시될 때 Dispatcher가 캐시를 새로 고치고 CDN이 캐시 만료 헤더를 준수하도록 해야 합니다.

### 활성화/비활성화 중 Dispatcher 캐시 무효화 {#cache-activation-deactivation}

이전 버전의 AEM과 마찬가지로 페이지를 게시하거나 게시를 취소하면 Dispatcher 캐시에서 콘텐츠가 지워집니다. 캐싱 문제가 의심되는 경우 해당 페이지를 다시 게시하고 와 일치하는 가상 호스트를 사용할 수 있는지 확인해야 합니다. `ServerAlias` localhost: Dispatcher 캐시 무효화에 필요합니다.

>[!NOTE]
>적절한 Dispatcher 무효화를 위해 &quot;127.0.0.1&quot;, &quot;localhost&quot;, &quot;\*.local&quot;, &quot;\*.adobeaemcloud.com&quot; 및 &quot;\*.adobeaemcloud.net&quot;의 요청이 모두 일치하고 vhost 구성에서 처리되어 요청이 제공될 수 있는지 확인하십시오. 참조의 패턴에 따라 catch-all vhost 구성에서 &quot;*&quot;를 전역 일치시켜 이 작업을 수행할 수 있습니다 [AEM Archetype](https://github.com/adobe/aem-project-archetype/blob/develop/src/main/archetype/dispatcher.cloud/src/conf.d/available_vhosts/default.vhost). 또는 vhost 중 하나에서 이전에 언급한 목록을 catch했는지 확인할 수 있습니다.

게시 인스턴스는 작성자로부터 페이지 또는 에셋의 새 버전을 수신하면 플러시 에이전트를 사용하여 해당 Dispatcher에서 적절한 경로를 무효화합니다. 업데이트된 경로는 상위 경로와 함께 Dispatcher 캐시에서 최대 수준까지 제거됩니다(다음을 사용하여 이 수준을 구성할 수 있음). [statfileslevel](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html#invalidating-files-by-folder-level)).

## 디스패처 캐시의 명시적 무효화 {#explicit-invalidation}

Adobe은 표준 캐시 헤더를 사용하여 콘텐츠 전달 수명 주기를 제어할 것을 권장합니다. 그러나 필요한 경우 Dispatcher에서 직접 콘텐츠를 무효화할 수 있습니다.

다음 목록에는 캐시를 명시적으로 무효화할 수 있는 시나리오가 포함되어 있습니다(선택적으로 무효화 완료를 수신하는 동안).

* 경험 조각 또는 콘텐츠 조각과 같은 콘텐츠를 게시한 후 해당 요소를 참조하는 게시된 콘텐츠 및 캐시된 콘텐츠를 무효화합니다.
* 참조된 페이지가 무효화되면 외부 시스템에 알립니다.

캐시를 명시적으로 무효화하는 방법에는 두 가지가 있습니다.

* 기본 접근 방식은 작성자의 Sling Content Distribution (SCD)을 사용하는 것입니다.
* 다른 방법은 복제 API를 사용하여 게시 Dispatcher 플러시 복제 에이전트를 호출하는 것입니다.

접근법들은 계층 가용성, 이벤트들을 중복 제거하는 기능 및 이벤트 처리 보장 측면에서 상이하다. 아래 표에는 다음 옵션이 요약되어 있습니다.

<table style="table-layout:auto">
 <tbody>
  <tr>
    <th>해당 사항 없음</th>
    <th>계층 가용성</th>
    <th>중복 제거 </th>
    <th>보증 </th>
    <th>작업 </th>
    <th>영향 </th>
    <th>설명 </th>
  </tr>  
  <tr>
    <td>Sling 콘텐츠 배포(SCD) API</td>
    <td>작성자</td>
    <td>검색 API를 사용하거나 <a href="https://github.com/apache/sling-org-apache-sling-distribution-journal/blob/e18f2bd36e8b43814520e87bd4999d3ca77ce8ca/src/main/java/org/apache/sling/distribution/journal/impl/publisher/DistributedEventNotifierManager.java#L146-L149">중복 제거 모드</a>.</td>
    <td>한 번만이라도</td>
    <td>
     <ol>
       <li>추가</li>
       <li>삭제</li>
       <li>무효화</li>
     </ol>
     </td>
    <td>
     <ol>
       <li>계층 구조/통계 수준</li>
       <li>계층 구조/통계 수준</li>
       <li>레벨 리소스 전용</li>
     </ol>
     </td>
    <td>
     <ol>
       <li>콘텐츠를 게시하고 캐시를 무효화합니다.</li>
       <li>콘텐츠를 제거하고 캐시를 무효화합니다.</li>
       <li>게시하지 않고 콘텐츠를 무효화합니다.</li>
     </ol>
     </td>
  </tr>
  <tr>
    <td>복제 API</td>
    <td>게시</td>
    <td>그럴 수 없습니다. 모든 게시 인스턴스에서 이벤트가 발생했습니다.</td>
    <td>최선의 노력.</td>
    <td>
     <ol>
       <li>활성화</li>
       <li>비활성화</li>
       <li>삭제</li>
     </ol>
     </td>
    <td>
     <ol>
       <li>계층 구조/통계 수준</li>
       <li>계층 구조/통계 수준</li>
       <li>계층 구조/통계 수준</li>
     </ol>
     </td>
    <td>
     <ol>
       <li>콘텐츠를 게시하고 캐시를 무효화합니다.</li>
       <li>작성자/Publish 계층에서 - 콘텐츠를 제거하고 캐시를 무효화합니다.</li>
       <li><p><strong>작성자 계층에서</strong> - 콘텐츠를 제거하고 캐시를 무효화합니다(Publish 에이전트의 AEM 작성자 계층에서 트리거된 경우).</p>
           <p><strong>Publish 계층에서</strong> - 캐시만 무효화합니다( 플러시 또는 리소스 전용 플러시 에이전트의 AEM Publish 계층에서 트리거된 경우).</p>
       </li>
     </ol>
     </td>
  </tr>
  </tbody>
</table>

캐시 무효화와 직접 관련된 두 가지 작업은 Sling SCD(콘텐츠 배포) API 무효화 및 복제 API 비활성화입니다.

또한 테이블에서 다음을 관찰할 수 있습니다.

* SCD API는 정확한 지식이 필요한 외부 시스템과 동기화하는 등 모든 이벤트가 보장되어야 할 때 필요합니다. 무효화 호출 시 게시 계층 업스케일링 이벤트가 있는 경우, 각 새 게시가 무효화를 처리할 때 추가 이벤트가 발생합니다.

* 복제 API를 사용하는 것은 일반적인 사용 사례가 아니지만 캐시를 무효화하는 트리거가 작성자 계층이 아닌 게시 계층에서 온 경우 사용할 수 있습니다. 이 방법은 Dispatcher TTL이 구성된 경우 유용할 수 있습니다.

결론적으로 Dispatcher 캐시를 무효화하려는 경우 권장 옵션은 작성자의 SCD API 무효화 작업을 사용하는 것입니다. 또한 이벤트를 수신하여 추가 다운스트림 작업을 트리거할 수도 있습니다.

### Sling 콘텐츠 배포(SCD) {#sling-distribution}

>[!NOTE]
>아래 지침을 사용하는 경우 로컬이 아닌 AEM Cloud Service 개발 환경에서 사용자 지정 코드를 테스트합니다.

작성자의 SCD 작업을 사용할 때 구현 패턴은 다음과 같습니다.

1. 작성자에서 사용자 지정 코드를 작성하여 sling 콘텐츠 배포를 호출합니다 [API](https://sling.apache.org/documentation/bundles/content-distribution.html), 경로 목록과 함께 무효화 작업을 전달합니다.

```
@Reference
private Distributor distributor;

ResourceResolver resolver = ...; // the resource resolver used for authorizing the request
String agentName = "publish";    // the name of the agent used to distribute the request

String pathToInvalidate = "/content/to/invalidate";
DistributionRequest distributionRequest = new SimpleDistributionRequest(DistributionRequestType.INVALIDATE, false, pathToInvalidate);
distributor.distribute(agentName, resolver, distributionRequest);
```

* (선택 사항) 모든 Dispatcher 인스턴스에 대해 무효화되는 리소스를 반영하는 이벤트를 수신합니다.


```
package org.apache.sling.distribution.journal.shared;

import org.apache.sling.discovery.DiscoveryService;
import org.apache.sling.distribution.journal.impl.event.DistributionEvent;
import org.osgi.service.component.annotations.Component;
import org.osgi.service.component.annotations.Reference;
import org.osgi.service.event.Event;
import org.osgi.service.event.EventHandler;
import org.slf4j.Logger;
import org.slf4j.LoggerFactory;

import static org.apache.sling.distribution.DistributionRequestType.INVALIDATE;
import static org.apache.sling.distribution.event.DistributionEventProperties.DISTRIBUTION_PATHS;
import static org.apache.sling.distribution.event.DistributionEventProperties.DISTRIBUTION_TYPE;
import static org.apache.sling.distribution.event.DistributionEventTopics.AGENT_PACKAGE_DISTRIBUTED;
import static org.osgi.service.event.EventConstants.EVENT_TOPIC;

@Component(immediate = true, service = EventHandler.class, property = {
        EVENT_TOPIC + "=" + AGENT_PACKAGE_DISTRIBUTED
})
public class InvalidatedHandler implements EventHandler {
    private static final Logger LOG = LoggerFactory.getLogger(InvalidatedHandler.class);

    @Reference
    private DiscoveryService discoveryService;

    @Override
    public void handleEvent(Event event) {

        String distributionType = (String) event.getProperty(DISTRIBUTION_TYPE);

        if (INVALIDATE.name().equals(distributionType)) {
            boolean isLeader = discoveryService.getTopology().getLocalInstance().isLeader();
            // process the OSGi event on the leader author instance
            if (isLeader) {
                String[] paths = (String[]) event.getProperty(DISTRIBUTION_PATHS);
                String packageId = (String) event.getProperty(DistributionEvent.PACKAGE_ID);
                invalidated(paths, packageId);
            }
        }
    }

    private void invalidated(String[] paths, String packageId) {
        // custom logic
        LOG.info("Successfully applied package with id {}, paths {}", packageId, paths);
    }
}
```

<!-- Optionally, instead of using the isLeader approach, one could add an OSGi configuration for the PID org.apache.sling.distribution.journal.impl.publisher.DistributedEventNotifierManager and property deduplicateEvent=true. But we'll stick with just one strategy and not mention it (double-check this).**review this**-->

* (선택 사항) `invalidated(String[] paths, String packageId)` 위의 메서드를 사용합니다.

>[!NOTE]
>
>Dispatcher가 무효화되면 Adobe CDN이 플러시되지 않습니다. Adobe 관리 CDN은 TTL을 준수하므로 플러시할 필요가 없습니다.

### 복제 API {#replication-api}

다음은 복제 API 비활성화 작업을 사용할 때의 구현 패턴입니다.

1. 게시 계층에서 복제 API를 호출하여 게시 Dispatcher 플러시 복제 에이전트를 트리거합니다.

플러시 에이전트 끝점은 구성할 수 없지만 플러시 에이전트와 함께 실행되는 게시 서비스와 일치하는 Dispatcher를 가리키도록 사전 구성되어 있습니다.

플러시 에이전트는 일반적으로 OSGi 이벤트 또는 워크플로를 기반으로 하는 사용자 지정 코드에 의해 트리거될 수 있습니다.

```
String[] paths = …
ReplicationOptions options = new ReplicationOptions();
options.setSynchronous(true);
options.setFilter( new AgentFilter {
  public boolean isIncluded (Agent agent) {
   return agent.getId().equals("flush");
  }
});

Replicator.replicate (session,ReplicationActionType.DELETE,paths, options);
```

<!-- In general, it will not be necessary to manually invalidate content in the dispatcher, but it is possible if needed.

>[!NOTE]
>Prior to AEM as a Cloud Service, there were two ways of invalidating the dispatcher cache.
>
>1. Invoke the replication agent, specifying the publish dispatcher flush agent
>2. Directly calling the `invalidate.cache` API (for example, `POST /dispatcher/invalidate.cache`)
>
>The dispatcher's `invalidate.cache` API approach will no longer be supported since it addresses only a specific dispatcher node. AEM as a Cloud Service operates at the service level, not the individual node level and so the invalidation instructions in the [Invalidating Cached Pages From AEM](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/page-invalidate.html) page are not longer valid for AEM as a Cloud Service.

The replication flush agent should be used. This can be done using the [Replication API](https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/replication/Replicator.html). The flush agent endpoint is not configurable but pre-configured to point to the dispatcher, matched with the publish service running the flush agent. The flush agent can typically be triggered by OSGi events or workflows.

<!-- Need to find a new link and/or example -->
<!-- 
and for an example of flushing the cache, see the [API example page](https://helpx.adobe.com/experience-manager/using/aem64_replication_api.html) (specifically the `CustomStep` example issuing a replication action of type ACTIVATE to all available agents). 

The diagram presented below illustrates this.

![CDN](assets/cdnd.png "CDN")

If there is a concern that the dispatcher cache is not clearing, contact [customer support](https://helpx.adobe.com/support.ec.html) who can flush the dispatcher cache if necessary.

The Adobe-managed CDN respects TTLs and thus there is no need fo it to be flushed. If an issue is suspected, [contact customer support](https://helpx.adobe.com/support.ec.html) support who can flush an Adobe-managed CDN cache as necessary. -->

## 클라이언트 측 라이브러리 및 버전 일관성 {#content-consistency}

페이지는 HTML, JavaScript, CSS 및 이미지로 구성됩니다. 고객은 다음을 사용하는 것이 좋습니다 [클라이언트측 라이브러리(clientlibs) 프레임워크](/help/implementing/developing/introduction/clientlibs.md) javascript 및 CSS 리소스를 HTML 페이지로 가져오려면 JS 라이브러리 간의 종속성을 고려해야 합니다.

clientlibs 프레임워크는 자동 버전 관리를 제공합니다. 즉, 개발자는 소스 제어에서 JS 라이브러리에 대한 변경 사항을 체크인할 수 있고 고객이 릴리스를 푸시할 때 최신 버전을 사용할 수 있습니다. 이 워크플로가 없으면 개발자는 라이브러리의 새 버전에 대한 참조를 사용하여 HTML을 수동으로 변경해야 합니다. 이는 동일한 라이브러리가 많은 HTML 템플릿을 공유하는 경우 특히 문제가 됩니다.

라이브러리의 새 버전이 프로덕션에 릴리스되면 참조 HTML 페이지가 업데이트된 라이브러리 버전에 대한 새 링크로 업데이트됩니다. 지정된 HTML 페이지에 대한 브라우저 캐시가 만료되면 이전 라이브러리가 브라우저 캐시에서 로드될 염려가 없습니다. 이유는 AEM에서 새로 고친 페이지 가 이제 라이브러리의 새 버전을 참조하도록 보장되기 때문입니다. 즉, 새로 고친 HTML 페이지에는 모든 최신 라이브러리 버전이 포함됩니다.

이 기능의 메커니즘은 클라이언트 라이브러리 링크에 추가되는 직렬화된 해시입니다. 브라우저가 CSS/JS를 캐시할 수 있는 고유한 버전 URL을 보장합니다. 직렬화된 해시는 클라이언트 라이브러리의 내용이 변경될 때만 업데이트됩니다. 즉, 새 배포가 있더라도 관련되지 않은 업데이트가 발생하는 경우(즉, 클라이언트 라이브러리의 기본 css/js가 변경되지 않는 경우) 참조는 동일하게 유지됩니다. 결과적으로 브라우저 캐시의 중단을 줄입니다.

### 클라이언트측 라이브러리의 Longcache 버전 활성화 - AEM as a Cloud Service SDK 빠른 시작 {#enabling-longcache}

기본 clientlib은 다음 예제와 같이 HTML 페이지에 포함됩니다.

```
<link rel="stylesheet" href="/etc.clientlibs/wkndapp/clientlibs/clientlib-base.css" type="text/css">
```

엄격한 clientlib 버전 관리를 사용하면 장기 해시 키가 선택기로 클라이언트 라이브러리에 추가됩니다. 따라서 clientlib 참조는 다음과 같이 표시됩니다.

```
<link rel="stylesheet" href="/etc.clientlibs/wkndapp/clientlibs/clientlib-base.lc-7c8c5d228445ff48ab49a8e3c865c562-lc.css" type="text/css">
```

모든 AEM as a Cloud Service 환경에서 기본적으로 엄격한 clientlib 버전 관리가 활성화됩니다.

로컬 SDK 빠른 시작에서 엄격한 clientlib 버전 관리를 활성화하려면 다음을 수행하십시오.

1. OSGi 구성 관리자로 이동합니다. `<host>/system/console/configMgr`
1. Adobe Granite HTML 라이브러리 관리자에 대한 OSGi 구성을 찾습니다.
   * 엄격한 버전 관리를 활성화하려면 확인란을 선택합니다.
   * 레이블이 지정된 필드에서 **장기적인 클라이언트측 캐시 키**, / 값을 입력합니다.*;해시
1. 변경 사항을 저장합니다. AEMas a Cloud Service 는 개발, 스테이지 및 프로덕션 환경에서 이 구성을 자동으로 활성화하므로 소스 제어에 이 구성을 저장할 필요가 없습니다.
1. 클라이언트 라이브러리의 내용이 변경될 때마다 새 해시 키가 생성되고 HTML 참조가 업데이트됩니다.
