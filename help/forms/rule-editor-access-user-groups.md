---
title: 사용자 그룹을 선택하기 위해 AEM 적응형 양식 규칙 편집기에 대한 액세스 권한을 제공하는 방법은 무엇입니까?
description: 적응형 Forms과 작동하는 다양한 스킬을 가진 다양한 유형의 사용자가 있습니다. 역할 또는 기능에 따라 규칙 편집기 액세스를 사용자에게 제한하는 방법에 대해 알아봅니다.
feature: Adaptive Forms
role: User
level: Beginner, Intermediate
hide: true
hidefromtoc: true
source-git-commit: 937bd4653e454beea3111cfc7ef7b4bbc1ace193
workflow-type: tm+mt
source-wordcount: '320'
ht-degree: 2%

---


# 사용자 그룹을 선택하는 규칙 편집기 액세스 부여 {#grant-rule-editor-access-to-select-user-groups}

## 개요 {#overview}

적응형 Forms과 작동하는 다양한 스킬을 가진 다양한 유형의 사용자가 있습니다. 전문가 사용자는 스크립트 및 복잡한 규칙을 사용하여 작업할 수 있는 적절한 지식을 보유할 수 있지만 적응형 Forms의 레이아웃 및 기본 속성으로만 작업해야 하는 기본 수준 사용자가 있을 수 있습니다.

[!DNL Experience Manager Forms]을(를) 사용하면 규칙 편집기 액세스를 사용자의 역할이나 기능에 따라 제한할 수 있습니다. 적응형 Forms 구성 서비스 설정에서 규칙 편집기를 보고 액세스할 수 있는 [사용자 그룹](forms-groups-privileges-tasks.md)을 지정할 수 있습니다.

## 규칙 편집기에 액세스할 수 있는 사용자 그룹 지정 {#specify-user-groups-that-can-access-rule-editor}

1. [!DNL Experience Manager Forms]에 관리자로 로그인합니다.
1. 작성자 인스턴스에서 ![Adobe Experience Manager](assets/adobeexperiencemanager.png)Adobe Experience Manager > 도구 ![hammer](assets/hammer-icon.svg) > **[!UICONTROL 작업]** > **[!UICONTROL 웹 콘솔]**&#x200B;을 클릭합니다. 웹 콘솔이 새 창에 열립니다.

   ![1-2](assets/1-2.png)

1. [!UICONTROL 웹 콘솔] 창에서 **[!UICONTROL 적응형 양식 구성 서비스]**&#x200B;를 찾아 클릭합니다. **[!UICONTROL 적응형 양식 구성 서비스]** 대화 상자가 나타납니다. 값을 변경하지 말고 **[!UICONTROL 저장]**&#x200B;을 클릭하세요.

   CRX 저장소에 `/apps/system/config/com.adobe.aemds.guide.service.impl.AdaptiveFormConfigurationServiceImpl.config` 파일을 만듭니다.

1. CRXDE에 관리자로 로그인합니다. 편집할 `/apps/system/config/com.adobe.aemds.guide.service.impl.AdaptiveFormConfigurationServiceImpl.config` 파일을 엽니다.
1. 다음 속성을 사용하여 규칙 편집기(예: RuleEditorsUserGroup)에 액세스할 수 있는 그룹의 이름을 지정하고 **[!UICONTROL 모두 저장]**&#x200B;을 클릭합니다.

   `af.ruleeditor.custom.groups=["RuleEditorsUserGroup"]`

   여러 그룹에 대한 액세스를 활성화하려면 쉼표로 구분된 값 목록을 지정합니다.

   `af.ruleeditor.custom.groups=["RuleEditorsUserGroup", "PermittedUserGroup"]`

   ![사용자 만들기](assets/create_user_new.png)

   이제 지정된 사용자 그룹에 속하지 않는 사용자일 경우    `RuleEditorsUserGroup`) 필드를 탭합니다. 구성 요소 도구 모음에서 규칙 편집 아이콘(![edit-rules1](assets/edit-rules1.png))을 사용할 수 없습니다.

   ![componentstoolbarwithre](assets/componentstoolbarwithre.png)

   규칙 편집기 액세스 권한이 있는 사용자가 볼 수 있는 구성 요소 도구 모음:

   ![componentstoolbarwithouter](assets/componentstoolbarwithoutre.png)

   규칙 편집기 액세스 권한 없이 사용자가 볼 수 있는 구성 요소 도구 모음

   그룹에 사용자를 추가하는 방법에 대한 지침은 [사용자 관리 및 보안](https://experienceleague.adobe.com/docs/experience-manager-65/administering/security/security.html)을 참조하세요.

