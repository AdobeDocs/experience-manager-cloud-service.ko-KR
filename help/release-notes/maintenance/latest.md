---
title: ' [!DNL Adobe Experience Manager] as a Cloud Service의 최신 유지 관리 릴리스 정보입니다.'
description: ' [!DNL Adobe Experience Manager] as a Cloud Service의 최신 유지 관리 릴리스 정보입니다.'
source-git-commit: edb8949b532b80a55106e706a49e2ada68722a67
workflow-type: tm+mt
source-wordcount: '303'
ht-degree: 100%

---


# 유지 관리 릴리스 정보 {#maintenance-release-notes}

다음 섹션에서는 Experience Manager as a Cloud Service 최신 유지 관리 릴리스의 기술 릴리스 정보에 대해 간략히 소개합니다.

## 릴리스 11289 {#release-11289}

2023년 3월 7일에 릴리스된 유지 관리 릴리스 11289의 지속적인 개선 사항이 아래에 요약되어 있습니다. 이 유지 관리 릴리스는 이전 유지 관리 릴리스 10912의 업데이트입니다.

이 유지 관리 릴리스에 대한 기능 활성화는 전체 기능 세트를 제공합니다. 자세한 내용은 [최신 릴리스 정보](/help/release-notes/release-notes-cloud/release-notes-current.md)를 참조하십시오.

### 알려진 문제 {#known-issues}

CORS를 사용하는 경우 업그레이드하지 마십시오. 이 릴리스에서 GraphQL 콘텐츠 게재 기능에 영향을 미치는 문제가 확인되었습니다. GraphQL 지속 쿼리가 캐시되는 방식에 대한 기본 AEM Dispatcher 구성의 변경으로 인해, CORS 구성을 사용하는 고객의 경우 이러한 쿼리의 GraphQL 콘텐츠 게재가 중단될 수 있습니다. 이 문제는 다음 유지 관리 릴리스에서 해결될 예정입니다.

### 해결된 문제 {#fixed-issues}

#### Sites {#sites-issues}

- SITES-11584 주석이 있는 페이지에 대해 생성할 수 없는 Live Copy 관련 문제가 해결되었습니다.
- SITES-11683 상속이 부분적으로 손상된 MSM Live Copy가 비활성화되었습니다.

#### Assets {#assets-issues}

- ASSETS-20879 에셋 보고서 UI가 올바르게 작동하지 못하게 하고 생성된 보고서에서 잘못된 결과를 초래하는 회귀 문제가 해결되었습니다.
- ASSETS-21020 에셋 이동 후 이미지 프로필이 존재하지 않는 손상된 에셋 다운로드 관련 문제가 해결되었습니다.
- ASSETS-21023 API를 통한 액세스를 방해하는 Dynamic Media의 이미지 렌디션 관련 문제가 해결되었습니다.

#### Forms {#forms-issues}

- 없음

#### Platform {#platform-issues}

- GRANITE-44467 - 기존 노드를 업데이트할 때 특정 인스턴스에서 Filevault가 믹스인 유형 및 하위 노드를 유지하지 않아 가져오기가 실패하는 문제가 해결되었습니다.

### 임베드된 기술 {#embedded-tech}

| 기술 | 버전 | 링크 |
|---|---|---|
| AEM OAK | 1.44-T20221206170501-6d59064 | [Oak API 1.44.0 API](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.44.0/index.html) |
| AEM SLING API | 버전 2.27.0 | [Apache Sling API 2.27.0 API](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 버전 1.4.20-1.4.0 | [HTML 템플릿 언어 사양](https://github.com/adobe/htl-spec) |
| AEM 핵심 구성 요소 | 버전 2.21.2 | [AEM WCM 핵심 구성 요소](https://github.com/adobe/aem-core-wcm-components) |
