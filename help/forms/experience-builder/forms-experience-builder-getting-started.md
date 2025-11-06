---
title: Forms Experience Builder 시작하기
description: Forms Experience Builder를 사용하여 첫 번째 AI 기반 양식을 만드는 기본 사항에 대해 알아봅니다. 예제 및 모범 사례를 포함한 단계별 튜토리얼입니다.
hide: true
index: false
hidefromtoc: true
role: Admin, Developer
exl-id: c4f838bc-a001-48e7-afaa-c2ff9034f5d4
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '1133'
ht-degree: 9%

---

# Forms Experience Builder 시작하기 {#getting-started-forms-experience-builder}

Forms Experience Builder는 AI를 활용하여 자연어 설명을 완전히 기능하는 디지털 양식으로 전환함으로써 양식 생성을 혁신합니다. 이 안내서를 통해 첫 번째 양식을 만들고 Forms Experience Builder를 강력한 것으로 만드는 핵심 개념을 이해할 수 있습니다.

## Forms Experience Builder란? {#what-is-forms-experience-builder}

Forms Experience Builder는 대화형 언어를 사용하여 정교한 디지털 양식을 작성할 수 있는 AI 기반의 양식 생성 도구입니다. 기존의 드래그 앤 드롭 인터페이스나 복잡한 코딩 대신 원하는 내용을 간단히 설명하면 AI가 양식을 만들어 준다.

**주요 기능:**

* **자연어 양식 만들기** - 일반 영어로 양식 요구 사항 설명

* **지능적인 가져오기 및 변환** - 기존 문서를 대화형 양식으로 변환

* **스마트 필드 생성** - 미리 채워진 옵션이 있는 AI 기반 필드

* **비즈니스 논리 자동화** - 대화를 통해 조건부 규칙 만들기 및 유효성 검사

* **시스템 통합** - 양식을 기존 비즈니스 워크플로에 연결

## 사전 요구 사항 {#prerequisites-getting-started}

시작하기 전에 다음을 확인하십시오.

* **Forms Experience Builder 액세스** - 조기 액세스 프로그램을 통해 사용할 수 있습니다.
* **AEM Forms as a Cloud Service** - 적응형 Forms 핵심 구성 요소가 있는 프로덕션 작성 환경
* **기본 이해** - 양식 개념 및 비즈니스 요구 사항에 익숙함

자세한 기술 설정 요구 사항 및 환경 구성은 [Forms Experience Builder 배포 및 구성](deploy-forms-experience-builder.md)을 참조하십시오.

## 양식을 만드는 방법 {#two-ways-to-create-forms}

Forms 마법사를 사용하여 [핵심 구성 요소 템플릿](/help/forms/creating-adaptive-form-core-components.md) 또는 [Edge Delivery Services](/help/edge/docs/forms/universal-editor/create-forms.md) 템플릿, 테마 및 기타 옵션을 선택하면 Forms Experience Builder에서 두 가지 기본 양식 만들기 방법을 제공합니다.

### &#x200B;1. 처음부터 제작 {#create-from-scratch}

요구 사항에 대한 자연어 설명을 사용하여 양식을 작성합니다.

**사용 시기:**

* 요구 사항에서 새 양식 작성

* 새 비즈니스 프로세스를 위한 양식 만들기

* 명확한 사양은 있지만 기존 문서가 없는 경우

**예:**

    다음을 사용하여 고객 피드백 양식 만들기:
    &#x200B;- 상품평 (별점 1~5점)
    &#x200B;- 자세한 피드백을 위한 댓글 필드
    &#x200B;- 고객 이메일 (선택 사항)
    &#x200B;- 이메일 알림으로 제출

