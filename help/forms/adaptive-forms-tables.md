---
title: 적응형 양식의 표
seo-title: Tables in adaptive forms
description: AEM Forms의 표 구성 요소를 사용하면 모바일 레이아웃에 응답하는 적응형 양식으로 표를 만들 수 있고 XDP 표 구성 요소를 사용할 수도 있습니다.
seo-description: The Table component in AEM Forms lets you create tables in adaptive forms that are responsive to mobile layouts, and also allows using XDP table components.
products: SG_EXPERIENCEMANAGER/Cloud Service/FORMS
feature: Adaptive Forms
source-git-commit: c9cfaff7f155dc85b2f2ee4e2851e3eb59f5871d
workflow-type: tm+mt
source-wordcount: '2418'
ht-degree: 0%

---

# 적응형 양식의 표 {#tables-in-adaptive-forms}

표를 사용하는 것은 복잡한 데이터를 효과적으로 단순화하고 체계적으로 제공하는 방법입니다. 사용자가 정보를 쉽게 식별하고 행과 열을 순서대로 배열하여 입력을 제공하는 데 도움이 됩니다. 금융 서비스 및 정부 조직의 대부분의 양식에서는 숫자를 지정하고 계산을 수행하기 위해 큰 데이터 테이블이 필요합니다.

AEM Forms은 사이드바의 구성 요소 브라우저에서 적응형 양식으로 표를 만들 수 있는 표 구성 요소를 제공합니다. 이 기능이 제공하는 몇 가지 주요 기능은 다음과 같습니다.

* 모바일 장치의 응답형 레이아웃
* 구성 가능한 행 및 열
* 런타임 시 행의 동적 추가 및 삭제
* 셀 결합 또는 병합 및 분할
* 화면 판독기에서 액세스 가능
* CSS를 사용한 사용자 지정 레이아웃
* XDP 테이블 구성 요소와 호환 및 매핑
* XSD 복합 형식 요소를 사용하여 행 또는 셀 추가 지원
* XML 파일에서 데이터 병합

## 표 만들기 {#create-a-table}

테이블을 만들려면 적응형 양식의 사이드 킥에 있는 구성 요소 브라우저에서 표 구성 요소를 드래그하여 놓습니다. 기본적으로 표에는 머리글 행을 포함하여 두 개의 열과 세 개의 행이 포함되어 있습니다.

![AEM 사이드바의 표 구성 요소](assets/sidebar-tables.png)

### 헤더 및 본문 셀 정보 {#about-header-and-body-cells}

헤더 셀은 텍스트 필드입니다. 헤더의 레이블을 변경하려면 헤더 셀을 마우스 오른쪽 단추로 클릭하고 를 클릭합니다. **편집**. 편집 대화 상자에서 **값** 필드를 입력하고 **확인**.

본문 셀은 기본적으로 텍스트 상자입니다. 본문 셀을 숫자 상자, 날짜 선택기 또는 드롭다운 목록과 같이 사이드 킥에서 사용할 수 있는 다른 적응형 양식 구성 요소로 바꿀 수 있습니다.

예를 들어, 다음 표의 첫 번째 본문 행에는 텍스트 상자, 날짜 선택기 및 드롭다운 목록 구성 요소가 셀로 포함되어 있습니다.

![row-cell-types](assets/row-cell-types.png)

병합할 셀을 선택하고 마우스 오른쪽 단추를 클릭한 다음 을 선택하여 둘 이상의 본문 셀을 병합할 수 있습니다 **병합**. 병합된 셀을 마우스 오른쪽 단추로 클릭하고 선택하여 분할할 수도 있습니다 **셀 분할**.

### 행 및 열 추가, 삭제, 이동 {#add-delete-move-rows-and-columns}

행이나 열을 추가 및 삭제하고 테이블에서 행을 위아래로 이동할 수 있습니다.

#### 행 추가, 삭제 또는 이동

행을 추가, 삭제 또는 이동하려면 행의 셀을 누릅니다. 컨텐츠 브라우저 열기 ![컨텐츠 브라우저](/help/forms/assets/Smock_Layers_18_N.svg) 해당 행을 선택하면 선택한 행이 강조 표시되고, 이 도구 모음 옵션은 행을 추가, 삭제 또는 이동할 수 있는 위쪽 또는 아래쪽의 도구 모음 옵션을 사용합니다.
* 다음 **[!UICONTROL 위로 이동]** 및 **[!UICONTROL 아래로 이동]** 작업은 선택한 행을 위아래로 이동합니다.

* 다음 **[!UICONTROL 열 추가]** 선택한 행 아래에 행이 추가됩니다.

