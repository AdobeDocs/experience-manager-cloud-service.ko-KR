---
title: 콘텐츠 조각을 사용한 작업
description: Adobe Experience Manager(AEM)의 컨텐츠 조각을 Cloud Service으로 사용하여 페이지에 영향을 받지 않는 컨텐츠를 디자인, 제작, 조정 및 사용하는 방법을 알아봅니다.
translation-type: tm+mt
source-git-commit: a5b0d8789a50974c5b633feb5a84824b5999916c
workflow-type: tm+mt
source-wordcount: '1828'
ht-degree: 3%

---


# 콘텐츠 조각을 사용한 작업{#working-with-content-fragments}

With Adobe Experience Manager (AEM) as a Cloud Service, Content Fragments allow you to design, create, curate and [publish page-independent content](/help/sites-cloud/authoring/fundamentals/content-fragments.md). 여러 위치/여러 채널에서 사용할 수 있는 컨텐츠를 준비할 수 있습니다.

콘텐츠 조각에 구조화된 콘텐츠 포함:

* 결과 조각의 구조를 미리 정의하는 [컨텐츠 조각](/help/assets/content-fragments/content-fragments-models.md)모델을 기반으로 합니다.

AEM 핵심 구성 요소의 JSON(Sling Model) 내보내기 기능을 사용하여 컨텐츠 조각을 JSON 포맷으로 전달할 수도 있습니다. 이 전달 형식:

* 구성 요소를 사용하여 전달할 조각의 요소를 관리할 수 있습니다.
* API 전달에 사용되는 페이지에 여러 개의 컨텐츠 조각 핵심 구성 요소를 추가하여 일괄 배달을 허용합니다.

이 페이지와 다음 페이지에서는 컨텐츠 조각을 생성, 구성 및 유지 관리하는 작업을 다룹니다.

* [컨텐츠 조각 관리](/help/assets/content-fragments/content-fragments-managing.md) - 컨텐츠 조각 만들기; 그런 다음 편집, 게시 및 참조
* [컨텐츠 조각 모델](/help/assets/content-fragments/content-fragments-models.md) - 모델 활성화, 생성 및 정의
* [변형 - 조각 컨텐츠](/help/assets/content-fragments/content-fragments-variations.md) 작성 - 조각 컨텐츠를 작성하고 기본 변형된
* [마크다운](/help/assets/content-fragments/content-fragments-markdown.md) - 조각에 대한 마크다운 구문 사용
* [관련 컨텐츠 사용](/help/assets/content-fragments/content-fragments-assoc-content.md) - 관련 컨텐츠 추가
* [메타데이터 - 조각 속성](/help/assets/content-fragments/content-fragments-metadata.md) - 조각 속성 보기 및 편집

>[!NOTE]
>
>이러한 페이지는 컨텐츠 조각으로 [페이지 작성과 함께 읽어야 합니다](/help/sites-cloud/authoring/fundamentals/content-fragments.md).

통신 채널의 수는 매년 증가하고 있다. 일반적으로 채널은 다음 중 하나로 배달 메커니즘을 참조합니다.

* 물리적 채널; 예: 데스크탑, 모바일
* 실제 채널에서의 전달 방식 예: &quot;제품 세부 정보 페이지&quot;, 데스크탑용 &quot;제품 카테고리 페이지&quot; 또는 모바일용 &quot;모바일 웹&quot;, &quot;모바일 앱&quot;

그러나 모든 채널에 대해 동일한 컨텐츠를 사용하지 않으려는 경우 특정 채널에 따라 컨텐츠를 최적화해야 합니다.

컨텐츠 조각을 사용하면 다음을 수행할 수 있습니다.

* 다양한 채널에서 효율적으로 타겟 고객에게 도달하는 방법을 고려해 보십시오.
* 채널 중립적인 편집 컨텐츠 제작 및 관리
* 다양한 채널을 위한 컨텐츠 풀 구축
* 특정 채널에 맞는 다양한 컨텐츠 디자인
* 에셋(혼합 미디어 조각)을 삽입하여 텍스트에 이미지를 추가합니다.

