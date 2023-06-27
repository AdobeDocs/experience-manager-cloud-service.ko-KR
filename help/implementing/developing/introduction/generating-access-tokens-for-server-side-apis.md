---
title: 서버측 API용 액세스 토큰 생성
description: 보안 JWT 토큰을 생성하여 타사 서버와 AEM as a Cloud Service 간의 통신을 용이하게 하는 방법에 대해 알아봅니다
exl-id: 20deaf8f-328e-4cbf-ac68-0a6dd4ebf0c9
source-git-commit: d361ddc9a50a543cd1d5f260c09920c5a9d6d675
workflow-type: tm+mt
source-wordcount: '2090'
ht-degree: 0%

---

# 서버측 API용 액세스 토큰 생성 {#generating-access-tokens-for-server-side-apis}

일부 아키텍처는 AEM 인프라 외부의 서버에 호스팅된 애플리케이션에서 AEM을 as a Cloud Service으로 호출하는 데 의존합니다. AEM 예를 들어, 서버를 호출한 다음 API를 as a Cloud Service으로 요청하는 모바일 애플리케이션입니다.

개발을 위한 간소화된 흐름과 함께 서버 간 흐름이 아래에 설명되어 있습니다. 더 AEM as a Cloud Service [개발자 콘솔](development-guidelines.md#crxde-lite-and-developer-console) 은 인증 프로세스에 필요한 토큰을 생성하는 데 사용됩니다.

<!-- Alexandru: hiding this until the tutorials reflect the new UI

>[!NOTE]
>
>In addition to this documentation, you can also consult the tutorials on [Token-based authentication for AEM as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/authentication/overview.html?lang=en#authentication) and [Getting a Login Token for Integrations](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-5/cloud5-getting-login-token-integrations.html). -->

## 서버 간 흐름 {#the-server-to-server-flow}

AEM 작성자의 AEM 사용자 또는 AEM 관리자 제품 프로필 멤버인 IMS 조직 관리자 역할이 있는 사용자는 AEM as a Cloud Service에서 자격 증명 세트를 생성할 수 있습니다. 각 자격 증명은 인증서(공개 키), 개인 키 및 `clientId` 및 `clientSecret`. 이러한 자격 증명은 나중에 AEM as a Cloud Service 환경 관리자 역할이 있는 사용자가 검색할 수 있으며 비 AEM 서버에 설치하고 보안 키로 주의 깊게 처리해야 합니다. 이 JSON 형식 파일에는 AEM as a Cloud Service API와 통합하는 데 필요한 모든 데이터가 포함되어 있습니다. 이 데이터는 서명된 JWT 토큰을 생성하는 데 사용되며, IMS(Identity Management 서비스) Adobe과 IMS 액세스 토큰으로 교환됩니다. 그런 다음 이 액세스 토큰을 Bearer 인증 토큰으로 사용하여 AEM에 as a Cloud Service으로 요청할 수 있습니다. 자격 증명의 인증서는 기본적으로 1년 후에 만료되지만, 설명된 대로 필요할 때 새로 고칠 수 있습니다 [여기](#refresh-credentials).

서버 간 흐름에는 다음 단계가 포함됩니다.

* AEM Developer Console에서 as a Cloud Service으로 자격 증명 가져오기
* AEM을 호출하는 비 AEM 서버에 AEMas a Cloud Service 용 자격 증명을 설치합니다.
* JWT 토큰을 생성하고 Adobe의 IMS API를 사용하여 해당 토큰을 액세스 토큰으로 교환
* 액세스 토큰을 전달자 인증 토큰으로 사용하여 AEM API 호출
* AEM 환경에서 기술 계정 사용자에 대한 적절한 권한 설정

### AEM as a Cloud Service 자격 증명 가져오기 {#fetch-the-aem-as-a-cloud-service-credentials}

AEM as a Cloud Service 개발자 콘솔에 대한 액세스 권한이 있는 사용자는 Developer Console의 통합 탭에서 주어진 환경을 볼 수 있습니다. AEM as a Cloud Service 환경 관리자 역할이 있는 사용자는 자격 증명을 만들거나 보거나 관리할 수 있습니다.

클릭 **새 기술 계정 만들기**, 클라이언트 id, 클라이언트 암호, 개인 키, 인증서 및 pod 선택에 관계없이 환경의 작성자 및 게시 계층에 대한 구성을 포함하는 자격 증명 세트가 만들어집니다.

![새 기술 계정 만들기](/help/implementing/developing/introduction/assets/s2s-createtechaccount.png)

새 브라우저 탭이 열리고 자격 증명이 표시됩니다. 이 보기를 사용하여 상태 제목 옆에 있는 다운로드 아이콘을 눌러 자격 증명을 다운로드할 수 있습니다.

![자격 증명 다운로드](/help/implementing/developing/introduction/assets/s2s-credentialdownload.png)

자격 증명이 만들어지면 아래에 표시됩니다. **기술 계정** 의 탭 **통합** 섹션:

![자격 증명 보기](/help/implementing/developing/introduction/assets/s2s-viewcredentials.png)

사용자는 나중에 보기 작업을 사용하여 자격 증명을 볼 수 있습니다. 또한 이 문서의 뒷부분에 설명된 대로 사용자는 동일한 기술 계정에 대한 자격 증명을 편집할 수 있습니다. 인증서를 갱신하거나 취소해야 하는 경우에 대해 새 개인 키 또는 인증서를 만들어 이러한 편집을 수행합니다.

AEM as a Cloud Service 환경 관리자 역할이 있는 사용자는 나중에 추가 기술 계정에 대한 자격 증명을 만들 수 있습니다. 이 기능은 API마다 액세스 요구 사항이 다를 때 유용합니다. 예를 들어 읽기 및 읽기/쓰기가 있습니다.

>[!NOTE]
>
>고객은 이미 삭제된 계정을 포함하여 최대 10개의 기술 계정을 만들 수 있습니다.

>[!IMPORTANT]
>
>AEM 작성자의 AEM 사용자 또는 AEM 관리자 제품 프로필 의 멤버이기도 한 IMS 조직 관리자(일반적으로 Cloud Manager를 통해 환경을 프로비저닝한 동일한 사용자)는 먼저 Developer Console에 액세스해야 합니다. 그런 다음 을 클릭합니다. **새 기술 계정 만들기** AEM as a Cloud Service 환경에 대한 관리자 권한이 있는 사용자가 자격 증명을 생성하고 나중에 검색할 수 있도록 해 줍니다. IMS 조직 관리자가 아직 기술 계정을 만들지 않은 경우 IMS 조직 관리자 역할이 필요하다는 메시지가 표시됩니다.

### 비 AEM 서버에 AEM 서비스 자격 증명 설치 {#install-the-aem-service-credentials-on-a-non-aem-server}

AEMAEM 을 호출하는 애플리케이션은 as a Cloud Service으로 자격 증명에 액세스하여 이를 비밀로 취급할 수 있어야 합니다.

### JWT 토큰을 생성하고 액세스 토큰으로 교환 {#generate-a-jwt-token-and-exchange-it-for-an-access-token}

자격 증명을 사용하여 24시간 동안 유효한 액세스 토큰을 검색하기 위해 Adobe의 IMS 서비스 호출에 JWT 토큰을 생성합니다.

AEM CS 서비스 자격 증명은 이를 위해 설계된 클라이언트 라이브러리를 사용하여 액세스 토큰으로 교환될 수 있습니다. 클라이언트 라이브러리는 다음에서 사용할 수 있습니다. [Adobe의 공개 GitHub 저장소](https://github.com/adobe/aemcs-api-client-lib): 더 자세한 지침과 최신 정보가 포함되어 있습니다.

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

올바른 형식으로 서명된 JWT 토큰을 생성하고 IMS 토큰 교환 API를 호출할 수 있는 모든 언어에서 동일한 교환을 수행할 수 있습니다.

액세스 토큰은 만료되는 시점을 정의하며, 일반적으로 24시간입니다. git 저장소에는 액세스 토큰을 관리하고 만료되기 전에 새로 고치는 샘플 코드가 있습니다.

>[!NOTE]
>자격 증명이 여러 개 있는 경우 나중에 호출되는 AEM에 대한 API 호출에 적절한 json 파일을 참조해야 합니다.

### AEM API 호출 {#calling-the-aem-api}

헤더의 액세스 토큰을 포함하여 AEM as a Cloud Service 환경에 대한 적절한 서버 간 API 호출을 수행합니다. 따라서 &quot;Authorization&quot; 헤더에 값을 사용합니다. `"Bearer <access_token>"`. 예를 들어 `curl`:

```curlc
curl -H "Authorization: Bearer <your_ims_access_token>" https://author-p123123-e23423423.adobeaemcloud.com/content/dam.json
```

### AEM에서 기술 계정 사용자에 대한 적절한 권한 설정 {#set-the-appropriate-permissions-for-the-technical-account-user-in-aem}

먼저 Adobe Admin Console에서 새 제품 프로필을 만들어야 합니다.

1. Adobe Admin Console으로 이동 [https://adminconsole.adobe.com/](https://adminconsole.adobe.com/).
1. 누르기 **관리** 링크: **제품 및 서비스** 왼쪽 열입니다.
1. 선택 **AEM as a Cloud Service**.
1. 누르기 **새 프로필** 단추를 클릭합니다.

   ![새 프로필](/help/implementing/developing/introduction/assets/s2s-newproductprofile.png)

1. 프로필 이름을 지정하고 키를 누릅니다 **저장**.

   ![프로필 저장](/help/implementing/developing/introduction/assets/s2s-saveprofile.png)

1. 프로파일 목록에서 생성한 프로파일을 선택합니다.
1. 선택 **사용자 추가**.

   ![사용자 추가](/help/implementing/developing/introduction/assets/s2s-addusers.png)

1. 만든 기술 계정(이 경우) 추가 `84b2c3a2-d60a-40dc-84cb-e16b786c1673@techacct.adobe.com`), 클릭 **저장**.

   ![기술 계정 추가](/help/implementing/developing/introduction/assets/s2s-addtechaccount.png)

1. 변경 사항이 적용될 때까지 10분 동안 기다렸다가 새 자격 증명에서 생성된 액세스 토큰으로 AEM에 대한 API를 호출합니다. cURL 명령으로는 다음 예와 유사하게 표시됩니다.

   `curl -H "Authorization: Bearer <access_token>" https://author-pXXXXX-eXXXXX.adobeaemcloud.net/content/dam.json `


API를 호출하면 제품 프로필이 AEM as a Cloud Service 작성자 인스턴스에 사용자 그룹으로 표시되고 적절한 기술 계정이 해당 그룹의 멤버로 표시됩니다.

이 정보를 확인하려면 다음을 수행하십시오.

1. 작성자 인스턴스에 로그온합니다.
1. 다음으로 이동 **도구** > **보안**&#x200B;을(를) 클릭하고 **그룹** 카드.
1. 그룹 목록에서 생성한 프로필의 이름을 찾아 클릭합니다.

   ![그룹 프로필](/help/implementing/developing/introduction/assets/s2s-groupprofile.png)

1. 다음 창에서 로 전환합니다 **구성원** 기술 계정이 다음 탭에 올바르게 나열되어 있는지 확인합니다.

   ![구성원 탭](/help/implementing/developing/introduction/assets/s2s-techaccountmembers.png)


또는 작성자 인스턴스에서 아래 단계를 수행하여 사용자 목록에 기술 계정이 표시되는지 확인할 수도 있습니다.

1. 다음으로 이동 **도구** > **보안** > **사용자**.
1. 기술 계정이 사용자 목록인지 확인하고 선택합니다.
1. 다음을 클릭합니다. **그룹** 탭으로 이동하여 사용자가 제품 프로필에 해당하는 그룹의 일부인지 확인할 수 있습니다. 이 사용자는 기여자를 포함하여 소수의 다른 그룹에도 속합니다.

   ![그룹 멤버십](/help/implementing/developing/introduction/assets/s2s-groupmembership.png)

>[!NOTE]
>
>2023년 중반 이전에는 여러 자격 증명을 만들 수 있었지만 Adobe Admin Console에서 제품 프로필을 만들도록 고객에게 안내되지 않았습니다. 따라서 기술 계정은 AEM as a Cloud Service 인스턴스의 &quot;기여자&quot; 이외의 그룹과 연결되지 않았습니다. 일관성을 위해 이 기술 계정의 경우 위에서 설명한 대로 Adobe Admin Console에서 제품 프로필을 만들고 기존 기술 계정을 해당 그룹에 추가하는 것이 좋습니다.

<u>**적절한 그룹 권한 설정**</u>

마지막으로, API를 적절하게 호출하거나 잠글 수 있도록 필요한 적절한 권한으로 그룹을 구성합니다.

1. 적절한 작성자 인스턴스에 로그온하여 다음으로 이동합니다. **설정** > **보안** > **권한**
1. 왼쪽 창에서 제품 프로필에 해당하는 그룹의 이름(이 경우 읽기 전용 API)을 검색하고 선택합니다.

   ![그룹 검색](/help/implementing/developing/introduction/assets/s2s-searchforgroup.png)

1. 다음 창에서 편집 단추를 클릭합니다.

   ![권한 편집](/help/implementing/developing/introduction/assets/s2s-editpermissions.png) 

1. 권한을 적절하게 수정하고 **저장**

   ![권한 편집 확인](/help/implementing/developing/introduction/assets/s2s-confirmeditpermissions.png)

>[!INFO]
>
>Adobe IMS(Identity Management System) 및 AEM 사용자 및 그룹에 대해 자세히 알아보십시오. 다음을 참조하십시오. [설명서](/help/security/ims-support.md).

## 개발자 흐름 {#developer-flow}

개발자는 개발 AEM as a Cloud Service 개발 환경에 대한 요청을 수행하는 비 AEM 애플리케이션의 개발 인스턴스(랩톱에서 실행되거나 호스팅됨)를 사용하여 테스트하려고 할 수 있습니다. 그러나 개발자에게 반드시 IMS 관리자 역할 권한이 있는 것은 아니기 때문에 Adobe은 일반 서버 간 흐름에서 설명한 JWT 전달자를 생성할 수 있다고 간주할 수 없습니다. 따라서 Adobe은 개발자가 액세스 권한이 있는 AEMas a Cloud Service 의 환경에 대한 요청에 사용할 수 있는 액세스 토큰을 직접 생성하는 메커니즘을 제공합니다.

다음을 참조하십시오. [개발자 가이드라인 설명서](/help/implementing/developing/introduction/development-guidelines.md#crxde-lite-and-developer-console) AEM as a Cloud Service 개발자 콘솔을 사용하는 데 필요한 권한에 대한 자세한 내용을 보려면 여기를 클릭하십시오.

>[!NOTE]
>
>로컬 개발 액세스 토큰은 최대 24시간 동안 유효하며, 그 후에는 동일한 방법을 사용하여 다시 생성해야 합니다.

개발자는 이 토큰을 사용하여 비 AEM AEM 테스트 애플리케이션에서 as a Cloud Service 환경으로 호출할 수 있습니다. 일반적으로 개발자는 랩톱에서 비 AEM 애플리케이션과 함께 이 토큰을 사용합니다. 또한 AEM as a Cloud는 일반적으로 비프로덕션 환경입니다.

개발자 플로우에는 다음 단계가 포함됩니다.

* Developer Console에서 액세스 토큰 생성
* 액세스 토큰을 사용하여 AEM 애플리케이션을 호출합니다.

개발자는 로컬 컴퓨터에서 실행 중인 AEM 프로젝트에 API를 호출할 수도 있습니다. 이 경우 액세스 토큰이 필요하지 않습니다.

### 액세스 토큰 생성 {#generating-the-access-token}

1. 로 이동 **로컬 토큰** 아래에 **통합**
1. 클릭 **로컬 개발 토큰 가져오기** 액세스 토큰을 생성할 수 있도록 Developer Console에서 를 참조하십시오.

### 액세스 토큰으로 AEM 애플리케이션 호출 {#call-the-aem-application-with-an-access-token}

헤더에서 액세스 토큰을 포함하여 비 AEM 애플리케이션에서 AEM as a Cloud Service 환경으로 서버 간 API를 적절하게 호출합니다. 따라서 &quot;Authorization&quot; 헤더에 값을 사용합니다. `"Bearer <access_token>"`.

## 자격 증명 새로 고침 {#refresh-credentials}

기본적으로 AEM의 자격 증명은 1년 후에 as a Cloud Service으로 만료됩니다. 서비스 연속성을 보장하기 위해 개발자는 자격 증명을 새로 고치고 1년 동안 가용성을 확장할 수 있습니다.

이 새로 고침 확장을 수행하려면 다음을 수행합니다.

* 사용 **인증서 추가** 아래에 있는 단추 **통합** - **기술 계정** 아래 표시된 대로 Developer Console에서

  ![자격 증명 새로 고침](/help/implementing/developing/introduction/assets/s2s-credentialrefresh.png)

* 버튼을 누르면 새 인증서를 포함하는 자격 증명 세트가 생성됩니다. 오프 AEM 서버에 새 자격 증명을 설치하고 이전 자격 증명을 제거하지 않고 연결이 예상대로 이루어지도록 하십시오.
* 액세스 토큰을 생성할 때 이전 자격 증명 대신 새 자격 증명을 사용해야 합니다.
* 필요한 경우 AEM as a Cloud Service으로 인증하는 데 더 이상 사용할 수 없도록 이전 인증서를 취소(및 삭제)합니다.

## 자격 증명 해지 {#credentials-revocation}

개인 키가 손상된 경우 새 인증서와 새 개인 키로 자격 증명을 만들어야 합니다. 액세스 토큰을 생성할 수 있도록 애플리케이션이 새 자격 증명을 사용한 후 다음을 수행하여 이전 인증서를 취소하고 삭제할 수 있습니다.

1. 먼저 새 키를 추가합니다. 이 키는 새 개인 키 및 새 인증서를 사용하여 자격 증명을 생성합니다. 새 개인 키가 사용자 인터페이스에 다음과 같이 표시됩니다. **현재** 따라서 앞으로 이 기술 계정의 모든 새 자격 증명에 사용됩니다. 이전 개인 키와 연결된 자격 증명은 해지될 때까지 계속 유효합니다. 이 취소를 수행하려면 세 점(**...**)을 클릭하여 현재 기술 계정에서 **새 개인 키 추가**:

   ![새 개인 키 추가](/help/implementing/developing/introduction/assets/s2s-addnewprivatekey.png)

1. 선택 **추가** 다음 프롬프트에서:

   ![새 개인 키 추가 확인](/help/implementing/developing/introduction/assets/s2s-addprivatekeyconfirm.png)

   새 자격 증명이 포함된 새 찾아보기 탭이 열리고 사용자 인터페이스가 새 개인 키가 로 표시된 두 개인 키를 모두 표시하도록 업데이트됩니다. **현재**:

   ![UI의 개인 키](/help/implementing/developing/introduction/assets/s2s-twokeys.png)

1. 비 AEM 서버에 새 자격 증명을 설치하고 연결이 예상대로 작동하는지 확인합니다. 다음을 참조하십시오 [서버 간 흐름 섹션](#the-server-to-server-flow) 을 참조하십시오.
1. 세 점을 선택하여 이전 인증서 취소(**...**) 인증서 오른쪽에서 다음을 선택합니다. **취소**:

   ![인증서 취소](/help/implementing/developing/introduction/assets/s2s-revokecert.png)

   그런 다음 을 눌러 다음 프롬프트에서 취소를 확인합니다 **취소** 단추:

   ![인증서 취소 확인](/help/implementing/developing/introduction/assets/s2s-revokecertificateconfirmation.png)

1. 마지막으로 손상된 인증서를 삭제합니다.
