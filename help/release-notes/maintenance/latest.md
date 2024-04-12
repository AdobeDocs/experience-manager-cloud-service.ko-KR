---
title: ' [!DNL Adobe Experience Manager] as a Cloud Service의 현재 유지 관리 릴리스 정보입니다.'
description: ' [!DNL Adobe Experience Manager] as a Cloud Service의 현재 유지 관리 릴리스 정보입니다.'
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
source-git-commit: 1dd2eae9201c86d2cdac78ff99634eff8ca57a05
workflow-type: tm+mt
source-wordcount: '272'
ht-degree: 85%

---

# 유지 관리 릴리스 정보 {#maintenance-release-notes}

다음 섹션에서는 Experience Manager as a Cloud Service 현재 유지 관리 릴리스의 기술 릴리스 정보에 대해 간략히 소개합니다.

## 릴리스 15860 {#release-15860}

다음은 2024년 4월 10일에 공개적으로 릴리스된 유지 보수 릴리스 15860에 대한 지속적인 개선 사항을 요약했습니다. 이전 유지 관리 릴리스는 릴리스 15787.

이 유지 관리 릴리스(2024.3.0)에 대한 기능 활성화는 전체 기능 세트를 제공합니다. 자세한 내용은 [Experience Manager 릴리스 로드맵](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap.html?lang=ko-KR)을 참조하십시오.

### 개선 사항 {#enhancements-15860}

없음.

### 해결된 문제 {#fixed-issues-15860}

* 론치가 삭제되거나 이동된 페이지를 참조할 때 론치 콘솔을 표시하기 위한 회귀 문제를 수정합니다.

### 알려진 문제 {#known-issues-15860}

없음.

### 사용 중단된 기능 및 API {#deprecated-15860}

* [Adobe Developer Console에서 JWT 자격 증명 사용 중단](/help/security/jwt-credentials-deprecation-in-adobe-developer-console.md)

AEM as a Cloud Service에서 더 이상 사용되지 않거나 제거된 기능을 살펴보려면 [사용 중단된 기능 및 API](/help/release-notes/deprecated-removed-features.md)를 확인하십시오.

### 변경 사항 공지 {#change-notice-15860}

**조치 필요**

#### CM Java 버전을 11로 설정 {#set-java-version-11}

aem-sdk-api의 새 버전에는 Cloud Manager 빌드 환경 기본 JDK 버전 1.8과 호환되지 않는 Java 11 대상으로 컴파일된 클래스가 포함되어 있습니다. 이 업데이트를 사용하려면 JDK 11을 사용하여 Maven을 실행해야 합니다.

고객은 `.cloudmanager/java-version` 파일을 콘텐츠 `11`과 함께 Git 저장소의 루트에 추가할 것이 권장됩니다. [빌드 환경 / Maven JDK 버전 설정](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/build-environment-details.md#alternate-maven-jdk-version)을 참조하십시오.


### 임베드된 기술 {#embedded-tech-15860}

| 기술 | 버전 | 링크 |
|---|---|---|
| AEM OAK | 1.60-T20240131102219-0cde853 | [Oak API 1.60.0 API](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.60.0/index.html) |
| AEM SLING API | 버전 2.27.2 | [Apache Sling API 2.27.2 API](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 버전 1.4.20-1.4.0 | [HTML 템플릿 언어 사양](https://github.com/adobe/htl-spec) |
| AEM 핵심 구성 요소 | 버전 2.24.4 | [AEM WCM 핵심 구성 요소](https://github.com/adobe/aem-core-wcm-components) |
