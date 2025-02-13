---
title: AEM Forms as a Cloud Service용 Edge Delivery Services와 함께 reCAPTCHA 사용
description: AEM Forms용 Edge Delivery Services 양식에서 Google reCAPTCHA 사용
feature: Edge Delivery Services
keywords: 양식의 reCAPTCHA, 범용 편집기에서 reCAPTCHA 사용, 양식의 reCAPTCHA 추가
role: Admin, Architect, Developer
hide: true
hidefromtoc: true
exl-id: 1f28bd13-133f-487e-8b01-334be7c08a3f
source-git-commit: 320ab86bc73e874705d985b927e90eec3cad1cf9
workflow-type: tm+mt
source-wordcount: '1225'
ht-degree: 6%

---


# WYSIWYG 작성에서 reCAPTCHA 사용

CAPTCHA (컴퓨터와 인간을 구분하기 위해 완전히 자동화된 공공 튜링 테스트)는 사기성 활동, 스팸 및 오용으로부터 웹 사이트를 보호하는 데 사용되는 인기있는 도구입니다.

예를 들어 추가 공제액과 세율을 기준으로 세금을 계산하는 양식을 생각해 보자. 이러한 경우, 악의적인 사용자가 피싱 이메일을 보내거나 스팸봇을 사용하여 관련이 없거나 유해한 콘텐츠를 대량으로 보내는 등의 목적으로 양식을 악용할 위험이 있습니다. CAPTCHA를 통합하면 제출 내용이 실제 사용자로부터 받은 것임을 확인하여 보안을 강화함으로써 스팸 항목을 효과적으로 최소화할 수 있습니다.

![Google recaptcha](/help/edge/docs/forms/universal-editor/assets/google-recaptcha.png)

