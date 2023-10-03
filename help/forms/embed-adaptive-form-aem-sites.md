---
title: AEM Sites 페이지에 적응형 양식을 추가하는 방법
description: 적응형 Forms을 AEM Sites 페이지 또는 AEM 외부에서 호스팅되는 웹 페이지에 원활하게 임베드합니다.
feature: Adaptive Forms
Keywords: Forms AEM Sites, Embed Form to a Sites page, Adaptive Forms AEM Sites, Embed Adaptive Forms to AEM Page, Embed Forms in an AEM Sites page
exl-id: 359b05e8-d8c1-4a77-9e70-6f6b6e668560
source-git-commit: 7e3eb3426002408a90e08bee9c2a8b7a7bfebb61
workflow-type: tm+mt
source-wordcount: '3165'
ht-degree: 6%

---

# AEM 사이트 페이지에 적응형 양식 포함 {#embed-an-adaptive-form-to-aem-sites-page}

| 버전 | 문서 링크 |
| -------- | ---------------------------- |
| AEM 6.5 | [여기 클릭](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-basic-authoring/embed-adaptive-form-aem-sites.html) |
| AEM as a Cloud Service | 이 문서 |


## 개요 {#overview}

AEM Forms을 사용하면 양식 개발자가 적응형 Forms을 AEM Sites 페이지나 AEM 외부에 호스팅된 웹 페이지에 원활하게 포함할 수 있습니다. 임베드된 적응형 양식은 완전히 기능할 수 있으며, 사용자는 페이지를 종료하지 않고도 양식을 작성하고 제출할 수 있습니다. 사용자가 웹 페이지의 다른 요소 컨텍스트에 남아 있으면서 양식과 동시에 상호 작용하는 데 도움이 됩니다. 이렇게 하면 사용자가 진행 중인 페이지를 벗어나지 않고도 편리하게 양식을 작성하여 제출할 수 있습니다. 이 통합은 이미 만들어진 적응형 Forms을 재사용하는 편리한 방법을 제공합니다.

AEM 페이지 편집기 를 사용하여 여러 양식을 AEM Sites 페이지에 빠르게 포함할 수 있습니다. 콘텐츠 작성자는 AEM 페이지 편집기를 사용하여 동적 동작, 유효성 검사, 데이터 통합, 기록 문서 생성 및 비즈니스 프로세스 자동화 등 적응형 Forms 구성 요소의 기능을 사용하여 Sites 페이지 내에서 매끄러운 데이터 캡처 경험을 만들 수 있습니다. 또한 버전 관리, 타겟팅, 번역 및 다중 사이트 관리자와 같은 AEM Sites 페이지의 다양한 기능을 사용할 수 있습니다.

AEM Forms 제공 **[!UICONTROL 적응형 양식 컨테이너]** 및 **[!UICONTROL 적응형 Forms - 포함(v2)]** 구성 요소. 다음을 사용할 수 있습니다. **[!UICONTROL 적응형 Forms - 포함(v2)]** 적응형 Forms 편집기 를 사용하여 기존 적응형 양식을 추가하거나 양식을 만들 수 있는 구성 요소 **[!UICONTROL 적응형 양식 컨테이너]** 경험 조각 또는 AEM Sites 페이지 내에서 새 양식을 만들 수 있습니다.

![AEM Sites 페이지의 적응형 양식의 예](/help/forms/assets/adaptive-form-in-sites-page.png)

<!-- For information about embedding an Adaptive Form in an external web page, see [Embed Adaptive Form in external web page](/help/forms/using/embed-adaptive-form-external-web-page.md). 

## Why embed an Adaptive Form in AEM Sites page or AEM Experience Fragment? 

Using **[!UICONTROL Adaptive Forms – Embed(v2)]** in AEM Page Editor lets you create seamless data capture experiences within a Sites page using the power of Adaptive Forms components including dynamic behavior, validations, data integration, generate document of record and business process automation. It also lets you use various features of AEM Sites pages like, versioning, targeting, translation, and multi-site manager, enhancing the overall form creation and management experience. Let's explore some of these features:

