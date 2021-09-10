---
title: Screens에서 Cloud Service 구성
description: 이 페이지에서는 Screens의 Dispatcher 구성을 Cloud Service으로 설명합니다.
source-git-commit: b00fd1e3826a7d0b0a4bf80b002fffda8f3983d0
workflow-type: tm+mt
source-wordcount: '140'
ht-degree: 0%

---


# Screens에서 Cloud Service 구성 {#dispatcher-configurations-screens-cloud}

이 섹션에서는 Screens에 대한 디스패처 구성을 Cloud Service으로 설명합니다.

## Screens용 Dispatcher에서 Cloud Service 배포으로 필터 및 캐시 규칙 추가 {#deployment}

Screens에서 Cloud Service 인스턴스로 게시 인스턴스에 대해 dispatcher에서 다음 필터 및 캐시 규칙을 허용합니다.

### AEM Screens 필터 {#filters}

```
## # Content Configurations
/0200 { /type "allow" /method '(GET|HEAD)' /url "/content/screens/*" }
#/0201 { /type "allow" /method '(GET|HEAD)' /url "/content/experience-fragments/*" } ## uncomment this, if you're using experience-fragments
## add any other formats required for your project here
/0202 { /type "allow" /extension '(css|eot|gif|ico|jpeg|jpg|js|gif|pdf|png|svg|swf|ttf|woff|woff2|html|mp4|mov|m4v)' /path "/content/dam/*" }
/0203 { /type "allow" /method 'GET' /url "/screens/channels.json" }
## # Enable clientlibs proxy servlet
/0210 { /type "allow" /method "GET" /url "/etc.clientlibs/*" }
```

### 캐시 규칙 {#cache-rules}

* `publish_farm.any`/의 `/cache` 섹션에 `/statfileslevel "10"`을 추가합니다.

   >[!NOTE]
   >이 캐시 규칙은 캐시 docroot에서 최대 10개 수준의 캐싱을 지원하며 컨텐츠가 게시되면 모든 항목을 무효화하지 않고 무효화합니다. 컨텐츠 구조가 설정되는 깊이에 따라 이 수준을 변경할 수 있습니다.

* `publish_farm.any`의 `/invalidate` 섹션에 다음을 추가합니다.

   ```
   /0003 {
       /glob "*.json"
       /type "allow"
   }
   ```

* 다음 규칙을 publish_farm.any의 `/cache`에 있는 `/rules` 섹션 또는 `publish_farm.any`에 포함된 파일에 추가합니다.

   ```
   ## Allow Dispatcher Cache for Screens channels
    /0002
        {
        /glob "/content/screens/*.html"
        /type "allow"
        }
   
   ## Allow Dispatcher Cache for Screens offline manifests
   
   /0003
       {
       /glob "/content/screens/*.manifest.json"
       /type "allow"
       }
   
   ## Allow Dispatcher Cache for Assets
   /0004
       {
       /glob "/content/dam/*"
       /type "allow"
       }
   
   ## Deny Screens Channels json
   /0005
       {
       /glob "/screens/channels.json"
       /type "deny"
       }
   ```
