---
title: ' [!DNL Adobe Experience Manager] as a Cloud Service의 현재 유지 관리 릴리스 정보입니다.'
description: ' [!DNL Adobe Experience Manager] as a Cloud Service의 현재 유지 관리 릴리스 정보입니다.'
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: d73ccc454c89c7e06752de694af97ac26694be17
workflow-type: ht
source-wordcount: '902'
ht-degree: 100%

---


# 유지 관리 릴리스 정보 {#maintenance-release-notes}

다음 섹션에서는 Experience Manager as a Cloud Service의 현재 유지 관리 릴리스에 대한 기술 릴리스 정보를 간략히 소개합니다.

## 릴리스 22450 {#22450}

2025년 9월 16일에 릴리스된 유지 관리 릴리스 22450의 지속적인 개선 사항이 아래에 요약되어 있습니다. 이전 유지 관리 릴리스는 릴리스 22171이었습니다.

이 유지 관리 릴리스에 대한 2025.9.0 기능 활성화는 전체 기능 세트를 제공합니다. 자세한 내용은 [Experience Manager 릴리스 로드맵](https://experienceleague.adobe.com/ko/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap)을 참조하십시오.

### 새로운 기능 {#new-features-22450}

* SITES-32595: 이제 생략되거나 거부된 조각으로 완료된 워크플로를 식별할 수 있습니다. 워크플로 API 응답에서 새 속성을 사용할 수 있으며, 이는 유효하지 않거나 참조가 잘못되어 제외된 조각을 나열합니다.
* SITES-33642: 이제 수정된 콘텐츠 조각에 대해 새 API 이벤트가 생성되고 사용됩니다.
* SITES-33320: 이제 검색 API를 통해 `technicalName`을 사용하여 콘텐츠 조각 모델을 검색할 수 있습니다.

### 개선 사항 {#enhancements-22450}

* SITES-34023: 더 나은 식별을 위해 콘텐츠 조각 모델 엔드포인트의 응답에 `technicalName` 필드가 추가되었습니다.
* SITES-32766: 이제 콘텐츠 조각 모델의 콘텐츠 자산 참조에서 더 광범위한 바이너리 파일 유형을 지원합니다.
* SITES-33974: 보다 정확하고 사용자 친화적인 OpenAPI 설명서를 개선했습니다.
* SITES-9173: 캐시 `ContentPolicyStatus`.
* SITES-9290: `TouchEditContext`의 캐싱을 개선합니다.
* SITES-33355: 워크플로 콘솔에서 “페이로드 보기”에 새 CF 편집기를 엽니다.
* SITES-33356: CF 생성에서 새 CF 편집기 열기 → TouchUI 관리자 UI에서 열기.
* SITES-32952: 게재 API를 사용할 때 CFM 필드의 기본값이 일관되지 않음.
* SITES-31539: 범용 편집기를 사용한 Edge Delivery: `head.html`에서 Universal Editor 구성 메타 태그에 대한 지원 추가.
* SITES-20672: 범용 편집기가 있는 Edge Delivery: 작성 시 추가 벌크 메타데이터 스프레드시트에 대한 지원을 추가합니다.
* SITES-32963: 범용 편집기가 있는 Edge Delivery: 최적화 대상, 자동 할당 및 자체 학습에 대한 새로운 실험 메타데이터를 추가합니다.
* SITES-30847: 핵심 구성 요소 2.30.0 릴리스.
* SITES-29617: referencedBy 엔드포인트가 ReferenceSearch 클래스를 사용하도록 업데이트되어 성능과 신뢰성이 향상되었습니다.
* SITES-19308: 참조 유효성 검사 단계를 최적화하여 페이지 삭제 프로세스의 성능을 개선했습니다.
* SITES-34293: 성능을 향상시키기 위해 템플릿화된 리소스에 대해 지연 로딩을 구현했습니다.
* SITES-33892: 성능을 향상시킬 수 있는 유사 페이지의 참조 검사를 건너뛰는 기능 토글이 추가되었습니다.

### 해결된 문제 {#fixed-issues-22450}

* CQ-4360550: AEM 클라우드 서비스에서 페이지 이동을 되돌린 후 언어 복제가 예기치 않게 사라지는 문제를 해결했습니다.
* SITES-25232: 날짜 설정 및 종료 타임워프 링크에 포커스 표시기가 표시되지 않습니다.
* SITES-25258: 포커스는 주석 삭제 모달 대화 상자로 관리되지 않습니다.
* SITES-25305: 인구 통계 도구 모음이 논리적 순서로 포커스를 받지 않습니다.
* SITES-25366: 티저 모드의 로딩 상태가 화면 판독기에 의해 공지되지 않습니다.
* SITES-34276: 범용 편집기가 있는 Edge Delivery: 게재 계층에 적용되지 않는 자동 생성된 CORS 정책 수정했습니다.
* SITES-34811: 범용 편집기가 있는 Edge Delivery: 작성 중인 스프레드시트의 링크에 hlx 선택기가 추가되지 않도록 수정했습니다.
* SITES-31669: 도구 > 사이트 > 론치에서 현지화되지 않은 문자열 “이 페이지는 로 리디렉션됩니다.”
* SITES-30879: 사이트 > 페이지 편집기 > 검색 구성 요소에서 현지화되지 않은 문자열.
* SITES-30959: 페이지 편집기 > 이미지 구성 요소에서 현지화되지 않은 문자열.
* SITES-21743: 현지화되지 않음 “표시할 문서를 선택하십시오.” 페이지 편집기 > PDF 뷰어의 문자열
* SITES-19785: 문자열이 핵심 구성 요소 사이트 > 탭에서 현지화되지 않았습니다.
* SITES-22059: 핵심 구성 요소 사이트 > PDF 뷰어에서 현지화되지 않은 “파일 미리보기를 사용할 수 없음” 문자열.
* SITES-33360: 론치 > 편집에서 시작되는 “Error during operation. Provided path is not a launch” 문자열이 현지화되지 않았습니다.
* SITES-32975: Headless UI > 론치 > 소스와 비교 론치 > 지역화되지 않은 날짜 형식입니다.
* SITES-32973: Headless UI > 시작 > 리베이스에서 하드코딩된 문자열.
* SITES-13540: 론치 > 프로모션의 현지화되지 않은 문자열.
* SITES-13085: 사이트 > 론치 생성 페이지의 현지화되지 않은 오류 문자열.
* SITES-21499: 현지화되지 않은 문자열은 사이트 > 론치 > 편집입니다.
* SITES-14961: 사이트 > 속성 > 블루프린트 > 롤아웃 대화 상자에서 날짜 필드를 자릅니다.
* SITES-33764: 론치 필터(Source 경로/워크플로에서 만든 론치)가 작동하지 않습니다.
* SITES-33884: “현재 페이지 및 하위 페이지 홍보”가 의도하지 않게 범위 밖의 페이지에 대한 홍보를 수행합니다.
* SITES-33611: 대규모 시장에서 Live Copy 개요가 작동하지 않습니다.
* SITES-34331: 관리자가 아닌 사용자를 위해 롤아웃 오버레이를 로드할 때 503 시간 초과입니다.
* SITES-34403: 종료 중 `GraphqlClientImpl deactivate()`의 `NullPointerException`.
* SITES-33817: 일관성을 보장하기 위해 UI 스키마와 JCR 모델 간의 동기화 문제를 해결했습니다.
* SITES-31141: 이제 경로로 표시되지 않는 콘텐츠 참조가 API 응답에서 올바르게 반환됩니다.
* SITES-34080: 이제 콘텐츠 조각 만들기 프로세스가 보다 강력하며 요청에 필드가 제공되지 않으면 실패하지 않습니다.
* SITES-30773: “찾기 및 바꾸기”를 사용하여 단어를 찾는 정규 표현식이 UTF-8 문자와 올바르게 일치하도록 개선되었습니다.
* SITES-33742: 워크플로 API를 사용할 때 콘텐츠 조각을 성공적으로 이동할 수 없는 버그가 해결되었습니다.

### 알려진 문제 {#known-issues-22450}

없음.

### 사용 중단된 기능 및 API {#deprecated-22450}

AEM as a Cloud Service에서 더 이상 사용되지 않는 기능과 API는 [사용 중단된 기능 및 API](/help/release-notes/deprecated-removed-features.md) 문서에 자세히 설명되어 있습니다.

### 보안 수정 {#security-22450}

AEM as a Cloud Service는 플랫폼의 보안 및 성능 최적화에 중점을 둡니다. 이 유지 관리 릴리스는 18개의 식별된 취약점을 해결하여 강력한 시스템 보호에 대한 우리의 노력을 강화합니다.

### 임베드된 기술 {#embedded-tech-22450}

| 기술 | 버전 | 링크 |
|---|---|---|
| AEM Oak | 1.84.0 | [Oak API 1.84.0 API](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.84/index.html) |
| AEM SLING API | 2.27.6 | [Apache Sling API 2.27.6 API](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 1.4.28-1.4.0 | [HTML 템플릿 언어 사양](https://github.com/adobe/htl-spec) |
| Apache HTTP 서버 | 2.4.65 | [Apache Httpd 2.4.65](https://apache.googlesource.com/httpd/+/refs/tags/2.4.65/CHANGES) |
| AEM 핵심 구성 요소 | 2.29.0 | [AEM WCM 핵심 구성 요소](https://github.com/adobe/aem-core-wcm-components) |
| Node.js | 14 (기본값) | [지원되는 Node.js 버전](https://experienceleague.adobe.com/ko/docs/experience-manager-cloud-service/content/implementing/developing/developing-with-front-end-pipelines#node-versions) |
