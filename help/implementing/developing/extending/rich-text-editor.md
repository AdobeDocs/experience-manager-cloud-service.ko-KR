---
title: ' [!DNL Adobe Experience Manager] 의 컨텐츠를 Cloud Service으로 작성하도록 리치 텍스트 편집기를 구성합니다.'
description: ' [!DNL Adobe Experience Manager] 의 컨텐츠를 Cloud Service으로 작성하도록 리치 텍스트 편집기를 구성합니다.'
contentOwner: AG
translation-type: tm+mt
source-git-commit: 739dde6f9a6a7f4fe773e27e53f23a395f2881dc
workflow-type: tm+mt
source-wordcount: '1981'
ht-degree: 0%

---


# 리치 텍스트 편집기 구성 {#configure-the-rich-text-editor}

RTE(Rich Text Editor)에서는 작성자가 텍스트 컨텐츠를 편집하는 다양한 기능을 제공합니다. 아이콘, 선택 상자, 도구 모음 및 메뉴는 WYSIWYG 텍스트 편집 환경을 위해 제공됩니다. 관리자는 작성 구성 요소에서 사용 가능한 기능을 활성화, 비활성화 및 확장하도록 RTE를 구성합니다. 작성자가 [웹 내용 작성에 RTE를 사용하는 방법을 참조하십시오.](/help/sites-cloud/authoring/fundamentals/rich-text-editor.md)

구성하는 데 필요한 RTE 개념 및 단계는 아래에 나열되어 있습니다.

