---
title: ' [!DNL AEM Assets View]에서 UI 확장성 사용'
description: ' [!DNL AEM Assets View]. [!DNL AEM Assets View] UI의 UI 확장성 기능에 대해 알아봅니다. UI를 통해 특정 비즈니스 요구 사항을 충족하는 사용자 지정 UI 구성 요소를 추가할 수 있습니다.'
feature: App Builder
role: User, Developer
exl-id: a11f7043-17cf-4331-b76c-d3db099c2411
source-git-commit: 9c1104f449dc2ec625926925ef8c95976f1faf3d
workflow-type: tm+mt
source-wordcount: '598'
ht-degree: 0%

---

# [!DNL AEM Assets View]에서 UI 확장성 사용 {#AEM-Assets-View-UI-Extensibility}

[!DNL AEM Assets View]은(는) UI 확장성을 지원하므로 [!DNL AEM Assets View]의 기본 기능에서 충족되지 않는 특정 워크플로 및 비즈니스 요구 사항에 대해 [!DNL Assets View] UI에 사용자 지정 UI 구성 요소를 추가할 수 있습니다. [!DNL AEM Assets View]의 이 UI 확장성 기능은 유연성을 향상시켜 조직에서 특정 워크플로 및 요구 사항에 맞게 인터페이스를 조정할 수 있도록 합니다.\
**자산**, **폴더** 및 **컬렉션** 수준에 확장을 추가할 수 있습니다. 추가된 확장은 **자산**, **컬렉션** 또는 **폴더** **[!UICONTROL 세부 정보]** 페이지의 전용 패널에 표시됩니다.

