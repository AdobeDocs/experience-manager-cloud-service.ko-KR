---
title: AEM Forms AI 어시스턴트 - 프롬프트 라이브러리
description: Forms 관리 UI, 적응형 양식 편집기 및 범용 편집기에서 AI 어시스턴트를 활용하여 양식을 작성하기 위한 검증된 프롬프트 패턴과 예제 모음입니다.
feature: Edge Delivery Services
hide: true
hidefromtoc: true
role: Admin, Architect, Developer
exl-id: 333d42e0-625f-432e-a61b-5d49bf08765a
source-git-commit: abcd5be06b0bf24ebe8737827fb4abdbf148b1b0
workflow-type: ht
source-wordcount: '1613'
ht-degree: 100%

---

# AEM Forms AI 어시스턴트 - 프롬프트 라이브러리

일반적인 양식 작성 시나리오에 대한 재사용 가능한 프롬프트 패턴과 예제 모음입니다. 이들 모음을 특정 요구 사항에 맞게 조정할 수 있는 템플릿이라고 생각하십시오. 각 섹션에서는 특정 사용 사례를 다루고, 사용 시기에 대한 지침과 검증된 예제를 제공합니다.

>[!NOTE]
>
> AEM Forms용 AI 어시스턴트는 얼리 어답터 프로그램에서 사용할 수 있습니다. 액세스를 요청하려면 회사 주소에서 mailto:aem-forms-ea@adobe.com로 이메일을 보내시기 바랍니다.

>[!IMPORTANT]
>
> **변경될 수 있는 설명서**: 이 프롬프트 라이브러리는 현재 제품과의 일치 여부를 테스트 중이며 업데이트 및 개정이 이루어질 수 있습니다. 얼리 어답터 프로그램이 진행되는 동안 AEM Forms용 AI 어시스턴트가 계속 발전함에 따라 프롬프트, 예제 및 모범 사례가 변경될 수 있습니다.

## 최적의 결과를 위한 모범 사례

AI 어시스턴트를 최대한 활용하려면 다음 팁을 염두에 두시기 바랍니다.

### 간단하게 시작하고 점진적으로 확장하기

처음에는 너무 복잡한 여러 단계로 구성된 요청보다는 작고 구체적인 명령(예: ““이름”에 대한 텍스트 입력 추가”)부터 시작하십시오. 이러한 접근 방식은 정확성을 높이는 데 도움이 되며, 예상대로 작동하지 않을 경우 문제를 쉽게 해결할 수 있게 해 줍니다.

**간단한 시작 예제:**

```
Add a text input field for "First Name" with placeholder "Enter your first name"
```

**점진적 확장 예제:**

```
Make @firstName mandatory and add validation message "First name is mandatory"
```

### AEM Forms 용어 사용

어시스턴트가 더 잘 이해할 수 있도록 “패널”, “텍스트 입력 필드”, “체크박스 그룹”, “제출 액션”, “규칙” 등의 용어를 사용하십시오. 이렇게 하면 AI가 AEM Forms 컨텍스트 내에서 요청을 올바르게 해석할 수 있습니다.

**선호하는 용어:**

- “텍스트 상자” 대신 “텍스트 입력 필드”
- “체크박스” 대신 “체크박스 그룹”
- “선택 목록” 대신 “드롭다운”
- “섹션” 또는 “컨테이너” 대신 “패널”
- “양식 제출” 대신 “제출 액션”
- “논리” 또는 “조건” 대신 “규칙”

### 참조 필드를 명확하게

기존 필드를 구성할 때 @fieldName 표기법을 사용하십시오(예: “@firstName을 필수로 지정”). 이렇게 하면 AI가 특히 여러 필드가 포함된 복잡한 양식에서 사용자가 언급하는 필드가 정확히 무엇인지 식별하는 데 도움이 됩니다.

**예제:**

- `Make @email mandatory with real-time validation`
- `Show @spouseInfo panel when @maritalStatus equals "Married"`
- `Set @country default value to "United States"`

### 정기적인 계획 검토

“적용”을 클릭하기 전에, 범용 편집기에서 어시스턴트가 제안한 변경 사항에 대한 계획을 항상 주의 깊게 검토하십시오. AI는 수행할 계획을 보여 주며, 그 내용이 기대한 바와 일치하는지 잠시 확인해 보시기 바랍니다.

