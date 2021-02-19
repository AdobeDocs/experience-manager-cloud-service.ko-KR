---
title: 로깅
description: 중앙 로깅 서비스에 대한 전역 매개 변수, 개별 서비스에 대한 특정 설정 또는 데이터 로깅을 요청하는 방법을 알아봅니다.
translation-type: tm+mt
source-git-commit: 17ba5068b0df0724bcebeecb2323b7dcdc8d8cfa
workflow-type: tm+mt
source-wordcount: '2314'
ht-degree: 3%

---


# 로깅 {#logging}

Cloud Service은 고객이 고객층마다 고유한 경험을 만들 수 있도록 사용자 정의 코드를 포함하는 플랫폼입니다. 이러한 점을 염두에 두고 로깅은 로컬 개발 및 클라우드 환경에서 코드 실행을 디버깅하고 이해하기 위한 중요한 기능이며, 특히 Cloud Service의 개발 환경인 AEM도 이 기능을 사용합니다.

AEM 로깅 및 로그 수준은 Git에서 AEM 프로젝트의 일부로 저장되어 Cloud Manager를 통해 AEM 프로젝트의 일부로 배포되는 구성 파일에서 관리됩니다. Cloud Service으로 AEM에 로그인하면 두 개의 논리 세트로 나눌 수 있습니다.

* AEM 응용 프로그램 수준에서 로깅을 수행하는 AEM 로깅
* 게시 계층에서 웹 서버 및 디스패처의 로깅을 수행하는 Apache HTTPD 웹 서버/디스패처 로깅.

## AEM 로깅 {#aem-loggin}

AEM 응용 프로그램 수준에서 로깅은 3개의 로그로 처리됩니다.

1. AEM Java 로그. AEM 응용 프로그램에 대한 Java 로깅 문을 렌더링합니다.
1. HTTP 요청 로그 - AEM에서 제공하는 HTTP 요청 및 응답에 대한 정보를 기록합니다.
1. AEM에서 제공하는 요약 정보 및 HTTP 요청을 기록하는 HTTP 액세스 로그

>[!NOTE]
>
>게시 계층의 Dispatcher 캐시나 업스트림 CDN에서 제공되는 HTTP 요청은 이러한 로그에 반영되지 않습니다.

## AEM Java 로깅 {#aem-java-logging}

AEM as a Cloud Service은 Java 로그 문에 대한 액세스를 제공합니다. AEM용 애플리케이션 개발자는 다음 로그 수준에서 일반적인 Java 로깅 우수 사례를 따르고 사용자 정의 코드 실행에 대한 관련 문을 로깅해야 합니다.

<table>
<tr>
<td>
<b>AEM 환경</b></td>
<td>
<b>로그 수준</b></td>
<td>
<b>설명</b></td>
<td>
<b>로그 문 사용 가능 여부</b></td>
</tr>
<tr>
<td>
개발</td>
<td>
디버그</td>
<td>
애플리케이션에서 발생하는 작업을 설명합니다.<br>
DEBUG 로깅이 활성화되면 어떤 활동이 발생하는지 명확하게 파악하고 처리에 영향을 주는 주요 매개 변수를 제공하는 문이 기록됩니다.</td>
<td>
<ul>
<li> 로컬 개발</li>
<li>개발</li>
</ul></td>
</tr>
<tr>
<td>
단계</td>
<td>
경고</td>
<td>
오류가 될 가능성이 있는 조건을 설명합니다.<br>
WARN 로깅이 활성화되면 하위 최적화에 접근하는 조건을 나타내는 명령문만 기록됩니다.</td>
<td>
<ul>
<li> 로컬 개발</li>
<li>개발</li>
<li>단계</li>
</ul></td>
</tr>
<tr>
<td>
프로덕션</td>
<td>
오류</td>
<td>
실패를 나타내고 이를 해결해야 하는 조건을 설명합니다.<br>
ERROR 로깅이 활성화되면 오류를 나타내는 명령문만 기록됩니다. 오류 로그 명령문은 가능한 빨리 해결해야 하는 심각한 문제를 나타냅니다.</td>
<td>
<ul>
<li> 로컬 개발</li>
<li>개발</li>
<li>단계</li>
<li>프로덕션</li>
</ul></td>
</tr>
</table>

