---
title: 네트워크 연결 테스트
description: 환경에서 네트워킹을 활성화하기 전에 Cloud Manager의 네트워크 연결 테스트를 사용하여 프로그램의 이그레스 경로에서 고급 네트워킹 및 VPN 구성을 확인하십시오.
feature: Security
role: Admin
source-git-commit: b29b3a980a0bc1c619fb23c52acda79fae9bf945
workflow-type: tm+mt
source-wordcount: '2047'
ht-degree: 2%

---


# 네트워크 연결 테스트 {#network-connectivity-test}

**네트워크 연결 테스트**&#x200B;는 환경에서 고급 네트워킹을 활성화하기 전과 라이브로 전환하기 전에 고급 네트워킹 및 VPN 구성을 확인할 수 있는 Cloud Manager 진단 도구입니다. 고급 네트워킹에서 사용할 연결 경로를 통해 내부 또는 개인 끝점을 포함하여 AEM에서 도달해야 하는 호스트 및 포트를 확인할 수 있습니다.

테스트는 작성자 또는 게시 pod가 아니라 프로그램의 고급 네트워킹 설정에 속하는 **이그레스 프록시 인프라**&#x200B;에서 실행됩니다. 고급 네트워킹이 활성 상태일 때 AEM이 사용하는 것과 동일한 아웃바운드 네트워크 경로를 사용합니다. 이 디자인은 **VPN** 시나리오에 특히 유용합니다. DNS 확인, 네트워크 라우팅, 방화벽 규칙 및 개인 또는 온-프레미스 시스템에 대한 서비스 사용 가능 여부를 확인한 후 실행할 수 있습니다.

VPN, 전용 이그레스 IP 또는 유연한 포트 이그레스에 대한 배경에 대해서는 [AEM as a Cloud Service에 대한 고급 네트워킹 구성](/help/security/configuring-advanced-networking.md)을 참조하십시오.

>[!IMPORTANT]
>
>성공적인 연결 테스트는 고급 네트워킹의 네트워크 경로가 대상에 도달할 수 있음을 증명합니다. 필요한 경우 고급 네트워킹 프록시를 사용하도록 애플리케이션 코드를 구성해야 합니다(예: 프록시 관련 환경 변수 및 포트 전달). 코드가 프록시를 무시하는 경우 테스트가 통과하더라도 예상 이그레스 경로의 트래픽이 표시되지 않을 수 있습니다.

## 이 도구 사용 시기 {#when-to-use}

* **고급 네트워킹**&#x200B;이 **프로그램** 수준 및 **이전**&#x200B;에서 만들어진 후 또는 **환경**&#x200B;에서 사용하도록 설정하는 동안.
* 개인 또는 온-프레미스 시스템에 대한 **VPN** 연결을 확인하려면(예: 내부 호스트 이름 또는 개인 IP 주소).
* 서비스가 예상대로 응답하지 않을 때 방화벽 또는 라우팅 문제와 비교하여 DNS 문제를 좁히려면

>[!NOTE]
>
>이 도구는 고급 네트워킹(VPN, 전용 이그레스 IP 또는 유연한 포트 이그레스)을 사용하는 프로그램용입니다. 고급 네트워킹이 없는 표준 AEM 연결에 대한 일반적인 목적의 테스트가 아닙니다.

## 사전 요구 사항 {#prerequisites}

* Cloud Manager 프로그램.
* 프로그램에 대한 고급 네트워킹 인프라가 이미 생성되었습니다([고급 네트워킹 구성](/help/security/configuring-advanced-networking.md) 참조).

## 테스트 실행 방법 {#how-to-run-a-test}

1. [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/)에서 Cloud Manager에 로그인하고 조직과 프로그램을 엽니다.
1. 프로그램의 **환경** 탭을 엽니다. 왼쪽 사이드바에서 **네트워크 인프라**&#x200B;를 선택합니다.

