---
title: Cloud Service 릴리스 2020.11.0으로서 AEM의 Cloud Manager에 대한 릴리스 노트
description: Cloud Service 릴리스 2020.11.0으로서 AEM의 Cloud Manager에 대한 릴리스 노트
translation-type: tm+mt
source-git-commit: 738cff4231f329826b44f1b0f1a184fa15edd82a
workflow-type: tm+mt
source-wordcount: '186'
ht-degree: 4%

---


# Cloud Service 2020.11.0인 Adobe Experience Manager의 클라우드 관리자에 대한 릴리스 노트 {#release-notes}

이 페이지에서는 AEM의 Cloud Manager 릴리스 노트를 Cloud Service 2020.11.0으로 간략하게 설명합니다.

## 릴리스 날짜 {#release-date}

2020.11.0 Cloud Service으로 AEM의 Cloud Manager에 대한 릴리스 날짜는 2020년 11월 12일입니다.

## Cloud Manager {#cloud-manager}

### 새로운 기능 {#what-is-new}

* 이제 환경 카드 및 환경 요약 페이지의 환경 메뉴 옵션에서 사용자가 새 메뉴 옵션 **로컬 로그인**을 사용할 수 있습니다.
자세한 내용은 [환경 관리](/help/implementing/cloud-manager/manage-environments.md##login-locally)를 참조하십시오.

* Cloud Manager의 **학습** 탭이 UI의 새 이미지로 새로 고침되었습니다.

### 버그 수정 {#bug-fixes-cloud-manager}

* 빌드 실행 전에 수행된 종속성 로딩은 Maven 플러그인을 다운로드해야 합니다.
* 이제 언어를 선택하는 Cloud Manager 바닥글의 링크가 올바른 위치로 이동합니다.
* 경우에 따라 코드 검색 중 SonarQube 프로세스가 시작되지 않습니다. 이제 자동으로 감지되고 다시 시작하려고 합니다.
* 모든 기존 프로덕션 파이프라인은 경험 감사 단계를 통해 자동으로 활성화됩니다.