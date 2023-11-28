---
title: 적응형 Forms에서 CAPTCHA를 사용하는 방법
description: 적응형 양식에 대한 또는 Google reCAPTCHA 서비스를 구성하는 방법에 대해 알아봅니다.
uuid: 0e11e98a-12ac-484c-b77f-88ebdf0f40e5
contentOwner: vishgupt
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: adaptive_forms, author
exl-id: 3fdbe5a3-5c3c-474d-b701-e0182da4191a
source-git-commit: 9e06c115af2a262859d39bcd5ee0016df2475591
workflow-type: tm+mt
source-wordcount: '1825'
ht-degree: 12%

---


# 적응형 Forms에서 reCAPTCHA 사용 {#using-reCAPTCHA-in-adaptive-forms}

<span class="preview"> [새 적응형 양식 만들기](/help/forms/creating-adaptive-form-core-components.md) 또는 [AEM Sites 페이지에 적응형 양식 추가](/help/forms/create-or-add-an-adaptive-form-to-aem-sites-page.md) 작업을 할 때 현대적이고 확장 가능한 데이터 캡처 [핵심 구성 요소](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html)를 사용하는 것이 좋습니다. 이러한 구성 요소는 적응형 양식 만들기 작업이 대폭 개선되어 우수한 사용자 경험을 보장할 수 있게 되었음을 나타냅니다. 이 문서에서는 기초 구성 요소를 사용하여 적응형 양식을 작성하는 이전 접근법에 대해 설명합니다. </span>


| 버전 | 문서 링크 |
| -------- | ---------------------------- |
| AEM 6.5 | [여기 클릭](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-basic-authoring/captcha-adaptive-forms.html) |
| AEM as a Cloud Service | 이 문서 |
| 적용 대상 | 기초 구성 요소를 기반으로 하는 적응형 양식입니다. <br> 핵심 구성 요소 기반 적응형 양식의 경우 [여기를 클릭하십시오.](/help/forms/captcha-adaptive-forms-core-components.md). |


CAPTCHA(컴퓨터와 인간을 구분하기 위해 완전히 자동화된 공공 튜링 테스트)는 인간과 자동화된 프로그램 또는 봇을 구별하기 위해 온라인 거래에서 일반적으로 사용되는 프로그램입니다. 문제를 제기하고 사용자 응답을 평가하여 사이트와 상호 작용하는 것이 인간인지 봇인지 판단합니다. 테스트가 실패할 경우 사용자가 진행하지 못하도록 차단하고 봇이 스팸을 게시하거나 악의적인 목적으로 상호 작용하는 것을 방지하여 온라인 거래를 안전하게 할 수 있도록 도와줍니다.

[!DNL AEM Forms] 적응형 Forms에서 reCAPTCHA를 지원합니다. Google의 reCAPTCHA 서비스를 사용하여 CAPTCHA를 구현할 수 있습니다.

>[!NOTE]
>
>* [!DNL AEM Forms] reCaptcha v2 및 reCaptcha Enterprise를 지원합니다. 다른 버전은 지원되지 않습니다.
>* 적응형 Forms의 reCAPTCHA는의 오프라인 모드에서 지원되지 않습니다. [!DNL AEM Forms] 앱.
>

## Google에서 reCAPTCHA 서비스 구성 {#google-reCAPTCHA}

