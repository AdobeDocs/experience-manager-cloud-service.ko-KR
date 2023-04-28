---
title: 폴더 메타데이터 스키마
description: 에서 자산 폴더에 대한 메타데이터 스키마를 만드는 방법을 알아보십시오 [!DNL Experience Manager Assets]
contentOwner: AG
feature: Metadata
role: User,Admin
exl-id: c86760ed-169d-40f7-91a4-8aee449b286c
source-git-commit: 8bdd89f0be5fe7c9d4f6ba891d7d108286f823bb
workflow-type: tm+mt
source-wordcount: '1090'
ht-degree: 11%

---

# 폴더 메타데이터 스키마 {#folder-metadata-schema}

[!DNL Adobe Experience Manager Assets]을 사용하면 폴더 속성 페이지에 표시되는 레이아웃 및 메타데이터를 정의하는 자산 폴더에 대한 메타데이터 스키마를 생성할 수 있습니다. 

## 폴더 메타데이터 스키마 양식 추가 {#add-a-folder-metadata-schema-form}

폴더 메타데이터 스키마 Forms 편집기를 사용하여 폴더에 대한 메타데이터 스키마를 만들고 편집합니다.

1. 을 탭/클릭합니다. [!DNL Experience Manager] 로고로 이동하여 **[!UICONTROL 도구]** > **[!UICONTROL 자산]** > **[!UICONTROL 폴더 메타데이터 스키마]**.
1. 폴더 메타데이터 스키마 Forms 페이지에서 을 탭/클릭합니다 **[!UICONTROL 만들기]**.
1. 양식의 이름을 지정하고 탭/클릭합니다 **[!UICONTROL 만들기]**. 새 스키마 양식은 스키마 Forms 페이지에 나열됩니다.

## 폴더 메타데이터 스키마 양식 편집 {#edit-folder-metadata-schema-forms}

다음을 포함하는 새로 추가되거나 기존 메타데이터 스키마 양식을 편집할 수 있습니다.

* 탭
* 탭 내의 양식 항목.

이러한 양식 항목을 CRX 저장소의 메타데이터 노드 내의 필드에 매핑/구성할 수 있습니다. 새 탭 또는 양식 항목을 메타데이터 스키마 양식에 추가할 수 있습니다.

1. 스키마 Forms 페이지에서 만든 양식을 선택한 다음 **[!UICONTROL 편집]** 아이콘 을 클릭하여 제품에서 사용할 수 있습니다.
1. 폴더 메타데이터 스키마 편집기 페이지에서 **[!UICONTROL +]** 아이콘을 클릭하여 양식에 탭을 추가합니다. 탭의 이름을 변경하려면 기본 이름을 탭/클릭하고 아래에 새 이름을 지정합니다 **[!UICONTROL 설정]**.

   ![custom_tab](assets/custom_tab.png)

   탭을 더 추가하려면 **[!UICONTROL +]** 아이콘. 탭/클릭 **[!UICONTROL X]** 탭을 삭제하려면 다음을 수행하십시오.

1. 활성 탭에서 구성 요소를 한 개 이상 추가합니다 **[!UICONTROL 양식 작성]** 탭.

   ![adding_components](assets/adding_components.png)

   여러 탭을 만드는 경우 특정 탭을 탭/클릭하여 구성 요소를 추가합니다.

1. 구성 요소를 구성하려면 구성 요소를 선택하고 에서 해당 속성을 수정합니다 **[!UICONTROL 설정]** 탭.

   필요한 경우 구성 요소에서 삭제 **[!UICONTROL 설정]** 탭.

   ![configure_properties](assets/configure_properties.png)

1. 탭/클릭 **[!UICONTROL 저장]** 도구 모음에서 변경 사항을 저장합니다.

### 양식을 작성할 구성 요소 {#components-to-build-forms}

다음 **[!UICONTROL 양식 작성]** 탭에는 폴더 메타데이터 스키마 양식에서 사용하는 양식 항목이 나열됩니다. 다음 **[!UICONTROL 설정]** 탭에는 **[!UICONTROL 양식 작성]** 탭. 다음은 에서 사용할 수 있는 양식 항목의 목록입니다 **[!UICONTROL 양식 작성]** 탭:

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
   <td><p> 한 줄 텍스트 속성을 추가합니다. 문자열로 저장됩니다.</p> </td>
  </tr>
  <tr>
   <td><p>다중 값 텍스트</p> </td>
   <td><p> 다중 값 텍스트 속성을 추가합니다. 문자열 배열로 저장됩니다.</p> </td>
  </tr>
  <tr>
   <td><p>숫자</p> </td>
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
   <td><p> 숨김 필드를 추가합니다. 자산을 저장할 때 POST 매개 변수로 전송됩니다.</p> </td>
  </tr>
 </tbody>
</table>

### 양식 항목 편집 {#editing-form-items}

양식 항목의 속성을 편집하려면 구성 요소를 탭/클릭하고 **[!UICONTROL 설정]** 탭. 메타데이터 스키마의 주어진 속성에 필드를 하나만 매핑하는 것이 좋습니다. 그렇지 않으면 시스템에 의해 속성에 매핑된 최신 추가 필드가 선택됩니다.

**[!UICONTROL 필드 레이블]**: 폴더의 속성 페이지에 표시되는 메타데이터 속성의 이름입니다.

