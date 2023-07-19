---
title: 검색
description: 포괄적인 검색으로 신속하게 콘텐츠 찾기
exl-id: 8a799e9a-1461-4e79-ae90-1978af6cf0ed
source-git-commit: 635f4c990c27a7646d97ebd08b453c71133f01b3
workflow-type: ht
source-wordcount: '491'
ht-degree: 100%

---

# 검색 {#search-feature}

AEM의 작성 환경에서는 리소스 유형에 따라 콘텐츠를 검색하기 위한 다양한 메커니즘을 제공합니다.

## 검색 기본 사항 {#search-basics}

검색은 상단 도구 모음에서 사용할 수 있습니다.

![검색 아이콘](/help/sites-cloud/authoring/assets/search-icon.png)

검색 레일을 사용하면 다음 작업을 할 수 있습니다.

* 특정 키워드, 경로 또는 태그를 검색합니다
* 리소스별 기준(예: 수정한 날짜, 페이지 상태, 파일 크기 등)에 따라 필터링합니다.
* 위의 기준에 따라 [저장된 검색](#saved-searches)을 정의하고 사용합니다

>[!NOTE]
>
>검색 레일이 표시될 때마다 핫키 `/`(슬래시)를 사용하여 검색을 호출할 수 있습니다.

## 검색 및 필터링 {#search-and-filter}

리소스를 검색하고 필터링하려면:

1. **검색**(도구 모음에 돋보기가 표시됨)을 열고 검색어를 입력합니다. 제안 사항이 만들어지고 선택할 수 있습니다.

   ![검색어](/help/sites-cloud/authoring/assets/search-term.png)

   기본적으로 검색 결과는 현재 위치(콘솔 및 관련 리소스 유형)로 제한됩니다.

   ![검색 위치](/help/sites-cloud/authoring/assets/search-term-location.png)

1. 필요한 경우 위치 필터를 제거(제거할 필터에서 **X** 선택)하여 모든 콘솔/리소스 유형에서 검색할 수 있습니다.
1. 콘솔 및 관련 리소스 유형에 따라 그룹화된 결과가 표시됩니다.

   필수 리소스 유형(예: **모든 사이트 보기**)을 선택하여 드릴다운하거나 추가 작업을 위해 특정 리소스를 선택할 수 있습니다.

   ![검색 결과](/help/sites-cloud/authoring/assets/search-results.png)

1. 추가로 드릴다운하려면 레일 기호(왼쪽 상단)를 선택하여 사이드 패널 **필터 및 옵션**&#x200B;을 엽니다.

   ![레일 버튼](/help/sites-cloud/authoring/assets/rail-button.png)

   리소스 유형에 따라 검색에 미리 정의된 검색/필터 조건이 표시됩니다.

   사이드 패널에서 다음을 선택할 수 있습니다.

   * 저장된 검색
   * 검색 디렉터리
   * 태그
   * 검색 기준(예: 수정한 날짜, 게시 상태, Live Copy 상태)

   >[!NOTE]
   >
   >검색 기준은 다음과 같이 다양할 수 있습니다.
   >
   >* 선택한 리소스 유형에 따라(예: 자산 및 커뮤니티) 기준이 세분화됩니다.
   >* 검색 양식과 같은 인스턴스는 AEM 내의 위치에 맞게 사용자 정의할 수 있습니다.

<!--
  >* Your instance as the [Search Forms](/help/sites-administering/search-forms.md) can be customized (appropriate to the location within AEM).
  -->

![검색 사이드 패널](/help/sites-cloud/authoring/assets/search-side-panel.png)

1. 검색어를 추가할 수도 있습니다.

1. **X**&#x200B;를 클릭하여(오른쪽 상단) **검색**&#x200B;을 닫습니다.

>[!NOTE]
>
>검색 기준은 검색 결과에서 항목을 선택해도 유지됩니다.
>
>검색 결과 페이지에서 항목을 선택하고, 브라우저의 뒤로 버튼을 사용하여 검색 페이지로 돌아가도 검색 기준은 유지됩니다.

## 저장된 검색 {#saved-searches}

다양한 패싯별로 검색할 수 있을 뿐만 아니라 이후 단계에서 검색하여 사용할 수 있게 특정 검색 구성을 저장할 수도 있습니다.

1. 검색 기준을 정의하고 **저장**&#x200B;을 선택합니다.

   ![검색 저장](/help/sites-cloud/authoring/assets/search-side-panel.png)

1. 이름을 지정한 다음 **저장**&#x200B;을 사용하여 확인합니다.

   ![이름으로 검색 저장](/help/sites-cloud/authoring/assets/search-save-name.png)

1. 다음에 검색 패널에 액세스할 때 선택기에서 저장된 검색을 사용할 수 있습니다.

   ![저장된 검색](/help/sites-cloud/authoring/assets/saved-searches.png)

1. 저장했으면 다음과 같은 작업을 수행할 수 있습니다.

   * **x**(저장된 검색 이름에 대해)를 사용하여 새 쿼리를 시작합니다(저장된 검색 자체는 삭제되지 않음).
   * **저장된 검색을 편집**&#x200B;하고, 검색 조건을 변경한 다음 다시 **저장**&#x200B;합니다.

검색 패널 하단에서 저장된 검색을 선택한 다음 **저장된 검색 편집**&#x200B;을 클릭하여 저장된 검색을 수정할 수 있습니다.

![저장된 검색 수정](/help/sites-cloud/authoring/assets/saved-searches-modify.png)
