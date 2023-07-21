---
title: 적응형 Forms을 만드는 방법
description: 을 사용하여 적응형 양식을 만드는 방법 알아보기 [!DNL Experience Manager Forms]. 적응형 Forms은 정보 수집 및 처리를 간소화하는 반응형 HTML 5 양식입니다. 양식 데이터 모델 및 XML 또는 JSON 스키마를 기반으로 적응형 양식을 만드는 방법에 대해 자세히 알아보십시오.
feature: Adaptive Forms
role: User, Developer
level: Beginner
exl-id: 38ca5eea-793b-420b-ae60-3a0bd83caf00
source-git-commit: 86da8e784e3e5ff034efdb9186cf134d4b1c6e9c
workflow-type: tm+mt
source-wordcount: '1576'
ht-degree: 4%

---

# 적응형 양식 만들기(기초 구성 요소) {#creating-an-adaptive-form}

<span class="preview"> Adobe은 현대적이고 확장 가능한 데이터 캡처를 사용할 것을 권장합니다 [핵심 구성 요소](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html) 대상 [새 적응형 Forms 만들기](/help/forms/creating-adaptive-form-core-components.md) 또는 [AEM Sites 페이지에 적응형 Forms 추가](/help/forms/create-or-add-an-adaptive-form-to-aem-sites-page.md). 이러한 구성 요소는 적응형 Forms 작성의 중요한 발전을 나타내어 인상적인 사용자 경험을 보장합니다. 이 문서에서는 기초 구성 요소를 사용하여 적응형 Forms을 작성하는 이전 방법에 대해 설명합니다. </span>

