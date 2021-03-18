---
title: 구성 요소 참조 안내서
description: 구성 요소 및 해당 구조에 대한 세부 사항에 대한 개발자 참조 가이드
translation-type: tm+mt
source-git-commit: f9a6dbec25b8154fda8069ff213aaaaa1d443ca1
workflow-type: tm+mt
source-wordcount: '3675'
ht-degree: 1%

---


# 구성 요소 참조 안내서 {#components-reference-guide}

구성 요소는 AEM에서 경험을 구축하는 데 있어 핵심입니다. [핵심 구성 요소](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html) 및 [AEM 프로젝트 원형](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html)을 사용하면 미리 만들어진 강력한 구성 요소 세트로 쉽게 시작할 수 있습니다. [WKND 자습서](/help/implementing/developing/introduction/develop-wknd-tutorial.md)에서는 개발자에게 이러한 도구를 사용하는 방법과 새 AEM 사이트를 만들기 위해 사용자 정의 구성 요소를 빌드하는 방법을 안내합니다.

>[!TIP]
>
>이 문서를 참조하기 전에 [WKND 자습서](/help/implementing/developing/introduction/develop-wknd-tutorial.md)를 완료했는지 확인하십시오. 그러므로 [핵심 구성 요소](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html) 및 [AEM 프로젝트 전형.](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html)

WKND 튜토리얼은 대부분의 사용 사례를 다룹니다. 이 문서는 이러한 리소스에 대한 보충 내용으로만 사용하기 위함입니다. 이 가이드는 구성 요소가 AEM에서 구조화되고 구성되어 있으며 시작하기 안내서로 의도하지 않은 방법에 대한 자세한 기술 설명을 제공합니다.

## 개요 {#overview}

이 섹션에서는 구성 요소를 개발할 때 필요한 세부 사항을 소개하기 위해 주요 개념 및 문제를 다룹니다.

### 계획 {#planning}

구성 요소를 실제로 구성하거나 코드를 지정하기 전에 다음을 수행해야 합니다.

* 새 구성 요소를 사용하려면 정확히 무엇을 해야 합니까?
* 구성 요소를 처음부터 새로 만들어야 합니까? 아니면 기존 구성 요소에서 기본 사항을 상속할 수 있습니까?
* 구성 요소에 컨텐츠를 선택/조작하는 논리가 필요합니까?
   * 로직은 사용자 인터페이스 레이어와 분리되어야 합니다. HTL은 이러한 상황을 보장할 수 있도록 설계되었습니다.
* 구성 요소에 CSS 형식이 필요합니까?
   * CSS 서식은 구성 요소 정의와 분리되어야 합니다. 외부 CSS 파일을 통해 수정할 수 있도록 HTML 요소의 이름을 지정하는 규칙을 정의합니다.
* 새로운 구성 요소의 보안 관련 이점은 무엇입니까?

### 기존 구성 요소 다시 사용 {#reusing-components}

완전히 새로운 구성 요소를 만드는 데 시간을 투자하려면 기존 구성 요소를 사용자 정의하거나 확장하십시오. [핵심 ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html) 구성 요소는 유연하고 강력하며 테스트를 잘 거친 프로덕션 지원 구성 요소를 제공합니다.

#### 핵심 구성 요소 확장 {#extending-core-components}

핵심 구성 요소는 또한 [명확한 사용자 지정 패턴](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/customizing.html)을 제공하여 프로젝트에 맞게 사용자 정의할 수 있습니다.

#### 구성 요소 오버레이 {#overlying-components}

구성 요소를 검색 경로 로직을 기준으로 [overlay](/help/implementing/developing/introduction/overlays.md)로 재정의할 수도 있습니다. 그러나 이러한 경우 [Sling 리소스 합병](/help/implementing/developing/introduction/sling-resource-merger.md)은 트리거되지 않으며 `/apps`는 전체 오버레이를 정의해야 합니다.

#### 구성 요소 대화 상자 확장 {#extending-component-dialogs}

또한 Sling 리소스 합병을 사용하고 속성 `sling:resourceSuperType`을 정의하여 구성 요소 대화 상자를 재정의할 수 있습니다.

즉, 전체 대화 상자를 다시 정의하는 대신 필요한 차이점을 재정의하기만 하면 됩니다.

### 내용 논리 및 렌더링 마크업 {#content-logic-and-rendering-markup}