이러한 컨텐츠 조각을 취합하여 다양한 채널을 통해 경험을 제공할 수 있습니다.

## 컨텐츠 조각 및 컨텐츠 서비스 {#content-fragments-and-content-services}

AEM Content Services는 웹 페이지에 중점을 둔 수준에서 AEM 내/에서 컨텐츠 설명 및 전달을 일반화하기 위해 고안되었습니다.

모든 클라이언트가 사용할 수 있는 표준화된 방법을 사용하여 기존 AEM 웹 페이지가 아닌 채널에 컨텐츠를 배달합니다. 이러한 채널에는 다음이 포함될 수 있습니다.

* 단일 페이지 애플리케이션
* 기본 모바일 애플리케이션
* AEM 외부에 있는 기타 채널 및 터치 포인트

배달은 JSON 내보내기 도구를 사용하여 JSON 형식으로 만들어집니다.

AEM 컨텐츠 조각을 사용하여 구조화된 컨텐츠를 설명하고 관리할 수 있습니다. 구조화된 컨텐츠는 다양한 컨텐츠 유형을 포함할 수 있는 모델에서 정의됩니다. 텍스트, 숫자 데이터, 부울, 날짜 및 시간 등을 포함합니다.

그런 다음 AEM 핵심 구성 요소의 JSON 내보내기 기능과 함께 구조화된 이 컨텐츠를 사용하여 AEM 페이지 이외의 채널에 AEM 컨텐츠를 전달할 수 있습니다.

>[!NOTE]
>
>**컨텐츠 조각** 및 **[경험 조각](/help/sites-cloud/authoring/fundamentals/experience-fragments.md)**은 AEM 내의 다양한 기능입니다.
>* **컨텐츠 조각은** 편집 컨텐츠로 텍스트, 번호, 날짜 등 구조화된 데이터에 액세스하는 데 사용할 수 있습니다. 정의 및 구조가 있지만 추가적인 시각적 디자인 및/또는 레이아웃이 없는 순수 컨텐츠입니다.
>* **경험 조각**&#x200B;은 전체적으로 배치된 컨텐츠, 즉 웹 페이지 조각입니다.

