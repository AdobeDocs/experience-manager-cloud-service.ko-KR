---
title: 범용 편집기에서 양식에 Google reCAPTCHA 추가
description: 스팸 및 자동화된 공격을 방지하기 위해 Edge Delivery Services 양식에 Google reCAPTCHA 보호 기능을 구현하는 방법에 대한 안내서입니다.
feature: Edge Delivery Services
keywords: 양식의 reCAPTCHA, 범용 편집기에서 reCAPTCHA 사용, 양식의 reCAPTCHA 추가, 양식 보안, 스팸 방지
role: Developer, Admin
level: Intermediate
exl-id: 1f28bd13-133f-487e-8b01-334be7c08a3f
source-git-commit: fd3c53cf5a6d1c097a5ea114a831ff626ae7ad7e
workflow-type: ht
source-wordcount: '1281'
ht-degree: 100%

---


# 범용 편집기에서 양식에 Google reCAPTCHA 추가

Google reCAPTCHA는 사람 사용자와 자동화된 봇을 구분하여 양식을 보호하는 데 도움이 됩니다. 이 안내서에서는 범용 편집기에서 reCAPTCHA Enterprise 및 Standard 버전을 모두 구현하는 방법을 설명합니다.

**목표:**

- 적절한 reCAPTCHA 솔루션을 선택합니다.
- reCAPTCHA Enterprise 또는 Standard를 구성합니다.
- 양식에 reCAPTCHA를 추가합니다.
- 구현의 유효성을 검사하고 테스트합니다.
- 성능을 모니터링하고 최적화합니다.

## 사전 요구 사항

시작하기 전에 다음 사전 요구 사항이 충족되었는지 확인합니다.

### 액세스 요구 사항

- AEM as a Cloud Service 작성 액세스
- 양식 편집 권한이 있는 범용 편집기 액세스

### 기술 요구 사항

- 활성화된 Google 계정
- Enterprise의 경우: 청구가 활성화된 Google Cloud Platform 프로젝트
- Standard의 경우: Google reCAPTCHA 계정
- 양식에 대한 확인된 도메인 소유권

### 지식 요구 사항

- AEM Forms 및 범용 편집기에 대한 기본 지식
- 클라우드 서비스 구성에 대한 이해
- 양식 보안 개념에 대한 이해

## 양식에 reCAPTCHA를 사용하는 이유

| ![보안](/help/edge/docs/forms/universal-editor/assets/security.svg) | ![봇 보호](/help/edge/docs/forms/universal-editor/assets/bot-protection.svg) | ![사용자 경험](/help/edge/docs/forms/universal-editor/assets/user-experience.svg) |
|:-------------:|:-------------:|:-------------:|
| **향상된 보안** | **봇 및 스팸 방지** | **원활한 사용자 경험** |
| 사기 활동 및 공격으로부터 양식 보호 | 자동화된 봇이 양식을 제출하지 못하도록 방지 | 보이지 않는 reCAPTCHA가 합법적인 사용자를 방해하지 않습니다. |

**핵심 개념:** reCAPTCHA는 머신 러닝을 사용하여 사용자 비헤이비어를 분석하고 사람과의 상호 작용 가능성을 나타내는 점수(0.0~1.0)를 할당합니다. 점수가 높을수록 사람 사용자이며, 낮을수록 봇입니다.

**예:** 민감한 데이터를 처리하는 세금 계산 양식에는 자동화된 공격에 대한 보호가 필요합니다. reCAPTCHA는 제출이 봇이 아닌 실제 사용자에 의해 이루어졌는지 확인합니다.

## 적절한 reCAPTCHA 솔루션 선택

Edge Delivery Services 양식은 두 가지 Google reCAPTCHA 옵션을 지원합니다. 다음 기준을 사용하여 올바른 솔루션을 선택합니다.

### 빠른 결정 안내서

**다음과 같은 경우 reCAPTCHA Enterprise를 사용합니다.**

