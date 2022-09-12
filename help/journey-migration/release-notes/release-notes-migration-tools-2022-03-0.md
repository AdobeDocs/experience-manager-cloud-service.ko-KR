---
title: AEM as a Cloud Service 릴리스 2022.3.0의 마이그레이션 도구에 대한 릴리스 노트
description: AEM as a Cloud Service 릴리스 2022.3.0의 마이그레이션 도구에 대한 릴리스 노트
feature: Release Information
exl-id: ab43605d-d46e-43de-b71f-fab610609550
source-git-commit: 87e3291b4a72c24fc6cf8df488df305f1a078ea5
workflow-type: tm+mt
source-wordcount: '366'
ht-degree: 86%

---

# AEM as a Cloud Service 릴리스 2022.3.0의 마이그레이션 도구에 대한 릴리스 노트 {#release-notes}

이 페이지에서는 AEM as a Cloud Service 2022.3.0의 마이그레이션 도구에 대한 릴리스 노트를 간략하게 설명합니다.

## Best Practices Analyzer {#bpa-release}

### 릴리스 날짜 {#release-date-bpa}

Best Practices Analyzer v2.1.26의 릴리스 날짜는 2022년 3월 16일입니다.

### 새로운 기능 {#what-is-new-bpa}

* 처리되지 않은 에셋을 감지할 수 있습니다. 처리되지 않은 에셋이 감지되면 이들 에셋을 처리됨으로 설정하거나 콘텐츠 전송 도중 마이그레이션 세트에서 제거하여 콘텐츠 수집 과정에서 문제가 발생하지 않도록 해야 합니다.
* 콘텐츠의 vanity URL이 1000개를 초과하는지 감지할 수 있습니다. 디스패처 및 게시 서버에 부하가 걸리게 되므로 다수의 vanity URL을 사용하는 것은 권장되지 않습니다.
* Oak 인덱스 정의와 관련된 문제를 식별하고 AEM as a Cloud Service와의 비호환성을 감지할 수 있습니다.
* 외부화 구성의 사용을 감지하고 보고할 수 있습니다. AEM as a Cloud Service 외부화 구성은 Cloud Manager에 의해 설정되므로 호환성을 유지하려면 기존 외부화 구성을 리팩터링해야 합니다.

### 버그 수정 {#bug-fixes-bpa}

* 일부 시나리오에서 어설션 오류를 발생시키는 FormsSelectiveFeaturesAnalysis로 인해 BPA가 실행되지 못했습니다. 이 문제가 해결되었습니다.
* BPA가 WRK 패턴과 관련된 결과를 “심각”이 아닌 “주요” 문제로 보고했습니다. 이 문제가 해결되었습니다.
* BPA가 ui.apps의 OAK 인덱스 정의와 관련된 결과를 “심각”으로 잘못 보고했습니다. 이 문제가 해결되었습니다.

## 콘텐츠 전송 도구 {#ctt-release}

### 릴리스 날짜 {#release-date-ctt}

콘텐츠 전송 도구 v1.9.0의 릴리스 날짜는 2022년 2월 28일입니다.

### 새로운 기능 {#what-is-new-ctt}

* 점검 크기 가드레일 - 콘텐츠 전송 도구 점검 크기 기능을 사용하여 콘텐츠 전송 실패율을 줄일 수 있습니다.  점검 크기 기능을 사용하여 1) 추출하기 전에 `crx-quickstart` 하위 디렉터리에 디스크 공간이 충분한지 결정하고, 2) 마이그레이션 세트 크기를 예측하고 현재 지원되는지 확인할 수 있습니다. 점검 사항 중 하나 또는 두 개 모두 위반한 경우 CTT UI에 경고가 표시됩니다. 이 가드레일을 사용하여 콘텐츠 전송 실패를 방지하고, Adobe 고객 지원 센터와 주도적으로 마이그레이션 옵션에 대해 논의할 수 있습니다. 자세한 내용은 [마이그레이션 세트 크기 및 디스크 공간 확인](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/getting-started-content-transfer-tool.html?lang=ko#migration-set-size)을 참조하십시오.
