---
title: 콘텐츠 조각 - 설정
description: 콘텐츠 조각 및 GraphQL 기능을 활성화하여 AEM Headless 게재 기능을 사용하는 방법에 대해 알아봅니다.
feature: Content Fragments
role: Developer, Architect
source-git-commit: 676173813b6ea4defeafe25c95be9668d32aac38
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 37%

---


# 콘텐츠 조각 - 설정 {#content-fragments-setup}

Adobe Experience Manager(AEM) 내의 콘텐츠 조각을 as a Cloud Service으로 사용하여 여러 위치 및 여러 채널에서 사용할 수 있는 콘텐츠를 준비할 수 있습니다. Headless 게재 및 페이지 작성에 이상적입니다.

콘텐츠 조각 기능에 대한 인스턴스를 활성화하려면 다음을 활성화해야 합니다.

* **콘텐츠 조각 모델** - 필수

  >[!CAUTION]
  >
  >**콘텐츠 조각 모델**&#x200B;을 활성화하지 않는 경우
  >
  >* 다음 **만들기** 모델을 만드는 데 옵션을 사용할 수 없습니다.
  >* [사이트 구성을 선택하여 관련 엔드포인트를 생성](/help/headless/graphql-api/graphql-endpoint.md)할 수 없습니다.

* **GraphQL 지속 쿼리** - 옵션

인스턴스 설정이 완료되었습니다.

* 작성자: [구성 브라우저에서 기능 활성화](#enable-content-fragment-functionality-configuration-browser)
* 그러면 [개별 Assets 폴더에 구성 적용](#apply-the-configuration-to-your-folder)

## 구성 브라우저에서 콘텐츠 조각 기능 활성화 {#enable-content-fragment-functionality-configuration-browser}

콘텐츠 조각 모델 및 GraphQL 지속 쿼리의 콘텐츠 조각 기능을 사용하려면 **필수** 먼저 를 통해 활성화합니다. **구성 브라우저**:

>[!NOTE]
>
>자세한 내용은 [구성 브라우저](/help/implementing/developing/introduction/configurations.md#using-configuration-browser).

>[!NOTE]
>
>[하위 구성](/help/implementing/developing/introduction/configurations.md#configuration-resolution)(다른 구성 내에 중첩된 구성)은 콘텐츠 조각, 콘텐츠 조각 모델 및 GraphQL 쿼리와 함께 사용할 수 있도록 완전히 지원됩니다.
>
>다음을 참고하십시오.
>
>* 하위 구성에서 모델을 생성한 후에는 해당 모델을 다른 하위 구성으로 이동하거나 복사할 수 없습니다.
>
>* GraphQL 엔드포인트는 상위(루트) 구성을 기반으로 합니다.
>
>* 지속 쿼리는 상위(루트) 구성과 관련하여 저장됩니다.

1. **도구**, **일반**&#x200B;으로 이동한 다음 **구성 브라우저**&#x200B;를 엽니다.

1. **만들기**&#x200B;를 사용하여 대화 상자를 열고 여기에서

   1. **제목**&#x200B;을 지정합니다.
   1. 생성 시 **이름** 는 저장소의 노드 이름이 됩니다.
이름을 입력합니다. 필드를 비워 두면 제목을 기반으로 자동으로 생성된 다음, [AEM 이름 지정 규칙](/help/implementing/developing/introduction/naming-conventions.md): 필요한 경우 결과를 조정할 수 있습니다.
   1. 사용을 활성화하려면 다음을 선택합니다.
      * **콘텐츠 조각 모델**
      * **GraphQL 지속 쿼리**

      ![구성 정의](assets/cf-setup-create-conf.png)

1. **만들기**&#x200B;를 선택하여 정의를 저장합니다.

## 폴더에 구성 적용 {#apply-the-configuration-to-your-folder}

구성 시 **글로벌** 가 콘텐츠 조각 기능에 대해 활성화되면 를 통해 액세스할 수 있는 모든 에셋 폴더에 적용됩니다. **에셋** 콘솔.

비교 가능한 자산 폴더와 함께 다른 구성(전역 제외)을 사용하려면 연결을 정의해야 합니다. 적절한 을(를) 선택하여 이 작업을 수행합니다 **구성** 다음에서 **Cloud Service** 의 탭 **폴더 속성** 를 사용하십시오.

![구성 적용](assets/cf-setup-apply-conf.png)
