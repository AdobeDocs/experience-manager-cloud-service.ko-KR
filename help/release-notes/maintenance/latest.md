---
title: ' [!DNL Adobe Experience Manager] as a Cloud Service의 현재 유지 관리 릴리스 정보입니다.'
description: ' [!DNL Adobe Experience Manager] as a Cloud Service의 현재 유지 관리 릴리스 정보입니다.'
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: c8a798e1f1b7234f91682b6e5ef7072e024df022
workflow-type: ht
source-wordcount: '693'
ht-degree: 100%

---


# 유지 관리 릴리스 정보 {#maintenance-release-notes}

다음 섹션에서는 Experience Manager as a Cloud Service의 현재 유지 관리 릴리스에 대한 기술 릴리스 정보를 간략히 소개합니다.

## 릴리스 18751 {#18751}

2024년 12월 11일에 릴리스된 유지 관리 릴리스 18751의 지속적인 개선 사항이 아래에 요약되어 있습니다. 이전 유지 관리 릴리스는 릴리스 18598이었습니다.

이 유지 관리 릴리스(2025.1.0)에 대한 기능 활성화는 전체 기능 세트를 제공합니다. 자세한 내용은 [Experience Manager 릴리스 로드맵](https://experienceleague.adobe.com/ko/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap)을 참조하십시오.

### 개선 사항 {#enhancements-18751}

* SKYOPS-88509: Java 21 AEM SDK 지원

### 해결된 문제 {#fixed-issues-18751}

* ASSETS-42802: MFE의 뒤로 버튼이 작동하지 않으며 추가 대화 상자가 표시됩니다.
* ASSETS-44148: AEM의 NODE_MOVED 이벤트가 NPE를 일으킬 수 있습니다.
* ASSETS-44418: Skyline에 올바른 env가 구성되어 있지 않은 문제가 해결되었습니다.
* ASSETS-44821: 업로드 이벤트에 대한 form-url-encoded 데이터를 포함하도록 업데이트 이벤트 필터를 수정했습니다.
* CNTBF-298: UUID 충돌로 인해 고정 콘텐츠 복사 실패 문제가 해결되었습니다.
* CNTBF-331: [content-copy-bundle] 릴리스 2.0.14.
* FORMS-16572: Java 21 SDK 빌드에 대한 Workflow 테스트 실패가 해결되었습니다.
* GRANITE-36205: QS에서 내부 Oak 릴리스에 대한 업데이트가 자동화되었습니다.
* GRANITE-53704: 저장소 서비스에서 Sling Discovery를 다시 평가합니다.
* GRANITE-54300: 최신 공개 릴리스(1.70.0)로 Oak가 업데이트되었습니다.
* GRANITE-54416: 버전 3.8.2로 Filevault가 업데이트되었습니다.
* GRANITE-54462: “systemready”의 hc.tags를 사용하도록 SubscriberAgents가 구성되었습니다.
* GRANITE-54542: commons-io 종속성을 2.17.0으로 업데이트했습니다.
* GRANITE-54658: QS의 fullGC에 대한 delayFactor 및 batch-size OSGi 구성이 추가되었습니다.
* GRANITE-54696: Jackrabbit API의 가져오기 범위가 확대되었습니다.
* GRANITE-54803: imsauth가 활성화되어 있을 때 AEM에서 ClusterAtExchange를 비활성화합니다.
* GRANITE-55095: 최신 공개 릴리스(1.72.0)로 Oak가 업데이트되었습니다.
* GUIDES-20006: 완료로 표시된 문서 상태가 새 버전을 저장하기 전에 초안 상태로 되돌아가므로 완료 상태가 모든 문서 버전에서 유지되지 않습니다.
* GUIDES-21840: 기본 PDF 출력에서 TOC에 챕터 제목이 누락되어 계층 구조가 잘못됩니다.
* GUIDES-19558: 클라우드 설정에서 기준선을 편집한 다음 저장할 때 기준선에 주제나 맵이 너무 많으면 1분 후 시간 초과가 발생합니다.
* GUIDES-19733: 기준선을 사용하는 맵 번역이 느려지고 결국 관련 주제와 맵 파일 목록을 모두 로드하지 못합니다.
* SITES-26798: 자동 프로모션 실행 시 프로모션 상태(프로모션 날짜)가 업데이트되지 않습니다.
* SITES-27137: MSM 코어에서 Sling 일반 지표 종속성을 제거합니다.
* SKYOPS-75446: AEM에서 가끔 404 오류나 콘텐츠가 누락된 페이지를 반환하는 문제가 해결되었습니다.
* SKYOPS-76366: AEM 릴리스 15977 이상에서 Jetty Threadpool 지표가 없습니다.
* SKYOPS-82371: java.io.IOException: classFile.delete() 실패.
* SKYOPS-83369: 변환 작업 실행이 번들을 생성하지 않으면 AEM 배포가 시작되지 않습니다.
* SKYOPS-83910: SKYOPS-82371에서 발견된 동시성 문제가 해결되었습니다.
* SKYOPS-84821: Sling Main Servlet의 sling.includes.checkcontenttype 구성을 true로 설정합니다.
* SKYOPS-85798: 고정 변환 작업이 빈 인덱스 정의를 생성합니다.
* SKYOPS-86251: AEM Analyser Core 1.5.6으로 업그레이드하고 변환 작업에서 product-package-import 분석기를 활성화합니다.
* SKYOPS-86710: Java 21 SDK 빌드에 대한 Minify 테스트 실패 문제가 해결되었습니다.
* SKYOPS-86745: Sling ResourceResolver 1.12.2로 업데이트되었습니다.
* SKYOPS-89616: Adobe Developer Console에서 기술 계정을 만들 수 없는 문제가 해결되었습니다.
* SKYOPS-89691: ASM 경고에 잘못된 아티팩트 ID가 사용되는 문제가 해결되었습니다.
* SKYOPS-89699: Groovy Console의 “orbinson” 플레이버에 임베드된 이전 Groovy 버전에 대한 경고가 누락됩니다.
* SKYOPS-88664: 다운로드한 맵 파일의 줄이 1024줄 제한을 초과하는 경우를 기록하고 보호합니다.
* SKYOPS-89734: Dispatcher 이미지 2.0.235가 릴리스되었습니다.

Experience Manager Guides에서 수정된 새로운 기능과 향상된 기능에 대한 자세한 내용은 [Experience Manager Guides 릴리스 로드맵](https://experienceleague.adobe.com/ko/docs/experience-manager-guides/using/release-info/aem-guides-releases-roadmap)을 참조하십시오.

### 알려진 문제 {#known-issues-18751}

없음.

### 사용 중단된 기능 및 API {#deprecated-18751}

AEM as a Cloud Service에서 더이상 사용되지 않는 기능과 API는 [사용 중단된 기능 및 API](/help/release-notes/deprecated-removed-features.md) 문서에 자세히 설명되어 있습니다.

### 보안 수정 {#security-18751}

AEM as a Cloud Service는 플랫폼의 보안 및 성능 최적화에 중점을 둡니다. 이 유지 관리 릴리스에서는 강력한 시스템 보호에 대한 노력의 일환으로 식별된 취약점 3가지가 해결되었습니다.

### 임베드된 기술 {#embedded-tech-18751}

| 기술 | 버전 | 링크 |
|---|---|---|
| AEM Oak | 1.72.0 | [Oak API 1.72.0 API](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.72.0/index.html) |
| AEM SLING API | 2.27.6 | [Apache Sling API 2.27.6 API](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 1.4.24-1.4.0 | [HTML 템플릿 언어 사양](https://github.com/adobe/htl-spec) |
| AEM 핵심 구성 요소 | 2.27.0 | [AEM WCM 핵심 구성 요소](https://github.com/adobe/aem-core-wcm-components) |
