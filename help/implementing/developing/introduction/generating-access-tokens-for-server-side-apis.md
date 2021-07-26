---
title: 서버 측 API에 대한 액세스 토큰 생성
description: 보안 JWT 토큰을 생성하여 서드파티 서버와 AEM as a Cloud Service 간의 커뮤니케이션을 용이하게 하는 방법을 알아봅니다
exl-id: 20deaf8f-328e-4cbf-ac68-0a6dd4ebf0c9
source-git-commit: 89b43e14f35e18393ffab538483121c10f6b5a01
workflow-type: tm+mt
source-wordcount: '1250'
ht-degree: 0%

---

# 소개 {#introduction}

일부 아키텍처에서는 AEM 인프라 외부의 서버에 호스팅된 애플리케이션에서 AEM을 Cloud Service으로 호출하는 데 사용합니다. 예를 들어 서버를 호출한 다음 AEM에 Cloud Service으로 API 요청을 수행하는 모바일 애플리케이션입니다.

서버 간 흐름은 개발을 위한 간단한 흐름과 함께 아래에 설명되어 있습니다. AEM as a Cloud Service [개발자 콘솔](development-guidelines.md#crxde-lite-and-developer-console)은 인증 프로세스에 필요한 토큰을 생성하는 데 사용됩니다.

>[!NOTE]
>
>이 설명서 외에 AEM용 토큰 기반 인증인 [Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/authentication/overview.html?lang=en#authentication)에 대한 자습서를 참조할 수도 있습니다.

## 서버 간 흐름 {#the-server-to-server-flow}

IMS 조직 관리자 역할을 가진 사용자이며, AEM 작성자의 AEM 사용자 또는 AEM 관리자 제품 프로필 멤버이기도 한 사용자는 AEM을 Cloud Service 자격 증명으로 생성할 수 있습니다. 이러한 자격 증명은 나중에 AEM을 Cloud Service 환경 관리자 역할로 사용하는 사용자가 검색할 수 있으며 서버에 설치되어야 하며 보안 키로 신중하게 처리해야 합니다. 이 JSON 형식 파일에는 AEM as a Cloud Service API와 통합하는 데 필요한 모든 데이터가 포함되어 있습니다. 이 데이터는 IMS 액세스 토큰에 대해 IMS와 교환되는 서명된 JWT 토큰을 만드는 데 사용됩니다. 그런 다음 이 액세스 토큰을 베어러 인증 토큰으로 사용하여 AEM을 Cloud Service으로 요청할 수 있습니다.

서버 간 흐름에는 다음 단계가 포함됩니다.

* 개발자 콘솔에서 AEM을 Cloud Service 자격 증명으로 가져오기
* AEM을 호출하는 비 AEM 서버에 Cloud Service 자격 증명으로 AEM을 설치합니다
* JWT 토큰을 생성하고 Adobe의 IMS API를 사용하여 액세스 토큰에 대해 해당 토큰을 교환합니다
* 액세스 토큰을 사용하여 AEM API를 베어러 인증 토큰으로 호출
* AEM 환경에서 기술 계정 사용자에 대한 적절한 권한 설정

### AEM을 Cloud Service 자격 증명으로 가져오기 {#fetch-the-aem-as-a-cloud-service-credentials}

AEM as a Cloud Service 개발자 콘솔에 액세스할 수 있는 사용자는 지정된 환경에 대한 개발자 콘솔의 통합 탭 과 두 개의 버튼을 볼 수 있습니다. AEM as a Cloud Service Environment 관리자 역할을 사용하는 사용자는 **서비스 자격 증명 가져오기** 단추를 클릭하여 서비스 자격 증명 json을 표시할 수 있습니다. 이 JSON에는 Pod 선택 여부에 관계없이 환경의 작성자 및 게시 계층 구성을 포함하여 AEM 이외의 서버에 필요한 모든 정보가 포함됩니다. 클라이언트 ID, 클라이언트 암호, 개인 키, 인증서, 이 환경은 구성 및 게시 구성 등이 포함됩니다.

![JWT 생성](assets/JWTtoken3.png)

출력은 다음과 비슷합니다.

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

>[!IMPORTANT]
>
>IMS 조직 관리자(일반적으로 Cloud Manager를 통해 환경을 프로비저닝한 사용자)는 AEM 작성자의 AEM 사용자 또는 AEM 관리자 제품 프로필에 포함되어야 하며, 먼저 개발자 콘솔에 액세스한 다음 **서비스 자격 증명 가져오기** 단추를 클릭하여 자격 증명을 생성하고 나중에 Cloud Service 환경으로 AEM에 대한 관리자 권한이 있는 사용자가 자격 증명을 검색하도록 해야 합니다. IMS 조직 관리자가 이를 수행하지 않은 경우 IMS 조직 관리자 역할이 필요하다는 메시지가 표시됩니다.

### 비 AEM 서버에 AEM 서비스 자격 증명 설치 {#install-the-aem-service-credentials-on-a-non-aem-server}

AEM에 대한 호출을 하는 비 AEM 애플리케이션은 AEM을 Cloud Service 자격 증명으로 액세스하여 암호로 처리할 수 있어야 합니다.

### JWT 토큰을 생성하고 액세스 토큰으로 교환합니다{#generate-a-jwt-token-and-exchange-it-for-an-access-token}

24시간 동안 유효한 액세스 토큰을 검색하기 위해 자격 증명을 사용하여 Adobe의 IMS 서비스 호출에 JWT 토큰을 만듭니다.

이 용도로 설계된 클라이언트 라이브러리를 사용하여 AEM CS 서비스 자격 증명을 액세스 토큰과 교환할 수 있습니다. 클라이언트 라이브러리는 [Adobe의 공개 GitHub 저장소](https://github.com/adobe/aemcs-api-client-lib)에서 사용할 수 있으며, 여기에는 보다 자세한 안내서와 최신 정보가 포함되어 있습니다.

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

### AEM API를 호출합니다 {#calling-the-aem-api}

헤더에 액세스 토큰을 포함하여 AEM에 대한 적절한 서버 간 API 호출을 Cloud Service 환경으로 만드십시오. 따라서 &quot;Authorization&quot; 헤더의 경우 값 `"Bearer <access_token>"`을 사용하십시오. 예를 들어 `curl` 사용:

```curlc
curl -H "Authorization: Bearer <your_ims_access_token>" https://author-p123123-e23423423.adobeaemcloud.com/content/dam.json
```

### AEM에서 기술 계정 사용자에 대한 적절한 권한 설정 {#set-the-appropriate-permissions-for-the-technical-account-user-in-aem}

기술 계정 사용자가 AEM에서 만들어지면(해당 액세스 토큰이 있는 첫 번째 요청 후 발생) 기술 계정 사용자는&#x200B;**AEM에서**&#x200B;의 권한을 적절하게 부여받아야 합니다.

기본적으로 AEM 작성자 서비스에서는 기술 계정 사용자가 읽기 액세스 AEM을 제공하는 기여자 사용자 그룹에 추가됩니다.

AEM에서 이 기술 계정 사용자는 일반적인 방법을 사용하여 권한을 추가로 보유할 수 있습니다.

## 개발자 흐름 {#developer-flow}

개발자는 개발 AEM에 Cloud Service 개발 환경으로 요청하는 비 AEM 애플리케이션(랩톱에서 실행 또는 호스팅)의 개발 인스턴스를 사용하여 테스트하려고 할 수 있습니다. 그러나 개발자에게 반드시 IMS 관리자 역할 권한이 없으므로 일반 서버 간 플로우에 설명된 JWT 전달자를 생성할 수 있다고 간주할 수 없습니다. 따라서 Adobe는 개발자가 액세스 권한이 있는 Cloud Service 환경으로 AEM에 대한 요청에 사용할 수 있는 액세스 토큰을 직접 생성하는 메커니즘을 제공합니다.

AEM을 Cloud Service 개발자 콘솔로 사용하는 데 필요한 권한에 대한 자세한 내용은 [개발자 지침 설명서](/help/implementing/developing/introduction/development-guidelines.md#crxde-lite-and-developer-console) 를 참조하십시오.

>[!NOTE]
>
>로컬 개발 액세스 토큰은 동일한 방법으로 재생성해야 하는 후 최대 24시간 동안 유효합니다.

개발자는 이 토큰을 사용하여 AEM이 아닌 테스트 애플리케이션에서 AEM으로 Cloud Service 환경을 호출할 수 있습니다. 일반적으로 개발자는 자체 랩탑에서 비 AEM 애플리케이션과 함께 이 토큰을 사용합니다. 또한 AEM as a Cloud는 일반적으로 비프로덕션 환경입니다.

개발자 플로우에는 다음 단계가 포함됩니다.

* 개발자 콘솔에서 액세스 토큰 생성
* 액세스 토큰을 사용하여 AEM 애플리케이션을 호출합니다.

개발자는 로컬 시스템에서 실행 중인 AEM 프로젝트에 API를 호출할 수도 있습니다. 이 경우 액세스 토큰이 필요하지 않습니다.

### 액세스 토큰 생성 {#generating-the-access-token}

개발자 콘솔에서 **로컬 개발 토큰 가져오기** 단추를 클릭하여 액세스 토큰을 생성합니다.

### 액세스 토큰을 사용하여 AEM 애플리케이션을 호출한 다음 {#call-the-aem-application-with-an-access-token}

헤더에 액세스 토큰을 포함하여 비 AEM 애플리케이션에서 AEM으로 적절한 서버 간 API 호출을 Cloud Service 환경으로 수행하십시오. 따라서 &quot;Authorization&quot; 헤더의 경우 값 `"Bearer <access_token>"`을 사용하십시오.

## 서비스 자격 증명 해지 {#service-credentials-revocation}

자격 증명을 취소해야 하는 경우 다음 단계를 사용하여 고객 지원에 요청을 제출해야 합니다.

1. 사용자 인터페이스에서 Adobe Admin Console에 대한 기술 계정 사용자를 비활성화합니다.
   * Cloud Manager에서 **.. 키를 누릅니다.환경 옆에 있는** 버튼을 클릭합니다. 제품 프로필 페이지가 열립니다
   * 이제 **AEM Users** 프로필을 클릭하여 사용자 목록을 표시합니다
   * **API 자격 증명** 탭을 클릭한 다음 적절한 기술 계정 사용자를 찾아 삭제합니다
2. 고객 지원에 문의하여 해당 특정 환경에 대한 서비스 자격 증명을 삭제하도록 요청하십시오
3. 마지막으로 이 설명서에 설명된 대로 자격 증명을 다시 생성할 수 있습니다. 또한 만들어진 새 기술 계정 사용자에게 적절한 권한이 있는지 확인합니다.
