---
title: AEM Screens Cloud와 Adobe Analytics 통합
description: 이 페이지를 따라 AEM Screens과 Adobe Analytics의 획기적인 통합에 대해 알아보고 재생 증명을 제공합니다.
contentOwner: trushton
content-type: reference
products: SG_EXPERIENCEMANAGER/Cloud/SCREENS
topic-tags: administering
docset: aem65
role: Admin, Developer
level: Intermediate
exl-id: e22242ce-e5ce-4486-bba4-e6a89ac4fb5e
source-git-commit: abe5f8a4b19473c3dddfb79674fb5f5ab7e52fbf
workflow-type: tm+mt
source-wordcount: '408'
ht-degree: 0%

---

# AEM Screens Cloud와 Adobe Analytics 통합 {#adobe-analytics-integration-with-aem-screens}

이 섹션에서는 다음 주제를 다룹니다.

* **개요**
* **아키텍처 세부 정보**

## 개요 {#overview}

***AEM Screens*** 는 Adobe Analytics을 활용하므로 시장에서 독보적인 성과를 창출할 수 있습니다. 크로스 채널 분석 을 통해 위치에 표시된 콘텐츠를 다른 데이터 소스와 상호 연관시킬 수 있습니다.

AEM Screens은 Adobe Analytics과의 획기적인 통합을 제공하며 재생 증명을 제공합니다.

이 섹션에서는 Adobe Analytics과 AEM Screens 프로젝트 연결과 관련된 다음 기능에 대해 설명합니다.

* 장치별 재생 증명 보고 허용
* 자산별 재생 증명 보고 허용
* 모든 플레이어 이벤트가 캡처되고 타임스탬프가 지정되었는지 확인합니다.
* 플레이가 네트워크에 연결되어 있지 않은 경우 모든 플레이어 이벤트가 로컬에 저장되도록 합니다.
* 시간 경과에 따른 재생 이벤트를 추적하는 피드백 루프를 작성할 수 있도록 합니다.
* 시스템은 콘텐츠 작성자가 정의한 성공 기준에 따라 콘텐츠 및 레이아웃을 수정할 수 있습니다

AEM Screens과 Adobe Analytics 통합은 다음을 적용합니다 *목표*:

* 디지털 사이니지 구현에서 ROI 활성화
* 향후 사용 정보 수집 및 분석을 위한 기반으로 Analytics 통합

## 아키텍처 세부 정보 {#architectural-details}

AEM Screens 고객은 표시된 시간과 기간(집계된) 동안 표시되는 콘텐츠를 이해하려고 합니다. 이는 간판 솔루션의 일반적인 기능입니다. AEM Screens은 자체 분석을 구축하는 대신 Adobe Analytics을 사용하며, 이를 통해 위치에 표시된 콘텐츠를 다른 데이터 소스와 상호 연관시키는 데 도움이 되는 크로스 채널 분석이라는 시장에서 고유한 기능을 달성할 수 있습니다.

다음 아키텍처 다이어그램은 AEM Screens과 Adobe Analytics 통합에 대해 설명합니다.

![Adobe Analytics과 통합](/help/screens-cloud/assets/analytics-architecture.png)

## AEM Screens Cloud에서 Adobe Analytics 활성화 {#enabling-adobe-analytics-in-aem-screens-cloud}

Screens Cloud에서 Adobe 분석을 활성화하려면 Adobe 관계 관리자에게 문의하십시오.

## AEM Screens Cloud에서 Adobe Analytics 서비스 사용 {#using-adobe-analytics-service-in-aem-screens}

이 시나리오는 펌웨어 및 기기 화면 핵심 구성 요소에 있는 분석 서비스의 REST 호출을 통해 Analytics API를 호출하여 특정 사용 사례와 관련된 이벤트를 명시적으로 만들고 보내는 동시에 사용자 지정 개발 채널에서 Analytics로 사용자 지정 메시지를 보낼 수 있는 확장성을 허용합니다.

Analytics 이벤트는 indexedDB에 오프라인으로 저장되고 나중에 청크되어 클라우드로 전송됩니다.

>[!NOTE]
>이벤트의 시퀀싱 및 표준 데이터 모델에 대한 자세한 내용은 [AEM Screens용 Adobe Analytics 구성](https://experienceleague.adobe.com/docs/experience-manager-screens/user-guide/administering/analytics-integration/configuring-adobe-analytics-aem-screens.html) 을 참조하십시오.
