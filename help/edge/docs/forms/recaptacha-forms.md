---
title: AEM Forms as a Cloud Service용 Edge Delivery Services와 함께 reCAPTCHA 사용
description: AEM Forms용 Edge Delivery Services 양식에서 Google reCAPTCHA 사용
feature: Edge Delivery Services
exl-id: ac104e23-f175-435f-8414-19847efa5825
role: Admin, Architect, Developer
source-git-commit: 4a8153ffbdbc4da401089ca0a6ef608dc2c53b22
workflow-type: ht
source-wordcount: '848'
ht-degree: 100%

---


# AEM Forms as a Cloud Service용 Edge Delivery Services와 함께 reCAPTCHA 사용

<span> **reCAPTCHA** 기능은 프리릴리스 프로그램에 포함되어 있습니다. AEM Forms용 Edge Delivery Services의 **reCAPTCHA** 기능에 대한 액세스 권한을 요청하려면 귀사의 주소를 통해 mailto:aem-forms-ea@adobe.com으로 이메일을 보내십시오.</span>

reCAPTCHA는 사기 행위, 스팸, 오용으로부터 웹 사이트를 보호하는 데 사용되는 인기 도구입니다. Edge Delivery Services에서 적응형 양식 블록은 인간과 봇을 구별하도록 Google reCAPTCHA를 추가하는 기능을 제공합니다. 이 기능을 사용하여 사용자는 스팸 및 오용으로부터 웹 사이트를 보호할 수 있습니다.
여행 시작 및 종료 날짜, 객실 예산, 여행 예상 비용 및 여행자 정보 등의 데이터를 수집하는 문의 양식을 고려해 보십시오. 이러한 경우, 악의적인 사용자가 피싱 이메일을 보내거나 스팸봇을 사용하여 관련이 없거나 유해한 콘텐츠를 대량으로 보내는 등의 목적으로 양식을 악용할 위험이 있습니다. reCAPTCHA를 통합하면 실제 사용자가 제출한 것인지 확인해서 스팸 항목을 효과적으로 최소화하여 보안을 강화합니다.

<!-- ![Recaptcha Image](/help/edge/docs/forms/assets/recaptcha-image.png){width="300" align="center"} -->

Edge Delivery Services는 적응형 양식 블록에 대해 **점수 기반(v3)-reCAPTCHA**&#x200B;만 지원합니다.

![Recaptcha V2](/help/forms/assets/recaptcha-v2-invisible.png){width="300" align="center"}


