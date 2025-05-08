---
title: 유니버설 편집기 확장
description: 콘텐츠 작성자의 요구 사항을 지원하기 위해 범용 편집기의 기능을 확장하는 다양한 옵션에 대해 알아봅니다.
feature: Developing
role: Admin, Architect, Developer
exl-id: 2f487fa5-57a7-477a-ad68-590e6cc12f4e
source-git-commit: 9941c652a1509934662cdaae6d187d1a28a1cc31
workflow-type: tm+mt
source-wordcount: '580'
ht-degree: 0%

---

# 유니버설 편집기 확장 {#extending}

콘텐츠 작성자의 요구 사항을 지원하기 위해 범용 편집기의 기능을 확장하는 다양한 옵션에 대해 알아봅니다.

>[!TIP]
>
>또한 유니버설 편집기는 프로젝트 요구 사항을 더 잘 충족할 수 있도록 여러 [사용자 지정 옵션](/help/implementing/universal-editor/customizing.md)을 제공합니다.

## 확장 {#extensions}

Adobe Experience Cloud 서비스로서, App Builder 및 Experience Manager을 사용하여 범용 편집기의 UI를 확장할 수 있습니다. Adobe에서는 프로젝트에 사용할 수 있는 [Extension Manager](https://experience.adobe.com/aem/extension-manager)을 통해 사용할 수 있는 다양한 준비된 확장을 제공합니다.

* **[AEM MSM(다중 사이트 관리) 확장](/help/sites-cloud/authoring/universal-editor/authoring.md#inheritance)**: 구성 요소 수준에서 상속을 중단하거나 복원합니다.
* **[AEM 페이지 속성 확장](/help/sites-cloud/authoring/universal-editor/authoring.md#page-properties)**: 유니버설 편집기에서 페이지의 페이지 속성 창에 액세스합니다
* **[AEM 사이트 관리자 확장](/help/sites-cloud/authoring/universal-editor/authoring.md#sites-console)**: 범용 편집기에서 페이지 위치에 대한 사이트 콘솔을 엽니다.
* **[AEM 페이지 잠금 확장 기능](/help/sites-cloud/authoring/universal-editor/authoring.md#locking-pages)**: 유니버설 편집기에서 페이지 잠금 상태를 보고 변경합니다
* **[AEM 워크플로 확장](/help/sites-cloud/authoring/universal-editor/authoring.md#workflows)**: 페이지에서 워크플로를 시작하고 유니버설 편집기에서 페이지 콘텐츠를 가져옵니다.
* **[AEM 유니버설 편집기 개발 로그인 확장](/help/sites-cloud/authoring/universal-editor/authoring.md#developer-login)**: 로컬로 개발할 때 로컬 AEM SDK에 쉽게 인증할 수 있습니다
* **[변형 생성](/help/generative-ai/generate-variations-integrated-editor.md)**: 생성 AI(인공 지능)를 사용하여 속성 패널에서 직접 콘텐츠에 대한 변형을 만듭니다.
* **[범용 편집기에 대한 AEM 제품 선택기](https://developer.adobe.com/uix/docs/extension-manager/extension-developed-by-adobe/ue-product-picker/)**: 편집기에서 제품 데이터를 선택하거나 제거하여 Adobe Commerce 데이터를 통합합니다.
* **[유니버설 편집기 콘텐츠 초안](https://developer.adobe.com/uix/docs/extension-manager/extension-developed-by-adobe/universal-editor-content-drafts/)**: 여러 콘텐츠 초안을 만들고 편집하고 관리합니다.
* **[구성 가능한 자산 선택기](https://developer.adobe.com/uix/docs/extension-manager/extension-developed-by-adobe/configurable-asset-picker/)**: 편집된 페이지에서 사용하는 저장소가 아닌 저장소에서 자산 선택을 사용하도록 설정합니다.
* **Forms 규칙 편집기**: 코딩하지 않고 시각적으로 AEM Forms 필드에 동적 동작을 추가하십시오.
* **[Adobe Target으로 콘텐츠 조각 내보내기](https://developer.adobe.com/uix/docs/extension-manager/extension-developed-by-adobe/exporting-content-fragment-to-adobe-target/)**: Target 활동의 오퍼로 사용할 수 있도록 Adobe Experience Manager as a Cloud Service에서 만든 콘텐츠 조각을 Adobe Target으로 내보내 규모에 맞게 경험을 테스트하고 개인화합니다.
* **[콘텐츠 조각 워크플로](https://developer.adobe.com/uix/docs/extension-manager/extension-developed-by-adobe/content-fragments-workflows/)**: 선택한 콘텐츠 조각에 대한 AEM 워크플로를 시작합니다.

이러한 확장을 사용하는 방법에 대한 자세한 내용은 [Extension Manager 설명서를 참조하십시오.](https://developer.adobe.com/uix/docs/extension-manager/feature-highlights/#enablingdisabling-extensions)

## UI 확장 {#extending-ui}

범용 편집기의 UI 확장은 Adobe App Builder으로 빌드된 JavaScript 애플리케이션입니다. 이와 동일한 도구를 사용하여 헤더 메뉴 및 속성 패널에 고유한 버튼과 작업을 추가할 수 있을 뿐만 아니라 범용 편집기에 대한 고유한 이벤트를 만들 수도 있습니다.

고유한 확장을 만들 수 있는 가능성을 알아보려면 다음 리소스를 참조하십시오.

1. [UI 확장성](https://developer.adobe.com/uix/docs/) - UI 확장에 대한 개발자 설명서입니다.
1. [UI 확장성 안내서](https://developer.adobe.com/uix/docs/guides/) - 고유한 확장을 개발하는 방법에 대한 단계별 지침
1. [유니버설 편집기 UI 확장 지점](https://developer.adobe.com/uix/docs/services/aem-universal-editor/) - 유니버설 편집기별 확장 지점 문서

>[!TIP]
>
>예를 통해 학습하려면 [AEM UI 확장성 자습서](https://experienceleague.adobe.com/en/docs/experience-manager-learn/cloud-service/developing/extensibility/ui/overview)를 참조하십시오. 콘텐츠 조각 콘솔 확장에 중점을 두고 있지만, 범용 편집기에서 UI 확장을 구현하는 개념은 동일합니다.

[AEM Sites에서 Extension Manager 사용](https://developer.adobe.com/uix/docs/extension-manager/)을 통해 인스턴스별로 확장을 활성화하거나 비활성화하고, 범용 편집기용 확장을 포함하여 Adobe의 자사 확장에 액세스할 수 있습니다.

## 확장 지점 {#extension-points}

UI 확장성 외에도 유니버설 편집기는 사용자 정의 비즈니스 요구 사항을 매끄럽게 통합할 수 있도록 다양한 유연한 확장 지점을 제공합니다.

* **[블록](/help/edge/developer/block-collection.md)**: 간단한 JSON 형식에서 프로젝트는 콘텐츠를 만드는 데 사용할 수 있는 블록 및 UE 기능을 조정할 수 있습니다.
* **[사용자 지정 사용자 인터페이스](#extending-ui)**: 확장에서 사이드 패널 또는 모달 대화 상자에 필요한 UI를 표시할 수 있습니다.
* **[이벤트](/help/implementing/universal-editor/events.md)**: 확장에서는 작성자의 작업 및 선택 사항에 대한 이벤트를 페이지에 수신하여 적절하게 응답합니다.
