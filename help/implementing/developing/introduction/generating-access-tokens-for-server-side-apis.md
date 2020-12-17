---
title: 서버측 API에 대한 액세스 토큰 생성
description: 안전한 JWT 토큰을 생성하여 제3자 서버와 AEM 간의 Cloud Service으로 원활한 커뮤니케이션을 제공하는 방법을 살펴볼 수 있습니다.
translation-type: tm+mt
source-git-commit: 9a4cb6d981fdf5eea4d1b9c7ae9e3c99947d9745
workflow-type: tm+mt
source-wordcount: '684'
ht-degree: 0%

---


# 소개 {#introduction}

>[!IMPORTANT]
>
>이 기능은 아직 사용할 수 없습니다. 최신 기능 목록은 [릴리스 노트](/help/release-notes/release-notes-cloud/release-notes-current.md)를 참조하십시오.

일부 아키텍처에서는 AEM에 대한 호출을 AEM 인프라 외부의 서버에 호스팅된 애플리케이션의 Cloud Service으로 사용합니다. 예를 들어 서버를 호출한 다음 API가 AEM에 Cloud Service으로 요청을 하는 모바일 응용 프로그램입니다.

서버 간 흐름은 개발을 위한 간소화된 흐름과 함께 아래에 설명되어 있습니다. Cloud Service [Developer Console](development-guidelines.md#crxde-lite-and-developer-console)(으)로 AEM은 인증 프로세스에 필요한 토큰을 생성하는 데 사용됩니다.

## 서버 간 흐름 {#the-server-to-server-flow}

관리자 역할을 가진 사용자는 JWT 전달자 토큰을 생성할 수 있습니다. 이 토큰은 서버에 설치되어야 하며 이를 비밀 키로 신중하게 취급해야 합니다. JWT 전달자 토큰은 IMS와 액세스 토큰으로 교환되어야 하며, 이것은 AEM에 Cloud Service으로 요청서에 포함되어야 합니다.

서버 간 흐름에는 다음 단계가 포함됩니다.

* 개발자 콘솔에서 JWT 전달자 토큰을 생성합니다.
* AEM 호출을 수행하는 AEM이 아닌 서버에 토큰을 설치합니다.
* Adobe IMS API를 사용하여 액세스 토큰으로 JWT 전달자 토큰을 교환합니다.
* AEM API 호출

### JWT 전달자 토큰 {#generating-the-jwt-bearer-token} 생성

조직에 대한 관리자 역할을 가진 사용자는 주어진 환경에 대한 개발자 콘솔의 통합 탭과 두 개의 단추를 볼 수 있습니다. **서비스 자격 증명 가져오기** 단추를 클릭하면 개인 키, 인증서 및 구성이 생성됩니다.

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

### AEM이 아닌 서버 {#install-the-token-on-a-non-aem-server}에 토큰 설치

AEM에 대한 호출을 하지 않는 응용 프로그램은 JWT 전달자 토큰을 설치하여 이를 암호로 취급해야 합니다.

### 액세스 토큰 {#exchange-the-jwt-token-for-an-access-token}에 대한 JWT 토큰 교환

24시간 동안 유효한 액세스 토큰을 검색하기 위해 Adobe IMS 서비스 호출에 JWT 토큰을 포함합니다.

### AEM API {#calling-the-aem-api} 호출

헤더의 액세스 토큰을 포함하여 AEM에 대한 적절한 서버 간 API 호출을 Cloud Service 환경으로 만듭니다. 따라서 &quot;인증&quot; 헤더의 경우 `"Bearer <access_token>"` 값을 사용합니다.

<!-- ### Code Samples {#code-samples}

https://git.corp.adobe.com/boston/skyline-api-client-lib (internal note: URL will change to public git repo before we publish) contains client libraries written in node.js that will exchange the JSON outputted by the developer console for an access token. -->

## 개발자 흐름 {#developer-flow}

개발자는 Cloud Service 개발 환경으로 개발 AEM에 요청을 하는 AEM 애플리케이션이 아닌 애플리케이션의 개발 인스턴스(랩탑에서 실행 또는 호스팅)를 사용하여 테스트할 수 있습니다. 그러나, 개발자는 Cloud Service 개발 환경으로 AEM에 대한 관리자 역할 액세스 권한이 반드시 없는 경우, 일반 서버간 흐름에 설명된 JWT 전달자를 생성할 수 있다고 간주할 수 없습니다. 따라서, 개발자가 액세스 권한이 있는 Cloud Service 환경으로 AEM 요청에 사용할 수 있는 액세스 토큰을 직접 생성할 수 있는 메커니즘을 제공합니다. AEM을 Cloud Service 개발자 콘솔로 사용하는 데 필요한 권한에 대한 자세한 내용은 [개발자 지침 문서](/help/implementing/developing/introduction/development-guidelines.md)를 참조하십시오.

>[!NOTE]
>
>토큰은 동일한 방법으로 다시 생성해야 하는 시간이 지난 후 24시간 동안 유효합니다.

개발자는 이 토큰을 사용하여 AEM이 아닌 테스트 애플리케이션에서 AEM으로 전화를 거는 Cloud Service 환경을 만들 수 있습니다. 일반적으로 개발자는 자체 랩탑에서 AEM이 아닌 응용 프로그램과 함께 이 토큰을 사용합니다. 또한 AEM as a Cloud는 일반적으로 비 프로덕션 환경입니다.

개발자 흐름에는 다음 단계가 포함됩니다.

* 개발자 콘솔에서 액세스 토큰 생성
* 액세스 토큰을 사용하여 AEM 응용 프로그램을 호출합니다.

또한 개발자는 로컬 시스템에서 실행 중인 AEM 프로젝트에 API 호출을 수행할 수 있습니다. 이 경우 액세스 토큰이 필요하지 않습니다.

### 액세스 토큰 {#generating-the-access-token} 생성

액세스 토큰을 생성하려면 개발자 콘솔에서 **로컬 개발 토큰 가져오기** 버튼을 클릭합니다.

### 액세스 토큰 {#call-the-aem-application-with-an-access-token}이 있는 AEM 응용 프로그램을 호출한 다음

헤더에 있는 액세스 토큰을 포함하여 AEM이 아닌 응용 프로그램에서 AEM으로 적절한 서버 간 API 호출을 Cloud Service 환경으로 만듭니다. 따라서 &quot;인증&quot; 헤더의 경우 `"Bearer <access_token>"` 값을 사용합니다.

## JWT 베어러 토큰 해지 {#jwt-bearer-token-revocation}

JWT 전달자 토큰을 취소해야 하는 경우 고객 지원에 요청을 제출하십시오.