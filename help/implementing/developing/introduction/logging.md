---
title: AEM as a Cloud Service에 대한 로깅
description: AEM용 로깅을 as a Cloud Service으로 사용하여 중앙 로깅 서비스의 전역 매개 변수, 개별 서비스에 대한 특정 설정 또는 데이터 로깅을 요청하는 방법을 알아봅니다.
exl-id: 262939cc-05a5-41c9-86ef-68718d2cd6a9
feature: Developing
role: Admin, Architect, Developer
source-git-commit: 646ca4f4a441bf1565558002dcd6f96d3e228563
workflow-type: tm+mt
source-wordcount: '2797'
ht-degree: 8%

---

# AEM as a Cloud Service에 대한 로깅 {#logging-for-aem-as-a-cloud-service}

AEM as a Cloud Service은 고객이 자신의 고객 기반을 위해 고유한 경험을 만들 수 있도록 사용자 지정 코드를 포함하는 플랫폼입니다. 이러한 점을 고려하여 로깅 서비스는 로컬 개발 및 클라우드 환경, 특히 AEMas a Cloud Service 의 개발 환경에서 코드 실행을 디버깅하고 이해하는 데 중요한 기능입니다.

AEM as a Cloud Service 로깅 설정 및 로그 수준은 Git에서 AEM 프로젝트의 일부로 저장되고 Cloud Manager를 통해 AEM 프로젝트의 일부로 배포되는 구성 파일에서 관리됩니다. AEM as a Cloud Service으로 로그인하면 두 개의 논리 세트로 나뉠 수 있습니다.

* AEM 로깅 - AEM 애플리케이션 수준에서 로깅을 수행합니다.
* 게시 계층에서 웹 서버 및 Dispatcher의 로깅을 수행하는 Apache HTTPD 웹 서버/Dispatcher 로깅.
* CDN 로깅은 이름 그대로 CDN에서 로깅을 수행합니다. 이 기능은 9월 초에 고객에게 점진적으로 출시되고 있습니다.

## AEM 로깅 {#aem-logging}

AEM 애플리케이션 수준에서 로깅은 다음 세 가지 로그에 의해 처리됩니다.

1. AEM Java 로그: AEM 애플리케이션에 대한 Java 로깅 문을 렌더링합니다.
1. AEM에서 제공하는 HTTP 요청 및 해당 응답에 대한 정보를 기록하는 HTTP 요청 로그
1. 요약된 정보 및 AEM에서 제공하는 HTTP 요청을 기록하는 HTTP 액세스 로그

>[!NOTE]
>
>게시 계층의 Dispatcher 캐시 또는 업스트림 CDN에서 제공되는 HTTP 요청은 이러한 로그에 반영되지 않습니다.

## AEM Java 로깅 {#aem-java-logging}

AEM as a Cloud Service에서는 Java 로그 문에 대한 액세스를 제공합니다. AEM용 애플리케이션 개발자는 다음 로그 수준에서 사용자 지정 코드 실행에 대한 관련 문을 로깅하는 일반적인 Java 로깅 모범 사례를 따라야 합니다.

<table>
<tr>
<td>
<b>AEM 환경</b></td>
<td>
<b>로그 수준</b></td>
<td>
<b>설명</b></td>
<td>
<b>로그 문 가용성</b></td>
</tr>
<tr>
<td>
개발</td>
<td>
디버그</td>
<td>
애플리케이션에서 발생하는 작업을 설명합니다.<br>
DEBUG 로깅이 활성화되면 어떤 활동이 발생하는지 명확하게 파악할 수 있는 문과 처리에 영향을 주는 주요 매개 변수가 기록됩니다.</td>
<td>
<ul>
<li> 로컬 개발</li>
<li>개발</li>
</ul></td>
</tr>
<tr>
<td>
스테이지</td>
<td>
경고</td>
<td>
오류가 발생할 가능성이 있는 조건을 설명합니다.<br>
WARN 로깅이 활성화되면 하위 최적에 가까워지는 조건을 나타내는 문만 기록됩니다.</td>
<td>
<ul>
<li> 로컬 개발</li>
<li>개발</li>
<li>스테이지</li>
</ul></td>
</tr>
<tr>
<td>
프로덕션</td>
<td>
오류</td>
<td>
실패를 나타내는 조건 및 해결해야 하는 조건에 대해 설명합니다.<br>
ERROR 로깅이 활성화되면 실패를 나타내는 문만 기록됩니다. 오류 로그 문은 가능한 한 빨리 해결해야 하는 심각한 문제를 나타냅니다.</td>
<td>
<ul>
<li> 로컬 개발</li>
<li>개발</li>
<li>스테이지</li>
<li>프로덕션</li>
</ul></td>
</tr>
</table>

Java 로깅은 다른 여러 수준의 로깅 세부기간을 지원하지만 AEMas a Cloud Service 에서는 위에 설명된 세 가지 수준을 사용하는 것이 좋습니다.

