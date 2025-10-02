---
title: 콘텐츠 조각 모델 정의
description: 콘텐츠 조각 모델이 AEM에서 콘텐츠 조각을 위한 기반 역할을 하여 Headless 게재 또는 페이지 작성에 사용할 구조화된 콘텐츠를 만드는 방법에 대해 알아봅니다.
feature: Content Fragments
role: User, Developer, Architect
exl-id: 8ab5b15f-cefc-45bf-a388-928e8cc8c603
solution: Experience Manager Sites
source-git-commit: 416cb98fbf48885688ee70d63e606e3f7c90f9f8
workflow-type: tm+mt
source-wordcount: '2201'
ht-degree: 59%

---

# 콘텐츠 조각 모델 정의 {#defining-content-fragment-models}

Adobe Experience Manager(AEM) as a Cloud Service의 콘텐츠 조각 모델은 [콘텐츠 조각](/help/sites-cloud/administering/content-fragments/overview.md)의 콘텐츠 구조를 정의합니다. 그런 다음 이 조각은 페이지 작성에 사용하거나 Headless 콘텐츠의 기반으로 사용할 수 있습니다.

이 페이지에서는 전용 편집기를 사용하여 콘텐츠 조각 모델을 정의하는 방법을 다룹니다. 콘텐츠 조각 콘솔에서 사용할 수 있는 [작업](/help/sites-cloud/administering/content-fragments/managing-content-fragment-models.md), [폴더에서 모델 허용](/help/sites-cloud/administering/content-fragments/managing-content-fragment-models.md#actions) 및 [모델 게시](/help/sites-cloud/administering/content-fragments/managing-content-fragment-models.md#allowing-content-fragment-models-assets-folder)를 포함하여 조각을 만든 후 사용할 수 있는 추가 작업 및 옵션에 대해서는 [콘텐츠 조각 모델 관리](/help/sites-cloud/administering/content-fragments/managing-content-fragment-models.md#publishing-a-content-fragment-model)를 참조하십시오.

>[!CAUTION]
>
>참조된 여러 조각에 대해 쿼리하는 경우 다양한 조각 모델에 이름이 같지만 유형이 다른 필드 이름이 있는 것은 권장되지 않습니다.
>
>자세한 내용은 [콘텐츠 조각과 함께 사용할 AEM GraphQL API - 제한 사항](/help/headless/graphql-api/content-fragments.md#limitations)을 참조하십시오.

>[!NOTE]
>
>이 새 편집기로 모델을 만드는 경우 항상 해당 모델에 이 편집기를 사용해야 합니다.
>
>[원본 모델 편집기](/help/assets/content-fragments/content-fragments-models.md)가 있는 모델을 열면 다음과 같은 메시지가 표시됩니다.
>
>* &quot;이 모델에는 사용자 정의 UI 스키마가 구성되어 있습니다. 이 UI에 표시되는 필드 순서가 UI 스키마와 일치하지 않을 수 있습니다. UI 스키마와 정렬된 필드를 보려면 새 콘텐츠 조각 편집기로 전환해야 합니다.&quot;

## 콘텐츠 조각 모델 정의 {#defining-your-content-fragment-model}

콘텐츠 조각 모델은 다양한 **[데이터 유형](#data-types)**&#x200B;을 사용하여 최종 콘텐츠 조각의 구조를 효과적으로 정의합니다. 모델 편집기를 사용하여 데이터 유형의 인스턴스를 추가한 다음 필요한 필드를 만들도록 구성할 수 있습니다.

>[!CAUTION]
>
>기존 콘텐츠 조각에서 이미 사용된 모델을 편집하면 종속된 조각이 영향을 받을 수 있습니다.

1. 콘텐츠 조각 콘솔에서 [콘텐츠 조각 모델](/help/sites-cloud/administering/content-fragments/managing-content-fragment-models.md#basic-structure-handling-content-fragment-models-console)에 대한 패널을 선택하고 콘텐츠 조각 모델을 포함하는 폴더로 이동합니다.

   >[!NOTE]
   >
   >[모델을 만든 후](/help/sites-cloud/administering/content-fragments/managing-content-fragment-models.md#creating-a-content-fragment-model)바로 모델을 열 수도 있습니다.

1. **편집**&#x200B;에 필요한 모델을 엽니다. 빠른 작업 링크 중 하나를 사용하거나, 모델을 선택한 후 도구 모음에서 작업을 선택하십시오.


   ![속성](assets/cf-cfmodels-empty-model.png)

   모델 편집기를 열면 다음과 같이 표시됩니다.

   * top:
      * **홈** 아이콘
      * [원본](/help/assets/content-fragments/content-fragments-models.md)과(와) 새 편집기 간을 전환하는 옵션
      * **취소**
      * **저장**

   * 왼쪽: 필드를 만드는 데 사용할 수 있는 **데이터 형식**

   * 가운데: **추가** 옵션과 함께 이미 정의된 필드입니다.

   * 오른쪽: 오른쪽 끝에 있는 아이콘을 사용하여 다음 중에서 선택할 수 있습니다.

      * **속성**: 선택한 필드에 대한 속성을 정의하고 봅니다.
      * **모델 세부 정보**: **사용** 상태, **모델 제목**, **태그**, **설명** 및 **미리 보기 URL** 표시

1. **필드를 추가하려면**

   * 다음 중 하나를 선택합니다.

      * 왼쪽 패널의 데이터 유형을 가운데 패널의 필드에 필요한 위치로 드래그합니다.
      * 데이터 유형별로 **+** 아이콘을 선택하여 필드 목록의 맨 아래에 추가합니다.
      * 중간 패널에서 **추가**&#x200B;를 선택한 다음 결과 드롭다운 목록에서 필요한 데이터 유형을 선택하여 목록 맨 아래에 필드를 추가합니다.

     >[!NOTE]
     >
     >**탭 자리 표시자** 필드는 항상 기존 필드 위에 표시되어야 합니다.

   * 필드 상자 왼쪽에 점을 형성하여 필드의 위치를 변경할 수 있습니다.

     ![필드 이동](assets/cf-cfmodels-move-field-icon.png)

   * 모델에 필드를 추가하고(및 선택) 오른쪽 패널에 해당 특정 데이터 형식에 대해 정의할 수 있는 **속성**이 표시됩니다. 여기에서 특정 항목에 필요한 사항을 정의할 수 있습니다
필드.

      * 설명이 따로 필요하지 않은 속성도 많습니다. 자세한 내용은 [속성(데이터 형식)](#properties)을 참조하세요.
      * **필드 레이블**&#x200B;을 입력하면 **속성 이름**&#x200B;이 자동으로 채워집니다. 비어 있는 경우 이후에 수동으로 업데이트할 수 있습니다.

        >[!CAUTION]
        >
        >데이터 유형의 **속성 이름** 속성을 수동으로 업데이트할 때에는 이름에 A-Z, a-z, 0-9 및 밑줄 “_”*만* 포함해야 합니다.
        >
        >이전 버전의 AEM에서 만든 모델에 잘못된 문자가 포함되어 있는 경우, 해당 문자를 제거하거나 업데이트하십시오.

     예:

     ![필드 속성](assets/cf-cfmodels-field-properties.png)

     >[!NOTE]
     >
     >필드가 **필수**(으)로 정의된 경우 가운데 창에 표시된 **레이블**&#x200B;이(가) 별표(**&#42;**)로 표시됩니다.

1. **필드를 제거하려면**

   중간 패널에서 해당 필드에 대한 휴지통 아이콘을 선택합니다.

   ![제거](assets/cf-cfmodels-remove-icon.png)

1. 모든 필수 필드를 추가하고 필요에 따라 관련 속성을 정의합니다.

1. 정의를 유지하려면 **저장**&#x200B;을 선택합니다.

## 데이터 유형 {#data-types}

모델을 정의하는 데 다양한 데이터 유형을 사용할 수 있습니다.

* **한 줄 텍스트**
   * 한 줄의 텍스트에 대한 필드를 추가합니다. 최대 길이를 정의할 수 있습니다.
   * 조각 작성자가 필드의 새 인스턴스를 만들 수 있도록 필드를 구성할 수 있습니다

* **여러 줄 텍스트**
   * 리치 텍스트, 일반 텍스트 또는 Markdown일 수 있는 텍스트 영역입니다.
   * 조각 작성자가 필드의 새 인스턴스를 만들 수 있도록 필드를 구성할 수 있습니다

  >[!NOTE]
  >
  >텍스트 영역이 리치 텍스트, 일반 텍스트 또는 Markdown 인지 여부는 모델에서 **기본 유형** 속성에 의해 정의됩니다.
  >
  >이 포맷은 [콘텐츠 조각 편집기](/help/sites-cloud/administering/content-fragments/authoring.md)가 아니라 모델에서만 변경할 수 있습니다.

* **숫자**
   * 숫자 필드 추가
   * 조각 작성자가 필드의 새 인스턴스를 만들 수 있도록 필드를 구성할 수 있습니다

* **부울**
   * 부울 확인란을 추가합니다.

* **날짜 및 시간**
   * 날짜 및/또는 시간 필드 추가

* **열거**
   * 확인란, 라디오 버튼 또는 드롭다운 필드 세트 추가
      * 조각 작성자가 사용할 수 있는 옵션을 지정할 수 있습니다

* **태그**
   * 조각 작성자가 태그의 영역에 액세스하고 선택할 수 있습니다.

* **조각 참조**
   * 다른 콘텐츠 조각을 참조합니다. [중첩된 콘텐츠를 생성](#using-references-to-form-nested-content)하는 데 사용할 수 있습니다.
   * 조각 작성자가 다음과 같은 작업을 수행할 수 있도록 데이터 유형을 구성할 수 있습니다.
      * 참조된 조각 직접 편집
      * 적절한 모델을 기반으로 새 콘텐츠 조각 만들기
      * 필드의 새 인스턴스 만들기
   * 참조는 참조된 리소스에 대한 경로를 지정합니다(예: `/content/dam/path/to/resource`).

     <!--
    * Internally the reference is held as a universally unique ID (UUID) that references the resource
    * You do not need to know the UUID; in the fragment editor you can browse to the required fragment.
    -->

  <!--
  >[!NOTE]
  >
  >The UUIDs are repository specific. If you use the [Content Copy Tool](/help/implementing/developing/tools/content-copy.md) to copy Content Fragments, the UUIDs will be recalculated in the target environment.
  -->

* **콘텐츠 참조**
   * 모든 유형의 다른 콘텐츠를 참조합니다. [중첩된 콘텐츠를 생성](#using-references-to-form-nested-content)하는 데 사용할 수 있습니다.
   * 이미지가 참조되면 썸네일을 표시하도록 선택할 수 있습니다.
   * 조각 작성자가 필드의 새 인스턴스를 만들 수 있도록 필드를 구성할 수 있습니다
   * 참조는 참조된 리소스에 대한 경로를 지정합니다(예: `/content/dam/path/to/resource`).

     <!--
    * Internally the reference is held as a universally unique ID (UUID) that references the resource
    * You do not need to know the UUID; in the fragment editor you can browse to the required asset resource
    -->

  <!--
  >[!NOTE]
  >
  >The UUIDs are repository specific. If you use the [Content Copy Tool](/help/implementing/developing/tools/content-copy.md) to copy Content Fragments, the UUIDs will be recalculated in the target environment.
  -->

* **JSON 오브젝트**
   * 콘텐츠 조각 작성자는 조각의 해당 요소에 JSON 구문을 입력할 수 있습니다.
      * AEM이 다른 서비스에서 복사/붙여넣기한 직접 JSON을 저장하도록 합니다.
      * JSON이 전달되고 GraphQL에서 JSON으로 출력됩니다.
      * 콘텐츠 조각 편집기에 JSON 구문 강조, 자동 채우기 및 오류 강조 표시를 포함합니다.

* **탭 자리 표시자**
   * 콘텐츠 조각 콘텐츠를 편집할 때 사용할 탭을 가져올 수 있습니다.
      * 이는 모델 편집기에서 콘텐츠 데이터 유형 목록의 섹션을 구분하는 구분선으로 표시됩니다. 각 인스턴스는 새 탭의 시작을 나타냅니다.
      * 조각 편집기에서 각 인스턴스는 탭으로 표시됩니다.

     >[!NOTE]
     >
     >이 데이터 유형은 순전히 서식에 사용되며 AEM GraphQL 스키마에서는 무시됩니다.
     >
     >**탭 자리 표시자** 필드는 항상 기존 필드 위에 표시되어야 합니다.

## 속성(데이터 유형) {#properties}

설명이 따로 필요하지 않은 특정 속성들에 대한 자세한 내용은 아래를 참조하십시오.

* **속성 이름**

  데이터 유형의 이 속성을 수동으로 업데이트할 때에는 이름에 A-Z, a-z, 0-9 및 밑줄 “_”*만* **포함해야 합니다**.

  >[!CAUTION]
  >
  >이전 버전의 AEM에서 만든 모델에 잘못된 문자가 포함되어 있는 경우, 해당 문자를 제거하거나 업데이트하십시오.

* **렌더링 형식**

  조각의 필드를 구현하거나 렌더링하기 위한 다양한 옵션입니다. 이를 통해 작성자에게 필드의 단일 인스턴스가 표시되는지 또는 작성자가 여러 인스턴스를 만들 수 있는지를 정의할 수 있습니다. **여러 필드**&#x200B;를 사용하면 최소 및 최대 항목 수를 정의할 수 있습니다. 자세한 내용은 [유효성 검사](#validation)를 참조하세요.

* **필드 레이블**
**필드 레이블**&#x200B;을 입력하면 **속성 이름**&#x200B;이 자동으로 생성되며, 필요한 경우 수동으로 업데이트할 수 있습니다.

* **유효성 검사**
기본 유효성 검사는 **필수** 속성과 같은 메커니즘을 통해 사용할 수 있습니다. 일부 데이터 유형에는 추가 유효성 검사 필드가 있습니다. 자세한 내용은 [유효성 검사](#validation)를 참조하십시오.

* 데이터 유형 **여러 줄 텍스트**&#x200B;의 경우 **기본 유형**&#x200B;을 다음 중 하나로 정의할 수 있습니다.

   * **리치 텍스트**
   * **Markdown**
   * **일반 텍스트**

  지정하지 않으면 이 필드에 기본값인 **리치 텍스트**&#x200B;가 사용됩니다.

  콘텐츠 조각 모델의 **기본 유형** 변경은 해당 조각을 편집기에서 열고 저장한 후에 기존 관련 콘텐츠 조각에만 적용됩니다.

* **고유**
특정 필드의 경우, 콘텐츠는 현재 모델에서 만들어진 모든 콘텐츠 조각에서 고유해야 합니다.

  콘텐츠 작성자가 동일한 모델의 다른 조각에 이미 추가된 콘텐츠를 반복할 수 없도록 하는 데 사용됩니다.

  예를 들어 `Country`라고 하는 콘텐츠 조각 모델의 **한 줄 텍스트** 필드는 두 개의 종속 콘텐츠 조각에서 `Japan` 값을 가질 수 없습니다. 두 번째 인스턴스를 시도하면 경고가 표시됩니다.

  >[!NOTE]
  >
  >언어 루트별로 고유성이 보장됩니다.

  >[!NOTE]
  >
  >변형은 동일한 조각의 변형과 동일한 *고유* 값을 가질 수 있지만, 다른 조각의 변형에 사용되는 것과 동일한 값을 가질 수는 없습니다.

* 특정 데이터 유형 및 그 속성에 대한 자세한 내용은 **[콘텐츠 참조](#content-reference)**&#x200B;를 참조하십시오.

* 특정 데이터 유형 및 그 속성에 대한 자세한 내용은 **[조각 참조(중첩된 조각)](#fragment-reference-nested-fragments)**&#x200B;를 참조하십시오.

* **변환 가능**

  콘텐츠 조각 모델 편집기의 필드에서 **변환 가능** 확인란을 선택하면

   * 필드의 속성 이름이 아직 존재하지 않는 경우 번역 구성, 컨텍스트 `/content/dam/<sites-configuration>`에 추가됩니다.
   * GraphQL의 경우: 콘텐츠 조각 필드의 `<translatable>` 속성을 `yes`로 설정하여 GraphQL 쿼리가 변환 가능한 콘텐츠만 포함하는 JSON 출력을 필터링하도록 합니다.

## 유효성 검사 {#validation}

이제 다양한 데이터 유형에는 최종 조각에 콘텐츠를 입력하는 경우에 대한 유효성 검사 요구 사항을 정의할 수 있는 기능이 포함됩니다.

* **한 줄 텍스트**
   * 사전 정의된 정규 표현식과 비교합니다.
* **숫자**
   * 특정 값을 확인합니다.
* **콘텐츠 참조**
   * 특정 유형의 콘텐츠를 테스트합니다.
   * 지정된 파일 크기 이하의 자산만 참조할 수 있습니다.
   * 사전 정의된 폭 및/또는 높이 범위(픽셀 단위) 내의 이미지만 참조할 수 있습니다.
* **조각 참조**
   * 특정 콘텐츠 조각 모델을 테스트합니다.
* **최소 항목 수** / **최대 항목 수**

  **다중 필드**(**렌더링 형식**(으)로 설정)로 정의된 필드에는 다음 옵션이 있습니다.

   * **최소 항목 수**
   * **최대 항목 수**

  [콘텐츠 조각 편집기](/help/sites-cloud/administering/content-fragments/authoring.md)에서 유효성을 검사합니다.

## 참조를 사용하여 중첩된 콘텐츠 형성 {#using-references-to-form-nested-content}

콘텐츠 조각은 다음 데이터 유형 중 하나를 사용하여 중첩된 콘텐츠를 형성할 수 있습니다.

* [콘텐츠 참조](#content-reference)
   * 모든 유형의 다른 콘텐츠에 대한 간단한 참조를 제공합니다.
   * **콘텐츠 참조** 데이터 형식에서 제공
   * 최종 조각에서 하나 이상의 참조에 대해 구성할 수 있습니다.

* [조각 참조](#fragment-reference-nested-fragments)(중첩된 조각)
   * 지정된 특정 모델에 따라 다른 조각을 참조합니다.
   * **조각 참조** 데이터 형식에서 제공
   * 구조화된 데이터를 포함/검색할 수 있습니다.

     >[!NOTE]
     >
     >이 방법은 특히 [GraphQL을 통해 콘텐츠 조각을 사용하여 Headless 콘텐츠를 게재할 때](/help/sites-cloud/administering/content-fragments/content-delivery-with-graphql.md) 사용할 수 있습니다.
   * 최종 조각에서 하나 이상의 참조에 대해 구성할 수 있습니다.

<!--
>[!NOTE]
>
>See [Upgrade your Content Fragments for UUID References](/help/headless/graphql-api/uuid-reference-upgrade.md) for further information about Content/Fragment Reference and Content/Fragment Reference (UUID), and upgrading to the UUID-based data types.
-->

>[!NOTE]
>
>AEM은 다음에 대한 재발 방지 기능을 제공합니다.
>
>* 콘텐츠 참조
>  >  따라서 사용자가 현재 조각에 대한 참조를 추가할 수 없으며 이로 인해 빈 조각 참조 선택기 대화 상자가 나타날 수 있습니다.
>
>* GraphQL의 조각 참조
>  >  서로 참조하는 여러 콘텐츠 조각을 반환하는 복합 쿼리를 만들면 첫 번째 발생 시 null을 반환합니다.

>[!CAUTION]
>
>참조된 여러 조각에 대해 쿼리하는 경우 다양한 조각 모델에 이름이 같지만 유형이 다른 필드 이름이 있는 것은 권장되지 않습니다.
>
>자세한 내용은 [콘텐츠 조각과 함께 사용할 AEM GraphQL API - 제한 사항](/help/headless/graphql-api/content-fragments.md#limitations)을 참조하십시오.

### 콘텐츠 참조 {#content-reference}

**콘텐츠 참조** 데이터 형식을 사용하면 다른 소스의 콘텐츠를 렌더링할 수 있습니다(예: 이미지, 페이지 또는 경험 조각).

표준 속성 외에 다음을 지정할 수 있습니다.

* 참조된 콘텐츠를 저장할 위치를 지정하거나 나타내는 **루트 경로**
  >[!NOTE]
  >
  >이 경로는 콘텐츠 조각 편집기를 사용할 때 이 필드에 이미지를 직접 업로드하고 참조하려는 경우 필수입니다.
  >
  >자세한 내용은 [이미지 참조](/help/sites-cloud/administering/content-fragments/authoring.md#reference-images)를 참조하십시오.

* 참조할 수 있는 콘텐츠 유형
  >[!NOTE]
  >
  >콘텐츠 조각 편집기를 사용할 때 이 필드에 이미지를 직접 업로드하고 참조하려는 경우 이에 **이미지**&#x200B;가 포함되어야 합니다.
  >
  >자세한 내용은 [이미지 참조](/help/sites-cloud/administering/content-fragments/authoring.md#reference-images)를 참조하십시오.

* 파일 크기 제한
* 이미지를 참조한 경우:
   * 썸네일 표시
   * 높이 및 폭의 이미지 제한

![콘텐츠 참조](assets/cf-cfmodels-content-reference.png)

### 조각 참조(중첩된 조각) {#fragment-reference-nested-fragments}

**조각 참조** 데이터 형식은 하나 이상의 콘텐츠 조각을 참조할 수 있습니다. 여러 계층으로 구조화된 데이터를 검색할 수 있어 앱에서 사용할 콘텐츠를 검색할 때 특히 유용한 기능입니다.

예:

* 다음을 포함하는 직원의 세부 정보를 정의하는 모델
   * 고용주(회사)를 정의하는 모델에 대한 참조

```xml
type EmployeeModel {
    name: String
    firstName: String
    company: CompanyModel
}

type CompanyModel {
    name: String
    street: String
    city: String
}
```

>[!NOTE]
>
>콘텐츠 참조는 특히 [GraphQL을 통해 콘텐츠 조각을 사용하여 Headless 콘텐츠를 게재할 때](/help/sites-cloud/administering/content-fragments/content-delivery-with-graphql.md) 사용할 수 있습니다.

표준 속성 외에 다음을 정의할 수 있습니다.

* **렌더링 형식**:

   * **다중 필드** - 조각 작성자는 여러 개별 참조를 생성할 수 있습니다.

   * **조각 참조** - 조각 작성자가 조각에 대한 단일 참조를 선택하도록 합니다.

* **모델 유형**
여러 모델을 선택할 수 있습니다. 참조를 콘텐츠 조각에 추가할 때 이러한 모델을 사용하여 참조된 조각을 만들어야 합니다.

* **루트 경로**
참조된 조각의 루트 경로를 지정하거나 나타냅니다.

* **조각 생성 허용**

  이를 통해 조각 작성자는 적절한 모델을 기반으로 조각을 만들 수 있습니다.

   * **조각 참조 합성** - 이 기능을 사용하면 조각 작성자가 여러 조각을 선택하여 합성을 빌드할 수 있습니다.

  ![조각 참조](assets/cf-cfmodels-fragment-reference.png)

>[!NOTE]
>
>재발 방지 메커니즘을 사용할 수 있습니다. 이는 사용자가 조각 참조에서 현재 콘텐츠 조각을 선택할 수 없도록 하고 이로 인해 빈 조각 참조 선택기 대화 상자가 나타날 수 있습니다.
>
>또한 GraphQL에는 조각 참조에 대한 재발 방지 기능이 있습니다. 서로 참조하는 두 개의 콘텐츠 조각 간에 복합 쿼리를 만들면 null을 반환합니다.
