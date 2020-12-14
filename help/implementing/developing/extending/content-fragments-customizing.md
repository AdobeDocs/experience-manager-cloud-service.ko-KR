---
title: 컨텐츠 조각 사용자 지정 및 확장
description: 컨텐츠 조각은 표준 자산을 확장합니다.
translation-type: tm+mt
source-git-commit: 639bf1add463c0e62982a44ecdca834e2c7c53fe
workflow-type: tm+mt
source-wordcount: '1818'
ht-degree: 3%

---


# 컨텐츠 조각 사용자 지정 및 확장{#customizing-and-extending-content-fragments}

Adobe Experience Manager 내에서 Cloud Service으로 컨텐츠 조각은 표준 자산을 확장합니다.참조:

* [컨텐츠 조각 만들기 및 관리 ](/help/assets/content-fragments/content-fragments.md) 및 컨텐츠  [조각을 사용한 페이지 ](/help/sites-cloud/authoring/fundamentals/content-fragments.md) 작성을 참조하십시오.

* [자산 ](/help/assets/manage-digital-assets.md) 관리를 참조하십시오.

<!-- Removing the extend-asset-editor article for now as I'm unsure of its accuracy. Hence commenting this link.
* [Managing Assets](/help/assets/manage-digital-assets.md) and [Customizing and Extending the Asset Editor](/help/assets/extend-asset-editor.md) for further information about standard assets.
-->

## 아키텍처 {#architecture}

