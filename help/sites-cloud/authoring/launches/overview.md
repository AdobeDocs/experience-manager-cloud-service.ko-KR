---
title: 론치
description: 론치를 사용하여 향후 릴리스용 콘텐츠를 효율적으로 개발할 수 있습니다. 현재 페이지를 유지하면서 나중에 게시할 수 있도록 변경할 수 있습니다
exl-id: 3e410120-d08f-4d05-932f-07bc4440af2b
source-git-commit: 635f4c990c27a7646d97ebd08b453c71133f01b3
workflow-type: tm+mt
source-wordcount: '903'
ht-degree: 59%

---

# 론치 {#launches}

론치를 사용하여 향후 릴리스용 콘텐츠를 효율적으로 개발할 수 있습니다.

론치는 현재 페이지를 유지하면서 나중에 게시할 준비를 하고 변경할 수 있도록 하기 위해 만들어집니다. 론치 페이지를 편집하고 업데이트한 후 이를 소스에 다시 홍보한 후 소스 페이지(최상위 레벨)를 활성화합니다. 홍보를 하면 론치 콘텐츠가 소스 페이지에 다시 복제되며, 홍보는 수동 또는 자동으로 수행할 수 있습니다(론치를 생성 및 편집할 때 설정된 필드에 따라 다름).

예를 들어 온라인 상점의 계절별 제품 페이지는 주력 제품이 현재 계절과 일치하도록 분기별로 업데이트합니다. 다음 분기별 업데이트를 준비하기 위해 적절한 웹 페이지 시작을 만들 수 있습니다. 분기 내내, 론치 사본에 다음 변경 사항이 누적되었습니다.

* 일반적인 유지 관리 작업의 결과로 발생하는 소스 페이지의 변경 사항입니다. 이러한 변경 사항은 론치 페이지에서 자동으로 복제됩니다.
* 다음 분기를 준비하기 위해 론치 페이지에서 직접 수행되는 편집.

다음 작업도 수행할 수 있습니다.

* 론치 분기의 콘텐츠를 탐색하고 필요에 따라 페이지를 추가하거나 제거합니다.
* 미래의 특정 날짜/시간에 게시된 콘텐츠가 표시되는 방식을 미리 봅니다.

다음 분기가 되면 소스 페이지(업데이트된 콘텐츠 보관 중)를 게시할 수 있도록 론치 페이지를 홍보합니다. 모든 페이지를 홍보하거나 수정한 페이지만 홍보할 수 있습니다.

론치는 다음과 같을 수도 있습니다.

* 여러 루트 분기에 대해 생성되었습니다. 전체 사이트에 대한 론치를 만들고 변경을 수행할 수 있지만 전체 사이트를 복사해야 하므로 실용적이지 않을 수 있습니다. 수백 또는 수천 개의 페이지가 관련된 경우 시스템 요구 사항 및 성능은 복사 작업과 이후 프로모션 작업에 필요한 비교 모두에 의해 영향을 받습니다.
* 중첩(론치 내의 론치)을 사용하면 작성자가 각 론치에 대해 동일한 변경 작업을 여러 번 수행할 필요 없이 기존 론치에서 론치를 만들어 이미 수행된 변경 사항을 활용할 수 있습니다.

