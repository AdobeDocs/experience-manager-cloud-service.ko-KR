---
title: 폴더 메타데이터 스키마
description: AEM Assets에서 자산 폴더에 대한 메타데이터 스키마를 만드는 방법 살펴보기
contentOwner: AG
translation-type: tm+mt
source-git-commit: dc5cec192a70413e0ebcc27eb5e58577079ae93b
workflow-type: tm+mt
source-wordcount: '1040'
ht-degree: 2%

---


# 폴더 메타데이터 스키마 {#folder-metadata-schema}

Adobe Experience Manager(AEM) 자산을 사용하면 폴더 속성 페이지에 표시되는 레이아웃 및 메타데이터를 정의하는 자산 폴더의 메타데이터 스키마를 생성할 수 있습니다.

## {#add-a-folder-metadata-schema-form} 폴더 메타데이터 스키마 추가

폴더 메타데이터 스키마 Forms 편집기를 사용하여 폴더의 메타데이터 스키마를 만들고 편집할 수 있습니다.

1. AEM 로고를 탭/클릭하고 **[!UICONTROL 도구]** > **[!UICONTROL 자산]** > **[!UICONTROL 폴더 메타데이터 스키마]**&#x200B;로 이동합니다.
1. 폴더 메타데이터 스키마 Forms 페이지에서 **[!UICONTROL 만들기]**&#x200B;를 탭/클릭합니다.
1. 양식의 이름을 지정하고 **[!UICONTROL 만들기]**&#x200B;를 탭/클릭합니다. 새 스키마 양식이 스키마 Forms 페이지에 나열됩니다.

## 폴더 메타데이터 스키마 양식 편집 {#edit-folder-metadata-schema-forms}

다음을 포함하는 새로 추가되거나 기존 메타데이터 스키마 양식을 편집할 수 있습니다.

* 탭
* 탭 내의 양식 항목

이러한 양식 항목을 CRX 저장소의 메타데이터 노드 내의 필드에 매핑/구성할 수 있습니다. 메타데이터 스키마 양식에 새 탭 또는 양식 항목을 추가할 수 있습니다.

1. 스키마 Forms 페이지에서 작성한 양식을 선택한 다음 도구 모음에서 **[!UICONTROL 편집]** 아이콘을 탭/클릭합니다.
1. 폴더 메타데이터 스키마 편집기 페이지에서 **[!UICONTROL +]** 아이콘을 탭/클릭하여 양식에 탭을 추가합니다. 탭의 이름을 변경하려면 기본 이름을 탭/클릭하고 **[!UICONTROL 설정]** 아래에 새 이름을 지정합니다.

   ![custom_tab](assets/custom_tab.png)

   탭을 더 추가하려면 **[!UICONTROL +]** 아이콘을 탭/클릭합니다. 탭을 삭제하려면 **[!UICONTROL X]**&#x200B;을(를) 탭/클릭합니다.

1. 활성 탭에서 **[!UICONTROL 빌드 양식]** 탭에서 하나 이상의 구성 요소를 추가합니다.

   ![adding_components](assets/adding_components.png)

   여러 탭을 만드는 경우 특정 탭을 탭/클릭하여 구성 요소를 추가합니다.

1. 구성 요소를 구성하려면 구성 요소를 선택하고 **[!UICONTROL 설정]** 탭에서 해당 속성을 수정합니다.

   필요한 경우 **[!UICONTROL 설정]** 탭에서 구성 요소를 삭제합니다.

   ![configure_properties](assets/configure_properties.png)

1. 도구 모음에서 **[!UICONTROL 저장]**&#x200B;을 탭/클릭하여 변경 내용을 저장합니다.

### 양식 {#components-to-build-forms} 작성을 위한 구성 요소

**[!UICONTROL 빌드 양식]** 탭에는 폴더 메타데이터 스키마 양식에서 사용하는 양식 항목이 나열됩니다. **[!UICONTROL 설정]** 탭에는 **[!UICONTROL 빌드 양식]** 탭에서 선택한 각 항목에 대한 속성이 표시됩니다. 다음은 **[!UICONTROL 빌드 양식]** 탭에서 사용할 수 있는 양식 항목의 목록입니다.

