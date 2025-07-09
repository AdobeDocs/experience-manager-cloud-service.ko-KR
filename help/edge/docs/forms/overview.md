---
title: AEM Forms용 Edge Delivery Services 개요
description: Edge Delivery Services을 사용하여 AEM Forms으로 고성능 양식을 만들고 전달하여 신속한 개발과 간소화되는 데이터 수집을 가능하게 하는 방법에 대해 알아봅니다.
feature: Edge Delivery Services
exl-id: ecea1e05-d36b-4d63-af9d-c69dafd2f94f
role: Admin, Architect, Developer
source-git-commit: 1ddf97f56e5a9b7c95959da47a748f5a6d128e43
workflow-type: tm+mt
source-wordcount: '864'
ht-degree: 8%

---


# AEM Forms용 Edge Delivery Services


AEM Forms용 Edge Delivery Services는 새 양식을 빠르게 업데이트, 게시 및 시작할 수 있는 신속한 개발 환경을 지원하는 구성 가능한 서비스 세트입니다. 이러한 서비스는 참여와 전환을 촉진하는 탁월하고 영향력 있는 양식 경험을 선사합니다. 이러한 양식 환경은 쉽게 작성하고 개발할 수 있습니다.

* **더 빠른 환경:** Forms은 CDN(Global Content Delivery Network)에서 제공되므로 사용자에게 빠르게 로드됩니다.
* **신속한 개발:** 간소화된 개발 프로세스를 통해 더 빠른 업데이트를 수행할 수 있습니다. 긴 파이프라인 빌드를 기다리지 않고 변경 사항을 게시할 수 있습니다.
* **유연한 작성:** 문서 기반 작성(Microsoft Word, Google Docs/Sheets) 또는 시각적 WYSIWYG 편집기(유니버설 편집기)를 포함하여 다양한 도구 중에서 선택하여 양식을 만들 수 있습니다.

## 작동 방식

Edge Delivery Services을 사용하면 양식의 구조 및 컨텐츠가 AEM as a Cloud Service, Microsoft SharePoint 또는 Google 드라이브와 같은 소스에 상주할 수 있습니다. 이 콘텐츠는 글로벌 CDN에 게시됩니다. 사용자가 사이트를 방문할 때 최적의 성능을 위해 가장 가까운 CDN 에지 서버에서 양식이 직접 제공됩니다.

콘텐츠 원본, CDN 및 사용자를 보여 주는 ![간소화된 아키텍처 다이어그램입니다.](/help/forms/assets/eds-simplified-architecture.png)
**Forms을 사용한 간소화된 Edge Delivery Services 아키텍처**

사용자가 제출한 데이터는 추가 처리를 위해 간단한 스프레드시트에서 강력한 AEM 백엔드로 다양한 대상으로 전송할 수 있습니다.

## 작성 방법 선택

여러 가지 방법으로 Edge Delivery Services 사이트에 대한 양식을 만들 수 있습니다. 가장 좋은 방법은 팀의 기술, 양식의 복잡성 및 프로젝트 요구 사항에 따라 다릅니다.

![양식 작성 방법을 선택하는 데 도움이 되는 결정 트리입니다.](/help/forms/assets/eds-authoring-selection.png)
**양식 작성 결정 트리**

### 문서 기반 작성

이 방법을 사용하면 [Microsoft Word 또는 Google Docs/Sheets를 사용하여 양식을 만들 수 있습니다](/help/edge/docs/forms/create-forms.md). 특정 테이블 형식을 사용하여 문서에서 양식 필드, 레이블 및 유형을 정의합니다. Edge Delivery Services은 이 문서를 대화형 HTML 양식으로 변환합니다.

**기능:**

