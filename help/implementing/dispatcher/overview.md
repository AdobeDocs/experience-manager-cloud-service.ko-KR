---
title: 컨텐츠 전달 흐름 개요
description: 컨텐츠 전달 흐름 개요
exl-id: fe42fb9e-cdf4-43e1-b688-7cecf4124fa5
source-git-commit: 60fc1b8f93c93ca427507dbe56511342f285e6bc
workflow-type: tm+mt
source-wordcount: '207'
ht-degree: 1%

---

# 콘텐츠 전송 플로우 {#content-delivery}

현재 페이지 세부 사항은 AEM as a Cloud Service에서 서비스 컨텐츠 전달을 게시합니다. 게시 서비스 컨텐츠 게재에는 다음이 포함됩니다.

* CDN
* AEM Dispatcher
* AEM 게시

데이터 흐름은 다음과 같습니다.

1. URL이 브라우저에 추가됩니다
1. DNS에 매핑된 CDN에 대한 요청
1. 컨텐츠가 CDN에 완전히 캐시되면 CDN은 브라우저에 제공됩니다
1. 컨텐츠가 완전히 캐시되지 않으면 CDN은 디스패처에 대해 아웃(역방향 프록시)을 호출합니다
1. 컨텐츠가 Dispatcher에 완전히 캐시되면 Dispatcher가 CDN에 제공합니다
1. 컨텐츠가 완전히 캐시되지 않으면 디스패처가 AEM 게시으로 출력(역방향 프록시)을 호출합니다
1. 컨텐츠는 브라우저에 의해 렌더링되며, 브라우저에 따라 캐싱할 수 있습니다

기본적으로 컨텐츠 유형 HTML/텍스트는 디스패처 캐시와 CDN이 모두 준수하는 임계값인 디스패처 레이어에서 300초(5분) 후에 만료되도록 설정됩니다. 게시 서비스를 다시 배포하는 동안 디스패처 캐시가 지워지고 후에 새 게시 노드가 트래픽을 허용하기 전에 데워집니다.

다음 섹션에서는 컨텐츠 전달에 대해 더 자세히 설명합니다.
* [CDN 구성](/help/implementing/dispatcher/cdn.md)
* [캐싱](/help/implementing/dispatcher/caching.md)


작성자 서비스에서 게시 서비스로의 복제에 대한 정보를 사용할 수 있습니다 [여기](/help/operations/replication.md).
