---
title: Forms Experience Builder 시작하기
description: Forms Experience Builder를 사용하여 모든 사용자 유형에 대한 점진적 공개가 포함된 양식을 만들고 관리하는 방법을 알아봅니다
feature: Edge Delivery Services
hide: true
index: false
hidefromtoc: true
role: Admin, Architect, Developer
exl-id: da429952-ccc0-4579-a243-8bddeb73a0fb
source-git-commit: 8be2b09200af58c701721b3e8537ea5e6cc3e4a2
workflow-type: tm+mt
source-wordcount: '1720'
ht-degree: 15%

---

# Forms Experience Builder 시작하기

>[!NOTE]
>
> Forms Experience Builder 기능은 **얼리어답터 프로그램**&#x200B;에서 사용할 수 있습니다. 필요한 경우 회사 주소에서 `aem-forms-ea@adobe.com`(으)로 빠른 전자 메일을 보내 기능에 대한 액세스를 요청하세요.

>[!IMPORTANT]
>
> **변경될 수 있는 설명서**: 이 설명서는 현재 제품과의 일치 여부를 테스트 중이며 업데이트 및 개정이 이루어질 수 있습니다. Forms Experience Builder가 얼리어답터 프로그램 동안 계속 발전함에 따라 기능, 명령 및 예가 변경될 수 있습니다.

이 포괄적인 안내서는 대화형 AI 기술을 사용하여 양식을 만들고 관리하는 데 도움이 됩니다. 첫 번째 양식을 만들려는 초보자든 고급 기능을 활용하려는 고급 사용자든 상세 정보 및 실제 사례를 통해 Forms Experience Builder의 기능을 통해 여정에게 안내할 수 있습니다.

## 사전 요구 사항 및 설정

### &#x200B;1. 액세스 요청

Forms Experience Builder에 대한 액세스 권한이 없는 경우:

1. **액세스 요청**: 회사 전자 메일에서 [aem-forms-ea@adobe.com](mailto:aem-forms-ea@adobe.com)(으)로 전자 메일 보내기
2. **정보 포함**: 조직 이름 및 프로젝트 세부 정보
3. **승인 대기**: Adobe에서 온보딩 지침을 검토하고 제공합니다.

### &#x200B;2. Forms이 활성화되었는지 확인

Forms Experience Builder를 사용하기 전에 [환경에 대해 AEM Forms이 활성화되어 있는지 확인](/help/forms/setup-forms-cloud-service.md)하십시오.


### &#x200B;3. 환경 설정


* **Edge Delivery Services(EDS)의 경우:**

   * [Edge Delivery Services Forms용 환경 설정](/help/edge/docs/forms/universal-editor/getting-started-universal-editor.md)
   * [Edge Delivery Forms 템플릿을 사용하여 새 양식 만들기](/help/edge/docs/forms/universal-editor/create-forms.md)

* **핵심 구성 요소 기반 양식의 경우:**

   * Adobe Experience Manager 인스턴스에서 Forms > Forms 및 문서로 이동했습니다.
   * [핵심 구성 요소 템플릿을 사용하여 새 페이지 만들기](/help/forms/creating-adaptive-form-core-components.md)

## 빠른 시작

### Forms Experience Builder 액세스

**범용 편집기**

* 범용 편집기에서 EDS 페이지 열기
* 왼쪽 패널에서 Forms Experience Builder 아이콘을 찾습니다
* 대화 인터페이스를 열려면 클릭하십시오.

**적응형 양식 편집기**

* AEM > Forms > Forms 및 문서로 이동합니다.
* 편집할 핵심 구성 요소 기반 양식 만들기 또는 열기
* 편집기 도구 모음에서 Forms Experience Builder 아이콘을 클릭합니다

### 첫 번째 양식

시작하려면 다음과 같은 간단한 대화를 시도해 보십시오.

