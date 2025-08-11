---
title: 범용 편집기에서 양식에 대한 양식 데이터 모델(FDM)을 통합하는 방법은 무엇입니까?
description: 양식 데이터 모델(FDM)을 기반으로 에지 전달 서비스를 위한 양식을 만드는 방법을 알아봅니다. FDM의 데이터 모델 오브젝트에 대한 샘플 데이터를 생성하고 편집합니다.
feature: Edge Delivery Services, Form Data Model
role: Admin, User
exl-id: 9ce51223-57d0-47d8-8868-84b37d4e8e3e
source-git-commit: cfff846e594b39aa38ffbd3ef80cce1a72749245
workflow-type: tm+mt
source-wordcount: '716'
ht-degree: 31%

---


# 양식 데이터 모델(FDM)과 Forms 통합

FDM을 사용하여 양식을 백엔드 데이터 소스에 연결하여 데이터 바인딩, 유효성 검사 및 제출 워크플로우를 활성화합니다.

## 사전 요구 사항

FDM을 양식에 통합하기 전에 다음 단계를 완료합니다.

1. **[데이터 Source 구성](/help/forms/configure-data-sources.md)**: 백엔드 연결 설정
2. **[양식 데이터 모델 만들기](/help/forms/create-form-data-models.md)**: 데이터 구조 및 서비스 정의
3. **[데이터 모델 개체 구성](/help/forms/work-with-form-data-model.md)**: 데이터 관계 매핑

## 고려 사항

범용 편집기 인터페이스에서 **데이터 소스** 아이콘이 표시되지 않거나 오른쪽 속성 패널에서 **바인드 참조** 속성이 표시되지 않으면 **Extension Manager**&#x200B;에서 **데이터 소스** 확장 기능을 활성화하십시오.

![양식 통합을 위해 활성화할 수 있는 데이터 소스 확장을 포함하여 사용 가능한 확장을 보여 주는 범용 편집기 Extension Manager 인터페이스의 스크린샷](/help/edge/docs/forms/universal-editor/assets/extension-manager.png)

범용 편집기에서 확장 기능을 활성화하거나 비활성화하는 방법을 알아보려면 [Extension Manager 기능 하이라이트](https://developer.adobe.com/uix/docs/extension-manager/feature-highlights/#enablingdisabling-extensions) 문서를 참조하십시오.

## 양식 유형 선택

유니버설 편집기는 두 가지 양식 만들기 접근 방식을 지원합니다.

| 측면 | 스키마 기반 양식 | 스키마 기반이 아닌 양식 |
|--------|-------------------|----------------------|
| **설치 복잡성** | 단순(자동 바인딩) | 수동(필드별 바인딩) |
| **사용 사례** | 데이터 구조가 정의된 새 양식 | 기존 양식 또는 유연한 요구 사항 |
| **데이터 소스** | 생성 중 필요 | 나중에 추가할 수 있음 |
| **바인딩** | 자동 필드 바인딩 | 필드당 수동 바인딩 |

![범용 편집기의 양식 유형](/help/edge/docs/forms/universal-editor/assets/form-types.png){width="50%" align="center" height="50%"}

## 스키마 기반 양식

스키마 기반 양식은 데이터 소스를 자동으로 구성하고 양식 필드를 데이터에 바인딩합니다. 이 접근 방식은 데이터 구조가 잘 정의된 새 양식에 이상적입니다.

### 스키마 기반 양식 만들기

1. **Forms 콘솔에 액세스**
   - [!DNL Experience Manager Forms] 작성자 인스턴스에 로그인
   - **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Forms]** > **[!UICONTROL Forms 및 문서]**(으)로 이동

2. **양식 만들기 시작**
   - **[!UICONTROL 만들기]** > **[!UICONTROL 적응형 Forms]** 선택
   - Edge Delivery Services 템플릿 선택
   - 활성화되면 **[!UICONTROL 만들기]** 클릭

   ![Edge Delivery Services 템플릿](/help/edge/assets/create-eds-forms.png)

3. **데이터 모델 구성**
   - **데이터** 탭으로 이동
   - 여러 데이터 소스의 경우 **FDM(양식 데이터 모델)**&#x200B;을 선택하고 단일 백엔드 시스템의 경우 **JSON 스키마**&#x200B;을 선택합니다.
   - 생성된 FDM(예: Pet 양식 데이터 모델) 선택

   ![양식 데이터 모델 선택](/help/edge/docs/forms/universal-editor/assets/select-petstore-form-data-model.png)

4. **양식 설정 완료**
   - **이름** 및 **제목** 입력
   - **GitHub URL** 지정(예: `https://github.com/wkndforms/edsforms`)
   - **[!UICONTROL 만들기]**&#x200B;를 클릭합니다.

   ![스키마 기반 양식 만들기](/help/edge/docs/forms/universal-editor/assets/create-schema-based-form.png)

### 스키마 기반 양식 확인

양식이 사전 구성된 데이터 바인딩이 있는 유니버설 편집기에서 열립니다.

