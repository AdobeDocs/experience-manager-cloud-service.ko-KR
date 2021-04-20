---
product: adobe experience manager
description: Adobe Experience Manager을 Cloud Service 문서로 제공합니다.
git-repo: https://git.corp.adobe.com/AdobeDocs/experience-manager-cloud-service.ko-KR
index: y
type: Documentation
solution: Experience Manager
version: Cloud Service
cloud: Experience Cloud
translation-type: tm+mt
source-git-commit: 6908b5215dcbff0692d4e03dd1588ca5d34aeffe
workflow-type: tm+mt
source-wordcount: '91'
ht-degree: 7%

---


# 내부 사용을 위한 메타데이터

GitHub 저작 시스템의 메타데이터는 계층적이며 다음과 같은 선례 수준 증가를 정의합니다.

1. metadata.md
1. ToC
1. 기사

metadata.md 파일에 정의된 메타데이터는 전체 보고서에 적용되지만 ToC 및 아티클 수준에서 재정의할 수 있습니다. 메타데이터를 재정의하는 작업은 가능한 가장 낮은 수준에서 수행해야 합니다.

experience-manager-cloud-service.en repo의 메타데이터는 최소한으로 필요합니다.

metadata.md

* `product`
* `git-repo`
* `index`
* `solution-title`
* `solution-hub-url`
* `getting-started-title`
* `getting-started-url`
* `tutorials-title`
* `tutorials-url`

ToCs

* `sub-product`
* `user-guide-title`

기사

* `title`
* `description`
* `contentOwner` (아래에서 핵심 자산 컨텐츠에만 해당 `/help/assets`)
