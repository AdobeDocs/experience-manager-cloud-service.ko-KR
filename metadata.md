---
product: adobe experience manager
description: Adobe Experience Manager as a Cloud Service 설명서
git-repo: https://git.corp.adobe.com/AdobeDocs/experience-manager-cloud-service.ko-KR
index: y
type: Documentation
solution: Experience Manager, Experience Manager as a Cloud Service
version: Cloud Service
feature-set: Experience Manager Assets,Experience Manager Sites,Experience Manager, Experience Manager Forms, Experience Manager Cloud Manager
cloud: Experience Cloud
source-git-commit: c19c15c4e71c8ead1c3cb05add052a8ffae79d0a
workflow-type: tm+mt
source-wordcount: '90'
ht-degree: 6%

---


# 내부 사용을 위한 메타데이터

GitHub 작성 시스템의 메타데이터는 계층적이며, 다음과 같이 증가하는 선례 수준으로 정의됩니다.

1. metadata.md
1. ToC
1. 기사

metadata.md 파일에 정의된 메타데이터는 전체 저장소에 적용되지만 ToC 및 문서 수준에서 재정의할 수 있습니다. 메타데이터를 재정의하는 작업은 가능한 가장 낮은 수준에서 수행해야 합니다.

experience-manager-cloud-service.en 보고서의 메타데이터는 최소값입니다.

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
* `contentOwner` ( `/help/assets`의 핵심 자산 컨텐츠에서만)
