---
title: 콘텐츠 조각 작업 개요
description: AEM의 콘텐츠 조각을 as a Cloud Service으로 사용하여 Headless 게재 및 페이지 작성에 이상적인 콘텐츠를 만들고 사용하는 방법에 대해 알아봅니다.
feature: Content Fragments
role: User, Developer, Architect
exl-id: ce9cb811-57d2-4a57-a360-f56e07df1b1a
source-git-commit: 19685cb952a890731bd7d75a2adf3cfd841a465f
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# 콘텐츠 조각 작업 개요 {#overview-working-with-content-fragments}

Adobe Experience Manager(AEM) as a Cloud Service의 콘텐츠 조각을 사용하여 [페이지 독립적 콘텐츠](/help/sites-cloud/authoring/fundamentals/content-fragments.md)를 디자인, 작성, 조정 및 게시할 수 있습니다. 이를 통해 Headless 게재에 이상적인 여러 위치 및 여러 채널에서 사용할 수 있도록 콘텐츠를 준비하고 페이지를 작성할 수 있습니다.

>[!IMPORTANT]
>
>콘텐츠 조각은 다음 두 콘솔에서 액세스할 수 있습니다. **콘텐츠 조각** 및 **자산**.
>
>또한 콘텐츠 조각에 사용할 수 있는 편집기가 두 개 있습니다. (두 편집기는 모두 두 콘솔에서 액세스할 수 있습니다.)
>
>이 섹션에서는 **콘텐츠 조각** 콘솔과 *새* 콘텐츠 조각 편집기를 다룹니다. 이는 Headless 콘텐츠 게재를 맞게 개발되었습니다(단, 모든 시나리오에서 사용 가능).
>
>자세한 내용은 다음을 참조하십시오.
>
>* [콘텐츠 조각 관리](/help/assets/content-fragments/content-fragments-managing.md)용 **자산** 콘솔 사용
>* [*원래* 콘텐츠 조각 편집기](/help/assets/content-fragments/content-fragments-variations.md) 사용,
>* [페이지 작성에 콘텐츠 조각](/help/sites-cloud/authoring/fundamentals/content-fragments.md) 사용,


콘텐츠 조각에는 구조화된 콘텐츠가 포함되어 있습니다.

* 각 조각은 [콘텐츠 조각 모델](/help/sites-cloud/administering/content-fragments/content-fragment-models.md)을 기반으로 합니다.
   * 콘텐츠 조각 모델은 결과 조각의 구조를 정의합니다.
