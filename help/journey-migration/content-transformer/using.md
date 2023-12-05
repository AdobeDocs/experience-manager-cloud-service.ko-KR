---
title: 컨텐츠 변환기 사용
description: AEM으로 as a Cloud Service으로 마이그레이션할 것을 대비하여 콘텐츠 구조를 변형하는 방법에 대해 알아봅니다.
exl-id: 40516ff7-5686-42e6-bdd1-c9c6de432b09
source-git-commit: 2d4ffd5518d671a55e45a1ab6f1fc41ac021fd80
workflow-type: tm+mt
source-wordcount: '630'
ht-degree: 1%

---

# 컨텐츠 변환기 사용 {#using-ct}

## 콘텐츠 변환기 사용에 대한 중요한 고려 사항 {#imp-considerations-ct}

콘텐츠 변환기(CT) 사용에 대한 중요한 고려 사항을 이해하려면 아래 섹션을 따르십시오.

* 콘텐츠 변환기를 사용하려면 먼저 Adobe Experience Manager(AEM) 환경에서 모범 사례 분석기를 실행해야 합니다.
* 프로덕션 환경에서 콘텐츠 변환기를 실행할 수 있지만 프로덕션 환경의 복제본에서 콘텐츠 변환기를 실행하는 것이 좋습니다. 더 중요한 것은 BPA와 CT가 동일한 환경에서 실행되는지 확인해야 한다는 것입니다.
* 콘텐츠 변환기를 실행하려는 환경에서 관리자여야 합니다.
* 소스 컨텐츠( 이동/제거/이름 바꾸기 )를 변경할 수 있는 모든 작업은 기본적으로 아래에 소스 경로의 백업 패키지를 만듭니다. `/etc/packages/content-transformation` 변환 전. 각 작업 대화 상자에는 백업 패키지 생성을 비활성화/활성화하는 옵션이 있지만, 항상 패키지 생성 활성화를 선택하는 것이 좋습니다.
* 콘텐츠 변환기의 각 페이지는 최대 50개의 검색 결과를 나열하도록 구성되므로 한 번에 최대 50개의 검색 결과를 변환할 수 있습니다. 이 작업은 UI에 적시성 응답을 제공하기 위해 수행됩니다.

## 사용 가능 {#availability-ct}

콘텐츠 변환기는 와 함께 번들로 제공됩니다. [컨텐츠 전송 도구](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/getting-started-content-transfer-tool.md) 소프트웨어 배포 포털에서 zip 파일로 다운로드할 수 있습니다. 패키지 관리자를 통해 소스 AEM 인스턴스에 패키지를 설치할 수 있습니다.

>[!NOTE]
>콘텐츠 변환기는 콘텐츠 전송 도구 v2.0.20 이상에서 사용할 수 있습니다.

## 콘텐츠 변환기 열기 {#opening-ct}

1. 소스 AEM 인스턴스에 관리자로 로그인하고 시작 페이지 https://host:port/aem/start.html으로 이동합니다.
1. 도구 > 작업 > 컨텐츠 마이그레이션으로 이동합니다.

   ![이미지](/help/journey-migration/content-transformer/assets/ct-1.png)

   >[!NOTE]
   > 이전에 BPA 보고서를 실행한 적이 있는지 확인하고 URL http://host:port/apps/best-practices-analyzer/content/BestPracticesReport.html을 사용하여 확인합니다.

1. 제목이 있는 카드 클릭 **BPA 보고서에 대한 컨텐츠 변환기**

   ![이미지](/help/journey-migration/content-transformer/assets/ct-2.png)

   다음은 BPA 보고서 만들기에 성공했으며 콘텐츠 관련 문제가 발견된 경우 콘텐츠 변환기 개요 페이지가 어떻게 표시되는지 보여 주는 예입니다.

   BPA 보고서의 만료 시간은 측면 레일에 표시됩니다. 콘텐츠 관련 결과가 누락되지 않도록 최신 BPA 보고서로 콘텐츠 변환기를 실행하는 것이 좋습니다.

   ![이미지](/help/journey-migration/content-transformer/assets/ct-3.png)

1. 다음을 기반으로 문제를 필터링할 수 있습니다. `Pattern Code`, `Subtype`, `Importance`, 및 `Source`.

   ![이미지](/help/journey-migration/content-transformer/assets/ct-4.png)

1. 모든 문제 또는 특정 문제를 선택하고 이를 해결하기 위해 이동하거나 제거하거나 이름을 바꿀 수 있습니다. 을 사용하여 사용자 정의 경로를 추가할 수도 있습니다. **경로 추가** 오른쪽 상단의 버튼입니다.

   >[!NOTE]
   > 이동 작업을 사용할 때는 모든 경로를 하나의 폴더(예: 아래)로만 이동하는 것이 좋습니다. `/etc/packages/content-transformation/paths`) 따라서 백업 패키지를 설치하여 인스턴스를 원래 상태로 되돌리면 폴더 (`/etc/packages/content-transformation/paths`)은 저장소 크기를 줄이기 위해 제거 작업을 사용하여 삭제할 수 있습니다.

   ![이미지](/help/journey-migration/content-transformer/assets/ct-5.png)
   ![이미지](/help/journey-migration/content-transformer/assets/ct-6.png)

   >[!NOTE]
   > 소스 콘텐츠를 변경할 수 있는 모든 작업(`move`/`remove`/`rename`)는 기본적으로 아래에 소스 경로의 백업 패키지를 만듭니다. `/etc/packages/content-transformation` 변환 전. 각 작업 대화 상자에는 백업 패키지 생성을 비활성화/활성화하는 옵션이 있지만, 항상 패키지 생성 활성화를 선택하는 것이 좋습니다.

1. 경로 이동 작업을 위해 만든 백업 패키지의 예는 아래에 나와 있습니다. 설치 를 클릭하여 소스 경로를 다시 가져옵니다. 소스 경로가 원래 위치로 복구될 뿐, 변환 중에 이동된 경로는 삭제되지 않습니다. 이동된 위치에서 경로를 삭제하려면 **경로 추가** 위치를 추가하는 버튼(예: `/etc/packages/content-transformation/paths`), 위치를 선택하고 **제거**.

   >[!CAUTION]
   > 삭제하지 않음 `/etc/packages/content-transformation` 백업 패키지가 있는 위치입니다. 이러한 패키지가 더 이상 필요하지 않은 경우에만 이 위치를 삭제하여 저장소 크기를 줄일 수 있습니다.

   ![이미지](/help/journey-migration/content-transformer/assets/ct-7.png)
   ![이미지](/help/journey-migration/content-transformer/assets/ct-8.png)
