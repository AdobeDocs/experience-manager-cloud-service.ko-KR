---
title: ' [!DNL Adobe Experience Manager] as a Cloud Service의 현재 유지 관리 릴리스 정보입니다.'
description: ' [!DNL Adobe Experience Manager] as a Cloud Service의 현재 유지 관리 릴리스 정보입니다.'
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: 6884e33a922a7147e3a6a3f3ddb3dd3b2da85fbf
workflow-type: tm+mt
source-wordcount: '562'
ht-degree: 48%

---


# 유지 관리 릴리스 정보 {#maintenance-release-notes}

다음 섹션에서는 Experience Manager as a Cloud Service의 현재 유지 관리 릴리스에 대한 기술 릴리스 정보를 간략히 소개합니다.

## 릴리스 21005 {#21005}

2025년 5월 27일에 공개적으로 릴리스된 유지 보수 릴리스 21005에 대한 지속적인 개선 사항을 요약하면 다음과 같습니다. 이전 유지 관리 릴리스는 릴리스 20626이었습니다.

이 유지 관리 릴리스(2025.5.0)에 대한 기능 활성화는 전체 기능 세트를 제공합니다. 자세한 내용은 [Experience Manager 릴리스 로드맵](https://experienceleague.adobe.com/ko/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap)을 참조하십시오.

### 개선 사항 {#enhancements-21005}

* GRANITE-58927: 의미 체계 검색 전환 개선 사항.
* GRANITE-58800: Apache Commons 컬렉션을 버전 4.5.0으로 업데이트합니다.
* GRANITE-58866: Oak을 1.80.0으로 업데이트합니다.
* SKYOPS-106509: Java 21에서 반사 액세스를 통해 GSON 호환성을 개선했습니다.
* SKYOPS-107761: Jackson Exporter 슬링 모델을 1.1.6으로 업데이트합니다.
* SKYOPS-107813: Sling ResourceResolver 1.12.8로 업데이트합니다.

### 해결된 문제 {#fixed-issues-21005}

* CNTBF-443: SearchSlingJob `EVENT_JOB_TOPIC` 속성을 수정했습니다.
* GRANITE-57853: UI의 드롭다운 정렬 문제가 수정되었습니다.
* GRANITE-58107: OAuth 처리기에서 사용자 기반 pod 친화성을 비활성화하여 게시에서 404 오류를 해결했습니다.
* GRANITE-58276, SLING-12755: HTL 스크립트 엔진 팩토리가 올바르게 시작되지 않도록 하여 서버측 렌더링 오류가 간헐적으로 발생하는 OSGi 종속성 사이클을 수정했습니다.
* SKYOPS-105151: 번들 목록에 액세스할 때 NPE가 수정되었습니다.
* SKYOPS-83910, SKYOPS-82371 - JSP 컴파일 동시 실행 문제가 수정되었습니다.

#### AEM 안내서 {#guides}

* GUIDES-26919 : 통합 셸이 활성화된 DITA 맵을 열면 편집기가 간헐적으로 새로 고쳐집니다.
* GUIDES-26282: 항목을 업데이트하거나 만드는 동안 JCR 세션 연결을 닫지 못하면 메모리 누수 및 서비스 다운타임이 발생합니다.
* GUIDES-26434: DITA 콘텐츠에 `external` 범위가 없는 웹 링크가 있는 경우 기본 PDF 게시가 무기한 계속됩니다.
* GUIDES-26516: 콘텐츠에 오류가 있으면 기본 PDF 및 AEM 사이트 게시가 중지되고 대기열에 삽입됩니다.

릴리스에서 수정된 새로운 기능과 향상된 기능 및 문제에 대한 자세한 내용은 [Experience Manager Guides 릴리스 로드맵](https://experienceleague.adobe.com/ko/docs/experience-manager-guides/using/release-info/aem-guides-releases-roadmap)을 참조하십시오.

### 알려진 문제 {#known-issues-21005}

없음.

### 사용 중단된 기능 및 API {#deprecated-21005}

* GRANITE-54164: 공개 API에서 `org.apache.jackrabbit.oak.plugins.blob`을(를) 제거했습니다.
* GRANITE-54280: 공개 API에서 `org.apache.jackrabbit.oak.cache`을(를) 제거했습니다.
* GRANITE-58332: 공용 API에서 `org.apache.jackrabbit.oak.plugins.memory`을(를) 사용하지 않습니다.
* JAVASCRIPT용 YUI 압축기는 더 이상 사용되지 않습니다.
* [Experience Cloud 설치 자동화](/help/sites-cloud/integrating/adobe-analytics-exc-setup-automation.md) 기능은 더 이상 사용되지 않습니다.

AEM as a Cloud Service에서 더 이상 사용되지 않는 기능과 API는 [사용 중단된 기능 및 API](/help/release-notes/deprecated-removed-features.md) 문서에 자세히 설명되어 있습니다.

### 보안 수정 {#security-21005}

AEM as a Cloud Service는 플랫폼의 보안 및 성능 최적화에 중점을 둡니다. 이 유지 관리 릴리스에서는 강력한 시스템 보호에 대한 노력의 일환으로 식별된 취약점 5가지가 해결되었습니다.

### 변경 사항 공지 {#change-notice-21005}

* 이 릴리스에는 다음과 같은 새로운 제품 인덱스 버전이 포함되어 있습니다.
   * **damAssetLucene-12**

이전 색인 버전의 사용자 정의 버전은 새 제품 색인 버전과 자동으로 병합됩니다. 병합된 버전에 추가 사용자 정의 업데이트를 적용하십시오.

#### Aem-cloud-testing-clients 업데이트 {#update-aem-cloud-testing-clients-21005}

향후 변경 사항을 적용하려면 사용자 정의 기능 테스트에 사용된 [aem-cloud-testing-clients](https://github.com/adobe/aem-testing-clients) 라이브러리를 **1.2.1** 이상 버전으로 업데이트해야 합니다(권장: 최신 버전 1.2.9).

`it.tests/pom.xml`의 종속성이 업데이트되었는지 확인합니다.

```xml
<dependency>
   <groupId>com.adobe.cq</groupId>
   <artifactId>aem-cloud-testing-clients</artifactId>
   <version>1.2.9</version>
</dependency>
```

이 변경 사항은 2025년 6월 15일 이전에 수행해야 합니다.
종속성 라이브러리를 업데이트할 수 없으면 “사용자 정의 기능 테스트” 단계에서 파이프라인 오류가 발생합니다.

### 임베드된 기술 {#embedded-tech-21005}

| 기술 | 버전 | 링크 |
|---|---|---|
| AEM Oak | 1.80.0 | [Oak API 1.80.0 API](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.80.0/index.html) |
| AEM SLING API | 2.27.6 | [Apache Sling API 2.27.6 API](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 1.4.28-1.4.0 | [HTML 템플릿 언어 사양](https://github.com/adobe/htl-spec) |
| AEM 핵심 구성 요소 | 2.29.0 | [AEM WCM 핵심 구성 요소](https://github.com/adobe/aem-core-wcm-components) |
