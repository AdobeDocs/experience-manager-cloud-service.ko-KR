---
title: 클라우드 서비스 개발 지침으로서 AEM
description: '완료 예정 '
translation-type: tm+mt
source-git-commit: cedc14b0d71431988238d6cb4256936a5ceb759b

---


# 클라우드 서비스 개발 지침으로서 AEM {#aem-as-a-cloud-service-development-guidelines}

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
* [OK Http](확인 Http(AEM에서 제공되지 않음)(AEM에서 제공되지 않음)

## 모니터링 및 디버깅 {#monitoring-and-debugging}

### 로그 {#logs}

* 로컬 개발의 경우 로그 항목은 로컬 파일에 기록됩니다
   * `./crx-quickstart/logs`
* 클라우드 환경에서 개발자는 Cloud Manager를 통해 로그를 다운로드하거나 명령줄 툴을 사용하여 로그를 추적할 수 있습니다. <!-- See the [Cloud Manager documentation](https://docs.adobe.com/content/help/en/experience-manager-cloud-manager/using/introduction-to-cloud-manager.html) for more details. Note that custom logs are not supported and so all logs should be output to the error log. -->
* 클라우드 환경의 로그 수준을 변경하려면 Sling Logging OSGI 구성을 수정한 후 전체 재배포해야 합니다. 이는 즉각적이지는 않으므로 많은 트래픽을 받는 프로덕션 환경에서 자세한 로그를 활성화하는 것에 주의하십시오. 앞으로 로그 수준을 보다 신속하게 변경하는 메커니즘이 있을 수 있습니다.

### 스레드 덤프 {#thread-dumps}

클라우드 환경의 스레드 덤프는 지속적으로 수집되지만 현재는 셀프 서비스 방식으로 다운로드할 수 없습니다. 한편 문제를 디버깅하기 위해 스레드 덤프가 필요한 경우 정확한 시간 창을 지정하여 AEM 지원에 문의하십시오.

### CRX/DE Lite 및 System Console {#crxde-lite-and-system-console}

## 로컬 개발 {#local-development}

로컬 개발의 경우 개발자는 CRXDE Lite(`/crx/de`) 및 AEM Web Console(`/system/console`)에 대한 전체 액세스 권한을 갖습니다.

로컬 개발 시(클라우드 지원 빠른 시작 사용) `/apps` 직접 작성할 `/libs` 수 있으며, 최상위 폴더를 변경할 수 없는 클라우드 환경과는 다릅니다.

## AEM을 클라우드 서비스 개발 도구로 사용 {#aem-as-a-cloud-service-development-tools}

고객은 개발 환경에서 CRXDE lite를 이용할 수 있지만 스테이지나 프로덕션은 이용할 수 없습니다. 변경 불가능한 저장소(`/libs`, `/apps`)를 런타임에 쓸 수 없으므로 작성하려고 하면 오류가 발생합니다.

AEM을 클라우드 서비스 개발자 환경으로 디버깅하기 위한 도구 세트는 개발, 준비 및 프로덕션 환경을 위해 개발자 콘솔에서 사용할 수 있습니다. URL은 다음과 같이 작성자 또는 게시 서비스 URL을 조정하여 결정할 수 있습니다.

`https://dev-console>-<namespace>.<cluster>.dev.adobeaemcloud.com`

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

**AEM 스테이징 및 프로덕션 서비스**

고객은 스테이징 및 프로덕션 환경을 위한 개발자 도구에 액세스할 수 없습니다.

### 진단 {#diagnostics}

시스템 콘솔은 개발 환경에 사용할 수 있습니다. 그러나 스테이징 및 프로덕션에 대한 진단 덤프는 사용할 수 없습니다.