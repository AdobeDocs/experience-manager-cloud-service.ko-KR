---
title: ' [!DNL Adobe Experience Manager] as a Cloud Service의 현재 유지 관리 릴리스 정보입니다.'
description: ' [!DNL Adobe Experience Manager] as a Cloud Service의 현재 유지 관리 릴리스 정보입니다.'
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: 68444ac15513bad7c1eaee97c474e21d36992d49
workflow-type: tm+mt
source-wordcount: '502'
ht-degree: 37%

---


# 유지 관리 릴리스 정보 {#maintenance-release-notes}

다음 섹션에서는 Experience Manager as a Cloud Service의 현재 유지 관리 릴리스에 대한 기술 릴리스 정보를 간략히 소개합니다.

## 릴리스 23482 {#23482}

다음은 2025년 12월 3일에 공개적으로 릴리스된 유지 보수 릴리스 23482에 대한 지속적인 개선 사항을 요약했습니다. 이전 유지 관리 릴리스는 릴리스 23385.

이 유지 관리 릴리스에 대한 2025.12.0 기능 활성화는 전체 기능 세트를 제공합니다. 자세한 내용은 [Experience Manager 릴리스 로드맵](https://experienceleague.adobe.com/ko/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap)을 참조하십시오.


### 개선 사항 {#enhancements-23482}

* ASSETS-49770: 맬웨어 스캔 결과에 대한 격리 알림을 추가합니다.
* ASSETS-54079: 격리 폴더에 대해 사용자 지정 메타데이터 양식을 적용합니다.
* ASSETS-54083: 예약된 격리 정리 메커니즘을 만듭니다.
* ASSETS-54278: 에셋에서 `dam:avScanTime` 속성을 제거합니다.
* ASSETS-57284: 파일 업로드를 격리 폴더로 제한합니다(드래그 앤 드롭 비활성화).
* ASSETS-57428: Assets 보기 UI에서 격리 폴더를 숨깁니다.
* ASSETS-57626: 비동기 자산 작업에 대한 다시 시도 동작을 개선합니다.
* ASSETS-57879: 비동기 자산 이동/복사 작업에 대한 병합 옵션을 추가합니다.
* ASSETS-58099: 전체 환경에 대해 향상된 스마트 태그를 비활성화하려면 구성을 추가하십시오.
* ASSETS-58136: 검색 OpenAPI에서 페이지 매김 피드백을 구현합니다.
* ASSETS-59402: 폴더 삭제 API에 대한 비동기 작업 끝점을 추가합니다. 패키지를 내부 영역으로 내보냅니다.
* ASSETS-59966: 맬웨어 관리자 그룹의 이름을 격리 관리자로 변경합니다.
* ASSETS-60166: iframe 기반 URL 대신 VideoViewer.js를 사용합니다.
* GRANITE-61378: 권한 디버깅 도구 - ListPrincipals API.
* GRANITE-63235: `cq:conf` 속성을 사용하여 사이트를 식별하도록 쿼리하고 이전 페이지/버전 검색을 지원합니다.
* SITES-30452: ASO가 포함된 콘텐츠 API - 제목 및 설명 제안, XWalk 지원, JSON 패치 작업, IMS 서비스 사용자 바인딩.

### 해결된 문제 {#fixed-issues-23482}

* ASSETS-57430: 전처리를 건너뛰는 Assets 보기 업로드를 수정했습니다. `repoapi.preprocessing` 패키지를 내보내고 RAPI를 최신 버전으로 업데이트하십시오.
* ASSETS-58190: 컬렉션 UI에서 불필요하게 높은 추측률을 줄입니다.
* ASSETS-58866: OpenAPI 응답에서 반환되는 에셋 제목/설명/ID를 수정합니다.
* ASSETS-58868: 에셋에서 정렬 필드가 누락된 경우 페이지 매김을 수정합니다.
* ASSETS-58920: 사전 처리를 건너뛰고 일괄 에셋 가져오기를 수정합니다.
* ASSETS-59168: 잘못된 시간대를 표시하는 스캔 시작/종료 시간을 수정합니다.
* ASSETS-59702: 에셋 상태가 상태 없음으로 설정되면 이벤트 순서 지정을 수정합니다.
* ASSETS-59830: pod 종료 중 중지된 비동기 작업 다시 큐
* ASSETS-49757: 맬웨어 검색 이벤트에 대한 수정 사항.
* GRANITE-61019: AEM을 다시 시작한 후 처음 실행할 때 `gcMonitor` 수정 메시지가 표시되지 않습니다.
* GRANITE-62717: ASCII 이외 문자로 `JSafe` 암호 처리를 수정하십시오.
* SITES-34331: 관리자가 아닌 사용자(`cqLiveSyncCancelled index`)에 대한 롤아웃 오버레이 로드 중 503 시간 제한을 수정했습니다.

### 알려진 문제 {#known-issues-23482}

없음.

### 사용 중단된 기능 및 API {#deprecated-23482}

AEM as a Cloud Service에서 더 이상 사용되지 않는 기능과 API는 [사용 중단된 기능 및 API](/help/release-notes/deprecated-removed-features.md) 문서에 자세히 설명되어 있습니다.

### 보안 수정 {#security-23482}

AEM as a Cloud Service는 플랫폼의 보안 및 성능 최적화에 중점을 둡니다. 이 유지 관리 릴리스에서는 강력한 시스템 보호에 대한 노력의 일환으로 식별된 취약점 4개가 해결되었습니다.

### 임베드된 기술 {#embedded-tech-23482}

| 기술 | 버전 | 링크 |
|---|---|---|
| AEM Oak | 1.88.0 | [Oak 1.88.0 API](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.88/index.html) |
| AEM SLING API | 2.27.6 | [Apache Sling API 2.27.6 API](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 1.4.28-1.4.0 | [HTML 템플릿 언어 사양](https://github.com/adobe/htl-spec) |
| Apache HTTP 서버 | 2.4.65 | [Apache Httpd 2.4.65](https://apache.googlesource.com/httpd/+/refs/tags/2.4.65/CHANGES) |
| AEM 핵심 구성 요소 | 2.30.2 | [AEM WCM 핵심 구성 요소](https://github.com/adobe/aem-core-wcm-components) |
| Node.js | 14 (기본값) | [지원되는 Node.js 버전](https://experienceleague.adobe.com/ko/docs/experience-manager-cloud-service/content/implementing/developing/developing-with-front-end-pipelines#node-versions) |

