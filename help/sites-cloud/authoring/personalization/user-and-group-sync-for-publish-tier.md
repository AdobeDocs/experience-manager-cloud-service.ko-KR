---
title: '등록, 로그인 및 사용자 프로필 '
description: AEM as a Cloud Service에 대한 등록, 로그인, 사용자 데이터 및 그룹 동기화에 대해 알아봅니다.
exl-id: a991e710-a974-419f-8709-ad86c333dbf8
source-git-commit: c49a70b4048acc4e925c69b7ebbedbf8779bbbc0
workflow-type: tm+mt
source-wordcount: '1174'
ht-degree: 1%

---

# 등록, 로그인 및 사용자 프로필 {#registration-login-and-userprofile}

## 소개 {#introduction}

웹 애플리케이션에서는 최종 사용자가 웹 사이트에 등록할 수 있도록 계정 관리 기능을 제공하는 경우가 있으며, 이 기능은 사용자 데이터 정보를 그대로 유지하여 나중에 로그인하고 일관된 경험을 제공할 수 있습니다. 이 문서에서는 AEM as a Cloud Service에 대한 다음 개념에 대해 설명합니다.

* 등록
* 로그인
* 사용자 프로필 데이터 저장
* 그룹 멤버십
* 데이터 동기화

>[!IMPORTANT]
>
>이 문서에 설명된 기능이 작동하려면 사용자 데이터 동기화 기능을 활성화해야 합니다. 이 경우 적절한 프로그램 및 환경을 나타내는 고객 지원 요청을 수행해야 합니다. 활성화되지 않은 경우 사용자 정보가 사라지기 전에 짧은 기간(1~24시간) 동안 유지됩니다.

## 등록 {#registration}

최종 사용자가 AEM 애플리케이션에서 계정에 등록하면 AEM 게시 서비스에 사용자 계정이 생성되며, 이 계정은 아래의 사용자 리소스에 반영됩니다 `/home/users` 를 클릭합니다.

아래에 설명된 대로 등록을 구현하는 방법에는 두 가지가 있습니다.

### AEM 관리 {#aem-managed-registration}

사용자 지정 등록 코드는 최종 사용자의 사용자 이름과 암호를 최소한으로 사용하고, 이 사용자 레코드를 AEM에서 만들어 로그인 중에 인증할 수 있습니다. 일반적으로 다음 단계는 이 등록 메커니즘을 구성하는 데 사용됩니다.

1. 등록 정보를 수집하는 사용자 지정 AEM 구성 요소를 표시합니다
1. 제출 시 적절하게 제공된 서비스 사용자가
   1. UserManager API 중 하나를 사용하여 기존 사용자가 아직 존재하지 않는지 확인합니다. `findAuthorizables()` 메서드
   1. UserManager API 중 하나를 사용하여 사용자 레코드를 만듭니다 `createUser()` 메서드
   1. Authorizable 인터페이스의 `setProperty()` 메서드
1. 사용자가 이메일의 유효성을 검사해야 하는 등의 선택적 플로우입니다.

### 외부 {#external-managed-registration}

경우에 따라 등록 또는 사용자 생성이 AEM 외부의 인프라에서 이전에 발생한 경우가 있습니다. 이 시나리오에서는 로그인 중에 사용자 레코드가 AEM에 생성됩니다.

## 로그인 {#login}

최종 사용자가 AEM 게시 서비스에 등록되면 이러한 사용자는 인증된 액세스(AEM 인증 메커니즘 사용)와 프로필 데이터와 같은 지속적인 사용자 특정 데이터를 얻기 위해 로그인할 수 있습니다.

## 구현 {#implementation}

다음 두 가지 방법으로 로그인을 구현할 수 있습니다.

### AEM 관리 {#aem-managed-implementation}

고객은 고유한 사용자 지정 구성 요소를 작성할 수 있습니다. 자세한 내용을 알아보려면 다음 사항을 숙지하십시오.

