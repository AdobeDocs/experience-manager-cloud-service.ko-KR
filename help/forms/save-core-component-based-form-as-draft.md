---
title: 핵심 구성 요소 기반 적응형 양식을 초안으로 저장하는 방법
description: 핵심 구성 요소 기반 적응형 양식을 초안으로 저장하고 Forms 포털을 만들고 AEM Sites 페이지에서 바로 사용할 수 있는 핵심 구성 요소를 사용하는 방법에 대해 알아봅니다.
feature: Adaptive Forms, Core Components
exl-id: c0653bef-afeb-40c1-b131-7d87ca5542bc
role: User, Developer, Admin
source-git-commit: 52b87073cad84705b5dc0c6530aff44d1e686609
workflow-type: tm+mt
source-wordcount: '1053'
ht-degree: 2%

---


# 핵심 구성 요소 기반 적응형 양식을 초안으로 저장 {#save-af-form}

적응형 양식을 초안으로 저장하는 것은 사용자 효율성과 정확성을 향상시키는 필수적인 기능입니다. 이 기능을 사용하면 진행 상황을 저장하고 나중에 입력한 정보를 손실하지 않고 작업을 완료할 수 있습니다. `save-as-draft` 옵션을 제공하면 시간 관리를 유연하게 하고, 데이터 손실 위험을 줄이고, 제출의 정밀도를 유지할 수 있습니다. 양식을 초안으로 저장하여 나중에 완료할 수 있습니다.

## 고려 사항

* [환경에 맞는 적응형 Forms 핵심 구성 요소를 활성화합니다.](/help/forms/enable-adaptive-forms-core-components.md)

