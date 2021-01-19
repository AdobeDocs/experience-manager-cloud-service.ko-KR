---
title: 서버측 API에 대한 액세스 토큰 생성
description: 안전한 JWT 토큰을 생성하여 제3자 서버와 AEM 간의 Cloud Service으로 원활한 커뮤니케이션을 제공하는 방법을 살펴볼 수 있습니다.
translation-type: tm+mt
source-git-commit: a29eda3347502a3a498c2f40ed2e46cda59b2a24
workflow-type: tm+mt
source-wordcount: '1095'
ht-degree: 0%

---


# 소개 {#introduction}

>[!IMPORTANT]
>
>이 기능은 아직 사용할 수 없습니다. 최신 기능 목록은 [릴리스 노트](/help/release-notes/release-notes-cloud/release-notes-current.md)를 참조하십시오.

일부 아키텍처에서는 AEM에 대한 호출을 AEM 인프라 외부의 서버에 호스팅된 애플리케이션의 Cloud Service으로 사용합니다. 예를 들어 서버를 호출한 다음 API가 AEM에 Cloud Service으로 요청을 하는 모바일 응용 프로그램입니다.

서버 간 흐름은 개발을 위한 간소화된 흐름과 함께 아래에 설명되어 있습니다. Cloud Service [Developer Console](development-guidelines.md#crxde-lite-and-developer-console)(으)로 AEM은 인증 프로세스에 필요한 토큰을 생성하는 데 사용됩니다.

## 서버 간 흐름 {#the-server-to-server-flow}

IMS 조직 관리자 역할을 가진 사용자는 AEM을 Cloud Service 자격 증명으로 생성할 수 있으며, 자격 증명으로 만든 다음 AEM을 Cloud Service 환경 관리자 역할로 사용하여 검색할 수 있고 서버에 설치되어야 하며 비밀 키로 신중하게 취급해야 합니다. 이 JSON 형식 파일에는 Cloud Service API로 AEM과 통합하는 데 필요한 모든 데이터가 포함되어 있습니다. 이 데이터는 IMS 액세스 토큰과 교환되는 서명된 JWT 토큰을 만드는 데 사용됩니다. 그런 다음 이 액세스 토큰을 베어러 인증 토큰으로 사용하여 AEM에 Cloud Service으로 요청을 할 수 있습니다.

서버 간 흐름에는 다음 단계가 포함됩니다.

* 개발자 콘솔에서 AEM을 Cloud Service 자격 증명으로 가져오기
* AEM 호출을 수행하는 AEM 서버가 아닌 서버에 AEM을 Cloud Service 자격 증명으로 설치합니다.
* JWT 토큰을 생성하고 Adobe의 IMS API를 사용하여 액세스 토큰에 대해 해당 토큰을 교환합니다.
* 액세스 토큰이 있는 AEM API를 Bearer 인증 토큰으로 호출
* AEM 환경에서 기술 계정 사용자에 대한 적절한 권한 설정

### AEM을 Cloud Service 자격 증명 {#fetch-the-aem-as-a-cloud-service-credentials}으로 가져오기

Cloud Service 개발자 콘솔로 AEM에 액세스할 수 있는 사용자는 주어진 환경에 대한 개발자 콘솔의 통합 탭과 두 개의 단추를 볼 수 있습니다. AEM을 Cloud Service 환경 관리자 역할로 사용하는 사용자는 **서비스 자격 증명 가져오기** 단추를 클릭하여 서비스 자격 증명 json을 표시할 수 있습니다. 이 JSON은 창 선택에 상관없이 클라이언트 ID, 클라이언트 암호, 개인 키, 인증서, 환경 작성자 및 게시 계층에 대한 구성 등 AEM 이외의 서버에 필요한 모든 정보를 포함합니다.

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

>[!IMPORTANT]
>
>IMS 조직 관리자(일반적으로 클라우드 관리자를 통해 환경을 프로비저닝한 사용자)는 먼저 개발자 콘솔에 액세스한 후 **서비스 자격 증명 가져오기** 단추를 클릭하여 자격 증명을 생성하고 AEM에 대한 관리 권한이 있는 사용자가 Cloud Service 환경으로 검색하도록 해야 합니다. IMS 조직 관리자가 이 작업을 수행하지 않은 경우 IMS 조직 관리자 역할이 필요하다는 메시지가 표시됩니다.

### AEM 서버가 아닌 서버에 AEM 서비스 자격 증명 설치 {#install-the-aem-service-credentials-on-a-non-aem-server}

AEM을 호출하지 않는 응용 프로그램은 AEM을 Cloud Service 자격 증명으로 액세스하여 암호로 처리할 수 있어야 합니다.

### JWT 토큰을 생성하고 액세스 토큰{#generate-a-jwt-token-and-exchange-it-for-an-access-token}에 대해 교환

24시간 동안 유효한 액세스 토큰을 검색하기 위해 자격 증명을 사용하여 Adobe IMS 서비스 호출 시 JWT 토큰을 만듭니다.

AEM CS 서비스 자격 증명은 이러한 목적으로 설계된 클라이언트 라이브러리를 사용하여 액세스 토큰으로 교환될 수 있습니다. 클라이언트 라이브러리는 보다 자세한 지침 및 최신 정보가 포함된 [Adobe의 공용 GitHub 저장소](https://github.com/adobe/aemcs-api-client-lib)에서 사용할 수 있습니다.

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

서명된 JWT 토큰을 올바른 형식으로 생성하고 IMS 토큰 교환 API를 호출할 수 있는 모든 언어로 동일한 교환을 수행할 수 있습니다.

액세스 토큰은 만료 시기를 정의합니다(일반적으로 12시간). git 리포지토리에 액세스 토큰을 관리하고 만료되기 전에 새로 고치는 샘플 코드가 있습니다.

### AEM API {#calling-the-aem-api} 호출

헤더의 액세스 토큰을 포함하여 AEM에 대한 적절한 서버 간 API 호출을 Cloud Service 환경으로 만듭니다. 따라서 &quot;인증&quot; 헤더의 경우 `"Bearer <access_token>"` 값을 사용합니다. 예를 들어 `curl` 사용:

```curlc
curl -H "Authorization: Bearer <your_ims_access_token>" https://author-p123123-e23423423.adobeaemcloud.com/content/dam.json
```

### AEM {#set-the-appropriate-permissions-for-the-technical-account-user-in-aem}에서 기술 계정 사용자에 대한 적절한 권한 설정

기술 계정 사용자가 AEM에서 만들어지면(해당 액세스 토큰의 첫 번째 요청 후 발생) 기술 계정 사용자가&#x200B;**AEM에서**&#x200B;의 권한을 제대로 부여받아야 합니다.

기본적으로 AEM 작성자 서비스에서 기술 계정 사용자는 읽기 액세스 AEM을 제공하는 기여자 사용자 그룹에 추가됩니다.

AEM의 이 기술 계정 사용자는 일반적인 방법을 사용하여 권한을 추가로 부여할 수 있습니다.

## 개발자 흐름 {#developer-flow}

개발자는 Cloud Service 개발 환경으로 개발 AEM에 요청을 하는 AEM 애플리케이션이 아닌 애플리케이션의 개발 인스턴스(랩탑에서 실행 또는 호스팅)를 사용하여 테스트할 수 있습니다. 그러나 개발자가 IMS 관리자 역할 권한을 가지고 있지 않아도 되므로 일반 서버 간 흐름에 설명된 JWT 전달자를 생성할 수 있다고 가정할 수는 없습니다. 따라서, 개발자가 액세스 권한이 있는 Cloud Service 환경으로 AEM 요청에 사용할 수 있는 액세스 토큰을 직접 생성할 수 있는 메커니즘을 제공합니다.

AEM을 Cloud Service 개발자 콘솔로 사용하는 데 필요한 권한에 대한 자세한 내용은 [개발자 지침 문서](/help/implementing/developing/introduction/development-guidelines.md#crxde-lite-and-developer-console)를 참조하십시오.

>[!NOTE]
>
>로컬 개발 액세스 토큰은 24시간 동안 유효하며 동일한 방법으로 다시 생성해야 합니다.

개발자는 이 토큰을 사용하여 AEM이 아닌 테스트 애플리케이션에서 AEM으로 전화를 거는 Cloud Service 환경을 만들 수 있습니다. 일반적으로 개발자는 자체 랩탑에서 AEM이 아닌 응용 프로그램과 함께 이 토큰을 사용합니다. 또한 AEM as a Cloud는 일반적으로 비 프로덕션 환경입니다.

개발자 흐름에는 다음 단계가 포함됩니다.

* 개발자 콘솔에서 액세스 토큰 생성
* 액세스 토큰을 사용하여 AEM 응용 프로그램을 호출합니다.

또한 개발자는 로컬 시스템에서 실행 중인 AEM 프로젝트에 API 호출을 수행할 수 있습니다. 이 경우 액세스 토큰이 필요하지 않습니다.

### 액세스 토큰 {#generating-the-access-token} 생성

액세스 토큰을 생성하려면 개발자 콘솔에서 **로컬 개발 토큰 가져오기** 버튼을 클릭합니다.

### 액세스 토큰 {#call-the-aem-application-with-an-access-token}이 있는 AEM 응용 프로그램을 호출한 다음

헤더에 있는 액세스 토큰을 포함하여 AEM이 아닌 응용 프로그램에서 AEM으로 적절한 서버 간 API 호출을 Cloud Service 환경으로 만듭니다. 따라서 &quot;인증&quot; 헤더의 경우 `"Bearer <access_token>"` 값을 사용합니다.

## 서비스 자격 증명 해지 {#service-credentials-revocation}

JWT 전달자 토큰을 취소해야 하는 경우 고객 지원에 요청을 제출하십시오.