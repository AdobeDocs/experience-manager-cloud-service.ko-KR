---
title: 적응형 양식 조각을 만들고 사용하는 방법
description: 양식 조각은 양식의 모듈식 재사용 가능한 구성 요소입니다. 효율적인 양식 어셈블리를 위해 양식 조각을 빌드하고 여러 양식에서 재사용하는 방법에 대해 알아봅니다.
uuid: bb4830b5-82a0-4026-9dae-542daed10e6f
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: author
feature: Adaptive Forms, Foundation Components
discoiquuid: 1a32eb24-db3b-4fad-b1c7-6326b5af4e5e
exl-id: e4d8bcb9-ce1f-425e-b35c-d0a79fa771f3
role: User, Developer
source-git-commit: bcd3a2a813833d7c1705e45829bcf769645cd154
workflow-type: tm+mt
source-wordcount: '2150'
ht-degree: 1%

---

# 적응형 양식에서 적응형 Forms 조각 생성 및 사용  {#adaptive-form-fragments}


| 버전 | 문서 링크 |
| -------- | ---------------------------- |
| AEM as a Cloud Service(Foundation 구성 요소) | 이 문서 |
| AEM as a Cloud Service (핵심 구성 요소) | [여기 클릭](/help/forms/adaptive-form-fragments-core-components.md) |
| AEM 6.5 | [여기 클릭](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-basic-authoring/adaptive-form-fragments.html?lang=ko) |

모든 양식은 특정 목적을 위해 설계되었지만 대부분의 양식에는 개인 정보 좋아요 이름 및 주소, 가족 세부 정보, 소득 세부 정보 등을 제공하는 것과 같은 몇 가지 공통 세그먼트가 있습니다. 양식 개발자는 새 양식을 만들 때마다 이러한 공통 세그먼트를 만들어야 합니다. 적응형 Forms는 패널 또는 필드 그룹 세그먼트 좋아요 양식을 한 번만 작성하고 적응형 Forms에서 재사용할 수 있는 편리한 메커니즘을 제공합니다. 이러한 재사용 가능한 독립 세그먼트를 적응형 양식 조각이라고 합니다.


## 조각 만들기 {#create-a-fragment}

적응형 양식 조각을 처음부터 만들거나 기존 적응형 양식에 패널을 조각으로 저장할 수 있습니다.

### 처음부터 조각 만들기 {#create-fragment-from-scratch}

1. https://[*hostname*]:[*포트*]/aem/forms.html 에서 작성자 인스턴스에 [!DNL AEM Forms] 로그인합니다.
1. 적응형 양식 단편만들기 >Adaptive Form Fragment **)를 클릭합니다**.
1. 조각의 제목, 이름, 설명 및 태그를 지정합니다.

   >[!NOTE]
   >
   >조각에 고유한 이름을 지정해야 합니다. 같은 이름의 다른 조각이 이미 있는 경우 조각을 만들 수 없습니다.

1. 클릭하여 **양식 모델** 탭을 열고 **다음에서 선택** 드롭다운 메뉴에서 조각에 대해 다음 모델 중 하나를 선택합니다.

   * **없음**: 양식 모델을 사용하지 않고 조각을 처음부터 만들도록 지정합니다.

     >[!NOTE]
     >
     > 적응형 Forms에서는 양식에서 단일 양식 조각(핵심 구성 요소 기반)을 여러 번 사용할 수 있습니다. none 기반 양식 조각과 schema 기반 양식 조각을 모두 지원합니다.

   * **양식 서식 파일**: [!DNL AEM Forms]에 업로드된 XDP 서식 파일을 사용하여 조각을 만들도록 지정합니다. 조각의 양식 모델로 적절한 XDP 템플릿을 선택합니다.

   ![양식 템플릿을 모델로 사용하여 적응형 양식 만들기](assets/form-template-model.png)

   선택한 양식 템플릿에서 조각으로 표시된 하위 양식도 표시됩니다. 드롭다운 목록에서 적응형 양식 조각에 대한 하위 양식을 선택할 수 있습니다.

   ![지정된 양식 서식 파일에서 하위 양식 선택](assets/fragment-subform.png)

   또한 드롭다운 상자에서 하위 양식에 대한 SOM 표현식을 지정하여 양식 템플릿에서 조각으로 표시되지 않은 하위 양식을 사용하여 적응형 양식 조각을 만들 수 있습니다.

   * **XML 스키마**: [!DNL AEM Forms]에 업로드된 XML 스키마를 사용하여 조각을 만들도록 지정합니다. 사용 가능한 XML 스키마를 업로드하거나 조각의 양식 모델로 선택할 수 있습니다.

   ![XML 스키마를 모델로 하여 적응형 양식 조각 만들기](assets/xml-schema-model.png)

   드롭다운 상자에서 선택한 스키마에 있는 complexType을 선택하여 적응형 양식 조각을 만들 수도 있습니다.

   ![지정한 XML 스키마 모델에서 복합 형식을 선택하십시오](assets/complex-type.png)

