---
title: AEM as a Cloud Service 릴리스 2024.09의 마이그레이션 도구 릴리스 정보
description: AEM as a Cloud Service 릴리스 2024.09.0의 마이그레이션 도구 릴리스 정보
feature: Release Information
exl-id: 52709511-eab2-47a7-8bea-1b707cd568a1
role: Admin
source-git-commit: 0c16f264826a46907afc33c91a021e7696f5b7a8
workflow-type: tm+mt
source-wordcount: '230'
ht-degree: 7%

---

# AEM as a Cloud Service 릴리스 2024.09.0의 마이그레이션 도구 릴리스 정보 {#release-notes}

이 페이지에서는 AEM as a Cloud Service 2024.09.0의 마이그레이션 도구 릴리스 정보에 대해 간략히 설명합니다.

## 콘텐츠 전송 도구 {#ctt-release}

### 릴리스 날짜 {#release-date-ctt}

컨텐츠 전송 도구 v3.0.20의 릴리스 날짜는 2024년 8월 28일입니다.

### 새로운 기능 {#what-is-new-ctt}

* 사용자는 더 이상 이 릴리스에서 수집되지 않으며, 이러한 이유로 사용자 매핑 선택 기능이 제거되었습니다.
* 추출 및 수집 중에 주도자 마이그레이션을 비활성화하거나 활성화하기 위한 OSGI 구성 옵션이 추가되었습니다(기본 설정은 이를 활성화하는 것입니다).

### 버그 수정 {#bug-fixes-ctt}

* CTT가 개선되어 azcopy 구성에서 비밀 키의 보호를 해제하는 동안 오류가 발생하지 않습니다.
* 이제 CTT는 유효성 검사 단계에서 AzCopy 로그를 복사하는 동안 모든 오류를 정상적으로 처리합니다
* 추출 프로세스 중에 생성된 azcopy 로그 디렉토리 변경

## Best Practices Analyzer {#bpa-release}

### 릴리스 날짜 {#release-date-bpa}

모범 사례 분석기 v2.1.52의 릴리스 날짜는 2024년 9월 4일입니다

### 새로운 기능 {#what-is-new-bpa}

* AEM에서 JCR 기반 이벤트를 탐지하기 위해 새로운 패턴이 도입되었습니다

### 버그 수정 {#bug-fixes-bpa}

* 긍정 오류(false positive) 수정
* Dispatcher의 리디렉션된 응답을 처리하는 견고성 개선
* /apps/wcm/core/resources/languages/ 하의 모든 언어에 대한 NCC 검색 결과의 비보고를 해결했습니다.
* 노드의 다중 속성에 값이 없는지 확인하기 위한 검사를 추가했습니다.

