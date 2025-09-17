---
title: Forms Experience Builder - 프롬프트 라이브러리
description: Forms 관리 UI, 적응형 양식 편집기 및 범용 편집기에서 AI 어시스턴트를 활용하여 양식을 작성하기 위한 검증된 프롬프트 패턴과 예제 모음입니다.
feature: Edge Delivery Services
hide: true
index: false
hidefromtoc: true
role: Admin, Architect, Developer
exl-id: c8f64082-a23f-4919-ad66-042faad77d31
source-git-commit: fe34b44d02c308e7d18a08dd05f21abc67bd0cb2
workflow-type: ht
source-wordcount: '2193'
ht-degree: 100%

---


# Forms Experience Builder - 프롬프트 라이브러리

Forms Experience Builder에 최적화된 재사용 가능한 프롬프트 패턴과 예제 모음. 이 간소화된 라이브러리는 LLM 기반 스마트 필드와 브랜드 일관성에 대한 향상된 지원을 통해 “처음부터 만들기”와 “가져오기 및 변환”이라는 두 가지 핵심 생성 방법에 중점을 둡니다.

>[!NOTE]
>
> Forms Experience Builder는 얼리 어답터 프로그램에서 사용할 수 있습니다. 액세스 권한을 요청하려면 회사 이메일 주소를 통해 `aem-forms-ea@adobe.com`으로 이메일을 보내시기 바랍니다.

>[!IMPORTANT]
>
> **변경될 수 있는 설명서**: 이 프롬프트 라이브러리는 현재 제품과의 일치 여부를 테스트 중이며 업데이트 및 개정이 이루어질 수 있습니다. 얼리 어답터 프로그램이 진행되는 동안 Forms Experience Builder가 계속 발전함에 따라 프롬프트. 예시 및 모범 사례가 변경될 수 있습니다.

## 이 프롬프트 라이브러리 사용

