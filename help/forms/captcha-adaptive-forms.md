---
title: 적응형 Forms에서 CAPTCHA 사용
seo-title: Using CAPTCHA in Adaptive Forms
description: 적응형 Forms에서 AEM CAPTCHA 또는 Google reCAPTCHA 서비스를 구성하는 방법을 알아봅니다.
seo-description: Learn how to configure AEM CAPTCHA or Google reCAPTCHA service in Adaptive Forms.
uuid: 0e11e98a-12ac-484c-b77f-88ebdf0f40e5
contentOwner: vishgupt
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: adaptive_forms, author
discoiquuid: 4c53dfc0-25ca-419d-abfe-cf31fc6ebf61
docset: aem65
exl-id: 3fdbe5a3-5c3c-474d-b701-e0182da4191a
source-git-commit: 7163eb2551f5e644f6d42287a523a7dfc626c1c4
workflow-type: tm+mt
source-wordcount: '1376'
ht-degree: 0%

---

# 적응형 Forms에서 CAPTCHA 사용{#using-captcha-in-adaptive-forms}

CAPTCHA(컴퓨터와 인간을 구분하기 위해 완전히 자동화된 공공 튜링 테스트)는 사람과 자동화된 프로그램 또는 보트를 구별하기 위해 온라인 트랜잭션에 자주 사용되는 프로그램입니다. 과제를 안고 사용자 응답을 평가하여 그것이 사람인지 아니면 사이트와 상호 작용하는 봇인지를 결정합니다. 따라서 테스트가 실패하면 사용자가 진행할 수 없고, 봇이 스팸 또는 악의적인 목적을 게시하지 못하도록 하여 온라인 거래를 안전하게 할 수 있습니다.

[!DNL AEM Forms] 은 응용 Forms에서 CAPTCHA를 지원합니다. Google의 reCAPTCHA 서비스를 사용하여 CAPTCHA를 구현할 수 있습니다.

>[!NOTE]
>
>* [!DNL AEM Forms] reCaptcha v2만 지원합니다. 다른 버전은 지원되지 않습니다.
>* 응용 Forms의 CAPTCHA는 [!DNL AEM Forms] 앱.

>


## Google의 ReCAPTCHA 서비스 구성 {#google-recaptcha}

