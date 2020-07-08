---
title: 검색 양식 구성
description: Adobe Experience Manager에 대한 검색 양식을 Cloud Service으로 구성
translation-type: tm+mt
source-git-commit: 23349f3350631f61f80b54b69104e5a19841272f
workflow-type: tm+mt
source-wordcount: '2030'
ht-degree: 15%

---


# 검색 양식 구성 {#configuring-search-forms}

Cloud Service의 Adobe Experience Manager은 강력한 [검색](/help/sites-cloud/authoring/getting-started/search.md) 메커니즘을 제공합니다.

이와 함께 컨텐츠를 필터링하는 데 도움이 되는 사전 정의된 옵션 세트도 있습니다. 이러한 보류 중인 패싯은 **수정한 날짜**, **게시 상태**&#x200B;또는 **Livecopy 상태** 와 같은 사전 정의된패싯으로 필요한 리소스로 빠르게 드릴다운할 수 있도록 도와줍니다.

![검색 및 필터 사용](assets/csf-usage.png)

다음과 같은 목적을 통해 컨텐츠를 빠르고 손쉽게 찾을 수 있습니다.

* [검색 및 필터](/help/sites-cloud/authoring/getting-started/search.md#search-and-filter)
* [레일 선택기](/help/sites-cloud/authoring/getting-started/basic-handling.md#rail-selector)
* 자산 [브라우저](/help/sites-cloud/authoring/fundamentals/environment-tools.md#assets-browser) (페이지 편집 시)

>[!NOTE]
>
>기본 [컨텐츠 검색 및 인덱싱](/help/operations/indexing.md) 서비스를 구성할 수 있습니다.

양식 **검색**&#x200B;기능을 사용하면 특정 요구 사항에 따라 이러한 패널을 사용자 정의하고 확장할 수 있습니다.

검색 **양식** 은 결합하고 정의할 수 있는 [예측](#predicates-and-their-settings) 항목을 즉시 제공합니다. 이러한 양식 [을 구성하기 위한 대화 상자는 다음을 통해 액세스할](#configuring-your-search-forms) 수 있습니다.

* **도구**

   * **일반**

      * **검색 양식**

## 기본 양식 {#default-forms}

양식 **검색** 콘솔에 처음 액세스하면 모든 구성에 자물쇠 기호가 있음을 확인할 수 있습니다. 이는 해당 구성이 기본(기본) 구성이며 삭제할 수 없음을 나타냅니다. 사용자 정의 및 저장했으면 잠금이 사라집니다. 사용자 지정된 구성을 [삭제하면 이](#deleting-a-configuration-to-reinstate-the-default)지표가 다시 나타납니다. 이 경우 기본(및 자물쇠 표시기)이 복원됩니다.

![검색 양식 개요 구성](assets/csf-overview.png)

사용 가능한 기본 구성(알파벳순 목록)은 다음과 같습니다.

* **자산 관리자 검색 레일:**

* **페이지 편집기(문서 검색):**

* **페이지 편집기(경험 조각 검색):**

* **페이지 편집기(이미지 검색):**

* **페이지 편집기(원고 검색):**

* **페이지 편집기(페이지 검색):**

* **페이지 편집기(단락 검색):**

* **페이지 편집기(제품 검색):**

* **페이지 편집기(Scene7 검색)**:

* **페이지 편집기(비디오 검색)**:

* **프로젝트 관리자 검색 레일:**

* **프로젝트 번역 검색 레일:**

* **사이트 관리자 검색 레일**:

* **코드 조각 관리자 검색 레일**:

* **Stock 관리자 검색 레일**:

>[!NOTE]
>
>자산 관련 검색 양식에 대한 자세한 내용은 [자산 - 검색 패싯을 참조하십시오.](/help/assets/search-facets.md)


## 설명 및 설정 {#predicates-and-their-settings}

### 예측 {#predicates}

구성에 따라 다음 예측자를 사용할 수 있습니다.

<table>
 <tbody>
  <tr>
   <th>설명</th>
   <th>목적</th>
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
   <td>특정 체크아웃 상태의 자산을 검색합니다.</td>
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
   <td>작성자가 특정 구성 요소가 있는 페이지를 검색/필터링할 수 있습니다. For example an image gallery.<br /> </td>
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
   <td>날짜 속성에 대해 지정된 범위 내에서 만들어진 리소스를 검색합니다. 검색 패널에서 시작 날짜와 종료 날짜를 지정할 수 있습니다.</td>
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
   <td>파일/MIME 형식을 기반으로 자산을 검색합니다.</td>
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
   <td>전체 텍스트 검색에 대한 검색 조건입니다. 이 연산자는 'jcr:contains' 연산자와 매핑됩니다.</td>
   <td>
    <ul>
     <li>자리 표시자</li>
     <li>속성 이름</li>
     <li>설명</li>
    </ul> </td>
  </tr>
  <tr>
   <td>그룹</td>
   <td>그룹에 대한 검색 설명(인사이트 술어 내에서만 사용됨).</td>
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
   <td>여러 예측자로 구성된 복잡한 조건자입니다.
    <ul>
     <li>그룹</li>
     <li>범위</li>
     <li>옵션</li>
    </ul> 
   </td>
  </tr>
  <tr>
   <td>컬렉션 구성원</td>
   <td>컬렉션의 구성원인 자산 검색</td>
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
   <td><p>옵션은 사용자가 만든 컨텐츠 노드입니다.</p> <p>자세한 <a href="#addinganoptionspredicate">내용은 옵션 설명</a> 추가를 참조하십시오.</p> </td>
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
   <td>옵션 속성을 하나 이상 검색합니다.</td>
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
   <td>경로 필터. 사용자에게 표시되지 않습니다.</td>
   <td>
    <ul>
     <li>속성 이름('path')</li>
     <li>속성 값('/content/dam')</li>
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
   <td>지정된 범위 내에 있는 리소스를 검색합니다. 검색 패널에서 범위에 대한 최소 및 최대 값을 지정할 수 있습니다.</td>
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
   <td>작성의 상대 날짜를 기준으로 리소스를 필터링합니다. 예를 들어 1주 전, 1개월 전</td>
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
   <td>슬라이더 기능으로 범위 술어를 확장한 일반적인 검색 조건자입니다. 검색된 속성의 값은 슬라이더 한도 사이여야 합니다.</td>
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
   <td>여러 예측자로 구성된 복잡한 조건자입니다.
    <ul>
     <li>승인 상태</li>
     <li>체크아웃 상태</li>
    </ul> 
   </td>
  </tr>
  <tr>
   <td>태그</td>
   <td>태그를 기반으로 검색</td>
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
>일반적인 검색 예측자는
>  `/libs/cq/gui/components/common/admin/customsearch/searchpredicates`
>
>이 정보는 참조용이므로 변경할 수 없습니다 `/libs`.

<!--
>* Search predicates related only to siteadmin (classic UI) are located under:
> `/libs/cq/gui/components/siteadmin/admin/searchpanel/searchpredicates`
>   * These are deprecated and only available for backward compatibility.
>
-->

### 설명 설정 {#predicate-settings}

조건자에 따라 다음과 같은 설정을 선택할 수 있습니다.

* **필드 레이블**

   축소 가능한 헤더 또는 술어의 필드 레이블로 표시되는 레이블입니다.

* **설명**

   사용자에 대한 설명 세부 정보입니다.

* **자리 표시자**

   필터링 텍스트를 입력하지 않은 경우 빈 텍스트 또는 술어의 자리 표시자입니다.

* **속성 이름**

   검색할 속성입니다. 상대 경로를 사용하고 와일드카드는 노드를 기준으로 속성의 깊이를 `*/*/*` `jcr:content` 지정합니다(각 별표는 한 노드 수준을 나타냅니다).

   노드의 속성이 있는 리소스의 첫 번째 수준 하위 노드에서만 `x` `jcr:content` 검색하려는 경우 `*/jcr:content/x`

* **속성 깊이**

   리소스 내에서 해당 속성을 검색하는 최대 깊이입니다. 따라서 하위 수준이 지정된 깊이와 같아지기까지 리소스 및 재귀적 자식에 대한 검색을 수행할 수 있습니다.

* **속성 값**

   절대 문자열 또는 표현식 언어로 된 속성 값 예를 들어, `cq:Page` 또는

   `${empty requestPathInfo.suffix ? "/content" : requestPathInfo.suffix}`.

* **범위 텍스트**

   날짜 범위 설명 **에 있는 범위 필드의** 레이블입니다.

* **옵션 경로**

   술어 설정 탭에서 경로 브라우저를 사용하여 경로를 선택할 수 있습니다. After select the **+** icon is used to add the selection to the list of valid options (then the **-** icon to remove if required).

   옵션은 다음 구조를 갖는 사용자가 만든 컨텐츠 노드입니다.

   `(jcr:primaryType = nt:unstructured, value (String), jcr:title (String))`

* **옵션 노드 경로**&#x200B;는 **옵션 경로**&#x200B;와 효과적으로 동일하며, 이 경계는 공통 술어 필드에만 있고 다른 경계는 자산에 한정됩니다.
**단일 선택**&#x200B;이 선택된 경우 옵션이 하나의 선택만 허용하는 확인란으로 렌더링됩니다. 실수로 선택한 경우 확인란을 선택 취소할 수 있습니다.

* **게시 및 Live Copy 속성 이름**&#x200B;사이트 특정 술어에 대한 게시 및 Live Copy 확인란의 레이블입니다.

* &amp;ast; 설정 **** 탭의 필드 레이블에는 필드가 필수이며 비워 두면 오류 메시지가 표시됩니다.

* 검색 양식 구성 {#configuring-your-search-forms}**

## 사용자 지정된 구성 만들기/열기 {#creating-opening-a-customized-configuration}

### 도구, **일반**, **검색 양식**&#x200B;으로 **이동합니다**.

1. 사용자 정의할 구성을 선택합니다.************

1. 편집 **** 아이콘을 사용하여 업데이트를 위한 구성을 엽니다.
1. 새로운 사용자 지정 기능을 사용할 경우 새 설명 필드를 [추가하고 필요에 따라 설정을](#add-edit-a-predicate-field-and-define-field-settings) 정의할 수 있습니다. 기존 사용자 지정 시 기존 필드를 선택하고 설정을 [업데이트할 수 있습니다](#add-edit-a-predicate-field-and-define-field-settings).
1. Select **Done** to save the configuration. 구성은 다음에 볼 수 있습니다.[](#add-edit-a-predicate-field-and-define-field-settings)
1. [!NOTE]**

   >[!NOTE]사용자 지정된 구성은 다음 위치에 저장됩니다.
   >
   >`/apps/cq/gui/content/facets/<option>`
   >
   >* `/apps/commerce/gui/content/facets/<option>`
   >* 설명 필드 추가/편집 및 필드 설정 정의 {#add-edit-a-predicate-field-and-define-field-settings}


### 필드를 추가하거나 편집하고 설정을 정의/업데이트할 수 있습니다.{#add-edit-a-predicate-field-and-define-field-settings}

[업데이트할 사용자 지정된 구성을](#creating-opening-a-customized-configuration) 엽니다.

1. 새 필드를 추가하려면 설명 선택 탭 **을** 열고 필요한 술어를 필요한 위치로 드래그합니다. 예를 들어 날짜 범위 **설명**:
1. ![설명 추가](assets/csf-add-predicate.png)****

   ![다음 여부에 따라 다름:](assets/csf-add-predicate.png)

1. 새 필드를 추가하고 있습니다.

   * 조건자를 추가하면 **설정** 탭이 열리고 정의할 수 있는 속성이 표시됩니다.

      기존 조건자를 업데이트하려는 경우:****

   * 설명 필드(오른쪽)를 선택한 다음 설정 **탭을** 엽니다.

      예를 들어 날짜 범위 설명 **에 대한 설정은 다음과 같습니다**.
   ![설명 수정](assets/csf-modify-predicate.png)

   필요에 따라 변경하고 완료를 **확인합니다**. 구성은 다음에 볼 수 있습니다.

1. 검색 구성 미리 보기 {#previewing-the-search-configuration}**

### 미리 보기 아이콘을 선택합니다.{#previewing-the-search-configuration}

1. ![미리 보기 아이콘](assets/csf-preview-icon.png)

   ![그러면 해당 콘솔의 검색 열에 표시될 검색 양식이 표시됩니다(완전히 확장됨).](assets/csf-preview-icon.png)

1. ![미리 보기 양식](assets/csf-preview-form.png)

   **미리 보기를 닫아서** 구성을 다시 시작하고 완료합니다.

1. 설명 필드 삭제 {#deleting-a-predicate-field}**

### [업데이트할 사용자 지정된 구성을](#creating-opening-a-customized-configuration) 엽니다.

1. 설명 필드(오른쪽)를 선택하고 **설정** 탭을 연 다음 **삭제** 아이콘(왼쪽 아래)을 선택합니다.
1. ![삭제 아이콘](assets/csf-delete-icon.png)****

   ![대화 상자가 삭제 작업의 확인을 요청합니다.](assets/csf-delete-icon.png)

1. 완료를 사용하여 이 및 기타 모든 변경 사항을 **확인합니다**.

1. 구성 삭제(기본값 복원) {#deleting-a-configuration-to-reinstate-the-default}**

### 구성을 사용자 지정했으면 기본값이 무시됩니다. 사용자 지정된 구성을 삭제하여 기본 구성을 다시 지정할 수 있습니다.{#deleting-a-configuration-to-reinstate-the-default}

[!NOTE]

>[!NOTE]기본 구성은 삭제할 수 없습니다.
>
>콘솔에서 사용자 지정된 구성 삭제가 수행됩니다.

필요한 구성(예: **페이지 편집기(단락 검색)**)을 선택한 다음 도구 모음에서 **삭제** 아이콘을 선택합니다.

1. ![기본값 복원](assets/csf-restore-default.png)****

   ![사용자 지정된 구성이 삭제되고 기본 복원됩니다(콘솔에 자물쇠 기호가 다시 표시됨).](assets/csf-restore-default.png)

1. 옵션 설명 추가 {#adding-options-predicates}

### 옵션 설명(옵션, 옵션 속성)을 사용하면 검색할 항목을 구성할 수 있습니다. 일반적으로 페이지 바로 아래에서 항목을 검색하는 데 사용됩니다. 예를 들어 페이지 노드의 속성입니다.{#adding-options-predicates}

다음 예제(페이지를 만드는 데 사용된 템플릿에 따라 검색하기)에서는 관련 단계를 보여 줍니다.

검색할 속성을 정의하는 노드를 만듭니다.

1. 사용자가 사용할 수 있는 개별 옵션에 대한 정의를 포함하는 루트 노드가 필요합니다.

   개별 옵션에 대한 노드에는 속성이 필요합니다.

   `jcr:title` - 검색 레일에 표시할 필드 레이블

   * `value` - 검색할 속성 값
   * ![설명 정의](assets/csf-options-predicate-01.png)

   [!NOTE]](assets/csf-options-predicate-01.png)

   >경로 ***에서 어떤 것도 변경하지*** 않아야 `/libs` 합니다.
   >
   >이는 다음에 인스턴스를 업그레이드할 때 `/libs` 의 컨텐츠를 덮어쓰고, 핫픽스 또는 기능 팩을 적용할 때 덮어쓸 수 있기 때문입니다.***`/libs`
   >
   >구성 및 기타 변경에 대해 권장되는 방법은 다음과 같습니다.`/libs`
   >
   >에 있는 것처럼 아래 `/libs`에서 필요한 항목을 다시 만듭니다 `/apps`. 이 경우:
   >
   >1. `/libs/cq/gui/content/common/options/predicates``/apps`
   >1. Make any changes within `/apps.`
   >1. 양식 **검색** 콘솔을 열고 업데이트할 구성을 선택합니다. 예: **사이트 관리자 검색 레일**. 그런 다음 **편집을 선택합니다**.


1. 구성에 따라 구성에 **옵션** 또는 **옵션 속성** 을 추가합니다.****

1. 특히 필드를 업데이트합니다.********
1. **속성 이름**

   * **대상 노드에서 검색할 노드 속성에 대해 지정합니다. 예:**

      `jcr:content/cq:template`

      **옵션 노드 경로**

   * **옵션을 저장할 경로를 선택합니다. 예:**

      `/apps/cq/gui/content/common/options/predicates/templatetype`

      ![옵션 설명](assets/csf-options-predicate-02.png)
   Select **Done** to save your configuration.

1. 적절한 콘솔(이 예: **사이트**)으로 이동하고 **검색 - 필터** 레일을엽니다. 새롭게 정의된 검색 양식과 다양한 옵션이 표시됩니다. 필요한 옵션을 선택하여 검색 결과를 확인합니다.
1. ![사용 중인 옵션](assets/csf-options-usage.png)****

   사용자 권한 {#user-permissions}](assets/csf-options-usage.png)


## 다음 표에는 검색 양식에서 편집, 삭제 및 미리 보기 작업을 수행하는 데 필요한 권한이 나와 있습니다.{#user-permissions}



<table>
 <thead>
  <tr>
   </td>
   </td>
  </tr>
 </thead>
 <tbody>
  <tr>
   </td>
   </td>
  </tr>
  <tr>
   </td>
   </td>
  </tr>
  <tr>
   </td>
   <td>Read, Write, Delete permissions on the <code>/var/dam/content</code> node.<br /> Read, Write permissions on the <code>/apps</code> node.</td>
  </tr>
 </tbody>
</table>
