---
title: ' [!DNL Adobe Experience Manager] as a Cloud Service의 2024.11.0 릴리스 정보입니다.'
description: ' [!DNL Adobe Experience Manager] as a Cloud Service의 2024.11.0 릴리스 정보입니다.'
feature: Release Information
role: Admin
exl-id: 3fd6482e-66f0-48ee-983c-4cb6b7742dcd
source-git-commit: bb149cd43158bfd1ceb43b04cc536c8c8291f968
workflow-type: tm+mt
source-wordcount: '1810'
ht-degree: 98%

---

# [!DNL Adobe Experience Manager] as a Cloud Service 2024.11.0 릴리스 정보 {#release-notes}

다음 섹션에서는 [!DNL Experience Manager] as a Cloud Service의 2024.11.0 버전 기능 릴리스 정보에 대해 간략히 소개합니다.

>[!NOTE]
>
>여기에서 2022년 또는 2023년과 같은 이전 버전의 릴리스 정보로 이동할 수 있습니다.
>
>[!DNL Experience Manager] as a Cloud Service의 향후 기능 활성화에 대해 알아보려면 [Experience Manager 릴리스 로드맵](https://experienceleague.adobe.com/ko/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap)을 살펴보십시오.

>[!NOTE]
>
>Experience Cloud 릴리스 정보의 업데이트에 대한 월별 이메일 알림을 받아 보려면 [Adobe 우선순위 제품 업데이트](https://www.adobe.com/kr/subscription/priority-product-update.html)를 구독하십시오.

## 릴리스 일자 {#release-date}

[!DNL Adobe Experience Manager] as a [!DNL Cloud Service]의 현재 기능 릴리스(2024.11.0) 날짜는 2024년 11월 21일입니다. 다음 기능 릴리스(2025.1.0)는 2025년 1월 30일 금요일에 예정되어 있습니다.

## 유지 관리 릴리스 정보 {#maintenance}

[여기](/help/release-notes/maintenance/latest.md)에서 최신 유지 관리 릴리스 정보를 확인할 수 있습니다.

## 릴리스 비디오 {#release-video}

2024년 11월 릴리스 개요 비디오를 통해 2024.11.0 릴리스에 추가된 기능에 대한 간단한 요약을 살펴보십시오.

>[!VIDEO](https://video.tv.adobe.com/v/3440927?quality=12&captions=kor)

## [!DNL Experience Manager Sites] as a [!DNL Cloud Service] {#sites}

**[!DNL Edge Delivery Services]범용 편집기 작성 기능을 갖춘 페이지 템플릿**

모든 Edge Delivery 페이지를 빠르게 페이지 템플릿으로 전환하십시오. 이를 통해 빈 페이지 대신 미리 정의된 구조와 콘텐츠로 새 페이지를 시작할 수 있습니다. [자세히 보기](/help/sites-cloud/authoring/universal-editor/templates.md)

**[!DNL Edge Delivery Services]CSV 가져오기 도구를 통해 AEM 인스턴스로 게시**

자주 사용하는 스프레드시트 도구에서 Edge Delivery 스프레드시트 데이터(예: 리디렉션)를 효율적으로 관리하고 새로운 CSV 가져오기 도구를 통해 AEM에 업로드합니다. [자세히 보기](https://www.aem.live/docs/authoring-tabular-data)

### AEM Sites의 프리릴리스 기능

[고유 ID 기반 참조와 함께 콘텐츠 조각을 참조](/help/headless/graphql-api/uuid-reference-upgrade.md)하여 에셋 또는 조각을 이동할 때에도 유효한 링크를 유지할 수 있으므로 업데이트나 다시 게시할 필요가 없습니다. 현재 제한 사항: 페이지 참조는 아직 고유 ID로 지원되지 않습니다. 콘텐츠 조각에서 페이지를 참조하는 경우에는 이 기능을 사용하면 안 됩니다.

### 얼리 어답터 프로그램 {#sites-early-adopter}

**콘텐츠 조각 게재를 위한 AEM REST OpenAPI**

[콘텐츠 조각 게재를 위한 AEM REST OpenAPI](/help/headless/aem-content-fragment-delivery-with-openapi.md)가 AEM as a Cloud Service에서 현재 사용 가능합니다.

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### Dynamic Media의 얼리 액세스 기능 {#dm-early-access}

**AI 생성 비디오 캡션**

Adobe Dynamic Media의 AI 생성 비디오 캡션은 인공 지능을 통해 비디오 콘텐츠에 대한 캡션을 자동으로 생성합니다. 이 기능은 정확한 실시간 캡션을 제공하여 접근성을 개선하고 사용자 경험을 향상시킬 수 있도록 설계되었습니다. AI는 비디오의 오디오 트랙을 분석하여 음성을 기록하고 캡션을 생성하며, 정확성이나 사용자 정의를 위해 해당 캡션을 편집할 수 있습니다. 이러한 캡션은 접근성 요구 사항을 충족하며, 텍스트 기반 비디오 지원에 의존하거나 이를 선호하는 대상자의 비디오 참여를 개선하는 데 도움이 됩니다.

Dynamic Media 계정에서 AI 생성 캡션 지원에 얼리 액세스하려면 [Adobe 고객 지원 사례를 작성하고 제출](/help/assets/dynamic-media/video.md##enable-dash)하십시오.

**Dynamic Media 게재 보고서**

자산 수준 게재 카운트, 레퍼러 정보, AEM Assets의 자산 경로 및 고유 자산 ID와 함께 Dynamic Media를 통해 게재된 자산에 대한 게재 인사이트를 확인할 수 있습니다. Dynamic Media를 통해 게재된 AEM Assets 저장소의 모든 자산 또는 AEM Assets 내 특정 폴더 계층 구조의 모든 자산에 대한 보고서를 생성할 수 있습니다. 인사이트는 게재된 자산의 ROI를 측정하고, 채널 성과를 측정하고, 자산에 대해 정보에 입각한 자산 관리 작업을 수행하는 데 도움이 됩니다.

Dynamic Media 계정에서 Dynamic Media 게재 보고서에 얼리 액세스하려면 [Adobe 고객 지원 사례를 작성하고 제출](https://helpx.adobe.com/kr/enterprise/using/support-for-experience-cloud.html)하십시오.

### Assets 보기의 새로운 기능 {#assets-view-new-features}

**Dynamic Media 패널**

이제 자산 보기를 통해 별도의 패널에서 Dynamic Media와 OpenAPI 포함 Dynamic Media 렌디션에 액세스할 수 있습니다. 자산 및 렌디션 유형에 따라 게재 URL을 복사하거나 렌디션을 다운로드할 수 있습니다. 자세한 내용은 [Dynamic Media 렌디션](/help/assets/renditions.md#dynamic-media-renditions) 및 [OpenAPI 기능 포함 Dynamic Media 렌디션](/help/assets/renditions.md#dm-with-openapi-renditions)을 참조하십시오.

![동적 렌디션](/help/assets/assets/dm-scene7-renditions.png)

## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

### AEM Forms의 새로운 기능 {#forms-new-features}

* **[Adobe Sign 범위 쉽게 업데이트](/help/forms/adobe-sign-integration-adaptive-forms.md)**: Adobe Sign 구성의 범위를 AEM 클라우드 구성 페이지에서 직접 수정할 수 있습니다. 이를 통해 기존 구성을 더 빠르고 쉽게 업데이트할 수 있습니다.

* **[적응형 양식에 대한 비동기 기능 지원](/help/forms/using-async-funct-in-rule-editor.md)**: 적응형 양식에 외부 프로세스나 데이터 검색을 기다리는 등의 비동기 작업이 필요한 경우, 이러한 작업을 사용자 정의 함수로 구현하고 규칙 편집기에서 구성할 수 있습니다.

### AEM Forms의 프리릴리스 기능 {#forms-new-prerelease-features}

* **게시 관리**: 게시 관리 워크플로를 사용하여 작성자 인스턴스에서 게시 및 미리보기 인스턴스에 이르기까지 여러 환경에서 양식을 게시하거나 게시 취소할 수 있습니다. 이를 통해 사용자는 간소화된 방식으로 콘텐츠를 게시 또는 게시 취소하거나 게시 일정을 예약할 수 있습니다.

* **[핵심 구성 요소 기반 적응형 양식의 초안 자동 저장](/help/forms/save-core-component-based-form-as-draft.md)**: 사용자는 이제 자동 저장 기능을 통해 작성 중인 양식을 초안으로 자동 저장할 수 있습니다. 나중에 돌아와 동일한 디바이스 또는 다른 디바이스에서 작성을 마칠 수 있습니다. 이 기능을 사용하면 사용자가 처음부터 양식을 작성할 필요가 없으므로 양식 폐기를 방지하여 전환율을 높일 수 있습니다.

* **[규칙 편집기 개선 사항](/help/forms/invoke-service-enhancements-rule-editor.md)**: 핵심 구성 요소를 기반으로 하는 적응형 양식의 경우 이제 호출 서비스의 출력을 사용하여 드롭다운 옵션을 채우고, 반복 가능한 패널을 설정하고, 개별 패널을 설정하고, 호출 서비스의 출력 매개변수를 사용하여 다른 필드의 유효성을 검사할 수 있습니다.

* **[사용자 경험 향상을 위한 패널 레이아웃 내 탐색 버튼 추가](/help/forms/rule-editor-core-components-usecases.md#navigating-among-panels-using-button)**: 이제 가로 탭, 세로 탭, 아코디언 또는 마법사와 같은 탐색 버튼을 패널 레이아웃에 추가할 수 있습니다. 이러한 버튼은 패널 간 전환을 간소화하고 선택된 패널에 초점을 맞춤으로써 사용자 경험을 향상시킵니다.


### AEM Forms의 얼리 액세스 기능 {#forms-new-early-access-features}

AEM Forms 얼리 액세스 프로그램은 최첨단 혁신에 독점적으로 액세스할 수 있는 특별한 기회를 제공하며, 혁신의 발전을 구체화하는 데 도움을 줍니다.

이 릴리스 정보에는 현재 릴리스에서 제공되는 혁신 사항이 나열되어 있습니다. 얼리 액세스 프로그램에서 사용할 수 있는 전체 혁신 목록은 [AEM Forms 얼리 액세스 프로그램 설명서](/help/forms/early-access-ea-features.md)를 참조하십시오.

#### 통합

* **[적응형 양식과 Adobe Marketo Engage 통합](/help/forms/integrate-form-to-marketo-engage.md)**: 이제 AEM Forms as a Cloud Service에서는 적응형 양식을 Adobe Marketo Engage와 간단하게 연결할 수 있습니다. 이 통합을 통해 Marketo Engage의 리드 캡처와 관련 사용자 정의 오브젝트를 사용하여 직접 적응형 양식을 만들 수 있습니다. 이제 Marketo Engage의 데이터로 양식 필드를 미리 채우고 데이터를 다시 제출하여 스마트 캠페인 및 이메일 자동화와 같이 워크플로를 자동화할 수 있습니다. 적응형 양식을 Munchkin 라이브러리에 연결하여 방문 횟수, 클릭 수 및 양식 제출 수를 추적할 수도 있습니다.

#### 적응형 양식 및 HTML5 양식

* **[기존 XFA 템플릿 기반 적응형 양식 만들기](/help/forms/create-adaptive-form-using-xfa-templates.md)**: 이제 XFA 양식 템플릿(*.XDP 파일)을 사용하여 핵심 구성 요소 기반의 적응형 양식을 만들 수 있습니다. 이 기능을 통해 기존 XFA 기술에 투자한 AEM Forms On-Premise 고객도 AEM Forms as a Cloud Service를 채택할 수 있습니다.

* **HTML5 양식(XFA 기반 웹 양식)**: 이제 XFA 기술을 사용하는 AEM Forms On-Premise 고객은 HTML5 양식(XFA 기반 웹 양식)을 통한 기존 사용자 경험을 유지하면서 AEM Forms as a Cloud Service로 손쉽게 전환할 수 있습니다. 이 기능을 통해 XFA 양식 템플릿을 HTML5 포맷으로 렌더링할 수 있으므로 XFA 기반 PDF 양식을 지원하지 않는 디바이스에서도 양식에 액세스할 수 있습니다.

  ![HTML 양식 (XFA 기반 웹 양식)](/help/forms/assets/html-forms-xfa-based-web-forms.png)


* **[첨부 파일을 위한 Base64 인코딩 문자열 지원](https://experienceleague.adobe.com/ko/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/file-attachment#basic-tab)**: 이제 핵심 구성 요소 기반 적응형 양식의 첨부 파일 구성 요소에 첨부 파일을 Base64 인코딩 문자열로 제출하는 옵션이 포함됩니다.

#### 인터랙티브 커뮤니케이션 및 커뮤니케이션 API

* **인터랙티브 커뮤니케이션 편집기**: 인터랙티브 커뮤니케이션 편집기는 사용자 친화적인 그래픽 커뮤니케이션 디자인 도구로, 모든 최신 브라우저에서 실행되어 개인화된 데이터 기반 서신 작성 과정을 간소화할 수 있습니다. 원활한 데이터 통합, 복잡한 논리 정의, 리치 미디어 통합을 지원하며, 이를 통해 다양한 비즈니스 요구 사항에 맞는 전문적이고 규정을 준수하는 문서, 커뮤니케이션 및 템플릿을 생성할 수 있습니다.

  ![인터랙티브 커뮤니케이션 편집기](/help/forms/assets/ic-editor.png)


* **[PDF/A 규정 준수 개선](/help/forms/aem-forms-cloud-service-communications-introduction.md#convert-to-and-validate-pdfa-compliant-documents)**: 이제 커뮤니케이션 API를 사용하여 보관 목적으로 PDF 문서를 PDF/A 포맷(1a, 2a, 3a)으로 변환하는 동시에, 접근성을 확보하고 이러한 표준을 준수하는지 확인할 수 있습니다.


* **[서명 API(Document Assurance)](/help/forms/aem-forms-cloud-service-communications-introduction.md#document-assurance)**: 커뮤니케이션 API의 새로운 RESTful API를 통해 PDF 서명을 쉽게 관리할 수 있습니다. 다음과 같은 작업이 지원됩니다.
   * 서명 지우기: 지정된 필드에서 서명을 제거합니다.
   * 서명 필드 제거: 지정된 서명 필드를 삭제합니다.

<!-- 
* **Hamburger Menu Layout in Adaptive Forms**: Adaptive Forms now offers a responsive hamburger menu layout for mobile devices. This collapsible menu organizes form sections, making navigation more 
intuitive and improving the mobile form-filling experience.

* **Masked Field with Eye Icon (Password Box Component)**: The Password Box is a text input field that masks the characters typed into it by displaying placeholder symbols. It allows users to securely input sensitive information, such as passwords and enables them to toggle visibility on demand using the eye icon.

-->

## 자동화된 양식 변환 서비스

* **[PDF 양식을 핵심 구성 요소 기반 적응형 양식으로 변환](https://experienceleague.adobe.com/ko/docs/aem-forms-automated-conversion-service/using/convert-existing-forms-to-adaptive-forms)**: 이제 자동화된 양식 변환 서비스를 사용하여 PDF 양식, AcroForms 또는 XFA 기반 양식을 핵심 구성 요소 기반 적응형 양식으로 변환할 수 있습니다.

>[!IMPORTANT]
>
> Forms 혁신을 위한 얼리 액세스 프로그램에 참여하는 데 관심이 있으십니까? 공식 주소에서 [aem-forms-ea@adobe.com](mailto:aem-forms-ea@adobe.com)으로 관심 있는 기능 목록을 포함하여 이메일을 보내 주십시오.## CIF 추가 기능 {#cloud-services-cif}

## CIF 추가 기능 {#cif}

### 버그 수정 {#bug-fixes-cif}

* 코어 CIF 구성 요소에서 제대로 작동하도록 UI 테스트를 수정했습니다.
* 카테고리 URL 형식이 클라우드 인스턴스에서 예상대로 작동하지 않는 문제가 해결되었습니다.

## [!DNL Experience Manager] as a [!DNL Cloud Service] Foundation {#foundation}

### 트리 복제 성능 개선 (게시 콘텐츠 트리 워크플로 사용 중단) {#tree-replication-performance}

[트리 활성화 워크플로 단계](/help/operations/replication.md#tree-activation)는 심층적인 콘텐츠 계층 구조를 복제하는 데 권장되는 새로운 워크플로 모델 단계입니다. 주목할 점은 진행 중인 트리 복제 워크플로와 독립적인 복제(예: 빠른 게시 또는 게시 관리를 통한 복제)를 동시에 진행할 수 있다는 것입니다. 이는 대량 복제가 진행되는 도중 긴급한 콘텐츠를 게시해야 하는 경우에 특히 유용합니다. 트리 복제 단계는 이제 더 이상 사용되지 않는 콘텐츠 트리 게시 워크플로 및 관련 워크플로 단계를 대체합니다.

### OpenAPI 기반 API - 얼리 어답터 프로그램 {#open-apis-earlyadopter}

개발자는 AEM as Cloud Service 기능을 자신의 애플리케이션과 도구에 긴밀하게 통합할 수 있습니다. 새 AEM as a Cloud Service API는 OpenAPI 사양을 따르며, 일관되고 문서화가 잘 되며 사용자 친화적인 것을 목표로 합니다. 인증이 필요한 엔드포인트에 대한 자격 증명은 Adobe Developer Console 프로젝트를 만드는 방식으로 생성됩니다.

[OpenAPI 기반 AEM API](/help/implementing/developing/open-api-based-apis.md)에 대해 자세히 알아보고 구성 및 사용 방법을 안내하는 [전체 튜토리얼](https://experienceleague.adobe.com/ko/docs/experience-manager-learn/cloud-service/aem-apis/invoke-openapi-based-aem-apis)을 살펴보십시오.

구체적으로 아래에 나열된 API 엔드포인트가 얼리 어답터 프로그램의 일부로 제공됩니다. 관심이 있는 경우 [aem-apis@adobe.com](mailto:aem-apis@adobe.com)에 이메일로 문의하여 사용 계획을 설명해 주십시오.
* [Sites 콘텐츠 조각 API](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/stable/sites/)
* [Assets API](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/assets/author/)
* 사이트 및 Assets 폴더 API
* [Forms 커뮤니케이션 API](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/document/)

### 에지 컴퓨팅 - 피드백 요청 {#edge-computing-feedback}

에지 컴퓨팅은 데이터 처리를 브라우저에 더 가까운 위치에서 수행하여, 지연 시간 감소와 같은 이점을 제공합니다. 로드맵에 반영하기 위한 목적으로, 이 기술이 AEM 게시 게재 및 Edge Delivery Services 프로젝트에 유용할 것이라고 생각하는지, 이를 어떻게 활용할 계획인지에 대한 귀하의 의견을 듣고 싶습니다. 질문과 의견을 [aemcs-edgecompute-feedback@adobe.com](mailto:aemcs-edgecompute-feedback@adobe.com)에 이메일로 보내 주십시오.

### 새로운 AEM Developer Console (공개 Beta) {#aem-developer-console-beta}

클라우드 환경에서 코드 디버깅을 위한 보다 인터랙티브한 경험을 제공하는 개선된 [AEM Developer Console](/help/implementing/developing/introduction/aem-developer-console.md)을 사용해 보십시오.

현재 AEM Developer Console에서 *새 콘솔 사용 가능* 버튼을 클릭하여 누구나 공개 Beta에 액세스할 수 있습니다. Adobe는 여러분의 피드백을 환영합니다. 의견이 있는 경우 [aemcs-new-devconsole-ui-beta@adobe.com](mailto:aemcs-new-devconsole-ui-beta@adobe.com)으로 이메일을 보내 주십시오.

## [!DNL Experience Manager] 안내서 {#guides}

[여기](https://experienceleague.adobe.com/ko/docs/experience-manager-guides/using/release-info/aem-guides-releases-roadmap)에서 Adobe Experience Manager Guides 최신 릴리스의 새로운 기능과 향상된 기능의 전체 목록을 찾을 수 있습니다.

## Cloud Manager {#cloud-manager}

[여기](/help/implementing/cloud-manager/release-notes/current.md)에서 Cloud Manager 월별 릴리스의 전체 목록을 찾을 수 있습니다.

## 마이그레이션 도구 {#migration-tools}

[여기](/help/journey-migration/release-notes/release-notes-migration-tools-current.md)에서 마이그레이션 도구의 전체 목록을 찾을 수 있습니다.

## 범용 편집기 {#universal-editor}

[여기](/help/release-notes/universal-editor/current.md)에서 범용 편집기의 전체 목록을 찾을 수 있습니다.

## 변형 생성 {#generate-variations}

[여기](/help/generative-ai/release-notes-generate-variations.md)에서 변형 생성의 전체 목록을 찾을 수 있습니다.

## Experience Cloud 릴리스 정보 {#experience-cloud}

기타 Experience Cloud 애플리케이션 릴리스에 대한 정보는 [여기](https://experienceleague.adobe.com/ko/docs/release-notes/experience-cloud/current)에서 확인할 수 있습니다.
