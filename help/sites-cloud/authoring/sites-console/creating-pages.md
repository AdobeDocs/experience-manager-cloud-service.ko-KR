---
title: 페이지 만들기
description: 사이트 콘솔을 사용하여 웹 사이트의 새 페이지를 만드는 방법에 대해 알아봅니다.
exl-id: 77264562-e76a-40c8-9878-847a8878fb8e
solution: Experience Manager Sites
feature: Authoring
role: User
source-git-commit: 6e13244d7ba7bb6e7a51525b66274427fe21d664
workflow-type: tm+mt
source-wordcount: '477'
ht-degree: 27%

---


# 페이지 만들기 {#creating-pages}

**사이트** 콘솔을 사용하여 웹 사이트의 새 페이지를 만드는 방법에 대해 알아봅니다.

>[!TIP]
>
>새 페이지를 만들기 전에 [페이지가 AEM에서 어떻게 구성되어 있는지 알아보세요.](/help/sites-cloud/authoring/sites-console/organizing-pages.md)

## 액세스 권한 {#access-privileges}

페이지를 만들려면 계정에 적절한 액세스 권한과 권한이 필요합니다.

문제가 발생하면 시스템 관리자에게 문의하십시오.

## 새 페이지 만들기 {#creating-a-new-page}

모든 페이지가 미리 만들어져 있지 않다면 콘텐츠를 만들기 전에 먼저 페이지를 만들어야 합니다.

1. [**사이트** 콘솔을 엽니다.](/help/sites-cloud/authoring/sites-console/introduction.md)
1. 새 페이지를 만들 위치로 이동합니다.
1. 도구 모음에서 **만들기**&#x200B;를 사용하여 드롭다운 선택기를 연 다음, 목록에서 **페이지**&#x200B;를 선택합니다.

   ![페이지 만들기](/help/sites-cloud/authoring/assets/organizing-create-page.png)

1. 마법사의 첫 번째 단계에서 다음 중 하나를 수행할 수 있습니다.

   * 새 페이지를 만드는 데 사용할 템플릿을 선택한 다음 **다음**&#x200B;을(를) 선택하여 계속 진행하거나 **취소**&#x200B;을(를) 선택하여 프로세스를 중단합니다.
   * 템플릿은 [페이지 편집기](/help/sites-cloud/authoring/page-editor/introduction.md)와 [범용 편집기](/help/edge/wysiwyg-authoring/templates.md) 모두에서 지원됩니다.

   ![새 페이지에 사용할 템플릿 선택](/help/sites-cloud/authoring/assets/organizing-create-page-template.png)

1. 마법사의 마지막 단계에서 다음 중 하나를 수행할 수 있습니다.

   * 세 탭을 사용하여 새 페이지에 지정할 [페이지 속성](/help/sites-cloud/authoring/sites-console/page-properties.md)을 입력한 다음 실제로 페이지를 만들려면 **만들기**&#x200B;를 선택하십시오.

   * 선택한 템플릿으로 돌아가려면 **뒤로**&#x200B;를 사용하십시오.

   주요 필드는 다음과 같습니다.

   * **제목**:

      * 사용자에게 표시되며 필수입니다.

   * **이름**:

      * URI를 생성하는 데 사용됩니다. 지정하지 않을 경우 이름이 제목에서 파생됩니다.
      * 페이지를 만들 때 **이름** 페이지를 제공하면 AEM [AEM 및 JCR에서 지정한 규칙에 따라 이름을 확인](/help/implementing/developing/introduction/naming-conventions.md)합니다.
      * **이름** 필드에 **잘못된 문자를 제출**&#x200B;할 수 없습니다. AEM에서 유효하지 않은 문자를 발견하면 필드가 강조 표시되고 제거/교체가 필요한 문자를 나타내는 설명 메시지가 표시됩니다.

   >[!TIP]
   >
   >[페이지 이름 지정 규칙](#page-naming-conventions)을 참조하십시오.

   페이지를 만드는 데 필요한 최소 정보는 **제목**&#x200B;입니다.

   ![페이지 제목 입력](/help/sites-cloud/authoring/assets/organizing-create-page-title.png)

1. 프로세스를 완료하고 새 페이지를 만들려면 **만들기**&#x200B;를 탭하거나 클릭합니다. 확인 대화 상자에 페이지를 즉시 **열기**&#x200B;할지 또는 콘솔로 돌아갈지(**완료**) 여부를 묻는 메시지가 표시됩니다. 하나를 선택하여 페이지 작성 프로세스를 종료합니다.

   ![페이지 작성 성공](/help/sites-cloud/authoring/assets/organizing-create-page-success.png)

   * **열기**&#x200B;를 선택하면 **사이트** 콘솔이 새 페이지의 템플릿을 기반으로 적절한 편집기를 엽니다.
      * [페이지 편집기](/help/sites-cloud/authoring/page-editor/introduction.md)
      * [유니버설 편집기](/help/sites-cloud/authoring/universal-editor/authoring.md)

콘솔로 돌아오면 새 페이지를 볼 수 있습니다.

![결과 새 페이지](/help/sites-cloud/authoring/assets/organizing-create-page-result.png)

>[!NOTE]
>
>동일한 위치에 이미 존재하는 이름을 사용하여 페이지를 만드는 경우 AEM에서는 숫자를 추가하여 지정된 이름의 변형 페이지를 만듭니다. 예를 들어 `beach`이(가) 이미 있으면 새 페이지는 `beach1`이(가) 됩니다.

>[!CAUTION]
>
>페이지가 만들어지면 [새 템플릿으로 론치를 만들기](/help/sites-cloud/authoring/launches/creating.md#create-launch-with-new-template)해야 해당 템플릿을 변경할 수 있지만, 이렇게 하면 기존 콘텐츠는 모두 손실됩니다.
