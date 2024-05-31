---
title: 핵심 구성 요소 기반 적응형 양식을 초안으로 저장하는 방법
description: 핵심 구성 요소 기반 적응형 양식을 초안으로 저장하고 Forms 포털을 만들고 AEM Sites 페이지에서 바로 사용할 수 있는 핵심 구성 요소를 사용하는 방법에 대해 알아봅니다.
feature: Adaptive Forms, Core Components
source-git-commit: 494e90bd5822495f0619e8ebf55f373a26a3ffe6
workflow-type: tm+mt
source-wordcount: '1072'
ht-degree: 1%

---


<span class="preview"> 이 문서에는 프리릴리스 기능에 대한 내용이 포함되어 있습니다. 프리릴리스 기능은 다음을 통해서만 액세스할 수 있습니다. [프리릴리스 채널](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/release-notes/prerelease.html#new-features).

# 핵심 구성 요소 기반 적응형 양식을 초안으로 저장 {#save-af-form}

적응형 양식을 초안으로 저장하는 것은 사용자 효율성과 정확성을 향상시키는 필수적인 기능입니다. 이 기능을 사용하면 진행 상황을 저장하고 나중에 입력한 정보를 손실하지 않고 작업을 완료할 수 있습니다. 제공  `save-as-draft` 옵션은 시간 관리의 유연성을 보장하고, 데이터 손실의 위험을 줄이며, 제출 작업의 정밀도를 유지합니다. 양식을 초안으로 저장하여 나중에 완료할 수 있습니다.

## 고려 사항

* [환경에 맞는 적응형 Forms 핵심 구성 요소를 활성화합니다.](/help/forms/enable-adaptive-forms-core-components.md)

* 다음을 확인합니다. [핵심 구성 요소가 버전 3.0.24 이상으로 설정되었습니다.](https://github.com/adobe/aem-core-forms-components) 을 클릭하여 이 기능을 사용하십시오.
* 다음 항목이 있는지 확인합니다. [Azure 스토리지 계정 및 액세스 키](https://learn.microsoft.com/en-us/azure/storage/common/storage-account-keys-manage?tabs=azure-portal) azure 스토리지 계정에 대한 액세스 권한을 부여합니다.

## 적응형 양식을 초안으로 저장

[!DNL Experience Manager Forms] 데이터 통합(data-integration.md)은 다음을 제공합니다 [!DNL Azure] 양식을 와 통합하기 위한 스토리지 구성 [!DNL Azure] 스토리지 서비스. FDM(양식 데이터 모델)을 사용하여 과 상호 작용하는 적응형 Forms을 만들 수 있습니다. [!DNL Azure] 비즈니스 워크플로를 활성화하는 서버입니다.

양식을 초안으로 저장하려면 Azure 스토리지 계정과 다음에 대한 액세스 권한을 부여할 액세스 키가 있는지 확인하십시오. [!DNL Azure] 저장소 계정입니다. 양식을 초안으로 저장하려면 다음 단계를 수행합니다.

1. [스토리지 구성 경로](#create-azure-storage-configuration)
1. [Forms 포털용 통합 스토리지 커넥터 구성](#configure-usc-forms-portal)
1. [적응형 양식을 초안으로 저장하는 규칙 만들기](#rule-to-save-adaptive-form-as-draft)


### 1. Azure 스토리지 구성 만들기 {#create-azure-storage-configuration}

Azure 스토리지 계정과 액세스 키가 있으면에서 액세스 권한을 부여합니다. [!DNL Azure] 저장소 계정에서 Azure 저장소 구성을 만들려면 다음 단계를 수행하십시오.

1. 다음으로 이동 **[!UICONTROL 도구]** > **[!UICONTROL Cloud Service]** > **[!UICONTROL Azure 스토리지]**.

   ![Azure 스토리지 카드 선택](/help/forms/assets/save-form-as-draft-azure-card.png)

1. 구성을 생성할 구성 폴더를 선택하고 **[!UICONTROL 만들기]**.

   ![Azure 스토리지 구성 폴더 선택](/help/forms/assets/save-form-as-draft-select-config-folder.png)

1. 에서 구성의 제목을 지정합니다. **[!UICONTROL 제목]** 필드.
1. 의 이름을 지정합니다. [!DNL Azure] 의 저장소 계정 **[!UICONTROL Azure 스토리지 계정]** 및 **[!UICONTROL Azure 액세스 키]** 필드.

   ![Azure Storage 구성](/help/forms/assets/save-form-as-draft-azure-storage.png)

1. **저장**&#x200B;을 클릭합니다.

>[!NOTE]
>
> 다음을 검색할 수 있습니다. **[!UICONTROL Azure 스토리지 계정]** 및 **[!UICONTROL Azure 액세스 키]** 다음에서 [Microsoft Azure 포털](https://learn.microsoft.com/en-us/azure/storage/common/storage-account-keys-manage?tabs=azure-portal).


### 2. Forms 포털용 통합 스토리지 커넥터 구성 {#configure-usc-forms-portal}

Azure 스토리지 구성을 만들었으면 다음 단계를 사용하여 Forms 포털용 통합 스토리지 커넥터를 구성하십시오.

1. 다음으로 이동 **[!UICONTROL 도구]** > **[!UICONTROL Forms]** > **[!UICONTROL 통합 스토리지 커넥터]**.

   ![통합 커넥터 스토리지](/help/forms/assets/save-form-as-draft-unified-connector.png)

1. 다음에서 **[!UICONTROL Forms 포털]** 섹션, 선택 **[!UICONTROL Azure]** 다음에서 **[!UICONTROL 스토리지]** 드롭다운 목록입니다.
1. 다음을 지정합니다. [azure 스토리지 구성에 대한 구성 경로](#create-azure-storage-configuration) 다음에서 **[!UICONTROL 스토리지 구성 경로]** 필드.

   ![통합 커넥터 스토리지 설정](/help/forms/assets/save-form-as-draft-unified-connector-storage.png)

1. 선택 **[!UICONTROL 저장]** 다음을 선택합니다. **[!UICONTROL 게시]** 구성을 게시합니다.

### 3. 적응형 양식을 초안으로 저장하는 규칙 만들기 {#rule-to-save-adaptive-form-as-draft}

양식을 초안으로 저장하려면 **양식 저장** 단추와 같은 양식 구성 요소에 대한 규칙입니다. 버튼을 클릭하면 규칙이 트리거되고 양식이 초안으로 저장됩니다. 다음 단계를 수행하여 을 만듭니다. **양식 저장** 버튼 구성 요소에 대한 규칙:

1. 작성자 인스턴스에서 편집 모드로 적응형 양식을 엽니다.
1. 왼쪽 창에서 을(를) 선택합니다 ![구성 요소 아이콘](assets/components_icon.png) 을(를) 끌어서 놓습니다. **[!UICONTROL 단추]** 구성 요소를 양식에 추가합니다.
1. 다음 항목 선택 **[!UICONTROL 단추]** 구성 요소를 선택한 다음 ![구성 아이콘](assets/configure_icon.png).
1. 다음 항목 선택 **[!UICONTROL 규칙 편집]** 아이콘을 클릭하여 규칙 편집기를 엽니다.
1. 선택 **[!UICONTROL 만들기]** 을 클릭하여 규칙을 구성하고 생성할 수 있습니다.
1. 다음에서 **[!UICONTROL 날짜]** 섹션, 선택 **클릭됨** 및 **[!UICONTROL 그러면]** 섹션에서 **양식 저장** 옵션을 선택합니다.
1. 선택 **[!UICONTROL 완료]** 을 눌러 규칙을 저장합니다.

![단추에 대한 규칙 만들기](/help/forms/assets/save-form-as-drfat-create-rule.png)

적응형 양식을 미리 볼 때 작성하고 을 클릭합니다. **양식 저장** 버튼을 누르면 양식이 나중에 사용할 수 있도록 초안으로 저장됩니다.

## AEM Sites 페이지에 초안을 나열할 초안 및 제출 구성 요소

AEM Forms은 **초안 및 제출** 포털 구성 요소를 통해 AEM Sites 페이지에 저장된 양식을 표시할 수 있습니다. 다음 **초안 및 제출** 구성 요소는 제출된 양식과 함께 나중에 완료할 수 있도록 초안으로 저장된 양식을 표시합니다. 이 구성 요소는 사용자가 만든 적응형 Forms과 관련된 초안 및 제출 사항을 나열하여 로그인한 사용자에게 개인화된 경험을 제공합니다.

기본 Forms 포털 구성 요소를 사용하여 AEM Sites 페이지에 양식 초안을 나열할 수 있습니다. 다음 단계를 수행하여 을 사용합니다. **초안 및 제출** 포털 구성 요소:

1. [초안 및 제출 Forms 포털 구성 요소 활성화](#enable-component)
2. [AEM Sites 페이지의 초안 및 제출 구성 요소 추가](#Add-drafts-submissions-component)
3. [초안 및 제출 구성 요소 구성](#configure-drafts-submissions-component)

### 1. 초안 및 제출 Forms 포털 구성 요소 활성화{#enable-component}

활성화하려면 **[!UICONTROL 초안 및 제출]** 템플릿 정책의 구성 요소에서 다음 단계를 수행합니다.

1. 에서 AEM Sites 페이지를 엽니다. **편집** 모드.
1. 로 이동 **[!UICONTROL 페이지 정보]** > **[!UICONTROL 템플릿 편집]**
   ![템플릿 정책 편집](/help/forms/assets/save-form-as-draft-edit-template.png)

1. 다음을 클릭합니다. **[!UICONTROL 정책]** 및 선택 **[!UICONTROL 초안 및 제출]**  확인란 **[AEM Archetype 프로젝트 이름] - Forms 및 통신 포털**.

   ![정책 선택](/help/forms/assets/save-form-as-draft-enable-policy.png)

1. **[!UICONTROL 완료]**&#x200B;를 클릭합니다.

포털 구성 요소가 활성화되면 AEM Sites 페이지의 작성자 인스턴스에서 사용할 수 있습니다.

### 2. AEM Sites 페이지의 초안 및 제출 구성 요소 추가{#Add-drafts-submissions-component}

포털 구성 요소를 추가 및 구성하여 AEM을 사용하여 작성된 웹 사이트에서 Forms 포털을 만들고 사용자 지정할 수 있습니다. 다음을 확인합니다. [초안 및 제출 구성 요소 활성화됨](#enable-component) AEM Sites 페이지에서 사용하기 전에.

구성 요소를 추가하려면 목록에서 구성 요소를 드래그 앤 드롭하십시오. **초안 및 제출** 구성 요소 창을 페이지의 레이아웃 컨테이너에 추가하거나 레이아웃 컨테이너에서 추가 아이콘을 선택하고 **[!UICONTROL 새 구성 요소 삽입]** 대화 상자.

![초안 및 제출 구성 요소 추가](/help/forms/assets/save-form-as-draft-add-dns.png)

### 3. 초안 및 제출 구성 요소 구성 {#configure-drafts-submissions-component}

다음 **초안 및 제출** 나중에 제출한 양식을 완료하기 위해 초안으로 저장된 양식이 구성 요소에 표시됩니다. 구성하려면 **초안 및 제출**&#x200B;를 클릭하고 다음 단계를 수행하십시오.
1. 다음 항목 선택 **초안 및 제출** 구성 요소.
1. 다음을 클릭합니다. ![구성 아이콘](assets/configure_icon.png) 그러면 대화상자가 나타납니다.
1. 다음에서 **[!UICONTROL 초안 및 제출]** 대화 상자에서 다음을 지정합니다.
   * **제목** Sites 페이지에서 구성 요소를 식별하기 위해 기본적으로 제목이 구성 요소 위에 나타납니다.
   * **유형**: 양식 목록을 초안 또는 제출된 양식으로 표시합니다.
   * **레이아웃**: 목록 초안 양식 또는 제출된 양식을 카드 또는 목록 형식으로 표시합니다.

   ![초안 및 제출 구성 요소 등록 정보](/help/forms/assets/save-form-as-draft-dns-properties.png)

1. **완료**&#x200B;를 클릭합니다.

날짜 **[!UICONTROL 유형 선택]** 이(가) 다음으로 선택됨 **초안 Forms**, 초안으로 저장된 양식이 표시됩니다.
![초안 아이콘](assets/drafts-component.png)

날짜 **[!UICONTROL 유형 선택]** 이(가) 다음으로 선택됨 **제출된 Forms**, 제출된 양식이 표시됩니다.

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