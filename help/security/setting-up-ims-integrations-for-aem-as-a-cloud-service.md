---
title: AEM as a Cloud Service에 대한 IMS 통합 설정
description: AEM as a Cloud Service에 대한 IMS 통합을 설정하는 방법 알아보기
exl-id: 72fb1ea1-355c-4faa-a733-77bc7de75ed5
feature: Security
role: Admin
source-git-commit: 00a05b3bdc1a689947c1507847da99b54c94dcac
workflow-type: ht
source-wordcount: '386'
ht-degree: 100%

---

# AEM as a Cloud Service에 대한 IMS 통합 설정 {#setting-up-ims-integrations-for-aemaacs}

>[!NOTE]
>
>자동 프로비저닝된 JWT 구성은 Adobe에서 자동으로 처리되므로 수동으로 마이그레이션해서는 안 됩니다.

Adobe Experience Manager(AEM) as a Cloud Service은 다른 여러 Adobe 솔루션과 통합할 수 있습니다. 예를 들어 Adobe Target, Adobe Analytics 등이 있습니다.

통합은 S2S OAuth로 구성된 IMS 통합을 사용합니다.

* 우선 다음을 만듭니다.

   * [Developer Console의 자격 증명](#credentials-in-the-developer-console)

* 이후에 다음과 같은 작업을 수행할 수 있습니다.

   * (신규) [OAuth 구성](#creating-oauth-configuration) 만들기

   * [기존 JWT 구성을 OAuth 구성으로 마이그레이션](#migrating-existing-JWT-configuration-to-oauth)

>[!CAUTION]
>
>이전에는 구성을 만들 때 [JWT 자격 증명을 사용했지만 이는 현재 Adobe Developer Console에서 더 이상 사용되지 않습니다](/help/security/jwt-credentials-deprecation-in-adobe-developer-console.md).
>
>이러한 구성은 더 이상 만들거나 업데이트할 수 없지만 OAuth 구성으로 마이그레이션할 수 있습니다.

## Developer Console의 자격 증명 {#credentials-in-the-developer-console}

첫 번째 단계로 Adobe Developer Console에서 OAuth 자격 증명을 구성해야 합니다.

이를 수행하는 방법에 대한 자세한 내용은 요구 사항에 따라 Developer Console 설명서를 참조하십시오.

* 개요:

   * [서버 간 인증](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/)

* 새 OAuth 자격 증명 만들기:

   * [OAuth 서버 간 자격 증명 구현 안내서](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/implementation)

* 기존 JWT 자격 증명을 OAuth 자격 증명으로 마이그레이션:

   * [서비스 계정(JWT) 자격 증명에서 OAuth 서버 간 자격 증명으로 마이그레이션](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/migration/)

예:

![Developer Console의 OAuth 자격 증명](assets/ims-configuration-developer-console.png)

## OAuth 구성 만들기 {#creating-oauth-configuration}

OAuth를 사용하여 새로운 Adobe IMS 통합을 만들려면 다음 작업을 수행하십시오.

1. AEM에서 **도구**, **보안**, **Adobe IMS 통합**&#x200B;으로 이동합니다.

1. **만들기**&#x200B;를 선택합니다.

1. [Developer Console](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/implementation)의 세부 정보에 따라 구성을 완료합니다. 예:

   ![OAuth 구성 만들기](assets/ims-create-oauth-configuration.png)

1. 변경 사항을 **저장**&#x200B;합니다.

## 기존 JWT 구성을 OAuth 구성으로 마이그레이션 {#migrating-existing-JWT-configuration-to-oauth}

JWT 자격 증명을 기반으로 기존 Adobe IMS 통합을 마이그레이션하려면 다음 작업을 수행하십시오.

>[!NOTE]
>
>이 예에서는 실행 IMS 구성을 보여 줍니다.

1. AEM에서 **도구**, **보안**, **Adobe IMS 통합**&#x200B;으로 이동합니다.

1. 마이그레이션해야 하는 JWT 구성을 선택합니다. JWT 구성에는 **JWT 자격 증명(사용 안 함)**&#x200B;이라는 경고가 표시됩니다.

1. **속성**&#x200B;을 선택합니다.

   ![JWT 구성 선택](assets/ims-migrate-jwt-select-configuration.png)

1. 구성이 읽기 전용으로 열립니다.

   ![구성 속성 - 읽기 전용](assets/ims-migrate-jwt-properties-read-only.png)

1. **인증 유형** 드롭다운에서 **OAuth**&#x200B;를 선택합니다.

   ![인증 유형 선택](assets/ims-migrate-jwt-authentication-type.png)

1. 사용 가능한 속성이 업데이트됩니다. Developer Console의 세부 정보를 사용하여 작성합니다.

   ![OAuth 세부 정보 작성](assets/ims-migrate-jwt-complete-oauth-details.png)

1. **저장 믿 닫기**를 사용하여 업데이트 내용을 유지합니다.
콘솔로 돌아오면 **JWT 자격 증명(사용 안 함)** 경고가 사라집니다.
