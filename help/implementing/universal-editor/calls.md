---
title: Universal Editor 호출
description: 범용 편집기에서 디버깅할 때 유용하게 사용할 수 있도록 앱에 수행하는 다양한 유형의 호출에 대해 알아봅니다.
exl-id: 00d66e59-e445-4b5c-a5b1-c0a9f032ebd9
feature: Developing
role: Admin, Architect, Developer
source-git-commit: 646ca4f4a441bf1565558002dcd6f96d3e228563
workflow-type: tm+mt
source-wordcount: '615'
ht-degree: 2%

---


# Universal Editor 호출 {#calls}

범용 편집기에서 디버깅할 때 유용하게 사용할 수 있도록 앱에 수행하는 다양한 유형의 호출에 대해 알아봅니다.

## 개요 {#overview}

범용 편집기는 일련의 정의된 호출을 통해 계측된 앱과 통신합니다. 이 작업은 최종 사용자 경험에 영향을 주지 않으며 투명합니다.

그러나 개발자의 경우 이러한 호출과 호출이 수행하는 작업을 이해하는 것은 범용 편집기를 사용할 때 애플리케이션을 디버깅할 때 유용할 수 있습니다. 앱을 계측했지만 예상대로 작동하지 않는 경우 브라우저에서 개발자 도구의 **네트워크** 탭을 열고 앱에서 콘텐츠를 편집할 때 호출을 검사하는 것이 좋습니다.

![브라우저 개발자 도구의 네트워크 탭에 대한 세부 정보 호출의 예](assets/calls-network-tab.png)

* 호출의 **페이로드**&#x200B;에는 업데이트할 항목과 업데이트 방법을 확인하는 등 편집기에서 업데이트 중인 항목에 대한 세부 정보가 포함되어 있습니다.
* **응답**&#x200B;에는 편집기 서비스에서 정확히 업데이트한 내용에 대한 세부 정보가 포함되어 있습니다. 편집기에서 콘텐츠를 쉽게 새로 고칠 수 있도록 하기 위한 것입니다. 경우에 따라 `move` 호출과 같이 전체 페이지를 새로 고쳐야 합니다.

호출이 성공적으로 완료되면 요청 및 응답의 페이로드를 포함하는 이벤트가 트리거되며, 이는 자체 앱에 대해 사용자 지정할 수 있습니다. 자세한 내용은 [유니버설 편집기 이벤트](/help/implementing/universal-editor/events.md) 문서를 참조하십시오.

다음은 범용 편집기에서 앱에 수행하는 호출 유형 목록과 함께 샘플 페이로드 및 응답입니다.

## 업데이트 {#update}

범용 편집기를 사용하여 앱에서 콘텐츠를 편집할 때 `update` 호출이 발생합니다. `update`은(는) 변경 내용을 유지합니다.

페이로드에는 JCR에 다시 쓸 내용에 대한 세부 사항이 포함되어 있습니다.

* `resource`: 업데이트할 JCR 경로
* `prop`: 업데이트 중인 JCR 속성
* `type`: 업데이트하는 속성의 JCR 값 형식입니다
* `value`: 업데이트된 데이터

>[!BEGINTABS]

>[!TAB 샘플 페이로드]

```json
{
  "connections": [
    {
      "name": "aem",
      "protocol": "aem",
      "uri": "https://localhost:8443"
    }
  ],
  "target": {
    "resource": "urn:aem:/content/wknd/language-masters/en/jcr:content/root/container/carousel/item_1571954853062",
    "type": "text",
    "prop": "jcr:title"
  },
  "value": "Tiny Toon Adventures"
}
```

>[!TAB 샘플 응답]

```json
{
  "updates": [
    {
      "resource": "urn:aem:/content/wknd/language-masters/en/jcr:content/root/container/carousel/item_1571954853062",
      "prop": "jcr:title",
      "type": "text"
    }
  ]
}
```

>[!ENDTABS]

## 세부 사항 {#details}

