---
title: 계획 단계
description: 계획 단계
translation-type: tm+mt
source-git-commit: 3478827949356c4a4f5133b54c6cf809f416efef
workflow-type: tm+mt
source-wordcount: '395'
ht-degree: 8%

---


# 계획 {#planning-phase}

클라우드 서비스로 전환 작업을 시작하기 전에 먼저 AEM을 클라우드 서비스로 숙지하고 이에 대한 주목할 만한 변경 사항을 검토하고 교체되거나 더 이상 사용되지 않는 기능을 검토해야 합니다.

## 주요 변경 사항 {#notable-changes}

클라우드 서비스인 AEM에는 AEM 프로젝트 관리에 대한 새로운 기능과 여러 가지 기능이 포함되어 있습니다.

그러나 AEM을 클라우드 서비스로 사용하는 경우와 비교하여 AEM 온프레미스 또는 Adobe Managed Services가 서로 많은 차이점이 있습니다.

중요한 차이점을 [이해하려면 AEM Cloud Service](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/release-notes/aem-cloud-changes.html) 의 주목할 만한 변경 사항을 참조하십시오.

## 더 이상 사용되지 않는 기능 {#deprecated-features}

Adobe는 항상 이전 기능과의 호환성을 신중하게 고려하면서 전반적인 고객 가치를 향상하도록 오랜 시간에 걸쳐 오래된 기능을 새롭게 만들거나 더 현대적인 대안으로 교체하기 위해 제품 기능을 지속해서 평가합니다.

Experience Manager에서 [클라우드 서비스로 더 이상 사용되지 않는 기능](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/release-notes/deprecated-removed-features.html#deprecated-features) 에 대한 자세한 내용은 더 이상 사용되지 않는 기능을 참조하십시오.

## 계획 단계 이해 {#introduction}

다음 그림은 계획 단계 중 관련된 주요 단계를 보여줍니다.

![이미지](/help/move-to-cloud-service/assets/planning-phaseimg1.png)

### 클라우드 서비스 준비 평가 {#access-cloud-readiness}

계획 단계의 첫 번째 단계는 기존 AEM 버전에서 클라우드 서비스로 이동할 준비를 평가하고 리팩토링이 클라우드 서비스로 AEM과 호환되어야 하는 영역을 결정하는 것입니다.

주목할 만한 변경 사항 및 더 이상 사용되지 않는 기능에 대해 현재 AEM 소스 코드에 대한 포괄적인 평가를 수행하여 전환 과정에서 예상되는 작업 수준을 결정해야 합니다.

>[!NOTE]
>이미 Cloud Manager 및 클라우드 서비스 환경에 액세스할 수 있는 경우, 클라우드 서비스와 호환되도록 필요한 코드 변경 사항을 평가하려면 Cloud Manager 코드 품질 파이프라인에서 현재 코드를 실행하는 것이 좋습니다.

### 리소스 계획 검토 {#review-resource-planning}

Cloud Service로 이동하는 데 필요한 노력 수준을 예측했으면 리소스를 식별하고, 팀을 만들고, 전환 프로세스에 대한 역할과 책임을 매핑해야 합니다.

### KPI 설정 {#establish-kpis}

이전에 KPI(주요 성과 지표)를 설정하지 않은 경우 AEM(Adobe Experience Manager) 구현에 대한 KPI를 설정하여 팀이 가장 중요한 사항에 집중할 수 있도록 하는 것이 좋습니다.

비즈니스 목표 [에](https://guided.adobe.com/welcome/aem/part6.html) 적합한 KPI를 선택하는 방법은 KPI 개발을 참조하십시오.

