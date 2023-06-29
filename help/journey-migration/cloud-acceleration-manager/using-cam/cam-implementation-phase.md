---
title: Cloud Acceleration Manager의 구현 단계
description: 이 페이지에서는 Cloud Acceleration Manager의 구현 단계에 대한 개요를 제공합니다.
exl-id: e6ac88f0-4b3f-43a1-98bc-8c6608713784
source-git-commit: 1994b90e3876f03efa571a9ce65b9fb8b3c90ec4
workflow-type: tm+mt
source-wordcount: '662'
ht-degree: 4%

---

# Cloud Acceleration Manager의 구현 단계 {#implementation-phase-cam}

구현 단계에는 다음이 포함됩니다.

* [로컬 개발](#local-development)
* [코드 리팩터링](#code-refactoring)
* [AEM as a Cloud Service 배포](#aem-as-a-cloud-service-deployment)
* [컨텐츠 전송](#content-transfer)


프로젝트 카드를 클릭하면 프로젝트 랜딩 페이지를 열고 로 이동할 수 있습니다. **구현** 다음 그림과 같은 섹션입니다.

![이미지](/help/journey-migration/cloud-acceleration-manager/assets/implementation-1.png)

>[!NOTE]
>다음을 참조하십시오 [Cloud Acceleration Manager에서 프로젝트 생성 및 관리](getting-started-cam.md#create-project) 자세히 알아보십시오.


## 로컬 개발 카드 사용 {#local-development}

로컬 개발 카드는 마이그레이션 여정의 구현 단계를 시작할 때 로컬 AEM 개발 환경을 설정하는 데 도움이 되는 모든 관련 컨텐츠를 제공합니다.

로컬 개발 활동 카드를 살펴볼 수 있도록 다음 섹션을 따르십시오.

1. 클릭 **보기** 다음에서 **로컬 개발** 카드.

   ![이미지](/help/journey-migration/cloud-acceleration-manager/assets/implementation-2.png)

1. 컨텐츠 캐러셀은 마이그레이션 여정의 이 단계에 대한 관련 정보를 표시합니다.

   ![이미지](/help/journey-migration/cloud-acceleration-manager/assets/implementation-3.png)


## 코드 리팩터링 카드 사용 {#code-refactoring}

코드 리팩터링 활동 카드는 모든 관련 정보를 제공하며 AEM as a Cloud Service으로 이동할 때 검토하고 해결할 코드 리팩터링 영역을 강조 표시합니다.

코드 리팩터링 활동 카드를 살펴볼 수 있도록 다음 섹션을 따르십시오.

1. 클릭 **리뷰** 다음에서 **코드 리팩터링** 활동 카드.

   ![이미지](/help/journey-migration/cloud-acceleration-manager/assets/implementation-4.png)

1. 이 페이지에는 심각도 수준별로 구성된 코드 리팩터링 활동 목록이 표시됩니다. 강조 표시된 두 개의 아이콘을 클릭하면 자세한 내용을 알 수 있습니다.

   이 페이지에는 코드 리팩터링 고려 사항이 세 개의 서로 다른 탭에 표시됩니다.

   * 개요
   * Dispatcher
   * 테스트

>[!NOTE]
>모범 사례 분석기에서 다루지 않는 몇 가지 추가 영역을 이해하려면 이 탭의 내용을 검토하십시오.

다음 **디스패처** 탭에서는 클라우드 환경에 배포하기 전에 AEM as a Cloud Service Apache 및 Dispatcher 구성을 구성하는 방법과 이를 로컬에서 확인하고 실행하는 방법에 대해 설명합니다. 또한 클라우드 환경에서의 디버깅에 대해서도 설명합니다.

![이미지](/help/journey-migration/cloud-acceleration-manager/assets/coderefactoring-2.png)

다음 **테스트** 탭은 기능, 경험 감사 및 UI 테스트에 대한 정보를 제공합니다.

![이미지](/help/journey-migration/cloud-acceleration-manager/assets/coderefactoring-3.png)


## AEM as a Cloud Service 배포 카드 사용 {#aem-as-a-cloud-service-deployment}

AEM as a Cloud Service AEM 배포 카드는 코드를 as a Cloud Service으로 배포하는 데 도움이 되는 모든 관련 콘텐츠를 제공합니다.

AEM as a Cloud Service 배포 카드 활동 카드를 탐색할 수 있도록 다음 섹션을 따르십시오.

1. 클릭 **보기** 다음에서 **AEM as a Cloud Service 배포** 활동 카드.

   ![이미지](/help/journey-migration/cloud-acceleration-manager/assets/implementation-6.png)

1. 컨텐츠 캐러셀은 마이그레이션 여정의 이 단계에 대한 관련 정보를 표시합니다.

   ![이미지](/help/journey-migration/cloud-acceleration-manager/assets/aem-deployment-card.png)


## 컨텐츠 전송 카드 사용 {#content-transfer}

컨텐츠 전송 카드를 사용하면 현재 AEM AEM 인스턴스에서 as a Cloud Service으로 컨텐츠 전송을 시작 및 관리할 수 있습니다.

콘텐츠 전송 활동 카드를 살펴볼 수 있도록 다음 섹션을 따르십시오.

1. 클릭 **리뷰** 다음에서 **컨텐츠 전송** 활동 카드.

   ![이미지](/help/journey-migration/cloud-acceleration-manager/assets/contenttransfer-1.png)

1. 콘텐츠 전송을 시작하려면 마이그레이션 세트를 만들어야 합니다. 클릭 **마이그레이션 세트 만들기**. 마이그레이션 세트는 콘텐츠를 AEM에 as a Cloud Service으로 전송할 수 있도록 해줍니다.

   ![이미지](/help/journey-migration/cloud-acceleration-manager/assets/contenttransfer-2.png)

   >[!NOTE]
   >오랫동안 사용하지 않으면 마이그레이션 세트가 만료됩니다. 다음을 참조하십시오 [마이그레이션 세트 만료](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/overview-content-transfer-tool.md#migration-set-expiry) 을 참조하십시오.

   >[!NOTE]
   >다음을 참조하십시오 [전제 조건](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/prerequisites-content-transfer-tool.html) 및 [우수 사례 및 지침](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/overview-content-transfer-tool.html) 컨텐츠 전송 도구를 사용하기 전에.

1. 콘텐츠 전송 도구 를 다운로드하여 설치하고 마이그레이션 세트를 채우고 콘텐츠 전송의 추출 단계를 완료합니다. 리뷰 [컨텐츠 전송 도구 시작하기](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/getting-started-content-transfer-tool.html?lang=ko-KR) 콘텐츠 전송 도구 사용 방법을 알아봅니다.

1. AEM에서 환경으로 마이그레이션 세트의 컨텐츠를 as a Cloud Service으로 수집하려면 수집을 시작해야 합니다. 다음으로 이동 **수집 작업** 및 클릭 **새로운 수집**. 리뷰 [Target에 컨텐츠 수집](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/ingesting-content.html) 따라서 콘텐츠 전송의 수집 단계를 완료하는 방법을 배울 수 있습니다.

   ![이미지](/help/journey-migration/cloud-acceleration-manager/assets/contenttransfer-3.png)

<!--### Estimating Content Transfer Time {#calculating}

A Content Transfer Tool calculator has been provided to estimate how long it could take to complete the content transfer activity. You can use the content repository size slider to select the size that applies to your project. The transfer times vary for the extraction and ingestion phases. 

   ![image](/help/journey-migration/cloud-acceleration-manager/assets/contenttransfer-4.png)

   >[!NOTE]
   >These times are estimates only. Factor such as network speeds and time to scale up instances have not been accounted for in these estimates.

To estimate the size of the AEM Repository, you can run the Disk Usage report under `http://HOST:PORT/etc/reports/diskusage.html`. 

You can also estimate the size of specific repository paths by using the `path` parameter, for example, `http://HOST:PORT/etc/reports/diskusage.html?path=/content/dam`. -->

## 다음 단계 {#whats-next}

Cloud Acceleration Manager에 로그온하는 방법과 구현 단계를 사용하는 방법을 배운다면 의 다음 단계를 검토할 준비가 된 것입니다. [실행 단계](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-acceleration-manager/using-cam/cam-golive-phase.html).
