---
title: ' [!DNL Adobe Experience Manager] as a Cloud Service의 현재 유지 관리 릴리스 정보입니다.'
description: ' [!DNL Adobe Experience Manager] as a Cloud Service의 현재 유지 관리 릴리스 정보입니다.'
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
source-git-commit: 0dab7428d8ae5ec4c11a88ff310fad649a365868
workflow-type: tm+mt
source-wordcount: '511'
ht-degree: 24%

---

# 유지 관리 릴리스 정보 {#maintenance-release-notes}

다음 섹션에서는 Experience Manager as a Cloud Service 현재 유지 관리 릴리스의 기술 릴리스 정보에 대해 간략히 소개합니다.

## 릴리스 13665 {#release-13665}

다음은 2023년 9월 27일에 공개적으로 릴리스된 유지 보수 릴리스 13665에 대한 지속적인 개선 사항을 요약한 것입니다. 이 유지 관리 릴리스에서는 릴리스 13420를 대체합니다.

2023.10.0 기능 활성화는 이 유지 관리 릴리스에 대한 전체 기능 세트를 제공합니다. 자세한 내용은 [Experience Manager 릴리스 로드맵](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap.html)을 참조하십시오.

### 개선 사항 {#enhancements-13665}

* 콘텐츠 조각 API의 다양한 개선 사항.
* ASSETS-26713: 에셋 대시보드: 이제 터치 UI에서 새 경험 UI 대시보드에 연결할 수 있습니다.
* SITES-11206: 콘텐츠 조각: 콘텐츠 조각에 대한 검색 API.
* SITES-11262: 콘텐츠 조각: 새 콘텐츠 조각 편집기로 전환하는 버튼입니다.
* SITES-15447: 핵심 구성 요소: 버전 2.23.4 릴리스.

### 해결된 문제 {#fixed-issues-13665}

* 다양한 번역 관련 업데이트.
* CQ-4354428: 워크플로우: 받은 편지함에서 작업을 완료할 수 없습니다.
* SITES-9733: 콘텐츠 조각: 콘텐츠 조각 참조 패널의 에셋 참조에 0개의 참조가 표시됩니다.
* SITES-14561: 콘텐츠 조각: 마크업 변환에 대한 HTML을 고정하고 개선했습니다.
* SITES-14882: 콘텐츠 조각: 콘텐츠 조각을 편집하고 저장 또는 닫기 버튼을 클릭하지 않고 탭을 닫으면 값이 저장됩니다.
* SITES-15167: 콘텐츠 조각: 잘못된 페이로드로 변형을 패치하면 400이 반환되지 않고 500이 반환됩니다.
* SITES-15514: 콘텐츠 조각: RTE 내의 테이블에 대한 잘못된 형식의 Markdown 출력.
* SITES-15661: 콘텐츠 조각: 조각 API의 참조 필드에서 고유 제약 조건을 사용하고 항목 순서를 변경하지 마십시오.
* SITES-15730: Screens: Screens 채널 미리 보기 기능이 대시보드에서 작동하지 않습니다.
* SITES-15995: 콘텐츠 조각: 모델 및 조각 긴 텍스트 필드의 MIME 유형이 하드코딩됩니다.
* SITES-16074: 콘텐츠 조각: 문자열이 아닌 태그 필드[] jcr에서 검색할 수 없습니다.
* SITES-16084: 콘텐츠 조각: CFHomeCardModelImpl에 타겟 탐색기가 없습니다.
* SITES-14773: 경험 조각: 링크 참조가 경험 조각 내에서 업데이트되지 않습니다.
* SITES-14899: 경험 조각: Target의 XF 변형에 대해 생성된 여러 오퍼입니다.
* SITES-8590: GraphQL: 지속 쿼리의 변수 인코딩 문제
* SITES-9224: GraphQL: GraphQLServlet에서 &quot;Writer가 이미 닫혔습니다&quot; 예외가 발생했습니다.
* SITES-14800: GraphQL: 변수가 있는 지속 GraphQL 쿼리의 예외.
* SITES-15586: GraphQL: null 값이 있는 지속 쿼리 필터링 문제.
* SITES-15622: GraphQL: 숫자 및 부울 매개 변수와 함께 지속된 쿼리 문제.
* SITES-15654: GraphQL: 같은 이름의 조합 및 속성 문제.
* SITES-15267: 론치: 프로모션은 론치 구성을 수정하기 전에 수정된 론치 페이지를 선택하지 않습니다.
* SITES-15406: Launches: 시작 페이지를 추가할 수 없습니다.
* SITES-15427: Launches: &quot;현재 페이지 및 하위 페이지 승격&quot; 범위의 일관되지 않은 동작.
* SITES-15429: 론치: 론치를 홍보하는 동안 삭제된 페이지 작성.
* SITES-15462: 시작: 자동 프로모션 프로세스에서 프로모션 범위의 페이지를 게시합니다.
* SITES-15815: Launch에서 Launches: 삭제된 페이지로 인해 Launch가 정상적으로 홍보되지 않습니다.
* SITES-15223: 페이지 편집기: 태블릿 크기 에뮬레이터에서 구성 요소의 크기를 조정할 수 없습니다.
* SITES-15463: 페이지 템플릿: 템플릿을 게시할 수 없습니다.

### 알려진 문제 {#known-issues-13665}

없음

### 임베드된 기술 {#embedded-tech-13665}

| 기술 | 버전 | 링크 |
|---|---|---|
| AEM Oak | 1.54-T20230817132355-3800a65 | [Oak API 1.54.0 API](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.54.0/index.html) |
| AEM SLING API | 버전 2.27.2 | [Apache Sling API 2.27.2 API](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 버전 1.4.20-1.4.0 | [HTML 템플릿 언어 사양](https://github.com/adobe/htl-spec) |
| AEM 핵심 구성 요소 | 버전 2.23.4 | [AEM WCM 핵심 구성 요소](https://github.com/adobe/aem-core-wcm-components) |