1. **만들기**&#x200B;를 클릭한 다음 **열기**&#x200B;를 클릭하여 기본 템플릿으로 편집 모드에서 조각을 엽니다.

편집 모드에서 적응형 양식 구성 요소를 AEM 사이드 킥에서 조각으로 드래그 앤 드롭할 수 있습니다. <!-- For information about Adaptive Form components, see Introduction to authoring Adaptive Forms. -->

또한 조각에 대한 양식 모델로 XML 스키마 또는 XDP 양식 템플릿을 선택한 경우 양식 모델 계층을 표시하는 새 탭이 콘텐츠 파인더에 나타납니다. 양식 모델 요소를 조각으로 드래그 앤 드롭할 수 있습니다. 추가된 양식 모델 요소는 연결된 XDP 또는 XSD의 원래 속성을 유지하면서 양식 구성 요소로 변환됩니다.

### 패널을 조각으로 저장 {#save-panel-as-a-fragment}

1. 적응형 양식 조각으로 저장할 패널이 포함된 적응형 양식을 엽니다.
1. 패널 도구 모음에서 **[!UICONTROL 조각으로 저장]**&#x200B;을 클릭합니다. 조각으로 저장 대화 상자가 열립니다.

   >[!NOTE]
   >
   >조각으로 저장하는 패널에 하위 패널이 포함된 경우 결과 조각에 하위 패널이 포함됩니다.

1. 조각 생성 대화 상자에서 다음 정보를 지정합니다.

   * **이름**: 조각의 이름입니다. 기본값은 패널의 요소 이름입니다. 필수 필드입니다.

     >[!NOTE]
     >
     >조각에 고유한 이름을 지정해야 합니다. 같은 이름의 다른 조각이 이미 있는 경우 조각을 만들 수 없습니다.

   * **제목**: 조각의 제목입니다. 기본값은 패널 제목입니다.

   * **설명**: 조각에 대한 설명입니다.

   * **태그**: 조각에 대한 태그 메타데이터입니다.

   * **대상 경로**: 조각이 저장되는 저장소 경로입니다. 경로를 지정하지 않으면 적응형 양식을 포함하는 노드 옆에 조각의 이름과 동일한 이름의 노드가 만들어집니다. 조각은 이 노드에 저장됩니다.

   * **양식 모델**: 적응형 양식의 양식 모델에 따라 이 필드에는 **XML 스키마**, **양식 서식 파일** 또는 **없음**&#x200B;이 표시됩니다. 편집할 수 없는 필드입니다.

   * **조각 모델 루트**: XSD 기반 적응형 Forms에만 나타납니다. 조각 모델의 루트를 지정합니다. 드롭다운에서 **/** 또는 XSD 복합 형식을 선택할 수 있습니다. 복잡한 유형을 조각 모델 루트로 선택하는 경우에만 다른 적응형 양식에서 조각을 재사용할 수 있습니다.
**/**&#x200B;을(를) 조각 모델 루트로 선택하면 루트의 전체 XSD 트리가 적응형 양식 데이터 모델 탭에 표시됩니다. 복합 유형 조각 모델 루트의 경우 적응형 양식 데이터 모델 탭에 선택한 복합 유형의 하위 항목만 표시됩니다.

   * **XSD 참조**: XSD 기반 적응형 Forms에만 나타납니다. XML 스키마의 위치를 표시합니다.

   * **XDP Ref**: XDP 기반 적응형 Forms에만 나타납니다. XDP 양식 템플릿의 위치를 표시합니다.

   ![조각 저장](assets/save-fragment.png)

   조각으로 저장 대화 상자

