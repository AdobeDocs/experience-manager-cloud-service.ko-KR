---
title: IMS 클라우드 서비스로서의 Adobe Experience Manager 지원
description: 'IMS 클라우드 서비스로서의 Adobe Experience Manager 지원 '
translation-type: tm+mt
source-git-commit: bef17376f0b7de79511f9ad6ceb00e9f084f45d2

---


# IMS 클라우드 서비스로서의 Adobe Experience Manager 지원 {#ims-support-for-aem-as-a-cloud-service}

## 소개 {#introduction}

* 클라우드 서비스로서의 AEM에는 AEM 인스턴스 및 Adobe IMS(Identity Management System) 기반 인증에 대한 관리 콘솔 지원이 포함되어 있습니다.
* 관리자는 관리 콘솔을 사용하여 모든 Experience Cloud 사용자를 중앙에서 관리할 수 있습니다.
* 사용자 및 그룹을 클라우드 서비스 인스턴스로 AEM과 연결된 제품 프로필에 할당하여 해당 인스턴스에 로그인할 수 있도록 할 수 있습니다.

## 주요 특징 {#key-highlights}

클라우드 서비스로서 AEM은 작성자, 관리자 및 개발 사용자에 대해서만 IMS 인증 지원을 제공합니다. 사이트 방문자와 같은 고객 사이트의 외부 최종 사용자를 지원하지 않습니다.

* 관리 콘솔은 고객이 IMS 조직, 작성자 및 게시 인스턴스로 제품 컨텍스트 인스턴스로 표시됩니다. 이렇게 하면 시스템 및 제품 관리자가 인스턴스에 대한 액세스를 관리할 수 있습니다.
* 관리 콘솔의 제품 프로필에서 사용자가 액세스할 수 있는 인스턴스를 결정합니다.
* 고객은 SSO(Single Sign On)에 대해 자체 SAML 2 호환 ID 공급자(IDP)를 사용할 수 있습니다.
* 고객 SSO(Single Sign On)에 대한 Enterprise ID 또는 Federated ID만 지원되며 개인 Adobe ID는 지원되지 않습니다.

## 아키텍처 {#architecture}

IMS 인증은 AEM과 Adobe IMS 끝점 간 OAuth 프로토콜을 사용합니다. 사용자가 IMS에 추가되고 Adobe Identity가 있으면 IMS 자격 증명을 사용하여 AEM 작성자 서비스에 로그인할 수 있습니다.

사용자 로그인 흐름이 아래에 표시되어 있고, 사용자는 IMS로 리디렉션되고, 선택적으로 SSO용 고객 IDP로 리디렉션된 다음 AEM으로 다시 리디렉션됩니다.

![IMS 아키텍처](/help/security/assets/ims1.png)

## 설정 방법 {#how-to-set-up}

### Adobe Admin Console로 조직 가입 {#onboarding-orgs-to-adobe-admin-console}

Adobe Admin Console에 대한 고객 등록은 AEM 인증에 Adobe IMS를 사용하기 위한 사전 요구 사항입니다.

