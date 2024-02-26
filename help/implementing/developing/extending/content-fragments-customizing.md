---
title: 콘텐츠 조각 맞춤화 및 확장
description: 컨텐츠 조각은 표준 자산을 확장합니다. 이를 맞춤화하는 방법에 대해 알아봅니다.
exl-id: 58152d6e-21b6-4f45-a45c-0f46ee58825e
source-git-commit: 89f23a590338561b4cfeb10b54a260a135ec2f08
workflow-type: tm+mt
source-wordcount: '1689'
ht-degree: 1%

---

# 콘텐츠 조각 맞춤화 및 확장{#customizing-and-extending-content-fragments}

Adobe Experience Manager as a Cloud Service 내에서 컨텐츠 조각은 표준 자산을 확장합니다. 다음을 참조하십시오.

* [컨텐츠 조각 생성 및 관리](/help/sites-cloud/administering/content-fragments/overview.md) 및 [컨텐츠 조각으로 페이지 작성](/help/sites-cloud/authoring/fragments/content-fragments.md) 콘텐츠 조각에 대한 자세한 내용은 을 참조하십시오.

* [자산 관리](/help/assets/manage-digital-assets.md) 표준 에셋에 대한 자세한 내용을 보려면 .

## 아키텍처 {#architecture}

기본 [구성 부분](/help/sites-cloud/administering/content-fragments/overview.md#constituent-parts-of-a-content-fragment) 콘텐츠 조각은 다음과 같습니다.

* A *컨텐츠 조각* 그 자체
* 하나 이상으로 구성되어 있습니다 *컨텐츠 요소*
* 하나 이상 있을 수 있습니다. *컨텐츠 변형*

개별 콘텐츠 조각은 콘텐츠 조각 모델을 기반으로 합니다.

* 콘텐츠 조각 모델은 콘텐츠 조각을 만들 때 콘텐츠 조각의 구조를 정의합니다.
* 조각은 모델을 참조하므로 모델 변경 사항은 모든 종속 조각에 영향을 주거나 줄 수 있습니다.
* 모델은 데이터 유형을 기반으로 합니다.
* 새 변형을 추가하는 기능 등은 조각을 적절하게 업데이트해야 합니다.

  >[!NOTE]
  >
  >콘텐츠 조각을 표시/렌더링하려면 계정에 다음이 있어야 합니다. `read` 모델에 대한 권한.

  >[!CAUTION]
  >
  >기존 콘텐츠 조각 모델을 변경하면 종속된 조각이 영향을 받을 수 있습니다. 이로 인해 해당 조각에서 고립 속성이 발생할 수 있습니다.

### Sites와 자산 통합 {#integration-of-sites-with-assets}

CFM(콘텐츠 조각 관리)은 다음과 같이 Adobe Experience Manager(AEM) 에셋의 일부입니다.

* 컨텐츠 조각은 에셋입니다.
* 기존 에셋 기능을 사용합니다.
* Assets는 Assets(관리 콘솔 등)와 완전히 통합됩니다.

컨텐츠 조각은 다음과 같이 AEM Sites 기능으로 간주됩니다.

* 페이지를 작성할 때 사용됩니다.

#### 에셋에 콘텐츠 조각 매핑 {#mapping-content-fragments-to-assets}

![에셋으로의 콘텐츠 조각](assets/content-fragment-to-assets.png)

컨텐츠 조각 모델을 기반으로 하는 컨텐츠 조각은 단일 자산에 매핑됩니다.

* 모든 콘텐츠는 아래에 저장됩니다. `jcr:content/data` 에셋의 노드:

   * 요소 데이터는 마스터 하위 노드 아래에 저장됩니다.
     `jcr:content/data/master`

   * 변형은 변형의 이름을 전달하는 하위 노드 아래에 저장됩니다. 예: `jcr:content/data/myvariation`

   * 각 요소의 데이터는 각 하위 노드에 요소 이름(예: 요소의 콘텐츠)을 갖는 속성으로 저장됩니다 `text` 속성으로 저장됩니다. `text` 날짜 `jcr:content/data/master`

* 메타데이터 및 관련 콘텐츠는 아래에 저장됩니다. `jcr:content/metadata`
기존 메타데이터로 간주되지 않고 에 저장되는 제목과 설명을 제외하고 `jcr:content`

#### 자산 위치 {#asset-location}

표준 에셋과 마찬가지로 콘텐츠 조각은 아래에 보관됩니다.

`/content/dam`

#### 자산 권한 {#asset-permissions}

다음을 참조하십시오 [컨텐츠 조각 - 삭제 고려 사항](/help/sites-cloud/administering/content-fragments/delete-considerations.md).

#### 기능 통합 {#feature-integration}

에셋 코어와 통합하려면 다음을 수행하십시오.

* CFM(Content Fragment Management) 기능은 에셋 코어를 기반으로 합니다.

* CFM은 카드/열/목록 보기의 항목에 대한 자체 구현을 제공합니다. 이러한 구현은 기존 Assets 콘텐츠 렌더링 구현에 연결됩니다.

* 콘텐츠 조각을 지원하기 위해 몇 가지 Assets 구성 요소가 확장되었습니다.

### 페이지에서 컨텐츠 조각 사용 {#using-content-fragments-in-pages}

>[!CAUTION]
>
>다음 [콘텐츠 조각 구성 요소는 핵심 구성 요소의 일부입니다.](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/wcm-components/content-fragment-component.html). 다음을 참조하십시오 [핵심 구성 요소 개발](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/overview.html) 을 참조하십시오.

다른 에셋 유형과 마찬가지로 AEM 페이지에서 콘텐츠 조각을 참조할 수 있습니다. AEM에서 제공하는 **[콘텐츠 조각 핵심 구성 요소](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/wcm-components/content-fragment-component.html)** - a [페이지에 콘텐츠 조각을 포함할 수 있는 구성 요소](/help/sites-cloud/authoring/fragments/content-fragments.md#adding-a-content-fragment-to-your-page). 이를 확장할 수도 있습니다. **[컨텐츠 조각](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/overview.html)** 핵심 구성 요소입니다.

* 구성 요소는 `fragmentPath` 속성을 사용하여 실제 콘텐츠 조각을 참조합니다. 다음 `fragmentPath` 속성은 다른 에셋 유형의 유사한 속성과 동일한 방식으로 처리됩니다(예: 콘텐츠 조각을 다른 위치로 이동할 때).

* 구성 요소를 사용하여 표시할 변형을 선택할 수 있습니다.

* 또한 단락 범위를 선택하여 출력을 제한할 수 있습니다. 예를 들어, 다중 열 출력에 사용할 수 있습니다.

* 구성 요소에서 중간 콘텐츠를 사용할 수 있습니다.

   * 여기에서 구성 요소를 사용하여 참조된 조각의 단락 사이에 다른 에셋(이미지 등)을 배치할 수 있습니다.

   * 중간 콘텐츠:

      * 참조가 불안정할 수 있다는 것을 알고 있어야 합니다. 중간 콘텐츠(페이지 작성 시 추가됨)는 옆에 있는 단락에 고정된 관계가 없습니다. 중간 콘텐츠 위치 앞에 새 단락(콘텐츠 조각 편집기에서)을 삽입하면 상대 위치가 손실될 수 있습니다.

      * 변형 및 단락 필터 등 추가 매개 변수를 고려하여 페이지에서 렌더링되는 내용을 구성합니다.

>[!NOTE]
>
>**콘텐츠 조각 모델:**
>
>페이지에서 콘텐츠 조각을 사용하면 그 기반이 되는 콘텐츠 조각 모델이 참조됩니다.
>
>즉, 페이지를 게시할 때 모델이 게시되지 않은 경우 이에 플래그가 지정되고 모델이 페이지와 함께 게시할 리소스에 추가됩니다.

### 다른 프레임워크와 통합 {#integration-with-other-frameworks}

컨텐츠 조각은 다음과 통합할 수 있습니다.

* **번역**

  콘텐츠 조각은 [AEM 번역 워크플로](/help/sites-cloud/administering/translation/overview.md). 아키텍처 수준에서 이는 다음을 의미합니다.

   * 컨텐츠 조각의 개별 번역은 개별 조각입니다. 예를 들면 다음과 같습니다.

      * 이러한 언어 루트는 서로 다른 언어 루트 아래에 있지만 관련 언어 루트 아래의 상대 경로를 공유합니다.

        `/content/dam/<path>/en/<to>/<fragment>`

        및

        `/content/dam/<path>/de/<to>/<fragment>`

   * 규칙 기반 경로 외에도 콘텐츠 조각의 다른 언어 버전 간에는 다른 연결이 없습니다. UI에서 언어 변형 사이를 탐색할 수 있는 수단을 제공하지만 두 조각은 두 개의 개별 조각으로 처리됩니다.

  >[!NOTE]
  >
  >AEM 번역 워크플로우는 `/content`:
  >
  >* 콘텐츠 조각 모델 위치 `/conf`, 이러한 번역은 포함되지 않습니다. UI 문자열을 국제화할 수 있습니다.

* **메타데이터 스키마**

   * 콘텐츠 조각은 [메타데이터 스키마](/help/assets/metadata-schemas.md) 표준 에셋으로 정의할 수 있습니다.

   * CFM은 고유한 특정 스키마를 제공합니다.

     `/libs/dam/content/schemaeditors/forms/contentfragment`

     필요한 경우 이를 연장할 수 있습니다.

   * 각 스키마 양식은 조각 편집기와 통합됩니다.

## 콘텐츠 조각 관리 API - 서버측 {#the-content-fragment-management-api-server-side}

서버측 API를 사용하여 콘텐츠 조각에 액세스할 수 있습니다. 다음을 참조하십시오.

[com.adobe.cq.dam.cfm](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/adobe/cq/dam/cfm/package-summary.html#package.description)

>[!CAUTION]
>
>Adobe은 콘텐츠 구조에 직접 액세스하는 대신 서버측 API를 사용하는 것을 권장합니다.

### 주요 인터페이스 {#key-interfaces}

다음 세 가지 인터페이스는 진입점 역할을 할 수 있습니다.

* **컨텐츠 조각** ([ContentFragment](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/adobe/cq/dam/cfm/ContentFragment.html))

  이 인터페이스를 사용하면 추상적인 방식으로 콘텐츠 조각을 사용하여 작업할 수 있습니다.

  인터페이스는 다음과 같은 수단을 제공합니다.

   * 기본 데이터 관리(예: 이름 가져오기, 제목/설명 가져오기/설정)
   * 메타데이터 액세스
   * 액세스 요소:

      * 목록 요소
      * 이름별 요소 가져오기
      * 요소 만들기(참조) [주의 사항](#caveats))

      * 요소 데이터 액세스(참조) `ContentElement`)

   * 조각에 대해 정의된 목록 변형
   * 전체적으로 변형 만들기
   * 관련 콘텐츠 관리:

      * 컬렉션 나열
      * 컬렉션 추가
      * 컬렉션 제거

   * 조각의 모델에 액세스

  조각의 주요 요소를 나타내는 인터페이스는 다음과 같습니다.

   * **컨텐츠 요소** ([ContentElement](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/adobe/cq/dam/cfm/ContentElement.html))

      * 기본 데이터(이름, 제목, 설명) 가져오기
      * 콘텐츠 가져오기/설정
      * 요소의 변형 액세스:

         * 목록 변형
         * 이름별 변형 가져오기
         * 변형 만들기(참조) [주의 사항](#caveats))
         * 변형 제거(참조) [주의 사항](#caveats))
         * 변형 데이터 액세스(참조) `ContentVariation`)

      * 변형 해결을 위한 바로 가기(지정된 변형을 요소에 사용할 수 없는 경우 구현별 추가 폴백 논리 적용)

   * **컨텐츠 변형** ([ContentVariation](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/adobe/cq/dam/cfm/ContentVariation.html))

      * 기본 데이터(이름, 제목, 설명) 가져오기
      * 콘텐츠 가져오기/설정
      * 마지막으로 수정된 정보를 기반으로 한 간단한 동기화

  세 가지 인터페이스 모두( `ContentFragment`, `ContentElement`, `ContentVariation`) 확장 `Versionable` 컨텐츠 조각에 필요한 버전 관리 기능을 추가하는 인터페이스:

   * 요소 버전 만들기
   * 요소의 목록 버전
   * 버전이 지정된 요소의 특정 버전 콘텐츠 가져오기

### 적응 - adaptTo() 사용 {#adapting-using-adaptto}

다음 항목을 조정할 수 있습니다.

* `ContentFragment` 을 다음과 같이 조정할 수 있습니다.

   * `Resource` - 기본 Sling 리소스, 기본 업데이트 `Resource` 을(를) 직접 다시 빌드해야 합니다. `ContentFragment` 개체.

   * `Asset` - DAM `Asset` 콘텐츠 조각을 나타내는 추상화; 업데이트 `Asset` 을(를) 직접 다시 빌드해야 합니다. `ContentFragment` 개체.

* `ContentElement` 을 다음과 같이 조정할 수 있습니다.

   * [`ElementTemplate`](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/adobe/cq/dam/cfm/ElementTemplate.html) - 요소의 구조 정보에 액세스합니다.

* [`FragmentTemplate`](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/adobe/cq/dam/cfm/FragmentTemplate.html)

* `Resource` 을 다음과 같이 조정할 수 있습니다.

   * `ContentFragment`

### 주의 사항 {#caveats}

주의해야 할 사항은 다음과 같습니다.

* 전체 API는 **아님** api JavaDoc에 별도로 명시되지 않는 한 변경 사항을 자동으로 유지합니다. 따라서 항상 해당 요청의 리소스 확인자(또는 실제로 사용 중인 확인자)를 커밋하십시오.

* 추가 작업이 필요할 수 있는 작업:

   * Adobe은 다음에서 변형을 만들 것을 권장합니다. `ContentFragment`. 이렇게 하면 모든 요소가 이 변형을 공유하고, 콘텐츠 구조의 새로운 변형을 반영하기 위해 필요에 따라 적절한 전역 데이터 구조가 업데이트됩니다.

   * 요소를 통해 기존 변형 제거, `ContentElement.removeVariation()`은 변형에 지정된 전역 데이터 구조를 업데이트하지 않습니다. 이러한 데이터 구조가 계속 동기화되도록 하려면 `ContentFragment.removeVariation()` 대신, 변형을 전체적으로 제거합니다.

## 콘텐츠 조각 관리 API - 클라이언트측 {#the-content-fragment-management-api-client-side}

>[!CAUTION]
>
>클라이언트측 API는 내부에 있습니다.

### 추가 정보 {#additional-information}

다음을 참조하십시오.

* `filter.xml`

  다음 `filter.xml` 의 콘텐츠 조각 관리는 에셋 핵심 콘텐츠 패키지와 겹치지 않도록 구성됩니다.

## 세션 편집 {#edit-sessions}

>[!CAUTION]
>
>이 배경 정보를 고려하십시오. 여기에는 (으)로 표시되므로 여기서는 아무것도 변경하면 안 됩니다. *개인 영역* 저장소에서), 그러나 때때로 내부에서 작업이 작동하는 방식을 이해하는 데 도움이 될 수 있습니다.

여러 보기(= HTML 페이지)에 걸쳐 있을 수 있는 컨텐츠 조각 편집은 원자적입니다. 이러한 원자 형식의 다중 보기 편집 기능은 일반적인 AEM 개념이 아니므로 콘텐츠 조각은 *세션 편집*.

편집 세션은 사용자가 편집기에서 콘텐츠 조각을 열 때 시작됩니다. 사용자가 다음 중 하나를 선택하여 편집기를 떠나면 편집 세션이 종료됩니다 **저장** 또는 **취소**.

기술적으로 모든 편집은에 수행됩니다. *live* 다른 모든 AEM 편집과 마찬가지로 컨텐츠. 편집 세션이 시작되면 편집되지 않은 현재 상태의 버전이 만들어집니다. 사용자가 편집을 취소하면 해당 버전이 복원됩니다. 사용자가 **저장**&#x200B;에서 편집이 실행되었기 때문에 특정 작업은 수행되지 않습니다. *live* 따라서 모든 변경 사항은 이미 지속됩니다. 또한 **저장** 는 전체 텍스트 검색 정보 만들기, 혼합 미디어 에셋 처리 또는 둘 다와 같은 일부 백그라운드 처리를 트리거합니다.

예를 들어 사용자가 편집 세션을 저장하거나 취소하지 않고 편집기를 종료하려고 하는 경우, 경계 사례에 대한 몇 가지 안전 조치가 있습니다. 또한 데이터 손실을 방지하기 위해 정기적으로 자동 저장할 수 있습니다.
두 명의 사용자가 동일한 콘텐츠 조각을 동시에 편집할 수 있으므로 서로의 변경 사항을 덮어쓸 수 있습니다. 이를 방지하려면 DAM 관리 를 적용하여 콘텐츠 조각을 잠가야 합니다. *체크아웃* 조각에 대한 작업입니다.

## 예 {#examples}

### 예: 기존 콘텐츠 조각 액세스 {#example-accessing-an-existing-content-fragment}

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

### 예제: 컨텐츠 조각 만들기 {#example-creating-a-new-content-fragment}

프로그래밍 방식으로 콘텐츠 조각을 만들려면 `FragmentTemplate` 모델 리소스를 통해 조정됩니다.

예:

```java
Resource modelRsc = resourceResolver.getResource("...");
FragmentTemplate tpl = modelRsc.adaptTo(FragmentTemplate.class);
ContentFragment newFragment = tpl.createFragment(parentRsc, "A fragment name", "A fragment description.");
```

### 예: 자동 저장 간격 지정 {#example-specifying-the-auto-save-interval}

다음 [자동 저장 간격](/help/sites-cloud/administering/content-fragments/managing.md#save-close-and-versions) (초 단위)는 구성 관리자(ConfMgr)를 사용하여 정의할 수 있습니다.

* 노드: `<conf-root>/settings/dam/cfm/jcr:content`
* 속성 이름: `autoSaveInterval`
* 유형: `Long`

* 기본값: `600` (10분); 다음에서 정의됨: `/libs/settings/dam/cfm/jcr:content`

자동 저장 간격을 5분으로 설정하려면 노드에서 속성을 정의합니다.

예:

* 노드: `/conf/global/settings/dam/cfm/jcr:content`
* 속성 이름: `autoSaveInterval`

* 유형: `Long`

* 값: `300` (5분은 300초와 동일)

## 페이지 작성을 위한 구성 요소 {#components-for-page-authoring}

자세한 내용은

* [핵심 구성 요소 - 콘텐츠 조각 구성 요소](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/wcm-components/content-fragment-component.html) (권장)
