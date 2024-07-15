---
title: 적응형 양식 기반의 핵심 구성 요소를 번역하려면 어떻게 해야 합니까?
description: AEM Forms에서 양식 데이터 모델(FDM)을 만들고, 샘플 데이터 및 서비스로 모델을 테스트하며, 모델에 대해 다양한 옵션을 구성하는 방법에 대해 알아봅니다.
feature: Adaptive Forms, Core Components
exl-id: ad46bf0f-e6ec-4c52-9695-5768a9968e16
role: User, Developer
source-git-commit: 2b76f1be2dda99c8638deb9633055e71312fbf1e
workflow-type: tm+mt
source-wordcount: '885'
ht-degree: 4%

---

# 기계 번역 또는 사람 번역을 사용하여 적응형 양식 기반의 핵심 구성 요소 번역 {#using-aem-translation-workflow-to-localize-adaptive-forms-and-document-of-record}

현지화된 양식을 통해 전 세계 다양한 지역의 대상자를 지원할 수 있습니다. Adobe Experience Manager 번역 워크플로를 통해 적응형 Forms 및 해당 기록 문서 를 현지화할 수 있습니다. **기계 번역** 또는 **사람 번역자**&#x200B;를 사용하여 적응형 양식을 지역화할 수 있습니다.

## 기계 번역을 사용하여 적응형 양식 및 기록 문서 번역 {#localizing-an-adaptive-form-and-document-of-record-using-machine-translation}

기계 번역 서비스는 적응형 양식 및 [기록 문서](/help/forms/generate-document-of-record-core-components.md)에서 콘텐츠를 즉시 번역합니다. Microsoft Translator 버전을 사용하도록 AEM Forms as a Cloud Service 평가판이 사전 구성되어 있습니다. 다음 단계를 수행하여 적응형 Forms 및 기록 문서에 대한 기계 번역을 활성화합니다.

1. AEM Forms UI에서 양식을 선택하고 **[!UICONTROL 사전 추가]** 옵션을 선택합니다.
1. 번역 프로젝트에 사전 추가 화면에서 **[!UICONTROL 프로젝트]** 옵션을 사용합니다.

   * 번역 프로젝트를 만들려면 **[!UICONTROL 새 번역 프로젝트 만들기]** 옵션을 선택하고 **프로젝트 제목** 필드에서 제목을 지정합니다. 예, `Government Reference Site - German locale.`
   * 기존 번역 프로젝트에 새 사전을 추가하려면 **[!UICONTROL 기존 번역 프로젝트에 추가]** 옵션을 선택하고 **[!UICONTROL 기존 번역 프로젝트]**&#x200B;를 선택하십시오.
1. **대상 언어** 필드에 로케일(예: `German(de)`)을 지정하십시오. 여러 로케일을 지정할 수 있습니다. 양식이 **타겟 언어** 필드에 지정된 모든 로케일로 번역됩니다. **완료**&#x200B;를 클릭합니다.
1. [사전 추가] 대화 상자에서 **프로젝트 열기**&#x200B;를 클릭합니다.
1. 프로젝트 화면에서 생성된 프로젝트를 클릭합니다. 예를들어 **정부 참조 사이트 - 독일어 로케일** 타일을 클릭합니다.
1. **번역 작업** 타일에서 ![aem62forms_downarrow](assets/aem62forms_downarrow.png) 아이콘을 클릭하고 **시작**&#x200B;을 클릭합니다. 타일의 상태가 초안으로 변경됩니다. 번역이 완료되면 상태가 **승인됨**(으)로 변경됩니다. 몇 분 후 페이지를 새로 고치고 상태를 확인합니다.

   ![번역 시작](/help/forms/assets/adaptive-forms-core-components-start-translation.png)
1. **번역 작업** 타일에서 상태가 **승인됨**(으)로 변경된 후 ![aem62forms_downarrow](assets/aem62forms_downarrow.png) 아이콘을 클릭하고 **완료**&#x200B;를 클릭하십시오.

1. 현지화된 양식을 미리 보려면 AEM Forms UI에서 현지화된 양식을 선택합니다. **[!UICONTROL 미리 보기]** >**[!UICONTROL HTML으로 미리 보기]**&#x200B;를 클릭합니다. 양식의 URL에 `afAcceptLang=<locale code>`을(를) 추가한 후 양식을 다시 여십시오. 예를들어 독일어 버전의 양식을 열려면 `afAcceptLang=de`을(를) 추가합니다.


   >[!NOTE]
   >
   >* 브라우저 창에서 지역화된 버전의 양식을 열기 전에 브라우저의 로케일이 양식의 로케일과 일치하도록 설정되어 있는지 확인하십시오. 예를 들어, 양식이 독일어(de)로 번역된 경우 브라우저의 로케일을 독일어(de)로 설정합니다.
   >* 적응형 양식 구성 요소는 RTL(오른쪽에서 왼쪽) 언어를 지원하지 않습니다. 예를 들면, 히브리어.

