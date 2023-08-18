---
title: ' [!DNL Adobe Experience Manager] as a Cloud Service의 현재 유지 관리 릴리스 정보입니다.'
description: ' [!DNL Adobe Experience Manager] as a Cloud Service의 현재 유지 관리 릴리스 정보입니다.'
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
source-git-commit: cf8b5d8b11452268b2839053c1e05cc2ec107a91
workflow-type: tm+mt
source-wordcount: '222'
ht-degree: 63%

---

# 유지 관리 릴리스 정보 {#maintenance-release-notes}

다음 섹션에서는 Experience Manager as a Cloud Service 현재 유지 관리 릴리스의 기술 릴리스 정보에 대해 간략히 소개합니다.

## 릴리스 13173 {#release-13173}

다음은 2023년 8월 18일에 공개적으로 릴리스된 유지 보수 릴리스 13173에 대한 지속적인 개선 사항을 요약합니다. 이 유지 관리 릴리스는 이전 유지 관리 릴리스 13099의 업데이트입니다.

이 유지 관리 릴리스(2023.8.0)에 대한 기능 활성화는 전체 기능 세트를 제공합니다. 자세한 내용은 [Experience Manager 릴리스 로드맵](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap.html)을 참조하십시오.

### 향상된 기능 {#enhancements-13173}

없음.

### 해결된 문제 {#fixed-issues-13173}

- SITES-15463: 사이트 템플릿 - 템플릿을 게시할 수 없습니다.

### 알려진 문제 {#known-issues-13173}

- SITES-15359: 콘텐츠 조각 - 변형 이름 패턴이 이 있는 변형과 올바르게 일치하지 않음 ```'_'``` 리소스 이름.
- FORMS-10444: 적응형 Forms 템플릿 - 템플릿을 게시할 수 없습니다(해결 방법: 배포 콘솔 사용).
- CQ-4354191: 워크플로 - nt:unstructured 노드에 있는 복제 메타데이터로 인해 사용자 지정 런처가 여러 번 트리거될 수 있습니다(해결 방법: 겹치지 않도록 복제 메타데이터 속성을 제외하도록 런처를 업데이트).

### 임베드된 기술 {#embedded-tech-13173}

| 기술 | 버전 | 링크 |
|---|---|---|
| AEM OAK | 1.52-T20230629133256-25c01b8 | [Oak API 1.52.0 API](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.52.0/index.html) |
| AEM SLING API | 버전 2.27.2 | [Apache Sling API 2.27.2 API](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 버전 1.4.20-1.4.0 | [HTML 템플릿 언어 사양](https://github.com/adobe/htl-spec) |
| AEM 핵심 구성 요소 | 버전 2.23.2 | [AEM WCM 핵심 구성 요소](https://github.com/adobe/aem-core-wcm-components) |