Edge Delivery Services Forms에서 양식 블록을 사용하면 **Captcha(보이지 않음)** 구성 요소를 사용하여 [Google reCAPTCHA를 양식과 연결](#connect-forms-with-recaptcha-service-by-google)하여 사람과 보트를 구분할 수 있습니다. 이 기능은 작성자가 양식을 스팸 및 오용으로부터 보호하는 데 도움이 됩니다.

## Google에서 제공하는 reCAPTCHA 서비스와 Forms 연결

Edge Delivery Services Forms을 작성하여 Google에서 제공하는 reCAPTCHA 서비스를 구현할 수 있습니다. 필요에 따라 Edge Delivery Services Forms에 대해 다음 reCAPTCHA 서비스 중 하나를 구성할 수 있습니다.

* [reCAPTCHA 엔터프라이즈](#configure-recaptcha-enterprise)
* [reCAPTCHA](#configure-recaptcha)

>[!NOTE]
>
> reCAPTCHA 작동 방식에 대한 자세한 내용은 [Google reCAPTCHA](https://developers.google.com/recaptcha/)을(를) 참조하십시오.

### reCAPTCHA Enterprise 구성

reCAPTCHA Enterprise는 Google에서 제공하는 프리미엄 엔터프라이즈급 사기 행위 탐지 및 예방 서비스입니다. reCAPTCHA(점수 기반)를 기반으로 구축되지만 기업의 복잡한 요구 사항을 충족할 수 있는 추가적인 기능, 확장성 및 맞춤화를 제공합니다.

#### 시작하기에 앞서

Edge Delivery Services Forms용 Google reCAPTCHA Enterprise를 구성하기 전에 다음 단계를 완료했는지 확인하십시오.

1. [Google 클라우드 프로젝트](https://cloud.google.com/recaptcha/docs/prepare-environment#before-you-begin)를 만들거나 선택하고 [프로젝트 ID](https://support.google.com/googleapi/answer/7014113?hl=en#:~:text=To%20locate%20your%20project%20ID,a%20member%20of%20are%20displayed)를 검색합니다.

1. [Google Cloud 프로젝트에 대해 reCAPTCHA Enterprise API를 활성화](https://cloud.google.com/recaptcha/docs/prepare-environment#enable-api)하고 [API 키를 만듭니다](https://console.cloud.google.com/apis/credentials).

1. Google Cloud 프로젝트에 대한 [사이트 키](https://console.cloud.google.com/security/recaptcha)를 만들고 사이트 키를 복사합니다.

이러한 자격 증명이 있으면 양식에 대해 reCAPTCHA Enterprise 구성을 계속할 수 있습니다.

1. [클라우드 구성 컨테이너 만들기](#1-create-cloud-configuration-container)
1. [reCAPTCHA Enterprise용 클라우드 서비스 구성 만들기](#2-create-the-cloud-service-configuration-for-recaptcha-enterprise)

#### 1. 클라우드 구성 컨테이너 만들기

클라우드 구성 컨테이너를 만들려면 다음 단계를 수행하십시오.

1. 작성자 인스턴스에 로그인합니다.
1. **[!UICONTROL 도구]** ![도구-1](/help/forms/assets/tools-1.png) > **[!UICONTROL 일반]** > **[!UICONTROL 구성 브라우저]**&#x200B;로 이동합니다.

   ![클라우드 구성 컨테이너](/help/edge/docs/forms/universal-editor/assets/recaptcha-general-configuration.png)

1. **[!UICONTROL 구성 브라우저]**&#x200B;에서 양식으로 이동하여 **[!UICONTROL 속성]**&#x200B;을 선택합니다.

   ![클라우드 구성 속성](/help/edge/docs/forms/universal-editor/assets/general-configuration-properties.png)

1. **[!UICONTROL 구성 속성]** 대화 상자에서 **[!UICONTROL 클라우드 구성]**&#x200B;을 사용하도록 설정합니다.

1. 구성을 저장하고 대화 상자를 종료하려면 **[!UICONTROL 저장 및 닫기]**&#x200B;를 선택하십시오.

   ![클라우드 구성 속성 사용](/help/edge/docs/forms/universal-editor/assets/enable-cloud-configurations.png)
`
클라우드 구성 컨테이너를 만든 후 게시합니다.

   ![클라우드 구성 게시](/help/edge/docs/forms/universal-editor/assets/publish-cloud-configuration.png)

#### 2. reCAPTCHA Enterprise에 대한 클라우드 서비스 구성 만들기

reCAPTCHA Enterprise에 대한 클라우드 서비스 구성을 생성하려면 다음 단계를 수행하십시오.

1. 작성자 인스턴스에 로그인합니다.
1. **[!UICONTROL 도구]** ![도구-1](/help/forms/assets/tools-1.png) > **[!UICONTROL 클라우드 서비스]** > **[!UICONTROL reCAPTCHA]**(으)로 이동합니다.

   ![Recaptcha 클라우드 구성](/help/edge/docs/forms/universal-editor/assets/recaptcha-cloud-configuration.png)

   **구성** 대화 상자가 열립니다.

1. 양식으로 이동하여 **[!UICONTROL 만들기]**&#x200B;를 선택합니다.

   ![CAPTCHA 구성](/help/edge/docs/forms/universal-editor/assets/create-captcha-confguration.png)

   **[!UICONTROL reCAPTCHA 구성 만들기]** 대화 상자가 열립니다.

   ![reCaptcha Enterprise](/help/edge/docs/forms/universal-editor/assets/recaptcha-enterprise.png)

1. 버전을 [!DNL ReCAPTCHA Enterprise](으)로 선택하고 제목, 이름, 프로젝트 ID, 사이트 키 및 API 키를 지정합니다.

   >[!NOTE]
   >
   > reCAPTCHA Enterprise의 [시작하기 전에](#before-you-start) 섹션에서 프로젝트 ID, 사이트 키 및 API 키를 가져올 수 있습니다.

1. **[!UICONTROL 키 유형]**&#x200B;을(를) **점수 기반 사이트 키**(으)로 선택하십시오.
1. 0에서 1](https://cloud.google.com/recaptcha/docs/interpret-assessment-website#interpret_scores) 사이의 [임계값 점수를 지정하십시오. 임계값 점수보다 크거나 같은 점수는 인간 상호 작용을 식별하며, 그렇지 않으면 봇 상호 작용으로 간주됩니다.
1. 클라우드 서비스 구성을 만들려면 **[!UICONTROL 만들기]**&#x200B;를 선택하십시오.

   reCAPTCHA 클라우드 구성을 만든 후 게시합니다.

   ![Recaptcha 구성 게시](/help/edge/docs/forms/universal-editor/assets/publisg-recaptcha-configuration.png)

이제 WYSIWYG 기반 작성을 사용하여 양식을 만들거나 편집하고 reCAPTCHA 구성 요소를 추가할 수 있습니다. 양식에 Google reCAPTCHA를 통합하는 방법에 대한 자세한 지침은 [양식에서 reCAPTCHA 사용](#use-recaptcha-in-your-form)을 참조하세요.

## reCAPTCHA 구성

reCAPTCHA는 Google에서 제공하는 무료 서비스로, 웹사이트가 봇과 스팸을 포함한 모욕적인 트래픽을 감지하고 방지할 수 있도록 도와줍니다. 백그라운드에서 작동하는 점수 기반 버전을 지원하고 각 사용자 상호 작용에 위험 점수(0.0~1.0 범위)를 할당합니다. 임계값 점수보다 크거나 같은 점수는 인간 상호 작용을 식별하며, 그렇지 않으면 봇 상호 작용으로 간주됩니다.

#### 시작하기 전에

Edge Delivery Services Forms용 Google reCAPTCHA를 구성하기 전에 Google 콘솔에서 [reCAPTCHA API 키 쌍을 검색하십시오](https://www.google.com/recaptcha/admin). 이 쌍은 사이트 키 및 비밀 키를 포함합니다.

>[!NOTE]
>
> * Edge Delivery Services Forms은 **reCAPTCHA 점수 기반** 버전만 지원합니다.

API 키 쌍이 있으면 양식에 대해 reCAPTCHA 구성을 계속할 수 있습니다.

1. [클라우드 구성 컨테이너 만들기](#1-create-cloud-configuration-container-1)
1. [reCAPTCHA에 대한 클라우드 서비스 구성 만들기](#2-create-the-cloud-service-configuration-for-recaptcha)

#### 1. 클라우드 구성 컨테이너 만들기

클라우드 구성 컨테이너를 만들려면 다음 단계를 수행하십시오.

1. 작성자 인스턴스에 로그인합니다.
1. **[!UICONTROL 도구]** ![도구-1](/help/forms/assets/tools-1.png) > **[!UICONTROL 일반]** > **[!UICONTROL 구성 브라우저]**&#x200B;로 이동합니다.

   ![클라우드 구성 컨테이너](/help/edge/docs/forms/universal-editor/assets/recaptcha-general-configuration.png)

1. **[!UICONTROL 구성 브라우저]**&#x200B;에서 양식으로 이동하여 **[!UICONTROL 속성]**&#x200B;을 선택합니다.

   ![클라우드 구성 속성](/help/edge/docs/forms/universal-editor/assets/general-configuration-properties.png)

1. **[!UICONTROL 구성 속성]** 대화 상자에서 **[!UICONTROL 클라우드 구성]**&#x200B;을 사용하도록 설정합니다.

1. 구성을 저장하고 대화 상자를 종료하려면 **[!UICONTROL 저장 및 닫기]**&#x200B;를 선택하십시오.

   ![클라우드 구성 속성 사용](/help/edge/docs/forms/universal-editor/assets/enable-cloud-configurations.png)

   클라우드 구성 컨테이너를 만든 후 게시합니다.

   ![클라우드 구성 게시](/help/edge/docs/forms/universal-editor/assets/publish-cloud-configuration.png)

#### 2. reCAPTCHA에 대한 클라우드 서비스 구성 만들기

reCAPTCHA에 대한 클라우드 서비스 구성을 만들려면 다음 단계를 수행하십시오.

1. 작성자 인스턴스에 로그인합니다.
1. **[!UICONTROL 도구]** ![도구-1](/help/forms/assets/tools-1.png) > **[!UICONTROL 클라우드 서비스]** > **[!UICONTROL reCAPTCHA]**(으)로 이동합니다.

   ![Recaptcha 클라우드 구성](/help/edge/docs/forms/universal-editor/assets/recaptcha-cloud-configuration.png)

   **구성** 대화 상자가 열립니다.

1. 양식으로 이동하여 **[!UICONTROL 만들기]**&#x200B;를 선택합니다.

   ![CAPTCHA 구성](/help/edge/docs/forms/universal-editor/assets/create-captcha-confguration.png)

   **[!UICONTROL reCAPTCHA 구성 만들기]** 대화 상자가 열립니다.

   ![reCaptcha Enterprise](/help/edge/docs/forms/universal-editor/assets/recaptcha.png)

1. 버전을 [!DNL ReCAPTCHA v2](으)로 선택하고 제목 및 이름 을 지정하십시오.
1. 사이트 키 및 암호 키를 지정합니다.

   >[!NOTE]
   >
   > reCAPTCHA에 대한 [시작하기 전에](#before-you-begin) 섹션에서 사이트 키 및 암호 키를 가져올 수 있습니다.

1. 클라우드 서비스 구성을 만들려면 **[!UICONTROL 만들기]**&#x200B;를 선택하십시오.

   reCAPTCHA 클라우드 구성을 만든 후 게시합니다.

   ![Recaptcha 구성 게시](/help/edge/docs/forms/universal-editor/assets/publisg-recaptcha-configuration.png)

이제 WYSIWYG 기반 작성을 사용하여 양식을 작성 및 편집하고 reCAPTCHA 구성 요소를 추가할 수 있습니다. 양식에 Google reCAPTCHA를 통합하는 방법에 대한 자세한 지침은 [양식에서 reCAPTCHA 사용](#use-recaptcha-in-your-form)을 참조하세요.

### 양식에서 reCAPTCHA 사용

양식을 작성하고 reCAPTCHA(보이지 않음) 구성 요소를 추가하려면 다음 단계를 수행하십시오.

1. 편집을 위해 범용 편집기에서 양식을 엽니다.
1. 콘텐츠 트리에서 추가된 적응형 양식 섹션으로 이동합니다.
1. **[!UICONTROL 추가]** 아이콘을 클릭하고 **적응형 양식 구성 요소** 목록에서 **[!UICONTROL Captcha(Invisible)]** 구성 요소를 추가합니다.

   ![reCaptcha 구성 요소 추가](/help/edge/docs/forms/universal-editor/assets/add-recaptcha-component.png)

   또한 범용 편집기에서 직관적인 드래그 앤 드롭 기능을 제공하므로 필요한 적응형 Forms 구성 요소를 드래그 앤 드롭할 수도 있습니다.

1. **[!UICONTROL Captcha(Invisible)]** 구성 요소를 추가한 후 양식을 다시 게시하려면 **게시**&#x200B;를 클릭하십시오.

   ![양식 다시 게시](/help/edge/docs/forms/universal-editor/assets/publish-form.png)

이제 다음 URL에서 reCAPTCHA 서비스를 사용하여 양식을 볼 수 있습니다.
`https://<branch>--<repo>--<owner>.aem.live/content/forms/af/<form-name`.

![reCAPTCHA가 있는 양식](/help/edge/docs/forms/universal-editor/assets/form-with-recaptcha.png)

## 자주 묻는 질문

* **사용자가 reCAPTCHA 클라우드 구성을 만들지 않으면 어떻게 됩니까?**

  **A**: 사용자가 reCAPTCHA 클라우드 구성을 만들지 않은 경우 AEM 서버는 전역 구성 컨테이너에서 reCAPTCHA 클라우드 구성을 검색합니다. 전역 구성 컨테이너에 구성이 없는 경우 AEM 서버에서 오류가 발생합니다.

* **사용자가 여러 reCAPTCHA 클라우드 구성을 만들면 어떻게 됩니까?**
  **A**: 사용자가 두 개 이상의 reCAPTCHA 클라우드 구성을 만드는 경우 시스템이 처음 만든 reCAPTCHA 구성을 자동으로 선택합니다.

* **수정 사항 또는 변경 사항이 게시된 URL에 표시되지 않는 이유는 무엇입니까?**
게시된 URL에 수정 또는 변경 사항이 표시되지 않는 경우 업데이트를 적용하려면 양식을 다시 게시해야 합니다.

* **Edge Delivery Services Forms에서 지원하는 reCAPTCHA 서비스는 무엇입니까?**
  **A**: Edge Delivery Services Forms은 Google에서 제공하는 점수 기반 reCAPTCHA 서비스만 지원합니다.


## 추가 참조

{{see-more-forms-eds}}
