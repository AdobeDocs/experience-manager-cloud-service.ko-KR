---
title: 테스트 결과 개요 - Cloud Services
description: 테스트 결과 개요 - Cloud Services
translation-type: tm+mt
source-git-commit: 25ba5798de175b71be442d909ee5c9c37dcf10d4
workflow-type: tm+mt
source-wordcount: '112'
ht-degree: 16%

---


# 개요 {#overview}

클라우드 서비스에 대한 Cloud Manager 파이프라인 실행은 스테이지 환경에서 실행되는 테스트 실행을 지원합니다. 이는 실행 중인 AEM 환경에 대한 액세스 권한 없이 오프라인으로 실행되는 빌드 및 단위 테스트 단계 동안 실행된 테스트와 대비됩니다.

Cloud Manager에서 Cloud Services 파이프라인을 지원하는 세 가지 범주가 있습니다.

1. [코드 품질 테스트](/help/implementing/cloud-manager/code-quality-testing.md)
1. [기능 테스트](/help/implementing/cloud-manager/functional-testing.md)
1. [컨텐츠 감사 테스트](/help/implementing/cloud-manager/content-audit-testing.md)

이러한 테스트는 다음을 수행할 수 있습니다.

* 고객 서면
* Adobe
* 오픈 소스 툴(Google의 Lighthouse 제공)

   >[!NOTE]
   > 고객이 작성한 테스트와 Adobe으로 작성된 테스트 모두 이러한 유형의 테스트를 실행하기 위해 설계된 통합 인프라에서 실행됩니다.

