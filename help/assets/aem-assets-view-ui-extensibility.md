---
title: AEM Assets 보기 UI 확장성
description: AEM Assets 보기의 UI 확장성 기능에 대해 알아봅니다. AEM Assets 보기 UI를 사용하면 특정 비즈니스 요구 사항을 충족하도록 사용자 지정 UI 구성 요소를 추가할 수 있습니다.
feature: App Builder
role: User, Developer
exl-id: a11f7043-17cf-4331-b76c-d3db099c2411
source-git-commit: af7e6ab40212dfa3d91cda80a76b1b6b01dd65a3
workflow-type: tm+mt
source-wordcount: '598'
ht-degree: 3%

---

# AEM Assets 보기 UI 확장성{#AEM-Assets-View-UI-Extensibility}

| [모범 사례 검색](/help/assets/search-best-practices.md) | [메타데이터 모범 사례](/help/assets/metadata-best-practices.md) | [Content Hub](/help/assets/product-overview.md) | [OpenAPI 기능 포함 Dynamic Media](/help/assets/dynamic-media-open-apis-overview.md) | [AEM Assets 개발자 설명서](https://developer.adobe.com/experience-cloud/experience-manager-apis/) |
| ------------- | --------------------------- |---------|----|-----|

AEM Assets 보기에는 UI 확장성 기능이 있습니다. 이 기능을 사용하면 사용자가 Assets 보기의 기본 기능이 충족하지 않는 특정 비즈니스 요구 사항을 충족하도록 AEM Assets 보기 UI에 사용자 지정 UI 구성 요소를 추가할 수 있습니다. 이 확장성 기능은 조직이 특정 워크플로우 및 요구 사항에 맞게 인터페이스를 조정할 수 있도록 하는 AEM Assets 보기의 유연성을 향상시킵니다.
자산, 폴더 및 컬렉션 수준에 확장을 추가할 수 있습니다. 추가된 확장은 에셋, 컬렉션 또는 폴더 세부 사항 페이지의 전용 패널 내에 표시됩니다.

>[!IMPORTANT]
>
> * AEM Assets 보기 UI 확장은 [Assets Ultimate](/help/assets/assets-ultimate-overview.md)에서 사용할 수 있습니다.
> * Assets View UI 확장은 Beta 릴리스로 사용할 수 있습니다. Assets 보기 UI 확장성에 일찍 액세스하려면 [Adobe 고객 지원 사례를 만들어 제출](https://helpx.adobe.com/kr/enterprise/using/support-for-experience-cloud.html)하십시오.
> * 세부 피드백 옵션을 확장하고 문제 보고를 클릭하여 설명서 피드백을 제공할 수 있습니다.

## <a id="1"></a> Assets 보기에 액세스하는 방법

다음과 같은 방법으로 Assets 보기에 액세스합니다.
![access-assets-view-ui](/help/assets/assets/access-assets-view.jpg)

## Assets 보기 UI에서 UI 확장은 어디에 표시됩니까? {#ui-extensibility-panel-assets-view}

Assets 보기에서 에셋, 폴더 또는 컬렉션의 세부 정보 페이지로 이동합니다. 이 세부 정보 페이지에는 추가된 UI 확장을 표시하는 전용 패널이 있습니다.
![내 작업 공간](/help/assets/assets/my-workspace-assets-view3.png)


## 확장성 구성 요소를 추가하기 위한 사전 요구 사항

* [Assets 보기에 액세스](#1).
* 기본적으로 [Assets Ultimate](/help/assets/assets-ultimate-overview.md)에 포함된 [Adobe 앱 빌더](https://developer.adobe.com/app-builder/docs/overview/)에 액세스합니다.
* 조직 내에서 시스템 관리자 역할의 개발자에게 권한이 부여됩니다. 자세한 내용은 [this](https://developer.adobe.com/uix/docs/guides/get-access/)을(를) 참조하십시오.
* Adobe IO 명령줄 도구(AIO CLI)가 로컬 시스템에 설치되어 있어야 합니다. 이 도구는 확장 프로젝트를 만들고 배포하는 데 필수적입니다. 자세한 내용은 [this](https://developer.adobe.com/app-builder/docs/getting_started/#local-environment-set-up)을(를) 참조하십시오.
* JavaScript, Node.js 및 React 기술에 대한 올바른 이해입니다.

## Assets 보기 UI에서 UI 확장성 구성 요소 추가{#Adding-UI-Extensibility-Component-on-Assets-View}

1. UI 확장 및 App Builder Adobe 프레임워크에 대한 필수 정보는 [시작하기](https://developer.adobe.com/uix/docs/getting-started/)를 참조하십시오. UI 확장성을 통해 Adobe Experience Cloud 서비스 내에서 사용자 지정 논리 및 UI를 통합하는 방법을 알아보고 UI 확장을 구현하기 위한 아키텍처 및 워크플로를 이해합니다.
1. 로컬 환경 설정, 로컬 미리 보기, 게시 및 관리를 포함하여 UI 확장성에 대한 일반 정보는 [안내서](https://developer.adobe.com/uix/docs/guides/)를 참조하십시오.
1. AEM Assets 보기용 UI 확장을 개발하는 데 필요한 기본 사항을 이해하려면 [확장 만들기의 일반적인 개념](https://developer.adobe.com/uix/docs/services/aem-assets-view/api/commons/)을 참조하십시오.
1. Assets 보기 인터페이스에 사용자 지정 사이드 패널을 추가합니다. 호스트 애플리케이션(Assets 보기)은 이러한 패널을 관리하여 전환 및 딥링크와 같은 UI 상호 작용을 처리합니다. 확장은 `aem/assets/details/1` 확장 지점을 사용하여 패널 ID, 제목 및 콘텐츠 URL과 같은 속성을 지정하는 사용자 지정 패널을 통합합니다. 개발자는 `getPanels()` 메서드로 사용자 지정 패널을 등록하고 사용자 지정 콘텐츠를 표시하도록 빌드 경로를 설정합니다. API 참조 및 코드 예제를 포함한 자세한 구현은 [자세히 보기](https://developer.adobe.com/uix/docs/services/aem-assets-view/api/details-view/)를 참조하십시오.
1. 첫 번째 UI 확장을 만들어 Assets 보기에서 직접 로컬 환경을 설정하고 UI 확장을 개발하는 프로세스를 경험하십시오. 자세한 내용은 [단계별 AEM Assets 보기 확장 개발](https://developer.adobe.com/uix/docs/services/aem-assets-view/extension-development/)을 참조하십시오.
1. AIO CLI를 사용하여 앱을 설정하여 기본 확장 구조 및 필수 코드를 생성합니다. 자세한 내용은 [AEM Assets 보기에 대한 코드 생성](https://developer.adobe.com/uix/docs/services/aem-assets-view/code-generation/)을 참조하십시오.
1. 확장을 로컬에서 테스트하여 배포하기 전에 예상대로 작동하는지 확인합니다. 완전히 격리된 환경 또는 부분 격리된 환경에서 확장을 실행하고 테스트를 위해 프로덕션 AEM Assets 보기에 확장을 연결합니다. 자세한 내용은 [문제 해결 - AEM Assets 보기 확장성](https://developer.adobe.com/uix/docs/services/aem-assets-view/debug/)을 참조하십시오.
