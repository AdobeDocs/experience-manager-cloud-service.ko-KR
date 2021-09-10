---
title: Cloud Acceleration Manager의 구현 단계
description: 이 페이지에서는 Cloud Acceleration Manager의 구현 단계에 대한 개요를 제공합니다.
exl-id: 4ea13f12-7251-448f-9f54-c8d710aef2ba
source-git-commit: e786fe40d97294b4ab5e8657920f2ecbb401d8e9
workflow-type: tm+mt
source-wordcount: '674'
ht-degree: 2%

---

# Cloud Acceleration Manager의 구현 단계 {#implementation-phase-cam}

구현 단계에는 다음이 포함됩니다.

* [로컬 개발](#local-development)
* [코드 리팩터링](#code-refactoring)
* [AEM as a Cloud Service 배포](#aem-as-a-cloud-service-deployment)
* [컨텐츠 전송](#content-transfer)


프로젝트 카드를 클릭하여 프로젝트 랜딩 페이지를 열고 아래 그림과 같이 **구현** 섹션으로 이동합니다.

![이미지](/help/move-to-cloud-service/cloud-acceleration-manager/assets/implementation-1.png)

>[!NOTE]
>자세한 내용은 [Cloud Acceleration Manager에서 프로젝트 만들기 및 관리](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-acceleration-manager/using-cam/getting-started-cam.html?lang=en#create-project) 를 참조하십시오.


## 로컬 개발 카드 사용 {#local-development}

로컬 개발 카드는 마이그레이션 여정의 구현 단계를 시작할 때 로컬 AEM 개발 환경을 설정하는 데 도움이 되는 모든 관련 컨텐츠를 제공합니다.

다음 섹션을 통해 로컬 개발 활동 카드를 살펴보십시오.

1. **Local Development** 카드에서 **보기** 단추를 클릭합니다.

   ![이미지](/help/move-to-cloud-service/cloud-acceleration-manager/assets/implementation-2.png)

1. 컨텐츠 회전판에 마이그레이션 여정의 이 단계에 대한 관련 정보가 표시됩니다.

   ![이미지](/help/move-to-cloud-service/cloud-acceleration-manager/assets/implementation-3.png)


## 코드 리팩터링 카드 사용 {#code-refactoring}

코드 리팩터링 활동 카드 카드는 모든 관련 정보를 제공하며 Cloud Service으로 AEM으로 이동할 때 검토하고 해결해야 하는 코드 리팩터링 영역을 강조 표시합니다.

코드 리팩터링 활동 카드를 탐색하려면 다음 섹션을 따르십시오.

1. **코드 리팩터링** 활동 카드에서 **검토** 단추를 클릭합니다.

   ![이미지](/help/move-to-cloud-service/cloud-acceleration-manager/assets/implementation-4.png)

1. 이 페이지에는 심각도 수준별로 구성된 코드 리팩터링 활동 목록이 표시됩니다. 강조 표시된 두 개의 아이콘을 클릭하여 자세히 알아볼 수 있습니다.

   이 페이지에는 다음 세 개의 서로 다른 탭에 코드 리팩터링 고려 사항이 표시됩니다.

   * 개요
   * Dispatcher
   * 테스트

>[!NOTE]
>모범 사례 분석기에서 다루지 않는 몇 가지 추가 영역을 이해하려면 이 탭의 컨텐츠를 검토하십시오.

**Dispatcher** 탭에서는 AEM을 Cloud Service Apache 및 Dispatcher 구성으로 구성하는 방법과 클라우드 환경에 배포하기 전에 로컬로 확인하고 실행하는 방법에 대한 정보를 제공합니다. 클라우드 환경에서의 디버깅에도 대해 설명합니다.

![이미지](/help/move-to-cloud-service/cloud-acceleration-manager/assets/coderefactoring-2.png)

**테스트** 탭은 기능, 경험 감사 및 UI 테스트에 대한 정보를 제공합니다.

![이미지](/help/move-to-cloud-service/cloud-acceleration-manager/assets/coderefactoring-3.png)


## AEM을 Cloud Service 배포 카드로 사용 {#aem-as-a-cloud-service-deployment}

AEM as a Cloud Service 배포 카드는 AEM as a Cloud Service에 코드를 배포하는 데 도움이 되는 모든 관련 컨텐츠를 제공합니다.

AEM as a Cloud Service 배포 카드 활동 카드로 살펴보려면 이 섹션을 따르십시오.

1. **AEM as a Cloud Service 배포** 활동 카드로 **보기** 단추를 클릭합니다.

   ![이미지](/help/move-to-cloud-service/cloud-acceleration-manager/assets/implementation-6.png)

1. 컨텐츠 회전판에 마이그레이션 여정의 이 단계에 대한 관련 정보가 표시됩니다.

   ![이미지](/help/move-to-cloud-service/cloud-acceleration-manager/assets/aem-deployment-card.png)


## 컨텐츠 전송 카드 사용 {#content-transfer}

컨텐츠 전송 활동 카드는 컨텐츠 전송 도구를 사용하여 컨텐츠를 현재 AEM 인스턴스에서 Cloud Service으로 이동할 때 검토해야 하는 지침과 고려 사항을 제공합니다.

컨텐츠 전송 활동 카드를 탐색하려면 이 섹션을 따르십시오.

1. **컨텐츠 전송** 활동 카드에서 **보기** 단추를 클릭합니다.

   ![이미지](/help/move-to-cloud-service/cloud-acceleration-manager/assets/implementation-8.png)

1. 컨텐츠 회전판에 마이그레이션 여정의 이 단계에 대한 관련 정보가 표시됩니다.

   ![이미지](/help/move-to-cloud-service/cloud-acceleration-manager/assets/content-transfertool-card.png)

   >[!NOTE]
   >컨텐츠 전송 도구를 사용하기 전에 [사전 요구 사항](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/prerequisites-content-transfer-tool.html?lang=en) 및 [우수 사례 및 지침](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/overview-content-transfer-tool.html?lang=en)을 검토하십시오.

### 컨텐츠 전송 시간 추정 {#calculating}

컨텐츠 전송 활동을 완료하는 데 걸리는 시간을 예상하기 위해 새로운 컨텐츠 전송 도구 계산기가 제공되었습니다. 컨텐츠 저장소 크기 슬라이더를 사용하여 프로젝트에 적용되는 크기를 선택할 수 있습니다. 전송 시간은 추출 및 수집 단계에 따라 다릅니다.

>[!NOTE]
>지금은 추정일 뿐입니다. 이러한 추정치에는 네트워크 속도 및 인스턴스 확장 시간과 같은 요소가 언급되지 않았습니다.

AEM 저장소의 크기를 추정하는 데 필요한 경우 `http://HOST:PORT/etc/reports/diskusage.html`에서 디스크 사용량 보고서를 실행할 수 있습니다.

`path` 매개 변수(예: `http://HOST:PORT/etc/reports/diskusage.html?path=/content/dam`)를 사용하여 특정 저장소 경로의 크기를 예측할 수도 있습니다.

## 다음은 무엇입니까? {#whats-next}

Cloud Acceleration Manager에 로그인하는 방법과 구현 단계를 활용하는 방법을 학습하면 이제 [Go Live Phase](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-acceleration-manager/using-cam/cam-golive-phase.html?lang=en)에서 다음 단계를 검토할 준비가 되었습니다.
