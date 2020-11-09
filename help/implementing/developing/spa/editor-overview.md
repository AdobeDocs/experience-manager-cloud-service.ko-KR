---
title: SPA 편집기 개요
description: 이 문서에서는 SPA 편집기의 전체 개요와 작동 방식에 AEM 내의 SPA 편집기의 상호 작용에 대한 자세한 워크플로우가 포함되어 있는 방법을 설명합니다.
translation-type: tm+mt
source-git-commit: 8bdb7bbe80a4e22bb2b750c0719c6db745133392
workflow-type: tm+mt
source-wordcount: '1641'
ht-degree: 0%

---


# SPA 편집기 개요 {#spa-editor-overview}

단일 페이지 애플리케이션(SPA)을 통해 웹 사이트 사용자에게 매력적인 경험을 제공할 수 있습니다. 개발자는 SPA 프레임워크을 사용하여 사이트를 구축하고자 하며, 작성자는 이러한 프레임워크를 사용하여 구축한 사이트에 대해 AEM 내에서 컨텐츠를 완벽하게 편집하고자 합니다.

SPA Editor는 AEM에서 SPA을 지원하는 포괄적인 솔루션을 제공합니다. 이 페이지에서는 SPA 지원이 AEM에서 구조화되는 방식, SPA 편집기의 작동 방식, SPA 프레임워크과 AEM의 동기화 방식에 대한 개요를 제공합니다.

## 소개 {#introduction}

동적 JSON을 통해 반응형 및 각로드와 같은 일반적인 SPA 프레임워크을 사용하여 구축한 사이트는 컨텐츠를 제작하며 AEM 페이지 편집기에서 편집 컨트롤을 배치하는 데 필요한 HTML 구조를 제공하지 않습니다.

AEM 내에서 SPA을 편집하려면 컨텐츠의 변경 사항을 저장하려면 SPA의 JSON 출력 및 AEM 저장소의 컨텐츠 모델 간의 매핑이 필요합니다.

AEM의 SPA 지원 기능에서는 페이지 편집기에서 이벤트를 전송할 수 있고 편집 컨트롤의 위치를 활성화하여 상황에 맞는 편집을 허용할 때 SPA JS 코드와 상호 작용하는 가상 JS 레이어를 도입합니다. 이 기능은 SPA의 컨텐츠를 Content Services를 통해 로드해야 하므로 Content Services API Endpoint 개념을 기반으로 합니다.

AEM에서 SPA에 대한 자세한 내용은 다음 문서를 참조하십시오.

* [SPA](blueprint.md) 기술 요구 사항을 위한 SPA Blueprint
* [AEM에서 SPA 시작하기](getting-started-react.md) Reresponse를 사용하여 간단한 SPA을 빠르게 둘러보십시오
* [AEM에서 SPA 시작(Angular](getting-started-angular.md) 사용)을 사용하여 간단한 SPA을 신속하게 둘러봅니다.

## 디자인 {#design}

SPA용 페이지 구성 요소는 JSP 또는 HTL 파일을 통해 하위 구성 요소의 HTML 요소를 제공하지 않습니다. 이 작업은 SPA 프레임워크에 위임됩니다. 하위 구성 요소 또는 모델의 표현은 JCR에서 JSON 데이터 구조로 가져옵니다. 그러면 SPA 구성 요소가 해당 구조에 따라 페이지에 추가됩니다. 이 동작은 페이지 구성 요소의 초기 본문 컴포지션을 SPA이 아닌 것과 구별합니다.

### 페이지 모델 관리 {#page-model-management}

페이지 모델의 해상도 및 관리는 제공된 `PageModel` 라이브러리에 위임됩니다. SPA 편집기가 초기화하고 제작하려면 SPA에서 페이지 모델 라이브러리를 사용해야 합니다. 페이지 모델 라이브러리는 npm을 통해 AEM 페이지 구성 요소에 간접적으로 `aem-react-editable-components` 제공되었습니다. 페이지 모델은 AEM과 SPA 간의 인터프리터이므로 항상 있어야 합니다. 페이지를 작성할 때 페이지 편집기와의 통신을 활성화하려면 추가 라이브러리를 추가해야 `cq.authoring.pagemodel.messaging` 합니다.

SPA 페이지 구성 요소가 페이지 코어 구성 요소에서 상속되는 경우 클라이언트 라이브러리 카테고리를 사용할 수 있도록 하는 두 가지 옵션이 `cq.authoring.pagemodel.messaging` 있습니다.

* 템플릿을 편집할 수 있는 경우 페이지 정책에 추가합니다.
* 또는 를 사용하여 카테고리를 추가합니다 `customfooterlibs.html`.

내보낸 모델의 각 리소스에 대해 SPA은 렌더링할 실제 구성 요소를 매핑합니다. 그런 다음 JSON으로 표현되는 모델이 컨테이너 내의 구성 요소 매핑을 사용하여 렌더링됩니다.

![SPA의 모델 및 구성 요소 매핑](assets/model-component-mapping.png)

