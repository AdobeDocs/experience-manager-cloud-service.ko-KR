---
title: 구성 요소 참조 안내서
description: 구성 요소 및 해당 구조에 대한 세부 사항에 대한 개발자 참조 안내서
exl-id: 45e5265b-39d6-4a5c-be1a-e66bb7ea387d
source-git-commit: 5ad33f0173afd68d8868b088ff5e20fc9f58ad5a
workflow-type: tm+mt
source-wordcount: '3648'
ht-degree: 2%

---

# 구성 요소 참조 안내서 {#components-reference-guide}

구성 요소는 AEM에서 경험을 구축하는 핵심입니다. 다음 [핵심 구성 요소](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html) 및 [AEM Project Archetype](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html) 준비된 강력한 구성 요소 도구 세트를 간단하게 시작할 수 있습니다. 다음 [WKND 자습서](/help/implementing/developing/introduction/develop-wknd-tutorial.md) 개발자는 이러한 도구를 사용하는 방법과 사용자 지정 구성 요소를 빌드하여 AEM 사이트를 만드는 방법을 안내합니다.

>[!TIP]
>
>이 문서를 참조하기 전에 다음을 완료했는지 확인하십시오. [WKND 자습서](/help/implementing/developing/introduction/develop-wknd-tutorial.md) 따라서 다음 내용에 익숙합니다. [핵심 구성 요소](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html) 및 [AEM Project Archetype](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html)

WKND 튜토리얼은 대부분의 사용 사례를 다루므로, 이 문서는 이러한 리소스를 보완하기 위한 목적으로만 제공됩니다. 시작 안내서는 구성 요소가 AEM에서 구성되고 구성되는 방식에 대한 기술적인 세부 사항을 심층적으로 설명합니다.

## 개요 {#overview}

이 섹션에서는 구성 요소를 개발할 때 필요한 세부 사항을 소개하는 주요 개념과 문제를 다룹니다.

### 계획 {#planning}

구성 요소를 실제로 구성하거나 코딩하기 전에 다음 사항을 문의해야 합니다.

* 새 구성 요소를 사용하려면 정확히 어떤 작업이 필요합니까?
* 구성 요소를 처음부터 만들어야 합니까? 또는 기존 구성 요소에서 기본 사항을 상속할 수 있습니까?
* 콘텐츠를 선택/조작하기 위해 구성 요소에 논리가 필요합니까?
   * 논리는 사용자 인터페이스 레이어와 별도로 유지되어야 합니다. HTL은 이러한 일이 발생하는지 확인할 수 있도록 설계되었습니다.
* 구성 요소에 CSS 서식이 필요합니까?
   * CSS 서식은 구성 요소 정의와 별도로 유지해야 합니다. 외부 CSS 파일을 통해 수정할 수 있도록 HTML 요소의 이름을 지정하는 규칙을 정의합니다.
* 새 구성 요소에 도입될 수 있는 보안은 무엇입니까?

### 기존 구성 요소 재사용 {#reusing-components}

완전히 새로운 구성 요소를 만드는 데 시간을 투자하기 전에 기존 구성 요소를 사용자 정의하거나 확장하는 것이 좋습니다. [핵심 구성 요소](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html) 는 유연하고 강력하며 테스트를 마친 프로덕션 준비 구성 요소 제품군을 제공합니다.

#### 코어 구성 요소 확장 {#extending-core-components}

핵심 구성 요소는 [사용자 정의 패턴 지우기](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/customizing.html) 를 사용하여 프로젝트를 자체 프로젝트의 요구 사항에 맞게 조정할 수 있습니다.

#### 구성 요소 오버레이 {#overlying-components}

구성 요소는 를 사용하여 재정의할 수도 있습니다. [오버레이](/help/implementing/developing/introduction/overlays.md) 검색 경로 논리를 기반으로 합니다. 그러나 이러한 경우 [Sling 리소스 병합](/help/implementing/developing/introduction/sling-resource-merger.md) 은(는) 트리거되지 않으며 `/apps` 전체 오버레이를 정의해야 합니다.

#### 구성 요소 대화 상자 확장 {#extending-component-dialogs}

Sling 리소스 병합을 사용하고 속성을 정의하는 구성 요소 대화 상자를 재정의할 수도 있습니다 `sling:resourceSuperType`.

즉, 전체 대화상자를 다시 정의하는 것이 아니라 필요한 차이점만 재정의하면 됩니다.

### 컨텐츠 논리 및 렌더링 마크업  {#content-logic-and-rendering-markup}

