---
title: Adobe Analytics와 Experience Cloud 설정 자동화 통합
description: Experience Cloud 설정 자동화는 간단한 UI 마법사 인터페이스를 통해 Experience Platform Tags 및 Adobe Analytics와 Experience Manager Sites를 통합하고 측정하는 간단하고 자동화된 방법을 제공합니다. 내 사이트에 자동화된 설정을 사용하는 방법에 대해 알아보십시오.
feature: Administering
role: Admin
exl-id: 351ead2c-7b0d-4bd9-a020-47516948d467
source-git-commit: f91885a7d15c0ff927c6e10f65852f787cf26eb3
workflow-type: tm+mt
source-wordcount: '756'
ht-degree: 100%

---

# Adobe Analytics와 Experience Cloud 설정 자동화 통합 {#integrate-adobe-analytics-automation-setup}

Experience Cloud 설정 자동화는 간단한 UI 마법사 인터페이스를 통해 Experience Platform Tags 및 Adobe Analytics와 Experience Manager Sites를 통합하고 측정하는 간단하고 자동화된 방법을 제공합니다.

이제 그 어느 때보다 간단하게 Adobe Analytics와 AEM Sites를 통합할 수 있습니다. Experience Cloud 설정 자동화를 통해 몇 번의 클릭으로 사이트를 설정하고, 통합하고, 측정하여 성능 분석을 캡처함으로써 고객이 얼마나 효율적으로 참여하고 전환하는지 파악할 수 있습니다.

이 비디오에서는 Experience Cloud 설정 자동화를 사용하여 AEM 사이트를 Experience Platform Tags 및 Analytics와 통합하는 방법에 대해 살펴봅니다.

>[!VIDEO](https://video.tv.adobe.com/v/345372/?quality=12)

## 요구 사항

자동화 설정은 특히 [Adobe 클라이언트 데이터 레이어](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/data-layer/overview.html)가 활성화된 [AEM 핵심 구성 요소](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html)를 사용하여 구축된 AEM 사이트를 사용하여 작업하도록 설계되었습니다. [AEM Project Archetype](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html)을 사용하거나 [사이트 템플릿](/help/journey-sites/quick-site/create-site.md)을 사용하여 사이트를 생성함으로써 이러한 기능이 자동으로 활성화되어 있는 새 사이트를 생성할 수 있습니다.

## 사전 요구 사항 {#prerequisites}

이 기능을 사용하기 전에 사전 요구 사항 서비스가 해당 환경에 올바르게 설정되도록 아래 지침을 따르는 것이 중요합니다.

1. Adobe Admin Console(https://adminconsole.adobe.com/)에 로그인합니다.
1. 오른쪽 상단에서 올바른 IMS Org ID가 선택되어 있어야 합니다.
1. 제품 탐색 옵션을 클릭합니다.
1. “Adobe Experience Manager as a Cloud Service”가 IMS Org에 대해 프로비저닝되었는지 확인합니다.
1. “Adobe Analytics”가 IMS Org에 대해 프로비저닝되었는지 확인합니다.
1. Cloud Manager(https://experience.adobe.com/cloud-manager)로 이동합니다.
1. 적절한 프로그램을 선택합니다.
1. 환경이 Cloud Service 최신 버전인지 확인합니다(아닌 경우, 메뉴 옵션에서 업데이트를 선택).
1. Cloud Manager에서 Full Stack 파이프라인을 실행합니다.

이제 환경이 Experience Cloud 설정 자동화를 수행할 준비가 되었습니다.

## 설정 방법

1. **사이트**&#x200B;로 이동한 다음 Adobe Analytics와 통합하려는 사이트의 루트를 선택합니다.
1. 측면의 레일 메뉴를 확장한 다음 **Analytics 설정**&#x200B;을 탭합니다.

   이 옵션은 측면 레일의 새로운 옵션으로, 이 옵션을 사용하면 Experience Cloud 설정 자동화를 위한 컨트롤 및 상태를 제공하는 패널이 열립니다.
1. **Analytics 통합** 버튼을 탭합니다.
1. 그 결과로 표시되는 대화 상자에서 **보고서 세트 ID**&#x200B;의 이름을 입력합니다.

   이 문자열은 선택된 AEM 사이트에 대한 분석 데이터를 위한 데이터 저장소인 Adobe Analytics에서 새 [보고서 세트 ID](https://experienceleague.adobe.com/docs/analytics/admin/manage-report-suites/new-report-suite/t-create-a-report-suite.html?lang=ko)를 만들 때 사용됩니다. 제공된 문자열에는 고유성을 위해 환경 및 계층 식별자가 추가됩니다.

1. 페이지 및 패널을 새로 고침한 다음 **통합 상태 확인**&#x200B;을 탭하여 자동화 상태를 확인합니다.

   자동화 설정은 비동기적으로 발생합니다. **통합 상태 확인**&#x200B;에는 현재 통합 상태가 표시됩니다.

   * **진행 중** - 작업이 실행 중임을 나타냅니다.
   * **통합 완료** - 작업이 Analytics 및 Tags 통합, Tags 확장 및 Tags 규칙 설정 및 Adobe Analytics에서의 새 보고서 세트 생성을 완료했음을 나타냅니다.
   * **실패** - 자동화된 작업이 정상적으로 완료되지 않았음을 나타냅니다. 로그 링크를 클릭하여 이 작업에 대한 로그 파일을 확인하십시오.

## AEM 설정 유효성 검사

자동화가 완료되면 이제 사이트에서 Analytics 이벤트가 실행되는지 확인하십시오.

1. **사이트 편집기**&#x200B;를 사용하여 사이트의 페이지를 엽니다.
1. **게시됨으로 보기** 옵션을 사용하여 게시된 페이지 버전을 로드합니다.
1. 브라우저의 개발자 도구를 사용하여 네트워크 트래픽을 검사하고 **Tags** 및 `AppMeasurement.js` 파일이 로드되는지 검사합니다.
1. 브라우저의 콘솔을 검사하여 Adobe 클라이언트 데이터 레이어에 의해 페이지 및 구성 요소 수준 이벤트가 실행되고 수집되는지 확인합니다.

## Analytics 설정 유효성 검사

다음으로 Adobe Analytics로 이동하여 AEM 사이트의 이벤트에서 유입되는 데이터를 확인합니다.

1. 내 AEM 사이트와 동일한 IMS 조직의 Adobe Analytics로 이동합니다.
1. **보고서** > **참여** > **Adobe Experience Manager** > **사이트 성능 개요**&#x200B;로 이동하여 AEM Sites에 대한 새 개요 보고서를 생성합니다.
1. **보고서 열기**&#x200B;를 탭합니다.
1. 이전 활동에서 사용한 보고서 세트 이름과 일치하는 **보고서 세트 ID**&#x200B;를 선택합니다.
1. 시간이 지남에 따라 새 템플릿으로 흐르는 분석 데이터를 확인합니다.

   >[!NOTE]
   >
   > 새 통합의 경우 보고서가 데이터로 채워질 때까지 몇 시간 정도 소요될 수 있습니다.
