---
title: 범용 편집기 소개
description: 범용 편집기는 마케팅 조직이 영향력 있는 웹 경험을 제작할 수 있도록 지원하기 위해 설계된 최신 시각적 작성 도구입니다.
exl-id: d4fc2384-a0f5-4a6f-9572-62749786be4c
feature: Developing
role: Admin, Developer
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '948'
ht-degree: 100%

---


# 범용 편집기 소개 {#introduction}

범용 편집기는 마케팅 조직이 영향력 있는 웹 경험을 제작할 수 있도록 지원하기 위해 설계된 최신 시각적 작성 도구입니다.

## 개요 {#overview}

범용 편집기는 Adobe Experience Manager Sites의 일부인 다용도 시각적 편집기입니다. 작성자는 모든 헤드리스 또는 헤드풀 경험에 대한 WYSIWYG(what-you-see-is-what-you-get) 편집을 수행할 수 있습니다. 제공되는 기능은 다음과 같습니다.

* **즉시 편집**: 작성자는 미리보기 경험 내에서 콘텐츠를 직접 편집할 수 있으므로 개별 콘텐츠 소스를 찾고 탐색할 필요가 없습니다.
* **시각적 편집**: 변경하는 동안 작성자는 변경 내용이 실제 방문자 경험에 어떤 영향을 미치는지 즉시 확인하여 마찰을 최소화합니다.
* **검색 가능한 옵션**: 명확한 레이블이 지정된 옵션과 직관적인 UI를 통해 작성자는 메타데이터를 구성하고 레이아웃을 쉽게 구성할 수 있습니다.
* **비기술**: 편집을 위해 전문적인 전문 지식이 필요하지 않으며, 기업 브랜드 지침이 자동으로 적용되어 조직 전체에서 콘텐츠 작업을 확장할 수 있습니다.
* **통합 및 확장성**: AEM과 완벽하게 통합된 범용 편집기의 유연한 [확장 지점](#extensibility)을 통해 모든 필수 도구를 하나의 응집력 있는 인터페이스 내에서 통합할 수 있습니다. AI 기반 기능부터 고유한 비즈니스 요구 사항에 맞는 사용자 정의 확장 기능에 이르기까지 팀은 워크플로를 간소화하고 생산성을 손쉽게 향상시킬 수 있습니다.

요약하면 다음과 같습니다.

* **작성자는** 모든 형태의 AEM 콘텐츠에 대해 동일하고 일관된 시각적 편집을 지원하므로 범용 편집기의 유연성으로부터 이점을 얻습니다.
* **개발자는** 구현의 진정한 분리를 지원하므로 범용 편집기의 다양성으로부터 이점을 얻습니다.

진정한 서비스형 편집기이며 전반적으로 더 유연한 범용 편집기는 궁극적으로 [페이지 편집기](/help/sites-cloud/authoring/page-editor/introduction.md)를 대체하는 것을 목표로 합니다.

## 지원되는 아키텍처 {#supported-architectures}

범용 편집기는 다음 두 가지 주요 AEM 설정을 지원합니다.

1. **[Edge Delivery Services](/help/edge/overview.md)**: 이는 단순성, 더 빠른 가치 창출 시간 및 향상된 성능을 위한 기본 접근 방식입니다.
1. **[Headless 구현](/help/headless/introduction.md)**: 기존 Headless 프로젝트가 있거나 분리된 렌더링에 대한 특정 요구 사항이 있는 경우, 범용 편집기는 전체 프로젝트를 리팩토링할 필요 없이 엔터프라이즈급 시각적 편집을 허용합니다. 사실상 모든 아키텍처(SSR, CSR), 웹 프레임워크(Next.js, React, Astro 등) 및 호스팅 모델(“자체 앱 가져오기”)과 호환됩니다.

>[!TIP]
>
>지원되는 아키텍처에 대한 자세한 내용은 [범용 편집기 사용 사례 및 학습 경로](/help/implementing/universal-editor/use-cases.md) 문서를 참조하십시오.

## 지원되는 AEM 버전 {#aem-versions}

범용 편집기는 다음에서 지원됩니다.

* AEM as a Cloud Service(릴리스 `2023.8.13099` 이상)
* [AEM 6.5 LTS](https://experienceleague.adobe.com/ko/docs/experience-manager-65-lts/content/implementing/developing/headless/universal-editor/introduction)
   * 온프레미스 및 AMS 호스팅이 모두 지원됩니다.
* [AEM 6.5](https://experienceleague.adobe.com/ko/docs/experience-manager-65/content/implementing/developing/headless/universal-editor/introduction)
   * 온프레미스 및 AMS 호스팅이 모두 지원됩니다.

이 문서는 AEM as a Cloud Service에서 범용 편집기를 사용하는 방법에 대한 설명서입니다.

## 기능 {#features}

범용 편집기는 효율적인 콘텐츠 관리를 위한 광범위한 사용 사례를 지원하는 다양한 기능을 제공합니다.

* **[WYSIWYG](/help/sites-cloud/authoring/universal-editor/authoring.md)**: 일반 텍스트, 리치 텍스트, 미디어 및 메타데이터를 포함한 모든 형태의 웹 콘텐츠에 대해 WYSIWYG(what-you-see-is-what-you-get) 편집을 수행합니다.
* **[구성](/help/sites-cloud/authoring/universal-editor/authoring.md#editing-content)**: 다양한 유형의 콘텐츠 블록(제목, 버튼, 티저, 섹션, 임베드 등)을 만들고, 편집하고, 재정렬하고, 중첩하고, 삭제합니다.
* **[레이아웃](/help/sites-cloud/authoring/universal-editor/templates.md)**: 페이지 템플릿을 활용하고, 시각적 스타일을 적용하고, 열, 캐러셀 및 아코디언과 같은 블록으로 레이아웃을 구성합니다.
* **[디바이스 시뮬레이션](/help/sites-cloud/authoring/universal-editor/navigation.md#emulator)**: 편집하는 동안 다른 방문자 디바이스에 대한 콘텐츠를 미리 보고 최적화합니다.
* **옴니채널**: 여러 채널에서 구조화된 콘텐츠와 비구조화된 콘텐츠를 모두 재사용합니다.
* **[현지화](/help/sites-cloud/authoring/universal-editor/inheritance.md)**: Multi-Site Manager(MSM)를 사용하여 콘텐츠 번역 워크플로를 간소화하고 현지화된 콘텐츠 상속을 효율적으로 처리합니다.
* **일관성**: 브랜드 지침을 준수하고 모든 콘텐츠에서 일관성을 유지합니다.
* **보안**: [액세스 제어를 적용](/help/implementing/universal-editor/authentication.md)하고, 콘텐츠 무결성을 보호하고, [강력한 버전 관리](/help/sites-cloud/authoring/sites-console/page-versions.md)를 통해 변경 사항을 추적합니다.
* **[게시](/help/sites-cloud/authoring/universal-editor/publishing.md)**: 검토, 승인 및 게시 워크플로를 편집기 내에 직접 통합합니다.
* **통합**: [Sites Console,](/help/sites-cloud/authoring/sites-console/introduction.md) [콘텐츠 조각 편집기](/help/sites-cloud/administering/content-fragments/overview.md) 등과 같은 AEM 도구와 완벽하게 통합되어 일관된 작성 경험을 제공합니다.

## 확장성 {#extensibility}

범용 편집기는 기본적으로 매우 유용할 뿐만 아니라 다양한 확장 가능성을 제공합니다.

* **확장 기능**&#x200B;은 워크플로 지원, 베리에이션 생성, 실험 활성화와 같은 요구 사항을 지원하기 위해 다양하게 준비되어 있습니다.
* **확장 가능한 UI**&#x200B;를 사용하면 프로젝트 요구에 맞게 조정할 수 있는 궁극적인 유연성을 제공하는 미리 만들어진 확장 기능이 활용하는 것과 동일한 기본 프레임워크를 사용하여 자체 확장 기능을 만들 수 있습니다.
* 블록, 사용자 정의 데이터 유형 및 이벤트와 같은 **확장 지점**&#x200B;을 통해 UI를 넘어 사용자 정의 비즈니스 요구 사항을 원활하게 통합할 수 있습니다.

>[!TIP]
>
>범용 편집기의 확장성에 대한 자세한 내용은 [범용 편집기 확장](/help/implementing/universal-editor/extending.md) 문서를 참조하십시오.

## 범용 편집기와 콘텐츠 조각 편집기 {#universal-editor-content-fragment-editor}

얼핏 보면 범용 편집기와 콘텐츠 조각 편집기가 유사한 편집 기능을 제공하는 것처럼 보일 수 있습니다. 단, 두 편집기는 서로 매우 다른 기능을 제공하며 마케팅 실무자의 다른 작업을 담당합니다.

### 콘텐츠 조각 편집기 {#content-fragment-editor}

마케팅 실무자가 레이아웃에 신경 쓰지 않고 콘텐츠를 만들어 다양한 경험 컨텍스트에서 재사용할 수 있기를 원합니다.

* 수행해야 할 기본 작업은 콘텐츠 전략을 확장하는 것입니다.

### 범용 편집기 {#universal-editor}

마케팅 실무자가 뛰어난 경험을 제공하기 위해 주어진 컨텍스트의 레이아웃에 맞는 콘텐츠를 만들고자 합니다.

* 수행해야 할 기본 작업은 독자와 설득력 있게 소통하는 것입니다.

## 제한 사항 {#limitations}

범용 편집기를 탐색하고 자체 프로젝트에 구현할 때 다음 제한 사항을 염두에 두어야 합니다.

* 단일 페이지에 대한 계측으로 참조되는 AEM 리소스(콘텐츠 조각, 페이지, 경험 조각, 자산 등)는 25개를 넘지 않아야 합니다.
* AEM as a Cloud Service, [AEM 6.5 LTS](https://experienceleague.adobe.com/ko/docs/experience-manager-65-lts/content/implementing/developing/headless/universal-editor/introduction) 및 [AEM 6.5](https://experienceleague.adobe.com/ko/docs/experience-manager-65/content/implementing/developing/headless/universal-editor/introduction)는 지원되는 유일한 AEM 백엔드입니다.
* AEM as a Cloud Service에는 릴리스 `2023.8.13099` 이상이 필요합니다.
* 콘텐츠 작성자는 자체적인 개별 Experience Cloud 계정이 있어야 합니다.
* AEM의 일부인 범용 편집기는 [AEM과 동일한 데스크탑 브라우저를 지원](/help/overview/supported-platforms.md)합니다.
   * 이러한 브라우저의 모바일 버전은 지원되지 않습니다.

{{ip-allow-lists-ue}}

## 다음 단계 {#next-steps}

범용 편집기의 일반적인 사용 사례에 대해 자세히 알아보고 프로젝트를 지원하기 위한 올바른 설명서 리소스를 찾으려면 [범용 편집기 사용 사례 및 학습 경로](/help/implementing/universal-editor/use-cases.md) 문서를 참조하십시오.
