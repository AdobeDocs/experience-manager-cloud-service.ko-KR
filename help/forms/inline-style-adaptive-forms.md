---
title: 적응형 양식 구성 요소에 인라인 스타일을 적용하는 방법
description: 적응형 양식에 사용자 지정 스타일을 적용할 수 있지만 적응형 양식의 개별 구성 요소에 인라인 CSS 속성을 적용할 수도 있습니다. 적응형 양식 구성 요소에 인라인 스타일을 적용하는 방법을 알아봅니다. 텍스트 필드 구성 요소에 인라인 스타일을 적용하는 예를 사용하여 심층적인 방법을 살펴봅니다.
feature: Adaptive Forms
role: User
level: Intermediate
exl-id: 25adabfb-ff19-4cb2-aef5-0a8086d2e552
source-git-commit: 7163eb2551f5e644f6d42287a523a7dfc626c1c4
workflow-type: tm+mt
source-wordcount: '717'
ht-degree: 2%

---

# 적응형 양식 구성 요소의 인라인 스타일 {#inline-styling-of-adaptive-form-components}

스타일을 사용하여 지정하여 적응형 양식의 전체 모양과 스타일을 정의할 수 있습니다 [테마 편집기](themes.md). 또한 개별 적응형 양식 구성 요소에 인라인 CSS 스타일을 적용하고 변경 사항을 즉시 미리 볼 수 있습니다. 인라인 스타일은 테마에 제공된 스타일을 재정의합니다.

## 인라인 CSS 속성 적용 {#apply-inline-css-properties}

구성 요소에 인라인 스타일을 추가하려면 다음을 수행하십시오.

1. 양식 편집기에서 양식을 열고 모드를 스타일 지정 모드로 변경합니다. 모드를 스타일 지정 모드로 변경하려면 페이지 도구 모음에서 를 누릅니다 ![캔버스 드롭다운](assets/Smock_ChevronDown.svg) > **[!UICONTROL 스타일]**.
1. 페이지에서 구성 요소를 선택하고 편집 단추를 누릅니다 ![편집 단추](assets/edit.svg). 사이드바에서 열리는 스타일 지정 속성입니다.

   사이드바의 양식 계층 트리에서 구성 요소를 선택할 수도 있습니다. 양식 계층 트리는 사이드바의 양식 개체로 사용할 수 있습니다.

   에서 [!UICONTROL 스타일] 모드에서는 양식 객체 아래에 나열된 구성 요소를 볼 수 있습니다. 그러나 사이드바의 양식 객체 목록에는 필드 및 패널과 같은 구성 요소가 나열됩니다. 필드 및 패널은 텍스트 상자 및 라디오 단추와 같은 구성 요소를 포함할 수 있는 일반적인 구성 요소입니다.

   사이드바에서 구성 요소를 선택하면 나열된 모든 하위 구성 요소와 선택한 구성 요소의 속성이 표시됩니다. 특정 하위 구성 요소를 선택하고 스타일을 지정할 수 있습니다.

1. 사이드바의 탭을 클릭하여 CSS 속성을 지정합니다. 다음과 같은 속성을 지정할 수 있습니다.

   * [!UICONTROL Dimension 및 위치] (표시 설정, 패딩, 높이, 너비, 여백, 위치, z-색인, 부동, 지우기, 오버플로)
   * [!UICONTROL 텍스트] (글꼴 패밀리, 두께, 색상, 크기, 선 높이 및 정렬)
   * [!UICONTROL 배경] (이미지 및 그라데이션, 배경색)
   * [!UICONTROL 테두리] (너비, 스타일, 색상, 반경)
   * [!UICONTROL 효과] (그림자, 불투명도)
   * [!UICONTROL 고급] (구성 요소에 대한 사용자 지정 CSS를 작성할 수 있음)

