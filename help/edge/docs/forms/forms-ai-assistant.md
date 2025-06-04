---
title: AEM Forms용 AI Assistant(Forms Experience Builder)
description: 양식 조각을 사용하여 강력한 양식을 더 빠르게 제작
feature: Edge Delivery Services
hide: true
hidefromtoc: true
role: Admin, Architect, Developer
exl-id: a8d64082-a23f-4919-ad66-042faad77d29
source-git-commit: ab071b9159f3d4db275313080d7c14a46096c4de
workflow-type: tm+mt
source-wordcount: '1141'
ht-degree: 1%

---

# AEM Forms용 AI Assistant(Forms Experience Builder)

>[!NOTE]
>
>
> AEM Forms용 AI Assistant(Forms Experience Builder) 기능은 **얼리어답터 프로그램**&#x200B;에서 사용할 수 있습니다. 관심이 있는 경우, 기능에 대한 액세스를 요청하려면 회사 주소에서 mailto:aem-forms-ea@adobe.com으로 빠른 이메일을 보내십시오.

>[!IMPORTANT]
>
> **변경될 수 있는 설명서**: 이 설명서는 현재 제품에 대해 테스트 중이며 업데이트 및 개정이 적용됩니다. AEM Forms용 AI Assistant가 얼리어답터 프로그램 동안 계속 발전함에 따라 기능, 명령 및 예제가 변경될 수 있습니다.

AEM Forms용 AI Assistant는 양식 생성 방법을 혁신합니다. 즉, 필요한 사항을 자연어로 설명하고 양식이 실제로 작동하는 것을 지켜볼 수 있습니다. Forms 관리 UI, 적응형 Forms 편집기 및 유니버설 편집기에서 사용할 수 있으며, 사용자의 의도를 이해하고 원하는 내용을 정확하게 빌드합니다.

## 시작하기: 간단히 설명

AI 비서는 아는 동료와 대화하는 것처럼 작동합니다. 복잡한 메뉴와 설정을 학습하는 대신 만들려는 항목을 간단히 설명합니다.

### 빠른 시작

소개 비디오를 통해 빠르게 시작하고 실행:

