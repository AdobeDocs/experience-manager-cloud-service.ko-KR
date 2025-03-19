---
title: 범용 편집기에서 양식에 대해 FDM(양식 데이터 모델)을 통합하는 방법을 선택하십시오.
description: 양식 데이터 모델(FDM)을 기반으로 양식을 만드는 방법을 알아봅니다. FDM에서 데이터 모델 개체에 대한 샘플 데이터를 생성하고 편집합니다.
feature: Edge Delivery Services, Form Data Model
role: Admin, User
hide: true
hidefromtoc: true
exl-id: 9ce51223-57d0-47d8-8868-84b37d4e8e3e
source-git-commit: 381aad580762fe957e1dc1d5824e4d35098f1ca4
workflow-type: tm+mt
source-wordcount: '1036'
ht-degree: 7%

---

# 범용 편집기에서 양식 데이터 모델과 양식 통합

범용 편집기에서 양식을 양식 데이터 모델(FDM)과 통합하면 다양한 백엔드 데이터 소스를 사용하여 양식 데이터 모델(FDM)을 만들 수 있습니다. FDM(양식 데이터 모델)을 다양한 양식 워크플로우에서 스키마로 사용할 수 있습니다. 데이터 소스를 구성하고 데이터 소스에서 사용할 수 있는 데이터 모델 개체 및 서비스를 기반으로 양식 데이터 모델(FDM)을 만듭니다.

## 고려 사항

* 유니버설 편집기의 양식에 대한 미리 채우기 서비스는 현재 지원되지 않습니다.

## 전제 조건

범용 편집기에서 양식 데이터 모델을 사용하여 양식을 구성하기 전에 다음 단계를 완료했는지 확인하십시오.

* [데이터 Source 구성](/help/forms/configure-data-sources.md): 양식을 백엔드 데이터에 연결하도록 데이터 소스를 설정합니다.
* [FDM(양식 데이터 모델) 만들기](/help/forms/create-form-data-models.md): 구성된 데이터 원본의 데이터 개체 및 서비스를 사용하여 데이터 모델을 만듭니다.
* [데이터 모델 개체 및 서비스 구성](/help/forms/work-with-form-data-model.md): 데이터 모델 개체 및 서비스를 매핑하여 양식과 데이터 원본 간의 원활한 데이터 흐름을 보장합니다.

## 범용 편집기에서 양식 데이터 모델로 Forms 만들기

