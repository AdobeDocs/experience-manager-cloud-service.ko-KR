---
title: 파이프라인 실행
description: 이 페이지에서는 Cloud Manager에서 Screens용 파이프라인을 Cloud Service 프로젝트로 실행하는 방법에 대해 설명합니다.
hide: true
hidefromtoc: true
index: false
source-git-commit: 83d2ac2d22827ebe13578b900907dd089d8d7e45
workflow-type: tm+mt
source-wordcount: '320'
ht-degree: 2%

---


# Cloud Manager {#run-pipeline-screens-cloud}에서 Cloud Service 프로그램으로 화면을 위한 파이프라인 실행

이 섹션에서는 Cloud Manager에서 파이프라인을 실행하고 프로그램에 대한 코드를 배포하는 방법에 대해 설명합니다.

>[!NOTE]
>Cloud Manager에서 프로그램에 대한 파이프라인을 실행하는 방법에 대해 알아보려면 [CD-CD 파이프라인 구성](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/configure-pipeline.html?lang=en) 및 [코드 배포](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/deploy-code.html?lang=en)를 참조하십시오.

## 목표 {#objective}

다음 섹션에서는 Cloud Manager에서 CI/CD 파이프라인을 구성하고 프로그램에 대한 코드를 배포하는 방법에 대해 설명합니다.

## Cloud Manager에서 스크린 프로젝트에 대한 파이프라인을 실행하는 단계 {#steps-branch-creation}

1. 환경 설정이 완료되면 Cloud Manager의 **개요** 페이지에 클릭유도문안 카드 업데이트가 표시됩니다.

   ![이미지](/help/screens-cloud/assets/onboarding/add-environ3.png)

1. **개요** 페이지에서 **파이프라인 설정**&#x200B;을 클릭합니다.

1. 분기를 선택한 후 **다음**&#x200B;을 클릭합니다.

   ![이미지](/help/screens-cloud/assets/onboarding/run-pipeline1.png)

1. **파이프라인 설정** 마법사에서 옵션을 선택합니다. **저장**&#x200B;을 클릭합니다.

   >[!NOTE]
   >파이프라인 설정 마법사의 옵션에 대해 알려면 [Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/configure-pipeline.html?lang=en)에서 파이프라인 설정 구성 을 참조하십시오.

   ![이미지](/help/screens-cloud/assets/onboarding/run-pipeline2-a.png)

1. 설정 파이프라인이 완료되면 클릭 유도 카드가 아래 그림과 같이 업데이트됩니다. 배포를 클릭합니다.

   >[!NOTE]
   >Cloud Manager의 배포 단계에 대해 알아보려면 [코드 배포](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/deploy-code.html?lang=en)를 참조하십시오.

   ![이미지](/help/screens-cloud/assets/onboarding/run-pipeline3.png)

1. **빌드**&#x200B;를 클릭하여 빌드 프로세스를 시작합니다.

   ![이미지](/help/screens-cloud/assets/onboarding/run-pipeline4.png)

1. 빌드 프로세스가 완료되면 Cloud Manager의 **개요** 페이지에서 **환경** 카드의 작성자 링크가 표시됩니다.

   ![이미지](/help/screens-cloud/assets/onboarding/run-pipeline5.png)

## 다음 기능 {#whats-next}

Cloud Manager에서 프로그램에 대한 환경을 설정하는 방법을 학습하면 이제 온보딩 프로세스의 다음 단계인 [Screens 서비스 제공업체로 이동](/help/screens-cloud/configuring/navigating-to-screens-services-provider.md)으로 이동할 수 있습니다.