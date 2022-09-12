---
title: 새 Relic One
description: AEM as a Cloud Service에 대한 APM(New Relic One Application Performance Monitoring) 서비스와 이 서비스에 액세스하는 방법에 대해 알아봅니다.
exl-id: 9fa0c5eb-415d-4e56-8136-203d59be927e
source-git-commit: 8ae52afc366c6607cfc806f68bec2069a2e93f94
workflow-type: tm+mt
source-wordcount: '1612'
ht-degree: 3%

---


# 새 Relic One {#user-access}

AEM as a Cloud Service에 대한 APM(New Relic One Application Performance Monitoring) 서비스와 이 서비스에 액세스하는 방법에 대해 알아봅니다.

## 소개 {#introduction}

Adobe은 애플리케이션의 모니터링, 가용성 및 성능에 크게 중점을 둡니다. AEM as a Cloud Service은 표준 제품 서비스의 일부로서 사용자 정의 New Relic One 모니터링 세트에 대한 액세스를 제공하여 팀이 AEM as a Cloud Service 시스템 및 환경 성능 지표를 최대한 파악할 수 있도록 합니다.

이 문서에서는 AEM as a Cloud Service 환경에서 APM(New Relic One Application Performance Monitoring) 기능에 대한 액세스를 관리하여 성능을 지원하고 AEM을 최대한 활용할 수 있는 방법에 대해 설명합니다.

새 프로덕션 프로그램이 만들어지면 AEM as a Cloud Service 프로그램과 연관된 New Relic One 하위 계정이 자동으로 생성됩니다.

## 기능 {#transaction-monitoring}

AEM as a Cloud Service용 New Relic One APM에는 많은 기능이 있습니다.

* 전용 New Relic One 계정에 직접 액세스(Adobe 지원으로 관리)

* 외부 종속성 및 데이터베이스를 포함하여 줄 번호를 사용하여 정확한 메서드 호출을 표시하는 New Relic One APM 에이전트를 구현했습니다.

* 인프라 수준 모니터링과 애플리케이션(Adobe Experience Manager) 모니터링의 주요 지표를 결합하여 전체적인 성능 최적화

* AEM as a Cloud Service JMX Mbean 및 상태 검사를 New Relic Insights 지표 내에서 직접 노출하여 애플리케이션 스택 성능 및 상태 지표를 심층적으로 검사할 수 있습니다.

## 새 Relic One 사용자 관리 {#manage-users}

다음 단계에 따라 AEM as a Cloud Service 프로그램과 연결된 New Relic One 하위 계정의 사용자를 정의합니다.

>[!NOTE]
>
>의 사용자 **비즈니스 소유자** 또는 **배포 관리자** New Relic One 사용자를 관리하려면 역할에 로그인해야 합니다.

1. [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/)에서 Cloud Manager에 로그인한 다음 적절한 조직을 선택합니다.

1. New Relic One 사용자를 관리할 프로그램을 클릭합니다.

1. 아래쪽에서 **환경** 프로그램 개요 페이지에서 카드를 클릭하고 줄임표 단추를 클릭한 다음 **사용자 관리**.

   ![사용자 관리](assets/newrelic-manage-users.png)

   * 또한 **사용자 관리** 맨 위에 있는 줄임표 단추를 통한 옵션 **환경** 프로그램 화면

1. 에서 **새 Relic 사용자 관리** 대화 상자에서 추가할 사용자의 이름과 성을 입력하고 **추가** 버튼을 클릭합니다. 추가할 모든 사용자에 대해 이 단계를 반복합니다.

   ![사용자 추가](assets/newrelic-add-users.png)

1. New Relic One 사용자를 제거하려면 사용자를 나타내는 행 오른쪽 끝에 있는 삭제 단추를 클릭합니다.

1. 클릭 **저장** 사용자를 생성합니다.

사용자가 정의되면, New Relic은 사용자가 액세스 권한을 부여받은 각 사용자에게 확인 이메일을 보내어 사용자가 설정 프로세스를 완료하고 로그인할 수 있도록 합니다.

>[!NOTE]
>
>New Relic One 사용자를 관리하고 있는 경우 사용자로도 액세스할 수 있어야 합니다. 사용 **비즈니스 소유자** 또는 **배포 관리자** New Relic One에 접근하는 것은 충분하지 않습니다. 사용자로도 자신을 만들어야 합니다.

## 새 Relic One 사용자 계정 활성화 {#activate-account}

