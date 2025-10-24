---
title: Admin Console에 액세스
description: 온보딩에 필요한 준비와 AEM as a Cloud Service 구조의 기본 사항을 이해하면 Admin Console에 처음 로그인할 수 있습니다.
exl-id: 0ccce328-a356-4ba9-b7fe-f67abc25b924
feature: Onboarding
role: Admin, User, Developer
source-git-commit: 8ed13eb6f476bab07da07549a83ab9ac16bdea72
workflow-type: tm+mt
source-wordcount: '1147'
ht-degree: 55%

---

# Admin Console에 액세스 {#accessing-admin-console}

이 [온보딩 여정](overview.md) 부분에서는 시스템에 처음 로그인하기 전에 필요한 준비에 대해 배웁니다.

## 목표 {#objective}

[AEM as a Cloud Service 용어](terminology.md) 문서를 읽고 AEMaaCS 구조의 기본 사항을 이해했으므로 이제 Admin Console에 처음으로 로그인할 준비가 된 것입니다!

시스템 관리자는 Admin Console을 사용하여 조직 내에서 사용자를 관리할 책임이 있습니다. 이 섹션을 읽고 나면 다음 작업을 수행할 수 있습니다.

* Adobe ID가 무엇인지 이해합니다.
* Admin Console에 로그인할 수 있습니다.
* Admin Console을 통해 시스템 관리자로서의 권한을 검토하는 방법을 이해합니다.
* 도움이 필요한 경우 Adobe 지원 센터에 문의하는 방법을 이해합니다.

## Admin Console 정보 {#admin-console}

Adobe Admin Console은 Adobe 제품 라이선스 및 사용자를 관리하는 중앙 위치입니다. Admin Console을 사용하면 다양한 개별 솔루션이 아닌 단일 위치에서 사용자를 생성하고 관리할 수 있습니다.

### Adobe ID {#adobe-id}

Admin Console에 로그인하려면 Adobe ID가 필요합니다. Adobe ID은 AEM as a Cloud Service 또는 Adobe 솔루션에 로그인하고 액세스하는 데 필요한 특정 이메일 주소에 연결된 계정입니다. Adobe ID을 사용하면 모든 Adobe 계획 및 제품을 단일 계정과 연결된 상태로 유지할 수 있습니다.

시스템 관리자가 Admin Console에서 팀을 설정할 때 Adobe ID로 사용할 이메일 주소를 지정합니다.

Adobe ID에는 세 가지 유형이 있습니다.

* **개인 ID**: adobe.com에 만들어지는 Adobe ID의 기본 형식입니다. Adobe에서 관리하며 누구나 이 유형의 계정을 만들 수 있습니다.

* **Enterprise ID**: 조직은 일반적으로 사용자 계정에 대한 제어를 강화하기를 원합니다. 시스템 관리자만 Enterprise ID를 만들 수 있으며 조직에서 이러한 계정을 소유하고 Adobe는 호스트 역할만 합니다.

* **Federated ID**: federated ID를 사용하면 조직이 계정에 대한 완전한 소유권과 제어 권한을 갖습니다. 조직은 Adobe Experience Cloud을 SAML2 SSO(Single Sign-On) 시스템과 통합해야 합니다. 이렇게 하면 사용자가 Adobe에서 호스팅하는 계정이 아닌 조직의 SSO 시스템에 대해 인증할 수 있습니다.

시스템 관리자는 개인 ID를 사용하여 자신과 팀을 AEM as a Cloud Service에 온보딩할 수 있습니다. Enterprise ID 또는 Federated ID가 설치되기 전에 이 작업을 수행하십시오. Enterprise ID 또는 Federated ID가 설정되면 멤버가 해당 ID를 사용하도록 전환할 수 있습니다.

### Admin Console에 직접 로그인 {#steps-admin-console}

Admin Console을 사용하여 팀 내 사용자를 관리하려면 먼저 자신이 적절하게 액세스할 수 있고 적절한 권한이 있는지 확인해야 합니다.

1. 시스템 관리자는 온보딩 프로세스의 일부로 Adobe에서 여러 개의 이메일을 수신하게 됩니다. 액세스 권한이 부여된 조직 이름에 대한 정보를 제공하는 환영 이메일을 찾습니다.