양식 작성자는 Google의 reCAPTCHA 서비스를 사용하여 적응형 Forms에서 reCAPTCHA를 구현할 수 있습니다. 사이트 보호를 위한 고급 CAPTCHA 기능을 제공합니다. reCAPTCHA 작동 방식에 대한 자세한 내용은 [Google recaptcha](https://developers.google.com/recaptcha/). reCAPTCHA 서비스는 다음을 포함합니다 [!DNL reCAPTCHA v2] 및 [!DNL reCAPTCHA Enterprise] 를 통합할 수 있습니다. [!DNL AEM Forms]. 요구 사항에 따라 reCAPTCHA 서비스를 구성하여 다음을 활성화할 수 있습니다.

![reCAPTCHA](/help/forms/assets/recaptcha_new.png)

* [AEM Forms의 reCAPTCHA Enterprise](#steps-to-implement-reCAPTCHA-enterprise-in-forms)
* [AEM Forms의 reCAPTCHA v2](#steps-to-implement-reCAPTCHA-v2-in-forms)


### reCAPTCHA Enterprise 구성  {#steps-to-implement-reCAPTCHA-enterprise-in-forms}

1. 만들기 또는 선택 [Google 클라우드 프로젝트](https://cloud.google.com/recaptcha-enterprise/docs/set-up-non-google-cloud-environments-api-keys#before-you-begin) 및 활성화 [reCAPTCHA Enterprise API](https://cloud.google.com/recaptcha-enterprise/docs/set-up-non-google-cloud-environments-api-keys#enable-the-recaptcha-enterprise-api).
1. 다음을 획득 [프로젝트 ID](https://support.google.com/googleapi/answer/7014113?hl=en#:~:text=To%20locate%20your%20project%20ID,a%20member%20of%20are%20displayed) 및 만들기 [API 키](https://cloud.google.com/recaptcha-enterprise/docs/set-up-non-google-cloud-environments-api-keys#create_an_api_key) 및 a [웹 사이트에 대한 사이트 키](https://cloud.google.com/recaptcha-enterprise/docs/create-key#create-key).
1. 클라우드 서비스에 대한 구성 컨테이너를 만듭니다.

   1. **[!UICONTROL 도구 > 일반 > 구성 브라우저]**&#x200B;로 이동합니다.
   1. 폴더를 선택하거나 폴더를 만들고 다음 단계를 사용하여 클라우드 구성에 대해 폴더를 활성화하십시오.
      1. 구성 브라우저에서 폴더를 선택하고 을 누릅니다 **[!UICONTROL 속성]**.
      1. 구성 속성 대화 상자에서 다음을 활성화합니다 **[!UICONTROL 클라우드 구성]**.
      1. **[!UICONTROL 저장 및 닫기]**&#x200B;를 탭하여 구성을 저장하고 대화 상자를 종료합니다.

1. 클라우드 서비스 구성 [!DNL reCAPTCHA Enterprise].

   1. Experience Manager 작성자 인스턴스에서 ![tools-1](assets/tools-1.png) > **[!UICONTROL Cloud Service]**.
   1. 누르기 **[!UICONTROL reCAPT차]**. Configurations 페이지가 열립니다. 만든 구성 컨테이너를 선택한 다음 탭합니다. **[!UICONTROL 만들기]**.
   1. 다음으로 버전 선택 [!DNL reCAPTCHA Enterprise] 및 reCAPTCHA Enterprise 서비스에 대한 이름, 프로젝트 ID, 사이트 키 및 API 키(2단계에서 획득)를 지정합니다.
   1. 키 유형을 선택합니다. 키 유형은 에서 구성한 사이트 키와 동일해야 합니다. [Google 클라우드 프로젝트](https://cloud.google.com/recaptcha-enterprise/docs/set-up-non-google-cloud-environments-api-keys#before-you-begin), 예: **확인란 사이트 키** 또는 **점수 기반 사이트 키**.
   1. 지정 [0~1 범위의 임계값 점수](https://cloud.google.com/recaptcha-enterprise/docs/interpret-assessment#interpret_scores). 임계값 점수보다 크거나 같은 점수는 인간 상호 작용을 식별하고, 그렇지 않으면 봇 상호 작용으로 간주됩니다.
   1. 누르기 **[!UICONTROL 만들기]** 을 클릭하여 클라우드 서비스 구성을 생성합니다.

<!--
    1. In the Edit Component dialog, specify the name, project ID, site key, API key (obtained in steps 2 and 3), select the key type, and enter the threshold score. Tap **[!UICONTROL Save Settings]** and then tap **[!UICONTROL OK]** to complete the configuration.
-->

reCAPTCHA Enterprise 서비스가 활성화되면 적응형 양식에서 사용할 수 있습니다. 다음을 참조하십시오 [적응형 양식에서 CAPTCHA 사용](#using-reCAPTCHA).

<!--
![reCAPTCHA Enterprise](/help/forms/assets/recaptcha1-enterprise.png)
-->

### Google reCAPTCHA v2 구성 {#steps-to-implement-reCAPTCHA-v2-in-forms}

1. 획득 [reCAPTCHA API 키 쌍](https://www.google.com/recaptcha/admin) Google에서. 여기에는 다음이 포함됩니다 **사이트 키** 및 a **비밀 키**.
1. 클라우드 서비스에 대한 구성 컨테이너를 만듭니다.
   1. **[!UICONTROL 도구 > 일반 > 구성 브라우저]**&#x200B;로 이동합니다.
   1. 폴더를 선택하거나 폴더를 만들고 다음 단계를 사용하여 클라우드 구성에 대해 폴더를 활성화하십시오.
      1. 구성 브라우저에서 폴더를 선택하고 을 누릅니다 **[!UICONTROL 속성]**.
      1. 구성 속성 대화 상자에서 다음을 활성화합니다 **[!UICONTROL 클라우드 구성]**.
      1. **[!UICONTROL 저장 및 닫기]**&#x200B;를 탭하여 구성을 저장하고 대화 상자를 종료합니다.

1. reCAPTCHA v2에 대한 클라우드 서비스를 구성합니다.

   1. AEM 작성자 인스턴스에서 ![tools-1](assets/tools-1.png) > **Cloud Service**.
   1. 누르기 **[!UICONTROL reCAPT차]**. Configurations 페이지가 열립니다. 만든 구성 컨테이너를 선택한 다음 탭합니다. **[!UICONTROL 만들기]**.
   1. 다음으로 버전 선택 [!DNL reCAPTCHA v2] , reCAPTCHA 서비스(1단계에서 획득)에 대한 이름, 사이트 키 및 비밀 키를 지정하고 을 누릅니다 **[!UICONTROL 만들기]** 을 클릭하여 클라우드 서비스 구성을 생성합니다.
   1. 구성 요소 편집 대화 상자에서 1단계에서 얻은 사이트 및 비밀 키를 지정합니다. 누르기 **[!UICONTROL 설정 저장]** 그런 다음 을 누릅니다 **확인** 구성을 완료합니다.

   reCAPTCHA 서비스가 구성되면 적응형 양식에서 사용할 수 있습니다. 자세한 내용은 [적응형 양식에서 CAPTCHA 사용](#using-reCAPTCHA).

<!--![reCAPTCHA v2](/help/forms/assets/recaptcha-v2.png)-->


## 적응형 양식에서 reCAPTCHA 사용 {#using-reCAPTCHA}

적응형 양식에서 reCAPTCHA를 사용하려면:

1. 편집 모드에서 적응형 양식을 엽니다.

   >[!NOTE]
   >
   >적응형 양식을 만들 때 선택한 구성 컨테이너에 reCAPTCHA 클라우드 서비스가 포함되어 있는지 확인합니다. 적응형 양식 속성을 편집하여 양식과 관련된 구성 컨테이너를 변경할 수도 있습니다.

1. 구성 요소 브라우저에서 **Captcha** 구성 요소를 적응형 양식에 추가합니다.

   >[!NOTE]
   >
   >* 적응형 양식에서 Captcha 구성 요소를 두 개 이상 사용하는 것은 지원되지 않습니다. 또한 소극적 로드로 표시된 패널 또는 조각에서는 CAPTCHA를 사용하지 않는 것이 좋습니다.
   >* reCaptcha는 시간에 민감하며 약 2~3분 후에 만료됩니다. 따라서 적응형 양식에서 Captcha 구성 요소를 제출 단추 바로 앞에 배치하는 것이 좋습니다.

1. 추가한 Captcha 구성 요소를 선택하고 을 누릅니다 ![cmppr](assets/cmppr.png) 속성을 편집합니다.
1. CAPTCHA 위젯의 제목을 지정합니다. 기본값은 입니다. **Captcha**. 선택 **제목 숨기기** 제목을 표시하지 않으려는 경우
1. 다음에서 **Captcha 서비스** 드롭다운, 선택 **reCAPT차** 에 설명된 대로 구성한 경우 reCAPTCHA 서비스를 활성화하려면 다음을 수행하십시오 [Google의 reCAPTCHA 서비스](#google-reCAPTCHA).
1. 다음에 대한 설정 드롭다운에서 구성을 선택합니다. **reCAPTCHA 엔터프라이즈** 또는 **reCAPTCHA v2**
   1. 다음을 선택하는 경우 **reCAPTCHA 엔터프라이즈** version의 키 형식은 다음과 같을 수 있습니다. **확인란** 또는 **점수 기준**, 구성 시 선택한 항목에 따라 달라집니다 [웹 사이트에 대한 사이트 키](https://cloud.google.com/recaptcha-enterprise/docs/create-key#create-key):

   >[!NOTE]
   >
   >* 을 사용하는 클라우드 구성 **키 유형** 다음으로: **확인란**, 사용자 지정된 오류 메시지는 captcha 유효성 검사가 실패하면 인라인 메시지로 표시됩니다.
   >* 을 사용하는 클라우드 구성 **키 유형** 다음으로: **점수 기준**&#x200B;사용자 지정된 오류 메시지는 captcha 유효성 검사가 실패하면 팝업 메시지로 표시됩니다.

   1. 다음과 같이 크기를 선택할 수 있습니다. **[!UICONTROL 기본]** 및 **[!UICONTROL 콤팩트]**.
   1. 다음을 선택할 수 있습니다. **[!UICONTROL 바인드 참조]**, 위치 **[!UICONTROL 바인드 참조]** 제출된 데이터는 바인딩된 데이터이며, 그렇지 않으면 바인딩되지 않은 데이터입니다. 다음은 양식 제출 시 바인딩되지 않은 데이터와 바인딩된 데이터(바인드 참조를 SSN으로 사용)의 XML 예입니다.

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

   다음을 선택하는 경우 **reCAPTCHA v2** 버전:
   1. 다음과 같이 크기를 선택할 수 있습니다. **[!UICONTROL 기본]** 또는 **[!UICONTROL 콤팩트]** reCAPTCHA 위젯용
   1. 다음을 선택할 수 있습니다. **[!UICONTROL 숨김]** 의심되는 활동이 있는 경우에만 CAPTCHA 문제를 표시하는 옵션입니다.

   reCAPTCHA 서비스가 적응형 양식에서 활성화됩니다. 양식을 미리 보고 CAPTCHA가 작동하는 것을 볼 수 있습니다. 다음 **reCAPTCHA로 보호됨** 아래 표시된 배지는 보호된 양식에 표시됩니다.
   ![reCAPTCHA 배지로 보호된 Google](/help/forms/assets/google-recaptcha-v2.png)

1. 속성을 저장합니다.

>[!NOTE]
> 
> 선택 안 함 **[!UICONTROL 기본값]** 기본 AEM CAPTCHA 서비스가 더 이상 사용되지 않으므로 CAPTCHA 서비스 드롭다운에서 을 사용하십시오.

>[!VIDEO](https://video.tv.adobe.com/v/3422641/recaptcha-google-adaptive-forms/?quality=12&learn=on)

### 규칙에 따라 CAPTCHA 구성 요소 표시 또는 숨기기 {#show-hide-captcha}

적응형 양식의 구성 요소에 적용하는 규칙에 따라 CAPTCHA 구성 요소를 표시하거나 숨기도록 선택할 수 있습니다. 구성 요소를 탭하고 을 선택합니다. ![규칙 편집](assets/edit-rules-icon.svg), 및 탭 **[!UICONTROL 만들기]** 을 클릭하여 규칙을 만듭니다. 규칙 만들기에 대한 자세한 내용은 [규칙 편집기](rule-editor.md).

예를 들어 CAPTCHA 구성 요소는 양식의 통화 값 필드에 25000보다 큰 값이 있는 경우에만 적응형 양식에 표시해야 합니다.

탭 **[!UICONTROL 통화 값]** 양식에 필드를 입력하고 다음 규칙을 만듭니다.

![규칙 표시 또는 숨기기](assets/rules-show-hide-captcha.png)

>[!NOTE]
>
> reCAPTCHA v2 구성을 선택하고 크기를 로 설정하면 [!UICONTROL 숨김], 표시/숨기기 옵션은 비활성화 상태로 유지됩니다.

### CAPTCHA 유효성 검사 {#validate-captcha}

양식을 제출하거나 사용자 작업 및 조건에 대한 CAPTCHA 유효성 검사의 기초가 될 때 적응형 양식에서 CAPTCHA의 유효성을 검사할 수 있습니다.

#### 양식 제출 시 CAPTCHA 유효성 검사 {#validation-form-submission}

적응형 양식을 제출할 때 CAPTCHA의 유효성을 자동으로 검사하려면 다음 작업을 수행하십시오.

1. CAPTCHA 구성 요소를 탭하고 을 선택합니다 ![cmppr](assets/configure-icon.svg) 구성 요소 속성을 봅니다.
1. 다음에서 **[!UICONTROL CAPTCHA 유효성 검사]** 섹션, 선택 **[!UICONTROL 양식 제출 시 CAPTCHA 유효성 검사]**.
1. 누르기 ![완료](assets/save_icon.svg) 구성 요소 속성을 저장합니다.

#### 사용자 작업 및 조건에 대한 CAPTCHA 유효성 검사 {#validate-captcha-user-action}

조건 및 사용자 작업을 기반으로 CAPTCHA의 유효성을 검사하려면 다음을 수행하십시오.

1. CAPTCHA 구성 요소를 탭하고 을 선택합니다 ![cmppr](assets/configure-icon.svg) 구성 요소 속성을 봅니다.
1. 다음에서 **[!UICONTROL CAPTCHA 유효성 검사]** 섹션, 선택 **[!UICONTROL 사용자 작업에 대한 CAPTCHA 유효성 검사]**.
1. 누르기 ![완료](assets/save_icon.svg) 구성 요소 속성을 저장합니다.

[!DNL Experience Manager Forms] 다음을 제공합니다 `ValidateCAPTCHA` 사전 정의된 조건을 사용하여 CAPTCHA의 유효성을 검사하기 위한 API입니다. 사용자 지정 제출 액션을 사용하거나 적응형 양식의 구성 요소에 대한 규칙을 정의하여 API를 호출할 수 있습니다.

다음은 의 예입니다 `ValidateCAPTCHA` 사전 정의된 조건을 사용하여 CAPTCHA의 유효성을 검사하기 위한 API:

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

이 예제는 `ValidateCAPTCHA` API는 양식을 작성하는 동안 사용자가 지정한 숫자 상자의 자릿수가 5보다 큰 경우에만 양식에서 CAPTCHA를 확인합니다.

**옵션 1: 사용 [!DNL Experience Manager Forms] 사용자 지정 제출 액션을 사용하여 CAPTCHA의 유효성을 검사하기 위한 CAPTCHA API**

다음 단계를 수행하여 을 사용합니다. `ValidateCAPTCHA` 사용자 지정 제출 액션을 사용하여 CAPTCHA의 유효성을 검사하기 위한 API:

1. 다음을 포함하는 스크립트 추가 `ValidateCAPTCHA` 사용자 지정 제출 액션에 대한 API입니다. 사용자 지정 제출 액션에 대한 자세한 내용은 [적응형 Forms에 대한 사용자 지정 제출 액션 만들기](custom-submit-action-form.md).
1. 에서 사용자 지정 제출 액션의 이름을 선택합니다. **[!UICONTROL 제출 액션]** 드롭다운 목록 **[!UICONTROL 제출]** 적응형 양식의 속성입니다.
1. 누르기 **[!UICONTROL 제출]**. CAPTCHA는에 정의된 조건을 기반으로 유효성이 검사됩니다. `ValidateCAPTCHA` 사용자 지정 제출 액션의 API입니다.

**옵션 2: 사용 [!DNL Experience Manager Forms] 양식을 제출하기 전에 사용자 작업에서 CAPTCHA의 유효성을 검사하기 위한 CAPTCHA API 확인**

을 호출할 수도 있습니다. `ValidateCAPTCHA` 적응형 양식의 구성 요소에 규칙을 적용하여 만든 API.

예를 들어 **[!UICONTROL CAPTCHA 유효성 검사]** 를 클릭하고, 단추를 클릭할 때 서비스를 호출하는 규칙을 만듭니다.

다음 그림은 를 클릭할 때 서비스를 호출하는 방법을 보여 줍니다. **[!UICONTROL CAPTCHA 유효성 검사]** 단추:

![CAPTCHA 유효성 검사](assets/captcha-validation1.gif)

다음을 포함하는 사용자 정의 서블릿을 호출할 수 있습니다. `ValidateCAPTCHA` 규칙 편집기를 사용하는 API이며, 유효성 검사 결과에 따라 적응형 양식의 제출 단추를 활성화하거나 비활성화합니다.

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

reCAPTCHA 서비스는 `https://www.recaptcha.net/` 을 기본 도메인으로 설정합니다. 설정할 설정을 수정할 수 있습니다 `https://www.google.com/` 또는 reCAPTCHA 서비스 로드, 렌더링 및 유효성 검사를 위한 사용자 지정 도메인 이름입니다.

설정 **[!UICONTROL af.cloudservices.recaptcha.domain]** 의 속성 **[!UICONTROL 적응형 양식 및 대화형 통신 웹 채널 구성]** 지정할 구성 `https://www.google.com/` 또는 기타 모든 사용자 정의 도메인 이름. 다음 JSON 파일에는 샘플이 표시됩니다.

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