앱의 콘텐츠를 검색하기 위해 유니버설 편집기에서 앱을 로드할 때 `details` 호출이 발생합니다.

페이로드에는 범용 편집기에서 렌더링할 수 있도록 렌더링할 데이터와 데이터가 나타내는 사항(스키마)에 대한 세부 사항이 포함됩니다.

* 데이터 스키마가 앱에 정의되어 있으므로 구성 요소의 경우 유니버설 편집기는 `data` 개체만 검색합니다.
* 콘텐츠 조각의 경우 콘텐츠 조각 모델이 JCR에 정의되어 있으므로 유니버설 편집기는 `schema` 개체도 검색합니다.

>[!BEGINTABS]

>[!TAB 샘플 페이로드]

```json
{
  "connections": [
    {
      "name": "aem",
      "protocol": "aem",
      "uri": "https://localhost:8443"
    }
  ],
  "target": {
    "resource": "urn:aem:/content/wknd/language-masters/en/jcr:content/root/container/carousel/item_1571954853062",
    "type": "component",
    "prop": ""
  }
}
```

>[!TAB 샘플 응답]

```json
{
  "data": {
    "jcr:primaryType": "nt:unstructured",
    "jcr:title": "Tiny Toon Adventures",
    "fileReference": "/content/dam/wknd-shared/en/adventures/riverside-camping-australia/adobestock-216674449.jpeg",
    "cq:panelTitle": "WKND Adventures",
    "actionsEnabled": "true",
    "jcr:lastModifiedBy": "admin",
    "titleFromPage": "false",
    "jcr:description": "<p>With WKND Adventures, you don't just see the world you experinece it.</p>\r\n",
    "jcr:lastModified": "Fri Jan 19 2024 11:05:59 GMT+0100",
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

>[!ENDTABS]

## 추가 {#add}

범용 편집기를 사용하여 앱에 새 구성 요소를 배치하면 `add` 호출이 발생합니다.

페이로드에는 콘텐츠를 추가해야 하는 `path` 개체가 포함되어 있습니다.

또한 각 플러그인에 대해 [을(를) 저장할 콘텐츠의 끝점별 세부 정보에 대한 추가 개체가 있는 `content` 개체도 포함됩니다.](/help/implementing/universal-editor/architecture.md) 예를 들어 앱이 AEM 및 Magento의 콘텐츠를 기반으로 하는 경우 페이로드에는 각 시스템의 데이터 개체가 포함됩니다.

>[!BEGINTABS]

>[!TAB 샘플 페이로드]

```json
{
  "connections": [
    {
      "name": "aemconnection",
      "protocol": "aem",
      "uri": "https://author-pXXXX-eYYYYY.adobeaemcloud.com"
    }
  ],
  "target": {
    "container": {
      "resource": "urn:aemconnection:/content/wknd/language-masters/en/universal-editor-container/jcr:content/root/container",
      "type": "container",
      "prop": ""
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

>[!TAB 샘플 응답]

```json
{
  "updates": [
    {
      "resource": "urn:aemconnection:/content/wknd/language-masters/en/universal-editor-container/jcr:content/root/container",
      "type": "container"
    }
  ],
  "resource": "urn:aemconnection:/content/wknd/language-masters/en/universal-editor-container/jcr:content/root/container/text_1138559521"
}
```

>[!ENDTABS]

## 이동 {#move}

범용 편집기를 사용하여 앱 내에서 구성 요소를 이동할 때 `move` 호출이 발생합니다.

페이로드에는 구성 요소가 있던 위치를 정의하는 `from` 개체와 구성 요소가 이동된 위치를 정의하는 `to` 개체가 포함됩니다.

>[!BEGINTABS]

>[!TAB 샘플 페이로드]

```json
{
  "connections": [
    {
      "name": "aemconnection",
      "protocol": "aem",
      "uri": "https://author-pXXXX-eYYYYY.adobeaemcloud.com"
    }
  ],
  "from": {
    "container": {
      "resource": "urn:aemconnection:/content/wknd/language-masters/en/universal-editor-container/jcr:content/root/container",
      "type": "container",
      "prop": ""
    },
    "component": {
      "resource": "urn:aemconnection:/content/wknd/language-masters/en/universal-editor-container/jcr:content/root/container/image_275525847",
      "type": "media",
      "prop": "fileReference"
    }
  },
  "to": {
    "container": {
      "resource": "urn:aemconnection:/content/wknd/language-masters/en/universal-editor-container/jcr:content/root/container",
      "type": "container",
      "prop": ""
    }
  }
}
```

>[!TAB 샘플 응답]

```json
{
  "updates": [
    {
      "resource": "urn:aemconnection:/content/wknd/language-masters/en/universal-editor-container/jcr:content/root/container",
      "type": "container"
    }
  ]
}
```

>[!ENDTABS]

## 제거 {#remove}

범용 편집기를 사용하여 앱 내의 구성 요소를 삭제하면 `remove` 호출이 발생합니다.

페이로드에는 제거되는 객체의 경로가 포함됩니다.

>[!BEGINTABS]

>[!TAB 샘플 페이로드]

```json
{
  "connections": [
    {
      "name": "aemconnection",
      "protocol": "aem",
      "uri": "https://author-pXXXX-eYYYYY.adobeaemcloud.com"
    }
  ],
  "target": {
    "component": {
      "resource": "urn:aemconnection:/content/wknd/language-masters/en/universal-editor-container/jcr:content/root/container/text_593170193",
      "type": "text",
      "prop": "text"
    },
    "container": {
      "resource": "urn:aemconnection:/content/wknd/language-masters/en/universal-editor-container/jcr:content/root/container",
      "type": "container",
      "prop": ""
    }
  }
}
```

>[!TAB 샘플 응답]

```json
{
  "updates": [
    {
      "resource": "urn:aemconnection:/content/wknd/language-masters/en/universal-editor-container/jcr:content/root/container",
      "prop": "",
      "type": "container"
    }
  ]
}
```

>[!ENDTABS]

## 게시 {#publish}

편집한 콘텐츠를 게시하기 위해 범용 편집기에서 **Publish** 단추를 클릭하면 `publish` 호출이 발생합니다.

유니버설 편집기는 콘텐츠를 반복하여 게시해야 하는 참조 목록을 생성합니다.

>[!BEGINTABS]

>[!TAB 샘플 페이로드]

```json
{
  "connections": [
    {
      "name": "aemconnection",
      "protocol": "aem",
      "uri": "https://author-pXXXX-eYYYYY.adobeaemcloud.com"
    }
  ],
  "references": [
    "urn:aemconnection:/content/dam/wknd-shared/en/magazine/arctic-surfing/aloha-spirits-in-northern-norway/jcr:content/data/master",
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
    "urn:aemconnection:/content/wknd/language-masters/en/universal-editor-container/jcr:content/root/container/image",
    "urn:aemconnection:/content/wknd/language-masters/en/universal-editor-container/jcr:content/root/container/text",
    "urn:aemconnection:/content/wknd/language-masters/en/universal-editor-container/jcr:content/root/container/image_229050934",
    "urn:aemconnection:/content/wknd/language-masters/en/universal-editor-container/jcr:content/root/container/image_2123678383",
    "urn:aemconnection:/content/wknd/language-masters/en/universal-editor-container/jcr:content/root/container/text_1668104604",
    "urn:aemconnection:/content/wknd/language-masters/en/universal-editor-container/jcr:content/root/container/text_1138559521",
    "urn:aemconnection:/content/wknd/language-masters/en/universal-editor-container/jcr:content/root/container/image_275525847"
  ]
}
```

>[!TAB 샘플 응답]

```json
{
  "publishes": [
    "/content/dam/wknd-shared/en/magazine/arctic-surfing/aloha-spirits-in-northern-norway",
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

>[!ENDTABS]

## 추가 리소스 {#additional-resources}

* [유니버설 편집기 이벤트](/help/implementing/universal-editor/events.md)

