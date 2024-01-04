---
title: 유니버설 편집기 호출
description: 범용 편집기에서 디버깅할 때 유용하게 사용할 수 있도록 앱에 수행하는 다양한 유형의 호출에 대해 알아봅니다.
source-git-commit: 16f2922a3745f9eb72f7070c30134e5149eb78ce
workflow-type: tm+mt
source-wordcount: '635'
ht-degree: 1%

---


# 유니버설 편집기 호출 {#calls}

범용 편집기에서 디버깅할 때 유용하게 사용할 수 있도록 앱에 수행하는 다양한 유형의 호출에 대해 알아봅니다.

{{universal-editor-status}}

## 개요 {#overview}

범용 편집기는 일련의 정의된 호출을 통해 계측된 앱과 통신합니다. 이 작업은 최종 사용자 경험에 영향을 주지 않으며 투명합니다.

그러나 개발자의 경우 이러한 호출과 호출이 수행하는 작업을 이해하는 것은 범용 편집기를 사용할 때 애플리케이션을 디버깅할 때 유용할 수 있습니다. 앱을 계측했지만 예상대로 작동하지 않는 경우 를 여는 것이 도움이 될 수 있습니다. **네트워크** 브라우저에서 개발자 도구의 탭을 열고 앱에서 콘텐츠를 편집할 때 호출을 검사합니다.

![브라우저 개발자 도구의 네트워크 탭에 있는 세부 정보 호출의 예](assets/calls-network-tab.png)

* 다음 **페이로드** 의 호출에는 업데이트할 항목과 업데이트 방법을 식별하는 등 편집기에서 업데이트 중인 사항에 대한 세부 정보가 포함되어 있습니다.
* 다음 **응답** 편집기 서비스에서 정확히 업데이트한 내용에 대한 세부 정보를 포함합니다. 편집기에서 콘텐츠를 쉽게 새로 고칠 수 있도록 하기 위한 것입니다. 특정 경우, 예: `move` 를 호출하면 전체 페이지를 새로 고쳐야 합니다.

다음은 범용 편집기에서 앱에 수행하는 호출 유형 목록과 함께 샘플 페이로드 및 응답입니다.

## 업데이트 {#update}

An `update` 범용 편집기를 사용하여 앱의 콘텐츠를 편집할 때 호출이 발생합니다. 다음 `update` 는 변경 사항을 유지합니다.

페이로드에는 JCR에 다시 쓸 내용에 대한 세부 사항이 포함되어 있습니다.

* `itemid`: 업데이트할 JCR 경로
* `itemprop`: 업데이트 중인 JCR 속성
* `itemtype`: 업데이트 중인 속성의 JCR 값 유형
* `value`: 업데이트된 데이터

### 샘플 페이로드 {#update-payload}

```json
{
  "op": "patch",
  "connections": {
    "aem": "aem:https://author-pXXXX-eYYYYY.adobeaemcloud.com"
  },
  "path": {
    "itemid": "urn:aem:/content/wknd/language-masters/en/jcr:content/root/container/carousel/item_1571954853062",
    "itemtype": "text",
    "itemprop": "jcr:title"
  },
  "value": "Tiny Toon Adventures"
}
```

### 샘플 응답 {#update-response}

```json
{
  "updates": [
    {
      "itemid": "urn:aem:/content/wknd/language-masters/en/jcr:content/root/container/carousel/item_1571954853062",
      "itemprop": "jcr:title",
      "itemtype": "text"
    }
  ]
}
```

## 세부 사항 {#details}

A `details` 범용 편집기에서 앱을 로드하여 앱 콘텐츠를 검색할 때 호출이 발생합니다.

페이로드에는 범용 편집기에서 렌더링할 수 있도록 렌더링할 데이터와 데이터가 나타내는 사항(스키마)에 대한 세부 사항이 포함됩니다.

* 구성 요소의 경우 범용 편집기는 `data` 데이터의 스키마가 앱에서 정의되므로 개체를 작성합니다.
* 콘텐츠 조각의 경우 범용 편집기는 `schema` jcr에 콘텐츠 조각 모델 이 정의되어 있으므로 개체가 잘못되었습니다.

### 샘플 페이로드 {#details-payload}

