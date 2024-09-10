---
title: ' [!DNL Adobe Experience Manager] as a Cloud Service의 현재 유지 관리 릴리스 정보입니다.'
description: ' [!DNL Adobe Experience Manager] as a Cloud Service의 현재 유지 관리 릴리스 정보입니다.'
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: 9323464610b804ff407f5eedf404ab2cca93a8da
workflow-type: tm+mt
source-wordcount: '572'
ht-degree: 40%

---


# 유지 관리 릴리스 정보 {#maintenance-release-notes}

다음 섹션에서는 Experience Manager as a Cloud Service 현재 유지 관리 릴리스의 기술 릴리스 정보에 대해 간략히 소개합니다.

## 릴리스 17689 {#release-17689}

다음은 2024년 9월 10일에 공개적으로 릴리스된 유지 보수 릴리스 17689에 대한 지속적인 개선 사항을 요약합니다. 이전 유지 관리 릴리스는 릴리스 17569.

2024.9.0 기능 활성화는 이 유지 관리 릴리스에 대한 전체 기능 세트를 제공합니다. 자세한 내용은 [Experience Manager 릴리스 로드맵](https://experienceleague.adobe.com/ko/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap)을 참조하십시오.

### 개선 사항 {#enhancements-17689}

* ASSETS-41404: DRM 개선 사항을 지원하도록 변경되었습니다.
* ASSETS-41621: 비동기 자산 복사 작업이 업데이트되었습니다.
* ASSETS-32166: 비동기 자산 이동 작업이 업데이트되었습니다.
* ASSETS-41429: DM OpenAPI에서 이미지 사전 설정이 지원됩니다.
* ASSETS-38968: 콘텐츠 조각 참조의 표현을 개선합니다.
* ASSETS-41787, ASSETS-41183: Assets 대량 작업 프레임워크 개선 사항.
* GRANITE-52917: 콘텐츠 복사 패키지 설치 시간을 개선하기 위해 최적화되었습니다.
* SCRNS-3980: 자산이 예약되지 않은 하위 시퀀스가 있는 플레이어에서 회색 화면을 감지합니다.

### 해결된 문제 {#fixed-issues-17689}

* ASSETS-40875: AssetDeleteHandler에 의해 기록된 가짜 NPE.
* ASSETS-42422: 단일 자산 이동에 대해 비동기 작업을 트리거하지 마십시오.
* ASSETS-41234: 검색 창을 열면 통합 셸 - 전역 탐색이 작동하지 않을 수 있습니다.
* ASSETS-42256: 통합 쉘 - 환경을 나타내는 태그/배지는 간헐적으로 작동합니다.
* ASSETS-41271: 이동 작업 중에 Assets을 불필요하게 다시 게시하지 마십시오.
* ASSETS-38894: 처리 감시기별로 재시도를 제한합니다.
* ASSETS-40815: PDF 공유 UI에서 PPT 파일을 표시하기 위해 미리 보기 링크 표현물을 사용합니다.
* ASSETS-37123: 링크 공유 대화 상자에서 에셋 미리보기를 로드할 수 없습니다.
* CQ-4358156: 삭제 중인 태그의 백링크를 업데이트합니다.
* SCRNS-4495: 고정 붙여넣기 단추가 다른 사용자 그룹에 대해 제대로 작동하지 않습니다.
* SCRNS-4512: AEMaaCS 화면에서 장치와 관련된 구성 요소를 제거합니다.
* SCRNS-4466: 채널 대시보드에서 숨기기 - 매니페스트 보기, 오프라인 콘텐츠 생성, 매니페스트 캐시 업데이트, 디스플레이 패널.
* SCRNS-4513: 목록 보기의 검색 결과 페이지에 대한 열 헤더를 추가합니다.

### 알려진 문제 {#known-issues-17689}

* FORMS-14340: FormsAndDocumentOmniSearchHandler 및 CloudStorageSubmitActionInserter를 인스턴스화하는 동안 오류가 발생했습니다. 이는 해를 미치지 않는 로그 구문입니다.
* FORMS-15818: 구성 요소 설명자 항목 &#39;OSGI-INF/com.adobe.aemfd.docmanager.impl.서버 로그에서 *.xml&#39; 구문을 찾을 수 없습니다. 이는 해를 미치지 않는 로그 구문입니다.
* SITES-23662: 게시를 트리거하는 사용자는 서버 로그의 JCR 로그 문에서 추출할 수 없습니다. 이는 개발 중인 기능으로 인해 로그에 &quot;OSGI 이벤트 일괄 처리에서 유효한 사용자 ID를 찾을 수 없음&quot; 오류가 발생하고 안전할 수 있습니다.

### 변경 사항 공지 {#change-notice-17689}

* 2024년 9월부터 AEM as a Cloud Service는 Sling Model Exporter 프레임워크를 통해 Resource Resolver의 직렬화를 비활성화합니다. 자세한 내용은 [설명서](/help/implementing/developing/hybrid/disallow-the-serialization-of-resourceresolvers-via-sling-model-exporter.md)를 참조하십시오.

### 사용 중단된 기능 및 API {#deprecated-17689}

현재 `com.day.cq.wcm.api` 업데이트가 진행 중이며, 현재 릴리스에서는 몇 가지 메서드와 클래스를 `@Deprecated`로 표시했습니다. 이러한 기능은 향후 릴리스에서 제거될 예정이므로, 해당 기능을 사용 중이라면 제안된 대체 기능으로 전환하는 것을 고려해 보시기 바랍니다.

AEM as a Cloud Service에서 더 이상 사용되지 않는 기능과 API는 [사용 중단된 기능 및 API](/help/release-notes/deprecated-removed-features.md) 문서에 자세히 설명되어 있습니다.

### 보안 수정 {#security-17689}

AEM as a Cloud Service는 플랫폼의 보안 및 성능을 최적화하는 데 사용됩니다. 이 유지 관리 릴리스는 4가지 식별된 취약점을 해결하여 강력한 시스템 보호에 대한 약속을 강화합니다.

### 임베드된 기술 {#embedded-tech-17689}

| 기술 | 버전 | 링크 |
|---|---|---|
| AEM Oak | 1.68.0 | [Oak API 1.68.0 API](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.68.0/index.html) |
| AEM SLING API | 2.27.6 | [Apache Sling API 2.27.6 API](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 1.4.24-1.4.0 | [HTML 템플릿 언어 사양](https://github.com/adobe/htl-spec) |
| AEM 핵심 구성 요소 | 2.26.0 | [AEM WCM 핵심 구성 요소](https://github.com/adobe/aem-core-wcm-components) |
