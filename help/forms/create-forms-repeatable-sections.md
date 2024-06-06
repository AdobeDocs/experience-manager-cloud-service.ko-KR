---
title: 적응형 양식 핵심 구성 요소에서 반복 가능한 패널을 만드는 방법
description: 적응형 양식에서 반복 가능한 섹션 또는 필드를 만드는 방법에 대해 알아봅니다.
role: Architect, Developer, Admin, User
feature: Adaptive Forms, Core Components
exl-id: 02521bf3-83c1-40a0-8fe6-23af240727e9
source-git-commit: d3c5adf0b5b2155308e0bf9f4459682f11b67780
workflow-type: tm+mt
source-wordcount: '1258'
ht-degree: 8%

---

# 반복 가능한 섹션이 포함된 양식 만들기(핵심 구성 요소) {#repeat-panel}


| 버전 | 문서 링크 |
| -------- | ---------------------------- |
| AEM 6.5 | [여기 클릭](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-basic-authoring/creating-forms-repeatable-sections.html?lang=en) |
| AEM as a Cloud Service | 이 문서 |

반복 가능 섹션은 동일한 데이터의 여러 인스턴스에 대한 정보를 수집하기 위해 중복되거나 여러 번 반복될 수 있는 양식의 일부를 나타냅니다.

예를 들어 개인 경력에 대한 정보를 수집하는 데 사용되는 양식을 고려해 보십시오. 이전 작업의 세부 정보를 캡처하는 반복 가능한 섹션이 있을 수 있습니다. 반복 가능한 섹션은 일반적으로 회사 이름, 직책, 고용일, 직무 등과 같은 필드를 포함합니다. 사용자는 반복 가능한 섹션의 여러 인스턴스를 추가하여 각 직무에 대한 정보를 입력할 수 있습니다.

![반복성](/help/forms/assets/repeatable-adaptive-form-example.gif)

이 문서가 작성되면 다음 방법을 파악할 수 있습니다.

* 적응형 양식에 반복 가능한 섹션 만들기
* 적응형 양식 구성 요소에 대한 최소 또는 최대 반복 횟수 설정
* 규칙 편집기를 사용하여 반복 가능한 섹션에 대한 추가 또는 삭제 작업을 구성합니다.

