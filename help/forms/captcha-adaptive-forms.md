---
title: 적응형 Forms에서 CAPTCHA를 사용하는 방법
description: 적응형 양식에 대한 또는 Google reCAPTCHA 서비스를 구성하는 방법에 대해 알아봅니다.
uuid: 0e11e98a-12ac-484c-b77f-88ebdf0f40e5
contentOwner: vishgupt
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: adaptive_forms, author
feature: Adaptive Forms, Foundation Components
exl-id: 3fdbe5a3-5c3c-474d-b701-e0182da4191a
role: User, Developer
source-git-commit: 2b76f1be2dda99c8638deb9633055e71312fbf1e
workflow-type: tm+mt
source-wordcount: '1742'
ht-degree: 10%

---


# 적응형 Forms에서 reCAPTCHA 사용 {#using-reCAPTCHA-in-adaptive-forms}

<span class="preview"> [새 적응형 양식 만들기](/help/forms/creating-adaptive-form-core-components.md) 또는 [AEM Sites 페이지에 적응형 양식 추가](/help/forms/create-or-add-an-adaptive-form-to-aem-sites-page.md) 작업을 할 때 현대적이고 확장 가능한 데이터 캡처 [핵심 구성 요소](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html)를 사용하는 것이 좋습니다. 이러한 구성 요소는 적응형 양식 만들기 작업이 대폭 개선되어 우수한 사용자 경험을 보장할 수 있게 되었음을 나타냅니다. 이 문서에서는 기초 구성 요소를 사용하여 적응형 양식을 작성하는 이전 접근법에 대해 설명합니다. </span>


| 버전 | 문서 링크 |
| -------- | ---------------------------- |
| AEM 6.5 | [여기 클릭](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-basic-authoring/captcha-adaptive-forms.html) |
| AEM as a Cloud Service | 이 문서 |
| 적용 대상 | 기초 구성 요소를 기반으로 하는 적응형 양식입니다. <br> 핵심 구성 요소를 기반으로 하는 적응형 양식에 대해 [여기를 클릭하세요](/help/forms/captcha-adaptive-forms-core-components.md). |


CAPTCHA(컴퓨터와 인간을 구분하기 위해 완전히 자동화된 공공 튜링 테스트)는 인간과 자동화된 프로그램 또는 봇을 구별하기 위해 온라인 거래에서 일반적으로 사용되는 프로그램입니다. 문제를 제기하고 사용자 응답을 평가하여 사이트와 상호 작용하는 것이 인간인지 봇인지 판단합니다. 테스트가 실패할 경우 사용자가 진행하지 못하도록 차단하고 봇이 스팸을 게시하거나 악의적인 목적으로 상호 작용하는 것을 방지하여 온라인 거래를 안전하게 할 수 있도록 도와줍니다.

AEM Formsas a Cloud Service 에서 CAPTCHA 솔루션을 지원합니다.