유니버설 편집기에서 다음을 만들 수 있습니다.
* [스키마 기반 양식](#schema-based-form): 스키마 기반 양식은 **데이터** 탭에서 양식을 만드는 동안 구성된 데이터 원본을 사용하여 데이터를 양식 필드에 자동으로 바인딩합니다.
* [비스키마 기반 양식](#non-schema-based-form): 비스키마 기반 양식을 사용하려면 데이터 소스를 수동으로 추가하고 콘텐츠 트리에서 각 필드를 바인딩해야 합니다.

![유니버설 편집기의 양식 유형](/help/edge/docs/forms/universal-editor/assets/form-types.png){width="50%" align="center" height="50%"}

이러한 방법을 사용하면 필요에 따라 데이터 모델을 양식과 유연하게 연결할 수 있습니다.

### 스키마 기반 양식

스키마 기반 양식을 만들면 데이터 소스로 자동으로 구성되며 양식 필드는 데이터 바인딩을 통해 데이터에 이미 연결되어 있습니다. 양식 만들기 마법사를 사용하여 스키마 기반 양식을 만들려면 다음 단계를 수행하십시오.

1. [!DNL Experience Manager Forms] 작성자 인스턴스에 로그인합니다.
2. Experience Manager 로그인 페이지에서 자격 증명을 입력합니다. 로그인 후 왼쪽 상단 모서리에서 **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Forms]** > **[!UICONTROL Forms 및 문서]**&#x200B;를 선택합니다.
3. **[!UICONTROL 만들기]** > **[!UICONTROL 적응형 Forms]**&#x200B;을(를) 선택합니다. 마법사가 열립니다. **Source** 탭에서 템플릿을 선택합니다.

   ![Edge Delivery Services 템플릿](/help/edge/assets/create-eds-forms.png)

   Edge Delivery Services 기반 템플릿을 선택하면 **[!UICONTROL 만들기]** 단추가 활성화됩니다. **[!UICONTROL 데이터 Source]** 또는 **[!UICONTROL 제출]** 탭으로 이동하여 데이터 원본을 선택하거나 작업을 제출할 수 있습니다.

4. **데이터** 탭에서 다음 데이터 모델 중 하나를 선택할 수 있습니다.

   * **양식 데이터 모델(FDM)**: 데이터 소스의 데이터 모델 개체와 서비스를 양식에 통합합니다. 양식에 여러 소스에서 데이터를 읽고 써야 하는 경우 양식 데이터 모델(FDM)을 선택합니다.

   * **JSON 스키마**: 데이터 구조를 정의하는 JSON 스키마를 연결하여 양식을 백엔드 시스템과 통합합니다. 스키마 요소를 사용하여 다이내믹 콘텐츠를 추가할 수 있습니다.

     예를 들어 Pet 양식 데이터 모델이라는 작성된 양식 데이터 모델을 선택합니다.

     ![양식 데이터 모델 선택](/help/edge/docs/forms/universal-editor/assets/select-petstore-form-data-model.png)


     기본적으로 연결된 JSON 스키마 또는 양식 데이터 모델(FDM)의 모든 필드가 자동으로 선택되고 해당 양식 구성 요소로 변환되므로 작성 프로세스가 단순해집니다. 또한 마법사를 사용하면 확인란을 사용하여 양식에 포함할 필드를 선택적으로 선택할 수 있습니다.

5. **[!UICONTROL 만들기]**&#x200B;를 클릭하면 **양식 만들기** 마법사가 나타납니다.
6. **이름** 및 **제목**&#x200B;을 지정하십시오.
7. **GitHub URL**&#x200B;을 지정합니다. 예를 들어 GitHub 저장소의 이름이 `edsforms`이고 `wkndforms` 계정 아래에 있는 경우 URL은 다음과 같습니다.
   `https://github.com/wkndforms/edsforms`
8. **[!UICONTROL 만들기]**&#x200B;를 클릭합니다.

   ![스키마 기반 양식 만들기](/help/edge/docs/forms/universal-editor/assets/create-schema-based-form.png)

   **[!UICONTROL 만들기]**&#x200B;를 클릭하자마자 범용 편집기에서 작성할 양식이 열립니다.

   ![작성자 양식](/help/edge/docs/forms/universal-editor/assets/schema-based-form-in-ue.png)

   폼은 연결된 데이터 소스의 데이터 요소를 사용하여 만들어집니다. 폼 필드에는 미리 구성된 데이터 바인딩이 있습니다.

   ![자동 데이터 바인딩](/help/edge/docs/forms/universal-editor/assets/schema-based-form-data-binding.png)

   이제 양식에 대해 및 [제출 액션을 구성](/help/edge/docs/forms/universal-editor/submit-action.md)할 수 있습니다.

### 비스키마 기반 양식

스키마 기반이 아닌 양식을 만들 때 데이터 소스가 구성되지 않습니다. 나중에 양식 속성을 편집하여 데이터 소스를 추가하고 양식 필드에 대한 데이터 바인딩을 수동으로 구성할 수 있습니다. 양식 속성을 편집하고 데이터 소스를 추가하려면 다음 단계를 수행하십시오.

1. [!DNL Experience Manager Forms] 작성자 인스턴스에 로그인합니다.
1. Experience Manager 로그인 페이지에서 자격 증명을 입력합니다. 로그인 후 왼쪽 상단 모서리에서 **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Forms]** > **[!UICONTROL Forms 및 문서]**&#x200B;를 선택합니다.
1. 데이터 원본을 추가할 양식을 선택하고 **[!UICONTROL 속성]**을 클릭합니다.
   ![양식 속성 열기](/help/edge/docs/forms/universal-editor/assets/non-schema-based-edit-properties.png)

   양식 속성이 열립니다.
