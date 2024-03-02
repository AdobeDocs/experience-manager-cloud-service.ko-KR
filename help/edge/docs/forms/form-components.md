---
title: 양식 구성 요소 및 속성
description: 이 문서에서는 AEM Forms Edge Delivery Service에서 사용할 수 있는 양식 구성 요소 및 해당 속성에 대한 개요를 제공합니다.
feature: Edge Delivery Services
hide: true
hidefromtoc: true
source-git-commit: e8fbe3efae7368c940cc2ed99cc9a352bbafbc22
workflow-type: tm+mt
source-wordcount: '865'
ht-degree: 3%

---


# 양식 구성 요소

AEM Forms Edge Delivery Service를 통해 다양한 구성 요소를 사용하여 사용자 친화적인 대화형 양식을 만들 수 있습니다. 이러한 구성 요소는 다양한 유형의 데이터 수집에 적합하며 특정 요구 사항에 맞게 쉽게 사용자 지정할 수 있습니다.

적응형 양식 블록은 [균일 HTML 구조](/help/edge/docs/forms/style-theme-forms.md) 일관성을 유지하기 위해 모든 필드 유형 및 컨테이너(패널)에 사용됩니다. 이러한 일관된 구조를 통해 다음과 같은 작업을 쉽게 수행할 수 있습니다 [양식 스타일 지정](/help/edge/docs/forms/style-theme-forms.md).


## 사용 가능한 구성 요소

다음은 사용 가능한 구성 요소에 대한 개요입니다.

### 입력 필드