```
👤 You: "Create a simple contact form"
🤖 AI: "I'll create a contact form with name, email, and message fields for you."

👤 You: "Make the email field required"
🤖 AI: "Updated the email field to be required with validation."
```

### 필수 명령

| 기호 | 용도 | 사용 방법 |
|--------|---------|------------|
| `/` | 빠른 작업 및 단축키 | 양식을 만들려면 `/create`을(를) 입력하고 도움이 필요하면 `/help`을(를) 입력하십시오. |
| `@` | 기존 양식 필드 참조 | 특정 필드(예: `@fieldName`)를 수정하려면 `@email`을(를) 입력하십시오. |
| 일반 텍스트 | 자연스러운 대화 | 원하는 내용 설명: &quot;필수 전화번호 필드 추가&quot; |

### 성공을 위한 팁

* **고유해야 함**: &quot;유효성 검사를 사용하여 필수 전자 메일 필드 추가&quot;가 &quot;전자 메일 추가&quot;보다 더 잘 작동합니다.
* **기존 필드 참조**: 양식을 수정할 때 `@fieldName` 사용
* **도움 요청**: `/help` 입력 후 질문
* **반복**: 최상의 결과를 얻으려면 한 번에 하나씩 변경하십시오

## 핵심 기능

### Forms을 만드는 두 가지 방법

#### &#x200B;1. 처음부터 만들기

양식 요구 사항을 자연어로 설명하면 Forms Experience Builder가 전체 양식 구조를 생성합니다.

**예제:**

* &quot;개인 정보, 금융 세부 정보 및 문서 업로드를 포함한 대출 신청서 양식 만들기&quot;
* &quot;등급, 댓글 및 제품 범주가 포함된 고객 피드백 양식 작성&quot;
* &quot;결제 처리가 된 전화 회의에 대한 여러 단계 등록 양식이 필요합니다.&quot;

#### &#x200B;2. 가져오기 및 전환

기존 양식 및 문서를 최신 대화형 환경으로 변환:

**지원되는 소스:**

* **PDF forms**: 유효성을 검사한 대화형 디지털 양식→ 정적 PDF 업로드
* **스크린샷/이미지**: 종이 양식 → 기능 디지털 버전 사진
* **HTML Forms**: 기본 웹 양식 → 고급 기능이 포함된 향상된 AEM Forms
* **XFA Forms**: 이전 Adobe 양식 → 최신 반응형 양식
* **URL**: 기존 웹 양식→ 향상된 UX를 사용하는 네이티브 AEM Forms

**가져오는 방법:**

1. Forms Experience Builder 인터페이스에서 첨부 아이콘 클릭
2. 파일 업로드(PDF, 이미지, Figure 디자인 등)
3. 요구 사항 설명:
   * &quot;이 PDF 양식을 디지털 버전으로 변환&quot;
   * &quot;이 스크린샷 레이아웃과 일치하는 양식 만들기&quot;
   * “내 Figma 디자인으로 이 양식 만들기”

**지원되는 파일 형식:**

* **이미지**(PNG, JPG, GIF): 양식 레이아웃, UI mockups, 스캔한 양식
* **PDF 파일**: 기존 양식, 사양, 문서
* **Figma 파일**: 디자인 프로토타입, 브랜드 지침
* **디자인 파일**: 시각적 참조, 스타일 가이드

### 주요 상호 작용

#### 양식 요소 추가

**기본 추가:**

```
👤 You: "Add a section for personal information"
🤖 AI: "Added a personal information panel with standard fields"

👤 You: "Include a file upload for resume"
🤖 AI: "Added a secure file upload component for documents"

👤 You: "Add a dropdown for country selection"
🤖 AI: "Added a country dropdown with common options"
```

**자세한 사양:**