* 다음 **[!UICONTROL 열 삭제]** 선택한 행을 삭제합니다.

![add-delete-move-row-column](assets/add-delete-move-row.png)

행을 두 번 클릭하여 이름, 바인딩 참조, 반복 설정, CSS 클래스와 같은 행의 속성을 구성합니다.
![add-delete-move-row-column](assets/row-properties-image.png)


#### 열 추가 또는 삭제

열을 추가하거나 삭제하려면, 헤더 섹션에서 텍스트 셀을 클릭하면, 열을 추가 또는 삭제하는 옵션이 있는 도구 모음이 열립니다.

![add-delete-move-row-column](assets/add-delet-column.png)

>[!NOTE]
>
>테이블에 행 수를 추가할 수 있지만 추가할 수 있는 최대 열 수는 6개입니다. 또한 테이블에서 머리글 행을 삭제할 수 없습니다.

### 테이블 설명 추가 {#add-table-description}

표의 설명을 추가하여 화면 판독기에서 해석하고 읽을 수 있도록 정보를 구성하는 방법을 설명할 수 있습니다. 설명을 추가하려면:

1. 표를 선택하고 탭합니다 ![cmppr](assets/cmppr.png) 를 클릭하여 사이드바에서 해당 속성을 확인합니다.
1. 액세스 가능성 탭에서 요약을 지정합니다.
1. 클릭 **완료**.

### 테이블의 열 정렬 {#sortcolumnstable}

적응형 양식의 표에 있는 열을 기준으로 데이터를 정렬할 수 있습니다. 열의 값은 오름차순 또는 내림차순으로 정렬할 수 있습니다.

다음 항목이 포함된 테이블 열에 정렬을 적용할 수 있습니다.

* 정적 텍스트
* 데이터 모델 개체 속성
* 정적 텍스트와 데이터 모델 개체 속성의 조합

테이블 열에 정렬을 적용하려면 테이블 열 셀에 다음 구성 요소 중 하나가 있어야 합니다. 숫자 상자, 숫자 문자열, 날짜 입력 필드, 날짜 선택기, 텍스트 또는 텍스트 상자

정렬을 활성화하려면

1. 표를 선택하고 탭합니다 ![configure_icon](assets/configure_icon.png) (구성). 또한 **컨텐츠** 대화형 커뮤니케이션의 사이드 킥에 있는 브라우저.
1. 선택 **정렬 활성화**.
1. 탭 ![done_icon](assets/done_icon.png) 표 속성을 저장하려면 열 헤더에서 위쪽 및 아래쪽 화살표로 정렬하는 아이콘은 정렬이 활성화되었음을 나타냅니다.

   ![정렬 활성화](assets/enable_sorting_new.png)

1. 로 전환 **미리 보기** 모드를 사용하여 출력을 봅니다. 표는 테이블의 첫 번째 열을 기준으로 자동으로 정렬됩니다.
1. 열 헤더를 클릭하여 열을 기준으로 값을 정렬합니다.

   위쪽 화살표가 있는 열 헤더는 테이블이 해당 열을 기준으로 정렬되었음을 나타냅니다. 또한 열의 값은 오름차순으로 표시됩니다.

   ![오름차순으로 정렬](assets/sorting_ascending_new.png)

   마찬가지로, 아래쪽 화살표가 있는 열 헤더는 열의 값이 내림차순으로 표시됨을 나타냅니다.

   또한 **미리 보기** 모드를 선택하고 열 헤더를 다시 클릭하여 열 값을 정렬합니다.

## 표의 열 너비 설정 {#set-column-width}

다음 단계를 실행하여 테이블의 열 너비를 설정합니다.

1. 에서 **[!UICONTROL 컨텐츠]** 탭에서 **[!UICONTROL 표]** 구성 요소를 선택하고 구성 (![구성](assets/configure-icon.svg)) 아이콘을 클릭합니다.

1.쉼표로 구분된 값 목록을 **[!UICONTROL 열 너비]** 필드에 추가하여 표에 있는 각 열의 비율을 지정합니다. 예를 들어, 3개의 열이 포함된 테이블의 경우 **[!UICONTROL 열 너비]** 필드의 경우 첫 번째 열에 2/12, 두 번째 열에 4/12, 세 번째 열에 6/12 열 너비가 설정됩니다. 첫 번째 열의 너비는 표 너비의 1/6을 나타내므로 2/12. 마찬가지로 4/12 두 번째 열 너비를 표 너비의 1/3으로 설정하고 세 번째 열 너비를 표 너비의 반으로 6/12.