AEM 로그 수준은 OSGi 구성을 통해 환경 유형별로 설정되며, OSGi 구성은 Git에 커밋되고 Cloud Manager를 통해 AEM as a Cloud Service으로 배포됩니다. 따라서 업데이트된 로그 수준 구성으로 애플리케이션을 다시 배포하지 않고도 AEM as Cloud Service을 통해 사용할 수 있는 로그를 최적의 로그 수준에서 사용할 수 있도록 로그 문을 일관되게 유지하고 환경 유형에 대해 잘 알려진 상태로 유지하는 것이 가장 좋습니다.

**로그 출력 예**

```
22.06.2020 18:33:30.120 [cm-p12345-e6789-aem-author-86657cbb55-xrnzq] *ERROR* [qtp501076283-1809] io.prometheus.client.dropwizard.DropwizardExports Failed to get value from Gauge
22.06.2020 18:33:30.229 [cm-p12345-e6789-aem-author-86657cbb55-xrnzq] *INFO* [qtp501076283-1805] org.apache.sling.auth.core.impl.SlingAuthenticator getAnonymousResolver: Anonymous access not allowed by configuration - requesting credentials
22.06.2020 18:33:30.370 [cm-p12345-e6789-aem-author-86657cbb55-xrnzq] *INFO* [73.91.59.34 [1592850810364] GET /libs/granite/core/content/login.html HTTP/1.1] org.apache.sling.i18n.impl.JcrResourceBundle Finished loading 0 entries for 'en_US' (basename: <none>) in 4ms
22.06.2020 18:33:30.372 [cm-p12345-e6789-aem-author-86657cbb55-xrnzq] *INFO* [FelixLogListener] org.apache.sling.i18n Service [5126, [java.util.ResourceBundle]] ServiceEvent REGISTERED
22.06.2020 18:33:30.372 [cm-p12345-e6789-aem-author-86657cbb55-xrnzq] *WARN* [73.91.59.34 [1592850810364] GET /libs/granite/core/content/login.html HTTP/1.1] libs.granite.core.components.login.login$jsp j_reason param value 'unknown' cannot be mapped to a valid reason message: ignoring
```

**로그 형식**

<table>
<tbody>
<tr>
<td>날짜 및 시간</td>
<td>29.04.2020 21:50:13.398</td>
</tr>
<tr>
<td>AEM as a Cloud Service 노드 ID</td>
<td>[cm-p1234-e5678-aem-author-59555cb5b8-q7l9s]</td>
</tr>
<tr>
<td>로그 수준</td>
<td>디버그</td>
</tr>
<tr>
<td>스레드</td>
<td>qtp2130572036-1472</td>
</tr>
<tr>
<td>Java 클래스</td>
<td>com.example.approval.workflow.impl.CustomApprovalWorkflow</td>
</tr>
<tr>
<td>로그 메시지</td>
<td>지정된 승인자가 없습니다. [ Creative Approvers 사용자 그룹 ]이 기본값으로 설정됩니다.</td>
</tr>
</tbody>
</table>

### 구성 로거 {#configuration-loggers}

AEM Java 로그는 OSGi 구성으로 정의되므로 실행 모드 폴더를 사용하여 특정 AEM as a Cloud Service 환경을 타깃팅합니다.

Sling LogManager 팩토리에 대한 OSGi 구성을 통해 사용자 지정 Java 패키지에 대한 Java 로깅을 구성합니다. 지원되는 구성 속성에는 두 가지가 있습니다.

| OSGi 구성 속성 | 설명 |
|---|---|
| org.apache.sling.commons.log.names | 로그 문을 수집할 Java 패키지입니다. |
| org.apache.sling.commons.log.level | org.apache.sling.commons.log.names에 의해 지정된 Java 패키지를 기록하는 로그 수준 |

다른 LogManager OSGi 구성 속성을 변경하면 AEM as a Cloud Service에서 가용성 문제가 발생할 수 있습니다.

다음은 권장되는 로깅 구성의 예입니다( 의 자리 표시자 Java 패키지 사용). `com.example`AEM as a Cloud Service )을 참조하십시오.

### 개발 {#development}

/apps/my-app/config/org.apache.sling.commons.log.LogManager.factory.config-example.cfg.json

```
{
    "org.apache.sling.commons.log.names": ["com.example"],
    "org.apache.sling.commons.log.level": "debug"
}
```

### 스테이지 {#stage}

/apps/my-app/config.stage/org.apache.sling.commons.log.LogManager.factory.config-example.cfg.json

```
{
    "org.apache.sling.commons.log.names": ["com.example"],
    "org.apache.sling.commons.log.level": "warn"
}
```

### 프로덕션 {#productiomn}

/apps/my-app/config.prod/org.apache.sling.commons.log.LogManager.factory.config-example.cfg.json

```
{
    "org.apache.sling.commons.log.names": ["com.example"],
    "org.apache.sling.commons.log.level": "error"
}
```

## AEM HTTP 요청 로깅 {#aem-http-request-logging}

AEM as a Cloud Service의 HTTP 요청 로깅을 통해 AEM에 수행된 HTTP 요청과 그 HTTP 응답을 시간 순서대로 파악할 수 있습니다. 이 로그는 AEM에 대한 HTTP 요청과 이 요청이 처리되고 응답하는 순서를 이해하는 데 유용합니다.

