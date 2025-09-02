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
workflow-type: tm+mt
source-wordcount: '2193'
ht-degree: 13%

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

- **브랜드 템플릿** - 조직의 색상, 글꼴 및 레이아웃 패턴을 사용하여 표준화된 양식 템플릿을 준비합니다.
- **스타일 지침** - Forms Experience Builder가 적용할 수 있는 일관된 필드 스타일, 단추 디자인 및 간격 표준을 정의합니다.
- **구성 요소 라이브러리** - 개발 팀과 함께 브랜드 ID와 일치하는 재사용 가능한 양식 구성 요소를 준비합니다.
- **시각적 Assets** - 양식 통합을 위해 로고, 아이콘 및 배경 요소 준비

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

    이름, 전자 메일 및 메시지 필드가 있는 기본 연락처 양식을 만듭니다

**2단계 - 유효성 검사 추가:**

    적절한 유효성 검사를 사용하여 필수 필드를 @name 및 @email

**3단계 - 사용자 경험 향상:**

    자리 표시자 텍스트 추가: @name전체 이름&quot;, @emailyour.email@company.com&quot;, @message&quot;도움말 방법 설명&quot;

**4단계 - 고급 기능 추가:**

    옵션이 있는 드롭다운 inquiryType 추가: &quot;일반 질문&quot;, &quot;지원 요청&quot;, &quot;판매 조회&quot;, &quot;파트너 관계&quot;

**5단계 - 조건 논리 구현:**

    /create-rule은 @inquiryType이 &quot;지원 요청&quot;과 같은 경우에만 @urgencyLevel 드롭다운(낮음, Medium, 높음)을 표시합니다

### 예제 2: 점진적으로 등록 양식 작성

**1단계 - 기본 구조:**

    개인 정보 패널을 사용하여 사용자 등록 양식을 만듭니다

**2단계 - 필수 필드 추가:**

    적절한 유효성 검사를 사용하여 @firstName, @lastName, @email, @phoneNumber에 대한 필드 추가

**3단계 - 비즈니스 논리 추가:**

    규칙 만들기: @age이 18세 미만이면 부모/보호자 정보 섹션을 표시

**4단계 - 기본 설정으로 개선:**

    @newsletterSubscription, @marketingConsent, @termsAccepted이 포함된 환경 설정 패널 추가

**5단계 - 파일 업로드 추가:**

    크기 제한이 5MB인 @profilePicture의 파일 업로드 필드를 포함합니다

## 양식 생성 및 관리

**사용 시기:** 새 양식을 만들거나 기존 양식을 수정해야 하는 경우.

