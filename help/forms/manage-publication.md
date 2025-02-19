---
title: 미리보기 또는 게시 인스턴스에 양식을 게시하거나 게시 취소하는 방법
description: AEM 작성 환경에서 양식을 게시 또는 게시 취소하여 인스턴스를 미리 보거나 게시하는 방법에 대해 알아봅니다. 스테이징 환경에서 양식을 테스트하든, 최종 사용자를 위해 라이브로 배포하든 상관없이 AEM에서는 이 프로세스를 효율적으로 관리할 수 있는 간소화된 도구를 제공합니다.
Keywords: Manage publication, Forms Manage publication, AF Manage publication, Adaptive Forms Manage publication, Cloud Manage publication
feature: Adaptive Forms
feature-set: Experience Manager Assets,Experience Manager Sites,Experience Manager, Experience Manager Forms, Experience Manager Cloud Manager
role: User, Developer
level: Intermediate
exl-id: 6ade40f1-bad5-4f5e-aa0e-84b7c6a82e02
source-git-commit: d8294c358bcc31b7c5e41e3103ec73adc05da6d9
workflow-type: tm+mt
source-wordcount: '945'
ht-degree: 1%

---


# Experience Manager Forms&#x200B;에서 게시 관리

Adobe Experience Manager(AEM) Forms 관리자는 작성자 인스턴스의 양식을 Experience Manager Forms에 게시할 수 있습니다. 양식 또는 폴더 게시를 나중 날짜 또는 시간으로 예약하는 옵션도 있습니다. 게시되면 사용자는 양식에 액세스하고 양식을 작성할 수 있습니다.