컨텐츠 조각의 기본 [구성 부분](/help/assets/content-fragments/content-fragments.md#constituent-parts-of-a-content-fragment)은 다음과 같습니다.

* *컨텐츠 조각*,
* 하나 이상의 *컨텐트 요소*,
* 하나 이상의 *컨텐트 변형*&#x200B;을 가질 수 있습니다.

개별 컨텐츠 조각은 컨텐츠 조각 모델을 기반으로 합니다.

* 컨텐츠 조각 모델은 컨텐츠 조각을 만들 때 해당 구조를 정의합니다.
* 조각이 모델을 참조합니다.따라서 모델에 대한 변경 사항은 종속 조각에 영향을 줄 수/미칠 수 있습니다.
* 모델은 데이터 유형이 내장되어 있습니다.
* 새 변형 등을 추가하는 함수는 그에 따라 조각을 업데이트해야 합니다.

   >[!NOTE]
   >
   >컨텐츠 조각을 표시/렌더링하려면 계정에 모델에 대한 `read` 권한이 있어야 합니다.

   >[!CAUTION]
   >
   >기존 컨텐츠 조각 모델에 대한 모든 변경 사항은 종속 조각에 영향을 줄 수 있습니다.이렇게 하면 해당 조각에 고아 속성이 생길 수 있습니다.

### 자산 {#integration-of-sites-with-assets}과 사이트 통합

CFM(Content Fragment Management)은 다음과 같은 AEM Assets의 일부입니다.

* 컨텐츠 조각은 자산입니다.
* 기존 자산 기능을 사용합니다.
* 자산(관리 콘솔 등)과 완전히 통합됩니다.

컨텐츠 조각은 다음과 같이 사이트 기능으로 간주됩니다.

* 페이지를 작성할 때 사용됩니다.

#### 콘텐츠 조각을 자산 {#mapping-content-fragments-to-assets}에 매핑

![자산에 대한 컨텐츠 조각](assets/content-fragment-to-assets.png)

컨텐츠 조각 모델을 기반으로 하는 컨텐츠 조각은 단일 자산에 매핑됩니다.

* 모든 콘텐츠는 자산의 `jcr:content/data` 노드 아래에 저장됩니다.

   * 요소 데이터는 마스터 하위 노드 아래에 저장됩니다.
      `jcr:content/data/master`

   * 변형은 변형의 이름을 가진 하위 노드 아래에 저장됩니다.
예:`jcr:content/data/myvariation`

   * 각 요소의 데이터는 요소 이름을 가진 속성으로 각 하위 노드에 저장됩니다.
예: `text` 요소의 컨텐츠가 `jcr:content/data/master`의 속성 `text`으로 저장됩니다.

* 메타데이터 및 관련 콘텐트가 `jcr:content/metadata` 아래에 저장됩니다.
일반 메타데이터로 간주되지 않고 
`jcr:content`

#### 자산 위치 {#asset-location}

표준 자산과 마찬가지로 컨텐츠 조각은 다음 아래에서 보관됩니다.

`/content/dam`

#### 자산 권한 {#asset-permissions}

자세한 내용은 [컨텐츠 조각 - 고려 사항 삭제](/help/assets/content-fragments/content-fragments-delete.md)를 참조하십시오.

#### 기능 통합 {#feature-integration}

자산 코어와 통합하려면:

* CFM(컨텐츠 조각 관리) 기능은 자산 코어를 기반으로 구축됩니다.

* CFM은 카드/열/목록 보기의 항목에 대한 자체 구현을 제공합니다.이러한 플러그인을 기존 자산 컨텐츠 렌더링 구현에 연결합니다.

* 여러 자산 구성 요소가 컨텐츠 조각에 맞게 확장되었습니다.

### {#using-content-fragments-in-pages} 페이지에서 컨텐츠 조각 사용

>[!CAUTION]
>
>[컨텐츠 조각 구성 요소는 핵심 구성 요소](https://docs.adobe.com/content/help/ko-KR/experience-manager-core-components/using/components/content-fragment-component.html)의 일부입니다. 자세한 내용은 [핵심 구성 요소 개발](https://docs.adobe.com/content/help/en/experience-manager-core-components/using/developing/developing.html)을 참조하십시오.

컨텐츠 조각은 다른 자산 유형과 마찬가지로 AEM 페이지에서 참조할 수 있습니다. AEM은 **[컨텐츠 조각 핵심 구성 요소](https://docs.adobe.com/content/help/en/experience-manager-core-components/using/components/content-fragment-component.html)** 구성 요소를 제공합니다. 이 구성 요소는 페이지](/help/sites-cloud/authoring/fundamentals/content-fragments.md#adding-a-content-fragment-to-your-page)에 컨텐츠 조각을 포함할 수 있게 합니다. [ 이 **[컨텐츠 조각](https://docs.adobe.com/content/help/en/experience-manager-core-components/using/developing/developing.html)** 핵심 구성 요소를 확장할 수도 있습니다.

* 구성 요소는 `fragmentPath` 속성을 사용하여 실제 컨텐츠 조각을 참조합니다. `fragmentPath` 속성은 다른 자산 유형의 속성과 유사한 방식으로 처리됩니다.예를 들어 컨텐츠 조각을 다른 위치로 이동할 때

* 구성 요소를 사용하면 표시할 변형을 선택할 수 있습니다.

* 또한 여러 단락을 선택하여 출력을 제한할 수 있습니다.예를 들어 다중 열 출력에 사용할 수 있습니다.

* 구성 요소는 중간 컨텐츠를 허용합니다.

   * 여기에서 구성 요소를 사용하여 다른 자산(이미지 등)을 배치할 수 있습니다. 를 참조하십시오.

   * 중간 컨텐츠의 경우 다음을 수행해야 합니다.

      * 불투명한 참조 가능성을 인식하다.중간 컨텐츠(페이지를 작성할 때 추가됨)는 옆에 배치된 단락에 대해 고정된 관계가 없습니다. 중간 컨텐츠의 위치가 상대 위치를 잃기 전에 새 단락(컨텐츠 조각 편집기에서)을 삽입하십시오

      * 추가 매개 변수(예: 변형 및 단락 필터)를 고려하여 페이지에서 렌더링되는 내용을 구성합니다.

>[!NOTE]
>
>**컨텐츠 조각 모델:**
>
>컨텐츠 조각을 페이지에서 사용하면 컨텐츠 조각을 기반으로 하는 컨텐츠 조각 모델이 참조됩니다.
>
>즉, 페이지를 게시할 때 모델이 게시되지 않은 경우 플래그가 지정되고 모델이 페이지와 함께 게시될 리소스에 추가됩니다.

### 다른 프레임워크 {#integration-with-other-frameworks}와의 통합

컨텐츠 조각은 다음과 통합할 수 있습니다.

* **번역**

   컨텐츠 조각은 AEM 번역 워크플로우와 완전히 통합됩니다. 이것은 건축적 수준에서 다음을 의미합니다.

   * 컨텐츠 조각의 개별 변환은 실제로 개별 조각입니다.예를 들면 다음과 같습니다.

      * 서로 다른 언어 루트 아래 있습니다.관련 언어 루트 아래에서 동일한 상대 경로를 공유합니다.

         `/content/dam/<path>/en/<to>/<fragment>`

         vs.

         `/content/dam/<path>/de/<to>/<fragment>`
   * 규칙 기반 경로 외에도 컨텐츠 조각의 서로 다른 언어 버전 간에 더 이상 연결되지 않습니다.언어 변형을 탐색하는 방법을 UI에서 제공하지만 두 개의 개별 조각으로 처리됩니다.
   >[!NOTE]
   >
   >AEM 번역 워크플로우는 `/content`과(와) 연동됩니다.
   >
   >* 컨텐츠 조각 모델은 `/conf`에 있으므로 이러한 변환에 포함되지 않습니다. UI 문자열을 국제화할 수 있습니다.


* **메타데이터 스키마**

   * 컨텐츠 조각(re)은 표준 자산으로 정의할 수 있는 [메타데이터 스키마](/help/assets/metadata-schemas.md)를 사용합니다.

   * CFM은 고유한 특정 스키마를 제공합니다.

      `/libs/dam/content/schemaeditors/forms/contentfragment`

      필요한 경우 확장할 수 있습니다.

   * 각 스키마 양식이 조각 편집기와 통합됩니다.

## 컨텐츠 조각 관리 API - 서버측 {#the-content-fragment-management-api-server-side}

서버측 API를 사용하여 컨텐츠 조각에 액세스할 수 있습니다.참조:

[com.adobe.cq.dam.cfm](https://docs.adobe.com/content/help/en/experience-manager-cloud-service-javadoc/com/adobe/cq/dam/cfm/package-summary.html#package.description)

>[!CAUTION]
>
>콘텐츠 구조에 직접 액세스하는 대신 서버측 API를 사용하는 것이 좋습니다.

### 키 인터페이스 {#key-interfaces}

다음 3개의 인터페이스는 시작 지점으로 사용할 수 있습니다.

* **컨텐츠 조각** ([컨텐츠 조각](https://docs.adobe.com/content/help/en/experience-manager-cloud-service-javadoc/com/adobe/cq/dam/cfm/ContentFragment.html))

   이 인터페이스를 사용하면 추상적인 방식으로 컨텐츠 조각을 사용하여 작업할 수 있습니다.

   이 인터페이스는 다음 방법을 제공합니다.

   * 기본 데이터 관리(예: 이름 가져오기;get/set title/description)
   * 메타 데이터 액세스
   * 액세스 요소:

      * 목록 요소
      * 이름으로 요소 가져오기
      * 새 요소 만들기([Caveats](#caveats) 참조)

      * 요소 데이터에 액세스합니다(`ContentElement` 참조).
   * 조각에 대해 정의된 목록 변형
   * 전역적으로 새로운 변형 만들기
   * 관련 컨텐츠 관리:

      * 목록 컬렉션
      * 컬렉션 추가
      * 컬렉션 제거
   * 조각 모델에 액세스

   조각의 주요 요소를 나타내는 인터페이스는 다음과 같습니다.

   * **콘텐츠 요소** ([ContentElement](https://docs.adobe.com/content/help/en/experience-manager-cloud-service-javadoc/com/adobe/cq/dam/cfm/ContentElement.html))

      * 기본 데이터 가져오기(이름, 제목, 설명)
      * 콘텐츠 가져오기/설정
      * 요소의 변형 액세스:

         * 목록 변형
         * 이름별로 변형 가져오기
         * 새 변형 만들기([Caveats](#caveats) 참조)
         * 변형 제거([Caveze](#caveats) 참조)
         * 변형 데이터 액세스(`ContentVariation` 참조)
      * 변형을 해결하기 위한 단축키(지정한 변형을 요소에 사용할 수 없는 경우 몇 가지 추가 구현 관련 폴백 논리 적용)
   * **컨텐츠 변형** ([ContentVariation](https://docs.adobe.com/content/help/en/experience-manager-cloud-service-javadoc/com/adobe/cq/dam/cfm/ContentVariation.html))

      * 기본 데이터 가져오기(이름, 제목, 설명)
      * 콘텐츠 가져오기/설정
      * 마지막으로 수정한 정보를 기반으로 하는 단순 동기화

   3개의 인터페이스( `ContentFragment`, `ContentElement`, `ContentVariation`)가 모두 `Versionable` 인터페이스를 확장하여 컨텐츠 조각에 필요한 버전 관리 기능을 추가합니다.

   * 요소의 새 버전 만들기
   * 요소의 버전 목록
   * 버전 관리 요소의 특정 버전의 컨텐츠 가져오기







### 적응 - adaptTo() {#adapting-using-adaptto} 사용

다음을 조정할 수 있습니다.

* `ContentFragment` 다음을 적용할 수 있습니다.

   * `Resource` - 기본 Sling 리소스;기본 객체를  `Resource` 직접 업데이트하려면 객체를 다시  `ContentFragment` 구성해야 합니다.

   * `Asset` - 컨텐츠 조각을 나타내는 DAM  `Asset` 추상화객체를  `Asset` 직접 업데이트하려면 객체를 다시  `ContentFragment` 구성해야 합니다.

* `ContentElement` 다음을 적용할 수 있습니다.

   * [`ElementTemplate`](https://docs.adobe.com/content/help/en/experience-manager-cloud-service-javadoc/com/adobe/cq/dam/cfm/ElementTemplate.html) - 요소의 구조 정보에 액세스할 수 있습니다.

* [`FragmentTemplate`](https://docs.adobe.com/content/help/en/experience-manager-cloud-service-javadoc/com/adobe/cq/dam/cfm/FragmentTemplate.html)

* `Resource` 다음을 적용할 수 있습니다.

   * `ContentFragment`

### Caveze {#caveats}

다음 사항에 유의해야 합니다.

* 전체 API는 API JavaDoc에 별도로 명시되어 있지 않는 한 **변경 내용을 자동으로 지속하지 않도록 설계되었습니다.** 따라서 항상 각 요청의 리소스 해결 프로그램(또는 실제로 사용 중인 해결 프로그램)을 커밋해야 합니다.

* 추가 노력이 필요할 수 있는 작업:

   * `ContentFragment`에서 새 변형을 만드는 것이 좋습니다. 이렇게 하면 모든 요소가 이러한 변화를 공유하고 컨텐츠 구조에 새로 생성된 변형을 반영하기 위해 적절한 글로벌 데이터 구조를 필요에 따라 업데이트할 수 있습니다.

   * `ContentElement.removeVariation()`을 사용하여 요소를 통해 기존 변형을 제거해도 변형에 할당된 글로벌 데이터 구조가 업데이트되지 않습니다. 이러한 데이터 구조가 동기화된 상태를 유지하려면 `ContentFragment.removeVariation()` 대신 변형을 전체적으로 제거합니다.

## 컨텐츠 조각 관리 API - 클라이언트측 {#the-content-fragment-management-api-client-side}

>[!CAUTION]
>
>클라이언트측 API는 내부입니다.

### 추가 정보 {#additional-information}

다음을 참조하십시오.

* `filter.xml`

   컨텐츠 조각 관리에 대한 `filter.xml`이(가) Assets 핵심 컨텐츠 패키지와 겹치지 않도록 구성되었습니다.

## 세션 편집 {#edit-sessions}

>[!CAUTION]
>
>이 배경 정보를 고려하십시오. 저장소에서 *개인 영역*&#x200B;으로 표시되므로 여기에서 어떤 것도 변경할 수 없지만 경우에 따라 백그라운드에서 작동하는 방식을 이해하는 데 도움이 될 수 있습니다.

여러 보기(= HTML 페이지)를 확장할 수 있는 컨텐츠 조각을 편집하는 것은 원자적입니다. 이러한 원자적 다중 보기 편집 기능은 일반적인 AEM 개념이 아니므로 컨텐츠 조각은 *편집 세션*&#x200B;이라고 하는 것을 사용합니다.

사용자가 편집기에서 컨텐츠 조각을 열면 편집 세션이 시작됩니다. 사용자가 **저장** 또는 **취소**&#x200B;를 선택하여 편집기를 떠날 때 편집 세션이 종료됩니다.

기술적으로, 모든 편집은 다른 모든 AEM 편집과 마찬가지로 *라이브* 컨텐츠에서 수행됩니다. 편집 세션이 시작되면 편집되지 않은 현재 상태의 버전이 만들어집니다. 사용자가 편집을 취소하면 해당 버전이 복원됩니다. 사용자가 **저장**&#x200B;을 클릭하는 경우, 모든 편집이 *live* 콘텐트에서 실행되므로 모든 변경 내용이 이미 유지됩니다. 또한 **저장**&#x200B;을 클릭하면 일부 백그라운드 처리가 트리거됩니다(전체 텍스트 검색 정보 만들기 및/또는 혼합 미디어 자산 처리).

에지 사례에 대한 몇 가지 안전 조치가 있습니다.예를 들어 사용자가 편집 세션을 저장하거나 취소하지 않고 편집기를 떠나려고 할 경우 또한 주기적인 자동 저장을 사용하여 데이터 손실을 방지할 수 있습니다.
두 사용자는 동일한 컨텐츠 조각을 동시에 편집할 수 있으므로 다른 변경 사항을 덮어쓸 수 있습니다. 이를 방지하려면 조각에 DAM 관리의 *체크아웃* 작업을 적용하여 컨텐츠 조각을 잠가야 합니다.

## 예 {#examples}

### 예:기존 컨텐츠 조각 {#example-accessing-an-existing-content-fragment}에 액세스

이를 위해 API를 나타내는 리소스를 다음과 같이 적용할 수 있습니다.

`com.adobe.cq.dam.cfm.ContentFragment`

예:

```java
// first, get the resource
Resource fragmentResource = resourceResolver.getResource("/content/dam/fragments/my-fragment");
// then adapt it
if (fragmentResource != null) {
    ContentFragment fragment = fragmentResource.adaptTo(ContentFragment.class);
    // the resource is now accessible through the API
}
```

### 예:새 컨텐츠 조각 {#example-creating-a-new-content-fragment} 만들기

프로그래밍 방식으로 새 컨텐츠 조각을 만들려면
`FragmentTemplate`이(가) 모델 리소스에서 채택되었습니다.

예:

```java
Resource modelRsc = resourceResolver.getResource("...");
FragmentTemplate tpl = modelRsc.adaptTo(FragmentTemplate.class);
ContentFragment newFragment = tpl.createFragment(parentRsc, "A fragment name", "A fragment description.");
```

### 예:자동 저장 간격 지정 {#example-specifying-the-auto-save-interval}

구성 관리자(ConfMgr)를 사용하여 [자동 저장 간격](/help/assets/content-fragments/content-fragments-managing.md#save-cancel-and-versions)(초 단위)을 정의할 수 있습니다.

* 노드:`<conf-root>/settings/dam/cfm/jcr:content`
* 속성 이름: `autoSaveInterval`
* 유형: `Long`

* 기본값:`600`(10분);`/libs/settings/dam/cfm/jcr:content`에 정의됩니다.

자동 저장 간격을 5분으로 설정하려면 노드에서 속성을 정의해야 합니다.예를 들면 다음과 같습니다.

* 노드:`/conf/global/settings/dam/cfm/jcr:content`
* 속성 이름: `autoSaveInterval`

* 유형: `Long`

* 값:`300`(5분은 300초로 완료)

## 페이지 작성용 구성 요소 {#components-for-page-authoring}

자세한 내용은

* [핵심 구성 요소 - 컨텐츠 조각 구성 요소](https://docs.adobe.com/content/help/en/experience-manager-core-components/using/components/content-fragment-component.html) (권장)
