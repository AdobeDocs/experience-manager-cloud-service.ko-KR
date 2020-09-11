---
title: 클라우드 서비스로서의 AEM 개발 지침
description: 클라우드 서비스로서의 AEM 개발 지침
translation-type: tm+mt
source-git-commit: 1ebc4f833d4a01f1144c585dc71057f007031e43
workflow-type: tm+mt
source-wordcount: '1953'
ht-degree: 2%

---


# 클라우드 서비스로서의 AEM 개발 지침 {#aem-as-a-cloud-service-development-guidelines}

Cloud Service으로 AEM에서 실행되는 코드는 클러스터에서 항상 실행되고 있다는 사실을 알고 있어야 합니다. 즉, 실행되는 인스턴스가 항상 두 개 이상 있습니다. 특히 특정 시점에 인스턴스가 중지될 수 있으므로 코드는 복원력이 있어야 합니다.

AEM을 Cloud Service으로 업데이트하는 동안 이전 코드와 새 코드가 동시에 실행되는 인스턴스가 있게 됩니다. 따라서 이전 코드는 새 코드로 만들어진 컨텐츠와 구분해서는 안 되며 새 코드는 이전 컨텐츠를 처리할 수 있어야 합니다.
<!--

>[!NOTE]
> All of the best practices mentioned here hold true for on-premise deployments of AEM, if not stated otherwise. An instance can always stop due to various reasons. However, with Skyline it is more likely to happen therefore an instance stopping is the rule not an exception.

-->

클러스터에서 운영 체제를 식별할 필요가 있는 경우 Apache Sling Discovery API를 사용하여 이를 감지할 수 있습니다.

## 상태 인 메모리 {#state-in-memory}

상태는 메모리에 유지되지 않고 보관소에 보관되어야 합니다. 그렇지 않으면 인스턴스가 중지되면 이 상태가 손실될 수 있습니다.

## 파일 시스템의 상태 {#state-on-the-filesystem}

인스턴스의 파일 시스템은 AEM에서 Cloud Service으로 사용해서는 안 됩니다. 이 디스크는 일시적이며, 인스턴스가 재생될 때 폐기될 것이다. 단일 요청 처리와 관련된 임시 저장에 파일 시스템을 제한적으로 사용할 수는 있지만 대용량 파일에 악용되어서는 안 됩니다. 이는 리소스 사용량 할당량에 부정적인 영향을 줄 수 있고 디스크 제한 사항이 있기 때문입니다.

파일 시스템 사용이 지원되지 않는 예를 들어, 게시 계층은 지속되어야 하는 모든 데이터를 장기 보관을 위해 외부 서비스로 배송해야 합니다.

## 관찰 {#observation}

마찬가지로, 관측 이벤트 시 비동기 방식으로 발생하는 모든 작업을 통해, 로컬에서 실행되도록 보장할 수 없으므로 주의해야 합니다. 이는 JCR 이벤트와 Sling 리소스 이벤트 모두에 적용됩니다. 변경 시 인스턴스가 제거되고 다른 인스턴스로 대체될 수 있습니다. 해당 시간에 활성 상태인 토폴로지 내의 다른 인스턴스는 해당 이벤트에 응답할 수 있습니다. 그러나 이번 사건이 벌어지면 지방 사건이 아니어서 선거 때마다 지도자 연대가 없는 경우가 많다.

## 백그라운드 작업 및 긴 실행 작업 {#background-tasks-and-long-running-jobs}

백그라운드 작업으로 실행되는 코드는 실행 중인 인스턴스를 언제든지 중지할 수 있다고 간주해야 합니다. 따라서 코드가 복원력이 있어야 하며 가져오기 작업이 가능해야 합니다. 즉, 코드가 다시 실행될 경우 처음부터 다시 시작하지 않고 코드가 종료되는 부분에서 더 가까워야 합니다. 이러한 종류의 코드에 대한 새로운 요구 사항은 아니지만, AEM에서는 Cloud Service의 경우 인스턴스가 삭제될 가능성이 더 높습니다.