<table>
 <tbody>
  <tr>
   <td><p><strong>구성 요소 이름</strong></p> </td>
   <td><p><strong>설명</strong></p> </td>
  </tr>
  <tr>
   <td><p>섹션 머리글</p> </td>
   <td><p> 공통 구성 요소 목록에 대한 섹션 머리글을 추가합니다.</p> </td>
  </tr>
  <tr>
   <td><p>한 줄 텍스트</p> </td>
   <td><p> 단일 행 텍스트 속성을 추가합니다. 문자열로 저장됩니다.</p> </td>
  </tr>
  <tr>
   <td><p>다중 값 텍스트</p> </td>
   <td><p> 다중 값 텍스트 속성을 추가합니다. 문자열 배열로 저장됩니다.</p> </td>
  </tr>
  <tr>
   <td><p>번호</p> </td>
   <td><p> 숫자 구성 요소를 추가합니다.</p> </td>
  </tr>
  <tr>
   <td><p>날짜</p> </td>
   <td><p> 날짜 구성 요소를 추가합니다.</p> </td>
  </tr>
  <tr>
   <td><p>드롭다운</p> </td>
   <td><p> 드롭다운 목록을 추가합니다.</p> </td>
  </tr>
  <tr>
   <td><p>표준 태그</p> </td>
   <td><p> 태그 추가. </p> </td>
  </tr>
  <tr>
   <td><p>숨김 필드</p> </td>
   <td><p> 숨김 필드를 추가합니다. 에셋을 저장할 때 POST 매개 변수로 전송됩니다.</p> </td>
  </tr>
 </tbody>
</table>

### 양식 항목 편집 {#editing-form-items}

양식 항목의 속성을 편집하려면 구성 요소를 탭/클릭하고 **[!UICONTROL 설정]** 탭에서 다음 속성의 전체 또는 하위 집합을 편집합니다.

**[!UICONTROL 필드 레이블]**:폴더의 속성 페이지에 표시되는 메타데이터 속성의 이름입니다.

**[!UICONTROL 속성에 매핑]**:이 속성은 CRX 저장소의 폴더 노드의 상대 경로를 지정합니다. &quot;**로 시작합니다./**&quot; - 경로가 폴더의 노드 아래에 있음을 나타냅니다.

다음은 이 속성에 유효한 값입니다.

* `./jcr:content/metadata/dc:title`:폴더의 메타데이터 노드에 값을 속성으로 저장합니다 `dc:title`.

* `./jcr:created`:자산의 생성 날짜와 시간을 저장합니다. 보호된 속성입니다. 이러한 속성을 구성하는 경우 [!UICONTROL 편집 비활성화]로 표시하는 것이 좋습니다.

구성 요소가 메타데이터 스키마 양식에서 제대로 표시되도록 하려면 속성 경로에 공백을 포함하지 마십시오.

**[!UICONTROL JSON 경로]**:옵션에 대한 키-값 쌍을 지정하는 JSON 파일의 경로를 지정하는 데 사용합니다.

**[!UICONTROL 자리 표시자]**:이 속성을 사용하여 메타데이터 속성과 관련된 관련 자리 표시자 텍스트를 지정합니다.

**[!UICONTROL 선택 사항]**:이 속성을 사용하여 목록에서 선택 사항을 지정합니다.

**[!UICONTROL 설명]**:이 속성을 사용하여 메타데이터 구성 요소에 대한 짧은 설명을 추가합니다.

**[!UICONTROL 클래스]**:속성이 연결된 객체 클래스입니다.

## 폴더 메타데이터 스키마 양식 {#delete-folder-metadata-schema-forms} 삭제

폴더 메타데이터 스키마 Forms 페이지에서 폴더 메타데이터 스키마 양식을 삭제할 수 있습니다. 양식을 삭제하려면 해당 양식을 선택하고 도구 모음에서 삭제 아이콘을 탭/클릭합니다.

![delete_form](assets/delete_form.png)

## 폴더 메타데이터 스키마 지정 {#assign-a-folder-metadata-schema}

폴더 메타데이터 스키마 Forms 페이지 또는 폴더를 만들 때 폴더 메타데이터 스키마를 폴더에 지정할 수 있습니다.

폴더에 대한 메타데이터 스키마를 구성하는 경우 스키마 양식 경로는 아래 폴더 노드의 `folderMetadataSchema` 속성에 저장됩니다.*/jcr:content*.

