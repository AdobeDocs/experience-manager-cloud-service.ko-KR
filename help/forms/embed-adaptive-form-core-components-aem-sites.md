---
title: AEM Sites 페이지에서 적응형 양식(핵심 구성 요소) 추가
seo-title: How to add an Adaptive Form (Core Components) to an AEM Sites page?
description: AEM Sites 페이지에서 적응형 양식(핵심 구성 요소)을 사용하여 AEM Sites 페이지를 종료하지 않고 양식을 작성하고 제출할 수 있습니다.
feature: Adaptive Forms
hide: true
hidefromtoc: true
source-git-commit: 2a487654c3af2d2ec3aa43481caed5e1d4fc77a2
workflow-type: tm+mt
source-wordcount: '2185'
ht-degree: 2%

---

# AEM Sites 페이지에 적응형 Forms 추가 {#add-an-adaptive-form-to-aem-sites-page}

## 개요 {#overview}

AEM Sites 페이지에 적응형 Forms을 원활하게 작성 또는 포함하여 사용자가 사이트 페이지를 종료하지 않고 양식을 작성하고 제출할 수 있도록 할 수 있습니다. 따라서 사용자는 웹 페이지의 다른 요소 컨텍스트에 남아 있고 동시에 양식과 상호 작용할 수 있습니다.

다음 방법 중 하나를 선택하여 AEM Sites 페이지에 적응형 양식을 작성하거나 포함할 수 있습니다.

