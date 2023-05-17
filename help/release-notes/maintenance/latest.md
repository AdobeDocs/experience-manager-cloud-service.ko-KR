---
title: ' [!DNL Adobe Experience Manager] as a Cloud Service의 현재 유지 관리 릴리스 정보입니다.'
description: ' [!DNL Adobe Experience Manager] as a Cloud Service의 현재 유지 관리 릴리스 정보입니다.'
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
source-git-commit: 4353f2a9f6cd649a4377adb9891e0873a51d6ab2
workflow-type: tm+mt
source-wordcount: '240'
ht-degree: 85%

---

# 유지 관리 릴리스 정보 {#maintenance-release-notes}

다음 섹션에서는 Experience Manager as a Cloud Service 현재 유지 관리 릴리스의 기술 릴리스 정보에 대해 간략히 소개합니다.

## 릴리스 11873 {#release-11873}

2023년 5월 3일에 릴리스된 유지 관리 릴리스 11873의 지속적인 개선 사항이 아래에 요약되어 있습니다. 이 유지 관리 릴리스는 이전 유지 관리 릴리스 11835의 업데이트입니다.

이 유지 관리 릴리스에 대한 기능 활성화는 전체 기능 세트를 제공합니다. 자세한 내용은 [최신 릴리스 정보](/help/release-notes/release-notes-cloud/release-notes-current.md)를 참조하십시오.

### 향상된 기능 {#enhancements}

- SITES-1200 - 태그 기반 필터링을 통한 검색 API 개선 사항
- GRANITE-42939 - Oauth 서버 코드에 사용 중단 주석 및 경고 추가

### 알려진 문제 {#known-issues-11873}

- SITES-13253 - 코어 구성 요소 v2.22.6의 RecursionTooDeepException
- SITES-13256 - 특수 URL로 구성된 코어 WCM Teaser가 페이지 렌더링을 중단합니다
- GRANITE-45462 - 메시징 클라이언트 다중 영역 구성
- GRANITE-45562 - 404 대신 200을 반환하는 이미지 조합 문제

### 해결된 문제 {#fixed-issues-11873}

- SKYSI-19884/SKYOPS-53745 - PublishPageRenderingErrorsHigh 문제 해결
- GRANITE-4388 - Mongo에서 대량의 DAM 자산 쓰기 후 처리량 저하 해결
- SITES-11922 - 미리보기에서 게시 취소 시 동기화 상태가 제거되지 않는 문제 해결
- ASSETS-21648 - 자산 관련 기능의 권한 문제 해결

### 임베드된 기술 {#embedded-tech-11873}

| 기술 | 버전 | 링크 |
|---|---|---|
| AEM OAK | 1.50-T20230405052634-f9df4aa | [Oak API 1.50.0 API](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.50.0/index.html) |
| AEM SLING API | 버전 2.27.0 | [Apache Sling API 2.27.0 API](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 버전 1.4.20-1.4.0 | [HTML 템플릿 언어 사양](https://github.com/adobe/htl-spec) |
| AEM 핵심 구성 요소 | 버전 2.22.6 | [AEM WCM 핵심 구성 요소](https://github.com/adobe/aem-core-wcm-components) |
