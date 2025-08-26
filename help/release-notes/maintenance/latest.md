---
title: ' [!DNL Adobe Experience Manager] as a Cloud Service의 현재 유지 관리 릴리스 정보입니다.'
description: ' [!DNL Adobe Experience Manager] as a Cloud Service의 현재 유지 관리 릴리스 정보입니다.'
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: 3067e88f8adea50f6b6b05e0466974bc57bc4a4e
workflow-type: tm+mt
source-wordcount: '607'
ht-degree: 35%

---


# 유지 관리 릴리스 정보 {#maintenance-release-notes}

다음 섹션에서는 Experience Manager as a Cloud Service의 현재 유지 관리 릴리스에 대한 기술 릴리스 정보를 간략히 소개합니다.

## 릴리스 21994 {#21994}

다음은 2025년 8월 19일에 공개적으로 릴리스된 유지 보수 릴리스 21994에 대한 지속적인 개선 사항을 요약했습니다. 이전 유지 관리 릴리스는 릴리스 21772.

이 유지 관리 릴리스(2025.8.0)에 대한 기능 활성화는 전체 기능 세트를 제공합니다. 자세한 내용은 [Experience Manager 릴리스 로드맵](https://experienceleague.adobe.com/ko/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap)을 참조하십시오.

### 새로운 기능  {#new-features-21994}

없음.

### 개선 사항 {#enhancements-21994}

* GRANITE-53488: deleteconf.json 끝점 오류 처리를 개선합니다.
* GRANITE-59968: REPLICATION_FORCE_READY_MILLIES를 구성할 수 있습니다.
* GRANITE-60183: Apache commons-fileupload 1.6.0.
* GRANITE-60306: Apache commons-lang ~ 3.18.0.
* GRANITE-60637: Apache commons-codec to 1.19.0.
* GRANITE-60645: Apache commons-io 2.20.0.
* GRANITE-60663: Apache commons-text 1.14.0.
* GRANITE-60714: Mongo Java Driver 5.2.
* GRANITE-60778: Filevault 4.0.0.
* GRANITE-60823: Jackrabbit 2.22.2.
* GRANITE-60967: clientlib 컴파일 시간 추적을 위한 지표를 만듭니다.
* SKYOPS-105469: 자동 수정 api에 acsredirectMgr 지원을 추가하는 중입니다.
* SKYOPS-113929: 복제 준비 확인을 위한 지표를 추가합니다.
* SKYOPS-84821: Sling 엔진 2.16.6.
* SKYOPS-114322: 폐쇄 컴파일러 언어를 `ECMASCRIPT_2018` 수준으로 증가시킵니다.

### 해결된 문제 {#fixed-issues-21994}

* GRANITE-60167: Skyline의 비동기 인덱스 업데이트는 CSV 데이터를 지원하지 않습니다.
* GRANITE-60532: 값 전환 수정이 선택되지 않습니다.
* SITES-34277: 페이지의 번역 워크플로우에서 차단 오류를 수정합니다.
* SKYOPS-105471: aso 자동 수정에 대한 dambaseredirect 수정을 지원합니다.
* SKYOPS-109532: 기능 제거 링크를 주석 뒤 토글로 추가합니다.

#### AEM Guides {#guides-21994}

* GUIDES-26688: 기본 PDF 템플릿의 CSS 및 페이지 레이아웃 파일에 일관되지 않은 파일 잠금 동작이 발생하여 파일이 잠긴 경우에도 편집할 수 있습니다.
* GUIDES-30900: Assets UI에서 에셋 수가 많은 폴더를 복사하면 API 시간 초과가 발생합니다. 작업은 백엔드에서 계속 실행되고 잠시 후 완료되지만 성공 또는 실패 메시지나 알림이 UI에 표시되지 않습니다.
* GUIDES-29090: 기본 PDF 출력에서 색인 목록(LOI)은 알파벳순이 아닌 순서로 표시되고 중첩된 색인 용어가 제대로 그룹화되지 않아 색인을 탐색하기 어렵습니다.
* GUIDES-11227: Assets UI에서 DITA 맵을 복사하면 첨부된 기준선도 새 맵에 복사됩니다.
* GUIDES-31506: 최근 파일 위젯에 나열된 파일 중 하나가 소스 템플릿에 썸네일이 포함되지 않은 템플릿을 기반으로 하는 경우 홈 페이지가 비어 있습니다.

릴리스에서 수정된 새로운 기능과 향상된 기능 및 문제에 대한 자세한 내용은 [Experience Manager Guides 릴리스 로드맵](https://experienceleague.adobe.com/ko/docs/experience-manager-guides/using/release-info/aem-guides-releases-roadmap)을 참조하십시오.

### 알려진 문제 {#known-issues-21994}

* Apache HTTPD 버전 2.4.65에서는 보안 수정 사항의 일부로 구현된 새로운 제한 사항으로 인해 특정 구성에 영향을 줄 수 있는 변경 사항이 도입되었습니다. 이러한 수정 사항은 Content-Type 헤더를 수정하는 데 사용되는 `RequestHeader set`, `edit` 및 `edit_r`과(와) 같은 지시문이 이제 요청 헤더로 올바르게 제한되도록 함으로써 취약성을 해결합니다. 이 변경 사항은 특히 정적 콘텐츠의 경우 의도하지 않은 응답 헤더 수정을 방지합니다.

### 사용 중단된 기능 및 API {#deprecated-21994}

AEM as a Cloud Service에서 더 이상 사용되지 않는 기능과 API는 [사용 중단된 기능 및 API](/help/release-notes/deprecated-removed-features.md) 문서에 자세히 설명되어 있습니다.

### 보안 수정 {#security-21994}

AEM as a Cloud Service는 플랫폼의 보안 및 성능 최적화에 중점을 둡니다. 이 유지 관리 릴리스에서는 강력한 시스템 보호에 대한 노력의 일환으로 식별된 취약점 2개가 해결되었습니다.

### 임베드된 기술 {#embedded-tech-21994}

| 기술 | 버전 | 링크 |
|---|---|---|
| AEM Oak | 1.84.0 | [Oak API 1.84.0 API](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.84/index.html) |
| AEM SLING API | 2.27.6 | [Apache Sling API 2.27.6 API](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 1.4.28-1.4.0 | [HTML 템플릿 언어 사양](https://github.com/adobe/htl-spec) |
| Apache HTTP 서버 | 2.4.65 | [Apache Httpd 2.4.65](https://apache.googlesource.com/httpd/+/refs/tags/2.4.65/CHANGES) |
| AEM 핵심 구성 요소 | 2.29.0 | [AEM WCM 핵심 구성 요소](https://github.com/adobe/aem-core-wcm-components) |
| Node.js | 14 (기본값) | [지원되는 Node.js 버전](https://experienceleague.adobe.com/ko/docs/experience-manager-cloud-service/content/implementing/developing/developing-with-front-end-pipelines#node-versions) |
