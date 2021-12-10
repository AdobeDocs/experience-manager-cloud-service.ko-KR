---
title: AEM as a Cloud Service 릴리스의 마이그레이션 도구에 대한 릴리스 2021.12.0
description: AEM as a Cloud Service 릴리스의 마이그레이션 도구에 대한 릴리스 2021.12.0
feature: Release Information
source-git-commit: 58dcf083ebf4cd2546213ba574f0f9c547aef008
workflow-type: tm+mt
source-wordcount: '257'
ht-degree: 7%

---


# AEM as a Cloud Service 릴리스의 마이그레이션 도구에 대한 릴리스 2021.12.0 {#release-notes}

이 페이지에서는 AEM as a Cloud Service의 마이그레이션 도구에 대한 릴리스 노트를 간략하게 설명합니다2021.12.0.

>[!NOTE]
>Adobe Experience Manager as a Cloud Service의 현재 릴리스 노트를 보려면 [여기](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/release-notes/release-notes/release-notes-current.html?lang=ko-KR).

## 모범 사례 분석기 {#bpa-release}

### 릴리스 날짜 {#release-date-bpa}

Best Practices Analyzer v2.1.22 릴리스 날짜는 2021년 12월 1일입니다.

### 새로운 기능 {#what-is-new-bpa}

* 사용된 ACS commons 버전을 감지하고 보고하는 기능.
* 그룹의 사용자 및 하위 그룹 수를 감지하고 보고하는 기능.
* 16MB를 초과하는 MongoDB의 노드 속성 값을 감지하고 보고할 수 있습니다.

### 버그 수정 {#bug-fixes-bpa}

* 잘못된 네거티브를 줄이기 위해 기초 구성 요소 탐지를 개선했습니다.
* AEM Forms 고객의 경우 `EMAIL_PDF_SUBMIT_ACTION` AEM as a Cloud Service에서 사용할 수 없는 것이 수정되었습니다.


## 컨텐츠 전송 도구 {#ctt-release}

### 릴리스 날짜 {#release-date-ctt}

컨텐츠 전송 도구 v1.7.10의 릴리스 날짜는 2021년 12월 8일입니다.

### 새로운 기능 {#what-is-new-ctt}

* 사용자가 비활성화할 수 있도록 컨텐츠 전송 도구에서 수집 단계에 추가/전환 [사전 복사](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/handling-large-content-repositories.html?lang=en) 수집 중. 최적의 수집 속도를 위해 작은 마이그레이션 세트에 대해 또는 마지막 수집 이후 몇 개의 Blob만 추가한 경우 수집 중 사전 복사를 비활성화해야 합니다.
* 사용자 매핑 을 업데이트하여 한 번에 2,000명의 사용자를 얻을 수 있는 향상된 사용자 관리 API를 사용하여 성능을 크게 개선했습니다.
