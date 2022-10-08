---
title: SPA 모델 라우팅
description: AEM의 단일 페이지 애플리케이션의 경우, 앱은 라우팅을 담당합니다. 이 문서에서는 사용 가능한 라우팅 메커니즘, 계약 및 옵션에 대해 설명합니다.
exl-id: 1186b64e-11f8-43a6-bc75-450c4d7587ec
source-git-commit: ca849bd76e5ac40bc76cf497619a82b238d898fa
workflow-type: tm+mt
source-wordcount: '442'
ht-degree: 1%

---

# SPA 모델 라우팅{#spa-model-routing}

AEM의 단일 페이지 애플리케이션의 경우, 앱은 라우팅을 담당합니다. 이 문서에서는 사용 가능한 라우팅 메커니즘, 계약 및 옵션에 대해 설명합니다.

## 프로젝트 라우팅 {#project-routing}

앱은 라우팅을 소유하며 프로젝트 프런트 엔드 개발자에 의해 구현됩니다. 이 문서에서는 AEM 서버에서 반환한 모델에 대한 라우팅에 대해 설명합니다. 페이지 모델 데이터 구조는 기본 리소스의 URL을 표시합니다. 프런트 엔드 프로젝트는 라우팅 기능을 제공하는 모든 사용자 지정 라이브러리 또는 타사 라이브러리를 사용할 수 있습니다. 라우트에서 모델 조각을 예상하면 `PageModelManager.getData()` 함수를 만들 수 있습니다. 모델 경로가 변경된 경우 페이지 편집기와 같은 수신 라이브러리를 경고하도록 이벤트를 트리거해야 합니다.

## 아키텍처 {#architecture}

자세한 내용은 [PageModelManager](blueprint.md#pagemodelmanager) SPA 블루프린트 문서의 섹션을 참조하십시오.

## ModelRouter {#modelrouter}

다음 `ModelRouter` - 활성화되면 - HTML5 내역 API 함수를 캡슐화합니다. `pushState` 및 `replaceState` 지정된 모델 조각을 미리 가져와서 액세스할 수 있도록 합니다. 그런 다음 등록된 프런트엔드 구성 요소에 모델이 수정되었음을 알립니다.

## 수동 및 자동 모델 공정순서 {#manual-vs-automatic-model-routing}

다음 `ModelRouter` 모델의 조각 가져오기를 자동화합니다. 그러나 자동화 도구에는 제한이 있습니다. 필요한 경우 `ModelRouter` 메타 속성을 사용하여 경로를 무시하도록 비활성화하거나 구성할 수 있습니다( [SPA 페이지 구성 요소](page-component.md) 문서). 그러면 프런트 엔드 개발자는 `PageModelManager` 를 사용하여 주어진 모델 조각을 로드하려면 `getData()` 함수 위에 있어야 합니다.

>[!CAUTION]
>
>의 현재 버전입니다. `ModelRouter` Sling 모델 시작 지점의 실제 리소스 경로를 가리키는 URL의 사용만 지원합니다. 별칭 URL 또는 별칭 사용을 지원하지 않습니다.

## 공정순서 계약 {#routing-contract}

현재 구현은 SPA 프로젝트에서 다른 애플리케이션 페이지로 라우팅하기 위해 HTML5 내역 API를 사용한다고 가정 하에 수행됩니다.

### 구성 {#configuration}

다음 `ModelRouter` 은 수신 대기하는 모델 라우팅 개념을 지원합니다 `pushState` 및 `replaceState` 모델 조각을 미리 가져오기 위한 호출. 내부적으로 `PageModelManager` 지정된 URL에 해당하는 모델을 로드하고 `cq-pagemodel-route-changed` 다른 모듈이 수신할 수 있는 이벤트입니다.

기본적으로 이 동작은 자동으로 활성화됩니다. 비활성화하려면 SPA에서 다음 메타 속성을 렌더링해야 합니다.

```
<meta property="cq:pagemodel_router" content="disabled"\>
```

SPA의 모든 경로는 AEM에서 액세스할 수 있는 리소스에 해당해야 합니다(예: &quot;). `/content/mysite/mypage"`) 이후 `PageModelManager` 경로가 선택되면 은 자동으로 해당 페이지 모델을 로드합니다. 그러나 필요한 경우 SPA에서 무시해야 하는 경로의 &quot;차단 목록&quot;도 정의할 수 있습니다 `PageModelManager`:

```
<meta property="cq:pagemodel_route_filters" content="route/not/found,^(.*)(?:exclude/path)(.*)"/>
```
