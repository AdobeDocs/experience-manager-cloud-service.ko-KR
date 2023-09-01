---
title: 콘텐츠 조각을 사용한 작업 개요
description: AEM as a Cloud Service(Adobe Experience Manager)의 콘텐츠 조각을 사용하여 Headless 전달 및 페이지 작성에 이상적인 페이지 독립적인 콘텐츠를 디자인하고, 만들고, 선별하고, 사용하는 방법에 대해 알아봅니다.
feature: Content Fragments
role: User, Developer, Architect
source-git-commit: 3d20f4bca566edcdb5f13eab581c33b7f3cf286d
workflow-type: tm+mt
source-wordcount: '1823'
ht-degree: 40%

---


# 콘텐츠 조각을 사용한 작업 개요 {#overview-working-with-content-fragments}

Adobe Experience Manager(AEM) as a Cloud Service으로 콘텐츠 조각을 사용하여 디자인하고, 만들고, 선별하고, [페이지에 영향을 받지 않는 콘텐츠 게시](/help/sites-cloud/authoring/fundamentals/content-fragments.md). 이를 통해 Headless 게재 및 페이지 작성에 이상적인, 여러 위치 및 여러 채널에서 사용할 수 있도록 컨텐츠를 준비할 수 있습니다.

>[!IMPORTANT]
>
>두 개의 콘솔에서 컨텐츠 조각에 액세스할 수 있습니다. **컨텐츠 조각** 및 **에셋**.
>
>콘텐츠 조각에 사용할 수 있는 편집기도 두 개 있습니다. 두 편집기 모두 두 콘솔에서 액세스할 수 있습니다.
>
>이 섹션에서는 다음을 다룹니다. **컨텐츠 조각** 콘솔 및 *신규* 콘텐츠 조각 편집기. 이는 Headless 콘텐츠 전달을 위해 개발되었지만 모든 시나리오에서 사용할 수 있습니다.
>
>자세한 내용은 다음을 참조하십시오.
>
>* 사용 **에셋** 콘솔 [컨텐츠 조각 관리](/help/assets/content-fragments/content-fragments-managing.md)
>* 사용 [*원본* 콘텐츠 조각 편집기](/help/assets/content-fragments/content-fragments-variations.md),
>* 사용 [페이지 작성을 위한 콘텐츠 조각](/help/sites-cloud/authoring/fundamentals/content-fragments.md).


콘텐츠 조각에는 구조화된 콘텐츠가 포함되어 있습니다.

* 각 조각은 [콘텐츠 조각 모델](/help/sites-cloud/administering/content-fragments/content-fragment-models.md).
   * 콘텐츠 조각 모델은 결과 조각의 구조를 정의합니다.
