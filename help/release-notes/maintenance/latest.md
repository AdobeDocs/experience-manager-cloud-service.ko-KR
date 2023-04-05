---
title: ' [!DNL Adobe Experience Manager] as a Cloud Service의 현재 유지 관리 릴리스 정보입니다.'
description: ' [!DNL Adobe Experience Manager] as a Cloud Service의 현재 유지 관리 릴리스 정보입니다.'
source-git-commit: c56ed1878b89a1f31c5b7b44696511d51cfa5351
workflow-type: tm+mt
source-wordcount: '342'
ht-degree: 90%

---


# 유지 관리 릴리스 정보 {#maintenance-release-notes}

다음 섹션에서는 Experience Manager as a Cloud Service 현재 유지 관리 릴리스의 기술 릴리스 정보에 대해 간략히 소개합니다.

## 릴리스 11382 {#release-11382}

2023년 3월 28일에 릴리스된 유지 관리 릴리스 11382의 지속적인 개선 사항이 아래에 요약되어 있습니다. 이 유지 관리 릴리스는 이전 유지 관리 릴리스 11289의 업데이트입니다.

이 유지 관리 릴리스에 대한 기능 활성화는 전체 기능 세트를 제공합니다. 자세한 내용은 [최신 릴리스 정보](/help/release-notes/release-notes-cloud/release-notes-current.md)를 참조하십시오.

### 알려진 문제 {#known-issues-11382}

- SITES-12573 - 필터 내에 변수를 사용하는 GraphQL 쿼리는 하나의 변수를 지정하지 않으면 실패합니다. AEM as a Cloud Service에서 GraphQL을 사용하려면 이 릴리스를 업데이트하지 마십시오.

### 해결된 문제 {#fixed-issues-11382}

- ASSETS-21023 - 고객이 API를 통해 이러한 렌디션에 액세스하려고 할 때 모든 AEM 환경의 게시자 인스턴스에서 Null 포인터 예외가 발생할 수 있는 스마트 자르기 렌디션을 해결했습니다.
- SKYOPS-49280 - RDE를 사용하여 구성 또는 번들 업데이트를 게시에 설치할 때 게시 Dispatcher 캐시가 무효화되지 않아 결과가 표시되지 않을 수 있음

#### Sites {#sites-issues-11382}

- SITES-7796 - 콘텐츠 작성자가 대상으로 내보낼 때 마스터 콘텐츠 조각 및 해당 변형을 게시할 수 있는 기능
- SITES-97 - GraphQL: 페이지 매김, 정렬 및 하이브리드 필터링

>[!NOTE]
>
> SITES-97에서는 예기치 않은 동작을 유발할 수 있는 GraphQL 구현이 일부 개선되었습니다. 자세한 내용은 [Null 값 처리와 관련된 AEM GraphQL 변경 사항](https://experienceleague.adobe.com/docs/experience-cloud-kcs/kbarticles/KA-21792.html)을 참조하십시오.

#### Assets {#assets-issues-11382}

- ASSETS-20076 - 현재 이미지 워터마킹 지원과 일치하는 비디오 워터마킹 지원 추가
- ASSETS-21428 - CSS 변경에 대한 제외 사항 추가

#### Forms {#forms-issues-11382}

- CQ-4351502 - Sites에서 읽기 액세스를 허용하도록 서비스 사용자 매핑 업데이트

#### Platform {#platform-issues-11382}

- SITES-11040 - Dispatcher에서 GraphQL 지속 쿼리 캐싱의 조건부 활성화

### 임베드된 기술 {#embedded-tech-11382}

| 기술 | 버전 | 링크 |
|---|---|---|
| AEM OAK | 1.44-T20221206170501-6d59064 | [Oak API 1.44.0 API](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.44.0/index.html) |
| AEM SLING API | 버전 2.27.0 | [Apache Sling API 2.27.0 API](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 버전 1.4.20-1.4.0 | [HTML 템플릿 언어 사양](https://github.com/adobe/htl-spec) |
| AEM 핵심 구성 요소 | 버전 2.21.2 | [AEM WCM 핵심 구성 요소](https://github.com/adobe/aem-core-wcm-components) |
