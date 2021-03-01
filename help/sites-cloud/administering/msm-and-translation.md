---
title: 다중 사이트 관리자 및 번역
description: 프로젝트에서 컨텐츠를 재사용하고 AEM에서 다국어 웹 사이트를 관리하는 방법을 살펴봅니다.
translation-type: tm+mt
source-git-commit: 4fc4dbe2386d571fa39fd6d10e432bb2fc060da1
workflow-type: tm+mt
source-wordcount: '372'
ht-degree: 0%

---


# 다중 사이트 관리자 및 번역 {#msm-and-translation}

Adobe Experience Manager에 내장된 멀티 사이트 관리자 및 번역 도구를 사용하면 컨텐츠 현지화를 간소화할 수 있습니다.

* MSM(Multi Site Manager) 및 해당 Live Copy 기능을 사용하면 여러 위치에서 동일한 사이트 컨텐츠를 사용할 수 있고 다음을 변경할 수 있습니다.
   * [컨텐츠 재활용:다중 사이트 관리자 및 Live Copy](msm/overview.md)
* 번역 기능을 사용하면 다국어 웹 사이트를 제작 및 유지 관리할 수 있도록 페이지 컨텐츠 번역 작업을 자동화할 수 있습니다.
   * [다국어 사이트의 컨텐츠 번역](translation/overview.md)

이 두 기능은 모두 [다국적 및 다국어](#multinational-and-multilingual-sites)인 웹 사이트에 맞게 결합할 수 있습니다.

## 다국적 및 다국어 사이트 {#multinational-and-multilingual-sites}

다중 사이트 관리자 및 번역 워크플로우의 통합을 통해 다국적 사이트와 다국어 사이트의 컨텐츠를 효율적으로 만들 수 있습니다.

일반적으로 한 언어와 특정 국가에서 마스터 사이트를 만든 다음 필요한 경우 번역을 사용하여 해당 컨텐츠를 다른 사이트의 기초로 사용합니다.

1. [마스터 ](translation/overview.md) 사이트를 다른 언어로 변환합니다.
1. [다중 사이트 관리자](msm/overview.md)를 사용하여 다음을 수행합니다.
   1. 마스터 사이트의 컨텐트와 번역을 다시 사용하여 다른 국가 및 문화를 위한 사이트를 만들 수 있습니다.
   1. 필요한 경우 Live Copy의 요소를 분리하여 현지화 세부 사항을 추가합니다.

>[!TIP]
>
>다중 사이트 관리자의 사용을 한 언어 내의 컨텐츠로 제한합니다.
>
>예: 영어 마스터를 사용하여 미국, 캐나다, 영국 등의 영어 버전의 페이지를 만듭니다. 페이지를 만들고 프랑스어 마스터를 사용하여 프랑스, 스위스, 캐나다 등의 프랑스어 버전 페이지를 만듭니다.

다음 다이어그램은 기본 개념이 교차하는 방식을 보여 줍니다(관련된 모든 레벨/요소는 표시되지 않음).

![현지화 개요](assets/localization-overview.png)

이와 유사한 시나리오에서는 MSM이 이와 같이 다른 언어 버전을 관리하지 않습니다.

* [](msm/overview.md) MSM언어 경계 내에서 블루프린트(즉, 글로벌 마스터)에서 Live Copy(즉, 로컬 사이트)로 번역된 컨텐츠의 배포를 관리합니다.
* 제3자 번역 관리 서비스와 함께 AEM의 [번역](translation/overview.md) 통합 기능은 언어를 관리하고 컨텐츠를 이러한 다른 언어로 번역합니다.

고급 사용 사례의 경우 MSM은 언어 마스터 간에 사용될 수 있습니다.

>[!TIP]
>
>모든 사용 사례의 경우 다음 우수 사례를 읽는 것이 좋습니다.
>
>* [MSM에 대한 우수 사례](msm/best-practices.md)
>* [번역 우수 사례](translation/best-practices.md)

