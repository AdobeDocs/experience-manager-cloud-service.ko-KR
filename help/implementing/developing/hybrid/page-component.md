---
title: SPA 페이지 구성 요소
description: SPA에서 페이지 구성 요소는 하위 구성 요소의 HTML 요소를 제공하지 않고 대신 SPA 프레임워크에 전달합니다. 이 문서에서는 이 방법이 SPA의 페이지 구성 요소를 고유하게 만드는 방법을 설명합니다.
exl-id: 41b56a60-ebb8-499d-a0ab-a2e920f26227
source-git-commit: 90de3cf9bf1c949667f4de109d0b517c6be22184
workflow-type: tm+mt
source-wordcount: '598'
ht-degree: 2%

---

# SPA 페이지 구성 요소 {#spa-page-component}

SPA용 페이지 구성 요소는 JSP 또는 HTL 파일 및 리소스 개체를 통해 하위 구성 요소의 HTML 요소를 제공하지 않습니다. 이 작업은 SPA 프레임워크에 위임됩니다. 하위 구성 요소의 표현을 JSON 데이터 구조(즉, 모델)로 가져옵니다. 그런 다음 제공된 JSON 모델에 따라 SPA 구성 요소가 페이지에 추가됩니다. 따라서 페이지 구성 요소의 초기 본문 구성은 사전 렌더링된 HTML 상대와 다릅니다.

## 페이지 모델 관리 {#page-model-management}

페이지 모델의 해상도 및 관리는 제공된 [`PageModelManager`](blueprint.md#pagemodelmanager) 모듈에 위임됩니다. SPA은 초기 페이지 모델을 가져오고 모델 업데이트를 등록하도록 초기화될 때 `PageModelManager` 모듈과 상호 작용해야 합니다. 이 모듈은 작성자가 페이지 편집기를 통해 페이지를 편집 중일 때 주로 생성됩니다. `PageModelManager`은 SPA 프로젝트에서 npm 패키지로 액세스할 수 있습니다. AEM과 SPA 간의 해석자가 되는 경우 `PageModelManager`은 SPA과 함께 사용할 수 있습니다.

페이지를 작성할 수 있도록 하려면 SPA과 페이지 편집기 간에 통신 채널을 제공하기 위해 `cq.authoring.pagemodel.messaging` 라는 클라이언트 라이브러리를 추가해야 합니다. SPA 페이지 구성 요소가 페이지 wcm/코어 구성 요소에서 상속되는 경우 `cq.authoring.pagemodel.messaging` 클라이언트 라이브러리 카테고리를 사용할 수 있는 다음 옵션이 있습니다.

* 템플릿을 편집할 수 있는 경우 클라이언트 라이브러리 범주를 페이지 정책에 추가합니다.
* 페이지 구성 요소의 `customfooterlibs.html` 을 사용하여 클라이언트 라이브러리 카테고리를 추가합니다.

`cq.authoring.pagemodel.messaging` 카테고리 포함을 페이지 편집기의 컨텍스트에서 제한하는 것을 잊지 마십시오.

## 통신 데이터 유형 {#communication-data-type}

통신 데이터 유형은 `data-cq-datatype` 속성을 사용하여 AEM Page 구성 요소 내의 HTML 요소를 설정합니다. 통신 데이터 유형이 JSON으로 설정되면 GET 요청이 구성 요소의 Sling 모델 종단점에 도달합니다. 페이지 편집기에서 업데이트가 발생하면 업데이트된 구성 요소의 JSON 표현이 페이지 모델 라이브러리로 전송됩니다. 그러면 페이지 모델 라이브러리에서는 업데이트 SPA에 대해 경고합니다.

**SPA 페이지 구성 요소 -`body.html`**

```
<div id="page"></div>
```

SPA 프레임워크은 DOM 생성을 지연하지 않는 것이 좋습니다. 본문 끝에 스크립트를 추가해야 합니다.

**SPA 페이지 구성 요소 -`customfooterlibs.html`**

```
<sly data-sly-use.clientLib="${'/libs/granite/sightly/templates/clientlib.html'}"></sly>
<sly data-sly-test="${wcmmode.edit || wcmmode.preview}"
     data-sly-call="${clientLib.js @ categories='cq.authoring.pagemodel.messaging'}"></sly>
<sly data-sly-call="${clientLib.js @ categories='we-retail-journal-react'}"></sly>
```

SPA 컨텐츠를 설명하는 메타 리소스 속성:

**SPA 페이지 구성 요소 -`customheaderlibs.html`**

```
<meta property="cq:datatype" data-sly-test="${wcmmode.edit || wcmmode.preview}" content="JSON"/>
<meta property="cq:wcmmode" data-sly-test="${wcmmode.edit}" content="edit"/>
<meta property="cq:wcmmode" data-sly-test="${wcmmode.preview}" content="preview"/>
<meta property="cq:pagemodel_root_url" data-sly-use.page="com.adobe.cq.sample.spa.journal.models.AppPage" content="${page.rootUrl}"/>
<sly data-sly-use.clientlib="/libs/granite/sightly/templates/clientlib.html">
    <sly data-sly-call="${clientlib.css @ categories='we-retail-journal-react'}"/>
</sly>
```

>[!NOTE]
>
>구성 요소의 Sling 모델 표현을 요청할 때 기본 모델 선택기가 정적으로 설정됩니다.

## 메타 속성 {#meta-properties}

* `cq:wcmmode`:편집기의 WCM 모드(예: 페이지, 템플릿)
* `cq:pagemodel_root_url`:앱의 루트 모델의 URL입니다. 하위 페이지 모델이 앱 루트 모델의 조각이므로 하위 페이지에 직접 액세스할 때 중요합니다. 그런 다음 `PageModelManager`은(는) 응용 프로그램 초기 모델을 해당 루트 시작 지점에서 응용 프로그램을 입력하는 것을 체계적으로 권장합니다.
* `cq:pagemodel_router`:라이브러리 [`ModelRouter`](routing.md) 의 를 활성화하거나  `PageModelManager` 비활성화합니다
* `cq:pagemodel_route_filters`:무시해야 하는 경로를 제공하기 위해 쉼표로 구분된 목록 또는 정규  [`ModelRouter`](routing.md) 표현식입니다.

## 페이지 편집기 오버레이 동기화 {#page-editor-overlay-synchronization}

오버레이의 동기화는 `cq.authoring.page` 카테고리에서 제공하는 매우 동일한 돌연변이 관찰자에 의해 보장됩니다.

## Sling 모델 JSON을 내보낸 구조 구성 {#sling-model-json-exported-structure-configuration}

라우팅 기능이 활성화되면 AEM 탐색 구성 요소의 JSON 내보내기 덕분에 SPA의 JSON 내보내기에 애플리케이션의 다른 경로가 포함되어 있다고 가정합니다. AEM 탐색 구성 요소의 JSON 출력은 다음 두 속성을 통해 SPA 루트 페이지 컨텐츠 정책에 구성할 수 있습니다.

* `structureDepth`:내보낸 트리의 깊이에 해당하는 번호
* `structurePatterns`:내보낼 페이지에 해당하는 레지엑스 배열을 재생성합니다