>[!VIDEO](https://video.tv.adobe.com/v/3463164/)

### AI Assistant 액세스

AEM Forms의 세 위치에서 AI Assistant에 액세스할 수 있습니다.

1. **Forms 관리 UI**
   - Adobe Experience Manager > Forms > Forms 및 문서로 이동합니다.
   - 인터페이스 왼쪽에 있는 AI Assistant 아이콘을 찾습니다
   - 아이콘을 클릭하여 AI 지원 패널을 엽니다

   ![AI Assistant 아이콘*](/help/edge/docs/forms/assets/forms-manager.gif){width="50%"}

2. **적응형 Forms 편집기**
   - Adobe Experience Manager > Forms > Forms 및 문서로 이동합니다.
   - 편집할 양식 선택 및 열기
   - 편집기 인터페이스에서 AI Assistant 아이콘을 클릭합니다

   ![AI Assistant 아이콘*](/help/edge/docs/forms/assets/adaptive-forms-editor.gif){width="75%"}

3. **범용 편집기**

   - Adobe Experience Manager > Forms > Forms 및 문서로 이동합니다.
   - 인터페이스 왼쪽에 있는 AI Assistant 아이콘을 찾습니다
   - 편집기 인터페이스에서 AI Assistant 아이콘을 클릭합니다

### 시작 방법: 간단한 대화

AI Assistant를 시작하는 가장 좋은 방법은 자연어를 사용하는 것입니다. 방법은 다음과 같습니다.

**필요한 사항을 설명하세요.**

- &quot;내 웹 사이트에 대한 연락처 양식 만들기&quot;
- &quot;등급 스케일이 포함된 고객 피드백 양식이 필요합니다.&quot;
- &quot;예정된 이벤트에 대한 등록 양식 작성&quot;
- &quot;제품 만족도에 대한 간단한 설문 조사 만들기&quot;

**이동 중 세부 정보 추가:**

- &quot;이름, 이메일, 전화 및 메시지 필드가 있는 연락처 양식 만들기&quot;
- &quot;전화 회의에 대한 여러 단계 등록 양식이 필요합니다.&quot;
- &quot;별 5개 등급 및 댓글 섹션이 포함된 고객 피드백 양식 작성&quot;

**기존 필드 참조:**

- &quot;이메일 필드를 필수로 설정&quot;(@email)
- &quot;전화 번호 필드에 유효성 검사 추가&quot;(@phoneNumber)
- &quot;결혼을 선택한 경우에만 배우자 정보 표시&quot;(@spouseInfo 및 @maritalStatus)

### 수행할 수 있는 작업

자연어 외에도 AI 어시스턴트는 상호 작용하는 추가 방법을 제공합니다.

- **파일 업로드**: 이미지, PDF 또는 Fi그마 디자인을 첨부하여 AI에 원하는 내용을 표시합니다.
- **빠른 명령 사용**: 일반적인 작업에 사용할 수 있는 바로 가기를 보려면 `/`을(를) 입력하십시오.
- **특정 필드 참조**: `@fieldName`을(를) 사용하여 기존 양식 필드(예: `@firstName`, `@emailAddress`)를 수정하십시오.

## 만들 수 있는 사항: 작동하는 예제

다음은 간단한 자연어로 수행할 수 있는 작업의 실제 예입니다.

### 새 양식 시작

**간단한 방법:**

```
"Create a contact form"
```

**자세한 접근 방식:**

```
"Create a professional contact form for a law firm with fields for name, email, phone, case type, and message. Make it mobile-friendly."
```

**디자인 참조:**

```
"Create a contact form based on the attached design mockup. Include all the fields shown in the layout."
```

### 양식 요소 추가

**기본 추가 항목:**

```
"Add a section for personal information"
"Include a file upload for resume"
"Add a dropdown for country selection"
```

**세부 사양:**

```
"Add a personal information panel with fields for full name, date of birth, phone number, and email address"
"Include a secure file upload component for documents, limited to PDF files under 5MB"
"Add a country dropdown with options for USA, Canada, UK, and Germany"
```

### 동적 비헤이비어 만들기

**단순 논리:**

```
"Show additional fields when 'Other' is selected"
"Make the email field required"
"Calculate the total automatically"
```

**복잡한 비즈니스 규칙:**

```
"Show the spouse information fields only when marital status is set to 'Married'"
"Calculate the total cost by multiplying quantity and price, then add 10% tax"
"Enable the submit button only when all required fields are completed and terms are accepted"
```

### 양식 레이아웃 및 디자인

**레이아웃 변경:**

```
"Make this a multi-step form"
"Organize fields in two columns"
"Convert to an accordion layout"
```

**디자인 개선 사항:**

```
"Create a wizard-style form with 3 steps: personal info, preferences, and review"
"Arrange the address fields in a compact two-column layout"
"Update the layout to match the attached wireframe"
```

### 제출 및 통합

**기본 제출:**

```
"Send form data to our email"
"Save responses to a spreadsheet"
"Redirect to a thank you page"
```

**고급 통합:**

```
"Send form submissions to hr@company.com and create a case in our CRM system"
"Submit data to our REST API endpoint and trigger the new customer workflow"
"Email responses to the sales team and add the lead to our marketing automation platform"
```

## 첨부 파일 작업

파일을 업로드하여 AI가 원하는 내용을 정확히 이해할 수 있도록 합니다.

### 지원되는 파일 유형

| 파일 유형 | 다음에 대한 우수 사례 | 사용 예 |
|-----------|----------|-------------|
| **이미지**(PNG, JPG, GIF) | 양식 레이아웃, UI mockups, 종이 양식 스캔 | &quot;이 레이아웃과 일치하는 양식 만들기&quot; |
| **PDF 파일** | 변환할 기존 양식, 사양 | &quot;이 PDF 양식을 디지털로 변환&quot; |
| **그림 파일** | 디자인 프로토타입, 브랜드 지침 | &quot;내 Figma 디자인에서 이 양식 작성&quot; |
| **디자인 파일** | 시각적 참조, 스타일 가이드 | &quot;이 디자인의 스타일 일치&quot; |

### 첨부 파일 사용 방법

1. AI Assistant 인터페이스에서 **첨부 파일 아이콘 클릭**
2. 장치에서 **파일 선택**
3. 첨부 파일을 참조하는 **원하는 내용을 설명**:
   - &quot;첨부된 이 PDF을 기반으로 양식 만들기&quot;
   - &quot;이 이미지의 레이아웃과 일치하는 연락처 양식 작성&quot;
   - &quot;이 종이 양식을 디지털 버전으로 변환&quot;

### 첨부 파일 관련 우수 사례

- 더 나은 AI 분석을 위해 **선명한 고품질 이미지 사용**
- **첨부 파일당 하나의 개념에 집중**(레이아웃, 스타일 등)
- 첨부 파일과 함께 **원하는 항목 설명**
- 최적의 처리를 위해 **파일을 10MB 미만으로 유지**

## 최상의 결과를 위한 팁

### 단순하게 시작, 위로

- 기본 요청으로 시작: &quot;연락처 양식 만들기&quot;
- 세부 사항을 점진적으로 추가: &quot;이메일 필드에 유효성 검사 추가&quot;
- 테스트 및 세분화: &quot;전화 필드를 선택 사항으로 설정&quot;

### 필요한 경우 구체화

- 대신: &quot;보기 좋게 만들기&quot;
- 시도: &quot;전문적인 색상과 깨끗한 타이포그래피 사용&quot;

### 자연어 사용

- 대신: &quot;텍스트 입력 구성 요소 추가&quot;
- 시도: &quot;이름에 대한 필드 추가&quot;

### 기존 요소 참조

- 기존 필드에 `@fieldName`을(를) 사용합니다. &quot;필수 @email 만들기&quot;
- 필드 이름을 구체적으로 지정하십시오. &quot;@phoneNumber 필드 업데이트&quot;

### 복잡한 요청 분류

- 하나의 큰 요청 대신 여러 개의 작은 요청을 시도하십시오.
- 단계별 양식 작성
- 다음 단계로 이동하기 전에 각 변경 사항 테스트

## 제품 도움말 및 학습

AI 어시스턴트는 또한 AEM Forms 기능에 대해 가르쳐 줄 수 있습니다.

### 질문하기:

- &quot;여러 단계 양식을 만들려면 어떻게 해야 합니까?&quot;
- &quot;패널과 섹션의 차이점은 무엇입니까?&quot;
- &quot;이메일 알림을 설정하려면 어떻게 해야 합니까?&quot;
- &quot;모바일 친화적 인 양식에 대한 우수 사례는 무엇입니까?&quot;
- &quot;양식에 테마를 적용하려면 어떻게 해야 합니까?&quot;

### 다음에 대한 도움말 보기:

- AEM Forms 개념 및 용어
- 복잡한 기능에 대한 단계별 지침
- 모범 사례 및 권장 사항
- 일반적인 문제 해결

## 고급 기능 참조

고급 기능을 살펴보려는 사용자의 경우:

### 빠른 명령

사용 가능한 바로 가기를 보려면 `/`을(를) 입력하십시오.

| 명령 | 용도 | 예 |
|---------|---------|---------|
| `/create-form` | 새 양식 시작 | `/create-form customer survey` |
| `/add-form` | 유니버설 편집기에서 양식 추가 | `/add-form contact form` |
| `/update-layout` | 양식 구조 변경 | `/update-layout wizard with 3 steps` |
| `/update-field` | 필드 속성 수정 | `/update-field @email to be required` |
| `/create-rule` | 동적 동작 추가 | `/create-rule show @spouse if married` |
| `/create-panel` | 필드 컨테이너 추가 | `/create-panel Personal Information` |
| `/configure-submit` | 양식 제출 설정 | `/configure-submit to email support` |
| `/help` | 지원 받기 | `/help multi-step forms` |

### 필드 참조 구문

기존 필드를 참조하려면 `@fieldName`을(를) 사용하십시오.

- `@firstName` - 이름 필드
- `@email` - 전자 메일 필드
- `@phoneNumber` - 전화 번호 필드
- `@dateOfBirth` - 생년월일 필드

### 구성 요소 유형

최상의 결과를 얻으려면 다음 용어를 사용하십시오.

- `text input` - 한 줄 텍스트 필드
- `text area` - 여러 줄 텍스트 필드
- `dropdown` - 목록 선택
- `checkbox` - 단일 확인란
- `checkbox group` - 여러 확인란
- `radio group` - 라디오 단추 그룹
- `date picker` - 날짜 선택
- `file upload` - 첨부 파일
- `panel` - 필드 그룹화를 위한 컨테이너

## 문제 해결

### 일반적인 문제 및 솔루션

**AI 길잡이가 응답하지 않음:**

- 인터넷 연결 확인
- 지원되는 환경에 있는지 확인합니다.
- AI 지원 패널을 닫았다가 다시 엽니다.

**예기치 않은 결과:**

- 요청을 보다 구체적으로 고쳐 보십시오.
- 복잡한 요청을 더 작은 단계로 나누기
- 표준 AEM Forms 용어 사용

**필드 참조가 작동하지 않음:**

- 필드 이름의 철자가 표시되는 것과 정확히 일치하는지 확인
- 기존 필드에 `@fieldName` 구문 사용
- 참조하기 전에 필드가 있는지 확인하십시오.

**디자인 가져오기 문제:**

- 파일이 명확하고 잘 구성되어 있는지 확인합니다.
- 지원되는 형식 사용(PDF, PNG, JPG, Figma)
- 파일 크기가 10MB 미만인지 확인합니다.

## 피드백 및 지원

AI Assistant 개선 지원:

- **피드백 제공**: AI Assistant 인터페이스의 피드백 단추를 사용하십시오.
- **문제 보고**: 공식 채널을 통해 Adobe 지원 센터에 문의하십시오.
- **경험 공유**: 입력한 내용을 통해 도우미를 모든 사람에게 더 잘 제공할 수 있습니다.

## 관련 리소스

[AEM Forms AI Assistant - 프롬프트 라이브러리](/help/edge/docs/forms/ai-assistant-prompt-library.md)
