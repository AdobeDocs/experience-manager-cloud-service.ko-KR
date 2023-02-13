---
title: 적응형 양식 템플릿을 만드는 방법
description: 적응형 양식 템플릿을 만들어 템플릿 편집기를 사용하여 기본 구조 및 초기 컨텐츠를 정의합니다.
exl-id: a882cba2-c621-4ff7-a972-c504641b5639
source-git-commit: fce9900a1979875fc725318a6cd735341d0b6275
workflow-type: tm+mt
source-wordcount: '2017'
ht-degree: 1%

---

# 적응형 양식 템플릿 만들기 {#adaptive-form-templates}

양식을 작성할 때는 필드 및 구성 요소를 추가하여 편집기에서 양식 구조, 컨텐츠 및 작업을 정의합니다. 에서 필드 및 구성 요소를 추가합니다 `guideRootPanel` 섹션에 있는 마지막 항목이 될 필요가 없습니다. 템플릿 편집기를 사용하면 작성자가 양식을 만드는 데 사용할 수 있는 기본 구조와 초기 컨텐츠가 포함된 템플릿을 만들 수 있습니다.

예를 들어, 모든 양식 작성자가 등록 양식에 특정 텍스트 상자, 탐색 단추 및 제출 단추를 포함하도록 할 수 있습니다. 작성자가 다른 등록 양식과 일치하는 양식을 만드는 데 사용할 수 있는 구성 요소를 사용하여 템플릿을 만들 수 있습니다. 작성자가 템플릿을 사용하여 적응형 양식을 만들면 새 양식은 템플릿에서 지정한 구조 및 구성 요소를 상속받습니다. 템플릿 편집기를 사용하면 다음 작업을 수행할 수 있습니다.

* 양식의 머리글 및 바닥글 구성 요소를 구조 레이어에 추가합니다.
* 양식의 초기 컨텐츠를 제공합니다.
* 테마, 작업 제출 을 지정합니다.

다운로드하여 설치할 수 있습니다 [!DNL AEM Forms] 다음에서 컨텐츠 패키지 참조 [소프트웨어 배포](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html) 참조 테마 및 템플릿을 환경에 가져오기 위한 포털입니다.

## 템플릿 작업 {#working-with-templates}

도구 메뉴에서 로 이동하여 템플릿 편집기에 액세스할 수 있습니다 **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL 도구]** > **[!UICONTROL 일반]** > **[!UICONTROL 템플릿]**. 여기서는 편집 가능한 템플릿에 대해 사용 가능한 폴더에 템플릿을 구성합니다.