구성 요소가 [HTML](https://www.w3schools.com/htmL/html_intro.asp). 구성 요소는 작성자와 게시 환경 모두에서 필요한 콘텐츠를 가져온 다음 필요에 따라 렌더링하는 데 필요한 HTML을 정의해야 합니다.

마크업 및 렌더링을 담당하는 코드는 구성 요소의 콘텐츠를 선택하는 데 사용되는 논리를 제어하는 코드와 별도로 유지하는 것이 좋습니다.

이 철학은 다음을 통해 지원됩니다. [HTL](https://experienceleague.adobe.com/docs/experience-manager-htl/content/overview.html)는 기본 비즈니스 논리를 정의하는 데 실제 프로그래밍 언어를 사용하도록 의도적으로 제한된 템플릿 언어입니다. 이 메커니즘은 주어진 뷰에 대해 호출되는 코드를 강조 표시하고, 필요한 경우 동일한 구성 요소의 다른 뷰에 대해 특정 논리를 허용합니다.

이 (선택 사항) 논리는 다양한 방식으로 구현할 수 있으며 특정 명령으로 HTL에서 호출됩니다.

* Java 사용 - [HTL Java Use-API](https://experienceleague.adobe.com/docs/experience-manager-htl/content/java-use-api.html) htl 파일이 사용자 지정 Java 클래스의 도우미 메서드에 액세스할 수 있도록 합니다. 이렇게 하면 Java 코드를 사용하여 구성 요소 콘텐츠를 선택하고 구성하기 위한 논리를 구현할 수 있습니다.
* JavaScript 사용 - [HTL JavaScript Use-API](https://experienceleague.adobe.com/docs/experience-manager-htl/using/htl/use-api-javascript.html) htl 파일이 JavaScript로 작성된 도우미 코드에 액세스할 수 있도록 합니다. 이렇게 하면 JavaScript 코드를 사용하여 구성 요소 콘텐츠를 선택하고 구성하는 논리를 구현할 수 있습니다.
* 클라이언트측 라이브러리 사용 - 최신 웹 사이트는 복잡한 JavaScript 및 CSS 코드로 구동되는 클라이언트측 처리에 크게 의존합니다. 문서 보기 [AEM에서 클라이언트측 라이브러리 as a Cloud Service 사용](/help/implementing/developing/introduction/clientlibs.md) 추가 정보.

## 구성 요소 구조 {#structure}

AEM 구성 요소의 구조는 강력하고 유연합니다. 주요 부분은 다음과 같습니다.

* [리소스 유형](#resource-type)
* [구성 요소 정의](#component-definition)
* [구성 요소의 속성 및 하위 노드](#properties-and-child-nodes-of-a-component)
* [대화 상자](#dialogs)
* [디자인 대화 상자](#design-dialogs)

### 리소스 유형 {#resource-type}

구조의 주요 요소는 리소스 유형입니다.

* 콘텐츠 구조는 의도를 선언합니다.
* 리소스 유형은 이를 구현합니다.

이는 시간이 지남에 따라 외모와 느낌이 변하는 경우에도 의도가 시간에 머물러 있도록 하는 데 도움이 되는 추상화이다.

### 구성 요소 정의 {#component-definition}

컴포넌트의 정의는 다음과 같이 나눌 수 있습니다.

* AEM 구성 요소는 [슬링](https://sling.apache.org/documentation.html)
* AEM 구성 요소는 아래에 있습니다. `/libs/core/wcm/components`.
* 프로젝트/사이트별 구성 요소는 `/apps/<myApp>/components`.
* AEM 표준 구성 요소는 다음과 같이 정의됩니다. `cq:Component` 및 에는 다음과 같은 주요 요소가 있습니다.
   * jcr 속성 - jcr 속성 목록입니다. 이러한 속성은 변수이며 일부는 구성 요소 노드의 기본 구조, 속성 및 하위 노드가 `cq:Component` 정의.
   * 리소스 - 구성 요소에서 사용하는 정적 요소를 정의합니다.
   * 스크립트 - 구성 요소의 결과 인스턴스 동작을 구현하는 데 사용됩니다.

#### 중요한 속성 {#vital-properties}

* **루트 노드**:
   * `<mycomponent> (cq:Component)` - 구성 요소의 계층 노드
* **중요한 속성**:
   * `jcr:title` - 구성 요소 제목: 예를 들어 구성 요소가 [구성 요소 브라우저](/help/sites-cloud/authoring/fundamentals/environment-tools.md#components-browser) 및 [구성 요소 콘솔](/help/sites-cloud/authoring/features/components-console.md)
   * `jcr:description` - 구성 요소에 대한 설명. 구성 요소 브라우저 및 구성 요소 콘솔에서 마우스 오버 힌트로 사용됩니다.
   * 섹션 보기 [구성 요소 아이콘](#component-icon) (세부 사항)
* **중요한 하위 노드**:
   * `cq:editConfig (cq:EditConfig)` - 구성 요소의 편집 속성을 정의하고 구성 요소를 구성 요소 브라우저에 표시할 수 있습니다.
      * 구성 요소에 대화 상자가 있으면 cq:editConfig가 없어도 구성 요소 브라우저 또는 Sidekick에 자동으로 표시됩니다.
   * `cq:childEditConfig (cq:EditConfig)` - 자체 구성 요소를 정의하지 않는 하위 구성 요소에 대한 작성자 UI 측면을 제어합니다. `cq:editConfig`.
   * `cq:dialog (nt:unstructured)` - 이 구성 요소에 대한 대화 상자 사용자가 구성 요소를 구성 및/또는 콘텐츠를 편집할 수 있는 인터페이스를 정의합니다.
   * `cq:design_dialog (nt:unstructured)` - 이 구성 요소의 디자인 편집

#### 구성 요소 아이콘 {#component-icon}

구성 요소의 아이콘 또는 약어는 개발자가 구성 요소를 만들 때 구성 요소의 JCR 속성을 통해 정의됩니다. 이러한 속성은 다음 순서로 평가되며 발견된 첫 번째 유효한 속성이 사용됩니다.

1. `cq:icon` - 의 표준 아이콘을 가리키는 문자열 속성 [Coral UI 라이브러리](https://opensource.adobe.com/coral-spectrum/examples/#icon) 구성 요소 브라우저에 표시하려면
   * Coral 아이콘의 HTML 속성 값을 사용합니다.
1. `abbreviation` - 구성 요소 브라우저에서 구성 요소 이름의 약어를 사용자 지정하는 문자열 속성
   * 약어는 두 문자로 제한해야 합니다.
   * 빈 문자열을 제공하면 의 처음 두 문자에서 약어가 만들어집니다. `jcr:title` 속성.
      * 예: &quot;Image&quot;의 &quot;Im&quot;
      * 지역화된 제목은 약어를 작성하는 데 사용됩니다.
   * 구성 요소에 다음이 있는 경우에만 약어가 번역됩니다. `abbreviation_commentI18n` 속성. 그런 다음 번역 힌트로 사용됩니다.
1. `cq:icon.png` 또는 `cq:icon.svg` - 구성 요소 브라우저에 표시되는 이 구성 요소의 아이콘
   * 20 x 20 픽셀은 표준 구성 요소의 아이콘 크기입니다.
      * 더 큰 아이콘은 크기가 줄어듭니다(클라이언트측).
   * 권장 색상은 rgb(112, 112, 112) > #707070입니다.
   * 표준 구성 요소 아이콘의 배경은 투명합니다.
   * 전용 `.png` 및 `.svg` 파일이 지원됩니다.
   * Eclipse 플러그인을 통해 파일 시스템에서 가져오는 경우 파일 이름을 로 이스케이프해야 합니다. `_cq_icon.png` 또는 `_cq_icon.svg` 예.
   * `.png` 선례를 이어받습니다. `.svg` 둘 다 있는 경우

위의 속성 중 어느 것도 없는 경우(`cq:icon`, `abbreviation`, `cq:icon.png` 또는 `cq:icon.svg`)을 구성 요소에서 찾을 수 있습니다.

* 시스템은 다음에 나오는 상위 구성 요소에서 동일한 속성을 검색합니다. `sling:resourceSuperType` 속성.
* 수퍼 컴포넌트 레벨에서 아무 것도 발견되지 않거나 빈 약어가 발견되면, 시스템은 의 첫 글자에서 약어를 작성합니다. `jcr:title` 현재 구성 요소 속성.

상위 구성 요소에서 아이콘 상속을 취소하려면 빈 을 설정합니다. `abbreviation` 구성 요소의 속성은 기본 동작으로 되돌아갑니다.

다음 [구성 요소 콘솔](/help/sites-cloud/authoring/features/components-console.md#component-details) 특정 구성 요소의 아이콘이 정의되는 방식을 표시합니다.

#### SVG 아이콘 예 {#svg-icon-example}

```xml
<?xml version="1.0" encoding="utf-8"?>
<!DOCTYPE svg PUBLIC "-//W3C//DTD SVG 1.1//EN" "https://www.w3.org/Graphics/SVG/1.1/DTD/svg11.dtd">
<svg version="1.1" id="Layer_1" xmlns="https://www.w3.org/2000/svg" xmlns:xlink="https://www.w3.org/1999/xlink" x="0px" y="0px"
     width="20px" height="20px" viewBox="0 0 20 20" enable-background="new 0 0 20 20" xml:space="preserve">
    <ellipse cx="5" cy="5" rx="3" ry="3" fill="#707070"/>
    <ellipse cx="15" cy="5" rx="4" ry="4" fill="#707070"/>
    <ellipse cx="5" cy="15" rx="5" ry="5" fill="#707070"/>
    <ellipse cx="15" cy="15" rx="4" ry="4" fill="#707070"/>
</svg>
```

### 구성 요소의 속성 및 하위 노드 {#properties-and-child-nodes-of-a-component}

구성 요소를 정의하는 데 필요한 노드/속성 중 다수는 두 UI에 공통되지만, 구성 요소가 두 환경에서 작동할 수 있도록 차이는 독립적으로 유지됩니다.

구성 요소는 유형의 노드입니다. `cq:Component` 에는 다음 속성과 하위 노드가 있습니다.

| 이름 | 유형 | 설명 |
|---|---|---|
| `.` | `cq:Component` | 현재 구성 요소를 나타냅니다. 구성 요소가 노드 유형입니다. `cq:Component`. |
| `componentGroup` | `String` | 다음에서 구성 요소를 선택할 수 있는 그룹을 나타냅니다. [구성 요소 브라우저](/help/sites-cloud/authoring/fundamentals/environment-tools.md#components-browser). 다음으로 시작하는 값 `.` 다른 구성 요소가 상속되는 기본 구성 요소와 같이 UI에서 선택할 수 없는 구성 요소에 사용됩니다. |
| `cq:isContainer` | `Boolean` | 이는 구성 요소가 컨테이너 구성 요소이므로 단락 시스템과 같은 다른 구성 요소를 포함할 수 있는지 여부를 나타냅니다. |
| `cq:dialog` | `nt:unstructured` | 구성 요소에 대한 편집 대화 상자 정의입니다. |
| `cq:design_dialog` | `nt:unstructured` | 구성 요소에 대한 디자인 대화 상자의 정의입니다. |
| `cq:editConfig` | `cq:EditConfig` | 다음을 정의합니다. [구성 요소의 구성을 편집합니다.](#edit-behavior) |
| `cq:htmlTag` | `nt:unstructured` | 주변 HTML 태그에 추가된 추가 태그 속성을 반환합니다. 자동으로 생성된 div에 속성을 추가할 수 있습니다. |
| `cq:noDecoration` | `Boolean` | true인 경우 구성 요소는 자동으로 생성된 div 및 css 클래스로 렌더링되지 않습니다. |
| `cq:template` | `nt:unstructured` | 이 노드가 검색되면 구성 요소 브라우저에서 구성 요소를 추가할 때 컨텐츠 템플릿으로 사용됩니다. |
| `jcr:created` | `Date` | 구성 요소를 만든 날짜입니다. |
| `jcr:description` | `String` | 구성 요소에 대한 설명입니다. |
| `jcr:title` | `String` | 구성 요소의 제목입니다. |
| `sling:resourceSuperType` | `String` | 설정하면 구성 요소가 이 구성 요소에서 상속됩니다. |
| `component.html` | `nt:file` | 구성 요소의 HTL 스크립트 파일입니다. |
| `cq:icon` | `String` | 이 값은 다음을 가리킵니다. [구성 요소의 아이콘](#component-icon) 구성 요소 브라우저에 나타납니다. |

다음을 살펴보면 **텍스트** 구성 요소에서는 다음과 같은 여러 요소를 볼 수 있습니다.

![텍스트 구성 요소 구조](assets/components-text.png)

관심 있는 속성은 다음과 같습니다.

* `jcr:title` - 구성 요소 브라우저 내에서 구성 요소를 식별하는 데 사용되는 구성 요소의 제목입니다.
* `jcr:description` - 구성 요소에 대한 설명입니다.
* `sling:resourceSuperType` - 정의를 재정의하여 구성 요소를 확장할 때 상속 경로를 나타냅니다.

특히 관심 있는 하위 노드는 다음과 같습니다.

* `cq:editConfig` - 편집 시 구성 요소의 시각적 측면을 제어합니다.
* `cq:dialog` - 이 구성 요소의 콘텐츠를 편집하기 위한 대화 상자를 정의합니다.
* `cq:design_dialog` - 이 구성 요소의 디자인 편집 옵션을 지정합니다.

### 대화 상자 {#dialogs}

대화 상자는 작성자가 콘텐츠 페이지에서 구성 요소를 구성하고 해당 구성 요소에 대한 입력을 제공할 수 있는 인터페이스를 제공하므로 구성 요소의 핵심 요소입니다. 다음을 참조하십시오. [작성 설명서](/help/sites-cloud/authoring/fundamentals/editing-content.md) 콘텐츠 작성자가 구성 요소와 상호 작용하는 방법에 대한 자세한 내용.

구성 요소의 복잡성에 따라 대화 상자에 하나 이상의 탭이 필요할 수 있습니다.

AEM 구성 요소에 대한 대화 상자:

* 다음과 같음 `cq:dialog` 유형의 노드 `nt:unstructured`.
* 아래에 위치 `cq:Component` 노드 및 구성 요소 정의 옆에 있는 노드
* 이 구성 요소의 콘텐츠를 편집하기 위한 대화 상자를 정의합니다.
* Granite UI 구성 요소를 사용하여 정의됩니다.
* 콘텐츠 구조 및 를 기반으로 서버측(Sling 구성 요소)을 렌더링합니다. `sling:resourceType` 속성.
* 대화 상자 내의 필드를 설명하는 노드 구조를 포함합니다
   * 이러한 노드는 다음과 같습니다 `nt:unstructured` (필수 포함) `sling:resourceType` 속성.

![제목 구성 요소의 대화 상자 정의](assets/components-title-dialog.png)

대화 상자 내에서 개별 필드가 정의됩니다.

![제목 구성 요소의 대화 상자 정의 필드](assets/components-title-dialog-items.png)

### 디자인 대화 상자 {#design-dialogs}

디자인 대화 상자는 콘텐츠를 편집하고 구성하는 데 사용되는 대화 상자와 유사하지만, 템플릿 작성자가 페이지 템플릿에서 해당 구성 요소에 대한 디자인 세부 정보를 미리 구성하고 제공할 수 있는 인터페이스를 제공합니다. 그런 다음 콘텐츠 작성자는 페이지 템플릿을 사용하여 콘텐츠 페이지를 만듭니다. 다음을 참조하십시오. [템플릿 설명서](/help/sites-cloud/authoring/features/templates.md) 템플릿 생성 방법에 대한 자세한 내용

[페이지 템플릿을 편집할 때 디자인 대화 상자가 사용됩니다](/help/sites-cloud/authoring/features/templates.md)모든 구성 요소에 필요한 것은 아니지만. 예를 들어 **제목** 및 **이미지 구성 요소** 둘 다 디자인 대화 상자가 있지만 **소셜 미디어 공유 구성 요소** 그렇지 않습니다.

### Coral UI 및 Granite UI {#coral-and-granite}

Coral UI 및 Granite UI는 AEM의 모양과 느낌을 정의합니다.

* [Coral UI](https://opensource.adobe.com/coral-spectrum/documentation/) 는 모든 클라우드 솔루션에서 일관된 UI를 제공합니다.
* [Granite UI](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/granite-ui/api/jcr_root/libs/granite/ui/index.html) 는 UI 콘솔 및 대화 상자를 작성하기 위해 Sling 구성 요소에 래핑된 Coral UI 마크업을 제공합니다.

Granite UI는 작성 환경에서 대화 상자를 만드는 데 필요한 다양한 기본 위젯을 제공합니다. 필요한 경우 이 선택 항목을 확장하고 고유한 위젯을 만들 수 있습니다.

자세한 내용은 다음 리소스를 참조하십시오.

* [AEM UI 구조](/help/implementing/developing/introduction/ui-structure.md)

### 대화 상자 필드 사용자 지정 {#customizing-dialog-fields}

<!--
Content not found

>[!TIP]
>
>See the [AEM Gems session](https://docs.adobe.com/content/ddc/en/gems/customizing-dialog-fields-in-touch-ui.html) on customizing dialog fields.
-->

구성 요소 대화 상자에서 사용할 새 위젯을 만들려면 새 Granite UI 필드 구성 요소를 만들어야 합니다.

대화 상자를 양식 요소의 간단한 컨테이너로 간주하면 대화 상자 콘텐츠의 기본 콘텐츠도 양식 필드로 볼 수 있습니다. 새 양식 필드를 만들려면 리소스 유형을 만들어야 합니다. 이는 새 구성 요소를 만드는 것과 같습니다. Granite UI는 이러한 작업에서 상속할 일반 필드 구성 요소를 제공합니다(사용). `sling:resourceSuperType`):

`/libs/granite/ui/components/coral/foundation/form/field`

보다 구체적으로, Granite UI는 대화 상자, 또는 보다 일반적으로 설명하기에 적합한 다양한 필드 구성 요소를 제공합니다 [양식.](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/granite-ui/api/jcr_root/libs/granite/ui/components/foundation/form/index.html)

리소스 유형을 만든 후에는 속성을 사용하여 대화 상자에 새 노드를 추가하여 필드를 인스턴스화할 수 있습니다 `sling:resourceType` 방금 소개한 리소스 유형을 참조합니다.

#### 대화 상자 필드 액세스 {#access-to-dialog-fields}

렌더링 조건(`rendercondition`) 대화 상자의 특정 탭/필드에 액세스할 수 있는 사용자를 제어합니다. 예를 들면 다음과 같습니다.

```text
+ mybutton
  - sling:resourceType = granite/ui/components/coral/foundation/button
  + rendercondition
    - sling:resourceType = myapp/components/renderconditions/group
    - groups = ["administrators"]
```

## 구성 요소 사용 {#using-components}

구성 요소를 만든 후 사용할 수 있도록 활성화해야 합니다. 이를 사용하여 구성 요소 구조가 저장소의 결과 콘텐츠 구조와 어떻게 연관되어 있는지 보여 줍니다.

### 템플릿에 구성 요소 추가 {#adding-your-component-to-the-template}

구성 요소를 정의한 후 사용할 수 있도록 해야 합니다. 구성 요소를 템플릿에서 사용할 수 있도록 하려면 템플릿의 레이아웃 컨테이너 정책에서 구성 요소를 활성화해야 합니다.

다음을 참조하십시오. [템플릿 설명서](/help/sites-cloud/authoring/features/templates.md) 템플릿 생성 방법에 대한 자세한 내용

### 구성 요소 및 구성 요소가 만드는 콘텐츠 {#components-and-the-content-they-create}

의 인스턴스를 만들고 구성하는 경우 **제목** 페이지의 구성 요소: `/content/wknd/language-masters/en/adventures/extreme-ironing.html`

![제목 편집 대화 상자](assets/components-title-dialog.png)

그러면 저장소 내에 만들어진 컨텐츠의 구조를 볼 수 있습니다.

![제목 구성 요소 노드 구조](assets/components-title-content-nodes.png)

특히 의 실제 텍스트를 보면 **제목 구성 요소**:

* 컨텐츠에 다음 항목이 포함되어 있습니다. `jcr:title` 작성자가 입력한 제목의 실제 텍스트를 보유하는 속성입니다.
* 여기에는 또한 `sling:resourceType` 구성 요소 정의에 대한 참조.

정의된 속성은 개별 정의에 따라 다릅니다. 비록 그것들이 위보다 더 복잡할 수 있지만 여전히 같은 기본 원칙을 따르고 있다.

## 구성 요소 계층 및 상속 {#component-hierarchy-and-inheritance}

AEM 내의 구성 요소는 **리소스 유형 계층**. 속성을 사용하여 구성 요소를 확장하는 데 사용됩니다. `sling:resourceSuperType`. 이렇게 하면 구성 요소가 다른 구성 요소에서 상속될 수 있습니다.

섹션 보기 [구성 요소 재사용](#reusing-components) 추가 정보.

## 비헤이비어 편집 {#edit-behavior}

이 섹션에서는 구성 요소의 편집 동작을 구성하는 방법을 설명합니다. 여기에는 구성 요소에 사용할 수 있는 작업, in.place 편집기의 특성 및 구성 요소의 이벤트와 관련된 리스너와 같은 속성이 포함됩니다.

구성 요소의 편집 동작은 다음을 추가하여 구성됩니다. `cq:editConfig` 유형의 노드 `cq:EditConfig` (유형의) 구성 요소 노드 아래 `cq:Component`) 특정 속성 및 하위 노드를 추가합니다. 다음 속성 및 하위 노드를 사용할 수 있습니다.

* `cq:editConfig` 노드 속성
* [`cq:editConfig` 하위 노드](#configuring-with-cq-editconfig-child-nodes):
   * `cq:dropTargets` (노드 유형 `nt:unstructured`): 콘텐츠 파인더의 에셋에서 삭제를 수락할 수 있는 삭제 대상 목록을 정의합니다(단일 삭제 대상이 허용됨).
   * `cq:inplaceEditing` (노드 유형 `cq:InplaceEditingConfig`): 구성 요소에 대한 즉석 편집 구성을 정의합니다
   * `cq:listeners` (노드 유형 `cq:EditListenersConfig`): 구성 요소에서 작업이 발생하기 전이나 후에 발생하는 작업을 정의합니다

AEM에는 많은 기존 구성이 있습니다. 에서 쿼리 도구를 사용하여 특정 속성이나 하위 노드를 쉽게 검색할 수 있습니다 **CRXDE Lite**.

### 구성 요소 자리 표시자 {#component-placeholders}

구성 요소에 콘텐츠가 없는 경우에도 구성 요소는 항상 작성자가 볼 수 있는 일부 HTML을 렌더링해야 합니다. 그렇지 않으면 편집기의 인터페이스에서 시각적으로 사라져 페이지와 편집기에서 기술적으로 표시되지만 보이지 않을 수 있습니다. 이러한 경우 작성자는 빈 구성 요소를 선택하고 상호 작용할 수 없습니다.

따라서 구성 요소는 페이지가 페이지 편집기에서 렌더링될 때(WCM 모드가 인 경우) 표시되는 출력을 렌더링하지 않는 한 자리 표시자를 렌더링해야 합니다 `edit` 또는 `preview`).
자리 표시자에 대한 일반적인 HTML 마크업은 다음과 같습니다.

```HTML
<div class="cq-placeholder" data-emptytext="Component Name"></div>
```

위의 자리 표시자 HTML을 렌더링하는 일반적인 HTL 스크립트는 다음과 같습니다.

```HTML
<div class="cq-placeholder" data-emptytext="${component.properties.jcr:title}"
     data-sly-test="${(wcmmode.edit || wcmmode.preview) && isEmpty}"></div>
```

앞의 예에서 `isEmpty` 는 구성 요소에 콘텐츠가 없고 작성자에게 보이지 않는 경우에만 true인 변수입니다.

Adobe 반복을 방지하기 위해 구성 요소 구현자는 이러한 자리 표시자에 HTL 템플릿을 사용하는 것이 좋습니다. [핵심 구성 요소에서 제공하는 것과 같습니다.](https://github.com/adobe/aem-core-wcm-components/blob/master/content/src/content/jcr_root/apps/core/wcm/components/commons/v1/templates.html)

그런 다음 이전 링크에서 템플릿 사용은 다음 HTL 행을 통해 수행됩니다.

```HTML
<sly data-sly-use.template="core/wcm/components/commons/v1/templates.html"
     data-sly-call="${template.placeholder @ isEmpty=!model.text}"></sly>
```

앞의 예에서 `model.text` 는 콘텐츠에 콘텐츠가 있고 이 콘텐츠가 표시되는 경우에만 true인 변수입니다.

이 템플릿의 사용 예는 핵심 구성 요소에서 확인할 수 있습니다. [제목 구성 요소에서와 같습니다.](https://github.com/adobe/aem-core-wcm-components/blob/master/content/src/content/jcr_root/apps/core/wcm/components/title/v2/title/title.html#L27)

### cq:EditConfig 하위 노드로 구성 {#configuring-with-cq-editconfig-child-nodes}

#### 대화 상자에 자산 끌어 놓기 - cq:dropTargets {#cq-droptargets}

다음 `cq:dropTargets` 노드(노드 유형) `nt:unstructured`)는 콘텐츠 파인더에서 드래그한 에셋의 드롭을 수락할 수 있는 드롭 대상을 정의합니다. 유형의 노드입니다. `cq:DropTargetConfig`.

유형의 하위 노드 `cq:DropTargetConfig` 구성 요소에서 드롭 대상을 정의합니다.

### 즉석 편집 - cq:inplaceEditing {#cq-inplaceediting}

즉석 편집기를 사용하면 대화 상자를 열지 않고도 컨텐츠 플로우에서 직접 컨텐츠를 편집할 수 있습니다. 예: 표준 **텍스트** 및 **제목** 구성 요소 모두 즉석 편집기를 가지고 있습니다.

모든 구성 요소 유형에 즉석 편집기가 필요/의미 있는 것은 아닙니다.

다음 `cq:inplaceEditing` 노드(노드 유형) `cq:InplaceEditingConfig`) 구성 요소에 대한 즉석 편집 구성을 정의합니다. 다음과 같은 속성을 가질 수 있습니다.

| 속성 이름 | 속성 유형 | 속성 값 |
|---|---|---|
| `active` | `Boolean` | `true` 구성 요소를 바로 편집할 수 있도록 설정 |
| `configPath` | `String` | 구성 노드에 의해 지정될 수 있는 편집기 구성의 경로 |
| `editorType` | `String` | 사용 가능한 유형은 다음과 같습니다. `plaintext` 비 HTML 콘텐츠의 경우, `title` 편집을 시작하기 전에 그래픽 제목을 일반 텍스트로 변환합니다. `text` 리치 텍스트 편집기 사용 |

다음 구성은 구성 요소를 즉석에서 편집할 수 있도록 하며 `plaintext` 편집기 유형으로:

```text
    <cq:inplaceEditing
        jcr:primaryType="cq:InplaceEditingConfig"
        active="{Boolean}true"
        editorType="plaintext"/>
```

### 필드 이벤트 처리 - cq:listeners {#cq-listeners}

대화 상자 필드의 이벤트 처리 방법은 사용자 지정 의 리스너를 통해 수행됩니다 [클라이언트 라이브러리](/help/implementing/developing/introduction/clientlibs.md).

필드에 논리를 삽입하려면 다음을 수행해야 합니다.

* 필드를 지정된 CSS 클래스(후크)로 표시하십시오.
* 클라이언트 라이브러리에서 해당 CSS 클래스 이름에 후크된 JS 수신기를 정의합니다(이렇게 하면 사용자 지정 논리의 범위가 필드에만 지정되며 동일한 유형의 다른 필드에는 영향을 주지 않음).

이를 위해서는 상호 작용하려는 기본 위젯 라이브러리에 대해 알아야 합니다. [Coral UI 설명서 참조](https://opensource.adobe.com/coral-spectrum/documentation/) 반응할 이벤트를 식별합니다.

다음 `cq:listeners` 노드(노드 유형) `cq:EditListenersConfig`) 구성 요소에서 작업 전 또는 후에 수행되는 작업을 정의합니다. 다음 표는 가능한 속성을 정의합니다.

| 속성 이름 | 속성 값 |
|---|---|
| `beforedelete` | 구성 요소를 제거하기 전에 처리기가 트리거됩니다. |
| `beforeedit` | 구성 요소를 편집하기 전에 처리기가 트리거됩니다. |
| `beforecopy` | 구성 요소가 복사되기 전에 처리기가 트리거됩니다. |
| `beforeremove` | 구성 요소를 이동하기 전에 처리기가 트리거됩니다. |
| `beforeinsert` | 구성 요소를 삽입하기 전에 처리기가 트리거됩니다. |
| `beforechildinsert` | 처리기는 구성 요소가 다른 구성 요소 내부에 삽입되기 전에 트리거됩니다(컨테이너만 해당). |
| `afterdelete` | 구성 요소가 제거되면 핸들러가 트리거됩니다. |
| `afteredit` | 처리기는 구성 요소를 편집한 후 트리거됩니다. |
| `aftercopy` | 처리기는 구성 요소가 복사된 후 트리거됩니다. |
| `afterinsert` | 처리기는 구성 요소가 삽입된 후 트리거됩니다. |
| `aftermove` | 처리기는 구성 요소를 이동한 후 트리거됩니다. |
| `afterchildinsert` | 처리기는 구성 요소가 다른 구성 요소 내부에 삽입되면 트리거됩니다(컨테이너만 해당). |

>[!NOTE]
>
>중첩된 구성 요소의 경우에서 속성으로 정의된 작업에 대한 특정 제한 사항이 있습니다. `cq:listeners` 노드. 중첩된 구성 요소의 경우 다음 속성 값 **필수** be `REFRESH_PAGE`:
>
>* `aftermove`
>* `aftercopy`

이벤트 처리기는 사용자 지정 구현으로 구현할 수 있습니다. 예, (여기서 `project.customerAction` 은 정적 메서드입니다).

`afteredit = "project.customerAction"`

다음 예제는 `REFRESH_INSERTED` 구성:

`afterinsert="function(path, definition) { this.refreshCreated(path, definition); }"`

다음 구성을 사용하면 구성 요소가 삭제, 편집, 삽입 또는 이동된 후 페이지가 새로 고쳐집니다.

```text
    <cq:listeners
        jcr:primaryType="cq:EditListenersConfig"
        afterdelete="REFRESH_PAGE"
        afteredit="REFRESH_PAGE"
        afterinsert="REFRESH_PAGE"
        afterMove="REFRESH_PAGE"/>
```

### 필드 유효성 검사 {#field-validation}

Granite UI 및 Granite UI 위젯의 필드 유효성 검사는 다음을 사용하여 수행됩니다. `foundation-validation` API. 다음을 참조하십시오. [`foundation-valdiation` Granite 설명서](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/granite-ui/api/jcr_root/libs/granite/ui/components/coral/foundation/clientlibs/foundation/js/validation/index.html) 을 참조하십시오.

### 대화 상자의 사용 가능 여부 감지 {#dialog-ready}

대화 상자를 사용할 수 있고 준비가 되었을 때만 실행해야 하는 사용자 지정 JavaScript가 있는 경우 `dialog-ready` 이벤트.

이 이벤트는 대화 상자가 로드(또는 다시 로드)되고 사용할 준비가 될 때마다 트리거됩니다. 즉, 대화 상자의 DOM에 변경(만들기/업데이트)이 있을 때마다 트리거됩니다.

`dialog-ready` 대화 상자 또는 유사한 작업 내의 필드에 대한 사용자 지정을 수행하는 JavaScript 사용자 지정 코드를 후크하는 데 사용할 수 있습니다.

## 미리 보기 동작 {#preview-behavior}

다음 [WCM 모드](https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/wcm/api/WCMMode.html) 쿠키는 페이지를 새로 고치지 않아도 미리보기 모드로 전환할 때 설정됩니다.

렌더링이 WCM 모드에 민감한 구성 요소의 경우, 특별히 자신을 새로 고치도록 정의한 다음 쿠키 값을 사용해야 합니다.

## 구성 요소 문서화 {#documenting-components}

개발자는 구성 요소의 내용을 빠르게 이해할 수 있도록 구성 요소 설명서에 쉽게 액세스할 수 있습니다.

* 설명
* 의도한 사용
* 컨텐츠 구조 및 속성
* 노출된 API 및 확장 지점
* 등

따라서 구성 요소 자체 내에서 사용할 수 있는 기존 설명서 Markdown을 만드는 것은 매우 쉽습니다.

필요한 것은 `README.md` 구성 요소 구조의 파일입니다.

![구성 요소 구조의 README.md](assets/components-documentation.png)

그러면 이 Markdown이 [구성 요소 콘솔](/help/sites-cloud/authoring/features/components-console.md).

![구성 요소 콘솔에 표시되는 README.md](assets/components-documentation-console.png)

지원되는 Markdown은 의 경우와 동일합니다 [컨텐츠 조각](/help/sites-cloud/administering/content-fragments/content-fragments.md).
