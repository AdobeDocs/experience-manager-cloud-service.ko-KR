---
title: 콘텐츠 게재 플로우 개요
description: 콘텐츠 게재 데이터 흐름과 콘텐츠 게시 방법에 대해 자세히 알아보기
exl-id: fe42fb9e-cdf4-43e1-b688-7cecf4124fa5
feature: Dispatcher
role: Admin
source-git-commit: d58055cd0ed2451b5e8063fbb4e7269885d0787c
workflow-type: tm+mt
source-wordcount: '219'
ht-degree: 93%

---

# 콘텐츠 게재 플로우 {#content-delivery}

현재 페이지 세부 정보는 AEM as a Cloud Service에서 서비스 콘텐츠 게재를 게시합니다. 게시 서비스 콘텐츠 게재에는 다음이 포함됩니다.

* CDN
* AEM Dispatcher
* AEM 게시자

데이터 흐름은 다음과 같습니다.

1. URL은 브라우저에 추가됨
1. DNS에서 해당 도메인에 매핑된 CDN에 대한 요청
1. 콘텐츠가 CDN에 완전히 캐시된 경우 CDN은 브라우저에 콘텐츠 제공
1. 콘텐츠가 완전히 캐시되지 않은 경우, CDN은 Dispatcher를 호출함(역방향 프록시)
1. 콘텐츠가 Dispatcher에 완전히 캐시된 경우, Dispatcher는 CDN에 콘텐츠 제공
1. 콘텐츠가 완전히 캐시되지 않은 경우, Dispatcher는 AEM 게시를 호출함(역방향 프록시)
1. 콘텐츠는 헤더에 따라 캐시될 수도 있는 브라우저에 의해 렌더링됨

기본적으로 콘텐츠 유형 HTML/텍스트는 Dispatcher 계층에서 Dispatcher 캐시와 CDN이 모두 적용하는 임계값인 300초(5분) 후에 만료되도록 설정합니다. 게시 서비스를 다시 배포하는 동안 새 게시 노드가 트래픽을 허용하기 전에 Dispatcher 캐시를 지우고 난 다음 준비합니다.

다음 섹션에서는 콘텐츠 게재에 대해 자세히 설명합니다.
* [CDN 구성](/help/implementing/dispatcher/cdn.md)
* [캐싱](/help/implementing/dispatcher/caching.md)

작성자 서비스에서 게시 서비스로의 복제에 대한 자세한 내용은 [복제](/help/operations/replication.md)를 참조하십시오.
