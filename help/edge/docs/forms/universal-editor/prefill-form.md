---
title: 적응형 양식 필드를 미리 채우는 방법
description: 기존 데이터를 사용하여 적응형 양식의 필드를 미리 채웁니다. 사용자는 소셜 프로필로 로그인하여 양식에 기본 정보를 미리 채울 수 있습니다.
feature: Adaptive Forms, Edge Delivery Services
role: User, Developer
level: Beginner, Intermediate
time: 45-60 minutes
keywords: 적응형 양식 미리 채우기, 적응형 양식 에지 전달 서비스, 적응형 양식 자동 채우기
source-git-commit: 6c93af923e600dbb20add6c5f1053c832d5a5ca0
workflow-type: tm+mt
source-wordcount: '1829'
ht-degree: 3%

---


# Edge Delivery Services을 사용하여 적응형 Forms에서 미리 채우기 서비스 구성

양식 미리 채우기는 사용자가 양식을 여는 즉시 외부 소스의 관련 데이터로 양식 필드를 자동으로 채우는 프로세스입니다. 미리 채우기를 통해 사용자 프로필, 데이터베이스, 저장된 초안 또는 기타 백엔드 시스템의 정보를 활용함으로써 양식 작성 환경을 간소화하여 수동 입력 감소, 오류 최소화 및 완료 시간 단축을 실현합니다. 이는 사용자 만족도를 향상시킬 뿐만 아니라 양식 제출이 성공할 가능성도 높입니다.

## 양식 미리 채우기의 이점

| 이익 | 설명 |
|---------|-------------|
| **더 빠른 완료** | 수동 데이터 입력 감소, 사용자가 양식을 신속하게 작성 |
| **향상된 사용자 환경** | Forms은 특히 재방문 사용자에게 보다 개인화되고 편리함을 느낄 수 있습니다 |
| **높은 전환율** | 필요한 사용자 작업을 최소화하여 양식 포기 감소 |
| **입력 오류 감소** | 신뢰할 수 있는 소스의 데이터가 오타 및 잘못된 항목을 줄임 |
| **데이터 품질 개선** | 백엔드 시스템을 위한 정형화되고 정확하며 일관된 데이터 보장 |

## 미리 채우기 작동 방식

다음 다이어그램은 사용자가 적응형 양식을 열 때 발생하는 자동 미리 채우기 프로세스를 보여 줍니다.

![양식 미리 채우기 프로세스 흐름](/help/edge/docs/forms/universal-editor/assets/prefill-process-flow.svg)

미리 채우기 프로세스에는 다음 네 가지 주요 단계가 포함됩니다.

1. **사용자가 양식을 엽니다**: 사용자가 URL 또는 탐색을 통해 적응형 양식에 액세스합니다
2. **데이터 Source 식별**: 미리 채우기 서비스가 구성된 데이터 원본(양식 데이터 모델 또는 초안 서비스)을 결정합니다.
3. **데이터 검색**: 시스템은 컨텍스트, 매개 변수 또는 사용자 식별을 기반으로 관련 사용자 데이터를 가져옵니다
4. **매핑 및 표시**: 데이터가 `bindRef` 속성을 사용하여 양식 필드에 매핑되고 채워진 양식이 사용자에게 표시됩니다.

이러한 자동화된 프로세스를 통해 사용자는 관련 정보로 미리 채워진 양식을 볼 수 있으므로 사용자 경험과 양식 완료율이 크게 향상됩니다.

## 미리 채우기를 위한 데이터 구조

적응형 Forms은 두 가지 유형의 필드를 지원합니다.

- **바인딩된 필드**: 비어 있지 않은 `bindRef` 속성으로 데이터 원본에 연결된 필드
- **바인딩되지 않은 필드**: `bindRef` 값이 비어 있는 독립 실행형 필드

미리 채우기 데이터 구조에는 다음이 포함됩니다.

- **afBoundData**: 바인딩된 필드 및 패널에 대한 데이터를 포함합니다.
- **afUnBoundData**: 바인딩되지 않은 필드에 대한 데이터를 포함합니다.

데이터 형식은 양식 모델과 일치해야 합니다.

- **XFA 양식**: XML이 XFA 템플릿 스키마를 준수합니다.
- **XML 스키마 양식**: 스키마 구조와 일치하는 XML
- **JSON 스키마 양식**: 스키마와 호환되는 JSON
- **FDM(양식 데이터 모델) 양식**: FDM 구조와 일치하는 JSON
- **스키마 없는 양식**: 모든 필드가 바인딩되지 않았으며 바인딩되지 않은 XML을 사용합니다.


