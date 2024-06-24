---
title: 지속 GraphQL 쿼리 문제 해결
description: Adobe Experience Manager as a Cloud Service에서 지속되는 GraphQL 쿼리와 관련된 문제를 해결하는 방법을 알아봅니다.
feature: Headless, Content Fragments,GraphQL API
exl-id: 71bd1f68-ca96-4c78-a936-abed250ecec1
role: Admin, Developer
source-git-commit: bdf3e0896eee1b3aa6edfc481011f50407835014
workflow-type: tm+mt
source-wordcount: '363'
ht-degree: 0%

---

# 지속 GraphQL 쿼리 문제 해결 {#troubleshoot-persisted-graphql-queries}

다음 [작업 센터](/help/operations/actions-center.md) 다음을 포함: **GraphQL 지속 쿼리 오류** 경고. 즉, GraphQL 지속 쿼리 중 하나에서 오류가 발생할 때마다 알림을 받습니다.

이 페이지에서는 이러한 문제를 해결하고 해결할 수 있도록 다음 사항을 다룹니다 *가장 일반적이* 실패의 원인과 이를 수정하는 방법에 대한 단계.

## 콘텐츠 조각 모델 변경 {#changes-to-content-fragment-model}

GraphQL 지속 쿼리는 종종 기본 콘텐츠 조각 모델의 변경으로 인해 더 이상 사용되지 않는 GraphQL 유형을 기반으로 하는 경우 실패할 수 있습니다.

이러한 오류는 다양한 이유로 발생할 수 있습니다. 예를 들어 콘텐츠 조각 모델의 작성자가 다음과 같은 경우 (목록은 완전하지 않음)이 있습니다.

* 필드 제거 또는 이름 바꾸기
* 업데이트: **모델 유형** 조각 참조에 허용되는 모델을 정의합니다.
* 다른 모델에서 참조하는 모델 게시 취소

이러한 오류를 해결하려면 다음 중 하나를 수행해야 합니다.

* 콘텐츠 조각 모델에 대한 변경 사항을 수용하지 못하는 지속 쿼리를 업데이트합니다.
* 문제를 도입한 모델의 변경 사항을 되돌립니다.

## GraphQL 엔드포인트가 구성되지 않음 {#graphql-endpoint-not-configured}

지속 쿼리가 다음을 반환하는 경우 `404` 오류 코드 및 정보 `No suitable endpoint found`즉, AEM 환경에 GraphQL 엔드포인트가 구성되지 않습니다.

이 문제를 해결하려면 다음에서 끝점을 활성화하고 게시하는 단계를 따르십시오. [AEM에서 GraphQL 엔드포인트 관리](/help/headless/graphql-api/graphql-endpoint.md).

## GraphQL 지속 쿼리 URL에 경로가 누락됨 {#missing-path-query-url}

지속 쿼리가 `400` 오류 코드 및 정보 `Suffix: '/' does not contain a path`, GraphQL 서블릿이 경로 접미사 없이 호출되고 있습니다.

패턴은 다음과 같아야 합니다 `/graphql/execute.json/thePath`.

## IP 허용 목록으로 인해 차단됨 {#blocked-due-to-ip-allow-list}

이 경우 쿼리는 다음을 반환합니다. `405` 오류 코드.

이러한 오류는 GraphQL에만 해당되지 않습니다. 참조 자료 문서 [405 오류가 허용되지 않음](https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-20824).

## 디스패처에 의해 차단됨 {#blocked-dispatcher}

GraphQL 종단점이 다음을 반환하는 경우 `404` 을(를) 게시할 때 오류 발생 `POST` 는 GraphQL 쿼리가 dispatcher 수준에서 차단되고 끝점을 수동으로 활성화해야 함을 의미합니다.

이는 기본적으로 해당되지 않지만 사용자 지정 Dispatcher 구성으로 인해 이 문제가 발생할 수 있습니다. 아래에 자세히 보기 [Dispatcher - AEM Headless를 사용한 엔드포인트 구성](/help/headless/deployment/dispatcher.md).