```
👤 You: "Add a personal information panel with fields for full name, date of birth, phone number, and email address"
🤖 AI: "Created a personal information panel with all requested fields and appropriate validation"

👤 You: "Include a secure file upload component for documents, limited to PDF files under 5MB"
🤖 AI: "Added a file upload field with PDF restriction and 5MB size limit"

👤 You: "Add a country dropdown with options for USA, Canada, UK, and Germany"
🤖 AI: "Added a country dropdown with the specified options"
```

#### 동적 비헤이비어 만들기

**간단한 논리:**

```
👤 You: "Show additional fields when 'Other' is selected"
🤖 AI: "Created a conditional rule that shows additional fields when 'Other' is chosen"

👤 You: "Make the email field required"
🤖 AI: "Updated the email field to be required with validation"

👤 You: "Calculate the total automatically"
🤖 AI: "Added calculation logic to automatically compute totals"
```

**복잡한 비즈니스 규칙:**

```
👤 You: "Show the spouse information fields only when marital status is set to 'Married'"
🤖 AI: "Created a conditional rule that displays spouse fields based on marital status"

👤 You: "Calculate the total cost by multiplying quantity and price, then add 10% tax"
🤖 AI: "Added calculation logic with quantity, price, and tax computation"

👤 You: "Enable the submit button only when all required fields are completed and terms are accepted"
🤖 AI: "Created validation logic that enables submission only when all conditions are met"
```

#### 양식 레이아웃 및 디자인

**레이아웃 변경:**

```
👤 You: "Make this a multi-step form"
🤖 AI: "Converted the form to a progressive layout with navigation"

👤 You: "Organize fields in two columns"
🤖 AI: "Updated the layout to display fields in a two-column arrangement"

👤 You: "Convert to an accordion layout"
🤖 AI: "Transformed the form to use accordion-style sections"
```

**디자인 개선 사항:**

```
👤 You: "Create a wizard-style form with 3 steps: personal info, preferences, and review"
🤖 AI: "Created a wizard form with three distinct steps and navigation"

👤 You: "Arrange the address fields in a compact two-column layout"
🤖 AI: "Organized address fields in a compact two-column format"

👤 You: "Update the layout to match the attached wireframe"
🤖 AI: "Modified the layout to match the provided design reference"
```

### 통합 설정

Forms Experience Builder는 양식을 외부 시스템 및 서비스와 연결하도록 다양한 제출 엔드포인트를 구성할 수 있습니다.

| 통합 유형 | 설치 명령 | 사용 사례 |
|------------------|---------------|----------|
| **이메일** | &quot;전자 메일로 양식 보내기&quot; | 양식 제출을 위한 알림 및 확인 |
| **REST API** | &quot;REST 끝점에 제출&quot; | 맞춤형 애플리케이션 및 서드파티 시스템 |
| **클라우드 저장소** | &quot;Azure/SharePoint에 저장&quot; | 문서 스토리지 및 파일 관리 |
| **워크플로** | &quot;Power Automate에 연결&quot; | 비즈니스 프로세스 자동화 및 승인 |
| **마케팅** | &quot;Marketo과 통합&quot; | 리드 관리 및 마케팅 자동화 |

**고급 통합 예:**

```
👤 You: "Send form submissions to hr@company.com and create a case in our CRM system"
🤖 AI: "Configured email submission and CRM integration"

👤 You: "Submit data to our REST API endpoint and trigger the new customer workflow"
🤖 AI: "Set up REST API submission with workflow triggers"

👤 You: "Email responses to the sales team and add the lead to our marketing automation platform"
🤖 AI: "Configured multi-channel submission with email and marketing automation"
```





## 고급 양식 작업


### 복잡한 규칙 만들기

사용자 상호 작용에 대응하고 데이터 무결성을 보장하는 정교한 유효성 검사 및 비즈니스 로직 구축:

```
👤 You: "Show the address section only if the user selects 'Ship to different address'"
🤖 AI: "Created a conditional rule that shows/hides the address panel based on checkbox selection"
```

### 여러 단계 양식 만들기

