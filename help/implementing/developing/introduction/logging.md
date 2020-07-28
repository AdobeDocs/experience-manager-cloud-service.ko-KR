---
title: 로깅
description: 중앙 로깅 서비스에 대한 전역 매개 변수, 개별 서비스에 대한 특정 설정 또는 데이터 로깅을 요청하는 방법을 알아봅니다.
translation-type: tm+mt
source-git-commit: a7c8e1ab8e0196a3a79d8e0963192775e64a2400
workflow-type: tm+mt
source-wordcount: '386'
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

### AEM Java 로깅 {#aem-java-logging}

AEM은 Cloud Service으로 Java 로그 문에 액세스할 수 있습니다. AEM용 애플리케이션 개발자는 일반적인 Java 로깅 우수 사례를 따라야 하며, 사용자 지정 코드 실행에 대한 관련 문을 다음 로그 수준에서 기록합니다.

<table>
<tbody>
<tr>
<td> <b>AEM 환경</b></td>
<td> <b>로그 수준</b></td>
<td> <b>설명</b></td>
<td> <b>로그 문 가용성</b></td>
</tr>
<tr>
<td> 개발</td>
<td> 디버그</td>
<td> 애플리케이션에서 발생하는 내용을 설명합니다.

DEBUG 로깅이 활성화되면 어떤 활동이 발생하는지 명확하게 파악하고 처리에 영향을 주는 모든 키 매개 변수를 제공하는 문이 기록됩니다.</td>
<td> <ul>
<li> 로컬 개발</li>
<li>개발</li>
</ul></td>
</tr>
<tr>
<td> 단계</td>
<td> 경고</td>
<td> 오류가 될 가능성이 있는 조건에 대해 설명합니다.

WARN 로깅이 활성화되면 하위 최적화에 접근하는 조건을 나타내는 명령문만 기록됩니다.</td>
<td> <ul>
<li> 로컬 개발</li>
<li>개발</li>
<li>단계</li>
</ul></td>
</tr>
<tr>
<td> 프로덕션</td>
<td> 오류</td>
<td> 실패를 나타내며 이를 해결해야 하는 조건을 설명합니다.

ERROR 로깅이 활성화되면 오류를 나타내는 문만 기록됩니다. 오류 로그 문은 가능한 빨리 해결해야 하는 심각한 문제를 나타냅니다.</td>
<td> <ul>
<li> 로컬 개발</li>
<li>개발</li>
<li>단계</li>
<li>프로덕션</li>
</ul></td>
</tr>
</tbody>
</table>