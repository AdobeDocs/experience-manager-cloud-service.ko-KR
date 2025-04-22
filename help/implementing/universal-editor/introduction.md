---
title: Universal Editor 소개
description: 유니버설 편집기는 마케팅 조직이 효과적인 웹 경험을 제작할 수 있도록 고안된 최신 시각적 작성 도구입니다.
exl-id: d4fc2384-a0f5-4a6f-9572-62749786be4c
feature: Developing
role: Admin, Architect, Developer
source-git-commit: ae59b00e7e8149477a87d0b0b63493a6c2cfebe7
workflow-type: tm+mt
source-wordcount: '956'
ht-degree: 13%

---


# Universal Editor 소개 {#introduction}

유니버설 편집기는 마케팅 조직이 효과적인 웹 경험을 제작할 수 있도록 고안된 최신 시각적 작성 도구입니다.

## 개요 {#overview}

범용 편집기는 Adobe Experience Manager Sites의 일부인 다목적 비주얼 편집기입니다. 이를 통해 작성자는 Headless 또는 Headful 경험에 대한 보이는 항목(WYSIWYG) 편집을 수행할 수 있습니다. 제공되는 기능은 다음과 같습니다.

* **즉시 편집**: 작성자가 미리 보기 환경에서 직접 콘텐츠를 편집할 수 있으므로 개별 콘텐츠 원본을 찾아 이동할 필요가 없습니다.
* **시각적 편집**: 작성자는 변경을 수행하는 동안 실제 방문자 경험에 어떤 영향을 미치는지 즉시 확인하여 마찰을 최소화합니다.
* **검색 가능한 옵션**: 레이블이 명확하게 지정된 옵션과 직관적인 UI를 통해 작성자는 메타데이터를 쉽게 구성하고 레이아웃을 구성할 수 있습니다.
* **비기술적**: 편집하는 데 전문 지식이 필요하지 않지만 회사 브랜드 지침은 자동으로 적용되어 조직 전반에서 콘텐츠 작업의 크기를 용이하게 할 수 있습니다.
* **통합 및 확장성**: AEM과 완전히 통합된 유니버설 편집기의 유연한 [확장 지점](#extensibility)을 통해 모든 필수 도구를 통합적인 단일 인터페이스 내에서 통합할 수 있습니다. AI 기반 기능에서 고유한 비즈니스 요구 사항에 맞는 맞춤형 확장에 이르기까지, 팀은 워크플로를 간소화하고 생산성을 손쉽게 향상시킬 수 있습니다.

요약:

* **작성자는 모든 형식의 AEM 콘텐츠에 대해 동일한 일관된 시각적 편집을 지원하므로 유니버설 편집기의 유연성이 향상됩니다**.
* 구현의 진정한 분리를 지원하므로 **개발자는 유니버설 편집기의 다기능성을 활용할 수 있습니다**.

진정한 편집기로서의 서비스로서 전체적으로 더 융통성 있는 유니버설 편집기는 결국 [페이지 편집기](/help/sites-cloud/authoring/page-editor/introduction.md)를 대체하려고 합니다.

## 지원되는 아키텍처 {#supported-architectures}

범용 편집기는 다음 두 가지 기본 AEM 설정을 지원합니다.

1. **[Edge Delivery Services](/help/edge/overview.md)**: 간소화, 가치 실현 시간 단축 및 성능 향상을 위해 선호되는 접근 방법입니다.
1. **[Headless 구현](/help/headless/introduction.md)**: 기존 Headless 프로젝트 또는 분리된 렌더링에 대한 특정 요구 사항이 있는 경우 유니버설 편집기를 사용하면 전체 프로젝트를 리팩터링할 필요 없이 엔터프라이즈급 시각적 편집을 사용할 수 있습니다. 거의 모든 아키텍처(SSR, CSR), 웹 프레임워크(Next.js, React, Astro 등) 및 호스팅 모델(&quot;Bring your own app&quot;)과 호환됩니다.

>[!TIP]
>
>지원되는 아키텍처에 대한 자세한 내용은 [유니버설 편집기 사용 사례 및 학습 경로](/help/implementing/universal-editor/use-cases.md) 문서를 참조하십시오.

## 지원되는 AEM 버전 {#aem-versions}

유니버설 편집기는 다음에서 지원합니다.

* AEM as a Cloud Service(릴리스 `2023.8.13099` 이상)
* AEM 6.5(서비스 팩 21 또는 22 + 기능 팩 추가)
   * 온-프레미스 및 AMS 호스팅이 모두 지원됩니다.

이 설명서는 AEM as a Cloud Service과 함께 범용 편집기를 사용하기 위한 것입니다. AEM 6.5에서 유니버설 편집기를 사용하려면 [AEM 6.5 설명서를 참조하십시오.](https://experienceleague.adobe.com/ko/docs/experience-manager-65/content/implementing/developing/headless/universal-editor/introduction)

## 기능 {#features}

유니버설 편집기는 효율적인 콘텐츠 관리를 위한 다양한 사용 사례를 지원하는 다양한 기능을 제공합니다.

* **[WYSIWYG](/help/sites-cloud/authoring/universal-editor/authoring.md)**: 일반 텍스트, 서식 있는 텍스트, 미디어 및 메타데이터를 비롯한 모든 형식의 웹 콘텐츠를 편집합니다.
* **[컴포지션](/help/sites-cloud/authoring/universal-editor/authoring.md#editing-content)**: 다양한 유형의 콘텐츠 블록(제목, 단추, 티저, 섹션, 포함 등)을 만들거나 편집하거나, 다시 정렬하거나, 중첩하거나, 삭제합니다.
* **[레이아웃](/help/sites-cloud/authoring/universal-editor/templates.md)**: 페이지 템플릿을 사용하고, 시각적 스타일을 적용하고, 열, 회전 메뉴 및 아코디언과 같은 블록으로 레이아웃을 구성합니다.
* **[장치 시뮬레이션](/help/sites-cloud/authoring/universal-editor/navigation.md#emulator)**: 편집하는 동안 다른 방문자 장치에 대한 콘텐츠를 미리 보고 최적화합니다.
* **옴니채널**: 여러 채널에서 정형 콘텐츠와 비정형 콘텐츠를 모두 다시 사용합니다.
* **[지역화](/help/sites-cloud/authoring/universal-editor/inheritance.md)**: 다중 사이트 관리자를 사용하여 콘텐츠 번역 워크플로를 간소화하고 지역화된 콘텐츠 상속을 효율적으로 처리합니다.
* **일관성**: 브랜드 지침을 준수하고 모든 콘텐츠에 일관성을 유지합니다.
* **보안**: [액세스 제어 적용](/help/implementing/universal-editor/authentication.md), 콘텐츠 무결성 보호, [강력한 버전 관리로 변경 내용 추적](/help/sites-cloud/authoring/sites-console/page-versions.md)
* **[게시](/help/sites-cloud/authoring/universal-editor/publishing.md)**: 검토, 승인 및 게시 워크플로를 편집기 내에서 직접 통합합니다.
* **통합**: [사이트 콘솔,](/help/sites-cloud/authoring/sites-console/introduction.md) [콘텐츠 조각 편집기,](/help/sites-cloud/administering/content-fragments/overview.md) 등과 같은 AEM 도구와 완전히 통합되어 일관된 작성 환경을 제공합니다.

## 확장성 {#extensibility}

범용 편집기는 즉시 사용할 수 있을 뿐만 아니라 다양한 확장 기능을 제공합니다.

* **확장**&#x200B;에는 워크플로 지원, 변형 생성, 실험 지원 등 다양한 요구 사항을 지원할 수 있는 준비된 확장이 많습니다.
* **확장 가능한 UI**&#x200B;를 사용하면 준비된 확장이 활용하는 기본 프레임워크와 동일한 기본 프레임워크를 사용하여 고유한 확장을 만들 수 있으므로 프로젝트 요구 사항에 맞게 유연하게 조정할 수 있습니다.
* 블록, 사용자 지정 데이터 형식 및 이벤트와 같은 **확장 지점**&#x200B;을 사용하면 UI 이상의 사용자 지정 비즈니스 요구 사항을 매끄럽게 통합할 수 있습니다.

>[!TIP]
>
>유니버설 편집기의 확장성에 대한 자세한 내용은 [유니버설 편집기 확장](/help/implementing/universal-editor/extending.md) 문서를 참조하십시오.

## Universal Editor와 콘텐츠 조각 편집기 {#universal-editor-content-fragment-editor}

얼핏 보면 Universal Editor와 콘텐츠 조각 편집기가 유사한 편집 기능을 제공하는 것처럼 보일 수 있습니다. 단, 두 편집기는 서로 매우 다른 기능을 제공하며 마케팅 실무자의 다른 작업을 담당합니다.

### 콘텐츠 조각 편집기 {#content-fragment-editor}

마케팅 실무자가 레이아웃에 신경 쓰지 않고 콘텐츠를 만들어 다양한 경험 컨텍스트에서 재사용할 수 있기를 원합니다.

* 수행해야 할 기본 작업은 콘텐츠 전략을 확장하는 것입니다.

### Universal Editor  {#universal-editor}

마케팅 실무자가 뛰어난 경험을 제공하기 위해 주어진 컨텍스트의 레이아웃에 맞는 콘텐츠를 만들고자 합니다.

* 수행해야 할 기본 작업은 독자와 설득력 있게 소통하는 것입니다.

## 제한 사항 {#limitations}

유니버설 편집기를 살펴보고 고유한 프로젝트에서 이를 구현하는 데 있어 다음 제한 사항을 염두에 두십시오.

* 단일 페이지에서 계측을 위해 AEM 리소스(콘텐츠 조각, 페이지, 경험 조각, Assets 등)를 25개 이하로 지정해야 합니다.
* AEM as a Cloud Service 및 [AEM 6.5](https://experienceleague.adobe.com/ko/docs/experience-manager-65/content/implementing/developing/headless/universal-editor/introduction)만 지원되는 AEM 백엔드입니다.
* AEM as a Cloud Service에는 릴리스 `2023.8.13099` 이상이 필요합니다.
* 콘텐츠 작성자는 고유한 개별 Experience Cloud 계정이 있어야 합니다.
* AEM의 일부로 범용 편집기 [은(는) AEM과 동일한 데스크톱 브라우저를 지원합니다.](/help/overview/supported-platforms.md)
   * 이러한 브라우저의 모바일 버전은 지원되지 않습니다.

{{ip-allow-lists-ue}}

## 다음 단계 {#next-steps}

유니버설 편집기의 일반적인 사용 사례에 대해 자세히 알아보고 프로젝트에서 지원할 올바른 설명서 리소스를 검색하려면 [유니버설 편집기 사용 사례 및 학습 경로](/help/implementing/universal-editor/use-cases.md) 문서를 참조하십시오.