![미리 채워진 양식 필드가 있는 스키마 기반 양식과 사용 가능한 데이터 소스 요소를 표시하는 콘텐츠 브라우저를 보여 주는 범용 편집기의 스크린샷](/help/edge/docs/forms/universal-editor/assets/schema-based-form-in-ue.png)

![자동 데이터 바인딩](/help/edge/docs/forms/universal-editor/assets/schema-based-form-data-binding.png)

## 스키마 기반이 아닌 양식

비스키마 양식에는 수동 데이터 소스 구성 및 필드 바인딩이 필요합니다. 이 접근 방식은 기존 양식 또는 복잡한 요구 사항에 대한 유연성을 제공합니다.

### 비스키마 기반 양식 만들기

1. **양식 속성에 액세스**
   - [!DNL Experience Manager Forms] 작성자 인스턴스에 로그인
   - **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Forms]** > **[!UICONTROL Forms 및 문서]**(으)로 이동
   - 양식을 선택하고 **[!UICONTROL 속성]**&#x200B;을 클릭하세요.

   ![양식 속성 열기](/help/edge/docs/forms/universal-editor/assets/non-schema-based-edit-properties.png)

2. **양식 모델 구성**
   - **양식 모델** 탭을 엽니다.
   - **다음에서 선택** 드롭다운에서 **양식 데이터 모델(FDM)**&#x200B;을 선택합니다.
   - 목록에서 FDM 선택

   ![양식 모델 탭 선택](/help/edge/docs/forms/universal-editor/assets/select-form-model.png)

   ![FDM 선택](/help/edge/docs/forms/universal-editor/assets/select-fdm.png)

3. **구성 확인**
   - 경고 대화 상자에서 **확인**&#x200B;을 클릭합니다
   - **[!UICONTROL 저장 및 닫기]** 클릭

   ![양식 모델 마법사](/help/edge/docs/forms/universal-editor/assets/form-model-wizard.png)

### 데이터 요소 추가

1. **편집할 양식 열기**
   - 양식이 유니버설 편집기에서 열립니다

   ![스키마 기반이 아닌 양식 작성](/help/edge/docs/forms/universal-editor/assets/non-schema-form-authoring.png)

2. **데이터 Source 요소에 액세스**
   - **[!UICONTROL 콘텐츠 브라우저]**&#x200B;의 **[!UICONTROL 데이터 원본]** 탭으로 이동
   - FDM에서 사용 가능한 데이터 요소 보기

   ![양식 데이터 소스](/help/edge/docs/forms/universal-editor/assets/non-schema-data-source.png)

3. **양식에 요소 추가**
   - 데이터 요소를 선택하고 **[!UICONTROL 추가]**&#x200B;를 클릭합니다.
   - 또는 요소를 드래그 앤 드롭하여 양식을 작성하십시오.

   ![데이터 요소 추가](/help/edge/docs/forms/universal-editor/assets/non-schema-add-data-element.png)

   ![데이터 소스 탭에서 데이터 요소를 양식 구조로 드래그 앤 드롭하여 스키마 기반이 아닌 양식이 구축되는 범용 편집기를 보여 주는 스크린샷](/help/edge/docs/forms/universal-editor/assets/non-schema-form.png)

### 수동 데이터 바인딩 추가

기존 양식 필드의 경우 **바인드 참조** 속성을 통해 데이터 바인딩을 추가하십시오.

1. **필드 속성 열기**
   - 바인딩할 양식 필드 선택
   - 속성 패널을 엽니다.

2. **바인드 참조 구성**
   - **바인드 참조** 속성으로 이동
   - **찾아보기** 아이콘 클릭

   ![양식 필드에 대한 데이터 바인딩 수동 추가](/help/edge/docs/forms/universal-editor/assets/non-schema-add-data-binding.png)

3. **데이터 요소 선택**
   - **바인드 참조 선택** 마법사의 데이터 소스 트리에서 선택하십시오.
   - 원하는 데이터 요소를 선택하고 **선택**&#x200B;을 클릭합니다

   ![데이터 바인드 참조 선택](/help/edge/docs/forms/universal-editor/assets/select-bind-reference.png)

   ![데이터 요소 선택](/help/edge/docs/forms/universal-editor/assets/select-data-element.png)

4. **바인딩 확인**
   - 이제 양식 필드가 데이터 요소에 바인딩됩니다
   - 바인딩이 **바인딩 참조** 속성에 나타납니다.

   ![자동 데이터 바인딩](/help/edge/docs/forms/universal-editor/assets/schema-based-form-data-binding.png)

## 통합 확인

통합 완료 후:

1. **데이터 바인딩 테스트**: 양식 필드에 올바른 데이터가 표시되는지 확인
2. **제출 확인**: 구성된 소스에 데이터가 저장되었는지 확인
3. **오류 처리 확인**: 잘못된 데이터 시나리오가 있는 테스트

## 다음 단계

양식 워크플로우를 완료하려면 [작업 제출](/help/edge/docs/forms/universal-editor/submit-action.md)을 구성하십시오.
