---
title: 컨텐츠 조각 사용자 정의 및 확장
description: 컨텐츠 조각은 표준 자산을 확장합니다.
translation-type: tm+mt
source-git-commit: 5f266358ed824d3783abb9ba591789ba47d7a521

---


# 컨텐츠 조각 사용자 정의 및 확장{#customizing-and-extending-content-fragments}

클라우드 서비스로 Adobe Experience Manager에서 컨텐츠 조각은 표준 자산을 확장합니다.참조:

* [컨텐츠 조각에 대한 자세한 내용을](/help/assets/content-fragments/content-fragments.md) 보려면 컨텐츠 조각 [및 컨텐츠 조각으로 페이지](/help/sites-cloud/authoring/fundamentals/content-fragments.md) 작성 및 관리를 참조하십시오.

* [자산 관리](/help/assets/manage-digital-assets.md) 및 [자산 편집기 사용자 지정 및 확장을](/help/assets/extend-asset-editor.md) 참조하십시오.

## 아키텍처 {#architecture}

컨텐츠 조각의 기본 [구성 부분은](/help/assets/content-fragments/content-fragments.md#constituent-parts-of-a-content-fragment) 다음과 같습니다.

* 컨텐츠 *조각*,
* 하나 이상의 컨텐츠 요소로 *구성된*&#x200B;경우,
* 하나 이상의 컨텐츠 변형을 사용할 수 *있습니다*.

조각 유형에 따라 모델 또는 단순 조각 **템플릿도** 사용됩니다.

>[!CAUTION]
>
>[이제 컨텐츠 조각 모델을](/help/assets/content-fragments/content-fragments-models.md) 모든 조각을 만드는 데 권장합니다.
>
>컨텐츠 조각 모델은 WKND의 모든 예에 사용됩니다.

* 콘텐츠 조각 모델:

   * 구조화된 컨텐츠를 포함하는 컨텐츠 조각을 정의하는 데 사용됩니다.
   * 컨텐츠 조각 모델은 컨텐츠 조각을 만들 때 해당 구조를 정의합니다.
   * 조각이 모델을 참조합니다.따라서 모델의 변경 사항이 종속 조각에 영향을 줄 수/영향을 줄 수 있습니다.
   * 모델은 데이터 유형이 내장되어 있습니다.
   * 새 변형 등을 추가하기 위한 함수에서는 그에 따라 조각을 업데이트해야 합니다.
   >[!NOTE]
   >
   >컨텐츠 조각을 표시하거나 렌더링하려면 계정에 모델에 대한 읽기 권한이 있어야 합니다.

   >[!CAUTION]
   >
   >기존 컨텐츠 조각 모델을 변경하면 종속 조각에 영향을 줄 수 있습니다.이렇게 하면 해당 조각에 고아 속성이 생길 수 있습니다.

* 컨텐츠 조각 템플릿 - **단순 조각**:

   * 간단한 컨텐츠 조각을 정의하는 데 사용됩니다.

   * 이 템플릿은 컨텐츠 조각을 만들 때 컨텐츠 조각의 (기본, 텍스트 전용) 구조를 정의합니다.

   * 템플릿이 작성되면 조각에 복사됩니다.

   * 새 변형 등을 추가하기 위한 함수에서는 그에 따라 조각을 업데이트해야 합니다.

   * 컨텐츠 조각 템플릿(**단순**&#x200B;조각)은 AEM 에코시스템 내의 다른 템플릿 메커니즘과 다른 방식으로 작동합니다(예: 페이지 템플릿 등). 따라서 별도로 고려해야 합니다.

   * 단순 조각 **템플릿을 기반으로** 하면 컨텐츠의 MIME 유형이 실제 컨텐츠에서 관리됩니다.즉, 각 요소와 변형에 다른 MIME 유형이 있을 수 있습니다.

### 사이트와 자산 통합 {#integration-of-sites-with-assets}

CFM(컨텐츠 조각 관리)은 다음과 같은 AEM 자산의 일부입니다.

* 콘텐츠 조각은 자산입니다.
* 기존 자산 기능을 사용합니다.
* 이 콘솔은 자산(관리 콘솔 등)과 완전히 통합됩니다.

컨텐츠 조각은 사이트 기능으로 간주됩니다.

* 페이지를 작성할 때 사용됩니다.

#### 구조화된 컨텐츠 조각을 자산에 매핑 {#mapping-structured-content-fragments-to-assets}

![구조화된 자산에 대한 컨텐츠 조각](assets/content-fragment-to-assets-structured.png)

구조화된 컨텐츠가 있는 컨텐츠 조각(즉, 컨텐츠 조각 모델을 기반으로 함)은 단일 자산에 매핑됩니다.

* 모든 컨텐츠는 자산의 `jcr:content/data` 노드 아래에 저장됩니다.

   * 요소 데이터는 마스터 하위 노드 아래에 저장됩니다.
      `jcr:content/data/master`

   * 변형은 변형의 이름을 가진 하위 노드 아래에 저장됩니다.예: `jcr:content/data/myvariation`

   * 각 요소의 데이터는 해당 하위 노드에 요소 이름이 있는 속성으로 저장됩니다.예를 들어 요소의 컨텐츠는 `text` 다음 `text` 위치에 속성으로 저장됩니다. `jcr:content/data/master`

* 메타데이터 및 관련 컨텐츠는 아래에 저장됩니다. `jcr:content/metadata`이 제목 및 설명은 일반적인 메타데이터로 간주되지 않고 `jcr:content`

#### 간단한 컨텐츠 조각을 자산에 매핑 {#mapping-simple-content-fragments-to-assets}

![자산을 간단하게](assets/content-fragment-to-assets-simple.png)

단순 조각 템플릿 기반 단순 컨텐츠 **조각은** 기본 자산 및 (선택적) 하위 자산으로 구성된 합성에 매핑됩니다.

* 조각(예: 제목, 설명, 메타데이터, 구조)의 모든 비컨텐츠 정보는 기본 자산에서만 관리됩니다.
* 조각의 첫 번째 요소의 컨텐츠는 기본 자산의 원래 변환에 매핑됩니다.

   * 첫 번째 요소의 변형(있는 경우)은 기본 자산의 다른 변환에 매핑됩니다.

* 추가 요소(존재하는 경우)는 기본 자산의 하위 자산에 매핑됩니다.

   * 이러한 추가 요소의 주요 컨텐츠는 해당 하위 자산의 원래 변환에 매핑됩니다.
   * 추가 요소의 기타 변형(해당되는 경우)은 해당 하위 자산의 다른 변환에 매핑됩니다.

#### 자산 위치 {#asset-location}

표준 자산과 마찬가지로 컨텐츠 조각은 다음 아래에서 보관됩니다.

`/content/dam`

#### 자산 권한 {#asset-permissions}

자세한 내용은 컨텐츠 조각 - [삭제 고려 사항을 참조하십시오](/help/assets/content-fragments/content-fragments-delete.md).

#### 기능 통합 {#feature-integration}

자산 코어와 통합하려면

* CFM(컨텐츠 조각 관리) 기능은 자산 코어를 기반으로 구축됩니다.

* CFM은 카드/열/목록 보기의 항목에 대한 자체 구현을 제공합니다.이러한 플러그인을 기존 자산 컨텐츠 렌더링 구현에 연결합니다.

* 콘텐츠 조각에 맞게 여러 자산 구성 요소가 확장되었습니다.

### 페이지에서 컨텐츠 조각 사용 {#using-content-fragments-in-pages}

>[!CAUTION]
>
>컨텐츠 [조각 구성 요소는 핵심 구성 요소의 일부입니다](https://docs.adobe.com/content/help/kr/experience-manager-core-components/using/components/content-fragment-component.html). 자세한 [내용은 핵심](https://docs.adobe.com/content/help/en/experience-manager-core-components/using/developing/developing.html) 구성 요소 개발을 참조하십시오.

컨텐츠 조각은 다른 자산 유형과 마찬가지로 AEM 페이지에서 참조할 수 있습니다. AEM에서는 **[컨텐츠 조각 핵심 구성 요소](https://docs.adobe.com/content/help/kr/experience-manager-core-components/using/components/content-fragment-component.html)**(페이지에[컨텐츠 조각을 포함할 수 있는](/help/sites-cloud/authoring/fundamentals/content-fragments.md#adding-a-content-fragment-to-your-page)구성 요소)를 제공합니다. 이 컨텐츠 조각 코어**[구성 요소를 확장할](https://docs.adobe.com/content/help/en/experience-manager-core-components/using/developing/developing.html)** 수도 있습니다.

* 구성 요소는 `fragmentPath` 속성을 사용하여 실제 컨텐츠 조각을 참조합니다. 속성은 `fragmentPath` 다른 자산 유형의 비슷한 속성과 동일한 방식으로 처리됩니다.예를 들어 컨텐츠 조각을 다른 위치로 이동하면

* 구성 요소를 사용하면 표시할 변형을 선택할 수 있습니다.

* 또한 여러 단락을 선택하여 출력을 제한할 수 있습니다.예를 들어 다중 열 출력에 사용할 수 있습니다.

* 구성 요소는 중간 컨텐츠를 허용합니다.

   * 여기에서 구성 요소를 사용하여 다른 자산(이미지 등)을 배치할 수 있습니다. 를 참조하십시오.

   * 중간 컨텐츠의 경우 다음을 수행해야 합니다.

      * 불완전한 언급의 가능성을 인식하다.중간 컨텐츠(페이지 작성 시 추가됨)는 옆에 배치된 단락에 대해 고정 관계가 없으므로 중간 컨텐츠 위치가 상대 위치를 잃을 수 있기 전에 새 단락(컨텐츠 조각 편집기에서)을 삽입합니다

      * 변형 및 단락 필터와 같은 추가 매개 변수를 사용하여 페이지에서 렌더링된 내용을 구성할 수 있습니다.

>[!NOTE]
>
>**컨텐츠 조각 모델:**
>
>페이지에서 컨텐츠 조각 모델을 기반으로 한 컨텐츠 조각을 사용할 경우 모델이 참조됩니다. 즉, 페이지를 게시할 때 모델이 게시되지 않은 경우 플래그가 지정되고 모델이 페이지와 함께 게시될 리소스에 추가됩니다.
>
>**컨텐츠 조각 템플릿 - 단순 조각:**
>
>페이지에서 컨텐츠 조각 템플릿 단순 조각을 기반으로 **한 컨텐츠 조각을** 사용할 때 조각을 만들 때 템플릿이 복사되었기 때문에 참조가 없습니다.

### 다른 프레임워크와 통합 {#integration-with-other-frameworks}

컨텐츠 조각은 다음과 통합할 수 있습니다.

* **번역**

   컨텐츠 조각은 AEM 번역 워크플로우와 완전히 통합됩니다. 건축적 수준에서 이것은 다음을 의미합니다.

   * 컨텐츠 조각의 개별 변환은 실제로 개별 조각입니다.예를 들면 다음과 같습니다.

      * 그들은 다른 언어 뿌리 아래에 위치한다.관련 언어 루트 아래에 정확히 동일한 상대 경로를 공유합니다.

         `/content/dam/<path>/en/<to>/<fragment>`

         vs.

         `/content/dam/<path>/de/<to>/<fragment>`
   * 규칙 기반 경로 외에 컨텐츠 조각의 다른 언어 버전 간에 더 이상 연결되지 않습니다.UI는 언어 변형을 탐색하는 수단을 제공하지만 두 개의 개별 조각으로 처리됩니다.
   >[!NOTE]
   >
   >AEM 번역 워크플로우는 `/content`다음과 같이 작동합니다.
   >
   >* 컨텐츠 조각 모델이 에 상주하므로 `/conf`이러한 번역에 포함되지 않습니다. UI 문자열을 국제화할 수 있습니다.


* **메타데이터 스키마**

   * 컨텐츠 조각(re)은 표준 자산으로 정의할 수 있는 [메타데이터 스키마를](/help/assets/metadata-schemas.md)사용합니다.

   * CFM은 고유한 특정 스키마를 제공합니다.

      `/libs/dam/content/schemaeditors/forms/contentfragment`

      필요한 경우 확장할 수 있습니다.

   * 각 스키마 양식이 조각 편집기와 통합됩니다.

## 컨텐츠 조각 관리 API - 서버측 {#the-content-fragment-management-api-server-side}

서버측 API 파섹참조:

[com.adobe.cq.dam.cfm](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/implementing/developing/ref/javadoc/com/adobe/cq/dam/cfm/package-frame.html)

>[!CAUTION]
>
>컨텐츠 구조에 직접 액세스하는 대신 서버측 API를 사용하는 것이 좋습니다.

### 주요 인터페이스 {#key-interfaces}

다음 세 가지 인터페이스는 시작 지점으로 사용할 수 있습니다.

* **컨텐츠 조각** ([컨텐츠 조각](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/implementing/developing/ref/javadoc/com/adobe/cq/dam/cfm/ContentFragment.html))

   이 인터페이스를 사용하면 추상적으로 컨텐츠 조각을 사용하여 작업할 수 있습니다.

   인터페이스는 다음 방법을 제공합니다.

   * 기본 데이터 관리(예: 이름 가져오기;get/set title/description)
   * 메타 데이터 액세스
   * 액세스 요소:

      * 목록 요소
      * 이름별로 요소 가져오기
      * 새 요소 만들기(경고 [참조](#caveats))

      * 요소 데이터에 액세스( `ContentElement`참조)
   * 조각에 대해 정의된 목록 변형
   * 전역적으로 새로운 변형 만들기
   * 관련 콘텐츠 관리:

      * 컬렉션 목록
      * 컬렉션 추가
      * 컬렉션 제거
   * 조각의 모델 또는 템플릿에 액세스
   조각의 주요 요소를 나타내는 인터페이스는 다음과 같습니다.

   * **콘텐츠 요소** ([ContentElement](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/implementing/developing/ref/javadoc/com/adobe/cq/dam/cfm/ContentElement.html))

      * 기본 데이터 가져오기(이름, 제목, 설명)
      * 콘텐츠 가져오기/설정
      * 요소의 변형 액세스:

         * 목록 변형
         * 이름별로 변형 가져오기
         * 새 변형 만들기(경고 [참조](#caveats))
         * 변형 제거(주의 [참조](#caveats))
         * 변형 데이터에 액세스( `ContentVariation`참조)
      * 변형에 대한 해결 단축키(지정한 변형을 요소에 사용할 수 없는 경우 구현 전용 폴백 로직 추가 적용)
   * **컨텐츠 변형** ([ContentVariation](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/implementing/developing/ref/javadoc/com/adobe/cq/dam/cfm/ContentVariation.html))

      * 기본 데이터 가져오기(이름, 제목, 설명)
      * 콘텐츠 가져오기/설정
      * 마지막으로 수정한 정보를 기반으로 간단한 동기화
   세 가지 인터페이스( `ContentFragment`, `ContentElement`, `ContentVariation`)는 모두 `Versionable` 인터페이스를 확장하여 컨텐츠 조각에 필요한 버전 관리 기능을 추가합니다.

   * 요소의 새 버전 만들기
   * 요소의 목록 버전
   * 버전 관리 요소의 특정 버전 컨텐츠 가져오기







### 적용 - adaptTo() 사용 {#adapting-using-adaptto}

다음을 조정할 수 있습니다.

* `ContentFragment` 다음을 적용할 수 있습니다.

   * `Resource` - 기본 Sling 리소스;기본 개체를 `Resource` 직접 업데이트하려면 `ContentFragment` 개체를 다시 빌드해야 합니다.

   * `Asset` - 컨텐츠 조각을 나타내는 DAM `Asset` 추상객체를 `Asset` 직접 업데이트하려면 `ContentFragment` 객체를 다시 빌드해야 합니다.

* `ContentElement` 다음을 적용할 수 있습니다.

   * `ElementTemplate` - 요소의 구조 정보에 액세스하는 경우

* `Resource` 다음을 적용할 수 있습니다.

   * `ContentFragment`

### Caveats {#caveats}

다음 사항에 유의해야 합니다.

* 전체 API는 API JavaDoc에 별도로 명시되어 있지 않는 한 자동으로 변경 내용을 지속하지 **않도록** 설계되었습니다. 따라서 항상 해당 요청의 리소스 해결 프로그램(또는 실제로 사용 중인 해결 프로그램)을 커밋해야 합니다.

* 추가 노력이 필요할 수 있는 작업:

   * 데이터 구조를 `ContentFragment` 업데이트하려면 새 변형을 만듭니다.

   * 요소를 통해 기존 변형을 제거해도 변형에 할당된 전역 데이터 구조가 업데이트되지 `ContentElement.removeVariation()`않습니다. 이러한 데이터 구조를 동기화하려면 `ContentFragment.removeVariation()` 대신 변형을 전체적으로 제거합니다.

## 컨텐츠 조각 관리 API - 클라이언트측 {#the-content-fragment-management-api-client-side}

>[!CAUTION]
>
>클라이언트측 API는 내부입니다.

### 추가 정보 {#additional-information}

다음을 참조하십시오.

* `filter.xml`

   컨텐츠 조각 관리에 `filter.xml` 대한 구성이 Assets 핵심 컨텐츠 패키지와 겹치지 않도록 구성되었습니다.

## 세션 편집 {#edit-sessions}

>[!CAUTION]
>
>이 배경 정보를 고려하십시오. 저장소에서 *비공개 영역으로* 표시되므로 여기서 어떤 것도 변경해서는 안 되지만, 경우에 따라 백그라운드에서 어떻게 작동하는지 이해하는 데 도움이 될 수 있습니다.

여러 보기(= HTML 페이지)를 확장할 수 있는 컨텐츠 조각을 편집하는 것은 원자적입니다. 이러한 원자 다중 보기 편집 기능은 일반적인 AEM 개념이 아니므로 컨텐츠 조각은 *편집 세션이라고*&#x200B;하는 것을 사용합니다.

사용자가 편집기에서 컨텐츠 조각을 열면 편집 세션이 시작됩니다. 편집 세션은 사용자가 저장 또는 취소를 선택하여 편집기를 **떠날 때** **완료됩니다**.

기술적으로 모든 편집 작업은 다른 모든 AEM 편집과 마찬가지로 *라이브* 컨텐츠에서도 수행됩니다. 편집 세션이 시작되면 편집되지 않은 현재 상태의 버전이 만들어집니다. 사용자가 편집을 취소하면 해당 버전이 복원됩니다. 사용자가 [저장] **을**&#x200B;클릭하는 경우 모든 편집이 *라이브* 컨텐츠에서 실행되므로 특정 작업이 수행되지 않으므로 모든 변경 사항이 이미 유지됩니다. 또한 저장을 클릭하면 **일부** 백그라운드 처리가 트리거됩니다(전체 텍스트 검색 정보 만들기 및/또는 혼합 미디어 자산 처리).

최첨단 사례에 대한 몇 가지 안전 조치가 있습니다.예를 들어 사용자가 편집 세션을 저장하거나 취소하지 않고 편집기를 벗어나려고 할 경우 또한 주기적인 자동 저장을 사용하여 데이터 손실을 방지할 수 있습니다.
두 사용자가 동일한 컨텐츠 조각을 동시에 편집할 수 있으므로 다른 변경 사항을 덮어쓸 수 있습니다. 이를 방지하려면 조각에 DAM 관리의 체크아웃 *작업을 적용하여 컨텐츠 조각을* 잠가야 합니다.

## 예 {#examples}

### 예:기존 컨텐츠 조각 액세스 {#example-accessing-an-existing-content-fragment}

이를 위해 API 파섹

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

### 예:새 컨텐츠 조각 만들기 {#example-creating-a-new-content-fragment}

프로그래밍 방식으로 새 컨텐츠 조각을 만들려면 모델 또는 템플릿 리소스에서`FragmentTemplate` 수정한 내용을 사용해야 합니다.

예:

```java
Resource templateOrModelRsc = resourceResolver.getResource("...");
FragmentTemplate tpl = templateOrModelRsc.adaptTo(FragmentTemplate.class);
ContentFragment newFragment = tpl.createFragment(parentRsc, "A fragment name", "A fragment description.");
```

### 예:자동 저장 간격 지정 {#example-specifying-the-auto-save-interval}

구성 관리자(ConfMgr)를 사용하여 [자동 저장 간격](/help/assets/content-fragments/content-fragments-managing.md#save-cancel-and-versions) (초 단위)을 정의할 수 있습니다.

* 노드: `<conf-root>/settings/dam/cfm/jcr:content`
* 속성 이름: `autoSaveInterval`
* 유형: `Long`

* 기본값: `600` 10분)this is defined on `/libs/settings/dam/cfm/jcr:content`

자동 저장 간격을 5분으로 설정하려면 노드에서 속성을 정의해야 합니다.예를 들면 다음과 같습니다.

* 노드: `/conf/global/settings/dam/cfm/jcr:content`
* 속성 이름: `autoSaveInterval`

* 유형: `Long`

* 값: `300` (5분은 300초로 완료)

## 페이지 작성용 구성 요소 {#components-for-page-authoring}

자세한 내용은

* [핵심 구성 요소 - 컨텐츠 조각 구성 요소](https://docs.adobe.com/content/help/kr/experience-manager-core-components/using/components/content-fragment-component.html) (권장)