* [Google recaptcha](#configure-recaptcha-service-by-google)
* [Cloudflare 턴스타일](/help/forms/integrate-adaptive-forms-turnstile.md)
* [hCaptcha](/help/forms/integrate-adaptive-forms-hcaptcha.md)

## Google에서 reCAPTCHA 서비스 구성 {#google-reCAPTCHA}

양식 작성자는 Google의 reCAPTCHA 서비스를 사용하여 적응형 Forms에서 reCAPTCHA를 구현할 수 있습니다. 사이트 보호를 위한 고급 CAPTCHA 기능을 제공합니다. reCAPTCHA 작동 방식에 대한 자세한 내용은 [Google reCAPTCHA](https://developers.google.com/recaptcha/)을(를) 참조하십시오. AEM Forms은 [!DNL reCAPTCHA v2] 및 [!DNL reCAPTCHA Enterprise]을(를) 지원합니다. 다른 버전은 지원되지 않습니다. 또한 응용 Forms의 reCAPTCHA는 [!DNL AEM Forms] 앱의 오프라인 모드에서 지원되지 않습니다. 요구 사항에 따라 reCAPTCHA 서비스를 구성하여 다음을 활성화할 수 있습니다.

![reCAPTCHA](/help/forms/assets/recaptcha_new.png)

* [AEM Forms의 reCAPTCHA Enterprise](#steps-to-implement-reCAPTCHA-enterprise-in-forms)
* [AEM Forms의 reCAPTCHA v2](#steps-to-implement-reCAPTCHA-v2-in-forms)


### reCAPTCHA Enterprise 구성  {#steps-to-implement-reCAPTCHA-enterprise-in-forms}

1. [Google Cloud 프로젝트](https://cloud.google.com/recaptcha-enterprise/docs/set-up-non-google-cloud-environments-api-keys#before-you-begin)를 만들거나 선택하고 [reCAPTCHA Enterprise API](https://cloud.google.com/recaptcha-enterprise/docs/set-up-non-google-cloud-environments-api-keys#enable-the-recaptcha-enterprise-api)를 활성화하십시오.
1. [프로젝트 ID](https://support.google.com/googleapi/answer/7014113?hl=en#:~:text=To%20locate%20your%20project%20ID,a%20member%20of%20are%20displayed)를 가져오고 [API 키](https://cloud.google.com/recaptcha-enterprise/docs/set-up-non-google-cloud-environments-api-keys#create_an_api_key) 및 웹 사이트에 대한 [사이트 키](https://cloud.google.com/recaptcha-enterprise/docs/create-key#create-key)를 만듭니다.
1. 클라우드 서비스에 대한 구성 컨테이너를 만듭니다.

   1. **[!UICONTROL 도구 > 일반 > 구성 브라우저]**&#x200B;로 이동합니다.
   1. 폴더를 선택하거나 폴더를 만들고 다음 단계를 사용하여 클라우드 구성에 대해 폴더를 활성화하십시오.
      1. 구성 브라우저에서 폴더를 선택하고 **[!UICONTROL 속성]**&#x200B;을 선택합니다.
      1. 구성 속성 대화 상자에서 **[!UICONTROL 클라우드 구성]**&#x200B;을 사용하도록 설정합니다.
      1. 구성을 저장하고 대화 상자를 종료하려면 **[!UICONTROL 저장 및 닫기]**&#x200B;를 선택하십시오.

1. [!DNL reCAPTCHA Enterprise]에 대한 클라우드 서비스를 구성하십시오.

   1. Experience Manager 작성자 인스턴스에서 ![도구-1](assets/tools-1.png) > **[!UICONTROL Cloud Service]**(으)로 이동합니다.
   1. **[!UICONTROL reCAPTCHA]**&#x200B;을(를) 선택합니다. Configurations 페이지가 열립니다. 만든 구성 컨테이너를 선택하고 **[!UICONTROL 만들기]**&#x200B;를 선택합니다.
   1. 버전을 [!DNL reCAPTCHA Enterprise](으)로 선택하고 이름, 프로젝트 ID, 사이트 키 및 reCAPTCHA Enterprise 서비스에 대한 API 키(2단계에서 획득)를 지정합니다.
   1. 키 유형을 선택하십시오. 키 유형은 [Google Cloud 프로젝트](https://cloud.google.com/recaptcha-enterprise/docs/set-up-non-google-cloud-environments-api-keys#before-you-begin)에서 구성한 사이트 키와 동일해야 합니다(예: **확인란 사이트 키** 또는 **점수 기반 사이트 키**).
   1. 0에서 1](https://cloud.google.com/recaptcha-enterprise/docs/interpret-assessment#interpret_scores) 사이의 [임계값 점수를 지정하십시오. 임계값 점수보다 크거나 같은 점수는 인간 상호 작용을 식별하고, 그렇지 않으면 봇 상호 작용으로 간주됩니다.
   1. 클라우드 서비스 구성을 만들려면 **[!UICONTROL 만들기]**&#x200B;를 선택하십시오.

<!--
    1. In the Edit Component dialog, specify the name, project ID, site key, API key (obtained in steps 2 and 3), select the key type, and enter the threshold score. Select **[!UICONTROL Save Settings]** and then select **[!UICONTROL OK]** to complete the configuration.
-->

reCAPTCHA Enterprise 서비스가 활성화되면 적응형 양식에서 사용할 수 있습니다. [적응형 양식에서 CAPTCHA 사용](#using-reCAPTCHA)을 참조하세요.

<!--
![reCAPTCHA Enterprise](/help/forms/assets/recaptcha1-enterprise.png)
-->

### Google reCAPTCHA v2 구성 {#steps-to-implement-reCAPTCHA-v2-in-forms}

1. Google에서 [reCAPTCHA API 키 쌍](https://www.google.com/recaptcha/admin)을(를) 가져옵니다. 여기에는 **사이트 키** 및 **암호 키**&#x200B;가 포함됩니다.
1. 클라우드 서비스에 대한 구성 컨테이너를 만듭니다.
   1. **[!UICONTROL 도구 > 일반 > 구성 브라우저]**&#x200B;로 이동합니다.
   1. 폴더를 선택하거나 폴더를 만들고 다음 단계를 사용하여 클라우드 구성에 대해 폴더를 활성화하십시오.
      1. 구성 브라우저에서 폴더를 선택하고 **[!UICONTROL 속성]**&#x200B;을 선택합니다.
      1. 구성 속성 대화 상자에서 **[!UICONTROL 클라우드 구성]**&#x200B;을 사용하도록 설정합니다.
      1. 구성을 저장하고 대화 상자를 종료하려면 **[!UICONTROL 저장 및 닫기]**&#x200B;를 선택하십시오.

1. reCAPTCHA v2에 대한 클라우드 서비스를 구성합니다.

   1. AEM 작성자 인스턴스에서 ![도구-1](assets/tools-1.png) > **Cloud Service**(으)로 이동합니다.
   1. **[!UICONTROL reCAPTCHA]**&#x200B;을(를) 선택합니다. Configurations 페이지가 열립니다. 만든 구성 컨테이너를 선택하고 **[!UICONTROL 만들기]**&#x200B;를 선택합니다.
   1. [!DNL reCAPTCHA v2](으)로 버전을 선택하고 reCAPTCHA 서비스(1단계에서 획득)에 대한 이름, 사이트 키 및 비밀 키를 지정한 다음 **[!UICONTROL 만들기]**&#x200B;를 선택하여 클라우드 서비스 구성을 만듭니다.
   1. 구성 요소 편집 대화 상자에서 1단계에서 얻은 사이트 및 비밀 키를 지정합니다. **[!UICONTROL 설정 저장]**&#x200B;을 선택한 다음 **확인**&#x200B;을 선택하여 구성을 완료합니다.

   reCAPTCHA 서비스가 구성되면 적응형 양식에서 사용할 수 있습니다. 자세한 내용은 [적응형 양식에서 CAPTCHA 사용](#using-reCAPTCHA)을 참조하세요.

<!--![reCAPTCHA v2](/help/forms/assets/recaptcha-v2.png)-->


## 적응형 양식에서 Google reCAPTCHA 사용 {#using-reCAPTCHA}

적응형 양식에서 Google reCAPTCHA를 사용하려면 다음 작업을 수행하십시오.

1. 편집 모드에서 적응형 양식을 엽니다.

   >[!NOTE]
   >
   >적응형 양식을 만들 때 선택한 구성 컨테이너에 reCAPTCHA 클라우드 서비스가 포함되어 있는지 확인합니다. 적응형 양식 속성을 편집하여 양식과 관련된 구성 컨테이너를 변경할 수도 있습니다.

1. 구성 요소 브라우저에서 **Captcha** 구성 요소를 적응형 양식으로 드래그 앤 드롭합니다.

   >[!NOTE]
   >
   >* 적응형 양식에서 Captcha 구성 요소를 두 개 이상 사용하는 것은 지원되지 않습니다. 또한 소극적 로드로 표시된 패널 또는 조각에서는 CAPTCHA를 사용하지 않는 것이 좋습니다.
   >* reCaptcha는 시간에 민감하며 약 2~3분 후에 만료됩니다. 따라서 적응형 양식에서 Captcha 구성 요소를 제출 단추 바로 앞에 배치하는 것이 좋습니다.

1. 추가한 Captcha 구성 요소를 선택하고 ![cmppr](assets/cmppr.png)을(를) 선택하여 해당 속성을 편집합니다.
1. CAPTCHA 위젯의 제목을 지정합니다. 기본값은 **Captcha**&#x200B;입니다. 제목을 표시하지 않으려면 **제목 숨기기**&#x200B;를 선택하십시오.
1. Google의 [reCAPTCHA 서비스](#google-reCAPTCHA)에 설명된 대로 구성한 경우 **Captcha 서비스** 드롭다운에서 **reCAPTCHA**&#x200B;을(를) 선택하여 reCAPTCHA 서비스를 활성화하십시오.
1. 설정 드롭다운에서 **reCAPTCHA Enterprise** 또는 **reCAPTCHA v2**&#x200B;에 대한 구성을 선택하십시오.
   1. **reCAPTCHA Enterprise** 버전을 선택하는 경우 키 유형은 **확인란** 또는 **점수 기반**&#x200B;일 수 있습니다. [웹 사이트에 대한 사이트 키](https://cloud.google.com/recaptcha-enterprise/docs/create-key#create-key)를 구성할 때 선택한 항목에 따라 다릅니다.

   >[!NOTE]
   >
   >* **키 유형**&#x200B;이(가) **checkbox**(으)로 설정된 클라우드 구성에서 captcha 유효성 검사에 실패하면 사용자 지정된 오류 메시지가 인라인 메시지로 표시됩니다.
   >* **키 형식**&#x200B;이 **점수 기반**&#x200B;인 클라우드 구성에서 captcha 유효성 검사에 실패하면 사용자 지정된 오류 메시지가 팝업 메시지로 표시됩니다.

   1. 크기를 **[!UICONTROL 보통]** 및 **[!UICONTROL 작게]**&#x200B;로 선택할 수 있습니다.
   1. **[!UICONTROL 바인드 참조]**&#x200B;를 선택할 수 있습니다. **[!UICONTROL 바인드 참조]**&#x200B;에서 제출된 데이터는 바인딩된 데이터이고, 그렇지 않으면 바인딩되지 않은 데이터입니다. 다음은 양식 제출 시 바인딩되지 않은 데이터와 바인딩된 데이터(바인드 참조를 SSN으로 사용)의 XML 예입니다.

   ```xml
           <?xml version="1.0" encoding="UTF-8" standalone="no"?>
           <afData>
           <afUnboundData>
               <data>
                   <captcha16820607953761>
                       <captchaType>reCaptchaEnterprise</captchaType>
                       <captchaScore>0.9</captchaScore>
                   </captcha16820607953761>
               </data>
           </afUnboundData>
           <afBoundData>
               <Root
                   xmlns:xfa="http://www.xfa.org/schema/xfa-data/1.0/"
                   xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
                   <PersonalDetails>
                       <SSN>371237912</SSN>
                       <FirstName>Sarah </FirstName>
                       <LastName>Smith</LastName>
                   </PersonalDetails>
                   <OtherInfo>
                       <City>California</City>
                       <Address>54 Residency</Address>
                       <State>USA</State>
                       <Zip>123112</Zip>
                   </OtherInfo>
               </Root>
           </afBoundData>
           <afSubmissionInfo>
               <stateOverrides/>
               <signers/>
               <afPath>/content/dam/formsanddocuments/captcha-form</afPath>
               <afSubmissionTime>20230608034928</afSubmissionTime>
           </afSubmissionInfo>
           </afData>
   ```

   ```xml
           <?xml version="1.0" encoding="UTF-8" standalone="no"?>
           <afData>
           <afUnboundData>
               <data/>
           </afUnboundData>
           <afBoundData>
               <Root
                   xmlns:xfa="http://www.xfa.org/schema/xfa-data/1.0/"
                   xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
                   <PersonalDetails>
                       <SSN>
                           <captchaType>reCaptchaEnterprise</captchaType>
                           <captchaScore>0.9</captchaScore>
                       </SSN>
                       <FirstName>Sarah</FirstName>
                       <LastName>Smith</LastName>
                   </PersonalDetails>
                   <OtherInfo>
                       <City>California</City>
                       <Address>54 Residency</Address>
                       <State>USA</State>
                       <Zip>123112</Zip>
                   </OtherInfo>
               </Root>
           </afBoundData>
           <afSubmissionInfo>
               <stateOverrides/>
               <signers/>
               <afPath>/content/dam/formsanddocuments/captcha-form</afPath>
               <afSubmissionTime>20230608035111</afSubmissionTime>
           </afSubmissionInfo>
           </afData>
   ```

   **reCAPTCHA v2** 버전을 선택하는 경우:
   1. reCAPTCHA 위젯의 크기를 **[!UICONTROL 보통]** 또는 **[!UICONTROL 작게]**(으)로 선택할 수 있습니다.
   1. 의심되는 활동이 있는 경우에만 **[!UICONTROL 보이지 않음]** 옵션을 선택하여 CAPTCHA 문제를 표시할 수 있습니다.

   reCAPTCHA 서비스가 적응형 양식에서 활성화됩니다. 양식을 미리 보고 CAPTCHA가 작동하는 것을 볼 수 있습니다. 아래에 표시된 **reCAPTCHA로 보호** 배지가 보호된 양식에 표시됩니다.
   ![reCAPTCHA 배지로 보호된 Google](/help/forms/assets/google-recaptcha-v2.png)

1. 속성을 저장합니다.

>[!NOTE]
> 
> 기본 AEM CAPTCHA 서비스가 더 이상 사용되지 않으므로 CAPTCHA 서비스 드롭다운에서 **[!UICONTROL Default]**&#x200B;을(를) 선택하지 마십시오.

>[!VIDEO](https://video.tv.adobe.com/v/3422641/recaptcha-google-adaptive-forms/?quality=12&learn=on)

### 규칙에 따라 CAPTCHA 구성 요소 표시 또는 숨기기 {#show-hide-captcha}

적응형 양식의 구성 요소에 적용하는 규칙에 따라 CAPTCHA 구성 요소를 표시하거나 숨기도록 선택할 수 있습니다. 구성 요소를 선택하고 ![규칙 편집](assets/edit-rules-icon.svg)을 선택한 다음 **[!UICONTROL 만들기]**&#x200B;를 선택하여 규칙을 만듭니다. 규칙 만들기에 대한 자세한 내용은 [규칙 편집기](rule-editor.md)를 참조하십시오.

예를 들어 CAPTCHA 구성 요소는 양식의 통화 값 필드에 25000보다 큰 값이 있는 경우에만 적응형 양식에 표시해야 합니다.

양식에서 **[!UICONTROL 통화 값]** 필드를 선택하고 다음 규칙을 만듭니다.

![규칙 표시 또는 숨기기](assets/rules-show-hide-captcha.png)

>[!NOTE]
>
> reCAPTCHA v2 구성을 선택하고 크기가 [!UICONTROL 보이지 않음](으)로 설정된 경우 표시/숨기기 옵션이 비활성화됩니다.

### CAPTCHA 유효성 검사 {#validate-captcha}

양식을 제출하거나 사용자 작업 및 조건에 대한 CAPTCHA 유효성 검사의 기초가 될 때 적응형 양식에서 CAPTCHA의 유효성을 검사할 수 있습니다.

#### 양식 제출 시 CAPTCHA 유효성 검사 {#validation-form-submission}

적응형 양식을 제출할 때 CAPTCHA의 유효성을 자동으로 검사하려면 다음 작업을 수행하십시오.

1. CAPTCHA 구성 요소를 선택하고 ![cmpr](assets/configure-icon.svg)을(를) 선택하여 구성 요소 속성을 확인합니다.
1. **[!UICONTROL CAPTCHA 유효성 검사]** 섹션에서 **[!UICONTROL 양식 제출로 CAPTCHA 유효성 검사]**&#x200B;를 선택합니다.
1. 구성 요소 속성을 저장하려면 ![완료](assets/save_icon.svg)를 선택하십시오.

#### 사용자 작업 및 조건에 대한 CAPTCHA 유효성 검사 {#validate-captcha-user-action}

조건 및 사용자 작업을 기반으로 CAPTCHA의 유효성을 검사하려면 다음을 수행하십시오.

1. CAPTCHA 구성 요소를 선택하고 ![cmpr](assets/configure-icon.svg)을(를) 선택하여 구성 요소 속성을 확인합니다.
1. **[!UICONTROL CAPTCHA 유효성 검사]** 섹션에서 **[!UICONTROL 사용자 작업에 대한 CAPTCHA 유효성 검사]**&#x200B;를 선택합니다.
1. 구성 요소 속성을 저장하려면 ![완료](assets/save_icon.svg)를 선택하십시오.

[!DNL Experience Manager Forms]은(는) 사전 정의된 조건을 사용하여 CAPTCHA의 유효성을 검사하는 `ValidateCAPTCHA` API를 제공합니다. 사용자 지정 제출 액션을 사용하거나 적응형 양식의 구성 요소에 대한 규칙을 정의하여 API를 호출할 수 있습니다.

다음은 사전 정의된 조건을 사용하여 CAPTCHA의 유효성을 검사하기 위한 `ValidateCAPTCHA` API의 예입니다.

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

이 예제는 양식을 채우는 동안 사용자가 지정한 숫자 상자의 자릿수가 5보다 큰 경우에만 `ValidateCAPTCHA` API가 양식의 CAPTCHA를 확인함을 의미합니다.

**옵션 1: [!DNL Experience Manager Forms] ValidateCAPTCHA API를 사용하여 사용자 지정 제출 액션을 사용하여 CAPTCHA의 유효성을 검사합니다**

사용자 지정 제출 액션을 사용하여 `ValidateCAPTCHA` API를 사용하여 CAPTCHA의 유효성을 검사하려면 다음 단계를 수행하십시오.

1. 사용자 지정 제출 액션에 `ValidateCAPTCHA` API를 포함하는 스크립트를 추가합니다. 사용자 지정 제출 액션에 대한 자세한 내용은 [적응형 Forms에 대한 사용자 지정 제출 액션 만들기](custom-submit-action-form.md)를 참조하십시오.
1. 적응형 양식의 **[!UICONTROL 제출]** 속성에 있는 **[!UICONTROL 제출 액션]** 드롭다운 목록에서 사용자 지정 제출 액션의 이름을 선택합니다.
1. **[!UICONTROL 제출]**&#x200B;을 선택합니다. 사용자 지정 제출 액션의 `ValidateCAPTCHA` API에 정의된 조건을 기반으로 CAPTCHA의 유효성을 검사합니다.

**옵션 2: 양식을 제출하기 전에 사용자 작업에서 [!DNL Experience Manager Forms] ValidateCAPTCHA API를 사용하여 CAPTCHA의 유효성을 검사하십시오**

적응형 양식의 구성 요소에 규칙을 적용하여 `ValidateCAPTCHA` API를 호출할 수도 있습니다.

예를 들어 적응형 양식에 **[!UICONTROL CAPTCHA 유효성 검사]** 단추를 추가하고 단추 클릭 시 서비스를 호출하는 규칙을 만듭니다.

다음 그림은 **[!UICONTROL CAPTCHA 유효성 검사]** 단추를 클릭할 때 서비스를 호출하는 방법을 보여 줍니다.

![CAPTCHA 유효성 검사](assets/captcha-validation1.gif)

규칙 편집기를 사용하여 `ValidateCAPTCHA` API를 포함하는 사용자 지정 서블릿을 호출하고 유효성 검사 결과에 따라 적응형 양식의 제출 단추를 활성화하거나 비활성화할 수 있습니다.

마찬가지로 규칙 편집기를 사용하여 적응형 양식에서 CAPTCHA의 유효성을 검사하는 사용자 지정 방법을 포함할 수 있습니다.

<!--

### Add custom CAPTCHA services {#add-custom-captcha-service}

[!DNL Experience Manager Forms] provides reCAPTCHA as the CAPTCHA service. However, you can add a custom service to display in the **[!UICONTROL CAPTCHA Service]** drop-down list.  

The following is a sample implementation of the interface to add additional CAPTCHA service to your Adaptive Form:

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

`captchaPropertyNodePath` refers to the resource path of the CAPTCHA component in the Sling repository. Use this property to include details specific to the CAPTCHA component. For example, `captchaPropertyNodePath` includes information for the reCAPTCHA cloud configuration configured on the CAPTCHA component. The cloud configuration information provides **[!UICONTROL Site Key]** and **[!UICONTROL Secret Key]** settings for implementing the reCAPTCHA service.

`userResponseToken` refers to the `g_recaptcha_response` that gets generated after solving a CAPTCHA in a form. -->

### reCAPTCHA 서비스 도메인 편집 {#reCAPTCHA-service-domain}

reCAPTCHA 서비스는 `https://www.recaptcha.net/`을(를) 기본 도메인으로 사용합니다. reCAPTCHA 서비스 로드, 렌더링 및 유효성 검사를 위해 `https://www.google.com/` 또는 사용자 지정 도메인 이름을 설정하도록 설정을 수정할 수 있습니다.

**[!UICONTROL 적응형 양식 및 대화형 통신 웹 채널 구성]** 구성의 **[!UICONTROL af.cloudservices.recaptcha.domain]** 속성을 설정하여 `https://www.google.com/` 또는 기타 사용자 지정 도메인 이름을 지정하십시오. 다음 JSON 파일에는 샘플이 표시됩니다.

```json
{
  "af.cloudservices.recaptcha.domain": "https://www.google.com/"
}
```

구성의 값을 설정하려면 [AEM SDK를 사용하여 OSGi 구성을 생성](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/deploying/configuring-osgi.html?lang=ko#generating-osgi-configurations-using-the-aem-sdk-quickstart)하고 Cloud Service 인스턴스에 [구성을 배포](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/deploy-code.html?lang=ko#deployment-process)합니다.

## 추가 참조 {#see-also}

{{see-also}}

<!--

>[!MORELIKETHIS]
>
>* [Reference Themes, Templates, and Form Data models for Adaptive Forms](/help/forms/reference-themes-templates-data-models.md)

-->
