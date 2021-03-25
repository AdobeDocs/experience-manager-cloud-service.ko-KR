---
title: AEM as a Cloud Service 개발 지침
description: AEM as a Cloud Service 개발 지침
translation-type: tm+mt
source-git-commit: e70135d7f59fc46c24f73f109d027f3536ffbbd7
workflow-type: tm+mt
source-wordcount: '2283'
ht-degree: 1%

---


# AEM as a Cloud Service 개발 지침 {#aem-as-a-cloud-service-development-guidelines}

Cloud Service으로 AEM에서 실행되는 코드는 항상 클러스터에서 실행 중임을 인식해야 합니다. 즉, 실행되는 인스턴스가 항상 두 개 이상 있습니다. 인스턴스는 언제든지 중단할 수 있으므로 특히 코드는 복원력이 있어야 합니다.

Cloud Service으로 AEM을 업데이트하는 동안 이전 코드와 새 코드가 동시에 실행되는 인스턴스가 있게 됩니다. 따라서 이전 코드는 새 코드로 만든 콘텐츠와 분리되지 않아야 하며 새 코드는 이전 컨텐츠를 처리할 수 있어야 합니다.
<!--

>[!NOTE]
> All of the best practices mentioned here hold true for on-premise deployments of AEM, if not stated otherwise. An instance can always stop due to various reasons. However, with Skyline it is more likely to happen therefore an instance stopping is the rule not an exception.

-->

클러스터에서 기본 인스턴스를 식별할 필요가 있는 경우 Apache Sling Discovery API를 사용하여 이를 감지할 수 있습니다.

## 메모리 상태 {#state-in-memory}

상태는 메모리에 유지되지 않고 보관소에 보관되어야 합니다. 그렇지 않으면 인스턴스가 중지되면 이 상태가 손실될 수 있습니다.

## 파일 시스템 {#state-on-the-filesystem}의 상태

인스턴스의 파일 시스템은 AEM에서 Cloud Service으로 사용해서는 안 됩니다. 디스크는 일시적으로 삭제되며, 인스턴스가 재생될 때 삭제됩니다. 단일 요청 처리와 관련하여 임시 스토리지에 파일 시스템을 제한적으로 사용할 수는 있지만 대용량 파일에 대해서는 남용되어서는 안 됩니다. 이는 리소스 사용량 할당량에 부정적인 영향을 미쳐 디스크 제한 사항이 발생할 수 있기 때문입니다.

파일 시스템 사용이 지원되지 않는 한 예를 들어, 게시 계층은 지속되어야 하는 모든 데이터를 장기 저장을 위해 외부 서비스로 발송해야 합니다.

## 관측 {#observation}

마찬가지로, 관측 이벤트 시 비동기 방식으로 발생하는 모든 작업은 로컬에서 실행되도록 보장할 수 없으므로 주의해야 합니다. 이는 JCR 이벤트와 Sling 리소스 이벤트 모두에 적용됩니다. 변경이 발생할 때 인스턴스가 삭제되고 다른 인스턴스로 대체될 수 있습니다. 해당 시점에서 활성 상태인 토폴로지의 다른 인스턴스는 해당 이벤트에 응답할 수 있습니다. 그러나 이번 사태는 지역적인 행사가 아니며 행사가 있을 때 진행중인 지도자 선거에도 적극적으로 지도자가 없을 수도 있다.

## 백그라운드 작업 및 긴 실행 작업 {#background-tasks-and-long-running-jobs}

백그라운드 작업으로 실행되는 코드는 실행 중인 인스턴스를 언제든지 중단할 수 있다고 간주해야 합니다. 따라서 코드는 복원력이 있어야 하며 대부분의 가져오기 다시 시작 가능 해야 합니다. 즉, 코드가 다시 실행될 경우 처음부터 다시 시작하지 않고 코드가 종료되는 지점으로부터 코드 가동이 다시 시작되어야 합니다. 이러한 유형의 코드에 대한 새로운 요구 사항은 아니지만, Cloud Service의 경우 인스턴스가 삭제될 가능성이 더 높습니다.