### 수동으로 유효성 검사

어시스턴트가 변경 사항을 적용한 후에는 항상 양식을 미리 보고 테스트하여 예상대로 동작하고 표시되는지 확인하십시오. AI는 강력한 도구이지만 품질을 보장하려면 최종 확인이 중요합니다.

**유효성 검사 체크리스트:**

- 미리보기 모드에서 양식 기능 테스트
- 조건 논리가 올바르게 작동하는지 확인
- 모바일 반응성 확인
- 양식 제출 테스트
- 접근성 기능 유효성 검사

### 반복 및 개선

첫 번째 프롬프트에서 원하는 결과가 나오지 않으면 요청을 변경하거나 더 작은 단계로 나누어 보십시오. AI는 맥락을 통해 학습하므로, 보다 구체적인 세부 정보를 제공하면 결과가 향상되는 경우가 많습니다.

**반복 예제:**

1. 첫 번째 시도: “양식을 모바일 친화적으로 만들기”
2. 개선된 프롬프트: “768px 미만의 모바일 화면에 맞춰 단일 열 레이아웃과 보다 큰 터치 타깃을 사용하여 양식 레이아웃 최적화”

### 피드백 제공

기본 제공되는 피드백 메커니즘을 사용하여 어시스턴트가 학습하고 개선할 수 있도록 도와주십시오. 여러분의 피드백은 AI를 모두에게 더 나은 도구로 만드는 데 기여합니다.


## 점진적 개발 예제

다음 예제에서는 간단한 것부터 시작하여 점차 복잡도를 추가하는 방식으로 단계별로 양식을 작성하는 방법을 보여 줍니다.

### 예제 1: 점진적으로 연락처 양식 작성

**1단계 - 간단하게 시작하기:**

```
Create a basic contact form with name, email, and message fields
```

**2단계 - 유효성 검사 추가:**

```
Make @name and @email mandatory fields with appropriate validation
```

**3단계 - 사용자 경험 향상:**

```
Add placeholder text: @name "Your full name", @email "your.email@company.com", @message "Tell us how we can help"
```

**4단계 - 고급 기능 추가:**

```
Add a dropdown @inquiryType with options: "General Question", "Support Request", "Sales Inquiry", "Partnership"
```

**5단계 - 조건 논리 구현:**

```
Show @urgencyLevel dropdown (Low, Medium, High) only when @inquiryType equals "Support Request"
```

### 예제 2: 점진적으로 등록 양식 작성

**1단계 - 기본 구조:**

```
Create a user registration form with personal information panel
```

**2단계 - 핵심 필드 추가:**

```
Add text input fields: @firstName, @lastName, @email, @phone to the personal information panel
```

**3단계 - 유효성 검사 추가:**

```
Make @firstName, @lastName, and @email mandatory with real-time validation
```

**4단계 - 계정 정보 추가:**

```
Create a new panel "Account Information" with @username and @password fields
```

**5단계 - 보안 향상:**

```
Add password confirmation field @confirmPassword with validation to match @password
```

**6단계 - 환경 설정 추가:**

```
Create "Preferences" panel with @newsletter checkbox and @communicationMethod radio group (Email, SMS, Phone)
```

이러한 점진적인 접근 방식은 다음과 같은 데 도움이 됩니다.

- 문제가 악화되기 전에 조기에 발견할 수 있습니다.
- 각 기능을 철저히 테스트할 수 있습니다.
- 사용자 피드백을 바탕으로 조정할 수 있습니다.
- 개발 프로세스를 보다 효과적으로 제어할 수 있습니다.

## 새로운 양식 시작

**사용 시기:** 모든 양식 프로젝트를 시작하는 경우. 이 프롬프트는 AI가 사용자의 요구 사항을 이해하고 기반 구조를 구축하는 데 도움이 됩니다.

**사용 방법:** 기본 구조와 핵심 요구 사항부터 시작합니다. 양식 유형, 타깃 대상자 및 주 목적을 지정합니다. 이후의 프롬프트에 복잡성을 추가합니다.

**프롬프트 예제 - 간단하게 시작하기:**

