---
title: AEM Edge Delivery Services의 Forms 시작하기
description: Adobe Experience Manager Edge Delivery Services에서 범용 편집기 작성 접근 방식에 중점을 두고 고성능 양식을 생성하고 전달하는 방법에 대해 알아봅니다.
feature: Edge Delivery Services
exl-id: ecea1e05-d36b-4d63-af9d-c69dafd2f94f
role: Admin, Architect, Developer
source-git-commit: 2e2a0bdb7604168f0e3eb1672af4c2bc9b12d652
workflow-type: tm+mt
source-wordcount: '591'
ht-degree: 100%

---


# AEM Edge Delivery Services의 Forms 시작하기

<span class="preview"> 이는 프리릴리스 기능이고 <a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/release-notes/prerelease.html?lang=ko#new-features">프리릴리스 채널</a>을 통해 사용할 수 있습니다. </span>

Adobe Experience Manager(AEM) Edge Delivery Services(EDS)는 에지에서 매우 빠르고 확장성이 뛰어난 웹 경험을 제공합니다. 이 안내서에서는 **해당 경험을 위한 양식을 빌드하고 게시하는 방법**&#x200B;을 명확한 권장 계층과 함께 설명합니다.

1. **범용 편집기(UE) – 대부분의 팀에 최적의 선택**
2. **문서 기반 작성 (Docs/Sheets) – 빠르고 간단한 양식에 적합**
3. **문서 작성 (DA) – DA로 작성된 페이지에 양식을 임베드하는 데 사용**

마지막으로 올바른 작성 방법을 선택하고, 제출 옵션을 이해하며, 프로덕션 준비가 된 양식을 만드는 다음 단계를 따를 수 있습니다.



## 작성 방법 선택

| 팀 및 요구 사항 | 권장 방법 | 이유 |
|--------------------|--------------------|-----|
| 마케터/디자이너에게 시각적 제어, 조건 논리 또는 AEM 통합이 필요합니다. | **범용 편집기** | 드래그 앤 드롭, 고급 규칙, FSS 또는 AEM Publish로 제출 |
| Word/Google Docs/Sheets에서 이미 작업 중인 콘텐츠 작성자, 스프레드시트, 이메일에 대한 간단한 데이터 캡처 | **문서 기반 작성** | 익숙한 도구, 기본 양식에 대한 가장 빠른 경로 |
| **문서 작성(DA)**&#x200B;에 기본 제공되는 웹 사이트 페이지 | UE 또는 문서 기반 양식을 DA 페이지에 **임베드** | DA는 양식을 직접 빌드하지 않습니다. |


## 작성 방법 상세 설명

### 범용 편집기

범용 편집기는 속도와 엔터프라이즈급 기능을 결합한 마케터 및 디자이너를 위한 시각적 드래그 앤 드롭 작성 도구입니다.

- 실시간 WYSIWYG 편집 및 디바이스 미리보기 기능을 제공합니다.
- 코드가 필요 없는 고급 규칙 및 유효성 검사 UI를 제공합니다.
- AEM 자산, 워크플로 및 Forms 데이터 모델(FDM)과의 직접 통합을 지원합니다.
- Vanilla JS/CSS에서 사용자 정의 구성 요소를 개발자에게 원활하게 전달합니다.
- 유연한 제출 대상: **Forms 제출 서비스(FSS)**&#x200B;로 간단하게 시작하거나 필요에 따라 **AEM Publish 제출 작업**&#x200B;으로 전환할 수 있습니다.

> **권장 사항**: 팀이 100% 문서 중심이고 양식이 매우 기본적인 경우가 아니라면 모든 새 양식 프로젝트를 범용 편집기로 시작하는 것이 좋습니다.


### 문서 기반 작성 (Docs/Sheets)

문서 기반 작성은 Microsoft Word, Google Docs 또는 Google Sheets와 같은 익숙한 도구를 사용하여 간단하고 복잡도가 낮은 양식을 만드는 데 가장 적합합니다. 이 방법은 빠르고 간단하게 양식을 빌드해야 하는 콘텐츠 팀에게 이상적입니다.

- 테이블 내에서(Docs) 또는 행으로(Sheets) 양식 필드를 정의합니다.
- 기본 필드 유효성 검사 및 스팸 방지를 위한 Google reCAPTCHA를 지원합니다.
- 양식 제출은 Forms 제출 서비스를 통해서만 처리됩니다.
- 즉시 게시: 소스 문서에서 변경된 내용은 배포 파이프라인 없이도 사이트에 즉시 반영됩니다.


### 문서 작성(DA)에 양식 임베드

문서 작성(DA)은 구조화된 페이지 콘텐츠 생성을 위해 설계되었으며, 기본 양식 생성을 지원하지 않습니다. DA로 작성된 페이지에 양식을 추가하려면 다음 단계를 따르십시오.

1. **범용 편집기**(권장) 또는 문서 기반 작성을 사용하여 양식을 생성합니다.
2. 고유 URL(예: `/forms/contact-us`)을 생성하도록 양식을 게시합니다.
3. DA 페이지에서 **양식 임베드** 블록을 삽입하고 게시된 양식의 URL을 지정합니다.

<!-- 
## Feature Comparison

| Capability | Universal Editor | Document-Based | Document Authoring |
|------------|-----------------|----------------|--------------------|
| Visual drag-and-drop | ✅ | – | – |
| Advanced rules editor | ✅ | Limited | – |
| Attachments | ✅ | EA | – |
| reCAPTCHA Enterprise | ✅ | ✅ | Depends on embed |
| Submit to spreadsheet/email | ✅ (FSS) | ✅ (FSS) | Via embed |
| Submit to AEM workflows/FDM | ✅ | – | Via UE embed |
| Custom components (JS/CSS) | ✅ | ✅ | Via embed |
| Localization via Sites | ✅ | Manual | Via embed |

-->

## 다음 단계

1. **범용 편집기로 시작:** 양식 작성을 시작하려면 [범용 편집기 시작 안내서](/help/edge/docs/forms/universal-editor/overview-universal-editor-for-edge-delivery-services-for-forms.md)를 참조하십시오.
2. **양식 제출 구성:** 선호하는 제출 방법을 선택하고 설정합니다. 구성 지침은 [Forms 제출 서비스](/help/edge/docs/forms/configure-submission-action-for-eds-forms.md) 또는 AEM Publish 제출 작업을 참조하십시오.
3. **모범 사례 적용:** 접근성 및 성능을 보장하기 위해 [양식 디자인 모범 사례](/help/edge/docs/forms/universal-editor/best-practices-eds-forms.md)를 검토합니다.
4. **문서 기반 작성 사용:** Microsoft Excel 또는 Google Sheets로 양식을 생성하려면 [문서 기반 작성 튜토리얼](/help/edge/docs/forms/tutorial.md)을 따르십시오.
5. **문서 작성에 양식 임베드:** 문서 작성에서 페이지를 빌드하는 경우 게시된 양식을 임베드하는 방법에 대한 지침은 [DA 튜토리얼](https://www.aem.live/developer/da-tutorial)을 참조하십시오.

> **이제 AEM Edge Delivery Services를 사용하여 첫 번째 고성능 양식을 생성할 준비가 되었습니다.**