---
title: AEM as a Cloud Service 개발 지침
description: AEM as a Cloud Service 개발에 대한 지침과 AMS의 AEM On-Premise 및 AEM과 다른 중요한 방식에 대해 알아봅니다.
exl-id: 94cfdafb-5795-4e6a-8fd6-f36517b27364
source-git-commit: 6a26006a20ed2f1d18ff376863b3c8b149de1157
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# AEM as a Cloud Service 개발 지침 {#aem-as-a-cloud-service-development-guidelines}

>[!CONTEXTUALHELP]
>id="development_guidelines"
>title="AEM as a Cloud Service 개발 지침"
>abstract="AEM as a Cloud Service 개발에 대한 지침과 AMS의 AEM On-Premise 및 AEM과 다른 중요한 방식에 대해 알아봅니다."
>additional-url="https://video.tv.adobe.com/v/330555/" text="패키지 구조 데모"

이 문서에서는 AEM에서 as a Cloud Service으로 개발하기 위한 지침 및 AMS의 AEM 온프레미스 및 AEM과 차이가 있는 중요한 방법에 대해 설명합니다.

## 코드는 클러스터를 인식해야 합니다. {#cluster-aware}

AEMas a Cloud Service 에서 실행되는 코드는 항상 클러스터에서 실행되고 있음을 인식해야 합니다. 즉, 실행되는 인스턴스가 항상 두 개 이상 있습니다. 특히 인스턴스가 언제든지 중지될 수 있으므로 코드는 복원력이 있어야 합니다.

AEM을 as a Cloud Service으로 업데이트하는 동안 이전 코드와 새 코드가 동시에 실행되는 인스턴스가 있습니다. 따라서 이전 코드는 새 코드로 만든 콘텐츠와 분리해서는 안 되며, 새 코드는 이전 콘텐츠를 처리할 수 있어야 합니다.

클러스터에서 기본 을 식별해야 하는 경우 Apache Sling Discovery API를 사용하여 이를 감지할 수 있습니다.

## 메모리 상태 {#state-in-memory}

상태는 메모리에 유지되지 않고 저장소에 유지되어야 합니다. 그렇지 않으면 인스턴스가 중지되면 이 상태가 손실될 수 있습니다.

## 파일 시스템의 상태 {#state-on-the-filesystem}

인스턴스의 파일 시스템을 AEM as a Cloud Service으로 사용하면 안 됩니다. 디스크는 사용 후 삭제되며 인스턴스가 재활용될 때 삭제됩니다. 단일 요청 처리와 관련된 임시 스토리지에 파일 시스템을 제한적으로 사용할 수 있지만 대용량 파일에 대해 남용되어서는 안 됩니다. 리소스 사용 할당량에 부정적인 영향을 주고 디스크 제한에 걸릴 수 있기 때문입니다.

파일 시스템 사용이 지원되지 않는 예를 들어 게시 계층은 지속되어야 하는 모든 데이터가 장기 저장을 위해 외부 서비스로 전달되도록 해야 합니다.

## 관찰 {#observation}

마찬가지로, 관찰 사건에서 행동하는 것처럼 비동기적으로 발생하는 모든 것으로, 그것이 지역적으로 실행될 수 있다고 보장할 수 없기 때문에 신중하게 사용되어야 한다. 이는 JCR 이벤트와 Sling 리소스 이벤트 모두에 적용됩니다. 변경 사항이 발생하면 인스턴스가 중단되고 다른 인스턴스로 대체될 수 있습니다. 해당 시간에 활성 상태인 토폴로지의 다른 인스턴스는 해당 이벤트에 반응할 수 있습니다. 다만 이 경우 현지 행사가 아니라 행사 발행 시 현재 진행 중인 대표 선출 시 현역 지도자도 없을 수 있다.

## 백그라운드 작업 및 장기 실행 작업 {#background-tasks-and-long-running-jobs}

백그라운드 작업으로 실행되는 코드는 이 코드에서 실행 중인 인스턴스를 언제든지 종료할 수 있다고 가정해야 합니다. 따라서 코드는 복원력이 있어야 하며 가장 중요한 것은 복원 가능해야 합니다. 즉, 코드가 다시 실행되면 처음부터 다시 시작하지 않고 중지된 위치에 가까워야 합니다. 이러한 종류의 코드에 대한 새로운 요구 사항은 아니지만, AEM as a Cloud Service에서는 인스턴스 다운이 발생할 가능성이 높습니다.

