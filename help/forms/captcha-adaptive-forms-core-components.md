---
title: AEM 적응형 양식에서 Google reCAPTCHA를 사용하는 방법
description: Google reCAPTCHA 서비스를 통해 손쉽게 양식 보안을 강화할 수 있습니다. 단계별 안내서가 포함되어 있습니다.
topic-tags: Adaptive Forms, author
keywords: Google reCAPTCHA 서비스, 적응형 Forms, CAPTCHA 과제, 보트 방지, 핵심 구성 요소, 양식 제출 보안, 양식 스팸 방지
feature: Adaptive Forms, Core Components
exl-id: d116f979-efb6-4fac-8202-89afd1037b2c
role: User, Developer
source-git-commit: 2b76f1be2dda99c8638deb9633055e71312fbf1e
workflow-type: tm+mt
source-wordcount: '939'
ht-degree: 11%

---

# 핵심 구성 요소를 기반으로 하는 AEM 적응형 양식에서 Google reCAPTCHA 사용 {#using-reCAPTCHA-in-adaptive-forms}

| 적용 대상 | 문서 링크 |
| -------- | ---------------------------- |
| 핵심 구성 요소를 기반으로 하는 적응형 양식 | 이 문서 |
| 기초 구성 요소를 기반으로 하는 적응형 양식 | [여기 클릭](/help/forms/captcha-adaptive-forms.md) |

CAPTCHA(컴퓨터와 인간을 구분하기 위해 완전히 자동화된 공공 튜링 테스트)는 인간과 자동화된 프로그램 또는 봇을 구별하기 위해 온라인 거래에서 일반적으로 사용되는 프로그램입니다. 문제를 제기하고 사용자 응답을 평가하여 사이트와 상호 작용하는 것이 인간인지 봇인지 판단합니다. 테스트가 실패할 경우 사용자가 진행하지 못하도록 차단하고 봇이 스팸을 게시하거나 악의적인 목적으로 상호 작용하는 것을 방지하여 온라인 거래를 안전하게 할 수 있도록 도와줍니다.

AEM Formsas a Cloud Service 에서 CAPTCHA 솔루션을 지원합니다.

