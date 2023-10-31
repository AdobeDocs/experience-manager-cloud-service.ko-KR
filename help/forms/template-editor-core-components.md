---
title: 핵심 구성 요소를 기반으로 적응형 양식 템플릿을 만드는 방법
description: 템플릿 편집기를 사용하여 기본 구조 및 초기 콘텐츠를 정의하는 핵심 구성 요소를 기반으로 적응형 양식 템플릿을 만드십시오.
Keywords: create adaptive form template, create adaptive form template based on core components, Use template to create adpative form.
exl-id: c1c050d3-953e-4e56-a96b-d84f2ec05e5e
source-git-commit: f562d082520037fa1b15272c763d35e93dab137f
workflow-type: tm+mt
source-wordcount: '1991'
ht-degree: 1%

---

# 핵심 구성 요소를 기반으로 적응형 양식 템플릿 만들기 {#adaptive-form-templates}

양식을 작성할 때 편집기에서 양식 구조, 콘텐츠 및 작업을 정의하는 필드 및 구성 요소를 추가합니다. 에서 필드 및 구성 요소를 추가합니다 `guideRootPanel` 양식 컨테이너. 템플릿 편집기를 사용하면 작성자가 양식을 만드는 데 사용할 수 있는 기본 구조와 초기 콘텐츠가 포함된 템플릿을 만들 수 있습니다.

예를 들어 모든 양식 작성자가 등록 양식에 특정 텍스트 상자, 탐색 단추 및 제출 단추를 포함할 수 있습니다. 작성자가 다른 등록 양식과 일치하는 양식을 만드는 데 사용할 수 있는 구성 요소로 템플릿을 만들 수 있습니다. 작성자가 템플릿을 사용하여 적응형 양식을 만들면 새 양식은 템플릿에서 지정한 구조 및 구성 요소를 상속받습니다. 템플릿 편집기 를 사용하여 다음과 같은 작업을 수행할 수 있습니다.

* 구조 레이어에서 양식의 머리글 및 바닥글 구성 요소를 추가합니다.
* 양식에 대한 초기 콘텐츠를 제공합니다.
* 테마를 지정하고 작업을 제출합니다.

<!--
You can download and install [!DNL AEM Forms] reference content package from [Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html) portal to import reference themes and templates to your environment.
-->

## 전제 조건

**환경에 맞는 적응형 Forms 핵심 구성 요소 활성화**: 프로그램을 만들 때 환경에 대한 적응형 Forms 핵심 구성 요소가 이미 활성화되었습니다. 다음을 기반으로 하는 양식 as a Cloud Service 환경이 있는 경우 [AEM Archetype 39 이하](https://github.com/adobe/aem-project-archetype), [환경에 맞는 적응형 Forms 핵심 구성 요소 활성화](enable-adaptive-forms-core-components.md).

>[!NOTE]
>
> Archetype 45 기반 Forms as a Cloud Service 환경 배포 시 **적응형 Forms(핵심 구성 요소)** 템플릿 및 핵심 구성 요소 기반 테마가 환경에 추가됩니다.

## 템플릿 작업 {#working-with-templates}

도구 메뉴에서 다음 위치로 이동하여 템플릿 편집기에 액세스할 수 있습니다. **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL 도구]** > **[!UICONTROL 일반]** > **[!UICONTROL 템플릿]**. 여기에서 템플릿은 편집 가능한 템플릿을 사용할 수 있도록 설정된 폴더로 구성됩니다.

>[!NOTE]
>
> 핵심 구성 요소별 폴더에서 편집 가능한 핵심 구성 요소 기반 템플릿을 찾을 수 있습니다.

