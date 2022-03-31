---
title: 검색 패싯.
description: 이 문서에서는 Experience Manager에서 검색 패싯을 만들고, 수정하고, 사용하는 방법에 대해 설명합니다.
feature: Search,Metadata
role: User,Admin
exl-id: f994c1bf-3f9d-4cb2-88f4-72a9ad6fa999
source-git-commit: 8a9a3f60d6d52f6cc18a079f372a55d15bb60790
workflow-type: tm+mt
source-wordcount: '2397'
ht-degree: 20%

---

# 검색 패싯 {#search-facets}

엔터프라이즈급 Adobe Experience Manager Assets 배포는 많은 자산을 저장할 수 있는 기능을 제공합니다. Experience Manager의 일반 검색 기능만 사용하는 경우 적절한 자산을 찾는 것이 어렵고 시간이 걸릴 수 있습니다.

필터 패널의 검색 패싯을 사용하여 검색 경험에 더 많은 세부 사항을 추가하고 검색 기능을 보다 효율적이고 다양하게 만들 수 있습니다. 검색 패싯에는 더 복잡한 검색을 수행할 수 있도록 여러 차원(설명)이 추가됩니다. 필터 패널에는 몇 가지 표준 패싯이 포함되어 있습니다. 사용자 정의 검색 패싯을 추가할 수도 있습니다.

요약하면 검색 패싯을 사용하면 사전 결정된 단일 분류 순서가 아니라 여러 가지 방식으로 자산을 검색할 수 있습니다. 보다 집중된 검색을 위해 원하는 세부 정보로 쉽게 드릴다운할 수 있습니다.

예를 들어, 이미지를 찾는 경우 비트맵과 벡터 이미지 중 어느 것을 선택할지 선택할 수 있습니다. 이미지의 MIME 유형을 지정하여 검색 범위를 더 줄일 수 있습니다. 마찬가지로 문서를 검색할 때 형식인 PDF 또는 MS Word를 지정할 수 있습니다.

## 설명 추가 {#adding-a-predicate}

필터 패널에 표시되는 검색 패싯은 조건자를 사용하여 기본 검색 양식에 정의됩니다. 더 많거나 다른 패싯을 표시하려면 기본 양식에 설명을 추가하거나 선택한 패싯을 포함하는 사용자 정의 양식을 사용합니다.

전체 텍스트 검색의 경우 `Fulltext` 조건자를 추가합니다. 속성 설명을 사용하여 지정한 단일 속성과 일치하는 자산을 검색합니다. 옵션 조건부를 사용하여 특정 속성에 대해 하나 이상의 값과 일치하는 자산을 검색합니다. 날짜 범위 설명을 추가하여 지정된 날짜 범위 내에서 만들어진 자산을 검색합니다.

1. Experience Manager 로고를 클릭한 다음 **[!UICONTROL 도구]** > **[!UICONTROL 일반]** > **[!UICONTROL Forms 검색]**.
1. Forms 검색 페이지에서 **[!UICONTROL Assets 관리 검색 레일]**&#x200B;를 탭한 다음,  **편집** ![aemassets_edit](assets/aemassets_edit.png).

   ![자산 관리 검색 레일을 찾아 선택합니다](assets/assets_admin_searchrail.png)

1. [검색 편집] Forms 페이지에서 **[!UICONTROL 설명 선택]** 기본 창으로 이동합니다. 예를 들어 **[!UICONTROL 속성 설명]**.

   ![설명을 선택하고 이동하여 검색 필터를 사용자 지정합니다](assets/drag_predicate.png)

   *그림: 설명을 선택하고 이동하여 검색 필터를 사용자 지정합니다.*

1. 설정 탭에서 조건자에 대한 필드 레이블, 자리 표시자 텍스트 및 설명을 입력합니다. 조건자와 연결할 메타데이터 속성의 올바른 이름을 지정합니다. 설정 탭의 헤더 레이블은 선택한 조건부의 유형을 식별합니다.

   ![설정 탭을 사용하여 조건자의 필수 옵션을 제공합니다](assets/settings.png)

   *그림: 설정 탭을 사용하여 조건부의 필수 옵션을 제공합니다.*

