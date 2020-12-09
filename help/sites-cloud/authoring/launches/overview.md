---
title: 론치
description: 론치를 사용하여 향후 릴리스용 컨텐츠를 효율적으로 개발할 수 있습니다. 현재 페이지를 유지 관리하면서 나중에 게시할 수 있도록 변경할 수도 있습니다.
translation-type: tm+mt
source-git-commit: 21f14d1f4e0ae26e097d4b31fe6811f1d089813d
workflow-type: tm+mt
source-wordcount: '907'
ht-degree: 81%

---


# 론치 {#launches}

론치를 사용하여 향후 릴리스용 컨텐츠를 효율적으로 개발할 수 있습니다.

론치가 생성되며 향후에 게시할 수 있도록 변경할 수 있습니다(현재 페이지를 유지하는 동안). 론치 페이지를 편집하고 업데이트한 후, 이를 소스에 다시 홍보한 후 소스 페이지(최상위 레벨)를 활성화합니다. 홍보를 하면 론치 컨텐츠가 소스 페이지에 다시 복제되며, 홍보는 수동 또는 자동으로 수행할 수 있습니다(론치를 생성 및 편집할 때 설정된 필드에 따라 다름).

예를 들어, 온라인 상점의 계절별 제품 페이지는 주력 제품이 현재 계절과 일치하도록 분기별로 업데이트합니다. 다음 분기별 업데이트를 준비할 수 있도록, 적절한 웹 페이지의 론치를 만들 수 있습니다. 분기 내내, 론치 복사본에 다음 변경 사항이 누적되었습니다.

* 일반 유지 관리 작업의 결과인 소스 페이지 변경 사항. 이 변경 사항은 론치 페이지에서 자동으로 복제됩니다.
* 다음 분기에 대한 준비로 론치 페이지에서 직접 수행한 편집 사항.

다음을 작업도 수행할 수 있습니다.

* 론치 분기의 컨텐츠 탐색필요에 따라 페이지 추가 또는 제거
* 게시된 컨텐츠가 미래의 특정 날짜/모습을 어떻게 보일지 미리 볼 수 있습니다.

다음 분기가 되면 소스 페이지(업데이트된 컨텐츠 보관 중)를 게시할 수 있도록 론치 페이지를 홍보합니다. 모든 페이지를 홍보하거나 수정한 페이지만 홍보할 수 있습니다.

론치는

* 다중 루트 분기용으로 만들 수도 있습니다. 전체 사이트용으로 론치를 만들 수는 있지만(그리고 거기에서 변경을 수행할 수는 있지만) 전체 사이트를 복사해야 하므로 터무니없는 일입니다. 수백 또는 수천 개의 페이지가 관련되어 있는 경우, 시스템 요구 사항과 성능이 복사 작업과 홍보에 필요한 향후의 비교 작업 모두에 영향을 받습니다.
* 기존 론치에서 론치를 만들 수 있도록 중첩(론치 내 론치)할 수 있으므로, 작성자는 각 론치에 대해 동일한 변경을 여러 번 수행하지 않고 이미 수행된 변경 사항을 이용할 수 있습니다.

