---
title: 신유교 원
description: AEM as a Cloud Service에 대한 APM(New Relic One Application Performance Monitoring) 서비스와 이 서비스에 액세스하는 방법에 대해 알아봅니다.
exl-id: 9fa0c5eb-415d-4e56-8136-203d59be927e
source-git-commit: 6cf164093cc543fe4847859b248e70efd86efbb1
workflow-type: tm+mt
source-wordcount: '1038'
ht-degree: 2%

---


# 신유교 원 {#user-access}

AEM as a Cloud Service에 대한 APM(New Relic One Application Performance Monitoring) 서비스와 이 서비스에 액세스하는 방법에 대해 알아봅니다.

## 소개 {#introduction}

Adobe은 애플리케이션의 모니터링, 가용성 및 성능에 크게 중점을 둡니다. 이 목표를 달성하기 위해 AEM as a Cloud Service은 표준 제품 서비스의 일부로서 사용자 정의 New Relic One 모니터링 세트에 대한 액세스를 제공하여 팀이 AEM as a Cloud Service 시스템 및 환경 성능 지표를 최대한 파악할 수 있도록 합니다.

이 문서에서는 AEM as a Cloud Service 환경에서 사용할 수 있는 APM(New Relic One Application Performance Monitoring) 기능에 대해 설명하며, 성능을 지원하고 AEM as a Cloud Service을 최대한 활용할 수 있습니다.

## 기능 {#transaction-monitoring}

AEM as a Cloud Service용 New Relic One APM에는 많은 기능이 있습니다.

* 전용 New Relic One 계정에 직접 액세스(Adobe 지원으로 관리)

* 외부 종속성 및 데이터베이스를 포함하여 줄 번호를 사용하여 정확한 메서드 호출을 표시하는 New Relic One APM 에이전트를 구현했습니다.

* 인프라 수준 모니터링과 애플리케이션(Adobe Experience Manager) 모니터링의 주요 지표를 결합하여 전체적인 성능 최적화

* AEM as a Cloud Service JMX Mbean 및 상태 검사를 New Relic Insights 지표 내에서 직접 노출하여 애플리케이션 스택 성능 및 상태 지표를 심층적으로 검사할 수 있습니다.

## New Relic One 액세스 {#accessing-new-relic}

다음 단계에 따라 AEM as a Cloud Service 프로그램과 연결된 New Relic One 하위 계정에 액세스할 수 있습니다.

1. Admin Console에서 지원 탭에 액세스하여 요청을 여십시오.
1. 요청에는 프로그램 ID의 세부 사항과 New Relic에 액세스해야 하는 사용자 목록을 포함합니다.
   * 모든 사용자의 전체 이름과 유효한 이메일 주소를 제공해야 합니다.