1. **확인**&#x200B;을 클릭합니다.

   패널은 저장소의 지정된 위치 또는 기본 위치에 저장됩니다. 적응형 양식에서 패널은 조각의 스냅샷으로 대체됩니다. 아래 그림과 같이 일반 정보 패널과 해당 하위 패널인 개인 정보 및 주소는 조각으로 저장됩니다.

   조각을 편집하려면 패널 도구 모음에서 **[!UICONTROL 에셋 편집]**&#x200B;을 클릭합니다. 조각이 편집 모드의 새 탭이나 창에서 열립니다.

   ![조각 편집](assets/edit-fragment.png)

## 조각 작업 {#working-with-fragments}

### 조각 모양 구성 {#configure-fragment-appearance}

적응형 Forms에 삽입하는 조각은 자리 표시자 이미지로 표시됩니다. 자리 표시자는 조각에 최대 10개의 하위 패널 제목을 표시합니다. 자리 표시자 이미지 대신 전체 조각을 표시하도록 [!DNL AEM Forms]을(를) 구성할 수 있습니다.

양식의 전체 조각을 표시하려면 다음 단계를 수행하십시오.

1. https:[*host*]:[*port*]/system/console/configMgr의 AEM 웹 콘솔 구성 페이지로 이동합니다.

1. **[!UICONTROL 적응형 양식 구성 서비스]**&#x200B;를 검색하여 클릭하여 편집 모드로 엽니다.
1. **[!UICONTROL 조각 대신 자리 표시자 사용]** 확인란을 비활성화하여 자리 표시자 이미지가 아닌 전체 조각을 표시합니다.

### 적응형 양식에 단편 삽입 {#insert-a-fragment-in-an-adaptive-form}

사용자가 만든 적응형 양식 단편은 AEM 컨텐츠 파인더의 적응형 양식 단편 탭에 나타납니다. 적응형 양식에 적응형 양식 단편을 삽입하려면:

1. 적응형 양식 단편을 삽입할 적응형 양식을 편집 모드에서 엽니다.
1. 사이드바에서 **Assets** ![에셋-브라우저](assets/assets-browser.png)을 클릭합니다. 에셋 브라우저의 드롭다운에서 **적응형 양식 조각**&#x200B;을 선택합니다.

   양식 템플릿, XML 스키마 또는 기본 등 모든 적응형 양식 조각을 표시하거나 해당 양식 모델을 기반으로 필터링을 표시하도록 선택할 수도 있습니다.

1. 적응형 양식 조각을 적응형 양식에 드래그 앤 드롭합니다.

   >[!NOTE]
   >
   >적응형 양식 내에서 작성하려면 적응형 양식 조각을 사용할 수 없습니다. 또한 JSON 기반 적응형 양식에서 XSD 기반 조각을 사용할 수 없으며 그 반대의 방법도 사용할 수 없습니다.

적응형 양식 조각은 적응형 양식에서 참조에 의해 삽입되며 독립형 적응형 양식 조각과 동기화됩니다. 즉, 적응형 양식 조각을 업데이트하면 변경 사항이 조각이 사용되는 모든 적응형 Forms에 반영됩니다.

### 적응형 양식에 단편 포함 {#embed-a-fragment-in-adaptive-form}

다음 예제 이미지와 같이 추가된 조각의 패널 도구 모음에서 **자산 포함: &lt;*fragmentName*>** 단추를 클릭하여 적응형 양식에 적응형 양식 조각을 포함하도록 선택할 수 있습니다.

![적응형 양식에 양식 단편 포함](assets/embed-fragment.png)

>[!NOTE]
>
>임베드된 조각은 더 이상 독립형 조각과 연결되지 않습니다. 적응형 양식 내에서 임베드된 조각의 구성 요소를 편집할 수 있습니다.

### 조각 내 조각 사용 {#using-fragments-within-fragments}

중첩된 적응형 양식 조각을 만들 수 있습니다. 즉, 다른 조각에서 조각을 드래그 앤 드롭할 수 있고 중첩된 조각 구조를 가질 수 있습니다.

### 조각 변경 {#change-fragments}

적응형 양식 단편 패널에 대한 구성 요소 편집 대화 상자에서 **단편 자산 선택** 속성을 사용하여 적응형 양식 단편을 다른 단편으로 바꾸거나 변경할 수 있습니다.

