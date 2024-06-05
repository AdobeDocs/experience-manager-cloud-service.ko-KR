---
title: SPA 모델 라우팅
description: AEM의 단일 페이지 애플리케이션의 경우 앱이 라우팅을 담당합니다. 이 문서에서는 경로지정 메커니즘, 계약 및 사용 가능한 옵션에 대해 설명합니다.
exl-id: 1186b64e-11f8-43a6-bc75-450c4d7587ec
feature: Developing
role: Admin, Architect, Developer
source-git-commit: 646ca4f4a441bf1565558002dcd6f96d3e228563
workflow-type: tm+mt
source-wordcount: '438'
ht-degree: 0%

---

# SPA 모델 라우팅{#spa-model-routing}

AEM의 단일 페이지 애플리케이션의 경우 앱이 라우팅을 담당합니다. 이 문서에서는 경로지정 메커니즘, 계약 및 사용 가능한 옵션에 대해 설명합니다.

## 프로젝트 라우팅 {#project-routing}

앱은 라우팅을 소유하며 프로젝트 프론트엔드 개발자에 의해 구현됩니다. 이 문서에서는 AEM 서버에서 반환된 모델과 관련된 라우팅에 대해 설명합니다. 페이지 모델 데이터 구조는 기본 리소스의 URL을 노출합니다. 프론트엔드 프로젝트는 라우팅 기능을 제공하는 모든 사용자 지정 또는 서드파티 라이브러리를 사용할 수 있습니다. 경로에 모델의 조각이 예상되면 `PageModelManager.getData()` 함수를 만들 수 있습니다. 모델 경로가 변경된 경우 페이지 편집기와 같은 수신 라이브러리를 경고하기 위해 이벤트를 트리거해야 합니다.

## 아키텍처 {#architecture}

자세한 설명은 을 참조하십시오. [PageModelManager](blueprint.md#pagemodelmanager) SPA 섹션에 있는 마지막 항목이 될 필요가 없습니다.

## 모델 라우터 {#modelrouter}

다음 `ModelRouter` - 활성화된 경우 - HTML5 내역 API 함수를 캡슐화합니다. `pushState` 및 `replaceState` 모델의 지정된 조각을 미리 가져오고 액세스할 수 있도록 보장합니다. 그런 다음 등록된 프런트엔드 구성 요소에 모델이 수정되었음을 알립니다.

## 수동 및 자동 모델 라우팅 {#manual-vs-automatic-model-routing}

다음 `ModelRouter` 모델의 조각 가져오기를 자동화합니다. 그러나 모든 자동화된 툴은 제한 사항이 있습니다. 필요한 경우 `ModelRouter` 메타 속성을 사용하여 경로를 무시하도록 비활성화하거나 구성할 수 있습니다( 의 메타 속성 섹션 참조). [SPA 페이지 구성 요소](page-component.md) 문서 참조). 그러면 프론트엔드 개발자는 다음을 요청하여 자체 모델 라우팅 레이어를 구현할 수 있습니다. `PageModelManager` 를 사용하여 모델의 지정된 조각을 로드하려면 `getData()` 함수.

>[!CAUTION]
>
>의 현재 버전 `ModelRouter` 슬링 모델 진입점의 실제 리소스 경로를 가리키는 URL만 사용할 수 있습니다. Vanity URL 또는 별칭의 사용을 지원하지 않습니다.

## 라우팅 계약 {#routing-contract}

현재 구현은 SPA 프로젝트가 다른 애플리케이션 페이지로 라우팅하기 위해 HTML5 내역 API를 사용한다는 가정을 기반으로 합니다.

### 구성 {#configuration}

다음 `ModelRouter` 는 수신 시 모델 라우팅 개념을 지원합니다. `pushState` 및 `replaceState` 모델 조각을 미리 가져오는 호출. 내부적으로 `PageModelManager` 지정된 URL에 해당하는 모델을 로드하고 `cq-pagemodel-route-changed` 다른 모듈이 수신할 수 있는 이벤트입니다.

기본적으로 이 동작은 자동으로 활성화됩니다. 비활성화하려면 SPA에서 다음 메타 속성을 렌더링해야 합니다.

```
<meta property="cq:pagemodel_router" content="disabled"\>
```

SPA의 모든 경로는 AEM에서 액세스 가능한 리소스에 해당해야 합니다(예: &quot; `/content/mysite/mypage"`) 이후 `PageModelManager` 경로를 선택하면 해당 페이지 모델을 자동으로 로드합니다. 그러나 필요한 경우 SPA은 가 무시해야 하는 경로의 &quot;차단 목록&quot;를 정의할 수도 있습니다. `PageModelManager`:

```
<meta property="cq:pagemodel_route_filters" content="route/not/found,^(.*)(?:exclude/path)(.*)"/>
```