>[!VIDEO](https://video.tv.adobe.com/v/3473104)



### &#x200B;2. 가져오기 및 전환 {#import-and-convert}

기존 문서를 대화형 디지털 양식으로 변환합니다.

이 옵션을 사용하기 전에 PDF 파일 또는 양식 이미지를 업로드하십시오. PDF은 AcroForm 또는 XFA 기반 PDF 양식일 수 있습니다. [다른 유형의 PDF forms](https://experienceleague.adobe.com/ko/docs/experience-manager-learn/forms/document-services/pdf-forms-and-documents)의 경우 Adobe Acrobat의 [양식 준비](https://helpx.adobe.com/in/acrobat/using/creating-distributing-pdf-forms.html) 옵션을 사용하여 AcroForm으로 변환합니다

**사용 시기:**

* 기존 PDF forms 전환

* 종이 문서 기반 프로세스 현대화

* 기존 양식 디자인을 개선해야 하는 경우

**예:**

    /create-form 첨부된 PDF 파일을 적응형 양식으로 변환

>[!VIDEO](https://video.tv.adobe.com/v/3474042)


## 첫 번째 양식: 단계별 자습서 {#first-form-tutorial}

기본 워크플로를 이해할 수 있는 간단한 연락처 양식을 만들어 보겠습니다.

### 1단계: 간단한 설명으로 시작 {#step-1-simple-description}

기본 양식 설명으로 시작합니다.

    이름, 이메일, 메시지 필드가 있는 기본 연락처 양식 만들기

이렇게 하면 세 가지 필수 필드가 있는 폼이 만들어집니다.

필수 필드가 세 개인 ![폼 - 자연어 프롬프트를 사용하여 만들어짐](/help/forms/assets/forms-experience-builder-contact-us-form.png)

### 2단계: 유효성 검사 및 요구 사항 추가 {#step-2-add-validation}

유효성 검사 규칙으로 양식 개선:

    적절한 유효성 검사를 통해 @name 및 @email을 필수 필드로 만들기

`@` 기호가 타깃팅된 수정 사항에 대한 특정 필드를 참조합니다.

![자연어 프롬프트를 사용하여 양식 경험 빌더에서 유효성 검사를 추가했습니다.](/help/forms/assets/forms-experience-builder-contact-us-form-add-validation.png)


### 3단계: 사용자 경험 개선 {#step-3-improve-ux}

유용한 자리 표시자 텍스트 및 지침 추가:

    플레이스홀더 텍스트 추가: @name “이름”, @email “your.email@company.com”, @message “어떻게 도와드릴 수 있는지 알려 주세요”

![Forms Experience Builder에서 자연어 프롬프트를 사용하여 유효성 검사 추가](/help/forms/assets/forms-experience-builder-contact-us-form-add-placeholder.png)

### 4단계: 고급 기능 추가 {#step-4-advanced-features}

추가 기능 포함:

    두 개의 드롭다운을 추가
    
    &#x200B;- 옵션이 있는 inquiryType: &quot;일반 질문&quot;, &quot;지원 요청&quot;, &quot;판매 문의&quot;, &quot;파트너 관계&quot;
    
    &#x200B;- 옵션이 있는 긴급도 수준(낮음, Medium, 높음)


![Forms Experience Builder에서 자연어 프롬프트를 사용하여 드롭다운 구성 요소를 추가했습니다.](/help/forms/assets/forms-experience-builder-contact-us-form-add-dropdown.png)


### 5단계: 조건부 논리 구현 {#step-5-conditional-logic}

다음과 같은 규칙을 추가하여 스마트 컨텍스트 인식 동작을 만듭니다.

    양식 로드 시 @urgencyLevel 드롭다운 숨기기
    @urgencyLevel 드롭다운 표시(낮음, Medium, 높음)@inquiryType &quot;지원 요청&quot;과 같은 경우에만

양식이 로드될 때 긴급도 수준 드롭다운을 숨기고 다른 규칙은 조회 유형이 &quot;지원 요청&quot;인 경우에만 표시하는 두 개의 별도 규칙입니다. 별도의 프롬프트를 사용하여 각 규칙을 만들어야 합니다. 한 번에 하나의 규칙만 만들 수 있습니다.

## AI 대화 방식 이해 {#ai-conversation-approach}

Forms Experience Builder는 다음과 같은 작업을 수행할 수 있는 대화형 인터페이스를 사용합니다.

### @ 기호가 있는 참조 필드 {#reference-fields}

특정 필드를 참조하려면 `@fieldName`을(를) 사용합니다.

    필수 필드 @email
    미국 형식에 대한 @phoneNumber에 유효성 검사 추가
    @submitButton 텍스트를 &quot;메시지 보내기&quot;로 변경

>[!VIDEO](https://video.tv.adobe.com/v/3474043)


### 자연어 명령 사용 {#natural-language-commands}

원하는 내용을 쉬운 영어로 설명:

    &#x200B;- 회사 정보에 대한 섹션 추가
    &#x200B;- 부서 선택에 대한 드롭다운 만들기
    &#x200B;- 다시 시작에 대한 파일 업로드 포함
    &#x200B;- 양식 제출 시 이메일 알림 설정

### 점진적 구축 {#build-incrementally}

단순하게 시작하고 복잡성을 점진적으로 추가합니다.

1. **기본 구조** - 필수 필드를 먼저 만듭니다.
2. **유효성 검사 추가** - 필수 필드 및 형식 유효성 검사 구현
3. **UX 향상** - 자리 표시자, 도움말 텍스트 및 스타일 추가
4. **논리 구현** - 조건부 규칙 및 비즈니스 논리 추가
5. **제출 구성** - 양식 처리 및 알림 설정


## 일반적인 양식 패턴 {#common-form-patterns}

### 연락처 및 피드백 양식 {#contact-feedback-forms}

**기본 연락처 양식:**

    다음 주소로 연락처 양식 만들기:
    &#x200B;- 이름(필수)
    &#x200B;- 전자 메일(필수, 유효성 검사)
    &#x200B;- 제목 드롭다운(일반, 지원, 판매, 파트너 관계)
    &#x200B;- 메시지(필수, 여러 줄)
    &#x200B;- 제출 단추

**고객 피드백 양식:**

    다음을 사용하여 고객 피드백 양식 만들기:
    &#x200B;- 상품평 (별점 1~5점)
    &#x200B;- 자세한 피드백을 위한 댓글 필드
    &#x200B;- 고객 이메일 (선택 사항)
    &#x200B;- 이메일 알림으로 제출

### 등록 및 온보딩 양식 {#registration-onboarding-forms}

**사용자 등록:**

    개인 정보(이름, 전자 메일, 전화)를 사용하여 사용자 등록 양식을 만듭니다.
    
    &#x200B;- 계정 환경 설정(뉴스레터, 알림)
    &#x200B;- 약관 수락
    &#x200B;- 보안 강화를 통해 암호 만들기

**직원 온보딩:**

    다음을 사용하여 직원 온보딩 양식 만들기:
    &#x200B;- 개인 세부 정보 및 연락처 정보
    &#x200B;- 취업 정보 및 시작 날짜
    &#x200B;- 문서 업로드(다시 시작, ID, 세금 양식)
    &#x200B;- 혜택 선택 및 환경 설정

### 설문 조사 및 평가 양식 {#survey-assessment-forms}

**고객 만족도 조사:**

    다음 내용으로 고객 만족도 설문 조사 만들기:
    &#x200B;- 전체 등급(1~10단계)
    &#x200B;- 카테고리 등급(제품, 서비스, 지원)
    &#x200B;- 개방형 피드백 섹션
    &#x200B;- 인구 통계 정보(선택 사항)

**기술 평가:**

    
    &#x200B;- 숙련도 수준이 있는 기술 범주
    &#x200B;- 각 기술에 대한 경험 기간
    &#x200B;- 인증 및 교육 정보
    &#x200B;- 자체 평가 및 목표
(으)로 기술 평가 양식을 만듭니다.

## 테스트 및 유효성 검사 {#testing-validation}

### 항상 양식 테스트 {#always-test-forms}

양식을 배포하기 전에:

1. **모든 필드 테스트** - 유효성 검사가 올바르게 작동하는지 확인

2. **조건부 논리 확인** - 규칙이 올바르게 트리거되는지 확인

3. **제출 테스트** - 데이터가 올바르게 처리되었는지 확인

4. **다른 장치에서 유효성 검사** - 모바일 호환성 확인

5. **이해 당사자와 검토** - 최종 사용자로부터 피드백 받기

### 일반적인 유효성 검사 패턴 {#validation-patterns}

**전자 메일 유효성 검사:**

    @email 필드에 전자 메일 형식 유효성 검사 추가

**전화 번호 유효성 검사:**

    @phoneNumber
에 미국 전화 번호 형식 유효성 검사 추가
**연령 유효성 검사:**

    나이 유효성 검사 추가: @dateOfBirth
의 경우 18세 이상이어야 합니다.
**파일 업로드 유효성 검사:**

    파일 형식 유효성 검사 추가: PDF, DOC, DOCX만 @resume
    파일 크기 제한 추가: @resume 최대 5MB

## 다음 단계 {#next-steps}

기본 사항을 이해했으므로 다음 고급 항목을 살펴보십시오.

* **[LLM 강화 스마트 필드](forms-experience-builder-llm-smart-fields.md)** - AI 지식을 사용하여 미리 채워진 옵션을 사용하여 필드를 만듭니다.
* **[AI 기반 양식 만들기](forms-experience-builder-prompt-examples-library.md)** - 고급 프롬프트 패턴 및 예제
* **[지능적인 가져오기 및 변환](intelligent-import-conversion.md)** - 기존 문서를 양식으로 변환
* **[양식 제출 및 통합](form-submission-integration.md)** - 양식을 비즈니스 시스템에 연결


## 관련 문서

* [Forms Experience Builder 개요](product-overview.md)
* [LLM 향상 스마트 필드](forms-experience-builder-llm-smart-fields.md)
* [AI 기반 양식 만들기](forms-experience-builder-prompt-examples-library.md)
* [지능적인 가져오기 및 전환](intelligent-import-conversion.md)
* [양식 제출 및 통합](form-submission-integration.md)
* [자주 묻는 질문](forms-experience-builder-frequently-asked-questions.md)