이를 최소화하려면 장기간에 걸친 작업은 가급적 뒤로 하고 최소한 재개는 수 있도록 해야 한다. 이러한 작업을 실행하는 경우, 적어도 한 번 이상 보증할 수 있으며 중단되는 경우 가능한 한 빨리 다시 실행됩니다. 그러나 처음부터 다시 시작해서는 안 될 것이다. 이러한 작업을 예약하려면 [Sling 작업](https://sling.apache.org/documentation/bundles/apache-sling-eventing-and-job-handling.html#jobs-guarantee-of-processing) 스케줄러를 다시 한 번 이상 실행하는 것이 가장 좋습니다.

실행을 보장할 수 없으므로 Sling Commons Scheduler를 사용하여 예약하면 안 됩니다. 일정이 좀 더 잡힐 것 같다.

마찬가지로, 관측 이벤트(JCR 이벤트 또는 Sling 리소스 이벤트)를 수행하는 것과 같이 비동기적으로 발생하는 모든 작업은 실행 여부를 보장할 수 없으므로 주의해야 합니다. 현재 AEM 배포에서는 이미 마찬가지입니다.

## 나가는 HTTP 연결 {#outgoing-http-connections}

나가는 모든 HTTP 연결은 적절한 연결 및 읽기 시간 제한을 설정하는 것이 좋습니다. 이러한 시간 초과를 적용하지 않는 코드의 경우 Cloud Service으로 AEM에서 실행되는 AEM 인스턴스는 전역 시간 초과를 적용합니다. 이러한 시간 초과 값은 연결 호출의 경우 10초, 다음 인기 있는 Java 라이브러리에서 사용하는 연결에 대한 읽기 호출에 대해 60초입니다.

Adobe에서는 HTTP 연결을 만들려면 제공된 [Apache HttpComponents Client 4.x 라이브러리](https://hc.apache.org/httpcomponents-client-ga/)를 사용하는 것이 좋습니다.

효과가 있는 것으로 알려져 있지만 스스로 종속성을 제공해야 할 수 있는 대체 항목은 다음과 같습니다.

* [java.net.](https://docs.oracle.com/javase/7/docs/api/java/net/URL.html) URL 및/또는  [java.net.URLConnection](https://docs.oracle.com/javase/7/docs/api/java/net/URLConnection.html) (AEM에서 제공)
* [Apache Commons HttpClient 3.x](https://hc.apache.org/httpclient-3.x/) (이전 버전이고 버전 4.x로 대체되므로 권장하지 않음)
* [확인 Http](https://square.github.io/okhttp/) (AEM에서 제공되지 않음)

## 클래식 UI 사용자 지정 없음 {#no-classic-ui-customizations}

Cloud Service으로 AEM은 타사 고객 코드에 대한 터치 UI만 지원합니다. 클래식 UI는 사용자 정의에 사용할 수 없습니다.

## 기본 이진 파일 방지 {#avoid-native-binaries}

런타임에 바이너리를 다운로드하거나 수정할 수 없습니다. 예를 들어 `jar` 또는 `tar` 파일의 압축을 풀 수 없습니다.

## Cloud Service {#no-streaming-binaries}(으)로 AEM을 통한 스트리밍 바이너리가 없습니다.

바이너리는 핵심 AEM 서비스 외부의 바이너리를 제공하는 CDN을 통해 액세스해야 합니다.

예를 들어 AEM 서비스의 임시 디스크에 바이너리를 다운로드하는 트리거인 `asset.getOriginal().getStream()`을 사용하지 마십시오.

## 역방향 복제 에이전트 없음 {#no-reverse-replication-agents}

게시에서 작성자로 되돌리기는 AEM에서 Cloud Service으로 지원되지 않습니다. 이러한 전략이 필요한 경우 게시 인스턴스의 팜 및 작성자 클러스터 간에 공유되는 외부 지속성 저장소를 사용할 수 있습니다.

## 앞으로 복제 에이전트를 포팅해야 할 수 있습니다. {#forward-replication-agents}

pub-sub 메커니즘을 통해 작성자에서 게시로 컨텐츠를 복제합니다. 사용자 지정 복제 에이전트는 지원되지 않습니다.

## 모니터링 및 디버깅 {#monitoring-and-debugging}

### 로그 {#logs}

로컬 개발의 경우 로그 항목은 `/crx-quickstart/logs` 폴더의 로컬 파일에 기록됩니다.

클라우드 환경에서 개발자는 Cloud Manager를 통해 로그를 다운로드하거나 명령줄 툴을 사용하여 로그를 추적할 수 있습니다.<!-- See the [Cloud Manager documentation](https://docs.adobe.com/content/help/en/experience-manager-cloud-manager/using/introduction-to-cloud-manager.html) for more details. Note that custom logs are not supported and so all logs should be output to the error log. -->

**로그 수준 설정**

클라우드 환경의 로그 수준을 변경하려면 Sling 로깅 OSGI 구성을 수정한 후 전체 재배포해야 합니다. 이는 즉각적이지 않으므로 많은 트래픽을 받는 프로덕션 환경에서 자세한 로그를 활성화하는 것에 주의하십시오. 앞으로 로그 수준을 더 빨리 변경하는 메커니즘이 있을 수 있습니다.

>[!NOTE]
>
>아래에 나열된 구성 변경 사항을 수행하려면 로컬 개발 환경에서 구성 변경 사항을 만든 다음 Cloud Service 인스턴스로 AEM에 푸시해야 합니다. 이 방법에 대한 자세한 내용은 [Cloud Service](/help/implementing/deploying/overview.md)으로 AEM에 배포를 참조하십시오.

**디버그 로그 수준 활성화**

기본 로그 수준은 INFO입니다. 즉, DEBUG 메시지는 기록되지 않습니다.
DEBUG 로그 수준을 활성화하려면

``` /libs/sling/config/org.apache.sling.commons.log.LogManager/org.apache.sling.commons.log.level ```

디버깅할 속성입니다. 로그 양이 많은 로그를 생성하므로 로그를 필요한 것보다 오래 DEBUG 로그 수준으로 남겨두지 마십시오.
디버그 파일의 한 줄은 일반적으로 DEBUG로 시작되며 로그 수준, 설치 프로그램 작업 및 로그 메시지를 제공합니다. 예:

``` DEBUG 3 WebApp Panel: WebApp successfully deployed ```

로그 수준은 다음과 같습니다.

| 0 | 치명적인 오류 | 작업이 실패하여 설치 프로그램을 계속할 수 없습니다. |
|---|---|---|
| 1 | 오류 | 작업이 실패했습니다. 설치가 진행되지만 CRX의 일부가 제대로 설치되지 않아 제대로 작동하지 않습니다. |
| 2 | 경고 | 작업에 성공했지만 문제가 발생했습니다. CRX는 제대로 작동하지 않거나 않을 수 있습니다. |
| 3 | 정보 | 작업이 성공했습니다. |

### 스레드 덤프 {#thread-dumps}

클라우드 환경의 스레드 덤프는 지속적으로 수집되지만 지금은 셀프 서비스 방식으로 다운로드할 수 없습니다. 한편 문제를 디버깅하는 데 스레드 덤프가 필요한 경우 정확한 시간 창을 지정하여 AEM 지원에 문의하십시오.

## CRX/DE Lite 및 개발자 콘솔 {#crxde-lite-and-developer-console}

### 로컬 개발 {#local-development}

로컬 개발의 경우 개발자는 CRXDE Lite(`/crx/de`) 및 AEM 웹 콘솔(`/system/console`)에 대한 모든 액세스 권한을 가집니다.

로컬 개발(SDK 사용)에서 `/apps` 및 `/libs`은(는) 직접 작성할 수 있으며, 이는 최상위 폴더를 변경할 수 없는 클라우드 환경과 다릅니다.

### AEM을 Cloud Service 개발 도구로 사용 {#aem-as-a-cloud-service-development-tools}

고객은 작성자 계층의 개발 환경에서 CRXDE lite에 액세스할 수 있지만 스테이지나 프로덕션은 액세스할 수 없습니다. 변경할 수 없는 저장소(`/libs`, `/apps`)를 런타임에 쓸 수 없으므로 이를 시도하면 오류가 발생합니다.

개발, 준비 및 프로덕션 환경을 위해 개발자 콘솔에서 AEM을 Cloud Service 개발자 환경으로 디버깅하기 위한 도구 세트를 사용할 수 있습니다. URL은 다음과 같이 작성자 또는 게시 서비스 URL을 조정하여 결정할 수 있습니다.

`https://dev-console/-<namespace>.<cluster>.dev.adobeaemcloud.com`

단축키로, 아래 설명된 환경 매개 변수를 기반으로 다음 Cloud Manager CLI 명령을 사용하여 개발자 콘솔을 시작할 수 있습니다.

`aio cloudmanager:open-developer-console <ENVIRONMENTID> --programId <PROGRAMID>`

자세한 내용은 [이 페이지](/help/release-notes/home.md)를 참조하십시오.

개발자는 상태 정보를 생성하고 다양한 리소스를 확인할 수 있습니다.

아래에 설명된 대로 사용 가능한 상태 정보에는 번들, 구성 요소, OSGI 구성, 오크 색인, OSGI 서비스 및 Sling 작업의 상태가 포함됩니다.

![개발 콘솔 1](/help/implementing/developing/introduction/assets/devconsole1.png)

아래 그림과 같이 개발자는 패키지 종속성 및 서비스를 해결할 수 있습니다.

![개발 콘솔 2](/help/implementing/developing/introduction/assets/devconsole2.png)

![개발 콘솔 3](/help/implementing/developing/introduction/assets/devconsole3.png)

디버깅에도 유용한 개발자 콘솔에는 쿼리 설명 도구에 대한 링크가 있습니다.

![개발 콘솔 4](/help/implementing/developing/introduction/assets/devconsole4.png)

프로덕션 프로그램의 경우, 개발자 콘솔에 대한 액세스는 Admin Console의 &quot;클라우드 관리자 - 개발자 역할&quot;에 의해 정의되고, 샌드박스 프로그램의 경우 개발자 콘솔을 모든 사용자가 AEM에 대한 Cloud Service에 액세스할 수 있는 제품 프로필을 사용할 수 있습니다. 모든 프로그램의 경우, 두 서비스의 상태 덤프 데이터를 보려면 &quot;Cloud Manager - Developer Role&quot;이 필요하며 작성자 및 게시 서비스 모두에서 AEM 사용자 또는 AEM 관리자 제품 프로필에 사용자가 정의되어 있어야 합니다. 사용자 권한 설정에 대한 자세한 내용은 [클라우드 관리자 설명서](https://docs.adobe.com/content/help/en/experience-manager-cloud-manager/using/requirements/setting-up-users-and-roles.html)를 참조하십시오.

### AEM 스테이징 및 프로덕션 서비스 {#aem-staging-and-production-service}

고객은 스테이징 및 프로덕션 환경을 위한 개발자 도구에 액세스할 수 없습니다.

### 성능 모니터링 {#performance-monitoring}

Adobe은 응용 프로그램 성능을 모니터하고 변동을 관찰하는 경우 이를 해결하기 위한 조치를 취합니다. 지금은 애플리케이션 지표를 검색할 수 없습니다.

## 전용 송신 IP 주소 {#dedicated-egress-ip-address}

요청 시, Cloud Service으로 AEM은 Java 코드에 프로그래밍된 HTTP(포트 80) 및 HTTPS(포트 443) 아웃바운드 트래픽에 대한 정적 전용 IP 주소를 제공합니다.

### 이점 {#benefits}

이 전용 IP 주소는 IP 주소 AEM을 제공하는 Cloud Service으로 SaaS 공급업체(예: CRM 공급업체)와 통합하거나 외부에서 다른 통합을 통합할 때 보안을 강화할 수 허용 목록에 추가하다 있습니다. 전용 IP 주소를에 추가하면 고객허용 목록에 추가하다의 AEM Cloud Service의 트래픽만 외부 서비스로 이동할 수 있습니다. 이는 허용되는 다른 IP의 트래픽 이외에도 됩니다.

전용 IP 주소 기능을 사용하지 않으면 Cloud Service이 다른 고객과 공유된 IP 세트를 통해로 AEM에서 나오는 트래픽입니다.

### 구성 {#configuration}

전용 IP 주소를 활성화하려면 IP 주소 정보를 제공하는 고객 지원 센터에 요청을 제출합니다. 요청은 초기 요청 이후 새 환경에 기능이 필요한 경우 각 환경을 지정해야 하며, 추가 요청은 해야 합니다. 샌드박스 프로그램 환경은 지원되지 않습니다.

### 기능 사용 {#feature-usage}

이 기능은 프록시 구성에 표준 Java 시스템 속성을 사용하는 경우 아웃바운드 트래픽을 발생시키는 Java 코드 또는 라이브러리와 호환됩니다. 실제로 대부분의 공용 라이브러리를 포함해야 합니다.

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

예상되는 전용 IP 주소에서 트래픽이 실제로 전송되는지 확인하려면, 가능한 경우 대상 서비스의 로그를 확인하십시오. 그렇지 않은 경우 호출 IP 주소를 반환하는 [https://ifconfig.me/ip](https://ifconfig.me/ip)과 같은 디버깅 서비스를 콜아웃하는 것이 유용할 수 있습니다.

## 이메일 {#sending-email} 보내기

Cloud Service으로 AEM을 사용하려면 아웃바운드 메일을 암호화해야 합니다. 아래 섹션에서는 이메일을 요청, 구성 및 보내는 방법에 대해 설명합니다.

### 액세스 요청 {#requesting-access}

기본적으로 아웃바운드 이메일은 비활성화됩니다. 정품 인증을 받으려면 다음을 사용하여 지원 티켓을 제출하십시오.

1. 메일 서버의 정규화된 도메인 이름(예: `smtp.sendgrid.net`)
1. 사용할 포트입니다. 메일 서버에서 지원하는 경우 포트 465이고, 그렇지 않은 경우 포트 587이어야 합니다. 포트 587은 메일 서버가 해당 포트에 TLS를 사용하고 적용하는 경우에만 사용할 수 있습니다
1. 메일 발송할 환경에 대한 프로그램 ID 및 환경 ID
1. 작성자, 게시 또는 둘 다에 SMTP 액세스 필요 여부.

### 이메일 보내기 {#sending-emails}

[Day CQ Mail Service OSGI 서비스](https://docs.adobe.com/content/help/en/experience-manager-65/administering/operations/notification.html#configuring-the-mail-service)를 사용하고 이메일을 수신자에게 직접 보내는 대신 지원 요청에 지정된 메일 서버로 보내야 합니다.

AEM CS는 포트 465를 통해 메일을 보내야 합니다. 메일 서버에서 포트 465를 지원하지 않는 경우 TLS 옵션이 활성화된 한 포트 587을 사용할 수 있습니다.

>[!NOTE]
>
>Adobe은 고유한 전용 IP 주소를 통한 SMTP 전송을 지원하지 않습니다.

### 구성 {#email-configuration}

AEM의 이메일은 [Day CQ Mail Service OSGi 서비스](https://docs.adobe.com/content/help/en/experience-manager-65/administering/operations/notification.html#configuring-the-mail-service)를 사용하여 보내야 합니다.

이메일 설정 구성에 대한 자세한 내용은 [AEM 6.5 설명서](https://docs.adobe.com/content/help/en/experience-manager-65/administering/operations/notification.html)를 참조하십시오. Cloud Service의 경우 `com.day.cq.mailer.DefaultMailService OSGI` 서비스를 다음과 같이 조정해야 합니다.

포트 465가 요청된 경우:

* `smtp.port`을(를) `465`로 설정
* `smtp.ssl`을(를) `true`로 설정

포트 587이 요청된 경우(메일 서버가 포트 465를 지원하지 않는 경우에만 허용됨):

* `smtp.port`을(를) `587`로 설정
* `smtp.ssl`을(를) `false`로 설정

`smtp.starttls` 속성은 런타임에 Cloud Service으로 AEM에 의해 적절한 값으로 자동 설정됩니다. 따라서 `smtp.tls`이 true로 설정된 경우 `smtp.startls`은 무시됩니다. `smtp.ssl`이(가) false로 설정된 경우 `smtp.starttls`이(가) true로 설정됩니다. 이것은 OSGI 구성에 설정된 `smtp.starttls` 값에 상관없이 동일합니다.
