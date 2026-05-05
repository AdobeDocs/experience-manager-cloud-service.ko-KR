---
title: 일반적인 시나리오에 대한 CDN 구성 조각
description: 에지 인증, 리디렉션, 캐시 변동, 트래픽 셰이핑 및 비율 제한을 포함하여 Adobe 관리 CDN 및 고객 관리 CDN 설정에 대한 복사 준비 YAML 패턴입니다.
feature: Dispatcher
role: Admin
source-git-commit: ab43facbd4c34c92878e303acf2fef9cc127e28a
workflow-type: tm+mt
source-wordcount: '434'
ht-degree: 0%

---


# 일반적인 시나리오에 대한 CDN 구성 조각 {#cdn-configuration-snippets}

이 문서에서는 AEM as a Cloud Service에 대한 실용적인 `cdn.yaml` 패턴을 수집합니다. [CDN 트래픽 규칙](/help/implementing/dispatcher/cdn-configuring-traffic.md), [고객 관리 CDN 자격 증명](/help/implementing/dispatcher/cdn-credentials-authentication.md) 및 [WAF을 포함한 트래픽 필터 규칙](/help/security/traffic-filter-rules-including-waf.md)에 대한 기능 설명서와 함께 사용하십시오. Cloud Manager [구성 파이프라인](/help/operations/config-pipeline.md)을 사용하여 코드 조각을 배포합니다.

>[!NOTE]
>
>호스트 이름, 경로, IP 범위, 키 및 임계값을 프로그램과 일치하는 값으로 바꿉니다. 프로모션하기 전에 비프로덕션 환경에서 변경 사항을 테스트합니다.

## 고객 관리 CDN {#customer-managed-cdn}

### 일부 도메인에 대해서만 Edge 키 인증 설정 {#edge-auth-selected-hosts}

