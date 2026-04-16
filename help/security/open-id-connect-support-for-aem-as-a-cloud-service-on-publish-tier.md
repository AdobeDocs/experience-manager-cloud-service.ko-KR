---
title: 게시 계층의 AEM as a Cloud Service에 대한 Open ID Connect 지원
description: 게시 계층에서 AEM as a Cloud Service에 대한 Open ID Connect(OIDC)를 설정하는 방법에 대해 알아봅니다.
feature: Security
role: Admin
exl-id: d2f30406-546c-4a2f-ba88-8046dee3e09b
source-git-commit: 70687e4f2ea0df923e44237bc20635745c46323a
workflow-type: tm+mt
source-wordcount: '2610'
ht-degree: 53%

---

# 게시 계층의 AEM as a Cloud Service에 대한 Open ID Connect 지원 {#open-id-connect-support-for-aem-as-a-cloud-service-on-publish-tier}

## 소개 {#introduction}

조직이 디지털 경험을 현대화함에 따라 안전하고 확장 가능한 ID 관리가 기본적인 요구 사항이 되었습니다. 이제 AEM(Adobe Experience Manager) Cloud Service는 게시 계층에서 OpenID Connect(OIDC)를 지원하므로 Entra ID(Azure AD), Google, Okta, Auth0, Ping Identity, ForgeRock 및 OIDC 지원 IdP와 같은 주요 IdP(Identity Provider)와의 원활하고 표준 기반 통합을 허용합니다.

OIDC는 OAuth 2.0 프로토콜 위에 있는 ID 계층으로, 개발자를 위한 단순성을 유지하면서 강력한 사용자 인증을 가능하게 합니다. 안전한 사용자 로그인 및 ID 페더레이션이 필요한 B2C(Business-to-Consumer), 인트라넷 및 파트너 포털 시나리오에 널리 채택됩니다.

지금까지 AEM 고객은 게시 계층에 자체 사용자 정의 로그인 논리를 구현해야 했으므로 개발 시간이 늘어나고 장기적인 유지 관리 및 보안 문제가 발생했습니다. OIDC에 대한 기본 지원을 통해 AEM Cloud Service는 게시 환경에 액세스하는 최종 사용자를 위한 안전하고 확장 가능하며 Adobe에서 지원하는 인증 메커니즘을 제공하여 이러한 부담을 없앱니다.

개인화된 소비자 웹 사이트를 제공하든 인증된 내부 포털을 제공하든 관계없이 게시물의 OIDC는 ID 페더레이션을 단순화하고 중앙 집중식 ID 거버넌스를 통해 위험을 줄입니다. 또한 조직이 민첩성을 희생하지 않고도 최신 규정 준수 및 보안 표준을 충족하도록 돕습니다.

## OIDC 인증에 대해 AEM 구성 {#configure-aem-oidc-authentication}

### 사전 요구 사항 {#prerequisits}

다음 정보가 사용 가능하거나 정의된 것으로 가정합니다.

1. AEM 저장소에서 보호할 콘텐츠의 경로
1. 구성할 IdP의 식별자 모든 문자열일 수 있습니다.

IdP 구성의 정보:

1. IdP에서 구성된 클라이언트 ID
1. IdP에서 구성된 클라이언트 보안 PKCE가 IdP에서 구성된 경우 클라이언트 보안을 사용할 수 없습니다. 구성 파일에 일반 텍스트 값을 저장하지 마십시오. CM 보안 사용 및 참조
1. IdP에서 구성된 범위 `openid` 범위 이상을 제공해야 합니다.
1. PKCE가 IdP에서 활성화되었는지 여부
1. `callbackUrl`은 1번 지점에서 정의된 구성 경로 중 하나를 사용하여 정의하고 `/j_security_check` 접미사를 추가합니다.
1. 표준 `.well-known` 파일에 액세스하기 위한 `baseUrl` 예를 들어 well-known url이 `https://login.microsoftonline.com/53279d7a-438f-41cd-a6a0-fdb09efc8891/v2.0/.well-known/openid-configuration`인 경우 `baseUrl`은 `https://login.microsoftonline.com/53279d7a-438f-41cd-a6a0-fdb09efc8891`입니다.

### 구성 파일 개요 {#overview-of-the-configuration-files}

구성해야 하는 파일 목록은 다음과 같습니다.