이 섹션에서는 Sites 콘솔 또는 [론치 콘솔](#the-launches-console) 내에서 론치 페이지를 만들고, 편집하고, 홍보하고, 필요한 경우 [삭제](/help/sites-cloud/authoring/launches/creating.md#deleting-a-launch)하는 방법에 대해 설명합니다.

* [론치 만들기](/help/sites-cloud/authoring/launches/creating.md)
* [론치 편집](/help/sites-cloud/authoring/launches/editing.md)
* [론치 내 페이지 관리](/help/sites-cloud/authoring/launches/managing-pages.md)
* [타임워프를 사용하여 론치를 기반으로 하는 콘텐츠 미리보기](/help/sites-cloud/authoring/launches/preview.md)
* [론치 홍보](/help/sites-cloud/authoring/launches/promoting.md)

## 론치 - 이벤트 순서 {#launches-the-order-of-events}

론치를 사용하면 하나 이상의 활성화된 웹 페이지에 대한 향후 릴리스를 위해 콘텐츠를 효율적으로 개발할 수 있습니다.

론치를 사용하여 다음을 수행할 수 있습니다.

* Create a copy of your source pages:
   * The copy is your launch.
   * The top-level source pages are known as **Production**.
      * 소스 페이지는 여러 (개별) 분기에서 가져올 수 있습니다.

  ![론치 작업 순서](/help/sites-cloud/authoring/assets/launches-order.png)

* 론치 구성을 편집합니다.
   * 론치에/에서 페이지 및/또는 분기를 추가하거나 제거합니다.
   * **제목**, **론치 날짜**, **프로덕션 준비** 플래그와 같은 론치 속성을 편집합니다.
* 콘텐츠의 수동 또는 자동 홍보 및 게시
   * 수동:
      * 론치 콘텐츠를 게시할 준비가 되면 다시 **타겟**(소스 페이지)으로 홍보합니다.
      * 소스(다시 홍보 후) 페이지의 콘텐츠를 게시합니다.
      * 모든 페이지를 홍보하거나 수정된 페이지만 홍보합니다.
   * 자동 - 다음 내용이 포함됩니다.
      * **론치**(**라이브**) **날짜** 필드: 론치를 만들거나 편집할 때 설정할 수 있습니다.
      * 다음 **프로덕션 준비** 플래그: 론치를 편집할 때만 설정할 수 있습니다.
      * 다음과 같은 경우 **프로덕션 준비** 플래그가 설정되면 론치가 지정된 의 프로덕션 페이지로 자동 홍보됩니다. **시작**(**라이브**) **날짜**. 홍보 이후 프로덕션 페이지는 자동으로 게시됩니다.\
        날짜를 설정하지 않았다면 플래그가 적용되지 않습니다.
* 소스 페이지와 론치 페이지 동시 업데이트:
   * 소스 페이지 변경 내용은 론치 사본(상속을 통해, 즉 라이브 카피로 설정된 경우)에서 자동으로 구현됩니다.
   * 론치 사본에 대한 변경은 이 자동 업데이트 또는 소스 페이지를 중단하지 않고 수행할 수 있습니다.

  ![동시 작업](/help/sites-cloud/authoring/assets/launches-parallel.png)

* [중첩 론치 만들기](/help/sites-cloud/authoring/launches/creating.md#creating-a-nested-launch) - 론치 내의 론치:
   * 소스가 기존 론치입니다.
   * 다음을 수행할 수 있습니다. [중첩 론치 홍보](/help/sites-cloud/authoring/launches/promoting.md#promoting-a-nested-launch) 대상: 상위 론치 또는 최상위 소스 페이지(프로덕션)일 수 있습니다.

  ![중첩 론치 만들기](/help/sites-cloud/authoring/assets/launches-nested.png)

  >[!CAUTION]
  >
  >론치를 삭제하면 론치 자체 및 모든 하위 중첩 론치가 제거됩니다.

>[!NOTE]
>
>론치를 만들고 편집하려면 기본 그룹 `content-authors`에서와 같이 `/content/launches`에 대한 액세스 권한이 필요합니다.
>
>문제가 발생하면 시스템 관리자에게 문의하십시오.

## 참조의 론치 (Sites 콘솔) {#launches-in-references-sites-console}

1. **Sites** 콘솔에서 론치의 소스로 이동합니다.
1. 를 엽니다. **참조** 소스 페이지를 레일로 이동한 다음 선택합니다.
1. 선택 **론치**, 기존 론치가 다음에 대한 액세스 권한과 함께 나열됩니다. **론치 콘솔**:

   ![Sites 콘솔의 론치 참조](/help/sites-cloud/authoring/assets/launches-references.png)

1. 적절한 론치를 탭/클릭하면 가능한 작업 목록이 표시됩니다.

   ![Sites 콘솔의 론치에 대해 수행하는 작업](/help/sites-cloud/authoring/assets/launches-references-actions.png)

## 론치 콘솔 {#the-launches-console}

론치 콘솔에서는 론치에 대한 개요를 제공하며 여기에 나열된 론치에 대한 작업을 수행할 수 있습니다. 이 콘솔은 다음 방법으로 액세스할 수 있습니다.

* **도구** 콘솔: **도구**, **사이트**, **론치**

* **참조** 레일의 **론치** 섹션 하단에 있는 **론치 콘솔**(Sites 콘솔에서 소스 콘텐츠 검색 시)

  ![Sites 콘솔의 론치 참조에 있는 론치 콘솔](/help/sites-cloud/authoring/assets/launches-references.png)

* 오른쪽 상단의 **론치 버튼**(Sites 콘솔에서 론치 콘텐츠 검색 시):

  ![Sites 콘솔의 론치 옵션](/help/sites-cloud/authoring/assets/launches-console-navigate-launch-content.png)

* 또는 직접
  `https://<host>:<port>/libs/launches/content/launches.html`
