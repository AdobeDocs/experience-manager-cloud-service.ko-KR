---
title: AEM에서 GraphQL 엔드포인트 관리
description: 헤드리스 컨텐츠 전달을 위해 Adobe Experience Manager as a Cloud Service에서 GraphQL 종단점을 관리하는 방법을 알아봅니다.
feature: Content Fragments,GraphQL API
source-git-commit: 4e37db128aa31d6e8e950be0d077eae921a27468
workflow-type: tm+mt
source-wordcount: '515'
ht-degree: 8%

---


# AEM에서 GraphQL 엔드포인트 관리 {#graphql-aem-endpoint}

끝점은 AEM용 GraphQL에 액세스하는 데 사용되는 경로입니다. 이 경로 사용(또는 앱)은 다음 작업을 수행할 수 있습니다.

* GraphQL 스키마 액세스,
* GraphQL 쿼리 전송,
* 응답을 받습니다(GraphQL 쿼리에 대한).

AEM에는 두 가지 유형의 엔드포인트가 있습니다.

* 전역
   * 모든 사이트에서 사용할 수 있습니다.
   * 이 종단점은 모든 사이트 구성(에 정의됨)의 모든 컨텐츠 조각 모델을 사용할 수 있습니다 [구성 브라우저](/help/assets/content-fragments/content-fragments-configuration-browser.md#enable-content-fragment-functionality-in-configuration-browser)).
   * 사이트 구성 간에 공유해야 하는 컨텐츠 조각 모델이 있는 경우 글로벌 사이트 구성 아래에 만들어야 합니다.
* 사이트 구성:
   * 에 정의된 대로 Sites 구성에 해당합니다 [구성 브라우저](/help/assets/content-fragments/content-fragments-configuration-browser.md#enable-content-fragment-functionality-in-configuration-browser).
   * 지정된 사이트/프로젝트에 특정합니다.
   * 사이트 구성 특정 종단점은 전역 사이트 구성의 컨텐츠 조각 모델과 함께 해당 특정 사이트 구성의 컨텐츠 조각 모델을 사용합니다.

>[!CAUTION]
>
>컨텐츠 조각 편집기를 사용하면 한 사이트 구성의 컨텐츠 조각이 다른 사이트 구성의 컨텐츠 조각(정책을 통해)을 참조할 수 있습니다.
>
>이러한 경우 사이트 구성 특정 종단점을 사용하여 일부 컨텐츠를 검색할 수 있는 것은 아닙니다.
>
>컨텐츠 작성자는 이 시나리오를 제어해야 합니다. 예를 들어, 글로벌 사이트 구성에 공유 컨텐츠 조각 모델을 적용하는 것이 유용할 수 있습니다.

AEM용 GraphQL 글로벌 끝점의 저장소 경로는 다음과 같습니다.

`/content/cq:graphql/global/endpoint`

요청 URL에서 다음 경로를 사용할 수 있는 앱의 경우:

`/content/_cq_graphql/global/endpoint.json`

GraphQL for AEM에 대해 끝점을 활성화하려면 다음을 수행해야 합니다.

* [GraphQL 끝점 활성화](#enabling-graphql-endpoint)
* [GraphQL 끝점 게시](#publishing-graphql-endpoint)

## GraphQL 끝점 활성화 {#enabling-graphql-endpoint}

GraphQL 종단점을 사용하려면 먼저 적절한 구성이 있어야 합니다. 자세한 내용은 [컨텐츠 조각 - 구성 브라우저](/help/assets/content-fragments/content-fragments-configuration-browser.md).

>[!CAUTION]
>
>[컨텐츠 조각 모델 사용이 활성화되지 않은](/help/assets/content-fragments/content-fragments-configuration-browser.md) 경우 **만들기** 옵션을 사용할 수 없습니다.

해당 끝점을 활성화하려면

1. 다음으로 이동 **도구**, **자산**&#x200B;를 선택하고 을 선택합니다. **GraphQL**.
1. **만들기**&#x200B;를 선택합니다.
1. 다음 **새 GraphQL 끝점 만들기** 대화 상자가 열립니다. 여기에서 다음을 지정할 수 있습니다.
   * **이름**: 끝점의 이름; 텍스트를 입력할 수 있습니다.
   * **GraphQL 스키마에서 제공되는 스키마 사용**: 드롭다운을 사용하여 필요한 사이트/프로젝트를 선택합니다.

   >[!NOTE]
   >
   >대화 상자에 다음 경고가 표시됩니다.
   >
   >* *GraphQL 엔드포인트는 신중하게 관리하지 않을 경우 데이터 보안 및 성능 문제를 초래할 수 있습니다. 엔드포인트를 만든 후 적절한 사용 권한을 설정했는지 확인하십시오.*


1. 다음으로 확인 **만들기**.
1. 다음 **다음 단계** 대화 상자에서는 새로 만든 끝점에 적절한 권한이 있는지 확인할 수 있도록 보안 콘솔에 직접 링크를 제공합니다.

   >[!CAUTION]
   >
   >엔드포인트는 모든 사람이 액세스할 수 있습니다. GraphQL 쿼리는 서버에 많은 로드를 부과할 수 있으므로 특히 게시 인스턴스에서 보안에 문제가 발생할 수 있습니다.
   >
   >사용 사례에 적합한 ACL을 엔드포인트에서 설정할 수 있습니다.

## GraphQL 끝점 게시 {#publishing-graphql-endpoint}

새 끝점을 선택하고 **게시** 모든 환경에서 완전히 사용할 수 있도록 합니다.

>[!CAUTION]
>
>엔드포인트는 모든 사람이 액세스할 수 있습니다.
>
>GraphQL 쿼리는 서버에 많은 로드를 부과할 수 있으므로 게시 인스턴스에서 이 기능은 보안 문제가 될 수 있습니다.
>
>다음을 설정해야 합니다. [사용 사례에 적합한 ACL](/help/headless/security/permissions.md) 를 가리키도록 업데이트하는 것이 좋습니다.