첫 번째 단계로, 고객은 Adobe IMS에서 조직이 프로비저닝되어야 합니다. Adobe Enterprise 고객은 Adobe Admin Console에서 [IMS로](https://helpx.adobe.com/enterprise/using/admin-console.html) 표시됩니다. Adobe 고객이 사용자 및 그룹에 대한 제품 권한을 관리하는 데 사용하는 포털입니다.

AEM 고객은 이미 조직이 프로비저닝되어 있어야 하며 IMS 프로비저닝의 일부로 사용자 권한 및 액세스를 관리하기 위해 고객 인스턴스를 관리 콘솔에서 사용할 수 있게 됩니다.

고객이 IMS 조직으로 존재하면 아래 요약으로 시스템을 구성해야 합니다.

![IMS 온보딩](/help/security/assets/ims2.png)

1. 지정된 시스템 관리자는 Cloud Manager에 로그인하라는 초대를 받습니다. Cloud Manager에 로그인한 후 시스템 관리자는 AEM 프로그램 및 환경을 프로비저닝하거나 관리 작업을 위해 관리 콘솔로 이동할 수 있습니다.
1. 시스템 관리자는 도메인을 요청하여 해당 도메인의 소유권을 확인합니다(예: acme.com).
1. 시스템 관리자가 사용자 디렉토리를 설정합니다.
1. 시스템 관리자는 Single Sign On을 설정하기 위해 관리 콘솔에서 IDP 구성을 수행합니다.
1. AEM 관리자는 평소대로 로컬 그룹, 권한 및 권한을 관리합니다.

IDP 구성을 비롯한 Adobe Identity Management 기본 사항은 [여기에서](https://helpx.adobe.com/enterprise/using/set-up-identity.html)다룹니다.

엔터프라이즈 관리 및 관리 콘솔 사용에 대해서는 [여기에서](https://helpx.adobe.com/enterprise/managing/user-guide.html)다룹니다.

### Admin Console에서 온보딩 사용자 {#onboarding-users-in-admin-console}

고객의 규모와 선호도에 따라 사용자를 승선시키는 방법은 세 가지가 있습니다.관리 콘솔에서 사용자를 수동으로 만들고, .csv 파일을 업로드하거나, 고객의 기업 Active Directory에서 사용자를 동기화합니다.

**관리 콘솔 UI를 통한 수동 추가**

사용자 및 그룹은 관리 콘솔 UI에서 수동으로 만들 수 있습니다. 이 방법은 관리할 사용자가 많지 않은 경우에 사용할 수 있습니다. 예를 들어 50명 미만의 AEM 사용자 또는 Analytics, Target 또는 Creative Cloud 애플리케이션과 같은 다른 Adobe 제품을 관리하기 위해 이 방법을 이미 사용하고 있는 경우

![사용자 온보딩](/help/security/assets/ims3.png)

**관리 콘솔 UI에서 파일 업로드**

사용자 작성을 쉽게 처리하기 위해 사용자를 일괄 추가하기 위해 `.csv` 파일을 업로드할 수 있습니다.

![파일 업로드](/help/security/assets/ims4.png)

**사용자 동기화 도구**

UST(User Sync Tool)를 통해 기업 고객은 Active Directory를 사용하여 Adobe 사용자를 만들고 관리할 수 있습니다. 또한 다른 테스트된 OpenLDAP 디렉토리 서비스에도 적용됩니다. 대상 사용자는 도구를 설치 및 구성할 수 있는 IT ID 관리자(Enterprise Directory 또는 시스템 관리자)입니다. 오픈 소스 툴은 고객이 특정 요구 사항에 맞게 수정할 수 있도록 사용자 정의할 수 있습니다.

사용자 동기화가 실행되면 조직의 Active Directory 사용자 목록을 가져와서 관리 콘솔 내의 사용자 목록과 비교합니다.  그런 다음 Adobe User Management API를 호출하여 Admin Console이 조직의 디렉토리와 동기화되도록 합니다. 변경 흐름은 완전히 한 가지 방식입니다. Admin Console에서 편집한 내용은 해당 디렉토리에 푸시되지 않습니다.

시스템 관리자는 이 도구를 사용하여 고객 디렉토리의 사용자 그룹을 관리 콘솔의 제품 구성 및 사용자 그룹과 매핑할 수 있습니다.

사용자 동기화를 설정하려면 조직에서 사용자 관리 API를 사용하는 것과 같은 방식으로 자격 증명 세트를 만들어야 [합니다](https://www.adobe.io/apis/experienceplatform/umapi-new.html).

![사용자 동기화 도구](/help/security/assets/ims5.png)

사용자 동기화 도구는 이 [위치의](https://github.com/adobe-apiplatform/user-sync.py/releases/latest)Adobe Github 저장소를 통해 배포됩니다.

>[!NOTE]
>
> A prerelease version **2.4RC1** is available with dynamic group creation support, and can be found [here](https://github.com/adobe-apiplatform/user-sync.py/releases/tag/v2.4rc1).

이 릴리스의 주요 기능은 Admin Console에서 사용자 멤버십에 대한 새 LDAP 그룹을 동적으로 매핑하고 동적 사용자 그룹 생성을 수행하는 기능입니다.

새 그룹 기능에 대한 자세한 내용은 이 [위치에서](https://github.com/adobe-apiplatform/user-sync.py/blob/v2/docs/en/user-manual/advanced_configuration.md#additional-group-options)찾을 수 있습니다.

**사용자 동기화 설명서**

자세한 내용은 [UST 설명서를](https://adobe-apiplatform.github.io/user-sync.py/en/) 참조하십시오.

사용자 동기화 도구는 [여기에서](https://adobe-apiplatform.github.io/umapi-documentation/en/UM_Authentication.html)절차를 사용하여 Adobe I/O 클라이언트 UMAPI로 등록해야 합니다.

Adobe I/O 콘솔 문서는 [여기에서](https://www.adobe.io/apis/cloudplatform/console.html)찾을 수 있습니다.

사용자 동기화 도구에서 사용되는 사용자 관리 API는 [여기에서](https://www.adobe.io/apis/cloudplatform/umapi-new.html)다룹니다.

## 클라우드 서비스 구성으로서의 Adobe Experience {#aem-configuration}

> [!NOTE]
>
>필요한 AEM IMS 구성은 AEM 환경 및 인스턴스가 프로비전될 때 자동으로 구성됩니다. 그러나 관리자는 [여기에서](/help/implementing/deploying/overview.md)설명하는 방법을 사용하여 요구 사항에 따라 수정할 수 있습니다.

필요한 AEM IMS 구성은 AEM 환경 및 인스턴스가 프로비전될 때 자동으로 구성됩니다.  고객 관리자는 요구 사항에 따라 구성의 일부를 수정할 수 있습니다.

전체 접근 방식은 Adobe IMS를 OAuth 공급자로 구성하는 것입니다. Apache **Jackrabbit Oak Default Sync** Handler를 LDAP 동기화의 경우와 마찬가지로 수정할 수 있습니다.

다음은 사용자 자동 구성원 자격 또는 그룹 매핑과 같은 속성을 변경하기 위해 수정해야 하는 주요 OSGI 구성입니다.

<!-- Arun to provide list of osgi configs -->

## 사용 방법 {#how-to-use}

### 관리 콘솔에서 제품 및 사용자 액세스 관리 {#managing-products-and-user-access-in-admin-console}

제품 관리자가 관리 콘솔에 로그인하면, 아래와 같이 AEM Managed Services 제품 컨텍스트의 여러 인스턴스가 표시됩니다.

![인스턴스 로그인](/help/security/assets/ims6.png)

이 예에서는 조직 AEM-MS- **Onboard의** 경우 스테이지 또는 Prod와 같은 서로 다른 토폴로지 및 환경에 걸쳐 32개의 인스턴스가 있습니다.

![인스턴스 로그인2](/help/security/assets/ims7.png)

각 제품 컨텍스트 인스턴스에는 관련 제품 프로필이 있습니다. 이러한 제품 프로필은 필요한 권한을 가진 사용자 및 그룹에 대한 액세스 권한을 할당하는 데 사용됩니다.

Administrator **_xxx** 프로필은 연결된 AEM 인스턴스에서 관리자 권한을 부여하는 데 사용되고 User_xxx **프로필은** 일반 사용자를 추가하는 데 사용됩니다.

이 제품 프로필에 추가된 모든 사용자 및 그룹은 아래 예와 같이 해당 특정 인스턴스에 로그인할 수 있습니다.

![제품 프로필](/help/security/assets/ims8.png)

### 클라우드 서비스로 Adobe Experience Manager 로그인(#logging-in-to-aem)

**로컬 관리자 로그인**

AEM은 관리 사용자에 대한 로컬 로그인을 계속 지원할 수 있습니다. 로그인 화면에는 로컬로 로그인할 수 있는 옵션이 있습니다.

![로컬 로그인](/help/security/assets/ims9.png)

<!-- the above image needs to be updated for skyline -->

**IMS 기반 로그인**

다른 사용자의 경우 인스턴스에 IMS가 구성되면 IMS 기반 로그인을 사용할 수 있습니다. 사용자는 아래에 표시된 대로 먼저 Adobe로 로그인 버튼을 클릭합니다.

![IMS 로그인](/help/security/assets/ims10.png)

그러면 IMS 로그인 화면으로 리디렉션되고 자격 증명을 입력해야 합니다.

![IMS 로그인2](/help/security/assets/ims11.png)

![IMS 로그인3](/help/security/assets/ims12.png)

Federated IDP가 초기 Admin Console 설정 중에 구성된 경우 사용자는 SSO용 고객 IDP로 리디렉션됩니다.

![IMS 로그인4](/help/security/assets/ims13.png)

인증이 완료되면 사용자는 다시 AEM으로 리디렉션되고 로그인됩니다.

![IMS 로그인5](/help/security/assets/ims14.png)

### 클라우드 서비스로 Adobe Experience Manager의 권한 및 ACL 관리 {#managing-permissions-in-aem}

ACL 및 권한은 AEM에서 계속 관리됩니다. IMS에서 동기화된 사용자 그룹은 ACL 및 권한이 정의된 로컬 그룹에 할당할 수 있습니다.

아래 예에서는 동기화된 그룹을 로컬 Dam_Users **그룹에** 추가합니다.

사용자는 IMS에서 다음 그룹의 일부입니다.

![ACL1](/help/security/assets/ims15.png)

사용자가 로그인하면 그룹 멤버십이 아래와 같이 동기화됩니다.

![ACL2](/help/security/assets/ims16.png)

AEM 파섹  ****

![ACL3](/help/security/assets/ims17.png)

아래에 표시된 바와 같이, **AEM-GRP_008** 그룹은 DAM 사용자의 권한과 권한을 ****&#x200B;상속합니다. 이는 동기화된 그룹에 대한 권한을 효과적으로 관리하는 방법이며 LDAP 기반 인증 방법에서도 일반적으로 사용됩니다.

![ACL3](/help/security/assets/ims18.png)