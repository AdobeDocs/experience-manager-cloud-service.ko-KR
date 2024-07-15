---
title: Cloud Acceleration Manager의 준비 단계
description: 이 페이지에서는 Cloud Acceleration Manager의 준비 단계에 대한 개요를 제공합니다.
exl-id: 2583985b-0358-433c-9d31-38e2c60dc3dc
feature: Migration
role: Admin
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '1045'
ht-degree: 9%

---

# Cloud Acceleration Manager의 준비 단계 {#readiness-phase-cam}

CAM(Cloud Acceleration Manager)에서 프로젝트를 생성하면 이제 준비 단계에서 현재 AEM(Adobe Experience Manager) 구현에 대한 평가를 시작할 수 있습니다.

준비 단계는 다음과 같습니다.

* [모범 사례 분석](#best-practices-analysis)
* [계획 및 설정](#planning-setup)

준비 단계로 이동하려면 아래 단계를 따르십시오.

1. 프로젝트 카드를 클릭합니다.

   ![이미지](/help/journey-migration/cloud-acceleration-manager/assets/cam-landing1.png)

1. 프로젝트 랜딩 페이지에서 아래 그림과 같이 **준비** 섹션으로 이동합니다.

   ![이미지](/help/journey-migration/cloud-acceleration-manager/assets/readiness-1.png)

   >[!NOTE]
   >자세한 내용은 Cloud Acceleration Manager에서 프로젝트 만들기 및 관리 를 참조하십시오.

## 모범 사례 분석 카드 사용 {#best-practices-analysis}

>[!CONTEXTUALHELP]
>id="aemcloud_cam_bpa"
>title="모범 사례 분석 보고서"
>abstract="BPA 보고서를 CAM에 업로드하여 AEM as a Cloud Service로의 마이그레이션과 관련된 분석을 제공할 수 있습니다."
>additional-url="https://experienceleague.adobe.com/ko/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/best-practices-analyzer/using-best-practices-analyzer" text="모범 사례 분석기 사용"

1. **모범 사례 분석** 카드에서 **검토**&#x200B;를 클릭합니다.

   ![이미지](/help/journey-migration/cloud-acceleration-manager/assets/readiness-2.png)

1. BPA(모범 사례 분석기)를 다운로드합니다.

   >[!NOTE]
   >Adobe 비즈니스 크리티컬 인스턴스에 영향을 주지 않도록 작성자 환경에서 BPA를 실행하는 것이 좋습니다. 환경은 사용자 정의, 구성, 콘텐츠 및 사용자 애플리케이션 영역의 프로덕션 환경과 최대한 유사해야 합니다. 또는 프로덕션 작성 환경의 복제본에서 실행할 수 있습니다.

   1. [소프트웨어 배포](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html?fulltext=best*) 포털로 이동하여 모범 사례 분석기를 zip 파일로 다운로드합니다.

      >[!NOTE]
      >[모범 사례 분석기 사용](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/best-practices-analyzer/using-best-practices-analyzer.html#imp-considerations)을 검토하여 BPA를 실행하는 방법을 알아보십시오.

1. CAM에서 **업로드 키 가져오기**&#x200B;를 클릭하면 BPA 보고서를 자동으로 CAM에 바로 업로드하도록 시스템을 구성하는 데 사용되는 키를 가져올 수 있습니다.

   ![이미지](/help/journey-migration/cloud-acceleration-manager/assets/readiness-3b.png)

   >[!IMPORTANT]
   >보고서를 여전히 수동으로 업로드할 수 있지만 업로드 키를 사용하면 작업이 간소화됩니다. 브라우저의 시크릿 모드에 있는 경우 보고서를 수동으로 업로드할 수 없습니다.

1. 새 보고서가 업로드되면 CAM에서 모범 사례 분석 보고서를 볼 수 있습니다.

   ![이미지](/help/journey-migration/cloud-acceleration-manager/assets/cam-bpareport.png)

   >[!NOTE]
   >서로 다른 보고서를 여러 개 업로드하는 경우, 항상 세부 정보가 표시되는 보고서가 가장 최근 생성 날짜(업로드 날짜가 아님)인 보고서입니다.

1. CAM의 모범 사례 분석 대시보드를 검토하고 탐색합니다. 자세한 내용은 [모범 사례 분석 보고서 검토](#analysis-report)를 참조하세요.

   >[!NOTE]
   >새 보고서를 업로드하면 이전에 로드된 보고서보다 최신인 경우 모든 평가가 재설정됩니다.

### 인쇄 미리 보기 사용 {#print-preview-cam}

보고서의 인쇄 가능한 미리 보기를 위해 Cloud Acceleration Manager에서 인쇄 미리 보기 옵션을 선택하거나 쉽게 공유할 수 있도록 보고서를 PDF 형식으로 인쇄할 수 있습니다.

아래 단계를 따르십시오.

1. **인쇄 미리 보기** 작업을 클릭합니다.

   ![이미지](/help/journey-migration/best-practices-analyzer/assets/bpa-printpreview1b.png)

1. 인쇄 가능한 미리 보기에 보고서가 표시된 새 탭에서 **인쇄**&#x200B;를 클릭하여 보고서를 PDF 형식으로 인쇄합니다.

   >[!IMPORTANT]
   >
   >* 위의 기능에는 **PDF으로 저장** 옵션이 권장되며 지원됩니다.
   >* 브라우저의 인쇄 버튼을 사용하면 한 페이지만 인쇄됩니다.

   ![이미지](/help/journey-migration/best-practices-analyzer/assets/bpa-printpreview2.png)

### 추세선 보기 사용 {#trendline-view-cam}

프로젝트에 둘 이상의 개별 BPA(모범 사례 분석기) 보고서를 업로드할 때 **추세선 보기** 옵션을 선택하여 기록 BPA 보고서의 결과를 보고 비교할 수 있습니다.

트렌드 라인 옵션에서 보고서를 보려면 아래 단계를 따르십시오.

>[!NOTE]
>프로젝트에 둘 이상의 개별 BPA 보고서를 업로드하면 **..** 아이콘이 표시됩니다. 보고서는 호스트와 생성 시간이 동일한 경우 동일한 것으로(고유하지 않음) 간주됩니다.

1. 프로젝트로 이동하고 **준비** 단계의 **모범 사례 분석** 카드에서 **검토**&#x200B;를 클릭합니다.

   ![이미지](/help/journey-migration/cloud-acceleration-manager/assets/trendline-view1a.png)

1. 아래 그림과 같이 **보기** 드롭다운 목록에서 **추세선 보고서**&#x200B;를 클릭합니다.

   ![이미지](/help/journey-migration/cloud-acceleration-manager/assets/trendline-view1b.png)

1. **추세선 보고서**&#x200B;를 클릭하면 보고서의 추세선 보기가 열립니다.

   ![이미지](/help/journey-migration/cloud-acceleration-manager/assets/trendline-view3a.png)


   >[!NOTE]
   >추세선 보고서는 내역 BPA 보고서의 결과를 그래픽으로 표시합니다.
   >
   >다음의 트렌드를 표시하는 두 개의 그래프가 표시됩니다.
   > 
   >1. **보고서 결과 트렌드**
   >1. **사용자 지정 구성 요소 및 템플릿 트렌드**
   >
   >아래 그림과 같이 드롭다운을 통해 그래픽 보기를 추가하거나 변경할 수 있습니다.
   >![이미지](/help/journey-migration/cloud-acceleration-manager/assets/reports-bpa1.png)


### Best Practices Analysis 보고서 검토 {#analysis-report}

모범 사례 분석 보고서 페이지에서 사용할 수 있는 다음 카드를 살펴보십시오.

![이미지](/help/journey-migration/cloud-acceleration-manager/assets/cam-bpareport.png)

>[!NOTE]
> 각 카드를 사용하여 다음과 같은 작업을 수행할 수 있습니다.
>
>* 관련 탭을 엽니다.
>* 공유 또는 나중에 검색할 수 있도록 모든 보고서 탭(필터링 포함)을 책갈피로 지정
>* 세부 정보 아이콘을 사용하여 각 보고서 검색 결과의 세부 정보를 볼 수 있습니다

#### 보고서 속성 {#report-properties}

**보고서 속성** 카드는 보고서 날짜, 기간, 필터, 업로드 날짜 및 Adobe Experience Manager(AEM) 세부 정보 등의 보고서 속성에 대한 정보를 제공합니다.

![이미지](/help/journey-migration/cloud-acceleration-manager/assets/report-properties.png)

#### 보고서 개요 {#report-overview}

이 **보고서 개요** 카드는 아래 그림과 같이 AEM as a Cloud Service으로 이동할 준비를 평가할 때 적용되는 보고서 결과 및 심각도 수준을 제공합니다.

![이미지](/help/journey-migration/cloud-acceleration-manager/assets/report-overview.png)

이 보고서를 클릭하면 **보고서** 탭이 열립니다.

![이미지](/help/journey-migration/cloud-acceleration-manager/assets/report-overview2.png)

중요도, 하위 유형 또는 수를 기준으로 보고서를 필터링할 수 있습니다.

![이미지](/help/journey-migration/cloud-acceleration-manager/assets/report-overview3.png)

>[!NOTE]
>검색 결과 범주 및 중요도 수준에 대한 자세한 내용은 [모범 사례 분석기 보고서 해석](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/best-practices-analyzer/using-best-practices-analyzer.html)을 참조하십시오.

#### 모범 사례 평가 {#best-practices-assessment}

모범 사례 평가 옵션은 현재 AEM 인스턴스에 대한 평가를 제공하고 AEM 모범 사례를 채택하기 위한 다음 단계에 대한 지침을 제공합니다. 이 탭에서 다음 정보를 검토할 수 있습니다.

* AEM 인스턴스 개요
* 사용자 지정 구성 요소 및 템플릿
* 추가 결과
* 느린 쿼리
* 유지 관리 작업

#### 마이그레이션 복잡성 평가 {#migration-complexity-assessment}

마이그레이션 복잡성 평가 옵션은 기존 AEM 구현을 AEM as a Cloud Service으로 마이그레이션하는 데 따른 복잡성을 평가합니다.

이 탭에서 다음 정보를 검토할 수 있습니다.

* AEM 인스턴스 개요
* 평가
* 콘텐츠 마이그레이션 고려 사항

  ![이미지](/help/journey-migration/cloud-acceleration-manager/assets/migration-complexity-1.png)

## Planning 및 설정 카드 사용 {#planning-setup}

1. **계획 및 설정** 카드에서 **보기**&#x200B;를 클릭합니다. 이 카드는 AEM 마이그레이션을 계획하고 설정하는 데 도움이 되는 모든 관련 콘텐츠를 제공합니다.

   ![이미지](/help/journey-migration/cloud-acceleration-manager/assets/readiness-view.png)

1. 컨텐츠 캐러셀은 마이그레이션 여정의 이 단계에 대한 모든 관련 정보를 표시합니다.

   ![이미지](/help/journey-migration/cloud-acceleration-manager/assets/readiness-5-planning.png)

### 추세선 보기에서 모범 사례 분석 보고서 삭제 {#delete-trendline}

>[!IMPORTANT]
>프로젝트에 둘 이상의 보고서가 업로드된 경우에만 보고서를 삭제할 수 있습니다.

1. 프로젝트로 이동하고 **준비** 단계의 **모범 사례 분석** 카드에서 **검토**&#x200B;를 클릭합니다.

   ![이미지](/help/journey-migration/cloud-acceleration-manager/assets/trendline-view1a.png)

1. **..**&#x200B;을(를) 클릭합니다.

   ![이미지](/help/journey-migration/cloud-acceleration-manager/assets/trendline-view1.png)

1. 아래 그림과 같이 드롭다운 목록에서 **추세선 보기**&#x200B;를 클릭합니다.

   ![이미지](/help/journey-migration/cloud-acceleration-manager/assets/trendline-view1b.png)

1. **추세선 보고서** 화면에서 삭제 아이콘을 클릭합니다.

   ![이미지](/help/journey-migration/cloud-acceleration-manager/assets/trendline-view5a.png)

1. **삭제**&#x200B;를 클릭하여 삭제를 확인합니다.

   ![이미지](/help/journey-migration/cloud-acceleration-manager/assets/trendline-view6a.png)

## 다음 단계 {#whats-next}

Cloud Acceleration Manager에 로그인하는 방법과 프로젝트를 만드는 방법을 배우면 이제 [구현 단계](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-acceleration-manager/using-cam/cam-implementation-phase.html)의 다음 단계를 검토할 준비가 되었습니다.
