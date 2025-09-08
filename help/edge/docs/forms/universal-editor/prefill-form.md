---
title: 적응형 양식 필드를 미리 채우는 방법
description: 기존 데이터를 사용하여 적응형 양식 필드를 미리 채웁니다. 사용자는 소셜 프로필로 로그인하여 양식의 기본 정보를 미리 채울 수 있습니다.
feature: Adaptive Forms, Edge Delivery Services
role: User, Developer
level: Beginner, Intermediate
time: 45-60 minutes
keywords: 적응형 양식 미리 채우기, 적응형 양식 Edge Delivery Services, 적응형 양식 자동 채우기
exl-id: 7b6224e2-a19c-4146-8545-0ce9d1da9b29
source-git-commit: edfefb163e2d48dc9f9ad90fa68809484ce6abb0
workflow-type: ht
source-wordcount: '1787'
ht-degree: 100%

---

# Edge Delivery Services를 사용하여 적응형 양식에서 미리 채우기 서비스 구성

양식 미리 채우기는 사용자가 양식을 여는 즉시 외부 소스의 관련 데이터로 양식 필드를 자동으로 채우는 프로세스입니다. 사용자 프로필, 데이터베이스, 저장된 초안 또는 기타 백엔드 시스템의 정보를 활용하여 미리 채우기는 수동 입력을 줄이고 오류를 최소화하며 완료 속도를 높여 양식 작성 경험을 간소화합니다. 이렇게 하면 사용자 만족도가 향상될 뿐만 아니라 성공적인 양식 제출 가능성도 높아집니다.

## 양식 미리 채우기의 이점

| 이점 | 설명 |
|---------|-------------|
| **더 빠른 완료** | 수동 데이터 입력을 줄여 사용자가 양식을 빠르게 작성하도록 돕습니다. |
| **개선된 사용자 경험**: | 특히 재방문 사용자에게 양식이 더욱 개인화되고 편리하게 느껴지도록 합니다. |
| **더 높은 전환율** | 필요한 사용자 노력을 최소화하여 양식 포기율을 줄입니다. |
| **입력 오류 감소** | 신뢰할 수 있는 소스의 데이터는 오타 및 잘못된 항목을 줄입니다. |
| **더 나은 데이터 품질** | 백엔드 시스템에 대해 구조화되고 정확하며 일관된 데이터를 보장합니다. |

## 미리 채우기 작동 방식

다음 다이어그램은 사용자가 적응형 양식을 열 때 발생하는 자동 미리 채우기 프로세스를 보여 줍니다.

![양식 미리 채우기 프로세스 플로우](/help/edge/docs/forms/universal-editor/assets/prefill-process-flow.svg)

미리 채우기 프로세스에는 네 가지 주요 단계가 포함됩니다.

1. **사용자가 양식 열기**: 사용자가 URL 또는 탐색을 통해 적응형 양식에 액세스합니다.
1. **데이터 소스 식별**: 미리 채우기 서비스는 구성된 데이터 소스(양식 데이터 모델 또는 초안 서비스)를 결정합니다.
1. **데이터 검색**: 시스템이 컨텍스트, 매개변수 또는 사용자 식별을 기반으로 관련 사용자 데이터를 가져옵니다.
1. **매핑 및 디스플레이**: `bindRef` 속성을 사용하여 데이터가 양식 필드에 매핑되고 채워진 양식이 사용자에게 표시됩니다.

이 자동화된 프로세스를 통해 사용자는 관련 정보로 미리 채워진 양식을 확인하여 사용자 경험과 양식 완료율을 크게 향상할 수 있습니다.

## 미리 채우기를 위한 데이터 구조

적응형 양식은 두 가지 유형의 필드를 지원합니다.

- **바운드 필드**: 비어 있지 않은 `bindRef` 속성을 사용하여 데이터 소스에 연결된 필드입니다.
- **언바운드 필드**: `bindRef` 값이 비어 있는 독립 실행형 필드입니다.