Java 로깅은 몇 가지 다른 로깅 세부기간 수준을 지원하지만, Cloud Service은 위에서 설명한 3가지 수준을 사용하는 것이 좋습니다.

AEM 로그 수준은 OSGi 구성을 통해 환경 유형별로 설정되며, 이 구성 역시 Git에 커밋되고 Cloud Manager를 통해 AEM을 통해 Cloud Service으로 배포됩니다. 따라서 업데이트된 로그 수준 구성을 사용하여 애플리케이션을 다시 배포하지 않고도 AEM을 통해 Cloud Service으로 사용할 수 있는 로그를 최적의 로그 수준에서 사용할 수 있도록 하기 위해 로그 문을 일관되게 유지하는 것이 좋습니다.

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
<td>Cloud Service 노드 ID로 AEM</td>
<td>[cm-p1234-e5678-aem-author-5955cb5b8-q7l9s]</td>
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
<td>지정된 승인자가 없습니다. [ 크리에이티브 승인자 사용자 그룹 ] 로 기본 설정됩니다.</td>
</tr>
</tbody>
</table>

### 구성 로거 {#configuration-loggers}

AEM Java 로그는 OSGi 구성으로 정의되므로 실행 모드 폴더를 사용하는 Cloud Service 환경으로 특정 AEM을 타깃팅합니다.

Sling LogManager 팩터리에 대한 OSGi 구성을 통해 사용자 지정 Java 패키지에 대한 Java 로깅을 구성합니다. 지원되는 구성 속성은 두 가지가 있습니다.

| OSGi 구성 속성 | 설명 |
|---|---|
| org.apache.sling.commons.log.names | 로그 문을 수집할 Java 패키지. |
| org.apache.sling.commons.log.level | org.apache.sling.commons.log.names에 의해 지정된 Java 패키지를 기록할 로그 수준 |

다른 LogManager OSGi 구성 속성을 변경하면 AEM에서 Cloud Service으로 가용성 문제가 발생할 수 있습니다.

다음은 Cloud Service 환경 유형으로 3개의 AEM에 대한 권장 로깅 구성(자리 표시자 Java 패키지 `com.example` 사용)의 예입니다.

### 개발 {#development}

/apps/my-app/config/org.apache.sling.commons.log.LogManager.factory.config-example.cfg.json

```
{
    "org.apache.sling.commons.log.names": ["com.example"],
    "org.apache.sling.commons.log.level": "debug"
}
```

### 단계 {#stage}

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

AEM은 Cloud Service의 HTTP 요청 로깅으로 AEM에 대한 HTTP 요청과 해당 HTTP 응답에 대한 통찰력을 시간 순서로 제공합니다. 이 로그는 AEM에 대한 HTTP 요청 및 처리 및 응답의 순서를 이해하는 데 도움이 됩니다.

이 로그를 이해하는 열쇠는 대괄호 안의 숫자 값으로 나타내는 ID로 HTTP 요청 및 응답 쌍을 매핑하는 것입니다. 요청과 해당 응답에는 로그에 있는 다른 HTTP 요청과 응답 간에 상호 작용한 경우가 많습니다.

**예제 로그**

