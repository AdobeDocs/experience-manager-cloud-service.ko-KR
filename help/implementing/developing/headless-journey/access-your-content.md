---
title: AEM 배달 API를 통해 콘텐츠에 액세스하는 방법
description: AEM 헤드리스 개발자 여정의 이 부분에서 GraphQL 쿼리를 사용하여 콘텐츠 조각 컨텐츠에 액세스하는 방법을 알아봅니다.
hide: true
hidefromtoc: true
index: false
translation-type: tm+mt
source-git-commit: 9fb18dbe60121f46dba1e11d4133e5264a6d538d
workflow-type: tm+mt
source-wordcount: '764'
ht-degree: 2%

---


# AEM 배달 API {#access-your-content}를 통해 콘텐츠에 액세스하는 방법

>[!CAUTION]
>
>진행 중인 작업 - 이 문서의 작성은 진행 중이며 완전한 또는 최종적인 것으로 해석되거나 제작 목적으로 사용되어서는 안 됩니다.

[AEM 헤드리스 개발자 여정의 이 부분에서 ](overview.md) GraphQL 쿼리를 사용하여 콘텐츠 조각의 콘텐츠에 액세스하는 방법을 알아봅니다.

## 지금까지 스토리 {#story-so-far}

AEM 헤드리스 여정의 이전 문서에서 [컨텐츠를 모델링하는 방법](model-your-content.md) AEM에서 데이터 모델링에 대한 기본 사항을 학습했으며 이제 다음을 수행해야 합니다.

* 컨텐츠 디자인에 대한 중요한 계획 고려 사항을 이해합니다.
* 통합 수준 요구 사항에 따라 헤드리스를 구현하는 단계를 이해합니다.
* 필요한 도구 및 AEM 구성을 설정합니다.
* 헤드리스 여정을 매끄럽게 만들고 콘텐츠를 효율적으로 생성하며 콘텐츠를 신속하게 전달하는 모범 사례를 소개합니다.

이 문서는 이러한 기본 사항을 기반으로 구축되므로 API를 통해 AEM의 기존 헤드리스 콘텐츠에 액세스하는 방법을 이해할 수 있습니다.

* **대상**:초급
* **목표**:AEM GraphQL 쿼리를 사용하여 컨텐츠 조각 컨텐츠에 액세스하는 방법을 알아봅니다.
   * GraphQL 소개
   * AEM GraphQL API 소개
   * AEM GraphQL API에 대한 세부 정보를 참조하십시오.
   * 몇 가지 샘플 쿼리를 살펴보면서 실제로 어떻게 작동하는지 확인할 수 있습니다.

AEM(Adobe Experience Manager)을 Cloud Service으로 사용하면 AEM GraphQL API와 함께 컨텐츠 조각을 사용하여 애플리케이션에서 사용할 수 있도록 구조화된 컨텐츠를 헤드윅(headly)에 전달할 수 있습니다. 단일 API 쿼리를 사용자 지정하는 기능을 사용하면 렌더링할 특정 컨텐츠를 검색하고 전달할 수 있습니다(단일 API 쿼리에 대한 응답).

>[!NOTE]
>AEM GraphQL API는 표준 GraphQL을 기반으로 사용자 정의된 구현입니다.

## GraphQL - 소개 {#graphql-introduction}

GraphQL:

* &quot;*...API에 대한 쿼리 언어 및 기존 데이터를 사용한 쿼리를 충족하는 런타임입니다.*&quot;

   *GraphQL*&#x200B;을 참조하십시오.

### GraphQL - 유형 {#graphql-types}

### GraphQL - 스키마 {#graphql-schemas}

### GraphQL - 쿼리 {#graphql-queries}

## AEM 및 GraphQL {#aem-graphql}

GraphQL은 AEM의 다양한 위치에 사용됩니다.

* 상거래
   * 자리 표시자
* 콘텐츠 조각
   * 이 사용 사례용으로 사용자 지정된 API가 개발되었습니다.
   * AEM GraphQL API입니다.

## AEM GraphQL API {#aem-graphql-api}

Adobe Experience as a Cloud Experience의 경우, 표준 GraphQL API의 맞춤형 구현이 개발되었습니다.

