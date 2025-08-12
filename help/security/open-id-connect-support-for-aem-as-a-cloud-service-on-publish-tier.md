---
title: 게시 계층에서 AEM as a Cloud Service에 대한 Open ID Connect 지원
description: 게시 계층에서 AEM as a Cloud Service에 대한 OIDC(Open ID Connect)를 설정하는 방법에 대해 알아봅니다
feature: Security
role: Admin
source-git-commit: 7f96e51861cb544f83f8ff557dd923fa5b59c0b2
workflow-type: tm+mt
source-wordcount: '1469'
ht-degree: 0%

---


# 게시 계층에서 AEM as a Cloud Service에 대한 Open ID Connect 지원

## 소개 {#introduction}

조직이 디지털 환경을 현대화함에 따라 안전하고 확장 가능한 ID 관리가 기본 요구 사항이 됩니다. Adobe Experience Manager(AEM) Cloud Service은 이제 게시 계층에서 OIDC(OpenID Connect)를 지원하여 Entra ID(Azure AD), Google, Okta, Auth0, Ping Identity, ForgeRock 및 OIDC에서 지원하는 IDP와 같은 주요 ID 공급자(IdP)와 매끄럽고 표준 기반의 통합을 지원합니다.

OIDC는 OAuth 2.0 프로토콜 위에 있는 ID 레이어로 개발자의 단순성을 유지하면서 강력한 사용자 인증을 지원합니다. B2C(Business-to-Consumer), 인트라넷 및 파트너 포털 시나리오에서 보안 사용자 로그인 및 ID 페더레이션이 필요한 경우에 널리 채택됩니다.

지금까지 AEM 고객은 게시 계층에서 자체 사용자 지정 로그인 논리를 구현하여 개발 시간을 늘리고 장기적인 유지 관리 및 보안 문제를 도입했습니다. OIDC에 대한 기본 지원을 통해 AEM Cloud Service는 게시 환경에 액세스하는 최종 사용자에게 안전하고 확장 가능한 Adobe 지원 인증 메커니즘을 제공하여 이러한 부담을 제거합니다.

개인화된 소비자 웹 사이트를 제공하든 인증된 내부 포털을 제공하든, Publish의 OIDC는 중앙 집중식 ID 거버넌스를 통해 ID 페더레이션을 단순화하고 위험을 줄입니다. 또한 조직은 민첩성을 그대로 유지하면서 최신 규정 준수 및 보안 표준을 충족할 수 있습니다.

## OIDC 인증을 위한 AEM 구성 {#configure-aem-oidc-authentication}

### 사전 요구 사항 {#prerequisits}

다음 정보가 사용 가능하거나 정의되어 있다고 가정합니다.

1. AEM 저장소에서 보호할 콘텐츠의 경로
1. 구성할 IdP의 식별자입니다. 어떤 문자열이든 가능합니다.

IdP 구성의 정보:

1. IdP에 구성된 클라이언트 Id
1. Idp에 구성된 클라이언트 암호입니다. PKCE가 Idp에 구성된 경우 클라이언트 암호를 사용할 수 없습니다. 구성 파일에 일반 텍스트 값을 저장하지 마십시오. CM 암호 사용 및 참조
1. Idp에 구성된 범위입니다. 최소한 `openid` 범위를 제공해야 합니다.
1. IdP에서 PKCE가 활성화되었는지 여부
1. `callbackUrl`은(는) 지점 1에 정의된 구성된 경로 중 하나를 사용하고 접미사 `/j_security_check`을(를) 추가하여 정의됩니다.
1. 표준 `baseUrl` 파일에 액세스할 수 있는 `.well-known`. 예를 들어 잘 알려진 URL이 `https://login.microsoftonline.com/53279d7a-438f-41cd-a6a0-fdb09efc8891/v2.0/.well-known/openid-configuration`인 경우 `baseUrl`은(는) `https://login.microsoftonline.com/53279d7a-438f-41cd-a6a0-fdb09efc8891`입니다.

### 구성 파일 개요 {#overview-of-the-configuration-files}

