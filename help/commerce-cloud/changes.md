---
title: CIF(Commerce Integration Framework) 추가 기능의 주요 변경 사항
description: 이전 CIF 버전과 비교한 Commerce Integration Framework(CIF)의 주요 변경 사항.
exl-id: 5a526960-96a1-421e-9fb0-0825e7df8f32
source-git-commit: 1994b90e3876f03efa571a9ce65b9fb8b3c90ec4
workflow-type: tm+mt
source-wordcount: '452'
ht-degree: 3%

---

# CIF(Commerce Integration Framework) 추가 기능의 주요 변경 사항{#notable-changes}

Adobe Experience Manager as a Cloud Service은 AEM 프로젝트를 관리할 수 있는 많은 새로운 기능과 가능성을 제공합니다. 이러한 기능에 대해 자세히 알아보려면 다음 링크를 따르십시오. [Experience Manager as a Cloud Service 변경 사항](/help/release-notes/aem-cloud-changes.md).

이 문서에서는 CIF(Commerce Integration Framework) 추가 기능과 CIF Classic(Quickstart) 및 CIF 오픈 소스로 알려진 이전 CIF 버전 간의 중요한 차이점을 조명합니다.

## 설치 및 업데이트

AEM CIF 추가 기능은 Cloud Manager를 통해 설치됩니다. 설치에는 크레딧 없이 CIF를 설치할 수 있는 샌드박스를 제외하고 CIF 크레딧이 필요합니다. 점수는 AEM 계약에서 CIF 추가 기능의 프로비저닝을 통해 자동으로 수신됩니다.

추가 기능은 정기 AEM as a Cloud Service 업데이트의 일부로 자동 업데이트됩니다.

**이전 CIF 버전**

* CIF Classic: 설치할 필요가 없습니다. CIF는 빠른 시작에 속했습니다. CIF 업데이트는 일반 AEM 또는 서비스 팩 업데이트의 일부였습니다
* AEM 온-프레미스용 CIF 오픈 소스: GitHub를 통해 설치. 업데이트는 수동 업데이트/유지 관리 작업의 일부였습니다.
* AEM Adobe Managed Services용 CIF 오픈 소스: Adobe 계정 팀을 통해 설치. 업데이트는 수동 업데이트/유지 관리 작업의 일부였습니다.

## 끝점 구성

끝점은 Cloud Manager UI 또는 해당 CLI를 통해 구성 및 업데이트됩니다.

**이전 CIF 버전**

* CIF Classic: AEM에서 OSGi 구성을 통해
* CIF 오픈 소스: CIF 구성 브라우저를 통해

## CIF Venia 프로젝트 배포

사용 가능한 프로젝트 [Cloud Manager Git 저장소](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/managing-code/integrating-with-git.html) 및 배포 를 통해 완료 [Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/deploying/overview.html)

**이전 CIF 버전**

* CIF Classic: AEM 패키지 설치
* CIF 오픈 소스: [Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/content/introduction.html)

## 제품 카탈로그 데이터

제품 카탈로그 데이터는 필요한 GraphQL API를 지원하는 외부 엔드포인트에 대한 실시간 호출을 통해 온디맨드로 요청됩니다. 이러한 API는 지정된 날짜에 라이브 또는 스테이징된 데이터에 대한 액세스를 지원합니다. 복제 불필요.

**이전 CIF 버전**

* CIF Classic: 라이브 및 스테이징된 제품 데이터를 가져와 전체 또는 델타 제품 가져오기를 통해 AEM 작성자의 JCR에서 지속됩니다. 라이브 제품 데이터가 AEM 게시로 복제됩니다.

## AEM 렌더링을 통한 제품 카탈로그 경험

AEM은 제품 및 범주에 할당된 AEM 카탈로그 템플릿을 사용하여 제품 카탈로그 경험을 즉시 렌더링합니다. 복제 불필요.

**이전 CIF 버전**

* CIF Classic: AEM 작성자는 카탈로그 블루프린트 도구를 사용하여 모든 카테고리/제품에 대한 AEM 페이지를 만듭니다. 이러한 페이지는 AEM 게시로 복제됩니다.

>[!NOTE]
>
>AEM Managed Service 또는 AEM On-Premise와 함께 CIF를 사용하는 방법에 대한 추가 설명서는 를 참조하십시오. [Commerce 통합 프레임워크](https://www.adobe.io/apis/experiencecloud/commerce-integration-framework/getting-started.html)
