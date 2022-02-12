---
title: AEM에서 GraphiQL IDE 사용
description: Adobe Experience Manager에서 GraphiQL IDE를 사용하는 방법을 알아봅니다.
feature: Content Fragments,GraphQL API
source-git-commit: c4490690edb1ec0e2a6b8cca724fe9c290650bc8
workflow-type: tm+mt
source-wordcount: '226'
ht-degree: 3%

---


# GraphiQL IDE 사용 {#graphiql-ide}

표준 구현 [GraphiQL](https://graphql.org/learn/serving-over-http/#graphiql) AEM GraphQL에서 IDE를 사용할 수 있습니다. 다음 중 하나일 수 있습니다 [AEM에 설치](#installing-graphiql-ide).

>[!NOTE]
>
>GraphiQL이 전역 끝점에 바인딩되어 있으며 특정 사이트 구성에 대한 다른 끝점에서는 작동하지 않습니다.

GraphiQL 도구를 사용하여 쿼리를 직접 입력, 테스트 및 디버그할 수 있습니다. GraphiQL도 설명서에 쉽게 액세스할 수 있으므로 사용 가능한 방법을 쉽게 파악하고 이해할 수 있습니다.

예:

* `http://localhost:4502/content/graphiql.html`

여기에는 내역 및 온라인 설명서와 함께 구문 강조, 자동 완료, 자동 제안 등의 기능이 제공됩니다.

![GraphiQL 인터페이스](assets/cfm-graphiql-interface.png "GraphiQL 인터페이스")

## AEM GraphiQL IDE 설치 {#installing-graphiql-ide}

GraphiQL IDE는 개발 툴이며 개발이나 로컬 인스턴스와 같은 하위 수준 환경에서만 필요합니다. 따라서 AEM 프로젝트에는 포함되지 않지만, 임시로 설치할 수 있는 별도의 패키지로 제공됩니다.

1. 로 이동합니다 **[소프트웨어 배포 포털](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html)** > **AEM as a Cloud Service**.
1. &quot;GraphiQL&quot;을 검색합니다(를). **i** in **GraphiQL**.
1. 최신 다운로드 **GraphiQL 컨텐츠 패키지 v.x.x.x**
1. 에서 **AEM 시작** 메뉴 탐색 **도구** > **배포** > **패키지**.
1. 클릭 **패키지 업로드** 이전 단계에서 다운로드한 패키지를 선택합니다. 클릭 **설치** 를 클릭하여 패키지를 설치합니다.

