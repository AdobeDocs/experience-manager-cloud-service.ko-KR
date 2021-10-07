---
title: Adobe Analytics와 통합
description: 'Adobe Analytics와 통합 '
feature: Administering
role: Admin
exl-id: e353a1fa-3e99-4d79-a0d1-40851bc55506
source-git-commit: d37193833d784f3f470780b8f28e53b473fd4e10
workflow-type: tm+mt
source-wordcount: '530'
ht-degree: 4%

---

# Adobe Analytics와 통합{#integrating-with-adobe-analytics}

Adobe Analytics과 AEM as a Cloud Service을 통합하여 웹 페이지 활동을 추적할 수 있습니다. 통합에는 다음이 필요합니다.

* touch UI를 사용하여 AEM as a Cloud Service에서 Analytics 구성을 만듭니다.
* [Adobe Launch](#analytics-launch)에서 Adobe Analytics을 확장으로 추가하고 구성하는 중입니다. Launch에 대한 자세한 내용은 [이 페이지](https://experienceleague.adobe.com/docs/experience-platform/tags/get-started/quick-start.html)를 참조하십시오.

이전 AEM 버전과 비교하여 프레임워크 지원은 AEM as a Cloud Service의 Analytics 구성에서 제공되지 않습니다. 대신 이제 Analytics 기능(JS 라이브러리)을 사용하여 AEM 사이트를 계측하는 사실상의 도구인 Adobe Launch를 통해 수행됩니다. Launch에서 Adobe Analytics 확장을 구성할 수 있고 Adobe Analytics에 데이터를 보내기 위한 규칙을 만드는 속성이 만들어집니다. Adobe Launch가 sitecatalyst에서 제공하는 analytics 작업을 대체했습니다.

>[!NOTE]
>
>기존 Analytics 계정이 없는 Adobe Experience Manager as a Cloud Service 고객은 Experience Cloud에 대한 Analytics Foundation Pack 액세스 권한을 요청할 수 있습니다. 이 기초 팩은 Analytics의 볼륨 제한을 제공합니다.

## Adobe Analytics 구성 만들기 {#analytics-configuration}

1. **도구** → **Cloud Services**&#x200B;로 이동합니다.
2. **Adobe Analytics**을 선택합니다.
   ![Adobe Analytics ](assets/analytics_screen2.png "WindowAdobe Analytics 창")
3. **만들기** 단추를 선택합니다.
4. 세부 사항을 입력하고(아래 참조) **연결**&#x200B;을 클릭합니다.

### 구성 매개 변수 {#configuration-parameters}

Adobe Analytics 구성 창에 있는 구성 필드는 다음과 같습니다.

![구성 ](assets/properties_field1.png "매개 변수구성 매개 변수")

| 속성 | 설명 |
|---|---|
| 회사 | Adobe Analytics 로그인 회사 |
| 사용자 이름 | Adobe Analytics API 사용 |
| 암호 | 인증에 사용되는 Adobe Analytics 암호 |
| 데이터 센터 | 계정이 연결된 Adobe Analytics 데이터 센터(예: San Jose, London) |
| 세그먼트 | 현재 보고 세트에 정의된 Analytics 세그먼트를 사용하는 옵션. Analytics 보고서는 세그먼트를 기반으로 필터링됩니다. 자세한 내용은 [이 페이지](https://experienceleague.adobe.com/docs/analytics/components/segmentation/seg-overview.html)를 참조하십시오. |
| 보고서 세트 | 데이터를 보내고 보고서를 가져오는 저장소입니다. 보고서 세트 는 선택한 웹 사이트, 웹 사이트 집합 또는 웹 사이트 페이지의 하위 집합에 대한 전체적이고 독립적인 보고를 정의합니다. 단일 보고서 세트에서 가져온 보고서를 볼 수 있으며, 요구 사항에 따라 언제든지 구성에서 이 필드를 편집할 수 있습니다. |

### 사이트에 구성 추가 {#add-configuration}

사이트에 Touch UI 구성을 적용하려면 다음 위치로 이동하십시오. **사이트** → **사이트 페이지** → **속성** → **고급** → **구성** → 구성 테넌트를 선택합니다.

## Launch를 사용하여 AEM 사이트에서 Adobe Analytics 통합 {#analytics-launch}

Adobe Analytics은 Launch 속성에서 확장으로 추가할 수 있습니다. Adobe Analytics에 대한 매핑 및 사후 호출을 수행하도록 규칙을 정의할 수 있습니다.

* 기본 사이트에 대한 Launch에서 Analytics 확장을 구성하는 방법을 알려면 [이 비디오](https://experienceleague.adobe.com/docs/analytics-learn/tutorials/implementation/via-adobe-launch/basic-configuration-of-the-analytics-launch-extension.html)를 시청하십시오.

* 규칙을 만들고 Adobe Analytics으로 데이터를 보내는 방법에 대한 자세한 내용은 [이 페이지](https://experienceleague.adobe.com/docs/core-services-learn/implementing-in-websites-with-launch/implement-solutions/analytics.html)을 참조하십시오.

>[!NOTE]
>
>기존(기존) 프레임워크는 여전히 작동하지만 Touch UI에서는 구성할 수 없습니다. Launch에서 변수 매핑 구성을 다시 빌드하는 것이 좋습니다.

>[!NOTE]
>
>Launch용 IMS 구성(기술 계정)은 AEM as a Cloud Service에서 미리 구성되어 있습니다. 사용자는 이 구성을 만들 필요가 없습니다.
