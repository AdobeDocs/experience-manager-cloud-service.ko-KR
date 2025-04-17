---
title: ' [!DNL Adobe Experience Manager] as a Cloud Service의 현재 유지 관리 릴리스 정보입니다.'
description: ' [!DNL Adobe Experience Manager] as a Cloud Service의 현재 유지 관리 릴리스 정보입니다.'
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: c5152543550b5f81bf0b79741f288b0c16648584
workflow-type: tm+mt
source-wordcount: '452'
ht-degree: 38%

---


# 유지 관리 릴리스 정보 {#maintenance-release-notes}

다음 섹션에서는 Experience Manager as a Cloud Service의 현재 유지 관리 릴리스에 대한 기술 릴리스 정보를 간략히 소개합니다.

## 릴리스 20476 {#20476}

다음은 2025년 4월 15일에 공개적으로 릴리스된 유지 보수 릴리스 20476에 대한 지속적인 개선 사항을 요약했습니다. 이전 유지 관리 릴리스는 릴리스 20133.

이 유지 관리 릴리스(2025.4.0)에 대한 기능 활성화는 전체 기능 세트를 제공합니다. 자세한 내용은 [Experience Manager 릴리스 로드맵](https://experienceleague.adobe.com/ko/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap)을 참조하십시오.

### 개선 사항 {#enhancements-20476}

* CNTBF-411: JCR에서 슬링 작업을 삭제하는 경우 가능성을 추가합니다.
* CQ-4359813: AEM 번역 키트: 3월 20일
* CQ-4359811: Granite 번역 키트: 3월 20일.
* GRANITE-57863: Filevault를 버전 3.8.4로 업데이트합니다.
* GRANITE-56154: oak-segment-azure에서 지수 재시도를 구성합니다.
* GRANITE-55999: UserPropertiesService의 성능을 개선합니다.
* GRANITE-55781: 사용자 멤버십을 중복 재구성하지 마십시오.
* GRANITE-53956: oak-segment-azure용 Azure SDK V8을 V12로 업그레이드합니다.
* GRANITE-50654: 사용자 권한 탭에서 기본적으로 프런트 엔드에 있는 &quot;모든 사용자&quot; 로드를 제거합니다.
* SKYOPS-103444: Sling ResourceResolver 1.12.6으로 업데이트합니다.
* SKYOPS-101147: 캐시 임플을 업데이트합니다.
* SKYOPS-97124: 오래된 버전의 SPIFly 번들에 대한 분석기 경고를 추가합니다.
* SKYOPS-95826: 런타임 Java 버전을 11.0.26 및 21.0.6으로 업데이트합니다.
* SKYOPS-53671: (RDE) AEM 재시작에서 기능 모델에서 고객이 설치한 아티팩트를 사용합니다.

### 해결된 문제 {#fixed-issues-20476}

* ASSETS-49027: [회귀] AemRequestEventFilter는 OSGI 웹 콘솔에 대한 POST 요청을 중단합니다.
* ASSETS-44956: Dynamic Media 렌디션을 선택할 수 없음 - 스크립트 태그가 최상위 구성 요소에 로드되어야 합니다.
* CNTBF-410: ContentCopy 번들의 CheckJob getId null 포인터입니다.
* CNTBF-341: ContentCopy 내보내기 인덱스가 범위를 벗어났습니다.
* CQ-4355411: 도구 설명이 &quot;사용자 환경 설정&quot; 대화 상자의 디스플레이에 남아 있습니다.
* GRANITE-57265: 드롭다운 선택 값이 선택되지 않습니다.
* GRANITE-57067 - UI에 대한 효과적인 정책이 없습니다.
* SITES-30727: AEM 편집기 내의 하위 구성 요소에 대한 끌어다 놓기가 실패할 수 있습니다.
* SKYOPS-90607: 슬링 작업은 비활성 배포/변경 가능한 콘텐츠에서 실행됩니다.
* SKYOPS-95722: AEM-SDK의 빠른 시작 플래그에서 `MaxPermSize` 크기를 제거합니다.
* SKYOPS-103569: 특정 이미지는 Java 21로 로드할 수 없습니다. `javax.imageio.IIOException: Cannot create Sun JPEGImageReader backend`.

### 알려진 문제 {#known-issues-20476}

없음.

### 사용 중단된 기능 및 API {#deprecated-20476}

AEM as a Cloud Service에서 더 이상 사용되지 않는 기능과 API는 [사용 중단된 기능 및 API](/help/release-notes/deprecated-removed-features.md) 문서에 자세히 설명되어 있습니다.

### 보안 수정 {#security-20476}

AEM as a Cloud Service는 플랫폼의 보안 및 성능 최적화에 중점을 둡니다. 이 유지 관리 릴리스는 확인된 5개의 취약점을 해결하여 강력한 시스템 보호에 대한 약속을 강화합니다.

### 임베드된 기술 {#embedded-tech-20476}

| 기술 | 버전 | 링크 |
|---|---|---|
| AEM Oak | 1.78.0 | [Oak API 1.78.0 API](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.78.0/index.html) |
| AEM SLING API | 2.27.6 | [Apache Sling API 2.27.6 API](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 1.4.26-1.4.0 | [HTML 템플릿 언어 사양](https://github.com/adobe/htl-spec) |
| AEM 핵심 구성 요소 | 2.28.0 | [AEM WCM 핵심 구성 요소](https://github.com/adobe/aem-core-wcm-components) |