1. 마찬가지로 구성 요소의 다른 부분(예: [!UICONTROL 위젯], [!UICONTROL 캡션], 및 [!UICONTROL 도움말].
1. 탭 **[!UICONTROL 완료]** 변경 사항을 확인하려면 **[!UICONTROL 취소]** 변경 사항을 취소하려면

## 예: 필드 구성 요소의 인라인 스타일 {#example-inline-styles-for-a-field-component}

다음 이미지는 인라인 스타일이 적용되기 전후의 텍스트 필드를 나타냅니다.

![인라인 스타일이 적용되기 전의 텍스트 상자 구성 요소](assets/no-style.png)

인라인 스타일 속성을 적용하기 전에 텍스트 상자 구성 요소

다음 CSS 속성을 적용한 후 다음 이미지에 표시된 텍스트 상자 스타일의 변경 사항에 주목하십시오.

<table>
 <tbody>
  <tr>
   <td><p>선택기</p> </td>
   <td><p>CSS 속성</p> </td>
   <td><p>값</p> </td>
   <td><p>효과</p> </td>
  </tr>
  <tr>
   <td><p>필드</p> </td>
   <td><p>테두리</p> </td>
   <td><p>테두리 너비 = 2px</p> <p>테두리 스타일=단색</p> <p>테두리 색상=#1111</p> </td>
   <td><p>필드 주위에 검정 2px 너비의 테두리를 만듭니다</p> </td>
  </tr>
  <tr>
   <td><p>텍스트 상자</p> </td>
   <td><p>background-color</p> </td>
   <td><p>#6495ED</p> </td>
   <td><p>배경색을 CornflowerBlue(#6495ED)으로 변경합니다</p> <p>참고: 값 필드에 색상 이름 또는 16진수 코드를 지정할 수 있습니다.</p> </td>
  </tr>
  <tr>
   <td><p>레이블</p> </td>
   <td><p>Dimension 및 위치 &gt; 너비</p> </td>
   <td><p>100px</p> </td>
   <td><p>레이블의 너비를 100px로 수정</p> </td>
  </tr>
  <tr>
   <td>필드 도움말 아이콘</td>
   <td>텍스트 &gt; 글꼴 색상</td>
   <td>#2ECC40</td>
   <td>도움말 아이콘 화면의 색상을 변경합니다.</td>
  </tr>
  <tr>
   <td><p>긴 설명</p> </td>
   <td><p>text-align</p> </td>
   <td><p>가운데</p> </td>
   <td><p>도움말을 가운데로 가져올 긴 설명을 맞춥니다.</p> </td>
  </tr>
 </tbody>
</table>

![인라인 스타일이 적용된 후 텍스트 상자 스타일](assets/applied-style.png)

인라인 스타일 속성을 적용한 후 텍스트 상자 구성 요소

위의 단계에 따라 패널, 제출 단추 및 라디오 단추와 같은 기타 구성 요소를 선택하고 스타일을 지정할 수 있습니다.

>[!NOTE]
>
>스타일 지정 속성은 선택한 구성 요소에 따라 다릅니다.

## 스타일 복사 및 붙여넣기 {#copy-paste-styles}

한 구성 요소의 스타일을 적응형 양식의 다른 구성 요소로 복사하여 붙여넣을 수도 있습니다. 에서 **[!UICONTROL 스타일]** 모드에서 구성 요소를 탭하고 복사 아이콘을 탭합니다 ![복사](assets/property-copy-icon.svg).

같은 유형의 다른 구성 요소를 탭하고 붙여넣기 아이콘을 탭합니다 ![복사](assets/Smock_Paste_18_N.svg) 복사한 스타일을 붙여넣습니다. 스타일 지우기 아이콘을 탭할 수도 있습니다 ![복사](assets/clear-style-icon.svg) 적용된 스타일을 지우려면

## 구성 요소의 다른 상태에 대한 스타일 설정 {#set-styles-for-states}

구성 요소 유형의 여러 상태에 대한 스타일을 설정할 수 있습니다. 다양한 상태는 다음과 같습니다. [!UICONTROL 포커스], [!UICONTROL 비활성화됨], [!UICONTROL 마우스로 가리키기], [!UICONTROL 오류], [!UICONTROL 성공], 및 [!UICONTROL 필수].

구성 요소 상태에 대한 스타일링을 정의하려면

1. 에서 **[!UICONTROL 스타일]** 모드에서 구성 요소를 탭하고 편집 아이콘을 탭합니다 ![편집](assets/Smock_Edit_18_N.svg).

1. 구성 요소의 상태를 **[!UICONTROL 주/도]** 드롭다운 목록.

   ![상태 선택](assets/select-state.png)

1. 구성 요소의 선택한 상태에 대한 스타일을 정의하고 탭합니다 ![저장](assets/save_icon.svg) 속성을 저장합니다.

성공 및 오류 상태를 시뮬레이션할 수도 있습니다. 확장 아이콘을 탭하여 **[!UICONTROL 성공 시뮬레이션]** 및 **[!UICONTROL 오류 시뮬레이션]** 옵션.

![상태 시뮬레이션](assets/simulate-states.png)
