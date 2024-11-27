---
title: ' [!DNL Adobe Experience Manager] as a Cloud Service 최신 릴리스 정보'
description: ' [!DNL Adobe Experience Manager] as a Cloud Service 최신 릴리스 정보'
mini-toc-levels: 1
exl-id: a2d56721-502c-4f4e-9b72-5ca790df75c5
feature: Release Information
role: Admin
source-git-commit: d424b6f2e0a2ec40ab607dcbdcba3120c7f45a58
workflow-type: tm+mt
source-wordcount: '1778'
ht-degree: 39%

---

# [!DNL Adobe Experience Manager] as a Cloud Service 최신 릴리스 정보 {#release-notes}

다음 섹션에서는 [!DNL Experience Manager] as a Cloud Service의 최신 버전 기능 릴리스 정보에 대해 간략히 소개합니다.

>[!NOTE]
>
>여기에서 2022년 또는 2023년과 같은 이전 버전의 릴리스 정보로 이동할 수 있습니다.
>
>[!DNL Experience Manager] as a Cloud Service의 향후 기능 활성화에 대해 알아보려면 [Experience Manager 릴리스 로드맵](https://experienceleague.adobe.com/ko/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap)을 살펴보십시오.

>[!NOTE]
>
>Experience Cloud 릴리스 정보의 업데이트에 대한 월별 이메일 알림을 받아 보려면 [Adobe 우선순위 제품 업데이트](https://www.adobe.com/kr/subscription/priority-product-update.html)를 구독하십시오.

## 릴리스 일자 {#release-date}

[!DNL Cloud Service] 현재 기능 릴리스(2024.11.0)인 [!DNL Adobe Experience Manager]의 릴리스 날짜는 2024년 11월 21일입니다. 다음 기능 릴리스(2025.1.0)는 2024년 1월 30일에 예정되어 있습니다.

## 유지 관리 릴리스 정보 {#maintenance}

[ 여기](/help/release-notes/maintenance/latest.md)에서 최신 유지 관리 릴리스 정보를 확인할 수 있습니다.

<!-- ## Release Video {#release-video}

Have a look at the November 2024 Release Overview video for a summary of the features added in the 2024.11.0 release:

>[!VIDEO](https://video.tv.adobe.com/v/3434847?quality=12)

-->

## [!DNL Experience Manager Sites] as a [!DNL Cloud Service] {#sites}

유니버설 편집기가 작성된 **[!DNL Edge Delivery Services]페이지 템플릿**

Edge Delivery 페이지를 페이지 템플릿으로 빠르게 전환합니다. 빈 페이지가 아닌 사전 정의된 구조 및 콘텐츠로 새 페이지를 시작할 수 있습니다. [자세한 내용](/help/sites-cloud/authoring/universal-editor/templates.md).

AEM 인스턴스를 통해 게시하기 위한 **[!DNL Edge Delivery Services]CSV 가져오기**

즐겨 사용하는 스프레드시트 도구에서 Edge Delivery 스프레드시트 데이터(예: 리디렉션)를 효율적으로 관리하고 새 CSV 가져오기를 통해 AEM에 업로드합니다. [자세한 내용](/help/edge/wysiwyg-authoring/tabular-data.md#importing).

### AEM Sites의 프리릴리스 기능

[고유 ID 기반 참조와 함께 콘텐츠 조각을 참조](/help/headless/graphql-api/uuid-reference-upgrade.md)하여 에셋 또는 조각을 이동할 때에도 유효한 링크가 유지되도록 개선하므로 업데이트 또는 다시 게시할 필요가 없습니다. 현재 제한 사항: 페이지 참조는 아직 고유 ID로 지원되지 않습니다. 페이지가 콘텐츠 조각에서 참조되는 경우 이 기능을 사용해서는 안 됩니다.

### 얼리 어답터 프로그램 {#sites-early-adopter}

**콘텐츠 조각 게재를 위한 AEM REST OpenAPI**

[콘텐츠 조각 게재를 위한 AEM REST OpenAPI](/help/headless/aem-rest-openapi-content-fragment-delivery.md)가 AEM as a Cloud Service에서 현재 사용 가능합니다.

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### Dynamic Media의 조기 액세스 기능 {#dm-early-access}

**AI 생성 비디오 캡션**

Adobe Dynamic Media의 AI 생성 비디오 캡션은 인공 지능을 통해 비디오 콘텐츠에 대한 캡션을 자동으로 생성합니다. 이 기능은 정확한 실시간 캡션을 제공하여 접근성을 개선하고 사용자 경험을 향상시킬 수 있도록 설계되었습니다. AI는 비디오의 오디오 트랙을 분석하여 음성을 기록하고 캡션을 생성하며, 해당 캡션은 정확성이나 사용자 정의를 위해 편집할 수 있습니다. 이러한 캡션은 접근성 요구 사항을 충족하며, 텍스트 기반 비디오 지원에 의존하거나 이를 선호하는 대상자의 비디오 참여를 개선하는 데 도움이 됩니다.

Dynamic Media 계정에서 AI 생성 캡션 지원에 얼리 액세스하려면 [Adobe 고객 지원 사례를 작성하고 제출](/help/assets/dynamic-media/video.md##enable-dash)하십시오.

**Dynamic Media 배달 보고서**

자산 수준 게재 카운트, 레퍼러 정보, Dynamic Media의 자산 경로 및 고유 자산 ID를 사용하여 AEM Assets으로 게재된 자산에 대한 게재 인사이트를 얻을 수 있습니다. Dynamic Media for AEM Assets 저장소 또는 AEM Assets의 특정 폴더 계층 구조를 통해 전달되는 모든 자산에 대해 보고서를 생성할 수 있습니다. 인사이트를 통해 제공된 자산의 ROI를 측정하고, 채널 성과를 측정하며, 자산에 대한 올바른 자산 관리 작업을 수행할 수 있습니다.

Dynamic Media 계정에서 Dynamic Media 배달 보고서에 일찍 액세스하려면 [Adobe 고객 지원 사례를 만들어 제출](https://helpx.adobe.com/kr/enterprise/using/support-for-experience-cloud.html)하세요.

### Assets 보기의 새로운 기능 {#assets-view-new-features}

**Dynamic Media 패널**

이제 Assets 보기를 사용하여 사용 가능한 별도의 패널에서 OpenAPI 렌디션을 사용하여 Dynamic Media 및 Dynamic Media에 액세스할 수 있습니다. 에셋 및 렌디션 유형에 따라 게재 URL을 복사하거나 렌디션을 다운로드하도록 선택할 수 있습니다. 자세한 내용은 [Dynamic Media 렌디션](/help/assets/renditions.md#dynamic-media-renditions) 및 [OpenAPI 기능이 있는 Dynamic Media 렌디션](/help/assets/renditions.md#dm-with-openapi-renditions)을 참조하십시오.

![동적 변환](/help/assets/assets/dm-scene7-renditions.png)

## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

### AEM Forms의 새로운 기능 {#forms-new-features}

* **[Adobe Sign 범위 쉽게 업데이트](/help/forms/adobe-sign-integration-adaptive-forms.md)**: Adobe Sign 구성의 범위를 AEM 클라우드 구성 페이지에서 직접 수정할 수 있습니다. 이를 통해 기존 구성을 더 빠르고 쉽게 업데이트할 수 있습니다.

* **[적응형 양식에 대한 비동기 기능 지원](/help/forms/using-async-funct-in-rule-editor.md)**: 적응형 양식에 외부 프로세스나 데이터 검색을 기다리는 등의 비동기 작업이 필요한 경우, 이러한 작업을 사용자 정의 함수로 구현하고 규칙 편집기에서 구성할 수 있습니다.

### AEM Forms의 프리릴리스 기능 {#forms-new-prerelease-features}

* **게시 관리**: 게시 관리 워크플로를 사용하여 일반적으로 작성자 인스턴스에서 게시 및 미리보기 인스턴스로 환경 간에 양식을 게시하거나 게시 취소할 수 있습니다. 간소화된 방식으로 콘텐츠 게시를 게시, 게시 취소 또는 예약할 수 있습니다.

* **[핵심 구성 요소 기반 적응형 양식의 초안 자동 저장](/help/forms/save-core-component-based-form-as-draft.md)**: 사용자는 이제 자동 저장 기능을 통해 작성 중인 양식을 초안으로 자동 저장할 수 있습니다. 나중에 돌아와 동일한 디바이스 또는 다른 디바이스에서 작성을 마칠 수 있습니다. 이 기능을 통해 사용자가 처음부터 양식을 작성할 필요가 없으므로 양식 폐기를 방지하여 전환율을 높일 수 있습니다.

* **[규칙 편집기 개선 사항](/help/forms/invoke-service-enhancements-rule-editor.md)**: 핵심 구성 요소 기반의 적응형 Forms의 경우 이제 Invoke Service의 출력을 사용하여 드롭다운 옵션을 채우고, Invoke Service의 출력을 사용하여 반복 가능한 패널을 설정하고, Invoke Service의 출력을 사용하여 개별 패널을 설정하고, Invoke Service의 출력 매개 변수를 사용하여 다른 필드의 유효성을 확인할 수 있습니다.

* **[사용자 경험 향상을 위한 패널 레이아웃 내 탐색 버튼 추가](/help/forms/rule-editor-core-components-usecases.md#navigating-among-panels-using-button)**: 이제 가로 탭, 세로 탭, 아코디언 또는 마법사와 같은 탐색 버튼을 패널 레이아웃에 추가할 수 있습니다. 이러한 버튼은 패널 간 전환을 간소화하고 선택된 패널에 초점을 맞춤으로써 사용자 경험을 향상시킵니다.


### AEM Forms의 얼리 액세스 기능 {#forms-new-early-access-features}

AEM Forms 얼리 액세스 프로그램은 최첨단 혁신에 독점적으로 액세스할 수 있는 특별한 기회를 제공하며, 혁신의 발전을 구체화하는 데 도움을 줍니다.

이 릴리스 정보에는 현재 릴리스에서 제공되는 혁신 사항이 나열되어 있습니다. 얼리 액세스 프로그램에서 사용할 수 있는 전체 혁신 목록은 [AEM Forms 얼리 액세스 프로그램 설명서](/help/forms/early-access-ea-features.md)를 참조하십시오.

#### 통합

* **[Adobe Marketo Engage과 적응형 Forms 통합](/help/forms/integrate-form-to-marketo-engage.md)**: 이제 AEM Formsas a Cloud Service 에 적응형 Forms과 Adobe Marketo Engage을 연결하는 사용하기 쉬운 옵션이 포함되어 있습니다. 이 통합을 통해 Marketo Engage의 잠재 고객 캡처 및 관련 사용자 지정 개체로 직접 적응형 Forms을 만들 수 있습니다. 이제 양식 필드에 Marketo Engage의 데이터를 미리 채우고 데이터를 다시 제출하여 스마트 캠페인 및 이메일 자동화와 같은 워크플로우를 자동화할 수 있습니다. 또한 Munchkin 라이브러리와 적응형 양식을 연결하여 방문 횟수, 클릭 수 및 양식 제출 횟수를 추적할 수도 있습니다.

#### 적응형 Forms 및 HTML5 Forms

* **[기존 XFA 템플릿을 기반으로 적응형 Forms 만들기](/help/forms/create-adaptive-form-using-xfa-templates.md)**: 이제 XFA 양식 템플릿(*.XDP 파일)을 사용하여 핵심 구성 요소 기반 적응형 Forms을 만들 수 있습니다. 이 기능은 AEM Forms On-Premise 고객이 AEM Forms as a Cloud Service 를 채택할 수 있도록 XFA 기술에 대한 기존 투자를 용이하게 합니다.

* **HTML5 Forms(XFA 기반 웹 양식)**: 이제 XFA 기술을 사용하는 AEM Forms On-Premise 고객은 기존 사용자 HTML Forms(XFA 기반 웹 양식)를 유지하면서 AEM Formsas a Cloud Service 로 간편하게 전환할 수 있습니다. 이 기능을 사용하면 XFA 양식 템플릿을 HTML5 형식으로 렌더링하여 XFA 기반 PDF forms을 지원하지 않는 장치에서 양식에 액세스할 수 있습니다.

  ![Forms(XFA 기반 웹 양식) HTML](/help/forms/assets/html-forms-xfa-based-web-forms.png)


* **[첨부 파일에 대한 Base64 인코딩된 문자열 지원](https://experienceleague.adobe.com/en/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/file-attachment#basic-tab)**: 이제 핵심 구성 요소를 기반으로 하는 적응형 Forms의 첨부 파일 구성 요소에 Base64 인코딩된 문자열로 첨부된 파일을 제출하는 옵션이 포함됩니다.

#### 대화형 통신 및 통신 API

* **대화형 통신 편집기**: 대화형 통신 편집기는 개인 맞춤화된 데이터 기반 서신 작성을 단순화하고 최신 브라우저에서 실행할 수 있는 사용자 친화적인 그래픽 통신 디자인 도구입니다. 원활한 데이터 통합, 복잡한 논리 정의 및 리치 미디어 통합을 지원하므로 다양한 비즈니스 요구 사항에 맞는 전문적이고 규정 준수 문서, 커뮤니케이션 및 템플릿 생성을 보장할 수 있습니다.

  ![대화형 통신 편집기](/help/forms/assets/ic-editor.png)


* **[PDF/A 규정 준수 개선 사항](/help/forms/aem-forms-cloud-service-communications-introduction.md#convert-to-and-validate-pdfa-compliant-documents)**: 이제 통신 API를 사용하여 PDF 문서를 보관 목적으로 PDF/A 형식(1a, 2a, 3a)으로 변환할 수 있으며 접근성을 보장하고 이러한 표준에 대한 규정 준수를 확인할 수 있습니다.


* **[서명 API(문서 Assurance)](/help/forms/aem-forms-cloud-service-communications-introduction.md#document-assurance)**: 통신 API의 새로운 RESTful API를 통해 PDF 서명을 쉽게 관리할 수 있습니다. 다음과 같은 작업을 지원합니다.
   * 서명 지우기: 지정된 필드에서 서명을 제거합니다.
   * 서명 필드 제거: 지정된 서명 필드를 삭제합니다.


<!-- 
* **Hamburger Menu Layout in Adaptive Forms**: Adaptive Forms now offers a responsive hamburger menu layout for mobile devices. This collapsible menu organizes form sections, making navigation more 
intuitive and improving the mobile form-filling experience.

* **Masked Field with Eye Icon (Password Box Component)**: The Password Box is a text input field that masks the characters typed into it by displaying placeholder symbols. It allows users to securely input sensitive information, such as passwords and enables them to toggle visibility on demand using the eye icon.

-->

## 자동화된 양식 전환 서비스

* **[PDF forms을 적응형 Forms 기반의 핵심 구성 요소로 변환](https://experienceleague.adobe.com/en/docs/aem-forms-automated-conversion-service/using/convert-existing-forms-to-adaptive-forms)**: 이제 Automated forms conversion 서비스를 사용하여 PDF forms, AcroForms 또는 XFA 기반 양식을 적응형 Forms 기반의 핵심 구성 요소로 변환할 수 있습니다.


>[!IMPORTANT]
>
> Forms 혁신을 위한 얼리 액세스 프로그램에 참여하는 데 관심이 있으십니까? 공식 주소에서 [aem-forms-ea@adobe.com](mailto:aem-forms-ea@adobe.com)로 관심 있는 기능 목록을 포함하여 이메일을 보내 주십시오.## CIF 추가 기능 {#cloud-services-cif}

## CIF 추가 기능 {#cif}

### 버그 수정 {#bug-fixes-cif}

* 코어 CIF 구성 요소에서 제대로 작동하도록 UI 테스트를 수정했습니다.
* 카테고리 URL 형식이 클라우드 인스턴스에서 예상대로 작동하지 않는 문제가 해결되었습니다.

## [!DNL Experience Manager] as a [!DNL Cloud Service] Foundation {#foundation}

### 트리 복제 성능 향상(및 Publish 콘텐츠 트리 워크플로 사용 중단) {#tree-replication-performance}

[트리 활성화 워크플로 단계](/help/operations/replication.md#tree-activation)는 딥 콘텐츠 계층을 복제하는 데 권장되는 새로운 워크플로 모델 단계입니다. 특히 빠른 게시 또는 게시 관리를 통해 독립 복제를 진행 중인 트리 복제 워크플로와 동시에 진행할 수 있습니다. 이 기능은 대량 복제가 진행 중인 동안 시간에 민감한 콘텐츠를 게시해야 하는 경우에 특히 유용합니다. 트리 복제 단계는 Publish 콘텐츠 트리 워크플로 및 관련 워크플로 단계(이제 더 이상 사용되지 않음)를 대체합니다.

### OpenAPI 기반 API - 얼리 어답터 프로그램 {#open-apis-earlyadopter}

개발자는 AEM as Cloud Service 기능을 자체 애플리케이션 및 도구에 심층적으로 통합할 수 있습니다. 새로운 AEM as a Cloud Service API는 일관되고, 잘 문서화되고, 사용자 친화적인 목표를 가지고 OpenAPI 사양을 따릅니다. 인증이 필요한 엔드포인트에 대한 자격 증명은 Adobe Developer Console 프로젝트를 생성하여 생성됩니다.

[OpenAPI 기반 AEM API](/help/implementing/developing/open-api-based-apis.md)에 대해 자세히 알아보고 구성 및 사용을 보여 주는 [엔드 투 엔드 튜토리얼](https://experienceleague.adobe.com/en/docs/experience-manager-learn/cloud-service/aem-apis/invoke-openapi-based-aem-apis)을 사용해 보세요.

구체적으로 아래 나열된 API 끝점은 얼리어답터 프로그램의 일부로 사용할 수 있습니다. 관심이 있는 경우 사용 방법을 설명하는 [aem-apis@adobe.com](mailto:aem-apis@adobe.com)(으)로 전자 메일을 보내십시오.
* [사이트 콘텐츠 조각 API](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/stable/sites/)
* [Assets API](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/assets/author/)
* [사이트 및 Assets 폴더 API](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/folders/)
* [Forms Communications API](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/document/)

### Edge 컴퓨팅 - 피드백 요청! {#edge-computing-feedback}

Edge 컴퓨팅은 데이터 처리를 브라우저에 더 가깝게 가져오므로 지연 시간 감소 등의 이점이 있습니다. 이 기술이 AEM Publish 제공 및 Edge Delivery Services 프로젝트에 유용한지, 그리고 이 기술을 사용하여 어떤 작업을 수행할 것인지 로드맵에 자세히 설명해 주십시오. 질문과 의견이 있는 전자 메일 [aemcs-edgecompute-feedback@adobe.com](mailto:aemcs-edgecompute-feedback@adobe.com)!

### 새로운 AEM Developer Console (공개 Beta) {#aem-developer-console-beta}

클라우드 환경에서 코드 디버깅을 위한 보다 인터랙티브한 경험을 제공하는 개선된 [AEM Developer Console](/help/implementing/developing/introduction/aem-developer-console.md)을 사용해 보십시오.

현재 AEM Developer Console에서 *새 콘솔 사용 가능* 버튼을 클릭하여 누구나 공개 Beta에 액세스할 수 있습니다. Adobe은 [aemcs-new-devconsole-ui-beta@adobe.com](mailto:aemcs-new-devconsole-ui-beta@adobe.com)에 전자 메일을 보낼 수 있는 피드백을 환영합니다.

## [!DNL Experience Manager] 안내서 {#guides}

[여기](https://experienceleague.adobe.com/ko/docs/experience-manager-guides/using/release-info/release-notes/cloud-release-notes/2024-releases/2410-release/2410-0-release/whats-new-2024-10-0)에서 Adobe Experience Manager Guides 최신 릴리스의 새로운 기능과 향상된 기능의 전체 목록을 찾을 수 있습니다.

## Cloud Manager {#cloud-manager}

[여기](/help/implementing/cloud-manager/release-notes/current.md)에서 Cloud Manager 월별 릴리스의 전체 목록을 찾을 수 있습니다.

## 마이그레이션 도구 {#migration-tools}

[여기](/help/journey-migration/release-notes/release-notes-migration-tools-current.md)에서 마이그레이션 도구의 전체 목록을 찾을 수 있습니다.

## 범용 편집기 {#universal-editor}

[여기](/help/release-notes/universal-editor/current.md)에서 범용 편집기의 전체 목록을 찾을 수 있습니다.

## 변형 생성 {#generate-variations}

[여기](/help/generative-ai/release-notes-generate-variations.md)에서 변형 생성의 전체 목록을 찾을 수 있습니다.

## Experience Cloud 릴리스 정보 {#experience-cloud}

다른 Experience Cloud 애플리케이션 릴리스에 대한 정보는 [여기](https://experienceleague.adobe.com/ko/docs/release-notes/experience-cloud/current)에서 확인할 수 있습니다.