1. In the **[!UICONTROL Property Name]** field, specify a valid name for the metadata property you want to associate with the predicate. It is the name based on which the search is performed. For example, enter `jcr:content/metadata/dc:description` or `./jcr:content/metadata/dc:description`. 선택 대화 상자에서 기존 노드를 선택할 수도 있습니다.

   ![속성 이름 필드의 조건자와 메타데이터 속성을 연결합니다](assets/property_settings.png)

   *그림: 속성 이름 필드에서 메타데이터 속성을 조건자와 연결합니다.*

1. 을(를) 클릭합니다. **[!UICONTROL 미리 보기]** ![미리 보기](assets/preview.png) 설명을 추가한 후 나타나는 [필터] 패널의 미리 보기를 생성하려면 다음을 수행합니다.
1. 미리 보기 모드에서 조건자의 레이아웃을 검토합니다.

   ![변경 사항을 제출하기 전에 검색 양식 미리 보기](assets/preview-1.png)

   변경 사항을 제출하기 전에 검색 양식 미리 보기

1. 미리 보기를 닫으려면 를 클릭합니다 **[!UICONTROL 닫기]** ![close](assets/do-not-localize/close_icon.png) 미리 보기 오른쪽 상단 모서리에서 을(를) 클릭합니다.
1. 탭 **[!UICONTROL 완료]** 설정을 저장하려면 을 클릭합니다.
1. 자산 사용자 인터페이스에서 검색 패널로 이동합니다. 속성 설명이 패널에 추가됩니다.
1. 텍스트 상자에서 검색할 자산에 대한 설명을 입력합니다. 예를 들어 &quot;Adobe&quot;을 입력합니다. 검색을 수행하면 &quot;Adobe&quot;과 일치하는 설명이 있는 자산이 검색 결과에 나열됩니다.

## 옵션 설명 추가 {#adding-an-options-predicate}

[옵션] 조건부를 사용하면 [필터] 패널에서 여러 검색 옵션을 추가할 수 있습니다. 필터 패널에서 이러한 옵션 중 하나 이상을 선택하여 자산을 검색할 수 있습니다. 예를 들어 파일 유형을 기반으로 자산을 검색하려면 검색 양식에서 이미지, 멀티미디어, 문서, 아카이브 등의 옵션을 구성합니다. 이러한 옵션을 구성한 후 필터 패널에서 이미지 옵션을 선택하면 GIF, JPEG, PNG 등 유형의 자산에 대해 검색이 수행됩니다.

옵션을 각 속성에 매핑하려면 옵션에 대한 노드 구조를 만들고 옵션 조건부의 속성 이름 속성에 상위 노드의 경로를 제공합니다. 부모 노드는 형식이어야 합니다. `sling`: `OrderedFolder`. 옵션은 유형이어야 합니다 `nt:unstructured`. 옵션 노드에는 속성이 있어야 합니다 `jcr:title` 및 `value` 구성했습니다.

다음 `jcr:title` 속성은 [필터] 패널에 표시되는 옵션의 사용자에게 친숙한 이름입니다. 다음 `value` 지정된 속성과 일치하도록 쿼리에 필드가 사용됩니다.

옵션을 선택하면 `value` 옵션 노드 및 그 하위 노드의 등록 정보(있는 경우)입니다. 옵션 노드 아래의 전체 트리가 탐색되고 `value` 각 하위 노드의 속성은 OR 작업을 사용하여 검색 쿼리를 형성합니다.

For example, if you select &quot;Images&quot; for file types, the search query for the assets is built by combining the `value` property using an OR operation. For example, the search query for images is built by combining the results matched for *image/jpeg*, *image/gif*, *image/png*, *image/pjpeg*, and *image/tiff* for the property `jcr:content/metadata/dc:format` using an OR operation.

