---
title: AEM Forms as a Cloud Service용 Edge Delivery Services와 함께 reCAPTCHA 사용
description: AEM Forms용 Edge Delivery Services 양식에서 Google reCAPTCHA 사용
feature: Edge Delivery Services
keywords: 양식의 reCAPTCHA, 범용 편집기에서 reCAPTCHA 사용, 양식의 reCAPTCHA 추가
role: Admin, Architect, Developer
exl-id: 1f28bd13-133f-487e-8b01-334be7c08a3f
source-git-commit: 0c6f024594e1b1fd98174914d2c0714dffecb241
workflow-type: tm+mt
source-wordcount: '1273'
ht-degree: 96%

---


# WYSIWYG 작성에서 reCAPTCHA 사용

<span class="preview"> 이 기능은 조기 액세스 프로그램을 통해 사용할 수 있습니다. 액세스를 요청하려면 공식 주소에서 GitHub 조직 이름 및 저장소 이름으로 <a href="mailto:aem-forms-ea@adobe.com">aem-forms-ea@adobe.com</a>(으)로 이메일을 보내십시오. 예를 들어 저장소 URL이 https://github.com/adobe/abc이면 조직 이름은 adobe이고 저장소 이름은 abc입니다.</span>


CAPTCHA(컴퓨터와 인간을 구분하기 위해 완전히 자동화된 공개 튜링 테스트)는 웹 사이트를 사기, 스팸 및 오용으로부터 보호하는 데 사용되는 인기 있는 도구입니다.

예를 들어 추가 공제와 세율을 기준으로 세금을 계산하는 양식을 생각해 보겠습니다. 이러한 경우, 악의적인 사용자가 피싱 이메일을 보내거나 스팸봇을 사용하여 관련이 없거나 유해한 콘텐츠를 대량으로 보내는 등의 목적으로 양식을 악용할 위험이 있습니다. CAPTCHA를 통합하면 실제 사용자가 제출한 것인지 확인해서 스팸 항목을 효과적으로 최소화하여 보안을 강화합니다.

![Google recaptcha](/help/edge/docs/forms/universal-editor/assets/google-recaptcha.png)

