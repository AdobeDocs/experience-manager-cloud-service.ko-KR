---
title: GraphQL 지속 쿼리 문제 해결
description: Adobe Experience Manager as a Cloud Service에서 지속적으로 발생하는 GraphQL 쿼리 관련 문제를 해결하는 방법을 알아봅니다.
feature: Headless, Content Fragments,GraphQL API
exl-id: 71bd1f68-ca96-4c78-a936-abed250ecec1
role: Admin, Developer
source-git-commit: bdf3e0896eee1b3aa6edfc481011f50407835014
workflow-type: ht
source-wordcount: '363'
ht-degree: 100%

---

# GraphQL 지속 쿼리 문제 해결 {#troubleshoot-persisted-graphql-queries}

[액션 센터](/help/operations/actions-center.md)에는 **GraphQL 지속 쿼리 오류** 경고가 포함되어 있습니다. 따라서 GraphQL 지속 쿼리 중 하나에서 오류가 발생할 때마다 알림을 받게 됩니다.

이 페이지에서는 이러한 문제를 해결하는 데 도움이 되도록 *가장 일반적인* 오류 원인과 오류 교정 방법에 대한 단계를 다룹니다.

## 콘텐츠 조각 모델 변경 {#changes-to-content-fragment-model}

GraphQL 지속 쿼리는 기본 콘텐츠 조각 모델의 변경으로 인해 더 이상 사용되지 않는 GraphQL 유형을 기반으로 하는 경우 실패할 수 있습니다.

이러한 오류는 다양한 이유로 발생할 수 있습니다. 예시로는 콘텐츠 조각 모델 작성자가 다음과 같은 작업을 수행하는 경우 등이 있습니다.

* 필드를 제거하거나 이름을 변경
* 조각 참조에 허용되는 모델을 정의하는 **모델 유형**&#x200B;을 업데이트
* 다른 모델에서 참조하는 모델의 게시를 취소

이러한 오류를 해결하려면 다음 중 하나를 수행해야 합니다.

* 콘텐츠 조각 모델에 대한 변경 사항을 수용하지 못하는 지속 쿼리를 업데이트
* 문제를 일으킨 모델의 변경 사항을 되돌리기

## GraphQL 엔드포인트 미구성 {#graphql-endpoint-not-configured}

지속 쿼리가 `404` 오류 코드와 `No suitable endpoint found` 정보를 함께 반환하는 경우 AEM 환경에서 GraphQL 엔드포인트가 구성되지 않았음을 의미합니다.

이를 해결하려면 [AEM에서 GraphQL 엔드포인트 관리](/help/headless/graphql-api/graphql-endpoint.md)에서 엔드포인트를 활성화하고 게시하는 단계를 따릅니다.

## GraphQL 지속형 쿼리 URL 내 경로 누락 {#missing-path-query-url}

지속 쿼리가 `400` 오류 코드와 `Suffix: '/' does not contain a path` 정보를 반환하는 경우 GraphQL 서블릿이 경로 접미사 없이 호출됩니다.

패턴은 `/graphql/execute.json/thePath`이어야 합니다.

## IP 허용 목록으로 인한 차단 {#blocked-due-to-ip-allow-list}

이 경우 쿼리는 `405` 오류 코드를 반환합니다.

이러한 오류는 GraphQL에만 국한된 것이 아닙니다. KB 문서 [405 오류 허용되지 않음](https://experienceleague.adobe.com/ko/docs/experience-cloud-kcs/kbarticles/ka-20824)을 참조하십시오.

## Dispatcher에 의한 차단 {#blocked-dispatcher}

GraphQL 엔드포인트가 게시 시점에 `POST` 요청에 대한 `404` 오류를 반환하는 경우, 이는 GraphQL 쿼리가 Dispatcher 레벨에서 차단되었으며 엔드포인트를 수동으로 활성화해야 함을 의미합니다.

이러한 경우는 기본적으로 발생하지 않는 것이 맞으나, 사용자 정의 Dispatcher 구성으로 인해 발생할 수 있습니다. [Dispatcher - AEM Headless를 통한 엔드포인트 구성](/help/headless/deployment/dispatcher.md)에서 자세한 내용을 확인하십시오.
