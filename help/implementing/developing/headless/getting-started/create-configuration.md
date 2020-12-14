---
title: 구성 헤드리스 빠른 시작 안내서 만들기
description: AEM에서 Cloud Service으로 헤드리스를 시작하기 위한 첫 번째 단계로 구성을 만들어야 합니다.
translation-type: tm+mt
source-git-commit: 259d54a225f8dee5929f62b784e28f3fc2bb794a
workflow-type: tm+mt
source-wordcount: '336'
ht-degree: 2%

---


# 구성 헤드리스 빠른 시작 안내서 만들기 {#creating-configuration}

AEM에서 Cloud Service으로 헤드리스를 시작하기 위한 첫 번째 단계로 구성을 만들어야 합니다.

## 구성이란 무엇입니까?{#what-is-a-configuration}

구성 브라우저는 AEM에서 구성을 위한 범용 구성 API, 컨텐트 구조, 해상도 메커니즘을 제공합니다.

AEM의 헤드리스 컨텐츠 관리 측면에서 AEM에서 컨텐츠를 제작하여 향후 컨텐츠 및 컨텐츠 조각의 구조를 정의하는 컨텐츠 모델을 생성할 수 있는 작업 공간으로 구성을 생각해 보십시오. 이러한 모델을 구분하기 위해 여러 구성을 사용할 수 있습니다.

전체 스택 AEM 구현의 [페이지 템플릿에 익숙한 경우](/help/sites-cloud/authoring/features/templates.md) 컨텐트 모델 관리를 위한 구성 사용은 유사합니다.

## 구성 {#how-to-create-a-configuration}을 만드는 방법

컨텐츠 모델을 구성하는 데 새로운 작업 영역이 필요한 경우 관리자는 구성을 한 번만 만들거나 매우 선택적으로 만들어야 합니다. 이 시작 안내서의 목적을 위해 하나의 구성만 만들어야 합니다.

1. AEM에 Cloud Service으로 로그인하고 주 메뉴에서 **도구 -> 일반 -> 구성 브라우저**&#x200B;를 선택합니다.
1. 구성에 **제목** 및 **이름**&#x200B;을 입력합니다.
   * **제목**&#x200B;은 설명적이어야 합니다.
   * **이름**&#x200B;은 저장소의 노드 이름이 됩니다.
      * 제목 기반으로 자동으로 생성되고 [AEM 이름 지정 규칙에 따라 조정됩니다.](/help/implementing/developing/introduction/naming-conventions.md)
      * 필요한 경우 조정할 수 있습니다.
1. 다음 옵션을 선택합니다.
   * **콘텐츠 조각 모델**
   * **GraphQL 영구 쿼리**

   ![구성 만들기](../assets/create-configuration.png)

1. **만들기**&#x200B;를 탭하거나 클릭합니다

필요한 경우 여러 구성을 만들 수 있습니다. 구성을 중첩할 수도 있습니다.

>[!NOTE]
>
>구현 요구 사항에 따라 **컨텐츠 조각 모델** 및 **GraphQL 영구 쿼리** 외에 구성 옵션이 필요할 수 있습니다.

## 다음 단계 {#next-steps}

이제 이 구성을 사용하여 시작 안내서의 두 번째 부분으로 이동할 수 있으며 [컨텐츠 조각 모델 만들기](create-content-model.md)

>[!TIP]
>
>구성 브라우저에 대한 자세한 내용은 [구성 브라우저 설명서를 참조하십시오.](/help/implementing/developing/introduction/configurations.md)
