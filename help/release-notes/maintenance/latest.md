---
title: ' [!DNL Adobe Experience Manager] as a Cloud Service의 현재 유지 관리 릴리스 정보입니다.'
description: ' [!DNL Adobe Experience Manager] as a Cloud Service의 현재 유지 관리 릴리스 정보입니다.'
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
source-git-commit: dbdc63db9a9ac954ce6359d3643231d6e195fd53
workflow-type: tm+mt
source-wordcount: '302'
ht-degree: 84%

---

# 유지 관리 릴리스 정보 {#maintenance-release-notes}

다음 섹션에서는 Experience Manager as a Cloud Service 현재 유지 관리 릴리스의 기술 릴리스 정보에 대해 간략히 소개합니다.

## 릴리스 15575 {#release-15575}

2024년 3월 19일에 공개적으로 릴리스된 유지 보수 릴리스 15575에 대한 지속적인 개선 사항을 요약하면 다음과 같습니다. 이전 유지 관리 릴리스는 릴리스 15262.

이 유지 관리 릴리스(2024.3.0)에 대한 기능 활성화는 전체 기능 세트를 제공합니다. 자세한 내용은 [Experience Manager 릴리스 로드맵](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap.html)을 참조하십시오.

### 개선 사항 {#enhancements-15575}

없음.

### 해결된 문제 {#fixed-issues-15575}

* ASSETS-36358: 업로드 보고서를 렌더링할 수 없습니다.
* GRANITE-50774: GraniteContent는 초기화 시 속성 값의 결정적 순서를 사용해야 합니다.

### 알려진 문제 {#known-issues-15575}

없음.

### 변경 사항 공지 {#change-notice-15575}

**조치 필요**

#### CM Java 버전을 11로 설정 {#set-java-version-11}

aem-sdk-api의 새 버전에는 Cloud Manager 빌드 환경 기본 JDK 버전 1.8과 호환되지 않는 Java 11 대상으로 컴파일된 클래스가 포함되어 있습니다. 이 업데이트를 사용하려면 JDK 11을 사용하여 Maven을 실행해야 합니다.

고객은 `.cloudmanager/java-version` 파일을 콘텐츠 `11`과 함께 Git 저장소의 루트에 추가할 것이 권장됩니다. 다음을 참조하십시오 [빌드 환경 / Maven JDK 버전 설정](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/build-environment-details.md#alternate-maven-jdk-version).

#### aem-cloud-testing-clients를 1.2.1로 업데이트 {#update-aem-cloud-testing-clients}

향후 변경 사항을 적용하려면 사용자 정의 기능 테스트에 사용되는 [aem-cloud-testing-clients](https://github.com/adobe/aem-testing-clients) 라이브러리를 최소 버전 **1.2.1로 업데이트해야 합니다.**

`it.tests/pom.xml`의 종속성이 업데이트되었는지 확인합니다.

```xml
<dependency>
   <groupId>com.adobe.cq</groupId>
   <artifactId>aem-cloud-testing-clients</artifactId>
   <version>1.2.1</version>
</dependency>
```

이 변경 사항은 2024년 4월 6일 이전에 수행해야 합니다.

종속성 라이브러리를 업데이트할 수 없으면 “사용자 정의 기능 테스트” 단계에서 파이프라인 오류가 발생합니다.

### 임베드된 기술 {#embedded-tech-15575}

| 기술 | 버전 | 링크 |
|---|---|---|
| AEM OAK | 1.60-T20240131102219-0cde853 | [Oak API 1.60.0 API](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.60.0/index.html) |
| AEM SLING API | 버전 2.27.2 | [Apache Sling API 2.27.2 API](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 버전 1.4.20-1.4.0 | [HTML 템플릿 언어 사양](https://github.com/adobe/htl-spec) |
| AEM 핵심 구성 요소 | 버전 2.23.4 | [AEM WCM 핵심 구성 요소](https://github.com/adobe/aem-core-wcm-components) |