AEM GraphQL API를 사용하면 컨텐츠 조각에 대해 (복잡한) 쿼리를 수행할 수 있습니다.각 쿼리는 특정 모델 유형에 따라 달라집니다. 그런 다음 반환된 컨텐츠를 애플리케이션에서 사용할 수 있습니다.

>[!NOTE]
>
>AEM GraphQL API 구현은 GraphQL Java 라이브러리를 기반으로 합니다.

### AEM GraphQL API 및 컨텐츠 조각 {#aem-graphql-content-fragments}

## AEM GraphQL API {#content-fragments-use-with-aem-graphql-api}에 사용할 컨텐츠 조각

컨텐츠 조각은 다음과 같이 AEM 쿼리에 대한 GraphQL의 기초로 사용할 수 있습니다.

* 페이지와 독립된 컨텐츠를 디자인, 제작, 조정 및 게시할 수 있습니다.
* 컨텐츠 조각 모델은 정의된 데이터 유형을 통해 필요한 구조를 제공합니다.
* 모델을 정의할 때 사용할 수 있는 조각 참조를 사용하여 구조의 추가 레이어를 정의할 수 있습니다.

### 콘텐츠 조각 {#content-fragments}

콘텐츠 조각:

* 구조화된 컨텐츠를 포함합니다.

* 결과 조각의 구조를 미리 정의하는 컨텐츠 조각 모델을 기반으로 합니다.

### 컨텐츠 조각 모델 {#content-fragments-models}

다음 컨텐츠 조각 모델:

* 스키마를 생성하는 데 사용됩니다(**Enabled**).

* GraphQL에 필요한 데이터 유형과 필드를 제공합니다. 응용 프로그램이 가능한 것만 요청하고 예상대로 수신하도록 합니다.

* 데이터 유형 **조각 참조**&#x200B;는 모델에서 다른 컨텐츠 조각을 참조하기 위해 사용할 수 있으므로 추가 구조 수준을 활용할 수 있습니다.

### 조각 참조 {#fragment-references}

**조각 참조**:

* GraphQL과 함께 사용하는 경우에 특히 유용합니다.

* 컨텐츠 조각 모델을 정의할 때 사용할 수 있는 특정 데이터 유형입니다.

* 특정 컨텐츠 조각 모델에 따라 다른 조각을 참조합니다.

* 구조화된 데이터를 검색할 수 있습니다.

   * **다중 피드**&#x200B;로 정의되면 여러 하위 조각을 기본 조각의 참조(검색)할 수 있습니다.

### JSON 미리 보기 {#json-preview}

컨텐츠 조각 모델을 디자인하고 개발하는 데 도움이 되도록 [JSON 출력](/help/assets/content-fragments/content-fragments-json-preview.md)을 미리 볼 수 있습니다.

## 다음 {#whats-next} 소개

[REST API를 사용하여 컨텐츠 조각에 액세스하고 업데이트하는 방법을 알아봅니다](/help/implementing/developing/headless-journey/update-your-content.md).

## 추가 리소스 {#additional-resources}

* [AEM 헤드리스 시작하기](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/graphql/overview.html)  - 데이터 모델링 및 GraphQL을 비롯한 AEM 헤드리스 기능 사용에 대한 개요를 제공하는 짧은 비디오 자습서 시리즈입니다.
* [GraphQL.org](https://graphql.org)
   * [스키마](https://graphql.org/learn/schema/)
   * [GraphQL Java 라이브러리](https://graphql.org/code/#java)
* [컨텐츠 조각에 사용할 AEM GraphQL API](/help/assets/content-fragments/graphql-api-content-fragments.md)
   * [AEM에서 GraphQL 사용 방법 학습 - 샘플 컨텐츠 및 쿼리](/help/assets/content-fragments/content-fragments-graphql-samples.md)
   * [컨텐츠 조각에 대한 원격 AEM GraphQL 쿼리 인증](/help/assets/content-fragments/graphql-authentication-content-fragments.md)
* [콘텐츠 조각을 사용한 작업](/help/assets/content-fragments/content-fragments.md)
   * [콘텐츠 조각 모델](/help/assets/content-fragments/content-fragments-models.md)
   * [JSON 출력](/help/assets/content-fragments/content-fragments-json-preview.md)
