---
title: 등록, 로그인 및 사용자 프로필
description: AEM as a Cloud Service의 등록, 로그인, 사용자 데이터 및 그룹 동기화에 대해 알아봅니다.
exl-id: a991e710-a974-419f-8709-ad86c333dbf8
solution: Experience Manager Sites
feature: Authoring, Personalization
role: User
source-git-commit: 6719e0bcaa175081faa8ddf6803314bc478099d7
workflow-type: tm+mt
source-wordcount: '1343'
ht-degree: 64%

---

# 등록, 로그인 및 사용자 프로필 {#registration-login-and-userprofile}

## 소개 {#introduction}

웹 애플리케이션은 종종 최종 사용자가 웹 사이트에 등록할 수 있도록 하는 계정 관리 기능을 제공하는데, 이를 통해 최종 사용자는 사용자 데이터 정보를 유지하여 향후 손쉽게 로그인하고 일관된 경험을 누릴 수 있습니다. 이 문서에서는 다음과 같은 AEM as a Cloud Service에 대한 개념에 대해 설명합니다.

* 등록
* 로그인
* 사용자 프로필 데이터 저장
* 그룹 멤버십
* 데이터 동기화

## 등록 {#registration}

최종 사용자가 AEM 애플리케이션에 계정을 등록하면 JCR 저장소의 `/home/users` 아래에 있는 사용자 리소스에 반영된 사용자 계정이 AEM Publish 서비스에 생성됩니다.

아래 설명된 것처럼, 등록 구현에는 두 가지 접근 방식이 있습니다.

### AEM Managed {#aem-managed-registration}

사용자 정의 등록 코드를 작성하면 사용자 사용자 이름과 암호를 최소한으로 사용하고 AEM에서 로그인 중에 인증에 사용할 수 있는 사용자 레코드를 생성할 수 있습니다. 다음은 이러한 등록 메커니즘을 구성할 때 일반적으로 사용하는 단계입니다.

1. 등록 정보를 수집하는 사용자 정의 AEM 구성 요소 표시
1. 제출 후 올바르게 프로비저닝된 서비스 사용자가 다음 작업을 수행
   1. UserManager API의 `findAuthorizables()` 방법 중 하나를 사용하여 기존 사용자가 이미 존재하지 않는지 확인
   1. UserManager API의 `createUser()` 방법 중 하나를 사용하여 사용자 레코드 생성
   1. Authorizable 인터페이스의 `setProperty()` 방법을 사용하여 캡처된 프로필 데이터 유지
1. 선택적 플로우 (예: 사용자에게 이메일 유효성 확인 요구)

**필수 구성 요소:**

