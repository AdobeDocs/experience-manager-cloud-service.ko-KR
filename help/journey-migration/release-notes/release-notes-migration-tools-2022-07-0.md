---
title: AEM as a Cloud Service 릴리스 2022.7.0의 마이그레이션 도구 릴리스 정보
description: AEM as a Cloud Service 릴리스 2022.7.0의 마이그레이션 도구 릴리스 정보
feature: Release Information
exl-id: bc8f1a80-867e-423a-9c03-4a53b1ebc57c
source-git-commit: 1994b90e3876f03efa571a9ce65b9fb8b3c90ec4
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 9%

---

# AEM as a Cloud Service 릴리스 2022.7.0의 마이그레이션 도구 릴리스 정보 {#release-notes}

이 페이지에서는 AEM as a Cloud Service 2022.7.0의 마이그레이션 도구 릴리스 정보에 대해 간략히 설명합니다.

## Best Practices Analyzer {#bpa-release}

### 릴리스 날짜 {#release-date-bpa}

Best Practices Analyzer v2.1.30의 릴리스 날짜는 2022년 7월 27일입니다.

### 새로운 기능 {#what-is-new-bpa}

* 이제 BPA는 다음을 제외한 총 마이그레이션 가능한 Lucene 인덱스 크기인 총 Lucene 인덱스를 감지하고 보고할 수 있습니다. `/oak:index/lucene` 및 `/oak:index/damAssetLucene`.
* 사용자 지정 i18n 사전의 사용을 감지하고 보고하기 위해 BPA에 새로운 패턴이 추가되었습니다. Translator.html은 AEM as a Cloud Service에서 사용할 수 없으며 사용자 지정 i18n 사전을 Cloud Manager CI/CD 파이프라인을 통해 Git에서 배포해야 합니다.

### 버그 수정 {#bug-fixes-bpa}

* BPA가 콘텐츠 조각에 대한 원본 렌디션 누락을 보고했습니다. 콘텐츠 조각에는 렌디션이 없으므로 콘텐츠 조각에 대해서는 이제 이 검사를 건너뜁니다.
* ACS Commons 검색 결과를 필터링하는 옵션이 BPA UI에서 누락되었습니다. 이 문제가 해결되었습니다.

## 콘텐츠 전송 도구 {#ctt-release}

### 릴리스 날짜 {#release-date-ctt}

컨텐츠 전송 도구 v2.0.12의 릴리스 날짜는 2022년 7월 19일입니다.

### 새로운 기능 {#what-is-new-ctt}

* LDAP를 통해 로그인한 사용자는 이제 CTT에서 크기 확인 및 사용자 매핑 기능을 실행할 수 있습니다.
* 추출 중에 SSL/TLS 연결 문제를 디버깅하기 위해 사용자는 이제 SSL 로깅을 활성화할 수 있습니다.
* 이제 소스 연결 문제를 디버깅할 수 있도록 Azure 연결에 실패하면 하위 도메인 이름이 로그에 인쇄됩니다.
* 사전 복사 중 문제를 디버깅하기 위해 이제 사전 복사가 실패할 때 AzCopy 로그가 추출 로그에 추가됩니다.
* 부실한 검사 크기 결과를 방지하기 위해 사용자는 이전 검사 크기가 완료된 후에만 검사 크기를 다시 실행할 수 있습니다.

### 버그 수정 {#bug-fixes-ctt}

* 마이그레이션 세트를 삭제하고 다시 만든 후 이전 추출 로그가 표시되었습니다. 이 문제가 해결되었습니다.
* 정지됨 상태의 마이그레이션 세트에는 진행 상황 보기 작업 버튼을 사용할 수 없습니다. 이 문제가 해결되었습니다.
* 만료 추출 키가 있는 마이그레이션 세트에 대해 작업 삭제 버튼을 사용할 수 없습니다. 이 문제가 해결되었습니다.
* 여러 UI 버그가 수정되었습니다.

## Cloud Acceleration Manager {#cam-release}

### 릴리스 일자 {#release-date-cam}

Cloud Acceleration Manager 의 릴리스 날짜는 2022년 7월 15일입니다.

### 새로운 기능 {#what-is-new-cam}

* Cloud Acceleration Manager는 이제 자동 검색이 실패할 때 수집을 시작할 수 있도록 사용자가 마이그레이션 토큰을 수동으로 검색할 수 있도록 제공합니다. 고객이 CAM을 차단하는 IP 허용 목록을 설정했거나 관리자가 아닌 사용자가 수집을 시작하려고 하는 경우 자동 검색이 실패할 수 있습니다. 다음을 참조하십시오 [문제 해결](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/ingesting-content.md#troubleshooting) 추가 정보.
* 이제 마이그레이션 복잡성 페이지의 긴 테이블을 쉽게 접을 수 있습니다.
