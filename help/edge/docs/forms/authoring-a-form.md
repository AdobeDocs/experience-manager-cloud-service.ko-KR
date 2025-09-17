---
title: AEM에서 양식을 작성하는 방법은 무엇입니까?
description: Adobe Experience Manager(AEM)에서 사용할 수 있는 다양한 양식 작성 플랫폼에 대해 알아보고, 요구 사항에 따라 적합한 플랫폼을 선택하는 방법을 알아봅니다.
feature: Edge Delivery Services, Adaptive Forms, Core Components
role: User, Developer
exl-id: bd9cb623-c272-4cdf-ad39-f97043f781a6
hide: true
index: false
hidefromtoc: true
source-git-commit: a0cb31cefb6f3c086882c237acb13020646573a5
workflow-type: ht
source-wordcount: '1075'
ht-degree: 100%

---

# Adobe Experience Manager(AEM)에서 양식을 작성하는 방법은 무엇입니까?

Adobe Experience Manager(AEM)는 매력적이고, 반응성이 뛰어나고, 역동적이며, 적응성이 뛰어난 양식을 만드는 데 유연한 플랫폼을 제공합니다. 직관적인 사용자 인터페이스와 다양한 기본 제공 구성 요소를 통해 적응형 양식을 작성하고 관리할 수 있습니다. 요구 사항에 따라 양식 모델이나 스키마를 사용하거나 사용하지 않고 양식을 작성할 수 있습니다.

## 작성 플랫폼 선택 시 주요 고려 사항

AEM은 인터랙티브하고 매력적인 양식을 만들기 위한 다양한 양식 작성 옵션을 제공합니다. 양식 작성 환경을 선택할 때 다음 요소를 고려하십시오.

| 📝 **고려 사항** | 💡 **질문 내용** |
|----------------------|--------------------|
| **사용자 전문성** | 양식을 작성하는 사람은 개발자, 비즈니스 사용자, 콘텐츠 작성자 중 누구입니까? |
| **양식 복잡성** | 양식에 고급 규칙, 동적 섹션 또는 통합이 필요합니까? |
| **재사용성 요구 사항** | 양식의 일부가 다른 양식이나 프로젝트에서 재사용될 수 있습니까? |
| **디자인 유연성** | 레이아웃, 테마, 스타일을 완벽하게 제어해야 합니까? |
| **통합 요구 사항** | 양식을 데이터 모델, 워크플로 또는 외부 시스템에 연결해야 합니까? |
| **사용의 용이성** | 플랫폼이 팀의 기술 수준에 직관적입니까? |
| **성능 및 확장성** | 양식이 대규모로 사용되거나 트래픽이 많은 환경에서 사용될 예정입니까? |
| **옴니채널 게재** | 양식이 웹 사이트, 모바일 앱, 키오스크 또는 여러 채널에서 사용될 예정입니까? |
| **게시 유연성** | 양식이 AEM, Edge Delivery 또는 사용자 정의 앱 중 어디에 게시될 예정입니까? |

## AEM에서의 양식 작성 방법 개요

AEM은 다양한 사용자 요구 사항, 기술 수준 및 게시 대상에 적합한 여러 가지 작성 방법을 지원합니다.

- [기초 구성 요소](/help/forms/create-adaptive-form-tutorial.md): 기초 구성 요소를 사용하여 기존의 대화형 양식을 작성할 수 있습니다. 기존 시스템과 통합되거나 오래된 워크플로에 의존하는 양식에 가장 적합합니다. 기초 구성 요소를 사용하여 작성된 양식은 AEM에만 게시할 수 있으며 Edge Delivery Services와 호환되지 않습니다.

- [핵심 구성 요소](/help/forms/creating-adaptive-form-core-components.md): 핵심 구성 요소를 사용하여 현대적이고 반응성이 뛰어나며 확장 가능한 양식을 만들 수 있습니다. 핵심 구성 요소는 재사용 가능하고, 접근성이 뛰어나며, 더 나은 성능을 지원합니다. 핵심 구성 요소를 사용하여 작성된 양식은 AEM과 Edge Delivery Services 모두에 게시할 수 있으므로 플랫폼 전반에 걸쳐 유연성을 제공합니다.

