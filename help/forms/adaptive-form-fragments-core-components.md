---
title: 적응형 양식 조각이란?
description: 적응형 Forms은 적응형 양식에서 사용할 패널 또는 필드 그룹과 같은 양식 세그먼트를 만드는 메커니즘을 제공합니다. 기존 패널을 조각으로 저장할 수도 있습니다.
topic-tags: author
keywords: 적응형 양식 단편 추가, 적응형 양식 단편, 양식 단편 만들기, 적응형 양식에 단편 추가, 단편 관리
feature: Adaptive Forms, Core Components
exl-id: 3a9ad1b7-2f6f-4ca9-a1c9-549c4238c59e
role: User, Developer
source-git-commit: a99bd181a079713571fd659ec2a04207c5eeee90
workflow-type: tm+mt
source-wordcount: '1479'
ht-degree: 12%

---

# 핵심 구성 요소를 기반으로 하는 적응형 양식에서 적응형 Forms 조각 생성 및 사용 {#adaptive-form-fragments}


| 버전 | 문서 링크 |
| -------- | ---------------------------- |
| AEM as a Cloud Service (핵심 구성 요소) | 이 문서 |
| AEM as a Cloud Service(Foundation 구성 요소) | [여기 클릭](/help/forms/adaptive-form-fragments.md) |
| AEM 6.5 | [여기 클릭](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-basic-authoring/adaptive-form-fragments.html) |

모든 양식은 특정 목적을 위해 디자인되었지만 대부분의 양식에는 이름 및 주소, 가족 세부 사항, 소득 세부 사항 등의 개인 세부 사항을 제공하는 것과 같은 몇 가지 일반적인 세그먼트가 있습니다. 양식 개발자는 새 양식을 만들 때마다 이러한 공통 세그먼트를 만들어야 합니다.

적응형 Forms은 패널 또는 필드 그룹과 같은 양식 세그먼트를 한 번만 만들어 적응형 Forms 간에 재사용할 수 있는 편리한 메커니즘을 제공합니다. 이러한 재사용 가능한 독립 세그먼트를 적응형 양식 조각이라고 합니다.

양식 조각은 여러 양식에 원활하게 통합되어 일관되고 전문적인 양식을 간편하게 만들 수 있습니다. 양식 조각의 “한번 변경하여 전체 반영” 기능을 통해 재사용성, 표준화와 브랜드 일관성을 보장합니다. 한 위치에서의 업데이트가 이러한 조각을 활용하는 모든 양식에 자동으로 전파되므로 유지 관리 가능성과 효율성이 개선됩니다.

문서에 조각을 여러 번 추가하고 해당 구성 요소의 데이터 바인딩 속성을 사용하여 다른 데이터 소스 또는 스키마에 연결할 수 있습니다. 예를 들어 영구, 통신 및 청구 주소에 동일한 주소 조각을 사용하고 이를 데이터 소스 또는 스키마의 다른 필드에 연결할 수 있습니다.

