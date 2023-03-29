---
title: 의 현재 유지 관리 릴리스 노트 [!DNL Adobe Experience Manager] as a Cloud Service.
description: 의 현재 유지 관리 릴리스 노트 [!DNL Adobe Experience Manager] as a Cloud Service.
source-git-commit: 7e66c9f26211bd92119c74f311f3e9b3195a8d98
workflow-type: tm+mt
source-wordcount: '265'
ht-degree: 36%

---


# 유지 관리 릴리스 정보 {#maintenance-release-notes}

다음 섹션에서는 Experience Manager as a Cloud Service의 현재 유지 관리 릴리스에 대한 기술 릴리스 노트를 간략하게 설명합니다.

## 릴리스 11382 {#release-11382}

2023년 3월 28일에 릴리스된 유지 관리 릴리스 11382에 대한 지속적인 개선 사항이 아래에 요약되어 있습니다. 이 유지 관리 릴리스는 이전 유지 관리 릴리스 11289의 업데이트입니다.

이 유지 관리 릴리스에 대한 기능 활성화는 전체 기능 세트를 제공합니다. 자세한 내용은 [최신 릴리스 정보](/help/release-notes/release-notes-cloud/release-notes-current.md)를 참조하십시오.

### 해결된 문제 {#fixed-issues}

- ASSETS-21023 - API를 통해 이러한 변환에 액세스하려고 할 때 고객이 모든 AEM 환경의 게시자 인스턴스에서 Null 포인터 예외를 관찰할 수 있는 스마트 자르기 렌디션이 수정되었습니다.
- SKYOPS-49280 - RDE를 사용하여 구성 또는 번들 업데이트를 게시에 설치하는 경우 게시 디스패처 캐시가 무효화되지 않으므로 결과를 확인할 수 없습니다

#### Sites {#sites-issues}

- SITES-7796 - target으로 내보낼 때 컨텐츠 작성자가 기본 컨텐츠 조각 및 해당 변형을 게시할 수 있는 기능입니다

#### Assets {#assets-issues}

- ASSETS-20076 - 현재 이미지 워터마크 지원과 일치하는 비디오 워터마킹을 위한 지원을 추가합니다
- ASSETS-21428 - CSS 변경 사항에 대한 제외가 추가되었습니다.

#### Forms {#forms-issues}

- CQ-4351502 - 사이트에서 읽기 액세스를 허용하도록 서비스 사용자 매핑 업데이트

#### Platform {#platform-issues}

- SITES-11040 - Dispatcher에서 GraphQL 지속적인 쿼리 캐싱의 조건부 지원

### 임베드된 기술 {#embedded-tech}

| 기술 | 버전 | 링크 |
|---|---|---|
| AEM OAK | 1.44-T20221206170501-6d59064 | [Oak API 1.44.0 API](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.44.0/index.html) |
| AEM SLING API | 버전 2.27.0 | [Apache Sling API 2.27.0 API](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 버전 1.4.20-1.4.0 | [HTML 템플릿 언어 사양](https://github.com/adobe/htl-spec) |
| AEM 핵심 구성 요소 | 버전 2.21.2 | [AEM WCM 핵심 구성 요소](https://github.com/adobe/aem-core-wcm-components) |