<!-- 
   Along with the Adaptive form, the auto-generated document of record is also localized.

   For more information on Document of Record settings and configuration, see:

   [Document of Record Template](/help/forms/using/generate-document-of-record-for-non-xfa-based-adaptive-forms.md#p-document-of-record-template-configuration-p)

   [Document of Record settings](/help/forms/using/generate-document-of-record-for-non-xfa-based-adaptive-forms.md#p-document-of-record-settings-p)

1. [Customize the branding information of the document of record](/help/forms/using/generate-document-of-record-for-non-xfa-based-adaptive-forms.md) and ensure that the browser locale is set to the same language to which you have localized the Adaptive Form using machine language. The browser locale helps localize the branding information in the document of record.
1. To view the localized document of record, select Generate Preview. The document of record PDF is generated and opened in a new tab in your browser.

-->

## 사람 번역을 사용하여 적응형 양식 및 해당 기록 문서 현지화 {#localizing-an-adaptive-form-and-its-document-of-record-using-human-translation}

사람 번역에서는 콘텐츠를 전문 번역사가 번역할 수 있도록 번역 공급업체로 보냅니다. 번역이 완료되면 번역된 콘텐츠는 반환되어 AEM으로 가져와집니다. 번역 공급업체를 AEM과 통합하면 콘텐츠는 자동으로 AEM과 번역 공급업체 간 전송됩니다.

번역을 위해 XLIFF 형식의 파일이 포함된 사전을 전문 번역자와 공유합니다. 사전에는 각 로케일에 대한 별도의 XLIFF 파일이 포함되어 있습니다. 각 XLIFF 파일에는 최종 사용자와 해당 지역화된 텍스트의 자리 표시자에 표시되는 텍스트가 포함되어 있습니다.

사람 번역기를 사용하여 양식 및 해당 기록 문서를 현지화하려면 다음 단계를 수행하십시오.

1. AEM Forms UI에서 양식을 선택하고 **[!UICONTROL 사전 추가]** 옵션을 선택합니다.
1. 번역 프로젝트에 사전 추가 화면에서 **[!UICONTROL 프로젝트]** 옵션을 사용합니다.

   * 번역 프로젝트를 만들려면 **[!UICONTROL 새 번역 프로젝트 만들기]** 옵션을 선택하고 **프로젝트 제목** 필드에서 제목을 지정합니다. 예, `Government Reference Site - German locale.`
   * 기존 번역 프로젝트에 새 사전을 추가하려면 **[!UICONTROL 기존 번역 프로젝트에 추가]** 옵션을 선택하고 **[!UICONTROL 기존 번역 프로젝트]**&#x200B;를 선택하십시오.
1. **대상 언어** 필드에 로케일(예: `German(de)`)을 지정하십시오. 여러 로케일을 지정할 수 있습니다. 양식이 **타겟 언어** 필드에 지정된 모든 로케일로 번역됩니다. **완료**&#x200B;를 클릭합니다.
1. [사전 추가] 대화 상자에서 **프로젝트 열기**&#x200B;를 클릭합니다.
1. 프로젝트 화면에서 생성된 프로젝트를 클릭합니다. 예를들어 **정부 참조 사이트 - 독일어 로케일** 타일을 클릭합니다.
1. **요약** 타일 하단에서 **줄임표**&#x200B;를 클릭합니다. 번역 프로젝트 속성 화면이 열립니다.
1. **번역 프로젝트 속성** 화면 맨 위에서 **[!UICONTROL 고급]** 탭을 엽니다. **[!UICONTROL 번역 필드]**&#x200B;에 대해 **[!UICONTROL 사람 번역]**&#x200B;을 선택하세요. 화면 상단의 **저장 및 닫기**&#x200B;를 클릭합니다.
1. **번역 작업** 타일에서 ![aem62forms_downarrow](assets/aem62forms_downarrow.png) 아이콘을 클릭하고 **내보내기**를 클릭합니다. 내보내기 대화 상자에서 내보낸 파일 다운로드 옵션을 클릭합니다. .zip 파일을 다운로드합니다.
   ![번역 파일 내보내기](/help/forms/assets/adaptive-forms-core-components-start-translation-export.png)
1. 다운로드한 .zip 파일의 압축을 풉니다. 추출된 폴더에는 두 개의 파일이 있습니다.
   * translation_export_summary.xml
   * [form-fields-file].xml
1. 편집할 [form-fields-file].xml을 엽니다. 양식 필드에 대한 현지화된 문자열 및 메시지를 추가합니다. 파일을 저장하고 닫습니다.
1. translation_export_summary.xml 및 [form-fields-file].xml 파일을 압축합니다.
1. **번역 작업** 타일에서 ![aem62forms_downarrow](assets/aem62forms_downarrow.png) 아이콘을 클릭하고 **가져오기**&#x200B;를 클릭합니다. [form-fields-file].xml이 포함된 아카이브를 선택하십시오. (양식 필드에 대한 현지화된 문자열 및 메시지 포함)

   ![번역 파일 가져오기](/help/forms/assets/adaptive-forms-core-components-start-translation-import.png)

1. 현지화된 양식을 미리 보려면 AEM Forms UI에서 현지화된 양식을 선택합니다. **[!UICONTROL 미리 보기]** >**[!UICONTROL HTML으로 미리 보기]**&#x200B;를 클릭합니다. 양식의 URL에 `afAcceptLang=<locale code>`을(를) 추가한 후 양식을 다시 여십시오. 예를들어 독일어 버전의 양식을 열려면 `afAcceptLang=de`을(를) 추가합니다.

## 추가 참조 {#see-also}

{{see-also}}