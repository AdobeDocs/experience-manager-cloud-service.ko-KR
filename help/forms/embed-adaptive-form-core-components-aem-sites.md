---
title: AEM Sites 페이지에서 적응형 양식 핵심 구성 요소를 추가하거나 만드는 방법
description: AEM Sites 페이지에서 적응형 양식 핵심 구성 요소를 사용하여 AEM Sites 페이지를 종료하지 않고 양식을 작성하고 제출합니다.
feature: Adaptive Forms
hide: true
hidefromtoc: true
source-git-commit: 81951a9507ec3420cbadb258209bdc8e2b5e2942
workflow-type: tm+mt
source-wordcount: '2071'
ht-degree: 4%

---

# AEM Sites 편집기를 사용하여 적응형 양식 만들기 또는 추가 {#add-an-adaptive-form-to-aem-sites-page}

AEM Sites 페이지에 적응형 Forms을 원활하게 작성하거나 임베드하여 사용자가 사이트 페이지를 종료하지 않고도 양식을 작성하고 제출할 수 있습니다. 사용자가 웹 페이지의 다른 요소 컨텍스트에 남아 있으면서 양식과 동시에 상호 작용하는 데 도움이 됩니다.

다음 방법 중 하나를 선택하여 적응형 양식을 만들거나 AEM Sites 페이지에 추가할 수 있습니다.