- 트래픽이 많은 양식 (월 10,000회 요청 초과)
- 엄격한 규정 준수 요구 사항 (GDPR, SOX, HIPAA)
- 고급 분석 및 보고에 대한 필요
- 프리미엄 보안 기능을 위한 예산
- 복잡한 다중 도메인 배포

**다음과 같은 경우 reCAPTCHA Standard를 사용합니다.**

- 보통 이하의 트래픽 (월 10,000회 요청 미만)
- 기본 보안 요구 사항
- 제한된 예산 (무료 계층)
- 간단한 단일 도메인 설정
- reCAPTCHA를 처음 사용하십니까?

### 상세 비교

| **기능** | **reCAPTCHA Enterprise** | **reCAPTCHA 표준** |
|-------------|--------------------------|------------------------|
| **비용** | 유료 (사용량 기반 가격 책정) | 무료 |
| **요청 제한** | 제한 없음 | 월 100만 회 요청 |
| **고급 Analytics** | 상세 보고 | 기본 통계만 해당 |
| **사용자 정의 규칙** | 계정별 규칙 | 글로벌 규칙만 해당 |
| **다중 도메인 지원** | 고급 관리 | 기본 지원 |
| **SLA** | 99.9% 가동 시간 보장 | 모범 사례 |
| **지원** | 엔터프라이즈 지원 | 커뮤니티 지원 |
| **규정 준수** | 엔터프라이즈급 | 표준 규정 준수 |

**두 솔루션 모두 다음을 제공합니다.**

- 점수 기반 감지 (0.0~1.0 배율)
- 보이지 않는 작업 (사용자 상호 작용 필요 없음)
- 머신 러닝 기반 봇 감지
- 실시간 위험 평가

## reCAPTCHA Enterprise 설정하기


+++ 1단계: Google Cloud 환경 준비

**요구 사항:**

1. 청구가 활성화된 Google Cloud 프로젝트
2. 프로젝트 ID (GCP 대시보드에서)
3. 양식에 대한 도메인 확인
4. GCP 및 AEM에 대한 관리자 액세스

**설정:**

