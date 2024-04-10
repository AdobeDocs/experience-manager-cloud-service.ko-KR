---
title: AEM Forms Edge Delivery Services 양식 번역 및 현지화
description: AEM Forms Edge Delivery Services 양식 번역 및 현지화
feature: Edge Delivery Services
hide: true
hidefromtoc: true
exl-id: 8a0c826f-8acc-4a00-bd84-7b0df9a82457
source-git-commit: eadfc3d448bd2fadce08864ab65da273103a6212
workflow-type: tm+mt
source-wordcount: '543'
ht-degree: 6%

---


# AEM Forms Edge Delivery Services 양식 번역 및 현지화

Edge Delivery Services에서 양식 번역에는 정확성, 명확성 및 일관성에 중점을 두고 양식 콘텐츠를 한 언어에서 다른 언어로 변환하는 작업이 포함됩니다. 번역된 또는 지역화된 양식을 사용하면 다양한 지리적 위치에서 광범위한 대상자를 연결할 수 있으므로 사용자 경험을 향상시키고 다양한 언어 환경 설정에서 더 나은 커뮤니케이션을 용이하게 합니다.


이 문서의 마지막 부분에서는 다음 내용을 학습합니다.

* [Google 드라이브 내 양식 번역](#translate-form-google-drive)
* [SharePoint 사이트 내 양식 번역](#translate-form-sharepoint)

## Google 드라이브 내 양식 번역 {#translate-form-google-drive}

다음 `GOOGLETRANSLATE` Google 시트의 함수 는 기본 제공 번역 도구에 탭하여 양식을 번역하고 Google 시트 내에서 직접 텍스트를 한 언어에서 다른 언어로 변경합니다. Google 드라이브 내에서 양식을 번역하려면:

1. Google 드라이브의 AEM 프로젝트 폴더로 이동하여 Google 시트를 엽니다.
2. 기존 시트 이름 바꾸기(`shared-default`) 받는 사람 `shared-en`.
3. 이름이 인 시트 추가 `shared-default`. 다음 `shared-default` 시트에는 특정 언어로의 현지화에 대한 콘텐츠가 포함되어 있습니다.
4. 지역화된 콘텐츠 추가 `shared-default` 를 사용한 시트 `GOOGLETRANSLATE` 함수.
수식을 사용하여 셀의 D2 내용을 `shared-en` 다음 내에서 프랑스어로 표시 `shared-default` 시트. 다음은 사용할 수식입니다.
   `=GOOGLETRANSLATE('shared-en'!D2,"en","fr")`

   ![조회 스프레드시트 번역](/help/forms/assets/translate-enquiry-spreadsheet.png)

5. 다음을 사용하여 시트 미리보기 및 게시 [AEM Sidekick](https://www.aem.live/developer/tutorial#preview-and-publish-your-content).

다음을 참조할 수 있습니다 [스프레드시트](/help/forms/assets/enquirytranslate.xlsx) 다음에 대한 양식 정의 포함 `enquiry` 영어에서 불어로 번역된 양식.

![질의 번역 양식](/help/forms/assets/translate-form-french.png)

프랑스어 번역이 포함된 양식을 볼 수 있는 아래 URL을 참조하십시오. https://main--portal--wkndforms.hlx.live/enquirytranslate

## SharePoint 사이트 내 양식 번역{#translate-form-sharepoint}

Microsoft® SharePoint 사이트에서 양식을 번역하려면 번역 서비스를 사용하여 필드의 레이블을 수동으로 변경해야 합니다. SharePoint 사이트 내에서 양식을 번역하려면 다음 작업을 수행하십시오.

1. Microsoft® SharePoint의 AEM 프로젝트 폴더로 이동하여 스프레드시트를 엽니다.
2. 기존 시트 이름 바꾸기(`shared-default`) 받는 사람 `shared-en`.
3. 이름이 인 시트 추가 `shared-default`. 다음 `shared-default` 시트에는 특정 언어로의 현지화에 대한 콘텐츠가 포함되어 있습니다.
4. 지역화된 콘텐츠 추가 `shared-default` 수동으로 작성하십시오.

   ![조회 스프레드시트 번역](/help/forms/assets/translate-enquiry-sp-spreadsheet.png)

5. 다음을 사용하여 시트 미리보기 및 게시 [AEM Sidekick](https://www.aem.live/developer/tutorial#preview-and-publish-your-content).

다음을 참조하십시오. [스프레드시트](/help/forms/assets/enquirytranslate-sp.xlsx) 다음에 대한 양식 정의 포함 `enquiry` 영어에서 불어로 번역된 양식.

![질의 번역 양식](/help/forms/assets/translate-form-french.png)

프랑스어 번역이 포함된 양식을 볼 수 있는 아래 URL을 참조하십시오. https://main--wefinance--wkndforms.hlx.live/enquirytranslate

## 알려진 문제 {#known-issues}

* 양식의 레이블은 의 지정된 현지화된 언어로 번역됩니다 `shared-default` 시트는 표시되지만 오류 메시지는 브라우저의 기본 언어로 표시됩니다.

  ![오류 메시지](/help/forms/assets/translate-error-message.png)

* 캘린더를 열면 캘린더 드롭다운이 브라우저의 기본 언어로 표시됩니다.

  ![오류 메시지](/help/forms/assets/translate-calender-display.png)


## 자주 묻는 질문 {#faq}

**Q**: 양식에 지정된 현지화 언어로 입력을 입력하려면 어떻게 해야 합니까?

**A**: 지역화된 특정 언어로 텍스트를 입력하려면 장치에서 키보드 설정을 조정하십시오. 수행 방법에 대한 지침은 다음 링크를 참조하십시오.

* [다른 언어로 입력을 받도록 Mac 설정](https://support.apple.com/en-in/guide/mac-help/mchlp1406/mac)
* [다른 언어로 입력하도록 Windows 설정](https://support.microsoft.com/en-us/windows/manage-the-input-and-display-language-settings-in-windows-12a10cb4-8626-9b77-0ccb-5013e0c7c7a2#:~:text=Select%20the%20Start%20%3E%20Settings%20%3E%20Time,you%20want%2C%20then%20select%20Options)
* [다른 언어로 입력하도록 Android 또는 iPhone/iPad 설정](https://support.google.com/gboard/answer/7068494?hl=en&amp;co=GENIE.Platform%3DAndroid)


**Q**: 다음에서 사용되는 로케일 목록을 검색하려면 어떻게 합니까? `GOOGLETRANSLATE` 기능?

**A**: 다음을 의미할 수 있습니다. [Google 공식 설명서](https://cloud.google.com/translate/docs/languages) GOOGLETRANSLATE에 사용되는 로케일의 전체 목록을 보려면 다음을 수행하십시오.

## 추가 참조

{{see-more-forms-eds}}

