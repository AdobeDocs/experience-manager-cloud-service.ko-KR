---
title: AEM as a Cloud Service 릴리스 2020.10.0의 Cloud Manager 릴리스 노트
description: AEM as a Cloud Service 릴리스 2020.10.0의 Cloud Manager 릴리스 노트
feature: 릴리스 정보
exl-id: 129d0dd8-3d6e-4cf0-b42e-5526f5cf0836
source-git-commit: 90de3cf9bf1c949667f4de109d0b517c6be22184
workflow-type: tm+mt
source-wordcount: '302'
ht-degree: 48%

---

# Adobe Experience Manager as a Cloud Service 2020.10.0 {#release-notes} 의 Cloud Manager 릴리스 노트

이 페이지에서는 AEM as a Cloud Service 2020.10.0에 있는 Cloud Manager 릴리스 노트를 간략하게 설명합니다.

## 릴리스 날짜 {#release-date}

AEM as a Cloud Service 2020.10.0에 있는 Cloud Manager의 릴리스 날짜는 2020년 10월 1일입니다.

## Cloud Manager {#cloud-manager}

### 새로운 기능 {#what-is-new}

* 환경 페이지가 다시 디자인되었습니다.

* 최대 절전 모드인 환경에서 이제 최대 절전 모드일 경우 Cloud Manager에서 개별 상태를 볼 수 있습니다.

* 이제 Cloud Manager 빌드 컨테이너가 Java 8 또는 Java 11을 사용하여 프로젝트 컴파일링을 지원합니다. Java 11에 대한 지원은 Maven 도구 체인 시스템에서 제공합니다.

* 환경당 환경 변수의 수가 200개로 증가했습니다.

* 이제 개요 페이지의 환경 카드에 최대 3개의 환경이 나열됩니다. 사용자는 **모두 표시** 단추를 선택하여 환경 요약 페이지로 이동하여 전체 환경 목록이 있는 테이블을 볼 수 있습니다.
자세한 내용은 [환경 보기](/help/implementing/cloud-manager/manage-environments.md#viewing-environment)를 참조하십시오.


### 버그 수정 {#bug-fixes-cloud-manager}

* 환경이 완전히 만들어지기 전에 Cloud Manager에서 개발자 콘솔로의 링크가 잘못 활성화되었습니다.

* Cloud Manager에서 직접 개발자 콘솔로 연결되는 링크에는 샌드박스 프로그램 환경의 최대 절전 모드 해제/최대 절전 모드 해제 옵션이 표시되지 않습니다.

* 비프로덕션 파이프라인 편집 페이지의 취소 및 저장 단추가 항상 표시되는 것은 아닙니다.

* 코드 품질 프로세스의 일부 오류로 인해 로그 파일이 올바로 생성되지 않을 수 있습니다.

* 새 프로그램을 만들 때 제안된 이름은 기존 프로그램 이름의 복제본을 반환하는 경우가 있습니다.

* 일부 큰 파이프라인 단계 로그를 사용자 인터페이스를 통해 일관되게 다운로드할 수 없습니다.

* 환경 이름의 유효성 검사에 오류가 발생했습니다.

* 환경 페이지는 존재하지 않을 때 게시 및 발송자 세그먼트를 표시하는 경우가 있습니다.
