---
title: AEM 번역 워크플로를 사용하여 적응형 Forms 및 기록 문서를 현지화하려면 어떻게 해야 합니까?
description: AEM 번역 워크플로를 사용하여 적응형 Forms 및 기록 문서를 현지화하는 방법에 대해 알아봅니다.
uuid: 6c87a283-0203-4cf7-989a-3770ddbbbd6e
content-type: reference
topic-tags: develop
discoiquuid: f5642571-9657-4ca1-93c5-4ae2eb91e967
noindex: true
source-git-commit: 2d4ffd5518d671a55e45a1ab6f1fc41ac021fd80
workflow-type: tm+mt
source-wordcount: '533'
ht-degree: 1%

---


# 적응형 Forms 및 기록 문서 현지화{#using-aem-translation-workflow-to-localize-adaptive-forms-and-document-of-record}

현지화된 양식을 통해 전 세계 다양한 지역의 대상자를 지원할 수 있습니다. Adobe Experience Manager 번역 워크플로를 통해 적응형 Forms 및 해당 기록 문서 를 현지화할 수 있습니다. 다음을 사용할 수 있습니다. **기계 번역** 또는 **사람 번역가** 을 클릭하여 적응형 양식을 현지화합니다.

이 문서에서는 적응형 Forms 및 기록 문서와 함께 AEM 번역 워크플로를 사용하는 프로세스에 대해 설명합니다.

## 기계 번역을 사용하여 적응형 양식 및 기록 문서 현지화 {#localizing-an-adaptive-form-and-document-of-record-using-machine-translation}

기계 번역 서비스는 적응형 양식 및 기록 문서에서 콘텐츠를 즉시 번역합니다. [!DNL AEM Forms] 은(는) 의 체험판 버전을 사용하도록 사전 구성되어 있습니다. [!DNL Microsoft Translator] 기계 번역. 다음 단계를 수행하여 적응형 Forms 및 기록 문서에 대한 기계 번역을 활성화합니다.

1. 다음에서 [!DNL AEM Forms] UI에서 양식을 선택하고 **사전 추가** 옵션을 선택합니다.
1. 위치 **사전을 번역 프로젝트에 추가** 화면에서 **새 번역 프로젝트 만들기** 또는 **기존 번역 프로젝트에 추가** 옵션을 선택합니다.
1. 다음에서 **프로젝트 제목** 필드, 제목을 지정합니다. 예, `Government Reference Site - German locale.`
1. 다음에서 **타겟 언어** 필드, 로케일 지정(예: `German(de)`), 클릭 **완료**. 여러 로케일을 지정할 수 있습니다. 양식이 다음에 지정된 모든 로케일로 변환됩니다. **타겟 언어** 필드.
1. Dictionary Added 대화 상자에서 **프로젝트 열기**. 프로젝트 화면에서 생성된 프로젝트를 엽니다.
1. 다음을 클릭합니다. **생략 부호** 의 맨 아래에 **번역 요약** 타일. 번역 요약 화면이 열립니다.
1. 다음을 클릭합니다. **편집** 아이콘(맨 위에 있음) **번역 요약** 화면. 를 엽니다. **번역** 을(를) 탭하고 **번역 방법** 화면. 적절한 항목 선택 **번역 공급업체** 및 **클라우드 구성**. 다음을 클릭합니다. **완료** 화면 맨 위에 있는 아이콘.
1. 다음에서 **번역 작업** 타일에서 ![aem62forms_downarrow](assets/aem62forms_downarrow.png) 아이콘 및 클릭 **시작**. 타일의 상태가 초안으로 변경됩니다. 번역이 완료되면 상태가 (으)로 변경됩니다. **검토 준비됨**. 몇 분 후 페이지를 새로 고치고 상태를 확인합니다.
1. 상태가 다음으로 변경된 후 **검토 준비됨** 다음에 있음 **번역 작업** 타일을 지정하고 브라우저 창에서 양식을 엽니다. 지역화된 버전의 양식이 표시됩니다.

   >[!NOTE]
   >
   >* 브라우저 창에서 지역화된 버전의 양식을 열기 전에 브라우저의 로케일이 양식의 로케일과 일치하도록 설정되어 있는지 확인하십시오. 예를 들어, 양식이 독일어(de)로 번역된 경우 브라우저의 로케일을 독일어(de)로 설정합니다.
   >* 적응형 양식 구성 요소는 RTL(오른쪽에서 왼쪽) 언어를 지원하지 않습니다. 예를 들면, 히브리어.

   적응형 양식과 함께 자동 생성된 기록 문서 도 현지화됩니다.

   기록 문서 설정 및 구성에 대한 자세한 내용은 다음을 참조하십시오.

[기록 문서 템플릿 구성](generate-document-of-record-for-non-xfa-based-adaptive-forms.md#p-document-of-record-template-configuration-p)

[기록 문서 설정](generate-document-of-record-for-non-xfa-based-adaptive-forms.md#p-document-of-record-settings-p)

1. [기록 문서의 브랜딩 정보 사용자 정의](generate-document-of-record-for-non-xfa-based-adaptive-forms.md) 및 브라우저 로케일이 시스템 언어를 사용하여 적응형 양식을 지역화한 것과 동일한 언어로 설정되어 있는지 확인합니다. 브라우저 로케일은 기록 문서의 브랜딩 정보를 현지화하는 데 도움이 됩니다.
1. 현지화된 기록 문서를 보려면 미리보기 생성을 선택합니다. 기록 문서 PDF이 생성되고 브라우저의 새 탭에서 열립니다.

<!-- ## Localizing an Adaptive Form and its Document of Record using Human Translation {#localizing-an-adaptive-form-and-its-document-of-record-using-human-translation}

In Human translation the content is sent to a translation provider and translated by professional translators. When complete, the translated content is returned and imported into AEM. When your translation provider is integrated with AEM, content is automatically sent between AEM and the translation provider.

For translation, a dictionary containing files in XLIFF format is shared with the professional translators. The dictionary includes a separate XLIFF file for each locale. Each XLIFF file contains text that is displayed to the end users and placeholders for the corresponding localized text.

Perform the following steps to localize a form and its Document of Record using Human Translators:

1. [Connect AEM with your translation service provider](/help/sites-administering/tc-tic.md) and [create translation integration framework configurations](/help/sites-administering/tc-tic.md).

1. [Associate the pages of your language master](/help/sites-administering/tc-tic.md) with the translation service and framework configurations.

1. [Identify the type of content](/help/sites-administering/tc-rules.md) to translate.

1. [Prepare the content for translation](/help/sites-administering/tc-prep.md) by authoring the language master and creating the root pages of language copies.

1. [Create translation projects](/help/sites-administering/tc-manage.md) to gather the content to translate and to prepare the translation process.

1. Use the translation projects to [manage the content translation process](/help/sites-administering/tc-manage.md).

>[!NOTE]
>
>* Adaptive Form components do not support right to left (RTL) languages. For example, Hebrew.
> -->

