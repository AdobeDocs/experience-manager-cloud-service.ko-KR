---
title: 페이지 편집기 및 유니버설 편집기
description: 페이지 편집기는 Adobe에서 계속 지원되지만, 범용 편집기는 새로운 프로젝트에 흥미로운 가능성을 제공합니다.
feature: Developing
role: Admin, Architect, Developer
exl-id: 0a13fb52-623e-4aff-b254-186d8d117e4d
source-git-commit: f21e21b0f7239ec9112d65b94b372344c4a07566
workflow-type: tm+mt
source-wordcount: '1065'
ht-degree: 3%

---

# 페이지 편집기 및 유니버설 편집기 {#page-editor-universal-editor}

페이지 편집기는 Adobe에서 계속 지원되지만, 범용 편집기는 새로운 프로젝트에 흥미로운 가능성을 제공합니다.

## 배경 {#background}

Adobe은 최신 Javascript 기반 개발 방식을 수용하는 간소화된 편집기로 2024년에 [범용 편집기](/help/implementing/universal-editor/introduction.md)를 도입했습니다. 범용 편집기는 원활하고 확장 가능한 시각적 컨텐츠 작성 경험을 위한 Adobe의 비전입니다.

[페이지 편집기](/help/sites-cloud/authoring/page-editor/introduction.md)의 풍부한 기능 집합과 AEM의 오랜 역사 동안 여기에 투자하는 수많은 프로젝트를 인식하면서 Adobe은 계속해서 페이지 편집기를 완전히 지원하고 있지만, 혁신은 범용 편집기에 중점을 둘 것입니다.

## 추천 {#recommendation}

