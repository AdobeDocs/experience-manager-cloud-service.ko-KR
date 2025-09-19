---
title: Forms Experience Builder - 자주 묻는 질문
description: 설정, 사용, 문제 해결 및 모범 사례를 포함하여 Forms Experience Builder에 대한 일반적인 질문에 대한 답변을 찾을 수 있습니다.
feature: Edge Delivery Services
hide: true
index: false
hidefromtoc: true
role: Admin, Architect, Developer
source-git-commit: de524aeddd5f53cbd713ff0523222966752ebbc0
workflow-type: tm+mt
source-wordcount: '1060'
ht-degree: 1%

---


# Forms Experience Builder - 자주 묻는 질문

>[!NOTE]
>
> Forms Experience Builder는 조기 액세스 프로그램에서 사용할 수 있습니다. 시작하기 전에 액세스 권한을 요청 및 부여했는지 확인하십시오.

이 FAQ는 기본 설정에서 고급 기능 및 문제 해결에 이르기까지 Forms Experience Builder에 대한 가장 일반적인 질문을 해결합니다.

## 일반 질문

### Forms Experience Builder란?

Forms Experience Builder는 대화형 언어를 사용하여 정교한 디지털 양식을 작성할 수 있는 AI 기반의 양식 생성 도구입니다. 기존의 드래그 앤 드롭 인터페이스나 복잡한 코딩 대신 원하는 내용을 간단히 설명하면 AI가 양식을 만들어 준다.

### Forms Experience Builder는 누가 사용할 수 있습니까?

Forms Experience Builder는 다음 사용자를 위해 설계되었습니다.

- 양식을 빠르고 효율적으로 작성하려는 **양식 작성자**
- 기술 전문 지식 없이도 양식을 만들어야 하는 **비즈니스 사용자**
- 신속한 양식 프로토타이핑을 위해 AI를 활용하려는 **개발자**
- 양식 만들기 워크플로를 구성하고 관리해야 하는 **관리자**

### 모든 AEM Forms 고객이 Forms Experience Builder를 사용할 수 있습니까?

Forms Experience Builder는 현재 조기 액세스 프로그램을 통해 사용할 수 있습니다. 액세스를 요청하고 조직의 가용성에 대해 알아보려면 Adobe 담당자에게 문의하십시오.

## 설정 및 구성

### Forms Experience Builder를 사용하기 위한 사전 요구 사항은 무엇입니까?

Forms Experience Builder를 사용하기 전에 다음을 확인하십시오.

- 조기 액세스 프로그램을 통해 Forms Experience Builder에 액세스
- 적응형 Forms 핵심 구성 요소가 포함된 AEM Forms as a Cloud Service
- 양식 개념 및 비즈니스 요구 사항에 대한 기본 이해

자세한 기술 설정 요구 사항은 [Forms Experience Builder 배포 및 구성](deploy-forms-experience-builder.md)을 참조하십시오.

### 내 환경에서 Forms Experience Builder를 활성화하려면 어떻게 합니까?

Forms Experience Builder 설정은 AEM Forms 구현에 따라 다릅니다.

**Edge Delivery Services의 경우:**

- Edge Delivery Services Forms에 대한 프로젝트 준비
- 범용 편집기에서 Forms Experience Builder 활성화

**핵심 구성 요소 기반 양식의 경우:**

- 적응형 Forms 핵심 구성 요소가 활성화되었는지 확인
- 적응형 Forms 편집기에서 Forms Experience Builder 구성

### 기존 양식과 함께 Forms Experience Builder를 사용할 수 있습니까?

예. Forms Experience Builder는 여러 가지 방법으로 기존 양식으로 작업할 수 있습니다.

- 기존 PDF forms 가져오기 및 전환
- AI 기반 기능으로 기존 적응형 양식 개선
- 현재 양식 구조에 지능형 필드 추가

## 양식 만들기

### 첫 번째 양식을 만들려면 어떻게 해야 합니까?

원하는 내용에 대한 간단한 설명으로 시작합니다.

    이름, 전자 메일 및 메시지 필드가 있는 연락처 양식을 만듭니다

AI가 기본 양식 구조를 생성하여 추가 기능, 유효성 검사 및 스타일링으로 향상시킬 수 있습니다.

### 어떤 유형의 양식을 만들 수 있습니까?

Forms Experience Builder는 다양한 양식 유형을 지원합니다.

- 연락처 및 피드백 양식
- 등록 및 온보딩 양식
- 설문 조사 및 평가 양식
- 조건부 논리를 사용하는 여러 단계 양식
- 파일 업로드 및 복잡한 유효성 검사 기능이 있는 Forms

### 여러 단계 양식을 만들 수 있습니까?

예. 자연어를 사용하여 여러 단계 양식을 만들 수 있습니다.

    개인 정보, 환경 설정, 확인 등 3단계로 점진적 양식 만들기

AI가 단계 간 탐색을 통해 양식 구조를 자동으로 설정합니다.

### 양식 필드에 유효성 검사를 추가하려면 어떻게 합니까?

자연어 명령을 사용하여 유효성 검사 추가:

    전자 메일 형식 유효성 검사를 사용하여 필수 필드를 @email
    미국 전화 번호 형식 유효성 검사를 @phoneNumber에 추가
    연령 유효성 검사 설정: @dateOfBirth
의 경우 18 이상이어야 합니다.

## 고급 기능

### LLM 강화 스마트 필드란 무엇입니까?

