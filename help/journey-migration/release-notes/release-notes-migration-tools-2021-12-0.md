---
title: AEM as a Cloud Service 릴리스 2021.12.0의 마이그레이션 도구 릴리스 정보
description: AEM as a Cloud Service 릴리스 2021.12.0의 마이그레이션 도구 릴리스 정보
feature: Release Information
exl-id: 4155e1c0-cd40-4cbc-9d6c-b106d68a2db5
role: Admin
source-git-commit: 6719e0bcaa175081faa8ddf6803314bc478099d7
workflow-type: tm+mt
source-wordcount: '251'
ht-degree: 38%

---

# AEM as a Cloud Service 릴리스 2021.12.0의 마이그레이션 도구 릴리스 정보 {#release-notes}

이 페이지에서는 AEM as a Cloud Service 2021.12.0의 마이그레이션 도구 릴리스 정보에 대해 간략히 설명합니다.

>[!NOTE]
>
>최신 릴리스 노트는 [Adobe Experience Manager as a Cloud Service 최신 릴리스 노트](/help/release-notes/release-notes-cloud/release-notes-current.md)를 참조하십시오.

## Best Practices Analyzer {#bpa-release}

### 릴리스 날짜 {#release-date-bpa}

모범 사례 분석기 v2.1.22의 릴리스 날짜는 2021년 12월 1일입니다.

### 새로운 기능 {#what-is-new-bpa}

* 사용된 ACS 커먼즈 버전 감지 및 보고 기능.
* 그룹 내 사용자 및 하위 그룹 수 감지 및 보고 기능.
* 16MB를 초과하는 MongoDB의 노드 속성 값 감지 및 보고 기능.

### 버그 수정 {#bug-fixes-bpa}

* Foundation 구성 요소의 감지가 거짓 음성을 줄이도록 개선되었습니다.
* AEM Forms 고객의 경우 AEM as a Cloud Service에서 사용할 수 없는 `EMAIL_PDF_SUBMIT_ACTION` 관련 BPA 메시징이 수정되었습니다.


## 콘텐츠 전송 도구 {#ctt-release}

### 릴리스 날짜 {#release-date-ctt}

컨텐츠 전송 도구 v1.7.10의 릴리스 날짜는 2021년 12월 8일입니다.

### 새로운 기능 {#what-is-new-ctt}

* 사용자가 수집 중에 [사전 복사](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/handling-large-content-repositories.html?lang=ko)를 사용하지 않도록 설정할 수 있도록 콘텐츠 전송 도구의 수집 단계에 추가된 토글 수집 속도를 최적화하려면 작은 마이그레이션 세트에 대해 수집 중 사전 복사를 비활성화하거나 마지막 수집 이후 몇 개의 블롭만 추가된 경우 비활성화해야 합니다.
* 사용자 매핑은 한 번에 2000명의 사용자를 확보할 수 있는 향상된 사용자 관리 API를 사용하도록 업데이트되어 성능이 크게 향상되었습니다.
