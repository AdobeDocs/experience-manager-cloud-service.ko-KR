---
title: AEM as a Cloud Service 릴리스 2022.5.0의 마이그레이션 도구 릴리스 정보
description: AEM as a Cloud Service 릴리스 2022.5.0의 마이그레이션 도구 릴리스 정보
feature: Release Information
exl-id: 1aa49e85-1914-44d9-bcf7-0a1b03926df0
source-git-commit: 01c4a21b980918ba99ac174419d80b577bc96dda
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 12%

---

# AEM as a Cloud Service 릴리스 2022.5.0의 마이그레이션 도구 릴리스 정보 {#release-notes}

이 페이지에서는 AEM as a Cloud Service 2022.5.0의 마이그레이션 도구 릴리스 정보에 대해 간략히 설명합니다.

## Best Practices Analyzer {#bpa-release}

### 릴리스 날짜 {#release-date-bpa}

Best Practices Analyzer v2.1.30의 릴리스 날짜는 2022년 6월 1일입니다.

### 새로운 기능 {#what-is-new-bpa}

* CoralUI 및 클래식 대화 상자 위젯을 사용하여 사용자 정의 대화 상자 위젯의 사용을 감지하고 보고하는 기능. 사용자 정의 클래식 대화 상자 위젯을 ExtJS에서 CoralUI로 변환하는 것이 좋습니다. 사용자 정의 Coral 대화 상자 위젯은 CoralUI3로 업데이트해야 합니다.
* Assets Share Commons의 사용 및 버전을 감지하고 보고하는 기능. Asset Share Commons 1.x는 AEM as a Cloud Service에서 지원되지 않으며 2.x로 업그레이드해야 합니다.
* 버전에서 노드 수를 감지하고 보고하는 기능.
* 사용자 정의 복제 에이전트 또는 수정된 기본 복제 에이전트를 감지하고 보고하는 기능.

### 버그 수정 {#bug-fixes-bpa}

* BPA가 긍정 오류(false positive)인 NCC(호환되지 않는 변경), UMI(업그레이드 잘못된 구성 문제) 및 PCX(페이지 복잡성) 검색 결과를 보고했습니다. 이러한 문제가 해결되었습니다.
* 노드 이름 길이가 150바이트를 초과할 때 BPA에서 오류를 보고했습니다. 이 오류는 노드 상위 경로가 350바이트보다 크거나 같은 경우에만 이러한 오류를 검색하도록 수정되었습니다.

## 콘텐츠 전송 도구 {#ctt-release}

### 릴리스 날짜 {#release-date-ctt}

컨텐츠 전송 도구 v2.0.10의 릴리스 날짜는 2022년 6월 2일입니다.

### 새로운 기능 {#what-is-new-ctt}

* CTT(콘텐츠 전송 도구)는 Cloud Acceleration Manager와 함께 전체 콘텐츠 전송 프로세스를 간소화하도록 발전되었습니다. 이제 CTT는 콘텐츠 추출 수행에 중점을 둡니다. 이제 CTT 수집 서비스가 Cloud Acceleration Manager에 통합됩니다. 이러한 진화를 통해 제공되는 이점은 다음과 같습니다.
   * 마이그레이션 세트를 한 번 추출하여 동시에 여러 환경에서 수집하는 셀프서비스 방식.
   * 효율적인 로딩 상태, 가드레일 및 오류 처리를 통해 개선된 사용자 경험.
   * 수집 로그는 지속되며 항상 문제 해결에 사용할 수 있습니다.

## Cloud Acceleration Manager {#cam-release}

### 릴리스 일자 {#release-date-cam}

Cloud Acceleration Manager 의 릴리스 날짜는 2022년 6월 2일입니다.

### 새로운 기능 {#what-is-new-cam}

* Cloud Acceleration Manager는 이제 마이그레이션 프로젝트의 일부로 고객의 AEM 인스턴스(온-프레미스 또는 Adobe Managed Services)에서 AEM as a Cloud Service으로 콘텐츠를 이동하기 위한 콘텐츠 전송을 시작하고 관리할 수 있는 기능을 사용자에게 제공합니다. 을(를) 참조하십시오 [컨텐츠 전송 카드 사용](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-acceleration-manager/using-cam/cam-implementation-phase.html#content-transfer) 을 참조하십시오.
