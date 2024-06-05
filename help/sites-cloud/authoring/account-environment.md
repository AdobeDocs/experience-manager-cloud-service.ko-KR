---
title: 계정 환경 구성
description: Adobe Experience Manager(AEM)에서는 계정과, 작성 환경의 특정 측면들을 구성하는 기능을 제공합니다.
exl-id: 1b948f0b-85b9-478a-8b7e-61495c1d57b6
solution: Experience Manager Sites
feature: Authoring
role: User
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '501'
ht-degree: 100%

---

# 계정 환경 구성 {#configuring-your-account-environment}

Adobe Experience Manager(AEM)에서는 계정과, 작성 환경의 특정 측면들을 구성하는 기능을 제공합니다.

[헤더](/help/sites-cloud/authoring/basic-handling.md#the-header)의 [사용자](#user-settings) 선택 사항 및 연관된 [내 환경 설정](#my-preferences) 대화 상자를 사용하면 사용자 선택 사항을 수정할 수 있습니다.

헤더에서 [사용자](#user-settings) 선택 사항에 액세스해 보십시오.

## 사용자 설정 {#user-settings}

**사용자 설정** 대화 상자에서는 다음에 액세스할 수 있습니다.

* 가장 대상
   * 가장 대상 기능을 사용하면 사용자는 다른 사용자를 대신하여 작업할 수 있습니다. <!--With the [Impersonate as](/help/sites-administering/security.md#impersonating-another-user) functionality, a user can work on behalf of another user.-->
* 프로필
   * 사용자 설정을 연결하는 편리한 링크 제공 <!--Offers a convenient link to your [user settings](/help/sites-administering/security.md))-->
* [내 환경 설정](#my-preferences)
   * 사용자에게만 해당하는 다양한 환경 설정을 지정합니다.

![사용자 설정](/help/sites-cloud/authoring/assets/user-settings.png)

### 내 환경 설정 {#my-preferences}

**내 환경 설정** 대화 상자는 헤더에서 [사용자](#user-settings) 선택 사항을 통해 액세스합니다.

각 사용자는 원하는 속성을 설정할 수 있습니다.

![내 환경 설정](/help/sites-cloud/authoring/assets/user-preferences.png)

* **언어**

  작성 환경의 UI에 사용할 언어를 정의합니다. 사용 가능한 목록에서 필요한 언어를 선택합니다.

* **창 관리**

  동작 또는 창 열기를 정의합니다. 다음 중 하나를 선택합니다.

   * **여러 창**(기본값)

      * 페이지가 새 창에 열립니다.

   * **단일 창**

      * 현재 창에 페이지가 열립니다.

* **자산에 대한 데스크탑 작업 표시**

  이 옵션을 사용하려면 AEM 데스크탑 앱을 사용해야 합니다.

* **주석 색상**

  주석을 작성할 때 사용되는 기본 색상을 정의합니다.

   * 색상을 선택하는 견본 선택기를 열 수 있도록 색상 블록을 클릭합니다.
   * 또는 필드에 원하는 색상의 16진수 코드를 입력하십시오.

* **상대적 날짜 표시**

  가독성을 높이기 위해 AEM에서는 최근 7일 이내의 날짜는 상대적 날짜(예: 3일 전)로 렌더링하고 그보다 오래된 날짜는 정확한 날짜(예: 2017년 3월 20일)로 렌더링합니다.

  이 선택 사항은 시스템 날짜가 표시되는 방법을 정의합니다. 다음 옵션을 사용할 수 있습니다.

   * **항상 정확한 날짜 표시**: 항상 정확한 날짜가 표시됩니다(상대적 날짜가 아님).
   * **1일**: 1일 이내의 날짜는 상대적 날짜가 표시되고, 그 외에는 정확한 날짜가 표시됩니다.
   * **7일(기본값)**: 7일 이내의 날짜는 상대적 날짜가 표시되고, 그 외에는 정확한 날짜가 표시됩니다.
   * **1개월**: 한 달 이내의 날짜는 상대적 날짜가 표시되고, 그 외에는 정확한 날짜가 표시됩니다.
   * **1년**: 1년 이내의 날짜는 상대적 날짜가 표시되고, 그 외에는 정확한 날짜가 표시됩니다.
   * **항상 상대적 날짜 표시**: 정확한 날짜는 표시되지 않고 상대적 날짜만 표시됩니다.

* **단축키 사용**

  AEM은 작성의 효율성을 개선하는 다양한 키보드 단축키를 지원합니다.

   * [페이지 편집을 위한 키보드 단축키](/help/sites-cloud/authoring/page-editor/keyboard-shortcuts.md)
   * [콘솔용 키보드 단축키](/help/sites-cloud/authoring/sites-console/keyboard-shortcuts.md)

  키보드 단축키를 사용할 수 있도록 합니다. 기본적으로 사용할 수 있지만 사용자에게 특정 액세스 가능성 요구 사항이 있는 경우처럼 원하는 경우에는 사용하지 않도록 설정할 수 없습니다.

* **자산 홈 페이지 활성화**

  이 선택 사항은 시스템 관리자가 전체 조직에 대해 [자산 홈 페이지] 환경을 활성화한 경우에만 사용할 수 있습니다.

* **Stock 구성**

  이 옵션을 통해 기본 Adobe Stock 구성을 지정할 수 있으며, 이 옵션은 시스템 관리자가 [Adobe Stock 통합](/help/assets/aem-assets-adobe-stock.md)을 사용하도록 설정한 경우에만 사용할 수 있습니다.
