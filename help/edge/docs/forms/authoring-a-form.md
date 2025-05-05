---
title: AEM에서 양식을 작성하는 방법
description: Adobe Experience Manager(AEM)에서 사용할 수 있는 다양한 양식 작성 플랫폼과 요구 사항에 따라 올바른 양식 작성 플랫폼을 선택하는 방법에 대해 알아봅니다.
feature: Edge Delivery Services, Adaptive Forms, Core Components
role: User, Developer
hide: true
hidefromtoc: true
source-git-commit: f6c6b4c17482eb519fb0d4287704d775d0a5da00
workflow-type: tm+mt
source-wordcount: '1176'
ht-degree: 7%

---


# Adobe Experience Manager(AEM)에서 Forms을 작성하는 방법

Adobe Experience Manager(AEM)는 매력적인 반응형, 동적 및 적응형 양식을 만들 수 있는 유연한 플랫폼을 제공합니다. 적응형 Forms을 구축하고 관리할 수 있는 직관적인 사용자 인터페이스와 다양한 기본 구성 요소 세트를 제공합니다. Forms은 요구 사항에 따라 양식 모델 또는 스키마를 사용하거나 사용하지 않고 작성할 수 있습니다.

## 작성 플랫폼을 선택하는 동안의 주요 고려 사항

AEM은 대화형의 매력적인 양식을 만들 수 있는 다양한 양식 작성 옵션을 제공합니다. 양식 작성 환경을 선택할 때는 다음 요소를 고려하십시오.

| ?? **고려 사항** | ?? **질문할 내용** |
|----------------------|--------------------|
| **사용자 전문 지식** | 개발자, 비즈니스 사용자 또는 콘텐츠 작성자 등 누가 양식을 작성합니까? |
| **양식 복잡성** | 양식에 고급 규칙, 동적 섹션 또는 통합이 필요합니까? |
| **재사용성 필요** | 양식의 일부가 다른 양식 또는 프로젝트에서 재사용됩니까? |
| **디자인 유연성** | 레이아웃, 테마 및 스타일을 완전히 제어해야 합니까? |
| **통합 요구 사항** | 양식이 데이터 모델, 워크플로우 또는 외부 시스템에 연결해야 합니까? |
| **사용 편의성** | 귀사의 기술 수준에 맞게 플랫폼이 직관적입니까? |
| **성능 및 확장성** | 양식이 규모에 맞게 사용됩니까, 아니면 트래픽이 많은 환경에서 사용됩니까? |
| **옴니채널 게재** | 양식이 웹 사이트, 모바일 앱, 키오스크 또는 여러 채널에서 사용됩니까? |
| **게시 유연성** | AEM, Edge Delivery 또는 사용자 정의 앱에서 양식이 게시되는 위치는 어디입니까? |

## AEM의 양식 작성 방법 개요

AEM은 다양한 사용자 요구 사항, 기술 기술 수준 및 게시 대상에 적합한 여러 작성 방법을 지원합니다.

* [Foundation 구성 요소](/help/forms/create-adaptive-form-tutorial.md): Foundation 구성 요소를 사용하여 기존의 대화형 양식을 빌드합니다. 기존 시스템과 통합되거나 오랫동안 구축된 워크플로우를 사용하는 양식에 가장 적합합니다. 기초 구성 요소로 작성된 Forms은 AEM에서만 게시할 수 있으며 Edge Delivery Services과 호환되지 않습니다.

* [핵심 구성 요소](/help/forms/creating-adaptive-form-core-components.md): 핵심 구성 요소를 사용하여 최신 반응형 확장 가능한 양식을 만드십시오. 재사용 가능성, 접근성 및 향상된 성능을 지원합니다. 핵심 구성 요소로 작성된 Forms은 AEM 및 Edge Delivery Services 모두에서 게시할 수 있으므로 플랫폼 간에 유연성을 제공합니다.

* [Edge Delivery Services Forms](/help/edge/docs/forms/overview.md): Edge Delivery Services Forms은 양식을 작성, 실행 및 처리하는 방법을 변환합니다. 조직은 Edge Delivery Services를 활용하여 빠르고 안전하며 가용성이 높은 디지털 양식을 만들 수 있으며, 빠른 개발 환경을 통해 사용자 경험과 운영 효율성을 향상시킬 수 있습니다. 다음 두 가지 방법으로 Edge Delivery Services Forms을 작성할 수 있습니다.
   * [WYSIWYG 작성](/help/edge/docs/forms/universal-editor/overview-universal-editor-for-edge-delivery-services-for-forms.md): 기술적 지식이 제한된 콘텐츠 작성자에게 적합한 시각적, 끌어서 놓기 양식 작성에는 범용 편집기를 사용하십시오. 범용 편집기로 작성된 Forms은 빠르고 가벼운 렌더링을 위해 Edge Delivery Services을 사용하여 제공됩니다.
   * [문서 기반 작성](/help/edge/docs/forms/tutorial.md): Microsoft Excel 또는 Google Sheets와 같은 도구를 사용하여 양식 구조 및 콘텐츠를 정의합니다. 이 방법은 스프레드시트 기반 입력을 선호하는 비즈니스 사용자에게 유용합니다. 이러한 양식은 일반적으로 Edge Delivery Services을 통해 게시되며 가벼운 대량 사용 사례에 적합합니다.
