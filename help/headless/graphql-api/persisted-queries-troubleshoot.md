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

[작업 센터](/help/operations/actions-center.md)에 **GraphQL 지속 쿼리 오류** 경고가 포함되어 있습니다. 즉, GraphQL 지속 쿼리 중 하나에서 오류가 발생할 때마다 알림을 받습니다.

이러한 문제를 해결하고 해결하는 데 도움이 되도록 이 페이지에서는 *가장 일반적인* 오류 원인과 해결 방법에 대한 단계를 다룹니다.

## 콘텐츠 조각 모델 변경 {#changes-to-content-fragment-model}

GraphQL 지속 쿼리는 종종 기본 콘텐츠 조각 모델의 변경으로 인해 더 이상 사용되지 않는 GraphQL 유형을 기반으로 하는 경우 실패할 수 있습니다.

이러한 오류는 다양한 이유로 발생할 수 있습니다. 예를 들어 콘텐츠 조각 모델의 작성자가 다음과 같은 경우 (목록은 완전하지 않음)이 있습니다.

* 필드 제거 또는 이름 바꾸기
* 조각 참조에 허용된 모델을 정의하는 **모델 형식**&#x200B;을(를) 업데이트합니다.
* 다른 모델에서 참조하는 모델 게시 취소

이러한 오류를 해결하려면 다음 중 하나를 수행해야 합니다.

* 콘텐츠 조각 모델에 대한 변경 사항을 수용하지 못하는 지속 쿼리를 업데이트합니다.
* 문제를 도입한 모델의 변경 사항을 되돌립니다.

## GraphQL 엔드포인트가 구성되지 않음 {#graphql-endpoint-not-configured}

지속 쿼리가 `No suitable endpoint found` 정보와 함께 `404` 오류 코드를 반환하면 AEM 환경에 GraphQL 끝점이 구성되지 않은 것입니다.

이 문제를 해결하려면 [AEM의 GraphQL 끝점 관리](/help/headless/graphql-api/graphql-endpoint.md)에서 끝점을 활성화하고 게시하는 단계를 따르십시오.

## GraphQL 지속 쿼리 URL에 경로가 누락됨 {#missing-path-query-url}

지속 쿼리가 `Suffix: '/' does not contain a path` 정보가 있는 `400` 오류 코드를 반환하는 경우 경로 접미사 없이 GraphQL 서블릿이 호출됩니다.

패턴은 `/graphql/execute.json/thePath`이어야 합니다.

## IP 허용 목록으로 인해 차단됨 {#blocked-due-to-ip-allow-list}

이 경우 쿼리는 `405` 오류 코드를 반환합니다.

이러한 오류는 GraphQL에만 해당되지 않습니다. 참조 자료 문서 [405 오류 허용 안 함](https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-20824)을(를) 참조하십시오.

## 디스패처에 의해 차단됨 {#blocked-dispatcher}

GraphQL 끝점이 `POST` 요청에 대해 게시할 때 `404` 오류를 반환하는 경우 GraphQL 쿼리가 Dispatcher 수준에서 차단되며 끝점을 수동으로 활성화해야 합니다.

이는 기본적으로 해당되지 않지만 사용자 지정 Dispatcher 구성으로 인해 이 문제가 발생할 수 있습니다. [Dispatcher - AEM Headless를 사용한 끝점 구성](/help/headless/deployment/dispatcher.md)에서 자세히 알아보십시오.
