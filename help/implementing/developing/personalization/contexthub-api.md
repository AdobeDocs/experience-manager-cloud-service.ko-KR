---
title: ContextHub Javascript API 참조
description: ContextHub 구성 요소를 페이지에 추가한 경우 스크립트에 ContextHub Javascript API를 사용할 수 있습니다
exl-id: ec35bef5-610c-4e85-a43a-d4201b5eb03e
source-git-commit: 90de3cf9bf1c949667f4de109d0b517c6be22184
workflow-type: tm+mt
source-wordcount: '4621'
ht-degree: 2%

---

# ContextHub Javascript API 참조 {#contexthub-javascript-api-reference}

ContextHub Javascript API는 [ContextHub 구성 요소가 페이지에 추가되었습니다](adding-contexthub.md).

## ContextHub 상수 {#contexthub-constants}

ContextHub Javascript API가 정의하는 상수 값입니다.

### 이벤트 상수 {#event-constants}

다음 표에는 ContextHub 저장소에 대해 발생하는 이벤트 이름이 나와 있습니다. 참조 - [ContextHub.Utils.Eventing](#contexthub-utils-eventing).

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

##### 반환 {#returns-}

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

* **`name`:** 스토어가 등록된 이름입니다.

##### 반환 {#returns-getstore-name}

저장소를 나타내는 개체입니다.

##### 예 {#example-getstore-name}

다음 예제에서는 지리적 위치 저장소를 검색합니다.

```javascript
var geoloc = ContextHub.getStore("geolocation");
```

## ContextHub.SegmentEngine.Segment {#contexthub-segmentengine-segment}

ContextHub 세그먼트를 나타냅니다. 를 사용하십시오 `ContextHub.SegmentEngine.SegmentManager` 세그먼트 가져오기.

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

##### 반환 {#returns-getresolvedsegments}

일련의 `ContextHub.SegmentEngine.Segment` 개체.

## ContextHub.Store.Core {#contexthub-store-core}

ContextHub 저장소의 기본 클래스입니다.

### 속성(ContextHub.Store.Core) {#properties-contexthub-store-core}

#### 이벤트 {#eventing}

A [`ContextHub.Utils.Eventing`](#contexthub-utils-eventing) 개체. 이벤트를 저장할 함수를 바인딩하는 데 이 개체를 사용합니다. 기본값 및 초기화에 대한 자세한 내용은 [`init(name,config)`](#init-name-config).

#### 이름 {#name}

저장소의 이름입니다.

#### 지속성 {#persistence}

A `ContextHub.Utils.Persistence` 개체. 기본값 및 초기화에 대한 자세한 내용은 [`init(name,config)`](#init-name-config).

### 함수(ContextHub.Store.Core) {#functions-contexthub-store-core}

#### addAllItems(tree, options) {#addallitems-tree-options}

데이터 개체 또는 배열을 저장소 데이터와 병합합니다. 개체나 배열에 있는 각 키/값 쌍이 저장소에 추가됩니다( `setItem` ):

* **개체:** 키는 속성 이름입니다.
* **배열:** 키는 배열 지표입니다.

값은 객체가 될 수 있습니다.

##### 매개 변수 {#parameters-addallitems}

* **`tree`:** (개체 또는 배열) 저장소에 추가할 데이터입니다.
* **`options`:** (개체) setItem 함수에 전달되는 옵션 개체 자세한 내용은 `options` 매개 변수 [`setItem(key,value,options)`](#setitem-key-value-options).

##### 반환 {#returns-addallitems}

A `boolean` 값:

* 값 `true` 데이터 개체가 저장되었음을 나타냅니다.
* 값 `false` 데이터 저장소가 변경되지 않음을 나타냅니다.

#### addReference(key, anotherKey) {#addreference-key-anotherkey}

한 키에서 다른 키로 참조를 만듭니다. 키는 자신을 참조할 수 없습니다.

##### 매개 변수 {#parameters-addreference}

* **`key`:** 참조하는 키 `anotherKey`.

* **`anotherkey`:** 이 키는 `key`.

##### 반환 {#returns-addreference}

A `boolean` 값:

* 값 `true` 참조가 추가되었음을 나타냅니다.
* 값 `false` 참조가 추가되지 않았음을 나타냅니다.

#### announceReadiness() {#announcereadiness}

트리거 `ready` 이 저장소에 대한 이벤트입니다. 이 함수에는 매개 변수가 없으며 값을 반환하지 않습니다.

#### clean() {#clean}

저장소에서 모든 데이터를 제거합니다. 함수에는 매개 변수 및 반환 값이 없습니다.

#### getItem(key) {#getitem-key}

키와 연결된 값을 반환합니다.

##### 매개 변수 {#parameters-getitem}

* **`key`:** (문자열) 값을 반환할 키입니다.

##### 반환 {#returns-getitem}

키의 값을 나타내는 개체입니다.

#### getKeys(includeInternals) {#getkeys-includeinternals}

저장소에서 키를 검색합니다. 선택적으로 ContextHub 프레임워크에서 내부적으로 사용되는 키를 검색할 수 있습니다.

##### 매개 변수 {#parameters-getkeys}

* **`includeInternals`:** 값 `true` 결과에 내부적으로 사용되는 키를 포함합니다. 이러한 키는 밑줄로 시작합니다(`_`) 문자를 사용할 수 없습니다. 기본값은 `false`입니다.

##### 반환 {#returns-getkeys}

키 이름의 배열( `string` 값).

#### getReferences() {#getreferences}

저장소에서 참조를 검색합니다.

##### 반환 {#returns-getreferences}

참조하는 키를 참조된 키의 인덱스로 사용하는 배열입니다.

* 참조하는 키는 `key` 의 매개 변수 `addReference` 함수 위에 있어야 합니다.
* 참조된 키는 `anotherKey` 의 매개 변수 `addReference` 함수 위에 있어야 합니다.

#### getTree(includeInternals) {#gettree-includeinternals}

저장소에서 데이터 트리를 검색합니다. 선택적으로 ContextHub 프레임워크에서 내부적으로 사용하는 키/값 쌍을 포함할 수 있습니다.

##### 매개 변수 {#parameters-gettree}

* `includeInternals:` 값 `true` 결과에 내부적으로 사용된 키/값 쌍을 포함합니다. 이 데이터의 키는 밑줄(`_`) 문자를 사용할 수 없습니다. 기본값은 `false`입니다.

##### 반환 {#returns-gettree}

데이터 트리를 나타내는 개체입니다. 키는 개체의 속성 이름입니다.

#### init(name, config) {#init-name-config}

저장소를 초기화합니다.

* 저장소 데이터를 빈 개체로 설정합니다.
* 저장소 참조를 빈 개체로 설정합니다.
* 다음 `eventChannel` is `data:<name>`, 위치 `<name>` 은 저장소 이름입니다.
* 다음 `storeDataKey` is `/store/<name>`, 위치 `<name>` 은 저장소 이름입니다.

##### 매개 변수 {#parameters-init}

* **`name`:** 저장소의 이름입니다.
* **`config`:** 구성 속성을 포함하는 객체입니다.
   * `eventDeferring`: 기본값은 32입니다.
   * `eventing`: 다음 [ContextHub.Utils.Eventing](#contexthub-utils-eventing) 이 저장소에 대한 개체입니다. 기본값은 입니다. `ContextHub.eventing` 개체를 사용합니다.
   * `persistence`: 다음 `ContextHub.Utils.Persistence` 이 저장소에 대한 개체입니다. 기본값은 입니다. `ContextHub.persistence` 개체.

#### isEventingPaused() {#iseventingpaused}

이 저장소에 대해 이벤트가 일시 중지되었는지 여부를 결정합니다.

##### 반환 {#returns-iseventingpaused}

부울 값:

* `true`: 이 저장소에 대해 이벤트가 트리거되지 않도록 이벤트가 일시 중지되었습니다.
* `false`: 이벤트가 일시 중지되지 않아 이 저장소에 대해 이벤트가 트리거됩니다.

#### pauseEventing() {#pauseeventing}

이벤트가 트리거되지 않도록 저장소에 대한 이벤트를 일시 중지합니다. 이 함수에는 매개 변수가 필요하지 않으며 값을 반환하지 않습니다.

#### removeItem(키, 옵션) {#removeitem-key-options}

저장소에서 키/값 쌍을 제거합니다.

키가 제거되면 함수는 `data` 이벤트. 이벤트 데이터에는 저장소 이름, 제거된 키의 이름, 제거된 값, 키에 대한 새 값(null) 및 &quot;제거&quot;의 작업 유형이 포함됩니다.

선택적으로, `data` 이벤트.

##### 매개 변수 {#parameters-removeitem}

* **`key`:** (문자열) 제거할 키의 이름입니다.
* **`options`:** (객체) 옵션 객체입니다. 다음 개체 속성이 유효합니다.
   * 자동: 값 `true` 는 `data` 이벤트. 기본값은 `false`입니다.

##### 반환 {#returns-removeitem}

A `boolean` 값:

* 값 `true` 키/값 쌍이 제거되었음을 나타냅니다.
* 값 `false` 키가 저장소에서 없으므로 데이터 저장소가 변경되지 않음을 나타냅니다.

#### removeReference(key) {#removereference-key}

저장소에서 참조를 제거합니다.

##### 매개 변수 {#parameters-removereference}

* **`key`:** 제거할 키 참조입니다. 이 매개 변수는 `key` 의 매개 변수 `addReference` 함수 위에 있어야 합니다.

##### 반환 {#returns-removereference}

A `boolean` 값:

* 값 `true` 참조가 제거되었음을 나타냅니다.
* 값 `false` 키가 유효하지 않으며 저장소가 변경되지 않음을 나타냅니다.

#### reset(keepRemainingData) {#reset-keepremainingdata}

저장소의 지속된 데이터의 초기 값을 재설정합니다. 선택적으로 저장소에서 다른 모든 데이터를 제거할 수 있습니다. 저장소가 다시 설정되는 동안 이벤트가 이 저장소에 대해 일시 중지되었습니다. 이 함수는 값을 반환하지 않습니다.

초기값은 `initialValues` 저장소 개체를 인스턴스화하는 데 사용되는 구성 개체의 속성입니다.

##### 매개 변수 {#parameters-reset}

* **`keepRemainingData`**: (부울) true 값을 지정하면 비초기 데이터가 유지됩니다. false 값을 지정하면 초기 값을 제외하고 모든 데이터가 제거됩니다.

#### resolveReference(키, 다시 시도) {#resolvereference-key-retry}

참조된 키를 검색합니다. 최적 일치 해결을 위해 사용할 반복 횟수를 지정할 수 있습니다(선택적).

##### 매개 변수 {#parameters-resolvereference}

* **`key`:** (문자열) 참조를 확인할 키입니다. 이 `key` 매개 변수는 `key` 의 매개 변수 `addReference` 함수 위에 있어야 합니다.
* **`retry`:** (숫자) 사용할 반복 횟수입니다.

##### 반환 {#returns-resolvereference}

A `string` 참조된 키를 나타내는 값입니다. 참조가 해결되지 않으면, `key` 매개 변수가 반환됩니다.

#### resumeEventing() {#resumeeventing}

이벤트가 트리거되도록 이 저장소에 대한 이벤트를 다시 시작합니다. 이 함수는 매개 변수를 정의하지 않으며 값을 반환하지 않습니다.

#### setItem(키, 값, 옵션) {#setitem-key-value-options}

키/값 쌍을 저장소에 추가합니다.

트리거 `data` 이벤트에 대한 값은 키에 현재 저장된 값과 다른 경우에만 발생합니다. 선택적으로 `data` 이벤트.

이벤트 데이터에는 저장소 이름, 키, 이전 값, 새 값 및 작업 유형이 포함됩니다 `set`.

##### 매개 변수 {#parameters-setitem}

* **`key`:** (문자열) 키의 이름입니다.
* **`options`:** (객체) 옵션 객체입니다. 다음 개체 속성이 유효합니다.
   * `silent`: 값 `true` 는 `data` 이벤트. 기본값은 `false`입니다.
* **`value`:** (개체) 키와 연결할 값입니다.

##### 반환 {#returns-setitem}

A `boolean` 값:

* 값 `true` 데이터 개체가 저장되었음을 나타냅니다.
* 값 `false` 데이터 저장소가 변경되지 않음을 나타냅니다.

## ContextHub.Store.JSONPStore {#contexthub-store-jsonpstore}

JSON 데이터를 포함하는 스토어. 데이터는 외부 JSONP 서비스에서 검색되거나, 선택적으로 JSON 데이터를 반환하는 서비스에서 검색됩니다. 를 사용하여 서비스 세부 사항을 지정합니다. [`init`](#init-name-config) 이 클래스의 인스턴스를 만들 때 사용됩니다.

저장소는 메모리 내 지속성을 사용합니다(Javascript 변수). 데이터 저장 은 페이지 수명 동안에만 사용할 수 있습니다.

ContextHub.Store.JSONPStore가 확장됩니다 [ContextHub.Store.Core](#contexthub-store-core) 및 은 해당 클래스의 함수를 상속합니다.

### 함수(ContextHub.Store.JSONPStore) {#functions-contexthub-store-jsonpstore}

#### configureService(serviceConfig, override) {#configureservice-serviceconfig-override}

이 개체가 사용하는 JSONP 서비스에 연결하는 세부 정보를 구성합니다. 기존 구성을 업데이트하거나 바꿀 수 있습니다. 함수는 값을 반환하지 않습니다.

##### 매개 변수 {#parameters-configureservice}

* **`serviceConfig`:** 다음 속성을 포함하는 객체입니다.
   * `host`: (문자열) 서버 이름 또는 IP 주소입니다.
   * `jsonp`: (부울) true 값을 지정하면 서비스가 JSONP 서비스임을 나타내고, 그렇지 않으면 false를 나타냅니다. true인 경우 {callback: &quot;ContextHub.Callback.*Object.name*} 개체가 service.params 개체에 추가됩니다.
   * `params`: (개체) 개체 속성으로 표시되는 URL 매개 변수입니다. 매개 변수 이름은 속성 이름이고 매개 변수 값은 속성 값입니다.
   * `path`: (문자열) 서비스의 경로입니다.
   * `port`: (번호) 서비스의 포트 번호입니다.
   * `secure`: (문자열 또는 부울) 서비스 URL에 사용할 프로토콜을 결정합니다.
      * `auto`: //
      * `true`: https://
      * `false`: 세션이://
* **재정의:** (부울). 값 `true` 기존 서비스 구성이 `serviceConfig`. 값 `false` 기존 서비스 구성 속성이 `serviceConfig`.

#### getRawResponse() {#getrawresponse}

JSONP 서비스에 대한 마지막 호출 이후 캐시된 원시 응답을 반환합니다. 함수에는 매개 변수가 필요하지 않습니다.

##### 반환 {#returns-getrawresponse}

원시 응답을 나타내는 객체입니다.

#### getServiceDetails() {#getservicedetails}

이 ContextHub.Store.JSONPStore 개체의 서비스 개체를 검색합니다. 서비스 개체에는 서비스 URL을 만드는 데 필요한 모든 정보가 들어 있습니다.

##### 반환 {#returns-getservicedetails}

다음 속성을 갖는 객체:

* **`host`:** (문자열) 서버 이름 또는 IP 주소입니다.
* **`jsonp`:** (부울) true 값을 지정하면 서비스가 JSONP 서비스임을 나타내고, 그렇지 않으면 false를 나타냅니다. true인 경우 {callback: &quot;ContextHub.Callback.*Object.name*} 개체가 service.params 개체에 추가됩니다.
* **`params`:** (개체) 개체 속성으로 표시되는 URL 매개 변수입니다. 매개 변수 이름은 속성 이름이고 매개 변수 값은 속성 값입니다.
* **`path`:** (문자열) 서비스의 경로입니다.
* **`port`:** (번호) 서비스의 포트 번호입니다.
* **`secure`:** (문자열 또는 부울) 서비스 URL에 사용할 프로토콜을 결정합니다.
   * `auto`: //
   * `true`: https://
   * `false`: 세션이://

#### getServiceURL(resolve) {#getserviceurl-resolve}

JSONP 서비스의 URL을 검색합니다.

##### 매개 변수 {#parameters-getserviceurl}

* **`resolve`:** (부울) URL에 확인된 매개 변수를 포함할지 여부를 결정합니다. 값 `true` 매개 변수 확인 및 `false` 그렇지 않습니다.

##### 반환 {#returns-getserviceurl}

A `string` 서비스 URL을 나타내는 값입니다.

#### init(name, config) {#init-name-config-1}

초기화 `ContextHub.Store.JSONPStore` 개체.

##### 매개 변수 {#parameters-init-1}

* **`name`:** (문자열) 저장소의 이름입니다.
* **`config`:** (객체) 서비스 속성을 포함하는 객체입니다. JSONPStore 개체는 `service` jsonp 서비스의 URL을 구성하는 개체:
   * `eventDeferring`: 32.
   * `eventing`: 이 저장소에 대한 ContextHub.Utils.Eventing 개체입니다. 기본값은 입니다. `ContextHub.eventing` 개체.
   * `persistence`: 이 저장소에 대한 ContextHub.Utils.Persistence 개체입니다. 기본적으로 메모리 지속성이 사용됩니다(Javascript 개체).
   * `service`: (개체)
      * `host`: (문자열) 서버 이름 또는 IP 주소입니다.
      * `jsonp`: (부울) true 값을 지정하면 서비스가 JSONP 서비스임을 나타내고, 그렇지 않으면 false를 나타냅니다. true면 `{callback: "ContextHub.Callbacks.*Object.name*}`개체가에 추가됩니다. `service.params`.
      * `params`: (개체) 개체 속성으로 표시되는 URL 매개 변수입니다. 매개 변수 이름 및 값은 각각 개체 속성 이름 및 값입니다.
      * `path`: (문자열) 서비스의 경로입니다.
      * `port`: (번호) 서비스의 포트 번호입니다.
      * `secure`: (문자열 또는 부울) 서비스 URL에 사용할 프로토콜을 결정합니다.
         * `auto`: //
         * `true`: https://
         * `false`: 세션이://
      * `timeout`: (숫자) 시간 초과 전에 JSONP 서비스가 응답할 때까지 기다리는 시간(밀리초)입니다.
         * `ttl`: JSONP 서비스로 호출 사이에 경과되는 최소 시간(밀리초)입니다. (자세한 내용은 [queryService](#queryservice-reload) 함수 위에 있어야 합니다.

#### queryService(다시 로드) {#queryservice-reload}

원격 JSONP 서비스를 쿼리하고 응답을 캐시합니다. 이 함수에 대한 이전 호출 이후의 시간이 `config.service.ttl`인 경우 서비스가 호출되지 않고, 캐시된 응답이 변경되지 않습니다. 원할 경우 서비스를 강제로 호출할 수 있습니다. 다음 `config.service.ttl`속성은 [init](#init-name-config) 함수를 사용하여 저장소를 초기화합니다.

쿼리가 완료되면 준비 이벤트를 트리거합니다. JSONP 서비스 URL이 설정되지 않은 경우 함수는 아무 작업도 하지 않습니다.

##### 매개 변수 {#parameters-queryservice}

* **`reload`:** (부울) true 값을 지정하면 캐시된 응답을 제거하고 JSONP 서비스를 호출하게 합니다.

#### 재설정 {#reset}

저장소의 지속된 데이터의 초기 값을 재설정한 다음 JSONP 서비스를 호출합니다. 선택적으로 저장소에서 다른 모든 데이터를 제거할 수 있습니다. 초기 값이 재설정되는 동안 이벤트가 이 저장소에 대해 일시 중지되었습니다. 이 함수는 값을 반환하지 않습니다.

초기 값은 저장소 개체를 인스턴스화하는 데 사용되는 구성 개체의 initialValues 속성에 제공됩니다.

##### 매개 변수 {#parameters-reset-1}

* **`keepRemainingData`:** (부울) true 값을 지정하면 비초기 데이터가 유지됩니다. false 값을 지정하면 초기 값을 제외하고 모든 데이터가 제거됩니다.

#### resolveParameter(f) {#resolveparameter-f}

지정된 매개 변수를 확인합니다.

## ContextHub.Store.PersistedJSONPStore {#contexthub-store-persistedjsonpstore}

`ContextHub.Store.PersistedJSONPStore` 확장 [ContextHub.Store.JSONPStore](#contexthub-store-jsonpstore) 따라서 해당 클래스의 모든 함수를 상속합니다. 그러나 JSONP 서비스에서 검색한 데이터는 ContextHub 지속성 구성에 따라 유지됩니다. (자세한 내용은 [지속성 모드:](adding-contexthub.md#persistence-modes))

## ContextHub.Store.PersistedStore {#contexthub-store-persistedstore}

`ContextHub.Store.PersistedStore` 확장 [ContextHub.Store.Core](#contexthub-store-core) 따라서 해당 클래스의 모든 함수를 상속합니다. 이 저장소의 데이터는 ContextHub 지속성 구성에 따라 유지됩니다.

## ContextHub.Store.SessionStore {#contexthub-store-sessionstore}

`ContextHub.Store.SessionStore` 확장 [ContextHub.Store.Core](#contexthub-store-core) 따라서 해당 클래스의 모든 함수를 상속합니다. 이 저장소의 데이터는 메모리 내 지속성(Javascript 개체)을 사용하여 유지됩니다.

## ContextHub.UI {#contexthub-ui}

UI 모듈 및 UI 모듈 렌더러를 관리합니다.

### 함수(ContextHub.UI) {#functions-contexthub-ui}

#### registerRenderer(moduleType, renderer, dontRender) {#registerrenderer-moduletype-renderer-dontrender}

ContextHub에 UI 모듈 렌더러를 등록합니다. 렌더러를 등록하면 다음 작업을 수행할 수 있습니다 [UI 모듈 만들기](configuring-contexthub.md#adding-a-ui-module). 가능하면 이 함수를 사용하십시오 [확장 `ContextHub.UI.BaseModuleRenderer`](extending-contexthub.md#creating-contexthub-ui-module-types) 사용자 지정 UI 모듈 렌더러를 만들려면

##### 매개 변수 {#parameters-registerrenderer}

* **`moduleType`:** (문자열) UI 모듈 렌더러에 대한 식별자입니다. 지정한 값을 사용하여 렌더러를 이미 등록한 경우에는 이 렌더러가 등록되기 전에 기존 렌더러가 등록되지 않습니다.
* **`renderer`:** (문자열) UI 모듈을 렌더링하는 클래스의 이름입니다.
* **`dontRender`:** (부울) 를 로 설정합니다. `true` 렌더러를 등록한 후 ContextHub UI가 렌더링되지 않도록 하려면 다음을 수행하십시오. 기본값은 `false`입니다.

##### 예 {#example-registerrenderer}

다음 예제에서는 렌더러를 `contexthub.browserinfo` 모듈 유형.

```javascript
ContextHub.UI.registerRenderer('contexthub.browserinfo', new SurferinfoRenderer());
```

## ContextHub.Utils.Cookie {#contexthub-utils-cookie}

쿠키와 상호 작용하는 유틸리티 클래스입니다.

### 함수(ContextHub.Utils.Cookie) {#functions-contexthub-utils-cookie}

#### exists(key) {#exists-key}

쿠키가 있는지 여부를 결정합니다.

##### 매개 변수 {#parameters-exists}

* **`key`:** A `String` 에는 테스트 중인 쿠키의 키가 포함되어 있습니다.

##### 반환 {#returns-exists}

A `boolean` true 값은 쿠키가 존재함을 나타냅니다.

##### 예 {#example-exists}

```javascript
if (ContextHub.Utils.Cookie.exists("name")) {
   // conditionally-executed code
}
```

#### getAllItems(필터) {#getallitems-filter}

필터와 일치하는 키가 있는 모든 쿠키를 반환합니다.

##### 매개 변수 {#parameters-getallitems}

* **`filter`:** (선택 사항) 쿠키 키 일치 기준. 모든 쿠키를 반환하려면 값을 지정하지 않습니다. 지원되는 유형은 다음과 같습니다.
   * 문자열: 문자열은 쿠키 키와 비교됩니다.
   * 배열: 배열의 각 항목은 필터입니다.
   * RegExp 개체: 개체의 테스트 함수를 사용하여 쿠키 키를 일치시킵니다.
   * 함수 호출: 일치에 대한 쿠키 키를 테스트하는 함수입니다. 함수는 쿠키 키를 매개 변수로 사용하고 테스트가 일치를 확인하면 true를 반환해야 합니다.

##### 반환 {#returns-getallitems}

쿠키의 개체. 개체 속성은 쿠키 키이고 키 값은 쿠키 값입니다.

##### 예 {#example-getallitems}

```javascript
ContextHub.Utils.Cookie.getAllItems([/^cq-authoring/, /^cq-editor/])
```

#### getItem(key) {#getitem-key-1}

쿠키 값을 반환합니다.

##### 매개 변수 {#parameters-getitem-1}

* **`key`:** 값에 사용할 쿠키의 키입니다.

##### 반환 {#returns-getitem-1}

쿠키 값 또는 `null` 키에 대한 쿠키가 없는 경우.

##### 예 {#example-getitem-1}

```javascript
ContextHub.Utils.Cookie.getItem("name");
```

#### getKeys(filter) {#getkeys-filter}

필터와 일치하는 기존 쿠키의 배열을 반환합니다.

##### 매개 변수 {#parameters-getkeys-1}

* **`filter`:** 쿠키 키 일치 기준. 지원되는 유형은 다음과 같습니다.
   * 문자열: 문자열은 쿠키 키와 비교됩니다.
   * 배열: 배열의 각 항목은 필터입니다.
   * RegExp 개체: 개체의 테스트 함수를 사용하여 쿠키 키를 일치시킵니다.
   * 함수 호출: 일치에 대한 쿠키 키를 테스트하는 함수입니다. 함수는 쿠키 키를 매개 변수로 사용하고 를 반환해야 합니다 `true` 테스트가 일치를 확인하는 경우

##### 반환 {#returns-getkeys-1}

각 문자열이 필터와 일치하는 쿠키의 키인 문자열의 배열입니다.

##### 예 {#example-getkeys-1}

```javascript
ContextHub.Utils.Cookie.getKeys([/^cq-authoring/, /^cq-editor/])
```

#### removeItem(키, 옵션) {#removeitem-key-options-1}

쿠키를 제거합니다. 쿠키를 제거하려면 값이 빈 문자열로 설정되고 만료 날짜가 현재 날짜 이전 날짜로 설정됩니다.

##### 매개 변수 {#parameters-removeitem-1}

* **`key`:** A `String` 제거할 쿠키의 키를 나타내는 값입니다.
* **`options`:** 쿠키 속성을 구성하기 위한 속성 값을 포함하는 객체입니다. 자세한 내용은 [`setItem`](#setitem-key-value-options) 함수 내에 있어야 합니다. 다음 `expires` 속성은 영향을 주지 않습니다.

##### 반환 {#returns-removeitem-1}

이 함수는 값을 반환하지 않습니다.

##### 예 {#example-removeitem-1}

```javascript
ContextHub.Utils.Cookie.vanish([/^cq-authoring/, 'cq-scrollpos']);
```

#### setItem(키, 값, 옵션) {#setitem-key-value-options-1}

주어진 키와 값의 쿠키를 만들고 현재 문서에 쿠키를 추가합니다. 선택적으로, 쿠키의 속성을 구성하는 옵션을 지정할 수 있습니다.

##### 매개 변수 {#parameters-setitem-1}

* **`key`:** 쿠키의 키를 포함하는 문자열입니다.
* **`value`:** 쿠키 값을 포함하는 문자열입니다.
* **`options`:** (선택 사항) 쿠키 속성을 구성하는 다음 속성 중 하나를 포함하는 객체입니다.
   * `expires`: A `date` 또는 `number` 쿠키가 만료되는 시기를 지정하는 값입니다. 날짜 값은 만료 절대 시간을 지정합니다. 숫자(일 단위)는 만료 시간을 현재 시간과 숫자를 더한 값으로 설정합니다. 기본값은 `undefined`입니다.
   * `secure`: A `boolean` 를 지정하는 값 `Secure` 쿠키의 속성입니다. 기본값은 `false`입니다.
   * `path`: A `String` 값으로 사용할 값 `Path` 쿠키의 속성입니다. 기본값은 `undefined`입니다.

##### 반환 {#returns-setitem-1}

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

주어진 필터와 일치하는 모든 쿠키를 제거합니다. 쿠키는 를 사용하여 일치합니다 `getKeys` 함수 및 `removeItem` 함수 위에 있어야 합니다.

##### 매개 변수 {#parameters-vanish}

* **`filter`:** 다음 `filter` 호출에 사용할 인수 [`getKeys`](#getkeys-filter) 함수 위에 있어야 합니다.
* **`options`:** 다음 `options` 호출에 사용할 인수 [`removeItem`](#removeitem-key-options) 함수 위에 있어야 합니다.

##### 반환 {#returns-vanish}

이 함수는 값을 반환하지 않습니다.

## ContextHub.Utils.Eventing {#contexthub-utils-eventing}

ContextHub 저장소 이벤트에 함수를 바인딩하고 바인딩 해제할 수 있습니다. 액세스 `ContextHub.Utils.Eventing` 를 사용하여 저장할 객체 [이벤트](#eventing) 저장소의 속성입니다.

### 함수(ContextHub.Utils.Eventing) {#functions-contexthub-utils-eventing}

#### off(name, selector) {#off-name-selector}

이벤트에서 함수를 바인딩하지 않습니다.

##### 매개 변수 {#parameters-off}

* **`name`:** 다음 [이벤트 이름](#contexthub-utils-eventing) 함수에 대한 바인딩을 해제합니다.
* **`selector`:** 바인딩을 식별하는 선택기입니다. (자세한 내용은 `selector` 매개 변수 [`on`](#on-name-handler-selector-triggerforpastevents) 및 [`once`](#once-name-handler-selector-triggerforpastevents) 함수 위에 있어야 합니다.

##### 반환 {#returns-off}

이 함수는 값을 반환하지 않습니다.

#### on(name, handler, selector, triggerForPastEvents) {#on-name-handler-selector-triggerforpastevents}

함수를 이벤트에 바인딩합니다. 함수는 이벤트가 발생할 때마다 호출됩니다. 선택적으로, 바인딩이 설정되기 전에 이전에 발생한 이벤트에 대해 함수를 호출할 수 있습니다.

##### 매개 변수 {#parameters-on}

* **`name`:** (문자열) [이벤트 이름](#contexthub-utils-eventing) 함수에 바인딩하는 위치입니다.
* **`handler`:** (함수) 이벤트에 바인딩할 함수입니다.
* **`selector`:** (문자열) 바인딩의 고유 식별자입니다. 를 사용하려는 경우 선택기를 사용하여 바인딩을 확인해야 합니다 `off` 바인딩을 제거하는 함수입니다.
* **`triggerForPastEvents`:** (부울) 과거에 발생한 이벤트에 대해 핸들러를 실행할지 여부를 나타냅니다. 값 `true` 는 과거 이벤트에 대한 처리기를 호출합니다. 값 `false` 은 향후 이벤트에 대한 처리기를 호출합니다. 기본값은 `true`입니다.

##### 반환 {#returns-on}

이 `triggerForPastEvents` 인수가 `true`로 지정하는 경우 이 함수는 `boolean` 과거 이벤트가 발생했는지 여부를 나타내는 값입니다.

* `true`: 이전에 이벤트가 발생했으므로 처리기가 호출됩니다.
* `false`: 이 이벤트는 과거에 발생하지 않았습니다.

If `triggerForPastEvents` is `false`로 설정되면 이 함수는 값을 반환하지 않습니다.

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

* **`name`:** (문자열) [이벤트 이름](#contexthub-utils-eventing) 함수에 바인딩하는 위치입니다.
* **`handler`:** (함수) 이벤트에 바인딩할 함수입니다.
* **`selector`:** (문자열) 바인딩의 고유 식별자입니다. 를 사용하려는 경우 선택기를 사용하여 바인딩을 확인해야 합니다 `off` 바인딩을 제거하는 함수입니다.
* **`triggerForPastEvents`:** (부울) 과거에 발생한 이벤트에 대해 핸들러를 실행할지 여부를 나타냅니다. 값 `true` 는 과거 이벤트에 대한 처리기를 호출합니다. 값 `false` 은 향후 이벤트에 대한 처리기를 호출합니다. 기본값은 `true`입니다.

##### 반환 {#returns-once}

이 `triggerForPastEvents` 인수가 `true`로 지정하는 경우 이 함수는 `boolean` 과거 이벤트가 발생했는지 여부를 나타내는 값입니다.

* `true`: 이전에 이벤트가 발생했으므로 처리기가 호출됩니다.
* `false`: 이 이벤트는 과거에 발생하지 않았습니다.

If `triggerForPastEvents` is `false`로 설정되면 이 함수는 값을 반환하지 않습니다.

## ContextHub.Utils.inheritance {#contexthub-utils-inheritance}

개체가 다른 개체의 속성과 메서드를 상속할 수 있도록 하는 유틸리티 클래스입니다.

### 함수(ContextHub.Utils.inheritance) {#functions-contexthub-utils-inheritance}

#### inherit(child, parent) {#inherit-child-parent}

개체가 다른 개체의 속성과 메서드를 상속하도록 합니다.

##### 매개 변수 {#parameters-inherit}

* **`child`:** (객체) 상속되는 객체입니다.
* **`parent`:** (객체) 상속되는 속성과 메서드를 정의하는 객체입니다.

## ContextHub.Utils.JSON {#contexthub-utils-json}

개체를 JSON 형식으로 직렬화하고 JSON 문자열을 객체로 deserialize하는 함수를 제공합니다.

### 함수(ContextHub.Utils.JSON) {#functions-contexthub-utils-json}

#### parse(data) {#parse-data}

문자열 값을 JSON으로 구문 분석하여 Javascript 개체로 변환합니다.

##### 매개 변수 {#parameters-parse}

* **`data`:** JSON 형식의 문자열 값입니다.

##### 반환 {#returns-parse}

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

##### 반환 {#returns-stringify}

직렬화된 문자열 값입니다. When `data` 은 R입니다 `egExp` 값을 지정하면 이 함수는 빈 개체를 반환합니다. When `data` 는 함수입니다. `undefined`.

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
* **`secondTree`:** 개체의 복사본과 병합되는 개체 `tree` 개체.

##### 반환 {#returns-addallitems-1}

병합된 데이터가 포함된 객체입니다.

#### cleanup() {#cleanup}

개체의 복사본을 만들고, 데이터 트리에서 값, null 값 또는 정의되지 않은 값이 들어 있지 않은 항목을 찾아 제거하고 복사본을 반환합니다.

##### 매개 변수 {#parameters-cleanup}

* **`tree`:** 정리할 개체입니다.

##### 반환 {#returns-cleanup}

정리된 트리 사본.

#### getItem() {#getitem}

키에 대한 개체에서 값을 검색합니다.

##### 매개 변수 {#parameters-getitem-2}

* **`tree`:** 데이터 개체.
* **`key`:** 검색할 값의 키입니다.

##### 반환 {#returns-getitem-2}

키와 일치하는 값입니다. 키에 자식 키가 있으면 이 함수는 복잡한 개체를 반환합니다. 키의 값 유형이 `undefined`, `null` 가 반환됩니다.

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

다음 예제 코드는 값을 반환합니다 `260`:

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

* **`tree`:** 데이터 트리의 키를 검색할 객체입니다.
* **`parent`:** (선택 사항) 하위 항목의 키를 검색할 데이터 트리의 항목 키입니다.
* **`order`:** (선택 사항) 반환된 키의 정렬 순서를 결정하는 함수입니다. (자세한 내용은 [`Array.prototype.sort`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/sort) ( Mozilla Developer Network)에서 생성합니다.

##### 반환 {#returns-getkeys-2}

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

다음 `ContextHub.Utils.JSON.tree.getKeys(myObject);` 스크립트는 다음 배열을 반환합니다.

```javascript
["/location", "/location/city", "/location/country", "/location/latitude", "/location/longitude", "/location/weather", "/location/weather/humidity", "/location/weather/precipitation", "/location/weather/temperature", "/location/weather/wind"]
```

#### removeItem() {#removeitem}

지정된 객체의 복사본을 만들고 데이터 트리에서 지정된 분기를 제거하고 수정된 복사본을 반환합니다.

##### 매개 변수 {#parameters-removeitem-2}

* **`tree`:** 데이터 개체.
* **`key`:** 제거할 키입니다.

##### 반환 {#returns-removeitem-2}

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

#### decrizeKey(key) {#sanitizekey-key}

문자열 값을 정리하여 키로 사용할 수 있도록 합니다. 문자열을 정리하려면 다음 작업을 수행합니다.

* 연속된 여러 슬래시를 단일 슬래시로 줄입니다.
* 문자열의 시작 및 끝에서 공백을 제거합니다.
* 결과를 슬래시로 구분된 문자열 배열로 분할합니다.

결과 배열을 사용하여 사용 가능한 키를 만듭니다.

##### 매개 변수 {#parameters-sanitizekey}

* **`key`:** 다음 `string` 세정처리

##### 반환 {#returns-sanitizekey}

일련의 `string` 각 문자열이 의 부분인 값 `key` 그것은 슬래시로 표시되었다. 정리된 키를 나타냅니다. 정리된 배열의 길이가 0인 경우 이 함수는 를 반환합니다 `null`.

##### 예 {#example-sanitizekey}

다음 코드는 문자열을 정리하여 배열을 생성합니다 `["this", "is", "a", "path"]`, 그런 다음 키를 생성합니다 `"/this/is/a/path"` 스토리지 시스템:

```javascript
var key = " / this////is/a/path ";
ContextHub.Utils.JSON.tree.sanitizeKey(key)
"/" + ContextHub.Utils.JSON.tree.sanitizeKey(key).join("/");
```

#### setItem(tree, key, value) {#setitem-tree-key-value}

객체 사본의 데이터 트리에 키/값 쌍을 추가합니다. 데이터 트리에 대한 자세한 내용은 [지속성.](contexthub.md#persistence)

##### 매개 변수 {#parameters-setitem-2}

* **`tree`:** 데이터 개체.
* **`key`:** 추가할 값과 연결할 키입니다. 키는 데이터 트리에 있는 항목의 경로입니다. 이 함수 호출 `ContextHub.Utils.JSON.tree.sanitize` 를 추가하여 키를 가릴 수 있습니다.
* **`value`:** 데이터 트리에 추가할 값입니다.

##### 반환 {#returns-setitem-2}

의 사본 `tree` 를 포함하는 개체 `key`/ `value` 한 개.

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

## ContextHub.Utils.storeCandidates {#contexthub-utils-storecandidates}

저장소 후보를 등록하고 등록된 저장소 후보자를 가져올 수 있습니다.

### 함수(ContextHub.Utils.store후보자) {#functions-contexthub-utils-storecandidates}

#### getRegisteredCompanies(storeType) {#getregisteredcandidates-storetype}

저장소 후보로 등록된 저장소 유형을 반환합니다. 특정 저장소 유형 또는 모든 저장소 유형의 등록된 후보자를 검색합니다.

##### 매개 변수 {#parameters-getregisteredcandidates}

* **`storeType`:** (문자열) 저장소 유형의 이름입니다. 자세한 내용은 `storeType` 의 매개 변수 [`ContextHub.Utils.storeCandidates.registerStoreCandidate`](#contexthub-utils-storecandidates) 함수 위에 있어야 합니다.

##### 반환 {#returns-getregisteredcandidates}

저장소 유형의 개체입니다. 객체 등록 정보는 저장소 유형 이름이고 등록 정보 값은 등록된 저장소 후보의 배열입니다.

#### getStoreFromCandiers(storeType) {#getstorefromcandidates-storetype}

등록된 후보로부터 저장소 유형을 반환합니다. 동일한 이름의 저장소 유형이 두 개 이상 등록된 경우 함수는 우선 순위가 가장 높은 저장소 유형을 반환합니다.

##### 매개 변수 {#parameters-getstorefromcandidates}

* `storeType`: (문자열) 저장소 후보의 이름입니다. 자세한 내용은 `storeType` 의 매개 변수 [`ContextHub.Utils.storeCandidates.registerStoreCandidate`](#registerstorecandidate-store-storetype-priority-applies) 함수 위에 있어야 합니다.

##### 반환 {#returns-getstorefromcandidates}

등록된 저장소 후보자를 나타내는 개체입니다. 요청한 저장소 유형이 등록되지 않은 경우 오류가 발생합니다.

#### getSupportedStoreTypes() {#getsupportedstoretypes}

저장소 후보로 등록된 저장소 유형의 이름을 반환합니다. 이 함수에는 매개 변수가 필요하지 않습니다.

##### 반환 {#returns-getsupportedstoretypes}

각 문자열이 저장소 후보가 등록된 저장소 유형인 문자열 값의 배열입니다. 자세한 내용은 `storeType` 의 매개 변수 [`ContextHub.Utils.storeCandidates.registerStoreCandidate`](#contexthub-utils-storecandidates) 함수 위에 있어야 합니다.

#### registerStoreCandidate(store, storeType, priority, apply) {#registerstorecandidate-store-storetype-priority-applies}

이름과 우선 순위를 사용하여 저장소 개체를 저장소 후보로 등록합니다.

우선 순위는 같은 이름의 점포의 중요성을 나타내는 숫자입니다. 이미 등록된 상점 후보자와 같은 이름을 사용하여 상인등록을 하면 우선순위가 높은 후보가 사용된다. 상인등록을 할 때 상인은 같은 이름 등록된 상인보다 우선순위가 높은 경우에만 등록된다.

##### 매개 변수 {#parameters-registerstorecandidate}

* **`store`:** (개체) 저장소 후보로 등록할 저장소 개체입니다.
* **`storeType`:** (문자열) 저장소 후보의 이름입니다. 이 값은 저장소 후보의 인스턴스를 만들 때 필요합니다.
* **`priority`:** (숫자) 상점 후보자의 우선순위.
* **`applies`:** (함수) 현재 환경에서 저장소의 적용을 평가하는 를 호출하는 함수입니다. 함수는 `true` 스토어가 적용 가능한 경우 `false` 그렇지 않은 경우 기본값은 true를 반환하는 함수입니다. `function() {return true;}`

##### 예 {#example-registerstorecandidate}

```javascript
ContextHub.Utils.storeCandidates.registerStoreCandidate(myStoreCandidate,
                                'contexthub.mystorecandiate', 0);
```
