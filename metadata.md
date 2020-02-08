---
product: adobe experience manager
git-repo: https://github.com/AdobeDocs/experience-manager-cloud-service.en
index: y
solution-title: 클라우드 서비스로서의 Adobe Experience Manager
solution-hub-url: https://docs.adobe.com/content/help/en/experience-manager-cloud-service/landing/home.html
getting-started-title: 시작하기
getting-started-url: https://docs.adobe.com/content/help/en/experience-manager-cloud-service/core-concepts/home.html
tutorials-title: 튜토리얼
tutorials-url: https://docs.adobe.com/content/help/en/experience-manager-learn/cloud-service/overview.html
translation-type: tm+mt
source-git-commit: 98988a1f8f436e836a8023c2a4087560dd37aef2

---


# 내부용 메타데이터

GitHub 저작 시스템의 메타데이터는 계층적이며 다음과 같은 선례 수준을 증가시킵니다.

1. metadata.md
1. ToC
1. 기사

metadata.md 파일에 정의된 메타데이터는 전체 보고서에 적용되지만 ToC 및 아티클 수준에서 재정의할 수 있습니다. 메타데이터를 재정의하는 작업은 가능한 가장 낮은 수준에서 수행해야 합니다.

Adobe Experience-manager-cloud-service.en repo의 메타데이터는 최소한으로 필요합니다.

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
* `contentOwner` (핵심 자산 컨텐츠에만 해당 `/help/assets`)

메타데이터에 대한 자세한 내용은 [내부 작성 안내서를 참조하십시오.](https://docs.adobe.com/help/en/collaborative-doc-instructions/collaboration-guide/markdown/metadata.html#solution-metadata)