---
title: Screensas a Cloud Service 의 Dispatcher 구성
description: 이 페이지에서는 Screensas a Cloud Service 의 Dispatcher 구성에 대해 설명합니다.
exl-id: cc04b480-9310-4975-a7c2-20682c567fa4
feature: Administering Screens
role: Admin, Developer, User
source-git-commit: f9ba9fefc61876a60567a40000ed6303740032e1
workflow-type: tm+mt
source-wordcount: '140'
ht-degree: 0%

---

# Screensas a Cloud Service 의 Dispatcher 구성 {#dispatcher-configurations-screens-cloud}

이 섹션에서는 Screensas a Cloud Service 용 dispatcher 구성에 대해 설명합니다.

## Screens as a Cloud Service 배포를 위한 Dispatcher의 필터 및 캐시 규칙 추가 {#deployment}

Screensas a Cloud Service 의 dispatcher에서 다음 필터 및 캐시 규칙을 허용합니다.

### AEM Screens 필터 {#filters}

```
## # Content Configurations
/0200 { /type "allow" /method '(GET|HEAD)' /url "/content/screens/*" }
#/0201 { /type "allow" /method '(GET|HEAD)' /url "/content/experience-fragments/*" } ## uncomment this, if you are using experience-fragments
## add any other formats required for your project here
/0202 { /type "allow" /extension '(css|eot|gif|ico|jpeg|jpg|js|gif|pdf|png|svg|swf|ttf|woff|woff2|html|mp4|mov|m4v)' /path "/content/dam/*" }
/0203 { /type "allow" /method 'GET' /url "/screens/channels.json" }
## # Enable clientlibs proxy servlet
/0210 { /type "allow" /method "GET" /url "/etc.clientlibs/*" }
```

### 캐시 규칙 {#cache-rules}

* `publish_farm.any`/의 `/cache` 섹션에 `/statfileslevel "10"`을(를) 추가합니다.

  >[!NOTE]
  >이 캐시 규칙은 캐시 docroot에서 최대 10개 수준의 캐싱을 지원하며 모든 것을 무효화하는 대신 콘텐츠가 게시될 때 무효화됩니다. 콘텐츠 구조가 얼마나 깊이 설정되어 있는지 기준으로 이 수준을 변경할 수 있습니다.

* `publish_farm.any`의 `/invalidate` 섹션에 다음 내용을 추가하십시오.

  ```
  /0003 {
      /glob "*.json"
      /type "allow"
  }
  ```

* publish_farm.any 또는 `publish_farm.any`에서 포함된 파일의 `/cache`에 있는 `/rules` 섹션에 다음 규칙을 추가하십시오.

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
