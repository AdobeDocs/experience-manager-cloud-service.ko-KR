---
title: ' [!DNL Adobe Experience Manager] as a Cloud Service의 현재 유지 관리 릴리스 정보입니다.'
description: ' [!DNL Adobe Experience Manager] as a Cloud Service의 현재 유지 관리 릴리스 정보입니다.'
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: 89597ae0c54b1b2f42f597f556276700545ecd26
workflow-type: tm+mt
source-wordcount: '554'
ht-degree: 35%

---


# 유지 관리 릴리스 정보 {#maintenance-release-notes}

다음 섹션에서는 Experience Manager as a Cloud Service의 현재 유지 관리 릴리스에 대한 기술 릴리스 정보를 간략히 소개합니다.

>[!NOTE]
>
>릴리스 23122은 11월 3일에 비공개로 설정되었습니다.

## 릴리스 22943 {#22943}

다음은 2025년 10월 14일에 공개적으로 릴리스된 유지 보수 릴리스 22943에 대한 지속적인 개선 사항을 요약했습니다. 이전 유지 관리 릴리스는 릴리스 22758.

2025.10.0 기능 활성화는 이 유지 관리 릴리스에 대한 전체 기능 세트를 제공합니다. 자세한 내용은 [Experience Manager 릴리스 로드맵](https://experienceleague.adobe.com/ko/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap)을 참조하십시오.

### 개선 사항 {#enhancements-22943}

* ASSETS-57809: damAssetLucene-13의 색인 정의 업데이트입니다.
* ASSETS-36521: 일관된 후처리를 위해 DM 재업로드 워크플로우가 개선되었습니다.
* ASSETS-56400: 투명도가 있는 에셋에 대한 새 OOTB 확대/축소 PNG 렌디션이 추가되었습니다.
* ASSETS-55326: HTTP 이벤트를 통해 AI 메타데이터 폴더 구성 보기를 사용할 수 있습니다.
* ASSETS-56905: 프록시를 통해 Indesign에 연결할 수 있습니다.
* ASSETS-48286: GenStudio용 Algolia에 CAI 속성을 추가합니다.
* ASSETS-48653: 전처리 단계에서 보이지 않는 워터마크를 적용합니다.
* ASSETS-55874: 이미지 사전 설정을 scene7에서 DMWithOpenapi로 마이그레이션하는 중입니다.
* SITES-30452: /content/definition 끝점의 ASO에 대한 콘텐츠 API 개선 사항.

### 해결된 문제 {#fixed-issues-22943}

* ASSETS-56301: CSV에 PredictedTags를 포함하도록 선택적 메타데이터 내보내기가 수정되었습니다.
* ASSETS-55543: 비동기 처리 논리를 재사용 가능한 번들로 리팩터링했습니다.
* ASSETS-54789: DM ACL이 활성화되면 ACLPermissionsValidator에서 NPE가 수정되었습니다.
* ASSETS-55888: UI 렌디션 패널에 표시되는 맬웨어 렌디션을 수정했습니다.
* GRANITE-62236: 스마트 컬렉션에 대한 저장된 검색에서 키워드 현지화 문제가 수정되었습니다.
* GRANITE-61875: 콘텐츠 조각 및 자산 다운로드를 저장하지 못하는 &quot;잘못된 표현식 평가&quot; 핫픽스 문제를 수정했습니다.
* SITES-24074: 키보드 탭 탐색 중 포커스를 받는 숨겨진 모바일 탐색이 수정되었습니다.
* SITES-33611: 대량 시장을 위한 라이브 카피 개요 문제가 수정되었습니다.

#### AEM Guides {#guides-22943}

* GUIDES-31421: 여러 DITA 맵 또는 주제가 열려 있고 주제 중 하나가 닫혀 있으면 열려 있는 모든 탭이 탭 막대의 열려 있는 나머지 탭과 겹치는 **>>** 단추가 표시됩니다.
* GUIDES-33229: PDF를 생성할 때 속성 이름에 마침표가 포함된 경우 DITAVAL 파일의 필터링 규칙이 무시됩니다.
* 안내서-33720: 번역 UI의 화면을 확대할 때 번역용으로 보내기 버튼이 줄임표 아래로 이동하며 에셋을 선택하지 않아도 활성화됩니다.
* GUIDES-33590: 검토자가 검토 작업을 완료하거나 개시자가 주석을 입력하지 않고 검토 작업을 업데이트하면 전송된 알림 이메일에 가장 최근의 이전 주석이 표시됩니다.

릴리스에서 수정된 새로운 기능과 향상된 기능 및 문제에 대한 자세한 내용은 [Experience Manager Guides 릴리스 로드맵](https://experienceleague.adobe.com/ko/docs/experience-manager-guides/using/release-info/aem-guides-releases-roadmap)을 참조하십시오.

### 사용 중단된 기능 및 API {#deprecated-22943}

AEM as a Cloud Service에서 더 이상 사용되지 않는 기능과 API는 [사용 중단된 기능 및 API](/help/release-notes/deprecated-removed-features.md) 문서에 자세히 설명되어 있습니다.

### 보안 수정 {#security-22943}

AEM as a Cloud Service는 플랫폼의 보안 및 성능 최적화에 중점을 둡니다. 이 유지 관리 릴리스는 14개의 식별된 취약점을 해결하여 강력한 시스템 보호에 대한 노력을 강화합니다.

### 변경 사항 공지

* 이 릴리스에는 다음과 같은 새로운 제품 인덱스 버전이 포함되어 있습니다.
* **damAssetLucene-13**

### 임베드된 기술 {#embedded-tech-22943}

| 기술 | 버전 | 링크 |
|---|---|---|
| AEM Oak | 1.86.0 | [Oak 1.86.0 API](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.86/index.html) |
| AEM SLING API | 2.27.6 | [Apache Sling API 2.27.6 API](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 1.4.28-1.4.0 | [HTML 템플릿 언어 사양](https://github.com/adobe/htl-spec) |
| Apache HTTP 서버 | 2.4.65 | [Apache Httpd 2.4.65](https://apache.googlesource.com/httpd/+/refs/tags/2.4.65/CHANGES) |
| AEM 핵심 구성 요소 | 2.30.2 | [AEM WCM 핵심 구성 요소](https://github.com/adobe/aem-core-wcm-components) |
| Node.js | 14 (기본값) | [지원되는 Node.js 버전](https://experienceleague.adobe.com/ko/docs/experience-manager-cloud-service/content/implementing/developing/developing-with-front-end-pipelines#node-versions) |