## 표 스타일 구성 {#configure}

페이지 도구 모음에서 스타일 모드를 사용하여 표의 스타일을 정의할 수 있습니다. 스타일 모드로 전환하고 테이블 스타일을 편집하려면 다음 단계를 수행하십시오

1. 페이지 도구 모음의 미리 보기 전에 ![캔버스 드롭다운](assets/canvas-drop-down.png) > **스타일**.

1. 사이드바에서 표를 선택하고 편집 단추를 누릅니다 ![편집 단추](assets/edit-button.png).
사이드바에서 스타일 지정 속성을 볼 수 있습니다.

![테이블의 스타일 지정 속성](assets/style-table.png)

>[!NOTE]
>
>의 값을 변경하여 머리글 및 본문 행의 색상 테마를 변경할 수 있습니다 [LESS 변수](https://lesscss.org//). 자세한 내용은 [AEM Forms의 테마](/help/forms/themes.md).

## 동적으로 행 추가 또는 삭제 {#add-or-delete-a-row-dynamically}

표는 런타임 시 행을 동적으로 추가하거나 삭제할 수 있도록 즉시 지원합니다.

1. 표 행을 선택하고 탭합니다 ![cmppr](assets/cmppr.png).
1. 반복 설정 탭에서 최소 및 최대 개수를 지정하여 테이블의 행 수를 제한합니다.
1. 클릭 **완료**.

런타임 또는 미리 보면 **+** 및 ![삭제 단추](/help/forms/assets/Smock_Delete.svg) 행을 추가하거나 삭제할 단추

![add-delete-rows-dynamically](assets/add-delete-layout.png)

>[!NOTE]
>
>표의 왼쪽 모바일 레이아웃에서 행을 동적으로 추가하거나 삭제하는 것은 헤더에서 지원되지 않습니다.

## 테이블의 표현식 {#expressions-in-a-table}

적응형 양식의 표를 사용하면 JavaScript에서 표현식을 작성하여 표 또는 행 표시 또는 숨기기, 모든 숫자 추가 및 셀에서 합계 표시, 셀 활성화 또는 비활성화, 사용자 입력 확인 등과 같은 동작을 유도할 수 있습니다. 이러한 표현식은 적응형 양식 스크립팅 모델 API를 사용합니다.

테이블과 행은 표현식에서 반환된 값을 기반으로 가시성을 제어하는 가시성 표현식만 지원하는 반면 셀에서는 다음 표현식을 지원합니다.

* **초기화 스크립트:** 필드의 초기화에 대한 작업을 수행합니다.
* **값 커밋 스크립트:** 필드의 값이 변경된 후에 양식의 구성 요소를 변경하려면 다음을 수행하십시오.

>[!NOTE]
>
>XFA 변경/종료 스크립트도 동일한 필드에 적용되는 경우 XFA 변경/종료 스크립트는 값 커밋 스크립트 전에 실행됩니다.

* **표현식 계산**: 를 눌러 필드의 값을 자동으로 계산합니다.
* **유효성 검사 표현식**: 필드의 유효성을 검사하려면
* **표현식 액세스**: 필드를 활성화/비활성화합니다.
* **가시성 표현식**: 필드 및 패널의 가시성을 제어하기 위해

테이블 또는 행의 가시성 표현식은 해당 편집 구성 요소 대화 상자의 패널 속성 탭에서 정의할 수 있습니다. 셀의 표현식은 해당 편집 구성 요소 대화 상자의 스크립트 탭에서 정의할 수 있습니다.

적응형 양식 클래스, 이벤트, 개체 및 공용 API의 전체 목록은 다음을 참조하십시오 [적응형 양식에 대한 JavaScript 라이브러리 API 참조](https://helpx.adobe.com/experience-manager/6-5/forms/javascript-api/index.html).

## 모바일 레이아웃 {#mobile-layouts}

적응형 양식의 표는 유동적이고 반응형 레이아웃으로 인해 탁월한 경험 모바일 장치를 제공합니다. AEM Forms에서는 표에 대한 두 가지 유형의 모바일 레이아웃, 즉 왼쪽 및 축소 가능한 열을 제공합니다.

테이블에 대한 구성 요소 편집 대화 상자의 스타일 지정 탭에서 표에 대한 모바일 레이아웃을 구성할 수 있습니다.

### 왼쪽의 머리글 {#headers-on-left}

왼쪽 레이아웃의 헤더 에서는 테이블의 헤더가 왼쪽에 배치되고 헤더에 대해 하나의 셀만 표시됩니다. 이 레이아웃의 각 행은 개별 섹션으로 표시됩니다. 다음 이미지는 데스크탑의 표를 모바일 장치의 테이블과 비교합니다.

![데스크탑 보기](assets/desktopview_new.png)

왼쪽 레이아웃에 머리글이 있는 테이블의 데스크탑 보기

![왼쪽의 머리글](assets/headersontheleft_new.png)

왼쪽 레이아웃에 헤더가 있는 테이블의 모바일 보기

### 축소 가능한 열 레이아웃 {#collapsible-columns-layout}

축소 가능한 열 레이아웃에서 테이블의 열은 장치 크기에 따라 하나 또는 두 개의 열을 표시하도록 축소되고 다른 열은 축소됩니다. 축소/확장 아이콘을 클릭하여 테이블의 다른 열을 볼 수 있습니다.

>[!NOTE]
>
>축소 가능한 열 레이아웃은 모바일 장치에 맞게 최적화되어 있지만 사용 가능한 너비가 테이블의 모든 열을 표시하기에 충분하지 않은 경우 데스크톱에서도 작동합니다.

다음 이미지는 축소된 열과 확장된 열이 있는 장치에서 표가 표시되는 방식을 비교합니다.

![축소 열](assets/collapsed-column.png)

모바일 장치에 두 개의 열만 표시되는 테이블의 축소된 열

![축소 가능_열](assets/collapsible_column.png)

모바일 장치에서 테이블의 확장된 열

## 테이블의 데이터 병합 {#merge-data-in-a-table}

적응형 양식의 표를 사용하면 XML 파일의 데이터를 사용하여 런타임 시 테이블을 채울 수 있습니다. 데이터 XML 파일은 AEM Forms 서버가 실행되는 시스템의 로컬 파일 시스템 또는 CRX 저장소에 있을 수 있습니다.

XML 파일의 데이터로 채울 다음 은행 거래 요약 테이블을 예로 들어 보겠습니다.

![데이터 병합 테이블](assets/data-merge-table.png)

이 예제에서 요소 이름 속성은 다음과 같습니다.

* 행은 다음과 같습니다. **행1**
* 트랜잭션 날짜의 본문 셀은 다음과 같습니다. **tableItem1**
* 설명 아래의 본문 셀은 다음과 같습니다. **tableItem2**
* 트랜잭션 유형 아래의 본문 셀은 다음과 같습니다. **유형**
* USD의 금액 아래의 본문 셀은 다음과 같습니다 **tableItem3**

다음 형식의 데이터를 포함하는 XML 파일입니다.

```xml
<?xml version="1.0" encoding="UTF-8"?><afData>
  <afUnboundData>
    <data>
 <typeSelect>0</typeSelect>
 <Row1>
      <tableItem1>2015-01-08</tableItem1>
      <tableItem2>Purchase laptop</tableItem2>
      <type>0</type>
      <tableItem3>12000</tableItem3>
 </Row1>
 <Row1>
      <tableItem1>2015-01-05</tableItem1>
      <tableItem2>Transport expense</tableItem2>
      <type>0</type>
      <tableItem3>120</tableItem3>
 </Row1>
 <Row1>
      <tableItem1>2014-01-08</tableItem1>
      <tableItem2>Laser printer</tableItem2>
      <type>0</type>
      <tableItem3>500</tableItem3>
 </Row1>
 <Row1>
      <tableItem1>2014-12-08</tableItem1>
      <tableItem2>Credit card payment</tableItem2>
      <type>0</type>
      <tableItem3>300</tableItem3>
 </Row1>
 <Row1>
      <tableItem1>2015-01-06</tableItem1>
      <tableItem2>Interest earnings</tableItem2>
      <type>1</type>
      <tableItem3>12000</tableItem3>
 </Row1>
 <Row1>
      <tableItem1>2015-01-05</tableItem1>
      <tableItem2>Payment from a client</tableItem2>
      <type>1</type>
      <tableItem3>500</tableItem3>
 </Row1>
 <Row1>
      <tableItem1>2015-01-08</tableItem1>
      <tableItem2>Food expense</tableItem2>
      <type>0</type>
      <tableItem3>120</tableItem3>
 </Row1>
 </data>
  </afUnboundData>
  <afBoundData>
    <data/>
  </afBoundData>
  <afBoundData/>
</afData>
```

샘플 XML에서 행의 데이터는 `<Row1>` 태그 - 테이블의 행에 대한 요소 이름입니다. 내 `<Row1>` 태그로, 각 셀의 데이터는 요소 이름에 대한 태그 내에 정의됩니다(예: ). `<tableItem1>`, `<tableItem2>`, `<tableItem3>`, 및 `<type>`.

런타임 시 이 데이터를 테이블과 병합하려면 테이블이 포함된 적응형 양식을 wcmmode가 비활성화된 절대 XML 위치로 가리켜야 합니다. 예를 들어 적응형 양식이 *https://localhost:4502/myForms/bankTransaction.html* 데이터 XML 파일은 *C:/myTransactions/bankSummary.xml*, 다음 URL에서 데이터가 있는 테이블을 볼 수 있습니다.

*https://localhost:4502/myForms/bankTransaction.html?dataRef=file:/// C:/myTransactions/bankSummary.xml&amp;wcmmode=disabled*

![데이터 병합 테이블](assets/data-merged-table.png)

## XDP 구성 요소 및 XSD 복합 형식 사용 {#use-xdp-components-and-xsd-complex-types}

XFA 양식 템플릿을 기반으로 적응형 양식을 만든 경우 AEM 컨텐츠 파인더의 데이터 모델 탭에서 XFA 요소를 사용할 수 있습니다. 테이블을 포함한 이러한 XFA 요소를 적응형 양식에 드래그하여 놓을 수 있습니다.

XFA 테이블 요소는 표 구성 요소에 매핑되고 적응형 양식에서 즉시 작동합니다. XDP 테이블의 모든 속성 및 기능은 적응형 양식으로 이동할 때 유지되며 네이티브 적응형 양식 테이블을 사용하는 것처럼 이 테이블에서 모든 작업을 수행할 수 있습니다. 예를 들어 XDP 테이블의 행이 반복 가능으로 표시된 경우 적응형 양식에서 드롭될 때도 반복됩니다.

또한 XDP 하위 양식을 끌어 놓아 테이블에 새 행을 추가할 수 있습니다. 그러나 중첩된 하위 폼을 삭제하는 것은 작동하지 않습니다.

>[!NOTE]
>
>헤더 행이 없는 XDP 테이블은 적응형 양식 테이블 구성 요소에 매핑되지 않습니다. 대신 유동 레이아웃이 있는 적응형 양식 패널 구성 요소에 매핑됩니다. 또한 XDP에서 적응형 양식에 중첩 테이블을 추가하면 외부 테이블이 내부 테이블을 유지하면서 패널로 변환됩니다.

또한 XSD 복합 형식 요소 그룹을 끌어 테이블 행을 만들 수도 있습니다. 요소를 삭제한 행 바로 아래에 새 행이 만들어집니다. XSD 복합 형식 요소를 사용하여 만든 셀에서는 XSD에 대한 바인딩 참조를 유지합니다. 요소를 셀에 드롭하여 본문 셀을 XSD 복합 형식 요소로 바꿀 수도 있습니다.

>[!NOTE]
>
>XDP 테이블 구성 요소, 하위 폼 또는 XSD 복합 형식의 요소 수는 행의 셀 수를 초과할 수 없습니다. 예를 들어 세 개의 셀만 있는 행에는 네 개의 요소를 놓을 수 없습니다. 오류가 발생합니다.
>
>요소 수가 행의 셀 수보다 적으면 새 행이 먼저 요소를 기반으로 셀을 추가한 다음 기본 셀이 추가되어 행의 나머지 셀을 채웁니다. 예를 들어 네 개의 셀이 있는 행에 세 개의 요소 그룹을 놓으면 처음 세 개의 셀이 삭제한 요소를 기반으로 하며 나머지 한 셀은 기본 테이블 셀이 됩니다.

## 주요 고려 사항 {#key-considerations}

* XSD 기반 테이블을 작성하는 동안 행을 위아래로 이동하는 경우 양식 제출 시 생성된 데이터 XML에 테이블 행의 일부 데이터 손실이 표시됩니다.
* 기본 테이블의 각 본문 셀에는 사전 정의된 요소 이름이 연결되어 있습니다. 적응형 양식에 다른 테이블을 추가하면 새 테이블의 기본 본문 셀이 첫 번째 테이블과 동일한 요소 이름을 갖게 됩니다. 이러한 시나리오에서는 양식 제출 시 생성된 데이터에 테이블 중 하나에만 있는 기본 본문 셀에 데이터가 포함됩니다. 따라서 기본 본문 셀의 요소 이름을 변경하여 테이블 간에 고유하고 데이터 손실을 방지해야 합니다.

   기본 본문 셀에만 적용할 수 있습니다. 테이블에 행 또는 열을 더 추가하면 기본값이 아닌 본문 셀에 대한 고유 요소 이름이 자동으로 생성됩니다.
