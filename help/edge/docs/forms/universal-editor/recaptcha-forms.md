---
title: reCAPTCHA - 시각적 안내서를 사용하여 Forms 보호
description: 스팸 및 보트 제출을 방지하기 위해 Google reCAPTCHA를 Edge Delivery Services 양식에 손쉽게 추가하는 방법을 알아봅니다
feature: Edge Delivery Services
keywords: 양식의 reCAPTCHA, 범용 편집기에서 reCAPTCHA 사용, 양식의 reCAPTCHA 추가, 양식 보안, 스팸 보호
role: Developer
exl-id: 1f28bd13-133f-487e-8b01-334be7c08a3f
source-git-commit: babddee34b486960536ce7075684bbe660b6e120
workflow-type: tm+mt
source-wordcount: '1085'
ht-degree: 1%

---


# Google reCAPTCHA를 사용하여 스팸으로부터 Forms 보호

<span class="preview"> 이 기능은 조기 액세스 프로그램을 통해 사용할 수 있습니다. 액세스를 요청하려면 공식 주소에서 GitHub 조직 이름 및 저장소 이름으로 <a href="mailto:aem-forms-ea@adobe.com">aem-forms-ea@adobe.com</a>에 전자 메일을 보내십시오.</span>



## 양식에서 reCAPTCHA를 사용하는 이유는 무엇입니까?

| ![보안](/help/edge/docs/forms/universal-editor/assets/security.svg) | ![보트 보호](/help/edge/docs/forms/universal-editor/assets/bot-protection.svg) | ![사용자 환경](/help/edge/docs/forms/universal-editor/assets/user-experience.svg) |
|:-------------:|:-------------:|:-------------:|
| **향상된 보안** | **보트 및 스팸 방지** | **원활한 사용자 환경** |
| 사기성 활동 및 악의적인 공격으로부터 양식 보호 | 자동화된 봇이 관련성이 없거나 유해한 콘텐츠로 양식을 유출하지 않도록 방지 | 보이지 않는 reCAPTCHA는 정당한 사용자를 방해하지 않고 뒤에서 작동한다 |

예를 들어 민감한 재무정보를 담은 세금계산서는 오남용으로부터 보호가 필요하다. reCAPTCHA는 제출물이 자동화된 시스템이 아닌 실제 사용자로부터 왔는지를 확인합니다.

## reCAPTCHA 솔루션 선택

Edge Delivery Services Forms은 두 가지 Google reCAPTCHA 옵션을 지원합니다.