* 모든 조각은 다음과 같이 구성됩니다.
   * **[기본](#main-and-variations)** - 핵심 콘텐츠를 가지고, 항상 존재하고, 삭제할 수 없는 조각의 필수 부분
   * **[변형](#main-and-variations)** - 작성자가 만든 하나 이상의 콘텐츠 순열
* 구조의 범위는 다음과 같습니다.
   * 기본
      * 여러 줄이 있는 단일 텍스트 필드를 예로 들 수 있습니다.
      * 페이지 작성 시 사용할 간단한 콘텐츠를 준비하는 데 사용할 수 있습니다.
      * 애플리케이션의 Headless 게재에도 사용할 수 있습니다.
   * 복합
      * 텍스트, 숫자, 부울 및 데이터와 시간 등 다양한 데이터 유형의 여러 필드 조합입니다.
      * 페이지 작성을 위해 보다 구조화된 콘텐츠를 준비하거나 Headless 방식으로 애플리케이션에 게재하는 데 사용할 수 있습니다.
   * 중첩
      * 사용 가능한 참조 데이터 유형을 사용하면 콘텐츠를 중첩할 수 있습니다.
      * 주로 Headless 방식으로 애플리케이션에 게재하는 데 사용됩니다.

AEM 핵심 구성 요소의 Sling Model(JSON) 내보내기 기능을 사용하여 콘텐츠 조각을 JSON 포맷으로 게재할 수도 있습니다. 이 게재 형식을 사용하면

* 구성 요소를 사용하여 게재할 조각의 요소를 관리할 수 있습니다.
* API 게재에 사용되는 페이지에서 여러 [콘텐츠 조각 핵심 구성 요소](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/wcm-components/content-fragment-component.html)를 추가하여 벌크 게재를 수행할 수 있습니다.

커뮤니케이션 채널의 수는 매년 증가하고 있습니다. 일반적으로 채널은 다음 중 하나로서 게재 메커니즘을 나타냅니다.

* 물리적 채널 - 예: 데스크탑, 모바일
* 실제 채널에서의 게재 형태 - 예: 데스크탑의 “제품 세부 정보 페이지”, “제품 범주 페이지” 또는 모바일의 “모바일 웹”, “모바일 앱”

단, 대개 모든 채널에 대해 *정확하게* 동일한 콘텐츠를 사용하고 싶지 않을 것이므로 특정 채널에 따라 콘텐츠를 최적화해야 합니다.

콘텐츠 조각을 사용하면

* 다양한 채널에서 효율적으로 타겟 대상자에게 도달하는 방법을 고려할 수 있습니다.
* 채널 중립적인 에디토리얼 콘텐츠를 만들고 관리할 수 있습니다.
* 다양한 채널을 위한 콘텐츠 풀을 빌드할 수 있습니다.
* 특정 채널에 맞는 콘텐츠 변형을 디자인할 수 있습니다.
* 자산을 삽입하여 텍스트에 이미지를 추가합니다.
* 데이터의 복잡성을 반영하도록 중첩된 콘텐츠를 만듭니다.

그런 다음 이러한 콘텐츠 조각을 취합하여 다양한 채널에서 경험을 제공할 수 있습니다.

>[!NOTE]
>
>**콘텐츠 조각** 및 **[경험 조각](/help/sites-cloud/authoring/fundamentals/experience-fragments.md)**&#x200B;은 AEM 내의 다양한 기능입니다.
>* **콘텐츠 조각**&#x200B;은 정의 및 구조를 갖지만 추가적인 시각적 디자인 및/또는 레이아웃을 포함하지 않는 에디토리얼 콘텐츠입니다. 텍스트, 숫자, 날짜 등과 같은 구조화된 데이터에 액세스하는 데 사용할 수 있습니다.
>* **경험 조각**&#x200B;은 전체적으로 배치된 콘텐츠, 즉 웹 페이지 조각입니다.
>
>경험 조각은 콘텐츠 조각 형태로 콘텐츠를 포함할 수 있지만 반대로는 불가능합니다.
>
>자세한 내용은 [AEM의 콘텐츠 조각 및 경험 조각 이해](https://experienceleague.adobe.com/docs/experience-manager-learn/sites/content-fragments/understand-content-fragments-and-experience-fragments.html#content-fragments)를 참조하십시오.

이 페이지와 다음 페이지에서는 콘텐츠 조각 생성, 구성, 관리 및 사용을 위한 작업을 다룹니다.

* [인스턴스에 대해 콘텐츠 조각 기능 활성화](/help/sites-cloud/administering/content-fragments/setup.md)
* [콘텐츠 조각 모델](/help/sites-cloud/administering/content-fragments/content-fragment-models.md) - 모델 활성화, 생성 및 정의
* [콘텐츠 조각 만들기](/help/sites-cloud/administering/content-fragments/managing.md#creating-a-content-fragment)(콘텐츠 조각 콘솔 사용)

조각이 만들어지면 다음과 같은 작업을 수행할 수 있습니다.

* [콘텐츠 조각 콘솔 사용](/help/sites-cloud/administering/content-fragments/managing.md) - 조각 액세스, (미리보기 또는 프로덕션에) 게시 및 참조
* [콘텐츠 조각 편집기 사용](/help/sites-cloud/administering/content-fragments/authoring.md) - 조각 편집, (미리보기 또는 프로덕션에) 게시 및 참조
* 편집기를 사용하여 콘텐츠 조각의 구조 [분석](/help/sites-cloud/administering/content-fragments/analysis.md)
* [Headless 방식으로 애플리케이션에 게재하기 위해 GraphQL을 사용하여 조각에 액세스합니다](/help/sites-cloud/administering/content-fragments/content-delivery-with-graphql.md).
* [또는 페이지를 작성하는 데 조각을 사용합니다.](/help/sites-cloud/authoring/fundamentals/content-fragments.md)

>[!NOTE]
>
>이 페이지는 다음과 함께 읽을 수 있습니다.
>
>* [콘텐츠 조각 사용자 정의 및 확장](/help/implementing/developing/extending/content-fragments-customizing.md)
>* [콘텐츠 조각 렌더링용 구성 요소 구성](/help/implementing/developing/extending/content-fragments-configuring-components-rendering.md)
>* [AEM Assets HTTP API의 콘텐츠 조각 지원](/help/assets/content-fragments/assets-api-content-fragments.md)
>* [콘텐츠 조각과 함께 사용하기 위한 AEM GraphQL API](/help/headless/graphql-api/content-fragments.md)
>* [콘텐츠 조각을 사용하여 페이지 작성](/help/sites-cloud/authoring/fundamentals/content-fragments.md)

## 기본과 변형 {#main-and-variations}

변형은 AEM 콘텐츠 조각의 중요한 기능입니다. 특정 채널 및 시나리오에서 사용할 **기본** 콘텐츠의 사본을 만들고 편집할 수 있어 Headless 콘텐츠 게재와 페이지 작성을 보다 유연하게 해 줍니다.

* **기본**

   * **기본**&#x200B;은 그러한 변형이 아니라 모든 변형의 기초입니다.
   * 조각의 필수 부분

      * 모든 콘텐츠 조각에는 하나의 **기본** 인스턴스가 있습니다.
      * **기본**&#x200B;은 삭제할 수 없습니다.

   * **기본**&#x200B;은 **[변형](/help/sites-cloud/administering/content-fragments/authoring.md#variations)** 아래의 조각 편집기에서 액세스할 수 있습니다.

  >[!NOTE]
  >
  >**자산** 콘솔에서 사용할 수 있는 편집기에서 **기본**&#x200B;을 **마스터**&#x200B;로 레이블 지정합니다.

* **변형**

   * 에디토리얼 목적에 맞는 조각 텍스트의 표현물은 채널과 관련을 지을 수 있지만, 의무적이지는 않으며, 임시적 로컬 수정용일 수도 있습니다.
   * **기본**&#x200B;의 사본으로 만들어지지만 필요에 따라 편집할 수 있습니다. 종종 변형 간에 콘텐츠가 겹치게 됩니다.
   * 왼쪽 패널에서 조각 작성 중에 정의할 수 있습니다.
   * 조각 내에 저장되므로 콘텐츠 사본 살포를 방지할 수 있습니다.
   * 변형은 **기본**&#x200B;과 [비교하여 동기화](/help/sites-cloud/administering/content-fragments/authoring.md#compare-and-synchronize-rich-text)될 수 있습니다.
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
>AEM은 조각 콘텐츠 번역도 지원합니다. 자세한 내용은 [자산 번역](/help/assets/translate-assets.md)을 참조하십시오.

## 콘텐츠 유형 {#content-type}

콘텐츠 조각은

* **사이트** 기능입니다.

* **자산**&#x200B;으로 저장됩니다.

   * 콘텐츠 조각(및 그 변형)은 [콘텐츠 조각 콘솔에서 만들고 유지 관리할 수 있습니다](/help/sites-cloud/administering/content-fragments/managing.md#content-fragments-console).
   * [콘텐츠 조각 편집기](/help/sites-cloud/administering/content-fragments/authoring.md)에서 작성 및 편집됩니다.

* [AEM GraphQL API](/help/headless/graphql-api/content-fragments.md)를 사용하여 콘텐츠 게재에 액세스할 수 있습니다.

* [콘텐츠 조각 구성 요소(참조 구성 요소)를 통해 페이지 편집기](/help/sites-cloud/authoring/fundamentals/content-fragments.md)에서 사용 가능합니다.

   * [콘텐츠 조각 핵심 구성 요소](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/wcm-components/content-fragment-component.html)는 페이지 작성자가 사용할 수 있습니다. 이를 통해 페이지 작성자는 HTML 또는 JSON 포맷으로 필요한 콘텐츠 조각을 참조 및 게재할 수 있습니다.

콘텐츠 조각은 다음과 같은 콘텐츠 구조입니다.

* 레이아웃이나 디자인이 없습니다(텍스트 필드에서 텍스트 서식 지정 가능).
* 게재 메커니즘(예: 페이지 또는 채널)에 독립적입니다.
* 하나 이상의 [구성 부분](#constituent-parts-of-a-content-fragment)을 포함합니다.
* [이미지를 포함하거나 이미지에 연결](#fragments-with-visual-assets)할 수 있습니다.

### 시각적 자산이 있는 조각 {#fragments-with-visual-assets}

작성자가 콘텐츠를 더 잘 제어할 수 있도록 이미지를 콘텐츠 조각에 추가하거나 콘텐츠 조각과 통합할 수 있습니다.

자산은 각각 고유한 장점이 있는 여러 가지 방법으로 콘텐츠 조각에 사용할 수 있습니다.

* **콘텐츠 참조**&#x200B;로서 사용
* **여러 줄 텍스트 필드** 내부에서 사용

### 콘텐츠 조각을 구성하는 부분 {#constituent-parts-of-a-content-fragment}

콘텐츠 조각 자산은 다음 부분으로 구성됩니다(직접 또는 간접적으로).

* **조각 요소**

   * 요소는 콘텐츠를 포함하는 데이터 필드와 관련이 있습니다.
   * [콘텐츠 조각 모델](/help/sites-cloud/administering/content-fragments/content-fragment-models.md)을 사용하여 콘텐츠 조각을 만듭니다. 모델에 지정된 요소(필드)는 조각의 구조를 정의합니다. 이러한 요소(필드)는 다양한 데이터 유형일 수 있습니다.

* **조각 단락**

   * 개별 엔티티로 구분된 텍스트 블록(종종 여러 줄)입니다.

   * 페이지 작성 중 콘텐츠를 제어할 수 있도록 해 줍니다.

* **조각 메타데이터**

   * [자산 메타데이터 스키마](/help/assets/metadata-schemas.md)를 사용합니다.
   * 다음 경우에 태그를 만들 수 있습니다.

      * 조각을 만들고 작성할 때
      * 아니면 나중에 조각 편집기에 있을 때 [속성을 보거나 편집](/help/sites-cloud/administering/content-fragments/authoring.md#view-properties-tags)하는 경우

  >[!CAUTION]
  >
  >메타데이터 처리 프로필은 콘텐츠 조각에 적용되지 않습니다.

  >[!CAUTION]
  >
  >콘텐츠 조각 모델은 종종 **제목**&#x200B;과 **설명**&#x200B;으로 이름이 지정된 데이터 필드를 정의할 수 있습니다. 이 두 필드가 존재하는 경우, 해당 필드는 사용자 정의 필드이고 편집기의 콘텐츠 영역에서 업데이트할 수 있습니다.
  >
  >또한 콘텐츠 조각과 변형에는 **제목**&#x200B;과 **설명**&#x200B;이라는 메타데이터(속성) 필드가 있습니다. 이 두 메타데이터 필드는 콘텐츠 조각과 변형의 필수 부분이며 처음 조각이 생성될 때 정의됩니다. 해당 필드는 편집기의 속성/메타데이터 영역에서 업데이트할 수 있습니다.

* **[기본](#main-and-variations)**
* **[변형](#main-and-variations)**

### 조각에 필요한 사항 {#required-by-fragments}

콘텐츠 조각을 만드는 데 필요한 사항은 다음과 같습니다.

* **콘텐츠 모델**

   * [구성 브라우저를 사용하여 활성화](/help/sites-cloud/administering/content-fragments/setup.md)됩니다.
   * [도구를 사용하여 생성](/help/sites-cloud/administering/content-fragments/content-fragment-models.md)됩니다.
   * [조각 생성](/help/sites-cloud/administering/content-fragments/managing.md#creating-content-fragments)에 필요합니다.
   * 조각의 구조(제목, 콘텐츠 요소, 태그 정의)를 정의합니다.
   * 콘텐츠 조각 모델 정의에는 제목과 하나의 데이터 요소가 필요하며, 기타 모든 항목은 선택 사항입니다.
   * 모델은 기본 콘텐츠(해당되는 경우)를 정의할 수 있습니다.
   * 조각 콘텐츠를 작성할 때 작성자는 정의된 구조를 변경할 수 없습니다. 단, 조각 편집기에서는 모델 편집기를 열 수 있습니다.
   * 종속 콘텐츠 조각을 만든 후 모델을 변경하면 해당 콘텐츠 조각에 영향을 줄 수 있습니다.

Headless 콘텐츠 게재에 콘텐츠 조각을 사용하려면 다음 사항이 필요합니다.

* 필요한 콘텐츠를 요청하는 경우 [GraphQL 쿼리](/help/headless/graphql-api/content-fragments.md)
* 그런 다음 이 콘텐츠를 사용하여 AEM용 SPA를 직접 개발할 수 있습니다. 자세한 내용은 다음 문서를 검토합니다.

   * [SPA WKND 튜토리얼](/help/implementing/developing/hybrid/wknd-tutorial.md)
   * [React를 사용하여 시작하기](/help/implementing/developing/hybrid/getting-started-react.md)
   * [Angular를 사용하여 시작하기](/help/implementing/developing/hybrid/getting-started-angular.md)

페이지 작성에 콘텐츠 조각을 사용하려면 다음 사항이 필요합니다.

* 한 개의 **콘텐츠 조각 구성 요소**

   * 조각을 HTML 및/또는 JSON 형식으로 게재하는 데 중요합니다.
   * [페이지에서 조각을 참조](/help/sites-cloud/authoring/fundamentals/content-fragments.md)하는 데 필요합니다.
   * 채널 등과 같이 조각의 레이아웃 및 게재를 담당합니다.
   * 조각은 레이아웃을 정의하고 일부 또는 모든 요소/변형 및 관련 콘텐츠를 게재하기 위해 하나 이상의 전용 구성 요소를 필요로 합니다.
   * 작성 중인 페이지에 조각을 드래그하면 필요한 구성 요소가 자동으로 연결됩니다.
   * [콘텐츠 조각 핵심 구성 요소](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/wcm-components/content-fragment-component.html)을 참조하십시오.

## 사용 예 {#example-usage}

요소 및 변형을 포함한 조각을 사용하여 여러 채널용의 일관된 콘텐츠를 만들 수 있습니다. 조각을 디자인할 때에는 어디에 사용할 것인지 고려해야 합니다.

### WKND 샘플 {#wknd-sample}

제공되는 [WKND 사이트 및 공유 WKND](/help/implementing/developing/introduction/develop-wknd-tutorial.md) 샘플은 AEM as a Cloud Service에 대해 학습하는 데 도움이 됩니다.

<!-- CHECK: which links can/should be used these days? -->

WKND 프로젝트에는 다음이 포함되어 있습니다.

* 콘텐츠 조각 모델은 다음에서 사용할 수 있습니다.

   * `.../libs/dam/cfm/models/console/content/models.html/conf/wknd`

   * `.../ui#/aem/libs/dam/cfm/models/console/content/models.html/conf/wknd-shared`

* 콘텐츠 조각(및 기타 콘텐츠)은 다음에서 사용할 수 있습니다.

   * `.../assets.html/content/dam/wknd/en`
