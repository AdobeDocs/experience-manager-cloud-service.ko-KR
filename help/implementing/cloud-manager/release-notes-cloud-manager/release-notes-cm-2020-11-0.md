---
title: AEM as a Cloud Service 릴리스 2020.11.0의 Cloud Manager 릴리스 노트
description: AEM as a Cloud Service 릴리스 2020.11.0의 Cloud Manager 릴리스 노트
feature: Release Information
exl-id: e2acf515-d339-4d2b-9b62-09c1dab1ffac
source-git-commit: 09d5d125840abb6d6cc5443816f3b2fe6602459f
workflow-type: tm+mt
source-wordcount: '186'
ht-degree: 8%

---

# Adobe Experience Manager as a Cloud Service 2020.11.0의 Cloud Manager 릴리스 노트 {#release-notes}

이 페이지에서는 AEM as a Cloud Service Manager에 대한 릴리스 노트를 간략하게 설명합니다2020.11.0.

## 릴리스 날짜 {#release-date}

AEM as a Cloud Service 2020.11.0의 Cloud Manager 릴리스 날짜는 2020년 11월 12일입니다.

## Cloud Manager {#cloud-manager}

### 새로운 기능 {#what-is-new}

* 새 메뉴 옵션 **로컬 로그인** 이제 환경 카드 및 환경 요약 페이지의 환경 메뉴 옵션에서 사용자가 이 기능을 사용할 수 있습니다.
자세한 내용은 [환경 관리](/help/implementing/cloud-manager/manage-environments.md#login-locally)를 참조하십시오.

* 다음 **학습** cloud Manager의 탭이 UI의 새 이미지로 새로 고침되었습니다.

### 버그 수정 {#bug-fixes-cloud-manager}

* 빌드 실행 전에 수행된 종속성을 로드하려면 Maven 플러그인을 다운로드해야 합니다.
* Cloud Manager 바닥글의 언어를 선택하는 링크를 통해 올바른 위치로 이동합니다.
* 코드 스캔 중에 SonarQube 프로세스가 시작되지 않는 경우가 있습니다. 이제 자동 검색되고 다시 시작하려고 합니다.
* 모든 기존 프로덕션 파이프라인은 경험 감사 단계에서 자동으로 활성화됩니다.
