---
title: 서버 측 API용 액세스 토큰 생성(기존)
description: 보안 JWT 토큰을 생성하여 타사 서버와 AEM as a Cloud Service 간의 통신을 용이하게 하는 방법을 알아봅니다
hidefromtoc: true
exl-id: 6561870c-cbfe-40ef-9efc-ea75c88c4ed7
feature: Developing
role: Admin, Architect, Developer
source-git-commit: 22216d2c045b79b7da13f09ecbe1d56a91f604df
workflow-type: tm+mt
source-wordcount: '1382'
ht-degree: 0%

---

# 서버 측 API용 액세스 토큰 생성(기존) {#generating-access-tokens-for-server-side-apis-legacy}

일부 아키텍처는 AEM 인프라 외부의 서버에 호스팅된 애플리케이션에서 AEM as a Cloud Service을 호출하는 데 의존합니다. 예를 들어, 서버를 호출한 다음 AEM as a Cloud Service에 API 요청을 수행하는 모바일 애플리케이션입니다.

개발을 위한 간소화된 흐름과 함께 서버 간 흐름이 아래에 설명되어 있습니다. AEM as a Cloud Service [Developer Console](development-guidelines.md#crxde-lite-and-developer-console)을(를) 사용하여 인증 프로세스에 필요한 토큰을 생성합니다.

<!-- ERROR: Not Found (HTTP error 404)
>[!NOTE]
>
>In addition to this documentation, you can also consult the tutorials on [Token-based authentication for AEM as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/authentication/overview.html?lang=ko#authentication) and [Getting a Login Token for Integrations](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-5/cloud5-getting-login-token-integrations.html). -->

## 서버 간 흐름 {#the-server-to-server-flow}

IMS 조직 관리자 역할이 있고 AEM 작성자의 AEM 사용자 또는 AEM 관리자 제품 프로필 멤버인 사용자는 AEM as a Cloud Service 자격 증명을 생성할 수 있습니다. 이 자격 증명은 나중에 AEM as a Cloud Service 환경 관리자 역할이 있는 사용자가 검색할 수 있으며 서버에 설치해야 하며, 비밀 키로 주의 깊게 처리해야 합니다. 이 JSON 형식 파일에는 AEM as a Cloud Service API와 통합하는 데 필요한 모든 데이터가 포함되어 있습니다. 이 데이터는 IMS 액세스 토큰으로 IMS와 교환되는 서명된 JWT 토큰을 생성하는 데 사용됩니다. 그런 다음 이 액세스 토큰을 전달자 인증 토큰으로 사용하여 AEM as a Cloud Service에 요청할 수 있습니다. 자격 증명은 기본적으로 1년 후에 만료되지만 필요한 경우 새로 고칠 수 있습니다. [자격 증명 새로 고침](#refresh-credentials)을 참조하세요.

서버 간 흐름에는 다음 단계가 포함됩니다.

* Developer Console에서 AEM as a Cloud Service에 대한 자격 증명 가져오기
* AEM을 호출하는 AEM이 아닌 서버에 AEM as a Cloud Service에 대한 자격 증명을 설치합니다.
* JWT 토큰을 생성하고 Adobe의 IMS API를 사용하여 해당 토큰을 액세스 토큰으로 교환
* 액세스 토큰을 전달자 인증 토큰으로 사용하여 AEM API 호출
* AEM 환경에서 기술 계정 사용자에 대한 적절한 권한을 설정합니다

### AEM as a Cloud Service 자격 증명 가져오기 {#fetch-the-aem-as-a-cloud-service-credentials}

AEM as a Cloud Service 개발자 콘솔에 액세스할 수 있는 사용자에게는 주어진 환경에 대한 Developer Console의 통합 탭과 두 개의 버튼이 표시됩니다. AEM as a Cloud Service 환경 관리자 역할이 있는 사용자는 **서비스 자격 증명 생성** 단추를 클릭하여 서비스 자격 증명 json을 생성하고 표시할 수 있습니다. JSON에는 Pod 선택에 관계없이 클라이언트 ID, 클라이언트 암호, 개인 키, 인증서 및 환경의 작성자 및 게시 계층에 대한 구성을 포함하여 AEM이 아닌 서버에 필요한 모든 정보가 포함되어 있습니다.

![JWT 생성](assets/JWTtoken3.png)

출력은 다음과 유사합니다.

```
{
  "ok": true,
  "integration": {
    "imsEndpoint": "ims-na1.adobelogin.com",
    "metascopes": "ent_aem_cloud_sdk,ent_cloudmgr_sdk",
    "technicalAccount": {
      "clientId": "cm-p123-e1234",
      "clientSecret": "4AREDACTED17"
    },
    "email": "abcd@techacct.adobe.com",
    "id": "ABCDAE10A495E8C@techacct.adobe.com",
    "org": "1234@AdobeOrg",
    "privateKey": "-----BEGIN RSA PRIVATE KEY-----\r\REDACTED\r\n==\r\n-----END RSA PRIVATE KEY-----\r\n",
    "publicKey": "-----BEGIN CERTIFICATE-----\r\nREDACTED\r\n-----END CERTIFICATE-----\r\n"
  },
  "statusCode": 200
}
```

생성되면 나중에 같은 위치에서 **서비스 자격 증명 가져오기** 단추를 눌러 자격 증명을 검색할 수 있습니다.

>[!IMPORTANT]
>
>IMS 조직 관리자(일반적으로 Cloud Manager을 통해 환경을 프로비저닝한 사용자)는 AEM 작성자의 AEM 사용자 또는 AEM 관리자 제품 프로필에도 속해야 하며 Developer Console에 액세스합니다. 그런 다음 **서비스 자격 증명 생성** 단추를 클릭해야 자격 증명이 생성되고 나중에 AEM as a Cloud Service 환경에 대한 관리자 권한이 있는 사용자가 자격 증명을 검색할 수 있습니다. IMS 조직 관리자가 이 작업을 수행하지 않은 경우 IMS 조직 관리자 역할이 필요하다는 메시지가 표시됩니다.

### 비 AEM 서버에 AEM 서비스 자격 증명 설치 {#install-the-aem-service-credentials-on-a-non-aem-server}

AEM을 호출하는 AEM 이외의 애플리케이션은 AEM as a Cloud Service의 자격 증명에 액세스하여 이를 비밀로 취급할 수 있어야 합니다.

### JWT 토큰을 생성하고 액세스 토큰으로 교환 {#generate-a-jwt-token-and-exchange-it-for-an-access-token}

자격 증명을 사용하여 Adobe의 IMS 서비스 호출에서 24시간 동안 유효한 액세스 토큰을 검색하는 JWT 토큰을 만듭니다.

AEM CS 서비스 자격 증명은 이를 위해 설계된 코드 샘플을 사용하여 액세스 토큰으로 교환될 수 있습니다. 샘플 코드는 [Adobe의 공용 GitHub 저장소](https://github.com/adobe/aemcs-api-client-lib)에서 사용할 수 있으며, 여기에는 자체 프로젝트에 맞게 복사하고 조정할 수 있는 코드 예제가 포함되어 있습니다. 이 저장소에는 참조용 샘플 코드가 포함되어 있으며 프로덕션 준비 라이브러리 종속성으로 유지 관리되지 않습니다.

```
/*jshint node:true */
"use strict";

const fs = require('fs');
// Sample code adapted from Adobe's GitHub repository
const exchange = require("./your-local-aemcs-client"); // Copy and adapt the code from the GitHub repository

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

### AEM API 호출 {#calling-the-aem-api}

헤더에 액세스 토큰을 포함하여 AEM as a Cloud Service 환경에 대한 적절한 서버 간 API를 호출합니다. 따라서 &quot;Authorization&quot; 헤더에 값 `"Bearer <access_token>"`을(를) 사용합니다. 예를 들어 `curl`을(를) 사용하는 경우:

```curlc
curl -H "Authorization: Bearer <your_ims_access_token>" https://author-p123123-e23423423.adobeaemcloud.com/content/dam.json
```

### AEM에서 기술 계정 사용자에 대한 적절한 권한 설정 {#set-the-appropriate-permissions-for-the-technical-account-user-in-aem}

AEM에서 기술 계정 사용자가 만들어지면(해당 액세스 토큰을 사용하여 첫 번째 요청 후 발생) 기술 계정 사용자에게 **in** AEM의 권한이 올바르게 부여되어야 합니다.

기본적으로 AEM 작성자 서비스에서는 기술 계정 사용자가 읽기 액세스 AEM을 제공하는 기여자 사용자 그룹에 추가됩니다.

AEM의 이 기술 계정 사용자에게 일반적인 방법을 사용하여 권한을 추가로 제공할 수 있습니다.

## 개발자 흐름 {#developer-flow}

개발자는 개발 AEM as a Cloud Service 개발 환경을 요청하는 비 AEM 애플리케이션(랩톱에서 실행되거나 호스팅됨)의 개발 인스턴스를 사용하여 테스트해야 합니다. 그러나 개발자에게 반드시 IMS 관리자 역할 권한이 있는 것은 아니기 때문에 Adobe은 일반 서버 간 흐름에서 설명한 JWT 전달자를 생성할 수 있다고 간주할 수 없습니다. 따라서 Adobe은 개발자가 액세스 권한이 있는 AEM as a Cloud Service 환경에 대한 요청에 사용할 수 있는 액세스 토큰을 직접 생성하는 메커니즘을 제공합니다.

AEM as a Cloud Service 개발자 콘솔을 사용하는 데 필요한 권한에 대한 자세한 내용은 [개발자 지침 설명서](/help/implementing/developing/introduction/development-guidelines.md#crxde-lite-and-developer-console)를 참조하십시오.

>[!NOTE]
>
>로컬 개발 액세스 토큰은 최대 24시간 동안 유효하며, 그 후에는 동일한 방법을 사용하여 다시 생성해야 합니다.

개발자는 이 토큰을 사용하여 비 AEM 테스트 애플리케이션에서 AEM as a Cloud Service 환경으로 호출할 수 있습니다. 일반적으로 개발자는 랩톱에서 비 AEM 애플리케이션과 함께 이 토큰을 사용합니다. 또한 AEM as a Cloud는 일반적으로 비프로덕션 환경입니다.

개발자 플로우에는 다음 단계가 포함됩니다.

* Developer Console에서 액세스 토큰 생성
* 액세스 토큰을 사용하여 AEM 애플리케이션을 호출합니다.

개발자는 로컬 컴퓨터에서 실행 중인 AEM 프로젝트에 대한 API를 호출할 수도 있습니다. 이 경우 액세스 토큰이 필요하지 않습니다.

### 액세스 토큰 생성 {#generating-the-access-token}

액세스 토큰을 생성하려면 Developer Console에서 **로컬 개발 토큰 가져오기**&#x200B;를 클릭하십시오.

### 그런 다음 액세스 토큰을 사용하여 AEM 애플리케이션 호출 {#call-the-aem-application-with-an-access-token}

헤더에 액세스 토큰을 포함하여 AEM이 아닌 애플리케이션에서 AEM as a Cloud Service 환경으로 적합한 서버 간 API를 호출합니다. 따라서 &quot;Authorization&quot; 헤더에 값 `"Bearer <access_token>"`을(를) 사용합니다.

## 자격 증명 새로 고침 {#refresh-credentials}

기본적으로 AEM as a Cloud Service의 자격 증명은 1년 후에 만료됩니다. 서비스 연속성을 보장하기 위해 개발자는 자격 증명을 새로 고치고 1년 동안 가용성을 확장할 수 있습니다. 아래와 같이 Developer Console의 **통합** 탭에서 **서비스 자격 증명 새로 고침**&#x200B;을 사용합니다.

![자격 증명 새로 고침](assets/credential-refresh.png)

버튼을 누르면 새 자격 증명 세트가 생성됩니다. 새 자격 증명으로 보안 저장소를 업데이트하고 보안 저장소가 제대로 작동하는지 확인할 수 있습니다.

>[!NOTE]
>
> **서비스 자격 증명 새로 고침** 단추를 클릭하면 이전 자격 증명이 만료되기 전까지 등록된 상태로 유지되지만, Developer Console에서는 언제든지 최신 설정만 볼 수 있습니다.

## 서비스 자격 증명 해지 {#service-credentials-revocation}

자격 증명을 취소해야 하는 경우 다음 단계를 사용하여 고객 지원 센터에 요청을 제출해야 합니다.

1. 사용자 인터페이스에서 Adobe Admin Console의 기술 계정 사용자를 비활성화합니다.
   * Cloud Manager에서 환경 옆에 있는 **..** 단추를 누릅니다. 이 작업을 수행하면 제품 프로필 페이지가 열립니다
   * 이제 **AEM 사용자** 프로필을 클릭하여 사용자 목록을 표시합니다
   * **API 자격 증명** 탭을 클릭한 다음 적절한 기술 계정 사용자를 찾아 삭제합니다
2. 고객 지원 센터에 문의하여 해당 특정 환경에 대한 서비스 자격 증명을 삭제하도록 요청하십시오
3. 마지막으로, 이 설명서에 설명된 대로 자격 증명을 다시 생성할 수 있습니다. 또한 새로 만든 기술 계정 사용자에게 적절한 권한이 있는지 확인하십시오.