>[!IMPORTANT]
>
> * [[!DNL Assets Ultimate]](/help/assets/assets-ultimate-overview.md)에서 [!DNL AEM Assets View] UI 확장성을 사용할 수 있습니다.
> * [!DNL Assets view] UI 확장성에 액세스하려면 [고객 지원 사례를 만들어 제출 [!DNL Adobe] 하십시오](https://helpx.adobe.com/kr/enterprise/using/support-for-experience-cloud.html).
> * **[!UICONTROL 자세한 피드백 옵션]**&#x200B;을 확장하고 **[!UICONTROL 문제 보고]**&#x200B;를 클릭하여 문서 피드백을 제공할 수 있습니다.

## <a id="1"></a> Assets 보기에 액세스{#add-UI-Extensibility-in-AEM-Assets-View}

[!DNL Assets View]에 액세스하려면 아래 이미지에 언급된 단계를 따르십시오.
![access-assets-view-ui](/help/assets/assets/access-assets-view.jpg)

## [!DNL Assets View]에서 UI 확장 보기 {#ui-extensibility-panel-assets-view}

[!DNL Assets View] 내에서 자산, 폴더 또는 컬렉션의 **[!UICONTROL 세부 정보]** 페이지로 이동합니다. **[!UICONTROL 세부 정보]** 페이지에는 추가된 UI 확장이 전용 패널에 표시됩니다.
![내 작업 공간](/help/assets/assets/my-workspace-assets-view3.png)

## 확장성 구성 요소를 추가하기 위한 사전 요구 사항{#assets-view-ui-extensibility}

[!DNL Assets View UI]에 확장성 구성 요소를 추가하려면 다음 요구 사항을 충족하십시오.

* [액세스 대상 [!DNL Assets View]](#1).
* [[!DNL Adobe app builder]](https://developer.adobe.com/app-builder/docs/overview/)에 대한 액세스 권한.
* 조직 내 시스템 관리자 역할의 개발자에 대한 자격 부여. 자세한 내용은 [이 설명서](https://developer.adobe.com/uix/docs/guides/get-access/)를 참조하세요.
* [!DNL Adobe IO command line tool (AIO CLI)]이(가) 로컬 컴퓨터에 설치되어 있습니다. 이 도구는 확장 프로젝트를 만들고 배포하는 데 필수적입니다. 자세한 내용은 [첫 번째 App Builder 응용 프로그램 만들기](https://developer.adobe.com/app-builder/docs/get_started/app_builder_get_started/first-app#local-environment-set-up)&#x200B;(액세스를 위한 인증 필요)를 참조하십시오.
* [!DNL JavaScript], [!DNL Node.js] 및 [!DNL React] 기술을 잘 이해하고 있습니다.

## [!DNL Assets View]에 UI 확장성 구성 요소 추가 {#ui-extensibility-in-assets-view}

1. UI 확장 및 [!DNL Adobe App Builder] 프레임워크에 대한 필수 정보는 [시작하기](https://developer.adobe.com/uix/docs/getting-started/)를 참조하십시오. UI 확장성을 통해 [!DNL Adobe Experience Cloud services] 내에서 사용자 지정 논리와 UI를 통합하는 방법을 알아보고 UI 확장을 구현하기 위한 아키텍처 및 워크플로를 이해합니다.
1. 로컬 환경 설정, 로컬 미리 보기, 게시 및 관리를 포함하여 UI 확장성에 대한 일반 정보는 [안내서](https://developer.adobe.com/uix/docs/guides/)를 참조하십시오.
1. [!DNL AEM Assets View]의 UI 확장을 개발하는 데 필요한 기본 사항을 이해하려면 [확장을 만드는 일반적인 개념](https://developer.adobe.com/uix/docs/services/aem-assets-view/api/commons/)을 참조하십시오.
1. 사용자 지정 사이드 패널을 [!DNL Assets View] 인터페이스에 추가합니다. 호스트 응용 프로그램([!DNL Assets View])은 이러한 패널을 관리하여 전환 및 딥링크와 같은 UI 상호 작용을 처리합니다. 확장은 `aem/assets/details/1` 확장 지점을 사용하여 패널 ID, 제목 및 콘텐츠 URL과 같은 속성을 지정하는 사용자 지정 패널을 통합합니다. 개발자는 `getPanels()` 메서드로 사용자 지정 패널을 등록하고 사용자 지정 콘텐츠를 표시하도록 빌드 경로를 설정합니다. API 참조 및 코드 예제를 포함한 자세한 구현은 [자세히 보기](https://developer.adobe.com/uix/docs/services/aem-assets-view/api/details-view/)를 참조하십시오.
1. 로컬 환경을 설정하고 첫 번째 UI 확장을 만들어 [!DNL Assets View]에서 UI 확장을 개발하는 과정을 직접 경험하십시오. 자세한 내용은 [단계별 AEM Assets 보기 확장 개발](https://developer.adobe.com/uix/docs/services/aem-assets-view/extension-development/)을 참조하십시오.
1. AIO CLI를 사용하여 애플리케이션을 설정하여 기본 확장 구조 및 필수 코드를 생성합니다. 자세한 내용은 [코드 생성 대상 [!DNL AEM Assets View]](https://developer.adobe.com/uix/docs/services/aem-assets-view/code-generation/)을 참조하십시오.
1. 확장을 로컬에서 테스트하여 배포하기 전에 예상대로 작동하는지 확인합니다. 완전히 격리된 환경 또는 부분 격리된 환경에서 확장을 실행하고 테스트를 위해 프로덕션 [!DNL AEM Assets View]에 확장을 연결합니다. 자세한 내용은 [문제 해결 - [!DNL AEM Assets View] 확장성](https://developer.adobe.com/uix/docs/services/aem-assets-view/debug/)을 참조하십시오.

## Assets 보기에서 빠른 작업 및 작업 표시줄 사용자 지정 {#customize-quick-actions-and-actions-bar}

Assets 보기에서 에셋을 하나 이상 선택하면 표시되는 작업(작업 표시줄)을 사용자 지정할 수 있습니다. Assets 보기를 사용하면 에셋 카드에서 추가 옵션(...)을 클릭할 때 표시되는 작업을 사용자 지정할 수도 있습니다. 자세한 내용은 [보기 찾아보기](https://developer.adobe.com/uix/docs/services/aem-assets-view/api/browse-view/)를 참조하십시오.

## Assets 보기에서 사용자 지정 대화 상자 열기 {#open-custom-dialogs-assets-view}

Assets 보기는 선택한 텍스트로 사용자 지정 대화 상자를 여는 기능도 제공합니다. 텍스트에 링크를 추가할 수도 있습니다. 자세한 내용은 [모달 API](https://developer.adobe.com/uix/docs/services/aem-assets-view/api/commons/#modal-api)를 참조하십시오.
