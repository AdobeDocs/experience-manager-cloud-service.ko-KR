---
title: Adobe Experience Manager as a Cloud Service 오버레이
description: AEM as a Cloud Service에서는 오버레이 원리를 사용하여 콘솔 및 기타 기능을 확장 및 사용자 지정할 수 있습니다
exl-id: 24bdb1a9-6d77-43c7-a75e-28e6e0fd7608
source-git-commit: ac760e782f80ee82a9b0604ef64721405fc44ee4
workflow-type: tm+mt
source-wordcount: '403'
ht-degree: 2%

---

# AEM as a Cloud Service 오버레이 {#overlays-in-aem}

Adobe Experience Manager as a Cloud Service은 오버레이 원리를 사용하여 콘솔과 기타 기능(예: 페이지 작성)을 확장 및 사용자 지정할 수 있습니다.

오버레이는 많은 컨텍스트에서 사용할 수 있는 용어입니다. 이 컨텍스트(AEM as a Cloud Service 확장)에서 오버레이는 사전 정의된 기능을 가져와서 해당 기능에 대한 자체 정의를 적용(표준 기능을 사용자 지정)하는 것을 의미합니다.

표준 인스턴스에서 사전 정의된 기능은 `/libs` 및 아래에서는 오버레이(사용자 지정)를 정의하는 것이 좋습니다. `/apps` 분기(사용 [검색 경로](#search-paths) 을 눌러 리소스를 확인합니다.

* 터치 활성화 UI는 [Granite](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/granite-ui/api/index.html)-관련 오버레이:

   * 메서드

      * 적절한 `/libs` 구조 `/apps`.

         따라서 1:1 복사본이 필요하지 않습니다. [Sling Resource Merger](/help/implementing/developing/introduction/sling-resource-merger.md) 필요한 원래 정의를 상호 참조하는 데 사용됩니다. Sling Resource Merger는 차이(차이점) 메커니즘을 통해 리소스에 액세스하고 병합하는 서비스를 제공합니다.

      * 에서 변경 작업을 수행합니다 `/apps`.
   * 장점

      * 의 변경 사항에 더욱 강력함 `/libs`.
      * 실제로 필요한 것만 재정의합니다.


>[!CAUTION]
>
>다음 [Sling Resource Merger](/help/implementing/developing/introduction/sling-resource-merger.md) 및 관련 메서드는 [Granite](https://www.adobe.io/experience-manager/reference-materials/6-5/granite-ui/api/jcr_root/libs/granite/ui/index.html). 즉, 뼈대 구조의 오버레이를 만드는 것은 터치 지원 표준 UI에만 적합합니다.

오버레이는 콘솔 구성 또는 사이드 패널의 자산 브라우저에 선택 카테고리 만들기(페이지 작성 시 사용)와 같이 많은 변경 사항에 권장되는 방법입니다. 이 변수는 다음과 같이 필요합니다.

* 사용자 ***필수가 아니어야 합니다.* 에서 변경 `/libs` 분기&#x200B;**이 분기는 인스턴스에 업그레이드가 적용될 때마다 변경 사항이 적용되므로 변경 사항이 손실될 수 있습니다.

* 한 곳에 여러분의 변화를 집중합니다. 필요에 따라 변경 사항을 추적, 마이그레이션, 백업 및/또는 디버깅하는 것이 쉬워집니다.

## 경로 검색 {#search-paths}

AEM에서는 검색 경로를 사용하여 리소스를 찾습니다(기본적으로). 먼저 `/apps` 분기 및 `/libs` 분기 이 메커니즘은 오버레이가 `/apps` (그리고 여기에 정의된 사용자 지정) 우선순위가 있습니다.

오버레이의 경우 전달된 리소스는 OSGi 구성에 정의된 검색 경로에 따라 검색된 리소스 및 속성의 합계입니다.