| 버전 | 문서 링크 |
| -------- | ---------------------------- |
| AEM 6.5 | [여기를 클릭하십시오.](https://experienceleague.adobe.com/docs/experience-manager-65/forms/getting-started/create-first-adaptive-form/create-your-first-adaptive-form.html) |
| AEM as a Cloud Service | 이 문서 |


적응형 Forms을 사용하면 매력적인 반응형, 동적 및 적응형 양식을 만들 수 있습니다. AEM Forms은 적응형 Forms을 신속하게 작성할 수 있는 비즈니스 사용자 친화적 마법사를 제공합니다. 마법사에는 미리 구성된 템플릿, 스타일, 필드 및 제출 옵션을 손쉽게 선택하여 적응형 양식을 만들 수 있는 빠른 탭 탐색 기능이 있습니다.

시작하기 전에 사용 가능한 Forms 구성 요소 유형에 대해 알아보십시오.

* [적응형 Forms 핵심 구성 요소](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html?lang=ko) 는 표준화된 데이터 캡처 구성 요소입니다. 이 구성 요소는 맞춤화 기능을 제공하고, 개발 시간을 단축하고, 유지 관리 비용을 줄여 디지털 등록 경험을 개선합니다. 개발자는 이러한 구성 요소를 손쉽게 맞춤화하고 스타일을 지정할 수 있습니다. Adobe은 이러한 현대적이고 확장 가능한 구성 요소를 활용하여 적응형 Forms을 개발할 것을 권장합니다.

* [적응형 Forms Foundation 구성 요소](creating-adaptive-form.md) 는 클래식(이전) 데이터 캡처 구성 요소입니다. 적응형 양식 기반의 기존 기초 구성 요소를 편집하는 데 계속 사용할 수 있습니다. Adobe 새 양식을 만드는 경우 다음을 사용하는 것이 좋습니다.  [적응형 Forms 핵심 구성 요소](creating-adaptive-form-core-components.md) 를 클릭하여 적응형 Forms을 만듭니다.



<!-- 

You can choose to create an Adaptive Form based on a form model or schema or without a form model. It is important to carefully choose the form model that not only suits your requirements but extends your existing infrastructural investments and assets. You get to choose from the following options to create an Adaptive Form: 

-->

![적응형 양식 만들기 마법사](/help/release-notes/assets/wizard.png)

<!-- 

Adaptive Forms allow you to create forms that are engaging, responsive, dynamic, and adaptive. [!DNL AEM Forms] provides an intuitive wizard and out-of-the-box components to create Adaptive Forms. You can choose to create an Adaptive Form based on a form model or schema or without a form model. It is important to carefully choose the form model that not only suits your requirements but extends your existing infrastructural investments and assets. You get to choose from the following options to create an Adaptive Form:

* **Using a form data model**
  [Data integration](data-integration.md) lets you integrate entities and services from disparate data sources in to a Form Data Model that you can use to create Adaptive Forms. Choose Form Data Model if the Adaptive Form you are creating involves fetching and write data from and to multiple data source.

  <!--  * **Using an XDP Form Template**
   It is an ideal form model if you have investments in XFA-based or XDP forms. It provides a direct way to convert your XFA-based forms into Adaptive Forms. Any existing XFA rules are retained in the associated Adaptive Forms. The resulting Adaptive Forms support XFA constructs, such as validations, events, properties, and patterns. 

* **Using an XML Schema Definition (XSD) or a JSON Schema**
   XML and JSON schemas represent the structure in which data is produced or consumed by the back-end system in your organization. You can associate the schema to an Adaptive Form and use its elements to add dynamic content to the Adaptive Form. The elements of the schema are available for use in the Data Model Objects tab of the Content browser when authoring Adaptive Forms.

* **Using none or without a form model**
   Adaptive Forms created with this option do not use any form model. The data XML generated from such forms has flat structure with fields and corresponding values. -->

## 전제 조건

적응형 양식을 만들려면 다음 항목이 필요합니다.

* **권한**: 사용자 추가 [!DNL forms-users] 적응형 양식을 만들 수 있는 권한을 제공합니다. 양식별 사용자 그룹의 자세한 목록은 다음을 참조하십시오. [그룹 및 권한](forms-groups-privileges-tasks.md).

* **적응형 양식 테마**: 테마에는 구성 요소 및 패널에 대한 스타일 세부 사항이 포함되어 있습니다. 스타일에는 배경색, 상태 색상, 투명도, 정렬 및 크기와 같은 속성이 포함됩니다. 테마를 적용하면 지정된 스타일이 해당 구성 요소에 반영됩니다. 다음을 수행할 수 있습니다. [새 테마 만들기](themes.md) 또는 [기존 테마 가져오기](import-export-forms-templates.md#uploading-a-theme). 를 배포할 수도 있습니다. [최신 Archetype](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/using.html#create-project) 일부 샘플 테마의 경우.

* **적응형 양식 템플릿**: 템플릿은 기본 구조를 제공하고 적응형 양식의 모양(레이아웃 및 스타일)을 정의합니다. 여기에는 특정 속성 및 콘텐츠 구조를 포함하는 미리 형식이 지정된 구성 요소가 있습니다. 또한 테마 및 제출 액션을 정의하는 옵션을 제공합니다. 테마는 모양과 느낌을 정의하고 제출 작업은 적응형 양식 제출 시 수행할 작업을 정의합니다. (예: 수집된 데이터를 데이터 소스로 전송) 클라우드 서비스는 두 가지 유형의 템플릿을 지원합니다.

   * **편집 가능한 템플릿**: 다음 작업을 수행할 수 있습니다 [새로 만들기](template-editor.md) 또는 [편집 가능한 기존 템플릿 가져오기](migrate-to-forms-as-a-cloud-service.md). 를 배포할 수도 있습니다. [최신 Archetype](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/using.html?lang=en#:~:text=The%20AEM%20Archetype%20is%20made%20up%20of%20modules%3A,and%20request%20filters.%20it.tests%3A%20are%20Java 기반%20integration%20tests.) 몇 가지 샘플 편집 가능한 템플릿을 가져올 수 있습니다.

   * **정적 템플릿**: 기존 템플릿이며, Adobe Managed Services(AMS) 및 온프레미스 AEM Forms 설치(AEM 6.5 Forms 또는 이전 버전)에서 마이그레이션하는 고객에게만 권장됩니다. 이를 통해 정적 템플릿에 대한 기존 투자를 계속 사용할 수 있습니다. 새 적응형 양식을 만들 때 편집 가능한 템플릿을 사용하는 것이 좋습니다.



## 적응형 양식 만들기(기초 구성 요소) {#create-an-adaptive-form-foundation-components}

1. 액세스 [!DNL Experience Manager Forms] 작성자 인스턴스. 클라우드 인스턴스 또는 로컬 개발 인스턴스일 수 있습니다.

1. Experience Manager 로그인 페이지에 자격 증명을 입력합니다.

   로그인 후 왼쪽 상단 모서리에서 을 누릅니다 **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Forms]** > **[!UICONTROL Forms 및 문서]**.

1. 누르기 **[!UICONTROL 만들기]**  > **[!UICONTROL 적응형 Forms]**. 마법사가 열립니다.
1. 소스 탭에서 템플릿을 선택합니다.

   * 편집 가능한 템플릿을 선택하면 템플릿에 지정된 테마 및 제출 액션이 자동으로 선택되고 **[!UICONTROL 만들기]** 버튼이 활성화되었습니다. 다음 페이지로 이동할 수 있습니다. **[!UICONTROL 스타일]** 또는 **[!UICONTROL 제출]** 탭을 사용하여 다른 테마를 선택하거나 작업을 제출할 수 있습니다. 선택한 편집 가능 템플릿이 테마를 지정하지 않으면 만들기 버튼이 비활성화됩니다. 다음 페이지로 이동할 수 있습니다. **[!UICONTROL 스타일]** 탭을 사용하여 테마를 수동으로 선택할 수 있습니다.

     >[!NOTE]
     >
     > 다음을 만들 수도 있습니다. [!UICONTROL 기록 문서] 적응형 Forms 편집기를 사용하는 템플릿. 자세한 내용은 [적응형 양식 편집기의 기록 지원 문서](/help/forms/generate-document-of-record-for-non-xfa-based-adaptive-forms.md#document-of-record-support-in-adaptive-form-editor-dor-support-in-adaptiveform).

   * 정적 템플릿을 선택하면 데이터, 스타일, 제출, 전달 및 미리 보기 옵션을 사용할 수 없습니다. 새 적응형 양식을 만들 때 편집 가능한 템플릿을 사용하는 것이 좋습니다.

1. 다음에서 **[!UICONTROL 스타일]** 탭에서 테마를 선택합니다.

   * 선택한 템플릿에서 테마를 지정하면 마법사에서 테마가 자동으로 선택됩니다. 스타일 탭에서 다른 테마를 선택할 수도 있습니다.
   * 선택한 템플릿에서 테마를 지정하지 않은 경우 스타일 탭을 사용하여 테마를 선택할 수 있습니다. 다음 **[!UICONTROL 만들기]** 테마를 선택한 후에만 버튼이 활성화됩니다.

1. (선택 사항) **[!UICONTROL 데이터]** 탭에서 데이터 모델을 선택합니다.

   * **양식 데이터 모델**: A [양식 데이터 모델](data-integration.md) 서로 다른 데이터 소스의 엔티티와 서비스를 적응형 양식에 통합할 수 있습니다. 생성 중인 적응형 양식에 여러 데이터 소스에서 데이터를 가져와 작성하는 작업이 포함된 경우 양식 데이터 모델 을 선택합니다.

   * **JSON 스키마**: [JSON 스키마](adaptive-form-json-schema-form-model.md) 조직의 백엔드 시스템에서 데이터를 생성하거나 사용하는 구조를 나타냅니다. 스키마를 적응형 양식에 연결하고 해당 요소를 사용하여 동적 콘텐츠를 적응형 양식에 추가할 수 있습니다. 적응형 Forms을 작성할 때 콘텐츠 브라우저의 데이터 모델 개체 탭에서 스키마 요소를 사용할 수 있으며 모든 필드는 새로 만든 적응형 양식에도 추가됩니다.

   기본적으로 데이터 모델의 모든 필드가 선택됩니다. 적응형 양식을 만들면 선택한 모든 데이터 모델 필드가 해당 적응형 양식 구성 요소로 변환됩니다. 마법사는 적응형 양식에 포함해야 하는 필드만 선택할 수 있는 확인란을 제공합니다.

   <!-- 
   
   If your JSON schema contains a fragment, the fragment is considered a single unit. You can select or deselect a complete fragment and all the fields of the fragment are selected or deselected accordingly. 
   
   -->

1. 다음에서 **[!UICONTROL 제출]** 탭에서 제출 액션을 선택합니다.

   * 템플릿을 선택하면 템플릿에 지정된 제출 작업이 자동으로 선택됩니다. 제출 탭에서 다른 제출 액션을 선택할 수 있습니다. 다음 **[!UICONTROL 제출]** 탭에는 사용 가능한 모든 제출 작업이 표시됩니다.

   * 선택한 템플릿에서 제출 액션을 지정하지 않은 경우 **[!UICONTROL 제출]** 제출 액션을 선택할 수 있는 탭

1. (선택 사항) 게재 탭에서 적응형 양식의 게시 또는 게시 취소 날짜를 지정할 수 있습니다.

1. 누르기 **[!UICONTROL 만들기]**. 적응형 양식을 저장할 제목, 이름 및 위치를 지정하는 대화 상자가 나타납니다.

   * **[!UICONTROL 제목]** 양식의 표시 이름을 지정합니다. 제목을 통해 다음에서 양식을 식별할 수 있습니다. [!DNL Experience Manager Forms] 사용자 인터페이스.
   * **[!UICONTROL 이름:]** 양식 이름을 지정합니다. 지정된 이름의 노드가 저장소에 생성됩니다. 제목 입력을 시작하면 이름 필드에 대한 값이 자동으로 생성됩니다. 제안 값을 변경할 수 있습니다. 이름 필드에는 영숫자, 하이픈 및 밑줄만 포함할 수 있습니다. 잘못된 모든 입력은 하이픈으로 대체됩니다.
   * **[!UICONTROL 경로:]** 적응형 양식을 저장할 위치를 지정합니다. 다음 위치에서 적응형 양식을 직접 저장할 수 있습니다. `/content/dam/formsanddocuments` 또는 다음과 같은 폴더를 생성합니다. `/content/dam/formsanddocuments/adaptiveforms` 을 클릭하여 적응형 양식을 저장하십시오. 경로에서 폴더를 사용하기 전에 폴더를 만들어야 합니다. 다음 **[!UICONTROL 경로:]** 필드는 폴더를 자동으로 만들지 않습니다.

1. 누르기 **[!UICONTROL 만들기]**. 적응형 양식이 만들어지고 적응형 Forms 편집기에서 열립니다. 템플릿에서 사용할 수 있는 콘텐츠가 편집기에 표시됩니다. 또한 필요에 따라 새로 만든 양식을 사용자 지정할 수 있는 사이드바가 표시됩니다.

   적응형 양식 유형에 따라 연관된 양식 요소에 있는 양식 요소 <!--XFA form template, XML schema or --> JSON 스키마 또는 양식 데이터 모델은 **[!UICONTROL 데이터 모델 개체]** 의 탭 **[!UICONTROL 컨텐츠 브라우저]** 를 클릭합니다. 이러한 요소를 드래그 앤 드롭하여 적응형 양식을 작성할 수도 있습니다.

<!-- ## Create an Adaptive Form based on a Form Data Model {#fdm}

[Data integration](data-integration.md) lets you integrate multiple data sources and bring their entities and services together to create a form data model. It is an extension of JSON schema. You can use a Form Data Model to create an Adaptive Form. The entities or data model objects configured in a Form Data Model are available as data model objects for form authoring. They are bound to respective data sources and used to prefill a form and write submitted data back to the respective data sources. You can also call services configured in a Form Data Model using Adaptive Form rules.

To use a Form Data Model for creating an Adaptive Form:

1. In Form Model tab on Add Properties screen, select **[!UICONTROL Form Data Model]** in the **[!UICONTROL Select From]** drop-down list.

   ![Create an Adaptive Form](assets/create-af-1-1.png)

1. Tap to expand **[!UICONTROL Select Form Data Model]**. All available form data models are listed.Select a from data model.

>[!NOTE]
>
>You can also change the Form Data Model for an Adaptive Form. For detailed steps, see [Edit Form Model properties of an Adaptive Form](#edit-form-model).

## Create an Adaptive Form based on XML or JSON schema {#create-an-adaptive-form-based-on-xml-or-json-schema}

XML and JSON schemas represent the structure in which data is produced or consumed by the back-end system in your organization. You can associate a schema to an Adaptive Form and use its elements to add dynamic content to the Adaptive Form. The elements of the schema are available in the Data Model Object tab of the content browser for authoring Adaptive Forms. You can drag-drop the schema elements to build the form.

See the following documents to understand how to design XML or JSON schema for authoring Adaptive Forms.

* [Creating Adaptive Forms using XML schema](adaptive-form-xml-schema-form-model.md)
* [Creating Adaptive Forms using JSON schema](adaptive-form-json-schema-form-model.md)

Do the following to use XML or JSON schema as form model for an Adaptive Form:

1. On the **[!UICONTROL Add Properties]** step of Adaptive Form creation page, tap on the **[!UICONTROL Form Model]** tab.
1. In the Form Model tab, select **[!UICONTROL Schema]** from the **[!UICONTROL Select From]** drop-down field.

1. Tap **[!UICONTROL Select Schema]** and do one of the following:

    * **[!UICONTROL Upload from disk]** - Select this option and tap Upload Schema Definition to browse and upload an XML schema or JSON schema from your file system. The uploaded schema file resides with the form and is not accessible to other Adaptive Forms.
    * **[!UICONTROL Search in repository]** - Select this option to select from the list of schema definition files available in the repository. Select the XML or JSON schema file as form model. The selected schema is associated with the form by reference and is accessible for use in other Adaptive Forms.

      Ensure that the JSON schema filename ends with **.schema.json**. For example: mySchema.schema.json

   ![Selecting XML or JSON schema](assets/upload-schema.png)
**Figure:** *Selecting XML or JSON schema*

1. (For XML schema only) After you select or upload an XML Schema, specify a root element of the selected XSD file to map with the Adaptive Form.

   ![Selecting XSD root element](assets/xsd-root-element.png)
**Figure:** *Selecting XSD root element*

>[!NOTE]
>
>You can also change the schema for an Adaptive Form. For detailed steps, see [Edit Form Model properties of an Adaptive Form](#edit-form-model). -->

## 적응형 양식의 양식 모델 속성 편집 {#edit-form-model}

적응형 양식에 대한 양식 모델(JSON 기반 또는 양식 데이터 모델)을 변경할 수 있습니다. 한 양식 모델에서 다른 양식 모델로 변경할 수 없습니다.

1. 적응형 양식을 선택하고 **속성** 아이콘.
1. 를 엽니다. **[!UICONTROL 양식 모델]** 을(를) 탭하고 다음 중 하나를 수행합니다.

   * 적응형 양식에 양식 모델이 없는 경우 다른 양식 모델을 선택하고 그에 따라 을(를) 선택할 수 있습니다 <!-- a form template, --> XML 또는 JSON 스키마 또는 양식 데이터 모델.
   * 적응형 양식이 양식 모델을 기반으로 하는 경우 다른 양식을 선택할 수 있습니다 <!-- form template, --> 동일한 양식 모델에 대한 XML 또는 JSON 스키마 또는 양식 데이터 모델.

1. 누르기 **[!UICONTROL 저장]** 속성을 저장합니다.

적응형 양식 편집기 또는 적응형 양식 템플릿 편집기에서 양식 모델 속성을 수정할 수도 있습니다.

1. 다음 항목 선택 **[!UICONTROL 적응형 양식 컨테이너(루트)]** 구성 요소.
1. 클릭 ![구성 아이콘](/help/forms/assets/configure-icon.svg) 아이콘을 클릭하여 엽니다. **[!UICONTROL 속성]** 적응형 양식 컨테이너.
1. 다음 항목 선택 **[!UICONTROL 데이터 모델]** 을(를) 탭하고 다음 중 하나를 수행합니다.

   * 적응형 양식에 양식 모델이 없는 경우 양식 모델을 선택하고 그에 따라 을(를) 선택할 수 있습니다 <!-- a form template, --> XML 또는 JSON 스키마 또는 양식 데이터 모델.
   * 적응형 양식이 양식 모델을 기반으로 하는 경우 양식 모델을 변경할 수 없습니다. 다른 항목을 선택할 수 있습니다. <!-- form template, --> 해당되는 경우 동일한 양식 모델에 대한 XML 또는 JSON 스키마 또는 양식 데이터 모델.
1. 누르기 ![저장](/help/forms/assets/check-button.png) 속성을 저장합니다.

![FDM-Schema-Support](/help/forms/assets/fdmsupport.png)

>[!NOTE]
>
> 관리 양식을 템플릿으로 저장할 수도 있습니다. 자세한 내용은 [적응형 양식을 사용하여 템플릿 만들기](/help/forms/template-editor.md#saving-an-adaptive-form-as-template-saving-adaptive-form-as-template).