* **적응형 Forms 컨테이너 구성 요소를 사용하여 적응형 양식을 만듭니다**: [적응형 양식 컨테이너](#af-container-component) 구성 요소를 사용하여 AEM Sites 편집기 내에서 직접 적응형 Forms 구성 요소를 활용하여 디지털 등록 경험을 빌드할 수 있습니다. 이 통합은 AEM Sites 페이지 내에서 양식을 만들고 관리하려는 AEM Sites 작성자에게 원활한 경험을 제공합니다.

* **기존 적응형 양식 추가**: [적응형 Forms - Embed(v2)](#embed-existing-af) 구성 요소를 사용하여 기존 적응형 양식을 AEM Sites 내의 페이지에 쉽게 추가할 수 있습니다. 이 기능은 적응형 Forms의 적응성과 재사용성을 향상시킵니다. 이 통합은 고객이 이미 만든 적응형 Forms을 재사용할 수 있는 편리한 방법을 제공합니다.

* **적응형 Forms 마법사를 사용하여 양식을 만드십시오**: [적응형 Forms - Embed(v2)](#embed-new-af) 구성 요소를 사용하여 양식 만들기 마법사를 사용하여 AEM Sites 편집기 내에서 적응형 양식을 만드십시오. 양식이 외부 엔티티로 저장됩니다. 다른 Sites 페이지 및 독립 실행형 양식에서도 이 양식을 재사용할 수 있습니다.

* **AEM Sites 페이지에 여러 적응형 Forms 추가**: AEM Sites 페이지에 여러 적응형 Forms을 추가하려면 AEM Forms 컨테이너 구성 요소([적응형 Forms - 포함(v2)](#embed-new-af) 및 [적응형 양식 컨테이너](#af-container-component))를 사용하십시오. AEM Sites 페이지 내에 div로서 적응형 양식을 두 개 이상 추가해야 하는 경우 적응형 양식 컨테이너 구성 요소를 사용할 수 있습니다.

규칙 편집기를 사용하여 적응형 양식 구성 요소의 동적 동작을 추가하거나 제어할 수 있습니다. 예를 들어 구성 요소를 숨기거나 표시합니다. 적응형 양식 구성 요소가 아닌 구성 요소에는 규칙 편집기를 사용할 수 없습니다. 따라서 AEM Forms 컨테이너 구성 요소에서 적응형 양식 구성 요소가 아닌 구성 요소를 사용하는 동안 주의력을 사용하십시오.

## 적응형 Forms 컨테이너 구성 요소를 사용하여 적응형 양식 만들기 {#af-container-component}

[!UICONTROL 적응형 양식 컨테이너] 구성 요소를 사용하면 AEM Sites 편집기에서 적응형 Forms 구성 요소를 사용하여 디지털 등록 경험을 빌드할 수 있습니다. 양식 구성 요소를 드래그 앤 드롭하여 적응형 양식을 만들 수 있습니다.

### 사전 요구 사항 {#prerequisites-af-container}

+++ **[!UICONTROL 적응형 Forms 컨테이너]** 구성 요소를 사용하도록 설정합니다.

템플릿의 정책에서 [!UICONTROL 적응형 양식 컨테이너] 구성 요소를 활성화하려면 다음 절차를 수행해야 합니다.

1. [!UICONTROL 페이지 정보] > [!UICONTROL 템플릿 편집](으)로 이동
1. [!UICONTROL 정책]을 클릭하고 **[AEM Archetype 프로젝트 이름] - 적응형 양식**&#x200B;에서 **[!UICONTROL 적응형 Forms 컨테이너]** 확인란을 선택하십시오.
1. **[!UICONTROL 완료]**&#x200B;를 클릭합니다.

>[!VIDEO](https://video.tv.adobe.com/v/3419370?quality=12&learn=on)

+++

+++ AEM Sites 페이지에 적응형 Forms 클라이언트 라이브러리 포함

AEM Sites 페이지에서 적응형 Forms 구성 요소를 사용하려면 AEM Archetype/Git 저장소 및 배포 파이프라인을 사용하여 Customheaderlibs 및 Customfooterlibs 클라이언트 라이브러리를 AEM Sites 페이지에 포함합니다.

1. 텍스트 편집기에서 [AEM Forms Archetype 또는 복제된 Git 저장소](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html) 프로젝트를 엽니다. 예: Visual Studio Code.
1. 다음으로 이동 `ui.apps/src/main/content/jcr_root/apps/corecomponents/components/page/.content.xml`.
1. `sling:resourceSuperType`의 값을 복사합니다. 예를 들어 값은 `core/wcm/components/page/v3/page`입니다.

   ![Sling 리소스](/help/forms/assets/slingresource.png)

1. `ui.apps/src/main/content/jcr_root/apps` 위치에 `core/wcm/components/page/v3/page`과(와) 동일한 유사한 구조를 만듭니다.

   ![오버레이 구조](/help/forms/assets/overlaystructure.png)

1. `customheaderlibs.html` 및 `customfooterlibs.html` 파일을 추가합니다.

   ```
   //Customheaderlibs.html
   <sly data-sly-use.clientlib="core/wcm/components/commons/v1/templates/clientlib.html">
       <sly data-sly-call="${clientlib.css @ categories='core.forms.components.runtime.all'}"/>
   </sly> 
   
   //customfooterlibs.html
   <sly data-sly-use.clientlib="core/wcm/components/commons/v1/templates/clientlib.html">
       <sly data-sly-test="${!wcmmode.edit}" data-sly-call="${clientlib.js @ categories='core.forms.components.runtime.all', async=true}"/>
   </sly> 
   ```

   customfooterlibs.html은 JavaScript에 사용되고 customheaderlibs.html은 css에 사용됩니다.

1. [파이프라인을 실행](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/sites/administering/site-creation/enable-front-end-pipeline.html)하여 변경 내용을 배포합니다.

+++

### 적응형 Forms 컨테이너 구성 요소를 사용하여 적응형 양식 만들기 {#create-af-using-af-container}


[!UICONTROL 적응형 Forms 컨테이너] 구성 요소를 사용하여 적응형 양식을 만들려면:

1. 편집 모드에서 AEM Sites 페이지를 엽니다.
1. 구성 요소 브라우저 패널에서 페이지의 **[!UICONTROL 적응형 Forms 컨테이너]** 구성 요소를 드래그 앤 드롭합니다.
1. 적응형 Forms 구성 요소를 사용하여 적응형 양식을 만듭니다.
1. 설정을 저장합니다.

>[!VIDEO](https://video.tv.adobe.com/v/3419284?quality=12&learn=on)

양식이 준비되었습니다. AEM Sites 페이지를 게시하면 적응형 양식 및 관련 참조 자산이 자동으로 게시됩니다.

#### 적응형 양식 컨테이너 속성 구성 {#configure-additional-settings-container}

[!UICONTROL 적응형 양식 컨테이너] 구성 요소의 고급 설정을 사용자 지정할 수 있습니다. 예:

* 사이트 페이지에 미리 채워진 값이 있는 적응형 양식을 로드하도록 미리 채우기 서비스를 구성할 수 있습니다.
* 적응형 양식을 데이터 소스와 연결하도록 데이터 모델 설정을 구성할 수 있습니다.
* 제출 액션을 구성하여 Microsoft® OneDrive, Microsoft® OneDrive 또는 양식 제출 시 기타 데이터 소스에 있는 데이터를 보낼 수 있습니다. 적응형 Forms에 대한 사용자 지정 제출 액션을 만들고 선택할 수도 있습니다.

**[!UICONTROL 적응형 Forms 컨테이너]** 구성 요소의 속성을 설정하려면 작업 표시줄에서 ![settings_icon](/help/forms/assets/Smock_Wrench_18_N.svg)을(를) 클릭하십시오. **[!UICONTROL 적응형 Forms 컨테이너 편집]** 대화 상자가 열립니다.

![편집 대화 상자](/help/forms/assets/adaptiveformcontainer-editdialog.png)

[!UICONTROL 적응형 Forms 컨테이너 편집] 대화 상자에서 다음을 지정할 수 있습니다.
* **기본 탭**
   * **미리 채우기 서비스**: 미리 채우기 서비스를 사용하여 기존 데이터를 사용하는 적응형 양식의 필드를 자동으로 채울 수 있습니다. 사용자가 양식을 열면 해당 필드의 값이 미리 채워집니다. 미리 채우기 서비스에 대한 자세한 내용은 [적응형 양식 필드 미리 채우기](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-foundation-components/prepopulate-adaptive-form-fields.html#configuring-prefill-service-using-configuration-manager)를 참조하세요.
   * **클라이언트 라이브러리 범주**: 식에 사용되고 적응형 Forms에서 지원하는 [JavaScript 함수](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-foundation-components/add-rules-and-use-expressions-in-an-adaptive-form/rule-editor.html?lang=en#custom-functions)를 지정합니다.
* **데이터 모델**: 데이터 모델을 사용하면 서로 다른 데이터 원본의 엔터티 및 서비스를 적응형 양식에 통합할 수 있습니다. 생성 중인 적응형 양식에 여러 데이터 원본에서 데이터를 가져오고 쓰는 작업이 포함된 경우 **[!UICONTROL 양식 데이터 모델]**&#x200B;을(를) 선택하십시오.
   * **양식 데이터 모델**: FDM(양식 데이터 모델)을 사용하면 적응형 양식이 개별 데이터 소스와 통신할 수 있습니다. 자세한 내용은 데이터 원본 구성에 대한 자세한 내용은 [데이터 원본 구성](/help/forms/configure-data-sources.md)을 참조하세요.
   * **스키마**: 스키마는 조직의 백엔드 시스템에서 데이터를 생성하거나 사용하는 구조를 나타냅니다. [스키마를 적응형 양식에 연결](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-foundation-components/create-an-adaptive-form-on-forms-cs/adaptive-form-json-schema-form-model.html)하고 해당 요소를 사용하여 적응형 양식에 동적 콘텐츠를 추가할 수 있습니다.

     >[!NOTE]
     >
     > 양식 데이터 모델(FDM)을 구성한 후에는 연관된 양식 모델을 변경할 수 없습니다. 하지만 양식 데이터 모델(FDM)과 연관된 스키마를 수정할 수 있습니다.

* **제출 탭**

   * **URL로 리디렉션**
      * **리디렉션 URL/경로**: 제출 후 적응형 양식을 리디렉션할 URL 또는 경로를 지정합니다.

      * **제출 액션**: 사용자가 적응형 양식에서 제출 단추를 클릭하면 제출 액션이 트리거됩니다. [적응형 양식에서 제출 액션을 구성](/help/forms/configuring-submit-actions.md)할 수 있습니다. 적응형 양식은 즉시 다음과 같은 제출 액션을 제공합니다.
         * REST 엔드포인트에 제출
         * 이메일 보내기
         * 양식 데이터 모델(FDM)을 사용하여 제출
         * AEM Workflow 호출
         * SharePoint에 제출
         * OneDrive에 제출
         * Azure Blob 스토리지에 제출

  [기본 제출 액션을 확장](custom-submit-action-form.md)하여 자신만의 사용자 지정 제출 액션을 만들 수도 있습니다.

* **메시지 표시**
   * **메시지 콘텐츠**: 서식 있는 텍스트 편집기를 사용하여 메시지를 작성하여 양식 제출 시 표시합니다. 이 옵션은 감사 메시지를 표시하도록 선택한 경우에만 사용할 수 있습니다.

## 적응형 양식 포함  {#aem-container-component}

**[!UICONTROL 적응형 Forms - 임베드 (V2)]** 구성 요소를 사용하여 새 적응형 양식을 임베드하거나 사이트의 페이지에 기존 적응형 양식을 임베드할 수 있습니다. [!UICONTROL 적응형 Forms - 포함(v2)] 구성 요소를 사용하여 다음 작업을 수행할 수 있습니다.

* [기존 적응형 양식 추가](#embed-new-af)

* [새 적응형 양식 만들기 및 추가](#embed-existing-af)

### 사전 요구 사항 {#prerequisites}

+++ **적응형 Forms - 포함** 구성 요소를 사용하도록 설정합니다.

템플릿의 정책에서 [!UICONTROL 적응형 Forms - Embed(v2)] 구성 요소를 활성화하려면 다음 단계를 수행하십시오.

1. [!UICONTROL 페이지 정보] > [!UICONTROL 템플릿 편집](으)로 이동

1. [!UICONTROL 정책]을 클릭하고 **[!UICONTROL [AEM Archetype 프로젝트 이름] - Forms]** 그룹 아래에서 **[!UICONTROL 적응형 양식 - 포함(v2)]** 확인란을 선택합니다.
1. **[!UICONTROL 완료]**&#x200B;를 클릭합니다.

>[!VIDEO](https://video.tv.adobe.com/v/3419369?quality=12&learn=on)

+++

+++ AEM Sites 페이지에 적응형 Forms 클라이언트 라이브러리 포함

**[!UICONTROL 양식 컨테이너]** 구성 대화 상자에서 **[!UICONTROL 양식이 페이지의 전체 너비를 포함하는 경우]** 옵션을 선택하고 **핵심 구성 요소를 사용하는 적응형 Forms**&#x200B;를 사용하는 경우 해당 사이트의 페이지에 clientlib을 포함해야 합니다.

![오버레이 Gif](/help/forms/assets/overlaycorecomponent.gif)

AEM Sites 페이지에서 적응형 Forms 구성 요소를 사용하려면 AEM Archetype/Git 저장소 및 배포 파이프라인을 사용하여 AEM Sites 페이지에 `Customheaderlibs` 및 `Customfooterlibs` 클라이언트 라이브러리를 포함하십시오.

1. 텍스트 편집기에서 [AEM Forms Archetype 또는 복제된 Git 저장소](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html) 프로젝트를 엽니다. 예: Visual Studio Code.
1. 다음으로 이동 `ui.apps/src/main/content/jcr_root/apps/corecomponents/components/page/.content.xml`.
1. `sling:resourceSuperType`의 값을 복사합니다. 예를 들어 값은 `core/wcm/components/page/v3/page`입니다.

   ![Sling 리소스](/help/forms/assets/slingresource.png)

1. `ui.apps/src/main/content/jcr_root/apps` 위치에 `core/wcm/components/page/v3/page`과(와) 동일한 유사한 구조를 만듭니다.

   ![오버레이 구조](/help/forms/assets/overlaystructure.png)

1. `customheaderlibs.html` 및 `customfooterlibs.html` 파일을 추가합니다.

   ```
   //Customheaderlibs.html
   <sly data-sly-use.clientlib="core/wcm/components/commons/v1/templates/clientlib.html"
       data-sly-use.form="com.adobe.cq.forms.core.components.models.aemform.AEMForm">
       <sly data-sly-test="${form.formVersion=='2.1' && !wcmmode.edit}" data-sly-call="${clientlib.css @ categories='core.forms.components.runtime.all'}"/>
   </sly>
   
   //customfooterlibs.html
   <sly data-sly-use.clientlib="core/wcm/components/commons/v1/templates/clientlib.html"
     data-sly-use.form="com.adobe.cq.forms.core.components.models.aemform.AEMForm">
     <sly data-sly-test="${form.formVersion=='2.1' && !wcmmode.edit}" data-sly-call="${clientlib.js @ categories='core.forms.components.runtime.all', async=true}"/>
   </sly>
   ```

   `customfooterlibs.html`은(는) JavaScript에 사용되고 `customheaderlibs.html`은(는) CSS에 사용됩니다.

1. [파이프라인을 실행](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/sites/administering/site-creation/enable-front-end-pipeline.html)하여 변경 내용을 배포합니다.

+++

### AEM Sites 페이지에 기존 적응형 양식 추가 {#embed-existing-af}

1. 편집 모드에서 AEM Sites 페이지를 엽니다.
1. 구성 요소 브라우저 패널에서 페이지의 [!UICONTROL 적응형 Forms - 포함] 구성 요소를 드래그 앤 드롭합니다.
1. 사이트 페이지에서 [!UICONTROL 적응형 Forms - 포함] 구성 요소를 선택하고 작업 표시줄에서 ![settings_icon](/help/forms/assets/Smock_Wrench_18_N.svg)을(를) 선택합니다. **[!UICONTROL 적응형 Forms 편집 - 포함]** 대화 상자가 열립니다.
1. [!UICONTROL 자산 경로]에 포함할 적응형 양식을 검색하여 선택하십시오.
1. 설정을 저장합니다. 이제 적응형 양식이 페이지에 포함됩니다.

>[!VIDEO](https://video.tv.adobe.com/v/3419368?quality=12&learn=on)



### 새 적응형 양식을 만들어 AEM Sites 페이지에 추가 {#embed-new-af}

1. 편집 모드에서 AEM Sites 페이지를 엽니다.
1. 구성 요소 브라우저 패널에서 페이지에 [!UICONTROL 적응형 Forms - 포함(v2)] 구성 요소를 드래그 앤 드롭합니다.
1. **Plus** 아이콘을 클릭하면 양식 만들기 마법사로 리디렉션됩니다.

   ![적응형 Forms - 임베디드 구성 요소](/help/forms/assets/aemformcontainer.png)

1. [!UICONTROL 양식 만들기] 마법사에서 새 적응형 양식을 만듭니다.
1. [!UICONTROL 자산 경로]에 이미 만들어진 적응형 양식의 경로가 포함되어 있습니다.
1. 설정을 저장합니다. 이제 적응형 양식이 페이지에 포함됩니다.

>[!VIDEO](https://video.tv.adobe.com/v/3419366/adaptive-form-aem-forms?quality=12&learn=on)

#### 적응형 양식 구성 - 임베드(v2) 속성 {#configure-adaptive-form-embed}

[!UICONTROL 적응형 양식 - 포함(v2)] 구성 요소의 고급 설정을 사용자 지정할 수 있습니다. [!UICONTROL 적응형 Forms 편집 - 포함(v2)] 대화 상자에서 다음을 지정할 수 있습니다.

* **자산 경로**: 포함할 적응형 양식을 검색하여 선택하십시오. Assets 브라우저에서 삭제한 경우 자동으로 채워집니다.
* **Post 제출** : 양식 제출 시 트리거할 작업을 선택합니다. 감사 메시지 또는 감사 페이지를 표시하도록 선택할 수 있습니다.
   * **감사 메시지 표시**: 서식 있는 텍스트 편집기를 사용하여 메시지를 작성하여 양식 제출 시 표시합니다. 이 옵션은 감사 메시지를 표시하도록 선택한 경우에만 사용할 수 있습니다.
   * **감사 인사 페이지 표시**: 양식 제출에 표시할 페이지를 검색하여 선택하십시오. 이 옵션은 감사 페이지를 표시하도록 선택한 경우에만 사용할 수 있습니다.
   * **감사 페이지로 리디렉션**: 포함된 적응형 양식이 포함된 페이지를 감사 페이지로 바꾸는 옵션을 사용하도록 설정합니다. 그렇지 않으면 감사 페이지는 페이지의 기본 사이트를 새로 고치지 않고 [!UICONTROL 적응형 Forms - 포함] 구성 요소의 적응형 양식을 대체합니다. 이 옵션은 감사 페이지를 표시하도록 선택한 경우에만 사용할 수 있습니다.
* **페이지 언어 사용**: 적응형 양식의 로케일 대신 AEM Sites 페이지의 로컬 로케일을 사용합니다.
* **양식에 초점 설정**: 적응형 양식의 첫 번째 필드에 초점을 설정하려면 선택합니다.
* **폼은 프레임의 전체 너비를 포함합니다**: 이 옵션을 선택하면 iframe이 폼을 렌더링하는 데 사용되지 않습니다.
* **높이**: 컨테이너의 높이를 지정하십시오. 컨테이너의 크기를 자동으로 조정하려면 비워 둡니다.
* **CSS 클라이언트 라이브러리**: CSS 클라이언트 라이브러리의 경로를 지정하십시오.

### Publish이 적응형 양식 - 임베드(v2) 구성 요소를 사용하여 적응형 Forms 추가  {#publish-embedded-adaptive-form}

**[!UICONTROL 적응형 양식 - 임베드(v2)]** 구성 요소를 사용하여 추가된 적응형 Forms을 게시하기 위한 다음 시나리오를 고려하십시오.

* AEM Sites 페이지를 처음 게시하면 Sites 페이지에 추가된 양식이 자동으로 게시됩니다.
* 이미 게시된 사이트 페이지에 추가된 적응형 양식을 수정하는 경우 해당 적응형 Forms을 수동으로 게시하십시오.
* Sites 페이지와 해당 적응형 Forms을 수정하면 Sites 페이지와 Sites 페이지에 추가된 모든 적응형 Forms을 다시 게시합니다.

### 적응형 양식 - 임베드(v2) 구성 요소를 사용하여 추가된 적응형 Forms 수정  {#modifying-embedded-adaptive-form}

적응형 양식의 구성 또는 속성을 수정하려면 다음 중 하나를 수행합니다.

* 각 편집기에서 적응형 양식의 원본 양식을 열고 수정합니다.
* 편집 모드로 사이트 페이지 내에서 적응형 양식을 선택한 다음 **[!UICONTROL 새 창에서 편집]**&#x200B;을 선택합니다. 원본 양식은 편집 모드에서 열리고 수정할 수 있습니다.

## AEM Sites 페이지에 추가된 적응형 양식의 레이아웃 변경 {#change-layout-af-aem-sites-page}

AEM Sites 페이지에서 [레이아웃 모드](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/sites/authoring/features/responsive-layout.html?#defining-layouts-layout-mode)를 사용하면 AEM Sites 페이지에 만들거나 추가하는 적응형 양식의 크기를 조정할 수 있습니다.

![AF 레이아웃 지원](/help/forms/assets/afsite-layoutsupport.gif)

AEM sites 페이지는 적응형 양식에 대한 참조를 유지 관리합니다. AEM Sites 페이지를 번역할 때 [번역 프로젝트](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/sites/administering/reusing-content/translation/managing-projects.html?lang=en#adding-pages-assets-to-a-translation-job)를 사용하여 적응형 양식 및 관련 참조 자산을 다른 언어로 자동으로 번역합니다.

## 모범 사례 {#best-practices}

* 원래 양식의 머리글 및 바닥글은 포함된 양식에 포함되지 않습니다.
* 포함된 양식의 사용자 초안 및 제출은 Forms 포털의 초안 및 제출된 Forms 탭에서 지원되고 볼 수 있습니다.

>[!MORELIKETHIS]
>
>* [핵심 구성 요소를 기반으로 하는 적응형 양식을 외부 웹 페이지에 포함](/help/forms/embed-adaptive-form-core-components-external-web-page.md)
>* [외부 웹 페이지에 적응형 양식 포함](/help/forms/embed-adaptive-form-external-web-page.md)