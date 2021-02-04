---
title: AEM의 헤드라인 및 헤드리스
description: AEM 프로젝트는 헤드라인 및 헤드리스 모델을 통해 구현될 수 있지만 이진형이 아닙니다. AEM은 한 프로젝트에서 두 모델의 이점을 모두 활용할 수 있는 유연성을 제공합니다.
translation-type: tm+mt
source-git-commit: 772717b7ad3baa17a58e251c128663035eb89931
workflow-type: tm+mt
source-wordcount: '1009'
ht-degree: 0%

---


# AEM {#headful-headless}의 헤드리스 및 헤드리스

Adobe Experience Manager 프로젝트는 헤드리스 모델과 헤드리스 모델 모두에서 구현할 수 있지만 이진형이 아닙니다. AEM은 한 프로젝트에서 두 모델의 이점을 모두 활용할 수 있는 유연성을 제공합니다. 이 문서에서는 서로 다른 모델에 대한 개요와 SPA 통합 수준을 설명합니다.

## 개요 {#overview}

AEM은 컨텐츠 제작 및 하나의 플랫폼에서 전달 방식을 관리할 수 있는 강력한 툴을 제공합니다. 컨텐츠 작성자와 개발자가 동일한 플랫폼을 사용하여 컨텐츠 소비자에게 경험을 전달하는 기존의 &quot;헤드풀&quot; 컨텐츠 관리 모델입니다.

또한 AEM을 사용하여 컨텐츠를 간편하게 관리할 수 있으므로 다른 플랫폼에서 컨텐츠를 프레젠테이션과 전달할 수 있습니다. 컨텐츠 작성자와 개발자는 다양한 플랫폼에서 작업하여 컨텐츠 소비자에게 경험을 제공하는 &quot;헤드리스&quot; 컨텐츠 관리 모델입니다.

그러나 이것은 이진 선택이 아니다. AEM은 탁월한 유연성을 제공하므로 두 모델의 프로젝트를 활용할 수 있습니다.

![AEM 구현 모델](headless/assets/aem-implementation-models.png)

헤드리스 또는 전체 스택 모델에서 컨텐츠는 Java, HTL 등을 기반으로 AEM 저장소 및 AEM 구성 요소에서 관리됩니다. 는 사용자 경험을 위한 컨텐츠를 렌더링하는 데 사용됩니다. 이 모델에서 컨텐츠를 만들고, 스타일을 지정하고, 표현하고, 전달하는 작업이 모두 AEM에서 이루어집니다.

헤드리스 모델에서 컨텐츠는 AEM 저장소에서 관리되지만 REST 및 GraphQL과 같은 API를 통해 다른 시스템으로 전달하여 사용자 경험에 대한 컨텐츠를 렌더링합니다. 이 모델에서 컨텐츠는 AEM으로 만들어지지만, 스타일링하고, 표현하며, 다른 플랫폼에서 모든 것을 제공합니다.

SPA(단일 페이지 애플리케이션)는 종종 AEM에서 헤드없이 제공하는 컨텐츠의 대상입니다. 그러나 이러한 SPA이 AEM에 완전히 외부 애플리케이션이 될 필요는 없습니다. AEM을 사용하면 SPA에 어떤 수준의 통합을 결정할 수 있습니다. 예를 들어봅시다.

## 웹 스토어 예 {#web-shop-example}

SPA으로 회사를 위한 기존의 웹 숍이 있다고 합시다. 제품 세부 정보와 이미지가 모두 포함되어 있습니다. 그런 다음 홍보 사이트, 블로그 및 캠페인 컨텐츠와 같은 마케팅 활동을 강화할 수 있도록 AEM을 소개할 수 있습니다. 이 둘을 어떻게 통합하나요? AEM에서는 다음과 같은 다양한 옵션을 사용할 수 있습니다.

* **시스템이 독립적으로 작동하도록 허용합니다.**
* **GraphQL을 통해 AEM에서 제한된 컨텐츠를 웹 센터에 제공합니다.** 컨텐츠는 AEM의 작성자가 작성할 수 있지만 웹 스토어 SPA을 통해서만 볼 수 있습니다.
* **AEM에 웹 스토어 SPA을 포함합니다.** 컨텐츠는 AEM의 저자에 의해 제작되고 웹 샵 컨텍스트에서 AEM으로 볼 수 있지만 조작되지는 않습니다.
* **AEM에 Web Shop SPA을 포함하고 편집 가능한 지점을 활성화할 수 있습니다.** 컨텐츠는 AEM에서 작성자가 작성할 수 있고, 웹 숍의 컨텍스트에서 AEM에서 볼 수 있으며, 작성자는 AEM 내에서 웹 샵 SPA의 컨텐츠를 조작하는 능력이 제한되어 있습니다.
* **AEM에 웹 샵 SPA을 임베드하여 전체 영역을 편집하여 편집할 수 있습니다.** 컨텐츠는 AEM에서 작성자가 작성할 수 있고, 웹 숍의 컨텍스트에서 AEM에서 볼 수 있으며, 작성자는 AEM 내에서 웹 샵 SPA의 컨텐츠를 조작하는 능력이 제한되어 있습니다.

