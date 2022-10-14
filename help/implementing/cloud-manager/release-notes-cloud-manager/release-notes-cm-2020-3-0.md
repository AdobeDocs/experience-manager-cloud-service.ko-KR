---
title: AEM as a Cloud Service 릴리스 2020.3.0의 Cloud Manager 릴리스 정보
description: AEM as a Cloud Service 릴리스 2020.3.0의 Cloud Manager 릴리스 정보
feature: Release Information
exl-id: 2ff62ba5-a657-4739-b646-1e948332bf79
source-git-commit: 09d5d125840abb6d6cc5443816f3b2fe6602459f
workflow-type: tm+mt
source-wordcount: '245'
ht-degree: 100%

---

# Adobe Experience Manager as a Cloud Service 2020.3.0의 Cloud Manager 릴리스 정보 {#release-notes}

이 페이지에서는 AEM as a Cloud Service 2020.3.0의 Cloud Manager 릴리스 정보에 대해 간략히 설명합니다.

## 릴리스 일자 {#release-date}

AEM as a Cloud Service 2020.3.0의 Cloud Manager 릴리스 일자는 2020년 3월 5일입니다.

### 새로운 기능 {#what-is-new}

* 이제 빌드 단계가 실행되는 동안 빌드 단계에 대한 로그를 사용할 수 있습니다.
* 파이프라인 실행 세부 사항 페이지에 나와 있는 메시지 중 일부가 명확한 의미 전달을 위해 편집되었습니다.

### 버그 수정  {#bug-fixes}

* 사용자 정의 및 제품 기능 테스트 단계에 대한 로그 파일은 UI를 통해 다운로드할 수 없습니다.
* 클라우드 서비스 프로그램에 대한 git 저장소를 만들지 못한 경우 배포 관리자 역할을 하는 사용자가 이 오류에서 복구할 수 없는 경우가 있었습니다.
* 샌드박스 프로그램을 생성하는 동안 특정 사용자 활동으로 인해 비프로덕션 파이프라인이 생성되기 전에 프로그램이 생성되지 않을 수 있습니다.
* 빌드 단계에서 사용되는 사용 후 삭제되는 SonarQube 인스턴스가 구성된 제한 시간 내에 시작되지 않는 경우가 있었습니다.
* 동일한 클라우드 서비스 프로그램에서 개발 환경을 동시에 만들면 하나만 성공적으로 만들 수 있는 조건이 발생할 수 있습니다.
* 클라우드 서비스 프로그램에 대한 Experience Cloud 알림을 일관되게 받지 못했습니다.
* 특정 프로젝트에서 *ResourceResolver 개체를 항상 닫으면* Null 포인터 예외가 발생하지만 파이프라인 실행에는 영향을 주지 않았습니다.
