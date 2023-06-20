---
title: 검색 양식 구성
description: Adobe Experience Manager as a Cloud Service에 대해 Forms 검색을 구성하는 중입니다.
exl-id: b06649c4-cc91-44e3-8699-00e90140b90d
source-git-commit: f7525b6b37e486a53791c2331dc6000e5248f8af
workflow-type: tm+mt
source-wordcount: '2037'
ht-degree: 16%

---

# 검색 양식 구성 {#configuring-search-forms}

Adobe Experience Manager as a Cloud Service에는 강력한 [검색](/help/sites-cloud/authoring/getting-started/search.md) 메커니즘.

이와 함께 콘텐츠를 필터링하는 데 도움이 되는 사전 정의된 옵션 세트도 있습니다. 여기에는 다음과 같이 사전 정의된 패싯이 포함됩니다. **수정한 날짜**, **게시 상태**, 또는 **라이브 카피 상태** 필요한 리소스로 신속하게 드릴다운할 수 있도록 지원합니다.

![검색 및 필터 사용](assets/csf-usage.png)

이러한 목표를 함께 사용하면 다음 위치에서 빠르고 쉽게 콘텐츠를 찾을 수 있습니다.

* [검색 및 필터링](/help/sites-cloud/authoring/getting-started/search.md#search-and-filter)
* [레일 선택기](/help/sites-cloud/authoring/getting-started/basic-handling.md#rail-selector)
* 다음 [에셋 브라우저](/help/sites-cloud/authoring/fundamentals/environment-tools.md#assets-browser) (페이지 편집 시)

>[!NOTE]
>
>기본 항목을 구성할 수 있습니다. [콘텐츠 검색 및 색인화](/help/operations/indexing.md) 서비스.

사용 **Forms 검색**, 특정 요구 사항에 따라 이러한 패널을 사용자 정의하고 확장할 수 있습니다.

다음 **Forms 검색** 기본 제공 [술어](#predicates-and-their-settings) 을 사용하여 를 결합하고 정의할 수 있습니다. 다음 [이러한 양식을 구성하기 위한 대화 상자](#configuring-your-search-forms) 을 통해 액세스할 수 있습니다.

* **도구**
   * **일반**
      * **검색 양식**

## 기본 Forms {#default-forms}

에 처음 액세스하면 **Forms 검색** 콘솔 모든 구성에 자물쇠 기호가 있는 것을 볼 수 있습니다. 이는 해당 구성이 기본(기본) 구성이며 삭제할 수 없음을 나타냅니다. 구성을 사용자 지정하고 저장하면 잠금 기능이 사라집니다. 다음 작업을 수행하면 다시 나타납니다. [사용자 지정된 구성 삭제](#deleting-a-configuration-to-reinstate-the-default), 이 경우 기본값(및 자물쇠 표시기)이 복원됩니다.

![검색 양식 구성 개요](assets/csf-overview.png)

사용할 수 있는 기본 구성(알파벳순으로 나열됨)은 다음과 같습니다.

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
>에셋 관련 검색 양식에 대한 자세한 내용은 [에셋 - 검색 패싯](/help/assets/search-facets.md)


## 술어 및 설정 {#predicates-and-their-settings}

### 술어 {#predicates}

구성에 따라 다음 술어를 사용할 수 있습니다.

<table>
 <tbody>
  <tr>
   <th>조건자</th>
   <th>용도</th>
   <th>설정</th>
  </tr>
  <tr>
   <td>분석</td>
   <td>분석 기반 데이터를 표시할 때 사이트 브라우저의 검색/필터 기능입니다. Analytics 검색 필터가 매핑된 사용자 지정 분석 열과 일치하도록 로드됩니다.</td>
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
   <td>작성자</td>
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
   <td>특정 사용자가 체크아웃한 에셋을 검색합니다.</td>
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
   <td>특정 체크아웃 상태의 에셋을 검색합니다.</td>
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
   <td>작성자는 특정 구성 요소가 있는 페이지를 검색/필터링할 수 있습니다. 예를 들어 이미지 갤러리가 있습니다.<br /> </td>
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
   <td>날짜 속성에 대해 지정된 범위 내에서 생성된 리소스를 검색합니다. 검색 패널에서 시작 및 종료 날짜를 지정할 수 있습니다.</td>
   <td>
    <ul>
     <li>필드 레이블</li>
     <li>자리 표시자</li>
     <li>속성 이름*</li>
     <li>범위 텍스트(시작)*</li>
     <li>범위 텍스트(종료)*</li>
     <li>설명</li>
    </ul> </td>
  </tr>
  <tr>
   <td>만료 상태</td>
   <td>만료 상태를 기반으로 리소스를 검색합니다.</td>
   <td>
    <ul>
     <li>필드 레이블</li>
     <li>속성 이름*</li>
     <li>설명</li>
    </ul> </td>
  </tr>
  <tr>
   <td>파일 크기</td>
   <td>크기에 따라 리소스를 필터링합니다.</td>
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
   <td>파일/MIME 유형을 기반으로 자산을 검색합니다.</td>
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
   <td>전체 텍스트 검색에 대한 검색 조건자입니다. "jcr:contains" 연산자와 매핑됩니다.</td>
   <td>
    <ul>
     <li>자리 표시자</li>
     <li>속성 이름</li>
     <li>설명</li>
    </ul> </td>
  </tr>
  <tr>
   <td>그룹</td>
   <td>그룹에 대한 검색 조건자(Insights 조건자 내에서만 사용됨).</td>
   <td>
    <ul>
     <li>필드 레이블</li>
     <li>설명</li>
    </ul> </td>
  </tr>
  <tr>
   <td>숨겨진 필터</td>
   <td>사용자에게 표시되지 않는 속성 및 값에 대한 필터입니다.</td>
   <td>
    <ul>
     <li>속성 이름*</li>
     <li>속성 값*</li>
     <li>설명</li>
    </ul> </td>
  </tr>
  <tr>
   <td>인사이트</td>
   <td>선택한 Insights 매개 변수에 따라 검색합니다.</td>
   <td>여러 술어로 구성된 복잡한 술어입니다.
    <ul>
     <li>그룹</li>
     <li>범위</li>
     <li>옵션</li>
    </ul> 
   </td>
  </tr>
  <tr>
   <td>컬렉션 구성원</td>
   <td>컬렉션의 멤버인 에셋 검색</td>
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
   <td><p>옵션은 사용자가 만든 콘텐츠 노드입니다.</p> <p>다음을 참조하십시오 <a href="#addinganoptionspredicate">옵션 설명 추가</a> 추가 정보.</p> </td>
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
   <td>옵션 속성</td>
   <td>하나 이상의 옵션 속성을 검색합니다.</td>
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
   <td>미리 정의된 루트 경로에서 검색할 경로 브라우저를 제공합니다.</td>
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
   <td>사용자에게 표시되지 않는 경로의 필터입니다.</td>
   <td>
    <ul>
     <li>속성 이름('path')</li>
     <li>속성 값 (`/content/dam`)</li>
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
   <td>지정된 범위 내에 있는 리소스를 검색합니다. [검색] 패널에서 범위의 최소값과 최대값을 지정할 수 있습니다.</td>
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
   <td>만든 상대적 날짜를 기준으로 리소스를 필터링합니다. 예를 들어 1주 전, 1개월 전입니다.</td>
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
   <td>슬라이더 기능을 사용하여 범위 술어를 확장하는 일반적인 검색 술어입니다. 에서 검색된 속성 값은 슬라이더 제한 사이여야 합니다.</td>
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
   <td>여러 술어로 구성된 복잡한 술어입니다.
    <ul>
     <li>승인 상태</li>
     <li>체크아웃 상태</li>
    </ul> 
   </td>
  </tr>
  <tr>
   <td>태그</td>
   <td>태그를 기반으로 검색합니다.</td>
   <td>
    <ul>
     <li>필드 레이블</li>
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
>일반적인 검색 조건자는 다음에서 정의됩니다.
>  `/libs/cq/gui/components/common/admin/customsearch/searchpredicates`
>
>이 정보는 참조용이므로 변경할 수 없습니다. `/libs`.

<!--
>* Search predicates related only to siteadmin (classic UI) are located under:
> `/libs/cq/gui/components/siteadmin/admin/searchpanel/searchpredicates`
>   * These are deprecated and only available for backward compatibility.
>
-->

### 조건자 설정 {#predicate-settings}

술어에 따라 다음을 포함한 다양한 설정을 구성할 수 있습니다.

* **필드 레이블**

  접을 수 있는 헤더 또는 술어의 필드 레이블로 표시되는 레이블입니다.

* **설명**

  사용자에 대한 설명 세부 정보.

* **자리 표시자**

  필터링 텍스트가 입력되지 않은 경우 빈 텍스트 또는 술어 자리 표시자

* **속성 이름**

  검색할 속성입니다. 상대 경로와 와일드카드를 사용합니다 `*/*/*` 을(를) 기준으로 속성의 깊이를 지정합니다. `jcr:content` 노드(각 별표는 하나의 노드 레벨을 나타냅니다.)

  을(를) 가진 리소스의 첫 번째 수준 하위 노드에서만 검색하려면 `x` 다음에 대한 속성 `jcr:content` 노드 사용 `*/jcr:content/x`

* **속성 깊이**

  리소스 내에서 해당 속성을 검색할 수 있는 최대 깊이입니다. 따라서 자식 수준이 지정된 깊이와 같을 때까지 리소스 및 재귀 자식 항목에서 해당 속성을 검색할 수 있습니다.

* **속성 값**

  속성 값(절대 문자열 또는 표현식 언어). 예: `cq:Page` 또는

  `${empty requestPathInfo.suffix ? "/content" : requestPathInfo.suffix}`.

* **범위 텍스트**

  에 있는 범위 필드의 레이블 **날짜 범위** 조건자.

* **옵션 경로**

  사용자는 술어 설정 탭의 경로 브라우저를 사용하여 경로를 선택할 수 있습니다. 을(를) 선택한 후 **+** 아이콘을 사용하여 유효한 옵션 목록에 선택 항목을 추가한 다음 **-** 필요한 경우 제거할 아이콘입니다.

  옵션은 사용자가 만든 콘텐츠 노드로서 다음 구조를 갖습니다.

  `(jcr:primaryType = nt:unstructured, value (String), jcr:title (String))`

* **옵션 노드 경로**
와 효과적으로 동일 **옵션 경로**&#x200B;에서는 이 항목만 일반 술어 필드에 있으며, 다른 항목은 에셋에 따라 다릅니다.

* **단일 선택**
선택하면 옵션이 단일 선택 항목만 허용하는 확인란으로 렌더링됩니다. 잘못 선택한 경우 확인란을 선택 취소할 수 있습니다.

* **게시 및 라이브 카피 속성 이름**
Sites 특정 술어에 대한 게시 및 라이브 카피 확인란의 레이블입니다.

* 필드 레이블의 &amp;ast; **설정** 탭은 필드가 필수임을 의미하며 비워 두면 오류 메시지가 표시됩니다.

## 검색 Forms 구성 {#configuring-your-search-forms}

### 사용자 지정된 구성 만들기/열기 {#creating-opening-a-customized-configuration}

1. 다음으로 이동 **도구**, **일반**, **Forms 검색**.

1. 사용자 지정할 구성을 선택합니다.
1. 사용 **편집** 아이콘을 클릭하여 업데이트할 구성을 엽니다.
1. 새 사용자 지정의 경우 [새 술어 필드 추가 및 설정 정의](#add-edit-a-predicate-field-and-define-field-settings) 필요에 따라. 기존 사용자 지정의 경우 기존 필드를 선택하고 [설정 업데이트](#add-edit-a-predicate-field-and-define-field-settings).
1. 선택 **완료** 구성을 저장합니다. 다음 번에 구성을 사용하면 변경 사항을 볼 수 있습니다.

   >[!NOTE]
   >
   >사용자 지정된 구성은 아래에 (적절히) 저장됩니다.
   >
   >* `/apps/cq/gui/content/facets/<option>`
   >* `/apps/commerce/gui/content/facets/<option>`

### 술어 필드 추가/편집 및 필드 설정 정의 {#add-edit-a-predicate-field-and-define-field-settings}

필드를 추가 또는 편집하고 설정을 정의/업데이트할 수 있습니다.

1. [사용자 지정된 구성을 엽니다.](#creating-opening-a-customized-configuration) 업데이트용.
1. 새 필드를 추가하려면 **조건자 선택** 필요한 설명을 탭하고 필요한 위치로 드래그합니다. 예를 들어 **날짜 범위 조건자**:

   ![조건자 추가](assets/csf-add-predicate.png)

1. 다음 여부에 따라 달라집니다.

   * 새 필드를 추가하고 있습니다.

     술어를 추가한 후 **설정** 탭이 열리고 정의할 수 있는 속성이 표시됩니다.

   * 기존 술어를 업데이트하려고 합니다.

     술어 필드(오른쪽)를 선택한 다음 **설정** 탭.

   예를 들어, 다음에 대한 설정 **날짜 범위 조건자**:

   ![설명 수정](assets/csf-modify-predicate.png)

1. 필요에 따라 변경하고 확인합니다. **완료**. 다음 번에 구성을 사용하면 변경 사항을 볼 수 있습니다.

### 검색 구성 미리 보기 {#previewing-the-search-configuration}

1. 미리 보기 아이콘을 선택합니다.

   ![미리 보기 아이콘](assets/csf-preview-icon.png)

1. 검색 양식을 해당 콘솔의 검색 열에 표시(완전히 확장)한 대로 표시합니다.

   ![양식 미리 보기](assets/csf-preview-form.png)

1. **닫기** 구성을 반환하고 완료하는 미리보기.

### 술어 필드 삭제 {#deleting-a-predicate-field}

1. [사용자 지정된 구성을 엽니다.](#creating-opening-a-customized-configuration) 업데이트용.
1. 술어 필드(오른쪽)를 선택하고 **설정** 탭을 선택한 다음 **삭제** 아이콘(왼쪽 하단).

   ![삭제 아이콘](assets/csf-delete-icon.png)

1. 대화 상자에서 삭제 작업 확인을 요청합니다.

1. 을(를) 통해 이 변경 사항 및 기타 변경 사항을 확인합니다. **완료**.

### 구성 삭제(기본값 복원) {#deleting-a-configuration-to-reinstate-the-default}

구성을 사용자 정의하면 기본값이 재정의됩니다. 사용자 지정된 구성을 삭제하여 기본 구성을 복원할 수 있습니다.

>[!NOTE]
>
>기본 구성은 삭제할 수 없습니다.

사용자 정의된 구성을 삭제하는 작업은 콘솔에서 수행됩니다.

1. 필요한 구성 선택(예: **페이지 편집기(단락 검색)**) 그런 다음 **삭제** 아이콘(도구 모음):

   ![기본값 복원](assets/csf-restore-default.png)

1. 사용자정의된 구성이 삭제되고 기본값이 복원됩니다(콘솔에 자물쇠 기호가 다시 나타나는 것으로 표시됨).

### 옵션 술어 추가 {#adding-options-predicates}

옵션 술어(옵션, 옵션 속성)를 사용하면 검색할 항목을 구성할 수 있습니다. 일반적으로 페이지 바로 아래에서 무언가를 검색하는 데 사용됩니다(예: 페이지 노드의 속성).

페이지를 만드는 데 사용된 템플릿에 따라 검색할 수 있는 다음 예제는 관련 단계를 보여 줍니다.

1. 검색할 속성을 정의하는 노드를 만듭니다.

   사용자가 사용할 수 있는 개별 옵션의 정의를 포함하는 루트 노드가 필요합니다.

   개별 옵션의 노드에는 다음 속성이 필요합니다.

   * `jcr:title` - 검색 레일에 표시할 필드 레이블
   * `value` - 검색할 속성 값

   ![조건자 정의](assets/csf-options-predicate-01.png)

   >[!NOTE]
   >
   >본인 ***필수*** 의 아무 것도 변경하지 마십시오. `/libs` 경로.
   >
   >이는 의 콘텐츠가 `/libs` 는 다음에 인스턴스를 업그레이드할 때 덮어쓰기됩니다(또한 핫픽스 또는 기능 팩을 적용할 때 덮어쓰기될 수도 있음).
   >
   >구성 및 기타 변경에 권장되는 방법은 다음과 같습니다.
   >
   >1. 필요한 항목이 있는 대로 다시 만들기 `/libs`, 아래 `/apps`. 이 경우 다음에서:
   >1. `/libs/cq/gui/content/common/options/predicates`
   >1. 다음 범위 내에서 변경 `/apps.`

1. 를 엽니다. **Forms 검색** 콘솔을 클릭하고 업데이트할 구성을 선택합니다. 예를 들어, **사이트 관리자 검색 레일**. 그런 다음 을 선택합니다 **편집**.

1. 구성에 따라 **옵션** 또는 **Options 속성** 구성을 참조하십시오.
1. 필드를 업데이트합니다. 특히

   * **속성 이름**

     대상 노드에서 검색할 노드 속성을 지정합니다. 예:

     `jcr:content/cq:template`

   * **옵션 노드 경로**

     옵션이 있는 경로를 선택합니다. 예:

     `/apps/cq/gui/content/common/options/predicates/templatetype`

   ![옵션 조건자](assets/csf-options-predicate-02.png)

1. 선택 **완료** 구성을 저장합니다.
1. 적절한 콘솔로 이동합니다(이 예제에서는 **사이트**) 및 를 엽니다 **검색 - 필터** 레일. 다양한 옵션과 함께 새로 정의된 검색 양식이 표시됩니다. 필요한 옵션을 선택하여 검색 결과를 확인합니다.

   ![사용 중인 옵션](assets/csf-options-usage.png)


## 사용자 권한 {#user-permissions}

다음 표에는 검색 양식에서 편집, 삭제 및 미리 보기 작업을 수행하는 데 필요한 권한이 나열되어 있습니다.

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
   <td>읽기, 쓰기 권한 <code>/apps </code>노드.</td>
  </tr>
  <tr>
   <td>삭제</td>
   <td>읽기, 쓰기, 삭제 권한 <code>/apps</code> 노드</td>
  </tr>
  <tr>
   <td>미리보기</td>
   <td>읽기, 쓰기, 삭제 권한 <code>/var/dam/content</code> 노드.<br /> 읽기, 쓰기 권한 <code>/apps</code> 노드.</td>
  </tr>
 </tbody>
</table>
