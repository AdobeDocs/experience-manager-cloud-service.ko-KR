---
title: ' [!DNL Adobe Experience Manager] as a Cloud Service의 현재 유지 관리 릴리스 정보입니다.'
description: ' [!DNL Adobe Experience Manager] as a Cloud Service의 현재 유지 관리 릴리스 정보입니다.'
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: 30b5d5838087a35a457939cdbaa13c5735df144e
workflow-type: tm+mt
source-wordcount: '375'
ht-degree: 40%

---


# 유지 관리 릴리스 정보 {#maintenance-release-notes}

다음 섹션에서는 Experience Manager as a Cloud Service의 현재 유지 관리 릴리스에 대한 기술 릴리스 정보를 간략히 소개합니다.

## 릴리스 19823 {#19823}

2025년 3월 4일에 공개적으로 릴리스된 유지 보수 릴리스 19823에 대한 지속적인 개선 사항을 요약하면 다음과 같습니다. 이전 유지 관리 릴리스는 릴리스 19687.

2025.3.0 기능 활성화는 이 유지 관리 릴리스에 대한 전체 기능 세트를 제공합니다. 자세한 내용은 [Experience Manager 릴리스 로드맵](https://experienceleague.adobe.com/ko/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap)을 참조하십시오.

### 개선 사항 {#enhancements-19823}

* ASSETS-46491: 에셋 처리 상태 변경에 대한 OSGI 이벤트 핸들러입니다.
* ASSETS-45613: 에셋이 삭제되거나 이동될 때 게시 취소 이벤트를 보냅니다.
* ASSETS-45131: Content Hub에서 사용자 지정 태그 속성을 지원합니다.

### 해결된 문제 {#fixed-issues-19823}

* ASSETS-20433: 암호로 보호된 PDF와 관련된 Dynamic Media 수집 문제
* ASSETS-24675: 견본 전용 이미지 프로필에 대해 이미지 처리 옵션이 표시되지 않습니다.
* ASSETS-41257: 에셋 버전 비교가 잘못된 종횡비로 에셋을 렌더링합니다. 자산 버전이 타임라인에 잘못된 순서로 표시됩니다.
* ASSETS-44894: Assets 보기 책갈피를 클릭할 수 없습니다.
* ASSETS-45015: 스마트 자르기 에셋 핸들을 찾을 수 없는 경우 스마트 자르기 너비와 높이가 0으로 설정됩니다.
* ASSETS-45192: 펄스 요청 빈도를 줄입니다.
* ASSETS-45724: 업로드 작업이 할당되지 않은 경우 DM 업로드를 다시 시도해야 합니다.
* ASSETS-46425: Adobe Stock 통합 검색 문제.
* ASSETS-27400: 폴더 미리 보기 생성기가 원본 열기를 시도할 수 있습니다.
* CQ-4358722: Java 11 및 Java 17에서 다양한 로케일 코드를 처리합니다.
* SITES-29369: 에셋 활성화/비활성화 시 트리거된 페이지 게시/게시 취소 이벤트.
* SITES-24074: 통합 쉘에서 키보드 접근성을 수정합니다.
* SITES-28058: Assets 폴더 제목이 Live Copy로 이월되지 않습니다.

### 알려진 문제 {#known-issues-19823}

없음.

### 사용 중단된 기능 및 API {#deprecated-19823}

AEM as a Cloud Service에서 더 이상 사용되지 않는 기능과 API는 [사용 중단된 기능 및 API](/help/release-notes/deprecated-removed-features.md) 문서에 자세히 설명되어 있습니다.

### 보안 수정 {#security-19823}

AEM as a Cloud Service는 플랫폼의 보안 및 성능 최적화에 중점을 둡니다. 이 유지 관리 릴리스는 6개의 식별된 취약점을 해결하여 강력한 시스템 보호에 대한 약속을 강화합니다.

### 임베드된 기술 {#embedded-tech-19823}

| 기술 | 버전 | 링크 |
|---|---|---|
| AEM Oak | 1.76.0 | [Oak API 1.76.0 API](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.76.0/index.html) |
| AEM SLING API | 2.27.6 | [Apache Sling API 2.27.6 API](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 1.4.26-1.4.0 | [HTML 템플릿 언어 사양](https://github.com/adobe/htl-spec) |
| AEM 핵심 구성 요소 | 2.27.0 | [AEM WCM 핵심 구성 요소](https://github.com/adobe/aem-core-wcm-components) |
