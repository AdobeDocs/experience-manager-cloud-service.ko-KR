---
title: ' [!DNL Adobe Experience Manager] as a Cloud Service의 현재 유지 관리 릴리스 정보입니다.'
description: ' [!DNL Adobe Experience Manager] as a Cloud Service의 현재 유지 관리 릴리스 정보입니다.'
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
source-git-commit: a8651a44300772b5c9706a5fd85e7fefef72e47d
workflow-type: tm+mt
source-wordcount: '1124'
ht-degree: 14%

---

# 유지 관리 릴리스 정보 {#maintenance-release-notes}

다음 섹션에서는 Experience Manager as a Cloud Service 현재 유지 관리 릴리스의 기술 릴리스 정보에 대해 간략히 소개합니다.

## 릴리스 14227 {#release-14227}

다음은 2023년 11월 9일에 공개적으로 릴리스된 유지 보수 릴리스 14227에 대한 지속적인 개선 사항을 요약합니다. 이 유지 관리 릴리스는 이전 유지 관리 릴리스 14029의 업데이트입니다. 유지 관리 릴리스 14227은 14157를 대체하여 한 가지 문제를 수정합니다.

이 유지 관리 릴리스(2023.11.0)에 대한 기능 활성화는 전체 기능 세트를 제공합니다. 자세한 내용은 [Experience Manager 릴리스 로드맵](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap.html)을 참조하십시오.

### 개선 사항 {#enhancements-14227}

* ASSETS-29631: Assets Cloud: 보안 게재/검색을 위해 dam:roles를 사용합니다.
* CQ-4354515: 번역: 참조된 리소스의 번역을 표시하지 않는 옵션입니다.
* FORMS-9993: Forms 핵심 구성 요소를 Skyline으로 이동하는 단계를 정의합니다.
* FORMS-10570: API에 EC API 온보드 - 첫 번째 라우터.
* GRANITE-48143: Sling ResourceMerger를 1.4.4로 업그레이드하십시오.
* SITES-14874: 이벤트: 모델 이벤트에 대한 CFM 트리를 확장하여 메타데이터 변경 사항을 포함합니다.
* SITES-2719: 콘텐츠 조각: 콘텐츠 조각 변형에 대한 태깅 지원(다시 활성화됨).
* SITES-3619: 컨텐츠 조각: JSON의 GraphQL CF 변형 태그 출력 및 변형 태그로 필터링(다시 활성화됨).
* SITES-13750: 콘텐츠 조각: 콘텐츠 조각 모델에 대한 태그를 삭제합니다.
* SITES-13920: 콘텐츠 조각: 여러 필드(시험판)에 대한 minItems 구성 지원.
* SITES-14080: 콘텐츠 조각: 콘텐츠 조각 변형의 태그를 삭제합니다.
* SITES-14770: 콘텐츠 조각: 조각 변형에 fieldTags 속성이 포함되어야 합니다.
* SITES-15356: 콘텐츠 조각: 리소스가 생성될 때 응답 헤더로 etag를 반환합니다.
* SITES-15357: 콘텐츠 조각: 해당 참조가 없는 조각의 게시를 허용합니다.
* SITES-15938: 컨텐츠 조각: 컨텐츠 참조 메타데이터가 누락되었습니다.
* SITES-16078: 콘텐츠 조각: 조각을 가져올 때 변형의 유효성 검사 결과 속성을 채웁니다.
* SITES-16545: 콘텐츠 조각: 콘텐츠 조각 변형의 참조를 검색하기 위한 엔드포인트를 추가합니다.
* SITES-16853: 콘텐츠 조각: /adobe/sites/cf/fragments/ 제거{fragmentId}/variation/{name}/tags 끝점입니다.

### 해결된 문제 {#fixed-issues-14227}

