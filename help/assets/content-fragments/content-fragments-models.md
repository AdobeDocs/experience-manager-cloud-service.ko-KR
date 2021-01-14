---
title: 컨텐츠 조각 모델
description: 컨텐츠 조각 모델은 구조화된 컨텐츠와 함께 컨텐츠 조각을 생성하는 데 사용됩니다.
translation-type: tm+mt
source-git-commit: da8fcf1288482d406657876b5d4c00b413461b21
workflow-type: tm+mt
source-wordcount: '1189'
ht-degree: 43%

---


# 컨텐츠 조각 모델 {#content-fragment-models}

>[!CAUTION]
>
>요청에 따라 컨텐츠 조각 전달용 AEM GraphQL API를 사용할 수 있습니다.
>
>AEM용 API를 Cloud Service 프로그램으로 활성화하려면 [Adobe 지원](https://experienceleague.adobe.com/?lang=en&amp;support-solution=General#support)에 문의하십시오.

컨텐츠 조각 모델은 [컨텐츠 조각](/help/assets/content-fragments/content-fragments.md)에 대한 컨텐츠 구조를 정의합니다.

컨텐츠 조각 모델을 사용하려면 다음을 수행합니다.

1. [인스턴스에 대한 컨텐츠 조각 모델 기능 활성화](/help/assets/content-fragments/content-fragments-configuration-browser.md)
1. [컨텐츠 조각 모델 생성](#creating-a-content-fragment-model) 및  [구성](#defining-your-content-fragment-model)
1. [컨텐츠 조각을 ](#enabling-disabling-a-content-fragment-model) 만들 때 사용할 컨텐츠 조각을 만들 때 사용할 컨텐츠 조각 모델을 활성화합니다.

## 컨텐츠 조각 모델 만들기 {#creating-a-content-fragment-model}

1. **도구**, **자산**&#x200B;으로 이동한 후 **컨텐츠 조각 모델**&#x200B;을 엽니다.
1. [구성](/help/assets/content-fragments/content-fragments-configuration-browser.md)에 적절한 폴더로 이동합니다.
1. **만들기**&#x200B;를 사용하여 마법사를 엽니다.

   >[!CAUTION]
   >
   >[컨텐츠 조각 모델 사용이 활성화되지 않은](/help/assets/content-fragments/content-fragments-configuration-browser.md) 경우 **만들기** 옵션을 사용할 수 없습니다.

1. **모델 제목**&#x200B;을 지정합니다. **태그**&#x200B;와 필요한 경우 **설명**&#x200B;을 추가할 수도 있습니다.

   ![제목 및 설명](assets/cfm-models-02.png)

1. **만들기**&#x200B;를 사용하여 빈 모델을 저장합니다. 작업의 성공을 나타내는 메시지가 표시되면 **열기**&#x200B;를 선택하여 모델을 즉시 편집하거나 **완료**&#x200B;를 선택하여 콘솔로 돌아갈 수 있습니다.

## 컨텐츠 조각 모델 정의 {#defining-your-content-fragment-model}

컨텐츠 조각 모델은 **[데이터 유형](#data-types)** 선택을 사용하여 결과 컨텐츠 조각 구조를 효과적으로 정의합니다. 모델 편집기를 사용하여 데이터 유형의 인스턴스를 추가한 다음 이를 구성하여 필수 필드를 만들 수 있습니다.

>[!CAUTION]
>
>기존 컨텐츠 조각 모델을 편집하면 종속된 조각이 영향을 받을 수 있습니다.

1. **도구**, **자산**&#x200B;으로 이동한 후 **컨텐츠 조각 모델**&#x200B;을 엽니다.

1. 컨텐츠 조각 모델을 포함하는 폴더로 이동합니다.
1. **편집**&#x200B;에 필요한 모델을 엽니다. 빠른 작업을 사용하거나, 모델을 선택한 후 도구 모음에서 작업을 선택하십시오.

   모델 편집기를 열면 다음과 같이 표시됩니다.

   * 왼쪽: 이미 정의된 필드
   * 오른쪽: 필드를 만드는 데 사용할 수 있는 **데이터 유형**(필드가 만들어지면 사용할 **속성**)

   >[!NOTE]
   >
   >필드가 **필수**&#x200B;이면 왼쪽 창에 표시되는 **레이블**&#x200B;이 지정된 레이블은 별표(*****)로 표시됩니다.

1. **필드를 추가하려면**

   * 필수 데이터 유형을 필드에 필요한 위치로 드래그합니다.

   * 모델에 필드가 추가되면 오른쪽 패널에 그 특정 데이터 유형에 대해 정의할 수 있는 **속성**이 표시됩니다. 여기에서 해당 필드에 필요한 사항을 정의할 수 있습니다.
많은 속성은 자체 설명이므로 자세한 내용은 [속성](#properties)을 참조하십시오.

1. **필드를 제거하려면**

   필요한 필드를 선택한 후 휴지통 아이콘을 클릭/탭합니다. 작업을 확인하는 메시지가 나타납니다.

1. 필요한 모든 필드를 추가하고 필요에 따라 관련 속성을 정의합니다.

1. **저장**&#x200B;을 선택하여 정의를 유지합니다.

<!--
## Defining your Content Fragment Model {#defining-your-content-fragment-model}

The content fragment model effectively defines the structure of the resulting content fragments using a selection of **[Data Types](#data-types)**. Using the model editor you can add instances of the data types, then configure them to create the required fields:

>[!CAUTION]
>
>Editing an existing content fragment model can impact dependent fragments.

1. Navigate to **Tools**, **Assets**, then open **Content Fragment Models**.

1. Navigate to the folder holding your content fragment model.
1. Open the required model for **Edit**; use either the quick action, or select the model and then the action from the toolbar.

   Once open the model editor shows:

    * left: fields already defined
    * right: **Data Types** available for creating fields (and **Properties** for use once fields have been created)

   >[!NOTE]
   >
   >When a field as **Required**, the **Label** indicated in the left pane will be marked with an asterix (**&#42;**).

   ![properties](assets/cfm-models-03.png)

1. **To Add a Field**

    * Drag a required data type to the required location for a field:

      ![data type to field](assets/cfm-models-04.png)

    * Once a field has been added to the model, the right panel will show the **Properties** that can be defined for that particular data type. Here you can define what is required for that field. 
      Many properties are self-explanatory, for additional details see [Properties](#properties).
      For example:

      ![field properties](assets/cfm-models-05.png)

1. **To Remove a Field**

   Select the required field, then click/tap the trash-can icon. You will be asked to confirm the action.

   ![remove](assets/cfm-models-06.png)

1. Add all required fields, and define the related properties, as required. For example:

   ![save](assets/cfm-models-07.png)

1. Select **Save** to persist the definition.
-->

## 데이터 유형 {#data-types}

모델을 정의하는 데 사용할 수 있는 데이터 유형은 다음과 같습니다.

* **한 줄 텍스트**
   * 단일 텍스트 줄의 필드를 하나 이상 추가합니다.최대 길이를 정의할 수 있습니다.
* **여러 줄 텍스트**
   * 서식 있는 텍스트, 일반 텍스트 또는 마크다운일 수 있는 텍스트 영역
* **번호**
   * 숫자 필드를 하나 이상 추가합니다.
* **부울**
   * 부울 확인란 추가
* **날짜 및 시간**
   * 날짜 및/또는 시간 추가
* **열거**
   * 확인란, 라디오 단추 또는 드롭다운 필드 추가
* **태그**
   * 조각 작성자가 태그 영역에 액세스하고 선택할 수 있습니다.
* **컨텐츠 참조**
   * 모든 유형의 다른 컨텐츠를 참조합니다.은(는) [중첩 컨텐트 만들기](#using-references-to-form-nested-content)에 사용할 수 있습니다.

<!--
* **Fragment Reference**
  * References other content fragments; can be used to [create nested content](#using-references-to-form-nested-content)
  * The data type can be configured to allow fragment authors to:
    * Edit the referenced fragment directly.
    * Create a new content fragment, based on the appropriate model  
* **JSON Object**
  * Allows the content fragment author to enter JSON syntax into the corresponding elements of a fragment. 
    * To allow AEM to store direct JSON that you have copy/pasted from another service.
    * The JSON will be passed through, and output as JSON in GraphQL.
    * Includes JSON syntax-highlighting, auto-complete and error-highlighting in the content fragment editor.
-->

## 속성 {#properties}

많은 속성이 자체 설명이므로 특정 속성에 대한 자세한 내용은 다음과 같습니다.

* **렌더링조각**
에서 필드를 구현하거나 렌더링하기 위한 다양한 옵션입니다. 종종 이 기능을 사용하면 작성자가 필드의 단일 인스턴스를 표시할지 또는 여러 인스턴스를 만들 수 있는지 정의할 수 있습니다.

* **필드**
레이블에 
**필드** 레이블은 속성  **이름을** 자동으로 생성하며, 필요한 경우 수동으로 업데이트할 수 있습니다.

* **ValidationBasic**
유효성 검사는 Requirements 속성과 같은 메커니즘에 의해  **** 제공됩니다. 일부 데이터 유형에는 추가 유효성 검사 필드가 있습니다. 자세한 내용은 [유효성 검사](#validation)를 참조하십시오.

* 데이터 유형 **여러 줄 텍스트**&#x200B;의 경우 **기본 유형**&#x200B;을 다음 중 하나로 정의할 수 있습니다.

   * **리치 텍스트**
   * **Markdown**
   * **일반 텍스트**

   지정하지 않으면 이 필드에 기본값인 **리치 텍스트**&#x200B;가 사용됩니다.

   컨텐츠 조각 모델의 **기본 유형** 변경은 해당 조각을 편집기에서 열고 저장한 후에 기존 관련 컨텐츠 조각에만 적용됩니다.

<!--
* **Translatable**
  Checking the "Translatable" checkbox on a field in CF model editor will

  * Ensure the field's property name is added in translation config, context `/content/dam/<tenant>`, if not already present. 
  * For GraphQL: set a `<translatable>` property on the Content Fragment field to `yes`, to allow GraphQL query filter for JSON output with only translatable content.

* See **[Fragment Reference (Nested Fragments)](#fragment-reference-nested-fragments)** for more details about that specific data type and its properties.
-->

## 유효성 검사 {#validation}

이제 다양한 데이터 유형에는 결과 조각에서 컨텐츠를 입력할 때 유효성 검사 요구 사항을 정의할 수 있는 가능성이 포함됩니다.

* **한 줄 텍스트**
   * 미리 정의된 regex와 비교합니다.
* **번호**
   * 특정 값을 확인합니다.

<!--
* **Content Reference**
  * Test for specific types of content.
  * Only images within a predefined range of width and height (in pixels) can be referenced. 
  * Only assets of specified file size or smaller can be referenced. 
  * Only predefined file types can be referenced.
  * No more than the predefined number of assets can be referenced. 
  * No more than the predefined number of fragments can be referenced.
* **Fragment Reference**
  * Test for a specific content fragment model.
-->

<!--
## Using References to form Nested Content {#using-references-to-form-nested-content}

Content Fragments can form nested content, using either of the following data types:

* **[Content Reference](#content-reference)**
  * Provides a simple reference to other content; of any type.
  * Can be configured for a one or multiple references (in the resulting fragment).

* **[Fragment Reference](#fragment-reference-nested-fragments)** (Nested Fragments)
  * References other fragments, dependent on the specific models specified.
  * Allows you to include/retrieve structured data.
    >[!NOTE]
    >
    >This method is of particular interest in conjunction with [Headless Content Delivery using Content Fragments with GraphQL](/help/assets/content-fragments/content-fragments-graphql.md).
  * Can be configured for one or multiple references (in the resulting fragment)..

>[!NOTE]
>
>AEM has a recurrence protection for:
>
>* Content References
>  This prevents the user from adding a reference to the current fragment. This may lead to an empty Fragment Reference picker dialog.
>
>* Fragment References in GraphQL 
>  If you create a deep query that returns multiple Content Fragments referenced by each another, it will return null at first occurence.

### Content Reference {#content-reference}

The Content Reference allows you to render content from another source; for example, image or content fragment.

In addition to standard properties you can specify:

* The **Root Path** for any referenced content.
* The content types that can be referenced.
* Limitations for file sizes.
* Image restraints.
-->

<!-- Check screenshot - might need update

   ![Content Reference](assets/cfm-content-reference.png)
-->

<!--
### Fragment Reference (Nested Fragments) {#fragment-reference-nested-fragments}

The Fragment Reference references one, or more, content fragments. This feature of particular interest when retrieving content for use in your app, as it allows you to retrieve structured data with multiple layers.

For example:

* A model defining details for an employee; these include:
  * A reference to the model that defines the employer (company)

```xml
type EmployeeModel {
    name: String
    firstName: String
    company: CompanyModel
}

type CompanyModel {
    name: String
    street: String
    city: String
}
```

>[!NOTE]
>
>This is of particular interest in conjunction with [Headless Content Delivery using Content Fragments with GraphQL](/help/assets/content-fragments/content-fragments-graphql.md).

In addition to standard properties you can define:

* **Render As**:

  * **multifield** - the fragment author can create multiple, individual, references

  * **fragmentreference** - allows the fragment author to select a single reference to a fragment

* **Model Type**
  Multiple models can be selected. When authoring the Content Fragment any referenced fragments must have been created using these models.

* **Root Path**
  This specifies a root path for any fragments referenced.

* **Allow Fragment Creation**

  This will allow the fragment author to create a new fragment based on the appropriate model.
-->

<!--
  * **fragmentreferencecomposite** - allows the fragment author to build a composite, by selecting multiple fragments
-->

<!-- Check screenshot - might need update

   ![Fragment Reference](assets/cfm-fragment-reference.png)
-->

<!--
>[!NOTE]
>
>A recurrence protection mechanism is in place. It prohibits the user from selecting the current Content Fragment in the Fragment Reference. This may lead to an empty Fragment Reference picker dialog.
>
>There is also a recurrence protection for Fragment References in GraphQL. If you create a deep query across two Content Fragments that reference each other, it will return null.
-->

## 컨텐츠 조각 모델 {#enabling-disabling-a-content-fragment-model} 활성화 또는 비활성화

컨텐츠 조각 모델의 사용을 완벽하게 제어하기 위해 설정할 수 있는 상태가 있습니다.

### 컨텐츠 조각 모델 {#enabling-a-content-fragment-model} 활성화

모델이 만들어지면 다음을 수행할 수 있도록 활성화해야 합니다.

* 새 컨텐츠 조각을 만들 때 선택할 수 있습니다.
* 컨텐츠 조각 모델 내에서 참조할 수 있습니다.
* GraphQL에서 사용할 수 있습니다.따라서 스키마가 생성됩니다.

다음 중 하나로 플래그가 지정된 모델을 활성화하려면:

* **초안** :mew(활성화되지 않음).
* **사용 안 함** :이 특별히 비활성화되어 있습니다.

다음 중 하나에서 **Enable** 옵션을 사용합니다.

* 필수 모델이 선택되면 상단 도구 모음입니다.
* 해당 빠른 작업(필요한 모델 위에 마우스 놓기)입니다.

![초안 또는 사용 불가능한 모델 활성화](assets/cfm-status-enable.png)

### 컨텐츠 조각 모델 {#disabling-a-content-fragment-model} 비활성화

다음과 같은 방법으로 모델을 비활성화할 수도 있습니다.

* 모델은 더 이상 *new* 컨텐츠 조각을 만드는 기준으로 사용할 수 없습니다.
* 하지만:
   * GraphQL 스키마는 계속 생성되며 여전히 쿼리할 수 있습니다(JSON API에 영향을 주지 않기 위해).
   * 모델의 모든 컨텐츠 조각은 GraphQL 끝점에서 쿼리하여 반환할 수 있습니다.
* 모델을 더 이상 참조할 수 없지만 기존 참조는 그대로 유지되며 GraphQL 끝점에서 쿼리하여 반환할 수 있습니다.

**활성화됨**&#x200B;으로 플래그가 지정된 모델을 비활성화하려면 다음 중 하나에서 **비활성화** 옵션을 사용합니다.

* 필수 모델이 선택되면 상단 도구 모음입니다.
* 해당 빠른 작업(필요한 모델 위에 마우스 놓기)입니다.

![활성화된 모델 비활성화](assets/cfm-status-disable.png)

## 컨텐츠 조각 모델 삭제 {#deleting-a-content-fragment-model}

>[!CAUTION]
컨텐츠 조각 모델을 삭제하면 종속된 조각이 영향을 받을 수 있습니다.

컨텐츠 조각 모델을 삭제하려면

1. **도구**, **자산**&#x200B;으로 이동한 후 **컨텐츠 조각 모델**&#x200B;을 엽니다.

1. 컨텐츠 조각 모델을 포함하는 폴더로 이동합니다.
1. 모델을 선택한 후 도구 모음에서 **삭제**&#x200B;를 클릭합니다.

   >[!NOTE]
   참조되는 모델의 경우 경고가 표시됩니다. 적절하게 조치하십시오.

## 컨텐츠 조각 모델 게시 {#publishing-a-content-fragment-model}

컨텐츠 조각 모델은 종속된 컨텐츠 조각이 게시될 때/게시되기 전에 게시해야 합니다.

컨텐츠 조각 모델을 게시하려면

1. **도구**, **자산**&#x200B;으로 이동한 후 **컨텐츠 조각 모델**&#x200B;을 엽니다.

1. 컨텐츠 조각 모델을 포함하는 폴더로 이동합니다.
1. 모델을 선택한 후 도구 모음에서 **게시**를 클릭합니다.
게시된 상태가 콘솔에 표시됩니다.

   >[!NOTE]
   모델이 아직 게시되지 않은 컨텐츠 조각을 게시하는 경우 선택 목록에 이것이 표시되고 모델이 조각과 함께 게시됩니다.

## 컨텐츠 조각 모델 {#unpublishing-a-content-fragment-model} 게시 취소

컨텐츠 조각 모델은 조각에서 참조되지 않는 경우 게시 취소할 수 있습니다.

컨텐츠 조각 모델을 게시 취소하려면 다음을 수행하십시오.

1. **도구**, **자산**&#x200B;으로 이동한 후 **컨텐츠 조각 모델**&#x200B;을 엽니다.

1. 컨텐츠 조각 모델을 포함하는 폴더로 이동합니다.
1. 모델을 선택하고 도구 모음에서 **게시 취소**를 선택합니다.
게시된 상태가 콘솔에 표시됩니다.
