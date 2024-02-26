---
title: 페이지 작성 사용자 정의
description: AEM as a Cloud Service가 페이지 작성 기능을 사용자 정의하기 위해 제공하는 메커니즘에 대해 알아봅니다.
exl-id: 98d3c7ab-46d2-4e8d-b0da-5c8a7b398135
source-git-commit: f6162dcbc5b7937d55922e8c963a402697110329
workflow-type: tm+mt
source-wordcount: '937'
ht-degree: 94%

---

# 페이지 작성 사용자 정의 {#customizing-page-authoring}

Adobe Experience Manager as a Cloud Service는 작성 인스턴스의 페이지 작성 기능(및 [콘솔](/help/implementing/developing/extending/consoles.md))을 사용자 정의할 수 있는 메커니즘을 제공합니다.

## Clientlibs {#clientlibs}

Clientlibs를 사용하면 기본 구현을 확장하여 새로운 기능을 활성화하면서 표준 기능, 오브젝트 및 메서드를 재사용할 수 있습니다.

사용자 정의할 때 `/apps.` 아래에서 자체적인 clientlib을 만들 수 있습니다. 새 clientlib은 다음을 충족해야 합니다.

* 작성 clientlib `cq.authoring.editor.sites.page`에 의존합니다.
* 적절한 `cq.authoring.editor.sites.page.hook` 카테고리에 속합니다.

다음을 참조하십시오 [AEM에서 클라이언트측 라이브러리 as a Cloud Service 사용](/help/implementing/developing/introduction/clientlibs.md).

## 오버레이 {#overlays}

오버레이는 노드 정의를 기반으로 하며 이를 통해 `/apps`의 사용자 정의 기능으로 `/libs`의 표준 기능을 오버레이할 수 있습니다.

오버레이를 만들 때 원본의 1:1 사본은 필요하지 않습니다. [Sling 리소스 병합](/help/implementing/developing/introduction/sling-resource-merger.md)을 통해 상속되기 때문입니다.