```
Create a **customer onboarding form** for new bank account applications with:

**Purpose:** Collect personal information for account setup
**Target Users:** New customers applying for checking/savings accounts
**Basic Structure:** Single panel with essential fields
**Core Fields:** Name, email, phone, account type selection

Start with a simple layout that we can enhance step by step.
```

**점진적 확장 예제:**

```
Add an address panel to @customerOnboardingForm with street address, city, state, and zip code fields
```

```
Add employment information panel with @employer, @jobTitle, and @annualIncome fields
```

```
Add file upload field @identityDocuments for identity verification (Accept: .pdf,.jpg,.png)
```

**대체 간단한 시작 프롬프트:**

```
Create a basic **event registration form** with name, email, and event selection fields
```

```
Build a simple **contact form** with name, email, and message fields
```

```
Design a basic **feedback survey** with rating scale and comments field
```

## 양식 구조 및 레이아웃

**사용 시기:** 복잡한 양식을 구성하거나 더 나은 레이아웃 디자인을 통해 사용자 경험을 개선해야 하는 경우.

**사용 방법:** 사용자 여정과 정보의 논리적인 그룹화에 집중합니다. 레이아웃 환경 설정과 탐색 패턴을 지정합니다.

**예제 프롬프트 - 다단계 양식 구조:**

```
Convert this single-page form into a **3-step wizard** with:

**Step 1: Personal Information**
- Name, email, phone, address fields
- Progress indicator showing "Step 1 of 3"
- "Next" button (validate mandatory fields before proceeding)

**Step 2: Preferences & Requirements** 
- Service selection (checkbox group)
- Budget range (dropdown)
- Timeline preferences (radio group)
- Special requirements (text input field)

**Step 3: Review & Submit**
- Summary of all entered information
- Edit links to go back to specific steps
- Terms and conditions checkbox
- Submit button with confirmation

Include "Previous" and "Next" buttons, allow users to jump between completed steps, save progress automatically.
```

**레이아웃 최적화 프롬프트:**

```
Reorganize this form using a **wizard layout** for desktop and single column for mobile. 
```

```
Convert this long form into an **accordion layout** where users can expand/collapse sections.
```

```
Create a **vertical tabbed interface** for this form with tabs for: Basic Info, Contact Details, Preferences, and Review.
```

## 필드 관리 및 유효성 검사

**사용 시기:** 특정 유효성 검사 규칙 및 비헤이비어가 필요한 양식 필드를 추가, 수정 또는 향상해야 하는 경우.

**사용 방법:** 필드 유형, 유효성 검사 요구 사항 및 사용자 경험 기대 사항을 구체적으로 명시합니다. @fieldName 구문을 사용하여 기존 필드를 참조합니다.

**예제 프롬프트 - 필드 향상:**

```
Enhance the form fields with these specific requirements:

**Email Field (@email):**
- Make mandatory with real-time validation
- Show green checkmark when valid format entered
- Display helpful error message: "Please enter a valid email address"
- Add placeholder: "your.email@company.com"

**Phone Number (@phone):**
- Type: tel for mobile optimization
- Make mandatory for business customers, optional for personal
- Add placeholder: "Enter your phone number"

**Date of Birth (@dateOfBirth):**
- Type: date with date picker
- Validate age is 18+ for account opening
- Show error if under 18: "Must be 18 or older to open account"

**File Upload (@documents):**
- Accept: .pdf,.doc,.docx
- Multiple: true for multiple document upload
- Show upload progress and file names after upload
```

**필드 관련 프롬프트:**

```
Add a **file upload field** for resume with these specs: Accept only PDF/DOC/DOCX files, allow multiple files, show upload progress, display file names after upload.
```

```
Create a **dropdown field** for country selection with all countries listed. Set default value based on user's location if available.
```

```
Build a **repeatable panel** for work experience where users can add/remove multiple jobs. Each entry needs: company, title, start date, end date, description.
```

## 조건부 논리 및 규칙

**사용 시기:** 사용자 입력 또는 비즈니스 규칙에 따라 동적인 양식 비헤이비어가 필요한 경우.

**사용 방법:** 조건과 그에 따른 작업을 명확하게 정의합니다. 특정 필드 참조와 논리 연산자를 사용합니다.

**예제 프롬프트 - 복잡한 조건부 논리:**

