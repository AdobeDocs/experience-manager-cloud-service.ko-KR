---
title: AEM as a Cloud Service 릴리스 2022.4.0의 마이그레이션 도구 릴리스 정보
description: AEM as a Cloud Service 릴리스 2022.4.0의 마이그레이션 도구 릴리스 정보
feature: Release Information
exl-id: 4941736b-82cd-4050-b3e9-aef250d5c4c7
source-git-commit: a3e79441d46fa961fcd05ea54e84957754890d69
workflow-type: tm+mt
source-wordcount: '231'
ht-degree: 5%

---

# AEM as a Cloud Service 릴리스 2022.4.0의 마이그레이션 도구 릴리스 정보 {#release-notes}

이 페이지에서는 AEM as a Cloud Service 2022.4.0의 마이그레이션 도구 릴리스 정보에 대해 간략히 설명합니다.

## Best Practices Analyzer {#bpa-release}

### 릴리스 날짜 {#release-date-bpa}

모범 사례 분석기 v2.1.28의 릴리스 날짜는 2022년 4월 22일입니다.

### 새로운 기능 {#what-is-new-bpa}

* 지원되지 않는 Asset Manager API의 사용을 감지하고 보고하는 기능. AEM as a Cloud Service에서 더 이상 지원되지 않는 4개의 API가 있습니다. 고객은 더 이상 이러한 API를 사용하지 않고 새로운 에셋 업로드 방법을 사용해야 합니다.

* 콘텐츠 조각 템플릿의 사용을 감지하는 기능. 콘텐츠 조각 템플릿은 더 이상 AEM as a Cloud Service에서 새 콘텐츠 조각 생성에 지원되지 않습니다. 고객은 콘텐츠 조각 템플릿을 대체할 콘텐츠 조각 모델을 생성해야 합니다.

* 저장소에 있는 에셋의 메타데이터 노드 아래에서 하위 항목이 100개를 초과하는 에셋을 감지하는 기능. 이러한 에셋으로 구성된 폴더를 로드할 때 성능을 개선하는 데 필요하지 않은 메타데이터 노드를 제거하는 것이 좋습니다.

* 사용된 데이터 저장소 유형을 감지하고 보고하는 기능.

* AEM Form Portal에 대한 패턴이 업데이트되었습니다.

### 버그 수정 {#bug-fixes-bpa}

* BPA가 고객 구성 요소에 대해서만 보고하는 대신 핵심 구성 요소에 대한 검색 결과를 보고했습니다. 이 문제가 해결되었습니다.
