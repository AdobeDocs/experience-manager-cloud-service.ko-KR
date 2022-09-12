---
title: CIF 작성 시작하기
description: CIF 작성 시작하기
exl-id: 0bef4d8c-0ad3-4ec8-ab08-8c83203b3b68
source-git-commit: 940a01cd3b9e4804bfab1a5970699271f624f087
workflow-type: tm+mt
source-wordcount: '805'
ht-degree: 2%

---

# AEM CIF 작성 시작하기 {#getting-started}

AEM CIF 작성에 대해 알아봅니다.

## 지금까지의 이야기 {#story-so-far}

이 AEM Content and Commerce 여정의 이전 문서에서, [AEM 콘텐츠 및 상거래에 대해 알아보기](/help/commerce-cloud/introduction.md), 헤드리스 CMS가 무엇인지 기본 이론을 배웠고 이제 AEM 컨텐츠 및 커머스 의 기본 개념을 이해해야 합니다.

이 문서는 이러한 기본 사항을 기반으로 합니다.

## 목표 {#objective}

이 문서는 콘텐츠 및 상거래 관련 작성에 CIF를 사용하는 방법을 이해하는 데 도움이 됩니다. 읽기 후에는 다음을 수행해야 합니다.

* 범용 편집기를 사용하여 CIF 작성의 개념 이해
* 제품 및 카테고리 선택기를 사용하여 AEM에서 제품 카탈로그 데이터에 액세스하는 방법
* 제품 조종실과 AEM Omnisearch를 사용하여 콘텐츠 및 상거래 데이터에 액세스하는 방법

## 범용 편집기에서 CIF 작성 {#cif-authoring}

CIF는 범용 편집기를 확장하여 컨텍스트를 종료하지 않고 실시간 제품 데이터에 액세스할 수 있습니다.

사이드 패널을 열고 드롭다운에서 &#39;Products&#39;를 선택합니다.
![제품 유형 선택](assets/asset-finder-overview.png)

제품 카탈로그를 찾아보거나 전체 텍스트 검색 필드를 사용하여 제품을 찾을 수 있습니다.
![제품 유형](assets/asset-finder-search.png)

제품 티저 구성 요소를 자동으로 만드는 페이지에서 바로 제품 삭제(예: 제품 티저, 제품 회전 메뉴)를 지원하는 구성 요소에 제품을 놓을 수 있습니다.

## 제품 및 카테고리 선택기 {#pickers}

상거래 구성 요소 또는 AEM 백오피스 대화 상자에서 제품 및 카테고리 데이터가 필요한 경우 AEM 작성자는 UI 요소인 선택기를 사용하여 제품 카탈로그 데이터를 편안하게 검색하고 선택할 수 있습니다.

### 제품 선택기

폴더 아이콘을 클릭하면 선택기 모달 UI(예: 제품 티저)가 열립니다
![제품 선택기](assets/product-picker-open.png)

제품은 왼쪽의 카탈로그 구조를 탐색하거나 검색하여 찾을 수 있습니다. 전체 텍스트 검색은 선택한 카테고리를 준수하며 검색 결과를 이 카테고리로 제한합니다.
![제품 선택기 폴더](assets/product-picker-folders.png)

변형을 포함한 제품은 모든 변형을 표시하기 위해 클릭할 수 있는 폴더 아이콘으로 표시됩니다.
![제품 선택기 변형](assets/product-picker-variants.png)
![제품 선택기 변형 열기](assets/product-picker-variants-open.png)

### 카테고리 선택기

제품 선택기와 같습니다. 폴더 아이콘을 클릭하면 선택기 모달 UI(예: 카테고리 회전판)가 열립니다
![카테고리 선택기](assets/category-picker-open.png)

왼쪽의 카탈로그 구조를 탐색하고 범주를 선택합니다.
![카테고리 선택기](assets/category-picker-folders.png)

## 제품 관리실 {#cockpit}