1. **네트워크 인프라** 페이지에서 표에서 인프라를 찾습니다. 행을 선택하여 테스트 환경을 열거나 행 작업 메뉴(![가로 줄임표 행 작업 메뉴에 대한 Adobe Spectrum Small More 아이콘](assets/ellipsis.svg))를 열고 **테스트**&#x200B;를 선택합니다.

   ![네트워크 연결 테스트를 시작하는 데 사용되는 네트워크 인프라 테이블, 인프라 행 및 행 작업 메뉴가 있는 Cloud Manager 프로그램 환경 영역](assets/network-connectivity-test-cloud-manager-open-test-from-infrastructure-list.png)

1. **네트워크 테스트** 대화 상자가 열립니다. **호스트** 및 **포트**&#x200B;을(를) 입력하고 **테스트**&#x200B;를 선택한 다음 결과 영역에서 DNS 확인, 포트 열기, HTTP 연결 및 연결 가능성을 검토하십시오. **클립보드에 복사** 및 최근 테스트 기록과 같은 선택적 작업이 대화 상자에 나타납니다. 각 섹션을 해석하는 방법은 [결과 이해](#understanding-results)를 참조하십시오.

   ![호스트 및 포트 필드가 포함된 Cloud Manager 네트워크 연결 테스트 대화 상자, 테스트 작업, DNS 확인, 포트 열기, HTTP 연결 및 연결 확인 결과](assets/network-connectivity-test-cloud-manager-results-dialog.png)

### 입력 필드 {#input-fields}

| 필드 | 설명 | 예 |
| --- | --- | --- |
| **호스트** | AEM이 도달해야 하는 서비스의 호스트 이름 또는 IP 주소입니다. | `internal-api.example.com`, `10.0.1.50` |
| **포트** | 대상 호스트의 TCP 포트(1-65535). 공통 값은 바로 가기 목록(예: 80, 443, 587, 22)에 나타날 수 있습니다. | `443` |

### 단계 {#test-steps}

1. **호스트** 및 **포트**&#x200B;를 입력하십시오.
1. **테스트**&#x200B;를 선택합니다. 결과는 일반적으로 몇 초 이내에 나타납니다.
1. 선택 사항: **클립보드에 복사**&#x200B;를 사용하여 전체 JSON 결과를 캡처합니다(지원 사례에 유용함).
1. 빠른 재실행을 위해 최근 테스트가 나열될 수 있습니다.

## 결과 이해 {#understanding-results}

이 도구는 여러 차원을 보고합니다. 고급 네트워킹에서 타겟에 연결할 수 있는지 여부와 HTTP 인식 검사가 작동하는 방식을 설명합니다.

### DNS 문제 해결 {#dns-resolution}

| 결과 | 의미 |
| --- | --- |
| `ips: ["10.0.1.50"]` | DNS 확인에 성공했습니다. 고급 네트워킹 구성과 연결된 확인자를 사용하여 나열된 IP 주소로 확인된 호스트 이름입니다. |
| `error: "DNS resolution error: ..."` | DNS 확인 실패. 구성된 DNS 서버가 호스트 이름을 확인할 수 없습니다(잘못된 이름, 확인자에 연결할 수 없음, 레코드 누락 및 유사한 원인). |

>[!NOTE]
>
>호스트 이름 대신 **숫자 IP**&#x200B;을(를) 입력하면 해당 값에 대한 DNS 확인을 건너뛰고 IP가 직접 사용됩니다.

### 포트 열림 {#port-open}

| 결과 | 의미 |
| --- | --- |
| `Yes` / true | TCP 연결 성공 — 포트가 열려 있고 연결을 수락합니다. |
| `No` / false | 포트가 닫혀 있거나 방화벽에 의해 필터링되었거나 호스트에 연결할 수 없습니다. |

### HTTP 연결 {#http-connectivity}

**모든 포트**&#x200B;에서 HTTP/HTTPS 요청을 시도합니다. 이 도구는 항상 먼저 **HTTPS**&#x200B;을(를) 시도한 다음 **HTTP**(으)로 돌아갑니다. 둘 다 작동하지 않는 경우 결과는 읽기 쉬운 짧은 **오류** 메시지에 매핑됩니다(아래 표 참조).

