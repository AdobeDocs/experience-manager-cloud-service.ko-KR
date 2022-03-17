---
title: AEM as a Cloud Service 릴리스 2022.3.0의 마이그레이션 도구에 대한 릴리스 노트
description: AEM as a Cloud Service 릴리스 2022.3.0의 마이그레이션 도구에 대한 릴리스 노트
feature: Release Information
source-git-commit: c497424271ea960d22a30b4a6c66432935ec820d
workflow-type: tm+mt
source-wordcount: '366'
ht-degree: 7%

---


# AEM as a Cloud Service 릴리스 2022.3.0의 마이그레이션 도구에 대한 릴리스 노트 {#release-notes}

이 페이지에서는 AEM as a Cloud Service 2022.3.0의 마이그레이션 도구에 대한 릴리스 노트를 간략하게 설명합니다.

## 모범 사례 분석기 {#bpa-release}

### 릴리스 날짜 {#release-date-bpa}

Best Practices Analyzer v2.1.26 릴리스 날짜는 2022년 3월 16일입니다.

### 새로운 기능 {#what-is-new-bpa}

* 처리되지 않은 자산을 탐지하는 기능. 처리되지 않은 자산이 감지되면 이러한 자산을 처리됨으로 설정해야 하거나 컨텐츠를 처리하는 동안 문제가 발생하지 않도록 컨텐츠를 전송하는 동안 마이그레이션 세트에서 제거해야 합니다.
* 컨텐츠에 별칭 URL이 1,000개를 초과하는지 감지하는 기능. 별칭 URL을 많이 사용하는 것은 Dispatcher 및 Publish 서버에 로드되므로 좋지 않습니다.
* Oak 색인 정의와 관련된 문제를 식별하고 AEM as a Cloud Service와의 비호환성을 감지하는 기능.
* 외부자 구성 사용을 감지하고 보고하는 기능. AEM as a Cloud Service Externalizer 구성은 Cloud Manager에 의해 설정되므로 호환성을 유지하기 위해 기존 Externalizer 구성을 리팩터링해야 합니다.

### 버그 수정 {#bug-fixes-bpa}

* 일부 시나리오에서 FormsSelectiveFeaturesAnalysis에서 어설션 오류가 발생하여 BPA를 실행하지 못했습니다. 이 문제가 해결되었습니다.
* BPA는 WRK 패턴과 관련된 결과를 CRITICAL 대신 MAJOR로 보고 중이었습니다. 이 문제가 해결되었습니다.
* BPA가 ui.apps의 OAK 색인 정의와 관련된 결과를 CRITICAL로 잘못 보고했습니다. 이 문제가 해결되었습니다.

## 콘텐츠 전송 도구 {#ctt-release}

### 릴리스 날짜 {#release-date-ctt}

컨텐츠 전송 도구 v1.9.0의 릴리스 날짜는 2022년 2월 28일입니다.

### 새로운 기능 {#what-is-new-ctt}

* 크기 보호 확인 - 컨텐츠 전송 도구 확인 크기 기능은 실패한 컨텐츠 전송을 줄이는 데 도움이 됩니다.  [크기 확인] 기능을 사용하면 1) 사용자가 1) `crx-quickstart` 하위 디렉토리 추출 전 및 2) 마이그레이션 세트 크기를 추정하고 지원되는지 확인합니다. 이 검사 중 하나 또는 둘 다를 위반한 경우 CTT UI에 경고가 표시됩니다. 이러한 보호를 통해 컨텐츠 전송 오류를 방지하고 Adobe 고객 지원 센터를 통해 마이그레이션 옵션에 대해 미리 논의할 수 있습니다. 을(를) 참조하십시오. [마이그레이션 세트 크기 및 디스크 공간 확인](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/getting-started-content-transfer-tool.html?lang=en#migration-set-size) 자세한 내용