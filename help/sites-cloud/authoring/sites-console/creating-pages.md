---
title: 페이지 만들기
description: 사이트 콘솔을 사용하여 웹 사이트의 새 페이지를 만드는 방법에 대해 알아봅니다.
exl-id: 77264562-e76a-40c8-9878-847a8878fb8e
solution: Experience Manager Sites
feature: Authoring
role: User
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '461'
ht-degree: 29%

---

# 페이지 만들기 {#creating-pages}

를 사용하여 웹 사이트의 새 페이지를 만드는 방법을 알아봅니다. **사이트** 콘솔.

>[!TIP]
>
>새 페이지를 만들기 전에 다음 사항에 익숙해지도록 합니다 [AEM에서 페이지를 구성하는 방법.](/help/sites-cloud/authoring/sites-console/organizing-pages.md)

## 액세스 권한 {#access-privileges}

페이지를 만들려면 계정에 적절한 액세스 권한과 권한이 필요합니다.

문제가 발생하면 시스템 관리자에게 문의하십시오.

## 새 페이지 만들기 {#creating-a-new-page}

모든 페이지가 미리 만들어져 있지 않다면 콘텐츠를 만들기 전에 먼저 페이지를 만들어야 합니다.

1. 열기 [다음 **사이트** 콘솔.](/help/sites-cloud/authoring/sites-console/introduction.md)
1. 새 페이지를 만들 위치로 이동합니다.
1. 도구 모음에서 **만들기**&#x200B;를 사용하여 드롭다운 선택기를 연 다음, 목록에서 **페이지**&#x200B;를 선택합니다.

   ![페이지 만들기](/help/sites-cloud/authoring/assets/organizing-create-page.png)

1. 마법사의 첫 번째 단계에서 다음 중 하나를 수행할 수 있습니다.

   * 새 페이지를 만드는 데 사용할 템플릿을 선택한 다음 를 선택합니다 **다음** 계속합니다.

   * 프로세스를 중단하려면 **취소**&#x200B;를 클릭/탭합니다.

   ![새 페이지에 사용할 템플릿 선택](/help/sites-cloud/authoring/assets/organizing-create-page-template.png)

1. 마법사의 마지막 단계에서 다음 중 하나를 수행할 수 있습니다.

   * 세 탭을 사용하여 [페이지 속성](/help/sites-cloud/authoring/sites-console/page-properties.md) 새 페이지에 할당한 다음 **만들기** 를 클릭하여 페이지를 실제로 만듭니다.

   * 선택한 템플릿으로 돌아가려면 **뒤로**&#x200B;를 사용하십시오.

   주요 필드는 다음과 같습니다.

   * **제목**:

      * 사용자에게 표시되며 필수입니다.

   * **이름**:

      * URI를 생성하는 데 사용됩니다. 지정하지 않을 경우 이름이 제목에서 파생됩니다.
      * 페이지를 제공하는 경우 **이름** 페이지를 만들 때 AEM [규칙에 따라 이름을 확인합니다.](/help/implementing/developing/introduction/naming-conventions.md) AEM 및 JCR에서 적용합니다.
      * **이름** 필드에 **잘못된 문자를 제출**&#x200B;할 수 없습니다. AEM에서 유효하지 않은 문자를 발견하면 필드가 강조 표시되고 제거/교체가 필요한 문자를 나타내는 설명 메시지가 표시됩니다.

   >[!TIP]
   >
   >[페이지 이름 지정 규칙](#page-naming-conventions)을 참조하십시오.

   페이지를 만드는 데 필요한 최소 정보는 **제목**.

   ![페이지 제목 입력](/help/sites-cloud/authoring/assets/organizing-create-page-title.png)

1. 탭 또는 클릭 **만들기** 을 클릭하여 프로세스를 완료하고 새 페이지를 만듭니다. 확인 대화 상자에 다음을 원하는지 여부가 표시됩니다. **열기** 페이지를 즉시 표시하거나 콘솔로 돌아갑니다(**완료**). 하나를 선택하여 페이지 작성 프로세스를 종료합니다.

   ![페이지 작성 성공](/help/sites-cloud/authoring/assets/organizing-create-page-success.png)

   * 다음을 선택하는 경우 **열기**, **사이트** 콘솔은 다음 중 하나의 새 페이지 템플릿에 따라 적절한 편집기를 엽니다.
      * [페이지 편집기](/help/sites-cloud/authoring/page-editor/introduction.md)
      * [유니버설 편집기](/help/sites-cloud/authoring/universal-editor/authoring.md)

콘솔로 돌아오면 새 페이지를 볼 수 있습니다.

![결과 새 페이지](/help/sites-cloud/authoring/assets/organizing-create-page-result.png)

>[!NOTE]
>
>동일한 위치에 이미 존재하는 이름을 사용하여 페이지를 만드는 경우 AEM에서는 숫자를 추가하여 지정된 이름의 변형 페이지를 만듭니다. 예를 들어 다음과 같습니다. `beach` 이미 존재합니다. 새 페이지는 `beach1`.

>[!CAUTION]
>
>페이지가 만들어지면 해당 템플릿을 변경할 수 없습니다. [새 템플릿을 사용하여 론치 만들기](/help/sites-cloud/authoring/launches/creating.md#create-launch-with-new-template), 이렇게 하면 기존 컨텐츠가 손실되지만