* **Versioning:** AEM Sites pages offer [robust versioning capabilities](/help/sites-cloud/authoring/features/page-versions.md), allowing you to track and manage different versions of your forms. This enables you to make changes and enhancements to forms while maintaining the ability to roll back to previous versions if needed. Versioning ensures a controlled and organized approach to form development and evolution.
* **Targeting (Integration with Adobe Target):** With AEM Sites pages targeting capabilities, you can also [personalize the form experience for different audiences](/help/sites-cloud/integrating/integration-adobe-target-ims.md). By leveraging user segments and targeting criteria, you can tailor the form's content, design, or behavior to specific groups of users. This enables you to provide a personalized and relevant form experience, increasing engagement and conversion rates.
* **Translation:** AEM Sites [seamless integration with translation services](/help/sites-cloud/administering/translation/overview.md), allowing you to translate forms into multiple languages easily. This feature simplifies the localization process, ensuring that your forms are accessible to a global audience. You can manage translations efficiently within AEM translation projects, reducing time and effort required for multilingual form support. See considerations section for more information on translation.  
* **Multi-site Management and Live Copy:** AEM Sites provide robust [Multi-site Management and Live Copy capabilities](/help/sites-cloud/administering/msm/overview.md), enabling you to create and manage multiple websites within a single environment. This feature now lets you reuse forms across different sites, ensuring consistency and reducing duplication efforts. With centralized control and management, you can efficiently maintain and update forms across multiple websites.
* **Themes:** AEM Sites pages provide a framework for designing and maintaining consistent visual styles across multiple web pages. These define colors, fonts, style sheets, and other visual elements that contribute to the overall look and feel of the website. [You can use the themes designed for an AEM Sites page for an Adaptive Form, saving time and effort](/help/sites-cloud/administering/site-creation/site-themes.md#using-site-themes-using-themes). 
* **Tagging:** AEM Sites pages allow you to [assign tags or labels to a page, an asset, or other content](/help/implementing/developing/introduction/tagging-framework.md). Tags are keywords or metadata labels that provide a way to categorize and organize content based on specific criteria. You can assign one or more tags to pages, assets, or any other content items within AEM to improve search and categorize the assets. 
* **Locking and Unlocking content:** AEM Sites allow users to [control access and modifications to pages](/help/sites-cloud/authoring/fundamentals/editing-content.md) within the AEM Sites environment. When a page is locked, it means that it is protected from unauthorized changes or edits by other users. Only the user who has locked the content or a designated administrator can unlock it to allow modifications. 

In addition, Adaptive Forms in AEM Page Editor use [Adaptive Forms Core Components](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html?lang=en#features). These Core Components provide a standard and easier methods to style and customize the components, identical to [AEM Sites WCM Components](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=en).

-->

## AEM Sites 페이지 또는 AEM 경험 조각에서 적응형 양식을 만들거나 임베드하는 방법 {#various-options-to-create-or-embed-an-adaptive-form-in-aem-sites-page-or-aem-experience-fragment}

다음 옵션을 사용하여 이 기능을 최대한 활용할 수 있습니다.

* **[승인된 템플릿을 사용하여 적응형 양식을 만들고 AEM Sites 페이지에 임베드합니다](#embed-form-using-adaptive-form-wizzard-aem-sites):** 사전 승인된 템플릿을 활용하여 조직의 브랜딩 지침 및 디자인 표준에 맞는 적응형 Forms을 신속하게 만들고 포함할 수 있습니다.

* **[AEM Sites 페이지에 기존 양식 포함](#embed-an-adaptive-form-in-sites-editor):** 이미 만든 양식을 웹 사이트에 쉽게 통합하여 방문자가 직접 상호 작용할 수 있도록 할 수 있습니다.

* **[임베드된 적응형 양식을 경험 조각으로 변환](#convert-an-adaptive-form-in-sites-page-to-an-experience-fragment):** AEM Sites 페이지에 추가된 임베드된 적응형 양식을 여러 AEM Sites 페이지에서 양식을 재사용하기 위한 경험 조각으로 변환합니다.

* **[사용자 지정 적응형 양식을 만들어 AEM Sites 페이지에 추가](/help/forms/create-or-add-an-adaptive-form-to-aem-sites-page.md#create-an-adaptive-form-in-sites-editor-or-experience-fragment):** 다음을 사용할 수 있습니다. **[!UICONTROL 적응형 양식 컨테이너]** 요구 사항 및 디자인 환경 설정에 맞게 맞춤화하여 처음부터 새로운 양식을 작성할 구성 요소.

* **[사용자 정의 적응형 양식을 만들어 경험 조각에 추가](/help/forms/create-or-add-an-adaptive-form-to-aem-sites-page.md#create-an-adaptive-form-in-sites-editor):** AEM Experience Fragments에 양식을 추가하여 도달 범위를 확장함으로써 여러 페이지 또는 사이트에서 원활하게 재사용할 수 있습니다.

* **AEM Sites 페이지 또는 경험 조각에 여러 양식 추가:**  AEM Sites 페이지에 여러 적응형 Forms을 만들거나 추가하여 사용자의 환경 설정 및 요구 사항에 따라 다양한 선택 사항을 제공할 수 있습니다. AEM 페이지 편집기 를 사용하여 여러 양식을 AEM Sites 페이지에 빠르게 포함할 수 있습니다. 다음을 사용할 수 있습니다. **[!UICONTROL 적응형 양식 컨테이너]** AEM Sites 페이지에 적응형 Forms을 추가하기 위한 구성 요소를 여러 번 추가했습니다. 다음을 사용할 수 있습니다. **[!UICONTROL 적응형 Forms - 포함]** 구성 요소를 AEM Sites 페이지에서 여러 번 만듭니다. **[!UICONTROL 폼은 프레임의 전체 너비를 포함합니다.]** 옵션이 선택되어 있습니다. 만일의 경우에 **[!UICONTROL 폼은 프레임의 전체 너비를 포함합니다.]** 옵션이 선택되어 있지 않습니다. AEM Sites 페이지는 iframe 없이 하나의 적응형 양식만 존재하도록 지원합니다. 를 사용하여 더 많은 적응형 Forms을 추가하려면 **[!UICONTROL 적응형 Forms - 포함]** 구성 요소, 선택 **[!UICONTROL 폼은 프레임의 전체 너비를 포함합니다.]** 옵션을 선택합니다.

## AEM Sites 페이지 또는 AEM 경험 조각에 적응형 양식을 임베드하기 위한 고려 사항 {#consideration}

* 을 사용하여 양식을 만들거나 추가할 때 **[!UICONTROL 적응형 Forms - 포함(v2)]** 구성 요소인 양식은 AEM Forms 번역 플로우를 사용하여 번역 및 현지화 과정을 거칩니다. 이 경우 Sites 페이지의 모든 언어 사본에서 단일 양식을 관리하고 참조하십시오. **[!UICONTROL 적응형 Forms - 포함(v2)]** 구성 요소는 버전 관리, 타기팅, 번역 및 다중 사이트 관리자와 같은 AEM Sites 페이지의 다양한 기능에 대한 액세스를 제공하지 않습니다.

* 를 사용할 때 **[!UICONTROL 적응형 양식 컨테이너]** 양식을 만들려면 AEM Sites 번역 플로우를 통해 양식이 번역되고 현지화됩니다. 각 언어별로 사이트 페이지와 해당 양식의 별도 사본(언어 사본)을 생성하고, 콘텐츠 작성자가 상위 페이지의 양식에서 규칙을 수정하는 경우 양식의 모든 언어 사본에 대해 동일한 변경을 수행해야 합니다. **[!UICONTROL 적응형 양식 컨테이너]** 또한 버전 관리, 타겟팅, 번역 및 다중 사이트 관리자와 같은 AEM Sites 페이지의 다양한 기능을 사용할 수 있습니다.


## AEM Sites 페이지 또는 AEM 경험 조각에 적응형 양식을 임베드하기 위한 요구 사항 {#before-you-start-embedding-an-adaptive-form}

새 적응형 양식 또는 기존 적응형 양식 임베드를 시작하기 전에 **[!UICONTROL 적응형 Forms - 포함(v2)]**, 활성화 **적응형 Forms 핵심 구성 요소** 및 추가 **적응형 Forms 클라이언트 라이브러리** AEM Sites 페이지로:

+++  AEM Cloud Service 환경에 맞는 적응형 양식 핵심 구성 요소를 활성화합니다

[AEM Forms as a Cloud Service 환경에 맞는 적응형 양식 핵심 구성 요소가 활성화되어 있는지](enable-adaptive-forms-core-components.md) 확인합니다.

+++

+++  AEM Sites 페이지 또는 경험 조각에 적응형 Forms 클라이언트 라이브러리 추가

다음의 경우 **[!UICONTROL 양식이 페이지의 전체 너비를 포함하는 경우]** 옵션이에서 선택됨 **[!UICONTROL 양식 컨테이너]** 구성 대화 상자 및 핵심 구성 요소를 사용하는 적응형 Forms 가 사용되며 해당 사이트의 페이지에 클라이언트 라이브러리를 포함해야 합니다.

![양식이 페이지 전체 너비를 포함하면 옵션이 선택되고 핵심 구성 요소가 있는 적응형 양식이 사용됩니다](/help/forms/assets/overlaycorecomponent.gif)


추가 **Customheaderlibs** 및 **Customfooterlibs** 클라이언트 라이브러리를 배포 파이프라인을 사용하여 AEM Sites 페이지에 추가합니다. 클라이언트 라이브러리를 추가하려면 다음을 수행하십시오.

1. [AEM Cloud Service Git 저장소](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/content/managing-code/repositories.html)를 사용하고 복제합니다.
1. 플랜 텍스트 편집기에서 AEM Cloud Service Git 저장소 폴더를 엽니다. 예를 들어 Microsoft® Visual Code가 있습니다.
1. 를 엽니다. `ui.apps\src\main\content\jcr_root\apps\[your-project]\components\page\customheaderlibs.html` 을(를) 파일하고 다음 코드를 파일에 추가합니다.

   ```
       //Customheaderlibs.html
       <sly data-sly-use.clientlib="core/wcm/components/commons/v1/templates/clientlib.html">
       <sly data-sly-call="${clientlib.css @ categories='core.forms.components.runtime.all'}"/>
       </sly> 
   ```

1. 를 엽니다. `ui.apps\src\main\content\jcr_root\apps\[your-project]\components\page\customfooterlibs.html` 을(를) 파일하고 다음 코드를 파일에 추가합니다.

   ```
       //customfooterlibs.html
       <sly data-sly-use.clientlib="core/wcm/components/commons/v1/templates/clientlib.html">
       <sly data-sly-test="${!wcmmode.edit}" data-sly-call="${clientlib.js @ categories='core.forms.components.runtime.all', async=true}"/>
       </sly> 
   ```

1. 를 엽니다. `ui.apps\src\main\content\jcr_root\apps\[your-project]\components\xfpage\customheaderlibs.html` 을(를) 파일하고 다음 코드를 파일에 추가합니다.

   ```
       //Customheaderlibs.html
       <sly data-sly-use.clientlib="core/wcm/components/commons/v1/templates/clientlib.html">
       <sly data-sly-call="${clientlib.css @ categories='core.forms.components.runtime.all'}"/>
       </sly> 
   ```

1. 를 엽니다. `ui.apps\src\main\content\jcr_root\apps\[your-project]\components\xfpage\customfooterlibs.html` 을(를) 파일하고 다음 코드를 파일에 추가합니다.

   ```
       //customfooterlibs.html
       <sly data-sly-use.clientlib="core/wcm/components/commons/v1/templates/clientlib.html">
       <sly data-sly-test="${!wcmmode.edit}" data-sly-call="${clientlib.js @ categories='core.forms.components.runtime.all', async=true}"/>
       </sly> 
   ```

1. [배포 파이프라인을 실행](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/sites/administering/site-creation/enable-front-end-pipeline.html)하여 AEM as a Cloud Service 환경에 클라이언트 라이브러리를 배포합니다.

+++

+++ 사용 **[!UICONTROL 적응형 Forms - 포함(v2)]** AEM Sites 페이지 또는 경험 조각용

활성화하려면 **[!UICONTROL 적응형 Forms - 포함(v2)]** 템플릿 정책의 구성 요소에서 다음 단계를 수행합니다.

1. 편집할 AEM Sites 페이지 또는 경험 조각을 엽니다. 편집할 페이지를 열려면 페이지를 선택한 다음 **[!UICONTROL 편집]**.
1. 사이트 또는 경험 조각 페이지의 템플릿을 엽니다. 템플릿을 열려면 **[!UICONTROL 페이지 정보]** ![페이지 정보](/help/forms/assets/Smock_Properties_18_N.svg) > **[!UICONTROL 템플릿 편집]**&#x200B;으로 이동합니다. 템플릿 편집기에서 해당 템플릿이 열립니다.
1. 구조 보기의 메뉴 막대에서 **[!UICONTROL 정책]** ![정책](/help/forms/assets/Smock_FeedManagement_18_N.svg) 아이콘을 클릭합니다. 다음에서 **[!UICONTROL 허용된 구성 요소]** 목록 및 선택 **[!UICONTROL 적응형 Forms - 포함(v2)]**  확인란 **[AEM Archetype 프로젝트 이름] - 적응형 양식**.
1. **[!UICONTROL 완료]**&#x200B;를 클릭합니다.

>[!VIDEO](https://video.tv.adobe.com/v/3419369?quality=12&learn=on)

+++

## 적응형 Forms - 임베드(v2) 구성 요소를 사용하여 적응형 양식 임베드 {#embed-an-adaptive-form-in-sites-editor-or-experience-fragment}

사용 **[!UICONTROL 적응형 Forms - 포함(v2)]** 양식 만들기 마법사를 사용하여 AEM Sites 편집기 내에서 직접 적응형 양식을 만들 구성 요소. 결과 양식은 외부 엔티티로 저장되므로 다른 Sites 페이지 및 독립 실행형 양식에서 재사용할 수 있습니다. 완전히 새로운 양식을 임베드하여 요구 사항 및 디자인 환경 설정에 맞게 특별히 맞춤화한 후 AEM Sites 페이지 또는 경험 조각에서 바로 사용할 수 있습니다. 일회성 양식의 경우 AEM Sites 페이지로 직접 작성하는 것이 좋지만 경험 조각은 웹 사이트의 여러 페이지에서 재사용해야 하는 양식에 이상적입니다.

를 사용하여 새 양식을 쉽게 포함할 수 있습니다. **[!UICONTROL 적응형 Forms - 포함(v2)]**.  예를 들어 새로운 연락처 양식을 AEM Sites 페이지 또는 AEM 경험 조각에 통합한다고 가정해 보겠습니다. AEM Sites 페이지 또는 경험 조각 내에서 연락처 양식에 대해 수행된 모든 업데이트 또는 수정 사항은 배포된 모든 페이지에 자동으로 적용됩니다. 이를 통해 웹 사이트의 양식 관리를 간소화하여 전체 프로세스를 간소화하는 동시에 원활한 사용자 경험을 제공합니다.

사용 **[!UICONTROL 적응형 Forms - 포함(v2)]**, 다음 작업을 수행할 수 있습니다.

* [AEM Sites 페이지의 적응형 Forms 마법사를 사용하여 새 양식 포함](#embed-form-using-adaptive-form-wizzard-aem-sites)
* [경험 조각에 적응형 Forms 마법사를 사용하여 새 양식 포함](#embed-form-using-adaptive-form-wizzard-experience-fragment)
* [AEM Sites 페이지에 기존 적응형 양식 포함](#embed-an-adaptive-form-in-sites-editor)
* [경험 조각에 기존 양식 포함](#embed-an-adaptive-form-in-experience-fragment)
* [AEM Sites 페이지의 적응형 양식을 경험 조각으로 변환](#convert-an-adaptive-form-in-sites-page-to-an-experience-fragment)

### AEM Sites 페이지의 적응형 Forms 마법사를 사용하여 새 양식 포함 {#embed-form-using-adaptive-form-wizzard-aem-sites}

AEM Sites 페이지에 새 양식을 임베드하는 단계는 다음과 같습니다.

1. 편집 모드에서 AEM Sites 페이지를 엽니다.
1. 구성 요소 브라우저 패널에서 를 드래그 앤 드롭합니다. **[!UICONTROL 적응형 Forms - 포함(v2)]** 구성 요소를 추가합니다.
1. 다음을 클릭합니다. **플러스** 아이콘을 클릭하면 양식 만들기 마법사로 리디렉션됩니다.

   ![적응형 Forms - 임베디드 구성 요소](/help/forms/assets/aemformcontainer.png)

1. 에서 새 적응형 양식 만들기 **[!UICONTROL 양식 만들기]** 마법사.
다음 **[!UICONTROL 자산 경로]** 은(는) 이미 생성된 적응형 양식의 경로를 포함합니다.
1. 설정을 저장합니다. 이제 적응형 양식이 페이지에 포함됩니다.

>[!VIDEO](https://video.tv.adobe.com/v/3419366/adaptive-form-aem-forms?quality=12&learn=on)

다음으로, 다음을 수행할 수 있습니다. [제출 액션 설정](/help/forms/configuring-submit-actions.md) 및 양식 만들기 마법사를 사용하여 임베드된 적응형 양식의 고급 속성을 만들 수 있습니다.


### 경험 조각에 적응형 Forms 마법사를 사용하여 새 양식 포함 {#embed-form-using-adaptive-form-wizzard-experience-fragment}

새 양식을 경험 조각에 임베드하는 단계는 다음과 같습니다.

1. 편집 모드에서 경험 조각을 엽니다.
1. 구성 요소 브라우저 패널에서 를 드래그 앤 드롭합니다. **[!UICONTROL 적응형 Forms - 포함(v2)]** 구성 요소를 추가합니다.
1. 다음을 클릭합니다. **플러스** 아이콘을 클릭하면 양식 만들기 마법사로 리디렉션됩니다.

   ![적응형 Forms - 임베디드 구성 요소](/help/forms/assets/aemformcontainer.png)

1. 에서 새 적응형 양식 만들기 **[!UICONTROL 양식 만들기]** 마법사.
다음 **[!UICONTROL 자산 경로]** 은(는) 이미 생성된 적응형 양식의 경로를 포함합니다.
1. 설정을 저장합니다. 이제 적응형 양식이 경험 조각에 포함됩니다.

다음으로, 다음을 수행할 수 있습니다. [제출 액션 설정](/help/forms/configuring-submit-actions.md) 및 양식 만들기 마법사를 사용하여 임베드된 적응형 양식의 고급 속성을 만들 수 있습니다.

### AEM Sites 페이지에 기존 적응형 양식 포함 {#embed-an-adaptive-form-in-sites-editor}

포함 **[!UICONTROL 적응형 Forms - 포함(v2)]** 구성 요소를 사용하면 기존 적응형 양식을 AEM Sites 내의 페이지에 쉽게 통합할 수 있습니다. 이 기능은 적응형 Forms의 적응성과 재사용성을 크게 향상시켜 고객이 이미 만든 양식을 재사용할 수 있는 편리한 방법을 제공합니다. 예를 들어 연락처 양식을 AEM Sites 페이지에 통합하여 양식을 여러 번 다시 만들 필요가 없다고 가정해 보겠습니다.

Sites 페이지에 기존 적응형 양식을 포함하려면 다음 작업을 수행하십시오.

1. 편집 모드에서 AEM Sites 페이지를 엽니다.
1. 을(를) 드래그 앤 드롭합니다 **[!UICONTROL 적응형 Forms - 포함(v2)]** 구성 요소 브라우저의 구성 요소를 사이트 페이지로 복사합니다.
1. 탭 **[!UICONTROL 적응형 Forms - 포함]** 사이트 페이지의 구성 요소 및 탭 ![적응형 양식 컨테이너 속성](/help/forms/assets/configure-icon.svg) 작업 표시줄에 표시됩니다. 다음 **[!UICONTROL 적응형 Forms 편집 - 포함(v2)]** 대화 상자가 열립니다.
1. 에 포함할 적응형 양식을 검색하여 선택하십시오. **[!UICONTROL 자산 경로]**.
1. 설정을 저장합니다. 이제 적응형 양식이 페이지에 포함됩니다.

>[!VIDEO](https://video.tv.adobe.com/v/3419368?quality=12&learn=on)

다음으로, 다음을 수행할 수 있습니다. [제출 액션 설정](/help/forms/configuring-submit-actions.md) 및 양식 만들기 마법사를 사용하여 임베드된 적응형 양식의 고급 속성을 만들 수 있습니다.

### 경험 조각에 기존 적응형 양식 포함 {#embed-an-adaptive-form-in-experience-fragment}

양식을 AEM 경험 조각에 임베드하여 액세스 가능성을 확장할 수도 있습니다. 경험 조각에 적응형 양식을 임베드하려면 다음 작업을 수행하십시오.

1. 편집 모드에서 경험 조각을 엽니다.
1. 을(를) 드래그 앤 드롭합니다 **[!UICONTROL 적응형 Forms - 포함(v2)]** 구성 요소 브라우저의 구성 요소를 경험 조각으로 복사합니다.
1. 탭 **[!UICONTROL 적응형 Forms - 포함]** 경험 조각의 구성 요소 및 탭 ![적응형 양식 컨테이너 속성](/help/forms/assets/configure-icon.svg) 작업 표시줄에 표시됩니다. 다음 **[!UICONTROL 적응형 Forms 편집 - 포함(v2)]** 대화 상자가 열립니다.
1. 에 포함할 적응형 양식을 검색하여 선택하십시오. **[!UICONTROL 자산 경로]**.
1. 설정을 저장합니다. 이제 적응형 양식이 경험 조각에 임베드됩니다.

다음으로, 다음을 수행할 수 있습니다. [제출 액션 설정](/help/forms/configuring-submit-actions.md) 및 양식 만들기 마법사를 사용하여 임베드된 적응형 양식의 고급 속성을 만들 수 있습니다.

### AEM Sites 페이지의 양식을 경험 조각으로 변환 {#convert-an-adaptive-form-in-sites-page-to-an-experience-fragment}

Sites 페이지 편집기의 기존 적응형 양식을 경험 조각으로 변환하여 여러 페이지 또는 사이트에서 양식을 재사용할 수 있습니다.

AEM Sites 페이지의 적응형 양식을 경험 조각으로 변환하려면 다음 작업을 수행하십시오.

1. 편집 모드로 적응형 양식(적응형 Forms 컨테이너 구성 요소)이 포함된 AEM Sites 페이지를 엽니다.
1. 콘텐츠 트리를 열고 다음을 선택합니다. **[!UICONTROL 적응형 Forms 컨테이너]** 적응형 양식을 호스팅합니다. AEM Sites 페이지는 여러 적응형 Forms을 호스팅할 수 있습니다. 따라서 올바른 적응형 Forms 컨테이너를 신중하게 선택하십시오.
1. 메뉴 모음에서 ![경험 조각 변형으로 변환 아이콘](/help/forms/assets/Smock_FilingCabinet_18_N.svg) 경험 조각 변형 아이콘으로 변환합니다.

   ![파일 캐비닛 로고를 클릭하여 AEM Sites 페이지의 적응형 양식을 경험 조각으로 변환합니다](/help/forms/assets/convert-form-in-sites-page-to-an-experience-fragment.png)

   적응형 양식 컨테이너를 새 경험 조각으로 변환하거나 기존 경험 조각에 추가할 수 있는 대화 상자가 나타납니다.

1. 다음에서 **[!UICONTROL 경험 조각으로 변환]** 변형 대화 상자에서 다음 옵션의 값을 설정합니다.

   * **작업:** 을(를) 선택하여 경험 조각을 만들거나 기존 경험 조각에 추가를 선택합니다.
   * **상위 경로:** 경험 조각을 호스팅할 폴더의 경로를 지정합니다. 옵션은 새 경험 조각을 만드는 경우에만 사용할 수 있습니다.
   * **템플릿:** 경험 조각 템플릿의 경로를 지정합니다. 경험 조각 템플릿이 없는 경우 [만들기](/help/implementing/developing/extending/experience-fragments.md). 옵션은 기존 경험 조각에 적응형 양식을 추가하는 데만 사용할 수 있습니다.
   * **조각 제목:** 경험 조각의 제목을 지정합니다. 제목은 경험 조각을 고유하게 식별합니다.
   * **조각 태그:** 경험 조각의 태그를 지정합니다. 태그는 경험 조각의 카테고리를 고유하게 식별합니다.

## 적응형 양식-포함(v2) 속성 구성

의 고급 설정을 사용자 지정할 수 있습니다. **[!UICONTROL 적응형 양식 - 포함(v2)]** 구성 요소. 다음에서 **[!UICONTROL 적응형 Forms 편집 - 임베드]** 대화 상자에서 다음을 지정할 수 있습니다.

* **자산 경로**: 포함할 적응형 양식을 검색하여 선택하십시오. 에셋 브라우저에서 삭제한 경우 자동으로 채워집니다.
* **사후 제출** : 양식 제출 시 트리거할 작업을 선택합니다. 감사 메시지 또는 감사 페이지를 표시하도록 선택할 수 있습니다.
   * **감사 인사 메시지 표시**: 서식 있는 텍스트 편집기를 사용하여 메시지를 작성하여 양식 제출 시 표시하십시오. 이 옵션은 감사 메시지를 표시하도록 선택한 경우에만 사용할 수 있습니다.
   * **감사 인사 페이지 표시**: 양식 제출에 표시할 페이지를 검색하여 선택합니다. 이 옵션은 감사 페이지를 표시하도록 선택한 경우에만 사용할 수 있습니다.
   * **감사 인사 페이지로 리디렉션**: 임베드된 적응형 양식이 포함된 페이지를 감사 페이지로 바꾸는 옵션을 활성화합니다. 그렇지 않으면 감사 인사 페이지가 의 적응형 양식을 대체합니다. **[!UICONTROL 적응형 Forms - 포함(v2)]** 구성 요소. 페이지의 기본 사이트를 새로 고치지 않음 이 옵션은 감사 페이지를 표시하도록 선택한 경우에만 사용할 수 있습니다.
   * **감사 메시지**: 양식을 성공적으로 제출한 후 화면에 표시되는 간단한 확인 또는 승인입니다.
   * **감사 페이지**: 양식을 성공적으로 제출한 후 표시할 페이지를 찾아 선택합니다.

* **페이지 언어 사용**: 적응형 양식의 로케일 대신 AEM Sites 페이지의 로컬 로케일을 사용합니다. 이 옵션은 적응형 양식(Foundation)에만 적용됩니다.
* **양식에 초점 설정**: 적응형 양식의 첫 번째 필드에 초점을 설정하려면 선택합니다. 이 옵션은 적응형 양식(Foundation)에만 적용됩니다.
* **테마**: 적응형 양식 구성 요소의 스타일을 정의하는 테마를 선택합니다. 스타일링에는 글꼴 스타일, 배경색, 치수 및 정렬과 같은 모양 속성이 포함됩니다. 이 옵션은 적응형 양식(Foundation)에만 적용됩니다.

  >[!NOTE]
  >
  > 다음을 사용할 수 있습니다. **페이지 언어 사용**, **양식에 초점 설정** 및 **테마** 적응형 양식(Foundation)에만 해당하는 옵션입니다.

* **폼은 프레임의 전체 너비를 포함합니다.**: 인라인 프레임(iframe)은 적응형 양식을 AEM Sites 페이지에 로드하는 HTML 요소입니다.

   * 다음과 같은 경우 **[!UICONTROL 폼은 프레임의 전체 너비를 포함합니다.]** 확인란을 선택하면 적응형 양식이 배치되는 컨테이너의 전체 폭을 차지합니다. 이 경우 양식 렌더링에는 iframe이 사용되지 않습니다. 적응형 양식의 레이아웃과 디자인은 컨테이너의 전체 너비에 맞게 조정되므로 반응형이 좋고 다양한 화면 크기로 조정할 수 있습니다. 이 옵션을 사용하면 AEM Sites 페이지 내에 여러 적응형 Forms을 포함할 수 있습니다.

     >[!NOTE]
     >
     > AEM Sites 페이지에 여러 양식을 임베드하려면 **[!UICONTROL 폼은 프레임의 전체 너비를 포함합니다.]** 확인란.

   * 다음과 같은 경우 **[!UICONTROL 폼은 프레임의 전체 너비를 포함합니다.]** 확인란이 선택되어 있지 않으면 적응형 양식이 컨테이너의 전체 너비를 포함하지 않습니다. 대신 iframe을 사용하여 양식을 렌더링하고 특정 너비를 초과하여 확장할 수 없습니다. 이 방법은 적응형 양식에 명확한 경계가 있고 컨테이너 내에서 그 옆에 있는 다른 AEM 구성 요소와 공존해야 하는 경우 유용합니다. 이 옵션을 선택하지 않으면 AEM Sites 페이지의 적응형 Forms 하나만 iframe 없이 포함할 수 있습니다.

     >[!NOTE]
     >
     > AEM Sites 페이지는 iframe 없이 하나의 적응형 양식만 존재하도록 지원합니다. 를 사용하여 더 많은 적응형 Forms을 추가하려면 **[!UICONTROL 적응형 Forms - 포함]** 구성 요소, 선택 **[!UICONTROL 폼은 프레임의 전체 너비를 포함합니다.]** 옵션을 선택합니다.

* **높이**: 컨테이너의 높이를 지정합니다. 컨테이너의 크기를 자동으로 조정하려면 비워 둡니다.
* **CSS 클라이언트 라이브러리**: CSS 클라이언트 라이브러리의 경로를 지정합니다.

<!--
In AEM Sites page, you can add an Adaptive Form using:

* **Adaptive Forms - Embed component**
   Adaptive Forms - Embed component enables AEM Sites authors to include an existing Adaptive Form within an AEM Sites page, thereby enhancing the reusability of adaptive forms. Existing Adaptive Forms can be used standalone or embedded in the site page. This integration provides a convenient way for customers to reuse Adaptive Forms they have already created.

* **Asset browser**
  All the forms are available under Assets. You can drag-drop the form as an asset on your page.

## Prerequisites {#prerequisites}

 To embed an Adaptive Form in an AEM Sites page that uses an editable template, ensure that the AEM Form component is configured as an allowed component in the associated template. 

In case **Adaptive Forms - Embed component** is not visible in the **Component browser panel** of AEM sites page, perform the following steps as illustrated in the video.

>[!VIDEO](https://video.tv.adobe.com/v/3410544)

In case Sites page is using a static template, you need to configure it in the paragraph system of the site page. 

## Embedding an Adaptive Form {#af-component}

To embed an Adaptive Form using the **[!UICONTROL Adaptive Forms - Embed]** component:

1. Open the AEM sites page, in edit mode, in which you want to embed an Adaptive Form.
1. From the Component browser panel, drag-drop the [!UICONTROL Adaptive Forms - Embed] component on the page. Alternatively, you can search for an Adaptive Form in the Assets browser and drag-drop it onto the Sites page. You can add a new Adaptive Form or embed an existing Adaptive Form. 

   >[!NOTE]
   >
   >Multiple Adaptive Forms - Embed components on a page are not supported.

1. To create and embed a new form, on the component toolbar, tap the **Create Form** icon. A window to create the form opens. 

1. Tap the embedded Adaptive Forms - Embed component in the sites page, and then tap ![settings_icon](assets/settings_icon.png) on the action bar. The **[!UICONTROL Edit Adaptive Forms - Embed]** dialog opens.
1. In the Edit Adaptive Forms - Embed dialog, specify the following.

    **Asset Type:** Select the type of asset to embed. 
    * **Asset Path**: Browse and select the Adaptive Form to embed. It is auto-populated if you dropped it from the Assets browser.
    * **Post Submission** : Select the action to trigger on form submission. You can choose to show a thank you message or a thank you page.
        * Show

        * **Thank You Message**: Write a message using the rich text editor to show on form submission. This option is available only when you choose to show a thank you message.
        * **Thank You Page**: Browse and select the page to display on form submission. This option is available only when you choose to show a thank you page.
           * **Redirect to thank you page**: Enable the option to replace the page containing the embedded Adaptive Form with thank you page. Otherwise, the thank you page replaces the Adaptive Form in the [!UICONTROL Adaptive Forms - Embed] component, without refreshing underlying sites the page. This option is available only when you choose to show a thank you page.
    * **Use Page Language**: Use local of the AEM Sites page instead locale of Adaptive Form.
    * **Set Focus on Form**: Select to set the focus on the first field of the Adaptive Form.
    * **Theme**: Select a theme that defines styling for components of your Adaptive Form. Styling includes appearance properties such as font style, background color, dimensions, and alignment.
    * **Form covers entire width of the frame**: If checked, iframe is not used to render the form. 
    * **Height**: Specify the height of the container. Leave it blank to automatically resize the container.
    * **CSS Client library**: Specify path to a CSS client library.

1. Save the settings. The Adaptive Form  is now embedded in the page.


AEM site also lets you create an Adaptive Form on the fly using the Adaptive Forms - Embed component. Follow the steps to create an Adaptive Form using the **Adaptive Forms - Embed component** on AEM sites page:
1. Open the AEM sites page, in edit mode, in which you want to embed an Adaptive Form.
1. From the Component browser panel, drag-drop the Adaptive Forms - Embed component on the page.
1. Click the **Plus** icon and you are redirected to the form creation wizard.

    ![Adaptive Forms - Embed Component](/help/forms/assets/aemformcontainer.png)

1. You can now embed an Adaptive Form on AEM site pages using the [!UICONTROL AEM Forms Container Component].
-->

## 포함된 적응형 양식 게시 {#publishing-embedded-adaptive-form}

AEM sites 페이지에 임베드된 적응형 양식을 게시하기 위한 다음 시나리오를 살펴보겠습니다.

* AEM Sites 페이지를 처음 게시하며 임베드된 적응형 양식이 포함된 경우 사이트 페이지와 임베드된 에셋을 게시합니다.
* 게시된 사이트 페이지에서 임베드된 적응형 양식만 수정한 경우 원래 에셋을 게시하고 변경 사항은 게시된 사이트 페이지에 반영됩니다. 게시된 사이트 페이지에는 자산에 대한 참조가 포함되어 있으며 페이지를 다시 게시할 필요가 없습니다.
* 사이트 페이지 및 임베드된 적응형 양식을 수정한 경우 사이트 페이지 및 임베드된 자산을 다시 게시하십시오.

## 포함된 적응형 양식 수정  {#modifying-embedded-adaptive-form}

임베드된 적응형 양식의 구성 또는 속성을 수정하려면 다음 중 하나를 수행합니다.

* 각 편집기에서 적응형 양식의 원본 양식을 열고 수정합니다.
* 편집 모드로 사이트 페이지 내에서 적응형 양식을 탭한 다음 을 누릅니다 **[!UICONTROL 새 창에서 편집]**. 원본 양식은 편집 모드에서 열리고 수정할 수 있습니다.

>[!NOTE]
>
>원래 적응형 양식에서 변경된 사항은 임베드된 양식에 자동으로 반영됩니다. 단, 적응형 양식 또는 사이트의 페이지를 다시 게시하여 게시된 페이지의 변경 사항을 반영합니다.

## 모범 사례 {#best-practices}

AEM 사이트 페이지에 적응형 Forms을 포함할 때는 다음 사항을 염두에 두십시오.

* 원래 양식의 머리글 및 바닥글은 포함된 양식에 포함되지 않습니다.
* 포함된 양식의 사용자 초안 및 제출은 Forms 포털의 초안 및 제출된 Forms 탭에서 지원되고 볼 수 있습니다.
* 원래 양식에 구성된 제출 액션은 포함된 양식에 유지됩니다.
* 원래 양식에 대해 Adobe Analytics이 구성된 경우, 임베드된 양식의 분석 데이터가 Adobe Analytics에 캡처됩니다. 하지만 양식 분석 보고서에서는 사용할 수 없습니다.

## 추가 참조 {#see-also}

* [독립형 적응형 Forms 기반의 핵심 구성 요소 만들기](/help/forms/creating-adaptive-form-core-components.md)
* [AEM Sites 페이지에서 바로 핵심 구성 요소 기반 적응형 양식 만들기](/help/forms/create-or-add-an-adaptive-form-to-aem-sites-page.md)
