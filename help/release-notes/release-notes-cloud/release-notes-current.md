---
title: ' [!DNL Adobe Experience Manager] as a Cloud Service 최신 릴리스 정보'
description: ' [!DNL Adobe Experience Manager] as a Cloud Service 최신 릴리스 정보'
mini-toc-levels: 1
exl-id: a2d56721-502c-4f4e-9b72-5ca790df75c5
feature: Release Information
role: Admin
source-git-commit: f81e8434029ade26dd2c30b249537699971e9a4b
workflow-type: tm+mt
source-wordcount: '1750'
ht-degree: 98%

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

[!DNL Adobe Experience Manager] as a [!DNL Cloud Service]의 현재 기능 릴리스(2025.1.0) 일자는 2025년 1월 30일입니다. 다음 기능 릴리스(2025.2.0)는 2025년 2월 27일에 예정되어 있습니다.

## 유지 관리 릴리스 정보 {#maintenance}

[ 여기](/help/release-notes/maintenance/latest.md)에서 최신 유지 관리 릴리스 정보를 확인할 수 있습니다.

<!-- 

## Release Video {#release-video}

Have a look at the January 2025 Release Overview video for a summary of the features added in the 2025.1.0 release:

>[!VIDEO](https://video.tv.adobe.com/v/3440920?quality=12)

-->

## [!DNL Experience Manager Sites] as a [!DNL Cloud Service] {#sites}

**콘텐츠 조각 편집기 댓글 기능이 이제 일반적으로 사용 가능합니다.**

AEM 콘텐츠 조각 편집기의 새롭고 현대화된 댓글 달기 서비스를 사용하면 AEM 콘텐츠 조각을 작성할 때 동료와 간편하게 공동 작업을 수행할 수 있습니다.
[자세히 보기](https://experienceleague.adobe.com/ko/docs/experience-manager-cloud-service/content/sites/administering/content-fragments/authoring?#commenting-on-your-fragment)

**콘텐츠 조각 편집기 및 관리자 사용자 인터페이스, 업데이트된 AEM as a Cloud Service 버전 지원**

새로운 콘텐츠 조각 관리자 및 편집기 사용자 인터페이스에 대해 지원되는 최소 AEM as a Cloud Service 버전은 이제 2023.8.13099입니다. 새 사용자 인터페이스의 일반 가용성 릴리스 이전의 버전은 더 이상 지원되지 않습니다.

### 얼리 어답터 프로그램 {#sites-early-adopter}

**향상된 콘텐츠 조각**

[고유 ID 기반 참조를 참조하는 콘텐츠 조각](/help/headless/graphql-api/uuid-reference-upgrade.md)이 개선되었습니다. 이를 통해 조각이 다른 위치로 이동한 경우에도 개별 콘텐츠 조각에 대한 GraphQL 쿼리가 안정적으로 유지될 수 있습니다. 이제 “ByID” 쿼리를 통해 가능해진 것입니다. 경로는 변경되어 잠재적으로 “ByPath” 쿼리를 중단시킬 수 있지만 UUID는 안정적입니다. 새 ID는 모든 쿼리나 기타 해당되는 API 요청에서 속성으로 반환될 수도 있습니다. 현재 제한 사항(2025.1): 페이지 참조는 아직 고유 ID로 지원되지 않습니다. 콘텐츠 조각에서 페이지를 참조하는 경우에는 이 기능을 사용하면 안 됩니다. 이러한 제한은 다음 AEM as a Cloud Service 릴리스에서 제거될 예정입니다.

**콘텐츠 조각 게재를 위한 AEM REST OpenAPI**

[콘텐츠 조각 게재를 위한 AEM REST OpenAPI](/help/headless/aem-rest-openapi-content-fragment-delivery.md)가 AEM as a Cloud Service에서 현재 사용 가능합니다.

### 더 이상 사용되지 않는 기능 {#sites-deprecated}

#### SPA 편집기 {#spa-editor}

[SPA 편집기](/help/implementing/developing/hybrid/introduction.md)는 릴리스 2025.1.0부터 새 프로젝트에 더 이상 사용되지 않습니다. SPA 편집기는 기존 프로젝트에서는 계속 지원되지만 새 프로젝트에는 사용해서는 안 됩니다.

AEM에서 Headless 콘텐츠를 관리하기 위한 권장 편집기는 다음과 같습니다.

* 시각적 편집을 위한 [범용 편집기](/help/edge/wysiwyg-authoring/authoring.md)
* 양식 기반 편집을 위한 [콘텐츠 조각 편집기](/help/assets/content-fragments/content-fragments-managing.md)

#### PWA 기능 {#pwa-features}

AEM Sites의 [PWA(progressive web app) 기능](/help/sites-cloud/authoring/sites-console/enable-pwa.md)은 릴리스 2025.1.0부터 새 프로젝트에서 더 이상 사용되지 않습니다. 이 기능은 기존 프로젝트에서는 계속 지원되지만 새 프로젝트에서는 사용해서는 안 됩니다.

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### AEM Assets의 새로운 기능 {#new-features-assets}

**Dynamic Media 템플릿**

사용하기 쉬운 WYSIWYG Dynamic Media 템플릿 편집기로 이미지와 텍스트 배너를 즉석에서 개인화하고, URL을 자사 또는 서드파티 애플리케이션에 임베드함으로써 배너 콘텐츠를 실시간으로 업데이트하여 매력적인 경험을 제공할 수 있습니다.

![동적 렌디션](/help/assets/assets/dm-templates-smart-text-resize.png)

**Dynamic Media 게재 보고서**

자산 수준 게재 카운트, 레퍼러 세부 정보, AEM Assets의 자산 경로 및 고유 자산 ID를 포함한 Dynamic Media를 통해 게재된 자산에 대한 게재 인사이트를 확인할 수 있습니다. AEM Assets 저장소 또는 특정 폴더 계층에 있는 모든 자산에 대한 보고서를 생성합니다. 이러한 인사이트를 통해 제공된 자산의 ROI를 측정하고, 채널 성과를 평가하고, 자산 관리에 대한 정보에 입각한 결정을 내릴 수 있습니다.

![동적 렌디션](/help/assets/assets/referrer.png)

**Dynamic Media 다중 오디오 및 캡션**

[Dynamic Media로 비디오의 다중 캡션 및 다중 오디오 트랙 지원](/help/assets/dynamic-media/video.md#about-msma) - 이제 기본 비디오에 여러 개의 캡션과 오디오 트랙을 손쉽게 추가할 수 있습니다. 즉, 이러한 기능을 통해 글로벌 대상자는 비디오에 액세스할 수 있습니다. 여러 언어로 글로벌 대상자에게 게시된 하나의 기본 비디오를 사용자 정의하고 지역별 액세스 가능성 가이드라인을 준수할 수 있습니다. 작성자는 사용자 인터페이스의 단일 탭에서 캡션 및 오디오 트랙을 관리할 수도 있습니다.

**Dynamic Adaptive Streaming over HTTP 지원**

새로운 프로토콜(DASH - Dynamic Adaptive Streaming over HTTP)이 Dynamic Media 비디오 게재(CMAF 활성화)에서 적응형 스트리밍을 위해 시작되었습니다.

* 적응형 스트리밍(DASH/HLS)은 비디오에 대한 더 나은 사용자 시청 경험을 보장합니다.

* DASH는 적응형 비디오 스트리밍을 위한 국제 표준 프로토콜이며 업계에서 널리 채택되고 있습니다.

**자산 관계**

이제 자산 보기의 간소화된 자산 세부 정보 패널에서 자산 관계를 보고 편집할 수 있습니다. 소스 및 파생과 같은 관계를 콘텐츠에 쉽게 추가하면 사용자가 관련성 있는 히어로 콘텐츠를 보다 효과적으로 찾을 수 있습니다.

**자산 재처리**

이제 자산 보기에서 폴더에서 사용할 수 있는 자산의 재처리가 지원됩니다. **전체 프로세스** 옵션을 사용하거나 기본 미리보기 렌디션, 메타데이터, 사후 처리 워크플로, 처리 프로필과 같은 고급 옵션을 사용할 수 있습니다.

### AEM Assets의 얼리 액세스 기능 {#early-access-features-assets}

**AI 생성 비디오 캡션**

Adobe Dynamic Media의 AI 생성 비디오 캡션은 인공 지능을 통해 비디오 콘텐츠에 대한 캡션을 자동으로 생성합니다. 이 기능은 정확한 실시간 캡션을 제공하여 접근성을 개선하고 사용자 경험을 향상시킬 수 있도록 설계되었습니다. 캡션은 원본 오디오, 추가 오디오 트랙 또는 비디오 속성 페이지의 “캡션 및 오디오” 탭에서 제공된 추가 캡션에서 생성됩니다. 60개 이상의 언어를 지원하므로 비디오를 게시하기 전에 캡션을 검토하고 미리 볼 수 있습니다.

## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

### AEM Forms의 새로운 기능 {#forms-new-features}

#### 게시 관리

[게시 관리](/help/forms/manage-publication.md#publish-forms-using-the-manage-publication-option) 워크플로우를 사용하여 일반적으로 작성자 인스턴스에서 게시 및 미리보기 인스턴스로 환경 간에 양식을 게시하거나 게시 취소할 수 있습니다. 이를 통해 사용자는 간소화된 방식으로 콘텐츠를 게시 또는 게시 취소하거나 게시 일정을 예약할 수 있습니다.

#### 핵심 구성 요소 기반 적응형 양식의 초안 자동 저장

이제 사용자는 부분적으로 완료된 양식을 초안으로 자동 저장하는 [자동 저장 기능](/help/forms/save-core-component-based-form-as-draft.md)을 활용할 수 있습니다. 나중에 돌아와 동일한 디바이스 또는 다른 디바이스에서 작성을 마칠 수 있습니다. 이 기능을 사용하면 사용자가 처음부터 양식을 작성할 필요가 없으므로 양식 폐기를 방지하여 전환율을 높일 수 있습니다.

#### 규칙 편집기 개선 사항

핵심 구성 요소 기반 적응형 양식의 경우, [호출 서비스의 출력을 사용하여 드롭다운 옵션을 채우고, 반복 가능한 패널을 설정하고, 개별 패널을 설정](/help/forms/invoke-service-enhancements-rule-editor.md)할 수 있습니다. 이 출력은 다른 필드의 유효성을 검사하는 데 사용할 수도 있습니다.

#### 패널 레이아웃의 탐색 버튼으로 사용자 경험 개선

이제 가로 탭, 세로 탭, 아코디언, 마법사 등의 탐색 버튼을 패널 레이아웃에 추가할 수 있습니다. 이러한 버튼은 [패널 간 전환을 간소화하고 선택된 패널에 초점을 맞춤으로써 사용자 경험을 향상시킵니다](/help/forms/rule-editor-core-components-usecases.md#navigating-among-panels-using-button).


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

이제 Java 21로 코드를 작성할 수 있습니다. 여기에는 새로운 기능(예: switch 문에 대한 패턴 매칭, 봉인된 클래스)과 성능 개선이 포함됩니다. Java 17 빌드도 새롭게 지원됩니다. Maven 프로젝트 및 라이브러리 버전 업데이트를 포함한 구성 단계는 [빌드 환경](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/build-environment-details.md#using-java-support) 문서를 참조하십시오.

Java 17 또는 21 빌드가 감지되면 성능이 더 뛰어난 Java 21 **런타임**&#x200B;이 자동으로 배포됩니다. 그러나 Java 11로 빌드된 환경에서는 Java 21 런타임을 선택하는 것도 좋습니다. 이를 위해서는 [aemcs-java-adopter@adobe.com](mailto:aemcs-java-adopter@adobe.com)로 이메일을 보내 문의하시기 바랍니다. [Java 21 런타임 요구 사항](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/build-environment-details.md#runtime-requirements)에 대해 알아보십시오.

>[!IMPORTANT]
>
> Java 21 **런타임**&#x200B;은 Java 17 또는 21로 이미 빌드된 환경을 제외한 **모든** 환경에 점진적으로 배포될 예정입니다. 2월에는 샌드박스 및 개발/RDE 환경부터 시작되며, 4월에는 스테이지 및 프로덕션 환경으로 확대될 예정입니다.

### 샌드박스 프로그램은 구성 파이프라인을 지원합니다. {#sandbox-config-pipelines}

샌드박스 프로그램은 이제 구성 파이프라인을 지원하며, 이를 Cloud Manager에서 구성하여 git에서 지속되는 YAML 파일을 배포할 수 있습니다.

콘텐츠 전송 네트워크 구성, 로그 전달, 버전 삭제/감사 로그 삭제 유지 관리 작업을 설정할 수 있는 구성 파이프라인에 대해 [자세히 알아보십시오](/help/operations/config-pipeline.md).

### OpenAPI 기반 API - 얼리 어답터 프로그램 {#open-apis-earlyadopter}

개발자는 AEM as Cloud Service 기능을 자신의 애플리케이션과 도구에 긴밀하게 통합할 수 있습니다. 새 AEM as a Cloud Service API는 OpenAPI 사양을 따르며, 일관되고 문서화가 잘 되며 사용자 친화적인 것을 목표로 합니다. 인증이 필요한 엔드포인트에 대한 자격 증명은 Adobe Developer Console 프로젝트를 만드는 방식으로 생성됩니다.

[OpenAPI 기반 AEM API](/help/implementing/developing/open-api-based-apis.md)에 대해 자세히 알아보고 구성 및 사용 방법을 안내하는 [전체 튜토리얼](https://experienceleague.adobe.com/ko/docs/experience-manager-learn/cloud-service/aem-apis/invoke-openapi-based-aem-apis)을 살펴보십시오.

구체적으로 아래에 나열된 API 엔드포인트가 얼리 어답터 프로그램의 일부로 제공됩니다. 관심이 있는 경우 [aem-apis@adobe.com](mailto:aem-apis@adobe.com)에 이메일로 문의하여 사용 계획을 설명해 주십시오.

* [Sites 콘텐츠 조각 API](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/stable/sites/)
* [Assets API](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/assets/author/)
* [Sites 및 Assets 폴더 API](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/folders/)
* [Forms 커뮤니케이션 API](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/document/)

### 에지 컴퓨팅 - 피드백 요청 {#edge-computing-feedback}

에지 컴퓨팅은 데이터 처리를 브라우저에 더 가까운 위치에서 수행하여, 지연 시간 감소와 같은 이점을 제공합니다. Adobe는 이 기술이 AEM 게시 게재 및 Edge Delivery Services 프로젝트에 유용할 것이라고 생각하는지에 대한 귀하의 의견을 듣고 싶습니다. 또한 제품 로드맵에 반영할 수 있도록 이 기술을 어떻게 활용할 계획인지 알려 주십시오. 질문과 의견을 [aemcs-edgecompute-feedback@adobe.com](mailto:aemcs-edgecompute-feedback@adobe.com)에 이메일로 보내 주십시오.

### 새로운 AEM Developer Console (공개 Beta) {#aem-developer-console-beta}

클라우드 환경에서 코드 디버깅을 위한 보다 인터랙티브한 경험을 제공하는 개선된 [AEM Developer Console](/help/implementing/developing/introduction/aem-developer-console.md)을 사용해 보십시오.

현재 AEM Developer Console에서 *새 콘솔 사용 가능* 버튼을 클릭하여 누구나 공개 Beta에 액세스할 수 있습니다. Adobe는 여러분의 피드백을 환영합니다. 의견이 있는 경우 [aemcs-new-devconsole-ui-beta@adobe.com](mailto:aemcs-new-devconsole-ui-beta@adobe.com)으로 이메일을 보내 주십시오.

## [!DNL Experience Manager] 안내서 {#guides}

[여기](https://experienceleague.adobe.com/ko/docs/experience-manager-guides/using/release-info/release-notes/cloud-release-notes/2024-releases/2410-0-release/whats-new-2024-10-0)서 Adobe Experience Manager Guides 최신 릴리스의 새로운 기능과 향상된 기능의 전체 목록을 찾을 수 있습니다.

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
