---
title: Adobe Experience Manager에서 슬링 리소스 합병을 Cloud Service으로 사용
description: Sling Resource Combination은 리소스에 액세스하고 병합하는 서비스를 제공합니다
translation-type: tm+mt
source-git-commit: 1a8a9781da7390d25ec687d46af8d8a976c069bc
workflow-type: tm+mt
source-wordcount: '1241'
ht-degree: 1%

---


# Cloud Service으로 AEM에서 Sling 리소스 합병 사용 {#using-the-sling-resource-merger-in-aem}

## 목적 {#purpose}

Sling Resource Combination은 리소스에 액세스하고 병합하는 서비스를 제공합니다. 두 가지 모두에 대해 차이(차이) 메커니즘을 제공합니다.

* **[구성된](/help/implementing/developing/introduction/overlays.md)**검색 경로를 사용하여[리소스의 오버레이](/help/implementing/developing/introduction/overlays.md#configuring-the-search-paths).

* **리소스** 유형 계층 구조(속성을 통해)를 사용하여 터치 지원 UI에 대한 구성 요소 대화 상자`cq:dialog`를 무시합니다 `sling:resourceSuperType`.

Sling Resource Commodification을 사용하면 오버레이/재정의 리소스 및/또는 속성이 원본 리소스/속성과 병합됩니다.

* 사용자 지정된 정의의 컨텐츠의 우선 순위가 원본보다 높습니다(예: 오버레이 *또는* 무시 ** ).

* 필요한 경우 사용자 [정의에 정의된 속성](#properties) 원본에서 병합된 컨텐츠의 사용 방법을 나타냅니다.

<!-- Still links to reference material in 6.5 -->

>[!CAUTION]
>
>Sling 리소스 합병 및 관련 메서드는 Granite에서만 사용할 수 [있습니다](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/granite-ui/api/index.html). 이는 표준 터치 지원 UI에만 해당됨을 의미합니다. 이 방법으로 정의된 특정 오버라이드는 구성 요소의 터치 지원 대화 상자에만 적용됩니다.
>
>다른 영역(터치 지원 구성 요소의 다른 측면 포함)에 대한 오버레이/오버라이드는 적절한 노드 및 구조를 원본에서 사용자 지정이 정의될 위치로 복사하는 것을 포함합니다.

### AEM에 대한 목표 {#goals-for-aem}

AEM에서 Sling Resource Combination을 사용하는 방법은 다음과 같습니다.

* 사용자 정의 변경 사항이 `/libs`
* 복제된 구조를 축소합니다 `/libs`.

   Sling Resource Combination을 사용하는 경우 전체 구조를 복사하지 않는 것이 좋습니다. 이렇게 하면 사용자 지정(일반적으로 `/libs` `/apps`)에서 정보가 너무 많이 보관됩니다. 정보를 중복하면 시스템을 어떤 식으로든 업그레이드할 때 문제가 발생할 가능성이 불필요하게 커집니다.

>[!NOTE]
>
>오버라이드는 검색 경로에 종속되지 않고 속성을 사용하여 연결을 `sling:resourceSuperType` 만듭니다.
>
>그러나 AEM에서 가장 좋은 방법은 사용자 지정 `/apps`을 정의하는 것이므로, 대체를 정의하 `/apps`는 경우가 많습니다. 이것은 여러분이 아래의 어떤 것도 바꾸지 말아야 하기 때문입니다 `/libs`.

>[!CAUTION]
>
>경로 ***에서 어떤 것도 변경하지*** 않아야 `/libs` 합니다.
>
>이는 다음에 인스턴스를 업그레이드할 때 `/libs` 의 컨텐츠를 덮어쓰고, 핫픽스 또는 기능 팩을 적용할 때 덮어쓸 수 있기 때문입니다.
>
>구성 및 기타 변경에 대해 권장되는 방법은 다음과 같습니다.
>
>1. 필요한 항목(예: 존재함)을 `/libs``/apps`
   >
   >
1. Make any changes within `/apps`

>



### 속성 {#properties}

리소스 병합은 다음 속성을 제공합니다.

* `sling:hideProperties` ( `String` 또는 `String[]`)

   숨길 속성 또는 속성 목록을 지정합니다.

   와일드카드가 모두 `*` 숨겨집니다.

* `sling:hideResource` ( `Boolean`)

   하위 항목을 포함하여 리소스를 완전히 숨겨야 하는지 여부를 나타냅니다.

* `sling:hideChildren` ( `String` 또는 `String[]`)

   숨길 하위 노드 또는 하위 노드 목록을 포함합니다. 노드의 속성이 유지됩니다.

   와일드카드가 모두 `*` 숨겨집니다.

* `sling:orderBefore` ( `String`)

   현재 노드가 앞에 배치되어야 하는 형제 노드의 이름을 포함합니다.

이러한 속성은 해당/원래 리소스/속성(보낸 사람 `/libs`)이 오버레이/재정의(종종 `/apps`)에 사용되는 방식에 영향을 줍니다.

### 구조 만들기 {#creating-the-structure}

오버레이 또는 오버라이드를 만들려면 원래 노드를 대상(보통 `/apps`) 아래에 상응하는 구조로 다시 만들어야 합니다. 예:

* 오버레이

   * 레일에 표시된 사이트 콘솔의 탐색 항목 정의는 다음과 같습니다.

      `/libs/cq/core/content/nav/sites/jcr:title`

   * 이를 오버레이하려면 다음 노드를 만드십시오.

      `/apps/cq/core/content/nav/sites`

      그런 다음 필요에 따라 속성 `jcr:title` 을 업데이트합니다.

* 재정의

   * 텍스트 콘솔에 대한 터치 지원 대화 상자의 정의는 다음과 같이 정의됩니다.

      `/libs/foundation/components/text/cq:dialog`

   * 이 항목을 무시하려면 다음 노드를 만드십시오. 예:

      `/apps/the-project/components/text/cq:dialog`

이 중 하나를 만들려면 뼈대 구조를 다시 만들어야 합니다. 구조를 간소화하기 위해 모든 중간 노드는 유형(원본 노드 유형을 반영하지 않아도 `nt:unstructured` 됩니다. 예: in `/libs`).

따라서 위의 오버레이 예에서 다음 노드가 필요합니다.

```shell
/apps
  /cq
    /core
      /content
        /nav
          /sites
```

>[!NOTE]
>
>Sling 리소스 합병(예: 표준 터치 지원 UI를 처리할 때)을 사용하는 경우 너무 많은 정보가 저장되므로 전체 구조를 복사하지 않는 `/libs` 것이 좋습니다 `/apps`. 이로 인해 시스템을 업그레이드하면 문제가 발생할 수 있습니다.

### Use Cases {#use-cases}

이러한 기능은 표준 기능과 함께 다음과 같은 이점을 제공합니다.

* **속성 추가**

   속성이 정의에 존재하지 않지만 `/libs` `/apps` 오버레이/override에 필요합니다.

   1. 해당 노드를 `/apps`
   1. 이 노드에서 새 속성을 만듭니다. &quot;

* **속성 재정의(자동 생성된 속성이 아님)**

   속성은 에 정의되어 `/libs`있지만 `/apps` overlay/override에 새 값이 필요합니다.

   1. 해당 노드를 `/apps`
   1. 이 노드에서 일치하는 속성을 만듭니다( / 아래 `apps`).

      * 속성 우선 순위는 Sling Resource Resolver 구성을 기반으로 합니다.
      * 속성 유형 변경이 지원됩니다.

         에 사용된 속성 유형과 다른 속성 유형을 사용하는 `/libs`경우 정의한 속성 유형이 사용됩니다.
   >[!NOTE]
   >
   >속성 유형 변경이 지원됩니다.

* **자동 생성 속성 재정의**

   기본적으로 자동 생성된 속성(예: `jcr:primaryType`)은 현재 사용 중인 노드 유형이 존중되도록 하기 위해 오버레이/재정의 `/libs` 를 받지 않습니다. 오버레이/재정의를 적용하려면 노드를 다시 만들어야 하며, 속성을 명시적으로 `/apps`숨기고 재정의해야 합니다.

   1. 원하는 노드 아래 `/apps` 에 해당 노드를 만듭니다. `jcr:primaryType`
   1. 해당 노드 `sling:hideProperties` 에 자동으로 생성된 속성의 값으로 설정된 속성을 만듭니다. 예를 들면 `jcr:primaryType`

      에 정의된 이 속성 `/apps`은 이제 `/libs`

* **노드 및 해당 하위 재정의**

   노드 및 그 하위 항목은 에 정의되어 `/libs`있지만 `/apps` overlay/override에 새 구성이 필요합니다.

   1. 다음 작업의 결합:

      1. 노드의 하위 항목 숨기기(노드의 속성 유지)
      1. 속성/속성 재정의

* **속성 숨기기**

   속성은 에서 정의되지만 `/libs``/apps` 오버레이/override에는 필요하지 않습니다.

   1. 해당 노드를 `/apps`
   1. 또는 유형 `sling:hideProperties` 의 속성을 `String` 만듭니다 `String[]`. 숨거나 무시할 속성을 지정합니다. 와일드카드를 사용할 수도 있습니다. 예:

      * `*`
      * `["*"]`
      * `jcr:title`
      * `["jcr:title", "jcr:description"]`

* **노드 및 해당 하위 숨기기**

   노드 및 그 자식은 에 정의되어 `/libs`있지만 `/apps` overlay/override에는 필요하지 않습니다.

   1. /apps 아래에 해당 노드 만들기
   1. 속성 만들기 `sling:hideResource`

      * 유형: `Boolean`
      * 정렬 단추: `true`

* **노드의 하위 항목 숨기기(노드의 속성을 유지하는 동안)**

   노드, 해당 속성 및 하위 항목은 `/libs` 노드 및 해당 속성은 `/apps` overlay/override에 필요하지만 일부 또는 모든 하위 노드는 `/apps` overlay/override에 필요하지 않습니다.

   1. 해당 노드를 `/apps`
   1. 속성을 만듭니다 `sling:hideChildren`.

      * 유형: `String[]`
      * value: 숨기기/무시할 하위 노드 목록(정의된 항목 `/libs`)

      와일드카드 &amp;ast; 모든 하위 노드를 숨기거나 무시하는 데 사용할 수 있습니다.


* **노드 순서 변경**

   노드 및 그 형제자매는 에 정의되어 있습니다 `/libs`. 노드를 오버레이/재정의에서 다시 만들도록 새 위치가 필요한 경우, 여기서 새 위치는 의 해당 동기 노드에 대한 참조로 정의됩니다 `/apps` `/libs`.

   * 다음 속성을 `sling:orderBefore` 사용하십시오.

      1. 해당 노드를 `/apps`
      1. 속성을 만듭니다 `sling:orderBefore`.

         이 값은 현재 노드가 앞에 위치해야 하는 노드( `/libs`과 같이)를 지정합니다.

         * 유형: `String`
         * 정렬 단추: `<before-SiblingName>`

### 코드에서 Sling 리소스 합병 호출 {#invoking-the-sling-resource-merger-from-your-code}

Sling Resource Combination에는 두 개의 사용자 지정 리소스 공급자(하나는 오버레이이고 다른 하나는 오버라이드용)가 포함됩니다. 이러한 각 호출은 마운트 지점을 사용하여 코드 내에서 호출할 수 있습니다.

>[!NOTE]
>
>리소스에 액세스할 때는 적절한 마운트 지점을 사용하는 것이 좋습니다.
>
>이렇게 하면 Sling 리소스 병합이 호출되고 완전히 병합된 리소스가 반환됩니다(복제해야 하는 구조가 감소됨). `/libs`

* 오버레이:

   * 목적: 검색 경로에 따라 리소스 병합
   * 마운트 지점: `/mnt/overlay`
   * usage: `mount point + relative path`
   * 예:

      * `getResource('/mnt/overlay' + '<relative-path-to-resource>');`

* 재정의:

   * 목적: 슈퍼 유형에 따라 리소스 병합
   * 마운트 지점: `/mnt/overide`
   * usage: `mount point + absolute path`
   * 예:

      * `getResource('/mnt/override' + '<absolute-path-to-resource>');`

<!--
### Example of Usage {#example-of-usage}

Some examples are covered:

* Overlay:

    * [Customizing the Consoles](/help/sites-developing/customizing-consoles-touch.md)
    * [Customizing Page Authoring](/help/sites-developing/customizing-page-authoring-touch.md)

* Override:

    * [Configuring your Page Properties](/help/sites-developing/page-properties-views.md#configuring-your-page-properties)
-->