CRXDE에서와 같이 파일 형식의 값 속성은 검색 쿼리가 작동하는 데 사용됩니다

Instead of manually creating a node structure for the options in the CRX repository, you can define the options in a JSON file by specifying corresponding key-value pairs. Specify the path of the JSON file in the **[!UICONTROL Property Name]** field. For example, you can define the key-value pairs, `image/bmp`, `image/gif`, `image/jpeg`, and `image/png` and specify their values as shown in the following sample JSON file. In the **[!UICONTROL Property Name]** field, you can specify the CRX path for this file.

```json
{
    "options" :
 [
          {"value" : "image/bmp","text" : "BMP"},
          {"value" : "image/gif","text" : "GIF"},
          {"value" : "image/jpeg","text" : "JPEG"},
          {"value" : "image/png","text" : "PNG"}
 ]
}
```

기존 노드를 사용하려면 선택 대화 상자를 사용하여 지정합니다.

>[!NOTE]
>
>옵션 조건부는 설명된 동작을 보여주는 속성 설명을 포함하는 사용자 지정 래퍼입니다. 현재 기능을 기본적으로 지원하는 데 사용할 수 있는 REST 엔드포인트가 없습니다.

1. Experience Manager 로고를 탭한 다음, **[!UICONTROL 도구 > 일반 > Forms 검색]**.
1. From the **[!UICONTROL Search Forms]** page, select **[!UICONTROL Assets Admin Search Rail]**, then tap the Edit icon.
1. In the **[!UICONTROL Edit Search Form]** page, drag **[!UICONTROL Options Predicate]** from the **[!UICONTROL Select Predicate]** tab to the main pane.
1. In the **[!UICONTROL Settings]** tab, enter a label and a name for the property. For example, to search assets based on their format, specify a user-friendly name for the label, for example **[!UICONTROL File Type]**. Specify the property based on which the search is to be performed in the property field, for example `jcr:content/metadata/dc:format.`
1. 다음 중 하나를 수행하십시오.

   * 에서 **[!UICONTROL 속성 이름]** 필드에 옵션에 대한 노드를 정의하고 해당 키-값 쌍을 지정하는 JSON 파일의 경로가 설명되어 있습니다.
   * 탭 ![자산 추가 아이콘](assets/do-not-localize/aem_assets_add_icon.png) 옵션 필드 옆에 있는 [필터] 패널에서 제공하려는 옵션의 표시 텍스트와 값을 지정합니다. 다른 옵션을 추가하려면 탭/클릭합니다 ![자산 추가 아이콘](assets/do-not-localize/aem_assets_add_icon.png) 단계를 반복합니다.

1. Ensure that **[!UICONTROL Single Select]** is cleared to let the user select multiple options for file types at a time (for example, Images, Documents, Multimedia, and Archives). If you select **[!UICONTROL Single Select]**, the user can select only one option for file types at a time.

   ![옵션 조건부의 사용 가능한 필드](assets/options_predicate.png)

   옵션 조건부의 사용 가능한 필드

1. 에서 **설명** 필드, 선택적 설명을 입력한 다음 **[!UICONTROL 완료]**.
1. 검색 패널로 이동합니다. 옵션 조건부가 **검색** 패널. 옵션 **[!UICONTROL 파일 유형]** 확인란으로 표시됩니다.

## 다중 값 속성 설명 추가 {#adding-a-multi-value-property-predicate}

다음 `Multi Value Property` 조건부를 사용하면 여러 값에 대한 자산을 검색할 수 있습니다. 에 여러 제품의 이미지가 있는 시나리오를 생각해 보십시오 [!DNL Assets] 및 각 이미지의 메타데이터에는 제품과 연관된 SKU 번호가 포함됩니다. 이 설명을 사용하여 여러 SKU 번호를 기반으로 제품 이미지를 검색할 수 있습니다.