| RTE 개념 이해 | 필수 기능 사용 | 개별 기능 구성 |
|---|---|---|
| [인터페이스 이해](#understand-rte-ui) | [구성 위치 이해 및 설정](#understand-the-configuration-paths-and-locations) | [플러그인 구성](#enable-rte-functionalities-by-activating-plug-ins) |
| [편집 모드 유형](#editingmodes) | [플러그인 활성화](/help/implementing/developing/extending/configure-rich-text-editor-plug-ins.md#activateplugin) | [기능 속성 설정](#aboutplugins) |
| [플러그인 정보](#aboutplugins) | [RTE 도구 모음 구성](#dialogfullscreen) | [붙여넣기 모드 구성](/help/implementing/developing/extending/configure-rich-text-editor-plug-ins.md#textstyles) |

## 작성자가 사용할 수 있는 사용자 인터페이스 이해{#understand-rte-ui}

RTE 인터페이스는 작성 환경을 위한 [반응형 디자인](/help/sites-cloud/authoring/features/responsive-layout.md)을 제공합니다. 인터페이스는 터치 및 데스크톱 장치에서 사용하도록 설계되었습니다.

![리치 텍스트 편집기 도구 모음](assets/rte-toolbar-full-screen-mode.png)

*그림:사용 가능한 모든 옵션이 활성화된 리치 텍스트 편집기 도구 모음.*

도구 모음은 WYSIWYG 작성 환경에 대한 옵션을 제공합니다. [!DNL Experience Manager] 관리자는 인터페이스의 도구 모음에서 사용할 수 있는 옵션을 구성할 수 있습니다. 포괄적인 편집 옵션은 기본적으로 [!DNL Experience Manager]에서 사용할 수 있습니다. 개발자는 [!DNL Experience Manager]을(를) 사용자 정의하여 추가 편집 옵션을 추가할 수 있습니다.

## 다양한 편집 모드 {#editingmodes}

작성자는 다양한 구성 요소 모드를 사용하여 [!DNL Experience Manager]에서 텍스트 컨텐츠를 만들고 편집할 수 있습니다. 컨텐츠 작성 및 서식 지정을 위한 툴바 옵션과 다양한 편집 모드에서 RTE 지원 구성 요소의 사용자 환경은 RTE 구성에 따라 다릅니다.

| 편집 모드 | 편집 영역 | 활성화할 기능 권장 |
|--- |--- |--- |
| 인라인 | 즉석 편집을 통해 간단한 편집대화 상자를 열지 않고 형식을 지정합니다. | 최소 RTE 기능. |
| RTE 전체 화면 | 전체 페이지를 포함합니다. | 모든 필수 RTE 기능. |
| 대화 상자 | 대화 상자는 페이지 컨텐츠 맨 위에 있지만 전체 페이지를 포함하지 않습니다. | 간편하게 기능을 사용할 수 있습니다. |
| 대화 상자 전체 화면 | 전체 화면 모드와 동일;은 RTE와 함께 대화 상자의 필드를 포함합니다. | 모든 필수 RTE 기능. |

>[!NOTE]
>
>소스 편집 기능은 인라인 편집 모드에서 사용할 수 없습니다. 전체 화면 모드에서는 이미지를 드래그할 수 없습니다. 다른 모든 기능은 모든 모드에서 작동합니다.

### 인라인 편집 {#inline-editing}

페이지 내의 컨텐츠를 편집하려면 느리게 두 번 클릭하여 컨텐츠를 엽니다. 기본 옵션이 포함된 작은 도구 모음이 표시됩니다.

![툴바의 기본 옵션을 사용한 인라인 편집](assets/inline-editing-mode-basic-options.png)

*그림:도구 모음의 기본 옵션을 사용하여 인라인 편집.*

### 전체 화면 편집 {#full-screen-editing}

[!DNL Experience Manager] 구성 요소는 페이지 컨텐츠를 숨기고 사용 가능한 화면을 차지하는 전체 화면 보기에서 열 수 있습니다. 대부분의 편집 옵션을 제공하므로 전체 화면 편집이 인라인 편집의 자세한 버전입니다. 인라인 편집 모드를 사용할 때 압축 도구 모음에서 ![아이콘을 클릭하여 전체 화면](assets/rte_fullscreen.png)에서 RTE를 열 수 있습니다.

대화 상자의 전체 화면 모드에서 세부 RTE 도구 모음과 함께 대화 상자에서 사용할 수 있는 옵션 및 구성 요소도 사용할 수 있습니다. 다른 구성 요소와 함께 RTE를 포함하는 대화상자에만 적용됩니다.

![전체 화면 모드에서 편집할 때 자세한 RTE 도구 모음](assets/rte-toolbar-full-screen-mode.png)

*그림:전체 화면 모드에서 편집할 때 자세한 RTE 도구 모음*

### 대화 상자 편집 {#dialog-editing}

구성 요소를 두 번 클릭하면 컨텐츠를 편집할 수 있는 대화 상자가 열립니다. 대화 상자가 기존 페이지 상단에 열립니다. 일부 특정 시나리오에서는 대화 상자가 팝업 창으로 열립니다. 예를 들어 텍스트 구성 요소가 여러 열로 구성된 페이지 레이아웃의 열에 포함되어 있고 대화 상자에 사용할 수 있는 영역이 더 적은 경우

![대화 상자 편집 모드](assets/dialog_editing_modetouchui.png)

*그림:대화 상자 편집 모드.*

## RTE 플러그인 및 관련 기능정보 {#aboutplugins}

이 기능은 다음과 같이 일련의 플러그인을 통해 사용할 수 있습니다.

* `features` 속성(

   * 해당 플러그인의 기본 기능을 활성화 또는 비활성화하는 데 사용됩니다.
   * 표준화된 절차를 사용하여 구성됩니다.

* 적절한 경우 전문화된 구성이 필요한 속성과 옵션이 더 있습니다.

해당 플러그인과 관련된 노드에 있는 `features` 속성 값으로 RTE의 기본 기능이 활성화되거나 비활성화됩니다.

다음 표에는 현재 플러그인이 표시되어 있습니다.

* API 설명서에 대한 링크가 있는 플러그인 ID입니다. ID는 [플러그인](/help/implementing/developing/extending/configure-rich-text-editor-plug-ins.md#activateplugin)을 활성화할 때 노드 이름으로 사용됩니다.
* `features` 속성에 허용된 값.
* 플러그인에서 제공하는 기능에 대한 설명입니다.

| 플러그인 ID | features | 설명 |
|--- |--- |--- |
| 편집 | `cut`,  `copy`,  `paste-default`,  `paste-plaintext`,  `paste-wordhtml` | [잘라내기, 복사 및 붙여넣기 모드](/help/implementing/developing/extending/configure-rich-text-editor-plug-ins.md#textstyles) 3가지를 수행합니다. |
| [findreplace](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.rte.plugins.FindReplacePlugin) | `find`, `replace` | 찾기 및 바꾸기 |
| [format](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.rte.plugins.FormatPlugin) | `bold`,  `italic`  `underline` | [기본 텍스트 서식](configure-rich-text-editor-plug-ins.md#textstyles). |
| [이미지](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.rte.plugins.ImagePlugin) | `image` | 기본 이미지 지원(컨텐츠 또는 컨텐츠 파인더에서 드래그). 브라우저에 따라 작성자에 대한 지원 동작이 다릅니다 |
| [keys](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.rte.plugins.KeyPlugin) | - | 이 값을 정의하려면 [탭 크기](configure-rich-text-editor-plug-ins.md#tabsize)를 참조하십시오. |
| [justify](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.rte.plugins.JustifyPlugin) | `justifyleft`,  `justifycenter`  `justifyright` | 단락 정렬. |
| [링크](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.rte.plugins.LinkPlugin) | `modifylink`,  `unlink`  `anchor` | [하이퍼링크 및 앵커](configure-rich-text-editor-plug-ins.md#linkstyles). |
| [lists](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.rte.plugins.ListPlugin) | `ordered`,  `unordered`,  `indent`,  `outdent` | 이 플러그인은 [들여쓰기 및 목록](configure-rich-text-editor-plug-ins.md#indentmargin);을 모두 제어합니다.중첩된 목록 포함. |
| [misctools](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.rte.plugins.MiscToolsPlugin) | `specialchars`,  `sourceedit` | 기타 도구를 사용하여 작성자는 [특수 문자](configure-rich-text-editor-plug-ins.md#spchar)를 입력하거나 HTML 소스를 편집할 수 있습니다. 또한 목록을 직접 정의하려면 [특수 문자 범위](configure-rich-text-editor-plug-ins.md#definerangechar)를 추가할 수도 있습니다. |
| Paraformat | `paraformat` | 기본 단락 형식은 단락, 머리글 1, 머리글 2 및 머리글 3(`<p>`, `<h1>`, `<h2>` 및 `<h3>`)입니다. [단락 서식](configure-rich-text-editor-plug-ins.md#paraformats)을 더 추가하거나 목록을 확장할 수 있습니다. |
| spellcheck | `checktext` | [언어 인식 맞춤법 검사기입니다](configure-rich-text-editor-plug-ins.md#adddict). |
| 스타일 | `styles` | CSS 클래스를 사용하여 스타일 지정을 지원합니다. [텍스트에 사용할 ](configure-rich-text-editor-plug-ins.md#textstyles) 고유한 스타일 범위를 추가하거나 확장하려는 경우 새로운 텍스트 스타일을 추가할 수 있습니다. |
| subsuperscript | `subscript`,  `superscript` | 기본 포맷으로 확장하며 하위 스크립트 및 수퍼 스크립트를 추가합니다. |
| 표 | `table`, `removetable`, `insertrow`, `removerow`, `insertcolumn`, `removecolumn`, `cellprops`, `mergecells`, `splitcell`, `selectrow`, `selectcolumns` | 전체 표 또는 개별 셀에 대해 고유한 스타일을 추가하려면 [표 스타일 구성](configure-rich-text-editor-plug-ins.md#tablestyles)을 참조하십시오. |
| 실행 취소 | `undo`,  `redo` | [실행 취소 및 다시 실행](configure-rich-text-editor-plug-ins.md#undohistory) 작업의 기록 크기입니다. |

>[!NOTE]
>
>전체 화면 플러그인은 대화 상자에서 지원되지 않습니다. `dialogFullScreen` 설정을 사용하여 전체 화면 모드로 도구 모음을 구성합니다.

## 구성 경로 및 위치이해 {#understand-the-configuration-paths-and-locations}

[RTE 플러그인](configure-rich-text-editor-plug-ins.md#activateplugin)을 활성화할 때 작성자를 위해 제공하는 [RTE 편집의 모드 및 인터페이스](#editingmodes)에서 구성 세부 사항의 위치를 결정합니다. 위치는 다음과 같습니다.

* 인라인 모드:`cq:editConfig/cq:inplaceEditing`.
* 전체 화면 모드: `cq:editConfig/cq:inplaceEditing`.
* 대화 모드:`cq:dialog`.
* 전체 화면 대화 모드:`cq:dialog`.

>[!NOTE]
>
>`cq:inplaceEditing` 아래의 노드 이름을 `config`(으)로 지정하지 마십시오. `cq:inplaceEditing` 노드에서 다음 속성을 정의합니다.
>
>* **이름**: `configPath`
>* **유형**: `String`
>* **값**:실제 구성을 포함하는 노드의 경로
>
>RTE 구성 노드의 이름을 `config`으로 지정하지 마십시오. 그렇지 않은 경우 RTE 구성은 관리자에게만 적용되고 `content-author` 그룹의 사용자에 대해서는 적용되지 않습니다.

대화 상자 편집 모드에 적용되는 다음 속성을 구성합니다.

* `useFixedInlineToolbar`:떠 있는 대신 RTE 도구 모음을 고정시킬 수 있습니다. sling:resourceType= `cq/gui/components/authoring/dialog/richtext`을(를) 사용하여 RTE 노드에 정의된 이 부울 속성을 `True`으로 설정합니다. 이 속성을 `True`으로 설정하면 `foundation-contentloaded` 이벤트에서 리치 텍스트 편집이 시작됩니다. 이를 방지하려면 `customStart` 속성을 `True`으로 설정하고 `rte-start` 이벤트를 트리거하여 RTE 편집을 시작합니다. 이 속성이 `true`인 경우 RTE는 클릭할 때 시작되지 않으며 이는 기본 동작입니다.

* `customStart`:이벤트를 트리거하여 RTE를 시작할 시기를 제어하려면 RTE 노드에 정의된 이  `True`부울 속성을 로 설정합니다 `rte-start`.

* `rte-start`:RTE 편집을 시작할 때 RTE `contenteditable-div` 의 경우 이 이벤트를 트리거합니다. `customStart`이(가) `true`로 설정된 경우에만 작동합니다.

터치 지원 대화 상자에서 RTE를 사용하는 경우 문제를 방지하려면 `useFixedInlineToolbar` 속성을 `true`으로 설정합니다.

## 플러그인을(를) 활성화하여 RTE 기능 활성화 {#enable-rte-functionalities-by-activating-plug-ins}

RTE 기능은 여러 플러그인을 통해 제공되며 각각 기능 속성이 있습니다. 각 플러그인의 다양한 기능을 활성화하거나 비활성화하도록 기능 속성을 구성할 수 있습니다.

RTE 플러그인의 자세한 구성에 대해서는 [RTE 플러그인 활성화 및 구성 방법](configure-rich-text-editor-plug-ins.md)을 참조하십시오.

<!-- TBD ENGREVIEW: To confirm if the sample works in CS or not?
**Sample**: Download [this sample configuration](/help/sites-administering/assets/rte-sample-all-features-enabled-10.zip) that illustrates how to configure RTE. In this package all the features are enabled. -->

템플릿 편집자는 [핵심 구성 요소 텍스트 구성 요소](https://docs.adobe.com/content/help/en/experience-manager-core-components/using/components/text.html#the-text-component-and-the-rich-text-editor)를 사용하여 사용자 인터페이스를 컨텐츠 정책으로 사용하여 많은 RTE 플러그인을 구성할 수 있으므로 기술 구성이 필요하지 않습니다. 컨텐츠 정책은 이 문서에 설명된 대로 RTE UI 구성에서 작동할 수 있습니다. 자세한 내용은 [페이지 템플릿 만들기](/help/sites-cloud/authoring/features/templates.md) 및 [핵심 구성 요소 개발자 설명서](https://docs.adobe.com/content/help/en/experience-manager-core-components/using/developing/developing.html)를 참조하십시오.

>참조용으로 기본 텍스트 구성 요소(표준 설치의 일부로 제공)는 다음 위치에서 찾을 수 있습니다.
>
>* `/libs/wcm/foundation/components/text`
>* `/libs/foundation/components/text`
>
>고유한 텍스트 구성 요소를 만들려면 이러한 구성 요소를 편집하는 대신 위의 구성 요소를 복사하십시오.

## RTE 도구 모음구성 {#dialogfullscreen}

[!DNL Experience Manager] 다양한 편집 모드에 대해 리치 텍스트 편집기의 인터페이스를 다르게 구성할 수 있습니다. 기본 설정은 아래에 제공됩니다. 요구 사항에 따라 이러한 기본값을 재정의할 수 있습니다. 작성자에게 제공할 도구 모음 기능만 사용자 정의합니다. 도구 모음 구성을 모두 지정할 필요는 없습니다.

`dialogFullScreen`에 대한 도구 모음을 구성하려면 다음 샘플 구성을 사용하십시오.

```java
<uiSettings jcr:primaryType="nt:unstructured">
  <cui jcr:primaryType="nt:unstructured">
    <inline
      jcr:primaryType="nt:unstructured"
      toolbar="[format#bold,format#italic,format#underline,#justify,#lists,links#modifylink,links#unlink,#paraformat]">
      <popovers jcr:primaryType="nt:unstructured">
        <justify
          jcr:primaryType="nt:unstructured"
          items="[justify#justifyleft,justify#justifycenter,justify#justifyright,justify#justifyjustify]"
          ref="justify"/>
        <lists
          jcr:primaryType="nt:unstructured"
          items="[lists#unordered,lists#ordered,lists#outdent,lists#indent]"
          ref="lists"/>
        <paraformat
          jcr:primaryType="nt:unstructured"
          items="paraformat:getFormats:paraformat-pulldown"
          ref="paraformat"/>
      </popovers>
    </inline>
    <dialogFullScreen
      jcr:primaryType="nt:unstructured"
      toolbar="[format#bold,format#italic,format#underline,justify#justifyleft,justify#justifycenter,justify#justifyright,justify#justifyjustify,lists#unordered,lists#ordered,lists#outdent,lists#indent,links#modifylink,links#unlink,table#createoredit,#paraformat,image#imageProps]">
      <popovers jcr:primaryType="nt:unstructured">
        <paraformat
          jcr:primaryType="nt:unstructured"
          items="paraformat:getFormats:paraformat-pulldown"
          ref="paraformat"/>
      </popovers>
    </dialogFullScreen>
    <tableEditOptions
      jcr:primaryType="nt:unstructured"
      toolbar="[table#insertcolumn-before,table#insertcolumn-after,table#removecolumn,-,table#insertrow-before,table#insertrow-after,table#removerow,-,table#mergecells-right,table#mergecells-down,table#mergecells,table#splitcell-horizontal,table#splitcell-vertical,-,table#selectrow,table#selectcolumn,-,table#ensureparagraph,-,table#modifytableandcell,table#removetable,-,undo#undo,undo#redo,-,table#exitTableEditing,-]">
    </tableEditOptions>
  </cui>
</uiSettings>
```

인라인 모드 및 전체 화면 모드에 서로 다른 사용자 인터페이스 설정이 사용됩니다. toolbar 속성은 도구 모음의 옵션을 지정합니다.

예를 들어 옵션 자체가 기능(예: `Bold`)인 경우 `PluginName#FeatureName`(예: `links#modifylink`)으로 지정됩니다.

옵션이 팝업(플러그인의 일부 기능 포함)인 경우 `#PluginName`(예: `#format`)으로 지정됩니다.

옵션 그룹 사이의 구분 문자(`|`)는 `-`로 지정할 수 있습니다.

인라인 또는 전체 화면 모드 아래의 팝업 노드에는 사용 중인 팝업 오버의 목록이 포함되어 있습니다. `popovers` 노드 아래의 각 하위 노드의 이름은 플러그인(예: 형식)의 이름을 따릅니다. 플러그인 기능 목록이 포함된 속성 &#39;items&#39;가 있습니다(예: format#bold).

## RTE 사용자 인터페이스 설정 및 콘텐츠 정책 {#rtecontentpolicies}

관리자는 위에서 설명한 대로 구성을 수행하는 대신 컨텐츠 정책을 사용하여 RTE 옵션을 제어할 수 있습니다. 컨텐트 정책은 [편집 가능한 템플릿](/help/sites-cloud/authoring/features/templates.md)의 일부로 사용할 때 구성 요소의 디자인 속성을 정의합니다. 예를 들어 RTE를 사용하는 텍스트 구성 요소가 편집 가능한 템플릿과 함께 사용되는 경우 컨텐츠 정책은 굵은체 옵션을 사용할 수 있고 몇 가지 단락 서식 지정 옵션을 사용할 수 있음을 정의할 수 있습니다. 컨텐츠 정책은 다시 사용할 수 있으며 여러 템플릿에 적용할 수 있습니다.

사용자 인터페이스 구성에서 컨텐츠 정책으로 이어지는 RTE 흐름의 사용 가능한 옵션입니다.

* 사용자 인터페이스 구성 설정은 콘텐츠 정책에 사용할 수 있는 옵션을 정의합니다.
* RTE의 사용자 인터페이스 구성이 제거되었거나 항목을 활성화하지 않으면 콘텐트 정책이 해당 항목을 구성할 수 없습니다.
* 작성자는 사용자 인터페이스 구성 및 컨텐츠 정책에 의해 사용 가능한 기능에만 액세스할 수 있습니다.

예를 들어 [텍스트 코어 구성 요소 설명서](https://docs.adobe.com/help/en/experience-manager-core-components/using/components/text.html#the-text-component-and-the-rich-text-editor)를 볼 수 있습니다.

## 도구 모음 아이콘과 명령간의 매핑을 사용자 정의합니다. {#iconstoolbar}

RTE 도구 모음에 표시된 Coral 아이콘과 사용 가능한 명령 간의 매핑을 사용자 지정할 수 있습니다. Coral 아이콘 외에는 다른 아이콘을 사용할 수 없습니다.

1. `uiSettings/cui` 아래에 `icons` 노드를 만듭니다.

1. 아래에 개별 아이콘용 노드를 만듭니다.
1. 각 개별 아이콘 노드에서 Coral 아이콘과 아이콘에 매핑할 명령을 지정합니다.

다음은 명령 `Bold`을 `textItalic`이라는 Coral 아이콘에 매핑하기 위한 샘플 조각입니다.

```java
<text jcr:primaryType="nt:unstructured" sling:resourceType="cq/gui/components/authoring/dialog/richtext" name="./text" useFixedInlineToolbar="{Boolean}true">
    <rtePlugins jcr:primaryType="nt:unstructured">
        <format jcr:primaryType="nt:unstructured" features="bold,italic"/>
    </rtePlugins>
    <uiSettings jcr:primaryType="nt:unstructured">
        <cui jcr:primaryType="nt:unstructured">
            <inline jcr:primaryType="nt:unstructured"
                toolbar="[format#bold,format#italic,format#underline,links#modifylink,links#unlink]">
            </inline>
            <icons jcr:primaryType="nt:unstructured">
                <bold jcr:primaryType="nt:unstructured"
                    command="format#bold"
                    icon="textItalic"/>
            </icons>
        </cui>
    </uiSettings>
</text>
```

## 알려진 제한 사항 {#known-limitations}

[!DNL Experience Manager] RTE 기능에는 다음과 같은 제한 사항이 있습니다.

* RTE 기능은 [!DNL Experience Manager] 구성 요소 대화 상자에서만 지원됩니다. RTE는 마법사 또는 Foundation 양식에서 지원되지 않습니다.

* [!DNL Experience Manager] 은 하이브리드 장치에서 작동하지 않습니다.  <!-- TBD: Check. This is not mentioned in Known Issue /help/release-notes/known-issues.md-->

* RTE 구성 노드 `config`의 이름을 지정하지 마십시오. 그렇지 않은 경우 RTE 구성은 관리자에게만 적용되고 `content-author` 그룹의 사용자에 대해서는 적용되지 않습니다.

* RTE는 인라인 프레임 또는 iframe에 내용을 포함할 수 없습니다.

## 모범 사례 및 팁 {#best-practices-and-tips}

* 부동 대화 상자의 경우 팝업 대화 상자 없이 플러그인만 활성화합니다. 팝업이 없는 플러그인의 크기는 작고 부동 대화 상자에 가장 적합합니다.
* `Paste` 플러그인과 같이 전체 화면 대화 모드 또는 전체 화면 모드에서만 큰 팝업을 사용하여 플러그인을 활성화합니다. 대형 팝업이 있는 플러그인에는 저작 경험을 제공하기 위해 더 많은 화면 실제 공간이 필요합니다.
* CoralUI3 RTE용 사용자 정의 플러그인을 사용하는 경우 `rte.coralui3` 라이브러리를 사용합니다.

>[!MORELIKETHIS]
>
>* [RTE 플러그인 구성](configure-rich-text-editor-plug-ins.md)
>* [작성을 위해 리치 텍스트 편집기 사용](/help/sites-cloud/authoring/fundamentals/rich-text-editor.md)
>* [액세스 가능한 사이트에 대한 RTE 구성](rte-accessible-content.md)
>* [복합 다중 필드 구성 요소를 만들기 위한 자습서 샘플](https://experience-aem.blogspot.com/2019/05/aem-65-touchui-composite-multifield-with-coral3-rte-rich-text.html)

