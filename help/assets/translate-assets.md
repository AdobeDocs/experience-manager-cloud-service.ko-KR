---
title: 다양한 언어로 디지털 에셋 제작 및 관리
description: 이진, 메타데이터 및 태그를 여러 언어로 번역하는 워크플로우를 자동화하는 방법을 살펴볼 수 있습니다.
contentOwner: AG
translation-type: tm+mt
source-git-commit: f85dea62ba334fd5b3a7cc45fbf09556cbfdd2ec
workflow-type: tm+mt
source-wordcount: '2608'
ht-degree: 3%

---


# 다국어 자산 {#multilingual-assets}

다국어 자산은 이진, 메타데이터 및 태그를 여러 언어로 포함한 자산을 의미합니다. 일반적으로 에셋에 대한 바이너리, 메타데이터 및 태그는 한 언어로 되어 있으며, 이 언어는 다른 언어로 번역되어 다국어 프로젝트에서 사용할 수 있습니다. Adobe Experience Manager(AEM) 자산을 사용하면 자산(이진, 메타데이터 및 태그 포함)의 번역 워크플로우를 자동화하여 다국어 프로젝트에서 사용할 수 있도록 다른 언어로 자산을 생성할 수 있습니다.

번역 워크플로우를 자동화하려면 번역 서비스 제공업체를 AEM과 통합하고 에셋을 여러 언어로 번역하는 프로젝트를 제작해야 합니다. AEM은 인간 및 기계 번역 워크플로우를 지원합니다.

인간 번역:번역된 에셋이 반환되어 AEM으로 가져옵니다. 번역 공급자가 AEM과 통합되면 AEM과 번역 공급자 사이에 자산이 자동으로 전송됩니다.

기계 번역:기계 번역 서비스는 자산의 메타데이터와 태그를 즉시 변환합니다.

<!--
We have multiple articles around translation of assets. For now, dumping all content in this article to remove others and create only ONE UBER article.

