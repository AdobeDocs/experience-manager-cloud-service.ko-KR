---
title: 액세스 가능한 웹 페이지 및 사이트를 만들도록 RTE를 구성합니다.
description: ' [!DNL Adobe Experience Manager]에서 액세스 가능한 사이트를 만들도록 리치 텍스트 편집기를 구성하는 방법에 대해 학습합니다.'
contentOwner: AG
translation-type: tm+mt
source-git-commit: 96c59974a868779df6979818bea0d942060cf5bc
workflow-type: tm+mt
source-wordcount: '508'
ht-degree: 1%

---


# 액세스 가능한 사이트를 생성하도록 RTE 구성 {#configure-rte-accessible-sites}

[!DNL Adobe Experience Manager] 에서는 이미지의 대체 텍스트와 같은 표준 액세서빌러티 기능과 컨텐츠를 만들 때 액세스할 수 있는 추가 기능을 지원합니다. 컨텐츠 작성자는 리치 텍스트 편집기(RTE)를 사용하는 구성 요소에서 이러한 기능을 사용합니다. 이 기능에는 머리글과 단락 요소를 통해 대체 텍스트, 구조적 정보 추가 등이 포함됩니다.

RTE의 일반 구성에 대한 자세한 내용은 [RTE](rich-text-editor.md) 구성 및 [특정 기능에 대한 RTE 플러그인 구성](configure-rich-text-editor-plug-ins.md)을 참조하십시오.

RTE 플러그인 구성을 사용하여 액세스 가능성 관련 기능을 구성하고 사용자 정의합니다. 예를 들어 기본적으로 제공되는 기본 `H1`, `H2` 및 `H3` 외에 지원되는 머리글 수준 수를 확장하는 등 추가 블록 수준 의미 요소를 추가하려면 `paraformat`을 사용하십시오. 작성 사용자 인터페이스의 많은 구성 요소를 사용하여 리치 텍스트를 편집할 수 있습니다. 일반적으로 사용되는 구성 요소는 텍스트, 이미지, 다운로드 등입니다.

RTE 기능은 많은 구성 요소에서 사용할 수 있습니다. 기본 구성 요소는 `Text` 구성 요소입니다.

[!DNL Experience Manager]의 `Text` 구성 요소의 경우 다음 스크린샷은 `paraformat`를 포함하여 다양한 플러그인이 활성화된 리치 텍스트 편집기를 표시합니다.

![전체 화면 모드의 RTE 텍스트 구성 요소](assets/rte-toolbar-full-screen-mode.png)

## 플러그인 기능 {#configuring-the-plugin-features} 구성

RTE 구성 지침은 [리치 텍스트 편집기](rich-text-editor.md) 페이지 구성을 참조하십시오. 이 문서에서는 다음과 같은 내용을 다룹니다.