```
Implement these conditional rules for the application form:

**Business vs Personal Account Logic:**
- If @accountType equals "Business", show:
  - Business name field (mandatory)
  - Tax ID field (mandatory)
  - Business address section
  - Number of employees dropdown
- If @accountType equals "Personal", hide all business fields

**Income-Based Requirements:**
- If @annualIncome is less than 25000:
  - Show additional verification section
  - Make co-signer information mandatory
  - Display message: "Additional documentation may be required"
- If @annualIncome is greater than 100000:
  - Show premium services options
  - Enable priority processing checkbox

**Age-Based Validation:**
- If @age is under 18:
  - Show parent/guardian information section
  - Make parent signature upload mandatory
  - Change submit button text to "Submit for Review"
- If @age is 65 or older:
  - Show senior discount options
  - Add accessibility preferences section
```

**규칙 관련 프롬프트:**

```
Create a **visibility rule** that shows @spouseInformation panel only when @maritalStatus equals "Married" or "Domestic Partnership".
```

```
Add **progressive disclosure** where additional questions appear based on previous answers. Start with basic info, then show relevant follow-ups.
```

```
Implement **smart defaults** where @country selection auto-sets related fields. Allow manual override.
```

## 데이터 통합 및 제출

**사용 시기:** 백엔드 시스템, 데이터베이스 또는 외부 서비스에 양식을 연결해야 하는 경우.

**사용 방법:** 기본 제출 설정부터 시작한 다음 점진적으로 추가 통합을 추가합니다. 통합 유형, 데이터 형식 요구 사항 및 오류 처리 환경 설정을 지정합니다.

**예제 프롬프트 - 기본 제출로 시작:**

```
Configure basic form submission for @applicationForm:

**Primary Submission:**
- Send form data to REST endpoint: `/api/v1/applications`
- Format data as JSON
- Show success message: "Application submitted successfully"
- Show error message if submission fails: "Submission failed, please try again"
```

**점진적인 보조 작업 추가 예제:**

```
Add email notification to @applicationForm: Send confirmation email to @email address with application reference number
```

```
Add CRM integration to @applicationForm: Create new lead record with @firstName, @lastName, @email, and set Status to "New Application"
```

**예제 프롬프트 - 고급 다중 채널 제출:**

```
Configure form submission with multiple data destinations:

**Primary Submission:**
- Send form data to REST endpoint: `/api/v1/applications`
- Include authentication header with API key
- Format data as JSON with nested objects for address and employment
- Handle success response (201) by showing thank you message

**Secondary Actions:**
- Send notification email to applicant at @email address
- Copy application data to tracking system
- Trigger workflow for approval process
- Create record in CRM with lead status "New Application"

**Error Handling:**
- If primary submission fails, save data locally and retry
- Show user-friendly error message: "Submission temporarily unavailable"
- Provide option to download form data as backup
- Send alert email to admin team about failed submission

**Success Flow:**
- Redirect to confirmation page with application reference number
- Send confirmation email with next steps
- Display estimated processing timeline
```

**통합 관련 프롬프트:**

```
Connect this form to **CRM system** to create new leads. Map @firstName to FirstName, @email to Email, set LeadSource to "Web Form", and Status to "New".
```

```
Set up **workflow trigger** when form is submitted. Pass all form data and trigger approval workflow with manager notification.
```

```
Configure **database integration** to save form submissions as records. Create new folder for each submission with uploaded documents.
```

## 디자인 가져오기 및 변환

**사용 시기:** 기존 양식 디자인(PDF, Figma, 이미지)을 기능적인 AEM 양식으로 변환해야 하는 경우.

**사용 방법:** 소스 디자인에 대한 명확한 맥락을 제공하고 필요한 수정이나 개선 사항을 명시합니다.

**예제 프롬프트 - PDF 양식 변환:**

```
Convert this uploaded **PDF application form** into a functional AEM adaptive form:

**Source Analysis:**
- Analyze the PDF layout and identify all form fields
- Preserve the visual hierarchy and grouping
- Maintain the professional appearance and branding

**Field Mapping:**
- Convert PDF text fields to adaptive form text inputs
- Transform checkboxes to checkbox components
- Convert dropdown lists to AEM dropdown components
- Map signature areas to digital signature fields

**Enhancements:**
- Add real-time validation that wasn't possible in PDF
- Implement conditional logic for dependent fields
- Make the form responsive for mobile devices
- Add progress saving capability
- Include accessibility improvements (ARIA labels, keyboard navigation)

**Styling:**
- Match the original color scheme and fonts
- Maintain professional business appearance
- Ensure consistent spacing and alignment
- Add subtle animations for better user experience

Preserve all original field labels and help text, but improve the user experience with modern form interactions.
```

