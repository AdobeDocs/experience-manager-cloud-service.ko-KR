---
title: 적응형 Forms에 대한 기록 문서 생성
description: 적응형 Forms용 레코드 문서(DoR)에 대한 템플릿을 생성하는 방법을 설명합니다.
exl-id: 15540644-c0c3-45ce-97d3-3bdaa16fb4b6
source-git-commit: 90a10fd4e414f3457fa9658a50ccd0cf935fdb69
workflow-type: tm+mt
source-wordcount: '3172'
ht-degree: 2%

---

# 적응형 Forms(핵심 구성 요소)에 대한 레코드 문서 생성

## 개요 {#overview}

양식을 채우거나 제출하면 양식의 레코드를 인쇄나 문서 형식으로 유지할 수 있습니다. 이 레코드를 레코드 문서(DoR)라고 합니다. 제출된 양식의 인쇄용 복사본입니다. 고객이 나중에 입력한 정보에 대한 레코드 문서를 참조하거나 기록 문서를 사용하여 PDF 형식으로 양식과 콘텐츠를 함께 보관할 수도 있습니다.

![기록 문서](assets/document-of-record.png)

기록 문서를 만들기 위해 XFA 또는 Acrobat 기반 템플릿은 적응형 양식을 통해 수집된 데이터와 병합됩니다. 자동으로 또는 온디맨드로 기록 문서를 생성할 수 있습니다. 요청 시 옵션을 사용하면 사용자 지정 XFA 또는 Acroform 기반 템플릿을 지정하여 기록 문서에 사용자 지정 모양을 제공할 수 있습니다.

다음과 같은 작업을 수행할 수 있습니다.

