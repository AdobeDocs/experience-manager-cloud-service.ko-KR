---
title: Adobe Analytics과 Experience Cloud 설정 자동화 통합
description: Experience Cloud 설정 자동화는 간단한 UI 마법사 인터페이스를 통해 Experience Manager Sites을 Experience Platform Launch 및 Adobe Analytics과 통합 및 계측하는 간단하고 자동화된 방법을 제공합니다. 자체 사이트에서 자동화된 설정을 사용하는 방법을 알아봅니다.
feature: Administering
role: Admin
hide: true
hidefromtoc: true
index: false
exl-id: 351ead2c-7b0d-4bd9-a020-47516948d467
source-git-commit: 940a01cd3b9e4804bfab1a5970699271f624f087
workflow-type: tm+mt
source-wordcount: '639'
ht-degree: 0%

---

# Adobe Analytics과 Experience Cloud 설정 자동화 통합 {#integrate-adobe-analytics-automation-setup}

>[!CAUTION]
>
> 이 기능은 현재 내부 베타에 있습니다. Target 릴리스는 2022년 1분기에 제공됩니다.

Experience Cloud 설정 자동화는 간단한 UI 마법사 인터페이스를 통해 Experience Manager Sites을 Experience Platform Launch 및 Adobe Analytics과 통합 및 계측하는 간단하고 자동화된 방법을 제공합니다.

Adobe Analytics을 AEM Sites과 통합하는 것이 결코 간단하지 않았습니다. Experience Cloud 설정 자동화를 통해 성능 분석을 캡처하여 고객이 얼마나 잘 참여하고 전환하고 있는지 파악할 수 있도록 사이트를 설정, 통합 및 계측하여 몇 번의 클릭만으로 처리할 수 있습니다.

이 비디오에서는 Experience Cloud 설정 자동화를 사용하여 AEM 사이트를 Experience Platform Launch 및 Analytics와 통합하는 방법을 설명합니다.

>[!VIDEO](https://video.tv.adobe.com/v/339605/?quality=12)

## 요구 사항

자동화 설정은 AEM Site를 [AEM 코어 구성 요소](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=ko) 사용 [Adobe 클라이언트 데이터 레이어](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/data-layer/overview.html) 활성화되었습니다. 를 사용하여 이러한 기능을 자동으로 활성화하는 새 사이트를 생성할 수 있습니다. [AEM 프로젝트 원형](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html) 또는 다음을 사용하여 사이트를 만들어 [사이트 템플릿](/help/journey-sites/quick-site/create-site.md).

## 설정 방법

1. 다음으로 이동 **Sites** Adobe Analytics과 통합할 사이트의 루트를 선택합니다.
1. 사이드 레일 메뉴를 확장하고 를 누릅니다 **Analytics 설정**.

   사이드 레일에서 새 옵션으로서, Experience Cloud 설정 자동화를 위한 컨트롤과 상태를 제공하는 패널을 열 수 있습니다.
1. 탭하기 **Analytics 통합** 버튼을 클릭합니다.
1. 결과 대화 상자에서 **보고서 세트 ID**.

   이 문자열은 새 [보고서 세트 ID](https://experienceleague.adobe.com/docs/analytics/admin/manage-report-suites/new-report-suite/t-create-a-report-suite.html?lang=en) Adobe Analytics에서 선택한 AEM 사이트에 대한 analytics 데이터에 대한 데이터 저장소로 사용됩니다. 제공된 문자열에 환경 및 계층 식별자가 추가되어 고유성이 확보됩니다.

1. 페이지 및 패널 새로 고침 및 탭 **통합 상태 확인** 자동화의 상태를 확인합니다.

   자동화 설정은 비동기식으로 수행됩니다. 다음 **통합 상태 확인** 은 통합의 현재 상태를 표시합니다.

   * **진행 중** - 작업이 실행 중임을 나타냅니다.
   * **통합 완료** - 작업이 Analytics와 Launch 통합, Launch 확장 및 Launch 규칙 설정, Adobe Analytics에서 새 보고서 세트 만들기를 완료했음을 나타냅니다.
   * **실패** - 자동화된 작업을 성공적으로 완료할 수 없음을 나타냅니다. 로그 링크를 클릭하여 이 작업에 대한 로그 파일을 확인합니다.

## AEM 설정 유효성 검사

자동화가 완료되면 사이트가 이제 Analytics 이벤트를 실행하는지 확인합니다.

1. 를 사용하여 사이트에서 페이지를 엽니다. **사이트 편집기**.
1. 를 사용하십시오 **게시됨으로 보기** 게시된 페이지 버전을 로드하는 옵션.
1. 브라우저의 개발자 도구를 사용하여 네트워크 트래픽과 이를 검사합니다 **Launch** 및 `AppMeasurement.js` 이제 파일을 로드하는 중입니다.
1. Inspect 브라우저의 콘솔로 Adobe 클라이언트 데이터 레이어에서 페이지 및 구성 요소 수준 이벤트가 실행 및 수집되는지 확인합니다.

## Analytics 설정의 유효성 검사

다음으로 AEM 사이트의 이벤트에서 유입되는 데이터를 보려면 Adobe Analytics 로 이동합니다.

1. AEM 사이트와 동일한 IMS 조직의 Adobe Analytics으로 이동합니다.
1. 로 이동하는 AEM Sites에 대한 새 개요 보고서 만들기 **보고서** > **참여** > **Adobe Experience Manager** > **사이트 성능 개요**.
1. 탭 **보고서 열기**.
1. 을(를) 선택합니다 **보고서 세트 ID** 는 이전 연습에서 사용된 보고서 세트 이름과 일치합니다.
1. 시간에 따라 새 템플릿으로 analytics 데이터 흐름을 볼 수 있습니다.

   >[!NOTE]
   >
   > 새로운 통합을 사용하면 보고서가 데이터로 채워지기까지 몇 시간이 걸릴 수 있습니다.
