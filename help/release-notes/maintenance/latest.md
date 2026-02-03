---
title: ' [!DNL Adobe Experience Manager] as a Cloud Service의 현재 유지 관리 릴리스 정보입니다.'
description: ' [!DNL Adobe Experience Manager] as a Cloud Service의 현재 유지 관리 릴리스 정보입니다.'
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: a842a5f0bd5561563a86f6f0b6e8abf8cfd679ec
workflow-type: tm+mt
source-wordcount: '972'
ht-degree: 21%

---


# 유지 관리 릴리스 정보 {#maintenance-release-notes}

다음 섹션에서는 Experience Manager as a Cloud Service의 현재 유지 관리 릴리스에 대한 기술 릴리스 정보를 간략히 소개합니다.

## 릴리스 24222 {#24222}

다음은 2026년 2월 3일에 공개적으로 릴리스된 유지 보수 릴리스 24222에 대한 지속적인 개선 사항을 요약합니다. 이전 유지 관리 릴리스는 릴리스 23963.

이 유지 관리 릴리스에 대한 2026.2.0 기능 활성화는 전체 기능 세트를 제공합니다. 자세한 내용은 [Experience Manager 릴리스 로드맵](https://experienceleague.adobe.com/ko/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap)을 참조하십시오.

### 개선 사항 {#enhancements-24222}

* CNTBF-604: 새 contentbackflow 번들 릴리스를 만듭니다.
* CQ-4361592: 프로젝트 생성 및 업데이트에 TypeHint 지원을 추가합니다.
* CQ-4362198: 최신 AEM 및 Granite 패키지 번역.
* GRANITE-36205: 내부 Oak 릴리스 버전을 최신 버전으로 업데이트합니다.
* GRANITE-59211: OPTEL: 임시 지원 및 셀프서비스 구성이 추가되었습니다.
* GRANITE-62166: 마이그레이션 도구에서 마이그레이션 상태를 재사용하도록 마이그레이션 번들을 업데이트합니다.
* GRANITE-62598: 컨텐츠 패키지 필터에서 중복 속성을 제거합니다.
* GRANITE-62684: skyline-ops를 통해 클라이언트 소켓 시간 제한을 구성할 수 있도록 합니다.
* GRANITE-62702: 온라인 마이그레이션을 위해 sling 검색을 독립형 구현으로 대체합니다.
* GRANITE-62763: ASSETS 로터리를 기반으로 구아바 사용 중단 예외 목록을 업데이트합니다.
* GRANITE-62771: 더 이상 사용되지 않는 새로운 Commons-Lang 종속성이 도입되면 빠른 시작 빌드가 실패합니다.
* GRANITE-62987: Felix 웹 콘솔을 버전 5.0.18로 업데이트합니다.
* GRANITE-63339: Azure 마이그레이션 상태 Blob에 대한 임대 메커니즘을 개선합니다.
* GRANITE-63343: workflow.core에 최신 버전의 Sling API 번들에 대한 지원을 추가합니다.
* GRANITE-63799: 범프 OIDC 인증 번들 버전.
* GRANITE-63821: JCRVLT-831/JCRVLT-839를 수정하여 FileVault 릴리스로 빠른 시작을 업데이트합니다.
* GRANITE-63827: Oak의 최신 공개 릴리스(1.90.0)로 빠른 시작을 업데이트합니다.
* GRANITE-63888: Jackrabbit 2.22.3으로 빠른 시작을 업데이트합니다.
* GRANITE-64030: 표현식 언어 유효성 검사기 허용 목록에 키워드 및 패턴을 추가합니다.
* GRANITE-64050: 숨겨진 conf 폴더가 외부 제품 기능을 숨길 수 있도록 허용합니다.
* SITES-30452: ASO가 포함된 콘텐츠 API - 제목 및 설명 제안.
* SITES-38099: 더 높은 버전의 정상 상태 검사를 사용하도록 `testing-model.txt`을(를) 업데이트합니다.
* SKYOPS-43616: Jenkins 자격 증명을 Dispatcher 저장소의 저장소로 마이그레이션합니다.
* SKYOPS-108584: FACT 도구를 0.6.0에서 0.6.10으로 범프
* SKYOPS-115691: CORS 필터 번들을 업그레이드하여 Preflight 요청에 Vary Origin 헤더를 추가합니다.
* SKYOPS-123094: Quickstart에서 Apache HTTP 구성 요소를 업데이트합니다.
* SKYOPS-123236: 복제 패키지에 `rep:cugPolicy`을(를) 포함합니다.
* SKYOPS-123240: 빠른 시작에서 CRXDE 종속성을 업데이트합니다.
* SKYOPS-123247: 빠른 시작에서 Sling XSS 번들을 업데이트합니다.
* SKYOPS-123250: 빠른 시작에서 Sling 보안 번들을 업데이트합니다.
* SKYOPS-123327: AEM-CS SDK에 Java 21이 필요합니다.
* SKYOPS-125574: Quickstart에서 netcentric AC 도구 번들을 업데이트합니다.
* SKYOPS-126150: 스레드 덤프 생성기 스크립트에 대한 최상위 명령을 개선합니다.

### 해결된 문제 {#fixed-issues-24222}

* FORMS-23687: 포함 규칙이 기본값 없이 사용될 때 SSV 유효성 검사 오류를 수정합니다.
* GRANITE-48472: 사용자 설정 편집 탭에서 암호를 변경할 때 현지화 오류가 발생합니다.
* GRANITE-50286: 사용자 관리 모달의 상태 열에서 레이아웃 문제를 수정합니다.
* GRANITE-52301: 현지화 보안 그룹의 세션 문자열에 변경 사항을 커밋할 수 없습니다.
* GRANITE-52920: 보안에서 사용자를 만들 때 현지화 오류 발생 새 사용자 만들기.
* GRANITE-54654: 보안 Adobe IMS 구성 확인 대화 상자의 현지화 문자열.
* GRANITE-56371: 보안 Trust Store에서 잘못된 데이터 형식을 수정합니다.
* GRANITE-62717: ASCII 이외 문자를 사용하여 JSafe 암호 처리에 대한 암호화 키 저장소를 업그레이드합니다.
* GRANITE-62789: 컨텐츠 배포에서 다시 시도 안 함 모드를 지원하도록 messaging-client를 업데이트합니다.
* GRANITE-62824: 사용자 편집기의 그룹 탭에 액세스할 때 `NullPointerException`을(를) 수정합니다.
* GRANITE-63080: `org.slf4j.spi`의 가져오기를 `slf4j 2.x`과(와) 호환되도록 합니다.
* GRANITE-63210: 게시 시작 시 Dispatcher 무효화를 수정하도록 배포 코어를 업데이트합니다.
* GRANITE-63293: 처음 작성한 후 필수 별표가 손실되는 필수 경로 필드를 수정합니다.
* GRANITE-63360: 여러 경로를 선택할 때 표시되는 잘못된 정보를 수정합니다.
* SITES-36242: GraphQL 실행 정규 표현식 범위를 좁혀 Dispatcher 필터 바이패스를 수정합니다.
* SKYOPS-84379: RDE에 의한 적절한 기능 전환 픽업을 위해 최신 FACT 도구를 사용합니다.
* SKYOPS-121216: Jackson 2.20.0 라이브러리로 업데이트를 되돌립니다.

#### AEM Guides {#guides-24222}

* GUIDES-38198 : 컨텍스트 메뉴의 MathML 편집 옵션을 사용하여 인라인 MathML 방정식을 업데이트할 때 페이지를 새로 고칠 때까지 업데이트된 값이 반영되지 않습니다.
* GUIDES-38276: Assets UI의 버전 기록 패널에서 버전 레이블을 제거할 수 없습니다.
* GUIDES-36641: AEM Sites 출력을 생성할 때 `<ph>` 요소가 있는 키워드 및 주제 제목이 포함된 맵 제목이 게시된 출력에 포함되지 않습니다.
* 안내서-37837: 주제나 맵을 저장하려고 할 때 특히 백그라운드에서 실행되는 집중 에셋 처리 작업 또는 번역 워크플로 중에 파일 저장 실패 오류가 발생하여 작업이 간헐적으로 실패할 수 있습니다.
* GUIDES-27774: 끊김 목록 보고서에 현재 맵의 범위 내에서 올바르게 확인된 외부 링크, 올바른 `keyrefs` 및 키워드가 잘못 포함되어 있습니다.

릴리스에서 수정된 새로운 기능과 향상된 기능 및 문제에 대한 자세한 내용은 [Experience Manager Guides 릴리스 로드맵](https://experienceleague.adobe.com/ko/docs/experience-manager-guides/using/release-info/aem-guides-releases-roadmap)을 참조하십시오.

### 알려진 문제 {#known-issues-24222}

없음.

### 사용 중단된 기능 및 API {#deprecated-24222}

* AEMSRE-2896: 사용자 지정된 Logmanager 구성 처리를 수정합니다.
* GRANITE-62802: `commons-lang`에서 사용되지 않는 `granite.auth.saml` 종속성을 제거합니다.
* GRANITE-62805: `commons-lang`에서 사용되지 않는 `granite.httpcache.core` 종속성을 제거합니다.
* GRANITE-62864: `commons-lang`에서 사용되지 않는 `granite.jobs.async` 종속성을 제거합니다.
* GRANITE-62865: `commons-lang`에서 사용되지 않는 `granite.replication.core` 종속성을 제거합니다.
* GRANITE-62868: `commons-lang`에서 사용되지 않는 `granite.rest.api` 종속성을 제거합니다.
* GRANITE-62895: `commons-lang`에서 사용되지 않는 `translation.connector.msft.core` 종속성을 제거합니다.
* GRANITE-63069: `com.adobe.granite.httpcache.core`을(를) 사용하지 않습니다.
* GRANITE-63179: `commons-lang`에서 사용되지 않는 `cq-workflow-impl` 종속성을 제거합니다.
* GRANITE-63180: `commons.lang` 번들에서 더 이상 사용되지 않는 `cq-mailer` 내보내기를 제거하십시오.
* SKYOPS-123329: AEM Ethos 배포에 대한 Java 11 지원을 삭제하고 `commons-lang3`을(를) 업데이트합니다.
* SKYOPS-124983: AEM 시작 스크립트에서 더 이상 사용되지 않는 `nashorn.args`을(를) 제거합니다.

AEM as a Cloud Service에서 더 이상 사용되지 않는 기능과 API는 [사용 중단된 기능 및 API](/help/release-notes/deprecated-removed-features.md) 문서에 자세히 설명되어 있습니다.

### 보안 수정 {#security-24222}

AEM as a Cloud Service는 플랫폼의 보안 및 성능 최적화에 중점을 둡니다. 이 유지 관리 릴리스는 확인된 10개의 취약점을 해결하여 강력한 시스템 보호에 대한 노력을 강화합니다.

### 임베드된 기술 {#embedded-tech-24222}

| 기술 | 버전 | 링크 |
|---|---|---|
| AEM Oak | 1.90.0 | [Oak 1.90.0 API](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.90.0/index.html) |
| AEM SLING API | 2.27.6 | [Apache Sling API 2.27.6 API](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 1.4.28-1.4.0 | [HTML 템플릿 언어 사양](https://github.com/adobe/htl-spec) |
| Apache HTTP 서버 | 2.4.65 | [Apache Httpd 2.4.65](https://apache.googlesource.com/httpd/+/refs/tags/2.4.65/CHANGES) |
| AEM 핵심 구성 요소 | 2.30.2 | [AEM WCM 핵심 구성 요소](https://github.com/adobe/aem-core-wcm-components) |
| Node.js | 14 (기본값) | [지원되는 Node.js 버전](https://experienceleague.adobe.com/ko/docs/experience-manager-cloud-service/content/implementing/developing/developing-with-front-end-pipelines#node-versions) |
