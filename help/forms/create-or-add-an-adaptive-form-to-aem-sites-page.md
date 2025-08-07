---
title: AEM Sites 페이지에 적응형 양식을 추가하는 방법
description: 적응형 양식을 만들거나 AEM Sites 페이지에 추가하는 방법을 알아봅니다. 또한 웹 사이트에 양식을 통합하는 이점 및 다양한 방법에 대해 알아봅니다.
feature: Adaptive Forms, Foundation Components
Keywords: AF in Sites editor, af in aem sites, aem sites af, add af to a sites page, af aem sites, af sites, create af in a sites page, adaptive form in aem sites, forms aem sites, add form to a sites page, adaptive forms aem sites, add adaptive forms to aem page, create forms in an aem sites page
exl-id: a1846c5d-7b0f-4f48-9d15-96b2a8836a9d
role: User, Developer
source-git-commit: 2e2a0bdb7604168f0e3eb1672af4c2bc9b12d652
workflow-type: tm+mt
source-wordcount: '3162'
ht-degree: 19%

---

# AEM Sites 페이지 또는 경험 조각에 적응형 양식 추가 {#create-or-add-an-adaptive-form-to-aem-sites-page}

| 버전 | 문서 링크 |
| -------- | ---------------------------- |
| AEM 6.5 | [여기 클릭](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-basic-authoring/create-or-add-an-adaptive-form-to-aem-sites-page.html) |
| AEM as a Cloud Service | 이 문서 |

## 개요 {#overview}

AEM Forms을 사용하면 AEM Sites 페이지에 양식을 원활하게 추가할 수 있습니다. 이를 통해 방문자는 현재 페이지를 떠나지 않고 편리하게 양식을 작성하고 제출할 수 있습니다. 이렇게 하면 방문자는 양식과 상호 작용하면서 웹 사이트의 다른 요소에 지속적으로 관심을 가질 수 있습니다.

AEM 페이지 편집기 를 사용하여 여러 양식을 신속하게 만들고 AEM Sites 페이지에 추가할 수 있습니다. 콘텐츠 작성자는 AEM 페이지 편집기를 사용하여 동적 동작, 유효성 검사, 데이터 통합, 기록 문서 생성 및 비즈니스 프로세스 자동화를 비롯한 적응형 양식 구성 요소의 기능을 사용하여 Sites 페이지 내에서 매끄러운 데이터 캡처 경험을 만들 수 있습니다. 또한 버전 관리, 타겟팅, 번역 및 다중 사이트 관리자와 같은 AEM Sites 페이지의 다양한 기능을 사용할 수 있습니다.

AEM Forms Cloud Service은 적응형 양식 컨테이너 및 적응형 Forms - 임베드 구성 요소 를 제공합니다. 적응형 양식 컨테이너를 사용하여 AEM Sites 페이지 또는 경험 조각에서 양식을 만들 수 있습니다. 반면 적응형 Forms - 임베드 구성 요소를 사용하면 기존 적응형 양식을 추가하거나 적응형 Forms 편집기를 사용하여 양식을 만들 수 있습니다.

![AEM Sites 페이지의 적응형 양식의 예](/help/forms/assets/adaptive-form-in-sites-page.png)

## 적응형 Forms 핵심 구성 요소를 사용하여 AEM Sites 페이지 또는 경험 조각에서 적응형 양식을 만드는 이유는 무엇입니까?

과거에 사이트에 대한 적응형 Forms 기초 구성 요소 또는 일반 HTML 기반 양식을 만든 경우 Adobe에서는 적응형 Forms 핵심 구성 요소를 사용하여 AEM Sites 페이지 또는 경험 조각에서 적응형 양식을 만들 것을 권장합니다. 이를 통해 버전 관리, 타겟팅, 번역 및 다중 사이트 관리자와 같은 AEM Sites 페이지의 다양한 기능을 사용할 수 있으므로 적응형 Forms에 대한 전반적인 양식 생성 및 관리 경험이 향상됩니다. 다음 기능 중 일부를 살펴보겠습니다.

