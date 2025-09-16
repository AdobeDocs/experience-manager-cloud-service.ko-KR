---
title: '양식 빌더: 핵심 구성 요소로 양식 만들기'
description: AEM Forms의 양식 빌더를 사용하여 핵심 구성 요소가 있는 적응형 양식을 만드는 방법을 알아봅니다. 정보 수집 및 처리를 간소화하는 반응형 HTML5 양식이 필요한 양식 작성자에게 적합합니다.
keywords: 양식 빌더, 핵심 구성 요소, 양식 만들기, 양식 작성자, 적응형 양식, 양식 작성, AEM 양식, 반응형 양식
feature: Adaptive Forms, Core Components
role: User, Developer
level: Beginner
exl-id: 1e812d93-4ba5-4589-b59b-2f564d754b0f
source-git-commit: ab84a96d0e206395063442457a61f274ad9bed23
workflow-type: tm+mt
source-wordcount: '2348'
ht-degree: 49%

---

# 양식 빌더: 핵심 구성 요소로 양식 만들기 {#creating-an-adaptive-form-core-components}

| 버전 | 문서 링크 |
| -------- | ---------------------------- |
| AEM 6.5 | [여기 클릭](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-core-components/create-an-adaptive-form-core-components.html) |
| AEM as a Cloud Service | 이 문서 |


AEM Forms의 양식 빌더를 사용하면 매력적인 반응형, 동적 및 적응형 양식을 만들 수 있습니다. 전문적인 양식을 작성하는 양식 작성자이든, 반응형 양식을 신속하게 만들어야 하든 상관없이 AEM Forms에서는 사용자에게 친숙한 마법사를 제공합니다. 마법사에는 사전 구성된 템플릿, 스타일, 필드 및 제출 옵션을 쉽게 선택할 수 있는 빠른 탭 탐색 기능이 있습니다.

시작하기 전에 사용할 수 있는 Forms 구성 요소 유형에 대해 알아봅니다.

* [적응형 양식 핵심 구성 요소](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html?lang=ko): 표준화된 데이터 캡처 구성 요소입니다. 이 구성 요소는 맞춤화 기능을 제공하고, 개발 시간을 단축하고, 유지 관리 비용을 줄여 디지털 등록 경험을 개선합니다. 개발자는 이러한 구성 요소를 손쉽게 사용자 정의하고 스타일링할 수 있습니다. Adobe에서는 이러한 현대적이고 확장 가능한 구성 요소를 사용하여 적응형 Forms을 개발할 것을 권장합니다.

* [적응형 양식 기초 구성 요소](creating-adaptive-form.md): 클래식(이전) 데이터 캡처 구성 요소입니다. 이를 계속 사용하여 기존의 기초 구성 요소 기반 적응형 양식을 편집할 수 있습니다. Adobe 새 양식을 만드는 경우 [적응형 Forms 핵심 구성 요소](creating-adaptive-form-core-components.md)를 사용하여 적응형 Forms을 만드는 것이 좋습니다.

![적응형 양식 만들기 마법사](/help/release-notes/assets/wizard.png)


## 사전 요구 사항

적응형 양식을 만들려면 다음이 필요합니다.


