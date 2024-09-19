---
title: ' [!DNL Adobe Experience Manager] as a Cloud Service의 현재 유지 관리 릴리스 정보입니다.'
description: ' [!DNL Adobe Experience Manager] as a Cloud Service의 현재 유지 관리 릴리스 정보입니다.'
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: 9323464610b804ff407f5eedf404ab2cca93a8da
workflow-type: ht
source-wordcount: '572'
ht-degree: 100%

---


# 유지 관리 릴리스 정보 {#maintenance-release-notes}

다음 섹션에서는 Experience Manager as a Cloud Service 현재 유지 관리 릴리스의 기술 릴리스 정보에 대해 간략히 소개합니다.

## 릴리스 17689 {#release-17689}

2024년 9월 10일에 릴리스된 유지 관리 릴리스 17689의 지속적인 개선 사항이 아래에 요약되어 있습니다. 이전 유지 관리 릴리스는 릴리스 17569이었습니다.

이 유지 관리 릴리스(2024.9.0)에 대한 기능 활성화는 전체 기능 세트를 제공합니다. 자세한 내용은 [Experience Manager 릴리스 로드맵](https://experienceleague.adobe.com/ko/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap)을 참조하십시오.

### 개선 사항 {#enhancements-17689}

* ASSETS-41404: DRM 개선을 지원하기 위한 변경 사항입니다.
* ASSETS-41621: 비동기 자산 복사 작업이 업데이트되었습니다.
* ASSETS-32166: 비동기 자산 이동 작업이 업데이트되었습니다.
* ASSETS-41429: DM OpenAPI에서 이미지 사전 설정이 지원됩니다.
* ASSETS-38968: 콘텐츠 조각 참조의 표현이 개선되었습니다.
* ASSETS-41787, ASSETS-41183: 자산 일괄 작업 프레임워크가 개선되었습니다.
* GRANITE-52917: 콘텐츠 복사 패키지 설치 시간을 개선하기 위한 최적화가 수행되었습니다.
* SCRNS-3980: 자산이 예약되지 않은 하위 시퀀스가 있는 플레이어에서 회색 화면이 감지됩니다.

### 해결된 문제 {#fixed-issues-17689}

* ASSETS-40875: AssetDeleteHandler에서 잘못된 NPE가 기록됩니다.
* ASSETS-42422: 단일 자산 이동에 대해 비동기 작업이 트리거되는 것을 방지합니다.
* ASSETS-41234: 통합 셸 - 검색 창이 열려 있을 때 전역 탐색이 종종 작동되지 않습니다.
* ASSETS-42256: 통합 셸 - 환경을 나타내는 태그/배지가 간헐적으로 작동합니다.
* ASSETS-41271: 이동 작업 중 불필요한 자산 재게시를 방지합니다.
* ASSETS-38894: 처리 워치도그로 재시도를 제한합니다.
* ASSETS-40815: 링크 공유 UI에서 PPT 파일을 표시하기 위해 PDF 미리보기를 사용합니다.
* ASSETS-37123: 링크 공유 대화 상자에서 자산 미리보기를 로드할 수 없습니다.
* CQ-4358156: 삭제되는 태그의 백링크가 업데이트됩니다.
* SCRNS-4495: 다른 사용자 그룹에서 붙여넣기 버튼이 제대로 작동하지 않는 문제가 수정되었습니다.
* SCRNS-4512: AEMaaCS 화면에서 디바이스와 관련된 구성 요소가 제거됩니다.
* SCRNS-4466: 채널 대시보드에서 매니페스트를 숨기거나 보고, 오프라인 콘텐츠를 생성하고, 매니페스트 캐시를 업데이트하고, 패널을 표시합니다.
* SCRNS-4513: 목록 보기에서 검색 결과 페이지에 열 헤더를 추가합니다.

### 알려진 문제 {#known-issues-17689}

* FORMS-14340: FormsAndDocumentOmniSearchHandler 및 CloudStorageSubmitActionInserter를 인스턴스화하는 도중 오류가 발생했습니다. 이는 해를 미치지 않는 로그 구문입니다.
* FORMS-15818: 구성 요소 설명자 항목 &#39;OSGI-INF/com.adobe.aemfd.docmanager.impl.*.xml&#39; 이 서버 로그에서 구문을 찾을 수 없습니다. 이는 해를 미치지 않는 로그 구문입니다.
* SITES-23662: 게시를 트리거하는 사용자를 서버 로그의 JCR 로그 구문에서 추출할 수 없습니다. 이는 로그에 간헐적이고 해를 미치지 않는 “일괄 OSGI 이벤트에서 유효한 사용자 ID를 찾을 수 없습니다.”라는 오류가 발생할 수 있는 개발 중인 기능에 대한 것입니다.

### 변경 사항 공지 {#change-notice-17689}

* 2024년 9월부터 AEM as a Cloud Service는 Sling Model Exporter 프레임워크를 통해 Resource Resolver의 직렬화를 비활성화합니다. 자세한 내용은 [설명서](/help/implementing/developing/hybrid/disallow-the-serialization-of-resourceresolvers-via-sling-model-exporter.md)를 참조하십시오.

### 사용 중단된 기능 및 API {#deprecated-17689}

현재 `com.day.cq.wcm.api` 업데이트가 진행 중이며, 현재 릴리스에서는 몇 가지 메서드와 클래스를 `@Deprecated`로 표시했습니다. 이러한 기능은 향후 릴리스에서 제거될 예정이므로, 해당 기능을 사용 중이라면 제안된 대체 기능으로 전환하는 것을 고려해 보시기 바랍니다.

AEM as a Cloud Service에서 더 이상 사용되지 않는 기능과 API는 [사용 중단된 기능 및 API](/help/release-notes/deprecated-removed-features.md) 문서에 자세히 설명되어 있습니다.

### 보안 수정 {#security-17689}

AEM as a Cloud Service는 플랫폼의 보안 및 성능을 최적화하는 데 사용됩니다. 이 유지 관리 릴리스에서는 강력한 시스템 보호에 대한 노력의 일환으로 식별된 취약점 4개가 해결되었습니다.

### 임베드된 기술 {#embedded-tech-17689}

| 기술 | 버전 | 링크 |
|---|---|---|
| AEM Oak | 1.68.0 | [Oak API 1.68.0 API](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.68.0/index.html) |
| AEM SLING API | 2.27.6 | [Apache Sling API 2.27.6 API](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 1.4.24-1.4.0 | [HTML 템플릿 언어 사양](https://github.com/adobe/htl-spec) |
| AEM 핵심 구성 요소 | 2.26.0 | [AEM WCM 핵심 구성 요소](https://github.com/adobe/aem-core-wcm-components) |
