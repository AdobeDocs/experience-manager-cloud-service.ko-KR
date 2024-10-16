---
title: ' [!DNL Adobe Experience Manager] as a Cloud Service의 현재 유지 관리 릴리스 정보입니다.'
description: ' [!DNL Adobe Experience Manager] as a Cloud Service의 현재 유지 관리 릴리스 정보입니다.'
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: 6fa6fc9015624bec9113a198285531a3bdd7e29c
workflow-type: tm+mt
source-wordcount: '773'
ht-degree: 95%

---


# 유지 관리 릴리스 정보 {#maintenance-release-notes}

다음 섹션에서는 Experience Manager as a Cloud Service 현재 유지 관리 릴리스의 기술 릴리스 정보에 대해 간략히 소개합니다.

## 릴리스 18175 {#release-18175}

다음은 2024년 10월 10일에 공개적으로 릴리스된 유지 보수 릴리스 18175에 대한 지속적인 개선 사항을 요약했습니다. 이전 유지 관리 릴리스는 릴리스 17964. 문제18099 인해 릴리스 정보가 비공개로 설정되었습니다.

이 유지 관리 릴리스(2024.10.0)에 대한 기능 활성화는 전체 기능 세트를 제공합니다. 자세한 내용은 [Experience Manager 릴리스 로드맵](https://experienceleague.adobe.com/ko/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap)을 참조하십시오.

### 개선 사항 {#enhancements-18175}

* ASSETS-38322: AEM에 대한 http 요청 이벤트 활성화.
* ASSETS-41448: 그룹 매핑에 대한 FI를 지원하도록 auth.ims 번들 업데이트.
* ASSETS-41684: Assets, Foundation, Sites 및 Forms에 대한 그룹 매핑에 대한 FI를 정의하기 위해 OOB OSGI 구성 추가.
* ASSETS-43015: 최신 auth.ims 번들로 업데이트.
* CQ-4356633: “콘텐츠 전용” 툴팁에 추가 문자 추가.
* GRANITE-50948: 저장소 서비스를 위해 AEM 지원에 저장소 서비스 통합.
* GRANITE-52454: 지원 도우미 0.1.2 추가.
* GRANITE-52454: 지원 도우미 GRANITE-52454 업그레이드 AEMaaCS의 최신 릴리스를 사용하도록 지원 도우미 업그레이드.
* GRANITE-53287: 보안 권한 통합 테스트 버전 업데이트.
* GRANITE-53485: Azure Blob Storage 복제에 대한 서비스 주체 인증 지원.
* GRANITE-53514: 버전 1.0.26으로 트리 활성화 업데이트.
* GRANITE-53870: 빠른 시작을 위해 최대 JVM 버전 확인을 건너뛸 수 있는 내부 메커니즘 생성.
* GRANITE-53914: Java 17로 인한 플랫폼 테스트 실패 수정. 모듈 버전 업데이트.
* GRANITE-53966: 콘텐츠 배포에 별도의 스레드 풀 사용.
* GRANITE-54006: 2.17.2로 Jackson 업데이트.
* GRANITE-54038: AEM IMS 클라이언트 허용 목록에 Creative Cloud Enterprise IMS 클라이언트 추가.
* GRANITE-54054: com.adobe.granite.repository.impl.SystemUserValidation warnOnly에 대한 환경 변수.
* GRANITE-54266: 프로덕션 SDK에 검색 제안 서비스 누락.
* GRANITE-54274: Firefly IMS 클라이언트 수락.
* GRANITE-54300: 최신 공개 릴리스(1.70.0)로 Oak 업데이트.
* GUIDES-19069: AEM Guides 추가 기능에 guidesPeerLinkIndex 추가.
* SITES-23584: Java 17에서 Foundation 구성 요소에 대한 테스트 실패 문제 수정.
* SKYOPS-69768: SlingModels는 ResourceResolver를 역직렬화하지 않습니다.
* SKYOPS-76378: i18n에서 ResourceBundle 등록/등록 해제의 스레드 안전성 개선.
* SKYOPS-79285: 2.4.2로 Sling XSS 업데이트.
* SKYOPS-82383: 명령 실행 설명자에서 “helm-values” 변환-병합-분석 결과를 노출합니다.
* SKYOPS-84810: RDE 시작 시 “40-initialize-publish.sh” 실행 건너뜀.
* SKYOPS-84951: 변경 가능한 콘텐츠 체크섬 생성 코드 수정.
* SKYOPS-85335: 1.1.52로 org.apache.sling.jcr.repoinit 업데이트.
* SKYOPS-85336: 3.3.0으로 Sling Commons Threads 업데이트.
* SKYOPS-86329: Java 21 SDK를 지원하도록 플랫폼 테스트 모듈 버전 업데이트.

### 해결된 문제 {#fixed-issues-18175}

* CNTBF-298: CC에서 내보낸 패키지에서 jcr:uuid 제거.
* SKYOPS-83910: SKYOPS-82371에서 발견된 동시성 문제 수정.
* GRANITE-52876: com.adobe.granite.ui.content 0.8.1448로 업데이트.
* GUIDES-14445: Node.js에 대한 종속성을 가져오는 것과 관련된 오류로 인해 기본 PDF 생성이 실패합니다.
* GUIDES-16961: 웹 편집기의 기준선 및 번역 대시보드에서 `<conref>`를 포함한 제목이 확인되지 않습니다.
* GUIDES-17283: **topicmeta에 추가된 메타데이터 사용** 옵션을 선택하면 메타데이터 속성이 기본 PDF 출력의 문서 속성에 전파되지 않습니다.
* GUIDES-17793: 게시된 콘텐츠의 대량 활성화 도중 참조된 PDF가 **대량 게시 대시보드**&#x200B;에서 활성화되지 않습니다.

릴리스에서 수정된 새로운 Guides 기능과 향상된 기능 및 문제에 대한 자세한 내용은 [Experience Manager Guides 릴리스 로드맵](https://experienceleague.adobe.com/ko/docs/experience-manager-guides/using/release-info/aem-guides-releases-roadmap)을 참조하십시오.

### 알려진 문제 {#known-issues-18175}

* FORMS-15818: 구성 요소 설명자 항목 `OSGI-INF/com.adobe.aemfd.docmanager.impl.*.xml` 서버 로그에서 진술을 찾을 수 없음. 이는 해를 미치지 않는 로그 구문입니다.

### 사용 중단된 기능 및 API {#deprecated-18175}

AEM as a Cloud Service에서 더 이상 사용되지 않는 기능과 API는 [사용 중단된 기능 및 API](/help/release-notes/deprecated-removed-features.md) 문서에 자세히 설명되어 있습니다.

최근 사용이 중단된 기능이나 사용이 중단되는 과정에 있는 기능을 요약한 내용은 다음과 같습니다.

#### JavaScript Use API {#javascript-use-api}

[JavaScript Use API](https://github.com/adobe/htl-spec/blob/master/SPECIFICATION.md#42-javascript-use-api)는 사용자가 API를 활용하는 코드를 디버깅하고 유지 관리하는 데 어려움을 겪고 Java 대안과 비교했을 때 성능이 제한되어 공식적으로 더 이상 사용되지 않습니다.

더 나은 성능, 쉬운 디버깅 및 더 나은 장기 지원을 제공하는 [Java Use API](https://experienceleague.adobe.com/ko/docs/experience-manager-htl/content/java-use-api)로 전환해야 합니다.

#### com.day.cq.wcm.api {#com-day-cq-wcm-api}

Adobe는 `com.day.cq.wcm.api`를 업데이트하고 있습니다. 최신 릴리스에서는 일부 메서드와 클래스가 `@Deprecated`로 표시되었습니다. 이러한 메서드와 클래스는 향후 릴리스에서 제거될 예정입니다. 제안된 대안으로 전환하는 것이 좋습니다.

#### org.apache.jackrabbit.oak.plugins.blob {#org.apache.jackrabbit.oak.plugins.blob}

* GRANITE-54165: 공개 API에서 org.apache.jackrabbit.oak.plugins.blob을 더 이상 사용하지 않습니다.

### 보안 수정 {#security-18175}

AEM as a Cloud Service는 플랫폼의 보안 및 성능을 최적화하는 데 사용됩니다. 이 유지 관리 릴리스에서는 강력한 시스템 보호에 대한 노력의 일환으로 식별된 취약점 2개가 해결되었습니다.

### 임베드된 기술 {#embedded-tech-18175}

| 기술 | 버전 | 링크 |
|---|---|---|
| AEM Oak | 1.70.0 | [Oak API 1.70.0 API](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.70.0/index.html) |
| AEM SLING API | 2.27.6 | [Apache Sling API 2.27.6 API](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 1.4.24-1.4.0 | [HTML 템플릿 언어 사양](https://github.com/adobe/htl-spec) |
| AEM 핵심 구성 요소 | 2.27.0 | [AEM WCM 핵심 구성 요소](https://github.com/adobe/aem-core-wcm-components) |