이를 최소화하려면 장기간에 걸친 작업은 가급적 뒤로 하고 최소한 재개해야 한다. 이러한 작업을 실행하는 경우, 적어도 한 번 보증이 있어 중단되는 경우 가능한 한 빨리 다시 실행됩니다. 그러나 처음부터 다시 시작해서는 안 될 것이다. 이러한 작업을 예약하려면 Sling 작업 [스케줄러를 다시 한 번](https://sling.apache.org/documentation/bundles/apache-sling-eventing-and-job-handling.html#jobs-guarantee-of-processing) 실행으로 사용하는 것이 가장 좋습니다.

실행을 보장할 수 없으므로 Sling Commons Scheduler를 사용하여 예약하면 안 됩니다. 일정이 더 잡힐 것 같다.

마찬가지로, 관측 이벤트(JCR 이벤트 또는 Sling 리소스 이벤트 포함)에 대한 작업과 같이 비동기적으로 발생하는 모든 것은 실행될 수 없으므로 주의해야 합니다. 현재 AEM 배포에서는 이미 마찬가지입니다.

## 나가는 HTTP 연결 {#outgoing-http-connections}

나가는 모든 HTTP 연결은 적절한 연결 및 읽기 시간 제한을 설정하는 것이 좋습니다. 이러한 시간 초과를 적용하지 않는 코드의 경우 Cloud Service으로 AEM에서 실행되는 AEM 인스턴스는 전역 시간 초과를 적용합니다. 이러한 시간 초과 값은 연결 호출의 경우 10초, 다음 인기 있는 Java 라이브러리에서 사용하는 연결에 대한 읽기 호출에 60초입니다.

Adobe은 HTTP 연결을 만들기 위해 제공된 [Apache HttpComponents Client 4.x 라이브러리를](https://hc.apache.org/httpcomponents-client-ga/) 사용하는 것이 좋습니다.

효과가 있지만 직접 종속성을 제공해야 할 수 있는 대체 방법은 다음과 같습니다.

* [java.net.URL](https://docs.oracle.com/javase/7/docs/api/java/net/URL.html) 및/ [또는 java.net.URLConnection](https://docs.oracle.com/javase/7/docs/api/java/net/URLConnection.html) (AEM 제공)
* [Apache Commons HttpClient 3.x](https://hc.apache.org/httpclient-3.x/) (이전 버전이고 버전 4.x로 대체되므로 권장되지 않음)
* [OK Http](https://square.github.io/okhttp/) (AEM에서 제공되지 않음)

## 클래식 UI 사용자 정의 없음 {#no-classic-ui-customizations}

AEM은 Cloud Service로서 타사 고객 코드에 대해서만 터치 UI를 지원합니다. 클래식 UI는 사용자 정의에 사용할 수 없습니다.

## 네이티브 바이너리 방지 {#avoid-native-binaries}

런타임에 바이너리를 다운로드하거나 수정할 수 없습니다. 예를 들어, 파일 `jar` 이나 파일의 압축을 풀 수 `tar` 없습니다.

## AEM을 통해 Cloud Service으로 바이너리를 스트리밍하지 않음 {#no-streaming-binaries}

바이너리는 핵심 AEM 서비스 외부의 바이너리를 제공하는 CDN을 통해 액세스해야 합니다.

예를 들어, AEM 서비스 `asset.getOriginal().getStream()`의 임시 디스크에 바이너리를 다운로드하는 트리거인 바이너리를 사용하지 마십시오.

## 역방향 복제 에이전트 없음 {#no-reverse-replication-agents}

게시에서 작성자로 역 복제는 AEM에서 Cloud Service으로 지원되지 않습니다. 이러한 전략이 필요한 경우 게시 인스턴스의 팜 및 작성자 클러스터 간에 공유되는 외부 지속성 저장소를 사용할 수 있습니다.

## 포팅해야 할 수도 있습니다. {#forward-replication-agents}

pub-sub 메커니즘을 통해 작성자에서 게시로 컨텐츠를 복제할 수 있습니다. 사용자 지정 복제 에이전트는 지원되지 않습니다.

## 모니터링 및 디버깅 {#monitoring-and-debugging}

### 로그 {#logs}

로컬 개발의 경우 로그 항목은 `/crx-quickstart/logs` 폴더의 로컬 파일에 기록됩니다.

클라우드 환경에서 개발자는 Cloud Manager를 통해 로그를 다운로드하거나 명령줄 툴을 사용하여 로그를 추적할 수 있습니다. <!-- See the [Cloud Manager documentation](https://docs.adobe.com/content/help/en/experience-manager-cloud-manager/using/introduction-to-cloud-manager.html) for more details. Note that custom logs are not supported and so all logs should be output to the error log. -->

**로그 수준 설정**

클라우드 환경의 로그 수준을 변경하려면 Sling Logging OSGI 구성을 수정한 후 전체 재배포해야 합니다. 이는 즉각적이지는 않으므로 많은 트래픽을 받는 프로덕션 환경에서 자세한 로그를 활성화하는 것에 주의하십시오. 앞으로 로그 수준을 보다 빠르게 변경하는 메커니즘이 있을 수 있습니다.

>[!NOTE]
>
>아래에 나열된 구성 변경 사항을 수행하려면 로컬 개발 환경에서 구성 변경 사항을 만든 다음 AEM에 Cloud Service 인스턴스로 푸시해야 합니다. 이 방법에 대한 자세한 내용은 AEM에 Cloud Service [로 배포를 참조하십시오](/help/implementing/deploying/overview.md).

**디버그 로그 수준 활성화**

기본 로그 수준은 INFO입니다. 즉, DEBUG 메시지는 기록되지 않습니다.
디버그 로그 수준을 활성화하려면

``` /libs/sling/config/org.apache.sling.commons.log.LogManager/org.apache.sling.commons.log.level ```

property to debug. 로그를 많은 로그를 생성하므로 로그를 필요 이상으로 길게 DEBUG 로그 수준으로 남겨두지 마십시오.
디버그 파일의 한 줄은 대개 DEBUG로 시작하고 로그 수준, 설치 프로그램 작업 및 로그 메시지를 제공합니다. 예:

``` DEBUG 3 WebApp Panel: WebApp successfully deployed ```

로그 수준은 다음과 같습니다.

| 0 | 치명적인 오류 | 작업이 실패했으며 설치 관리자를 계속할 수 없습니다. |
|---|---|---|
| 1 | 오류 | 작업이 실패했습니다. 설치가 진행되지만 CRX의 일부가 올바르게 설치되지 않아 작동하지 않습니다. |
| 2 | 경고 | 작업에 성공했지만 문제가 발생했습니다. CRX가 제대로 작동하지 않거나 작동하지 않을 수 있습니다. |
| 3 | 정보 | 그 행동은 성공했다. |

### 스레드 덤프 {#thread-dumps}

클라우드 환경의 스레드 덤프는 지속적으로 수집되지만 지금은 셀프 서비스 방식으로 다운로드할 수 없습니다. 한편 문제를 디버깅하는 데 스레드 덤프가 필요한 경우 정확한 시간 창을 지정하여 AEM 지원에 문의하십시오.

## CRX/DE Lite 및 시스템 콘솔 {#crxde-lite-and-system-console}

### 로컬 개발 {#local-development}

로컬 개발의 경우 개발자는 CRXDE Lite(`/crx/de`)와 AEM 웹 콘솔(`/system/console`)에 대한 모든 액세스 권한을 가집니다.

로컬 개발 시(클라우드 지원 빠른 시작 사용) `/apps` 에 직접 작성할 `/libs` 수 있으며 최상위 폴더를 변경할 수 없는 클라우드 환경과는 다릅니다.

### AEM as a Cloud Service Development tools {#aem-as-a-cloud-service-development-tools}

고객은 개발 환경에서 CRXDE lite에 액세스할 수 있지만 스테이지나 프로덕션은 액세스할 수 없습니다. 실행 시 변경 불가능한 저장소(`/libs`, `/apps`)를 쓸 수 없으므로 작성하려고 하면 오류가 발생합니다.

개발, 준비 및 프로덕션 환경을 위해 개발자 콘솔에서 AEM을 Cloud Service 개발자 환경으로 디버깅하는 도구 세트를 사용할 수 있습니다. URL은 다음과 같이 작성자 또는 게시 서비스 URL을 조정하여 결정할 수 있습니다.

`https://dev-console/-<namespace>.<cluster>.dev.adobeaemcloud.com`

바로 가기 키, 아래 설명된 환경 매개 변수를 기반으로 다음 Cloud Manager CLI 명령을 사용하여 개발자 콘솔을 시작할 수 있습니다.

`aio cloudmanager:open-developer-console <ENVIRONMENTID> --programId <PROGRAMID>`

자세한 내용은 [이 페이지를](/help/release-notes/home.md) 참조하십시오.

개발자는 상태 정보를 생성하고 다양한 리소스를 해결할 수 있습니다.

아래 그림에서와 같이 사용 가능한 상태 정보에는 번들, 구성 요소, OSGI 구성, 오크 인덱스, OSGI 서비스 및 Sling 작업의 상태가 포함됩니다.

![개발 콘솔 1](/help/implementing/developing/introduction/assets/devconsole1.png)

아래 그림과 같이 개발자는 패키지 종속성 및 서비스를 해결할 수 있습니다.

![개발 콘솔 2](/help/implementing/developing/introduction/assets/devconsole2.png)

![개발 콘솔 3](/help/implementing/developing/introduction/assets/devconsole3.png)

디버깅에도 유용한 개발자 콘솔에는 쿼리 설명 도구에 대한 링크가 있습니다.

![개발 콘솔 4](/help/implementing/developing/introduction/assets/devconsole4.png)

일반 프로그램의 경우, 개발자 콘솔에 대한 액세스는 Admin Console의 &quot;클라우드 관리자 - 개발자 역할&quot;에 의해 정의되고, 샌드박스 프로그램의 경우, 개발자 콘솔은 AEM에 대한 Cloud Service 액세스를 제공하는 제품 프로필을 가진 모든 사용자가 사용할 수 있습니다. 모든 프로그램의 경우, 상태 덤프에 대해 &quot;Cloud Manager - Developer Role&quot;이 필요하며 두 서비스의 상태 덤프 데이터를 보려면 작성자 및 게시 서비스 모두에서 AEM 사용자 또는 AEM 관리자 제품 프로필에 사용자가 정의되어 있어야 합니다. 사용자 권한 설정에 대한 자세한 내용은 [Cloud Manager 설명서를 참조하십시오](https://docs.adobe.com/content/help/en/experience-manager-cloud-manager/using/requirements/setting-up-users-and-roles.html).


### AEM 스테이징 및 프로덕션 서비스 {#aem-staging-and-production-service}

고객은 스테이징 및 프로덕션 환경을 위한 개발자 도구에 액세스할 수 없습니다.

### 성능 모니터링 {#performance-monitoring}

Adobe은 응용 프로그램 성능을 모니터링하고 변치 여부를 처리하는 조치를 수행합니다. 현재는 애플리케이션 지표를 검색할 수 없습니다.

## 전용 송신 IP 주소 {#dedicated-egress-ip-address}

요청이 있을 경우, AEM은 Java 코드로 프로그래밍된 HTTP(포트 80) 및 HTTPS(포트 443) 아웃바운드 트래픽에 대한 정적 전용 IP 주소를 제공합니다.

### 이점 {#benefits}

이 전용 IP 주소는 SaaS 공급업체(예: CRM 공급업체)와 통합하거나 IP 주소 AEM을 제공하는 Cloud Service으로 외부에서 다른 통합을 할 때 보안을 강화할 수 허용 목록에 추가하다 있습니다. 전용 IP 주소를에 허용 목록에 추가하다 추가하면 고객의 AEM Cloud Service의 트래픽만 외부 서비스로 이동할 수 있습니다. 이는 허용된 다른 IP의 트래픽 외에 추가됩니다.

전용 IP 주소 기능을 사용하지 않으면 Cloud Service이 다른 고객과 공유된 IP 세트를 통해 AEM에서 나오는 트래픽입니다.

### 구성 {#configuration}

전용 IP 주소를 활성화하려면 고객 지원 센터에 요청을 제출하여 IP 주소 정보를 제공합니다. 요청은 초기 요청 이후 새 환경에 기능이 필요한 경우 각 환경을 지정해야 하고 추가 요청을 해야 합니다. 샌드박스 프로그램 환경은 지원되지 않습니다.

### 기능 사용 {#feature-usage}

이 기능은 프록시 구성에 표준 Java 시스템 속성을 사용하는 경우 아웃바운드 트래픽을 발생하는 Java 코드 또는 라이브러리와 호환됩니다. 실제로 대부분의 공용 라이브러리를 포함해야 합니다.

다음은 코드 샘플입니다.

```
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

동일한 전용 IP가 Adobe 조직의 모든 프로그램과 각 프로그램의 모든 환경에 적용됩니다. 작성자 및 게시 서비스 모두에 적용됩니다.

HTTP 및 HTTPS 포트만 지원됩니다. 여기에는 HTTP/1.1뿐만 아니라 암호화 시 HTTP/2도 포함됩니다.

### 디버깅 고려 사항 {#debugging-considerations}

예상되는 전용 IP 주소에서 트래픽이 실제로 전송되는지 확인하려면, 가능한 경우 대상 서비스에서 로그를 확인하십시오. 그렇지 않으면 호출 IP 주소를 반환하는 [https://ifconfig.me/ip과](https://ifconfig.me/ip)같은 디버깅 서비스로 전화하는 것이 유용할 수 있습니다.