자세한 내용은 [JS 설명서 세트](https://developer.adobe.com/experience-manager/reference-materials/6-5/jsdoc/ui-touch/editor-core/index.html).

오버레이에 대한 자세한 내용은 [Adobe Experience Manager as a Cloud Service용 오버레이](/help/implementing/developing/introduction/overlays.md).

## 새 레이어(모드) 추가 {#add-new-layer-mode}

페이지를 편집할 때 다양한 [모드](/help/sites-cloud/authoring/page-editor/introduction.md#page-modes)를 사용할 수 있습니다. 이러한 모드는 [레이어](/help/implementing/developing/introduction/ui-structure.md#layer)를 사용하여 구현됩니다. 이를 통해 동일한 페이지 콘텐츠에 대해 서로 다른 유형의 기능에 액세스할 수 있습니다. 표준 AEM 모드로는 편집, 레이아웃, 개발자, 타임워프, Live Copy 상태, 타겟팅이 있습니다.

### 레이어 예: Live Copy 상태 {#layer-example-live-copy-status}

표준 AEM 인스턴스는 MSM 레이어를 제공합니다. 이는 [다중 사이트 관리](/help/sites-cloud/administering/msm/overview.md)와 관련된 데이터에 액세스하며 레이어에서 이러한 데이터를 강조 표시합니다.

실제 작동을 보려면 [WKND 샘플 콘텐츠](/help/implementing/developing/introduction/develop-wknd-tutorial.md)에서 언어 사본을 편집하고 **Live Copy 상태** 모드를 선택하면 됩니다.

다음 위치에서 MSM 레이어 정의(참조용)를 확인할 수 있습니다.

`/libs/wcm/msm/content/touch-ui/authoring/editor/js/msm.Layer.js`

### 코드 샘플 {#code-sample}

MSM 보기를 위한 레이어(모드)를 만드는 방법을 보여 주는 샘플 패키지입니다.

이 페이지의 코드는 [GitHub](https://github.com/Adobe-Marketing-Cloud/aem-authoring-new-layer-mode)에서 확인할 수 있습니다.

## 자산 브라우저에 새 선택 카테고리 추가 {#add-new-selection-category-to-asset-browser}

자산 브라우저에는 다양한 유형/카테고리(예: 이미지 및 문서)의 자산이 표시됩니다. 자산을 이러한 자산 카테고리별로 필터링할 수도 있습니다.

### 코드 샘플 {#code-sample-1}

`aem-authoring-extension-assetfinder-flickr`는 자산 파인더에 그룹을 추가하는 방법을 보여 주는 샘플 패키지입니다. 이 예는 [Flickr](https://www.flickr.com)의 공개 스트림에 연결하며 이러한 스트림을 측면 패널에 표시합니다.

이 페이지의 코드는 [GitHub](https://github.com/Adobe-Marketing-Cloud/aem-authoring-extension-assetfinder-flickr)에서 확인할 수 있습니다.

## 리소스 필터링 {#filtering-resources}

페이지를 작성할 때 사용자는 흔히 목록의 리소스 중에서 선택해야 합니다.

목록을 적당한 크기로 유지하고 사용 사례와도 관련되게 하려면 필터를 사용자 정의 조건자 형태로 구현할 수 있습니다. 예를 들어 `pathbrowser` Granite 구성 요소는 사용자가 특정 리소스에 대한 경로를 선택할 수 있도록 하는 데 사용하며, 표시된 경로는 다음과 같은 방식으로 필터링할 수 있습니다.

* [`com.day.cq.commons.predicate.AbstractNodePredicate`](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/commons/predicate/package-summary.html) 상호 작용을 구현하여 사용자 정의 조건자를 구현합니다.
* 조건자의 이름을 지정하고, `pathbrowser`를 사용할 때 해당 이름을 참조합니다.

사용자 정의 조건자 만들기에 대한 자세한 내용은 [이 문서](/help/implementing/developing/introduction/query-builder-custom-predicate.md)를 참조하십시오.

## 구성 요소 도구 모음에 새 작업 추가 {#add-new-action-to-a-component-toolbar}

일반적으로 각 구성 요소에는 해당 구성 요소에서 수행할 수 있는 다양한 작업에 대한 액세스를 제공하는 도구 모음이 있습니다.

### 코드 샘플 {#code-sample-2}

`aem-authoring-extension-toolbar-screenshot`은 구성 요소를 렌더링하는 사용자 정의 도구 모음 작업을 만드는 방법을 보여 주는 샘플 패키지입니다.

이 페이지의 코드는 [GitHub](https://github.com/Adobe-Marketing-Cloud/aem-authoring-extension-toolbar-screenshot)에서 확인할 수 있습니다.

## 새 바로 편집기 추가 {#add-new-in-place-editor}

### 표준 바로 편집기 {#standard-in-place-editor}

표준 AEM 설치에서

1. `/libs/cq/gui/components/authoring/editors/clientlibs/core/js/editors/editorExample.js`는 사용 가능한 다양한 편집기의 정의를 보유합니다.

1. 편집기와 이를 사용할 수 있는 각 리소스 유형(구성 요소에서와 같이) 간에는 연결이 있습니다.

   * `cq:inplaceEditing`

     예:

      * `/libs/foundation/components/text/cq:editConfig`
      * `/libs/foundation/components/image/cq:editConfig`

         * 속성: `editorType`

           해당 구성 요소에 대해 바로 편집이 트리거될 때 사용되는 인라인 편집기 유형을 정의합니다. 예를 들면 `text`, `textimage`, `image`, `title`과 같습니다.

1. 편집기의 추가 구성 세부 정보는 구성을 포함하는 `config` 노드 및 필요한 플러그인 구성 세부 정보를 포함하는 `plugin` 노드를 사용하여 구성할 수 있습니다.


다음은 이미지 구성 요소의 이미지 자르기 플러그인의 화면 비율을 정의한 예입니다.

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
>`ratio` 속성으로 설정되는 AEM 자르기 비율은 **높이/폭**&#x200B;으로 정의됩니다. 이는 종래의 폭/높이 정의와 다르며, 레거시 호환성을 위해 수행됩니다. `name` 속성을 명확히 정의한 경우 이 이름이 UI에 표시되므로 작성 사용자가 차이를 알지 못합니다.

#### 새 바로 편집기 만들기 {#creating-a-new-in-place-editor}

새 바로 편집기를 구현하려면(clientlib 내에서) 다음 작업을 수행하십시오.

1. 다음을 구현합니다.

   * `setUp`
   * `tearDown`

1. 다음과 같이 편집기를 등록합니다(생성자 포함).

   * `editor.register`

1. 편집기와 이를 사용할 수 있는 모든 리소스 유형(구성 요소에서와 같이) 간의 연결을 제공합니다.

#### 새 바로 편집기를 만들기 위한 코드 샘플 {#code-sample-for-creating-a-new-in-place-editor}

`aem-authoring-extension-inplace-editor`는 AEM에서 바로 편집기를 만드는 방법을 보여 주는 샘플 패키지입니다.

이 페이지의 코드는 [GitHub](https://github.com/Adobe-Marketing-Cloud/aem-authoring-extension-inplace-editor)에서 확인할 수 있습니다.

## 새 페이지 작업 추가 {#add-a-new-page-action}

페이지 도구 모음에 새 페이지 작업을 추가하려면(예: ) **사이트로 돌아가기** (콘솔) 작업.

### 코드 샘플 {#code-sample-3}

`aem-authoring-extension-header-backtosites`는 사이트 콘솔로 돌아가기 위한 사용자 정의 헤더 표시줄 작업을 만드는 방법을 보여 주는 샘플 패키지입니다.

이 페이지의 코드는 [GitHub](https://github.com/Adobe-Marketing-Cloud/aem-authoring-extension-header-backtosites)에서 확인할 수 있습니다.

## 활성화 요청 워크플로 사용자 정의 {#customizing-the-request-for-activation-workflow}

즉시 사용 가능한 워크플로인 **활성화 요청**&#x200B;은 다음과 같이 작동합니다.

* 콘텐츠 작성자에게 적절한 복제 권한이 **없지만** DAM 사용자 및 작성자의 멤버십이 **있는** 경우 적절한 메뉴에 자동으로 표시됩니다.

* 이외에는 복제 권한이 제거되었기 때문에 아무것도 표시되지 않습니다.

이러한 활성화에 대해 사용자 정의 동작을 만들려면 **활성화 요청** 워크플로를 오버레이할 수 있습니다.

1. `/apps`에서 **Sites** 마법사 `/libs/wcm/core/content/common/managepublicationwizard`를 다음과 같이 오버레이합니다.

   * 이 자체로는 `/libs/cq/gui/content/common/managepublicationwizard`의 공통 인스턴스가 무시됩니다.

1. 필요에 따라 워크플로 모델 및 관련 구성/스크립트를 업데이트합니다.
1. 모든 관련 페이지에 대해 모든 적절한 사용자에게서 `replicate` 작업에 대한 권리를 제거합니다. 사용자가 있을 때 이 워크플로가 기본 작업으로 트리거되도록 하려면 페이지 게시(또는 복제)해 봅니다.
