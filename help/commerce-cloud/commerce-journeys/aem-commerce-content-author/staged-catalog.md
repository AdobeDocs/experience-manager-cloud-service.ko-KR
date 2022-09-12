---
title: 준비된 제품 카탈로그 경험 관리
description: 준비된 제품 카탈로그 경험을 관리하는 방법을 알아봅니다.
exl-id: 1db18818-b8e0-4127-8a65-dc3dea1f2927
source-git-commit: 940a01cd3b9e4804bfab1a5970699271f624f087
workflow-type: tm+mt
source-wordcount: '494'
ht-degree: 8%

---

# 단계적 제품 카탈로그 경험 구축 {#building-experiences}

준비된 제품 카탈로그 경험을 관리하는 방법을 알아봅니다.

## 지금까지의 이야기 {#story-so-far}

AEM Content and Commerce 여정의 이전 문서에서, [제품 카탈로그 페이지 및 템플릿 관리](catalog-templates.md), 템플릿을 기반으로 제품 카탈로그 경험을 관리 및 구축하는 방법을 알아보았습니다.

이 문서는 이러한 기본 사항을 기반으로 합니다.

## 목표 {#objective}

이 문서는 준비된 제품 데이터 및 AEM 시작을 기반으로 제품 카탈로그 경험을 관리하는 방법을 이해하는 데 도움이 됩니다. 작성자는 예정된 제품 실행(예: 새 의류 컬렉션)을 동시에 준비해야 하는 경우가 많습니다. 이렇게 하려면 준비된 제품 데이터(아직 출시되지 않음)에 액세스해야 하며 컨텐츠를 준비할 수 있어야 합니다. 이 새 컨텐츠는 제품 출시와 함께 라이브로 전송됩니다.

    >[!NOTE]
    >
    >이 기능은 토큰 기반 인증을 지원하는 Adobe Commerce 또는 Cloud Edition 및 타사 커넥터에서만 사용할 수 있습니다. 자세한 내용은 [시작하기](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content-and-commerce/storefront/getting-started.html)을 참조하십시오.

먼저 작성자가 CIF를 사용하여 준비된 제품 데이터에 액세스하는 방법을 살펴보겠습니다.

## 준비된 제품 데이터 작업 {#staged-product-data}

준비된 제품 데이터에 액세스하는 한 가지 방법은 제품 조종실을 사용하는 것입니다. 기본 AEM 메뉴에서 상거래 아이콘을 클릭하여 제품 카탈로그를 엽니다. 이렇게 하면 라이브 제품 데이터에 액세스할 수 있습니다. 왼쪽의 필터 탭을 열고 확장합니다. **준비된 카탈로그**. 이제 미리 보기 데이터를 사용하여 언제든지 준비된 제품 데이터에 액세스할 수 있습니다. 준비된 데이터에는 새로운 카테고리, 제품 또는 가격과 같은 업데이트된 필드가 포함됩니다.

![조종실](assets/staged-cockpit.png)

타임워프 보기를 사용하여 준비된 데이터가 있는 스토어를 미리 볼 수 있습니다. 편집기를 열고 모드를 타임워프로 전환합니다. 미래 날짜를 선택합니다. 특정 날짜 동안 페이지를 보고 있는 편집기 맨 위에 있는 정보를 확인합니다.

![단계 타임워프](assets/staged-timewarp.png)

이제 준비된 데이터로 카탈로그를 찾을 수 있습니다. 준비된 카테고리 또는 제품 페이지를 열면 편집기에 시각적 표시기가 표시됩니다.

![단계 플롭](assets/staged-plp.png)

    >[!NOTE]
    >
    >Omnisearch에는 컨텍스트가 없으므로 라이브 제품 카탈로그 데이터만 반환합니다

## AEM 실행 {#launches}

AEM Launches에서 준비된 제품 데이터에 대한 컨텐츠를 만들 수 있습니다. Launches에 익숙하지 않은 경우, 아래의 설명서 링크를 클릭하십시오. [추가 리소스 섹션](#additional-resources). 그런 다음 론치 날짜를 사용하여 준비된 제품 데이터에 액세스합니다.

![단계 시작](assets/staged-launch.png)

피커는 오른쪽에 준비된 표시기와 함께 실행 날짜를 준수합니다.

![단계 선택기](assets/staged-picker.png)

## 다음 단계 {#what-is-next}

여정의 이 부분을 완료했으므로 다음을 수행해야 합니다.

* launches에서 준비된 제품 카탈로그 및 컨텐츠의 개념 이해
* 제품 조종실 및 편집기를 통해 준비된 제품 카탈로그 데이터에 액세스할 수 있습니다.

이제 관리할 준비가 되었습니다. [제품 경험](product-experience-management.md). 그러나 AEM 컨텐츠 및 상거래 에는 다양한 추가 옵션이 있습니다. 이 여정에서 확인한 기능들에 대한 자세한 내용은 [추가 리소스 섹션](#additional-resources)에서 사용할 수 있는 몇 가지 추가 리소스를 확인하십시오.

## 추가 리소스 {#additional-resources}

* [제품 관리실](/help/commerce-cloud/authoring/product-cockpit.md)
* [시작하기](/help/commerce-cloud/getting-started.md)
* [론치](/help/sites-cloud/authoring/launches/overview.md)
