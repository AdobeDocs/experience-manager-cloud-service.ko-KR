---
title: AEM as a Cloud Service 고급 네트워킹 구성
description: AEM as a Cloud Service용 VPN 또는 전용 송신 IP 주소와 같은 고급 네트워킹 기능을 구성하는 방법을 알아봅니다.
source-git-commit: d37193833d784f3f470780b8f28e53b473fd4e10
workflow-type: tm+mt
source-wordcount: '2797'
ht-degree: 1%

---


# AEM as a Cloud Service 고급 네트워킹 구성 {#configuring-advanced-networking}

>[!INFO]
>
>고급 네트워킹 기능은 2021.9.0 릴리스의 일부이며, 10월 중순에 고객이 사용할 수 있도록 제공됩니다.

AEM as a Cloud Service은 Cloud Manager API를 사용하는 고객이 구성할 수 있는 몇 가지 유형의 고급 네트워킹 기능을 제공합니다. 이러한 쿠키에는 다음이 포함됩니다.

* [유연한 포트 송신](#flexible-port-egress)  - AEM as a Cloud Service을 구성하여 비표준 포트로부터 아웃바운드 트래픽을 허용합니다
* [전용 송신 IP 주소](#dedicated-egress-IP-address)  - 고유한 IP에서 시작되도록 AEM as a Cloud Service에서 트래픽을 구성합니다
* [가상 사설 네트워크](#vpn)  - VPN 기술을 보유한 고객을 위해 고객의 인프라와 AEM as a Cloud Service 간의 트래픽을 보호합니다.

이 문서에서는 구성 방법을 비롯하여 각 옵션에 대해 자세히 설명합니다. 일반적인 구성 전략으로서, `/networkInfrastructures` API 종단점은 프로그램 수준에서 호출되어 원하는 유형의 고급 네트워킹을 선언하고, 그런 다음 각 환경에 대해 `/advancedNetworking` 종단점을 호출하여 인프라를 활성화하고 환경별 매개 변수를 구성합니다. 각 공식 구문과 샘플 요청 및 응답에 대해 Cloud Manager API 설명서의 적절한 엔드포인트를 참조하십시오.

Adobe이 유연한 포트 송신 트래픽의 성능을 최적화할 수 있으므로 유연한 포트 송신 및 전용 송신 IP 주소 중 하나를 결정할 때 특정 IP 주소가 필요하지 않은 경우 유연한 포트 송신(flexible port 송신)을 선택하는 것이 좋습니다.

>[!INFO]
>
>샌드박스 프로그램에는 고급 네트워킹을 사용할 수 없습니다.

>[!NOTE]
>
>이미 기존 전용 송신 기술을 프로비저닝한 고객은 이러한 옵션 중 하나를 구성해야 하는 경우 그렇지 않아야 하거나 사이트 연결에 영향을 줄 수 있습니다. 도움이 필요하면 Adobe 지원 센터에 문의하십시오.

## 유연한 포트 송신 {#flexible-port-egress}

이 고급 네트워킹 기능을 사용하면 기본적으로 열려 있는 HTTP(포트 80) 및 HTTPS(포트 443) 이외의 포트를 통해 트래픽을 내보내도록 AEM as a Cloud Service을 구성할 수 있습니다.

### 고려 사항 {#flexible-port-egress-considerations}

VPN이 필요하지 않고 전용 송신 IP 주소가 필요하지 않은 경우, 전용 송신 포트에 의존하지 않는 트래픽은 처리량이 더 높을 수 있으므로 유연한 포트 송신 기능이 권장됩니다.

### 구성 {#configuring-flexible-port-egress-provision}

프로그램당 한 번 POST `/program/<programId>/networkInfrastructures` 종단점이 호출되고, `kind` 매개 변수 및 영역에 대해 `flexiblePortEgress` 값을 전달하기만 하면 됩니다. 엔드포인트는 `network_id` 과 상태를 포함한 기타 정보에 응답합니다. 전체 매개 변수 세트와 정확한 구문은 API 문서에서 참조해야 합니다.

호출되면 일반적으로 네트워킹 인프라를 프로비저닝하는 데 약 15분이 걸립니다. Cloud Manager의 [환경 GET 종단점에 대한 호출에는 &quot;ready&quot; 상태가 표시됩니다.](https://developer.adobe.com/experience-cloud/cloud-manager/reference/api/#operation/getEnvironment)

프로그램 범위의 유연한 포트 송신 구성이 준비되면 환경 수준에서 네트워킹을 활성화하고 포트 전달 규칙을 선언하려면 환경 별로 `PUT /program/<program_id>/environment/<environment_id>/advancedNetworking` 끝점을 호출해야 합니다. 매개 변수는 유연성을 제공하기 위해 환경별로 구성할 수 있습니다.

대상 호스트 집합(이름 또는 IP, 포트 포함)을 지정하여 80/443 이외의 포트에 대해 포트 전달 규칙을 선언해야 합니다. 각 대상 호스트의 경우 고객이 의도한 대상 포트를 30000에서 30999까지 포트에 매핑해야 합니다.

API는 업데이트 상태를 나타내는 몇 초 후에 응답해야 하며 약 10분 후에 끝점의 `GET` 메서드는 고급 네트워킹이 활성화되었음을 나타냅니다.

### 업데이트 {#updating-flexible-port-egress-provision}

프로그램 수준 구성은 `PUT /api/program/<program_id>/network/<network_id>` 끝점을 호출하여 업데이트할 수 있으며 몇 분 이내에 적용됩니다.

>[!NOTE]
>
> &quot;kind&quot; 매개 변수(`flexiblePortEgress`, `dedicatedEgressIP` 또는 `VPN`)는 수정할 수 없습니다. 고객 지원 센터에 문의하여 이미 생성한 내용과 변경 이유를 확인하십시오.

환경 포트 전달 규칙은 다시 `PUT /program/{programId}/environment/{environmentId}/advancedNetworking` 종단점을 호출하여 업데이트할 수 있습니다. 따라서 하위 세트가 아니라 전체 구성 매개 변수 세트를 포함해야 합니다.

### 유연한 포트 송신 삭제 또는 비활성화 {#deleting-disabling-flexible-port-egress-provision}

네트워크 인프라를 **삭제**&#x200B;하려면 고객 지원 티켓을 제출해서 생성한 내용과 삭제해야 하는 이유를 설명합니다.

특정 환경에서 **유연한 포트 송신 기능을 비활성화하려면 `DELETE [/program/{programId}/environment/{environmentId}/advancedNetworking]()`을 호출하십시오.**

자세한 내용은 [Cloud Manager API 설명서](https://developer.adobe.com/experience-cloud/cloud-manager/reference/api/#operation/disableEnvironmentAdvancedNetworkingConfiguration)를 참조하십시오.

### 트래픽 라우팅 {#flexible-port-egress-traffic-routing}

표준 Java 네트워킹 라이브러리가 사용된다고 가정할 때 포트 80 또는 443을 통해 대상으로 이동하는 Http 또는 https 트래픽은 사전 구성된 프록시를 통해 전달됩니다. 다른 포트를 통해 이동하는 http 또는 https 트래픽의 경우 다음 속성을 사용하여 프록시를 구성해야 합니다.

* `AEM_HTTP_PROXY_HOST / AEM_HTTPS_PROXY_HOST`
* `AEM_HTTP_PROXY_PORT / AEM_HTTPS_PROXY_PORT`

예를 들어 다음은 `www.example.com:8443`에 요청을 보내는 샘플 코드입니다.

```java
HttpsHost target = new HttpsHost("example.com", 8443, "https");
 
HttpHost proxy = new HttpHost(System.getenv("AEM_HTTPS_PROXY_HOST"),
                              Integer.parseInt(System.getenv("AEM_HTTPS_PROXY_PORT")),
                              "https");
 
RequestConfig config = RequestConfig.custom().setProxy(proxy).build();
 
HttpGet request = new HttpGet("/");
request.setConfig(config);
CloseableHttpResponse response = httpclient.execute(target, request);
```

비표준 Java 네트워킹 라이브러리를 사용하는 경우 모든 트래픽에 대해 위의 속성을 사용하여 프록시를 구성합니다.

`portForwards` 매개 변수에 선언된 포트를 통해 대상이 있는 비http/s 트래픽은 매핑된 포트와 함께 `AEM_PROXY_HOST` 라는 속성을 참조해야 합니다. 예:

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
    <th>예</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td><b>Http 또는 https 프로토콜</b></td>
    <td>표준 http/s 트래픽</td>
    <td>80 또는 443</td>
    <td>허용</td>
    <td></td>
  </tr> 
  <tr>
    <td></td>
    <td>이러한 환경 변수를 사용하여 구성된 http 프록시를 통해 비표준 트래픽(80 또는 443 외부의 다른 포트)입니다.<br><ul>
     <li>AEM_HTTP_PROXY_HOST / AEM_HTTPS_PROXY_HOST</li>
     <li>AEM_HTTP_PROXY_PORT / AEM_HTTPS_PROXY_PORT</li>
    </ul>
    <td>80 또는 443 이외의 포트</td>
    <td>허용</td>
  </tr>
  <tr>
    <td></td>
    <td>http 프록시를 사용하지 않는 비표준 트래픽(포트 80 또는 443 외부의 다른 포트에서)</td>
    <td>80 또는 443 이외의 포트</td>
    <td>차단됨</td>
    <td></td>
  </tr>
  <tr>
    <td><b>http가 아니거나 https가 아님</b></td>
    <td>클라이언트는 <code>portForwards</code> API 매개 변수에 선언된 <code>portOrig</code>을(를) 사용하여 <code>AEM_PROXY_HOST</code> 환경 변수에 연결합니다.</td>
    <td>임의</td>
    <td>허용</td>
    <td><code>mysql.example.com:3306</code></td>
  </tr>
  <tr>
    <td></td>
    <td>기타 모든 것</td>
    <td>임의</td>
    <td>차단됨</td>
    <td><code>db.example.com:5555</code></td>
  </tr>
</tbody>
</table>

**Apache/Dispatcher 구성**

AEM Cloud Service Apache/Dispatcher 계층의 `mod_proxy` 지시문은 위에 설명된 속성을 사용하여 구성할 수 있습니다.

```
ProxyRemote "http://example.com" "http://${AEM_HTTP_PROXY_HOST}:${AEM_HTTP_PROXY_PORT}"
ProxyPass "/somepath" "http://example.com"
ProxyPassReverse "/somepath" "http://example.com"
```

```
SSLProxyEngine on //needed for https backends
 
ProxyRemote "https://example.com:8443" "http://${AEM_HTTPS_PROXY_HOST}:${AEM_HTTPS_PROXY_PORT}"
ProxyPass "/somepath" "https://example.com:8443"
ProxyPassReverse "/somepath" "https://example.com:8443"
```

## 전용 송신 IP 주소 {#dedicated-egress-IP-address}

>[!NOTE]
>
>2021년 9월 릴리스(10/6/21) 이전에 전용 송신 IP가 제공된 경우 [기존 전용 송신 주소 고객](#legacy-dedicated-egress-address-customers)을(를) 참조하십시오.

### 이점 {#benefits}

이 전용 IP 주소는 IP 주소 AEM을 제공하는 as a Cloud Service 외부의 다른 통합이나 SaaS 공급업체(CRM 공급업체 등)와 통합할 때 보안을 향상시킬 수 허용 목록에 추가하다 있습니다. 전용 IP 주소를에 허용 목록에 추가하다 추가하면 고객의 AEM Cloud Service에서 들어오는 트래픽만 외부 서비스로 유입될 수 있습니다. 이는 허용되는 다른 IP의 트래픽 외에도 입니다.

전용 IP 주소 기능이 활성화되지 않은 경우 AEM as a Cloud Service에서 들어오는 트래픽은 다른 고객과 공유되는 IP 집합을 통해 전달됩니다.

### 구성 {#configuring-dedicated-egress-provision}

>[!INFO]
>
>전용 송신 IP 주소에서 Splunk 전달 기능을 사용할 수 없습니다.

전용 송신 IP 주소 구성은 [유연한 포트 송신](#configuring-flexible-port-egress-provision)과 동일합니다.

가장 큰 차이점은 트래픽이 항상 고유한 전용 IP에서 전송된다는 것입니다. 해당 IP를 찾으려면 DNS 확인자를 사용하여 `p{PROGRAM_ID}.external.adobeaemcloud.com`과(와) 연결된 IP 주소를 식별합니다. IP 주소는 변경되지 않지만 나중에 변경해야 하는 경우 고급 알림이 제공됩니다.

`PUT /program/<program_id>/environment/<environment_id>/advancedNetworking` 종단점의 유연한 포트 헤딩에서 지원하는 라우팅 규칙 외에도 전용 송신 IP 주소는 `nonProxyHosts` 매개 변수를 지원합니다. 이를 통해 전용 IP가 아닌 공유 IP 주소 범위를 통해 라우팅해야 하는 호스트 세트를 선언할 수 있습니다. 이 설정은 공유 IP를 통한 트래픽 유입이 더 최적화될 수 있으므로 유용할 수 있습니다. `nonProxyHost` URL은 `example.com` 또는 `*.example.com` 패턴을 따를 수 있습니다. 여기서 와일드카드는 도메인의 시작 시에만 지원됩니다.

유연한 포트 송신 IP 주소와 전용 송신 IP 주소 중 하나를 결정할 때 Adobe이 유연한 포트 송신 트래픽의 성능을 최적화할 수 있으므로 특정 IP 주소가 필요하지 않은 경우 유연한 포트 수신 옵션을 선택해야 합니다.

### 트래픽 라우팅 {#dedcated-egress-ip-traffic-routing}

<table>
<thead>
  <tr>
    <th>트래픽</th>
    <th>대상 조건</th>
    <th>포트</th>
    <th>연결</th>
    <th>예</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td><b>Http 또는 https 프로토콜</b></td>
    <td>Azure 또는 Adobe 서비스에 대한 트래픽</td>
    <td>임의</td>
    <td>공유 클러스터 IP(전용 IP 아님) 사용</td>
    <td>adobe.io<br>api.windows.net</td>
  </tr>
  <tr>
    <td></td>
    <td><code>nonProxyHosts</code> 매개 변수와 일치하는 호스트</td>
    <td>80 또는 443</td>
    <td>공유 클러스터 IP 사용</td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td><code>nonProxyHosts</code> 매개 변수와 일치하는 호스트</td>
    <td>80 또는 443 이외의 포트</td>
    <td>차단됨</td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td>http 프록시 구성을 통해 표준 Java HTTP 클라이언트 라이브러리를 사용하는 http/s 트래픽에 대해 기본적으로 구성되어 있습니다</td>
    <td>임의</td>
    <td>전용 송신 IP 사용</td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td>Http 프록시 구성을 무시합니다(예를 들어, 표준 Java HTTP 클라이언트 라이브러리에서 명시적으로 제거되었거나 표준 프록시 구성을 무시하는 Java 라이브러리를 사용하는 경우)</td>
    <td>80 또는 443</td>
    <td>공유 클러스터 IP 사용</td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td>Http 프록시 구성을 무시합니다(예를 들어, 표준 Java HTTP 클라이언트 라이브러리에서 명시적으로 제거되었거나 표준 프록시 구성을 무시하는 Java 라이브러리를 사용하는 경우)</td>
    <td>80 또는 443 이외의 포트</td>
    <td>차단됨</td>
    <td></td>
  </tr>
  <tr>
    <td><b>http가 아니거나 https가 아님</b></td>
    <td>클라이언트는 <code>portForwards</code> API 매개 변수에 선언된 <code>portOrig</code>을(를) 사용하여 <code>AEM_PROXY_HOST</code> env 변수에 연결합니다</td>
    <td>임의</td>
    <td>전용 송신 IP 사용</td>
    <td><code>mysql.example.com:3306</code></td>
  </tr>
  <tr>
    <td></td>
    <td>기타 정보</td>
    <td></td>
    <td>차단됨</td>
    <td></td>
  </tr>
</tbody>
</table>

## 기존 전용 송신 주소 고객 {#legacy-dedicated-egress-address-customers}

2021.09.30 전에 전용 송신 IP를 프로비저닝한 경우 전용 송신 IP 기능은 아래에 설명된 대로 작동합니다.

### 기능 사용 {#feature-usage}

프록시 구성에 표준 Java 시스템 속성을 사용하는 경우, 아웃바운드 트래픽을 발생하는 Java 코드 또는 라이브러리와 호환됩니다. 실제로 여기에는 가장 일반적인 라이브러리가 포함되어야 합니다.

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

일부 라이브러리는 프록시 구성에 표준 Java 시스템 속성을 사용하려면 명시적 구성이 필요합니다.

에 대한 명시적 호출이 필요한 Apache HttpClient를 사용하는 예
[`HttpClientBuilder.useSystemProperties()`](https://hc.apache.org/httpcomponents-client-4.5.x/current/httpclient/apidocs/org/apache/http/impl/client/HttpClientBuilder.html) 또는
[`HttpClients.createSystem()`](https://hc.apache.org/httpcomponents-client-4.5.x/current/httpclient/apidocs/org/apache/http/impl/client/HttpClients.html#createSystem()):

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

동일한 전용 IP는 Adobe 조직의 모든 고객 프로그램과 각 프로그램의 모든 환경에 적용됩니다. 이것은 작성자 및 게시 서비스 모두에 적용됩니다.

HTTP 및 HTTPS 포트만 지원됩니다. 여기에는 암호화된 경우 HTTP/1.1 및 HTTP/2가 포함됩니다.

### 디버깅 고려 사항 {#debugging-considerations}

예상되는 전용 IP 주소에서 트래픽이 실제로 전송되는지 확인하려면 대상 서비스의 로그(사용 가능한 경우)를 확인하십시오. 그렇지 않으면 호출 IP 주소를 반환하는 [https://ifconfig.me/IP](https://ifconfig.me/IP) 등의 디버깅 서비스를 호출하는 것이 유용할 수 있습니다.

## 가상 사설 네트워크(VPN) {#vpn}

VPN을 사용하면 작성자, 게시 또는 미리 보기에서 온-프레미스 인프라 또는 데이터 센터에 연결할 수 있습니다. 예를 들어, 데이터베이스에 액세스하는 수단의 경우

또한 VPN을 지원하거나 회사 네트워크에서 AEM as a Cloud Service 작성자, 미리 보기 또는 게시로 연결하는 CRM 공급업체와 같은 SaaS 공급업체에 연결할 수도 있습니다.

IPSec 기술을 사용하는 대부분의 VPN 장치가 지원됩니다. **RouteBased 구성 지침** 열의 정보를 기반으로 이 페이지](https://docs.microsoft.com/en-us/azure/vpn-gateway/vpn-gateway-about-vpn-devices#devicetable)에서 장치 목록을 참조하십시오. [ 표에 설명된 대로 장치를 구성합니다.

### 일반 고려 사항 {#general-vpn-considerations}

* 지원이 단일 VPN 연결로 제한됩니다
* VPN 연결을 통해 Splunk 전달 기능을 사용할 수 없습니다.

### 작품 {#vpn-creation}

프로그램당 한 번, POST `/program/<programId>/networkInfrastructures` 종단점이 호출되어 다음을 포함한 구성 정보의 페이로드를 전달합니다. `kind` 매개 변수, 영역, 주소 공간(CIDR 목록 - 나중에 수정할 수 없습니다. 참고 사항), DNS 확인기(고객 네트워크에서 이름 확인용) 및 VPN 연결 정보(게이트웨이 구성, 공유 VPN 키 및 IP 보안 정책 등)에 대한 &quot;vpn&quot;의 값입니다. 엔드포인트는 `network_id` 과 상태를 포함한 기타 정보에 응답합니다. 전체 매개 변수 세트와 정확한 구문은 [API 설명서](https://developer.adobe.com/experience-cloud/cloud-manager/reference/api/#operation/createNetworkInfrastructure)에서 참조되어야 합니다.

호출되면 일반적으로 네트워킹 인프라를 프로비저닝하는 데 45~60분 정도가 소요됩니다. API의 GET 메서드를 호출하여 현재 상태를 반환할 수 있습니다. 이 메서드는 결국 `creating`에서 `ready`(으)로 대칭 이동합니다. 모든 상태에 대해서는 API 설명서를 참조하십시오.

프로그램 범위 VPN 구성이 준비되면 환경 수준에서 네트워킹을 활성화하고 포트 전달 규칙을 선언하려면 환경 별로 `PUT /program/<program_id>/environment/<environment_id>/advancedNetworking` 끝점을 호출해야 합니다. 매개 변수는 유연성을 제공하기 위해 환경별로 구성할 수 있습니다.

자세한 내용은 [API 설명서](https://developer.adobe.com/experience-cloud/cloud-manager/reference/api/#operation/enableEnvironmentAdvancedNetworkingConfiguration)를 참조하십시오.

대상 호스트 집합(이름 또는 IP, 포트 포함)을 지정하여 VPN을 통해 라우팅해야 하는 비 http/s 프로토콜 TCP 트래픽에 대해 포트 전달 규칙을 선언해야 합니다. 각 대상 호스트의 경우 고객이 의도한 대상 포트를 30000에서 30999으로 포트에 매핑해야 합니다. 여기서 값은 프로그램의 환경에서 고유해야 합니다. 고객은 `nonProxyHosts` 매개 변수에 URL 세트를 나열할 수도 있습니다. 이 매개 변수에는 트래픽이 VPN 라우팅을 우회해야 하지만 대신 공유 IP 범위를 통해 이 URL을 선언합니다. 이 패턴은 `example.com` 또는 `*.example.com` 패턴을 따릅니다. 여기서 와일드카드는 도메인의 시작 시에만 지원됩니다.

API는 몇 초 후에 응답해야 합니다. 이 응답에는 `updating` 상태를 나타내고, 약 10분 후에 Cloud Manager의 환경 GET 종단점에 대한 호출에는 환경에 대한 업데이트가 적용되었음을 나타내는 `ready` 상태가 표시됩니다.

환경 트래픽 라우팅 규칙(호스트 또는 바이패스)이 없는 경우에도 빈 페이로드를 사용하여 `PUT /program/<program_id>/environment/<environment_id>/advancedNetworking`을 호출해야 합니다.

### VPN 업데이트 {#updating-the-vpn}

프로그램 수준 VPN 구성은 `PUT /api/program/<program_id>/network/<network_id>` 끝점을 호출하여 업데이트할 수 있습니다.

초기 VPN 프로비저닝 후에는 주소 공간을 변경할 수 없습니다. 필요한 경우 고객 지원에 문의하십시오. 또한 `kind` 매개 변수(`flexiblePortEgress`, `dedicatedEgressIP` 또는 `VPN`)는 수정할 수 없습니다. 고객 지원 센터에 문의하여 이미 생성한 내용과 변경 이유를 확인하십시오.

환경별 라우팅 규칙은 다시 `PUT /program/{programId}/environment/{environmentId}/advancedNetworking` 종단점을 호출하여 업데이트할 수 있습니다. 따라서 하위 집합이 아니라 전체 구성 매개 변수 집합을 포함해야 합니다. 환경 업데이트를 적용하는 데 일반적으로 5~10분이 소요됩니다.

### VPN 삭제 또는 사용 안 함 {#deleting-or-disabling-the-vpn}

네트워크 인프라를 삭제하려면 생성된 내용과 삭제해야 하는 이유를 설명하는 고객 지원 티켓을 제출하십시오.

특정 환경에 대한 VPN을 사용하지 않도록 설정하려면 `DELETE /program/{programId}/environment/{environmentId}/advancedNetworking`을 호출하십시오. [API 설명서](https://developer.adobe.com/experience-cloud/cloud-manager/reference/api/#operation/disableEnvironmentAdvancedNetworkingConfiguration)의 자세한 내용을 참조하십시오.

### 트래픽 라우팅 {#vpn-traffic-routing}

아래 표에서는 트래픽 라우팅에 대해 설명합니다.

<table>
<thead>
  <tr>
    <th>트래픽</th>
    <th>대상 조건</th>
    <th>포트</th>
    <th>연결</th>
    <th>예</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td><b>Http 또는 https 프로토콜</b></td>
    <td>Azure 또는 Adobe 서비스에 대한 트래픽</td>
    <td>임의</td>
    <td>공유 클러스터 IP(전용 IP 아님) 사용</td>
    <td>adobe.io<br>api.windows.net</td>
  </tr>
  <tr>
    <td></td>
    <td><code>nonProxyHosts</code> 매개 변수와 일치하는 호스트</td>
    <td>80 또는 443</td>
    <td>공유 클러스터 IP 사용</td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td><code>nonProxyHosts</code> 매개 변수와 일치하는 호스트</td>
    <td>80 또는 443 이외의 포트</td>
    <td>차단됨</td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td>IP가 <i>VPN 게이트웨이 주소</i> 공간 범위 및 http 프록시 구성(표준 Java HTTP 클라이언트 라이브러리를 사용하는 http/s 트래픽에 대해 기본적으로 구성됨)을 통해 전달되는 경우</td>
    <td>임의</td>
    <td>VPN 사용</td>
    <td><code>10.0.0.1:443</code>호스트 이름일 수도 있습니다.</td>
  </tr>
  <tr>
    <td></td>
    <td>IP가 <i>VPN 게이트웨이 주소 공간</i> 범위 및 http 프록시 구성(표준 Java HTTP 클라이언트 라이브러리를 사용하는 http/s 트래픽에 대해 기본적으로 구성됨)을 사용하지 않는 경우</td>
    <td>임의</td>
    <td>전용 송신 IP 사용</td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td>Http 프록시 구성을 무시합니다(예를 들어, 표준 Java HTTP 클라이언트 라이브러리에서 명시적으로 제거된 경우 또는 표준 프록시 구성을 무시하는 Java 라이브러리를 사용하는 경우)
</td>
    <td>80 또는 443</td>
    <td>공유 클러스터 IP 사용</td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td>Http 프록시 구성을 무시합니다(예를 들어, 표준 Java HTTP 클라이언트 라이브러리에서 명시적으로 제거된 경우 또는 표준 프록시 구성을 무시하는 Java 라이브러리를 사용하는 경우)</td>
    <td>80 또는 443 이외의 포트</td>
    <td>차단됨</td>
    <td></td>
  </tr>
  <tr>
    <td><b>http가 아니거나 https가 아님</b></td>
    <td>IP가 <i>VPN 게이트웨이 주소 공간</i> 범위에 속하고 클라이언트가 <code>portForwards</code> API 매개 변수에 선언된 <code>portOrig</code>를 사용하여 <code>AEM_PROXY_HOST</code> env 변수에 연결하는 경우</td>
    <td>임의</td>
    <td>VPN 사용</td>
    <td><code>10.0.0.1:3306</code>호스트 이름일 수도 있습니다.</td>
  </tr>
  <tr>
    <td></td>
    <td>IP가 <i>VPN 게이트웨이 주소 공간</i> 범위에 속하지 않고 <code>portForwards</code> API 매개 변수에 선언된 <code>portOrig</code>을 사용하여 클라이언트가 <code>AEM_PROXY_HOST</code> env 변수에 연결하는 경우</td>
    <td>임의</td>
    <td>전용 송신 IP 사용</td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td>기타 정보</td>
    <td>임의</td>
    <td>차단됨</td>
    <td></td>
  </tr>
</tbody>
</table>

### 구성에 유용한 도메인{#vpn-useful-domains-for-configuration}

아래 다이어그램은 구성 및 개발에 유용한 도메인 및 관련 IP 세트를 시각적으로 보여줍니다. 다이어그램 아래 표에서는 해당 도메인 및 IP에 대해 설명합니다.

![VPN 도메인 구성](/help/security/assets/AdvancedNetworking.jpg)

<table>
<thead>
  <tr>
    <th>도메인 패턴</th>
    <th>송신(AEM에서) 의미</th>
    <th>수신(AEM에) 의미</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td><code>p{PROGRAM_ID}.external.adobeaemcloud.com</code></td>
    <td>비공개 네트워크를 통해 인터넷에 이동하는 트래픽에 대한 전용 송신 IP 주소 </td>
    <td>VPN의 연결은 이 IP에서 온 것처럼 CDN에 표시됩니다. VPN의 연결만 AEM으로 이동할 수 있도록 하려면 이 IP만 허용하도록 Cloud Manager를 구성하여 다른 모든 것을 차단하십시오. 자세한 내용은 "VPN 연결로 수신 제한" 섹션을 참조하십시오.</td>
  </tr>
  <tr>
    <td><code>p{PROGRAM_ID}-gateway.external.adobeaemcloud.com</code></td>
    <td>N/A</td>
    <td>AEM 측에 있는 VPN 게이트웨이의 IP입니다. 고객의 네트워크 엔지니어링 팀은 이를 사용하여 특정 IP 주소에서 VPN 게이트웨이에 대한 VPN 연결만 허용할 수 있습니다. </td>
  </tr>
  <tr>
    <td><code>p{PROGRAM_ID}.inner.adobeaemcloud.net</code></td>
    <td>VPN의 AEM 측에서 고객 측으로 들어오는 트래픽의 IP입니다. 고객의 구성에서 허용 목록에추가된으로 이러한 연결을 AEM에서만 연결할 수 있도록 할 수 있습니다.</td>
    <td>고객이 AEM에 대한 VPN 액세스만 허용하려면 CNAME DNS 항목을 구성하여 <code>author-p{PROGRAM_ID}-e{ENVIRONMENT_ID}.adobeaemcloud.com</code> 및/또는 <code>publish-p{PROGRAM_ID}-e{ENVIRONMENT_ID}.adobeaemcloud.com</code>을 이 항목에 매핑해야 합니다.</td>
  </tr>
</tbody>
</table>

### VPN을 수신 연결로 제한 {#restrict-vpn-to-ingress-connections}

AEM에 대한 VPN 액세스만 허용하려면 Cloud Manager에서 환경 허용 목록을 구성하여 `p{PROGRAM_ID}.external.adobeaemcloud.com`에 의해 정의된 IP만 환경에 통신할 수 있도록 합니다. 이 작업은 Cloud Manager의 다른 IP 기반과 허용 목록에 추가하다 동일한 방식으로 수행할 수 있습니다.

규칙이 경로 기반이어야 하는 경우 dispatcher 수준에서 표준 http 지시어를 사용하여 특정 IP를 거부하거나 허용합니다. 또한 원하는 경로가 CDN에서 캐시될 수 없으므로 요청이 항상 원본으로 이어지도록 해야 합니다.

**Httpd 구성 예**

```
Order deny,allow
Deny from all
Allow from 192.168.0.1
Header always set Cache-Control private
```

## 고급 네트워킹 유형 간 전환 {#transitioning-between-advanced-networking-types}

`kind` 매개 변수는 수정할 수 없으므로 고객 지원 센터에 연락하여 이미 만들어진 내용과 변경 이유를 설명하십시오.