Experience Manager은 템플릿을 구성하는 전역 폴더를 제공합니다. 그러나 기본적으로 활성화되어 있지 않습니다. 관리자에게 전역 폴더를 활성화하거나 템플릿에 대한 폴더를 만들도록 요청할 수 있습니다. 폴더를 만드는 방법에 대한 자세한 내용은 [템플릿 폴더](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/sites/authoring/features/templates.html#editing-templates-template-authors).

### 템플릿 만들기 {#create-template}

폴더를 만든 후 폴더를 열고 다음 단계를 수행하여 템플릿을 만듭니다.

1. 탭 **[!UICONTROL 만들기]** 만든 폴더 안에 있습니다.
1. 템플릿 유형 선택 섹션에서 **[!UICONTROL 적응형 양식 템플릿]** 탭 **[!UICONTROL 다음]**.

1. 템플릿 세부 사항 섹션에서 템플릿 제목을 제공하고 **[!UICONTROL 만들기]**.
설명을 제공할 수도 있습니다.

1. 탭 **[!UICONTROL 완료]** 콘솔로 돌아가거나 **[!UICONTROL 열기]** 를 클릭하여 편집기에서 템플릿을 엽니다.

### 템플릿 편집기 UI {#template-editor-ui}

편집할 템플릿을 열면 다음 AEM Editor 구성 요소를 볼 수 있습니다.

* **페이지 도구 모음**
다음 옵션을 포함합니다.

   * **사이드 패널 전환**: 사이드바를 표시하거나 숨길 수 있습니다.
   * **페이지 정보**: 게시/게시 취소 시간, 축소판, 클라이언트측 라이브러리, 페이지 정책 및 페이지 디자인 클라이언트측 라이브러리와 같은 정보를 지정할 수 있습니다.

   <!-- * **Emulator**: Lets you simulate and customize the look for different devices.-->
   * **모드 선택기:** 모드를 변경할 수 있습니다. **[!UICONTROL 구조]** 모드, **[!UICONTROL 초기 컨텐츠]**, **[!UICONTROL 레이아웃 컨트롤]** 모드. 구조 모드에서 머리글 및 바닥글을 추가하고 사용자 지정할 수 있습니다. 초기 컨텐츠 모드에서는 양식 컨텐츠를 사용자 지정할 수 있습니다.
   * **미리 보기:** 게시할 때 템플릿이 어떻게 보이는지 미리 볼 수 있습니다. 레이어 선택기 및 미리 보기 를 사용하여 편집 및 미리 보기 모드를 전환할 수 있습니다.
* **사이드바:** 컨텐츠, 속성, 자산 및 구성 요소 브라우저를 제공합니다.
* **구성 요소 도구 모음:** 구성 요소를 선택하면 구성 요소를 사용자 지정할 수 있는 도구 모음이 표시됩니다.
* **페이지**: 템플릿을 만들 콘텐츠를 추가하는 영역입니다.

<!-- See [Introduction to authoring Adaptive Forms](introduction-forms-authoring.md) to understand the Touch UI editor. -->

### 템플릿 편집 {#editing-a-template}

적응형 양식 템플릿은 다음 두 개의 계층을 사용하여 만듭니다.

* 구조
* 초기 콘텐츠

레이어 선택기는 화면의 오른쪽 상단 모서리에 있는 [미리 보기] 옵션 옆에 있습니다.

### 구조 {#structure}

템플릿 편집기에서 구조 레이어를 선택하면 적응형 양식 컨테이너 위아래에 레이아웃 컨테이너가 표시됩니다. 작성자는 머리글 및 바닥글에 이러한 레이아웃 컨테이너를 사용할 수 있습니다. 머리글 및 바닥글을 추가, 편집 또는 사용자 지정할 수 있습니다. 적응형 양식 컨테이너 위의 레이아웃 컨테이너에 있는 적응형 양식 헤더 구성 요소를 드래그하여 템플릿 헤더를 사용자 지정합니다. 적응형 양식 컨테이너 아래의 레이아웃 컨테이너에서 적응형 양식 바닥글 구성 요소를 드래그하여 템플릿 바닥글을 사용자 지정합니다.

![구조 레이어의 레이아웃 컨테이너](assets/header-layer-selector.png)

구조 레이어의 레이아웃 컨테이너

**A.** 헤더 구성 요소의 레이아웃 컨테이너 **B.** 바닥글 구성 요소의 레이아웃 컨테이너

적응형 양식 컨테이너 위의 레이아웃 컨테이너에 있는 적응형 양식 헤더 구성 요소를 드래그하여 놓습니다. 구성 요소를 추가한 후 로고를 추가하고 해당 제목을 제공할 수 있는 속성을 지정할 수 있습니다.

마찬가지로 적응형 양식 컨테이너 아래의 레이아웃 컨테이너에서 바닥글 구성 요소를 드래그하여 놓으면 저작권 정보와 회사 세부 사항을 제공할 수 있습니다.

![구조 레이어에 머리글 및 바닥글 추가](assets/header-and-footer.png)

구조 레이어에 머리글 및 바닥글 추가

#### 구조 레이어의 구성 요소 잠금/잠금 해제 {#locking-unlocking-components-in-the-structure-layer}

구조 레이어를 선택한 상태로 템플릿을 편집할 때 템플릿의 머리글 및 바닥글의 잠금을 해제할 수 있습니다. 템플릿에서 구성 요소 잠금이 해제된 경우 양식 작성자는 템플릿을 사용하는 적응형 양식에서 구성 요소를 편집할 수 있습니다. 구성 요소를 잠그면 양식 작성자가 적응형 양식에서 해당 구성 요소를 편집할 수 없습니다. 잠금 옵션은 구성 요소 도구 모음에서 사용할 수 있습니다.

예를 들어 템플릿에 헤더 구성 요소를 추가합니다. 구성 요소를 선택하면 구성 요소 도구 모음에 잠금 옵션이 표시됩니다. 일반적으로 헤더에 회사 이름과 로고가 포함되며, 양식 작성자가 템플릿의 로고와 헤더를 변경하지 않도록 합니다. 헤더 구성 요소가 잠긴 템플릿을 사용하여 만든 적응형 양식에서는 양식 작성자가 로고와 회사 이름을 변경할 수 없습니다.

>[!NOTE]
>
>헤더 구성 요소에서 이미지 또는 로고를 개별적으로 잠금 또는 잠금 해제할 수는 없습니다. 헤더 구성 요소의 잠금을 해제할 수 있습니다.

### 초기 콘텐츠 {#initial-content}

초기 컨텐츠 옵션을 선택하면 템플릿의 적응형 양식 컨테이너가 편집을 위한 적응형 양식과 같이 열립니다. 적응형 양식 작성과 마찬가지로 테마 선택 및 작업 제출과 같은 초기 설정을 지정할 수 있습니다.

양식 작성자는 양식을 만들기 위한 기반으로 사용합니다. 컨텐츠 흐름 구조는 템플릿의 초기 컨텐츠 레이어에 지정됩니다. 양식 템플릿의 초기 컨텐츠 편집으로 전환하려면 페이지 도구 모음에서 미리 보기 를 누른 다음 ![캔버스 드롭다운](assets/canvas-drop-down.png) **>** **[!UICONTROL 초기 컨텐츠]**.


초기 컨텐츠 레이어에서 작성자가 기반으로 사용하는 적응형 양식 템플릿을 만듭니다. 템플릿 작성은 양식 작성과 유사하며, 사이드바에서 사용할 수 있는 옵션을 사용합니다. 사이드바는 컨텐츠, 속성, 자산 및 구성 요소 브라우저를 제공합니다.

<!-- See [Sidebar](introduction-forms-authoring.md#sidebar). -->

>[!NOTE]
>
>컨텐츠 저장 또는 StorePDF를 제출 작업으로 선택하면 저장 경로를 지정하는 옵션이 제공됩니다. 템플릿에 경로를 지정하면 템플릿에서 만든 모든 양식의 경로가 동일합니다. 올바른 저장소 경로를 지정하거나 양식 작성자가 업데이트하여 모든 양식이 동일한 위치에 저장되지 않도록 할 수 있습니다.

#### 탭 및 패널을 사용하여 적응형 양식 템플릿 만들기 {#creating-an-adaptive-form-template-with-tabs-and-panels-nbsp}

예를 들어 다음 탭으로 템플릿을 만들 수 있습니다.

* 일반 정보
* 전문 정보

로고를 추가하고 제목을 제공하고 구조 레이어에 바닥글을 추가했습니다. 양식 작성자가 템플릿을 사용하여 양식을 만들 때 양식 머리글 및 바닥글을 편집하지 못하도록 합니다.

레이어를 구조(Structure)에서 초기 컨텐츠(Initial Content)로 변경하고 양식에 컨텐츠를 추가합니다. 탭 구조를 만들려면 적응형 양식 컨테이너의 guideRootPanel에 하위 패널을 추가합니다. 패널을 추가하려면 다음을 수행하십시오.

* 을 탭하여 패널을 추가할 수 있습니다 **[!UICONTROL +]** 버튼을 선택하면 **[!UICONTROL 구성 요소를 여기로 드래그하십시오]** 선택 사항입니다.

* 사이드바의 구성 요소 브라우저에서 패널 구성 요소를 드래그하여 놓을 수 있습니다.
* 의 하위 패널을 추가할 수 있습니다 `guideRootPanel` 구성 요소 도구 모음에서 를 클릭합니다.

일반 정보 및 전문 정보 탭을 만들려면 `guideRootPanel`. 패널을 선택하고 탭합니다 ![cmppr](assets/configure-icon.svg) 를 클릭하여 사이드바에서 속성을 엽니다. 요소 이름을 `general-info` 및 `professional-info`및 제목으로 각각 일반 정보 및 전문 정보. 사이드바에서 컨텐츠를 탭하여 컨텐츠 브라우저를 엽니다. 양식 객체 탭에서 `guideRootPanel`. 편집기에서 guideRootPanel 이 선택됩니다. 탭 ![cmppr](assets/configure-icon.svg) 구성 요소 도구 모음에서 해당 속성을 엽니다. 패널 레이아웃 필드에서 **[!UICONTROL 맨 위에 있는 탭]** 탭 **[!UICONTROL 완료]**. 탭 템플릿 구조가 적용됩니다.

#### 탭에서 컨텐츠 추가 {#adding-content-in-tabs}

패널을 추가하고 탭으로 구조화한 후 탭 내에 필드를 추가할 수 있습니다. 편집기에서 탭을 선택하면 **[!UICONTROL 구성 요소를 여기로 드래그하십시오]** 선택 사항입니다. 텍스트 상자, 목록 항목 및 단추와 같은 구성 요소를 드래그하여 놓을 수 있습니다. 사이드바의 구성 요소 브라우저에서 구성 요소를 드래그하여 놓을 수 있습니다.

각 구성 요소에는 데이터 캡처 및 조작을 향상시키는 속성이 있습니다. 예를 들어 **[!UICONTROL 필수 필드]** 구성 요소의 속성입니다. 작성자는 고객이 필수 필드 채우기를 건너뛸 때 표시되는 메시지를 지정할 수 있습니다. 메시지를 **[!UICONTROL 필수 필드 메시지]** 속성을 사용합니다.

예제 템플릿의 이름, 전화 번호 및 생년월일 필드가 일반 정보 탭에 추가됩니다. Professional Information 탭에서 현재 고용된 사람, 고용 유형, 교육 자격 필드가 추가됩니다.

필드를 추가한 후 제출 및 재설정 등의 단추를 추가할 수 있습니다.

### 템플릿 활성화 {#enabling-the-template}

템플릿을 만들면 초안으로 추가됩니다. 템플릿을 활성화하여 적응형 Forms 만들기에 사용할 수 있습니다. 템플릿을 활성화하려면

1. 다음으로 이동 **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL 도구]** > **[!UICONTROL 템플릿]**&#x200B;을 클릭하고 템플릿을 만든 폴더를 엽니다.

1. 작성한 템플릿이 초안으로 표시됩니다.
1. 템플릿을 선택하고 탭합니다 **[!UICONTROL 활성화]** 클릭합니다.
적응형 양식을 만들 때 템플릿을 선택하라는 메시지가 표시되면 나열된 템플릿을 볼 수 있습니다.

## 템플릿 가져오기 또는 내보내기 {#importing-or-exporting-a-template}

양식은 해당 템플릿에서 작동합니다. 사용자 지정된 템플릿을 사용하여 만든 적응형 양식을 다운로드하면 템플릿이 다운로드되지 않습니다. 다른 형식으로 양식을 가져올 때 [!DNL AEM Forms] 예를 들어 템플릿 없이 가져옵니다. 양식을 가져오지만 해당 템플릿을 사용할 수 없으면 양식이 렌더링되지 않습니다. 에서 사용자 지정 템플릿을 패키지할 수 있습니다. `/conf` 노드 `https://<server>:<port>/crx/packmgr`를 입력하여 [!DNL AEM Forms] 양식을 업로드할 인스턴스. 다음을 수행할 수도 있습니다 [AEM Archetype을 사용하여 템플릿을 만들고 Cloud Services 인스턴스에 배포합니다](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-wknd-tutorial-develop/pages-templates.html#prerequisites).

>[!NOTE]
>
> * 를 구성할 수도 있습니다 [!UICONTROL 기록 문서] 적응형 양식 편집기 또는 적응형 양식 템플릿 편집기에서 바로 템플릿을 생성할 수 있습니다. 자세한 내용은 [적응형 Forms에 대한 기록 문서 생성](/help/forms/generate-document-of-record-for-non-xfa-based-adaptive-forms.md#document-of-record-support-in-adaptive-form-editor-dor-support-in-adaptiveform).



### 양식 데이터 모델 스키마를 템플릿에 연결 {#associating-form-data-model-schema-in-template}

작성자가 [!UICONTROL 양식 데이터 모델 스키마] 추가 정보 작성자는 템플릿 편집기에서 스키마를 선택할 수 있습니다. 스키마를 템플릿에 연결하고 양식 작성자가 템플릿을 기반으로 양식을 만들면 해당 스키마에 대해 스키마가 미리 선택됩니다. 양식 작성자가 스키마 사용을 규제하고 양식 작성자를 위한 시간도 절약할 수 있습니다. 템플릿 편집기에서 양식 데이터 모델 스키마를 선택하려면 다음을 수행합니다.

1. 탭 **[!UICONTROL 컨텐츠 브라우저]** 왼쪽에 있습니다.
1. 양식 컨테이너로 이동합니다. **[!UICONTROL 설정]**.
1. 선택 **[!UICONTROL 데이터 모델]**.
1. 을 통해 양식 데이터 모델 선택 **[!UICONTROL 양식 데이터 모델 선택]** 구성을 저장합니다.

![Form-Data-Model-Association-in-Forms](/help/forms/assets/select-form-data-model-img.png)



## 템플릿을 사용하여 적응형 양식 만들기 {#creating-an-adaptive-form-using-the-template}

템플릿을 만들고 활성화하면 적응형 양식을 만들 때 양식 관리자에서 사용할 수 있습니다. 템플릿을 사용하고 적응형 양식을 만들려면 다음을 참조하십시오 [적응형 양식 만들기](creating-adaptive-form.md).


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
    * To show or hide out of the box Adaptive Form templates that were added in AEM 6.0 Forms or AEM 6.1 Forms releases but are now deprecated, check or uncheck the **Include AEM 6.0 AF Templates** option. If this option is checked, in order to take effect, it requires the **Include Out of the box AF and AD Templates** configuration to be enabled.

1. Click **Save**. The display options for the out of the box templates are changed. -->

## 적응형 양식을 템플릿으로 저장 {#saving-adaptive-form-as-template}

나중에 사용할 수 있도록 적응형 양식을 템플릿으로 저장할 수도 있습니다. 적응형 양식을 템플릿으로 저장하려면 다음을 수행합니다.

1. 적응형 양식을 선택하여 템플릿으로 저장합니다.
1. 클릭 **[!UICONTROL 템플릿으로 저장]**. 대화 상자가 나타납니다.
1. 지정 **[!UICONTROL 제목]** (필수 필드), **[!UICONTROL 위치]** (필수 필드) 및 **[!UICONTROL 설명]** (선택 사항 필드) 를 포함할 수 없습니다.
1. **[!UICONTROL 만들기]**&#x200B;를 클릭합니다.

   ![양식으로 저장](/help/forms/assets/saveformastemplate.png)



>[!NOTE]
>
>소스 적응형 양식과 동일한 컨테이너 정책을 사용하려면 소스 적응형 양식과 동일한 폴더에 템플릿을 저장하는 것이 좋습니다. 생성된 템플릿이 기본 컨테이너 정책을 사용하는 경우를 제외하고 템플릿이 다른 폴더에 저장되는 경우가 있습니다.

## 권장 사항 {#recommendations}

* 템플릿 편집기에서 폼의 속성을 수정할 때는 BindReference 속성을 사용하지 마십시오.
* 중단점을 추가하려면 적응형 양식 템플릿을 작성할 때 만듭니다.
중단점에 대한 자세한 내용은 [응답형 레이아웃](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/sites/authoring/features/responsive-layout.html#authoring).