미리 보기 섹션에 설명된 대로 New Relic One 사용자 계정이 생성되면 [새 Relic One 사용자 관리](#manage-users)기존 전자 메일 주소를 기존 주소로 전송한 경우 이러한 계정을 사용하려면 먼저 암호를 재설정하여 New Relic로 계정을 활성화해야 합니다.

다음 단계에 따라 계정을 New Relic 사용자로 활성화합니다.

1. New Relic에서 이메일에 제공된 링크를 클릭합니다. 브라우저를 New Relic 로그인 페이지로 엽니다.

1. New Relic 로그인 페이지에서 **암호를 잊으셨습니까?**.

   ![새 Relic 로그인](/help/implementing/cloud-manager/assets/new-relic/newrelic-1.png)

1. 확인 이메일을 받은 이메일 주소를 입력하고 을(를) 선택합니다 **내 재설정 링크 보내기**.

   ![전자 메일 주소 입력](/help/implementing/cloud-manager/assets/new-relic/newrelic-2.png)

1. New Relic에서 계정을 확인하는 링크가 포함된 이메일을 보냅니다.

New Relic에서 확인 이메일을 받지 못한 경우 다음을 참조하십시오. [문제 해결 섹션 을 참조하십시오.](#troubshooting)

## New Relic One 액세스 {#accessing-new-relic}

한번 드시면 [New Relic 계정을 활성화했습니다.](#activate-account) Cloud Manager를 통해 또는 직접 New Relic One에 액세스할 수 있습니다.

Cloud Manager를 통해 New Relic One에 액세스하려면 다음을 수행하십시오.

1. [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/)에서 Cloud Manager에 로그인한 다음 적절한 조직을 선택합니다.

1. New Relic One에 액세스할 프로그램을 클릭합니다.

1. 아래쪽에서 **환경** 프로그램 개요 페이지에서 카드를 클릭하고 줄임표 단추를 클릭한 다음 **Open New Relic**.

   ![사용자 관리](assets/newrelic-access.png)

   * 또한 상단의 줄임표 단추를 통해 New Relic에 액세스할 수도 있습니다 **환경** 프로그램 화면

1. 열리는 새 브라우저 탭에서 New Relic One에 로그인합니다.

New Relic One에 직접 액세스하려면

1. New Relic의 로그인 페이지 위치 [`https://login.newrelic.com/login`](https://login.newrelic.com/login)

1. New Relic One에 로그인합니다.

### 이메일 확인 {#verify-email}

New Relic One에 로그인하는 동안 이메일을 확인하라는 메시지가 표시되면 이메일이 여러 계정과 연결된 것입니다. 이를 통해 액세스할 계정을 선택할 수 있습니다.

이메일 주소를 확인하지 않는 경우 New Relic에서 이메일 주소와 연결된 가장 최근에 만든 사용자 레코드로 로그인하려고 합니다. 각 로그인 동안 이메일을 확인하지 않으려면 **내 정보 저장** 로그인 화면의 확인란.

자세한 내용은 [AEM 지원 포털](https://helpx.adobe.com/kr/enterprise/using/support-for-experience-cloud.html).

## New Relic One Access 문제 해결 {#troubleshooting}

섹션에 설명된 대로 New Relic One 사용자로 추가된 경우 [새 Relic One 사용자 관리](#manage-users) 및 은(는) 다음의 원래 계정 확인 이메일을 찾을 수 없습니다.

1. New Relic의 로그인 페이지 위치 [`login.newrelic.com/login`](https://login.newrelic.com/login).

1. 선택 **암호를 잊으셨습니까?**.

   ![새 Relic 로그인](/help/implementing/cloud-manager/assets/new-relic/newrelic-1.png)

1. 계정을 만드는 데 사용한 이메일 주소를 입력하고 을(를) 선택합니다 **내 재설정 링크 보내기**.

   ![전자 메일 주소 입력](/help/implementing/cloud-manager/assets/new-relic/newrelic-2.png)

1. New Relic에서 계정을 확인하는 링크가 포함된 이메일을 보냅니다.

등록 프로세스를 완료하고 전자 메일 또는 암호 오류 메시지로 인해 계정에 로그인할 수 없는 경우 [Admin Console.](https://adminconsole.adobe.com/)

New Relic에서 전자 메일을 받지 않는 경우:

* 다음 문서를 확인하십시오. [스팸 필터](https://docs.newrelic.com/docs/accounts/accounts-billing/account-setup/create-your-new-relic-account/).
* 해당되는 경우 [이메일 허용 목록에 New Relic 추가](https://docs.newrelic.com/docs/accounts/accounts/account-maintenance/account-email-settings/#email-whitelist).
* 어느 제안도 도움이 되지 않는 경우 지원 티켓에 대한 피드백을 제공하고 Adobe 지원 팀이 추가 지원을 제공합니다.

## 제한 사항 {#limitations}

다음 제한 사항은 New Relic One에 사용자를 추가하는 데 적용됩니다.

* 최대 25명의 사용자를 추가할 수 있습니다. 최대 사용자 수에 도달한 경우 새 사용자를 추가할 수 있도록 사용자를 제거합니다.
* 신유물에 추가된 사용자가 그 종류를 지정할 것이다 **제한됨** 참조 [자세한 내용은 New Relic 문서 를 참조하십시오.](https://docs.newrelic.com/docs/accounts/original-accounts-billing/original-users-roles/users-roles-original-user-model/#:~:text=In%20general%2C%20Admins%20take%20responsibility,Restricted%20Users%20can%20use%20them.&amp;text=One%20or%20more%20indicators%20who,change)%20any%20New%20Relic%20기능)
* AEM as a Cloud Service은 New Relic One APM 솔루션만 제공하며 경고, 로깅 또는 API 통합을 지원하지 않습니다.

AEM as a Cloud Service 프로그램을 위한 New Relic One 오퍼링에 대한 자세한 도움이나 추가 지침은 [AEM 지원 포털](https://helpx.adobe.com/enterprise/using/support-for-experience-cloud.html).

## New Relic One에 관한 자주 묻는 질문 {#faqs}

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