## 사전 요구 사항

미리 채우기 서비스를 구성하기 전에 다음을 확인하십시오.

### 필수 설정

- [Edge Delivery Services용으로 구성된 GitHub 저장소](/help/edge/docs/forms/universal-editor/getting-started-universal-editor.md#create-a-new-aem-project-pre-configured-with-adaptive-forms-block)
- [적응형 Forms 블록이 프로젝트에 추가됨](/help/edge/docs/forms/universal-editor/getting-started-universal-editor.md#add-adaptive-forms-block-to-your-existing-aem-project)
- [데이터 소스 구성됨](/help/forms/configure-data-sources.md)
- [양식 데이터 모델(FDM) 생성됨](/help/forms/create-form-data-models.md)

### 액세스 요구 사항

- AEM Forms as a Cloud Service 액세스
- 양식 만들기 및 편집 권한
- 필수 확장이 활성화된 유니버설 편집기 액세스

>[!TIP]
>
> 양식을 편집하여 범용 편집기에서 FDM(양식 데이터 모델)을 통합하여 다양한 백엔드 소스에서 데이터를 가져올 수도 있습니다. 자세한 내용은 [범용 편집기에서 양식 데이터 모델과 양식 통합](/help/edge/docs/forms/universal-editor/integrate-forms-with-data-source.md) 문서를 참조하십시오.

## 미리 채우기 서비스 옵션

범용 편집기는 두 가지 미리 채우기 서비스 옵션을 제공합니다.

| 서비스 유형 | 용도 | 데이터 소스 | 가장 적합한 형식 |
|--------------|---------|-------------|----------|
| **양식 포털 초안 미리 채우기** | 부분적으로 완료된 양식 다시 시작 | Forms 포털에 저장된 초안 | 불완전한 응용 프로그램 계속 |
| **양식 데이터 모델 미리 채우기** | 외부 시스템에서 필드 채우기 | FDM을 통한 백엔드 데이터베이스 | 사용자 프로필 데이터 자동 채우기 |

### 세부 비교

| 기능 | 초안 미리 채우기 서비스 | FDM 미리 채우기 서비스 |
|---------|----------------------|---------------------|
| **인증** | 초안 액세스를 위해 사용자 로그인 필요 | 데이터 소스를 기반으로 구성 가능 |
| **설치 복잡성** | 최소 구성 | FDM 설정 및 매핑 필요 |
| **데이터 형식** | 정적 저장 데이터 | 실시간 동적 데이터 |
| **사용 사례** | 저장된 응용 프로그램 다시 시작 | 사용자 프로필 또는 데이터베이스에서 미리 채우기 |


## 양식에 대한 미리 채우기 서비스 구성


+++1단계: 양식 데이터 모델 설정

### 1단계: 양식 데이터 모델 만들기

1. AEM Forms as a Cloud Service 인스턴스에 로그인합니다
2. **Adobe Experience Manager** > **Forms** > **데이터 통합**(으)로 이동
3. **만들기** > **양식 데이터 모델** 선택
4. **데이터 Source 구성**&#x200B;을 선택하고 구성된 **데이터 Source**&#x200B;을(를) 선택하십시오.

   ![양식 데이터 모델을 만들었습니다](/help/edge/docs/forms/universal-editor/assets/create-fdm.png)

   >[!TIP]
   >
   > 양식 데이터 모델을 만드는 방법에 대한 자세한 지침은 [양식 데이터 모델 만들기](/help/forms/create-form-data-models.md)를 참조하십시오.

### 2단계: FDM 서비스 구성

1. **Adobe Experience Manager** > **Forms** > **데이터 통합**(으)로 이동
2. 편집 모드에서 양식 데이터 모델 열기
3. 데이터 모델 개체를 선택하고 **속성 편집**&#x200B;을 클릭합니다.
4. 선택한 데이터 모델 개체에 대해 **읽기** 및 **쓰기** 서비스 구성

   ![읽기 쓰기 서비스 구성](/help/edge/docs/forms/universal-editor/assets/configure-reda-write-service.png)

5. 서비스 인수 구성:
   - 읽기 서비스 인수에 대한 편집 아이콘을 클릭합니다
   - 인수를 **사용자 프로필 특성**, **요청 특성** 또는 **리터럴 값**&#x200B;에 바인딩합니다.
   - 바인딩 값(예: pet 등록 양식의 경우 `petid`) 지정

   ![pet id 인수 구성](/help/edge/docs/forms/universal-editor/assets/pet-id-arguments.png)

6. 인수를 저장하려면 **완료**&#x200B;를 클릭하고 FDM을 저장하려면 **저장**&#x200B;을 클릭합니다

   >[!NOTE]
   >
   > [FDM(양식 데이터 모델)을 사용하여 작업](/help/forms/work-with-form-data-model.md)에서 FDM 서비스를 구성하는 방법에 대해 자세히 알아보십시오.

+++

+++2단계: 적응형 양식 만들기 및 구성

### 3단계: 적응형 양식 만들기

1. **Adobe Experience Manager** > **Forms** > **Forms 및 문서**(으)로 이동
1. **만들기** > **적응형 Forms** 선택
1. **Source** 탭에서 Edge Delivery Services 템플릿을 선택합니다.

   ![Edge Delivery Services 템플릿](/help/edge/assets/create-eds-forms.png)

1. **만들기**&#x200B;를 클릭하여 **양식 만들기** 마법사를 엽니다.
1. 양식 세부 사항 지정:

   - **이름**: 양식에 대한 수사적 이름을 입력하십시오.
   - **제목**: 사용자에게 친숙한 제목을 제공합니다.
   - **GitHub URL**: 저장소 URL(예: `https://github.com/wkndforms/edsforms`) 입력

1. **만들기**&#x200B;를 클릭합니다.

   ![스키마 기반 양식 만들기](/help/edge/docs/forms/universal-editor/assets/create-schema-based-form1.png)

작성용 범용 편집기에서 양식이 열립니다.

### 4단계: 양식 데이터 Source 구성

1. 양식을 선택하고 **속성**&#x200B;을 클릭하세요.

   ![양식 속성 선택](/help/edge/docs/forms/universal-editor/assets/select-form-properties1.png)

2. **양식 모델** 탭을 엽니다.
3. **다음에서 선택** 드롭다운에서 **양식 데이터 모델(FDM)**&#x200B;을 선택합니다.
4. 드롭다운에서 만든 양식 데이터 모델(예: PetFDM)을 선택합니다

   ![양식 모델 탭 선택](/help/edge/docs/forms/universal-editor/assets/select-form-model1.png)

5. **저장 및 닫기** 클릭
6. 유니버설 편집기에서 편집할 양식 열기

FDM의 양식 요소가 **콘텐츠 브라우저**&#x200B;의 **데이터 소스** 탭에 나타납니다.

### 5단계: 양식 필드에 데이터 바인딩 추가

1. **데이터 원본** 탭에서 데이터 요소 선택
2. **추가**&#x200B;를 클릭하거나 요소를 드래그 앤 드롭하여 양식을 작성하세요.

   ![스키마 기반 양식을 보여주는 유니버설 편집기의 스크린샷](/help/edge/docs/forms/universal-editor/assets/ue-form.png)

3. 양식 필드에 데이터 바인딩 추가:

   - 양식 필드 선택
   - **속성** 패널에서 **바인드 참조** 속성을 찾습니다
   - 적절한 데이터 바인딩 참조를 선택합니다

     ![데이터 바인딩](/help/edge/docs/forms/universal-editor/assets/schema-based-form-data-binding1.png)

+++

+++3단계: 미리 채우기 서비스 구성

### 6단계: 필요한 확장 활성화

범용 편집기에서 다음 확장이 활성화되어 있는지 확인합니다.

1. **AEM 양식 속성 확장**

   - 유니버설 편집기에서 **Extension Manager** 열기
   - **AEM 양식 속성** 확장 사용

   ![양식 속성 아이콘](/help/edge/docs/forms/universal-editor/assets/form-edit-properties.png)

1. **데이터 Source 확장**

   - **데이터 원본** 아이콘이 보이지 않는 경우 **데이터 원본** 확장 사용

   ![범용 편집기 Extension Manager의 스크린샷](/help/edge/docs/forms/universal-editor/assets/extension-manager.png)

   >[!TIP]
   >
   > 확장 관리에 대한 자세한 지침은 [Extension Manager 기능 하이라이트](https://developer.adobe.com/uix/docs/extension-manager/feature-highlights/#enablingdisabling-extensions)를 참조하십시오.

### 7단계: 미리 채우기 서비스 구성

1. 범용 편집기에서 적응형 양식 열기
2. **AEM 양식 속성** 확장 아이콘을 클릭합니다.

   ![양식 속성 선택 아이콘](/help/edge/docs/forms/universal-editor/assets/select-fdm-properties-icon.png)

3. **미리 채우기** 탭을 클릭합니다.
4. **양식 데이터 모델 미리 채우기 서비스 선택**

   ![미리 채우기 서비스 선택](/help/edge/docs/forms/universal-editor/assets/select-fdm-prefill.png)

5. **저장 및 닫기** 클릭

+++

+++4단계: 미리 채우기 구성 테스트

### 8단계: 미리보기 및 테스트

1. **Forms** > **Forms 및 문서**(으)로 이동
2. 적응형 양식 선택
3. **HTML으로 미리 보기** 선택
4. URL에 매개 변수를 추가하여 미리 채우기 테스트:

   https://your-preview-url.com?&lt;bindreferencefield>=&lt;value>

   **예:**

   https://your-preview-url.com?petid=12345

   ![양식 미리 채우기](/help/edge/docs/forms/universal-editor/assets/prefill-form.png)

제공된 매개 변수를 기반으로 양식이 자동으로 데이터로 채워집니다.

+++

## 예

### 샘플 미리 채우기 데이터 구조

FDM 기반 양식에 대한 **JSON 예:**

    &quot;
    
    &lbrace;
    &quot;afBoundData&quot;: &lbrace;
    &quot;user&quot;: &lbrace;
    &quot;firstName&quot;: &quot;John&quot;,
    &quot;lastName&quot;: &quot;Doe&quot;,
    &quot;email&quot;: &quot;john.doe@example.com&quot;,
    &quot;phone&quot;: &quot;+1-555-0123&quot;
    
    ,
    &quot;afUnBoundData&quot;: &lbrace;
    &quot;additionalInfo&quot;: &quot;사용자 환경 설정 로드됨&quot;
    &rbrace;
    
    
    &quot;

**XFA 기반 양식에 대한 XML 예:**

    &quot;
    
    &lt;?xml version=&quot;UTF-8&quot;?>
    &lt;afData>
    &lt;afBoundData>
    &lt;user>
    &lt;firstName>John&lt;/firstName>
    &lt;lastName>Doe&lt;/lastName>
    &lt;email>john.doe@example.com&lt;/email>
    &lt;/user>
    &lt;/afBoundData>
    &lt;/afData>
    
    &quot;

### 예제 미리 채우기 URL

아래 URL은 일러스트레이션용으로만 사용되며 그대로 작동하지 않습니다. 미리 채우기 기능을 테스트할 때 호스트 및 매개 변수를 사용자 환경과 관련된 것으로 바꿉니다.

**기본 미리 채우기 테스트:**

`https://preview.example.com/form.html?userId=12345`

**여러 매개 변수 테스트:**

`https://preview.example.com/form.html?userId=12345&category=premium`


## 문제 해결

+++일반적인 문제 및 솔루션

| 문제 | 가능한 원인 | 솔루션 |
|-------|----------------|----------|
| **미리 채우지 않는 양식 필드** | 잘못된 `bindRef` 값 | `bindRef`이(가) FDM 필드 이름과 정확히 일치하는지 확인 |
| **데이터 형식 오류** | 일치하지 않는 데이터 구조 | 미리 채우기 데이터가 양식 모델 스키마와 일치하는지 확인 |
| **서비스를 찾을 수 없음** | FDM 구성 문제 | FDM 서비스가 올바르게 구성 및 저장되었는지 확인 |
| **인증 오류** | 데이터 소스 연결 | 데이터 소스 자격 증명 및 연결 확인 |
| **부분 데이터 로드** | 필드 매핑 누락 | 모든 필수 필드에 적절한 데이터 바인딩이 있는지 확인합니다. |

+++

+++디버깅 단계

1. **FDM 구성 확인:**

   - 서비스가 올바르게 구성되었는지 확인
   - 독립적으로 FDM 서비스 테스트
   - 데이터 소스 연결 확인

2. **양식 구성 확인:**

   - 양식이 올바른 FDM과 연결되어 있는지 확인
   - 필드 `bindRef` 값 확인
   - 먼저 미리 채우지 않고 양식 테스트

3. **테스트 데이터 흐름:**

   - 브라우저 개발자 도구를 사용하여 네트워크 요청 검사
   - 콘솔에서 JavaScript 오류 확인
   - 응답 데이터 형식 유효성 검사

4. **일반적인 오류 메시지:**

   - &quot;미리 채우기 서비스를 찾을 수 없음&quot;: 서비스 구성 확인
   - &quot;데이터 바인딩 실패&quot;: `bindRef` 정확도 확인
   - &quot;잘못된 데이터 형식&quot;: 데이터가 스키마와 일치하는지 확인

+++

## 모범 사례

+++구성 모범 사례

- **설명 이름 지정 사용**: FDM과 서비스의 이름을 명확하게 지정합니다.
- **데이터 스키마 유효성 검사**: 데이터 구조가 양식 요구 사항과 일치하는지 확인
- **증분 테스트**: 한 번에 한 필드를 구성하고 테스트합니다.
- **문서 매핑**: 필드-데이터 매핑을 추적합니다.

+++

+++성능 최적화

- **데이터 볼륨 최소화**: 필요한 필드만 미리 채웁니다.
- **캐싱 사용**: 자주 액세스하는 데이터에 대한 적절한 캐싱 구성
- **쿼리 최적화**: 데이터베이스 쿼리가 효율적인지 확인
- **성능 모니터링**: 미리 채우기를 사용하여 양식 로드 시간을 추적합니다.

+++

+++보안 고려 사항

- **입력 매개 변수의 유효성 검사**: 항상 URL 매개 변수의 유효성을 검사하십시오.
- **데이터 정리**: 양식을 미리 채우기 전에 데이터 정리
- **액세스 제어 구현**: 사용자가 자신의 데이터에만 액세스할 수 있는지 확인
- **HTTPS 사용**: 항상 데이터 전송에 보안 연결을 사용합니다.

+++

+++사용자 경험 지침

- **피드백 제공**: 데이터를 가져오는 동안 로딩 지표를 표시합니다.
- **오류를 정상적으로 처리**: 유용한 오류 메시지 표시
- **재정의 허용**: 사용자가 미리 채워진 데이터를 수정하도록 허용
- **일관성 유지**: 양식에서 일관된 미리 채우기 동작을 사용합니다.

+++

## 자주 묻는 질문

+++미리 채우기가 제대로 작동하는지 테스트하려면 어떻게 해야 합니까?

`?<bindreferencefield>=<value>` 형식을 사용하여 양식을 미리 보고 미리 채우기 매개 변수를 URL에 추가하십시오. 필드에 데이터 구조와 일치하는 올바른 `bindRef`이(가) 있는지 확인하십시오. 브라우저 개발자 도구를 사용하여 네트워크 요청을 검사하고 데이터를 올바르게 가져오는지 확인하십시오.

+++

+++적응형 Forms 미리 채우기에 지원되는 데이터 형식은 무엇입니까?

적응형 Forms은 양식 모델에 따라 여러 형식을 지원합니다.

- **XFA 양식**: XFA 스키마와 일치하는 XML
- **JSON 스키마 양식**: 스키마와 호환되는 JSON 데이터
- **FDM 양식**: 데이터 모델 구조에 매핑되는 JSON
- **XML 스키마 양식**: 스키마 구조와 일치하는 XML

+++

+++바인딩된 필드와 바인딩되지 않은 필드를 모두 미리 채울 수 있습니까?

예, 두 가지 유형의 필드를 미리 채울 수 있습니다. 바인딩된 필드는 `afBoundData` 섹션을 사용하며 양식 모델 스키마와 일치해야 합니다. 바인딩되지 않은 필드는 `afUnBoundData` 섹션을 사용하며 추가 데이터를 포함할 수 있습니다.

+++

+++일부 필드만 미리 채우는 경우 어떻게 해야 합니까?

모든 필드에 FDM과 정확히 일치하는 올바른 `bindRef` 값이 있는지 확인하십시오. 데이터 소스에 모든 필수 필드가 포함되어 있는지, 데이터 구조가 양식 모델 스키마와 일치하는지 확인합니다.

+++

+++미리 채우기 서비스에 대한 인증을 처리하려면 어떻게 해야 합니까?

인증은 데이터 소스 구성에 따라 다릅니다. FDM 기반 미리 채우기의 경우 데이터 소스 설정에서 인증을 구성합니다. 초안 미리 채우기의 경우 일반적으로 저장된 초안에 액세스하려면 로그인해야 합니다.

+++

+++한 양식에서 여러 미리 채우기 서비스를 사용할 수 있습니까?

양식당 하나의 기본 미리 채우기 서비스를 구성할 수 있습니다. 그러나 단일 양식 데이터 모델 내에서 서로 다른 데이터 소스를 결합하여 유사한 기능을 수행할 수 있습니다.

+++

## 관련 항목

- [범용 편집기에서 양식 데이터 모델과 양식 통합](/help/edge/docs/forms/universal-editor/integrate-forms-with-data-source.md)
- [양식 데이터 모델 만들기](/help/forms/create-form-data-models.md)
- [양식 데이터 모델(FDM) 작업](/help/forms/work-with-form-data-model.md)
- [데이터 소스 구성](/help/forms/configure-data-sources.md)
- [AEM Forms용 Edge Delivery Services 시작하기](/help/edge/docs/forms/universal-editor/getting-started-universal-editor.md)
