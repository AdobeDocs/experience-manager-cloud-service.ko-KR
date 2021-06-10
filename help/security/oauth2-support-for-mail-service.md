---
title: 메일 서비스에 대한 OAuth2 지원
description: Adobe Experience Manager as a Cloud Service으로 메일 서비스에 대한 Oauth2 지원
source-git-commit: b46062697b25aa8d3f215a8a4249f5203bec268e
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# 메일 서비스 {#oauth2-support-for-the-mail-service}에 대한 OAuth2 지원

AEM as a Cloud Service은 조직이 보안 이메일 요구 사항을 준수할 수 있도록 통합 이메일 서비스에 대한 OAuth2 지원을 제공합니다.

여러 이메일 공급자에 대해 OAuth를 구성할 수 있습니다. 다음은 Microsoft Office 365 Outlook에서 OAuth2를 통해 인증하도록 AEM 메일 서비스를 구성하는 단계별 지침입니다. 다른 공급업체도 유사한 방식으로 구성할 수 있습니다.

AEM as a Cloud Service 메일 서비스에 대한 자세한 내용은 [이메일 보내기](/help/implementing/developing/introduction/development-guidelines.md#sending-email)를 참조하십시오.

## Microsoft Outlook {#microsoft-outlook}

1. [https://portal.azure.com/](https://portal.azure.com/)로 이동한 후 로그인합니다.
1. 검색 막대에서 **Azure Active Directory**&#x200B;를 검색하고 결과를 클릭합니다. 또는 [https://portal.azure.com/#blade/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade/Overview](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade/Overview)로 바로 이동할 수 있습니다
1. **앱 등록** - **새 등록**&#x200B;을 클릭합니다.

   ![](assets/oauth-outlook1.png)

1. 요구 사항에 따라 정보를 입력한 다음 **등록**&#x200B;을 클릭합니다.
1. 새로 만든 앱으로 이동하고 **API 권한**&#x200B;을 선택합니다.
1. **권한 추가** - **그래프 권한** - **위임된 권한**&#x200B;으로 이동합니다.
1. 앱에 대한 아래 권한을 선택한 다음 **권한 추가**&#x200B;를 클릭합니다.
   * `SMTP.Send`
   * `Mail.Read`
   * `Mail.Send`
   * `openid`
   * `offline_access`
1. **인증** - **플랫폼 추가** - **웹**&#x200B;로 이동하고 **리디렉션 URL** 섹션에서 슬래시 없이 하나씩 아래 URL을 추가하십시오.
   * `http://localhost/`
   * `http://localhost`
1. 각 URL을 추가한 후 **구성**&#x200B;을 누르고 요구 사항에 따라 설정을 구성합니다
1. 그런 다음 **인증서 및 Secrets**&#x200B;로 이동하여 **새 클라이언트 암호**&#x200B;를 클릭하고 화면 단계에 따라 암호를 만듭니다. 나중에 사용할 수 있도록 이 암호를 반드시 기록하십시오
1. 왼쪽 창에서 **개요**&#x200B;를 누르고 나중에 사용할 수 있도록 **응용 프로그램(클라이언트) ID** 및 **디렉토리(테넌트) ID**&#x200B;의 값을 복사합니다

다시 매핑하려면 AEM 측에서 Mail 서비스에 대해 OAuth2를 구성하려면 다음 정보가 필요합니다.

* 테넌트 ID로 빌드되는 인증 URL입니다. 다음 양식이 있습니다.`https://login.microsoftonline.com/<tenantID>/oauth2/v2.0/authorize`
* 테넌트 ID로 구성될 토큰 URL입니다. 다음 양식이 있습니다.`https://login.microsoftonline.com/<tenantID>/oauth2/v2.0/token`
* 테넌트 ID로 빌드되는 새로 고침 URL입니다. 다음 양식이 있습니다.`https://login.microsoftonline.com/<tenantID>/oauth2/v2.0/token`
* 클라이언트 ID
* 클라이언트 암호

### 새로 고침 토큰 생성 {#generating-the-refresh-token}

다음으로, 다음 단계에서 OSGi 구성의 일부인 새로 고침 토큰을 생성해야 합니다.

다음 단계를 수행하여 이 작업을 수행할 수 있습니다.

1. `clientID` 및 `tenantID` 를 계정에 대한 값으로 바꾼 후 브라우저에서 다음 URL을 엽니다.`https://login.microsoftonline.com/<tenantID>/oauth2/v2.0/authorize?client_id=<clientId>&response_type=code&redirect_uri=http://localhost&response_mode=query&scope=https%3A%2F%2Foutlook.office365.com%2FSMTP.Send%20EWS.AccessAsUser.All%20https%3A%2F%2Foutlook.office365.com%2FSMTP.Send%20https%3A%2F%2Foutlook.office365.com%2FMail.Read%20https%3A%2F%2Foutlook.office365.com%2FMail.Send%20openid%20offline_access&state=12345`
1. 요청 시 권한 허용
1. URL은 다음 형식으로 만들어진 새 위치로 리디렉션됩니다.`http://localhost/?code=<code>&state=12345&session_state=4f984c6b-cc1f-47b9-81b2-66522ea83f81#`
1. 위의 예에서 `<code>` 값을 복사합니다.
1. 다음 cURL 명령을 사용하여 refreshToken을 가져옵니다. tenantID, clientID 및 clientSecret을 계정 값과 `<code>` 값으로 바꿔야 합니다.

   `curl --location --request POST 'https://login.microsoftonline.com/<tenantId>/oauth2/v2.0/token' \
--header 'Content-Type: application/x-www-form-urlencoded' \
--header 'Cookie: buid=0.ARgAep0nU49DzUGmoP2wnvyIkcQjsx26HEpOnvHS0akqXQgYAAA.AQABAAEAAAD--DLA3VO7QrddgJg7Wevry9XPJSKbGVlPt5NWYxLtTl3K1W0LwHXelrffApUo_K02kFrkvmGm94rfBT94t25Zq4bCd5IM3yFOjWb3V22yDM7-rl112sLzbBQBRCL3QAAgAA; esctx=AQABAAAAAAD--DLA3VO7QrddgJg7Wevr4a8wBjYcNbBXRievdTOd15caaeAsQdXeBAQA3tjVQaxmrOXFGkKaE7HBzsJrzA-ci4RRpor-opoo5gpGLh3pj_iMZuqegQPEb1V5sUVQV8_DUEbBv5YFV2eczS5EAhLBAwAd1mHx6jYOL8LwZNDFvd2-MhVXwPd6iKPigSuBxMogAA; x-ms-gateway-slice=estsfd; stsservicecookie=estsfd; fpc=Auv6lTuyAP1FuOOCfj9w0U_5vR5dAQAAALDXP9gOAAAAwIpkkQEAAACT2T_YDgAAAA' \
--data-urlencode 'client_id=<clientID>' \
--data-urlencode 'scope=https://outlook.office365.com/SMTP.Send https://outlook.office365.com/Mail.Read https://outlook.office365.com/Mail.Send openid' \
--data-urlencode 'redirect_uri=http://localhost' \
--data-urlencode 'grant_type=authorization_code' \
--data-urlencode 'client_secret=<clientSecret>' \
--data-urlencode 'code=<code>'`

1. refreshToken 및 accessToken을 기록합니다.

### 토큰 {#validating-the-tokens} 확인

AEM 측에서 OAuth 구성을 계속 진행하기 전에 아래 절차에 따라 accessToken 및 refreshToken 의 유효성을 모두 확인합니다.

1. 이전 절차에서 생성된 refreshToken을 사용하여 accessToken을 생성합니다. curl을 사용하여 `<client_id>`,`<client_secret>` 및 `<refreshToken>`의 값을 바꿀 수 있습니다.

   `curl --location --request POST 'https://login.microsoftonline.com/<tenetId>/oauth2/v2.0/token' \
--header 'Content-Type: application/x-www-form-urlencoded' \
--header 'Cookie: buid=0.ARgAep0nU49DzUGmoP2wnvyIkcQjsx26HEpOnvHS0akqXQgYAAA.AQABAAEAAAD--DLA3VO7QrddgJg7Wevry9XPJSKbGVlPt5NWYxLtTl3K1W0LwHXelrffApUo_K02kFrkvmGm94rfBT94t25Zq4bCd5IM3yFOjWb3V22yDM7-rl112sLzbBQBRCL3QAAgAA; esctx=AQABAAAAAAD--DLA3VO7QrddgJg7Wevr4a8wBjYcNbBXRievdTOd15caaeAsQdXeBAQA3tjVQaxmrOXFGkKaE7HBzsJrzA-ci4RRpor-opoo5gpGLh3pj_iMZuqegQPEb1V5sUVQV8_DUEbBv5YFV2eczS5EAhLBAwAd1mHx6jYOL8LwZNDFvd2-MhVXwPd6iKPigSuBxMogAA; x-ms-gateway-slice=estsfd; stsservicecookie=estsfd; fpc=Auv6lTuyAP1FuOOCfj9w0U_IezHLAQAAAPeNSdgOAAAA' \
--data-urlencode 'client_id=<client_id>' \
--data-urlencode 'scope=https://outlook.office365.com/SMTP.Send https://outlook.office365.com/Mail.Read https://outlook.office365.com/Mail.Send openid' \
--data-urlencode 'redirect_uri=http://localhost' \
--data-urlencode 'grant_type=refresh_token' \
--data-urlencode 'client_secret=<client_secret>' \
--data-urlencode 'refresh_token=<refreshToken>'`

1. accessToken을 사용하여 메일을 보내 제대로 작동하는지 확인하십시오.

>[!NOTE]
>
> [이 위치](https://docs.microsoft.com/en-us/azure/active-directory/develop/v2-oauth2-auth-code-flow)에서 Postman API 컬렉션을 가져올 수 있습니다.

### AEM as a Cloud Service {#integration-with-aem-as-a-cloud-service} 과 통합

1. `/apps/<my-project>/osgiconfig/config` 아래에 다음 구문을 사용하여 `com.day.cq.mailer.oauth.impl.OAuthConfigurationProviderImpl.cfg.json`라는 OSGI 속성 파일을 만듭니다.

   ```
   {
       authUrl: "<Authorization Url>",
       tokenUrl: "<Token Url>",
       clientId: "<clientID>",
       clientSecret: "$[secret:SECRET_SMTP_OAUTH_CLIENT_SECRET]",
       scopes: [
          "scope1",
          "scope2"
       ],
       refreshUrl: "<Refresh token Url>",
       refreshToken: "$[secret:SECRET_SMTP_OAUTH_REFRESH_TOKEN]"
   }
   ```

1. 이전 섹션에 설명된 대로 구성을 수행하여 `authUrl`, `tokenUrl` 및 `refreshURL`를 입력합니다.
1. 구성에 다음 범위를 추가합니다.
   * `openid`
   * `offline_access`
   * `https://outlook.office365.com/Mail.Send`
   * `https://outlook.office365.com/Mail.Read`
   * `https://outlook.office365.com/SMTP.Send`
1. OSGI 속성 파일 `called com.day.cq.mailer.impl.DefaultMailService.cfg.json` 만들기
아래에 
`/apps/<my-project>/osgiconfig/config`  다음 구문 사용:

   ```
   {
    "smtp.host": "<smtp hostname>"
    "smtp.user": "<user account that logged into get the oauth tokens>",
    "smtp.password": "value not used",
    "smtp.port": 587,
    "from.address": "<from address used for sending>"
    "smtp.ssl": false,
    "smtp.starttls": true,
    "smtp.requiretls": true,
    "debug.email": false,
    "oauth.flow": true
   }
   ```

1. outlook의 경우 `smtp.host` 구성 값은 `smtp.office365.com`입니다.
1. 런타임 시 [여기](/help/implementing/deploying/configuring-osgi.md#setting-values-via-api)에 설명된 대로 Cloud Manager 변수 API를 사용하여 `refreshToken values` 및 `clientSecret` 암호를 전달합니다. 변수 `SECRET_SMTP_OAUTH_REFRESH_TOKEN` 및 `SECRET_SMTP_OAUTH_CLIENT_SECRET` 값을 정의해야 합니다.

### 문제 해결 {#troubleshooting}

메일 서비스가 제대로 작동하지 않으면 대부분의 경우 Cloud Manager API를 통해 새 값을 전달하여 위에 설명된 대로 `refreshToken`을 다시 생성해야 합니다. 새 값을 배포하려면 몇 분 정도 걸립니다.
