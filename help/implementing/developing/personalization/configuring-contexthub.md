---
title: ContextHub 구성
description: Context Hub 구성 방법에 대해 알아봅니다.
translation-type: tm+mt
source-git-commit: b8bc27b51eefcfcfa1c23407a4ac0e7ff068081e
workflow-type: tm+mt
source-wordcount: '1683'
ht-degree: 1%

---


# ContextHub {#configuring-contexthub} 구성

ContextHub는 컨텍스트 데이터를 저장, 조작 및 표시하기 위한 프레임워크입니다. ContextHub에 대한 자세한 내용은 [ContextHub 개발자 개요](contexthub.md)를 참조하십시오.

ContextHub 도구 모음을 구성하여 미리 보기 모드에 나타나는지, ContextHub 저장소를 만들지, UI 모듈을 추가할지 여부를 제어할 수 있습니다.

## ContextHub UI 표시 및 숨기기 {#showing-and-hiding-the-contexthub-ui}

페이지에서 [ContextHub UI](/help/sites-cloud/authoring/personalization/targeted-content.md)을 표시하거나 숨기도록 Adobe Granite ContextHub OSGi 서비스를 구성합니다. 이 서비스의 PID는 `com.adobe.granite.contexthub.impl.ContextHubImpl.`입니다.

서비스를 구성하려면 [웹 콘솔](/help/implementing/deploying/configuring-osgi.md)을 사용하거나 저장소의 JCR 노드를 사용할 수 있습니다.

* **웹 콘솔:** UI를 표시하려면 [UI 표시] 속성을 선택합니다. UI를 숨기려면 UI 숨기기 속성을 지우십시오.
* **JCR 노드:** UI를 표시하려면 부울  `com.adobe.granite.contexthub.show_ui` 속성을 로  `true`설정합니다. UI를 숨기려면 속성을 `false`으로 설정합니다.

ContextHub UI를 표시할 때 AEM 작성자 인스턴스의 페이지에만 나타납니다. UI는 게시 인스턴스의 페이지에 표시되지 않습니다.

## ContextHub UI 모드 및 모듈 추가 {#adding-contexthub-ui-modes-and-modules}

미리 보기 모드의 ContextHub 도구 모음에 표시되는 UI 모드 및 모듈을 구성합니다.

* UI 모드:관련 모듈 그룹
* 모듈:스토어의 컨텍스트 데이터를 노출하고 작성자가 컨텍스트를 조작할 수 있는 위젯

UI 모드는 도구 모음의 왼쪽에 일련의 아이콘으로 표시됩니다. 선택하면 UI 모드의 모듈이 오른쪽에 나타납니다.

![ContextHub 도구 모음](assets/contexthub-toolbar.png)

