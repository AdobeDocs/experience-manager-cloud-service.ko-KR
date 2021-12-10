---
title: 반복 가능한 섹션을 사용하여 양식 만들기
seo-title: Creating forms with repeatable sections
description: 반복 가능한 섹션은 양식에 동적으로 추가하거나 제거할 수 있는 패널입니다.
seo-description: Repeatable sections are panels that can be dynamically added or removed to a form.
uuid: c3fa2aa4-a6b4-458e-8534-138e075290b1
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: author
discoiquuid: 01724ca0-6901-45e7-b045-f44814ed574e
source-git-commit: 7163eb2551f5e644f6d42287a523a7dfc626c1c4
workflow-type: tm+mt
source-wordcount: '1117'
ht-degree: 0%

---


# 반복 가능한 섹션을 사용하여 양식 만들기 {#creating-forms-with-repeatable-sections}

반복 가능한 섹션은 동적으로 양식에 추가하거나 제거할 수 있는 패널입니다.

예를 들어 Job에 지원하는 동안 Job 검색자는 회사 이름, 역할, 프로젝트 및 기타 정보와 같은 이전 고용 상세내역을 제공합니다. 모든 고용주의 정보는 서로 다르지만 비슷한 모습을 보이는 섹션이 필요합니다. 이러한 시나리오에서 고용 양식은 고용주 섹션을 제공하며 이러한 섹션을 동적으로 추가할 수 있는 옵션도 제공합니다. 동적으로 추가된 이러한 섹션을 반복 가능한 섹션이라고 합니다.

다음 방법 중 하나를 사용하여 반복 가능한 패널을 만들 수 있습니다.

## 스크립트를 통해 인스턴스 관리자 사용  {#using-instance-manager-via-scripts-nbsp}

1. 편집 모드에서 패널을 선택한 다음 ![cmppr](assets/cmppr.png). 사이드바의 속성에서 **[!UICONTROL 패널 반복 가능]**. 에 대한 값을 지정합니다. **[!UICONTROL 최대]** 및 **[!UICONTROL 최소]** 필드.

   최대 필드는 페이지에 패널을 표시할 수 있는 최대 횟수를 지정합니다. 최대 개수 필드에 -1을 지정하여 패널을 무한 횟수만큼 표시할 수 있습니다.

   최소 필드는 양식이 양식에 표시되는 최소 횟수를 지정합니다. 최소 개수 필드를 0으로 설정하면 나중에 표현물이 완료된 후 스크립트를 통해 모든 인스턴스를 제거할 수 있습니다.

   >[!NOTE]
   >
   >반복되지 않는 패널을 만들려면 최대값 및 최소값 필드 값을 1로 설정합니다. 아코디언 레이아웃은 최대 개수 필드에서 -1을 지원하지 않습니다. 무한 값의 개념을 제공하기 위해 숫자를 지정할 수 있습니다.

1. 반복할 패널의 상위 패널에는 반복 가능한 패널의 인스턴스를 관리하기 위해 추가 및 삭제 단추가 포함되어야 합니다. 다음 단계를 수행하여 상위 단추에 단추를 삽입하고 단추에서 스크립트를 활성화합니다.

   1. 사이드바에서 단추 구성 요소를 패널의 부모로 드래그하여 놓습니다. 구성 요소를 선택하고 탭합니다 ![편집 규칙](assets/edit-rules.png). 버튼 규칙이 규칙 편집기에서 열립니다.
   1. 규칙 편집기 창에서 **만들기**.

      선택 **Visual Editor** 를 클릭합니다.

      1. 규칙 영역의 WHEN에서 state를 선택합니다. **를 클릭합니다.**.
      1. THEN에서:

         * 패널 추가 단추를 만들려면 **인스턴스 추가**&#x200B;를 클릭하고 ![토글 사이드 패널](assets/toggle-side-panel.png) 또는 **개체를 끌어 놓거나 여기를 선택하십시오.**
         * 삭제 패널 단추를 만들려면 **인스턴스 제거**&#x200B;를 클릭하고 ![토글 사이드 패널](assets/toggle-side-panel.png) 또는 **개체를 끌어 놓거나 여기를 선택하십시오.**

      선택 **코드 편집기** 를 클릭합니다. 클릭 **규칙 편집** 및 는 코드 영역에서 다음을 수행합니다.

      * 패널 추가 단추를 만들려면 `this.panel.instanceManager.addInstance()`
      * 삭제 패널 단추를 만들려면 `this.panel.instanceManager.removeInstance(this.panel.instanceIndex)`

      클릭 **완료**.

      >[!NOTE]
      >
      >필드가 반복 가능한 패널에 속하는 경우 스크립트에서 해당 이름을 사용하여 직접 액세스할 수 없습니다. 필드에 액세스하려면 를 사용하여 필드가 속한 반복 가능한 인스턴스를 지정합니다. `instances` 의 API `InstanceManager`. 를 사용할 구문 `instances` 의 API `InstanceManager` is:
      >
      >
      >`<panelName>.instanceManager.instances[<instanceNumber>].<fieldname>`
      >
      >
      >예를 들어, 텍스트 상자가 있는 반복 가능한 패널을 사용하여 적응형 양식을 만듭니다. 반복 가능한 텍스트 상자 세 개로 양식을 미리 채우면 아래의 xml이 필요합니다.
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
      >자세한 내용은 다음을 참조하십시오. 클래스: InstanceManager#instances in [AEM Forms Java API 참조](https://adobe.com/go/learn_aemforms_documentation_63).

      >[!NOTE]
      >
      >패널의 모든 인스턴스가 적응형 양식에서 제거되면 제거된 패널의 인스턴스를 추가하려면 _panelName 구문을 사용하여 패널의 인스턴스 관리자를 캡처하고 인스턴스 관리자의 addInstance API를 사용하여 삭제된 인스턴스를 추가합니다. 예를 들어 _panelName.addInstance() 제거된 패널의 인스턴스가 추가됩니다.



