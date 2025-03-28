---
title: ' [!DNL Adobe Experience Manager] as a Cloud Service 최신 릴리스 정보'
description: ' [!DNL Adobe Experience Manager] as a Cloud Service 최신 릴리스 정보'
mini-toc-levels: 1
exl-id: a2d56721-502c-4f4e-9b72-5ca790df75c5
feature: Release Information
role: Admin
source-git-commit: 5a1c951813e026806aa3b5b23a912a48681f4505
workflow-type: tm+mt
source-wordcount: '1072'
ht-degree: 75%

---

# [!DNL Adobe Experience Manager] as a Cloud Service 최신 릴리스 정보 {#release-notes}

다음 섹션에서는 [!DNL Experience Manager] as a Cloud Service의 최신 기능 릴리스 정보에 대해 간략히 소개합니다.

>[!NOTE]
>
>여기에서 2023년 또는 2024년과 같은 이전 버전의 릴리스 정보로 이동할 수 있습니다.
>
>[!DNL Experience Manager] as a Cloud Service의 향후 기능 활성화에 대해 알아보려면 [Experience Manager 릴리스 로드맵](https://experienceleague.adobe.com/ko/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap)을 살펴보십시오.

>[!NOTE]
>
>Experience Cloud 릴리스 정보의 업데이트에 대한 월별 이메일 알림을 받아 보려면 [Adobe 우선순위 제품 업데이트](https://www.adobe.com/kr/subscription/priority-product-update.html)를 구독하십시오.

## 릴리스 일자 {#release-date}

[!DNL Adobe Experience Manager] as a [!DNL Cloud Service]의 현재 기능 릴리스(2025.3.0) 일자는 2025년 3월 27일 금요일입니다. 다음 기능 릴리스(2025.4.0)는 2025년 4월 24일에 예정되어 있습니다.

## 유지 관리 릴리스 정보 {#maintenance}

[ 여기](/help/release-notes/maintenance/latest.md)에서 최신 유지 관리 릴리스 정보를 확인할 수 있습니다.

<!-- 

## Release Video {#release-video}

Have a look at the February 2025 Release Overview video for a summary of the features added in the 2025.2.0 release:

>[!VIDEO](https://video.tv.adobe.com/v/3440920?quality=12)

-->

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### Dynamic Media의 새로운 기능 {#new-features-dynamic-media}

**Open API가 있는 Dynamic Media를 사용하여 제공되는 비디오에 대한 긴 양식 지원**

OpenAPI가 포함된 Dynamic Media는 이제 긴 양식 비디오를 지원합니다. 긴 형식의 비디오는 최대 50GB 및 2시간을 지원할 수 있습니다.

### Assets 보기의 새로운 기능 {#new-features-assets-view}


**루트 태그 지원**

이제 AEM Assets에서는 메타데이터 양식의 태그 속성을 사용자 지정 메타데이터에 매핑할 수 있습니다. 또한 관리자는 특정 루트 태그 및 루트 태그 아래에 있는 태그에 대한 액세스를 제한하여 사용자에 대한 태그 가용성을 제한할 수 있습니다.

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
> Java 21 **runtime**&#x200B;은(는) 2월에 개발/RDE 환경에 배포되었습니다. **4월 28일과 29일**&#x200B;에 단계/프로덕션 환경에 적용됩니다. Java 21(또는 Java 17)을 사용하여 **코드 빌드**&#x200B;는 Java 21 런타임과 독립적입니다. Java 21(또는 Java 17)을 사용하여 코드를 빌드하려면 명시적으로 단계를 수행해야 합니다.

### 더 많은 대상으로 AEM 로그 전달 - Beta 프로그램 {#log-forwarding-earlyadopter}

이제 Beta에서는 AEM 로그를 New Relic(HTTPS 사용), Amazon S3 및 Sumo Logic에 전달할 수 있습니다. AEM 로그(Apache/Dispatcher 포함)는 지원되지만 CDN 로그는 지원되지 않습니다. 액세스하려면 [aemcs-logforwarding-beta@adobe.com](mailto:aemcs-logforwarding-beta@adobe.com)에 전자 메일을 보내십시오.

Cloud Manager에서 로그를 다운로드할 수 있지만 많은 조직은 이러한 로그를 기본 로깅 대상으로 스트리밍하는 것이 좋습니다. AEM은 이미 (GA) AEM 및 Azure Blob Storage, Datadog, HTTPS, Elasticsearch(및 OpenSearch) 및 Splunk로의 CDN 로그 전달을 지원합니다. 이 기능은 셀프서비스 방식으로 구성되고 구성 파이프라인을 사용하여 배포됩니다.

자세한 내용은 [로그 전달 설명서](/help/implementing/developing/introduction/log-forwarding.md)를 참조하세요.

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
* [Sites 및 Assets 폴더 API](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/folders/)
* [Forms 커뮤니케이션 API](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/document/)

### 새로운 AEM Developer Console (공개 Beta) {#aem-developer-console-beta}

클라우드 환경에서 코드 디버깅을 위한 보다 인터랙티브한 경험을 제공하는 개선된 [AEM Developer Console](/help/implementing/developing/introduction/aem-developer-console.md)을 사용해 보십시오.

현재 AEM Developer Console에서 *새 콘솔 사용 가능* 버튼을 클릭하여 누구나 공개 Beta에 액세스할 수 있습니다. Adobe는 여러분의 피드백을 환영합니다. 의견이 있는 경우 [aemcs-new-devconsole-ui-beta@adobe.com](mailto:aemcs-new-devconsole-ui-beta@adobe.com)으로 이메일을 보내 주십시오.

## [!DNL Experience Manager] 안내서 {#guides}

[여기](https://experienceleague.adobe.com/ko/docs/experience-manager-guides/using/release-info/release-notes/cloud-release-notes/2024-releases/2410-release/2410-0-release/whats-new-2024-10-0)서 Adobe Experience Manager Guides 최신 릴리스의 새로운 기능과 향상된 기능의 전체 목록을 찾을 수 있습니다.

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