문서를 참조하십시오 [Experience Cloud을 위한 AEM 지원 포털](https://helpx.adobe.com/kr/enterprise/using/support-for-experience-cloud.html) 를 참조하십시오.

액세스 권한이 제공되면 New Relic에서 각 사용자에게 확인 이메일을 보내어 사용자가 설정 프로세스를 완료하고 로그인할 수 있습니다.

사용자가 원래 계정 확인 이메일을 찾을 수 없는 경우 다음 단계를 따르십시오.

1. New Relic의 로그인 페이지 위치 [`login.newrelic.com/login`](https://login.newrelic.com/login).

1. 선택 **암호를 잊으셨습니까?**.

   ![새 Relic 로그인](/help/implementing/cloud-manager/assets/new-relic/newrelic-1.png)

1. 계정 이메일 주소를 입력하고 을(를) 선택합니다 **내 재설정 링크 보내기**.

   ![전자 메일 주소 입력](/help/implementing/cloud-manager/assets/new-relic/newrelic-2.png)

1. New Relic는 계정을 확인하는 링크가 포함된 이메일을 사용자에게 보냅니다.

등록 프로세스를 완료하고 전자 메일 또는 암호 오류 메시지로 인해 계정에 로그인할 수 없는 경우 [Admin Console](https://adminconsole.adobe.com/).

>[!TIP]
>
>New Relic에서 전자 메일을 받지 않는 경우:
>
>* 다음 문서를 확인하십시오. [스팸 필터](https://docs.newrelic.com/docs/accounts/accounts-billing/account-setup/create-your-new-relic-account/).
>* 해당되는 경우 [이메일 허용 목록에 New Relic 추가](https://docs.newrelic.com/docs/accounts/accounts/account-maintenance/account-email-settings/#email-whitelist).
>* 어느 제안도 도움이 되지 않는 경우 지원 티켓에 대한 피드백을 제공하고 Adobe 지원 팀이 추가 지원을 제공합니다.


### 이메일 확인 {#verify-email}

로그인 중에 전자 메일을 확인하라는 메시지가 표시되면 전자 메일이 여러 계정과 연결되어 있는 것입니다. 이를 통해 액세스할 계정을 선택할 수 있습니다.

이메일 주소를 확인하지 않는 경우 New Relic에서 이메일 주소와 연결된 가장 최근에 만든 사용자 레코드로 로그인하려고 합니다. 각 로그인 동안 이메일을 확인하지 않으려면 **내 정보 저장** 로그인 화면의 확인란.

자세한 내용은 [AEM 지원 포털](https://helpx.adobe.com/enterprise/using/support-for-experience-cloud.html).

## 예외 {#exceptions}

AEM as a Cloud Service은 New Relic One APM 솔루션만 제공하며 경고, 로깅 또는 API 통합을 지원하지 않습니다.

AEM as a Cloud Service 프로그램을 위한 New Relic One 오퍼링에 대한 자세한 도움이나 추가 지침은 [AEM 지원 포털](https://helpx.adobe.com/enterprise/using/support-for-experience-cloud.html).

## 신규 기존 고객을 위한 FAQ {#faqs}

### New Relic One을 사용한 Adobe 모니터는 무엇입니까? {#adobe-monitor}

Adobe은 New Relic One의 Java 플러그인을 통해 AEM as a Cloud Service 작성자, 게시 및 미리 보기(사용 가능한 경우) 서비스를 모니터링합니다. Adobe을 사용하면 비프로덕션 및 프로덕션 AEM as a Cloud Service 환경에서 사용자 정의 New Relic One APM 원격 분석과 모니터링을 수행할 수 있습니다.

New Relic One 계정은 기본 Adobe 유지 관리 계정에 연결되며 다음과 같은 여러 애플리케이션을 보고합니다. AEM as a Cloud Service 환경당 3개.

* 환경당 작성자 서비스를 위한 하나의 애플리케이션
* 환경당 게시 서비스를 위한 하나의 애플리케이션(골든 게시 포함)
* 환경당 미리 보기 서비스를 위한 하나의 애플리케이션

참고 사항:

* 각 애플리케이션은 하나의 라이센스 키를 사용합니다.
* AEM as a Cloud Service 환경은 하나의 New Relic One 계정에만 보고합니다.
* New Relic One에 대한 전체 모니터링 지표와 이벤트는 7일 동안 유지됩니다.

### 누가 New Relic One 클라우드 서비스 데이터에 액세스할 수 있습니까? {#access-new-relic-cloud}

최대 10명의 팀원에 대해 전체 읽기 액세스 권한이 부여됩니다. 읽기 액세스 권한에는 New Relic One 에이전트가 수집한 모든 APM 지표가 포함됩니다.

### 사용자 지정 SSO 구성이 지원됩니까? {#custom-sso}

Adobe이 제공한 New Relic One 계정에 대해 사용자 지정 SSO 구성이 지원되지 않습니다.

### 이미 온-프레미스 New Relic 구독이 있다면 어떻게 합니까? {#new-relic-subscription}

New Relic One은 New Relic에서 제공하는 새로운 가시성 플랫폼으로, Adobe 지원 및 팀이 지표와 이벤트를 한 곳에서 관찰, 모니터링 및 볼 수 있습니다.

New Relic One은 사용자가 모든 서비스 및 호스트의 데이터를 한 보기에서 액세스하고 시각화할 수 있는 모든 계정을 검색할 수 있는 기능을 제공합니다.

Adobe 지원은 New Relic One 및 기타 사내 도구를 사용하여 AEM as a Cloud Service 애플리케이션을 모니터링하지만, New Relic for on-predictive 호스팅 서비스 및 인프라를 계속 활용할 수 있습니다. New Relic One 계정과 고객 관리 New Relic 계정 모두에서 데이터를 시각화할 수 있습니다.

>[!NOTE]
>
>New Relic One 내에서 두 데이터 세트를 모두 보려면 사용자에게 올바른 권한이 있어야 하며 두 계정(Adobe New Relic One 및 고객 관리 New Relic 계정)에 대해 동일한 로그인 방법을 사용해야 합니다.
