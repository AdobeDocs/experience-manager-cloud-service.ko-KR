---
title: AEM as a Cloud Service 릴리스 2023.03.0의 마이그레이션 도구 릴리스 정보
description: AEM as a Cloud Service 릴리스 2022.03.0의 마이그레이션 도구 릴리스 정보
feature: Release Information
exl-id: 2f787321-f156-480d-bbe8-1a6d04f110c5
source-git-commit: 5815dacd2806cc7886aa0c7c5c9fd329306b3e1b
workflow-type: tm+mt
source-wordcount: '150'
ht-degree: 15%

---

# AEM as a Cloud Service 릴리스 2023.03.0의 마이그레이션 도구 릴리스 정보 {#release-notes}

이 페이지에서는 AEM as a Cloud Service 2022.03.0의 마이그레이션 도구 릴리스 정보에 대해 간략히 설명합니다.

## Best Practices Analyzer {#bpa-release}

### 릴리스 날짜 {#release-date-bpa}

Best Practices Analyzer v2.1.40의 릴리스 날짜는 2023년 3월 03일입니다.

### 새로운 기능 {#what-is-new-bpa}

* 이제 BPA는 충돌하는 노드 - 동일한 노드를 감지하고 보고할 수 있습니다 `jcr:uuid`. 이러한 결과는 컨텐츠를 AEM as a Cloud Service으로 이동할 때 컨텐츠 수집 실패를 초래할 수 있으므로 중대하다고 플래그가 지정됩니다.
* 이제 BPA가 이벤트 리스너의 사용을 감지하고 보고할 수 있습니다. AEM as a Cloud Service으로 이동할 때 이러한 유형의 이벤트 처리 메커니즘을 슬링 작업으로 리팩터링하는 것이 좋습니다.

### 버그 수정 {#bug-fixes-bpa}

* BPA가 다음에 대한 긍정 오류(false positive)를 보고했습니다. `grouprendercondition`. 이 문제가 해결되었습니다.