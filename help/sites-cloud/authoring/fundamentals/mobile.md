---
title: 모바일 디바이스용 페이지 작성
description: 모바일용으로 작성할 때 몇 개의 에뮬레이터 간을 전환하여 최종 사용자에게 표시되는 내용을 확인할 수 있습니다.
exl-id: fabd4468-3304-402f-9522-342da3bbae94
source-git-commit: 90de3cf9bf1c949667f4de109d0b517c6be22184
workflow-type: tm+mt
source-wordcount: '267'
ht-degree: 100%

---

# 모바일 디바이스용 페이지 작성 {#authoring-a-page-for-mobile-devices}

Adobe Experience Manager 페이지는 반응형 레이아웃을 기반으로 합니다. [반응형 레이아웃](/help/sites-cloud/authoring/features/responsive-layout.md)은 대상 디바이스에 맞게 콘텐츠를 자동으로 조정하므로 특정 디바이스를 위한 콘텐츠를 작성할 필요가 없습니다.

모바일 페이지를 작성할 때는 모바일 디바이스를 에뮬레이션하는 방식으로 페이지가 표시됩니다. 페이지를 작성할 때에는 몇 개의 에뮬레이터 간을 전환하여 페이지에 액세스할 때 최종 사용자에게 표시되는 내용을 확인할 수 있습니다.

디바이스는 페이지를 렌더링할 디바이스의 기능에 따라 카테고리 기능, 스마트와 터치로 그룹화됩니다. 최종 사용자가 모바일 페이지에 액세스하면 AEM이 디바이스를 감지하여 디바이스 그룹에 해당하는 표현 데이터를 전송합니다.

>[!NOTE]
>
>기존 표준 사이트를 기반으로 모바일 사이트를 만들려면 표준 사이트의 Live Copy를 만드십시오. [라이브 카피 만들기](/help/sites-cloud/administering/msm/creating-live-copies.md)를 참조하십시오.
>
>AEM 개발자는 새 디바이스 그룹을 만들 수 있습니다. 디바이스 그룹 필터 만들기를 참조하십시오.

<!--
>AEM developers can create new device groups. (See [Creating Device Group Filters](/help/sites-developing/groupfilters.md).)
-->

다음 절차를 사용하여 모바일 페이지를 작성하십시오.

1. 전역 탐색에서 **Sites** 콘솔을 엽니다.
1. 콘텐츠 페이지를 편집합니다.
1. 페이지 맨 위에서 **에뮬레이터** 아이콘을 클릭하여 원하는 에뮬레이터로 전환합니다.

   ![에뮬레이터 아이콘](/help/sites-cloud/authoring/assets/emulator.png)

1. 구성 요소 브라우저 또는 에셋 브라우저에 있는 구성 요소를 페이지에 드래그하여 놓습니다.
1. 선택한 디바이스를 기반으로 페이지 및 해당 구성 요소의 [응답형 레이아웃](/help/sites-cloud/authoring/features/responsive-layout.md)을 수정합니다.

페이지 모습은 다음과 유사합니다.

![모바일 예](/help/sites-cloud/authoring/assets/mobile.png)

>[!NOTE]
>
>모바일 디바이스에서 작성 인스턴스의 페이지를 요청하면 에뮬레이터가 비활성화됩니다.