문제를 최소화하기 위해, 장기 실행 작업은 가능한 경우 피해야 하고, 최소한으로 재개할 수 있어야 합니다. 이러한 작업을 실행하는 경우 최소 한 번 이상의 보장이 있는 Sling 작업을 사용하면 작업이 중단되면 가능한 한 빨리 재실행됩니다. 그러나 처음부터 다시 시작하면 안 된다. 이러한 작업을 예약하려면 다음을 사용하는 것이 좋습니다. [Sling 작업](https://sling.apache.org/documentation/bundles/apache-sling-eventing-and-job-handling.html#jobs-guarantee-of-processing) 이와 같은 스케줄러는 최소 한 번 이상 실행되도록 합니다.

실행을 보장할 수 없으므로 Sling Commons 스케줄러를 예약에 사용하면 안 됩니다. 그것은 단지 그것이 예정될 것이라는 더 많은 가능성.

마찬가지로, 관찰 이벤트(JCR 이벤트 또는 Sling 리소스 이벤트)에 대한 연기와 같이 비동기적으로 발생하는 모든 작업은 실행을 보장할 수 없으므로 주의하여 사용해야 합니다. 이는 현재 AEM 배포에 이미 해당됩니다.

## 발신 HTTP 연결 {#outgoing-http-connections}

모든 발신 HTTP 연결은 적절한 연결 및 읽기 시간 제한을 설정하는 것이 좋습니다. 제안된 값은 연결 시간 제한의 경우 1초, 읽기 시간 제한의 경우 5초입니다. 정확한 숫자는 이러한 요청을 처리하는 백엔드 시스템의 성능에 따라 결정되어야 합니다.

이러한 시간 초과를 적용하지 않는 코드의 경우, AEMas a Cloud Service 에서 실행되는 AEM 인스턴스가 글로벌 시간 초과를 적용합니다. 이 시간 초과 값은 연결 호출의 경우 10초, 연결 읽기 호출의 경우 60초입니다.

Adobe은 제공된 를 사용할 것을 권장합니다 [Apache HttpComponents Client 4.x 라이브러리](https://hc.apache.org/httpcomponents-client-ga/) HTTP 연결을 만드는 경우.

작동하는 것으로 알려져 있지만, 종속성을 직접 제공해야 할 수 있는 대안은 다음과 같습니다.

* [java.net.URL](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/net/URL.html) 및/또는 [java.net.URLConnection](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/net/URLConnection.html) (AEM 제공)
* [Apache Commons HttpClient 3.x](https://hc.apache.org/httpclient-3.x/) (오래된 버전이며 버전 4.x로 대체되었으므로 권장되지 않음)
* [OK Http](https://square.github.io/okhttp/) (AEM에서 제공되지 않음)

시간 초과를 제공하는 것 외에 이러한 시간 초과와 예기치 않은 HTTP 상태 코드의 적절한 처리도 구현해야 합니다.

## 클래식 UI 사용자 지정 없음 {#no-classic-ui-customizations}

AEM as a Cloud Service은 타사 고객 코드에 대한 Touch UI만 지원합니다. 클래식 UI는 사용자 지정할 수 없습니다.

## 기본 바이너리 또는 기본 라이브러리 없음 {#avoid-native-binaries}

기본 바이너리 및 라이브러리는 클라우드 환경에 배포하거나 설치할 수 없습니다.

또한 코드는 런타임 시 네이티브 바이너리 또는 네이티브 Java 확장 프로그램(예: JNI)을 다운로드하지 않아야 합니다.

## AEM as a Cloud Service으로 스트리밍 바이너리 없음 {#no-streaming-binaries}

바이너리는 핵심 AEM 서비스 외부의 바이너리를 제공하는 CDN을 통해 액세스해야 합니다.

예를 들어 를 사용하지 마십시오 `asset.getOriginal().getStream()`: AEM 서비스의 사용 후 디스크에 바이너리를 다운로드하도록 트리거합니다.

## 역방향 복제 에이전트 없음 {#no-reverse-replication-agents}

게시에서 작성자로의 역방향 복제는 AEM as a Cloud Service에서 지원되지 않습니다. 이러한 전략이 필요한 경우 게시 인스턴스의 팜 및 잠재적으로 작성자 클러스터 간에 공유되는 외부 지속성 저장소를 사용할 수 있습니다.

## 순방향 복제 에이전트를 포팅해야 할 수 있음 {#forward-replication-agents}

게시자-하위 메커니즘을 통해 컨텐츠가 작성자에서 게시로 복제됩니다. 사용자 지정 복제 에이전트는 지원되지 않습니다.

## 모니터링 및 디버깅 {#monitoring-and-debugging}

### 로그 {#logs}

로컬 개발의 경우 로그 항목이 `/crx-quickstart/logs` 폴더를 삭제합니다.

클라우드 환경에서 개발자는 Cloud Manager를 통해 로그를 다운로드하거나 명령줄 도구를 사용하여 로그를 추적할 수 있습니다. <!-- See the [Cloud Manager documentation](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/introduction-to-cloud-manager.html) for more details. Note that custom logs are not supported and so all logs should be output to the error log. -->

**로그 수준 설정**

클라우드 환경에 대한 로그 수준을 변경하려면 Sling 로깅 OSGI 구성을 수정한 후 전체 재배포해야 합니다. 즉시 확인할 수 없으므로 많은 트래픽을 수신하는 프로덕션 환경에서 자세한 로그를 활성화하는 것은 신중해야 합니다. 향후에는 로그 수준을 보다 신속하게 변경하는 메커니즘이 있을 수 있습니다.

>[!NOTE]
>
>아래 나열된 구성 변경 사항을 수행하려면 로컬 개발 환경에서 구성 변경 사항을 만든 다음 AEM as a Cloud Service 인스턴스로 푸시해야 합니다. 이 작업을 수행하는 방법에 대한 자세한 내용은 [AEM에 as a Cloud Service 배포](/help/implementing/deploying/overview.md).

**DEBUG 로그 수준 활성화**

기본 로그 수준은 INFO입니다. 즉, DEBUG 메시지는 기록되지 않습니다. DEBUG 로그 수준을 활성화하려면 다음 속성을 디버그 모드로 업데이트합니다.

`/libs/sling/config/org.apache.sling.commons.log.LogManager/org.apache.sling.commons.log.level`

예를 들어, 을 설정합니다. `/apps/<example>/config/org.apache.sling.commons.log.LogManager.factory.config~<example>.cfg.json` (다음 값 포함)

```json
{
   "org.apache.sling.commons.log.names": [
      "com.example"
   ],
   "org.apache.sling.commons.log.level": "DEBUG",
   "org.apache.sling.commons.log.file": "logs/error.log",
   "org.apache.sling.commons.log.additiv": "false"
}
```

디버그 로그 수준에서 로그를 필요 이상으로 오래 두면 많은 항목이 생성됩니다.

항상 다음 위치에 기록하는 것이 바람직한 경우 실행 모드 기반 OSGi 구성 타겟팅을 사용하여 다양한 AEM 환경에 대해 개별 로그 수준을 설정할 수 있습니다. `DEBUG` 개발 중. 예:

| 환경 | 실행 모드별 OSGi 구성 위치 | `org.apache.sling.commons.log.level` 속성 값 |
| - | - | - |
| 개발 | /apps/example/config/org.apache.sling.commons.log.LogManager.factory.config~example.cfg.json | 디버그 |
| 스테이징 | /apps/example/config.stage/org.apache.sling.commons.log.LogManager.factory.config~example.cfg.json | 경고 |
| 프로덕션 | /apps/example/config.prod/org.apache.sling.commons.log.LogManager.factory.config~example.cfg.json | 오류 |

디버그 파일의 행은 일반적으로 DEBUG로 시작한 다음 로그 수준, 설치 관리자 작업 및 로그 메시지를 제공합니다. 예:

```text
DEBUG 3 WebApp Panel: WebApp successfully deployed
```

로그 수준은 다음과 같습니다.

| 0 | 치명적인 오류 | 작업이 실패하여 설치 관리자를 진행할 수 없습니다. |
|---|---|---|
| 1 | 오류 | 작업이 실패했습니다. 설치가 진행되지만 CRX의 일부가 올바르게 설치되지 않아 작동하지 않습니다. |
| 2 | 경고 | 작업이 성공했지만 문제가 발생했습니다. CRX가 제대로 작동할 수도 있고 작동하지 않을 수도 있습니다. |
| 3 | 정보 | 작업이 성공했습니다. |

### 스레드 덤프 {#thread-dumps}

클라우드 환경의 스레드 덤프는 지속적으로 수집되지만 지금은 셀프서비스 방식으로 다운로드할 수 없습니다. 그동안, 문제를 디버깅하는 데 스레드 덤프가 필요한 경우 정확한 시간 창을 지정하여 AEM 지원에 문의하십시오.

## CRX/DE Lite 및 개발자 콘솔 {#crxde-lite-and-developer-console}

### 로컬 개발 {#local-development}

로컬 개발의 경우 개발자는 CRXDE Lite(`/crx/de`) 및 AEM 웹 콘솔(`/system/console`).

로컬 개발(SDK 사용)에서 `/apps` 및 `/libs` 는 직접 쓸 수 있으며, 이는 상위 수준 폴더를 변경할 수 없는 클라우드 환경과는 다릅니다.

### AEM as a Cloud Service 개발 도구 {#aem-as-a-cloud-service-development-tools}

고객은 작성 계층의 개발 환경에서 CRXDE lite에 액세스할 수 있지만, 스테이지나 프로덕션 환경에서는 액세스할 수 없습니다. 변경할 수 없는 저장소(`/libs`, `/apps`)은 런타임 시 쓸 수 없으므로 그렇게 하면 오류가 발생합니다.

대신 개발자 콘솔에서 저장소 브라우저를 실행하여 작성자, 게시 및 미리보기 계층의 모든 환경에 대한 저장소에 읽기 전용 보기를 제공할 수 있습니다. 저장소 브라우저에 대해 자세히 알아보기 [여기](/help/implementing/developing/tools/repository-browser.md).

AEM as a Cloud Service 개발자 환경을 디버깅하기 위한 도구 세트는 RDE, 개발, 스테이지 및 프로덕션 환경을 위한 Developer Console에서 사용할 수 있습니다. URL은 다음과 같이 Author 또는 Publish 서비스 URL을 조정하여 결정할 수 있습니다.

`https://dev-console/-<namespace>.<cluster>.dev.adobeaemcloud.com`

바로 가기로는 아래 설명된 환경 매개 변수를 기반으로 다음 Cloud Manager CLI 명령을 사용하여 개발자 콘솔을 시작할 수 있습니다.

`aio cloudmanager:open-developer-console <ENVIRONMENTID> --programId <PROGRAMID>`

다음을 참조하십시오 [이 페이지](/help/release-notes/home.md) 추가 정보.

개발자는 상태 정보를 생성하고 다양한 리소스를 해결할 수 있다.

사용 가능한 상태 정보에는 아래에서 보듯이 번들, 구성 요소, OSGI 구성, oak 색인, OSGI 서비스 및 Sling 작업의 상태가 포함됩니다.

![개발 콘솔 1](/help/implementing/developing/introduction/assets/devconsole1.png)

아래 그림과 같이 개발자는 패키지 종속성 및 서블릿을 해결할 수 있습니다.

![개발 콘솔 2](/help/implementing/developing/introduction/assets/devconsole2.png)

![개발 콘솔 3](/help/implementing/developing/introduction/assets/devconsole3.png)

디버깅에 유용하며, 개발자 콘솔에는 쿼리 설명 도구에 대한 링크가 있습니다.

![개발 콘솔 4](/help/implementing/developing/introduction/assets/devconsole4.png)

프로덕션 프로그램의 경우 Admin Console에서 &quot;Cloud Manager - 개발자 역할&quot;에 의해 개발자 콘솔에 대한 액세스가 정의되지만 샌드박스 프로그램의 경우 제품 프로필이 있는 모든 사용자가 Developer Console을 사용하여 AEM as a Cloud Service에 액세스할 수 있습니다. 모든 프로그램의 경우 &quot;Cloud Manager - 개발자 역할&quot;이 상태 덤프에 필요하며 작성자와 게시 서비스 모두에서 데이터를 보려면 저장소 브라우저 및 사용자가 AEM 사용자 또는 AEM 관리자 제품 프로필에 정의되어 있어야 합니다. 사용자 권한 설정에 대한 자세한 내용은 [Cloud Manager 설명서](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/requirements/setting-up-users-and-roles.html).

### 성능 모니터링 {#performance-monitoring}

Adobe은 애플리케이션 성능을 모니터링하고 성능 저하가 관찰되는 경우 문제를 해결하기 위한 조치를 취합니다. 현재 애플리케이션 지표는 관찰할 수 없습니다.

## 이메일 전송 중 {#sending-email}

아래 섹션에서는 이메일을 요청, 구성 및 보내는 방법을 설명합니다.

>[!NOTE]
>
>OAuth2 지원을 통해 메일 서비스를 구성할 수 있습니다. 자세한 내용은 [메일 서비스에 대한 OAuth2 지원](/help/security/oauth2-support-for-mail-service.md).

### 아웃바운드 이메일 활성화 {#enabling-outbound-email}

기본적으로 이메일을 보내는 데 사용되는 포트는 비활성화되어 있습니다. 포트를 활성화하려면 다음을 구성하십시오. [고급 네트워킹](/help/security/configuring-advanced-networking.md), 필요한 각 환경에 대해 를 설정해야 합니다. `PUT /program/<program_id>/environment/<environment_id>/advancedNetworking` 의도한 포트(예: 465 또는 587)를 프록시 포트에 매핑하는 끝점의 포트 전달 규칙

를 사용하여 고급 네트워킹을 구성하는 것이 좋습니다. `kind` 매개 변수가 로 설정됨 `flexiblePortEgress` Adobe은 유연한 포트 이그레스 트래픽의 성능을 최적화할 수 있기 때문입니다. 고유한 이그레스 IP 주소가 필요한 경우 `kind` 매개 변수 `dedicatedEgressIp`. 다른 이유로 이미 VPN을 구성한 경우 해당 고급 네트워킹 변형에서 제공하는 고유 IP 주소를 사용할 수도 있습니다.

전자 메일 클라이언트로 직접 보내는 대신 메일 서버를 통해 전자 메일을 보내야 합니다. 그렇지 않으면 이메일이 차단될 수 있습니다.

### 이메일 보내기 {#sending-emails}

다음 [일별 CQ 메일 서비스 OSGI 서비스](https://experienceleague.adobe.com/docs/experience-manager-65/administering/operations/notification.html#configuring-the-mail-service) 은 을 사용해야 하며 이메일은 수신자에게 직접 전송되지 않고 지원 요청에 지정된 메일 서버로 전송되어야 합니다.

### 구성 {#email-configuration}

AEM에서 전자 메일은 [일별 CQ 메일 서비스 OSGi 서비스](https://experienceleague.adobe.com/docs/experience-manager-65/administering/operations/notification.html#configuring-the-mail-service).

다음을 참조하십시오. [AEM 6.5 설명서](https://experienceleague.adobe.com/docs/experience-manager-65/administering/operations/notification.html) 이메일 설정 구성에 대한 자세한 내용을 참조하십시오. AEM as a Cloud Service의 경우 다음에 필요한 조정을 참고하십시오. `com.day.cq.mailer.DefaultMailService OSGI` 서비스:

* SMTP 서버 호스트 이름을 $(으)로 설정해야 함[env:AEM_PROXY_HOST;default=proxy.tunnel]
* SMTP 서버 포트는 고급 네트워킹을 구성할 때 API 호출에 사용되는 portForwards 매개변수에 설정된 원래 프록시 포트의 값으로 설정되어야 합니다. 예를 들어 30465(465가 아님)

SMTP 서버 포트는 (으)로 설정해야 합니다. `portDest` 고급 네트워킹 및 를 구성할 때 API 호출에 사용되는 portForwards 매개 변수에 설정된 값 `portOrig` 값은 필요한 30000 - 30999 범위 내에 있는 의미 있는 값이어야 합니다. 예를 들어 SMTP 서버 포트가 465이면 포트 30465을 로 사용해야 합니다. `portOrig` 값.

이 경우 및 의 구성에서 SSL을 활성화해야 한다고 가정 **일별 CQ 메일 서비스 OSGI** 서비스:

* 설정 `smtp.port` 끝 `30465`
* 설정 `smtp.ssl` 끝 `true`

또는 대상 포트가 587이면 `portOrig` 30587 값을 사용해야 합니다. 또한 SSL을 비활성화해야 한다고 가정할 경우 일별 CQ 메일 서비스 OSGI 서비스의 구성은 다음과 같습니다.

* 설정 `smtp.port` 끝 `30587`
* 설정 `smtp.ssl` 끝 `false`

다음 `smtp.starttls` 속성은 런타임 시 AEMas a Cloud Service 에 의해 자동으로 적절한 값으로 설정됩니다. 따라서 다음과 같습니다. `smtp.ssl` 이 true로 설정되어 있으면 `smtp.startls` 은(는) 무시됩니다. If `smtp.ssl` false로 설정되어 있습니다. `smtp.starttls` 가 true로 설정되어 있는 경우 이것은 `smtp.starttls` osgi 구성에 설정된 값입니다.


OAuth2 지원을 통해 메일 서비스를 선택적으로 구성할 수 있습니다. 자세한 내용은 [메일 서비스에 대한 OAuth2 지원](/help/security/oauth2-support-for-mail-service.md).

### 이전 이메일 구성 {#legacy-email-configuration}

2021.9.0 릴리스 이전에는 고객 지원 요청을 통해 이메일을 구성했습니다. 다음에 필요한 조정을 적어 두십시오. `com.day.cq.mailer.DefaultMailService OSGI` 서비스:

AEM as a Cloud Service에서는 포트 465를 통해 메일을 보내야 합니다. 메일 서버가 포트 465를 지원하지 않는 경우 TLS 옵션이 활성화되어 있는 한 포트 587을 사용할 수 있습니다.

포트 465가 요청된 경우:

* set `smtp.port` 끝 `465`
* set `smtp.ssl` 끝 `true`

포트 587이 요청된 경우:

* set `smtp.port` 끝 `587`
* set `smtp.ssl` 끝 `false`

다음 `smtp.starttls` 속성은 런타임 시 AEMas a Cloud Service 에 의해 자동으로 적절한 값으로 설정됩니다. 따라서 다음과 같습니다. `smtp.ssl` 이 true로 설정되어 있으면 `smtp.startls` 은(는) 무시됩니다. If `smtp.ssl` false로 설정되어 있습니다. `smtp.starttls` 가 true로 설정되어 있는 경우 이것은 `smtp.starttls` osgi 구성에 설정된 값입니다.

SMTP 서버 호스트는 메일 서버의 호스트로 설정해야 합니다.

## 큰 다중 값 속성 방지 {#avoid-large-mvps}

AEM as a Cloud Service의 기반이 되는 Oak 콘텐츠 저장소는 과도한 수의 MVP(다중 값 속성)와 함께 사용하기 위한 것이 아닙니다. MVP를 1000명 미만으로 유지하는 것이 경험칙이다. 그러나 실제 성능은 많은 요인에 따라 다릅니다.

경고는 1,000을 초과한 후 기본적으로 기록됩니다. 이는 다음과 유사합니다.

```text
org.apache.jackrabbit.oak.jcr.session.NodeImpl Large multi valued property [/path/to/property] detected (1029 values). 
```

대형 MVP는 16MB를 초과하는 MongoDB 문서로 인해 오류가 발생할 수 있으며 다음과 유사한 오류가 발생합니다.

```text
Caused by: com.mongodb.MongoWriteException: Resulting document after update is larger than 16777216
```

다음을 참조하십시오. [Apache Oak 설명서](https://jackrabbit.apache.org/oak/docs/dos_and_donts.html#Large_Multi_Value_Property) 을 참조하십시오.

## [!DNL Assets] 개발 지침 및 사용 사례 {#use-cases-assets}

Assets에 대한 개발 사용 사례, 권장 사항 및 참조 자료를 as a Cloud Service으로 제공하는 방법에 대해 알아보려면 다음을 참조하십시오. [자산에 대한 개발자 참조.](/help/assets/developer-reference-material-apis.md#assets-cloud-service-apis)