## 상위 패널에 대해 아코디언 레이아웃 사용   {#using-the-accordion-layout-for-the-parent-panel-nbsp}

패널에는 다양한 레이아웃 옵션이 있습니다. 아코디언 디자인용 레이아웃 옵션은 기본적으로 반복 가능한 패널을 지원합니다. 아코디언 디자인 옵션을 위한 레이아웃으로 반복 가능한 패널에 대해 다음 단계를 수행합니다.

1. 반복할 패널의 상위 패널에서 ![cmppr](assets/cmppr.png). 사이드바에서 속성을 볼 수 있습니다. 에서 **레이아웃** 드롭다운에서 을 선택합니다. **아코디언**.
1. 반복할 패널에서 ![cmppr](assets/cmppr.png). 사이드바에서 패널 속성을 볼 수 있습니다. 를 활성화합니다 **패널 반복 가능** 탭하고 **최대** 및 **최소** 필드.

   이제 더하기(+) 및 삭제( ![delete-panel](assets/delete-panel.png)) 단추를 클릭하여 패널을 추가하고 제거합니다.

## 양식 서식 파일에서 반복 하위 양식 사용(XDP/XSD) {#using-repeating-subforms-from-form-template-xdp-xsd}

반복 가능한 하위 양식은 적응형 Forms의 반복 가능한 패널과 유사합니다. in [!DNL AEM Forms] 디자이너에서 다음 단계를 수행하여 반복 하위 폼을 만듭니다.

1. 계층 팔레트에서 반복할 하위 양식의 상위 하위 폼을 선택합니다.
1. 개체 팔레트에서 하위 양식 탭을 클릭하고 콘텐츠 목록에서 흐름됨 을 선택합니다.
1. 반복할 하위 양식을 선택합니다.
1. 개체 팔레트에서 하위 양식 탭을 클릭하고 콘텐츠 목록에서 위치하거나 흐르기를 선택합니다.
1. 바인딩 탭을 클릭하고 각 데이터 항목에 대해 반복 하위 폼을 선택합니다.
1. 최소 반복 횟수를 지정하려면 최소 카운트를 선택하고 관련 상자에 숫자를 입력합니다. 이 옵션이 0으로 설정되어 있고 데이터 병합 시 하위 양식의 개체에 대해 데이터를 제공하지 않으면 폼을 렌더링할 때 하위 양식이 삽입되지 않습니다.
1. 최대 하위 양식 반복 횟수를 지정하려면 [최대]를 선택하고 연결된 상자에 숫자를 입력합니다. 최대 상자에 값을 지정하지 않으면 하위 양식 반복 수가 무제한이 됩니다.
1. 데이터 수량과 관계없이 하위 양식 반복 횟수를 설정하려면 초기 계산 을 선택하고 관련 상자에 숫자를 입력합니다. 이 옵션을 선택하고 사용할 수 있는 데이터가 없거나 지정한 초기 계산 값보다 적은 데이터 항목이 존재하는 경우, 하위 양식의 빈 인스턴스가 여전히 양식에 배치됩니다.
1. 부모 하위 폼에 반복 가능한 하위 양식의 인스턴스를 삭제하기 위한 단추와 인스턴스를 추가하는 단추를 두 개 추가합니다. 자세한 단계는 [작업 빌드](https://help.adobe.com/en_US/AEMForms/6.1/DesignerHelp/WS107c29ade9134a2c74572b5612a87ca2b56-8000.2.html#WS107c29ade9134a2c-1f74d86012a87d4fe55-8000.2).
1. 이제 양식 템플릿을 적응형 양식에 연결합니다. 자세한 단계는 [템플릿을 기반으로 적응형 양식 만들기](creating-adaptive-form.md#create-an-adaptive-form-based-on-a-template).
1. 9단계에서 만든 단추를 사용하여 하위 양식을 추가하고 제거합니다.

첨부된 .zip 파일에는 샘플 반복 가능한 하위 양식이 포함되어 있습니다.

[파일 가져오기](assets/samplerepeatablesubform.zip)

## XSD(XML 스키마)의 반복 설정 사용 {#using-repeat-settings-of-an-xml-schema-xsd-br}

XML 스키마와 복잡한 형식 요소의 minOccours 및 maxOccurs 속성에서 반복 가능한 패널을 만들 수 있습니다. XML 스키마에 대한 자세한 내용은 [XML 스키마를 양식 모델로 사용하여 적응형 Forms 만들기](adaptive-form-xml-schema-form-model.md).

다음 코드에서 `SampleType`패널에서는 minOccourse 및 maxOccurs 속성을 사용합니다.

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

>[!NOTE]
>
>아코디언 레이아웃의 경우 적응형 양식 단추 구성 요소를 사용하여 인스턴스를 추가하고 제거합니다.