* **환경에 적응형 Forms 핵심 구성 요소 사용**: 프로그램을 만들 때 환경에 대해 적응형 Forms 핵심 구성 요소가 이미 활성화되었습니다.  AEM Cloud Service 환경에 대한 적응형 Forms 핵심 구성 요소를 활성화하려면 최신 파트를 설치하십시오. 환경에 대한 핵심 구성 요소를 활성화하면 **적응형 Forms(핵심 구성 요소)** 템플릿과 테마가 환경에 추가됩니다. 적응형 양식 핵심 구성 요소는 2023.02.0 릴리스 이전의 프리릴리스 일부로 제공되었으므로 사용 중인 AEM SDK 버전이 2023.02.0 이전 버전이라면 [해당 환경에서 `prerelease` 플래그가 활성화](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/release-notes/prerelease.html?lang=ko#new-features)되어 있어야 합니다.

* **적응형 양식 템플릿**: 템플릿은 기본 구조를 제공하고 적응형 양식의 모양(레이아웃 및 스타일)을 정의합니다. 특정 속성과 콘텐츠 구조를 포함하는 서식이 미리 지정된 구성 요소가 있습니다. 또한 테마와 제출 액션을 정의하는 옵션이 제공됩니다. 테마는 모양과 느낌을 정의하고 제출 액션은 적응형 양식 제출 시 수행할 작업을 정의합니다. 예: 수집된 데이터를 데이터 소스로 보내기. 클라우드 서비스는 blank라는 OOTB 템플릿을 제공합니다.

   * `blank` 템플릿은 새로운 모든 AEM Forms as a Cloud Service 프로그램에 포함됩니다.
   * 패키지 관리자를 통해 참조 패키지를 설치하여 `blank` 템플릿을 AEM Forms as a Cloud Service 프로그램에 추가할 수 있습니다.
   * [적응형 Forms 템플릿(핵심 구성 요소)을 ](/help/forms/template-editor-core-components.md)할 수도 있습니다.
   * [샘플 템플릿](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/sample-themes-templates-form-data-models-core-components.html)을 환경에 배포할 수도 있습니다. 이렇게 하면 양식을 신속하게 만들 수 있습니다.

* **적응형 양식 테마**: 테마에 구성 요소 및 패널에 대한 스타일링 세부 정보가 포함됩니다. 스타일에는 배경색, 상태 색상, 투명도, 정렬과 크기와 같은 속성이 포함됩니다. 테마를 적용하면 지정된 스타일은 해당 구성 요소에 반영됩니다.  `Canvas` 템플릿은 모든 최신 AEM Forms as a Cloud Service 프로그램에 포함되어 있습니다. [샘플 테마](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/sample-themes-templates-form-data-models-core-components.html)를 환경에 배포할 수도 있습니다. 이를 통해 양식의 스타일을 시작하고 비즈니스 요구 사항에 따라 테마를 만들거나 맞춤화할 수 있는 기본 구조를 제공할 수 있습니다.

  <!-- * You can install the reference package, via package manager, to add the `Canvas` template to your AEM Forms as a Cloud Service program.
    * You can also [create an Adaptive Forms theme (Core Components)](template-editor.md) and deploy it to your AEM Forms as a Cloud Service program. -->

* **권한**: 사용자를 [!DNL forms-users] 그룹에 추가합니다. [!DNL forms-users] 그룹의 멤버는 적응형 양식을 만들 수 있는 권한이 있습니다. 양식별 사용자 그룹에 대한 세부 목록은 [그룹 및 권한](forms-groups-privileges-tasks.md)을 참조하십시오.

<!--
>[!NOTE]
>
>
> In addition to the given themes and templates when you enable Core Components, you can also deploy the latest out-of-the box [sample themes and templates](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/sample-themes-templates-form-data-models-core-components.html) to your AEM environment for use in Core Components based Adaptive Forms.
-->

## 적응형 양식 작성  {#create-an-adaptive-form-core-components}

1. [!DNL Experience Manager Forms] 작성자 인스턴스에 로그인합니다. 클라우드 인스턴스 또는 로컬 개발 인스턴스일 수 있습니다.

1. Experience Manager 로그인 페이지에서 자격 증명을 입력합니다. 로그인한 후 왼쪽 상단에서 **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL 양식]** > **[!UICONTROL 양식 및 문서]**&#x200B;를 선택합니다.

1. **[!UICONTROL 만들기]** > **[!UICONTROL 적응형 양식]**&#x200B;을 선택합니다. 마법사가 열립니다. 소스 탭에서 템플릿을 선택합니다.

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

   * **양식 데이터 모델(FDM)**: [양식 데이터 모델](data-integration.md)을 사용하면 서로 다른 데이터 소스의 엔터티 및 서비스를 적응형 양식에 통합할 수 있습니다. 생성 중인 적응형 양식에 여러 데이터 소스에서 데이터를 가져오고 쓰는 작업이 포함된 경우 양식 데이터 모델(FDM)을 선택합니다.

   * **JSON 스키마**: [JSON 스키마](adaptive-form-json-schema-form-model.md) 핵심 구성 요소 기반의 적응형 양식을 통해 생성 또는 사용 중인 데이터의 구조를 나타내는 JSON 스키마를 연결함으로써 조직의 백엔드 시스템과 원활하게 통합할 수 있습니다. 이 연결을 통해 작성자는 스키마 요소를 사용하여 콘텐츠를 적응형 양식에 동적으로 추가할 수 있습니다. 작성 프로세스 중에 컨텐츠 브라우저의 데이터 모델 개체 탭에서 스키마 요소에 쉽게 액세스할 수 있으며, 모든 필드는 만든 적응형 양식에 자동으로 추가됩니다.

   기본적으로 연결된 JSON 스키마의 모든 필드는 자동으로 선택되고 해당 적응형 구성 요소로 변환되어 작성 프로세스를 간소화합니다. 편리성을 추가하기 위해 마법사는 확인란을 통해 적응형 양식에 포함되어야 하는 필드를 선택할 수 있습니다.

