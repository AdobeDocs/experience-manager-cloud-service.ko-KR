---
title: 로깅
description: 중앙 로깅 서비스에 대한 전역 매개 변수, 개별 서비스에 대한 특정 설정 또는 데이터 로깅을 요청하는 방법을 알아봅니다.
translation-type: tm+mt
source-git-commit: 161dc733d335fc62d7c3017647fe27c64a8dd26f
workflow-type: tm+mt
source-wordcount: '1077'
ht-degree: 3%

---


# 로깅 {#logging}

AEM은 고객이 고객층마다 고유한 경험을 만들 수 있는 맞춤형 코드를 포함할 수 있는 플랫폼입니다. 이러한 점을 염두에 두고, 로깅은 로컬 개발 및 클라우드 환경에서 코드 실행을 디버깅하고 이해하기 위한 중요한 기능이며, 특히 AEM은 Cloud Service 개발 환경입니다.

AEM 로깅 및 로그 수준은 Git에서 AEM 프로젝트의 일부로 저장되어 Cloud Manager를 통해 AEM 프로젝트의 일부로 배포되는 구성 파일에서 관리됩니다. AEM에 Cloud Service으로 로그인하면 두 개의 논리 세트로 나눌 수 있습니다.

* AEM 응용 프로그램 수준에서 로깅을 수행하는 AEM 로깅
* Apache HTTPD Web Server/Dispatcher 로깅. 게시 계층에서 웹 서버 및 Dispatcher의 로깅을 수행합니다.

## AEM 로깅 {#aem-loggin}

AEM 응용 프로그램 수준에서 로깅은 세 가지 로그로 처리됩니다.

1. AEM Java 로그. AEM 응용 프로그램에 대한 Java 로깅 문을 렌더링합니다.
1. HTTP 요청 로그 - AEM에서 제공하는 HTTP 요청 및 응답에 대한 정보를 기록합니다.
1. AEM에서 제공하는 요약된 정보와 HTTP 요청을 기록하는 HTTP 액세스 로그

게시 계층의 Dispatcher 캐시 또는 업스트림 CDN에서 제공되는 HTTP 요청은 이러한 로그에 반영되지 않습니다.

## AEM Java 로깅 {#aem-java-logging}

AEM은 Cloud Service으로 Java 로그 문에 액세스할 수 있습니다. AEM용 애플리케이션 개발자는 일반적인 Java 로깅 우수 사례를 따라야 하며, 사용자 지정 코드 실행에 대한 관련 문을 다음 로그 수준에서 기록합니다.

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
애플리케이션에서 발생하는 내용을 설명합니다.<br>
DEBUG 로깅이 활성화되면 어떤 활동이 발생하는지 명확하게 파악하고 처리에 영향을 주는 모든 키 매개 변수를 제공하는 문이 기록됩니다.</td>
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
오류가 될 가능성이 있는 조건에 대해 설명합니다.<br>
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
실패를 나타내며 이를 해결해야 하는 조건을 설명합니다.<br>
ERROR 로깅이 활성화되면 오류를 나타내는 문만 기록됩니다. 오류 로그 문은 가능한 빨리 해결해야 하는 심각한 문제를 나타냅니다.</td>
<td>
<ul>
<li> 로컬 개발</li>
<li>개발</li>
<li>단계</li>
<li>프로덕션</li>
</ul></td>
</tr>
</table>

Java 로깅은 몇 가지 다른 수준의 로깅 세부기간을 지원하는 반면 AEM은 위에 설명된 세 가지 수준을 사용하는 것이 좋습니다.

AEM 로그 레벨은 OSGi 구성을 통해 환경 유형별로 설정되며, 이는 Git에 커밋되고 Cloud Manager를 통해 AEM을 Cloud Service으로 배포합니다. 따라서, 업데이트된 로그 수준 구성을 사용하여 애플리케이션을 재배포하지 않고도 AEM을 통해 사용 가능한 로그가 최적의 로그 수준에서 사용할 수 있도록 하기 위해, Cloud Service을 통해 사용 가능한 로그를 환경 유형에 대해 일관되고 잘 알려진 로그 문을 유지하는 것이 가장 좋습니다.

### 로그 형식 {#log-format}

| 날짜 및 시간 | AEM의 Cloud Service 도드 ID | 로그 수준 | 스레드 | Java 클래스 | 로그 메시지 |
|---|---|---|---|---|---|
| 29.04.2020 21:50:13.398 | `[cm-p1234-e5678-aem-author-59555cb5b8-q7l9s]` | `*DEBUG*` | qtp2130572036-1472 | com.example.approval.workflow.impl.CustomApprovalWorkflow | `No specified approver, defaulting to [ Creative Approvers user group ]` |

