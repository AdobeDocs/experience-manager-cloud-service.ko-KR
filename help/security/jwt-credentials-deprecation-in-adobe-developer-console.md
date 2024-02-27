---
title: Adobe Developer 콘솔에서 JWT 자격 증명 사용 중단
description: Adobe Developer 콘솔의 JWT 자격 증명 사용이 AEM에 미치는 영향에 대해 알아봅니다
source-git-commit: e02e38a5267188111f0392a0a5c7b73e6a4f22b5
workflow-type: tm+mt
source-wordcount: '598'
ht-degree: 0%

---


# Adobe Developer 콘솔에서 JWT 자격 증명 사용 중단 {#jwt-credentials-deprecation-in-adobe-developer-console}

Adobe 고객이 사용 [Adobe Developer 콘솔](https://developer.adobe.com/console) 다양한 API에 액세스할 수 있는 자격 증명을 생성할 수 있습니다. 고객은 OAuth 서버 간 앱에서 단일 페이지 앱에 이르기까지 다양한 자격 증명 유형에서 선택합니다. 이러한 자격 증명 유형 중 하나인 JWT(서비스 계정) 자격 증명은 OAuth 서버 간 자격 증명을 위해 더 이상 사용되지 않습니다. 2024년 5월 1일 이후 새 서비스 계정(JWT) 자격 증명을 만들 수 없으며 기존 JWT 자격 증명은 2025년 1월 1일 이후 작동하지 않습니다. 다음을 수행할 수 있습니다. [사용 중단에 대해 읽어보기](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/migration/).

이 문서에서는 AEM as a Cloud Service 및 AEM 6.5 고객이 사용 중단을 처리하는 방법에 대한 몇 가지 추가 컨텍스트를 제공합니다.

현재 주요 해결 방법은 AEM 기능이 아직 새 OAuth 서버 간 자격 증명을 지원하지 않는다는 것입니다. 최신 서비스 팩 20 이하를 실행 중인 경우(서비스 팩 21 이상에는 자동으로 포함됨) 2024년 4월 중순까지 AEMas a Cloud Service 용 AEM 릴리스와 AEM 6.5용 설치를 위한 특수 호환성 패키지를 통해 지원이 제공될 예정입니다. JWT 자격 증명을 마이그레이션하라는 지침이 포함된 이메일을 받았겠지만 AEM이 새 OAuth 서버 간 자격 증명 유형을 지원할 때까지 자격 증명 마이그레이션을 보류할 수 있으며 보류해야 합니다.

아래 섹션에는 AEM이 4월 중순에 서비스 계정(JWT) 자격 증명을 지원하면 고객이 해당 서비스 계정(JWT) 자격 증명을 OAuth 서버 간 자격 증명으로 교체해야 하는(또는 경우에 따라 교체해서는 안 되는) 시나리오가 나와 있습니다. [읽기 방법](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/migration/#migration-overview) 나중에 자격 증명을 바꿀 수 있습니다.

>[!NOTE]
>
>다음 [**AEM** 개발자 콘솔](/help/implementing/developing/introduction/development-guidelines.md#crxde-lite-and-developer-console) (다음을 참고하십시오. **AEM** 와 구별되는 이름 **Adobe** Developer Console) 생성 유틸리티 제공 [JWT 토큰](/help/implementing/developing/introduction/generating-access-tokens-for-server-side-apis.md) 서버 간 API에 사용됩니다. 이러한 자격 증명은 더 이상 사용되지 않으며 계속 사용할 수 있습니다.


## 다른 Adobe 솔루션과 AEM 통합 {#integrating-aem-with-other-adobe-solutions}

**작업**: AEM이 지원하는 2024년 4월 중순 이후까지 마이그레이션할 것을 기다리십시오.

**관련 AEM 버전**: AEM as a Cloud Service 및 Managed Services Adobe(서비스 팩 20 이하).


AEM 고객은 AEM Author UI를 사용하여 다른 모든 Adobe 솔루션과의 통합을 구성합니다. 예를 들어 Adobe Target, Adobe Analytics, Adobe Launch, AFCS 등이 있습니다.

![다른 솔루션과 AEM 통합](/help/security/assets/jwt-deprecation.png)

예를 들면 다음과 같습니다 [지침](https://docs.mktossl.com/docs/experience-manager-cloud-service/content/sites/integrations/integration-adobe-target-ims.html?lang=en) Adobe Target과의 통합을 구성합니다. 의 API 키 [AEM에서 IMS 구성 완료](https://docs.mktossl.com/docs/experience-manager-cloud-service/content/sites/integrations/integration-adobe-target-ims.html#completing-the-ims-configuration-in-aem) AEM이 4월 중순에 해당 자격 증명을 지원하면 섹션을 OAuth 서버 간 자격 증명 유형으로 마이그레이션해야 합니다. 이러한 지침은 새로운 OAuth 서버 간 자격 증명을 적용할 수 있도록 4월 중순에 수정될 예정입니다.

## Cloud Manager API {#cloud-manager-apis}

**작업**: AEM이 지원하는 2024년 4월 중순 이후까지 마이그레이션할 것을 기다리십시오.

**관련 AEM 버전**: AEM as a Cloud Service 및 Managed Services Adobe(서비스 팩 20 이하).

고객은 를 호출할 수 있도록 Adobe Developer 콘솔 프로젝트를 만듭니다. [Cloud Manager API](https://developer.adobe.com/experience-cloud/cloud-manager/guides/getting-started/create-api-integration/). AEM 및 Cloud Manager에서 지원하는 경우 Adobe Developer 프로젝트의 자격 증명은 OAuth 서버 간 자격 증명 유형으로 마이그레이션되어야 합니다.

## 자동 생성된 프로젝트 {#autogen-projects}

**작업**: Adobe이 귀하를 대신하여 마이그레이션되므로 마이그레이션하지 마십시오.

**관련 AEM 버전**: AEM만 as a Cloud Service으로.

Cloud Manager는 AEM as a Cloud Service 환경을 프로비저닝하면 JWT 자격 증명으로 Adobe Developer 콘솔 프로젝트를 자동으로 생성합니다. 이 프로젝트는 아래 스크린샷에 표시된 대로 읽기 전용으로 표시됩니다. 고객은 이러한 프로젝트를 OAuth 서버 간 자격 증명으로 마이그레이션할 수 없으며 마이그레이션하려고 하면 안 됩니다. 대신 자격 증명을 더 이상 사용할 수 없게 되기 전에 Adobe이 이러한 프로젝트를 자체적으로 마이그레이션합니다.

![자동 생성된 프로젝트](/help/security/assets/jwt-deprecation-autogen-projects.png)

