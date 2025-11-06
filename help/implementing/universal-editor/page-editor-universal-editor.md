---
title: 페이지 편집기 및 범용 편집기
description: 페이지 편집기는 Adobe에서 계속 지원되지만, 범용 편집기는 새로운 프로젝트에 흥미로운 가능성을 제공합니다.
feature: Developing
role: Admin, Developer
exl-id: 0a13fb52-623e-4aff-b254-186d8d117e4d
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '1067'
ht-degree: 100%

---

# 페이지 편집기 및 범용 편집기 {#page-editor-universal-editor}

페이지 편집기는 Adobe에서 계속 지원되지만, 범용 편집기는 새로운 프로젝트에 흥미로운 가능성을 제공합니다.

## 배경 {#background}

Adobe는 2024년에 현대적인 JavaScript 기반 개발 접근 방식을 도입한 능률적인 편집기인 [범용 편집기](/help/implementing/universal-editor/introduction.md)를 도입했습니다. 범용 편집기는 원활하고 확장 가능한 시각적 콘텐츠 작성 경험을 제공하기 위한 Adobe의 비전입니다.

[페이지 편집기](/help/sites-cloud/authoring/page-editor/introduction.md)의 풍부한 기능 세트와 오랜 AEM 역사에 걸쳐 페이지 편집기에 투자하는 수많은 프로젝트를 인식하여 Adobe는 페이지 편집기를 계속해서 완전히 지원하지만, 혁신은 범용 편집기에 집중될 것입니다.

## 추천 {#recommendation}