* [플러그인 및 기능](rich-text-editor.md#aboutplugins)
* [구성 위치](rich-text-editor.md#understand-the-configuration-paths-and-locations)
* [플러그인 활성화 및 기능 속성 구성](rich-text-editor.md#enable-rte-functionalities-by-activating-plug-ins)
* [RTE의 다른 기능 구성](rich-text-editor.md#enable-rte-functionalities-by-activating-plug-ins)

플러그인에 대한 일부 또는 모든 기능을 활성화하려면 CRXDE Lite의 해당 `rtePlugins` 하위 분기 내에서 플러그인을 구성합니다.

![예제 rtePlugin을 보여주는 CRXDE Lite](assets/example-rteplugin-crxde-lite.png)

### RTE 선택 필드 {#example-specifying-paragraph-formats-available-in-rte-selection-field}에서 사용할 수 있는 단락 서식 지정 예

새로운 의미 체계 블록 형식을 선택할 수 있습니다.

1. RTE에 따라 [구성 위치](rich-text-editor.md#understand-the-configuration-paths-and-locations)를 확인하고 탐색합니다.
1. [플러그인을 ](rich-text-editor.md) 활성화하여 단락 선택  [필드를 활성화합니다](rich-text-editor.md#enable-rte-functionalities-by-activating-plug-ins).
1. [단락 선택 필드에서 사용할 형식을 지정합니다](rich-text-editor.md).
1. 그런 다음 RTE의 선택 필드에서 컨텐츠 작성자가 단락 포맷을 사용할 수 있습니다.

RTE에서 단락 형식 옵션을 통해 구조적 요소를 사용할 수 있으므로 [!DNL Experience Manager]은(는) 액세스 가능한 컨텐츠를 개발할 수 있는 적절한 기반을 제공합니다. 컨텐츠 작성자는 RTE를 사용하여 글꼴 크기 또는 색상 또는 기타 관련 속성의 서식을 지정할 수 없으므로 인라인 서식을 만들 수 없습니다. 대신, 작성자는 제목 등의 적절한 구조적 요소를 선택하고 스타일 옵션에서 선택한 전역 스타일을 사용하여 스타일 시트와 올바르게 구조화된 컨텐츠를 원하는 사용자에게 더 나은 마크업 및 깔끔한 마크업 옵션을 제공할 수 있습니다.

## 소스 편집 기능 사용 {#use-of-the-source-edit-feature}

경우에 따라 컨텐츠 작성자는 RTE를 사용하여 만든 HTML 소스 코드를 검토하고 조정할 필요가 있습니다. 예를 들어 RTE 내에서 만들어진 컨텐츠는 WCAG 2.0을 준수하기 위해 더 많은 마크업이 필요할 수 있습니다. RTE의 [소스 편집](rich-text-editor.md#aboutplugins) 옵션을 사용하여 이 작업을 수행할 수 있습니다. `misctools` 플러그인](rich-text-editor.md#aboutplugins)에 [`sourceedit` 기능을 지정할 수 있습니다.

>[!CAUTION]
>
>`sourceedit` 기능을 신중하게 사용하십시오. 입력 오류 및 지원되지 않는 기능은 문제를 일으킬 수 있습니다.

<!--
TBD ENGREVIEW: Is this only applicable to Classic UI? 

## Adding Support for further HTML Elements and Attributes {#adding-support-for-additional-html-elements-and-attributes}

To further extend the accessibility features of [!DNL Experience Manager], it is possible to extend the existing components based on the RTE (such as the `Text` and `Table` components) with extra elements and attributes.

The following procedure illustrates how to extend the `Table` component with a `Caption` element that provides information about a data table to assistive technology users:

### Example: Add a caption to a table properties dialog {#example-adding-the-caption-to-the-table-properties-dialog}

In the constructor of the `TablePropertiesDialog`, add an extra text input field that is used for editing the caption. Set the `itemId` to `caption` (the DOM attribute’s name) to automatically handle its content.

In a `Table`, set the attribute to the DOM element or or remove it from the DOM element. The dialog in the `config` object passed the value. Set or remove the DOM attributes using the corresponding `CQ.form.rte.Common` methods (`com` is a shortcut for `CQ.form.rte.Common`). Using `CQ.form.rte.Common` methods avoids common pitfalls with browser implementations.

>[!NOTE]
>
>This procedure is only suitable for the classic UI.

### Step-by-step instructions {#step-by-step-instructions}

1. Start CRXDE Lite. For example: [http://localhost:4502/crx/de/](http://localhost:4502/crx/de/)

1. Copy `/libs/cq/ui/widgets/source/widgets/form/rte/commands/Table.js` to `/apps/cq/ui/widgets/source/widgets/form/rte/commands/Table.js`. Create intermediate folders if those do not exist.

1. Copy `/libs/cq/ui/widgets/source/widgets/form/rte/plugins/TablePropertiesDialog.js` to `/apps/cq/ui/widgets/source/widgets/form/rte/plugins/TablePropertiesDialog.js`.

1. Open `/apps/cq/ui/widgets/source/widgets/form/rte/plugins/TablePropertiesDialog.js` file to edit.

1. In the `constructor` method, before the mention of `var dialogRef = this;`, add the following code:

   ```javascript
   editItems.push({
       "itemId": "caption",
       "name": "caption",
       "xtype": "textfield",
       "fieldLabel": CQ.I18n.getMessage("Caption"),
       "value": (this.table && this.table.caption ? this.table.caption.textContent : "")
   });
   ```

1. Open `/apps/cq/ui/widgets/source/widgets/form/rte/commands/Table.js` file.

1. Add the following code at the end of the `transferConfigToTable` method:

   ```javascript
   /**
    * Adds Caption Element
   */
   var captionElement;
   if (dom.firstChild && dom.firstChild.tagName.toLowerCase() == "caption")
   {
      captionElement = dom.firstChild;
   }
   if (config.caption)
   {
       var captionTextNode = document.createTextNode(config.caption)
       if (captionElement)
       {
          dom.replaceNode(captionElement.firstChild,captionTextNode);
       } else
       {
           captionElement = document.createElement("caption");
           captionElement.appendChild(captionTextNode);
           if (dom.childNodes.length>0)
           {
              dom.insertBefore(captionElement, dom.firstChild);
           } else
           {
              dom.appendChild(captionElement);
           }
       }
   } else if (captionElement)
   {
     dom.removeChild(captionElement);
   }
   ```

1. To save your changes, click **[!UICONTROL Save All]**.

## Best practices and limitations {#best-practices-limitations-tips}

* A plain text field is not the only type of input allowed for the value of the caption element. You can use any ExtJS widget, that provides the caption’s value through its `getValue()` method.
* To add editing capabilities for more elements and attributes, ensure that:

  * The `itemId` property for each corresponding field is set to the name of the appropriate DOM attribute (`TablePropertiesDialog`).
  * The attribute is set and/or removed on the DOM element explicitly (`Table`).
-->

>[!MORELIKETHIS]
>
>* [WCAG 표준에 대한 빠른 안내](/help/onboarding/accessibility/quick-guide-wcag.md)
>* [Experience Manager에서 액세스 가능한 컨텐츠를 만드는 방법](/help/sites-cloud/authoring/fundamentals/accessible-content.md)

