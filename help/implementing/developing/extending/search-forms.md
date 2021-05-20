---
title: 검색 양식 구성
description: Adobe Experience Manager에 대한 Search Forms을 Cloud Service으로 구성
exl-id: b06649c4-cc91-44e3-8699-00e90140b90d
source-git-commit: 90de3cf9bf1c949667f4de109d0b517c6be22184
workflow-type: tm+mt
source-wordcount: '2043'
ht-degree: 16%

---

# 검색 양식 구성 {#configuring-search-forms}

Adobe Experience Manager as a Cloud Service은 강력한 [검색](/help/sites-cloud/authoring/getting-started/search.md) 메커니즘과 함께 제공됩니다.

이와 함께 컨텐츠를 필터링할 수 있도록 미리 정의된 옵션 세트가 있습니다. 이러한 패싯은 **수정한 날짜**, **게시 상태** 또는 **Livecopy 상태**&#x200B;와 같이 사전 정의된 패싯으로 구성되어 필요한 리소스로 빠르게 드릴다운할 수 있습니다.

![검색 및 필터 사용](assets/csf-usage.png)

이러한 목적을 함께 사용하면 다음과 같이 컨텐츠를 빠르고 쉽게 찾을 수 있습니다.

* [검색 및 필터](/help/sites-cloud/authoring/getting-started/search.md#search-and-filter)
* [레일 선택기](/help/sites-cloud/authoring/getting-started/basic-handling.md#rail-selector)
* [자산 브라우저](/help/sites-cloud/authoring/fundamentals/environment-tools.md#assets-browser)(페이지를 편집할 때)

>[!NOTE]
>
>기본 [콘텐츠 검색 및 색인 지정](/help/operations/indexing.md) 서비스를 구성할 수 있습니다.

**Forms 검색**&#x200B;을 사용하면 특정 요구 사항에 따라 이러한 패널을 사용자 지정하고 확장할 수 있습니다.

**Forms 검색**&#x200B;에서는 결합하고 정의할 수 있는 [에 대한 기본 선택 항목을 제공합니다. ](#predicates-and-their-settings) 이러한 양식](#configuring-your-search-forms)을 구성하기 위한 [대화 상자는 다음을 통해 액세스할 수 있습니다.

* **도구**
   * **일반**
      * **검색 양식**

## 기본 Forms {#default-forms}

처음 **Forms 검색** 콘솔에 액세스하면 모든 구성에 자물쇠 기호가 있음을 알 수 있습니다. 이는 해당 구성이 기본(기본) 구성이며 삭제할 수 없음을 나타냅니다. 사용자 지정하고 저장하면 구성이 사라집니다. [사용자 지정된 구성](#deleting-a-configuration-to-reinstate-the-default)을 삭제하면 다시 나타납니다. 이 경우 기본값(및 자물쇠 표시기)이 복원됩니다.

![검색 양식 구성 개요](assets/csf-overview.png)

사용 가능한 기본 구성(알파벳순으로 나열됨)은 다음과 같습니다.

* **자산 관리자 검색 레일**
* **페이지 편집기(문서 검색)**
* **페이지 편집기(경험 조각 검색)**
* **페이지 편집기(이미지 검색)**
* **페이지 편집기(원고 검색)**
* **페이지 편집기(페이지 검색)**
* **페이지 편집기(단락 검색)**
* **페이지 편집기(제품 검색)**
* **페이지 편집기(Scene7 검색)**
* **페이지 편집기(비디오 검색)**
* **프로젝트 관리자 검색 레일**
* **프로젝트 번역 검색 레일**
* **사이트 관리자 검색 레일**
* **코드 조각 관리자 검색 레일**
* **Stock 관리자 검색 레일**
* **컨텐츠 조각 모델 검색 레일**
* **프로젝트 관리자 검색 레일**
* **프로젝트 번역 검색 레일**

>[!NOTE]
>
>자산 관련 검색 양식에 대한 자세한 내용은 [자산 - 검색 패싯](/help/assets/search-facets.md)을 참조하십시오.


## 설명 및 설정 {#predicates-and-their-settings}

### 설명 {#predicates}

구성에 따라 다음 설명을 사용할 수 있습니다.

<table>
 <tbody>
  <tr>
   <th>조건자</th>
   <th>목적</th>
   <th>설정</th>
  </tr>
  <tr>
   <td>분석</td>
   <td>Analytics 기반 데이터를 표시할 때 Sites 브라우저에서 검색/필터링 기능을 사용할 수 있습니다. Analytics 검색 필터가 매핑된 사용자 지정된 분석 열과 일치하도록 로드됩니다.</td>
   <td>
    <ul>
     <li>필드 레이블</li>
     <li>설명</li>
    </ul> </td>
  </tr>
  <tr>
   <td>승인 상태</td>
   <td>승인 상태에 따라 검색합니다.</td>
   <td>
    <ul>
     <li>필드 레이블</li>
     <li>속성 이름*</li>
     <li>설명</li>
    </ul> 
   </td>
  </tr>
  <tr>
   <td>작성</td>
   <td>작성자에 따라 검색합니다.</td>
   <td>
    <ul>
     <li>자리 표시자</li>
     <li>속성 이름*</li>
     <li>설명</li>
    </ul> 
   </td>
  </tr>
  <tr>
   <td>체크아웃 기준</td>
   <td>특정 사용자가 체크 아웃한 자산을 검색합니다.</td>
   <td>
    <ul>
     <li>필드 레이블</li>
     <li>자리 표시자</li>
     <li>설명</li>
    </ul> 
   </td>
  </tr>
  <tr>
   <td>체크아웃 상태</td>
   <td>특정 체크아웃 상태로 자산을 검색합니다.</td>
   <td>
    <ul>
     <li>필드 레이블</li>
     <li>속성 이름*</li>
     <li>설명</li>
    </ul> 
   </td>
  </tr>
  <tr>
   <td>구성 요소</td>
   <td>작성자가 특정 구성 요소가 있는 페이지를 검색/필터링할 수 있습니다. 예: 이미지 갤러리.<br /> </td>
   <td>
    <ul>
     <li>자리 표시자</li>
     <li>속성 이름*</li>
     <li>속성 깊이</li>
     <li>설명</li>
    </ul> </td>
  </tr>
  <tr>
   <td>날짜 범위</td>
   <td>지정된 범위 내에서 만든 리소스에 대해 날짜 속성을 검색합니다. 검색 패널에서 시작 및 종료 날짜를 지정할 수 있습니다.</td>
   <td>
    <ul>
     <li>필드 레이블</li>
     <li>자리 표시자</li>
     <li>속성 이름*</li>
     <li>범위 텍스트(시작)*</li>
     <li>범위 텍스트(끝)*</li>
     <li>설명</li>
    </ul> </td>
  </tr>
  <tr>
   <td>만료 상태</td>
   <td>만료 상태에 따라 리소스를 검색합니다.</td>
   <td>
    <ul>
     <li>필드 레이블</li>
     <li>속성 이름*</li>
     <li>설명</li>
    </ul> </td>
  </tr>
  <tr>
   <td>파일 크기</td>
   <td>크기를 기준으로 리소스를 필터링합니다.</td>
   <td>
    <ul>
     <li>필드 레이블</li>
     <li>속성 이름*</li>
     <li>옵션 경로</li>
     <li>설명</li>
    </ul> </td>
  </tr>
  <tr>
   <td>파일 유형</td>
   <td>파일/mime 유형을 기반으로 자산을 검색합니다.</td>
   <td>
    <ul>
     <li>필드 레이블</li> 
     <li>속성 이름*</li>
     <li>MIME 유형 경로</li>
     <li>설명</li>
    </ul> 
   </td>
  </tr>
  <tr>
   <td>전체 텍스트</td>
   <td>전체 텍스트 검색에 대한 검색 조건입니다. 이 변수는 'jcr:contains' 연산자와 매핑됩니다.</td>
   <td>
    <ul>
     <li>자리 표시자</li>
     <li>속성 이름</li>
     <li>설명</li>
    </ul> </td>
  </tr>
  <tr>
   <td>그룹</td>
   <td>그룹에 대한 검색 설명(인사이트 조건에서만 사용).</td>
   <td>
    <ul>
     <li>필드 레이블</li>
     <li>설명</li>
    </ul> </td>
  </tr>
  <tr>
   <td>숨겨진 필터</td>
   <td>사용자가 볼 수 없는 속성 및 값에 대한 필터입니다.</td>
   <td>
    <ul>
     <li>속성 이름*</li>
     <li>속성 값*</li>
     <li>설명</li>
    </ul> </td>
  </tr>
  <tr>
   <td>인사이트</td>
   <td>선택한 인사이트 매개 변수에 따라 검색합니다.</td>
   <td>여러 조건자로 구성된 복잡한 조건입니다.
    <ul>
     <li>그룹</li>
     <li>범위</li>
     <li>옵션</li>
    </ul> 
   </td>
  </tr>
  <tr>
   <td>컬렉션의 멤버</td>
   <td>컬렉션의 멤버인 자산 검색</td>
   <td>
    <ul>
     <li>설명</li>
    </ul> 
   </td>
  </tr>
  <tr>
   <td>다중 값 속성</td>
   <td>지정된 속성의 여러 값을 검색합니다.</td>
   <td>
    <ul>
     <li>필드 레이블</li>
     <li>자리 표시자</li>
     <li>속성 이름*</li>
     <li>구분 기호 지원</li>
     <li>입력 구분 기호</li>
     <li>대소문자 구분 안 함</li>
     <li>설명</li>
    </ul> 
   </td>
  </tr>
  <tr>
   <td>옵션</td>
   <td><p>옵션은 사용자가 만든 컨텐츠 노드입니다.</p> <p>자세한 내용은 <a href="#addinganoptionspredicate">옵션 설명</a> 추가 를 참조하십시오.</p> </td>
   <td>
    <ul>
     <li>필드 레이블</li>
     <li>속성 이름*</li>
     <li>단일 선택</li>
     <li>옵션 추가</li>
     <li>수동</li>
     <li>설명</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Options 속성</td>
   <td>옵션의 속성을 하나 이상 검색합니다.</td>
   <td>
    <ul>
     <li>필드 레이블</li>
     <li>속성 이름*</li>
     <li>옵션 노드 경로</li>
     <li>속성 깊이</li>
     <li>단일 선택</li>
     <li>설명</li>
    </ul> </td>
  </tr>
  <tr>
   <td>페이지 상태</td>
   <td>상태에 따라 페이지를 필터링합니다.</td>
   <td>
    <ul>
     <li>필드 레이블</li>
     <li>속성 이름 게시*</li>
     <li>잠긴 페이지 속성 이름*</li>
     <li>설명</li>
    </ul> </td>
  </tr>
  <tr>
   <td>경로</td>
   <td>특정 경로에 따라 필터링합니다. 여러 경로를 옵션으로 지정할 수 있습니다.</td>
   <td>
    <ul>
     <li>필드 레이블</li>
     <li>검색 경로 추가</li>
     <li>설명</li>
    </ul> </td>
  </tr>
  <tr>
   <td>경로 브라우저</td>
   <td>사전 정의된 루트 경로 아래에서 검색할 경로 브라우저를 제공합니다.</td>
   <td>
    <ul>
     <li>자리 표시자</li>
     <li>루트 경로</li>
     <li>설명</li>
    </ul> 
   </td>
  </tr>
  <tr>
   <td>숨겨진 경로</td>
   <td>경로에 있는 필터이며 사용자가 볼 수 없습니다.</td>
   <td>
    <ul>
     <li>속성 이름('path')</li>
     <li>속성 값 ('/content/dam')</li>
    </ul> 
   </td>
  </tr>
  <tr>
   <td>속성</td>
   <td>지정된 속성을 검색합니다.</td>
   <td>
    <ul>
     <li>필드 레이블</li>
     <li>자리 표시자</li>
     <li>속성 이름</li>
     <li>부분 검색</li>
     <li>대소문자 구분 안 함</li>
     <li>설명</li>
    </ul> 
   </td>
  </tr>
  <tr>
   <td>게시 상태</td>
   <td>게시 상태에 따라 리소스를 필터링합니다.</td>
   <td>
    <ul>
     <li>필드 레이블</li>
     <li>속성 이름*</li>
     <li>설명</li>
    </ul> </td>
  </tr>
  <tr>
   <td>범위</td>
   <td>지정된 범위 내에 있는 리소스를 검색합니다. [검색] 패널에서 범위에 대한 최소값과 최대값을 지정할 수 있습니다.</td>
   <td>
    <ul>
     <li>필드 레이블</li>
     <li>속성 이름*</li>
     <li>설명</li>
    </ul> </td>
  </tr>
  <tr>
   <td>등급</td>
   <td>평균 등급에 따라 리소스를 검색합니다.<br /> </td>
   <td>
    <ul>
     <li>필드 레이블</li>
     <li>속성 이름*</li>
     <li>옵션 경로</li>
     <li>설명</li>
    </ul> </td>
  </tr>
  <tr>
   <td>상대적 날짜</td>
   <td>만든 상대적 날짜에 따라 리소스를 필터링합니다. 예를 들어, 1주 전, 1개월 전.</td>
   <td>
    <ul>
     <li>필드 레이블</li>
     <li>속성 이름*</li>
     <li>상대적 날짜</li>
     <li>설명</li>
    </ul> </td>
  </tr>
  <tr>
   <td>슬라이더 범위</td>
   <td>슬라이더 기능을 사용하여 범위 설명을 확장하는 일반적인 검색 조건입니다. 검색된 속성 값은 슬라이더 제한 사이여야 합니다.</td>
   <td>
    <ul>
     <li>필드 레이블</li>
     <li>속성 이름*</li>
     <li>옵션 노드 경로</li>
     <li>설명</li>
    </ul> </td>
  </tr>
  <tr>
   <td>상태</td>
   <td>승인 및 체크아웃 상태에 따라 검색합니다.</td>
   <td>여러 조건자로 구성된 복잡한 조건입니다.
    <ul>
     <li>승인 상태</li>
     <li>체크아웃 상태</li>
    </ul> 
   </td>
  </tr>
  <tr>
   <td>태그</td>
   <td>태그를 기준으로 검색합니다.</td>
   <td>
    <ul>
     <li>필드 라벨</li>
     <li>자리 표시자</li>
     <li>속성 이름*</li>
     <li>일치하는 모든 태그 옵션 표시</li>
     <li>루트 태그 경로</li>
     <li>설명</li>
    </ul> </td>
  </tr>
  <tr>
   <td>템플릿</td>
   <td>선택한 템플릿에 따라 검색합니다.</td>
   <td>
    <ul>
     <li>자리 표시자</li>
     <li>속성 이름*</li>
     <li>설명</li>
    </ul> 
   </td>
  </tr>
  <tr>
   <td>번역 상태</td>
   <td>번역 상태에 따라 검색합니다.</td>
   <td>
    <ul>
     <li>필드 레이블</li>
    </ul> 
   </td>
  </tr>
 </tbody>
</table>

<!--
  <tr>
   <td>Date ???</td>
   <td>Slider-based search of assets based on a date property.</td>
   <td>
    <ul>
     <li>Field Label</li>
     <li>Property Name*</li>
     <li>Description</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Asset Last Modified ?????</td>
   <td>Date the asset was last modified.<br /> </td>
   <td>A customized predicate, based on the Date Predicate.</td>
  </tr>
  <tr>
   <td>Range Options ???</td>
   <td>A specific search predicate for Assets and the same as common Slider Predicate. Is still available due to backward compatibilty issues.</td>
   <td>
    <ul>
     <li>Field Label</li>
     <li>Property Name*</li>
     <li>Option Path</li>
     <li>Description</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Tag </td>
   <td>Search assets based on tags. You can configure the Path property to populate various tags in the Tags list.</td>
   <td>
    <ul>
     <li>Field Label</li>
     <li>Property Name*</li>
     <li>Option Path</li>
     <li>Description</li>
    </ul> </td>
  </tr>
-->

>[!NOTE]
>
>일반적인 검색 조건은에서 정의됩니다.
>  `/libs/cq/gui/components/common/admin/customsearch/searchpredicates`
>
>이 정보는 참조용이므로 `/libs`을 변경할 수 없습니다.

<!--
>* Search predicates related only to siteadmin (classic UI) are located under:
> `/libs/cq/gui/components/siteadmin/admin/searchpanel/searchpredicates`
>   * These are deprecated and only available for backward compatibility.
>
-->

### 설명 설정 {#predicate-settings}

조건자에 따라 다음 설정을 포함하여 구성에 사용할 수 있습니다.

* **필드 레이블**

   축소 가능한 헤더 또는 조건부의 필드 레이블로 표시되는 레이블입니다.

* **설명**

   사용자에 대한 설명 세부 사항입니다.

* **자리 표시자**

   필터링 텍스트를 입력하지 않은 경우 빈 텍스트 또는 조건자의 자리 표시자입니다.

* **속성 이름**

   검색할 속성입니다. 상대 경로를 사용하고 와일드카드 `*/*/*` 은 `jcr:content` 노드에 상대적인 속성 깊이를 지정합니다(각 별표는 하나의 노드 수준을 나타냅니다).

   `jcr:content` 노드에서 `x` 속성이 있는 리소스의 첫 번째 수준 하위 노드에서만 검색하려면 `*/jcr:content/x` 를 사용하십시오

* **속성 깊이**

   리소스 내에서 해당 속성을 검색할 최대 깊이입니다. 따라서 자식의 수준이 지정된 깊이와 같을 때까지 리소스 및 재귀 자식에 대해 해당 속성에 대한 검색을 수행할 수 있습니다.

* **속성 값**

   속성 값은 절대 문자열 또는 표현식 언어로서 사용됩니다.예: `cq:Page` 또는

   `${empty requestPathInfo.suffix ? "/content" : requestPathInfo.suffix}`.

* **범위 텍스트**

   **날짜 범위** 조건부의 범위 필드의 레이블입니다.

* **옵션 경로**

   사용자는 설명 설정 탭에서 경로 브라우저 를 사용하여 경로를 선택할 수 있습니다. **+** 아이콘을 선택한 후 선택 사항을 유효한 옵션 목록에 추가합니다(그런 다음 필요한 경우 제거하려면 **-** 아이콘).

   옵션은 다음 구조를 갖는 사용자가 만든 컨텐츠 노드입니다.

   `(jcr:primaryType = nt:unstructured, value (String), jcr:title (String))`

* **옵션 노드**
경로와 효과적으로 동일합니다 
**옵션 경로**. 이 경로만 공통 설명 필드에 있고 다른 경로도 자산에 대해 다릅니다.

* **단일**
선택If를 선택하면 옵션이 하나의 선택만 허용하는 확인란으로 렌더링됩니다. 실수로 선택한 경우 확인란을 선택 취소할 수 있습니다.

* **게시 및 Live Copy 속성 이름**
사이트 특정 조건자에 대한 게시 및 Live Copy 확인란의 레이블입니다.

* &amp;ast;**설정** 탭의 필드 레이블은 필수 필드이며 비워 두면 오류 메시지가 표시됩니다.

## 검색 Forms 구성 {#configuring-your-search-forms}

### 사용자 지정된 구성 만들기/열기 {#creating-opening-a-customized-configuration}

1. **도구**, **일반**, **Forms 검색**&#x200B;으로 이동합니다.

1. 사용자 지정할 구성을 선택합니다.
1. **편집** 아이콘을 사용하여 업데이트할 구성을 엽니다.
1. 새 사용자 지정을 사용하는 경우 [새 설명 필드를 추가하고 필요에 따라 설정](#add-edit-a-predicate-field-and-define-field-settings)을(를) 정의합니다. 기존 사용자 지정인 경우 기존 필드를 선택하고 [설정을 업데이트](#add-edit-a-predicate-field-and-define-field-settings)할 수 있습니다.
1. **완료**&#x200B;를 선택하여 구성을 저장합니다. 다음에 구성을 사용할 때 변경 사항이 표시될 수 있습니다.

   >[!NOTE]
   >
   >사용자 지정된 구성은 다음 아래에 적절히 저장됩니다.
   >
   >* `/apps/cq/gui/content/facets/<option>`
   >* `/apps/commerce/gui/content/facets/<option>`


### 설명 필드 추가/편집 및 필드 설정 정의 {#add-edit-a-predicate-field-and-define-field-settings}

필드를 추가하거나 편집하고 설정을 정의/업데이트할 수 있습니다.

1. [업데이트할 사용자 지정 ](#creating-opening-a-customized-configuration) 구성을 엽니다.
1. 새 필드를 추가하려면 **설명 선택** 탭을 열고 필요한 설명을 필요한 위치로 드래그합니다. 예를 들어 **날짜 범위 설명**:

   ![설명 추가](assets/csf-add-predicate.png)

1. 다음 여부에 따라 달라집니다.

   * 새 필드를 추가하고 있습니다.

      설명을 추가하면 **설정** 탭이 열리고 정의할 수 있는 속성이 표시됩니다.

   * 기존 설명을 업데이트하려는 경우:

      설명 필드(오른쪽)를 선택한 다음 **설정** 탭을 엽니다.
   예를 들어 **날짜 범위 설명**&#x200B;에 대한 설정이 있습니다.

   ![설명 수정](assets/csf-modify-predicate.png)

1. 필요에 따라 변경하고 **완료**&#x200B;로 확인합니다. 다음에 구성을 사용할 때 변경 사항이 표시될 수 있습니다.

### 검색 구성 미리 보기 {#previewing-the-search-configuration}

1. 미리 보기 아이콘을 선택합니다.

   ![미리 보기 아이콘](assets/csf-preview-icon.png)

1. 검색 양식이 해당 콘솔의 검색 열에 표시되는 대로 표시됩니다(완전히 확장됨).

   ![미리 보기 양식](assets/csf-preview-form.png)

1. **** 미리 보기를 닫아서 구성을 반환하고 완료합니다.

### 설명 필드 삭제 {#deleting-a-predicate-field}

1. [업데이트할 사용자 지정 ](#creating-opening-a-customized-configuration) 구성을 엽니다.
1. 설명 필드(오른쪽)를 선택하고 **설정** 탭을 연 다음 **삭제** 아이콘(왼쪽 아래)을 선택합니다.

   ![아이콘 삭제](assets/csf-delete-icon.png)

1. 대화 상자가 삭제 작업의 확인을 요청합니다.

1. **완료**&#x200B;로 이 작업과 다른 변경 사항을 확인합니다.

### 구성 삭제(기본값 복원) {#deleting-a-configuration-to-reinstate-the-default}

구성을 사용자 지정하고 나면 기본값이 재정의됩니다. 사용자 지정된 구성을 삭제하여 기본 구성을 재지정할 수 있습니다.

>[!NOTE]
>
>기본 구성은 삭제할 수 없습니다.

사용자 지정된 구성 삭제는 콘솔에서 수행됩니다.

1. 필요한 구성(예: **페이지 편집기(단락 검색)**)을 선택한 다음 도구 모음에서 **삭제** 아이콘을 선택합니다.

   ![기본값 복원](assets/csf-restore-default.png)

1. 사용자 지정된 구성이 삭제되고 기본 복원됩니다(콘솔에서 자물쇠 기호가 다시 나타나도록 표시됨).

### 옵션 설명 추가 {#adding-options-predicates}

옵션 설명(옵션, 옵션 속성)을 사용하여 검색할 항목을 구성할 수 있습니다. 일반적으로 페이지 아래에서 바로 검색할 때 사용됩니다.예를 들어, 페이지 노드의 속성입니다.

다음 예제(페이지를 만드는 데 사용된 템플릿에 따라 검색하기)는 관련 단계를 보여줍니다.

1. 검색할 속성을 정의하는 노드를 만듭니다.

   사용자가 사용할 수 있는 개별 옵션의 정의를 포함하는 루트 노드가 필요합니다.

   개별 옵션의 노드에는 속성이 필요합니다.

   * `jcr:title` - 검색 레일에 표시할 필드 레이블
   * `value` - 검색할 속성 값

   ![설명 정의](assets/csf-options-predicate-01.png)

   >[!NOTE]
   >
   >***은 `/libs` 경로에서 아무 것도 변경하지 않아야 합니다.***
   >
   >이는 다음 번에 인스턴스를 업그레이드할 때 `/libs` 컨텐츠를 덮어쓰게 되기 때문입니다(핫픽스 또는 기능 팩을 적용할 때 덮어쓸 수 있음).
   >
   >구성 및 기타 변경에 대해 권장되는 방법은 다음과 같습니다.
   >
   >1. `/libs`에 있는 필수 항목을 `/apps` 아래에 다시 만드십시오. 이 경우
   >1. `/libs/cq/gui/content/common/options/predicates`
   >1. `/apps.` 내에서 변경


1. **Forms 검색** 콘솔을 열고 업데이트할 구성을 선택합니다. 예: **사이트 관리자 검색 레일**. 그런 다음 **편집**&#x200B;을 선택합니다.

1. 구성에 따라 구성에 **Options** 또는 **Options 속성**&#x200B;을 추가합니다.
1. 필드를 업데이트합니다. 특히:

   * **속성 이름**

      대상 노드에서 검색할 노드 속성에 대해 지정합니다. 예:

      `jcr:content/cq:template`

   * **옵션 노드 경로**

      옵션이 있는 경로를 선택합니다. 예:

      `/apps/cq/gui/content/common/options/predicates/templatetype`
   ![옵션 설명](assets/csf-options-predicate-02.png)

1. **완료**&#x200B;를 선택하여 구성을 저장합니다.
1. 적절한 콘솔(이 예에서 **사이트**)로 이동하고 **검색 - 필터** 레일을 엽니다. 새로 정의된 검색 양식과 다양한 옵션이 표시됩니다. 필요한 옵션을 선택하여 검색 결과를 확인합니다.

   ![사용 중인 옵션](assets/csf-options-usage.png)


## 사용자 권한 {#user-permissions}

다음 표에는 검색 양식에서 편집, 삭제 및 미리 보기 작업을 수행하는 데 필요한 권한이 나와 있습니다.

<table>
 <thead>
  <tr>
   <td><strong>작업</strong></td>
   <td><strong>권한</strong></td>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td>편집 </td>
   <td>읽기, <code>/apps </code>노드에 대한 쓰기 권한.</td>
  </tr>
  <tr>
   <td>삭제</td>
   <td><code>/apps</code> 노드에 대한 읽기, 쓰기, 삭제 권한</td>
  </tr>
  <tr>
   <td>미리 보기</td>
   <td><code>/var/dam/content</code> 노드에 대한 읽기, 쓰기, 삭제 권한.<br /> 노드에 대한 읽기, 쓰기  <code>/apps</code> 권한.</td>
  </tr>
 </tbody>
</table>
