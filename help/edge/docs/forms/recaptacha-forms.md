---
title: AEM Forms as a Cloud Service용 Edge Delivery Services와 함께 reCAPTCHA 사용
description: EDS 양식에서 Google reCAPTCHA 사용
feature: Edge Delivery Services
exl-id: ac104e23-f175-435f-8414-19847efa5825
role: Admin, Architect, Developer
source-git-commit: fe45123b3aefddaf02bc8584283941db168ba174
workflow-type: tm+mt
source-wordcount: '841'
ht-degree: 24%

---


# AEM Forms as a Cloud Service용 Edge Delivery Services와 함께 reCAPTCHA 사용

<span>**reCAPTCHA** 기능은 시험판 프로그램에 있습니다. AEM Forms Edge Delivery Services의 **reCAPTCHA** 기능에 대한 액세스를 요청하려면 회사 주소에서 mailto:aem-forms-ea@adobe.com으로 전자 메일을 보내십시오.</span>

reCAPTCHA는 사기 행위, 스팸, 오용으로부터 웹 사이트를 보호하는 데 사용되는 인기 도구입니다. Edge Delivery Services에서 적응형 양식 블록은 인간과 봇을 구별하도록 Google reCAPTCHA를 추가하는 기능을 제공합니다. 이 기능을 사용하여 사용자는 스팸 및 오용으로부터 웹 사이트를 보호할 수 있습니다.
여행 시작 및 종료 날짜, 객실 예산, 여행 예상 비용 및 여행자 정보 등의 데이터를 수집하는 문의 양식을 고려해 보십시오. 이러한 경우, 악의적인 사용자가 피싱 이메일을 보내거나 스팸봇을 사용하여 관련이 없거나 유해한 콘텐츠를 대량으로 보내는 등의 목적으로 양식을 악용할 위험이 있습니다. reCAPTCHA를 통합하면 실제 사용자가 제출한 것인지 확인해서 스팸 항목을 효과적으로 최소화하여 보안을 강화합니다.

<!-- ![Recaptcha Image](/help/edge/docs/forms/assets/recaptcha-image.png){width="300" align="center"} -->

Edge Delivery Services은 적응형 양식 블록에 대한 **점수 기반(v3)-reCAPTCHA**&#x200B;만 지원합니다.

![Recaptcha V2](/help/forms/assets/recaptcha-v2-invisible.png){width="300" align="center"}


