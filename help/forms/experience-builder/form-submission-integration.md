---
title: 양식 제출 및 통합
description: 양식 제출을 구성하고 Forms Experience Builder 양식을 외부 시스템, API 및 비즈니스 워크플로우와 통합하는 방법을 알아봅니다.
feature: Edge Delivery Services
hide: true
index: false
hidefromtoc: true
role: Admin, Developer
exl-id: c772556b-dab6-4fa8-b728-1fe52c6596a4
source-git-commit: 1d378e6c8ac714779e77314d3457a14d40cd222f
workflow-type: tm+mt
source-wordcount: '890'
ht-degree: 0%

---

# 양식 제출 및 통합

>[!NOTE]
>
> Forms Experience Builder는 조기 액세스 프로그램에서 사용할 수 있습니다. 시작하기 전에 액세스 권한을 요청 및 부여했는지 확인하십시오.

Forms Experience Builder는 양식을 외부 시스템, API 및 비즈니스 워크플로우와 연결할 수 있는 강력한 통합 기능을 제공합니다. 이 안내서에서는 양식 제출을 구성하고 다양한 통합 시나리오를 설정하는 방법을 다룹니다.

## 제출 구성 옵션

### 이메일 제출

이메일을 통해 제출을 보내도록 양식 구성:

**기본 전자 메일 설정:**

- 수신자 이메일 주소 설정
- 이메일 템플릿 구성
- 참조 및 숨은 참조 수신자 추가
- 이메일 알림 설정

**고급 전자 메일 기능:**

- 동적 수신자 선택
- 양식 데이터를 사용한 이메일 템플릿
- 첨부 파일 처리
- 이메일 게재 확인

### REST API 통합

외부 API 및 서비스에 양식 연결:

**API 끝점 구성:**

- REST API URL 설정
- 인증 방법 구성
- 요청 헤더 및 매개 변수 설정
- 응답 데이터 처리

**데이터 매핑:**

- 양식 필드를 API 매개 변수에 매핑
- 데이터 형식 변환
- 중첩 JSON 구조 처리
- 오류 응답 관리

### 클라우드 스토리지 통합

클라우드 스토리지 서비스에 양식 제출을 저장합니다.

**지원되는 플랫폼:**

- Microsoft Azure Blob 저장소
- Amazon
- Google 클라우드 스토리지
- SharePoint Online

**구성 옵션:**

- 저장소 자격 증명 설정
- 폴더 구조 구성
- 파일 이름 지정 규칙 설정
- 액세스 권한 관리

### 워크플로우 통합

양식을 비즈니스 프로세스 워크플로에 연결:

**Microsoft Power Automate:**

- 양식 제출 시 워크플로우 트리거
- 워크플로우 단계에 양식 데이터 전달
- 워크플로우 응답 처리
- 승인 프로세스 관리

**Adobe 워크플로:**

- AEM 워크플로우와 통합
- 승인 체인 설정
- 알림 단계 구성
- 문서 처리 관리

## 양식 제출 설정

### 1단계: 제출 구성에 액세스

1. Forms Experience Builder에서 양식 열기
2. 제출 설정으로 이동
3. &quot;양식 제출 구성&quot; 선택
4. 통합 유형 선택

### 2단계: 이메일 제출 구성

**기본 전자 메일 설정:**

    hr@company.com에 전자 메일 제출 구성:
    - 제목: &quot;새 직원 응용 프로그램&quot;
    - 전자 메일 본문에 양식 데이터 포함
    - 신청자에게 확인 보내기

**고급 전자 메일 구성:**

    동적 전자 메일 라우팅 설정:
    - 부서가 &quot;IT&quot;인 경우 it-hr@company.com
    - 부서가 &quot;Sales&quot;인 경우 sales-hr@company.com
    - 기본값을 hr@company.com
으로 보냅니다.

### 3단계: API 통합 설정

**REST API 구성:**

    REST 끝점에 양식 데이터 제출:
    - URL: https://api.company.com/forms/submit
    - 메서드: POST
    - 인증: 전달자 토큰
    - 콘텐츠 유형: application/json

**데이터 매핑 예:**

    양식 필드를 API에 매핑:
    - firstName -> user.first_name
    - lastName -> user.last_name
    - 전자 메일 -> user.email_address
    - 부서 -> user.department_id

### 4단계: 클라우드 스토리지 구성

**Azure Blob 저장소 설정:**

    Azure에 양식 제출 저장:
    - 컨테이너: 양식 제출
    - 폴더: /{year}/{month}/{day}/
    - 파일 형식: 첨부 파일이 있는 JSON
    - 액세스 수준: 비공개

## 통합 예

### 고객 피드백 양식

**제출 구성:**

- 지원 팀에 대한 이메일 알림
- API를 통해 CRM 시스템에 데이터 저장
- 자동으로 지원 티켓 만들기
- 고객에게 확인 이메일 보내기

