---
title: ' [!DNL Adobe Experience Manager] as a Cloud Service의 현재 유지 관리 릴리스 정보입니다.'
description: ' [!DNL Adobe Experience Manager] as a Cloud Service의 현재 유지 관리 릴리스 정보입니다.'
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
source-git-commit: b7e7bc7546b836667fff9db0ea5419e751f492cb
workflow-type: tm+mt
source-wordcount: '269'
ht-degree: 78%

---

# 유지 관리 릴리스 정보 {#maintenance-release-notes}

다음 섹션에서는 Experience Manager as a Cloud Service 현재 유지 관리 릴리스의 기술 릴리스 정보에 대해 간략히 소개합니다.

## 릴리스 15977 {#release-15977}

2024년 4월 19일에 릴리스된 유지 관리 릴리스 15977의 지속적인 개선 사항이 아래에 요약되어 있습니다. 이전 유지 관리 릴리스는 릴리스 15939이었습니다.

이 유지 관리 릴리스(2024.4.0)에 대한 기능 활성화는 전체 기능 세트를 제공합니다. 자세한 내용은 [Experience Manager 릴리스 로드맵](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap.html)을 참조하십시오.

### 개선 사항 {#enhancements-15977}

* GRANITE-51335: AEM 상태 검사가 최적화되어 인스턴스 안정성이 향상되었습니다.

### 해결된 문제 {#fixed-issues-15977}

* CQ-4357226: OAuth 자격 증명에 대한 IMS 구성 지원의 회귀 문제가 해결되었습니다.
* GRANITE-51335: Ratelimit가 5.0.4로 업그레이드되어 Felix 상태 검사 등록이 수정되었습니다.

### 알려진 문제 {#known-issues-15977}

* **(AEM Forms 전용)** AEM Cloud Foundation 유지 관리 릴리스 15977을 설치한 후 양식 작성 및 게시된 양식의 경우 적응형 양식 필드가 잘못된 순서로 렌더링됩니다. AEM Forms을 사용하는 경우 불편을 방지하려면 향후 유지 관리 릴리스에서 문제가 해결될 때까지 15977 릴리스로 업그레이드하지 않는 것이 좋습니다.


### 사용 중단된 기능 및 API {#deprecated-15977}

* [Adobe Developer Console에서 JWT 자격 증명 사용 중단](/help/security/jwt-credentials-deprecation-in-adobe-developer-console.md)

AEM as a Cloud Service에서 더 이상 사용되지 않거나 제거된 기능을 살펴보려면 [사용 중단된 기능 및 API](/help/release-notes/deprecated-removed-features.md)를 확인하십시오.

### 임베드된 기술 {#embedded-tech-15977}

| 기술 | 버전 | 링크 |
|---|---|---|
| AEM OAK | 1.62.0 | [Oak API 1.62.0 API](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.62.0/index.html) |
| AEM SLING API | 2.27.2 | [Apache Sling API 2.27.2 API](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 1.4.20-1.4.0 | [HTML 템플릿 언어 사양](https://github.com/adobe/htl-spec) |
| AEM 핵심 구성 요소 | 2.24.6 | [AEM WCM 핵심 구성 요소](https://github.com/adobe/aem-core-wcm-components) |
