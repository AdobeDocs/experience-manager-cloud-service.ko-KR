---
title: 범용 편집기에서 Google reCAPTCHA를 Forms에 추가
description: 스팸 및 자동화된 공격을 방지하기 위해 Google forms에서 Edge Delivery Services reCAPTCHA 보호 구현에 대한 안내서입니다
feature: Edge Delivery Services
keywords: 양식의 reCAPTCHA, 범용 편집기에서 reCAPTCHA 사용, 양식의 reCAPTCHA 추가, 양식 보안, 스팸 방지
role: Developer, Admin
level: Intermediate
exl-id: 1f28bd13-133f-487e-8b01-334be7c08a3f
source-git-commit: 2e2a0bdb7604168f0e3eb1672af4c2bc9b12d652
workflow-type: tm+mt
source-wordcount: '1290'
ht-degree: 4%

---


# 범용 편집기에서 Google reCAPTCHA를 Forms에 추가

Google reCAPTCHA는 인간 사용자와 자동화된 봇을 구별하여 양식을 보호하는 데 도움이 됩니다. 이 안내서에서는 범용 편집기에서 reCAPTCHA Enterprise 및 Standard 버전을 모두 구현하는 방법을 설명합니다.

**목표:**

- 적절한 reCAPTCHA 솔루션 선택
- reCAPTCHA Enterprise 또는 Standard 구성
- 양식에 reCAPTCHA 추가
- 구현의 유효성 검사 및 테스트
- 성능 모니터링 및 최적화

## 사전 요구 사항

시작하기 전에 다음을 확인하십시오.

### 액세스 요구 사항

- AEM as a Cloud Service 작성 액세스
- 양식 편집 권한을 사용한 유니버설 편집기 액세스
- reCAPTCHA 기능에 대한 조기 액세스 프로그램 등록

### 기술 요구 사항

- 활성 Google 계정
- 엔터프라이즈의 경우: 청구가 활성화된 Google Cloud Platform 프로젝트
- Standard의 경우: Google reCAPTCHA 계정
- 양식에 대한 도메인 소유권을 확인했습니다.

### 기술 자료 요구 사항

- AEM Forms 및 유니버설 편집기에 대한 기본 이해
- 클라우드 서비스 구성에 익숙함
- 양식 보안 개념 이해

## Forms에서 reCAPTCHA를 사용하는 이유는 무엇입니까?

| ![보안](/help/edge/docs/forms/universal-editor/assets/security.svg) | ![봇 보호](/help/edge/docs/forms/universal-editor/assets/bot-protection.svg) | ![사용자 경험](/help/edge/docs/forms/universal-editor/assets/user-experience.svg) |
|:-------------:|:-------------:|:-------------:|
| **향상된 보안** | **봇 및 스팸 방지** | **원활한 사용자 경험** |
| 부정 행위 및 공격으로부터 양식 보호 | 자동화된 봇이 양식을 제출하지 못하도록 방지 | 보이지 않는 reCAPTCHA는 합법적인 사용자를 방해하지 않습니다 |

**주요 개념:** reCAPTCHA는 기계 학습을 사용하여 사용자 행동을 분석하고 사람의 상호 작용 가능성을 나타내는 점수(0.0 ~ 1.0)를 할당합니다. 점수가 높을수록 사용자가 있음을 나타내고, 점수가 낮을수록 봇이 있음을 나타냅니다.

**예:** 중요한 데이터를 처리하는 세금 계산 양식에는 자동화된 공격으로부터 보호해야 합니다. reCAPTCHA는 제출이 봇이 아닌 실제 사용자로부터 이루어졌는지 확인합니다.

## 적절한 reCAPTCHA 솔루션 선택

Edge Delivery Services Forms은 두 개의 Google reCAPTCHA 옵션을 지원합니다. 다음 기준을 사용하여 적합한 솔루션을 선택합니다.

### 빠른 결정 안내서

**다음 항목이 있는 경우 reCAPTCHA Enterprise 사용:**

- 높은 트래픽 양식(월별 요청 10,000개 이상)
- 엄격한 규정 준수 요구 사항(GDPR, SOX, HIPAA)
- 고급 분석 및 보고 필요
- 프리미엄 보안 기능 예산
- 복잡한 다중 도메인 배포

**다음이 있는 경우 reCAPTCHA Standard 사용:**

- 낮은 트래픽에서 중간 트래픽(&lt;10,000개 요청/월)
- 기본 보안 요구 사항
- 제한된 예산(프리 티어)
- 간단한 단일 도메인 설정
- reCAPTCHA를 처음 사용함

### 세부 비교

| **기능** | **reCAPTCHA Enterprise** | **reCAPTCHA 표준** |
|-------------|--------------------------|------------------------|
| **비용** | 유료(사용량 기반 가격) | 무료 |
| **요청 제한** | 제한 없음 | 1개월 요청 1백만 개 |
| **고급 분석** | 상세 보고 | 기본 통계만 |
| **사용자 지정 규칙** | 계정별 규칙 | 전역 규칙만 |
| **다중 도메인 지원** | 고급 관리 | 기본 지원 |
| **SLA** | 99.9% 가동 시간 보장 | 최상의 노력 |
| **지원** | 엔터프라이즈 지원 | 커뮤니티 지원 |
| **준수** | 엔터프라이즈급 | 표준 규정 준수 |