문제: [고객 관리 CDN](/help/implementing/dispatcher/cdn.md#point-to-point-cdn)에서는 일부 고객 호스트 이름에 인증을 적용해야 하지만, 게시로 연결되는 다른 호스트 이름은 해당 헤더 없이 사용 가능합니다(예: 롤아웃 중이나 CDN 뒤에 브랜드 도메인이 하나만 있는 경우).

해결 방법: `X-Forwarded-Host`의 첫 번째 호스트 이름이 대상 호스트 이름과 같은 경우에만 `X-AEM-Edge-Key` 인증이 필요합니다(예: `example.com`). 규칙은 `forwardedDomain` 요청 속성을 사용하여 해당 일치를 수행하고 Edge Authenticator에 대해 `authenticate` 작업을 실행합니다. 프로그램의 호스트 이름, 인증자 이름 및 키 자리 표시자를 바꿉니다.

```yaml
kind: "CDN"
version: "1"
data:
  authentication:
    authenticators:
      - name: edge-key-auth
        type: edge
        edgeKey1: ${{CDN_EDGEKEY_1}}
        edgeKey2: ${{CDN_EDGEKEY_2}}
    rules:
      - name: edge-key-auth-rule
        when: { reqProperty: forwardedDomain, equals: "example.com" }
        action:
          type: authenticate
          authenticator: edge-key-auth
```

### VPN IP에서 전송되지 않는 요청에 대해 Edge 키 인증 설정 {#edge-auth-trusted-ips}

문제: BYOCDN에 대해 에지 키 인증을 설정했지만 VPN IP에 대해서만 게시 도메인에 대한 직접 액세스를 허용합니다.

해결 방법: 클라이언트 IP가 VPN IP 목록에 없는 경우에만 X-AEM-Edge-Key 인증 필요

```yaml
kind: "CDN"
version: "1"
data:
  authentication:
    authenticators:
      - name: edge-key-auth
        type: edge
        edgeKey1: ${{CDN_EDGEKEY_1}}
        edgeKey2: ${{CDN_EDGEKEY_2}}
    rules:
      - name: edge-key-auth-rule
        when: { reqProperty: clientIp, notIn: ["10.0.0.1", "11.0.0.0/24", "<other VPN IPs>"] }
        action:
          type: authenticate
          authenticator: edge-key-auth
```

## 리디렉션 {#redirects}

### APEX 도메인에서 wwww로 리디렉션 중 {#apex-to-www}

```yaml
kind: "CDN"
version: "1"
data:
 redirects:
   rules:
     - name: non-www-to-www-redirect
       when:
         reqProperty: domain
         doesNotMatch: '^www\.'
       action:
         type: redirect
         status: 301
         location:
           join:
             format: 'https://www.%s%s'
             args:
               - reqProperty: domain
               - reqProperty: url
```

### 캐시 키 수정 {#cache-key}

CDN은 별도의 &quot;캐시 키&quot; 필드를 노출하지 않습니다. URL이 캐싱에 참여하므로 URL을 변경하여(예: [요청 변환](/help/implementing/dispatcher/cdn-configuring-traffic.md#request-transformations)을 통해 쿼리 매개 변수를 추가) 캐시 항목을 분할할 수 있습니다.

```yaml
kind: "CDN"
version: "1"
data:
  requestTransformations:
    rules:
      - name: set-request-different-cache-curl
        when:
          allOf:
            - reqProperty: tier
              equals: publish
            - reqHeader: user-agent
              matches: curl
        actions:
          - type: set
            queryParam: cache
            value: 'curl'
```

### 정규화된 경로로 리디렉션 {#trailing-slash}

브라우저에서 게시 시 후행 슬래시를 요청하면 영구 리디렉션을 보냅니다(예: `https://www.example.com/path/`에서 `https://www.example.com/path`(으)로).

```yaml
kind: "CDN"
version: "1"
data:
  redirects:
    rules:
      - name: remove-trailing-slash
        when:
          allOf:
            - reqProperty: tier
              equals: publish
            - reqProperty: domain
              equals: www.example.com
            - reqProperty: originalPath
              matches: ^/(.+)/$
        action:
          type: redirect
          status: 301
          location:
            reqProperty: originalPath
            transform:
              - op: replace
                match: ^/(.+)/$
                replacement: https://www.example.com/\1
```

### JSON 쿠키에서 정보 추출 {#json-cookie}

```yaml
kind: "CDN"
version: "1"
data:
  requestTransformations:
    rules:
      - name: options-response
        when: { reqProperty: tier, equals: publish }
        actions:
        - type: set
          reqHeader: x-mycookie-info
          value:
            reqCookie: mycookie
            transform: 
            - 'base64decode'
            - { op: 'replace', match: '"info":\s*"([^"]*)"', replacement: '\1'} 
```

## 원본 간 설정 {#cross-origin}

### CDN의 OPTIONS 요청 제공 {#options-from-cdn}

```yaml
kind: "CDN"
version: "1"
data:
  requestTransformations:
    rules:
      - name: options-response
        when:
          allOf: 
            - { reqProperty: path, like: /mypathi*  }
            - { reqProperty: method, equals: "OPTIONS" }
            - { reqHeader: Origin, equals: "https://example.com" }
        actions:
          - type: respond
            status: 200
            reason: "OK"
            headers:
              content-type: 'text/plain'
              access-control-allow-origin: { reqHeader: Origin }
              access-control-allow-methods: "*"
              access-control-allow-headers: "*"
```

## 트래픽 필터 {#traffic-filters}

### 속도 제한 ASN {#rate-limit-asn}

문제: IP당 속도 제한으로 인해 DDoS(분산 서비스 거부) 패턴이 누락될 수 있음: 각 주소가 임계값 아래에 유지되므로 합법적인 트래픽과 모욕적인 트래픽이 IP 계층에서 동일하게 보입니다.

해결 방법: 자율 시스템 이름(`clientAsName`)별로 요청을 계산하여 동일한 네트워크 이름을 공유하는 호스트를 제한기가 집계하도록 합니다. 이 코드 조각은 모든 요청의 로그 속성에 `clientAsName`을(를) 쓴 다음 해당 값으로 그룹화된 작성자 및 게시의 속도 제한을 적용합니다. 많은 사용자가 하나의 ASN을 공유할 수 있으므로(예: 대규모 ISP 또는 기업 VPN 종료) 제한을 신중하게 조정하고 CDN 로그에서 긍정 오류(false positive)를 모니터링합니다.

```yaml
kind: "CDN"
version: "1"
data:
  requestTransformations:
    rules:
      - name: log-on-request
        when: "*"
        actions:
          - type: set
            logProperty: client_as_name
            value:
              reqProperty: clientAsName
  trafficFilters:
    rules:
    - name: limit-requests-client-as-name
      when:
        reqProperty: tier
        matches: "author|publish"
      rateLimit:
        limit: 60
        window: 10
        penalty: 300
        count: all
        groupBy:
          - reqProperty: clientAsName
      action: block
```
