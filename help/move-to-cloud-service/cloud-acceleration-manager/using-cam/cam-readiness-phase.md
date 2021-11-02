---
title: Cloud Acceleration Manager의 준비 단계
description: 이 페이지에서는 Cloud Acceleration Manager의 준비 단계에 대한 개요를 제공합니다.
exl-id: 91a13cae-4934-42e8-9538-896fd72f5acb
source-git-commit: ba405db754fd6335c76180c7520ab9c08e259f6e
workflow-type: tm+mt
source-wordcount: '1057'
ht-degree: 5%

---

# Cloud Acceleration Manager의 준비 단계 {#readiness-phase-cam}

Cloud Acceleration Manager에서 프로젝트를 만들었으면 이제 준비 단계에서 현재 AEM 구현에 대한 평가를 시작할 수 있습니다.

준비 단계 에는 다음이 포함됩니다.

* [우수 사례 분석](#best-practices-analysis)
* [계획 및 설정](#planning-setup)

아래 절차에 따라 준비 단계로 이동합니다.

1. 프로젝트 카드를 클릭하여 프로젝트 랜딩 페이지를 엽니다.

   ![이미지](/help/move-to-cloud-service/cloud-acceleration-manager/assets/cam-landing1.png)

1. 로 이동합니다 **준비** 섹션을 참조하십시오.

   ![이미지](/help/move-to-cloud-service/cloud-acceleration-manager/assets/readiness-1.png)

   >[!NOTE]
   >자세한 내용은 Cloud Acceleration Manager에서 프로젝트 만들기 및 관리 를 참조하십시오.

## 우수 사례 분석 카드 사용 {#best-practices-analysis}

우수 사례 분석 카드를 사용하려면 아래 절차를 따르십시오.

1. 을(를) 클릭합니다. **검토** 단추 **우수 사례 분석** 카드.

   ![이미지](/help/move-to-cloud-service/cloud-acceleration-manager/assets/readiness-2.png)

1. 다음 단계에 따라 모범 사례 분석기 (BPA)를 다운로드합니다.

   >[!NOTE]
   >비즈니스 크리티컬 인스턴스에 영향을 주지 않도록 사용자 지정, 구성, 컨텐츠 및 사용자 애플리케이션 영역의 프로덕션 환경에 최대한 가까운 작성 환경에서 BPA를 실행하는 것이 좋습니다. 또는 프로덕션 작성 환경의 복제본에서 실행할 수 있습니다.

   1. 다음으로 이동 [소프트웨어 배포](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html) 포털 및 우수 사례 분석기를 zip 파일로 다운로드합니다.

      >[!NOTE]
      >검토 [우수 사례 분석기 사용](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/best-practices-analyzer/using-best-practices-analyzer.html?lang=en#imp-considerations) bpa 실행 방법을 알아봅니다.

   1. 보고서를 CSV 형식으로 내보냅니다

1. 클릭 **새 보고서 업로드** 를 눌러 CAM에서 BPA 보고서를 업로드합니다.

   ![이미지](/help/move-to-cloud-service/cloud-acceleration-manager/assets/readiness-3.png)

   >[!IMPORTANT]
   >브라우저의 Incognito 모드에 있는 경우에는 보고서를 업로드할 수 없습니다.

1. 새 보고서를 업로드하면 모범 사례 분석 보고서가 표시됩니다.

   ![이미지](/help/move-to-cloud-service/cloud-acceleration-manager/assets/cam-bpareport.png)

1. CAM에서 모범 사례 분석 대시보드를 검토하고 살펴봅니다. 아래 섹션을 참조하십시오 [우수 사례 분석 보고서 검토](#analysis-report) 자세한 내용

   >[!NOTE]
   >새 보고서를 업로드하면 모든 평가가 재설정됩니다.

### 인쇄 미리 보기 사용 {#print-preview-cam}

Cloud Acceleration Manager에서 인쇄 미리 보기 옵션을 선택하여 보고서의 인쇄 가능 미리 보기를 수행하거나 보고서를 PDF 형식으로 인쇄하여 쉽게 공유할 수 있습니다.

아래 단계를 따르십시오.

1. 클릭 **인쇄 미리 보기** 아이콘 을 채우는 방법을 설명합니다.

   ![이미지](/help/move-to-cloud-service/best-practices-analyzer/assets/bpa-printpreview1.png)

1. 클릭 **인쇄 미리 보기** 인쇄 가능한 미리 보기에 표시된 보고서가 있는 새 탭을 엽니다. 클릭 **인쇄** 보고서를 PDF 형식으로 인쇄하려면

   >[!IMPORTANT]
   >* 옵션 **다른 이름으로 저장 PDF** 는 위의 기능에 대해 권장되고 지원됩니다.
   >* 브라우저의 인쇄 단추를 사용하면 한 페이지만 인쇄됩니다.


   ![이미지](/help/move-to-cloud-service/best-practices-analyzer/assets/bpa-printpreview2.png)

### 트렌드 라인 보기 사용 {#trendline-view-cam}

프로젝트에서 두 개 이상의 BPA(Best Practices Analyzer) 보고서를 업로드할 때 **트렌드 라인 보기** 기록 BPA 보고서의 결과를 보고 비교하는 옵션입니다.

트렌드 라인 옵션에서 보고서를 보려면 아래 절차를 따르십시오.

>[!NOTE]
>프로젝트에서 두 개 이상의 BPA 보고서를 업로드하면 **...** 아이콘.

1. 프로젝트로 이동하고 을(를) 클릭합니다 **검토** 에서 **우수 사례 분석** 의 카드 **준비** 단계.

   ![이미지](/help/move-to-cloud-service/cloud-acceleration-manager/assets/trendline-view1a.png)

1. 을(를) 클릭합니다. **...** 아이콘을 클릭하여 드롭다운을 표시합니다.

   ![이미지](/help/move-to-cloud-service/cloud-acceleration-manager/assets/trendline-view1.png)

   >[!IMPORTANT]
   >표시된 보고서는 항상 최신 보고서 날짜가 있는 보고서입니다.

1. 클릭 **트렌드 라인 보기**&#x200B;아래 그림과 같이,

   ![이미지](/help/move-to-cloud-service/cloud-acceleration-manager/assets/trendline-view2.png)

1. 클릭 **트렌드 라인 보기** 아래 그림과 같이 보고서의 트렌드 라인 보기를 엽니다.

   ![이미지](/help/move-to-cloud-service/cloud-acceleration-manager/assets/trendline-view3.png)

   >[!NOTE]
   >트렌드 라인 보고서는 내역 BPA 보고서의 결과를 그래픽 표현으로 표시합니다.
   >
   >다음 두 개의 그래프에서 트렌드를 확인할 수 있습니다.
   >1. **보고서 결과 트렌드**
   >1. **사용자 지정 구성 요소 및 템플릿 트렌드**

   >
   >아래 그림과 같이 드롭다운을 통해 그래픽 보기를 추가하거나 변경할 수 있습니다.
   >![이미지](/help/move-to-cloud-service/cloud-acceleration-manager/assets/trendline-view4.png)


### 우수 사례 분석 보고서 검토 {#analysis-report}

우수 사례 분석 보고서 페이지에서 사용할 수 있는 다음 카드를 살펴보십시오.

![이미지](/help/move-to-cloud-service/cloud-acceleration-manager/assets/cam-bpareport.png)

>[!NOTE]
> 각 카드를 사용할 경우 다음을 수행할 수 있습니다.
>* 각 카드를 클릭하여 관련 탭을 엽니다.
>* 공유하거나 나중에 검색할 수 있도록 모든 보고서 탭(필터링 포함)을 책갈피로 지정합니다
>* 세부 정보 아이콘을 사용하여 각 보고서 검색 결과의 세부 사항을 볼 수 있습니다


#### 보고서 속성 {#report-properties}

다음 **보고서 속성** 카드는 보고서 날짜, 기간, 필터, 업로드 날짜 및 Adobe Experience Manager(AEM) 세부 사항 등의 보고서 속성에 대한 정보를 제공합니다.

![이미지](/help/move-to-cloud-service/cloud-acceleration-manager/assets/report-properties.png)

#### 보고서 개요 {#report-overview}

이 **보고서 개요** 카드는 아래 그림과 같이 AEM as a Cloud Service으로 이동할 준비를 평가할 때 적용되는 보고서 결과 및 심각도 수준을 제공합니다.

![이미지](/help/move-to-cloud-service/cloud-acceleration-manager/assets/report-overview.png)

이 보고서를 클릭하면 **보고서** 탭.

![이미지](/help/move-to-cloud-service/cloud-acceleration-manager/assets/report-overview2.png)

중요도, 하위 유형 또는 개수를 기반으로 보고서를 필터링할 수 있습니다.

![이미지](/help/move-to-cloud-service/cloud-acceleration-manager/assets/report-overview3.png)

>[!NOTE]
>을(를) 참조하십시오. [모범 사례 분석기 보고서 해석](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/best-practices-analyzer/using-best-practices-analyzer.html?lang=en) 검색 결과 카테고리 및 중요도 수준에 대해 알아봅니다.

#### 모범 사례 평가 {#best-practices-assessment}

모범 사례 평가 선택 사항은 현재 AEM 인스턴스에 대한 평가를 제공하며 AEM 모범 사례를 채택할 다음 단계에 대한 지침을 제공합니다. 이 탭에서 다음 정보를 검토할 수 있습니다.

* AEM 인스턴스 개요
* 사용자 지정 구성 요소 및 템플릿
* 추가 결과
* 느린 쿼리
* 유지 관리 작업

#### 마이그레이션 복잡성 평가 {#migration-complexity-assessment}

마이그레이션 복잡성 평가 옵션은 기존 AEM 구현을 AEM as a Cloud Service으로 마이그레이션하는 데 따르는 복잡성에 대한 평가를 제공합니다.

이 탭에서 다음 정보를 검토할 수 있습니다.

* AEM 인스턴스 개요
* 평가
* 콘텐츠 마이그레이션 고려 사항

   ![이미지](/help/move-to-cloud-service/cloud-acceleration-manager/assets/migration-complexity-1.png)

## 계획 및 설정 카드 사용 {#planning-setup}

이 섹션을 따라 계획 및 설정 활동 카드를 탐색합니다.

1. 을(를) 클릭합니다. **보기** 단추 **계획 및 설정** 카드. 이 카드는 AEM 마이그레이션을 계획 및 설정하는 데 도움이 되는 모든 관련 컨텐츠를 제공합니다.

   ![이미지](/help/move-to-cloud-service/cloud-acceleration-manager/assets/readiness-view.png)

1. 컨텐츠 회전판에 마이그레이션 여정의 이 단계에 대한 모든 관련 정보가 표시됩니다.

   ![이미지](/help/move-to-cloud-service/cloud-acceleration-manager/assets/readiness-5-planning.png)

### 우수 사례 분석 보고서 삭제 {#delete-trendline}

트렌드 라인 보기에서 보고서를 삭제하려면 아래 절차를 따르십시오.

>[!IMPORTANT]
>프로젝트에 두 개 이상의 보고서가 업로드된 경우에만 보고서를 삭제할 수 있습니다.

1. 프로젝트로 이동하고 을(를) 클릭합니다 **검토** 에서 **우수 사례 분석** 의 카드 **준비** 단계.

   ![이미지](/help/move-to-cloud-service/cloud-acceleration-manager/assets/trendline-view1a.png)

1. 을(를) 클릭합니다. **...** 아이콘을 클릭하여 드롭다운을 표시합니다.

   ![이미지](/help/move-to-cloud-service/cloud-acceleration-manager/assets/trendline-view1.png)

1. 클릭 **트렌드 라인 보기**&#x200B;아래 그림과 같이,

   ![이미지](/help/move-to-cloud-service/cloud-acceleration-manager/assets/trendline-view2.png)

1. 에서 삭제 아이콘을 클릭합니다 **트렌드 라인 보고서** 화면.

   ![이미지](/help/move-to-cloud-service/cloud-acceleration-manager/assets/trendline-view5.png)

1. 클릭 **삭제** 를 클릭하여 삭제를 확인합니다.

   ![이미지](/help/move-to-cloud-service/cloud-acceleration-manager/assets/trendline-view6.png)

## 다음은 무엇입니까? {#whats-next}

Cloud Acceleration Manager에 로그인하는 방법과 프로젝트를 만드는 방법을 학습하면 이제 의 다음 단계를 검토할 준비가 되었습니다 [구현 단계](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-acceleration-manager/using-cam/cam-implementation-phase.html?lang=en).