```
29/Apr/2020:19:14:21 +0000 [137] -> POST /conf/global/settings/dam/adminui-extension/metadataprofile/ HTTP/1.1 [cm-p1234-e5678-aem-author-59555cb5b8-q7l9s]
...
29/Apr/2020:19:14:22 +0000 [139] -> GET /mnt/overlay/dam/gui/content/processingprofilepage/metadataprofiles/editor.html/conf/global/settings/dam/adminui-extension/metadataprofile/main HTTP/1.1 [cm-p1234-e5678-aem-author-59555cb5b8-q7l9s]
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
<td>Cloud Service 노드 ID로 AEM</td>
<td>[cm-p1234-e5678-aem-author-5955cb5b8-q7l9s]</td>
</tr>
</tbody>
</table>

### 로그 {#configuring-the-log} 구성

AEM HTTP 요청 로그는 AEM에서 Cloud Service으로 구성할 수 없습니다.

## AEM HTTP 액세스 로깅 {#aem-http-access-logging}

AEM의 Cloud Service HTTP 액세스 로깅은 HTTP 요청을 시간 순서대로 표시합니다. 각 로그 항목은 AEM에 액세스하는 HTTP 요청을 나타냅니다.

이 로그는 AEM에 대한 HTTP 요청의 내용과 함께 제공되는 HTTP 응답 상태 코드 및 HTTP 요청이 완료되는 데 걸린 시간을 확인하는 데 성공한 경우 이를 빨리 이해하는 데 도움이 됩니다. 이 로그는 사용자별로 로그 항목을 필터링하여 특정 사용자의 활동을 디버깅하는 데 도움이 될 수 있습니다.

**로그 출력 예**

```
cm-p1234-e26813-aem-author-59555cb5b8-8kgr2 - example@adobe.com 30/Apr/2020:17:37:14 +0000  "GET /libs/granite/ui/references/clientlibs/references.lc-5188e85840c529149e6cd29d94e74ad5-lc.min.css HTTP/1.1" 200 1141 "https://author-p10711-e26813.adobeaemcloud.com/mnt/overlay/dam/gui/content/assets/metadataeditor.external.html?item=/content/dam/en/images/example.jpeg&_charset_=utf8" "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_4) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/81.0.4044.122 Safari/537.36"
cm-p1234-e26813-aem-author-59555cb5b8-8kgr2 - example@adobe.com 30/Apr/2020:17:37:14 +0000  "GET /libs/dam/gui/coral/components/admin/customthumb/clientlibs.lc-60e4443805c37afa0c74b674b141f1df-lc.min.css HTTP/1.1" 200 809 "https://author-p10711-e26813.adobeaemcloud.com/mnt/overlay/dam/gui/content/assets/metadataeditor.external.html?item=/content/dam/en/images/example.jpeg&_charset_=utf8" "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_4) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/81.0.4044.122 Safari/537.36"
cm-p1234-e26813-aem-author-59555cb5b8-8kgr2 - example@adobe.com 30/Apr/2020:17:37:14 +0000  "GET /libs/dam/gui/coral/components/admin/metadataeditor/clientlibs/metadataeditor.lc-4a2226d8232f8b7ab27d24820b9ddd64-lc.min.js HTTP/1.1" 200 7965 "https://author-p10711-e26813.adobeaemcloud.com/mnt/overlay/dam/gui/content/assets/metadataeditor.external.html?item=/content/dam/en/images/example.jpeg&_charset_=utf8" "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_4) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/81.0.4044.122 Safari/537.36"
```

**로그 형식**

<table>
<tbody>
<tr>
<td>Cloud Service 노드 ID로 AEM</td>
<td>cm-p1235-e2644-aem-author-5955cb5b8-8kgr2</td>
</tr>
<tr>
<td>클라이언트의 IP 주소</td>
<td>-</td>
</tr>
<tr>
<td>사용자</td>
<td>myuser@adobe.com</td>
</tr>
<tr>
<td>날짜 및 시간</td>
<td>30/4/2020:17:37:14 +0000</td>
</tr>
<tr>
<td>HTTP 메서드</td>
<td>GET</td>
</tr>
<tr>
<td>URL</td>
<td>/libs/granite/ui/references/clientlibs/references.lc-5188e85840c529149e6cd29d94e74ad5-lc.min.css</td>
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
<td>HTTP 요청 시간(밀리초)</td>
<td>1141년</td>
</tr>
<tr>
<td>레퍼러</td>
<td><code>"https://author-p1234-e4444.adobeaemcloud.com/mnt/overlay/dam/gui/content/assets/metadataeditor.external.html?item=/content/dam/wknd/en/adventures/surf-camp-in-costa-rica/adobestock_266405335.jpeg&_charset_=utf8"</code></td>
</tr>
<tr>
<td>사용자 에이전트</td>
<td>"Mozilla/5.0(Macintosh;Intel Mac OS X 10_15_4) AppleWebKit/537.36(KHTML, 예: Gecko) Chrome/81.0.4044.122 Safari/537.36"</td>
</tr>
</tbody>
</table>

### HTTP 액세스 로그 구성 {#configuring-the-http-access-log}

HTTP 액세스 로그는 AEM에서 Cloud Service으로 구성할 수 없습니다.

## Apache 웹 서버 및 디스패처 로깅 {#apache-web-server-and-dispatcher-logging}

AEM은 Publish에서 Apache 웹 서버 및 디스패처 레이어에 대해 3개의 로그를 제공합니다.

* Apache HTTPD 웹 서버 액세스 로그
* Apache HTTPD 웹 서버 오류 로그
* 디스패처 로그

이러한 로그는 게시 계층에만 사용할 수 있습니다.

이 로그 세트는 AEM 애플리케이션에 도달하는 요청에 앞서 Cloud Service 게시 계층으로서 AEM에 대한 HTTP 요청에 대한 통찰력을 제공합니다. 이는 Apache HTTPD Web Server 및 AEM Dispatcher에서 캐시하고 AEM 응용 프로그램 자체에 도달할 수 없는 컨텐츠에 의해 게시 계층 서버에 대한 대부분의 HTTP 요청을 제공한다는 점을 이해하는 데 중요합니다. 따라서 AEM Java, 요청 또는 액세스 로그에 이러한 요청에 대한 로그 명령문이 없습니다.

### Apache HTTPD 웹 서버 액세스 로그 {#apache-httpd-web-server-access-log}

Apache HTTP Web Server 액세스 로그는 게시 계층의 웹 서버/디스패처에 도달하는 각 HTTP 요청에 대한 문을 제공합니다. 업스트림 CDN에서 제공되는 요청은 이러한 로그에 반영되지 않습니다.

[공식 apache 설명서](https://httpd.apache.org/docs/2.4/logs.html#accesslog)의 오류 로그 형식에 대한 정보를 참조하십시오.

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
<td>AEM을 클라우드 서비스 노드 ID로 사용</td>
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
<td>200년</td>
</tr>
<tr>
<td>크기</td>
<td>310년</td>
</tr>
<tr>
<td>참조</td>
<td>-</td>
</tr>
<tr>
<td>사용자 에이전트</td>
<td>"Mozilla/5.0(Macintosh;Intel Mac OS X 10_15_4) AppleWebKit/537.36(KHTML, 예: Gecko) Chrome/81.0.4044.122 Safari/537.36"</td>
</tr>
</tbody>
</table>

### Apache HTTPD 웹 서버 액세스 로그 구성 {#configuring-the-apache-httpd-webs-server-access-log}

이 로그는 AEM에서 Cloud Service으로 구성할 수 없습니다.

## Apache HTTPD 웹 서버 오류 로그 {#apache-httpd-web-server-error-log}

Apache HTTP 웹 서버 오류 로그는 게시 계층의 웹 서버/디스패처의 각 오류에 대한 문을 제공합니다.

[공식 apache 설명서](https://httpd.apache.org/docs/2.4/logs.html#errorlog)의 오류 로그 형식에 대한 정보를 참조하십시오.

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
<td>2020년 7월 17일 02:16:42.608913</td>
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
<td>창 이름</td>
<td>[cm-p1234-e56789-aem-publish-b86c6b466-qpfvp]</td>
</tr>
<tr>
<td>메시지</td>
<td>AH00094:명령줄:'httpd -d /etc/httpd -f /etc/httpd/conf/httpd.conf -D FOREGROUND -D </td>
</tr>
</tbody>
</table>

### Apache HTTPD 웹 서버 오류 로그 구성 {#configuring-the-apache-httpd-web-server-error-log}

mod_rewrite 로그 수준은 `conf.d/variables/global.var` 파일의 REWRITE_LOG_LEVEL 변수에 의해 정의됩니다.

이 값은 Warn의 기본값을 사용하여 Error, Warn, Info, Debug 및 Trace1 - Trace8로 설정할 수 있습니다. RewriteRules를 디버깅하려면 로그 수준을 Trace2로 높이는 것이 좋습니다.

자세한 내용은 [mod_rewrite 모듈 설명서](https://httpd.apache.org/docs/current/mod/mod_rewrite.html#logging)를 참조하십시오.

환경별 로그 수준을 설정하려면 아래 설명된 대로 global.var 파일에서 적절한 조건부 분기를 사용하십시오.

```
Define REWRITE_LOG_LEVEL Debug
  
