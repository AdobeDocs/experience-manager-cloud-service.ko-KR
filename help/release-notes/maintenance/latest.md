---
title: ' [!DNL Adobe Experience Manager] as a Cloud Service의 현재 유지 관리 릴리스 정보입니다.'
description: ' [!DNL Adobe Experience Manager] as a Cloud Service의 현재 유지 관리 릴리스 정보입니다.'
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: c8a798e1f1b7234f91682b6e5ef7072e024df022
workflow-type: tm+mt
source-wordcount: '693'
ht-degree: 28%

---


# 유지 관리 릴리스 정보 {#maintenance-release-notes}

다음 섹션에서는 Experience Manager as a Cloud Service의 현재 유지 관리 릴리스에 대한 기술 릴리스 정보를 간략히 소개합니다.

## 릴리스 18751 {#18751}

다음은 2024년 12월 11일에 공개적으로 릴리스된 유지 보수 릴리스 18751에 대한 지속적인 개선 사항을 요약한 것입니다. 이전 유지 관리 릴리스는 릴리스 18598.

2025.1.0 기능 활성화는 이 유지 관리 릴리스에 대한 전체 기능 세트를 제공합니다. 자세한 내용은 [Experience Manager 릴리스 로드맵](https://experienceleague.adobe.com/ko/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap)을 참조하십시오.

### 개선 사항 {#enhancements-18751}

* SKYOPS-88509: AEM SDK에 대한 Java 21 지원.

### 해결된 문제 {#fixed-issues-18751}

* ASSETS-42802: MFE의 [뒤로] 단추가 항상 작동하지 않으며 추가 대화 상자가 표시됩니다.
* ASSETS-44148: AEM에서 NODE_MOVED 이벤트가 수정되면 NPE가 발생할 수 있습니다.
* ASSETS-44418: 고정 올바른 환경이 skyline에 구성되지 않았습니다.
* ASSETS-44821: 업로드 이벤트에 대한 양식 URL로 인코딩된 데이터를 포함하도록 업데이트 이벤트 필터를 수정했습니다.
* CNTBF-298: 고정 컨텐츠 복사가 UUID 충돌로 실패합니다.
* CNTBF-331: [콘텐츠 복사 번들] 릴리스 2.0.14.
* FORMS-16572: java 21 SDK 빌드에 대한 워크플로우 테스트 실패를 제거합니다.
* GRANITE-36205: QS의 내부 oak 릴리스에 대한 자동 업데이트.
* GRANITE-53704: 저장소 서비스의 Sling 검색을 다시 평가합니다.
* GRANITE-54300: 최신 공개 릴리스(1.70.0)로 Oak 업데이트.
* GRANITE-54416: Filevault를 버전 3.8.2로 업데이트합니다.
* GRANITE-54462: &quot;systemready&quot;의 hc.tags를 사용하도록 SubscriberAgent를 구성합니다.
* GRANITE-54542: commons-io 종속성을 2.17.0으로 업데이트합니다.
* GRANITE-54658: QS에 fullGC에 대한 delayFactor 및 배치 크기 OSGi 구성을 추가합니다.
* GRANITE-54696: Jackrabbit API의 가져오기 범위를 넓힙니다.
* GRANITE-54803: imsauth가 활성 상태일 때 AEM에서 ClusterAtExchange를 비활성화합니다.
* GRANITE-55095: Oak을 최신 공개 릴리스(1.72.0)로 업데이트합니다.
* GUIDES-20006: 완료로 표시된 문서 상태는 새 버전을 저장하기 전에 초안으로 되돌아가며, 그 결과 문서 버전에서 완료 상태가 지속되지 않습니다.
* GUIDES-21840: 기본 PDF 출력에서 챕터 제목이 TOC에서 누락되어 잘못된 계층 구조가 발생합니다.
* 안내서-19558: 기준선에 많은 항목 또는 맵이 있는 경우 1분 후 클라우드 설정 시간 초과에서 기준선을 편집한 후 저장합니다.
* GUIDES-19733: 기준선을 사용한 맵 번역이 느려지고 결국 연결된 모든 주제 및 맵 파일 목록을 로드하지 못합니다.
* SITES-26798: Launch 자동 승격이 승격 상태(승격 날짜)를 업데이트하지 않습니다.
* SITES-27137: MSM 코어에서 Sling Commons 지표 종속성을 제거합니다.
* SKYPPS-75446: 고정 AEM에서 콘텐츠가 누락된 404개 이상의 페이지를 반환하는 경우가 있습니다.
* SKYOPS-76366: AEM 릴리스 15977 이상에서는 Jetty Threadpool 지표가 없습니다.
* SKYOPS-82371: java.io.IOException: classFile.delete() 실패.
* SKYOPS-83369: 변환 작업 실행이 번들을 생성하지 않는 경우 AEM 배포를 시작할 수 없습니다.
* SKYOPS-83910: SKYOPS-82371에서 발견된 동시성 문제가 수정되었습니다.
* SKYOPS-84821: Sling 기본 서블릿의 sling.includes.checkcontenttype 구성을 true로 설정합니다.
* SKYOPS-85798: 고정 변환 작업은 빈 색인 정의를 생성합니다.
* SKYOPS-86251: AEM Analyzer Core 1.5.6으로 업그레이드하고 변환 작업에서 제품-패키지-가져오기 분석기를 활성화합니다.
* SKYOPS-86710: Java 21 sdk 빌드에 대한 축소 테스트 오류를 제거합니다.
* SKYOPS-86745: Sling ResourceResolver 1.12.2로 업데이트합니다.
* SKYOPS-89616: Adobe Developer Console에서 기술 계정을 만들 수 없음을 수정했습니다.
* SKYOPS-89691: ASM 경고에 사용된 잘못된 아티팩트 ID가 수정되었습니다.
* SKYOPS-89699: Groovy 콘솔의 &#39;orbinson&#39; 버전에 포함된 이전 Groovy 버전에 대한 경고 누락.
* SKYOPS-88664: 다운로드한 맵 파일에 1024 제한을 초과하는 줄이 있을 경우 로그하여 사례에 대비합니다.
* SKYOPS-89734: Dispatcher 이미지 2.0.235를 릴리스합니다.

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