위에서 설명한 논리가 올바르게 작동하려면 다음을 제출하여 [데이터 동기화](#data-synchronization-data-synchronization)를 활성화하십시오.
적절한 프로그램 및 환경을 나타내는 고객 지원 센터 요청.

### 외부 {#external-managed-registration}

경우에 따라 등록 및 사용자가 이전에 AEM 외부 인프라에서 생성되었을 수 있습니다. 이러한 경우 사용자 레코드는 AEM에서 로그인 동안 생성됩니다.

## 로그인 {#login}

최종 사용자가 AEM Publish 서비스에 등록되면 이들 사용자는 로그인하여 AEM 인증 메커니즘을 사용하는 인증된 액세스와 더불어 프로필 데이터와 같은 사용자별 지속 데이터를 얻을 수 있습니다.

## 구현 {#implementation}

다음과 같은 두 가지 접근 방식을 통해 로그인을 구현할 수 있습니다.

### AEM Managed {#aem-managed-implementation}

고객은 사용자 정의 구성 요소를 작성할 수 있습니다. 자세한 내용은 다음을 참조하십시오.

* [Sling 인증 프레임워크](https://sling.apache.org/documentation/the-sling-engine/authentication/authentication-framework.html)
* 또한 로그인에 관련하여 [AEM 커뮤니티 전문가 세션에 문의](https://bit.ly/ATACEFeb15)할 수도 있습니다.

**필수 구성 요소:**

위에서 설명한 논리가 올바르게 작동하려면 다음을 제출하여 [데이터 동기화](#data-synchronization-data-synchronization)를 활성화하십시오.
적절한 프로그램 및 환경을 나타내는 고객 지원 센터 요청.

### ID 공급자와 통합 {#integration-with-an-idp}

고객은 사용자를 인증하는 IdP(ID 공급자)와 통합될 수 있습니다. 통합 기술에는 아래 설명된 것처럼 SAML 및 OAuth/SSO가 포함되어 있습니다.

**SAML 기반**

고객은 기본 SAML IdP를 통해 SAML 기반 인증을 사용할 수 있습니다. AEM에서 IdP를 사용할 때, IdP는 SAML 어설션에 설명된 대로 사용자의 자격 증명을 인증하고, AEM을 통해 사용자 인증을 브로커링하고, 필요에 따라 AEM에서 사용자 레코드를 생성하고, AEM에서 사용자의 그룹 멤버십을 관리합니다.

>[!NOTE]
>
>IdP는 사용자 자격 증명의 초기 인증만 인증하며, 이후 AEM으로의 요청은 AEM 로그인 토큰 쿠키(사용 가능한 한)를 사용하여 수행됩니다.

[SAML 2.0 인증 핸들러](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/authentication/saml-2-0.html?lang=ko)에 대한 자세한 내용은 설명서를 참조하십시오.

**OAuth/SSO**

AEM의 SSO 인증 핸들러 서비스 사용에 대한 자세한 내용은 [SSO(Single Sign-On) 설명서](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/configuring/single-sign-on.html?lang=ko)를 참조하십시오.

원하는 OAuth 공급자를 통해 `com.adobe.granite.auth.oauth.provider` 인터페이스를 구현할 수 있습니다.

**필수 구성 요소:**

사용자별 데이터를 저장할 때 항상 idP(ID 공급자)를 단일 관리 지점으로 사용하는 것이 좋습니다. 추가 사용자 정보가 idP의 일부가 아닌 로컬 저장소에 저장된 경우 고객 지원 센터에 적절한 프로그램 및 환경을 나타내는 요청을 제출하여 [데이터 동기화](#data-synchronization-data-synchronization)를 활성화하십시오. SAML 인증 공급자의 경우 [데이터 동기화](#data-synchronization-data-synchronization) 외에 [동적 그룹 구성원](https://experienceleague.adobe.com/ko/docs/experience-manager-learn/cloud-service/authentication/saml-2-0)이 활성화되어 있는지 확인하십시오.

### 고정 세션 및 압축된 토큰 {#sticky-sessions-and-encapsulated-tokens}

AEM as a Cloud Service은 쿠키 기반의 고정 세션을 활성화하여 최종 사용자가 각 요청에 대해 동일한 게시 노드로 라우팅되도록 합니다. 사용자 트래픽 스파이크와 같은 특별한 경우에는 캡슐화된 토큰 기능이 성능을 높일 수 있으므로 각 요청에서 저장소의 사용자 레코드를 참조하지 않아도 됩니다. 최종 사용자가 선호도를 갖는 게시 노드가 교체된 경우, 아래 [데이터 동기화](#data-synchronization-data-synchronization) 섹션에 설명된 대로 새 게시 노드에서 사용자 ID 레코드를 사용할 수 있습니다.

캡슐화된 토큰 기능을 활용하려면 고객 지원 센터에 적절한 프로그램 및 환경을 나타내는 요청을 제출하십시오. 더 중요한 것은 캡슐화된 토큰을 [데이터 동기화](#data-synchronization-data-synchronization) 없이 사용할 수 없으므로 함께 사용해야 한다는 것입니다. 따라서 활성화하기 전에 사용 사례를 주의 깊게 검토하고 기능이 필수인지 확인하십시오.

## 사용자 프로필 {#user-profile}

데이터 특성에 따라, 데이터를 유지하는 접근 방식에는 여러 가지가 있습니다.

### AEM 저장소 {#aem-repository}

사용자 프로필 정보를 작성하고 읽는 방법에는 두 가지가 있습니다.

* `com.adobe.granite.security.user` 인터페이스 UserPropertiesManager 인터페이스를 통한 서버측 사용. 데이터가 `/home/users`에서 사용자의 노드 아래에 배치됩니다. 사용자별로 고유한 페이지가 캐시되지 않았는지 확인하십시오.
* [설명서](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/personalization/contexthub.html?lang=ko#personalization)에 따라 ContextHub를 사용하는 클라이언트측

**필수 구성 요소:**

서버측 사용자 프로필 지속성 로직이 올바르게 작동하려면 다음을 제출하여 [데이터 동기화](#data-synchronization-data-synchronization)를 활성화하십시오.
적절한 프로그램 및 환경을 나타내는 고객 지원 센터 요청.

### 서드파티 데이터 저장소 {#third-party-data-stores}

최종 사용자 데이터는 CRM과 같은 서드파티 공급업체에 전송되고, 사용자가 AEM에 로그인한 후 API를 통해 검색되고, AEM 사용자의 프로필 노드에서 유지(또는 새로 고침)되고, 필요에 따라 AEM에 의해 사용될 수 있습니다.

프로필 속성을 검색하기 위해 서드파티 서비스에 실시간으로 액세스할 수 있지만, AEM에서의 요청 처리에 물리적으로 영향을 미치지 않도록 해야 합니다.

**필수 구성 요소:**

위에서 설명한 논리가 올바르게 작동하려면 다음을 제출하여 [데이터 동기화](#data-synchronization-data-synchronization)를 활성화하십시오.
적절한 프로그램 및 환경을 나타내는 고객 지원 센터 요청.

## 권한 (폐쇄형 사용자 그룹) {#permissions-closed-user-groups}

CUG(폐쇄형 사용자 그룹)라고도 하는 Publish 계층 액세스 정책은 AEM 작성자에 정의되어 있습니다. [폐쇄형 사용자 그룹 만들기](https://experienceleague.adobe.com/docs/experience-manager-65/administering/security/cug.html?lang=ko#applying-your-closed-user-group-to-content-pages)를 참조하십시오. 일부 사용자로부터 웹 사이트의 특정 섹션 또는 페이지를 제한하려면 여기에 설명된 대로 AEM 작성자를 사용하여 필요에 따라 CUG를 적용한 다음 게시 계층에 복제하십시오.

* 사용자가 SAML을 사용하여 ID 공급자(IdP)를 통해 인증하여 로그인하는 경우, 인증 핸들러는 사용자의 그룹 멤버십(게시 계층의 CUG와 일치해야 함)을 식별한 다음 저장소 레코드를 통해 사용자와 그룹 간의 연결을 유지합니다.
* IdP 통합 없이 로그인하는 경우 사용자 정의 코드를 동일한 저장소 구조 관계에 적용할 수 있습니다.

또한 사용자 정의 코드는 로그인과 관계없이 조직의 고유한 요구 사항에 따라 사용자의 그룹 멤버십을 유지하고 관리할 수 있습니다.

## 데이터 동기화 {#data-synchronization}

웹 사이트 최종 사용자는 모든 웹 페이지 요청마다, 심지어 다른 브라우저를 사용하여 로그인할 때에도 일관된 경험을 기대합니다. 그러나 자신이 모를 때에도 이들 최종 사용자는 게시 계층 인프라의 서로 다른 서버 노드로 이동합니다. AEM as a Cloud Service은 게시 계층의 모든 노드에 걸쳐 `/home` 폴더 계층 구조(사용자 프로필 정보, 그룹 멤버십 등)를 빠르게 동기화함으로써 이를 수행합니다.

다른 AEM 솔루션과 달리 AEM as a Cloud Service의 사용자 및 그룹 멤버십 동기화는 지점 간 메시징 접근 방식을 사용하지 않으며, 대신 고객 구성이 필요하지 않은 게시-구독 접근 방식을 구현합니다.

>[!NOTE]
>
>기본적으로 사용자 프로필 및 그룹 멤버십 동기화는 비활성화되어 있으므로 데이터가 게시 계층으로 동기화되거나 영구적으로 유지되지 않습니다. 이 기능을 활성화하려면 고객 지원 팀에 적절한 프로그램 및 환경을 나타내는 요청을 전송하십시오.

>[!IMPORTANT]
>
>프로덕션 환경에서 데이터 동기화를 활성화하기 전에 구현을 규모에 맞게 테스트하십시오. 사용 사례와 지속되는 데이터에 따라 일부 일관성 및 지연 문제가 발생할 수 있습니다.

## 캐시 고려 사항 {#cache-considerations}

인증된 HTTP 요청은 사용자별 상태가 요청 응답의 일부로 전송될 수 있으므로 CDN 및 Dispatcher에 캐시하기 어려울 수 있습니다. 의도치 않게 인증된 요청을 캐시하여 다른 요청 브라우저에 제공하면 올바르지 않은 경험이 발생하거나 보호 데이터 또는 사용자 데이터가 유출될 수 있습니다.

사용자별 반응을 지원하면서 요청의 높은 캐시 기능을 유지하기 위한 접근 방식은 다음과 같습니다.

* AEM Dispatcher 권한 구분 캐시
* Sling Dynamic 포함 항목
* AEM ContextHub
