---
title: AEM Screens as a Cloud Service 소개
description: AEM Screens을 as a Cloud Service으로 이해합니다.
exl-id: b1cc0a63-ecd3-4d89-ac49-f384cc610cdc
source-git-commit: 07db10c4ee9cced7b6a697fe4f41c99eaba6a39f
workflow-type: tm+mt
source-wordcount: '365'
ht-degree: 97%

---


# AEM Screens as a Cloud Service 소개 {#introduction-screens-cloud}

Adobe Experience Manager(AEM) Screens as a Cloud Service를 사용하면 공공 장소에서 사용할 수 있도록 설계된 매력적인 동적 디지털 사이니지 경험을 만들 수 있습니다. 진화된 차세대 AEM Screens 제품이며 유용성과 확장성 분야에도 크게 도약한 제품입니다.

AEM Screens as a Cloud Service는 마케터가 대규모 동적 디지털 경험을 만들고 관리할 수 있도록 하는 디지털 사이니지 솔루션입니다. 또한 포괄적인 디지털 마케팅 전략의 일부로 다양한 유형의 실제 화면이 포함됩니다. Adobe의 옴니채널 서비스를 확장하여 일반 웹 및 모바일 채널뿐만 아니라 주변의 디지털 사이니지 채널을 포함하기도 합니다. AEM Screens as a Cloud Service를 통해 공공 장소의 모든 소비자와 방문자에게 제공되는 콘텐츠 생성, 콘텐츠 어셈블리, 트리거된 이벤트 관리 및 미디어 재생에 대해 깊이 이해하고 있어야 관련성 있고 상황에 적절하고 생산적이며 예측 가능한 사용자 경험을 사용할 수 있습니다.

## Screens as a Cloud Service의 구성 요소 이해 {#understanding-components}

Screens as a Cloud Service에는 다음의 두 가지 주요 구성 요소가 있습니다.

* **[Content Provider](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/screens-as-cloud-service/configure-screens-cloud/using-screens-content-provider.html)**&#x200B;는 AEM Cloud Service 또는 AMS(Adobe Managed Services)에서 실행되는 Screens 추가 기능입니다. Screens Content Provider를 통해 콘텐츠 작성자는 채널을 만들고 관리할 수 있습니다. 콘텐츠 작성자는 세부적인 디스플레이 생성 또는 플레이어 등록에 대한 걱정 없이 새 콘텐츠를 추가하고 콘텐츠를 편집할 수 있습니다. Content Provider는 개발 콘텐츠, 디스플레이 또는 플레이어 등록의 기본 세부 정보에서 추상적인 개념을 제공합니다.

* **[Services Provider](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/screens-as-cloud-service/configure-screens-cloud/navigating-to-screens-services-provider.html)**&#x200B;는 Adobe I/O Runtime에서 실행되는 디지털 사이니지 관리 서비스입니다. Screens Services Provider를 사용하여 콘텐츠를 채널에 추가하면 콘텐츠 작성자, 개발자 및 관리자는 콘텐츠 재생 디스플레이와 플레이어를 관리할 수 있습니다. 또한 Screens Services Provider는 고급 수준에서 재생되는 콘텐츠의 위치와 시기를 오케스트레이터에게 알려 줍니다.


## 아키텍처 개요 {#architectural-overview}

AEM Screens as a Cloud Service 사용자는 채널에서 콘텐츠를 추가 및 관리할 수 있습니다. Screens as a Cloud Service(즉, **Screens Services Provider** 및 **Screens Content Provider**)를 위해 특별히 설계된 인터페이스의 디스플레이와 플레이어를 등록 및 관리할 수 있습니다.

![이미지](/help/screens-cloud/assets/architecture-screenscloud.png)
