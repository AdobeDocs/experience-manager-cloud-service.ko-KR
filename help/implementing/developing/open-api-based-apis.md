---
title: OpenAPI 기반 API
description: OpenAPI 기반 API에 대한 AEM as a Cloud Service 지원에 대해 알아보기
feature: Developing
role: Admin, Architect, Developer
exl-id: 4aeafba9-8f9e-4ecb-9e37-8d048b0474cc
source-git-commit: e735f7d2a39e3165907969d2e27565639499a636
workflow-type: tm+mt
source-wordcount: '497'
ht-degree: 1%

---

# OpenAPI 기반 API {#openapi-based-apis}

>[!NOTE]
>
>OpenAPI는 조기 액세스 프로그램의 일부로 사용할 수 있습니다. 액세스하는 데 관심이 있는 경우 사용 사례에 대한 설명을 포함하여 [aem-apis@adobe.com](mailto:aem-apis@adobe.com)에 전자 메일을 보내는 것이 좋습니다.

최신 AEM as a Cloud Service API는 OpenAPI 사양을 따르므로 일관되고 문서화되었으며 사용자 친화적인 API를 생성합니다. 자세한 내용은 다음 페이지에서 확인할 수 있습니다.

* 서버 간 인증을 사용하여 OpenAPI 기반 AEM API를 구성하고 호출하는 방법에 대한 [전체 튜토리얼](https://experienceleague.adobe.com/ko/docs/experience-manager-learn/cloud-service/aem-apis/invoke-openapi-based-aem-apis)입니다.
* [API 개념 및 구문](https://developer.adobe.com/experience-cloud/experience-manager-apis/guides/how-to/)을(를) 포함한 정보 [안내서](https://developer.adobe.com/experience-cloud/experience-manager-apis/guides/).
* API 끝점 [참조 설명서](https://developer.adobe.com/experience-cloud/experience-manager-apis/). 여기서 일부 API는 OpenAPI 기반입니다(예: [이 Sites API](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/stable/sites/)). 참조 설명서에는 Adobe Developer Console으로 생성된 전달자 토큰을 사용하여 엔드포인트를 쉽게 시도할 수 있는 API 플레이그라운드도 포함되어 있습니다.

일반적인 API 사용 사례는 CRM 또는 PIM과 같은 시스템과의 통합을 포함하며, 여기서 AEM API를 호출하여 데이터를 검색하거나 유지합니다. 통합 구현의 일부로 응용 프로그램이 [AEM에서 제공하는 이벤트](https://experienceleague.adobe.com/en/docs/experience-manager-learn/cloud-service/aem-eventing/overview)를 구독할 수 있으며, 이로 인해 Adobe App Builder 또는 기타 인프라에서 비즈니스 논리가 트리거될 수 있습니다.

지원되는 API 인증 유형은 끝점에 따라 다르지만 OAuth 서버 간, OAuth 웹 앱 및 OAuth SPA(단일 페이지 앱) 일 수 있습니다.

>[!NOTE]
>
> [전체 튜토리얼](https://experienceleague.adobe.com/ko/docs/experience-manager-learn/cloud-service/aem-apis/invoke-openapi-based-aem-apis)은(는) OpenAPI 기반 AEM API를 구성하고 호출하는 방법을 알아보는 권장 리소스입니다.


## API 액세스 구성 {#configuring-api-access}

많은 OpenAPI 기반 AEM API에는 인증이 필요하며, 이를 위해서는 [Adobe Developer Console](https://developer.adobe.com/developer-console/docs/guides/)을 사용하여 자격 증명을 생성해야 합니다. 구성에는 다음 단계가 포함됩니다.

1. AEM 프로그램의 [제품 프로필이 업데이트되었는지](/help/onboarding/aem-cs-team-product-profiles.md#aem-product-profiles) 확인하고 원하는 API에 액세스할 수 있는 적절한 서비스를 사용하도록 설정하십시오.
1. Adobe Developer Console에서 새 프로젝트를 만들고 원하는 API를 프로젝트에 추가하고 적절한 인증 유형도 선택합니다.
1. API를 호출할 때 나중에 전달자 토큰으로 교환하는 데 사용되는 자격 증명을 생성합니다.
1. 구성 파이프라인(또는 RDE의 명령줄)을 사용하여 배포되는 YAML 파일을 구성하여 환경에 클라이언트 ID를 등록합니다.

단계별 지침은 [OpenAPI 기반 API 설정 자습서](https://experienceleague.adobe.com/en/docs/experience-manager-learn/cloud-service/aem-apis/setup)를 참조하십시오.

## 클라이언트 ID 등록 {#registering-a-client-id}

클라이언트 ID는 Adobe Developer Console 프로젝트에 있는 AP를 특정 AEM 환경으로 범위로 지정합니다. 이는 다음과 같이 수행됩니다.

1. 원하는 계층(작성자, 게시, 미리보기)을 포함하여 아래 코드 조각과 같은 구성으로 `api.yaml` 또는 유사한 파일을 만드십시오. `Client_id` 값은 Adobe Developer Console API 프로젝트에서 가져와야 합니다.

   `kind`, `version` 및 `metadata` 속성은 [파이프라인 구성](/help/operations/config-pipeline.md#common-syntax) 문서에 설명되어 있습니다. `kind` 속성 값을 *API*(으)로 설정하고 `version` 속성을 *1*(으)로 설정해야 합니다.

   ```
   kind: "API"
   version: "1"
   metadata:
     envTypes: ["dev"]
   data:
     allowedClientIDs:
       author:
         - "<client_id>"
       publish:
         - "<client_id>"
       preview:
         - "<client_id>"
   ```

1. [파이프라인 구성](/help/operations/config-pipeline.md#folder-structure)에 설명된 대로 파일을 `config` 또는 유사한 최상위 폴더 아래에 배치합니다.
1. RDE 이외의 환경 유형(명령줄 도구 사용)의 경우 Config Pipeline 문서의 [이 섹션](/help/operations/config-pipeline.md#creating-and-managing)에서 참조한 대로 Cloud Manager에서 타깃팅된 배포 구성 파이프라인을 만드십시오. 전체 스택 파이프라인 및 웹 계층 파이프라인은 구성 파일을 배포하지 않습니다.
1. 구성 배포.