| ![reCAPTCHA Enterprise](/help/edge/docs/forms/universal-editor/assets/enterprise.svg) | ![reCAPTCHA 표준](/help/edge/docs/forms/universal-editor/assets/standard.svg) |
|:-------------:|:-------------:|
| [**reCAPTCHA Enterprise**](#set-up-recaptcha-enterprise) | [**reCAPTCHA 표준**](#set-up-recaptcha-standard) |
| 추가 기능 및 맞춤화를 통해 엔터프라이즈급 부정 행위 감지 기능 제공 | 배경에서 보이지 않게 작동하는 점수 기반 감지 기능이 있는 무료 서비스 |
| 최적의 용도: 복잡한 보안 요구 사항이 있는 대규모 조직 | 최적의 솔루션: 기본적인 보호 요구 사항을 가진 중소 규모 프로젝트 |

두 옵션 모두 점수 기반 감지(0.0 - 1.0)를 사용하여 사용자 경험을 중단하지 않고 인간과 봇 상호 작용을 식별합니다.

## reCAPTCHA Enterprise 설정

### 1단계: Google Cloud 자격 증명 가져오기

reCAPTCHA Enterprise를 구성하기 전에 다음이 필요합니다.

- [프로젝트 ID](https://support.google.com/googleapi/answer/7014113)의 [Google Cloud 프로젝트](https://cloud.google.com/recaptcha/docs/prepare-environment#before-you-begin)
- 프로젝트에 대해 [reCAPTCHA Enterprise API가 활성화됨](https://cloud.google.com/recaptcha/docs/prepare-environment#enable-api)
- 인증을 위한 [API 키](https://console.cloud.google.com/apis/credentials)
- 도메인의 [사이트 키](https://console.cloud.google.com/security/recaptcha)

### 2단계: 클라우드 구성 컨테이너 만들기

![단계별 클라우드 구성 설정](/help/edge/docs/forms/universal-editor/assets/recaptcha-general-configuration.png)

1. AEM 작성자 인스턴스에 로그인합니다
2. **도구** > **일반** > **구성 브라우저**(으)로 이동
3. 양식을 찾아 **속성** 선택
4. 대화 상자에서 **클라우드 구성** 사용
5. 구성 저장 및 게시

### 3단계: reCAPTCHA 엔터프라이즈 서비스 구성

![reCAPTCHA Enterprise 구성 화면](/help/edge/docs/forms/universal-editor/assets/recaptcha-enterprise.png)

1. **도구** > **클라우드 서비스** > **reCAPTCHA**(으)로 이동
2. 양식으로 이동하여 **만들기**&#x200B;를 클릭합니다.
3. 대화 상자에서:
   - **ReCAPTCHA Enterprise** 버전 선택
   - 제목 및 이름 입력
   - 프로젝트 ID, 사이트 키 및 API 키 추가
   - 키 유형으로 **점수 기반 사이트 키** 선택
   - 봇과 인간을 구분하도록 임계값 점수(0-1)를 설정합니다
4. **만들기**&#x200B;를 클릭하고 구성을 게시합니다.

## reCAPTCHA Standard 설정

### 1단계: API 키 가져오기

시작하기 전에 [Google reCAPTCHA 콘솔에서 reCAPTCHA API 키 쌍](https://www.google.com/recaptcha/admin)&#x200B;(사이트 키 및 암호 키)을 가져옵니다.

>[!IMPORTANT]
>
>Edge Delivery Services 양식만 **reCAPTCHA 점수 기반 버전**&#x200B;을 지원합니다.

### 2단계: 클라우드 구성 컨테이너 만들기

Enterprise 버전과 동일한 단계에 따라 클라우드 구성 컨테이너를 생성하고 게시합니다.

### 3단계: reCAPTCHA 표준 서비스 구성

![reCAPTCHA 표준 구성 화면](/help/edge/docs/forms/universal-editor/assets/recaptcha.png)

1. **도구** > **클라우드 서비스** > **reCAPTCHA**(으)로 이동
2. 양식으로 이동하여 **만들기**&#x200B;를 클릭합니다.
3. 대화 상자에서:
   - **ReCAPTCHA v2** 버전 선택
   - 제목 및 이름 입력
   - 사이트 키 및 암호 키 추가
4. **만들기**&#x200B;를 클릭하고 구성을 게시합니다.

## 양식에 reCAPTCHA 추가

이제 reCAPTCHA를 구성했으므로 양식에 추가할 차례입니다.

![양식에 reCAPTCHA 구성 요소 추가](/help/edge/docs/forms/universal-editor/assets/add-recaptcha-component.png)

1. 유니버설 편집기에서 양식 열기
2. 콘텐츠 트리의 적응형 양식 섹션으로 이동합니다
3. **추가** 아이콘을 클릭하고 적응형 양식 구성 요소 목록에서 **Captcha(보이지 않음)**&#x200B;을(를) 선택합니다.
   - *또는 구성 요소를 양식으로 끌어다 놓으십시오*
4. reCAPTCHA 보호를 사용하여 양식을 업데이트하려면 **게시**&#x200B;를 클릭하십시오.

이제 양식이 보호됩니다! 다음에서 보기:
`https://<branch>--<repo>--<owner>.aem.live/content/forms/af/<form-name>`

![reCAPTCHA 보호가 활성화된 양식](/help/edge/docs/forms/universal-editor/assets/form-with-recaptcha.png)

## reCAPTCHA 통합 확인

양식에 reCAPTCHA를 추가한 후에는 제대로 작동하는지 확인해야 합니다. 구현의 유효성을 검사하는 방법은 다음과 같습니다.

### 시각적 확인

reCAPTCHA v2(점수 기반)는 보이지 않게 작동하지만 다음을 통해 존재를 확인할 수 있습니다.

1. **페이지 소스 검사**: 양식 페이지를 마우스 오른쪽 단추로 클릭하고 &quot;페이지 Source 보기&quot;를 선택합니다.
   - 사이트 키를 사용하여 reCAPTCHA 스크립트 포함을 찾습니다
   - 예: `<script src="https://www.google.com/recaptcha/api.js?render=YOUR_SITE_KEY"></script>`

2. **네트워크 요청 확인**: 브라우저 개발자 도구 사용(F12)
   - 양식을 제출하고 `google.com/recaptcha`에 대한 네트워크 요청을 찾습니다.
   - 이러한 요청은 양식에서 reCAPTCHA가 활성화되었음을 나타냅니다.

### 기능 테스트

reCAPTCHA가 실제로 양식을 보호하고 있는지 확인하려면:

1. **일반 제출 테스트**:
   - 유효한 데이터로 양식 작성
   - 일반적인 속도로 양식 제출
   - 양식 제출 성공 여부 확인

2. **봇과 유사한 동작 테스트**:
   - 시크릿/비공개 탐색 창에서 양식 열기
   - 양식을 매우 빠르게 작성(자동화와 유사한 행동)
   - 빠르게 연속해서 여러 번 제출
   - reCAPTCHA가 작동하는 경우 이러한 제출이 차단되거나 플래그가 지정될 수 있습니다

3. **양식 전송 레코드 확인**:
   - 양식 제출 데이터 검토
   - 각 제출에는 reCAPTCHA 점수가 포함되어야 합니다
   - 점수가 1.0에 가까우면 사람 사용자일 가능성이 높습니다
   - 점수가 0.0에 가까우면 잠재적인 봇 활동을 나타냅니다.

### Google reCAPTCHA Admin Console 사용

엔터프라이즈 사용자를 위해 Google Cloud Console은 다음과 같은 세부 분석을 제공합니다.

1. [Google 클라우드 콘솔로 이동](https://console.cloud.google.com/)
2. **보안** > **reCAPTCHA**(으)로 이동
3. 사이트 키 선택
4. 평가 차트 및 통계 검토
5. 다음을 찾습니다.
   - 트래픽 패턴
   - 점수 분포
   - 잠재적으로 사기성 활동

표준 reCAPTCHA 사용자의 경우 [reCAPTCHA Admin Console](https://www.google.com/recaptcha/admin/)에서 기본 통계를 사용할 수 있습니다.

### 구현 조정

유효성 검사 결과를 기반으로 다음을 수행합니다.

- 합법적인 사용자가 차단되고 있는 경우 임계값 점수를 낮추는 것이 좋습니다.
- 스팸을 계속 받고 있는 경우 임계값 점수를 높이는 것이 좋습니다
- 지속적인 문제의 경우 reCAPTCHA 구성을 검토하고 모든 키가 올바르게 입력되었는지 확인하십시오

reCAPTCHA는 시간이 지남에 따라 머신 러닝을 사용하여 개선되므로 사이트의 트래픽 패턴을 학습함에 따라 그 효과가 증가할 수 있다는 점을 기억하십시오.

## 문제 해결 및 FAQ

| ![질문](/help/edge/docs/forms/universal-editor/assets/question.svg) | ![답변](/help/edge/docs/forms/universal-editor/assets/answer.svg) |
|:-------------:|:-------------:|
| **reCAPTCHA 구성을 만들지 않으면 어떻게 합니까?** | 시스템은 전역 컨테이너에서 구성을 찾습니다. 존재하지 않으면 오류가 발생합니다. |
| **구성을 여러 개 만들면 어떻게 합니까?** | 시스템은 처음 생성된 구성을 자동으로 사용합니다. |
| **게시된 URL에 변경 내용이 표시되지 않는 이유는 무엇입니까?** | 변경한 후 양식을 다시 게시해야 합니다. |
| **지원되는 reCAPTCHA 서비스는 무엇입니까?** | Edge Delivery Services Forms은 점수 기반 reCAPTCHA 서비스만 지원합니다. |

## 다음 단계

이제 reCAPTCHA로 양식을 보호했으므로:

- **구현의 유효성을 검사하십시오**: [유효성 검사 단계](#-validating-your-recaptcha-integration)에 따라 reCAPTCHA가 올바르게 작동하는지 확인하십시오
- **성능 모니터링**: Google reCAPTCHA 대시보드에서 의심되는 활동 및 점수 분포를 정기적으로 확인합니다
- **설정 미세 조정**: 보안 요구 사항 및 사용자 경험 피드백에 따라 임계값 점수를 조정합니다
- **업데이트 유지**: Google의 최신 보안 권장 사항을 사용하여 reCAPTCHA 구현을 최신 상태로 유지하십시오.
- **팀 교육**: reCAPTCHA 작동 방식과 분석을 해석하는 방법에 대한 지식을 공유합니다.
- **피드백 수집**: 올바른 사용자가 차단되지 않도록 사용자 환경을 모니터링합니다.

효과적인 양식 보호는 정기적인 모니터링과 조정이 필요한 지속적인 프로세스라는 점을 기억하십시오.