* 익숙한 도구: Word, Google Docs 또는 Google Sheets에서 작성합니다.
* 텍스트 입력, 이메일, 드롭다운, 확인란 및 라디오 버튼과 같은 필드를 정의합니다.
* 필수 필드 등 기본 유효성 검사 규칙을 설정합니다.
* 스팸 보호를 위해 Google reCAPTCHA를 통합합니다.
* 파일 업로드 지원.
* 스프레드시트나 이메일 주소로 직접 데이터를 제출합니다.
* 고급 구성 요소 및 스타일을 위해 GitHub를 통해 사용자 지정 코드로 확장합니다.

**추천 항목:**

* 콘텐츠 작성에 문서 편집기를 주로 사용하는 팀.
* 간단하거나 중간 정도의 복잡한 양식을 신속하게 만들 수 있습니다.
* 스프레드시트나 이메일로 간단한 데이터 수집.

문서 기반 양식의 제출은 일반적으로 구성된 스프레드시트 또는 전자 메일 주소로 데이터를 라우팅하는 [AEM Forms 제출 서비스](/help/forms/forms-submission-service.md)에서 처리됩니다.

### 범용 편집기 작성

[유니버설 편집기는 끌어서 놓기 경험이 있는 양식을 작성할 수 있는 최신 WYSIWYG 인터페이스를 제공합니다](/help/edge/docs/forms/universal-editor/overview-universal-editor-for-edge-delivery-services-for-forms.md).

**기능:**

* 미리 빌드된 구성 요소 라이브러리가 있는 드래그 앤 드롭 양식 빌드를 시각적으로 표시합니다.
* 실시간 유효성 검사 및 복잡한 비즈니스 논리 구성(예: 사용자 선택에 따라 필드 표시/숨기기).
* 다른 디바이스를 위한 라이브 미리보기.
* 컨텐츠 조각, AEM 워크플로 및 사용자 권한과 같은 AEM as a Cloud Service 기능과 긴밀하게 통합됩니다.
* &quot;Experience Builder&quot;를 통해 AI 지원 양식 작성 및 편집

**추천 항목:**

* 조건부 논리, 여러 단계 패널 또는 개인화를 사용하여 복잡한 양식을 작성합니다.
* 시각적 도구를 선호하는 팀(예: 마케터, 비즈니스 사용자)
* 데이터 처리 및 워크플로우를 위해 AEM 백엔드와 강력한 통합이 필요한 프로젝트.

유니버설 편집기로 빌드된 Forms은 [Forms 제출 서비스](/help/forms/forms-submission-service.md)를 사용하거나 [고급 데이터 처리를 위해 OOTB에 제공된 제출 액션](/help/edge/docs/forms/configure-submission-action-for-eds-forms.md)을 사용하도록 구성할 수 있습니다(예: AEM 워크플로, REST 끝점 또는 데이터베이스로 데이터 보내기).

### 문서 작성 페이지에 Forms 포함

