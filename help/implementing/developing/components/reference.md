---
title: 구성 요소 참조 안내서
description: 구성 요소 및 해당 구조에 대한 세부 사항에 대한 개발자 참조 안내서
exl-id: 45e5265b-39d6-4a5c-be1a-e66bb7ea387d
source-git-commit: a446efacb91f1a620d227b9413761dd857089c96
workflow-type: tm+mt
source-wordcount: '3659'
ht-degree: 1%

---

# 구성 요소 참조 안내서 {#components-reference-guide}

구성 요소는 AEM에서 경험을 작성하는 데 핵심입니다. [코어 구성 요소](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=ko-KR) 및 [AEM Project Archetype](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html)을 사용하면 준비된 강력한 구성 요소 집합을 간단하게 시작할 수 있습니다. [WKND 자습서](/help/implementing/developing/introduction/develop-wknd-tutorial.md)에서는 개발자에게 이러한 도구를 사용하는 방법과 새 AEM 사이트를 만들기 위해 사용자 지정 구성 요소를 빌드하는 방법을 안내합니다.

>[!TIP]
>
>이 문서를 참조하기 전에 [WKND 자습서](/help/implementing/developing/introduction/develop-wknd-tutorial.md)를 완료했는지 확인하고 따라서 [코어 구성 요소](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html) 및 [AEM Project Archetype.](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html)에 익숙한지 확인하십시오.

WKND 자습서에서는 대부분의 사용 사례를 다룹니다. 이 문서는 해당 리소스를 보완하는 용도로만 사용됩니다. 이 안내서에서는 구성 요소가 AEM에서 구조화되고 구성되는 방법에 대한 심층적인 기술 세부 사항을 제공하며 시작 안내서로서 의도되지 않습니다.

## 개요 {#overview}

이 섹션에서는 구성 요소를 개발할 때 필요한 세부 사항을 소개하는 주요 개념과 문제를 다룹니다.

### 계획 {#planning}

구성 요소를 실제로 구성하거나 코드를 만들려면 먼저 다음 사항을 고려해야 합니다.

* 새로운 구성 요소가 정확히 필요한 작업은 무엇입니까?
* 구성 요소를 처음부터 새로 만들어야 합니까, 아니면 기존 구성 요소에서 기본 사항을 상속할 수 있습니까?
* 구성 요소에서 컨텐츠를 선택/조작하는 논리를 필요로 합니까?
   * 로직은 사용자 인터페이스 레이어와 별도로 유지되어야 합니다. HTL은 이러한 상황이 발생하지 않도록 하기 위해 설계되었습니다.
* 구성 요소에 CSS 형식이 필요합니까?
   * CSS 서식은 구성 요소 정의와 별도로 유지되어야 합니다. 외부 CSS 파일을 통해 수정할 수 있도록 HTML 요소의 이름을 지정하는 규칙을 정의합니다.
* 새로운 구성 요소에 어떤 보안 문제가 발생할 수 있습니까?

### 기존 구성 요소 재사용 {#reusing-components}

완전히 새로운 구성 요소를 만드는 데 시간을 투자하기 전에 기존 구성 요소를 사용자 지정하거나 확장하는 것이 좋습니다. [핵심 ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html) 구성 요소는 유연하고 강력하며 테스트를 잘 거친 프로덕션 지원 구성 요소 세트를 제공합니다.

#### 코어 구성 요소 확장 {#extending-core-components}

코어 구성 요소는 또한 [명확한 사용자 지정 패턴](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/customizing.html)을 제공하여 프로젝트의 요구 사항에 맞게 조정할 수 있습니다.

#### 구성 요소 오버레이 {#overlying-components}

구성 요소를 검색 경로 로직을 기반으로 [오버레이](/help/implementing/developing/introduction/overlays.md)로 다시 정의할 수도 있습니다. 그러나 이 경우 [Sling Resource Merger](/help/implementing/developing/introduction/sling-resource-merger.md)는 트리거되지 않고 `/apps`가 전체 오버레이를 정의해야 합니다.

#### 구성 요소 대화 상자 확장 {#extending-component-dialogs}

Sling Resource Merger를 사용하여 구성 요소 대화 상자를 재정의하고 `sling:resourceSuperType` 속성을 정의할 수도 있습니다.

즉, 전체 대화 상자를 재정의하는 대신 필요한 차이만 재정의할 수 있습니다.

### 컨텐츠 논리 및 렌더링 마크업 {#content-logic-and-rendering-markup}

