---
title: ' [!DNL Adobe Experience Manager] as a Cloud Service의 현재 유지 관리 릴리스 정보입니다.'
description: ' [!DNL Adobe Experience Manager] as a Cloud Service의 현재 유지 관리 릴리스 정보입니다.'
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: 7ae30d2053a17c2855c66b265c831ea27d19d535
workflow-type: tm+mt
source-wordcount: '1496'
ht-degree: 17%

---


# 유지 관리 릴리스 정보 {#maintenance-release-notes}

다음 섹션에서는 Experience Manager as a Cloud Service의 현재 유지 관리 릴리스에 대한 기술 릴리스 정보를 간략히 소개합니다.

## 릴리스 21331 {#21331}

다음은 2025년 6월 24일에 공개적으로 릴리스된 유지 보수 릴리스 21331에 대한 지속적인 개선 사항을 요약했습니다. 이전 유지 관리 릴리스는 릴리스 21193.

2025.7.0 기능 활성화는 이 유지 관리 릴리스에 대한 전체 기능 세트를 제공합니다. 자세한 내용은 [Experience Manager 릴리스 로드맵](https://experienceleague.adobe.com/ko/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap)을 참조하십시오.

### 개선 사항 {#enhancements-21331}

* CQ-4356522: `WorkflowResourceStatusProvider` 최적화.
* FORMS-16458: 글꼴 속성(서체)을 선택하기 위한 UI입니다.
* FORMS-17707: AEP 커넥터가 AEP platform stage에서 작동하지 않습니다.
* FORMS-19125: AF 편집기에서 자동 조각 매핑을 지원합니다.
* FORMS-19336: AF 편집기의 데이터 Source 트리에 검색이 추가되었습니다.
* FORMS-19417: 계층 보기에서 라디오 버튼 지원.
* FORMS-19603: 규칙 편집기에서 마스터 페이지와 디자인 페이지를 지원합니다.
* SITES-10575: &quot;MSM 블루프린트 블룸필터 로더&quot;가 100000개 이상의 행을 로드하려고 합니다.
* SITES-14542: 라이브 카피 소스 페이지의 이름을 변경/이동하면 이전에 게시된 경우 이름이 변경되었거나 이동된 라이브 카피 페이지 게시가 트리거되어야 합니다.
* SITES-19754: 범용 편집기가 있는 Edge Delivery: 통합에 문제가 있을 때 사람이 읽을 수 있는 오류 메시지를 추가합니다.
* SITES-23499: 범용 편집기가 있는 Edge Delivery: 블록 옵션에 사용할 여러 필드에 대한 지원을 추가합니다.
* SITES-23518: 범용 편집기가 있는 Edge Delivery: Edge Delivery 특정 에셋 렌디션에 대한 지원을 추가합니다.
* SITES-25913: 콘텐츠 조각 REST API: 게시 워크플로우를 시작하기 전에 리소스에 대한 타임박스 유효성 검사.
* SITES-25976: MSM 롤아웃 이후 경험 조각 내부 링크가 조정되지 않습니다.
* SITES-26271: 콘텐츠 조각 Rest API: GET 변형 끝점에 대한 BFS 트래버스로 전환합니다.
* SITES-27486: 범용 편집기 - AEM 통합.
* SITES-27775: 게시 중 최적화된 참조 검색(메타데이터 지연 로드).
* SITES-27782: 범용 편집기가 있는 Edge Delivery: 콘텐츠를 Edge Delivery에 게시하려면 특정 게시자 구독자 구현을 추가하십시오(조기 액세스).
* SITES-27792: 범용 편집기가 있는 Edge Delivery: 전용 Edge Delivery 서비스 구성 템플릿을 추가합니다.
* SITES-28683: MSM LiveRelationship 검색에서 고급 상태를 건너뛸 수 있도록 허용합니다.
* SITES-29930: 콘텐츠 조각 Rest API: 콘텐츠 조각 게시 워크플로우에 대한 지표를 추가합니다.
* SITES-29986: 콘텐츠 조각 Rest API: CF 모델 기술 이름 지정을 지원합니다.
* SITES-30088: 콘텐츠 조각 Rest API: CF Publish - filterReferencesByStatus가 비어 있는 경우 참조 검색을 건너뜁니다.
* SITES-30328: 범용 편집기가 있는 Edge Delivery: Sidekick에서 미리 볼 수 있도록 지원을 추가합니다.
* SITES-30445: 콘텐츠 조각 Rest API: CF 모델 UI 스키마: 축소 가능한 초기 상태를 제어하는 옵션을 추가합니다.
* SITES-30604: 콘텐츠 조각 Rest API: 새 UI에서 모델 메타데이터 스키마 채택을 지원합니다.
* SITES-30885: 지속 쿼리에서 JSON 처리가 최적화되었습니다.
* SITES-30886: 컨텐츠 조각 REST API: 워크플로우 메타데이터에 저장된 조각 uuid를 기반으로 컨텐츠 조각 엔드포인트를 위한 GET 워크플로우입니다.
* SITES-31005: 진행 상황을 표시하도록 롤아웃 작업 UI를 개선합니다.
* SITES-31020: 진행 상황을 표시하도록 라이브 카피 만들기 작업 UI를 개선합니다.
* SITES-31472: 론치 삭제로 인해 론치가 대용량일 경우 저장소가 일시 중지될 수 있습니다.
* SITES-31677: 사용자 지정 작업 영역은 Target으로 AEM 컨텐츠 조각 내보내기를 지원합니다.
* SITES-31782: 콘텐츠 조각 REST API: 로컬 자산에 대한 설명을 추가합니다.
* SITES-32175: 라이브 카피 생성 및 MSM 페이지 롤아웃 모두에 대해 중개 커밋을 허용합니다.
* SITES-5358: 컨텐츠 조각 Rest API: 하위 항목이 있는 CF를 복사합니다.

### 해결된 문제 {#fixed-issues-21331}

* CQ-4359756: 이제 번역 규칙에 구성 요소 수준의 필터 속성이 포함됩니다.
* CQ-4359826: 콘텐츠 조각 참조 패널에서 일관되지 않은 상태를 확인합니다.
* CQ-4359866: 이제 LanguageUtils 클래스는 추가적인 종속성을 추가하지 않고 단위 테스트를 지원합니다.
* FORMS-13990: Forms 서비스 API: 문서 생성 : 선택한 후 비어 있을 때 데이터 필드는 예상이 400일 때 200을 제공합니다.
* FORMS-14309: Forms 서비스 API : 데이터 응답 코드 수정 추출
* FORMS-18526: 조건에 여러 필드가 있는 규칙을 복사할 때 고정 필드는 변경되지 않습니다.
* FORMS-18977: DOR 서비스가 문서의 제목을 전달하지 않습니다.
* FORMS-19047: SP22의 AEM Forms에 적응형 양식을 게시한 후 번역이 누락되었습니다.
* FORMS-19234: AEM forms에서 PDF의 타임라인 기능을 사용할 수 없습니다.
* FORMS-19628: 자동 생성된 DOR에서 중첩된 패널 제목을 제외하면 루트 패널 제목도 숨깁니다.
* FORMS-19651: 클릭한 단추가 이진 조건에서 사용되고 동일한 단추가 then 문에서 사용되는 경우 규칙을 수정합니다.
* FORMS-19808: FormsPortal - 소극적 로드가 활성화된 경우 초안을 가져올 수 없습니다.
* FORMS-19887: HTML5 미리 보기에서 액세스 속성이 작동하지 않습니다.
* SITES-15452: 출시 시 고유한 CF 요소를 사본과 비교하여 검사해서는 안 됩니다.
* SITES-24492: ARIA 탭 목록에 액세스 가능한 이름이 없습니다.
* SITES-24623: 콘텐츠 조각 Rest API: 동일한 CF에 대한 끝점 간 ETag 불일치 문제를 해결합니다.
* SITES-24668: 확대/축소를 400%로 늘리면 참조 레일 기능이 중단됩니다.
* SITES-24678: 참조 레일 상태 메시지가 화면 판독기에 의해 발표되지 않습니다.
* SITES-24697: 화면 판독기에서 이미지 모델의 로드 상태를 알리지 않습니다.
* SITES-24708: 확대/축소가 400%로 증가하면 레일 기능이 중단됩니다.
* SITES-25235: 필터 레일 콘텐츠 로드 메시지가 화면 판독기에 의해 발표되지 않습니다.
* SITES-25254: 콘텐츠를 320px에서 보면 가로 스크롤 막대가 회전 모달에 나타납니다.
* SITES-25433: 범용 편집기가 있는 Edge Delivery: 다국어 사이트 구조에 대한 페이지 버전 렌더링을 수정합니다.
* SITES-26890: 키보드를 사용하는 동안 범위 &quot;테이블 헤더&quot; 키보드 포커스가 게시 관리 페이지에 표시되지 않습니다.
* SITES-29075: 대용량 웹 사이트에는 라이브 카피 개요가 작동하지 않습니다.
* SITES-29514: 범용 편집기가 있는 Edge Delivery: 새 사이트를 만들 때 GitHub/프로젝트 URL을 필수 항목으로 설정합니다.
* SITES-29691: 특정 실행 관련 사례에서 페이지를 이동할 수 없습니다.
* SITES-29745: 콘텐츠 조각 Rest API: BFS 순회에서 참조 변형의 하이드레이션을 구현합니다.
* SITES-29748: CF 편집기 내에서 managepublication/quickpublish 작업을 표시하도록 renderconditions가 수정되었습니다.
* SITES-29789: 복사된 루트 페이지의 구성 요소 링크 변경 문제.
* SITES-29987: 콘텐츠 조각 Rest API: 콘텐츠 조각 모델 만들기 및 편집은 `previewUrlPattern`을(를) 지원하지 않습니다.
* SITES-30140: 콘텐츠 조각 참조를 만들 때 이중 창 문제가 발생합니다.
* SITES-30260: 콘텐츠 조각 REST API: 최신 ETag를 사용하여 CF를 업데이트/삭제하는 도중 오류 발생.
* SITES-30327: 콘텐츠 조각 Rest API: 권한 없이 CF를 게시하면 각 페이로드 리소스에 대해 별도의 워크플로우가 만들어집니다.
* SITES-30333: XMP 구문 분석 문제가 발생하는 것을 방지하기 위해 jcr에서 자산 메타데이터를 읽습니다.
* SITES-30353: AEM 콘텐츠 조각의 “src” 필드에 대한 GraphQL DataFetchingExceptions.
* SITES-30377: 범용 편집기가 있는 Edge Delivery: 조직 및 사이트 이름을 정리합니다.
* SITES-30386: 범용 편집기가 있는 Edge Delivery: 중복된 레거시 UE `cors.js`을(를) 제거합니다.
* SITES-30583: 콘텐츠 조각 Rest API: 찾기 및 바꾸기 도구가 모든 문자를 소문자로 바꿉니다.
* SITES-30585: 콘텐츠 조각 REST API: `previewUrlPattern`이(가) 참조를 사용하여 CFM을 만들 때 설정되지 않았습니다.
* SITES-30634: RTE 이미지 대체 텍스트 및 맞춤이 일관되게 작동하지 않습니다.
* SITES-30660: 사용자 지정 AEM 구성 요소의 ADA 규정 준수 문제입니다.
* SITES-30695: 범용 편집기가 있는 Edge Delivery: 사용자 지정 코드를 방해하지 않도록 재작성기 파이프라인 등급을 높입니다.
* SITES-30727: 프로덕션 작성자 편집기에서 구성 요소를 끌어다 놓을 수 없습니다.
* SITES-30752: 지속 쿼리 응답을 생성할 때 `If-modified-since`/`last-modified` 헤더를 사용하지 마십시오.
* SITES-30871: AFTEREDIT 리스너가 트리거된 후 DOM이 업데이트됩니다.
* SITES-30877: 잘못된 하위 페이지 롤아웃 상태입니다.
* SITES-30899: &quot;나중에&quot; 롤아웃 옵션을 사용하면 날짜를 선택하지 않고 계속할 수 있습니다.
* SITES-30947: 롤아웃 중에 블루프린트에 &quot;비헤이비어&quot; 속성이 누락되어 Null 포인터 예외가 발생했습니다.
* SITES-31157: 콘텐츠 조각 Rest API: 패치 실패는 특정 사례입니다.
* SITES-31272: PageManager.copy를 통해 Assets 언어 사본을 만들 수 없습니다.
* SITES-31327: 컨텐츠 조각 REST API: GET 조각 요청에서 ETag 유효성 검사 제거.
* SITES-31387: 고스트 구성 요소 상속을 다시 활성화할 때 JavaScript 오류 &quot;ns.ui.alert가 함수가 아닙니다.&quot;가 발생합니다.
* SITES-31455: 콘텐츠 조각 Rest API: 동일한 콘텐츠 조각 모델에 대한 끝점 간 ETag 불일치 문제를 해결합니다.
* SITES-31459: 콘텐츠 조각 REST API: 콘텐츠 참조 필드가 있는 경우 CF Live Copy를 편집할 수 없습니다.
* SITES-31467: 페이지 편집기의 contexthub.authoring-hook.js에서 js-errors.
* SITES-31594: 콘텐츠 조각 REST API: `extractMetadataSchemaFieldLabel` 오류.
* SITES-31621: 범용 편집기가 있는 Edge Delivery: 라이브 카피인 스프레드시트에서 빈 행을 제거합니다.
* SITES-31676: 구성 요소를 작성하거나 삭제하면 페이지 하단에 빈 공간이 남습니다.
* SITES-31822: ClassicUI 확인란 레이블 누락 및 인코딩된 HTML.
* SITES-31857: 작은 따옴표가 있는 폴더에서 CF를 만들 수 없습니다.
* SITES-31888: 콘텐츠 조각 삭제가 미리 보기에 전파되지 않습니다.
* SITES-31922: 콘텐츠 조각 Rest API: 페이지 참조가 referencedBy 끝점에서 반환되지 않습니다.
* SITES-31987: 미리보기에 게시할 때 콘텐츠 조각에 대한 previewURL을 표시하지 않습니다.
* SITES-32095: Live Copy의 Afterchilddelete 이벤트 리스너에서 자동 새로 고침이 실패합니다.
* SITES-32237: 범용 편집기가 있는 Edge Delivery: 비어 있거나 형식이 잘못된 텍스트 구성 요소의 렌더링을 수정합니다.

### 알려진 문제 {#known-issues-21331}

없음.

### 사용 중단된 기능 및 API {#deprecated-21331}

AEM as a Cloud Service에서 더 이상 사용되지 않는 기능과 API는 [사용 중단된 기능 및 API](/help/release-notes/deprecated-removed-features.md) 문서에 자세히 설명되어 있습니다.

### 보안 수정 {#security-21331}

AEM as a Cloud Service는 플랫폼의 보안 및 성능 최적화에 중점을 둡니다. 이 유지 관리 릴리스에서는 강력한 시스템 보호에 대한 노력의 일환으로 식별된 취약점 21개를 해결했습니다.

### 임베드된 기술 {#embedded-tech-21331}

| 기술 | 버전 | 링크 |
|---|---|---|
| AEM Oak | 1.80.0 | [Oak API 1.80.0 API](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.80.0/index.html) |
| AEM SLING API | 2.27.6 | [Apache Sling API 2.27.6 API](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 1.4.28-1.4.0 | [HTML 템플릿 언어 사양](https://github.com/adobe/htl-spec) |
| AEM 핵심 구성 요소 | 2.29.0 | [AEM WCM 핵심 구성 요소](https://github.com/adobe/aem-core-wcm-components) |
