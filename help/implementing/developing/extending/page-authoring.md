---
title: 페이지 작성 사용자 지정
description: AEM이 페이지 작성 기능을 사용자 지정하는 데 as a Cloud Service으로 제공하는 메커니즘에 대해 알아봅니다.
source-git-commit: f159f0ef86c2b82da4e7308a0892b4947b6e43fb
workflow-type: tm+mt
source-wordcount: '981'
ht-degree: 3%

---


# 페이지 작성 사용자 지정 {#customizing-page-authoring}

Adobe Experience Manager as a Cloud Service은 페이지 작성 기능 및 [콘솔](/help/implementing/developing/extending/consoles.md))을 참조하십시오.

## Clientlibs {#clientlibs}

Clientlib을 사용하면 기본 구현을 확장하여 새로운 기능을 사용할 수 있도록 하는 동시에 표준 함수, 개체 및 메서드를 재사용할 수 있습니다.

를 사용자 지정할 때 `/apps.` 새 clientlib은 다음 작업을 수행해야 합니다.

* 작성 clientlib에 따라 다름 `cq.authoring.editor.sites.page`.
* 적절한 것의 일부가 되다 `cq.authoring.editor.sites.page.hook` 범주.

clientlib에 대한 자세한 내용은 문서를 참조하십시오. [AEM에서 클라이언트측 라이브러리 as a Cloud Service 사용.](/help/implementing/developing/introduction/clientlibs.md)

## 오버레이 {#overlays}

오버레이는 노드 정의를 기반으로 하며, 를 사용하여 의 표준 기능을 오버레이할 수 있습니다. `/libs` 에서 맞춤화된 기능 사용 `/apps`.

오버레이를 만들 때 원본의 1:1 사본은 다음과 같이 필요하지 않습니다. [sling 리소스 병합](/help/implementing/developing/introduction/sling-resource-merger.md) 상속을 허용합니다.

