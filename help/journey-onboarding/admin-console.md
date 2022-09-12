---
title: Admin Console 액세스
description: AEMaaCS 구조의 온보딩에 필요한 준비와 기본 사항을 이해하면 Admin Console에 처음으로 로그인할 수 있습니다.
exl-id: 0ccce328-a356-4ba9-b7fe-f67abc25b924
source-git-commit: 097c17b37cc308dc906cd4af7dc7c5d51862bdfa
workflow-type: tm+mt
source-wordcount: '1092'
ht-degree: 2%

---

# Admin Console 액세스 {#accessing-admin-console}

의 이 부분에서 [온보딩 여정,](overview.md) 시스템에 처음 로그인하기 전에 필요한 준비에 대해 학습합니다.

## 목표 {#objective}

이제 그 기사를 읽으셨군요 [AEM as a Cloud Service 용어](terminology.md) aemAaCS 구조의 기본 사항을 이해하면 처음으로 Admin Console에 로그인할 수 있습니다.

시스템 관리자는 조직 내에서 사용자를 관리할 책임이 있습니다. Admin Console을 사용하여 이 작업을 수행합니다. 이 섹션을 읽은 후에는 다음을 수행해야 합니다.

* Adobe ID 정의 이해
* Admin Console에 로그인할 수 있습니다.
* Admin Console을 통해 시스템 관리자로서 권한을 검토하는 방법을 이해합니다.
* 도움이 필요하면 Adobe 지원에 문의하는 방법을 알아봅니다.

## Admin Console {#admin-console}

Adobe Admin Console은 Adobe 제품 라이선스 및 사용자를 관리하고 관리할 수 있는 중앙 위치입니다. Admin Console을 사용하면 다양한 개별 솔루션 내에서 사용자를 만들고 관리할 수 있습니다.

## Adobe ID {#adobe-id}

Admin Console에 로그인하려면 Adobe ID이 필요합니다. 또한 Adobe ID은 AEM as a Cloud Service 또는 모든 Adobe 솔루션에 로그인하고 액세스하는 데 필요한 특정 이메일 주소에 연결된 계정입니다. Adobe ID을 사용하면 모든 Adobe 계획과 제품을 단일 계정과 연결된 상태로 유지할 수 있습니다.

시스템 관리자가 Admin Console에서 팀을 설정할 때 Adobe ID으로 사용할 이메일 주소를 지정합니다.

다음 세 가지 유형의 Adobe ID가 있습니다.

* **개인 ID**: Adobe ID의 기본 유형이며 adobe.com에 만들어집니다. 이 계정은 Adobe에서 관리되며 누구나 이 유형의 계정을 만들 수 있습니다.

* **Enterprise ID**: 조직은 일반적으로 사용자 계정에 대한 제어를 증가시키려고 합니다. 시스템 관리자만 Enterprise ID를 만들 수 있으며, 조직은 Adobe을 호스트로만 제공하는 계정을 소유합니다.

* **Federated ID**: Federated ID를 통해 조직은 계정에 대한 전체 소유와 제어를 수행합니다. 이를 수행하려면 조직에서 Adobe Experience Cloud을 SAML2 SSO(Single Sign-On) 시스템과 통합해야 합니다. 이를 통해 사용자는 Adobe에서 호스팅하는 계정이 아니라 조직의 SSO 시스템을 인증할 수 있습니다.

시스템 관리자는 Enterprise ID 또는 Federated ID를 설정하기 전에 개인 ID를 사용하여 자신과 팀을 AEM as a Cloud Service으로 온보딩하도록 결정할 수 있습니다. Enterprise ID 또는 Federated ID가 설정되면 구성원은 해당 ID를 사용하여로 전환될 수 있습니다.

## Admin Console에 로그인 {#steps-admin-console}

Admin Console을 사용하여 팀 내의 사용자를 관리하려면 먼저 사용자 자신이 해당 사용자에 제대로 액세스하고 적절한 권한을 가질 수 있는지 확인해야 합니다.

1. 시스템 관리자는 온보딩 프로세스의 일부로 Adobe에서 여러 이메일을 받게 됩니다. 액세스 권한이 부여된 조직 이름에 대한 정보를 제공하는 환영 이메일을 찾습니다.