### 적응형 양식에서 양식 단편 여러 번 사용 {#using-form-fragment-mutiple-times-in-af}

적응형 양식에서 스키마 기반 양식 조각을 여러 번 사용하여 각 양식 조각 필드에 대해 고유하게 데이터를 저장할 수 있습니다. 예를 들어 주소 양식 조각을 사용하여 대출 신청 양식에 영구, 통신 및 현재 거주 주소에 대한 주소 세부 정보를 수집할 수 있습니다.

![적응형 양식에서 여러 조각 사용](/help/forms/assets/using-multiple-fragment-af.gif)

>[!NOTE]
>
> 적응형 양식에서 비 기반 양식 조각을 여러 번 사용하는 경우 조각 필드 간의 데이터 동기화 문제가 발생합니다. 양식 데이터 모델(FDM)에 연결되지 않은 [핵심 구성 요소 기반 양식 조각](/help/forms/adaptive-form-fragments-core-components.md)을 데이터 동기화 문제가 발생하지 않고 양식에서 여러 번 사용할 수 있습니다.

## 데이터 바인딩을 위한 조각 자동 매핑 {#auto-mapping-of-fragments-for-data-binding}

XFA 양식 템플릿 또는 XSD 복합 유형을 사용하여 적응형 양식 조각을 만들고 이 조각을 적응형 양식으로 드래그 앤 드롭하면 조각 모델 루트가 XFA 조각 또는 XSD 복합 유형에 매핑된 해당 적응형 양식 조각으로 XFA 조각 또는 XSD 복합 유형이 자동으로 대체됩니다.

구성 요소 편집 대화 상자에서 조각 에셋과 해당 바인딩을 변경할 수 있습니다.

>[!NOTE]
>
>AEM 콘텐츠 파인더의 적응형 양식 단편 라이브러리에서 바인딩된 적응형 양식 단편을 드래그 앤 드롭하고 적응형 양식 단편 패널의 구성 요소 편집 대화 상자에서 올바른 바인딩 참조를 제공할 수도 있습니다.

## 조각 관리 {#manage-fragments}

[!DNL AEM Forms] UI를 사용하여 적응형 양식 조각에 대해 여러 작업을 수행할 수 있습니다.

1. `https://[hostname]:'port'/aem/forms.html`로 이동합니다.

1. [!DNL AEM Forms] UI 도구 모음에서 **선택**&#x200B;을 클릭하고 적응형 양식 조각을 선택합니다. 도구 모음에는 선택한 적응형 양식 조각에서 수행할 수 있는 다음 작업이 표시됩니다.

<table>
 <tbody>
  <tr>
   <td><p><strong>작업</strong></p> </td>
   <td><p><strong>설명</strong></p> </td>
  </tr>
  <tr>
   <td><p>열기</p> </td>
   <td><p>선택한 적응형 양식 단편을 편집 모드로 엽니다.<br /> <br /> </p> </td>
  </tr>
  <tr>
   <td><p>속성 보기</p> </td>
   <td><p>속성 패널을 엽니다. [속성] 패널에서 속성을 확인 및 편집하고, 미리 보기를 생성하고, 선택한 조각에 대한 썸네일 이미지를 업로드할 수 있습니다. 자세한 내용은 <a href="manage-form-metadata.md" target="_blank">메타데이터 관리</a>.<br /> <br />를 참조하십시오. </p> </td>
  </tr>
  <tr>
   <td><p>복사</p> </td>
   <td><p>선택한 조각을 복사합니다. 도구 모음에 붙여넣기 단추가 나타납니다.<br /> <br /> </p> </td>
  </tr>
  <tr>
   <td><p>다운로드</p> </td>
   <td><p>선택한 조각을 다운로드합니다.<br /> <br /> </p> </td>
  </tr>
  <tr>
   <td><p>미리보기</p> </td>
   <td><p>XML 파일의 데이터를 조각과 병합하여 조각을 HTML 또는 사용자 지정 미리 보기로 미리 보는 옵션을 제공합니다. <!-- For more information, see <a href="previewing-forms.md" target="_blank">Previewing a form</a>.<br /> <br /> --></p> </td>
  </tr>
  <tr>
   <td><p>검토 시작/검토 관리</p> </td>
   <td><p>선택한 조각의 검토를 시작하고 관리할 수 있습니다. <!-- For more information, see <a href="create-reviews-forms.md" target="_blank">Creating and managing reviews</a>.<br /> <br /> </p> --> </td>
  </tr>
  <tr>
   <td><p>사전 만들기</p> </td>
   <td><p>선택한 조각을 현지화하기 위한 사전을 생성합니다. <!-- For more information, see <a href="lazy-loading-adaptive-forms.md" target="_blank">Localizing Adaptive Forms</a>.<br /> <br /> --> </p> </td>
  </tr>
  <tr>
   <td><p>Publish / 게시 취소</p> </td>
   <td><p>선택한 조각을 게시/게시 취소합니다.<br /> <br /> </p> </td>
  </tr>
  <tr>
   <td><p>삭제</p> </td>
   <td><p>선택한 조각을 삭제합니다.<br /> <br /> </p> </td>
  </tr>
 </tbody>