<IfDefine ENVIRONMENT_STAGE>
  ...
  Define REWRITE_LOG_LEVEL Warn
  ...
</IfDefine>
<IfDefine ENVIRONMENT_PROD>
  ...
  Define REWRITE_LOG_LEVEL Error
  ...
</IfDefine>
```

## 발송자 로그 {#dispatcher-log}

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
<td>[17/Jul/2020:23:48:16 +0000]</td>
</tr>
<tr>
<td>창 이름</td>
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
<td>발송자 응답 상태 코드</td>
<td>/content/experience-fragments/wknd/language-masters/en/contributors/sofia-sjoeberg/master/_jcr_content/root/responsivegrid/image.coreimg.100.500.jpeg/1572236359031/ayo-ogunseinde-237739.jpeg</td>
</tr>
<tr>
<td>기간</td>
<td>1949ms</td>
</tr>
<tr>
<td>농장</td>
<td>[publishfarm/0]</td>
</tr>
<tr>
<td>캐시 상태</td>
<td>[작업 누락]</td>
</tr>
<tr>
<td>호스트</td>
<td>"publish-p12904-e25628.adobeaemcloud.com"</td>
</tr>
</tbody>
</table>

### 발송자 오류 로그 구성 {#configuring-the-dispatcher-error-log}

디스패처 로그 수준은 `conf.d/variables/global.var` 파일의 DISP_LOG_LEVEL 변수에 의해 정의됩니다.

이 값은 Warn의 기본값을 사용하여 Error, Warn, Info, Debug 및 Trace1로 설정할 수 있습니다.

Dispatcher 로깅은 몇 가지 다른 로깅 세부기간 수준을 지원하지만 AEM은 Cloud Service으로 아래 설명된 수준을 사용하는 것이 좋습니다.

환경별 로그 수준을 설정하려면 아래 설명에 따라 `global.var` 파일에서 적절한 조건부 분기를 사용하십시오.

```
Define DISP_LOG_LEVEL Debug
  