자세한 내용은 다음을 참조하십시오. [JS 설명서 세트](https://developer.adobe.com/experience-manager/reference-materials/6-5/jsdoc/ui-touch/editor-core/index.html).

오버레이에 대한 자세한 내용은 문서를 참조하십시오. [Adobe Experience Manager as a Cloud Service용 오버레이](/help/implementing/developing/introduction/overlays.md)

## 새 레이어 추가(모드) {#add-new-layer-mode}

페이지를 편집할 때 다양한 옵션이 있습니다 [모드](/help/sites-cloud/authoring/fundamentals/environment-tools.md#page-modes) 사용 가능. 이러한 모드는 를 사용하여 구현됩니다 [레이어](/help/implementing/developing/introduction/ui-structure.md#layer). 이를 통해 동일한 페이지 콘텐츠에 대해 서로 다른 유형의 기능에 액세스할 수 있습니다. 표준 AEM 모드에는 편집, 레이아웃, 개발자, 타임워프, 라이브 카피 상태 및 타깃팅이 포함됩니다.

### 레이어 예: Live Copy 상태 {#layer-example-live-copy-status}

표준 AEM 인스턴스는 MSM 계층을 제공합니다. 관련 데이터에 액세스합니다. [다중 사이트 관리](/help/sites-cloud/administering/msm/overview.md) 레이어에서 강조 표시됩니다.

작동 중인 문서를 보려면 [WKND 샘플 콘텐츠](/help/implementing/developing/introduction/develop-wknd-tutorial.md) 및 선택 **Live Copy 상태** 모드.

MSM 레이어 정의(참조용)는에서 찾을 수 있습니다.

`/libs/wcm/msm/content/touch-ui/authoring/editor/js/msm.Layer.js`

### 코드 샘플 {#code-sample}

MSM 보기용 레이어(모드)를 만드는 방법을 보여주는 샘플 패키지입니다.

이 페이지의 코드는에서 찾을 수 있습니다. [GitHub.](https://github.com/Adobe-Marketing-Cloud/aem-authoring-new-layer-mode)

## 자산 브라우저에 새 선택 범주 추가 {#add-new-selection-category-to-asset-browser}

에셋 브라우저에는 다양한 유형/카테고리(예: 이미지 및 문서)의 에셋이 표시됩니다. 자산은 이러한 자산 카테고리로 필터링할 수도 있습니다.

### 코드 샘플 {#code-sample-1}

`aem-authoring-extension-assetfinder-flickr` 는 에셋 파인더에 그룹을 추가하는 방법을 보여 주는 샘플 패키지입니다. 이 예는에 연결합니다. [Flickr](https://www.flickr.com)의 공개 스트림에 사이드 패널에 표시됩니다.

이 페이지의 코드는에서 찾을 수 있습니다. [GitHub.](https://github.com/Adobe-Marketing-Cloud/aem-authoring-extension-assetfinder-flickr)

## 리소스 필터링 {#filtering-resources}

페이지를 작성할 때 사용자는 종종 목록의 리소스에서 선택해야 합니다.

목록을 적절한 크기로 유지하고 사용 사례와 관련이 있도록 맞춤형 술어 형식으로 필터를 구현할 수 있습니다. 예를 들어 `pathbrowser` Granite 구성 요소를 사용하여 사용자가 특정 리소스에 대한 경로를 선택할 수 있습니다. 표시된 경로는 다음과 같은 방식으로 필터링될 수 있습니다.

* 를 구현하여 사용자 지정 술어 구현 [`com.day.cq.commons.predicate.AbstractNodePredicate`](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/commons/predicate/package-summary.html) 인터페이스.
* 술어 이름을 지정하고, 을 사용할 때 해당 이름을 참조합니다. `pathbrowser`.

사용자 지정 술어 만들기에 대한 자세한 내용은 [이 문서입니다.](/help/implementing/developing/introduction/query-builder-custom-predicate.md)

## 구성 요소 도구 모음에 새 작업 추가 {#add-new-action-to-a-component-toolbar}

각 구성 요소에는 일반적으로 해당 구성 요소에서 수행할 수 있는 작업 범위에 대한 액세스를 제공하는 도구 모음이 있습니다.

### 코드 샘플 {#code-sample-2}

`aem-authoring-extension-toolbar-screenshot` 는 구성 요소를 렌더링하기 위해 사용자 지정 도구 모음 작업을 만드는 방법을 보여 주는 샘플 패키지입니다.

이 페이지의 코드는에서 찾을 수 있습니다. [GitHub.](https://github.com/Adobe-Marketing-Cloud/aem-authoring-extension-toolbar-screenshot)

## 새로운 즉석 편집기 추가 {#add-new-in-place-editor}

### 표준 즉석 편집기 {#standard-in-place-editor}

표준 AEM 설치에서

1. `/libs/cq/gui/components/authoring/editors/clientlibs/core/js/editors/editorExample.js` 사용 가능한 다양한 편집기에 대한 정의를 보관합니다.

1. 편집기와 이를 사용할 수 있는 각 리소스 유형(구성 요소에서와 같이) 간에 연결이 있습니다.

   * `cq:inplaceEditing`

     예:

      * `/libs/foundation/components/text/cq:editConfig`
      * `/libs/foundation/components/image/cq:editConfig`

         * 속성: `editorType`

           해당 구성 요소에 대해 즉석 편집이 트리거될 때 사용되는 인라인 편집기 유형을 정의합니다. 예: `text`, `textimage`, `image`, `title`.

1. 편집기의 추가 구성 세부 정보는 `config` 구성 및 `plugin` 필요한 플러그인 구성 세부 정보를 포함할 노드입니다.


다음은 이미지 구성 요소의 이미지 자르기 플러그인에 대한 종횡비를 정의하는 예입니다.

```xml
   <cq:inplaceEditing
           jcr:primaryType="cq:InplaceEditingConfig"
           active="{Boolean}true"
           editorType="image">
           <config jcr:primaryType="nt:unstructured">
               <plugins jcr:primaryType="nt:unstructured">
                   <crop jcr:primaryType="nt:unstructured">
                       <aspectRatios jcr:primaryType="nt:unstructured">
                           <_x0031_6-10
                               jcr:primaryType="nt:unstructured"
                               name="16 : 10"
                               ratio="0.625"/>
                       </aspectRatios>
                   </crop>
               </plugins>
           </config>
   </cq:inplaceEditing>
```

>[!NOTE]
>
>AEM 자르기 비율, 다음으로 설정: `ratio` 속성은 다음과 같이 정의됩니다. **높이/폭**. 이는 종래의 폭/높이 정의와 다르며, 레거시 호환성을 위해 수행됩니다. 사용자가 를 정의한 경우 작성 사용자가 차이를 알지 못합니다. `name` 속성이 UI에 표시되므로 명확하게 알 수 있습니다.

#### 새로운 즉석 편집기 만들기 {#creating-a-new-in-place-editor}

새로운 즉석 편집기를 구현하려면(clientlib 내에서):

1. 구현:

   * `setUp`
   * `tearDown`

1. 편집기 등록(생성자 포함):

   * `editor.register`

1. 편집기와 이를 사용할 수 있는 모든 리소스 유형(구성 요소에서와 같이) 간의 연결을 제공합니다.

#### 새로운 즉석 편집기를 만들기 위한 코드 샘플 {#code-sample-for-creating-a-new-in-place-editor}

`aem-authoring-extension-inplace-editor` 는 AEM에서 즉석 편집기를 만드는 방법을 보여 주는 샘플 패키지입니다.

이 페이지의 코드는에서 찾을 수 있습니다. [GitHub.](https://github.com/Adobe-Marketing-Cloud/aem-authoring-extension-inplace-editor)

## 새 페이지 작업 추가 {#add-a-new-page-action}

페이지 도구 모음에 새 페이지 작업을 추가하려면(예: ) **사이트로 돌아가기** (콘솔) 작업.

### 코드 샘플 {#code-sample-3}

`aem-authoring-extension-header-backtosites` 는 사이트 콘솔로 다시 이동하기 위해 사용자 지정 헤더 막대 작업을 만드는 방법을 보여 주는 샘플 패키지입니다.

이 페이지의 코드는에서 찾을 수 있습니다. [GitHub.](https://github.com/Adobe-Marketing-Cloud/aem-authoring-extension-header-backtosites)

## 활성화 요청 워크플로 사용자 지정 {#customizing-the-request-for-activation-workflow}

기본 워크플로우 **활성화 요청**:

* 콘텐츠 작성자는 적절한 메뉴에 자동으로 표시됩니다. **이(가) 다음을 포함하지 않음** 적절한 복제 권한이지만 **다음을 포함** DAM 사용자 및 작성자의 멤버십.

* 그렇지 않으면 복제 권한이 제거되어 아무 것도 표시되지 않습니다.

이러한 활성화에 대한 사용자 지정 동작을 만들려면 다음을 오버레이할 수 있습니다. **활성화 요청** 워크플로:

1. 위치 `/apps` 오버레이 **사이트** 마법사 `/libs/wcm/core/content/common/managepublicationwizard`

   * 이 자체는 의 공통 인스턴스를 무시합니다. `/libs/cq/gui/content/common/managepublicationwizard`.

1. 필요에 따라 워크플로우 모델 및 관련 구성/스크립트를 업데이트합니다.
1. 에 대한 권한 제거 `replicate` 모든 관련 페이지에 대한 모든 적절한 사용자의 작업. 사용자 중 한 명이라도 이 워크플로를 기본 작업으로 트리거하려면 페이지를 게시(또는 복제)해 보십시오.