이 로그를 이해하는 핵심은 HTTP 요청 및 응답 쌍을 해당 ID로 매핑하는 것입니다(대괄호의 숫자 값으로 표시됨). 종종 요청 및 해당 응답에는 다른 HTTP 요청과 응답이 로그에 있는 요청 사이에 끼어있습니다.

**예제 로그**

```
29/Apr/2020:19:14:21 +0000 [137] > POST /conf/global/settings/dam/adminui-extension/metadataprofile/ HTTP/1.1 [cm-p1234-e5678-aem-author-59555cb5b8-q7l9s]
...
29/Apr/2020:19:14:22 +0000 [139] > GET /mnt/overlay/dam/gui/content/processingprofilepage/metadataprofiles/editor.html/conf/global/settings/dam/adminui-extension/metadataprofile/main HTTP/1.1 [cm-p1234-e5678-aem-author-59555cb5b8-q7l9s]
...
29/Apr/2020:19:14:21 +0000 [137] <- 201 text/html 111ms [cm-p1234-e5678-aem-author-59555cb5b8-q7l9s]
...
29/Apr/2020:19:14:22 +0000 [139] <- 200 text/html;charset=utf-8 637ms [cm-p1234-e5678-aem-author-59555cb5b8-q7l9s]
```

**로그 형식**

<table>
<tbody>
<tr>
<td>날짜 및 시간</td>
<td>29/4/2020:19:14:21 +0000</td>
</tr>
<tr>
<td>요청/응답 쌍 ID</td>
<td><code>[137]</code></td>
</tr>
<tr>
<td>HTTP 메서드</td>
<td>POST</td>
</tr>
<tr>
<td>URL</td>
<td>/conf/global/settings/dam/adminui-extension/metadataprofile/</td>
</tr>
<tr>
<td>프로토콜</td>
<td>HTTP/1.1
</td>
</tr>
<tr>
<td>AEM as a Cloud Service 노드 ID</td>
<td>[cm-p1234-e5678-aem-author-59555cb5b8-q7l9s]</td>
</tr>
</tbody>
</table>

### 로그 구성 {#configuring-the-log}

AEM AEM HTTP 요청 로그는 as a Cloud Service으로 구성할 수 없습니다.

## AEM HTTP 액세스 로깅 {#aem-http-access-logging}

AEM as Cloud Service HTTP 액세스 로깅은 HTTP 요청을 시간 순서로 표시합니다. 각 로그 항목은 AEM에 액세스하는 HTTP 요청을 나타냅니다.

이 로그는 AEM에 대해 수행 중인 HTTP 요청, 함께 제공되는 HTTP 응답 상태 코드를 보고 성공하는 경우 및 HTTP 요청이 완료되는 데 걸린 시간을 빠르게 이해하는 데 유용합니다. 이 로그는 사용자별로 로그 항목을 필터링하여 특정 사용자의 활동을 디버깅하는 데에도 도움이 될 수 있습니다.

**로그 출력 예**

```
cm-p1234-e26813-aem-author-59555cb5b8-8kgr2 - example@adobe.com 30/Apr/2020:17:37:14 +0000  "GET /libs/granite/ui/references/clientlibs/references.lc-5188e85840c529149e6cd29d94e74ad5-lc.min.css HTTP/1.1" 200 1141 "https://author-p10711-e26813.adobeaemcloud.com/mnt/overlay/dam/gui/content/assets/metadataeditor.external.html?item=/content/dam/en/images/example.jpeg&_charset_=utf8" "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_4) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/81.0.4044.122 Safari/537.36"
cm-p1234-e26813-aem-author-59555cb5b8-8kgr2 - example@adobe.com 30/Apr/2020:17:37:14 +0000  "GET /libs/dam/gui/coral/components/admin/customthumb/clientlibs.lc-60e4443805c37afa0c74b674b141f1df-lc.min.css HTTP/1.1" 200 809 "https://author-p10711-e26813.adobeaemcloud.com/mnt/overlay/dam/gui/content/assets/metadataeditor.external.html?item=/content/dam/en/images/example.jpeg&_charset_=utf8" "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_4) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/81.0.4044.122 Safari/537.36"
cm-p1234-e26813-aem-author-59555cb5b8-8kgr2 - example@adobe.com 30/Apr/2020:17:37:14 +0000  "GET /libs/dam/gui/coral/components/admin/metadataeditor/clientlibs/metadataeditor.lc-4a2226d8232f8b7ab27d24820b9ddd64-lc.min.js HTTP/1.1" 200 7965 "https://author-p10711-e26813.adobeaemcloud.com/mnt/overlay/dam/gui/content/assets/metadataeditor.external.html?item=/content/dam/en/images/example.jpeg&_charset_=utf8" "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_4) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/81.0.4044.122 Safari/537.36"
```

