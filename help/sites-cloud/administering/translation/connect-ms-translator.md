---
title: Microsoft Translator에 연결
description: AEM을 Microsoft Translator에 즉시 연결하여 번역 워크플로우를 자동화하는 방법을 알아봅니다.
feature: 언어 복사
role: Admin
exl-id: ca3c50f9-005e-4871-8606-0cfd3ed21936
source-git-commit: 24a4a43cef9a579f9f2992a41c582f4a6c775bf3
workflow-type: tm+mt
source-wordcount: '478'
ht-degree: 1%

---

# Microsoft Translator에 연결 {#connecting-to-microsoft-translator}

AEM 페이지 콘텐츠 또는 자산을 번역할 때 Microsoft 번역 계정을 사용하려면 [Microsoft Translator](https://hub.microsofttranslator.com) 클라우드 서비스에 대한 구성을 만드십시오.

>[!NOTE]
>
>AEM에서는 매월 최대 200,000개의 무료 번역 문자를 사용할 수 있는 평가판 Microsoft Translation 계정을 제공합니다. 프로덕션 시스템에 적합한 계정 구독을 얻으려면 [Microsoft Translator 평가판 라이선스 구성 업그레이드](#upgrading-the-microsoft-translator-trial-license-configuration)를 참조하십시오.

| 속성 | 설명 |
|---|---|
| 번역 레이블 | 번역 서비스의 표시 이름입니다 |
| 번역 기여도 분석 | (선택 사항) 사용자가 생성한 컨텐츠의 경우, 번역된 텍스트 옆에 표시되는 속성(예: `Translations by Microsoft`) |
| 작업 공간 ID | (선택 사항) 사용할 사용자 지정된 Microsoft Translator 엔진의 ID입니다 |
| 가입 키 | Microsoft Translator용 Microsoft 구독 키 |

구성을 만든 후 [활성화해야 합니다](#activating-the-translator-service-configurations).

다음 절차에서는 Microsoft Translator 구성을 만듭니다.

1. [탐색 패널에서 ](/help/sites-cloud/authoring/getting-started/basic-handling.md#first-steps) **도구** -> **Cloud Services** -> **번역 Cloud Services**&#x200B;을 클릭하거나 탭합니다.
1. 구성을 만들 위치로 이동합니다. 일반적으로 사이트 루트에 있거나 전역 기본 구성일 수 있습니다.
1. **만들기** 단추를 탭하거나 클릭합니다.
1. 구성을 정의합니다.
   1. 드롭다운에서 **Microsoft Translator**&#x200B;를 선택합니다.
   1. 구성에 사용할 제목을 입력합니다. 제목은 페이지 속성 드롭다운 목록뿐만 아니라 Cloud Services 콘솔에서 구성을 식별합니다.
   1. 구성을 저장하는 저장소 노드에 사용할 이름을 입력합니다(선택적).

   ![번역 구성 만들기](../assets/create-translation-config.png)

1. **만들기**&#x200B;를 클릭합니다.
1. **구성 편집** 창에서 이전 테이블에 설명된 번역 서비스의 값을 제공합니다.

   ![번역 구성 편집](../assets/edit-translation-config.png)

1. **Connect**&#x200B;를 탭하거나 클릭하여 연결을 확인합니다.
1. **저장 및 닫기**&#x200B;를 탭하거나 클릭합니다.

## Microsoft Translator 평가판 라이선스 구성 업그레이드 {#upgrading-the-microsoft-translator-trial-license-configuration}

Microsoft Translation 구성 페이지에서는 운영 시스템에 적합한 계정 구독을 얻기 위해 Microsoft 웹 사이트에 대한 편리한 링크를 제공합니다.

1. [탐색 패널에서 ](/help/sites-cloud/authoring/getting-started/basic-handling.md#first-steps)도구&#x200B;**->** Cloud Services **->**&#x200B;번역 Cloud Services **을 탭하거나 클릭합니다.**
1. 기존 Microsoft Translator 구성을 탭하거나 클릭합니다.
1. **편집**&#x200B;을 탭하거나 클릭합니다.
1. **구성 편집** 창에서 **구독 업그레이드**&#x200B;를 탭하거나 클릭합니다. 서비스에 대한 세부 정보가 포함된 Microsoft 웹 페이지가 열립니다.

## Microsoft Translator 엔진 사용자 지정 {#customizing-your-microsoft-translator-engine}

Microsoft Translation 구성 페이지에서는 Microsoft Translator 엔진을 사용자 지정하기 위해 Microsoft 웹 사이트에 대한 편리한 링크를 제공합니다.

1. [탐색 패널에서 ](/help/sites-cloud/authoring/getting-started/basic-handling.md#first-steps)도구&#x200B;**->** Cloud Services **->**&#x200B;번역 Cloud Services **을 탭하거나 클릭합니다.**
1. 기존 Microsoft Translator 구성을 탭하거나 클릭합니다.
1. **편집**&#x200B;을 탭하거나 클릭합니다.
1. **구성 편집** 창에서 **번역기 사용자 지정**&#x200B;을 탭하거나 클릭합니다. 열려 있는 Microsoft 웹 페이지를 사용하여 서비스를 사용자 지정합니다.

## 번역기 서비스 구성 활성화 {#activating-the-translator-service-configurations}

게시 인스턴스에 복제된 번역된 컨텐츠를 지원하려면 클라우드 서비스 구성을 활성화해야 합니다. [트리 게시](/help/sites-cloud/authoring/fundamentals/publishing-pages.md#publishing-and-unpublishing-a-tree) 메서드를 사용하여 Microsoft Translator 구성을 저장하는 저장소 노드를 활성화합니다. 노드는 다음 상위 노드 아래에 있습니다.

* `/libs/settings/cloudconfigs/translation/msft-translation`