1. 시작 이메일의 **시작하기** 링크를 클릭하여 Admin Console으로 이동합니다. 이메일을 찾을 수 없는 경우 [`https://adminconsole.adobe.com`](https://adminconsole.adobe.com)에서 Admin Console로 직접 브라우저를 엽니다.

   ![환영 이메일](/help/journey-onboarding/assets/get-started-email.png)

1. Adobe ID를 사용하여 로그인합니다. 로그인에 성공하면 Adobe Admin Console의 **개요** 페이지가 표시됩니다.

   ![Admin Console](/help/journey-onboarding/assets/get-started1.png)

1. 여러 조직에 대한 액세스 권한이 있는 경우 올바른 조직에 로그인했는지 확인하십시오. 조직을 변경하려면 오른쪽 상단에서 조직 이름을 클릭하고 액세스가 필요한 필수 조직을 선택합니다.

   ![조직 변경](/help/journey-onboarding/assets/admin-console-orgswitch.png)

1. 시스템 관리자인지 확인하려면 **사용자** 카드에서 **관리자**&#x200B;를 선택합니다.

   ![관리자 검토](/help/journey-onboarding/assets/get-started2.png)

1. **사용자** 카드에서 **관리자**&#x200B;를 클릭하면 Adobe ID 이메일, 사용자 이름, 이름 또는 성을 입력하여 검색할 수 있습니다.

   ![사용자 검색](/help/journey-onboarding/assets/get-started3.png)

1. 모든 것이 제대로 작동하면 검색에서 레코드를 반환합니다. **관리자 역할** 열의 값에 **시스템**&#x200B;이 표시되면 자신(또는 표시된 사용자)가 시스템 관리자임을 알 수 있습니다.

   ![시스템 상태](/help/journey-onboarding/assets/get-started4.png)

구성, 시스템 관리자!

## Experience Hub을 통해 Admin Console 액세스  {#access-admin-console-via-experience-hub}

[Experience Hub](/help/experience-hub.md)은(는) AEM을 위한 통합되고 개인화된 홈입니다. AEM 도구와 Admin Console을 한 곳에 통합합니다.

![Experience Hub 홈 페이지에 표시되는 Admin Console 옵션](/help/journey-onboarding/assets/experiencehub-adminconsole1.png)

**Experience Hub을 통해 Admin Console에 액세스하려면:**

1. Experience Hub의 홈 페이지를 열려면 [Adobe Experience Cloud](https://experience.adobe.com/#/@foundationinternal/home)을 클릭하세요.

1. **빠른 액세스** 그룹화에서 [**Admin Console**](https://experience.adobe.com)을(를) 클릭합니다.

## Adobe Identity Management 시스템 {#ims}

AEM as a Cloud Service는 인증을 위해 Adobe Identity Management System(IMS라고도 함)과 함께 사전 구성되어 제공됩니다. 이 기능을 활성화하기 위해 시스템 관리자가 수행해야 할 작업은 없습니다.

AEM as a Cloud Service는 IMS를 사용하여 AEM과 나머지 Adobe Experience Cloud 간의 로그인 경험을 통합합니다. Adobe 제품이 많은 조직이 가장 많은 이득을 얻습니다. Admin Console에서 역할 기반 그룹을 만들고 AEM as a Cloud Service과 같은 IMS를 통해 제품 액세스 권한을 부여합니다.

이 온보딩 여정의 다음 부분에서는 제품 프로필 및 사용자 할당에 대해 자세히 알아봅니다.

## Adobe 지원 문의 {#support}

문제가 있는 경우 Admin Console을 통해 Adobe 지원 센터에 액세스할 수 있습니다. **지원** 탭을 사용하여 간단하고 사용하기 쉬운 인터페이스를 통해 다양한 Adobe 지원 기능을 이용할 수 있습니다.

![지원 탭](/help/journey-onboarding/assets/support-menu.png)

이 탭에서 사례를 만들고 관리할 수 있으며 Adobe 고객 지원 센터 담당자와 직접 채팅하고 전문가와의 세션을 예약할 수 있습니다. 시스템 관리자 및 지원 관리자는 지원 사례와 전문가 세션 옵션을 이용하려면 로그인해야 합니다.

## 다음 단계 {#whats-next}

지금까지 이 문서를 통해 다음과 같은 성과를 달성했습니다.

* Adobe ID가 무엇인지 이해합니다.
* Admin Console에 로그인할 수 있습니다.
* Admin Console을 사용하여 시스템 관리자로서의 권한을 검토하는 방법을 이해합니다.
* 도움이 필요한 경우 Adobe 지원 센터에 문의하는 방법을 이해합니다.

동료가 AEMaaCS에 액세스할 수 있도록 [Cloud Manager 제품 프로필에 팀원을 할당](assign-profiles-cloud-manager.md)하는 방법을 배움으로써 온보딩 여정을 계속할 준비가 되었습니다.

## 추가 리소스 {#additional-resources}

온보딩 여정의 콘텐츠를 능가하려는 경우 다음은 추가적인 옵션 리소스입니다.

* [Admin Console 개요](https://helpx.adobe.com/kr/enterprise/using/admin-console.html) - Admin Console에 대한 포괄적인 개요
* [Adobe ID 만들기 또는 업데이트](https://helpx.adobe.com/kr/manage-account/using/create-update-adobe-id.html#HowtocreateorupdateyourAdobeID) - Adobe ID를 만들고, 변경하고, 여러 Adobe ID를 관리하는 방법에 대해 알아봅니다.
* [SAML 2.0 Authentication Handler](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/security/saml-2-0-authenticationhandler#) - AEM은 SAML 인증 핸들러와 함께 제공됩니다. 이 핸들러는 HTTP POST 바인딩을 사용하여 SAML 2.0 인증 요청 프로토콜(Web-SSO 프로필)을 지원합니다.
* [관리 역할](https://helpx.adobe.com/kr/enterprise/using/admin-roles.html) - 조직은 Adobe Admin Console을 사용하여 Adobe 제품 액세스 및 사용을 세분화하고 관리할 수 있는 유연한 관리 계층 구조를 정의할 수 있습니다.
* [지원 및 전문가 세션](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.html) - Admin Console에서 지원 옵션에 액세스하고, 지원 사례를 관리하고, 전문가 세션을 예약하는 방법 등에 대해 알아봅니다.
