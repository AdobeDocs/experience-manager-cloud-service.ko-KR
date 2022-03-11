---
title: ContextHub 확장
description: 제공된 항목이 솔루션 요구 사항을 충족하지 못할 경우 새로운 유형의 ContextHub 저장소 및 모듈을 정의합니다
exl-id: ba817c18-f8bd-485d-b043-87593a6a93b5
source-git-commit: 90de3cf9bf1c949667f4de109d0b517c6be22184
workflow-type: tm+mt
source-wordcount: '628'
ht-degree: 0%

---

# ContextHub 확장 {#extending-contexthub}

제공된 항목이 솔루션 요구 사항을 충족하지 못할 경우 새로운 유형의 ContextHub 저장소 및 모듈을 정의합니다.

## 사용자 지정 저장소 후보 만들기 {#creating-custom-store-candidates}

ContextHub 저장소는 등록된 저장소 후보로부터 만들어집니다. 사용자 지정 스토어를 만들려면 저장소 후보자를 만들고 등록해야 합니다.

저장소 후보자를 만들고 등록하는 코드가 포함된 Javascript 파일은 [클라이언트 라이브러리 폴더](/help/implementing/developing/introduction/clientlibs.md). 폴더의 카테고리는 다음 패턴과 일치해야 합니다.

```xml
contexthub.store.[storeType]
```

