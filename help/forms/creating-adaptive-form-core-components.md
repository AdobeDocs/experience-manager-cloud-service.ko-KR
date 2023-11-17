---
title: 핵심 구성 요소를 기반으로 적응형 양식을 만드는 방법
description: 을 사용하여 적응형 양식을 만드는 방법 알아보기 [!DNL Experience Manager Forms]. 적응형 Forms은 정보 수집 및 처리를 간소화하는 반응형 HTML 5 양식입니다. 양식 데이터 모델 및 XML 또는 JSON 스키마를 기반으로 적응형 양식을 만드는 방법에 대해 자세히 알아보십시오.
feature: Adaptive Forms, Core Components
role: User, Developer
level: Beginner
exl-id: 1e812d93-4ba5-4589-b59b-2f564d754b0f
source-git-commit: e2505c0fec1da8395930f131bfc55e1e2ce05881
workflow-type: tm+mt
source-wordcount: '2301'
ht-degree: 65%

---

# 적응형 양식 만들기 {#creating-an-adaptive-form-core-components}

| 버전 | 문서 링크 |
| -------- | ---------------------------- |
| AEM 6.5 | [여기 클릭](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-core-components/create-an-adaptive-form-core-components.html) |
| AEM as a Cloud Service | 이 문서 |


적응형 양식을 사용하면 멋지고, 반응이 빠르고, 동적이고, 적응력이 뛰어난 양식을 만들 수 있습니다. AEM Forms는 적응형 양식을 신속하게 만들 수 있는 비즈니스 사용자 친화적 마법사를 제공합니다. 마법사에는 미리 구성된 템플릿, 스타일, 필드 및 제출 옵션을 손쉽게 선택하여 적응형 양식을 만들 수 있는 빠른 탭 탐색 기능이 있습니다.

시작하기 전에 사용할 수 있는 Forms 구성 요소 유형에 대해 알아봅니다.

* [적응형 양식 핵심 구성 요소](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html?lang=ko): 표준화된 데이터 캡처 구성 요소입니다. 이 구성 요소는 맞춤화 기능을 제공하고, 개발 시간을 단축하고, 유지 관리 비용을 줄여 디지털 등록 경험을 개선합니다. 개발자는 이러한 구성 요소를 손쉽게 사용자 정의하고 스타일링할 수 있습니다. Adobe은 이러한 현대적이고 확장 가능한 구성 요소를 활용하여 적응형 Forms을 개발할 것을 권장합니다.

* [적응형 양식 기초 구성 요소](creating-adaptive-form.md): 클래식(이전) 데이터 캡처 구성 요소입니다. 이를 계속 사용하여 기존의 기초 구성 요소 기반 적응형 양식을 편집할 수 있습니다. 새 양식을 만드는 경우 [](creating-adaptive-form-core-components.md)적응형 양식을 만드는 적응형 양식 핵심 구성 요소를 사용하는 것이 좋습니다.

![적응형 양식 만들기 마법사](/help/release-notes/assets/wizard.png)


## 전제 조건

적응형 양식을 만들려면 다음이 필요합니다.

