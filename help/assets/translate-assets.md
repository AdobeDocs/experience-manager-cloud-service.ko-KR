---
title: AEM에서 자산을 번역하는 방법
description: 바이너리, 메타데이터 및 태그를 비롯한 AEM의 에셋을 여러 언어로 번역하기 위해 워크플로우를 자동화하는 방법에 대해 알아봅니다.
contentOwner: AG
feature: Asset Management,Translation
role: Admin,User
exl-id: 98df1412-a957-48a3-81c2-7dfe1d5e6d31
source-git-commit: 80ac947976bab2b0bfedb4ff9d5dd4634de6b4fc
workflow-type: tm+mt
source-wordcount: '2642'
ht-degree: 25%

---

# AEM에서 에셋 번역 {#multilingual-assets}

| 버전 | 문서 링크 |
| -------- | ---------------------------- |
| AEM 6.5 | [여기를 클릭하십시오.](https://experienceleague.adobe.com/docs/experience-manager-65/assets/using/multilingual-assets.html?lang=en) |
| AEM as a Cloud Service | 이 문서 |

다국어 에셋은 여러 언어로 된 바이너리, 메타데이터 및 태그가 있는 에셋을 의미합니다. 일반적으로 에셋의 바이너리, 메타데이터 및 태그는 한 언어로 된 후 다국어 프로젝트에서 사용할 수 있도록 다른 언어로 번역됩니다. Adobe Experience Manager Assets를 사용하면 워크플로우를 자동화하여 자산(바이너리, 메타데이터 및 태그 포함)을 번역하여 다국어 프로젝트에서 사용할 다른 언어의 자산을 생성할 수 있습니다.

AEM 에셋 번역을 자동화하려면 번역 서비스 공급업체를 Experience Manager과 통합하고 에셋을 여러 언어로 번역하기 위한 프로젝트를 제작해야 합니다. Experience Manager은 사람 번역 및 기계 번역 워크플로를 지원합니다.

AEM의 사람 에셋 번역: 번역된 에셋이 반환되고 Experience Manager으로 가져옵니다. 번역 공급업체를 Experience Manager과 통합하면 에셋이 Experience Manager과 번역 공급업체 간에 자동으로 전송됩니다.

AEM의 기계 자산 번역: 기계 번역 서비스는 자산의 메타데이터와 태그를 즉시 번역합니다.

<!--
We have multiple articles around translation of assets. For now, dumping all content in this article to remove others and create only ONE UBER article.

https://experienceleague.adobe.com/docs/experience-manager-65/assets/managing/translation-projects.html
https://experienceleague.adobe.com/docs/experience-manager-65/assets/managing/preparing-assets-for-translation.html
[Apply translation cloud services to folders](https://experienceleague.adobe.com/docs/experience-manager-65/assets/managing/transition-cloud-services.html)

One of these articles is a copy of [Preparing Content for Translation](https://experienceleague.adobe.com/docs/experience-manager-65/administering/introduction/tc-prep.html

-->

<!-- 
Translating assets includes the following:

1. [Connecting Experience Manager with the translation service provider](/help/sites-administering/tc-tic.md#connecting-to-a-translation-service-provider)
1. [Creating translation integration framework configurations](/help/sites-administering/tc-tic.md)
1. [Preparing assets for translation](prepare-assets-for-translation.md)
1. [Applying translation cloud services to folders](transition-cloud-services.md)
1. [Create translation projects](translation-projects.md)

If your translation service provider does not provide a connector to integrate with Experience Manager, use an [alternative process](/help/sites-administering/tc-manage.md#exporting-a-translation-job).

Also see, [Creating translation projects for content fragments](creating-translation-projects-for-content-fragments.md).

-->

## 자산 번역 준비 {#prepare-to-translate-assets}

다국어 에셋은 여러 언어로 된 바이너리, 메타데이터 및 태그가 있는 에셋을 의미합니다. 일반적으로 에셋의 바이너리, 메타데이터 및 태그는 한 언어로 된 후 다국어 프로젝트에서 사용할 수 있도록 다른 언어로 번역됩니다.

Adobe Experience Manager Assets에서 다국어 자산은 폴더에 포함되며, 여기서 각 폴더에는 다른 언어의 자산이 포함됩니다.

각 언어 폴더를 언어 사본이라고 합니다. 언어 루트라고도 하는 언어 사본의 루트 폴더는 언어 사본에 있는 콘텐츠의 언어를 식별합니다. 예를 들어, `/content/dam/it` 는 이탈리아어 사본의 이탈리아어 루트입니다. 언어 사본은 [올바르게 구성된 언어 루트](#create-a-language-root) 소스 에셋의 번역을 수행할 때 올바른 언어가 타깃팅되도록 합니다.

자산을 처음 추가하는 언어 사본은 언어 기본 사본입니다. 기본 언어는 다른 언어로 번역되는 소스입니다. 샘플 폴더 계층에는 여러 언어 루트가 포함됩니다.

```shell
/content
    /- dam
        |- en
        |- fr
        |- de
        |- es
        |- it
        |- ja
        |- zh
```

자산 번역을 준비하려면 다음 단계를 수행하십시오.

1. 기본 언어의 언어 루트를 만듭니다. 예를 들어 샘플 폴더 계층에서 영어 사본의 언어 루트는 입니다. `/content/dam/en`. 언어 루트가 의 정보에 따라 올바르게 구성되었는지 확인합니다. [언어 루트 만들기](#create-a-language-root).

1. 언어 기본 항목에 자산을 추가합니다.
1. 언어 사본이 필요한 각 대상 언어의 언어 루트를 만듭니다.

### 언어 루트 만들기 {#create-a-language-root}

언어 루트를 만들려면 폴더를 만들고 ISO 언어 코드를 이름 속성 값으로 사용합니다. 언어 루트를 만든 후에는 언어 루트 내의 모든 수준에서 언어 사본을 만들 수 있습니다.

예를 들어 샘플 계층의 이탈리아어 언어 사본의 루트 페이지에는 `it` 를 이름 속성으로 설정합니다. 이름 속성은 저장소의 자산 노드 이름으로 사용되므로 자산 경로를 결정합니다. (*&lt;server>:&lt;port>/assets.html/content/dam/it/*)

1. From the Assets console, click/tap **[!UICONTROL Create]** and choose **[!UICONTROL Folder]** from the menu.
1. 이름 필드에 다음 형식으로 국가 코드를 입력합니다. `<language-code>`.
1. **[!UICONTROL 만들기]**&#x200B;를 클릭하거나 탭합니다. 언어 루트는 자산 콘솔에서 만들어집니다.

### 언어 루트 보기 {#view-language-roots}

터치에 적합한 UI는 내에서 만들어진 언어 루트 목록을 표시하는 참조 패널을 제공합니다 [!DNL Assets].

1. 자산 콘솔에서 언어 사본을 만들 기본 언어를 선택합니다.
1. GlobalNav 아이콘을 클릭하거나 탭하고 **[!UICONTROL 참조]** 참조 창을 엽니다.
1. 참조 창에서 을 클릭하거나 탭합니다 **[!UICONTROL 언어 복사]**. 언어 사본 패널에 자산의 언어 사본이 표시됩니다.

### 새 번역 프로젝트 만들기 {#create-a-new-translation-project}

이 옵션을 사용하면 번역할 에셋이 번역하려는 언어의 언어 루트에 복사됩니다. 선택한 옵션에 따라 프로젝트 콘솔에서 에셋에 대한 번역 프로젝트가 만들어집니다. 설정에 따라 번역 프로젝트를 수동으로 시작하거나 번역 프로젝트를 만드는 즉시 자동으로 실행할 수 있습니다.

1. Assets UI에서 언어 사본을 만들 소스 폴더를 선택합니다.
1. Open the **[!UICONTROL References]** pane and click/tap **[!UICONTROL Language Copies]** under **[!UICONTROL Copies]**.
1. 클릭/탭 **[!UICONTROL 만들기 및 번역]** 맨 아래에
1. From the **[!UICONTROL Target Languages]** list, select the language(s) for which you want to create a folder structure.
1. 다음에서 **[!UICONTROL 프로젝트]** 목록, 선택 **[!UICONTROL 새 번역 프로젝트 만들기]**.
1. In the **[!UICONTROL Project Title]** field, enter a title for the project.
1. 클릭/탭 **[!UICONTROL 만들기]**. 소스 폴더의 에셋은 4단계에서 선택한 로케일에 대한 대상 폴더로 복사됩니다.
1. 폴더로 이동하려면 언어 사본을 선택하고 **[!UICONTROL 에셋에 표시]**.
1. 프로젝트 콘솔로 이동합니다. 번역 폴더가 프로젝트 콘솔에 복사됩니다.
1. 번역 프로젝트를 보려면 폴더를 엽니다.
1. 프로젝트를 클릭/탭하여 세부 정보 페이지를 엽니다.
1. 번역 작업의 상태를 보려면 아래쪽의 생략 부호를 클릭합니다 **[!UICONTROL 번역 작업]** 타일. <!-- For more details around job statuses, see [Monitoring the Status of a Translation Job](/help/sites-administering/tc-manage.md#monitoring-the-status-of-a-translation-job). -->
1. 에셋 사용자 인터페이스에서 번역된 각 에셋의 속성 페이지를 열어 번역된 메타데이터를 봅니다.

>[!NOTE]
>
>이 기능은 에셋과 폴더 모두에서 사용할 수 있습니다. 폴더 대신 에셋을 선택하면 언어 루트까지 폴더의 전체 계층 구조가 복사되어 에셋에 대한 언어 사본을 만듭니다.

### 기존 번역 프로젝트에 추가 {#add-to-existing-translation-project}

이 옵션을 사용하면 이전 번역 워크플로를 실행한 후 소스 폴더에 추가하는 에셋에 대해 번역 워크플로가 실행됩니다. 새로 추가된 에셋만 이전에 번역된 에셋이 포함된 대상 폴더에 복사됩니다. 이 경우 새로운 번역 프로젝트가 생성되지 않습니다.

1. 에셋 UI에서 번역되지 않은 에셋이 포함된 소스 폴더로 이동합니다.
1. Select an asset you want to translate, and open the **[!UICONTROL Reference pane]**. The **[!UICONTROL Language Copies]** section displays the number of translation copies that are currently available.
1. Click/tap **[!UICONTROL Language Copies]** under **[!UICONTROL Copies]**. A list of available translation copies is displayed.
1. 클릭/탭 **[!UICONTROL 만들기 및 번역]** 맨 아래에
1. From the **[!UICONTROL Target Languages]** list, select the language(s) for which you want to create a folder structure.
1. From the **[!UICONTROL Project]** list, select **[!UICONTROL Add to existing translation project]** to run the translation workflow on the folder.
   >[!NOTE]
   >
   >다음을 선택하면 **[!UICONTROL 기존 번역 프로젝트에 추가]** 옵션을 선택하면 프로젝트 설정이 기존 프로젝트의 설정과 정확히 일치하는 경우에만 번역 프로젝트가 기존 프로젝트에 추가됩니다. 그렇지 않으면 새 프로젝트가 만들어집니다.
1. 다음에서 **[!UICONTROL 기존 번역 프로젝트]** 목록에서 번역을 위해 에셋을 추가할 프로젝트를 선택합니다.
1. Click/tap **[!UICONTROL Create]**. The assets to be translated are added to the target folder. The updated folder is listed under the **[!UICONTROL Language Copies]** section.
1. 프로젝트 콘솔로 이동한 다음 추가한 기존 번역 프로젝트를 엽니다.
1. 번역 프로젝트 프로젝트 프로젝트 세부 정보 페이지 보기 를 클릭/탭합니다.
1. 아래 줄임표 클릭/탭 **번역 작업** 타일을 사용하여 번역 워크플로우에서 에셋을 볼 수 있습니다. 번역 작업 목록에는 에셋 메타데이터와 태그에 대한 항목도 표시됩니다. 이 항목들은 에셋의 메타데이터와 태그도 번역됨을 나타냅니다.

   >[!NOTE]
   >
   >* 태그나 메타데이터에 대한 항목을 삭제하면 어떤 에셋에 대해서도 태그나 메타데이터가 번역되지 않습니다.
   >* 기계 번역을 사용하는 경우 에셋 바이너리는 번역되지 않습니다.
   >* 번역 작업에 추가하는 에셋에 하위 에셋이 포함된 경우, 하위 에셋을 선택하고 이를 제거하여 결함 없이 번역을 진행합니다.


1. 에셋에 대한 번역을 시작하려면 의 화살표를 클릭/탭합니다. **[!UICONTROL 번역 작업]** 타일 및 선택 **[!UICONTROL 시작]** 목록에서 삭제할 수 있습니다. 번역 작업이 시작되었음을 알리는 메시지가 표시됩니다.
1. 번역 작업의 상태를 보려면 아래 줄임표를 클릭/탭합니다. **[!UICONTROL 번역 작업]** 타일. <!-- For more details, see [Monitoring the Status of a Translation Job](/help/sites-administering/tc-manage.md#monitoring-the-status-of-a-translation-job). -->
1. 번역이 완료되면 상태가 검토 준비됨으로 변경됩니다. 에셋 UI로 이동하고 번역된 각 에셋에 대한 속성 페이지를 열어 번역된 메타데이터를 봅니다.

### 언어 사본 업데이트 {#update-language-copies}

이 워크플로우를 실행하여 추가 자산 세트를 번역하고 특정 로케일의 언어 사본에 포함합니다. 이 경우 번역된 에셋은 이전에 번역된 에셋이 이미 포함된 대상 폴더에 추가됩니다. 옵션 선택에 따라 번역 프로젝트가 생성되거나 기존 번역 프로젝트가 새 에셋에 대해 업데이트됩니다. 언어 사본 업데이트 워크플로에는 다음 옵션이 포함됩니다.

* 새 번역 프로젝트 만들기
* 기존 번역 프로젝트에 추가

### 기존 번역 프로젝트에 추가 {#add-to-existing-translation-project-1}

이 옵션을 사용하면 선택한 로케일에 대한 언어 사본을 업데이트하기 위해 에셋 세트가 기존 번역 프로젝트에 추가됩니다.

1. 에셋 UI에서 에셋 폴더를 추가한 소스 폴더를 선택합니다.
1. Open the **[!UICONTROL References pane]**, and click/tap **[!UICONTROL Language Copies]** under **[!UICONTROL Copies]** to display the list of language copies.
1. Select the check box before **[!UICONTROL Language Copies]**, which selects all language copies. Unselect other copies except the language copy (copies) corresponding to the locale(s) to which you want to translate.
1. 클릭/탭 **[!UICONTROL 언어 사본 업데이트]** 맨 아래에
1. 다음에서 **[!UICONTROL 프로젝트]** 목록, 선택 **[!UICONTROL 기존 번역 프로젝트에 추가]**.
1. 다음에서 **[!UICONTROL 기존 번역 프로젝트]** 목록에서 번역을 위해 에셋을 추가할 프로젝트를 선택합니다.
1. Click/tap **[!UICONTROL Start]**.
1. 의 9~14단계 참조 [기존 번역 프로젝트에 추가](#add-to-existing-translation-project) 나머지 절차를 완료합니다.

### 임시 언어 사본 만들기 {#creating-temporary-language-copies}

번역 워크플로우를 실행하여 언어 사본을 원본 에셋의 편집된 버전으로 업데이트하면 번역된 에셋을 승인할 때까지 기존 언어 사본이 유지됩니다. [!DNL Assets] 새로 번역된 에셋을 임시 위치에 저장하고 에셋을 명시적으로 승인한 후 기존 언어 사본을 업데이트합니다. 에셋을 거부하면 언어 사본은 변경되지 않은 상태로 유지됩니다.

1. Click/tap the source root folder under **[!UICONTROL Language Copies]** for which you already created a language copy, and then click/tap **[!UICONTROL Reveal in Assets]** to open the folder in [!DNL Assets].
1. 에셋 UI에서 이미 번역한 에셋을 선택하고 **[!UICONTROL 편집]** 아이콘을 클릭하여 자산을 편집 모드로 엽니다.
1. 에셋을 편집한 다음 변경 사항을 저장합니다.
1. 의 2-14단계를 수행합니다. [기존 번역 프로젝트에 추가](#add-to-existing-translation-project) 언어 사본을 업데이트하는 절차.
1. 아래 줄임표 클릭/탭 **[!UICONTROL 번역 작업]** 타일. 의 자산 목록에서 **[!UICONTROL 번역 작업]** 페이지에서 자산의 번역본이 저장된 임시 위치를 명확하게 볼 수 있습니다.
1. 옆에 있는 확인란을 선택합니다. **[!UICONTROL 제목]**.
1. From the toolbar, click/tap **[!UICONTROL Accept Translation]** and then click/tap **[!UICONTROL Accept]** in the dialog to overwrite the translated asset in the target folder with the translated version of the edited asset.

   >[!NOTE]
   >
   >번역 워크플로를 활성화하여 대상 에셋을 업데이트하려면 에셋과 메타데이터 모두를 수락하십시오.

   클릭/탭 **[!UICONTROL 번역 거부]** 대상 로케일 루트에 있는 에셋의 원래 번역 버전을 유지하고 편집된 버전을 거부합니다.

1. 에셋 콘솔로 이동하고 번역된 각 에셋에 대한 속성 페이지를 열어 번역된 메타데이터를 봅니다.

<!-- TBD: Possibly this blog wasn't migrated. Still try to find from the author. Old one is archived at https://web.archive.org/web/20180423042713/https://blogs.adobe.com/experiencedelivers/experience-management/translate_aemassets_metadata/

For tips on translating metadata for assets efficiently, see [5 Steps to efficiently translate metadata](https://blogs.adobe.com/experiencedelivers/experience-management/translate_aemassets_metadata/). 
-->

## 번역 프로젝트 만들기 {#creating-translation-projects}

언어 사본을 만들려면 자산 UI의 참조 레일에서 사용할 수 있는 다음 언어 사본 워크플로 중 하나를 트리거합니다.

**만들기 및 번역**

이 워크플로에서는 번역할 에셋이 번역하려는 언어의 언어 루트에 복사됩니다. 또한 선택한 옵션에 따라 프로젝트 콘솔에서 에셋에 대한 번역 프로젝트가 만들어집니다. 설정에 따라 번역 프로젝트를 수동으로 시작하거나 번역 프로젝트를 만드는 즉시 자동으로 실행되도록 할 수 있습니다.

**언어 사본 업데이트**

이 워크플로우를 실행하여 추가 자산 그룹을 번역하고 특정 로케일의 언어 사본에 포함합니다. 이 경우 번역된 에셋은 이전에 번역된 에셋이 이미 포함된 대상 폴더에 추가됩니다.

>[!NOTE]
>
>자산 바이너리는 번역 서비스 공급자가 바이너리 번역을 지원하는 경우에만 번역됩니다.

>[!NOTE]
>
>PDF 파일 및 Adobe InDesign 파일과 같은 복잡한 에셋에 대한 번역 워크플로를 시작하는 경우, 해당 하위 에셋 또는 렌디션(있는 경우)이 번역을 위해 제출되지 않습니다.

### 워크플로우 만들기 및 번역 {#create-and-translate-workflow}

만들기 및 번역 워크플로우를 사용하여 처음으로 특정 언어에 대한 언어 사본을 생성합니다. 워크플로는 다음과 같은 옵션을 제공합니다.

* 구조만 생성
* 새 번역 프로젝트 만들기
* 기존 번역 프로젝트에 추가

### 구조만 생성 {#create-structure-only}

Use the **Create structure only** option to create a target folder hierarchy within the target language root to match the hierarchy of the source folder within the source language root. In this case, source assets are copied to the destination folder. However, no translation project is generated.

1. Assets UI에서 타겟 언어 루트에 구조를 만들 소스 폴더를 선택합니다.
1. Open the **[!UICONTROL References]** pane and click/tap **[!UICONTROL Language Copies]** under **[!UICONTROL Copies]**.
1. 클릭/탭 **[!UICONTROL 만들기 및 번역]** 맨 아래에
1. 다음에서 **[!UICONTROL Target 언어]** 목록에서 폴더 구조를 만들 언어를 선택합니다.
1. From the **[!UICONTROL Project]** list, choose **[!UICONTROL Create structure only]**.
1. Click/tap **[!UICONTROL Create]**. 대상 언어의 새 구조는 아래에 나열됩니다. **[!UICONTROL 언어 복사]**.
1. 목록에서 구조를 클릭/탭한 다음 클릭/탭합니다. **[!UICONTROL 에셋에 표시]** 대상 언어 내에서 폴더 구조로 이동합니다.

## 폴더에 번역 클라우드 서비스 적용 {#applying-translation-cloud-services-to-folders}

Adobe Experience Manager을 사용하면 원하는 번역 공급업체에서 클라우드 기반 번역 서비스를 이용하여 에셋을 사용자의 요구 사항에 따라 번역할 수 있습니다.

번역 클라우드 서비스를 에셋 폴더에 직접 적용하여 번역 워크플로 중에 활용할 수 있습니다.

### 번역 서비스 적용 {#applying-the-translation-services}

번역 클라우드 서비스를 자산 폴더에 직접 적용하면 번역 워크플로를 만들거나 업데이트할 때 번역 서비스를 구성할 필요가 없습니다.

1. Assets 사용자 인터페이스에서 번역 서비스를 적용할 폴더를 선택합니다.
1. From the toolbar, click/tap the **[!UICONTROL Properties]** icon to display the **[!UICONTROL Folder Properties]** page.

   ![chlimage_1-215](assets/chlimage_1-215.png)

1. Navigate to the **[!UICONTROL Cloud Services]** tab.
1. Cloud Service 구성 목록에서 원하는 번역 공급업체를 선택합니다. 예를 들어 Microsoft에서 번역 서비스를 이용하려면 다음을 선택합니다 **[!UICONTROL Microsoft 번역기]**.

   ![chlimage_1-216](assets/chlimage_1-216.png)

1. 번역 공급업체에 대한 커넥터를 선택합니다.

   ![chlimage_1-217](assets/chlimage_1-217.png)

1. From the toolbar, click/tap **[!UICONTROL Save]**, and then click **[!UICONTROL OK]** to close the dialog.The translation service is applied to the folder.

### 사용자 지정 번역 커넥터 적용 {#applying-custom-translation-connector}

If you want to apply a custom connector for the translation services you want to use in translation workflows. 사용자 지정 커넥터를 적용하려면 먼저 다음에서 커넥터를 설치합니다. [패키지 관리자.](/help/implementing/developing/tools/package-manager.md) Then, configure the connector from the Cloud Services console. After you configure the connector, it is available in the list of connectors in the Cloud Services tab described in [Applying the translation services](#applying-the-translation-services). After you apply the custom connector and run translation workflows, the **[!UICONTROL Translation Summary]** tile of the translation project displays the connector details under the heads **[!UICONTROL Provider]** and **[!UICONTROL Method]**.

1. 에서 커넥터 설치 [패키지 관리자.](/help/implementing/developing/tools/package-manager.md)
1. Experience Manager 로고를 클릭/탭하고 다음 위치로 이동 **[!UICONTROL 도구 > 배포 > Cloud Services]**.
1. Locate the connector you installed under **[!UICONTROL Third Party Services]** in the **[!UICONTROL Cloud Services]** page.

   ![chlimage_1-218](assets/chlimage_1-218.png)

1. 클릭/탭 **[!UICONTROL 지금 구성]** 를 여는 링크 **[!UICONTROL 구성 만들기]** 대화 상자.

   ![chlimage_1-219](assets/chlimage_1-219.png)

1. Specify a title and a name for the connector, and then click/tap **[!UICONTROL Create]**. The custom connector is available in the list of connectors in the **[!UICONTROL Cloud Services]** tab described in step 5 of [Applying the translation services](#applying-the-translation-services).
1. Run any translation workflow described in creating translation projects after you apply the custom connector. Verify the details of the connector in the **[!UICONTROL Translation Summary]** tile of the translation project in the **[!UICONTROL Projects]** console.

   ![chlimage_1-220](assets/chlimage_1-220.png)

**추가 참조**

* [Assets HTTP API](mac-api-assets.md)
* [에셋이 지원되는 파일 형식](file-format-support.md)
* [에셋 검색](search-assets.md)
* [연결된 에셋](use-assets-across-connected-assets-instances.md)
* [에셋 보고서](asset-reports.md)
* [메타데이터 스키마](metadata-schemas.md)
* [에셋 다운로드](download-assets-from-aem.md)
* [메타데이터 관리](manage-metadata.md)
* [검색 패싯](search-facets.md)
* [컬렉션 관리](manage-collections.md)
* [일괄 메타데이터 가져오기](metadata-import-export.md)
