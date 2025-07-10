---
title: ' [!DNL Adobe Experience Manager] as a Cloud Service의 현재 유지 관리 릴리스 정보입니다.'
description: ' [!DNL Adobe Experience Manager] as a Cloud Service의 현재 유지 관리 릴리스 정보입니다.'
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: 17064d27dd34bbd5aad89f814481c29b0f6a7fe1
workflow-type: tm+mt
source-wordcount: '366'
ht-degree: 56%

---


# 유지 관리 릴리스 정보 {#maintenance-release-notes}

다음 섹션에서는 Experience Manager as a Cloud Service의 현재 유지 관리 릴리스에 대한 기술 릴리스 정보를 간략히 소개합니다.

## 릴리스 21484 {#21484}

다음은 2025년 7월 10일에 공개적으로 릴리스된 유지 보수 릴리스 21484에 대한 지속적인 개선 사항을 요약했습니다. 이전 유지 관리 릴리스는 릴리스 21331.

이 유지 관리 릴리스(2025.7.0)에 대한 기능 활성화는 전체 기능 세트를 제공합니다. 자세한 내용은 [Experience Manager 릴리스 로드맵](https://experienceleague.adobe.com/ko/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap)을 참조하십시오.

### 개선 사항 {#enhancements-21484}

없음.

### 해결된 문제 {#fixed-issues-21484}

없음

#### AEM Guides {#guides-21484}

* GUIDES-29781: Source 보기의 요소 내에 XML 주석을 추가하면 보기를 전환할 때 주석 주위의 선행 및 후행 공백이 손실됩니다.
* GUIDES-29078: 브라우저를 새로 고친 후 작성자 보기에서 주제를 열 때 [파일 속성] 패널의 이전에 적용된 태그는 유지되지 않으며, 특히 선택할 수 있는 태그가 많을 경우 새 태그를 추가하면 기존 태그를 덮어씁니다.
* GUIDES-28214: 검토 노드가 생성되지 않으므로 AEM 워크플로우를 통해 검토 작업을 만들려고 하면 지속적으로 실패합니다.
* GUIDES-28104: `chunk=to-content` 특성이 있는 DITA 맵을 게시하면 새 AEM Sites 출력에 중복 JCR 노드가 생성되어 AEM Sites에서 컨텐츠 구조가 중복됩니다.
* GUIDES-29065, GUIDES-28793: 큰 컬렉션으로 작업할 때 로드 시간이 길어지고 간헐적인 시간 초과와 같은 성능 문제가 발생합니다.

릴리스에서 수정된 새로운 기능과 향상된 기능 및 문제에 대한 자세한 내용은 [Experience Manager Guides 릴리스 로드맵](https://experienceleague.adobe.com/ko/docs/experience-manager-guides/using/release-info/aem-guides-releases-roadmap)을 참조하십시오.

### 알려진 문제 {#known-issues-21484}

없음.

### 사용 중단된 기능 및 API {#deprecated-21484}

AEM as a Cloud Service에서 더 이상 사용되지 않는 기능과 API는 [사용 중단된 기능 및 API](/help/release-notes/deprecated-removed-features.md) 문서에 자세히 설명되어 있습니다.

### 보안 수정 {#security-21484}

AEM as a Cloud Service는 플랫폼의 보안 및 성능 최적화에 중점을 둡니다. 이 유지 관리 릴리스에서는 강력한 시스템 보호에 대한 노력의 일환으로 식별된 취약점 5가지가 해결되었습니다.

### 임베드된 기술 {#embedded-tech-21484}

| 기술 | 버전 | 링크 |
|---|---|---|
| AEM Oak | 1.80.0 | [Oak API 1.80.0 API](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.80.0/index.html) |
| AEM SLING API | 2.27.6 | [Apache Sling API 2.27.6 API](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 1.4.28-1.4.0 | [HTML 템플릿 언어 사양](https://github.com/adobe/htl-spec) |
| AEM 핵심 구성 요소 | 2.29.0 | [AEM WCM 핵심 구성 요소](https://github.com/adobe/aem-core-wcm-components) |
