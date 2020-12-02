---
title: Cloud Service으로 Adobe Experience Manager용 오버레이
description: AEM as Cloud Service은 오버레이의 원칙을 사용하여 콘솔 및 기타 기능을 확장하고 사용자 정의할 수 있습니다
translation-type: tm+mt
source-git-commit: 8028682f19ba6ba7db6b60a2e5e5f5843f7ac11f
workflow-type: tm+mt
source-wordcount: '401'
ht-degree: 1%

---


# AEM as a Cloud Service에서 오버레이 {#overlays-in-aem}

Adobe Experience Manager은 오버레이 원칙을 사용하여 콘솔 및 기타 기능(예: 페이지 작성)을 확장하고 사용자 정의할 수 있도록 해줍니다.

<!--
Adobe Experience Manager as a Cloud Service uses the principle of overlays to allow you to extend and customize the [consoles](/help/sites-developing/customizing-consoles-touch.md) and other functionality (for example, [page authoring](/help/sites-developing/customizing-page-authoring-touch.md)).
-->

오버레이는 많은 컨텍스트에서 사용될 수 있는 용어입니다. 이 컨텍스트(AEM을 Cloud Service으로 확장)에서 오버레이는 사전 정의된 기능을 사용하고 표준 기능을 사용자 정의하기 위해 해당 기능에 사용자 정의 정의를 적용하는 것을 의미합니다.

표준 인스턴스에서 사전 정의된 기능은 `/libs` 아래에 있으며, 리소스를 해결하려면 [검색 경로](#search-paths)를 사용하여 `/apps` 분기 아래에 오버레이(사용자 지정)를 정의하는 것이 좋습니다.

* 터치 지원 UI는 [Granite](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/granite-ui/api/index.html) 관련 오버레이를 사용합니다.

   * 메서드

      * `/apps` 아래에 적절한 `/libs` 구조를 재구성합니다.

         필요한 원본 정의를 상호 참조하는 데 [Sling 리소스 합병](/help/implementing/developing/introduction/sling-resource-merger.md)이 사용되므로 1:1 사본이 필요하지 않습니다. Sling Resource Combination은 차이(차이) 메커니즘을 통해 리소스에 액세스하고 병합하는 서비스를 제공합니다.

      * `/apps` 아래에서 변경합니다.
   * 장점

      * `/libs` 아래에서 변경 사항이 더욱 강력해졌습니다.
      * 실제로 필요한 것만 재정의합니다.


<!-- Still links to reference material in 6.5 -->

>[!CAUTION]
>
>[Sling 리소스 합병](/help/implementing/developing/introduction/sling-resource-merger.md) 및 관련 메서드는 [Granite](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/granite-ui/api/index.html)에서만 사용할 수 있습니다. 즉, 골격 구조를 갖는 오버레이를 만드는 것은 표준 터치 가능 UI에만 적합합니다.

오버레이는 콘솔 구성 또는 사이드 패널의 자산 브라우저에 선택 카테고리 만들기(페이지 작성 시 사용) 등 많은 변경 사항에 대해 권장되는 방법입니다. 이러한 요구 사항은 다음과 같습니다.

<!--
Overlays are the recommended method for many changes, such as [configuring your consoles](/help/sites-developing/customizing-consoles-touch.md#create-a-custom-console) or [creating your selection category to the asset browser in the side panel](/help/sites-developing/customizing-page-authoring-touch.md#add-new-selection-category-to-asset-browser) (used when authoring pages). They are required as:
-->

* ***은(는) `/libs` 분기&#x200B;**에서 변경할 수 없습니다.
이 분기는 인스턴스에 업그레이드가 적용될 때마다 변경 사항이 적용되므로 변경 사항이 손실될 수 있습니다.*

* 한 곳에서 변경 사항을 집중적으로 적용를 사용하면 필요에 따라 변경 사항을 추적, 마이그레이션, 백업 및/또는 디버깅할 수 있습니다.

## 검색 경로 {#search-paths}

AEM에서는 검색 경로를 사용하여 리소스를 찾습니다. 기본적으로 `/apps` 분기, `/libs` 분기 순으로 검색합니다. 이 메커니즘은 `/apps`(및 여기에 정의된 사용자 지정) 오버레이에 우선 순위가 지정됨을 의미합니다.

오버레이의 경우 제공된 리소스는 OSGi 구성에 정의된 검색 경로에 따라 검색된 리소스와 속성의 집합입니다.

<!--
## Example of Usage {#example-of-usage}

Some examples are covered when:

* [Customizing the Consoles](/help/sites-developing/customizing-consoles-touch.md)
* [Customizing Page Authoring](/help/sites-developing/customizing-page-authoring-touch.md)
-->