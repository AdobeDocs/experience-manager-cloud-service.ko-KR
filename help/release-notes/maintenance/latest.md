---
title: ' [!DNL Adobe Experience Manager] as a Cloud Service의 현재 유지 관리 릴리스 정보입니다.'
description: ' [!DNL Adobe Experience Manager] as a Cloud Service의 현재 유지 관리 릴리스 정보입니다.'
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: 339dd64c602b2eed163f36f70089a50dd0d4a11c
workflow-type: tm+mt
source-wordcount: '521'
ht-degree: 76%

---

# 유지 관리 릴리스 정보 {#maintenance-release-notes}

다음 섹션에서는 Experience Manager as a Cloud Service 현재 유지 관리 릴리스의 기술 릴리스 정보에 대해 간략히 소개합니다.

## 릴리스 16544 {#release-16544}

2024년 6월 4일에 릴리스된 유지 관리 릴리스 16544의 지속적인 개선 사항이 아래에 요약되어 있습니다. 이전 유지 관리 릴리스는 릴리스 16461이었습니다.

이 유지 관리 릴리스(2024.6.0)에 대한 기능 활성화는 전체 기능 세트를 제공합니다. 자세한 내용은 [Experience Manager 릴리스 로드맵](https://experienceleague.adobe.com/ko/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap)을 참조하십시오.

>[!CAUTION]
>
>이전 SDK에서 회귀가 확인되었으므로 여기에서 참조된 SDK를 사용해 주십시오.
>`AEM SDK v2024.06.16647.20240607T103723Z-240500`

### 개선 사항 {#enhancements-16544}

* GRANITE-41133: Jakarta 서블릿 API 5 및 OSGi 서블릿 화이트보드 API를 지원합니다.
* GRANITE-51355: org.slf4j.event를 더 이상 사용하지 않습니다.
* GRANITE-51565: AEM에서 로컬 그룹이 게시되면 AEM은 외부 그룹과의 로컬 그룹 관계를 잃습니다.
* GRANITE-51707: 인증을 위한 http 리디렉션 중에 쿠키 saml_request_path를 설정합니다.
* GRANITE-52010: Jackrabbit 버전을 2.20.16으로 업데이트합니다.
* GRANITE-52057: Filevault를 3.7.3-T20240514105118-694f6aea로 업데이트하여 JCRVLT-745를 수정합니다.
* SKYOPS-35998: “Sling RepoInit” 종속성 업데이트: Repoinit Parser 1.9.0, Repoinit JCR 1.1.46.

### 해결된 문제 {#fixed-issues-16544}

* GRANITE-51375: 중간 경로가 지정되지 않은 경우 idp-sync에서 NPE가 발생합니다.
* GUIDES-17171: 15KB를 초과하는 항목의 복사 및 붙여넣기 작업이 예기치 않은 오류로 인해 실패합니다.
* GUIDES-17088: **파일 속성** 패널에서 문서 상태를 변경하는 기능이 올바르게 작동하지 않고 *초안* 상태로 변경됩니다.
* GUIDES-16931: 버전 생성 후 항목의 링크된 이미지가 기준선에 나타나지 않습니다.
* GUIDES-16896: **사용자 기본 설정**&#x200B;이 **파일 이름**&#x200B;으로 파일을 보도록 설정된 경우 재사용 가능한 콘텐츠 패널에 요소가 나열되지 않습니다.

Experience Manager Guides에서 수정된 새로운 기능과 향상된 기능에 대한 자세한 내용은 [Experience Manager Guides 릴리스 로드맵](https://experienceleague.adobe.com/kr/docs/experience-manager-guides/using/release-info/aem-guides-releases-roadmap)을 참조하십시오.

### 알려진 문제 {#known-issues-16544}

* GRANITE-52573: 이중 슬래시가 포함된 요청 `//` 거부되었습니다(상태 코드 400). 이 동작은 후속 유지 관리 릴리스에서 되돌려집니다.

>[!NOTE]
> AEM Engineering에서는 Analytics로 시작하는 현재 AEM 릴리스에 영향을 주는 론치 기능에 대한 회귀 문제를 16461. 이러한 회귀 현상으로 인해, 딥이 아닌 페이지를 포함하는 새 론치(새 릴리스가 적용된 후 생성됨)는 누락된 구성으로 인해 제대로 홍보되지 않습니다.
> 환경이 영향을 받는 경우 고객 지원을 통해 누락된 구성을 식별하고 업데이트하는 셸 스크립트를 사용할 수 있습니다(내부 참조 SITES-22457).
> 올바른 구성으로 새 론치를 만들 수 있도록 하는 보다 장기적인 수정 사항이 제공됩니다. 그때까지 온디맨드로 내부 패치 릴리스도 이용할 수 있습니다.

### 변경 사항 공지 {#change-notice-16544}

2024년 9월부터 AEM as a Cloud Service는 Sling Model Exporter 프레임워크를 통해 Resource Resolver의 직렬화를 비활성화합니다. 자세한 내용은 [설명서](/help/implementing/developing/hybrid/disallow-the-serialization-of-resourceresolvers-via-sling-model-exporter.md)를 참조하십시오.

### 사용 중단된 기능 및 API {#deprecated-16544}

AEM as a Cloud Service에서 더 이상 사용되지 않는 기능을 살펴보려면 [사용 중단된 기능 및 API](/help/release-notes/deprecated-removed-features.md)를 참조하십시오.

### 임베드된 기술 {#embedded-tech-16544}

| 기술 | 버전 | 링크 |
|---|---|---|
| AEM Oak | 1.64.0 | [Oak API 1.64.0 API](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.64.0/index.html) |
| AEM SLING API | 2.27.2 | [Apache Sling API 2.27.2 API](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 1.4.22-1.4.0 | [HTML 템플릿 언어 사양](https://github.com/adobe/htl-spec) |
| AEM 핵심 구성 요소 | 2.25.4 | [AEM WCM 핵심 구성 요소](https://github.com/adobe/aem-core-wcm-components) |