>[!CAUTION]
>
>카테고리 포함은 `cq.authoring.pagemodel.messaging` SPA 편집기의 컨텍스트로 제한되어야 합니다.

### 통신 데이터 유형 {#communication-data-type}

카테고리가 페이지에 추가되면 페이지 편집기에 메시지를 보내 JSON 커뮤니케이션 데이터 유형을 설정합니다. `cq.authoring.pagemodel.messaging` 통신 데이터 유형이 JSON으로 설정되면 GET 요청은 구성 요소의 Sling Model 끝점과 통신하게 됩니다. 페이지 편집기에서 업데이트가 발생하면 업데이트된 구성 요소의 JSON 표현이 페이지 모델 라이브러리로 전송됩니다. 그런 다음 페이지 모델 라이브러리가 SPA에 업데이트를 알려줍니다.

![SPA 커뮤니케이션](assets/communication.png)

## 워크플로우 {#workflow}

SPA과 AEM의 상호 작용의 흐름을 양쪽의 중재자로 생각하면서 이해할 수 있다.

* 페이지 편집기와 SPA 간의 통신은 HTML 대신 JSON을 사용하여 이루어집니다.
* 페이지 편집기는 iframe 및 messaging API를 통해 최신 버전의 페이지 모델을 SPA에 제공합니다.
* 페이지 모델 관리자는 에디션이 준비되었음을 편집자에게 알리고 페이지 모델을 JSON 구조로 전달합니다.
* 편집기는 최신 페이지 모델을 제공하는 것이 아니라 작성 중인 페이지의 DOM 구조를 변경하거나 심지어 액세스할 수도 없습니다.

![SPA 워크플로우](assets/workflow.png)

### 기본 SPA 편집기 워크플로우 {#basic-spa-editor-workflow}

SPA 편집기의 주요 요소를 염두에 두고, AEM 내에서 SPA을 편집하는 고급 워크플로우는 다음과 같이 작성자에게 표시됩니다.

![애니메이션 SPA 워크플로우](assets/workflow.gif)

1. SPA 편집기가 로드됩니다.
1. SPA은 별도의 프레임으로 로드됩니다.
1. SPA은 JSON 콘텐츠를 요청하고 구성 요소를 클라이언트측에서 렌더링합니다.
1. SPA 편집기는 렌더링된 구성 요소를 감지하고 오버레이를 생성합니다.
1. 작성자가 오버레이를 클릭하고 구성 요소의 편집 도구 모음을 표시합니다.
1. SPA 편집기는 서버에 대한 POST 요청과 함께 편집한 내용을 유지합니다.
1. SPA 편집기 요청이 SPA 편집기로 JSON을 업데이트하여 DOM 이벤트가 있는 SPA으로 전송됩니다.
1. SPA은 관련 구성 요소를 다시 렌더링하여 DOM을 업데이트합니다.

>[!NOTE]
>
>주의 사항:
>
>* SPA은 항상 그 디스플레이를 담당한다.
>* SPA 편집기는 SPA 자체에서 분리되어 있다.
>* 제작(게시)에서는 SPA 편집기가 로드되지 않습니다.


### 클라이언트-서버 페이지 편집 워크플로우 {#client-server-page-editing-workflow}

SPA 편집 시 클라이언트-서버 상호 작용에 대한 자세한 개요입니다.

![클라이언트 서버 편집 워크플로우](assets/client-server-editing.png)

1. SPA은 자체적으로 초기화하고 Sling Model Exporter에서 페이지 모델을 요청합니다.
1. Sling Model Exporter는 저장소에서 페이지를 구성하는 리소스를 요청합니다.
1. 저장소가 리소스를 반환합니다.
1. Sling Model Exporter는 페이지의 모델을 반환합니다.
1. SPA은 페이지 모델을 기반으로 구성 요소를 인스턴스화합니다.
1. **6a** 컨텐츠는 편집자에게 작성할 준비가 되었음을 알려줍니다.

   **6b** 페이지 편집기는 구성 요소 작성 구성을 요청합니다.

   **6c** 페이지 편집기는 구성 요소 구성을 수신합니다.
1. 작성자가 구성 요소를 편집할 때 페이지 편집기는 수정 요청을 기본 POST 서블릿에 게시합니다.
1. 저장소에서 리소스가 업데이트됩니다.
1. 업데이트된 리소스가 POST 서블릿에 제공됩니다.
1. 기본 POST 서블릿은 페이지 편집기에 리소스가 업데이트되었음을 알려줍니다.
1. 페이지 편집기가 새 페이지 모델을 요청합니다.
1. 페이지를 구성하는 리소스는 저장소에서 요청됩니다.
1. 페이지를 구성하는 리소스는 저장소에서 Sling Model Exporter로 제공됩니다.
1. 업데이트된 페이지 모델이 편집기로 반환됩니다.
1. 페이지 편집기는 SPA의 페이지 모델 참조를 업데이트합니다.
1. SPA은 새 페이지 모델 참조를 기반으로 구성 요소를 업데이트합니다.
1. 페이지 편집기의 구성 요소 구성이 업데이트됩니다.

   **17a** SPA은 페이지 편집기에 컨텐츠가 준비되었음을 알립니다.

   **17b** 페이지 편집기는 SPA에 구성 요소 구성을 제공합니다.

   **17c** SPA은 업데이트된 구성 요소 구성을 제공합니다.

