---
title: New Relic에 대한 사용자 액세스
description: AEM as a Cloud Service용 New Relic Application Performance Monitoring에 대해 알려면 이 페이지를 따르십시오
source-git-commit: 696b86e9e88ca1fd7c0a5b688fa78f46227df3a4
workflow-type: tm+mt
source-wordcount: '1049'
ht-degree: 0%

---


# New Relic에 대한 사용자 액세스 {#user-access}

## 소개 {#introduction}

Adobe은 애플리케이션의 모니터링, 가용성 및 성능을 크게 강조합니다. 이 목표를 달성하기 위해 AEM as a Cloud Service은 표준 제품 서비스의 일부로서 사용자 정의 New Relic 모니터링 세트에 대한 액세스를 제공하여 팀이 Adobe Experience Manager Cloud Service 시스템 및 환경 성능 지표를 최대 볼 수 있도록 합니다. 이 섹션에서는 AEM as a Cloud Service 환경에서 성능을 강화하고 AEM as a Cloud Service을 최대한 활용할 수 있도록 해주는 새로운 Relic 모니터링 기능에 대해 설명합니다.

## New Relic를 통한 AEM as a Cloud Service 거래 모니터링 - 가치 제안 {#transaction-monitoring}

다음은 AEM as a Cloud Service을 위한 New Relic Application Performance Monitoring의 가치 제안 요약입니다.

* 전용 New Relic One 계정에 직접 액세스(Adobe 지원에서 액세스 관리)

* 외부 종속성 및 데이터베이스를 포함하여 줄 번호를 사용하여 정확한 메서드 호출을 표시하는 New Relic APM 에이전트를 구현했습니다.

* 인프라 수준 모니터링과 애플리케이션(Adobe Experience Manager) 모니터링의 주요 지표를 결합하여 전체적인 성능 최적화

* AEM as a Cloud Service JMX Mbean 및 상태 검사를 새로운 Relic Insights 지표에 직접 노출하여 애플리케이션 스택 성능 및 상태 지표를 심층적으로 검사할 수 있습니다.

## AEM as a Cloud Service New Relic 계정 액세스 {#accessing-new-relic}

전용 New Relic 계정은 고객 지원 서비스를 통해 Adobe에서 프로비저닝되고 관리됩니다. Adobe은 소유자 및 관리자로 남으며 전용 하위 계정에 액세스할 수 있도록 사용자를 대신하여 계정을 프로비저닝합니다.

AEM as a Cloud Service 프로그램과 연결된 New Relic 하위 계정에 액세스하려면 다음을 수행하십시오.