1. Experience Manager 로고를 클릭한 다음 **[!UICONTROL 도구]** > **[!UICONTROL 일반]** > **[!UICONTROL Forms 검색]**.
1. Forms 검색 페이지에서 **[!UICONTROL Assets 관리 검색 레일]**, 탭 **편집** ![aemassets_edit](assets/aemassets_edit.png).
1. In the Edit Search Form page, drag a **[!UICONTROL Multi Value Property Predicate]** from the **[!UICONTROL Select Predicate]** tab to the main pane.
1. 에서 **[!UICONTROL 설정]** 탭에서 조건자의 레이블과 자리 표시자 텍스트를 입력합니다. 속성 필드에서 검색을 수행할 속성 이름을 지정합니다(예: ) `jcr:content/metadata/dc:value`. 선택 대화 상자에서 노드를 선택할 수도 있습니다.
1. Ensure that **[!UICONTROL Delimiter Support]** is selected. In the **[!UICONTROL Input Delimiters]** field, specify delimiters to separate individual values. By default, comma is specified as the delimiter. You can specify a different delimiter.
1. 에서 **설명** 필드, 선택적 설명 입력 및 탭 **[!UICONTROL 완료]**.
1. 자산 사용자 인터페이스의 필터 패널로 이동합니다. The **[!UICONTROL Multi Value Property]** predicate is added to the panel.
1. 복수 값 필드에 구분 기호로 구분된 여러 값을 지정하고 검색을 수행합니다. 조건부는 지정한 값에 대해 정확한 텍스트 일치를 가져옵니다.

## 태그 설명 추가 {#adding-a-tags-predicate}

다음 `Tags` 조건부를 사용하면 자산에 대해 태그 기반 검색을 수행할 수 있습니다. 기본적으로 [!DNL Assets] 는 지정하는 태그를 기준으로 하나 이상의 태그가 일치하는 자산을 검색합니다. 즉, 검색 쿼리는 지정된 태그를 사용하여 OR 작업을 수행합니다. 하지만 모든 태그 일치 옵션을 사용하여 지정하는 모든 태그를 포함하는 자산을 검색할 수 있습니다.

1. Experience Manager 로고를 클릭한 다음 **[!UICONTROL 도구]** > **[!UICONTROL 일반]** > **[!UICONTROL Forms 검색]**.
1. Forms 검색 페이지에서 **[!UICONTROL Assets 관리 검색 레일]** 그런 다음 **편집** ![aemassets_edit](assets/aemassets_edit.png).
1. 검색 양식 편집 페이지에서 **[!UICONTROL 태그 설명]** 설명 선택 탭에서 기본 창으로 이동합니다.
1. 설정 탭에서 조건자의 자리 표시자 텍스트를 입력합니다. 속성 필드에서 검색을 수행할 속성 이름을 지정합니다(예: ) `jcr:content/metadata/cq:tags`. 또는 선택 대화 상자에서 CRXDE의 노드를 선택할 수 있습니다.
1. 태그 목록에서 다양한 태그를 채우도록 이 술어의 루트 태그 경로 속성을 구성합니다.
1. Select **[!UICONTROL Show match all tags option]** to search for assets that include all tags that you specify.

   ![태그 조건부의 일반적인 설정](assets/tags_predicate.png)

1. 에서 **[!UICONTROL 설명]** 필드에서 선택적 설명을 입력한 다음 클릭/탭합니다 **[!UICONTROL 완료]**.
1. 검색 패널로 이동합니다. 다음 **[!UICONTROL 태그]** 설명이 [검색] 패널에 추가됩니다.
1. 자산을 검색할 위치에 대한 태그를 지정하거나 제안 목록에서 선택합니다.
1. 선택 **[!UICONTROL 모두 일치]** 를 입력하여 지정한 모든 태그를 포함하는 일치 항목을 검색합니다.

태그 구조를 **[!UICONTROL 이름]** (알파벳 순서), **[!UICONTROL 생성됨]** 날짜 또는 **[!UICONTROL 수정됨]** 날짜. 다음 그림에서 태그 구조는 **[!UICONTROL 이름]**.

![추가 태그](assets/add-tags-to-asset.png)


