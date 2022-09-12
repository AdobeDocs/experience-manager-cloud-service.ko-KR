---
title: 제품 카탈로그 페이지 및 템플릿 관리
description: 제품 카탈로그 페이지 및 템플릿을 관리하는 방법을 알아봅니다.
exl-id: 0d795d85-c865-40d5-941e-e02ee96fdd11
source-git-commit: 940a01cd3b9e4804bfab1a5970699271f624f087
workflow-type: tm+mt
source-wordcount: '724'
ht-degree: 1%

---

# 제품 카탈로그 페이지 및 템플릿 관리 {#product-catalog}

제품 카탈로그 페이지 및 템플릿을 관리하는 방법을 알아봅니다.

## 지금까지의 이야기 {#story-so-far}

AEM 컨텐츠 및 상거래 작성 여정의 이전 문서에서, [AEM CIF 작성 기본 사항 시작하기](getting-started.md)를 사용하여 CIF 작성의 기본 사항을 학습했습니다.

이 문서는 이러한 기본 사항을 기반으로 합니다.

## 목표 {#objective}

이 문서는 제품 카탈로그 페이지 및 템플릿을 관리하는 방법을 이해하는 데 도움이 됩니다. 문서를 읽고 나면

* 카탈로그 템플릿의 개념 이해
* 일반 템플릿 작동 방식
* 개별 템플릿을 만들었습니다.

## 기본 개념 {#basic-concept}

Venia storefront에는 탐색 및 랜딩, 카테고리(PLP) 및 제품 세부 사항 페이지(PDP)가 포함된 일반적인 제품 카탈로그 경험이 포함되어 있습니다.

카탈로그 페이지는 필요한 경우 상거래 종단점에서 가져오는 AEM CIF 카탈로그 템플릿과 실시간 제품 데이터를 사용하여 동적으로 작성됩니다. 모든 카탈로그에는 제품 및 카테고리 페이지에 대한 일반 템플릿이 있습니다.
![카탈로그 구조](assets/catalog-structure.png)

탐색 구성 요소는 컨텐츠 및 카탈로그 페이지를 보여줍니다. 카탈로그 랜딩 페이지나 탐색의 첫 번째 수준 카테고리를 표시할 수 있습니다. 마우스로 카테고리를 가리키면 두 번째 수준 카테고리가 두 번째 라인으로 표시됩니다.
![카탈로그 탐색](assets/catalog-navigation.png)

카테고리를 클릭하면 카테고리 페이지(또는 제품 목록 페이지)가 열립니다.

![PLP](assets/catalog-plp.png)

제품을 클릭하면 제품 세부 사항 페이지가 열립니다.

![PLP](assets/catalog-pdp.png)

## 템플릿 {#templates}

### 일반 템플릿 {#generic}

일반 Venia 카탈로그 템플릿은 제품 목록 핵심 구성 요소를 사용합니다. 이 구성 요소는 사용 가능한 경우 카테고리 이미지와 해당 카테고리의 제품을 표시합니다.
![카테고리 템플릿](assets/category-template.png)

일반 Venia 제품 템플릿은 제품 세부 사항 핵심 구성 요소를 사용합니다. 이 구성 요소는 다양한 제품 유형 및 장바구니에 추가 작업에 대한 제품 정보를 표시합니다.
![제품 템플릿](assets/product-template.png)

### 템플릿 편집 {#edit-templates}

템플릿은 템플릿 페이지를 직접 열거나 제품 카탈로그 페이지를 검색하는 동안 편집 모드로 전환하여 편집할 수 있습니다. 페이지를 변경하면 제품/카테고리의 특정 페이지뿐만 아니라 템플릿이 변경된다는 점을 기억하십시오.

### 카테고리 또는 제품별 템플릿 {#specific}

CIF는 몇 번의 클릭만으로 여러 템플릿을 지원합니다. 다른 템플릿을 만들려면 각 카테고리에서 일반 템플릿을 선택하고 을(를) 사용하여 새 페이지를 만듭니다 **만들기** 작업.

![템플릿 페이지 만들기](assets/create-template-page.png)

각 제품 또는 카테고리 템플릿을 선택합니다.

![템플릿 만들기 선택](assets/create-template-select.png)

제목을 입력하고 페이지를 만듭니다.

![템플리트 입력](assets/create-template-enter.png)

이제 일반 템플릿 아래에 특정 템플릿이 있습니다.

![템플릿 계층 만들기](assets/create-template-hierachry.png)

템플릿을 엽니다. 일반 카테고리 템플릿과 동일하게 표시됩니다.

![템플릿 새로 만들기](assets/create-template-new.png)

페이지 상단에 이미지를 추가합니다.

![템플릿 업데이트 만들기](assets/create-template-update.png)

모든 카테고리/제품으로 템플릿을 미리 볼 수 있습니다. 열기 **페이지 정보** 그런 다음 **카테고리/제품으로 보기**. 이 제품/카테고리로 미리 보기를 가져오려면 선택기에서 제품/카테고리를 선택합니다. 선택 **Look** 카테고리를 사용하여 업데이트된 템플릿의 미리 보기를 가져옵니다.

![템플릿 만들기 ](assets/create-template-picker.png)

이제 이 템플릿을 특정 카테고리에 할당해야 합니다. 에서 속성을 엽니다. **페이지 정보** 메뉴를 표시하고 commerce 탭으로 전환합니다. 폴더 아이콘을 클릭하여 **Look** 카테고리 선택기의 카테고리. 확인란을 활성화하여 템플릿에 여러 카테고리를 지정하고 하위 카테고리를 포함할 수도 있습니다.

![템플릿 연결 만들기](assets/create-template-associate.png)

기본 홈 페이지로 돌아가서 를 클릭합니다. **Look** 카테고리 를 클릭하여 특정 템플릿을 확인합니다. 다른 모든 카테고리는 여전히 일반 템플릿을 사용합니다.

![템플릿 결과 만들기](assets/create-template-result.png)

개별 제품 템플릿을 만드는 데 동일한 워크플로우를 적용할 수 있습니다.

## 다음 단계 {#what-is-next}

여정의 이 부분을 완료했으므로 다음을 수행해야 합니다.

* 카탈로그 템플릿의 개념 이해
* 일반 템플릿 작동 방식
* 개별 템플릿을 만들었습니다.

이 지식을 바탕으로 구축하고 다음 문서를 검토하여 여정을 계속 진행합니다 [준비된 제품 카탈로그 경험 관리](staged-catalog.md): 준비된 제품 데이터 및 AEM Launches에서 작업하는 방법을 알아봅니다.

## 추가 리소스 {#additional-resources}

문서를 검토하여 여정의 다음 부분으로 이동하는 것이 좋습니다 [준비된 제품 카탈로그 경험 관리](staged-catalog.md), 다음은 이 문서에서 언급된 일부 개념을 자세히 설명하는 몇 가지 추가 선택적 리소스입니다. 하지만 헤드리스 여정을 계속 진행할 필요는 없습니다.

* [여러 카테고리 및 제품 페이지 만들기](/help/commerce-cloud/authoring/multi-template-usage.md)
* [Experience Manager Cloud Service 마이그레이션 안내서](/help/commerce-cloud/migration.md) - 이전 버전에서 CIF(AEM Commerce Integration Framework) 추가 기능으로 마이그레이션하는 방법
