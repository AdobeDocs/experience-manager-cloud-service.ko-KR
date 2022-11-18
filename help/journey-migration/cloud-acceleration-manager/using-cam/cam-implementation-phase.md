---
title: Cloud Acceleration Manager의 구현 단계
description: 이 페이지에서는 Cloud Acceleration Manager의 구현 단계에 대한 개요를 제공합니다.
exl-id: e6ac88f0-4b3f-43a1-98bc-8c6608713784
source-git-commit: dbf01e5bd9ee83e378b4297d2f3d341d548f9238
workflow-type: tm+mt
source-wordcount: '683'
ht-degree: 4%

---

# Cloud Acceleration Manager의 구현 단계 {#implementation-phase-cam}

구현 단계에는 다음이 포함됩니다.

* [로컬 개발](#local-development)
* [코드 리팩터링](#code-refactoring)
* [AEM as a Cloud Service 배포](#aem-as-a-cloud-service-deployment)
* [컨텐츠 전송](#content-transfer)


프로젝트 카드를 클릭하여 프로젝트 랜딩 페이지를 열고 다음 위치로 이동합니다 **구현** 섹션을 참조하십시오.

![이미지](/help/journey-migration/cloud-acceleration-manager/assets/implementation-1.png)

>[!NOTE]
>을(를) 참조하십시오. [Cloud Acceleration Manager에서 프로젝트 생성 및 관리](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-acceleration-manager/using-cam/getting-started-cam.html?lang=en#create-project) 추가 정보


## 로컬 개발 카드 사용 {#local-development}

로컬 개발 카드는 마이그레이션 여정의 구현 단계를 시작할 때 로컬 AEM 개발 환경을 설정하는 데 도움이 되는 모든 관련 컨텐츠를 제공합니다.

다음 섹션을 통해 로컬 개발 활동 카드를 살펴보십시오.

1. 을(를) 클릭합니다. **보기** 단추 **로컬 개발** 카드.

   ![이미지](/help/journey-migration/cloud-acceleration-manager/assets/implementation-2.png)

1. 컨텐츠 회전판에 마이그레이션 여정의 이 단계에 대한 관련 정보가 표시됩니다.

   ![이미지](/help/journey-migration/cloud-acceleration-manager/assets/implementation-3.png)


## 코드 리팩터링 카드 사용 {#code-refactoring}

코드 리팩터링 활동 카드는 모든 관련 정보를 제공하며 AEM as a Cloud Service으로 이동할 때 검토하고 해결해야 하는 코드 리팩터링 영역을 강조 표시합니다.

코드 리팩터링 활동 카드를 탐색하려면 다음 섹션을 따르십시오.

1. 을(를) 클릭합니다. **검토** 단추 **코드 리팩터링** 활동 카드.

   ![이미지](/help/journey-migration/cloud-acceleration-manager/assets/implementation-4.png)

1. 이 페이지에는 심각도 수준별로 구성된 코드 리팩터링 활동 목록이 표시됩니다. 강조 표시된 두 개의 아이콘을 클릭하여 자세히 알아볼 수 있습니다.

   이 페이지에는 다음 세 개의 서로 다른 탭에 코드 리팩터링 고려 사항이 표시됩니다.

   * 개요
   * Dispatcher
   * 테스트

>[!NOTE]
>모범 사례 분석기에서 다루지 않는 몇 가지 추가 영역을 이해하려면 이 탭의 컨텐츠를 검토하십시오.

다음 **Dispatcher** 탭에서는 AEM as a Cloud Service Apache 및 Dispatcher 구성을 구성하는 방법과 클라우드 환경에 배포하기 전에 로컬로 확인하고 실행하는 방법에 대해 설명합니다. 클라우드 환경에서의 디버깅에도 대해 설명합니다.

![이미지](/help/journey-migration/cloud-acceleration-manager/assets/coderefactoring-2.png)

다음 **테스트** 탭은 기능, 경험 감사 및 UI 테스트에 대한 정보를 제공합니다.

![이미지](/help/journey-migration/cloud-acceleration-manager/assets/coderefactoring-3.png)


## AEM as a Cloud Service 배포 카드 사용 {#aem-as-a-cloud-service-deployment}

AEM as a Cloud Service 배포 카드는 AEM as a Cloud Service에 코드를 배포하는 데 도움이 되는 모든 관련 컨텐츠를 제공합니다.

다음 섹션을 통해 AEM as a Cloud Service 배포 카드 활동 카드를 살펴보십시오.

1. 을(를) 클릭합니다. **보기** 단추 **AEM as a Cloud Service 배포** 활동 카드.

   ![이미지](/help/journey-migration/cloud-acceleration-manager/assets/implementation-6.png)

1. 컨텐츠 회전판에 마이그레이션 여정의 이 단계에 대한 관련 정보가 표시됩니다.

   ![이미지](/help/journey-migration/cloud-acceleration-manager/assets/aem-deployment-card.png)


## 컨텐츠 전송 카드 사용 {#content-transfer}

컨텐츠 전송 카드를 사용하면 현재 AEM 인스턴스에서 AEM as a Cloud Service으로 컨텐츠 전송을 시작 및 관리할 수 있습니다.

컨텐츠 전송 활동 카드를 탐색하려면 이 섹션을 따르십시오.

1. 을(를) 클릭합니다. **검토** 단추 **컨텐츠 전송** 활동 카드.

   ![이미지](/help/journey-migration/cloud-acceleration-manager/assets/contenttransfer-1.png)

1. 컨텐츠 전송을 시작하려면 마이그레이션 세트를 만들어야 합니다. 클릭 **마이그레이션 세트 만들기**. 마이그레이션 세트를 사용하면 컨텐츠를 AEM as a Cloud Service으로 전송할 수 있습니다.

   ![이미지](/help/journey-migration/cloud-acceleration-manager/assets/contenttransfer-2.png)

   >[!NOTE]
   >다음 문서를 검토하십시오 [전제 조건](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/prerequisites-content-transfer-tool.html?lang=en) 그리고 [모범 사례 및 지침](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/overview-content-transfer-tool.html?lang=en) 컨텐츠 전송 도구를 사용하기 전에

1. 컨텐츠 전송 도구를 다운로드하고 설치하여 마이그레이션 세트를 채우고 컨텐츠 전송의 추출 단계를 완료해야 합니다. 검토 [컨텐츠 전송 도구 시작하기](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/getting-started-content-transfer-tool.html?lang=ko) 컨텐츠 전송 도구 사용 방법을 알아봅니다.

1. 마이그레이션 세트의 컨텐츠를 AEM as a Cloud Service의 환경으로 수집하려면 수집을 시작해야 합니다. 다음으로 이동 **수집 작업** 을(를) 클릭합니다. **새 수집**. 검토 [Target에 컨텐츠 수집](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/ingesting-content.html?lang=en) 컨텐츠 전송의 수집 단계를 완료하는 방법을 알아봅니다.

   ![이미지](/help/journey-migration/cloud-acceleration-manager/assets/contenttransfer-3.png)

<!--### Estimating Content Transfer Time {#calculating}

A Content Transfer Tool calculator has been provided to estimate how long it could take to complete the content transfer activity. You can use the content repository size slider to select the size that applies to your project. The transfer times vary for the extraction and ingestion phases. 

   ![image](/help/journey-migration/cloud-acceleration-manager/assets/contenttransfer-4.png)

   >[!NOTE]
   >These times are estimates only. Factor such as network speeds and time to scale up instances have not been accounted for in these estimates.

To estimate the size of the AEM Repository, you can run the Disk Usage report under `http://HOST:PORT/etc/reports/diskusage.html`. 

You can also estimate the size of specific repository paths by using the `path` parameter, for example, `http://HOST:PORT/etc/reports/diskusage.html?path=/content/dam`. -->

## 다음 단계 {#whats-next}

Cloud Acceleration Manager에 로그인하는 방법과 구현 단계를 활용하는 방법을 학습하면 이제 의 다음 단계를 검토할 준비가 되었습니다. [라이브 단계 이동](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-acceleration-manager/using-cam/cam-golive-phase.html?lang=en).
