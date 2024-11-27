---
title: 스크리블 서명을 사용하여 양식에 전자 서명을 적용하려면 어떻게 해야 합니까?
description: 스크리블 서명을 사용하여 양식에 전자 서명을 적용하는 방법에 대해 알아봅니다.
uuid: ffeba886-9b24-4ed1-95c0-e19356ff2f23
products: SG_EXPERIENCEMANAGER/FORMS
topic-tags: author
feature: Adaptive Forms, Foundation Components
exl-id: dc89ecb1-2d9e-4d1d-b85b-af90c550e7d8
role: User, Developer
source-git-commit: ad28fd933a85c8b5ba1cdad4927f0a0a45ad478d
workflow-type: tm+mt
source-wordcount: '1318'
ht-degree: 54%

---

# 스크리블 서명을 사용하여 양식에 전자 서명{#apply-electronic-signatures-to-a-form-using-deprecated-scribble-signatures}

<span class="preview"> [새 적응형 양식 만들기](/help/forms/creating-adaptive-form-core-components.md) 또는 [AEM Sites 페이지에 적응형 양식 추가](/help/forms/create-or-add-an-adaptive-form-to-aem-sites-page.md) 작업을 할 때 현대적이고 확장 가능한 데이터 캡처 [핵심 구성 요소](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html)를 사용하는 것이 좋습니다. 이러한 구성 요소는 적응형 양식 만들기 작업이 대폭 개선되어 우수한 사용자 경험을 보장할 수 있게 되었음을 나타냅니다. 이 문서에서는 기초 구성 요소를 사용하여 적응형 양식을 작성하는 이전 접근법에 대해 설명합니다. </span>

| 버전 | 문서 링크 |
| -------- | ---------------------------- |
| AEM 6.5 | [여기 클릭](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-basic-authoring/signing-forms-using-scribble.html) |
| AEM as a Cloud Service | 이 문서 |


**스크리블 서명** 구성 요소를 사용하여 적응형 양식에 스크리블 서명을 그릴 수 있습니다. <!-- The Signature step component displays a PDF version of the Adaptive Form. You require a Document of Record option enabled or form template based Adaptive Forms to use the Signature step component. -->

![스크리블 서명 대화 상자](assets/scribble-signature.png)

## 서명 창에서 사용할 수 있는 다양한 옵션

* **A:** 캔버스에 서명을 그리려면 **페인트 브러시** 아이콘을 클릭하세요.
* **B:** 캔버스에서 서명을 지우려면 **지우기** 아이콘을 클릭하십시오.
* **C:** **지리적 위치** 아이콘을 클릭하여 서명과 함께 지리적 위치를 추가하십시오.
* **D:** 캔버스에 이름을 입력하려면 **키보드** 아이콘을 클릭하십시오.

스크리블 서명 창에서 완료 ![aem_forms_save](assets/aem_forms_save.png) 아이콘을 선택하면 서명을 편집할 수 없습니다. 서명을 편집하려면 현재 서명을 무시하고 위의 [페인트 브러쉬/키보드] 옵션을 사용하여 다시 서명해야 합니다.

**구성** ![구성 아이콘](assets/configure.png) 아이콘을 선택하여 스크리블 서명 캔버스의 종횡비를 설정할 수 있습니다.
* 스크리블 서명 캔버스의 종횡비가 1보다 작은 경우 지리적 위치 정보가 스크리블 서명 캔버스의 맨 아래에 추가됩니다.


* 스크리블 서명 캔버스의 종횡비가 1보다 큰 경우 지리적 위치 정보가 스크리블 서명 캔버스의 오른쪽에 추가됩니다.


![스크리블 서명-하단](assets/scribble-signature-aspectratio.PNG)



>[!NOTE]
>
>서명은 항상 PNG 형식으로 저장됩니다.
>

## 스크리블 서명을 사용하도록 적응형 양식 구성 {#configure-an-adaptive-form-to-use-scribble-signature}