```
👤 You: "Create a progressive form with 3 steps: personal info, preferences, confirmation"
🤖 AI: "Created a progressive form with navigation between steps and validation at each stage"
```

### 고급 필드 유형

* 문서 관리에 대한 유효성 검사 및 크기 제한이 있는 파일 업로드
* 스케줄링에 대한 제한 및 업무 규칙이 있는 일자 선택기
* 사용자 선택에 따라 변경되는 동적 옵션이 있는 드롭다운
* 복잡한 결정 트리에 대한 조건부 논리가 있는 라디오 단추


### PDF에서 양식 전환

```
👤 You: "Convert this PDF into an interactive form"
🤖 AI: "Analyzed the PDF and created a form with appropriate field types and validation"
```

### 양식 변환 URL

```
👤 You: "Create a form from this website"
🤖 AI: "Extracted form elements and created a native AEM Form with enhanced functionality"
```

### 성능 분석

```
👤 You: "Analyze this form's conversion performance"
🤖 AI: "Provided insights on form effectiveness and suggested optimizations"
```

### 고급 사용자 지정

#### 사용자 지정 유효성 검사 규칙

* 사용자 입력을 기반으로 동적 양식 동작을 만드는 필드 종속성
* 사용자 요구 사항에 맞게 양식 환경을 조정하는 복잡한 조건부 논리
* 사용자에게 명확한 지침을 제공하는 사용자 정의 오류 메시지
* 여러 입력 간 데이터 일관성을 보장하는 크로스 필드 유효성 검사

#### 레이아웃 최적화

* 모든 장치에서 양식이 원활하게 작동하도록 하는 모바일 응답성
* 장애가 있는 사용자가 양식을 사용할 수 있도록 하는 접근성 규정 준수
* 사용자 참여 및 완료율을 개선하는 시각적 디자인 개선 사항
* 마찰을 줄이고 만족도를 향상시키는 사용자 경험 개선

#### 통합 워크플로

* 비즈니스 워크플로우를 통해 양식 제출을 라우팅하는 여러 단계 승인 프로세스
* 양식 데이터를 외부 시스템에 필요한 형식으로 변환하는 데이터 변환
* 양식 제출에 특정 규칙 및 계산을 적용하는 사용자 정의 비즈니스 논리
* 시스템 문제로부터 정상 복구를 제공하는 고급 오류 처리

## 명령 참조

### 필수 명령

| 기호 | 용도 | 사용 방법 |
|--------|---------|------------|
| `/` | 빠른 작업 및 단축키 | 양식을 만들려면 `/create`을(를) 입력하고 도움이 필요하면 `/help`을(를) 입력하십시오. |
| `@` | 기존 양식 필드 참조 | 특정 필드(예: `@fieldName`)를 수정하려면 `@email`을(를) 입력하십시오. |
| 일반 텍스트 | 자연스러운 대화 | 원하는 내용 설명: &quot;필수 전화번호 필드 추가&quot; |

### 슬래시 명령

| 명령 | 컨텍스트 | 사용 예 |
|---------|---------|---------------|
| `/create-form` | 모든 환경 | `/create-form customer survey` |
| `/add-form` | 범용 편집기 | `/add-form contact form` |
| `/update-layout` | 양식 편집기 | `/update-layout wizard with 3 steps` |
| `/update-field` | 양식 편집기 | `/update-field @email to be required` |
| `/create-rule` | 양식 편집기 | `/create-rule show @spouse if married` |
| `/create-panel` | 양식 편집기 | `/create-panel Personal Information` |
| `/configure-submit` | 양식 편집기 | `/configure-submit to email support` |
| `/help` | 모든 환경 | `/help multi-step forms` |

### 필드 참조

기존 필드를 참조하려면 `@fieldName`를 사용하십시오.

* `@firstName`, `@lastName` * 이름 필드
* `@email`, `@phoneNumber` * 연락처 필드
* `@address`, `@city`, `@zipCode` * 주소 필드
* `@dateOfBirth`, `@startDate` * 날짜 필드