LLM 강화 스마트 필드는 AI 기술 자료의 관련 옵션이 미리 채워져 있는 지능형 양식 필드입니다. 예:

- 모든 세계 국가와 함께 국가 드롭다운
- 표준 코드를 사용한 업계 분류
- 주, 도시 및 우편 번호가 포함된 지역 데이터

### 기존 문서를 양식으로 가져오려면 어떻게 해야 합니까?

다양한 문서 유형을 가져올 수 있습니다.

- **PDF forms**: 정적 또는 대화형 PDF 업로드
- **이미지**: 종이 양식 또는 스크린샷 사진 업로드
- **디자인 파일**: Figure 디자인 또는 기타 디자인 형식 가져오기

Forms Experience Builder의 첨부 파일 아이콘을 사용하여 문서를 업로드하고 전환 요구 사항을 설명합니다.

### 양식을 외부 시스템과 통합할 수 있습니까?

예. Forms Experience Builder는 다양한 통합 옵션을 지원합니다.

- 사용자 정의 템플릿을 사용한 이메일 제출
- 외부 서비스와 REST API 통합
- 클라우드 스토리지 통합(Azure, AWS, Google Cloud)
- 워크플로우 통합(Power Automate, AEM 워크플로우)

## 문제 해결

### AI가 내 요청을 이해하지 못합니다. 어떻게 해야 합니까?

다음 접근 방식을 시도해 보십시오.

- 설명에 보다 구체적임
- 복잡한 요청을 더 작은 단계로 나누기
- 타겟팅된 변경 사항에 @fieldName 필드 참조(AEM) 사용
- 원하는 내용에 대한 명확한 예 제공

### 양식 유효성 검사가 작동하지 않습니다. 어떻게 고치죠?

다음과 같은 일반적인 문제를 확인합니다.

- 필드 이름이 정확하게 일치하는지 확인(대/소문자 구분)
- 유효성 검사 구문이 올바른지 확인합니다.
- 개별적으로 유효성 검사 규칙 테스트
- 특정 문제에 대한 오류 메시지 검토

### 조건부 논리가 제대로 트리거되지 않습니다. 왜 그래?

다음 방법으로 조건부 논리 문제 해결:

- 필드 이름이 올바르게 참조되는지 확인
- 규칙 구문 및 조건 확인
- 다양한 입력 조합으로 테스트
- 필드 유형이 규칙 요구 사항과 일치하는지 확인하는 중

### 인터페이스가 로드되지 않습니다. 어떻게 해야 합니까?

다음 솔루션을 사용해 보십시오.

- 브라우저를 새로 고치고 캐시를 지우십시오.
- 인터넷 연결 확인
- 적절한 액세스 권한이 있는지 확인
- 문제가 지속되면 시스템 관리자에게 문의하십시오

## 모범 사례

### Forms Experience Builder로 더 나은 양식을 만들려면 어떻게 해야 합니까?

다음 모범 사례를 따르십시오.

- **구체적으로**: 원하는 내용에 대한 자세한 설명을 제공합니다.
- **단순 시작**: 기본 구조로 시작하고 복잡성을 점차적으로 추가합니다.
- **철저하게 테스트**: 배포하기 전에 모든 양식 기능을 확인합니다.
- **증분 개발 사용**: 단계별 양식 작성

### 양식을 만들 때 피해야 하는 것은 무엇입니까?

다음과 같은 일반적인 실수를 방지하십시오.

- 당신의 설명에 너무 모호한
- 모든 항목을 한 번에 만들려고 함
- 테스트 및 유효성 검사 건너뛰기
- 모바일 응답성을 고려하지 않음

### 양식에 액세스할 수 있도록 하려면 어떻게 해야 합니까?

Forms Experience Builder에는 다음과 같은 접근성 기능이 포함되어 있습니다.

- 자동 WCAG 준수 검사
- 화면 판독기 호환성
- 키보드 탐색 지원
- 고대비 모드 옵션

## 통합 및 배포

### Forms Experience Builder로 만든 양식을 배포하려면 어떻게 합니까?

Forms Experience Builder로 만든 Forms은 표준 AEM Forms 배포 프로세스를 따릅니다.

- AEM 작성 환경을 통해 양식 게시
- 양식 제출 엔드포인트 구성
- 양식 처리 워크플로우 설정
- 프로덕션 환경의 테스트 양식

### AI 응답 및 동작을 사용자 지정할 수 있습니까?

예. 다양한 측면을 구성할 수 있습니다.

- 응답 스타일(간결, 세부, 균형 조정)
- 언어 환경 설정 및 용어
- 인터페이스 사용자 지정 옵션
- 접근성 설정

### Forms Experience Builder에 대한 도움말을 보려면 어떻게 합니까?

추가 지원의 경우:

- [시작 가이드](forms-experience-builder-getting-started.md)를 확인하세요.
- [배포 및 구성 가이드](deploy-forms-experience-builder.md)를 검토하십시오.
- 시스템 관리자에게 문의하십시오
- 기술 문제에 대해서는 Adobe 지원 센터에 문의하십시오

## 관련 문서

- [Forms Experience Builder 개요](product-overview.md)
- [Forms Experience Builder 시작하기](forms-experience-builder-getting-started.md)
- [Forms Experience Builder 배포 및 구성](deploy-forms-experience-builder.md)
- [LLM 향상 스마트 필드](forms-experience-builder-llm-smart-fields.md)
- [지능적인 가져오기 및 전환](intelligent-import-conversion.md)
- [양식 제출 및 통합](form-submission-integration.md)
