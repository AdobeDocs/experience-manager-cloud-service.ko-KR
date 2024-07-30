---
title: ' [!DNL Adobe Experience Manager] as a Cloud Service의 현재 유지 관리 릴리스 정보입니다.'
description: ' [!DNL Adobe Experience Manager] as a Cloud Service의 현재 유지 관리 릴리스 정보입니다.'
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: dc7150c6ce971aa6f89fa24f7ca387cbb28db1f2
workflow-type: tm+mt
source-wordcount: '319'
ht-degree: 51%

---


# 유지 관리 릴리스 정보 {#maintenance-release-notes}

다음 섹션에서는 Experience Manager as a Cloud Service 현재 유지 관리 릴리스의 기술 릴리스 정보에 대해 간략히 소개합니다.

## 릴리스 17258 {#release-17258}

다음은 2024년 7월 30일에 공개적으로 릴리스된 유지 보수 릴리스 17258에 대한 지속적인 개선 사항을 요약했습니다. 이전 유지 관리 릴리스는 릴리스 17098.

2024.8.0 기능 활성화는 이 유지 관리 릴리스에 대한 전체 기능 세트를 제공합니다. 자세한 내용은 [Experience Manager 릴리스 로드맵](https://experienceleague.adobe.com/ko/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap)을 참조하십시오.

### 개선 사항 {#enhancements-17258}

* ASSETS-31445 - 초기 Dynamic Media 템플릿 기능
* ASSETS-40399 - 업데이트된 DM 자동 트랜스크립션 큐 설정
* ASSETS-40873 - OSGI 구성을 통해 메타데이터 내보내기 최대 행을 설정할 수 있음

### 해결된 문제 {#fixed-issues-17258}

* ASSETS-30613 - 에셋 바꾸기가 새 게재 계층에서 에셋을 삭제하고 추가하지 않음
* ASSETS-31882 - 작성자의 스트리밍 매니페스트 파일에 액세스할 수 없습니다.
* ASSETS-39598 - 일괄 가져오기를 통해 S3 백엔드에서 이름에 특수 문자가 있는 자산을 삭제할 수 없음
* CNTBF-209 - 역류 작업 취소 개선
* SCRNS-3762 - 브라우저에서 채널을 미리 볼 때 시퀀스 채널의 playerLogger를 개선하여 콘솔에 로그를 배치합니다.
* SCRNS-4455 - 채널 컨텐츠 공급자에서 관리자가 아닌 사용자를 위한 &quot;게시 관리&quot; 및 &quot;빠른 Publish&quot; 버튼 누락
* SITES-22940 - 콘텐츠 조각을 워크플로 페이로드로 볼 수 없음

### 알려진 문제 {#known-issues-17258}

없음

### 변경 사항 공지 {#change-notice-17258}

* 2024년 9월부터 AEM as a Cloud Service는 Sling Model Exporter 프레임워크를 통해 Resource Resolver의 직렬화를 비활성화합니다. 자세한 내용은 [설명서](/help/implementing/developing/hybrid/disallow-the-serialization-of-resourceresolvers-via-sling-model-exporter.md)를 참조하십시오.

### 사용 중단된 기능 및 API {#deprecated-17258}

AEM as a Cloud Service에서 더 이상 사용되지 않는 기능과 API는 [사용 중단된 기능 및 API](/help/release-notes/deprecated-removed-features.md) 문서에 자세히 설명되어 있습니다.

### 임베드된 기술 {#embedded-tech-17258}

| 기술 | 버전 | 링크 |
|---|---|---|
| AEM Oak | 1.66.0 | [Oak API 1.66.0 API](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.66.0/index.html) |
| AEM SLING API | 2.27.2 | [Apache Sling API 2.27.2 API](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 1.4.24-1.4.0 | [HTML 템플릿 언어 사양](https://github.com/adobe/htl-spec) |
| AEM 핵심 구성 요소 | 2.25.4 | [AEM WCM 핵심 구성 요소](https://github.com/adobe/aem-core-wcm-components) |