이 섹션에서는 사이트 콘솔 또는 [론치 콘솔](#the-launches-console)에서 론치 페이지를 만들고, 편집하고, 홍보하는 방법(필요한 경우 [delete](/help/sites-cloud/authoring/launches/creating.md#deleting-a-launch))에 대해 설명합니다.

* [론치 만들기](/help/sites-cloud/authoring/launches/creating.md)
* [론치 편집](/help/sites-cloud/authoring/launches/editing.md)
* [론치 내 페이지 관리](/help/sites-cloud/authoring/launches/managing-pages.md)
* [타임워프를 사용하여 론치를 기반으로 컨텐츠 미리 보기](/help/sites-cloud/authoring/launches/preview.md)
* [론치 홍보](/help/sites-cloud/authoring/launches/promoting.md)

## 론치 - 이벤트 순서 {#launches-the-order-of-events}

론치를 사용하면 하나 이상의 활성화된 웹 페이지에 대한 향후 릴리스를 위해 컨텐츠를 효율적으로 개발할 수 있습니다.

론치를 사용하면 다음 작업을 수행할 수 있습니다.

* 소스 페이지 사본 만들기
   * 이 사본이 론치입니다.
   * 최상위 수준 소스 페이지는 **프로덕션**&#x200B;이라고 합니다.
      * 소스 페이지를 여러 개의(독립된) 분기에서 가져올 수 있습니다.

   ![실행 순서](/help/sites-cloud/authoring/assets/launches-order.png)

* 론치 구성 편집:
   * 론치에서 페이지 및/또는 분기를 추가 또는 제거합니다.
   * **제목**, **론치 날짜**, **프로덕션 준비** 플래그와 같은 론치 속성을 편집합니다.
* 컨텐츠의 수동 또는 자동 홍보 및 게시
   * 수동:
      * 론치 컨텐츠를 게시할 준비가 되면 다시 **타겟**(소스 페이지)으로 홍보합니다.
      * 소스(다시 홍보 후) 페이지의 컨텐츠를 게시합니다.
      * 모든 페이지를 승인하거나 수정된 페이지만 홍보합니다.
   * 자동 - 다음 내용이 포함됩니다.
      * **론치**(**라이브**) **날짜** 필드: 론치를 만들거나 편집할 때 설정할 수 있습니다.
      * **프로덕션 준비** 플래그: 론치를 편집할 때만 설정할 수 있습니다.
      * **프로덕션 준비** 플래그를 설정하면, 론치가 지정된 **론치**(**라이브**) **날짜**&#x200B;의 프로덕션 페이지로 자동 홍보됩니다. 홍보 후에는 프로덕션 페이지가 자동으로 게시됩니다.\
         날짜를 설정하지 않았다면 플래그가 적용되지 않습니다.
* 소스 페이지와 론치 페이지 동시 업데이트:
   * 소스 페이지 변경 사항은 론치 카피(상속을 통해, 즉 Live Copy로 설정된 경우)에서 자동으로 구현됩니다.
   * 론치 카피에 대한 변경은 이 자동 업데이트 또는 소스 페이지를 중단하지 않고 수행할 수 있습니다.

   ![동시 작업](/help/sites-cloud/authoring/assets/launches-parallel.png)

* [중첩 론치 만들기](/help/sites-cloud/authoring/launches/creating.md#creating-a-nested-launch) - 론치 내 론치:
   * 소스는 기존 론치입니다.
   * 어떤 타겟으로든 [중첩 론치를 홍보](/help/sites-cloud/authoring/launches/promoting.md#promoting-a-nested-launch)할 수 있습니다. 이 타겟은 상위 론치나 최상위 수준 소스 페이지(프로덕션)일 수 있습니다.

   ![중첩 론치](/help/sites-cloud/authoring/assets/launches-nested.png)

   >[!CAUTION]
   >
   >론치를 삭제하면 론치 자체 및 모든 하위 중첩 론치가 제거됩니다.

>[!NOTE]
>
>론치를 만들고 편집하려면 기본 그룹 `content-authors`과 같이 `/content/launches`에 대한 액세스 권한이 필요합니다.
>
>문제가 발생하면 시스템 관리자에게 문의하십시오.

## 참조의 론치(사이트 콘솔) {#launches-in-references-sites-console}

1. **사이트** 콘솔에서 론치의 소스로 이동합니다.
1. **참조** 레일을 열고 소스 페이지를 선택합니다.
1. **론치**&#x200B;를 선택하면 기존 론치가 나열되고 **론치 콘솔**&#x200B;에 액세스할 수 있습니다.

   ![사이트 콘솔의 론치 참조](/help/sites-cloud/authoring/assets/launches-references.png)

1. 적절한 론치를 탭/클릭합니다. 가능한 작업 목록이 표시됩니다.

   ![사이트 콘솔에서 실행할 작업](/help/sites-cloud/authoring/assets/launches-references-actions.png)

## 론치 콘솔 {#the-launches-console}

론치 콘솔은 론치에 대한 개요를 제공하며, 나열된 론치에 대해 작업을 수행할 수 있도록 합니다. 이 콘솔은 다음 방법으로 액세스할 수 있습니다.

* **도구** 콘솔: **도구**, **사이트**, **론치**.

* **론치** 콘솔 **** 에서 소스 컨텐츠를 탐색할 때  **** 참조 레일의 론치 맨 아래에 콘솔이 표시됩니다.

   ![사이트 콘솔의 론치 참조의 론치 콘솔](/help/sites-cloud/authoring/assets/launches-references.png)

* 사이트 콘솔에서 론치 컨텐츠를 탐색할 때 오른쪽 상단에 있는 **론치** 단추:

   ![사이트 콘솔의 론치 옵션](/help/sites-cloud/authoring/assets/launches-console-navigate-launch-content.png)

* 또는 직접for example:
   `https://<host>:<port>/libs/launches/content/launches.html`