* [Headless 작성](https://experienceleague.adobe.com/ko/docs/experience-manager-headless-adaptive-forms/using/tutorial/build-engaging-forms-using-core-components-and-headless-adaptive-forms-aem-forms-cloud-service): AEM에 의존하지 않고 API를 사용하여 React, Angular, 모바일 앱 또는 키오스크와 같은 프런트 엔드에 대해 양식을 JSON으로 렌더링합니다. 현재 핵심 구성 요소만 Headless 전달을 지원합니다. Headless 양식은 옴니채널 사용 사례에 이상적이며 AEM의 페이지 렌더링과 독립적으로 사용되므로 사용자 정의 프론트엔드 배포에 유연하게 사용할 수 있습니다.

### AEM 양식 작성 방법 비교 분석

다음 표는 다양한 AEM 양식 작성 방법을 간결하게 비교하여 &#x200B; 접근 방식, 기능, 게시 옵션 및 이상적인 사용 사례를 강조하여 요구 사항에 가장 적합한 방법을 선택할 수 있도록 합니다.

| **고려 사항** | **기초 구성 요소** | **핵심 구성 요소** | **유니버설 편집기(WYSIWYG)** | **문서 기반 작성** | **헤드리스 작성** |
|--------------------------|---------------------------------------------------------------------|------------------------------------------------------------------------|-------------------------------------------------------------------------|---------------------------------------------------------------------------|-------------------------------------------------------------------------|
| **이상적 대상** | AEM 내에서 기존 양식 및 워크플로 유지 관리 | 복잡한 워크플로우 및 통합을 통해 확장 가능한 최신 양식 | 복잡한 요구 사항을 갖춘 Edge Delivery 서비스 사이트용 양식 만들기 | 고급 제출 서비스를 사용하지 않는 빠른 프로토타이핑 또는 기본 양식 | 플랫폼(웹, 모바일, 키오스크 등)에서의 옴니채널 경험 |
| **사용자 전문 지식** | 개발자, 콘텐츠 작성자 | 개발자, 고급 작성자 | 비즈니스 사용자, 콘텐츠 작성자 | 비즈니스 사용자 | 개발자 |
| **양식 복잡성** | 기본 양식 | 동적 섹션이 포함된 복잡한 양식 | 사용자 지정 작업이 포함된 복잡한 양식 | 단순 양식 | 매우 복잡한 API 기반 양식 |
| **디자인 유연성** | 제한적 | 높음(CSS/JS 사용자 지정) | 중재(템플릿 기반) | 제한적 | 높음(프론트엔드 프레임워크 제어) |
| **통합 기능** | 기본 AEM 워크플로 | 고급(데이터 모델, 워크플로) | 외부 시스템과 통합 | 기본(Google Sheets, Excel) | API를 통한 전체 제어 |
| **게시 방법** | AEM 전용 | AEM 및 Edge Delivery Services | Edge Delivery Services | Edge Delivery Services | API를 통한 모든 프론트엔드 |
| **성능 및 SEO** | 표준 | 기초 구성 요소에 비해 개선됨 | 더 빠른 렌더링 및 더 나은 SEO를 위한 높은 Google 등대 점수 | 더 빠른 렌더링 및 더 나은 SEO를 위한 높은 Google 등대 점수 | 구현에 따라 다름 |
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

다음 표는 다양한 AEM 양식 작성 방법 간의 주요 기능을 자세히 비교하여 요구 사항에 가장 적합한 방법을 선택하는 데 도움이 됩니다&#x200B;.

| **기능** | **기초 구성 요소** | **핵심 구성 요소** | **유니버설 편집기(WYSIWYG)** | **문서 기반 작성** | **헤드리스 작성** |
|-----------------------------------------|---------------------------|---------------------|-------------------------------|-----------------------------|------------------------|
| **Sites를 사용한 통합 구성** | ❌ | ✅ | ✅ | ❌ | ❌ |
| **양식 지원 포함** | ✅ | ✅ | ✅ | ✅ | ✅ |
| **규칙(동적 동작)** | 사용자 정의 기능이 있는 고급 규칙 편집기 | 사용자 정의 기능이 있는 고급 규칙 편집기 | 사용자 정의 기능이 있는 고급 규칙 편집기 | 제한적: 표시/숨기기, 값 계산, 사용자 정의 함수 | 제한적: 사용자 지정 구현 필요 |
| **첨부 파일 지원** | ✅ | ✅ | ✅ | ℹ️(조기 액세스) | ❌ |
| **CAPTCHA 지원** | reCAPTCHA v2/Enterprise, hCaptcha (EA), Turnstile (EA) | reCAPTCHA v2/Enterprise, hCaptcha (EA) | reCAPTCHA Enterprise | reCAPTCHA Enterprise | 사용자 정의 통합 필요 |
| **제출 기능** | REST 끝점, 이메일, 양식 데이터 모델(FDM), AEM 워크플로 호출, SharePoint, OneDrive, Azure Blob Storage, Power Automate, Workfront Fusion(EA) | REST 끝점, 이메일, 양식 데이터 모델(FDM), AEM 워크플로 호출, SharePoint, OneDrive, Azure Blob Storage, Power Automate, Workfront Fusion(EA) | REST 끝점, 이메일, 양식 데이터 모델(FDM), AEM 워크플로 호출, SharePoint, OneDrive, Azure Blob Storage, Power Automate, Workfront Fusion(EA) | 스프레드시트만 | 사용자 지정 API 엔드포인트 |
| **데이터 스키마** | FDM, 사용자 정의 | FDM, 사용자 정의 | FDM, 사용자 정의 | 사용자 정의 | 사용자 정의 |
| **미리 채우기** | ✅ | ✅ | ?? (마법사를 통해) | ✅ | 사용자 정의 구현 |
| **조각** | ✅ | ✅ | ✅ | ✅ | ❌ |
| **시각적 규칙 편집기** | ✅ | ✅ | ✅ | ❌ | ❌ |
| **로컬라이제이션** | ✅ | ✅ | ?? (사이트를 통해) | ℹ️ (Excel - 수동, Google Sheets 함수) | 사용자 정의 구현 |
| **데이터 스키마(데이터 트리)** | ✅ | ✅ | ?? (UI 확장 사용) | ❌ | 사용자 정의 구현 |
| **템플릿 지원** | ✅ | ✅ | 초기 콘텐츠만, 정책 없음 | ❌ | 사용자 정의 구현 |
| **포털** | ✅ | ✅ | ❌ | ❌ | ❌ |
| **DoR 작성** | ✅ | ✅ | ?? (Derlina를 통해) | ❌ | ❌ |
| **DoR 생성** | ✅ | ✅ | ?? (FORMS-2475 신규) | ❌ | ❌ |
| **테마** | ✅ | ✅ | ℹ️(프로젝트 수준) | ℹ️(프로젝트 수준) | 사용자 정의 구현 |
| **사용자 지정 구성 요소** | ✅ | ✅ | ✅ | ✅ | ✅ |
| **OOTB 및 사용자 지정 함수** | ✅ | ✅ | ✅ | ✅ | ✅ |
| **조각 참조** | ✅ | ❌ | ❌ | ❌ | ❌ |
| **통합 서명** | ✅ | ❌ | ❌ | ❌ | ❌ |
| **RTL 지원** | ❌ | ✅ | ?? | ?? | 사용자 정의 구현 |
| **실험** | ❌ | ❌ | ✅ | ✅ | 사용자 정의 구현 |
| **Workfront을 통한 작업 관리** | ❌ | ❌ | ✅ | ❌ | ❌ |
| **Personalization 확장** | ❌ | ❌ | ?? | ❌ | 사용자 정의 구현 |
| **편집기 사용자 지정** | ❌ | ❌ | ✅(UI 확장 사용) | ❌ | 사용자 정의 구현 |
| **작업 제출** | ✅ | ✅ | ✅ | 스프레드시트만 | 사용자 정의 구현 |


## 관련 문서

* [Microsoft Excel 또는 Google Sheets를 사용하여 문서 기반 작성](/help/edge/docs/forms/create-forms.md)
* [WYSIWYG 작성용 범용 편집기](https://experienceleague.adobe.com/ko/docs/experience-manager-cloud-service/content/edge-delivery/wysiwyg-authoring/authoring)
* [적응형 양식(기초 구성 요소) 만들기](/help/forms/creating-adaptive-form.md)
* [적응형 양식(핵심 구성 요소) 만들기](/help/forms/create-an-adaptive-form.md)
