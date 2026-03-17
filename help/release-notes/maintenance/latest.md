---
title: ' [!DNL Adobe Experience Manager] as a Cloud Service의 현재 유지 관리 릴리스 정보입니다.'
description: ' [!DNL Adobe Experience Manager] as a Cloud Service의 현재 유지 관리 릴리스 정보입니다.'
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: 2a7b83b99547637e02ec7cef9c92c5dd794a9adc
workflow-type: tm+mt
source-wordcount: '636'
ht-degree: 31%

---


# 유지 관리 릴리스 정보 {#maintenance-release-notes}

다음 섹션에서는 Experience Manager as a Cloud Service의 현재 유지 관리 릴리스에 대한 기술 릴리스 정보를 간략히 소개합니다.

## 릴리스 24893 {#release-24893}

다음은 2026년 3월 17일에 공개적으로 릴리스된 유지 보수 릴리스 24893에 대한 지속적인 개선 사항을 요약했습니다. 이전 유지 관리 릴리스는 릴리스 24678.

이 유지 관리 릴리스에 대한 2026.3.0 기능 활성화는 전체 기능 세트를 제공합니다. 자세한 내용은 [Experience Manager 릴리스 로드맵](https://experienceleague.adobe.com/ko/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap)을 참조하십시오.

### 개선 사항 {#enhancements-24893}

* CNTBF-613: 수정 액세스 거부됨(JCR-101) - 노드 유형을 등록하지 못했습니다.
* GRANITE-53957: oak-blob-azure용 Azure SDK V8을 V12로 업그레이드합니다.
* GRANITE-57035: 바운시 성을 기본 보안 공급자로 사용합니다.
* GRANITE-59249: JVM에 보안 공급자를 등록하지 마십시오.
* GRANITE-61564: 관리자에 대해 `/security/users.html`의 설정 보기를 열 수 없습니다.
* GRANITE-64748: OIDC: 구성 가능한 sling.oauth-request-key 쿠키 만료.
* SITES-39767: 요청 특성(CSP)을 통해 임시 값을 지원합니다.
* SKYOPS-129301: API jar javadoc 준수 수준을 17로 설정합니다.
* GRANITE-64962: Apache Jackrabbit Oak을 1.92.0으로 업데이트합니다.
* GRANITE-64963: Apache Jackrabbit Filevault를 4.2.0으로 업데이트합니다.
* GRANITE-64764: Apache Commons 텍스트를 버전 1.15.0으로 업데이트합니다.
* SKYOPS-131412: Apache Commons Exec를 1.6.0으로 업데이트합니다.
* SKYOPS-131432: Felix SCR을 2.2.14로 업데이트합니다.
* SKYOPS-131907: Sling API 영역을 1.1.10으로 업데이트합니다.
* SKYOPS-131938: GSON을 2.13.2로 업데이트합니다.
* SKYOPS-132173: Apache Commons 코덱을 1.21.0으로 업데이트합니다.
* SKYOPS-132182: Sling 테넌트를 1.1.8로 업데이트합니다.
* SKYOPS-132267: org.osgi.service.component를 1.5.1로 업데이트합니다.
* SKYOPS-132272: Sling 기능 모델을 2.0.4로 업데이트합니다.
* SKYOPS-133689: Apache httpd 2.4.66을 사용하도록 Dispatcher을 업데이트합니다.

### 해결된 문제 {#fixed-issues-24893}

* GRANITE-64443: `workflow.core` `log4j`의 더 이상 사용되지 않는 내보내기를 제거합니다.
* GRANITE-64543: 권한 제한 응답이 API 계약과 일치해야 합니다.

#### AEM Guides {#guides-24893}

* GUIDES-38412 : Schematron `(*.sch)` 파일을 편집하고 찾기 및 바꾸기 기능을 사용하면 찾기 및 바꾸기 패널이 맨 아래에 일부 화면 밖에 표시되어 입력 필드 및 컨트롤에 액세스할 수 없습니다.
* GUIDES-37806: 조건부 사전 설정이 다른 여러 맵에서 동일한 주제가 재사용되는 경우 Salesforce에 최신 맵을 게시하면 주제 콘텐츠가 덮어쓰므로 이전에 게시된 맵의 사용자에게 잘못된 데이터가 표시됩니다.
* GUIDES-39394: 처음에 특정 버전(예: `/en/` 아래)의 언어별 자산으로 관리된 이미지를 업데이트된 버전이 있는 글로벌 폴더로 이동하고 기준 요소 내보내기가 수행되면 새 기준 요소가 해당 이미지의 오래된 언어별 버전을 계속 참조하여 기준 요소 내보내기가 실패합니다.
* GUIDES-39054: 동적 기준선을 만들 때 편집기가 여러 개의 동시 API 요청으로 인해 응답하지 않아 다른 모든 작업이 중지되는 경우가 있습니다.
* GUIDES-37781: 검토 작업에 사용자를 할당할 때 드롭다운에 선택한 프로젝트와 관련된 사용자만 나열하는 대신 모든 사용자가 나열되므로 사용자 옵션이 유효하지 않습니다.
* GUIDES-39385: 맵에 대한 보고서를 여는 동안 필터 패널 로드가 지연됩니다.

릴리스에서 수정된 새로운 기능과 향상된 기능 및 문제에 대한 자세한 내용은 [Experience Manager Guides 릴리스 로드맵](https://experienceleague.adobe.com/ko/docs/experience-manager-guides/using/release-info/aem-guides-releases-roadmap)을 참조하십시오.

### 알려진 문제 {#known-issues-24893}

없음.

### 사용 중단된 기능 및 API {#deprecated-24893}

AEM as a Cloud Service에서 더 이상 사용되지 않는 기능과 API는 [사용 중단된 기능 및 API](/help/release-notes/deprecated-removed-features.md) 문서에 자세히 설명되어 있습니다.

### 보안 수정 {#security-24893}

AEM as a Cloud Service는 플랫폼의 보안 및 성능 최적화에 중점을 둡니다. 이 유지 관리 릴리스는 9개의 식별된 취약점을 해결하여 강력한 시스템 보호에 대한 노력을 강화합니다.

### 임베드된 기술 {#embedded-tech-24893}

| 기술 | 버전 | 링크 |
|---|---|---|
| AEM Oak | 1.92.0 | [Oak 1.92.0 API](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.92.0/index.html) |
| AEM SLING API | 2.27.6 | [Apache Sling API 2.27.6 API](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 1.4.28-1.4.0 | [HTML 템플릿 언어 사양](https://github.com/adobe/htl-spec) |
| Apache HTTP 서버 | 2.4.66 | [Apache Httpd 2.4.66](https://apache.googlesource.com/httpd/+/refs/tags/2.4.66/CHANGES) |
| AEM 핵심 구성 요소 | 2.30.4 | [AEM WCM 핵심 구성 요소](https://github.com/adobe/aem-core-wcm-components) |
| Node.js | 14 (기본값) | [지원되는 Node.js 버전](https://experienceleague.adobe.com/ko/docs/experience-manager-cloud-service/content/implementing/developing/developing-with-front-end-pipelines#node-versions) |