```json
{
  "op": "patch",
  "connections": {
    "aem": "aem:https://author-pXXXX-eYYYYY.adobeaemcloud.com"
  },
  "path": {
    "itemid": "urn:aem:/content/wknd/language-masters/en/jcr:content/root/container/carousel/item_1571954853062",
    "itemtype": "component",
    "itemprop": ""
  }
}
```

### 샘플 응답 {#details-response}

```json
{
  "data": {
    "jcr:primaryType": "nt:unstructured",
    "jcr:title": "Tiny Toon Adventures!",
    "fileReference": "/content/dam/wknd-shared/en/adventures/riverside-camping-australia/adobestock-216674449.jpeg",
    "cq:panelTitle": "WKND Adventures",
    "actionsEnabled": "true",
    "jcr:lastModifiedBy": "admin",
    "titleFromPage": "false",
    "jcr:description": "<p>With WKND Adventures, you don't just see the world you experinece it.</p>",
    "jcr:lastModified": "Wed Jan 03 2024 09:06:05 GMT+0100",
    "descriptionFromPage": "true",
    "sling:resourceType": "wknd/components/teaser",
    "textIsRich": "true",
    "cq:styleIds": [
      "1555543212672"
    ],
    "actions": {
      "jcr:primaryType": "nt:unstructured",
      "item0": {
        "jcr:primaryType": "nt:unstructured",
        "link": "/content/wknd/language-masters/en/adventures",
        "text": "View Trips"
      }
    }
  }
}
```

## 추가 {#add}

An `add` 범용 편집기를 사용하여 앱에 새 구성 요소를 배치하면 호출이 발생합니다.

페이로드에는 다음이 포함됩니다. `path` 컨텐츠를 추가해야 하는 위치를 포함하는 객체입니다.

여기에는 또한 `content` 저장할 콘텐츠의 끝점별 세부 정보에 대한 추가 개체가 있는 개체 [각 플러그인에 대해](/help/implementing/universal-editor/architecture.md) 예를 들어 앱이 AEM 및 Magento의 콘텐츠를 기반으로 하는 경우 페이로드에는 각 시스템에 대한 데이터 개체가 포함됩니다.

### 샘플 페이로드 {#add-payload}

```json
{
  "op": "patch",
  "connections": {
    "aemconnection": "aem:https://author-pXXXX-eYYYYY.adobeaemcloud.com"
  },
  "path": {
    "container": {
      "itemid": "urn:aemconnection:/content/wknd/language-masters/en/universal-editor-container/jcr:content/root/container",
      "itemtype": "container",
      "itemprop": ""
    }
  },
  "content": {
    "name": "text",
    "aem": {
      "page": {
        "resourceType": "wknd/components/text",
        "template": {
          "text": "Default Text"
        }
      }
    }
  }
}
```

### 샘플 응답 {#add-response}

```json
{
  "updates": [
    {
      "itemid": "urn:aemconnection:/content/wknd/language-masters/en/universal-editor-container/jcr:content/root/container",
      "itemtype": "container"
    }
  ]
}
```

## 이동 {#move}

A `move` 호출은 범용 편집기를 사용하여 앱 내의 구성 요소를 이동할 때 발생합니다.

페이로드에는 다음이 포함됩니다. `from` 구성 요소가 있었던 위치와 `to` 이동된 위치를 정의하는 개체입니다.

### 샘플 페이로드 {#move-payload}

```json
{
  "op": "patch",
  "connections": {
    "aemconnection": "aem:https://author-pXXXX-eYYYYY.adobeaemcloud.com"
  },
  "from": {
    "container": {
      "itemid": "urn:aemconnection:/content/wknd/language-masters/en/universal-editor-container/jcr:content/root/container",
      "itemtype": "container",
      "itemprop": ""
    },
    "component": {
      "itemid": "urn:aemconnection:/content/wknd/language-masters/en/universal-editor-container/jcr:content/root/container/text_1068508321",
      "itemtype": "text",
      "itemprop": "text"
    }
  },
  "to": {
    "container": {
      "itemid": "urn:aemconnection:/content/wknd/language-masters/en/universal-editor-container/jcr:content/root/container",
      "itemtype": "container",
      "itemprop": ""
    },
    "before": {
      "itemid": "urn:aemconnection:/content/wknd/language-masters/en/universal-editor-container/jcr:content/root/container/text_2063168902",
      "itemtype": "text",
      "itemprop": "text"
    }
  }
}
```

