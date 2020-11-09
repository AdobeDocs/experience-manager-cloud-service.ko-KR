---
title: SPA 모델 라우팅
description: AEM의 단일 페이지 애플리케이션의 경우, 앱은 라우팅을 담당합니다. 이 문서에서는 사용 가능한 라우팅 메커니즘, 계약 및 옵션에 대해 설명합니다.
translation-type: tm+mt
source-git-commit: c075bcc415b68ba0deaeca61d6d179bd7263ca5f
workflow-type: tm+mt
source-wordcount: '441'
ht-degree: 1%

---


# SPA 모델 라우팅{#spa-model-routing}

AEM의 단일 페이지 애플리케이션의 경우, 앱은 라우팅을 담당합니다. 이 문서에서는 사용 가능한 라우팅 메커니즘, 계약 및 옵션에 대해 설명합니다.

## 프로젝트 라우팅 {#project-routing}

앱은 라우팅을 소유하며 프로젝트 프런트 엔드 개발자에 의해 구현됩니다. 이 문서에서는 AEM 서버에서 반환된 모델에 대한 라우팅에 대해 설명합니다. 페이지 모델 데이터 구조는 기본 리소스의 URL을 표시합니다. 프런트 엔드 프로젝트는 라우팅 기능을 제공하는 사용자 정의 라이브러리 또는 타사 라이브러리를 사용할 수 있습니다. 경로의 요청에 모델 조각이 필요한 경우 함수를 호출할 수 `PageModelManager.getData()` 있습니다. 모델 경로가 변경된 경우 페이지 편집기와 같은 의견 수렴 라이브러리를 경고하도록 이벤트를 트리거해야 합니다.

## 아키텍처 {#architecture}

자세한 설명은 SPA Blueprint 문서의 [PageModelManager](blueprint.md#pagemodelmanager) 섹션을 참조하십시오.

## ModelRouter {#modelrouter}

- `ModelRouter` 활성화되면 - HTML5 내역 API 함수 `pushState` 를 캡슐화하고 해당 모델 조각 `replaceState` 을 미리 반입하여 액세스할 수 있도록 합니다. 그런 다음 등록된 프런트 엔드 구성 요소에 모델이 수정되었음을 알립니다.

## 수동 및 자동 모델 라우팅 {#manual-vs-automatic-model-routing}

모델의 조각 `ModelRouter` 가져오기를 자동화합니다. 그러나 자동화된 툴에는 제한 사항이 적용됩니다. 필요할 때 메타 속성을 사용하여 경로를 무시하도록 해당 경로를 비활성화하거나 구성할 `ModelRouter` 수 있습니다( [SPA 페이지 구성 요소](page-component.md) 문서의 메타 속성 섹션 참조). 그런 다음 프런트 엔드 개발자는 해당 함수를 사용하여 주어진 모델 조각 `PageModelManager` 을 로드하도록 요청하여 자체 모델 라우팅 레이어를 구현할 수 `getData()` 있습니다.

>[!CAUTION]
>
>현재 버전의 유일한 `ModelRouter` 는 Sling 모델 진입점의 실제 리소스 경로를 가리키는 URL의 사용을 지원합니다. 별칭 URL 또는 별칭 사용을 지원하지 않습니다.

## 라우팅 계약 {#routing-contract}

현재 구현은 SPA 프로젝트에서 HTML5 내역 API를 사용하여 다른 응용 프로그램 페이지로 라우팅한다는 가정을 기반으로 합니다.

### 구성 {#configuration}

모델 조각 `ModelRouter` 을 수신 `pushState` 및 프리페치 모델 조각 `replaceState` 호출을 수행할 때 모델 라우팅 개념을 지원합니다. 내부적으로 해당 URL `PageModelManager` 에 해당하는 모델을 로드하고 다른 모듈에서 들을 수 있는 `cq-pagemodel-route-changed` 이벤트를 발생시킵니다.

기본적으로 이 동작은 자동으로 활성화됩니다. 비활성화하려면 SPA에서 다음 메타 속성을 렌더링해야 합니다.

```
<meta property="cq:pagemodel_router" content="disable"\>
```

라우트가 선택되면 SPA에서 해당 페이지 모델을 자동으로 로드하려고 `/content/mysite/mypage"``PageModelManager` 하므로의 모든 경로는 AEM에서 액세스 가능한 리소스(예: &quot;)에 해당됩니다. 하지만, 필요할 경우, SPA은 다음 항목에 의해 무시되어야 하는 경로의 &quot;차단 목록&quot;을 정의할 수도 있습니다 `PageModelManager`.

```
<meta property="cq:pagemodel_route_filters" content="route/not/found,^(.*)(?:exclude/path)(.*)"/>
```