[DA(문서 작성)](https://www.aem.live/developer/da-tutorial)은(는) Edge Delivery Services의 웹 사이트 콘텐츠를 관리하기 위한 Adobe 호스팅 서비스입니다. DA는 양식 작성 도구 자체는 아니지만 웹 페이지를 작성한 다음 다른 메서드로 만든 양식을 임베드하는 데 사용할 수 있습니다.

**작동 방식:**

1. **양식 만들기:** 문서 기반 작성 또는 유니버설 편집기를 사용하여 양식을 작성합니다.
2. **양식 게시:** 양식이 게시되어 있고 자체 URL에서 액세스할 수 있는지 확인하십시오.
3. **DA에 포함:** 문서 작성 페이지에서 양식의 URL을 참조하는 블록을 추가하여 포함시킵니다.

이 방법은 Edge Delivery Services 사이트의 기본 컨텐츠 관리 시스템으로 문서 작성 을 사용하는 팀을 위한 것입니다.

## 작성 방법 비교

| 기준 | 문서 기반 작성 | 유니버설 편집기(WYSIWYG) | DA(문서 작성)의 Forms |
|----------------------------------|---------------------------------------|-----------------------------------------|-------------------------------------------|
| **기본 제작 도구** | Word/Google Docs/Sheets | 브라우저(AEM 유니버설 편집기) | 해당 없음(Forms은 *포함*&#x200B;됨) |
| **팀 스킬 레벨** | 문서 편집기에 익숙함 | 시각적 웹 도구에 익숙함 | 페이지 콘텐츠에 DA 사용 |
| **일반적인 양식 복잡성** | 단순-중재 | 중간에서 복잡으로, 엔터프라이즈급 | 포함된 양식에 따라 다름 |
| **제출 옵션** | Forms 제출 서비스(시트/이메일로) | Forms 제출 서비스, AEM 게시(워크플로우, 양식 데이터 모델, 서드파티 통합) | 임베드된 양식의 설정을 따릅니다. |
| **AEM 백엔드 통합** | 최소 | 높음(AEM Publish 제출 시) | 임베드된 범용 편집기 양식을 통해 간접적으로 |
| **가장 적합한 대상...** | 콘텐츠 팀이 간단한 양식을 신속하게 작성하고 데이터를 빠르게 캡처합니다. | 시각적 제어, 복잡한 양식 또는 심층 AEM 통합이 필요한 마케터 및 비즈니스 사용자. | DA에서 기본 콘텐츠가 관리되는 사이트. |

<!-- 
## Detailed Feature Comparison

| **Capability**                        | **Universal Editor (WYSIWYG)** | **Document-based Authoring** | **Document Authoring (DA)** |
|-----------------------------------------|-------------------------------|-----------------------------|-----------------------------|
| **Unified Composition with Sites**    | ✅                            |                              | ✅ (with embedded forms)     |
| **Embedding Form Support**            | ✅                            | ✅                          | ✅ (embed from Universal Editor or Docs)   |
| **Rules (Dynamic Behavior)**          | Advanced rules editor with custom functions | Limited: Show/hide, compute value, custom functions | Depends on embedded form     |
| **Attachment Support**                | ✅                            | ℹ️ (Early Access)           | Depends on embedded form     |
| **CAPTCHA Support**                   | reCAPTCHA Enterprise          | reCAPTCHA Enterprise       | Depends on embedded form     |
| **Submission Features**               | REST, Email, FDM, Workflow, SharePoint, OneDrive, Azure Blob, Power Automate, Workfront Fusion (EA) | Only Spreadsheet            | Follows embedded form's setup |
| **Data Schema**                       | FDM, Custom                   | Custom                      | Based on embedded form       |
| **Pre-fill**                          | 💡 (via Wizard)               | ✅                          | Depends on embedded form     |
| **Fragments**                         | ✅                            | ✅                          | Depends on embedded form     |
| **Visual Rule Editor**                | ✅                            |                              |                              |
| **Localization**                      | 💡 (via Sites)                | ℹ️ (Excel/Sheets manual)    | Depends on embedded form     |
| **Template Support**                  | Only Initial Content          |                              |                              |
| **Theme**                             | ℹ️ (at project level)         | ℹ️ (at project level)        | ℹ️ (based on hosting site)    |
| **Custom Component**                  | ✅                            | ✅                          | ✅ (if embedded component supports it) |
| **Experimentation**                   | ✅                            | ✅                          | Depends on embed context     |
| **Submit Action**                     | ✅                            | Only Spreadsheet            | Based on embedded form       |
-->



## 다음 단계

* [문서 기반 작성으로 양식 만들기](/help/edge/docs/forms/tutorial.md)
* [Forms용 유니버설 편집기에 대해 알아보기](/help/edge/docs/forms/universal-editor/overview-universal-editor-for-edge-delivery-services-for-forms.md)
* [양식 제출 작업 구성](/help/edge/docs/forms/configure-submission-action-for-eds-forms.md)
* [DA(문서 작성)에 대해 알아보기](https://www.aem.live/developer/da-tutorial)