* Admin Console에서 지원 탭에 액세스하여 요청을 여십시오.
* 티켓에 프로그램 ID의 세부 사항과 새 Relic 액세스를 열기 위해 Adobe 팀에 요청한 사용자 목록이 포함되어 있는지 확인합니다.
* 모든 사용자에게 전체 이름과 유효한 이메일 주소를 제공해야 합니다.

   >[!NOTE]
   >을(를) 참조하십시오. [Experience Cloud을 위한 AEM 지원 포털](https://helpx.adobe.com/enterprise/using/support-for-experience-cloud.html) 자세한 내용

액세스 권한이 제공되면 New Relic에서 각 사용자에게 확인 이메일을 보내어 사용자가 설정 프로세스를 완료하고 로그인할 수 있습니다.

사용자가 원래 계정 확인 이메일을 찾을 수 없는 경우:

1. New Relic의 로그인 페이지 위치 [login.newrelic.com/login](https://login.newrelic.com/login).

1. 선택 **암호를 잊으셨습니다.**.

   ![](/help/implementing/cloud-manager/assets/new-relic/newrelic-1.png)

1. 계정 이메일 주소를 입력하고 을(를) 선택합니다 **내 재설정 링크 보내기**.

   ![](/help/implementing/cloud-manager/assets/new-relic/newrelic-2.png)

1. New Relic의 시스템에서 이메일 메시지를 반환하면 해당 링크를 선택하여 계정을 다시 확인합니다.

   >[!NOTE]
   >New Relic에서 전자 메일을 받지 않는 경우:
   >다음 문서를 확인하십시오. [스팸 필터](https://docs.newrelic.com/docs/accounts/accounts-billing/account-setup/create-your-new-relic-account/). 해당되는 경우 [이메일 허용 목록에 New Relic 추가](https://docs.newrelic.com/docs/accounts/accounts/account-maintenance/account-email-settings/#email-whitelist).
   >지원 티켓에 대한 피드백을 제공하고 Adobe 지원 팀이 추가 지원을 제공할 것입니다.

1. 등록 프로세스를 완료하고 전자 메일 또는 암호 오류 메시지로 인해 계정에 로그인할 수 없는 경우 [Admin Console](https://adminconsole.adobe.com/).

### 이메일 확인 {#verify-email}

로그인 동안 전자 메일을 확인하라는 메시지가 표시되면 전자 메일이 여러 계정과 연결되어 있고 로그인 중에 전자 메일을 확인하는 옵션이 제공됩니다. 이를 통해 액세스할 계정을 선택할 수 있습니다. 이메일 주소를 확인하지 않는 경우 New Relic에서 이메일 주소와 연결된 가장 최근에 만든 사용자 레코드로 로그인하려고 합니다. 각 로그인 동안 이메일을 확인하지 않으려면 로그인 화면에서 내 정보 저장 확인란을 클릭합니다.

자세한 도움말을 보려면 [AEM 지원 포털](https://helpx.adobe.com/enterprise/using/support-for-experience-cloud.html).

## 예외 {#exceptions}

AEM as a Cloud Service은 New Relic APM 솔루션에 대해서만 서비스를 제공하며 경고, 로깅 또는 API 통합 기능을 지원하지 않습니다.

AEM as a Cloud Service 프로그램을 위한 New Relic 오퍼링에 대한 자세한 도움이나 추가 지침은 [AEM 지원 포털](https://helpx.adobe.com/enterprise/using/support-for-experience-cloud.html) 지원 요청.

## 신규 기존 고객을 위한 FAQ {#faqs}

### New Relic를 사용한 Adobe 모니터는 무엇입니까? {#adobe-monitor}

Adobe은 New Relic APM Java 플러그인을 통해 AEM as a Cloud Service 작성자, 게시 및 미리 보기(사용 가능한 경우) 서비스를 모니터링합니다. Adobe을 사용하면 비프로덕션 및 프로덕션 AEM as a Cloud Service 환경에서 사용자 정의 New Relic APM 원격 분석을 사용하고 모니터링할 수 있습니다. New Relic 계정은 기본 Adobe 유지 관리 계정에 연결되며 여러 애플리케이션을 보고 있습니다.

AEM as a Cloud Service 환경당 3개:

* 환경당 작성자 서비스를 위한 하나의 애플리케이션
* 환경당 게시 서비스를 위한 하나의 애플리케이션(골든 게시 포함)
* 환경당 미리 보기 서비스를 위한 애플리케이션 하나
   >[!IMPORTANT]
   >각 애플리케이션은 하나의 라이센스 키를 사용하며, AEM as a Cloud Service 환경은 하나의 New Relic 계정에만 보고됩니다. New Relic APM 모두에 대한 전체 모니터링 지표와 이벤트는 7일 동안 유지됩니다.

### 누가 New Relic Cloud Service 데이터에 액세스할 수 있습니까? {#access-new-relic-cloud}

최대 10명의 팀원에 대해 전체 읽기 액세스 권한이 부여됩니다. 읽기 액세스 권한에는 New Relic 에이전트가 수집한 모든 APM 지표가 포함됩니다.

### 사용자 지정 SSO 구성이 지원됩니까? {#custom-sso}

Adobe이 제공한 New Relic 계정에 대해 현재 사용자 지정 SSO 구성이 지원되지 않습니다.

### 이미 온-프레미스 New Relic Subscription이 있다면 어떻게 합니까? {#new-relic-subscription}

New Relic One이라는 새로운 가시성 플랫폼을 통해 Adobe 지원 그룹과 팀이 지표와 이벤트를 한 곳에서 관찰, 모니터링 및 볼 수 있습니다. New Relic One은 사용자가 모든 서비스 및 호스트의 데이터를 한 보기에서 액세스하고 시각화할 수 있는 모든 계정을 검색할 수 있는 기능을 제공합니다. Adobe 지원 팀은 New Relic 및 기타 사내 도구를 사용하여 AEM as a Cloud Service 애플리케이션을 모니터링하지만 New Relic for on-predictive 호스팅 서비스 및 인프라를 계속 활용할 수 있습니다. Adobe 및 고객 관리 New Relic 계정 모두에서 데이터를 시각화할 수 있습니다.

>[!NOTE]
>사용자에게 올바른 권한이 있어야 하며 두 계정(Adobe 및 고객 관리 New Relic 계정)에 대해 동일한 로그인 방법을 사용해야 합니다.