* 이 기능을 사용하려면 [핵심 구성 요소가 버전 3.0.24 이상으로 설정되어 있는지 확인](https://github.com/adobe/aem-core-forms-components)하십시오.
* Azure 저장소 계정에 대한 액세스 권한을 부여할 [Azure 저장소 계정과 액세스 키](https://learn.microsoft.com/en-us/azure/storage/common/storage-account-keys-manage?tabs=azure-portal)가 있는지 확인하세요.

## 적응형 양식을 초안으로 저장

[!DNL Experience Manager Forms] 데이터 통합(data-integration.md)은 [!DNL Azure] 저장소 서비스와 양식을 통합하는 [!DNL Azure] 저장소 구성을 제공합니다. 양식 데이터 모델(FDM)을 사용하여 [!DNL Azure] 서버와 상호 작용하여 비즈니스 워크플로를 가능하게 하는 적응형 Forms을 만들 수 있습니다.

양식을 초안으로 저장하려면 Azure 저장소 계정 및 [!DNL Azure] 저장소 계정에 대한 액세스 권한을 부여하는 액세스 키가 있는지 확인하세요. 양식을 초안으로 저장하려면 다음 단계를 수행합니다.

1. [스토리지 구성 경로](#create-azure-storage-configuration)
1. [Forms 포털용 통합 스토리지 커넥터 구성](#configure-usc-forms-portal)
1. [적응형 양식을 초안으로 저장하는 규칙 만들기](#rule-to-save-adaptive-form-as-draft)


### 1. Azure 스토리지 구성 만들기 {#create-azure-storage-configuration}

Azure 저장소 계정과 [!DNL Azure] 저장소 계정에 대한 액세스 권한을 부여하는 액세스 키가 있으면 다음 단계를 수행하여 Azure 저장소 구성을 만드십시오.

1. **[!UICONTROL 도구]** > **[!UICONTROL Cloud Service]** > **[!UICONTROL Azure 저장소]**&#x200B;로 이동합니다.

   ![Azure 저장소 카드 선택](/help/forms/assets/save-form-as-draft-azure-card.png)

1. 구성을 만들 구성 폴더를 선택하고 **[!UICONTROL 만들기]**&#x200B;를 선택합니다.

   ![Azure 저장소 구성 폴더 선택](/help/forms/assets/save-form-as-draft-select-config-folder.png)

1. **[!UICONTROL 제목]** 필드에 구성의 제목을 지정합니다.
1. **[!UICONTROL Azure 저장소 계정]** 및 **[!UICONTROL Azure 액세스 키]** 필드에 [!DNL Azure] 저장소 계정의 이름을 지정하십시오.

   ![Azure Storage 구성](/help/forms/assets/save-form-as-draft-azure-storage.png)

1. **저장**&#x200B;을 클릭합니다.

>[!NOTE]
>
> [Microsoft Azure 포털](https://learn.microsoft.com/en-us/azure/storage/common/storage-account-keys-manage?tabs=azure-portal)에서 **[!UICONTROL Azure 저장소 계정]** 및 **[!UICONTROL Azure 액세스 키]**&#x200B;를 검색할 수 있습니다.


### 2. Forms 포털용 통합 스토리지 커넥터 구성 {#configure-usc-forms-portal}

Azure 스토리지 구성을 만들었으면 다음 단계를 사용하여 Forms 포털용 통합 스토리지 커넥터를 구성하십시오.

1. **[!UICONTROL 도구]** > **[!UICONTROL Forms]** > **[!UICONTROL 통합 저장소 커넥터]**&#x200B;로 이동합니다.

   ![통합 커넥터 저장소](/help/forms/assets/save-form-as-draft-unified-connector.png)

1. **[!UICONTROL Forms 포털]** 섹션의 **[!UICONTROL 저장소]** 드롭다운 목록에서 **[!UICONTROL Azure]**&#x200B;을(를) 선택합니다.
1. **[!UICONTROL 저장소 구성 경로]** 필드에 Azure 저장소 구성에 대한 [구성 경로](#create-azure-storage-configuration)를 지정하십시오.

   ![통합 커넥터 저장소 설정](/help/forms/assets/save-form-as-draft-unified-connector-storage.png)

1. **[!UICONTROL 저장]**&#x200B;을 선택한 다음 **[!UICONTROL Publish]**&#x200B;을 선택하여 구성을 게시합니다.

### 3. 적응형 양식을 초안으로 저장하는 규칙 만들기 {#rule-to-save-adaptive-form-as-draft}

양식을 초안으로 저장하려면 단추와 같은 양식 구성 요소에 **양식 저장** 규칙을 만듭니다. 버튼을 클릭하면 규칙이 트리거되고 양식이 초안으로 저장됩니다. 단추 구성 요소에 **양식 저장** 규칙을 만들려면 다음 단계를 수행하십시오.

1. 작성자 인스턴스에서 편집 모드로 적응형 양식을 엽니다.
1. 왼쪽 창에서 ![구성 요소 아이콘](assets/components_icon.png)을(를) 선택하고 **[!UICONTROL Button]** 구성 요소를 양식으로 끌어 옵니다.
1. **[!UICONTROL Button]** 구성 요소를 선택한 다음 ![구성 아이콘](assets/configure_icon.png)을 선택합니다.
1. **[!UICONTROL 규칙 편집]** 아이콘을 선택하여 규칙 편집기를 엽니다.
1. 규칙을 구성하고 만들려면 **[!UICONTROL 만들기]**&#x200B;를 선택하십시오.
1. **[!UICONTROL When]** 섹션에서 **클릭됨**&#x200B;을(를) 선택하고 **[!UICONTROL Then]** 섹션에서 **양식 저장** 옵션을 선택합니다.
1. **[!UICONTROL 완료]**&#x200B;를 선택하여 규칙을 저장합니다.

![단추에 대한 규칙 만들기](/help/forms/assets/save-form-as-drfat-create-rule.png)

적응형 양식을 미리 보고 작성하고 **양식 저장** 단추를 클릭하면 양식이 나중에 사용할 수 있도록 초안으로 저장됩니다.

## AEM Sites 페이지에 초안을 나열할 초안 및 제출 구성 요소

AEM Forms은 저장된 양식을 AEM Sites 페이지에 표시할 수 있도록 **초안 및 제출** 포털 구성 요소를 즉시 제공합니다. **초안 및 제출** 구성 요소는 나중에 완료할 수 있도록 초안으로 저장된 양식과 제출된 양식을 표시합니다. 이 구성 요소는 사용자가 만든 적응형 Forms과 관련된 초안 및 제출 사항을 나열하여 로그인한 사용자에게 개인화된 경험을 제공합니다.

기본 Forms 포털 구성 요소를 사용하여 AEM Sites 페이지에 양식 초안을 나열할 수 있습니다. **초안 및 제출** 포털 구성 요소를 사용하려면 다음 단계를 수행하십시오.

1. [초안 및 제출 Forms 포털 구성 요소 활성화](#enable-component)
2. [AEM Sites 페이지의 초안 및 제출 구성 요소 추가](#Add-drafts-submissions-component)
3. [초안 및 제출 구성 요소 구성](#configure-drafts-submissions-component)

### 1. 초안 및 제출 Forms 포털 구성 요소 활성화{#enable-component}

템플릿 정책에서 **[!UICONTROL 초안 및 제출]** 구성 요소를 활성화하려면 다음 단계를 수행하십시오.

1. **편집** 모드로 AEM Sites 페이지를 엽니다.
1. **[!UICONTROL 페이지 정보]** > **[!UICONTROL 템플릿 편집]**(으)로 이동
   ![템플릿 정책 편집](/help/forms/assets/save-form-as-draft-edit-template.png)

1. **[!UICONTROL 정책]**&#x200B;을 클릭하고 **[AEM Archetype 프로젝트 이름] - Forms 및 통신 포털**&#x200B;에서 **[!UICONTROL 초안 및 제출]** 확인란을 선택하십시오.

   ![정책 선택](/help/forms/assets/save-form-as-draft-enable-policy.png)

1. **[!UICONTROL 완료]**&#x200B;를 클릭합니다.

포털 구성 요소가 활성화되면 AEM Sites 페이지의 작성자 인스턴스에서 사용할 수 있습니다.

### 2. AEM Sites 페이지의 초안 및 제출 구성 요소 추가{#Add-drafts-submissions-component}

포털 구성 요소를 추가 및 구성하여 AEM을 사용하여 작성된 웹 사이트에서 Forms 포털을 만들고 사용자 지정할 수 있습니다. AEM Sites 페이지에서 초안 및 제출 구성 요소를 사용하기 전에 [초안 및 제출 구성 요소가 활성화되었는지](#enable-component) 확인하십시오.

구성 요소를 추가하려면 **초안 및 제출** 구성 요소 창에서 페이지의 레이아웃 컨테이너로 구성 요소를 드래그 앤 드롭하거나 레이아웃 컨테이너에서 추가 아이콘을 선택하고 **[!UICONTROL 새 구성 요소 삽입]** 대화 상자에서 구성 요소를 추가하십시오.

![초안 및 제출 구성 요소 추가](/help/forms/assets/save-form-as-draft-add-dns.png)

### 3. 초안 및 제출 구성 요소 구성 {#configure-drafts-submissions-component}

**초안 및 제출** 구성 요소는 나중에 제출한 양식을 완성하기 위해 초안으로 저장된 양식을 표시합니다. **초안 및 제출**&#x200B;을 구성하려면 다음 단계를 수행하십시오.
1. **초안 및 제출** 구성 요소를 선택하십시오.
1. ![구성 아이콘](assets/configure_icon.png)을 클릭하면 대화 상자가 나타납니다.
1. **[!UICONTROL 초안 및 제출]** 대화 상자에서 다음을 지정하십시오.
   * **제목** Sites 페이지에서 구성 요소를 식별하기 위해 기본적으로 제목이 구성 요소 위에 나타납니다.
   * **Type**: 양식이 초안 또는 제출된 양식으로 나열됨을 나타냅니다.
   * **레이아웃**: 목록 초안 양식이나 제출된 양식을 카드 또는 목록 형식으로 표시합니다.

   ![초안 및 제출 구성 요소 속성](/help/forms/assets/save-form-as-draft-dns-properties.png)

1. **완료**&#x200B;를 클릭합니다.

**[!UICONTROL 유형 선택]**&#x200B;을(를) **초안 Forms**(으)로 선택하면 초안으로 저장된 양식이 표시됩니다.
![초안 아이콘](assets/drafts-component.png)

**[!UICONTROL 유형 선택]**&#x200B;을(를) **제출된 Forms**(으)로 선택하면 제출된 양식이 표시됩니다.

![제출 아이콘](assets/submission-listing.png)

해당 양식을 클릭하여 양식을 열 수 있습니다.

<!--

### Configure Search & Lister Component {#configure-search-lister-component}

The Search & Lister component is used to list adaptive forms on a page and to implement search on the listed forms. 

![Search and Lister icon](assets/search-and-lister-component.png)

To configure, select the component and then select the ![Configure icon](assets/configure_icon.png). The [!UICONTROL Search and Lister] dialog opens.

1. In the [!UICONTROL Display] tab, configure the following:
    * In **[!UICONTROL Title]**, specify the title for the Search & Lister component. An indicative title enables the users perform quick search across the list of forms.
    * From the **[!UICONTROL Layout]** list, select the layout to represent the forms in card or list format.
    * Select **[!UICONTROL Hide Search]** and **[!UICONTROL Hide Sorting]** to hide the search and sort by features.
    * In **[!UICONTROL Tooltip]**, provide the tooltip that appears when you hover over the component. 
1. In the [!UICONTROL Asset Folder] tab, specify the location from where the forms are pulled and listed on the page. You can configure multiple folder locations.
1. In the [!UICONTROL Results] tab, configure the maximum number of forms to display per page. The default is eight forms per page.

### Configure Link Component {#configure-link-component}

The link component enables you to provide links to an adaptive form on the page. To configure, select the component and then select the ![Configure icon](assets/configure_icon.png). The [!UICONTROL Edit Link Component] dialog opens.

1. In the [!UICONTROL Display] tab, provide the link caption and tooltip to ease identification of the forms represented by the link.
1. In the [!UICONTROL Asset Info] tab, specify the repository path where the asset is stored. 
1. In the [!UICONTROL Query Params] tab, specify the additional parameters in the key-value pair format. When the link is clicked, these additional parameters and passed along with the form.

## Configure Asynchronous Form Submission Using Adobe Sign {#configure-asynchronous-form-submission-using-adobe-sign}

You can configure to submit an adaptive form only when all the recipients have completed the signing ceremony. Follow the steps below to configure the setting using Adobe Sign.

1. In the author instance, open an Adaptive Form in the edit mode.
1. From the left pane, select the Properties icon and expand the **[!UICONTROL ELECTRONIC SIGNTATURE]** option.
1. Select **[!UICONTROL Enable Adobe Sign]**. Various configuration options display. 
1. In the [!UICONTROL Submit the form] section, select the **[!UICONTROL after every recipient completes signing ceremony]** option to configure the Submit Form action, where the form is first sent to all the recipients for signing. Once all the recipients have signed the form, only then the form is submitted. 

## Save Adaptive Forms As Drafts {#save-adaptive-forms-as-drafts}

You can save forms as Drafts for completing them later. There are two ways in which a form is saved as a draft:

* Create a "Save Form" rule on a form component, for example, a button. On clicking the button, the rule triggers and the form are saved a draft.
* Enable Auto-Save feature, which saves the form as per the specified event or after a configured interval of time.

### Create Rules to Save an Adaptive Form as Draft {#rule-to-save-adaptive-form-as-draft}

To create a "Save Form" rule on a form component, for example, a button, follow the steps below:

1. In the author instance, open an Adaptive Form in edit mode.
1. From the left pane, select ![Components icon](assets/components_icon.png) and drag the [!UICONTROL Button] component to the form.
1. Select the [!UICONTROL Button] component and then select the ![Configure icon](assets/configure_icon.png). 
1. Select the [!UICONTROL Edit Rules] icon to open the Rule Editor. 
1. Select **[!UICONTROL Create]** to configure and create the rule.
1. In the [!UICONTROL When] section, select "is clicked" and in the [!UICONTROL Then] section, select the "Save Form" options.
1. Select **[!UICONTROL Done]** to save the rule.

### Enable Auto-save {#enable-auto-save}

You can configure the auto-save feature for an adaptive form as follows:

1. In the author instance, open an Adaptive Form in edit mode.
1. From the left pane, select the ![Properties icon](assets/configure_icon.png) and expand the [!UICONTROL AUTO-SAVE] option.
1. Select the **[!UICONTROL Enable]** check box to enable auto-save of the form. You can configure the following:
* By default, the [!UICONTROL Adaptive Form Event] is set to "true", which implies that the form is auto-saved after every event.
* In [!UICONTROL Trigger], configure to trigger auto-save based on the occurrence of an event or after a specific interval of time.
-->

## 추가 참조 {#see-also}

{{see-also}}



<!--

>[!MORELIKETHIS]
>
>* [Configure data sources for AEM Forms](/help/forms/configure-data-sources.md)
>* [Configure Azure storage for AEM Forms](/help/forms/configure-azure-storage.md)
>* [Integrate Microsoft Dynamics 365 and Salesforce with Adaptive Forms](/help/forms/configure-msdynamics-salesforce.md)

-->
