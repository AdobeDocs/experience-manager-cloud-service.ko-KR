---
title: Cloud Acceleration Manager의 준비 단계
description: 이 페이지에서는 Cloud Acceleration Manager의 준비 단계에 대한 개요를 제공합니다.
hide: true
hidefromtoc: true
index: false
source-git-commit: b5b6a4a84c57805770ec1c72741c2d56d4711309
workflow-type: tm+mt
source-wordcount: '594'
ht-degree: 4%

---


# Cloud Acceleration Manager의 준비 단계 {#readiness-phase-cam}

Cloud Acceleration Manager에서 프로젝트를 만들었으면 이제 준비 단계에서 사용 가능한 도구 실행을 시작할 수 있습니다.

준비 단계 에는 다음이 포함됩니다.

* [우수 사례 분석](#best-practices-analysis)
* [계획 및 설정](#planning-setup)

아래 절차에 따라 준비 단계로 이동합니다.

1. 프로젝트 카드를 클릭하여 프로젝트 랜딩 페이지를 엽니다.

   ![이미지](/help/move-to-cloud-service/cloud-acceleration-manager/assets/cam-landing1.png)

1. 아래 그림과 같이 **준비** 섹션으로 이동합니다.

   ![이미지](/help/move-to-cloud-service/cloud-acceleration-manager/assets/readiness-1.png)

   >[!NOTE]
   >자세한 내용은 [Cloud Acceleration Manager에서 프로젝트 만들기 및 관리](/help/move-to-cloud-service/cloud-acceleration-manager/using-cam/getting-started-cam.md) 를 참조하십시오.

## 우수 사례 분석 카드 사용 {#best-practices-analysis}

우수 사례 분석 카드를 사용하려면 아래 절차를 따르십시오.

1. **우수 사례 분석** 카드에서 **검토** 단추를 클릭합니다.

   ![이미지](/help/move-to-cloud-service/cloud-acceleration-manager/assets/readiness-2.png)

1. 다음 단계에 따라 BPA(Best Practices Analyzer)를 다운로드하고 AEM 시스템의 복제본에서 실행합니다.

   1. [소프트웨어 배포](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html) 포털로 이동하여 우수 사례 분석기를 zip 파일로 다운로드합니다.

      >[!NOTE]
      >[우수 사례 분석기 사용](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/best-practices-analyzer/using-best-practices-analyzer.html?lang=en#imp-considerations)을 검토하여 BPA를 실행하는 방법을 알아보십시오.

   1. 보고서를 CSV 형식으로 내보냅니다

1. **새 보고서 업로드**&#x200B;를 클릭하여 CAM에서 BPA 보고서를 업로드합니다.

   ![이미지](/help/move-to-cloud-service/cloud-acceleration-manager/assets/readiness-3.png)

1. 새 보고서를 업로드하면 모범 사례 분석 보고서가 표시됩니다.

   ![이미지](/help/move-to-cloud-service/cloud-acceleration-manager/assets/cam-bpareport.png)

1. CAM에서 모범 사례 분석 대시보드를 검토하고 살펴봅니다. 자세한 내용은 [우수 사례 분석 보고서 검토](#analysis-report) 섹션을 참조하십시오.

   >[!NOTE]
   >새 보고서를 업로드하면 모든 평가가 재설정됩니다.

### 우수 사례 분석 보고서 검토 {#analysis-report}

우수 사례 분석 보고서 페이지에서 사용할 수 있는 다음 카드를 살펴보십시오.

![이미지](/help/move-to-cloud-service/cloud-acceleration-manager/assets/cam-bpareport.png)

>[!NOTE]
> 각 카드를 사용할 경우 다음을 수행할 수 있습니다.
>* 각 카드를 클릭하여 관련 탭을 엽니다.
>* 공유하거나 나중에 검색할 수 있도록 모든 보고서 탭(필터링 포함)을 책갈피로 지정합니다
>* 세부 정보 아이콘을 사용하여 각 보고서 검색 결과의 세부 사항을 볼 수 있습니다


#### 보고서 속성 {#report-properties}

**보고서 속성** 카드는 보고서 날짜, 기간, 필터, 업로드 날짜 및 Adobe Experience Manager(AEM) 세부 사항과 같은 보고서 속성에 대한 정보를 제공합니다.

![이미지](/help/move-to-cloud-service/cloud-acceleration-manager/assets/report-properties.png)

#### 보고서 개요 {#report-overview}

이 **보고서 개요** 카드는 아래 그림과 같이 보고서 결과를 제공합니다.

![이미지](/help/move-to-cloud-service/cloud-acceleration-manager/assets/report-overview.png)

이 보고서를 클릭하면 **보고서** 탭이 열립니다.

![이미지](/help/move-to-cloud-service/cloud-acceleration-manager/assets/report-overview2.png)

중요도, 하위 유형 또는 개수를 기반으로 보고서를 필터링할 수 있습니다.

![이미지](/help/move-to-cloud-service/cloud-acceleration-manager/assets/report-overview3.png)

>[!NOTE]
>검색 결과 카테고리 및 중요도 수준에 대해 알려면 [우수 사례 분석기 보고서 해석](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/best-practices-analyzer/using-best-practices-analyzer.html?lang=en)을 참조하십시오.

#### 모범 사례 평가 {#best-practices-assessment}

모범 사례 평가 선택 사항은 현재 AEM 인스턴스에 대한 평가를 제공하며 AEM 모범 사례를 채택할 다음 단계에 대한 지침을 제공합니다. 이 탭에서 다음 정보를 검토할 수 있습니다.

* AEM 인스턴스 개요
* 사용자 지정 구성 요소 및 템플릿
* 추가 결과
* 느린 쿼리
* 유지 관리 작업

#### 마이그레이션 복잡성 평가 {#migration-complexity-assessment}

마이그레이션 복잡성 평가 옵션은 기존 AEM 구현을 Cloud Service으로 AEM으로 마이그레이션하는 데 따르는 복잡성에 대한 평가를 제공합니다. 이 탭에서 다음 정보를 검토할 수 있습니다.

* AEM 인스턴스 개요
* 평가
* 콘텐츠 마이그레이션 고려 사항

   ![이미지](/help/move-to-cloud-service/cloud-acceleration-manager/assets/migration-complexity-1.png)

## 계획 및 설정 카드 사용 {#planning-setup}

이 섹션을 따라 계획 및 설정 활동 카드를 탐색합니다.

1. AEM 마이그레이션을 계획 및 설정하는 데 도움이 되는 모든 관련 콘텐츠를 제공하는 **계획 및 설정** 카드에서 **보기** 단추를 클릭합니다.

   ![이미지](/help/move-to-cloud-service/cloud-acceleration-manager/assets/readiness-4.png)

1. 마이그레이션 여정의 이 단계에 대한 관련 정보가 포함된 컨텐츠 회전판이 표시됩니다.

   ![이미지](/help/move-to-cloud-service/cloud-acceleration-manager/assets/readiness-5-planning.png)

## 다음은 무엇입니까? {#whats-next}

Cloud Acceleration Manager에 로그인하는 방법과 프로젝트를 만드는 방법을 학습하면 이제 구현 단계를 사용하면서 다음 단계를 검토할 수 있습니다.
