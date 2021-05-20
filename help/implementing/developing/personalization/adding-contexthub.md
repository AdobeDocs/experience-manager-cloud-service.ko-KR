---
title: 페이지에 ContextHub 추가 및 저장소 액세스
description: 페이지에 ContextHub를 추가하여 ContextHub 기능을 활성화하고 ContextHub Javascript 라이브러리에 연결합니다
exl-id: 8bfe2cff-3944-4e86-a95c-ebf1cb13913c
source-git-commit: 90de3cf9bf1c949667f4de109d0b517c6be22184
workflow-type: tm+mt
source-wordcount: '927'
ht-degree: 1%

---

# 페이지에 ContextHub 추가 및 저장소 액세스 {#adding-contexthub-to-pages-and-accessing-stores}

페이지에 ContextHub를 추가하여 ContextHub 기능을 활성화하고 ContextHub Javascript 라이브러리에 연결합니다.

ContextHub Javascript API는 ContextHub에서 관리하는 컨텍스트 데이터에 대한 액세스를 제공합니다. 이 페이지에서는 컨텍스트 데이터 액세스 및 조작에 대한 API의 주요 기능에 대해 간략하게 설명합니다. API 참조 설명서 링크를 따라 자세한 정보 및 코드 예제를 참조하십시오.

## 페이지 구성 요소에 ContextHub 추가 {#adding-contexthub-to-a-page-component}

ContextHub 기능을 활성화하고 ContextHub Javascript 라이브러리에 연결하려면 페이지의 `head` 섹션에 `contexthub` 구성 요소를 포함하십시오. 페이지 구성 요소의 HTL 코드는 다음 예와 유사해야 합니다.

```xml
<sly data-sly-resource="${'contexthub' @ resourceType='granite/contexthub/components/contexthub'}"/>
```

