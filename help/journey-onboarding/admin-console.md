---
title: Admin Console 액세스
description: 온보딩에 필요한 준비와 AEMaaCS 구조의 기본 사항을 이해했으면 처음으로 Admin Console에 로그인할 준비가 된 것입니다.
exl-id: 0ccce328-a356-4ba9-b7fe-f67abc25b924
source-git-commit: 77ae5d79ecb8a11a230cee461f247ffe0e9891a5
workflow-type: tm+mt
source-wordcount: '1111'
ht-degree: 98%

---

# Admin Console 액세스 {#accessing-admin-console}

이 [온보딩 여정](overview.md) 부분에서는 시스템에 처음 로그인하기 전에 필요한 준비에 대해 배웁니다.

## 목표 {#objective}

[AEM as a Cloud Service 용어](terminology.md) 문서를 읽고 AEMaaCS 구조의 기본 사항을 이해했으므로 이제 Admin Console에 처음으로 로그인할 준비가 된 것입니다!

시스템 관리자는 조직 내에서 사용자를 관리할 책임이 있습니다. 이 작업은 Admin Console을 사용하여 수행할 수 있습니다. 이 섹션을 읽고 나면 다음과 같은 작업을 수행할 수 있습니다.

* Adobe ID가 무엇인지 이해합니다.
* Admin Console에 로그인할 수 있습니다.
* Admin Console을 통해 시스템 관리자로서의 권한을 검토하는 방법을 이해합니다.
* 도움이 필요한 경우 Adobe 지원 센터에 문의하는 방법을 이해합니다.

## Admin Console {#admin-console}

Adobe Admin Console은 Adobe 제품 라이선스 및 사용자를 관리하는 중앙 위치입니다. Admin Console을 사용하면 다양한 개별 솔루션이 아닌 단일 위치에서 사용자를 생성하고 관리할 수 있습니다.

## Adobe ID {#adobe-id}

Admin Console에 로그인하려면 Adobe ID가 필요합니다. Adobe ID는 AEM as a Cloud Service 또는 Adobe 솔루션에 로그인하고 액세스하는 데 필요한 특정 이메일 주소에 연결된 계정입니다. Adobe ID를 사용하면 단일 계정과 연결된 모든 Adobe 플랜 및 제품을 유지할 수 있습니다.

시스템 관리자가 Admin Console에서 팀을 설정할 때 Adobe ID로 사용할 이메일 주소를 지정합니다.

Adobe ID에는 세 가지 유형이 있습니다.

* **Personal ID**: Adobe ID의 기본 유형이며 adobe.com에서 생성됩니다. 이 계정은 Adobe에서 관리하며 누구나 이 유형의 계정을 만들 수 있습니다.

* **Enterprise ID**: 조직은 일반적으로 사용자 계정에 대한 제어를 강화하기를 원합니다. 시스템 관리자만 Enterprise ID를 만들 수 있으며 조직에서 이러한 계정을 소유하고 Adobe는 호스트 역할만 합니다.

* **Federated ID**: Federated ID를 사용하면 조직이 계정에 대한 완전한 소유권과 제어 권한을 갖습니다. 이렇게 하려면 조직에서 Adobe Experience Cloud를 SAML2 SSO(Single Sign-On) 시스템과 통합해야 합니다. 이를 통해 사용자는 Adobe에서 호스팅하는 계정이 아닌 조직의 SSO 시스템에 대해 인증할 수 있습니다.

시스템 관리자는 Enterprise ID 또는 Federated ID를 설정하기 전에 Personal ID를 사용하여 자신과 팀을 AEM as a Cloud Service에 온보딩하기로 결정할 수 있습니다. Enterprise ID 또는 Federated ID가 설정되면 멤버가 해당 ID를 사용하도록 전환할 수 있습니다.

## Admin Console 로그인 {#steps-admin-console}

Admin Console을 사용하여 팀 내 사용자를 관리하려면 먼저 자신이 적절하게 액세스할 수 있고 적절한 권한이 있는지 확인해야 합니다.

1. 시스템 관리자는 온보딩 프로세스의 일부로 Adobe로부터 여러 개의 이메일을 받게 됩니다. 액세스 권한이 부여된 조직 이름에 대한 정보를 제공하는 시작 이메일을 찾습니다.