>
>
경험 조각은 컨텐츠 조각 형태로 컨텐츠를 포함할 수 있지만 반대로는 불가능합니다.
>
>자세한 내용은 AEM의 [컨텐츠 조각 및 경험 조각 이해를 참조하십시오](https://helpx.adobe.com/experience-manager/kt/platform-repository/using/content-fragments-experience-fragments-article-understand.html).

>[!NOTE]
>
>또한 AEM은 조각 컨텐츠 변환을 지원합니다. 자세한 내용은 컨텐츠 조각에 대한 번역 프로젝트 만들기를 참조하십시오.

<!--
>[!NOTE]
>
>AEM also supports the translation of fragment content. See [Creating Translation Projects for Content Fragments](/help/assets/creating-translation-projects-for-content-fragments.md) for further information.
-->

## 컨텐트 유형 {#content-type}

컨텐츠 조각:

* 자산으로 **저장**:

   * 콘텐츠 조각(및 그 변형)은 **자산** 콘솔에서 만들고 유지 관리할 수 있습니다.
   * 컨텐츠 조각 편집기에서 작성 및 편집됨.

* 컨텐츠 조각 구성 요소 [(참조 구성 요소)를 통해](/help/sites-cloud/authoring/fundamentals/content-fragments.md) 페이지 편집기에서 사용됩니다.

   * 컨텐츠 **조각** 구성 요소는 페이지 작성자가 사용할 수 있습니다. 이를 통해 HTML 또는 JSON 형식으로 필요한 컨텐츠 조각을 참조하고 전달할 수 있습니다.

컨텐츠 조각은 다음과 같은 컨텐츠 구조입니다.

* 레이아웃이나 디자인이 없는 경우(일부 텍스트 서식은 리치 텍스트 모드에서 가능)
* 하나 이상의 구성 [부분을 포함합니다](#constituent-parts-of-a-content-fragment).
* 이미지를 [포함하거나 연결할 수 있습니다](#fragments-with-visual-assets).
* 페이지에서 참조될 [때 중간](#in-between-content-when-page-authoring-with-content-fragments) 컨텐츠를 사용할 수 있습니다.

* 전달 메커니즘(예: 페이지, 채널)과 독립적입니다.

### 시각적 자산이 있는 조각 {#fragments-with-visual-assets}

작성자가 컨텐츠를 더 잘 제어할 수 있도록 컨텐츠 조각에 이미지를 추가하거나 통합할 수 있습니다.

자산은 여러 가지 방법으로 컨텐츠 조각과 함께 사용할 수 있습니다. each with its own advantage:

* **자산을** 조각에 삽입(혼합 미디어 조각)

   * 조각의 필수 부분입니다(컨텐츠 조각의 [구성 요소 참조](#constituent-parts-of-a-content-fragment)).
   * 자산의 위치를 정의합니다.
   * 자세한 [내용은 조각 편집기에서](/help/assets/content-fragments/content-fragments-variations.md#inserting-assets-into-your-fragment) 조각에 자산 삽입을 참조하십시오.

   >[!NOTE]
   >
   >컨텐츠 조각 자체에 삽입된 시각적 자산은 이전 단락에 첨부됩니다. 조각을 페이지에 추가하면 중간 컨텐츠가 추가되면 해당 단락을 기준으로 해당 자산이 이동됩니다.

* **관련 컨텐츠**

   * 조각에 연결되어 있습니다. 하지만 조각의 고정 부분이 아닙니다(컨텐츠 조각의 [구성 요소 참조](#constituent-parts-of-a-content-fragment)).
   * 위치를 유연하게 지정할 수 있습니다.
   * 페이지에서 조각을 사용할 때 (중간 컨텐츠로) 쉽게 사용할 수 있습니다.
   * 자세한 [내용은 관련](/help/assets/content-fragments/content-fragments-assoc-content.md) 컨텐츠를 참조하십시오.

* 페이지 편집기의 **자산 브라우저에서** 사용할 수 있는 자산

   * 에셋을 선택할 수 있는 완벽한 유연성
   * 위치를 유연하게 지정할 수 있습니다.
   * 특정 조각에 대해 승인되는 개념을 제공하지 않습니다.
   * 자세한 내용은 [자산](/help/sites-cloud/authoring/fundamentals/environment-tools.md#assets-browser) 브라우저를 참조하십시오.

### 컨텐츠 조각의 구성 요소 {#constituent-parts-of-a-content-fragment}

컨텐츠 조각 자산은 다음 부분으로 구성됩니다(직접 또는 간접적으로).

* **조각 요소**

   * 요소는 컨텐츠를 포함하는 데이터 필드에 상관 관계를 맺습니다.
   * 컨텐츠 모델을 사용하여 컨텐츠 조각을 생성합니다. 모델에 지정된 요소(필드)는 조각의 구조를 정의합니다. 이러한 요소(필드)는 다양한 데이터 유형일 수 있습니다.

* **조각 단락**

   * 개별 엔티티로 구분된 여러 줄로 된 텍스트 블록.

   * 리치 텍스트 [및](/help/assets/content-fragments/content-fragments-variations.md#rich-text) 마크다운 [](/help/assets/content-fragments/content-fragments-variations.md#markdown) 모드에서 단락 서식을 머리글로 지정할 수 있습니다. 이 경우 단락을 모두 하나로 묶습니다.

   * 페이지 작성 중 컨텐츠 컨트롤을 활성화합니다.

* **조각에 삽입된 자산(혼합 미디어 조각)**

   * 실제 조각에 삽입되고 조각의 내부 컨텐츠로 사용된 자산(이미지)
   * 조각의 단락 시스템에 포함됩니다.
   * 페이지에서 [조각을 사용/참조할 때 형식을 지정할 수 있습니다](/help/sites-cloud/authoring/fundamentals/content-fragments.md).
   * 조각 편집기를 사용하여 조각 내에서만 추가, 삭제 또는 이동할 수 있습니다. 이러한 작업은 페이지 편집기에서 수행할 수 없습니다.
   * 조각 편집기에서 리치 텍스트 형식을 사용하는 조각에만 추가, 삭제 또는 [이동할 수 있습니다](/help/assets/content-fragments/content-fragments-variations.md#inserting-assets-into-your-fragment).
   * 여러 줄 텍스트 요소(모든 조각 유형)에만 추가할 수 있습니다.
   * 앞에 있는 텍스트(단락)에 첨부됩니다.

   >[!CAUTION]
   >
   >실수로 일반 텍스트 형식으로 전환하여 조각에서 제거할 수 있습니다.

   >[!NOTE]
   >
   >또한 페이지에서 조각을 사용할 때 자산을 [추가(중간) 컨텐츠로](/help/sites-cloud/authoring/fundamentals/content-fragments.md#using-associated-content) 추가할 수 있습니다. 관련 컨텐츠 또는 자산 브라우저의 자산을 사용합니다.

* **관련 컨텐츠**

   * 조각 외부 컨텐츠이지만 편집과 연관성이 있는 컨텐츠입니다. 일반적으로 이미지, 비디오 또는 기타 조각.
   * 컬렉션 내의 개별 자산은 페이지에 추가될 때 페이지 편집기의 조각과 함께 사용할 수 있습니다. 즉, 특정 채널의 요구 사항에 따라 선택 사항입니다.
   * 자산은 컬렉션을 통해 조각에 [연결됩니다](/help/assets/content-fragments/content-fragments-assoc-content.md). 연결된 컬렉션은 작성자가 페이지를 작성할 때 사용할 자산을 결정할 수 있도록 해줍니다.

      * 컬렉션은 기본 컨텐츠로 조각에 연결하거나 조각 작성 도중 작성자가 연결할 수 있습니다.
      * [자산(DAM) 컬렉션은](/help/assets/manage-collections.md) 조각과 관련된 컨텐츠의 기본입니다.
   * 선택적으로 조각 자체를 컬렉션에 추가하여 추적을 지원할 수도 있습니다.

* **조각 메타데이터**

   * 자산 [메타데이터 스키마를 사용합니다](/help/assets/metadata-schemas.md).
   * 다음과 같은 경우에 태그를 만들 수 있습니다.

      * 조각 만들기 및 작성
      * 또는 이후:

         * 콘솔에서 조각 **속성** 보기/편집
         * 조각 편집기에서 **메타데이터** 편집

   >[!CAUTION]
   >
   >메타데이터 처리 프로필은 컨텐츠 조각에 적용되지 않습니다.

* **마스터**

   * 조각의 필수 부분

      * 모든 컨텐츠 조각에는 하나의 인스턴스가 기본 있습니다.
      * 삭제할 수 기본 없습니다.
   * 변형 아래의 조각 편집기에서 기본 액세스할 수 **[있습니다](/help/assets/content-fragments/content-fragments-variations.md)**.
   * 변형이 기본 아니라 모든 변형의 기초가 됩니다.


* **변형**

   * 편집 목적에 맞는 조각 텍스트 변환 채널과 관련될 수 있지만, 강제적이지 않으며, 임시 로컬 수정에 사용할 수도 있습니다.
   * 는 사본 **기본**&#x200B;로 생성되지만 필요에 따라 편집할 수 있습니다. 일반적으로 변형 자체 간에 내용이 겹치는 경우가 있습니다.
   * 조각 작성 중에 정의할 수 있습니다.
   * 조각 내에 저장되므로 컨텐츠 복사본 분산을 방지할 수 있습니다.
   * 컨텐츠가 업데이트된 기본 경우 변형기본을 [](/help/assets/content-fragments/content-fragments-variations.md#synchronizing-with-master) 과 동기화할 수 있습니다.
   * 사전 정의된 [길이로](/help/assets/content-fragments/content-fragments-variations.md#summarizing-text) 텍스트를 빠르게 자르기 위해 요약할 수 있습니다.
   * 조각 편집기의 [변형](/help/assets/content-fragments/content-fragments-variations.md) 탭에서 사용할 수 있습니다.

### 컨텐츠 조각으로 페이지 작성 시 중간 컨텐츠 {#in-between-content-when-page-authoring-with-content-fragments}

중간 컨텐츠:

* 컨텐츠 조각 작업 시 페이지 편집기에서 사용할 수 있습니다.
* 페이지에서 사용/참조되면 조각 [흐름 내에 추가된](/help/sites-cloud/authoring/fundamentals/content-fragments.md#adding-in-between-content) 추가 컨텐츠입니다.
* 컨텐츠 조각 작업 시 [페이지 편집기에서 사용할 수 있습니다](/help/sites-cloud/authoring/fundamentals/content-fragments.md).
* 중간 컨텐츠는 모든 조각에 추가할 수 있으며, 여기에서 하나의 요소만 볼 수 있습니다.
* 관련 컨텐츠는 해당 브라우저의 자산 및/또는 구성 요소처럼 사용할 수 있습니다.

>[!CAUTION]
>
>중간 컨텐츠는 페이지 컨텐츠이며, 컨텐츠 조각에 저장되지 않습니다.

### 조각에 필요 {#required-by-fragments}

필요한 컨텐츠 조각을 만들고 편집하고 사용하려면 다음을 수행하십시오.

* **콘텐츠 모델**

   * 활성화한 [다음 도구를 사용하여 만듭니다](/help/assets/content-fragments/content-fragments-models.md).
   * 조각 [을 만드는 데 필요합니다](/help/assets/content-fragments/content-fragments-managing.md#creating-content-fragments).
   * 조각(제목, 컨텐츠 요소, 태그 정의)의 구조를 정의합니다.
   * 콘텐츠 모델 정의는 제목과 하나의 데이터 요소가 필요합니다. 그 외의 모든 것은 선택 사항입니다.
   * 모델은 기본 컨텐트를 정의할 수 있습니다(해당되는 경우).
   * 작성자는 조각 컨텐츠를 작성할 때 정의된 구조를 변경할 수 없습니다.
   * 종속 컨텐츠 조각을 만든 후 모델에 대한 변경 사항은 해당 컨텐츠 조각에 영향을 줄 수 있습니다.

* **컨텐츠 조각 구성 요소**

   * 조각을 HTML 및/또는 JSON 형식으로 전달하는 데 도움이 됩니다.
   * 페이지에서 조각을 [참조하는 데 필요합니다](/help/sites-cloud/authoring/fundamentals/content-fragments.md).
   * 조각 레이아웃 및 배달 책임 채널 등
   * 조각을 사용하면 레이아웃을 정의하고 일부 또는 모든 요소/변형 및 관련 컨텐츠를 전달할 수 있는 하나 이상의 전용 구성 요소가 필요합니다.
   * 작성 중인 페이지로 조각을 드래그하면 필요한 구성 요소가 자동으로 연결됩니다.

## 사용 예 {#example-usage}

요소 및 변형을 포함한 조각을 사용하여 여러 채널에 일관된 컨텐츠를 만들 수 있습니다. 조각을 디자인할 때는 어디에 사용될 것인지 고려해야 합니다.

### WKND 샘플 {#wknd-sample}

Cloud Service [로 AEM에 대해 학습하는 데 도움이 되는 WKND 사이트](/help/implementing/developing/introduction/develop-wknd-tutorial.md) 샘플이 제공됩니다. 여기에는 샘플 조각이 포함되어 있으며 다음과 같이 볼 수 있습니다.

`hhttp://<host>:<port>/assets.html/content/dam/wknd/en/adventures`