또한 ContextHub 도구 모음이 미리 보기 모드에 표시되는지를 구성해야 합니다. [ContextHub UI](configuring-contexthub.md#showing-and-hiding-the-contexthub-ui) 표시 및 숨기기 를 참조하십시오.

## ContextHub 저장소 {#about-contexthub-stores} 정보

ContextHub 저장소를 사용하여 컨텍스트 데이터를 유지합니다. ContextHub에서는 모든 저장소 유형을 기반으로 하는 다음과 같은 유형의 저장소를 제공합니다.

* [PersistentStore](contexthub-api.md#contexthub-store-persistedstore)
* [SessionStore](contexthub-api.md#contexthub-store-sessionstore)
* [JSONPStore](contexthub-api.md#contexthub-store-persistedjsonpstore)
* [지속형 JSONPStore](contexthub-api.md#contexthub-store-persistedstore)

모든 저장소 유형은 [`ContextHub.Store.Core`](contexthub-api.md#contexthub-store-core) 클래스의 확장입니다. 새 저장소 유형을 만드는 방법에 대한 내용은 [사용자 지정 저장소 만들기](extending-contexthub.md#creating-custom-store-candidates)를 참조하십시오. 샘플 저장소 유형에 대한 자세한 내용은 [샘플 ContextHub 저장소 후보](sample-stores.md)를 참조하십시오.

### 지속성 모드 {#persistence-modes}

Context Hub 저장소는 다음 지속성 모드 중 하나를 사용합니다.

* **로컬:** HTML5 localStorage를 사용하여 데이터를 유지합니다. 로컬 저장소는 세션 간 브라우저에 유지됩니다.
* **세션:** HTML5 sessionStorage를 사용하여 데이터를 유지합니다. 세션 저장소는 브라우저 세션 기간 동안 유지되며 모든 브라우저 창에서 사용할 수 있습니다.
* **쿠키:** 데이터 저장소에 대한 브라우저의 기본 쿠키 지원을 사용합니다. 쿠키 데이터는 HTTP 요청에서 서버로 및 서버에서 전송됩니다.
* **Window.name:** window.name 속성을 사용하여 데이터를 유지합니다.
* **메모리:** Javascript 개체를 사용하여 데이터를 유지합니다.

기본적으로 Context Hub는 로컬 지속성 모드를 사용합니다. 브라우저가 HTML5 localStorage를 지원하지 않거나 허용하지 않는 경우 세션 지속성이 사용됩니다. 브라우저가 HTML5 sessionStorage를 지원하지 않거나 허용하지 않는 경우 Window.name 지속성이 사용됩니다.

### 데이터 저장 {#store-data}

내부적으로, 데이터 형식은 트리 구조로 저장되므로 값을 기본 형식 또는 복잡한 개체로 추가할 수 있습니다. 저장소에 복잡한 개체를 추가하면 개체 속성이 데이터 트리에 분기됩니다. 예를 들어 다음 복잡한 개체가 location이라는 빈 저장소에 추가됩니다.

```javascript
Object {
   number: 321,
   data: {
      city: "Basel",
      country: "Switzerland",
      details: {
         population: 173330,
         elevation: 260
      }
   }
}
```

저장소 데이터의 트리 구조는 다음과 같이 개념화할 수 있습니다.

```text
/
|- number
|- data
      |- city
      |- country
      |- details
            |- population
            |- elevation
```

트리 구조는 저장소의 데이터 항목을 키/값 쌍으로 정의합니다. 위의 예에서 키 `/number`은 값 `321`에 해당하고 키 `/data/country`는 값 `Switzerland`에 해당합니다.

### 개체 조작 {#manipulating-objects}

ContextHub는 Javascript 개체를 조작하기 위한 [`ContextHub.Utils.JSON.tree`](contexthub-api.md#contexthub-utils-json-tree) 클래스를 제공합니다. 저장소에 추가하기 전에 또는 저장소에서 가져온 후에 Javascript 개체를 조작하는 데 이 클래스의 함수를 사용합니다.

또한 [`ContextHub.Utils.JSON`](contexthub-api.md#contexthub-utils-json) 클래스는 개체를 문자열로 직렬화하고 문자열을 객체로 역직렬화하는 기능을 제공합니다. 기본적으로 `JSON.parse` 및 `JSON.stringify` 함수를 포함하지 않는 브라우저를 지원하려면 JSON 데이터를 처리하는 데 이 클래스를 사용하십시오.

## ContextHub 스토어와 상호 작용 {#interacting-with-contexthub-stores}

[`ContextHub`](contexthub-api.md#ui-event-constants) Javascript 개체를 사용하여 저장소를 Javascript 개체로 가져옵니다. 저장소 개체를 가져오면 포함된 데이터를 조작할 수 있습니다. [`getAllStores`](contexthub-api.md#getallstores) 또는 [`getStore`](contexthub-api.md#getstore-name) 함수를 사용하여 저장소를 가져옵니다.

### 저장소 데이터 {#accessing-store-data} 액세스

[`ContexHub.Store.Core`](contexthub-api.md#contexthub-store-core) Javascript 클래스는 저장소 데이터와 상호 작용하기 위한 여러 함수를 정의합니다. 다음 함수는 개체에 포함된 여러 데이터 항목을 저장하고 검색합니다.

* [addAllItems](contexthub-api.md#addallitems-tree-options)
* [getTree](contexthub-api.md#gettree-includeinternals)

개별 데이터 항목은 키/값 쌍 세트로 저장됩니다. 값을 저장하고 검색하려면 해당 키를 지정합니다.

* [getItem](contexthub-api.md#getitem-key)
* [setItem](contexthub-api.md#setitem-key-value-options)

사용자 지정 저장소 후보들은 데이터를 저장할 수 있는 액세스 권한을 제공하는 추가 기능을 정의할 수 있습니다.

>[!NOTE]
>
>ContextHub는 기본적으로 게시 서버에서 사용되는 현재 로그인한 사용자를 인식하지 않으며 이러한 사용자는 ContextHub에서 &quot;익명&quot;으로 간주됩니다.
>
>프로필 저장소를 로드하여 ContextHub에서 로그인한 사용자를 인식하도록 할 수 있습니다. 여기](https://github.com/Adobe-Marketing-Cloud/aem-sample-we-retail/blob/master/ui.apps/src/main/content/jcr_root/apps/weretail/components/structure/header/clientlib/js/utilities.js)에 있는 GitHub의 [샘플 코드를 참조하십시오.

### ContextHub 이벤트 {#contexthub-eventing}

ContextHub에는 이벤트를 저장하는 데 자동으로 대응할 수 있는 이벤트 프레임워크가 포함되어 있습니다. 각 저장소 개체에는 저장소의 [`eventing`](contexthub-api.md#eventing) 속성으로 사용할 수 있는 [`ContextHub.Utils.Eventing`](contexthub-api.md#contexthub-utils-eventing) 개체가 있습니다. Javascript 함수를 저장소 이벤트에 바인딩하려면 [`on`](contexthub-api.md#on-name-handler-selector-triggerforpastevents) 또는 [`once`](contexthub-api.md#once-name-handler-selector-triggerforpastevents) 함수를 사용합니다.

## Context Hub를 사용하여 쿠키 조작 {#using-context-hub-to-manipulate-cookies}

Context Hub Javascript API는 브라우저 쿠키 처리에 대한 브라우저 간 지원을 제공합니다. [`ContextHub.Utils.Cookie`](contexthub-api.md#contexthub-utils-cookie) 네임스페이스는 쿠키를 만들고, 조작하고, 삭제하는 몇 가지 함수를 정의합니다.

## 해결된 ContextHub 세그먼트 확인 {#determining-resolved-contexthub-segments}

ContextHub 세그먼트 엔진을 사용하면 현재 컨텍스트에서 해결된 등록된 세그먼트 중 하나를 결정할 수 있습니다. [`ContextHub.SegmentEngine.SegmentManager`](contexthub-api.md#contexthub-segmentengine-segmentmanager) 클래스의 getResolvedSegments 함수를 사용하여 해결된 세그먼트를 검색합니다. 그런 다음 [`ContextHub.SegmentEngine.Segment`](contexthub-api.md#contexthub-segmentengine-segment) 클래스의 `getName` 또는 `getPath` 함수를 사용하여 세그먼트를 테스트합니다.

### ContextHub 선분 {#contexthub-segments}

ContextHub 세그먼트는 `/conf/<site>/settings/wcm/segments` 노드 아래에 설치됩니다.

다음 세그먼트는 [WKND 자습서 사이트와 함께 설치됩니다.](/help/implementing/developing/introduction/develop-wknd-tutorial.md)

* 여름
* 겨울

이러한 세그먼트를 해결하는 데 사용되는 규칙은 다음과 같이 요약됩니다.

* 먼저 [지리적 위치](sample-stores.md#contexthub-geolocation-sample-store-candidate) 스토어를 사용하여 사용자의 위도를 결정합니다.
* 그런 다음 [surferinfo store](sample-stores.md#contexthub-surferinfo-sample-store-candidate)의 월 데이터 항목이 해당 위도에 있는 계절을 결정합니다.

>[!WARNING]
>
>설치된 세그먼트는 프로젝트에 대한 고유한 전용 구성을 만드는 데 도움이 되는 참조 구성으로 제공되며 이러한 구성을 직접 사용하지 않아야 합니다.

## ContextHub {#debugging-contexthub} 디버깅

로그 생성을 포함하여 ContextHub를 디버깅하는 여러 가지 옵션이 있습니다. 자세한 내용은 [ContextHub 구성 을 참조하십시오.](configuring-contexthub.md#logging-debug-messages-for-contexthub)

## ContextHub 프레임워크 {#see-an-overview-of-the-contexthub-framework} 개요를 참조하십시오.

ContextHub에서는 ContextHub 프레임워크의 개요를 볼 수 있는 [진단 페이지](contexthub-diagnostics.md)을 제공합니다.
