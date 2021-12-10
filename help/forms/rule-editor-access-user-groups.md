---
title: 사용자 그룹을 선택하는 규칙 편집기 액세스 권한을 부여하는 방법
description: 적응형 Forms과 함께 작동하는 다양한 기술을 사용하는 사용자 유형은 다양합니다. 역할 또는 기능에 따라 규칙 편집기 액세스를 사용자로 제한하는 방법을 알아봅니다.
feature: Adaptive Forms
role: User
level: Beginner, Intermediate
source-git-commit: 7163eb2551f5e644f6d42287a523a7dfc626c1c4
workflow-type: tm+mt
source-wordcount: '322'
ht-degree: 3%

---


# 사용자 그룹을 선택하는 규칙 편집기 액세스 부여 {#grant-rule-editor-access-to-select-user-groups}

## 개요 {#overview}

적응형 Forms과 함께 작동하는 다양한 기술을 사용하는 사용자 유형은 다양합니다. 전문가 사용자에게는 스크립트 및 복잡한 규칙으로 작업하는 올바른 지식이 있을 수 있지만, 적응형 Forms의 레이아웃 및 기본 속성으로만 작업해야 하는 기본 수준 사용자가 있을 수 있습니다.

[!DNL Experience Manager Forms] 사용자의 역할이나 기능을 기준으로 규칙 편집기 액세스를 제한할 수 있습니다. 응용 Forms 구성 서비스 설정에서 [사용자 그룹](forms-groups-privileges-tasks.md) 규칙 편집기를 보고 액세스할 수 있습니다.

## 규칙 편집기에 액세스할 수 있는 사용자 그룹을 지정합니다 {#specify-user-groups-that-can-access-rule-editor}

1. 에 로그인합니다. [!DNL Experience Manager Forms] 관리자로.
1. 작성자 인스턴스에서 를 클릭합니다. ![Adobe Experience Manager](assets/adobeexperiencemanager.png)Adobe Experience Manager > 도구 ![망치](assets/hammer-icon.svg) > **[!UICONTROL 작업]** > **[!UICONTROL 웹 콘솔]**. 웹 콘솔이 새 창에 열립니다.

   ![1-2](assets/1-2.png)

1. in [!UICONTROL 웹 콘솔] 창, 위치 및 클릭 **[!UICONTROL 적응형 양식 구성 서비스]**. **[!UICONTROL 적응형 양식 구성 서비스]** 대화 상자가 나타납니다. 값을 변경하지 않고 **[!UICONTROL 저장]**.

   파일을 만듭니다 `/apps/system/config/com.adobe.aemds.guide.service.impl.AdaptiveFormConfigurationServiceImpl.config` CRX-repository에서 제거합니다.

1. 관리자로 CRXDE에 로그인합니다. 파일 열기 `/apps/system/config/com.adobe.aemds.guide.service.impl.AdaptiveFormConfigurationServiceImpl.config` 참조하십시오.
1. 다음 속성을 사용하여 규칙 편집기에 액세스할 수 있는 그룹 이름(예: RuleEditorsUserGroup)을 지정하고 **[!UICONTROL 모두 저장]**.

   `af.ruleeditor.custom.groups=["RuleEditorsUserGroup"]`

   여러 그룹에 대한 액세스를 활성화하려면 쉼표로 구분된 값 목록을 지정하십시오.

   `af.ruleeditor.custom.groups=["RuleEditorsUserGroup", "PermittedUserGroup"]`

   ![사용자 만들기](assets/create_user_new.png)

   이제, 지정된 사용자 그룹의 일부가 아닌 사용자가    `RuleEditorsUserGroup`)가 필드를 탭합니다. 규칙 편집 아이콘( ![edit-rules1](assets/edit-rules1.png))은 구성 요소 도구 모음에서 사용할 수 없습니다.

   ![componentstoolbarwitter](assets/componentstoolbarwithre.png)

   구성 요소 도구 모음이 규칙 편집기 액세스 권한이 있는 사용자에게 표시되는 대로 표시됩니다.

   ![componentstoolbarwithout](assets/componentstoolbarwithoutre.png)

   규칙 편집기 액세스 권한이 없는 사용자에게 표시되는 구성 요소 도구 모음

   그룹에 사용자 추가에 대한 지침은 [사용자 관리 및 보안](https://experienceleague.adobe.com/docs/experience-manager-65/administering/security/security.html).