**성공 출력**

| 출력 | 의미 |
| --- | --- |
| `protocol: "https"`, `status_code: 200`, `reason: "200 OK"` | HTTPS 연결에 성공했습니다. |
| `protocol: "http"`, `status_code: 301`, `reason: "301 Moved Permanently"` | HTTP 연결에 성공했습니다. 서비스가 리디렉션되고 있습니다(일반적으로 HTTPS로). 이는 정상적인 현상입니다. |

**분류된 오류 출력**

| 오류 | 메모 | 의미 |
| --- | --- | --- |
| `"Not an HTTP/HTTPS service"` | `"The service appears to be a non-HTTP service (e.g., database, message queue, or custom TCP). Use the port_open and reachability fields to verify connectivity."` | 포트가 열려 있지만 서비스가 HTTP를 사용하지 않습니다. 데이터베이스, SFTP, 사용자 지정 TCP 및 이와 유사한 서비스에 필요합니다. |
| `"Connection refused"` | `"The port is not accepting connections. Verify the service is running and listening on this port."` | 이 포트에서는 아무것도 들을 수 없습니다. |
| `"Connection timed out"` | `"The connection timed out. Check firewall rules and network routing."` | 방화벽 또는 라우팅 문제로 인해 연결할 수 없습니다. |
| `"No IPs resolved for host"` | — | DNS 확인 실패. HTTP를 테스트할 수 없습니다. |

>[!NOTE]
>
>대상 서비스의 모든 HTTP 상태 코드(예: `200`, `301`, `302`, `403`, `404` 또는 `500`)는 연결을 위한 **성공 신호**&#x200B;입니다. 이는 **네트워크 경로**&#x200B;가 작동함을 의미합니다. 상태 코드는 전체 네트워크 상태가 아니라 서비스 자체의 응답을 반영합니다. HTTP가 아닌 서비스의 경우 도구는 **HTTP/HTTPS 서비스가 아님**&#x200B;을(를) 나타냅니다. 해당 서비스의 신뢰할 수 있는 표시기로 **포트 열기** 및 **연결 가능성**&#x200B;을 사용하십시오.

### 도달 용이성 {#reachability}

| 결과 | 의미 |
| --- | --- |
| **연결 가능** | 고급 네트워킹 인프라에서 대상 호스트 및 포트에 연결할 수 있습니다. 네트워크 구성이 올바릅니다. |
| **연결할 수 없음: 포트에 액세스할 수 없음** | DNS가 확인되었지만 포트에 대한 TCP가 실패했습니다. 일반적으로 방화벽 또는 라우팅 문제입니다. |
| **연결할 수 없음: DNS 확인 실패** | 구성으로 호스트 이름을 확인할 수 없습니다. 이는 DNS 구성 문제를 나타냅니다. |

### 여러 DNS Resolver {#multiple-dns-resolvers}

고급 네트워킹 인프라에서 **둘 이상의 DNS 확인자**&#x200B;를 정의하는 경우:

* **모든 확인자가 동일한 결과를 반환**&#x200B;하면 **(으)로 레이블이 지정된**&#x200B;단일 통합`default` 결과가 표시됩니다.
* 확인자가 **다른 결과**&#x200B;를 반환하면 각 확인자의 결과가 확인자 IP를 사용하여 **별도로**(`resolver_1`, `resolver_2` 등으로 레이블 지정됨), **표시되므로 불일치를 유발하는 DNS 서버를 확인할 수 있습니다.**

## 문제 해결 {#troubleshooting}