**로그 출력 예**

```
22.06.2020 18:33:30.120 [cm-p12345-e6789-aem-author-86657cbb55-xrnzq] *ERROR* [qtp501076283-1809] io.prometheus.client.dropwizard.DropwizardExports Failed to get value from Gauge
22.06.2020 18:33:30.229 [cm-p12345-e6789-aem-author-86657cbb55-xrnzq] *INFO* [qtp501076283-1805] org.apache.sling.auth.core.impl.SlingAuthenticator getAnonymousResolver: Anonymous access not allowed by configuration - requesting credentials
22.06.2020 18:33:30.370 [cm-p12345-e6789-aem-author-86657cbb55-xrnzq] *INFO* [73.91.59.34 [1592850810364] GET /libs/granite/core/content/login.html HTTP/1.1] org.apache.sling.i18n.impl.JcrResourceBundle Finished loading 0 entries for 'en_US' (basename: <none>) in 4ms
22.06.2020 18:33:30.372 [cm-p12345-e6789-aem-author-86657cbb55-xrnzq] *INFO* [FelixLogListener] org.apache.sling.i18n Service [5126, [java.util.ResourceBundle]] ServiceEvent REGISTERED
22.06.2020 18:33:30.372 [cm-p12345-e6789-aem-author-86657cbb55-xrnzq] *WARN* [73.91.59.34 [1592850810364] GET /libs/granite/core/content/login.html HTTP/1.1] libs.granite.core.components.login.login$jsp j_reason param value 'unknown' cannot be mapped to a valid reason message: ignoring
```

### 구성 로거 {#configuration-loggers}

AEM Java 로그는 OSGi 구성으로 정의되므로 실행 모드 폴더를 사용하는 Cloud Service 환경으로 특정 AEM을 타깃팅합니다.

Sling LogManager 팩터리에 대한 OSGi 구성을 통해 사용자 지정 Java 패키지에 대한 Java 로깅을 구성합니다. 지원되는 구성 속성은 다음과 같습니다.

| OSGi 구성 속성 | 설명 |
|---|---|
| org.apache.sling.commons.log.names | 로그 문을 수집할 Java 패키지 |
| org.apache.sling.commons.log.level | org.apache.sling.commons.log.names에 의해 지정된 Java 패키지를 기록할 로그 수준 |

다른 LogManager OSGi 구성 속성을 변경하면 AEM에서 Cloud Service으로 가용성 문제가 발생할 수 있습니다.

다음은 Cloud Service 환경 유형으로 3개의 AEM에 대해 권장되는 로깅 구성(자리 표시자 Java 패키지 사용 `com.example`)의 예입니다.

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

AEM은 Cloud Service의 HTTP 요청 로깅으로 AEM에 대한 HTTP 요청과 해당 HTTP 응답에 대한 통찰력을 시간 순서대로 제공합니다. 이 로그는 AEM에 대한 HTTP 요청 및 처리 및 응답 순서를 이해하는 데 도움이 됩니다.

이 로그를 이해하는 열쇠는 대괄호 안의 숫자 값으로 나타내는 ID로 HTTP 요청 및 응답 쌍을 매핑하는 것입니다. 요청과 해당 응답에 다른 HTTP 요청과 답변이 로그에 들어 있다는 점을 참고하십시오.

### 로그 형식 {#http-request-logging-format}

| 날짜 및 시간 | 요청/응답 쌍 ID |  | HTTP 메서드 | URL | 프로토콜 | AEM을 Cloud Service 노드 ID로 사용 |
|---|---|---|---|---|---|---|
| 2020년 4월 29일:19:14:21 +000 | `[137]` | -> | POST | /conf/global/settings/dam/adminui-extension/metadataprofile/ | HTTP/1.1 | `[cm-p1234-e5678-aem-author-59555cb5b8-q7l9s]` |

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

### 로그 구성 {#configuring-the-log}

AEM HTTP 요청 로그는 AEM에서 Cloud Service으로 구성할 수 없습니다.

## AEM HTTP 액세스 로깅 {#aem-http-access-logging}

AEM의 Cloud Service HTTP 액세스 로깅은 HTTP 요청을 시간 순서대로 표시합니다. 각 로그 항목은 AEM에 액세스하는 HTTP 요청을 나타냅니다.

