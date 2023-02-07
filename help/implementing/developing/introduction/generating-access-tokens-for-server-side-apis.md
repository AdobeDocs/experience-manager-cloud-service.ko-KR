---
title: 서버측 API용 액세스 토큰 생성
description: 보안 JWT 토큰을 생성하여 타사 서버와 AEM as a Cloud Service 간의 통신을 용이하게 하는 방법을 알아봅니다
exl-id: 20deaf8f-328e-4cbf-ac68-0a6dd4ebf0c9
source-git-commit: 9f7157be1a9e7b635b9c7d0f0c653646e6f1b43b
workflow-type: tm+mt
source-wordcount: '2132'
ht-degree: 1%

---

# 서버측 API용 액세스 토큰 생성 {#generating-access-tokens-for-server-side-apis}

일부 아키텍처에서는 AEM 인프라 외부의 서버에 호스팅된 애플리케이션에서 AEM as a Cloud Service을 호출하는 데 사용합니다. 예를 들어 서버를 호출한 다음 AEM as a Cloud Service에 API 요청을 수행하는 모바일 애플리케이션입니다.

서버 간 흐름은 개발을 위한 간단한 흐름과 함께 아래에 설명되어 있습니다. AEM as a Cloud Service [개발자 콘솔](development-guidelines.md#crxde-lite-and-developer-console) 는 인증 프로세스에 필요한 토큰을 생성하는 데 사용됩니다.

<!-- Alexandru: hiding this until the tutorials reflect the new UI

>[!NOTE]
>
>In addition to this documentation, you can also consult the tutorials on [Token-based authentication for AEM as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/authentication/overview.html?lang=en#authentication) and [Getting a Login Token for Integrations](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-5/cloud5-getting-login-token-integrations.html). -->

## 서버 간 흐름 {#the-server-to-server-flow}

IMS 조직 관리자 역할을 가진 사용자 및 AEM 작성자의 AEM 사용자 또는 AEM 관리자 제품 프로필 멤버이기도 한 사용자는 각각 인증서(공개 키), 개인 키 및 로 구성된 기술 계정을 포함하는 AEM as a Cloud Service 자격 증명 세트를 생성할 수 있습니다. `clientId` 및 `clientSecret`. 이러한 자격 증명은 나중에 AEM as a Cloud Service 환경 관리자 역할을 가진 사용자가 검색할 수 있으며 비 AEM 서버에 설치하고 보안 키로 신중하게 처리되어야 합니다. 이 JSON 형식 파일에는 AEM as a Cloud Service API와 통합하는 데 필요한 모든 데이터가 포함되어 있습니다. 이 데이터는 IMS 액세스 토큰에 대해 IMS(Adobe Identity Management Services)와 교환되는 서명된 JWT 토큰을 만드는 데 사용됩니다. 그런 다음 이 액세스 토큰을 AEM as a Cloud Service에 대한 요청을 수행하는 베어러 인증 토큰으로 사용할 수 있습니다. 자격 증명의 인증서는 기본적으로 1년 후에 만료되지만, 필요한 경우 새로 고칠 수 있습니다 [여기](#refresh-credentials).

서버 간 흐름에는 다음 단계가 포함됩니다.

* 개발자 콘솔에서 AEM as a Cloud Service 자격 증명을 가져옵니다.
* AEM을 호출하는 비 AEM 서버에 AEM as a Cloud Service 자격 증명을 설치합니다
* JWT 토큰을 생성하고 Adobe의 IMS API를 사용하여 액세스 토큰에 대해 해당 토큰을 교환합니다
* 액세스 토큰을 사용하여 AEM API를 베어러 인증 토큰으로 호출
* AEM 환경에서 기술 계정 사용자에 대한 적절한 권한 설정

### AEM as a Cloud Service 자격 증명 가져오기 {#fetch-the-aem-as-a-cloud-service-credentials}

AEM as a Cloud Service 개발자 콘솔에 액세스할 수 있는 사용자는 주어진 환경에 대해 개발자 콘솔에 통합 탭이 표시됩니다. AEM as a Cloud Service 환경 관리자 역할을 가진 사용자는 자격 증명을 생성, 보기 또는 관리할 수 있습니다.

클릭 **새 기술 계정 만들기** 단추. pod 선택 여부에 관계없이 환경의 작성자 및 게시 계층에 대한 구성, 클라이언트 id, 클라이언트 암호, 개인 키, 인증서 및 클라이언트 id를 포함하는 새 자격 증명 세트가 만들어집니다.

![새 기술 계정 만들기](/help/implementing/developing/introduction/assets/s2s-createtechaccount.png)

자격 증명을 표시하는 새 브라우저 탭이 열립니다. 이 보기를 사용하여 상태 제목 옆에 있는 다운로드 아이콘을 눌러 자격 증명을 다운로드할 수 있습니다.

![자격 증명 다운로드](/help/implementing/developing/introduction/assets/s2s-credentialdownload.png)

자격 증명이 만들어지면 아래에 표시됩니다 **기술 계정** 탭에서 다음을 수행합니다. **통합** 섹션:

![자격 증명 보기](/help/implementing/developing/introduction/assets/s2s-viewcredentials.png)

사용자는 나중에 보기 작업을 사용하여 자격 증명을 볼 수 있습니다. 또한 문서의 후반부에 설명된 대로, 인증서를 갱신하거나 취소해야 하는 경우 새 개인 키 또는 인증서를 만들어 동일한 기술 계정에 대한 자격 증명을 수정할 수 있습니다.

AEM as a Cloud Service 환경 관리자 역할을 가진 사용자는 나중에 추가 기술 계정에 대한 새 자격 증명을 만들 수 있습니다. 이 기능은 API에 액세스 요구 사항이 다른 경우에 유용합니다. 예를 들어, 읽기와 읽기 쓰기가 있습니다.

>[!NOTE]
>
>고객은 이미 삭제된 계정을 포함하여 최대 10개의 기술 계정을 만들 수 있습니다.

>[!IMPORTANT]
>
>IMS 조직 관리자(일반적으로 Cloud Manager를 통해 환경을 프로비저닝한 사용자)는 AEM 작성자의 AEM 사용자 또는 AEM 관리자 제품 프로필에 포함되어야 하며, 먼저 개발자 콘솔에 액세스하고 **새 기술 계정 만들기** 단추를 클릭하여 자격 증명을 생성하고 나중에 AEM as a Cloud Service 환경에 대한 관리자 권한이 있는 사용자가 검색할 수 있습니다. IMS 조직 관리자가 이를 수행하지 않은 경우 IMS 조직 관리자 역할이 필요하다는 메시지가 표시됩니다.

### 비 AEM 서버에 AEM 서비스 자격 증명 설치 {#install-the-aem-service-credentials-on-a-non-aem-server}

AEM에 전화를 거는 애플리케이션은 AEM as a Cloud Service 자격 증명에 액세스하여 암호로 처리할 수 있어야 합니다.

### JWT 토큰을 생성하고 액세스 토큰으로 교환합니다 {#generate-a-jwt-token-and-exchange-it-for-an-access-token}

24시간 동안 유효한 액세스 토큰을 검색하기 위해 자격 증명을 사용하여 Adobe의 IMS 서비스 호출에 JWT 토큰을 만듭니다.

이 용도로 설계된 클라이언트 라이브러리를 사용하여 AEM CS 서비스 자격 증명을 액세스 토큰과 교환할 수 있습니다. 클라이언트 라이브러리는 [Adobe의 공용 GitHub 리포지토리](https://github.com/adobe/aemcs-api-client-lib): 더 자세한 지침 및 최신 정보를 포함합니다.

```
/*jshint node:true */
"use strict";

const fs = require('fs');
const exchange = require("@adobe/aemcs-api-client-lib");

const jsonfile = "aemcs-service-credentials.json";

var config = JSON.parse(fs.readFileSync(jsonfile, 'utf8'));
exchange(config).then(accessToken => {
    // output the access token in json form including when it will expire.
    console.log(JSON.stringify(accessToken,null,2));
}).catch(e => {
    console.log("Failed to exchange for access token ",e);
});
```

올바른 형식의 서명된 JWT 토큰을 생성하고 IMS 토큰 교환 API를 호출할 수 있는 모든 언어로 동일한 교환을 수행할 수 있습니다.

액세스 토큰은 만료 시기를 정의합니다(일반적으로 24시간). 액세스 토큰을 관리하고 만료되기 전에 새로 고치는 샘플 코드가 Git 리포지토리에 있습니다.

>[!NOTE]
>자격 증명이 여러 개 있는 경우 나중에 호출될 AEM에 대한 API 호출에 적절한 json 파일을 참조해야 합니다.

### AEM API를 호출합니다 {#calling-the-aem-api}

헤더에 액세스 토큰을 포함하여 AEM as a Cloud Service 환경에 대한 적절한 서버 간 API 호출을 수행하십시오. 따라서 &quot;Authorization&quot; 헤더에 대해 값을 사용합니다 `"Bearer <access_token>"`. 예를 들어 `curl`:

```curlc
curl -H "Authorization: Bearer <your_ims_access_token>" https://author-p123123-e23423423.adobeaemcloud.com/content/dam.json
```

### AEM에서 기술 계정 사용자에 대한 적절한 권한 설정 {#set-the-appropriate-permissions-for-the-technical-account-user-in-aem}

먼저 Adobe Admin Console에서 새 제품 프로필을 만들어야 합니다. 다음 단계를 수행하여 이 작업을 수행할 수 있습니다.

1. 의 Adobe Admin Console으로 이동합니다. [https://adminconsole.adobe.com/](https://adminconsole.adobe.com/)
1. 누르기 **관리** 아래의 링크 **제품 및 서비스** 왼쪽에 있는 열입니다.
1. 선택 **AEM as a Cloud Service**
1. 누르기 **새 프로필** 버튼

   ![새 프로필](/help/implementing/developing/introduction/assets/s2s-newproductprofile.png)

1. 프로필 이름을 지정하고 키를 누릅니다 **저장**

   ![프로필 저장](/help/implementing/developing/introduction/assets/s2s-saveprofile.png)

1. 프로필 목록에서 방금 만든 프로필을 선택합니다
1. 누르기 **사용자 추가** 버튼

   ![사용자 추가](/help/implementing/developing/introduction/assets/s2s-addusers.png)

1. 방금 만든 기술 계정을 추가합니다(이 경우 `84b2c3a2-d60a-40dc-84cb-e16b786c1673@techacct.adobe.com`) 를 누르고 키를 누릅니다. **저장**

   ![기술 계정 추가](/help/implementing/developing/introduction/assets/s2s-addtechaccount.png)

1. 변경 사항이 적용되도록 10분을 기다린 후 새 자격 증명에서 생성된 액세스 토큰을 사용하여 AEM에 API를 호출합니다. 이 명령은 cURL 명령으로 다음 예제와 유사하게 표시됩니다.

   `curl -H "Authorization: Bearer <access_token>" https://author-pXXXXX-eXXXXX.adobeaemcloud.net/content/dam.json `


API를 호출한 후 제품 프로필은 AEM as a Cloud Service 작성자 인스턴스에서 사용자 그룹으로 표시되며, 적절한 기술 계정은 해당 그룹의 구성원으로 표시됩니다.

이를 확인하려면 다음을 수행해야 합니다.

1. 작성자 인스턴스에 로그인합니다.
1. 이동 **도구** - **보안** 을 클릭하고 **그룹** 카드
1. 그룹 목록에서 만든 프로필의 이름을 찾아 클릭합니다.

   ![그룹 프로필](/help/implementing/developing/introduction/assets/s2s-groupprofile.png)

1. 다음 창에서 **멤버** 탭하여 기술 계정이 여기에 올바르게 나열되는지 확인합니다.

   ![멤버 탭](/help/implementing/developing/introduction/assets/s2s-techaccountmembers.png)


또는 작성자 인스턴스에서 아래 단계를 수행하여 기술 계정이 사용자 목록에 표시되는지 확인할 수도 있습니다.

1. 이동 **도구** - **보안** - **사용자**
1. 기술 계정이 사용자 목록인지 확인하고 클릭합니다
1. 을(를) 클릭합니다. **그룹** 탭이 표시되어 사용자가 제품 프로필에 해당하는 그룹의 일부인지 확인합니다. 또한 이 사용자는 기여자를 포함한 소수의 다른 그룹의 구성원입니다.

   ![그룹 멤버십](/help/implementing/developing/introduction/assets/s2s-groupmembership.png)

>[!NOTE]
>
>2023년 중반 전에 여러 자격 증명을 만들 수 있기 전에 고객이 Adobe 관리 콘솔에서 제품 프로필을 만들도록 안내되지 않았으므로 기술 계정이 AEM as a Cloud Service 인스턴스의 &quot;기여자&quot;가 아닌 그룹과 연결되어 있지 않았습니다. 일관성을 위해 이 기술 계정의 경우 위에 설명된 대로 Adobe Admin Console에서 새 제품 프로필을 만들고 기존 기술 계정을 해당 그룹에 추가하는 것이 좋습니다.

<u>**적절한 그룹 권한 설정**</u>

마지막으로 API를 적절히 호출하거나 잠그기 위해 필요한 적절한 권한으로 그룹을 구성합니다. 다음을 통해 이 작업을 수행할 수 있습니다.

1. 적절한 작성자 인스턴스에 로그인하고 다음 **설정** - **보안** - **권한**
1. 왼쪽 창에서 제품 프로필에 해당하는 그룹 이름(이 경우 읽기 전용 API)을 검색하고 클릭합니다.

   ![그룹 검색](/help/implementing/developing/introduction/assets/s2s-searchforgroup.png)

1. 다음 창에서 편집 단추를 클릭합니다.

   ![권한 편집](/help/implementing/developing/introduction/assets/s2s-editpermissions.png) 

1. 권한을 적절하게 수정하고 를 클릭합니다 **저장**

   ![권한 편집 확인](/help/implementing/developing/introduction/assets/s2s-confirmeditpermissions.png)

>[!INFO]
>
>IMS(Identity Management System) 및 AEM 사용자 및 그룹에 대한 자세한 내용은 [설명서](/help/security/ims-support.md).

## 개발자 흐름 {#developer-flow}

개발자는 개발 AEM as a Cloud Service 개발 환경에 요청을 하는 AEM이 아닌 애플리케이션(랩탑에서 실행 또는 호스팅)의 개발 인스턴스를 사용하여 테스트하려고 할 수 있습니다. 그러나 개발자에게 반드시 IMS 관리자 역할 권한이 없으므로 일반 서버 간 플로우에 설명된 JWT 전달자를 생성할 수 있다고 간주할 수 없습니다. 따라서 Adobe는 개발자가 액세스 권한이 있는 AEM as a Cloud Service 환경에 대한 요청에 사용할 수 있는 액세스 토큰을 직접 생성하는 메커니즘을 제공합니다.

자세한 내용은 [개발자 지침 설명서](/help/implementing/developing/introduction/development-guidelines.md#crxde-lite-and-developer-console) AEM as a Cloud Service 개발자 콘솔을 사용하는 데 필요한 권한에 대한 정보를 제공합니다.

>[!NOTE]
>
>로컬 개발 액세스 토큰은 동일한 방법으로 재생성해야 하는 후 최대 24시간 동안 유효합니다.

개발자는 이 토큰을 사용하여 AEM이 아닌 테스트 애플리케이션에서 AEM as a Cloud Service 환경으로 호출할 수 있습니다. 일반적으로 개발자는 자체 랩탑에서 비 AEM 애플리케이션과 함께 이 토큰을 사용합니다. 또한 AEM as a Cloud는 일반적으로 비프로덕션 환경입니다.

개발자 플로우에는 다음 단계가 포함됩니다.

* 개발자 콘솔에서 액세스 토큰 생성
* 액세스 토큰을 사용하여 AEM 애플리케이션을 호출합니다.

개발자는 로컬 시스템에서 실행 중인 AEM 프로젝트에 API를 호출할 수도 있습니다. 이 경우 액세스 토큰이 필요하지 않습니다.

### 액세스 토큰 생성 {#generating-the-access-token}

1. 로 이동합니다. **로컬 토큰** 아래에 **통합**
1. 을(를) 클릭합니다. **로컬 개발 토큰 가져오기** 액세스 토큰을 생성하기 위한 개발자 콘솔에서 단추를 클릭합니다.

### 액세스 토큰을 사용하여 AEM 애플리케이션 호출 {#call-the-aem-application-with-an-access-token}

헤더에 액세스 토큰을 포함하여 비 AEM 애플리케이션에서 AEM as a Cloud Service 환경으로 적절한 서버 간 API 호출을 하십시오. 따라서 &quot;Authorization&quot; 헤더에 대해 값을 사용합니다 `"Bearer <access_token>"`.

## 자격 증명 새로 고침 {#refresh-credentials}

기본적으로, AEM as a Cloud Service 자격 증명은 1년 후에 만료됩니다. 서비스 연속성을 보장하기 위해 개발자는 자격 증명을 새로 고칠 수 있는 옵션을 제공하여 1년 더 가용성을 연장할 수 있습니다.

이를 위해 다음을 수행할 수 있습니다.

* 를 사용하십시오 **인증서 추가** 버튼 아래 **통합** - **기술 계정** 아래에 표시된 대로 개발자 콘솔에서

   ![자격 증명 새로 고침](/help/implementing/developing/introduction/assets/s2s-credentialrefresh.png)

* 단추를 누르면 새 인증서가 포함된 자격 증명 세트가 생성됩니다. 오프 AEM 서버에 새 자격 증명을 설치하고 이전 자격 증명을 제거하지 않고 연결이 예상대로 작동하는지 확인합니다 
* 액세스 토큰을 생성할 때 새 자격 증명이 이전 자격 증명 대신 사용되는지 확인하십시오
* 선택적으로 이전 인증서를 취소(및 삭제)하여 더 이상 AEM as a Cloud Service으로 인증하는 데 사용할 수 없습니다.

## 자격 증명 해지 {#credentials-revocation}

개인 키가 손상되면 새 인증서와 새 개인 키로 자격 증명을 만들어야 합니다. 응용 프로그램에서 새 자격 증명을 사용하여 액세스 토큰을 생성한 후 이전 인증서를 취소하고 삭제할 수 있습니다.

다음 단계를 따라 이 작업을 수행할 수 있습니다.

1. 먼저 새 키를 추가합니다. 이렇게 하면 새 개인 키와 새 인증서가 있는 자격 증명이 생성됩니다. 새 개인 키가 UI에 **현재** 따라서 앞으로 이 기술 계정의 모든 새 자격 증명에 사용됩니다. 기존 개인 키와 연결된 자격 증명은 해지될 때까지 계속 유효합니다. 이를 위해서는 세 점(**...**)을 클릭하여 현재 기술 계정을 사용하고 **새 개인 키 추가**:

   ![새 개인 키 추가](/help/implementing/developing/introduction/assets/s2s-addnewprivatekey.png)

1. 누르기 **추가** 프롬프트에 다음을 수행합니다.

   ![새 개인 키 추가 확인](/help/implementing/developing/introduction/assets/s2s-addprivatekeyconfirm.png)

   새 도메인으로 새 찾아보기 탭이 열리고 UI가 업데이트되어 개인 키가 모두 표시되고 새 개인 키가 로 표시됩니다 **현재**:

   ![UI의 개인 키](/help/implementing/developing/introduction/assets/s2s-twokeys.png)

1. 비 AEM 서버에 새 자격 증명을 설치하고 연결이 예상대로 작동하는지 확인합니다. 자세한 내용은 [서버 간 흐름 섹션](#the-server-to-server-flow) 방법
1. 이전 인증서를 취소합니다. 세 점(**...**)을 클릭하여 인증서 오른쪽의 **취소**:

   ![인증서 해지](/help/implementing/developing/introduction/assets/s2s-revokecert.png)

   그런 다음 을 눌러 다음 프롬프트에서 취소를 확인합니다 **취소** 버튼:

   ![인증서 확인 취소](/help/implementing/developing/introduction/assets/s2s-revokecertificateconfirmation.png)

1. 마지막으로 손상된 인증서를 삭제합니다.