**[!UICONTROL 속성에 매핑]**: 이 속성은 CRX 저장소가 저장된 폴더 노드의 상대 경로를 지정합니다. 다음으로 시작: &quot;**./**&quot; - 경로가 폴더의 노드 아래에 있음을 나타냅니다.

다음은 속성에 유효한 값의 예입니다.

* `./jcr:content/metadata/dc:title`: 폴더의 메타데이터 노드에 값을 속성으로 저장합니다 `dc:title`.

* `./jcr:created`: 자산의 생성 날짜 및 시간을 저장합니다. 보호된 속성입니다. 이러한 속성을 구성하는 경우 속성을 [!UICONTROL 편집 비활성화].

구성 요소가 메타데이터 스키마 양식에 올바르게 표시되는지 확인하려면 속성 경로에 공백을 포함하지 마십시오.

**[!UICONTROL JSON 경로]**: 옵션에 키-값 쌍을 지정하는 JSON 파일의 경로를 지정하는 데 사용합니다.

**[!UICONTROL 자리 표시자]**: 이 속성을 사용하여 메타데이터 속성과 관련된 관련 자리 표시자 텍스트를 지정합니다.

**[!UICONTROL 선택 사항]**: 이 속성을 사용하여 목록에서 선택 사항을 지정합니다.

**[!UICONTROL 설명]**: 이 속성을 사용하여 메타데이터 구성 요소에 대한 간단한 설명을 추가합니다.

**[!UICONTROL 클래스]**: 속성이 연결된 객체 클래스입니다.

## 폴더 메타데이터 스키마 양식 삭제 {#delete-folder-metadata-schema-forms}

폴더 메타데이터 스키마 Forms 페이지에서 폴더 메타데이터 스키마 양식을 삭제할 수 있습니다. 양식을 삭제하려면 해당 양식을 선택하고 도구 모음에서 삭제 아이콘을 탭/클릭합니다.

![delete_form](assets/delete_form.png)

## 폴더 메타데이터 스키마 할당 {#assign-a-folder-metadata-schema}

폴더 메타데이터 스키마 Forms 페이지나 폴더를 만들 때 폴더에 폴더 메타데이터 스키마를 할당할 수 있습니다.

폴더에 대한 메타데이터 스키마를 구성하는 경우 스키마 양식의 경로는 `folderMetadataSchema` 아래에 있는 폴더 노드의 속성입니다.*/jcr:content*.

### 폴더 메타데이터 스키마 페이지에서 스키마에 할당 {#assign-to-a-schema-from-the-folder-metadata-schema-page}

1. 을 탭/클릭합니다. [!DNL Experience Manager] 로고로 이동하여 **[!UICONTROL 도구]** > **[!UICONTROL 자산]**> **[!UICONTROL 폴더 메타데이터 스키마]**.
1. 폴더 메타데이터 스키마 Forms 페이지에서 폴더에 적용할 스키마 양식을 선택합니다.
1. 도구 모음에서 탭/클릭 **[!UICONTROL 폴더에 적용]**.

1. 스키마를 적용할 폴더를 선택한 다음 클릭/탭합니다 **[!UICONTROL 적용]**. 메타데이터 스키마가 폴더에 이미 적용된 경우 기존 메타데이터 스키마를 덮어쓸 것임을 알리는 경고 메시지가 표시됩니다. 탭/클릭 **[!UICONTROL 덮어쓰기]**.
1. 메타데이터 스키마를 적용한 폴더의 메타데이터 속성을 엽니다.

   ![folder_properties](assets/folder_properties.png)

   To view the folder metadata fields, tap/click the **[!UICONTROL Folder Metadata]** tab.

   ![folder_metadata_properties](assets/folder_metadata_properties.png)

### 폴더를 만들 때 스키마 할당 {#assign-a-schema-when-creating-a-folder}

폴더를 만들 때 폴더 메타데이터 스키마를 할당할 수 있습니다. 시스템에 폴더 메타데이터 스키마가 하나 이상 있으면 **[!UICONTROL 폴더 만들기]** 대화 상자. 원하는 스키마를 선택할 수 있습니다. 기본적으로 선택된 스키마가 없습니다.

1. 에서 [!DNL Experience Manager Assets] 사용자 인터페이스, 탭/클릭 **[!UICONTROL 만들기]** 를 클릭합니다.
1. 폴더의 제목과 이름을 지정합니다.
1. 폴더 메타데이터 스키마 목록에서 원하는 스키마를 선택합니다. 그런 다음 탭/클릭합니다 **[!UICONTROL 만들기]**.

   ![select_schema](assets/select_schema.png)

1. 메타데이터 스키마를 적용한 폴더의 메타데이터 속성을 엽니다.
1. To view the folder metadata fields, tap/click the **[!UICONTROL Folder Metadata]** tab.

## 폴더 메타데이터 스키마 사용 {#use-the-folder-metadata-schema}

Open the properties for a folder configured with a folder metadata schema. A **[!UICONTROL Folder Metadata]** tab is displayed in the folder properties page. To view the folder metadata schema form, select this tab.

다양한 필드에 메타데이터 값을 입력하고 탭/클릭합니다 **[!UICONTROL 저장]** 값을 저장합니다. 지정하는 값은 CRX 저장소의 폴더 노드에 저장됩니다.

![folder_metadata_properties-1](assets/folder_metadata_properties-1.png)

**추가 참조**

* [에셋 번역](translate-assets.md)
* [Assets HTTP API](mac-api-assets.md)
* [자산 지원 파일 형식](file-format-support.md)
* [에셋 검색](search-assets.md)
* [연결된 자산](use-assets-across-connected-assets-instances.md)
* [에셋 보고서](asset-reports.md)
* [메타데이터 스키마](metadata-schemas.md)
* [에셋 다운로드](download-assets-from-aem.md)
* [메타데이터 관리](manage-metadata.md)
* [검색 패싯](search-facets.md)
* [컬렉션 관리](manage-collections.md)
* [벌크 메타데이터 가져오기](metadata-import-export.md)
