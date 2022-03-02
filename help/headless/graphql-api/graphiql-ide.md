---
title: AEM에서 GraphiQL IDE 사용
description: Adobe Experience Manager에서 GraphiQL IDE를 사용하는 방법을 알아봅니다.
feature: Content Fragments,GraphQL API
source-git-commit: c4490690edb1ec0e2a6b8cca724fe9c290650bc8
workflow-type: ht
source-wordcount: '226'
ht-degree: 100%

---


# GraphiQL IDE 사용 {#graphiql-ide}

표준 [GraphiQL](https://graphql.org/learn/serving-over-http/#graphiql) IDE의 구현은 AEM GraphQL과 함께 사용할 수 있습니다. [AEM으로 설치](#installing-graphiql-ide)할 수 있습니다.

>[!NOTE]
>
>GraphiQL은 전역 끝점에 바인딩되어 있으며 특정 Sites 구성에 대한 다른 끝점에서는 작동하지 않습니다.

GraphiQL 도구를 사용하면 쿼리를 직접 입력하고 테스트하고 디버그할 수 있습니다. 또한 GraphiQL은 설명서에 쉽게 액세스할 수 있어 사용 가능한 방법을 쉽게 배우고 이해할 수 있습니다.

예:

* `http://localhost:4502/content/graphiql.html`

기록 및 온라인 설명서와 함께 구문 강조, 자동 완성, 자동 제안과 같은 기능을 제공합니다.

![GraphiQL 인터페이스](assets/cfm-graphiql-interface.png "GraphiQL 인터페이스")

## AEM GraphiQL IDE 설치 {#installing-graphiql-ide}

GraphiQL IDE는 개발 도구이며 개발 또는 로컬 인스턴스와 같은 하위 수준 환경에서만 필요합니다. 따라서 AEM 프로젝트에는 포함되어 있지 않지만 임시로 설치할 수 있는 별도의 패키지로 제공됩니다.

1. **[소프트웨어 배포 포털](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html)** > **AEM as a Cloud Service**&#x200B;로 이동합니다.
1. “GraphiQL”을 검색합니다(**GraphiQL**&#x200B;에 **i**&#x200B;를 반드시 포함하십시오).
1. 최신 **GraphiQL 콘텐츠 패키지 v.x.x.x** 다운로드
1. **AEM 시작** 메뉴에서 **도구** > **배포** > **패키지**&#x200B;로 이동합니다.
1. **패키지 업로드**&#x200B;를 클릭하고 이전 단계에서 다운로드한 패키지를 선택합니다. **설치**&#x200B;를 클릭하여 패키지를 설치합니다.