### 구성 요소 유형

양식 요소를 설명할 때 다음 용어를 사용하십시오.

* `text input` * 한 줄 텍스트 필드
* `text area` * 여러 줄 텍스트 필드
* `dropdown` * 옵션이 있는 목록 선택
* `checkbox` * 단일 확인란
* `checkbox group` * 여러 확인란
* `radio group` * 라디오 단추 그룹
* `date picker` * 날짜 선택 필드
* `file upload` * 첨부 파일 필드
* `panel` * 필드 그룹화를 위한 컨테이너

### 통합 명령

| 서비스 | 자연어 명령 | 요구 사항 |
|---------|--------------------------|--------------|
| 이메일 | &quot;[전자 메일]&#x200B;(으)로 제출 보내기&quot; | 유효한 이메일 주소 |
| 나머지 API | &quot;REST 끝점 [URL]에 제출&quot; | API 엔드포인트 및 자격 증명 |
| Azure 스토리지 | &quot;Azure 스토리지에 파일 저장&quot; | 저장소 계정 구성 |
| SharePoint | &quot;SharePoint [사이트]에 저장&quot; | SharePoint 사이트 액세스 |
| 전원 자동화 | &quot;Power Automate 플로우 트리거&quot; | 플로우 구성 |
| Marketo | &quot;Marketo에 리드 추가&quot; | Marketo API 자격 증명 |

### 팁

1. **자연어 사용**: AI는 복잡한 요청을 이해하고 세부 요구 사항을 해석할 수 있습니다
2. **구체적으로**: 자세한 설명은 더 나은 결과와 더 정확한 양식 생성을 제공합니다.
3. **반복**: 완벽한 사용자 경험을 위해 대화를 통해 양식을 세분화합니다
4. **컨텍스트 활용**: 기존 양식 요소를 참조하여 이미 보유한 항목을 기반으로 빌드합니다.
5. **철저하게 테스트**: 양식이 예상대로 작동하는지 확인하려면 모든 사용자 시나리오를 확인합니다

## 제품 도움말 및 학습

Forms Experience Builder에서 AEM Forms 기능에 대해서도 배울 수 있습니다.

### 다음과 같은 질문을 해보십시오.

* “여러 단계로 구성된 양식을 어떻게 만들까요?”
* “패널과 섹션의 차이점은 무엇인가요?”
* “이메일 알림을 어떻게 설정하나요?”
* “모바일 친화적인 양식을 만드는 가장 좋은 방법은 무엇인가요?”
* “양식에 테마를 적용하려면 어떻게 해야 하나요?”

### 도움말 보기:

* AEM Forms 개념 및 용어
* 복잡한 기능에 대한 단계별 지침
* 모범 사례 및 추천
* 일반적인 문제 해결

## 모범 사례

### 양식 디자인

* **단순하게 유지**: 필수 필드로 시작하고 필요한 경우에만 복잡성을 추가하여 사용자를 압도하지 않도록 합니다.
* **일반 레이블 사용**: 양식을 통해 사용자를 안내하는 설명 레이블을 사용하여 필드 용도를 명확하게 지정하십시오.
* **도움말 텍스트 제공**: 상황별 도움말 및 예제를 통해 복잡한 필드를 안내합니다.
* **철저하게 테스트**: 모든 사용자 경로를 확인하여 모든 시나리오에서 양식이 올바르게 작동하는지 확인합니다

### 사용자 경험

* **점진적 공개**: 컨텍스트를 기반으로 관련 필드를 표시하여 인지 부하를 줄이고 완료율을 개선합니다.
* **탐색 지우기**: 사용자가 양식의 위치와 남은 단계를 이해할 수 있도록 지원합니다.
* **반응형 디자인**: 모든 장치에서 양식이 작동하고 화면 크기가 최대한의 접근성을 제공하도록 합니다.
* **접근성**: 장애가 있는 사용자가 양식을 사용할 수 있도록 설정하려면 WCAG 지침을 따르십시오