**디자인 가져오기 프롬프트:**

```
Import this **design mockup** and convert it into an adaptive form. Maintain the exact visual design but add proper validation and mobile responsiveness.
```

```
Analyze this **image of a paper form** and recreate it digitally. Improve the layout for better mobile experience while keeping all mandatory fields.
```

```
Convert this **existing HTML form** to AEM adaptive form format. Preserve all functionality but add AEM-specific features like rules and themes.
```

## 모바일 최적화 및 반응성

**사용 시기:** 모든 디바이스 유형과 화면 크기에서 양식이 원활하게 작동해야 하는 경우.

**사용 방법:** 기본적인 모바일 최적화부터 시작한 다음 고급 기능으로 강화합니다. 모바일 우선 접근 방식을 강조하고 중단점 비헤이비어를 점진적으로 지정합니다.

**예제 프롬프트 - 기본 모바일 최적화로 시작하기:**

```
Make @contactForm mobile-friendly with:

**Basic Mobile Layout:**
- Single column layout for all form sections
- Larger touch targets for buttons and inputs
- Responsive design that works on phones and tablets
```

**고급 모바일 기능 추가 예제:**

```
Enhance @contactForm mobile experience with:
- Sticky submit button at bottom of screen
- Touch-friendly date pickers
- Swipe gestures for multi-step navigation
```

**예제 프롬프트 - 포괄적인 모바일 우선 최적화:**

```
Optimize this form for **mobile-first responsive design**:

**Mobile Layout (320px - 768px):**
- Single column layout for all form sections
- Larger touch targets (minimum 44px height)
- Simplified navigation with collapsible sections
- Sticky submit button at bottom of screen
- Auto-zoom disabled on input focus

**Tablet Layout (768px - 1024px):**
- Two-column layout for shorter fields (name, email)
- Single column for complex fields (address, comments)
- Side navigation for multi-step forms
- Optimized for both portrait and landscape

**Desktop Layout (1024px+):**
- Multi-column layouts where appropriate
- Horizontal form sections for related fields
- Sidebar navigation for long forms
- Hover states and advanced interactions

**Touch Optimization:**
- Larger checkbox and radio button targets
- Swipe gestures for multi-step navigation
- Pull-to-refresh for saved drafts
- Touch-friendly date/time pickers

**Performance:**
- Lazy load non-critical form sections
- Optimize images and icons for mobile
- Minimize JavaScript for faster loading
- Progressive enhancement approach
```

**모바일 전용 간단한 프롬프트:**

```
Make @checkoutForm mobile-optimized with large buttons and one-thumb navigation
```

```
Add touch-friendly controls to @surveyForm for tablet users
```

```
Enable offline functionality for @applicationForm with local data saving
```

## 접근성 및 규정 준수

**사용 시기:** 양식이 접근성 표준(WCAG 2.1 AA) 또는 규정 준수 요구 사항을 충족해야 하는 경우.

**사용 방법:** 충족해야 하는 접근성 요구 사항과 준수 표준을 지정합니다.

**예제 프롬프트 - 접근성 구현:**

```
Make this form **WCAG 2.1 AA compliant** with these accessibility features:

**Keyboard Navigation:**
- Logical tab order through all form elements
- Skip links to main content and form sections
- Keyboard shortcuts for common actions
- Focus indicators clearly visible on all interactive elements

**Screen Reader Support:**
- Proper ARIA labels for all form fields
- Descriptive error messages announced to screen readers
- Form section headings with proper hierarchy (h1, h2, h3)
- Progress announcements for multi-step forms

**Visual Accessibility:**
- Color contrast ratio minimum 4.5:1 for text
- Don't rely solely on color to convey information
- Text size minimum 16px for body text
- Scalable up to 200% without horizontal scrolling

**Motor Accessibility:**
- Large click targets (minimum 44x44px)
- Generous spacing between interactive elements
- No time limits or provide extension options
- Alternative input methods support

**Cognitive Accessibility:**
- Clear, simple language in all instructions
- Consistent navigation and layout patterns
- Error prevention and clear error recovery
- Help text and examples for complex fields

**Testing Requirements:**
- Test with screen readers (NVDA, JAWS, VoiceOver)
- Verify keyboard-only navigation
- Check color contrast with automated tools
- Validate HTML for semantic correctness
```

