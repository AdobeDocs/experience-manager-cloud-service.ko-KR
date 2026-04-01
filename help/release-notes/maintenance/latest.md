---
title: ' [!DNL Adobe Experience Manager] as a Cloud Service의 현재 유지 관리 릴리스 정보입니다.'
description: ' [!DNL Adobe Experience Manager] as a Cloud Service의 현재 유지 관리 릴리스 정보입니다.'
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: e035c1c27f652af231034588eb1359354182dcb0
workflow-type: tm+mt
source-wordcount: '341'
ht-degree: 47%

---


# 유지 관리 릴리스 정보 {#maintenance-release-notes}

다음 섹션에서는 Experience Manager as a Cloud Service의 현재 유지 관리 릴리스에 대한 기술 릴리스 정보를 간략히 소개합니다.

## 릴리스 25194 {#25194}

다음은 2026년 4월 1일에 공개적으로 릴리스된 유지 보수 릴리스 25194에 대한 지속적인 개선 사항을 요약합니다. 이전 유지 관리 릴리스는 릴리스 24678.

2026.4.0 기능 활성화는 이 유지 관리 릴리스에 대한 전체 기능 세트를 제공합니다. 자세한 내용은 [Experience Manager 릴리스 로드맵](https://experienceleague.adobe.com/ko/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap)을 참조하십시오.

>[!NOTE]
>
>릴리스 24893이 비공개로 설정되었습니다.

### 개선 사항 {#enhancements-25194}

* ASSETS-65127: 이벤트 사용자 지정 메타데이터: 메타데이터 이름 처리가 개선되었습니다.
* ASSETS-63313: C2PA 매니페스트를 기반으로 내보낸 에셋 및 상위 항목에 대한 관련 링크를 자동으로 만듭니다.
* ASSETS-10995: 다운로드 zip의 에셋 수 제한.

### 해결된 문제 {#fixed-issues-25194}

* ASSETS-62882: 관리자 보기: 잘못된 파일 이름이 여러 개 업로드되면 정보 툴팁이 중단됩니다.
* ASSETS-63642: 링크 공유가 일부 개발 환경에서 에셋을 렌더링하지 못합니다(SLA3).
* ASSETS-59267: 게재 페이로드용 애플리케이션 메타데이터를 로드할 때 NPE가 사용됩니다.
* ASSETS-59227: 메타데이터 내보내기: 정규 표현식 일치로 인해 선택하지 않은 속성이 더 이상 포함되지 않습니다.
* ASSETS-65187: 열 데이터에 이스케이프 처리된 쉼표가 포함된 경우 클라우드에서 CSV 미리 보기.
* ASSETS-63441: 모든 사용자에게 Assets Omnisearch 구성을 읽을 수 있는 권한이 있는지 확인합니다.
* SITES-40095: 메타데이터 편집기: 로컬 콘텐츠 조각이 10개 이상의 항목을 참조합니다.

### 알려진 문제 {#known-issues-25194}

없음.

### 사용 중단된 기능 및 API {#deprecated-25194}

AEM as a Cloud Service에서 더 이상 사용되지 않는 기능과 API는 [사용 중단된 기능 및 API](/help/release-notes/deprecated-removed-features.md) 문서에 자세히 설명되어 있습니다.

### 보안 수정 {#security-25194}

AEM as a Cloud Service는 플랫폼의 보안 및 성능 최적화에 중점을 둡니다. 이 유지 관리 릴리스는 9개의 식별된 취약점을 해결하여 강력한 시스템 보호에 대한 노력을 강화합니다.

### 임베드된 기술 {#embedded-tech-25194}

| 기술 | 버전 | 링크 |
|---|---|---|
| AEM Oak | 1.90.0 | [Oak 1.90.0 API](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.90.0/index.html) |
| AEM SLING API | 2.27.6 | [Apache Sling API 2.27.6 API](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 1.4.28-1.4.0 | [HTML 템플릿 언어 사양](https://github.com/adobe/htl-spec) |
| Apache HTTP 서버 | 2.4.65 | [Apache Httpd 2.4.65](https://apache.googlesource.com/httpd/+/refs/tags/2.4.65/CHANGES) |
| AEM 핵심 구성 요소 | 2.30.4 | [AEM WCM 핵심 구성 요소](https://github.com/adobe/aem-core-wcm-components) |
| Node.js | 14 (기본값) | [지원되는 Node.js 버전](https://experienceleague.adobe.com/ko/docs/experience-manager-cloud-service/content/implementing/developing/developing-with-front-end-pipelines#node-versions) |