### 샘플 응답 {#move-response}

```json
{
  "updates": [
    {
      "itemid": "urn:aemconnection:/content/wknd/language-masters/en/universal-editor-container/jcr:content/root/container",
      "itemtype": "container"
    }
  ]
}
```

## 제거 {#remove}

A `remove` 범용 편집기를 사용하여 앱 내의 구성 요소를 삭제하면 호출이 발생합니다.

페이로드에는 제거되는 객체의 경로가 포함됩니다.

### 샘플 페이로드 {#remove-payload}

```json
{
  "op": "patch",
  "connections": {
    "aemconnection": "aem:https://author-pXXXX-eYYYYY.adobeaemcloud.com"
  },
  "path": {
    "component": {
      "itemid": "urn:aemconnection:/content/wknd/language-masters/en/universal-editor-container/jcr:content/root/container/text_1068508321",
      "itemtype": "text",
      "itemprop": "text"
    },
    "container": {
      "itemid": "urn:aemconnection:/content/wknd/language-masters/en/universal-editor-container/jcr:content/root/container",
      "itemtype": "container",
      "itemprop": ""
    }
  }
}
```

### 샘플 응답 {#remove-response}

```json
{
  "updates": [
    {
      "itemid": "urn:aemconnection:/content/wknd/language-masters/en/universal-editor-container/jcr:content/root/container",
      "itemprop": "",
      "itemtype": "container"
    }
  ]
}
```

## 패치 {#patch}

A `patch` 호출은 앱 내의 대화 상자에서 콘텐츠를 업데이트할 때 발생합니다. 이렇게 하면 앱의 페이지 내에 있는 콘텐츠가 JSON 패치로 기존 콘텐츠에 업데이트됩니다.

페이로드에는 페이지에 있는 콘텐츠의 경로와, 변경할 JSON 패치가 포함됩니다.

### 샘플 페이로드 {#patch-payload}

```json
{
  "op": "patch",
  "connections": {
    "aemconnection": "aem:https://author-pXXXX-eYYYYY.adobeaemcloud.com"
  },
  "path": {
    "itemid": "urn:aemconnection:/content/wknd/language-masters/en/universal-editor-container/jcr:content/root/container/text_1540979193",
    "itemtype": "text",
    "itemprop": "text"
  },
  "patch": [
    {
      "op": "replace",
      "path": "/text",
      "value": "Still More WKND Adventures"
    }
  ]
}
```

### 샘플 응답 {#patch-response}

```json
{
  "updates": [
    {
      "itemid": "urn:aemconnection:/content/wknd/language-masters/en/universal-editor-container/jcr:content/root/container/text_1540979193"
    }
  ]
}
```

## 게시 {#publish}

A `publish` 을 클릭하면 호출이 발생합니다. **게시** 편집한 콘텐츠를 게시하려면 [범용 편집기]의 단추를 클릭하십시오.

유니버설 편집기는 콘텐츠를 반복하여 게시해야 하는 참조 목록을 생성합니다.

### 샘플 페이로드 {#publish-payload}