빠르게 격차가 좁혀지고 있지만, 범용 편집기와 페이지 편집기 간에는 여전히 기능 격차가 남아 있습니다([기능 비교는 다음 섹션에서 확인할 수 있습니다](#feature-comparison)).

경험을 바탕으로 한 일반적인 권장 사항은 다음과 같습니다.

* **새 프로젝트**&#x200B;는 기본적으로 범용 편집기를 활용해야 합니다.
* **기존 프로젝트**&#x200B;는 페이지 편집기를 계속 사용하고 Edge Delivery 또는 Headless efforts을 시작할 때 범용 편집기를 고려해야 합니다.

**선택하는 편집기는 전적으로 개별 프로젝트의 필요에 따라 결정되어야 합니다.**

## 기능 비교 {#feature-comparison}

두 편집기 간의 기능 격차는 지속적으로 줄어들고 있으므로 최신 개발 사항은 [범용 편집기의 릴리스 정보](/help/release-notes/universal-editor/current.md)를 참조하십시오.

### 게재 {#delivery}

|  | 페이지 편집기 | 메모 | 범용 편집기 | 메모 |
|---|---|---|---|---|
| [게재 게시](/help/sites-cloud/authoring/author-publish.md) | [!BADGE 사용 가능]{type=Positive} | 핵심 구성 요소 및 기존 AEM 프로젝트와 함께 사용하는 것이 좋습니다. | [!BADGE 사용할 수 없음]{type=Negative} | 기존 AEM 페이지는 일반적으로 범용 편집기에서 그대로 복제하기 어려운 페이지 편집기의 특정 기능에 의존합니다. |
| [Edge Delivery](/help/edge/overview.md) | [!BADGE 사용할 수 없음]{type=Negative} |  | [!BADGE 사용 가능]{type=Positive} |  |
| [Headless 게재](/help/headless/introduction.md) | [!BADGE 부분적으로 사용 가능]{type=Caution} | [SPA 편집기](/help/implementing/developing/hybrid/introduction.md)를 통해서만 가능하며, 이 편집기는 범용 편집기를 위해 [더 이상 사용되지 않습니다](/help/implementing/developing/hybrid/spa-editor-deprecation.md). | [!BADGE 사용 가능]{type=Positive} | 범용 편집기를 사용하면 개발자가 특정 프레임워크 요구 사항 또는 구현 제약을 부과하지 않고도 자체 웹 앱을 가져올 수 있습니다. |

### 지속성 {#persistence}

|  | 페이지 편집기 | 메모 | 범용 편집기 | 메모 |
|---|---|---|---|---|
| 페이지 구성 요소 편집 | [!BADGE 사용 가능]{type=Positive} |  | [!BADGE 사용 가능]{type=Positive} |  |
| [콘텐츠 조각](/help/assets/content-fragments/content-fragments.md) 편집 | [!BADGE 사용할 수 없음]{type=Negative} |  | [!BADGE 사용 가능]{type=Positive} | 새 조각 삽입 및 재정렬 포함 |

### 기능 {#capabilities}

|  | 페이지 편집기 | 메모 | 범용 편집기 | 메모 |
|---|---|---|---|---|
| 페이지 템플릿 | [!BADGE 사용 가능]{type=Positive} |  | [!BADGE 사용 가능]{type=Positive} | 범용 편집기는 사용되는 템플릿 시스템과 무관합니다. 그러나 최신 프론트엔드 도구를 사용하면 개발자가 코드에서 직접 템플릿 논리를 정의하고 유지 관리하기가 훨씬 쉬워지므로 일반적인 구현 패턴에 대해서 개발자가 정의한 템플릿이 선호됩니다. |
| WYSIWYG 편집 | [!BADGE 사용 가능]{type=Positive} | 페이지로 제한됨 | [!BADGE 사용 가능]{type=Positive} | 페이지 및 콘텐츠 조각 지원 |
| [베리에이션 생성](/help/generative-ai/generate-variations.md) | [!BADGE 사용할 수 없음]{type=Negative} |  | [!BADGE 사용 가능]{type=Positive} | [확장 기능으로 사용 가능](/help/implementing/universal-editor/extending.md) |
| 새로운 블록 삽입 | [!BADGE 사용 가능]{type=Positive} |  | [!BADGE 사용 가능]{type=Positive} |  |
| 블록 재정렬 | [!BADGE 사용 가능]{type=Positive} | 컨텍스트 내에서 드래그 앤 드롭이 가능하지만 “트리 보기” 사이드 패널에서는 불가능합니다. | [!BADGE 사용 가능]{type=Positive} | “트리 보기” 사이드 패널의 드래그 앤 드롭을 통해 가능하지만 아직 컨텍스트 내에서는 불가능합니다(지원 예정). |
| 블록 잘라내기/복사-붙여넣기 | [!BADGE 사용 가능]{type=Positive} |  | [!BADGE 사용 가능]{type=Positive} |  |
| 스타일 적용 | [!BADGE 사용 가능]{type=Positive} | [스타일 시스템](/help/sites-cloud/authoring/page-editor/style-system.md)을 사용하여 구성 요소에 스타일을 적용할 수 있습니다. | [!BADGE 사용 가능]{type=Positive} | 일반 구성 요소(또는 콘텐츠 조각) 속성을 사용하여 스타일을 적용할 수 있습니다. 범용 편집기에서는 동일한 스타일 선택기를 사용할 수 없지만 다중 선택 위젯을 사용하면 매우 유사한 UX를 구현할 수 있습니다. |
| 레이아웃 적용 | [!BADGE 사용 가능]{type=Positive} | 작성자가 세 가지 미리 정의된 중단점에서 구성 요소 크기를 조정할 수 있도록 하려면 사이트에서 [AEM 반응형 격자](/help/implementing/developing/introduction/responsive-design.md)를 구현해야 합니다. | [!BADGE 사용 가능]{type=Positive} | 일반 구성 요소(또는 콘텐츠 조각) 속성을 사용하여 레이아웃을 적용할 수 있지만 반응형 격자는 지원되지 않습니다. |
| 실행 취소-다시 실행 | [!BADGE 사용 가능]{type=Positive} |  | [!BADGE 사용 가능]{type=Positive} |  |
| 게시(미리보기 포함) | [!BADGE 사용 가능]{type=Positive} |  | [!BADGE 사용 가능]{type=Positive} |  |
| [워크플로 시작](/help/sites-cloud/authoring/workflows/overview.md) | [!BADGE 사용 가능]{type=Positive} |  | [!BADGE 사용 가능]{type=Positive} | 확장 기능으로 사용 가능 |
| 댓글 달기 | [!BADGE 사용 가능]{type=Positive} | [주석](/help/sites-cloud/authoring/page-editor/annotations.md) 사용 | [!BADGE 사용할 수 없음]{type=Negative} | 계획됨 |
| Workfront 통합 | [!BADGE 사용할 수 없음]{type=Negative} |  | [!BADGE 사용 가능]{type=Positive} | 확장 기능으로 사용 가능 |
| [MSM 및 시작](/help/sites-cloud/administering/msm-and-translation.md) | [!BADGE 사용 가능]{type=Positive} |  | [!BADGE 사용 가능]{type=Positive} | 확장 기능으로 페이지에 사용 가능 |
| 실험 및 개인화 | [!BADGE 사용 가능]{type=Positive} | [타깃 모드](/help/sites-cloud/authoring/personalization/targeted-content.md) 사용 | [!BADGE 사용 가능]{type=Positive} | Edge Delivery Services용 확장 기능으로 사용 가능 |
| 콘텐츠 트리 | [!BADGE 사용 가능]{type=Positive} |  | [!BADGE 사용 가능]{type=Positive} | 트리 내에서 재정렬도 허용됩니다. |
| 디바이스 시뮬레이션 | [!BADGE 사용 가능]{type=Positive} | [구성된 디바이스를 시뮬레이션할 수 있지만,](/help/sites-cloud/administering/responsive-layout.md) 사용자가 시뮬레이션할 다른 화면 치수를 수동으로 입력할 수는 없습니다. | [!BADGE 사용 가능]{type=Positive} | [시뮬레이션할 화면 치수는 수동으로 입력할 수 있지만](/help/sites-cloud/authoring/universal-editor/navigation.md#emulator) 기본 중단점은 구성할 수 없습니다. |
| [페이지 잠금](/help/sites-cloud/authoring/sites-console/managing-pages.md) | [!BADGE 사용 가능]{type=Positive} |  | [!BADGE 사용 가능]{type=Positive} | Sites Console에서 설정된 잠금 상태를 준수하며 편집기에서 페이지를 잠그거나 잠금 해제하는 확장 기능을 사용할 수 있습니다. |
| [페이지 속성](/help/sites-cloud/authoring/sites-console/edit-page-properties.md) | [!BADGE 사용 가능]{type=Positive} |  | [!BADGE 사용 가능]{type=Positive} | 사이트 관리자에서 사용할 수 있으며, 확장 기능을 사용하여 편집기에서 페이지 속성에도 액세스할 수 있습니다. |
| 다중 필드 속성 | [!BADGE 사용 가능]{type=Positive} |  | [!BADGE 사용할 수 없음]{type=Negative} | 계획됨 |
| [원격 DAM](/help/assets/dynamic-media-open-apis-overview.md) | [!BADGE 사용 가능]{type=Positive} |  | [!BADGE 사용 가능]{type=Positive} |  |
| [페이지 버전 관리](/help/sites-cloud/authoring/sites-console/page-versions.md) | [!BADGE 사용 가능]{type=Positive} |  | [!BADGE 사용 가능]{type=Positive} |  |
| [타임워프](/help/sites-cloud/authoring/sites-console/page-versions.md#timewarp) 및 [차이점 보기](/help/sites-cloud/authoring/sites-console/page-diff.md) | [!BADGE 사용 가능]{type=Positive} |  | [!BADGE 사용할 수 없음]{type=Negative} | 계획됨 |
| 관리자로 보기 | [!BADGE 사용 가능]{type=Positive} |  | [!BADGE 사용 가능]{type=Positive} | 확장 기능으로 페이지에 사용 가능 |
| 페이지 상태 보기 | [!BADGE 사용 가능]{type=Positive} |  | [!BADGE 사용할 수 없음]{type=Negative} | Sites 콘솔에서 사용 가능 |
| 확장성 | [!BADGE 사용 가능]{type=Positive} | AEM 오버레이로 | [!BADGE 사용 가능]{type=Positive} | App Builder를 사용하여 명확하게 정의된 확장 지점과 AEM에 대한 매우 적은 지식 |

## 범용 편집기 채택 {#adopt-ue}

범용 편집기는 많은 이점을 제공하므로 새 프로젝트에 적합한 솔루션입니다.

* **시각적 편집:** 페이지 편집기와 마찬가지로 작성자는 미리보기 내에서 직접 콘텐츠를 편집하고 변경 내용이 방문자 경험에 어떤 영향을 미치는지 즉시 확인할 수 있습니다.
* **미래 지향적:** AEM의 로드맵은 범용 편집기를 시각적 편집기로 우선시합니다. 이를 채택하면 최신 혁신 및 향상된 기능에 액세스할 수 있습니다.
* **더욱 간편한 통합:** 범용 편집기를 사용하기 위해 AEM 관련 SDK가 필요하지 않으므로 기술 스택 종속성이 줄어듭니다.
* **자체 앱 가져오기:** 범용 편집기는 모든 웹 프레임워크 또는 아키텍처를 지원하므로 복잡한 리팩토링 없이도 채택할 수 있습니다.
* **확장성:** 범용 편집기는 GenAI, Workfront 등과의 통합을 포함하여 강력한 [확장 프레임워크](/help/implementing/universal-editor/extending.md)의 이점을 누릴 수 있습니다.

### 범용 편집기로 마이그레이션 {#migrate-ue}

페이지 편집기에서 범용 편집기로 직접 마이그레이션하는 경로는 없습니다. 이는 두 기술의 근본적인 차이 때문입니다.

* 범용 편집기는 템플릿 편집기, 스타일 시스템 또는 반응형 격자와 같은 기능을 다시 도입하지 않습니다.
   * 이러한 사용 사례는 이제 Edge Delivery Services 또는 Headless 프로젝트의 간단한 프론트엔드 CSS 및 JavaScript로 더 효율적으로 처리할 수 있습니다.
* 범용 편집기는 서비스형 편집기이므로 구현자가 구성 요소 대화 상자에 CSS 또는 JS를 주입할 수 없습니다.
   * 이렇게 하면 페이지 편집기에서 구성 요소 대화 상자가 자동으로 변환되는 것을 방지합니다.
   * 이는 사용자 정의 위젯, 필드 유효성 검사, 표시/숨기기 규칙 및 템플릿 기반 사용자 정의와 같은 대화 상자의 여러 영역에 영향을 미칩니다.
      * 이러한 기능은 여전히 가능하지만, 범용 편집기는 대화 상자에 배포된 사용자 정의 JavaScript 대신 구성을 통해 이 문제를 해결합니다.

범용 편집기는 기술적으로 기존 AEM 프로젝트(예: 핵심 구성 요소로 빌드된 프로젝트)에 대한 페이지 편집을 활성화할 수 있지만, 이러한 사이트는 일반적으로 스타일 시스템, 반응형 격자, 편집 가능한 템플릿 및 대화 상자 내의 사용자 정의 JavaScript와 같은 여러 페이지 편집기 특정 기능에 의존합니다.

범용 편집기는 이러한 레거시 기능을 지원하지 않는 보다 간소화된 최신 접근 방식을 따르므로 이러한 사이트를 마이그레이션하려면 상당한 리팩토링이 필요합니다. 이러한 이유로 **페이지 편집기 사이트를 범용 편집기로 마이그레이션하는 것은 Edge Delivery Services로 전환하는 프로젝트에만 권장됩니다.**