**규정 준수 관련 프롬프트:**

```
Ensure this **healthcare form meets HIPAA requirements** with proper data encryption, audit logging, and privacy controls.
```

```
Make this **financial form PCI DSS compliant** with secure payment field handling and data protection measures.
```

```
Create a **government form meeting Section 508 standards** with full accessibility and plain language requirements.
```

## 테스트 및 품질 보증

**사용 시기:** 양식 기능, 사용자 경험 및 기술 성능을 검증해야 하는 경우.

**사용 방법:** 검증해야 하는 테스트 시나리오, 예외 사례 및 품질 기준을 지정합니다.

**예제 프롬프트 - 포괄적인 양식 테스트:**

```
Create a **comprehensive testing plan** for this application form:

**Functional Testing:**
- Test all field validations with valid and invalid data
- Verify conditional logic shows/hides fields correctly
- Test file upload with various file types and sizes
- Validate calculation fields update correctly
- Test form submission with complete and incomplete data

**User Experience Testing:**
- Test form completion time (target: under 10 minutes)
- Verify error messages are helpful and actionable
- Test progress saving and restoration
- Validate mobile touch interactions
- Check form accessibility with assistive technologies

**Edge Case Testing:**
- Test with extremely long text inputs
- Verify behavior with special characters and emojis
- Test with slow internet connections
- Validate offline functionality if applicable
- Test browser back/forward button behavior

**Performance Testing:**
- Measure form load time (target: under 3 seconds)
- Test with large file uploads
- Verify memory usage with long form sessions
- Test concurrent user submissions
- Validate database performance under load

**Security Testing:**
- Test input sanitization and XSS prevention
- Verify CSRF protection is working
- Test file upload security restrictions
- Validate data encryption in transit and at rest
- Check authentication and authorization controls

**Cross-Browser Testing:**
- Test on Chrome, Firefox, Safari, Edge
- Verify mobile browsers (iOS Safari, Chrome Mobile)
- Test on different operating systems
- Validate older browser fallbacks
- Check print functionality across browsers
```

**테스트 관련 프롬프트:**

```
Create **automated test scripts** for this form's critical user paths: successful submission, validation errors, and conditional logic.
```

```
Design a **user acceptance testing plan** with realistic scenarios and success criteria for business stakeholders.
```

```
Set up **performance monitoring** to track form completion rates, abandonment points, and submission success rates.
```

## 고급 기능 및 통합

**사용 시기:** AI 지원, 고급 워크플로 또는 복잡한 통합과 같은 정교한 양식 기능이 필요한 경우.

**사용 방법:** 고급 기능과 통합 요구 사항을 명확하게 정의합니다.

**예제 프롬프트 - AI 강화 양식:**

```
Add **AI-powered features** to enhance this application form:

**Smart Auto-Complete:**
- Use AI to suggest company names as user types
- Auto-populate address fields from partial input
- Suggest job titles based on industry selection
- Provide intelligent form completion suggestions

**Dynamic Question Generation:**
- Generate follow-up questions based on previous answers
- Adapt form complexity to user's experience level
- Show relevant optional fields based on user profile
- Personalize form sections for different user types

**Intelligent Validation:**
- Use AI to detect potentially incorrect information
- Suggest corrections for common data entry errors
- Validate business information against public databases
- Flag suspicious or inconsistent responses

**Content Optimization:**
- A/B test different form layouts automatically
- Optimize field order based on completion patterns
- Adjust form length based on user engagement
- Personalize help text based on user behavior

**Predictive Analytics:**
- Predict likelihood of form completion
- Identify users who might need assistance
- Suggest optimal times for form completion reminders
- Analyze drop-off points and suggest improvements

**Natural Language Processing:**
- Allow voice input for text fields
- Convert speech to text for accessibility
- Analyze open-text responses for sentiment
- Extract structured data from unstructured input
```

**고급 통합 프롬프트:**