다음 섹션에서는 이러한 통합 수준을 자세히 설명합니다.

>[!NOTE]
>
>물론 AEM SPA Editor 프레임워크를 사용하여 모든 기능이 작동하는 AEM SPA [로 웹 스토어 SPA을 다시 구현할 수도 있습니다.](/help/implementing/developing/hybrid/introduction.md) 이미 AEM이 있고 새 웹 스토어 또는 기타 SPA을 만들려는 경우 이 방법이 권장되지만 이 문서의 범위를 벗어납니다.

## SPA 통합 수준 {#integration-levels}

SPA과의 통합은 AEM에서 4단계로 이루어집니다.

* **레벨 0:통합 없음**
   * SPA과 AEM은 별도로 존재하며 정보를 교환하지 않습니다.
   * 컨텐츠는 별도의 두 시스템에서 별도로 작성, 관리 및 배달됩니다.
* **레벨 1:컨텐츠 조각 통합**
   * [컨텐츠 ](/help/assets/content-fragments/content-fragments.md) 조각은 AEM에서 SPA용 제한된 컨텐츠를 만들고 관리하는 데 사용됩니다.
   * SPA은 AEM [GraphQL API를 통해 이 컨텐츠를 검색합니다.](/help/assets/content-fragments/graphql-api-content-fragments.md)
   * 일부 컨텐츠는 AEM에서 관리되고 일부는 외부 시스템에서 관리됩니다.
   * 컨텐츠는 SPA에서만 볼 수 있습니다.
* **등급 2:AEM에 SPA 포함**
   * [컨텐츠 ](/help/assets/content-fragments/content-fragments.md) 조각은 AEM에서 SPA용 컨텐츠를 만들고 관리하는 데 사용됩니다.
   * SPA은 AEM [GraphQL API를 통해 이 컨텐츠를 검색합니다.](/help/assets/content-fragments/graphql-api-content-fragments.md)
   * 일부 컨텐츠는 AEM에서 관리되고 일부는 외부 시스템에서 관리됩니다.
   * 컨텐츠는 AEM 내에서 컨텍스트 내에서 볼 수 있습니다.
   * AEM 내에서 제한된 컨텐츠를 편집할 수 있습니다.
* **등급 3:AEM에 SPA 포함 및 전체 활성화**
   * [컨텐츠 ](/help/assets/content-fragments/content-fragments.md) 조각은 AEM에서 SPA용 컨텐츠를 만들고 관리하는 데 사용됩니다.
   * SPA은 AEM [GraphQL API를 통해 이 컨텐츠를 검색합니다.](/help/assets/content-fragments/graphql-api-content-fragments.md)
   * 컨텐츠는 AEM 내에서 컨텍스트 내에서 볼 수 있습니다.
   * 대부분의 컨텐츠는 AEM 내에서 편집할 수 있습니다.

레벨 1은 일반적인 헤드리스 구현의 예입니다. 그러나 컨텐츠 작성자는 SPA 내의 컨텍스트 내에서만 컨텐츠를 볼 수 있습니다. AEM은 저작 툴일 뿐입니다.

AEM의 장점과 유연성은 SPA의 이점을 그대로 유지하면서 레벨 2와 3을 통해 그대로 유지됩니다. 컨텐츠 작성자는 AEM에서 컨텐츠를 만들 수 있지만 AEM 내에서 컨텍스트 내에서 볼 수도 있습니다. SPA은 AEM에서 제작할 수 있지만 SPA으로 전달할 수 있습니다.

## 통합 수준 구현 {#implementing}

선택한 통합 수준에 따라 AEM에서 사용할 수 있는 다양한 도구가 있습니다. 각 수준은 이전 버전에 사용된 도구를 기반으로 만들어집니다. 다음 목록은 관련 리소스에 연결합니다.

* **레벨 1:** 컨텐츠 조각 및  [AEM 헤드리스 ](/help/implementing/developing/headless/introduction.md) 프레임워크를 사용하여 AEM 컨텐츠를 SPA에 전달할 수 있습니다.
* **레벨 2:** 레벨 1 추가:
   * [RemotePage ](/help/implementing/developing/hybrid/remote-page.md) 구성 요소를 사용하여 컨텍스트에서 AEM 컨텐츠를 볼 수 있는 외부 SPA을 AEM에 포함할 수 있습니다.
   * SPA의 특정 지점을 AEM에서 [제한된 편집 허용으로 활성화할 수도 있습니다.](/help/implementing/developing/hybrid/editing-external-spa.md)
* **레벨 3:** 레벨 2 추가:
   * SPA의 전체 영역을 활성화하여 AEM에서 포괄적인 편집을 허용할 수 있습니다.
