---
title: 적응형 양식 필드를 미리 채우는 방법
description: 기존 데이터를 사용하여 적응형 양식의 필드를 미리 채우면 사용자가 소셜 프로필로 로그인하여 양식의 기본 정보를 미리 채울 수 있습니다.
topic-tags: develop
feature: Adaptive Forms, Foundation Components
exl-id: e2a87233-a0d5-48f0-b883-915fe56f105f
source-git-commit: 6821856bd9f1a87a66ba296b3e315c0a4e78cea8
workflow-type: tm+mt
source-wordcount: '2007'
ht-degree: 3%

---

# 적응형 양식 필드 미리 채우기{#prefill-adaptive-form-fields}

<span class="preview"> [새 적응형 양식 만들기](/help/forms/creating-adaptive-form-core-components.md) 또는 [AEM Sites 페이지에 적응형 양식 추가](/help/forms/create-or-add-an-adaptive-form-to-aem-sites-page.md) 작업을 할 때 현대적이고 확장 가능한 데이터 캡처 [핵심 구성 요소](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html)를 사용하는 것이 좋습니다. 이러한 구성 요소는 적응형 양식 만들기 작업이 대폭 개선되어 우수한 사용자 경험을 보장할 수 있게 되었음을 나타냅니다. 이 문서에서는 기초 구성 요소를 사용하여 적응형 양식을 작성하는 이전 접근법에 대해 설명합니다. </span>

| 버전 | 문서 링크 |
| -------- | ---------------------------- |
| AEM 6.5 | [여기 클릭](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-advanced-authoring/prepopulate-adaptive-form-fields.html) |
| AEM as a Cloud Service | 이 문서 |

## 소개 {#introduction}

기존 데이터를 사용하여 적응형 양식의 필드를 미리 채울 수 있습니다. 사용자가 양식을 열면 해당 필드의 값이 미리 채워집니다. 적응형 양식에서 데이터를 미리 채우려면 적응형 Forms의 미리 채우기 데이터 구조를 준수하는 형식으로 사용자 데이터를 미리 채우기 XML/JSON으로 사용할 수 있습니다.

## 미리 채우기 데이터 구조 {#the-prefill-structure}

적응형 양식에는 바인딩된 필드와 바인딩되지 않은 필드가 혼합되어 있을 수 있습니다. 바인딩된 필드는 콘텐츠 파인더 탭에서 드래그하고 비어 있지 않은 필드를 포함합니다 `bindRef` 필드 편집 대화 상자의 속성 값입니다. 바인딩되지 않은 필드는 Sidekick의 구성 요소 브라우저에서 직접 드래그되며 비어 있습니다. `bindRef` 값.

적응형 양식의 바인딩된 필드와 바인딩되지 않은 필드를 모두 미리 채울 수 있습니다. 미리 채우기 데이터에는 적응형 양식의 바인딩된 필드와 바인딩되지 않은 필드를 모두 미리 채우는 afBoundData 섹션과 afUnBoundData 섹션이 포함됩니다. 다음 `afBoundData` 섹션에는 바인딩된 필드 및 패널의 미리 채우기 데이터가 포함됩니다. 이 데이터는 연결된 양식 모델 스키마와 호환되어야 합니다.