제품 조종실은 풍부한 모든 콘텐츠와 함께 제품 카탈로그에 빠르게 액세스할 수 있는 중앙 장소입니다. 다음 모듈 중 하나에서 컨텐츠로 제품 데이터를 보강하는 방법을 학습합니다. 이제 제품 데이터에 액세스하는 데 주력해 보겠습니다.

기본 메뉴에서 상거래 를 클릭하여 첨부된 모든 제품 카탈로그 목록을 확인합니다.
![상거래 메뉴 항목](assets/commerce-menu-item.png)

모든 연결 제품 카탈로그 목록이 표시됩니다.
![조종실 통합 카탈로그](assets/cockpit-Integrated-catalogs.png)

제품 카탈로그에는 기본적으로 모든 제품이 있는 모든 첫 번째 수준 카테고리가 표시됩니다. 카테고리를 클릭하면 해당 카테고리가 열리고 관련 제품 및 해당 제품을 포함한 하위 카테고리가 표시됩니다.
![조종실 제품 카탈로그](assets/cockpit-product-catalog.png)

속성 아이콘을 클릭하여 제품 속성을 열 수 있습니다. 제품 타일을 마우스로 가리키면 아이콘이 표시됩니다.
![조종실 제품 등록 정보](assets/cockpit-properties.png)

연결된 백엔드에서 데이터가 실시간으로 로드되므로 모든 제품 속성은 읽기 전용입니다. 제품 속성 변경은 레코드 시스템인 백엔드 시스템에서 수행해야 합니다. 탭 **변형** 에 변형이 있는 경우에만 나타납니다. 탭을 클릭하면 속성이 있는 모든 변형이 표시됩니다.
![조종식 제품 변형](assets/cockpit-properties-variants.png)

나머지 탭에는 제품과 연결된 모든 AEM 콘텐츠가 표시됩니다. 다음 모듈 중 하나에서 이러한 탭에 대해 설명합니다.

## AEM Omnisearch {#omnisearch}

Omnisearch를 사용하면 전체 텍스트 검색을 사용하여 AEM 컨텐츠를 쉽게 찾을 수 있습니다. CIF는 관련 AEM 컨텐츠과 함께 제품 카탈로그의 전체 텍스트 검색으로 Omnisearch를 확장합니다.
![상거래 메뉴 항목](assets/omnisearch.png)

Omnisearch는 모든 관련 제품을 찾기 위해 상거래 백엔드에서 전체 텍스트 검색을 실행합니다. 결과는 다음과 같습니다 **모든 제품 보기**. Omnisearch는 또한 AEM에서 검색한 제품과 연결된 콘텐츠를 검색합니다. 각 AEM 카테고리 아래에 결과가 나열됩니다. 이 예에서는 하나의 컨텐츠 조각이 제품과 관련되어 있습니다.

## 다음 단계 {#what-is-next}

여정의 이 부분을 완료했으므로 다음을 수행해야 합니다.

* 범용 편집기를 사용하여 CIF 작성의 개념 이해
* 제품 및 카테고리 선택기를 사용하여 AEM에서 제품 카탈로그에 액세스하는 방법
* 제품 조종실과 AEM Omnisearch를 사용하여 콘텐츠 및 상거래 데이터에 액세스하는 방법

이 지식을 바탕으로 구축하고 다음 문서를 검토하여 여정을 계속 진행합니다 [제품 카탈로그 페이지 및 템플릿 관리](catalog-templates.md): 첫 번째 제품 카탈로그 경험을 만들고 사용자 지정하는 방법을 배웁니다.

## 추가 리소스 {#additional-resources}

문서를 검토하여 여정의 다음 부분으로 이동하는 것이 좋습니다 [제품 카탈로그 페이지 및 템플릿 관리](catalog-templates.md)다음은 이 문서에서 언급된 일부 개념을 자세히 설명하는 몇 가지 추가 선택적 리소스입니다. 여정을 계속 진행할 필요는 없습니다.

* [저장소 및 카탈로그 구성](/help/commerce-cloud/getting-started.md#catalog)