미리 채우기 데이터 구조에는 다음이 포함됩니다.

- **afBoundData**: 바운드 필드 및 패널에 대한 데이터가 포함됩니다.
- **afUnBoundData**: 언바운드 필드에 대한 데이터가 포함됩니다.

데이터 형식은 양식 모델과 일치해야 합니다.

- **XFA 양식**: XFA 템플릿 스키마와 호환되는 XML입니다.
- **XML 스키마 양식**: 스키마 구조와 일치하는 XML
- **JSON 스키마 형식**: 스키마와 호환되는 JSON입니다.
- **양식 데이터 모델(FDM) 양식**: FDM 구조와 일치하는 JSON입니다.
- **스키마 없는 양식**: 모든 필드가 바인딩 해제되며 바인딩 해제된 XML을 사용합니다.

## 사전 요구 사항

미리 채우기 서비스를 구성하기 전에 다음을 확인해야 합니다.

### 필수 설정

- [Edge Delivery Services에 대해 구성된 GitHub 저장소](/help/edge/docs/forms/universal-editor/getting-started-universal-editor.md#create-a-new-aem-project-pre-configured-with-adaptive-forms-block)
- [프로젝트에 추가된 적응형 양식 블록](/help/edge/docs/forms/universal-editor/getting-started-universal-editor.md#add-adaptive-forms-block-to-your-existing-aem-project)
- [구성된 데이터 소스](/help/forms/configure-data-sources.md)
- [양식 데이터 모델(FDM) 작성됨](/help/forms/create-form-data-models.md)

### 액세스 요구 사항

- AEM Forms as a Cloud Service에 대한 액세스
- 양식 만들기 및 편집 권한
- 필요한 확장 기능 활성화된 범용 편집기 액세스

>[!TIP]
>
> 또한 범용 편집기에서 양식을 편집하여 양식 데이터 모델(FDM)을 통합하고 다양한 백엔드 소스에서 데이터를 가져올 수도 있습니다. 자세한 내용은 [범용 편집기에서 양식 데이터 모델과 양식 통합](/help/edge/docs/forms/universal-editor/integrate-forms-with-data-source.md) 문서를 참조하십시오.

## 미리 채우기 서비스 옵션

범용 편집기는 두 가지 미리 채우기 서비스 옵션을 제공합니다.

| 서비스 유형 | 용도 | 데이터 소스 | 적합한 대상 |
|--------------|---------|-------------|----------|
| **양식 포털 초안 미리 채우기** | 부분적으로 작성된 양식을 다시 작성합니다. | Forms 포털에 초안이 저장됩니다. | 불완전한 애플리케이션을 계속합니다. |
| **양식 데이터 모델 미리 채우기** | 외부 시스템의 필드를 채웁니다. | FDM을 통한 백엔드 데이터베이스 | 사용자 프로필 데이터 자동 채우기 |

### 상세 비교

| 기능 | 초안 미리 채우기 서비스 | FDM 미리 채우기 서비스 |
|---------|----------------------|---------------------|
| **인증** | 초안 액세스를 위해 사용자 로그인이 필요합니다. | 데이터 소스를 기반으로 구성 가능합니다. |
| **설정 복잡성** | 최소 구성 | FDM 설정 및 매핑이 필요합니다. |
| **데이터 유형** | 정적으로 저장된 데이터 | 실시간 동적 데이터 |
| **사용 사례** | 저장된 애플리케이션 다시 시작 | 사용자 프로필 또는 데이터베이스에서 미리 채우기 |


## 양식에 대한 미리 채우기 서비스 구성

+++1단계: 양식 데이터 모델 설정

### 1단계: 양식 데이터 모델 생성

1. AEM Forms as a Cloud Service 인스턴스에 로그인합니다.
1. **Adobe Experience Manager** > **Forms** > **데이터 통합**&#x200B;으로 이동합니다.
1. **만들기** > **양식 데이터 모델**&#x200B;을 선택합니다.
1. **데이터 소스 구성**&#x200B;을 선택하고 구성된 **데이터 소스**&#x200B;를 선택합니다.

   ![작성된 양식 데이터 모델](/help/edge/docs/forms/universal-editor/assets/create-fdm.png)

   >[!TIP]
   >
   >양식 데이터 모델 생성을 만드는 방법에 대한 자세한 내용은 [양식 데이터 모델 만들기](/help/forms/create-form-data-models.md)를 참조하십시오.

### 2단계: FDM 서비스 구성

1. **Adobe Experience Manager** > **Forms** > **데이터 통합**&#x200B;으로 이동합니다.
1. 편집 모드에서 양식 데이터 모델을 엽니다.
1. 데이터 모델 오브젝트를 선택하고 **속성 편집**&#x200B;을 클릭합니다.
1. 선택한 데이터 모델 오브젝트에 대한 **읽기** 및 **쓰기** 서비스를 구성합니다.

   ![읽기 쓰기 서비스 구성](/help/edge/docs/forms/universal-editor/assets/configure-reda-write-service.png)

1. 서비스 인수를 구성합니다.

   - 읽기 서비스 인수에 대한 편집 아이콘을 클릭합니다.
   - 인수를 **사용자 프로필 속성**, **요청 속성** 또는 **리터럴 값**&#x200B;에 바인딩합니다.
   - 바인딩 값(예: 펫 등록 양식의 경우 `petid`)을 지정합니다.

   ![펫 ID 인수 구성](/help/edge/docs/forms/universal-editor/assets/pet-id-arguments.png)

1. **완료**&#x200B;를 클릭하여 인수를 저장하고, **저장**&#x200B;을 클릭하여 FDM을 저장합니다.

   >[!NOTE]
   >
   > [양식 데이터 모델(FDM)을 사용하여 작업](/help/forms/work-with-form-data-model.md)에서 FDM 서비스 구성에 대해 자세히 알아봅니다.

+++

+++2단계: 적응형 양식 만들기 및 구성

### 3단계: 적응형 양식 만들기

1. **Adobe Experience Manager** > **양식** > **양식 및 문서**&#x200B;로 이동합니다.
1. **만들기** > **적응형 양식**&#x200B;을 선택합니다.
1. **소스** 탭에서 Edge Delivery Services 기반 템플릿을 선택합니다.

   ![Edge Delivery Services 템플릿](/help/edge/assets/create-eds-forms.png)

1. **만들기**&#x200B;를 클릭하여 **양식 생성** 마법사를 엽니다.
1. 양식 세부 사항을 지정합니다.

   - **이름**: 양식에 대한 설명적인 이름을 입력합니다.
   - **제목**: 사용자 친화적인 제목을 제공합니다.
   - **GitHub URL**: 저장소 URL(예: `https://github.com/wkndforms/edsforms`)을 입력합니다.

1. **만들기**&#x200B;를 클릭합니다.

   ![스키마 기반 양식 만들기](/help/edge/docs/forms/universal-editor/assets/create-schema-based-form1.png)

작성용 범용 편집기에서 양식이 열립니다.

### 4단계: 양식 데이터 소스 구성

1. 양식을 선택하고 **속성**&#x200B;을 클릭합니다.

   ![양식 속성 선택](/help/edge/docs/forms/universal-editor/assets/select-form-properties1.png)

2. **양식 모델** 탭을 엽니다.
3. **다음에서 선택** 드롭다운에서 **양식 데이터 모델(FDM)**&#x200B;을 선택합니다.
4. 드롭다운에서 생성된 양식 데이터 모델(예: PetFDM)을 선택합니다.

   ![양식 모델 탭 선택](/help/edge/docs/forms/universal-editor/assets/select-form-model1.png)

5. **저장 및 닫기**&#x200B;를 클릭합니다.
6. 편집을 위해 범용 편집기에서 양식을 엽니다.

FDM의 양식 요소는 **콘텐츠 브라우저**&#x200B;의 **데이터 소스** 탭에 표시됩니다.

### 5단계: 양식 필드에 데이터 바인딩 추가

1. **데이터 소스** 탭에서 데이터 요소를 선택합니다.
2. **추가**&#x200B;를 클릭하거나 요소를 드래그 앤 드롭하여 양식을 작성합니다.

   ![스키마 기반 양식을 보여 주는 범용 편집기의 스크린샷](/help/edge/docs/forms/universal-editor/assets/ue-form.png)

3. 양식 필드에 데이터 바인딩을 추가합니다.

   - 양식 필드를 선택합니다.
   - **속성** 패널에서 **바인딩 참조** 속성을 찾습니다.
   - 적절한 데이터 바인딩 참조를 선택합니다.

     ![데이터 바인딩](/help/edge/docs/forms/universal-editor/assets/schema-based-form-data-binding1.png)

+++

+++3단계: 미리 채우기 서비스 구성하기

### 6단계: 필수 확장 기능 활성화

범용 편집기에서 다음 확장 기능이 활성화되어 있는지 확인합니다.

1. **AEM 양식 속성 확장 기능**

   - 범용 편집기에서 **Extension Manager**&#x200B;를 엽니다.
   - **AEM 양식 속성** 확장 기능을 활성화합니다.

   ![양식 속성 아이콘](/help/edge/docs/forms/universal-editor/assets/form-edit-properties.png)

1. **데이터 소스 확장 기능**

   - **데이터 소스** 아이콘이 표시되지 않으면 **데이터 소스** 확장 기능을 활성화합니다.

   ![범용 편집기 Extension Manager의 스크린샷](/help/edge/docs/forms/universal-editor/assets/extension-manager.png)

   >[!TIP]
   >
   > 확장 기능 관리에 대한 자세한 내용은 [Extension Manager 기능 하이라이트](https://developer.adobe.com/uix/docs/extension-manager/feature-highlights/#enablingdisabling-extensions)를 참조하십시오.

### 7단계: 미리 채우기 서비스 구성

1. 범용 편집기에서 적응형 양식을 엽니다.
2. **AEM 양식 속성** 확장 기능 아이콘을 클릭합니다.

   ![양식 속성 아이콘 선택](/help/edge/docs/forms/universal-editor/assets/select-fdm-properties-icon.png)

3. **미리 채우기** 탭을 클릭합니다.
4. **양식 데이터 모델 미리 채우기 서비스**&#x200B;를 선택합니다.

   ![미리 채우기 서비스 선택](/help/edge/docs/forms/universal-editor/assets/select-fdm-prefill.png)

5. **저장 및 닫기**&#x200B;를 클릭합니다.

+++

+++4단계: 미리 채우기 구성 테스트

### 8단계: 미리보기 및 테스트

1. **Forms** > **양식 및 문서로 이동**
2. 적응형 양식을 선택합니다.
3. **HTML로 미리보기**&#x200B;를 선택합니다.
4. URL에 매개변수를 추가하여 미리 채우기를 테스트합니다.

   https://your-preview-url.com?`<bindreferencefield>`=`<value>`

   **예:**

   https://your-preview-url.com?petid=12345

   ![양식 미리 채우기](/help/edge/docs/forms/universal-editor/assets/prefill-form.png)

제공된 매개변수를 기반으로 데이터가 자동으로 양식에 채워집니다.

+++

## 예

### 샘플 미리 채우기 데이터 구조

**FDM 기반 양식에 대한 JSON 예시:**

```
  {
    "afBoundData": {
      "user": {
        "firstName": "John",
        "lastName": "Doe",
        "email": "john.doe@example.com",
        "phone": "+1-555-0123"
      }
    },
    "afUnBoundData": {
      "additionalInfo": "User preferences loaded"
    }
  }
```

**XFA 기반 양식에 대한 XML 예시:**

```
  <?xml version="1.0" encoding="UTF-8"?>
  <afData>
    <afBoundData>
      <user>
        <firstName>John</firstName>
        <lastName>Doe</lastName>
        <email>john.doe@example.com</email>
      </user>
    </afBoundData>
  </afData>
```

### 미리 채우기 URL 예시

아래 URL은 일러스트레이션 목적으로만 사용되었으며, 그대로 작동하지 않습니다. 미리 채우기 기능을 테스트할 때 호스트와 매개변수를 사용자 환경에 맞는 것으로 교체합니다.

**기본 미리 채우기 테스트:**

`https://preview.example.com/form.html?userId=12345`

**다중 매개변수 테스트:**

`https://preview.example.com/form.html?userId=12345&category=premium`


## 문제 해결

+++일반적인 문제 및 솔루션

| 문제 | 가능한 원인 | 솔루션 |
|-------|----------------|----------|
| **양식 필드가 미리 채워지지 않음** | 잘못된 `bindRef` 값 | `bindRef`가 FDM 필드 이름과 정확히 일치하는지 확인합니다. |
| **데이터 형식 오류** | 일치하지 않는 데이터 구조 | 미리 채우기 데이터가 양식 모델 스키마와 일치하는지 확인합니다. |
| **서비스를 찾을 수 없음** | FDM 구성 문제 | FDM 서비스가 올바르게 구성되고 저장되었는지 확인합니다. |
| **인증 오류** | 데이터 소스 연결 | 데이터 소스 자격 증명 및 연결을 확인합니다. |
| **부분 데이터 로드** | 필드 매핑 누락 | 모든 필수 필드에 적절한 데이터 바인딩이 있는지 확인합니다. |

+++

+++디버깅 단계

1. **FDM 구성 확인:**

   - 서비스가 올바르게 구성되었는지 확인합니다.
   - FDM 서비스를 독립적으로 테스트합니다.
   - 데이터 소스 연결의 유효성을 검사합니다.

2. **양식 구성 확인:**

   - 양식이 올바른 FDM과 연결되었는지 확인합니다.
   - 필드 `bindRef` 값의 유효성을 검사합니다.
   - 미리 채우기 없이 양식을 먼저 테스트합니다.

3. **데이터 플로우 테스트:**

   - 브라우저 개발자 도구를 사용하여 네트워크 요청을 검사합니다.
   - 콘솔에서 JavaScript 오류를 확인합니다.
   - 응답 데이터 형식의 유효성을 검사합니다.

4. **일반 오류 메시지**

   - “미리 채우기 서비스를 찾을 수 없습니다”: 서비스 구성을 확인합니다.
   - “데이터 바인딩에 실패했습니다”: `bindRef` 정확도를 확인합니다.
   - “잘못된 데이터 형식”: 데이터가 스키마와 일치하는지 확인합니다.

+++

## 모범 사례

+++구성 모범 사례

- **설명적인 이름 지정 사용**: FDM 및 서비스의 이름을 명확하게 지정합니다.
- **데이터 스키마의 유효성 검사**: 데이터 구조가 양식 요구 사항과 일치하는지 확인합니다.
- **점진적으로 테스트**: 한 번에 하나의 필드를 구성하고 테스트합니다.
- **문서 매핑**: 필드-데이터 매핑을 추적합니다.

+++

+++성능 최적화

- **데이터 볼륨 최소화**: 필요한 필드만 미리 채웁니다.
- **캐싱 사용**: 자주 액세스하는 데이터에 대해 적절한 캐싱을 구성합니다.
- **쿼리 최적화**: 데이터베이스 쿼리가 효율적인지 확인합니다.
- **성능 모니터링**: 미리 채우기 기능을 활성화하여 양식 로드 시간을 추적합니다.

+++

+++보안 고려 사항

- **입력 매개변수 유효성 검사**: 항상 URL 매개변수의 유효성을 검사합니다.
- **데이터 정리**: 양식을 미리 채우기 전에 데이터를 정리합니다.
- **액세스 제어 구현**: 사용자가 자신의 데이터에만 액세스할 수 있는지 확인합니다.
- **HTTPS 사용**: 데이터 전송에 항상 보안 연결을 사용합니다.

+++

+++사용자 경험 지침

- **피드백 제공**: 데이터 가져오기 중 로딩 표시기를 표시합니다.
- **오류를 정상적으로 처리**: 도움이 되는 오류 메시지를 표시합니다.
- **무시 허용**: 사용자가 미리 채워진 데이터를 수정할 수 있도록 허용합니다.
- **일관성 유지**: 여러 양식에서 일관된 미리 채우기 비헤이비어를 사용합니다.

+++

## 자주 묻는 질문

+++미리 채우기가 제대로 작동하는지 테스트하려면 어떻게 해야 합니까?

양식을 미리 본 다음 `?<bindreferencefield>=<value>` 형식을 사용하여 미리 채우기 매개변수를 URL에 추가합니다. 필드에 데이터 구조와 일치하는 유효한 `bindRef`가 있는지 확인합니다. 브라우저 개발자 도구를 사용하여 네트워크 요청을 검사하고 데이터가 올바르게 가져와지는지 확인합니다.

+++

+++적응형 양식을 미리 채우는 데 지원되는 데이터 형식은 무엇입니까?

적응형 양식은 양식 모델에 따라 여러 형식을 지원합니다.

- **XFA 양식**: XFA 스키마와 일치하는 XML
- **JSON 스키마 형식**: 스키마와 호환되는 JSON 데이터
- **FDM 양식**: 데이터 모델 구조에 매핑되는 JSON
- **XML 스키마 양식**: 스키마 구조와 일치하는 XML

+++

+++바운드 및 언바운드 필드를 모두 미리 채울 수 있습니까?

예. 두 가지 유형의 필드를 모두 미리 채울 수 있습니다. 바운드 필드는 `afBoundData` 섹션을 사용하며 양식 모델 스키마와 일치해야 합니다. 언바운드 필드는 `afUnBoundData` 섹션을 사용하며 추가 데이터를 포함할 수 있습니다.

+++

+++일부 필드만 미리 채워지는 경우 어떻게 해야 합니까?

모든 필드에 FDM과 정확히 일치하는 올바른 `bindRef` 값이 있는지 확인합니다. 데이터 소스에 필요한 모든 필드가 포함되어 있고 데이터 구조가 양식 모델 스키마와 일치하는지 확인합니다.

+++

+++하나의 양식에서 여러 미리 채우기 서비스를 사용할 수 있습니까?

양식당 하나의 기본 미리 채우기 서비스를 구성할 수 있습니다. 그러나 단일 양식 데이터 모델 내에서 다른 데이터 소스를 결합하여 유사한 기능을 구현할 수 있습니다.

+++

+++미리 채우기 서비스에 대한 인증은 어떻게 처리합니까?

인증은 데이터 소스 구성에 따라 다릅니다. FDM 기반 미리 채우기의 경우 데이터 소스 설정에서 인증을 구성합니다. 초안 미리 채우기의 경우 사용자는 일반적으로 저장된 초안에 액세스하기 위해 로그인해야 합니다.

+++



## 관련 항목

- [범용 편집기에서 양식 데이터 모델과 양식 통합](/help/edge/docs/forms/universal-editor/integrate-forms-with-data-source.md)
- [양식 데이터 모델 만들기](/help/forms/create-form-data-models.md)
- [양식 데이터 모델(FDM)을 사용하여 작업](/help/forms/work-with-form-data-model.md)
- [데이터 소스 구성](/help/forms/configure-data-sources.md)
- [AEM Forms용 Edge Delivery Services 시작하기](/help/edge/docs/forms/universal-editor/getting-started-universal-editor.md)