* 모든 조각은 다음과 같이 구성됩니다.
   * **[기본](#main-and-variations)** - 핵심 콘텐츠를 보유하는 조각의 필수 부분으로서, 항상 존재하지만 삭제할 수 없습니다.
   * **[변형](#main-and-variations)** - 작성자가 만든 하나 이상의 콘텐츠 순열
* 구조의 범위는 다음과 같습니다.
   * 기본
      * 예: 한 줄, 여러 줄 텍스트 필드.
      * 페이지 작성 시 사용할 간단한 콘텐츠를 준비하는 데 사용할 수 있습니다.
      * 애플리케이션에 대한 Headless 게재에 사용할 수도 있습니다.
   * 복합
      * 텍스트, 숫자, 부울, 날짜 및 시간 등 다양한 데이터 유형의 여러 필드 조합입니다.
      * 페이지 작성을 위한 보다 구조화된 콘텐츠를 준비하거나 애플리케이션에 Headless로 전달하는 데 사용할 수 있습니다.
   * 중첩
      * 사용 가능한 참조 데이터 유형을 사용하면 콘텐츠를 중첩할 수 있습니다.
      * 애플리케이션에 대한 Headless 게재에 사용되는 경향이 있습니다.

AEM 핵심 구성 요소의 Sling Model(JSON) 내보내기 기능을 사용하여 콘텐츠 조각을 JSON 형식으로 게재할 수도 있습니다. 이 게재 형식을 사용하면

* 구성 요소를 사용하여 게재할 조각의 요소를 관리할 수 있습니다.
* 대량 게재를 허용합니다. 여러 항목을 추가하여 [콘텐츠 조각 핵심 구성 요소](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/wcm-components/content-fragment-component.html) API 게재에 사용되는 페이지에서

커뮤니케이션 채널의 수는 매년 증가하고 있습니다. 일반적으로 채널은 다음 중 하나로서 게재 메커니즘을 나타냅니다.

* 물리적 채널 - 예: 데스크탑, 모바일
* 실제 채널에서의 게재 형태 - 예: 데스크탑의 “제품 세부 정보 페이지”, “제품 범주 페이지” 또는 모바일의 “모바일 웹”, “모바일 앱”

그러나 (아마도) 다음을 사용하고 싶지 않을 것입니다. *정확* 모든 채널에 대해 동일한 콘텐츠 - 특정 채널에 따라 콘텐츠를 최적화해야 합니다.

콘텐츠 조각을 사용하면

* 다양한 채널에서 효율적으로 타겟 대상자에게 도달하는 방법을 고려할 수 있습니다.
* 채널 중립적인 에디토리얼 콘텐츠를 만들고 관리할 수 있습니다.
* 다양한 채널을 위한 콘텐츠 풀을 빌드할 수 있습니다.
* 특정 채널에 맞는 콘텐츠 변형을 디자인할 수 있습니다.
* 에셋을 삽입하여 텍스트에 이미지를 추가합니다.
* 데이터의 복잡성을 반영하도록 중첩된 콘텐츠를 만듭니다.

그런 다음 이러한 콘텐츠 조각을 취합하여 다양한 채널에서 경험을 제공할 수 있습니다.

>[!NOTE]
>
>**콘텐츠 조각** 및 **[경험 조각](/help/sites-cloud/authoring/fundamentals/experience-fragments.md)**&#x200B;은 AEM 내의 다양한 기능입니다.
>* **콘텐츠 조각**&#x200B;은 정의 및 구조를 갖지만 추가적인 시각적 디자인 및/또는 레이아웃을 포함하지 않는 에디토리얼 콘텐츠입니다. 텍스트, 숫자 및 날짜 등 구조화된 데이터에 액세스하는 데 사용할 수 있습니다.
>* **경험 조각**&#x200B;은 전체적으로 배치된 콘텐츠, 즉 웹 페이지 조각입니다.
>
>경험 조각은 콘텐츠 조각 형태로 콘텐츠를 포함할 수 있지만 반대로는 불가능합니다.
>
>자세한 내용은 [AEM의 콘텐츠 조각 및 경험 조각 이해](https://experienceleague.adobe.com/docs/experience-manager-learn/sites/content-fragments/understand-content-fragments-and-experience-fragments.html#content-fragments).

이 페이지 및 다음 페이지에서는 콘텐츠 조각 생성, 구성, 유지 관리 및 사용을 위한 작업을 다룹니다.

* [인스턴스에 대해 콘텐츠 조각 기능 활성화](/help/sites-cloud/administering/content-fragments/setup.md)
* [컨텐츠 조각 모델](/help/sites-cloud/administering/content-fragments/content-fragment-models.md) - 모델 활성화, 생성 및 정의
* [콘텐츠 조각 만들기](/help/sites-cloud/administering/content-fragments/managing.md#creating-a-content-fragment) (콘텐츠 조각 콘솔 사용)

조각을 만든 후 다음을 수행할 수 있습니다.

* [콘텐츠 조각 콘솔 사용](/help/sites-cloud/administering/content-fragments/managing.md) - 조각 액세스, 게시(미리보기 또는 프로덕션) 및 참조
* [콘텐츠 조각 편집기 사용](/help/sites-cloud/administering/content-fragments/authoring.md) - 조각 편집, 게시(미리보기 또는 프로덕션) 및 참조
* [분석](/help/sites-cloud/administering/content-fragments/analysis.md)  편집기를 사용한 콘텐츠 조각의 구조
* [GraphQL을 사용하여 조각에 액세스하여 애플리케이션에 Headless 게재](/help/sites-cloud/administering/content-fragments/content-delivery-with-graphql.md).
* [또는 페이지 작성에 조각 사용](/help/sites-cloud/authoring/fundamentals/content-fragments.md)

>[!NOTE]
>
>이러한 페이지는 다음과 함께 읽을 수 있습니다.
>
>* [콘텐츠 조각 사용자 정의 및 확장](/help/implementing/developing/extending/content-fragments-customizing.md)
>* [콘텐츠 조각 렌더링용 구성 요소 구성](/help/implementing/developing/extending/content-fragments-configuring-components-rendering.md)
>* [AEM Assets HTTP API의 콘텐츠 조각 지원](/help/assets/content-fragments/assets-api-content-fragments.md)
>* [콘텐츠 조각과 함께 사용하기 위한 AEM GraphQL API](/help/headless/graphql-api/content-fragments.md)
>* [콘텐츠 조각을 사용하여 페이지 작성](/help/sites-cloud/authoring/fundamentals/content-fragments.md)

## 기본 및 변형 {#main-and-variations}

변형은 AEM 콘텐츠 조각의 중요한 기능입니다. 이 도구를 사용하여 의 복사본을 만들고 편집할 수 있습니다. **기본** headless 콘텐츠 전달 및 페이지 작성을 보다 유연하게 만들 수 있는 특정 채널 및 시나리오에서 사용할 콘텐츠.

* **기본**

   * **기본** 는 그러한 변형이 아니라 모든 변형의 기초입니다.
   * 조각의 필수 부분

      * 모든 콘텐츠 조각에는 다음 중 하나의 인스턴스가 있습니다. **기본**.
      * **기본** 삭제할 수 없습니다.

   * **기본** 아래의 조각 편집기에서 액세스할 수 있습니다. **[변형](/help/sites-cloud/administering/content-fragments/authoring.md#variations)**.

  >[!NOTE]
  >
  >에서 사용할 수 있는 편집기에서 **에셋** 콘솔, **기본** 은(는) (으)로 레이블이 지정됩니다. **기본**.

* **변형**

   * 에디토리얼 목적에 맞는 조각 텍스트의 표현물은 채널과 관련을 지을 수 있지만, 의무적이지는 않으며, 임시적 로컬 수정용일 수도 있습니다.
   * 의 사본으로 생성 **기본**, 그러나 필요에 따라 편집할 수 있습니다. 종종 변형 간에 컨텐츠가 겹치게 됩니다.
   * 조각 작성 중에 왼쪽 패널에서 정의할 수 있습니다.
   * 조각 내에 저장되므로 콘텐츠 사본 살포를 방지할 수 있습니다.
   * 변형은 다음과 같을 수 있습니다. [비교 및 동기화됨](/help/sites-cloud/administering/content-fragments/authoring.md#compare-and-synchronize-rich-text) 포함 **기본**.
  <!--
  * Can be [Summarized](/help/sites-cloud/administering/content-fragments/authoring.md#summarizing-text) to quickly truncate the text to a predefined length.
  -->

## 콘텐츠 조각 및 콘텐츠 서비스 {#content-fragments-and-content-services}

AEM Content Services는 웹 페이지에 초점을 두지 않고 AEM에서 콘텐츠 설명 및 게재를 일반화하기 위해 디자인되었습니다.

모든 클라이언트가 사용할 수 있는 표준화된 방법을 사용하여 기존 AEM 웹 페이지가 아닌 채널에 콘텐츠를 게재할 수 있습니다. 이러한 채널에는 다음과 같은 것들이 포함될 수 있습니다.

* SPA (Single Page Applications)
* 기본 모바일 애플리케이션
* AEM 외부에 있는 기타 채널 및 터치포인트

게재는 JSON 내보내기를 사용하여 JSON 형식으로 이루어집니다.

AEM 콘텐츠 조각을 사용하여 구조화된 콘텐츠를 설명하고 관리할 수 있습니다. 구조화된 콘텐츠는 텍스트, 숫자 데이터, 부울, 날짜 및 시간 등을 포함하여 다양한 콘텐츠 유형을 포함할 수 있는 모델에서 정의됩니다.

그런 다음 AEM 핵심 구성 요소의 JSON 내보내기 기능과 함께 이 구조화된 콘텐츠를 사용하여 AEM 페이지 이외의 채널에 AEM 콘텐츠를 게재할 수 있습니다.

>[!NOTE]
>
>AEM Sites as a Cloud Service용 Headless 개발에 대한 소개는 [Headless 및 AEM](/help/headless/introduction.md)을 참조하십시오.

>[!NOTE]
>
>AEM은 조각 콘텐츠 번역도 지원합니다. 자세한 내용은 [에셋 번역](/help/assets/translate-assets.md)을 참조하십시오.

## 콘텐츠 유형 {#content-type}

콘텐츠 조각은

* **사이트** 기능입니다.

* **자산**&#x200B;으로 저장됩니다.

   * 콘텐츠 조각(및 그 변형)은 [콘텐츠 조각 콘솔](/help/sites-cloud/administering/content-fragments/managing.md#content-fragments-console).
   * 에서 작성 및 편집됨 [콘텐츠 조각 편집기](/help/sites-cloud/administering/content-fragments/authoring.md).

* 를 사용하여 컨텐츠 전달에 액세스 가능 [AEM GRAPHQL API](/help/headless/graphql-api/content-fragments.md).

* 다음에서 사용 가능 [콘텐츠 조각 구성 요소를 사용한 페이지 편집기](/help/sites-cloud/authoring/fundamentals/content-fragments.md) (참조 구성 요소):

   * 다음 [콘텐츠 조각 핵심 구성 요소](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/wcm-components/content-fragment-component.html) 페이지 작성자가 사용할 수 있습니다. 따라서 페이지 작성자가 HTML 또는 JSON 형식으로 필요한 콘텐츠 조각을 참조하고 게재할 수 있습니다.

콘텐츠 조각은 다음과 같은 콘텐츠 구조입니다.

* 레이아웃이나 디자인이 없습니다(텍스트 필드의 경우 텍스트 서식 지정 가능).
* 게재 메커니즘(예: 페이지 또는 채널)에 독립적입니다.
* 하나 이상의 [구성 부분](#constituent-parts-of-a-content-fragment)을 포함합니다.
* [이미지를 포함하거나 이미지에 연결](#fragments-with-visual-assets)할 수 있습니다.

### 시각적 자산이 있는 조각 {#fragments-with-visual-assets}

작성자가 컨텐츠를 더 잘 제어할 수 있도록 이미지를 컨텐츠 조각에 추가하거나 컨텐츠 조각과 통합할 수 있습니다.

자산은 각각 고유한 장점이 있는 여러 가지 방법으로 컨텐츠 조각에 사용할 수 있습니다.

* as a **콘텐츠 참조**
* 다음 범위 내 **여러 줄 텍스트** 필드

### 콘텐츠 조각을 구성하는 부분 {#constituent-parts-of-a-content-fragment}

콘텐츠 조각 에셋은 다음 부분으로 구성됩니다(직접 또는 간접적으로).

* **조각 요소**

   * 요소는 콘텐츠를 포함하는 데이터 필드와 관련이 있습니다.
   * 다음을 사용합니다. [콘텐츠 조각 모델](/help/sites-cloud/administering/content-fragments/content-fragment-models.md) 컨텐츠 조각을 만듭니다. 모델에 지정된 요소(필드)는 조각의 구조를 정의합니다. 이러한 요소(필드)는 다양한 데이터 유형일 수 있습니다.

* **조각 단락**

   * 개별 엔티티로 구분된 텍스트 블록(종종 여러 줄)입니다.

   * 페이지 작성 중 콘텐츠를 제어할 수 있도록 해 줍니다.

* **조각 메타데이터**

   * [자산 메타데이터 스키마](/help/assets/metadata-schemas.md)를 사용합니다.
   * 다음 경우에 태그를 만들 수 있습니다.

      * 조각을 만들고 작성할 때
      * 또는 나중에 [속성 보기 또는 편집](/help/sites-cloud/administering/content-fragments/authoring.md#view-properties-tags) 조각 편집기에 있을 때

  >[!CAUTION]
  >
  >메타데이터 처리 프로필은 콘텐츠 조각에 적용되지 않습니다.

  >[!CAUTION]
  >
  >콘텐츠 조각 모델은 종종 다음과 같은 데이터 필드를 정의할 수 있습니다. **제목** 및 **설명**. 이 두 필드가 있으면 사용자 정의 필드이며 편집기의 콘텐츠 영역에서 업데이트할 수 있습니다.
  >
  >컨텐츠 조각 및 그 변형에는 이라는 메타데이터(속성) 필드도 있습니다. **제목** 및 **설명**. 이 두 메타데이터 필드는 컨텐츠 조각 및 변형의 필수적인 부분이며 조각이 생성될 때 초기에 정의됩니다. 편집기의 속성/메타데이터 영역에서 업데이트할 수 있습니다.

* **[기본](#main-and-variations)**
* **[변형](#main-and-variations)**

### 조각에 필요한 사항 {#required-by-fragments}

콘텐츠 조각을 만들려면 다음이 필요합니다.

* **콘텐츠 모델**

   * [구성 브라우저를 사용하여 활성화](/help/sites-cloud/administering/content-fragments/setup.md)됩니다.
   * [도구를 사용하여 생성](/help/sites-cloud/administering/content-fragments/content-fragment-models.md)됩니다.
   * [조각 생성](/help/sites-cloud/administering/content-fragments/managing.md#creating-content-fragments)에 필요합니다.
   * 조각의 구조(제목, 콘텐츠 요소, 태그 정의)를 정의합니다.
   * 콘텐츠 조각 모델 정의는 제목과 하나의 데이터 요소를 필요로 합니다. 그 외의 모든 것은 선택 사항입니다.
   * 기본 콘텐츠(해당되는 경우)를 정의할 수 있습니다.
   * 작성자는 조각 편집기에서 모델 편집기를 열 수 있지만 조각 콘텐츠를 작성할 때 정의된 구조를 변경할 수 없습니다.
   * 종속 콘텐츠 조각을 만든 후 모델을 변경하면 해당 콘텐츠 조각에 영향을 줄 수 있습니다.

Headless 콘텐츠 게재에 콘텐츠 조각을 사용하려면 다음 사항도 필요합니다.

* a [GraphQL 쿼리](/help/headless/graphql-api/content-fragments.md) 필요한 콘텐츠를 요청하려면
* 그런 다음 이 콘텐츠를 자체 SPA for AEM 개발에 사용할 수 있습니다. 자세한 내용은 다음 문서를 참조하십시오.

   * [SPA WKND 튜토리얼](/help/implementing/developing/hybrid/wknd-tutorial.md)
   * [React를 사용하여 시작하기](/help/implementing/developing/hybrid/getting-started-react.md)
   * [Angular를 사용하여 시작하기](/help/implementing/developing/hybrid/getting-started-angular.md)

페이지 작성에 콘텐츠 조각을 사용하려면 다음 사항이 필요합니다.

* A **콘텐츠 조각 구성 요소**

   * 조각을 HTML 및/또는 JSON 형식으로 게재하는 데 중요합니다.
   * [페이지에서 조각을 참조](/help/sites-cloud/authoring/fundamentals/content-fragments.md)하는 데 필요합니다.
   * 조각의 레이아웃 및 게재(예: 채널)를 담당합니다.
   * 조각은 레이아웃을 정의하고 일부 또는 모든 요소/변형 및 관련 콘텐츠를 게재하기 위해 하나 이상의 전용 구성 요소를 필요로 합니다.
   * 작성 중인 페이지로 조각을 드래그하면 필요한 구성 요소가 자동으로 연결됩니다.
   * 다음을 참조하십시오. [콘텐츠 조각 핵심 구성 요소](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/wcm-components/content-fragment-component.html).

## 사용 예 {#example-usage}

요소 및 변형을 포함한 조각을 사용하여 여러 채널용의 일관된 콘텐츠를 만들 수 있습니다. 조각을 디자인할 때는 사용할 항목과 위치를 고려해야 합니다.

### WKND 샘플 {#wknd-sample}

다음 [WKND 사이트 및 WKND 공유](/help/implementing/developing/introduction/develop-wknd-tutorial.md) AEM as a Cloud Service에 대해 학습하는 데 도움이 되는 샘플이 제공됩니다.

<!-- CHECK: which links can/should be used these days? -->

WKND 프로젝트에는 다음이 포함되어 있습니다.

* 콘텐츠 조각 모델은 다음에서 사용할 수 있습니다.

   * `.../libs/dam/cfm/models/console/content/models.html/conf/wknd`

   * `.../ui#/aem/libs/dam/cfm/models/console/content/models.html/conf/wknd-shared`

* 콘텐츠 조각(및 기타 콘텐츠)은 다음에서 사용할 수 있습니다.

   * `.../assets.html/content/dam/wknd/en`