- [Edge Delivery Services 양식](/help/edge/docs/forms/overview.md): Edge Delivery Services 양식은 양식 작성, 실행 및 처리 방식을 변화시킵니다. 조직은 Edge Delivery Services를 활용하여 빠르고 안전하며 가용성이 높은 디지털 양식을 만들 수 있으며, 빠른 개발 환경을 통해 사용자 경험과 운영 효율성을 향상시킬 수 있습니다. Edge Delivery Services 양식은 두 가지 방법으로 작성할 수 있습니다.
   - [WYSIWYG 작성](/help/edge/docs/forms/universal-editor/overview-universal-editor-for-edge-delivery-services-for-forms.md): 제한된 기술적 지식이 있는 콘텐츠 작성자의 경우 Universal Editor를 사용하여 시각적 드래그 앤 드롭 방식으로 양식을 작성할 수 있습니다. Universal Editor를 사용하여 작성된 양식은 빠르고 가벼운 렌더링을 위해 Edge Delivery Services를 통해 게재됩니다.
   - [문서 기반 작성](/help/edge/docs/forms/tutorial.md): Microsoft Excel 또는 Google Sheets와 같은 도구를 사용하여 양식 구조와 내용을 정의합니다. 이 방법은 스프레드시트 기반 입력을 선호하는 비즈니스 사용자에게 유용합니다. 이러한 양식은 일반적으로 Edge Delivery Services를 통해 게시되며, 가벼운 고용량 사용 사례에 적합합니다.
