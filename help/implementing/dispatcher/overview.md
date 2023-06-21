---
title: 콘텐츠 게재 플로우 개요
description: 콘텐츠 게재 플로우 개요
exl-id: fe42fb9e-cdf4-43e1-b688-7cecf4124fa5
source-git-commit: f0edd0e3deeba89dcbd2dc1a07859138b24e2220
workflow-type: tm+mt
source-wordcount: '207'
ht-degree: 48%

---

# 콘텐츠 게재 플로우 {#content-delivery}

현재 페이지 세부 정보는 AEM as a Cloud Service에서 서비스 콘텐츠 게재를 게시합니다. 게시 서비스 콘텐츠 게재에는 다음이 포함됩니다.

* CDN
* AEM 디스패처
* AEM 게시자

데이터 흐름은 다음과 같습니다.

1. URL은 브라우저에 추가됨
1. DNS에서 해당 도메인에 매핑된 CDN에 대한 요청
1. 콘텐츠가 CDN에 완전히 캐시된 경우 CDN은 브라우저에 콘텐츠 제공
1. 콘텐츠가 완전히 캐시되지 않은 경우 CDN이 Dispatcher를 호출(역방향 프록시)합니다
1. 콘텐츠가 Dispatcher에 완전히 캐시되는 경우 Dispatcher가 이를 CDN에 제공합니다
1. 콘텐츠가 완전히 캐시되지 않은 경우 Dispatcher는 AEM 게시로 (역방향 프록시)를 호출합니다
1. 콘텐츠는 헤더에 따라 캐시될 수도 있는 브라우저에 의해 렌더링됨

기본적으로 컨텐츠 유형 HTML/텍스트는 Dispatcher 레이어에서 Dispatcher 캐시와 CDN 모두가 준수하는 임계값인 300초(5분) 후에 만료되도록 설정됩니다. 게시 서비스를 재배포하는 동안 Dispatcher 캐시가 지워진 다음 새 게시 노드가 트래픽을 수락하기 전에 웜업됩니다.

다음 섹션에서는 콘텐츠 전달에 대해 자세히 설명합니다.
* [CDN 구성](/help/implementing/dispatcher/cdn.md)
* [캐싱](/help/implementing/dispatcher/caching.md)


작성자 서비스에서 게시 서비스로의 복제에 대한 정보는 [여기에서](/help/operations/replication.md) 확인할 수 있습니다.
