---
title: ' [!DNL Adobe Experience Manager] as a Cloud Service의 현재 유지 관리 릴리스 정보입니다.'
description: ' [!DNL Adobe Experience Manager] as a Cloud Service의 현재 유지 관리 릴리스 정보입니다.'
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
source-git-commit: beb6ac3dbb036559510e6a2e2700b28c433ef98d
workflow-type: tm+mt
source-wordcount: '355'
ht-degree: 38%

---

# 유지 관리 릴리스 정보 {#maintenance-release-notes}

다음 섹션에서는 Experience Manager as a Cloud Service 현재 유지 관리 릴리스의 기술 릴리스 정보에 대해 간략히 소개합니다.

## 릴리스 12255 {#release-12255}

다음은 2023년 6월 13일에 공개적으로 릴리스된 유지 보수 릴리스 12255에 대한 지속적인 개선 사항을 요약했습니다. 이 유지 관리 릴리스는 이전 유지 관리 릴리스 12142의 업데이트입니다.

이 유지 관리 릴리스에 대한 기능 활성화는 전체 기능 세트를 제공합니다. 자세한 내용은 [최신 릴리스 정보](/help/release-notes/release-notes-cloud/release-notes-current.md)를 참조하십시오.

### 향상된 기능 {#enhancements-12255}

없음.

### 알려진 문제 {#known-issues-12255}

- ASSETS-25729 - 전환기 보기 메뉴가 잘림
- ASSETS-25728 - 검색 보기에서 자산 재처리 옵션을 사용할 수 없음

### 해결된 문제 {#fixed-issues-12255}

- 다양한 접근성 관련 업데이트
- ASSETS-15116 - 에셋 검색 보기에서 사용할 수 있는 &quot;위치로 이동&quot; 옵션
- ASSETS-17453 - (Dynamic Media) 비디오에 대한 사용자 지정 썸네일을 선택할 수 없습니다.
- ASSETS-19279 - 대용량 파일을 위한 자산 다운로드 아카이브
- ASSETS-19544 - 자산 업데이트에 대해 사용자가 마지막으로 수정함
- ASSETS-20146 - (Touch UI) 유효성 검사 오류로 인해 자산 다운로드 보고서 실패 보고서가 보고서의 목록 페이지 맨 위에 항상 표시됩니다
- ASSETS-21056 - 쓰기를 최소화하기 위해 에셋 참조 성능 최적화
- ASSETS-21909 - vtt가 다운로드되지 않을 때 스마트 자르기 비디오를 볼 수 없음
- ASSETS-22261 - Linkshare 다운로드 폴더 구조가 Assets UI 다운로드와 일치하지 않음
- ASSETS-22550 - 이제 검색 필터 패널이 기본적으로 열립니다
- ASSETS-22920 - Brand Portal에서 폴더 게시를 취소하면 내의 자산이 게시 취소됨으로 표시되지 않습니다
- ASSETS-22922 - Dynamic Media 구성 요소에 비활성화된 뷰어 사전 설정이 표시됨
- ASSETS-23461 - 에셋 검색 보기에서 Brand Portal 빠른 게시
- ASSETS-23466 - InDesign Server에 액세스할 수 없는 링크 처리로 공백이 포함된 AAL 링크를 해결할 수 없음
- ASSETS-23469 - 기본 에셋 필터가 사용자 지정 필터와 충돌함
- ASSETS-23981 - 컬렉션 링크에서 작동하지 않는 제목의 정렬 기능
- ASSETS-24723 - 게시된 에셋이 사용자 개입 없이 다시 처리되었습니다.
- GRANITE-45385 - 워크플로우 대신 sling 작업을 사용하도록 트리 활성화 마이그레이션

### 임베드된 기술 {#embedded-tech-12255}

| 기술 | 버전 | 링크 |
|---|---|---|
| AEM OAK | 1.50-T20230405052634-f9df4aa | [Oak API 1.50.0 API](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.50.0/index.html) |
| AEM SLING API | 버전 2.27.0 | [Apache Sling API 2.27.0 API](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 버전 1.4.20-1.4.0 | [HTML 템플릿 언어 사양](https://github.com/adobe/htl-spec) |
| AEM 핵심 구성 요소 | 버전 2.23.0 | [AEM WCM 핵심 구성 요소](https://github.com/adobe/aem-core-wcm-components) |