- [Headless 작성](https://experienceleague.adobe.com/ko/docs/experience-manager-headless-adaptive-forms/using/tutorial/build-engaging-forms-using-core-components-and-headless-adaptive-forms-aem-forms-cloud-service): AEM에 의존하지 않고 API를 사용하여 React, Angular, 모바일 앱, 키오스크 등 모든 프론트엔드에서 양식을 JSON으로 렌더링합니다. 현재는 핵심 구성 요소만 Headless 게재를 지원합니다. Headless 양식은 옴니채널 사용 사례에 적합하며 AEM의 페이지 렌더링과 독립적으로 사용되므로 사용자 정의 프론트엔드 배포에 유연하게 사용할 수 있습니다.

### AEM 양식 작성 방법의 비교 분석

&#x200B;다음 표는 다양한 AEM 양식 작성 방법을 간략하게 비교한 것으로 접근 방식, 기능, 게시 옵션 및 이상적인 사용 사례를 강조하여 사용자의 요구 사항에 가장 적합한 방법을 선택하는 데 도움을 줍니다.

| **고려 사항** | **기초 구성 요소** | **핵심 구성 요소** | **Universal Editor (WYSIWYG)** | **문서 기반 작성** | **Headless 작성** |
|--------------------------|---------------------------------------------------------------------|------------------------------------------------------------------------|-------------------------------------------------------------------------|---------------------------------------------------------------------------|-------------------------------------------------------------------------|
| **적합한 용도** | AEM 내에서 기존 양식 및 워크플로 유지 관리 | 복잡한 워크플로 및 통합을 지원하는 확장 가능한 최신 양식 | 요구 사항이 복잡한 Edge Delivery Service 사이트를 위한 양식 만들기 | 빠른 프로토타이핑 또는 고급 제출 서비스가 없는 기본 양식 | 다양한 플랫폼(웹, 모바일, 키오스크 등)을 통한 옴니채널 경험 |
| **사용자 전문성** | 개발자, 콘텐츠 작성자 | 개발자, 고급 작성자 | 비즈니스 사용자, 콘텐츠 작성자 | 비즈니스 사용자 | 개발자 |
| **양식 복잡성** | 기본 양식 | 동적 섹션이 포함된 복잡한 양식 | 사용자 정의 액션이 포함된 복잡한 양식 | 간단한 양식 | 매우 복잡한 API 기반 양식 |
| **디자인 유연성** | 제한적 | 높음 (CSS/JS 사용자 정의) | 중간 (템플릿 기반) | 제한적 | 높음 (프론트엔드 프레임워크 제어) |
| **통합 기능** | 기본 AEM 워크플로 | 고급 (데이터 모델, 워크플로) | 외부 시스템과 통합 | 기본 (Google Sheets, Excel) | API를 통한 전체 제어 |
| **게시 방법** | AEM만 | AEM 및 Edge Delivery Services | Edge Delivery Services | Edge Delivery Services | API를 통한 모든 프론트엔드 |
| **성능 및 SEO** | 표준 | 기초 구성 요소보다 개선됨 | 더 빠른 렌더링과 더 나은 SEO로 높은 Google Lighthouse 점수 | 더 빠른 렌더링과 더 나은 SEO로 높은 Google Lighthouse 점수 | 구현에 따라 다름 |
| **옴니채널 게재** | 제한적 | 보통 | 보통 | 제한적 | 높음 |

<!--
| **Form authoring methods** | **Key Approach** | **Features** | **Publishing Method** | **Use Cases** |
|-----------------------------|------------------|--------------|-----------------------|---------------|
| **Foundation Components** | Classic AEM authoring interface designed for standard web pages. | Includes basic components like text, images, tables, and charts. Limited reuse capabilities and primarily web-based. | Published on AEM only. | Best for maintaining legacy forms and workflows within AEM. |
| **Core Components** | Provides a modern, flexible approach with high customization capabilities. | Component-based authoring within AEM, offering high customization with CSS and JS. Built around accessibility guidelines and integrated with AEM Sites. | Published on AEM and Edge Delivery Services. | Suitable for scalable, modern forms with complex workflows and integrations. |
| **Universal Editor (WYSIWYG)** | Offers a WYSIWYG interface for intuitive form creation. | Forms are designed using an intuitive drag-and-drop interface. These forms inherit look and feel from the configured Edge Delivery Services GitHub repository for the corresponding form. | Published on Edge Delivery Services, achieving high Google Lighthouse scores for faster rendering and better SEO. | Ideal for creating forms for Edge Delivery Service sites and pages, especially scenarios involving complex forms, workflows, custom actions, or integrations with external systems. |
| **Document-based Authoring** | Uses familiar tools like Google Docs and Microsoft Office for form creation. | Forms are designed using spreadsheets, with data directly submitted to Google Sheets or Microsoft Excel. These forms are faster to create and deploy. No prior knowledge of AEM is required to develop custom components and styles for these forms. | Published on Edge Delivery Services, achieving high Google Lighthouse scores for faster rendering and better SEO. | Ideal for quick prototyping or basic forms where advanced submission services are not needed. Well-suited for surveys, registration, or feedback forms requiring data storage in spreadsheets. |
| **Headless Authoring** | Enables API-driven content creation for omnichannel delivery. | Full control via frontend frameworks, allowing content delivery across various platforms through APIs. | Can be integrated with any frontend via APIs. | Ideal for omnichannel experiences across platforms, suitable for web, mobile, kiosks, and more. |-->

### AEM 양식 작성 방법의 기능 비교

다음 표는 다양한 AEM 양식 작성 방법의 주요 기능을 자세히 비교하여 요구 사항에 가장 적합한 방법을 선택하는 데 도움을 줍니다.&#x200B;

| **기능** | **기초 구성 요소** | **핵심 구성 요소** | **Universal Editor (WYSIWYG)** | **문서 기반 작성** | **Headless 작성** |
|-----------------------------------------|---------------------------|---------------------|-------------------------------|-----------------------------|------------------------|
| **Sites를 통한 통합 컴포지션** | ❌ | ✅ | ✅ | ❌ | ❌ |
| **양식 임베드 지원** | ✅ | ✅ | ✅ | ✅ | ✅ |
| **규칙 (동적 동작)** | 사용자 정의 함수가 포함된 고급 규칙 편집기 | 사용자 정의 함수가 포함된 고급 규칙 편집기 | 사용자 정의 함수가 포함된 고급 규칙 편집기 | 제한적: 표시/숨기기, 값 계산, 사용자 정의 함수 | 제한적: 사용자 정의 구현 필요 |
| **첨부 파일 지원** | ✅ | ✅ | ✅ | ℹ️ (얼리 액세스) | ❌ |
| **CAPTCHA 지원** | reCAPTCHA v2/Enterprise, hCaptcha(EA), Turnstile(EA) | reCAPTCHA v2/Enterprise, hCaptcha (EA) | reCAPTCHA Enterprise | reCAPTCHA Enterprise | 사용자 정의 통합 필요 |
| **제출 기능** | REST 엔드포인트, 이메일, 양식 데이터 모델(FDM), AEM 워크플로 호출, SharePoint, OneDrive, Azure Blob Storage, Power Automate, Workfront Fusion(EA) | REST 엔드포인트, 이메일, 양식 데이터 모델(FDM), AEM 워크플로 호출, SharePoint, OneDrive, Azure Blob Storage, Power Automate, Workfront Fusion(EA) | REST 엔드포인트, 이메일, 양식 데이터 모델(FDM), AEM 워크플로 호출, SharePoint, OneDrive, Azure Blob Storage, Power Automate, Workfront Fusion(EA) | 스프레드시트만 | 사용자 정의 API 엔드포인트 |
| **데이터 스키마** | FDM, 사용자 정의 | FDM, 사용자 정의 | FDM, 사용자 정의 | 사용자 정의 | 사용자 정의 |
| **미리 채우기** | ✅ | ✅ | 💡 (마법사 사용) | ✅ | 사용자 정의 구현 |
| **조각** | ✅ | ✅ | ✅ | ✅ | ❌ |
| **시각적 규칙 편집기** | ✅ | ✅ | ✅ | ❌ | ❌ |
| **현지화** | ✅ | ✅ | 💡 (Sites 사용) | ℹ️ (Excel - 수동, Google Sheets 함수) | 사용자 정의 구현 |
| **데이터 스키마 (데이터 트리)** | ✅ | ✅ | 💡 (UI 확장 기능 사용) | ❌ | 사용자 정의 구현 |
| **템플릿 지원** | ✅ | ✅ | 초기 콘텐츠만 제공, 정책 없음 | ❌ | 사용자 정의 구현 |
| **포털** | ✅ | ✅ | ❌ | ❌ | ❌ |
| **DoR 작성** | ✅ | ✅ | 💡 (Derlina 사용) | ❌ | ❌ |
| **DoR 생성** | ✅ | ✅ | 💡 (FORMS-2475 New) | ❌ | ❌ |
| **테마** | ✅ | ✅ | ℹ️ (프로젝트 수준에서) | ℹ️ (프로젝트 수준에서) | 사용자 정의 구현 |
| **사용자 정의 구성 요소** | ✅ | ✅ | ✅ | ✅ | ✅ |
| **OOTB 및 사용자 정의 함수** | ✅ | ✅ | ✅ | ✅ | ✅ |
| **조각 참조** | ✅ | ❌ | ❌ | ❌ | ❌ |
| **Sign 통합** | ✅ | ❌ | ❌ | ❌ | ❌ |
| **RTL 지원** | ❌ | ✅ | 💡 | 💡 | 사용자 정의 구현 |
| **실험** | ❌ | ❌ | ✅ | ✅ | 사용자 정의 구현 |
| **Workfront를 통한 작업 관리** | ❌ | ❌ | ✅ | ❌ | ❌ |
| **개인화 확장 기능** | ❌ | ❌ | 💡 | ❌ | 사용자 정의 구현 |
| **편집기 사용자 정의** | ❌ | ❌ | ✅ (UI 확장 기능 사용) | ❌ | 사용자 정의 구현 |
| **제출 액션** | ✅ | ✅ | ✅ | 스프레드시트만 | 사용자 정의 구현 |


## 관련 문서

- [Microsoft Excel 또는 Google Sheets를 사용하여 문서 기반 작성](/help/edge/docs/forms/create-forms.md)
- [WYSIWYG 작성용 Universal Editor](https://experienceleague.adobe.com/ko/docs/experience-manager-cloud-service/content/edge-delivery/wysiwyg-authoring/authoring)
- [적응형 양식(기초 구성 요소) 만들기](/help/forms/creating-adaptive-form.md)
- [적응형 양식(핵심 구성 요소) 만들기](/help/forms/create-an-adaptive-form.md)