구성해야 하는 파일 목록은 아래에서 확인하십시오.

1. **OIDC 연결**: `OidcAuthenticationHandler`이(가) 사용자를 인증하거나 다른 구성 요소에서 [OAuth를 사용하여 IdP로 보호되는 리소스에 대한 액세스 권한을 부여하는 데 사용됩니다](https://github.com/apache/sling-org-apache-sling-auth-oauth-client)
1. **OIDC 인증 처리기**: 구성된 경로에 액세스하는 사용자를 인증하는 데 사용되는 인증 처리기입니다
1. **UserInfoProcessor**: 이 구성 요소는 IdP에서 받은 정보를 처리합니다. 고객이 사용자 지정 논리를 구현하도록 확장할 수 있습니다
1. [**기본 동기화 처리기**](https://jackrabbit.apache.org/oak/docs/security/authentication/external/defaultusersync.html): 이 구성 요소는 저장소에서 사용자를 만듭니다
1. [**ExternalLoginModule**](https://jackrabbit.apache.org/oak/docs/security/authentication/externalloginmodule.html): 이 구성 요소는 로컬 oak 리포지토리에서 사용자를 인증합니다.

다음 다이어그램은 언급된 구성 요소가 연결되는 방식을 보여 줍니다. `ServiceFactory`개의 구성 요소이므로 `~uniqueid`은(는) 임의의 고유한 문자열일 수 있습니다.

![OIDC 구성 다이어그램](/help/security/assets/oidc-diagram.png)

### OIDC 연결 구성 {#configure-the-oidc-connection}

먼저 OIDC 연결을 구성해야 합니다. 여러 OIDC 연결을 구성할 수 있으며 각각 다른 이름을 사용해야 합니다.

1. 구성을 저장할 새 `.cfg.json` 파일을 만듭니다. 예를 들어 `org.apache.sling.auth.oauth_client.impl.OidcConnectionImpl~azure.cfg.json`을(를) 사용할 수 있습니다. **azure** 접미사는 연결의 고유 식별자여야 합니다.
1. 아래 예에서 구성 형식을 따르십시오.

   ```
   {
    "name":"azure",
    "scopes":[
      "openid"
    ],
    "baseUrl":"<https://login.microsoftonline.com/53279d7a-438f-41cd-a6a0-fdb09efc8891/v2.0>",
    "clientId":"5199fc45-8000-473e-ac63-989f1a78759f",
    "clientSecret":"xxxxxx"
   }
   ```

1. 속성을 다음과 같이 구성합니다.
   * 사용자가 **&quot;name&quot;**&#x200B;을(를) 정의할 수 있습니다.
   * `baseUrl`, `clientid` 및 `clientSecret`은(는) IdP에서 가져오는 구성 값입니다.
   * 범위에는 최소한 `openid` 값이 있어야 합니다.

### OIDC 인증 핸들러 구성 {#configure-oidc-authentication-handler}

이제 OIDC 인증 핸들러를 구성합니다. 여러 OIDC 연결을 구성할 수 있습니다. 각각 다른 이름을 사용해야 합니다. 동일한 [OAK 외부 ID 공급자](https://jackrabbit.apache.org/oak/docs/security/authentication/identitymanagement.html)를 공유하는 경우 사용자를 공유할 수 있습니다.

1. 구성 파일을 만듭니다. 이 예제에서는 `org.apache.sling.auth.oauth_client.impl.OidcConnectionImpl~azure.cfg.json`을(를) 사용합니다. `azure` 접미사는 고유 식별자여야 합니다. 아래 구성 파일의 예를 참조하십시오.

   ```
   {
     "path":"/content/tests/us/en/test-7",
     "callbackUri":"http://localhost:14503/content/tests/us/en/test-7/j_security_check",
     "pkceEnabled":false,
     "defaultConnectionName":"azure"
     "idp": "azure-idp"
   }
   ```

1. 그런 다음 속성을 다음과 같이 구성합니다.
   * `path`: 보호할 경로
   * `callbackUri`: 보호할 경로에 접미사 `/j_security_check`을(를) 추가합니다.
   * `defaultConnectionName`: 이전 단계의 OIDC 연결에 대해 정의된 이름과 동일한 이름으로 구성+
   * `pkceEnabled`: 인증 코드 흐름의 PKCE(Proof Key for Code Exchange) `true`
   * `idp`: [OAK 외부 ID 공급자](https://jackrabbit.apache.org/oak/docs/security/authentication/identitymanagement.html)의 이름입니다. 다른 OAK IDP는 사용자 또는 그룹을 공유할 수 없습니다

### SlingUserInfoProcessor 구성

1. 구성 파일을 만듭니다. 이 예제에서는 `org.apache.sling.auth.oauth_client.impl.SlingUserInfoProcessor~azure.cfg.json`을(를) 사용합니다. `azure` 접미사는 고유 식별자여야 합니다. 아래 구성 파일의 예를 참조하십시오.

   ```
   {
      "groupsInIdToken":true,
      "groupsClaimName": "groups",
      "connection":"azure",
      "storeAccessToken": false,
      "storeRefreshToken": false
   }
   ```

1. 그런 다음 속성을 다음과 같이 구성합니다.
   * `groupsInIdToken`: ID 토큰으로 그룹이 전송되는 경우 true로 설정합니다. 값이 false이거나 지정되지 않으면 UserInfo 끝점에서 그룹을 읽습니다.
   * `groupsClaimName`: 클레임 이름에 AEM에서 동기화할 그룹이 포함되어 있습니다.
   * `connection`: 이전 단계의 OIDC 연결에 대해 정의된 이름과 동일한 이름으로 구성
   * `storeAccessToken`: 액세스 토큰을 저장소에 저장해야 하는 경우 true입니다. 기본적으로 false입니다. AEM이 동일한 IdP로 보호되는 외부 서버에 저장된 사용자 대신 리소스에 액세스해야 하는 경우에만 true로 설정합니다.
   * `storeRefreshToken`: 새로 고침 토큰을 저장소에 저장해야 하는 경우 true입니다. 기본적으로 false입니다. AEM이 동일한 IdP로 보호되는 외부 서버에 저장된 사용자 대신 리소스에 액세스해야 하고 IdP에서 토큰을 새로 고쳐야 하는 경우에만 true로 설정합니다.
액세스 토큰 및 새로 고침 토큰은 AEM 마스터 키로 암호화되어 저장된다는 점을 나타냅니다.


### 동기화 핸들러 구성 {#configure-the-synchronization-handler}

oak에서 인증된 사용자를 동기화하려면 동기화 핸들러가 하나 이상 구성되어 있어야 합니다. 자세한 내용은 [이](https://jackrabbit.apache.org/oak/docs/security/authentication/external/defaultusersync.html) 페이지를 참조하세요.

이름이 `org.apache.jackrabbit.oak.spi.security.authentication.external.impl.DefaultSyncHandler~azure.cfg.json`인 파일을 만듭니다. **azure** 접미사는 고유 식별자여야 합니다. 속성을 구성하는 방법에 대한 자세한 내용은 [Oak 사용자 및 그룹 동기화 설명서](https://jackrabbit.apache.org/oak/docs/security/authentication/external/defaultusersync.html)를 참조하십시오. 아래의 예제 구성을 확인하십시오.

```
{
  "user.expirationTime":"300s",
  "user.membershipExpTime":"300s",
  "user.propertyMapping":[
    "profile/familyName=profile/familyName",
    "profile/givenName=profile/givenName",
    "rep:fullname=cn",
    "profile/email=profile/email",
    "oauth-tokens"
  ],
  "user.pathPrefix":"azure",
  "handler.name":"azure"
}
```

다음은 DefaultSyncHandler에서 구성할 가장 관련성이 높은 특성의 일부입니다. 클라우드 서비스에서 동적 그룹 멤버십을 항상 활성화해야 한다는 점을 참고하십시오.

| 속성 이름 | 메모 | 제안 값 |
|---|---|---|
| `user.expirationTime` | 동기화된 사용자가 만료될 때까지의 기간. 사용자는 만료 시간 이후에만 동기화됩니다. | 1시간 |
| `user.membershipExpTime` | 동기화된 사용자 멤버십이 만료될 때까지의 기간. 사용자 멤버십은 만료 시간이 지난 후에만 동기화됩니다. | 1시간 |
| `user.dynamicMembership` | 동적 그룹 멤버십을 활성화하는 것이 좋습니다. | true |
| `user.enforceDynamicMembership` | 동적 그룹 멤버십을 적용할 수 있도록 하는 것이 좋습니다. | true |
| `group.dynamicGroups` | 동적 그룹을 활성화하는 것이 좋습니다. | true |
| user.propertyMapping | 제공된 `UserInfoProcessor` 구현은 일부 속성만 동기화합니다. 수정하고 사용자 지정할 수 있습니다. | <code>&quot;profile/givenName=profile/given_name&quot;,</code><br><code>&quot;profile/familyName=profile/family_name&quot;,</code><br><code>&quot;rep:fullname=profile/name&quot;,</code><br><code>&quot;profile/email=profile/email&quot;,</code><br><code>&quot;access_token=access_token&quot;,</code><br><code>&quot;refresh_token=refresh_token&quot;</code> |  |
| `user.membershipNestingDepth` | 멤버십 관계가 동기화되면 그룹 중첩의 최대 깊이를 반환합니다. 값이 0이면 그룹 멤버십 조회가 효과적으로 비활성화됩니다. 값이 1이면 사용자의 직접 그룹만 추가됩니다. 이 값은 사용자 멤버십 상위 그룹을 동기화할 때만 개별 그룹을 동기화할 때 영향을 주지 않습니다. | 1 |

### 외부 로그인 모듈 구성 {#configure-the-external-login-module}

마지막으로 외부 로그인 모듈을 구성해야 합니다.

1. 이름이 `org.apache.jackrabbit.oak.spi.security.authentication.external.impl.ExternalLoginModuleFactory~azure.cfg.json`인 파일을 만듭니다. 아래의 예제 구성을 참조하십시오.

   ```
   {
    "sync.handlerName":"azure",
    "idp.name":"azure-idp"
   }
   ```

1. 속성을 다음과 같이 구성합니다.

   * `sync.handlerName`: 이전에 정의된 동기화 처리기의 이름
   * `idp.name`: OIDC 인증 처리기에 정의된 OAK ID 공급자

### 선택 사항: 사용자 지정 UserInfoProcessor 구현 {#implement-a-custom-userinfoprocessor}

사용자가 ID 토큰으로 인증되고 IdP에 대해 정의된 `userInfo` 끝점에서 추가 특성을 가져옵니다. 비표준 작업을 추가로 수행해야 하는 경우 Sling의 기본 구현은 [UserInfoProcessor](https://github.com/apache/sling-org-apache-sling-auth-oauth-client/blob/master/src/main/java/org/apache/sling/auth/oauth_client/impl/SlingUserInfoProcessorImpl.java)의 사용자 지정 구현입니다.

## 예: Azure Active Directory를 사용하여 OIDC 인증 구성

### Azure Active Directory에서 새 애플리케이션 구성 {#configure-a-new-application-in-azure-ad}

1. [Azure Active Directory 설명서](https://learn.microsoft.com/en-us/power-pages/security/authentication/openid-settings#create-an-app-registration-in-azure)를 따라 Azure Active Directory에서 새 응용 프로그램을 만드세요.  애플리케이션 개요를 자세히 설명하는 화면이 표시되는 방식은 아래를 참조하십시오.

   ![응용 프로그램 개요](/help/security/assets/odic-application-overview.png)

1. 그룹 또는 응용 프로그램 역할이 필요한 경우 [설명서](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-use-app-roles-customers)에 따라 응용 프로그램에서 사용하도록 설정하고 ID 토큰으로 보내십시오. 아래 구성된 그룹의 예는 다음과 같습니다.

![OIDC 클레임 토큰 ID](/help/security/assets/oidc-claim-id-token.png)

1. 이전에 문서화된 단계에 따라 필요한 구성 파일을 만듭니다. 아래에서는 Azure AD에 대한 예를 보여 줍니다.
   * oidc Connection, Authentication Handler 및 DefaultSyncHandler의 이름을 `azure`(으)로 정의합니다.
   * 웹 사이트 URL: `www.mywebsite.com`
   * `/content/wknd/us/en/adventures` 경로를 보호합니다.
   * 테넌트: `tennat-id`,
   * 클라이언트 ID: `client-id`,
   * 암호: `secret`,
   * 다음 클레임의 ID 토큰으로 그룹이 전송됩니다. `groups`

#### org.apache.sling.auth.oauth_client.impl.OidcConnectionImpl~azure.cfg.json

```
{
  "name":"azure",
  "scopes":[
    openid", "User.Read", "profile", "email
  ],
  "baseUrl":"https://login.microsoftonline.com/tenant-id/v2.0",
  "clientId":"client-id",
  "clientSecret":"secret"
}
```

#### org.apache.sling.auth.oauth_client.impl.OidcAuthenticationHandler~azure.cfg.json

```
{
  "callbackUri":"https://www.mywebsite.com/content/wknd/us/en/adventures/j_security_check",
  "path":[
    "/content/wknd/us/en/adventures"
  ],
  "idp":"azure",
  "defaultConnectionName":"azure"
}
```

#### org.apache.jackrabbit.oak.spi.security.authentication.external.impl.ExternalLoginModuleFactory~azure.cfg.json

```
{
  "sync.handlerName":"azure",
  "idp.name":"azure"
}
```

#### org.apache.jackrabbit.oak.spi.security.authentication.external.impl.DefaultSyncHandler~azure.cfg.json

```
{
  "user.expirationTime":"1s",
  "user.membershipExpTime":"1s",
  "user.propertyMapping":[
    "profile/givenName=profile/given_name",
    "profile/familyName=profile/family_name",
    "rep:fullname=profile/name",
    "profile/email=profile/email",
    "access_token=access_token",
    "refresh_token=refresh_token"
  ],
  "user.pathPrefix":"azure",
  "group.pathPrefix": "oidc",
  "user.membershipNestingDepth": "1",
  "handler.name":"azure"
}
```

#### org.apache.sling.auth.oauth_client.impl.SlingUserInfoProcessorImpl~azure.cfg.json

```
{
  "groupsInIdToken": "true",
  "storeAccessToken": "false",
  "storeRefreshToken": "false",
  "connection": "azure",
  "groupsClaimName": "groups"
}
```

### Azure AD 그룹에 대한 추가 정보 {#additional-information-about-azure-ad-groups}

Microsoft Azure 포털에서 엔터프라이즈 응용 프로그램에 대해 그룹을으로 구성하려면 **엔터프라이즈 응용 프로그램**&#x200B;에서 응용 프로그램을 검색하고 그룹을 추가해야 합니다. <!-- Alexandru: this bit cound be clearer-->

![OIDC 그룹 추가](/help/security/assets/oidc-ad-additional-info.png)

ID 토큰에서 그룹 클레임을 사용하려면 Microsoft Azure 포털 **의**&#x200B;토큰 구성<!-- Alexandru: this bit cound be clearer as well--> 섹션에 클레임을 추가하십시오.

![OIDC 클레임 토큰 ID](/help/security/assets/oidc-claim-id-token.png)

아래 예와 같이 `SlingUserInfoProcessor`의 구성을 수정해야 합니다.

수정해야 하는 파일 이름은 `org.apache.sling.auth.oauth_client.impl.SlingUserInfoProcessorImpl.cfg.json`입니다. 콘텐츠는 다음과 같이 구성되어야 합니다.

```
{
  "connection": "azure",
  "groupsInIdToken": "true",
  "storeAccessToken": "false",
  "storeRefreshToken": "false"
}
```
