---
title: Forms Experience Builder - 프롬프트 라이브러리
description: Forms 관리 UI, 적응형 양식 편집기 및 범용 편집기에서 AI 어시스턴트를 활용하여 양식을 작성하기 위한 검증된 프롬프트 패턴과 예제 모음입니다.
feature: Edge Delivery Services
hide: true
index: false
hidefromtoc: true
role: Admin, Architect, Developer
exl-id: 333d42e0-625f-432e-a61b-5d49bf08765a
source-git-commit: 8be2b09200af58c701721b3e8537ea5e6cc3e4a2
workflow-type: tm+mt
source-wordcount: '1338'
ht-degree: 28%

---

# Forms Experience Builder - 프롬프트 라이브러리

Forms Experience Builder에 최적화된 재사용 가능한 프롬프트 패턴 및 예제의 컬렉션입니다. 이 간소화된 라이브러리는 LLM 기반 스마트 필드 및 브랜드 일관성에 대한 향상된 지원을 통해 처음부터 제작 및 가져오기 및 변환이라는 두 가지 핵심 제작 방법에 중점을 둡니다.

>[!NOTE]
>
> Forms Experience Builder는 얼리어답터 프로그램에서 사용할 수 있습니다. 액세스 권한을 요청하려면 회사 주소에서 `aem-forms-ea@adobe.com`(으)로 전자 메일을 보내십시오.

>[!IMPORTANT]
>
> **변경될 수 있는 설명서**: 이 프롬프트 라이브러리는 현재 제품과의 일치 여부를 테스트 중이며 업데이트 및 개정이 이루어질 수 있습니다. Forms Experience Builder가 얼리어답터 프로그램 동안 계속 발전함에 따라 프롬프트, 예 및 우수 사례가 변경될 수 있습니다.

## 이 프롬프트 라이브러리 사용