* 다양한 접근성 문제 해결
* ASSETS-31015: 알 수 없는 파일 확장명을 가진 에셋에 파일을 업로드할 수 없습니다.
* ASSETS-24739: 게시할 때 Frame.io 사용자 지정 작업 끝점을 사용하지 않도록 설정합니다.
* CMGR-49845: 컨텐츠 백플로우: 지정된 체크포인트에 대한 올바른 루트 경로를 식별하는 데 문제가 있습니다.
* CMGR-49709: 컨텐츠 백플로우: 추가 속성을 무시하도록 속성 필터를 업데이트합니다.
* CQ-4354503: Adobe IMS 구성을 임의로 제거합니다.
* CQ-4354414: ConfigurationReplicationEventHandler는 많은 개별 플러시 작업을 만듭니다.
* CQ-4354401: 번역: 에셋 처리를 시작하기 전에 프로젝트에서 만든 에셋을 저장해야 합니다.
* CQ-4354430: 번역: 언어 폴더 구조의 일부가 아닌 에셋을 번역 프로젝트에 추가하는 도중 오류가 발생했습니다.
* CQ-4354412: 번역: 번역 작업 콘텐츠를 삭제해도 참조된 모든 콘텐츠는 삭제되지 않습니다.
* CQ-4354636: 번역: 언어 루트 수준에서 언어 사본을 만들어도 페이지의 경로가 조정되지 않습니다.
* CQ-4354700: 워크플로: 워크플로 페이로드 화면이 로드되지 않습니다.
* CQ-4354834: 워크플로: 워크플로 받은 편지함 작업에 주석을 추가할 수 없습니다.
* FORMS-11302: RTE에서 편집된 구성 요소의 제목이 적응형 양식 편집기 > 규칙 편집기에 잘못 표시됩니다.
* GRANITE-45706: 키 값이 Äúu)이면 i18n ‚ 가져오기에 ‚ 실패합니다.
* SITES-14156: 이벤트: 게시 이벤트가 항상 전송되는 것은 아닙니다.
* SITES-14520: GraphQL: FT_SITES-2719로 인해 페이지 매김된 Graphql 쿼리의 성능이 저하되었습니다.
* SITES-16444: GraphQL: GraphQL 쿼리에서 누락된 동일한 이름 필드에 대한 DataFetchException.
* SITES-16225: GraphQL: Java API에 의해 반환되는 모델 및 조각 RTE 필드의 콘텐츠 유형이 올바르지 않습니다.
* SITES-15373: 콘텐츠 조각: /adobe/sites/cf/fragments/{fragmentId}/variation/{name}/tags 끝점이 올바른 리소스 이름 지정 규칙을 사용하지 않습니다.
* SITES-15709: 컨텐츠 조각: 부울 필드를 만들 때 모델 끝점 만들기 문제를 해결했습니다.
* SITES-15727: 콘텐츠 조각: &quot;태그&quot; 유형의 필드는 모델 편집기에 한 번만 추가할 수 있습니다.
* SITES-15782: 콘텐츠 조각: 열거형 유형의 필드 모델에 고유 속성이 없습니다.
* SITES-15786: 콘텐츠 조각: &#39;이 포함된 폴더에 콘텐츠 조각을 만들 수 없습니다.
* SITES-15790: 콘텐츠 조각: 버전 생성을 위한 위치 헤더 업데이트.
* SITES-15923: 콘텐츠 조각: CF 관리자가 일부 폴더를 표시하지 않습니다.
* SITES-15987: 콘텐츠 조각: 변형을 만드는 동안 500개를 가져옵니다.
* SITES-16067: 콘텐츠 조각: 긴 텍스트 조각 필드의 MIME 유형은 수정할 수 없습니다.
* SITES-16074: 콘텐츠 조각: 문자열이 아닌 태그 필드는[] JCR에서 검색할 수 없습니다.
* SITES-16079: 콘텐츠 조각: /fragments/{id}/references에서 중복을 반환하기 시작했습니다.
* SITES-16118: 콘텐츠 조각: 조각이 패치되고 조각 필드가 모델에서 누락된 경우 예외가 발생합니다.
* SITES-16119: 콘텐츠 조각: 조각 메타데이터에 인식할 수 없는 필드가 포함된 경우 예외가 발생합니다.
* SITES-16121: 콘텐츠 조각: 모델 날짜 필드를 검색하면 예외가 발생합니다.
* SITES-16123: 콘텐츠 조각: 리소스가 콘텐츠 조각이 아닌 경우 조각 가져오기 끝점에서 예외가 발생합니다.
* SITES-16208: 콘텐츠 조각: ContentFragmentModelIdentifier가 잘못된 제목 속성을 노출합니다.
* SITES-16707: 콘텐츠 조각: 콘텐츠 조각 모델 데이터 유형이 올바르게 읽히지 않습니다.
* SITES-16818: 콘텐츠 조각: 태그가 있는 경우에만 삭제를 수행합니다.
* SITES-16207: 컨텐츠 조각: POST /adobe/sites/cf/models 작업이 두 개의 다른 확인 상태 코드를 반환합니다.
* SITES-15616: 콘텐츠 조각: 게시 끝점이 때로 콘텐츠 조각의 모든 참조를 게시하지 않습니다.
* SITES-16027: 콘텐츠 조각: 변형 참조 정보가 조각 응답에서 누락되었습니다.
* SITES-16243: 콘텐츠 조각: 찾기 및 바꾸기가 Render as: Multiple이 있는 필드에서는 작동하지 않습니다.
* SITES-16250: 콘텐츠 조각: CF를 패치하면 잘못된 etag 헤더가 반환되는 경우가 있습니다.
* SITES-16686: 콘텐츠 조각: 콘텐츠 조각 비조각 참조는 상위 참조가 최대 깊이일 때 일련화됩니다.
* SITES-12880: Fast-Track: Sites > Analytics 설정에 대한 현지화 수정.
* SITES-16103: 경험 조각: 콘솔 오류로 인해 Target 옵션이 Cloud Service 아래에 표시되지 않습니다.
* SITES-16001: MSM: 라이브 카피를 생성하는 동안 롤아웃 구성에서 다중 필드 구성 요소를 제외하는 기능.
* SITES-16559: MSM: 경험 조각에 대한 롤아웃 프로세스 중에 롤아웃 구성이 제거되었습니다.
* SITES-16797: MSM: 편집기에서 CF 필드에 대한 상속을 다시 활성화하는 수정되었습니다.
* SITES-16273: 페이지 편집기: 클립보드의 aem sites 페이지 내에 있는 복사 붙여넣기 오류입니다.
* SITES-16126: 사이트 관리자: SITES-10288 이후 관리자가 아닌 사용자의 작성 성능이 느려집니다.
* FORMS-10534: 부울 피연산자 옵션을 선택할 때 규칙 편집기에서 오류가 발생합니다.
* FORMS-10248: 적응형 양식에서 데이터 값이 부울 유형인 경우 규칙이 라디오 버튼 또는 확인란 구성 요소에 대한 값을 제대로 설정하지 못합니다.
* FORMS-11361: 드롭다운 구성 요소의 기본값은 목록에서 첫 번째 옵션을 선택하는 것입니다.
* FORMS-11413: Forms 포털 미리 채우기 서비스와 관련된 오류가 서비스가 사용되지 않는 경우에도 적응형 Forms에 의해 트리거됩니다.
* FORMS-11433: 비양식 구성 요소가 적응형 양식에 포함되면 제출 프로세스가 완료되지 않습니다.
* FORMS-11206: 사용자가 적응형 양식에 대해 게시 워크플로우를 예약하려고 할 때 예상대로 작동하지 않습니다.
* FORMS-11546: Lighthouse가 적응형 양식의 반복된 패널에 대한 ARIA 레이블이 누락되어 접근성에 영향을 미칩니다.
* FORMS-11095: 전화 번호, 이메일 주소 및 번호 필드에 대해 ARIA 속성이 잘못 정의되어 접근성 문제가 발생합니다.

### 알려진 문제 {#known-issues-14227}

없음.

### 임베드된 기술 {#embedded-tech-14227}

| 기술 | 버전 | 링크 |
|---|---|---|
| AEM OAK | 1.56-T20230927085643-189caed | [Oak API 1.56.0 API](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.56.0/index.html) |
| AEM SLING API | 버전 2.27.2 | [Apache Sling API 2.27.2 API](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 버전 1.4.20-1.4.0 | [HTML 템플릿 언어 사양](https://github.com/adobe/htl-spec) |
| AEM 핵심 구성 요소 | 버전 2.23.4 | [AEM WCM 핵심 구성 요소](https://github.com/adobe/aem-core-wcm-components) |
