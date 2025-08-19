---
title: 제품 관리실
description: 연결된 제품 카탈로그 및 관련 컨텐츠에 대한 통합 개요를 제공하는 제품 관리실을 사용하는 방법에 대해 알아봅니다.
exl-id: 6dbf039c-e040-48f1-88f3-ebbd70cdf94d
feature: Commerce Integration Framework
role: Admin
index: false
source-git-commit: 80bd8da1531e009509e29e2433a7cbc8dfe58e60
workflow-type: tm+mt
source-wordcount: '451'
ht-degree: 1%

---


# 제품 관리실 {#product-cockpit}

연결된 제품 카탈로그 및 관련 컨텐츠에 대한 통합 개요를 제공하는 제품 관리실을 사용하는 방법에 대해 알아봅니다.

## 개요 {#overview}

제품 관리실에서는 연결된 제품 카탈로그 및 관련 컨텐츠에 대한 통합 개요를 제공합니다. 모든 관련 콘텐츠에는 조종석에서 빠르게 액세스할 수 있는 링크가 있습니다.

스테이징된 제품 데이터에는 새 카테고리, 제품 또는 업데이트된 속성과 같은 향후 모든 돌연변이가 포함됩니다.

>[!NOTE]
>
>제품 카탈로그라는 용어는 상거래 상점, 스토어 보기 및 유사한 표현식과 상호 호환됩니다.

## 구성 {#configuration}

AEM에서 제품 카탈로그를 구성해야 합니다. 자세한 내용은 [저장소 및 카탈로그 구성](/help/commerce-cloud/cif-storefront/getting-started.md#catalog)을 참조하세요.

단계적 카탈로그 기능을 활성화하려면 인증이 필요합니다. 자세한 내용은 [시작하기](/help/commerce-cloud/cif-storefront/getting-started.md)를 참조하십시오.

>[!NOTE]
>
>단계적 카탈로그 기능은 토큰 기반 인증을 지원하는 Adobe Commerce 및 서드파티 커넥터에서만 사용할 수 있습니다.

## 제품 관리실 열기 {#opening-product-cockpit}

제품 관리실에 액세스하는 가장 쉬운 방법은 AEM의 메인 메뉴에 있는 &#39;Commerce&#39; 메뉴를 이용하는 것입니다. Omnisearch(Commerce 검색)를 사용하거나 `https://<yourAEMInstance>/commerce.html`을(를) 열 수도 있습니다.

![AEM 메뉴](../assets/aem-menu.png)

## 제품 카탈로그 찾아보기 {#browsing-product-catalogs}

제품 관리실은 제품 카탈로그 구조에 따라 계층적으로 구성됩니다. 첫 번째 수준은 상거래 백엔드의 메타 정보를 포함하여 구성된 모든 제품 카탈로그의 카탈로그 루트 수준을 보여줍니다.

![구성된 카탈로그](../assets/catalog-overview.png)

카테고리를 클릭하면 클릭한 카테고리의 하위 항목이 로드됩니다.

![범주 자식](../assets/catalog-category-children.png)

사용 가능한 경우 제품을 클릭하면 제품 변형이 로드됩니다.

![제품 변형](../assets/catalog-product-variation.png)

>[!NOTE]
>
>AEM의 제품 카탈로그 데이터는 구성된 상거래 끝점을 통해 실시간으로 검색되는 데이터입니다. AEM에 저장된 제품 카탈로그 데이터가 없습니다.

## 제품 카탈로그 검색 중 {#searching-product-catalog}

왼쪽 필터 탭에 전체 제품 카탈로그에 대한 전체 텍스트 검색이 제공되어 제품을 빠르게 찾을 수 있습니다.

![검색](../assets/search-cockpit.png)

## 단계적 제품 카탈로그 찾아보기 {#staged-product-catalogs}

기본적으로 제품 관리실에는 라이브 제품 카탈로그 데이터가 표시됩니다. 왼쪽 필터 탭에서 &quot;준비된 카탈로그&quot;를 사용하면 선택한 날짜에 대한 제품 카탈로그가 로드됩니다.

![준비된 카탈로그](../assets/staged-cockpit.png)

## 제품 카탈로그 속성 {#catalog-properties}

제품 또는 범주의 속성 아이콘을 클릭하면 선택한 객체의 속성 보기가 열립니다. 제품 변형의 열린 속성은 기본 제품 속성을 연 것과 같습니다.

### Commerce 탭 {#tabs}

일반 및 변형 탭에는 상거래 백엔드에서 가져오는 사전 정의된 상거래 속성이 표시됩니다. 이 데이터(포함) 레코드 시스템이 상거래 백엔드이므로 variants)는 AEM에서 읽기 전용 데이터입니다. 변형 탭은 변형이 있는 제품에만 표시되며 모든 변형 목록을 표시합니다.

![카탈로그 속성](../assets/catalog-properties.png)

### AEM 컨텐츠 탭 {#content-tabs}

AEM 컨텐츠 유형(경험 조각, 컨텐츠 조각, 연관된 Assets)별로 그룹화된 이 탭에는 상거래 오브젝트와 연관된 AEM 컨텐츠가 표시됩니다. &#39;세부 정보 보기&#39; 작업을 수행하면 선택한 콘텐츠로 새 브라우저 탭이 열립니다.

![콘텐츠 속성](../assets/content-properties.png)