구성 요소가 [HTML로 렌더링됩니다.](https://www.w3schools.com/htmL/html_intro.asp) 구성 요소는 필요한 컨텐츠를 가져온 다음 필요에 따라 작성자 및 게시 환경 모두에서 렌더링하는 데 필요한 HTML을 정의해야 합니다.

구성 요소의 컨텐츠를 선택하는 데 사용되는 논리를 제어하는 코드와 마크업 및 렌더링을 별도로 코드 작업을 유지하는 것이 좋습니다.

이 철학은 기본 비즈니스 로직을 정의하는 데 실제 프로그래밍 언어가 사용되도록 의도적으로 제한된 템플릿 언어인 [HTL](https://experienceleague.adobe.com/docs/experience-manager-htl/using/overview.html)에서 지원합니다. 이 메커니즘은 지정된 보기에 대해 호출되는 코드를 강조 표시하고 필요한 경우 동일한 구성 요소의 다른 보기에 대한 특정 논리를 허용합니다.

이(선택 사항) 로직은 다른 방식으로 구현될 수 있으며 특정 명령을 사용하여 HTL에서 호출됩니다.

* Java 사용 - [HTL Java Use-API](https://helpx.adobe.com/experience-manager/htl/using/use-api-java.html)를 사용하면 HTL 파일이 사용자 지정 Java 클래스의 도우미 메서드에 액세스할 수 있습니다. 이렇게 하면 Java 코드를 사용하여 구성 요소 컨텐츠를 선택하고 구성하는 논리를 구현할 수 있습니다.
* JavaScript 사용 - [HTL JavaScript Use-API](https://experienceleague.adobe.com/docs/experience-manager-htl/using/htl/use-api-javascript.html)를 사용하면 HTML 파일이 JavaScript로 작성된 헬퍼 코드에 액세스할 수 있습니다. 이렇게 하면 JavaScript 코드를 사용하여 구성 요소 컨텐츠를 선택하고 구성하기 위한 논리를 구현할 수 있습니다.
* 클라이언트측 라이브러리 사용 - 최신 웹 사이트에서는 복잡한 JavaScript 및 CSS 코드를 기반으로 하는 클라이언트측 처리에 상당히 의존합니다. 자세한 내용은 [AEM에서 클라이언트측 라이브러리를 Cloud Service](/help/implementing/developing/introduction/clientlibs.md)로 사용을 참조하십시오.

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
* 리소스 유형이 이를 구현합니다.

이것은 시간이 지남에 따라 모양과 느낌이 바뀔 때에도 의도가 시간을 유지하는 것을 보장하는 추상화이다.

### 구성 요소 정의 {#component-definition}

구성 요소의 정의는 다음과 같이 분류할 수 있습니다.

* AEM 구성 요소는 [Sling을 기반으로 합니다.](https://sling.apache.org/documentation.html)
* AEM 구성 요소는 `/libs/core/wcm/components` 아래에 있습니다.
* 프로젝트/사이트별 구성 요소는 `/apps/<myApp>/components` 아래에 있습니다.
* AEM 표준 구성 요소는 `cq:Component`으로 정의되고 주요 요소가 있습니다.
   * jcr 속성 - jcr 속성 목록입니다. 구성 요소 노드의 기본 구조, 속성 및 하위 노드가 `cq:Component` 정의로 정의되더라도 이러한 변수 및 일부는 선택 사항일 수 있습니다.
   * 리소스 - 구성 요소에서 사용하는 정적 요소를 정의합니다.
   * 스크립트 - 구성 요소의 결과 인스턴스의 동작을 구현하는 데 사용됩니다.

#### 중요 속성 {#vital-properties}

* **루트 노드**:
   * `<mycomponent> (cq:Component)` - 구성 요소의 계층 노드.
* **중요 속성**:
   * `jcr:title` - 구성 요소 제목;예를 들어 구성 요소가  [구성 요소 찾아보기 및 구성 요소 콘솔에 나열될 때 레이블로 ](/help/sites-cloud/authoring/fundamentals/environment-tools.md#components-browser)  [사용됩니다.](/help/sites-cloud/authoring/features/components-console.md)
   * `jcr:description` - 구성 요소에 대한 설명;구성 요소 브라우저 및 구성 요소 콘솔에서 마우스 오버 힌트로 사용됨
   * 자세한 내용은 [구성 요소 아이콘](#component-icon) 섹션을 참조하십시오.
* **중요 하위 노드**:
   * `cq:editConfig (cq:EditConfig)` - 구성 요소의 편집 속성을 정의하고 구성 요소 브라우저에 구성 요소를 표시할 수 있습니다.
      * 구성 요소에 대화 상자가 있으면 cq:editConfig가 없더라도 구성 요소 브라우저나 사이드 킥에 자동으로 나타납니다.
   * `cq:childEditConfig (cq:EditConfig)` - 자체 UI를 정의하지 않는 하위 구성 요소에 대한 작성자 UI 측면을 제어합니다 `cq:editConfig`.
   * `cq:dialog (nt:unstructured)` - 이 구성 요소에 대한 대화 상자 사용자가 구성 요소를 구성하고 컨텐츠를 편집할 수 있는 인터페이스를 정의합니다.
   * `cq:design_dialog (nt:unstructured)` - 이 구성 요소에 대한 디자인 편집

#### 구성 요소 아이콘 {#component-icon}

구성 요소의 아이콘 또는 약어는 개발자가 구성 요소를 만들 때 구성 요소의 JCR 속성을 통해 정의됩니다. 이러한 속성은 다음 순서로 평가되며 발견된 첫 번째 유효한 속성이 사용됩니다.

1. `cq:icon` - 구성 요소 브라우저에 표시할  [Coral UI ](https://opensource.adobe.com/coral-spectrum/examples/#icon) 라이브러리의 표준 아이콘을 가리키는 문자열 속성
   * Coral 아이콘의 HTML 속성 값을 사용합니다.
1. `abbreviation` - 구성 요소 브라우저에서 구성 요소 이름의 약어를 사용자 지정하는 문자열 속성
   * 약어는 2자로 제한되어야 합니다.
   * 빈 문자열을 제공하면 `jcr:title` 속성의 처음 2자에서 약어가 만들어집니다.
      * 예: &quot;Image&quot;의 &quot;Im&quot;
      * 현지화된 제목이 약어를 작성하는 데 사용됩니다.
   * 약어는 구성 요소에 번역 힌트로 사용되는 `abbreviation_commentI18n` 속성이 있는 경우에만 변환됩니다.
1. `cq:icon.png` 또는  `cq:icon.svg` - 구성 요소 브라우저에 표시되는 이 구성 요소의 아이콘
   * 20 x 20픽셀은 표준 구성 요소의 아이콘 크기입니다.
      * 더 큰 아이콘은 축소됩니다(클라이언트측).
   * 권장되는 색상은 rgb(112, 112, 112) > #707070
   * 표준 구성 요소 아이콘의 배경은 투명합니다.
   * `.png` 및 `.svg` 파일만 지원됩니다.
   * 예를 들어 Eclipse 플러그인을 통해 파일 시스템에서 가져올 경우 파일 이름을 `_cq_icon.png` 또는 `_cq_icon.svg`로 이스케이프해야 합니다.
   * `.png` 둘 다  `.svg` 있으면 선례를 맡는다.

위 속성(`cq:icon`, `abbreviation`, `cq:icon.png` 또는 `cq:icon.svg`)이 구성 요소에 없을 경우:

* `sling:resourceSuperType` 속성 다음에 있는 수퍼 구성 요소에서 동일한 속성을 검색합니다.
* 수퍼 구성 요소 수준에서 아무 약어 또는 빈 약어가 없는 경우 시스템은 현재 구성 요소의 `jcr:title` 속성의 첫 번째 문자로 약어를 작성합니다.

수퍼 구성 요소에서 아이콘 상속을 취소하려면 구성 요소에서 빈 `abbreviation` 속성을 설정하면 기본 동작으로 돌아갑니다.

[구성 요소 콘솔](/help/sites-cloud/authoring/features/components-console.md#component-details)에는 특정 구성 요소에 대한 아이콘이 정의된 방법이 표시됩니다.

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

구성 요소를 정의하는 데 필요한 많은 노드/속성은 두 UI 모두에서 공통으로 표시되며 구성 요소가 두 환경에서 모두 작동할 수 있도록 독립적 차이가 남아 있습니다.

구성 요소는 `cq:Component` 유형의 노드이며 다음 속성과 자식 노드를 가집니다.

| 이름 | 유형 | 설명 |
|---|---|---|
| `.` | `cq:Component` | 현재 구성 요소를 나타냅니다. 구성 요소는 노드 유형 `cq:Component`입니다. |
| `componentGroup` | `String` | 구성 요소 브라우저에서 구성 요소를 선택할 수 있는 그룹을 나타냅니다.[](/help/sites-cloud/authoring/fundamentals/environment-tools.md#components-browser) 다음으로 시작하는 값 `.` 은 다른 구성 요소가 상속하는 기본 구성 요소와 같이 UI에서 선택할 수 없는 구성 요소에 사용됩니다. |
| `cq:isContainer` | `Boolean` | 구성 요소가 컨테이너 구성 요소인지 여부를 나타내며 단락 시스템과 같은 다른 구성 요소를 포함할 수 있습니다. |
| `cq:dialog` | `nt:unstructured` | 구성 요소에 대한 편집 대화 상자의 정의입니다. |
| `cq:design_dialog` | `nt:unstructured` | 구성 요소에 대한 디자인 대화 상자의 정의입니다. |
| `cq:editConfig` | `cq:EditConfig` | 구성 요소의 [편집 구성을 정의합니다.](#edit-behavior) |
| `cq:htmlTag` | `nt:unstructured` | 그러면 주변 HTML 태그에 추가되는 추가 태그 속성이 반환됩니다. 자동으로 생성된 div에 속성을 추가할 수 있습니다. |
| `cq:noDecoration` | `Boolean` | true이면 구성 요소가 자동으로 생성된 div 및 css 클래스로 렌더링되지 않습니다. |
| `cq:template` | `nt:unstructured` | 구성 요소가 구성 요소 브라우저에서 추가되면 이 노드가 컨텐츠 템플릿으로 사용됩니다. |
| `jcr:created` | `Date` | 구성 요소 생성 날짜입니다. |
| `jcr:description` | `String` | 구성 요소에 대한 설명입니다. |
| `jcr:title` | `String` | 구성 요소의 제목입니다. |
| `sling:resourceSuperType` | `String` | 설정하면 구성 요소가 이 구성 요소에서 상속됩니다. |
| `component.html` | `nt:file` | 구성 요소의 HTL 스크립트 파일입니다. |
| `cq:icon` | `String` | 이 값은 구성 요소](#component-icon)의 [아이콘을 가리키며 구성 요소 브라우저에 나타납니다. |

**Text** 구성 요소를 보면 다음과 같은 요소가 많이 표시됩니다.

![텍스트 구성 요소 구조](assets/components-text.png)

특정 관심 영역의 속성은 다음과 같습니다.

* `jcr:title` - 구성 요소 브라우저 내에서 구성 요소를 식별하는 데 사용되는 구성 요소의 제목입니다.
* `jcr:description` - 구성 요소에 대한 설명입니다.
* `sling:resourceSuperType` - 정의를 재정의하여 구성 요소를 확장할 때 상속의 경로를 나타냅니다.

특정 관심 영역의 하위 노드는 다음과 같습니다.

* `cq:editConfig` - 편집 시 구성 요소의 시각적 측면을 제어합니다.
* `cq:dialog` - 이 구성 요소의 컨텐츠를 편집하기 위한 대화 상자를 정의합니다.
* `cq:design_dialog` - 이 구성 요소의 디자인 편집 옵션을 지정합니다.

### 대화 상자 {#dialogs}

대화 상자는 작성자가 컨텐츠 페이지에서 구성 요소를 구성하고 해당 구성 요소에 대한 입력을 제공하는 인터페이스를 제공하기 때문에 구성 요소의 핵심 요소입니다. 컨텐츠 작성자가 구성 요소와 상호 작용하는 방법에 대한 자세한 내용은 [작성 설명서](/help/sites-cloud/authoring/fundamentals/editing-content.md)를 참조하십시오.

구성 요소의 복잡성에 따라 대화 상자에 하나 이상의 탭이 필요할 수 있습니다.

AEM 구성 요소에 대한 대화 상자:

* `nt:unstructured` 유형의 `cq:dialog` 노드입니다.
* `cq:Component` 노드 아래에 있으며 해당 구성 요소 정의 옆에 있습니다.
* 이 구성 요소의 컨텐츠를 편집할 대화 상자를 정의합니다.
* Granite UI 구성 요소를 사용하여 정의됩니다.
* 컨텐트 구조와 `sling:resourceType` 속성을 기반으로 서버측에서 렌더링됩니다(Sling 구성 요소).
* 대화 상자 내의 필드를 설명하는 노드 구조 포함
   * 이러한 노드는 필요한 `sling:resourceType` 속성이 있는 `nt:unstructured`입니다.

![제목 구성 요소의 대화 상자 정의](assets/components-title-dialog.png)

대화 상자에서 개별 필드가 정의됩니다.

![제목 구성 요소의 대화 상자 정의 필드](assets/components-title-dialog-items.png)

### 디자인 대화 상자 {#design-dialogs}

디자인 대화 상자는 컨텐츠를 편집 및 구성하는 데 사용되는 대화 상자와 비슷하지만, 템플릿 작성자가 페이지 템플릿에서 해당 구성 요소의 디자인 세부 사항을 사전 구성하고 제공할 수 있는 인터페이스를 제공합니다. 그런 다음 컨텐츠 작성자가 페이지 템플릿을 사용하여 컨텐츠 페이지를 만듭니다. 템플릿을 만드는 방법에 대한 자세한 내용은 [템플릿 설명서](/help/sites-cloud/authoring/features/templates.md)를 참조하십시오.

[디자인 대화 상자는 모든 구성 요소에 필요한 것은 아니지만 페이지](/help/sites-cloud/authoring/features/templates.md) 템플릿을 편집할 때 사용됩니다. 예를 들어 **제목** 및 **이미지 구성 요소**&#x200B;에는 디자인 대화 상자가 있지만 **소셜 미디어 공유 구성 요소**&#x200B;에는 디자인 대화 상자가 없습니다.

### Coral UI 및 Granite UI {#coral-and-granite}

Coral UI 및 Granite UI는 AEM의 모양과 느낌을 정의합니다.

* [Coral ](https://opensource.adobe.com/coral-spectrum/documentation/) UI모든 클라우드 솔루션에서 일관된 UI를 제공합니다.
* [Granite ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/granite-ui/api/jcr_root/libs/granite/ui/index.html) UI는 UI 콘솔 및 대화 상자를 작성하기 위해 Sling 구성 요소에 래핑된 Coral UI 마크업을 제공합니다.

Granite UI는 작성 환경에서 대화 상자를 만드는 데 필요한 다양한 기본 위젯을 제공합니다. 필요한 경우 이 선택 영역을 확장하고 자신만의 위젯을 만들 수 있습니다.

자세한 내용은 다음 리소스를 참조하십시오.

* [AEM UI 구조](/help/implementing/developing/introduction/ui-structure.md)

### 대화 상자 필드 사용자 지정 {#customizing-dialog-fields}

>[!TIP]
>
>대화 상자 필드 사용자 정의에 대해서는 [AEM Gems 세션](https://docs.adobe.com/content/ddc/en/gems/customizing-dialog-fields-in-touch-ui.html)을 참조하십시오.

구성 요소 대화 상자에서 사용할 새 위젯을 만들려면 [granite UI] 필드 구성 요소를 새로 만들어야 합니다.

대화 상자를 양식 요소의 간단한 컨테이너로 간주하는 경우 대화 상자 내용의 기본 컨텐츠를 양식 필드로 볼 수도 있습니다. 새 양식 필드를 만들려면 리소스 유형을 만들어야 합니다.이는 새 구성 요소를 만드는 것과 같습니다. 이 작업을 수행하는 데 도움이 되도록 Granite UI는 상속할 일반 필드 구성 요소를 제공합니다(`sling:resourceSuperType` 사용).

`/libs/granite/ui/components/coral/foundation/form/field`

특히 [Granite UI]는 대화 상자에서 사용하거나 보다 일반적으로 [forms에서 말하는 데 적합한 다양한 필드 구성 요소를 제공합니다.](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/granite-ui/api/jcr_root/libs/granite/ui/components/foundation/form/index.html)

리소스 유형을 만든 후에는 방금 소개한 리소스 유형을 참조하는 `sling:resourceType` 속성을 사용하여 대화 상자에 새 노드를 추가하여 필드를 인스턴스화할 수 있습니다.

#### 대화 상자 필드 액세스 {#access-to-dialog-fields}

렌더링 조건(`rendercondition`)을 사용하여 대화 상자에서 특정 탭/필드에 액세스할 수 있는 사용자를 제어할 수도 있습니다.예를 들면 다음과 같습니다.

```text
+ mybutton
  - sling:resourceType = granite/ui/components/coral/foundation/button
  + rendercondition
    - sling:resourceType = myapp/components/renderconditions/group
    - groups = ["administrators"]
```

## 구성 요소 사용 {#using-components}

구성 요소를 만든 후 사용하려면 구성 요소를 활성화해야 합니다. 이 보고서를 사용하면 구성 요소의 구조가 저장소의 결과 컨텐츠 구조와 연관되는 방식을 알 수 있습니다.

### 템플릿 {#adding-your-component-to-the-template}에 구성 요소 추가

구성 요소를 정의한 후에는 사용할 수 있도록 설정해야 합니다. 템플릿에서 구성 요소를 사용할 수 있게 하려면 템플릿의 레이아웃 컨테이너 정책에 있는 구성 요소를 활성화해야 합니다.

템플릿을 만드는 방법에 대한 자세한 내용은 [템플릿 설명서](/help/sites-cloud/authoring/features/templates.md)를 참조하십시오.

### 구성 요소 및 만드는 내용 {#components-and-the-content-they-create}

페이지에서 **제목** 구성 요소의 인스턴스를 만들고 구성하는 경우:`/content/wknd/language-masters/en/adventures/extreme-ironing.html`

![제목 편집 대화 상자](assets/components-title-dialog.png)

그런 다음 저장소 내에서 만들어진 컨텐츠의 구조를 볼 수 있습니다.

![제목 구성 요소 노드 구조](assets/components-title-content-nodes.png)

특히 **제목 구성 요소**&#x200B;의 실제 텍스트를 보는 경우:

* 컨텐츠에는 작성자가 입력한 제목의 실제 텍스트를 포함하는 `jcr:title` 속성이 포함되어 있습니다.
* 구성 요소 정의에 대한 `sling:resourceType` 참조도 포함되어 있습니다.

정의된 속성은 개별 정의에 따라 다릅니다. 비록 그들은 위에 비해 더 복잡할 수 있지만, 여전히 같은 기본 원칙을 따른다.

## 구성 요소 계층 구조 및 상속 {#component-hierarchy-and-inheritance}

AEM 내의 구성 요소는 **리소스 유형 계층**&#x200B;의 적용을 받습니다. 이 속성은 `sling:resourceSuperType` 속성을 사용하여 구성 요소를 확장하는 데 사용됩니다. 이렇게 하면 구성 요소가 다른 구성 요소에서 상속될 수 있습니다.

자세한 내용은 [구성 요소 재사용](#reusing-components) 섹션을 참조하십시오.

## 비헤이비어 편집 {#edit-behavior}

이 섹션에서는 구성 요소의 편집 동작을 구성하는 방법에 대해 설명합니다. 구성 요소에 사용할 수 있는 작업, in.place 편집기의 특성, 구성 요소의 이벤트와 관련된 리스너와 같은 속성이 여기에 포함됩니다.

구성 요소의 편집 비헤이비어는 구성 요소 노드(`cq:Component` 유형) 아래에 `cq:EditConfig` 유형의 `cq:editConfig` 노드를 추가하고 특정 속성과 하위 노드를 추가하여 구성됩니다. 다음 속성과 자식 노드를 사용할 수 있습니다.

* `cq:editConfig` node 속성
* [`cq:editConfig` 하위 노드](#configuring-with-cq-editconfig-child-nodes):
   * `cq:dropTargets` (노드 유형  `nt:unstructured`):컨텐츠 파인더의 자산에서 드롭을 허용할 수 있는 드롭 대상 목록을 정의합니다(단일 드롭 타겟이 허용됨).
   * `cq:inplaceEditing` (노드 유형  `cq:InplaceEditingConfig`):구성 요소에 대한 즉석 편집 구성을 정의합니다.
   * `cq:listeners` (노드 유형  `cq:EditListenersConfig`):구성 요소에서 작업이 발생하기 전이나 후에 수행되는 작업을 정의합니다.

AEM에는 기존 구성이 많습니다. **CRXDE Lite**&#x200B;에서 쿼리 도구를 사용하여 특정 속성 또는 하위 노드를 쉽게 검색할 수 있습니다.

### 구성 요소 자리 표시자 {#component-placeholders}

구성 요소에 컨텐츠가 없는 경우에도 구성 요소는 항상 작성자가 볼 수 있는 일부 HTML을 렌더링해야 합니다. 그렇지 않으면 편집기의 인터페이스에서 시각적으로 사라져서 기술적으로 표시되지만 페이지 및 편집기에는 표시되지 않을 수 있습니다. 이 경우 작성자는 빈 구성 요소를 선택하고 상호 작용할 수 없습니다.

이러한 이유로, 페이지가 페이지 편집기에서 렌더링될 때(WCM 모드가 `edit` 또는 `preview`인 경우) 구성 요소는 표시되는 출력을 렌더링하지 않는 한 자리 표시자를 렌더링해야 합니다.
자리 표시자에 대한 일반적인 HTML 마크업은 다음과 같습니다.

```HTML
<div class="cq-placeholder" data-emptytext="Component Name"></div>
```

위의 자리 표시자 HTML을 렌더링하는 일반적인 HTL 스크립트는 다음과 같습니다.

```HTML
<div class="cq-placeholder" data-emptytext="${component.properties.jcr:title}"
     data-sly-test="${(wcmmode.edit || wcmmode.preview) && isEmpty}"></div>
```

이전 예에서 `isEmpty`은 구성 요소에 컨텐츠가 없고 작성자에게 표시되지 않을 때만 true인 변수입니다.

반복을 방지하기 위해 Adobe에서는 구성 요소 구현자가 코어 구성 요소에서 제공하는 템플릿과 마찬가지로 [이 자리 표시자에 대해 HTL 템플릿을 사용하는 것이 좋습니다.](https://github.com/adobe/aem-core-wcm-components/blob/master/content/src/content/jcr_root/apps/core/wcm/components/commons/v1/templates.html)

그런 다음 이전 링크의 템플릿 사용은 다음 HTL 행으로 수행됩니다.

```HTML
<sly data-sly-use.template="core/wcm/components/commons/v1/templates.html"
     data-sly-call="${template.placeholder @ isEmpty=!model.text}"></sly>
```

이전 예에서 `model.text`은 컨텐츠에 컨텐츠가 있고 볼 수 있을 때만 true인 변수입니다.

이 템플릿의 사용 예는 제목 구성 요소와 같이 핵심 구성 요소인 [에서 볼 수 있습니다.](https://github.com/adobe/aem-core-wcm-components/blob/master/content/src/content/jcr_root/apps/core/wcm/components/title/v2/title/title.html#L27)

### cq:EditConfig 하위 노드를 사용하여 구성 {#configuring-with-cq-editconfig-child-nodes}

#### 대화 상자에 자산 삭제 - cq:dropTargets {#cq-droptargets}

`cq:dropTargets` 노드(노드 유형 `nt:unstructured`)는 Content Finder에서 드래그한 자산에서 드롭을 허용할 수 있는 드롭 대상을 정의합니다. 이 노드는 `cq:DropTargetConfig` 유형의 노드입니다.

`cq:DropTargetConfig` 유형의 하위 노드는 구성 요소의 드롭 대상을 정의합니다.

### 즉석 편집 - cq:inplaceEditing {#cq-inplaceediting}

즉석 편집기를 사용하면 대화 상자를 열지 않고도 컨텐츠 흐름에서 바로 컨텐츠를 편집할 수 있습니다. 예를 들어 표준 **Text** 및 **Title** 구성 요소에는 모두 즉석 편집기가 있습니다.

즉석 편집기는 모든 구성 요소 유형에 필요하지 않거나 의미가 없습니다.

`cq:inplaceEditing` 노드(노드 유형 `cq:InplaceEditingConfig`)는 구성 요소에 대한 즉석 편집 구성을 정의합니다. 다음과 같은 속성을 가질 수 있습니다.

| 속성 이름 | 속성 유형 | 속성 값 |
|---|---|---|
| `active` | `Boolean` | `true` 구성 요소의 즉석 편집을 활성화합니다. |
| `configPath` | `String` | 구성 노드에서 지정할 수 있는 편집기 구성의 경로 |
| `editorType` | `String` | 사용 가능한 유형은 다음과 같습니다.HTML이 아닌 내용의 경우 `plaintext`은 편집을 시작하기 전에 그래픽 제목을 일반 텍스트로 변환하고 `text`는 리치 텍스트 편집기를 사용합니다`title` |

다음 구성은 구성 요소의 즉석 편집을 활성화하고 `plaintext`을 편집기 유형으로 정의합니다.

```text
    <cq:inplaceEditing
        jcr:primaryType="cq:InplaceEditingConfig"
        active="{Boolean}true"
        editorType="plaintext"/>
```

### 필드 이벤트 처리 - cq:listeners {#cq-listeners}

대화 상자 필드의 이벤트 처리 방법은 사용자 지정 [클라이언트 라이브러리의 리스너로 수행됩니다.](/help/implementing/developing/introduction/clientlibs.md)

필드에 논리를 삽입하려면 다음을 수행해야 합니다.

* 필드를 지정된 CSS 클래스(후크)로 표시하십시오.
* 클라이언트 라이브러리에서 해당 CSS 클래스 이름에 연결된 JS 리스너를 정의합니다. 이렇게 하면 사용자 지정 로직의 범위가 필드에만 적용되며 동일한 유형의 다른 필드에 영향을 주지 않습니다.

상호 작용하려는 기본 위젯 라이브러리에 대해 알아야 합니다. [반응할 이벤트를 ](https://opensource.adobe.com/coral-spectrum/documentation/) 식별하려면 Coral UI 문서를 참조하십시오.

`cq:listeners` 노드(노드 유형 `cq:EditListenersConfig`)는 구성 요소에 대한 작업 전후에 발생하는 상황을 정의합니다. 다음 표에서는 가능한 속성을 정의합니다.

| 속성 이름 | 속성 값 |
|---|---|
| `beforedelete` | 핸들러는 구성 요소를 제거하기 전에 트리거됩니다. |
| `beforeedit` | 핸들러는 구성 요소를 편집하기 전에 트리거됩니다. |
| `beforecopy` | 핸들러는 구성 요소가 복사되기 전에 트리거됩니다. |
| `beforeremove` | 핸들러는 구성 요소가 이동되기 전에 트리거됩니다. |
| `beforeinsert` | 핸들러는 구성 요소가 삽입되기 전에 트리거됩니다. |
| `beforechildinsert` | 핸들러는 구성 요소가 다른 구성 요소(컨테이너만 해당) 내에 삽입되기 전에 트리거됩니다. |
| `afterdelete` | 핸들러는 구성 요소가 제거된 후에 트리거됩니다. |
| `afteredit` | 핸들러는 구성 요소를 편집한 후 트리거됩니다. |
| `aftercopy` | 핸들러는 구성 요소가 복사되면 트리거됩니다. |
| `afterinsert` | 핸들러는 구성 요소가 삽입된 후 트리거됩니다. |
| `aftermove` | 핸들러는 구성 요소가 이동되면 트리거됩니다. |
| `afterchildinsert` | 핸들러는 구성 요소가 다른 구성 요소(컨테이너만 해당) 내에 삽입되면 트리거됩니다. |

>[!NOTE]
>
>중첩된 구성 요소의 경우 `cq:listeners` 노드에 속성으로 정의된 작업에 대한 특정 제한이 있습니다. 중첩된 구성 요소의 경우 다음 속성 **의 값은**&#x200B;이어야 합니다. `REFRESH_PAGE`
>
>* `aftermove`
>* `aftercopy`


이벤트 핸들러는 사용자 지정 구현으로 구현할 수 있습니다. 예를 들어 `project.customerAction`이(가) 정적 메서드인 경우:

`afteredit = "project.customerAction"`

다음 예는 `REFRESH_INSERTED` 구성에 해당합니다.

`afterinsert="function(path, definition) { this.refreshCreated(path, definition); }"`

구성 요소가 삭제, 편집, 삽입 또는 이동한 후 다음 구성을 통해 페이지가 새로 고쳐집니다.

```text
    <cq:listeners
        jcr:primaryType="cq:EditListenersConfig"
        afterdelete="REFRESH_PAGE"
        afteredit="REFRESH_PAGE"
        afterinsert="REFRESH_PAGE"
        afterMove="REFRESH_PAGE"/>
```

### 필드 유효성 검사 {#field-validation}

Granite UI 및 Granite UI 위젯의 필드 유효성 검사는 `foundation-validation` API를 사용하여 수행됩니다. 자세한 내용은 [`foundation-valdiation` Granite documentation](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/granite-ui/api/jcr_root/libs/granite/ui/components/coral/foundation/clientlibs/foundation/js/validation/index.html)을 참조하십시오.

### 대화 상자 {#dialog-ready}의 가용성 감지

대화 상자를 사용할 수 있고 사용할 준비가 되었을 때만 실행되어야 하는 사용자 지정 JavaScript가 있는 경우 `dialog-ready` 이벤트를 수신해야 합니다.

이 이벤트는 대화 상자가 로드되거나 다시 로드될 때마다 트리거되며 사용할 준비가 되어 대화 상자의 DOM에 변경(만들기/업데이트)이 있을 때마다 발생합니다.

`dialog-ready` 대화 상자 내부 필드나 유사한 작업 내의 필드에 대한 사용자 지정을 수행하는 JavaScript 사용자 지정 코드를 연결하는 데 사용할 수 있습니다.

## 미리 보기 동작 {#preview-behavior}

페이지를 새로 고치지 않아도 미리 보기 모드로 전환할 때 [WCM 모드](https://docs.adobe.com/content/help/en/experience-manager-cloud-service-javadoc/com/day/cq/wcm/api/WCMMode.html) 쿠키가 설정됩니다.

WCM 모드에 민감한 렌더링을 사용하는 구성 요소의 경우 특별히 새로 고친 다음 쿠키의 값을 사용해야 합니다.

## 구성 요소 문서화 {#documenting-components}

개발자는 구성 요소의 설명서를 쉽게 액세스하여 구성 요소의

* 설명
* 사용 목적
* 콘텐츠 구조 및 속성
* API 및 확장 지점 노출
* 기타

이러한 이유로 구성 요소 자체 내에서 사용 가능한 기존 설명서를 마크업하는 것은 매우 쉽습니다.

구성 요소 구조에 `README.md` 파일을 배치하기만 하면 됩니다.

![구성 요소 구조의 README.md](assets/components-documentation.png)

그러면 이 마크다운이 [구성 요소 콘솔에 표시됩니다.](/help/sites-cloud/authoring/features/components-console.md)

![구성 요소 콘솔에 표시되는 README.md](assets/components-documentation-console.png)

지원되는 마크다운은 [컨텐츠 조각에 대한 마크다운과 동일합니다.](/help/assets/content-fragments/content-fragments.md)