다음을 사용할 수 있습니다. [패널](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/panel-container.html), [어코디언](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/accordion.html), [가로 탭](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/horizontal-tabs.html), [세로 탭](https://experienceleague.adobe.com/en/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/vertical-tabs)  또는 [마법사](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/wizard.html) 적응형 양식의 섹션을 반복 가능하게 만들 구성 요소. 이러한 구성 요소에 하위 구성 요소를 추가하여 양식에 반복 가능한 섹션을 만들 수 있습니다.


이 문서의 예제는 [패널](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/panel-container.html) 구성 요소. 동일한 단계를 수행하여 다음을 만들 수 있습니다 [패널](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/panel-container.html), [어코디언](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/accordion.html), [가로 탭](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/horizontal-tabs.html), [세로 탭](https://experienceleague.adobe.com/en/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/vertical-tabs) 또는 [마법사](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/wizard.html) 구성 요소가 반복 가능합니다.

## 양식에서 반복 가능한 섹션 추가 또는 삭제 {#add-or-delete-repeatable-section-in-panel-container}

양식에서 패널을 반복하거나 반복 가능한 패널을 제거하려면 양식 작성자가 버튼 구성 요소를 사용하여 패널의 인스턴스를 추가하거나 제거합니다. 양식에서 반복 가능한 섹션(패널)을 추가하거나 삭제하려면 다음을 수행합니다.

* [패널 컨테이너를 반복 가능하도록 설정](#make-panel-container-repeatable)
* [반복 가능한 섹션 추가](#add-repeatable-section-using-instance-manager-via-scripts)
* [반복 가능한 섹션 삭제](#delete-repeatable-section-using-instance-manager-via-scripts)

### 패널 컨테이너를 반복할 수 있도록 설정 {#make-panel-container-repeatable}

![접근성 탭](/help/forms/assets/repeat-panel.png)

패널이 반복 가능하도록 하려면 다음 단계를 수행하십시오.
1. 패널 컨테이너를 선택하고 을(를) 선택합니다 ![cmppr](/help/forms/assets/cmppr.png).
1. 다음을 클릭합니다. **반복 패널** 토글을 다음으로 전환 **패널이 반복 가능하도록 설정**.
1. 설정 **최소 반복** 반복 가능한 최소 섹션에 필요한 경우 다음을 설정할 수 있습니다 **최소 반복** 패널을 복원하지 않거나 반복된 패널을 제거하려면 0으로 설정합니다. 기본적으로 최소 반복 값은 0입니다.
1. 설정 **최대 반복** 필요한 횟수만큼 패널을 반복하려면 기본적으로 값이 무한대입니다.

   >[!NOTE]
   >
   > 
   > * 최소 반복은 -ve 값일 수 없습니다.
   > * 반복할 수 없는 패널을 만들려면 최대 및 최소 필드 값을 1로 설정하십시오.

### 인스턴스 관리자를 사용하여 반복 가능한 섹션 추가(스크립트를 통해) {#add-repeatable-section-using-instance-manager-via-scripts}

반복할 패널의 상위 항목에는 패널의 반복 인스턴스를 관리하기 위한 추가 버튼이 포함되어 있어야 합니다. 상위에 단추를 삽입하고 단추에 스크립트를 활성화하려면 다음 단계를 수행하십시오.

1. 추가 **버튼 구성 요소** (으)로 변경되었습니다. 아래 예제 비디오에서 레이블 이름이 인 버튼 구성 요소 **추가** 및 필드 이름 **패널 추가**&#x200B;가 사용됩니다. 구성 요소를 선택하고 을 선택합니다. ![규칙 편집](/help/forms/assets/edit-rules.png). 버튼 구성 요소의 규칙이 규칙 편집기에 열립니다.
1. 규칙 편집기 창에서 **만들기**.

   선택 **비주얼 편집기** 양식 개체 및 함수 행에서

   1. 규칙 영역의 WHEN에서 state를 선택합니다 **클릭됨**.
   1. THEN에서 **인스턴스 추가**&#x200B;을 클릭하고 다음을 사용하여 패널을 드래그 앤 드롭합니다 ![토글 사이드 패널](/help/forms/assets/toggle-side-panel.png) 또는 다음을 사용하여 선택 **개체를 놓거나 여기를 선택하십시오.**

   선택 **코드 편집기** 양식 개체 및 함수 행에서 클릭 **규칙 편집** 코드 영역에서 다음을 수행합니다.

   * 패널 추가 단추를 만들려면 다음을 지정합니다 `this.panel.instanceManager.addInstance()`

   **완료**&#x200B;를 클릭합니다.

>[!VIDEO](https://video.tv.adobe.com/v/3421052/adaptive-forms-repeatable-sections-repeat-sections/?quality=12&learn=on)


### 인스턴스 관리자를 사용하여 반복 가능한 섹션 삭제(스크립트를 통해) {#delete-repeatable-section-using-instance-manager-via-scripts}

패널의 상위에는 반복 가능한 패널의 인스턴스를 삭제하려면 삭제 단추가 있어야 합니다. 상위에 단추를 삽입하고 단추에 스크립트를 활성화하여 반복 가능한 패널을 삭제하려면 다음 단계를 수행하십시오.

1. 추가 **버튼 구성 요소** 패널의 상위, 아래 비디오에서 레이블 이름이 인 버튼 구성 요소 **삭제** 및 필드 이름 **DeletePanel** 를 사용합니다. 구성 요소를 선택하고 을 선택합니다. ![규칙 편집](/help/forms/assets/edit-rules.png). 버튼 구성 요소의 규칙이 규칙 편집기에 열립니다.
1. 규칙 편집기 창에서 **만들기**.

   선택 **비주얼 편집기** 양식 개체 및 함수 행에서

   1. 규칙 영역에서 WHEN **DeletePanel**, 상태 선택 **클릭됨**.
   1. THEN에서 **인스턴스 제거**&#x200B;을 클릭하고 다음을 사용하여 패널을 드래그 앤 드롭합니다 ![토글 사이드 패널](/help/forms/assets/toggle-side-panel.png) 또는 다음을 사용하여 선택 **개체를 놓거나 여기를 선택하십시오.**

   선택 **코드 편집기** 양식 개체 및 함수 행에서 클릭 **규칙 편집** 코드 영역에서 다음을 수행합니다.

   * 패널 삭제 단추를 만들려면 다음을 지정합니다 `this.panel.instanceManager.removeInstance(this.panel.instanceIndex)`

   **완료**&#x200B;를 클릭합니다.
>[!VIDEO](https://video.tv.adobe.com/v/3421620/adaptive-forms-repeatable-sections)

>[!NOTE]
>
>필드가 반복 가능 패널에 속해 있으면 스크립트에서 해당 이름을 사용하여 직접 액세스할 수 없습니다. 필드에 액세스하려면 다음을 사용하여 필드가 속한 반복 가능 인스턴스를 지정합니다. `instances` 의 API `InstanceManager`. 사용할 구문 `instances` 의 API `InstanceManager` 은(는)
>
>
>`<panelName>.instanceManager.instances[<instanceNumber>].<fieldname>`
>
>
>예를 들어 텍스트 상자가 있는 반복 가능 패널이 있는 적응형 양식을 만들 수 있습니다. 반복 가능한 텍스트 상자 3개로 양식을 미리 채우려면 아래 xml이 필요합니다.
>
>
>`<panel1><textbox1>AA1</panel1></textbox1>`
>
>
>`<panel1><textbox1>AA2</panel1></textbox1>`
>
>
>`<panel1><textbox1>AA3</panel1></textbox1>`
>
>
>AA1 데이터를 읽으려면 다음을 지정합니다.
>
>
>`Panel1.instanceManager.instances[0].textbox.value`
>
>
>AA2 데이터를 읽으려면 다음을 지정합니다.
>
>
>`Panel1.instanceManager.instances[1].textbox.value`
>
>
>

<!-- 
>For more information, see: Class: InstanceManager#instances in [AEM Forms Java API reference](https://adobe.com/go/learn_aemforms_documentation_63).      
-->

>[!NOTE]
>
> 적응형 양식에서 패널의 모든 인스턴스가 제거되면 제거된 패널의 인스턴스를 추가하려면 _panelName 구문을 사용하여 패널의 인스턴스 관리자를 캡처하고 인스턴스 관리자의 addInstance API를 사용하여 삭제된 인스턴스를 추가합니다. 예: _panelName.addInstance(). 제거된 패널의 인스턴스가 추가됩니다.

<!--
![panel-repeatability-video](/help/adaptive-forms/assets/panel-repeatability-video.mp4)
-->

<!--

## Using the accordion layout for the parent panel &nbsp; {#using-the-accordion-layout-for-the-parent-panel-nbsp}

A panel has various layouts options. The Layout for accordian design option has out of the box support for repeatable panels. Perform the following steps to repeatable panel with Layout for accordian design option:

1. On the parent of panel to be repeated, select ![cmppr](assets/cmppr.png). You can see the properties in the sidebar. In the **Layout** drop-down, select **Accordion**.
1. On a panel, which is to be repeated, select ![cmppr](assets/cmppr.png). You can see the panel properties in the sidebar. Enable the **Make Panel Repeatable** tab, and specify value for the **Maximum** and **Minimum** fields.

   Now, you can use the plus (+) and delete ( ![delete-panel](assets/delete-panel.png)) buttons to add and remove the panels.

-->

## 양식 템플릿에서 반복되는 하위 양식 사용(XDP/XSD) {#using-repeating-subforms-from-form-template-xdp-xsd}

반복 가능한 하위 양식은 적응형 Forms의 반복 가능한 패널과 유사합니다. AEM Forms Designer에서 다음 단계를 수행하여 반복되는 하위 양식을 만듭니다.

1. 계층 팔레트에서 반복할 하위 양식의 상위 하위 양식을 선택합니다.
1. 개체 팔레트에서 하위 양식 탭을 클릭하고 컨텐츠 목록에서 흐름을 선택합니다.
1. 반복할 하위 양식을 선택합니다.
1. 개체 팔레트에서 하위 양식 탭을 클릭하고 컨텐츠 목록에서 위치함 또는 흐름을 선택합니다.
1. 바인딩 탭을 클릭하고 각 데이터 항목에 대해 하위 양식 반복을 선택합니다.
1. 최소 반복 횟수를 지정하려면 최소 횟수(Min Count)를 선택하고 연관된 상자에 숫자를 입력합니다. 이 옵션을 0으로 설정하고 데이터 병합 시 하위 양식의 개체에 대해 데이터가 제공되지 않으면 양식을 렌더링할 때 하위 양식이 배치되지 않습니다.
1. 하위 양식 반복의 최대 횟수를 지정하려면 최대값을 선택하고 연관된 상자에 숫자를 입력합니다. [최대] 상자에 값을 지정하지 않으면 하위 양식 반복 횟수는 제한이 없습니다.
1. 데이터 수량에 관계없이 하위 양식 반복 횟수를 지정하려면 초기 수를 선택하고 관련 상자에 숫자를 입력합니다. 이 옵션을 선택하고 사용할 수 있는 데이터가 없거나 지정된 초기 개수 값보다 적은 데이터 항목이 있는 경우 하위 양식의 빈 인스턴스가 계속 양식에 배치됩니다.
1. 상위 하위 양식에 인스턴스 추가 단추와 반복 가능한 하위 양식의 인스턴스 삭제 단추 두 개를 추가합니다. 자세한 단계는 를 참조하십시오. [작업 빌드](https://help.adobe.com/en_US/AEMForms/6.1/DesignerHelp/WS107c29ade9134a2c74572b5612a87ca2b56-8000.2.html#WS107c29ade9134a2c-1f74d86012a87d4fe55-8000.2).
1. 이제 양식 템플릿을 적응형 양식에 연결합니다. 자세한 단계는 를 참조하십시오. [템플릿을 기반으로 적응형 양식 만들기](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-basic-authoring/creating-adaptive-form.html?lang=en#create-an-adaptive-form-based-on-an-xfa-form-template).
1. 9단계에서 만든 단추를 사용하여 하위 양식을 추가하거나 제거합니다.

첨부된 .zip 파일에는 반복 가능한 하위 양식 샘플이 포함되어 있습니다.

[파일 가져오기](/help/forms/assets/samplerepeatablesubform.zip)

## XSD(XML 스키마)의 반복 설정 사용 {#using-repeat-settings-of-an-xml-schema-xsd-br}

XML 스키마와 복합 유형 요소의 minOccours 및 maxOccurs 속성에서 반복 가능한 패널을 만들 수 있습니다. XML 스키마에 대한 자세한 내용은 [XML 스키마를 양식 모델로 사용하여 적응형 양식 만들기](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-advanced-authoring/adaptive-form-xml-schema-form-model.html).

다음 코드에서는 `SampleType`패널은 minOccours 및 maxOccurs 속성을 사용합니다.

```xml
<?xml version="1.0" encoding="utf-8" ?>
    <xs:schema targetNamespace="https://adobe.com/sample.xsd"
                    xmlns="https://adobe.com/sample.xsd"
                    xmlns:xs="https://www.w3.org/2001/XMLSchema"
                >

        <xs:element name="sample" type="SampleType"/>

        <xs:complexType name="SampleType">
            <xs:sequence>
                <xs:element name="leaderName" type="xs:string" default="Enter Name"/>
                <xs:element name="assignmentStartDate" type="xs:date"/>
                <xs:element name="gender" type="GenderEnum"/>
                <xs:element name="noOfProjectsAssigned" type="IntType"/>
                <xs:element name="assignmentDetails" type="AssignmentDetails"
                                            minOccurs="0" maxOccurs="10"/>
            </xs:sequence>
        </xs:complexType>

        <xs:complexType name="AssignmentDetails">
            <xs:attribute name="name" type="xs:string" use="required"/>
            <xs:attribute name="durationOfAssignment" type="xs:unsignedInt" use="required"/>
            <xs:attribute name="numberOfMentees" type="xs:unsignedInt" use="required"/>
             <xs:attribute name="descriptionOfAssignment" type="xs:string" use="required"/>
             <xs:attribute name="financeRelatedProject" type="xs:boolean"/>
       </xs:complexType>
  <xs:simpleType name="IntType">
            <xs:restriction base="xs:int">
            </xs:restriction>
        </xs:simpleType>
  <xs:simpleType name="GenderEnum">
            <xs:restriction base="xs:string">
                <xs:enumeration value="Female"/>
                <xs:enumeration value="Male"/>
            </xs:restriction>
        </xs:simpleType>
    </xs:schema>
```


## 추가 참조 {#see-also}

{{see-also}}

<!--

>[!MORELIKETHIS]
>
>* [Create an Adaptive Form](creating-adaptive-form-core-components.md)
>* [Create style or themes for your forms](using-themes-in-core-components.md)
>* [Add dynamic behavior to forms using the rule editor](rule-editor.md)
>* [Set layout of forms for different screen sizes and device types](/help/sites-cloud/authoring/features/console-layout.md)

-->