이 라이브러리는 일반적인 양식 작성 시나리오에 재사용 가능한 프롬프트 패턴을 제공합니다. 포괄적인 모범 사례는 [Forms Experience Builder 시작 안내서](forms-ai-assistant-getting-started.md#best-practices)를 참조하십시오.

### 이 라이브러리에 대한 빠른 팁

- **예제로 시작** - 제공된 프롬프트를 템플릿으로 사용하고 필요에 맞게 조정하십시오.
- **두 가지 만들기 방법** - 처음부터 만들기 또는 가져오기 및 변환 접근 방식을 선택합니다.
- **고유해야 함** - 일반 예제에 사용자 고유의 세부 정보 추가
- **철저하게 테스트** - 항상 특정 환경에서 결과를 확인합니다.

### 브랜드 템플릿 및 스타일

**일관된 양식 생성을 위해 브랜드 자산을 미리 준비합니다.**

- **브랜드 템플릿** - 조직의 색상, 글꼴 및 레이아웃 패턴을 사용하여 표준화된 양식 템플릿을 만듭니다.
- **스타일 지침** - 일관된 필드 스타일, 단추 디자인 및 간격 표준을 정의합니다.
- **구성 요소 라이브러리** - 브랜드 ID와 일치하는 재사용 가능한 양식 구성 요소 빌드
- **시각적 Assets** - 양식 통합을 위해 로고, 아이콘 및 배경 요소 준비

**브랜드 템플릿 프롬프트 예:**

```
Create a brand template for financial services forms with:
- Corporate blue (#003366) and silver (#C0C0C0) color scheme
- Open Sans font family for all text
- 16px minimum font size for accessibility
- Consistent 24px spacing between sections
- Corporate logo in header with proper sizing
- Professional button styling with hover effects
```

>[!NOTE]
>
>**사용자 지정 구성 요소**: 사용자 지정 브랜드 요소를 구현하기 전에 조직별 구성 요소 사용 및 Forms Experience Builder와의 호환성에 대해 개발 팀에 문의하십시오.

>[!NOTE]
>
> 간소화된 Forms Experience Builder 기능을 반영하도록 이 프롬프트 라이브러리가 업데이트되었습니다. 예제에 표시된 일부 고급 통합 및 테스트 기능은 추가 구성이 필요할 수 있습니다.



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

**2단계 - 필수 필드 추가:**

```
Add fields for @firstName, @lastName, @email, @phoneNumber with appropriate validation
```

**3단계 - 비즈니스 논리 추가:**

```
Create a rule: if @age is under 18, show parent/guardian information section
```

**4단계 - 기본 설정으로 개선:**

```
Add a preferences panel with @newsletterSubscription, @marketingConsent, @termsAccepted
```

**5단계 - 파일 업로드 추가:**

```
Include a file upload field for @profilePicture with size limit of 5MB
```

## 양식 생성 및 관리

**사용 시기:** 새 양식을 만들거나 기존 양식을 수정해야 하는 경우.

**사용 방법:** 두 가지 방법 중 하나를 선택하십시오. 처음부터 만들기 또는 가져오기 및 변환([시작 안내서](/help/edge/docs/forms/forms-ai-assistant-getting-started.md) 참조).

**예제 프롬프트 - 간단한 양식 만들기:**

```
Create a customer feedback form with:
- Product rating (1-5 stars)
- Comment field for detailed feedback
- Customer email (optional)
- Submit to email notification
```

**예제 프롬프트 - 복잡한 양식 만들기:**

```
Create a comprehensive employee onboarding form with:

**Personal Information Section:**
- Full name (first, middle, last)
- Date of birth with age validation
- Contact information (email, phone, address)
- Emergency contact details

**Employment Details:**
- Position and department selection
- Start date with business day validation
- Salary information with confidentiality notice
- Reporting structure

**Document Upload:**
- Resume/CV upload (PDF, DOC, DOCX)
- ID verification documents
- Tax forms and banking information
- Signed employment agreement

**Preferences:**
- Benefits selection with cost calculator
- Work schedule preferences
- Training requirements
- Equipment needs

**Validation Rules:**
- Email format validation
- Phone number format validation
- Age must be 18 or older
- All required documents must be uploaded
- Terms and conditions must be accepted

**Submit Actions:**
- Send confirmation email to new employee
- Notify HR department
- Create employee record in HR system
- Schedule orientation meeting
```

**양식 관리 프롬프트:**

```
Import this PDF application form and convert it to an adaptive form with enhanced validation
```

```
Update the existing contact form to include social media handles and preferred contact method
```

```
Reorganize the registration form into a 3-step wizard: personal info, preferences, confirmation
```

## 필드 관리 및 구성

**사용할 시점:** 양식 필드를 추가, 수정 또는 구성해야 하는 경우.

**사용 방법:** 필드 형식, 유효성 검사 규칙 및 사용자 경험 요구 사항에 대해 구체적으로 지정합니다.

**예제 프롬프트 - 기본 필드 추가:**

```
Add a text input field for "Company Name" with placeholder "Enter your company name"
```

**예제 프롬프트 - 고급 필드 구성:**

```
Add a comprehensive address section with:

**Street Address:**
- Address line 1 (required, max 100 characters)
- Address line 2 (optional, max 100 characters)
- City (required, dropdown with common cities)
- State/Province (required, dropdown)
- Postal code (required, format validation)
- Country (required, default to "United States")

**Validation Rules:**
- Postal code must match state selection
- Address line 1 cannot be empty
- City must be a valid city for selected state

**User Experience:**
- Auto-complete for address fields
- Clear labels and help text
- Mobile-friendly input fields
- Accessibility compliance
```

**필드 구성 프롬프트:**

```
Make @email field required with real-time validation and custom error message
```

```
Add a dropdown for @country with options for USA, Canada, UK, Germany, France, and "Other"
```

```
Configure @phoneNumber field with format (XXX) XXX-XXXX and validation
```

```
Add a file upload field for @resume with PDF and DOC restrictions, max 5MB
```

## LLM 향상 스마트 필드

**사용 시기:** AI의 기술 자료를 활용하는 미리 채워진 옵션이 있는 필드가 필요한 경우.

**사용 방법:** 포괄적인 데이터 집합이 필요한 요청 필드 - AI는 기본 제공 지식을 사용하여 옵션을 자동으로 채울 수 있습니다.

### 지리적 및 위치 필드

**공항 및 교통 수단:**

```
Add a dropdown for departure airports with all major international airports
Add arrival airport field with IATA codes and full names
Create a field for nearest airport to user location
Add a selection of train stations for European cities
```

**관리 영역:**

```
Add a complete list of US states with abbreviations
Create a country dropdown with ISO codes and full names
Add a field for major world cities with time zones
Include a dropdown of Canadian provinces and territories
Add a field for UK counties and postal areas
```

### 비즈니스 및 업계 데이터

**회사 분류:**

```
Add a field for industry classification with NAICS codes
Create a dropdown of business entity types (LLC, Corporation, Partnership, etc.)
Add a field for company size categories (startup, SME, enterprise)
Include department selection for large organizations
Add a field for professional service types
```

**전문 분류:**

```
Add a field for job titles with common industry roles
Create a dropdown of professional certifications by field
Include education levels with degree types
Add a field for years of experience ranges
Create a selection for programming languages and frameworks
```

### 표준 및 규정

**재무 및 법적 정보:**

```
Add a field for currency codes with symbols and exchange rates
Create a dropdown of tax ID types by country
Include a field for legal document types
Add payment method options with security features
Create a selection for banking institutions by country
```

**기술 표준:**

```
Add a dropdown of file format types with extensions
Include network protocol options
Add a field for database types and versions
Create a selection for API authentication methods
```

### 의료 및 의료

**의료 분류:**

```
Add a field for medical specialties
Create a dropdown of common medications with generic names
Include a field for insurance provider types
Add a selection for medical emergency contact relationships
Create a field for dietary restrictions and allergies
```

### 시간 및 일정 인텔리전스

**날짜 및 시간 필드:**

```
Add a field for business hours with time zone handling
Create a dropdown of public holidays by country
Include seasonal options with date ranges
Add a field for conference room booking with availability
Create a selection for recurring meeting patterns
```

### 제품 및 서비스 범주

**전자 상거래 분류:**

```
Add a field for product categories with subcategories
Create a dropdown of shipping methods with delivery estimates
Include a field for return policy options
Add a selection for customer priority levels
Create a field for subscription billing cycles
```

**스마트 필드 프롬프트 예:**

```
"Add a departure airport field with all major airports worldwide including IATA codes and city names"
```

```
"Create a comprehensive industry field using standard NAICS classification with technology subcategories"
```

```
"Include a professional certification dropdown that adapts based on the selected job field"
```

```
"Add an international phone number field that formats based on the selected country"
```

```
"Create a university selection field with major institutions organized by country and ranking"
```

## 규칙 생성 및 비즈니스 논리

**사용할 시기:** 조건부 논리, 유효성 검사 규칙 또는 비즈니스 프로세스를 구현해야 하는 경우.

**사용 방법:** 조건 및 작업을 지정하여 비즈니스 논리를 명확하게 설명하십시오.

**예제 프롬프트 - 단순 조건부 논리:**

```
Create a rule that shows @spouseInformation panel only when @maritalStatus equals "Married"
```

**예제 프롬프트 - 복잡한 비즈니스 규칙:**

```
Implement comprehensive loan application validation:

**Income Validation:**
- If @annualIncome is less than 30000:
  - Show warning message: "Income may be insufficient for requested loan amount"
  - Require additional income documentation
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
Create a **visibility rule** that shows @spouseInformation panel only when @maritalStatus equals "Married" or "Domestic Partnership"
```

```
Add **progressive disclosure** where additional questions appear based on previous answers. Start with basic info, then show relevant follow-ups
```

```
Implement **smart defaults** where @country selection auto-sets related fields. Allow manual override
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

**예제 프롬프트 - 표준 다중 채널 제출:**

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
Connect this form to **CRM system** to create new leads. Map @firstName to FirstName, @email to Email, set LeadSource to "Web Form", and Status to "New"
```

```
Set up **workflow trigger** when form is submitted. Pass all form data and trigger approval workflow with manager notification
```

```
Configure **database integration** to save form submissions as records. Create new folder for each submission with uploaded documents
```

## 기존 Forms 가져오기 및 변환

**사용 시기:** 기존 양식, 문서 또는 디자인을 최신 AEM 양식으로 변형할 경우.

**사용 방법:** 소스 파일을 업로드하고 전환 요구 사항을 설명합니다([가져오기 안내서](/help/edge/docs/forms/forms-ai-assistant-getting-started.md) 참조).

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

Preserve all original field labels and help text, but improve the user experience with modern form interactions
```

**디자인 가져오기 프롬프트:**

```
Import this **design mockup** and convert it into an adaptive form. Maintain the exact visual design but add proper validation and mobile responsiveness
```

```
Analyze this **image of a paper form** and recreate it digitally. Improve the layout for better mobile experience while keeping all mandatory fields
```

```
Convert this **existing HTML form** to AEM adaptive form format. Preserve all functionality but add AEM-specific features like rules and themes
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
```

**모바일 전용 프롬프트:**

```
Make this form **touch-friendly** with larger buttons and simplified navigation for mobile users
```

```
Optimize form for **tablet users** with appropriate field sizes and navigation patterns
```

```
Add **swipe gestures** for multi-step form navigation on mobile devices
```

## 접근성 및 규정 준수

**사용 시기:** 양식이 WCAG(액세스 가능성 표준) 또는 준수 요구 사항을 충족해야 하는 시기.

**사용 방법:** 필요한 준수 수준과 필요한 특정 접근성 기능을 지정합니다.

**예제 프롬프트 - 기본 접근성:**

```
Make @contactForm accessible with:

**Basic Accessibility:**
- Proper ARIA labels for all form fields
- Keyboard navigation support
- High contrast color scheme
- Screen reader compatibility
- Focus indicators for all interactive elements
```

**예제 프롬프트 - 고급 액세스 가능성:**

```
Implement comprehensive accessibility for @applicationForm:

**WCAG 2.1 AA Compliance:**
- Semantic HTML structure with proper headings
- ARIA landmarks and roles for navigation
- Color contrast ratio of at least 4.5:1
- Keyboard-only navigation support
- Screen reader announcements for dynamic content

**Form-Specific Accessibility:**
- Error messages announced to screen readers
- Field validation with clear error descriptions
- Progress indicators for multi-step forms
- Skip navigation links for keyboard users
- Alternative text for all images and icons

**User Experience:**
- Clear focus indicators on all interactive elements
- Logical tab order through form fields
- Descriptive link text and button labels
- Help text available for complex fields
- Timeout warnings for session expiration
```

**접근성별 프롬프트:**

```
Add **screen reader support** to this form with proper ARIA labels and announcements
```

```
Implement **keyboard navigation** for all form interactions and navigation elements
```

```
Ensure **color contrast** meets WCAG AA standards for all text and interactive elements
```

## 성능 최적화

**사용할 시기:** 양식을 빠르게 로드하고 다양한 조건에서 잘 수행해야 하는 경우.

**사용 방법:** 성능 요구 사항과 최적화 전략을 지정합니다.

**예제 프롬프트 - 기본 성능:**

```
Optimize @contactForm for performance:

**Loading Optimization:**
- Lazy load non-critical form sections
- Minimize initial bundle size
- Optimize images and assets
- Enable caching for static resources
```

**예제 프롬프트 - 고급 성능:**

```
Implement comprehensive performance optimization for @applicationForm:

**Loading Performance:**
- Progressive loading of form sections
- Optimize images with WebP format
- Minimize JavaScript bundle size
- Enable gzip compression for all assets

**Runtime Performance:**
- Debounce validation calls to reduce API requests
- Optimize conditional logic execution
- Cache frequently used data
- Implement virtual scrolling for long lists

**User Experience:**
- Show loading indicators for async operations
- Provide offline capability for form data
- Auto-save form progress every 30 seconds
- Optimize form submission with retry logic

**Monitoring:**
- Track form load times and user interactions
- Monitor validation performance
- Measure submission success rates
- Alert on performance degradation
```

**성능별 프롬프트:**

```
Optimize form **loading speed** by implementing progressive loading and asset optimization
```

```
Add **auto-save functionality** to prevent data loss during form completion
```

```
Implement **offline support** so users can complete forms without internet connection
```

## 테스트 및 품질 보증

**사용할 시기:** 양식에서 안정성 및 사용자 만족도를 보장하기 위해 포괄적인 테스트가 필요한 경우.

**사용 방법:** 테스트 시나리오, 유효성 검사 요구 사항 및 품질 지표를 지정합니다.

**예제 프롬프트 - 기본 테스트:**

```
Add comprehensive testing for @contactForm:

**Functional Testing:**
- Test all form field validations
- Verify submit functionality works correctly
- Test error handling and user feedback
- Validate conditional logic and rules
```

**예제 프롬프트 - 고급 테스트:**

```
Implement comprehensive testing strategy for @applicationForm:

**Functional Testing:**
- Unit tests for all validation rules
- Integration tests for submit actions
- End-to-end testing for complete user flows
- Cross-browser compatibility testing

**User Experience Testing:**
- Usability testing with target user groups
- Accessibility testing with screen readers
- Mobile device testing on various screen sizes
- Performance testing under load conditions

**Quality Assurance:**
- Automated testing for regression prevention
- Manual testing for edge cases and scenarios
- Security testing for data protection
- Compliance testing for regulatory requirements

**Monitoring:**
- Track form completion rates and abandonment
- Monitor error rates and user feedback
- Measure performance metrics and load times
- Analyze user behavior and interaction patterns
```

**테스트 관련 프롬프트:**

```
Add **automated testing** for all form validations and submit functionality
```

```
Implement **user acceptance testing** scenarios for complete form workflows
```

```
Set up **performance monitoring** to track form load times and user interactions
```

## 문제 해결

일반적인 Forms Experience Builder 문제에 대한 빠른 솔루션:

| 문제 | 빠른 수정 |
|-------|-----------|
| 양식 제출 안 함 | 제출 액션 구성 및 유효성 검사 규칙 확인 |
| 유효성 검사 오류가 표시되지 않음 | 필드 유효성 검사 설정 및 오류 메시지 배치 확인 |
| 모바일 레이아웃 문제 | 반응형 디자인 설정 및 필드 크기 조정 검토 |
| 필드가 표시되지 않음 | 조건부 논리 및 가시성 규칙 확인 |
| 가져오기 실패 | 파일 형식 호환성 및 크기 제한 확인 |
| 통합 오류 | API 끝점 및 인증 자격 증명의 유효성 검사 |
| 성능 문제 | 필드 카운트 최적화 및 불필요한 유효성 검사 제거 |
| 접근성 문제 | 필드 레이블, ARIA 속성 및 탭 순서 검토 |

**디버그 모드 프롬프트:**

```
Enable debug mode to identify issues with form submission and field validation
```

**오류 분석 프롬프트:**

```
Analyze form errors: check validation rules, API responses, and user input patterns
```

## 고급 분석 및 통찰력

**사용할 시기:** 양식 성능 및 사용자 동작을 이해해야 하는 경우.

**사용 방법:** 필요한 분석 요구 사항 및 통찰력을 지정합니다.

**예제 프롬프트 - 기본 분석:**

```
Add analytics to @contactForm:

**Basic Metrics:**
- Form completion rates
- Field abandonment rates
- Submit success/failure rates
- User session duration
```

**예제 프롬프트 - 고급 분석:**

```
Implement comprehensive analytics for @applicationForm:

**User Behavior Analytics:**
- Track field completion rates and abandonment
- Monitor user session duration and patterns
- Analyze form navigation and user flow
- Identify bottlenecks and friction points

**Performance Analytics:**
- Measure form load times and performance
- Track API response times and failures
- Monitor validation rule effectiveness
- Analyze submission success rates

**Business Intelligence:**
- Generate reports on form effectiveness
- Track conversion rates and ROI
- Monitor user satisfaction and feedback
- Identify opportunities for optimization

**Predictive Analytics:**
- Predict form completion likelihood
- Identify users likely to abandon
- Recommend form improvements
- Optimize user experience based on data
```

**Analytics 관련 프롬프트:**

```
Add **conversion tracking** to measure form completion rates and user behavior
```

```
Implement **A/B testing** to compare different form designs and optimize performance
```

```
Create **analytics dashboard** to monitor form performance and user insights
```

## 보안 및 데이터 보호

**사용할 시기:** 양식이 중요한 데이터를 처리하고 보안 조치가 필요한 경우.

**사용 방법:** 보안 요구 사항 및 데이터 보호 조치를 지정합니다.

**예제 프롬프트 - 기본 보안:**

```
Add security measures to @contactForm:

**Basic Security:**
- HTTPS encryption for all data transmission
- Input validation and sanitization
- CSRF protection for form submissions
- Secure session management
```

**예제 프롬프트 - 고급 보안:**

```
Implement comprehensive security for @applicationForm:

**Data Protection:**
- End-to-end encryption for sensitive data
- PII data masking and anonymization
- Secure file upload with virus scanning
- Data retention and deletion policies

**Access Control:**
- Role-based access control for form data
- Multi-factor authentication for admin access
- Audit logging for all data access
- Secure API authentication and authorization

**Compliance:**
- GDPR compliance for data handling
- HIPAA compliance for health information
- PCI DSS compliance for payment data
- SOC 2 compliance for data security

**Monitoring:**
- Real-time security monitoring and alerts
- Intrusion detection and prevention
- Data breach notification systems
- Regular security audits and assessments
```

**보안별 프롬프트:**

```
Implement **data encryption** for sensitive form submissions and user information
```

```
Add **access control** to restrict form data access based on user roles and permissions
```

```
Set up **security monitoring** to detect and prevent unauthorized access to form data
```

## 명령 참조

### 필수 명령

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

### 필드 참조

`@fieldName` 구문을 사용하여 프롬프트의 기존 필드를 참조합니다.

- `@email` - 참조 전자 메일 필드
- `@firstName` - 참조 이름 필드
- `@maritalStatus` - 참조 결혼 상태 필드

### 구성 요소 유형

**입력 구성 요소:**

- `text`, `email`, `number`, `tel`, `date`, `checkbox`, `radio`, `dropdown`, `file`, `textarea`

**컨테이너 구성 요소:**

- `fieldset`, `panel`, `repeatable`, `wizard`

### 구성 요소 속성

**유니버설 속성(모든 구성 요소):**

- **유형**: 구성 요소 유형
- **이름**: 양식 제출을 위한 필드 식별자
- **레이블**: 필드에 대한 표시 텍스트
- **설명**: 필드에 대한 도움말 텍스트
- **표시**: 초기 가시성에 대한 부울 값
- **필수**: 필수 필드에 대한 부울 값

**입력 필드 속성:**

- **값**: 기본값/초기값
- **플레이스홀더**: 입력 필드에 대한 힌트 텍스트
- **최소값**: 최소값 (숫자/날짜의 경우)
- **최대값**: 최대값 (숫자/날짜의 경우)

**파일 업로드 속성:**

- **허용**: 파일 유형 (.pdf, .doc, .docx, .jpg, .png 등)
- **다중**: 여러 파일 선택을 위한 부울 값

**선택 컨트롤 속성:**

- **옵션**: 드롭다운에 대한 선택 사항 (쉼표로 구분된 목록)
- **선택됨**: 체크박스/라디오에 대한 기본 선택

**컨테이너 속성:**

- **Fieldset**: 관련 필드 그룹화
- **반복 가능**: 반복 가능한 섹션에 대한 부울 값

**고급 속성:**

- **가시적 표현**: 조건부 가시성을 위한 공식 (=formula)
- **값 표현식**: 계산된 값에 대한 공식 (=formula)

### 통합 명령

**제출 동작:**

- 이메일 알림
- REST API 제출
- 클라우드 스토리지(Azure, SharePoint)
- 워크플로우 자동화(Power Automate, Workfront Fusion)
- 마케팅 플랫폼(Marketo)
- CRM 통합

### 프롬프트 구문 지침

- **필드 참조**: 기존 필드에 `@fieldName`을(를) 사용합니다.
- **명령**: 특정 작업에 `/command` 사용
- **자연어**: 요구 사항을 명확하고 구체적으로 설명합니다.

### 유효성 검사 목록

포괄적인 모범 사례와 유효성 검사 지침은 [Forms Experience Builder 시작 안내서](forms-ai-assistant-getting-started.md#best-practices)를 참조하십시오.

*이 프롬프트 라이브러리는 사용자 피드백 및 새로운 Forms Experience Builder 기능에 따라 계속 업데이트됩니다. 최신 기능과 예제를 보려면 [AEM Forms 설명서](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/home.html)를 확인하십시오.*
