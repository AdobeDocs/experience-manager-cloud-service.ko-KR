---
title: 페이지 생성
description: 사이트 콘솔을 사용하여 웹 사이트의 새 페이지를 만드는 방법에 대해 알아봅니다.
source-git-commit: bbd845079cb688dc3e62e2cf6b1a63c49a92f6b4
workflow-type: tm+mt
source-wordcount: '425'
ht-degree: 64%

---


# 페이지 생성 {#creating-pages}

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
      * **이름** 필드에 **잘못된 문자를 제출**&#x200B;할 수 없습니다. AEM에서 잘못된 문자를 감지하면 필드가 강조 표시되고, 제거/교체가 필요한 문자를 나타내는 설명 메시지가 표시됩니다.

   >[!TIP]
   >
   >[페이지 이름 지정 규칙](#page-naming-conventions)을 참조하십시오.

   페이지를 만드는 데 필요한 최소 정보는 **제목**.

   ![페이지 제목 입력](/help/sites-cloud/authoring/assets/organizing-create-page-title.png)

1. **만들기**&#x200B;를 클릭하여 프로세스를 완료하고 새 페이지를 만듭니다. 확인 대화 상자에 페이지를 즉시 **열지** 또는 콘솔로 돌아갈지(**완료**) 여부를 묻는 메시지가 표시됩니다.

   ![페이지 작성 성공](/help/sites-cloud/authoring/assets/organizing-create-page-success.png)

   >[!NOTE]
   >
   >해당 위치에 이미 존재하는 이름을 사용하여 페이지를 만들 경우, 번호가 추가되어 변형된 이름이 자동으로 생성됩니다. 예를 들어 `beach`가 이미 존재하는 경우, 새 페이지는 `beach1`이 됩니다.

1. 콘솔로 돌아오면 새 페이지를 볼 수 있습니다.

   ![결과 새 페이지](/help/sites-cloud/authoring/assets/organizing-create-page-result.png)

>[!CAUTION]
>
>페이지가 만들어지면 해당 템플릿을 변경할 수 없습니다. 대신 [새 템플릿으로 론치를 만들 수는 있지만](/help/sites-cloud/authoring/launches/creating.md#create-launch-with-new-template) 그렇게 되면 존재하는 콘텐츠는 모두 잃게 됩니다.
