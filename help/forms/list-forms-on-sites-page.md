---
title: Forms 포털 구성 요소를 사용하여 Adobe Experience Manager Sites 페이지에 양식을 나열하는 방법
description: AEM Sites 페이지에 양식을 나열하는 방법을 알아봅니다.
feature: Adaptive Forms, Core Components
role: User, Developer
source-git-commit: 58533d9a950fa4dc0e043ef8cb935d65fc68d233
workflow-type: tm+mt
source-wordcount: '673'
ht-degree: 1%

---


# 사이트 페이지의 목록 양식

사용자가 계좌 개설 양식을 찾아 은행의 웹 사이트를 방문한다고 상상해 보십시오. 은행은 Forms 포털 구성 요소를 사용하여 사용자가 특정 키워드를 입력하거나 &#39;새 계정&#39; 또는 &#39;개인 뱅킹&#39;과 같은 카테고리별로 필터링하여 양식을 신속하게 찾을 수 있도록 지원하며, 사용자가 긴 목록을 스크롤하지 않고도 원하는 양식을 쉽게 찾을 수 있도록 합니다.

Forms 포털의 **검색 및 목록 작성기** 구성 요소를 사용하여 Sites 페이지에 양식을 표시하고 나열할 수 있습니다. 사용자는 조직 요구 사항을 충족하기 위해 특정 기준에 따라 포괄적인 양식 목록을 구성하고 제공할 수 있습니다. 익명의 사용자는 사이트 페이지를 방문하여 사용 가능한 양식을 보고 검색할 수 있습니다. 화면의 오른쪽 상단에 있는 **정렬 기준** 드롭다운 옵션을 사용하여 나열된 양식을 오름차순 또는 내림차순으로 정렬할 수 있습니다.

![검색 및 목록 작성자 아이콘](assets/search-and-lister-component.png){width="250" align="center"}

## 전제 조건

Forms 포털 구성 요소의 다양한 기능을 살펴보기 전에 환경에 대해 핵심 구성 요소가 활성화되었는지 확인하십시오. 사용자 환경에 대해 핵심 구성 요소를 활성화하는 방법에 대한 자세한 지침을 보려면 [여기를 클릭](/help/forms/enable-adaptive-forms-core-components.md)하십시오.

<!--
## Enable Forms Portal components for your existing environment

To enable out-of-the-box Forms Portal components on existing AEM Forms as a Cloud Service, perform the following steps:

1. **Clone Cloud Manager Git repository on your local development instance:**  Your Cloud Manager Git repository contains a default AEM project. It is based on [AEM Archetype](https://github.com/adobe/aem-project-archetype/). Clone your Cloud Manager Git Repository using Self-Service Git Account Management from Cloud Manager UI to bring the project on your local development environment. For details on accessing the repository, see [Accessing Repositories](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/managing-code/accessing-repos.html).  

1. **Create [!DNL Experience Manager Forms] as a [Cloud Service] project:** Create [!DNL Experience Manager Forms] as a [Cloud Service] project based on [AEM Archetype 50](https://github.com/adobe/aem-project-archetype/releases/tag/aem-project-archetype-50) or later. The archetype help developers easily start developing for [!DNL AEM Forms] as a Cloud Service. It also includes some sample themes and templates to help you started quickly.

    To create [!DNL Experience Manager Forms] as a Cloud Service project, open the command prompt and run the below command. To include [!DNL Forms] specific configurations, themes, and templates, set `includeForms=y`.  

    ```shell
    mvn -B archetype:generate -DarchetypeGroupId=com.adobe.aem -DarchetypeArtifactId=aem-project-archetype -DarchetypeVersion=30 -DaemVersion="cloud" -DappTitle="My Site" -DappId="mysite" -DgroupId="com.mysite" -DincludeForms="y"
    ```

    Also, change `appTitle`, `appId`, and `groupId`, in the above command to reflect your environment.

    After the project is ready, update the `<core.forms.components.version>x.y.z</core.forms.components.version>` property in the top-level `pom.xml` of the Archetype project to reflect the latest version of [core-forms-components](https://github.com/adobe/aem-core-forms-components) in your `AEM Archetype` project. 
 
1. **Deploy the project to your local development environment:** You can use the following command to deploy to your local development environment

    `mvn -PautoInstallPackage clean install`

    For the complete list of commands, see [Building and Installing](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/using.html?lang=en#building-and-installing)

1. [Deploy the archetype to your [!DNL AEM Forms] as a Cloud Service environment](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/aem-project-content-package-structure.html#embeddeds). -->

최신 핵심 구성 요소를 환경에 배포하면 작성 환경에서 Forms 포털 구성 요소에 액세스할 수 있습니다.

## 사이트 페이지의 목록 양식

Sites 페이지에 **Search &amp; List** 포털 구성 요소를 추가하려면 다음 단계를 수행하십시오.

1. **편집** 모드로 AEM Sites 페이지를 엽니다.
1. **[!UICONTROL 페이지 정보]** > **[!UICONTROL 템플릿 편집]**(으)로 이동
   ![템플릿 정책 편집](/help/forms/assets/save-form-as-draft-edit-template.png){width="250" align="center"}

1. **[!UICONTROL 정책]**&#x200B;을 클릭하고 **[AEM Archetype 프로젝트 이름] - Forms 및 통신 포털**&#x200B;에서 **[!UICONTROL 검색 및 목록 작성자]** 확인란을 선택하십시오.

   ![정책 선택](/help/forms/assets/search-lister-enable-policy.png){width="250" align="center"}

1. **[!UICONTROL 완료]**&#x200B;를 클릭합니다.
1. 이제 작성 모드에서 AEM Sites 페이지를 다시 엽니다.
1. 페이지 편집기 내에서 Forms 포털 구성 요소를 추가할 수 있는 섹션을 찾습니다.

1. **추가** 아이콘을 클릭합니다. 아이콘은 새 구성 요소를 추가하는 옵션을 나타내는 더하기 기호(+)입니다.

   **추가** 아이콘을 클릭하면 삽입할 다양한 구성 요소를 표시하는 **새 구성 요소 삽입** 대화 상자가 표시됩니다.

   >[!NOTE]
   >
   > 또는 구성 요소를 드래그 앤 드롭할 수도 있습니다.

1. 대화 상자에서 사용 가능한 구성 요소를 탐색하고 목록에서 원하는 구성 요소를 선택합니다. 예를 들어 목록에서 **검색 및 목록 작성기** 구성 요소를 선택하여 **검색 및 목록 작성기** Forms 포털 구성 요소를 추가합니다.

   ![검색 및 목록 작성자 구성 요소](/help/forms/assets/add-search-lister.png){width="250" align="center"}

이제 **검색 및 목록 작성기** 구성 요소의 속성을 구성하십시오.

## 검색 및 목록 작성자 구성 요소의 속성 이해

원활한 사용자 경험을 위해 구성 대화 상자를 사용하여 **검색 및 목록** 구성 요소 속성을 손쉽게 사용자 지정할 수 있습니다. 구성하려면 구성 요소를 선택한 다음 ![구성 아이콘](assets/configure_icon.png)을 선택합니다. **[!UICONTROL 검색 및 목록 작성기]** 대화 상자가 열립니다.

### 탭 표시

![탭 표시](/help/forms/assets/search-and-lister-display-tab.png){width="250" align="center"}

1. **[!UICONTROL 제목]**&#x200B;에서 검색 및 목록 구성 요소의 제목을 지정합니다. 직설적인 제목을 사용하면 사용자가 양식 목록에서 빠른 검색을 수행할 수 있습니다.
1. **[!UICONTROL 레이아웃]** 목록에서 카드 또는 목록 형식으로 양식을 나타내는 레이아웃을 선택하십시오.
1. 검색 및 정렬 기준 기능을 숨기려면 **[!UICONTROL 검색 숨기기]** 및 **[!UICONTROL 정렬 숨기기]**&#x200B;를 선택하십시오.
1. **[!UICONTROL 도구 설명]**&#x200B;에서 구성 요소를 마우스로 가리키면 표시되는 도구 설명을 제공합니다.

### 에셋 탭

![자산 탭](/help/forms/assets/search-and-lister-asset-tab.png){width="250" align="center"}

1. **[!UICONTROL 자산 폴더]** 탭에서 양식을 가져와서 페이지에 나열하는 위치를 지정합니다.
1. **[!UICONTROL 다른 위치 추가]**&#x200B;를 사용하여 여러 폴더 위치를 구성할 수 있습니다.

### 결과 탭

![탭 표시](/help/forms/assets/search-and-lister-result-tab.png){width="250" align="center"}

**[!UICONTROL 결과]** 탭에서 페이지당 표시할 최대 양식 수를 구성합니다. 기본값은 페이지당 8개의 양식입니다.

## Search &amp; List 구성 요소를 사용하여 Sites 페이지에서 양식 보기

양식 목록을 보려면 **검색 및 목록 작성기** Forms 포털 구성 요소를 사용하십시오. 화면에 표시된 **Assets** 폴더의 양식 목록을 보려면 AEM Sites 페이지를 미리 봅니다. 검색 창을 사용하여 특정 양식을 검색할 수도 있습니다.

![검색 및 목록 작성자 아이콘](assets/search-and-lister-component.png){width="250" align="center"}

<!--
## Configure Azure Storage for Adaptive Forms {#configure-azure-storage-adaptive-forms}

[[!DNL Experience Manager Forms] Data Integration](data-integration.md) provides [!DNL Azure] storage configuration to integrate forms with [!DNL Azure] storage services. The Form Data Model (FDM) can be used to create Adaptive Forms that interact with [!DNL Azure] server to enable business workflows.

### Create Azure Storage Configuration {#create-azure-storage-configuration}

Before executing these steps, ensure that you have an Azure storage account and an access key to authorize access to the [!DNL Azure] storage account.

1. Navigate to **[!UICONTROL Tools]** &gt; **[!UICONTROL Cloud Services]** &gt; **[!UICONTROL Azure Storage]**.
1. Select a folder to create the configuration and select **[!UICONTROL Create]**.
1. Specify a title for the configuration in the **[!UICONTROL Title]** field.
1. Specify the name of the [!DNL Azure] storage account in the **[!UICONTROL Azure Storage Account]** field.

### Configure Unified Storage Connector for Forms Portal {#configure-usc-forms-portal}

Perform the following steps to configure Unified Storage Connector for AEM Workflows:

1. Navigate to **[!UICONTROL Tools]** &gt; **[!UICONTROL Forms]** &gt; **[!UICONTROL Unified Storage Connector]**.
1. In the **[!UICONTROL Forms Portal]** section, select **[!UICONTROL Azure]** from the **[!UICONTROL Storage]** drop-down list.
1. Specify the [configuration path for the Azure storage configuration](#create-azure-storage-configuration) in the **[!UICONTROL Storage Configuration Path]** field.
1. Select **[!UICONTROL Publish]** and then select **[!UICONTROL Save]** to save the configuration.

## Enable Forms Portal Components {#enable-forms-portal-components}

To use any core component (including the out-of-the-box portal components) in an Adobe Experience Manager (AEM) site, you must create a proxy component and enable it for your site. For creating a proxy component and enabling portal components, see [Using Core Components](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/get-started/using.html?lang=en#create-proxy-components). 

Once a portal component is enabled, you can use it in the author instance of your sites page.

## Add and Configure Forms Portal Components {#configure-forms-portal-components}

You can create and customize Forms Portal on websites authored using AEM by adding and configuring the portal components. Ensure that the [components are enabled](#enable-forms-portal-components) before using them in the Forms Portal.

To add a component, either drag and drop the component from the Components pane to the layout container on the page, or select the add icon on the layout container and add the component from the [!UICONTROL Insert New Component] dialog.

### Configure Drafts & Submissions Component {#configure-drafts-submissions-component}

The Drafts & Submissions component displays forms that are saved as draft for completing later and submitted forms. To configure, select the component and then select the ![Configure icon](assets/configure_icon.png). In the [!UICONTROL Drafts and Submissions] dialog, specify the title to indicate the form listing as draft or submitted forms. Also select whether the component should list draft forms or submitted forms in card or list format.

![Drafts icon](assets/drafts-component.png)

![Submissions icon](assets/submission-listing.png)

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


## 다음 단계

다음 문서에서는 [양식을 초안으로 저장하고 초안 및 제출 Forms 포털 구성 요소를 사용하여 Sites 페이지에 나열하는 방법](/help/forms/save-core-component-based-form-as-draft.md)을 알아보겠습니다.

## 관련 문서

{{forms-portal-see-also}}

## 추가 참조 {#see-also}

{{see-also}}