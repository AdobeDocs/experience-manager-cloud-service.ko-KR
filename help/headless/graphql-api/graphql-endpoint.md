---
title: AEM에서 GraphQL 끝점 관리
description: Headless 콘텐츠 전달용 Adobe Experience Manager as a Cloud Service에서 GraphQL 끝점을 관리하는 방법을 알아봅니다.
feature: Content Fragments,GraphQL API
source-git-commit: 4e37db128aa31d6e8e950be0d077eae921a27468
workflow-type: ht
source-wordcount: '515'
ht-degree: 100%

---


# AEM에서 GraphQL 끝점 관리 {#graphql-aem-endpoint}

끝점은 AEM용 GraphQL에 액세스하는 데 사용되는 경로입니다. 이 경로를 사용하여 사용자(또는 앱)는 다음을 수행할 수 있습니다.

* GraphQL 스키마에 액세스,
* GraphQL 쿼리 보내기,
* (GraphQL 쿼리에 대한) 응답 받기.

AEM에는 두 가지 유형의 끝점이 있습니다.

* 전역
   * 모든 사이트에서 사용할 수 있습니다.
   * 이 끝점은 모든 Sites 구성의 모든 콘텐츠 조각 모델을 사용할 수 있습니다([구성 브라우저](/help/assets/content-fragments/content-fragments-configuration-browser.md#enable-content-fragment-functionality-in-configuration-browser)에 정의됨).
   * Sites 구성 간에 공유해야 하는 콘텐츠 조각 모델이 있는 경우 전역 Sites 구성에서 생성해야 합니다.
* Sites 구성:
   * [구성 브라우저](/help/assets/content-fragments/content-fragments-configuration-browser.md#enable-content-fragment-functionality-in-configuration-browser)에 정의된 Sites 구성에 해당합니다.
   * 지정된 사이트/프로젝트에만 해당됩니다.
   * Sites 구성 특정 끝점은 해당 특정 Sites 구성의 콘텐츠 조각 모델을 전역 Sites 구성의 콘텐츠 조각 모델과 함께 사용합니다.

>[!CAUTION]
>
>콘텐츠 조각 편집기는 한 Sites 구성의 콘텐츠 조각이 다른 Sites 구성의 콘텐츠 조각을 참조하도록 허용할 수 있습니다(정책을 통해).
>
>이러한 경우 Sites 구성 특정 끝점을 사용하여 모든 콘텐츠를 검색할 수 있는 것은 아닙니다.
>
>콘텐츠 작성자가 이 시나리오를 제어해야 합니다. 예를 들어 공유 콘텐츠 조각 모델을 전역 Sites 구성 아래에 두는 것이 유용할 수 있습니다.

AEM용 GraphQL 전역 끝점의 저장소 경로는 다음과 같습니다.

`/content/cq:graphql/global/endpoint`

앱이 요청 URL에서 다음 경로를 사용할 수 있는 경우:

`/content/_cq_graphql/global/endpoint.json`

AEM용 GraphQL의 끝점을 활성화하려면 다음을 수행해야 합니다.

* [GraphQL 끝점 활성화](#enabling-graphql-endpoint)
* [GraphQL 끝점 게시](#publishing-graphql-endpoint)

## GraphQL 끝점 활성화하기 {#enabling-graphql-endpoint}

GraphQL 끝점을 활성화하려면 먼저 적절한 구성이 필요합니다. [콘텐츠 조각 - 구성 브라우저](/help/assets/content-fragments/content-fragments-configuration-browser.md)를 참조하십시오.

>[!CAUTION]
>
>[콘텐츠 조각 모델 사용이 활성화되지 않은](/help/assets/content-fragments/content-fragments-configuration-browser.md) 경우 **만들기** 옵션을 사용할 수 없습니다.

해당 끝점을 활성화하려면 다음을 수행하십시오.

1. **도구**, **에셋**&#x200B;으로 이동한 다음 **GraphQL**&#x200B;을 선택합니다.
1. **만들기**&#x200B;를 선택합니다.
1. **새 GraphQL 끝점 만들기** 대화 상자가 열립니다. 여기에서 다음을 지정할 수 있습니다.
   * **이름**: 끝점의 이름입니다. 어떤 텍스트든 입력할 수 있습니다.
   * **다음에서 제공하는 GraphQL 스키마 사용**: 드롭다운을 사용하여 필요한 사이트/프로젝트를 선택합니다.

   >[!NOTE]
   >
   >다음 경고가 대화 상자에 표시됩니다.
   >
   >* *GraphQL 엔드포인트는 신중하게 관리하지 않을 경우 데이터 보안 및 성능 문제를 초래할 수 있습니다. 엔드포인트를 만든 후 적절한 사용 권한을 설정했는지 확인하십시오.*


1. **만들기**&#x200B;를 사용하여 확인합니다.
1. **다음 단계** 대화 상자는 보안 콘솔에 대한 직접 링크를 제공하므로 새로 생성된 끝점에 적절한 권한이 있는지 확인할 수 있습니다.

   >[!CAUTION]
   >
   >끝점은 모든 사용자가 액세스할 수 있습니다. 특히 게시 인스턴스에서, GraphQL 쿼리가 과도한 부하를 줄 수 있으므로 보안 문제가 발생할 수 있습니다.
   >
   >끝점에 사용 사례에 적합한 ACL을 설정할 수 있습니다.

## GraphQL 끝점 게시하기 {#publishing-graphql-endpoint}

새 끝점을 선택하고 **게시**&#x200B;를 선택하여 모든 환경에서 완전히 사용할 수 있도록 합니다.

>[!CAUTION]
>
>끝점은 모든 사용자가 액세스할 수 있습니다.
>
>게시 인스턴스에서 GraphQL 쿼리가 서버에 과부하를 줄 수 있으므로 보안 문제가 발생할 수 있습니다.
>
>끝점에 [사용 사례에 적합한 ACL](/help/headless/security/permissions.md)을 설정해야 합니다.