---
title: ' [!DNL Adobe Experience Manager] as a Cloud Service의 현재 유지 관리 릴리스 정보입니다.'
description: ' [!DNL Adobe Experience Manager] as a Cloud Service의 현재 유지 관리 릴리스 정보입니다.'
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: 90e1ca38bd517215a631573987462a716bfed160
workflow-type: tm+mt
source-wordcount: '629'
ht-degree: 23%

---


# 유지 관리 릴리스 정보 {#maintenance-release-notes}

다음 섹션에서는 Experience Manager as a Cloud Service 현재 유지 관리 릴리스의 기술 릴리스 정보에 대해 간략히 소개합니다.

## 릴리스 18459 {#18459}

다음은 2024년 11월 5일에 공개적으로 릴리스된 유지 보수 릴리스 18459에 대한 지속적인 개선 사항을 요약합니다. 이전 유지 관리 릴리스는 릴리스 18311.

2024.11.0 기능 활성화는 이 유지 관리 릴리스에 대한 전체 기능 세트를 제공합니다. 자세한 내용은 [Experience Manager 릴리스 로드맵](https://experienceleague.adobe.com/ko/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap)을 참조하십시오.

### 개선 사항 {#enhancements-18459}

* CQ-4357471: AEMaaCS에서 i18n 사전 번역에 대한 지원을 추가합니다.
* SITES-23591: 콘텐츠 조각: UUID 지원을 위한 콘텐츠 조각 업그레이드.
* SITES-25440: 콘텐츠 조각: 복제 상태를 표시하는 CFM 검색 API.
* SITES-24369: 콘텐츠 조각: OpenAPI 설명서 개선 사항.
* SITES-25478: 콘텐츠 조각: 외부 에셋 참조에 대한 백엔드 지원을 추가합니다.
* SITES-26119: 콘텐츠 조각: 참조 유형의 외부 에셋 참조에 대한 지원을 추가합니다.
* SITES-21199: 범용 편집기가 있는 Edge Delivery: 페이지에서 만든 템플릿에 대한 지원을 추가합니다.
* SITES-20311: 범용 편집기가 있는 Edge Delivery: CSV를 스프레드시트로 가져오도록 지원을 추가합니다.
* SITES-24821: 범용 편집기가 있는 Edge Delivery: aem.page / aem.live를 기본적으로 Edge Delivery과 통합하도록 설정합니다.

### 해결된 문제 {#fixed-issues-18459}

* CQ-4358730: 번역할 키가 10개 이상 있는 경우 CQPagePreviewGenerator가 실패합니다.
* FORMS-14978: 테마 편집기의 핵심 구성 요소 기반 양식에 대한 페이지 로드를 활성화합니다.
* FORMS-16596: 접근성 문제: 비활성화된 단추가 화면 Reader에서 인식되지 않습니다.
* SITES-10575: MSM: 블루프린트 블룸필터 로더가 100,000개 이상의 행을 로드하려고 합니다.
* SITES-20755: 콘텐츠 조각: UUID 새로 고침이 있는 에셋 참조에 썸네일이 표시되지 않습니다.
* SITES-26253: 콘텐츠 조각: UUID 마이그레이션: Sling 작업 주제를 일반으로 변경합니다.
* SITES-21338: 콘텐츠 조각: referencedBy 끝점이 올바른 페이지 참조를 반환하지 않습니다.
* SITES-24421: 컨텐츠 조각: CF 끝점 편집이 GET CF를 통해 검색된 CF에 대해 작동하지 않습니다.
* SITES-25461: 콘텐츠 조각: CF 검색에서 모델별로 필터링하려면 대/소문자를 구분해야 합니다.
* SITES-25471: 콘텐츠 조각: ModelValidatorServlet에서 전역 모델의 유효성 검사를 수정합니다.
* SITES-25795: cq 날짜 세트가 없는 경우 콘텐츠 조각: CF 모델 API가 실패했습니다.
* SITES-25817: 콘텐츠 조각: Enhance PromoteLaunch: CF 시작에 대한 마지막 프로모션을 업데이트합니다.
* SITES-26030: 콘텐츠 조각: Endpoint /referencesTree가 필요한 헤더를 반환하지 않습니다.
* SITES-26031: 콘텐츠 조각: CFM 검색 끝점에서 복제 상태가 반환되지 않았습니다.
* SITES-26213: 콘텐츠 조각: 콘텐츠 조각 게시 취소는 게시된 참조의 유효성을 검사해야 합니다.
* SITES-26226: 콘텐츠 조각: 제공된 경로 중 사용할 수 있는 경로가 없는 경우 워크플로우 시작 문제.
* SITES-26238: 콘텐츠 조각: API에서 반환한 에셋 참조의 순서가 JCR의 순서와 다릅니다.
* SITES-25456: 이벤트: 페이지를 이동할 때 페이지가 이동된 이벤트 외에 페이지가 삭제된 이벤트가 생성됩니다.
* SITES-25658: 이벤트: 계층 및 sourceUrl이 페이지 콘텐츠 상태 이벤트에서 채워지지 않습니다.
* SITES-6497: 시작: 시작에서 페이지 만들기가 작동하지 않습니다.
* SITES-25938: Launches: 번역 프로젝트 이후 예기치 않은 삭제가 발생했습니다.
* SITES-25393: 범용 편집기가 있는 Edge Delivery: 단일 단락으로 서식이 지정된 리치 텍스트를 렌더링할 때 텍스트 노드가 손실됩니다.
* SITES-24643: 범용 편집기가 있는 Edge Delivery: OpenGraph 및 twitter 메타데이터 속성이 페이지 메타데이터 모델에서 작동하지 않습니다.
* SITES-25401: 경험 구성요소: 느린 XF 참조 업데이트


### 알려진 문제 {#known-issues-18459}

없음.

### 사용 중단된 기능 및 API {#deprecated-18459}

AEM as a Cloud Service에서 더 이상 사용되지 않는 기능과 API는 [사용 중단된 기능 및 API](/help/release-notes/deprecated-removed-features.md) 문서에 자세히 설명되어 있습니다.

### 보안 수정 {#security-18459}

AEM as a Cloud Service는 플랫폼의 보안 및 성능을 최적화하는 데 사용됩니다. 이 유지 관리 릴리스는 21개의 식별된 취약점을 해결하여 강력한 시스템 보호에 대한 노력을 강화합니다.

### 임베드된 기술 {#embedded-tech-18459}

| 기술 | 버전 | 링크 |
|---|---|---|
| AEM Oak | 1.70.0 | [Oak API 1.70.0 API](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.70.0/index.html) |
| AEM SLING API | 2.27.6 | [Apache Sling API 2.27.6 API](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 1.4.24-1.4.0 | [HTML 템플릿 언어 사양](https://github.com/adobe/htl-spec) |
| AEM 핵심 구성 요소 | 2.27.0 | [AEM WCM 핵심 구성 요소](https://github.com/adobe/aem-core-wcm-components) |
