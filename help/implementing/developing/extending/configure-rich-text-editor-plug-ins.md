---
title: ' [!DNL Adobe Experience Manager]에서 리치 텍스트 편집기 플러그인을 구성합니다.'
description: ' [!DNL Adobe Experience Manager] 리치 텍스트 편집기 플러그인을 구성하는 방법에 대해 학습합니다.'
contentOwner: AG
mini-toc-levels: 1
translation-type: tm+mt
source-git-commit: 6db201f00e8f304122ca8c037998b363ff102c1f
workflow-type: tm+mt
source-wordcount: '4301'
ht-degree: 3%

---


# 리치 텍스트 편집기 플러그인 구성 {#configure-the-rich-text-editor-plug-ins}

RTE 기능은 기능 속성이 있는 일련의 플러그인을 통해 제공됩니다. 하나 이상의 RTE 기능을 활성화하거나 비활성화하도록 기능 속성을 구성할 수 있습니다. 이 문서에서는 RTE 플러그인을 구체적으로 구성하는 방법에 대해 설명합니다.

다른 RTE 구성에 대한 자세한 내용은 [리치 텍스트 편집기 구성](/help/implementing/developing/extending/rich-text-editor.md)을 참조하십시오.

>[!NOTE]
>
>CRXDE Lite 작업 시 [!UICONTROL 모두 저장] 옵션을 사용하여 변경 내용을 정기적으로 저장하는 것이 좋습니다.

## 플러그인 활성화 및 기능 속성 {#activateplugin} 구성

플러그인을 활성화하려면 다음 단계를 수행합니다. 일부 단계는 해당 노드가 없으므로 처음으로 플러그인을 구성할 때만 필요합니다.

기본적으로 `format`, `link`, `list`, `justify` 및 `control` 플러그인과 해당 모든 기능이 RTE에서 활성화됩니다.

>[!NOTE]
>
>이 아티클에서 중복을 방지하기 위해 각각의 `rtePlugins` 노드를 `<rtePlugins-node>`로 합니다.

1. CRXDE Lite을 사용하여 프로젝트의 텍스트 구성 요소를 찾습니다.
1. RTE 플러그인을 구성하기 전에 `<rtePlugins-node>`의 부모 노드가 없는 경우 만듭니다.

   * 구성 요소에 따라 상위 노드는 다음과 같습니다.

      * `config: .../text/cq:editConfig/cq:inplaceEditing/config`
      * 대체 구성 노드:`.../text/cq:editConfig/cq:inplaceEditing/inplaceEditingTextConfig`
      * `text: .../text/dialog/items/tab1/items/text`
   * 유형:**jcr:primaryType** `cq:Widget`
   * 두 속성 모두 다음 속성을 가집니다.

      * **이름** `name`
      * **유형** `String`
      * **값** `./text`


1. 구성 중인 인터페이스에 따라, 노드 `<rtePlugins-node>`이(가) 없는 경우 노드를 만듭니다.

   * **이름** `rtePlugins`
   * **유형** `nt:unstructured`

1. 아래에서 활성화할 각 플러그인에 대한 노드를 만듭니다.

   * **유형** `nt:unstructured`
   * **필수 플러그인** 의 플러그인 ID 이름

플러그인을 활성화한 후 다음 지침에 따라 `features` 속성을 구성합니다.

|  | 모든 기능 사용 | 몇 가지 특정 기능을 활성화합니다. | 모든 기능을 비활성화합니다. |
|---|---|---|---|
| 이름 | features | features | features |
| 유형 | 문자열 | `String` (multi-string;유형 `String` 을 설정하고 CRXDE Lite `Multi` 에서 클릭) | 문자열 |
| 값 | `*` (별표) | 하나 이상의 피쳐 값으로 설정합니다. | - |

## finderplace 플러그인 {#findreplace} 이해

`findreplace` 플러그인에 구성이 필요하지 않습니다. 그것은 틀리지 않는다.

바꾸기 기능을 사용할 때는 바꿀 대체 문자열을 찾기 문자열과 동시에 입력해야 합니다. 그래도 찾기 를 클릭하여 문자열을 교체하기 전에 검색할 수 있습니다. 찾기를 클릭한 후 대체 문자열을 입력하면 검색이 텍스트 시작으로 재설정됩니다.

찾기 및 바꾸기 대화 상자는 찾기를 클릭하면 투명하게 되고 바꾸기를 클릭하면 불투명해집니다. 이 동작을 통해 작성자는 바꿀 텍스트를 검토할 수 있습니다. 사용자가 모두 바꾸기를 클릭하면 대화 상자가 닫히고 교체 수가 표시됩니다.

## 붙여넣기 모드 {#pastemodes} 구성

RTE를 사용할 때 작성자는 다음 세 가지 모드 중 하나에 컨텐츠를 붙여넣을 수 있습니다.

* **브라우저 모드**:브라우저의 기본 붙여넣기 구현을 사용하여 텍스트를 붙여넣습니다. 원하지 않는 마크업을 도입할 수 있으므로 권장하지 않습니다.

* **일반 텍스트 모드**:클립보드 내용을 일반 텍스트로 붙여넣습니다. 복사한 콘텐트에서 스타일 및 서식 요소의 모든 요소를 제거하고 [!DNL Experience Manager] 구성 요소에 삽입합니다.

* **MS Word 모드**:표를 포함한 텍스트를 MS Word에서 복사할 때 서식과 함께 붙여넣습니다. 웹 페이지 또는 MS Excel과 같은 다른 소스에서 텍스트를 복사하고 붙여넣는 것은 지원되지 않으며 부분 서식만 유지합니다.

