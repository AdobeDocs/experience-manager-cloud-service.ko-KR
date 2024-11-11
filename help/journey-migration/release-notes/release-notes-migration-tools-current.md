---
title: AEM as a Cloud Service 릴리스 2024.09의 마이그레이션 도구 릴리스 정보
description: AEM as a Cloud Service 릴리스 2024.09.0의 마이그레이션 도구 릴리스 정보
feature: Release Information
exl-id: 52709511-eab2-47a7-8bea-1b707cd568a1
role: Admin
source-git-commit: 0c16f264826a46907afc33c91a021e7696f5b7a8
workflow-type: ht
source-wordcount: '230'
ht-degree: 100%

---

# AEM as a Cloud Service 릴리스 2024.09.0의 마이그레이션 도구 릴리스 정보 {#release-notes}

이 페이지에서는 AEM as a Cloud Service 2024.09.0의 마이그레이션 도구 릴리스 정보에 대해 간략히 설명합니다.

## 콘텐츠 전송 도구 {#ctt-release}

### 릴리스 일자 {#release-date-ctt}

콘텐츠 전송 도구 v3.0.20의 릴리스 일자는 2024년 8월 28일입니다.

### 새로운 기능 {#what-is-new-ctt}

* 이 릴리스에서는 더 이상 사용자를 수집할 수 없으므로 사용자 매핑 옵션 기능이 제거되었습니다.
* 추출 및 섭취 중에 주체의 마이그레이션을 비활성화하거나 활성화하는 OSGI 구성 옵션이 추가되었습니다(기본 설정은 활성화).

### 버그 수정 {#bug-fixes-ctt}

* CTT는 azcopy 구성에서 비밀 키 보호를 해제하면서 오류를 방지하도록 개선되었습니다
* 이제 CTT는 유효성 검사 단계에서 AzCopy 로그를 복사하는 동안 모든 오류를 정상적으로 처리합니다
* 추출 과정 중 생성된 azcopy 로그 디렉터리 변경

## Best Practices Analyzer {#bpa-release}

### 릴리스 일자 {#release-date-bpa}

모범 사례 분석기 v2.1.52의 릴리스 일자는 2024년 9월 4일입니다.

### 새로운 기능 {#what-is-new-bpa}

* AEM에서 JCR 기반 이벤트를 감지하기 위해 새로운 패턴이 도입되었습니다.

### 버그 수정 {#bug-fixes-bpa}

* 긍정 오류 수정됨
* Dispatcher에서 리디렉션된 응답을 처리할 수 있는 견고성 향상
* /apps/wcm/core/resources/languages/ 아래의 모든 언어에 대한 NCC 발견의 비보고가 수정됨
* 노드의 다중 속성 값이 없는지 감지하는 검사를 추가함