* [Google recaptcha](#connect-your-aem-forms-environment-with-recaptcha-service-by-google)
* [Cloudflare 턴스타일](/help/forms/integrate-adaptive-forms-turnstile-core-components.md)
* [hCaptcha](/help/forms/integrate-adaptive-forms-hcaptcha-core-components.md)


## Google의 reCAPTCHA 서비스를 사용하여 AEM Forms 환경 연결 {#connect-your-forms-environment-with-recaptcha-service-by-google}

양식 작성자는 Google의 reCAPTCHA 서비스를 사용하여 적응형 Forms에서 reCAPTCHA를 구현할 수 있습니다. 사이트 보호를 위한 고급 CAPTCHA 기능을 제공합니다. reCAPTCHA 작동 방식에 대한 자세한 내용은 [Google reCAPTCHA](https://developers.google.com/recaptcha/)을(를) 참조하십시오. [!DNL AEM Forms] as a [!DNL Cloud Service]은(는) 적응형 Forms에서 Google reCAPTCHA v2를 지원합니다. 양식 제출에 CAPTCHA 문제를 제시하는 데 사용할 수 있습니다. Google의 reCAPTCHA 서비스를 사용하여 AEM Forms 환경을 연결하려면

1. Google에서 [reCAPTCHA API 키 쌍](https://www.google.com/recaptcha/admin)을(를) 가져옵니다. 여기에는 **사이트 키** 및 **암호 키**&#x200B;가 포함됩니다.

   ![reCAPTCHA 키를 가져오기 위해 Google 웹 사이트의 Google reCAPTCHA 구성을 만듭니다](/help/forms/assets/google-captcha.gif)
1. AEM Forms as a Cloud Service 환경에서 컨테이너 를 만듭니다. 구성 컨테이너에는 AEM을 외부 서비스에 연결하는 데 사용되는 클라우드 구성이 포함됩니다. Google에서 제공하는 reCAPTCHA 서비스를 사용하여 AEM Forms 환경을 연결할 수 있도록 구성 컨테이너를 만들고 구성하려면 다음 작업을 수행하십시오.
   1. AEM Forms as a Cloud Service 인스턴스를 엽니다.
   1. **[!UICONTROL 도구 > 일반 > 구성 브라우저로 이동합니다]**. 구성 브라우저에서 다음 작업을 수행할 수 있습니다.
   1. 기존 폴더를 선택하거나 폴더를 만듭니다. 폴더를 만들고 이 폴더에 대해 클라우드 구성 옵션을 활성화하거나 기존 폴더에 대해 클라우드 구성 옵션을 활성화할 수 있습니다.

      * 폴더를 만들고 이 폴더에 대한 클라우드 구성 옵션을 활성화하려면 다음을 수행하십시오.
         1. 구성 브라우저에서 **[!UICONTROL 만들기]**&#x200B;를 클릭합니다.
         1. 구성 만들기 대화 상자에서 이름, 제목을 지정하고 **[!UICONTROL 클라우드 구성]** 옵션을 선택합니다.
         1. **[!UICONTROL 만들기]**&#x200B;를 클릭합니다.
      * 기존 폴더에 대해 클라우드 구성 옵션을 활성화하려면 다음을 수행하십시오.
         1. 구성 브라우저에서 폴더를 선택하고 **[!UICONTROL 속성]**&#x200B;을 선택합니다.
         1. 구성 속성 대화 상자에서 **[!UICONTROL 클라우드 구성]**&#x200B;을 사용하도록 설정합니다.
         1. 구성을 저장하고 대화 상자를 종료하려면 **[!UICONTROL 저장 및 닫기]**&#x200B;를 선택하십시오.

1. Cloud Service 구성:
   1. AEM 작성자 인스턴스에서 ![tools-1](assets/tools-1.png) > **[!UICONTROL Cloud Service]**(으)로 이동하여 **[!UICONTROL reCAPTCHA]**&#x200B;를 선택합니다.
   1. 이전 섹션에서 만들거나 업데이트한 구성 컨테이너를 선택합니다. **[!UICONTROL 만들기]**&#x200B;를 선택합니다.
   1. reCAPTCHA 서비스(1단계에서 획득)에 대해 **[!UICONTROL 제목]**, **[!UICONTROL 이름]**, **[!UICONTROL 사이트 키]** 및 **[!UICONTROL 비밀 키]**&#x200B;를 지정하십시오. **[!UICONTROL 만들기]**&#x200B;를 선택합니다.

   ![Google의 reCAPTCHA 서비스를 사용하여 AEM Forms 환경을 연결하도록 Cloud Service 구성](/help/forms/assets/captcha-configuration.gif)

   reCAPTCHA 서비스가 구성되면 적응형 양식에서 사용할 수 있습니다. 자세한 내용은 [적응형 양식에서 Google reCAPTCHA 사용](#using-reCAPTCHA)을 참조하십시오.

## 적응형 양식에서 Google reCAPTCHA 사용 {#using-reCAPTCHA}

적응형 Forms에서 reCAPTCHA를 사용하려면:

1. AEM Forms as a Cloud Service 인스턴스를 엽니다.
1. **[!UICONTROL Forms]** > **[!UICONTROL Forms 및 문서]**&#x200B;로 이동합니다.
1. 적응형 Forms을 선택하고 **[!UICONTROL 속성]**&#x200B;을 선택합니다. **[!UICONTROL 구성 컨테이너]** 옵션의 경우 AEM Forms과 Google의 reCAPTCHA 서비스를 연결하는 클라우드 구성이 포함된 구성 컨테이너를 선택하고 **[!UICONTROL 저장 및 닫기]**&#x200B;를 선택합니다.

   이러한 구성 컨테이너가 없는 경우 섹션 [Google의 reCAPTCHA 서비스와 AEM Forms 환경 연결](#connect-your-forms-environment-with-recaptcha-service-by-google)을 참조하여 이러한 구성 컨테이너를 만드는 방법을 알아보십시오.

   ![구성 컨테이너 선택](/help/forms/assets/captcha-properties.png)

1. 적응형 Forms을 선택하고 **[!UICONTROL 편집]**&#x200B;을 선택합니다. 적응형 양식이 적응형 Forms 편집기에서 열립니다.
1. 구성 요소 브라우저에서 **[!UICONTROL 적응형 양식 reCAPTCHA]** 구성 요소를 적응형 양식으로 드래그 앤 드롭합니다.

   Google reCAPTCHA 유효성 검사는 시간에 민감하며 약 2분 후에 만료됩니다. Adobe 따라서 **[!UICONTROL 제출]** 단추 바로 앞에 **[!UICONTROL 적응형 양식 reCAPTCHA]** 구성 요소를 배치하는 것이 좋습니다.

1. **[!UICONTROL 적응형 양식 reCAPTCHA]** 구성 요소를 선택하고 속성 ![속성 아이콘](assets/configure-icon.svg) 아이콘을 선택합니다. 속성 대화 상자가 열립니다. 다음 필수 속성을 지정합니다.
   * **[!UICONTROL 이름]:** 양식과 규칙 편집기에서 고유한 이름으로 양식 구성 요소를 쉽게 식별할 수 있지만 이름에는 공백이나 특수 문자를 사용할 수 없습니다.
   * **[!UICONTROL CAPTCHA 구성]:** 양식에 대한 Google reCAPTCHA 대화 상자를 제공하도록 구성된 클라우드 구성을 선택합니다. 유사한 목적으로 환경에 여러 클라우드 구성이 있을 수 있습니다. 그러므로, 서비스를 신중하게 선택하십시오. 서비스가 목록에 없으면 [Google의 AEM Forms 환경과 reCAPTCHA 서비스 연결](#connect-your-forms-environment-with-recaptcha-service-by-google)을 참조하여 AEM Forms 환경과 Google의 reCAPTCHA 서비스를 연결하는 Cloud Service을 만드는 방법을 알아보십시오.
   * **CAPTCHA 크기:** Google reCAPTCHA 챌린지 대화 상자의 표시 크기를 선택할 수 있습니다. 작은 크기를 표시하려면 **[!UICONTROL Compact]** 옵션을 사용하고, 비교적 큰 크기의 Google reCAPTCHA 문제 대화 상자를 표시하려면 **[!UICONTROL Normal]** 옵션을 사용하십시오.

1. **[!UICONTROL 완료]**&#x200B;를 선택합니다.

   이제 적응형 양식에 **reCAPTCHA로 보호**&#x200B;이(가) 표시됩니다. Google reCAPTCHA 서비스를 사용하도록 구성된 모든 적응형 Forms에 표시됩니다.

   이제 Google reCAPTCHA 서비스에 의해 제기된 문제를 양식 필러가 성공적으로 지운 합법적인 양식만 제출이 허용됩니다.
   ![reCAPTCHA 배지로 보호된 Google](/help/forms/assets/google-recaptcha-v2.png)

<!--
### Show or hide CAPTCHA component based on rules {#show-hide-captcha}

You can select to show or hide the CAPTCHA component based on rules that you apply on a component in an Adaptive Form. Select the component, select ![edit rules](assets/edit-rules-icon.svg), and select **[!UICONTROL Create]** to create a rule. For more information on creating rules, see [Rule Editor](rule-editor.md).

For example, the CAPTCHA component must display in an Adaptive Form only if the Currency Value field in the form has a value of more than 25000.

Select the **[!UICONTROL Currency Value]** field in the form and create the following rules:

![Show or hide rules](assets/rules-show-hide-captcha.png)

   >[!NOTE]
   >
   > When you select a reCAPTCHA v2 configuration and the size is set to [!UICONTROL Invisible], the show/hide option remains disabled.

   -->

## 자주 묻는 질문

**Q: 적응형 양식에 CAPTCHA 구성 요소를 두 개 이상 사용할 수 있습니까?**
**Ans:** 적응형 양식에서 둘 이상의 Captcha 구성 요소를 사용할 수 없습니다. 또한 지연 로드로 표시된 조각 또는 패널에서는 Captcha 구성 요소를 사용하지 않는 것이 좋습니다.

## 추가 참조 {#see-also}

{{see-also}}