</table>

## 단편이 포함된 적응형 양식 현지화 {#localizing-adaptive-form-containing-fragments}

적응형 양식 단편이 포함된 적응형 양식을 현지화하려면 단편과 양식을 별도로 현지화해야 합니다. 아이디어는 조각을 한 번 현지화하고 여러 적응형 Forms에서 재사용하는 것입니다.

>[!NOTE]
>
>조각의 현지화 키는 적응형 양식의 XLIFF 파일에 표시되지 않습니다.

## 조각을 사용하여 작업할 때 기억해야 할 주요 사항 {#key-points-to-remember-when-working-with-fragments}

* 조각 이름이 고유한지 확인합니다. 같은 이름의 기존 조각이 있는 경우 조각을 만들 수 없습니다.
* XDP 기반 적응형 양식에서 패널을 다른 XDP 조각이 포함된 조각으로 저장하면 결과 조각이 자동으로 하위 XDP 조각에 바인딩됩니다. XSD 기반 적응형 양식의 경우 결과 조각이 스키마 루트에 바인딩됩니다.
* 적응형 양식 조각을 만들면 CRXDe Lite의 적응형 양식에 대한 guideContainer 노드와 유사한 조각 노드가 만들어집니다.
* 다른 FDM(양식 데이터 모델)을 사용하는 적응형 양식의 단편은 지원되지 않습니다. 예를 들어, XDP 기반 조각은 XSD 기반 적응형 양식에서 지원되지 않으며 그 반대의 경우도 마찬가지입니다.
* 적응형 양식 조각은 AEM 콘텐츠 파인더의 적응형 양식 조각 탭을 통해 사용할 수 있습니다.
* 독립형 적응형 양식 조각의 모든 표현식, 스크립트 또는 스타일은 참조로 삽입되거나 적응형 양식에 임베드될 때 유지됩니다.
* 참조에 의해 삽입된 적응형 양식 단편을 적응형 양식 내에서 편집할 수 없습니다. 편집하려면 독립 실행형 적응형 양식 조각을 편집하거나 적응형 양식에 해당 조각을 임베드하십시오.
* 적응형 양식을 게시할 때 적응형 양식에 참조로 삽입된 독립 실행형 적응형 양식 단편을 게시해야 합니다.
* 업데이트된 적응형 양식 조각을 다시 게시하면 변경 사항이 조각이 사용되는 적응형 양식의 게시된 인스턴스에 반영됩니다.
* 확인 구성 요소가 포함된 적응형 양식은 익명 사용자를 지원하지 않습니다. 또한 적응형 양식 조각에서 확인 구성 요소를 사용하는 것은 권장되지 않습니다.
* (**Mac만 해당**) 양식 단편 기능이 모든 시나리오에서 완벽하게 작동하도록 하려면 /private/etc/hosts 파일에 다음 항목을 추가합니다.
  `127.0.0.1 <Host machine>`**호스트 컴퓨터**: 배포된 Apple Mac 컴퓨터 [!DNL AEM Forms] 입니다.

<!--
## Reference Fragments {#reference-fragments}

Reference Adaptive Form Fragments that you can use to create your form are available. For more information, see [Reference Fragments](reference-adaptive-form-fragments.md).
-->

>[!MORELIKETHIS]
>
>* [핵심 구성 요소의 적응형 양식 조각](/help/forms/adaptive-form-fragments-core-components.md)
