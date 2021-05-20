---
title: ContextHub Javascript API 참조
description: ContextHub 구성 요소를 페이지에 추가한 경우 스크립트에 ContextHub Javascript API를 사용할 수 있습니다
exl-id: ec35bef5-610c-4e85-a43a-d4201b5eb03e
source-git-commit: 90de3cf9bf1c949667f4de109d0b517c6be22184
workflow-type: tm+mt
source-wordcount: '4621'
ht-degree: 1%

---

# ContextHub Javascript API 참조 {#contexthub-javascript-api-reference}

ContextHub Javascript API는 [ContextHub 구성 요소가 페이지](adding-contexthub.md)에 추가되면 스크립트에 사용할 수 있습니다.

## ContextHub 상수 {#contexthub-constants}

ContextHub Javascript API가 정의하는 상수 값입니다.

### 이벤트 상수 {#event-constants}

다음 표에는 ContextHub 저장소에 대해 발생하는 이벤트 이름이 나와 있습니다. [ContextHub.Utils.Events](#contexthub-utils-eventing)도 참조하십시오.

| 상수 | 설명 | 값 |
|---|---|---|
| `ContextHub.Constants.EVENT_NAMESPACE` | ContextHub의 이벤트 네임스페이스 | `ch` |
| `ContextHub.Constants.EVENT_ALL_STORES_READY` | 모든 필수 저장소가 등록되고 초기화되며 사용할 준비가 되었음을 나타냅니다 | `all-stores-ready` |
| `ContextHub.Constants.EVENT_STORES_PARTIALLY_READY` | 지정된 시간 제한 내에 모든 저장소가 초기화되지 않았음을 나타냅니다 | `stores-partially-ready` |
| `ContextHub.Constants.EVENT_STORE_REGISTERED` | 스토어가 등록되면 실행됩니다. | `store-registered` |
| `ContextHub.Constants.EVENT_STORE_READY` | 저장소가 작동할 준비가 되었음을 나타냅니다. 데이터를 가져올 때 실행되는 JSONP 저장소를 제외하고 등록 후 즉시 트리거됩니다. | `store-ready` |
| `ContextHub.Constants.EVENT_STORE_UPDATED` | 저장소가 지속성을 업데이트할 때 실행됩니다 | `store-updated` |
| `ContextHub.Constants.PERSISTENCE_CONTAINER_NAME` | 지속성 컨테이너 이름 | `ContextHubPersistence` |
| `ContextHub.Constants.SERVICE_RAW_RESPONSE_KEY` | 원시 JSON 결과가 저장되는 특정 지속성 키 이름을 저장합니다 | `/_/raw-response` |
| `ContextHub.Constants.SERVICE_RESPONSE_TIME_KEY` | JSON 데이터를 가져오는 시점을 나타내는 특정 타임스탬프를 저장합니다 | `/_/response-time` |
| `ContextHub.Constants.SERVICE_LAST_URL_KEY` | 마지막 호출 동안 사용된 JSON 서비스의 특정 URL을 저장합니다 | `/_/url` |
| `ContextHub.Constants.IS_CONTAINER_EXPANDED` | ContextHub의 UI가 확장되었는지 여부를 나타냅니다 | `/_/container-expanded` |

### UI 이벤트 상수 {#ui-event-constants}

다음 표에는 ContextHub UI에 대해 발생하는 이벤트 이름이 나와 있습니다.

| **상수** | **설명** | **값** |
|---|---|---|
| `ContextHub.Constants.EVENT_UI_MODE_REGISTERED` | 모드가 등록되면 실행됩니다 | `ui-mode-registered` |
| `ContextHub.Constants.EVENT_UI_MODE_UNREGISTERED` | 모드가 등록되지 않은 경우 실행됩니다 | `ui-mode-unregistered` |
| `ContextHub.Constants.EVENT_UI_MODE_RENDERER_REGISTERED` | 모드 렌더러가 등록되면 실행됩니다 | `ui-mode-renderer-registered` |
| `ContextHub.Constants.EVENT_UI_MODE_RENDERER_UNREGISTERED` | 모드 렌더러가 등록되지 않은 경우 실행됩니다 | `ui-mode-renderer-unregistered` |
| `ContextHub.Constants.EVENT_UI_MODE_ADDED` | 새 모드가 추가되면 실행됩니다 | `ui-mode-added` |
| `ContextHub.Constants.EVENT_UI_MODE_REMOVED` | 모드가 제거되면 실행됩니다 | `ui-mode-removed` |
| `ContextHub.Constants.EVENT_UI_MODE_SELECTED` | 사용자가 모드를 선택하면 실행됩니다 | `ui-mode-selected` |
| `ContextHub.Constants.EVENT_UI_MODULE_REGISTERED` | 새 모듈이 등록되면 실행됩니다 | `ui-module-registered` |
| `ContextHub.Constants.EVENT_UI_MODULE_UNREGISTERED` | 모듈이 등록되지 않은 경우 실행됩니다 | `ui-module-unregistered` |
| `ContextHub.Constants.EVENT_UI_MODULE_RENDERER_REGISTERED` | 모듈 렌더러가 등록될 때 실행됩니다 | `ui-module-renderer-registered` |
| `ContextHub.Constants.EVENT_UI_MODULE_RENDERER_UNREGISTERED` | 모듈 렌더러가 등록되지 않은 경우 실행됩니다 | `ui-module-renderer-unregistered` |
| `ContextHub.Constants.EVENT_UI_MODULE_ADDED` | 새 모듈이 추가되면 실행됩니다 | `ui-module-added` |
| `ContextHub.Constants.EVENT_UI_MODULE_REMOVED` | 모듈이 제거되면 실행됩니다 | `ui-module-removed` |
| `ContextHub.Constants.EVENT_UI_CONTAINER_ADDED` | UI 컨테이너가 페이지에 추가되면 실행됩니다 | `ui-container-added` |
| `ContextHub.Constants.EVENT_UI_CONTAINER_OPENED` | ContextHub UI가 열려 있을 때 실행됩니다 | `ui-container-opened` |
| `ContextHub.Constants.EVENT_UI_CONTAINER_CLOSED` | ContextHub UI가 축소될 때 실행됩니다 | `ui-container-closed` |
| `ContextHub.Constants.EVENT_UI_PROPERTY_MODIFIED` | 속성이 수정될 때 실행됩니다 | `ui-property-modified` |
| `ContextHub.Constants.EVENT_UI_RENDERED` | ContextHub UI가 렌더링될 때마다(예: 속성 변경 후) 실행됩니다 | `ui-rendered` |
| `ContextHub.Constants.EVENT_UI_INITIALIZED` | UI 컨테이너가 초기화될 때 실행됩니다 | `ui-initialized` |
| `ContextHub.Constants.ACTIVE_UI_MODE` | 활성 UI 모드를 나타냅니다 | `/_/active-ui-mode` |

## ContextHub Javascript API 참조 {#contexthub-javascript-api-reference-2}

ContextHub 개체는 모든 저장소에 액세스할 수 있도록 합니다.

### 함수(ContextHub) {#functions-contexthub}

#### getAllStores() {#getallstores}

등록된 모든 ContextHub 저장소를 반환합니다.

이 함수에는 매개 변수가 없습니다.

##### {#returns-} 반환

모든 ContextHub 저장소를 포함하는 객체입니다. 각 저장소는 스토어와 동일한 이름을 사용하는 개체입니다.

##### 예 {#example-}

다음 예제에서는 모든 스토어를 검색한 다음 지리적 위치 스토어를 검색합니다.

```javascript
var allStores = ContextHub.getAllStores();
var geoloc = allStores.geolocation
```

#### getStore(name) {#getstore-name}

저장소를 Javascript 개체로 검색합니다.

##### 매개 변수 {#parameters-}

* **`name`:** 저장소가 등록된 이름입니다.

##### {#returns-getstore-name} 반환

저장소를 나타내는 개체입니다.

##### 예 {#example-getstore-name}

다음 예제에서는 지리적 위치 저장소를 검색합니다.

```javascript
var geoloc = ContextHub.getStore("geolocation");
```

## ContextHub.SegmentEngine.Segment {#contexthub-segmentengine-segment}

ContextHub 세그먼트를 나타냅니다. 세그먼트를 가져오려면 `ContextHub.SegmentEngine.SegmentManager` 을 사용하십시오.

### 함수(ContextHub.ContextEngine.Segment) {#functions-contexthub-contextengine-segment}

#### getName() {#getname}

세그먼트 이름을 문자열 값으로 반환합니다.

#### getPath() {#getpath}

세그먼트 정의의 저장소 경로를 문자열 값으로 반환합니다.

## ContextHub.SegmentEngine.SegmentManager {#contexthub-segmentengine-segmentmanager}

ContextHub 세그먼트에 대한 액세스 권한을 제공합니다.

### 함수(ContextHub.SegmentEngine.SegmentManager) {#functions-contexthub-segmentengine-segmentmanager}

#### getResolvedSegments() {#getresolvedsegments}

현재 컨텍스트에서 해결된 세그먼트를 반환합니다. 이 함수에는 매개 변수가 없습니다.

##### {#returns-getresolvedsegments} 반환

`ContextHub.SegmentEngine.Segment` 개체의 배열입니다.

## ContextHub.Store.Core {#contexthub-store-core}

ContextHub 저장소의 기본 클래스입니다.

### 속성(ContextHub.Store.Core) {#properties-contexthub-store-core}

#### 이벤트 {#eventing}

[`ContextHub.Utils.Eventing`](#contexthub-utils-eventing) 개체. 이벤트를 저장할 함수를 바인딩하는 데 이 개체를 사용합니다. 기본값 및 초기화에 대한 자세한 내용은 [`init(name,config)`](#init-name-config) 을 참조하십시오.

#### 이름 {#name}

저장소의 이름입니다.

#### 지속성 {#persistence}

`ContextHub.Utils.Persistence` 개체. 기본값 및 초기화에 대한 자세한 내용은 [`init(name,config)`](#init-name-config) 을 참조하십시오.

### 함수(ContextHub.Store.Core) {#functions-contexthub-store-core}

#### addAllItems(tree, options) {#addallitems-tree-options}

데이터 개체 또는 배열을 저장소 데이터와 병합합니다. 개체나 배열의 각 키/값 쌍이 저장소에 추가됩니다( `setItem` 함수를 통해).

* **개체:** 키는 속성 이름입니다.
* **배열:**  키는 배열 인덱스입니다.

값은 객체가 될 수 있습니다.

##### 매개 변수 {#parameters-addallitems}

* **`tree`:** (개체 또는 배열) 저장소에 추가할 데이터입니다.
* **`options`**  : (Object) setItem 함수에 전달되는 옵션의 선택적 개체입니다. 자세한 내용은 [`setItem(key,value,options)`](#setitem-key-value-options)의 `options` 매개 변수를 참조하십시오.

##### {#returns-addallitems} 반환

`boolean` 값:

* `true` 값은 데이터 개체가 저장되었음을 나타냅니다.
* `false` 값은 데이터 저장소가 변경되지 않음을 나타냅니다.

#### addReference(key, anotherKey) {#addreference-key-anotherkey}

한 키에서 다른 키로 참조를 만듭니다. 키는 자신을 참조할 수 없습니다.

##### 매개 변수 {#parameters-addreference}

* **`key`:** 를 참조하는 키  `anotherKey`.

* **`anotherkey`** :  `key`이 참조하는 키입니다.

##### {#returns-addreference} 반환

`boolean` 값:

* `true` 값은 참조가 추가되었음을 나타냅니다.
* `false` 값은 참조가 추가되지 않았음을 나타냅니다.

#### announceReadiness() {#announcereadiness}

이 저장소에 대한 `ready` 이벤트를 트리거합니다. 이 함수에는 매개 변수가 없으며 값을 반환하지 않습니다.

#### clean() {#clean}

저장소에서 모든 데이터를 제거합니다. 함수에는 매개 변수 및 반환 값이 없습니다.

#### getItem(key) {#getitem-key}

키와 연결된 값을 반환합니다.

##### 매개 변수 {#parameters-getitem}

* **`key`:**  (문자열) 값을 반환할 키입니다.

##### {#returns-getitem} 반환

키의 값을 나타내는 개체입니다.

#### getKeys(includeInternals) {#getkeys-includeinternals}

저장소에서 키를 검색합니다. 선택적으로 ContextHub 프레임워크에서 내부적으로 사용되는 키를 검색할 수 있습니다.

##### 매개 변수 {#parameters-getkeys}

* **`includeInternals`** : `true` 의 값은결과에 내부적으로 사용되는 키를 포함합니다. 이러한 키는 밑줄(`_`) 문자로 시작합니다. 기본값은 `false`입니다.

##### {#returns-getkeys} 반환

키 이름의 배열입니다( `string` 값).

#### getReferences() {#getreferences}

저장소에서 참조를 검색합니다.

##### {#returns-getreferences} 반환

참조하는 키를 참조된 키의 인덱스로 사용하는 배열입니다.

* 참조하는 키는 `addReference` 함수의 `key` 매개 변수에 해당합니다.
* 참조된 키는 `addReference` 함수의 `anotherKey` 매개 변수에 해당합니다.

#### getTree(includeInternals) {#gettree-includeinternals}

저장소에서 데이터 트리를 검색합니다. 선택적으로 ContextHub 프레임워크에서 내부적으로 사용하는 키/값 쌍을 포함할 수 있습니다.

##### 매개 변수 {#parameters-gettree}

* `includeInternals:` 의 값은  `true` 결과에 내부적으로 사용된 키/값 쌍을 포함합니다. 이 데이터의 키는 밑줄(`_`) 문자로 시작합니다. 기본값은 `false`입니다.

##### {#returns-gettree} 반환

데이터 트리를 나타내는 개체입니다. 키는 개체의 속성 이름입니다.

#### init(name, config) {#init-name-config}

저장소를 초기화합니다.

* 저장소 데이터를 빈 개체로 설정합니다.
* 저장소 참조를 빈 개체로 설정합니다.
* `eventChannel`은 `data:<name>`입니다. 여기서 `<name>`는 저장소 이름입니다.
* `storeDataKey`은 `/store/<name>`입니다. 여기서 `<name>`는 저장소 이름입니다.

##### 매개 변수 {#parameters-init}

* **`name`:** 저장소의 이름입니다.
* **`config`:** 구성 속성을 포함하는 객체입니다.
   * `eventDeferring`: 기본값은 32입니다.
   * `eventing`:이  [저장소의 ContextHub.Utils.](#contexthub-utils-eventing) Eventingobject입니다. 기본값은 `ContextHub.eventing` 개체가 사용하는 것입니다.
   * `persistence`:이  `ContextHub.Utils.Persistence` 저장소의 개체입니다. 기본값은 `ContextHub.persistence` 개체입니다.

#### isEventingPaused() {#iseventingpaused}

이 저장소에 대해 이벤트가 일시 중지되었는지 여부를 결정합니다.

##### {#returns-iseventingpaused} 반환

부울 값:

* `true`:이 저장소에 대해 이벤트가 트리거되지 않도록 이벤트가 일시 중지되었습니다.
* `false`:이벤트가 일시 중지되지 않아 이 저장소에 대해 이벤트가 트리거됩니다.

#### pauseEventing() {#pauseeventing}

이벤트가 트리거되지 않도록 저장소에 대한 이벤트를 일시 중지합니다. 이 함수에는 매개 변수가 필요하지 않으며 값을 반환하지 않습니다.

#### removeItem(key, options) {#removeitem-key-options}

저장소에서 키/값 쌍을 제거합니다.

키가 제거되면 이 함수는 `data` 이벤트를 트리거합니다. 이벤트 데이터에는 저장소 이름, 제거된 키의 이름, 제거된 값, 키에 대한 새 값(null) 및 &quot;제거&quot;의 작업 유형이 포함됩니다.

선택적으로 `data` 이벤트가 트리거되는 것을 방지할 수 있습니다.

##### 매개 변수 {#parameters-removeitem}

* **`key`:**  (문자열) 제거할 키의 이름입니다.
* **`options`:** (개체) 옵션 객체입니다. 다음 개체 속성이 유효합니다.
   * 자동:`true` 값은 `data` 이벤트를 트리거하지 않습니다. 기본값은 `false`입니다.

##### {#returns-removeitem} 반환

`boolean` 값:

* `true` 값은 키/값 쌍이 제거되었음을 나타냅니다.
* `false` 값은 키가 저장소에서 없으므로 데이터 저장소가 변경되지 않음을 나타냅니다.

#### removeReference(key) {#removereference-key}

저장소에서 참조를 제거합니다.

##### 매개 변수 {#parameters-removereference}

* **`key`:** 제거할 키 참조입니다. 이 매개 변수는 `addReference` 함수의 `key` 매개 변수에 해당합니다.

##### {#returns-removereference} 반환

`boolean` 값:

* `true` 값은 참조가 제거되었음을 나타냅니다.
* `false` 값은 키가 유효하지 않으며 저장소가 변경되지 않음을 나타냅니다.

#### reset(keepRemainingData) {#reset-keepremainingdata}

저장소의 지속된 데이터의 초기 값을 재설정합니다. 선택적으로 저장소에서 다른 모든 데이터를 제거할 수 있습니다. 저장소가 다시 설정되는 동안 이벤트가 이 저장소에 대해 일시 중지되었습니다. 이 함수는 값을 반환하지 않습니다.

초기 값은 저장소 개체를 인스턴스화하는 데 사용되는 구성 개체의 `initialValues` 속성에 제공됩니다.

##### 매개 변수 {#parameters-reset}

* **`keepRemainingData`**:(부울) true 값을 지정하면 비초기 데이터가 유지됩니다. false 값을 지정하면 초기 값을 제외하고 모든 데이터가 제거됩니다.

#### resolveReference(키, 다시 시도) {#resolvereference-key-retry}

참조된 키를 검색합니다. 최적 일치 해결을 위해 사용할 반복 횟수를 지정할 수 있습니다(선택적).

##### 매개 변수 {#parameters-resolvereference}

* **`key`:**  (문자열) 참조를 확인할 키입니다. 이 `key` 매개 변수는 `addReference` 함수의 `key` 매개 변수에 해당합니다.
* **`retry`:**  (숫자) 사용할 반복 횟수입니다.

##### {#returns-resolvereference} 반환

참조된 키를 나타내는 `string` 값입니다. 참조가 해결되지 않으면 `key` 매개 변수의 값이 반환됩니다.

#### resumeEventing() {#resumeeventing}

이벤트가 트리거되도록 이 저장소에 대한 이벤트를 다시 시작합니다. 이 함수는 매개 변수를 정의하지 않으며 값을 반환하지 않습니다.

#### setItem(키, 값, 옵션) {#setitem-key-value-options}

키/값 쌍을 저장소에 추가합니다.

키에 대한 값이 키에 현재 저장된 값과 다른 경우에만 `data` 이벤트를 트리거합니다. 선택적으로 `data` 이벤트를 트리거하지 않도록 할 수 있습니다.

이벤트 데이터에는 저장소 이름, 키, 이전 값, 새 값 및 `set` 작업 유형이 포함됩니다.

##### 매개 변수 {#parameters-setitem}

* **`key`:**  (문자열) 키의 이름입니다.
* **`options`:** (개체) 옵션 객체입니다. 다음 개체 속성이 유효합니다.
   * `silent`:값을 지정하면  `true` 이벤트가 트리거되지  `data` 않습니다. 기본값은 `false`입니다.
* **`value`:**  (개체) 키와 연결할 값입니다.

##### {#returns-setitem} 반환

`boolean` 값:

* `true` 값은 데이터 개체가 저장되었음을 나타냅니다.
* `false` 값은 데이터 저장소가 변경되지 않음을 나타냅니다.

## ContextHub.Store.JSONPStore {#contexthub-store-jsonpstore}

JSON 데이터를 포함하는 스토어. 데이터는 외부 JSONP 서비스에서 검색되거나, 선택적으로 JSON 데이터를 반환하는 서비스에서 검색됩니다. 이 클래스의 인스턴스를 만들 때 [`init`](#init-name-config) 함수를 사용하여 서비스 세부 정보를 지정합니다.

저장소는 메모리 내 지속성을 사용합니다(Javascript 변수). 데이터 저장 은 페이지 수명 동안에만 사용할 수 있습니다.

ContextHub.Store.JSONPStore는 [ContextHub.Store.Core](#contexthub-store-core)를 확장하고 해당 클래스의 함수를 상속합니다.

### 함수(ContextHub.Store.JSONPStore) {#functions-contexthub-store-jsonpstore}

#### configureService(serviceConfig, override) {#configureservice-serviceconfig-override}

이 개체가 사용하는 JSONP 서비스에 연결하는 세부 정보를 구성합니다. 기존 구성을 업데이트하거나 바꿀 수 있습니다. 함수는 값을 반환하지 않습니다.

##### 매개 변수 {#parameters-configureservice}

* **`serviceConfig`:** 다음 속성을 포함하는 객체입니다.
   * `host`:(문자열) 서버 이름 또는 IP 주소입니다.
   * `jsonp`:(부울) true 값을 지정하면 서비스가 JSONP 서비스임을 나타내고, 그렇지 않으면 false를 나타냅니다. true인 경우 {callback:&quot;ContextHub.Callback.*Object.name*} 개체가 service.params 개체에 추가됩니다.
   * `params`:(개체) 개체 속성으로 표시되는 URL 매개 변수입니다. 매개 변수 이름은 속성 이름이고 매개 변수 값은 속성 값입니다.
   * `path`:(문자열) 서비스의 경로입니다.
   * `port`:(번호) 서비스의 포트 번호입니다.
   * `secure`:(문자열 또는 부울) 서비스 URL에 사용할 프로토콜을 결정합니다.
      * `auto`: //
      * `true`:https://
      * `false`: 세션이://
* **재정의:**  (부울). `true` 값을 사용하면 기존 서비스 구성이 `serviceConfig` 속성으로 대체됩니다. `false` 값을 사용하면 기존 서비스 구성 속성이 `serviceConfig` 속성과 병합됩니다.

#### getRawResponse() {#getrawresponse}

JSONP 서비스에 대한 마지막 호출 이후 캐시된 원시 응답을 반환합니다. 함수에는 매개 변수가 필요하지 않습니다.

##### {#returns-getrawresponse} 반환

원시 응답을 나타내는 객체입니다.

#### getServiceDetails() {#getservicedetails}

이 ContextHub.Store.JSONPStore 개체의 서비스 개체를 검색합니다. 서비스 개체에는 서비스 URL을 만드는 데 필요한 모든 정보가 들어 있습니다.

##### {#returns-getservicedetails} 반환

다음 속성을 갖는 객체:

* **`host`:**  (문자열) 서버 이름 또는 IP 주소입니다.
* **`jsonp`**  : (부울) true 값을 지정하면 서비스가 JSONP 서비스임을 나타내고, 그렇지 않으면 false를 나타냅니다. true인 경우 {callback:&quot;ContextHub.Callback.*Object.name*} 개체가 service.params 개체에 추가됩니다.
* **`params`:**  (개체) 개체 속성으로 표시되는 URL 매개 변수입니다. 매개 변수 이름은 속성 이름이고 매개 변수 값은 속성 값입니다.
* **`path`:**  (문자열) 서비스의 경로입니다.
* **`port`:**  (번호) 서비스의 포트 번호입니다.
* **`secure`:** (String 또는 Boolean) 서비스 URL에 사용할 프로토콜을 결정합니다.
   * `auto`://
   * `true`:https://
   * `false`: 세션이://

#### getServiceURL(resolve) {#getserviceurl-resolve}

JSONP 서비스의 URL을 검색합니다.

##### 매개 변수 {#parameters-getserviceurl}

* **`resolve`:**  (부울) URL에 확인된 매개 변수를 포함할지 여부를 결정합니다. `true` 값은 매개 변수를 확인하며 `false` 값은 매개 변수를 해결하지 않습니다.

##### {#returns-getserviceurl} 반환

서비스 URL을 나타내는 `string` 값입니다.

#### init(name, config) {#init-name-config-1}

`ContextHub.Store.JSONPStore` 개체를 초기화합니다.

##### 매개 변수 {#parameters-init-1}

* **`name`:**  (문자열) 저장소의 이름입니다.
* **`config`:**  (Object) 서비스 속성을 포함하는 객체입니다. JSONPStore 개체는 `service` 개체의 속성을 사용하여 JSONP 서비스의 URL을 구성합니다.
   * `eventDeferring`:32.
   * `eventing`:이 저장소에 대한 ContextHub.Utils.Eventing 개체입니다. 기본값은 `ContextHub.eventing` 개체입니다.
   * `persistence`:이 저장소에 대한 ContextHub.Utils.Persistence 개체입니다. 기본적으로 메모리 지속성이 사용됩니다(Javascript 개체).
   * `service`: (개체)
      * `host`:(문자열) 서버 이름 또는 IP 주소입니다.
      * `jsonp`:(부울) true 값을 지정하면 서비스가 JSONP 서비스임을 나타내고, 그렇지 않으면 false를 나타냅니다. true면 `{callback: "ContextHub.Callbacks.*Object.name*}`개체가 `service.params`에 추가됩니다.
      * `params`:(개체) 개체 속성으로 표시되는 URL 매개 변수입니다. 매개 변수 이름 및 값은 각각 개체 속성 이름 및 값입니다.
      * `path`:(문자열) 서비스의 경로입니다.
      * `port`:(번호) 서비스의 포트 번호입니다.
      * `secure`:(문자열 또는 부울) 서비스 URL에 사용할 프로토콜을 결정합니다.
         * `auto`://
         * `true`:https://
         * `false`: 세션이://
      * `timeout`:(숫자) 시간 초과 전에 JSONP 서비스가 응답할 때까지 기다리는 시간(밀리초)입니다.
         * `ttl`:JSONP 서비스로 호출 사이에 경과되는 최소 시간(밀리초)입니다. ( [queryService](#queryservice-reload) 함수 참조).

#### queryService(다시 로드) {#queryservice-reload}

원격 JSONP 서비스를 쿼리하고 응답을 캐시합니다. 이 함수에 대한 이전 호출 이후의 시간이 `config.service.ttl` 값보다 작은 경우 서비스가 호출되지 않고, 캐시된 응답이 변경되지 않습니다. 원할 경우 서비스를 강제로 호출할 수 있습니다. `config.service.ttl`속성은 [init](#init-name-config) 함수를 호출하여 저장소를 초기화할 때 설정됩니다.

쿼리가 완료되면 준비 이벤트를 트리거합니다. JSONP 서비스 URL이 설정되지 않은 경우 함수는 아무 작업도 하지 않습니다.

##### 매개 변수 {#parameters-queryservice}

* **`reload`**  :(부울) true 값을 지정하면 캐시된 응답을 제거하고 JSONP 서비스를 호출하게 합니다.

#### 재설정 {#reset}

저장소의 지속된 데이터의 초기 값을 재설정한 다음 JSONP 서비스를 호출합니다. 선택적으로 저장소에서 다른 모든 데이터를 제거할 수 있습니다. 초기 값이 재설정되는 동안 이벤트가 이 저장소에 대해 일시 중지되었습니다. 이 함수는 값을 반환하지 않습니다.

초기 값은 저장소 개체를 인스턴스화하는 데 사용되는 구성 개체의 initialValues 속성에 제공됩니다.

##### 매개 변수 {#parameters-reset-1}

* **`keepRemainingData`**  :(부울) true 값을 지정하면 비초기 데이터가 유지됩니다. false 값을 지정하면 초기 값을 제외하고 모든 데이터가 제거됩니다.

#### resolveParameter(f) {#resolveparameter-f}

지정된 매개 변수를 확인합니다.

## ContextHub.Store.PersistedJSONPStore {#contexthub-store-persistedjsonpstore}

`ContextHub.Store.PersistedJSONPStore` 는  [ContextHub.Store.](#contexthub-store-jsonpstore) JSONPS를 확장하여 해당 클래스의 모든 함수를 상속합니다. 그러나 JSONP 서비스에서 검색한 데이터는 ContextHub 지속성 구성에 따라 유지됩니다. ([지속성 모드:](adding-contexthub.md#persistence-modes) 참조)

## ContextHub.Store.PersistentStore {#contexthub-store-persistedstore}

`ContextHub.Store.PersistedStore` 는  [ContextHub.Store를 확장합니다.](#contexthub-store-core) 따라서 해당 클래스의 모든 함수를 상속합니다. 이 저장소의 데이터는 ContextHub 지속성 구성에 따라 유지됩니다.

## ContextHub.Store.SessionStore {#contexthub-store-sessionstore}

`ContextHub.Store.SessionStore` 는  [ContextHub.Store를 확장합니다.](#contexthub-store-core) 따라서 해당 클래스의 모든 함수를 상속합니다. 이 저장소의 데이터는 메모리 내 지속성(Javascript 개체)을 사용하여 유지됩니다.

## ContextHub.UI {#contexthub-ui}

UI 모듈 및 UI 모듈 렌더러를 관리합니다.

### 함수(ContextHub.UI) {#functions-contexthub-ui}

#### registerRenderer(moduleType, renderer, dontRender) {#registerrenderer-moduletype-renderer-dontrender}

ContextHub에 UI 모듈 렌더러를 등록합니다. 렌더러가 등록되면 [UI 모듈 만들기](configuring-contexthub.md#adding-a-ui-module)에 사용할 수 있습니다. [을 확장하여 사용자 지정 UI 모듈 렌더러를 만들 때 이 함수를 사용하십시오.`ContextHub.UI.BaseModuleRenderer`](extending-contexthub.md#creating-contexthub-ui-module-types)

##### 매개 변수 {#parameters-registerrenderer}

* **`moduleType`:**  (문자열) UI 모듈 렌더러에 대한 식별자입니다. 지정한 값을 사용하여 렌더러를 이미 등록한 경우에는 이 렌더러가 등록되기 전에 기존 렌더러가 등록되지 않습니다.
* **`renderer`:**  (문자열) UI 모듈을 렌더링하는 클래스의 이름입니다.
* **`dontRender`:** (부울) 렌더러 `true` 를 등록한 후 ContextHub UI가 렌더링되지 않도록 하려면 로 설정합니다. 기본값은 `false`입니다.

##### 예 {#example-registerrenderer}

다음 예제에서는 렌더러를 `contexthub.browserinfo` 모듈 유형으로 등록합니다.

```javascript
ContextHub.UI.registerRenderer('contexthub.browserinfo', new SurferinfoRenderer());
```

## ContextHub.Utils.Cookie {#contexthub-utils-cookie}

쿠키와 상호 작용하는 유틸리티 클래스입니다.

### 함수(ContextHub.Utils.Cookie) {#functions-contexthub-utils-cookie}

#### exists(key) {#exists-key}

쿠키가 있는지 여부를 결정합니다.

##### 매개 변수 {#parameters-exists}

* **`key`** :  `String` 테스트할 쿠키의 키를 포함하는 입니다.

##### {#returns-exists} 반환

true인 `boolean` 값은 쿠키가 존재함을 나타냅니다.

##### 예 {#example-exists}

```javascript
if (ContextHub.Utils.Cookie.exists("name")) {
   // conditionally-executed code
}
```

#### getAllItems(filter) {#getallitems-filter}

필터와 일치하는 키가 있는 모든 쿠키를 반환합니다.

##### 매개 변수 {#parameters-getallitems}

* **`filter`:**  (선택 사항) 쿠키 키 일치 기준. 모든 쿠키를 반환하려면 값을 지정하지 않습니다. 지원되는 유형은 다음과 같습니다.
   * 문자열:문자열은 쿠키 키와 비교됩니다.
   * 배열:배열의 각 항목은 필터입니다.
   * RegExp 개체:개체의 테스트 함수를 사용하여 쿠키 키를 일치시킵니다.
   * 함수 호출:일치에 대한 쿠키 키를 테스트하는 함수입니다. 함수는 쿠키 키를 매개 변수로 사용하고 테스트가 일치를 확인하면 true를 반환해야 합니다.

##### {#returns-getallitems} 반환

쿠키의 개체. 개체 속성은 쿠키 키이고 키 값은 쿠키 값입니다.

##### 예 {#example-getallitems}

```javascript
ContextHub.Utils.Cookie.getAllItems([/^cq-authoring/, /^cq-editor/])
```

#### getItem(key) {#getitem-key-1}

쿠키 값을 반환합니다.

##### 매개 변수 {#parameters-getitem-1}

* **`key`** : 값을 원하는 쿠키 키입니다.

##### {#returns-getitem-1} 반환

쿠키 값 또는 키에 대한 쿠키가 없는 경우 `null` 입니다.

##### 예 {#example-getitem-1}

```javascript
ContextHub.Utils.Cookie.getItem("name");
```

#### getKeys(filter) {#getkeys-filter}

필터와 일치하는 기존 쿠키의 배열을 반환합니다.

##### 매개 변수 {#parameters-getkeys-1}

* **`filter`:** 쿠키 키 일치 기준. 지원되는 유형은 다음과 같습니다.
   * 문자열:문자열은 쿠키 키와 비교됩니다.
   * 배열:배열의 각 항목은 필터입니다.
   * RegExp 개체:개체의 테스트 함수를 사용하여 쿠키 키를 일치시킵니다.
   * 함수 호출:일치에 대한 쿠키 키를 테스트하는 함수입니다. 이 함수는 쿠키 키를 매개 변수로 사용하고, 테스트가 일치를 확인하면 `true`을 반환해야 합니다.

##### {#returns-getkeys-1} 반환

각 문자열이 필터와 일치하는 쿠키의 키인 문자열의 배열입니다.

##### 예 {#example-getkeys-1}

```javascript
ContextHub.Utils.Cookie.getKeys([/^cq-authoring/, /^cq-editor/])
```

#### removeItem(key, options) {#removeitem-key-options-1}

쿠키를 제거합니다. 쿠키를 제거하려면 값이 빈 문자열로 설정되고 만료 날짜가 현재 날짜 이전 날짜로 설정됩니다.

##### 매개 변수 {#parameters-removeitem-1}

* **`key`** :  `String` 제거할 쿠키의 키를 나타내는 값입니다.
* **`options`:** 쿠키 속성을 구성하기 위한 속성 값을 포함하는 객체입니다. 자세한 내용은 [`setItem`](#setitem-key-value-options) 함수를 참조하십시오. `expires` 속성은 영향을 주지 않습니다.

##### {#returns-removeitem-1} 반환

이 함수는 값을 반환하지 않습니다.

##### 예 {#example-removeitem-1}

```javascript
ContextHub.Utils.Cookie.vanish([/^cq-authoring/, 'cq-scrollpos']);
```

#### setItem(키, 값, 옵션) {#setitem-key-value-options-1}

주어진 키와 값의 쿠키를 만들고 현재 문서에 쿠키를 추가합니다. 선택적으로, 쿠키의 속성을 구성하는 옵션을 지정할 수 있습니다.

##### 매개 변수 {#parameters-setitem-1}

* **`key`:**  쿠키의 키를 포함하는 문자열입니다.
* **`value`:**  쿠키 값을 포함하는 문자열입니다.
* **`options`:**  (선택 사항) 쿠키 속성을 구성하는 다음 속성 중 하나를 포함하는 객체입니다.
   * `expires`:쿠키 `date` 가  `number` 만료되는 시기를 지정하는 또는 값입니다. 날짜 값은 만료 절대 시간을 지정합니다. 숫자(일 단위)는 만료 시간을 현재 시간과 숫자를 더한 값으로 설정합니다. 기본값은 `undefined`입니다.
   * `secure`:쿠키 `boolean` 의 속성 `Secure` 을 지정하는 값입니다. 기본값은 `false`입니다.
   * `path`:쿠키 `String` 의 속성 `Path` 으로 사용할 값입니다. 기본값은 `undefined`입니다.

##### {#returns-setitem-1} 반환

설정된 값이 있는 쿠키입니다.

##### 예 {#example-setitem-1}

```javascript
ContextHub.Utils.Cookie.setItem("name", "mycookie", {
    expires: 3,
    domain: 'localhost',
    path: '/some/directory',
    secure: true
});
```

#### destroy(filter, options) {#vanish-filter-options}

주어진 필터와 일치하는 모든 쿠키를 제거합니다. 쿠키는 `getKeys` 함수를 사용하여 일치하고 `removeItem` 함수를 사용하여 제거됩니다.

##### 매개 변수 {#parameters-vanish}

* **`filter`** :  `filter` 함수 호출에 사용할  [`getKeys`](#getkeys-filter) 인수입니다.
* **`options`** :  `options` 함수 호출에 사용할  [`removeItem`](#removeitem-key-options) 인수입니다.

##### {#returns-vanish} 반환

이 함수는 값을 반환하지 않습니다.

## ContextHub.Utils.Eventing {#contexthub-utils-eventing}

ContextHub 저장소 이벤트에 함수를 바인딩하고 바인딩 해제할 수 있습니다. 저장소의 [events](#eventing) 속성을 사용하여 저장소의 `ContextHub.Utils.Eventing` 개체에 액세스합니다.

### 함수(ContextHub.Utils.Eventing) {#functions-contexthub-utils-eventing}

#### off(name, selector) {#off-name-selector}

이벤트에서 함수를 바인딩하지 않습니다.

##### 매개 변수 {#parameters-off}

* **`name`** : [함수](#contexthub-utils-eventing) 를 바인딩 해제할 이벤트의 이름입니다.
* **`selector`:** 바인딩을 식별하는 선택기입니다. ( [`on`](#on-name-handler-selector-triggerforpastevents) 및 [`once`](#once-name-handler-selector-triggerforpastevents) 함수의 `selector` 매개 변수를 참조하십시오.)

##### {#returns-off} 반환

이 함수는 값을 반환하지 않습니다.

#### on(name, handler, selector, triggerForPastEvents) {#on-name-handler-selector-triggerforpastevents}

함수를 이벤트에 바인딩합니다. 함수는 이벤트가 발생할 때마다 호출됩니다. 선택적으로, 바인딩이 설정되기 전에 이전에 발생한 이벤트에 대해 함수를 호출할 수 있습니다.

##### 매개 변수 {#parameters-on}

* **`name`:**  (문자열) 함수를  [바인딩하](#contexthub-utils-eventing) 는 이벤트의 이름입니다.
* **`handler`:**  (함수) 이벤트에 바인딩할 함수입니다.
* **`selector`:**  (문자열) 바인딩의 고유 식별자입니다. `off` 함수를 사용하여 바인딩을 제거하려면 선택기가 필요합니다.
* **`triggerForPastEvents`:**  (부울) 과거에 발생한 이벤트에 대해 핸들러를 실행할지 여부를 나타냅니다. `true` 값은 과거 이벤트에 대한 처리기를 호출합니다. `false` 값은 향후 이벤트에 대한 처리기를 호출합니다. 기본값은 `true`입니다.

##### {#returns-on} 반환

`triggerForPastEvents` 인수가 `true`이면 이 함수는 이전에 이벤트가 발생했는지 여부를 나타내는 `boolean` 값을 반환합니다.

* `true`:이전에 이벤트가 발생했으므로 처리기가 호출됩니다.
* `false`:이 이벤트는 과거에 발생하지 않았습니다.

`triggerForPastEvents`이 `false`이면 이 함수는 값을 반환하지 않습니다.

##### 예 {#example-on}

다음 예제에서는 함수를 지리적 위치 저장소의 데이터 이벤트에 바인딩합니다. 함수는 페이지의 요소를 저장소의 위도 데이터 항목에 대한 값으로 채웁니다.

```html
<div class="location">
    <p>latitude: <span id="lat"></span></p>
</div>

<script>
    var geostore = ContextHub.getStore("geolocation");
    geostore.eventing.on(ContextHub.Constants.EVENT_DATA_UPDATE,getlat,"getlat");

    function getlat(){
       latitude = geostore.getItem("latitude");
       $("#lat").html(latitude);
    }
</script>
```

#### once(name, handler, selector, triggerForPastEvents) {#once-name-handler-selector-triggerforpastevents}

함수를 이벤트에 바인딩합니다. 함수는 이벤트의 첫 번째 발생 시 한 번만 호출됩니다. 선택적으로, 바인딩이 설정되기 전에 이전에 발생한 이벤트에 대해 함수를 호출할 수 있습니다.

##### 매개 변수 {#parameters-once}

* **`name`:**  (문자열) 함수를  [바인딩하](#contexthub-utils-eventing) 는 이벤트의 이름입니다.
* **`handler`:**  (함수) 이벤트에 바인딩할 함수입니다.
* **`selector`:**  (문자열) 바인딩의 고유 식별자입니다. `off` 함수를 사용하여 바인딩을 제거하려면 선택기가 필요합니다.
* **`triggerForPastEvents`:**  (부울) 과거에 발생한 이벤트에 대해 핸들러를 실행할지 여부를 나타냅니다. `true` 값은 과거 이벤트에 대한 처리기를 호출합니다. `false` 값은 향후 이벤트에 대한 처리기를 호출합니다. 기본값은 `true`입니다.

##### {#returns-once} 반환

`triggerForPastEvents` 인수가 `true`이면 이 함수는 이전에 이벤트가 발생했는지 여부를 나타내는 `boolean` 값을 반환합니다.

* `true`:이전에 이벤트가 발생했으므로 처리기가 호출됩니다.
* `false`:이 이벤트는 과거에 발생하지 않았습니다.

`triggerForPastEvents`이 `false`이면 이 함수는 값을 반환하지 않습니다.

## ContextHub.Utils.inheritance {#contexthub-utils-inheritance}

개체가 다른 개체의 속성과 메서드를 상속할 수 있도록 하는 유틸리티 클래스입니다.

### 함수(ContextHub.Utils.inheritance) {#functions-contexthub-utils-inheritance}

#### inherit(child, parent) {#inherit-child-parent}

개체가 다른 개체의 속성과 메서드를 상속하도록 합니다.

##### 매개 변수 {#parameters-inherit}

* **`child`:**  (Object) 상속하는 객체입니다.
* **`parent`:**  (개체) 상속되는 속성과 메서드를 정의하는 개체입니다.

## ContextHub.Utils.JSON {#contexthub-utils-json}

개체를 JSON 형식으로 직렬화하고 JSON 문자열을 객체로 deserialize하는 함수를 제공합니다.

### 함수(ContextHub.Utils.JSON) {#functions-contexthub-utils-json}

#### parse(data) {#parse-data}

문자열 값을 JSON으로 구문 분석하여 Javascript 개체로 변환합니다.

##### 매개 변수 {#parameters-parse}

* **`data`:** JSON 형식의 문자열 값입니다.

##### {#returns-parse} 반환

Javascript 개체.

##### 예 {#example-parse}

코드:

```javascript
ContextHub.Utils.JSON.parse("{'city':'Basel','country':'Switzerland','population':'173330'}");
```

다음 개체를 반환합니다.

```javascript
Object {
   city: "Basel",
   country: "Switzerland",
   population: 173330
}
```

#### stringify(data) {#stringify-data}

Javascript 값 및 개체를 JSON 형식의 문자열 값으로 serialize합니다.

##### 매개 변수 {#parameters-stringify}

* **`data`:** serialize할 값 또는 개체입니다. 이 함수는 부울, 배열, 숫자, 문자열 및 날짜 값을 지원합니다.

##### {#returns-stringify} 반환

직렬화된 문자열 값입니다. `data`이 R `egExp` 값이면 이 함수는 빈 개체를 반환합니다. `data` 이 함수이면 `undefined` 를 반환합니다.

##### 예 {#example-stringify}

다음 코드:

```javascript
ContextHub.Utils.JSON.stringify({
   city: "Basel",
   country: "Switzerland",
   population: 173330
});
```

반환:

```javascript
"{'city':'Basel','country':'Switzerland','population':'173330'}":
```

## ContextHub.Utils.JSON.tree {#contexthub-utils-json-tree}

이 클래스를 사용하면 ContextHub 저장소에서 저장되거나 검색할 데이터 개체를 쉽게 조작할 수 있습니다.

### 함수(ContextHub.Utils.JSON.tree) {#functions-contexthub-utils-json-tree}

#### addAllItems() {#addallitems}

데이터 개체의 복사본을 만들고 두 번째 개체의 데이터 트리에 추가합니다. 함수는 복사본을 반환하고 원본 개체 중 하나를 수정하지 않습니다. 두 개체의 데이터 트리에 동일한 키가 들어 있으면 두 번째 개체의 값이 첫 번째 개체의 값을 덮어씁니다.

##### 매개 변수 {#parameters-addallitems-1}

* **`tree`:** 복사된 객체입니다.
* **`secondTree`** :  `tree` 개체의 사본과 병합되는 개체입니다.

##### {#returns-addallitems-1} 반환

병합된 데이터가 포함된 객체입니다.

#### cleanup() {#cleanup}

개체의 복사본을 만들고, 데이터 트리에서 값, null 값 또는 정의되지 않은 값이 들어 있지 않은 항목을 찾아 제거하고 복사본을 반환합니다.

##### 매개 변수 {#parameters-cleanup}

* **`tree`:** 정리할 개체입니다.

##### {#returns-cleanup} 반환

정리된 트리 사본.

#### getItem() {#getitem}

키에 대한 개체에서 값을 검색합니다.

##### 매개 변수 {#parameters-getitem-2}

* **`tree`:** 데이터 객체입니다.
* **`key`:** 검색할 값의 키입니다.

##### {#returns-getitem-2} 반환

키와 일치하는 값입니다. 키에 자식 키가 있으면 이 함수는 복잡한 개체를 반환합니다. 키의 값 유형이 `undefined`이면 `null`이 반환됩니다.

##### 예 {#example-getitem-2}

다음 Javascript 개체를 고려하십시오.

```javascript
myObject {
  user: {
    location: {
      city: "Basel",
        details: {
          population: 173330,
          elevation: 260
        }
      }
    }
  }
```

다음 예제 코드는 값 `260`을 반환합니다.

```javascript
ContextHub.Utils.JSON.tree.getItem(myObject, "/user/location/details/elevation");
```

다음 예제 코드는 하위 키가 있는 키의 값을 검색합니다.

```javascript
ContextHub.Utils.JSON.tree.getItem(myObject, "/user");
```

함수는 다음 개체를 반환합니다.

```javascript
Object {
  location: {
    city: "Basel",
    details: {
      population: 173330,
      elevation: 260
    }
  }
}
```

#### getKeys() {#getkeys}

개체의 데이터 트리에서 모든 키를 검색합니다. 선택적으로 특정 키의 하위 키만 검색할 수 있습니다. 검색된 키의 정렬 순서를 선택적으로 지정할 수도 있습니다.

##### 매개 변수 {#parameters-getkeys-2}

* **`tree`** : 데이터 트리의 키를 검색할 객체입니다.
* **`parent`**  : (선택 사항) 데이터 트리에서 하위 항목의 키를 검색할 항목의 키입니다.
* **`order`**  : (선택 사항) 반환된 키의 정렬 순서를 결정하는 함수입니다. (Mozilla Developer Network의 [`Array.prototype.sort`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/sort) 을 참조하십시오.)

##### {#returns-getkeys-2} 반환

키 배열입니다.

##### 예 {#example-getkeys-2}

다음 개체를 고려해 보십시오.

```javascript
myObject {
  location: {
    weather: {
      temperature: "28C",
      humidity: "77%",
      precipitation: "10%",
      wind: "8km/h"
    },
    city: "Basel",
    country: "Switzerland",
    longitude: 7.5925727,
    latitude: 47.557421
  }
}
```

`ContextHub.Utils.JSON.tree.getKeys(myObject);` 스크립트는 다음 배열을 반환합니다.

```javascript
["/location", "/location/city", "/location/country", "/location/latitude", "/location/longitude", "/location/weather", "/location/weather/humidity", "/location/weather/precipitation", "/location/weather/temperature", "/location/weather/wind"]
```

#### removeItem() {#removeitem}

지정된 객체의 복사본을 만들고 데이터 트리에서 지정된 분기를 제거하고 수정된 복사본을 반환합니다.

##### 매개 변수 {#parameters-removeitem-2}

* **`tree`:** 데이터 객체입니다.
* **`key`:** 제거할 키입니다.

##### {#returns-removeitem-2} 반환

키가 제거된 원본 데이터 개체의 사본입니다.

##### 예 {#example-removeitem-2}

다음 개체를 고려해 보십시오.

```javascript
myObject {
  one: {
    foo: "bar",
    two: {
      three: {
        four: {
          five: 5,
          six: 6
        }
      }
    }
  }
}
```

다음 예제 스크립트는 데이터 트리에서 /one/2/3/4 분기를 제거합니다.

```javascript
myObject = ContextHub.Utils.JSON.tree.removeItem(myObject, "/one/two/three/four");
```

함수는 다음 개체를 반환합니다.

```javascript
myObject {
  one: {
    foo: "bar"
  }
}
```

#### hidzeKey(key) {#sanitizekey-key}

문자열 값을 정리하여 키로 사용할 수 있도록 합니다. 문자열을 정리하려면 다음 작업을 수행합니다.

* 연속된 여러 슬래시를 단일 슬래시로 줄입니다.
* 문자열의 시작 및 끝에서 공백을 제거합니다.
* 결과를 슬래시로 구분된 문자열 배열로 분할합니다.

결과 배열을 사용하여 사용 가능한 키를 만듭니다.

##### 매개 변수 {#parameters-sanitizekey}

* **`key`:** 가리기  `string` 대상.

##### {#returns-sanitizekey} 반환

각 문자열이 슬래시로 식별된 `key`의 부분인 `string` 값의 배열입니다. 정리된 키를 나타냅니다. 정리된 배열의 길이가 0인 경우 이 함수는 `null`을 반환합니다.

##### 예 {#example-sanitizekey}

다음 코드는 문자열을 정리하여 배열 `["this", "is", "a", "path"]`을 생성한 다음 배열에서 키 `"/this/is/a/path"`를 생성합니다.

```javascript
var key = " / this////is/a/path ";
ContextHub.Utils.JSON.tree.sanitizeKey(key)
"/" + ContextHub.Utils.JSON.tree.sanitizeKey(key).join("/");
```

#### setItem(tree, key, value) {#setitem-tree-key-value}

객체 사본의 데이터 트리에 키/값 쌍을 추가합니다. 데이터 트리에 대한 자세한 내용은 [지속성.](contexthub.md#persistence)

##### 매개 변수 {#parameters-setitem-2}

* **`tree`:** 데이터 객체입니다.
* **`key`** : 추가할 값과 연결할 키입니다. 키는 데이터 트리에 있는 항목의 경로입니다. 이 함수는 `ContextHub.Utils.JSON.tree.sanitize`을 호출하여 키를 추가하기 전에 삭제합니다.
* **`value`** : 데이터 트리에 추가할 값입니다.

##### {#returns-setitem-2} 반환

`key`/ `value` 쌍을 포함하는 `tree` 개체의 사본입니다.

##### 예 {#example-setitem-2}

다음 Javascript 코드를 고려하십시오.

```javascript
var myObject = {
     user: {
        location: {
           city: "Basel"
           }
        }
     };

var myKey = "/user/location/details";

var myValue = {
      population: 173330,
      elevation: 260
     };

myObject = ContextHub.Utils.JSON.tree.setItem(myObject, myKey, myValue);
```

## ContextHub.Utils.store후보자 {#contexthub-utils-storecandidates}

저장소 후보를 등록하고 등록된 저장소 후보자를 가져올 수 있습니다.

### 함수(ContextHub.Utils.store후보자) {#functions-contexthub-utils-storecandidates}

#### getRegisteredCandiers(storeType) {#getregisteredcandidates-storetype}

저장소 후보로 등록된 저장소 유형을 반환합니다. 특정 저장소 유형 또는 모든 저장소 유형의 등록된 후보자를 검색합니다.

##### 매개 변수 {#parameters-getregisteredcandidates}

* **`storeType`:**  (문자열) 저장소 유형의 이름입니다. [`ContextHub.Utils.storeCandidates.registerStoreCandidate`](#contexthub-utils-storecandidates) 함수의 `storeType` 매개 변수를 참조하십시오.

##### {#returns-getregisteredcandidates} 반환

저장소 유형의 개체입니다. 객체 등록 정보는 저장소 유형 이름이고 등록 정보 값은 등록된 저장소 후보의 배열입니다.

#### getStoreFromCandiers(storeType) {#getstorefromcandidates-storetype}

등록된 후보로부터 저장소 유형을 반환합니다. 동일한 이름의 저장소 유형이 두 개 이상 등록된 경우 함수는 우선 순위가 가장 높은 저장소 유형을 반환합니다.

##### 매개 변수 {#parameters-getstorefromcandidates}

* `storeType`:(문자열) 저장소 후보의 이름입니다. [`ContextHub.Utils.storeCandidates.registerStoreCandidate`](#registerstorecandidate-store-storetype-priority-applies) 함수의 `storeType` 매개 변수를 참조하십시오.

##### {#returns-getstorefromcandidates} 반환

등록된 저장소 후보자를 나타내는 개체입니다. 요청한 저장소 유형이 등록되지 않은 경우 오류가 발생합니다.

#### getSupportedStoreTypes() {#getsupportedstoretypes}

저장소 후보로 등록된 저장소 유형의 이름을 반환합니다. 이 함수에는 매개 변수가 필요하지 않습니다.

##### {#returns-getsupportedstoretypes} 반환

각 문자열이 저장소 후보가 등록된 저장소 유형인 문자열 값의 배열입니다. [`ContextHub.Utils.storeCandidates.registerStoreCandidate`](#contexthub-utils-storecandidates) 함수의 `storeType` 매개 변수를 참조하십시오.

#### registerStoreCandidate(store, storeType, priority, apply) {#registerstorecandidate-store-storetype-priority-applies}

이름과 우선 순위를 사용하여 저장소 개체를 저장소 후보로 등록합니다.

우선 순위는 같은 이름의 점포의 중요성을 나타내는 숫자입니다. 이미 등록된 상점 후보자와 같은 이름을 사용하여 상인등록을 하면 우선순위가 높은 후보가 사용된다. 상인등록을 할 때 상인은 같은 이름 등록된 상인보다 우선순위가 높은 경우에만 등록된다.

##### 매개 변수 {#parameters-registerstorecandidate}

* **`store`:**  (개체) 저장소 후보로 등록할 저장소 개체입니다.
* **`storeType`:**  (문자열) 저장소 후보의 이름입니다. 이 값은 저장소 후보의 인스턴스를 만들 때 필요합니다.
* **`priority`:**  (숫자) 저장소 후보의 우선 순위입니다.
* **`applies`:**  (함수) 현재 환경에서 저장소의 적용을 평가하는 를 호출하는 함수입니다. 저장소가 적용 가능한 경우 함수는 `true` 를 반환하고, 그렇지 않으면 `false` 를 반환해야 합니다. 기본값은 true를 반환하는 함수입니다.`function() {return true;}`

##### 예 {#example-registerstorecandidate}

```javascript
ContextHub.Utils.storeCandidates.registerStoreCandidate(myStoreCandidate,
                                'contexthub.mystorecandiate', 0);
```