**구현:**
고객 피드백 양식 제출 대상:
1. 양식 세부 정보가 포함된 이메일 <support@company.com>
2. CRM API에 게시하여 고객 레코드 만들기
3. 지원 티켓 만들기 워크플로우 트리거
4. 고객에게 감사 이메일 보내기

### 직원 온보딩 양식

**제출 구성:**

- 신규 고용 정보를 이메일로 HR 팀에 전송
- SharePoint에 문서 저장
- 온보딩 워크플로우 트리거
- 다양한 시스템에서 사용자 계정 만들기

**구현:**
직원 온보딩 처리:
1. 직원 세부 정보가 포함된 이메일(<hr@company.com>)
2. SharePoint 직원 폴더에 문서 업로드
3. Power Automate에서 온보딩 워크플로 시작
4. HR 시스템, 이메일 및 기타 도구에서 계정 생성

### 리드 생성 양식

**제출 구성:**

- 마케팅 자동화 플랫폼에 리드 데이터 저장
- 영업 팀에 알림 보내기
- CRM 시스템에 리드 추가
- 후속 이메일 시퀀스 트리거

**구현:**
프로세스 리드 생성:
1. Marketo API로 리드 데이터 게시
2. Salesforce에서 리드 레코드 만들기
3. 잠재 고객 세부 정보가 포함된 이메일 영업팀
4. 자동화된 이메일 육성 시퀀스 시작

## 고급 통합 시나리오

### 여러 단계 양식 처리

**복잡한 워크플로우 통합:**

- 외부 시스템에 대한 양식 데이터 유효성 검사
- 결제 게이트웨이를 통해 결제 처리
- 문서 및 계약서 생성
- 여러 관련자에게 알림 보내기

### 실시간 데이터 유효성 검사

**API 기반 유효성 검사:**

- 회사 디렉터리에 대한 이메일 주소 유효성 검사
- 재고 시스템에서 제품 가용성 확인
- CRM에서 고객 정보 확인
- 결제 정보 확인

### 조건부 제출 라우팅

**양식 데이터를 기반으로 한 동적 라우팅:**

- 조회 유형에 따라 다른 부서로 이동
- 고객 계층을 기반으로 다른 시스템으로 전송
- 양식 완료 상태에 따라 다르게 처리
- 지역별 다양한 비즈니스 규칙 처리

## 보안 및 규정 준수

### 데이터 보호

**암호화 및 보안:**

- 전송 중인 중요 데이터 암호화
- 보안 API 자격 증명 및 토큰
- 적절한 액세스 제어 구현
- 데이터 보존 정책 준수

### 규정 준수 요구 사항

**GDPR 및 개인 정보:**

- 동의 관리 구현
- 데이터 내보내기 기능 제공
- 데이터 삭제 요청 활성화
- 감사 추적 유지

**업계 표준:**

- 의료 양식에 대한 HIPAA 규정 준수
- 결제 처리를 위한 PCI DSS
- 금융 양식에 대한 SOX 규정 준수
- 업종별 규정

## 테스트 및 유효성 검사

### 제출 테스트

**테스트 시나리오:**

- 이메일 게재 및 형식 확인
- API 연결 및 데이터 매핑 테스트
- 클라우드 스토리지 업로드 확인
- 워크플로우 트리거 기능 확인

**오류 처리:**

- 네트워크 실패 시나리오 테스트
- 오류 메시지 표시 유효성 확인
- 다시 시도 메커니즘 확인
- 대체 옵션 확인

### 성능 최적화

**최적화 전략:**

- 비동기 처리 구현
- 대량 데이터에 일괄 처리 작업 사용
- API 호출 빈도 최적화
- 자주 액세스하는 데이터 캐시

## 통합 문제 해결

### 일반적인 문제

**전자 메일 배달 문제:**

- SMTP 서버 구성 확인
- 수신자 이메일 주소 확인
- 스팸 필터 설정 검토
- 이메일 템플릿 형식 테스트

**API 통합 문제:**

- API 끝점 URL 확인
- 인증 자격 증명 확인
- 요청 형식 및 헤더 유효성 검사
- API 응답 처리 검토

**저장소 통합 문제:**

- 스토리지 자격 증명 확인
- 폴더 권한 확인
- 파일 업로드 제한 확인
- 네트워크 연결 테스트

### 도움말 보기

통합 문제의 경우:

- [Forms Experience Builder FAQ](forms-experience-builder-frequently-asked-questions.md) 확인
- [시작 가이드](forms-experience-builder-getting-started.md)를 검토하세요.
- 기술 지원이 필요한 경우 시스템 관리자에게 문의하십시오
- 외부 서비스에 대한 API 설명서 참조

<!-- 
## Related articles

- [Forms Experience Builder Overview](product-overview.md)
- [Getting started with Forms Experience Builder](forms-experience-builder-getting-started.md)
- [Deploy and configure Forms Experience Builder](deploy-forms-experience-builder.md)
- [Intelligent import and conversion](intelligent-import-conversion.md)
- [Frequently asked questions](forms-experience-builder-frequently-asked-questions.md)

-->