* **환경에 맞는 적응형 Forms 핵심 구성 요소 활성화**: 프로그램을 만들 때 환경에 대한 적응형 Forms 핵심 구성 요소가 이미 활성화되었습니다. Archetype 39 또는 이전 버전을 기반으로 하는 Forms as a Cloud Service 환경을 이용하는 경우, [해당 환경에 대해 적응형 양식 핵심 구성 요소를 활성화](enable-adaptive-forms-core-components.md)하십시오. 환경에 대해 핵심 구성 요소를 활성화하면 **적응형 양식 (핵심 구성 요소)** 템플릿 및 캔버스 테마가 해당 환경에 추가됩니다. 적응형 양식 핵심 구성 요소는 2023.02.0 릴리스 이전의 프리릴리스 일부로 제공되었으므로 사용 중인 AEM SDK 버전이 2023.02.0 이전 버전이라면 [해당 환경에서 `prerelease` 플래그가 활성화](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/release-notes/prerelease.html?lang=ko#new-features)되어 있어야 합니다.

* **적응형 양식 템플릿**: 템플릿은 기본 구조를 제공하고 적응형 양식의 모양(레이아웃 및 스타일)을 정의합니다. 특정 속성과 콘텐츠 구조를 포함하는 서식이 미리 지정된 구성 요소가 있습니다. 또한 테마와 제출 액션을 정의하는 옵션이 제공됩니다. 테마는 모양과 느낌을 정의하고 제출 액션은 적응형 양식 제출 시 수행할 작업을 정의합니다. 예: 수집된 데이터를 데이터 소스로 보내기. 클라우드 서비스는 blank라는 OOTB 템플릿을 제공합니다.

   * `blank` 템플릿은 새로운 모든 AEM Forms as a Cloud Service 프로그램에 포함됩니다.
   * 패키지 관리자를 통해 참조 패키지를 설치하여 `blank` 템플릿을 AEM Forms as a Cloud Service 프로그램에 추가할 수 있습니다.
   * 다음을 수행할 수도 있습니다. [적응형 Forms 템플릿(핵심 구성 요소) 만들기](/help/forms/template-editor-core-components.md) 처음부터.
   * 를 배포할 수도 있습니다 [샘플 템플릿](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/sample-themes-templates-form-data-models-core-components.html) 을 참조하십시오. 이렇게 하면 양식을 신속하게 만들 수 있습니다.

* **적응형 양식 테마**: 테마에 구성 요소 및 패널에 대한 스타일링 세부 정보가 포함됩니다. 스타일에는 배경색, 상태 색상, 투명도, 정렬과 크기와 같은 속성이 포함됩니다. 테마를 적용하면 지정된 스타일은 해당 구성 요소에 반영됩니다.  `Canvas` 템플릿은 새로운 모든 AEM Forms as a Cloud Service 프로그램에 포함됩니다. 를 배포할 수도 있습니다 [샘플 테마](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/sample-themes-templates-form-data-models-core-components.html) 을 참조하십시오. 이를 통해 양식의 스타일을 시작하고 비즈니스 요구 사항에 따라 테마를 만들거나 맞춤화할 수 있는 기본 구조를 제공할 수 있습니다.

  <!-- * You can install the reference package, via package manager, to add the `Canvas` template to your AEM Forms as a Cloud Service program.
    * You can also [create an Adaptive Forms theme (Core Components)](template-editor.md) and deploy it to your AEM Forms as a Cloud Service program. -->

* **권한**: 사용자를 [!DNL forms-users] 그룹에 추가합니다. [!DNL forms-users] 그룹의 멤버는 적응형 양식을 만들 수 있는 권한이 있습니다. 양식별 사용자 그룹에 대한 세부 목록은 [그룹 및 권한](forms-groups-privileges-tasks.md)을 참조하십시오.

<!--
>[!NOTE]
>
>
> In addition to the given themes and templates when you enable Core Components, you can also deploy the latest out-of-the box [sample themes and templates](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/sample-themes-templates-form-data-models-core-components.html) to your AEM environment for use in Core Components based Adaptive Forms.
-->

## 적응형 양식 만들기  {#create-an-adaptive-form-core-components}

1. [!DNL Experience Manager Forms] 작성자 인스턴스에 로그인합니다. 클라우드 인스턴스 또는 로컬 개발 인스턴스일 수 있습니다.

1. Experience Manager 로그인 페이지에서 자격 증명을 입력합니다. 로그인한 후 왼쪽 상단에서 **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL 양식]** > **[!UICONTROL 양식 및 문서]**&#x200B;를 탭합니다.