이 로그는 AEM에 수행되는 HTTP 요청, 함께 제공되는 HTTP 응답 상태 코드 및 HTTP 요청이 완료되는 데 걸린 시간을 빨리 이해하는 데 유용합니다. 이 로그는 사용자별로 로그 항목을 필터링하여 특정 사용자의 활동을 디버깅하는 데 유용할 수도 있습니다.

### 로그 형식 {#access-log-format}

| AEM을 Cloud Service 노드 ID로 사용 | 클라이언트의 IP 주소 | 사용자 |  | 날짜 및 시간 |  | HTTP 메서드 | URL | 프로토콜 |  | HTTP 응답 | HTTP 요청 시간(밀리초) | 레퍼러 | 사용자 에이전트 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| cm-p1235-e2644-aem-author-5955cb5b8-8kgr2 | - | `myuser@adobe.com` | 2020년 4월 30일:17시 37분 14 +000 | &quot; | GET | /libs/granite/ui/references/clientlibs/references.lc-5188e85840c529149e6cd29d94e74ad5-lc.min.css |  | HTTP/1.1 | &quot; | 200 | 1141 | `"https://author-p1234-e4444.adobeaemcloud.com/mnt/overlay/dam/gui/content/assets/metadataeditor.external.html?item=/content/dam/wknd/en/adventures/surf-camp-in-costa-rica/adobestock_266405335.jpeg&_charset_=utf8"` | &quot;Mozilla/5.0(Macintosh; Intel Mac OS X 10_15_4) AppleWebKit/537.36(Gecko와 같은 KHTML) Chrome/81.0.4044.122 Safari/537.36형 |

**예**

```
cm-p1234-e26813-aem-author-59555cb5b8-8kgr2 - example@adobe.com 30/Apr/2020:17:37:14 +0000  "GET /libs/granite/ui/references/clientlibs/references.lc-5188e85840c529149e6cd29d94e74ad5-lc.min.css HTTP/1.1" 200 1141 "https://author-p10711-e26813.adobeaemcloud.com/mnt/overlay/dam/gui/content/assets/metadataeditor.external.html?item=/content/dam/en/images/example.jpeg&_charset_=utf8" "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_4) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/81.0.4044.122 Safari/537.36"
cm-p1234-e26813-aem-author-59555cb5b8-8kgr2 - example@adobe.com 30/Apr/2020:17:37:14 +0000  "GET /libs/dam/gui/coral/components/admin/customthumb/clientlibs.lc-60e4443805c37afa0c74b674b141f1df-lc.min.css HTTP/1.1" 200 809 "https://author-p10711-e26813.adobeaemcloud.com/mnt/overlay/dam/gui/content/assets/metadataeditor.external.html?item=/content/dam/en/images/example.jpeg&_charset_=utf8" "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_4) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/81.0.4044.122 Safari/537.36"
cm-p1234-e26813-aem-author-59555cb5b8-8kgr2 - example@adobe.com 30/Apr/2020:17:37:14 +0000  "GET /libs/dam/gui/coral/components/admin/metadataeditor/clientlibs/metadataeditor.lc-4a2226d8232f8b7ab27d24820b9ddd64-lc.min.js HTTP/1.1" 200 7965 "https://author-p10711-e26813.adobeaemcloud.com/mnt/overlay/dam/gui/content/assets/metadataeditor.external.html?item=/content/dam/en/images/example.jpeg&_charset_=utf8" "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_4) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/81.0.4044.122 Safari/537.36"
```

### HTTP 액세스 로그 구성 {#configuring-the-http-access-log}

AEM에서 Cloud Service으로 HTTP 액세스 로그를 구성할 수 없습니다.

## Apache 웹 서버/Dispatcher 로깅 {#dispatcher-logging}

AEM은 Publish에서 Apache 웹 서버 및 디스패처 레이어에 대해 3개의 로그를 제공합니다.

* Apache HTTPD 웹 서버 액세스 로그
* Apache HTTPD 웹 서버 오류 로그
* Dispatcher 로그

이러한 로그는 게시 계층에만 사용할 수 있습니다.

이 로그 세트는 AEM 애플리케이션에 도달하기 전에 Cloud Service 게시 계층으로 AEM에 대한 HTTP 요청에 대한 통찰력을 제공합니다. 이는 Publish 계층 서버에 대한 대부분의 HTTP 요청은 Apache HTTPD Web Server 및 AEM Dispatcher에서 캐시된 컨텐츠에 의해 제공되며 AEM 애플리케이션 자체에는 도달하지 않으므로 AEM Java, 요청 또는 액세스 로그에 이러한 요청에 대한 로그 명령문이 없음을 이해하는 데 중요합니다.