다음 `storeType` 카테고리의 부분은 다음과 같습니다 `storeType` 상점 입점자가 등록된 곳 (자세한 내용은 [ContextHub 저장소 후보 등록](#registering-a-contexthub-store-candidate)). 예를 들어 storeType의 경우 `contexthub.mystore`를 채울 경우 클라이언트 라이브러리 폴더의 범주는 다음과 같아야 합니다. `contexthub.store.contexthub.mystore`.

### ContextHub 저장소 후보 만들기 {#creating-a-contexthub-store-candidate}

저장소 후보를 만들려면 [`ContextHub.Utils.inheritance.inherit`](contexthub-api.md#inherit-child-parent) 기본 저장소 중 하나를 확장하는 기능:

* [&#39;ContextHub.Store.PersistentStore&#39;](contexthub-api.md#contexthub-store-persistedstore)
* [&#39;ContextHub.Store.SessionStore&#39;](contexthub-api.md#contexthub-store-sessionstore)
* [&#39;ContextHub.Store.JSONPStore&#39;](contexthub-api.md#contexthub-store-jsonpstore)
* [&#39;ContextHub.Store.PersistentJSONPStore&#39;](contexthub-api.md#contexthub-store-persistedjsonpstore)

각 기본 스토어는 [`ContextHub.Store.Core`](contexthub-api.md#contexthub-store-core) 저장.

다음 예에서는 `ContextHub.Store.PersistedStore` 저장소 후보:

```javascript
myStoreCandidate = function(){};
ContextHub.Utils.inheritance.inherit(myStoreCandidate,ContextHub.Store.PersistedStore);
```

현실적으로, 사용자 지정 스토어 후보자는 추가 기능을 정의하거나 스토어의 초기 구성을 재정의합니다. 몇 개 [샘플 저장소 후보](sample-stores.md) 이 아래 저장소에 설치됩니다 `/libs/granite/contexthub/components/stores`.

### ContextHub 저장소 후보 등록 {#registering-a-contexthub-store-candidate}

저장소 후보를 등록하여 ContextHub 프레임워크와 통합하고 저장소 만들기를 활성화합니다. 저장소 후보를 등록하려면 [`registerStoreCandidate`](contexthub-api.md#registerstorecandidate-store-storetype-priority-applies) 함수 `ContextHub.Utils.storeCandidates` 클래스 이름을 지정합니다.

저장소 후보자를 등록할 때 저장소 유형의 이름을 입력합니다. 후보자로부터 저장소를 만들 때 저장소 유형을 사용하여 저장소 유형이 기반으로 하는 후보를 식별합니다.

저장소 후보자를 등록할 때 우선순위가 표시됩니다. 이미 등록한 점포후보자와 같은 타입의 상표를 사용하여 상인등록을 하면 우선순위가 높은 후보자를 사용한다. 따라서 새 구현으로 기존 저장소 후보자를 재정의할 수 있습니다.

```javascript
ContextHub.Utils.storeCandidates.registerStoreCandidate(myStoreCandidate,
                                'contexthub.mystorecandidate', 0);
```

대부분의 경우 한 명의 후보만 필요하며 우선순위를 `0`하지만 관심이 있다면 [고급 등록,](contexthub-api.md#registerstorecandidate-store-storetype-priority-applies) 를 사용하면 javascript 조건(`applies`) 및 후보 우선 순위입니다.

## ContextHub UI 모듈 유형 만들기 {#creating-contexthub-ui-module-types}

다음과 같은 UI 모듈 유형을 만들 때 [ContextHub와 함께 설치됨](sample-modules.md) 요구 사항을 충족하지 않습니다. UI 모듈 유형을 만들려면 `ContextHub.UI.BaseModuleRenderer` 클래스 이름을 지정한 다음 `ContextHub.UI`.

UI 모듈 렌더러를 만들려면 `Class` UI 모듈을 렌더링하는 논리를 포함하는 개체입니다. 최소한 클래스는 다음 작업을 수행해야 합니다.

* 확장 `ContextHub.UI.BaseModuleRenderer` 클래스 이름을 지정합니다. 이 클래스는 모든 UI 모듈 렌더러에 대한 기본 구현입니다. 다음 `Class` object 는 라는 속성을 정의합니다 `extend` 이 클래스의 이름을 확장 중인 클래스로 지정하는 데 사용합니다.
* 기본 구성을 제공합니다. 만들기 `defaultConfig` 속성을 사용합니다. 이 속성은 [`contexthub.base`](sample-modules.md#contexthub-base-ui-module-type) UI 모듈 및 필요한 기타 모든 속성.

소스 `ContextHub.UI.BaseModuleRenderer` 에 있습니다. `/libs/granite/contexthub/code/ui/container/js/ContextHub.UI.BaseModuleRenderer.js`.  렌더러를 등록하려면 [`registerRenderer`](contexthub-api.md#registerrenderer-moduletype-renderer-dontrender) 의 방법 `ContextHub.UI` 클래스 이름을 지정합니다. 모듈 유형의 이름을 입력해야 합니다. 관리자는 이 렌더러를 기반으로 UI 모듈을 만들 때 이 이름을 지정합니다.

렌더러 클래스를 만들어 자체 실행 익명 함수에서 등록합니다. 다음 예제는 `contexthub.browserinfo` UI 모듈. 이 UI 모듈은 `ContextHub.UI.BaseModuleRenderer` 클래스 이름을 지정합니다.

```javascript
;(function() {

    var SurferinfoRenderer = new Class({
        extend: ContextHub.UI.BaseModuleRenderer,

        defaultConfig: {
            icon: 'coral-Icon--globe',
            title: 'Browser/OS Information',

            storeMapping: {
                surferinfo: 'surferinfo'
            },

            template:
                '<p>{{surferinfo.browser.family}} {{surferinfo.browser.version}}</p>' +
                '<p>{{surferinfo.os.name}} {{surferinfo.os.version}}</p>'
        }
    });

    ContextHub.UI.registerRenderer('contexthub.browserinfo', new SurferinfoRenderer());

}());
```

렌더러를 만들고 등록하는 코드가 포함된 Javascript 파일은 [클라이언트 라이브러리 폴더](/help/implementing/developing/introduction/clientlibs.md). 폴더의 카테고리는 다음 패턴과 일치해야 합니다.

```javascript
contexthub.module.[moduleType]
```

다음 `[moduleType]` 카테고리의 부분은 다음과 같습니다 `moduleType` 모듈 렌더러가 등록된 예를 들어 `moduleType` 의 `contexthub.browserinfo`를 채울 경우 클라이언트 라이브러리 폴더의 범주는 다음과 같아야 합니다. `contexthub.module.contexthub.browserinfo`.
