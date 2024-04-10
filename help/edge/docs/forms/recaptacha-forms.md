---
title: AEM Forms Edge Delivery Services과 함께 reCAPTCHA 사용
description: EDS 양식에서 Google reCAPTCHA 사용
feature: Edge Delivery Services
exl-id: ac104e23-f175-435f-8414-19847efa5825
source-git-commit: eadfc3d448bd2fadce08864ab65da273103a6212
workflow-type: tm+mt
source-wordcount: '190'
ht-degree: 1%

---


# AEM Forms Edge Delivery Services과 함께 reCAPTCHA 사용

reCAPTCHA는 사기성 활동, 스팸 및 오용으로부터 웹 사이트를 보호하는 데 사용되는 인기있는 도구입니다. Edge Delivery Services에서 적응형 Forms 블록은 Google reCAPTCHA를 추가하여 인간과 보트를 구분하는 기능을 제공합니다. 이 기능을 사용하면 웹 사이트를 스팸 및 오용으로부터 보호할 수 있습니다.
예를 들어, 여행 시작일과 종료일, 객실 예산, 예상 여행 비용, 여행자 정보 등의 데이터를 수집하는 조회 양식을 생각해 보십시오. 이러한 경우 악성 사용자가 피싱 이메일을 보내거나 스팸봇을 이용해 관련성이 없거나 해로운 콘텐츠로 유출하는 등의 목적으로 양식을 악용할 위험이 있다. reCAPTCHA를 통합하면 제출 내용이 실제 사용자로부터 받은 것임을 확인하여 보안을 강화함으로써 스팸 항목을 효과적으로 최소화할 수 있습니다.

Edge Delivery Services은 **점수 기준(v3)-reCAPTCHA** (적응형 양식 블록)

![Recaptcha V2](/help/forms/assets/recaptcha-v2-invisible.png)

다음 **reCAPT차** 기능은 프리릴리스 프로그램 아래에 있습니다. 액세스 권한을 요청하려면 **reCAPT차** AEM Forms Edge Delivery Services의 경우 회사 주소에서 mailto:aem-forms-ea@adobe.com으로 이메일을 보내십시오.

<!--
By the end of this article, you learn to:
  * [Enable Google reCAPTCHA's for a single form](#enable-google-recaptchas-for-a-single-form)
  * [Enable reCAPTCHA for all the forms on your Site](#enable-recaptcha-for-all-the-forms)

## Pre-requisite

Register your domain with [Google reCAPTCHA and obtain credentials](https://www.google.com/recaptcha/admin/create).

## Enable Google reCAPTCHA's for a single form {#enable-google-recaptchas-for-a-single-form}

Enabling Google reCAPTCHA for a single form involves integrating Google's reCAPTCHA service into a specific web form to prevent automated abuse or spam submissions.

To enable Google reCAPTCHA's for a single form:
1. [Configure the reCAPTCHA secret key in project configuration file](#configure-secret-key)
1. [Add reCAPTCHA site key to your form](#add-site-key)


### Configure the reCAPTCHA secret key in project configuration file {#configure-secret-key}

The Site Secret for domain registered with Google reCAPTCHA is added to project the configuration file (`.helix/config`) in your AEM Project folder at Microsoft SharePoint or Google Drive. To add the Site Secret to the config file:

1. Go to your AEM Project folder on Microsoft® SharePoint or Google Drive. 
1. Create the `.helix/config.xlsx` file in your AEM Project folder in Microsoft SharePoint Site or the `.helix/config` file in AEM Project folder within your Google Drive. 

    >[!NOTE]
    >
    > The [project configuration file](https://www.aem.live/docs/configuration) is a spreadsheet located at `/.helix/config`. If the file does not exist, create it.

1. Open the `config` file and add the following key and value pairs:

    * **captcha.secret**: Google reCAPTCHA secret key value
    * **captcha.type**: reCAPTCHA v2
  
   Refer to the image for an illustration of a project configuration file:

    ![Project configuration file](/help/forms/assets/recaptcha-config-file.png)

    >[!NOTE]
    >
    >  You can retrieve the reCAPTCHA keys from the [Google reCAPTCHA Admin Console](https://www.google.com/recaptcha/admin).

1.  Preview and publish the `config` file using [AEM Sidekick](https://www.aem.live/developer/tutorial#preview-and-publish-your-content). 

### Add reCAPTCHA site key to your form {#add-site-key}

The Site Key for domain registered with Google reCAPTCHA is added to the spreadsheet of the form that is to be protected. To add the Site key to a form:

1. Go to your AEM Project folder on Microsoft® SharePoint or Google Drive and open your spreadsheet. You can also create new spreadsheet for a form.
1. Insert a row into the spreadsheet to add new field as CAPTCHA, including the following details:
    * **type**: captcha
    * **value**: Google reCAPTCHA site key value
  
    Refer to the illustration below, depicting the spreadsheet with the new row type as CAPTCHA:
  
   ![Recaptcha spreadsheet](/help/forms/assets/recaptcha-spreadsheet.png)

    >[!NOTE]
    >
    >  You can retrieve the reCAPTCHA keys from the [Google reCAPTCHA Admin Console](https://www.google.com/recaptcha/admin).

1. Use [AEM Sidekick](https://www.aem.live/developer/tutorial#preview-and-publish-your-content) to preview and publish the sheet. 
You can refer to the [spreadsheet](/help/forms/assets/recaptcha-enquiry.xlsx) that includes the form definition for an enquiry form.

After adding new row in the form definition, a reCAPTCHA badge appears at the bottom-right corner of the form. This ensures that the form is now protected from fraudulent activities, spam, and misuse.

![recaptcha-form](/help/forms/assets/recaptcha-form.png)

Refer to the URL below, which showcases the live form with the reCAPTCHA badge:
https://main--wefinance--wkndforms.hlx.live/enquiry

## Enable reCAPTCHA for all the forms on your Site{#enable-recaptcha-for-all-the-forms}

To apply Google reCAPTCHA to all the forms on your Site that use Adaptive Forms Block, skip the previous steps and directly embed the `sitekey` value into the `recaptcha.js` file. To include site key value in the `recaptcha.js` file:

1. Open the corresponding GitHub repository on your local machine. 
1. Navigate to `../blocks/form/integrations/recaptcha.js` file.
1. Replace the `siteKey` with Google reCAPTCHA site key value.

    ![Recaptcha apply to all forms](/help/forms/assets/recaptcha-apply-to-all-forms.png)

    >[!NOTE]
    >
    >  You can retrieve the reCAPTCHA keys from the [Google reCAPTCHA Admin Console](https://www.google.com/recaptcha/admin).

1. Use [AEM Sidekick](https://www.aem.live/developer/tutorial#preview-and-publish-your-content) to preview and publish the site. 

The reCAPTCHA badge starts appearing for all the forms on your Site. 
-->

## 추가 참조

{{see-more-forms-eds}}

