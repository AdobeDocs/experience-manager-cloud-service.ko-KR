---
title: AEM as a Cloud Service 릴리스 2022.4.0의 마이그레이션 도구에 대한 릴리스 노트
description: AEM as a Cloud Service 릴리스 2022.4.0의 마이그레이션 도구에 대한 릴리스 노트
feature: Release Information
source-git-commit: 87e3291b4a72c24fc6cf8df488df305f1a078ea5
workflow-type: tm+mt
source-wordcount: '232'
ht-degree: 5%

---

# AEM as a Cloud Service 릴리스 2022.4.0의 마이그레이션 도구에 대한 릴리스 노트 {#release-notes}

이 페이지에서는 AEM as a Cloud Service 2022.4.0의 마이그레이션 도구에 대한 릴리스 노트를 간략하게 설명합니다.

## Best Practices Analyzer {#bpa-release}

### 릴리스 날짜 {#release-date-bpa}

Best Practices Analyzer v2.1.28의 출시일은 2022년 4월 22일입니다.

### 새로운 기능 {#what-is-new-bpa}

* 지원되지 않는 Asset Manager API 사용을 감지하고 보고하는 기능. AEM as a Cloud Service에서 더 이상 지원되지 않는 API는 4개 있습니다. 고객은 이러한 API를 더 이상 사용하지 않으며 자산 업로드의 새로운 방법을 사용해야 합니다.

* 컨텐츠 조각 템플릿 사용을 탐지하는 기능. 컨텐츠 조각 템플릿은 AEM as a Cloud Service에서 새 컨텐츠 조각 만들기에 더 이상 지원되지 않습니다. 고객은 컨텐츠 조각 템플릿을 대체하기 위해 컨텐츠 조각 모델을 만들어야 합니다.

* 저장소에서 자산의 메타데이터 노드에서 100개 이상의 하위 항목이 있는 자산을 감지할 수 있습니다. 이러한 자산으로 구성된 폴더를 로드할 때 성능을 향상하기 위해 필요하지 않은 메타데이터 노드를 제거하는 것이 좋습니다.

* 사용된 데이터 저장소 유형을 감지하고 보고하는 기능.

* AEM Form Portal에 대해 업데이트된 패턴입니다.

### 버그 수정 {#bug-fixes-bpa}

* BPA는 고객 구성 요소에만 보고하지 않고 핵심 구성 요소에 대한 결과 보고를 수행했습니다. 이 문제가 해결되었습니다.