* **양식 구성 요소를 적응형 Forms 컨테이너 구성 요소로 끌어다 놓아 적응형 양식 만들기**: 를 사용하십시오 [적응형 Forms 컨테이너](#af-container-component) 구성 요소를 사용하여 적응형 양식을 호스팅하는 웹 페이지 내에 공백을 만들 수 있습니다. 이 스페이스에서 적응형 양식 구성 요소를 끌어다 놓아 양식을 만들 수 있습니다. 예를 들어 다음 비디오를 참조하여 적응형 양식을 만드는 방법을 알아보십시오 [!UICONTROL 적응형 Forms 컨테이너] 구성 요소:

>[!VIDEO](/help/forms/assets/formcreationbyadaptiveformcontainer.mp4)

다음 [적응형 양식 컨테이너](#af-container-component) 구성 요소를 사용하면 AEM Sites 편집기 내에서 바로 적응형 Forms 구성 요소를 활용하여 디지털 등록 경험을 구축할 수 있습니다. 이 통합은 AEM Sites 페이지 내에서 양식을 만들고 관리하려는 AEM Sites 작성자에게 원활한 경험을 제공합니다.

* **기존 적응형 양식 포함**: 다음 [적응형 Forms - 포함](#embed-existing-af) 구성 요소를 사용하면 기존 적응형 양식을 AEM Sites 내의 페이지에 쉽게 통합할 수 있습니다. 예를 들어 [!UICONTROL 적응형 Forms - 포함] 다음 비디오에 표시된 대로 사이트 페이지의 구성 요소:

>[!VIDEO](/help/forms/assets/embednewform_embed.mp4)

이 기능은 적응형 Forms의 적응성 및 재사용을 개선합니다. 이 통합을 통해 고객은 이미 만든 적응형 Forms을 편리하게 재사용할 수 있습니다.

* **적응형 Forms 마법사를 사용하여 양식 만들기**:

   를 사용하십시오 [적응형 Forms - 포함](#embed-new-af) 구성 요소를 사용하여 양식 만들기 마법사를 사용하여 AEM Sites 편집기 내에서 적응형 양식을 만들 수 있습니다. 양식이 외부 엔티티로 저장됩니다. 이 양식은 다른 사이트 페이지와 독립 실행형 양식에서 다시 사용할 수도 있습니다.
예를 들어 아래 비디오를 참조하여 을 사용하여 새로 만든 적응형 양식을 만들고 포함하는 방법을 알아보십시오 [!UICONTROL 적응형 Forms - 포함] 구성 요소를 생성하지 않습니다.

>[!VIDEO](/help/forms/assets/createnewform_embed.mp4)

### 고려 사항 {#considerations}

규칙 편집기를 사용하여 적응형 양식 구성 요소의 동적 동작을 추가하거나 제어할 수 있습니다. 예를 들어 구성 요소를 숨기거나 표시합니다. 비적응형 양식 구성 요소에는 규칙 편집기를 사용할 수 없습니다. 따라서 AEM Forms 컨테이너 구성 요소에서 비적응형 양식 구성 요소를 사용하는 동안 부지런함을 사용하십시오.

## 적응형 Forms 컨테이너 구성 요소를 사용하여 적응형 양식 만들기 {#af-container-component}

다음 [!UICONTROL 적응형 양식 컨테이너] 구성 요소를 사용하면 AEM Sites 편집기에서 적응형 Forms 구성 요소를 사용하여 디지털 등록 경험을 작성할 수 있습니다. 양식 구성 요소를 끌어다 놓아 적응형 양식을 만들 수 있습니다.

### 사전 요구 사항 {#prerequisites-af-container}

+++ 활성화 **[!UICONTROL 적응형 Forms 컨테이너]** 관련 템플릿의 정책에 있는 구성 요소입니다.

활성화하려면 [!UICONTROL 적응형 Forms 컨테이너] 템플릿 정책에서 구성 요소를 수행하려면 다음 단계를 수행하십시오.
1. 로 이동합니다. [!UICONTROL 페이지 정보] > [!UICONTROL 템플릿 편집]
1. 을(를) 클릭합니다. [!UICONTROL 정책] 을(를) 선택하고 을(를) 선택합니다. **핵심 구성 요소 예 - 적응형 양식** 확인란을 선택합니다.
1. 클릭 [!UICONTROL 완료].

>[!VIDEO](/help/forms/assets/adaptiveformcontainer.mp4)

+++

+++ 사이트의 페이지에 clientlibs 포함

AEM Sites 페이지에서 적응형 Forms 구성 요소를 사용하려면 AEM Archetype/Git 리포지토리 및 배포 파이프라인을 사용하여 AEM Sites 페이지에 Customerlibs 및 Customfoterlibs 클라이언트 라이브러리를 포함합니다.

1. 다음 문서를 엽니다. [AEM Forms Archetype 또는 복제된 Git 리포지토리](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html) 텍스트 편집기의 프로젝트입니다. 예를 들어 Visual Studio 코드를 사용할 수 있습니다.
1. 다음으로 이동 `ui.apps/src/main/content/jcr_root/apps/corecomponents/components/page/.content.xml`.
1. 다음 값 복사 `sling:resourceSuperType`. 예를 들어, 값은 `core/wcm/components/page/v3/page`.

   ![sling 리소스](/help/forms/assets/slingresource.png)

1. 위치에서 유사한 구조를 만듭니다 `ui.apps/src/main/content/jcr_root/apps` 다음과 같음 `core/wcm/components/page/v3/page`.

   ![오버레이 구조](/help/forms/assets/overlaystructure.png)

1. 추가 `customheaderlibs.html` 및 `customfooterlibs.html` 파일.

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

   customfoterlibs.html은 css의 JavaScript와 customerlibs.html에 사용됩니다.

1. [파이프라인 실행](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/sites/administering/site-creation/enable-front-end-pipeline.html) 를 눌러 변경 사항을 배포합니다.

+++

### 적응형 Forms 컨테이너 구성 요소를 사용하여 적응형 양식 만들기 {#create-af-using-af-container}


을 사용하여 적응형 양식을 만들려면 [!UICONTROL 적응형 Forms 컨테이너] 구성 요소:

1. 편집 모드에서 AEM Sites 페이지를 엽니다.
1. 구성 요소 브라우저 패널에서 **[!UICONTROL 적응형 Forms 컨테이너]** 구성 요소를 생성하지 않습니다.
1. 적응형 Forms 구성 요소를 사용하여 적응형 양식을 만듭니다.
1. 설정을 저장합니다.

>[!VIDEO](/help/forms/assets/af-container.mp4)

양식을 준비했습니다. AEM Sites 페이지를 게시하면 적응형 양식 및 관련 참조된 자산을 자동으로 게시합니다.

#### 적응형 양식 컨테이너 속성 구성 {#configure-additional-settings-container}

의 고급 설정을 사용자 지정할 수 있습니다 [!UICONTROL 적응형 양식 컨테이너] 구성 요소. 예를 들어 사이트의 페이지에 값이 미리 채워진 적응형 양식을 로드하도록 미리 채우기 서비스를 구성할 수 있습니다. 적응형 양식과 데이터 모델을 연결하도록 데이터 모델 설정을 구성합니다. 적응형 양식을 제출할 때 OneDrive 또는 SharePoint에 데이터를 저장하려면 제출 작업에 대한 설정을 구성합니다. 응용 Forms에 대해 사용자 지정 제출 작업을 추가할 수도 있습니다.

에 대한 속성을 설정하려면 **[!UICONTROL 적응형 Forms 컨테이너]** 구성 요소에서 ![settings_icon](/help/forms/assets/Smock_Wrench_18_N.svg) 를 클릭합니다. 다음 **[!UICONTROL 응용 Forms 컨테이너 편집]** 대화 상자가 열립니다.

![편집 대화 상자](/help/forms/assets/adaptiveformcontainer-editdialog.png)

에서 [!UICONTROL 응용 Forms 컨테이너 편집] 대화 상자에서 다음을 지정할 수 있습니다.
* **기본 탭**
   * **미리 채우기 서비스**: 미리 채우기 서비스를 사용하여 기존 데이터를 사용하여 적응형 양식의 필드를 자동으로 채울 수 있습니다. 사용자가 양식을 열면 해당 필드의 값이 미리 채워집니다. 미리 채우기 서비스에 대한 자세한 내용은 [적응형 양식 필드 미리 채우기](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-foundation-components/prepopulate-adaptive-form-fields.html#configuring-prefill-service-using-configuration-manager)
   * **클라이언트 라이브러리 카테고리**: 을(를) 지정합니다. [JavaScript 함수](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-foundation-components/add-rules-and-use-expressions-in-an-adaptive-form/rule-editor.html?lang=en#custom-functions) 표현식에서 사용되며 적응형 Forms에서 지원합니다.
* **데이터 모델**: 데이터 모델을 사용하면 서로 다른 데이터 소스의 엔티티와 서비스를 적응형 양식에 통합할 수 있습니다. 선택 **[!UICONTROL 양식 데이터 모델]** 만들려는 적응형 양식에 및 여러 데이터 소스에서 데이터를 가져오고 쓰는 작업이 포함되어 있는 경우.
   * **양식 데이터 모델**: 양식 데이터 모델을 사용하면 적응형 양식을 서로 다른 데이터 소스와 통신할 수 있습니다. 데이터 소스 구성에 대한 자세한 내용은 [데이터 소스를 구성합니다.](/help/forms/configure-data-sources.md)
   * **스키마**: 스키마는 조직의 백엔드 시스템에서 데이터를 생성하거나 사용하는 구조를 나타냅니다. 다음을 수행할 수 있습니다 [스키마를 적응형 양식에 연결](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-foundation-components/create-an-adaptive-form-on-forms-cs/adaptive-form-json-schema-form-model.html) 및 해당 요소를 사용하여 적응형 양식에 동적 콘텐츠를 추가합니다.

      >[!NOTE]
      >
      > 양식 데이터 모델을 구성한 후에는 연결된 양식 모델을 변경할 수 없습니다. 그러나 양식 데이터 모델과 연결된 스키마를 수정할 수 있습니다.

* **전송 탭**

   * **URL로 리디렉션**

      **리디렉션 URL/경로**: 제출 작업 후 적응형 양식을 리디렉션할 URL 또는 경로를 지정합니다.

      **작업 제출**: 사용자가 적응형 양식에서 제출 단추를 클릭하면 제출 작업이 트리거됩니다. 다음을 수행할 수 있습니다 [적응형 양식에서 제출 작업 구성](/help/forms/configuring-submit-actions.md). 적응형 양식은 즉시 제출 작업을 제공합니다.
      * REST 엔드포인트에 제출
      * 이메일 보내기
      * 양식 데이터 모델을 사용하여 제출
      * AEM 워크플로우 호출
      * SharePoint에 제출
      * OneDrive에 제출
      * Azure Blob 스토리지에 제출

   다음을 수행할 수도 있습니다 [기본 제출 작업 확장](custom-submit-action-form.md) 를 입력하여 고유한 사용자 지정 제출 작업을 만들 수 있습니다.

* **메시지 표시**
   * **메시지 콘텐츠**: 서식 있는 텍스트 편집기를 사용하여 메시지를 작성하여 양식 제출 시 표시할 수 있습니다. 이 옵션은 감사 메시지를 표시하도록 선택하는 경우에만 사용할 수 있습니다.

## 기존 적응형 양식 포함  {#aem-container-component}

사용 **[!UICONTROL 적응형 Forms - 포함]** 구성 요소로 새 적응형 양식을 포함하거나 사이트의 페이지에 기존 적응형 양식을 포함할 수 있습니다. 다음 [!UICONTROL 적응형 Forms - 포함] 구성 요소로 다음을 수행할 수 있습니다.

* [기존 적응형 양식 포함](#embed-new-af)

* [새 적응형 양식 만들기 및 포함](#embed-existing-af)

### 사전 요구 사항 {#prerequisites}

+++ 를 활성화합니다 **적응형 Forms - 포함** 관련 템플릿의 정책에 있는 구성 요소입니다.

활성화하려면 [!UICONTROL 적응형 Forms - 포함] 템플릿 정책에서 구성 요소를 수행하려면 다음 단계를 수행하십시오.
1. 로 이동합니다. [!UICONTROL 페이지 정보] > [!UICONTROL 템플릿 편집]
1. 을(를) 클릭합니다. [!UICONTROL 정책] 을(를) 선택하고 을(를) 선택합니다. **핵심 컨텐츠** 확인란을 선택합니다.
1. 클릭 [!UICONTROL 완료].

>[!VIDEO](/help/forms/assets/enableadaptiveform-embedtemplate.mp4)

+++

+++ 사이트의 페이지에 clientlibs 포함

이 **[!UICONTROL 양식에서 페이지의 전체 너비를 다룹니다.]** 옵션이 **[!UICONTROL 양식 컨테이너]** 대화 상자 구성 및 **핵심 구성 요소를 사용하는 적응형 Forms** 를 사용하는 경우 해당 사이트의 페이지에 clientlibs를 포함해야 합니다.

![오버레이 Gif](/help/forms/assets/overlaycorecomponent.gif)

AEM Sites 페이지에서 적응형 Forms 구성 요소를 사용하려면 AEM Archetype/Git 리포지토리 및 배포 파이프라인을 사용하여 AEM Sites 페이지에 Customerlibs 및 Customfoterlibs 클라이언트 라이브러리를 포함합니다.

1. 다음 문서를 엽니다. [AEM Forms Archetype 또는 복제된 Git 리포지토리](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html) 텍스트 편집기의 프로젝트입니다. 예를 들어 Visual Studio 코드를 사용할 수 있습니다.
1. 다음으로 이동 `ui.apps/src/main/content/jcr_root/apps/corecomponents/components/page/.content.xml`.
1. 다음 값 복사 `sling:resourceSuperType`. 예를 들어, 값은 `core/wcm/components/page/v3/page`.

   ![sling 리소스](/help/forms/assets/slingresource.png)

1. 위치에서 유사한 구조를 만듭니다 `ui.apps/src/main/content/jcr_root/apps` 다음과 같음 `core/wcm/components/page/v3/page`.

   ![오버레이 구조](/help/forms/assets/overlaystructure.png)

1. 추가 `customheaderlibs.html` 및 `customfooterlibs.html` 파일.

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

   customfoterlibs.html은 CSS의 JavaScript와 customerlibs.html에 사용됩니다.

1. [파이프라인 실행](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/sites/administering/site-creation/enable-front-end-pipeline.html) 를 눌러 변경 사항을 배포합니다.

+++

### 새 적응형 양식 포함 {#embed-new-af}

1. 편집 모드에서 AEM Sites 페이지를 엽니다.
1. 구성 요소 브라우저 패널에서 [!UICONTROL 적응형 Forms - 포함] 구성 요소를 생성하지 않습니다.
1. 을(를) 클릭합니다. **플러스** 아이콘을 클릭하면 양식 만들기 마법사로 리디렉션됩니다.

   ![응용 Forms - 포함 구성 요소](/help/forms/assets/aemformcontainer.png)

1. 에서 새 적응형 양식 만들기 [!UICONTROL 양식 만들기] 마법사
1. 다음 [!UICONTROL 자산 경로] 이미 만든 적응형 양식의 경로가 포함되어 있습니다
1. 설정을 저장합니다. 이제 적응형 양식이 페이지에 포함됩니다.

### 기존 적응형 양식 포함 {#embed-existing-af}

1. 편집 모드에서 AEM Sites 페이지를 엽니다.
1. 구성 요소 브라우저 패널에서 [!UICONTROL 적응형 Forms - 포함] 구성 요소를 생성하지 않습니다.
1. 탭하기 [!UICONTROL 적응형 Forms - 포함] [사이트] 페이지의 구성 요소를 탭하고 ![settings_icon](/help/forms/assets/Smock_Wrench_18_N.svg) 를 클릭합니다. 다음 **[!UICONTROL 적응형 Forms 편집 - 포함]** 대화 상자가 열립니다.
1. 에 포함할 적응형 양식을 찾아 선택합니다 [!UICONTROL 자산 경로].
1. 설정을 저장합니다. 이제 적응형 양식이 페이지에 포함됩니다.

#### 적응형 양식 포함 속성 구성

의 고급 설정을 사용자 지정할 수 있습니다 [!UICONTROL 적응형 양식 - 포함] 구성 요소. 에서 [!UICONTROL 적응형 Forms 편집 - 포함] 대화 상자에서 다음을 지정할 수 있습니다.
* **자산 경로**: 포함할 적응형 양식을 찾아 선택합니다. 자산 브라우저에서 삭제한 경우 자동으로 채워집니다.
* **게시 제출** : 양식 제출 시 트리거할 작업을 선택합니다. 감사 메시지를 표시하거나 감사 인사 페이지를 표시하도록 선택할 수 있습니다.
   * **감사 메시지 표시**: 서식 있는 텍스트 편집기를 사용하여 메시지를 작성하여 양식 제출 시 표시할 수 있습니다. 이 옵션은 감사 메시지를 표시하도록 선택하는 경우에만 사용할 수 있습니다.
   * **감사 인사 페이지 표시**: 양식 제출 시 표시할 페이지를 찾아 선택합니다. 이 옵션은 감사 인사 페이지를 표시하도록 선택하는 경우에만 사용할 수 있습니다.
   * **감사 인사 페이지로 리디렉션**: 포함된 적응형 양식이 포함된 페이지를 감사 인사 페이지로 대체하려면 옵션을 활성화합니다. 그렇지 않으면 감사 인사 페이지에서 의 적응형 양식을 [!UICONTROL 적응형 Forms - 포함] 구성 요소를 생성하지 않고 페이지에서 기본 사이트를 새로 고치지 않습니다. 이 옵션은 감사 인사 페이지를 표시하도록 선택하는 경우에만 사용할 수 있습니다.
* **페이지 언어 사용**: 적응형 양식 대신 AEM Sites 페이지의 로컬 로케일을 사용합니다.
* **양식에 포커스 설정**: 을(를) 선택하여 적응형 양식의 첫 번째 필드에 초점을 둡니다.
* **양식은 프레임의 전체 너비를 포함합니다**: 이 확인란을 선택하면 iframe이 양식을 렌더링하는 데 사용되지 않습니다.
* **높이**: 컨테이너의 높이를 지정합니다. 컨테이너의 크기를 자동으로 조정하려면 이 필드를 비워 둡니다.
* **CSS 클라이언트 라이브러리**: CSS 클라이언트 라이브러리의 경로를 지정합니다.

### 포함된 적응형 양식 게시 {#publishing-embedded-adaptive-form}

AEM Sites 페이지에 포함된 적응형 양식을 게시하기 위한 다음 시나리오를 생각해 보겠습니다.

* AEM 사이트 페이지를 처음으로 게시하고 포함된 적응형 양식이 포함된 경우 사이트 페이지와 포함된 자산을 게시합니다.
* 게시된 사이트 페이지에서 포함된 적응형 양식만 수정한 경우 원래 자산을 게시하고 변경 사항이 게시된 사이트 페이지에 반영됩니다. 게시된 사이트 페이지에는 자산에 대한 참조가 포함되어 있으며 페이지를 다시 게시할 필요가 없습니다.
* 사이트 페이지 및 포함된 적응형 양식 을 수정한 경우 사이트 페이지와 포함된 자산을 다시 게시합니다.

### 포함된 적응형 양식 수정  {#modifying-embedded-adaptive-form}

포함된 적응형 양식의 구성이나 속성을 수정하려면 다음 중 하나를 수행합니다.

* 각 편집기에서 적응형 양식으로 원래 양식을 열고 수정합니다.
* 편집 모드의 사이트 페이지 내에서 적응형 양식을 탭한 다음 탭합니다 **[!UICONTROL 새 창에서 편집]**. 원본 양식은 수정할 수 있는 편집 모드로 열립니다.

>[!NOTE]
>
>원래 적응형 양식에서 변경한 내용은 포함된 양식에 자동으로 반영됩니다. 하지만 게시된 페이지의 변경 사항을 반영하도록 적응형 양식 또는 사이트의 페이지를 다시 게시합니다.

### 우수 사례 {#best-practices}

* 원본 양식의 머리글 및 바닥글은 포함된 양식에 포함되지 않습니다.
* 포함된 양식의 사용자 초안 및 제출 문서가 Forms 포털의 초안 및 제출된 Forms 탭에서 지원되고 표시됩니다.

[AEM Sites 페이지에서 레이아웃 모드](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/sites/authoring/features/responsive-layout.html?#defining-layouts-layout-mode) AEM 사이트의 페이지 내에 만들거나 포함된 적응형 양식의 크기를 조정할 수 있습니다.

![AF 레이아웃 지원](/help/forms/assets/afsite-layoutsupport.gif)

AEM 사이트 페이지는 적응형 양식에 대한 참조를 유지 관리합니다. AEM Sites 페이지를 번역하면 자동으로 적응형 양식 및 관련 참조된 자산을 [번역 프로젝트](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/sites/administering/reusing-content/translation/managing-projects.html?lang=en#adding-pages-assets-to-a-translation-job) 다른 언어로 변환해야 합니다.