<IfDefine ENVIRONMENT_STAGE>
  ...
  Define DISP_LOG_LEVEL Warn
  ...
</IfDefine>
<IfDefine ENVIRONMENT_PROD>
  ...
  Define DISP_LOG_LEVEL Error
  ...
</IfDefine>
```

## 로그 {#how-to-access-logs}에 액세스하는 방법

### 클라우드 환경 {#cloud-environments}

클라우드 서비스에 대한 Cloud Service 로그인 AEM은 Cloud Manager 인터페이스를 통해 다운로드하거나 Adobe I/O 명령줄 인터페이스를 사용하여 명령줄에서 로그를 밀어서 액세스할 수 있습니다. 자세한 내용은 [클라우드 관리자 로깅 설명서](/help/implementing/cloud-manager/manage-logs.md)를 참조하십시오.

### 로컬 SDK {#local-sdk}

AEM은 Cloud Service SDK로 로컬 개발을 지원하는 로그 파일을 제공합니다.

AEM 로그는 폴더 `crx-quickstart/logs`에 있으며 여기서 다음 로그를 볼 수 있습니다.

* AEM Java 로그:`error.log`
* AEM HTTP 요청 로그:`request.log`
* AEM HTTP 액세스 로그:`access.log`

디스패처를 포함한 Apache 레이어 로그는 디스패처를 포함하는 Docker 컨테이너에 있습니다. Dispatcher 시작 방법에 대한 자세한 내용은 [Dispatcher 설명서](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/implementing/content-delivery/disp-overview.html)를 참조하십시오.

로그를 검색하려면 다음을 수행하십시오.

1. 명령줄에 `docker ps`을 입력하여 컨테이너를 나열합니다.
1. 컨테이너에 로그인하려면 &quot;`docker exec -it <container> /bin/sh`&quot;을 입력합니다. 여기서 `<container>`은 이전 단계의 디스패처 컨테이너 ID입니다.
1. `/mnt/var/www/html` 아래의 캐시 루트로 이동합니다.
1. 로그가 `/etc/httpd/logs` 아래에 있습니다.
1. Inspect 로그:XYZ 폴더 아래에서 액세스할 수 있습니다. 여기서 다음 로그를 볼 수 있습니다.
   * Apache HTTPD 웹 서버 액세스 로그 - `httpd_access.log`
   * Apache HTTPD 웹 서버 오류 로그 - `httpd_error.log`
   * 디스패처 로그 - `dispatcher.log`

로그가 터미널 출력에 직접 인쇄됩니다. 대부분의 경우 이러한 로그는 DEBUG여야 하며 Docker를 실행할 때 디버그 수준을 매개 변수로 전달하여 수행할 수 있습니다. 예:

`DISP_LOG_LEVEL=Debug ./bin/docker_run.sh out docker.for.mac.localhost:4503 8080`

## 프로덕션 및 스테이지 디버깅 {#debugging-production-and-stage}

예외적인 상황에서는 스테이지 또는 프로덕션 환경에서 보다 세밀하게 기록하도록 로그 수준을 변경해야 합니다.

가능한 한 Git의 구성 파일에 있는 로그 수준을 Warn 및 Error에서 Debug로 변경하고 이러한 구성 변경 사항을 환경에 등록하기 위해 Cloud Service으로 AEM에 배포해야 합니다.

Debug로 작성된 트래픽 및 로그 문의 양에 따라 환경에 부정적인 성능이 발생할 수 있으므로 단계 및 프로덕션 디버그 수준의 변경 사항은 다음과 같습니다.

* 주의적으로 그리고 꼭 필요한 경우에만
* 적절한 수준으로 복귀하여 가능한 한 빨리 다시 배포

## Splunk 로그 {#splunk-logs}

Splunk 계정을 보유한 고객은 고객 지원 티켓을 통해 AEM Cloud Service 로그가 적절한 지표에 전달되도록 요청할 수 있습니다. 로깅 데이터는 Cloud Manager 로그 다운로드를 통해 사용할 수 있는 것과 동일하지만 고객은 Splunk 제품에서 사용할 수 있는 쿼리 기능을 활용할 수 있습니다.

Splunk로 전송된 로그와 연결된 네트워크 대역폭은 고객의 네트워크 I/O 사용량의 일부로 간주됩니다.

### 분할된 전달 활성화 {#enabling-splunk-forwarding}

지원 요청에서 고객은 다음을 나타내야 합니다.

* Splunk HEC 끝점 주소
* Splunk 지수
* 스플덩크 포트
* Splunk HEC 토큰. 자세한 내용은 [이 페이지](https://docs.splunk.com/Documentation/Splunk/8.0.4/Data/HECExamples)를 참조하십시오.

위의 속성은 각 관련 프로그램/환경 유형 조합에 대해 지정해야 합니다.  예를 들어 고객이 개발, 스테이징 및 프로덕션 환경을 원하는 경우 아래 설명된 대로 3개의 정보 세트를 제공해야 합니다.

>[!NOTE]
>
>샌드박스 프로그램 환경에 대한 스플렁크 포워딩은 지원되지 않습니다.

초기 요청에는 단계/prod 환경 외에 활성화해야 하는 모든 개발 환경이 포함되어야 합니다.

초기 요청 후에 생성된 새 개발 환경에서 Splunk 전달을 수행하려고 했으나 이를 활성화하지 않은 경우 추가 요청을 해야 합니다.

개발 환경이 요청되면 요청에 없는 다른 개발 환경이나 샌드박스 환경에서도 Splunk 포워딩을 사용하도록 설정하고 Splunk 인덱스를 공유할 수 있습니다. 고객은 `aem_env_id` 필드를 사용하여 이러한 환경을 구분할 수 있습니다.

아래에서 샘플 고객 지원 요청을 확인할 수 있습니다.

프로그램 123, Production Env

* Splunk HEC 끝점 주소:`splunk-hec-ext.acme.com`
* 스플렁크 색인:acme_123prod(고객은 원하는 이름 지정 규칙을 선택할 수 있음)
* Splunk 포트:443년
* HEC 토큰 분리:ABC123

프로그램 123, 스테이지 환경

* Splunk HEC 끝점 주소:`splunk-hec-ext.acme.com`
* 스플렁크 색인:acme_123stage
* Splunk 포트:443년
* HEC 토큰 분리:ABC123

프로그램 123, Dev Envs

* Splunk HEC 끝점 주소:`splunk-hec-ext.acme.com`
* 스플렁크 색인:acme_123dev
* Splunk 포트:443년
* HEC 토큰 분리:ABC123

각 환경에 대해 동일한 Splunk 인덱스를 사용하기에 충분할 수 있습니다. 이 경우 `aem_env_type` 필드를 사용하여 dev, stage 및 prod 값을 기준으로 구분할 수 있습니다. 개발 환경이 여러 개인 경우 `aem_env_id` 필드도 사용할 수 있습니다. 관련 색인이 축소된 Splunk 사용자 집합에 대한 액세스를 제한하는 경우 일부 조직은 프로덕션 환경 로그에 대해 별도의 인덱스를 선택할 수 있습니다.

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
