---
title: 타깃팅된 컨텐츠에 대한 다중 사이트 관리 구성 방식
description: 다이어그램은 타깃팅된 컨텐츠에 대한 다중 사이트 지원이 구조화되는 방식을 보여줍니다.
translation-type: tm+mt
source-git-commit: 16725342c1a14231025bbc1bafb4c97f0d7cfce8
workflow-type: tm+mt
source-wordcount: '181'
ht-degree: 86%

---


# 타깃팅된 컨텐츠에 대한 다중 사이트 관리 구성 방식 {#how-multisite-management-for-targeted-content-is-structured}

다음 다이어그램은 타깃팅된 컨텐츠에 대한 다중 사이트 지원이 구조화되는 방식을 보여줍니다.

영역은 **/content/campaigns/&lt;brand>** 아래에 나타나며 기본적으로 각 브랜드에는 자동으로 만들어지는 마스터 영역이 있습니다. 각 영역에는 영역만의 활동, 경험 및 오퍼 세트가 있습니다.

![멀티사이트 구조](/help/sites-cloud/authoring/assets/multisite-structure.png)

타깃팅된 컨텐츠를 조회하기 위해 페이지 또는 사이트를 영역에 매핑할 수 있습니다. 구성된 영역이 없는 경우, AEM은 이 특정 브랜드의 마스터 영역으로 돌아갑니다.

다음 다이어그램은 site1, site2 및 site3이라는 세 개의 사이트에 대해 논리가 작동하는 방식에 대한 예입니다.

![여러 사이트 구조](/help/sites-cloud/authoring/assets/multisite-structure-2.png)

* site1은 영역 매핑을 기반으로 brand1용의 myarea1과 brand2용의 otherarea2를 조회합니다.
* site2는 brand1용의 영역 매핑만 정의되어 있으므로 brand1용의 myarea1과 brand2용의 마스터 영역을 조회합니다.
* site3은 이 사이트용으로 정의된 다른 영역 매핑이 없으므로 brand1과 brand2용 마스터 영역을 조회합니다.
