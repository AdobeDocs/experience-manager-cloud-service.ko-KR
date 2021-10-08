---
title: AEM as a Cloud Service 개발 지침
description: AEM as a Cloud Service 개발 지침
exl-id: 94cfdafb-5795-4e6a-8fd6-f36517b27364
source-git-commit: c9ebeefa2a8707cbbf43df15cf90c10aadbba45f
workflow-type: tm+mt
source-wordcount: '2059'
ht-degree: 2%

---

# AEM as a Cloud Service 개발 지침 {#aem-as-a-cloud-service-development-guidelines}

AEM as a Cloud Service에서 실행되는 코드는 항상 클러스터에서 실행되고 있다는 것을 알고 있어야 합니다. 즉, 실행되는 인스턴스가 항상 두 개 이상 있습니다. 특정 시점에 인스턴스가 중지될 수 있으므로 코드는 복원력이 있어야 합니다.

AEM as a Cloud Service을 업데이트하는 동안 이전 코드와 새 코드가 동시에 실행되는 인스턴스가 있습니다. 따라서 이전 코드는 새 코드로 만든 콘텐츠로 나누면 안 되며, 새 코드는 이전 콘텐츠를 처리할 수 있어야 합니다.
<!--

>[!NOTE]
> All of the best practices mentioned here hold true for on-premise deployments of AEM, if not stated otherwise. An instance can always stop due to various reasons. However, with Skyline it is more likely to happen therefore an instance stopping is the rule not an exception.

-->

클러스터에서 기본 인스턴스를 식별해야 하는 경우 Apache Sling Discovery API를 사용하여 이를 감지할 수 있습니다.

## 메모리 상태 {#state-in-memory}

상태는 메모리에 유지되지 않고 리포지토리에 있어야 합니다. 그렇지 않으면 인스턴스가 중지되면 이 상태가 손실될 수 있습니다.

## 파일 시스템의 상태 {#state-on-the-filesystem}

인스턴스의 파일 시스템은 AEM as a Cloud Service에서 사용해서는 안 됩니다. 디스크가 사용 후 삭제되며 인스턴스가 재생될 때 삭제됩니다. 단일 요청 처리와 관련된 임시 스토리지에 파일 시스템을 제한적으로 사용할 수는 있지만 대규모 파일에 대해서는 악용되어서는 안 됩니다. 이는 리소스 사용 할당량에 부정적인 영향을 미쳐 디스크 제한 사항이 발생할 수 있기 때문입니다.

파일 시스템 사용이 지원되지 않는 예로서 게시 계층은 지속해야 하는 모든 데이터를 장기 보관을 위해 외부 서비스로 내보내야 합니다.

## 관찰 {#observation}

마찬가지로, 관찰 이벤트에 대한 동작과 같이 비동기적으로 발생하는 모든 것이므로 로컬에서 실행할 수 없으므로 주의하여 사용해야 합니다. JCR 이벤트 및 Sling 리소스 이벤트 모두에 대해 적용됩니다. 변경 시 인스턴스가 삭제되어 다른 인스턴스로 대체될 수 있습니다. 해당 시점에서 활성화된 토폴로지의 다른 인스턴스는 해당 이벤트에 응답할 수 있습니다. 그러나 이 경우 지역 행사가 아니며, 행사가 있을 때 진행 중인 지도자 선거에서도 어떠한 활성 지도자도 없을 수도 있습니다.

## 백그라운드 작업 및 장기 실행 작업 {#background-tasks-and-long-running-jobs}

백그라운드 작업으로 실행된 코드는 실행 중인 인스턴스를 언제든지 중지할 수 있다고 간주해야 합니다. 따라서 코드가 복원력이 있어야 하고 대부분의 가져오기 다시 시작할 수 있어야 합니다. 즉, 코드가 다시 실행되면 처음부터 다시 시작하지 않고 원래 상태로 유지한 곳에서 다시 시작하지 않아야 합니다. 이러한 종류의 코드에 대한 새로운 요구 사항은 아니지만 AEM as a Cloud Service에서 인스턴스가 삭제될 가능성이 높습니다.