1. 시작 이메일의 **시작하기** 링크를 클릭하여 Admin Console로 이동합니다. 이메일을 찾을 수 없는 경우 [`https://adminconsole.adobe.com`](https://adminconsole.adobe.com)에서 Admin Console로 직접 브라우저를 엽니다.

   ![시작 이메일](/help/journey-onboarding/assets/get-started-email.png)

1. Adobe ID를 사용하여 로그인합니다. 로그인에 성공하면 Adobe Admin Console의 **개요** 페이지가 표시됩니다.

   ![Admin Console](/help/journey-onboarding/assets/get-started1.png)

1. 여러 조직에 액세스할 수 있는 경우 올바른 조직에 로그인했는지 확인합니다. 조직을 변경하려면 오른쪽 상단에서 조직 이름을 클릭하고 액세스가 필요한 필수 조직을 선택합니다.

   ![조직 변경](/help/journey-onboarding/assets/admin-console-orgswitch.png)

1. 시스템 관리자인지 확인하려면 **사용자** 카드에서 **관리자**&#x200B;를 선택합니다.

   ![관리자 검토](/help/journey-onboarding/assets/get-started2.png)

1. **사용자** 카드에서 **관리자**&#x200B;를 클릭하면 Adobe ID 이메일, 사용자 이름, 이름 또는 성을 입력하여 검색할 수 있습니다.

   ![사용자 검색](/help/journey-onboarding/assets/get-started3.png)

1. 모든 기능이 제대로 작동하면 검색에서 레코드를 반환합니다. **관리자 역할** 열의 값에 **시스템**&#x200B;이 표시되면 자신(또는 표시된 사용자)가 시스템 관리자임을 알 수 있습니다.

   ![시스템 상태](/help/journey-onboarding/assets/get-started4.png)

구성, 시스템 관리자!

## Adobe Identity Management 시스템 {#ims}

AEM as a Cloud Service는 인증을 위해 Adobe Identity Management System(IMS라고도 함)과 함께 사전 구성되어 제공됩니다. 이 기능을 사용하기 위해 시스템 관리자가 수행해야 하는 작업은 없습니다.

AEM as a Cloud Service는 IMS를 사용하여 AEM과 나머지 Adobe Experience Cloud 간의 로그인 경험을 통합합니다. 여러 Adobe 제품을 사용하는 조직은 특히 Admin Console에서 역할 기반 그룹을 만든 다음 IMS를 통해 AEM as a Cloud Service를 포함하는 여러 제품에 대한 액세스 권한을 할당함으로써 이점을 얻을 수 있습니다.

이 온보딩 여정의 다음 부분에서는 제품 프로필 및 사용자 할당에 대해 자세히 알아봅니다.

## Adobe 지원 센터 문의 {#support}

문제가 있는 경우 Admin Console을 통해 Adobe 지원 센터에 액세스할 수 있습니다. **지원** 탭을 사용하여 간단하고 사용하기 쉬운 인터페이스를 통해 다양한 Adobe 지원 기능을 이용할 수 있습니다.

![지원 탭](/help/journey-onboarding/assets/support-menu.png)

이 탭에서 사례를 만들고 관리할 수 있으며 Adobe 고객 지원 센터 담당자와 직접 채팅하고 전문가와의 세션을 예약할 수 있습니다. 시스템 관리자 및 지원 관리자는 지원 사례와 전문가 세션 옵션을 이용하려면 로그인해야 합니다.

## 다음 단계 {#whats-next}

이 문서를 읽고 나면 다음과 같은 작업을 수행할 수 있습니다.

* Adobe ID가 무엇인지 이해합니다.
* Admin Console에 로그인할 수 있습니다.
* Admin Console을 통해 시스템 관리자로서의 권한을 검토하는 방법을 이해합니다.
* 도움이 필요한 경우 Adobe 지원 센터에 문의하는 방법을 이해합니다.

이제 온보딩 여정을 계속하여 [Cloud Manager 제품 프로필에 팀원 할당](assign-profiles-cloud-manager.md) 문서를 검토하고 동료도 AEMaaCS에 액세스할 수 있도록 팀원을 Cloud Manager 제품 프로필에 할당하는 방법을 배울 준비가 되었습니다.

## 추가 리소스 {#additional-resources}

다음은 온보딩 여정의 콘텐츠를 넘어서고자 하는 경우 선택할 수 있는 추가 리소스입니다.

* [Admin Console 개요](https://helpx.adobe.com/kr/enterprise/using/admin-console.html) - Admin Console에 대한 포괄적인 개요
* [Adobe ID 만들기 또는 업데이트](https://helpx.adobe.com/ca/manage-account/using/create-update-adobe-id.html#HowtocreateorupdateyourAdobeID) - Adobe ID를 만들고, 변경하고, 여러 Adobe ID를 관리하는 방법에 대해 알아봅니다.
* [SAML 2.0 Authentication Handler](https://experienceleague.adobe.com/docs/experience-manager-65/administering/security/saml-2-0-authenticationhandler.html) - AEM은 SAML 인증 핸들러와 함께 제공됩니다. 이 핸들러는 HTTP POST 바인딩을 사용하여 SAML 2.0 인증 요청 프로토콜(Web-SSO 프로필)을 지원합니다.
* [관리 역할](https://helpx.adobe.com/kr/enterprise/using/admin-roles.ug.html) - 조직은 Adobe Admin Console을 사용하여 Adobe 제품 액세스 및 사용을 세분화하고 관리할 수 있는 유연한 관리 계층 구조를 정의할 수 있습니다.
* [지원 및 전문가 세션](https://helpx.adobe.com/kr/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) - Admin Console에서 지원 옵션을 이용하고, 지원 사례를 관리하고, 전문가 세션을 예약하는 방법 등에 대해 알아봅니다.