## 다른 설명 추가 {#adding-other-predicates}

속성 조건자 또는 옵션 설명을 추가하는 방법과 유사하게 검색 패널에 다음과 같은 추가 설명을 추가할 수 있습니다.

<table>
 <tbody>
  <tr>
   <td><p><strong>설명 이름</strong></p> </td>
   <td><p><strong>설명</strong></p> </td>
   <td><p><strong>속성</strong></p> </td>
  </tr>
  <tr>
   <td><p>전체 텍스트</p> </td>
   <td>전체 자산 노드에서 전체 텍스트 검색을 수행하는 검색 조건입니다. 이 ID는 <code>jcr</code>:<code>contains</code> 연산자를 사용할 수 있습니다. 자산 노드의 특정 부분에서 전체 텍스트 검색을 수행하려면 상대 경로를 지정할 수 있습니다.</td>
   <td>
    <ul>
     <li>레이블</li>
     <li>자리 표시자</li>
     <li>속성 이름</li>
     <li>설명</li>
    </ul> </td>
  </tr>
  <tr>
   <td>경로 브라우저</td>
   <td>사전 구성된 루트 경로에서 폴더 및 하위 폴더의 자산을 검색하려면 검색 조건어를 사용하십시오</td>
   <td>
    <ul>
     <li>자리 표시자</li>
     <li>루트 경로</li>
     <li>설명</li>
    </ul> </td>
  </tr>
  <tr>
   <td><p>경로</p> </td>
   <td><p>결과를 위치에 대해 필터링하려면 이 변수를 사용하십시오. 다양한 경로를 옵션으로 지정할 수 있습니다.</p> </td>
   <td>
    <ul>
     <li>레이블</li>
     <li>경로</li>
     <li>설명</li>
    </ul> </td>
  </tr>
  <tr>
   <td><p>게시 상태</p> </td>
   <td><p>검색 조건자를 사용하여 게시 상태에 따라 자산을 검색합니다</p> </td>
   <td>
    <ul>
     <li>레이블</li>
     <li>속성 이름</li>
     <li>설명</li>
    </ul> </td>
  </tr>
  <tr>
   <td><p>상대적 날짜</p> </td>
   <td><p>검색 조건자를 사용하여 자산의 상대적 날짜에 따라 자산을 검색합니다. 예를 들어 2개월 전, 3주 전 등과 같은 옵션을 구성할 수 있습니다. </p> </td>
   <td>
    <ul>
     <li>레이블</li>
     <li>속성 이름</li>
     <li>상대적 날짜</li>
    </ul> </td>
  </tr>
  <tr>
   <td><p>범위</p> </td>
   <td><p>검색 조건자를 사용하여 지정된 범위 내에 있는 자산을 검색합니다. [검색] 패널에서 범위에 대한 최소값과 최대값을 지정할 수 있습니다.</p> </td>
   <td>
    <ul>
     <li>레이블</li>
     <li>속성 이름</li>
     <li>설명</li>
    </ul> </td>
  </tr>
  <tr>
   <td><p>날짜 범위</p> </td>
   <td><p>검색 조건자를 사용하여 날짜 속성에 대해 지정된 범위 내에서 생성된 자산을 검색합니다. 검색 패널에서 날짜 선택기를 사용하여 시작 및 종료 날짜를 지정할 수 있습니다.</p> </td>
   <td>
    <ul>
     <li>레이블</li>
     <li>자리 표시자</li>
     <li>속성 이름</li>
     <li>범위 텍스트(시작)</li>
     <li>범위 텍스트(끝)</li>
     <li>설명</li>
    </ul> </td>
  </tr>
  <tr>
   <td><p>날짜</p> </td>
   <td><p>날짜 속성을 기반으로 자산의 슬라이더 기반 검색에 대한 검색 조건입니다.</p> </td>
   <td>
    <ul>
     <li>레이블</li>
     <li>속성 이름</li>
     <li>설명</li>
    </ul> </td>
  </tr>
  <tr>
   <td><p>파일 크기</p> </td>
   <td><p>검색 조건자를 사용하여 크기를 기준으로 자산을 검색합니다. 구성 가능한 노드에서 슬라이더 옵션을 선택하는 실버 기반 조건입니다. 기본 옵션은 CRX 저장소의 /libs/dam/options/predicate/filesize에 정의됩니다. 파일 크기는 바이트 단위로 제공됩니다.</p> </td>
   <td>
    <ul>
     <li>레이블</li>
     <li>속성 이름</li>
     <li>경로</li>
     <li>설명</li>
    </ul> </td>
  </tr>
  <tr>
   <td>마지막으로 수정된 자산</td>
   <td>최근에 수정된 자산을 검색할 설명 검색 </td>
   <td>
    <ul>
     <li>속성 이름</li>
     <li>속성 값</li>
     <li>설명</li>
    </ul> </td>
  </tr>
  <tr>
   <td>게시 상태</td>
   <td>검색 조건자를 사용하여 게시 상태에 따라 자산을 검색합니다 </td>
   <td>
    <ul>
     <li>레이블</li>
     <li>속성 이름</li>
     <li>설명</li>
    </ul> </td>
  </tr>
  <tr>
   <td>만료 상태</td>
   <td>검색 조건자를 사용하여 만료 상태에 따라 자산을 검색합니다 </td>
   <td>
    <ul>
     <li>레이블</li>
     <li>속성 이름</li>
     <li>설명</li>
    </ul> </td>
  </tr>
  <tr>
   <td>숨김</td>
   <td>자산을 검색할 숨겨진 필드 속성을 정의하는 검색 조건입니다</td>
   <td>
    <ul>
     <li>속성 이름</li>
     <li>속성 값</li>
     <li>설명</li>
    </ul> </td>
  </tr>
 </tbody>
