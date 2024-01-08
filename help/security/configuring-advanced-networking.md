---
title: AEM as a Cloud Service에 대한 고급 네트워킹 구성
description: AEM as a Cloud Service에 대해 VPN 또는 유연한/전용 이그레스 IP 주소와 같은 고급 네트워킹 기능을 구성하는 방법에 대해 알아봅니다.
exl-id: 968cb7be-4ed5-47e5-8586-440710e4aaa9
source-git-commit: a77e5dc4273736b969e9a4a62fcac75664495ee6
workflow-type: ht
source-wordcount: '3526'
ht-degree: 100%

---

# AEM as a Cloud Service에 대한 고급 네트워킹 구성 {#configuring-advanced-networking}

이 문서에서는 VPN 셀프서비스 프로비저닝, 비표준 포트 및 전용 이그레스 IP 주소를 포함하여 AEM as a Cloud Service의 다양한 고급 네트워킹 기능에 대해 소개하고자 합니다.

>[!INFO]
>
>이 [위치](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/networking/advanced-networking.html)에서는 각각의 고급 네트워킹 옵션에 대해 설명하기 위해 설계된 일련의 문서를 찾아볼 수도 있습니다.

## 개요 {#overview}

AEM as a Cloud Service는 Cloud Manager API를 사용하여 구성할 수 있는 몇 가지 유형의 고급 네트워킹 기능을 제공합니다. 여기에는 다음이 포함됩니다.