### RTE 도구 모음 {#configure-paste-options-available-on-the-rte-toolbar}에서 사용할 수 있는 붙여넣기 옵션 구성

RTE 도구 모음에서 이러한 세 가지 아이콘 중 일부, 전체 또는 하나도 작성자에게 제공할 수 없습니다.

* **[!UICONTROL 붙여넣기(Ctrl+V)]**:위의 세 가지 붙여넣기 모드 중 하나에 해당하도록 미리 구성할 수 있습니다.

* **[!UICONTROL 텍스트로 붙여넣기]**:일반 텍스트 모드 기능을 제공합니다.

* **[!UICONTROL Word에서 붙여넣기]**:MS Word 모드 기능을 제공합니다.

필요한 아이콘을 표시하도록 RTE를 구성하려면 다음 단계를 따르십시오.

1. 구성 요소로 이동합니다(예: `/apps/<myProject>/components/text`).
1. 노드 `rtePlugins/edit`으로 이동합니다. 노드가 없으면 [플러그인](#activateplugin) 활성화를 참조하십시오.
1. `edit` 노드에서 `features` 속성을 만들고 하나 이상의 기능을 추가합니다. 모든 변경 사항을 저장합니다.

### 붙여넣기(Ctrl+V) 아이콘과 단축키 {#configure-the-behavior-of-the-paste-ctrl-v-icon-and-shortcut}의 동작을 구성합니다.

다음 단계를 사용하여 **[!UICONTROL 붙여넣기(Ctrl+V)]** 아이콘의 동작을 미리 구성할 수 있습니다. 또한 이 구성은 작성자가 컨텐츠를 붙여넣는 데 사용하는 키보드 단축키 Ctrl+V의 동작도 정의합니다.

이 구성을 통해 다음과 같은 세 가지 유형의 사용 사례를 사용할 수 있습니다.

* 브라우저의 기본 붙여넣기 구현을 사용하여 텍스트를 붙여넣습니다. 원하지 않는 마크업을 도입할 수 있으므로 권장하지 않습니다. 아래의 `browser`을(를) 사용하여 구성되었습니다.

* 클립보드 내용을 일반 텍스트로 붙여넣습니다. 복사한 콘텐트에서 스타일 및 서식 요소의 모든 요소를 제거하고 [!DNL Experience Manager] 구성 요소에 삽입합니다. 아래의 `plaintext`을(를) 사용하여 구성되었습니다.

* 표를 포함한 텍스트를 MS Word에서 복사할 때 서식과 함께 붙여넣습니다. 웹 페이지 또는 MS Excel과 같은 다른 소스에서 텍스트를 복사하고 붙여넣는 것은 지원되지 않으며 부분 서식만 유지합니다. 아래의 `wordhtml`을(를) 사용하여 구성되었습니다.

1. 구성 요소에서 `<rtePlugins-node>/edit` 노드로 이동합니다. 노드가 없으면 노드를 생성합니다. 자세한 내용은 [플러그인](#activateplugin) 활성화를 참조하십시오.
1. `edit` 노드에서 다음 세부 정보를 사용하여 속성을 만듭니다.

   * **이름** `defaultPasteMode`
   * **유형** `String`
   * **값** 은  `browser`,  `plaintext`또는  `wordhtml` 모드에서 필요한 붙여넣기 모드 중 하나입니다.

### 내용 {#pasteformats}을(를) 붙여넣을 때 허용되는 형식을 구성합니다.

Paste-as-Microsoft-Word(`paste-wordhtml`) 모드는 [!DNL Microsoft Word] 등의 다른 프로그램에서 [!DNL Experience Manager]에 붙여넣을 때 몇 가지 스타일을 명시적으로 허용할 수 있도록 추가로 구성할 수 있습니다.

예를 들어 [!DNL Experience Manager]에서 붙여넣을 때 굵은체 형식 및 목록만 허용해야 하는 경우 다른 형식을 필터링할 수 있습니다. 이를 구성 가능한 붙여넣기 필터라고 하며 두 가지 모두에 대해 수행할 수 있습니다.

* [텍스트](#pastemodes)
* [링크](#linkstyles)

링크의 경우 자동으로 허용되는 프로토콜을 정의할 수도 있습니다.

텍스트를 다른 프로그램에서 [!DNL Experience Manager]에 붙여넣을 때 허용되는 형식을 구성하려면:

1. 구성 요소에서 노드 `<rtePlugins-node>/edit`으로 이동합니다. 노드가 없으면 노드를 만듭니다. 자세한 내용은 [플러그인](#activateplugin) 활성화를 참조하십시오.
1. HTML 붙여넣기 규칙을 저장할 노드를 `edit` 노드 아래에 만듭니다.

   * **이름** `htmlPasteRules`
   * **유형** `nt:unstructured`

1. `htmlPasteRules` 아래에 노드를 만들어 허용되는 기본 포맷에 대한 세부 정보를 저장합니다.

   * **이름** `allowBasics`
   * **유형** `nt:unstructured`

1. 허용되는 개별 형식을 제어하려면 `allowBasics` 노드에서 다음 속성 중 하나 이상을 만드십시오.

   * **이름** `bold`
   * **이름** `italic`
   * **이름** `underline`
   * **이름** `anchor` (링크와 지정된 앵커의 경우)
   * **이름** `image`

   모든 속성은 **Type** `Boolean`이므로 적절한 **Value**&#x200B;에서 확인 표시를 선택하거나 제거하여 기능을 활성화하거나 비활성화할 수 있습니다.

   >[!NOTE]
   >
   >명시적으로 정의되지 않은 경우 true의 기본값이 사용되고 형식이 허용됩니다.

1. 다른 형식은 다른 속성 또는 노드 범위를 사용하여 정의할 수도 있으며, 이 범위는 `htmlPasteRules` 노드에도 적용됩니다.

| 속성 | 유형 | 설명 |
|--- |--- |--- |
| `allowBlockTags` | `String` | 허용되는 블록 태그 목록을 정의합니다. 헤드라인(h1, h2, h3), 단락(p), 목록(ol, ul), 표(표)가 가능한 몇 가지 블록 태그입니다. |
| `fallbackBlockTag` | `String` | `allowBlockTags`에 포함되지 않은 블록 태그가 있는 모든 블록에 사용된 블록 태그를 정의합니다. 일반적으로 `p` 접미사가 충분합니다. |
| `table` | `nt:unstructured` | 표를 붙여넣을 때의 동작을 정의합니다. This node must have the property allow (type Boolean) to define whether pasting tables is allowed. allow가 false로 설정된 경우, 붙여넣은 테이블 컨텐츠가 처리되는 방식을 정의하려면 property ignoreMode(문자열 유형)를 지정해야 합니다. ignoreMode에 대한 유효한 값은 테이블 컨텐츠를 제거하기 위한 `remove`이고 테이블 셀을 단락으로 전환하는 `paragraph`입니다. |
| `list` | `nt:unstructured` | 목록을 붙여넣을 때의 동작을 정의합니다. 목록 붙여넣기가 허용되는지 여부를 정의하려면 속성 `allow`(부울 유형)이 있어야 합니다. `allow`이(가) `false`으로 설정된 경우 속성 `ignoreMode`(유형 `String`)을 지정하여 붙여넣은 목록 컨텐트를 처리하는 방법을 정의합니다. ignoreMode에 유효한 값은 목록 컨텐츠를 제거하는 `remove`이고 목록 항목을 단락으로 바꾸는 `paragraph`입니다. |

유효한 `htmlPasteRules` 구조의 예는 다음과 같습니다.

```xml
"htmlPasteRules": {
    "allowBasics": {
        "italic": true,
        "link": true
    },
    "allowBlockTags": [
        "p", "h1", "h2", "h3"
    ],
    "list": {
        "allow": false,
        "ignoreMode": "paragraph"
    },
    "table": {
        "allow": true,
        "ignoreMode": "paragraph"
    }
}
```

1. 모든 변경 사항을 저장합니다.

## 텍스트 스타일 구성 {#textstyles}

작성자는 스타일을 적용하여 텍스트 부분의 모양을 변경할 수 있습니다. 스타일은 CSS 스타일 시트에서 미리 정의한 CSS 클래스를 기반으로 합니다. 스타일이 지정된 컨텐츠는 CSS 클래스를 참조하는 `class` 특성을 사용하여 `span` 태그로 둘러싸여 있습니다. 예:

`<span class=monospaced>Monospaced Text Here</span>`

Styles plug-in이 처음으로 활성화되어 있으면 기본 스타일을 사용할 수 없습니다. 팝업 목록이 비어 있습니다. 작성자에게 스타일을 제공하려면 다음을 수행합니다.

* 스타일 드롭다운 선택기를 활성화합니다.
* 스타일 시트의 위치를 하나 이상 지정합니다.
* 스타일 팝업 목록에서 선택할 수 있는 개별 스타일을 지정합니다.

나중에 다시 구성하는 경우, 스타일을 더 추가하려면 지침을 따라 새 스타일 시트를 참조하고 추가 스타일을 지정합니다.

>[!NOTE]
>
>[표 또는 표 셀](configure-rich-text-editor-plug-ins.md#tablestyles)에 대해서도 스타일을 정의할 수 있습니다. 이러한 구성에는 별도의 절차가 필요합니다.

### 스타일 드롭다운 선택기 목록 {#styleselectorlist} 활성화

이렇게 하려면 스타일 플러그인을 활성화합니다.

1. 구성 요소에서 노드 `<rtePlugins-node>/styles`으로 이동합니다. 노드가 없으면 노드를 생성합니다. 자세한 내용은 [플러그인](#activateplugin) 활성화를 참조하십시오.
1. `styles` 노드에서 `features` 속성을 만듭니다.

   * **이름** `features`
   * **유형** `String`
   * **값** `*` (별표)

1. 모든 변경 사항을 저장합니다.

>[!NOTE]
>
>스타일 플러그인이 활성화되면 스타일 드롭다운 목록이 편집 대화 상자에 표시됩니다. 하지만 스타일이 구성되지 않아 목록이 비어 있습니다.

### 스타일 시트 위치 {#locationofstylesheet} 지정

그런 다음 참조할 스타일 시트의 위치를 지정합니다.

1. 텍스트 구성 요소의 루트 노드(예: `/apps/<myProject>/components/text`)로 이동합니다.
1. 속성 `externalStyleSheets`을(를) `<rtePlugins-node>`의 상위 노드에 추가합니다.

   * **이름** `externalStyleSheets`
   * **Type** `String[]` (multi-string;멀티인  **** CRXDE 클릭)
   * **값** 을 포함할 모든 스타일 시트의 경로 및 파일 이름입니다. 저장소 경로를 사용합니다.

   >[!NOTE]
   >
   >나중에 추가 스타일 시트에 대한 참조를 추가할 수 있습니다.

1. 모든 변경 사항을 저장합니다.

대화 상자(클래식 UI)에서 RTE를 사용하는 경우 리치 텍스트 편집에 최적화된 스타일 시트를 지정할 수 있습니다. 기술 제한으로 인해 편집기에서 CSS 컨텍스트가 손실되므로 이 컨텍스트를 에뮬레이트하여 WYSIWYG 환경을 개선할 수 있습니다.

리치 텍스트 편집기는 보고 편집할 다른 스타일을 제공하는 ID가 `CQrte`인 컨테이너 DOM 요소를 사용합니다.

```css
#CQ td {
// defines the style for viewing
 }
```

```css
#CQrte td {
 // defines the style for editing
 }
```

### 팝업 목록 {#stylesindropdown}에서 사용 가능한 스타일을 지정합니다.

1. 구성 요소 정의에서 [스타일 드롭다운 선택기 활성화](#styleselectorlist)에서 만든 대로 노드 `<rtePlugins-node>/styles`으로 이동합니다.
1. 노드 `styles`에서 사용 가능한 목록을 저장할 노드(`styles`라고도 함)를 만듭니다.

   * **이름** `styles`
   * **유형** `cq:WidgetCollection`

1. 개별 스타일을 나타내는 노드를 `styles` 노드 아래에 만듭니다.

   * **이름**, 이름을 지정할 수 있지만 스타일에 적합해야 합니다
   * **유형** `nt:unstructured`

1. 이 노드에 속성 `cssName`을 추가하여 CSS 클래스를 참조합니다.

   * **이름** `cssName`
   * **유형** `String`
   * **값** CSS 클래스의 이름입니다(이전 &#39;.&#39; 없이).;예를 들어 `.cssClass` 대신 `cssClass`가 사용됩니다.

1. 속성 `text`을(를) 동일한 노드에 추가합니다.선택 상자에 표시되는 텍스트를 정의합니다.

   * **이름** `text`
   * **유형** `String`
   * **값** 스타일에 대한 설명;이 나타납니다.

1. 변경 사항을 저장합니다.

   각 필수 스타일에 대해 위 단계를 반복합니다.

### 일본어 {#jpwordwrap}에서 단어 분리를 최적화하기 위해 RTE 구성

[!DNL Experience Manager]을(를) 사용하여 일본어 언어 컨텐츠를 작성하는 작성자는 공백이 필요하지 않은 줄 바꿈을 방지하기 위해 문자에 스타일을 적용할 수 있습니다. 이를 통해 작성자는 원하는 위치에서 문장이 지워질 수 있습니다. 이 기능의 스타일은 CSS 스타일 시트에서 미리 정의된 CSS 클래스를 기반으로 합니다.

작성자가 일본어 텍스트에 적용할 수 있는 스타일을 만들려면 다음 단계를 수행하십시오.

1. Create a node under the styles node. [스타일](#stylesindropdown) 지정을 참조하십시오.
   * 이름: `jpn-word-wrap`
   * 유형: `nt:unstructure`

1. CSS 클래스를 참조하기 위해 노드에 속성 `cssName`을 추가합니다. 이 클래스 이름은 일본어 단어 감싸기 기능에 예약된 이름입니다.
   * 이름: `cssName`
   * 유형: `String`
   * 값:`jpn-word-wrap`(이전 `.` 없음)

1. 속성 텍스트를 동일한 노드에 추가합니다. 값은 작성자가 스타일을 선택할 때 보는 스타일의 이름입니다.
   * 이름:`text`
*유형: 
`String`
   * 값: `Japanese word-wrap`

1. 스타일 시트를 만들고 해당 경로를 지정합니다. See [specify location of stylesheet](#locationofstylesheet). Add the following contents to the stylesheet. 원하는 대로 배경색을 변경합니다.

   ```css
   .text span.jpn-word-wrap {
       display:inline-block;
   }
   .is-edited span.jpn-word-wrap {
       background-color: #ffddff;
   }
   ```

   ![작성자가 일본어 단어 감싸기 기능을 사용할 수 있도록 스타일 시트](assets/rte_jpwordwrap_stylesheet.jpg)

## 단락 형식 {#paraformats} 구성

RTE로 제작된 모든 텍스트는 블록 태그 내에 배치됩니다. 기본값은 `<p>`입니다. `paraformat` 플러그인을 활성화하면 드롭다운 선택 목록을 사용하여 단락에 할당할 수 있는 추가 블록 태그를 지정할 수 있습니다. 단락 포맷은 올바른 블록 태그를 지정하여 단락 유형을 결정합니다. 작성자는 형식 선택기를 사용하여 선택 및 할당할 수 있습니다. 예제 블록 태그에는 표준 단락 &lt;p> 및 머리글 &lt;h1>, &lt;h2> 등이 포함됩니다.

>[!CAUTION]
>
>이 플러그인은 목록 또는 표와 같이 구조가 복잡한 컨텐츠에 적합하지 않습니다.

>[!NOTE]
>
>`<hr>` 태그와 같은 블록 태그를 단락에 할당할 수 없는 경우 `paraformat` 플러그인에 유효한 사용 사례가 아닙니다.

Paragraph Formats 플러그인이 처음 활성화되면 기본 Paragraph Formats를 사용할 수 없습니다. 팝업 목록이 비어 있습니다. 작성자에게 단락 형식을 제공하려면 다음을 수행합니다.

* [!UICONTROL 형식] 팝업 선택기 목록을 활성화합니다.
* 팝업 메뉴에서 단락 포맷으로 선택할 수 있는 블록 태그를 지정합니다.

나중에 다시 구성하는 경우, 더 많은 포맷을 추가하려면 지침 중 관련 부분만 따르십시오.

### 형식 드롭다운 선택기 {#formatselectorlist} 활성화

`paraformat` 플러그인을 활성화하려면 다음 단계를 수행합니다.

1. 구성 요소에서 노드 `<rtePlugins-node>/paraformat`으로 이동합니다. 노드가 없으면 노드를 생성합니다. 자세한 내용은 [플러그인](#activateplugin) 활성화를 참조하십시오.
1. `paraformat` 노드에서 `features` 속성을 만듭니다.

   * **이름** `features`
   * **유형** `String`
   * **값** `*` (별표)

>[!NOTE]
>
>플러그인이 추가로 구성되지 않은 경우 활성화된 기본 형식은 단락( `<p>`), 머리글 1( `<h1>`), 머리글 2( `<h2>`), 머리글 3( `<h3>`)입니다.

>[!CAUTION]
>
>RTE의 단락 형식을 구성할 때 단락 태그 &lt;p>를 서식 옵션으로 제거하지 마십시오. `<p>` 태그가 제거된 경우, 내용 작성자는 추가 형식이 구성된 경우에도 [!UICONTROL 단락 형식] 옵션을 선택할 수 없습니다.

### 사용 가능한 단락 형식 {#paraformatsindropdown} 지정

단락 포맷은 다음과 같이 선택할 수 있습니다.

1. 구성 요소 정의에서 [형식 드롭다운 선택기 활성화](#styleselectorlist)에서 만든 대로 노드 `<rtePlugins-node>/paraformat`으로 이동합니다.
1. `paraformat` 노드 아래에서 노드를 만들어 형식 목록을 유지합니다.

   * **이름** `formats`
   * **유형** `cq:WidgetCollection`

1. Create a node under the `formats` node, this hold details for an individual format:

   * **이름을 지정할** 수 있지만 형식(예: myparagraph, myheading1)에 적합해야 합니다.
   * **유형** `nt:unstructured`

1. 이 노드에 속성을 추가하여 사용되는 블록 태그를 정의합니다.

   * **이름** `tag`
   * **유형** `String`
   * **값** 형식에 대한 블록 태그;예를 들면 다음과 같습니다.p, h1, h2 등

      구분 기호를 입력할 필요는 없습니다.

1. 같은 노드에서 다른 속성을 추가하여 설명 텍스트가 드롭다운 목록에 나타나도록 합니다.

   * **이름** `description`
   * **유형** `String`
   * **값** 이 형식을 설명하는 텍스트입니다.예를 들어 단락, 머리글 1, 머리글 2 등이 있습니다. 이 텍스트는 형식 선택 목록에 표시됩니다.

1. 변경 사항을 저장합니다.

   각 필수 형식에 대해 단계를 반복합니다.

>[!CAUTION]
사용자 지정 형식을 정의하는 경우 기본 형식(`<p>`, `<h1>`, `<h2>` 및 `<h3>`)이 제거됩니다. 기본 형식이므로 `<p>` 형식을 다시 만듭니다.

## 특수 문자 {#spchar} 구성

표준 [!DNL Experience Manager] 설치에서 `misctools` 플러그인이 특수 문자(`specialchars`)에 대해 활성화되면 즉시 기본 선택 항목을 사용할 수 있습니다.예를 들어, 저작권 및 상표 심볼입니다.

RTE를 구성하여 문자 선택 가능;개별 문자를 정의하거나 전체 시퀀스를 정의할 수 있습니다.

>[!CAUTION]
특수 문자를 추가하면 기본 선택 내용이 무시됩니다. 필요한 경우 선택 영역에서 이러한 문자를 재정의합니다.

### 단일 문자 {#definesinglechar} 정의

1. 구성 요소에서 노드 `<rtePlugins-node>/misctools`으로 이동합니다. 노드가 없으면 노드를 생성합니다. 자세한 내용은 [플러그인](#activateplugin) 활성화를 참조하십시오.
1. `misctools` 노드에서 `features` 속성을 만듭니다.

   * **이름** `features`
   * **유형** `String[]`
   * **값** `specialchars`

          (또는 이 플러그인에 대한 모든 기능을 적용하는 경우 `String / *`)

1. `misctools`에서 특수 문자 구성을 저장할 노드를 만듭니다.

   * **이름** `specialCharsConfig`
   * **유형** `nt:unstructured`

1. `specialCharsConfig` 아래에서 문자 목록을 저장할 다른 노드를 만듭니다.

   * **이름** `chars`
   * **유형** `nt:unstructured`

1. `chars` 아래에서 개별 문자 정의를 저장할 노드를 추가합니다.

   * **이름** 을 지정할 수 있지만 문자를 반영해야 합니다.예를 들어, 절반
   * **유형** `nt:unstructured`

1. 이 노드에 다음 속성을 추가합니다.

   * **이름** `entity`
   * **유형** `String`
   * **필수** 문자의 HTML 표현을 값;예를 들어 분수 1 `&189;` 의 경우,

1. 변경 사항을 저장합니다.

CRXDE에서 속성을 저장하면 표현된 문자가 표시됩니다. 아래 절반의 예를 참조하십시오. 작성자가 사용할 수 있는 특수 문자를 만들려면 위 단계를 반복합니다.

![CRXDE에서 RTE ](assets/chlimage_1-106.png "도구 모음에서 사용할 수 있는 단일 문자 추가CRXDE에서 RTE 도구 모음에서 사용할 수 있도록 단일 문자 추가")

### 문자 범위 정의 {#definerangechar}

1. [단일 문자](#definesinglechar)에서 1단계부터 3단계까지의 단계를 사용하십시오.
1. `chars` 아래에서 문자 범위의 정의를 저장할 노드를 추가합니다.

   * **이름** 을 지정할 수 있지만 문자 범위를 반영해야 합니다.예를 들어 연필
   * **유형** `nt:unstructured`

1. 이 노드 아래에서(특수 문자 범위에 따라 이름 지정) 다음 두 속성을 추가합니다.

   * **이름** `rangeStart`

      **유형** `Long`
      **값** 범위 [](https://unicode.org/) 에서 첫 번째 문자의 Unicoderepresentation(십진수)

   * **이름** `rangeEnd`

      **유형** `Long`
      **값** 범위 [](https://unicode.org/) 에서 마지막 문자의 유니코드표현(십진수)

1. 변경 사항을 저장합니다.

   예를 들어 9998 - 10000에서 범위를 정의하면 다음 문자가 제공됩니다.

   ![CRXDE에서 RTE에서 사용할 수 있는 문자 범위를 정의합니다.](assets/chlimage_1-107.png)

   *그림:CRXDE에서 RTE에서 사용할 수 있는 문자 범위를 정의합니다.*

   ![RTE에서 사용할 수 있는 특수 문자가 팝업 ](assets/rtepencil.png "창의 작성자에게 표시RTE에서 사용할 수 있는 특수 문자가 팝업 창의 작성자에게 표시됩니다")

## 표 스타일 {#tablestyles} 구성

스타일은 일반적으로 텍스트에 적용되지만 표 또는 일부 표 셀에도 별도의 스타일 세트를 적용할 수 있습니다. 이러한 스타일은 셀 속성 또는 표 속성 대화 상자의 스타일 선택기 상자에서 작성자가 사용할 수 있습니다. 이 스타일은 표준 표 구성 요소가 아닌 텍스트 구성 요소(또는 파생) 내의 표를 편집할 때 사용할 수 있습니다.

>[!NOTE]
클래식 UI에 대해서만 표 및 셀의 스타일을 정의할 수 있습니다.

>[!NOTE]
RTE 구성 요소의 테이블 복사 및 붙여넣기는 브라우저에 따라 다릅니다. 모든 브라우저에서는 지원되지 않습니다. 표 구조 및 브라우저에 따라 다양한 결과를 얻을 수 있습니다. 예를 들어 클래식 UI 및 터치 UI에서 Mozilla Firefox의 RTE 구성 요소에 표를 복사하여 붙여넣으면 표 레이아웃이 유지되지 않습니다.

1. 구성 요소 내에서 노드 `<rtePlugins-node>/table`으로 이동합니다. 노드가 없으면 노드를 생성합니다. 자세한 내용은 [플러그인](#activateplugin) 활성화를 참조하십시오.
1. `table` 노드에서 `features` 속성을 만듭니다.

   * **이름** `features`
   * **유형** `String`
   * **값** `*`

   >[!NOTE]
   모든 테이블 기능을 활성화하지 않으려면 `features` 속성을 다음과 같이 만들 수 있습니다.
   * **유형** `String[]`

   * **필요에 따라 다음 값** 중 하나 또는 둘 다를 선택합니다.
      * `table` to allow the editing of table properties;를 참조하십시오.
      * `cellprops` to allow the editing of cell properties, including the styles.


1. CSS 스타일 시트의 위치를 정의하여 지정합니다. 텍스트[에 대해 ](#locationofstylesheet)스타일을 정의할 때와 동일하게 스타일 시트[의 위치 지정을 참조하십시오. ](#textstyles) 다른 스타일을 정의한 경우 위치를 정의할 수 있습니다.
1. `table` 노드에서 필요에 따라 다음 노드를 만듭니다.

   * 전체 테이블에 대한 스타일을 정의하려면(**[!UICONTROL 표 속성]** 아래에서 사용 가능):

      * **이름** `tableStyles`
      * **유형** `cq:WidgetCollection`
   * 개별 셀의 스타일을 정의하려면(**[!UICONTROL 셀 속성]** 아래 사용 가능),

      * **이름** `cellStyles`
      * **유형** `cq:WidgetCollection`


1. 노드를 만들고(해당하는 경우 `tableStyles` 또는 `cellStyles` 노드 아래) 개별 스타일을 나타냅니다.

   * **이름** 을 지정할 수 있지만 스타일을 반영해야 합니다.
   * **유형** `nt:unstructured`

1. 이 노드에서 속성을 만듭니다.

   * 참조되는 CSS 스타일을 정의하려면

      * **이름** `cssName`
      * **유형** `String`
      * **CSS 클래스 이름** 을 지정합니다(예: 앞의 이름 `.`이  `cssClass` 아닌 이름)  `.cssClass`
   * 팝업 선택기에 표시할 설명 텍스트를 정의하려면

      * **이름** `text`
      * **유형** `String`
      * **선택 목록** 에 표시할 텍스트 값


1. 모든 변경 사항을 저장합니다.

각 필수 스타일에 대해 위 단계를 반복합니다.

### 접근성 {#hiddenheader}에 대한 테이블의 숨겨진 헤더 구성

열의 목적이 다른 열과 열 간의 시각적 관계에 의해 암묵되었다고 가정할 때, 열 머리글에 시각적 텍스트가 없는 데이터 표를 만들 수 있습니다. 이 경우, 다양한 요구 사항이 있는 독자가 열의 용도를 이해할 수 있도록 화면 판독기 및 기타 보조 기술을 허용하려면 헤더 셀의 셀 내에 숨겨진 내부 텍스트를 제공해야 합니다.

이러한 시나리오에서 액세서빌러티를 향상시키기 위해 RTE는 숨겨진 헤더 셀을 지원합니다. 또한 표의 숨겨진 헤더와 관련된 구성 설정을 제공합니다. 이러한 설정을 사용하면 편집 및 미리 보기 모드에서 숨겨진 헤더에 CSS 스타일을 적용할 수 있습니다. 작성자가 편집 모드에서 숨겨진 헤더를 식별하는 데 도움이 되도록 코드에 다음 매개 변수를 포함하십시오.

* `hiddenHeaderEditingCSS`:RTE를 편집할 때 숨겨진 헤더 셀에 적용되는 CSS 클래스의 이름을 지정합니다.
* `hiddenHeaderEditingStyle`:RTE를 편집할 때 숨겨진 헤더 셀에 적용되는 스타일 문자열을 지정합니다.

코드에서 CSS와 Style 문자열을 모두 지정하는 경우 CSS 클래스가 스타일 문자열보다 우선하며 스타일 문자열의 구성 변경 사항을 덮어쓸 수 있습니다.

작성자가 미리 보기 모드에서 숨겨진 헤더에 CSS를 적용하는 데 도움이 되도록 코드에 다음 매개 변수를 포함할 수 있습니다.

* `hiddenHeaderClassName`:미리 보기 모드에서 숨겨진 헤더 셀에 적용되는 CSS 클래스의 이름을 지정합니다.
* `hiddenHeaderStyle`:미리 보기 모드에서 숨겨진 헤더 셀에 적용되는 스타일 문자열을 지정합니다.

코드에서 CSS와 Style 문자열을 모두 지정하는 경우 CSS 클래스가 스타일 문자열보다 우선하며 스타일 문자열의 구성 변경 사항을 덮어쓸 수 있습니다.

## 맞춤법 검사기 {#adddict}에 대한 사전 추가

맞춤법 검사 플러그인이 활성화되면 RTE에서는 각 해당 언어에 대한 사전을 사용합니다. 그런 다음 하위 트리에서 언어 속성을 가져오거나 URL에서 언어를 추출하여 웹 사이트의 언어에 따라 선택됩니다.예를 들면 다음과 같습니다. `/en/` 분기가 영어로 확인되고 `/de/` 분기가 독일어로 선택됩니다.

>[!NOTE]
&quot;맞춤법 검사에 실패했습니다.&quot; 메시지 가 설치되지 않은 언어를 확인하려고 하면 표시됩니다.

표준 Experience Manager 설치에는 다음과 같은 사전이 포함됩니다.

* 미국 영어(en_us)
* 영어(en_gb)

>[!NOTE]
표준 사전은 해당 ReadMe 파일과 함께 `/libs/cq/spellchecker/dictionaries`에 있습니다. 파일을 수정하지 마십시오.

필요한 경우 사전을 더 추가하려면 다음 단계를 따르십시오.

1. [https://extensions.openoffice.org/](https://extensions.openoffice.org/) 페이지로 이동합니다.
1. 필요한 언어를 선택하고 맞춤법 정의가 있는 ZIP 파일을 다운로드합니다. 파일 시스템에서 아카이브 컨텐츠를 추출합니다.

   >[!CAUTION]
   OpenOffice.org v2.0.1 이전 버전의 `MySpell` 형식의 사전만 지원됩니다. 현재 사전이 파일을 보관하는 경우 다운로드 후 아카이브를 확인하는 것이 좋습니다.

1. .aff 및 .dic 파일을 찾습니다. 파일 이름을 소문자로 유지합니다. 예: `de_de.aff` 및 `de_de.dic`.
1. `/apps/cq/spellchecker/dictionaries`의 저장소에서 .aff 및 .dic 파일을 로드합니다.

>[!NOTE]
RTE 맞춤법 검사기는 on-demand로 사용할 수 있습니다. 텍스트를 입력하기 시작하면 자동으로 실행되지 않습니다.
맞춤법 검사기를 실행하려면 도구 모음에서 맞춤법 검사기 단추를 탭/클릭합니다. RTE는 단어의 맞춤법을 검사하고 철자가 잘못된 단어를 강조 표시합니다.
맞춤법 검사기에서 제안하는 변경 내용을 포함할 경우 텍스트 상태가 변경되고 맞춤법이 틀린 단어가 강조 표시된 문제가 해결되었습니다. 맞춤법 검사기를 실행하려면 맞춤법 검사기 단추를 다시 탭/클릭합니다.

## 실행 취소 및 재실행 작업 {#undohistory}에 대한 작업 내역 크기 구성

RTE를 통해 작성자는 몇 번의 마지막 편집 내용을 실행 취소하거나 재실행할 수 있습니다. 기본적으로 50개의 편집 내용이 내역에 저장됩니다. 필요에 따라 이 값을 구성할 수 있습니다.

1. 구성 요소 내에서 노드 `<rtePlugins-node>/undo`으로 이동합니다. 이러한 노드가 없으면 노드를 만듭니다. 자세한 내용은 [플러그인](#activateplugin) 활성화를 참조하십시오.
1. `undo` 노드에서 속성을 만듭니다.

   * **이름** `maxUndoSteps`
   * **유형** `Long`
   * **작업 내역** 에 저장할 실행 취소 단계 수를 지정합니다. 기본값은 50입니다. `0`을(를) 사용하여 실행 취소/다시 실행을 완전히 비활성화합니다.

1. 변경 사항을 저장합니다.

## 탭 크기 {#tabsize} 구성

텍스트 내에서 탭 문자를 누르면 사전 정의된 공백 수가 삽입됩니다.기본적으로 3개의 비분리 공백과 1개의 공백이 있습니다.

탭 크기를 정의하려면

1. 구성 요소에서 노드 `<rtePlugins-node>/keys`으로 이동합니다. 노드가 없으면 노드를 생성합니다. 자세한 내용은 [플러그인](#activateplugin) 활성화를 참조하십시오.
1. `keys` 노드에서 속성을 만듭니다.

   * **이름** `tabSize`
   * **유형** `String`
   * **** 탭에 사용할 공백 문자 수를 지정합니다.

1. 변경 사항을 저장합니다.

## 들여쓰기 여백 {#indentmargin} 설정

들여쓰기를 활성화하면(기본값) 들여쓰기 크기를 정의할 수 있습니다.

>[!NOTE]
이 들여쓰기 크기는 텍스트의 단락(블록)에만 적용됩니다.실제 목록의 들여쓰기에는 영향을 주지 않습니다.

1. 구성 요소 내에서 노드 `<rtePlugins-node>/lists`으로 이동합니다. 이러한 노드가 없으면 노드를 만듭니다. 자세한 내용은 [플러그인](#activateplugin) 활성화를 참조하십시오.
1. `lists` 노드에서 `identSize` 매개 변수를 만듭니다.

   * **이름**: `identSize`
   * **유형**: `Long`
   * **값**:들여쓰기 여백에 필요한 픽셀 수입니다.

## 편집 가능한 공간의 높이 구성 {#editablespace}

구성 요소 대화 상자 내에 표시된 편집 가능한 공간의 높이를 정의할 수 있습니다. 구성은 대화 상자에서 RTE를 사용하는 경우에만 적용됩니다. 구성은 대화 상자 창의 높이를 변경하지 않습니다.

1. `../items/text` 노드의 구성 요소에 대한 대화 상자 정의에서 속성을 만듭니다.

   * **이름** `height`
   * **유형** `Long`
   * **편집** 캔버스의 높이를 픽셀 단위로 지정합니다.

1. 변경 사항을 저장합니다.

## {#linkstyles} 링크에 대한 스타일 및 프로토콜 구성

[!DNL Experience Manager]에 링크를 추가할 때 사용할 CSS 스타일과 프로토콜이 자동으로 수락되도록 정의할 수 있습니다. 다른 프로그램의 [!DNL Experience Manager]에 링크가 추가되는 방식을 구성하려면 HTML 규칙을 정의합니다.

1. CRXDE Lite을 사용하여 프로젝트의 텍스트 구성 요소를 찾습니다.
1. 노드를 `<rtePlugins-node>`과 동일한 수준으로 만듭니다. 즉, 노드를 `<rtePlugins-node>`의 상위 노드 아래에 만듭니다.

   * **이름** `htmlRules`
   * **유형** `nt:unstructured`

   >[!NOTE]
   `../items/text` 노드에는 속성이 있습니다.
   * **이름** `xtype`
   * **유형** `String`
   * **값** `richtext`

   `../items/text` 노드의 위치는 대화 상자의 구조에 따라 다를 수 있습니다. 두 예는 `/apps/myProject>/components/text/dialog/items/text`과 `/apps/<myProject>/components/text/dialog/items/panel/items/text`입니다.

1. `htmlRules` 아래에서 노드를 만듭니다.

   * **이름** `links`
   * **유형** `nt:unstructured`

1. `links` 노드에서 필요에 따라 속성을 정의합니다.

   * 내부 링크에 대한 CSS 스타일:

      * **이름** `cssInternal`
      * **유형** `String`
      * **** CSS 클래스의 이름을 지정합니다(이전 &#39;.&#39; 없이).;예를 들어 `.cssClass` 대신 `cssClass`가 사용됩니다.
   * 외부 링크에 대한 CSS 스타일

      * **이름** `cssExternal`
      * **유형** `String`
      * **** CSS 클래스의 이름을 지정합니다(이전 &#39;.&#39; 없이).;예를 들어 `.cssClass` 대신 `cssClass`가 사용됩니다.
   * `https://`, `https://`, `file://`, `mailto:` 등이 포함된 유효한 **[!UICONTROL 프로토콜]**&#x200B;의 배열,

      * **이름** `protocols`
      * **유형** `String[]`
      * **값** 하나 이상의 프로토콜
   * **defaultProtocol** (type  **String** 속성):사용자가 명시적으로 프로토콜을 지정하지 않은 경우 사용할 프로토콜입니다.

      * **이름** `defaultProtocol`
      * **유형** `String`
      * **값** 하나 이상의 기본 프로토콜
   * 링크의 대상 속성을 처리하는 방법에 대한 정의입니다. 노드 만들기:

      * **이름** `targetConfig`
      * **유형** `nt:unstructured`

      노드 `targetConfig`에서:필수 속성을 정의합니다.

      * 대상 모드를 지정합니다.

         * **이름** `mode`
         * **유형** `String`)
         * **값**:

            * `auto`:자동 타겟이 선택된다는 의미입니다.

               (외부 링크의 `targetExternal` 속성 또는 내부 링크의 `targetInternal`에 의해 지정됨)

            * `manual`:이 컨텍스트에 적용되지 않음
            * `blank`:이 컨텍스트에 적용되지 않음
      * 내부 링크의 대상:

         * **이름** `targetInternal`
         * **유형** `String`
         * **내부** 링크에 대한 타겟의 값(모드가 인 경우에만 사용  `auto`)
      * 외부 링크의 대상:

         * **이름** `targetExternal`
         * **유형** `String`
         * **외부 링크** 의 타겟을 지정합니다(모드가 인 경우에만  `auto`사용됨).








1. 모든 변경 사항을 저장합니다.