양식 작성자는 Google의 reCAPTCHA 서비스를 사용하여 적응형 Forms에서 CAPTCHA를 구현할 수 있습니다. 사이트를 보호하기 위한 고급 CAPTCHA 기능을 제공합니다. reCAPTCHA 작동 방식에 대한 자세한 내용은 [Google reCAPTCHA](https://developers.google.com/recaptcha/).

![Recaptcha](assets/recaptcha_new.png)

에서 reCAPTCHA 서비스를 구현하려면 [!DNL AEM Forms]:

1. 획득 [reCAPTCHA API 키 쌍](https://www.google.com/recaptcha/admin) Google에서 가져옵니다. 사이트 키와 암호가 포함되어 있습니다.
1. 클라우드 서비스용 구성 컨테이너를 만듭니다.

   1. 이동 **[!UICONTROL 도구 > 일반 > 구성 브라우저]**.
      * 자세한 내용은 [구성 브라우저](https://experienceleague.adobe.com/docs/experience-manager-65/administering/introduction/configurations.html?lang=en#introduction) 설명서 를 참조하십시오.
   1. 클라우드 구성에 대한 글로벌 폴더를 활성화하려면 다음을 수행하십시오. 또는 이 단계를 건너뛰고 클라우드 서비스 구성에 대한 다른 폴더를 만들고 구성하려면 다음을 수행하십시오.

      1. 구성 브라우저에서 **[!UICONTROL 글로벌]** 폴더 및 탭 **[!UICONTROL 속성]**.

      1. 구성 속성 대화 상자에서 **[!UICONTROL 클라우드 구성]**.
      1. 탭 **[!UICONTROL 저장 및 닫기]** 구성을 저장하고 대화 상자를 종료합니다.
   1. 구성 브라우저에서 **[!UICONTROL 만들기]**.
   1. 구성 만들기 대화 상자에서 폴더의 제목을 지정하고 **[!UICONTROL 클라우드 구성]**.
   1. 탭 **[!UICONTROL 만들기]** 클라우드 서비스 구성에 대해 활성화된 폴더를 만들려면


1. reCAPTCHA에 대한 클라우드 서비스를 구성합니다.

   1. AEM 작성자 인스턴스에서 ![tools-1](assets/tools-1.png) > **[!UICONTROL Cloud Services]**.
   1. 탭 **[!UICONTROL reCAPTCHA]**. 구성 페이지가 열립니다. 이전 단계에서 만든 구성 컨테이너를 선택하고 을(를) 누릅니다 **[!UICONTROL 만들기]**.
   1. reCAPTCHA 서비스의 이름, 사이트 키 및 비밀 키를 지정하고 탭합니다. **[!UICONTROL 만들기]** 클라우드 서비스 구성을 만들려면
   1. 구성 요소 편집 대화 상자에서 1단계에서 얻은 사이트 및 비밀 키를 지정합니다. 탭 **[!UICONTROL 설정 저장]** 그런 다음 **[!UICONTROL 확인]** 구성을 완료합니다.

   reCAPTCHA 서비스가 구성되면 적응형 Forms에서 사용할 수 있습니다. 자세한 내용은 [적응형 Forms에서 CAPTCHA 사용](#using-captcha).

## 적응형 Forms에서 CAPTCHA 사용 {#using-captcha}

응용 Forms에서 CAPTCHA를 사용하려면:

1. 편집 모드에서 적응형 양식을 엽니다.

   >[!NOTE]
   >
   >적응형 양식을 만들 때 선택한 구성 컨테이너에 reCAPTCHA 클라우드 서비스가 포함되어 있는지 확인합니다. 적응형 양식 속성을 편집하여 양식과 연결된 구성 컨테이너를 변경할 수도 있습니다.

1. 구성 요소 브라우저에서 **[!UICONTROL Captcha]** 구성 요소를 적응형 양식에 추가합니다.

   >[!NOTE]
   >
   >적응형 양식에서 두 개 이상의 Captcha 구성 요소를 사용하는 것은 지원되지 않습니다. 또한 지연 로딩으로 표시된 패널 또는 조각에서 CAPTCHA를 사용하지 않는 것이 좋습니다.

   >[!NOTE]
   >
   >Captcha는 시간에 민감하며 약 1분 후에 만료됩니다. 따라서 적응형 양식의 제출 단추 바로 앞에 Captcha 구성 요소를 배치하는 것이 좋습니다.

1. 추가한 Captcha 구성 요소를 선택하고 탭합니다 ![cmppr](assets/configure-icon.svg) 속성을 편집하려면
1. CAPTCHA 위젯의 제목을 지정합니다. 기본값은 입니다. **[!UICONTROL Captcha]**. 선택 **[!UICONTROL 제목 숨기기]** 제목을 표시하지 않으려면
1. 에서 **[!UICONTROL Captcha 서비스]** 드롭다운에서 을 선택합니다. **[!UICONTROL reCaptcha]** reCAPTCHA 서비스를 사용하도록 설정하려면 [Google ReCAPTCHA 서비스](#google-recaptcha). 설정 드롭다운에서 구성을 선택합니다. 또한 크기를 **[!UICONTROL 일반]** 또는 **[!UICONTROL 컴팩트]** reCAPTCHA 위젯용.

   >[!NOTE]
   >
   >선택하지 않음 **[!UICONTROL 기본값]** 기본 AEM CAPTCHA 서비스는 더 이상 사용되지 않으므로 Captcha 서비스 드롭다운에서 제공됩니다.

1. 속성을 저장합니다.

reCAPTCHA 서비스는 적응형 양식에서 활성화됩니다. 양식을 미리 보고 CAPTCHA가 작동하는 것을 볼 수 있습니다.

### 규칙에 따라 CAPTCHA 구성 요소 표시 또는 숨기기 {#show-hide-captcha}

적응형 양식의 구성 요소에 적용하는 규칙에 따라 CAPTCHA 구성 요소를 표시하거나 숨기도록 선택할 수 있습니다. 구성 요소를 탭하고 을 선택합니다. ![규칙 편집](assets/edit-rules-icon.svg), 탭 **[!UICONTROL 만들기]** 규칙을 만들려면 다음을 수행하십시오. 규칙 만들기에 대한 자세한 내용은 [규칙 편집기](rule-editor.md).

예를 들어 양식의 통화 값 필드에 값이 25000 이상인 경우에만 CAPTCHA 구성 요소가 적응형 양식에 표시되어야 합니다.

탭하기 **[!UICONTROL 통화 값]** 필드의 필드를 만들고 다음 규칙을 만듭니다.

![규칙 표시 또는 숨기기](assets/rules-show-hide-captcha.png)

### CAPTCHA 유효성 검사 {#validate-captcha}

양식을 제출할 때 적응형 양식의 CAPTCHA의 유효성을 검사하거나 사용자 작업 및 조건에 따라 CAPTCHA 유효성 검사를 수행할 수 있습니다.

#### 양식 제출 시 CAPTCHA 유효성 검사 {#validation-form-submission}

적응형 양식을 제출할 때 CAPTCHA를 자동으로 확인하려면:

1. CAPTCHA 구성 요소를 탭하고 을(를) 선택합니다 ![cmppr](assets/configure-icon.svg) 구성 요소 속성을 보려면
1. 에서 **[!UICONTROL CAPTCHA 유효성 검사]** 섹션, **[!UICONTROL 양식 제출 시 CAPTCHA 유효성 검사]**.
1. 탭 ![완료](assets/save_icon.svg) 구성 요소 속성을 저장하려면

#### 사용자 작업 및 조건에 대한 CAPTCHA 유효성 검사 {#validate-captcha-user-action}

조건 및 사용자 작업을 기반으로 하여 CAPTCHA의 유효성을 검사하려면 다음을 수행하십시오.

1. CAPTCHA 구성 요소를 탭하고 을(를) 선택합니다 ![cmppr](assets/configure-icon.svg) 구성 요소 속성을 보려면
1. 에서 **[!UICONTROL CAPTCHA 유효성 검사]** 섹션, **[!UICONTROL 사용자 작업에서 CAPTCHA 유효성 검사]**.
1. 탭 ![완료](assets/save_icon.svg) 구성 요소 속성을 저장하려면

[!DNL Experience Manager Forms] 제공 `ValidateCAPTCHA` 사전 정의된 조건을 사용하여 CAPTCHA의 유효성을 검사하는 API입니다. 사용자 지정 제출 작업을 사용하거나 적응형 양식의 구성 요소에 대한 규칙을 정의하여 API를 호출할 수 있습니다.

다음은 의 예입니다 `ValidateCAPTCHA` 사전 정의된 조건을 사용하여 CAPTCHA의 유효성을 검사하는 API:

```javascript
if (slingRequest.getParameter("numericbox1614079614831").length() >= 5) {
    	GuideCaptchaValidatorProvider apiProvider = sling.getService(GuideCaptchaValidatorProvider.class);
        String formPath = slingRequest.getResource().getPath();
        String captchaData = slingRequest.getParameter(GuideConstants.GUIDE_CAPTCHA_DATA);
        if (!apiProvider.validateCAPTCHA(formPath, captchaData).isCaptchaValid()){
            response.setStatus(400);
            return;
        }
    }
```

그 예는 `ValidateCAPTCHA` API는 양식을 채우는 동안 사용자가 지정한 숫자 상자의 자릿수가 5보다 큰 경우에만 양식에서 CAPTCHA의 유효성을 검사합니다.

**옵션 1: 사용 [!DNL Experience Manager Forms] CAPTCHA API의 유효성을 검사하여 사용자 지정 제출 작업을 사용하여 CAPTCHA의 유효성을 검사합니다**

다음 단계를 수행하여 을 사용합니다 `ValidateCAPTCHA` 사용자 지정 제출 작업을 사용하여 CAPTCHA의 유효성을 검사하는 API:

1. 다음을 포함하는 스크립트를 추가합니다 `ValidateCAPTCHA` 사용자 지정 제출 작업에 대한 API. 사용자 지정 제출 작업에 대한 자세한 내용은 [적응형 Forms에 대한 사용자 지정 제출 작업 만들기](custom-submit-action-form.md).
1. 에서 사용자 지정 제출 작업 이름을 선택합니다 **[!UICONTROL 작업 제출]** 의 드롭다운 목록 **[!UICONTROL 제출]** 적응형 양식의 속성입니다.
1. 탭 **[!UICONTROL 제출]**. CAPTCHA는 `ValidateCAPTCHA` 사용자 지정 제출 작업의 API입니다.

**옵션 2: 사용 [!DNL Experience Manager Forms] 양식을 제출하기 전에 사용자 작업에서 CAPTCHA의 유효성을 검사하려면 CAPTCHA API의 유효성을 검사하십시오**

를 호출할 수도 있습니다 `ValidateCAPTCHA` 적응형 양식의 구성 요소에 규칙을 적용하여 API를 만들 수 있습니다.

예를 들어 **[!UICONTROL CAPTCHA 유효성 검사]** 단추를 클릭하여 서비스를 호출하는 규칙을 만듭니다.

다음 그림은 **[!UICONTROL CAPTCHA 유효성 검사]** 버튼:

![CAPTCHA 유효성 검사](assets/captcha-validation1.gif)

을 포함하는 사용자 지정 서블릿을 호출할 수 있습니다 `ValidateCAPTCHA` 규칙 편집기를 사용하여 API를 실행하고 유효성 검사 결과를 기반으로 적응형 양식의 제출 단추를 활성화 또는 비활성화합니다.

마찬가지로 규칙 편집기를 사용하여 사용자 지정 메서드를 포함하여 적응형 양식에 CAPTCHA의 유효성을 검사할 수 있습니다.

### 사용자 지정 CAPTCHA 서비스 추가 {#add-custom-captcha-service}

[!DNL Experience Manager Forms] 는 reCAPTCHA를 CAPTCHA 서비스로 제공합니다. 그러나 사용자 지정 서비스를 추가하여 **[!UICONTROL CAPTCHA 서비스]** 드롭다운 목록.

다음은 적응형 양식에 추가 CAPTCHA 서비스를 추가하기 위한 인터페이스의 샘플 구현입니다.

```javascript
package com.adobe.aemds.guide.service;

import org.osgi.annotation.versioning.ConsumerType;

/**
 * An interface to provide captcha validation at server side in Adaptive Form
 * This interface can be used to provide custom implementation for different captcha services.
 */
@ConsumerType
public interface GuideCaptchaValidator {
    /**
     * This method should define the actual validation logic of the captcha
     * @param captchaPropertyNodePath path to the node with CAPTCHA configurations inside form container
     * @param userResponseToken  The user response token provided by the CAPTCHA from client-side
     *
     * @return  {@link GuideCaptchaValidationResult} validation result of the captcha
     */
     GuideCaptchaValidationResult validateCaptcha(String captchaPropertyNodePath, String userResponseToken);

    /**
     * Returns the name of the captcha validator. This should be unique among the different implementations
     * @return  name of the captcha validator
     */
     String getCaptchaValidatorName();
}
```

`captchaPropertyNodePath` 는 Sling 저장소에 있는 CAPTCHA 구성 요소의 리소스 경로를 나타냅니다. CAPTCHA 구성 요소에 대한 세부 사항을 포함하려면 이 속성을 사용하십시오. 예, `captchaPropertyNodePath` captcha 구성 요소에 구성된 reCAPTCHA 클라우드 구성에 대한 정보를 포함합니다. 클라우드 구성 정보에서는 다음을 제공합니다 **[!UICONTROL 사이트 키]** 및 **[!UICONTROL 비밀 키]** reCAPTCHA 서비스 구현을 위한 설정입니다.

`userResponseToken` 는 `g_recaptcha_response` 이는 CAPTCHA를 양식에서 해결한 후 생성됩니다.

### reCAPTCHA 서비스 도메인 편집 {#recaptcha-service-domain}

reCAPTCHA 서비스 사용 `https://www.recaptcha.net/` 을 기본 도메인으로 설정합니다. 설정할 설정을 수정할 수 있습니다 `https://www.google.com/` 또는 reCAPTCHA 서비스를 로드, 렌더링 및 확인하기 위한 사용자 지정 도메인 이름입니다.

설정 **[!UICONTROL af.cloudservices.recaptcha.domain]** 속성 **[!UICONTROL 적응형 양식 및 대화형 통신 웹 채널 구성]** 지정할 구성 `https://www.google.com/` 또는 기타 모든 사용자 지정 도메인 이름. 다음 JSON 파일에는 샘플이 표시됩니다.

```json
{
  "af.cloudservices.recaptcha.domain": "https://www.google.com/"
}
```

구성 값을 설정하려면 [AEM SDK를 사용하여 OSGi 구성 생성](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/deploying/configuring-osgi.html?lang=en#generating-osgi-configurations-using-the-aem-sdk-quickstart), 및 [구성 배포](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/deploy-code.html?lang=en#deployment-process) Cloud Service 인스턴스에 매핑해야 합니다.