### 성능

* **필드 개수 최적화**: 양식 포기를 줄이고 완료율을 개선하는 데 필요한 정보만 요청하십시오
* **적절한 유효성 검사 사용**: 즉각적인 피드백 및 지침을 제공하기 위해 제출하기 전에 오류를 방지합니다.
* **테스트 완료율**: 분석 및 사용자 피드백을 통해 양식 효과를 모니터링하고 개선합니다.
* **정기 업데이트**: 최적의 성능을 위해 비즈니스 요구 사항 및 사용자 기대에 따라 양식을 최신 상태로 유지합니다.

### 브랜드 일관성

* **브랜드 서식 파일 만들기**: 양식 만들기를 시작하기 전에 조직의 색상, 글꼴 및 스타일을 사용하여 브랜드 양식 서식 파일을 준비합니다.
* **스타일 표준 정의**: 프롬프트에서 참조할 수 있는 일관된 단추 스타일, 필드 레이아웃 및 간격 지침을 설정합니다.
* **브랜드 자산 사용**: 양식을 만들 때 쉽게 참조할 수 있도록 로고, 색상 코드 및 브랜드 지침을 준비합니다.
* **템플릿 라이브러리**: 일반적인 사용 사례(연락처, 등록, 피드백)를 위한 브랜드 양식 템플릿 컬렉션을 빌드합니다.
* **스타일 프롬프트**: 브랜드별 지침 포함: &quot;단추 및 회사 글꼴 Helvetica에 회사 파란색(#1234AB) 사용&quot;

### 최상의 결과를 위한 팁

**간단한 시작, 빌드업**

* 기본 요청부터 시작: “연락처 양식 만들기”
* 점진적으로 세부 정보 추가: “이메일 필드에 유효성 검사 추가”
* 테스트 및 개선: “전화번호 필드를 선택 사항으로 만들기”

**필요한 경우 구체화**

* “디자인 개선” 대신
* “전문적인 색상과 깔끔한 타이포그래피 사용” 시도

**자연어 사용**

* “텍스트 입력 구성 요소 추가” 대신
* “이름 필드 추가” 시도

**기존 요소 참조**

* 기존 필드의 경우 `@fieldName` 사용: “@email을 필수로 설정”
* 필드 이름에 대해 구체적으로 설명: “@phoneNumber 필드 업데이트”

**복잡한 요청 분류**

* 하나의 큰 요청 대신 여러 개의 작은 요청 시도
* 단계별로 양식 만들기
* 다음으로 넘어가기 전에 각 변경 사항 테스트

## 문제 해결

| 문제 | 빠른 수정 |
|-------|-----------|
| **인터페이스가 로드되지 않음** | 브라우저 새로 고침, 인터넷 연결 확인 |
| **명령이 작동하지 않음** | `/help`을(를) 시도하거나 자연어를 대신 사용하십시오. |
| **@fieldName을(를) 인식할 수 없음** | 맞춤법 검사, 필드가 먼저 있는지 확인 |
| **파일 업로드 실패** | 10MB 이하의 PDF/JPG/PNG 사용 |
| **양식이 잘못된 것 같습니다** | 보다 구체화: &quot;모바일 친화적으로 만들기&quot; |
| **통합 실패** | API 자격 증명 및 권한 확인 |

**여전히 도움이 필요하십니까?** `/help`을(를) 입력한 후 특정 질문을 하거나 시스템 관리자에게 문의하십시오.

추가 지원이 필요하면 기본 [Forms Experience Builder 프롬프트 라이브러리](/help/edge/docs/forms/ai-assistant-prompt-library.md)를 참조하거나 시스템 관리자에게 문의하여 기술 지원을 받으십시오.