Experience Manager은 템플릿을 구성할 수 있는 전역 폴더를 제공합니다. 그러나 기본적으로 활성화되어 있지는 않습니다. 전역 폴더를 활성화하거나 템플릿용 폴더를 만들도록 관리자에게 요청할 수 있습니다. 폴더를 만드는 방법에 대한 자세한 내용은 [템플릿 폴더](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/sites/authoring/features/templates.html#editing-templates-template-authors).

## 템플릿 만들기 {#create-template}

폴더를 만든 후 폴더를 열고 다음 단계를 수행하여 템플릿을 만듭니다.

1. 누르기 **[!UICONTROL 만들기]** 을(를) 생성한 폴더 내에서 선택합니다.
1. 다음에서 **[!UICONTROL 템플릿 유형 선택]** 섹션, 선택 **[!UICONTROL 적응형 양식(핵심 구성 요소) 템플릿]** 및 탭 **[!UICONTROL 다음]**.

1. 다음에서 **[!UICONTROL 템플릿 세부 정보]** 섹션, 다음을 제공합니다. **템플릿 제목** 및 탭 **[!UICONTROL 만들기]**.
설명을 입력할 수도 있습니다.

1. 누르기 **[!UICONTROL 완료]** 콘솔로 돌아가거나 **[!UICONTROL 열기]** 를 클릭하여 편집기에서 템플릿을 엽니다.

## 템플릿 편집기 UI {#template-editor-ui}

편집할 템플릿을 열면 다음 AEM Editor 구성 요소를 볼 수 있습니다.

* **페이지 도구 모음**
다음 옵션을 포함합니다.

   * **사이드 패널 전환**: 사이드바를 표시하거나 숨길 수 있습니다.
   * **페이지 정보**: 게시/게시 취소 시간, 썸네일, 클라이언트측 라이브러리, 페이지 정책 및 페이지 디자인 클라이언트측 라이브러리와 같은 정보를 지정할 수 있습니다.
     <!-- * **Emulator**: Lets you simulate and customize the look for different devices.-->
   * **모드 선택기:** 모드를 변경할 수 있습니다. 다음을 선택할 수 있습니다. **[!UICONTROL 구조]** 모드, **[!UICONTROL 초기 컨텐츠]**, **[!UICONTROL 레이아웃 제어]** 모드. 구조 모드에서는 머리글과 바닥글을 추가하고 사용자 정의할 수 있습니다. 초기 컨텐츠 모드에서는 양식 컨텐츠를 사용자 정의할 수 있습니다.
   * **미리 보기:** 템플릿을 게시할 때 템플릿이 어떻게 표시되는지 미리 볼 수 있습니다. [레이어 선택기] 및 [미리 보기]를 사용하여 편집 모드와 미리 보기 모드를 전환할 수 있습니다.
* **사이드바:** 콘텐츠, 속성, 에셋 및 구성 요소 브라우저를 제공합니다.
* **구성 요소 도구 모음:** 구성 요소를 선택하면 구성 요소를 사용자 정의할 수 있는 도구 모음이 표시됩니다.
* **페이지**: 템플릿을 만들기 위해 콘텐츠를 추가하는 영역입니다.

<!-- See [Introduction to authoring Adaptive Forms](introduction-forms-authoring.md) to understand the Touch UI editor. -->

## 템플릿 편집 {#editing-a-template}

템플릿의 적절한 측면을 선택하고 편집하는 다양한 모드는 다음과 같습니다.

* [구조](#structure)
* [초기 콘텐츠](#initial-content)
* [레이아웃](#layout)

화면 오른쪽 상단의 미리 보기 옵션 옆에 있는 레이어 선택기를 사용할 수 있습니다.

### 구조 {#structure}

템플릿 편집기에서 구조 레이어를 선택하면 템플릿과 연결된 적응형 Forms을 만드는 동안 변경할 수 없는 콘텐츠를 미리 정의하는 데 도움이 됩니다.

<!-- you can see the layout containers above and below the Adaptive Form Container. Authors can use these layout containers for header and footer. -->


![구조 레이어의 레이아웃 컨테이너](/help/forms/assets/header-layer-selector-core-component.png)

<!--

**A. Layout container for Header component**
Drag-drop the Adaptive Form Header component in the layout container above the Adaptive Form Container. After you add the component, you can specify its properties that let you add a logo and provide its title.
**B. Adaptive Form Container component**
Drag-drop the Adaptive Form components in the Adaptive Form Container. You can specify the design and arrangement of fields and components in the template editor. After you add the components, you can specify its properties.
**C. Layout container for Footer component**
Similarly, when you drag-drop the footer component in the layout container below the Adaptive Form Container, you can provide the copyright information and company details. 
You can add, edit, or customize the header and footer. Drag-drop the Adaptive Form Header and Footer component to customize the template. Drag-drop the Adaptive Form components in the Adaptive Form Container. You can specify the design and arrangement of fields and components in the template editor. 


Header and footer are added in the Initial Content layer.
-->

#### 구조 레이어에서 구성 요소 잠금/잠금 해제 {#locking-unlocking-components-in-the-structure-layer}

구조 레이어를 선택한 상태로 템플릿을 편집할 때 템플릿의 머리글과 바닥글을 잠금 해제할 수 있습니다. 템플릿에서 구성 요소 잠금이 해제된 경우 양식 작성자는 템플릿을 사용하는 적응형 양식에서 구성 요소를 편집할 수 있습니다. 구성 요소를 잠그면 양식 작성자가 적응형 양식에서 편집할 수 없습니다. 잠금 옵션은 구성 요소 도구 모음에서 사용할 수 있습니다.

예를 들어 템플릿에 헤더 구성 요소를 추가합니다. 구성 요소를 선택하면 구성 요소 도구 모음에 잠금 옵션이 표시됩니다. 일반적으로 머리글에는 회사 이름과 로고가 포함되며 양식 작성자가 템플릿에서 로고와 머리글을 변경하지 마십시오. 헤더 구성 요소가 잠긴 템플릿을 사용하여 만든 적응형 양식에서는 양식 작성자가 로고와 회사 이름을 변경할 수 없습니다.

>[!NOTE]
>
>헤더 구성 요소에서 이미지 또는 로고를 개별적으로 잠그거나 잠금 해제하지 않는 것이 좋습니다. 헤더 구성 요소의 잠금을 해제할 수 있습니다.

### 초기 콘텐츠 {#initial-content}

초기 컨텐츠 옵션을 선택하면 템플릿의 적응형 양식 컨테이너가 편집을 위한 적응형 양식처럼 열립니다. 템플릿과 연결된 적응형 Forms을 만드는 동안 변경할 수 있는 사전 정의된 콘텐츠를 만들 수 있습니다. 적응형 양식 작성과 마찬가지로 테마 선택 및 작업 제출과 같은 초기 설정을 지정할 수 있습니다.

양식 작성자는 이 필드를 기반으로 양식을 만듭니다. 컨텐츠 흐름 구조는 템플릿의 초기 컨텐츠 레이어에 지정됩니다. 양식 템플릿의 초기 콘텐츠를 편집하는 것으로 전환하려면 페이지 도구 모음에서 미리 보기 전에 을 누릅니다 ![캔버스 드롭다운](assets/canvas-drop-down.png) **>** **[!UICONTROL 초기 컨텐츠]**.

![초기 컨텐츠 레이어에 머리글 및 바닥글 추가됨](assets/header-and-footer.png)

초기 컨텐츠 레이어에서 작성자가 기반으로 사용하는 적응형 양식 템플릿을 만듭니다. 템플릿 작성은 양식 작성과 유사하며, 사이드바에서 사용할 수 있는 옵션을 사용합니다. 사이드바는 콘텐츠, 속성, 에셋 및 구성 요소 브라우저를 제공합니다.

<!-- See [Sidebar](introduction-forms-authoring.md#sidebar). -->

>[!NOTE]
>
>[제출 액션]으로 [컨텐츠 저장] 또는 [PDF 저장]을 선택하면 [저장] 경로를 지정하는 옵션이 제공됩니다. 템플릿에 경로를 지정하면 해당 경로에서 생성된 모든 양식의 경로가 동일합니다. 올바른 저장소 경로를 지정하거나 양식 작성자가 모든 양식의 데이터가 동일한 위치에 저장되지 않도록 저장소 경로를 업데이트하도록 할 수 있습니다.

### 레이아웃 {#layout}

템플릿을 편집할 때 레이아웃을 정의할 수 있으며 표준 반응형 레이아웃을 사용합니다. 레이아웃은 장치 너비를 기반으로 구성 요소의 너비를 관리하여 반응형 적응형 양식 디자인을 용이하게 합니다.

![구조 레이어의 레이아웃 컨테이너](/help/forms/assets/layout-template-core-component.png)

이 문서 참조 [응답형 레이아웃 이해](https://experienceleague.adobe.com/docs/experience-manager-learn/sites/page-authoring/responsive-layout-feature-video-understand.html?lang=en) 추가 정보.

## 템플릿 활성화 {#enabling-the-template}

템플릿을 만들면 초안으로 추가됩니다. 적응형 Forms 생성에 사용할 수 있도록 템플릿을 활성화합니다. 템플릿을 활성화하려면 다음 작업을 수행하십시오.

1. 다음으로 이동 **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL 도구]** > **[!UICONTROL 템플릿]**을 클릭하고 템플릿을 만든 폴더를 엽니다.
생성한 템플릿이 초안으로 표시됩니다.
1. 템플릿을 선택하고 을 누릅니다 **[!UICONTROL 사용]** 을 클릭합니다.
적응형 양식을 만들 때 템플릿을 선택하라는 메시지가 표시되면 템플릿이 나열된 것을 볼 수 있습니다.

## 템플릿 가져오기 또는 내보내기 {#importing-or-exporting-a-template}

양식은 템플릿으로 작동합니다. 사용자 지정된 템플릿을 사용하여 만든 적응형 양식을 다운로드할 때 템플릿이 다운로드되지 않습니다. 다른 페이지에서 양식을 가져올 때 [!DNL AEM Forms] 예를 들어 템플릿 없이 가져옵니다. 양식을 가져왔지만 해당 템플릿을 사용할 수 없는 경우 양식이 렌더링되지 않습니다. 에서 사용자 지정 템플릿을 패키징할 수 있습니다. `/conf` 의 노드 `https://<server>:<port>/crx/packmgr`및 를 사용하여 [!DNL AEM Forms] 양식을 업로드할 인스턴스입니다. 다음을 수행할 수도 있습니다. [AEM Archetype을 사용하여 템플릿을 만들고 Cloud Service 인스턴스에 배포합니다](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-wknd-tutorial-develop/pages-templates.html#prerequisites).

>[!NOTE]
>
> * 다음을 구성할 수도 있습니다 [!UICONTROL 기록 문서] 적응형 양식 편집기 또는 적응형 양식 템플릿 편집기에서 바로 템플릿을 사용할 수 있습니다. 자세한 내용은 [적응형 Forms을 위한 기록 문서 생성](/help/forms/generate-document-of-record-for-non-xfa-based-adaptive-forms.md#document-of-record-support-in-adaptive-form-editor-dor-support-in-adaptiveform).

## 양식 데이터 모델 스키마를 템플릿에 연결 {#associating-form-data-model-schema-in-template}

작성자가 [!UICONTROL 양식 데이터 모델 스키마] 템플릿 편집기의 적응형 양식 템플릿을 참조하십시오. 이를 통해 작성자는 템플릿 편집기에서 스키마를 선택할 수 있습니다. 스키마를 템플릿에 연결하면 양식 작성자가 템플릿을 기반으로 양식을 만들 때 양식에 대해 스키마가 미리 선택됩니다. 양식 작성자가 스키마 사용을 규제하고 양식 작성자의 시간도 절약할 수 있습니다. 템플릿 편집기에서 양식 데이터 모델 스키마를 선택하려면 다음을 수행하십시오.

1. 누르기 **[!UICONTROL 컨텐츠 브라우저]** 왼쪽에 있습니다.
1. 양식 컨테이너로 이동 **[!UICONTROL 설정]**.
1. 선택 **[!UICONTROL 데이터 모델]**.
1. 다음을 통해 양식 데이터 모델 선택 **[!UICONTROL 양식 데이터 모델 선택]** 구성을 저장합니다.

![Form-Data-Model-Association-in-Forms](/help/forms/assets/select-form-data-model-img-core-component.png)

<!--

## Creating an Adaptive Form template with tabs and panels {#creating-an-adaptive-form-template-with-tabs-and-panels-nbs}

For example, you want to create a template with the following tabs:

* General Information
* Professional Information

You have added a logo, provided a title, and added a footer in the structure layer. Lock the header and footer to stop form authors from editing them when they use the template to create forms.

Change the layer from **Structure** to **Initial Content**, and start adding content to the form. To create a tabbed structure, add a child Panel in the guideRootPanel of the Adaptive Form container. To add a panel:

* You can add a panel by tapping the **[!UICONTROL +]** button when you select the **[!UICONTROL Drag components here]** option.

* You can drag-drop the panel component from the components browser in the sidebar.
* You can add child panel of the `guideRootPanel` from the component toolbar.

To create the General Information and Professional Information tabs, add two panels in the child panel of the `guideRootPanel`. Select the panels and tap ![cmppr](assets/configure-icon.svg) to open the properties in the sidebar. Change the element names as `general-info` and `professional-info`, and titles as General Information and Professional Information respectively. In the sidebar, tap content to open the content browser. In the Form Objects tab, select `guideRootPanel`. In the editor, the guideRootPanel is selected. Tap ![cmppr](assets/configure-icon.svg) in the component toolbar to open its properties. In the Panel Layout field, select **[!UICONTROL Tabs on Top]** and tap **[!UICONTROL Done]**. The tabbed template structure is applied.

### Adding content in tabs {#adding-content-in-tabs}

After you add panels and structure them as tabs, you can add fields inside the tabs. When you select a tab in the editor, you can see the **[!UICONTROL Drag components here]** option. You can drag-drop components such as text-boxes, list items, and buttons. You can drag-drop components from the components browser in the sidebar.

Each component has properties that enhance data capturing and manipulation. For example, you can enable the **[!UICONTROL Required field]** property of a component. Your authors can specify a message that your customers see when they skip filling a required field. Specify the message in **[!UICONTROL Required Field Message]** property.

In the example template, Name, Phone number, and Date of birth fields are added in the General Information tab. In the Professional Information tab, Currently employed, employment type, Educational qualification fields are added.

After you have added fields, you can add buttons such as Submit and Reset.
-->

### 템플릿 정책을 사용하여 적응형 양식 구성 요소에 사용자 지정 속성 추가

사용자 지정 속성을 사용하면 양식 템플릿을 사용하여 사용자 지정 속성(키-값 쌍)을 적응형 양식 핵심 구성 요소에 연결할 수 있습니다. 사용자 지정 속성이에 반영됩니다. **[!UICONTROL 속성]** 구성 요소의 헤드리스 렌디션 섹션에 자세히 설명되어 있습니다. 이를 통해 사용자 지정 속성 값에 따라 조정되는 동적 양식 비헤이비어를 만들 수 있습니다. 예를 들어 개발자는 모바일, 데스크탑 또는 웹 플랫폼용 Headless Forms 구성 요소의 다양한 표현물을 디자인할 수 있으므로 다양한 장치에서 사용자 경험을 크게 향상시킬 수 있습니다.

적응형 양식 핵심 구성 요소 필드에 사용자 지정 속성을 추가하는 단계는 다음과 같습니다.

1. [템플릿 편집기의 정책에 사용자 지정 그룹 이름 추가](#add-a-custom-group-name)
1. [적응형 양식 구성 요소의 편집 대화 상자에서 사용자 지정 그룹 이름을 선택합니다](#select-a-custom-group-name)

#### 템플릿 편집기의 정책에 사용자 지정 그룹 이름 추가 {#add-a-custom-group-name}

1. 다음으로 이동 **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL 도구]** > **[!UICONTROL 일반]** > **[!UICONTROL 템플릿]**.
1. 핵심 구성 요소를 기반으로 템플릿을 선택하고 편집 모드로 엽니다.
1. 다음을 클릭합니다. **[!UICONTROL 정책]** ![정책](/help/forms/assets/Smock_FeedManagement_18_N.svg) 사용자 지정 속성을 정의해야 하는 적응형 양식 핵심 구성 요소 필드의 아이콘. 다음 **[!UICONTROL 적응형 양식 필드]** 대화 상자가 나타납니다.
1. 다음 항목 선택 **[!UICONTROL 사용자 지정 속성]** 탭.
1. 다음을 지정합니다. **[!UICONTROL 정책 제목]** 다음 아래에 **[!UICONTROL 정책]** 섹션.
1. 다음을 지정합니다. **[!UICONTROL 그룹 이름]** 특정 그룹에 연결된 키-값 쌍을 추가합니다. 그룹 이름은 구성 요소의 편집 대화 상자에서 양식 작성자가 볼 수 있습니다. 그룹 이름을 선택하면 연관된 모든 키-값 쌍을 구성 요소에 적용할 수 있습니다.
1. **[완료]**&#x200B;를 클릭합니다.

![템플릿 편집기에서 사용자 지정 속성 그룹 이름 추가](/help/forms/assets/custom-properties-core-component.png)

템플릿 정책을 사용하여 하나 이상의 사용자 지정 속성 그룹을 추가할 때 **[!UICONTROL 고급]** 해당 핵심 구성 요소의 편집 대화 상자에 탭이 표시됩니다.

#### 핵심 구성 요소의 편집 대화 상자에서 사용자 지정 그룹 이름 선택 {#select-a-custom-group-name}

1. 편집 모드에서 적응형 양식을 엽니다.
1. 템플릿 편집기에서 사용자 지정 속성이 정의된 구성 요소를 탭하고 을 누릅니다 ![settings_icon](assets/configure-icon.svg) 구성 요소의 편집 대화 상자를 엽니다.
1. 다음 항목 선택 **[!UICONTROL 고급]** 탭.
1. 에서 사용자 정의 속성 그룹 이름 선택 **[!UICONTROL 사용자 지정 속성 선택]** 드롭다운. 정의된 모든 사용자 정의 그룹 이름은 드롭다운 목록에서 자동으로 채워집니다.
1. 누르기 **[!UICONTROL 완료]** 속성을 저장합니다.

![사용자 정의 속성 그룹 이름 선택](/help/forms/assets/select-custom-properties-group-name.png)

>[!NOTE]
>
> * 다음 **[!UICONTROL 추가 사용자 지정 속성]** 확인란을 선택하면 템플릿 정책에 제공된 속성 외에 구성 요소별 사용자 지정 속성을 동적으로 추가할 수 있습니다. 키 이름 값이 일치하면 특정 구성 요소의 사용자 지정 속성이 템플릿 정책에 설정된 사용자 지정 속성보다 우선합니다.

## 템플릿을 사용하여 적응형 양식 만들기 {#creating-an-adaptive-form-using-the-template}

템플릿을 만들고 활성화한 후 적응형 양식을 만들 때 Forms 관리자에서 사용할 수 있습니다. 템플릿을 사용하고 적응형 양식을 만들려면 다음을 참조하십시오. [핵심 구성 요소를 기반으로 적응형 양식 만들기](/help/forms/creating-adaptive-form-core-components.md).
<!--
## Change display option of out of the box templates  {#change-display-option-of-out-of-the-box-templates}

You can create custom templates for Adaptive Forms to define basic structure and initial content. [!DNL AEM Forms] also provides a set of out of the box template for Adaptive Forms. You can choose to show or hide the templates.

Perform the following steps to show and hide templates:

1. Log in to [!DNL AEM Forms] author instance and navigate to **[!UICONTROL Tools]** &gt; **[!UICONTROL Operations]** &gt; **[!UICONTROL Web Console]**.

   >[!NOTE]
   >
   >The URL of AEM web console is https://'[server]:[port]'/system/console/configMgr

1. Locate and open the **FormsManager Configuration** settings:

    * To show or hide out of the box Adaptive Forms template, check or uncheck the **Include Out of the box AF and AD Templates** option.
    * To show or hide out of the box Adaptive Form templates that were added in AEM 6.0 Forms or AEM 6.1 Forms releases but are now deprecated, check or uncheck the **Include AEM 6.0 AF Templates** option. If this option is checked, and you want it to take effect, it requires the **Include Out of the box AF and AD Templates** configuration to be enabled.

1. Click **Save**. The display options for the out of the box templates are changed. 

## Save an Adaptive Form as a template {#saving-adaptive-form-as-template}

You can also save an Adaptive Form as a template for future use. To save a Adaptive Form as a template:

1. Select an Adaptive Form to save it as a template.
1. Click **[!UICONTROL Save as Template]**. A dialog box appears.
1. Specify **[!UICONTROL Title]** (mandatory field), **[!UICONTROL Location]** (mandatory field) and **[!UICONTROL Description]** (optional field) for the template. 
1. Click **[!UICONTROL Create]**.

   ![Save as Form as Template](/help/forms/assets/saveformastemplate.png)



>[!NOTE]
>
>To use the same container policy as of the source Adaptive Form, it is recommended to save the template in the same folder as of the source Adaptive Form. In case, the template is saved in any other folder, than the created template uses a default container policy.
-->

## 모범 사례 {#best-practices}

* 적응형 양식 텍스트, 적응형 양식 컨테이너 등 핵심 구성 요소 기반의 구성 요소를 사용하여 템플릿을 만듭니다. 적응형 Forms 핵심 구성 요소에 대한 정보를 얻으려면 [여기를 클릭하십시오](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html).
* 웹 사이트에서 사용할 수 있는 근본적으로 다른 양식 유형과 일치하도록 템플릿 수 제한
* 템플릿에 사용된 사용자 지정 구성 요소에 필요한 유연성과 구성 기능을 제공합니다.

<!--
## See next

* [Create style or themes for your forms](using-themes-in-core-components.md)
* [Create an Adaptive Form (core components)](/help/forms/creating-adaptive-form-core-components.md)

-->

## 추가 참조 {#see-also}

{{see-also}}
* [양식에 맞는 스타일 또는 테마 만들기](using-themes-in-core-components.md)
* [적응형 양식 만들기(핵심 구성 요소)](/help/forms/creating-adaptive-form-core-components.md)