1. **양식 모델** 탭을 열고 **다음에서 선택** 드롭다운 메뉴에서 클릭합니다. 다음 옵션 중 하나를 선택할 수 있습니다.

   * **양식 데이터 모델(FDM)**: 양식 데이터 모델을 사용하여 양식을 만듭니다.
   * **커넥터**: Adobe Marketo 데이터 원본을 사용하여 양식을 만듭니다.
   * **스키마**: AEM Forms에 업로드된 JSON 스키마를 사용하여 양식을 만듭니다.
   * **없음**: 양식 모델을 사용하지 않고 처음부터 양식을 만듭니다.

     예를 들어 양식 데이터 모델(FDM)을 선택합니다

     ![양식 모델 탭 선택](/help/edge/docs/forms/universal-editor/assets/select-form-model.png)

1. 드롭다운 목록에서 생성된 양식 데이터 모델(FDM)을 선택합니다. 예를 들어, 드롭다운 목록에서 Pet 양식 데이터 모델이라는 작성된 양식 데이터 모델을 선택합니다.

   ![FDM 선택](/help/edge/docs/forms/universal-editor/assets/select-fdm.png)

   양식 데이터 모델(FDM)을 선택하면 경고 대화 상자가 나타납니다. 대화 상자를 닫으려면 **확인**&#x200B;을 클릭하세요.

   ![양식 모델 마법사](/help/edge/docs/forms/universal-editor/assets/form-model-wizard.png)

1. **[!UICONTROL 저장 및 닫기]**&#x200B;를 클릭합니다.
1. 편집할 양식을 엽니다. 작성을 위해 유니버설 편집기에서 양식이 열립니다.

   ![비스키마 기반 양식 작성](/help/edge/docs/forms/universal-editor/assets/non-schema-form-authoring.png)

   연결된 양식 데이터 모델(FDM)에 있는 양식 요소는 **속성 패널**&#x200B;에 있는 **[!UICONTROL 콘텐츠 브라우저]**&#x200B;의 **[!UICONTROL 데이터 소스]** 탭에 표시됩니다.

   ![양식 데이터 Source](/help/edge/docs/forms/universal-editor/assets/non-schema-data-source.png)

1. **[!UICONTROL 데이터 원본]** 탭에서 데이터 요소를 선택하고 **[!UICONTROL 추가]**&#x200B;를 클릭합니다.

   ![데이터 요소 추가](/help/edge/docs/forms/universal-editor/assets/non-schema-add-data-element.png)

   이러한 요소를 드래그 앤 드롭하여 적응형 양식을 작성할 수도 있습니다. **[!UICONTROL 추가]**&#x200B;를 클릭하면 **[!UICONTROL 데이터 원본]** 탭에서 선택한 요소가 양식에 추가되고 추가된 요소 앞에 눈금 표시가 나타납니다.

   ![양식 작성](/help/edge/docs/forms/universal-editor/assets/non-schema-form.png)

   양식 요소의 **바인드 참조** 속성에서 데이터 바인딩을 지정하여 수동으로 양식 요소에 추가해야 합니다.
예를 들어 다음 양식에 이미 있는 **Pet 이름** 텍스트 상자에 데이터 바인딩 참조를 추가하겠습니다.

   ![양식 필드에 수동으로 데이터 바인딩 추가](/help/edge/docs/forms/universal-editor/assets/non-schema-add-data-binding.png)

   이제 양식에 대해 및 [제출 액션을 구성](/help/edge/docs/forms/universal-editor/submit-action.md)할 수 있습니다.

## 추가 참조

{{universal-editor-see-also}}
