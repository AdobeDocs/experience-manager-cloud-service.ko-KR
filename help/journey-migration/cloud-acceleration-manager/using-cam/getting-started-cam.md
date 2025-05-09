---
title: Cloud Acceleration Manager 시작하기
description: 이 페이지에서는 Cloud Acceleration Manager을 사용하고 시작하는 방법에 대한 개요를 제공합니다.
exl-id: e2fad21c-3de6-4186-97c6-ebc84780b2e8
feature: Migration
role: Admin
source-git-commit: d840e0beb8036ed8e543ac85850290e778371bbe
workflow-type: tm+mt
source-wordcount: '555'
ht-degree: 20%

---

# Cloud Acceleration Manager 시작하기 {#get-started-cam}

Cloud Acceleration Manager는 계획 수립에서 Cloud Service로의 이행까지의 전환 과정 전반에 걸쳐 IT 팀을 안내하도록 설계된 클라우드 기반의 애플리케이션입니다. Adobe가 권장하는 모범 사례, 팁, 문서 및 도구를 사용하여 AEM as a Cloud Service로 전환하는 과정의 모든 단계에서 성공적인 마이그레이션을 위해 팀을 구성하십시오.

## 목표 {#objective}

이 문서는 CAM(Cloud Acceleration Manager)을 시작하는 방법을 이해하는 데 도움이 됩니다. 문서를 읽고 나면 다음과 같은 작업을 수행할 수 있습니다.

* cam에 로그인하는 방법 이해
* cam의 UI에서 프로젝트를 만듭니다.

## Cloud Acceleration Manager 사용 {#using-cam}

CAM(Cloud Acceleration Manager)은 마이그레이션을 위한 원스톱 환경을 제공합니다. AEM as a Cloud Service에서 성공적인 Go-Live를 보장하기 위해 초기 평가를 제공하고 올바른 도구, 설명서 및 모범 사례를 안내함으로써 가이드 여정 형태로 제공됩니다.

### Cloud Acceleration Manager으로 이동 {#navigating}

CAM(Cloud Acceleration Manager)으로 이동하려면 아래 단계를 따르십시오.

1. [Adobe Experience Cloud](https://experience.adobe.com)에 로그온합니다.

1. **Experience Manager** 카드를 클릭합니다.

1. 랜딩 페이지를 열려면 **Cloud Acceleration Manager** 카드에서 **시작**&#x200B;을 클릭하세요.

   ![이미지](/help/journey-migration/cloud-acceleration-manager/assets/cam-1.png)

### Cloud Acceleration Manager에서 프로젝트 만들기 및 관리 {#create-project}

>[!CONTEXTUALHELP]
>id="aemcloud_cam_gettingstarted"
>title="Cloud Acceleration Manager 시작하기"
>abstract="프로젝트를 만들고 AEM as a Cloud Service로의 여정을 시작합니다."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-acceleration-manager/introduction-cam/benefits-cam.html?lang=ko" text="Cloud Acceleration Manager 사용 시 장점"

CAM(Cloud Acceleration Manager)의 랜딩 페이지를 사용하여 여러 프로젝트를 만들고 편집할 수 있습니다.

아래 단계에 따라 프로젝트를 만듭니다.

1. 랜딩 페이지에서 **프로젝트 만들기**&#x200B;를 클릭합니다.

   ![이미지](/help/journey-migration/cloud-acceleration-manager/assets/cam-2.png)

   >[!NOTE]
   >CAM을 처음 사용하는 사용자에게는 프로젝트를 생성하는 대화 상자가 표시됩니다. 과거에 CAM을 사용한 사용자에게는 기본 프로젝트나 이전에 만든 프로젝트가 표시됩니다.

1. 프로젝트의 **이름** 및 **설명**&#x200B;을 입력하고 **만들기**&#x200B;를 클릭합니다.

   ![이미지](/help/journey-migration/cloud-acceleration-manager/assets/cam-3.png)

1. 이제 프로젝트가 만들어지고 **Cloud Acceleration Manager** 랜딩 페이지에 표시됩니다.

   ![이미지](/help/journey-migration/cloud-acceleration-manager/assets/cam-landing.png)

1. 프로젝트를 입력할 수 있도록 프로젝트 카드를 클릭합니다. 프로젝트 랜딩 페이지로 이동합니다.

   ![이미지](/help/journey-migration/cloud-acceleration-manager/assets/cam-5.png)

## 프로젝트 관리 {#manage-project}

프로젝트 이름, 설명, 썸네일 이미지를 편집하거나 프로젝트를 삭제할 수 있습니다.

### 프로젝트 편집 {#edit-project}

프로젝트를 편집하려면 아래 단계를 따르십시오.

1. 아래 그림과 같이 프로젝트를 선택하고 프로젝트 위로 마우스를 가져간 다음 연필 아이콘을 클릭하여 프로젝트 편집을 엽니다.

   ![이미지](/help/journey-migration/cloud-acceleration-manager/assets/cam-4.png)

1. **프로젝트 편집** 대화 상자에서 프로젝트 이름, 설명을 편집하고 새 이미지를 업로드하거나 기존 이미지를 편집할 수도 있습니다.

   ![이미지](/help/journey-migration/cloud-acceleration-manager/assets/cam-edit.png)

1. 변경 내용을 커밋하려면 **업데이트**&#x200B;를 클릭하십시오.

### 프로젝트 삭제 {#delete-project}

프로젝트를 삭제하려면 아래 단계를 따르십시오.

1. 아래 그림과 같이 프로젝트를 선택하고 프로젝트 위로 마우스를 가져간 다음 버킷 아이콘을 클릭하여 프로젝트를 삭제합니다.

   ![이미지](/help/journey-migration/cloud-acceleration-manager/assets/cam-4.png)

1. **삭제**&#x200B;를 클릭하여 단계를 확인합니다.

   >[!NOTE]
   >마이그레이션 비활성 기간 1년 후 프로젝트가 자동으로 만료되고 삭제됩니다. 프로젝트 이름 또는 설명을 편집하거나, BPA 보고서를 업로드하거나, 마이그레이션 세트를 만들거나 편집하거나, 추출을 실행하거나, 수집을 실행하여 프로젝트가 활성 상태로 유지됩니다.


## 다음 단계 {#whats-next}

Cloud Acceleration Manager에 로그인하는 방법과 프로젝트를 만드는 방법을 학습하면 [준비 단계](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-acceleration-manager/using-cam/cam-readiness-phase.html?lang=ko)의 다음 단계를 검토할 수 있습니다.