* [유연한 포트 이그레스](#flexible-port-egress) - 비표준 포트의 아웃바운드 트래픽을 허용하도록 AEM as a Cloud Service를 구성합니다.
* [전용 이그레스 IP 주소](#dedicated-egress-IP-address) - AEM as a Cloud Service의 트래픽을 고유 IP에서 생성되도록 구성합니다.
* [Virtual Private Network(VPN)](#vpn) - VPN 기술을 보유한 고객에 대해 고객 인프라 및 AEM as a Cloud Service 간의 트래픽을 보호합니다.

이 문서에서는 구성 방법을 포함하여 이러한 옵션 각각에 대해 자세히 설명합니다. 일반적인 구성 전략으로, 프로그램 수준에서 `/networkInfrastructures` API 엔드포인트가 호출되어 원하는 고급 네트워킹 유형을 선언한 다음 각 환경에 대해 `/advancedNetworking` 엔드포인트가 호출되어 인프라를 활성화하고 환경별 매개변수를 구성합니다. 각 형식 구문, 샘플 요청 및 응답은 Cloud Manager API 설명서에 기재된 적절한 엔드포인트를 참조하십시오.

프로그램에서 단일 고급 네트워킹 변형을 프로비저닝할 수 있습니다. 유연한 포트 이그레스와 전용 이그레스 IP 주소 사이에서 결정할 때, 특정 IP 주소가 필요하지 않은 경우 Adobe에서 유연한 포트 이그레스 트래픽의 성능을 최적화할 수 있으므로 유연한 포트 이그레스를 선택하는 것이 좋습니다.

>[!INFO]
>
>샌드박스 프로그램에서는 고급 네트워킹을 사용할 수 없습니다.
>또한 환경을 AEM 버전 5958 이상으로 업그레이드해야 합니다.

>[!NOTE]
>
>레거시 전용 이그레스 기술을 통해 이미 프로비저닝되었으며 이들 옵션 중 하나를 구성해야 하는 고객은 옵션을 구성해서는 안 되며, 그렇지 않으면 사이트 연결에 영향을 미칠 수 있습니다. 도움이 필요하면 Adobe 지원 팀에 문의하십시오.

## 유연한 포트 이그레스 {#flexible-port-egress}

이 고급 네트워킹 기능을 사용하면 기본적으로 열려 있는 HTTP(포트 80) 및 HTTPS(포트 443) 이외의 포트를 통해 이그레스 트래픽에 AEM as a Cloud Service를 구성할 수 있습니다.

### 고려 사항 {#flexible-port-egress-considerations}

VPN 및 전용 이그레스 IP 주소가 필요하지 않은 경우, 전용 이그레스에 의존하지 않는 트래픽을 사용할 때 더 많은 처리량을 달성할 수 있으므로 유연한 포트 이그레스가 권장됩니다.

### 구성 {#configuring-flexible-port-egress-provision}

프로그램당 한 번씩 POST `/program/<programId>/networkInfrastructures` 엔드포인트가 호출되어 `kind` 매개변수 및 지역에 대한 `flexiblePortEgress` 값이 간단히 전달됩니다. 해당 엔드포인트는 `network_id`와 상태 등의 기타 정보에 응답합니다. 전체 매개변수 세트와 정확한 구문은 물론 나중에 변경할 수 없는 매개변수와 같은 중요한 정보는 [API 문서에서 참조할 수 있습니다.](https://developer.adobe.com/experience-cloud/cloud-manager/reference/api/#operation/createNetworkInfrastructure)

호출되면 네트워킹 인프라가 프로비저닝되는 데 일반적으로 약 15분이 소요됩니다. Cloud Manager의 [네트워크 인프라 GET 엔드포인트](https://developer.adobe.com/experience-cloud/cloud-manager/reference/api/#operation/getNetworkInfrastructure) 호출은 “준비됨” 상태로 표시됩니다.

프로그램에서 설정한 유연한 포트 이그레스 구성이 준비되면 환경별로 `PUT /program/<program_id>/environment/<environment_id>/advancedNetworking` 엔드포인트를 호출하여 환경 수준에서 네트워킹을 활성화하고 필요한 경우 포트 전달 규칙을 선언해야 합니다. 유연성을 제공하기 위해 환경별로 매개변수를 구성할 수 있습니다.

포트 전달 규칙은 http 또는 https 프로토콜을 사용하는 경우에 한해서만 80/443 이외의 모든 대상 포트에 대해 대상 호스트(포트 포함, 이름 또는 IP)
집합을 지정하여 선언해야 합니다. http/https를 통해 포트 80/443을 사용하는 클라이언트 연결은 연결에 고급 네트워킹 속성을 적용하려면 연결 시 프록시 설정을 사용해야 합니다. 각 대상 호스트에 대해 고객은 원하는 대상 포트를 30000에서 30999 사이의 포트에 매핑해야 합니다.

API는 몇 초 안에 응답하여 업데이트 상태를 표시해야 하고, 약 10분 후 엔드포인트의 `GET` 메서드는 고급 네트워킹이 활성화되었음을 표시해야 합니다.

### 업데이트 {#updating-flexible-port-egress-provision}

`PUT /api/program/<program_id>/network/<network_id>` 엔드포인트를 호출하여 프로그램 수준 구성을 업데이트할 수 있으며 몇 분 안에 효력이 발생합니다.

>[!NOTE]
>
> “종류” 매개변수(`flexiblePortEgress`, `dedicatedEgressIP` 또는 `VPN`)는 수정할 수 없습니다. 도움이 필요하면 고객 지원 센터에 문의하여 기존 내용과 변경 사유에 대해 설명하고 도움을 얻으십시오.

`PUT /program/{programId}/environment/{environmentId}/advancedNetworking` 엔드포인트를 다시 호출하여 환경당 포트 전달 규칙을 하위 집합이 아닌 전체 구성 매개변수 집합을 포함하도록 업데이트할 수 있습니다.

### 유연한 포트 이그레스 비활성화 {#disabling-flexible-port-egress-provision}

특정 환경에서 유연한 포트 이그레스를 **비활성화**&#x200B;하려면 `DELETE [/program/{programId}/environment/{environmentId}/advancedNetworking]()`를 호출하십시오.

API에 대한 자세한 내용은 [Cloud Manager API 설명서](https://developer.adobe.com/experience-cloud/cloud-manager/reference/api/#operation/disableEnvironmentAdvancedNetworkingConfiguration)를 참조하십시오.

### 트래픽 라우팅 {#flexible-port-egress-traffic-routing}

80 또는 443 이외의 포트로 이동하는 HTTP 또는 HTTPS 트래픽의 경우 다음 호스트 및 포트 환경 변수를 사용하여 프록시를 구성해야 합니다.

* HTTP: `AEM_PROXY_HOST` / `AEM_HTTP_PROXY_PORT ` (`proxy.tunnel:3128`로 기본값 설정(AEM 릴리스) &lt; 6094)
* HTTPS: `AEM_PROXY_HOST` / `AEM_HTTPS_PROXY_PORT ` (`proxy.tunnel:3128`로 기본값 설정(AEM 릴리스) &lt; 6094)

`www.example.com:8443`으로 요청을 전송하는 샘플 코드로 예를 들어 보겠습니다.

```java
String url = "www.example.com:8443"
String proxyHost = System.getenv().getOrDefault("AEM_PROXY_HOST", "proxy.tunnel");
int proxyPort = Integer.parseInt(System.getenv().getOrDefault("AEM_HTTPS_PROXY_PORT", "3128"));
HttpClient client = HttpClient.newBuilder()
      .proxy(ProxySelector.of(new InetSocketAddress(proxyHost, proxyPort)))
      .build();
 
HttpRequest request = HttpRequest.newBuilder().uri(URI.create(url)).build();
HttpResponse<String> response = client.send(request, BodyHandlers.ofString());
```

비표준 Java 네트워킹 라이브러리를 사용하는 경우 모든 트래픽에 대해 위의 속성을 사용하여 프록시를 구성할 수 있습니다.

`portForwards` 매개변수에 선언된 포트를 통한 대상이 있는 비 HTTP/S 트래픽은 매핑된 포트와 함께 `AEM_PROXY_HOST`라는 속성을 참조해야 합니다. 예:

```java
DriverManager.getConnection("jdbc:mysql://" + System.getenv("AEM_PROXY_HOST") + ":53306/test");
```

아래 표에서는 트래픽 라우팅에 대해 설명합니다.

<table>
<thead>
  <tr>
    <th>트래픽</th>
    <th>대상 조건</th>
    <th>포트</th>
    <th>연결</th>
    <th>외부 대상 예</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td><b>HTTP 또는 HTTPS 프로토콜</b></td>
    <td>표준 HTTP/S 트래픽</td>
    <td>80 또는 443</td>
    <td>허용됨</td>
    <td></td>
  </tr> 
  <tr>
    <td></td>
    <td>다음 환경 변수 및 프록시 포트 번호를 사용하여 구성된 HTTP 프록시를 통한 80 또는 443 이외의 포트의 비표준 트래픽. Cloud Manager API 호출의 portForwards 매개변수에서 대상 포트를 선언하지 마십시오.<br><ul>
     <li>AEM_PROXY_HOST (`proxy.tunnel`로 기본값 설정(AEM 릴리스) &lt; 6094)</li>
     <li>AEM_HTTPS_PROXY_PORT (포트 3128로 기본값 설정(AEM 릴리스) &lt; 6094)</li>
    </ul>
    <td>80 또는 443 이외의 포트</td>
    <td>허용됨</td>
    <td>example.com:8443</td>
  </tr>
  <tr>
    <td></td>
    <td>HTTP 프록시를 사용하지 않는 포트 80 또는 443 이외의 다른 포트의 비표준 트래픽</td>
    <td>80 또는 443 이외의 포트</td>
    <td>차단됨</td>
    <td></td>
  </tr>
  <tr>
    <td><b>비 HTTP 또는 비 HTTPS</b></td>
    <td>클라이언트가 <code>portForwards</code> API 매개변수에서 선언된 <code>portOrig</code>를 사용하여 <code>AEM_PROXY_HOST</code> 환경 변수를 연결합니다.</td>
    <td>임의</td>
    <td>허용됨</td>
    <td><code>mysql.example.com:3306</code></td>
  </tr>
  <tr>
    <td></td>
    <td>기타</td>
    <td>임의</td>
    <td>차단됨</td>
    <td><code>db.example.com:5555</code></td>
  </tr>
</tbody>
</table>

**Apache/Dispatcher 구성**

위에서 설명한 속성을 사용하여 AEM Cloud Service Apache/Dispatcher 계층의 `mod_proxy` 지시문을 구성할 수 있습니다.

```
ProxyRemote "http://example.com:8080" "http://${AEM_PROXY_HOST}:3128"
ProxyPass "/somepath" "http://example.com:8080"
ProxyPassReverse "/somepath" "http://example.com:8080"
```

```
SSLProxyEngine on //needed for https backends
 
ProxyRemote "https://example.com:8443" "http://${AEM_PROXY_HOST}:3128"
ProxyPass "/somepath" "https://example.com:8443"
ProxyPassReverse "/somepath" "https://example.com:8443"
```

## 전용 이그레스 IP 주소 {#dedicated-egress-IP-address}

>[!NOTE]
>
>2021년 9월 릴리스(21/10/6) 이전에 전용 이그레스 IP로 프로비저닝된 경우, [레거시 전용 이그레스 주소 고객](#legacy-dedicated-egress-address-customers)을 참조하십시오.

### 이점 {#benefits}

이 전용 IP 주소를 사용하면 CRM 공급업체와 같은 SaaS 공급업체 또는 IP 주소 허용 목록을 제공하는 AEM as a Cloud Service 외부의 다른 통합과 통합 시 보안을 강화 수 있습니다. 전용 IP 주소를 허용 목록에 추가하면 고객의 AEM Cloud Service의 트래픽만 외부 서비스로 연결되도록 허용할 수 있습니다. 다른 허용된 IP의 트래픽도 포함됩니다.

전용 IP 주소 기능을 활성화하지 않으면 AEM as a Cloud Service의 트래픽이 다른 고객과 공유된 IP 집합을 통해 흐릅니다.

### 구성 {#configuring-dedicated-egress-provision}

>[!INFO]
>
>전용 이그레스 IP 주소에서는 Splunk 전달 기능을 사용할 수 없습니다.

전용 이그레스 IP 주소 구성은 [유연한 포트 이그레스](#configuring-flexible-port-egress-provision)와 동일합니다.

주요 차이점은 트래픽은 항상 전용 고유 IP에서 이그레스된다는 것입니다. 해당 IP를 찾으려면 DNS Resolver를 사용하여 `p{PROGRAM_ID}.external.adobeaemcloud.com`과 연계된 IP 주소를 식별하십시오. 해당 IP 주소는 변경되지 않지만 향후에 변경해야 하는 경우 고급 알림이 제공됩니다.

`PUT /program/<program_id>/environment/<environment_id>/advancedNetworking` 엔드포인트의 유연한 포트 이그레스에서는 라우팅 규칙을 지원하며 전용 이그레스 IP 주소에서는 `nonProxyHosts` 매개변수를 지원합니다. 이를 통해 전용 IP가 아닌 공유 IP 주소 범위를 통해 라우팅해야 하는 호스트 집합을 선언할 수 있습니다. 이렇게 하면 공유 IP를 통해 이그레스되는 트래픽이 더욱 최적화될 수 있습니다. `nonProxyHost` URL은 `example.com` 또는 `*.example.com`의 패턴을 따르며, 여기서 와일드카드는 도메인의 시작 위치에서만 지원됩니다.

유연한 포트 이그레스와 전용 이그레스 IP 주소 사이에서 결정할 때, 특정 IP 주소가 필요하지 않은 경우 Adobe에서 유연한 포트 이그레스 트래픽의 성능을 최적화할 수 있으므로 유연한 포트 이그레스를 선택해야 합니다.

### 전용 이그레스 IP 주소 비활성화 {#disabling-dedicated-egress-IP-address}

특정 환경에서 전용 이그레스 IP 주소를 **비활성화**&#x200B;하려면 `DELETE [/program/{programId}/environment/{environmentId}/advancedNetworking]()`를 호출하십시오.

API에 대한 자세한 내용은 [Cloud Manager API 설명서](https://developer.adobe.com/experience-cloud/cloud-manager/reference/api/#operation/disableEnvironmentAdvancedNetworkingConfiguration)를 참조하십시오.

### 트래픽 라우팅 {#dedcated-egress-ip-traffic-routing}

프록시 구성에 표준 Java 시스템 속성을 사용하는 경우 http 또는 https 트래픽은 사전 구성된 프록시를 통해 전달됩니다.

`portForwards` 매개변수에 선언된 포트를 통한 대상이 있는 비 HTTP/S 트래픽은 매핑된 포트와 함께 `AEM_PROXY_HOST`라는 속성을 참조해야 합니다. 예:

```java
DriverManager.getConnection("jdbc:mysql://" + System.getenv("AEM_PROXY_HOST") + ":53306/test");
```

<table>
<thead>
  <tr>
    <th>트래픽</th>
    <th>대상 조건</th>
    <th>포트</th>
    <th>연결</th>
    <th>외부 대상 예</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td><b>HTTP 또는 HTTPS 프로토콜</b></td>
    <td>Azure 또는 Adobe 서비스로의 트래픽</td>
    <td>임의</td>
    <td>전용 IP가 아닌 공유 클러스터 IP를 통해</td>
    <td>adobe.io<br>api.windows.net</td>
  </tr>
  <tr>
    <td></td>
    <td><code>nonProxyHosts</code> 매개변수와 일치하는 호스트</td>
    <td>80 또는 443</td>
    <td>공유 클러스터 IP를 통해</td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td><code>nonProxyHosts</code> 매개변수와 일치하는 호스트</td>
    <td>80 또는 443 이외의 포트</td>
    <td>차단됨</td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td>기본적으로 표준 Java HTTP 클라이언트 라이브러리를 사용하여 HTTP/S 트래픽에 대해 구성되는 HTTP 프록시 구성을 통해</td>
    <td>임의</td>
    <td>전용 이그레스 IP를 통해</td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td>HTTP 프록시 구성 무시(예: 표준 Java HTTP 클라이언트 라이브러리에서 명시적으로 제거된 경우 또는 표준 프록시 구성을 무시하는 Java 라이브러리를 사용하는 경우)</td>
    <td>80 또는 443</td>
    <td>공유 클러스터 IP를 통해</td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td>HTTP 프록시 구성 무시(예: 표준 Java HTTP 클라이언트 라이브러리에서 명시적으로 제거된 경우 또는 표준 프록시 구성을 무시하는 Java 라이브러리를 사용하는 경우)</td>
    <td>80 또는 443 이외의 포트</td>
    <td>차단됨</td>
    <td></td>
  </tr>
  <tr>
    <td><b>비 HTTP 또는 비 HTTPS</b></td>
    <td>클라이언트가 <code>portForwards</code> API 매개변수에서 선언된 <code>portOrig</code>를 사용하여 <code>AEM_PROXY_HOST</code> 환경 변수 연결</td>
    <td>임의</td>
    <td>전용 이그레스 IP를 통해</td>
    <td><code>mysql.example.com:3306</code></td>
  </tr>
  <tr>
    <td></td>
    <td>기타</td>
    <td></td>
    <td>차단됨</td>
    <td></td>
  </tr>
</tbody>
</table>

## 기능 사용 {#feature-usage}

해당 기능은 프록시 구성에 표준 Java 시스템 속성을 사용하는 경우 아웃바운드 트래픽을 생성하는 Java 코드 또는 라이브러리와 호환됩니다. 따라서 가장 일반적인 라이브러리가 포함되어야 합니다.

다음은 코드 샘플입니다.

```java
public JSONObject getJsonObject(String relativePath, String queryString) throws IOException, JSONException {
  String relativeUri = queryString.isEmpty() ? relativePath : (relativePath + '?' + queryString);
  URL finalUrl = endpointUri.resolve(relativeUri).toURL();
  URLConnection connection = finalUrl.openConnection();
  connection.addRequestProperty("Accept", "application/json");
  connection.addRequestProperty("X-API-KEY", apiKey);

  try (InputStream responseStream = connection.getInputStream(); Reader responseReader = new BufferedReader(new InputStreamReader(responseStream, Charsets.UTF_8))) {
    return new JSONObject(new JSONTokener(responseReader));
  }
}
```

일부 라이브러리는 프록시 구성에 표준 Java 시스템 속성을 사용하려면 명시적인 구성이 필요합니다.

[`HttpClientBuilder.useSystemProperties()`](https://hc.apache.org/httpcomponents-client-4.5.x/current/httpclient/apidocs/org/apache/http/impl/client/HttpClientBuilder.html)에 대한 명시적인 호출이 필요하거나 [`HttpClients.createSystem()`](https://hc.apache.org/httpcomponents-client-4.5.x/current/httpclient/apidocs/org/apache/http/impl/client/HttpClients.html#createSystem())을 사용하는 Apache HttpClient를 사용하는 예는 다음과 같습니다.

```java
public JSONObject getJsonObject(String relativePath, String queryString) throws IOException, JSONException {
  String relativeUri = queryString.isEmpty() ? relativePath : (relativePath + '?' + queryString);
  URL finalUrl = endpointUri.resolve(relativeUri).toURL();

  HttpClient httpClient = HttpClientBuilder.create().useSystemProperties().build();
  HttpGet request = new HttpGet(finalUrl.toURI());
  request.setHeader("Accept", "application/json");
  request.setHeader("X-API-KEY", apiKey);
  HttpResponse response = httpClient.execute(request);
  String result = EntityUtils.toString(response.getEntity());
}
```

Adobe 조직의 모든 고객 프로그램 및 각 프로그램의 모든 환경에 동일한 전용 IP가 적용됩니다. 작성자 및 게시 서비스 모두에 적용됩니다.

### 디버깅 고려 사항 {#debugging-considerations}

예상되는 전용 IP 주소에 트래픽이 실제로 송신되는지 확인하려면 가능한 경우 대상 서비스의 로그를 확인하십시오. 그렇지 않으면 [https://ifconfig.me/IP](https://ifconfig.me/IP)와 같이 호출 IP 주소를 반환하는 디버깅 서비스를 호출하는 것이 유용할 수 있습니다.

## 레거시 전용 이그레스 주소 고객 {#legacy-dedicated-egress-address-customers}

2021년 9월 30일 이전에 전용 이그레스 IP로 프로비저닝된 경우, 전용 이그레스 IP 기능은 HTTP 및 HTTPS 포트만 지원합니다.
여기에는 암호화 시 HTTP/1.1 및 HTTP/2가 포함됩니다. 또한 하나의 전용 이그레스 엔드포인트는 각각 포트 80/443에서 HTTP/HTTPS를 통해서만 대상과 통신할 수 있습니다.

## Virtual Private Network(VPN) {#vpn}

VPN을 사용하면 작성자, 게시 또는 미리보기에서 온프레미스 인프라 또는 데이터센터에 연결할 수 있습니다. 예를 들어 데이터베이스에 액세스할 수 있습니다.

또한 VPN을 사용하면 VPN을 지원하는 CRM 공급업체와 같은 SaaS 공급업체에 연결하거나 기업 네트워크에서 AEM as a Cloud Service 작성자, 미리보기 또는 게시에 연결할 수 있습니다.

대부분의 IPSec 기술이 내장된 VPN 디바이스가 지원됩니다. **RouteBased 구성 지침** 열에 기재된 정보에 따라 [이 페이지](https://docs.microsoft.com/en-us/azure/vpn-gateway/vpn-gateway-about-vpn-devices#devicetable)의 디바이스 목록을 참조하십시오. 표에 설명된 대로 디바이스를 구성하십시오.

### 일반적인 고려 사항 {#general-vpn-considerations}

* 지원은 단일 VPN 연결로 제한됩니다.
* VPN 연결에는 Splunk 전달 기능을 사용할 수 없습니다.

### 만들기 {#vpn-creation}

프로그램당 한 번씩 POST `/program/<programId>/networkInfrastructures` 엔드포인트가 호출되어 `kind` 매개변수, 지역, 주소 공간(CIDR 목록 - 나중에 수정할 수 없음)에 대한 “vpn” 값, 고객 네트워크의 이름 확인을 위한 DNS Resolver 및 게이트웨이 구성, 공유 VPN 키 및 IP 보안 정책과 같은 VPN 연결 정보 등을 포함하는 구성 정보 페이로드를 전달합니다. 해당 엔드포인트는 `network_id`와 상태 등의 기타 정보에 응답합니다. [API 설명서](https://developer.adobe.com/experience-cloud/cloud-manager/reference/api/#operation/createNetworkInfrastructure)에 전체 매개변수 및 정확한 구문 집합이 참조되어야 합니다.

호출되면 네트워킹 인프라가 프로비저닝되는 데 일반적으로 약 45분에서 60분이 소요됩니다. API의 GET 메서드를 호출하여 현재 상태를 반환하고 `creating`에서 `ready`로 전환할 수 있습니다. 모든 상태에 대한 내용은 API 설명서를 참조하십시오.

프로그램에서 설정한 VPN 구성이 준비되면 환경별로 `PUT /program/<program_id>/environment/<environment_id>/advancedNetworking` 엔드포인트를 호출하여 환경 수준에서 네트워킹을 활성화하고 포트 전달 규칙을 선언해야 합니다. 유연성을 제공하기 위해 환경별로 매개변수를 구성할 수 있습니다.

자세한 내용은 [API 설명서](https://developer.adobe.com/experience-cloud/cloud-manager/reference/api/#operation/enableEnvironmentAdvancedNetworkingConfiguration)를 참조하십시오.

포트 전달 규칙은 VPN을 통해 라우팅되어야 하는 비 HTTP/S 프로토콜 TCP 트래픽에 대해 대상 호스트(포트 포함, 이름 또는 IP) 집합을 지정하여 선언해야 합니다. 각 대상 호스트에 대해 고객은 원하는 대상 포트를 30000에서 30999 사이의 포트에 매핑해야 합니다. 이 값은 프로그램의 환경 간에 고유한 값이어야 합니다. 또한 고객은 `nonProxyHosts` 매개변수에 트래픽이 VPN 라우팅은 우회하고 공유 IP 범위를 거쳐야 하는 URL 세트를 나열할 수도 있습니다. 해당 URL 세트는 `example.com` 또는 `*.example.com`의 패턴을 따르며, 여기서 와일드카드는 도메인의 시작 위치에서만 지원됩니다.

API는 몇 초 안에 응답하여 `updating` 상태를 표시하고, 약 10분 후 Cloud Manager의 환경 GET 엔드포인트에 대한 호출에 환경 업데이트가 적용되었음을 나타내는 `ready` 상태가 표시됩니다.

환경 트래픽 라우팅 규칙(호스트 또는 우회)이 없더라도 빈 페이로드와 함께 `PUT /program/<program_id>/environment/<environment_id>/advancedNetworking`을 호출해야 합니다.

### VPN 업데이트 {#updating-the-vpn}

`PUT /api/program/<program_id>/network/<network_id>` 엔드포인트를 호출하여 프로그램 수준 VPN 구성을 업데이트할 수 있습니다.

최초 VPN 프로비저닝 후에는 주소 공간을 변경할 수 없습니다. 필요한 경우 고객 지원 팀에 문의하십시오. 또한 `kind` 매개변수(`flexiblePortEgress`, `dedicatedEgressIP` 또는 `VPN`)는 수정할 수 없습니다. 도움이 필요하면 고객 지원 센터에 문의하여 기존 내용과 변경 사유에 대해 설명하고 도움을 얻으십시오.

`PUT /program/{programId}/environment/{environmentId}/advancedNetworking` 엔드포인트를 다시 호출하여 환경당 라우팅 규칙을 하위 집합이 아닌 전체 구성 매개변수 집합을 포함하도록 업데이트할 수 있습니다. 일반적으로 환경 업데이트가 적용되는 데 5~10분 정도 소요됩니다.

### VPN 비활성화 {#disabling-the-vpn}

특정 환경에 대한 VPN을 비활성화하려면 `DELETE /program/{programId}/environment/{environmentId}/advancedNetworking`을 호출하십시오. 자세한 내용은 [API 설명서](https://developer.adobe.com/experience-cloud/cloud-manager/reference/api/#operation/disableEnvironmentAdvancedNetworkingConfiguration)를 참조하십시오.

### 트래픽 라우팅 {#vpn-traffic-routing}

아래 표에서는 트래픽 라우팅에 대해 설명합니다.

<table>
<thead>
  <tr>
    <th>트래픽</th>
    <th>대상 조건</th>
    <th>포트</th>
    <th>연결</th>
    <th>외부 대상 예</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td><b>HTTP 또는 HTTPS 프로토콜</b></td>
    <td>Azure 또는 Adobe 서비스로의 트래픽</td>
    <td>임의</td>
    <td>전용 IP가 아닌 공유 클러스터 IP를 통해</td>
    <td>adobe.io<br>api.windows.net</td>
  </tr>
  <tr>
    <td></td>
    <td><code>nonProxyHosts</code> 매개변수와 일치하는 호스트</td>
    <td>80 또는 443</td>
    <td>공유 클러스터 IP를 통해</td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td><code>nonProxyHosts</code> 매개변수와 일치하는 호스트</td>
    <td>80 또는 443 이외의 포트</td>
    <td>차단됨</td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td>IP가 <i>VPN 게이트웨이 주소</i> 공간 범위에 해당하는 경우, 기본적으로 표준 Java HTTP 클라이언트 라이브러리를 사용하여 HTTP/S 트래픽에 대해 구성되는 HTTP 프록시 구성을 통해</td>
    <td>임의</td>
    <td>VPN을 통해</td>
    <td><code>10.0.0.1:443</code><br>호스트 이름일 수도 있습니다.</td>
  </tr>
  <tr>
    <td></td>
    <td>IP가 <i>VPN 게이트웨이 주소 공간</i> 범위에 해당하지 않는 경우 기본적으로 표준 Java HTTP 클라이언트 라이브러리를 사용하여 HTTP/S 트래픽에 대해 구성되는 HTTP 프록시 구성을 통해</td>
    <td>임의</td>
    <td>전용 이그레스 IP를 통해</td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td>HTTP 프록시 구성 무시(예: 표준 Java HTTP 클라이언트 라이브러리에서 명시적으로 제거된 경우 또는 표준 프록시 구성을 무시하는 Java 라이브러리를 사용하는 경우)
</td>
    <td>80 또는 443</td>
    <td>공유 클러스터 IP를 통해</td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td>HTTP 프록시 구성 무시(예: 표준 Java HTTP 클라이언트 라이브러리에서 명시적으로 제거된 경우 또는 표준 프록시 구성을 무시하는 Java 라이브러리를 사용하는 경우)</td>
    <td>80 또는 443 이외의 포트</td>
    <td>차단됨</td>
    <td></td>
  </tr>
  <tr>
    <td><b>비 HTTP 또는 비 HTTPS</b></td>
    <td>IP가 <i>VPN 게이트웨이 주소 공간</i> 범위에 해당하고 클라이언트가 <code>portForwards</code> API 매개변수에서 선언된 <code>portOrig</code>를 사용하여 <code>AEM_PROXY_HOST</code> 환경 변수를 연결하는 경우</td>
    <td>임의</td>
    <td>VPN을 통해</td>
    <td><code>10.0.0.1:3306</code><br>호스트 이름일 수도 있습니다.</td>
  </tr>
  <tr>
    <td></td>
    <td>IP가 <i>VPN 게이트웨이 주소 공간</i> 범위에 해당하지 않고 클라이언트가 <code>portForwards</code> API 매개변수에서 선언된 <code>portOrig</code>를 사용하여 <code>AEM_PROXY_HOST</code> 환경 변수를 연결하는 경우</td>
    <td>임의</td>
    <td>전용 이그레스 IP를 통해</td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td>기타</td>
    <td>임의</td>
    <td>차단됨</td>
    <td></td>
  </tr>
</tbody>
</table>

### 구성에 유용한 도메인{#vpn-useful-domains-for-configuration}

다음 다이어그램은 구성 및 개발에 유용한 도메인 및 관련 IP 집합을 시각적으로 보여 줍니다. 다이어그램 아래의 표에서는 이들 도메인과 IP에 대해 설명합니다.

![VPN 도메인 구성](/help/security/assets/AdvancedNetworking.jpg)

<table>
<thead>
  <tr>
    <th>도메인 패턴</th>
    <th>AEM으로부터의 이그레스 의미</th>
    <th>AEM으로의 인그레스 의미</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td><code>p{PROGRAM_ID}.external.adobeaemcloud.com</code></td>
    <td>비공개 네트워크를 통하지 않고 인터넷으로 이동하는 트래픽에 대한 전용 이그레스 IP 주소 </td>
    <td>VPN으로부터의 연결은 CDN에 이 IP로부터 오는 연결로 표시됩니다. VPN에서 AEM으로 이동하는 연결만 허용하려면 이 IP만 허용하고 그 외 다른 모든 IP는 차단하도록 Cloud Manager를 구성하십시오. 자세한 내용은 “VPN 연결 인그레스 제한” 섹션을 확인하십시오.</td>
  </tr>
  <tr>
    <td><code>p{PROGRAM_ID}.{REGION}-gateway.external.adobeaemcloud.com</code></td>
    <td>해당 없음</td>
    <td>AEM측 VPN 게이트웨이의 IP입니다. 고객의 네트워크 엔지니어링 팀에서 이 IP를 사용하여 특정 IP 주소의 VPN 게이트웨이에 대한 VPN 연결만 허용할 수 있습니다. </td>
  </tr>
  <tr>
    <td><code>p{PROGRAM_ID}.{REGION}.inner.adobeaemcloud.net</code></td>
    <td>VPN의 AEM 측에서 고객측으로 이동하는 트래픽의 IP입니다. 고객의 구성 허용 목록에 추가하여 AEM으로부터의 연결만 허용할 수 있습니다.</td>
    <td>고객이 AEM으로의 VPN 액세스를 허용하고자 하는 경우 해당 액세스에 사용자 정의 도메인 및/또는 <code>author-p{PROGRAM_ID}-e{ENVIRONMENT_ID}.adobeaemcloud.com</code> 및/또는 <code>publish-p{PROGRAM_ID}-e{ENVIRONMENT_ID}.adobeaemcloud.com</code>을 매핑하도록 CNAME DNS 항목을 구성해야 합니다.</td>
  </tr>
</tbody>
</table>

### VPN을 인그레스 연결로 제한 {#restrict-vpn-to-ingress-connections}

AEM으로의 VPN 액세스만 허용하려면 `p{PROGRAM_ID}.external.adobeaemcloud.com`에 의해 정의된 IP만 환경에 접근할 수 있도록 Cloud Manager에 환경 허용 목록을 구성해야 합니다. 이 작업은 Cloud Manager의 다른 IP 기반 허용 목록과 동일한 방식으로 수행할 수 있습니다.

규칙이 경로 기반이어야 하는 경우 Dispatcher 수준에서 표준 HTTP 지시문을 사용하여 특정 IP를 거부하거나 허용하십시오. 요청이 항상 도메인에 도착하도록 원하는 경로도 CDN에서 캐시할 수 없어야 합니다.

**HTTPd 구성 예**

```
Order deny,allow
Deny from all
Allow from 192.168.0.1
Header always set Cache-Control private
```

## 프로그램의 네트워크 인프라 삭제 {#deleting-network-infrastructure}

프로그램의 네트워크 인프라를 **삭제**&#x200B;하려면 `DELETE /program/{program ID}/networkinfrastructure/{networkinfrastructureID}`를 호출하십시오.

>[!NOTE]
>
> 삭제는 모든 환경에서 고급 네트워크 작업이 비활성화된 경우에만 인프라를 삭제합니다.
> 

## 고급 네트워킹 유형 간 전환 {#transitioning-between-advanced-networking-types}

다음 절차에 따라 고급 네트워킹 유형 간에 마이그레이션할 수 있습니다.

* 모든 환경에서 고급 네트워킹 비활성화
* 고급 네트워킹 인프라 삭제
* 올바른 값으로 고급 네트워킹 인프라 다시 생성
* 환경 수준의 고급 네트워킹 다시 활성화

>[!WARNING]
>
> 이 절차를 사용하면 삭제와 재생성 사이에 고급 네트워킹 서비스의 가동이 중단될 수 있습니다.
> 

가동 중단으로 인해 심각한 비즈니스 영향이 발생하는 경우 고객 지원 센터에 문의하여 이미 생성된 내용과 변경 이유를 설명하십시오.

## 추가 게시 지역에 대한 고급 네트워킹 구성 {#advanced-networking-configuration-for-additional-publish-regions}

추가 지역이 고급 네트워킹이 이미 구성된 환경에 추가되면 고급 네트워킹 규칙과 일치하는 추가 게시 지역의 트래픽이 기본 지역을 통해 기본적으로 라우팅합니다. 단, 기본 지역을 사용할 수 없을 경우 고급 네트워킹이 추가 지역에서 활성화되지 않으면 고급 네트워킹 트래픽이 삭제됩니다. 지역 중 하나가 작동이 중단된 경우 지연 시간을 최적화하고 가용성을 높이려면 추가 게시 지역의 고급 네트워킹을 활성화해야 합니다. 다음 섹션에서 서로 다른 두 가지 시나리오를 설명합니다.

>[!NOTE]
>
>모든 지역이 동일한 [환경 고급 네트워킹 구성](https://developer.adobe.com/experience-cloud/cloud-manager/reference/api/#tag/Environment-Advanced-Networking-Configuration)을 공유하므로 트래픽이 이그레스되는 지역에 따라 서로 다른 대상으로 트래픽을 라우팅할 수 없습니다.

### 전용 이그레스 IP 주소 {#additional-publish-regions-dedicated-egress}

#### 기본 지역에서 이미 활성화된 고급 네트워킹 {#already-enabled}

고급 네트워킹 구성이 기본 지역에서 이미 활성화된 경우 다음 단계를 수행합니다.

1. 전용 AEM IP 주소가 허용 목록에 추가되도록 인프라를 잠그면 해당 인프라에서 거부 규칙을 일시적으로 비활성화하는 것이 좋습니다. 이 작업이 완료되지 않으면 새 지역의 IP 주소의 요청이 짧은 기간 동안 자체 인프라에서 거부됩니다. 모든 AEM 지역이 동일한 FQDN(Fully Qualified Domain Name)에서 고급 네트워킹 트래픽을 이그레스하기 때문에(예: `p1234.external.adobeaemcloud.com`) FQDN을 통해 인프라를 잠그는 경우에는 해당되지 않습니다.
1. 고급 네트워킹 설명서에 따라 Cloud Manager Create Network Infrastructure API에 대한 POST 호출을 통해 이차 지역의 프로그램에서 설정한 네트워킹 인프라를 만듭니다. 기본 지역과 비교하여 페이로드 JSON 구성의 유일한 차이점은 지역 속성입니다.
1. AEM 트래픽 허용을 위해 IP를 통해 인프라를 잠가야 하는 경우 `p1234.external.adobeaemcloud.com`과 일치하는 IPS를 추가합니다. 지역별로 하나의 IPS가 있어야 합니다.

#### 모든 지역에서 아직 구성되지 않은 고급 네트워킹 {#not-yet-configured}

절차는 대부분 이전 지침과 유사합니다. 단, 프로덕션 환경이 고급 네트워킹에 대해 아직 활성화되지 않은 경우 스테이징 환경에서 먼저 활성화하여 구성을 테스트할 수 있습니다.

1. [Cloud Manager Create Network Infrastructure API](https://developer.adobe.com/experience-cloud/cloud-manager/reference/api/#tag/Network-infrastructure/operation/createNetworkInfrastructure)에 대한 POST 호출을 통해 모든 지역에 네트워킹 인프라를 만듭니다. 기본 지역과 비교하여 페이로드 JSON 구성의 유일한 차이점은 지역 속성입니다.
1. 스테이징 환경의 경우 `PUT api/program/{programId}/environment/{environmentId}/advancedNetworking`을 실행하여 환경에서 설정한 고급 네트워킹을 활성화하고 구성합니다. 자세한 내용은 [여기](https://developer.adobe.com/experience-cloud/cloud-manager/reference/api/#tag/Environment-Advanced-Networking-Configuration/operation/enableEnvironmentAdvancedNetworkingConfiguration)에서 API 설명서를 참조하십시오.
1. 필요한 경우, FQDN을 통해 외부 인프라를 잠급니다(예: `p1234.external.adobeaemcloud.com`). 그렇지 않으면 IP 주소를 통해 잠글 수 있습니다.
1. 스테이징 환경이 예상대로 작동하는 경우 프로덕션의 환경에서 설정한 고급 네트워킹 구성을 활성화하고 구성합니다.

#### VPN {#vpn-regions}

절차는 전용 이그레스 IP 주소 지침과 거의 동일합니다. 유일한 차이점은 지역 속성을 기본 지역과 다르게 구성하는 것 외에도 조직에서 운영하는 다른 VPN 엔드포인트로 라우팅하도록 `connections.gateway` 필드를 선택적으로 구성할 수 있다는 것입니다(새 지역에 지리적으로 더 가깝게).
