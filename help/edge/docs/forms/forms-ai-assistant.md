---
title: AEM Forms용 AI 어시스턴트 (Forms Experience Builder)
description: 양식 조각을 사용하여 강력한 양식을 더 빠르게 제작
feature: Edge Delivery Services
hide: true
index: false
hidefromtoc: true
role: Admin, Architect, Developer
source-git-commit: 750674bbd29ec1b29388579d77c7c15bd89335ab
workflow-type: tm+mt
source-wordcount: '1145'
ht-degree: 97%

---


# AEM Forms용 AI Assistant 시작하기(Forms Experience Builder)

>[!NOTE]
>
>
> AEM Forms용 AI 어시스턴트(Forms Experience Builder) 기능은 **얼리 어답터 프로그램**&#x200B;에서 사용할 수 있습니다. 관심이 있는 경우 회사 주소에서 mailto:aem-forms-ea@adobe.com으로 빠른 전자 메일을 보내 기능에 대한 액세스를 요청하세요.

>[!IMPORTANT]
>
> **변경될 수 있는 설명서**: 이 설명서는 현재 제품과의 일치 여부를 테스트 중이며 업데이트 및 개정이 이루어질 수 있습니다. 얼리 어답터 프로그램이 진행되는 동안 AEM Forms용 AI 어시스턴트가 계속 발전함에 따라 기능, 명령 및 예제가 변경될 수 있습니다.

AEM Forms용 AI 어시스턴트는 양식을 만드는 방식을 혁신합니다. 자연어로 필요한 내용을 간단히 설명하면 양식이 실제로 구현됩니다. Forms 관리 UI, 적응형 양식 편집기 및 범용 편집기에서 사용할 수 있으며, 사용자의 의도를 이해하고 사용자가 원하는 것을 정확하게 구축합니다.

## 시작하기: 그냥 말하기

AI 어시스턴트는 지식이 풍부한 동료와 대화하는 것과 같이 작동합니다. 복잡한 메뉴와 설정을 배우는 대신, 만들고 싶은 것이 무엇인지 간단히 설명하면 됩니다.

### 빠른 시작

소개 비디오를 시청하여 빠르게 시작해 보십시오.

