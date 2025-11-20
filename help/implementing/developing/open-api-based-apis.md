---
title: OpenAPI 기반 API
description: OpenAPI 기반 API에 대한 AEM as a Cloud Service 지원에 대해 알아보기
feature: Developing
role: Admin, Developer
exl-id: 4aeafba9-8f9e-4ecb-9e37-8d048b0474cc
source-git-commit: 3a46db9c98fe634bf2d4cffd74b54771de748515
workflow-type: tm+mt
source-wordcount: '653'
ht-degree: 1%

---

# OpenAPI 기반 API {#openapi-based-apis}

최신 AEM as a Cloud Service API는 OpenAPI 사양을 따르므로 일관되고 잘 문서화된 API 세트를 제공합니다.

>[!NOTE]
>
> [전체 튜토리얼](https://experienceleague.adobe.com/ko/docs/experience-manager-learn/cloud-service/aem-apis/invoke-openapi-based-aem-apis)은(는) OpenAPI 기반 AEM API를 구성하고 호출하는 방법을 배우는 데 권장되는 리소스입니다.

인증이 필요한 끝점의 경우 인증 접근 방식은 끝점에 따라 다르지만 OAuth 서버 간, OAuth 웹 앱 또는 OAuth SPA(단일 페이지 앱)를 사용할 수 있습니다. 자격 증명이 [Adobe Developer Console](https://developer.adobe.com/developer-console/)의 프로젝트를 통해 구성되었습니다.

일반적인 API 사용 사례는 CRM 또는 PIM과 같은 시스템과의 통합을 포함하며, 여기서 AEM API를 호출하여 데이터를 검색하거나 유지합니다. 통합 구현의 일부로 응용 프로그램이 [AEM에서 제공하는 이벤트](https://experienceleague.adobe.com/en/docs/experience-manager-learn/cloud-service/aem-eventing/overview)를 구독할 수 있으며, 이로 인해 Adobe App Builder 또는 기타 인프라에서 비즈니스 논리가 트리거될 수 있습니다.

이 문서는 개요 역할을 하지만, 다음 페이지에서 보다 심층적인 문서를 사용할 수 있습니다.

* [참조 설명서](https://developer.adobe.com/experience-cloud/experience-manager-apis/)의 OpenAPI 기반 API 섹션의 링크입니다. 각 API의 참조 설명서에는 Adobe Developer Console으로 생성된 전달자 토큰을 사용하여 엔드포인트를 쉽게 시도할 수 있는 API 플레이그라운드도 포함되어 있습니다.

* [API 개념 및 구문](https://developer.adobe.com/experience-cloud/experience-manager-apis/guides/)을(를) 포함한 정보 [안내서](https://developer.adobe.com/experience-cloud/experience-manager-apis/guides/how-to/).

* [인증 접근 방식](https://experienceleague.adobe.com/en/docs/experience-manager-learn/cloud-service/aem-apis/openapis/overview#authentication-support) 및 기타 개념을 설명하는 최상위 튜토리얼입니다.

* [OpenAPI 기반 API를 구성하는 방법](https://experienceleague.adobe.com/en/docs/experience-manager-learn/cloud-service/aem-apis/openapis/setup)에 초점을 맞춘 비디오가 포함된 튜토리얼입니다.

* 서버 간 인증 전략으로 OpenAPI를 구성하고 호출하는 방법에 대한 [종합적인 자습서](https://experienceleague.adobe.com/ko/docs/experience-manager-learn/cloud-service/aem-apis/invoke-openapi-based-aem-apis). 웹 앱 및 단일 페이지 애플리케이션 인증 접근 방식에 대해서도 유사한 튜토리얼을 찾을 수 있습니다.

## API 액세스 구성 {#configuring-api-access}

일부 OpenAPI 기반 AEM API에는 인증이 필요합니다. 이 경우 [Adobe Developer Console](https://developer.adobe.com/developer-console/)을(를) 사용하여 자격 증명을 생성해야 합니다. 구성에는 다음 단계가 포함됩니다.

1. AEM as a Cloud Service 환경의 현대화. 자세한 내용은 [AEM as a Cloud Service 환경 현대화](https://experienceleague.adobe.com/en/docs/experience-manager-learn/cloud-service/aem-apis/openapis/setup?#modernization-of-aem-as-a-cloud-service-environment) 자습서 단계를 참조하십시오.
1. 제품 프로필을 사용하여 AEM API에 대한 액세스를 활성화합니다. 제품 프로필은 사전 정의된 ACL(액세스 제어 목록)이 있는 AEM 사용자 그룹을 나타내는 서비스와 연결됩니다. 일부 서비스는 기본적으로 특정 제품 프로필과 연결되어 있지만 다른 서비스는 명시적으로 연결해야 합니다. 예를 들어 AEM Assets API 사용자 서비스는 [제품 프로필](/help/onboarding/aem-cs-team-product-profiles.md#aem-product-profiles)과 연결되어 있지 않으므로 AEM Assets API를 사용하도록 설정해야 합니다. 자세한 내용은 [AEM API 액세스 사용](https://experienceleague.adobe.com/en/docs/experience-manager-learn/cloud-service/aem-apis/openapis/setup#enable-aem-apis-access) 자습서 단계를 참조하십시오.
1. 서버 간 인증을 추가하려면 통합 설정 사용자가 Adobe Admin Console에서 조직의 시스템 관리자이거나 서비스가 연결된 제품 프로필에 개발자로 추가되어야 합니다. 자세한 내용은 [AEM API 액세스 사용](https://experienceleague.adobe.com/en/docs/experience-manager-learn/cloud-service/aem-apis/openapis/setup#enable-aem-apis-access) 자습서 단계를 참조하십시오.
1. Adobe Developer Console(ADC) 프로젝트를 만듭니다.
1. ADC 프로젝트를 구성합니다. 이렇게 하면 API를 호출할 때 나중에 전달자 토큰으로 교환하는 데 사용되는 자격 증명이 생성됩니다.
1. ADC 프로젝트 통신을 사용하도록 AEM 인스턴스를 구성합니다. 아래 [클라이언트 ID 등록](#registering-a-client-id) 섹션에 설명된 대로 YAML 파일을 구성하고 배포하여 환경에 클라이언트 ID를 등록하는 작업이 포함됩니다.

자세한 단계별 지침은 [OpenAPI 기반 API 설정 자습서](https://experienceleague.adobe.com/en/docs/experience-manager-learn/cloud-service/aem-apis/openapis/setup)를 참조하십시오.

### 클라이언트 ID 등록 {#registering-a-client-id}

클라이언트 ID는 Adobe Developer Console 프로젝트의 API를 특정 AEM 환경으로 범위화합니다. 이는 다음과 같이 수행됩니다.

1. 원하는 계층(작성자, 게시, 미리보기)을 포함하여 아래 코드 조각과 같은 구성으로 `api.yaml` 또는 유사한 파일을 만드십시오. `Client_id` 값은 Adobe Developer Console API 프로젝트에서 가져와야 합니다.

   `kind`, `version` 및 `metadata` 속성은 [파이프라인 구성](/help/operations/config-pipeline.md#common-syntax) 문서에 설명되어 있습니다. `kind` 속성 값을 *API*(으)로 설정하고 `version` 속성을 *1*(으)로 설정해야 합니다.

   ```
   kind: "API"
   version: "1"
   data:
     allowedClientIDs:
       author:
         - "<client_id>"
       publish:
         - "<client_id>"
       preview:
         - "<client_id>"
   ```

1. `config`파이프라인 구성[에 설명된 대로 파일을 &#x200B;](/help/operations/config-pipeline.md#folder-structure) 또는 유사한 최상위 폴더 아래에 배치합니다.
1. RDE 이외의 환경 유형(명령줄 도구 사용)의 경우 Config Pipeline 문서의 [이 섹션](/help/operations/config-pipeline.md#creating-and-managing)에서 참조한 대로 Cloud Manager에서 타깃팅된 배포 구성 파이프라인을 만드십시오. 전체 스택 파이프라인 및 웹 계층 파이프라인은 구성 파일을 배포하지 않습니다.
1. 구성 배포.
