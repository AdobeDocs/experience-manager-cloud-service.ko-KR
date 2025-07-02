---
title: ' [!DNL Adobe Experience Manager] as a Cloud Service의 현재 유지 관리 릴리스 정보입니다.'
description: ' [!DNL Adobe Experience Manager] as a Cloud Service의 현재 유지 관리 릴리스 정보입니다.'
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: 080a79cdc0e48a54570ea53618b1f0be164d5156
workflow-type: tm+mt
source-wordcount: '1768'
ht-degree: 99%

---


# 유지 관리 릴리스 정보 {#maintenance-release-notes}

다음 섹션에서는 Experience Manager as a Cloud Service의 현재 유지 관리 릴리스에 대한 기술 릴리스 정보를 간략히 소개합니다.

## 릴리스 21331 {#21331}

2025년 6월 24일에 릴리스된 유지 관리 릴리스 21331의 지속적인 개선 사항이 아래에 요약되어 있습니다. 이전 유지 관리 릴리스는 릴리스 21193이었습니다.

이 유지 관리 릴리스(2025.7.0)에 대한 기능 활성화는 전체 기능 세트를 제공합니다. 자세한 내용은 [Experience Manager 릴리스 로드맵](https://experienceleague.adobe.com/ko/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap)을 참조하십시오.

### 개선 사항 {#enhancements-21331}

* CQ-4356522: `WorkflowResourceStatusProvider` 최적화.
* FORMS-16458: 글꼴 속성(서체)을 선택하기 위한 UI.
* FORMS-17707: AEP 커넥터가 AEP 플랫폼 단계에서 작동하지 않습니다.
* FORMS-19125: AF 편집기에서 자동 조각 매핑이 지원됩니다.
* FORMS-19336: AF 편집기의 데이터 소스 트리에 검색 기능이 추가되었습니다.
* FORMS-19417: 계층 구조 보기에서 라디오 버튼이 지원됩니다.
* FORMS-19603: 규칙 편집기에서 마스터 페이지와 디자인 페이지가 모두 지원됩니다.
* SITES-5358: 콘텐츠 조각 Rest API: 하위 항목을 포함하여 CF를 복사합니다.
* SITES-10575: “MSM: 블루프린트 블룸필터 로더”가 100,000개 이상의 행을 로드하려고 합니다.
* SITES-14542: Live Copy 소스 페이지의 이름을 변경하거나 이동하면 해당 Live Copy 페이지가 이전에 게시된 상태였을 경우 이름이 변경되거나 이동된 페이지도 게시되도록 트리거되어야 합니다.
* SITES-19754: 범용 편집기가 포함된 Edge Delivery: 통합에 문제가 있는 경우 사람이 읽을 수 있는 오류 메시지가 추가되었습니다.
* SITES-23499: 범용 편집기가 포함된 Edge Delivery: 블록 옵션에 여러 필드를 사용할 수 있도록 하는 지원이 추가되었습니다.
* SITES-23518: 범용 편집기가 포함된 Edge Delivery: Edge Delivery 특정 자산 렌디션에 대한 지원이 추가되었습니다.
* SITES-24436: 콘텐츠 조각 Rest API: 중복 참조 검색 속도를 높이기 위해 로컬 캐시가 도입되었습니다.
* SITES-25155: 콘텐츠 조각 Rest API: 모델 목록에서 더 이상 사용되지 않는 “enabledForFolder” 쿼리 매개변수가 제거되었습니다.
* SITES-25913: 콘텐츠 조각 Rest API: 게시 워크플로를 시작하기 전에 리소스의 시간 제한 유효성 검사가 수행됩니다.
* SITES-25976: MSM 롤아웃 이후 경험 조각 내부 링크가 조정되지 않습니다.
* SITES-26271: 콘텐츠 조각 Rest API: GET Variation 엔드포인트에 대해 BFS 순회로 전환합니다.
* SITES-27486: 범용 편집기 - AEM 통합.
* SITES-27775: 게시 중 참조 검색 기능이 최적화되었습니다(메타데이터 지연 로딩).
* SITES-27782: 범용 편집기가 포함된 Edge Delivery: Edge Delivery에 콘텐츠를 게시하기 위한 특정 게시자-구독자 구현이 추가되었습니다(얼리 액세스).
* SITES-27792: 범용 편집기가 포함된 Edge Delivery: 전용 Edge Delivery Service 구성 템플릿이 추가되었습니다.
* SITES-28557: 콘텐츠 조각 REST API: `/cf/fragments/{fragmentId}`에 `references=direct`를 통해 호출하여 가져온 ETag을 사용하여 콘텐츠 조각을 패치할 수 있도록 허용합니다.
* SITES-28683: MSM LiveRelationship 검색에서 고급 상태를 건너뛸 수 있도록 허용합니다.
* SITES-29601: 콘텐츠 조각 Rest API: 긴 텍스트 필드의 콘텐츠 조각 참조에 대한 유효성 검사.
* SITES-29614: 콘텐츠 조각 REST API: `/cf/workflows/{workflowInstanceId}` 엔드포인트를 사용하여 워크플로를 검색할 수 있으며, 이때 workflowInstanceId는 게시 요청 시 반환된 ID입니다.
* SITES-29615: 콘텐츠 조각 Rest API: `GET /cf/batch`를 사용하여 `/cf/batch`를 통해 생성된 모든 배치 요청을 나열합니다.
* SITES-29874: 콘텐츠 조각 Rest API: 이제 콘텐츠 조각의 긴 텍스트 필드에 포함된 참조가 검색 및 하이드레이션됩니다.
* SITES-29930: 콘텐츠 조각 Rest API: 콘텐츠 조각 게시 워크플로에 대한 지표가 추가되었습니다.
* SITES-29986: 콘텐츠 조각 Rest API: CF 모델 기술 명명이 지원됩니다.
* SITES-30088: 콘텐츠 조각 Rest API: CF 게시 - filterReferencesByStatus가 비어 있으면 참조 검색을 건너뜁니다.
* SITES-30126: 콘텐츠 조각 Rest API: CF 게시 성능 개선: 리소스가 조각인지 확인하는 검사가 최소한의 검사로 대체되었습니다.
* SITES-30328: 범용 편집기가 포함된 Edge Delivery: Sidekick에서 미리보기 기능에 대한 지원이 추가되었습니다.
* SITES-30445: 콘텐츠 조각 Rest API: CF 모델 UI 스키마: 축소 가능한 요소의 초기 상태를 제어하는 옵션이 추가되었습니다.
* SITES-30604: 콘텐츠 조각 Rest API: 새로운 UI에서 모델 메타데이터 스키마 채택이 지원됩니다.
* SITES-30885: 지속 쿼리에서 JSON 처리가 최적화되었습니다.
* SITES-30886: 콘텐츠 조각 Rest API: 워크플로 메타데이터에 저장된 조각 UUID를 기반으로 콘텐츠 조각 엔드포인트에 대한 GET 워크플로가 지원됩니다.
* SITES-31005: 진행 상황을 보여 주기 위해 롤아웃 작업 UI가 개선되었습니다.
* SITES-31020: 진행 상황을 보여 주기 위해 Live Copy 만들기 작업 UI가 개선되었습니다.
* SITES-31111: 콘텐츠 조각 Rest API: 변형 패치 API에서 콘텐츠 조각 내의 콘텐츠 조각 참조를 허용합니다.
* SITES-31343: 콘텐츠 조각 Rest API: 배치 요청을 나열하는 엔드포인트에 날짜별 필터링 및 페이지 매김 기능이 추가되었습니다.
* SITES-31472: 론치 삭제로 인해 론치가 대규모일 경우 저장소가 일시 중지될 수 있습니다.
* SITES-31641: 콘텐츠 조각 Rest API: 확장 기능과 관련된 동적 맵을 저장하기 위한 속성이 모델 필드에 추가되었습니다.
* SITES-31677: 사용자 정의 작업 영역이 AEM 콘텐츠 조각을 Target으로 내보낼 수 있도록 지원합니다.
* SITES-31770: 콘텐츠 조각 Rest API: 패치 성능 개선.
* SITES-31782: 콘텐츠 조각 Rest API: 로컬 자산에 대한 설명이 추가되었습니다.
* SITES-32175: Live Copy 생성과 MSM 페이지 롤아웃 모두에 대한 중간 커밋을 허용합니다.

### 해결된 문제 {#fixed-issues-21331}

* CQ-4359756: 이제 번역 규칙에 구성 요소 수준의 필터 속성이 포함됩니다.
* CQ-4359826: 콘텐츠 조각 참조 패널의 불일치 상태가 해결되었습니다.
* CQ-4359866: 이제 LanguageUtils 클래스는 종속성을 추가하지 않고도 단위 테스트를 지원합니다.
* FORMS-13990: Forms 서비스 API: Document Generation: 선택된 후 값을 비워둔 데이터 필드에 대해 400 오류가 예상되지만 실제로는 200 응답이 반환됩니다.
* FORMS-14309: Forms 서비스 API: 데이터 추출 응답 코드 수정.
* FORMS-18526: 조건에 여러 필드를 포함한 규칙을 복사할 때, 고정된 필드가 변경되지 않습니다.
* FORMS-18977: DOR 서비스가 문서 제목을 전달하지 않습니다.
* FORMS-19047: SP22에서 AEM Forms에 적응형 양식을 게시한 후 번역이 누락됩니다.
* FORMS-19234: AEM 양식에서 PDF의 타임라인 기능을 사용할 수 없습니다.
* FORMS-19628: 자동 생성 DOR에서 중첩된 패널 제목을 제외하면 루트 패널 제목도 숨겨집니다.
* FORMS-19651: 바이너리 조건에 버튼 클릭을 사용하고 then 문에도 동일한 버튼을 사용하는 경우의 규칙이 수정되었습니다.
* FORMS-19808: FormsPortal - 지연 로딩이 활성화된 경우 초안을 가져올 수 없습니다.
* FORMS-19887: Access 속성이 HTML5 미리보기에서 작동하지 않습니다.
* SITES-15452: 출시 시 고유한 CF 요소를 사본과 비교하여 검사해서는 안 됩니다.
* SITES-24492: ARIA 탭 목록에 액세스 가능한 이름이 없습니다.
* SITES-24623: 콘텐츠 조각 Rest API: 동일한 CF에 대한 엔드포인트 간 ETag 불일치가 수정되었습니다.
* SITES-24668: 확대/축소 비율을 400%로 늘리면 참조 레일 기능이 작동하지 않습니다.
* SITES-24678: 참조 레일 상태 메시지가 화면 판독기에서 읽히지 않습니다.
* SITES-24697: 이미지 모델의 로드 상태가 화면 판독기에서 읽히지 않습니다.
* SITES-24708: 확대/축소 비율을 400%로 늘리면 필터 레일 기능이 작동하지 않습니다.
* SITES-25235: 필터 레일 콘텐츠 로드 메시지가 화면 판독기에서 읽히지 않습니다.
* SITES-25254: 콘텐츠를 320px 폭으로 볼 때 슬라이드 모달에 가로 스크롤 막대가 나타납니다.
* SITES-25433: 범용 편집기가 포함된 Edge Delivery: 다국어 사이트 구조에 대한 페이지 버전 렌더링이 수정되었습니다.
* SITES-26064: 콘텐츠 조각 Rest API: 조각을 만들고 백엔드에서 `AccessDeniedException`을 가져올 때 반환되는 상태 코드가 수정되었습니다.
* SITES-26890: 키보드를 사용할 때, 게시 관리 페이지에서 “테이블 헤더” 지정에 대한 키보드 포커스가 표시되지 않습니다.
* SITES-29075: 대규모 웹 사이트에서 Live Copy 개요가 작동하지 않습니다.
* SITES-29514: 범용 편집기가 포함된 Edge Delivery: 새 사이트를 만들 때 GitHub/프로젝트 URL이 필수로 지정되었습니다.
* SITES-29691: 특정 론치 관련 상황에서 페이지를 이동할 수 없습니다.
* SITES-29745: 콘텐츠 조각 Rest API: BFS 순회에서 참조 변형의 하이드레이션이 구현되었습니다.
* SITES-29748: CF 편집기 내에서 managepublication/quickpublish 작업을 표시하도록 renderconditions가 수정되었습니다.
* SITES-29789: 복사된 루트 페이지의 구성 요소 링크가 변경되는 문제가 발생합니다.
* SITES-29987: 콘텐츠 조각 Rest API: 콘텐츠 조각 만들기 및 편집 모델이 `previewUrlPattern`을 지원하지 않습니다.
* SITES-30140: 콘텐츠 조각 참조를 만들 때 이중 창 문제가 발생합니다.
* SITES-30327: 콘텐츠 조각 Rest API: 권한 없이 CF를 게시하면 페이로드 리소스마다 별도의 워크플로가 생성됩니다.
* SITES-30333: XMP 구문 분석 문제가 발생하는 것을 방지하기 위해 jcr에서 자산 메타데이터를 읽습니다.
* SITES-30353: AEM 콘텐츠 조각의 “src” 필드에 대한 GraphQL DataFetchingExceptions.
* SITES-30377: 범용 편집기가 포함된 Edge Delivery: 조직 및 사이트 이름이 삭제되었습니다.
* SITES-30386: 범용 편집기가 포함된 Edge Delivery: 중복된 레거시 UE `cors.js`가 제거되었습니다.
* SITES-30583: 콘텐츠 조각 Rest API 찾기 및 바꾸기 도구를 사용하면 모든 문자가 소문자로 변경됩니다.
* SITES-30585: 콘텐츠 조각 Rest API: 참조가 포함된 CFM 생성 시 `previewUrlPattern`이 설정되지 않습니다.
* SITES-30634: RTE 이미지 대체 텍스트 및 정렬이 일관되게 작동하지 않습니다.
* SITES-30660: 사용자 정의 AEM 구성 요소와 관련된 ADA 규정 준수 문제.
* SITES-30695: 범용 편집기가 포함된 Edge Delivery: 사용자 정의 코드를 방해하지 않도록 재작성기 파이프라인의 순위가 상향 조정되었습니다.
* SITES-30727: 프로덕션 작성자 편집기에서 구성 요소를 끌어다 놓을 수 없습니다.
* SITES-30752: 지속 쿼리 응답을 생성할 때 `If-modified-since`/`last-modified` 헤더를 사용하면 안 됩니다.
* SITES-30871: afteredit 리스너가 트리거된 후 DOM이 업데이트됩니다.
* SITES-30877: 잘못된 하위 페이지 롤아웃 상태.
* SITES-30899: “나중에” 롤아웃 옵션을 사용하면 날짜를 선택하지 않고도 계속 진행할 수 있습니다.
* SITES-30947: 롤아웃 중 블루프린트에 “behavior” 속성이 없어 null 포인터 예외가 발생합니다.
* SITES-31157: 콘텐츠 조각 Rest API: 특정 경우에 패치가 실패합니다.
* SITES-31162: 콘텐츠 조각 Rest API: `ModelFieldMapper`의 `DateTimeField` 필드에 대한 캐스팅 문제가 해결되었습니다.
* SITES-31174: 콘텐츠 조각 Rest API: 태그가 게시 요청과 함께 게시되지 않았습니다.
* SITES-31272: PageManager.copy를 통해 자산 언어 사본을 생성할 수 없습니다.
* SITES-31327: 콘텐츠 조각 Rest API: GET 조각 요청에서 ETag 유효성 검사가 제거되었습니다.
* SITES-31387: Ghost 구성 요소 상속을 다시 활성화할 때 “ns.ui.alert는 함수가 아닙니다”라는 JavaScript 오류가 발생합니다.
* SITES-31454: 콘텐츠 조각 Rest API: 조각 참조 필드에 대한 패턴이 UUID도 허용하도록 완화되었습니다.
* SITES-31455: 콘텐츠 조각 Rest API: 동일한 콘텐츠 조각 모델에 대한 엔드포인트 간 ETag 불일치가 수정되었습니다.
* SITES-31459: 콘텐츠 조각 Rest API: 콘텐츠 참조 필드가 있는 경우 CF Live Copy를 편집할 수 없습니다.
* SITES-31467: 페이지 편집기의 contexthub.authoring-hook.js에서 js 오류가 발생합니다.
* SITES-31487: 콘텐츠 조각 Rest API: 루트 폴더에 대한 권한 엔드포인트가 호출되도록 허용합니다.
* SITES-31621: 범용 편집기가 포함된 Edge Delivery: Live Copy인 스프레드시트에서 빈 행이 제거되었습니다.
* SITES-31676: 구성 요소를 작성하거나 삭제하면 페이지 하단에 공백이 생깁니다.
* SITES-31822: ClassicUI 체크박스 레이블이 누락되고 HTML이 인코딩되어 표시됩니다.
* SITES-31857: 작은 따옴표가 포함된 폴더에서 CF 생성이 실패합니다.
* SITES-31888: 콘텐츠 조각 삭제가 미리보기에 전파되지 않습니다.
* SITES-31922: 콘텐츠 조각 Rest API: referencedBy 엔드포인트가 페이지 참조를 반환하지 않습니다.
* SITES-31987: 미리보기에 콘텐츠 조각을 게시할 때 해당 콘텐츠 조각의 previewURL이 표시되지 않습니다.
* SITES-32095: Live Copy의 afterchilddelete 이벤트 리스너에서 자동 새로 고침이 실패합니다.
* SITES-32237: 범용 편집기가 포함된 Edge Delivery: 비어 있거나 형식이 잘못된 텍스트 구성 요소의 렌더링이 수정되었습니다.

### 알려진 문제 {#known-issues-21331}

* SITES-33177: 쉼표로 구분된 문자열로 저장된 섹션 스타일이 중단됩니다.

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
