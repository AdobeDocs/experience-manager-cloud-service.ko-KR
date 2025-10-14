---
title: HTML5 양식에서 사용자 정의 표시 만들기
description: 모바일 Forms에 사용자 정의 위젯을 연결할 수 있습니다. 기존 jQuery 위젯을 확장하거나 사용자 정의 위젯을 개발할 수 있습니다.
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: hTML5_forms
docset: aem65
feature: HTML5 Forms,Mobile Forms
exl-id: 76bd1e2d-9e65-452c-8cef-123d28886a62
solution: Experience Manager, Experience Manager Forms
role: Admin, User, Developer
source-git-commit: 22aeedaaf4171ad295199a989e659b6bf5ce9834
workflow-type: tm+mt
source-wordcount: '662'
ht-degree: 0%

---

# HTML5 양식에서 사용자 정의 표시 만들기{#create-custom-appearances-in-html-forms}

<span class="preview"> HTML5 Forms 기능은 조기 액세스 프로그램의 일부로 제공됩니다. 액세스 권한을 요청하려면 공식(회사) 이메일 ID에서 aem-forms-ea@adobe.com으로 이메일을 보내십시오.
</span>

모바일 Forms에 사용자 정의 위젯을 연결할 수 있습니다. 기존 jQuery 위젯을 확장하거나 모양새 프레임워크를 사용하여 사용자 정의 위젯을 개발할 수 있습니다. XFA 엔진은 다양한 위젯을 사용합니다. 자세한 내용은 [적응형 및 HTML5 양식에 대한 모양 프레임워크](/help/forms/custom-widgets.md)를 참조하십시오.

![기본 및 사용자 지정 위젯의 예](assets/custom-widgets.jpg)

기본 및 사용자 정의 위젯의 예

## HTML5 양식과 사용자 정의 위젯 통합 {#integrating-custom-widgets-with-html-forms}

### 프로필 만들기  {#create-a-profile-nbsp}

프로필을 만들거나 기존 프로필을 선택하여 사용자 지정 위젯을 추가할 수 있습니다. 프로필 만들기에 대한 자세한 내용은 [사용자 지정 프로필 만들기](/help/forms/custom-profile.md)를 참조하십시오.

### 위젯 만들기 {#create-a-widget}

HTML5 forms는 새 위젯을 만들기 위해 확장할 수 있는 위젯 프레임워크의 구현을 제공합니다. 구현은 새 위젯을 작성하기 위해 확장할 수 있는 jQuery 위젯 *abstractWidget*&#x200B;입니다. 새로운 위젯은 아래에 언급된 기능들을 확장/재정의해야만 기능할 수 있다.

<table>
 <tbody>
  <tr>
   <td>함수/클래스</td>
   <td>설명</td>
  </tr>
  <tr>
   <td>렌더링</td>
   <td>렌더링 함수는 위젯의 기본 HTML 요소에 대한 jQuery 개체를 반환합니다. 기본 HTML 요소는 집중 가능한 유형이어야 합니다. 예: &lt;a&gt;, &lt;input&gt; 및 &lt;li&gt;. 반환된 요소가 $userControl로 사용됩니다. $userControl이 위의 제약 조건을 지정하면 AbstractWidget 클래스의 함수가 예상대로 작동하고 그렇지 않으면 일부 일반 API(포커스, 클릭)를 변경해야 합니다. </td>
  </tr>
  <tr>
   <td>getEventMap</td>
   <td>HTML 이벤트를 XFA 이벤트로 변환하는 맵을 반환합니다. <br /> {<br /> blur: XFA_EXIT_EVENT,<br /> }<br /> 이 예제는 흐림이 HTML 이벤트이고 XFA_EXIT_EVENT가 해당 XFA 이벤트임을 보여 줍니다. </td>
  </tr>
  <tr>
   <td>getOptionsMap</td>
   <td>옵션 변경 시 수행할 작업을 자세히 제공하는 맵을 반환합니다. 키는 위젯에 제공되는 옵션이며 값은 해당 옵션의 변경이 감지될 때마다 호출되는 기능입니다. 위젯은 모든 일반 옵션(값 및 displayValue 제외)에 대한 핸들러를 제공합니다</td>
  </tr>
  <tr>
   <td>getCommitValue</td>
   <td>위젯 프레임워크는 위젯 값이 XFAModel에 저장될 때마다(예: textField의 종료 이벤트에서) 함수를 로드합니다. 구현은 위젯에 저장된 값을 반환해야 합니다. 핸들러에 옵션에 대한 새 값이 제공됩니다.</td>
  </tr>
  <tr>
   <td>showValue</td>
   <td>기본적으로 XFA on enter 이벤트에서 필드의 rawValue가 표시됩니다. 이 함수는 사용자에게 rawValue를 표시하기 위해 호출됩니다. </td>
  </tr>
  <tr>
   <td>showDisplayValue</td>
   <td>기본적으로 종료 시 XFA에서 필드의 formattedValue가 표시됩니다. 이 함수는 사용자에게 formattedValue를 표시하기 위해 호출됩니다. </td>
  </tr>
 </tbody>
</table>

나만의 위젯을 만들려면 위에서 만든 프로필에 재정의된 함수와 새로 추가된 함수가 포함된 JavaScript 파일의 참조를 포함합니다. 예를 들어 *sliderNumericFieldWidget*&#x200B;은 숫자 필드에 대한 위젯입니다. 헤더 섹션의 프로필에서 위젯을 사용하려면 다음 줄을 포함하십시오.

```javascript
window.formBridge.registerConfig("widgetConfig" , widgetConfigObject);
```

### XFA 스크립팅 엔진을 사용하여 사용자 정의 위젯 등록  {#register-custom-widget-with-xfa-scripting-engine-nbsp}

사용자 지정 위젯 코드가 준비되면 `registerConfig`Form Bridge[용 &#x200B;](https://experienceleague.adobe.com/ko/docs/experience-manager-65/content/forms/developer-reference/form-bridge-apis)API를 사용하여 스크립팅 엔진에 위젯을 등록합니다. widgetConfigObject를 입력으로 사용합니다.

```javascript
window.formBridge.registerConfig("widgetConfig",
        {
        ".<field-identifier>":"<name-of-the-widget>"
        }
    );
```

#### widgetConfigObject {#widgetconfigobject}

위젯 구성은 키가 필드를 식별하고 값이 해당 필드와 함께 사용할 위젯을 나타내는 JSON 개체(키 값 쌍의 컬렉션)로 제공됩니다. 샘플 구성은 다음과 같습니다.

```
*{*

*"identifier1" : "customwidgetname",
"identifier2" : "customwidgetname2",
..
}*
```

여기서 &quot;identifier&quot;는 특정 필드, 특정 유형의 필드 집합 또는 모든 필드를 나타내는 jQuery CSS 선택기입니다. 다음은 여러 경우에 사용되는 식별자의 값을 나열합니다.

| 식별자 유형 | 식별자 | 설명 |
|---|---|---|
| 필드 이름이 인 특정 필드 | 식별자:&quot;div.fieldname&quot; | &quot;fieldname&quot;이라는 이름의 모든 필드는 위젯을 사용하여 렌더링됩니다. |
| &#39;type&#39; 유형의 모든 필드(type이 NumericField, DateField 등임).: | 식별자: &quot;div.type&quot; | Timefield 및 DateTimeField의 경우 이 필드는 지원되지 않으므로 이 유형은 textfield입니다. |
| 모든 필드 | 식별자: &quot;div.field&quot; |  |
