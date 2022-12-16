---
title: AEM as a Cloud Service 릴리스 2022.7.0의 마이그레이션 도구에 대한 릴리스 노트
description: AEM as a Cloud Service 릴리스 2022.7.0의 마이그레이션 도구에 대한 릴리스 노트
feature: Release Information
exl-id: bc8f1a80-867e-423a-9c03-4a53b1ebc57c
source-git-commit: cc52dfac1e7495d6a792bc7525720695022db8eb
workflow-type: tm+mt
source-wordcount: '430'
ht-degree: 9%

---

# AEM as a Cloud Service 릴리스 2022.7.0의 마이그레이션 도구에 대한 릴리스 노트 {#release-notes}

이 페이지에서는 AEM as a Cloud Service 2022.7.0의 마이그레이션 도구에 대한 릴리스 노트를 간략하게 설명합니다.

## Best Practices Analyzer {#bpa-release}

### 릴리스 날짜 {#release-date-bpa}

Best Practices Analyzer v2.1.30 릴리스 날짜는 2022년 7월 27일입니다.

### 새로운 기능 {#what-is-new-bpa}

* 이제 BPA는 Total Lucene Index를 제외한 마이그레이션 가능한 총 Lucene Index 크기를 감지하고 보고할 수 있습니다 `/oak:index/lucene` 및 `/oak:index/damAssetLucene`.
* 사용자 지정 i18n 사전 사용을 감지하고 보고하기 위해 BPA에 새로운 패턴이 추가되었습니다. Translator.html은 AEM as a Cloud Service에서 사용할 수 없으며 사용자 지정 i18n 사전을 Cloud Manager CI/CD 파이프라인을 통해 Git에서 배포해야 합니다.

### 버그 수정 {#bug-fixes-bpa}

* BPA가 컨텐츠 조각에 대한 원래 표현물이 누락되었다고 보고했습니다. 컨텐츠 조각에 표현물이 없으므로 이제 컨텐츠 조각에 대해 이 검사를 건너뜁니다.
* ACS Commons 결과를 필터링하는 옵션이 BPA UI에서 누락되었습니다. 이 문제가 해결되었습니다.

## 콘텐츠 전송 도구 {#ctt-release}

### 릴리스 날짜 {#release-date-ctt}

컨텐츠 전송 도구 v2.0.12의 릴리스 날짜는 2022년 7월 19일입니다.

### 새로운 기능 {#what-is-new-ctt}

* LDAP를 통해 로그인한 사용자는 이제 CTT에서 확인 크기 및 사용자 매핑 기능을 실행할 수 있습니다.
* 추출 중에 SSL/TLS 연결 문제를 디버깅하는 데 도움이 되도록 이제 사용자가 SSL 로깅을 활성화할 수 있습니다.
* 소스 연결 문제를 디버깅하는 데 도움이 되도록 이제 Azure에 연결하지 못할 때 하위 도메인 이름이 로그에 인쇄됩니다.
* 이제 사전 복사 중에 디버그 문제를 지원하기 위해 사전 복사가 실패할 때 AzCopy 로그가 추출 로그에 추가됩니다.
* 오래된 확인 크기 결과를 방지하려면 이전 확인 크기가 완료된 후에만 확인 크기를 다시 실행할 수 있습니다.

### 버그 수정 {#bug-fixes-ctt}

* 마이그레이션 세트를 삭제하고 다시 만든 후 이전 추출 로그가 표시되었습니다. 이 문제가 해결되었습니다.
* STOPTED 상태의 마이그레이션 세트에 대해 진행 보기 작업 단추를 사용할 수 없습니다. 이 문제가 해결되었습니다.
* 만료된 추출 키를 사용하는 마이그레이션 세트에 대해 작업 삭제 단추를 사용할 수 없습니다. 이 문제가 해결되었습니다.
* 여러 UI 버그가 수정되었습니다.

## Cloud Acceleration Manager {#cam-release}

### 릴리스 일자 {#release-date-cam}

Cloud Acceleration Manager 릴리스 날짜는 2022년 7월 15일입니다.

### 새로운 기능 {#what-is-new-cam}

* 이제 Cloud Acceleration Manager에서는 자동 검색이 실패할 때 수집을 시작할 수 있도록 마이그레이션 토큰을 수동으로 검색하는 기능을 제공합니다. 고객이 CAM을 차단하는 IP 허용 목록을 설정하거나 관리자가 아닌 사용자가 수집을 시작하려고 시도하는 경우 자동 검색이 실패할 수 있습니다. 을(를) 참조하십시오. [문제 해결](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/ingesting-content.md#troubleshooting) 추가 정보.
* 이제 마이그레이션 복잡도 페이지의 긴 테이블을 쉽게 사용할 수 있도록 축소됩니다.
