---
title: 릴리스 2020.3.0 릴리스 노트
description: 릴리스 2020.3.0 릴리스 노트
exl-id: 0393c789-3999-4e51-be83-269d6eabd3f3
source-git-commit: 90de3cf9bf1c949667f4de109d0b517c6be22184
workflow-type: tm+mt
source-wordcount: '245'
ht-degree: 100%

---

# AEM as a Cloud Service 2020.3.0 릴리스 노트 {#release-notes}

이 페이지에서는 Experience Manager as a Cloud Service 2020.3.0 일반 릴리스 노트를 간략하게 설명합니다.

## 릴리스 일자 {#release-date}

Experience Manager as a Cloud Service 2020.3.0의 출시일은 2020년 3월 5일입니다.

## Cloud Manager {#cloud-manager}

AEM as a Cloud Service 릴리스 2020.3.0에 있는 Cloud Manager의 새로운 기능과 업데이트에 대해 알려면 이 섹션을 따르십시오.

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