빠르게 좁혀지지만 범용 편집기와 페이지 편집기 사이에는 기능 차이가 있습니다([기능 비교는 다음 섹션에서 찾을 수 있음](#feature-comparison)).

경험상:

* **새 프로젝트**&#x200B;은(는) 기본적으로 유니버설 편집기를 활용하는 것입니다.
* **기존 프로젝트**&#x200B;에서는 Edge Delivery 또는 Headless 작업을 시작할 때 페이지 편집기를 계속 사용하고 유니버설 편집기를 고려해야 합니다.

**선택한 편집기는 개별 프로젝트의 요구 사항에 따라 완전히 결정됩니다.**

## 기능 비교 {#feature-comparison}

두 편집기 간의 기능 차이가 지속적으로 줄어들고 있으므로 [범용 편집기의 릴리스 정보](/help/release-notes/universal-editor/current.md)에서 최신 개발 내용을 참조하십시오.

### 제공 {#delivery}

|  | 페이지 편집기 | 메모 | 범용 편집기 | 메모 |
|---|---|---|---|---|
| [클래식 AEM 배달](/help/sites-cloud/authoring/author-publish.md) | [!BADGE 사용 가능]{type=Positive} | 핵심 구성 요소와 함께 사용하는 것이 좋습니다. | [!BADGE 사용할 수 없음]{type=Negative} | 클래식 AEM 페이지는 일반적으로 범용 편집기를 사용하여 있는 그대로 복제하기 어려운 몇 가지 페이지 편집기 관련 기능을 사용합니다. |
| [Edge Delivery](/help/edge/overview.md) | [!BADGE 사용할 수 없음]{type=Negative} |  | [!BADGE 사용 가능]{type=Positive} |  |
| [Headless 게재](/help/headless/introduction.md) | [!BADGE 부분적으로 사용 가능]{type=Caution} | [SPA 편집기,](/help/implementing/developing/hybrid/introduction.md)이(가) 있는 경우에만 [더 이상 사용되지 않음](/help/implementing/developing/hybrid/spa-editor-deprecation.md)(범용 편집기 사용) | [!BADGE 사용 가능]{type=Positive} | 범용 편집기를 사용하면 개발자가 특정 프레임워크 요구 사항이나 구현 제한 없이 고유한 웹 앱을 가져올 수 있습니다. |

### 지속성 {#persistence}

|  | 페이지 편집기 | 메모 | 범용 편집기 | 메모 |
|---|---|---|---|---|
| 페이지 구성 요소 편집 | [!BADGE 사용 가능]{type=Positive} |  | [!BADGE 사용 가능]{type=Positive} |  |
| [콘텐츠 조각](/help/assets/content-fragments/content-fragments.md) 편집 중 | [!BADGE 사용할 수 없음]{type=Negative} |  | [!BADGE 사용 가능]{type=Positive} | 새 조각 삽입 및 재정렬 포함 |

### 기능 {#capabilities}

|  | 페이지 편집기 | 메모 | 범용 편집기 | 메모 |
|---|---|---|---|---|
| 페이지 템플릿 | [!BADGE 사용 가능]{type=Positive} |  | [!BADGE 사용 가능]{type=Positive} | 범용 편집기는 사용된 템플릿 시스템에 대해 불가지론자적 태도를 갖습니다. 그러나 최신 프론트엔드 도구를 사용하면 개발자가 코드에서 직접 템플릿 논리를 정의하고 유지할 수 있으므로 일반적인 구현 패턴은 개발자가 정의한 템플릿을 선호합니다. |
| WYSIWYG 편집 | [!BADGE 사용 가능]{type=Positive} | 페이지로 제한 | [!BADGE 사용 가능]{type=Positive} | 지원 페이지 및 컨텐츠 조각 |
| [변형 생성](/help/generative-ai/generate-variations.md) | [!BADGE 사용할 수 없음]{type=Negative} |  | [!BADGE 사용 가능]{type=Positive} | [확장으로 사용 가능](/help/implementing/universal-editor/extending.md) |
| 새 블록 삽입 | [!BADGE 사용 가능]{type=Positive} |  | [!BADGE 사용 가능]{type=Positive} |  |
| 블록 재정렬 | [!BADGE 사용 가능]{type=Positive} | 컨텍스트 내 드래그 앤 드롭을 사용할 수 있지만 &quot;트리 보기&quot; 사이드 패널에서는 사용할 수 없음 | [!BADGE 사용 가능]{type=Positive} | &quot;트리 보기&quot; 사이드 패널의 드래그 앤 드롭을 통해 가능하지만 아직 컨텍스트(계획됨)에 있지 않습니다. |
| 블록 잘라내기/복사-붙여넣기 | [!BADGE 사용 가능]{type=Positive} |  | [!BADGE 사용할 수 없음]{type=Negative} | 계획됨 |
| 스타일 적용 | [!BADGE 사용 가능]{type=Positive} | [스타일 시스템을 사용하여 구성 요소에 스타일을 적용할 수 있습니다.](/help/sites-cloud/authoring/page-editor/style-system.md) | [!BADGE 사용 가능]{type=Positive} | 일반 구성 요소(또는 콘텐츠 조각) 속성을 사용하여 스타일을 적용할 수 있습니다. 범용 편집기에서는 동일한 스타일 선택기를 사용할 수 없지만 다중 선택 위젯을 사용하면 매우 유사한 UX를 수행할 수 있습니다. |
| 레이아웃 적용 | [!BADGE 사용 가능]{type=Positive} | Sites에서 작성자가 미리 정의된 세 개의 중단점에서 구성 요소의 크기를 조정할 수 있도록 [AEM 반응형 그리드](/help/implementing/developing/introduction/responsive-design.md)를 구현해야 합니다. | [!BADGE 사용 가능]{type=Positive} | 일반 구성 요소(또는 콘텐츠 조각) 속성을 사용하여 레이아웃을 적용할 수 있지만 반응형 그리드는 지원되지 않습니다. |
| 실행 취소-다시 실행 | [!BADGE 사용 가능]{type=Positive} |  | [!BADGE 사용할 수 없음]{type=Negative} | 계획됨 |
| 게시(미리보기에도) | [!BADGE 사용 가능]{type=Positive} |  | [!BADGE 사용 가능]{type=Positive} |  |
| [워크플로 시작](/help/sites-cloud/authoring/workflows/overview.md) | [!BADGE 사용 가능]{type=Positive} |  | [!BADGE 사용 가능]{type=Positive} | 확장 기능으로 사용 가능 |
| 댓글 달기 | [!BADGE 사용 가능]{type=Positive} | [주석](/help/sites-cloud/authoring/page-editor/annotations.md) 사용 중 | [!BADGE 사용할 수 없음]{type=Negative} | 계획됨 |
| Workfront 통합 | [!BADGE 사용할 수 없음]{type=Negative} |  | [!BADGE 사용 가능]{type=Positive} | 확장 기능으로 사용 가능 |
| [MSM 및 시작](/help/sites-cloud/administering/msm-and-translation.md) | [!BADGE 사용 가능]{type=Positive} |  | [!BADGE 사용 가능]{type=Positive} | 확장 기능으로 페이지에 사용 가능 |
| 실험 및 개인화 | [!BADGE 사용 가능]{type=Positive} | [대상 모드](/help/sites-cloud/authoring/personalization/targeted-content.md) 사용 중 | [!BADGE 사용 가능]{type=Positive} | Edge Delivery Services의 확장으로 사용 가능 |
| 콘텐츠 트리 | [!BADGE 사용 가능]{type=Positive} |  | [!BADGE 사용 가능]{type=Positive} | 트리 내에서 순서를 변경할 수도 있습니다. |
| 기기 시뮬레이션 | [!BADGE 사용 가능]{type=Positive} | [구성된 장치를 시뮬레이션할 수 있지만](/help/sites-cloud/administering/responsive-layout.md) 사용자는 시뮬레이션할 다른 화면 차원을 수동으로 입력할 수 없습니다. | [!BADGE 사용 가능]{type=Positive} | [시뮬레이션할 모든 화면 차원을 수동으로 입력할 수 있습니다.](/help/sites-cloud/authoring/universal-editor/navigation.md#emulator) 그러나 기본 중단점을 구성할 수 없습니다. |
| [페이지 잠금](/help/sites-cloud/authoring/sites-console/managing-pages.md) | [!BADGE 사용 가능]{type=Positive} |  | [!BADGE 사용 가능]{type=Positive} | 편집기에서 페이지를 잠금/잠금 해제할 수 있는 확장자를 사용하여 사이트 콘솔에 설정된 잠금 상태를 유지합니다. |
| [페이지 속성](/help/sites-cloud/authoring/sites-console/page-properties.md) | [!BADGE 사용 가능]{type=Positive} |  | [!BADGE 사용 가능]{type=Positive} | 편집기에서 페이지 속성에 액세스할 수 있는 확장 기능을 사이트 관리자로부터 받을 수 있습니다 |
| 다중 필드 속성 | [!BADGE 사용 가능]{type=Positive} |  | [!BADGE 사용할 수 없음]{type=Negative} | 계획됨 |
| [원격 DAM](/help/assets/dynamic-media-open-apis-overview.md) | [!BADGE 사용 가능]{type=Positive} |  | [!BADGE 사용 가능]{type=Positive} |  |
| [페이지 버전 관리](/help/sites-cloud/authoring/sites-console/page-versions.md) | [!BADGE 사용 가능]{type=Positive} |  | [!BADGE 사용 가능]{type=Positive} |  |
| [TimeWarp](/help/sites-cloud/authoring/sites-console/page-versions.md#timewarp) 및 [비교 보기](/help/sites-cloud/authoring/sites-console/page-diff.md) | [!BADGE 사용 가능]{type=Positive} |  | [!BADGE 사용할 수 없음]{type=Negative} | 계획됨 |
| 관리자 화면에서 보기 | [!BADGE 사용 가능]{type=Positive} |  | [!BADGE 사용 가능]{type=Positive} | 페이지 확장으로 사용 가능 |
| 페이지 상태 보기 | [!BADGE 사용 가능]{type=Positive} |  | [!BADGE 사용할 수 없음]{type=Negative} | 사이트 콘솔에서 사용 가능 |
| 확장성 | [!BADGE 사용 가능]{type=Positive} | AEM 오버레이 | [!BADGE 사용 가능]{type=Positive} | App Builder 및 극히 일부 AEM 관련 지식을 사용하여 명확하게 정의된 확장 지점입니다 |

## 범용 편집기 채택 {#adopt-ue}

유니버설 편집기는 많은 이점을 제공하므로 새로운 프로젝트에 적합한 솔루션입니다.

* **시각적 편집:** 페이지 편집기와 마찬가지로 작성자가 미리 보기 내에서 직접 콘텐츠를 편집하여 변경 내용이 방문자 경험에 미치는 영향을 즉시 확인할 수 있습니다.
* **향후 교정:** AEM의 로드맵은 비주얼 편집기로 유니버설 편집기의 우선 순위를 지정합니다. 이를 채택하면 최신 혁신 및 향상된 기능에 액세스할 수 있습니다.
* **간단한 통합:** 범용 편집기를 사용하는 데 AEM 관련 SDK이 필요하지 않으므로 기술 스택 잠금이 줄어듭니다.
* **나만의 앱 만들기:** 유니버설 편집기는 모든 웹 프레임워크나 아키텍처를 지원하므로 복잡한 리팩터링을 수행하지 않아도 됩니다.
* **확장성:** 유니버설 편집기는 GenAI, Workfront 등과의 통합을 포함하여 강력한 [확장 프레임워크,](/help/implementing/universal-editor/extending.md)의 이점을 제공합니다.

### 범용 편집기로 마이그레이션 {#migrate-ue}

페이지 편집기에서 범용 편집기로의 직접 마이그레이션 경로는 없습니다. 이는 두 기술의 근본적인 차이에서 기인한다.

* 범용 편집기는 템플릿 편집기, 스타일 시스템 또는 반응형 그리드 같은 기능을 다시 도입하지 않습니다.
   * 이제 Edge Delivery Services 또는 Headless 프로젝트에서 린 프론트엔드 CSS 및 Javascript를 사용하여 이러한 사용 사례를 보다 효율적으로 처리할 수 있습니다.
* 범용 편집기는 Editor-as-a-Service이므로 구현자가 CSS 또는 JS를 구성 요소 대화 상자에 삽입하도록 할 수 없습니다.
   * 이렇게 하면 페이지 편집기에서 구성 요소 대화 상자가 자동으로 변환되지 않습니다.
   * 이 기능은 사용자 정의 위젯, 필드 유효성 검사, 규칙 표시/숨기기 및 템플릿 기반 사용자 지정과 같은 대화 상자의 많은 영역에 영향을 줍니다.
      * 이러한 기능은 계속 사용할 수 있지만, 대화 상자에 배포된 사용자 지정 JavaScript 대신 범용 편집기가 구성을 통해 이러한 기능을 해결합니다.

범용 편집기는 클래식 AEM 페이지(예: 핵심 구성 요소로 빌드)에 대한 편집을 기술적으로 활성화할 수 있지만, 이러한 사이트는 일반적으로 대화 상자 내의 스타일 시스템, 반응형 그리드, 편집 가능한 템플릿 및 사용자 지정 Javascript와 같은 여러 페이지 편집기 관련 기능을 사용합니다.

범용 편집기는 이러한 레거시 기능을 지원하지 않는 보다 간소화된 최신 접근 방식을 따르므로 이러한 사이트를 마이그레이션하려면 상당한 리팩터링이 필요합니다. 따라서 **Edge Delivery Services으로 전환하는 프로젝트에만 페이지 편집기 사이트를 유니버설 편집기로 마이그레이션하는 것이 좋습니다.**