* [XFA 기반 레코드 문서 생성](#generate-an-XFA-based-document-of-record)
* [Acroform 기반(Acrobat 양식 PDF) 레코드 문서 생성](#generate-an-Acroform-based-document-of-record)
* [기록 문서 자동 생성](#auto-generate-a-document-of-record)

## 시작하기 전 {#components-to-automatically-generate-a-document-of-record}

학습 및 준비가 완료되기 전에 레코드 문서에 필요한 자산을 준비합니다.

**기본 템플릿:** Forms 디자이너 또는 Acrobat 양식(AcroForm)에서 만든 XFA 템플릿(XDP 파일)입니다. [기본 템플릿](#base-template-of-a-document-of-record) 레코드 문서에 대한 스타일 및 브랜딩 정보를 지정하는 데 사용됩니다. XFA 템플릿(XDP 파일)을 이전에 AEM Forms 인스턴스에 업로드합니다.

**적응형 양식:** 기록 문서를 생성할 적응형 양식입니다.

## XFA 기반 레코드 문서 생성 {#generate-an-XFA-based-document-of-record}

XFA 템플릿(XDP 파일)을 AEM Forms 인스턴스에 업로드합니다. XFA 템플릿(XDP 파일)을 레코드 문서의 템플릿으로 사용하도록 적응형 양식을 구성하려면 다음 단계를 수행하십시오.

1. Experience Manager 작성자 인스턴스에서 **[!UICONTROL Forms]** > **[!UICONTROL Forms 및 문서].**
1. 폼 또는 적응형 양식 만들기를 선택하고 **[!UICONTROL 속성]**.
1. 속성 창에서 **[!UICONTROL 양식 모델]**.
1. 설정  **[!UICONTROL 양식 모델]** 탭, **[!UICONTROL 선택 위치]** 드롭다운에서 을 선택합니다. **[!UICONTROL 양식 데이터 모델]**, **[!UICONTROL 스키마]** 또는 **[!UICONTROL 없음]**. 양식을 만들 때 양식 모델을 선택할 수도 있습니다.
1. 양식 모델 탭의 레코드 템플릿 구성 문서 섹션에서 **양식 서식 파일을 레코드 서식 파일 문서로 연결**. 이 옵션을 선택하면 시스템에서 사용할 수 있는 모든 XFA 템플릿(XDP 파일)이 표시됩니다. 적절한 파일을 선택합니다. 또한 적용형 양식과 선택한 XFA 템플릿(XDP 파일)에 동일한 스키마(데이터 스키마)가 사용되는지 확인하십시오.
1. 클릭 **[!UICONTROL 완료.]**

이제 적응형 양식이 XDP 파일을 레코드 문서의 템플릿으로 사용하도록 구성되었습니다. 다음 단계는 다음과 같습니다 [해당 템플릿 필드에 적응형 양식 구성 요소 바인딩](#bind-adaptive-form-components-with-template-fields).

## Acrobat 기반 레코드 문서 생성 {#generate-an-Acroform-based-document-of-record}

Adobe Acrobat PDF(Acrobat)를 AEM Forms 인스턴스에 업로드합니다. 다음 단계를 수행하여 Adobe Acrobat PDF(Acroform)을 기록 문서의 템플릿으로 사용하도록 적응형 양식을 구성합니다.

1. Experience Manager 작성자 인스턴스에서 **[!UICONTROL Forms]** > **[!UICONTROL Forms 및 문서].**
1. 양식 또는 **[!UICONTROL 적응형 양식 만들기]**&#x200B;를 클릭하고 **[!UICONTROL 속성]**.
1. 속성 창에서 **[!UICONTROL 양식 모델]**.
1. 설정  **[!UICONTROL 양식 모델]** 탭, **[!UICONTROL 선택 위치]** 드롭다운에서 을 선택합니다. **[!UICONTROL 양식 데이터 모델]**, **[!UICONTROL 스키마]** 또는 **[!UICONTROL 없음]**. 양식을 만들 때 양식 모델을 선택할 수도 있습니다.
1. 양식 모델 탭의 레코드 템플릿 구성 문서 섹션에서 **양식 서식 파일을 레코드 서식 파일 문서로 연결**. 이 옵션을 선택하면 시스템에서 사용할 수 있는 모든 Acrobat PDF(Acroform)이 표시됩니다. 사용할 Acroform을 선택합니다.
1. 클릭 **[!UICONTROL 완료.]**

이제 적응형 양식이 레코드 문서의 템플릿으로 Acrobat을 사용하도록 구성되었습니다. 다음 단계는 다음과 같습니다 [해당 템플릿 필드에 적응형 양식 구성 요소 바인딩](#bind-adaptive-form-components-with-template-fields).

## 기록 문서 자동 생성 {#auto-generate-a-document-of-record}

적응형 양식이 자동으로 레코드 문서를 생성하도록 구성되면 양식이 변경될 때마다 해당 레코드 문서가 즉시 업데이트됩니다. 예를 들어 기존 적응형 양식에서 필드를 제거하면 해당 필드도 제거되고 레코드 문서에도 표시되지 않습니다. Document of Record를 자동으로 생성할 수 있는 여러 가지 다른 이점이 있습니다.

* 양식 개발자는 데이터 바인딩을 수동으로 유지 관리할 필요가 없습니다. 자동 생성된 기록 문서는 데이터 바인딩 관련 업데이트를 처리합니다.
* 양식 개발자는 레코드 문서에서 제외로 표시된 필드를 수동으로 숨길 필요가 없습니다. 자동 생성된 레코드 문서는 이러한 필드를 제외하도록 사전 구성되어 있습니다.
* 자동으로 생성된 레코드 문서 옵션을 사용하면 레코드 문서에 대한 양식 서식 파일을 만드는 데 필요한 시간이 절약됩니다.
* 자동 생성된 기록 문서 옵션을 사용하면 다른 기본 템플릿을 사용하여 다양한 스타일 및 모양새를 사용할 수 있습니다. 조직의 기록 문서에 가장 적합한 스타일과 모양을 선택하는 데 도움이 됩니다. 스타일을 지정하지 않으면 시스템 스타일이 기본값으로 설정됩니다.
* 자동 생성된 기록 문서를 사용하면 양식의 변경 사항이 즉시 기록 문서에 반영됩니다.

다음 단계를 수행하여 적응형 양식을 구성하여 기록 문서를 자동으로 생성합니다.

1. Experience Manager 작성자 인스턴스에서 **[!UICONTROL Forms]** > **[!UICONTROL Forms 및 문서].**
1. 폼 또는 적응형 양식 만들기를 선택하고 **[!UICONTROL 속성]**.
1. 속성 창에서 **[!UICONTROL 양식 모델]**.
1. 설정  **[!UICONTROL 양식 모델]** 탭, **[!UICONTROL 선택 위치]** 드롭다운에서 을 선택합니다. **[!UICONTROL 양식 데이터 모델]**, **[!UICONTROL 스키마]** 또는 **[!UICONTROL 없음]**. 양식을 만들 때 양식 모델을 선택할 수도 있습니다.
1. 양식 모델 탭의 레코드 템플릿 구성 문서 섹션에서 **기록 문서 생성**.
1. 클릭 **[!UICONTROL 완료.]**

## 템플릿 필드에 적응형 양식 구성 요소 바인딩 {#bind-adaptive-form-components-with-template-fields}

적응형 양식 필드를 템플릿 필드에 바인딩하여 해당 레코드 필드의 문서에 캡처된 양식 데이터를 표시합니다. 적응형 양식 구성 요소를 해당 레코드 템플릿 필드 문서에 바인딩하려면 다음을 수행합니다.

1. 편집을 위해 사용자 지정 양식 템플릿을 사용하도록 구성된 적응형 양식을 엽니다.

1. 적응형 양식 구성 요소를 선택하고 구성 열기 를 클릭합니다 ![구성](assets/Smock_Wrench_18_N.svg) 아이콘. 속성 브라우저를 엽니다.

1. 속성 브라우저에서 필드를 찾아 선택합니다.

   * (AcroForm 템플릿의 경우) **[!UICONTROL 레코드 바인딩 참조 필드 문서]** 속성을 사용합니다.
   * (XFA 템플릿의 경우) **[!UICONTROL 데이터 모델 바인딩 참조]** 속성을 사용합니다.

1. **[!UICONTROL 저장]**&#x200B;을 클릭합니다.

<!-- 
In the following video Adaptive Form components are binded with corresponding Acroform template fields and the Document of Record is sent as an email attachment.
-->

&quot;이메일 보내기&quot;, &quot;AEM 워크플로우 호출&quot;, &quot;전원 자동화 흐름 호출&quot; 등의 제출 작업을 사용할 수 있습니다 [작업 제출](configuring-submit-actions.md) 레코드 문서를 수신하려면
![이미지 제출 작업](/help/forms/assets/submit-actions-img.png)



## 레코드 문서 템플릿에 대한 증분 업데이트 {#document-of-record-template-incremental-updates}

적응형 양식 및 기록 템플릿의 해당 문서는 일정 기간 동안 발전할 수 있습니다. 적응형 양식 또는 레코드 문서 템플릿에 필드를 추가, 제거 또는 수정하도록 선택할 수 있습니다.

레코드 문서 템플릿을 변경하고 변경된 레코드 문서 템플릿을 AEM Forms에 업로드하면 적응형 Forms 편집기가 변경된 바인딩을 자동으로 감지하고 새 바인딩이 필요한 적응형 양식 구성 요소에 대해 알려줍니다. 레코드 문서에 대한 증분 업데이트를 수행할 수 있습니다.

예를 들어, 조직, *We.Retail*&#x200B;에는 AcroForm 기반 레코드 문서가 있습니다. *we-retail-invoice.pdf*. 템플릿은 다음과 같습니다.

![원래 템플릿](assets/we-retail-invoice.png)

잠시 템플릿을 사용한 후 조직에서 이름을 바꾸기로 합니다 `invoice-number` 필드 대상 `bill-number` 구매자의 필드 및 이메일 주소를 캡처합니다. 개발자가 `invoice-number` 필드를 만들고 템플릿에 이메일 필드를 추가합니다. 또한 이라는 템플릿의 새 버전을 만듭니다  *we-retail-invoice-v2.pdf*.

![업데이트된 템플릿](assets/we-retail-new-invoice.png)

<!--

The developer uploads and applies to the updated template to the adaptive form. The adaptive form automatically detects and displays list of fields where binding has changed.

![Binding Error](assets/we-retail-binding-error.png)

The form developer binds Adaptive Forms fields with corresponding Document of Record template.

-->

>[!VIDEO](assets/we-retail-binding.mp4)

이제 적응형 양식이 제출되면 업데이트된 레코드 문서가 생성됩니다.

![세션 속성을 사용하도록-](assets/we-retail-new-invoice-sent-to-customer.png)

## 레코드 문서로 작업할 때 주요 고려 사항 {#key-considerations-when-working-with-document-of-record}

적응형 Forms에 대한 기록 문서에서 작업할 때에는 다음 고려 사항 및 제한 사항을 기억하십시오.

* 레코드 템플릿 문서는 서식 있는 텍스트를 지원하지 않습니다. 따라서 정적 적응형 양식의 리치 텍스트 또는 최종 사용자가 입력한 정보에 있는 리치 텍스트는 레코드 문서에 일반 텍스트로 표시됩니다.
* 적응형 양식의 문서 조각은 레코드 문서에 표시되지 않습니다. 그러나 적응형 양식 조각이 지원됩니다.
* XML 스키마 기반 적응형 양식에 대해 생성된 레코드 문서의 콘텐츠 바인딩은 지원되지 않습니다.
* 지역화된 버전의 Document of Record는 사용자가 Document of Record 렌더링을 요청할 때 로케일에 대한 요청 시 생성됩니다. 기록 문서 현지화는 적응형 양식의 현지화와 함께 수행됩니다. <!-- For more information on localization of Document of Record and Adaptive Forms see Using AEM translation workflow to localize Adaptive Forms and Document of Record.-->

<!-- ## Configure an adaptive form to generate  Document of Record {#adaptive-form-types-and-their-documents-of-record}

While creating an adaptive form, in the Form Model tab of Adaptive Form properties, select one the following option: 

* **None**
  Select the option to create an Adaptive Form without a form model. When the option is selected, the Document of Record is automatically generated for your Adaptive Form.

* **[Associate form template as a Document of Record template](creating-adaptive-form.md#create-an-adaptive-form-based-on-an-xfa-form-template)**
  
  Select the option to use an XFA Form as a template for Document of Record. 

* **[Generate Document of Record](creating-adaptive-form.md#create-an-adaptive-form-based-on-xml-or-json-schema)**
  Select the option to use an XFA Form as a template. When the option is selected, the Document of Record is automatically generated for your Adaptive Form. When you use an XML schema as a template for an Adaptive Form, ensure that the adaptive form and associated XFA Form use the same XML schema as your Adaptive Form
  

When you select a form model, configure Document of Record using options available under Document of Record Template Configuration. See [Document of Record Template Configuration](#document-of-record-template-configuration). -->

## 적응형 양식 요소 매핑 {#mapping-of-adaptive-form-elements}

다음 표에서는 적응형 양식 구성 요소와 해당 XFA 구성 요소를 설명하고 이러한 구성 요소가 기록 문서에 표시되는 경우를 설명합니다.

### 필드 {#fields}

<table>
 <tbody>
  <tr>
   <th>적응형 양식 구성 요소</th>
   <th>해당 XFA 구성 요소</th>
   <th>레코드 템플릿 문서에 기본적으로 포함됩니까?</th>
   <th>메모</th>
  </tr>
  <tr>
   <td>버튼</td>
   <td>버튼</td>
   <td>false</td>
   <td> </td>
  </tr>
  <tr>
   <td>확인란</td>
   <td>체크 상자</td>
   <td>true</td>
   <td> </td>
  </tr>
  <tr>
   <td>날짜 선택</td>
   <td>날짜/시간 필드</td>
   <td>true</td>
   <td> </td>
  </tr>
  <tr>
   <td>드롭다운 목록</td>
   <td>드롭다운 목록</td>
   <td>true</td>
   <td> </td>
  </tr>
  <tr>
   <td>숫자 상자</td>
   <td>숫자 필드</td>
   <td>true</td>
   <td> </td>
  </tr>
  <tr>
   <td>라디오 단추</td>
   <td>라디오 단추</td>
   <td>true</td>
   <td> </td>
  </tr>
  <tr>
   <td>텍스트 상자</td>
   <td>텍스트 필드</td>
   <td>true</td>
   <td> </td>
  </tr>
  <tr>
   <td>재설정 버튼</td>
   <td>재설정 단추</td>
   <td>false</td>
   <td> </td>
  </tr>
  <tr>
   <td>제출 단추</td>
   <td><p>전자 메일 전송 단추</p> <p>HTTP 전송 단추</p> </td>
   <td>false</td>
   <td> </td>
  </tr>
  <tr>
   <td>첨부 파일</td>
   <td> </td>
   <td>false</td>
   <td>레코드 문서에서 사용할 수 없습니다. 첨부 파일을 통해 기록 문서에서만 사용할 수 있습니다.</td>
  </tr>
 </tbody>
</table>

### 컨테이너 {#containers}

<table>
 <tbody>
  <tr>
   <th>적응형 양식 구성 요소</th>
   <th>해당 XFA 구성 요소</th>
   <th>메모</th>
  </tr>
  <tr>
   <td>패널<br /> </td>
   <td>하위 양식<br /> </td>
   <td>반복 가능한 패널은 반복 가능한 하위 폼에 매핑됩니다.</td>
  </tr>
 </tbody>
</table>

### 정적 구성 요소 {#static-components}

| 적응형 양식 구성 요소 | 해당 XFA 구성 요소 | 메모 |
|---|---|---|
| 이미지 | 이미지 | 바인딩 또는 바인딩되지 않은 TextDraw 및 Image 구성 요소는 레코드 문서 설정을 사용하여 제외하지 않는 한 XSD 기반 적응형 양식의 레코드 문서에 항상 표시됩니다. |
| 텍스트 | 텍스트 |

### 표 {#tables}

머리글, 바닥글 및 행과 같은 적응형 Forms 테이블 구성 요소는 해당 XFA 구성 요소에 매핑됩니다. 반복 가능한 패널을 기록 문서에서 테이블에 매핑할 수 있습니다.

## 레코드 문서의 기본 템플릿 {#base-template-of-a-document-of-record}

기본 템플릿은 레코드 문서에 스타일 및 모양 정보를 제공합니다. 자동 생성된 레코드 문서의 기본 모양을 사용자 정의할 수 있습니다. 예를 들어 기본 템플릿을 사용하여 머리글에 회사 로고를 추가하고 레코드 문서의 바닥글에 저작권 정보를 추가할 수 있습니다.

기본 템플릿의 마스터 페이지는 레코드 문서 템플릿의 마스터 페이지로 사용됩니다. 마스터 페이지에는 페이지 머리글, 페이지 바닥글 및 페이지 번호와 같은 정보가 있을 수 있으며, 이러한 정보는 레코드 문서에 적용할 수 있습니다. 기록 문서 자동 생성을 위해 기본 템플리트를 사용하여 이러한 정보를 기록 문서에 적용할 수 있습니다. 기본 템플릿을 사용하면 필드의 기본 속성을 변경할 수 있습니다.

항상 팔로우 [기본 템플릿 규칙](#base-template-conventions) 기본 템플릿을 디자인하는 경우

## 기본 템플릿 규칙 {#base-template-conventions}

기본 템플릿은 레코드 문서의 머리글, 바닥글, 스타일 지정 및 모양을 정의하는 데 사용됩니다. 머리글 및 바닥글에는 회사 로고 및 저작권 텍스트와 같은 정보가 포함될 수 있습니다. 기본 템플릿의 첫 번째 마스터 페이지가 복사되어 레코드 문서의 마스터 페이지로 사용됩니다. 이 페이지에는 머리글, 바닥글, 페이지 번호 또는 레코드 문서의 모든 페이지에 표시되어야 하는 기타 정보가 포함됩니다. 기본 템플릿 규칙을 준수하지 않는 기본 템플릿을 사용하는 경우 기본 템플릿의 첫 번째 마스터 페이지가 여전히 레코드 문서 템플릿에서 사용됩니다. 기본 템플릿을 규칙에 따라 디자인하고 기록 문서 자동 생성에 사용하는 것이 좋습니다.

**기본 페이지 규칙**

* 기본 템플릿에서 루트 하위 양식의 이름을 `AF_METATEMPLATE` 마스터 페이지를 `AF_MASTERPAGE`.

* 이름이 인 마스터 페이지 `AF_MASTERPAGE` 아래에 `AF_METATEMPLATE` 루트 하위 양식은 머리글, 바닥글 및 스타일 지정 정보를 추출하는 데 선호됩니다.

* If `AF_MASTERPAGE` 가 없으면 기본 템플릿에 있는 첫 번째 마스터 페이지가 사용됩니다.

**필드에 대한 스타일 지정 규칙**

* 레코드 문서의 필드에 스타일을 적용하려면 기본 템플릿은 `AF_FIELDSSUBFORM` 아래 하위 `AF_METATEMPLATE` 루트 하위 폼

* 이러한 필드의 속성은 레코드 문서의 필드에 적용됩니다. 이러한 필드는 `AF_<name of field in all caps>_XFO` 명명 규칙입니다. 예를 들어, 확인란에 대한 필드 이름은 `AF_CHECKBOX_XFO`.

기본 템플릿을 만들려면 Forms 디자이너에서 다음을 수행합니다.

1. 클릭 **[!UICONTROL 파일]** > **[!UICONTROL 새로 만들기]**.
1. 을(를) 선택합니다 **[!UICONTROL 템플릿 기반]** 선택 사항입니다.

1. 을(를) 선택합니다 **[!UICONTROL Forms - 기록 문서]** 카테고리.
1. 선택 **[!UICONTROL DoR 기본 템플릿]**.
1. 클릭 **[!UICONTROL 다음]** 필요한 정보를 제공합니다.

1. (선택 사항) 레코드 문서의 필드에 적용할 필드의 스타일 및 모양을 수정합니다.
1. 양식을 저장합니다.
   ![기본 속성](/help/forms/assets/form-designer-dor-img.png)

이제 저장된 양식을 기록 문서의 기본 템플릿으로 사용할 수 있습니다. 기본 템플릿에 있는 스크립트를 수정하거나 제거하지 마십시오.

**기본 템플릿 수정**

* 기본 템플릿의 필드에 스타일을 적용하지 마십시오. 기본 템플릿에 대한 업그레이드가 자동으로 선택되도록 기본 템플릿에서 해당 필드를 제거하는 것이 좋습니다.
* 기본 템플릿을 수정하는 동안 스크립트를 제거, 추가 또는 수정하지 마십시오.

기본 템플릿을 디자인하려면 위에서 언급한 규칙 및 지침을 엄격히 따르십시오.

## 기록 문서에서 브랜딩 정보 사용자 정의 {#customize-the-branding-information-in-document-of-record}

기록 문서를 생성하는 동안 기록 문서 탭에서 기록 문서에 대한 브랜딩 정보를 변경할 수 있습니다. 레코드 문서 탭에는 로고, 모양, 레이아웃, 머리글 및 바닥글, 면책조항 및 선택되지 않은 확인란 및 라디오 단추 옵션 포함 여부와 같은 옵션이 포함되어 있습니다.

기록 문서 탭에서 입력하는 브랜딩 정보를 현지화하려면 브라우저의 로케일이 적절히 설정되어 있는지 확인하십시오. 기록 문서의 브랜딩 정보를 사용자 정의하려면 다음 단계를 수행합니다.

1. [기록 문서]에서 패널(루트 패널)을 선택한 다음 ![구성](assets/configure.png).
1. 탭 ![도트](assets/dortab.png). 기록 문서 탭이 나타납니다.
1. 기본 템플릿 또는 레코드 문서 렌더링을 위한 사용자 지정 템플릿을 선택합니다. 기본 템플릿을 선택하면 템플릿 드롭다운 아래에 레코드 문서의 축소판 미리 보기가 나타납니다.
1. 기본값을 선택하는지 사용자 지정 템플릿을 선택하는지 여부에 따라 다음 속성 중 일부 또는 전부가 기록 문서 탭에 나타납니다. 아래 등록 정보를 지정하여 기록 문서의 모양을 정의합니다.

   1. **기본 속성**:
      * **템플릿**: 사용자 지정 템플릿을 선택하려면 [!DNL AEM Forms] server. 에서 사용할 수 없는 템플릿을 사용하려면 [!DNL AEM Forms] server, 먼저 XDP를 업로드해야 합니다 [!DNL AEM Forms] server.
      * **강조색**: 레코드 PDF 문서에서 머리글 텍스트 및 구분선이 렌더링되는 색상입니다.
      * **글꼴 패밀리**: 레코드 PDF 문서에 있는 텍스트의 글꼴 패밀리입니다.
      * **데이터 모델에 바인딩되지 않은 양식 개체 포함**: 속성을 설정하면 레코드 문서에서 스키마 기반 적응형 양식의 바인딩되지 않은 필드가 포함됩니다.
      * **레코드 문서에서 숨겨진 필드 제외**: 속성을 설정하면 레코드 문서에서 제외하기 위해 숨겨진 필드가 식별됩니다.
      * **패널 설명 숨기기**: 속성을 설정하면 레코드 문서에서 패널/테이블의 설명이 제외됩니다. 패널 및 테이블에 적용 가능합니다.
   1. **양식 필드 속성**:
      * **확인란 및 라디오 단추 구성 요소의 경우 선택한 값만 표시합니다**: 속성을 설정하면 확인란 및 라디오 단추의 선택한 값만 표시됩니다 [!UICONTROL 기록 문서].
      * **여러 값에 대한 구분자**: 쉼표나 줄바꿈 같은 구분자를 선택하여 여러 값을 표시할 수 있습니다.
      * **옵션 정렬**: 원하는 정렬(가로, 세로, 적응형 양식과 동일함)을 선택하여 표시할 확인란 또는 라디오 단추와 같은 필드에 대한 정렬을 설정할 수 있습니다 [!UICONTROL 기록 문서]. 기본적으로 의 필드에 대해 세로 맞춤이 설정됩니다 [!UICONTROL 기록 문서]. 에서 속성 설정 [!UICONTROL 양식 필드 속성] DoR은 [!UICONTROL 항목 정렬] 추가 정보. 경우에 따라 [!UICONTROL 적응형 양식과 동일] 옵션에는 적응형 양식 작성자 인스턴스에 구성된 정렬이 사용됩니다 [!UICONTROL 기록 문서] 필드.
      * **가로 정렬을 위한 옵션 수**: 가로 정렬을 위해 기록 문서에 표시할 옵션 수를 설정할 수 있습니다.
   1. **마스터 페이지  속성**:
      * **로고 이미지**: 적응형 양식에서 로고 이미지를 사용하거나, DAM에서 선택하거나, 컴퓨터에서 로고 이미지를 업로드하도록 선택할 수 있습니다.
      * **양식 제목**: DoR의 제목입니다.
      * **머리글 텍스트**: 레코드 문서의 머리글 섹션에 표시되는 텍스트입니다.
      * **면책조항 레이블**: 면책조항 레이블.
      * **면책조항**: 기록 문서에 대한 권한 및 의무의 범위를 지정하는 텍스트입니다.
      * **면책조항 텍스트**: 면책조항 텍스트입니다.

      ![마스터 페이지  속성](/help/forms/assets/dorpropertiesimg.png)
   >[!NOTE]
   >
   >6.3 이전 버전의 디자이너로 만든 적응형 양식 서식 파일을 사용하는 경우, 강조색 및 글꼴 패밀리 속성이 작동하려면 루트 하위 양식 아래의 적응형 양식 서식 파일에 다음 내용이 있는지 확인하십시오.

   ```xml
   <proto>
   <font typeface="Arial"/>
   <fill>
   <color value="4,166,203"/>
   </fill>
   <edge>
   <color value="4,166,203"/>
   </edge>
   </proto>
   ```

1. 브랜딩 변경 사항을 저장하려면 **[!UICONTROL 완료]**.



## 레코드 문서의 패널에 대한 표 및 열 레이아웃 {#table-and-column-layouts-for-panels-in-document-of-record}

적응형 양식은 여러 양식 필드가 있는 긴 양식일 수 있습니다. 적응형 양식의 정확한 사본으로 기록 문서를 저장하지 않을 수 있습니다. 이제 레코드 문서 PDF에서 하나 이상의 적응형 양식 패널을 저장할 테이블 또는 열 레이아웃을 선택할 수 있습니다.

[레코드 문서]를 생성하기 전에 패널의 설정에서 해당 패널에 대한 [레코드 문서의 레이아웃]을 [표] 또는 [열]로 선택합니다. 패널의 필드는 그에 따라 레코드 문서에서 구성됩니다.

![문서의 표 레이아웃에 렌더링된 패널의 필드](assets/dortablelayout.png)

문서의 표 레이아웃에 렌더링된 패널의 필드

![문서의 열 레이아웃에 렌더링된 패널의 필드](assets/dorcolumnlayout.png)

문서의 열 레이아웃에 렌더링된 패널의 필드

## 레코드 설정 문서 {#document-of-record-settings}

기록 문서 설정을 사용하면 기록 문서에 포함할 옵션을 선택할 수 있습니다. 예를 들어, 한 은행은 양식에 이름, 나이, 사회 보장 번호 및 전화 번호를 허용합니다. 이 양식은 은행 계좌 번호와 지점 상세내역을 생성합니다. Document of Record에서 이름, Social Security 번호, Bank Account 및 Branch Details만 표시하도록 선택할 수 있습니다.

기록 문서 구성 요소의 설정은 해당 등록 정보에서 사용할 수 있습니다. 구성 요소의 속성에 액세스하려면 구성 요소를 선택하고 ![cmppr](assets/cmppr.png) ( 오버레이에서)를 클릭합니다. 속성은 사이드바에 나열되며, 여기에서 다음 설정을 찾을 수 있습니다.

**필드 수준 설정**

* **기록 문서에서 제외**: true 속성을 설정하면 레코드 문서에서 필드가 제외됩니다. 이 속성은 명명된 스크립트 가능 속성입니다. `excludeFromDoR`. 그 행동은 다음에 따라 다르다 **숨겨진 경우 DoR에서 필드 제외** 양식 수준 속성입니다.

* **패널을 표로 표시:** 패널에 필드가 6개 미만인 경우 등록 정보를 설정하면 패널이 레코드 문서에 표로 표시됩니다. 패널에만 적용할 수 있습니다.
* **레코드 문서에서 제목 제외:** 속성을 설정하면 [레코드 문서]에서 패널/테이블의 제목이 제외됩니다. 패널 및 테이블에만 적용됩니다.
* **레코드 문서에서 설명 제외:** 속성을 설정하면 레코드 문서에서 패널/테이블의 설명이 제외됩니다. 패널 및 테이블에만 적용됩니다.

**양식 수준 설정**

* **DoR에 바인딩되지 않은 필드 포함:** 속성을 설정하면 스키마 기반 적응형 양식의 레코드 문서에서 바인딩되지 않은 필드가 포함됩니다. 기본적으로 true입니다.
* **숨겨진 경우 DoR에서 필드 제외:** 양식 제출 시 기록 문서에서 숨김 필드를 제외하려면 속성을 설정하십시오. 사용 설정 시 [서버에서 유효성 검사](/help/forms/configuring-submit-actions.md#server-side-revalidation-in-adaptive-form-server-side-revalidation-in-adaptive-form)를 지정하면 서버는 숨겨진 필드를 다시 계산하여 레코드 문서에서 해당 필드를 제외합니다.