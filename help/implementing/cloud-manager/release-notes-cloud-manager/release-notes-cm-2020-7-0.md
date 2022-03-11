---
title: AEM as a Cloud Service 릴리스 2020.7.0의 Cloud Manager 릴리스 노트
description: AEM as a Cloud Service 릴리스 2020.7.0의 Cloud Manager 릴리스 노트
feature: Release Information
exl-id: b5ac4dd4-18c6-4867-b2df-53711555007f
source-git-commit: 596a7a41dac617e2fb57ba2e4891a2b4dce31fad
workflow-type: tm+mt
source-wordcount: '309'
ht-degree: 73%

---

# Adobe Experience Manager as a Cloud Service 2020.7.0의 Cloud Manager 릴리스 노트 {#release-notes}

이 페이지에서는 AEM as a Cloud Service 2020.7.0에 있는 Cloud Manager 릴리스 노트를 간략하게 설명합니다.

## 릴리스 날짜 {#release-date}

AEM as a Cloud Service 2020.7.0의 Cloud Manager 릴리스 날짜는 2020년 7월 9일입니다.

## 새로운 기능 {#whats-new-cloud-manager}

* 환경 페이지가 다시 디자인되었습니다.

* 최대 절전 모드인 환경에서 이제 최대 절전 모드일 경우 Cloud Manager에서 개별 상태를 볼 수 있습니다.

* 환경당 환경 변수의 수가 200개로 증가했습니다.

* 이제 Cloud Manager 파이프라인이 고객 설정 변수 및 암호를 지원합니다.

   자세한 내용은 파이프라인 변수를 참조하십시오.

* 이제 인증 바인딩된 Private Maven 리포지토리가 지원됩니다.

* 이제 Cloud Manager 빌드 컨테이너가 Java 8과 Java 11을 모두 지원합니다.
자세한 내용은 Java 11 지원 사용 을 참조하십시오.

### 버그 수정 {#bug-fixes-cm}

* 환경이 완전히 만들어지기 전에 Cloud Manager에서 개발자 콘솔로의 링크가 잘못 활성화되었습니다.

* Cloud Manager에서 직접 개발자 콘솔로 연결되는 링크에는 샌드박스 프로그램 환경의 최대 절전 모드 해제/최대 절전 모드 해제 옵션이 표시되지 않습니다.

* 비프로덕션 파이프라인 편집 페이지의 **취소** 및 **저장** 옵션이 항상 표시되는 것은 아닙니다.

* 코드 품질 프로세스의 일부 오류로 인해 로그 파일이 올바로 생성되지 않을 수 있습니다.

* 새 프로그램을 만들 때 제안된 이름은 기존 프로그램 이름의 복제본을 반환하는 경우가 있습니다.

* 일부 큰 파이프라인 단계 로그를 사용자 인터페이스를 통해 일관되게 다운로드할 수 없습니다.

* 환경 이름의 유효성 검사에 오류가 발생했습니다.

* 환경 페이지는 존재하지 않을 때 게시 및 발송자 세그먼트를 표시하는 경우가 있습니다.

### 알려진 문제 {#known-issues}

* 코드 검사 계산 방식의 변경으로 인해 Jacoco 플러그인의 *최소* 버전은 이제 0.7.5.201505241946(2015년 5월 릴리스)입니다. 이전 버전을 명시적으로 참조하는 고객은 코드 품질 프로세스에서 오류 메시지를 받게 됩니다.