</table>

## 기본 검색 패싯 복원 {#restoring-default-search-facets}

기본적으로 앞에 잠금 아이콘이 표시됩니다 **[!UICONTROL Assets 관리 검색 레일]** 에서 **[!UICONTROL Forms 검색]** 페이지. 검색 패싯을 양식에 추가하면 기본 양식이 수정되었음을 나타내는 잠금 아이콘이 사라집니다.

Forms 검색 페이지의 옵션에 대한 잠금 아이콘은 기본 설정이 그대로 있고 사용자 지정되지 않았음을 나타냅니다.

기본 검색 패싯을 복원하려면 다음 단계를 수행합니다.

1. 선택 **[!UICONTROL Assets 관리 검색 레일]** 에서 **[!UICONTROL Forms 검색]** 페이지.
1. 탭 **[!UICONTROL 삭제]** ![아이콘 삭제](assets/do-not-localize/deleteoutline.png) 클릭합니다.
1. 확인 대화 상자에서 **[!UICONTROL 삭제]** 를 클릭하여 사용자 지정 변경 사항을 제거합니다.

   After you delete the custom changes to search facets, the Lock icon reappears before **[!UICONTROL Assets Admin Search Rail]** in the **[!UICONTROL Search Forms]** page.

## 사용자 권한 {#user-permissions}

관리자 역할이 할당되지 않은 경우 검색 패싯과 관련된 편집, 삭제 및 미리 보기 작업을 수행해야 하는 권한 목록이 있습니다.

| 작업 | 권한 |
|---|---|
| 편집 | 에 대한 읽기 및 쓰기 권한 `/apps` 노드 아래에 있어야 합니다. |
| 삭제 | 에서 사용 권한을 읽기, 쓰기 및 삭제합니다. `/apps` 노드 아래에 있어야 합니다. |
| 미리 보기 | 에서 사용 권한을 읽기, 쓰기 및 삭제합니다. `/var/dam/content` 노드 아래에 있어야 합니다. 또한 다음 항목에 대한 읽기 및 쓰기 권한 `/apps` 노드 아래에 있어야 합니다. |

>[!MORELIKETHIS]
>
>* [디지털 자산 검색](search-assets.md).