* 다음 [Sling 인증 프레임워크](https://sling.apache.org/documentation/the-sling-engine/authentication/authentication-framework.html)
* 그리고 [AEM Community 전문가 세션 요청](http://bit.ly/ATACEFeb15) 로그인 기본 정보.

### ID 공급자와의 통합 {#integration-with-an-idp}

고객은 사용자를 인증하는 IdP(ID 공급자)와 통합할 수 있습니다. 통합 기술에는 아래에 설명된 대로 SAML 및 OAuth/SSO가 포함됩니다.

**SAML 기반**

고객은 선호하는 SAML IdP를 통해 SAML 기반 인증을 사용할 수 있습니다. AEM에서 IdP를 사용하는 경우, IdP는 최종 사용자의 자격 증명을 인증하고 AEM으로 사용자 인증을 중개하고, 필요에 따라 AEM에서 사용자 레코드를 만들고, SAML 검증에 설명된 대로 AEM에서 사용자 그룹 구성원을 관리할 책임이 있습니다.

>[!NOTE]
>
>사용자 자격 증명의 초기 인증만 IdP에 의해 인증되고, 쿠키를 사용할 수 있는 한 AEM 로그인 토큰 쿠키를 사용하여 AEM에 대한 후속 요청이 수행됩니다.

에 대한 자세한 내용은 설명서 를 참조하십시오. [SAML 2.0 인증 핸들러](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/authentication/saml-2-0.html).

**OAuth/SSO**

자세한 내용은 [SSO(Single Sign On) 설명서](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/configuring/single-sign-on.html) AEM SSO 인증 핸들러 서비스 사용에 대한 정보를 참조하십시오.

다음 `com.adobe.granite.auth.oauth.provider` 원하는 OAuth 공급자를 사용하여 인터페이스를 구현할 수 있습니다.

### 고정 세션 및 캡슐화된 토큰 {#sticky-sessions-and-encapsulated-tokens}

AEM as a Cloud Service에는 쿠키 기반 고정 세션이 활성화되어 최종 사용자가 각 요청 시 동일한 게시 노드로 라우팅됩니다. 성능을 향상시키기 위해 캡슐화된 토큰 기능이 기본적으로 활성화되어 있으므로 저장소의 사용자 레코드를 각 요청에서 참조할 필요가 없습니다. 최종 사용자에게 친화성이 있는 게시 노드를 바꾸면 아래 데이터 동기화 섹션에 설명된 대로 새 게시 노드에서 사용자 ID 레코드를 사용할 수 있습니다.

## 사용자 프로필 {#user-profile}

데이터의 특성에 따라 데이터를 유지하는 방법은 다양합니다.

### AEM 저장소 {#aem-repository}

사용자 프로필 정보는 다음 두 가지 방법으로 작성하고 읽을 수 있습니다.

* 서버측 과 `com.adobe.granite.security.user` 인터페이스 UserPropertiesManager 인터페이스로, `/home/users`. 사용자당 고유한 페이지가 캐시되지 않았는지 확인합니다.
* 에 설명된 대로 ContextHub를 사용하는 클라이언트측 [설명서](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/personalization/contexthub.html?lang=en#personalization).

### 타사 데이터 저장소 {#third-party-data-stores}

최종 사용자 데이터는 CRM과 같은 타사 공급업체로 전송하고, 사용자가 AEM에 로그인할 때 API를 통해 검색되고, AEM 사용자의 프로필 노드에서 유지(또는 새로 고침)되며, 필요에 따라 AEM에서 사용할 수 있습니다.

AEM에서 프로필 속성을 검색하기 위해 타사 서비스에 대한 실시간 액세스가 가능하도록 하지만, 이렇게 해도의 요청 처리에 실질적으로 영향을 주지 않도록 하는 것이 중요합니다.

## 권한(닫힌 사용자 그룹) {#permissions-closed-user-groups}

폐쇄된 사용자 그룹(CUG)이라고도 하는 게시 계층 액세스 정책은 AEM 작성자에 [여기에서 설명합니다.](https://experienceleague.adobe.com/docs/experience-manager-65/administering/security/cug.html?lang=en#applying-your-closed-user-group-to-content-pages). 일부 사용자로부터 웹 사이트의 특정 섹션이나 페이지를 제한하려면 여기에 설명된 대로 AEM 작성자를 사용하여 필요에 따라 CUG를 적용하고 게시 계층에 복제합니다.

* 사용자가 SAML을 사용하여 ID 공급자(IdP)로 인증하여 로그인하는 경우 인증 처리기는 사용자의 그룹 멤버십(게시 계층의 CUG와 일치해야 함)을 식별하고 저장소 레코드를 통해 사용자와 그룹 간의 연결을 유지합니다
* IdP 통합 없이 로그인이 완료되면 사용자 지정 코드가 동일한 저장소 구조 관계를 적용할 수 있습니다.

로그인에 관계없이 사용자 지정 코드가 조직의 고유한 요구 사항에 따라 사용자 그룹 멤버십을 필요에 따라 유지 및 관리할 수도 있습니다.

## 데이터 동기화 {#data-synchronization}

웹 사이트 최종 사용자는 모든 웹 페이지 요청에서 일관된 경험을 사용하거나 다른 브라우저를 사용하여 로그인할 때에도 게시 계층 구조의 다른 서버 노드로 전달됩니다. AEM은 빠르게 동기화하여 이 작업을 완수합니다 `/home` 게시 계층의 모든 노드에 대한 폴더 계층 구조(사용자 프로필 정보, 그룹 멤버십 등).

다른 AEM 솔루션과 달리, AEM as a Cloud Service의 사용자 및 그룹 멤버십 동기에서는 포인트 투 포인트 메시징 접근 방식을 사용하지 않고, 고객 구성이 필요하지 않은 게시 구독 접근 방식을 구현합니다.

>[!NOTE]
>
>기본적으로 사용자 프로필 및 그룹 멤버십 동기화는 활성화되지 않으므로 데이터가 게시 계층에서 동기화되거나 영구적으로 유지되지 않습니다. 이 기능을 사용하려면 해당 프로그램 및 환경을 나타내는 요청을 고객 지원 센터에 보내십시오.

## 캐시 고려 사항 {#cache-considerations}

인증된 HTTP 요청은 요청 응답의 일부로 사용자별 상태가 전송될 수 있으므로 CDN 및 Dispatcher 모두에서 캐시하기 어려울 수 있습니다. 인증된 요청을 의도치 않게 캐싱하고 이를 다른 요청 브라우저에 제공하는 경우 잘못된 경험이 발생하거나 보호되거나 사용자 데이터가 유출될 수 있습니다.

사용자별 응답을 지원하면서 요청에 대한 높은 캐시 능력을 유지하는 방법은 다음과 같습니다.

* AEM Dispatcher 권한 구분 캐싱
* Sling 동적 포함
* AEM ContextHub