>[!NOTE]
>
> [양식 조각 구성 요소의 구성 대화 상자 및 디자인 대화 상자](https://experienceleague.adobe.com/en/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/adaptive-form-fragment)를 통해 사용자의 조각 환경을 손쉽게 사용자 지정할 수 있습니다.

## 적응형 양식 단편 만들기 {#create-a-fragment}

적응형 양식 조각을 처음부터 만들거나 기존 적응형 양식에 패널을 조각으로 저장할 수 있습니다. 양식 조각을 만들려면 다음 작업을 수행하십시오.

1. https://[*호스트 이름*]:[*포트*]/aem/forms.html에서 AEM Forms 인스턴스에 로그인합니다.
1. **만들기 > 적응형 양식 조각**&#x200B;을 클릭합니다.

   ![적응형 양식 단편 만들기](/help/forms/assets/adaptive-form-fragment.png)

1. 조각의 제목, 이름, 설명 및 태그를 지정합니다. 조각에 고유한 이름을 지정해야 합니다. 동일한 이름의 다른 조각이 존재하는 경우 조각은 생성되지 않습니다.
1. 양식 템플릿을 선택합니다. 적응형 Forms 또는 기초 구성 요소 기반 적응형 Forms 또는 적응형 에 대한 양식 조각을 만들 수 있습니다. 핵심 구성 요소 기반 양식에 대한 양식 조각을 만들려면 핵심 구성 요소 기반 템플릿을 선택합니다.

   핵심 구성 요소 기반 양식의 양식 조각을 만들 때 양식 테마 선택 옵션을 사용하여 핵심 구성 요소 기반 테마를 선택합니다.

1. 클릭하여 **양식 모델** 탭을 열고 **다음에서 선택** 드롭다운 메뉴에서 조각에 대해 다음 모델 중 하나를 선택합니다.

   ![양식 모델 탭에서 모델 유형 표시](assets/create-af-1-1.png)

   * **없음**: 양식 모델을 사용하지 않고 처음부터 조각을 만들도록 지정합니다.

     >[!NOTE]
     >
     > 적응형 Forms에서 단일 양식 조각(핵심 구성 요소 기반)을 여러 번 사용할 수 있습니다. none 기반 양식 조각과 schema 기반 양식 조각을 모두 지원합니다.

   * **스키마**: AEM Forms에 업로드된 XML 또는 JSON 스키마를 사용하여 조각을 만들도록 지정합니다. 사용 가능한 XML 또는 JSON 스키마 중에서 조각을 위한 양식 모델로 업로드하거나 선택할 수 있습니다. XML 스키마를 선택하면 **[!UICONTROL XML 스키마 복합 유형]** 드롭다운 상자에서 선택한 스키마에 있는 복합 유형을 선택하여 적응형 양식 조각을 만들 수도 있습니다. JSON 스키마를 선택하면 **[!UICONTROL JSON 스키마 정의]** 드롭다운 상자에서 선택한 스키마에 있는 스키마 정의를 선택하여 적응형 양식 조각을 만들 수도 있습니다.
   * **양식 데이터 모델**: FDM(양식 데이터 모델)을 사용하여 조각을 만들도록 지정합니다. FDM(양식 데이터 모델)의 한 데이터 모델 객체만 기반으로 적응형 양식 조각을 생성할 수 있습니다. 양식 데이터 모델(FDM) 정의 드롭다운을 확장합니다. 지정된 양식 데이터 모델(FDM)의 모든 데이터 모델 객체를 나열합니다. 목록에서 데이터 모델 개체를 선택합니다.

   ![양식 데이터 모델(FDM)](assets/create-af-3.png)

1. **만들기**&#x200B;를 클릭한 다음 **열기**&#x200B;를 클릭하여 기본 템플릿으로 편집 모드에서 조각을 엽니다. 편집 모드에서 모든 적응형 양식 구성 요소를 조각에 추가할 수 있습니다.

<!-- For information about Adaptive Form components, see [Introduction to authoring Adaptive Forms](../../forms/using/introduction-forms-authoring.md). --> 또한 조각에 대한 양식 모델로 XML 스키마를 선택한 경우 양식 모델 계층을 표시하는 새 탭이 콘텐츠 파인더에 나타납니다. 양식 모델 요소를 조각으로 드래그 앤 드롭할 수 있습니다. <!--The added form-model elements get converted into form components while retaining the original properties from the associated XDP or XSD. -->

스키마 또는 양식 데이터 모델(FDM)을 기반으로 하는 적응형 양식 조각이 생성되면 양식 데이터 모델(FDM) 또는 스키마 요소가 적응형 양식 편집기에 있는 콘텐츠 브라우저의 데이터 소스 탭에 나타납니다. 양식 모델 요소를 조각에 드래그 앤 드롭할 수 있습니다. 추가된 양식 모델 요소는 연결된 스키마의 원래 속성을 유지하면서 양식 구성 요소로 변환됩니다.


## 적응형 양식에 조각 추가 {#insert-a-fragment-in-an-adaptive-form}

적응형 양식에 적응형 양식 조각을 추가하려면 다음 작업을 수행하십시오.

1. 편집 모드에서 적응형 양식을 엽니다.
1. **적응형 양식 조각** 구성 요소를 양식에 추가하십시오.
1. **적응형 양식 조각** 구성 요소의 구성 대화 상자를 엽니다.
1. **기본** 탭에서 **조각 참조**&#x200B;를 선택합니다. 양식의 모델에 따라 양식에 사용할 수 있는 모든 적응형 Forms 조각이 표시됩니다.

1. 적응형 양식의 **적응형 양식 단편** 구성 요소에서 적응형 양식 단편을 선택하십시오.

   ![적응형 양식 단편 옵션 선택](/help/forms/assets/adaptive-form-fragment-basic.png)

<!-- >[!NOTE]
   >
   >The Adaptive Form fragment is not enabled for authoring from within the Adaptive Form. Moreover, you cannot use an XSD-based fragment in a JSON-based Adaptive Form and the opposite way. -->

적응형 양식 조각은 적응형 양식을 참조하여 추가되고 독립형 적응형 양식 조각과 동기화된 상태로 유지됩니다. 이는 적응형 양식 조각에 대한 모든 수정 사항이 조각이 적응형 Forms 내에 통합된 모든 인스턴스에 미러링됨을 의미합니다.

<!--### Embed a fragment in Adaptive Form {#embed-a-fragment-in-adaptive-form}

You can choose to embed an Adaptive Form fragment in an Adaptive Form by clicking the ![Embed](assets/Smock_Import_18_N.svg) icon the panel toolbar of the added fragment

The embedded fragment is no longer linked with the standalone fragment. You can edit the components in the embedded fragment from within the Adaptive Form.-->

<!-- 
## Configure fragment appearance {#configure-fragment-appearance}

Any fragment you insert in Adaptive Forms appears as a placeholder image. The placeholder displays titles of up to a maximum of ten child panels in the fragment. You can configure AEM Forms to show the complete fragment instead of the placeholder image.

Perform the following steps to show complete fragments in forms:

1. Go to AEM web console configuration page at https:[*host*]:[*port*]/system/console/configMgr.

1. Search and click **[!UICONTROL Adaptive Form and Interactive Communication Web Channel Configuration]** to open it in edit mode.
1. Disable **[!UICONTROL Enable Placeholder in place of Fragment]** checkbox to show complete fragments rather than the placeholder image.

-->

### 조각 내 조각 사용 {#using-fragments-within-fragments}

중첩된 적응형 양식 조각을 만들 수 있습니다. 즉, 다른 조각에 조각을 추가할 수 있고 중첩된 조각 구조를 가질 수 있습니다.

### 적응형 양식에서 양식 단편 여러 번 사용 {#using-form-fragment-mutiple-times-in-af}

적응형 양식에서 없음 기반 및 스키마 기반 양식 조각을 여러 번 사용하여 각 양식 조각 필드에 대해 고유하게 데이터를 저장할 수 있습니다. 예를 들어 주소 양식 조각을 사용하여 대출 신청 양식에 영구, 통신 및 현재 거주 주소에 대한 주소 세부 정보를 수집할 수 있습니다.

![적응형 양식에서 여러 조각 사용](/help/forms/assets/using-multiple-fragment-af.gif)

## 적응형 양식의 조각에 대한 자동 매핑 지원

JSON 스키마 정의를 기반으로 적응형 양식 조각을 만들면 동일한 스키마에서 만든 양식에서 자동으로 재사용할 수 있습니다.
적응형 양식 조각의 JSON 스키마 정의 매핑과 일치하는 스키마 객체 또는 중첩된 객체를 드래그 앤 드롭하면 객체가 일치하는 적응형 양식 조각으로 대체됩니다. 양식에서 개별 필드가 있는 패널을 추가하는 대신 매핑된 적응형 양식 조각을 삽입합니다.

![조각 끌어다 놓기](/help/forms/assets/fragment.png)

AEM 컨텐츠 파인더의 적응형 양식 단편 라이브러리에서 바인딩된 적응형 양식 단편을 드래그 앤 드롭하고 적응형 양식 단편 패널의 구성 요소 편집 대화 상자에서 올바른 바인딩 참조를 제공할 수도 있습니다.

## 조각 관리 {#manage-fragments}

AEM Forms UI를 사용하여 적응형 양식 조각에 대해 여러 작업을 수행할 수 있습니다.

1. `https://[hostname]/aem/forms.html`로 이동합니다.

1. AEM Forms UI 도구 모음에서 **선택**&#x200B;을 클릭하고 적응형 양식 조각을 선택합니다. 도구 모음에는 선택한 적응형 양식 조각에서 수행할 수 있는 다음 작업이 표시됩니다.

<table>
 <tbody>
  <tr>
   <td><p><strong>작업</strong></p> </td>
   <td><p><strong>설명</strong></p> </td>
  </tr>
  <tr>
   <td><p>편집</p> </td>
   <td><p>선택한 적응형 양식 단편을 편집 모드로 엽니다.<br /> <br /> </p> </td>
  </tr>
   <tr>
   <td><p>미리보기</p> </td>
   <td><p>XML 파일의 데이터를 조각과 병합하여 조각을 HTML 또는 사용자 지정 미리 보기로 미리 볼 수 있는 옵션을 제공합니다. 자세한 내용은 <a>양식 미리 보기</a>.<br /> <br />를 참조하세요. </p> </td>
  </tr>
  <tr>
   <td><p>다운로드</p> </td>
   <td><p>선택한 조각을 다운로드합니다.<br /> <br /> </p> </td>
  </tr>
  <tr>
   <td><p>검토 시작/검토 관리</p> </td>
   <td><p>선택한 조각의 검토를 시작하고 관리할 수 있습니다. 자세한 내용은 <a>리뷰 만들기 및 관리</a>를 참조하십시오.<br /> <br /> </p> </td>
  </tr>
  <tr>
   <td><p>사전 추가</p> </td>
   <td><p>선택한 조각을 현지화하기 위한 사전을 생성합니다. 자세한 내용은 <a>적응형 Forms 지역화</a>.<br /> <br />을(를) 참조하십시오. </p> </td>
  </tr>
  <tr>
   <td><p>게시/게시 취소</p> </td>
   <td><p>선택한 조각을 게시/게시 취소합니다.<br /> <br /> </p> </td>
  </tr>
  <tr>
   <td><p>삭제</p> </td>
   <td><p>선택한 조각을 삭제합니다.<br /> <br /> </p> </td>
  </tr>
 </tbody>
</table>

## 조각을 사용하여 작업할 때 기억해야 할 주요 사항 {#key-points-to-remember-when-working-with-fragments}

* 조각 이름이 고유한지 확인하십시오. 동일한 이름의 조각이 이미 있는 경우 조각을 만들 수 없습니다.
* 독립형 적응형 양식 조각의 모든 표현식, 스크립트 또는 스타일은 참조로 삽입되거나 적응형 양식에 임베드될 때 유지됩니다.
* 참조에 의해 삽입된 적응형 양식 단편을 적응형 양식 내에서 편집할 수 없습니다. 편집하려면 독립 실행형 적응형 양식 조각을 수정하십시오.
* 적응형 양식을 게시할 때 적응형 양식에 참조로 삽입된 독립 실행형 적응형 양식 조각을 게시해야 합니다.
* 업데이트된 적응형 양식 조각을 다시 게시하면 변경 사항이 조각이 사용되는 적응형 양식의 게시된 인스턴스에 반영됩니다.
* 확인 구성 요소가 포함된 적응형 양식은 익명 사용자를 지원하지 않습니다. 또한 적응형 양식 조각에서 확인 구성 요소를 사용하는 것은 권장되지 않습니다.

## 참조 조각 {#reference-fragments}

양식을 만드는 데 사용할 수 있는 적응형 양식 조각을 참조할 수 있습니다.
<!-- For more information, see [Reference Fragments](../../forms/using/reference-adaptive-form-fragments.md). -->



## 추가 참조 {#see-also}

{{see-also}}