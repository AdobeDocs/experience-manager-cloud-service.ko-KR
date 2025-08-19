---
title: Commerce integration framework(CIF) 추가 기능의 주요 변경 사항
description: 이전 CIF 버전과 비교한 Commerce integration framework(CIF)의 주요 변경 사항.
exl-id: 5a526960-96a1-421e-9fb0-0825e7df8f32
feature: Commerce Integration Framework
role: Admin
source-git-commit: 856442039fcd25ec675a6258d182f7a35f590c3c
workflow-type: tm+mt
source-wordcount: '425'
ht-degree: 0%

---


# Commerce integration framework(CIF) 추가 기능의 주요 변경 사항 {#notable-changes}

Adobe Experience Manager as a Cloud Service은 AEM 프로젝트를 관리할 수 있는 많은 새로운 기능과 가능성을 제공합니다. 이러한 기능에 대해 자세히 알아보려면 [Experience Manager as a Cloud Service 변경 사항](/help/release-notes/aem-cloud-changes.md)에 대한 링크를 따라가십시오.

이 문서에서는 Commerce integration framework(CIF) 추가 기능과 이전 CIF 버전(CIF Classic(Quickstart) 및 CIF Open-source로 알려짐) 간의 중요한 차이점을 조명합니다.

## 설치 및 업데이트

AEM CIF 추가 기능은 Cloud Manager을 통해 설치됩니다. 설치하려면 CIF 크레딧이 필요합니다. 단, 크레딧 없이 CIF을 설치할 수 있는 샌드박스는 예외입니다. 크레딧은 AEM 계약에서 CIF 추가 기능 프로비저닝을 통해 자동으로 수신됩니다.

추가 기능은 정기적인 AEM as a Cloud Service 업데이트의 일부로 자동 업데이트됩니다.

### 이전 CIF 버전 {#previous-versions-installation}

* CIF Classic: 설치할 필요가 없습니다. CIF은 빠른 시작에 속했습니다. CIF 업데이트는 일반 AEM 또는 서비스 팩 업데이트의 일부였습니다
* AEM 온-프레미스용 CIF 오픈 소스: GitHub를 통해 설치. 업데이트는 수동 업데이트/유지 관리 작업의 일부였습니다.
* AEM Adobe Managed Services용 CIF 오픈 소스: Adobe 계정 팀을 통해 설치. 업데이트는 수동 업데이트/유지 관리 작업의 일부였습니다.

## 끝점 구성 {#endpoint-configuration}

끝점은 Cloud Manager UI 또는 해당 CLI를 통해 구성 및 업데이트됩니다.

### 이전 CIF 버전 {#previous-versions-endpoint}

* CIF Classic: AEM에서 OSGi 구성을 통해
* CIF 오픈 소스: CIF 구성 브라우저 사용

## CIF Venia 프로젝트 배포 {#venia-project}

프로젝트는 [Cloud Manager Git 저장소](/help/implementing/cloud-manager/managing-code/integrating-with-git.md)에서 사용할 수 있으며 배포는 [Cloud Manager을 통해 수행됩니다.](/help/implementing/deploying/overview.md)

### 이전 CIF 버전 {#previous-versions-venia}

* CIF Classic: AEM 패키지 설치
* CIF 오픈 소스: [Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/content/introduction.html?lang=ko)을 통해

## 제품 카탈로그 데이터 {#product-catalog-data}

제품 카탈로그 데이터는 필요한 GraphQL API를 지원하는 외부 엔드포인트에 대한 실시간 호출을 통해 온디맨드로 요청됩니다. 이러한 API는 지정된 날짜에 라이브 또는 스테이징된 데이터에 대한 액세스를 지원합니다. 복제 불필요.

### 이전 CIF 버전 {#previous-versions-catalog}

* CIF Classic: 라이브 및 스테이징된 제품 데이터를 가져와 전체 또는 델타 제품 가져오기를 통해 AEM Author의 JCR에서 지속됩니다. 라이브 제품 데이터가 AEM 게시로 복제됩니다.

## AEM 렌더링을 사용한 제품 카탈로그 경험 {#catalog-experiences}

AEM은 제품 및 범주에 할당된 AEM 카탈로그 템플릿을 사용하여 제품 카탈로그 경험을 즉시 렌더링합니다. 복제 불필요.

### 이전 CIF 버전 {#previous-cif-versions}

* CIF Classic: AEM 작성자는 카탈로그 블루프린트 도구를 사용하여 모든 카테고리/제품에 대한 AEM 페이지를 만듭니다. 이러한 페이지는 AEM 게시로 복제됩니다.

>[!NOTE]
>
>AEM Managed Service 또는 AEM On-premise와 함께 CIF을 사용하는 방법에 대한 추가 설명서는 [Commerce integration framework](https://www.adobe.io/apis/experiencecloud/commerce-integration-framework/getting-started.html)을(를) 참조하십시오.