이 문서가 작성되면 다음 방법을 파악할 수 있습니다.
* [단일 양식에 맞게 Google reCAPTCHA 활성화](#enable-google-recaptchas-for-a-single-form)
* [사이트의 모든 양식에 맞게 reCAPTCHA 활성화](#enable-recaptcha-for-all-the-forms)

## 전제 조건

* [적응형 양식 블록을 사용하여 양식 만들기](/help/edge/docs/forms/create-forms.md)에 설명된 절차에 따라 Edge Delivery Services 양식 개발을 시작합니다.
* [Google reCAPTCHA를 통해 도메인을 등록하고 자격 증명](https://www.google.com/recaptcha/admin/create)을 얻습니다.

## 단일 양식에 맞게 Google reCAPTCHA 활성화 {#enable-google-recaptchas-for-a-single-form}

단일 양식에 맞게 Google reCAPTCHA를 활성화할 경우 Google의 reCAPTCHA 서비스를 특정 웹 양식에 통합하여 자동화된 남용 또한 스팸 제출을 방지할 수 있습니다.

단일 양식에 맞게 Google reCAPTCHA를 활성화하려면
1. [프로젝트 구성 파일에서 reCAPTCHA 암호 키 구성](#configure-secret-key)
1. [양식에 reCAPTCHA 사이트 키 추가](#add-site-key)

Edge Delivery Services 양식에서 reCaptcha 구성을 시작하려면 양식에 대한 양식 정의가 포함된 다음 [스프레드시트](/help/edge/docs/forms/assets/recaptcha.xlsx)를 참조하십시오.

### 프로젝트 구성 파일에서 reCAPTCHA 암호 키 구성 {#configure-secret-key}

Google reCAPTCHA에 등록된 도메인의 사이트 암호는 Microsoft SharePoint 또는 Google Drive의 AEM Project 폴더에 있는 프로젝트 구성 파일(`.helix/config`)에 추가됩니다. 구성 파일에 사이트 암호를 추가하려면

1. Microsoft® SharePoint 또는 Google Drive의 AEM Project 폴더로 이동합니다.
1. Microsoft SharePoint 사이트의 AEM Project 폴더에서 `.helix/config.xlsx` 파일을 만들거나 Google Drive 내의 AEM Project 폴더에서 `.helix/config` 파일을 만듭니다.

   >[!NOTE]
   >
   > [프로젝트 구성 파일](https://www.aem.live/docs/configuration)은 `/.helix/config` 위치에 있는 스프레드시트입니다. 파일이 존재하지 않는 경우 만듭니다.

1. `config` 파일을 열고 다음 키와 값 쌍 추가:

   * **captcha.secret**: Google reCAPTCHA 암호 키 값
   * **captcha.type**: reCAPTCHA v2

   >[!NOTE]
   >
   >  * [Google reCAPTCHA Admin Console](https://www.google.com/recaptcha/admin)에서 reCAPTCHA 키를 검색할 수 있습니다.
   >  * `config` 파일의 **captcha.type** 값을 **reCAPTCHA v2**&#x200B;로 지정해야 합니다.

   아래 프로젝트 구성 파일의 스크린샷을 참조하십시오.

   ![프로젝트 구성 파일](/help/forms/assets/recaptcha-config-file.png)

1. `config` 파일을 저장합니다.

1. [AEM Sidekick](https://www.aem.live/developer/tutorial#preview-and-publish-your-content)을 사용하여 `config` 파일을 미리 보고 게시합니다.

### 양식에 reCAPTCHA 사이트 키 추가 {#add-site-key}

Google reCAPTCHA에 등록된 도메인의 사이트 키는 보호할 양식의 스프레드시트에 추가됩니다. 양식에 사이트 키를 추가하려면

1. Microsoft® SharePoint 또는 Google Drive의 AEM 프로젝트 폴더로 이동하여 스프레드시트를 엽니다. 양식의 스프레드시트를 새로 만들 수도 있습니다.
1. 다음 세부 정보가 포함된 새 필드를 CAPTCHA로 추가하려면 스프레드시트에 행을 삽입합니다.
   * **유형**: captcha
   * **값**: Google reCAPTCHA 사이트 키 값

   새 열 유형인 CAPTCHA로 스프레드시트를 보여 주는 아래 스크린샷을 참조하십시오.

   ![Recaptcha 스프레드시트](/help/edge/docs/forms/assets/recaptcha-spreadsheet.png)

   >[!NOTE]
   >
   >  [Google reCAPTCHA Admin Console](https://www.google.com/recaptcha/admin)에서 reCAPTCHA 키를 검색할 수 있습니다.

1. 스프레드시트를 저장합니다.
1. [AEM Sidekick](https://www.aem.live/developer/tutorial#preview-and-publish-your-content)을 사용하여 시트를 미리 보고 게시합니다.

양식 정의에서 새 행을 추가하면 reCAPTCHA 배지가 양식의 오른쪽 하단에 나타납니다. 이렇게 하면 사기 행위, 스팸, 오용으로부터 양식을 보호할 수 있습니다.

![recaptcha-form](/help/edge/docs/forms/assets/recaptcha-form.png)

## 사이트의 모든 양식에 맞게 reCAPTCHA 활성화{#enable-recaptcha-for-all-the-forms}

사이트에서 적응형 양식 블록을 사용하는 모든 양식에 Google reCAPTCHA를 적용하려면 이전 단계를 건너뛰고 `sitekey` 값을 `recaptcha.js` 파일에 직접 임베드합니다. `recaptcha.js` 파일에서 사이트 키 값을 포함하려면

1. [recaptcha.js 파일에서 Google reCAPTCHA 사이트 키 업데이트](#1-update-google-recaptcha-site-key-in-recaptchajs-file)
1. [파일 배포 및 프로젝트 빌드](#2-deploy-the-file-and-build-the-project)
1. [AEM Sidekick을 사용하여 사이트 미리보기](#3-preview-the-site-using-the-aem-sidekick)

### recaptcha.js 파일에서 Google reCAPTCHA 사이트 키 업데이트

1. 로컬 컴퓨터에서 해당 GitHub 저장소를 엽니다.
1. `[../Form Block/integrations]` 폴더로 이동하고 `recaptcha.js` 파일을 엽니다.
1. `siteKey`를 Google reCAPTCHA 사이트 키 값으로 바꿉니다.

   ![Recaptcha는 모든 양식에 적용](/help/forms/assets/recaptcha-apply-to-all-forms.png)

   >[!NOTE]
   >
   >  [Google reCAPTCHA Admin Console](https://www.google.com/recaptcha/admin)에서 reCAPTCHA 키를 검색할 수 있습니다.

1. `recaptcha.js` 파일을 저장합니다.

### 파일 배포 및 프로젝트 빌드

업데이트된 `recaptcha.js` 파일을 GitHub 프로젝트에 배포하고 빌드되었는지 확인합니다.

### AEM Sidekick을 사용하여 사이트 미리보기

[AEM Sidekick](https://www.aem.live/developer/tutorial#preview-and-publish-your-content)을 사용하여 사이트를 미리 보고 게시합니다.

reCAPTCHA 배지가 사이트의 모든 양식에 나타나기 시작합니다.

## 추가 참조

{{see-more-forms-eds}}