```
Integrate with **CRM system** to pre-populate known customer data, update records in real-time, and trigger automated follow-up sequences.
```

```
Connect to **payment gateway** for secure transaction processing with PCI compliance, fraud detection, and multiple payment methods.
```

```
Implement **blockchain verification** for document authenticity, immutable audit trails, and decentralized identity verification.
```

## 문제 해결 및 최적화

**사용 시기:** 양식에 성능 문제, 사용자 경험 문제 또는 기술적 어려움이 있는 경우.

**사용 방법:** 구체적인 문제와 원하는 결과를 명확하게 설명합니다.

**예제 프롬프트 - 성능 최적화:**

```
Optimize this form for **better performance and user experience**:

**Current Issues:**
- Form takes 8+ seconds to load on mobile
- Users are abandoning at the address section (60% drop-off)
- File uploads frequently fail or timeout
- Validation errors are confusing users

**Performance Improvements:**
- Implement lazy loading for non-critical form sections
- Optimize images and reduce bundle size
- Add progressive loading indicators
- Cache frequently used data (country lists, etc.)
- Minimize JavaScript execution time

**User Experience Fixes:**
- Simplify the address section with auto-complete
- Add inline validation with helpful error messages
- Implement smart defaults based on user location
- Add progress saving every 30 seconds
- Provide clear instructions for each section

**Technical Optimizations:**
- Implement chunked file uploads with resume capability
- Add client-side validation before server submission
- Optimize database queries for faster responses
- Implement proper error handling and retry logic
- Add comprehensive logging for debugging

**Monitoring & Analytics:**
- Set up form analytics to track user behavior
- Monitor completion rates by section
- Track error rates and types
- Measure performance metrics continuously
- A/B test improvements with real users
```

**문제 해결 프롬프트:**

```
**Debug this form submission error:** Users report getting "500 Internal Server Error" when submitting. Check validation logic, server endpoints, and data formatting.
```

```
**Fix mobile layout issues:** Form fields are overlapping on iPhone screens and submit button is not visible. Ensure proper responsive design.
```

```
**Resolve validation conflicts:** Some users can't submit even with valid data. Review validation rules for conflicts and edge cases.
```

## 환경 관련 모범 사례

### Forms 관리 UI

**사용 시기:** 고수준 양식 생성 및 관리 작업 시.

```
In Forms Management UI, create a new **customer survey template** that can be reused across different departments. Include standard branding, common field types, and configurable sections.
```

### 적응형 양식 편집기

**사용 시기:** 상세한 양식 구성 및 복잡한 규칙 생성 시.

```
In the Adaptive Forms Editor, configure **advanced business rules** for this loan application: calculate debt-to-income ratio, determine eligibility, and show appropriate next steps.
```

### 범용 편집기

**사용 시기:** 시각적 편집이 가능한 Edge Delivery Services 양식 사용 시.

```
In Universal Editor, create a **responsive contact form** for the company website. Ensure it matches the site design and integrates with the existing content management workflow.
```

## 명령 참조 빠른 안내서

| 명령 | 모범 사용 사례 | 예 |
|---------|---------------|---------|
| `/create-form` | 새로운 양식 시작 | `/create-form employee onboarding with personal info and benefits selection` |
| `/add-form` | 페이지에 양식 추가 | `/add-form newsletter signup with email and preferences` |
| `/update-layout` | 양식 구조 변경 | `/update-layout wizard with 4 steps: info, preferences, review, confirm` |
| `/update-field` | 필드 속성 수정 | `/update-field @email to be mandatory with real-time validation` |
| `/create-rule` | 동적 비헤이비어 추가 | `/create-rule show @spouseInfo if @maritalStatus equals "Married"` |
| `/create-panel` | 양식 섹션 구성 | `/create-panel Employment Details with job title, company, salary fields` |
| `/add-panel` | 디자인 변환 | `/add-panel from uploaded form image with field recognition` |
| `/configure-submit` | 데이터 처리 설정 | `/configure-submit to CRM and send confirmation email` |
| `/help` | 도움 받기 | `/help how to implement multi-step validation?` |

## 지원되는 구성 요소 속성 참조

### 범용 속성 (모든 구성 요소)

