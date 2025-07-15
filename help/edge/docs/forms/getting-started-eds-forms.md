---
title: AEM Edge Delivery Services의 Forms 시작하기
description: 범용 편집기 작성 접근 방식을 강조하여 Adobe Experience Manager Edge Delivery Services에서 고성능 양식을 만들고 전달하는 방법을 알아봅니다.
feature: Edge Delivery Services
exl-id: ecea1e05-d36b-4d63-af9d-c69dafd2f94f
role: Admin, Architect, Developer
source-git-commit: e1ead9342fadbdf82815f082d7194c9cdf6d799d
workflow-type: tm+mt
source-wordcount: '591'
ht-degree: 5%

---


# AEM Edge Delivery Services의 Forms 시작하기

<span class="preview"> <a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/release-notes/prerelease.html?lang=ko#new-features">시험판 채널</a>을 통해 사용할 수 있는 시험판 기능입니다. </span>

Adobe Experience Manager(AEM) EDS(Edge Delivery Services)를 사용하면 엣지에서 매우 빠르고 확장성이 뛰어난 웹 경험을 제공할 수 있습니다. 이 안내서에서는 명확한 권장 계층 구조를 사용하여 **이러한 경험에 대한 양식을 작성하고 게시하는 방법**&#x200B;을 설명합니다.

1. **유니버설 편집기(UE) - 대부분의 팀에 가장 적합한 옵션**
2. **문서 기반 작성(문서/시트) - 빠르고 간단한 양식에 적합**
3. **DA(문서 작성) - DA가 작성된 페이지에 양식을 포함하는 데 사용**

마지막에 올바른 작성 방법을 선택하고 제출 옵션을 이해한 다음, 프로덕션 준비 양식에 대한 다음 단계를 따를 수 있습니다.



## 작성 방법 선택

| 팀 및 요구 사항 | 권장 메서드 | 이유 |
|--------------------|--------------------|-----|
| 마케터/디자이너는 시각적 제어, 조건부 논리 또는 AEM 통합이 필요합니다 | **Universal Editor** | 드래그 앤 드롭, 고급 규칙, FSS 또는 AEM 게시로 제출 |
| 이미 Word/Google Docs/Sheets에서 작업 중인 콘텐츠 작성자, 스프레드시트/이메일로 간단한 데이터 캡처 | **문서 기반 작성** | 친숙한 도구, 기본 양식을 위한 가장 빠른 경로 |
| **DA(문서 작성)**&#x200B;에 빌드된 웹 사이트 페이지 | DA 페이지에 UE 또는 문서 기반 양식을 **포함** | DA는 양식 자체를 빌드하지 않습니다. |


## 작성 방법 세부 정보

### Universal Editor

범용 편집기는 속도와 엔터프라이즈급 성능을 결합한 마케터 및 디자이너를 위한 시각적, 드래그 앤 드롭 작성 도구입니다.

* 실시간 WYSIWYG 편집 및 장치 미리 보기.
* 고급 규칙 및 유효성 검사 UI - 코드가 필요하지 않습니다.
* AEM 자산, 워크플로우 및 양식 데이터 모델(FDM)과 직접 통합합니다.
* 바닐라 JS/CSS의 사용자 지정 구성 요소에 대해 개발자에게 매끄러운 핸드오프입니다.
* 유연한 제출 대상: 필요에 따라 **Forms 제출 서비스(FSS)**&#x200B;로 단순하게 시작하거나 **AEM 게시 제출 작업**(으)로 전환하십시오.

> **권장 사항**: 팀이 100% 문서 중심이고 양식이 매우 기본이 아닌 경우 유니버설 편집기로 모든 새 양식 프로젝트를 시작하십시오.


### 문서 기반 작성(문서/시트)

문서 기반 작성은 Microsoft Word, Google Docs 또는 Google Sheets와 같은 친숙한 도구를 사용하여 단순하고 복잡하지 않은 양식을 작성하는 데 가장 적합합니다. 이 방법은 양식을 빠르고 간단하게 작성하는 방법이 필요한 콘텐츠 팀에 이상적입니다.

* 테이블(문서) 내의 양식 필드를 행(시트)으로 정의합니다.
* 스팸 보호를 위해 기본 필드 유효성 검사 및 Google reCAPTCHA를 지원합니다.
* 양식 제출은 Forms 제출 서비스를 통해서만 처리됩니다.
* 즉시 게시 - 소스 문서의 변경 사항은 배포 파이프라인 없이도 사이트에 즉시 반영됩니다.


### DA(문서 작성)에 Forms 포함

DA(Document Authoring)는 구조화된 페이지 콘텐츠를 만들기 위해 설계되었으며 기본 양식 만들기를 지원하지 않습니다. DA 작성 페이지에 양식을 추가하려면 다음 단계를 수행합니다.

1. **범용 편집기**(권장) 또는 문서 기반 작성을 사용하여 양식을 만듭니다.
2. 양식을 게시하여 고유한 URL을 생성합니다(예: `/forms/contact-us`).
3. DA 페이지에서 **양식 포함** 블록을 삽입하고 게시된 양식의 URL을 지정하십시오.

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

1. **유니버설 편집기로 시작:** 양식 작성을 시작하려면 [유니버설 편집기 시작 안내서](/help/edge/docs/forms/universal-editor/overview-universal-editor-for-edge-delivery-services-for-forms.md)를 참조하세요.
2. **양식 전송 구성:** 선호하는 전송 방법을 선택하고 설정합니다. 구성 지침은 [Forms 제출 서비스](/help/edge/docs/forms/configure-submission-action-for-eds-forms.md) 또는 AEM 게시 제출 액션을 참조하십시오.
3. **모범 사례 적용:** [양식 디자인 모범 사례](/help/edge/docs/forms/universal-editor/best-practices-eds-forms.md)를 검토하여 접근성과 성능을 확인하십시오.
4. **문서 기반 작성 사용:** Microsoft Excel 또는 Google Sheets로 양식을 만들려면 [문서 기반 작성 자습서](/help/edge/docs/forms/tutorial.md)를 따르십시오.
5. **문서 작성에 Forms 포함:** 문서 작성에서 페이지를 작성하는 경우 [DA 자습서](https://www.aem.live/developer/da-tutorial)에서 게시된 양식 포함에 대한 지침을 참조하십시오.

> **이제 AEM Edge Delivery Services을 사용하여 첫 번째 고성능 양식을 만들 준비가 되었습니다.**