| AEM as a Cloud Service 노드 ID | cm-p1235-e2644-aem-author-59555cb5b8-8kgr2 |
|---|---|
| 클라이언트의 IP 주소 | - |
| 사용자 | myuser@adobe.com |
| 날짜 및 시간 | 30/4/2020:17:37:14 +0000 |
| HTTP 메서드 | GET |
| URL | `/libs/granite/ui/references/clientlibs/references.lc-5188e85840c529149e6cd29d94e74ad5-lc.min.css` |
| 프로토콜 | HTTP/1.1 |
| HTTP 응답 상태 | 200 |
| 응답 본문 크기(바이트) | 1141 |
| 레퍼러 | `"https://author-p1234-e4444.adobeaemcloud.com/mnt/overlay/dam/gui/content/assets/metadataeditor.external.html?item=/content/dam/wknd/en/adventures/surf-camp-in-costa-rica/adobestock_266405335.jpeg&_charset_=utf8"` |
| 사용자 에이전트 | `"Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_4) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/81.0.4044.122 Safari/537.36"` |

### HTTP 액세스 로그 구성 {#configuring-the-http-access-log}

HTTP 액세스 로그는 AEM as a Cloud Service으로 구성할 수 없습니다.

## Apache 웹 서버 및 Dispatcher 로깅 {#apache-web-server-and-dispatcher-logging}

AEM as a Cloud Service에서는 게시에서 Apache 웹 서버 및 Dispatcher 계층에 대해 세 개의 로그를 제공합니다.

* Apache HTTPD 웹 서버 액세스 로그
* Apache HTTPD 웹 서버 오류 로그
* Dispatcher 로그

이러한 로그는 게시 계층에만 사용할 수 있습니다.

이 로그 세트는 HTTP 요청이 AEM 애플리케이션에 도달하기 전에 AEM as a Cloud Service 게시 계층에 대한 HTTP 요청에 대한 통찰력을 제공합니다. 게시 계층 서버에 대한 대부분의 HTTP 요청은 Apache HTTPD 웹 서버 및 AEM Dispatcher에 의해 캐시된 콘텐츠에서 제공되므로 AEM 애플리케이션 자체에는 절대 도달하지 않는다는 것을 이해하는 것이 중요합니다. 따라서 AEM Java, 요청 또는 액세스 로그에는 이러한 요청에 대한 로그 구문이 없습니다.

### Apache HTTPD 웹 서버 액세스 로그 {#apache-httpd-web-server-access-log}

Apache HTTP 웹 서버 액세스 로그는 게시 계층의 웹 서버/Dispatcher에 도달하는 각 HTTP 요청에 대한 문을 제공합니다. 업스트림 CDN에서 제공되는 요청은 이러한 로그에 반영되지 않습니다.

