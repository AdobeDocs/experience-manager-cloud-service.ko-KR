---
title: 파이프라인 실행
description: 이 페이지에서는 Cloud Manager에서 Screens as Cloud Service 프로젝트용 파이프라인을 실행하는 방법을 설명합니다.
exl-id: 3203cff7-5668-4f50-a2c5-80ae474b439d
feature: Screens Deployments
role: Admin, Developer, User
source-git-commit: f9ba9fefc61876a60567a40000ed6303740032e1
workflow-type: tm+mt
source-wordcount: '271'
ht-degree: 4%

---

# Cloud Manager에서 Screens as a Cloud Service Pipeline 프로그램을 실행 {#run-pipeline-screens-cloud}

이 섹션에서는 Cloud Manager에서 파이프라인을 실행하고 프로그램에 대한 코드를 배포하는 방법에 대해 설명합니다.

>[!NOTE]
>Cloud Manager에서 프로그램에 대한 파이프라인을 실행하는 방법은 [CI-CD 파이프라인 구성](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/cicd-pipelines/configuring-production-pipelines.html) 및 [코드 배포](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/deploy-code.html)를 참조하십시오.

## 목표 {#objective}

다음 섹션에서는 Cloud Manager에서 CI/CD 파이프라인을 구성하고 프로그램에 대한 코드를 배포하는 방법에 대해 설명합니다.

## Cloud Manager에서 Screens 프로젝트에 대한 파이프라인을 실행하는 단계 {#steps-branch-creation}

1. 환경 설정이 완료되면 Cloud Manager의 **개요** 페이지에 콜 투 액션 카드 업데이트가 표시됩니다.

   ![이미지](/help/screens-cloud/assets/onboarding/add-environ3.png)

1. **개요** 페이지에서 **파이프라인 설정**&#x200B;을 클릭합니다.

1. 분기를 선택한 후 **다음**&#x200B;을 클릭합니다.

   ![이미지](/help/screens-cloud/assets/onboarding/run-pipeline1.png)

1. **파이프라인 설정** 마법사에서 옵션을 선택합니다. **저장**&#x200B;을 클릭합니다.

   >[!NOTE]
   >파이프라인 설정 마법사의 옵션에 대한 자세한 내용은 [Cloud Manager에서 파이프라인 설정 구성](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/cicd-pipelines/configuring-production-pipelines.html)을 참조하십시오.

   ![이미지](/help/screens-cloud/assets/onboarding/run-pipeline2-a.png)

1. 설정 파이프라인이 완료되면 콜 투 액션 카드가 업데이트됩니다.

   >[!NOTE]
   >Cloud Manager의 배포 단계에 대한 자세한 내용은 [코드 배포](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/deploy-code.html)를 참조하세요.

   ![이미지](/help/screens-cloud/assets/onboarding/run-pipeline3.png)

1. **배포**&#x200B;를 클릭합니다.

1. 빌드 프로세스를 시작하려면 **빌드**&#x200B;를 클릭하십시오.

   ![이미지](/help/screens-cloud/assets/onboarding/run-pipeline4.png)

1. 빌드 프로세스가 완료되면 Cloud Manager **개요** 페이지에서 **환경** 카드의 작성자 링크를 볼 수 있습니다.

   ![이미지](/help/screens-cloud/assets/onboarding/run-pipeline5.png)

## 다음 단계 {#whats-next}

Cloud Manager에서 프로그램의 환경을 설정하는 방법에 대해 알아본 후에는 온보딩 프로세스의 다음 단계로 이동할 준비가 되었습니다. [Screens 서비스 공급자로 이동](/help/screens-cloud/configuring/navigating-to-screens-services-provider.md).
