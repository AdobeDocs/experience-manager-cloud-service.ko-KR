---
title: ' [!DNL Adobe Experience Manager] as a Cloud Service의 현재 유지 관리 릴리스 정보입니다.'
description: ' [!DNL Adobe Experience Manager] as a Cloud Service의 현재 유지 관리 릴리스 정보입니다.'
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: 82b3b4bdcd09aa86974518f4f62e73c9f377c83f
workflow-type: tm+mt
source-wordcount: '777'
ht-degree: 30%

---


# 유지 관리 릴리스 정보 {#maintenance-release-notes}

다음 섹션에서는 Experience Manager as a Cloud Service의 현재 유지 관리 릴리스에 대한 기술 릴리스 정보를 간략히 소개합니다.

## 릴리스 25821 {#release-25821}

다음은 2026년 5월 5일에 공개적으로 릴리스된 유지 보수 릴리스 25821에 대한 지속적인 개선 사항을 요약합니다. 이전 유지 관리 릴리스는 릴리스 25520.

2026.5.0 기능 활성화는 이 유지 관리 릴리스에 대한 전체 기능 세트를 제공합니다. 자세한 내용은 [Experience Manager 릴리스 로드맵](https://experienceleague.adobe.com/ko/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap)을 참조하십시오.

### 개선 사항 {#enhancements-25821}

* CQ-4362304: 지침 프론트엔드를 만들고 LLM 구성 UI를 업데이트합니다.
* GRANITE-39546: Apache Tika를 3.x로 업그레이드합니다.
* GRANITE-53957: oak-blob-azure용 Azure SDK V8을 V12로 업그레이드합니다.
* GRANITE-61245: commons-lang의 모든 사용을 제거합니다(commons-lang3으로 바꾸기).
* GRANITE-64748: OIDC 인증 핸들러를 범핑합니다.
* GRANITE-64764: Apache Commons 텍스트를 1.15.0으로 업데이트합니다.
* GRANITE-64963: Filevault를 4.2.0으로 업데이트합니다.
* GRANITE-66197: M365 테넌트에 대한 Microsoft Graph API 이메일 지원을 추가합니다.
* GRANITE-66449: Java 17 API 지원을 위해 Maven 플러그인을 업데이트합니다.
* GRANITE-66473: 기본-granite에 카페인 캐시 라이브러리를 추가합니다.
* GRANITE-66836: Oak 2.0.0으로 빠른 시작을 업데이트합니다.
* SKYOPS-129301: APIs jar Javadoc 준수 수준을 Java 17로 설정합니다.
* SKYOPS-129351: MCP SDK 호환성을 위해 반응 스트림 및 Reactor-core를 업데이트합니다.
* SKYOPS-131412: Apache Commons Exec를 최신 버전으로 업데이트합니다.
* SKYOPS-131432: Felix SCR을 2.2.14로 업데이트합니다.
* SKYOPS-131907: Sling API 영역을 1.1.10으로 업데이트합니다.
* SKYOPS-131938: GSON을 최신 버전으로 업데이트합니다.
* SKYOPS-132173: Apache Commons 코덱을 최신 버전으로 업데이트합니다.
* SKYOPS-132182: Sling 테넌트 번들을 업데이트합니다.
* SKYOPS-132267: `org.osgi.service.component` 주석을 업데이트합니다.
* SKYOPS-132272: 슬링 피쳐 모델 번들을 업데이트합니다.
* SKYOPS-132525: 새 API 제거를 방지하려면 빠른 시작 분석기를 추가합니다.
* SKYOPS-134408: `com.adobe.granite.asset.core`을(를) 2.2.82로 업데이트합니다.
* SKYOPS-137750: `com.adobe.granite.comments`을(를) 1.0.40으로 업데이트합니다.
* SKYOPS-137759: `com.adobe.granite.jobs.async.ui.commons`을(를) 3.2.4로 업데이트합니다.
* SKYOPS-138356: `com.adobe.granite.oauth.server`을(를) 1.1.36으로 업데이트합니다.
* SKYOPS-138739: SnakeYAML을 2.6으로 업데이트합니다.

### 해결된 문제 {#fixed-issues-25821}

* ASSETS-59546: 더 이상 사용되지 않는 commons-lang 라이브러리에 대한 종속성을 제거합니다.
* ASSETS-64831: AssetProcessorProcess 재설정 처리 시도 횟수로 인해 자산이 멈춥니다.
* ASSETS-66683: uploadBlob 오류로 인해 승인 루프가 발생했습니다.
* CNTBF-613: 노드 유형을 등록할 때 액세스 거부됨(JCR-101) 수정.
* GRANITE-44537: &quot;국가/지역&quot;의 문자열이 AEM에 현지화되지 않았습니다.
* GRANITE-61760: AdminUserInitializer 활성화에 실패했습니다.
* GRANITE-64543: 권한 제한 응답이 API 구조를 따르지 않습니다.
* GRANITE-66692: 내부 클래스 로더는 패키지 새로 고침에 민감하지 않습니다.
* GRANITE-66732: 시작 레벨 1 번들에 대한 서비스 구성 요소 대신 활성화자를 사용하십시오.
* GRANITE-66846: AEM 권한 API에 `rep:ntNames` 제한이 표시되지 않습니다.
* SITES-39267: 관계 체인 항목의 pagePath를 복원합니다.
* SITES-43715: 리소스 상태를 읽는 동안 권한 유효성 검사에 실패했습니다.

#### AEM Guides {#guides-25821}

* GUIDES-45110: 편집기에서 **파일 선택** 대화 상자를 사용하여 이미지를 선택하면 래스터 형식(예: JPG, PNG 및 GIF)만 표시됩니다. 벡터 파일(`.ai` 및 `.eps` 등)은 표시되지 않으며 선택할 수 없습니다.
* GUIDES-41938: 이름에 공백이 있는 폴더에 주제를 만들면 하이픈으로 공백을 대체하는 중복 폴더가 잘못 생성되고 주제가 원래 폴더 대신 여기에 저장됩니다.
* GUIDES-38377: 폴더 프로필의 출력 사전 설정 변경 사항이 기존 맵에 적용되면 AEM Sites 사전 설정에 대해 저장된 **게시 컨텍스트**&#x200B;가 재설정됩니다.
* GUIDES-43547: 큰 주제나 맵을 열면 작성자 인스턴스가 응답하지 않고 경우에 따라 다시 시작해야 합니다.
* GUIDES-32520: 요소에 백스페이스를 사용하면 편집기가 커서 위치에 관계없이 항목의 맨 위로 스크롤합니다(편집기 2.0).

릴리스에서 수정된 새로운 기능과 향상된 기능 및 문제에 대한 자세한 내용은 [Experience Manager Guides 릴리스 로드맵](https://experienceleague.adobe.com/ko/docs/experience-manager-guides/using/release-info/aem-guides-releases-roadmap)을 참조하십시오.

### 알려진 문제 {#known-issues-25821}

없음.

### 사용 중단된 기능 및 API {#deprecated-25821}

AEM as a Cloud Service에서 더 이상 사용되지 않는 기능과 API는 [사용 중단된 기능 및 API](/help/release-notes/deprecated-removed-features.md) 문서에 자세히 설명되어 있습니다.

### 보안 수정 {#security-25821}

AEM as a Cloud Service는 플랫폼의 보안 및 성능 최적화에 중점을 둡니다. 이 유지 관리 릴리스는 19개의 식별된 취약점을 해결하여 강력한 시스템 보호에 대한 노력을 강화합니다.

### 임베드된 기술 {#embedded-tech-25821}

| 기술 | 버전 | 링크 |
|---|---|---|
| AEM Oak | 2.0.0 | [Oak 2.0.0 API](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/2.0.0/index.html) |
| AEM SLING API | 2.27.6 | [Apache Sling API 2.27.6 API](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 1.4.28-1.4.0 | [HTML 템플릿 언어 사양](https://github.com/adobe/htl-spec) |
| Apache HTTP 서버 | 2.4.65 | [Apache Httpd 2.4.65](https://apache.googlesource.com/httpd/+/refs/tags/2.4.65/CHANGES) |
| AEM 핵심 구성 요소 | 2.30.4 | [AEM WCM 핵심 구성 요소](https://github.com/adobe/aem-core-wcm-components) |
| Node.js | 14 (기본값) | [지원되는 Node.js 버전](https://experienceleague.adobe.com/ko/docs/experience-manager-cloud-service/content/implementing/developing/developing-with-front-end-pipelines#node-versions) |
