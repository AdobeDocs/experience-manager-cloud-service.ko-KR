---
title: 콘텐츠 조각 맞춤화 및 확장
description: 컨텐츠 조각은 표준 자산을 확장합니다.
exl-id: 58152d6e-21b6-4f45-a45c-0f46ee58825e
source-git-commit: ca849bd76e5ac40bc76cf497619a82b238d898fa
workflow-type: tm+mt
source-wordcount: '1811'
ht-degree: 3%

---

# 콘텐츠 조각 맞춤화 및 확장{#customizing-and-extending-content-fragments}

Adobe Experience Manager as a Cloud Service 내에서 컨텐츠 조각은 표준 자산을 확장합니다. 다음을 참조하십시오.

* [컨텐츠 조각 만들기 및 관리](/help/sites-cloud/administering/content-fragments/content-fragments.md) 및 [컨텐츠 조각으로 페이지 작성](/help/sites-cloud/authoring/fundamentals/content-fragments.md) 컨텐츠 조각에 대한 자세한 정보.

* [자산 관리](/help/assets/manage-digital-assets.md) 표준 자산에 대한 추가 정보.

## 아키텍처 {#architecture}

기본 [구성 부분](/help/sites-cloud/administering/content-fragments/content-fragments.md#constituent-parts-of-a-content-fragment) 컨텐츠 조각의 유형은 다음과 같습니다.

* A *컨텐츠 조각*,
* 하나 이상으로 구성 *컨텐츠 요소*,
* 하나 이상의 *컨텐츠 변형*.

개별 컨텐츠 조각은 컨텐츠 조각 모델을 기반으로 합니다.

* 컨텐츠 조각 모델은 컨텐츠 조각을 만들 때 컨텐츠 조각의 구조를 정의합니다.
* 조각은 모델을 참조합니다. 따라서 모델 변경 사항은 모든 종속 조각에 영향을 줄 수/있을 것입니다.
* 모델은 데이터 유형을 기반으로 합니다.
* 새 변형 등을 추가하는 함수는 그에 따라 조각을 업데이트해야 합니다.

   >[!NOTE]
   >
   >컨텐츠 조각을 표시/렌더링하려면 계정에 `read` 모델에 대한 권한.

   >[!CAUTION]
   >
   >기존 컨텐츠 조각 모델을 변경하면 종속된 조각이 영향을 받을 수 있습니다. 이로 인해 해당 조각에서 고아 속성이 생길 수 있습니다.

### 자산과 사이트 통합 {#integration-of-sites-with-assets}

CFM(컨텐츠 조각 관리)은 다음 방법으로 AEM Assets에 포함되어 있습니다.

* 컨텐츠 조각은 자산입니다.
* 기존 자산 기능을 사용합니다.
* 자산(관리 콘솔 등)과 완전히 통합됩니다.

컨텐츠 조각은 다음과 같이 사이트 기능으로 간주됩니다.

* 페이지를 작성할 때 사용됩니다.

#### 컨텐츠 조각을 자산에 매핑 {#mapping-content-fragments-to-assets}

![자산에 대한 컨텐츠 조각](assets/content-fragment-to-assets.png)

컨텐츠 조각 모델을 기반으로 하는 컨텐츠 조각은 단일 자산에 매핑됩니다.

* 모든 컨텐츠는 `jcr:content/data` 자산의 노드:

   * 요소 데이터는 마스터 하위 노드 아래에 저장됩니다.
      `jcr:content/data/master`

   * 변형은 변형의 이름을 전달하는 하위 노드 아래에 저장됩니다. 예 `jcr:content/data/myvariation`

   * 각 요소의 데이터는 각 하위 노드에 요소 이름을 사용하는 속성으로 저장됩니다. 예를 들어 요소의 컨텐츠가 `text` 는 속성으로 저장됩니다. `text` on `jcr:content/data/master`

* 메타데이터 및 관련 컨텐츠는 아래에 저장됩니다 `jcr:content/metadata`
일반 메타데이터로 간주되지 않고 
`jcr:content`

#### 자산 위치 {#asset-location}

표준 자산과 마찬가지로 컨텐츠 조각도 다음 위치에 유지됩니다.

`/content/dam`

#### 자산 권한 {#asset-permissions}

자세한 내용은 [컨텐츠 조각 - 삭제 고려 사항](/help/sites-cloud/administering/content-fragments/content-fragments-delete.md).

#### 기능 통합 {#feature-integration}

자산 코어와 통합하려면:

* CFM(컨텐츠 조각 관리) 기능은 자산 코어에서 빌드됩니다.

* CFM은 카드/열/목록 보기의 항목에 대한 자체 구현을 제공합니다. 이러한 플러그인은 기존 자산 콘텐츠 렌더링 구현에 연결됩니다.

* 여러 자산 구성 요소가 컨텐츠 조각에 맞게 확장되었습니다.

### 페이지에서 컨텐츠 조각 사용 {#using-content-fragments-in-pages}

>[!CAUTION]
>
>다음 [컨텐츠 조각 구성 요소는 핵심 구성 요소의 일부입니다](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/components/content-fragment-component.html). 자세한 내용은 [핵심 구성 요소 개발](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/developing.html) 자세한 내용

컨텐츠 조각은 다른 자산 유형처럼 AEM 페이지에서 참조할 수 있습니다. AEM에서 **[컨텐츠 조각 코어 구성 요소](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/components/content-fragment-component.html)** - a [페이지에 컨텐츠 조각을 포함할 수 있는 구성 요소](/help/sites-cloud/authoring/fundamentals/content-fragments.md#adding-a-content-fragment-to-your-page). 이를 확장할 수도 있습니다 **[컨텐츠 조각](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/developing.html)** 코어 구성 요소입니다.

* 구성 요소는 `fragmentPath` 실제 컨텐츠 조각을 참조하는 속성입니다. 다음 `fragmentPath` 속성은 다른 자산 유형의 속성과 유사한 방식으로 처리됩니다. 예를 들어 컨텐츠 조각을 다른 위치로 이동할 때.

* 구성 요소로 표시할 변형을 선택할 수 있습니다.

* 또한 출력을 제한하기 위해 다양한 단락을 선택할 수 있습니다. 예를 들어 다중 열 출력에 사용할 수 있습니다.

* 구성 요소는 중간 컨텐츠를 허용합니다.

   * 구성 요소로 다른 자산(이미지 등)을 배치할 수 있습니다. 를 반환합니다.

   * 중간 컨텐츠의 경우 다음을 수행해야 합니다.

      * 불안정한 참고의 가능성을 인식하다. 중간 컨텐츠(페이지를 작성할 때 추가됨)에는 옆에 배치된 단락과 고정된 관계가 없으며 중간 컨텐츠의 위치가 상대 위치를 잃게 되기 전에 새 단락(컨텐츠 조각 편집기에서)을 삽입합니다

      * 추가 매개 변수(예: 변형 및 단락 필터)를 고려하여 페이지에서 렌더링되는 항목을 구성하십시오

>[!NOTE]
>
>**콘텐츠 조각 모델:**
>
>페이지에서 컨텐츠 조각을 사용하면 컨텐츠 조각이 기반으로 하는 컨텐츠 조각 모델이 참조됩니다.
>
>즉, 페이지를 게시할 때 모델이 게시되지 않은 경우 이 플래그가 지정되고 모델이 페이지와 함께 게시될 리소스에 추가됩니다.

### 다른 프레임워크와의 통합 {#integration-with-other-frameworks}

컨텐츠 조각은 다음과 통합할 수 있습니다.

* **번역**

   컨텐츠 조각은 [AEM 번역 워크플로우](/help/sites-cloud/administering/translation/overview.md). 아키텍처 수준에서, 이것은 다음을 의미합니다.

   * 컨텐츠 조각의 개별 번역은 실제로 별도의 조각입니다. 예:

      * 그들은 다른 언어 뿌리 아래에 위치해 있습니다. 하지만 관련 언어 루트 아래에 정확히 동일한 상대 경로를 공유합니다.

         `/content/dam/<path>/en/<to>/<fragment>`

         및

         `/content/dam/<path>/de/<to>/<fragment>`
   * 규칙 기반 경로 외에 컨텐츠 조각의 다른 언어 버전 간에 더 이상 연결할 수 없습니다. 언어 변형을 탐색하는 수단을 UI에서 제공하지만 두 개의 개별 조각으로 처리됩니다.
   >[!NOTE]
   >
   >AEM 번역 워크플로우는에서 작동합니다. `/content`:
   >
   >* 컨텐츠 조각 모델은 `/conf`에는 이러한 번역이 포함되지 않습니다. UI 문자열을 국제화할 수 있습니다.


* **메타데이터 스키마**

   * 컨텐츠 조각(재)은 [메타데이터 스키마](/help/assets/metadata-schemas.md), 표준 자산으로 정의할 수 있습니다.

   * CFM은 고유한 특정 스키마를 제공합니다.

      `/libs/dam/content/schemaeditors/forms/contentfragment`

      필요한 경우 확장할 수 있습니다.

   * 각 스키마 양식은 조각 편집기와 통합됩니다.

## 컨텐츠 조각 관리 API - 서버측 {#the-content-fragment-management-api-server-side}

서버측 API를 사용하여 컨텐츠 조각에 액세스할 수 있습니다. 다음을 참조하십시오.

[com.adobe.cq.dam.cfm](https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/com/adobe/cq/dam/cfm/package-summary.html#package.description)

>[!CAUTION]
>
>컨텐츠 구조에 직접 액세스하는 대신 서버측 API를 사용하는 것이 좋습니다.

### 주요 인터페이스 {#key-interfaces}

다음 세 개의 인터페이스가 시작 지점으로 사용될 수 있습니다.

* **컨텐츠 조각** ([컨텐츠 조각](https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/com/adobe/cq/dam/cfm/ContentFragment.html))

   이 인터페이스를 사용하면 컨텐츠 조각을 추상적으로 사용할 수 있습니다.

   인터페이스는 다음 방법을 제공합니다.

   * 기본 데이터를 관리합니다(예: get name; get/set title/description)
   * 메타데이터 액세스
   * 액세스 요소:

      * 목록 요소
      * 이름별로 요소 가져오기
      * 새 요소 만들기( [경고](#caveats))

      * 요소 데이터에 액세스( `ContentElement`)
   * 조각에 대해 정의된 목록 변형
   * 새로운 변형을 전체적으로 만들기
   * 관련 컨텐츠 관리:

      * 컬렉션 나열
      * 컬렉션 추가
      * 컬렉션 제거
   * 조각의 모델에 액세스합니다

   조각의 주요 요소를 나타내는 인터페이스는 다음과 같습니다.

   * **콘텐츠 요소** ([ContentElement](https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/com/adobe/cq/dam/cfm/ContentElement.html))

      * 기본 데이터 가져오기(이름, 제목, 설명)
      * 콘텐츠 가져오기/설정
      * 요소의 변형에 액세스합니다.

         * 목록 변형
         * 이름별로 변형 가져오기
         * 새 변형 만들기( [경고](#caveats))
         * 변형 제거(참조) [경고](#caveats))
         * 변형 데이터에 액세스( `ContentVariation`)
      * 변형 해결을 위한 바로 가기(지정된 변형을 요소에 사용할 수 없는 경우 몇 가지 추가 구현별 폴백 논리 적용)
   * **컨텐츠 변형** ([컨텐츠 변형](https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/com/adobe/cq/dam/cfm/ContentVariation.html))

      * 기본 데이터 가져오기(이름, 제목, 설명)
      * 콘텐츠 가져오기/설정
      * 마지막 수정된 정보를 기반으로 간단한 동기화

   세 개의 인터페이스 모두 ( `ContentFragment`, `ContentElement`, `ContentVariation`) 확장 `Versionable` 인터페이스: 컨텐츠 조각에 필요한 버전 관리 기능을 추가합니다.

   * 요소의 새 버전 만들기
   * 요소의 버전 나열
   * 버전이 지정된 요소의 특정 버전의 콘텐츠를 가져옵니다







### 적용 - adaptTo() 사용 {#adapting-using-adaptto}

다음을 적용할 수 있습니다.

* `ContentFragment` 다음을 적용할 수 있습니다.

   * `Resource` - 기본 Sling 리소스 기본 업데이트 `Resource` 직접 재구축 필요 `ContentFragment` 개체.

   * `Asset` - DAM `Asset` 컨텐츠 조각을 나타내는 추상화 업데이트 `Asset` 직접 재구축 필요 `ContentFragment` 개체.

* `ContentElement` 다음을 적용할 수 있습니다.

   * [`ElementTemplate`](https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/com/adobe/cq/dam/cfm/ElementTemplate.html) - 요소의 구조적 정보에 액세스하기 위한 것입니다.

* [`FragmentTemplate`](https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/com/adobe/cq/dam/cfm/FragmentTemplate.html)

* `Resource` 다음을 적용할 수 있습니다.

   * `ContentFragment`

### 주의 사항 {#caveats}

다음과 같이 명시해야 합니다.

* 전체 API는 **not** 는 변경 사항을 자동으로 유지합니다(API JavaDoc에 별도로 언급되지 않는 경우). 따라서 항상 각 요청의 리소스 확인자(또는 실제로 사용 중인 해결자)를 커밋해야 합니다.

* 추가 작업이 필요할 수 있는 작업:

   * 에서 새 변형을 만드는 것이 좋습니다 `ContentFragment`. 이렇게 하면 모든 요소가 이 변형을 공유하고 컨텐츠 구조에 새로 생성된 변형을 반영하기 위해 적절한 글로벌 데이터 구조가 필요에 따라 업데이트됩니다.

   * 요소를 통해 기존 변형 제거, `ContentElement.removeVariation()`에서는 변형에 지정된 전역 데이터 구조를 업데이트하지 않습니다. 이러한 데이터 구조를 동기화하려면 `ContentFragment.removeVariation()` 대신 변형을 전체적으로 제거합니다.

## 컨텐츠 조각 관리 API - 클라이언트측 {#the-content-fragment-management-api-client-side}

>[!CAUTION]
>
>클라이언트측 API는 내부입니다.

### 추가 정보 {#additional-information}

다음을 참조하십시오.

* `filter.xml`

   다음 `filter.xml` 컨텐츠 조각 관리의 경우 자산 핵심 컨텐츠 패키지와 겹치지 않도록 구성됩니다.

## 세션 편집 {#edit-sessions}

>[!CAUTION]
>
>이 배경 정보를 고려하십시오. 여기서 (이(가) *전용 영역* 하지만 일부 경우에는 후드 아래에서 일이 작동하는 방식을 이해하는 데 도움이 될 수 있습니다.

여러 보기(= HTML 페이지)에 걸쳐 있을 수 있는 컨텐츠 조각을 편집하는 것은 원자적입니다. 이러한 원자적 다중 보기 편집 기능은 일반적인 AEM 개념이 아니므로 컨텐츠 조각은 *세션 편집*.

사용자가 편집기에서 컨텐츠 조각을 열면 편집 세션이 시작됩니다. 사용자가 다음 중 하나를 선택하여 편집기를 벗어나면 편집 세션이 끝납니다 **저장** 또는 **취소**.

기본적으로 모든 편집은 *live* 다른 모든 AEM 편집과 마찬가지로 컨텐츠도 포함됩니다. 편집 세션이 시작되면 편집되지 않은 현재 상태의 버전이 만들어집니다. 사용자가 편집을 취소하면 해당 버전이 복원됩니다. 사용자가 클릭하는 경우 **저장**&#x200B;에서 모든 편집이 실행되므로 특별히 수행한 작업은 없습니다 *live* 따라서 모든 변경 사항이 이미 유지됩니다. 또한 **저장** 은 일부 배경 처리(예: 전체 텍스트 검색 정보 만들기 및/또는 혼합 미디어 자산 처리)를 트리거합니다.

경계 사례에 대한 몇 가지 안전 조치가 있습니다. 예를 들어 사용자가 편집 세션을 저장하거나 취소하지 않고 편집기를 종료하려고 할 때 또한, 데이터의 손실을 방지하기 위해 주기적인 자동 저장 기능을 사용할 수 있다.
두 사용자가 동일한 컨텐츠 조각을 동시에 편집할 수 있으므로 서로의 변경 사항을 덮어쓸 수 있습니다. 이를 방지하려면 DAM 관리에서 을 적용하여 컨텐츠 조각을 잠가야 합니다 *체크아웃* 조각에 대해 작업을 수행합니다.

## 예 {#examples}

### 예: 기존 컨텐츠 조각 액세스 {#example-accessing-an-existing-content-fragment}

이를 위해 API를 나타내는 리소스를 다음과 같이 조정할 수 있습니다.

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

### 예: 새 컨텐츠 조각 만들기 {#example-creating-a-new-content-fragment}

프로그래밍 방식으로 새 컨텐츠 조각을 만들려면 다음을 사용해야 합니다
`FragmentTemplate` 모델 리소스에서 조정되었습니다.

예:

```java
Resource modelRsc = resourceResolver.getResource("...");
FragmentTemplate tpl = modelRsc.adaptTo(FragmentTemplate.class);
ContentFragment newFragment = tpl.createFragment(parentRsc, "A fragment name", "A fragment description.");
```

### 예: 자동 저장 간격 지정 {#example-specifying-the-auto-save-interval}

다음 [자동 저장 간격](/help/sites-cloud/administering/content-fragments/content-fragments-managing.md#save-close-and-versions) 구성 관리자(ConfMgr)를 사용하여 (초 단위 측정)를 정의할 수 있습니다.

* 노드: `<conf-root>/settings/dam/cfm/jcr:content`
* 속성 이름: `autoSaveInterval`
* 유형: `Long`

* 기본값: `600` (10분) 다음에 정의되어 있습니다. `/libs/settings/dam/cfm/jcr:content`

5분의 자동 저장 간격을 설정하려면 노드에서 속성을 정의해야 합니다. 예:

* 노드: `/conf/global/settings/dam/cfm/jcr:content`
* 속성 이름: `autoSaveInterval`

* 유형: `Long`

* 값: `300` (5분은 300초와 같습니다.)

## 페이지 작성용 구성 요소 {#components-for-page-authoring}

자세한 내용은

* [핵심 구성 요소 - 컨텐츠 조각 구성 요소](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/components/content-fragment-component.html) (권장)