>[!VIDEO](https://video.tv.adobe.com/v/3463164/)

### AI 어시스턴트 액세스

AEM Forms의 세 가지 다른 위치에서 AI 어시스턴트에 액세스할 수 있습니다.

1. **Forms 관리 UI**
   - Adobe Experience Manager > 양식 > 양식 및 문서로 이동
   - 인터페이스 왼쪽에 있는 AI 어시스턴트 아이콘 찾기
   - 아이콘을 클릭하여 AI 어시스턴트 패널 열기

   ![AI 어시스턴트 아이콘*](/help/edge/docs/forms/assets/forms-manager.gif){width="50%"}

2. **적응형 양식 편집기**
   - Adobe Experience Manager > 양식 > 양식 및 문서로 이동
   - 편집할 양식 선택 및 열기
   - 편집기 인터페이스에서 AI 어시스턴트 아이콘 클릭

   ![AI 어시스턴트 아이콘*](/help/edge/docs/forms/assets/adaptive-forms-editor.gif){width="75%"}

3. **범용 편집기**

   - Adobe Experience Manager > 양식 > 양식 및 문서로 이동
   - 인터페이스 왼쪽에 있는 AI 어시스턴트 아이콘 찾기
   - 편집기 인터페이스에서 AI 어시스턴트 아이콘 클릭

### 시작 방법: 간단한 대화

AI 어시스턴트를 사용하는 가장 좋은 방법은 자연어를 사용하는 것입니다. 방법은 다음과 같습니다.

**필요한 것이 무엇인지 설명:**

- “내 웹 사이트를 위한 연락처 양식 만들기”
- “평가 척도가 포함된 고객 피드백 양식이 필요해”
- “다가오는 이벤트를 위한 등록 양식 작성”
- “제품 만족도에 대한 간단한 설문 조사 만들기”

**진행하면서 세부 정보 추가:**

- “이름, 이메일, 전화번호, 메시지 필드가 있는 연락처 양식 만들기”
- “컨퍼런스를 위한 여러 단계로 구성된 등록 양식이 필요해”
- “5점 만점 평가와 댓글 섹션을 포함된 고객 피드백 양식 만들기”

**기존 필드 참조**

- “이메일 필드를 필수로 만들기” (@email의 경우)
- “전화번호 필드에 유효성 검사 추가” (@phoneNumber의 경우)
- “기혼이 선택된 경우에만 배우자 정보 표시” (@spouseInfo 및 @maritalStatus의 경우)

### 가능한 추가 작업

자연어 외에도 AI 어시스턴트는 다음과 같은 추가적인 상호 작용 방식을 제공합니다.

- **파일 업로드**: 이미지, PDF 또는 Figma 디자인을 첨부하여 AI에게 구상하고 있는 내용 제시
- **빠른 명령 사용**: `/`를 입력하여 일반적인 작업에 사용 가능한 단축키 확인
- **특정 필드 참조**: `@fieldName`를 사용하여 기존 양식 필드(예: `@firstName`, `@emailAddress`) 수정

## 만들 수 있는 것: 효과적인 예제

다음은 간단한 자연어를 사용하여 실제로 만들 수 있는 예제입니다.

### 새로운 양식 시작

**간단한 접근 방식:**

```
"Create a contact form"
```

**더 자세한 접근 방식:**

```
"Create a professional contact form for a law firm with fields for name, email, phone, case type, and message. Make it mobile-friendly."
```

**디자인 참조 사용:**

```
"Create a contact form based on the attached design mockup. Include all the fields shown in the layout."
```

### 양식 요소 추가

**기본 추가:**

```
"Add a section for personal information"
"Include a file upload for resume"
"Add a dropdown for country selection"
```

**자세한 사양:**

```
"Add a personal information panel with fields for full name, date of birth, phone number, and email address"
"Include a secure file upload component for documents, limited to PDF files under 5MB"
"Add a country dropdown with options for USA, Canada, UK, and Germany"
```

### 동적 비헤이비어 만들기

**간단한 논리:**

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

파일을 업로드하여 AI가 정확히 원하는 바를 이해할 수 있도록 합니다.

### 지원되는 파일 유형

| 파일 유형 | 가장 적합한 형식 | 사용 예제 |
|-----------|----------|-------------|
| **이미지** (PNG, JPG, GIF) | 양식 레이아웃, UI 모형, 종이 양식 스캔 | “이 레이아웃과 일치하는 양식 만들기” |
| **PDF 파일** | 변환할 기존 양식, 사양 | “이 PDF 양식을 디지털로 변환” |
| **Figma 파일** | 디자인 프로토타입, 브랜드 가이드라인 | “내 Figma 디자인으로 이 양식 만들기” |
| **디자인 파일** | 시각적 참조, 스타일 가이드 | “이 디자인과 어울리게 스타일 설정” |

### 첨부 파일 사용 방법

1. AI 어시스턴트 인터페이스에서 **첨부 파일 아이콘 클릭**
2. 디바이스에서 **파일 선택**
3. 첨부 파일을 참조하여 **원하는 내용 설명**:
   - “첨부된 PDF를 기반으로 양식 만들기”
   - “이 이미지의 레이아웃과 일치하는 연락처 양식 만들기”
   - “이 종이 양식을 디지털 버전으로 변환”

### 첨부 파일 사용 모범 사례

- 더 나은 AI 분석을 위해 **선명한 고품질 이미지 사용**
- **첨부 파일당 하나의 콘셉트에 집중** (레이아웃, 스타일 등)
- 첨부 파일과 함께 **원하는 내용 설명**
- 최적의 처리를 위해 **파일 크기를 10MB 미만으로 유지**

## 최상의 결과를 위한 팁

### 간단하게 시작하고 확장하기

- 기본 요청부터 시작: “연락처 양식 만들기”
- 점진적으로 세부 정보 추가: “이메일 필드에 유효성 검사 추가”
- 테스트 및 개선: “전화번호 필드를 선택 사항으로 만들기”

### 필요할 때 구체적으로 말하기

- “디자인 개선” 대신
- “전문적인 색상과 깔끔한 타이포그래피 사용” 시도

### 자연어 사용

- “텍스트 입력 구성 요소 추가” 대신
- “이름 필드 추가” 시도

### 기존 요소 참조

- 기존 필드의 경우 `@fieldName` 사용: “@email을 필수로 설정”
- 필드 이름에 대해 구체적으로 설명: “@phoneNumber 필드 업데이트”

### 복잡한 요청 나누기

- 하나의 큰 요청 대신 여러 개의 작은 요청 시도
- 단계별로 양식 만들기
- 다음으로 넘어가기 전에 각 변경 사항 테스트

## 제품 도움말 및 학습

AI 어시스턴트는 AEM Forms 기능에 대해서도 알려 줄 수 있습니다.

### 다음과 같은 질문을 해보십시오.

- “여러 단계로 구성된 양식을 어떻게 만들까요?”
- “패널과 섹션의 차이점은 무엇인가요?”
- “이메일 알림을 어떻게 설정하나요?”
- “모바일 친화적인 양식을 만드는 가장 좋은 방법은 무엇인가요?”
- “양식에 테마를 적용하려면 어떻게 해야 하나요?”

### 도움말 보기:

- AEM Forms 개념 및 용어
- 복잡한 기능에 대한 단계별 지침
- 모범 사례 및 추천
- 일반적인 문제 해결

## 고급 기능 참조

고급 기능을 탐색하고자 하는 사용자의 경우:

### 빠른 명령

사용 가능한 단축키를 보려면 `/`를 입력하십시오.

| 명령 | 용도 | 예 |
|---------|---------|---------|
| `/create-form` | 새로운 양식 시작 | `/create-form customer survey` |
| `/add-form` | 범용 편집기에 양식 추가 | `/add-form contact form` |
| `/update-layout` | 양식 구조 변경 | `/update-layout wizard with 3 steps` |
| `/update-field` | 필드 속성 수정 | `/update-field @email to be required` |
| `/create-rule` | 동적 비헤이비어 추가 | `/create-rule show @spouse if married` |
| `/create-panel` | 필드 컨테이너 추가 | `/create-panel Personal Information` |
| `/configure-submit` | 양식 제출 설정 | `/configure-submit to email support` |
| `/help` | 도움 받기 | `/help multi-step forms` |

### 필드 참조 구문

기존 필드를 참조하려면 `@fieldName`를 사용하십시오.

- `@firstName` - 이름 필드
- `@email` - 이메일 필드
- `@phoneNumber` - 전화번호 필드
- `@dateOfBirth` - 생년월일 필드

### 구성 요소 유형

최상의 결과를 얻으려면 다음 용어를 사용하십시오.

- `text input` - 한 줄 텍스트 필드
- `text area` - 여러 줄 텍스트
- `dropdown` - 목록 선택
- `checkbox` - 단일 체크박스
- `checkbox group` - 여러 체크박스
- `radio group` - 라디오 버튼 그룹
- `date picker` - 날짜 선택
- `file upload` - 파일 첨부
- `panel` - 필드 그룹화를 위한 컨테이너

## 문제 해결

### 일반적인 문제 및 솔루션

**AI 어시스턴트가 응답하지 않음:**

- 인터넷 연결 확인
- 지원되는 환경에 있는지 확인
- AI 어시스턴트 패널을 닫았다가 다시 열기

**예기치 않은 결과:**

- 요청을 더 구체적으로 변경
- 복잡한 요청을 더 작은 단계로 나누기
- 표준 AEM Forms 용어 사용

**필드 참조가 작동하지 않음:**

- 필드 이름이 표시된 대로 정확하게 철자가 지정되었는지 확인
- 기존 필드의 경우 `@fieldName` 구문 사용
- 참조하기 전에 필드가 존재하는지 확인

**디자인 가져오기 문제:**

- 파일이 명확하고 잘 구성되어 있는지 확인
- 지원되는 형식(PDF, PNG, JPG, Figma) 사용
- 파일 크기가 10MB 미만인지 확인

## 피드백 및 지원

AI 어시스턴트 개선에 도움 주기:

- **피드백 제공**: AI 어시스턴트 인터페이스의 피드백 버튼을 사용하십시오.
- **문제 보고**: 공식 채널을 통해 Adobe 지원 팀에 문의하십시오.
- **경험 공유**: 여러분의 피드백은 어시스턴트를 모두에게 더 나은 도구로 만드는데 도움이 됩니다.

## 관련 리소스

[AEM Forms AI 어시스턴트 - 프롬프트 라이브러리](/help/edge/docs/forms/ai-assistant-prompt-library.md)
