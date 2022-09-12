---
title: AEM Screens as a Cloud Service 소개
description: 이 페이지는 AEM Screens as a Cloud Service 소개 역할을 합니다.
exl-id: b1cc0a63-ecd3-4d89-ac49-f384cc610cdc
source-git-commit: 4b76fbbb1b58324065b39d6928027759b0897246
workflow-type: tm+mt
source-wordcount: '382'
ht-degree: 12%

---

# AEM Screens as a Cloud Service 소개 {#introduction-screens-cloud}

AEM Screens as a Cloud Service를 사용하면 공공 장소에서 사용할 수 있도록 설계된 매력적인 동적 디지털 사이니지 경험을 만들 수 있습니다. 이는 AEM Screens 제품의 다음 진화된 제품으로서, 사용 편의성과 확장성 측면에서 큰 도약입니다.

AEM Screens as a Cloud Service는 마케터가 대규모 동적 디지털 경험을 만들고 관리할 수 있도록 하는 디지털 사이니지 솔루션입니다. 또한 포괄적인 디지털 마케팅 전략의 일부로서 다양한 유형의 실제 화면이 포함됩니다. 또한 일반적인 웹 및 모바일 채널 이상으로 Adobe의 옴니채널 오퍼링을 확장하여 전체 고객을 보유한 디지털 간판 채널도 포함합니다. AEM Screens as a Cloud Service을 사용하면 컨텐츠 작성, 컨텐츠 어셈블리, 트리거된 이벤트 관리 및 모든 공용 공간의 모든 소비자 및 방문자에 대한 미디어 플레이에 대한 심층적인 이해를 통해 보다 연관성 있고 상황에 맞는 생산성 및 예상 가능한 사용자 경험을 사용할 수 있습니다.

## 화면의 구성 요소 이해 as a Cloud Service {#understanding-components}

스크린 as a Cloud Service 에는 두 가지 주요 구성 요소가 있습니다. 즉,

* **[콘텐츠 공급자](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/screens-as-cloud-service/configure-screens-cloud/using-screens-content-provider.html?lang=en)**: AEM Cloud Service 또는 AMS(Adobe Managed Services)에서 실행되는 스크린 추가 기능입니다. 스크린 컨텐츠 제공업체 를 사용하면 컨텐츠 작성자가 채널을 만들고 관리할 수 있습니다. 컨텐츠 작성자는 디스플레이 또는 플레이어 등록 만들기의 세부 사항에 대해 신경 쓰지 않고 새 컨텐츠를 추가하거나 컨텐츠를 편집할 수 있습니다. 컨텐츠 제공업체는 컨텐츠 개발, 디스플레이 또는 플레이어 등록에 대한 기본 세부 정보에서 추상화를 제공합니다.

* **[서비스 공급자](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/screens-as-cloud-service/configure-screens-cloud/navigating-to-screens-services-provider.html?lang=en)**: Adobe I/O 런타임 시 실행되는 디지털 서명 관리 서비스입니다. Screens 서비스 공급자를 사용하면 컨텐츠 작성자, 개발자 및 관리자가 컨텐츠가 채널에 추가되면 컨텐츠 재생에 대한 디스플레이 및 플레이어를 관리할 수 있습니다. 또한 화면 서비스 공급자는 높은 수준에서 컨텐츠가 재생되는 위치와 시점을 오케스트레이터에게 알려줍니다.


## 아키텍처 개요 {#architectural-overview}

AEM Screens as a Cloud Service 인터페이스에서는 채널에서 컨텐츠를 추가 및 관리하고, 스크린 as a Cloud Service용으로 특별히 설계된 디스플레이와 플레이어의 이름을 등록 및 관리할 수 있습니다. 즉, **Screens 서비스 공급자** 및 **스크린 컨텐츠 공급자**.

![이미지](/help/screens-cloud/assets/architecture-screenscloud.png)