**두 솔루션 모두 제공:**

- 점수 기반 감지(0.0~1.0 배율)
- 보이지 않는 작업(사용자 상호 작용 필요 없음)
- 머신 러닝 기반의 보트 탐지
- 실시간 위험 평가

## reCAPTCHA Enterprise 설정하기


+++ 1단계: Google 클라우드 환경 준비

**요구 사항:**

1. 청구가 활성화된 Google 클라우드 프로젝트
2. 프로젝트 ID(GCP 대시보드의)
3. 양식에 대한 도메인 인증
4. GCP 및 AEM에 대한 관리자 액세스

**설치:**

1. Google 클라우드 프로젝트 만들기 또는 선택
   - [Google 클라우드 콘솔로 이동](https://console.cloud.google.com/)
   - 새 프로젝트 만들기 또는 기존 프로젝트 선택
   - 프로젝트 ID 확인

2. reCAPTCHA Enterprise API 활성화
   - API 및 서비스 > 라이브러리로 이동합니다.
   - &quot;reCAPTCHA Enterprise API&quot; 검색
   - Enable 클릭

3. API 자격 증명 만들기
   - API 및 서비스 > 자격 증명으로 이동합니다.
   - Create Credentials > API Key 클릭
   - API 키 복사 및 저장

4. 사이트 키 만들기
   - 보안 > reCAPTCHA Enterprise로 이동합니다.
   - Create Key 클릭
   - 점수 기반 키 유형 선택
   - 도메인 추가
   - 임계값 점수 설정(권장: 0.5)

**유효성 검사 검사점:** 다음을 확인하십시오.

- 프로젝트 ID
- API 키
- 사이트 키
- Google Cloud에서 확인된 도메인

+++

+++ 2단계: AEM 클라우드 구성 컨테이너 구성

![단계별 클라우드 구성 설정](/help/edge/docs/forms/universal-editor/assets/recaptcha-general-configuration.png)
*그림: 양식 컨테이너에 대한 클라우드 구성 사용*

**설치:**

1. 구성 브라우저 액세스
   - AEM 작성자 인스턴스에 로그인
   - 도구 > 일반 > 구성 브라우저로 이동합니다.

2. 클라우드 구성 활성화
   - 양식의 구성 컨테이너 찾기
   - 속성 선택
   - 클라우드 구성 확인
   - 저장 후 닫기 클릭

3. 구성 확인
   - 컨테이너 속성에 &quot;클라우드 구성&quot;이 표시되는지 확인

**유효성 검사 검사점:**

- 컨테이너에 대해 클라우드 구성 활성화됨
- 구성 브라우저에 나타나는 컨테이너
- 속성에 &quot;클라우드 구성&quot;이 활성화됨으로 표시됩니다.

+++

+++ 3단계: AEM에서 reCAPTCHA Enterprise Service 구성

![reCAPTCHA Enterprise 구성 화면](/help/edge/docs/forms/universal-editor/assets/recaptcha-enterprise.png)
*그림: AEM의 reCAPTCHA 엔터프라이즈 구성 인터페이스*

**구성:**

1. reCAPTCHA 구성 액세스
   - 도구 > 클라우드 서비스 > reCAPTCHA로 이동합니다.
   - 양식의 구성 컨테이너 선택
   - 만들기 를 클릭합니다

2. Enterprise 설정 구성
   - 제목: 설명하는 이름(예: &quot;Production reCAPTCHA&quot;)
   - 이름: 시스템 이름(자동 생성 또는 사용자 지정)
   - 버전: ReCAPTCHA Enterprise 선택
   - 프로젝트 ID: Google Cloud 프로젝트 ID 입력
   - 사이트 키: Google Cloud에서 사이트 키 입력
   - API 키: Google Cloud API 키 입력
   - 키 유형: 점수 기반 사이트 키 선택

3. 보안 임계값 설정
   - 임계값 점수: 0.0과 1.0 사이에 설정
   - 권장 값:
      - 0.7-0.9: 높은 보안(일부 합법적인 사용자를 차단할 수 있음)
      - 0.5-0.7: 균형 잡힌 보안(권장)
      - 0.1-0.5: 낮은 보안(더 많은 사용자 허용)

4. 저장 및 게시
   - 만들기 를 클릭하여 구성 저장
   - 게시 를 클릭하여 사용할 수 있게 만듭니다

**유효성 검사 검사점:**

- 구성이 저장되었습니다
- 모든 필수 필드가 완료됨
- 구성이 게시되고 표시됨
- 오류 메시지 없음

+++

## reCAPTCHA 표준 설정

+++1단계: reCAPTCHA API 키 가져오기(세부 정보 참조)

>[!IMPORTANT]
>
> Edge Delivery Services Forms은 reCAPTCHA v2(점수 기반)만 지원합니다. 확인란 버전을 사용하지 마십시오.

**키 생성:**

1. Google reCAPTCHA 콘솔 액세스

   - [Google reCAPTCHA Admin Console](https://www.google.com/recaptcha/admin)&#x200B;(으)로 이동
   - Google 계정으로 로그인

2. 새 사이트 만들기

   - 새 사이트를 추가하려면 +를 클릭하십시오.
   - 레이블: 설명하는 이름을 입력합니다.
   - reCAPTCHA 유형: reCAPTCHA v2 > &quot;I&#39;m not a robot&quot; Invisible 을 선택합니다.
   - 도메인: 양식 도메인 추가
   - 약관에 동의하고 제출을 누릅니다

3. 키 수집

   - 사이트 키: 사이트 키(공개 키) 복사
   - 비밀 키: 비밀 키(개인 키) 복사

**유효성 검사 검사점:**

- reCAPTCHA 콘솔에서 사이트가 생성됨

- 사이트 키 획득됨

- 암호 키 획득됨

- 도메인이 추가되고 확인되었습니다.

+++

+++2단계: AEM 클라우드 구성 컨테이너 구성(세부 정보 참조)

엔터프라이즈 설정과 동일한 프로세스를 따릅니다.

1. 구성 브라우저에서 클라우드 구성 활성화

2. 컨테이너 구성 확인

3. 설정이 저장되었는지 확인

+++

+++3단계: AEM에서 reCAPTCHA 표준 서비스 구성(세부 정보 참조)

![reCAPTCHA 표준 구성 화면](/help/edge/docs/forms/universal-editor/assets/recaptcha.png)
*그림: AEM의 reCAPTCHA 표준 구성 인터페이스*

**구성:**

1. reCAPTCHA 구성 액세스

   - 도구 > 클라우드 서비스 > reCAPTCHA로 이동합니다.
   - 양식의 구성 컨테이너 선택
   - 만들기 를 클릭합니다

2. 표준 설정 구성

   - 제목: 설명하는 이름(예: &quot;Standard reCAPTCHA&quot;)
   - 이름: 시스템 이름(자동 생성 또는 사용자 지정)
   - 버전: ReCAPTCHA v2 선택
   - 사이트 키: Google reCAPTCHA 사이트 키 입력
   - 비밀 키: Google reCAPTCHA 비밀 키 입력

3. 저장 및 게시

   - 만들기 를 클릭하여 구성 저장
   - 게시 를 클릭하여 사용할 수 있게 만듭니다

**유효성 검사 검사점:**

- 오류 없이 구성이 생성됨

- 두 키가 모두 올바르게 입력됨

- 구성이 게시되었습니다

- 구성이 목록에 나타납니다.

+++

## 양식에 reCAPTCHA 추가

reCAPTCHA 서비스를 구성한 후 다음과 같이 양식에 보호를 추가합니다.

![양식에 reCAPTCHA 구성 요소 추가](/help/edge/docs/forms/universal-editor/assets/add-recaptcha-component.png)
*그림: 폼에 보이지 않는 Captcha 구성 요소 추가*

+++1 유니버설 편집기에서 양식 열기
AEM Sites에서 양식으로 이동한 다음 편집 을 클릭하여 범용 편집기에서 엽니다. 편집기가 로드될 때까지 기다립니다.

- AEM Sites에서 양식으로 이동
- 편집 을 클릭하여 범용 편집기에서 엽니다.
- 편집기가 로드될 때까지 대기
+++

+++2. 양식 구조 찾기
콘텐츠 트리(왼쪽 패널)에서 적응형 양식 섹션을 찾아 양식 구조를 확장하여 삽입점을 확인합니다.

- 콘텐츠 트리(왼쪽 패널)에서 적응형 양식 섹션을 찾습니다
- 양식 구조를 확장하여 삽입점 표시
+++

+++3. reCAPTCHA 구성 요소 추가
Captcha(보이지 않음) 구성 요소를 양식에 추가합니다.

- 양식 섹션에서 추가 (+) 아이콘을 클릭합니다.
- 구성 요소 목록에서 Captcha(보이지 않음)를 선택합니다
- 또는 구성 요소 패널에서 구성 요소를 드래그하여 놓습니다
+++

+++4. 구성 요소 구성(선택 사항)
새로 추가된 captcha 구성 요소를 선택하고 reCAPTCHA 구성을 사용하는지 확인합니다.

- 새로 추가된 captcha 구성 요소 선택
- 속성 패널에서 reCAPTCHA 구성을 사용하는지 확인합니다
- 기본 설정에 대한 추가 구성이 필요하지 않습니다
+++

+++5. 변경 사항 게시
변경 사항을 게시하고 오류가 없는지 확인합니다.

- 범용 편집기에서 게시 를 클릭합니다.
- 확인 대기
- 오류가 표시되지 않는지 확인
+++

### 구현 확인

이제 다음 위치에서 보호된 양식을 사용할 수 있습니다.

```
https://<branch>--<repo>--<owner>.aem.live/content/forms/af/
<form-name>
```

**예제 URL:**

```
https://main--my-forms--company.aem.live/content/forms/af/
contact-form
```
