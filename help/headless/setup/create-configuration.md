---
title: 구성 만들기 - 헤드리스 설정
description: AEM as a Cloud Service에서 헤드리스를 시작하는 첫 번째 단계로 구성을 만듭니다.
exl-id: 48801599-f279-4e55-8033-9c418d2af5bb
source-git-commit: e81b852dc90e3cc5abc8b9f218f48d0fc1cc66eb
workflow-type: tm+mt
source-wordcount: '329'
ht-degree: 3%

---

# 구성 만들기 - 헤드리스 설정 {#creating-configuration}

AEM as a Cloud Service에서 헤드리스를 시작하는 첫 번째 단계로 구성을 만들어야 합니다.

## 구성이란 무엇입니까? {#what-is-a-configuration}

구성 브라우저는 AEM에서 구성을 위한 일반 구성 API, 컨텐츠 구조, 해상도 메커니즘을 제공합니다.

AEM의 헤드리스 컨텐츠 관리 컨텍스트에서 구성을 AEM 내에서 컨텐츠 모델을 만들고 향후 컨텐츠 및 컨텐츠 조각의 구조를 정의할 수 있는 작업 공간으로 생각하십시오. 이러한 모델을 구분하기 위한 여러 구성이 있을 수 있습니다.

잘 알고 계시면 [전체 스택 AEM 구현의 페이지 템플릿,](/help/sites-cloud/authoring/features/templates.md) 컨텐츠 모델 관리를 위한 구성 사용은 비슷합니다.

## 구성을 만드는 방법 {#how-to-create-a-configuration}

관리자는 컨텐츠 모델을 구성하는 데 새로운 작업 영역이 필요한 경우에만 구성을 한 번 만들거나 매우 신중하게 만들어야 합니다. 이 시작 안내서를 사용하려면 구성을 하나만 만들어야 합니다.

1. AEM as a Cloud Service에 로그인하고 기본 메뉴에서 를 선택합니다. **도구 -> 일반 -> 구성 브라우저**.
1. 다음을 제공합니다. **제목** 그리고 **이름** 참조하십시오.
   * 다음 **제목** 설명적이어야 합니다.
   * 다음 **이름** 은 저장소의 노드 이름이 됩니다.
      * 제목에 따라 자동으로 생성되고 [AEM 이름 지정 규칙.](/help/implementing/developing/introduction/naming-conventions.md)
      * 필요하면 조정할 수 있다.
1. 다음 옵션을 선택합니다.
   * **콘텐츠 조각 모델**
   * **GraphQL 영구 쿼리**

   ![구성 만들기](../assets/create-configuration.png)

1. **만들기**&#x200B;를 탭하거나 클릭합니다

필요한 경우 여러 구성을 만들 수 있습니다. 구성을 중첩할 수도 있습니다.

>[!NOTE]
>
>구성 옵션 및 **컨텐츠 조각 모델** 및 **GraphQL 영구 쿼리** 은 구현 요구 사항에 따라 필요할 수 있습니다.

## 다음 단계 {#next-steps}

이제 이 구성을 사용하여 시작 안내서의 두 번째 부분으로 이동할 수 있습니다. [컨텐츠 조각 모델을 만듭니다.](create-content-model.md)

>[!TIP]
>
>구성 브라우저에 대한 전체 세부 정보는 [구성 브라우저 설명서를 참조하십시오.](/help/implementing/developing/introduction/configurations.md)
