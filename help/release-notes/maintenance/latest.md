---
title: ' [!DNL Adobe Experience Manager] as a Cloud Service의 현재 유지 관리 릴리스 정보입니다.'
description: ' [!DNL Adobe Experience Manager] as a Cloud Service의 현재 유지 관리 릴리스 정보입니다.'
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: ea7e027b5247b64e78da1d14e4e602f39a37e4bd
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# 유지 관리 릴리스 정보 {#maintenance-release-notes}

다음 섹션에서는 Experience Manager as a Cloud Service 현재 유지 관리 릴리스의 기술 릴리스 정보에 대해 간략히 소개합니다.

## 릴리스 18099 {#release-18099}

다음은 2024년 10월 9일에 공개적으로 릴리스된 유지 보수 릴리스 18099에 대한 지속적인 개선 사항을 요약합니다. 이전 유지 관리 릴리스는 릴리스 17964.

이 유지 관리 릴리스(2024.10.0)에 대한 기능 활성화는 전체 기능 세트를 제공합니다. 자세한 내용은 [Experience Manager 릴리스 로드맵](https://experienceleague.adobe.com/ko/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap)을 참조하십시오.

### 개선 사항 {#enhancements-18099}

* ASSETS-43015: 최신 auth.ims 번들로 업데이트합니다.
* ASSETS-41684: src/main/features/docker/ethos/base-ims-oauth.json을 업데이트합니다.
* ASSETS-38322: AEM에 대해 http 요청 이벤트 활성화.
* ASSETS-41684: OOB OSGI 구성을 추가하여 Assets, Foundation, Sites 및 Forms에 대한 FI 대 그룹 매핑을 정의합니다.
* ASSETS-41448: 그룹 매핑에 대한 FI를 지원하도록 auth.ims 번들을 업데이트합니다.
* CQ-4356633: &quot;콘텐츠만&quot; 툴팁에 문자를 더 추가합니다.
* SITES-23584: Java 17에서 기초 구성 요소 테스트가 실패합니다.
* GUIDES-19069: AEM Guides 추가 기능에 대한 guidesPeerLinkIndex를 추가합니다.
* GRANITE-54300: Oak을 최신 공개 릴리스(1.70.0)로 업데이트합니다.
* GRANITE-54274: Firefly IMS 클라이언트를 허용합니다.
* GRANITE-36205: 내부 Oak 릴리스 버전을 최신 버전으로 업데이트합니다.
* GRANITE-45298: 권한이 낮은 사용자는 JS 없이 XSS 방식으로 악의적인 양식을 작성하여 RCE를 얻을 수 있습니다.
* GRANITE-54266: 프로덕션 SDK에 검색 제안자 서비스가 없습니다.
* GRANITE-50948 - AEM에 저장소 서비스 통합 로컬 개발을 위해 대체 저장소 서비스를 추가합니다.
* GRANITE-53966: 컨텐츠 배포를 위해 별도의 스레드 풀을 사용합니다.
* GRANITE-53514: 트리 활성화 1.0.26.
* GRANITE-54054: com.adobe.granite.repository.impl.SystemUserValidation warnOnly에 대한 환경 변수.
* GRANITE-50948: 저장소 서비스를 위한 AEM 지원에 저장소 서비스를 통합합니다.
* GRANITE-52454: 지원 도우미 0.1.2 추가.
* GRANITE-53514: 트리 활성화 1.0.26.
* GRANITE IMS 54038: Creative Cloud Enterprise IMS 클라이언트를 AEM IMS-허용 목록에 추가하다에 추가합니다.
* GRANITE-36205: 내부 Oak 릴리스 버전을 최신 버전으로 업데이트합니다.
* GRANITE-53485: 복제 Azure Blob 스토리지에 대한 서비스 주체 인증을 지원합니다.
* GRANITE-54006: Jackson을 2.17.2로 업데이트합니다.
* GRANITE-53287: 보안 권한 통합 테스트 버전을 업데이트하는 중입니다.
* GRANITE-53914: Java 17의 플랫폼 테스트 실패 모듈 버전이 업데이트되었습니다.
* GRANITE-53870: 빠른 시작에 대한 최대 JVM 버전 검사를 건너뛰기 위한 내부 메커니즘을 생성합니다.
* GRANITE-52454: AEMaaCS용 최신 릴리스를 사용하도록 Support Helper GRANITE-52454 업그레이드 지원 Helper.
* SKYOPS-85335: org.apache.sling.jcr.repoinit를 1.1.52로 업데이트합니다.
* SKYOPS-85336: Sling Commons Threads을 3.3.0으로 업데이트합니다.
* SKYOPS-76378: i18n에서 ResourceBundle 등록/등록 취소의 스레드 안전성을 개선합니다.
* SKYOPS-84951: 변경 가능한 콘텐츠 체크섬 생성 코드가 잘못되었습니다.
* SKYOPS-82383: 명령 실행 설명자에 &#39;helm-values&#39; 변환-병합-분석 결과를 표시합니다.
* SKYOPS-86329: java 21 sdk 지원을 위한 플랫폼 테스트 모듈의 버전을 업데이트합니다.
* SKYOPS-69768: SlingModels는 ResourceResolver를 deserialize하지 않습니다.
* SKYOPS-84810: RDE를 시작할 때 &quot;40-initialize-publish.sh&quot; 실행을 건너뜁니다.
* SKYOPS-79285: Sling XSS를 2.4.2로 업데이트

### 해결된 문제 {#fixed-issues-18099}

* CNTBF-298: CC 내보낸 패키지에서 jcr:uuid를 제거합니다.
* SKYOPS-83910: SKYOPS-82371에서 발견된 동시성 문제를 수정합니다.
* GRANITE-52876: com.adobe.granite.ui.content 0.8.1448로 업데이트합니다.
* GRANITE-53088: SITES-11992의 수정으로 도입된 회귀.
* GUIDES-14445: Node.js에 대한 종속성 가져오기와 관련된 오류로 인해 기본 PDF 생성에 실패합니다.
* GUIDES-16961: `<conref>`이(가) 있는 제목이 웹 편집기의 기본 및 번역 대시보드에서 확인되지 않습니다.
* GUIDES-17283: **topicmeta에 추가된 메타데이터 사용** 옵션을 선택할 때 메타데이터 속성이 기본 PDF 출력의 문서 고유성에 전파되지 않습니다.
* GUIDES-17793: 게시된 콘텐츠의 일괄 활성화 중에 **Publish 대시보드 일괄**&#x200B;에서 참조된 PDF이 활성화되지 않습니다.

릴리스에서 수정된 새로운 및 향상된 Guides 기능 및 문제에 대한 자세한 내용은 [Experience Manager Guides 릴리스 로드맵](https://experienceleague.adobe.com/kr/docs/experience-manager-guides/using/release-info/aem-guides-releases-roadmap)을 참조하세요.

### 알려진 문제 {#known-issues-18099}

* FORMS - 15818: 구성 요소 설명자 항목 `OSGI-INF/com.adobe.aemfd.docmanager.impl.*.xml` 서버 로그에서 진술을 찾을 수 없음. 이는 해를 미치지 않는 로그 구문입니다.

### 사용 중단된 기능 및 API {#deprecated-18099}

AEM as a Cloud Service에서 더 이상 사용되지 않는 기능과 API는 [사용 중단된 기능 및 API](/help/release-notes/deprecated-removed-features.md) 문서에 자세히 설명되어 있습니다.

다음은 최근에 사용되지 않는 기능이나 사용 중단 과정에 있는 기능에 대한 요약입니다.

#### JavaScript API 사용 {#javascript-use-api}

[JavaScript Use API](https://github.com/adobe/htl-spec/blob/master/SPECIFICATION.md#42-javascript-use-api)는 사용자가 API를 활용하는 코드를 디버깅하고 유지 관리하는 문제와 Java 대체 요소에 비해 성능 제한으로 인해 공식적으로 더 이상 사용되지 않습니다.

더 나은 성능, 더 쉬운 디버깅 및 더 나은 장기적 지원을 제공하는 [Java Use API,](https://experienceleague.adobe.com/en/docs/experience-manager-htl/content/java-use-api)(으)로 전환해야 합니다.

#### com.day.cq.wcm.api {#com-day-cq-wcm-api}

Adobe이 `com.day.cq.wcm.api`을(를) 업데이트하는 중입니다. 일부 메서드 및 클래스가 현재 릴리스에서 `@Deprecated`(으)로 표시되었습니다. 이러한 기능은 향후 릴리스에서 제거됩니다. 그들이 제안하는 대안으로 전환해 보십시오.

#### org.apache.jackrabbit.oak.plugins.blob {#org.apache.jackrabbit.oak.plugins.blob}

* GRANITE-54165: 공용 API에서 org.apache.jackrabbit.oak.plugins.blob을 사용하지 않습니다.

### 보안 수정 {#security-18099}

AEM as a Cloud Service는 플랫폼의 보안 및 성능을 최적화하는 데 사용됩니다. 이 유지 관리 릴리스는 2개의 식별된 취약점을 해결하여 강력한 시스템 보호에 대한 약속을 강화합니다.

### 임베드된 기술 {#embedded-tech-18099}

| 기술 | 버전 | 링크 |
|---|---|---|
| AEM Oak | 1.70.0 | [Oak API 1.70.0 API](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.70.0/index.html) |
| AEM SLING API | 2.27.6 | [Apache Sling API 2.27.6 API](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 1.4.24-1.4.0 | [HTML 템플릿 언어 사양](https://github.com/adobe/htl-spec) |
| AEM 핵심 구성 요소 | 2.27.0 | [AEM WCM 핵심 구성 요소](https://github.com/adobe/aem-core-wcm-components) |
