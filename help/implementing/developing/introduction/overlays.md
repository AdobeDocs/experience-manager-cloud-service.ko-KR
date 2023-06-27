---
title: Adobe Experience Manager as a Cloud Service용 오버레이
description: AEM as a Cloud Service에서는 오버레이 원리를 사용하여 콘솔 및 기타 기능을 확장하고 사용자 정의할 수 있습니다
exl-id: 24bdb1a9-6d77-43c7-a75e-28e6e0fd7608
source-git-commit: d361ddc9a50a543cd1d5f260c09920c5a9d6d675
workflow-type: tm+mt
source-wordcount: '404'
ht-degree: 2%

---

# AEM as a Cloud Service 오버레이 {#overlays-in-aem}

Adobe Experience Manager as a Cloud Service은 오버레이 원리를 사용하여 콘솔 및 기타 기능(예: 페이지 작성)을 확장하고 사용자 정의할 수 있습니다.

오버레이는 여러 컨텍스트에서 사용할 수 있는 용어입니다. 이러한 맥락에서 AEM을 as a Cloud Service으로 확장하는 것은 사전 정의된 기능을 사용하고 그 위에 고유한 정의를 부과하여 표준 기능을 사용자 지정하는 것을 의미합니다.

표준 인스턴스에서는 사전 정의된 기능이 `/libs` 및 아래에서 오버레이(사용자 정의)를 정의하는 것이 좋습니다. `/apps` 분기(사용) [검색 경로](#search-paths) 를 클릭하여 리소스를 확인합니다.

* 터치 지원 사용자 인터페이스는 [Granite](https://developer.adobe.com/experience-manager/reference-materials/6-5/granite-ui/api/jcr_root/libs/granite/ui/index.html)-관련 오버레이:

   * 메서드

      * 적절한 항목 재구성 `/libs` 아래 구조 `/apps`.

        이 재구조화에는 1:1 사본이 필요하지 않습니다. [Sling 리소스 병합](/help/implementing/developing/introduction/sling-resource-merger.md) 는 필요한 원래 정의를 상호 참조하는 데 사용됩니다. Sling 리소스 병합은 리소스를 액세스하고 차등(차이점 보관용) 메커니즘과 병합하는 서비스를 제공합니다.

      * 아래 `/apps`, 변경합니다.

   * 장점

      * 다음 변경 사항에 더욱 강력함: `/libs`.
      * 필요한 사항만 재정의합니다.

>[!CAUTION]
>
>다음 [Sling 리소스 병합](/help/implementing/developing/introduction/sling-resource-merger.md) 및 관련 메서드는 [Granite](https://developer.adobe.com/experience-manager/reference-materials/6-5/granite-ui/api/jcr_root/libs/granite/ui/index.html). 이 규칙은 뼈대 구조를 사용하는 오버레이를 만드는 것이 표준 터치 지원 사용자 인터페이스에만 적합하다는 것을 의미합니다.

오버레이는 많은 변경 사항에 대해 권장되는 방법입니다. 예를 들어, 콘솔을 구성하거나 사이드 패널에서 에셋 브라우저에 대한 선택 카테고리를 만들 수 있습니다(페이지를 작성할 때 사용). 필요한 형식은 다음과 같습니다.

* **다음에서 `/libs` 분기, *금지* 변경**
이 분기는 업그레이드가 인스턴스에 적용될 때마다 변경되기 때문에 수행하는 모든 변경 사항이 손실될 수 있습니다.

* 한 위치에서 변경 내용을 집중하여 필요에 따라 변경 내용을 더 쉽게 추적, 마이그레이션, 백업 또는 디버깅할 수 있습니다.

## 경로 검색 {#search-paths}

AEM은 검색 경로를 사용하여 리소스를 찾고, 기본적으로 을(를) 검색합니다. `/apps` 분기 및 다음 `/libs` 분기입니다. 이 메커니즘은에 오버레이가 있음을 의미합니다 `/apps` (및 여기서 정의한 사용자 정의)에 우선순위가 있습니다.

오버레이의 경우 전달된 리소스는 OSGi 구성에 정의된 검색 경로에 따라 검색된 리소스 및 속성의 집계입니다.