- 모든 유효한 HTML5 [입력 유형](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input#input_types) 및 [텍스트 영역](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/textarea). 예를 들어, button, checkbox, color, date, datetime-local, email, file, hidden, image, month, number, password, radio, range, reset, submit, tel, text, time, url 및 week가 있습니다.

### 선택 컨트롤

- [확인란 그룹](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input/checkbox): 여러 옵션을 선택합니다.
- [라디오 그룹](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input/radio): 그룹에서 단일 옵션을 선택합니다.
- [드롭다운 메뉴](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/select): 옵션 메뉴를 표시합니다. 예를 들어 드롭다운 상자입니다.

### 컨테이너

- 패널/컨테이너: 구성을 향상시키기 위해 관련 양식 요소를 함께 그룹화합니다. It is a combination of the [필드 세트](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/fieldset) 및 [범례](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/legend).


## 구성 요소 속성

각 양식 구성 요소에는 양식 구성 요소의 비헤이비어와 모양을 제어할 수 있는 다양한 속성이 포함되어 있습니다. 적응형 양식 블록 구성 요소에서 지원하는 속성은 다음과 같습니다.


| 속성 | 적용 가능한 구성 요소 | 세부 사항 |
|--------------|------------------------------|----------------------------------------------------------------------|
| 유형 | 모두 | 구성 요소의 유형을 지정합니다. 이 속성은 입력 필드의 동작 및 모양을 결정합니다. 예를 들어 텍스트 입력의 경우 유형은 &quot;text&quot;, 이메일 입력의 경우 &quot;email&quot;, 암호 입력의 경우 &quot;password&quot;일 수 있습니다. 적응형 양식 블록은 모든 유효한 HTML5를 지원합니다. <a href="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input#input_types">입력 유형</a>, <a href="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/textarea">텍스트 영역</a>, <a href="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/select">선택</a>, 및 <a href="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/fieldset">필드 세트</a> 형식: |
| 이름 | 모두 | 양식 제출을 위한 구성 요소를 식별합니다. 이름 속성은 양식 데이터가 서버에 제출될 때 사용자 입력을 특정 필드와 연결하는 데 사용됩니다. |
| 레이블 | 모두 | 사용자에게 컨텍스트 정보를 제공합니다. 레이블은 구성 요소 옆에 표시되는 텍스트로서, 사용자가 입력할 정보에 대한 지침을 제공합니다. |
| 값 | 텍스트, 암호, 이메일, 숫자, 범위, 날짜 및 변형(datetime-local, month, week, time), 확인란, 라디오, 숨김, 제출, 버튼 | 구성 요소의 초기 값을 지정합니다. 텍스트 입력, 텍스트 영역 및 요소 선택에서 표시되는 기본 텍스트 또는 옵션입니다. 라디오 및 확인란 구성 요소의 경우 선택할 때 제출한 값/데이터입니다. 값 속성은 선택 사항이지만 확인란 및 라디오 입력에 대해 필수로 간주해야 합니다. |
| 플레이스홀더 | 텍스트, 전화, 이메일, 암호, 날짜(및 월, 주, 시간, datetime-local과 같은 변형), 숫자, 범위 | 예상 입력에 대한 힌트를 제공합니다. 자리 표시자 속성은 입력 필드의 예상 값을 설명하는 간단한 힌트를 제공합니다. 사용자가 입력을 시작하면 사라집니다. |
| 설명 | 모두 | 구성 요소에 대한 추가 정보를 제공하고 도움말 텍스트 역할을 합니다. 설명 필드는 구성 요소를 작성하기 위한 목적 또는 지침에 대해 자세히 설명할 수 있습니다. 이는 사용자가 입력 필드의 컨텍스트를 이해하는 데 도움이 됩니다. |
| 보임 | 모두 | 초기 가시성을 제어합니다. visible 속성은 양식이 로드될 때 구성 요소를 처음에 표시할지 또는 숨길지 여부를 결정하는 부울 속성입니다. true로 설정하면 필드가 표시되고, 그렇지 않으면 숨겨집니다. |
| 필수 | 텍스트, 전화, 이메일, 암호, 날짜 및 변형(datetime-local, month, week, time), 숫자, 확인란, 라디오, 파일, 선택(드롭다운), 텍스트 영역 | 제출하기 전에 필드를 채워야 하는지 여부를 나타냅니다. 필수 속성은 양식을 제출하기 전에 사용자가 필드에 대한 입력을 제공해야 하는지 여부를 지정하는 데 사용되는 부울 속성입니다. |
| 최소 | 날짜(및 월, 주, 시간, datetime-local과 같은 변형), 숫자, 범위 | 허용된 최소 값을 지정합니다. min 속성은 사용자가 필드에 입력할 수 있는 최소값을 설정합니다. 예를 들어 숫자 입력의 경우 허용되는 가장 낮은 숫자를 정의합니다. |
| Max | 날짜(및 월, 주, 시간, datetime-local과 같은 변형), 숫자, 범위 | 최대 허용 값을 지정합니다. max 속성은 사용자가 필드에 입력할 수 있는 최대값을 설정합니다. 예를 들어 날짜 입력의 경우 허용되는 가장 높은 날짜를 정의합니다. |
| 수락 | 파일 | 허용되는 파일 유형을 정의합니다. accept 속성은 사용자가 파일 입력 필드에서 선택할 수 있는 파일 형식을 제한하는 쉼표로 구분된 고유한 파일 형식 지정자 목록입니다. |
| 복수 | 파일 | 여러 항목을 선택할 수 있습니다. 다중 속성은 파일 입력 필드에 사용되는 부울 속성입니다. true로 설정하면 사용자가 둘 이상의 파일을 선택할 수 있습니다. |
| 옵션 | 드롭다운 | 드롭다운 메뉴에 대한 선택 사항을 지정합니다. options 속성은 사용자에게 표시되는 선택 가능한 옵션을 정의하는 드롭다운 메뉴에 대한 선택 사항을 쉼표로 구분한 목록입니다. |
| 선택됨 | 확인란, 라디오 | 기본적으로 필드가 선택되어 있는지 여부를 결정합니다. checked 속성은 확인란 및 라디오 입력과 함께 사용되는 부울 속성입니다. true로 설정하면 양식이 로드될 때 필드가 기본적으로 선택됩니다. |
| 필드 세트 | 모두 | 필드를 그룹화하여 양식 내에서 시각적으로 구별되는 섹션을 만듭니다. 필드 집합 요소는 양식 내에서 관련 필드를 그룹화하고 시각적으로 분리하여 조직 및 사용자 경험을 개선합니다. </br> 필드 집합 내에서 필드 집합을 구성하려면 `fieldset` 속성을 지정하고 이름 속성을 지정합니다. 아래 예에서는 더 나은 구성을 위해 라디오 단추가 단일 필드 세트 내에 캡슐화되는 방식을 보여 줍니다. ![필드 집합 예](/help/edge/assets/fieldset-example.png) |



<!--

## Supported HTML 5 input types in Adaptive Form Block

The Adaptive Form Block supports a range of HTML 5 input types, and it also seamlessly renders forms created with AEM core components.
Here is the table which outlines how core components correspond to their HTML-5 input types in Edge Delivery:
<table>
 <tbody>
  <tr>
   <td><b>Core Components</b> </td>
   <td><b>HTML 5 input type</b> </td>
   <td><b>Details</b></td>
  </tr>
  <tr>
   <td><a href ="https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/form-container.html">Form Container</a></td>
   <td><a href ="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input#form">form </td>
   <td> Create a form to capture user inputs.
   </td>
  </tr>
  <tr>
   <td><a herf="https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/text-input.html">Text Input</a></td>
   <td><a href ="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input/text">text</a></td>
   <td> Defines a single-line text input field. </td>
  </tr>
  <tr>
   <td><a href = "https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/number-input.html">Number Input</a></td>
   <td><a href = "https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input/number">number</a></td>
   <td>Lets user  enter a number input. You can also add built-in validation to reject non-numerical inputs. Lets user  enter a number input. You can also add built-in validation to reject non-numerical inputs. Initially, the input field is displayed as a number input. If a user applies a display pattern, it changes to text to allow the author to apply number formatting, since HTML 5 lacks support for display patterns. However, when the user clicks it, it returns to typing numbers.</td>
  </tr>
  <tr>
   <td><a href ="https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/date-picker.html">Date Picker</a></td>
   <td><a href = "https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input/date">date </a></td>
   <td> Create an input field for entering a date. You have the option to input the date either through a text box, which validates the entry, or through a dedicated date picker interface. Initially, the native date input field is displayed. If a user applies a display pattern, it changes to text to allow the user to apply formatting, since HTML 5 lacks support for display patterns. However, when the user clicks it, it returns to typing a date.</td>
  </tr>
  <tr>
   <td><a href ="https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/file-attachment.html">File Attachment</a></td>
   <td><a href ="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input/file">file</a></td>
   <td> Allows user to choose one or more files from the device storage. It supports enhanced file input validations, such as accepted file types, file size restrictions, and minimum/maximum file selection limits. </td>
  </tr>
  <tr>
   <td><a href ="https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/drop-down.html"> Dropdown List</a></td>
   <td><a href ="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/select">select</a></td>
   <td> Allows users to select one or more options from a list of predefined options. The options can be of type String, Number, or Boolean.</td>
  </tr>
  <tr>
   <td><a href ="https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/checkbox-group.html">Checkbox Group</a></td>
   <td><a href ="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input/checkbox">multiple checkbox</a></td>
   <td> Allow users to select one or more options from a list. Multiple checkboxes are generated with identical names, each corresponding to an item in the enum. </td>
  </tr>
  <tr>
   <td><a href ="https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/radio-button.html">Radio Button Group</td>
   <td><a href ="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input/radio">multiple radio</a></td>
   <td> Allows a user to select one option from a group of related options. Multiple radio buttons are generated with identical names, each corresponding to an item in the enum.</td>
  </tr>
  <tr>
   <td><a href ="https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/button.html">Button</td>
   <td><a href ="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input/button">button</a></td>
   <td>A UI element that allows users to trigger an action when clicked. </td>
  </tr>
  <tr>
   <td><a href =""https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/panel-container.html">Panel</a></td>
   <td><a href ="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/fieldset">fieldset with legend</a></td>
   <td> Group sections within a form, where a nested *legend* element adds a caption for the form.</td>
  </tr>
   <tr>
   <td><a href ="https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/wizard.html">Wizard</a></td>
   <td><a href ="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/fieldset">fieldset</a></td>
   <td>Groups related sections within a form. It also controls the arrangement, supporting display options for positioning them at the top or at the left side. </td>
  </tr>
    <tr>
   <td><a href ="https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/text.html">Text</a></td>
   <td><a href ="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/p">p</a></td>
   <td>A p tag marks a paragraph. In visual content, paragraphs are chunks of text separated by blank lines or an indented first line</td>
  </tr>
     <tr>
   <td><a href ="https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/submit-button.html">Submit button</td>
   <td><a href ="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input/submit">submit</a></td>
   <td> A UI element that enables users to submit a form to the server upon clicking. If a user adds a submit rule to a button, it functions as the submit button. </td>
  </tr>
     <tr>
   <td><a href = "https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/reset-button.html">Reset button</a></td>
   <td><a href ="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input/reset">reset</a></td>
   <td>A UI element that resets a form upon clicking. If a user adds a reset rule to a button, it functions as the reset button. </td>
  </tr>
    <tr>
   <td><a href ="https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/email-input.html">Email Input</td>
   <td><a href ="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input/email">email</a></td>
   <td> Allows the user to enter and edit an email address. If the user adds the multiple attributes, a list of email addresses can be added or edited.</td>
  </tr>
   <tr>
   <td><a href ="https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/telephone-input.html">Telephone Input</a></td>
   <td><a href ="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input/tel">tel</a></td>
   <td>Allows user to enter and edit a telephone number.</td>
  </tr>
   <tr>
   <td><a href ="https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/header.html">Header</td>
   <td><a href = "https://developer.mozilla.org/en-US/docs/Web/HTML/Element/header"> header</a></td>
   <td>It includes introductory content, typically a group of introductory or navigational aids. It is supported outside Form container. </td>
  </tr>
  <tr>
   <td><a href ="https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/footer.html">Footer</td>
   <td><a href = "https://developer.mozilla.org/en-US/docs/Web/HTML/Element/footer">footer</a></td>
   <td> Contains information such as copyright data or links to related documents. It is supported outside Form container.</td>
  </tr>
  <tr>
   <td><a href = "https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/accordion.html">Accordion<a></td>
   <td><i>Not yet supported in Adaptive Form Block</i></td>
   <td> Allows user to create expandable and collapsible sections in a form. </td>
  </tr>
  <tr>
   <td><a href ="https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/horizontal-tabs.html">Horizontal tabs</a></td>
   <td><i>Not yet supported in Adaptive Form Block</i></td>
   <td>Organizes multiple sections of a form into separate tabs which are displayed horizontally.</td>
  </tr>
  <tr>
   <td><a href = "https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/image.html">Image</a></td>
   <td><i>Not yet supported in Adaptive Form Block</i></td>
   <td> Allows user to include images in a form.</td>
  </tr><tr>
   <td><a href ="https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/title.html">Title</a></td>
   <td><i>Not yet supported in Adaptive Form Block</i></td>
   <td> Refers to the text that appears at the top of the form. </td>
  </tr>
  <tr>
   <td><a href = "https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/submit-button.html">Switch</td>
   <td><i>Not yet supported in Adaptive Form Block</i></td>
   <td> A two-state toggle that allows user to select between two states such as enabling or disabling a feature, setting, or functionality.</td>
  </tr>
 </tbody>
</table>