1. 편집 모드에서 적응형 양식을 엽니다.
1. 구성 요소 브라우저에서 **스크리블 서명** 구성 요소를 적응형 양식으로 드래그 앤 드롭하십시오.
1. **구성** ![구성](assets/configure.png) 아이콘을 선택합니다. 속성 브라우저를 열고 스크리블 서명 구성 요소의 속성을 표시합니다. 다음 섹션에서 설명한 대로 [스크리블 서명의 속성을 구성](#properties-of-scribble-signature-component)합니다.

   ![스크리블 서명](/help/forms/assets/scribblesig.png)

1. 변경 사항을 저장하려면 완료 ![aem_forms_save](assets/aem_forms_save.png) 아이콘을 선택하십시오. 서명이 구성되었습니다.

## 스크리블 서명 구성 요소의 속성 구성

구성 대화 상자를 통해 방문자에 대한 스크리블 서명 구성 요소를 손쉽게 맞춤화할 수 있습니다.

### 기본 탭

![기본 탭](/help/forms/assets/scribblesig-basic.png)

* **이름** - 양식과 규칙 편집기 모두에서 고유한 이름으로 양식 구성 요소를 쉽게 식별할 수 있습니다. 단, 이름에는 공백이나 특수 문자가 포함되어서는 안 됩니다.

* **제목** - 제목을 사용하면 양식에서 구성 요소를 쉽게 식별할 수 있으며, 기본적으로 제목은 구성 요소 상단에 나타납니다. 제목을 추가하지 않으면 제목 텍스트 대신 구성 요소의 이름이 표시됩니다.

* **제목에 대해 서식 있는 텍스트 허용** - 이 기능을 사용하면 사용자가 굵게, 기울임꼴, 밑줄 친 텍스트, 다양한 글꼴, 글꼴 크기, 색상, 추가 옵션과 같은 기능을 통합해 일반 텍스트 제목의 서식을 지정하여 시각적 표현 및 사용자 정의를 향상할 수 있습니다. 더 큰 유연성과 창의적인 제어 기능으로 문서, 웹 사이트 또는 애플리케이션 내에서 제목을 돋보이게 할 수 있습니다.\
  **제목에 대해 서식 있는 텍스트 허용** 확인란을 선택하면 구성 요소 제목의 스타일을 지정할 수 있는 서식 지정 옵션이 표시됩니다. 사용 가능한 모든 서식 옵션에 액세스하려면 ![전체 화면 아이콘](/help/forms/assets/fullscreen-icon.png) 탭을 클릭하면 됩니다.

  ![서식 있는 텍스트 지원](/help/forms/assets/richtext-support-title.png)

* **제목 숨기기** - 구성 요소의 제목을 숨기려면 이 옵션을 선택합니다.
* **필수 필드** - 필드를 필수 필수로 설정하려면 옵션을 선택하십시오.
* **필수 필드 메시지** - **필수 필드 메시지**&#x200B;은(는) 사용자가 필수 필드를 입력하지 않고 양식을 제출하려고 할 때 표시되는 사용자 지정 가능한 메시지입니다.
* **데이터 모델 바인드 참조** - 바인드 참조는 외부 데이터 원본에 저장되어 양식에서 사용되는 데이터 요소에 대한 참조입니다. 바인드 참조를 사용하면 데이터를 양식 필드에 동적으로 바인딩하여 양식이 데이터 소스의 최신 데이터를 표시하도록 할 수 있습니다. 예를 들어 바인드 참조를 사용하여 양식에 입력된 고객의 ID를 기반으로 고객의 이름과 주소를 양식에 표시할 수 있습니다. 바인드 참조를 사용하여 양식에 입력된 데이터로 데이터 소스를 업데이트할 수도 있습니다. 이러한 방식으로 AEM Forms를 사용하면 외부 데이터 소스와 상호 작용하는 양식을 만들어 데이터 수집 및 관리를 위한 원활한 사용자 경험을 제공할 수 있습니다.
* **개체 숨기기** - 양식에서 구성 요소를 숨기려면 옵션을 선택합니다. 구성 요소는 다른 용도로(예: 규칙 편집기에서 계산에 사용) 계속 액세스할 수 있습니다. 구성 요소 숨기기는 사용자가 보거나 직접 변경할 필요가 없는 정보를 저장해야 할 때 유용합니다.
* **개체 비활성화** - 구성 요소를 비활성화하는 옵션을 선택합니다. 비활성화된 구성 요소는 활성 상태가 아니므로 최종 사용자가 편집할 수 없습니다. 사용자는 필드 값을 볼 수 있지만 수정할 수는 없습니다. 구성 요소는 다른 용도로(예: 규칙 편집기에서 계산에 사용) 계속 액세스할 수 있습니다.
* **종횡비** - 스크리블 서명 구성 요소의 종횡비는 너비와 높이 간의 비례 관계를 정의합니다.
* **필드 레이아웃** - **필드 레이아웃** 옵션은 레이블(캡션) 및 오류 메시지를 포함한 양식 요소를 구성 요소를 기준으로 배치하는 방법을 결정합니다. **위젯의 맨 위로 캡션 및 오류**&#x200B;은 필드의 캡션(레이블) 및 오류 메시지를 구성 요소 위에 배치합니다. **적응형 양식 구성에서 상속**&#x200B;은(는) 적응형 양식 구성에 지정된 기본 필드 레이아웃 설정을 사용합니다.
* **CSS 클래스** - **CSS 클래스**&#x200B;을(를) 사용하면 스타일시트에 정의된 하나 이상의 CSS 클래스를 할당하여 구성 요소에 사용자 지정 스타일을 적용할 수 있습니다. 적응형 양식 전체에서 일관된 스타일 및 레이아웃 사용자 지정이 가능합니다.

### 도움말 컨텐츠

![도움말 콘텐츠 탭](/help/forms/assets/scribblesig-help.png)

* **간단한 설명** - 간단한 설명은 특정 양식 필드의 용도에 대한 추가 정보 또는 설명을 제공하는 간단한 텍스트 설명입니다. 사용자가 필드에 입력해야 하는 데이터 유형을 이해하는 데 도움이 되며 입력된 정보가 유효하고 원하는 기준을 충족하는지 확인하는 데 도움이 되는 지침 또는 예시를 제공할 수 있습니다. 기본적으로 간단한 설명은 숨겨진 상태로 유지됩니다. **간단한 설명 항상 표시** 옵션을 활성화하여 구성 요소 아래에 표시할 수 있습니다.

* **간단한 설명 항상 표시** - 이 옵션을 활성화하여 구성 요소 아래에 간단한 설명을 표시할 수 있습니다.

* **긴 설명** - 양식 필드를 올바르게 작성하는 데 도움이 되도록 사용자에게 제공되는 추가 정보 또는 지침을 참조합니다. 구성 요소 옆에 있는 도움말 아이콘(i)을 클릭하면 표시됩니다. 양식 필드의 레이블이나 자리 표시자 텍스트보다 더 자세한 정보를 제공하며 사용자가 필드의 요구 사항이나 제약 조건을 이해하는 데 도움이 되도록 설계되었습니다. 또한 양식을 보다 쉽고 정확하게 작성할 수 있도록 제안이나 예시를 제공할 수도 있습니다.

### 접근성 탭 {#accessibility}

![접근성 탭](/help/forms/assets/scribblesig-acc.png)

**접근성** 탭에는 구성 요소에 대한 [ARIA 접근성](https://www.w3.org/WAI/standards-guidelines/aria/) 레이블에 값이 설정되어 있습니다. 다양한 옵션을 통해 화면 판독기용 텍스트를 사용할 수 있습니다.

* **화면 Reader 우선 순위** - 화면 Reader 우선 순위는 화면 판독기와 같은 보조 기술에 의해 읽히기 위해 특별히 고안된 시각 장애가 있는 사용자가 사용하는 추가 텍스트를 나타냅니다. 이 텍스트는 양식 필드의 용도에 대한 오디오 설명을 제공하며, 여기에는 필드의 제목, 설명, 이름 및 관련 메시지(사용자 정의 텍스트)에 대한 정보가 포함될 수 있습니다. 화면 판독기 텍스트는 시각 장애가 있는 사용자를 포함한 모든 사용자가 양식에 액세스할 수 있도록 돕고 양식 필드 및 해당 요구 사항을 완전히 이해할 수 있도록 합니다.

   * **사용자 정의 텍스트**: ARIA 접근성 레이블에 사용자 정의 텍스트를 사용하려면 이 옵션을 선택합니다. 이 옵션을 선택하면 사용자 정의 텍스트 대화 상자가 표시됩니다. 사용자 정의 텍스트 대화 상자에서 관련 정보를 추가할 수 있습니다.
   * **간단한 설명**: ARIA 액세스 가능성 레이블에 대한 설명을 사용하려면 이 옵션을 선택하십시오.
   * **제목**: ARIA 접근성 레이블에 제목을 사용하려면 이 옵션을 선택합니다.
   * **이름**: ARIA 접근성 레이블에 이름을 사용하려면 이 옵션을 선택합니다.
   * **없음**: ARIA 접근성 레이블에 아무 것도 추가하지 않으려면 이 옵션을 선택합니다.

<!--

 * **Element Name**: Specify name of the component.

    * **Title:** Specify unique title of the component.
    * **Template message:** Specify the message to be displayed while the signature PDF is being loaded. Adobe Sign services take some time to prepare and load signature PDF.
    * **Signing Service:** Select the **Scribble Signature** option.

    * **CSS Class**: Specify CSS class of the client library, if any. Adobe recommends using [themes](themes.md) and [in-line styles](inline-style-adaptive-forms.md) instead of CSS Class.
## Sign an Adaptive Form using Scribble Signature {#sign-an-adaptive-form-using-scribble-signature}

1. After you fill an Adaptive Form and reach the Signature Step page, the signature screen is displayed.

   ![Signature screen for EchoSign page](assets/esignscribblesign.jpg)

1. Click **[!UICONTROL Sign]**. The scribble sign dialog appears. Sign the form and click the Done ![aem_forms_save](assets/aem_forms_save.png) icon to save the signature.

   ![Scribble sign dialog](assets/scribblewidget.png)

1. Click complete to finish the signing process.

   ![Complete the signing process](assets/scribblecomplete.jpg)

The signatures are added to the form and the form control moves to the next panel. -->

## 추가 참조 {#see-also}

{{see-also}}