---
title: 타겟팅된 콘텐츠에 대한 다중 사이트 관리 구성 방식
description: 다이어그램은 타겟팅된 콘텐츠에 대한 다중 사이트 지원이 구조화되는 방식을 보여 줍니다.
exl-id: c6b05c2a-0897-4514-8937-e23bfcf757d5
source-git-commit: 90de3cf9bf1c949667f4de109d0b517c6be22184
workflow-type: tm+mt
source-wordcount: '181'
ht-degree: 100%

---

# 타겟팅된 콘텐츠에 대한 다중 사이트 관리 구성 방식 {#how-multisite-management-for-targeted-content-is-structured}

다음 다이어그램은 타겟팅된 콘텐츠에 대한 다중 사이트 지원이 구조화되는 방식을 보여 줍니다.

영역은 **/content/campaigns/&lt;brand>** 아래에 표시되며 기본적으로 각 브랜드에는 자동으로 생성되는 마스터 영역이 있습니다. 각 영역에는 영역만의 활동, 경험 및 오퍼 세트가 있습니다.

![다중 사이트 구조](/help/sites-cloud/authoring/assets/multisite-structure.png)

타겟팅된 콘텐츠를 조회하기 위해 페이지 또는 사이트를 영역에 매핑할 수 있습니다. 구성된 영역이 없는 경우, AEM은 이 특정 브랜드의 마스터 영역으로 돌아갑니다.

다음 다이어그램은 site1, site2 및 site3이라는 세 개의 사이트에 대해 논리가 작동하는 방식에 대한 예입니다.

![사이트 간 다중 사이트 구조](/help/sites-cloud/authoring/assets/multisite-structure-2.png)

* site1은 영역 매핑을 기반으로 brand1용의 myarea1과 brand2용의 otherarea2를 조회합니다.
* site2는 brand1용의 영역 매핑만 정의되어 있으므로 brand1용의 myarea1과 brand2용의 마스터 영역을 조회합니다.
* site3은 이 사이트용으로 정의된 다른 영역 매핑이 없으므로 brand1과 brand2용 마스터 영역을 조회합니다.