1. 을(를) 클릭합니다. **시작** Admin Console으로 이동하려면 환영 이메일에 연결합니다. 이메일을 찾을 수 없는 경우에는 브라우저를 직접 열어 을(를) Admin Console [`https://adminconsole.adobe.com`](https://adminconsole.adobe.com).

   ![시작 이메일](/help/journey-onboarding/assets/get-started-email.png)

1. Adobe ID를 사용하여 로그인합니다. 로그인하면 **개요** Adobe Admin Console 페이지입니다.

   ![Admin Console](/help/journey-onboarding/assets/get-started1.png)

1. 여러 조직에 대한 액세스 권한이 있는 경우 올바른 조직에 로그인되어 있는지 확인하십시오. 조직을 변경하려면 오른쪽 상단 모서리에서 조직 이름을 클릭하고 액세스 권한이 필요한 조직을 선택합니다.

   ![조직 변경](/help/journey-onboarding/assets/admin-console-orgswitch.png)

1. 선택 **관리자** 에서 **사용자** 시스템 관리자임을 확인하는 카드입니다.

   ![관리자 검토](/help/journey-onboarding/assets/get-started2.png)

1. 클릭하면 **관리자** 에서 **사용자** 카드에서는 Adobe ID 이메일, 사용자 이름, 이름 또는 성을 입력하여 검색할 수 있습니다.

   ![사용자 검색](/help/journey-onboarding/assets/get-started3.png)

1. 모든 것이 제대로 작동하면 검색이 레코드를 반환합니다. 에 있는 값이 **관리자 역할** 열 표시 **시스템**&#x200B;를 사용하는 사용자(또는 표시된 사용자)가 시스템 관리자임을 알 수 있습니다.

   ![시스템 상태](/help/journey-onboarding/assets/get-started4.png)

축하합니다, 시스템 관리자!

## Adobe ID 관리 시스템 {#ims}

AEM as a Cloud Service은 인증을 위해 Adobe Identity Management 시스템(IMS라고도 함)으로 사전 구성되어 있습니다. 이를 활성화하기 위해 시스템 관리자로 수행할 필요가 없습니다.

AEM에서는 IMS를 사용하여 AEM과 나머지 Adobe Experience Cloud 간에 로그인 경험을 as a Cloud Service으로 통합합니다. 여러 Adobe 제품을 사용하는 조직은 특히 Admin Console에서 역할 기반 그룹을 만든 다음 IMS를 통해 AEM as a Cloud Service을 포함한 여러 제품에 대한 액세스를 할당함으로써 혜택을 받습니다.

이 온보딩 여정의 다음 부분에서 제품 프로필과 사용자 지정에 대해 자세히 알아봅니다.

## Adobe 지원에 문의 {#support}

문제가 있는 경우 Admin Console을 통해 Adobe 지원에 액세스할 수 있습니다. 다음 **지원** 탭에서는 간단하고 사용하기 쉬운 인터페이스를 통해 다양한 Adobe 지원 기능에 액세스할 수 있습니다.

![지원 탭](/help/journey-onboarding/assets/support-menu.png)

탭에서는 사례를 만들고 관리하고, Adobe 고객 지원 담당자와 직접 채팅하고, 전문가와 세션을 예약할 수 있습니다. 시스템 관리자 및 지원 관리자는 지원 사례 및 전문가 세션 옵션에 액세스하려면 로그인해야 합니다.

## 다음 단계 {#whats-next}

이 문서를 읽은 후에는 다음을 수행해야 합니다.

* 및 Adobe ID의 정의 이해
* Admin Console에 로그인할 수 있습니다.
* Admin Console을 통해 시스템 관리자로서 권한을 검토하는 방법을 이해합니다.
* 도움이 필요하면 Adobe 지원에 문의하는 방법을 알아봅니다.

다음 방법을 배우면 온보딩 여정을 계속 진행할 수 있습니다 [Cloud Manager 제품 프로필에 팀 구성원 할당](assign-profiles-cloud-manager.md) 동료가 AEMaaCS에 액세스할 수도 있도록 하기 위해

## 추가 리소스 {#additional-resources}

* [Admin Console 개요](https://helpx.adobe.com/enterprise/using/admin-console.html) - Admin Console에 대한 포괄적인 개요
* [Adobe ID 만들기 또는 업데이트](https://helpx.adobe.com/ca/manage-account/using/create-update-adobe-id.html#HowtocreateorupdateyourAdobeID) - Adobe ID을 만들고, 변경하고, 여러 Adobe ID를 관리하는 방법을 알아봅니다.
* [SAML 2.0 인증 핸들러](https://experienceleague.adobe.com/docs/experience-manager-65/administering/security/saml-2-0-authenticationhandler.html) - AEM은 SAML 인증 핸들러를 사용하여 제공됩니다. 이 처리기는 HTTP POST 바인딩을 사용하여 SAML 2.0 인증 요청 프로토콜(Web-SSO 프로필)을 지원합니다.
* [관리 역할](https://helpx.adobe.com/enterprise/using/admin-roles.ug.html) - 조직은 Adobe Admin Console을 사용하여 Adobe 제품 액세스 및 사용을 세밀하게 관리할 수 있는 유연한 관리 계층을 정의할 수 있습니다.
* [지원 및 전문가 세션](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) - Admin Console의 지원 옵션에 액세스하고, 지원 사례를 관리하고, 전문가 세션을 예약하는 등의 방법을 알아봅니다.
