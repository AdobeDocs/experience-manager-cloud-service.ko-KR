---
title: Adobe Developer Console에서 JWT 자격 증명 사용 중단
description: Adobe Developer 콘솔의 JWT 자격 증명 사용이 AEM에 미치는 영향에 대해 알아봅니다.
exl-id: 7c811081-484c-41f7-a289-4e9a10a837b3
source-git-commit: 802e29017d3f1e59ee1676b4172292cb3453648a
workflow-type: tm+mt
source-wordcount: '557'
ht-degree: 56%

---

# Adobe Developer Console에서 JWT 자격 증명 사용 중단 {#jwt-credentials-deprecation-in-adobe-developer-console}

>[!NOTE]
>
>AEM 6.5 고객은 자세한 내용을 확인하려면 [이 문서](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/security/jwt-credentials-deprecation-in-adobe-developer-console)를 참조해야 합니다.

Adobe 고객은 [Adobe Developer Console](https://developer.adobe.com/console)을 사용하여 다양한 API에 액세스할 수 있는 자격 증명을 생성합니다. 고객은 OAuth 서버 간 자격 증명에서 단일 페이지 앱에 이르기까지 다양한 자격 증명 유형 중에서 선택합니다. 이러한 자격 증명 유형 중 하나인 서비스 계정(JWT) 자격 증명은 OAuth 서버 간 자격 증명이 마련되어 더 이상 사용되지 않습니다. 2024년 6월 3일 이후로 새 서비스 계정(JWT) 사용자 인증 정보를 생성할 수 없으며 기존 JWT 사용자 인증 정보는 2025년 1월 27일 이후에는 작동하지 않습니다. [사용 중단에 대해 살펴보십시오](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/migration/).

이 문서에서는 AEM as a Cloud Service 고객이 사용 중단을 처리하는 방법에 대한 몇 가지 추가 컨텍스트를 제공합니다.

현재 주요 해결 방법은 AEM 기능이 아직 새 OAuth 서버 간 자격 증명을 지원하지 않는다는 것입니다. as a Cloud Service용 AEM AEM 릴리스를 통해 2024년 5월 중순까지 지원이 곧 제공될 예정입니다. JWT 자격 증명을 마이그레이션하기 위한 지침이 포함된 이메일을 받았을 수 있지만, AEM이 새로운 OAuth 서버 간 자격 증명 유형을 지원할 때까지 자격 증명 마이그레이션을 유보할 수 있습니다.

아래 섹션에는 AEM이 5월 중순에 서비스 계정(JWT) 자격 증명을 지원하면 고객이 해당 서비스 계정(JWT) 자격 증명을 OAuth 서버 간 자격 증명으로 교체해야 하는(또는 때때로 교체해서는 안 되는) 시나리오가 나와 있습니다. [향후 자격 증명을 교체하는 방법](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/migration/#migration-overview)을 읽어보십시오.

>[!NOTE]
>
>[**AEM** Developer Console](/help/implementing/developing/introduction/development-guidelines.md#crxde-lite-and-developer-console)(**Adobe** Developer Console과 구별되는 이름의 **AEM** 참고)은 서버 간 API에 사용되는 [JWT](/help/implementing/developing/introduction/generating-access-tokens-for-server-side-apis.md) 토큰을 생성하는 유틸리티를 제공합니다. 이러한 자격 증명은 더 이상 사용되지 않으며 계속 사용할 수 있습니다.


## AEM을 다른 Adobe 솔루션과 통합 {#integrating-aem-with-other-adobe-solutions}

**작업**: AEM에서 지원하는 2024년 5월 중순 이후까지 마이그레이션할 때까지 기다리십시오(이 문서가 해당 시간에 업데이트될 예정)

**관련 AEM 버전**: AEM as a Cloud Service

AEM 고객은 AEM Author UI를 사용하여 다른 모든 Adobe 솔루션과의 통합을 구성합니다. 예를 들어 Adobe Target, Adobe Analytics, Adobe Launch, AFCS 등이 있습니다.

![AEM을 다른 솔루션과 통합](/help/security/assets/jwt-deprecation.png)

예를 들어 Adobe Target과의 통합을 구성하기 위한 [지침](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/sites/integrations/integration-adobe-target-ims)은 다음과 같습니다. 의 API 키 [AEM에서 IMS 구성 완료](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/sites/integrations/integration-adobe-target-ims#completing-the-ims-configuration-in-aem) AEM이 5월 중순에 해당 자격 증명을 지원하면 섹션을 OAuth 서버 간 자격 증명 유형으로 마이그레이션해야 합니다. 이러한 지침은 새 OAuth 서버 간 자격 증명을 적용하는 데 도움이 되도록 5월 중순에 업데이트됩니다.

## Cloud Manager API {#cloud-manager-apis}

**작업**: 서버 간 OAuth 자격 증명으로 마이그레이션합니다.

**관련 AEM 버전**: AEM as a Cloud Service

고객은 [Cloud Manager API](https://developer.adobe.com/experience-cloud/cloud-manager/guides/getting-started/create-api-integration/)를 호출할 수 있도록 Adobe Developer Console 프로젝트를 만듭니다. 더 이상 사용되지 않는 JWT 자격 증명이 2025년 1월에 만료되기 전에 Adobe Developer 프로젝트의 자격 증명을 OAuth 서버 간 자격 증명 유형으로 마이그레이션해야 합니다.

## 자동 생성된 프로젝트 {#autogen-projects}

**작업**: Adobe이 귀하를 대신하여 마이그레이션하게 되므로 마이그레이션하지 마십시오.

**관련 AEM 버전**: AEM as a Cloud Service.

Cloud Manager는 AEM as a Cloud Service 환경을 프로비저닝하면 JWT 자격 증명으로 Adobe Developer 콘솔 프로젝트를 자동으로 생성합니다. 아래 스크린샷에 표시된 것처럼 이 프로젝트는 읽기 전용으로 표시되어 있습니다. 고객은 이러한 프로젝트를 OAuth 서버 간 자격 증명으로 마이그레이션할 수 없으며 마이그레이션하려고 하면 안 됩니다. 대신 자격 증명을 더 이상 사용할 수 없게 되기 전에 Adobe이 이러한 프로젝트를 자체적으로 마이그레이션합니다.

![자동 생성된 프로젝트](/help/security/assets/jwt-deprecation-autogen-projects.png)