오류 로그 형식에 대한 자세한 내용은 [공식 apache 설명서](https://httpd.apache.org/docs/2.4/logs.html#accesslog).

**로그 출력 예**

```
cm-p1234-e5678-aem-publish-b86c6b466-qpfvp - - 17/Jul/2020:09:14:41 +0000  "GET /etc.clientlibs/wknd/clientlibs/clientlib-site/resources/images/favicons/favicon-32.png HTTP/1.1" 200 715 "-" "Mozilla/5.0 (Macintosh; Intel Mac OS X 10.15; rv:78.0) Gecko/20100101 Firefox/78.0"
cm-p1234-e5678-aem-publish-b86c6b466-qpfvp - - 17/Jul/2020:09:14:41 +0000  "GET /etc.clientlibs/wknd/clientlibs/clientlib-site/resources/images/favicons/favicon-512.png HTTP/1.1" 200 9631 "-" "Mozilla/5.0 (Macintosh; Intel Mac OS X 10.15; rv:78.0) Gecko/20100101 Firefox/78.0"
cm-p1234-e5678-aem-publish-b86c6b466-qpfvp - - 17/Jul/2020:09:14:42 +0000  "GET /etc.clientlibs/wknd/clientlibs/clientlib-site/resources/images/country-flags/US.svg HTTP/1.1" 200 810 "https://publish-p6902-e30226.adobeaemcloud.com/content/wknd/us/en.html" "Mozilla/5.0 (Macintosh; Intel Mac OS X 10.15; rv:78.0) Gecko/20100101 Firefox/78.0"
```

**로그 형식**

<table>
<tbody>
<tr>
<td>AEM as a Cloud Service 노드 ID</td>
<td>cm-p1234-e26813-aem-publish-5c787687c-lqlxr</td>
</tr>
<tr>
<td>클라이언트의 IP 주소</td>
<td>-</td>
</tr>
<tr>
<td>사용자</td>
<td>-</td>
</tr>
<tr>
<td>날짜 및 시간</td>
<td>01/5/2020:00:09:46 +0000</td>
</tr>
<tr>
<td>HTTP 메서드</td>
<td>GET</td>
</tr>
<tr>
<td>URL</td>
<td>/content/example.html</td>
</tr>
<tr>
<td>프로토콜</td>
<td>HTTP/1.1</td>
</tr>
<tr>
<td>HTTP 응답 상태</td>
<td>200</td>
</tr>
<tr>
<td>크기</td>
<td>310</td>
</tr>
<tr>
<td>Referer</td>
<td>-</td>
</tr>
<tr>
<td>사용자 에이전트</td>
<td>"Mozilla/5.0 (Macintosh, Intel Mac OS X 10_15_4) AppleWebKit/537.36 (KHTML, Gecko) Chrome/81.0.4044.122 Safari/537.36"</td>
</tr>
</tbody>
</table>

### Apache HTTPD 웹 서버 액세스 로그 구성 {#configuring-the-apache-httpd-webs-server-access-log}

이 로그는 AEM as a Cloud Service으로 구성할 수 없습니다.

## Apache HTTPD 웹 서버 오류 로그 {#apache-httpd-web-server-error-log}

Apache HTTP 웹 서버 오류 로그는 게시 계층의 웹 서버/Dispatcher에 있는 각 오류에 대한 문을 제공합니다.

오류 로그 형식에 대한 자세한 내용은 [공식 apache 설명서](https://httpd.apache.org/docs/2.4/logs.html#errorlog).

**로그 출력 예**

```
Fri Jul 17 02:19:48.093820 2020 [mpm_worker:notice] [pid 1:tid 140272153361288] [cm-p1234-e30226-aem-publish-b86c6b466-b9427] AH00292: Apache/2.4.43 (Unix) Communique/4.3.4-20200424 mod_qos/11.63 configured -- resuming normal operations
Fri Jul 17 02:19:48.093874 2020 [core:notice] [pid 1:tid 140272153361288] [cm-p1234-e30226-aem-publish-b86c6b466-b9427] AH00094: Command line: 'httpd -d /etc/httpd -f /etc/httpd/conf/httpd.conf -D FOREGROUND -D ENVIRONMENT_PROD'
Fri Jul 17 02:29:34.517189 2020 [mpm_worker:notice] [pid 1:tid 140293638175624] [cm-p1234-e30226-aem-publish-b496f64bf-5vckp] AH00295: caught SIGTERM, shutting down
```

**로그 형식**

<table>
<tbody>
<tr>
<td>날짜 및 시간</td>
<td>2002년 7월 17일 금요일:16:42.608913 2020</td>
</tr>
<tr>
<td>이벤트 수준</td>
<td>[mpm_worker:notice]</td>
</tr>
<tr>
<td>프로세스 ID</td>
<td>[pid 1:tid 140715149343624]</td>
</tr>
<tr>
<td>Pod 이름</td>
<td>[cm-p1234-e56789-aem-publish-b86c6b466-qpfvp]</td>
</tr>
<tr>
<td>메시지</td>
<td>AH00094: 명령줄: 'httpd -d /etc/httpd -f /etc/httpd/conf/httpd.conf -D FOREGROUND -D </td>
</tr>
</tbody>
</table>

### Apache HTTPD 웹 서버 오류 로그 구성 {#configuring-the-apache-httpd-web-server-error-log}

mod_rewrite 로그 레벨은 파일에서 REWRITE_LOG_LEVEL 변수에 의해 정의됩니다 `conf.d/variables/global.var`.

error, warn, info, debug 및 trace1 - trace8로 설정할 수 있으며 기본값은 warn입니다. RewriteRules를 디버깅하려면 로그 수준을 trace2로 높이는 것이 좋습니다. 다음을 사용하여 규칙 다시 작성을 디버그하는 것이 좋습니다. [Dispatcher SDK](../../dispatcher/validation-debug.md). AEM as a Cloud Service의 최대 로그 수준은 `debug`. 따라서 현재 클라우드에서 재작성 규칙을 디버깅하는 것이 효과적으로 불가능합니다.

다음을 참조하십시오. [mod_rewrite 모듈 설명서](https://httpd.apache.org/docs/current/mod/mod_rewrite.html#logging) 추가 정보.

환경당 로그 수준을 설정하려면 아래에 설명된 대로 global.var 파일에서 적절한 조건부 분기를 사용합니다.

```
Define REWRITE_LOG_LEVEL debug
  
<IfDefine ENVIRONMENT_STAGE>
  ...
  Define REWRITE_LOG_LEVEL warn
  ...
</IfDefine>
<IfDefine ENVIRONMENT_PROD>
  ...
  Define REWRITE_LOG_LEVEL error
  ...
</IfDefine>
```

## Dispatcher 로그 {#dispatcher-log}

**예**

```
[17/Jul/2020:23:48:06 +0000] [I] [cm-p12904-e25628-aem-publish-6c5f7c9dbd-mzcvr] "GET /content/wknd/us/en/adventures.html" - 475ms [publishfarm/0] [action miss] "publish-p12904-e25628.adobeaemcloud.com"
[17/Jul/2020:23:48:07 +0000] [I] [cm-p12904-e25628-aem-publish-6c5f7c9dbd-mzcvr] "GET /content/wknd/us/en/adventures/climbing-new-zealand/_jcr_content/root/responsivegrid/carousel/item_1571266094599.coreimg.jpeg/1473680817282/sport-climbing.jpeg" 302 10ms [publishfarm/0] [action none] "publish-p12904-e25628.adobeaemcloud.com"
[17/Jul/2020:23:48:07 +0000] [I] [cm-p12904-e25628-aem-publish-6c5f7c9dbd-mzcvr] "GET /content/wknd/us/en/adventures/ski-touring-mont-blanc/_jcr_content/root/responsivegrid/carousel/item_1571168419252.coreimg.jpeg/1572047288089/adobestock-238230356.jpeg" 302 11ms [publishfarm/0] [action none] "publish-p12904-e25628.adobeaemcloud.com"
```

**로그 형식**

<table>
<tbody>
<tr>
<td>날짜 및 시간</td>
<td>[17/2020년 7월:23:48:16 +0000]</td>
</tr>
<tr>
<td>Pod 이름</td>
<td>[cm-p12904-e25628-aem-publish-6c5f7c9dbd-mzcvr]</td>
</tr>
<tr>
<td>프로토콜</td>
<td>GET</td>
</tr>
<tr>
<td>URL</td>
<td>/content/experience-fragments/wknd/language-masters/en/contributors/sofia-sjoeberg/master/_jcr_content/root/responsivegrid/image.coreimg.100.500.jpeg/1572236359031/ayo-ogunseinde-237739.jpeg</td>
</tr>
<tr>
<td>Dispatcher 응답 상태 코드</td>
<td>/content/experience-fragments/wknd/language-masters/en/contributors/sofia-sjoeberg/master/_jcr_content/root/responsivegrid/image.coreimg.100.500.jpeg/1572236359031/ayo-ogunseinde-237739.jpeg</td>
</tr>
<tr>
<td>기간</td>
<td>1949밀리초</td>
</tr>
<tr>
<td>농장</td>
<td>[publishfarm/0]</td>
</tr>
<tr>
<td>캐시 상태</td>
<td>[액션 누락]</td>
</tr>
<tr>
<td>호스트</td>
<td>"publish-p12904-e25628.adobeaemcloud.com"</td>
</tr>
</tbody>
</table>

### Dispatcher 오류 로그 구성 {#configuring-the-dispatcher-error-log}

Dispatcher 로그 수준은 파일의 DISP_LOG_LEVEL 변수에 의해 정의됩니다 `conf.d/variables/global.var`.

기본값이 warn인 error, warn, info, debug 및 trace1로 설정할 수 있습니다.

AEM Dispatcher 로깅은 다른 여러 수준의 로깅 세부기간을 지원하지만 아래 설명된 수준을 as a Cloud Service으로 사용하는 것이 좋습니다.

환경당 로그 수준을 설정하려면 `global.var` 아래에 설명된 대로 파일을 작성합니다.

```
Define DISP_LOG_LEVEL debug
  
<IfDefine ENVIRONMENT_STAGE>
  ...
  Define DISP_LOG_LEVEL warn
  ...
</IfDefine>
<IfDefine ENVIRONMENT_PROD>
  ...
  Define DISP_LOG_LEVEL error
  ...
</IfDefine>
```

>[!NOTE]
>
>AEM as a Cloud Service 환경의 경우 debug는 최대 세부 정보 수준입니다. 추적 로그 수준은 지원되지 않으므로 클라우드 환경에서 작업할 때 이 수준을 설정하지 않아야 합니다.

## CDN 로그 {#cdn-log}

AEM as a Cloud Service에서는 캐시 적중률 최적화를 포함한 사용 사례에 유용한 CDN 로그에 액세스할 수 있습니다. CDN 로그 형식은 사용자 지정할 수 없으며 정보, 경고 또는 오류와 같은 다양한 모드로 설정하는 개념이 없습니다.

CDN 로그는 새로운 Splunk 전달 지원 티켓 요청을 위해 Splunk에 전달됩니다. 이미 Splunk 전달이 활성화된 고객은 향후 CDN 로그를 추가할 수 있습니다.

**예**

```
{
"timestamp": "2023-05-26T09:20:01+0000",
"ttfb": 19,
"cli_ip": "147.160.230.112",
"cli_country": "CH",
"rid": "974e67f6",
"req_ua": "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/605.1.15 (KHTML, like Gecko) Version/14.0.3 Safari/605.1.15",
"host": "example.com",
"url": "/content/hello.png",
"method": "GET",
"res_ctype": "image/png",
"cache": "PASS",
"status": 200,
"res_age": 0,
"pop": "PAR",
"rules": "match=Enable-SQL-Injection-and-XSS-waf-rules-globally,waf=SQLI,action=blocked"
}
```

**로그 형식**

CDN 로그는 json 형식을 준수한다는 점에서 다른 로그와 구별됩니다.

| **필드 이름** | **설명** |
|---|---|
| *timestamp* | TLS 종료 후 요청이 시작된 시간입니다. |
| *ttfb* | *Time To First Byte(첫 번째 바이트까지의 시간)*&#x200B;의 약어입니다. 요청이 시작된 후 응답 본문의 스트리밍이 시작되기까지의 시간 간격입니다. |
| *cli_ip* | 클라이언트 IP 주소입니다. |
| *cli_country* | 클라이언트 국가의 2글자 [ISO 3166-1](https://en.wikipedia.org/wiki/kr/ISO_3166-1) Alpha-2 국가 코드입니다. |
| *rid* | 요청을 고유하게 식별하는 데 사용되는 요청 헤더의 값입니다. |
| *req_ua* | 해당 HTTP 요청을 담당하는 사용자 에이전트입니다. |
| *host* | 요청이 의도한 대상 기관입니다. |
| *url* | 쿼리 매개변수를 포함한 전체 경로입니다. |
| *메서드* | “GET” 또는 “POST”와 같은 클라이언트에서 전송한 HTTP 메서드입니다. |
| *res_ctype* | 리소스의 원래 미디어 유형을 나타내는 데 사용되는 콘텐츠 유형입니다. |
| *cache* | 캐시의 상태입니다. 가능한 값은 HIT, MISS 또는 PASS입니다. |
| *상태* | HTTP 상태 코드입니다(정수 값). |
| *res_age* | 모든 노드에서 응답이 캐시되는 데 소요되는 시간(초)입니다. |
| *pop* | CDN 캐시 서버의 데이터센터입니다. |
| *rules* | 일치하는 모든 이름 [트래픽 필터 규칙](/help/security/traffic-filter-rules-including-waf.md) 및 WAF 플래그(일치 결과 블록 발생 여부를 나타냄) 일치하는 규칙이 없으면 비어 있습니다. |


## 로그 액세스 방법 {#how-to-access-logs}

### 클라우드 환경 {#cloud-environments}

클라우드 서비스용 AEM as a Cloud Service 로그는 Cloud Manager 인터페이스를 통해 다운로드하거나 Adobe I/O 명령줄 인터페이스를 사용하여 명령줄에서 로그를 테일링하여 액세스할 수 있습니다. 자세한 내용은 [Cloud Manager 로깅 설명서](/help/implementing/cloud-manager/manage-logs.md).

### 추가 게시 영역에 대한 로그 {#logs-for-additional-publish-regions}

특정 환경에 대해 추가 게시 영역이 활성화된 경우 위에서 언급한 대로 Cloud Manager에서 각 영역에 대한 로그를 다운로드할 수 있습니다.

추가 게시 영역에 대한 AEM 로그 및 Dispatcher 로그는 환경 ID 다음의 처음 3자로 영역을 지정합니다. **nld2** 아래 샘플에서는 네덜란드에 있는 추가 AEM 게시 인스턴스를 참조하며,

```
cm-p7613-e12700-nld2-aem-publish-bcbb77549-5qmmt 127.0.0.1 - 07/Nov/2023:23:57:11 +0000 "HEAD /libs/granite/security/currentuser.json HTTP/1.1" 200 - "-" "Java/11.0.19"
```

### 로컬 SDK {#local-sdk}

AEM as a Cloud Service SDK는 로컬 개발을 지원하기 위한 로그 파일을 제공합니다.

AEM 로그는 폴더에 있습니다. `crx-quickstart/logs`: 여기에서 다음 로그를 볼 수 있습니다.

* AEM Java 로그: `error.log`
* AEM HTTP 요청 로그: `request.log`
* AEM HTTP 액세스 로그: `access.log`

Dispatcher를 포함한 Apache 계층 로그는 Dispatcher를 보유하는 Docker 컨테이너에 있습니다. 다음을 참조하십시오. [Dispatcher 설명서](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/content-delivery/disp-overview.html) Dispatcher를 시작하는 방법에 대한 자세한 정보.

로그를 검색하려면 다음을 수행하십시오.

1. 명령줄에서 을(를) 입력합니다 `docker ps` 컨테이너를 나열하려면
1. 컨테이너에 로그인하려면 &quot;`docker exec -it <container> /bin/sh`&quot;, 여기서 `<container>` 는 이전 단계의 Dispatcher 컨테이너 id입니다
1. 아래의 캐시 루트로 이동합니다. `/mnt/var/www/html`
1. 로그가 아래에 있습니다. `/etc/httpd/logs`
1. Inspect 로그: XYZ 폴더 아래에서 액세스할 수 있으며 여기에서 다음 로그를 볼 수 있습니다.
   * Apache HTTPD 웹 서버 액세스 로그 - `httpd_access.log`
   * Apache HTTPD 웹 서버 오류 로그 - `httpd_error.log`
   * 디스패처 로그 - `dispatcher.log`

로그 또한 터미널 출력으로 직접 인쇄됩니다. 대부분의 경우 이러한 로그는 DEBUG여야 하며, 이는 Docker를 실행할 때 디버그 수준을 매개 변수로 전달하여 수행할 수 있습니다. 예:

`DISP_LOG_LEVEL=Debug ./bin/docker_run.sh out docker.for.mac.localhost:4503 8080`

## 프로덕션 및 스테이지 디버깅 {#debugging-production-and-stage}

예외적인 경우 스테이지 또는 프로덕션 환경에서 더 세분화된 단위로 기록하려면 로그 수준을 변경해야 합니다.

AEM 이 작업은 가능하지만 Git의 구성 파일에 있는 로그 수준을 경고와 오류에서 디버그로 변경하고, 이러한 구성 변경 사항을 환경에 등록하기 위해 as a Cloud Service으로 배포를 수행해야 합니다.

트래픽과 Debug에서 작성한 로그 구문의 양에 따라 환경에 부정적인 성능 영향을 줄 수 있으므로 스테이지 및 프로덕션 디버그 수준의 변경 사항은 다음과 같은 것이 좋습니다.

* 신중하게, 그리고 절대적으로 필요한 경우에만 수행
* 적절한 수준으로 되돌리고 가능한 한 빨리 다시 배포합니다.

## Splunk 로그 {#splunk-logs}

Splunk 계정이 있는 고객은 고객 지원 티켓을 통해 AEM Cloud Service 로그가 적절한 색인에 전달되도록 요청할 수 있습니다. 로깅 데이터는 Cloud Manager 로그 다운로드를 통해 사용할 수 있는 것과 동일하지만 고객은 Splunk 제품에서 사용할 수 있는 쿼리 기능을 사용하는 것이 편리할 수 있습니다.

Splunk로 전송된 로그와 관련된 네트워크 대역폭은 고객의 네트워크 I/O 사용의 일부로 간주됩니다.

CDN 로그는 새 지원 티켓 요청을 위해 Splunk에 전달됩니다. 이미 Splunk 전달이 활성화된 고객은 향후 CDN 로그를 추가할 수 있습니다.

### Splunk 전달 활성화 {#enabling-splunk-forwarding}

지원 요청에서 고객은 다음을 명시해야 합니다.

* Splunk HEC 끝점 주소입니다. 이 끝점에는 유효한 SSL 인증서가 있어야 하며 공개적으로 액세스할 수 있습니다.
* Splunk 인덱스
* Splunk 포트
* Splunk HEC 토큰. 다음을 참조하십시오 [이 페이지](https://docs.splunk.com/Documentation/Splunk/8.0.4/Data/HECExamples) 추가 정보.

위의 속성은 각 관련 프로그램/환경 유형 조합에 대해 지정해야 합니다. 예를 들어 고객이 개발, 스테이징 및 프로덕션 환경을 원하는 경우 아래에 표시된 대로 세 가지 정보 세트를 제공해야 합니다.

>[!NOTE]
>
>샌드박스 프로그램 환경에 대한 Splunk 전달은 지원되지 않습니다.

>[!NOTE]
>
>전용 이그레스 IP 주소에서는 Splunk 전달 기능을 사용할 수 없습니다.

초기 요청에 단계/프로덕션 환경 외에 활성화해야 하는 모든 개발 환경이 포함되어 있는지 확인해야 합니다. Splunk에는 SSL 인증서가 있어야 하며 공개 대상이어야 합니다.

초기 요청 후 생성된 새 개발 환경이 Splunk 전달을 사용하려고 하지만 활성화되지 않은 경우 추가 요청을 수행해야 합니다.

또한 개발 환경이 요청된 경우 요청에 없는 다른 개발 환경이나 샌드박스 환경에서도 Splunk 전달이 활성화되고 Splunk 인덱스를 공유할 수 있습니다. 고객은 `aem_env_id` 이러한 환경을 구분하는 필드입니다.

아래에 샘플 고객 지원 요청이 있습니다.

프로그램 123, 프로덕션 환경

* Splunk HEC 끝점 주소: `splunk-hec-ext.acme.com`
* Splunk index: acme_123prod(고객은 원하는 명명 규칙을 선택할 수 있음)
* Splunk 포트: 443
* Splunk HEC 토큰: ABC123

프로그램 123, Stage 환경

* Splunk HEC 끝점 주소: `splunk-hec-ext.acme.com`
* Splunk 색인: acme_123stage
* Splunk 포트: 443
* Splunk HEC 토큰: ABC123

프로그램 123, 개발 Envs

* Splunk HEC 끝점 주소: `splunk-hec-ext.acme.com`
* Splunk 인덱스: acme_123dev
* Splunk 포트: 443
* Splunk HEC 토큰: ABC123

각 환경에 대해 동일한 Splunk 인덱스를 사용해도 충분할 수 있으며, 이 경우 다음 중 하나를 수행합니다. `aem_env_type` 필드는 dev, stage 및 prod 값을 기준으로 구분하는 데 사용할 수 있습니다. 개발 환경이 여러 개인 경우 `aem_env_id` 필드를 사용할 수도 있습니다. 일부 조직에서는 관련 색인이 축소된 Splunk 사용자 집합에 대한 액세스를 제한하는 경우 프로덕션 환경의 로그에 대해 별도의 색인을 선택할 수 있습니다.

다음은 로그 항목의 예입니다.

```
aem_env_id: 1242
aem_env_type: dev
aem_program_id: 12314
aem_tier: author
file_path: /var/log/aem/error.log
host: 172.34.200.12 
level: INFO
msg: [FelixLogListener] com.adobe.granite.repository Service [5091, [org.apache.jackrabbit.oak.api.jmx.SessionMBean]] ServiceEvent REGISTERED
orig_time: 16.07.2020 08:35:32.346
pod_name: aemloggingall-aem-author-77797d55d4-74zvt
splunk_customer: true
```
