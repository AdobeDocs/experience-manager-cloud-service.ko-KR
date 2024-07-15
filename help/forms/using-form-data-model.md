---
title: 적응형 양식에 대한 양식 데이터 모델(FDM)을 만들려면 어떻게 해야 합니까?
description: FDM(양식 데이터 모델)을 기반으로 적응형 Forms 및 조각을 만드는 방법에 대해 알아봅니다. FDM에서 데이터 모델 개체에 대한 샘플 데이터를 생성하고 편집합니다.
feature: Adaptive Forms, Form Data Model
role: Admin, User
level: Beginner, Intermediate
exl-id: 827ce457-6585-46fb-8e28-1d970a40d949
source-git-commit: 7b31a2ea016567979288c7a8e55ed5bf8dfc181d
workflow-type: tm+mt
source-wordcount: '1321'
ht-degree: 4%

---

# 양식 데이터 모델(FDM) 사용 {#use-form-data-model}

| 버전 | 문서 링크 |
| -------- | ---------------------------- |
| AEM 6.5 | [여기 클릭](https://experienceleague.adobe.com/docs/experience-manager-65/forms/form-data-model/using-form-data-model.html) |
| AEM as a Cloud Service | 이 문서 |


![데이터 통합](do-not-localize/data-integeration.png)

[!DNL Experience Manager Forms] 데이터 통합을 사용하면 다양한 백엔드 데이터 소스를 사용하여 다양한 적응형 Forms <!--and interactive communications--> 워크플로에서 스키마로 사용할 수 있는 FDM(양식 데이터 모델)을 만들 수 있습니다. 데이터 소스를 구성하고 데이터 소스에서 사용할 수 있는 데이터 모델 개체 및 서비스를 기반으로 양식 데이터 모델(FDM)을 만들어야 합니다. 자세한 내용은 다음을 참조하십시오.

* [[!DNL Experience Manager Forms] 데이터 통합](data-integration.md)
* [데이터 소스 구성](configure-data-sources.md)
* [양식 데이터 모델(FDM) 만들기](create-form-data-models.md)
* [양식 데이터 모델(FDM) 작업](work-with-form-data-model.md)

FDM(양식 데이터 모델)은 다음과 같은 작업을 수행하는 데 사용할 수 있는 JSON 스키마의 확장입니다.

* [적응형 Forms 및 조각 만들기](#create-af)
  <!--* [Create interactive communications and building blocks like text, list, and condition fragments](#create-ic)-->
* [샘플 데이터로 미리 보기](#preview-ic)
* [양식 데이터 모델 서비스 사용](#prefill)
* [제출된 적응형 양식 데이터를 데이터 소스에 다시 쓰기](#write-af)
* [적응형 양식 규칙을 사용하여 서비스 호출](#invoke-services)

## 적응형 Forms 및 조각 만들기 {#create-af}

FDM(양식 데이터 모델)을 기반으로 [적응형 Forms](creating-adaptive-form.md) 및 적응형 양식 단편 <!-- [Adaptive Form Fragments](adaptive-form-fragments.md) -->을(를) 만들 수 있습니다. 적응형 양식 또는 적응형 양식 단편을 만들 때 FDM(양식 데이터 모델)을 사용하려면 다음을 수행하십시오.

1. 속성 추가 화면의 양식 모델 탭에서 **[!UICONTROL 다음에서 선택]** 드롭다운 목록에서 **[!UICONTROL 양식 데이터 모델]**&#x200B;을(를) 선택합니다.

   ![create-af-1-1](assets/create-af-1-1.png)

2. **[!UICONTROL 양식 데이터 모델 선택]**&#x200B;을 확장하려면 선택하십시오. 사용 가능한 모든 양식 데이터 모델(FDM)이 나열됩니다.

   데이터 모델에서 을(를) 선택합니다.

   ![create-af-2-1](assets/create-af-2-1.png)

3. (**적응형 양식 조각만**) FDM(양식 데이터 모델)의 데이터 모델 개체 하나만 기반으로 적응형 양식 조각을 만들 수 있습니다. **[!UICONTROL 양식 데이터 모델 정의]** 드롭다운을 확장합니다. 지정된 양식 데이터 모델(FDM)의 모든 데이터 모델 객체를 나열합니다. 목록에서 데이터 모델 개체를 선택합니다.

   ![create-af-3](assets/create-af-3.png)

   양식 데이터 모델(FDM)을 기반으로 하는 적응형 양식 또는 적응형 양식 단편을 만들면 양식 데이터 모델 개체가 적응형 양식 편집기에 있는 콘텐츠 브라우저의 **[!UICONTROL 데이터 소스]** 탭에 나타납니다.

   >[!NOTE]
   >
   >적응형 양식 조각의 경우 작성 시 선택한 데이터 모델 개체 및 연관된 데이터 모델 개체만 데이터 소스 탭에 나타납니다.

   ![data-model-objects-tab](assets/data-model-objects-tab.png)

   데이터 모델 개체를 적응형 양식 또는 조각으로 드래그 앤 드롭하여 양식 필드를 추가할 수 있습니다. 추가된 양식 필드는 메타데이터 속성 및 데이터 모델 개체 속성을 사용한 바인딩을 유지합니다. 바인딩을 사용하면 양식을 제출할 때 해당 데이터 소스에서 필드 값을 업데이트하고 양식을 렌더링할 때 미리 채워집니다.

<!-- ## Create interactive communications {#create-ic}

You can create an interactive communication based on a Form Data Model that you can use to prefill interactive communication with data from configured data sources. In addition, the building blocks of an interactive communication, such as text, list, and condition document fragments can be based on a form data model.

You can choose a Form Data Model when creating an interactive communication or a document fragment. The following image shows the General tab of the Create Interactive Communication dialog.

![create-ic](assets/create-ic.png)

General tab of Create Interactive Communication dialog

For more information, see:

[Create an interactive communication](create-interactive-communication.md)

[Text in Interactive Communications](texts-interactive-communications.md)

[Conditions in Interactive Communications](conditions-interactive-communications.md)

[List fragments](lists.md) -->

## 샘플 데이터로 미리 보기 {#preview-ic}

양식 데이터 모델 편집기를 사용하면 양식 데이터 모델(FDM)의 데이터 모델 개체에 대한 샘플 데이터를 생성하고 편집할 수 있습니다. 이 데이터를 사용하여 <!--interactive communications and--> 응용 Forms을 미리 보고 테스트할 수 있습니다. [양식 데이터 모델 작업](work-with-form-data-model.md#sample)에 설명된 대로 미리 보기 전에 샘플 데이터를 생성해야 합니다.

<!--To preview an interactive communication with sample Form Data Model data:

1. On [!DNL  Experience Manager] author instance, navigate to **[!UICONTROL Forms > Forms & Documents]**.
1. Select an interactive communication and select **[!UICONTROL Preview]** in the toolbar to select **[!UICONTROL Web Channel]**, **[!UICONTROL Print Channel]**, or **[!UICONTROL Both Channels]** to preview the interactive communication.
1. In the Preview [*channel*] dialog, ensure that **[!UICONTROL Test Data of Form Data Model]** is selected and select **[!UICONTROL Preview]**.

The interactive communication opens with prefilled sample data.

![web-preview](assets/web-preview.png)-->

샘플 데이터가 있는 적응형 양식을 미리 보려면 작성자 모드에서 적응형 양식을 열고 **[!UICONTROL 미리 보기]**&#x200B;를 선택하십시오.

## 양식 데이터 모델 서비스를 사용하여 미리 채우기 {#prefill}

[!DNL Experience Manager Forms]은(는) FDM(양식 데이터 모델)을 기반으로 적응형 Forms <!--and interactive communications-->에 대해 활성화할 수 있는 기본 양식 데이터 모델 미리 채우기 서비스를 제공합니다. 미리 채우기 서비스는 적응형 양식 <!--and interactive communication-->에서 데이터 모델 개체에 대한 데이터 원본을 쿼리하며 이에 따라 양식을 렌더링하거나 통신을 렌더링하는 동안 데이터를 미리 채웁니다.

적응형 양식에 대해 양식 데이터 모델 미리 채우기 서비스를 사용하려면 적응형 양식 컨테이너 속성을 열고 기본 아코디언의 **[!UICONTROL 미리 채우기 서비스]** 드롭다운에서 **[!UICONTROL 양식 데이터 모델 미리 채우기 서비스]**&#x200B;를 선택합니다. 그런 다음 속성을 저장합니다.

![미리 채우기 서비스](assets/prefill-service.png)

<!--To configure Form Data Model prefill service in an interactive communication, you can select Form Data Model Prefill Service in the Prefill Service drop-down while creating it or later by modifying the properties.

![edit-ic-props](assets/edit-ic-props.png)

Edit Properties dialog for an interactive communication-->

## 제출된 적응형 양식 데이터를 데이터 소스에 쓰기 {#write-af}

사용자가 양식 데이터 모델(FDM)을 기반으로 양식을 제출할 때 데이터 모델 객체에 대해 제출된 데이터를 해당 데이터 소스에 기록하도록 양식을 구성할 수 있습니다. 이 사용 사례를 달성하기 위해 [!DNL Experience Manager Forms]은(는) 양식 데이터 모델(FDM)을 기반으로 하는 적응형 Forms에 대해서만 즉시 사용할 수 있는 [양식 데이터 모델 제출 액션](configuring-submit-actions.md)을 제공합니다. 데이터 소스에 데이터 모델 개체에 대해 제출된 데이터를 기록합니다.

양식 데이터 모델 제출 액션을 구성하려면 다음 작업을 수행하십시오.

1. 콘텐츠 브라우저를 열고 적응형 양식의 **[!UICONTROL 안내서 컨테이너]** 구성 요소를 선택합니다.
1. 안내서 컨테이너 속성 ![안내서 속성](/help/forms/assets/configure-icon.svg) 아이콘을 클릭합니다. 적응형 양식 컨테이너 대화 상자가 열립니다.
1. **[!UICONTROL 제출]** 탭을 클릭합니다.
1. **[!UICONTROL 제출 액션]** 드롭다운 목록에서 **[!UICONTROL 양식 데이터 모델을 사용하여 제출]**&#x200B;을 선택합니다.

   ![작업 구성](/help/forms/assets/configure-submit-action-invoke-fdm.png)

1. 제출할 **[!UICONTROL 데이터 모델을 지정]**&#x200B;합니다.
1. **[!UICONTROL 완료]** 클릭

양식 제출 시 구성된 데이터 모델 개체의 데이터가 해당 데이터 소스에 기록됩니다. 또한 FDM(양식 데이터 모델) 및 DoR(기록 문서)을 사용하여 양식 첨부 파일을 데이터 소스에 제출할 수 있습니다. 양식 데이터 모델(FDM)에 대한 자세한 내용은 [[!DNL AEM Forms] 데이터 통합](data-integration.md)을 참조하십시오.

<!--![data-submission](assets/data-submission.png)-->

>[!NOTE]
>
> AEM as a Cloud Service에서는 양식 제출을 처리하기 위한 다양한 제출 액션을 제공합니다. [적응형 양식 제출 액션](/help/forms/configure-submit-actions-core-components.md) 문서에서 이러한 옵션에 대해 자세히 알아볼 수 있습니다.

이진 데이터 모델 개체 속성을 사용하여 데이터 소스에 양식 첨부 파일을 제출할 수도 있습니다. 다음을 수행하여 첨부 파일을 JDBC 데이터 소스에 제출합니다.

1. 이진 속성을 포함하는 데이터 모델 개체를 양식 데이터 모델(FDM)에 추가합니다.
1. 적응형 양식에서 구성 요소 브라우저에서 **[!UICONTROL 파일 첨부]** 구성 요소를 적응형 양식으로 드래그 앤 드롭합니다.
1. 추가된 구성 요소를 선택하려면 선택하고 구성 요소의 속성 브라우저를 열려면 ![settings_icon](assets/configure-icon.svg)을(를) 선택하십시오.
1. 바인드 참조 필드에서 ![foldersearch_18](assets/folder-search-icon.svg)을(를) 선택하고 FDM(양식 데이터 모델)에서 추가한 이진 속성을 선택하여 이동합니다. 필요에 따라 다른 속성을 구성합니다.

   속성을 저장하려면 ![확인 단추](assets/save_icon.svg)를 선택하세요. 이제 첨부 파일 필드가 양식 데이터 모델(FDM)의 이진 속성에 바인딩됩니다.

1. 적응형 양식 컨테이너 속성의 제출 섹션에서 **[!UICONTROL 양식 첨부 파일 제출]**&#x200B;을 사용하도록 설정합니다. 양식을 제출할 때 이진 속성 필드의 첨부 파일을 데이터 소스에 제출합니다.

## 규칙을 사용하여 적응형 Forms에서 서비스 호출 {#invoke-services}

FDM(양식 데이터 모델)을 기반으로 하는 적응형 양식에서 [규칙을 만들기](rule-editor.md)하여 FDM(양식 데이터 모델)에 구성된 서비스를 호출할 수 있습니다. 규칙의 **[!UICONTROL 서비스 호출]** 작업은 FDM(양식 데이터 모델)에서 사용 가능한 모든 서비스를 나열하며 서비스에 대한 입력 및 출력 필드를 선택할 수 있도록 해줍니다. **[!UICONTROL 값 설정]** 규칙 유형을 사용하여 양식 데이터 모델 서비스를 호출하고 필드의 값을 서비스에서 반환된 출력으로 설정할 수도 있습니다.

예를 들어, 다음 규칙은 직원 ID를 입력으로 취하며 반환된 값이 양식의 해당 종속 ID, 성, 이름 및 성별 필드에 채워지는 get 서비스를 호출합니다.

![서비스 호출](assets/invoke-service.png)

또한 `guidelib.dataIntegrationUtils.executeOperation` API를 사용하여 규칙 편집기의 코드 편집기에서 JavaScript을 작성할 수 있습니다. <!-- For API details, see [API to invoke Form Data Model service](invoke-form-data-model-services.md).-->

### 사용자 정의 함수를 사용하여 양식 데이터 모델(FDM) 호출 {#invoke-form-data-model-using-custom-functions}

[사용자 지정 함수를 사용하여 규칙 편집기에서 양식 데이터 모델을 호출할 수 있습니다](/help/forms/rule-editor.md#custom-functions-in-rule-editor-custom-functions). 허용 목록에 추가하다 양식 데이터 모델(FDM)을 호출하려면 양식 데이터 모델을 양식 데이터 모델에 추가합니다. 허용 목록에 양식 데이터 모델을 추가하려면 다음을 수행합니다.

1. `https://server:host/system/console/configMgr`의 Experience Manager 웹 콘솔로 이동합니다.
1. 서비스 호출 - 구성 팩터리&#x200B;]**에 대한 양식 데이터 모델의**[!UICONTROL &#x200B;적응형 양식 수준 화이트리스트를 찾습니다.
1. ![더하기 아이콘](/help/forms/assets/Smock_Add_18_N.svg) 아이콘을 클릭하여 구성을 추가합니다.
1. **[!UICONTROL 콘텐츠 경로 패턴]**&#x200B;을(를) 추가하여 적응형 Forms의 위치를 지정하십시오.  기본적으로 값은 모든 적응형 Forms을 포함하는 `/content/forms/af/(.*)`입니다. 특정 적응형 양식의 경로를 지정할 수도 있습니다.
1. **[!UICONTROL 양식 데이터 모델 경로 패턴]**&#x200B;을(를) 추가하여 양식 데이터 모델(FDM)의 위치를 지정하십시오. 기본적으로 값은 모든 양식 데이터 모델(FDM)을 포함하는 `/content/dams/formsanddocuments-fdm/(.*)`입니다. 특정 FDM(양식 데이터 모델)에 대한 경로를 지정할 수도 있습니다.
1. 설정을 저장합니다.

추가된 구성은 서비스 호출 - 구성 팩터리&#x200B;]**옵션에 대한**[!UICONTROL &#x200B;양식 데이터 모델의 적응형 양식 수준 화이트리스트에 저장됩니다.

>[!VIDEO](https://video.tv.adobe.com/v/3423977/adaptive-forms-custom-function-rule-editor)

>[!NOTE]
>
> AEM Archetype 프로젝트를 통해 사용자 정의 함수를 사용하여 규칙 편집기에서 양식 데이터 모델(FDM)을 호출하려면 다음을 수행합니다.
>
>1. [구성 파일을 만듭니다](https://github.com/adobe/aem-core-forms-components/blob/master/it/config/src/main/content/jcr_root/apps/system/config/com.adobe.aemds.guide.factory.impl.AdaptiveFormFDMConfigurationFactoryImpl~core-components-it.cfg.json).
>1. getContentPathPattern 및 getFormDataModelPathPattern의 속성을 설정합니다.
>1. 프로젝트 배포.

## 관련 문서

{{af-submit-action}}