이 라이브러리는 일반적인 양식 작성 시나리오에 재사용 가능한 프롬프트 패턴을 제공합니다. 종합적인 모범 사례는 [Forms Experience Builder 시작 안내서](forms-ai-assistant-getting-started.md#best-practices)를 참조하십시오.

### 이 라이브러리에 대한 간단한 팁

- **예시로 시작** - 제공된 프롬프트를 템플릿으로 사용하고 요구 사항에 맞게 조정
- **두 가지 생성 방법** - 처음부터 만들기 또는 가져오기 및 변환 접근 방식 선택
- **구체적으로 지정** - 일반적인 예시 세부 정보 추가
- **철저히 테스트** - 항상 특정 환경에서 결과 확인

### 브랜드 템플릿 및 스타일

**일관된 양식 생성을 위해 브랜드 자산을 미리 준비:**

- **브랜드 템플릿** - 조직의 색상, 글꼴 및 레이아웃 패턴을 사용하여 표준화된 양식 템플릿 준비
- **스타일 가이드라인** - Forms Experience Builder가 적용할 수 있는 일관된 필드 스타일, 버튼 디자인 및 간격 표준 정의
- **구성 요소 라이브러리** - 브랜드 아이덴티티와 일치하는 재사용 가능한 양식 구성 요소를 준비하기 위해 개발 팀과 협력
- **시각적 자산** - 양식 통합을 위한 로고, 아이콘 및 배경 요소 준비

<!-- **Example Brand Application Prompt:**

    Apply our financial services brand template with:
    - Corporate blue (#003366) and silver (#C0C0C0) color scheme
    - Open Sans font family for all text
    - 16px minimum font size for accessibility
    - Consistent 24px spacing between sections
    - Corporate logo in header with proper sizing
    - Professional button styling with hover effects

>[!NOTE]
>
>**Custom Components**: Check with your development team about using organization-specific components and their compatibility with Forms Experience Builder before implementing custom brand elements.

>[!NOTE]
>
> This prompt library has been updated to reflect the streamlined Forms Experience Builder capabilities. Some advanced integration and testing features shown in examples may require additional configuration.

-->


## 점진적 개발 예제

다음 예제에서는 간단한 것부터 시작하여 점차 복잡도를 추가하는 방식으로 단계별로 양식을 작성하는 방법을 보여 줍니다.

### 예제 1: 점진적으로 연락처 양식 작성

**1단계 - 간단하게 시작하기:**

    이름, 이메일, 메시지 필드가 있는 기본 연락처 양식 만들기

**2단계 - 유효성 검사 추가:**

    적절한 유효성 검사를 통해 @name 및 @email을 필수 필드로 만들기

**3단계 - 사용자 경험 향상:**

    플레이스홀더 텍스트 추가: @name “이름”, @email “your.email@company.com”, @message “어떻게 도와드릴 수 있는지 알려 주세요”

**4단계 - 고급 기능 추가:**

    드롭다운 문의 유형을 다음 옵션으로 추가: “일반 질문”, “지원 요청”, “영업 문의”, “파트너십”

**5단계 - 조건 논리 구현:**

    /create-rule @inquiryType이 “지원 요청”과 같은 경우에만 @urgencyLevel 드롭다운(낮음, 보통, 높음) 표시

### 예제 2: 점진적으로 등록 양식 작성

**1단계 - 기본 구조:**

    개인 정보 패널이 있는 사용자 등록 양식 만들기

**2단계 - 필수 필드 추가:**

    적절한 유효성 검사를 통해 @firstName, @lastName, @email, @phoneNumber에 대한 필드 추가

**3단계 - 비즈니스 로직 추가:**

    규칙 만들기: @age가 18세 미만인 경우 부모/보호자 정보 섹션 표시

**4단계 - 환경 설정에 따라 개선:**

    @newsletterSubscription, @marketingConsent, @termsAccepted를 사용하여 환경 설정 패널 추가

**5단계 - 파일 업로드 추가:**

    @profilePicture에 대해 5MB 크기 제한의 파일 업로드 필드 포함

## 양식 생성 및 관리

**사용 시기:** 새로운 양식을 만들거나 기존 양식을 수정해야 하는 경우.

**사용 방법:** 두 가지 접근 방식 중 선택: 처음부터 만들기 또는 가져오기 및 변환([시작 안내서](forms-ai-assistant-getting-started.md#two-ways-to-create-forms) 참조).

**예시 프롬프트 - 간단한 양식 생성:**

    다음을 사용하여 고객 피드백 양식 만들기:
    - 상품평 (별점 1~5점)
    - 자세한 피드백을 위한 댓글 필드
    - 고객 이메일 (선택 사항)
    - 이메일 알림으로 제출

**예시 프롬프트 - 복잡한 양식 생성:**

    다음을 포함하여 종합적인 직원 온보딩 양식 만들기:
    
    **개인 정보 섹션:**
    - 성명 (이름, 중간 이름, 성)
    - 생년월일 (나이 확인 포함)
    - 연락처 정보 (이메일, 전화번호, 주소)
    - 비상 연락처 정보
    
    **고용 정보:**
    - 직위 및 부서 선택
    - 영업일 확인이 포함된 시작일
    - 기밀 유지 고지가 포함된 급여 정보
    - 보고 구조
    
    **문서 업로드:**
    - 이력서/CV 업로드 (PDF, DOC, DOCX)
    - 신원 확인 문서
    - 세금 양식 및 은행 정보
    - 서명된 고용 계약서 계약
    
    **선호 사항:**
    - 비용 계산기를 사용한 혜택 선택
    - 근무 일정 선호 사항
    - 교육 요구 사항
    - 필요한 장비
    
    **검증 규칙:**
    - 이메일 형식 검증
    - 전화번호 형식 검증
    - 연령은 18세 이상이어야 함
    - 모든 필수 서류를 업로드해야 함
    - 약관에 동의해야 함
    
    **제출 액션:**
    - 신입 직원에게 확인 이메일 보내기
    - HR 부서에 알림
    - HR 시스템에 직원 기록 생성
    - 오리엔테이션 회의 일정 예약

**양식 관리 프롬프트:**

    이 PDF 신청서 가져오기 및 향상된 유효성 검사 기능을 갖춘 적응형 양식으로 변환
    
    소셜 미디어 핸들과 선호하는 연락 방법을 포함하도록 기존 연락처 양식 업데이트
    
    등록 양식을 개인 정보, 기본 설정, 확인의 3단계 마법사로 재구성

## 필드 관리 및 구성

**사용 시기:** 양식 필드를 추가, 수정 또는 구성해야 할 경우.

**사용 방법:** 필드 유형, 유효성 검사 규칙 및 사용자 경험 요구 사항을 구체적으로 명시합니다.

**예시 프롬프트 - 기본 필드 추가:**

    “회사 이름”에 대한 텍스트 입력 필드를 추가하고 “회사 이름을 입력하세요”라는 플레이스홀더 추가

**예시 프롬프트 - 고급 필드 구성:**

    다음을 포함하는 포괄적인 주소 섹션 추가
    
    **도로 주소:**
    - 주소 줄 1 (필수, 최대 100자)
    - 주소 줄 2 (선택 사항, 최대 100자)
    - 도시 (필수, 일반 도시가 있는 드롭다운)
    - 주/도 (필수, 드롭다운)
    - 우편번호 (필수, 형식 유효성 검사)
    - 국가 (필수, 기본값은 “미국”)
    
    **유효성 검사 규칙:**
    - 우편번호는 주 선택과 일치해야 함
    - 주소 줄 1은 비워 둘 수 없음
    - 도시는 선택한 도시에 대한 유효한 도시여야 함 상태
    
    **사용자 경험:**
    - 주소 필드 자동 완성
    - 명확한 레이블 및 도움말 텍스트
    - 모바일 친화적 입력 필드
    - 접근성 준수

**필드 구성 프롬프트:**

    @email 필드를 실시간 유효성 검사 및 사용자 정의 오류 메시지와 함께 필수로 설정
    
    미국, 캐나다, 영국, 독일, 프랑스 및 “기타” 옵션을 제공하는 @country에 대한 드롭다운 추가
    
    (XXX) XXX-XXXX 형식 및 유효성 검사를 통해 @phoneNumber 필드 구성
    
    PDF 및 DOC 제한이 있는 @resume에 대한 파일 업로드 필드 추가 (최대 5MB)

## LLM 강화 스마트 필드

**사용 시기:** AI의 지식 기반을 활용한 미리 채워진 옵션이 있는 필드가 필요한 경우.

**사용 방법:** 종합적인 데이터 세트가 필요한 필드 요청 - AI는 기본 제공 지식을 사용하여 자동으로 옵션을 채울 수 있습니다.

### 지리적 및 위치 분야

**공항 및 교통:**

    모든 주요 국제 공항을 포함해 출발 공항 드롭다운 추가
    IATA 코드 및 전체 이름을 포함해 도착 공항 필드 추가
    사용자 위치에서 가장 가까운 공항 필드 생성
    유럽 도시의 기차역 선택 항목 추가

**행정구역:**

    약어가 포함된 미국 주의 전체 목록 추가
    ISO 코드와 전체 이름을 포함해 국가 드롭다운 생성
    시간대가 포함된 주요 세계 도시 필드 추가
    캐나다 주 및 지역 드롭다운 포함
    영국 카운티 및 우편 지역 필드 추가

### 비즈니스 및 산업 데이터

**회사 분류:**

    NAICS 코드를 사용하여 산업 분류에 대한 필드 추가
    사업체 유형(LLC, 법인, 파트너십 등) 드롭다운 만들기
    회사 규모 카테고리(스타트업, 중소기업, 대기업)에 대한 필드 추가
    대규모 조직에 대한 부서 선택 항목 포함
    전문 서비스 유형에 대한 필드 추가

**전문 분류:**

    일반적인 산업 역할을 포함해 직책에 대한 필드 추가
    분야별 전문 자격증 드롭다운 만들기
    학위 유형을 포함해 교육 수준 포함
    경력 연도 범위에 대한 필드 추가
    프로그래밍 언어 및 프레임워크에 대한 선택 항목 만들기

### 표준 및 규제

**재정 및 법률:**

    기호와 환율을 포함해 통화 코드 필드 추가
    국가별 세금 ID 유형 드롭다운 만들기
    법률 문서 유형에 대한 필드 포함
    보안 기능을 갖춘 결제 방법 옵션 추가
    국가별 은행기관 선택 항목 만들기

**기술 표준:**

    확장자가 포함된 파일 형식 유형 드롭다운 추가
    네트워크 프로토콜 옵션 포함
    데이터베이스 유형 및 버전에 대한 필드 추가
    API 인증 방법에 대한 선택 항목 만들기

### 헬스 케어 및 의료

**의료 분류:**

    의료 전문 분야 필드 추가
    일반 이름을 사용하여 일반적인 약물 드롭다운 만들기
    보험 제공자 유형에 대한 필드 포함
    의료 비상 연락처 관계에 대한 선택 항목 추가
    식이 제한 및 알레르기에 대한 필드 만들기

### 시간 및 달력 인텔리전스

**날짜 및 시간 필드:**

    시간대 처리가 포함된 영업 시간 필드 추가
    국가별 공휴일 드롭다운 만들기
    날짜 범위에 계절 옵션 포함
    회의실 예약 가능 여부에 대한 필드 추가
    반복되는 회의 패턴에 대한 선택 항목 만들기

### 제품 및 서비스 카테고리

**전자 상거래 분류:**

    하위 카테고리가 있는 제품 카테고리에 대한 필드 추가
    배송 예상 시간을 포함해 배송 방법 드롭다운 만들기
    반품 정책 옵션에 대한 필드 포함
    고객 우선순위 수준에 대한 선택 항목 추가
    구독 청구 주기에 대한 필드 만들기

**스마트 필드 프롬프트 예시:**

    “IATA 코드와 도시 이름을 포함해 전 세계 주요 공항을 모두 포함하는 출발 공항 필드 추가”
    
    “기술 하위 카테고리를 포함해 표준 NAICS 분류를 사용하여 포괄적인 산업 분야 만들기
    
    “선택한 직무 분야에 따라 조정되는 전문 자격증 드롭다운 포함”
    
    “선택한 국가를 기준으로 형식이 지정된 국제 전화번호 필드 추가”
    
    “국가별, 순위별로 주요 대학을 정리한 대학선발 필드 구축”

## 규칙 생성 및 비즈니스 로직

**사용 시기:** 조건 논리, 유효성 검사 규칙 또는 비즈니스 프로세스를 구현해야 하는 경우

**사용 방법:** 조건과 액션을 지정하여 비즈니스 로직을 명확하게 설명

**예시 프롬프트 - 단순한 조건부 논리:**

    @maritalStatus가 “기혼”일 때만 @spouseInformation 패널을 표시하는 규칙 만들기

**예시 프롬프트 - 복잡한 비즈니스 규칙:**

    종합적인 대출 신청 유효성 검사 구현
    
    **소득 검증:**
    - @annualIncome이 30000 미만인 경우:
    - 경고 메시지 표시: “소득이 요청한 대출 금액에 부족할 수 있습니다”
    - 추가 소득 증빙 서류 요구
    - 메시지 표시: “추가 서류가 필요할 수 있습니다”
    - @annualIncome이 100000보다 큰 경우:
    - Premium 서비스 옵션 표시
    - 우선 처리 체크박스 활성화
    
    **연령 기반 검증:**
    - @age가 18세 미만인 경우:
    - 부모/보호자 정보 섹션 표시
    - 부모 서명 업로드 필수
    - 제출 버튼 텍스트를 “검토를 위해 제출”로 변경
    - @age가 65세 이상인 경우:
    - 노인 할인 옵션 표시
    - 접근성 기본 설정 섹션 추가

**규칙 관련 프롬프트:**

    @maritalStatus가 “기혼” 또는 “동거 관계”일 때만 @spouseInformation 패널을 표시하는 **가시성 규칙** 만들기
    
    이전 답변을 기반으로 추가 질문이 나타나는 곳에 **점진적 공개** 추가. 기본 정보부터 시작하여 관련 후속 조치 보여 주기
    
    @country 선택 시 관련 필드가 자동으로 설정되는 **스마트 기본값** 구현. 수동 재정의 허용

## 데이터 통합 및 제출

**사용 시기:** 백엔드 시스템, 데이터베이스 또는 외부 서비스에 양식을 연결해야 하는 경우.

**사용 방법:** 기본 제출 설정부터 시작한 다음 점진적으로 추가 통합을 추가합니다. 통합 유형, 데이터 형식 요구 사항 및 오류 처리 환경 설정을 지정합니다.

**예제 프롬프트 - 기본 제출로 시작:**

    @applicationForm에 대한 기본 양식 제출 구성:
    
    **기본 제출:**
    - REST 엔드포인트로 양식 데이터 전송: “/API/v1/applications”
    - JSON으로 데이터 형식 지정
    - 성공 메시지 표시: “신청이 성공적으로 제출되었습니다”
    - 제출에 실패하면 오류 메시지 표시: “제출에 실패했습니다. 다시 시도하세요”

**점진적인 보조 액션 추가 예제:**

    @applicationForm에 이메일 알림 추가: 신청 참조 번호와 함께 @email 주소로 확인 이메일 전송
    
    @applicationForm에 CRM 통합 추가: @firstName, @lastName, @email로 새 리드 레코드 생성 및 상태 “새 신청”으로 설정

**예시 프롬프트 - 표준 다중 채널 제출:**

    여러 데이터 대상을 사용하여 양식 제출 구성:
    
    **주요 제출:**
    - REST 엔드포인트로 양식 데이터 전송: “/API/v1/applications”
    - API 키가 있는 인증 헤더 포함
    - 주소 및 고용에 대한 중첩된 오브젝트를 사용하여 데이터를 JSON으로 포맷
    - 감사 메시지를 표시하여 성공 응답(201) 처리
    
    **보조 액션:**
    - @이메일 주소로 지원자에게 알림 이메일 전송
    - 추적 시스템에 지원서 데이터 복사
    - 승인 프로세스를 위한 워크플로 트리거
    - 리드 상태가 “새 신청”인 CRM에 레코드 생성
    
    **오류 처리:**
    - 기본 제출에 실패하면 로컬에 데이터를 저장하고 다시 시도합니다.
    - 사용자 친화적인 오류 메시지 표시: “제출을 일시적으로 사용할 수 없습니다”
    - 양식 데이터를 백업으로 다운로드하는 옵션 제공
    - 제출 실패에 대한 알림 이메일 관리팀에 전송
    
    **성공 흐름:**
    - 신청 참조 번호가 있는 확인 페이지로 리디렉션
    - 다음 단계가 포함된 확인 이메일 전송
    - 예상 처리 일정 표시

**통합 관련 프롬프트:**

    이 양식을 **CRM 시스템**에 연결하여 새로운 리드를 생성합니다. @firstName을 FirstName에, @email을 Email에 매핑하고, LeadSource를 “웹 양식”으로, 상태를 “신규”로 설정
    
    양식이 제출될 때 **워크플로 트리거** 설정. 모든 양식 데이터를 전달하고 관리자 알림을 통해 승인 워크플로 트리거
    
    양식 제출을 레코드로 저장하기 위해 **데이터베이스 통합** 구성. 업로드된 문서로 각 제출물에 대한 새 폴더 만들기

<!-- ## Import & Convert Existing Forms

**When to use:** When you have existing forms, documents, or designs to transform into modern AEM forms.

**How to use:** Upload your source file and describe the conversion requirements (see [Import Guide](forms-ai-assistant-getting-started.md#2-import-and-convert)).


**Design Import Prompts:**

    Import this **design mockup** and convert it into an adaptive form. Maintain the exact visual design but add proper validation and mobile responsiveness

    Analyze this **image of a paper form** and recreate it digitally. Improve the layout for better mobile experience while keeping all mandatory fields

    Convert this **existing HTML form** to AEM adaptive form format. Preserve all functionality but add AEM-specific features like rules and themes

## Mobile Optimization & Responsiveness

**When to use:** When forms need to work seamlessly across all device types and screen sizes.

**How to use:** Start with basic mobile optimization, then enhance with advanced features. Emphasize mobile-first approach and specify breakpoint behaviors incrementally.

**Example Prompt - Start with Basic Mobile Optimization:**

    Make @contactForm mobile-friendly with:
    
    **Basic Mobile Layout:**
    - Single column layout for all form sections
    - Larger touch targets for buttons and inputs
    - Responsive design that works on phones and tablets

**Then Add Advanced Mobile Features:**

    Enhance @contactForm mobile experience with:
    - Sticky submit button at bottom of screen
    - Touch-friendly date pickers
    - Swipe gestures for multi-step navigation

**Example Prompt - Comprehensive Mobile-First Optimization:**

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

**Mobile-Specific Prompts:**

    Make this form **touch-friendly** with larger buttons and simplified navigation for mobile users

    Optimize form for **tablet users** with appropriate field sizes and navigation patterns

    Add **swipe gestures** for multi-step form navigation on mobile devices

## Accessibility & Compliance

**When to use:** When forms need to meet accessibility standards (WCAG) or compliance requirements.

**How to use:** Specify the required compliance level and any specific accessibility features needed.

**Example Prompt - Basic Accessibility:**

    Make @contactForm accessible with:
    
    **Basic Accessibility:**
    - Proper ARIA labels for all form fields
    - Keyboard navigation support
    - High contrast color scheme
    - Screen reader compatibility
    - Focus indicators for all interactive elements

**Example Prompt - Advanced Accessibility:**

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

**Accessibility-Specific Prompts:**

    Add **screen reader support** to this form with proper ARIA labels and announcements

    Implement **keyboard navigation** for all form interactions and navigation elements

    Ensure **color contrast** meets WCAG AA standards for all text and interactive elements  

## Performance Optimization

**When to use:** When forms need to load quickly and perform well under various conditions.

**How to use:** Specify performance requirements and optimization strategies.

**Example Prompt - Basic Performance:**

    
Optimize @contactForm for performance:

**Loading Optimization:**

- Lazy load non-critical form sections
- Minimize initial bundle size
- Optimize images and assets
- Enable caching for static resources
    

**Example Prompt - Advanced Performance:**

    
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
    

**Performance-Specific Prompts:**

    
Optimize form **loading speed** by implementing progressive loading and asset optimization
    

    
Add **auto-save functionality** to prevent data loss during form completion
    

    
Implement **offline support** so users can complete forms without internet connection
    

## Testing & Quality Assurance

**When to use:** When forms need comprehensive testing to ensure reliability and user satisfaction.

**How to use:** Specify testing scenarios, validation requirements, and quality metrics.

**Example Prompt - Basic Testing:**

    
Add comprehensive testing for @contactForm:

**Functional Testing:**

- Test all form field validations
- Verify submit functionality works correctly
- Test error handling and user feedback
- Validate conditional logic and rules
    

**Example Prompt - Advanced Testing:**

    
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
    

**Testing-Specific Prompts:**

    
Add **automated testing** for all form validations and submit functionality
    

    
Implement **user acceptance testing** scenarios for complete form workflows
    

    
Set up **performance monitoring** to track form load times and user interactions
    
-->

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
| `/help` | 도움 받기 | `/help how to implement multi-step validation?` |

### 필드 참조

프롬프트에서 기존 필드를 참조하려면 `@fieldName` 구문 사용:

- `@email` - 이메일 필드 참조
- `@firstName` - 이름 필드 참조
- `@maritalStatus` - 결혼 상태 필드 참조

### 구성 요소 유형

**입력 구성 요소:**

- `text`, `email`, `number`, `tel`, `date`, `checkbox`, `radio`, `dropdown`, `file`, `textarea`

**컨테이너 구성 요소:**

- `fieldset`, `panel`, `repeatable`, `wizard`

### 구성 요소 속성

**범용 속성 (모든 구성 요소):**

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

**선택 제어 속성:**

- **옵션**: 드롭다운에 대한 선택 사항 (쉼표로 구분된 목록)
- **선택됨**: 체크박스/라디오에 대한 기본 선택

**컨테이너 속성:**

- **Fieldset**: 관련 필드 그룹화
- **반복 가능**: 반복 가능한 섹션에 대한 부울 값

**고급 속성:**

- **가시적 표현**: 조건부 가시성을 위한 공식 (=formula)
- **값 표현식**: 계산된 값에 대한 공식 (=formula)

### 통합 명령

**제출 액션:**

- 이메일 알림
- REST API 제출
- 클라우드 스토리지(Azure, SharePoint)
- 워크플로 자동화 (Power Automate, Workfront Fusion)
- 마케팅 플랫폼 (Marketo)
- CRM 통합

### 프롬프트 구문 지침

- **필드 참조**: 기존 필드에 `@fieldName`사용
- **명령**: 특정 액션에 `/command` 사용
- **자연어**: 요구 사항을 명확하고 구체적으로 설명

### 유효성 검사 체크리스트

포괄적인 모범 사례 및 유효성 검사 지침은 [Forms Experience Builder 시작 안내서](forms-ai-assistant-getting-started.md#best-practices)를 참조하십시오.

*이 프롬프트 라이브러리는 사용자 피드백과 새로운 Forms Experience Builder 기능을 기반으로 지속적으로 업데이트됩니다. 최신 기능과 예제를 보려면 [AEM Forms 설명서](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/home.html)를 확인하십시오.*