- **유형**: 구성 요소 유형 (텍스트, 이메일, 숫자, 전화번호, 날짜, 체크박스, 라디오, 드롭다운, 파일 등)
- **이름**: 양식 제출을 위한 필드 식별자
- **레이블**: 필드에 대한 표시 텍스트
- **설명**: 필드에 대한 도움말 텍스트
- **표시**: 초기 가시성에 대한 부울 값
- **필수**: 필수 필드에 대한 부울 값

### 입력 필드 속성

- **값**: 기본값/초기값
- **플레이스홀더**: 입력 필드에 대한 힌트 텍스트
- **최소값**: 최소값 (숫자/날짜의 경우)
- **최대값**: 최대값 (숫자/날짜의 경우)

### 파일 업로드 속성

- **허용**: 파일 유형 (.pdf, .doc, .docx, .jpg, .png 등)
- **다중**: 여러 파일 선택을 위한 부울 값

### 선택 제어 속성

- **옵션**: 드롭다운에 대한 선택 사항 (쉼표로 구분된 목록)
- **선택됨**: 체크박스/라디오에 대한 기본 선택

### 컨테이너 속성

- **Fieldset**: 관련 필드 그룹화
- **반복 가능**: 반복 가능한 섹션에 대한 부울 값

### 고급 속성

- **가시적 표현**: 조건부 가시성을 위한 공식 (=formula)
- **값 표현식**: 계산된 값에 대한 공식 (=formula)

## 모범 사례 요약

### 기술 지침

- 공식 AEM Forms 구성 요소 사양에서 **지원되는 속성만 사용**
- 필드 참조(@fieldName) 및 표현식(=formula)에 대한 **적절한 구문 따르기**
- 각 변경 후 **점진적으로 테스트**&#x200B;하여 문제를 조기에 포착
- **접근성을 처음부터 계획**
- 모든 디자인 결정에 **모바일 사용자 고려**
- 향후 유지 관리 및 팀 협업을 위해 **복잡한 규칙 문서화**

### 전략적 접근 방식

- **사용자 요구 사항부터 시작** - 기술적 기능뿐만 아니라 사용자가 달성해야 하는 것에도 집중합니다.
- **완성을 위한 디자인** - 양식 디자인에서 마찰과 인지 부하를 최소화합니다.
- **데이터 흐름을 조기에 계획** - 데이터가 어떻게 처리, 저장 및 사용될지 고려합니다.
- **규모에 맞춰 구축** - 예상되는 사용자 볼륨과 데이터 증가를 처리할 수 있는 양식을 디자인합니다.
- **점진적인 개선 구현** - 기본 기능이 작동하는지 확인한 다음 고급 기능을 추가합니다.

### 피해야 할 일반적인 위험 요소

- **너무 복잡한 초기 요청** - 큰 작업을 더 작고 관리하기 쉬운 단계로 나누십시오.
- AEM Forms 사양에 없는 **지원되지 않는 속성 사용**
- 개발 프로세스 후반까지 **모바일 경험 무시**
- 실제 시나리오와 예외 사례를 반영한 **사용자 테스트 생략**
- **AI가 명확하고 구체적인 지침을 제공하지 않고도 맥락을 이해한다고 가정**
- **접근성 및 규정 준수 요구 사항 무시**
- 다음 단계로 넘어가기 전에 **변경 사항을 검증하지 않음**

### 품질 보증 접근 방식

1. **자주 미리 보기** - 중요한 변경 사항이 있을 때마다 미리보기 모드에서 작업을 확인합니다.
2. **예외 사례 테스트** - 비정상적인 입력, 긴 텍스트, 특수 문자를 시도해 봅니다.
3. **다양한 디바이스에서 검증** - 모바일, 태블릿 및 데스크탑에서 테스트합니다.
4. **접근성 확인** - 키보드 탐색 및 화면 판독기 호환성을 확인합니다.
5. **성능 테스트** - 양식이 빠르게 로드되고 원활하게 응답하는지 확인합니다.
6. **사용자 수용 테스트** - 배포 전에 실제 사용자가 양식을 테스트하도록 합니다.


*이 프롬프트 라이브러리는 사용자 피드백과 새로운 AI 어시스턴트 기능을 기반으로 지속적으로 업데이트됩니다. 최신 기능과 예제를 보려면 [AEM Forms 설명서](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/home.html)를 확인하십시오.*