https://docs.adobe.com/content/help/en/experience-manager-65/assets/managing/translation-projects.html
https://docs.adobe.com/content/help/en/experience-manager-65/assets/managing/preparing-assets-for-translation.html
[Apply translation cloud services to folders](https://docs.adobe.com/content/help/en/experience-manager-65/assets/managing/transition-cloud-services.html)

One of these articles is a copy of [Preparing Content for Translation](https://docs.adobe.com/content/help/en/experience-manager-65/administering/introduction/tc-prep.html

-->

<!-- 
Translating assets includes the following:

1. [Connecting AEM with the translation service provider](/help/sites-administering/tc-tic.md#connecting-to-a-translation-service-provider)
1. [Creating translation integration framework configurations](/help/sites-administering/tc-tic.md)
1. [Preparing assets for translation](prepare-assets-for-translation.md)
1. [Applying translation cloud services to folders](transition-cloud-services.md)
1. [Create translation projects](translation-projects.md)

If your translation service provider does not provide a connector to integrate with AEM, use an [alternative process](/help/sites-administering/tc-manage.md#exporting-a-translation-job).

Also see, [Creating translation projects for content fragments](creating-translation-projects-for-content-fragments.md).

-->

## 자산 번역 준비 {#prepare-assets-for-translation}

다국어 자산은 이진, 메타데이터 및 태그를 여러 언어로 포함한 자산을 의미합니다. 일반적으로 에셋에 대한 바이너리, 메타데이터 및 태그는 한 언어로 되어 있으며, 이 언어는 다른 언어로 번역되어 다국어 프로젝트에서 사용할 수 있습니다.

Adobe Experience Manager(AEM) 자산에서 다국어 자산은 폴더에 포함되며, 이 폴더에는 각 폴더에 다른 언어의 자산이 포함됩니다.

각 언어 폴더를 언어 복사라고 합니다. 언어 루트라고 하는 언어 사본의 루트 폴더는 언어 사본에 있는 컨텐츠의 언어를 식별합니다. 예를 들어 이탈리아어 사본에 대한 이탈리아어 루트 `/content/dam/it` 가 있습니다. 소스 에셋의 번역이 수행될 때 올바른 언어를 타깃팅하도록 언어 복사본은 [올바르게 구성된 언어 루트를](#create-a-language-root) 사용해야 합니다.

자산을 처음 추가하는 언어 사본은 기본 언어입니다. 기본 언어는 다른 언어로 번역되는 소스입니다. 샘플 폴더 계층 구조에는 여러 언어 루트가 포함되어 있습니다.

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

다음 단계를 수행하여 자산을 번역할 준비를 합니다.

1. 기본 언어의 언어 루트를 만듭니다. 예를 들어 샘플 폴더 계층 구조에 있는 영어 사본의 언어 루트는 입니다 `/content/dam/en`. 언어 루트 만들기의 정보에 따라 언어 루트 [가 올바르게 구성되었는지 확인합니다](#create-a-language-root).

1. 기본 언어로 에셋을 추가합니다.
1. 언어 사본이 필요한 각 대상 언어의 언어 루트를 만듭니다.

### 언어 루트 만들기 {#create-a-language-root}

언어 루트를 만들려면 폴더를 만들고 이름 속성 값으로 ISO 언어 코드를 사용합니다. 언어 루트를 만든 후 언어 루트 내의 모든 수준에서 언어 사본을 만들 수 있습니다.

예를 들어 샘플 계층의 이탈리아어 언어 사본의 루트 페이지는 이름 속성 `it` 으로 되어 있습니다. Name 속성은 저장소의 자산 노드의 이름으로 사용되므로 자산의 경로를 결정합니다. (*&lt;server>:&lt;port>/assets.html/content/dam/it/*)

1. 자산 콘솔에서 **[!UICONTROL 만들기를 클릭/탭하고]** 메뉴에서 **[!UICONTROL 폴더]** 를 선택합니다.
1. 이름 필드에 국가 코드를 의 형식으로 입력합니다 `<language-code>`.
1. **[!UICONTROL 만들기]**&#x200B;를 클릭하거나 탭합니다. 언어 루트는 자산 콘솔에서 만들어집니다.

### 언어 루트 보기 {#view-language-roots}

터치에 적합한 UI는 AEM Assets 내에서 작성된 언어 루트 목록을 표시하는 참조 패널을 제공합니다.

1. 자산 콘솔에서 언어 사본을 만들 기본 언어를 선택합니다.
1. GlobalNav 아이콘을 클릭하거나 탭하고 **[!UICONTROL 참조를]** 선택하여 참조 창을 엽니다.
1. 참조 창에서 언어 사본 **[!UICONTROL 을 클릭하거나 탭합니다]**. 언어 복사 패널에는 자산의 언어 사본이 표시됩니다.

### 새 번역 프로젝트 만들기 {#create-a-new-translation-project}

이 옵션을 사용하면 번역될 에셋이 번역하려는 언어의 언어 루트로 복사됩니다. 선택한 옵션에 따라 프로젝트 콘솔에서 자산에 대한 번역 프로젝트가 생성됩니다. 설정에 따라 번역 프로젝트를 수동으로 시작하거나 번역 프로젝트를 만드는 즉시 자동으로 실행할 수 있습니다.

1. 자산 UI에서 언어 사본을 만들 소스 폴더를 선택합니다.
1. 참조 **[!UICONTROL 창을]** 열고 사본 **[!UICONTROL 에서 언어 사본]** 을 클릭/ **[!UICONTROL 탭합니다]**.
1. 아래쪽에서 **[!UICONTROL 만들기 및 번역을]** 클릭/탭합니다.
1. [ **[!UICONTROL Target 언어]** ] 목록에서 폴더 구조를 만들 언어를 선택합니다.
1. 프로젝트 **[!UICONTROL 목록]** 에서 **[!UICONTROL 새 번역 프로젝트]**&#x200B;만들기를 선택합니다.
1. 프로젝트 **[!UICONTROL 제목]** 필드에 프로젝트 제목을 입력합니다.
1. 만들기를 클릭/ **[!UICONTROL 탭합니다]**. 소스 폴더의 에셋이 4단계에서 선택한 로케일의 대상 폴더로 복사됩니다.
1. 폴더로 이동하려면 언어 사본을 선택하고 자산에 **[!UICONTROL 표시를 클릭합니다]**.
1. 프로젝트 콘솔로 이동합니다. 번역 폴더가 프로젝트 콘솔로 복사됩니다.
1. 번역 프로젝트를 보려면 폴더를 엽니다.
1. 프로젝트를 클릭/탭하여 세부 사항 페이지를 엽니다.
1. 번역 작업의 상태를 보려면 **[!UICONTROL 번역 작업]** 타일 맨 아래에 있는 줄임표를 클릭합니다. <!-- For more details around job statuses, see [Monitoring the Status of a Translation Job](/help/sites-administering/tc-manage.md#monitoring-the-status-of-a-translation-job). -->
1. 자산 사용자 인터페이스에서 번역된 각 자산에 대한 속성 페이지를 열어 번역된 메타데이터를 봅니다.

>[!NOTE]
>
>이 기능은 자산과 폴더에 모두 사용할 수 있습니다. 폴더 대신 에셋을 선택하면 언어 루트까지 폴더의 전체 계층 구조가 복사되어 에셋의 언어 복사본을 만듭니다.

### Add to an existing translation project {#add-to-existing-translation-project}

이 옵션을 사용하면 이전 번역 워크플로우를 실행한 후 소스 폴더에 추가하는 자산에 대해 번역 워크플로우가 실행됩니다. 이전에 번역된 에셋이 포함된 대상 폴더에는 새로 추가된 에셋만 복사됩니다. 이 경우에는 새 번역 프로젝트가 생성되지 않습니다.

1. 자산 UI에서 번역되지 않은 자산이 포함된 소스 폴더로 이동합니다.
1. 번역할 자산을 선택하고 **[!UICONTROL 참조 창을 엽니다]**. 언어 **[!UICONTROL 복사]** 섹션에는 현재 사용 가능한 번역 사본의 수가 표시됩니다.
1. 사본 아래의 **[!UICONTROL 언어]** 사본을 클릭/ **[!UICONTROL 탭합니다]**. 사용 가능한 번역 사본 목록이 표시됩니다.
1. 아래쪽에서 **[!UICONTROL 만들기 및 번역을]** 클릭/탭합니다.
1. [ **[!UICONTROL Target 언어]** ] 목록에서 폴더 구조를 만들 언어를 선택합니다.
1. 프로젝트 **[!UICONTROL 목록]** 에서 **[!UICONTROL 기존 번역 프로젝트에]** 추가를 선택하여 폴더에서 번역 워크플로우를 실행합니다.
   >[!NOTE]
   >
   >기존 번역 프로젝트에 **[!UICONTROL 추가]** 옵션을 선택하는 경우 프로젝트 설정이 기존 프로젝트의 설정과 정확히 일치하는 경우에만 번역 프로젝트가 기존 프로젝트에 추가됩니다. 그렇지 않으면 새 프로젝트가 만들어집니다.
1. 기존 **[!UICONTROL 번역 프로젝트]** 목록에서 프로젝트를 선택하여 번역 자산을 추가합니다.
1. Click/tap **[!UICONTROL Create]**. 변환할 에셋이 대상 폴더에 추가됩니다. 업데이트된 폴더가 언어 사본 **[!UICONTROL 섹션 아래에]** 나열됩니다.
1. 프로젝트 콘솔로 이동하고 추가한 기존 번역 프로젝트를 엽니다.
1. 번역 프로젝트 보기에서 프로젝트 세부 사항 페이지를 클릭/탭합니다.
1. Click/tap the ellipsis at the bottom of the **Translation Job** tile to view the assets in the translation workflow. 번역 작업 목록에는 자산 메타데이터 및 태그에 대한 항목도 표시됩니다. 이 항목들은 자산의 메타데이터와 태그도 번역됨을 나타냅니다.

   >[!NOTE]
   >
   >* 태그나 메타데이터의 항목을 삭제하면 해당 에셋에 대해 태그나 메타데이터가 번역되지 않습니다.
   >* 기계 번역을 사용하는 경우 자산 바이너리가 번역되지 않습니다.
   >* 번역 작업에 추가한 자산에 하위 자산이 포함되어 있는 경우, 번역을 위해 하위 자산을 선택하고 제거한 다음 아무 문제 없이 계속 진행하십시오.


1. 자산에 대한 번역을 시작하려면 **[!UICONTROL 번역 작업]** 타일의 화살표를 클릭/탭하고 목록에서 **[!UICONTROL 시작을]** 선택합니다. 변환 작업 시작을 알리는 메시지가 표시됩니다.
1. 번역 작업의 상태를 보려면 **[!UICONTROL 번역 작업]** 타일 맨 아래에 있는 줄임표를 클릭/탭합니다. <!-- For more details, see [Monitoring the Status of a Translation Job](/help/sites-administering/tc-manage.md#monitoring-the-status-of-a-translation-job). -->
1. 번역이 완료되면 상태가 검토 준비됨으로 변경됩니다. 자산 UI로 이동하고 번역된 각 자산에 대한 속성 페이지를 열어 번역된 메타데이터를 봅니다.

### 언어 복사 업데이트 {#update-language-copies}

이 워크플로우를 실행하여 추가 자산 세트를 번역하고 특정 로케일의 언어 복사본에 포함시킬 수 있습니다. 이 경우 번역된 자산은 이미 이전에 번역된 자산이 들어 있는 대상 폴더에 추가됩니다. 선택 사항에 따라 번역 프로젝트가 만들어지거나 새 자산에 대해 기존 번역 프로젝트가 업데이트됩니다. 언어 사본 업데이트 워크플로우에는 다음 옵션이 포함됩니다.

* 새 번역 프로젝트 만들기
* 기존 번역 프로젝트에 추가

### 기존 번역 프로젝트에 추가 {#add-to-existing-translation-project-1}

이 옵션을 사용하면 기존 번역 프로젝트에 자산 세트가 추가되어 선택한 로케일에 대한 언어 사본을 업데이트합니다.

1. 자산 UI에서 자산 폴더를 추가한 소스 폴더를 선택합니다.
1. 참조 창 **[!UICONTROL 을]**&#x200B;열고 사본 **[!UICONTROL 에서]** 언어 사본 **[!UICONTROL 을 클릭/탭하여]** 언어 사본목록을 표시합니다.
1. 모든 언어 사본을 선택하는 언어 사본 **[!UICONTROL 앞에]**&#x200B;있는 확인란을 선택합니다. 번역할 로케일에 해당하는 언어 사본(사본)을 제외한 다른 사본의 선택을 취소합니다.
1. 하단에 있는 언어 사본 **[!UICONTROL 업데이트를]** 클릭/탭합니다.
1. 프로젝트 **[!UICONTROL 목록]** 에서 기존 번역 프로젝트에 **[!UICONTROL 추가를 선택합니다]**.
1. 기존 **[!UICONTROL 번역 프로젝트]** 목록에서 프로젝트를 선택하여 번역 자산을 추가합니다.
1. 시작을 클릭/ **[!UICONTROL 탭합니다]**.
1. 나머지 절차를 완료하려면 기존 번역 프로젝트에 [추가](#add-to-existing-translation-project) 9-14단계를 참조하십시오.

### 임시 언어 사본 만들기 {#creating-temporary-language-copies}

번역 워크플로우를 실행하여 원본 자산의 편집된 버전으로 언어 사본을 업데이트할 때 번역된 자산을 승인할 때까지 기존 언어 사본은 유지됩니다. AEM Assets은 새로 번역된 자산을 임시 위치에 저장하고 사용자가 자산을 명시적으로 승인한 후 기존 언어 사본을 업데이트합니다. 자산을 거부하면 언어 사본은 변경되지 않습니다.

1. 언어 복사본을 이미 만든 언어 사본 **[!UICONTROL 의]** 소스 루트 폴더를 클릭/탭한 다음 자산에 **[!UICONTROL 표시를 클릭/탭하여 AEM Assets의]** 폴더를 엽니다.
1. 자산 UI에서 이미 번역한 자산을 선택하고 도구 모음에서 **[!UICONTROL 편집]** 아이콘을 클릭/탭하여 편집 모드로 자산을 엽니다.
1. 자산을 편집한 다음 변경 내용을 저장합니다.
1. 기존 번역 프로젝트에 [추가](#add-to-existing-translation-project) 절차의 2-14단계를 수행하여 언어 사본을 업데이트합니다.
1. 번역 작업 타일 아래쪽에 있는 줄임표를 **[!UICONTROL 클릭/]** 탭합니다. 번역 작업 **** 페이지의 자산 목록에서 번역된 버전의 자산이 저장되는 임시 위치를 명확하게 볼 수 있습니다.
1. 제목 옆에 있는 확인란을 **[!UICONTROL 선택합니다]**.
1. 도구 모음에서 **[!UICONTROL 번역]** 수락을 클릭/탭한 다음 대화 상자에서 **[!UICONTROL 동의]** 를 클릭/탭하여 대상 폴더의 번역된 자산을 편집된 자산의 번역된 버전으로 덮어씁니다.

   >[!NOTE]
   >
   >번역 워크플로우가 대상 자산을 업데이트하도록 하려면 자산과 메타데이터를 모두 수락합니다.

   번역 **[!UICONTROL 거부를 클릭/탭하여 원래 번역된 에셋 버전을 대상 로케일 루트에]** 유지하고 편집된 버전을 거부합니다.

1. 자산 콘솔로 이동하고 번역된 각 자산에 대한 속성 페이지를 열어 번역된 메타데이터를 봅니다.

에셋을 위한 메타데이터를 효율적으로 번역하는 방법에 대한 팁은 메타데이터를 효율적으로 번역하는 [5단계를 참조하십시오](https://blogs.adobe.com/experiencedelivers/experience-management/translate_aemassets_metadata/).

## 번역 프로젝트 만들기 {#creating-translation-projects}

언어 사본을 만들려면 자산 UI의 참조 레일에서 사용할 수 있는 다음 언어 복사 워크플로우 중 하나를 트리거합니다.

**작성 및 번역**

이 워크플로우에서는 번역될 자산이 번역하려는 언어의 언어 루트로 복사됩니다. 또한 선택한 옵션에 따라 프로젝트 콘솔의 자산에 대한 번역 프로젝트가 생성됩니다. 설정에 따라 번역 프로젝트를 수동으로 시작하거나 번역 프로젝트를 만드는 즉시 자동으로 실행할 수 있습니다.

**언어 복사 업데이트**

이 워크플로우를 실행하여 추가 자산 그룹을 번역하고 특정 로케일의 언어 복사본에 포함시킬 수 있습니다. 이 경우 번역된 자산은 이미 이전에 번역된 자산이 들어 있는 대상 폴더에 추가됩니다.

>[!NOTE]
>
>자산 바이너리는 번역 서비스 공급자가 바이너리 변환을 지원하는 경우에만 변환됩니다.

>[!NOTE]
>
>PDF 파일 및 Adobe InDesign 파일과 같은 복잡한 자산에 대한 번역 워크플로우를 실행하는 경우, 해당 하위 자산이나 변환(있는 경우)이 번역용으로 제출되지 않습니다.

### 워크플로우 작성 및 번역 {#create-and-translate-workflow}

작성 및 번역 워크플로우를 사용하여 특정 언어의 언어 사본을 처음으로 생성할 수 있습니다. 워크플로우는 다음 옵션을 제공합니다.

* 구조만 생성
* 새 번역 프로젝트 만들기
* 기존 번역 프로젝트에 추가

### 구조만 생성 {#create-structure-only}

대상 언어 루트 내에 대상 폴더 계층 구조를 만들어 소스 언어 루트 내의 소스 폴더 계층 구조에 일치시키려면 **구조만** 만들기 옵션을 사용합니다. 이 경우 소스 에셋이 대상 폴더에 복사됩니다. 그러나 번역 프로젝트는 생성되지 않습니다.

1. 자산 UI에서 대상 언어 루트에서 구조를 만들 소스 폴더를 선택합니다.
1. 참조 **[!UICONTROL 창을]** 열고 사본 **[!UICONTROL 에서 언어 사본]** 을 클릭/ **[!UICONTROL 탭합니다]**.
1. 아래쪽에서 **[!UICONTROL 만들기 및 번역을]** 클릭/탭합니다.
1. [ **[!UICONTROL Target 언어]** ] 목록에서 폴더 구조를 만들 언어를 선택합니다.
1. 프로젝트 **[!UICONTROL 목록]** 에서 구조만 **[!UICONTROL 만들기를 선택합니다]**.
1. Click/tap **[!UICONTROL Create]**. 대상 언어의 새 구조는 언어 사본 아래에 **[!UICONTROL 나열되어 있습니다]**.
1. 목록에서 구조를 클릭/탭한 다음, 자산에 **[!UICONTROL 표시]** 를 클릭/탭하여 대상 언어 내의 폴더 구조로 이동합니다.

## 폴더에 번역 클라우드 서비스 적용 {#applying-translation-cloud-services-to-folders}

Adobe Experience Manager(AEM)을 사용하면 원하는 번역 제공업체에서 클라우드 기반의 번역 서비스를 이용할 수 있으므로 요구 사항에 따라 에셋을 변환할 수 있습니다.

번역 워크플로우 동안 활용할 수 있도록 번역 클라우드 서비스를 자산 폴더에 직접 적용할 수 있습니다.

### 번역 서비스 적용 {#applying-the-translation-services}

번역 클라우드 서비스를 자산 폴더에 직접 적용하면 번역 워크플로우를 만들거나 업데이트할 때 번역 서비스를 구성할 필요가 없습니다.

1. 자산 사용자 인터페이스에서 번역 서비스를 적용할 폴더를 선택합니다.
1. 도구 모음에서 **[!UICONTROL 속성]** 아이콘을 클릭/탭하여 **[!UICONTROL 폴더 속성]** 페이지를 표시합니다.

   ![chlimage_1-215](assets/chlimage_1-215.png)

1. Cloud Services **[!UICONTROL 탭으로]** 이동합니다.
1. Cloud Service 구성 목록에서 원하는 번역 공급자를 선택합니다. 예를 들어 Microsoft의 번역 서비스를 사용하려면 **[!UICONTROL Microsoft Translator를 선택합니다]**.

   ![chlimage_1-216](assets/chlimage_1-216.png)

1. 변환 공급자에 대한 커넥터를 선택합니다.

   ![chlimage_1-217](assets/chlimage_1-217.png)

1. 도구 모음에서 **[!UICONTROL 저장을]**&#x200B;클릭/탭한 다음 **[!UICONTROL 확인을]** 클릭하여 대화 상자를 닫습니다.번역 서비스가 폴더에 적용됩니다.

### 사용자 정의 번역 커넥터 적용 {#applying-custom-translation-connector}

번역 워크플로우에서 사용할 번역 서비스의 사용자 지정 커넥터를 적용하려는 경우 사용자 지정 커넥터를 적용하려면 먼저 패키지 관리자에서 커넥터를 설치합니다. 그런 다음 Cloud Services 콘솔에서 커넥터를 구성합니다. 커넥터를 구성한 후에는 변환 서비스 적용 [에 설명된 Cloud Services 탭의 커넥터 목록에서 사용할 수 있습니다](#applying-the-translation-services). 사용자 정의 커넥터를 적용하고 번역 워크플로우를 실행하면 번역 프로젝트의 **[!UICONTROL 번역 요약]** 타일에 헤드 **[!UICONTROL 제공자]** 및 **[!UICONTROL 메서드 아래에 커넥터 세부 정보가]**&#x200B;표시됩니다.

1. 패키지 관리자에서 커넥터를 설치합니다.
1. AEM 로고를 클릭/탭하고 **[!UICONTROL 도구 > 배포 > Cloud Services으로 이동합니다]**.
1. Cloud Services **[!UICONTROL 페이지에서]** 타사 서비스 **[!UICONTROL 아래에 설치한 커넥터를]** 찾습니다.

   ![chlimage_1-218](assets/chlimage_1-218.png)

1. 지금 구성 **[!UICONTROL 링크를 클릭/탭하여 구성]** 만들기 **** 대화 상자를 엽니다.

   ![chlimage_1-219](assets/chlimage_1-219.png)

1. 커넥터의 제목과 이름을 지정한 다음 만들기를 클릭/ **[!UICONTROL 탭합니다]**. 사용자 지정 커넥터는 번역 서비스 **[!UICONTROL 적용 단계 5에 설명된 Cloud Services]** 탭의 커넥터 [목록에서 사용할 수 있습니다](#applying-the-translation-services).
1. 사용자 지정 커넥터를 적용한 후 번역 프로젝트 만들기에 설명된 변환 워크플로우를 실행합니다. 프로젝트 콘솔에서 번역 프로젝트의 **[!UICONTROL 번역 요약]** 타일에 있는 커넥터의 세부 사항을 **[!UICONTROL 확인합니다]** .

   ![chlimage_1-220](assets/chlimage_1-220.png)
