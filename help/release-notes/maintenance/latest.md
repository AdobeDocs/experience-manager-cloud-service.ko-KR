---
title: ' [!DNL Adobe Experience Manager] as a Cloud Service의 현재 유지 관리 릴리스 정보입니다.'
description: ' [!DNL Adobe Experience Manager] as a Cloud Service의 현재 유지 관리 릴리스 정보입니다.'
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: de06178f66c95baef15de19296a654f1ed4a0387
workflow-type: tm+mt
source-wordcount: '383'
ht-degree: 33%

---

# 유지 관리 릴리스 정보 {#maintenance-release-notes}

다음 섹션에서는 Experience Manager as a Cloud Service 현재 유지 관리 릴리스의 기술 릴리스 정보에 대해 간략히 소개합니다.

## 릴리스 16544 {#release-16544}

다음은 2024년 6월 4일에 공개적으로 릴리스된 유지 보수 릴리스 16544에 대한 지속적인 개선 사항을 요약합니다. 이전 유지 관리 릴리스는 릴리스 16461.

2024.6.0 기능 활성화는 이 유지 관리 릴리스에 대한 전체 기능 세트를 제공합니다. 자세한 내용은 [Experience Manager 릴리스 로드맵](https://experienceleague.adobe.com/ko/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap)을 참조하십시오.

### 개선 사항 {#enhancements-16544}

* GRANITE-41133: Jakarta Servlet API 5 및 OSGi Servlet Whiteboard API를 지원합니다.
* GRANITE-51355: org.slf4j.event를 사용하지 않습니다.
* GRANITE-51565: AEM에서 로컬 그룹이 게시될 때 AEM은 외부 그룹과의 로컬 그룹 관계를 손실합니다.
* GRANITE-51707: 인증을 위해 HTTP 리디렉션 중에 쿠키 saml_request_path를 설정합니다.
* GRANITE-52010: Jackrabbit 버전을 2.20.16으로 업데이트합니다.
* GRANITE-52057: JCRVLT-745를 고정하는 Filevault를 3.7.3-T20240514105118-694f6aea로 업데이트합니다.
* SKYOPS-35998: &#39;Sling RepoInit&#39; 종속성 업데이트 : Repoinit Parser 1.9.0, Repoinit JCR 1.1.46.

### 해결된 문제 {#fixed-issues-16544}

* GRANITE-51375: 중간 경로를 지정하지 않으면 idp-sync에서 NPE가 발생합니다.
* GUIDES-17171: 15KB를 초과하는 항목의 복사 및 붙여넣기 작업이 예기치 않은 오류로 실패합니다.
* GUIDES-17088: 문서 상태를 변경하는 기능 **파일 속성** 패널이 제대로 작동하지 않고 *초안* 주.
* GUIDES-16931: 항목의 연결된 이미지가 버전을 만든 후 기준선에 표시되지 않습니다.
* GUIDES-16896: 재사용 가능한 콘텐츠 패널은 **사용자 환경 설정** 다음 기준으로 파일을 보도록 설정됨: **파일 이름**.

Experience Manager 안내서에서 수정된 새로운 기능 및 향상된 기능에 대한 자세한 내용은 [Experience Manager 가이드 릴리스 로드맵](https://experienceleague.adobe.com/en/docs/experience-manager-guides/using/release-info/aem-guides-releases-roadmap).

### 알려진 문제 {#known-issues-16544}

없음.

### 변경 사항 공지 {#change-notice-16544}

2024년 9월부터 AEM에서 Sling 모델 내보내기 프레임워크를 통해 리소스 확인자의 직렬화를 as a Cloud Service으로 비활성화합니다. 다음을 참조하십시오 [설명서](/help/implementing/developing/hybrid/disallow-the-serialization-of-resourceresolvers-via-sling-model-exporter.md) 을 참조하십시오.

### 사용 중단된 기능 및 API {#deprecated-16544}

AEM as a Cloud Service에서 더 이상 사용되지 않는 기능을 살펴보려면 [사용 중단된 기능 및 API](/help/release-notes/deprecated-removed-features.md)를 참조하십시오.

### 임베드된 기술 {#embedded-tech-16544}

| 기술 | 버전 | 링크 |
|---|---|---|
| AEM Oak | 1.64.0 | [Oak API 1.64.0 API](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.64.0/index.html) |
| AEM SLING API | 2.27.2 | [Apache Sling API 2.27.2 API](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 1.4.22-1.4.0 | [HTML 템플릿 언어 사양](https://github.com/adobe/htl-spec) |
| AEM 핵심 구성 요소 | 2.25.4 | [AEM WCM 핵심 구성 요소](https://github.com/adobe/aem-core-wcm-components) |