다음 시나리오는 원인을 좁히는 단계와 함께 도구에 표시될 가능성이 높은 항목을 묶습니다. 동일한 상황을 보여 주는 전체 **클립보드에 복사** JSON에 대해서는 [출력 예](#example-outputs)를 참조하십시오.

### DNS 확인 실패 {#dns-failed}

#### 출력

고급 네트워킹 DNS 설정을 사용하여 호스트 이름이 확인되지 않았으므로 도구에서 포트를 테스트할 수 없습니다. 결과 보기에서 **DNS 확인**&#x200B;은 오류 문자열을 표시하고 **연결 가능성**&#x200B;은 DNS가 실패했음을 보고합니다.

```
DNS Resolution: error: "DNS resolution error: ..."
Reachability: "Unreachable: DNS resolution failed"
```

#### 권장 사항

1. **호스트 이름이 올바른지 확인**—오타가 있는지, 의도한 **DNS 영역**&#x200B;을 사용하고 있는지 확인합니다(잘못된 영역은 일반적인 실수).
1. 네트워크 인프라에 구성된 DNS 확인자 **DNS 확인자**&#x200B;이(가) 고급 네트워킹 CIDR 범위&#x200B;**(도구 및 AEM에서 아웃바운드 검사에 사용하는 동일한 주소 공간)에서**&#x200B;연결할 수 있는지 확인합니다. 개인 DNS를 사용하는 경우 해당 서버는 VPN 터널을 통해 또는 고급 네트워킹에 라우팅이 적용되는 네트워크 주소 공간 내에서 접근 가능해야 합니다.
1. **구성된 DNS 서버가 호스트 이름을 확인할 수 있는지 확인합니다** — 고급 네트워킹은 네트워크 인프라 설정에 정의된 확인기만 **사용합니다**. 공용 DNS는 **사용하지 않음**&#x200B;합니다(예: `8.8.8.8`). 내부 DNS에 해당 호스트 이름에 대한 레코드가 없는 경우 확인에 실패합니다.
1. **VPN 설정의 경우:** DNS 서버 IP 주소가 VPN 주소 공간(터널이 만들어진 원격 네트워크 CIDR) 내에 있는지 확인합니다. VPN 터널을 통해 라우팅되지 않은 서브넷의 확인자는 고급 네트워킹에서 연결할 수 없습니다.

### DNS가 작동하지만 포트에 액세스할 수 없음 {#dns-ok-port-blocked}

#### 출력

이 도구는 호스트를 확인할 수 있지만 포트에 대한 TCP가 성공하지 못합니다. 요약은 다음과 같은 경우가 많습니다.

```
DNS Resolution: ips: ["10.0.1.50"]
Port Open: No
Reachability: "Unreachable: Port not accessible"
```

#### 권장 사항

1. **대상 서비스의 방화벽 및 허용 목록 규칙 검토**—고급 네트워킹 인프라 CIDR 범위(및 AEM에서 사용하는 이그레스 IP 주소)에서 들어오는 트래픽을 허용해야 합니다. VPN을 사용하는 경우 설계에 따라 원격 네트워크 CIDR을 포함하십시오.
1. **서비스가 실행 중인지 확인** 및 **테스트에서 입력한 호스트 및 포트를 수신**.
1. **VPN 설정의 경우:** 터널이 작동되고 라우팅이 대상 서브넷에 도달하며 대상 주소가 VPN을 통해 전송되는 원격 네트워크 주소 공간에 있는지 확인합니다.
1. 인프라에서 고급 네트워킹과 대상 간의 포트를 차단할 수 있는 **네트워크 보안 그룹(NSG), 보안 규칙 또는 이와 동등한 항목**&#x200B;을 검토하십시오.
1. **포트 번호 확인**—테스트 중인 포트에서 프로세스가 실제로 수신 대기하고 있는지 확인합니다.

### 테스트 프로그램에 연결할 수 있지만 AEM이 연결되지 않음 {#reachable-but-aem-fails}

#### 출력

연결 검사 자체가 성공했습니다. 요약된 요약은 다음과 같습니다.

```
Port Open: Yes
Reachability: "Reachable"
```

이 결과는 고급 네트워킹에서 테스트한 호스트 및 포트로의 경로가 열려 있음을 의미합니다. AEM 애플리케이션 트래픽에서 해당 경로를 사용하는지 보장하지는 않습니다. 코드가 실행될 때 서비스 로그에 예상한 이그레스 IP의 요청이 표시되지 않을 수 있습니다.

#### 권장 사항

1. **프록시를 사용하도록 응용 프로그램 코드를 구성해야 합니다**. 연결 테스트는 네트워크 경로가 작동함을 확인하지만 AEM은 **고급 네트워킹 프록시**&#x200B;를 통해(예: **`AEM_PROXY_HOST`** 환경 변수를 통해) 요청을 명시적으로 라우팅해야 합니다. 코드가 프록시 없이 직접 연결하는 경우 트래픽이 고급 네트워킹 인프라를 거치지 않습니다.
1. **HTTP 클라이언트에서 프록시 설정을 검토하십시오** - HTTP 클라이언트는 동일한 프록시 구성(`AEM_PROXY_HOST` 및 해당되는 경우 포트 전달)을 사용해야 합니다.
1. **고급 네트워킹에 대한 포트 전달 구성을 확인** **환경** 수준에서: `portForwards`에서 각 항목은 **`portOrig`**&#x200B;을(를) 올바른 **`portDest`**&#x200B;대상 호스트&#x200B;**의**&#x200B;에 매핑해야 합니다. **`portOrig`**&#x200B;은(는) 프록시를 통해 아웃바운드 연결을 열 때 AEM 응용 프로그램 코드가 연결하는 **포트입니다**. **`portDest`**&#x200B;은(는) 원격 프로세스가 수신 중인 대상 서비스의 **실제 포트**&#x200B;입니다. **대상 호스트**&#x200B;은(는) 앞으로 사용된 해당 서비스의 **호스트 이름 또는 주소**&#x200B;입니다. 세 가지 모두 연결을 위해 애플리케이션을 작성하는 방식과 일치해야 합니다.
1. **확인`nonProxyHosts`**. 대상 호스트가 목록에 있으면 해당 호스트에 대해 **프록시 건너뛰기**&#x200B;를 요청하고 확인한 고급 네트워킹 경로를 따르지 않습니다.

### HTTP에 오류가 표시되지만 포트가 열려 있습니다. {#http-error-port-open}

#### 출력

TCP가 성공하지만 HTTP/HTTPS 프로브가 여전히 실패를 보고합니다. 요약은 다음과 같은 경우가 많습니다.

```
Port Open: Yes
HTTP Connectivity: error: "Connection error: ..." or "Both HTTPS and HTTP failed. ..."
Reachability: "Reachable"
```

#### 권장 사항

1. **서비스에서 HTTP 또는 HTTPS를 사용할 수 없습니다**(예: 원시 TCP, gRPC 또는 다른 프로토콜). `Port open: Yes` 및 `Reachability: Reachable`에서 네트워크 경로가 작동하는지 확인하는 동안 HTTP 프로브가 실패할 수 있습니다. 이러한 필드를 비 HTTP 서비스에 대한 신뢰할 수 있는 소스로 사용합니다.
1. **TLS 및 인증서 구성을 조사합니다**. HTTPS가 실패하지만 HTTP가 성공하는 경우(경우에 따라 `HTTPS failed, HTTP succeeded`과(와) 같은 메모로 표시됨) 서비스에 인증서 문제가 있거나 해당 포트에서 HTTP만 제공할 수 있습니다.

### 요청 시간 초과 {#timeout}

#### 출력

```json
{ "error": "Request timeout" }
```

#### 권장 사항

1. **서비스 응답 시간 허용**—확인 시 5초의 시간 제한을 사용합니다. 그보다 더 느리게 응답하는 대상은 정상인 경우에도 시간 초과됩니다.
1. **네트워크 대기 시간 계정**. VPN 연결에서 지연 시간이 길거나 비정상 터널이 한도를 초과하여 왕복 경로를 푸시할 수 있습니다. 터널 상태 및 라우팅을 검토하십시오.
1. **다시 테스트 실행**. 일회성 네트워크 장애로 인해 다시 발생하지 않는 시간 제한이 발생할 수 있습니다.

## 출력 예 {#example-outputs}

### 성공적인 HTTPS 테스트(예: 포트 443의 내부 API) {#example-output-successful-https}

```json
{
  "resolvers": [
    {
      "name": "default",
      "dns_resolution": {
        "ips": ["10.0.1.50"]
      },
      "port_open": true,
      "http_connectivity": {
        "protocol": "https",
        "status_code": 200,
        "reason": "200 OK"
      },
      "reachability": "Reachable"
    }
  ]
}
```

### 비 HTTP 서비스 테스트 성공(예: 포트 5432의 데이터베이스) {#example-output-successful-non-http}

```json
{
  "resolvers": [
    {
      "name": "default",
      "dns_resolution": {
        "ips": ["10.0.1.50"]
      },
      "port_open": true,
      "http_connectivity": {
        "error": "Not an HTTP/HTTPS service",
        "note": "The service appears to be a non-HTTP service (e.g., database, message queue, or custom TCP). Use the port_open and reachability fields to verify connectivity."
      },
      "reachability": "Reachable"
    }
  ]
}
```

>[!NOTE]
>
>비 HTTP 서비스에는 HTTP 오류가 필요합니다. **포트 열기: true** 및 **연결 가능: 연결 가능** 네트워크 경로가 작동하는지 확인합니다.

### DNS 확인 실패 {#example-output-dns-resolution-failure}

```json
{
  "resolvers": [
    {
      "name": "default",
      "dns_resolution": {
        "error": "DNS resolution error: dial udp 10.0.0.2:53: i/o timeout"
      },
      "port_open": false,
      "http_connectivity": {
        "error": "DNS resolution failed"
      },
      "reachability": "Unreachable: DNS resolution failed"
    }
  ]
}
```

### 포트에 액세스할 수 없음(방화벽/서비스 중단) {#example-output-port-not-accessible}

```json
{
  "resolvers": [
    {
      "name": "default",
      "dns_resolution": {
        "ips": ["10.0.1.50"]
      },
      "port_open": false,
      "http_connectivity": {
        "error": "Connection error: dial tcp 10.0.1.50:443: i/o timeout"
      },
      "reachability": "Unreachable: Port not accessible"
    }
  ]
}
```

## 중요 참고 사항 {#important-notes}

### 이 테스트로 수행할 수 없는 작업 {#what-this-test-does-not-do}

* 테스트는 AEM 작성자 또는 게시 pod 내에서 실행되지 않습니다. **이그레스 프록시 인프라**&#x200B;에서 실행됩니다. 코드에서 응용 프로그램 수준 프록시 구성이 아니라 네트워크 계층을 확인합니다.
* AEM 애플리케이션의 프록시 설정을 확인하지 않습니다. 결과가 `Reachable`인 경우에도 프록시를 사용하도록 AEM 코드를 구성해야 합니다.
* 자체적으로 환경 수준의 포트 전달 구성을 확인하지 않습니다. 인프라 경로에서 원시 연결을 테스트합니다.
* 사용자 지정 페이로드는 전송되지 않습니다. HTTP 테스트에서 `GET`에 기본 `/` 요청을 발행합니다.

### 응답 시간 {#response-time}

* **일반:** 약 2~3초.
* **최대:** 약 5초 시간 제한.
* **모든 DNS 확인자** 및 연결 검사가 동시에 실행됩니다.

### HTTP 서비스와 비 HTTP 서비스 비교 {#http-vs-non-http-services}

이 도구는 모든 포트에서 HTTP/HTTPS 연결을 시도합니다. HTTP가 아닌 서비스(예: 포트 5432의 PostgreSQL, 포트 3306의 MySQL, 포트 22의 SFTP, 포트 6379의 Redis)의 경우 HTTP 검사가 실패하고 연결 오류가 발생할 수 있습니다. 이는 예상된 결과입니다. 해당 서비스에 대한 연결을 확인하려면 `Port open` 및 `Reachability`을(를) 사용하세요.

## 관련 정보 {#related-information}

* [AEM as a Cloud Service에 대한 고급 네트워킹 구성](/help/security/configuring-advanced-networking.md)
* [Experience League의 고급 네트워킹 자습서](https://experienceleague.adobe.com/ko/docs/experience-manager-learn/cloud-service/networking/advanced-networking)
