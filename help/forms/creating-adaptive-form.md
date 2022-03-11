---
title: 적응형 양식을 만드는 방법
description: '을 사용하여 적응형 양식을 만드는 방법을 알아봅니다 [!DNL Experience Manager Forms]. 적응형 Forms은 정보 수집 및 처리를 간소화하는 반응형 HTML5 양식입니다. 양식 데이터 모델 및 XML 또는 JSON 스키마를 기반으로 적응형 양식을 만드는 방법에 대해 자세히 알아보십시오. '
feature: Adaptive Forms
role: User, Developer
level: Beginner
exl-id: 38ca5eea-793b-420b-ae60-3a0bd83caf00
source-git-commit: 7163eb2551f5e644f6d42287a523a7dfc626c1c4
workflow-type: tm+mt
source-wordcount: '1500'
ht-degree: 1%

---

# 적응형 양식 만들기 {#creating-an-adaptive-form}

적응형 Forms을 사용하면 매력적인 반응형, 동적 및 적응형 양식을 만들 수 있습니다. [!DNL AEM Forms] 은 응용 Forms을 만들고 사용하기 위한 직관적인 사용자 인터페이스와 기본 구성 요소를 제공합니다. 양식 모델이나 스키마를 기반으로 하거나 양식 모델 없이 적응형 양식을 만들도록 선택할 수 있습니다. 고객의 요구 사항에 부합할 뿐만 아니라 기존 인프라 투자 및 자산을 확장하는 양식 모델을 신중하게 선택하는 것이 중요합니다. 다음 옵션 중에서 선택하여 적응형 양식을 만들 수 있습니다.

* **양식 데이터 모델 사용**
   [데이터 통합](data-integration.md) 의 서로 다른 데이터 소스에서 온 엔티티와 서비스를 적응형 Forms을 만드는 데 사용할 수 있는 양식 데이터 모델에 통합할 수 있습니다. 생성 중인 적응형 양식에 여러 데이터 소스에서 데이터를 가져오고 쓰는 작업이 포함된 경우 양식 데이터 모델 을 선택합니다.

   <!--  * **Using an XDP Form Template**
   It is an ideal form model if you have investments in XFA-based or XDP forms. It provides a direct way to convert your XFA-based forms into Adaptive Forms. Any existing XFA rules are retained in the associated Adaptive Forms. The resulting Adaptive Forms support XFA constructs, such as validations, events, properties, and patterns. -->

* **XSD(XML 스키마 정의) 또는 JSON 스키마 사용**
XML 및 JSON 스키마는 조직의 백엔드 시스템에서 데이터를 생성하거나 사용하는 구조를 나타냅니다. 스키마를 적응형 양식에 연결하고 해당 요소를 사용하여 적응형 양식에 동적 컨텐츠를 추가할 수 있습니다. 적응형 Forms을 작성할 때 컨텐츠 브라우저의 데이터 모델 개체 탭에서 스키마의 요소를 사용할 수 있습니다.

* **없음 또는 양식 모델 없이 사용**
이 옵션을 사용하여 만든 응용 Forms에서는 양식 모델을 사용하지 않습니다. 이러한 양식에서 생성된 데이터 XML은 필드 및 해당 값이 있는 플랫 구조를 갖습니다.

## 전제 조건

적응형 양식을 만들려면 다음 항목이 필요합니다.