1. **[!UICONTROL 제출]** 탭에서 제출 액션을 선택합니다.

   * 템플릿을 선택하면 템플릿에 지정된 제출 액션이 자동으로 선택됩니다. 제출 탭에서 다른 제출 액션을 선택할 수 있습니다. **[!UICONTROL 제출]** 탭에 사용 가능한 모든 제출 액션이 표시됩니다.

   * 선택한 템플릿이 제출 액션을 지정하지 않은 경우 **[!UICONTROL 제출]** 탭을 사용하여 제출 액션을 선택할 수 있습니다.

1. (선택사항) **[!UICONTROL 게재]** 탭에서 적응형 양식의 게시 또는 게시 취소 일자를 지정할 수 있습니다.

1. **[!UICONTROL 만들기]**&#x200B;를 선택합니다. 제목, 이름과 위치를 지정하여 적응형 양식을 저장할 대화 상자가 나타납니다.

   * **[!UICONTROL 제목]**&#x200B;은 양식의 표시 이름을 지정합니다. 제목은 [!DNL Experience Manager Forms] 사용자 인터페이스에서 형식을 식별하는 데 도움이 됩니다.
   * **[!UICONTROL 이름:]** 양식의 이름을 지정합니다. 이름이 지정된 노드가 저장소에서 만들어집니다. 제목 입력이 시작되면 이름 필드 값이 자동으로 생성됩니다. 제안 값을 변경할 수 있습니다. 이름 필드에는 영숫자 문자, 하이픈 및 밑줄만 포함될 수 있습니다. 잘못된 모든 입력은 하이픈으로 대체됩니다.
   * **[!UICONTROL 경로:]** 적응형 양식을 저장할 위치를 지정합니다. 적응형 양식을 `/content/dam/formsanddocuments`에서 바로 저장하거나 `/content/dam/formsanddocuments/adaptiveforms`와 같은 폴더를 만들어 적응형 양식을 저장할 수 있습니다. 경로에서 사용하기 전에 폴더를 만들어야 합니다. **[!UICONTROL 경로]** 필드는 폴더를 자동으로 만들지 않습니다.

1. **[!UICONTROL 만들기]**&#x200B;를 선택합니다. 적응형 양식을 만들고 적응형 양식 편집기에서 엽니다. 편집기에 템플릿에서 사용 가능한 콘텐츠가 표시됩니다.  적응형 양식 유형에 따라 연결된 <!--XFA form template, XML schema or --> JSON 스키마 또는 양식 데이터 모델(FDM)에 있는 양식 요소가 사이드바의 **[!UICONTROL 콘텐츠 브라우저]**&#x200B;에 있는 **[!UICONTROL 데이터 모델 개체]** 탭에 표시됩니다. 이러한 요소를 드래그 앤 드롭하여 적응형 양식을 작성할 수도 있습니다.