* **버전 관리:** AEM Sites 페이지는 [강력한 버전 관리 기능](/help/sites-cloud/authoring/sites-console/page-versions.md)을 제공하므로 다양한 버전의 양식을 추적하고 관리할 수 있습니다. 이렇게 하면 필요한 경우 이전 버전으로 롤백하는 기능을 유지하면서 양식을 변경하고 개선할 수 있습니다. 버전 관리를 통해 개발 및 진화를 형성하기 위한 통제되고 조직화된 접근 방식을 확보할 수 있습니다.
* **타깃팅(Adobe Target과 통합):** AEM Sites 페이지 타깃팅 기능을 사용하면 [다른 대상자를 위해 양식 환경을 개인 설정할 수도 있습니다](/help/sites-cloud/integrating/integrating-adobe-target.md). 사용자 세그먼트와 타겟팅 기준을 사용하여 양식의 콘텐츠, 디자인 또는 동작을 특정 사용자 그룹에 맞게 조정할 수 있습니다. 이를 통해 개인화되고 관련성 있는 양식 경험을 제공하여 참여도와 전환율을 높일 수 있습니다.
* **번역:** AEM Sites [번역 서비스와 원활한 통합](/help/sites-cloud/administering/translation/overview.md)을 통해 양식을 여러 언어로 쉽게 번역할 수 있습니다. 이 기능은 현지화 프로세스를 단순화하여 양식을 전 세계 대상자가 액세스할 수 있도록 합니다. AEM 번역 프로젝트 내에서 번역을 효율적으로 관리할 수 있으므로 다국어 양식 지원에 필요한 시간과 노력을 줄일 수 있습니다. 번역에 대한 자세한 내용은 고려 사항 섹션을 참조하십시오.
* **다중 사이트 관리 및 Live Copy:** AEM Sites은 강력한 [다중 사이트 관리 및 Live Copy 기능](/help/sites-cloud/administering/msm/overview.md)을 제공하므로 단일 환경에서 여러 웹 사이트를 만들고 관리할 수 있습니다. 이제 이 기능을 사용하여 여러 사이트에서 양식을 재사용할 수 있으므로 일관성을 유지하고 복제 작업을 줄일 수 있습니다. 중앙 집중식 제어 및 관리를 통해 여러 웹 사이트에서 양식을 효율적으로 유지 관리하고 업데이트할 수 있습니다.
* **테마:** AEM Sites 페이지는 여러 웹 페이지에서 일관된 시각적 스타일을 디자인하고 유지 관리하는 프레임워크를 제공합니다. 색상, 글꼴, 스타일 시트 및 웹 사이트의 전체적인 모양과 느낌에 기여하는 기타 시각적 요소를 정의합니다. [AEM Sites 페이지에 맞게 디자인된 테마를 적응형 양식에 사용할 수 있으므로 시간과 노력이 절약됩니다](/help/sites-cloud/administering/site-creation/site-themes.md#using-site-themes-using-themes).
* **태그 지정:** AEM Sites 페이지를 사용하면 [페이지, 에셋 또는 기타 콘텐츠에 태그나 레이블을 할당](/help/implementing/developing/introduction/tagging-framework.md)할 수 있습니다. 태그는 특정 기준에 따라 콘텐츠를 분류하고 구성하는 방법을 제공하는 키워드 또는 메타데이터 레이블입니다. 페이지, 에셋 또는 AEM 내의 다른 콘텐츠 항목에 하나 이상의 태그를 할당하여 검색을 개선하고 에셋을 분류할 수 있습니다.
* **컨텐츠 잠금 및 잠금 해제:** AEM Sites을 사용하면 사용자가 AEM Sites 환경에서 [페이지에 대한 액세스 및 수정 사항을 제어](/help/sites-cloud/authoring/page-editor/edit-content.md)할 수 있습니다. 페이지가 잠기면 다른 사용자가 승인되지 않은 변경 또는 편집하지 못하도록 보호됩니다. 콘텐츠를 잠근 사용자 또는 지정된 관리자만 수정을 허용하도록 잠금을 해제할 수 있습니다.

또한 AEM 페이지 편집기의 적응형 Forms은 [적응형 Forms 핵심 구성 요소](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html#features)를 사용합니다. 이러한 핵심 구성 요소는 [AEM Sites WCM 구성 요소](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html)와(과) 동일하게 구성 요소의 스타일을 지정하고 사용자 지정하는 보다 쉬운 표준 방법을 제공합니다.


## AEM Sites 페이지 또는 AEM 경험 조각에서 적응형 양식을 만들거나 추가하는 방법 {#various-options-to-creat-or-add-an-adaptive-form-in-aem-sites-page-or-aem-experience-fragment}

다음 옵션을 활용하여 이 기능을 최대한 활용할 수 있습니다.

* **[사용자 지정 적응형 양식을 만들어 AEM Sites 페이지에 추가](#create-an-adaptive-form-in-sites-editor-or-experience-fragment):** 적응형 양식 컨테이너 구성 요소를 사용하여 새로운 양식을 처음부터 빌드할 수 있으며, 요구 사항 및 디자인 환경 설정에 맞게 맞춤화할 수 있습니다.

* **[사용자 지정 적응형 양식을 만들어 경험 조각에 추가](#create-an-adaptive-form-in-sites-editor):** 사용자 지정 적응형 양식을 AEM 경험 조각에 추가하여 양식의 범위를 확장하면 여러 페이지나 사이트에서 원활하게 재사용할 수 있습니다.

* **[적응형 양식을 경험 조각으로 변환](#convert-an-adaptive-form-in-sites-page-to-an-experience-fragment):** AEM Sites 페이지에 추가된 적응형 양식을 여러 AEM Sites 페이지에서 양식을 재사용하기 위한 경험 조각으로 변환합니다.

* **[승인된 템플릿을 기반으로 양식을 만들어 AEM Sites 페이지에 추가:](/help/forms/embed-adaptive-form-aem-sites.md#embed-form-using-adaptive-form-wizzard-aem-sites)** 사전 승인된 템플릿을 사용하여 조직의 브랜딩 지침 및 디자인 표준에 맞는 적응형 Forms을 신속하게 만들 수 있습니다. 옵션은 적응형 Forms 편집기 또는 적응형 Forms - 임베드 구성 요소로 생성된 적응형 Forms에 대해서만 사용할 수 있습니다.

* **[AEM Sites 페이지에 기존 양식 추가:](/help/forms/embed-adaptive-form-aem-sites.md#embed-an-adaptive-form-in-sites-editor)** 이미 만든 양식을 웹 사이트에 쉽게 통합하여 방문자가 직접 상호 작용할 수 있도록 할 수 있습니다. 옵션은 적응형 Forms 편집기 또는 적응형 Forms - 임베드 구성 요소로 생성된 적응형 Forms에 대해서만 사용할 수 있습니다.


* **AEM Sites 페이지 또는 경험 조각에 여러 양식 추가:** AEM Sites 페이지에 여러 적응형 Forms을 만들거나 추가하여 사용자의 환경 설정 및 요구 사항에 따라 다양한 선택 사항을 제공할 수 있습니다. 처음부터 새로 만든 양식과 기존 양식을 조합할 수 있습니다. **[!UICONTROL 적응형 양식 컨테이너]** 구성 요소를 여러 번 사용하여 AEM Sites 페이지에 적응형 Forms을 추가할 수 있습니다. **[!UICONTROL 폼이 프레임의 전체 너비를 포함]** 옵션을 선택한 경우에만 AEM Sites 페이지에서 **[!UICONTROL 적응형 Forms - 포함]** 구성 요소를 여러 번 사용할 수 있습니다. **[!UICONTROL Form이 프레임의 전체 너비를 포함]** 옵션이 선택되어 있지 않은 경우 AEM Sites 페이지에서는 iframe 없이 하나의 적응형 양식만 존재할 수 있습니다. **[!UICONTROL 적응형 Forms - 포함]** 구성 요소를 사용하여 적응형 Forms을 더 추가하려면 **[!UICONTROL 프레임의 전체 너비를 포함하는 양식]** 옵션을 선택하십시오.

## AEM Sites 페이지 또는 AEM 경험 조각에서 적응형 양식을 만들기 위한 고려 사항 {#consideration}

* 적응형 양식 컨테이너를 사용하여 양식을 만들거나 추가하는 경우 AEM Sites 번역 흐름을 통해 양식을 번역하고 현지화를 수행합니다. 각 언어별로 사이트 페이지와 해당 양식의 별도 사본(언어 사본)을 생성하고, 콘텐츠 작성자가 상위 페이지의 양식에서 규칙을 수정하는 경우 양식의 모든 언어 사본에 대해 동일한 변경을 수행해야 합니다. 또한 적응형 양식 컨테이너를 사용하여 버전 관리, 타기팅, 번역 및 다중 사이트 관리자와 같은 AEM Sites 페이지의 다양한 기능을 사용할 수 있습니다.

* 적응형 양식 임베드 구성 요소를 사용하여 양식을 만들거나 추가하는 경우 AEM Forms 번역 흐름을 통해 양식을 번역하고 현지화를 수행합니다. 이 경우 Sites 페이지의 모든 언어 사본에서 단일 양식을 관리하고 참조하십시오. 적응형 양식 임베드 구성 요소는 버전 관리, 타깃팅, 번역 및 다중 사이트 관리자 등 AEM Sites 페이지의 다양한 기능에 대한 액세스 권한을 제공하지 않습니다.


## AEM Sites 페이지 또는 AEM 경험 조각에서 적응형 양식을 만들거나 추가하기 위한 요구 사항 {#before-you-start-creating-an-adaptive-form}

적응형 양식 만들기를 시작하기 전에 적응형 Forms 핵심 구성 요소를 활성화하고 적응형 Forms 클라이언트 라이브러리를 AEM Sites 페이지에 추가합니다.

### AEM Cloud Service 환경에 대한 적응형 Forms 핵심 구성 요소 활성화

[AEM Forms as a Cloud Service 환경에 맞는 적응형 양식 핵심 구성 요소가 활성화되어 있는지](enable-adaptive-forms-core-components.md) 확인합니다.

### AEM Sites 페이지 또는 경험 조각에 적응형 Forms 클라이언트 라이브러리 추가

적응형 양식 컨테이너 구성 요소의 전체 기능을 활성화하려면 배포 파이프라인을 사용하여 AEM Sites 페이지에 Customheaderlibs 및 Customfooterlibs 클라이언트 라이브러리를 추가합니다. 라이브러리를 추가하려면:

1. [AEM Cloud Service Git 저장소](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/content/managing-code/repositories.html)를 사용하고 복제합니다.
1. 플랜 텍스트 편집기에서 AEM Cloud Service Git 저장소 폴더를 엽니다. 예: Microsoft Visual 코드.
1. `ui.apps\src\main\content\jcr_root\apps\[your-project]\components\page\customheaderlibs.html` 파일을 열고 다음 코드를 파일에 추가합니다.

   ```
       //Customheaderlibs.html
   
       <sly data-sly-use.clientlib="core/wcm/components/commons/v1/templates/clientlib.html">
       <sly data-sly-call="${clientlib.css @ categories='core.forms.components.runtime.all'}"/>
       </sly> 
   ```

1. `ui.apps\src\main\content\jcr_root\apps\[your-project]\components\page\customfooterlibs.html` 파일을 열고 다음 코드를 파일에 추가합니다.

   ```
       //customfooterlibs.html
       <sly data-sly-use.clientlib="core/wcm/components/commons/v1/templates/clientlib.html">
       <sly data-sly-test="${!wcmmode.edit}" data-sly-call="${clientlib.js @ categories='core.forms.components.runtime.all', async=true}"/>
       </sly> 
   ```

1. `ui.apps\src\main\content\jcr_root\apps\[your-project]\components\xfpage\customheaderlibs.html` 파일을 열고 다음 코드를 파일에 추가합니다.

   ```
       //Customheaderlibs.html
       <sly data-sly-use.clientlib="core/wcm/components/commons/v1/templates/clientlib.html">
       <sly data-sly-call="${clientlib.css @ categories='core.forms.components.runtime.all'}"/>
       </sly> 
   ```

1. `ui.apps\src\main\content\jcr_root\apps\[your-project]\components\xfpage\customfooterlibs.html` 파일을 열고 다음 코드를 파일에 추가합니다.

   ```
       //customfooterlibs.html
       <sly data-sly-use.clientlib="core/wcm/components/commons/v1/templates/clientlib.html">
       <sly data-sly-test="${!wcmmode.edit}" data-sly-call="${clientlib.js @ categories='core.forms.components.runtime.all', async=true}"/>
       </sly> 
   ```

1. [배포 파이프라인을 실행](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/sites/administering/site-creation/enable-front-end-pipeline.html)하여 AEM as a Cloud Service 환경에 클라이언트 라이브러리를 배포합니다.

### AEM Sites 페이지 또는 경험 조각에 대해 적응형 Forms 컨테이너 활성화

템플릿의 정책에서 [!UICONTROL 적응형 양식 컨테이너] 구성 요소를 활성화하려면 다음 절차를 수행해야 합니다.

1. 편집할 AEM Sites 페이지 또는 경험 조각을 엽니다. 편집할 페이지를 열려면 페이지를 선택하고 편집을 클릭합니다.
1. 사이트 또는 경험 조각 페이지의 템플릿을 엽니다. 템플릿을 열려면 [!UICONTROL 페이지 정보] ![페이지 정보](/help/forms/assets/Smock_Properties_18_N.svg) > [!UICONTROL 템플릿 편집]으로 이동합니다. 템플릿 편집기에서 해당 템플릿이 열립니다.
1. 구조 보기의 메뉴 막대에서 **[!UICONTROL 정책]** ![정책](/help/forms/assets/Smock_FeedManagement_18_N.svg) 아이콘을 클릭합니다. **[!UICONTROL 허용된 구성 요소]** 목록에서 **[AEM Archetype 프로젝트 이름] - 적응형 양식** 아래의 **[!UICONTROL 적응형 양식 컨테이너]** 확인란을 선택합니다.
1. **[!UICONTROL 완료]**&#x200B;를 클릭합니다.

>[!VIDEO](https://video.tv.adobe.com/v/3419370?quality=12&learn=on)

+++

## 적응형 양식 만들기 {#create-an-adaptive-form-in-sites-editor-or-experience-fragment}

AEM Sites 페이지 또는 경험 조각에서 직접 요구 사항 및 디자인 환경 설정에 맞게 맞춤화하여 처음부터 새로운 양식을 만들 수 있습니다. 일회성 양식의 경우 AEM Sites 페이지로 직접 작성하는 것이 좋지만 경험 조각은 웹 사이트의 여러 페이지에서 재사용해야 하는 양식에 이상적입니다.

* [AEM Sites 페이지에서 양식 만들기](#create-an-adaptive-form-in-sites-editor)
* [경험 조각에서 양식 만들기](#create-an-adaptive-form-in-experience-fragment)
* [AEM Sites 페이지의 적응형 양식을 경험 조각으로 변환](#convert-an-adaptive-form-in-sites-page-to-an-experience-fragment)

### AEM Sites 페이지에서 양식 만들기 {#create-an-adaptive-form-in-sites-editor}

AEM 페이지 편집기에서 적응형 양식 컨테이너 구성 요소를 사용하여 사용자 정의 양식을 만들 수 있습니다. 구성 요소를 사용하여 양식 구성 요소를 드래그 앤 드롭하여 양식을 만들 수 있습니다. 양식 구성 요소는 핵심 구성 요소를 기반으로 합니다. 조직의 요구 사항에 따라 손쉽게 사용자 정의할 수 있습니다.

>[!VIDEO](https://video.tv.adobe.com/v/3419284?quality=12&learn=on)

Sites 페이지에서 적응형 양식을 만들려면:

1. 편집 모드에서 AEM Sites 페이지를 엽니다.
1. **[!UICONTROL 적응형 양식 컨테이너]** 구성 요소를 구성 요소 브라우저에서 Sites 페이지로 드래그 앤 드롭합니다. 양식 페이지에 공간을 만듭니다. 레이아웃 모드를 사용하여 컨테이너 공간 크기를 변경할 수 있습니다.
1. 적응형 양식 핵심 구성 요소를 컨테이너 공간으로 드래그 앤 드롭하여 양식을 만듭니다.
1. 제출 버튼을 추가합니다.

그런 다음 [제출 액션을 설정](#configure-submit-action-for-form)하고 고급 속성을 설정합니다.

### 경험 조각에서 양식 만들기 {#create-an-adaptive-form-in-experience-fragment}

양식을 AEM 경험 조각에 추가하여 양식의 범위를 확장하고 여러 페이지 또는 사이트에서 원활하게 재사용할 수 있습니다. 예를 들어 경험 조각 내에 뉴스레터 신청 양식을 포함할 수 있습니다. 이렇게 하면 웹 사이트의 여러 페이지에서 조각을 편리하게 재사용할 수 있으므로 양식을 반복적으로 다시 만들 필요가 없습니다. 경험 조각 내에서 뉴스레터 등록 양식에 대해 수행된 모든 업데이트 또는 수정 사항은 활용되는 모든 페이지에 자동으로 전파됩니다. 이로써 프로세스를 간소화하고 원활한 사용자 경험을 제공하는 동시에 웹 사이트 양식 관리를 간소화합니다.

경험 조각에서 적응형 양식을 만들려면:

1. 경험 조각을 엽니다.
1. 구성 요소 브라우저에서 경험 조각으로 **[!UICONTROL 적응형 Forms 컨테이너]** 구성 요소를 드래그 앤 드롭합니다.
1. 적응형 양식 핵심 구성 요소를 경험 조각의 컨테이너 공간으로 끌어다 놓아 양식을 만듭니다.
1. 제출 버튼을 추가합니다.

그런 다음 [제출 액션을 설정](#configure-submit-action-for-form)하고 고급 속성을 설정합니다.

### AEM Sites 페이지의 양식을 경험 조각으로 변환 {#convert-an-adaptive-form-in-sites-page-to-an-experience-fragment}

Sites 페이지 편집기의 기존 적응형 양식을 경험 조각으로 변환하여 여러 페이지 또는 사이트에서 양식을 재사용할 수 있습니다.

AEM Sites 페이지의 적응형 양식을 경험 조각으로 변환하려면 다음 작업을 수행하십시오.

1. 편집 모드로 적응형 양식(적응형 Forms 컨테이너 구성 요소)이 포함된 AEM Sites 페이지를 엽니다.
1. 콘텐츠 트리를 열고 적응형 양식을 호스팅하는 **[!UICONTROL 적응형 Forms 컨테이너]**&#x200B;를 선택합니다. AEM Sites 페이지는 여러 적응형 Forms을 호스팅할 수 있습니다. 따라서 올바른 적응형 Forms 컨테이너를 신중하게 선택하십시오.
1. 메뉴 표시줄에서 ![경험 조각으로 변환 아이콘](/help/forms/assets/Smock_FilingCabinet_18_N.svg) 경험 조각 변형으로 변환 아이콘을 선택합니다.
   ![파일 캐비닛 로고를 클릭하여 AEM Sites 페이지의 적응형 양식을 경험 조각으로 변환](/help/forms/assets/convert-form-in-sites-page-to-an-experience-fragment.png)

   적응형 양식 컨테이너를 새 경험 조각으로 변환하거나 기존 경험 조각에 추가할 수 있는 대화 상자가 나타납니다
1. 경험 조각 변형으로 변환 대화 상자에서 다음 옵션에 대한 값을 설정합니다.

   * **작업:** 경험 조각을 만들거나 기존 경험 조각에 추가하려면 선택하십시오.
   * **상위 경로:** 경험 조각을 호스팅할 폴더의 경로를 지정합니다. 옵션은 경험 조각을 만드는 경우에만 사용할 수 있습니다.
   * **템플릿:** 경험 조각 템플릿의 경로를 지정합니다. 경험 조각 템플릿이 없는 경우 [만듭니다](/help/implementing/developing/extending/experience-fragments.md). 옵션은 기존 경험 조각에 적응형 양식을 추가하는 데만 사용할 수 있습니다.
   * **조각 제목:** 경험 조각의 제목을 지정합니다. 제목은 경험 조각을 고유하게 식별합니다


## AEM Sites 페이지 또는 경험 조각에서 양식에 대한 제출 액션 구성 {#configure-submit-action-for-form}

제출 액션을 사용하면 적응형 양식을 통해 캡처되는 데이터의 대상을 선택할 수 있습니다. 사용자가 적응형 양식에서 제출 단추를 클릭하면 트리거됩니다. 적응형 양식에는 즉시 사용 가능한 제출 액션이 포함됩니다. 기본 제출 액션을 확장하여 자신만의 사용자 지정 제출 액션을 만들 수도 있습니다. 양식에 대해 제출 액션을 구성하려면 다음 작업을 수행하십시오.

1. 적응형 양식이 포함된 AEM 페이지 편집기 또는 경험 조각을 엽니다.
1. 콘텐츠 트리를 열고 적응형 양식을 호스팅하는 **[!UICONTROL 적응형 Forms 컨테이너]**&#x200B;를 선택합니다. AEM Sites 페이지는 여러 적응형 Forms을 호스팅할 수 있습니다. 따라서 올바른 적응형 Forms 컨테이너를 신중하게 선택하십시오.
1. 적응형 양식 컨테이너 속성 ![적응형 양식 컨테이너 속성](/help/forms/assets/configure-icon.svg) 아이콘을 클릭합니다. 제출 액션을 구성할 수 있는 적응형 양식 컨테이너 대화 상자가 열립니다.
   ![렌치 아이콘을 클릭하여 적응형 양식 컨테이너 대화 상자를 열어 적응형 양식에 대한 제출 액션을 구성하십시오](/help/forms/assets/adaptive-forms-container.png)
1. 요구 사항에 따라 제출 액션을 선택하고 구성합니다. 제출 액션에 대한 자세한 내용은 [적응형 양식 제출 액션](/help/forms/configuring-submit-actions.md)을 참조하세요.


## AEM Sites 페이지 또는 경험 조각에서 양식에 대한 스키마 또는 양식 데이터 모델(FDM) 구성 {#configure-schema-or-data-model-for-form}

FDM(양식 데이터 모델)을 사용하여 양식을 데이터 Source에 연결하여 사용자 작업에 따라 데이터를 보내고 받을 수 있습니다. 양식을 JSON 스키마에 연결하여 미리 정의된 형식으로 제출된 데이터를 받을 수도 있습니다. 요구 사항에 따라 양식을 JSON 스키마 또는 양식 데이터 모델(FDM)에 연결합니다.

* [JSON 스키마를 만들고 환경에 업로드](/help/forms/adaptive-form-json-schema-form-model.md) 또는,
* [양식 데이터 모델(FDM) 만들기](/help/forms/create-form-data-models.md)

양식에 대해 JSON 스키마 또는 양식 데이터 모델(FDM)을 구성하려면 다음을 수행합니다.

1. 적응형 양식이 포함된 AEM 페이지 편집기 또는 경험 조각을 엽니다.
1. 콘텐츠 트리를 열고 적응형 양식을 호스팅하는 **[!UICONTROL 적응형 Forms 컨테이너]**&#x200B;를 선택합니다. AEM Sites 페이지는 여러 적응형 Forms을 호스팅할 수 있습니다. 따라서 올바른 적응형 Forms 컨테이너를 신중하게 선택하십시오.
1. 적응형 양식 컨테이너 속성 ![적응형 양식 컨테이너 속성](/help/forms/assets/configure-icon.svg) 아이콘을 클릭합니다. 데이터 모델을 구성하는 적응형 양식 컨테이너 대화 상자가 열립니다.
   ![렌치 아이콘을 클릭하여 적응형 양식에 대한 데이터 모델을 구성하십시오](/help/forms/assets/form-data-model-adaptive-forms-container.png)
1. 요구 사항에 따라 JSON 스키마 또는 양식 데이터 모델(FDM)을 선택하고 구성합니다. 제출 액션에 대한 자세한 내용은 [적응형 양식 제출 액션](/help/forms/configuring-submit-actions.md)을 참조하세요.

   * **[!UICONTROL 양식 모델]** 옵션을 선택하는 경우 **[!UICONTROL 양식 데이터 모델 선택]** 옵션을 사용하여 미리 구성된 양식 데이터 모델(FDM)을 선택합니다.
   * **[!UICONTROL 스키마]** 옵션을 선택하는 경우 **[!UICONTROL 스키마]** 옵션을 사용하여 양식에 대한 JSON 스키마를 선택하십시오.

1. **[!UICONTROL 완료]**&#x200B;를 클릭합니다.

## AEM Sites 페이지 또는 경험 조각에서 양식에 대한 미리 채우기 서비스를 구성합니다 {#configure-prefill-service-for-form}

미리 채우기 서비스를 사용하여 기존 데이터를 사용하는 적응형 양식의 필드를 자동으로 채울 수 있습니다. 사용자가 양식을 열면 해당 필드의 값이 미리 채워집니다. 다음과 같은 작업을 수행할 수 있습니다.

* [사용자 지정 미리 채우기 서비스 만들기](/help/forms/prepopulate-adaptive-form-fields.md)
* [양식 데이터 모델 미리 채우기 서비스 사용](#fdm-prefill-service)

### 양식 데이터 모델 미리 채우기 서비스를 사용하여 AEM Sites 페이지 또는 경험 조각에서 양식 필드를 미리 채웁니다 {#fdm-prefill-service}

양식 데이터 모델 미리 채우기 서비스를 사용하여 AEM Sites 페이지 또는 경험 조각에서 적응형 양식의 필드를 미리 채우거나 양식 데이터 모델 또는 사용자 지정 미리 채우기 서비스를 사용할 수 있습니다. 양식 데이터 모델 미리 채우기 서비스는 [구성된 양식 데이터 모델의 Get 서비스](work-with-form-data-model.md#add-data-model-objects-and-services-add-data-model-objects-and-services)를 사용하여 데이터를 검색합니다. 적응형 양식에 대해 양식 데이터 모델 미리 채우기 서비스를 사용하려면

1. 적응형 양식이 포함된 AEM 페이지 편집기 또는 경험 조각을 엽니다.
1. 콘텐츠 트리를 열고 적응형 양식을 호스팅하는 **[!UICONTROL 적응형 Forms 컨테이너]**&#x200B;를 선택합니다. AEM Sites 페이지는 여러 적응형 Forms을 호스팅할 수 있습니다. 따라서 올바른 적응형 Forms 컨테이너를 신중하게 선택하십시오.
1. 적응형 양식 컨테이너 속성 ![적응형 양식 컨테이너 속성](/help/forms/assets/configure-icon.svg) 아이콘을 클릭합니다. 데이터 모델을 구성하는 적응형 양식 컨테이너 대화 상자가 열립니다.
   ![렌치 아이콘을 클릭하여 적응형 양식 컨테이너 대화 상자를 열어 적응형 양식의 미리 채우기 서비스를 구성하십시오](/help/forms/assets/adaptive-forms-container.png)
1. 양식 데이터 모델을 선택합니다. **[!UICONTROL 기본]** 탭을 엽니다. 미리 채우기 서비스에서 **[!UICONTROL 양식 데이터 모델 미리 채우기 서비스]**&#x200B;를 선택합니다.
1. **[!UICONTROL 완료]**&#x200B;를 클릭합니다. 이제 적응형 양식이 양식 데이터 모델 미리 채우기를 사용하도록 구성되었습니다. 이제 [규칙 편집기](rule-editor.md)를 사용하여 양식의 필드를 미리 채우는 규칙을 만들 수 있습니다.


## 사용자를 페이지로 리디렉션하거나 양식 제출 시 감사 메시지 표시

양식을 제출할 때 사용자를 다른 웹 페이지나 메시지로 리디렉션할 수 있습니다. 사용자를 리디렉션하거나 감사 메시지를 구성하려면:

1. 적응형 양식이 포함된 AEM 페이지 편집기 또는 경험 조각을 엽니다.
1. 콘텐츠 트리를 열고 적응형 양식을 호스팅하는 **[!UICONTROL 적응형 Forms 컨테이너]**&#x200B;를 선택합니다. AEM Sites 페이지는 여러 적응형 Forms을 호스팅할 수 있습니다. 따라서 올바른 적응형 Forms 컨테이너를 신중하게 선택하십시오.

1. **[!UICONTROL 제출]** 탭을 엽니다.

   * 리디렉션 URL을 구성하려면 [제출 시] 옵션에서 **[!UICONTROL URL로 리디렉션]** 옵션을 선택하고 AEM Sites 페이지를 검색하여 선택하거나 외부 페이지의 URL을 제공합니다.
   * 사용자 지정 또는 감사 메시지를 구성하려면 [전송] 옵션에서 **[!UICONTROL 메시지 표시]** 옵션을 선택하고 **[!UICONTROL 메시지 내용]** 상자에 메시지를 제공합니다. 서식 있는 텍스트 상자입니다. 전체 화면 옵션을 사용하여 사용 가능한 모든 서식 있는 텍스트 항목을 볼 수 있습니다.