- 를 사용하는 적응형 Forms용 [XFA 양식 템플릿](#xfa-based-af)에서는 XFA 템플릿의 데이터 스키마와 호환되는 미리 채우기 XML을 사용합니다.
- 를 사용하는 적응형 Forms [XML 스키마](#xml-schema-af)XML 스키마 구조를 따르는 미리 채우기 XML을 사용합니다.
- 를 사용하는 적응형 Forms [JSON 스키마](#json-schema-based-adaptive-forms), JSON 스키마와 호환되는 미리 채우기 JSON을 사용합니다.
- FDM 스키마를 사용하는 적응형 Forms의 경우, FDM 스키마와 호환되는 JSON 미리 채우기를 사용하십시오.
- 를 사용하는 적응형 Forms [양식 모델 없음](#adaptive-form-with-no-form-model), 바인딩된 데이터가 없습니다. 모든 필드는 바인딩되지 않은 필드이며 바인딩되지 않은 XML을 사용하여 미리 채워집니다.

### 샘플 미리 채우기 XML 구조 {#sample-prefill-xml-structure}

```xml
<?xml version="1.0" encoding="UTF-8"?>
<afData>
  <afBoundData>
     <employeeData>
        .
     </employeeData>
  </afBoundData>

  <afUnboundData>
    <data>
      <textbox>Hello World</textbox>
         .
         .
      <numericbox>12</numericbox>
         .
         .
    </data>
  </afUnboundData>
</afData>
```

### 샘플 미리 채우기 JSON 구조 {#sample-prefill-json-structure}

```javascript
{
   "afBoundData": {
      "employeeData": { }
   },
   "afUnboundData": {
      "data": {
         "textbox": "Hello World",
         "numericbox": "12"
      }
   }
}
```

동일한 bindref를 가진 바인딩된 필드 또는 이름이 같은 바인딩되지 않은 필드의 경우 XML 태그 또는 JSON 개체에 지정된 데이터가 모든 필드에 채워집니다. 예를 들어 양식의 두 필드는 이름에 매핑됩니다. `textbox` 를 추가합니다. 런타임 중에 첫 번째 텍스트 상자 필드에 &quot;A&quot;가 포함되어 있으면 두 번째 텍스트 상자에 자동으로 &quot;A&quot;가 채워집니다. 이 연결을 적응형 양식 필드의 라이브 연결이라고 합니다.

### XFA 양식 템플릿을 사용한 적응형 양식 {#xfa-based-af}

XFA 기반 적응형 Forms을 위한 사전 채우기 XML 및 제출된 XML의 구조는 다음과 같습니다.

- **XML 구조 미리 채우기**: XFA 기반 적응형 양식을 위한 미리 채우기 XML은 XFA 양식 템플릿의 데이터 스키마와 호환되어야 합니다. 바인딩되지 않은 필드를 미리 채우려면 미리 채우기 XML 구조를 `/afData/afBoundData` 태그에 가깝게 배치하십시오.

- **제출된 XML 구조**: 미리 채우기 XML을 사용하지 않는 경우 제출된 XML에 의 바인딩된 필드와 바인딩되지 않은 필드 모두에 대한 데이터가 포함됩니다. `afData` 래퍼 태그입니다. 미리 채우기 XML을 사용하는 경우 제출된 XML의 구조는 미리 채우기 XML과 동일합니다. 미리 채우기 XML이 `afData` 루트 태그입니다. 출력 XML도 형식이 같습니다. 미리 채우기 XML에 `afData/afBoundData`래퍼 및 대신 와 같은 스키마 루트 태그에서 직접 시작됩니다. `employeeData`로 시작하는 경우 제출된 XML도 `employeeData` 태그에 가깝게 배치하십시오.

Prefill-Submit-Data-ContentPackage.zip

[파일 가져오기](assets/prefill-submit-data-contentpackage.zip)
미리 채우기 데이터 및 제출된 데이터가 포함된 샘플

### XML 스키마 기반 적응형 Forms  {#xml-schema-af}

XML 스키마를 기반으로 하는 적응형 Forms을 위한 사전 채우기 XML 및 제출된 XML의 구조는 다음과 같습니다.

- **XML 구조 미리 채우기**: 미리 채우기 XML이 연결된 XML 스키마를 준수해야 합니다. 바인딩되지 않은 필드를 미리 채우려면 미리 채우기 XML 구조를 /afData/afBoundData 태그로 래핑합니다.
- **제출된 XML 구조**: 미리 채우기 XML을 사용하지 않으면 제출된 XML에 의 바인딩된 필드와 바인딩되지 않은 필드 모두에 대한 데이터가 포함됩니다. `afData` 래퍼 태그입니다. 미리 채우기 XML을 사용하는 경우 제출된 XML의 구조는 미리 채우기 XML과 동일합니다. 미리 채우기 XML이 `afData` 루트 태그입니다. 출력 XML의 형식은 동일합니다. 미리 채우기 XML에 `afData/afBoundData` 래퍼 및 대신 와 같은 스키마 루트 태그에서 직접 시작합니다. `employeeData`로 시작하는 경우 제출된 XML도 `employeeData` 태그에 가깝게 배치하십시오.

```xml
<?xml version="1.0" encoding="utf-8" ?>
<xs:schema targetNamespace="https://adobe.com/sample.xsd"
            xmlns="https://adobe.com/sample.xsd"
            xmlns:xs="https://www.w3.org/2001/XMLSchema">

    <xs:element name="sample" type="SampleType"/>

    <xs:complexType name="SampleType">
        <xs:sequence>
            <xs:element name="noOfProjectsAssigned" type="xs:string"/>
        </xs:sequence>
    </xs:complexType>
</xs:schema>
```

모델이 XML 스키마인 필드의 경우 데이터가 `afBoundData` 아래 샘플 XML에 표시된 대로 태그를 지정합니다. 하나 이상의 바인딩되지 않은 텍스트 필드로 적응형 양식을 미리 채우는 데 사용할 수 있습니다.

```xml
<?xml version="1.0" encoding="UTF-8"?><afData>
  <afUnboundData>
    <data>
      <textbox>Ignorance is bliss :) </textbox>
    </data>
  </afUnboundData>
  <afBoundData>
    <data>
      <noOfProjectsAssigned>twelve</noOfProjectsAssigned>
    </data>
  </afBoundData>
</afData>
```

>[!NOTE]
>
>바인딩된 패널(비어 있지 않은 패널)에서는 바인딩되지 않은 필드를 사용하지 않는 것이 좋습니다 `bindRef` Sidekick 또는 데이터 소스 탭에서 구성 요소를 끌어 옵니다. 이로 인해 바인딩되지 않은 필드의 데이터가 손실될 수 있습니다. 또한 필드 이름은 양식 전체에서 고유하며 특히 바인딩되지 않은 필드에 대해 고유한 것이 좋습니다.

#### afData 및 afBoundData 래퍼가 없는 예 {#an-example-without-afdata-and-afbounddata-wrapper}

```xml
<?xml version="1.0" encoding="UTF-8"?><config>
 <assignmentDetails descriptionOfAssignment="Some Science Project" durationOfAssignment="34" financeRelatedProject="1" name="Lisa" numberOfMentees="1"/>
 <assignmentDetails descriptionOfAssignment="Kidding, right?" durationOfAssignment="4" financeRelatedProject="1" name="House" numberOfMentees="3"/>
</config>
```

### JSON 스키마 기반 적응형 Forms {#json-schema-based-adaptive-forms}

JSON 스키마를 기반으로 하는 적응형 Forms의 경우, 사전 채우기 JSON 및 제출된 JSON의 구조가 아래에 설명되어 있습니다. 자세한 내용은 [JSON 스키마를 사용하여 적응형 Forms 만들기](adaptive-form-json-schema-form-model.md).

- **JSON 구조 미리 채우기**: 미리 채우기 JSON은 관련 JSON 스키마와 호환되어야 합니다. 선택적으로 언바운드 필드도 미리 채우려면 /afData/afBoundData 개체에 래핑할 수 있습니다.
- **제출된 JSON 구조**: 미리 채우기 JSON을 사용하지 않는 경우, 제출된 JSON에는 afData 래퍼 태그의 바인딩된 필드와 바인딩되지 않은 필드 모두에 대한 데이터가 포함됩니다. 미리 채우기 JSON을 사용하는 경우 제출된 JSON의 구조가 미리 채우기 JSON과 동일합니다. 미리 채우기 JSON이 afData 루트 개체로 시작하는 경우 출력 JSON의 형식은 동일합니다. 미리 채우기 JSON에 afData/afBoundData 래퍼가 없고 대신 사용자와 같은 스키마 루트 오브젝트에서 직접 시작하는 경우, 제출된 JSON도 사용자 오브젝트로 시작됩니다.

```json
{
  "id": "https://some.site.somewhere/entry-schema#",
  "$schema": "https://json-schema.org/draft-04/schema#",
  "type": "object",
  "properties": {
    "address": {
      "type": "object",
      "properties": {
        "name": {
          "type": "string"
        },
        "age": {
          "type": "integer"
        }
      }
    }
  }
}
```

JSON 스키마 모델을 사용하는 필드의 경우, 데이터는 아래 샘플 JSON에 표시된 대로 afBoundData 개체에 미리 채워집니다. 하나 이상의 바인딩되지 않은 텍스트 필드로 적응형 양식을 미리 채우는 데 사용할 수 있습니다. 다음은 가 포함된 데이터의 예입니다. `afData/afBoundData` 래퍼:

```json
{
  "afData": {
    "afUnboundData": {
      "data": { "textbox": "Ignorance is bliss :) " }
    },
    "afBoundData": {
      "data": { {
   "user": {
    "address": {
     "city": "Noida",
     "country": "India"
}}}}}}}
```

다음은 가 없는 예제입니다. `afData/afBoundData` 래퍼:

```json
{
  "user": {
    "address": {
      "city": "Noida",
      "country": "India"
    }
  }
}
```

>[!NOTE]
>
> 바인딩된 패널(Sidekick 또는 데이터 소스 탭에서 구성 요소를 드래그하여 만든 비어 있지 않은 bindRef가 있는 패널)에서 바인딩되지 않은 필드를 사용하는 것은 다음과 같습니다 **아님** 바인딩되지 않은 필드의 데이터가 손실될 수 있으므로 권장됩니다. 특히 바인딩되지 않은 필드의 경우 양식에서 고유한 필드 이름을 사용하는 것이 좋습니다.
>

### 양식 모델이 없는 적응형 양식 {#adaptive-form-with-no-form-model}

양식 모델이 없는 적응형 Forms의 경우 모든 필드의 데이터는 `<data>` 태그 / `<afUnboundData> tag`.

또한 다음 사항에 유의하십시오.

다양한 필드에 대해 제출된 사용자 데이터의 XML 태그는 필드의 이름을 사용하여 생성됩니다. 따라서 필드 이름은 고유해야 합니다.

```xml
<?xml version="1.0" encoding="UTF-8"?><afData>
  <afUnboundData>
    <data>
      <radiobutton>2</radiobutton>
      <repeatable_panel_no_form_model>
        <numericbox>12</numericbox>
      </repeatable_panel_no_form_model>
      <repeatable_panel_no_form_model>
        <numericbox>21</numericbox>
      </repeatable_panel_no_form_model>
      <checkbox>2</checkbox>
      <textbox>Nopes</textbox>
    </data>
  </afUnboundData>
  <afBoundData/>
</afData>
```

## 미리 채우기 서비스 구성 중 {#configuring-prefill-service-using-configuration-manager}

사용 `alloweddataFileLocations` 의 속성 **기본 미리 채우기 서비스 구성** 데이터 파일 위치 또는 데이터 파일 위치에 대한 정규 표현식(정규 표현식)을 설정합니다.

다음 JSON 파일에는 샘플이 표시됩니다.

```JSON
  {
  "alloweddataFileLocations": "`file:///C:/Users/public/Document/Prefill/.*`"
  }
```

구성의 값을 설정하려면 다음을 수행합니다. [AEM SDK를 사용하여 OSGi 구성 생성](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/deploying/configuring-osgi.html?lang=ko#generating-osgi-configurations-using-the-aem-sdk-quickstart) 및 [구성 배포](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/deploy-code.html?lang=ko#deployment-process) Cloud Service 인스턴스로 이동합니다.

>[!NOTE]
>
> - 기본적으로 모든 유형의 적응형 Forms(XSD, XDP, JSON, FDM 및 양식 모델 기반 없음)에 대해 crx 파일을 통해 미리 채우기가 허용됩니다. 미리 채우기는 JSON 및 XML 파일에서만 허용됩니다.
> - crx 프로토콜은 미리 채워진 데이터 보안을 처리하므로 기본적으로 허용됩니다. 일반 정규 표현식을 사용하는 다른 프로토콜을 통해 미리 채우면 취약성이 발생할 수 있습니다. 구성에서 데이터를 보호하기 위한 보안 URL 구성을 지정합니다.

## 반복 가능한 패널의 이상한 사례 {#the-curious-case-of-repeatable-panels}

일반적으로 바인딩된(양식 스키마) 필드와 바인딩되지 않은 필드는 동일한 적응형 양식에서 작성되지만, 바인딩이 반복될 수 있는 경우 다음과 같은 몇 가지 예외가 있습니다.

- XFA 양식 템플릿, XSD, JSON 스키마 또는 FDM 스키마를 사용하는 적응형 Forms에 대해 바인딩되지 않은 반복 가능한 패널이 지원되지 않습니다.
- 바인딩된 반복 가능한 패널에 바인딩되지 않은 필드를 사용하지 마십시오.

>[!NOTE]
>
> 일반적으로 바인딩된 필드와 바인딩되지 않은 필드가 바인딩되지 않은 필드에서 사용자가 채운 데이터에 교차되는 경우 혼합하지 마십시오. 가능한 경우 스키마나 XFA 양식 템플릿을 수정하고 바인딩되지 않은 필드에 대한 항목을 추가하여 바인딩된 데이터가 제출된 데이터의 다른 필드와 같이 사용할 수 있도록 해야 합니다.

## 사용자 데이터 미리 채우기에 대해 지원되는 프로토콜 {#supported-protocols-for-prefilling-user-data}

적응형 Forms은 유효한 정규 표현식으로 구성된 경우 다음 프로토콜을 통해 미리 채우기 데이터 형식의 사용자 데이터로 미리 채울 수 있습니다.

### crx:// 프로토콜 {#the-crx-protocol}

```javascript
http
https://`servername`/content/forms/af/xml.html?wcmmode=disabled&dataRef=crx:///tmp/fd/af/myassets/sample.xml
```

지정한 노드에는 라는 속성이 있어야 합니다. `jcr:data` 데이터를 보관합니다.

### file:// 프로토콜  {#the-file-protocol-nbsp}

```javascript
https://`servername`/content/forms/af/someAF.html?wcmmode=disabled&dataRef=file:///C:/Users/form-user/Downloads/somesamplexml.xml
```

참조된 파일은 동일한 서버에 있어야 합니다.

### https:// 프로토콜 {#the-http-protocol}

```javascript
https://`servername`/content/forms/af/xml.html?wcmmode=disabled&dataRef=https://servername/somesamplexmlfile.xml
```

### service:// 프로토콜 {#the-service-protocol}

```javascript
https://`servername`/content/forms/af/abc.html?wcmmode=disabled&dataRef=service://[SERVICE_NAME]/[IDENTIFIER]
```

- SERVICE_NAME은 OSGI 미리 채우기 서비스의 이름을 나타냅니다. 다음을 참조하십시오 [미리 채우기 서비스 만들기 및 실행](prepopulate-adaptive-form-fields.md#create-and-run-a-prefill-service).
- IDENTIFIER는 미리 채우기 데이터를 가져오기 위해 OSGI 미리 채우기 서비스에 필요한 메타데이터를 나타냅니다. 로그인한 사용자에 대한 식별자는 사용할 수 있는 메타데이터의 예입니다.

>[!NOTE]
>
> 인증 매개 변수 전달은 지원되지 않습니다.

### slingRequest에서 데이터 속성 설정 {#setting-data-attribute-in-slingrequest}

다음을 설정할 수도 있습니다 `data` 의 속성 `slingRequest`, 여기서 `data` 속성은 아래 샘플 코드에 표시된 대로 XML 또는 JSON이 포함된 문자열입니다(예: XML용).

```javascript
<%
           String dataXML="<afData>" +
                            "<afUnboundData>" +
                                "<data>" +
                                    "<first_name>"+ "Tyler" + "</first_name>" +
                                    "<last_name>"+ "Durden " + "</last_name>" +
                                    "<gender>"+ "Male" + "</gender>" +
                                    "<location>"+ "Texas" + "</location>" +
                                    "</data>" +
                            "</afUnboundData>" +
                        "</afData>";
        slingRequest.setAttribute("data", dataXML);
%>
```

모든 데이터가 포함된 간단한 XML 또는 JSON 문자열을 작성하여 slingRequest에서 설정할 수 있습니다. 이 작업은 slingRequest 데이터 속성을 설정할 수 있는 페이지에 포함하려는 모든 구성 요소에 대해 렌더러 JSP에서 쉽게 수행할 수 있습니다.

예를 들어 특정 유형의 헤더가 있는 페이지에 특정 디자인을 사용하려는 경우. 이를 달성하기 위해 자신의 것을 쓸 수 있다 `header.jsp`: 페이지 구성 요소에 포함하고 `data` 특성.

또 다른 좋은 예는 Facebook, Twitter 또는 LinkedIn과 같은 소셜 계정을 통해 로그인할 때 데이터를 미리 채우는 사용 사례입니다. 이 경우 간단한 JSP를 포함할 수 있습니다 `header.jsp`: 사용자 계정에서 데이터를 가져오고 데이터 매개 변수를 설정합니다.

prefill-page component.zip

[파일 가져오기](assets/prefill-page-component.zip)
페이지 구성 요소의 샘플 prefill.jsp

## [!DNL AEM Forms] 사용자 정의 미리 채우기 서비스 {#aem-forms-custom-prefill-service}

사전 정의된 소스에서 데이터를 지속적으로 읽는 시나리오에 대해 사용자 지정 미리 채우기 서비스를 사용할 수 있습니다. 미리 채우기 서비스는 정의된 데이터 소스에서 데이터를 읽고 적응형 양식의 필드를 미리 채우기 데이터 파일의 콘텐츠로 채웁니다. 또한 미리 채워진 데이터를 적응형 양식과 영구적으로 연결할 수 있습니다.

### 미리 채우기 서비스 만들기 및 실행 {#create-and-run-a-prefill-service}

프리필 서비스는 OSGi 서비스이며 OSGi 번들을 통해 패키징된다. OSGi 번들을 만들고, 업로드한 다음, 다음에 설치합니다. [!DNL AEM Forms] 번들. 번들 만들기를 시작하기 전에 다음을 수행하십시오.

- [다운로드 [!DNL AEM Forms] 클라이언트 SDK](https://helpx.adobe.com/kr/aem-forms/kb/aem-forms-releases.html)
- 보일러 플레이트 패키지 다운로드

- crx-repository에 데이터(데이터 미리 채우기) 파일을 넣습니다. crx-repository의 \contents 폴더에 있는 임의의 위치에 파일을 배치할 수 있습니다.

[파일 가져오기](assets/prefill-sumbit-xmlsandcontentpackage.zip)

#### 미리 채우기 서비스 만들기 {#create-a-prefill-service}

보일러플레이트 패키지(샘플 미리 채우기 서비스 패키지)에는 [!DNL AEM Forms] 미리 채우기 서비스. 코드 편집기에서 상용구 패키지를 엽니다. 예를 들어 편집할 Eclipse에서 보일러판 프로젝트를 엽니다. 코드 편집기에서 상용구 패키지를 연 후 다음 단계를 수행하여 서비스를 만듭니다.

1. 편집할 src\main\java\com\adobe\test\Prefill.java 파일을 엽니다.
1. 코드에서 다음 값을 설정합니다.

   - `nodePath:` crx-repository 위치를 가리키는 노드 경로 변수에는 데이터(미리 채우기) 파일의 경로가 포함됩니다. 예: /content/prefilldata.xml
   - `label:` label 매개 변수는 서비스의 표시 이름을 지정합니다. 예: 기본 미리 채우기 서비스

1. 저장 후 닫기 `Prefill.java` 파일.
1. 추가 `AEM Forms Client SDK` boilerplate 프로젝트의 빌드 경로로 패키지입니다.
1. 프로젝트를 컴파일하고 번들에 대한 .jar를 만듭니다.

#### 미리 채우기 서비스 시작 및 사용 {#start-and-use-the-prefill-service}

미리 채우기 서비스를 시작하려면 JAR 파일을에 업로드합니다. [!DNL AEM Forms] 웹 콘솔 및 서비스를 활성화합니다. 이제 서비스가 적응형 Forms 편집기에 표시되기 시작합니다. 미리 채우기 서비스를 적응형 양식에 연결하려면 다음 작업을 수행하십시오.

1. Forms 편집기에서 적응형 양식을 열고 양식 컨테이너에 대한 속성 패널을 엽니다.
1. 속성 콘솔에서 다음 위치로 이동합니다. [!DNL AEM Forms] 컨테이너 > 기본 > 미리 채우기 서비스.
1. 기본 미리 채우기 서비스를 선택하고 **[!UICONTROL 저장]**. 서비스는 양식에 연결됩니다.

<!-- ## Prepopulate data at client {#prefill-at-client}

When you prefill an Adaptive Form, the [!DNL AEM Forms] server merges data with an Adaptive Form and delivers the filled form to you. By default, the data merge action takes place at the server.

You can configure the [!DNL AEM Forms] server to perform the data merge action at the client instead of the server. It significantly reduces the time required to prefill and render Adaptive Forms. By default, the feature is disabled. You can enable it from the Configuration Manager or command line.

* To enable or disable from configuration manager:
  1. Open AEM Configuration Manager.
  1. Locate and open the Adaptive Form and Interactive Communication Web Channel Configuration
  1. Enable the Configuration.af.clientside.datamerge.enabled.name option
* To enable or disable from the command line:
  * To enable, run the following cURL command:
    `curl -u admin:admin -X POST -d apply=true \ -d propertylist=af.clientside.datamerge.enabled \ -d af.clientside.datamerge.enabled=true \ http://${crx.host}:${crx.port}/system/console/configMgr/Adaptive%20Form%20and%20Interactive%20Communication%20Web%20Channel%20Configuration`

  * To disable, run the following cURL command:
    `curl -u admin:admin -X POST -d apply=true \ -d propertylist=af.clientside.datamerge.enabled \ -d af.clientside.datamerge.enabled=false \ http://${crx.host}:${crx.port}/system/console/configMgr/Adaptive%20Form%20and%20Interactive%20Communication%20Web%20Channel%20Configuration`

   To take full advantage of the prepopulate data at client option, update your prefill service to return [FileAttachmentMap](https://helpx.adobe.com/experience-manager/6-5/forms/javadocs/com/adobe/forms/common/service/PrefillData.html) and [CustomContext](https://helpx.adobe.com/experience-manager/6-5/forms/javadocs/com/adobe/forms/common/service/PrefillData.html) -->