1. **OIDC 연결**: 이 연결은 `OidcAuthenticationHandler`가 사용자를 인증하거나, 다른 구성 요소가 [OAuth를 사용하여 IdP에 의해 보호되는 리소스에 대한 액세스를 승인](https://github.com/apache/sling-org-apache-sling-auth-oauth-client)하는 데 사용됩니다.
1. **OIDC 인증 핸들러**: 구성된 경로에 액세스하는 사용자를 인증하는 데 사용되는 인증 핸들러입니다.
1. **UserInfoProcessor**: 이 구성 요소는 IdP가 수신한 정보를 처리합니다. 사용자 정의 논리를 구현하기 위해 고객이 확장할 수 있습니다.
1. [**기본 동기화 핸들러**](https://jackrabbit.apache.org/oak/docs/security/authentication/external/defaultusersync.html): 이 구성 요소는 저장소에서 사용자를 생성합니다.
1. [**ExternalLoginModule**](https://jackrabbit.apache.org/oak/docs/security/authentication/externalloginmodule.html): 이 구성 요소는 로컬 Oak 저장소에서 사용자를 인증합니다.

다음 다이어그램은 언급된 구성 요소가 연결되는 방식을 보여 줍니다. 이러한 구성 요소는 `ServiceFactory` 구성 요소이므로 `~uniqueid`는 임의의 고유한 문자열이 될 수 있습니다.

![OIDC 구성 다이어그램](/help/security/assets/oidc-diagram.png)

### OIDC 연결 구성 {#configure-the-oidc-connection}

먼저 OIDC 연결을 구성해야 합니다. 여러 OIDC 연결을 구성할 수 있으며, 각 연결은 서로 다른 이름을 가져야 합니다.

1. 구성을 보관할 새 `.cfg.json` 파일을 만듭니다. 예를 들어 `org.apache.sling.auth.oauth_client.impl.OidcConnectionImpl~azure.cfg.json`을 사용할 수 있습니다. **azure** 접미사는 연결에 대한 고유 식별자여야 합니다.
1. 아래 예시의 구성 형식을 따르십시오.

   ```
   {
    "name":"azure",
    "scopes":[
      "openid"
    ],
    "baseUrl":"<https://login.microsoftonline.com/tenant-id/v2.0>",
    "clientId":"client-id-from-idp",
    "clientSecret":"xxxxxx"
   }
   ```

일부 환경에서 IdP(ID 공급자)가 올바른 `.well-known` 끝점을 노출하지 않을 수 있습니다.
이 경우 구성 파일에서 다음 속성을 지정하여 필요한 끝점을 수동으로 정의할 수 있습니다.
이 구성 모드에서는 `baseUrl` 속성을 설정하지 않아야 합니다.

```
"authorizationEndpoint": "https://idp-url/oauth2/v1/authorize",
"tokenEndpoint": "https://idp-url/oauth2/v1/token",
"jwkSetURL":"https://idp-url/oauth2/v1/keys",
"issuer": "https://idp-url"
```

1. 해당 속성을 다음과 같이 구성합니다.
   * **“name”**&#x200B;은 사용자가 정의할 수 있습니다.
   * `baseUrl`, `clientid` 및 `clientSecret`는 IdP에서 제공되는 구성 값입니다.
   * 범위에는 최소한 `openid` 값이 포함되어야 합니다.

### OIDC 인증 핸들러 구성 {#configure-oidc-authentication-handler}

이제 OIDC 인증 핸들러를 구성합니다. 여러 OIDC 연결을 구성할 수 있습니다. 각 연결은 서로 다른 이름을 가져야 합니다. 동일한 [OAK 외부 ID 공급자](https://jackrabbit.apache.org/oak/docs/security/authentication/identitymanagement.html)를 공유하는 경우 사용자를 공유할 수 있습니다.

1. 구성 파일을 생성합니다. 이 예시에서는 `org.apache.sling.auth.oauth_client.impl.OidcAuthenticationHandler~azure.cfg.json`을 사용합니다. `azure` 접미사는 고유 식별자여야 합니다. 아래 구성 파일의 예제를 확인해 보십시오.

   ```
   {
     "path":"/content/tests/us/en/test-7",
     "callbackUri":"http://localhost:14503/content/tests/us/en/test-7/j_security_check",
     "pkceEnabled":false,
     "defaultConnectionName":"azure"
     "idp": "azure-idp"
   }
   ```

1. 그런 다음 해당 속성을 다음과 같이 구성합니다.
   * `path`: 보호할 경로
   * `callbackUri`: 보호될 경로. 접미사 `/j_security_check`을(를) 추가합니다. 원격 IdP에서도 동일한 callbackUri를 리디렉션 URL로 구성해야 합니다.
   * `defaultConnectionName`: 이전 단계에서 OIDC 연결에 대해 정의된 것과 동일한 이름으로 구성합니다.
   * `pkceEnabled`: 권한 부여 코드 플로우에서 PKCE(Proof Key for Code Exchange)가 `true`입니다.
   * `idp`: [OAK 외부 ID 공급자](https://jackrabbit.apache.org/oak/docs/security/authentication/identitymanagement.html)의 이름입니다. 서로 다른 OAK IdP는 사용자 또는 그룹을 공유할 수 없습니다.

### SlingUserInfoProcessor 구성 {#configure-slinguserinfoprocessor}

1. 구성 파일을 생성합니다. 이 예시에서는 `org.apache.sling.auth.oauth_client.impl.SlingUserInfoProcessorImpl~azure.cfg.json`을 사용합니다. `azure` 접미사는 고유 식별자여야 합니다. 아래 구성 파일의 예제를 확인해 보십시오.

   ```
   {
      "groupsInIdToken":true,
      "groupsClaimName": "groups",
      "connection":"azure",
      "storeAccessToken": false,
      "storeRefreshToken": false,
      "idpNameInPrincipals": true
   }
   ```

1. 그런 다음 해당 속성을 다음과 같이 구성합니다.
   * `groupsInIdToken`: 그룹이 ID 토큰으로 전송되면 true로 설정합니다. 값이 false이거나 지정되지 않은 경우 그룹은 UserInfo 엔드포인트에서 읽습니다.
   * `groupsClaimName`: AEM에 동기화할 그룹을 포함하는 클레임의 이름입니다.
   * `connection`: 이전 단계에서 OIDC 연결에 대해 정의된 것과 동일한 이름으로 구성합니다.
   * `storeAccessToken`: 액세스 토큰을 저장소에 저장해야 하는 경우 true입니다. 기본적으로 false입니다. AEM이 동일한 IdP로 보호되는 외부 서버에 저장된 사용자를 대신하여 리소스에 액세스해야 하는 경우에만 true로 설정합니다.
   * `storeRefreshToken`: 새로 고침 토큰을 저장소에 저장해야 하는 경우 true입니다. 기본적으로 false입니다. AEM이 동일한 IdP로 보호되는 외부 서버에 저장된 사용자 대신 리소스에 액세스해야 하고 IdP에서 토큰을 새로 고쳐야 하는 경우에만 true로 설정합니다.
   * `idpNameInPrincipals`: true로 설정하면 IdP의 이름이 &#39;;&#39;로 구분된 사용자 및 그룹 주체에 접미사로 추가됩니다. 예를 들어 IdP 이름이 `azure-idp`이고 사용자 이름이 `john.doe`인 경우 oak에 저장된 보안 주체는 `john.doe;azure-idp`이(가) 됩니다. 이 기능은 여러 IdP가 oak에 구성되어 다른 IdP에서 오는 동일한 이름의 사용자 또는 그룹 간의 충돌을 방지할 때 유용합니다. Saml과 같은 다른 인증 처리기에서 만든 사용자 또는 그룹과의 충돌을 방지하기 위해 설정할 수도 있습니다.
액세스 토큰 및 새로 고침 토큰은 AEM 마스터 키로 암호화되어 저장됩니다.


### 동기화 핸들러 구성 {#configure-the-synchronization-handler}

Oak에서 인증된 사용자를 동기화하려면 하나 이상의 동기화 핸들러를 구성해야 합니다. 자세한 내용은 [이 페이지](https://jackrabbit.apache.org/oak/docs/security/authentication/external/defaultusersync.html)를 참조하십시오.

이름이 `org.apache.jackrabbit.oak.spi.security.authentication.external.impl.DefaultSyncHandler~azure.cfg.json`인 파일을 생성합니다. **azure** 접미사는 고유 식별자여야 합니다. 해당 속성을 구성하는 방법에 대한 자세한 내용은 [Oak 사용자 및 그룹 동기화 설명서](https://jackrabbit.apache.org/oak/docs/security/authentication/external/defaultusersync.html)를 참조하십시오. 아래에서 구성 예제를 찾을 수 있습니다.

```
{
  "user.expirationTime":"1h",
  "user.membershipExpTime":"1h",
  "group.expirationTime": "1d"
  "user.propertyMapping":[
    "profile/givenName=profile/given_name",
    "profile/familyName=profile/family_name",
    "rep:fullname=profile/name",
    "profile/email=profile/email",
    "access_token=access_token",
    "refresh_token=refresh_token"
  ],
  "user.pathPrefix":"azure",
  "handler.name":"azure"
}
```

개발 중에 만료 시간을 낮은 값(예: 1초)으로 줄여 oak에서 사용자 및 그룹 동기화 테스트 속도를 높일 수 있습니다.
DefaultSyncHandler에서 구성할 수 있는 가장 관련성 있는 속성은 다음과 같습니다. Cloud Service에서는 항상 동적 그룹 멤버십을 활성화해야 합니다.

| 속성 이름 | 메모 | 제안 값 |
|---|---|---|
| `user.expirationTime` | 동기화된 사용자가 만료될 때까지의 기간입니다. 사용자는 만료 시간 이후에만 동기화됩니다. | 1시간 |
| `user.membershipExpTime` | 동기화된 사용자 멤버십이 만료될 때까지의 기간입니다. 사용자 멤버십은 만료 시간 이후에만 동기화됩니다. | 1시간 |
| `user.dynamicMembership` | 동적 그룹 멤버십을 활성화하는 것이 좋습니다. | true |
| `user.enforceDynamicMembership` | 동적 그룹 멤버십을 활성화하는 것이 좋습니다. | true |
| `group.dynamicGroups` | 동적 그룹을 활성화하는 것이 좋습니다. | true |
| user.propertyMapping | 제공된 `UserInfoProcessor` 구현은 일부 속성만 동기화합니다. 수정 및 사용자 정의할 수 있습니다. | <code>&quot;profile/givenName=profile/given_name&quot;,</code><br><code>&quot;profile/familyName=profile/family_name&quot;,</code><br><code>&quot;rep:fullname=profile/name&quot;,</code><br><code>&quot;profile/email=profile/email&quot;,</code><br><code>&quot;access_token=access_token&quot;,</code><br><code>&quot;refresh_token=refresh_token&quot;</code> |
| `user.membershipNestingDepth` | 멤버십 관계가 동기화될 때 그룹 중첩의 최대 깊이를 반환합니다. 값이 0이면 그룹 멤버십 조회가 효과적으로 비활성화됩니다. 값이 1이면 사용자의 직접 그룹만 추가됩니다. 이 값은 사용자의 멤버십 계보를 동기화할 때만 영향을 미치고 개별 그룹을 동기화할 때는 영향을 미치지 않습니다. | 1 |

### 외부 로그인 모듈 구성 {#configure-the-external-login-module}

마지막으로 외부 로그인 모듈을 구성해야 합니다.

1. 이름이 `org.apache.jackrabbit.oak.spi.security.authentication.external.impl.ExternalLoginModuleFactory~azure.cfg.json`인 파일을 생성합니다. 아래의 구성 예제를 확인해 보십시오.

   ```
   {
    "sync.handlerName":"azure",
    "idp.name":"azure-idp"
   }
   ```

1. 해당 속성을 다음과 같이 구성합니다.

   * `sync.handlerName`: 이전에 정의된 동기화 핸들러의 이름
   * `idp.name`: OIDC 인증 핸들러에 정의된 OAK ID 공급자

### 선택 사항: 사용자 정의 UserInfoProcessor 구현 {#implement-a-custom-userinfoprocessor}

사용자는 ID 토큰으로 인증되고 추가 특성은 IdP에 대해 정의된 `userInfo` 끝점에서 가져옵니다. `UserInfoProcessor`은(는) ID 공급자로부터 받은 데이터를 AEM이 사용자 동기화에 사용할 수 있는 자격 증명 및 특성으로 변환하는 역할을 합니다.

#### 사용자 지정 UserInfoProcessor를 만들 때 {#when-to-create-custom-userinfoprocessor}

기본 [SlingUserInfoProcessorImpl](https://github.com/apache/sling-org-apache-sling-auth-oauth-client/blob/master/src/main/java/org/apache/sling/auth/oauth_client/impl/SlingUserInfoProcessorImpl.java)은(는) 표준 OIDC 클레임 및 그룹 동기화를 처리합니다. 다음을 수행해야 하는 경우 사용자 지정 구현이 필요할 수 있습니다.

* ID 토큰 또는 UserInfo 응답에서 사용자 지정 클레임 추출 및 처리
* 클레임을 다른 특성 이름으로 변환 또는 매핑
* 중첩된 클레임에서 그룹 추출을 위한 사용자 지정 논리 구현
* 표준 OIDC 프로필의 일부가 아닌 사용자 속성을 더 추가합니다.
* 특정 사용 사례에 대한 액세스 토큰 처리 또는 토큰 새로 고침
* 외부 시스템과 통합하여 인증 중 사용자 데이터 보강

#### UserInfoProcessor 인터페이스 이해 {#understanding-userinfoprocessor-interface}

`UserInfoProcessor` 패키지의 `org.apache.sling.auth.oauth_client.spi` 인터페이스는 다음 두 가지 메서드를 정의합니다.

```java
public interface UserInfoProcessor {
    /**
     * Process the UserInfo and token response to create OIDC credentials
     *
     * @param userInfo - JSON response from the UserInfo endpoint (may be null)
     * @param tokenResponse - JSON response from the token endpoint
     * @param oidcSubject - The subject claim from the ID token
     * @param idp - The configured IDP name
     * @return OidcAuthCredentials containing user attributes and group memberships
     */
    @NotNull OidcAuthCredentials process(
        @Nullable String userInfo,
        @NotNull String tokenResponse,
        @NotNull String oidcSubject,
        @NotNull String idp
    );

    /**
     * @return The name of the OIDC connection this processor is associated with
     */
    @NotNull String connection();
}
```

반환된 `OidcAuthCredentials` 개체를 사용하면 다음을 수행할 수 있습니다.
* `setAttribute(key, value)`을(를) 통해 사용자 특성을 설정합니다. `DefaultSyncHandler` 속성 매핑을 기반으로 동기화됩니다.
* `addGroup(groupName)`을(를) 통해 그룹 멤버십을 추가하십시오. 이러한 그룹은 AEM에서 생성/동기화됩니다.

#### 예: 사용자 지정 UserInfoProcessor 구현 {#custom-userinfoprocessor-implementation}

다음은 사용자 지정 `UserInfoProcessor`을(를) 구현하는 방법을 보여 주는 전체 예입니다.

```java
package com.mycompany.aem.auth;

import java.nio.charset.StandardCharsets;
import java.util.Base64;

import org.apache.sling.auth.oauth_client.spi.OidcAuthCredentials;
import org.apache.sling.auth.oauth_client.spi.UserInfoProcessor;
import org.jetbrains.annotations.NotNull;
import org.jetbrains.annotations.Nullable;
import org.osgi.service.component.annotations.Activate;
import org.osgi.service.component.annotations.Component;
import org.osgi.service.metatype.annotations.AttributeDefinition;
import org.osgi.service.metatype.annotations.Designate;
import org.osgi.service.metatype.annotations.ObjectClassDefinition;
import org.slf4j.Logger;
import org.slf4j.LoggerFactory;

import com.google.gson.JsonObject;
import com.google.gson.JsonParser;

/**
 * Custom UserInfoProcessor that extracts additional claims from the ID token
 * and adds custom user attributes and group memberships.
 */
@Component(service = UserInfoProcessor.class, property = {"service.ranking:Integer=50"})
@Designate(ocd = CustomUserInfoProcessor.Config.class, factory = true)
public class CustomUserInfoProcessor implements UserInfoProcessor {

    private static final Logger logger = LoggerFactory.getLogger(CustomUserInfoProcessor.class);

    @ObjectClassDefinition(name = "Custom UserInfo Processor")
    @interface Config {
        @AttributeDefinition(name = "Connection Name", description = "OIDC Connection Name")
        String connection();
    }

    private final String connection;

    @Activate
    public CustomUserInfoProcessor(Config config) {
        this.connection = config.connection();
        logger.info("CustomUserInfoProcessor activated for connection: {}", connection);
    }

    @Override
    public @NotNull OidcAuthCredentials process(
            @Nullable String userInfo,
            @NotNull String tokenResponse,
            @NotNull String oidcSubject,
            @NotNull String idp) {

        // Parse the token response to extract tokens
        JsonObject tokenJson = JsonParser.parseString(tokenResponse).getAsJsonObject();
        String accessToken = tokenJson.has("access_token") ?
            tokenJson.get("access_token").getAsString() : null;
        String idToken = tokenJson.has("id_token") ?
            tokenJson.get("id_token").getAsString() : null;

        logger.debug("Processing authentication for subject: {}", oidcSubject);

        // Decode and extract claims from ID Token
        JsonObject claims = null;
        if (idToken != null) {
            claims = decodeJwtPayload(idToken);
            logger.debug("Extracted claims from ID token: {}", claims);
        }

        // Create credentials object
        OidcAuthCredentials credentials = new OidcAuthCredentials(oidcSubject, idp);
        credentials.setAttribute(".token", "");

        // Extract standard profile attributes
        if (claims != null) {
            // Standard OIDC claims
            setAttributeIfPresent(credentials, claims, "given_name", "profile/given_name");
            setAttributeIfPresent(credentials, claims, "family_name", "profile/family_name");
            setAttributeIfPresent(credentials, claims, "email", "profile/email");
            setAttributeIfPresent(credentials, claims, "name", "profile/name");

            // Custom claims from your IdP
            setAttributeIfPresent(credentials, claims, "department", "profile/department");
            setAttributeIfPresent(credentials, claims, "employee_id", "profile/employeeId");
            setAttributeIfPresent(credentials, claims, "job_title", "profile/jobTitle");
        }

        // Extract group memberships from claims
        if (claims != null && claims.has("groups")) {
            if (claims.get("groups").isJsonArray()) {
                claims.get("groups").getAsJsonArray().forEach(group -> {
                    credentials.addGroup(group.getAsString());
                });
            }
        }

        // Optionally store tokens if needed for later API calls
        // Note: Only store tokens if your application needs to call external APIs
        // on behalf of the user. Tokens are encrypted before storage.
        if (accessToken != null) {
            credentials.setAttribute("access_token", accessToken);
        }

        return credentials;
    }

    @Override
    public @NotNull String connection() {
        return connection;
    }

    /**
     * Helper method to set attribute if present in claims
     */
    private void setAttributeIfPresent(OidcAuthCredentials credentials,
                                      JsonObject claims,
                                      String claimName,
                                      String attributeName) {
        if (claims.has(claimName) && !claims.get(claimName).isJsonNull()) {
            String value = claims.get(claimName).getAsString();
            if (value != null && !value.isEmpty()) {
                credentials.setAttribute(attributeName, value);
            }
        }
    }

    /**
     * Decode JWT payload (middle part) to extract claims
     */
    private JsonObject decodeJwtPayload(String jwt) {
        try {
            String[] parts = jwt.split("\\.");
            if (parts.length != 3) {
                logger.warn("Invalid JWT format");
                return null;
            }

            // Decode the payload (second part)
            String payload = parts[1];
            // Add padding if needed
            payload = payload + "====".substring(0, (4 - payload.length() % 4) % 4);
            // Replace URL-safe characters
            payload = payload.replace('-', '+').replace('_', '/');

            byte[] decoded = Base64.getDecoder().decode(payload);
            String json = new String(decoded, StandardCharsets.UTF_8);
            return JsonParser.parseString(json).getAsJsonObject();
        } catch (Exception e) {
            logger.error("Failed to decode JWT payload", e);
            return null;
        }
    }
}
```

#### 구성 {#custom-userinfoprocessor-configuration}

`UserInfoProcessor` 아래 AEM 프로젝트에서 사용자 지정 `ui.config/src/main/content/jcr_root/apps/myapp/osgiconfig/config.publish/`에 대한 구성 파일을 만듭니다.

**com.mycompany.aem.auth.CustomUserInfoProcessor~azure.cfg.json**

```json
{
  "connection": "azure"
}
```

구성은 `OidcConnectionImpl` 구성에 정의된 연결 이름과 일치해야 합니다. `service.ranking` 주석의 `@Component` 속성(예제에서 `50`(으)로 설정됨)은 동일한 연결에 대해 여러 프로세서가 등록되어 있는 경우 우선 순위를 결정합니다. 순위가 `SlingUserInfoProcessorImpl`인 기본 `0`보다 높은 순위가 우선합니다.

#### 종속성 {#custom-userinfoprocessor-dependencies}

핵심 모듈의 `pom.xml`에 다음 종속성을 추가하십시오.

```xml
<dependency>
    <groupId>org.apache.sling</groupId>
    <artifactId>org.apache.sling.auth.oauth-client</artifactId>
    <version>0.1.7</version>
    <scope>provided</scope>
</dependency>
<dependency>
    <groupId>com.google.code.gson</groupId>
    <artifactId>gson</artifactId>
    <version>2.8.9</version>
    <scope>provided</scope>
</dependency>
```

#### 속성을 DefaultSyncHandler와 동기화 {#synchronizing-custom-attributes}

사용자 지정 특성이 JCR의 사용자 노드에 유지되도록 하려면 속성 매핑을 포함하도록 `DefaultSyncHandler` 구성을 업데이트하십시오.

**org.apache.jackrabbit.oak.spi.security.authentication.external.impl.DefaultSyncHandler~azure.cfg.json**

```json
{
  "user.expirationTime": "1h",
  "user.membershipExpTime": "1h",
  "user.propertyMapping": [
    "profile/givenName=profile/given_name",
    "profile/familyName=profile/family_name",
    "rep:fullname=profile/name",
    "profile/email=profile/email",
    "profile/department=profile/department",
    "profile/employeeId=profile/employeeId",
    "profile/jobTitle=profile/jobTitle",
    "access_token=access_token"
  ],
  "user.pathPrefix": "azure",
  "handler.name": "azure"
}
```

형식은 `jcrPropertyPath=credentialAttributeName`입니다. 왼쪽은 속성이 `/home/users` 아래의 사용자 노드에 저장되는 위치이고 오른쪽은 `UserInfoProcessor`을(를) 사용하여 `credentials.setAttribute()`에서 설정한 특성 이름과 일치합니다.

#### 배포 및 테스트 {#custom-userinfoprocessor-deployment}

1. 사용자 지정 **이(가) 포함된 AEM 프로젝트를**&#x200B;빌드 및 배포`UserInfoProcessor`:

   ```bash
   mvn clean install -PautoInstallPackage
   ```

2. **의 OSGi 콘솔에서**&#x200B;등록 확인`/system/console/components`:
   * 사용자 정의 프로세서 클래스 이름 검색
   * 구성 요소가 활성 상태이고 연결 구성이 올바른지 확인합니다.

3. **인증 흐름 테스트**:
   * `OidcAuthenticationHandler`에 구성된 보호된 경로에 액세스
   * 인증에 성공하면 `/home/users/<prefix>/<username>`의 CRXDE에서 사용자 노드를 확인하십시오.
   * 사용자 지정 특성이 동기화되었는지 확인
   * `/home/groups`의 그룹 멤버십 확인

4. 문제를 해결하려면 **디버그 로깅을 사용**&#x200B;합니다.

   ```
   Logger: com.mycompany.aem.auth
   Log Level: DEBUG
   ```

#### 모범 사례 {#custom-userinfoprocessor-best-practices}

* **토큰 저장소 최소화**: 응용 프로그램에서 사용자를 대신하여 외부 서비스에 API를 호출해야 하는 경우에만 액세스 토큰을 저장하거나 토큰을 새로 고치십시오. 토큰은 암호화되지만 여전히 오버헤드가 추가됩니다.
* **클레임 유효성 검사**: 처리하기 전에 클레임이 존재하고 null이 아닌지 항상 확인하십시오.
* **오류 처리**: 오류를 적절하게 기록하지만 선택적 클레임이 누락된 경우에도 인증 흐름이 완료될 수 있는지 확인하십시오.
* **성능**: 모든 인증에서 실행되므로 처리 논리를 단순하게 유지합니다.
* **보안**: 전체 토큰 또는 사용자 암호와 같은 중요한 정보를 기록하지 마십시오. 디버깅을 위해 토큰을 로깅할 경우 `substring()`을(를) 사용합니다.
* **테스트**: 모든 클레임 변형이 올바르게 처리되도록 IdP의 다양한 사용자 프로필을 사용하여 테스트합니다.

### 외부 그룹에 대한 ACL 구성 {#configure-acl-for-external-groups}

사용자가 OIDC를 통해 인증되면 해당 그룹 멤버십은 일반적으로 외부 ID 공급자로부터 동기화됩니다.
이러한 외부 그룹은 AEM 저장소에서 동적으로 생성되지만 액세스 제어 항목과 자동으로 연결되지는 않습니다.
사용자에게 적절한 권한이 있는지 확인하려면 이러한 그룹에 대해 ACL(액세스 제어 목록)을 명시적으로 정의해야 합니다.

두 가지 기본 접근 방식을 사용할 수 있습니다.

### 옵션 1 - 로컬 그룹

외부 그룹은 이미 필요한 ACL이 있는 로컬 그룹의 멤버로 추가할 수 있습니다.

* 외부 그룹은 저장소에 있어야 합니다. 이 그룹은 해당 그룹에 속한 사용자가 처음으로 로그인할 때 자동으로 발생합니다.
* 로컬 그룹이 작성자 및 게시 환경 모두에 존재하므로 CUG(폐쇄형 사용자 그룹)를 사용 중인 경우 이 옵션이 일반적으로 선호됩니다.

### 옵션 2 - RepoInit를 통해 외부 그룹에 직접 ACL 사용

ACL은 RepoInit 스크립트를 사용하여 외부 그룹에 직접 적용할 수 있습니다.

* 이러한 접근법은 더욱 효율적이며 CUG들이 사용되지 않을 때 선호된다.
* 다음 예제에서는 외부 그룹에 읽기 권한을 할당하는 RepoInit 구성을 보여 줍니다. `ignoreMissingPrincipal` 옵션을 사용하면 그룹이 저장소에 아직 없는 경우에도 ACL을 만들 수 있습니다.

  ```
  {
    "scripts":[
      "set ACL for \"my-group;my-idp\"  (ACLOptions=ignoreMissingPrincipal)\r\n  allow jcr:read on /content/wknd/us/en/magazine\r\nend"
    ]
  }    
  ```

>[!NOTE]
>AEM 권한 UI를 사용하여 그룹 주도자에게 할당된 ACL을 검사할 수 있습니다

## 예: Azure Active Directory를 사용하여 OIDC 인증 구성

### Azure Active Directory에서 새 애플리케이션 구성 {#configure-a-new-application-in-azure-ad}

1. [Azure Active Directory 설명서](https://learn.microsoft.com/en-us/power-pages/security/authentication/openid-settings#create-an-app-registration-in-azure)에 따라 Azure Active Directory에서 새 애플리케이션을 만듭니다. 애플리케이션 개요를 자세히 설명하는 화면이 어떻게 표시되는지 아래에서 확인해 보십시오.

   ![애플리케이션 개요](/help/security/assets/odic-application-overview.png)

1. 그룹 또는 애플리케이션 역할이 필요한 경우 [설명서](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-use-app-roles-customers)에 따라 애플리케이션에 대해 활성화하고 ID 토큰으로 전송합니다. 아래는 구성된 그룹의 예입니다.

![OIDC 클레임 토큰 ID](/help/security/assets/oidc-claim-id-token.png)

1. 이전에 문서화된 단계를 따라 필수 구성 파일을 생성합니다. Azure AD에 대한 구체적인 예는 다음과 같습니다.
   * Oidc 연결, 인증 핸들러 및 DefaultSyncHandler의 이름을 `azure`로 정의합니다.
   * 웹 사이트 url은 `www.mywebsite.com`입니다.
   * `/content/wknd/us/en/adventures` 그룹의 인증된 사용자만 액세스할 수 있는 `adventures` 경로를 보호합니다.
   * 테넌트는 `tennat-id`입니다.
   * 클라이언트 ID는 `client-id`입니다.
   * 암호는 `secret`입니다.
   * 그룹은 `groups`라는 클레임의 ID 토큰으로 전송됩니다.

### org.apache.sling.auth.oauth_client.impl.OidcConnectionImpl~azure.cfg.json

```
{
  "name":"azure",
  "scopes":[
    openid", "User.Read", "profile", "email"
  ],
  "baseUrl":"https://login.microsoftonline.com/tenant-id/v2.0",
  "clientId":"client-id",
  "clientSecret":"secret"
}
```

### org.apache.sling.auth.oauth_client.impl.OidcAuthenticationHandler~azure.cfg.json

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

### org.apache.jackrabbit.oak.spi.security.authentication.external.impl.ExternalLoginModuleFactory~azure.cfg.json

```
{
  "sync.handlerName":"azure",
  "idp.name":"azure"
}
```

### org.apache.jackrabbit.oak.spi.security.authentication.external.impl.DefaultSyncHandler~azure.cfg.json

```
{
  "user.expirationTime":"1h",
  "user.membershipExpTime":"1h",
  "group.expirationTime": "1d"
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

### org.apache.sling.jcr.repoinit.RepositoryInitializer~azure.cfg.json

```
{
  "scripts":[
    "set ACL for \"adventures;azure\"  (ACLOptions=ignoreMissingPrincipal)\r\n  allow jcr:read on /content/wknd/us/en/adventures\r\nend"
  ]
}
```

### org.apache.sling.auth.oauth_client.impl.SlingUserInfoProcessorImpl~azure.cfg.json

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

Microsoft Azure Portal의 엔터프라이즈 애플리케이션에 대한 그룹을 구성하려면 **엔터프라이즈 애플리케이션**&#x200B;에서 애플리케이션을 검색하고 그룹을 추가해야 합니다. <!-- Alexandru: this bit cound be clearer-->

![OIDC 그룹 추가](/help/security/assets/oidc-ad-additional-info.png)

ID 토큰에서 그룹 클레임을 활성화하려면 Microsoft Azure Portal의 **토큰 구성** 섹션에 클레임을 추가합니다. <!-- Alexandru: this bit cound be clearer as well-->

![OIDC 클레임 토큰 ID](/help/security/assets/oidc-claim-id-token.png)

`SlingUserInfoProcessor`의 구성은 아래 예시와 같이 수정되어야 합니다.

수정해야 하는 파일 이름은 `org.apache.sling.auth.oauth_client.impl.SlingUserInfoProcessorImpl.cfg.json`입니다. 콘텐츠는 다음과 같이 구성되어야 합니다.

```
{
  "connection": "azure",
  "groupsInIdToken": "true",
  "storeAccessToken": "false",
  "storeRefreshToken": "false"
}
```

## 인증 후 사용자 지정 리디렉션 {#custom-redirect-after-authentication}

기본적으로 OIDC 인증에 성공하면 사용자가 원래 요청한 URL로 다시 리디렉션됩니다. 그러나 `redirect` 쿼리 매개 변수를 사용하여 이 동작을 사용자 지정할 수 있습니다.

### 리디렉션 매개 변수 사용

인증을 시작할 때 인증 요청에 `redirect` 매개 변수를 추가하여 사용자 지정 리디렉션 URL을 지정할 수 있습니다.

```
/content/wknd/us/en/adventures?redirect=/content/wknd/us/en/welcome
```

이 예제에서는 인증에 성공하면 사용자가 원래 요청된 페이지가 아닌 `/content/wknd/us/en/welcome`(으)로 리디렉션됩니다.

### 보안 제한

보안상의 이유로 `redirect` 매개 변수에는 다음과 같은 제한이 있습니다.

* **상대 경로여야 함**: 리디렉션 URL은 `/`(예: `/content/mysite/dashboard`)로 시작해야 합니다.
* **사이트 간 리디렉션 없음**: 절대 URL(예: `https://external-site.com`)은 허용되지 않습니다.
* **프로토콜 관련 URL 없음**: 프로토콜 관련 리디렉션을 방지하기 위해 `//`(으)로 시작하는 URL이 거부되었습니다.

잘못된 리디렉션 URL이 제공되면 인증이 실패하고 오류가 발생합니다.

### 예시 사용 사례

1. **로그인 후 시작 페이지**: 첫 로그인 후 사용자를 개인 설정된 시작 페이지로 리디렉션합니다.

   ```
   /content/mysite/secure-area?redirect=/content/mysite/welcome
   ```

2. **대시보드 리디렉션**: 인증 후 사용자를 특정 대시보드로 보냅니다.

   ```
   /content/mysite/login?redirect=/content/mysite/user/dashboard
   ```

3. **딥링크**: 사용자가 인증한 후 특정 리소스에 액세스할 수 있도록 허용합니다.

   ```
   /content/mysite/protected?redirect=/content/mysite/protected/specific-document
   ```

## Saml Authentication Handler에서 Oidc Authentication Handler로 마이그레이션하는 방법

AEM이 이미 SAML 인증 핸들러로 구성되어 있고 사용자가 [데이터 동기화](https://experienceleague.adobe.com/ko/docs/experience-manager-cloud-service/content/sites/authoring/personalization/user-and-group-sync-for-publish-tier#data-synchronization)가 활성화된 저장소에 있는 경우 원래 SAML 사용자와 새 OIDC 사용자 간에 충돌이 발생할 수 있습니다.

1. [OidcAuthenticationHandler](#configure-oidc-authentication-handler)를 구성하고 `idpNameInPrincipals`SlingUserInfoProcessor[&#x200B; 구성에서 &#x200B;](#configure-slinguserinfoprocessor)을(를) 사용하도록 설정하십시오.
1. 외부 그룹에 대해 [ACL을 설정](#configure-acl-for-external-groups)합니다.
1. 사용자로부터 로그인하면 saml 인증 핸들러로 만든 이전 사용자를 삭제할 수 있습니다.

>[!NOTE]
>SAML 인증 처리기가 비활성화되고 OIDC 인증 처리기가 활성화되면 [데이터 동기화](https://experienceleague.adobe.com/ko/docs/experience-manager-cloud-service/content/sites/authoring/personalization/user-and-group-sync-for-publish-tier#data-synchronization)가 활성화되지 않으면 기존 세션이 유효하지 않게 됩니다. 사용자를 다시 인증해야 하므로 저장소에 새 OIDC 사용자 노드가 생성됩니다.

