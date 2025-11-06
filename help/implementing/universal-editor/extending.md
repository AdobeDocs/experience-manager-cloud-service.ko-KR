---
title: 범용 편집기 확장
description: 콘텐츠 작성자의 요구 사항을 지원하도록 범용 편집기의 기능을 확장하는 다양한 옵션에 대해 알아봅니다.
feature: Developing
role: Admin, Developer
exl-id: 2f487fa5-57a7-477a-ad68-590e6cc12f4e
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '581'
ht-degree: 100%

---

# 범용 편집기 확장 {#extending}

콘텐츠 작성자의 요구 사항을 지원하도록 범용 편집기의 기능을 확장하는 다양한 옵션에 대해 알아봅니다.

>[!TIP]
>
>또한 범용 편집기는 프로젝트 요구 사항을 더 잘 충족할 수 있는 여러 [사용자 정의 옵션](/help/implementing/universal-editor/customizing.md)을 제공합니다.

## 확장 {#extensions}

Adobe Experience Cloud 서비스인 범용 편집기의 UI는 App Builder 및 Experience Manager를 사용하여 확장할 수 있습니다. Adobe는 [Extension Manager](https://experience.adobe.com/aem/extension-manager)를 통해 프로젝트에 사용할 수 있는 많은 기본 제공 확장 기능을 제공합니다.

* **[AEM 다중 사이트 관리(MSM) 확장 기능](/help/sites-cloud/authoring/universal-editor/authoring.md#inheritance)**: 구성 요소 레벨에서 상속을 중단하거나 복원합니다.
* **[AEM 페이지 속성 확장 기능](/help/sites-cloud/authoring/universal-editor/authoring.md#page-properties)**: 범용 편집기에서 페이지의 페이지 속성 창에 액세스합니다.
* **[AEM Site Admin Extension](/help/sites-cloud/authoring/universal-editor/authoring.md#sites-console)**: 범용 편집기에서 해당 페이지 위치로 Sites Console을 엽니다.
* **[AEM 페이지 잠금 확장 기능](/help/sites-cloud/authoring/universal-editor/authoring.md#locking-pages)**: 범용 편집기에서 페이지 잠금 상태를 보고 변경합니다.
* **[AEM 워크플로 확장 기능](/help/sites-cloud/authoring/universal-editor/authoring.md#workflows)**: 범용 편집기에서 페이지 및 페이지 콘텐츠에 대한 워크플로를 시작합니다.
* **[AEM 범용 편집기 개발 로그인 확장 기능](/help/sites-cloud/authoring/universal-editor/authoring.md#developer-login)**: 로컬에서 개발할 때 로컬 AEM SDK에 쉽게 인증합니다.
* **[베리에이션 생성](/help/generative-ai/generate-variations-integrated-editor.md)**: 속성 패널에서 직접 생성형 AI를 사용하여 콘텐츠에 대한 베리에이션을 만듭니다.
* **[범용 편집기용 AEM 제품 선택기](https://developer.adobe.com/uix/docs/extension-manager/extension-developed-by-adobe/ue-product-picker/)**: 편집기에서 제품 데이터를 선택하거나 제거하여 Adobe Commerce 데이터를 통합합니다.
* **[범용 편집기 콘텐츠 초안](https://developer.adobe.com/uix/docs/extension-manager/extension-developed-by-adobe/universal-editor-content-drafts/)**: 여러 콘텐츠 초안을 만들고, 편집하고, 관리합니다.
* **[구성 가능한 자산 선택기](https://developer.adobe.com/uix/docs/extension-manager/extension-developed-by-adobe/configurable-asset-picker/)**: 편집된 페이지에서 사용된 저장소 외에 다른 저장소에서 자산 선택을 활성화합니다.
* **양식 규칙 편집기**: 코딩 없이 시각적으로 AEM Forms 필드에 동적 비헤이비어를 추가합니다.
* **[Adobe Target으로 콘텐츠 조각 내보내기](https://developer.adobe.com/uix/docs/extension-manager/extension-developed-by-adobe/exporting-content-fragment-to-adobe-target/)**: Adobe Experience Manager as a Cloud Service에서 만든 콘텐츠 조각을 Adobe Target으로 내보내 Target 활동에서 오퍼로 사용하여 대규모로 경험을 테스트하고 개인화합니다.
* **[콘텐츠 조각 워크플로](https://developer.adobe.com/uix/docs/extension-manager/extension-developed-by-adobe/content-fragments-workflows/)**: 선택한 콘텐츠 조각에 대해 AEM 워크플로를 시작합니다.

이 확장 기능을 활성화하는 방법에 대한 자세한 내용은 [Extension Manager 설명서를 참조하십시오](https://developer.adobe.com/uix/docs/extension-manager/feature-highlights/#enablingdisabling-extensions).

## UI 확장 {#extending-ui}

범용 편집기의 UI 확장 기능은 Adobe App Builder로 빌드된 JavaScript 애플리케이션입니다. 동일한 도구를 사용하여 헤더 메뉴 및 속성 패널에 자체 버튼 및 작업을 추가하고 범용 편집기에 대한 자체 이벤트를 생성할 수도 있습니다.

자체 확장 기능을 만드는 가능성을 알아보려면 다음 리소스를 참조하십시오.

1. [UI 확장성](https://developer.adobe.com/uix/docs/) - 이는 UI 확장에 대한 개발자 설명서입니다.
1. [UI 확장성 안내서](https://developer.adobe.com/uix/docs/guides/) - 자체 확장 기능을 개발하는 방법에 대한 단계별 지침
1. [범용 편집기 UI 확장 지점](https://developer.adobe.com/uix/docs/services/aem-universal-editor/) - 범용 편집기 관련 확장 지점 설명서

>[!TIP]
>
>예제를 통해 배우는 것을 선호하는 경우 [AEM UI 확장성 튜토리얼](https://experienceleague.adobe.com/ko/docs/experience-manager-learn/cloud-service/developing/extensibility/ui/overview)을 참조하십시오. 콘텐츠 조각 콘솔 확장에 중점을 두고 있지만, 범용 편집기에서 UI 확장 기능을 구현하기 위한 개념은 동일합니다.

[AEM Sites에서 Extension Manager를 사용](https://developer.adobe.com/uix/docs/extension-manager/)하면 인스턴스별로 확장 기능을 활성화하거나 비활성화하고, 범용 편집기에 대한 확장 기능을 포함하여 Adobe의 기본 확장 기능에 액세스하는 등의 작업을 수행할 수 있습니다.

## 확장 지점 {#extension-points}

UI 확장성 외에도 범용 편집기는 사용자 정의 비즈니스 요구 사항의 원활한 통합을 가능하게 하는 다른 여러 유연한 확장 지점을 제공합니다.

* **[블록](https://www.aem.live/developer/block-collection)**: 간단한 JSON 형식으로 프로젝트는 콘텐츠 제작에 사용할 수 있는 블록 및 UE 기능을 조정할 수 있습니다.
* **[맞춤형 사용자 인터페이스](#extending-ui)**: 확장 기능은 사이드 패널 또는 모달 대화 상자에 필요한 UI를 표시할 수 있습니다.
* **[이벤트](/help/implementing/universal-editor/events.md)**: 확장 기능은 작성자의 작업 및 페이지 선택에 대한 이벤트를 수신하여 적절하게 응답합니다.
