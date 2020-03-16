---
title: 클라우드 서비스로서의 AEM 개발 지침
description: '완료 예정 '
translation-type: tm+mt
source-git-commit: a95944055d74a14b2b35649105f284df6afc7e7b

---


# 클라우드 서비스로서의 AEM 개발 지침 {#aem-as-a-cloud-service-development-guidelines}

클라우드 서비스로 AEM에서 실행되는 코드는 항상 클러스터에서 실행 중임을 인지해야 합니다. 즉, 실행 중인 인스턴스가 두 개 이상 있습니다. 특히 인스턴스는 언제든지 중지될 수 있으므로 코드는 복원력이 있어야 합니다.

클라우드 서비스로 AEM을 업데이트하는 동안 이전 코드와 새 코드가 동시에 실행되는 인스턴스가 있게 됩니다. 따라서 이전 코드는 새 코드로 만든 콘텐츠와 분리되지 않아야 하며 새 코드는 이전 컨텐츠를 처리할 수 있어야 합니다.
<!--

>[!NOTE]
> All of the best practices mentioned here hold true for on-premise deployments of AEM, if not stated otherwise. An instance can always stop due to various reasons. However, with Skyline it is more likely to happen therefore an instance stopping is the rule not an exception.

-->

클러스터에서 마스터를 식별해야 하는 경우 Apache Sling Discovery API를 사용하여 이를 감지할 수 있습니다.

## 메모리 상태 {#state-in-memory}

상태는 메모리에 유지되지 않고 보관소에 있어야 합니다. 그렇지 않으면 인스턴스가 중지되면 이 상태가 손실될 수 있습니다.

## 파일 시스템의 상태 {#state-on-the-filesystem}

인스턴스의 파일 시스템은 AEM에서 클라우드 서비스로 사용해서는 안 됩니다. 이 디스크는 일시적이며, 인스턴스가 재생될 때 삭제됩니다. 단일 요청 처리와 관련된 임시 스토리지에 대한 파일 시스템을 제한적으로 사용할 수는 있지만 대용량 파일에 대해서는 남용되어서는 안 됩니다. 이는 리소스 사용 할당량에 부정적인 영향을 줄 수 있고 디스크 제한에 걸릴 수 있기 때문입니다.

파일 시스템 사용이 지원되지 않는 예로, 게시 계층은 지속해야 하는 모든 데이터를 장기 보관을 위해 외부 서비스로 발송해야 합니다.

## 관찰 {#observation}

유사하게, 관측 이벤트 시 비동기 방식으로 발생하는 모든 작업을 통해, 로컬에서 실행되도록 보장할 수 없으므로 주의해야 합니다. 이는 JCR 이벤트와 Sling 리소스 이벤트 모두에 적용됩니다. 변경 시 인스턴스가 삭제되고 다른 인스턴스로 대체될 수 있습니다. 해당 시간에 활성 상태인 토폴로지의 다른 인스턴스는 해당 이벤트에 응답할 수 있습니다. 그러나 이 경우, 이것은 지역 행사가 아니며, 이 행사가 발표되었을 때 진행중인 지도자 선거의 경우에 조차도 적극적인 지도자가 없을 수도 있습니다.

## 백그라운드 작업 및 장기 실행 작업 {#background-tasks-and-long-running-jobs}

백그라운드 작업으로 실행되는 코드는 실행 중인 인스턴스를 언제든지 중지할 수 있다고 간주해야 합니다. 따라서 코드는 복원력이 있어야 하며 대부분의 가져오기 다시 시작 가능해야 합니다. 즉, 코드가 다시 실행될 경우 처음부터 다시 시작하지 않고 처음부터 다시 시작되어야 합니다. 이러한 유형의 코드에 대한 새로운 요구 사항은 아니지만, AEM에서 클라우드 서비스로 사용할 경우 인스턴스가 삭제될 가능성이 높습니다.