* 적응형 양식 템플릿. 템플릿은 기본 구조를 제공하고 적응형 양식의 모양(레이아웃 및 스타일)을 정의합니다. 이 파일에는 특정 속성 및 컨텐츠 구조를 포함하는 사전 형식의 구성 요소가 있습니다. 다음을 수행할 수 있습니다 [새 템플릿 만들기](template-editor.md)기존 템플릿을 가져오거나 일부 템플릿을 다운로드하여 가져옵니다 [샘플 템플릿](https://documentcloud.adobe.com/link/track?uri=urn:aaid:scds:US:3f89abe1-0ece-492a-b5af-57c73badad52).
* 적응형 양식 테마. 테마에는 구성 요소 및 패널에 대한 스타일 세부 사항이 포함되어 있습니다. 스타일은 배경색, 상태 색상, 투명도, 정렬 및 크기와 같은 속성을 포함합니다. 테마를 적용하면 지정된 스타일이 해당 구성 요소에 반영됩니다. 다음을 수행할 수 있습니다 [새 테마 만들기](themes.md), [기존 테마 가져오기](import-export-forms-templates.md#uploading-a-theme), 다운로드 및 가져오기 [샘플 테마](https://documentcloud.adobe.com/link/track?uri=urn:aaid:scds:US:2779f80e-16ba-4cd1-a96f-8e2b53f3be25).
* 사용자를 [!DNL forms-users] 적응형 양식을 만들 수 있는 권한을 그들에게 제공하기 위한 것입니다. 양식의 특정 사용자 그룹에 대한 자세한 목록은 [그룹 및 권한](forms-groups-privileges-tasks.md).

## 적응형 양식 만들기 {#strong-create-an-adaptive-form-strong}

적응형 양식을 만들려면 다음 단계를 따르십시오.

1. 액세스 [!DNL Experience Manager Forms] 작성자 인스턴스. 클라우드 인스턴스 또는 로컬 개발 인스턴스일 수 있습니다.

1. Experience Manager 로그인 페이지에서 자격 증명을 입력합니다.

   로그인하고 왼쪽 위 모서리에서 을(를) 탭합니다 **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Forms]** > **[!UICONTROL Forms 및 문서]**.

1. 탭 **[!UICONTROL 만들기]** 을(를) 선택합니다. **[!UICONTROL 적응형 양식]**. 템플릿을 선택하고 탭합니다 **[!UICONTROL 다음]**.
1. 다음 옵션 **[!UICONTROL 속성 추가]** 이 나타납니다. 다음 속성 필드에 값을 지정합니다. 제목 및 이름 필드는 필수입니다.

   * **[!UICONTROL 제목:]** 양식의 표시 이름을 지정합니다. 제목은 [!DNL Experience Manager Forms] 사용자 인터페이스.
   * **[!UICONTROL 이름:]** 양식의 이름을 지정합니다. 지정된 이름의 노드가 저장소에 생성됩니다. 제목을 입력을 시작하면 이름 필드의 값이 자동으로 생성됩니다. 제안된 값을 변경할 수 있습니다. 이름 필드에는 영숫자, 하이픈 및 밑줄만 포함할 수 있습니다. 잘못된 입력은 모두 하이픈으로 대체됩니다.
   * **[!UICONTROL 설명:]** 양식에 대한 자세한 정보를 지정합니다.
   * **[!UICONTROL 태그:]** 적응형 양식을 고유하게 식별할 태그를 지정합니다. 태그는 양식을 검색하는 데 도움이 됩니다. 태그를 만들려면 **[!UICONTROL 태그]** 상자.

1. 다음 양식 모델 중 하나를 기반으로 적응형 양식을 만들 수 있습니다.

   * [양식 데이터 모델](#fdm)

   <!--* [XFA form template](#create-an-adaptive-form-based-on-an-xfa-form-template)-->
   * [XML 또는 JSON 스키마](#create-an-adaptive-form-based-on-xml-or-json-schema)
   * 없음 또는 양식 모델 없음

   다음 위치에서 이러한 매개 변수를 구성할 수 있습니다. **[!UICONTROL 양식 모델]** 탭에서 다음을 수행합니다. **[!UICONTROL 속성 추가]** 페이지. 기본적으로 선택한 양식 모델은 다음과 같습니다 **[!UICONTROL 없음]**.

1. 탭 **[!UICONTROL 만들기]**. 적응형 양식이 만들어지고 편집할 양식을 여는 대화 상자가 나타납니다.

1. 탭 **[!UICONTROL 열기]** 새 탭에서 새로 만든 양식을 열려면 다음을 수행하십시오. 편집하기 위해 양식이 열리고 템플릿에서 사용할 수 있는 컨텐츠가 표시됩니다. 또한 필요에 따라 새로 만든 양식을 사용자 지정하는 사이드바가 표시됩니다.

   적응형 양식 유형에 따라 연결된 <!--XFA form template, -->XML 스키마 또는 JSON 스키마는 **[!UICONTROL 데이터 모델 개체]** 의 탭 **[!UICONTROL 컨텐츠 브라우저]** 을 클릭합니다. 이러한 요소를 드래그하여 놓아 적응형 양식을 작성할 수도 있습니다.

## 양식 데이터 모델을 기반으로 적응형 양식 만들기 {#fdm}

[데이터 통합](data-integration.md) 여러 데이터 소스를 통합하고 해당 엔티티와 서비스를 함께 가져와서 양식 데이터 모델을 만들 수 있습니다. JSON 스키마의 확장입니다. 양식 데이터 모델을 사용하여 적응형 양식을 만들 수 있습니다. 양식 데이터 모델에 구성된 엔티티 또는 데이터 모델 개체는 양식 작성을 위한 데이터 모델 개체로 사용할 수 있습니다. 각 데이터 소스에 바인딩되고 양식을 미리 채우고 제출된 데이터를 각 데이터 소스에 다시 쓰는 데 사용됩니다. 적응형 양식 규칙을 사용하여 양식 데이터 모델에 구성된 서비스를 호출할 수도 있습니다.

적응형 양식을 만들기 위해 양식 데이터 모델을 사용하려면 다음을 수행하십시오.

1. 속성 추가 화면의 양식 모델 탭에서 을 선택합니다 **[!UICONTROL 양식 데이터 모델]** 에서 **[!UICONTROL 선택 위치]** 드롭다운 목록.

   ![적응형 양식 만들기](assets/create-af-1-1.png)

1. 탭하여 확장 **[!UICONTROL 양식 데이터 모델 선택]**. 사용 가능한 모든 양식 데이터 모델이 나열됩니다.데이터 모델에서 을 선택합니다.

>[!NOTE]
>
>적응형 양식에 대한 양식 데이터 모델을 변경할 수도 있습니다. 자세한 단계는 [적응형 양식의 양식 모델 속성 편집](#edit-form-model).

## XML 또는 JSON 스키마를 기반으로 적응형 양식 만들기 {#create-an-adaptive-form-based-on-xml-or-json-schema}

XML 및 JSON 스키마는 조직의 백엔드 시스템에서 데이터를 생성하거나 사용하는 구조를 나타냅니다. 스키마를 적응형 양식에 연결하고 해당 요소를 사용하여 적응형 양식에 동적 컨텐츠를 추가할 수 있습니다. 스키마의 요소는 적응형 Forms을 작성하는 컨텐츠 브라우저의 데이터 모델 개체 탭에서 사용할 수 있습니다. 스키마 요소를 드래그하여 놓아 양식을 작성할 수 있습니다.

적응형 Forms 작성을 위한 XML 또는 JSON 스키마를 디자인하는 방법을 이해하려면 다음 문서를 참조하십시오.

* [XML 스키마를 사용하여 적응형 Forms 만들기](adaptive-form-xml-schema-form-model.md)
* [JSON 스키마를 사용하여 적응형 Forms 만들기](adaptive-form-json-schema-form-model.md)

적응형 양식의 양식 모델로 XML 또는 JSON 스키마를 사용하려면 다음을 수행하십시오.

1. 설정 **[!UICONTROL 속성 추가]** 적응형 양식 작성 페이지의 한 단계에서 **[!UICONTROL 양식 모델]** 탭.
1. 양식 모델 탭에서 을 선택합니다 **[!UICONTROL 스키마]** 에서 **[!UICONTROL 선택 위치]** 드롭다운 필드.

1. 탭 **[!UICONTROL 스키마 선택]** 다음 중 하나를 수행합니다.

   * **[!UICONTROL 디스크에서 업로드]** - 이 옵션을 선택하고 스키마 정의 업로드 를 탭하여 파일 시스템에서 XML 스키마 또는 JSON 스키마를 찾아 업로드합니다. 업로드된 스키마 파일은 양식에 포함되어 있으며 다른 적응형 Forms에서 액세스할 수 없습니다.
   * **[!UICONTROL 저장소에서 검색]** - 리포지토리에서 사용할 수 있는 스키마 정의 파일 목록에서 선택하려면 이 옵션을 선택합니다. XML 또는 JSON 스키마 파일을 양식 모델로 선택합니다. 선택한 스키마는 참조로 양식에 연결되며 다른 적응형 Forms에서 사용할 수 있습니다.

      JSON 스키마 파일 이름이 다음으로 끝나야 합니다. **.schema.json**. 예: mySchema.schema.json
   ![XML 또는 JSON 스키마 선택](assets/upload-schema.png)
   **그림:** *XML 또는 JSON 스키마 선택*

1. (XML 스키마에만 해당) XML 스키마를 선택하거나 업로드한 후 적응형 양식에 매핑할 선택한 XSD 파일의 루트 요소를 지정합니다.

   ![XSD 루트 요소 선택](assets/xsd-root-element.png)
   **그림:** *XSD 루트 요소 선택*

>[!NOTE]
>
>적응형 양식의 스키마를 변경할 수도 있습니다. 자세한 단계는 [적응형 양식의 양식 모델 속성 편집](#edit-form-model).

## 적응형 양식의 양식 모델 속성 편집 {#edit-form-model}

적응형 Forms은 양식 모델(양식 모델의 경우 없음 옵션 사용)이나 양식 모델(예: <!-- form template, --> XML 스키마, JSON 스키마 또는 양식 데이터 모델. 적응형 양식에 대한 양식 모델을 없음에서 다른 양식 모델로 변경할 수 있습니다. 양식 모델을 기반으로 하는 적응형 양식의 경우 다른 양식을 선택할 수 있습니다 <!-- form template,--> 동일한 양식 모델을 위한 XML 스키마, JSON 스키마 또는 양식 데이터 모델 . 그러나 한 양식 모델에서 다른 양식 모델로 변경할 수는 없습니다.

1. 적응형 양식을 선택하고 **속성** 아이콘.
1. 를 엽니다. **[!UICONTROL 양식 모델]** 탭하고 다음 중 하나를 수행합니다.

   * 적응형 양식이 양식 모델이 없는 경우 다른 양식 모델을 선택하고 그에 따라 을 선택할 수 있습니다 <!-- a form template, --> XML 또는 JSON 스키마 또는 양식 데이터 모델.
   * 적응형 양식이 양식 모델을 기반으로 하는 경우 다른 양식을 선택할 수 있습니다 <!-- form template, --> XML 또는 JSON 스키마 또는 동일한 양식 모델의 양식 데이터 모델 .

1. 탭 **[!UICONTROL 저장]** 속성을 저장합니다.
