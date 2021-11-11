---
title: New Relic에 대한 사용자 액세스
description: New Relic에 대한 사용자 액세스
index: false
hide: true
source-git-commit: 22dc38ac4aa736ae5c676cfba16e16b0b3e44936
workflow-type: tm+mt
source-wordcount: '998'
ht-degree: 0%

---


# New Relic Application Performance Monitoring for AEM as a Cloud Service {#new-relic}

## 소개 {#introduction}

Adobe places a high emphasis on the monitoring, availability, and performance of your application. 이 목표를 달성하기 위해 AEM as a Cloud Service은 표준 제품 서비스의 일부로서 사용자 정의 New Relic 모니터링 세트에 대한 액세스를 제공하여 팀이 Adobe Experience Manager Cloud Service 시스템 및 환경 성능 지표를 최대 볼 수 있도록 합니다. 이 섹션에서는 AEM as a Cloud Service 환경에서 성능을 강화하고 AEM as a Cloud Service을 최대한 활용할 수 있도록 해주는 새로운 Relic 모니터링 기능에 대해 설명합니다.

## AEM as a Cloud Service Transaction Monitoring via New Relic {#transaction-monitoring}

다음은 AEM as a Cloud Service용 New Relic Application Performance Monitoring의 주요 기능입니다.

* 전용 New Relic One 계정에 직접 액세스(Adobe 지원에서 액세스 관리)

* 외부 종속성 및 데이터베이스를 포함하여 줄 번호를 사용하여 정확한 메서드 호출을 표시하는 New Relic APM 에이전트를 구현했습니다.

* Holistic performance optimization by combining key metrics from infrastructure-level monitoring as well as application (Adobe Experience Manager) monitoring.

* AEM as a Cloud Service JMX Mbean 및 상태 검사를 새로운 Relic Insights 지표에 직접 노출하여 애플리케이션 스택 성능 및 상태 지표를 심층적으로 검사할 수 있습니다.

## AEM as a Cloud Service New Relic 계정 액세스 {#accessing-new-relic}

전용 New Relic 계정은 고객 지원 서비스를 통해 Adobe에서 프로비저닝되고 관리됩니다. Adobe은 소유자 및 관리자로 남으며 전용 하위 계정에 액세스할 수 있도록 사용자를 대신하여 계정을 프로비저닝합니다.

AEM as a Cloud Service 프로그램과 연결된 New Relic 하위 계정에 액세스하려면 다음을 수행하십시오.

* Please open a request by accessing the Support tab in the Admin Console.
* 티켓에 프로그램 ID의 세부 사항과 새 Relic 액세스를 열기 위해 Adobe 팀에 요청한 사용자 목록이 포함되어 있는지 확인합니다.
* 모든 사용자에게 전체 이름과 유효한 이메일 주소를 제공해야 합니다.

   >[!NOTE]
   >AEM 지원 포털에 대한 자세한 내용은 Experience Cloud 지원 을 참조하십시오.

액세스 권한이 제공되면 New Relic는 각 사용자에게 확인 이메일을 보내어 설정 프로세스를 완료하고 로그인할 수 있습니다. 원래 계정 확인 이메일을 찾을 수 없는 경우:

1. login.newrelic.com/login에서 New Relic의 로그인 페이지로 이동합니다.

1. Select Forgot your password.

1. Type the account email address, and select Send my password.

1. When New Relic&#39;s system returns an email message, select the link in it to confirm your account again.

   >[!NOTE]
   >New Relic에서 전자 메일을 받지 않는 경우:
   >스팸 필터를 확인하십시오. 해당하는 경우 이메일 허용 목록에 New Relic를 추가합니다.
   >지원 티켓에 대한 피드백을 보내주시면 저희 팀이 추가 지원을 해 드리겠습니다

1. If you complete the signup process and are unable to log in to your account due to email or password error messages, please get us a support ticket via Admin Console.

If you are asked to verify your email during login, it means your email is associated with multiple accounts and will be given the option to verify your email during login. 이를 통해 액세스할 계정을 선택할 수 있습니다. If you do not verify your email address, New Relic will attempt to log you in with the most recently created user record associated with your email address. 각 로그인 동안 이메일을 확인하지 않으려면 로그인 화면에서 내 정보 저장 확인란을 클릭합니다.

자세한 내용은 AEM 지원 포털을 통해 지원 티켓을 여십시오.

## 예외 {#exceptions}

AEM as a Cloud Service은 New Relic APM 솔루션에 대해서만 서비스를 제공하며 경고, 로깅 또는 API 통합 기능을 지원하지 않습니다.

AEM as a Cloud Service 프로그램을 위한 New Relic 오퍼링에 대한 자세한 도움말 또는 추가 지침은 AEM Support Portal을 통해 지원 티켓을 여십시오.

## 신규 기존 고객을 위한 FAQ {#faqs}

### New Relic를 사용한 Adobe 모니터는 무엇입니까? {#adobe-monitor}

Adobe은 New Relic APM Java 플러그인을 통해 AEM as a Cloud Service 작성자, 게시 및 미리 보기(사용 가능한 경우) 서비스를 모니터링합니다. Adobe enables custom New Relic APM Telemetry and monitoring across non-production and production AEM as a Cloud Service environments. New Relic 계정은 기본 Adobe 유지 관리 계정에 연결되며 여러 애플리케이션을 보고 있습니다.

Three each per AEM as a Cloud Service environment:

* One application for the Author service per environment
* 환경당 게시 서비스를 위한 하나의 애플리케이션(골든 게시 포함)
* One application for the Preview service per environment
Each application uses one license key, AEM as a Cloud Service environments will report to only one New Relic account. New Relic APM 및 Infrastructure에 대한 전체 모니터링 지표와 이벤트는 7일 동안 유지됩니다.

### Who can access the New Relic Cloud Service data? {#access-new-relic-cloud}

최대 10명의 팀원에 대해 전체 읽기 액세스 권한이 부여됩니다. Read access will include all APM metrics collected by the New Relic agent.

### Is Custom SSO Configuration Supported? {#custom-sso}

Adobe이 제공한 New Relic 계정에 대해 현재 사용자 지정 SSO 구성이 지원되지 않습니다.

### 이미 온-프레미스 New Relic Subscription이 있다면 어떻게 합니까? {#new-relic-subscription}

The new observability platform from New Relic called New Relic One enables Adobe Support Groups and your teams to observe, monitor, and view metrics and events, all in one place. New Relic One은 사용자가 모든 서비스 및 호스트의 데이터를 한 보기에서 액세스하고 시각화할 수 있는 모든 계정을 검색할 수 있는 기능을 제공합니다. Adobe 지원 팀은 New Relic 및 기타 사내 도구를 사용하여 AEM as a Cloud Service 애플리케이션을 모니터링하지만 New Relic for on-predictive 호스팅 서비스 및 인프라를 계속 활용할 수 있습니다. Adobe 및 고객 관리 New Relic 계정 모두에서 데이터를 시각화할 수 있습니다.

>[!NOTE]
>사용자에게 올바른 권한이 있어야 하며 두 계정(Adobe 및 고객 관리 New Relic 계정)에 대해 동일한 로그인 방법을 사용해야 합니다.


