---
title: Cloud Manager에서 외부 저장소의 액세스 토큰 관리
description: AEM Cloud Manager에서 나만의 Git 가져오기에 사용되는 액세스 토큰을 보고, 편집하고, 삭제하는 방법에 대해 알아봅니다.
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
badge: label="얼리 어답터" type="Positive" url="/help/implementing/cloud-manager/release-notes/current.md#manage-access-tokens"
exl-id: bc9f392c-61f5-4d39-972b-4c6c8f9bab4a
source-git-commit: 9f9f931a233320014675c6aac86a2cc65f6909c6
workflow-type: tm+mt
source-wordcount: '420'
ht-degree: 3%

---

# 외부 저장소에 대한 액세스 토큰 관리 {#manage-access-tokens}

Cloud Manager은 액세스 토큰을 사용하여 외부 Git 플랫폼에서 호스팅되는 저장소를 관리합니다. 이전에는 토큰이 만료되면 연결된 저장소를 다시 온보딩하여 계속 작동해야 했습니다.

이제 **액세스 토큰 관리** 기능을 사용하여 토큰을 보다 효율적으로 관리할 수 있습니다. GitHub Enterprise, GitLab, Bitbucket 및 Azure DevOps를 포함하여 지원되는 외부 Git 공급자에 연결된 토큰을 보고, 이름을 바꾸거나, 제거할 수 있습니다.

[Cloud Manager에 외부 저장소 추가](/help/implementing/cloud-manager/managing-code/external-repositories.md)도 참조하세요.

>[!NOTE]
>
>이 문서에 설명된 기능은 조기 채택 프로그램을 통해서만 사용할 수 있습니다. 자세한 내용을 알고 얼리 어답터로 등록하려면 [자신의 Git 가져오기](/help/implementing/cloud-manager/release-notes/current.md#gitlab-bitbucket)를 참조하세요.

## 액세스 토큰 보기 {#view-access-tokens}

1. [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/)에서 Cloud Manager에 로그인한 다음 적절한 조직을 선택합니다.
1. **[내 프로그램](/help/implementing/cloud-manager/navigation.md#my-programs)** 콘솔에서 관리하려는 Git 액세스 토큰을 가져올 프로그램을 선택합니다.
1. 사이드 메뉴의 **프로그램**&#x200B;에서 ![폴더 개요 아이콘](https://spectrum.adobe.com/static/icons/workflow_18/Smock_FolderOutline_18_N.svg) **저장소**&#x200B;를 클릭합니다.
1. 페이지의 오른쪽 상단 모서리에서 **액세스 토큰 관리**&#x200B;를 클릭합니다.

   **액세스 토큰 관리** 단추는 프로그램에서 Git 가져오기 기능을 사용하는 경우에만 표시됩니다.

   ![활성 토큰 하나와 비활성 토큰 하나를 나열하는 액세스 토큰 관리 대화 상자](/help/implementing/cloud-manager/managing-code/assets/access-tokens-manage.png)

1. **액세스 토큰 관리** 대화 상자에서 다음을 수행합니다.
   * 모든 액세스 토큰이 나열됩니다.
   * 모든 액세스 토큰을 **편집**&#x200B;할 수 있습니다.
   * *현재 사용 중이 아닌 액세스 토큰만&#x200B;**삭제**&#x200B;할 수 있습니다*. 토큰을 사용 중이면 ![개요 삭제 아이콘](https://spectrum.adobe.com/static/icons/workflow_18/Smock_DeleteOutline_18_N.svg) 단추가 비활성화됩니다.

## 액세스 토큰 편집 {#edit-access-tokens}

1. 토큰 이름의 오른쪽에 있는 **액세스 토큰 관리** 대화 상자에서 ![편집 아이콘](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Edit_18_N.svg)을 클릭합니다.
1. **액세스 토큰 편집** 대화 상자에서 **토큰 이름**, **액세스 토큰** 값 또는 둘 다를 업데이트하십시오.

   **액세스 토큰**&#x200B;이(가) 현재 사용 중이면 업데이트 후 연결된 모든 저장소의 유효성을 자동으로 다시 검사한다는 알림이 표시됩니다.

   ![액세스 토큰 편집 대화 상자](/help/implementing/cloud-manager/managing-code/assets/access-tokens-edit.png)

1. 토큰이 사용 중이면 연관된 모든 저장소의 유효성이 자동으로 재확인된다는 알림이 표시됩니다.

1. 변경 내용을 저장하려면 **업데이트**&#x200B;를 클릭하세요.

## 액세스 토큰 삭제 {#delete-access-token}

1. 토큰 이름의 오른쪽에 있는 **액세스 토큰 관리** 대화 상자에서 ![삭제 아이콘](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Delete_18_N.svg)을 클릭합니다

   현재 사용 중인 토큰에 대해 아이콘이 비활성화되었습니다(![개요 삭제 아이콘](https://spectrum.adobe.com/static/icons/workflow_18/Smock_DeleteOutline_18_N.svg)).

1. **액세스 토큰 삭제** 대화 상자에서 **삭제**&#x200B;을 클릭하여 토큰을 영구적으로 제거하십시오.
