---
product: adobe experience manager
description: AEM AaCS 설명서 페이지에 필요한 메타데이터입니다.
git-repo: https://git.corp.adobe.com/AdobeDocs/experience-manager-cloud-service.ko-KR
index: y
type: 설명서
solution-title: Adobe Experience Manager as a Cloud Service
solution-hub-url: https://experienceleague.adobe.com/docs/experience-manager-cloud-service/landing/home.html
getting-started-title: 시작하기
getting-started-url: https://experienceleague.adobe.com/docs/experience-manager-cloud-service/overview/home.html
tutorials-title: 자습서
tutorials-url: https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/overview.html
translation-type: tm+mt
source-git-commit: 28de20620a7cc8a3df231abacde4b3daa98cbcdb
workflow-type: tm+mt
source-wordcount: '120'
ht-degree: 19%

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