Experience Manager Forms에서는 다음 방법 중 하나를 사용하여 양식을 게시할 수 있습니다.
* [게시 옵션](#publish-forms-using-the-publish-option)
* [게시 관리 옵션](#publish-forms-using-the-manage-publication-option)

## 명심해야 할 사항

* `forms-users` 그룹의 구성원만 **게시 관리** 옵션을 사용하여 양식을 게시할 수 있습니다.
* Experience Manager Forms의 양식 또는 폴더에 대한 변경 사항은 다시 게시될 때까지 **Publish** 인스턴스에 표시되지 않습니다. 이렇게 하면 진행 중인 작업 업데이트가 **Publish** 인스턴스에서 계속 사용할 수 없게 됩니다. 관리자가 명시적으로 게시한 변경 사항만 **Publish** 인스턴스에 반영됩니다.

## 게시 옵션을 사용하여 양식 게시

**게시** 옵션을 사용하면 양식을 즉시 게시할 수 있습니다. 도구 모음의 **게시** 단추를 사용하여 Experience Manager 양식을 게시하려면 다음을 수행하십시오. 게시 옵션을 사용하여 양식을 게시하려면 다음 작업을 수행하십시오.

1. Experience Manager Forms 콘솔에서 상위 폴더로 이동하여 게시할 양식을 선택합니다.
1. 도구 모음에서 **게시** 옵션을 클릭하여 양식과 함께 게시되는 모든 참조 자산을 살펴보십시오.
1. **[!UICONTROL 게시]**&#x200B;를 클릭합니다.

   ![양식 게시 및 게시 취소](/help/edge/docs/forms/assets/publish-form-option.png)

   양식 및 관련 에셋이 게시되면 **성공** 대화 상자가 나타납니다.
1. **닫기**&#x200B;를 클릭합니다.

   ![완료 대화 상자](/help/forms/assets/publish-success1.png)

### 양식 게시 취소

**게시** 옵션 및 관련 자산을 사용하여 양식을 게시한 후 도구 모음에서 사용할 수 있는 **[!UICONTROL 게시 취소]** 단추를 사용하여 게시를 취소할 수도 있습니다. 양식 게시를 취소하려면 다음 작업을 수행하십시오.

1. 양식 및 관련 에셋의 게시를 취소하려면 양식을 선택하고 도구 모음에서 **[!UICONTROL 게시 취소]**&#x200B;를 클릭합니다

   **[!UICONTROL 게시 취소]** 단추를 클릭하면 **자산 게시 취소** 대화 상자가 나타납니다.
1. 게시 취소 프로세스를 시작하려면 **[!UICONTROL 게시 취소]**&#x200B;를 클릭하십시오.

   ![대화 상자 제거](/help/forms/assets/unpublish-asset.png)

   양식 및 관련 에셋의 게시가 취소되면 **성공** 대화 상자가 나타납니다.
1. **닫기**&#x200B;를 클릭합니다.

   ![게시 취소 완료](/help/forms/assets/unpublishing-start.png)

## 게시 관리 옵션을 사용하여 양식 게시

게시 관리를 사용하면 선택한 대상에 콘텐츠를 게시하거나 게시를 취소하고, `forms&documents` 폴더의 게시 목록에 콘텐츠를 추가하고, 게시할 참조를 선택하고, 나중에 게시할 날짜 또는 시간에 게시를 예약할 수 있습니다.  **게시 관리** 옵션을 사용하여 양식을 게시하려면 다음 작업을 수행하십시오.

1. Experience Manager Forms 콘솔에서 상위 폴더로 이동하여 게시할 양식을 선택합니다.
1. 도구 모음에서 **[!UICONTROL 게시 관리]** 옵션을 클릭합니다.

   ![게시 관리 옵션](/help/forms/assets/manage-publication-option.png)

   **게시 관리** UI가 표시됩니다.

   ![게시 관리](/help/forms/assets/manage-publication.png)

   **게시 관리** UI에서 다음 옵션을 사용할 수 있습니다.

   * **작업**

      * **게시**: 선택한 대상에 양식을 게시합니다.
      * **게시 취소**: 대상에서 양식 게시 취소

   * **대상**

      * **게시**: Experience Manager Forms(AEM) 게시 인스턴스에 양식을 게시합니다.
      * **미리 보기**: Experience Manager Forms(AEM) 미리 보기 인스턴스에 양식을 게시합니다.

   * **예약**

      * **지금**: 양식을 즉시 게시합니다.
      * **나중에**: **활성화 날짜** 또는 시간을 기준으로 양식을 게시합니다.

1. 계속하려면 **다음**&#x200B;을 클릭하세요.
1. (선택 사항) **범위** 탭에서 [콘텐츠 추가](#add-content) 옵션을 사용하여 게시할 콘텐츠를 더 추가합니다. 예를 들어 Forms 또는 기록 문서 파일을 더 추가할 수 있습니다.
   ![범위 탭](/help/forms/assets/scope-tab.png)
1. **[!UICONTROL 게시]**를 클릭하여 양식 및 관련 자산을 게시하고 성공적인 메시지가 나타납니다.
   ![성공한 메시지 게시](/help/forms/assets/publish-successful.png)

### 콘텐츠 추가

Experience Manager Forms에 게시하면 게시 목록에 더 많은 컨텐츠(양식)를 추가할 수 있습니다.
게시할 양식을 더 추가하려면 다음을 수행하십시오.

1. 콘텐츠를 추가하려면 **콘텐츠 추가** 단추를 클릭하십시오.

   ![콘텐츠 추가](/help/forms/assets/add-content.png)

2. **경로 선택** 화면에서 양식을 선택합니다.

   ![콘텐츠 추가](/help/forms/assets/add-assets.png)

   >[!NOTE]
   >
   > `formsanddocuments` 폴더의 목록에 더 많은 양식 또는 폴더를 추가할 수 있습니다. 그러나 한 번에 여러 폴더의 양식을 추가할 수는 없습니다.

3. 양식에 대해 게시하거나 게시하지 않도록 참조를 구성하려면 양식을 선택하고 **[!UICONTROL 게시된 참조]**&#x200B;를 클릭합니다.

   ![게시된 참조](/help/forms/assets/published-references.png)

4. **게시된 참조** 대화 상자에서 게시하지 않을 자산을 선택 취소하고 **[!UICONTROL 완료]**를 클릭합니다.
   ![게시된 참조 대화 상자](/help/forms/assets/published-references-dialog.png)

<!--
### Include Folder Settings
By default, publishing a folder to Experience Manager Forms publishes all the assets, subfolders, and their references. To filter the folder for publishing:

1. Click **[Include Folder Settings]** to filter the folder.

    ![Include folder](/help/forms/assets/include-folder.png)

    The **[UICONTROL Include Folder Settings]** dialog appears. 
    
    ![Include folder dialog](/help/forms/assets/include-folder-dialog.png)
    
    The **[UICONTROL Include Folder Settings]** includes following options:

    * **[!UICONTROL Include folder contents]** checkbox. 
        * If selected, all forms and assets in the chosen folder, its subfolders (including all forms and assets within them), and references are published.
        * If not selected, only the forms and assets in the selected folder are published, while subfolder forms and assets are not.

    * **[!UICONTROL Include only immediate folder contents]** checkbox
        Selecting the **[!UICONTROL Include folder contents]** checkbox enables the **[!UICONTROL Include only immediate folder contents]** checkbox for selection.

        * If you select both options, all the forms and assets of the selected folder, subfolders (empty), and references are published. The forms and assets of the subfolders are not published.
        * -->


### 나중에 양식 게시 또는 게시 취소

나중에 게시 또는 게시 취소 옵션을 사용하면 나중에 양식을 게시하거나 게시 취소할 수 있을 뿐만 아니라 워크플로우를 구성할 수도 있습니다. 워크플로가 완료된 후 양식이 게시되거나 게시 취소됩니다.

양식을 게시하거나 게시 취소하도록 예약하려면 다음 작업을 수행하십시오.

1. Experience Manager Forms 콘솔에서 상위 폴더로 이동하고 게시 일정을 예약하려는 양식을 선택합니다.
1. 도구 모음에서 **[!UICONTROL 게시 관리]** 옵션을 클릭합니다.

   ![게시 관리](/help/forms/assets/manage-publication.png)

1. **[!UICONTROL 작업]**&#x200B;에서 **게시** 또는 **게시 취소**&#x200B;를 클릭합니다.
1. 콘텐츠를 게시하거나 게시를 취소할 **[!UICONTROL 대상]**&#x200B;을(를) 선택하십시오.
   * **미리 보기**: **미리 보기** 옵션을 사용하여 Experience Manager Forms 미리 보기 환경에 게시하거나 게시를 취소하세요. Experience Manager Forms 미리보기 환경은 개발 양식에서 테스트하는 데 사용됩니다.
   * **게시**: 프로덕션 환경에서 양식을 사용할 준비가 되면 Experience Manager Forms **게시** 옵션을 사용하여 양식을 Experience Manager Forms 게시 환경에 보냅니다.

1. **예약**&#x200B;에서 **[!UICONTROL 나중에]**&#x200B;을(를) 선택하십시오.

   ![나중에 게시 관리](/help/forms/assets/manage-publication-later.png)

1. **[!UICONTROL 활성화 날짜]**&#x200B;를 선택하고 날짜와 시간을 지정하십시오.
1. **[!UICONTROL 다음]**&#x200B;을 클릭합니다.
1. (선택 사항) **범위** 탭에서 **[!UICONTROL 콘텐츠 추가]** 를 사용하여 콘텐츠를 추가합니다.
   ![나중에 게시 관리 콘텐츠 추가](/help/forms/assets/publish-later-add-content.png)
1. **[!UICONTROL 다음]**&#x200B;을 클릭합니다.
1. **워크플로** 탭에서 **[!UICONTROL 워크플로 제목]**&#x200B;을 지정하십시오.
1. **[!UICONTROL 나중에 게시]**&#x200B;를 클릭합니다.

   ![게시 워크플로 관리](/help/forms/assets/manage-publication-workflows.png)

## 게시 상태 확인

게시 상태를 확인하는 방법에는 여러 가지가 있습니다.

* 대상 인스턴스에 로그인하여 게시된 양식 및 기타 에셋을 확인합니다(예약된 날짜 또는 시간에 따라 다름).

* 타임라인 보기를 사용하여 게시 상태를 확인합니다.

* 적응형 Forms 편집기에서 페이지 정보 메뉴를 사용합니다.