이를 최소화하려면 장기간에 걸친 작업은 가급적 뒤로 하고, 최소한 재개는 수 있도록 해야 한다. 이러한 작업을 실행하는 경우, 적어도 한 번 이상 보증되므로 중단된 경우 가능한 한 빨리 다시 실행될 수 있는 슬링 작업을 사용하십시오. 그러나 처음부터 다시 시작해서는 안 될 것이다. 이러한 작업을 예약하기 위해 Sling [작업](https://sling.apache.org/documentation/bundles/apache-sling-eventing-and-job-handling.html#jobs-guarantee-of-processing) 스케줄러를 다시 한 번 이상 실행하는 것이 가장 좋습니다.

실행을 보장할 수 없으므로 Sling Commons Scheduler를 사용하여 예약하면 안 됩니다. 그것이 계획될 가능성이 더 높다.

마찬가지로, 관측 이벤트(JCR 이벤트 또는 Sling 리소스 이벤트)를 수행하는 것과 같이 비동기적으로 발생하는 모든 작업은 반드시 실행되도록 보장될 수 없으므로 주의해야 합니다. 현재 AEM 배포에서는 이미 적용됩니다.

## 나가는 HTTP 연결 {#outgoing-http-connections}

나가는 모든 HTTP 연결은 적절한 연결 및 읽기 시간 제한을 설정하는 것이 좋습니다. 이러한 시간 초과를 적용하지 않는 코드의 경우 AEM에서 클라우드 서비스로 실행되는 AEM 인스턴스가 전역 시간 초과를 적용합니다. 이러한 시간 초과 값은 연결 호출의 경우 10초, 다음 자주 사용되는 Java 라이브러리에서 사용되는 연결에 대한 읽기 호출에 60초입니다.

Adobe에서는 HTTP 연결을 만들기 위해 제공된 [Apache HttpComponents Client 4.x 라이브러리를](https://hc.apache.org/httpcomponents-client-ga/) 사용하는 것이 좋습니다.

효과가 있다고 알려져 있지만 스스로 종속성을 제공해야 할 수 있는 대체 방법은 다음과 같습니다.

* [java.net.URL](https://docs.oracle.com/javase/7/docs/api/java/net/URL.html) 및/또는 [java.net.URLConnection](https://docs.oracle.com/javase/7/docs/api/java/net/URLConnection.html) (AEM에서 제공)
* [Apache Commons HttpClient 3.x](https://hc.apache.org/httpclient-3.x/) (이전 버전이므로 권장되지 않음, 버전 4.x로 대체됨)
* [확인 Http](https://square.github.io/okhttp/) (AEM에서 제공되지 않음)

## 클래식 UI 사용자 정의 없음 {#no-classic-ui-customizations}

클라우드 서비스로서 AEM은 타사 고객 코드에 대한 터치 UI만 지원합니다. 클래식 UI는 사용자 지정에 사용할 수 없습니다.

## 기본 바이너리 방지 {#avoid-native-binaries}

런타임에 바이너리를 다운로드하거나 수정할 수 없습니다. 예를 들어 `jar` 또는 `tar` 파일의 압축을 풀 수 없습니다.

## 클라우드 서비스로 AEM을 통한 스트리밍 바이너리 없음 {#no-streaming-binaries}

바이너리는 코어 AEM 서비스 외부의 바이너리를 제공하는 CDN을 통해 액세스해야 합니다.

예를 들어 AEM 서비스의 임시 디스크에 바이너리 다운로드를 트리거하는 `asset.getOriginal().getStream()`기능을 사용하지 마십시오.

## 역방향 복제 에이전트 없음 {#no-reverse-replication-agents}

게시에서 작성자로 역 복제는 AEM에서 클라우드 서비스로 지원되지 않습니다. 이러한 전략이 필요한 경우 게시 인스턴스의 팜 및 작성자 클러스터 간에 공유되는 외부 지속성 저장소를 사용할 수 있습니다.

## 전달 복제 에이전트를 포팅해야 할 수 있습니다. {#forward-replication-agents}

pub-sub 메커니즘을 통해 작성자에서 게시로 컨텐츠가 복제됩니다. 사용자 지정 복제 에이전트는 지원되지 않습니다.

## 모니터링 및 디버깅 {#monitoring-and-debugging}

### 로그 {#logs}

로컬 개발의 경우 로그 항목은 `/crx-quickstart/logs` 폴더의 로컬 파일에 기록됩니다.

클라우드 환경에서 개발자는 Cloud Manager를 통해 로그를 다운로드하거나 명령줄 툴을 사용하여 로그를 추적할 수 있습니다. <!-- See the [Cloud Manager documentation](https://docs.adobe.com/content/help/en/experience-manager-cloud-manager/using/introduction-to-cloud-manager.html) for more details. Note that custom logs are not supported and so all logs should be output to the error log. -->

**로그 수준 설정**

클라우드 환경의 로그 수준을 변경하려면 Sling Logging OSGI 구성을 수정한 후 전체 재배포해야 합니다. 이는 즉각적이지는 않으므로 많은 트래픽을 받는 프로덕션 환경에서 자세한 로그를 활성화하는 것에 주의하십시오. 앞으로 로그 수준을 보다 신속하게 변경하는 메커니즘이 있을 수 있습니다.

**디버그 로그 수준 활성화**

기본 로그 수준은 INFO입니다. 즉, DEBUG 메시지가 기록되지 않습니다.
디버그 로그 수준을 활성화하려면 CRX 탐색기를 사용하여

``` /libs/sling/config/org.apache.sling.commons.log.LogManager/org.apache.sling.commons.log.level ```

property to debug. 로그를 많은 로그를 생성하므로 DEBUG 로그 수준에서 로그를 필요 이상으로 오래 보관하지 마십시오.
디버그 파일의 행은 일반적으로 DEBUG로 시작되며 로그 수준, 설치 프로그램 작업 및 로그 메시지를 제공합니다. 예:

``` DEBUG 3 WebApp Panel: WebApp successfully deployed ```

로그 수준은 다음과 같습니다.

| 0 | 치명적인 오류 | 작업이 실패하여 설치 프로그램을 계속할 수 없습니다. |
|---|---|---|
| 1 | 오류 | 작업이 실패했습니다. 설치가 진행되지만 CRX의 일부가 제대로 설치되지 않아 작동하지 않습니다. |
| 2 | 경고 | 작업에 성공했지만 문제가 발생했습니다. CRX가 제대로 작동하지 않거나 작동하지 않을 수 있습니다. |
| 3 | 정보 | 작업이 성공했습니다. |

### 스레드 덤프 {#thread-dumps}

클라우드 환경의 스레드 덤프는 지속적으로 수집되지만 현재는 셀프 서비스 방식으로 다운로드할 수 없습니다. 한편 문제를 디버깅하기 위해 스레드 덤프가 필요한 경우 정확한 시간 창을 지정하여 AEM 지원에 문의하십시오.

## CRX/DE Lite 및 System Console {#crxde-lite-and-system-console}

### 로컬 개발 {#local-development}

로컬 개발의 경우 개발자는 CRXDE Lite(`/crx/de`) 및 AEM Web Console(`/system/console`)에 대한 전체 액세스 권한을 갖습니다.

로컬 개발 시(클라우드 지원 빠른 시작 사용) `/apps` 직접 작성할 `/libs` 수 있으며, 최상위 폴더를 변경할 수 없는 클라우드 환경과는 다릅니다.

### AEM as a Cloud Service Development tools {#aem-as-a-cloud-service-development-tools}

고객은 개발 환경에서 CRXDE lite를 이용할 수 있지만 스테이지나 프로덕션은 이용할 수 없습니다. 변경 불가능한 저장소(`/libs`, `/apps`)를 런타임에 쓸 수 없으므로 작성하려고 하면 오류가 발생합니다.

AEM을 클라우드 서비스 개발자 환경으로 디버깅하기 위한 도구 세트는 개발, 준비 및 프로덕션 환경을 위해 개발자 콘솔에서 사용할 수 있습니다. Url은 다음과 같이 작성자 또는 게시 서비스 URL을 조정하여 결정할 수 있습니다.

`https://dev-console/-<namespace>.<cluster>.dev.adobeaemcloud.com`

바로 가기 키로, 아래 설명된 환경 매개 변수를 기반으로 개발자 콘솔을 실행하는 데 다음 Cloud Manager CLI 명령을 사용할 수 있습니다.

`aio cloudmanager:open-developer-console <ENVIRONMENTID> --programId <PROGRAMID>`

자세한 내용은 [이 페이지를](/help/release-notes/home.md) 참조하십시오.

개발자는 상태 정보를 생성하고 다양한 리소스를 해결할 수 있습니다.

아래 그림과 같이 사용 가능한 상태 정보에는 번들, 구성 요소, OSGI 구성, 오크 인덱스, OSGI 서비스 및 Sling 작업 상태가 포함됩니다.

![개발 콘솔 1](/help/implementing/developing/introduction/assets/devconsole1.png)

아래 그림과 같이 개발자는 패키지 종속성 및 서비스를 해결할 수 있습니다.

![개발 콘솔 2](/help/implementing/developing/introduction/assets/devconsole2.png)

![개발 콘솔 3](/help/implementing/developing/introduction/assets/devconsole3.png)

디버깅에도 유용한 개발자 콘솔에는 쿼리 설명 도구에 대한 링크가 있습니다.

![개발 콘솔 4](/help/implementing/developing/introduction/assets/devconsole4.png)

### AEM 스테이징 및 프로덕션 서비스 {#aem-staging-and-production-service}

고객은 스테이징 및 프로덕션 환경을 위한 개발자 도구에 액세스할 수 없습니다.

### 성능 모니터링 {#performance-monitoring}

Adobe는 애플리케이션 성능을 모니터링하고 성능 저하가 발생하는 경우 이를 해결하기 위한 조치를 취합니다. 지금은 애플리케이션 지표를 검색할 수 없습니다.