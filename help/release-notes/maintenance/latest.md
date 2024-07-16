---
title: ' [!DNL Adobe Experience Manager] as a Cloud Service의 현재 유지 관리 릴리스 정보입니다.'
description: ' [!DNL Adobe Experience Manager] as a Cloud Service의 현재 유지 관리 릴리스 정보입니다.'
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: 573de431328650778b3ef0979a24190477382310
workflow-type: tm+mt
source-wordcount: '332'
ht-degree: 40%

---


# 유지 관리 릴리스 정보 {#maintenance-release-notes}

다음 섹션에서는 Experience Manager as a Cloud Service 현재 유지 관리 릴리스의 기술 릴리스 정보에 대해 간략히 소개합니다.

## 릴리스 17098 {#release-17098}

다음은 2024년 7월 16일에 공개적으로 릴리스된 유지 보수 릴리스 17098에 대한 지속적인 개선 사항을 요약했습니다. 이전 유지 관리 릴리스는 릴리스 16971.

2024.7.0 기능 활성화는 이 유지 관리 릴리스에 대한 전체 기능 세트를 제공합니다. 자세한 내용은 [Experience Manager 릴리스 로드맵](https://experienceleague.adobe.com/ko/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap)을 참조하십시오.

### 개선 사항 {#enhancements-17098}

- SKYOPS-79817: 서비스 사용자 매핑에 대해 Sling 기능 분석기 작업 활성화

### 해결된 문제 {#fixed-issues-17098}

- ASSETS-39665: 6.5에서 AEM CS로 마이그레이션한 후 Smart Crops 동기화가 작동하지 않음
- FORMS-14993: Forms API가 이전에 작업한 자료에 대해 500을 반환합니다
- GRANITE-52120: 액세스 제어 데이터를 표시할 때 CRXDE가 500을 반환함
- GRANITE-52573: 다시 작성된 URL에서 //를 사용할 때 400을 반환하는 요청
- GRANITE-52746: 노드 만들기 대화 상자에 모든 노드 유형이 로드되지 않음
- GRANITE-52777: 요청이 래핑될 때 404의 손상된 처리
- GRANITE-52871: publish-worker가 golden-publish와 동기화되고 압축되기 전에 완료되는지 확인합니다.
- SKYOPS-79173: 복제기가 지정된 AgentIdFilter와 일치하는 여러 에이전트에 복제하지 않음
- SKYOPS-80075: 게시 큐 차단을 초래하는 자산 이름 움라우트 문제(Mac)
- SKYOPS-81032: 고급 로깅을 사용할 때 로그를 가져오려면 요청에 의해 생성된 로그를 필터링합니다

### 알려진 문제 {#known-issues-17098}

없음

### 변경 사항 공지 {#change-notice-17098}

- 2024년 9월부터 AEM as a Cloud Service는 Sling Model Exporter 프레임워크를 통해 Resource Resolver의 직렬화를 비활성화합니다. 자세한 내용은 [설명서](/help/implementing/developing/hybrid/disallow-the-serialization-of-resourceresolvers-via-sling-model-exporter.md)를 참조하십시오.

### 사용 중단된 기능 및 API {#deprecated-17098}

AEM as a Cloud Service에서 사용이 중단되거나 제거된 기능 및 API는 [사용이 중단되거나 제거된 기능 및 API](/help/release-notes/deprecated-removed-features.md) 문서에 자세히 설명되어 있습니다.

### 임베드된 기술 {#embedded-tech-17098}

| 기술 | 버전 | 링크 |
|---|---|---|
| AEM Oak | 1.66.0 | [Oak API 1.66.0 API](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.66.0/index.html) |
| AEM SLING API | 2.27.2 | [Apache Sling API 2.27.2 API](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 1.4.24-1.4.0 | [HTML 템플릿 언어 사양](https://github.com/adobe/htl-spec) |
| AEM 핵심 구성 요소 | 2.25.4 | [AEM WCM 핵심 구성 요소](https://github.com/adobe/aem-core-wcm-components) |
