---
title: AEM Assets API를 통해 컨텐츠를 업데이트하는 방법
description: AEM 헤드리스 개발자 여정의 이 부분에서 REST API를 사용하여 콘텐츠 조각에 액세스하고 업데이트하는 방법을 알아봅니다.
hide: true
hidefromtoc: true
index: false
translation-type: tm+mt
source-git-commit: 6097cb8961f604ec2d3f5f6d602c927efc7344d5
workflow-type: tm+mt
source-wordcount: '319'
ht-degree: 1%

---


# AEM Assets API {#update-your-content}를 통해 컨텐츠를 업데이트하는 방법

>[!CAUTION]
>
>진행 중인 작업 - 이 문서의 작성은 진행 중이며 완전한 또는 최종적인 것으로 해석되거나 제작 목적으로 사용되어서는 안 됩니다.

[AEM 헤드리스 개발자 여정의 이 부분에서](#overview.md) REST API를 사용하여 콘텐츠 조각에 액세스하고 업데이트하는 방법을 알아봅니다.

## 지금까지 스토리 {#story-so-far}

AEM 헤드리스 여정의 이전 문서에서, [AEM 전달 API를 통해 콘텐츠에 액세스하는 방법](access-your-content.md) API를 통해 AEM에서 헤드리스 컨텐츠에 액세스하는 방법을 배웠으므로 이제 다음을 수행해야 합니다.

* GraphQL의 정의와 AEM GraphQL API의 작동 방식을 이해합니다.
* 몇 가지 실용적인 샘플 쿼리를 파악합니다.

이 문서는 이러한 기본 사항을 기반으로 구축되므로 API를 통해 AEM에서 헤드리스 콘텐츠를 업데이트하는 방법을 이해할 수 있습니다.

## 목표 {#objective}

* **대상**:고급
* **목표**:REST API를 사용하여 컨텐츠 조각의 컨텐츠에 액세스하고 업데이트하는 방법을 알아봅니다.
   * AEM Assets HTTP API를 소개합니다.
   * API에서 컨텐츠 조각 지원 소개 및 토론
   * API에 대한 세부 사항을 설명합니다.
   * 샘플 코드를 통해 실제 작동 방식을 확인할 수 있습니다.

## 다음 {#whats-next} 소개

AEM 헤드리스 개발자 여정의 이 부분을 완료하셨다면 다음을 수행해야 합니다.

* AEM Assets HTTP API를 이해합니다.
* API에서 컨텐츠 조각이 지원되는 방식을 이해합니다.
* 샘플 코드에 대한 경험과 API가 실제로 어떻게 작동하는지 알고 있습니다.

AEM 헤드리스 프로젝트를 사용하고 라이브할 준비를 하는 방법을 배울 수 있는 AEM Headless](put-it-all-together.md) 문서의 [모두 함께 놓는 방법 - 앱과 귀하의 컨텐츠를 차례로 검토하여 AEM 헤드리스 여정을 계속 진행해야 합니다.

## 추가 리소스 {#additional-resources}

* [자산 HTTP API](/help/assets/mac-api-assets.md)
* [컨텐츠 조각 REST API](/help/assets/content-fragments/assets-api-content-fragments.md)
