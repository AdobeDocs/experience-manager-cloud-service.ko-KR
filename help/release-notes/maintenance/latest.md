---
title: ' [!DNL Adobe Experience Manager] as a Cloud Service의 현재 유지 관리 릴리스 정보입니다.'
description: ' [!DNL Adobe Experience Manager] as a Cloud Service의 현재 유지 관리 릴리스 정보입니다.'
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: 3686697c85273ccc13e80b8d7f4ad1ff3c79845d
workflow-type: ht
source-wordcount: '632'
ht-degree: 100%

---


# 유지 관리 릴리스 정보 {#maintenance-release-notes}

다음 섹션에서는 Experience Manager as a Cloud Service의 현재 유지 관리 릴리스에 대한 기술 릴리스 정보를 간략히 소개합니다.

## 릴리스 21706 {#21706}

2025년 7월 24일에 릴리스된 유지 관리 릴리스 21706의 지속적인 개선 사항이 아래에 요약되어 있습니다. 이전 유지 관리 릴리스는 릴리스 21570이었습니다.

>[!NOTE]
>
>릴리스 21644는 비공개로 전환되었으며 릴리스 21706으로 대체되었습니다.

이 유지 관리 릴리스(2025.7.0)에 대한 기능 활성화는 전체 기능 세트를 제공합니다. 자세한 내용은 [Experience Manager 릴리스 로드맵](https://experienceleague.adobe.com/ko/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap)을 참조하십시오.

### 개선 사항 {#enhancements-21706}

* ASSETS-39377: Assets Bulk Importer에서 원격 스토리지의 429건 처리를 개선합니다.
* ASSETS-46026: 메타데이터 내보내기에 대해 구성 가능한 최대 깊이입니다.
* ASSETS-49172: 동적 미디어 템플릿 자산은 폴더에서 메타데이터를 상속해야 합니다.
* ASSETS-50209: DM 템플릿에서 하위 문자열 지원합니다.
* ASSETS-52326: Assets의 제목 표시 기본 설정을 지정하는 AEM Assets 구성 페이지입니다.
* ASSETS-52805: 대량 작업에 대한 CSV 출력/다운로드 지원을 추가합니다.
* ASSETS-52873: 폴더 속성에 새 구성을 추가하여 해당 폴더에 대한 AI 처리를 비활성화합니다.
* ASSETS-53535: YouTube 비디오 업로드 성능이 개선되었습니다.
* ASSETS-53612: Assets Omnisearch의 하이브리드 검색에 대한 제어입니다.
* GRANITE-60183: commons-fileupload 종속성을 1.6.0으로 업데이트합니다.
* GRANITE-60287: QS를 Jackrabbit 2.22.1로 업데이트합니다.
* SITES-30452: ASO가 포함된 콘텐츠 API - 제목 및 설명 제안입니다.
* SITES-31677: 사용자 정의 작업 영역이 AEM 콘텐츠 조각을 Target으로 내보낼 수 있도록 지원합니다.
* SKYOPS-112741: AEM-CS SDK에서 `com.adobe.granite.product.support` 번들을 제거합니다.

### 해결된 문제 {#fixed-issues-21706}

* ASSETS-12882: 뷰어 사전 설정을 연 후 UI 정렬 문제가 발생합니다.
* ASSETS-48958: Sites 로컬 AEM에서 Asset Sync로 인해 게시 상태가 변경되는 문제가 있습니다.
* ASSETS-50856: `dam:processingAttempts`가 completeUpload에서 재설정되지 않습니다.
* ASSETS-51604: 링크 공유 보고서 CSV에 “공유 대상” 데이터가 없습니다.
* ASSETS-51783: 검색 쿼리를 사용하여 구성을 찾을 수 없는 경우 `/conf/global`에서 DM 구성으로 대체합니다.
* ASSETS-51857: 자산 테이블 항목을 다시 정렬할 수 없습니다.
* ASSETS-52169: 새로운 BAT 머신 렌디션이 자산 다운로드에 잘못 포함되었습니다.
* ASSETS-52229: 클라우드 서비스인 AEM에서 자산 보고서에 대한 받은 편지함 알림이 누락되었습니다.
* ASSETS-52399: com.day.cq.dam.api의 버전 업데이트로 인해 고객 코드가 손상될 수 있습니다.
* ASSETS-52780: 토글을 활성화하지 않아도 자산을 미리 볼 수 있도록 표시할 수 있습니다.
* ASSETS-52866: 마이그레이션된 DM 비디오가 DM 동기화가 비활성화된 폴더에서 처리 상태로 남아 있습니다.
* ASSETS-53237: 이미지 사전 설정 편집기의 색상 프로필 드롭다운이 비어 있습니다.
* ASSETS-53240: 자산 보고서 - 동적 미디어에서 자산 렌디션 크기를 가져오는 동안 디스크 사용량이 실패합니다.
* ASSETS-53446: NPE로 인해 간헐적으로 YouTube 인증 토큰 새로 고침이 실패합니다.
* ASSETS-53827: ACL 유효성 검사가 혼합 미디어 집합 저장을 차단합니다.
* ASSETS-5403: 게시 인스턴스에서 사용되는 Dynamicmedia clientlibs에는 `allowProxy=true`가 있어야 합니다.
* ASSETS-54261: 메타데이터 가져오기에서 연결이 누출되고 파일 다운로드에 실패하면 차단됩니다.
* CQ-4359863: 콘텐츠 조각 편집기/자산 편집기에서 키워드 순서가 맞지 않아 태그 검색이 중단됩니다.
* CQ-4359958: openapi-support를 AEM 6.5.22.0 이상과 호환되도록 합니다.
* CQ-4360256: `/adobe` 서블릿 컨텍스트를 통해 처리되는 HTTP 요청에 대한 요청 경로에 서블릿 컨텍스트 경로를 포함합니다.
* CQ-4360317: 응답을 빌드할 때 일몰 날짜 헤더를 설정하는 방법을 추가합니다.
* GRANITE-60311: AEM SDK 빠른 시작 – “OSGi 설치 관리자 구성 프린터”에 대한 NPE입니다.
* GS-15285: 사용자가 비활성화된 것으로 표시됩니다.

### 알려진 문제 {#known-issues-21706}

없음.

### 사용 중단된 기능 및 API {#deprecated-21706}

AEM as a Cloud Service에서 더 이상 사용되지 않는 기능과 API는 [사용 중단된 기능 및 API](/help/release-notes/deprecated-removed-features.md) 문서에 자세히 설명되어 있습니다.

### 보안 수정 {#security-21706}

AEM as a Cloud Service는 플랫폼의 보안 및 성능 최적화에 중점을 둡니다. 이 유지 관리 릴리스에서는 강력한 시스템 보호에 대한 노력의 일환으로 식별된 취약점 4개가 해결되었습니다.

### 임베드된 기술 {#embedded-tech-21706}

| 기술 | 버전 | 링크 |
|---|---|---|
| AEM Oak | 1.80.0 | [Oak API 1.80.0 API](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.80/index.html) |
| AEM SLING API | 2.27.6 | [Apache Sling API 2.27.6 API](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 1.4.28-1.4.0 | [HTML 템플릿 언어 사양](https://github.com/adobe/htl-spec) |
| Apache HTTP 서버 | 2.4.63 | [Apache Httpd 2.4.63](https://github.com/apache/httpd/blob/2.4.63/CHANGES) |
| AEM 핵심 구성 요소 | 2.29.0 | [AEM WCM 핵심 구성 요소](https://github.com/adobe/aem-core-wcm-components) |
