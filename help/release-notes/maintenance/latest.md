---
title: ' [!DNL Adobe Experience Manager] as a Cloud Service의 현재 유지 관리 릴리스 정보입니다.'
description: ' [!DNL Adobe Experience Manager] as a Cloud Service의 현재 유지 관리 릴리스 정보입니다.'
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
source-git-commit: f15b42e4012385c461b5440b92f53c4e58fb8ac2
workflow-type: tm+mt
source-wordcount: '213'
ht-degree: 61%

---

# 유지 관리 릴리스 정보 {#maintenance-release-notes}

다음 섹션에서는 Experience Manager as a Cloud Service 현재 유지 관리 릴리스의 기술 릴리스 정보에 대해 간략히 소개합니다.

## 릴리스 15977 {#release-15977}

다음은 2024년 4월 19일에 공개적으로 릴리스된 유지 보수 릴리스 15977에 대한 지속적인 개선 사항을 요약한 것입니다. 이전 유지 관리 릴리스는 릴리스 15939.

2024.4.0 기능 활성화는 이 유지 관리 릴리스에 대한 전체 기능 세트를 제공합니다. 자세한 내용은 [Experience Manager 릴리스 로드맵](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap.html?lang=ko-KR)을 참조하십시오.

### 개선 사항 {#enhancements-15977}

* GRANITE-51335: AEM 상태 검사를 최적화하여 인스턴스 안정성을 향상시킵니다.

### 해결된 문제 {#fixed-issues-15977}

* CQ-4357226: OAuth 자격 증명에 대한 IMS 구성 지원에서 회귀 문제를 해결합니다.
* GRANITE-51335: 5.0.4 Felix Health Check 등록 수정 사항으로 Ratelimit 업그레이드.

### 알려진 문제 {#known-issues-15977}

없음.

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
