---
title: CDN에서 트래픽 구성
description: 구성 파일에서 규칙 및 필터를 선언하고 Cloud Manager 구성 파이프라인을 사용하여 CDN에 배포하여 CDN 트래픽을 구성하는 방법에 대해 알아봅니다.
feature: Dispatcher
exl-id: e0b3dc34-170a-47ec-8607-d3b351a8658e
role: Admin
source-git-commit: ab855192e4b60b25284b19cc0e3a8e9da5a7409c
workflow-type: tm+mt
source-wordcount: '1508'
ht-degree: 1%

---


# CDN에서 트래픽 구성 {#cdn-configuring-cloud}

AEM as a Cloud Service에서는 수신 요청 또는 발신 응답의 특성을 수정하는 [Adobe 관리 CDN](/help/implementing/dispatcher/cdn.md#aem-managed-cdn) 계층에서 구성할 수 있는 기능 컬렉션을 제공합니다. 이 페이지에 자세히 설명된 다음 규칙은 다음 동작을 달성하도록 선언할 수 있습니다.

* [요청 변환](#request-transformations) - 헤더, 경로 및 매개 변수를 포함하여 들어오는 요청의 측면을 수정합니다.
* [응답 변환](#response-transformations) - 클라이언트로 돌아가는 중인 헤더를 수정합니다(예: 웹 브라우저).
* [서버측 리디렉션](#server-side-redirectors) - 브라우저 리디렉션을 트리거합니다.
* [원본 선택기](#origin-selectors) - 다른 원본 백엔드에 대한 프록시입니다.

또한 CDN에서 구성할 수 있는 것은 CDN에서 허용하거나 거부하는 트래픽을 제어하는 트래픽 필터 규칙 (WAF 포함)입니다. 이 기능은 이미 릴리스되었으며 자세한 내용은 [WAF 규칙을 포함한 트래픽 필터 규칙](/help/security/traffic-filter-rules-including-waf.md) 페이지에서 확인할 수 있습니다.

또한 CDN이 해당 원본에 연결할 수 없는 경우 자체 호스팅된 사용자 지정 오류 페이지를 참조하는 규칙을 작성할 수 있습니다(그런 다음 렌더링됨). [CDN 오류 페이지 구성](/help/implementing/dispatcher/cdn-error-pages.md) 문서를 읽고 이에 대해 자세히 알아보십시오.

소스 제어의 구성 파일에서 선언된 이러한 모든 규칙은 Cloud Manager [구성 파이프라인](/help/operations/config-pipeline.md)을 사용하여 배포됩니다. 구성 파일의 누적 크기는 트래픽 필터 규칙을 포함하여 100KB를 초과할 수 없습니다.

## 평가 순서 {#order-of-evaluation}

기능적으로 앞에서 언급한 다양한 기능들은 다음 순서로 평가됩니다.

![평가 순서](/help/implementing/dispatcher/assets/order.png)

## 설정 {#initial-setup}

CDN에서 트래픽을 구성하려면 먼저 다음을 수행해야 합니다.

1. 아래 섹션에서 다양한 구성 조각을 참조하여 이름이 `cdn.yaml`이거나 유사한 파일을 만드십시오.

   모든 코드 조각에는 이러한 공통 속성이 있으며, 이는 [Config Pipeline](/help/operations/config-pipeline.md#common-syntax)에 설명되어 있습니다. `kind` 속성 값은 *CDN*&#x200B;이고 `version` 속성은 *1*(으)로 설정해야 합니다.

   ```
   kind: "CDN"
   version: "1"
   metadata:
     envTypes: ["dev"]
   ```

1. [Config Pipeline](/help/operations/config-pipeline.md#folder-structure)에 설명된 대로 파일을 *config* 또는 이와 유사한 최상위 폴더 아래에 위치시킵니다.

1. [구성 파이프라인](/help/operations/config-pipeline.md#managing-in-cloud-manager)에 설명된 대로 Cloud Manager에서 구성 파이프라인을 만듭니다.

1. 구성 배포.

## 규칙 구문 {#configuration-syntax}

아래 섹션의 규칙 유형은 일반적인 구문을 공유합니다.

이름, 조건부 &quot;when 절&quot; 및 작업에서 규칙을 참조합니다.

&quot;when&quot; 절은 도메인, 경로, 쿼리 문자열, 헤더 및 쿠키를 포함한 속성을 기반으로 규칙을 평가할지 여부를 결정합니다. 구문은 규칙 유형에서 동일합니다. 자세한 내용은 트래픽 필터 규칙 문서의 [조건 구조 섹션](/help/security/traffic-filter-rules-including-waf.md#condition-structure)을 참조하십시오.

작업 노드의 세부 사항은 규칙 유형에 따라 다르며 아래 개별 섹션에 설명되어 있습니다.

구성 규칙에서 환경 변수로 정의된 암호를 참조할 수 있습니다([구성 암호](/help/implementing/dispatcher/cdn-credentials-authentication.md) 참조).

## 변형 요청 {#request-transformations}

요청 변환 규칙을 사용하면 수신 요청을 수정할 수 있습니다. 규칙은 정규 표현식을 비롯한 다양한 일치 조건을 기반으로 경로, 쿼리 매개 변수 및 헤더(쿠키 포함)의 설정, 설정 해제 및 변경을 지원합니다. 변수를 설정할 수도 있습니다. 그런 다음 평가 시퀀스에서 나중에 참조할 수 있습니다.

사용 사례는 다양하며 애플리케이션 간소화를 위한 URL 재작성 또는 기존 URL 매핑을 포함합니다.

앞에서 언급했듯이 구성 파일의 크기가 제한되어 있으므로 요구 사항이 더 큰 조직은 `apache/dispatcher` 계층에서 규칙을 정의해야 합니다.

구성 예:

```
kind: "CDN"
version: "1"
metadata:
  envTypes: ["dev", "stage", "prod"]
data:
  requestTransformations:
    removeMarketingParams: true
    rules:
      - name: set-header-rule
        when:
          reqProperty: path
          like: /set-header
        actions:
          - type: set
            reqHeader: x-some-header
            value: some value
      - name: set-header-with-reqproperty-rule
        when:
          reqProperty: path
          like: /set-header
        actions:
          - type: set
            reqHeader: x-some-header
            value: {reqProperty: path}
      - name: unset-header-rule
        when:
          reqProperty: path
          like: /unset-header
        actions:
          - type: unset
            reqHeader: x-some-header
      - name: unset-matching-query-params-rule
        when:
          reqProperty: path
          equals: /unset-matching-query-params
        actions:
          - type: unset
            queryParamMatch: ^removeMe_.*$
      - name: unset-all-query-params-except-exact-two-rule
        when:
          reqProperty: path
          equals: /unset-all-query-params-except-exact-two
        actions:
          - type: unset
            queryParamMatch: ^(?!leaveMe$|leaveMeToo$).*$
      - name: multi-action
        when:
          reqProperty: path
          like: /multi-action
        actions:
          - type: set
            reqHeader: x-header1
            value: body set by transformation rule
          - type: set
            reqHeader: x-header2
            value: '201'
      - name: replace-html
        when:
          reqProperty: path
          like: /mypath
        actions:
          - type: transform
            reqProperty: path
            op: replace
            match: \.html$
            replacement: ""
      - name: log-on-request
        when: "*"
        actions:
          - type: set
            logProperty: forwarded_host
            value:
              reqHeader: x-forwarded-host
```

**작업**

사용 가능한 작업은 아래 표에 설명되어 있습니다.

| 이름 | 속성 | 의미 |
|-----------|--------------------------|-------------|
| **설정** | reqProperty, 값 | 지정된 요청 매개 변수를 설정합니다(&quot;path&quot; 속성만 지원됨). |
|     | reqHeader, 값 | 지정된 요청 헤더를 지정된 값으로 설정합니다. |
|     | queryParam, value | 지정된 쿼리 매개 변수를 지정된 값으로 설정합니다. |
|     | reqCookie, 값 | 지정된 요청 쿠키를 지정된 값으로 설정합니다. |
|     | logProperty, value | 지정된 CDN 로그 속성을 지정된 값으로 설정합니다. |
|     | var, 값 | 지정된 변수를 지정된 값으로 설정합니다. |
| **설정 해제** | reqProperty | 지정된 요청 매개 변수 제거(&quot;path&quot; 속성만 지원됨) |
|     | reqHeader, 값 | 지정된 요청 헤더를 제거합니다. |
|     | queryParam, value | 지정된 쿼리 매개 변수를 제거합니다. |
|     | reqCookie, 값 | 지정된 쿠키를 제거합니다. |
|     | logProperty, value | 지정된 CDN 로그 속성을 제거합니다. |
|     | var | 지정된 변수를 제거합니다. |
|     | queryParammatch | 지정된 정규 표현식과 일치하는 모든 쿼리 매개 변수를 제거합니다. |
|     | queryParamDoesNotMatch | 지정된 정규 표현식과 일치하지 않는 모든 쿼리 매개 변수를 제거합니다. |
| **변환** | op:replace, (reqProperty 또는 reqHeader 또는 queryParam 또는 reqCookie 또는 var), 일치, 대체 | 요청 매개 변수(&quot;path&quot; 속성만 지원됨), 요청 헤더 또는 쿼리 매개 변수, 쿠키 또는 변수의 일부를 새 값으로 바꿉니다. |
|              | op:tolower, (reqProperty 또는 reqHeader 또는 queryParam 또는 reqCookie 또는 var) | 요청 매개 변수(&quot;path&quot; 속성만 지원됨) 또는 요청 헤더, 쿼리 매개 변수, 쿠키 또는 변수를 해당 소문자 값으로 설정합니다. |

아래 그림과 같이 작업을 바꾸면 캡처 그룹이 지원됩니다.

```
      - name: extract-country-code-from-path
        when:
          reqProperty: path
          matches: ^/([a-zA-Z]{2})(/.*|$)
        actions:
          - type: set
            var: country-code
            value:
              reqProperty: path
          - type: transform
            var: country-code
            op: replace
            match: ^/([a-zA-Z]{2})(/.*|$)
            replacement: \1
      - name: replace-jpg-with-jpeg
        when:
          reqProperty: path
          like: /mypath
        actions:
          - type: transform
            reqProperty: path
            op: replace
            match: (.*)(\.jpg)$
            replacement: "\1\.jpeg"
```

작업은 함께 연결될 수 있습니다. 예:

```
actions:
    - type: transform
      reqProperty: path
      op: replace
      match: \.html$
      replacement: ""
    - type: transform
      reqProperty: path
      op: tolower
```

### 변수 {#variables}

요청 변환 중에 변수를 설정한 다음 평가 시퀀스에서 나중에 참조할 수 있습니다. 자세한 내용은 [평가 순서](#order-of-evaluation) 다이어그램을 참조하십시오.

구성 예:

```
kind: "CDN"
version: "1"
metadata:
  envTypes: ["prod", "dev"]
data:
  requestTransformations:
    rules:
      - name: set-variable-rule
        when:
          reqProperty: path
          equals: /set-variable
        actions:
          - type: set
            var: some_var_name
            value: some_value

  responseTransformations:
    rules:
      - name: set-response-header-while-variable
        when:
          var: some_var_name
          equals: some_value
        actions:
          - type: set
            respHeader: x-some-header
            value: some header value
```

### 로그 속성 {#logproperty}

요청 및 응답 변환을 사용하여 CDN 로그에 고유한 로그 속성을 추가할 수 있습니다.

구성 예:

```
requestTransformations:
  rules:
    - name: log-on-request
      when: "*"
      actions:
        - type: set
          logProperty: forwarded_host
          value:
            reqHeader: x-forwarded-host
responseTransformations:
  rules:
    - name: log-on-response
      when: '*'
      actions:
        - type: set
          logProperty: cache_control
          value:
            respHeader: cache-control
```

로그 예:

```
{
"timestamp": "2025-03-26T09:20:01+0000",
"ttfb": 19,
"cli_ip": "147.160.230.112",
"cli_country": "CH",
"rid": "974e67f6",
"req_ua": "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/605.1.15 (KHTML, like Gecko) Version/14.0.3 Safari/605.1.15",
"host": "example.com",
"url": "/content/hello.png",
"method": "GET",
"res_ctype": "image/png",
"cache": "PASS",
"status": 200,
"res_age": 0,
"pop": "PAR",
"rules": "",
"forwarded_host": "example.com",
"cache_control": "max-age=300"
}
```

## 응답 변환 {#response-transformations}

응답 변환 규칙을 사용하면 CDN의 발신 응답에 대한 헤더, 쿠키 및 상태를 설정하고 설정이 해제될 수 있습니다. 또한 요청 변환 규칙에 이전에 설정된 변수를 참조하려면 위의 예를 참조하십시오.

구성 예:

```
kind: "CDN"
version: "1"
metadata:
  envTypes: ["prod", "dev"]
data:
  responseTransformations:
    rules:
      - name: set-response-header-rule
        when:
          reqProperty: path
          like: /set-response-header
        actions:
          - type: set
            value: value-set-by-resp-rule
            respHeader: x-resp-header
      - name: unset-response-header-rule
        when:
          reqProperty: path
          like: /unset-response-header
        actions:
          - type: unset
            respHeader: x-header1
      - name: multi-action-response-header-rule
        when:
          reqProperty: path
          like: /multi-action-response-header
        actions:
          - type: set
            respHeader: x-resp-header-1
            value: value-set-by-resp-rule-1
          - type: set
            respHeader: x-resp-header-2
            value: value-set-by-resp-rule-2
      - name: status-code-rule
        when:
          reqProperty: path
          like: status-code
        actions:
          - type: set
            respProperty: status
            value: '410'
      - name: set-response-cookie-with-attributes-as-object
        when: '*'
        actions:
          - type: set
            respCookie: first-name
            value: first-value
            attributes:
              expires: '2025-08-29T10:00:00'
              domain: example.com
              path: /some-path
              secure: true
              httpOnly: true
              extension: ANYTHING
      - name: unset-response-cookie
        when: '*'
        actions:
          - type: unset
            respCookie: third-name
```

**작업**

사용 가능한 작업은 아래 표에 설명되어 있습니다.

| 이름 | 속성 | 의미 |
|-----------|--------------------------|-------------|
| **설정** | respProperty, 값 | 응답 속성을 설정합니다. 상태 코드를 설정하기 위해 속성 &quot;status&quot;만 지원합니다. |
|     | respHeader, 값 | 지정된 응답 헤더를 지정된 값으로 설정합니다. |
|     | respCookie, 속성(만료, 도메인, 경로, 보안, httpOnly, 확장), 값 | 특정 속성을 가진 지정된 요청 쿠키를 지정된 값으로 설정합니다. |
|     | logProperty, value | 지정된 CDN 로그 속성을 지정된 값으로 설정합니다. |
|     | var, 값 | 지정된 변수를 지정된 값으로 설정합니다. |
| **설정 해제** | respHeader | 응답에서 지정된 헤더를 제거합니다. |
|     | respCookie, 값 | 지정된 쿠키를 제거합니다. |
|     | logProperty, value | 지정된 CDN 로그 속성을 제거합니다. |
|     | var | 지정된 변수를 제거합니다. |

## 원본 선택기 {#origin-selectors}

AEM CDN을 활용하여 Adobe이 아닌 애플리케이션을 비롯한 다양한 백엔드로 트래픽을 라우팅할 수 있습니다(경로당 또는 하위 도메인별로).

구성 예:

```
kind: "CDN"
version: "1"
metadata:
  envTypes: ["dev"]
data:
  originSelectors:
    rules:
      - name: example-com
        when: { reqProperty: path, like: /proxy* }
        action:
          type: selectOrigin
          originName: example-com
          # skipCache: true
    origins:
      - name: example-com
        domain: www.example.com
        # ip: '1.1.1.1'
        # forwardHost: true
        # forwardCookie: true
        # forwardAuthorization: true
        # timeout: 20
```

**작업**

아래 표에 사용 가능한 작업이 설명되어 있습니다.

| 이름 | 속성 | 의미 |
|-----------|--------------------------|-------------|
| **selectOrigin** | originName | 정의된 원본 중 하나의 이름입니다. |
|     | skipCache(선택 사항, 기본값은 false) | 이 규칙과 일치하는 요청에 캐싱을 사용할지 여부를 플래그로 표시합니다. 기본적으로 응답은 응답 캐싱 헤더에 따라 캐시됩니다 (예: Cache-Control 또는 Expires) |

**원본**

원본에 대한 연결은 SSL만 사용하며 포트 443을 사용합니다.

| 속성 | 의미 |
|------------------|--------------------------------------|
| **이름** | &quot;action.originName&quot;에서 참조할 수 있는 이름입니다. |
| **도메인** | 사용자 지정 백엔드에 연결하는 데 사용되는 도메인 이름. 또한 SSL SNI 및 유효성 검사에 사용됩니다. |
| **ip**(선택 사항, 지원되는 iv4 및 ipv6) | 제공된 경우 &quot;도메인&quot; 대신 백엔드에 연결하는 데 사용됩니다. 여전히 &quot;도메인&quot;은 SSL SNI 및 유효성 검사에 사용됩니다. |
| **forwardHost**(선택 사항, 기본값은 false임) | true로 설정하면 클라이언트 요청의 &quot;호스트&quot; 헤더가 백엔드에 전달되고, 그렇지 않으면 &quot;도메인&quot; 값이 &quot;호스트&quot; 헤더에 전달됩니다. |
| **forwardCookie**(선택 사항, 기본값은 false임) | true로 설정하면 클라이언트 요청의 &quot;쿠키&quot; 헤더가 백엔드로 전달되고, 그렇지 않으면 쿠키 헤더가 제거됩니다. |
| **forwardAuthorization**(선택 사항, 기본값은 false임) | true로 설정하면 클라이언트 요청의 &quot;Authorization&quot; 헤더가 백엔드로 전달되고, 그렇지 않으면 Authorization 헤더가 제거됩니다. |
| **시간 초과**(선택 사항, 초 단위, 기본값은 60) | 백엔드 서버가 HTTP 응답 본문의 첫 번째 바이트를 전달할 때까지 CDN이 기다려야 하는 시간(초)입니다. 이 값은 백엔드 서버에 대한 바이트 제한 시간 사이의 값으로도 사용됩니다. |

### Edge Delivery Services에 프록시 설정 {#proxying-to-edge-delivery}

원본 선택기를 사용하여 AEM 게시를 통해 AEM Edge Delivery Services으로 트래픽을 라우팅해야 하는 시나리오가 있습니다.

* 일부 컨텐츠는 AEM Publish에서 관리하는 도메인에 의해 전달되지만, 동일한 도메인의 다른 컨텐츠는 Edge Delivery Services에 의해 전달됩니다
* Edge Delivery Services에서 제공하는 컨텐츠는 트래픽 필터 규칙 또는 요청/응답 변환을 포함하여 구성 파이프라인을 통해 배포된 규칙의 이점을 받습니다

다음은 이를 수행할 수 있는 원본 선택기 규칙의 예입니다.

```
kind: CDN
version: '1'
data:
  originSelectors:
    rules:
      - name: select-edge-delivery-services-origin
        when:
          allOf:
            - reqProperty: tier
              equals: publish
            - reqProperty: domain
              equals: <Production Host>
            - reqProperty: path
              matches: "^(/scripts/.*|/styles/.*|/fonts/.*|/blocks/.*|/icons/.*|.*/media_.*|/favicon.ico)"
        action:
          type: selectOrigin
          originName: aem-live
    origins:
      - name: aem-live
        domain: main--repo--owner.aem.live
```

>[!NOTE]
> Adobe 관리 CDN이 사용되었으므로 Edge Delivery Services [푸시 무효화 설정 설명서](https://www.aem.live/docs/byo-dns#setup-push-invalidation)를 따라 **관리** 모드에서 푸시 무효화를 구성해야 합니다.


## 서버측 리디렉션 {#server-side-redirectors}

301, 302 및 유사한 클라이언트측 리디렉션에 대해 클라이언트측 리디렉션 규칙을 사용할 수 있습니다. 규칙이 일치하는 경우 CDN은 상태 코드 및 메시지(예: HTTP/1.1 301 영구적으로 이동됨)와 위치 헤더 세트를 포함하는 상태 라인으로 응답합니다.

고정 값을 갖는 절대 위치와 상대 위치를 모두 사용할 수 있습니다.

구성 파일의 누적 크기는 트래픽 필터 규칙을 포함하여 100KB를 초과할 수 없습니다.

구성 예:

```
kind: "CDN"
version: "1"
metadata:
  envTypes: ["dev"]
data:
  redirects:
    rules:
      - name: redirect-absolute
        when: { reqProperty: path, equals: "/page.html" }
        action:
          type: redirect
          status: 301
          location: https://example.com/page
      - name: redirect-relative
        when: { reqProperty: path, equals: "/anotherpage.html" }
        action:
          type: redirect
          location: /anotherpage
```

| 이름 | 속성 | 의미 |
|-----------|--------------------------|-------------|
| **리디렉션** | 위치 | &quot;위치&quot; 헤더 값. |
|     | 상태(선택 사항, 기본값은 301) | 리디렉션 메시지에 사용할 HTTP 상태, 기본적으로 301. 허용되는 값은 301, 302, 303, 307, 308입니다. |

리디렉션의 위치는 문자열 리터럴(예: https://www.example.com/page) 또는 다음 구문으로 선택적으로 변환되는 속성(예: path)의 결과일 수 있습니다.

```
redirects:
  rules:
    - name: country-code-redirect
      when: { reqProperty: path, like: "/" }
      action:
        type: redirect
        location:
          reqProperty: clientCountry
          transform:
            - op: replace
              match: '^(.*)$'
              replacement: 'https://www.example.com/\1/home'
            - op: tolower
    - name: www-redirect
      when: { reqProperty: domain, equals: "example.com" }
      action:
        type: redirect
        location:
          reqProperty: url
          transform:
            - op: replace
              match: '^/(.*)$'
              replacement: 'https://www.example.com/\1'
```
