---
title: REST API
description: Screens as a Cloud Service은 Siren 사양을 따르는 간단한 RESTful API를 제공합니다. 이 페이지를 따라 콘텐츠 구조를 탐색하고 환경의 장치에 명령을 보내는 방법을 알아보십시오.
exl-id: 2c52583f-0dd9-4fa3-880b-7671442989ae
feature: Developing Screens
role: Admin, Developer
source-git-commit: f9ba9fefc61876a60567a40000ed6303740032e1
workflow-type: tm+mt
source-wordcount: '200'
ht-degree: 2%

---

# REST API {#rest-apis}

AEM Screens은 다음을 따르는 간단한 RESTful API를 제공합니다. [사이렌](https://github.com/kevinswiber/siren) 사양. 콘텐츠 구조를 탐색하고 환경의 장치에 명령을 전송할 수 있습니다.

API는에서 액세스할 수 있습니다. [*http://localhost:4502/api/screens.json*](http://localhost:4502/api/screens.json).

## 콘텐츠 구조 탐색 {#navigating-content-structure}

API 호출에 의해 반환되는 JSON에는 현재 리소스와 관련된 엔티티가 나열됩니다. 나열된 자체 링크에 따라 이러한 각 엔티티는 다시 REST 리소스로 액세스할 수 있습니다.

예를 들어 데모 대표 위치에 있는 디스플레이에 액세스하려면 다음을 호출할 수 있습니다.

```xml
GET /api/screens/content/screens/we-retail/locations/demo/flagship.json HTTP/1.1
Host: http://localhost:4502
```

또는 curl 사용:

```xml
curl -u admin:admin http://localhost:4502/api/screens/content/screens/we-retail/locations/demo/flagship.json
```

결과는 다음과 같습니다.

```xml
{
  "class": [
    "aem-io/screens/location"
  ],
  "links": [
    {
      "rel": [
        "self"
      ],
      "href": "http://localhost:4502/api/screens/content/screens/we-retail/locations/demo/flagship.json"
    },
    {
      "rel": [
        "parent"
      ],
      "href": "http://localhost:4502/api/screens/content/screens/we-retail/locations/demo.json"
    }
  ],
  "properties": {…},
  "entities": [
    {
      "class": [
        "aem-io/screens/display"
      ],
      "links": [
        {
          "rel": [
            "self"
          ],
          "href": "http://localhost:4502/api/screens/content/screens/we-retail/locations/demo/flagship/single.json"
        }
      ],
      "rel": [
        "child"
      ],
      "properties": {
        "title": "Single Screen Display",
        "height": 1440,
        "description": "Demo location of a single screen display.",
        "name": "single",
        "width": 2560,
        "idletimeout": 300,
        "layoutrows": 1,
        "layoutcols": 1
      }
    },
    …
  ]
}
```

그런 다음 단일 화면 디스플레이에 액세스하려면 다음을 호출할 수 있습니다.

```xml
GET /api/screens/content/screens/we-retail/locations/demo/flagship/single.json HTTP/1.1
Host: http://localhost:4502
```

## 리소스에 대한 작업 실행 {#executing-actions-on-the-resource}

API 호출에 의해 반환되는 JSON에는 리소스에서 사용할 수 있는 작업 목록이 포함될 수 있습니다.

예를 들어 디스플레이에는 다음 항목이 나열됩니다. *브로드캐스트 명령* 해당 디스플레이에 할당된 모든 장치에 명령을 보낼 수 있는 작업입니다.

```xml
GET /api/screens/content/screens/we-retail/locations/demo/flagship/single.json HTTP/1.1
Host: http://localhost:4502
```

또는 curl 사용:

```xml
curl -u admin:admin http://localhost:4502/api/screens/content/screens/we-retail/locations/demo/flagship/single.json
```

***결과:***

```xml
{
  "class": [
    "aem-io/screens/display"
  ],
  "links": […],
  "properties": {…},
  "entities": […],
  "actions": [
    {
      "title": "",
      "name": "broadcast-command",
      "method": "POST",
      "href": "/api/screens/content/screens/we-retail/locations/demo/flagship/single",
      "fields": [
        {
          "name": ":operation",
          "value": "broadcast-command",
          "type": "hidden"
        },
        {
          "name": "msg",
          "type": "text"
        }
      ]
    }
  ]
}
```

이 작업을 트리거하려면 다음을 호출합니다.

```xml
POST /api/screens/content/screens/we-retail/locations/demo/flagship/single.json HTTP/1.1
Host: http://localhost:4502

:operation=broadcast-command&msg=reboot
```

또는 curl 사용:

```xml
curl -u admin:admin -X POST -d ':operation=broadcast-command&msg=reboot' http://localhost:4502/api/screens/content/screens/we-retail/locations/demo/flagship/single.json
```