Edge Delivery Services Forms에서 양식 블록을 사용하면 **Captcha(숨김)** 구성 요소를 사용하여 [Google reCAPTCHA를 양식과 연결](#connect-forms-with-recaptcha-service-by-google)하여 사람과 봇을 구분할 수 있습니다. 이 기능은 작성자가 스팸 및 오용으로부터 양식을 보호하는 데 도움이 됩니다.

## Google의 reCAPTCHA 서비스와 양식 연결

Edge Delivery Services 양식을 작성하여 Google에서 제공하는 reCAPTCHA 서비스를 구현할 수 있습니다. 사용자의 요구 사항에 따라 Edge Delivery Services 양식에 대해 다음 reCAPTCHA 서비스 중 하나를 구성할 수 있습니다.

* [reCAPTCHA Enterprise](#configure-recaptcha-enterprise)
* [reCAPTCHA](#configure-recaptcha)

>[!NOTE]
>
> reCAPTCHA 작동 방식에 대한 자세한 내용은 [Google reCAPTCHA](https://developers.google.com/recaptcha/)를 참조하십시오.

### reCAPTCHA Enterprise 구성

reCAPTCHA Enterprise는 Google에서 제공하는 프리미엄 엔터프라이즈급 사기 탐지 및 예방 서비스입니다. reCAPTCHA(점수 기반)를 기반으로 구축되었지만 복잡한 비즈니스 요구 사항을 충족하기 위해 추가 기능, 확장성 및 사용자 정의 기능을 제공합니다.

#### 시작하기에 앞서

Edge Delivery Services 양식용 Google reCAPTCHA Enterprise를 구성하기 전에 다음 단계를 완료했는지 확인하십시오.

1. [Google Cloud 프로젝트](https://cloud.google.com/recaptcha/docs/prepare-environment#before-you-begin)를 만들거나 선택하고 [프로젝트 ID](https://support.google.com/googleapi/answer/7014113?hl=en#:~:text=To%20locate%20your%20project%20ID,a%20member%20of%20are%20displayed)를 가져옵니다.

1. Google Cloud 프로젝트에 [reCAPTCHA Enterprise API를 활성화](https://cloud.google.com/recaptcha/docs/prepare-environment#enable-api)하고 [API 키를 생성](https://console.cloud.google.com/apis/credentials)합니다.

1. [Google Cloud 프로젝트에 대한 사이트 키](https://console.cloud.google.com/security/recaptcha)를 생성하고 해당 사이트 키를 복사합니다.

이러한 자격 증명이 있으면 양식에 대한 reCAPTCHA Enterprise 구성을 진행할 수 있습니다.

1. [클라우드 구성 컨테이너 만들기](#1-create-cloud-configuration-container)
1. [reCAPTCHA Enterprise에 대한 클라우드 서비스 구성 만들기](#2-create-the-cloud-service-configuration-for-recaptcha-enterprise)

#### 1. 클라우드 구성 컨테이너 만들기

다음 단계를 수행하여 클라우드 구성 컨테이너를 만듭니다.

1. 작성자 인스턴스에 로그인합니다.
1. **[!UICONTROL 도구]** ![tools-1](/help/forms/assets/tools-1.png) > **[!UICONTROL 일반]** > **[!UICONTROL 구성 브라우저]**&#x200B;로 이동합니다.

   ![클라우드 구성 컨테이너](/help/edge/docs/forms/universal-editor/assets/recaptcha-general-configuration.png)

1. **[!UICONTROL 구성 브라우저]**&#x200B;에서 양식으로 이동하여 **[!UICONTROL 속성]**&#x200B;을 선택합니다.

   ![클라우드 구성 속성](/help/edge/docs/forms/universal-editor/assets/general-configuration-properties.png)

1. **[!UICONTROL 구성 속성]** 대화 상자에서 **[!UICONTROL 클라우드 구성]**&#x200B;을 활성화합니다.

1. **[!UICONTROL 저장 및 닫기]**&#x200B;를 선택하여 구성을 저장하고 대화 상자를 종료합니다.

   ![클라우드 구성 속성 활성화](/help/edge/docs/forms/universal-editor/assets/enable-cloud-configurations.png)
 `
클라우드 구성 컨테이너를 생성한 후 게시합니다.

   ![클라우드 구성 게시](/help/edge/docs/forms/universal-editor/assets/publish-cloud-configuration.png)

#### 2. reCAPTCHA Enterprise에 대한 클라우드 서비스 구성 만들기

reCAPTCHA Enterprise에 대한 클라우드 서비스 구성을 만들려면 다음 단계를 수행합니다.

1. 작성자 인스턴스에 로그인합니다.
1. **[!UICONTROL 도구]** ![tools-1](/help/forms/assets/tools-1.png) > **[!UICONTROL 클라우드 서비스]** > **[!UICONTROL reCAPTCHA]**&#x200B;로 이동합니다.

   ![Recaptcha 클라우드 구성](/help/edge/docs/forms/universal-editor/assets/recaptcha-cloud-configuration.png)

   **구성** 대화 상자가 열립니다.

1. 양식으로 이동하여 **[!UICONTROL 만들기]**&#x200B;를 선택합니다.

   ![Captcha 구성](/help/edge/docs/forms/universal-editor/assets/create-captcha-confguration.png)

   **[!UICONTROL reCAPTCHA 구성 만들기]** 대화 상자가 열립니다.

   ![reCaptcha Enterprise](/help/edge/docs/forms/universal-editor/assets/recaptcha-enterprise.png)

1. [!DNL ReCAPTCHA Enterprise]로 버전을 선택하고 제목, 이름, 프로젝트 ID, 사이트 키, API 키를 지정합니다.

   >[!NOTE]
   >
   > reCAPTCHA Enterprise의 [시작하기에 전에](#before-you-start) 섹션에서 프로젝트 ID, 사이트 키 및 API 키를 얻을 수 있습니다.

1. **[!UICONTROL 키 유형]**&#x200B;을 **점수 기반 사이트 키**&#x200B;로 선택합니다.
1. [임계값 점수를 0에서 1](https://cloud.google.com/recaptcha/docs/interpret-assessment-website#interpret_scores) 범위로 지정합니다. 임계값 점수 이상의 점수는 인간 상호 작용을 식별하며, 그렇지 않으면 봇 상호 작용으로 간주됩니다.
1. **[!UICONTROL 만들기]**&#x200B;를 선택하여 클라우드 서비스 구성을 만듭니다.

   reCAPTCHA 클라우드 구성을 만든 후 게시합니다.

   ![Recaptcha 구성 게시](/help/edge/docs/forms/universal-editor/assets/publisg-recaptcha-configuration.png)

이제 WYSIWYG 기반 작성을 사용하여 양식을 만들거나 편집하고 reCAPTCHA 구성 요소를 추가할 수 있습니다. Google reCAPTCHA를 양식에 통합하는 자세한 지침은 [양식에서 reCAPTCHA 사용](#use-recaptcha-in-your-form)을 참조하십시오.

## reCAPTCHA 구성

reCAPTCHA는 웹 사이트가 봇과 스팸을 포함한 악성 트래픽을 감지하고 예방할 수 있도록 도와주는 Google의 무료 서비스입니다. 백그라운드에서 작동하며 각 사용자 상호 작용에 위험 점수(0.0에서 1.0 범위)를 할당하는 점수 기반 버전을 지원합니다. 임계값 점수 이상의 점수는 인간 상호 작용을 식별하며, 그렇지 않으면 봇 상호 작용으로 간주됩니다.

#### 시작하기 전에

Edge Delivery Services 양식에 대해 Google reCAPTCHA를 구성하기 전에 [Google Console에서 reCAPTCHA API 키 쌍](https://www.google.com/recaptcha/admin)을 가져옵니다. 이 쌍에는 사이트 키와 비밀 키가 포함되어 있습니다.

>[!NOTE]
>
> * Edge Delivery Services 양식만 **reCAPTCHA 점수 기반 버전**&#x200B;을 지원합니다.

API 키 쌍이 있으면 양식에 대한 reCAPTCHA 구성을 진행할 수 있습니다.

1. [클라우드 구성 컨테이너 만들기](#1-create-cloud-configuration-container-1)
1. [reCAPTCHA에 대한 클라우드 서비스 구성 만들기](#2-create-the-cloud-service-configuration-for-recaptcha)

#### 1. 클라우드 구성 컨테이너 만들기

다음 단계를 수행하여 클라우드 구성 컨테이너를 만듭니다.

1. 작성자 인스턴스에 로그인합니다.
1. **[!UICONTROL 도구]** ![tools-1](/help/forms/assets/tools-1.png) > **[!UICONTROL 일반]** > **[!UICONTROL 구성 브라우저]**&#x200B;로 이동합니다.

   ![클라우드 구성 컨테이너](/help/edge/docs/forms/universal-editor/assets/recaptcha-general-configuration.png)

1. **[!UICONTROL 구성 브라우저]**&#x200B;에서 양식으로 이동하여 **[!UICONTROL 속성]**&#x200B;을 선택합니다.

   ![클라우드 구성 속성](/help/edge/docs/forms/universal-editor/assets/general-configuration-properties.png)

1. **[!UICONTROL 구성 속성]** 대화 상자에서 **[!UICONTROL 클라우드 구성]**&#x200B;을 활성화합니다.

1. **[!UICONTROL 저장 및 닫기]**&#x200B;를 선택하여 구성을 저장하고 대화 상자를 종료합니다.

   ![클라우드 구성 속성 활성화](/help/edge/docs/forms/universal-editor/assets/enable-cloud-configurations.png)

   클라우드 구성 컨테이너를 만든 후 게시합니다.

   ![클라우드 구성 게시](/help/edge/docs/forms/universal-editor/assets/publish-cloud-configuration.png)

#### 2. reCAPTCHA에 대한 클라우드 서비스 구성 만들기

reCAPTCHA에 대한 클라우드 서비스 구성을 만들려면 다음 단계를 수행합니다.

1. 작성자 인스턴스에 로그인합니다.
1. **[!UICONTROL 도구]** ![tools-1](/help/forms/assets/tools-1.png) > **[!UICONTROL 클라우드 서비스]** > **[!UICONTROL reCAPTCHA]**&#x200B;로 이동합니다.

   ![Recaptcha 클라우드 구성](/help/edge/docs/forms/universal-editor/assets/recaptcha-cloud-configuration.png)

   **구성** 대화 상자가 열립니다.

1. 양식으로 이동하여 **[!UICONTROL 만들기]**&#x200B;를 선택합니다.

   ![Captcha 구성](/help/edge/docs/forms/universal-editor/assets/create-captcha-confguration.png)

   **[!UICONTROL reCAPTCHA 구성 만들기]** 대화 상자가 열립니다.

   ![reCaptcha Enterprise](/help/edge/docs/forms/universal-editor/assets/recaptcha.png)

1. [!DNL ReCAPTCHA v2]로 버전을 선택하고 제목과 이름을 지정합니다.
1. 사이트 키와 비밀 키를 지정합니다.

   >[!NOTE]
   >
   > reCAPTCHA의 [시작하기 전에](#before-you-begin) 섹션에서 사이트 키와 비밀 키를 얻을 수 있습니다.

1. **[!UICONTROL 만들기]**&#x200B;를 선택하여 클라우드 서비스 구성을 만듭니다.

   reCAPTCHA 클라우드 구성을 만든 후 게시합니다.

   ![Recaptcha 구성 게시](/help/edge/docs/forms/universal-editor/assets/publisg-recaptcha-configuration.png)

이제 WYSIWYG 기반 작성을 사용하여 양식을 만들고 편집하여 reCAPTCHA 구성 요소를 추가할 수 있습니다. Google reCAPTCHA를 양식에 통합하는 자세한 지침은 [양식에서 reCAPTCHA 사용](#use-recaptcha-in-your-form)을 참조하십시오.

### 양식에서 reCAPTCHA 사용

양식을 작성하고 reCAPTCHA(숨김) 구성 요소를 추가하려면 다음 작업을 수행하십시오.

1. 편집을 위해 범용 편집기에서 양식을 엽니다.
1. 콘텐츠 트리에서 추가된 적응형 양식 섹션으로 이동합니다.
1. **[!UICONTROL 추가]** 아이콘을 클릭하고 **적응형 양식 구성 요소** 목록에서 원하는 **[!UICONTROL Captcha(숨김)]** 구성 요소를 추가합니다.

   ![reCaptcha 구성 요소 추가](/help/edge/docs/forms/universal-editor/assets/add-recaptcha-component.png)

   범용 편집기는 직관적인 드래그 앤 드롭 기능을 제공하므로 필요한 적응형 양식 구성 요소를 바로 끌어다 놓을 수도 있습니다.

1. **Captcha(숨김)** 구성 요소를 추가한 후 양식을 다시 게시하려면 **[!UICONTROL 게시]**&#x200B;를 클릭합니다.

   ![양식 재게시](/help/edge/docs/forms/universal-editor/assets/publish-form.png)

이제 다음 URL에서 reCAPTCHA 서비스를 사용하여 양식을 볼 수 있습니다.
`https://<branch>--<repo>--<owner>.aem.live/content/forms/af/<form-name`.

![reCAPTCHA를 사용한 양식](/help/edge/docs/forms/universal-editor/assets/form-with-recaptcha.png)

## 자주 묻는 질문

* **사용자가 reCAPTCHA 클라우드 구성을 생성하지 않으면 어떻게 됩니까?**

  **답변**: 사용자가 reCAPTCHA 클라우드 구성을 생성하지 않으면 AEM 서버는 글로벌 구성 컨테이너에서 reCAPTCHA 클라우드 구성을 검색합니다. 글로벌 구성 컨테이너에 구성이 없으면 AEM 서버에서 오류가 발생합니다.

* **사용자가 여러 개의 reCAPTCHA 클라우드 구성을 만들면 어떻게 됩니까?**
  **답변**: 사용자가 여러 개의 reCAPTCHA 클라우드 구성을 생성하면 시스템은 자동으로 처음 생성된 reCAPTCHA 구성을 선택합니다.

* **게시된 URL에서 수정 사항이나 변경 사항이 표시되지 않는 이유는 무엇입니까?**
게시된 URL에서 수정 사항이나 변경 사항이 보이지 않는 경우, 업데이트를 적용하기 위해 양식을 다시 게시해야 합니다.

* **Edge Delivery Services 양식은 어떤 reCAPTCHA 서비스를 지원합니까?**
  **답변**: Edge Delivery Services 양식은 Google가 제공하는 점수 기반 reCAPTCHA 서비스만 지원합니다.


## 추가 참조

{{universal-editor-see-also}}

