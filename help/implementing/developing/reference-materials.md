---
title: API 참조 자료
description: AEM에는 디지털 경험 프로젝트에 사용할 수 있는 광범위하고 강력한 API가 있습니다.
exl-id: d4ef3040-5a0a-4149-9e99-09eda9605038
source-git-commit: 674db680f46a4fd4772cb10fe7cb396652354dfe
workflow-type: tm+mt
source-wordcount: '608'
ht-degree: 4%

---

# API 참조 자료 {#api-reference-materials}

AEM(Adobe Experience Manager)은 애플리케이션 개발 및 AEM 확장을 위한 다양한 API를 제공합니다. AEM은 여러 오픈 소스 기술 위에 구축되어 있으며, 이 기술을 사용할 수도 있습니다.

## AEM 코어 API {#core-aem-apis}

다음 API는 AEM의 핵심입니다.

| API | 설명 |
|---|---|
| [Adobe Experience Manager as a Cloud Service](https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/index.html) | 페이지, 에셋, 워크플로우 등과 같은 제품 추상화입니다. |
| [Granite UI](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/granite-ui/api/jcr_root/libs/granite/ui/index.html#) | 다양한 필수 구성 요소를 제공하는 Adobe의 오픈 웹 스택(6.5 Granite 재료는 AEMaaCS에 적용됨) |
| [Coral UI](https://opensource.adobe.com/coral-spectrum/documentation/) | Adobe 경험에 일관성을 제공하도록 설계된 클라우드 UI에 대한 사용자의 시각적 스타일 |

<!---
|Editor core JavaScript API reference|Provides all the base objects and concepts to support authoring of content resources|
--->

>[!NOTE]
>
>Experience Manager API에 대한 최신 정보를 확인하려면 다음을 방문하십시오. [ADOBE EXPERIENCE MANAGER AS A CLOUD SERVICE API](https://developer.adobe.com/experience-cloud/experience-manager-apis/).

## 추가 프레임워크 {#additional-apis}

AEM은 몇 가지 추가 오픈 소스 API를 사용합니다.

| API | 설명 |
|---|---|
| [Apache Sling](https://sling.apache.org/apidocs/sling11/) | JCR(Java Content Repository)을 사용하여 컨텐츠를 저장하고 관리하는 웹 프레임워크 |
| [아파치 잭래빗 오크](https://jackrabbit.apache.org/oak/docs/oak_api/overview.html) | 확장 가능하고 성능이 뛰어난 JCR(Java Content Repository)을 구현하여 최신 세계적 수준의 웹 사이트의 기반으로 사용 |
| [Java 콘텐츠 저장소](https://www.adobe.io/experience-manager/reference-materials/spec/javax.jcr/javadocs/jcr-2.0/index.html) | JCR 버전 2.0 사양 |
| [Apache Felix](https://felix.apache.org) | OSGi(Open Services Gateway Initiative) 프레임워크 및 서비스 플랫폼 구현 |

## API 환경 설정 지침 {#guidelines}

AEM은 기본 설정의 내림차순으로 다음 4개의 기본 Java API 세트를 기반으로 구축됩니다.

| 우선 순위 | API | 설명 |
|---|---|---|
| 1 | [Adobe Experience Manager as a Cloud Service](https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/index.html) | 페이지, 에셋, 워크플로우 등과 같은 제품 추상화입니다. |
| 2 | [Apache Sling](https://sling.apache.org/apidocs/sling11/) | 리소스, 값 맵 및 HTTP 요청과 같은 REST 및 리소스 기반 추상화입니다. |
| 3 | [아파치 잭래빗 오크](https://jackrabbit.apache.org/oak/docs/oak_api/overview.html) | 노드, 속성 및 세션과 같은 데이터 및 콘텐츠 추상화입니다. |
| 4 | [Apache Felix](https://felix.apache.org/) | 서비스 및 (OSGi) 구성 요소와 같은 OSGi 애플리케이션 컨테이너 추상. |

AEM에서 API를 제공하는 경우 Sling, JCR 및 OSGi보다 선호합니다. AEM에서 API를 제공하지 않는 경우 JCR 및 OSGi보다 Sling을 선호합니다.

>[!TIP]
>
>이 지침에 대한 자세한 내용은 문서를 참조하십시오 [Java API 모범 사례를 이해합니다.](https://experienceleague.adobe.com/docs/experience-manager-learn/foundation/development/understand-java-api-best-practices.html)

## AEM Delivery 및 Content Management Services 및 API {#delivery-apis}

AEM은 사용자 지정 가능한 구성 요소 및 컨텐츠 전달 옵션을 제공합니다.

| 기능 | 설명 |
|---|---|
| [핵심 구성 요소](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=ko-KR) | AEM용 표준화된 웹 콘텐츠 관리(WCM) 구성 요소로 개발 시간을 단축하고 웹 사이트의 유지 관리 비용을 절감합니다. |
| [JSON 내보내기](/help/implementing/developing/components/json-exporter.md) | 모든 AEM 페이지의 콘텐츠를 JSON 데이터 모델 형식으로 전달 |
| [구성 요소에 대해 JSON 내보내기 활성화](/help/implementing/developing/components/enabling-json-exporter.md) | 모델러 프레임워크를 기반으로 구성 요소 콘텐츠의 JSON 내보내기 생성 |
| [Assets API](/help/assets/mac-api-assets.md) | 바이너리, 메타데이터, 렌디션 및 주석을 포함하여 에셋에서 CRUD(create-read-update-delete) 작업을 수행할 수 있습니다. AEM Assets HTTP API 를 참조하십시오 |
| [콘텐츠 조각 HTTP API](/help/assets/content-fragments/assets-api-content-fragments.md) | CRUD 작업을 통해 HTTP API로 콘텐츠 조각 콘텐츠에 직접 액세스 |
| [컨텐츠 조각 GraphQL API](/help/headless/graphql-api/content-fragments.md) | Headless CMS 구현에서 JavaScript 클라이언트에 콘텐츠 조각을 효율적으로 게재할 수 있도록 합니다 |
| [컨텐츠 조각 자산 HTTP API](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/assets/admin/mac-api-assets.html) | 지원되는 HTTP 자산 요청의 정확한 형식 |
| [컨텐츠 조각 및 컨텐츠 조각 모델 OpenAPI](/help/headless/content-fragment-openapis.md) | 컨텐츠 조각 및 컨텐츠 조각 모델 OpenAPI |

## SPA 관련 API {#spa-apis}

AEM 단일 페이지 애플리케이션(SPA) 편집기 SDK 프레임워크는 특정 JavaScript API 참조를 제공합니다.

| API | 설명 |
|---|---|
| [구성 요소 매핑](https://www.npmjs.com/package/@adobe/aem-spa-component-mapping) | 단일 페이지 애플리케이션에서 프론트엔드 구성 요소를 Adobe Experience Manager 리소스 유형(AEM 구성 요소)에 매핑하는 방법을 제공합니다. |
| [페이지 모델 관리자](https://www.npmjs.com/package/@adobe/aem-spa-page-model-manager) | Adobe Experience Manager 편집기와 Adobe Experience Manager SPA(단일 페이지 애플리케이션) 편집기 간의 인터프리터 |
| [React 편집 가능한 구성 요소](https://www.npmjs.com/package/@adobe/aem-react-editable-components) | Adobe Experience Manager Site Editor를 시작할 수 있는 React 구성 요소 및 통합 계층을 제공합니다. |
| [Angular 편집 가능한 구성 요소](https://www.npmjs.com/package/@adobe/aem-angular-editable-components) | Adobe Experience Manager 사이트 편집기를 시작할 수 있는 Angular 구성 요소 및 통합 레이어를 제공합니다. |

>[!TIP]
>
>다음을 확인하십시오. [SPA 소개 및 연습](/help/implementing/developing/hybrid/introduction.md) 단일 페이지 애플리케이션에 대한 자세한 내용은 을 참조하십시오.