1. **[!UICONTROL 만들기]** > **[!UICONTROL 적응형 양식]**&#x200B;을 탭합니다. 마법사가 열립니다. 소스 탭에서 템플릿을 선택합니다.

   ![핵심 구성 요소 템플릿](/help/forms/assets/core-components-template.png)

   템플릿을 선택하면 템플릿에 지정된 테마와 제출 액션이 자동으로 선택되고 **[!UICONTROL 만들기]** 버튼이 활성화됩니다. **[!UICONTROL 스타일]** 또는 **[!UICONTROL 제출]** 탭으로 이동하여 다른 테마를 선택하거나 액션을 제출할 수 있습니다. 선택한 템플릿이 테마를 지정하지 않으면 만들기 버튼은 비활성화된 상태로 유지됩니다. **[!UICONTROL 스타일]** 탭으로 이동하여 테마를 수동으로 선택할 수 있습니다.

   >[!NOTE]
   >
   >
   > 환경에 대해 **적응형 양식(핵심 구성 요소)** 템플릿이 없다면 [해당 환경에 대해 적응형 양식 핵심 구성 요소를 활성화합니다](setup-local-development-environment.md#enable-adaptive-forms-core-components-for-an-existing-aem-archetype-based-project). 환경에 대해 핵심 구성 요소를 활성화하면 **적응형 양식(핵심 구성 요소)** 템플릿이 해당 환경에 추가됩니다.

1. **[!UICONTROL 스타일]** 탭에서 테마를 선택합니다.

   * 선택한 템플릿이 테마를 지정하면 테마가 마법사에서 자동으로 선택됩니다. 스타일 탭에서 다른 테마를 선택할 수도 있습니다.

   * 선택한 템플릿이 테마를 지정하지 않으면 스타일 탭을 사용하여 테마를 선택할 수 있습니다. **[!UICONTROL 만들기]** 버튼은 테마가 선택된 후에만 활성화됩니다.

1. (선택 사항) 데이터 탭에서 데이터 모델을 선택합니다.

   * **양식 데이터 모델**: [양식 데이터 모델](data-integration.md)을 통해 서로 다른 데이터 소스의 엔티티와 서비스를 적응형 양식으로 통합할 수 있습니다. 생성 중인 적응형 양식에 여러 데이터 소스에서의 데이터 가져오기 및 쓰기 작업이 포함된 경우 양식 데이터 모델을 선택합니다.

   * **JSON 스키마**: [JSON 스키마](adaptive-form-json-schema-form-model.md) 핵심 구성 요소 기반의 적응형 양식을 통해 생성 또는 사용 중인 데이터의 구조를 나타내는 JSON 스키마를 연결함으로써 조직의 백엔드 시스템과 원활하게 통합할 수 있습니다. 이 연결을 통해 작성자는 스키마 요소를 사용하여 콘텐츠를 적응형 양식에 동적으로 추가할 수 있습니다. 작성 프로세스 도중 콘텐츠 브라우저의 데이터 모델 오브젝트 탭을 통해 스키마 요소에 쉽게 액세스할 수 있고, 모든 필드는 새로 만든 적응형 양식에 자동으로 추가됩니다.

   기본적으로 연결된 JSON 스키마의 모든 필드는 자동으로 선택되고 해당 적응형 구성 요소로 변환되어 작성 프로세스를 간소화합니다. 편리성을 추가하기 위해 마법사는 확인란을 통해 적응형 양식에 포함되어야 하는 필드를 선택할 수 있습니다.

1. **[!UICONTROL 제출]** 탭에서 제출 액션을 선택합니다.

   * 템플릿을 선택하면 템플릿에 지정된 제출 액션이 자동으로 선택됩니다. 제출 탭에서 다른 제출 액션을 선택할 수 있습니다. **[!UICONTROL 제출]** 탭에 사용 가능한 모든 제출 액션이 표시됩니다.

   * 선택한 템플릿이 제출 액션을 지정하지 않은 경우 **[!UICONTROL 제출]** 탭을 사용하여 제출 액션을 선택할 수 있습니다.

1. (선택사항) **[!UICONTROL 게재]** 탭에서 적응형 양식의 게시 또는 게시 취소 일자를 지정할 수 있습니다.

1. **[!UICONTROL 만들기]**&#x200B;를 탭합니다. 제목, 이름과 위치를 지정하여 적응형 양식을 저장할 대화 상자가 나타납니다.

   * **[!UICONTROL 제목]**&#x200B;은 양식의 표시 이름을 지정합니다. 제목은 [!DNL Experience Manager Forms] 사용자 인터페이스에서 형식을 식별하는 데 도움이 됩니다.
   * **[!UICONTROL 이름:]** 양식의 이름을 지정합니다. 이름이 지정된 노드가 저장소에서 만들어집니다. 제목 입력이 시작되면 이름 필드 값이 자동으로 생성됩니다. 제안 값을 변경할 수 있습니다. 이름 필드에는 영숫자 문자, 하이픈 및 밑줄만 포함될 수 있습니다. 잘못된 모든 입력은 하이픈으로 대체됩니다.
   * **[!UICONTROL 경로:]** 적응형 양식을 저장할 위치를 지정합니다. 적응형 양식을 `/content/dam/formsanddocuments`에서 바로 저장하거나 `/content/dam/formsanddocuments/adaptiveforms`와 같은 폴더를 만들어 적응형 양식을 저장할 수 있습니다. 경로에서 사용하기 전에 폴더를 만들어야 합니다. **[!UICONTROL 경로]** 필드는 폴더를 자동으로 만들지 않습니다.

1. **[!UICONTROL 만들기]**&#x200B;를 탭합니다. 적응형 양식을 만들고 적응형 양식 편집기에서 엽니다. 편집기에 템플릿에서 사용 가능한 콘텐츠가 표시됩니다.  적응형 양식 유형에 따라 연결된 <!--XFA form template, XML schema or --> JSON 스키마 또는 양식 데이터 모델에 존재하는 양식 요소가 사이드바에 있는 **[!UICONTROL 콘텐츠 브라우저]**&#x200B;의 **[!UICONTROL 데이터 모델 오브젝트]** 탭에 표시됩니다. 이러한 요소를 드래그 앤 드롭하여 적응형 양식을 작성할 수도 있습니다.

이제 을(를) 드래그 앤 드롭할 수 있습니다. [적응형 Forms 핵심 구성 요소](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html) Forms 을 클릭하여 양식을 디자인하고 만들 수 있습니다. 다음을 방문하실 수도 있습니다. [https://aemcomponents.dev/](https://aemcomponents.dev/) 사용 가능한 핵심 구성 요소 보기

## 적응형 양식에 대한 제출 액션 구성 {#configure-submit-action-for-form}

제출 액션을 사용하면 적응형 양식을 통해 캡처되는 데이터의 대상을 선택할 수 있습니다. 사용자가 적응형 양식에서 제출 버튼을 클릭하면 제출 액션이 트리거됩니다. 적응형 양식에는 즉시 사용 가능한 제출 액션이 포함됩니다. 기본 제출 액션을 확장하여 자신만의 사용자 지정 제출 액션을 만들 수도 있습니다. 양식에 대해 제출 액션을 구성하려면 다음 작업을 수행하십시오.

1. 콘텐츠 브라우저를 열고 적응형 양식의 **[!UICONTROL 안내서 컨테이너]** 구성 요소를 선택합니다.
1. 안내서 컨테이너 속성 ![안내서 속성](/help/forms/assets/configure-icon.svg) 아이콘을 클릭합니다. 적응형 양식 컨테이너 대화 상자가 열립니다.

1. **[!UICONTROL 제출]** 탭을 클릭합니다.

   ![제출 액션을 구성하려면 공구 모양 아이콘을 클릭하여 적응형 양식 컨테이너 대화 상자를 엽니다.](/help/forms/assets/adaptive-forms-submit-message.png)

1. 요구 사항에 따라 **[!UICONTROL 제출 액션]**&#x200B;을 선택하고 구성합니다. 제출 액션에 대한 자세한 내용은 [적응형 양식 제출 액션](/help/forms/configuring-submit-actions.md)

<!--
    
    ![Click the Wrench icon to open Adaptive Form Container dialog box to configure Data Models for the Adaptive Form Container component](/help/forms/assets/adaptive-forms-container.png)

-->

## 사용자를 페이지로 리디렉션하거나 양식 제출 시 감사 메시지 표시

양식을 제출할 때 사용자를 다른 웹 페이지나 메시지로 리디렉션할 수 있습니다. 사용자를 리디렉션하거나 감사 메시지를 구성하려면:

1. 콘텐츠 브라우저를 열고 적응형 양식의 **[!UICONTROL 안내서 컨테이너]** 구성 요소를 선택합니다.
1. 안내서 컨테이너 속성 ![안내서 속성](/help/forms/assets/configure-icon.svg) 아이콘을 클릭합니다. 적응형 양식 컨테이너 대화 상자가 열립니다.
1. 를 엽니다. **[!UICONTROL 제출]** 탭.

   ![렌치 아이콘을 클릭하여 적응형 양식 컨테이너 대화 상자를 열고 리디렉션 페이지 또는 감사 메시지를 구성합니다](/help/forms/assets/adaptive-forms-redirect-message.png)

   * 리디렉션 URL을 구성하려면 제출 시 옵션에서 **[!UICONTROL URL로 리디렉션]** 옵션을 클릭하고 AEM Sites 페이지를 검색 및 선택하거나 외부 페이지의 URL을 입력합니다.

   * 사용자 정의 메시지 또는 감사 메시지를 구성하려면 제출 시 옵션을 선택합니다. **[!UICONTROL 메시지 표시]** 옵션을 선택한 다음 **[!UICONTROL 메시지 콘텐츠]** 상자. 서식 있는 텍스트 상자입니다. 전체 화면 옵션을 사용하여 사용 가능한 모든 서식 있는 텍스트 항목을 볼 수 있습니다.

## 적응형 양식에 대한 스키마 또는 양식 데이터 모델 구성{#configure-schema-or-data-model-for-form}

양식 데이터 모델을 사용하여 사용자 작업에 따라 데이터를 보내고 받기 위해 양식을 데이터 소스에 연결할 수 있습니다. 양식을 JSON 스키마에 연결하여 사전 정의된 형식으로 제출된 데이터를 받을 수도 있습니다. 요구 사항에 따라 양식을 JSON 스키마 또는 양식 데이터 모델에 연결합니다.

* [JSON 스키마 만들기 및 환경에 업로드](/help/forms/adaptive-form-json-schema-form-model.md)
* [양식 데이터 모델 만들기](/help/forms/create-form-data-models.md)

### 양식에 대한 JSON 스키마 또는 양식 데이터 모델 구성

양식에 대해 JSON 스키마 또는 양식 데이터 모델을 구성하려면 다음 작업을 수행하십시오.

1. 콘텐츠 브라우저를 열고 적응형 양식의 **[!UICONTROL 안내서 컨테이너]** 구성 요소를 선택합니다.
1. 안내서 컨테이너 속성 ![안내서 속성](/help/forms/assets/configure-icon.svg) 아이콘을 클릭합니다. 적응형 양식 컨테이너 대화 상자가 열립니다.
1. 를 엽니다. **[!UICONTROL 데이터 모델]** 탭.

   ![렌치 아이콘을 클릭하여 적응형 양식 컨테이너 대화 상자를 열고 JSON 스키마 또는 양식 데이터 모델을 구성합니다.](/help/forms/assets/adaptive-forms-select-form-data-model-or-json-schema.png)

1. 요구 사항에 따라 JSON 스키마 또는 양식 데이터 모델을 선택하고 구성합니다.

   * 다음을 선택하면 **[!UICONTROL 양식 모델]** 옵션, 사용 **[!UICONTROL 양식 데이터 모델 선택]** 미리 구성된 양식 데이터 모델을 선택하는 옵션입니다.
   * 다음을 선택하면 **[!UICONTROL 스키마]** 옵션, 사용 **[!UICONTROL 스키마]** 양식에 대한 JSON 스키마를 선택하는 옵션입니다.

1. **[!UICONTROL 완료]**&#x200B;를 클릭합니다.

## 미리 채우기 서비스 구성  {#configure-prefill-service-for-form}

미리 채우기 서비스를 사용하여 기존 데이터를 사용하는 적응형 양식의 필드를 자동으로 채울 수 있습니다. 사용자가 양식을 열면 해당 필드의 값이 미리 채워집니다. 다음과 같은 작업을 수행할 수 있습니다.

* [사용자 지정 미리 채우기 서비스 만들기](/help/forms/prepopulate-adaptive-form-fields.md)
* [양식 데이터 모델 미리 채우기 서비스 사용](#fdm-prefill-service)

### 양식 데이터 모델 미리 채우기 서비스를 사용하여 적응형 양식의 필드를 미리 채웁니다 {#fdm-prefill-service}

양식 데이터 모델 미리 채우기 서비스를 사용하여 양식 데이터 모델이나 사용자 지정 미리 채우기 서비스를 사용하여 적응형 양식의 필드를 미리 채울 수 있습니다. 양식 데이터 모델 미리 채우기 서비스에서는 [구성된 양식 데이터 모델의 서비스 가져오기](work-with-form-data-model.md#add-data-model-objects-and-services-add-data-model-objects-and-services) 데이터를 검색합니다. 적응형 양식에 대해 양식 데이터 모델 미리 채우기 서비스를 사용하려면

1. 콘텐츠 브라우저를 열고 적응형 양식의 **[!UICONTROL 안내서 컨테이너]** 구성 요소를 선택합니다.
1. 안내서 컨테이너 속성 ![안내서 속성](/help/forms/assets/configure-icon.svg) 아이콘을 클릭합니다. 적응형 양식 컨테이너 대화 상자가 열립니다.
1. 적응형 양식 컨테이너 속성을 클릭합니다 ![적응형 양식 컨테이너 속성](/help/forms/assets/configure-icon.svg) 아이콘. 데이터 모델을 구성하는 적응형 양식 컨테이너 대화 상자가 열립니다.
   ![렌치 아이콘을 클릭하여 적응형 양식 컨테이너 대화 상자를 열고 리디렉션 페이지 또는 감사 메시지를 구성합니다](/help/forms/assets/adaptive-forms-container-prefill-service.png)
1. 양식 데이터 모델 선택. 를 엽니다. **[!UICONTROL 기본]** 탭. 미리 채우기 서비스에서 다음을 선택합니다. **[!UICONTROL 양식 데이터 모델 미리 채우기 서비스]**.
1. **[!UICONTROL 완료]**&#x200B;를 클릭합니다. 이제 적응형 양식이 양식 데이터 모델 미리 채우기를 사용하도록 구성되었습니다. 이제 다음을 사용할 수 있습니다. [규칙 편집기](rule-editor.md) 을 클릭하여 양식의 필드를 미리 채우는 규칙을 만듭니다.

## 적응형 양식의 양식 모델 속성 편집 {#edit-form-model}

1. 적응형 양식을 선택하고 ![페이지 정보](/help/forms/assets/Smock_Properties_18_N.svg) > **[!UICONTROL 속성 열기]**&#x200B;를 탭합니다. 양식 속성 페이지가 열립니다.

1. **[!UICONTROL 양식 모델]** 탭으로 이동하고 양식 모델을 선택합니다. 적응형 양식에 양식 모델이 없는 경우 JSON 스키마 또는 양식 데이터 모델 중 하나를 자유롭게 선택할 수 있습니다. 반면에 적응형 양식이 이미 양식 모델을 기반으로 하는 경우 같은 유형의 다른 양식 모델로 전환할 수 있는 옵션이 있습니다. 예를 들어 양식이 JSON 스키마를 사용하는 경우 다른 JSON 스키마로 쉽게 전환할 수 있고, 마찬가지로 양식이 양식 데이터 모델을 사용하는 경우 다른 양식 데이터 모델로 전환할 수 있습니다.

1. **[!UICONTROL 저장]**&#x200B;을 탭하여 변경 내용을 저장합니다.


<!--

## See next

* [Create style or themes for your forms](using-themes-in-core-components.md)
* [Add dynamic behavior to forms using the rule editor](rule-editor.md)
* [Set layout of forms for different screen sizes and device types](/help/sites-cloud/authoring/features/responsive-layout.md)
* [Sample themes templates and form data models](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/sample-themes-templates-form-data-models-core-components.html)

-->

## 추가 참조 {#see-also}

{{see-also}}
* [규칙 편집기를 사용하여 양식에 동적 동작 추가](rule-editor.md)
* [다양한 화면 크기 및 장치 유형에 대한 양식 레이아웃 설정](/help/sites-cloud/authoring/features/responsive-layout.md)

