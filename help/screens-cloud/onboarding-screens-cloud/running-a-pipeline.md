---
title: 파이프라인 실행
description: 이 페이지에서는 Cloud Manager에서 Screens용 파이프라인을 Cloud Service 프로젝트로 실행하는 방법에 대해 설명합니다.
exl-id: 3203cff7-5668-4f50-a2c5-80ae474b439d
source-git-commit: 96a0dacf69f6f9c5744f224d1a48b2afa11fb09e
workflow-type: tm+mt
source-wordcount: '320'
ht-degree: 14%

---

# Cloud Manager에서 Screens용 파이프라인 as a Cloud Service 프로그램 실행 {#run-pipeline-screens-cloud}

이 섹션에서는 Cloud Manager에서 파이프라인을 실행하고 프로그램에 대한 코드를 배포하는 방법을 설명합니다.

>[!NOTE]
>을(를) 참조하십시오 [CD-CD 파이프라인 구성](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/configure-pipeline.html?lang=en) 및 [코드 배포](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/deploy-code.html?lang=en) cloud Manager에서 프로그램에 대한 파이프라인을 실행하는 방법을 알아봅니다.

## 목표 {#objective}

다음 섹션에서는 Cloud Manager에서 CI/CD 파이프라인을 구성하고 프로그램에 대한 코드를 배포하는 방법에 대해 설명합니다.

## Cloud Manager에서 Screens 프로젝트에 대한 파이프라인을 실행하는 단계 {#steps-branch-creation}

1. 환경 설정이 성공적으로 완료되면 Cloud Manager에 콜 투 액션 카드 업데이트가 표시됩니다. **개요** 페이지를 가리키도록 업데이트하는 중입니다.

   ![이미지](/help/screens-cloud/assets/onboarding/add-environ3.png)

1. 클릭 **파이프라인 설정** 다음에서 **개요** 페이지를 가리키도록 업데이트하는 중입니다.

1. 클릭 **다음** 분기를 선택한 후.

   ![이미지](/help/screens-cloud/assets/onboarding/run-pipeline1.png)

1. 다음에서 옵션을 선택합니다. **파이프라인 설정** 마법사. 클릭 **저장**.

   >[!NOTE]
   >파이프라인 설정 마법사의 옵션에 대한 자세한 내용은 다음을 참조하십시오. [Cloud Manager에서 파이프라인 설정 구성](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/configure-pipeline.html?lang=en) 을 참조하십시오.

   ![이미지](/help/screens-cloud/assets/onboarding/run-pipeline2-a.png)

1. 설정 파이프라인이 완료되면 아래 그림과 같이 콜 투 액션 카드가 업데이트됩니다. 배포를 클릭합니다.

   >[!NOTE]
   >Cloud Manager의 배포 단계에 대한 자세한 내용은 을 참조하십시오. [코드 배포](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/deploy-code.html?lang=en) 을 참조하십시오.

   ![이미지](/help/screens-cloud/assets/onboarding/run-pipeline3.png)

1. 클릭 **빌드** 빌드 프로세스를 시작합니다.

   ![이미지](/help/screens-cloud/assets/onboarding/run-pipeline4.png)

1. 빌드 프로세스가 완료되면 의 작성자 링크가 표시됩니다. **환경** Cloud Manager 의 카드 **개요** 페이지를 가리키도록 업데이트하는 중입니다.

   ![이미지](/help/screens-cloud/assets/onboarding/run-pipeline5.png)

## 다음 단계 {#whats-next}

Cloud Manager에서 프로그램의 환경을 설정하는 방법을 배우면 이제 온보딩 프로세스의 다음 단계로 이동할 준비가 되었습니다. [Screens Services Provider로 이동](/help/screens-cloud/configuring/navigating-to-screens-services-provider.md).
