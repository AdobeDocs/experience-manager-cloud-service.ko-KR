---
title: 적응형 양식을 위한 XML 스키마 디자인
description: 적응형 양식에서 XML 스키마를 양식 모델로 사용하는 방법을 알아봅니다. XML 스키마 샘플을 사용하여 자세히 분석하고, XML 스키마를 사용하여 필드에 특수 속성을 추가하고, 적응형 양식 구성 요소에 허용 가능한 값을 제한합니다.
feature: Adaptive Forms
role: User, Developer
level: Beginner, Intermediate
exl-id: 5b8ad9a8-77d4-4234-a4d7-c8964b975e96
source-git-commit: 7163eb2551f5e644f6d42287a523a7dfc626c1c4
workflow-type: tm+mt
source-wordcount: '965'
ht-degree: 6%

---

# 적응형 양식을 위한 XML 스키마 디자인 {#creating-adaptive-forms-using-xml-schema}

## 사전 요구 사항 {#prerequisites}

XML 스키마를 양식 모델로 사용하여 적응형 양식을 작성하려면 XML 스키마를 기본 이해해야 합니다. 또한 이 문서 전에 다음 내용을 읽는 것이 좋습니다.

* [적응형 양식 만들기](creating-adaptive-form.md)
* [XML 스키마](https://www.w3.org/TR/xmlschema-2/)

## XML 스키마를 양식 모델로 사용 {#using-an-xml-schema-as-form-model}

[!DNL Experience Manager Forms] 에서는 기존 XML 스키마를 양식 모델로 사용하여 적응형 양식 만들기를 지원합니다. 이 XML 스키마는 조직의 백엔드 시스템에서 데이터를 생성하거나 사용하는 구조를 나타냅니다.

XML 스키마를 사용하는 주요 기능은 다음과 같습니다.

* 적응형 양식의 작성 모드에서 컨텐츠 파인더 탭에 XSD의 구조가 트리로 표시됩니다. XSD 계층 구조에서 요소를 적응형 양식에 드래그하여 추가할 수 있습니다.
* 연관된 스키마와 호환되는 XML을 사용하여 양식을 미리 채울 수 있습니다.
* 제출 시 사용자가 입력한 데이터는 관련 스키마에 맞는 XML로 제출됩니다.

XML 스키마는 간단하고 복잡한 요소 유형으로 구성됩니다. 요소에는 요소에 규칙을 추가하는 특성이 있습니다. 이러한 요소와 속성을 적응형 양식으로 드래그하면 해당 적응형 양식 구성 요소에 자동으로 매핑됩니다.

적응형 양식 구성 요소가 있는 XML 요소의 매핑은 다음과 같습니다.

<table>
 <tbody>
  <tr>
   <th><strong>XML 요소 또는 특성 </strong></th>
   <th><strong>적응형 양식 구성 요소</strong></th>
  </tr>
  <tr>
   <td><code>xs:string</code></td>
   <td>텍스트 상자</td>
  </tr>
  <tr>
   <td><code>xs:boolean</code></td>
   <td>확인란</td>
  </tr>
  <tr>
   <td>
    <ul>
     <li><code>xs:unsignedInt</code></li>
     <li><code>xs:xs:int</code></li>
     <li><code class="code">xs:decimal
        </code></li>
     <li>모든 유형의 숫자 값</li>
    </ul> </td>
   <td>숫자 상자</td>
  </tr>
  <tr>
   <td><code>xs:date</code></td>
   <td>날짜 선택</td>
  </tr>
  <tr>
   <td><code class="code">xs:enumeration
      </code></td>
   <td>드롭다운</td>
  </tr>
  <tr>
   <td>모든 복합 유형 요소</td>
   <td>패널</td>
  </tr>
 </tbody>
</table>

## 샘플 XML 스키마 {#sample-xml-schema}

다음은 XML 스키마의 예입니다.

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
                <xs:element name="assignmentStartBirth" type="xs:date"/>
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
>XML 스키마에 루트 요소가 하나만 있는지 확인합니다. 루트 요소가 두 개 이상 있는 XML 스키마가 지원되지 않습니다.

## XML 스키마를 사용하여 필드에 특수 속성 추가 {#adding-special-properties-to-fields-using-xml-schema}

XML 스키마 요소에 다음 속성을 추가하여 연결된 적응형 양식의 필드에 특수 속성을 추가할 수 있습니다.

<table>
 <tbody>
  <tr>
   <th><strong>스키마 속성</strong></th>
   <th><strong>적응형 양식에서 사용</strong></th>
   <th><strong>지원 대상 </strong></th>
  </tr>
  <tr>
   <td><code>use=required </code></td>
   <td>필수 필드를 표시합니다<br /> </td>
   <td>특성</td>
  </tr>
  <tr>
   <td><code>default="default value"</code></td>
   <td>기본값 추가</td>
   <td>요소 및 속성</td>
  </tr>
  <tr>
   <td><code>minOccurs="3"</code></td>
   <td><p>최소 발생 횟수를 지정합니다.</p> <p>(반복 가능한 하위 양식의 경우(복잡한 유형))</p> </td>
   <td>요소(복합 유형)</td>
  </tr>
  <tr>
   <td><code class="code">maxOccurs="10"
      </code></td>
   <td><p>최대 발생 횟수를 지정합니다.</p> <p>(반복 가능한 하위 양식의 경우(복잡한 유형))</p> </td>
   <td>요소(복합 유형)</td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>스키마 요소를 적응형 양식으로 드래그하면 다음과 같이 기본 캡션이 생성됩니다.
>
>* 요소 이름의 첫 번째 문자를 대문자로 바꿉니다
>* 카멜 케이스 경계에 공백을 삽입합니다.
>
>예를 들어 `userFirstName` 스키마 요소, 적응형 양식에 생성된 캡션은 `User First Name`.

## 적응형 양식 구성 요소에 사용할 수 있는 값 제한 {#limit-acceptable-values-for-an-adaptive-form-component}

XML 스키마 요소에 다음 제한 사항을 추가하여 적응형 양식 구성 요소에 허용 가능한 값을 제한할 수 있습니다.

<table>
 <tbody>
  <tr>
   <td><p><strong> 스키마 속성</strong></p> </td>
   <td><p><strong>데이터 형식</strong></p> </td>
   <td><p><strong>설명</strong></p> </td>
   <td><p><strong>구성 요소</strong></p> </td>
  </tr>
  <tr>
   <td><p><code>totalDigits</code></p> </td>
   <td><p>문자열</p> </td>
   <td><p>구성 요소에서 허용되는 최대 자릿수를 지정합니다. 지정한 자릿수는 0보다 커야 합니다.</p> </td>
   <td>
    <ul>
     <li>숫자 상자</li>
     <li>숫자 스텝퍼</li>
    </ul> </td>
  </tr>
  <tr>
   <td><p><code>maximum</code></p> </td>
   <td><p>문자열</p> </td>
   <td><p>숫자 값 및 날짜에 대한 상한을 지정합니다. 기본적으로 최대값이 포함됩니다.</p> </td>
   <td>
    <ul>
     <li>숫자 상자</li>
     <li>숫자 스텝퍼<br /> </li>
     <li>날짜 선택</li>
    </ul> </td>
  </tr>
  <tr>
   <td><p><code>minimum</code></p> </td>
   <td><p>문자열</p> </td>
   <td><p>숫자 값 및 날짜에 대해 하한 값을 지정합니다. 기본적으로 최소값이 포함됩니다.</p> </td>
   <td>
    <ul>
     <li>숫자 상자</li>
     <li>숫자 스텝퍼</li>
     <li>날짜 선택</li>
    </ul> </td>
  </tr>
  <tr>
   <td><p><code>exclusiveMaximum</code></p> </td>
   <td><p>부울</p> </td>
   <td><p>true일 경우 양식의 구성 요소에 지정된 숫자 값 또는 날짜는 최대 속성에 지정된 숫자 값 또는 날짜보다 작아야 합니다.</p> <p>false인 경우 양식의 구성 요소에 지정된 숫자 값 또는 날짜가 최대 속성에 대해 지정된 숫자 값 또는 날짜보다 작거나 같아야 합니다.</p> </td>
   <td>
    <ul>
     <li>숫자 상자</li>
     <li>숫자 스텝퍼</li>
     <li>날짜 선택</li>
    </ul> </td>
  </tr>
  <tr>
   <td><p><code>exclusiveMinimum</code></p> </td>
   <td><p>부울</p> </td>
   <td><p>true일 경우 양식의 구성 요소에 지정된 숫자 값 또는 날짜는 최소 속성에 지정된 숫자 값 또는 날짜보다 커야 합니다.</p> <p>false인 경우 양식의 구성 요소에 지정된 숫자 값 또는 날짜가 최소 속성에 지정된 숫자 값 또는 날짜보다 크거나 같아야 합니다.</p> </td>
   <td>
    <ul>
     <li>숫자 상자</li>
     <li>숫자 스텝퍼</li>
     <li>날짜 선택</li>
    </ul> </td>
  </tr>
  <tr>
   <td><p><code>minLength</code></p> </td>
   <td><p>문자열</p> </td>
   <td><p>구성 요소에 허용되는 최소 문자 수를 지정합니다. 최소 길이는 0보다 크거나 같아야 합니다.</p> </td>
   <td>
    <ul>
     <li>텍스트 상자</li>
    </ul> </td>
  </tr>
  <tr>
   <td><p><code>maxLength</code></p> </td>
   <td><p>문자열</p> </td>
   <td><p>구성 요소에서 허용되는 최대 문자 수를 지정합니다. 최대 길이는 0보다 커야 합니다.</p> </td>
   <td>
    <ul>
     <li>텍스트 상자</li>
    </ul> </td>
  </tr>
  <tr>
   <td><p><code>length</code></p> </td>
   <td><p>문자열</p> </td>
   <td><p>구성 요소에서 허용되는 정확한 문자 수를 지정합니다. 길이는 0보다 크거나 같아야 합니다.</p> </td>
   <td>
    <ul>
     <li>텍스트 상자</li>
    </ul> </td>
  </tr>
  <tr>
   <td><p><code>fractionDigits</code></p> </td>
   <td><p>문자열</p> </td>
   <td><p>구성 요소에서 허용되는 최대 소수 자릿수를 지정합니다. fractionDigits는 0보다 크거나 같아야 합니다.</p> </td>
   <td>
    <ul>
     <li> 데이터 유형이 부동 또는 십진수인 숫자 상자</li>
    </ul> </td>
  </tr>
  <tr>
   <td><p><code>pattern</code></p> </td>
   <td><p>문자열</p> </td>
   <td><p>문자의 시퀀스를 지정합니다. 구성 요소는 문자가 지정된 패턴을 준수하는 경우 문자를 허용합니다.</p> <p>패턴 속성은 해당 적응형 양식 구성 요소의 유효성 검사 패턴에 매핑됩니다.</p> </td>
   <td>
    <ul>
     <li>XSD 스키마에 매핑되는 모든 응용 Forms 구성 요소 </li>
    </ul> </td>
  </tr>
 </tbody>
</table>

## 자주 묻는 질문 {#frequently-asked-questions}

**컨텐츠 파인더에는 구조가 매우 복잡합니다. 특정 요소를 찾으려면 어떻게 해야 합니까?**

다음 두 가지 옵션이 있습니다.

* 트리 구조를 스크롤합니다.
* 검색 상자를 사용하여 요소를 찾습니다

**bindRef란 무엇입니까?**

A `bindRef` 적응형 양식 구성 요소와 스키마 요소 또는 속성 간의 연결입니다. 그것은 명령한다 `XPath` 여기서 이 구성 요소 또는 필드에서 캡처된 값을 출력 XML에서 사용할 수 있습니다. A `bindRef`미리 채워진(미리 채워진) XML에서 필드 값을 미리 채울 때도 사용됩니다.

**반복 가능한 하위 양식(minOccourse 또는 maxOccurts 값이 1보다 큼)에 대해 하위 양식의 개별 요소(복잡한 형식에서 생성된 구조)를 드래그할 수 없는 이유는 무엇입니까?**

반복 가능한 하위 양식에서는 Complete 하위 폼을 사용해야 합니다. 선택적 필드만 원하는 경우 전체 구조를 사용하고 원하지 않는 필드를 삭제합니다.
