---
title: ' [!DNL Adobe Experience Manager] as a Cloud Service의 현재 유지 관리 릴리스 정보입니다.'
description: ' [!DNL Adobe Experience Manager] as a Cloud Service의 현재 유지 관리 릴리스 정보입니다.'
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: 33468de99a3e77539f4bdc9435324c9f52a45d9f
workflow-type: tm+mt
source-wordcount: '350'
ht-degree: 59%

---


# 유지 관리 릴리스 정보 {#maintenance-release-notes}

다음 섹션에서는 Experience Manager as a Cloud Service의 현재 유지 관리 릴리스에 대한 기술 릴리스 정보를 간략히 소개합니다.

## 릴리스 22171 {#22171}

다음은 2025년 9월 2일에 공개적으로 릴리스된 유지 보수 릴리스 22171에 대한 지속적인 개선 사항을 요약합니다. 이전 유지 관리 릴리스는 릴리스 21994.

2025.9.0 기능 활성화는 이 유지 관리 릴리스에 대한 전체 기능 세트를 제공합니다. 자세한 내용은 [Experience Manager 릴리스 로드맵](https://experienceleague.adobe.com/ko/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap)을 참조하십시오.

### 새로운 기능  {#new-features-22171}

* ASSETS-53136: OpenAPI를 사용하는 Dynamic Media의 Vanity ID 지원.

### 개선 사항 {#enhancements-22171}

없음.

### 해결된 문제 {#fixed-issues-22171}

* ASSETS-52510: 유니코드 `U+202F`이(가) 포함된 파일 이름에 대해 중복 파일 이름 검색이 실패합니다.
* ASSETS-53489: Assets 보기 UI에서 폴더를 삭제해도 포함된 모든 에셋의 승인이 취소되지는 않습니다.
* ASSETS-54821: Asset Link에 간헐적으로 &quot;서버 오류&quot;가 발생했습니다.
* ASSETS-55024: AEM Assets &quot;이메일로 다운로드&quot; 템플릿의 손상된 이미지
* ASSETS-55325: Dynamic Media 정적 URL에서는 에셋 이름 변경 후 파일 확장자가 생략됩니다.
* ASSETS-55334: 링크 공유 대화 상자가 잠시 깜박이거나 사라지거나 나타나지 않습니다.
* ASSETS-55382: 비동기 자산 작업이 다시 시작되어 중복 대상 폴더를 만듭니다.
* ASSETS-55472: 게시 관리 옵션 &quot;이미 게시된 페이지만 포함&quot;이 무시됩니다.
* SITES-31600: 개인화를 중단하는 동안 Contexthub js 오류가 발생했습니다.

릴리스에서 수정된 새로운 기능과 향상된 기능 및 문제에 대한 자세한 내용은 [Experience Manager Guides 릴리스 로드맵](https://experienceleague.adobe.com/ko/docs/experience-manager-guides/using/release-info/aem-guides-releases-roadmap)을 참조하십시오.

### 알려진 문제 {#known-issues-22171}

없음.

### 사용 중단된 기능 및 API {#deprecated-22171}

AEM as a Cloud Service에서 더 이상 사용되지 않는 기능과 API는 [사용 중단된 기능 및 API](/help/release-notes/deprecated-removed-features.md) 문서에 자세히 설명되어 있습니다.

### 보안 수정 {#security-22171}

AEM as a Cloud Service는 플랫폼의 보안 및 성능을 최적화하는 데 사용됩니다. 이 유지 관리 릴리스에서는 강력한 시스템 보호에 대한 노력의 일환으로 식별된 취약점 7개가 해결되었습니다.

### 임베드된 기술 {#embedded-tech-22171}

| 기술 | 버전 | 링크 |
|---|---|---|
| AEM Oak | 1.84.0 | [Oak API 1.84.0 API](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.84/index.html) |
| AEM SLING API | 2.27.6 | [Apache Sling API 2.27.6 API](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 1.4.28-1.4.0 | [HTML 템플릿 언어 사양](https://github.com/adobe/htl-spec) |
| Apache HTTP 서버 | 2.4.65 | [Apache Httpd 2.4.65](https://apache.googlesource.com/httpd/+/refs/tags/2.4.65/CHANGES) |
| AEM 핵심 구성 요소 | 2.29.0 | [AEM WCM 핵심 구성 요소](https://github.com/adobe/aem-core-wcm-components) |
| Node.js | 14 (기본값) | [지원되는 Node.js 버전](https://experienceleague.adobe.com/ko/docs/experience-manager-cloud-service/content/implementing/developing/developing-with-front-end-pipelines#node-versions) |