### 폴더 메타데이터 스키마 페이지 {#assign-to-a-schema-from-the-folder-metadata-schema-page}에서 스키마에 할당

1. AEM 로고를 탭/클릭하고 **[!UICONTROL 도구]** > **[!UICONTROL 자산]** **[!UICONTROL 폴더 메타데이터 스키마]**&#x200B;로 이동합니다.
1. 폴더 메타데이터 스키마 Forms 페이지에서 폴더에 적용할 스키마 양식을 선택합니다.
1. 도구 모음에서 **[!UICONTROL 폴더에 적용]**&#x200B;을 탭/클릭합니다.

1. 스키마를 적용할 폴더를 선택한 다음 **[!UICONTROL 적용]**&#x200B;을 클릭/탭합니다. 메타데이터 스키마가 이미 폴더에 적용된 경우 기존 메타데이터 스키마를 덮어쓸지 모른다는 경고 메시지가 표시됩니다. **[!UICONTROL 덮어쓰기]**&#x200B;를 탭/클릭합니다.
1. 메타데이터 스키마를 적용한 폴더의 메타데이터 속성을 엽니다.

   ![folder_properties](assets/folder_properties.png)

   폴더 메타데이터 필드를 보려면 **[!UICONTROL 폴더 메타데이터]** 탭을 탭/클릭합니다.

   ![folder_metadata_properties](assets/folder_metadata_properties.png)

### {#assign-a-schema-when-creating-a-folder} 폴더를 만들 때 스키마 할당

폴더를 만들 때 폴더 메타데이터 스키마를 할당할 수 있습니다. 시스템에 폴더 메타데이터 스키마가 하나 이상 있으면 **[!UICONTROL 폴더 만들기]** 대화 상자에 추가 목록이 표시됩니다. 원하는 스키마를 선택할 수 있습니다. 기본적으로 스키마가 선택되지 않습니다.

1. AEM Assets 사용자 인터페이스에서 도구 모음에서 **[!UICONTROL 만들기]**&#x200B;를 탭/클릭합니다.
1. 폴더의 제목과 이름을 지정합니다.
1. 폴더 메타데이터 스키마 목록에서 원하는 스키마를 선택합니다. 그런 다음 **[!UICONTROL 만들기]**&#x200B;를 탭/클릭합니다.

   ![select_schema](assets/select_schema.png)

1. 메타데이터 스키마를 적용한 폴더의 메타데이터 속성을 엽니다.
1. 폴더 메타데이터 필드를 보려면 **[!UICONTROL 폴더 메타데이터]** 탭을 탭/클릭합니다.

## 폴더 메타데이터 스키마 사용 {#use-the-folder-metadata-schema}

폴더 메타데이터 스키마로 구성된 폴더의 속성을 엽니다. 폴더 속성 페이지에 **[!UICONTROL 폴더 메타데이터]** 탭이 표시됩니다. 폴더 메타데이터 스키마 양식을 보려면 이 탭을 선택합니다.

다양한 필드에 메타데이터 값을 입력하고 **[!UICONTROL 저장]**&#x200B;을 탭/클릭하여 값을 저장합니다. 지정하는 값은 CRX 저장소의 폴더 노드에 저장됩니다.

![folder_metadata_properties-1](assets/folder_metadata_properties-1.png)
