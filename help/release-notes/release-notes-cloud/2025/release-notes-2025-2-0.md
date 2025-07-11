---
title: ' [!DNL Adobe Experience Manager] as a Cloud Service의 2025.2.0 릴리스 정보입니다.'
description: ' [!DNL Adobe Experience Manager] as a Cloud Service의 2025.2.0 릴리스 정보입니다.'
feature: Release Information
role: Admin
exl-id: b893663d-35f1-43ae-a029-4c249b117f2d
source-git-commit: 403ffbede5438131d0b0e770215b990e2d16c018
workflow-type: tm+mt
source-wordcount: '1527'
ht-degree: 95%

---

# [!DNL Adobe Experience Manager] as a Cloud Service 2025.2.0 릴리스 정보 {#release-notes}

다음 섹션에서는 [!DNL Experience Manager] as a Cloud Service의 2025.2.0 버전 기능 릴리스 정보에 대해 간략히 소개합니다.

>[!NOTE]
>
>여기에서 2023년 또는 2024년과 같은 이전 버전의 릴리스 정보로 이동할 수 있습니다.
>
>[!DNL Experience Manager] as a Cloud Service의 향후 기능 활성화에 대해 알아보려면 [Experience Manager 릴리스 로드맵](https://experienceleague.adobe.com/ko/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap)을 살펴보십시오.

>[!NOTE]
>
>Experience Cloud 릴리스 정보의 업데이트에 대한 월별 이메일 알림을 받아 보려면 [Adobe 우선순위 제품 업데이트](https://www.adobe.com/kr/subscription/priority-product-update.html)를 구독하십시오.

## 릴리스 일자 {#release-date}

[!DNL Adobe Experience Manager] as a [!DNL Cloud Service]의 현재 기능 릴리스(2025.2.0) 일자는 2025년 3월 4일입니다. 다음 기능 릴리스(2025.3.0)는 2025년 3월 27일에 예정되어 있습니다.

## 유지 관리 릴리스 정보 {#maintenance}

[ 여기](/help/release-notes/maintenance/latest.md)에서 최신 유지 관리 릴리스 정보를 확인할 수 있습니다.

## 릴리스 비디오 {#release-video}

2025년 2월 릴리스 개요 비디오를 통해 2025.2.0 릴리스에 추가된 기능에 대한 간단한 요약을 살펴보십시오.

>[!VIDEO](https://video.tv.adobe.com/v/3458080?quality=12)

## [!DNL Experience Manager Sites] as a [!DNL Cloud Service] {#sites}

### AEM Sites의 새로운 기능 {#new-features-sites}

**콘텐츠 조각 자동 태그 지정**

콘텐츠 조각을 만들 때 이제 콘텐츠 모델에 할당된 태그를 자동으로 상속할 수 있습니다. 이를 통해 콘텐츠 조각에 저장된 콘텐츠를 손쉽게 자동 분류할 수 있습니다.

**콘텐츠 조각 UUID 지원**

콘텐츠 조각 UUID 지원은 이제 GA 상태입니다. 이 새로운 기능은 AEM 내에서 이동, 이름 바꾸기, 롤아웃과 같이 경로가 자동으로 조정되는 작업의 경로 기반 동작을 변경하지 않지만, 특히 ByPath 쿼리로 개별 조각을 직접 타기팅하는 GraphQL 쿼리를 사용할 때 콘텐츠 조각의 외부 사용을 더 쉽고 안정적으로 만들 수 있습니다. 이러한 쿼리는 조각 경로가 변경되면 중단될 수 있습니다. 새로운 ById 쿼리 유형을 사용하면 경로가 변경되어도 조각의 UUID는 변경되지 않으므로 쿼리가 안정적으로 유지됩니다.

**콘텐츠 조각 편집기 및 GraphQL에서의 OpenAPI 포함 Dynamic Media 지원**

콘텐츠 조각이 아닌 다른 AEM as a Cloud Service 프로그램에 저장된 자산이며 OpenAPI 기능이 포함된 새로운 Dynamic Media를 통해 활성화된 자산은 이제 콘텐츠 조각에서 사용할 수 있습니다. 새로운 콘텐츠 조각 편집기의 이미지 선택기를 사용하면 이제 조각에서 참조할 이미지 자산의 소스로 “원격” 저장소를 선택할 수 있습니다. 또한 AEM GraphQL을 사용하여 이러한 콘텐츠 조각을 게재할 때 JSON 응답에는 이제 원격 자산에 대한 필수 속성(assetId, repositoryId)이 포함되므로 클라이언트 애플리케이션에서 해당 OpenAPI 포함 Dynamic Media URL을 만들어 이미지를 가져올 수 있습니다.

**콘텐츠 조각 편집기 롤아웃**

[통합 셸](/help/overview/aem-cloud-service-on-unified-shell.md)(Spectrum-UI 사용)을 사용하여 AEM as a Cloud Service에서 새 [콘텐츠 조각 편집기](/help/sites-cloud/administering/content-fragments/authoring.md)를 계속 활성화합니다. 2024년 11월에 모든 클라우드 서비스 개발자 환경의 기본값이 된 후 2025년 4월 1일에 모든 스테이징 환경의 기본값으로 설정되고, 2025년 5월 1일에 모든 프로덕션 환경의 기본값으로 설정됩니다. 어떠한 경우에도 사용자는 AEM Touch UI에서 기존 콘텐츠 조각 편집기로 돌아갈 수 있습니다.

**번역 HTTP API**

한동안 얼리 어답터 모드에 있었던 AEM 번역 HTTP REST API는 이제 GA 상태입니다. 설명서는 여기에서 [을(를) 찾을 수 있습니다.](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/stable/translation/) API를 사용하면 AEM의 콘텐츠에 대한 번역 관리 프로세스에서 필요한 단계를 자동화할 수 있습니다.

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### AEM Assets의 새로운 기능 {#new-features-assets}

**Dynamic Media의 새로운 패키징 구조**

이제 시장 기대에 보다 잘 부합하고 추적을 지원할 수 있도록 새롭게 구성된 Dynamic Media 패키징 구조가 제공됩니다. 새로운 패키징 구조는 다음과 같이 구성됩니다.

* Dynamic Media Prime에는 OpenAPI 및 비디오를 포함한 Dynamic Media가 포함되어 게재 방식이 개선됩니다.

* Dynamic Media Ultimate에는 보다 높은 사용 요구 사항을 충족하기 위해 게재 및 변환 기능이 추가되어 있습니다.

새로운 패키징 구조의 혜택을 누리려면 Assets as a Cloud Service Prime 또는 Ultimate을 보유하고 있어야 합니다.

**AI 생성 비디오 캡션**

Adobe Dynamic Media의 AI 생성 비디오 캡션은 인공 지능을 통해 비디오 콘텐츠에 대한 캡션을 자동으로 생성합니다. 이 기능은 정확한 캡션을 제공하여 접근성을 개선하고 사용자 경험을 향상시킬 수 있도록 설계되었습니다. 캡션은 원본 오디오, 추가 오디오 트랙 또는 비디오 속성 페이지의 “캡션 및 오디오” 탭에서 제공된 추가 캡션에서 생성됩니다. 60개 이상의 언어를 지원하므로 비디오를 게시하기 전에 캡션을 검토하고 미리 볼 수 있습니다.

**검색 필터 사용자 정의**

사용자 정의 검색 필터를 사용하면 관련 정보를 검색할 때 정확도와 효율성이 향상됩니다. 브랜드, 제품, 카테고리 또는 기타 주요 식별자와 같은 특정 속성에 따라 데이터를 필터링하여 더욱 맞춤화된 검색이 가능합니다. 이를 통해 구성이 개선되고, 관련 없는 결과를 걸러내는 데 소요되는 시간이 줄어들며, 더 빠른 의사 결정이 가능해집니다. 또한 대규모 데이터 세트를 탐색하고 분석하기가 더 쉬워지므로 확장성도 확보됩니다.

![검색 필터 사용자 정의](/help/assets/assets/custom-search-filters.png)

### Content Hub의 얼리 액세스 기능 {#early-access-content-hub}

이제 Content Hub에서 기존의 정적 렌디션 외에도 동적 및 스마트 자르기 렌디션을 보고 다운로드할 수 있습니다. Content Hub 관리자는 구성 사용자 인터페이스를 사용하여 이러한 렌디션의 가용성을 구성할 수도 있습니다.

![동적 렌디션](/help/assets/assets/download-single-asset-renditions-dynamic.png)

## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

### AEM Forms의 얼리 액세스 기능 {#forms-new-early-access-features}

AEM Forms 얼리 액세스 프로그램은 최첨단 혁신에 독점적으로 액세스할 수 있는 특별한 기회를 제공하며, 혁신의 발전을 구체화하는 데 도움을 줍니다.

이 릴리스 정보에는 현재 릴리스에서 제공되는 혁신 사항이 나열되어 있습니다. 얼리 액세스 프로그램에서 사용할 수 있는 전체 혁신 목록은 [AEM Forms 얼리 액세스 프로그램 설명서](/help/forms/early-access-ea-features.md)를 참조하십시오.

#### 적응형 양식의 HTML 이메일 템플릿

적응형 양식을 사용하면 [HTML 이메일 템플릿](/help/forms/html-email-templates-in-adaptive-forms.md)을 사용할 수 있습니다. HTML 이메일 템플릿을 사용하면 양식을 제출할 때 내용이 풍부하고 개인화되고 시각적으로 매력적인 이메일을 보낼 수 있습니다. 이러한 이메일은 양식 데이터로 사용자 정의할 수 있으며, 이미지와 링크 등 다양한 이메일 태그를 사용하여 개선할 수 있습니다. 적응형 양식을 사용하면 HTML 템플릿이 포함된 파일을 업로드하거나 일반 텍스트 편집기를 사용하여 이러한 템플릿을 만들 수 있습니다.

![HTML 이메일 템플릿](/help/forms/assets/html-email.png)

#### 향상된 클라우드 스토리지 지원: Azure Blob 스토리지에 직접 PDF 업로드

AEM Forms Document Generation API를 사용하면 이제 [생성된 PDF 문서를 Azure Blob 스토리지에 직접 업로드](/help/forms/early-access-ea-features.md#doc-generation-api)할 수 있습니다. 이러한 향상된 기능을 통해 저장 및 검색을 간소화하여 클라우드 워크플로와의 통합과 효율성이 개선됩니다.

## [!DNL Experience Manager] as a [!DNL Cloud Service] Foundation {#foundation}

### Java 21 지원 {#java21}

1월 릴리스 정보에서 언급한 바와 같이 이제 Java 21로 코드를 작성할 수 있습니다. 여기에는 새로운 기능(예: switch 문에 대한 패턴 매칭, 봉인된 클래스)과 성능 개선이 포함됩니다. Java 17 빌드도 새롭게 지원됩니다. Maven 프로젝트 및 라이브러리 버전 업데이트를 포함한 구성 단계는 [빌드 환경](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/build-environment-details.md#using-java-support) 문서를 참조하십시오.

Java 17 또는 21 빌드가 감지되면 성능이 더 뛰어난 Java 21 **런타임**&#x200B;이 자동으로 배포됩니다. 그러나 Java 11로 빌드된 환경에서는 Java 21 런타임을 선택하는 것도 좋습니다. 이를 위해서는 [aemcs-java-adopter@adobe.com](mailto:aemcs-java-adopter@adobe.com)로 이메일을 보내 문의하시기 바랍니다. [Java 21 런타임 요구 사항](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/build-environment-details.md#runtime-requirements)에 대해 알아보십시오.

>[!IMPORTANT]
>
> 지난 2월에 Java 21 **런타임**&#x200B;이 dev/RDE 환경에 배포되었습니다(이미 Java 17 또는 21로 빌드되어 Java 21 런타임이 있는 환경 제외). Java 21은 4월에 스테이지/프로덕션 환경에 적용될 예정입니다.

### 에지 컴퓨팅 - 피드백 요청 {#edge-computing-feedback}

에지 컴퓨팅은 데이터 처리를 브라우저에 더 가까운 위치에서 수행하여, 지연 시간 감소와 같은 이점을 제공합니다. Adobe는 이 기술이 AEM 게시 게재 및 Edge Delivery Services 프로젝트에 유용할 것이라고 생각하는지에 대한 귀하의 의견을 듣고자 합니다. 또한 제품 로드맵에 반영할 수 있도록 이 기술을 어떻게 활용할 계획인지 알려 주십시오.

가능한 일부 사용 사례는 다음과 같습니다.
* 콘텐츠에 대한 액세스를 제어하기 위해 IdP를 통한 인증
* 지리적 위치, 디바이스 유형, 사용자 속성 등을 기반으로 동적(개인화, 지역화) 콘텐츠 렌더링
* 고급 이미지 조작
* CDN과 원본 간 미들웨어
* 브라우저와 서드파티 API 사이의 레이어, API 응답을 다시 포맷하기 위한 목적
* 여러 출처로부터 데이터를 집계하여 클라이언트 브라우저가 데이터를 보다 쉽게 렌더링할 수 있도록 함

질문과 의견을 이메일([aemcs-edgecompute-feedback@adobe.com](mailto:aemcs-edgecompute-feedback@adobe.com))로 보내 주십시오.

### OpenAPI 기반 API - 얼리 어답터 프로그램 {#open-apis-earlyadopter}

개발자는 AEM as Cloud Service 기능을 자신의 애플리케이션과 도구에 긴밀하게 통합할 수 있습니다. 새 AEM as a Cloud Service API는 OpenAPI 사양을 따르며, 일관되고 문서화가 잘 되며 사용자 친화적인 것을 목표로 합니다. 인증이 필요한 엔드포인트에 대한 자격 증명은 Adobe Developer Console 프로젝트를 만드는 방식으로 생성됩니다.

[OpenAPI 기반 AEM API](/help/implementing/developing/open-api-based-apis.md)에 대해 자세히 알아보고 구성 및 사용 방법을 안내하는 [전체 튜토리얼](https://experienceleague.adobe.com/ko/docs/experience-manager-learn/cloud-service/aem-apis/invoke-openapi-based-aem-apis)을 살펴보십시오.

구체적으로 아래에 나열된 API 엔드포인트가 얼리 어답터 프로그램의 일부로 제공됩니다. 관심이 있는 경우 [aem-apis@adobe.com](mailto:aem-apis@adobe.com)에 이메일로 문의하여 사용 계획을 설명해 주십시오.

* [Sites 콘텐츠 조각 API](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/stable/sites/)
* [Assets API](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/assets/author/)
* 사이트 및 Assets 폴더 API
* [Forms 커뮤니케이션 API](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/document/)

### 새로운 AEM Developer Console (공개 Beta) {#aem-developer-console-beta}

클라우드 환경에서 코드 디버깅을 위한 보다 인터랙티브한 경험을 제공하는 개선된 [AEM Developer Console](/help/implementing/developing/introduction/aem-developer-console.md)을 사용해 보십시오.

현재 AEM Developer Console에서 *새 콘솔 사용 가능* 버튼을 클릭하여 누구나 공개 Beta에 액세스할 수 있습니다. Adobe는 여러분의 피드백을 환영합니다. 의견이 있는 경우 [aemcs-new-devconsole-ui-beta@adobe.com](mailto:aemcs-new-devconsole-ui-beta@adobe.com)으로 이메일을 보내 주십시오.

## [!DNL Experience Manager] 안내서 {#guides}

[여기](https://experienceleague.adobe.com/ko/docs/experience-manager-guides/using/release-info/release-notes/cloud-release-notes/2025-releases/2502-release/whats-new-2025-02-0)서 Adobe Experience Manager Guides 최신 릴리스의 새로운 기능과 향상된 기능의 전체 목록을 찾을 수 있습니다.

## Cloud Manager {#cloud-manager}

[여기](/help/implementing/cloud-manager/release-notes/current.md)서 Cloud Manager 월별 릴리스의 전체 목록을 찾을 수 있습니다.

## 마이그레이션 도구 {#migration-tools}

[여기](/help/journey-migration/release-notes/release-notes-migration-tools-current.md)서 마이그레이션 도구의 전체 목록을 찾을 수 있습니다.

## 범용 편집기 {#universal-editor}

[여기](/help/release-notes/universal-editor/current.md)서 범용 편집기의 전체 목록을 찾을 수 있습니다.

## 변형 생성 {#generate-variations}

[여기](/help/generative-ai/release-notes-generate-variations.md)서 변형 생성의 전체 목록을 찾을 수 있습니다.

## Experience Cloud 릴리스 정보 {#experience-cloud}

다른 Experience Cloud 애플리케이션 릴리스에 대한 정보는 [여기](https://experienceleague.adobe.com/ko/docs/release-notes/experience-cloud/current)서 확인할 수 있습니다.