**사용 방법:** 두 가지 방법 중 하나를 선택하십시오. 처음부터 만들기 또는 가져오기 및 변환([시작 안내서](forms-ai-assistant-getting-started.md#two-ways-to-create-forms) 참조).

**예제 프롬프트 - 간단한 양식 만들기:**

    
    - 제품 등급(별 1~5개)
    - 자세한 피드백에 대한 댓글 필드
    - 고객 이메일(선택 사항)
    - 이메일 알림에 제출
(으)로 고객 피드백 양식 만들기
**예제 프롬프트 - 복잡한 양식 만들기:**

    다음을 사용하여 포괄적인 직원 온보딩 양식을 만드십시오.
    
    **개인 정보 섹션:**
    - 전체 이름(처음, 중간, 마지막)
    - 생년월일(나이 확인)
    - 연락처 정보(전자 메일, 전화, 주소)
    - 긴급 연락처 세부 정보
    
    **취업 세부 정보:**
    - 직책 및 부서 선택
    - 근무일 확인 시작 날짜
    - 기밀 유지 표시가 있는 급여 정보
    - 보고 구조
    
    **문서 업로드:**
    - 다시 시작/CV 업로드(PDF, DOC, DOCX)
    - ID 확인 문서
    - 세금 양식 및 금융 정보
    - 고용 계약
    
    **환경 설정:**
    - 비용 계산기를 통한 혜택 선택
    - 근무 일정 환경 설정
    - 교육 요구 사항
    - 장비 요구 사항
    
    **검증 규칙:**
    - 전자 메일 형식 유효성 검사
    - 전화 번호 형식 유효성 검사
    - 연령이 18세 이상이어야 함
    - 모든 필수 문서를 업로드해야 함
    - 약관을 수락해야 함
    
    **작업 제출:**
    - 새 직원에게 확인 전자 메일 보내기
    - HR 부서에 알림
    - HR 시스템에서 직원 기록 만들기
    - 방향 모임

**양식 관리 프롬프트:**

    이 PDF 응용 프로그램 양식을 가져와 유효성 검사가 향상된 적응형 양식으로 변환
    
    소셜 미디어 핸들과 기본 연락 방법을 포함하도록 기존 연락 양식을 업데이트
    
    등록 양식을 개인 정보, 환경 설정, 확인
의 3단계 마법사로 다시 구성합니다.

## 필드 관리 및 구성

**사용할 시점:** 양식 필드를 추가, 수정 또는 구성해야 하는 경우.

**사용 방법:** 필드 형식, 유효성 검사 규칙 및 사용자 경험 요구 사항에 대해 구체적으로 지정합니다.

**예제 프롬프트 - 기본 필드 추가:**

    자리 표시자 &quot;회사 이름 입력&quot;이 있는 &quot;회사 이름&quot;에 대한 텍스트 입력 필드를 추가하십시오.

**예제 프롬프트 - 고급 필드 구성:**

    주소 섹션을 다음과 같이 추가합니다.
    
    **상세 주소:**
    - 주소 라인 1(필수, 최대 100자)
    - 주소 라인 2(선택 사항, 최대 100자)
    - 구/군(일반 도시의 드롭다운)
    - 시/도(필수, 드롭다운)
    - 우편 번호(필수, 형식 유효성 검사)
    - 국가(필수, 기본 &quot;미국&quot;)
    
    **유효성 검사 규칙:**
    - 우편 번호는 상태 선택과 일치해야 함
    - 주소 라인 1은 비어 있을 수 없음
    - 구/군/시는 선택한 상태의 올바른 도시여야 함
    
    **사용자 환경:**
    - 주소에 대한 자동 완성 필드
    - 레이블 및 도움말 텍스트 지우기
    - 모바일 친화적 입력 필드
    - 접근성 준수

**필드 구성 프롬프트:**

    실시간 유효성 검사 및 사용자 지정 오류 메시지와 함께 @email 필드를 만드십시오
    
    미국, 캐나다, 영국, 독일, 프랑스 및 &quot;기타&quot; 옵션과 함께 @country 드롭다운을 추가하십시오.
    
    형식(XXX) XXX-XXXX 및 유효성 검사를 사용하여 @phoneNumber 필드를 구성하십시오.
    
    PDF 및 DOC 제한 사항과 함께 @resume 파일 업로드 필드를 추가하십시오.

## LLM 향상 스마트 필드

**사용 시기:** AI의 기술 자료를 활용하는 미리 채워진 옵션이 있는 필드가 필요한 경우.

**사용 방법:** 포괄적인 데이터 집합이 필요한 요청 필드 - AI는 기본 제공 지식을 사용하여 옵션을 자동으로 채울 수 있습니다.

### 지리적 및 위치 필드

**공항 및 교통 수단:**

    모든 주요 국제 공항이 있는 출발 공항의 드롭다운을 추가합니다
    IATA 코드와 전체 이름이 있는 도착 공항 필드를 추가합니다
    사용자 위치에 가장 가까운 공항 필드를 만듭니다
    유럽 도시의 기차역 선택 사항을 추가합니다

**관리 영역:**

    약어가 있는 미국 주의 전체 목록 추가
    ISO 코드와 전체 이름이 있는 국가 드롭다운을 만듭니다
    시간대가 있는 주요 세계 도시에 대한 필드 추가
    캐나다 지방 드롭다운 포함
    영국 카운티 및 우편 지역에 대한 필드 추가

### 비즈니스 및 업계 데이터

**회사 분류:**

    NAICS 코드를 사용하여 업계 분류를 위한 필드 추가
    비즈니스 엔터티 형식(LLC, Corporation, Partnership 등) 드롭다운 만들기
    회사 규모 범주(시작, SME, 엔터프라이즈)에 대한 필드 추가
    대규모 조직에 대한 부서 선택 포함
    전문 서비스 유형에 대한 필드 추가

**전문 분류:**

    일반적인 산업 역할을 가진 직책 필드를 추가
    분야별 전문 자격증 드롭다운을 만듭니다
    학위 유형을 가진 교육 수준 포함
    다년간의 경험 범위에 대한 필드를 추가
    프로그래밍 언어 및 프레임워크에 대한 선택 항목 만들기

### 표준 및 규정

**재무 및 법적 정보:**

    기호 및 환율이 포함된 통화 코드 필드 추가
    국가별 세금 ID 유형 드롭다운 만들기
    법적 문서 유형 필드 포함
    보안 기능이 포함된 결제 방법 옵션 추가
    국가별 금융 기관 선택 항목 만들기

**기술 표준:**

    확장명이 있는 파일 형식 형식의 드롭다운을 추가합니다
    네트워크 프로토콜 옵션 포함
    데이터베이스 형식 및 버전에 대한 필드 추가
    API 인증 방법에 대한 선택 항목 만들기

### 의료 및 의료

**의료 분류:**

    전문 의약품 분야 필드 추가
    일반 이름을 가진 일반 의약품 드롭다운 만들기
    보험 공급자 유형을 위한 필드 포함
    의료 비상 연락처 관계에 대한 선택 항목 추가
    식이 제한 및 알레르기에 대한 필드 만들기

### 시간 및 일정 인텔리전스

**날짜 및 시간 필드:**

    표준 시간대 처리가 포함된 업무 시간 필드 추가
    국가별 공휴일 드롭다운 만들기
    날짜 범위가 포함된 계절 옵션 포함
    가용성이 있는 회의실 예약 필드 추가
    되풀이 모임 패턴에 대한 선택 항목 만들기

### 제품 및 서비스 범주

**전자 상거래 분류:**

    하위 범주가 있는 제품 범주에 대한 필드 추가
    게재 예상 배송 방법의 드롭다운을 만듭니다
    반환 정책 옵션에 대한 필드 포함
    고객 우선 순위 수준에 대한 선택 항목 추가
    구독 청구 주기에 대한 필드 만들기

**스마트 필드 프롬프트 예:**

    &quot;IATA 코드 및 도시 이름을 포함한 전 세계의 모든 주요 공항과 함께 출발 공항 필드를 추가합니다.
    
    &quot;기술 하위 범주가 있는 표준 NAICS 분류를 사용하여 포괄적인 산업 필드를 만듭니다.
    
    &quot;선택한 직무 필드를 기반으로 적응하는 전문 인증 드롭다운을 포함합니다.
    
    &quot;선택한 국가를 기반으로 포맷하는 국제 전화 번호 필드를 추가합니다.
    
    &quot;국가별 및 순위별로 구성된 주요 기관과 함께 대학 선택 필드를 만듭니다.

## 규칙 생성 및 비즈니스 논리

**사용할 시기:** 조건부 논리, 유효성 검사 규칙 또는 비즈니스 프로세스를 구현해야 하는 경우.

**사용 방법:** 조건 및 작업을 지정하여 비즈니스 논리를 명확하게 설명하십시오.

**예제 프롬프트 - 단순 조건부 논리:**

    패널이 &quot;Married@spouseInformation인 경우에만 패널@maritalStatus 표시하는 규칙을 만듭니다.

**예제 프롬프트 - 복잡한 비즈니스 규칙:**

    종합 대출 신청 확인 구현:
    
    **수입 확인:**
    - @annualIncome이 30000 미만인 경우:
    - 경고 메시지 표시: &quot;수입이 요청된 대출 금액에 대해 불충분할 수 있음&quot;
    - 추가 수입 서류 필요
    - 메시지 표시: &quot;추가 서류가 필요할 수 있음&quot;
    - @annualIncome이 100000 초과인 경우:
    - 프리미엄 서비스 옵션 표시
    - 우선 순위 처리 확인란 사용
    
    **연령 기반 확인:**
    - @age이 18세 미만인 경우:
    - 상위/보호자 정보 섹션 표시
    - 상위 서명 업로드를 필수로 설정
    - &quot;검토용 제출&quot;에 단추 텍스트 변경
    - @age이 65인 경우 이전:
    - 고급 할인 옵션 표시
    - 접근성 환경 설정 추가

**규칙 관련 프롬프트:**

    패널@spouseInformation @maritalStatus &quot;Married **&#x200B; 또는 &quot;Domestic Partnership&quot;인 경우에만 표시하는 &#x200B;** 가시성 규칙 을 만듭니다
    
    **점진적 공개**&#x200B;를 추가합니다. 이때 이전 답변을 기반으로 추가 질문이 표시됩니다. 기본 정보로 시작한 다음 관련 후속 작업을 표시합니다
    
    **스마트 기본값**&#x200B;을 구현합니다. 여기서 선택 항목@country 관련 필드를 자동 설정합니다. 수동 재정의 허용

## 데이터 통합 및 제출

**사용 시기:** 백엔드 시스템, 데이터베이스 또는 외부 서비스에 양식을 연결해야 하는 경우.

**사용 방법:** 기본 제출 설정부터 시작한 다음 점진적으로 추가 통합을 추가합니다. 통합 유형, 데이터 형식 요구 사항 및 오류 처리 환경 설정을 지정합니다.

**예제 프롬프트 - 기본 제출로 시작:**

    @applicationForm 기본 양식 제출 구성:
    
    **기본 제출:**
    - 양식 데이터를 REST 엔드포인트로 보내기: &#39;/api/v1/applications&#39;
    - 데이터를 JSON으로 포맷
    - 성공 메시지 표시: &quot;응용 프로그램이 성공적으로 제출되었습니다&quot;
    - 제출이 실패하면 오류 메시지 표시: &quot;제출 실패, 다시 시도하십시오.&quot;

**점진적인 보조 작업 추가 예제:**

    @applicationForm에 전자 메일 알림 추가: 응용 프로그램 참조 번호가 있는 @email 주소로 확인 전자 메일을 보냅니다
    
    @applicationForm에 CRM 통합 추가: @firstName, @lastName, @email으로 새 잠재 고객 레코드를 만들고 상태를 &quot;새 응용 프로그램&quot;으로 설정합니다

**예제 프롬프트 - 표준 다중 채널 제출:**

    여러 데이터 대상을 사용하여 양식 제출을 구성합니다.
    
    **기본 제출:**
    - REST 끝점으로 양식 데이터 보내기: &#39;/api/v1/applications&#39;
    - API 키를 사용하여 인증 헤더 포함
    - 주소 및 고용에 대한 중첩된 개체가 있는 JSON으로 데이터 서식 지정
    - 감사 메시지를 표시하여 성공 응답 처리
    
    **보조 작업:**
    - @email 주소의 지원자에게 알림 이메일 보내기
    - 추적 시스템에 응용 프로그램 데이터 복사
    - 승인 프로세스에 대한 워크플로 트리거
    - CRM에서 리드 상태가 &quot;새 응용 프로그램&quot;
    
    **오류 처리:**
    - 기본 제출이 실패하면 로컬에서 데이터를 저장하고 다시 시도
     사용자에게 친숙한 오류 메시지 표시: &quot;제출을 일시적으로 사용할 수 없음&quot;
    - 양식 데이터를 백업으로 다운로드하는 옵션을 제공합니다
    - 실패한 제출에 대한 경고 이메일을 관리 팀에 보냅니다
    
    **성공 흐름:**
    - 응용 프로그램 참조 번호가 있는 확인 페이지로 리디렉션
    - 다음 단계로 확인 이메일 보내기
    - 예상 처리 타임라인 표시

**통합 관련 프롬프트:**

    새 리드를 만들려면 이 양식을 **CRM 시스템**&#x200B;에 연결하십시오. 양식@firstName 제출되면 FirstName에 매핑하고, Email에 @email, LeadSource를 &quot;Web Form&quot;으로 설정하고, Status를 &quot;New&quot;
    
    **워크플로 트리거**&#x200B;로 설정합니다. 관리자 알림을 사용하여 모든 양식 데이터를 전달하고 승인 워크플로우를 트리거합니다
    
    **데이터베이스 통합**&#x200B;을 구성하여 양식 제출을 레코드로 저장합니다. 업로드된 문서가 있는 각 제출에 대해 새 폴더를 만듭니다

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

*이 프롬프트 라이브러리는 사용자 피드백 및 새로운 Forms Experience Builder 기능에 따라 계속 업데이트됩니다. 최신 기능과 예제를 보려면 [AEM Forms 설명서](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/home.html?lang=ko)를 확인하십시오.*