구성 요소가 [HTML로 렌더링됩니다.](https://www.w3schools.com/htmL/html_intro.asp) 구성 요소는 필요한 컨텐츠를 가져온 다음 작성 환경과 게시 환경 모두에서 필요에 따라 렌더링하는 데 필요한 HTML을 정의해야 합니다.

구성 요소의 컨텐츠를 선택하는 데 사용되는 논리를 제어하는 코드와는 별도로 마크업 및 렌더링에 대한 코드를 유지하는 것이 좋습니다.

이 철학은 기본 비즈니스 논리를 정의하는 데 실제 프로그래밍 언어가 사용되도록 의도적으로 제한되는 템플릿 언어인 [HTL](https://experienceleague.adobe.com/docs/experience-manager-htl/using/overview.html?lang=ko-KR)에서 지원됩니다. 이 메커니즘은 지정된 보기에 대해 호출되는 코드를 강조 표시하며, 필요한 경우 동일한 구성 요소의 다른 보기에 대해 특정 논리를 허용합니다.

이(선택 사항) 로직은 다른 방식으로 구현될 수 있으며 특정 명령을 사용하여 HTL에서 호출됩니다.

* Java 사용 - [HTL Java Use-API](https://helpx.adobe.com/experience-manager/htl/using/use-api-java.html)를 사용하면 HTL 파일이 사용자 지정 Java 클래스의 보조 메서드에 액세스할 수 있습니다. 구성 요소 컨텐츠를 선택하고 구성하는 로직을 구현하는 데 Java 코드를 사용할 수 있습니다.
* JavaScript 사용 - [HTL JavaScript Use-API](https://experienceleague.adobe.com/docs/experience-manager-htl/using/htl/use-api-javascript.html)를 사용하면 HTL 파일이 JavaScript로 작성된 도우미 코드에 액세스할 수 있습니다. 이렇게 하면 JavaScript 코드를 사용하여 구성 요소 컨텐츠를 선택하고 구성하는 로직을 구현할 수 있습니다.
* 클라이언트측 라이브러리 사용 - 최신 웹 사이트는 복잡한 JavaScript 및 CSS 코드로 구동되는 클라이언트측 처리에 주로 의존합니다. 자세한 내용은 [AEM에서 클라이언트측 라이브러리를 Cloud Service](/help/implementing/developing/introduction/clientlibs.md)로 사용 문서를 참조하십시오.

## 구성 요소 구조 {#structure}

AEM 구성 요소의 구조는 강력하고 유연합니다. 주요 부분은 다음과 같습니다.

* [리소스 유형](#resource-type)
* [구성 요소 정의](#component-definition)
* [구성 요소의 속성 및 하위 노드](#properties-and-child-nodes-of-a-component)
* [대화 상자](#dialogs)
* [디자인 대화 상자](#design-dialogs)

### 리소스 유형 {#resource-type}

구조의 주요 요소는 리소스 유형입니다.

* 컨텐츠 구조가 의도를 선언합니다.
* 리소스 유형은 이러한 리소스를 구현합니다.

이것은 시간이 지남에 따라 모양과 느낌이 바뀔 때에도, 그 의도가 시간을 유지하게 하는 것을 보장하는 추상화입니다.

### 구성 요소 정의 {#component-definition}

구성 요소의 정의는 다음과 같이 분류할 수 있습니다.

* AEM 구성 요소는 [Sling을 기반으로 합니다.](https://sling.apache.org/documentation.html)
* AEM 구성 요소는 `/libs/core/wcm/components` 아래에 있습니다.
* 프로젝트/사이트별 구성 요소는 `/apps/<myApp>/components` 아래에 있습니다.
* AEM 표준 구성 요소는 `cq:Component`으로 정의되며 주요 요소가 있습니다.
   * jcr 속성 - jcr 속성 목록입니다. 이러한 변수는 변수이며, 일부는 구성 요소 노드, 속성 및 하위 노드의 기본 구조가 `cq:Component` 정의에서 정의되는 경우에도 선택 사항일 수 있습니다.
   * 리소스 - 구성 요소에서 사용하는 정적 요소를 정의합니다.
   * 스크립트 - 구성 요소의 결과 인스턴스의 동작을 구현하는 데 사용됩니다.

#### 필수 속성 {#vital-properties}

* **루트 노드**:
   * `<mycomponent> (cq:Component)` - 구성 요소의 계층 노드입니다.
* **중요한 속성**:
   * `jcr:title` - 구성 요소 제목;예를 들어 구성 요소가 구성 요소 브라우저 및 구성 요소  [콘솔에 나열될 때 ](/help/sites-cloud/authoring/fundamentals/environment-tools.md#components-browser) 레이블로  [사용됩니다](/help/sites-cloud/authoring/features/components-console.md)
   * `jcr:description` - 구성 요소에 대한 설명구성 요소 브라우저 및 구성 요소 콘솔에서 마우스 오른쪽 단추 힌트로 사용됩니다.
   * 자세한 내용은 [구성 요소 아이콘](#component-icon) 섹션을 참조하십시오
* **중요한 하위 노드**:
   * `cq:editConfig (cq:EditConfig)` - 구성 요소의 편집 속성을 정의하고 구성 요소 브라우저에 구성 요소를 표시할 수 있습니다
      * 구성 요소에 대화 상자가 있으면 cq:editConfig가 없는 경우에도 구성 요소 브라우저나 사이드 킥에 자동으로 표시됩니다.
   * `cq:childEditConfig (cq:EditConfig)` - 자체 UI를 정의하지 않는 하위 구성 요소에 대한 작성자 UI 측면을 제어합니다 `cq:editConfig`.
   * `cq:dialog (nt:unstructured)` - 이 구성 요소의 대화 상자 사용자가 구성 요소를 구성하거나 컨텐츠를 편집할 수 있는 인터페이스를 정의합니다.
   * `cq:design_dialog (nt:unstructured)` - 이 구성 요소에 대한 디자인 편집

#### 구성 요소 아이콘 {#component-icon}

구성 요소에 대한 아이콘 또는 약어는 개발자가 구성 요소를 만들 때 구성 요소의 JCR 속성을 통해 정의됩니다. 이러한 속성은 다음 순서로 평가되며 발견된 첫 번째 유효한 속성이 사용됩니다.

1. `cq:icon` - 구성 요소 브라우저에 표시할  [Coral UI ](https://opensource.adobe.com/coral-spectrum/examples/#icon) 라이브러리의 표준 아이콘을 가리키는 문자열 속성
   * Coral 아이콘의 HTML 속성 값을 사용합니다.
1. `abbreviation` - 구성 요소 브라우저에서 구성 요소 이름의 약어를 사용자 지정하는 문자열 속성
   * 약어는 두 문자로 제한해야 합니다.
   * 빈 문자열을 제공하면 `jcr:title` 속성의 처음 두 문자로부터 약어를 빌드합니다.
      * 예를 들어 &quot;Image&quot;의 &quot;Im&quot;
      * 현지화된 제목이 약어를 빌드하는 데 사용됩니다.
   * 약어는 구성 요소에 번역 힌트로 사용되는 `abbreviation_commentI18n` 속성이 있는 경우에만 변환됩니다.
1. `cq:icon.png` 또는  `cq:icon.svg` - 구성 요소 브라우저에 표시되는 이 구성 요소의 아이콘
   * 20 x 20 픽셀은 표준 구성 요소의 아이콘 크기입니다.
      * 더 큰 아이콘의 크기는 작아집니다(클라이언트측).
   * 권장되는 색상은 rgb(112, 112, 112) > #707070입니다.
   * 표준 구성 요소 아이콘의 배경이 투명합니다.
   * `.png` 및 `.svg` 파일만 지원됩니다.
   * Eclipse 플러그인을 통해 파일 시스템에서 가져오는 경우 파일 이름을 `_cq_icon.png` 또는 `_cq_icon.svg`로 이스케이프해야 합니다.
   * `.png` 둘 다  `.svg` 있으면 선례를 뒤집는다.

위의 속성(`cq:icon`, `abbreviation`, `cq:icon.png` 또는 `cq:icon.svg`)이 구성 요소에 없는 경우:

* 시스템이 `sling:resourceSuperType` 속성 다음에 있는 수퍼 구성 요소에서 동일한 속성을 검색합니다.
* 수퍼 구성 요소 수준에서 아무 것도 없거나 빈 약어를 찾을 수 없으면 시스템은 현재 구성 요소의 `jcr:title` 속성의 첫 번째 문자로부터 약어를 작성합니다.

수퍼 구성 요소에서 아이콘 상속을 취소하려면, 구성 요소에서 빈 `abbreviation` 속성을 설정하면 기본 동작으로 돌아갑니다.

[구성 요소 콘솔](/help/sites-cloud/authoring/features/components-console.md#component-details)에는 특정 구성 요소에 대한 아이콘이 정의된 방식이 표시됩니다.

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

### 구성 요소 {#properties-and-child-nodes-of-a-component}의 속성 및 하위 노드

구성 요소를 정의하는 데 필요한 많은 노드/속성은 두 UI 모두에서 일반적이지만, 구성 요소가 두 환경에서 모두 작동할 수 있도록 독립적입니다.

구성 요소는 `cq:Component` 유형의 노드이며 다음 속성 및 하위 노드를 가집니다.

| 이름 | 유형 | 설명 |
|---|---|---|
| `.` | `cq:Component` | 현재 구성 요소를 나타냅니다. 구성 요소는 노드 유형 `cq:Component`입니다. |
| `componentGroup` | `String` | 구성 요소 브라우저에서 구성 요소를 선택할 수 있는 그룹을 나타냅니다.[](/help/sites-cloud/authoring/fundamentals/environment-tools.md#components-browser) 로 시작하는 값 `.` 은 다른 구성 요소가 상속되는 기본 구성 요소와 같이 UI에서 선택할 수 없는 구성 요소에 사용됩니다. |
| `cq:isContainer` | `Boolean` | 구성 요소가 컨테이너 구성 요소인지 여부를 나타내므로 단락 시스템과 같은 다른 구성 요소를 포함할 수 있습니다. |
| `cq:dialog` | `nt:unstructured` | 구성 요소에 대한 편집 대화 상자의 정의입니다. |
| `cq:design_dialog` | `nt:unstructured` | 구성 요소에 대한 디자인 대화 상자의 정의입니다. |
| `cq:editConfig` | `cq:EditConfig` | 구성 요소의 [구성 편집을 정의합니다.](#edit-behavior) |
| `cq:htmlTag` | `nt:unstructured` | 그러면 주변 HTML 태그에 추가된 추가 태그 속성이 반환됩니다. 자동으로 생성된 div에 속성을 추가할 수 있습니다. |
| `cq:noDecoration` | `Boolean` | true일 경우 구성 요소는 자동으로 생성된 div 및 css 클래스로 렌더링되지 않습니다. |
| `cq:template` | `nt:unstructured` | 구성 요소가 있는 경우 이 노드는 구성 요소 브라우저에서 구성 요소를 추가할 때 컨텐츠 템플릿으로 사용됩니다. |
| `jcr:created` | `Date` | 구성 요소 생성 날짜입니다. |
| `jcr:description` | `String` | 구성 요소에 대한 설명입니다. |
| `jcr:title` | `String` | 구성 요소의 제목입니다. |
| `sling:resourceSuperType` | `String` | 이 설정을 지정하면 구성 요소가 이 구성 요소에서 상속됩니다. |
| `component.html` | `nt:file` | 구성 요소의 HTL 스크립트 파일입니다. |
| `cq:icon` | `String` | 이 값은 구성 요소](#component-icon)의 [아이콘을 가리키고 구성 요소 브라우저에 표시됩니다. |

**Text** 구성 요소를 보면 다음 요소의 수가 표시됩니다.

![텍스트 구성 요소 구조](assets/components-text.png)

특정 관심 영역의 속성은 다음과 같습니다.

* `jcr:title` - 구성 요소 브라우저 내에서 구성 요소를 식별하는 데 사용되는 구성 요소의 제목입니다.
* `jcr:description` - 구성 요소에 대한 설명입니다.
* `sling:resourceSuperType` - 구성 요소를 확장할 때(정의를 재정의하여) 상속의 경로를 나타냅니다.

특정 관심 영역의 하위 노드에는 다음이 포함됩니다.

* `cq:editConfig` - 편집 시 구성 요소의 시각적 측면을 제어합니다.
* `cq:dialog` - 이 구성 요소의 컨텐츠를 편집할 수 있는 대화 상자를 정의합니다.
* `cq:design_dialog` - 이 구성 요소의 디자인 편집 옵션을 지정합니다.

### 대화 상자 {#dialogs}

대화 상자는 작성자가 컨텐츠 페이지에서 구성 요소를 구성하고 해당 구성 요소에 대한 입력을 제공하는 인터페이스를 제공할 때 구성 요소의 주요 요소입니다. 컨텐츠 작성자가 구성 요소와 상호 작용하는 방법에 대한 자세한 내용은 [작성 설명서](/help/sites-cloud/authoring/fundamentals/editing-content.md)를 참조하십시오.

구성 요소의 복잡성에 따라 대화 상자에 하나 이상의 탭이 필요할 수 있습니다.

AEM 구성 요소의 대화 상자:

* `nt:unstructured` 유형의 `cq:dialog` 노드입니다.
* 은 해당 `cq:Component` 노드 아래에 있고 해당 구성 요소 정의 옆에 있습니다.
* 이 구성 요소의 컨텐츠를 편집할 대화 상자를 정의합니다.
* Granite UI 구성 요소를 사용하여 정의됩니다.
* 컨텐츠 구조 및 `sling:resourceType` 속성을 기반으로 서버측에서 렌더링됩니다(Sling 구성 요소).
* 대화 상자 내의 필드를 설명하는 노드 구조를 포함합니다
   * 이러한 노드는 필요한 `sling:resourceType` 속성이 있는 `nt:unstructured`입니다.

![제목 구성 요소의 대화 상자 정의](assets/components-title-dialog.png)

대화 상자 내에서 개별 필드가 정의됩니다.

![제목 구성 요소의 대화 상자 정의 필드](assets/components-title-dialog-items.png)

### 디자인 대화 상자 {#design-dialogs}

디자인 대화 상자는 컨텐츠를 편집하고 구성하는 데 사용되는 대화 상자와 유사하지만, 템플릿 작성자가 페이지 템플릿에서 해당 구성 요소에 대한 디자인 세부 사항을 사전 구성하고 제공하는 인터페이스를 제공합니다. 그런 다음 컨텐츠 작성자가 페이지 템플릿을 사용하여 컨텐츠 페이지를 만듭니다. 템플릿 생성 방법에 대한 자세한 내용은 [템플릿 설명서](/help/sites-cloud/authoring/features/templates.md)를 참조하십시오.

[디자인 대화 상자는 모든 구성 요소에](/help/sites-cloud/authoring/features/templates.md) 필요한 것은 아니지만 페이지 템플릿을 편집할 때 사용됩니다. 예를 들어 **제목** 및 **이미지 구성 요소**&#x200B;에는 모두 디자인 대화 상자가 있지만, **소셜 미디어 공유 구성 요소**&#x200B;에는 디자인 대화 상자가 없습니다.

### Coral UI 및 Granite UI {#coral-and-granite}

Coral UI 및 Granite UI는 AEM의 모양과 느낌을 정의합니다.

* [Coral ](https://opensource.adobe.com/coral-spectrum/documentation/) UI는 모든 클라우드 솔루션에서 일관된 UI를 제공합니다.
* [Granite ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/granite-ui/api/jcr_root/libs/granite/ui/index.html) UI는 UI 콘솔 및 대화 상자를 빌드하기 위해 Sling 구성 요소에 래핑된 Coral UI 마크업을 제공합니다.

Granite UI는 작성 환경에서 대화 상자를 만드는 데 필요한 다양한 기본 위젯을 제공합니다. 필요한 경우 이 선택 사항을 확장하고 고유한 위젯을 만들 수 있습니다.

자세한 내용은 다음 리소스를 참조하십시오.

* [AEM UI의 구조](/help/implementing/developing/introduction/ui-structure.md)

### 대화 상자 필드 사용자 지정 {#customizing-dialog-fields}

<!--
Content not found

>[!TIP]
>
>See the [AEM Gems session](https://docs.adobe.com/content/ddc/en/gems/customizing-dialog-fields-in-touch-ui.html) on customizing dialog fields.
-->

구성 요소 대화 상자에서 사용할 새 위젯을 만들려면 새로운 Granite UI 필드 구성 요소를 만들어야 합니다.

대화 상자를 양식 요소의 단순 컨테이너로 간주하는 경우 대화 상자 컨텐츠의 기본 컨텐츠를 양식 필드로 볼 수도 있습니다. 새 양식 필드를 만들려면 리소스 유형을 만들어야 합니다.이는 새 구성 요소를 만드는 것과 같습니다. 해당 작업을 지원하기 위해 Granite UI는 상속할 일반 필드 구성 요소를 제공합니다(`sling:resourceSuperType` 사용).

`/libs/granite/ui/components/coral/foundation/form/field`

특히 Granite UI는 대화 상자에서 사용하거나 일반적으로 [forms에서 사용하는 데 적합한 다양한 필드 구성 요소를 제공합니다.](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/granite-ui/api/jcr_root/libs/granite/ui/components/foundation/form/index.html)

리소스 유형을 만들면 방금 도입한 리소스 유형을 참조하는 `sling:resourceType` 속성을 사용하여 대화 상자에서 새 노드를 추가하여 필드를 인스턴스화할 수 있습니다.

#### 대화 상자 필드에 액세스 {#access-to-dialog-fields}

또한 렌더링 조건(`rendercondition`)을 사용하여 대화 상자의 특정 탭/필드에 액세스할 수 있는 사용자를 제어할 수도 있습니다.예:

```text
+ mybutton
  - sling:resourceType = granite/ui/components/coral/foundation/button
  + rendercondition
    - sling:resourceType = myapp/components/renderconditions/group
    - groups = ["administrators"]
```

## 구성 요소 {#using-components} 사용

구성 요소를 만든 후 사용하려면 구성 요소를 활성화해야 합니다. 사용 시 구성 요소의 구조가 저장소의 결과 컨텐츠 구조와 관련되는 방식을 보여줍니다.

### 템플릿에 구성 요소 추가 {#adding-your-component-to-the-template}

구성 요소가 정의되면 사용할 수 있도록 해야 합니다. 템플릿에 사용할 구성 요소를 사용할 수 있도록 하려면 템플릿의 레이아웃 컨테이너 정책에서 구성 요소를 활성화해야 합니다.

템플릿 생성 방법에 대한 자세한 내용은 [템플릿 설명서](/help/sites-cloud/authoring/features/templates.md)를 참조하십시오.

### 구성 요소 및 구성 요소가 만드는 컨텐츠 {#components-and-the-content-they-create}

페이지에서 **제목** 구성 요소의 인스턴스를 만들고 구성하는 경우:`/content/wknd/language-masters/en/adventures/extreme-ironing.html`

![제목 편집 대화 상자](assets/components-title-dialog.png)

저장소 내에서 만들어진 컨텐츠의 구조를 확인할 수 있습니다.

![제목 구성 요소 노드 구조](assets/components-title-content-nodes.png)

특히 **제목 구성 요소**&#x200B;의 실제 텍스트를 보면

* 컨텐츠에는 작성자가 입력한 제목의 실제 텍스트를 포함하는 `jcr:title` 속성이 포함되어 있습니다.
* 또한 구성 요소 정의에 대한 `sling:resourceType` 참조가 포함되어 있습니다.

정의된 속성은 개별 정의에 따라 다릅니다. 비록 그것들이 위보다 더 복잡할 수 있지만 그들은 여전히 같은 기본 원칙을 따르고 있습니다.

## 구성 요소 계층 및 상속 {#component-hierarchy-and-inheritance}

AEM 내의 구성 요소는 **리소스 유형 계층 구조**&#x200B;를 따릅니다. 이 확장은 `sling:resourceSuperType` 속성을 사용하여 구성 요소를 확장하는 데 사용됩니다. 이렇게 하면 구성 요소가 다른 구성 요소에서 상속될 수 있습니다.

자세한 내용은 [구성 요소 재사용](#reusing-components) 섹션을 참조하십시오.

## 동작 편집 {#edit-behavior}

이 섹션에서는 구성 요소의 편집 동작을 구성하는 방법을 설명합니다. 여기에는 구성 요소에 사용할 수 있는 작업, in.place 편집기의 특성 및 구성 요소의 이벤트와 관련된 청취자와 같은 특성이 포함됩니다.

구성 요소의 편집 동작은 구성 요소 노드(유형 `cq:Component`)의 아래에 `cq:EditConfig` 유형의 `cq:editConfig` 노드를 추가하고 특정 속성 및 하위 노드를 추가하여 구성됩니다. 다음 속성 및 하위 노드를 사용할 수 있습니다.

* `cq:editConfig` 노드 속성
* [`cq:editConfig` 하위 노드](#configuring-with-cq-editconfig-child-nodes):
   * `cq:dropTargets` (노드 유형  `nt:unstructured`):컨텐츠 파인더의 자산에서 드롭을 허용할 수 있는 드롭 대상 목록을 정의합니다(단일 드롭 대상이 허용됨).
   * `cq:inplaceEditing` (노드 유형  `cq:InplaceEditingConfig`):구성 요소에 대한 즉석 편집 구성 정의
   * `cq:listeners` (노드 유형  `cq:EditListenersConfig`):구성 요소에서 작업이 발생하기 전이나 후에 수행되는 작업을 정의합니다

AEM에는 기존 구성이 많습니다. **CRXDE Lite**&#x200B;에서 쿼리 도구를 사용하여 특정 속성 또는 하위 노드를 쉽게 검색할 수 있습니다.

### 구성 요소 자리 표시자 {#component-placeholders}

구성 요소에 컨텐츠가 없는 경우에도 구성 요소는 항상 작성자가 볼 수 있는 일부 HTML을 렌더링해야 합니다. 그렇지 않으면 편집기 인터페이스에서 보이지 않게 되어 기술적으로 페이지 및 편집기에서 보이지 않게 될 수 있습니다. 이러한 경우 작성자는 빈 구성 요소를 선택하고 상호 작용할 수 없습니다.

이러한 이유로, 페이지가 페이지 편집기에서 렌더링될 때(WCM 모드가 `edit` 또는 `preview`인 경우) 보이는 출력을 렌더링하지 않는 한 구성 요소는 자리 표시자를 렌더링해야 합니다.
자리 표시자에 대한 일반적인 HTML 마크업은 다음과 같습니다.

```HTML
<div class="cq-placeholder" data-emptytext="Component Name"></div>
```

위의 자리 표시자 HTML을 렌더링하는 일반적인 HTL 스크립트는 다음과 같습니다.

```HTML
<div class="cq-placeholder" data-emptytext="${component.properties.jcr:title}"
     data-sly-test="${(wcmmode.edit || wcmmode.preview) && isEmpty}"></div>
```

이전 예에서 `isEmpty`은 구성 요소에 컨텐츠가 없고 작성자에게 표시되지 않는 경우에만 true인 변수입니다.

반복을 방지하기 위해 Adobe은 구성 요소 구현자가 코어 구성 요소에서 제공하는 것과 마찬가지로 [이러한 자리 표시자에 대해 HTL 템플릿을 사용하는 것을 권장합니다.](https://github.com/adobe/aem-core-wcm-components/blob/master/content/src/content/jcr_root/apps/core/wcm/components/commons/v1/templates.html)

이전 링크에서 템플릿 사용은 다음 HTL 줄로 수행됩니다.

```HTML
<sly data-sly-use.template="core/wcm/components/commons/v1/templates.html"
     data-sly-call="${template.placeholder @ isEmpty=!model.text}"></sly>
```

이전 예에서 `model.text`은 컨텐츠에 컨텐츠가 있고 가 볼 때만 true인 변수입니다.

이 템플릿의 사용 예는 제목 구성 요소에서와 같이, [핵심 구성 요소에서 볼 수 있습니다.](https://github.com/adobe/aem-core-wcm-components/blob/master/content/src/content/jcr_root/apps/core/wcm/components/title/v2/title/title.html#L27)

### cq:EditConfig 하위 노드를 사용하여 구성 {#configuring-with-cq-editconfig-child-nodes}

#### 대화 상자에 자산 놓기 - cq:dropTargets {#cq-droptargets}

`cq:dropTargets` 노드(노드 유형 `nt:unstructured`)는 컨텐츠 파인더에서 드래그한 자산에서 드롭을 허용할 수 있는 드롭 대상을 정의합니다. `cq:DropTargetConfig` 유형의 노드입니다.

`cq:DropTargetConfig` 유형의 하위 노드는 구성 요소에 드롭 대상을 정의합니다.

### 즉석 편집 - cq:inplaceEditing {#cq-inplaceediting}

즉석 편집기를 사용하면 대화 상자를 열지 않고도 컨텐츠 플로우에서 직접 컨텐츠를 편집할 수 있습니다. 예를 들어, 표준 **텍스트** 및 **제목** 구성 요소 모두 즉석 편집기가 있습니다.

즉석 편집기는 모든 구성 요소 유형에 필요하지/의미가 없습니다.

`cq:inplaceEditing` 노드(노드 유형 `cq:InplaceEditingConfig`)는 구성 요소에 대한 즉석 편집 구성을 정의합니다. 여기에는 다음 속성이 있을 수 있습니다.

| 속성 이름 | 속성 유형 | 속성 값 |
|---|---|---|
| `active` | `Boolean` | `true` 구성 요소의 즉석 편집을 활성화하려면 |
| `configPath` | `String` | 구성 노드에서 지정할 수 있는 편집기 구성의 경로입니다 |
| `editorType` | `String` | 사용 가능한 유형은 다음과 같습니다.`plaintext` 비 HTML 컨텐츠의 경우 `title`은 편집을 시작하기 전에 그래픽 제목을 일반 텍스트로 변환하고 `text`는 리치 텍스트 편집기를 사용합니다 |

다음 구성은 구성 요소의 즉석 편집을 활성화하고 `plaintext`을 편집기 유형으로 정의합니다.

```text
    <cq:inplaceEditing
        jcr:primaryType="cq:InplaceEditingConfig"
        active="{Boolean}true"
        editorType="plaintext"/>
```

### 필드 이벤트 처리 - cq:listener {#cq-listeners}

대화 상자 필드의 이벤트 처리 방법은 사용자 지정 [클라이언트 라이브러리에 있는 리스너를 사용하여 수행됩니다.](/help/implementing/developing/introduction/clientlibs.md)

필드에 논리를 삽입하려면 다음을 수행해야 합니다.

* 필드에 주어진 CSS 클래스(후크)가 표시됩니다.
* 클라이언트 라이브러리에서 해당 CSS 클래스 이름에 연결된 JS 리스너를 정의합니다. 이렇게 하면 사용자 지정 논리 범위가 필드에만 적용되며 동일한 유형의 다른 필드에 영향을 주지 않습니다.

이를 위해서는 상호 작용할 기본 위젯 라이브러리에 대해 알고 있어야 합니다. [반응할 ](https://opensource.adobe.com/coral-spectrum/documentation/) 이벤트를 식별하려면 Coral UI 설명서를 참조하십시오.

`cq:listeners` 노드(노드 유형 `cq:EditListenersConfig`)는 구성 요소에 대한 작업 전후에 발생하는 작업을 정의합니다. 다음 표에서는 가능한 속성을 정의합니다.

| 속성 이름 | 속성 값 |
|---|---|
| `beforedelete` | 구성 요소가 제거되기 전에 처리기가 트리거됩니다. |
| `beforeedit` | 구성 요소를 편집하기 전에 처리기가 트리거됩니다. |
| `beforecopy` | 구성 요소를 복사하기 전에 처리기가 트리거됩니다. |
| `beforeremove` | 구성 요소를 이동하기 전에 처리기가 트리거됩니다. |
| `beforeinsert` | 구성 요소가 삽입되기 전에 처리기가 트리거됩니다. |
| `beforechildinsert` | 구성 요소가 다른 구성 요소(컨테이너만 해당) 내에 삽입되기 전에 처리기가 트리거됩니다. |
| `afterdelete` | 구성 요소가 제거되면 처리기가 트리거됩니다. |
| `afteredit` | 구성 요소를 편집한 후 처리기가 트리거됩니다. |
| `aftercopy` | 구성 요소가 복사된 후 처리기가 트리거됩니다. |
| `afterinsert` | 구성 요소가 삽입되면 처리기가 트리거됩니다. |
| `aftermove` | 구성 요소가 이동되면 처리기가 트리거됩니다. |
| `afterchildinsert` | 구성 요소가 다른 구성 요소(컨테이너만 해당) 내에 삽입되면 처리기가 트리거됩니다. |

>[!NOTE]
>
>중첩된 구성 요소의 경우 `cq:listeners` 노드에서 속성으로 정의된 작업에 특정 제한이 있습니다. 중첩된 구성 요소의 경우 다음 속성 **의 값은**&#x200B;이 `REFRESH_PAGE`여야 합니다.
>
>* `aftermove`
>* `aftercopy`


이벤트 핸들러는 사용자 지정 구현으로 구현할 수 있습니다. 예를 들어 `project.customerAction`이 정적 메서드인 경우:

`afteredit = "project.customerAction"`

다음 예는 `REFRESH_INSERTED` 구성과 같습니다.

`afterinsert="function(path, definition) { this.refreshCreated(path, definition); }"`

다음 구성을 사용하면 구성 요소가 삭제, 편집, 삽입 또는 이동한 후 페이지를 새로 고칩니다.

```text
    <cq:listeners
        jcr:primaryType="cq:EditListenersConfig"
        afterdelete="REFRESH_PAGE"
        afteredit="REFRESH_PAGE"
        afterinsert="REFRESH_PAGE"
        afterMove="REFRESH_PAGE"/>
```

### 필드 유효성 검사 {#field-validation}

Granite UI 및 Granite UI 위젯의 필드 유효성 검사는 `foundation-validation` API를 사용하여 수행됩니다. 자세한 내용은 [`foundation-valdiation` Granite 설명서](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/granite-ui/api/jcr_root/libs/granite/ui/components/coral/foundation/clientlibs/foundation/js/validation/index.html)를 참조하십시오.

### 대화 상자 {#dialog-ready} 가용성 검색

대화 상자를 사용할 수 있고 준비할 때만 실행해야 하는 사용자 지정 JavaScript가 있는 경우 `dialog-ready` 이벤트를 수신해야 합니다.

이 이벤트는 대화 상자가 로드(또는 다시 로드)될 때마다 트리거되며, 사용할 준비가 될 때마다(즉, 대화 상자의 DOM에 변경(만들기/업데이트)이 있을 때마다 트리거됩니다.

`dialog-ready` 대화 상자 또는 유사한 작업 내의 필드에서 사용자 지정을 수행하는 JavaScript 사용자 지정 코드를 후크하는 데 사용할 수 있습니다.

## 미리 보기 동작 {#preview-behavior}

페이지를 새로 고치지 않아도 미리 보기 모드로 전환할 때 [WCM 모드](https://docs.adobe.com/content/help/en/experience-manager-cloud-service-javadoc/com/day/cq/wcm/api/WCMMode.html) 쿠키가 설정됩니다.

WCM 모드에 민감한 렌더링을 사용하는 구성 요소의 경우 특별히 새로 고친 다음, 쿠키의 값에 의존하도록 정의해야 합니다.

## 구성 요소 {#documenting-components} 문서화

개발자는 구성 요소의 다음 내용을 빠르게 이해할 수 있도록 구성 요소 설명서에 쉽게 액세스하려고 합니다.

* 설명
* 목적
* 컨텐츠 구조 및 속성
* 노출된 API 및 확장 지점
* 기타

이러한 이유로 구성 요소 자체 내에서 사용 가능한 모든 기존 설명서 Markdown을 만드는 것은 매우 쉽습니다.

구성 요소 구조에 `README.md` 파일을 배치하기만 하면 됩니다.

![구성 요소 구조의 README.md](assets/components-documentation.png)

그러면 이 markdown이 [구성 요소 콘솔에 표시됩니다.](/help/sites-cloud/authoring/features/components-console.md)

![구성 요소 콘솔에 표시되는 README.md](assets/components-documentation-console.png)

지원되는 Markdown은 [컨텐츠 조각에 대한 markdown과 동일합니다.](/help/assets/content-fragments/content-fragments.md)
