---
title: ContextHub 확장
description: 제공된 항목이 솔루션 요구 사항을 충족하지 않을 때 새로운 유형의 ContextHub 저장소 및 모듈을 정의합니다.
translation-type: tm+mt
source-git-commit: 1c518830f0bc9d9c7e6b11bebd6c0abd668ce040
workflow-type: tm+mt
source-wordcount: '624'
ht-degree: 0%

---


# ContextHub 확장 {#extending-contexthub}

제공된 항목이 솔루션 요구 사항을 충족하지 않을 때 새로운 유형의 ContextHub 저장소 및 모듈을 정의합니다.

## 사용자 지정 스토어 후보자 {#creating-custom-store-candidates} 만들기

ContextHub 스토어는 등록된 스토어 후보자로부터 만들어집니다. 사용자 정의 스토어를 만들려면 스토어 지원자를 만들고 등록해야 합니다.

저장소 후보를 만들고 등록하는 코드를 포함하는 javascript 파일은 [클라이언트 라이브러리 폴더](/help/implementing/developing/introduction/clientlibs.md)에 포함되어야 합니다. 폴더의 카테고리는 다음 패턴과 일치해야 합니다.

```xml
contexthub.store.[storeType]
```

범주의 `storeType` 부분은 스토어 후보가 등록된 `storeType`입니다. ([ContextHub 저장소 후보 등록](#registering-a-contexthub-store-candidate) 참조). 예를 들어 `contexthub.mystore`의 storeType의 경우 클라이언트 라이브러리 폴더의 카테고리는 `contexthub.store.contexthub.mystore`이어야 합니다.

### ContextHub 저장소 후보 {#creating-a-contexthub-store-candidate} 만들기

스토어 후보를 만들려면 [`ContextHub.Utils.inheritance.inherit`](contexthub-api.md#inherit-child-parent) 함수를 사용하여 기본 스토어 중 하나를 확장합니다.

* [`ContextHub.Store.PersistedStore`](contexthub-api.md#contexthub-store-persistedstore)
* [`ContextHub.Store.SessionStore`](contexthub-api.md#contexthub-store-sessionstore)
* [`ContextHub.Store.JSONPStore`](contexthub-api.md#contexthub-store-jsonpstore)
* [`ContextHub.Store.PersistedJSONPStore`](contexthub-api.md#contexthub-store-persistedjsonpstore)

각 기본 스토어는 [`ContextHub.Store.Core`](contexthub-api.md#contexthub-store-core) 스토어를 확장합니다.

다음 예제에서는 `ContextHub.Store.PersistedStore` 스토어 후보자의 가장 간단한 확장자를 만듭니다.

```javascript
myStoreCandidate = function(){};
ContextHub.Utils.inheritance.inherit(myStoreCandidate,ContextHub.Store.PersistedStore);
```

현실적으로, 사용자 지정 스토어 지원자는 추가 기능을 정의하거나 스토어의 초기 구성을 무효화합니다. 일부 [샘플 스토어 후보](sample-stores.md)가 `/libs/granite/contexthub/components/stores` 아래의 저장소에 설치되어 있습니다.

### ContextHub 저장소 후보 등록 {#registering-a-contexthub-store-candidate}

스토어 후보를 등록하여 ContextHub 프레임워크와 통합하고 이를 통해 스토어를 만들 수 있습니다. 스토어 후보를 등록하려면 `ContextHub.Utils.storeCandidates` 클래스의 [`registerStoreCandidate`](contexthub-api.md#registerstorecandidate-store-storetype-priority-applies) 함수를 사용하십시오.

상점 후보를 등록할 때 스토어 유형의 이름을 입력합니다. 후보자로부터 스토어를 만들 때 스토어 유형을 사용하여 스토어가 기반이 되는 후보를 식별합니다.

상점 후보를 등록할 때 우선순위가 표시됩니다. 이미 등록한 스토어 후보자와 같은 유형을 사용하여 등록한 경우 우선 순위가 높은 후보가 사용됩니다. 따라서 기존 스토어 후보자를 새 구현으로 재정의할 수 있습니다.

```javascript
ContextHub.Utils.storeCandidates.registerStoreCandidate(myStoreCandidate,
                                'contexthub.mystorecandidate', 0);
```

대부분의 경우 한 명의 후보자만 필요하고 우선 순위를 `0`으로 설정할 수 있지만 관심 있는 경우 [보다 고급 등록에 대해 알 수 있습니다. 단, Javascript 조건(`applies`) 및 후보 우선 순위를 기준으로 몇 개의 스토어 구현 중 하나를 선택할 수 있는 ](contexthub-api.md#registerstorecandidate-store-storetype-priority-applies)입니다.

## ContextHub UI 모듈 유형 만들기 {#creating-contexthub-ui-module-types}

ContextHub](sample-modules.md)과 함께 설치된 [이 요구 사항을 충족하지 않을 때 사용자 지정 UI 모듈 유형을 만듭니다. UI 모듈 유형을 만들려면 `ContextHub.UI.BaseModuleRenderer` 클래스를 확장하고 `ContextHub.UI`에 등록하여 새 UI 모듈 렌더러를 만듭니다.

UI 모듈 렌더러를 만들려면 UI 모듈을 렌더링하는 논리를 포함하는 `Class` 개체를 만듭니다. 최소한 클래스는 다음 작업을 수행해야 합니다.

* `ContextHub.UI.BaseModuleRenderer` 클래스를 확장합니다. 이 클래스는 모든 UI 모듈 렌더러에 대한 기본 구현입니다. `Class` 개체는 확장되는 것으로 이 클래스의 이름을 지정하는 데 사용하는 `extend`이라는 속성을 정의합니다.
* 기본 구성을 제공합니다. `defaultConfig` 속성을 만듭니다. 이 속성은 [`contexthub.base`](sample-modules.md#contexthub-base-ui-module-type) UI 모듈에 대해 정의된 속성과 필요한 기타 속성을 포함하는 오브젝트입니다.

`ContextHub.UI.BaseModuleRenderer`의 원본이 `/libs/granite/contexthub/code/ui/container/js/ContextHub.UI.BaseModuleRenderer.js`에 있습니다.  렌더러를 등록하려면 `ContextHub.UI` 클래스의 [`registerRenderer`](contexthub-api.md#registerrenderer-moduletype-renderer-dontrender) 메서드를 사용합니다. 모듈 유형의 이름을 입력해야 합니다. 관리자는 이 렌더러를 기반으로 UI 모듈을 만들 때 이 이름을 지정합니다.

자동 실행 익명 함수에서 렌더러 클래스를 만들고 등록합니다. 다음 예제는 `contexthub.browserinfo` UI 모듈의 소스 코드를 기반으로 합니다. 이 UI 모듈은 `ContextHub.UI.BaseModuleRenderer` 클래스의 간단한 확장입니다.

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

렌더러를 만들고 등록하는 코드를 포함하는 javascript 파일은 [클라이언트 라이브러리 폴더](/help/implementing/developing/introduction/clientlibs.md)에 포함되어야 합니다. 폴더의 카테고리는 다음 패턴과 일치해야 합니다.

```javascript
contexthub.module.[moduleType]
```

범주의 `[moduleType]` 부분은 모듈 렌더러가 등록된 `moduleType`입니다. 예를 들어 `contexthub.browserinfo`의 `moduleType`의 경우 클라이언트 라이브러리 폴더의 카테고리는 `contexthub.module.contexthub.browserinfo`여야 합니다.