이 문서가 작성되면 다음 방법을 파악할 수 있습니다.
* [단일 양식에 Google reCAPTCHA 활성화](#enable-google-recaptchas-for-a-single-form)
* [사이트의 모든 양식에 대해 reCAPTCHA 활성화](#enable-recaptcha-for-all-the-forms)

## 전제 조건

* [적응형 Forms 블록을 사용하여 양식 만들기](/help/edge/docs/forms/create-forms.md)에 설명된 단계에 따라 Edge Delivery Services Forms 개발을 시작하십시오.
* [Google reCAPTCHA에 도메인을 등록하고 자격 증명을 획득](https://www.google.com/recaptcha/admin/create)합니다.

## 단일 양식에 Google reCAPTCHA 활성화 {#enable-google-recaptchas-for-a-single-form}

단일 양식에 대해 Google reCAPTCHA를 활성화하려면 자동화된 악용 또는 스팸 제출을 방지하기 위해 Google의 reCAPTCHA 서비스를 특정 웹 양식에 통합해야 합니다.

단일 양식에 대해 Google reCAPTCHA를 활성화하려면 다음을 수행하십시오.
1. [프로젝트 구성 파일에서 reCAPTCHA 비밀 키 구성](#configure-secret-key)
1. [양식에 reCAPTCHA 사이트 키 추가](#add-site-key)

Edge Delivery Services Forms에서 reCaptcha 구성을 시작하려면 양식에 대한 양식 정의를 포함하는 다음 [스프레드시트](/help/edge/docs/forms/assets/recaptcha.xlsx)를 참조하십시오.

### 프로젝트 구성 파일에서 reCAPTCHA 비밀 키 구성 {#configure-secret-key}

Google reCAPTCHA에 등록된 도메인의 사이트 암호가 Microsoft SharePoint 또는 Google 드라이브의 AEM Project 폴더에 구성 파일(`.helix/config`)을 투영하도록 추가됩니다. 구성 파일에 사이트 암호를 추가하려면:

1. Microsoft® SharePoint 또는 Google 드라이브의 AEM 프로젝트 폴더로 이동합니다.
1. Microsoft SharePoint 사이트의 AEM 프로젝트 폴더에 `.helix/config.xlsx` 파일을 만들거나 Google 드라이브의 AEM 프로젝트 폴더에 `.helix/config` 파일을 만듭니다.

   >[!NOTE]
   >
   > [프로젝트 구성 파일](https://www.aem.live/docs/configuration)은(는) `/.helix/config`에 있는 스프레드시트입니다. 파일이 없으면 만듭니다.

1. `config` 파일을 열고 다음 키 및 값 쌍을 추가합니다.

   * **captcha.secret**: Google reCAPTCHA 비밀 키 값
   * **captcha.type**: reCAPTCHA v2

   >[!NOTE]
   >
   >  * [Google reCAPTCHA Admin Console](https://www.google.com/recaptcha/admin)에서 reCAPTCHA 키를 검색할 수 있습니다.
   >  * `config` 파일의 **captcha.type** 값을 **reCAPTCHA v2**(으)로 지정해야 합니다.

   아래 프로젝트 구성 파일의 스크린샷을 참조하십시오.

   ![프로젝트 구성 파일](/help/forms/assets/recaptcha-config-file.png)

1. `config` 파일을 저장합니다.

1. [AEM Sidekick](https://www.aem.live/developer/tutorial#preview-and-publish-your-content)을(를) 사용하여 `config` 파일을 미리 보고 게시합니다.

### 양식에 reCAPTCHA 사이트 키 추가 {#add-site-key}

Google reCAPTCHA에 등록된 도메인의 사이트 키는 보호되는 양식 스프레드시트에 추가됩니다. 양식에 사이트 키를 추가하려면:

1. Microsoft® SharePoint 또는 Google Drive의 AEM 프로젝트 폴더로 이동하여 스프레드시트를 엽니다. 양식의 스프레드시트를 새로 만들 수도 있습니다.
1. 다음 세부 정보를 포함하여 새 필드를 CAPTCHA로 추가하려면 스프레드시트에 행을 삽입합니다.
   * **유형**: captcha
   * **값**: Google reCAPTCHA 사이트 키 값

   스프레드시트를 CAPTCHA로 새 행 유형으로 보여 주는 아래 스크린샷을 참조하십시오.

   ![Recaptcha 스프레드시트](/help/edge/docs/forms/assets/recaptcha-spreadsheet.png)

   >[!NOTE]
   >
   >  [Google reCAPTCHA Admin Console](https://www.google.com/recaptcha/admin)에서 reCAPTCHA 키를 검색할 수 있습니다.

1. 스프레드시트를 저장합니다.
1. [AEM Sidekick](https://www.aem.live/developer/tutorial#preview-and-publish-your-content)을 사용하여 시트를 미리 보고 게시합니다.

양식 정의에 새 행을 추가하면 양식의 오른쪽 하단 모서리에 reCAPTCHA 배지가 나타납니다. 이렇게 하면 이제 양식이 사기 활동, 스팸 및 오용으로부터 보호됩니다.

![recaptcha-form](/help/edge/docs/forms/assets/recaptcha-form.png)

## 사이트의 모든 양식에 대해 reCAPTCHA 활성화{#enable-recaptcha-for-all-the-forms}

적응형 Forms 블록을 사용하는 사이트의 모든 양식에 Google reCAPTCHA를 적용하려면 이전 단계를 건너뛰고 `sitekey` 값을 `recaptcha.js` 파일에 직접 포함하십시오. `recaptcha.js` 파일에 사이트 키 값을 포함하려면:

1. [recaptcha.js 파일에서 Google reCAPTCHA 사이트 키 업데이트](#1-update-google-recaptcha-site-key-in-recaptchajs-file)
1. [파일 배포 및 프로젝트 빌드](#2-deploy-the-file-and-build-the-project)
1. [AEM 사이드 킥을 사용하여 사이트 미리보기](#3-preview-the-site-using-the-aem-sidekick)

### recaptcha.js 파일에서 Google reCAPTCHA 사이트 키 업데이트

1. 로컬 컴퓨터에서 해당 GitHub 리포지토리를 엽니다.
1. `[../Form Block/integrations]` 폴더로 이동하여 `recaptcha.js` 파일을 엽니다.
1. `siteKey`을(를) Google reCAPTCHA 사이트 키 값으로 바꿉니다.

   ![Recaptcha가 모든 양식에 적용됨](/help/forms/assets/recaptcha-apply-to-all-forms.png)

   >[!NOTE]
   >
   >  [Google reCAPTCHA Admin Console](https://www.google.com/recaptcha/admin)에서 reCAPTCHA 키를 검색할 수 있습니다.

1. `recaptcha.js` 파일을 저장합니다.

### 파일 배포 및 프로젝트 빌드

업데이트된 `recaptcha.js` 파일을 GitHub 프로젝트에 배포하고 빌드 성공 여부를 확인합니다.

### AEM 사이드 킥을 사용하여 사이트 미리보기

[AEM Sidekick](https://www.aem.live/developer/tutorial#preview-and-publish-your-content)을(를) 사용하여 사이트를 미리 보고 게시하십시오.

reCAPTCHA 배지는 사이트의 모든 양식에 대해 표시되기 시작합니다.

## 추가 참조

{{see-more-forms-eds}}