### 작성 워크플로우 {#authoring-workflow}

작성 경험에 중점을 둔 보다 자세한 개요입니다.

![SPA 제작 워크플로우](assets/authoring-workflow.png)

1. SPA은 페이지 모델을 가져옵니다.
1. **2a** 페이지 모델은 작성에 필요한 데이터를 편집기에 제공합니다.

   **2b** 알림을 받으면 구성 요소 오케스트레이터가 페이지의 컨텐츠 구조를 업데이트합니다.
1. 구성 요소 오케스트레이터는 AEM 리소스 유형과 SPA 구성 요소 간의 매핑을 쿼리합니다.
1. 구성 요소 오케스트레이터는 페이지 모델 및 구성 요소 매핑을 기반으로 SPA 구성 요소를 동적으로 인스턴스화합니다.
1. 페이지 편집기가 페이지 모델을 업데이트합니다.
1. **6a** 페이지 모델은 업데이트된 작성 데이터를 페이지 편집기에 제공합니다.

   **6b** 페이지 모델은 구성 요소 오케스트레이터에 변경 사항을 전달합니다.
1. 구성 요소 오케스트레이터는 구성 요소 매핑을 페치합니다.
1. 구성 요소 오케스트레이터는 페이지의 컨텐츠를 업데이트합니다.
1. SPA에서 페이지의 컨텐츠 업데이트를 완료하면 페이지 편집기는 작성 환경을 로드합니다.

## 요구 사항 및 제한 사항 {#requirements-limitations}

작성자가 페이지 편집기를 사용하여 SPA의 컨텐츠를 편집할 수 있도록 하려면 AEM SPA 편집기 SDK와 상호 작용하기 위해 SPA 응용 프로그램을 구현해야 합니다. 최소 실행 방법을 알아야 하는 경우 AEM [에서 React](getting-started-react.md) 를 사용하여 SPA 시작하기를 참조하십시오.

### 지원되는 프레임워크 {#supported-frameworks}

SPA Editor SDK는 다음과 같은 최소 버전을 지원합니다.

* 16.x 이상 반응
* 각 6.x 이상

이러한 프레임워크의 이전 버전은 AEM SPA Editor SDK에서 사용할 수 있지만 지원되지 않습니다.

### 추가 프레임워크 {#additional-frameworks}

AEM SPA 편집기 SDK와 연동되도록 추가 SPA 프레임워크을 구현할 수 있습니다. AEM SPA 편집기로 작업할 모듈, 구성 요소 및 서비스로 구성된 프레임워크별 레이어를 만들기 위해 프레임워크가 충족해야 하는 요구 사항은 [SPA Blueprint](blueprint.md) 문서를 참조하십시오.

### 여러 선택기 사용 {#multiple-selectors}

추가적인 사용자 정의 선택기를 AEM SDK용으로 개발된 SPA의 일부로 정의하고 사용할 수 있습니다. 그러나 이 지원을 사용하려면 `model` 선택기가 첫 번째 선택기여야 하며 확장 기능은 JSON Exporter `.json` 에서 필요한 대로 해야 합니다.

### 텍스트 편집기 요구 사항 {#text-editor-requirements}

SPA에서 만든 텍스트 구성 요소의 즉석 편집기를 사용하려면 추가 구성이 필요합니다.

1. 텍스트 HTML을 포함하는 컨테이너 래퍼 요소에 속성을 설정합니다(모든 것일 수 있음). WKND SPA 프로젝트의 경우 `<div>` 요소이고 사용된 선택기가 사용됩니다 `data-rte-editelement`.
1. 해당 AEM 텍스트 구성 요소 `editElementQuery` 에서 해당 선택기를 가리키는 구성 `cq:InplaceEditingConfig` 을 설정합니다(예:). `data-rte-editelement`. 이를 통해 편집자는 HTML 텍스트를 래핑하는 HTML 요소를 알 수 있습니다.

속성 `editElementQuery` 및 리치 텍스트 편집기의 구성에 대한 자세한 내용은 리치 텍스트 편집기 [구성을 참조하십시오.](/help/implementing/developing/extending/rich-text-editor.md)

### 제한 사항 {#limitations}

AEM SPA Editor SDK는 Adobe에서 완벽하게 지원되며 새로운 기능으로서 지속적으로 향상되고 확장됩니다. 다음 AEM 기능은 아직 SPA 편집기에서 지원되지 않습니다.

* Target 모드
* ContextHub
* 인라인 이미지 편집
* 구성 편집(예: 청취자)
* 스타일 시스템
* 실행 취소/다시 실행
* 페이지 비교 및 시간 변형
* 링크 검사기, CDN 리작성기 서비스, URL 단축 등과 같은 HTML 재작성 서버측 기능을 수행하는 기능
* 개발자 모드
* AEM 실행
