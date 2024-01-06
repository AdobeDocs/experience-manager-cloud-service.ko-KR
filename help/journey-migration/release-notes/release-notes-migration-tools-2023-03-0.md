---
title: AEM as a Cloud Service 릴리스 2023.03.0의 마이그레이션 도구 릴리스 정보
description: AEM as a Cloud Service 릴리스 2023.03.0의 마이그레이션 도구 릴리스 정보
feature: Release Information
exl-id: cdc57cca-e10a-4b0d-b803-910ccc9350a6
source-git-commit: ecf4c06fd290d250c14386b3135250633b26c910
workflow-type: tm+mt
source-wordcount: '301'
ht-degree: 7%

---

# AEM as a Cloud Service 릴리스 2023.03.0의 마이그레이션 도구 릴리스 정보 {#release-notes}

이 페이지에서는 AEM as a Cloud Service 2023.03.0의 마이그레이션 도구 릴리스 정보에 대해 간략히 설명합니다.

## Best Practices Analyzer {#bpa-release}

### 릴리스 날짜 {#release-date-bpa}

Best Practices Analyzer v2.1.40의 릴리스 날짜는 2023년 3월 3일입니다.

### 새로운 기능 {#what-is-new-bpa}

* 이제 BPA는 충돌하는 노드 - 동일한 노드를 감지하고 보고할 수 있습니다 `jcr:uuid`. 이러한 결과는 컨텐츠를 AEM as a Cloud Service으로 이동할 때 컨텐츠 수집 실패를 초래할 수 있으므로 중대하다고 플래그가 지정됩니다.
* 이제 BPA가 이벤트 리스너의 사용을 감지하고 보고할 수 있습니다. AEM as a Cloud Service으로 이동할 때 이러한 유형의 이벤트 처리 메커니즘을 슬링 작업으로 리팩터링하는 것이 좋습니다.

### 버그 수정 {#bug-fixes-bpa}

* BPA가 다음에 대한 긍정 오류(false positive)를 보고했습니다. `grouprendercondition`. 이 문제가 해결되었습니다.

## 콘텐츠 전송 도구 {#ctt-release}

### 릴리스 날짜 {#release-date-ctt}

컨텐츠 전송 도구 v2.0.16의 릴리스 날짜는 2023년 3월 8일입니다.

### 새로운 기능 {#what-is-new-ctt}

* 사용자 매핑이 간소화되었으며 컨텐츠 추출 단계에 통합되었습니다. 설정이 필요하지 않으며 기본적으로 사용자가 콘텐츠 추출을 시작할 때 사용자 매핑이 자동으로 수행됩니다. 필요한 경우 사용자는 사용자 매핑을 비활성화할 수 있습니다. 자세히 알아보기 [여기.](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/user-mapping-and-migration.html#user-mapping-detail)
* 다음을 사용하는 사전 복사 단계: [AzCopy](https://learn.microsoft.com/en-us/azure/storage/common/storage-use-azcopy-v10) 는 컨텐츠 전송 도구와 통합되어 컨텐츠 추출 속도를 크게 향상했습니다. 이 버전의 CTT가 설치되면 사전 복사가 자동으로 구성 및 설치됩니다. 기본적으로 추출이 시작되면 200GB를 초과하는 마이그레이션 세트에 대해 사전 복사가 자동으로 실행됩니다. 필요한 경우 사용자는 비활성화할 수 있습니다. 자세히 알아보기 [여기.](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/handling-large-content-repositories.html)
* 이제 Windows 서버에서 CTT를 사용할 수 있습니다.

### 버그 수정 {#bug-fixes-ctt}

* 콘텐츠 추출 복원력을 개선하기 위해 여러 버그 수정.
