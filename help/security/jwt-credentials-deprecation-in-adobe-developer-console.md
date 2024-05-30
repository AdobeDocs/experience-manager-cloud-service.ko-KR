---
title: Adobe Developer Console에서 JWT 자격 증명 사용 중단
description: AEM의 Adobe Developer Console에서 JWT 자격 증명 사용 중단이 미치는 영향에 대해 알아봅니다.
exl-id: 7c811081-484c-41f7-a289-4e9a10a837b3
source-git-commit: f183e1999e29ee7f25f2d427d0b2273d244e4632
workflow-type: tm+mt
source-wordcount: '479'
ht-degree: 93%

---

# Adobe Developer Console에서 JWT 자격 증명 사용 중단 {#jwt-credentials-deprecation-in-adobe-developer-console}

>[!NOTE]
>
>AEM 6.5 고객은 자세한 내용을 확인하려면 [이 문서](https://experienceleague.adobe.com/ko/docs/experience-manager-65/content/security/jwt-credentials-deprecation-in-adobe-developer-console)를 참조해야 합니다.

Adobe 고객은 [Adobe Developer Console](https://developer.adobe.com/console)을 사용하여 다양한 API에 액세스할 수 있는 자격 증명을 생성합니다. 고객은 OAuth 서버 간 자격 증명에서 단일 페이지 앱에 이르기까지 다양한 자격 증명 유형 중에서 선택합니다. 이러한 자격 증명 유형 중 하나인 서비스 계정(JWT) 자격 증명은 OAuth 서버 간 자격 증명이 마련되어 더 이상 사용되지 않습니다. 2024년 6월 3일 이후로 새 서비스 계정(JWT) 사용자 인증 정보를 생성할 수 없으며 기존 JWT 사용자 인증 정보는 2025년 1월 27일 이후에는 작동하지 않습니다. [사용 중단에 대해 살펴보십시오](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/migration/).

이 문서에서는 AEM as a Cloud Service 고객이 사용 중단을 처리하는 방법에 대한 몇 가지 추가 컨텍스트를 제공합니다.

중요한 점은 AEM이 이제 AEM as a Cloud Service에 대한 새로운 OAuth 서버 간 자격 증명을 지원한다는 것입니다. JWT 자격 증명을 마이그레이션하라는 지침이 포함된 이메일을 수신했을 수 있으며, 이제 이 마이그레이션을 수행할 수 있습니다.

아래 섹션에서는 고객이 서비스 계정(JWT) 자격 증명을 현재 AEM에서 지원되는 OAuth 서버 간 자격 증명으로 교체해야 하는(또는 경우에 따라 교체해서는 안 되는) 시나리오를 나열합니다. 자격 증명을 마이그레이션하는 [방법을 확인](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/migration/#migration-overview)하십시오.

>[!NOTE]
>
>[**AEM** Developer Console](/help/implementing/developing/introduction/development-guidelines.md#crxde-lite-and-developer-console)(**Adobe** Developer Console과 구별되는 이름의 **AEM** 참고)은 서버 간 API에 사용되는 [JWT](/help/implementing/developing/introduction/generating-access-tokens-for-server-side-apis.md) 토큰을 생성하는 유틸리티를 제공합니다. 이러한 자격 증명은 더 이상 사용되지 않으며 계속 사용할 수 있습니다.

## AEM을 다른 Adobe 솔루션과 통합 {#integrating-aem-with-other-adobe-solutions}

**조치**: 이제 AEM에서 OAuth 자격 증명을 지원하므로 구성을 마이그레이션합니다.

**관련 AEM 버전**: AEM as a Cloud Service

AEM 고객은 AEM을 사용하여 다른 여러 Adobe 솔루션과의 통합을 구성합니다. 예를 들어 Adobe Target, Adobe Analytics 등이 있습니다.

다음 방법에 대한 자세한 내용은 [AEM as a Cloud Service에 대한 IMS 통합 설정](/help/security/setting-up-ims-integrations-for-aem-as-a-cloud-service.md)을 참조하십시오.

* OAuth 자격 증명으로 구성 만들기
* OAuth 자격 증명을 사용하기 위해 JWT 자격 증명으로 만든 구성을 마이그레이션

## Cloud Manager API {#cloud-manager-apis}

**작업**: JWT 자격 증명을 Cloud Manager가 지원하는 OAuth 자격 증명으로 마이그레이션합니다.

**관련 AEM 버전**: AEM as a Cloud Service

고객은 [Cloud Manager API](https://developer.adobe.com/experience-cloud/cloud-manager/guides/getting-started/create-api-integration/)를 호출할 수 있도록 Adobe Developer Console 프로젝트를 만듭니다. Adobe Developer 프로젝트의 자격 증명은 사용 중단된 JWT 자격 증명이 만료되는 2025년 1월 전에 OAuth 서버 간 자격 증명 유형으로 마이그레이션해야 합니다.

## 자동 생성된 프로젝트 {#autogen-projects}

**작업**: Adobe가 사용자를 대신하여 마이그레이션할 예정이므로 직접 마이그레이션하지 않아도 됩니다.

**관련 AEM 버전**: AEM as a Cloud Service.

Cloud Manager는 AEM as a Cloud Service 환경으로 프로비저닝할 때 JWT 자격 증명을 사용하여 Adobe Developer Console 프로젝트를 자동 생성합니다. 아래 스크린샷에 표시된 것처럼 이 프로젝트는 읽기 전용으로 표시되어 있습니다. 고객은 이러한 프로젝트를 OAuth 서버 간 자격 증명으로 마이그레이션할 수 없으며 마이그레이션을 시도해서도 안 됩니다. 대신 Adobe는 자격 증명이 더 이상 사용 불가능한 상태가 되기 전에 이러한 프로젝트를 자체적으로 마이그레이션합니다.

![자동 생성된 프로젝트](/help/security/assets/jwt-deprecation-autogen-projects.png)
