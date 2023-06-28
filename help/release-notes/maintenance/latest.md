---
title: ' [!DNL Adobe Experience Manager] as a Cloud Service의 현재 유지 관리 릴리스 정보입니다.'
description: ' [!DNL Adobe Experience Manager] as a Cloud Service의 현재 유지 관리 릴리스 정보입니다.'
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
source-git-commit: fd0b8ca281f35a92876f3c31baa4e17884f23948
workflow-type: tm+mt
source-wordcount: '297'
ht-degree: 47%

---

# 유지 관리 릴리스 정보 {#maintenance-release-notes}

다음 섹션에서는 Experience Manager as a Cloud Service 현재 유지 관리 릴리스의 기술 릴리스 정보에 대해 간략히 소개합니다.

## 릴리스 12441 {#release-12441}

2023년 6월 27일에 릴리스된 유지 관리 릴리스 12441의 지속적인 개선 사항이 아래에 요약되어 있습니다. 이 유지 관리 릴리스는 이전 유지 관리 릴리스 12255의 업데이트입니다.

2023.7.0 기능 활성화는 이 유지 관리 릴리스에 대한 전체 기능 세트를 제공합니다. 다음을 참조하십시오. [Experience Manager 릴리스 로드맵](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap.html) 추가 정보.

### 향상된 기능 {#enhancements-12441}

- SITES-8769: ResponsiveGrid에서 StyleImpl 호출 개선

### 해결된 문제 {#fixed-issues-12441}

- 접근성 관련된 다양한 업데이트
- SITES-12688: 페이지 편집기: 논리 연산자 또는 에셋 파인더 검색에서 제대로 작동하지 않음
- SITES-4951: 페이지 편집기: 페이지 편집기의 태그 검색에서 하위 태그를 찾을 수 없음
- SITES-12465: 경험 조각: 경험 조각 구성 요소 대화 상자에서 화살표 키가 작동하지 않음
- SITES-12893: 경험 조각: 경험 조각에 대한 순환 참조 유효성 검사 적용
- SITES-12715: Experience Fragments: Experience Fragments 폴더에 적용된 클라우드 서비스 구성이 지속되지 않음
- SITES-13097: 경험 조각: 경험 조각을 번역 프로젝트에 추가할 수 없음
- SITES-13165: GraphQL: null 값 필터링을 위한 기본 동작 복원
- SITES-12577: 링크 검사기: 변환기가 링크를 간헐적으로 다시 쓰지 않음
- SITES-13559: MSM: 구성 요소를 롤아웃할 때 &quot;수정할 수 없음&quot; 예외가 발생합니다.
- SITES-11757: MSM: 상위에서 롤아웃 구성 상속이 하위 페이지에 대해 다시 반환되지 않음
- SITES-14073: 사이트 관리자: 내보낼 속성이 없음을 선택하면 CSV 보고서가 500으로 실패합니다

### 알려진 문제 {#known-issues-12441}

없음.

### 임베드된 기술 {#embedded-tech-12441}

| 기술 | 버전 | 링크 |
|---|---|---|
| AEM OAK | 1.50-T20230405052634-f9df4aa | [Oak API 1.50.0 API](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.50.0/index.html) |
| AEM SLING API | 버전 2.27.0 | [Apache Sling API 2.27.0 API](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 버전 1.4.20-1.4.0 | [HTML 템플릿 언어 사양](https://github.com/adobe/htl-spec) |
| AEM 핵심 구성 요소 | 버전 2.23.0 | [AEM WCM 핵심 구성 요소](https://github.com/adobe/aem-core-wcm-components) |