```json
{
  "op": "patch",
  "connections": {
    "aemconnection": "aem:https://author-pXXXX-eYYYYY.adobeaemcloud.com"
  },
  "references": [
    "urn:aemconnection:/content/dam/wknd-shared/en/magazine/arctic-surfing/aloha-spirits-in-northern-norway/jcr:content/data/master",
    "urn:aemconnection:/content/wknd/us/en/adventures/jcr:content/root/container/container/title",
    "urn:aemconnection:/content/dam/wknd-shared/en/adventures/bali-surf-camp/bali-surf-camp/jcr:content/data/master",
    "urn:aemconnection:/content/dam/wknd-shared/en/adventures/climbing-new-zealand/climbing-new-zealand/jcr:content/data/master",
    "urn:aemconnection:/content/dam/wknd-shared/en/adventures/cycling-southern-utah/cycling-southern-utah/jcr:content/data/master",
    "urn:aemconnection:/content/dam/wknd-shared/en/adventures/cycling-tuscany/cycling-tuscany/jcr:content/data/master",
    "urn:aemconnection:/content/dam/wknd-shared/en/adventures/downhill-skiing-wyoming/downhill-skiing-wyoming/jcr:content/data/master",
    "urn:aemconnection:/content/dam/wknd-shared/en/adventures/napa-wine-tasting/napa-wine-tasting/jcr:content/data/master",
    "urn:aemconnection:/content/dam/wknd-shared/en/adventures/riverside-camping-australia/riverside-camping-australia/jcr:content/data/master",
    "urn:aemconnection:/content/dam/wknd-shared/en/adventures/ski-touring-mont-blanc/ski-touring-mont-blanc/jcr:content/data/master",
    "urn:aemconnection:/content/dam/wknd-shared/en/adventures/surf-camp-in-costa-rica/surf-camp-costa-rica/jcr:content/data/master",
    "urn:aemconnection:/content/dam/wknd-shared/en/adventures/tahoe-skiing/tahoe-skiing/jcr:content/data/master",
    "urn:aemconnection:/content/dam/wknd-shared/en/adventures/west-coast-cycling/west-coast-cycling/jcr:content/data/master",
    "urn:aemconnection:/content/dam/wknd-shared/en/adventures/yosemite-backpacking/yosemite-backpacking/jcr:content/data/master",
    "urn:aemconnection:/content/wknd/us/en/newsletter/jcr:content/root/container/title",
    "urn:aemconnection:/content/wknd/us/en/newsletter/jcr:content/root/container/text",
    "urn:aemconnection:/content/wknd/language-masters/en/universal-editor-container/jcr:content/root/title",
    "urn:aemconnection:/content/wknd/language-masters/en/universal-editor-container/jcr:content/root/container",
    "urn:aemconnection:/content/wknd/language-masters/en/universal-editor-container/jcr:content/root/container/text",
    "urn:aemconnection:/content/wknd/language-masters/en/universal-editor-container/jcr:content/root/container/image",
    "urn:aemconnection:/content/wknd/language-masters/en/universal-editor-container/jcr:content/root/container/image_2123678383",
    "urn:aemconnection:/content/wknd/language-masters/en/universal-editor-container/jcr:content/root/container/text_1668104604",
    "urn:aemconnection:/content/wknd/language-masters/en/universal-editor-container/jcr:content/root/container/image_229050934",
    "urn:aemconnection:/content/wknd/language-masters/en/universal-editor-container/jcr:content/root/container/image_275525847",
    "urn:aemconnection:/content/wknd/language-masters/en/universal-editor-container/jcr:content/root/container/text_358189229",
    "urn:aemconnection:/content/wknd/language-masters/en/universal-editor-container/jcr:content/root/container/text_2063168902",
    "urn:aemconnection:/content/wknd/language-masters/en/universal-editor-container/jcr:content/root/container/text_1540979193"
  ]
}
```

### 샘플 응답 {#publish-response}

```json
{
  "publishes": [
    "/content/dam/wknd-shared/en/magazine/arctic-surfing/aloha-spirits-in-northern-norway",
    "/content/wknd/us/en/adventures",
    "/content/dam/wknd-shared/en/adventures/bali-surf-camp/bali-surf-camp",
    "/content/dam/wknd-shared/en/adventures/climbing-new-zealand/climbing-new-zealand",
    "/content/dam/wknd-shared/en/adventures/cycling-southern-utah/cycling-southern-utah",
    "/content/dam/wknd-shared/en/adventures/cycling-tuscany/cycling-tuscany",
    "/content/dam/wknd-shared/en/adventures/downhill-skiing-wyoming/downhill-skiing-wyoming",
    "/content/dam/wknd-shared/en/adventures/napa-wine-tasting/napa-wine-tasting",
    "/content/dam/wknd-shared/en/adventures/riverside-camping-australia/riverside-camping-australia",
    "/content/dam/wknd-shared/en/adventures/ski-touring-mont-blanc/ski-touring-mont-blanc",
    "/content/dam/wknd-shared/en/adventures/surf-camp-in-costa-rica/surf-camp-costa-rica",
    "/content/dam/wknd-shared/en/adventures/tahoe-skiing/tahoe-skiing",
    "/content/dam/wknd-shared/en/adventures/west-coast-cycling/west-coast-cycling",
    "/content/dam/wknd-shared/en/adventures/yosemite-backpacking/yosemite-backpacking",
    "/content/wknd/us/en/newsletter",
    "/content/wknd/language-masters/en/universal-editor-container"
  ]
}
```