아이콘은 [Coral UI 아이콘 라이브러리](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/coral-ui/coralui3/Coral.Icon.html#availableIcons)의 참조입니다.

### UI 모드 {#adding-a-ui-mode} 추가

관련 ContextHub 모듈을 그룹화하는 UI 모드를 추가합니다. UI 모드를 만들 때 ContextHub 도구 모음에 표시되는 제목과 아이콘을 제공합니다.

1. Experience Manager 레일에서 도구 > 사이트 > 컨텍스트 허브를 클릭하거나 탭합니다.
1. 기본 구성 컨테이너를 클릭하거나 탭합니다.
1. Context Hub 구성을 클릭하거나 탭합니다.
1. 만들기 단추를 클릭하거나 탭한 다음, Context Hub UI 모드를 클릭하거나 탭합니다.

   ![UI 모드 추가](assets/contexthub-ui-mode.png)

1. 다음 속성에 대한 값을 제공합니다.

   * UI 모드 제목:UI 모드를 식별하는 제목
   * 모드 아이콘:사용할 [Coral UI 아이콘](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/coral-ui/coralui3/Coral.Icon.html#availableIcons)에 대한 선택기(예: `coral-Icon--user`)
   * 사용:ContextHub 도구 모음에 UI 모드를 표시하려면 선택합니다.

1. 저장을 클릭하거나 탭합니다.

### UI 모듈 {#adding-a-ui-module} 추가

페이지 컨텐츠를 미리 보기 위한 ContextHub 도구 모음에 표시되도록 UI 모드에 ContextHub UI 모듈을 추가합니다. UI 모듈을 추가하면 ContextHub에 등록된 모듈 유형의 인스턴스를 만드는 것입니다. UI 모듈을 추가하려면 연결된 모듈 유형의 이름을 알아야 합니다.

AEM에서는 UI 모듈을 기반으로 할 수 있는 몇 가지 샘플 UI 모듈 유형뿐만 아니라 기본 UI 모듈 유형을 제공합니다. 다음 표에서는 각 항목에 대한 간단한 설명을 제공합니다. 사용자 지정 UI 모듈 개발에 대한 자세한 내용은 [ContextHub UI 모듈 만들기](extending-contexthub.md#creating-contexthub-ui-module-types)를 참조하십시오.

UI 모듈 속성에는 모듈별 속성에 대한 값을 제공할 수 있는 세부 구성이 포함됩니다. JSON 형식으로 세부 구성을 제공합니다. 표의 [모듈 유형] 열은 각 UI 모듈 유형에 필요한 JSON 코드에 대한 정보 링크를 제공합니다.

| 모듈 유형 | 설명 | 저장소 |
|---|---|---|
| [contexthub.base](sample-modules.md#contexthub-base-ui-module-type) | 일반 UI 모듈 유형 | UI 모듈 속성에 구성됨 |
| [contexthub.browserinfo](sample-modules.md#contexthub-browserinfo-ui-module-type) | 브라우저에 대한 정보를 표시합니다. | `surferinfo` |
| [contexthub.datetime](sample-modules.md#contexthub-datetime-ui-module-type) | 날짜 및 시간 정보를 표시합니다. | `datetime` |
| [contexthub.location](sample-modules.md#contexthub-location-ui-module-type) | 클라이언트의 위도 및 경도와 지도 상의 위치를 표시합니다. 위치를 변경할 수 있습니다. | `geolocation` |
| [contexthub.screen-orientation](sample-modules.md#contexthub-screen-orientation-ui-module-type) | 장치의 화면 방향(가로 또는 세로)을 표시합니다. | `emulators` |
| [contexthub.tagcloud](sample-modules.md#contexthub-tagcloud-ui-module-type) | 페이지 태그에 대한 통계를 표시합니다. | `tagcloud` |
| [granite.profile](sample-modules.md#granite-profile-ui-module-type) | `authorizableID`, `displayName` 및 `familyName`를 포함하여 현재 사용자에 대한 프로필 정보를 표시합니다. `displayName` 및 `familyName` 값을 변경할 수 있습니다. | `profile` |

1. Experience Manager 레일에서 도구 > 사이트 > ContextHub를 클릭하거나 탭합니다.
1. UI 모듈을 추가할 구성 컨테이너를 클릭하거나 탭합니다.
1. UI 모듈을 추가할 ContextHub 구성을 클릭하거나 입력합니다.
1. UI 모듈을 추가할 UI 모드를 클릭하거나 탭합니다.
1. 만들기 단추를 클릭하거나 탭한 다음, ContextHub UI 모듈(일반)을 클릭하거나 탭합니다.

   ![ContextHub UI 모듈](assets/contexthub-ui-module.png)

1. 다음 속성에 대한 값을 제공합니다.

   * UI 모듈 제목:UI 모듈을 식별하는 제목
   * 모듈 유형:모듈 유형
   * 사용:ContextHub 도구 모음에 UI 모듈을 표시하려면 선택합니다.

1. (선택 사항) 기본 저장소 구성을 무시하려면 JSON 개체를 입력하여 UI 모듈을 구성합니다.
1. 저장을 클릭하거나 탭합니다.

## ContextHub 저장소 만들기 {#creating-a-contexthub-store}

사용자 데이터를 유지하고 필요에 따라 데이터에 액세스하는 Context Hub 저장소를 만듭니다. ContextHub 저장소는 등록된 스토어 후보자를 기반으로 합니다. 스토어를 만들 때 스토어 후보가 등록된 storeType의 값이 필요합니다. ([사용자 지정 스토어 후보자 만들기](extending-contexthub.md#creating-custom-store-candidates)를 참조하십시오.)

### 세부 저장소 구성 {#detailed-store-configuration}

스토어를 구성할 때 [세부 사항 구성] 속성을 사용하여 스토어별 속성에 대한 값을 제공할 수 있습니다. 값은 스토어의 `init` 함수의 `config` 매개 변수를 기반으로 합니다. 따라서 이 값을 제공해야 하는지 여부와 값의 형식은 스토어에 따라 달라집니다.

세부 구성 속성 값은 JSON 형식의 `config` 개체입니다.

### 샘플 스토어 후보자 {#sample-store-candidates}

AEM은 스토어를 기반으로 할 수 있는 다음과 같은 샘플 스토어 지원자를 제공합니다.

| 스토어 유형 | 설명 |
|---|---|
| [aem.segmentation](sample-stores.md#aem-segmentation-sample-store-candidate) | 해결된 및 해결되지 않은 ContextHub 세그먼트를 저장할 수 있습니다. ContextHub SegmentManager에서 세그먼트를 자동으로 검색합니다. |
| [contextub.geolocation](sample-stores.md#contexthub-geolocation-sample-store-candidate) | 브라우저 위치의 위도와 경도를 저장합니다. |
| [granite.emulators](sample-stores.md#granite-emulators-sample-store-candidate) | 다양한 장치에 대한 속성과 기능을 정의하고 현재 클라이언트 장치를 검색합니다. |
| [granite.profile](sample-stores.md#granite-profile-sample-store-candidate) | 현재 사용자의 프로필 데이터를 저장합니다. |
| [contexthub.surferinfo](sample-stores.md#contexthub-surferinfo-sample-store-candidate) | 장치 정보, 브라우저 유형 및 창 방향 등 클라이언트에 대한 정보를 저장합니다. |

1. Experience Manager 레일에서 도구 > 사이트 > ContextHub를 클릭하거나 탭합니다.
1. 기본 구성 컨테이너를 클릭하거나 탭합니다.
1. Contexthub 구성을 클릭하거나 탭합니다.
1. 스토어를 추가하려면 만들기 아이콘을 클릭하거나 탭한 다음 ContextHub 저장소 구성을 클릭하거나 탭합니다.

   ![ContextHub 저장소 구성](assets/contexthub-store-configuration.png)

1. 기본 구성 속성에 대한 값을 제공한 다음 다음을 클릭하거나 탭합니다.

   * **구성 제목:** 스토어를 식별하는 제목
   * **스토어 유형:** 스토어의 기반이 되는 스토어 대상의 storeType 속성 값
   * **필수:** 선택
   * **활성화됨:** 스토어를 활성화하려면 선택합니다.

1. (선택 사항) 기본 저장소 구성을 무시하려면 [세부 사항 구성(JSON)] 상자에 JSON 개체를 입력합니다.
1. 저장을 클릭하거나 탭합니다.

## 예:JSONP 서비스 {#example-using-a-jsonp-service} 사용

이 예에서는 스토어를 구성하고 UI 모듈에 데이터를 표시하는 방법을 보여줍니다. 이 예에서 jsontest.com 사이트의 MD5 서비스는 스토어의 데이터 소스로 사용됩니다. 서비스는 지정된 문자열의 MD5 해시 코드를 JSON 형식으로 반환합니다.

contexthub.generic-jsonp 스토어는 서비스 호출 `https://md5.jsontest.com/?text=%22text%20to%20md5%22`에 대한 데이터를 저장하도록 구성되어 있습니다. 서비스는 UI 모듈에 표시되는 다음 데이터를 반환합니다.

```javascript
{
   "md5": "919a56ab62b6d5e1219fe1d95248a2c5",
   "original": "\"text to md5\""
}
```

### contexthub.generic-jsonp 스토어 만들기 {#creating-a-contexthub-generic-jsonp-store}

contexthub.generic-jsonp 샘플 저장소 후보를 사용하면 JSON 데이터를 반환하는 JSONP 서비스 또는 웹 서비스에서 데이터를 검색할 수 있습니다. 이 스토어 지원자의 경우 스토어 구성을 사용하여 사용할 JSONP 서비스에 대한 세부 정보를 제공합니다.

`ContextHub.Store.JSONPStore` Javascript 클래스의 [init](contexthub-api.md#init-name-config) 함수는 이 저장소 후보를 초기화하는 `config` 개체를 정의합니다. `config` 객체에는 JSONP 서비스에 대한 세부 정보가 포함된 `service` 객체가 포함되어 있습니다. 스토어를 구성하려면 `service` 개체를 JSON 형식으로 [세부 구성] 속성 값으로 제공합니다.

jsontest.com 사이트의 MD5 서비스에서 데이터를 저장하려면 다음 속성을 사용하여 [Creating a ContextHub Store](#creating-a-contexthub-store)의 절차를 사용하십시오.

* **구성 제목:** md5
* **저장소 유형:** contexthub.generic-jsonp
* **필수:** 선택
* **활성화됨:** 선택
* **세부 정보 구성(JSON):**

   ```javascript
   {
    "service": {
    "jsonp": false,
    "timeout": 1000,
    "ttl": 1800000,
    "secure": false,
    "host": "md5.jsontest.com",
    "port": 80,
    "params":{
    "text":"text to md5"
        }
      }
    }
   ```

### md5 데이터의 UI 모듈 추가 {#adding-a-ui-module-for-the-md-data}

UI 모듈을 ContextHub 도구 모음에 추가하여 예제 md5 스토어에 저장된 데이터를 표시합니다. 이 예에서 contexthub.base 모듈은 다음 UI 모듈을 생성하는 데 사용됩니다.

![ContextHub MD5 스토어](assets/contexthub-md5-store.png)

[UI 모듈 추가](#adding-a-ui-module)의 절차를 사용하여 샘플 가상 UI 모드와 같은 기존 UI 모드에 UI 모듈을 추가합니다. UI 모듈에 대해 다음 속성 값을 사용하십시오.

* **UI 모듈 제목:** MD5
* **모듈 유형:** contexthub.base
* **세부 정보 구성(JSON):**

   ```javascript
   {
    "icon": "coral-Icon--data",
    "title": "MD5 Conversion",
    "storeMapping": { "md5": "md5" },
    "template": "<p> {{md5.original}}</p>;
                 <p>{{md5.md5}}</p>"
   }
   ```

## ContextHub {#debugging-contexthub} 디버깅

ContextHub에 대한 디버깅 모드를 사용하여 문제 해결을 허용할 수 있습니다. 디버그 모드는 ContextHub 구성 또는 CRXDE를 통해 활성화할 수 있습니다.

### 구성 {#via-the-configuration} 사용

ContextHub의 구성을 편집하고 옵션 **Debug**&#x200B;을 선택합니다.

1. 레일에서 **도구 > 사이트 > ContextHub**&#x200B;를 클릭하거나 탭합니다.
1. 기본 **구성 컨테이너**&#x200B;를 클릭하거나 탭합니다.
1. **ContextHub 구성**&#x200B;을 선택하고 **선택한 요소 편집**&#x200B;을 클릭하거나 탭합니다.
1. **디버그**&#x200B;를 클릭하거나 탭하고 **저장**&#x200B;을 클릭하거나 탭합니다.

### CRXDE {#via-crxde} 사용

CRXDE Lite을 사용하여 다음 아래의 `debug` 속성을 **true**&#x200B;로 설정합니다.

* `/conf/global/settings/cloudsettings` 또는
* `/conf/<site>/settings/cloudsettings`

### ContextHub {#logging-debug-messages-for-contexthub}에 대한 디버그 메시지 로깅

개발 시 유용한 세부 디버그 메시지를 기록하도록 Adobe Granite ContextHub OSGi 서비스(PID = `com.adobe.granite.contexthub.impl.ContextHubImpl`)를 구성합니다.

서비스를 구성하려면 [웹 콘솔](/help/implementing/deploying/configuring-osgi.md)을 사용하거나 저장소의 JCR 노드를 사용할 수 있습니다.

* 웹 콘솔:디버그 메시지를 기록하려면 디버그 속성을 선택합니다.
* JCR 노드:디버그 메시지를 기록하려면 부울 `com.adobe.granite.contexthub.debug` 속성을 `true`로 설정합니다.

### 자동 모드 {#silent-mode}

자동 모드를 사용하면 모든 디버그 정보가 표시되지 않습니다. 각 ContextHub 구성에 대해 독립적으로 설정할 수 있는 일반 디버그 옵션과 달리, 자동 모드는 ContextHub 구성 수준에서 모든 디버그 설정을 이전에 가능하게 하는 전역 설정입니다.

디버그 정보를 전혀 원하지 않는 게시 인스턴스에 유용합니다. 전역 설정이므로 OSGi를 통해 활성화됩니다.

1. `http://<host>:<port>/system/console/configMgr`에서 **Adobe Experience Manager 웹 콘솔 구성**&#x200B;을 엽니다.
1. **Adobe Granite ContextHub** 검색
1. **Adobe Granite ContextHub** 구성을 클릭하여 속성을 편집합니다.
1. **자동 모드** 옵션을 선택하고 **저장**&#x200B;을 클릭합니다.

## ContextHub {#disabling-contexthub} 비활성화

ContextHub을 비활성화하여 js/css를 로드하거나 초기화할 수 없습니다. ContextHub을 비활성화하는 두 가지 옵션이 있습니다.

* ContextHub 구성을 편집하고 **ContextHub 비활성화** 옵션을 선택합니다.

   1. 레일에서 **도구 > 사이트 > ContextHub**&#x200B;를 클릭하거나 탭합니다.
   1. 기본 **구성 컨테이너**&#x200B;를 클릭하거나 탭합니다.
   1. **ContextHub 구성**&#x200B;을 선택하고 **선택한 요소 편집**&#x200B;을 클릭하거나 탭합니다.
   1. **ContextHub 비활성화**&#x200B;를 클릭하거나 탭하고 **저장**&#x200B;을 클릭하거나 탭합니다.

또는

* CRXDE Lite을 사용하여 `/conf/global/settings/cloudsettings/<configName>/contexthub` 아래의 `disabled` 속성을 **true**&#x200B;로 설정합니다.
