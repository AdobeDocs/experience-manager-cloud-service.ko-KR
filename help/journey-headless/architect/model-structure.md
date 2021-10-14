---
title: AEM에서 컨텐츠 조각 모델 생성에 대해 알아봅니다
description: 컨텐츠 조각 모델을 사용하여 헤드리스 CMS용 컨텐츠 모델링 컨텐츠의 개념과 역학에 대해 알아봅니다.
index: true
hide: false
hidefromtoc: false
exl-id: fdfa79d3-fbed-4467-a898-c1b2678fc0cb
source-git-commit: ddea30a50c0c6146b0ac5b44c609d4a6f78f1fcc
workflow-type: tm+mt
source-wordcount: '700'
ht-degree: 7%

---

# AEM에서 컨텐츠 조각 모델 생성에 대해 알아봅니다 {#architect-headless-content-fragment-models}

## 지금까지 이야기 {#story-so-far}

[AEM Headless 컨텐츠 작성자 여정](overview.md) 의 시작 부분에서 AEM](basics.md)헤드리스를 사용하는 헤드리스를 위한 [컨텐츠 모델링 기본 사항 은 헤드리스 작성에 관련된 기본 개념과 용어를 다룹니다.

이 문서는 AEM 헤드리스 프로젝트에 대한 자체 컨텐츠 조각 모델을 만드는 방법을 이해할 수 있도록 이러한 조각을 기반으로 합니다.

## 목표 {#objective}

* **대상**: 초보
* **목표**: 컨텐츠 조각 모델을 사용하여 헤드리스 CMS용 컨텐츠 모델링 컨텐츠의 개념 및 역학을 참조하십시오.

<!-- which persona does this? -->
<!-- and who allows the configuration on the folders? -->

<!--
## Enabling Content Fragment Models {#enabling-content-fragment-models}

At the very start you need to enable Content Fragment Models for your site, this is done in the Configuration Browser; under Tools -> General -> Configuration Browser. You can either select to configure the global entry, or create a new configuration. For example:

![Define configuration](/help/assets/content-fragments/assets/cfm-conf-01.png)

>[!NOTE]
>
>See Additional Resources - Content Fragments in the Configuration Browser
-->

## 컨텐츠 조각 모델 만들기 {#creating-content-fragment-models}

그런 다음 컨텐츠 조각 모델 을 만들고 구조를 정의할 수 있습니다. 도구 -> 자산 -> 컨텐츠 조각 모델에서 이 작업을 수행할 수 있습니다.

![도구의 컨텐츠 조각 모델](assets/cfm-tools.png)

이 옵션을 선택한 후 모델의 위치로 이동하고 **만들기**&#x200B;를 선택합니다. 여기에서 다양한 주요 세부 정보를 입력할 수 있습니다.

**모델 활성화** 옵션이 기본적으로 활성화됩니다. 즉, 컨텐츠 조각을 저장하자마자 모델을 사용할 수 있습니다(컨텐츠 조각 만들기에서). 원할 경우 이 모델을 비활성화할 수 있습니다. 나중에 기존 모델을 활성화(또는 비활성화)할 기회가 있습니다.

![컨텐츠 조각 모델 만들기](/help/assets/content-fragments/assets/cfm-models-02.png)

**만들기**&#x200B;로 확인한 다음 **모델 열기**&#x200B;를 사용하여 구조 정의를 시작할 수 있습니다.

## 컨텐츠 조각 모델 정의 {#defining-content-fragment-models}

새 모델을 처음 열면 왼쪽에 큰 공백 및 오른쪽에 **데이터 유형**&#x200B;의 긴 목록이 표시됩니다.

![빈 모델](/help/assets/content-fragments/assets/cfm-models-03.png)

그럼 어떻게 해야 하죠?

**데이터 유형**&#x200B;의 인스턴스를 왼쪽 공간으로 드래그할 수 있습니다. 이미 모델을 정의하고 있습니다.

![필드 정의](/help/assets/content-fragments/assets/cfm-models-04.png)

데이터 유형을 추가하면 해당 필드에 대한 **속성**&#x200B;을 정의해야 합니다. 사용 유형에 따라 다릅니다. 예:

![데이터 속성](/help/assets/content-fragments/assets/cfm-models-05.png)

필요한 만큼 필드를 추가할 수 있습니다. 예:

![컨텐츠 조각 모델](/help/assets/content-fragments/assets/cfm-models-07.png)

### 컨텐츠 작성자 {#your-content-authors}

컨텐츠 작성자는 모델을 만드는 데 사용한 실제 데이터 유형 및 속성을 볼 수 없습니다. 즉, 특정 필드를 완료하는 방법에 대한 도움말 및 정보를 제공해야 할 수 있습니다. 기본 정보에 대해서는 필드 레이블 및 기본값을 사용할 수 있지만 프로젝트별 설명서를 고려해야 할 수도 있습니다.

>[!NOTE]
>
>추가 리소스 - 컨텐츠 조각 모델 을 참조하십시오.

## 컨텐츠 조각 모델 관리 {#managing-content-fragment-models}

<!-- needs more details -->

컨텐츠 조각 모델 관리에 다음이 포함됩니다.

* 활성화(또는 비활성화) - 컨텐츠 조각을 만들 때 작성자가 사용할 수 있습니다.
* 삭제 - 삭제가 항상 필요하지만, 이미 게시된 특정 조각과 같은 컨텐츠 조각에 이미 사용된 모델을 삭제하는 것을 알고 있어야 합니다.

## 게시 {#publishing}

<!-- needs more details -->

컨텐츠 조각 모델은 종속된 컨텐츠 조각이 게시될 때/게시되기 전에 게시해야 합니다.

>[!NOTE]
>
>작성자가 모델이 아직 게시되지 않은 컨텐츠 조각을 게시하려고 하면 선택 목록에 이것이 표시되고 모델이 조각과 함께 게시됩니다.

>[!NOTE]
>
>잠긴(게시된) 컨텐츠 조각 모델 기능은 베타에 있습니다.

모델이 게시되는 즉시 이 모델은 작성자의 읽기 전용 모드로 *잠긴*&#x200B;입니다. 이는 기존 GraphQL 스키마 및 쿼리, 특히 게시 환경에서 오류가 발생하는 변경을 방지하기 위한 것입니다. **잠김**&#x200B;에 의해 콘솔에 표시됩니다.

모델이 **잠금**(읽기 전용 모드)이면 모델의 내용 및 구조를 볼 수 있지만 직접 편집할 수는 없습니다. 그러나 콘솔 또는 모델 편집기에서 **잠금** 모델을 관리할 수 있습니다.

## 다음은 무엇입니까? {#whats-next}

기본 사항을 배웠으므로 다음 단계는 고유한 컨텐츠 조각 모델 만들기를 시작하는 것입니다.

## 추가 리소스 {#additional-resources}

* [작성 개념](/help/sites-cloud/authoring/getting-started/concepts.md)

* [기본 처리](/help/sites-cloud/authoring/getting-started/basic-handling.md)  - 이 페이지는 주로  **** 사이트 콘솔을 기반으로 하지만, 많은/대부분의 기능은  **자산 콘솔 아래의 컨텐츠 조각 모델** 로 이동하고 작업을 수행하는 데에도  **** 관련이 있습니다.

* [컨텐츠 조각을 사용한 작업](/help/assets/content-fragments/content-fragments.md)

   * [컨텐츠 조각 모델](/help/assets/content-fragments/content-fragments-models.md)

      * [컨텐츠 조각 모델 정의](/help/assets/content-fragments/content-fragments-models.md#defining-your-content-fragment-model)

      * [컨텐츠 조각 모델 활성화 또는 비활성화](/help/assets/content-fragments/content-fragments-models.md#enabling-disabling-a-content-fragment-model)

      * [자산 폴더에서 컨텐츠 조각 모델 허용](/help/assets/content-fragments/content-fragments-models.md#allowing-content-fragment-models-assets-folder)

      * [컨텐츠 조각 모델 삭제](/help/assets/content-fragments/content-fragments-models.md#deleting-a-content-fragment-model)

      * [컨텐츠 조각 모델 게시](/help/assets/content-fragments/content-fragments-models.md#publishing-a-content-fragment-model)

      * [컨텐츠 조각 모델 게시 취소](/help/assets/content-fragments/content-fragments-models.md#unpublishing-a-content-fragment-model)

      * [잠김(게시된) 컨텐츠 조각 모델](/help/assets/content-fragments/content-fragments-models.md#locked-published-content-fragment-models)

* 시작 안내서

   * [컨텐츠 조각 모델 만들기 헤드리스 빠른 시작 안내서](/help/implementing/developing/headless/getting-started/create-content-model.md)