이를 최소화하려면 장기실행 작업은 가급적 피할 수 있고, 최소한 재개는 가능하다. 이러한 작업을 실행하는 경우, 적어도 한 번 이상의 보증이 있으므로 중단되면 가능한 한 빨리 재실행됩니다. 그러나 처음부터 다시 시작하지 않아야 할 것이다. 이러한 작업을 예약하기 위해 [Sling 작업](https://sling.apache.org/documentation/bundles/apache-sling-eventing-and-job-handling.html#jobs-guarantee-of-processing) 스케줄러를 다시 한 번 이상 실행하는 것이 좋습니다.

실행을 보장할 수 없으므로 Sling Commons Scheduler를 예약에 사용하면 안 됩니다. 그것은 단지 일정이 잡힐 것 같습니다.

마찬가지로, 관찰 이벤트(JCR 이벤트 또는 Sling 리소스 이벤트 포함)에서 동작하는 것과 같이 비동기적으로 발생하는 모든 것을 사용하면 가 실행될 수 없으므로 주의해야 합니다. 현재 AEM 배포에 대해서는 이미 true입니다.

## 나가는 HTTP 연결 {#outgoing-http-connections}

나가는 모든 HTTP 연결은 적절한 연결 및 읽기 시간 제한을 설정하는 것이 좋습니다. 이러한 시간 초과를 적용하지 않는 코드의 경우, AEM as a Cloud Service에서 실행되는 AEM 인스턴스는 글로벌 시간 초과를 적용합니다. 이러한 시간 초과 값은 연결 호출의 경우 10초 및 다음의 일반적인 Java 라이브러리에서 사용하는 연결에 대한 읽기 호출의 60초입니다.

Adobe은 HTTP 연결을 만들려면 제공된 [Apache HttpComponents Client 4.x 라이브러리](https://hc.apache.org/httpcomponents-client-ga/)를 사용하는 것이 좋습니다.

잘 알려져 있지만, 직접 종속성을 제공해야 할 수 있는 대체 방법은 다음과 같습니다.

* [java.net.](https://docs.oracle.com/javase/7/docs/api/java/net/URL.html) URL 및/또는  [java.net.URLConnection](https://docs.oracle.com/javase/7/docs/api/java/net/URLConnection.html) (AEM에서 제공)
* [Apache Commons HttpClient 3.x](https://hc.apache.org/httpclient-3.x/) (오래된 버전이며 버전 4.x로 대체되었으므로 권장되지 않음)
* [OK Http](https://square.github.io/okhttp/) (AEM에서 제공하지 않음)

## 클래식 UI 사용자 지정 없음 {#no-classic-ui-customizations}

AEM as a Cloud Service은 타사 고객 코드에 대한 Touch UI만 지원합니다. 클래식 UI는 사용자 지정에 사용할 수 없습니다.

## 기본 바이너리 방지 {#avoid-native-binaries}

코드가 런타임에 바이너리를 다운로드하거나 수정할 수 없습니다. 예를 들어 `jar` 또는 `tar` 파일의 압축을 풀 수 없습니다.

## AEM as a Cloud Service을 통한 스트리밍 바이너리 없음 {#no-streaming-binaries}

코어 AEM 서비스 외부의 바이너리를 제공하는 CDN을 통해 바이너리에 액세스해야 합니다.

예를 들어, AEM 서비스의 사용 후 디스크에 바이너리 다운로드를 트리거하는 `asset.getOriginal().getStream()` 을 사용하지 마십시오.

## 역방향 복제 에이전트 없음 {#no-reverse-replication-agents}

게시에서 작성자로 역방향 복제는 AEM as a Cloud Service에서 지원되지 않습니다. 이러한 전략이 필요한 경우 게시 인스턴스의 팜 및 작성자 클러스터 간에 공유되는 외부 지속성 저장소를 사용할 수 있습니다.

## 앞으로 복제 에이전트를 포팅해야 할 수 있습니다. {#forward-replication-agents}

펍 하위 메커니즘을 통해 컨텐츠가 작성자에서 게시로 복제됩니다. 사용자 지정 복제 에이전트는 지원되지 않습니다.

## 모니터링 및 디버깅 {#monitoring-and-debugging}

### 로그 {#logs}

로컬 개발의 경우 로그 항목이 `/crx-quickstart/logs` 폴더의 로컬 파일에 기록됩니다.

클라우드 환경에서 개발자는 Cloud Manager를 통해 로그를 다운로드하거나 명령줄 도구를 사용하여 로그를 추적할 수 있습니다. <!-- See the [Cloud Manager documentation](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/introduction-to-cloud-manager.html) for more details. Note that custom logs are not supported and so all logs should be output to the error log. -->

**로그 수준 설정**

클라우드 환경의 로그 수준을 변경하려면 Sling 로깅 OSGI 구성을 수정한 후 전체 재배포해야 합니다. 이 작업은 순간적이지 않으므로 많은 트래픽을 받는 프로덕션 환경에서 세부 정보 로그를 활성화하는 것에 주의하십시오. 앞으로 로그 수준을 보다 빠르게 변경하는 메커니즘이 있을 수 있습니다.

>[!NOTE]
>
>아래 나열된 구성 변경 사항을 수행하려면 로컬 개발 환경에서 구성 요소를 만든 다음 AEM as a Cloud Service 인스턴스에 푸시해야 합니다. 이 작업을 수행하는 방법에 대한 자세한 내용은 [AEM as a Cloud Service](/help/implementing/deploying/overview.md)에 배포를 참조하십시오.

**디버그 로그 수준 활성화**

기본 로그 수준은 INFO, 즉 DEBUG 메시지는 기록되지 않습니다.
DEBUG 로그 레벨을 활성화하려면

``` /libs/sling/config/org.apache.sling.commons.log.LogManager/org.apache.sling.commons.log.level ```

디버그할 속성입니다. 로그를 많이 생성하므로 DEBUG 로그 수준에서 로그를 필요한 기간보다 오래 두지 마십시오.
디버그 파일의 한 줄은 일반적으로 DEBUG로 시작하며 로그 수준, 설치 관리자 작업 및 로그 메시지를 제공합니다. 예:

``` DEBUG 3 WebApp Panel: WebApp successfully deployed ```

로그 수준은 다음과 같습니다.

| 0 | 치명적인 오류 | 작업이 실패하여 설치 프로그램을 계속할 수 없습니다. |
|---|---|---|
| 1 | 오류 | 작업이 실패했습니다. 설치가 진행되지만 CRX 일부가 제대로 설치되지 않아 작동하지 않습니다. |
| 2 | 경고 | 작업에 성공했지만 문제가 발생했습니다. CRX가 제대로 작동하지 않을 수 있습니다. |
| 3 | 정보 | 작업이 성공했습니다. |

### 스레드 덤프 {#thread-dumps}

클라우드 환경의 스레드 덤프는 지속적으로 수집되지만 현재 셀프 서비스 방식으로 다운로드할 수 없습니다. 한편 문제를 디버깅하는 데 스레드 덤프가 필요한 경우 정확한 시간 기간을 지정하여 AEM 지원 센터에 문의하십시오.

## CRX/DE Lite 및 개발자 콘솔 {#crxde-lite-and-developer-console}

### 로컬 개발 {#local-development}

로컬 개발 시 개발자는 CRXDE Lite(`/crx/de`)와 AEM 웹 콘솔(`/system/console`)에 대한 전체 액세스 권한을 갖습니다.

로컬 개발(SDK 사용)에서 `/apps` 및 `/libs`에 직접 쓸 수 있으며, 이는 최상위 폴더를 변경할 수 없는 클라우드 환경과 다릅니다.

### AEM as a Cloud Service 개발 도구 {#aem-as-a-cloud-service-development-tools}

고객은 작성 계층의 개발 환경에서 CRXDE Lite에 액세스할 수 있지만, 스테이지나 프로덕션 환경에서는 액세스할 수 없습니다. 런타임 시에 변경할 수 없는 저장소(`/libs`, `/apps`)를 쓸 수 없으므로 작업을 시도하면 오류가 발생합니다.

AEM as a Cloud Service 개발자 환경을 디버깅하는 도구 세트는 개발자 콘솔에서 개발, 스테이지 및 프로덕션 환경에 사용할 수 있습니다. URL은 다음과 같이 작성자 또는 게시 서비스 URL을 조정하여 결정할 수 있습니다.

`https://dev-console/-<namespace>.<cluster>.dev.adobeaemcloud.com`

바로 가기를 사용하면 아래 설명된 환경 매개 변수를 기반으로 개발자 콘솔을 시작할 수 있습니다.

`aio cloudmanager:open-developer-console <ENVIRONMENTID> --programId <PROGRAMID>`

자세한 내용은 [이 페이지](/help/release-notes/home.md)를 참조하십시오.

개발자는 상태 정보를 생성하고 다양한 리소스를 해결할 수 있습니다.

아래 그림과 같이 사용 가능한 상태 정보에는 번들, 구성 요소, OSGI 구성, oak 색인, OSGI 서비스 및 Sling 작업의 상태가 포함됩니다.

![개발 콘솔 1](/help/implementing/developing/introduction/assets/devconsole1.png)

아래 그림과 같이 개발자는 패키지 종속성 및 서블릿을 해결할 수 있습니다.

![개발 콘솔 2](/help/implementing/developing/introduction/assets/devconsole2.png)

![개발 콘솔 3](/help/implementing/developing/introduction/assets/devconsole3.png)

디버깅에도 유용한 개발자 콘솔에는 쿼리 설명 도구에 대한 링크가 있습니다.

![개발 콘솔 4](/help/implementing/developing/introduction/assets/devconsole4.png)

프로덕션 프로그램의 경우 개발자 콘솔에 대한 액세스는 Admin Console의 &quot;Cloud Manager - 개발자 역할&quot;에 의해 정의되며, 샌드박스 프로그램의 경우 개발자 콘솔을 AEM as a Cloud Service에 액세스할 수 있는 제품 프로필이 있는 모든 사용자가 사용할 수 있습니다. 모든 프로그램의 경우, 상태 덤프에는 &quot;Cloud Manager - 개발자 역할&quot;이 필요하며, 두 서비스에서 상태 덤프 데이터를 보려면 작성자 및 게시 서비스 모두의 AEM 사용자 또는 AEM 관리자 제품 프로필에도 사용자가 정의되어 있어야 합니다. 사용자 권한 설정에 대한 자세한 내용은 [Cloud Manager 설명서](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/requirements/setting-up-users-and-roles.html)를 참조하십시오.

### AEM 스테이징 및 프로덕션 서비스 {#aem-staging-and-production-service}

고객은 스테이징 및 프로덕션 환경을 위한 개발자 도구에 액세스할 수 없습니다.

### 성능 모니터링 {#performance-monitoring}

Adobe은 응용 프로그램 성능을 모니터링하고 노후화가 확인되면 조치를 수행합니다. 현재는 애플리케이션 지표를 검색할 수 없습니다.

## 이메일 보내기 {#sending-email}

AEM as a Cloud Service을 사용하려면 아웃바운드 메일을 암호화해야 합니다. 아래 섹션에서는 이메일을 요청, 구성 및 전송하는 방법을 설명합니다.

>[!NOTE]
>
>메일 서비스는 OAuth2 지원을 사용하여 구성할 수 있습니다. 자세한 내용은 메일 서비스에 대한 [OAuth2 지원](/help/security/oauth2-support-for-mail-service.md)을 참조하십시오.

### 아웃바운드 이메일 활성화 {#enabling-outbound-email}

기본적으로 전송하는 데 사용되는 포트는 비활성화되어 있습니다. 이 기능을 활성화하려면 [고급 네트워킹](/help/security/configuring-advanced-networking.md)을 구성하여 필요한 각 환경에 대해 `PUT /program/<program_id>/environment/<environment_id>/advancedNetworking` 종단점의 포트 전달 규칙을 설정하여 트래픽이 포트 465(메일 서버에서 지원하는 경우) 또는 포트 587(메일 서버에 이 기능이 필요하고 해당 포트에서 TLS를 적용하는 경우)을 통과하도록 하십시오.

Adobe은 유연한 포트 송신 트래픽의 성능을 최적화할 수 있으므로 `kind` 매개 변수를 `flexiblePortEgress`로 설정하여 고급 네트워킹을 구성하는 것이 좋습니다. 고유 송신 IP 주소가 필요한 경우 `dedicatedEgressIp` 의 `kind` 매개 변수를 선택하십시오. 다른 이유로 이미 VPN을 구성한 경우 해당 고급 네트워킹 변형에서 제공하는 고유한 IP 주소도 사용할 수 있습니다.

전자 메일 클라이언트에 직접 이메일을 보내는 대신 메일 서버를 통해 전자 메일을 보내야 합니다. 그렇지 않으면 이메일이 차단될 수 있습니다.

### 전자 메일 보내기 {#sending-emails}

[일 CQ Mail Service OSGI 서비스](https://experienceleague.adobe.com/docs/experience-manager-65/administering/operations/notification.html#configuring-the-mail-service)를 사용하고 이메일을 수신자에게 직접 보내는 대신 지원 요청에 표시된 메일 서버로 보내야 합니다.

AEM as a Cloud Service은 포트 465를 통해 메일을 전송해야 합니다. 메일 서버가 포트 465를 지원하지 않는 경우 TLS 옵션이 활성화되어 있는 한 포트 587을 사용할 수 있습니다.

### 구성 {#email-configuration}

AEM의 이메일은 [일 CQ 메일 서비스 OSGi 서비스](https://experienceleague.adobe.com/docs/experience-manager-65/administering/operations/notification.html#configuring-the-mail-service)를 사용하여 전송해야 합니다.

전자 메일 설정 구성에 대한 자세한 내용은 [AEM 6.5 설명서](https://experienceleague.adobe.com/docs/experience-manager-65/administering/operations/notification.html)를 참조하십시오. AEM as a Cloud Service의 경우 `com.day.cq.mailer.DefaultMailService OSGI` 서비스를 다음과 같이 조정해야 합니다.

포트 465가 요청된 경우:

* `smtp.port`을 `465`(으)로 설정
* `smtp.ssl`을 `true`(으)로 설정

포트 587이 요청된 경우(메일 서버가 포트 465를 지원하지 않는 경우에만 허용됨):

* `smtp.port`을 `587`(으)로 설정
* `smtp.ssl`을 `false`(으)로 설정

`smtp.starttls` 속성은 런타임 시 AEM as a Cloud Service에서 적절한 값으로 자동 설정됩니다. 따라서 `smtp.tls`이 true로 설정된 경우 `smtp.startls`은 무시됩니다. `smtp.ssl`이 false로 설정된 경우 `smtp.starttls`이 true로 설정됩니다. 이는 OSGI 구성에 설정된 `smtp.starttls` 값에 관계없이 적용됩니다.

선택적으로 OAuth2 지원을 사용하여 메일 서비스를 구성할 수 있습니다. 자세한 내용은 메일 서비스에 대한 [OAuth2 지원](/help/security/oauth2-support-for-mail-service.md)을 참조하십시오.

## [!DNL Assets] 개발 지침 및 사용 사례 {#use-cases-assets}

Assets as a Cloud Service에 대한 개발 사용 사례, 권장 사항 및 참조 자료에 대해 알아보려면 [Assets](/help/assets/developer-reference-material-apis.md#assets-cloud-service-apis)에 대한 개발자 참조 를 참조하십시오.