이제 [적응형 Forms 핵심 구성 요소](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html)를 적응형 Forms 컨테이너로 드래그 앤 드롭하여 양식을 디자인하고 만들 수 있습니다. [https://aemcomponents.dev/](https://aemcomponents.dev/)을(를) 방문하여 사용 중인 핵심 구성 요소를 볼 수도 있습니다.

>[!NOTE]
>
> XFA 양식 템플릿(*.XDP 파일)을 사용하여 [적응형 Forms을 만들 수도 있습니다](/help/forms/create-adaptive-form-using-xfa-templates.md). 적응형 Forms에서 직접 XDP 파일의 필드를 재사용하여 시간을 절약할 수 있습니다.

## 적응형 양식에 대한 제출 액션 구성 {#configure-submit-action-for-form}

제출 액션을 사용하면 적응형 양식을 통해 캡처되는 데이터의 대상을 선택할 수 있습니다. 사용자가 적응형 양식에서 제출 단추를 클릭하면 트리거됩니다. 적응형 양식에는 즉시 사용 가능한 제출 액션이 포함됩니다. 기본 제출 액션을 확장하여 자신만의 사용자 지정 제출 액션을 만들 수도 있습니다. 양식에 대해 제출 액션을 구성하려면 다음 작업을 수행하십시오.

1. 콘텐츠 브라우저를 열고 적응형 양식의 **[!UICONTROL 안내서 컨테이너]** 구성 요소를 선택합니다.
1. 안내서 컨테이너 속성 ![안내서 속성](/help/forms/assets/configure-icon.svg) 아이콘을 클릭합니다. 적응형 양식 컨테이너 대화 상자가 열립니다.

1. **[!UICONTROL 제출]** 탭을 클릭합니다.

   ![제출 액션을 구성하려면 공구 모양 아이콘을 클릭하여 적응형 양식 컨테이너 대화 상자를 엽니다.](/help/forms/assets/adaptive-forms-submit-message.png)

1. 요구 사항에 따라 **[!UICONTROL 제출 액션]**&#x200B;을 선택하고 구성합니다. 제출 액션에 대한 자세한 내용은 [적응형 양식 제출 액션](/help/forms/configuring-submit-actions.md)을 참조하세요.

<!--
    
    ![Click the Wrench icon to open Adaptive Form Container dialog box to configure Data Models for the Adaptive Form Container component](/help/forms/assets/adaptive-forms-container.png)

-->

## 사용자를 페이지로 리디렉션하거나 양식 제출 시 감사 메시지 표시

양식을 제출할 때 사용자를 다른 웹 페이지나 메시지로 리디렉션할 수 있습니다. 사용자를 리디렉션하거나 감사 메시지를 구성하려면:

1. 콘텐츠 브라우저를 열고 적응형 양식의 **[!UICONTROL 안내서 컨테이너]** 구성 요소를 선택합니다.
1. 안내서 컨테이너 속성 ![안내서 속성](/help/forms/assets/configure-icon.svg) 아이콘을 클릭합니다. 적응형 양식 컨테이너 대화 상자가 열립니다.
1. **[!UICONTROL 제출]** 탭을 엽니다.

   ![렌치 아이콘을 클릭하여 적응형 양식 컨테이너 대화 상자를 열어 리디렉션 페이지 또는 감사 메시지를 구성하십시오](/help/forms/assets/adaptive-forms-redirect-message.png)

   * 리디렉션 URL을 구성하려면 [제출 시] 옵션에서 **[!UICONTROL URL로 리디렉션]** 옵션을 선택하고 AEM Sites 페이지를 검색하여 선택하거나 외부 페이지의 URL을 제공합니다.

   * 사용자 지정 또는 감사 메시지를 구성하려면 [전송] 옵션에서 **[!UICONTROL 메시지 표시]** 옵션을 선택하고 **[!UICONTROL 메시지 내용]** 상자에 메시지를 제공합니다. 서식 있는 텍스트 상자입니다. 전체 화면 옵션을 사용하여 사용 가능한 모든 서식 있는 텍스트 항목을 볼 수 있습니다.

## 적응형 양식에 대한 스키마 또는 양식 데이터 모델(FDM) 구성{#configure-schema-or-data-model-for-form}

FDM(양식 데이터 모델)을 사용하여 양식을 데이터 Source에 연결하여 사용자 작업에 따라 데이터를 보내고 받을 수 있습니다. 양식을 JSON 스키마에 연결하여 미리 정의된 형식으로 제출된 데이터를 받을 수도 있습니다. 요구 사항에 따라 양식을 JSON 스키마 또는 양식 데이터 모델(FDM)에 연결합니다.

* [JSON 스키마 만들기 및 환경에 업로드](/help/forms/adaptive-form-json-schema-form-model.md)
* [FDM(양식 데이터 모델) 만들기](/help/forms/create-form-data-models.md)

### 양식에 대한 JSON 스키마 또는 양식 데이터 모델(FDM) 구성

양식에 대해 JSON 스키마 또는 양식 데이터 모델(FDM)을 구성하려면 다음을 수행합니다.

1. 콘텐츠 브라우저를 열고 적응형 양식의 **[!UICONTROL 안내서 컨테이너]** 구성 요소를 선택합니다.
1. 안내서 컨테이너 속성 ![안내서 속성](/help/forms/assets/configure-icon.svg) 아이콘을 클릭합니다. 적응형 양식 컨테이너 대화 상자가 열립니다.
1. **[!UICONTROL 데이터 모델]** 탭을 엽니다.

   ![렌치 아이콘을 클릭하여 적응형 양식 컨테이너 대화 상자를 열어 JSON 스키마 또는 양식 데이터 모델(FDM)을 구성합니다](/help/forms/assets/adaptive-forms-select-form-data-model-or-json-schema.png)

1. 요구 사항에 따라 JSON 스키마 또는 양식 데이터 모델(FDM)을 선택하고 구성합니다.

   * **[!UICONTROL 양식 모델]** 옵션을 선택하는 경우 **[!UICONTROL 양식 데이터 모델 선택]** 옵션을 사용하여 미리 구성된 양식 데이터 모델(FDM)을 선택합니다.
   * **[!UICONTROL 스키마]** 옵션을 선택하는 경우 **[!UICONTROL 스키마]** 옵션을 사용하여 양식에 대한 JSON 스키마를 선택하십시오.

1. **[!UICONTROL 완료]**&#x200B;를 클릭합니다.

## 미리 채우기 서비스 구성  {#configure-prefill-service-for-form}

미리 채우기 서비스를 사용하여 기존 데이터를 사용하는 적응형 양식의 필드를 자동으로 채울 수 있습니다. 사용자가 양식을 열면 해당 필드의 값이 미리 채워집니다. 다음과 같은 작업을 수행할 수 있습니다.

* [사용자 지정 미리 채우기 서비스 만들기](/help/forms/prepopulate-adaptive-form-fields.md)
* [양식 데이터 모델 미리 채우기 서비스 사용](#fdm-prefill-service)

### 양식 데이터 모델 미리 채우기 서비스를 사용하여 적응형 양식의 필드를 미리 채웁니다 {#fdm-prefill-service}

양식 데이터 모델 미리 채우기 서비스를 사용하여 양식 데이터 모델이나 사용자 지정 미리 채우기 서비스를 사용하여 적응형 양식의 필드를 미리 채울 수 있습니다. 양식 데이터 모델 미리 채우기 서비스는 [구성된 양식 데이터 모델의 Get 서비스](work-with-form-data-model.md#add-data-model-objects-and-services-add-data-model-objects-and-services)를 사용하여 데이터를 검색합니다. 적응형 양식에 대해 양식 데이터 모델 미리 채우기 서비스를 사용하려면

1. 콘텐츠 브라우저를 열고 적응형 양식의 **[!UICONTROL 안내서 컨테이너]** 구성 요소를 선택합니다.
1. 안내서 컨테이너 속성 ![안내서 속성](/help/forms/assets/configure-icon.svg) 아이콘을 클릭합니다. 적응형 양식 컨테이너 대화 상자가 열립니다.
1. 적응형 양식 컨테이너 속성 ![적응형 양식 컨테이너 속성](/help/forms/assets/configure-icon.svg) 아이콘을 클릭합니다. 데이터 모델을 구성하는 적응형 양식 컨테이너 대화 상자가 열립니다.
   ![렌치 아이콘을 클릭하여 적응형 양식 컨테이너 대화 상자를 열어 리디렉션 페이지 또는 감사 메시지를 구성하십시오](/help/forms/assets/adaptive-forms-container-prefill-service.png)
1. 양식 데이터 모델(FDM)을 선택합니다. **[!UICONTROL 기본]** 탭을 엽니다. 미리 채우기 서비스에서 **[!UICONTROL 양식 데이터 모델 미리 채우기 서비스]**&#x200B;를 선택합니다.
1. **[!UICONTROL 완료]**&#x200B;를 클릭합니다. 이제 적응형 양식이 양식 데이터 모델 미리 채우기를 사용하도록 구성되었습니다. 이제 [규칙 편집기](rule-editor.md)를 사용하여 양식의 필드를 미리 채우는 규칙을 만들 수 있습니다.

## 적응형 양식의 양식 모델 속성 편집 {#edit-form-model}

1. 적응형 양식을 선택하고 ![페이지 정보](/help/forms/assets/Smock_Properties_18_N.svg) > **[!UICONTROL 속성 열기]**&#x200B;를 선택합니다. 양식 속성 페이지가 열립니다.

1. **[!UICONTROL 양식 모델]** 탭으로 이동하고 양식 모델을 선택합니다. 적응형 양식에 양식 모델이 없는 경우 JSON 스키마 또는 양식 데이터 모델(FDM)을 선택할 수 있습니다. 반면에 적응형 양식이 이미 양식 모델을 기반으로 하는 경우 같은 유형의 다른 양식 모델로 전환할 수 있는 옵션이 있습니다. 예를 들어 양식이 JSON 스키마를 사용하는 경우 다른 JSON 스키마로 쉽게 전환할 수 있으며, 마찬가지로 양식이 양식 데이터 모델(FDM)을 사용하는 경우 다른 양식 데이터 모델(FDM)로 전환할 수 있습니다.

1. 속성을 저장하려면 **[!UICONTROL 저장]**&#x200B;을(를) 선택하십시오.


## AEM 적응형 양식의 이름을 변경하는 방법 {#rename-an-AEM-Adaptive-Form}

적응형 양식의 이름을 변경하려면 다음 단계를 수행하십시오.

1. AEM Forms 사용자 인터페이스에서 적응형 양식을 선택합니다.
1. 위쪽 레일에 있는 **속성**&#x200B;을 클릭합니다.
1. 아래 그림과 같이 **제목** 탭에서 양식 이름을 변경합니다.
1. **저장 후 닫기**&#x200B;를 클릭합니다.

![AEM 적응형 양식 이름 바꾸기](/help/forms/assets/change-af-name.png)



