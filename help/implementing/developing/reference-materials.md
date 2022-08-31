---
title: API 참조 자료
description: AEM에는 디지털 경험 프로젝트에 활용할 수 있는 강력하고 광범위한 API가 있습니다.
exl-id: d4ef3040-5a0a-4149-9e99-09eda9605038
source-git-commit: 430179bf13c1fff077c515eed0676430e9e7f341
workflow-type: tm+mt
source-wordcount: '664'
ht-degree: 6%

---

# API 참조 자료 {#api-reference-materials}

Adobe Experience Manager(AEM)은 애플리케이션 개발 및 AEM 확장을 위한 많은 API를 제공합니다. AEM은 다양한 오픈 소스 기술을 기반으로 구축되었으며, 이를 활용할 수도 있습니다.

## AEM 핵심 API {#core-aem-apis}

다음 API는 AEM의 핵심입니다.

| API | 설명 |
|---|---|
| [Adobe Experience Manager as a Cloud Service](https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/index.html) | 페이지, 자산, 워크플로우 등과 같은 제품 추상 |
| [Granite UI](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/granite-ui/api/jcr_root/libs/granite/ui/index.html#) | Adobe의 개방형 웹 스택, 다양한 필수 구성 요소 제공(6.5 Granite 자료는 AEMaaCS에 적용됨) |
| [Coral UI](https://opensource.adobe.com/coral-spectrum/documentation/) | 사용자 경험에서 일관성을 제공하도록 설계된 Adobe의 클라우드 UI용 시각적 스타일 |

<!---
|Editor core JavaScript API reference|Provides all the base objects and concepts to support authoring of content resources|
--->

## 추가 프레임워크 {#additional-apis}

AEM은 많은 추가 오픈 소스 API를 사용합니다.

| API | 설명 |
|---|---|
| [Apache Sling](https://sling.apache.org/apidocs/sling11/) | JCR(Java Content Repository)을 사용하여 컨텐츠를 저장하고 관리하는 웹 프레임워크 |
| [Apache Jackrabbit Oak](https://jackrabbit.apache.org/oak/docs/oak_api/overview.html) | 최신 세계적 수준의 웹 사이트의 기반으로 사용할 확장 가능하고 고성능 계층적 Java Content Repository(JCR) 구현 |
| [Java Content Repository](https://www.adobe.io/experience-manager/reference-materials/spec/javax.jcr/javadocs/jcr-2.0/index.html) | JCR 버전 2.0의 사양 |
| [Apache Felix](https://felix.apache.org) | OSGi(Open Services Gateway Initiative) 프레임워크 및 서비스 플랫폼 구현 |

## API 기본 설정 지침 {#guidelines}

AEM은 다음 네 개의 기본 Java API 세트를 기본 설정의 내림차순으로 기반으로 구축됩니다.

| 우선 순위 | API | 설명 |
|---|---|---|
| 1 | [Adobe Experience Manager as a Cloud Service](https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/index.html) | 페이지, 자산, 워크플로우 등과 같은 제품 추상 |
| 2 | [Apache Sling](https://sling.apache.org/apidocs/sling11/) | 리소스, 값 맵 및 HTTP 요청과 같은 REST 및 리소스 기반 추상화. |
| 3 | [Apache Jackrabbit Oak](https://jackrabbit.apache.org/oak/docs/oak_api/overview.html) | 노드, 속성 및 세션과 같은 데이터 및 컨텐츠 추상. |
| 4 | [Apache Felix](https://felix.apache.org/) | 서비스 및 (OSGi) 구성 요소와 같은 OSGi 애플리케이션 컨테이너 추상. |

API가 AEM에서 제공되는 경우 Sling, JCR 및 OSGi보다 선호합니다. AEM에서 API를 제공하지 않는 경우 JCR 및 OSGi보다 Sling을 선호합니다.

>[!TIP]
>
>이러한 지침에 대한 자세한 내용은 문서를 참조하십시오 [Java API 우수 사례를 이해합니다.](https://experienceleague.adobe.com/docs/experience-manager-learn/foundation/development/understand-java-api-best-practices.html)

## AEM 배달 및 콘텐츠 관리 서비스 및 API {#delivery-apis}

AEM에서는 사용자 정의 가능한 구성 요소 및 콘텐츠 전달 옵션을 제공합니다.

| 기능 | 설명 |
|---|---|
| [핵심 구성 요소](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html) | AEM용 WCM(표준화된 웹 컨텐츠 관리) 구성 요소를 통해 개발 시간을 단축하고 웹 사이트의 유지 관리 비용을 절감할 수 있습니다 |
| [JSON 내보내기](/help/implementing/developing/components/json-exporter.md) | JSON 데이터 모델 형식으로 AEM 페이지의 콘텐츠를 전달합니다 |
| [구성 요소에 대해 JSON 내보내기 활성화](/help/implementing/developing/components/enabling-json-exporter.md) | 모델러 프레임워크를 기반으로 구성 요소 컨텐츠의 JSON 내보내기 생성 |
| [자산 API](/help/assets/mac-api-assets.md) | 이진, 메타데이터, 표현물 및 주석을 포함하여 자산에 대한 CRUD(Create-Read-update-delete) 작업을 허용합니다. AEM Assets HTTP API 를 참조하십시오 |
| [컨텐츠 조각 HTTP API](/help/assets/content-fragments/assets-api-content-fragments.md) | CRUD 작업을 통해 HTTP API를 통해 직접 컨텐츠 조각 컨텐츠에 액세스합니다 |
| [컨텐츠 조각 GraphQL API](/help/headless/graphql-api/content-fragments.md) | 헤드리스 CMS 구현에서 JavaScript 클라이언트에 컨텐츠 조각을 효율적으로 전달할 수 있도록 합니다 |
| [컨텐츠 조각 자산 HTTP API](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/assets/admin/mac-api-assets.html) | 지원되는 HTTP 자산 요청의 정확한 형식 |

## SPA 특정 API {#spa-apis}

AEM Single-Page Application(SPA) Editor SDK 프레임워크는 특정 JavaScript API 참조를 제공합니다.

| API | 설명 |
|---|---|
| [구성 요소 매핑](https://www.npmjs.com/package/@adobe/aem-spa-component-mapping) | 단일 페이지 애플리케이션에서 프런트엔드 구성 요소를 Adobe Experience Manager 리소스 유형(AEM 구성 요소)에 매핑할 수 있는 방법을 제공합니다 |
| [페이지 모델 관리자](https://www.npmjs.com/package/@adobe/aem-spa-page-model-manager) | Adobe Experience Manager 편집기와 SPA(Adobe Experience Manager Single Page Application) 편집기 간의 해석기입니다 |
| [React 편집 가능한 구성 요소](https://www.npmjs.com/package/@adobe/aem-react-editable-components) | Adobe Experience Manager 사이트 편집기를 시작할 수 있도록 React 구성 요소 및 통합 계층을 제공합니다 |
| [Angular 편집 가능한 구성 요소](https://www.npmjs.com/package/@adobe/aem-angular-editable-components) | Adobe Experience Manager 사이트 편집기를 시작할 수 있도록 Angular 구성 요소 및 통합 계층을 제공합니다 |

>[!TIP]
>
>다음을 확인하십시오 [SPA 소개 및 연습](/help/implementing/developing/hybrid/introduction.md) 단일 페이지 애플리케이션에 대한 자세한 정보.
