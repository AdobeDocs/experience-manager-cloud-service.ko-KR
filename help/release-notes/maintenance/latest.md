---
title: ' [!DNL Adobe Experience Manager] as a Cloud Service의 현재 유지 관리 릴리스 정보입니다.'
description: ' [!DNL Adobe Experience Manager] as a Cloud Service의 현재 유지 관리 릴리스 정보입니다.'
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
source-git-commit: d107f40c4bc43837db9d8fab3d06627d9e930620
workflow-type: tm+mt
source-wordcount: '1574'
ht-degree: 8%

---

# 유지 관리 릴리스 정보 {#maintenance-release-notes}

다음 섹션에서는 Experience Manager as a Cloud Service 현재 유지 관리 릴리스의 기술 릴리스 정보에 대해 간략히 소개합니다.

## 릴리스 16357 {#release-16357}

2024년 5월 22일에 공개적으로 릴리스된 유지 보수 릴리스 16357에 대한 지속적인 개선 사항을 요약하면 다음과 같습니다. 이전 유지 관리 릴리스는 릴리스 16145.

2024.5.0 기능 활성화는 이 유지 관리 릴리스에 대한 전체 기능 세트를 제공합니다. 자세한 내용은 [Experience Manager 릴리스 로드맵](https://experienceleague.adobe.com/ko/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap)을 참조하십시오.

### 개선 사항 {#enhancements-16357}

* SITES-19579: 콘텐츠 조각을 한 모델에서 다른 모델로 마이그레이션하기 위한 Java API입니다.
* SITES-19698 [API 열기] OpenAPI 정의에서 모델별 UI 스키마를 관리하기 위한 읽기 작업을 만듭니다.
* SITES-19834: Adobe I/O 이벤트에 게시/게시 취소에 대한 ID가 누락되었습니다.
* SITES-20146: 이동된 페이지에 대해 버전 미리보기/비교를 활성화합니다.
* SITES-19973: CFM 검색 API 구현.
* SITES-20333: 콘텐츠 조각을 만들 때 유효성 검사를 개선합니다.
* SITES-20334: 콘텐츠 조각 모델을 편집할 때 유효성 검사를 개선합니다.
* SITES-20585: 로케일별로 필터링하도록 콘텐츠 조각 검색 API를 개선합니다.
* SITES-20594: 리소스를 생성/수정/복제하는 사용자의 전체 이름을 반환합니다.
* SITES-20601 [오픈 API] 직접 하위 콘텐츠 조각만 가져올 수 있도록 CF Search API를 업데이트합니다.
* SITES-20656 [BE] 문자열을 바꿀 때 대/소문자를 일치시키는 옵션을 제공하십시오.
* SITES-20405 [Xwalk] 필드 축소용 mimeType 지원
* SITES-17854: CF 및 자산 참조에 대한 UUID를 지원합니다(Pfizer MVP).
* SITES-19555: UI 스키마에 대한 간단한 모델 API.
* SITES-19611 [API 열기] OpenAPI 정의에서 모델별 UI 스키마를 관리하기 위한 쓰기/업데이트 작업을 만듭니다.
* SITES-19614 [Xwalk] 스프레드시트 페이지 매김/무한 스크롤.
* SITES-20005: 작성자 파이프라인에는 구성 가능한 이벤트 지연이 있어야 합니다.
* SITES-20121: 열거형 필드에 defaultValue를 허용합니다.
* SITES-20342 [백엔드] 폴더 수준에서 게시 - CF만 게시하려면 필터를 추가하십시오.
* SITES-20355: 콘텐츠 조각 모델 및 권한 API 서블릿을 제거합니다.
* SITES-20387: tagadmin을 탐색하면 항상 태그 사용량이 계산됩니다.
* SITES-20495 [BE] 폴더 수준에서 게시할 수 있는 권한을 받는 기능입니다.
* SITES-20653 [Xwalk] experiment-start-date 및 -end-date 를 추가합니다.
* SITES-20666 [Xwalk] 작성 시 기본적으로 실험의 기능을 꺼야 합니다.
* SITES-20752 [cq-wcm-core] Apple CF 출시
* SITES-20946: LIST 모델 엔드포인트에 속성으로 etag를 추가합니다.
* SITES-20947 [지속성] 콘텐츠 조각 id로 하위 작업을 가져옵니다.
* SITES-21012: 모델 메타데이터 스키마를 제품에 병합합니다.
* SITES-21769: resource-by-id 검색에 /jcr:id/ 경로 접두사를 사용합니다.
* ASSETS-30379: DRM 라이센스 체크는 다운로드 중인 에셋의 전체 트리를 표시합니다.
* 자산-35535: [DaaS 어댑터 오류] v1 이벤트의 경우 빈 자산 다운로드를 무시해야 합니다.
* SITES-21550 [Xwalk] 사용자 지정 메타데이터: 숫자, 날짜, 날짜, 시간 필드.
* SITES-20149: RTC: [cq-wcm-launches-core] CF를 위한 론치를 위해 새 API를 내보냅니다.
* SITES-20150: RTC: [cq-command] 기존 API에 새 메서드를 추가합니다.
* SITES-20451: 사이드카 플러그인을 wcm-commons에 추가합니다.
* SITES-20499 [MSM][Async] AsyncOperationServlet에서 유틸리티 클래스로 코드를 추출합니다.
* SITES-20763: 사이트 통합에서 게재 API 엔드포인트를 업데이트합니다.
* SITES-20583: 에태그를 속성으로 추가 `LIST`/search 조각.
* CQ-4356445: 이벤트 생산자 및 스키마 구현.
* CQ-4356625: languagecopyrendercondition.jsp에서 인증 검사를 개선합니다.
* CQ-4356629: isWorkflowUser rendercondition에서 권한 부여 검사를 개선합니다.
* CQ-4356934: ResponseEntities로 작업할 때 RequestProcessor API를 간소화합니다.
* CQ-4357214: 요청 프로세서가 서블릿 논리에 종속되지 않아야 합니다.
* SITES-16392: 시작 생성에 실패해도 가비지 콘텐츠가 남아있지 않아야 합니다.
* SITES-20238 [RTC] Pfizer MVP - CF API를 추가하여 ID에 대한 CF 경로를 확인하거나 그 반대로 확인합니다.
* SITES-21043 [CF][launches] Cloud Service의 측면 포트 성능 향상.
* SITES-21044 [CF][launches] Side-port 비동기 편집 페이로드 구현을 Cloud Service에 추가합니다.
* FORMS-7483: 이제 AEM Forms JSON 스키마 파서가 JSON 스키마(2020-12)를 지원합니다.
* FORMS-13209: 적응형 Forms 기본 제출 성공 및 제출 실패 핸들러를 재정의하는 핸들러가 포함됩니다. 적응형 Forms 규칙 편집기를 통해 이러한 핸들러를 구성할 수 있습니다.
* FORMS-13612: 이제 화면 판독기에서 핵심 구성 요소 기반 적응형 Forms의 필드에 대한 오류 메시지, 간단한 설명 및 긴 설명을 읽습니다. 또한 양식에 오류가 있고 제출에 유효하지 않은 경우 적응형 양식 입력을 무효화할 수 있는 지원이 추가되었습니다.
* FORMS-12052: 이제 양식 작성자가 제출 전에 사용자 지정 함수를 적용하여 데이터를 사전 처리할 수 있습니다.
* FORMS-11295: AEM Forms 디지털 서명에 대한 ECDSA 알고리즘으로 SHA256에 대한 지원이 추가되었습니다.
* FORMS-9432: 추가 콘텐츠 유형(REST 끝점)이 데이터 소스 클라우드 구성에 추가되었습니다. 이 옵션을 사용하면 키-값 쌍으로 인증된 끝점에 데이터를 제출할 수 있습니다.

### 해결된 문제 {#fixed-issues-16357}

* SITES-20608: 템플릿에 포함될 때 개인화가 활성화된 경험 조각으로 인해 무한 루프가 발생합니다.
* SITES-19554 [Xwalk] 스프레드시트 편집기: 셀을 비워 둘 수 없습니다.
* SITES-19971: 탭이 포함된 CFM을 패치하면 필드의 순서가 변경됩니다.
* SITES-20168: 콘텐츠 조각 모델 `locked` 필드가 제대로 업데이트되지 않았습니다.
* SITES-20522: 손상된 콘텐츠 조각이 /adobe/sites/cf/fragments 엔드포인트를 중단합니다.
* SITES-20816: CF OpenAPI - 참조된 조각에 대한 모델 누락으로 출력 불일치.
* SITES-21239: ContentFragmentSearchService 순환 종속성을 제거합니다.
* SITES-20582: 콘텐츠 조각을 검색하고 나열하려면 깊이 0을 허용해야 합니다.
* SITES-20559: [MSM][XF][Lufthansa] 마스터/언어에서 국가/언어로 경험 조각을 롤아웃해도 참조가 업데이트되지 않습니다.
* SITES-17772: AEM: 관리자 그룹을 가진 사용자가 다른 사용자가 잠근 페이지를 잠금 해제할 수 없습니다.
* SITES-20401 [Xwalk] 섹션 메타데이터가 다중 값 속성을 지원하지 않습니다.
* SITES-21391 [OpenAPI 이벤트] 콘텐츠 조각 모델의 제목 또는 태그(속성)를 수정할 때 트리거되는 이벤트가 없습니다.
* SKYOPS-73234: AEM 릴리스 15553 및 PR ID 35362으로 AEM Assets 글로벌 DAM 프로그램을 업그레이드할 때 오류 로그 오류가 증가합니다.
* SKYOPS-75341: 배포 횡단보도 번들에 NoSuchMethodError가 있습니다.
* SCRNS-3945: Skyline: Screens에 현지화되지 않은 &quot;예약됨&quot; 문자열입니다.
* SITES-20586: 템플릿 &quot;게시됨&quot; 타임스탬프가 업데이트되지 않았습니다.
* SITES-16674: Live Copy 속성에서 사용할 수 없는 롤아웃 구성 상속 확인란입니다.
* SITES-18680: graphql 쿼리(Apple)에서 참조 변형을 가져올 수 없습니다.
* SITES-21233 [CoreCmp] Analytics로 업그레이드한 후 GS1 US에 대한 아코디언이 15860.
* SITES-20367: AEM에서 론치 삭제 문제.
* CQ-4357161: AEM 받은 편지함 페이로드 화면이 404를 반환합니다.
* SITES-20214: 저장 시 AEM 롤아웃 구성 시퀀스 문제.
* SITES-20364: URL의 선택기에서 302 리디렉션이 작동하지 않습니다.
* SITES-20547: 라이브 카피 제외 경로 목록에서 AEMas a Cloud Service 의 잘린 경로
* SITES-20691: 경험 조각 템플릿 제한이 cq:allowedTemplates를 준수하지 않습니다.
* SITES-21122: 콘텐츠 조각이 있는 AEM CS Live Copy 오류입니다.
* ASSETS-38723: 이.readRules가 초기화되기 전에 getReadRulesForMetadataChildNodes()가 호출될 때 MetadataRulesProviderImpl이 throw한 NPE입니다.
* SITES-11727 [GQL] 콘텐츠 조각 참조의 전체 하이드레이션에는 데이터가 없습니다.
* SITES-19462: AEM Cloud에서 에셋 검색이 제대로 작동하지 않습니다.
* SITES-19994: 사용자가 콘텐츠 조각을 닫으려고 할 때 닫기 버튼 클로킹이 발생합니다.
* SITES-20029: 컨텐츠 조각 버전은 컨텐츠를 변경하지 않고 닫기 직전에 생성됩니다.
* SITES-21316: 조각 미리보기: SITES-11727의 코드 변경으로 인해 미리보기가 실패합니다.
* SITES-20023: 다중 필드의 원격(다음 세대 에셋) 에셋에 대해 파일 업로드가 작동하지 않습니다.
* ASSETS-37611: 게시되지 않은 자산에 대해 &quot;이동 작업 완료 요청&quot; 워크플로우가 트리거됩니다.
* CQ-4357278: getRequestBodyType이 null을 반환하는 경우 DispatcherServlet이 NPE를 throw합니다.
* CQ-4357279: 요청에 대한 pathInfo가 없으면 요청 처리가 실패합니다.
* SITES-20496 [Xwalk] 사이트 관리자에서 스프레드시트를 선택할 때 속성 옵션이 없음.
* FORMS-13827: 적응형 Forms 규칙 편집기에서 WHEN 작업은 현재 날짜 선택기가 있는 다른 유형의 필드를 지원하지 않습니다.
* FORMS-13786: 적응형 Forms 규칙 편집기에서 드래그 앤 드롭 기능이 사용자 정의 함수에 작동하지 않습니다.
* FORMS-13587: 적응형 Forms 편집기에서, 장치 에뮬레이터 기능이 적응형 Forms 기반의 핵심 구성 요소에 대해 제대로 작동하지 않습니다.
* FORMS-14376 사용자가 재설정 버튼을 누르면 정적 텍스트가 바인딩 해제된 것으로 표시되는 경우 콘솔 오류가 발생합니다.
* FORMS-13801: 약관 구성 요소가 비활성화되어 있더라도 해당 확인란은 활성화된 상태로 유지됩니다.
* FORMS-11952: 양식을 제출할 때 양식에서 생성된 제출 URL이 /portale/ 대신 /content/ 로 시작되어 요청 라우팅이 잘못되었습니다. 이렇게 하면 요청이 의도한 서버에 도달하지 못합니다.
* FORMS-13616: 시간대 문제로 인해 날짜 선택기에서 현재 날짜를 하루 늦춰 표시하고 있으며, 이 불일치 및 추가 표시 패턴 문제로 인해 올바른 날짜 형식을 설정하는 데 문제가 있습니다.
* FORMS-13829: 선택 항목을 지우고 다시 선택한 후 라디오 버튼 기능을 모방하도록 규칙에 의해 제어되는 드롭다운이 올바르게 채워지지 않습니다. 원하는 동작은 개별 확인란이 라디오 단추로 동작하여 한 번에 하나의 선택만 허용하고 모든 옵션의 선택을 해제하는 것입니다.
* FORMS-14244: XDP를 기반으로 하는 적응형 양식에서 체크박스에 스크립트가 임베드되어 있으면 체크박스 이후의 요소에 대해 스크립트가 실행되지 않습니다.
* FORMS-14267: 개발, 단계 및 프로덕션 환경에서 API 요청을 전송할 때 일관된 시간 초과 오류가 발생합니다. 이러한 요청은 때로 데이터 바인딩을 사용하여 미리 채워진 데이터로 PDF 생성과 관련되어 있습니다. 이 문제로 인해 중단 프로세스가 발생하고 결국 시간이 초과되지만 오류 발생 후 재시도에 성공합니다.
* FORMS-11589: AEM Forms 솔루션만 있는(다른 솔루션은 없음) 사용자의 경우 프론트엔드 파이프라인이 작동하지 않습니다.
* FORMS-13896: DoR(Document of Record) 출력에서 날짜 및 숫자는 입력 데이터가 그레고리오 숫자를 사용하여 병합되는지 여부에 관계없이 아랍어로 표시됩니다.

### 알려진 문제 {#known-issues-16357}

없음.

### 사용 중단된 기능 및 API {#deprecated-16357}

AEM as a Cloud Service에서 더 이상 사용되지 않는 기능을 살펴보려면 [사용 중단된 기능 및 API](/help/release-notes/deprecated-removed-features.md)를 참조하십시오.

### 임베드된 기술 {#embedded-tech-16357}

| 기술 | 버전 | 링크 |
|---|---|---|
| AEM Oak | 1.62.0 | [Oak API 1.62.0 API](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.62.0/index.html) |
| AEM SLING API | 2.27.2 | [Apache Sling API 2.27.2 API](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 1.4.22-1.4.0 | [HTML 템플릿 언어 사양](https://github.com/adobe/htl-spec) |
| AEM 핵심 구성 요소 | 2.25.4 | [AEM WCM 핵심 구성 요소](https://github.com/adobe/aem-core-wcm-components) |