1. Google Cloud 프로젝트를 만들거나 선택합니다.
   - [Google Cloud Console](https://console.cloud.google.com/)로 이동합니다.
   - 새 프로젝트를 만들거나 기존 프로젝트를 선택합니다.
   - 프로젝트 ID를 기록합니다.

2. reCAPTCHA Enterprise API를 활성화합니다.
   - API 및 서비스 > 라이브러리로 이동합니다.
   - “reCAPTCHA Enterprise API”를 검색합니다.
   - 활성화를 클릭합니다.

3. API 자격 증명을 만듭니다.
   - API 및 서비스 > 자격 증명으로 이동합니다.
   - 자격 증명 만들기 > API 키를 클릭합니다.
   - API 키를 복사하여 저장합니다.

4. 사이트 키를 만듭니다.
   - 보안 > reCAPTCHA Enterprise로 이동합니다.
   - 키 만들기를 클릭합니다.
   - 점수 기반 키 유형을 선택합니다.
   - 도메인을 추가합니다.
   - 임계값 점수를 설정합니다(권장: 0.5).

**유효성 검사 체크포인트:** 다음을 보유하고 있는지 확인합니다.

- 프로젝트 ID
- API 키
- 사이트 키
- Google Cloud에서 확인된 도메인

+++

+++ 2단계: AEM 클라우드 구성 컨테이너 구성

![단계별 cloud 구성 설정](/help/edge/docs/forms/universal-editor/assets/recaptcha-general-configuration.png)
*그림: 양식 컨테이너에 대한 클라우드 구성 활성화*

**설정:**

1. 구성 브라우저 액세스
   - AEM 작성자 인스턴스에 로그인합니다.
   - 도구 > 일반 > 구성 브라우저로 이동합니다.

2. 클라우드 구성 활성화
   - 양식의 구성 컨테이너를 찾습니다.
   - 속성을 선택합니다.
   - 클라우드 구성을 확인합니다.
   - 저장 및 닫기를 클릭합니다.

3. 구성 확인
   - 컨테이너 속성에 “클라우드 구성”이 표시되는지 확인합니다.

**유효성 검사 체크포인트:**

- 컨테이너에 대해 클라우드 구성이 활성화되었습니다.
- 컨테이너가 구성 브라우저에 표시됩니다.
- 속성에 “클라우드 구성”이 활성화된 것으로 표시됩니다.

+++

+++ 3단계: AEM에서 reCAPTCHA 엔터프라이즈 서비스 구성

![reCAPTCHA Enterprise 구성 화면](/help/edge/docs/forms/universal-editor/assets/recaptcha-enterprise.png)
*그림: AEM의 reCAPTCHA Enterprise 구성 인터페이스*

**구성:**

1. reCAPTCHA 구성 액세스
   - 도구 > 클라우드 서비스 > reCAPTCHA로 이동합니다.
   - 양식의 구성 컨테이너를 선택합니다.
   - 만들기를 클릭합니다.

2. Enterprise 설정 구성
   - 제목: 설명적인 이름 (예: “프로덕션 reCAPTCHA”)
   - 이름: 시스템 이름 (자동 생성 또는 사용자 정의)
   - 버전: ReCAPTCHA Enterprise를 선택합니다.
   - 프로젝트 ID: Google Cloud Project ID를 입력합니다.
   - 사이트 키: Google Cloud의 사이트 키를 입력합니다.
   - API 키: Google Cloud API 키를 입력합니다.
   - 키 유형: 점수 기반 사이트 키를 선택합니다.

3. 보안 임계값 설정
   - 임계값 점수: 0.0에서 1.0 사이로 설정합니다.
   - 권장 값:
      - 0.7-0.9: 높은 보안 수준 (일부 적합한 사용자를 차단할 수 있음)
      - 0.5-0.7: 균형 잡힌 보안 (권장)
      - 0.1-0.5: 낮은 보안 (더 많은 사용자 허용)

4. 저장 및 게시
   - 만들기를 클릭하여 구성을 저장합니다.
   - 게시를 클릭하여 사용 가능하게 만듭니다.

**유효성 검사 체크포인트:**

- 구성이 성공적으로 저장되었습니다.
- 모든 필수 필드가 완료되었습니다.
- 구성이 게시되고 표시됩니다.
- 오류 메시지가 없습니다.

+++

## reCAPTCHA 표준 설정

+++1단계: reCAPTCHA API 키 확보 (세부 정보 확인)

>[!IMPORTANT]
>
> Edge Delivery Services 양식은 reCAPTCHA v2(점수 기반)만 지원합니다. 확인란 버전은 사용하지 마십시오.

**키 생성:**

1. Google reCAPTCHA 콘솔에 액세스

   - [Google reCAPTCHA Admin Console](https://www.google.com/recaptcha/admin)로 이동합니다.
   - Google 계정으로 로그인합니다.

2. 새 사이트 만들기

   - +를 클릭하여 새 사이트를 추가합니다.
   - 레이블: 설명적인 이름을 입력합니다.
   - reCAPTCHA 유형: reCAPTCHA v2 > “로봇이 아닙니다” 보이지 않음을 선택합니다.
   - 도메인: 양식 도메인을 추가합니다.
   - 약관에 동의하고 제출을 클릭합니다.

3. 키 수집

   - 사이트 키: 사이트 키(공개 키)를 복사합니다.
   - 시크릿 키: 시크릿 키(비공개 키)를 복사합니다.

**유효성 검사 체크포인트:**

- reCAPTCHA 콘솔에 사이트가 생성되었습니다.

- 사이트 키를 얻었습니다.

- 시크릿 키를 얻었습니다.

- 도메인이 추가되고 확인되었습니다.

+++

+++2단계: AEM 클라우드 구성 컨테이너 구성 (세부 정보 확인)

Enterprise 설정과 동일한 프로세스를 따릅니다.

1. 구성 브라우저에서 클라우드 구성을 활성화합니다.

2. 컨테이너 구성을 확인합니다.

3. 설정이 저장되었는지 확인합니다.

+++

+++3단계: AEM에서 reCAPTCHA 표준 서비스 구성 (세부 정보 확인)

![reCAPTCHA 표준 구성 화면](/help/edge/docs/forms/universal-editor/assets/recaptcha.png)
*그림: AEM의 reCAPTCHA 표준 구성 인터페이스*

**구성:**

1. reCAPTCHA 구성 액세스

   - 도구 > 클라우드 서비스 > reCAPTCHA로 이동합니다.
   - 양식의 구성 컨테이너를 선택합니다.
   - 만들기를 클릭합니다.

2. 표준 설정 구성

   - 제목: 설명적인 이름 (예: “표준 reCAPTCHA”)
   - 이름: 시스템 이름 (자동 생성 또는 사용자 정의)
   - 버전: ReCAPTCHA v2를 선택합니다.
   - 사이트 키: Google reCAPTCHA 사이트 키를 입력합니다.
   - 시크릿 키: Google reCAPTCHA 시크릿 키를 입력합니다.

3. 저장 및 게시

   - 만들기를 클릭하여 구성을 저장합니다.
   - 게시를 클릭하여 사용 가능하게 만듭니다.

**유효성 검사 체크포인트:**

- 구성이 오류 없이 생성되었습니다.

- 두 키가 올바르게 입력되었습니다.

- 구성이 성공적으로 게시되었습니다.

- 구성이 목록에 나타납니다.

+++

## 양식에 reCAPTCHA 추가

reCAPTCHA 서비스를 구성한 후 다음과 같이 양식에 보호 기능을 추가합니다.

![양식에 reCAPTCHA 구성 요소 추가](/help/edge/docs/forms/universal-editor/assets/add-recaptcha-component.png)
*그림: 양식에 보이지 않는 Captcha 구성 요소 추가*

+++&#x200B;1. 범용 편집기에서 양식 열기
AEM Sites의 양식으로 이동하고 편집을 클릭하여 범용 편집기에서 엽니다. 편집기가 로드될 때까지 기다립니다.

- AEM Sites의 양식으로 이동합니다.
- 편집을 클릭하여 범용 편집기에서 엽니다.
- 편집기가 로드될 때까지 기다립니다.
+++

+++&#x200B;2. 양식 구조 찾기
콘텐츠 트리(왼쪽 패널)에서 적응형 양식 섹션을 찾아 양식 구조를 확장하여 삽입 지점을 확인합니다.

- 콘텐츠 트리(왼쪽 패널)에서 적응형 양식 섹션을 찾습니다.
- 양식 구조를 확장하여 삽입 지점을 확인합니다.
+++

+++&#x200B;3. reCAPTCHA 구성 요소 추가
양식에 Captcha(보이지 않음) 구성 요소를 추가합니다.

- 양식 섹션에서 추가(+) 아이콘을 클릭합니다.
- 구성 요소 목록에서 Captcha(보이지 않음)를 선택합니다.
- 또는 구성 요소 패널에서 구성 요소를 드래그 앤 드롭합니다.
+++

+++&#x200B;4. 구성 요소 구성 (선택 사항)
새로 추가한 Captcha 구성 요소를 선택하고 reCAPTCHA 구성을 사용하는지 확인합니다.

- 새로 추가된 Captcha 구성 요소를 선택합니다.
- 속성 패널에서 reCAPTCHA 구성을 사용하는지 확인합니다.
- 기본 설정에는 추가 구성이 필요하지 않습니다.
+++

+++&#x200B;5. 변경 사항 게시
변경 사항을 게시하고 오류가 없는지 확인합니다.

- 범용 편집기에서 게시를 클릭합니다.
- 확인을 기다립니다.
- 오류가 표시되지 않는지 확인합니다.
+++

### 구현을 확인합니다.

보호된 양식은 이제 다음에서 사용할 수 있습니다.

```
https://<branch>--<repo>--<owner>.aem.live/content/forms/af/
<form-name>
```

**예제 URL:**

```
https://main--my-forms--company.aem.live/content/forms/af/
contact-us-form
```
