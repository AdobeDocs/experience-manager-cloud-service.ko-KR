---
title: AEM Forms용 Edge Delivery Services 양식 번역 및 현지화
description: AEM Forms용 Edge Delivery Services 양식 번역 및 현지화
feature: Edge Delivery Services
hide: true
hidefromtoc: true
exl-id: 8a0c826f-8acc-4a00-bd84-7b0df9a82457
role: Admin, Architect, Developer
source-git-commit: 4a8153ffbdbc4da401089ca0a6ef608dc2c53b22
workflow-type: ht
source-wordcount: '546'
ht-degree: 100%

---


# AEM Forms용 Edge Delivery Services 양식 번역 및 현지화

Edge Delivery Services에서 양식 번역에는 정확성, 명확성 및 일관성에 중점을 두고 양식 콘텐츠를 한 언어에서 다른 언어로 변환하는 작업이 포함됩니다. 번역되거나 현지화된 양식을 사용하면 다양한 지리적 위치에서 더 넓은 대상자 그룹에 연결할 수 있으므로 사용자 경험이 향상되고 다양한 언어 기본 설정에서 커뮤니케이션이 수월해집니다.


문서가 작성되면 다음 방법을 파악할 수 있습니다.

* [Google Drive 내 양식 번역](#translate-form-google-drive)
* [SharePoint Site 내 양식 번역](#translate-form-sharepoint)

## Google Drive 내 양식 번역 {#translate-form-google-drive}

Google 시트의 `GOOGLETRANSLATE` 함수는 내장된 번역 도구를 활용하여 양식을 번역하고 Google 시트 내에서 텍스트를 한 언어에서 다른 언어로 직접 변경합니다. Google Drive 내 양식을 번역하는 방법:

1. Google Drive의 AEM 프로젝트 폴더로 이동하여 Google 시트를 엽니다.
2. 기존 시트(`shared-default`)의 이름을 `shared-en`으로 바꿉니다.
3. `shared-default`라는 시트를 추가합니다. `shared-default` 시트에는 특정 언어로 현지화하기 위한 콘텐츠가 있습니다.
4. `shared-default` 함수를 사용하여 `GOOGLETRANSLATE` 시트에 현지화된 콘텐츠를 추가합니다.
공식을 사용하여 `shared-en` 시트의 셀 D2 콘텐츠를 `shared-default` 시트 내에서 프랑스어로 번역할 수 있습니다. 사용할 함수는 다음과 같습니다.
   `=GOOGLETRANSLATE('shared-en'!D2,"en","fr")`

   ![문의 스프레드시트 번역](/help/forms/assets/translate-enquiry-spreadsheet.png)

5. [AEM Sidekick](https://www.aem.live/developer/tutorial#preview-and-publish-your-content)을 사용하여 시트를 미리 보고 게시합니다.

영어에서 프랑스어로 번역된 `enquiry` 양식에 대한 양식 정의가 포함된 [스프레드시트](/help/forms/assets/enquirytranslate.xlsx)를 참조할 수 있습니다.

![문의 번역 양식](/help/forms/assets/translate-form-french.png)

프랑스어로 번역된 양식을 볼 수 있는 아래 URL을 참조하십시오.
https://main--portal--wkndforms.hlx.live/enquirytranslate

## SharePoint Site 내 양식 번역{#translate-form-sharepoint}

Microsoft® SharePoint 사이트의 양식을 번역하려면 번역 서비스를 사용하여 필드의 레이블을 수동 변경해야 합니다. SharePoint Site 내 양식을 번역하는 방법:

1. Microsoft® SharePoint의 AEM 프로젝트 폴더로 이동하여 스프레드시트를 엽니다.
2. 기존 시트(`shared-default`)의 이름을 `shared-en`으로 바꿉니다.
3. `shared-default`라는 시트를 추가합니다. `shared-default` 시트에는 특정 언어로 현지화하기 위한 콘텐츠가 있습니다.
4. `shared-default` 시트에 현지화된 콘텐츠를 수동으로 추가합니다.

   ![문의 스프레드시트 번역](/help/forms/assets/translate-enquiry-sp-spreadsheet.png)

5. [AEM Sidekick](https://www.aem.live/developer/tutorial#preview-and-publish-your-content)을 사용하여 시트를 미리 보고 게시합니다.

영어에서 프랑스어로 번역된 `enquiry` 양식에 대한 양식 정의가 포함된 [스프레드시트](/help/forms/assets/enquirytranslate-sp.xlsx)를 참조해 주십시오.

![문의 번역 양식](/help/forms/assets/translate-form-french.png)

프랑스어로 번역된 양식을 볼 수 있는 아래 URL을 참조하십시오.
https://main--wefinance--wkndforms.hlx.live/enquirytranslate

## 알려진 문제 {#known-issues}

* 양식 레이블은 `shared-default` 시트에 지정된 현지화된 언어로 번역되지만, 오류 메시지는 브라우저의 기본 언어로 표시됩니다.

  ![오류 메시지](/help/forms/assets/translate-error-message.png)

* 캘린더를 열면 캘린더 드롭다운이 브라우저의 기본 언어로 표시됩니다.

  ![오류 메시지](/help/forms/assets/translate-calender-display.png)


## 자주 묻는 질문 {#faq}

**Q**: 양식에서 지정된 현지 언어로 입력하려면 어떻게 해야 합니까?

**A**: 현지화된 특정 언어로 텍스트를 입력하려면 디바이스의 키보드 설정을 조정합니다. 수행 방법에 대한 지침은 다음 링크를 참조하십시오.

* [다른 언어로 입력하도록 Mac 설정](https://support.apple.com/en-in/guide/mac-help/mchlp1406/mac)
* [다른 언어로 입력하도록 Windows 설정](https://support.microsoft.com/ko/windows/manage-the-input-and-display-language-settings-in-windows-12a10cb4-8626-9b77-0ccb-5013e0c7c7a2#:~:text=Select%20the%20Start%20%3E%20Settings%20%3E%20Time,you%20want%2C%20then%20select%20Options)
* [다른 언어로 입력하도록 Android 또는 iPhone/iPad 설정](https://support.google.com/gboard/answer/7068494?hl=en&amp;co=GENIE.Platform%3DAndroid)


**Q**: `GOOGLETRANSLATE` 함수에 사용된 로케일 목록을 어떻게 검색할 수 있습니까?

**A**: GOOGLETRANSLATE에서 사용되는 전체 로케일 목록은 [Google 공식 문서](https://cloud.google.com/translate/docs/languages)를 참조하십시오.

## 추가 참조

{{see-more-forms-eds}}

