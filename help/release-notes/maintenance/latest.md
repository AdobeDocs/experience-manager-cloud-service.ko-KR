---
title: ' [!DNL Adobe Experience Manager] as a Cloud Service의 현재 유지 관리 릴리스 정보입니다.'
description: ' [!DNL Adobe Experience Manager] as a Cloud Service의 현재 유지 관리 릴리스 정보입니다.'
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: 1d6a54f87d55179c11c7ccc7766eeeb475674f05
workflow-type: tm+mt
source-wordcount: '446'
ht-degree: 40%

---


# 유지 관리 릴리스 정보 {#maintenance-release-notes}

다음 섹션에서는 Experience Manager as a Cloud Service의 현재 유지 관리 릴리스에 대한 기술 릴리스 정보를 간략히 소개합니다.

## 릴리스 19567 {#19567}

다음은 2025년 2월 18일에 공개적으로 릴리스된 유지 보수 릴리스 19567에 대한 지속적인 개선 사항을 요약했습니다. 이전 유지 관리 릴리스는 릴리스 19352.

2025.2.0 기능 활성화는 이 유지 관리 릴리스에 대한 전체 기능 세트를 제공합니다. 자세한 내용은 [Experience Manager 릴리스 로드맵](https://experienceleague.adobe.com/ko/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap)을 참조하십시오.

### 개선 사항 {#enhancements-19567}

* GRANITE-56650: 컨텐츠 배포는 몇 번 다시 시도한 후에만 차단된 대기열에 신호를 전송해야 합니다
* SKYOPS-89616: Adobe Developer Console에서 최대 40개의 기술 계정을 만들 수 있습니다.

### 해결된 문제 {#fixed-issues-19567}

* CNTBF-232: 필수 jcr:content 하위를 포함하도록 딥 패키지 nt:file 노드
* CQ-4358930: 여러 다중 필드로 페이지 속성을 로드하는 동안 성능 문제
* GRANITE-55960: AEM as Cloud Service의 Coral Select Field 성능 문제
* GRANITE-56197: 새 TreeActivation 워크플로 단계에서 대형 플랫 폴더 구조의 자산을 일괄 처리하지 않습니다.

#### AEM 안내서 {#guides}

* GUIDES-23526: 폴더 프로필에서 조건을 업데이트할 때 모든 조건 그룹이 손실되고 조건이 병합됩니다.
* GUIDES-22574: 외부 링크에 UUID가 포함되어 있는 경우 사후 처리로 이동하여 외부 링크를 UUID 링크로 변환하므로 편집기와 게시 사이트에서도 링크가 끊어집니다.
* GUIDES-24983: 외부 제품(예: MS PowerPoint)에서 이미지를 복사하여 Guides에 붙여넣을 때 파일 브레이크에서 사용할 자산을 즉시 업로드하는 기능이 제공됩니다.
* GUIDES-21772: **청크 특성**&#x200B;이 **to-content**(으)로 설정된 콘텐츠에 대해 기본 PDF 생성이 실패합니다.
* GUIDES-23964: **속성 편집**&#x200B;을 선택할 때 기준선 대화 상자에 동적 기준선에 대해 이전에 저장된 기준이 표시되지 않습니다.
* GUIDES-19067: 폴더 프로필을 복제할 때 해당 관리자 목록도 원래 폴더 프로필에서 복사됩니다

릴리스에서 수정된 새로운 기능과 향상된 기능 및 문제에 대한 자세한 내용은 [Experience Manager Guides 릴리스 로드맵](https://experienceleague.adobe.com/ko/docs/experience-manager-guides/using/release-info/aem-guides-releases-roadmap)을 참조하십시오.

### 알려진 문제 {#known-issues-19567}

없음.

### 사용 중단된 기능 및 API {#deprecated-19567}

AEM as a Cloud Service에서 더이상 사용되지 않는 기능과 API는 [사용 중단된 기능 및 API](/help/release-notes/deprecated-removed-features.md) 문서에 자세히 설명되어 있습니다.

### 보안 수정 {#security-19567}

AEM as a Cloud Service는 플랫폼의 보안 및 성능 최적화에 중점을 둡니다. 이 유지 관리 릴리스에서는 강력한 시스템 보호에 대한 노력의 일환으로 식별된 취약점 21개를 해결했습니다.

### 임베드된 기술 {#embedded-tech-19567}

| 기술 | 버전 | 링크 |
|---|--------------|-------------------------------------------------------------------------------------------------------------------|
| AEM Oak | 1.76.0 | [Oak API 1.76.0 API](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.76.0/index.html) |
| AEM SLING API | 2.27.6 | [Apache Sling API 2.27.6 API](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 1.4.26-1.4.0 | [HTML 템플릿 언어 사양](https://github.com/adobe/htl-spec) |
| AEM 핵심 구성 요소 | 2.27.0 | [AEM WCM 핵심 구성 요소](https://github.com/adobe/aem-core-wcm-components) |
