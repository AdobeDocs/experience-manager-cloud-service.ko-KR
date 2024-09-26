---
title: ' [!DNL Adobe Experience Manager] as a Cloud Service의 현재 유지 관리 릴리스 정보입니다.'
description: ' [!DNL Adobe Experience Manager] as a Cloud Service의 현재 유지 관리 릴리스 정보입니다.'
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: fa2da21ef6424bce0830d503eba650e1c1bf3dc2
workflow-type: tm+mt
source-wordcount: '1353'
ht-degree: 14%

---


# 유지 관리 릴리스 정보 {#maintenance-release-notes}

다음 섹션에서는 Experience Manager as a Cloud Service 현재 유지 관리 릴리스의 기술 릴리스 정보에 대해 간략히 소개합니다.

## 릴리스 17964 {#release-17964}

다음은 2024년 9월 25일에 공개적으로 릴리스된 유지 보수 릴리스 17964에 대한 지속적인 개선 사항을 요약합니다. 이전 유지 관리 릴리스는 릴리스 17689. 문제17882 인해 릴리스 정보가 비공개로 설정되었습니다.

2024.10.0 기능 활성화는 이 유지 관리 릴리스에 대한 전체 기능 세트를 제공합니다. 자세한 내용은 [Experience Manager 릴리스 로드맵](https://experienceleague.adobe.com/ko/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap)을 참조하십시오.

### 개선 사항 {#enhancements-17964}

* ASSETS - 37750: [우선 순위 4] [GraphQL] DM scene7 URL 지원: 이미지 스마트 자르기.
* CQ - 4354583: [AEMaaCS] Adobe 파이프라인을 통해 번역 프로세스 이벤트를 보냅니다.
* CQ - 4357642: OOTB 커넥터의 MSFT 자격 증명을 업데이트합니다.
* CQ - 4358217: 요청 엔티티에서 요청 본문을 역직렬화합니다.
* CQ - 4358342: 하나의 HTTP 메서드에만 RequestProcessors를 등록합니다.
* FORMS - 10781: 패널의 다음/이전 항목에 대한 규칙을 만들 수 있도록 규칙 편집기를 개선합니다.
* FORMS - 14595: 브라우저 없는 렌더링에 대한 DoR을 계산하는 데 미리 채워진 데이터를 사용할 때 DoR에 [브라우저 없는 기능] 값이 없습니다.
* FORMS - 15619: AEM Forms에서 번역 키트를 업데이트했습니다.
* FORMS - 16113: [Adobe Sign]다른 사용자가 계약 상태를 업데이트할 수 없습니다.
* FORMS - 16155: [규칙 편집기] 비동기 함수 구현.
* GRANITE - 53872: IMS 클라이언트 ID에 대한 새 환경 변수를 추가합니다.
* 사이트 - 23738: 릴리스 핵심 구성 요소 2.27.0.
* SITES - 16610: 콘텐츠 조각: 실행 세부 정보 끝점 가져오기.
* SITES - 16614: 콘텐츠 조각: Launch 엔드포인트 재지정.
* SITES - 16615: 콘텐츠 조각: 론치 홍보 엔드포인트.
* SITES - 24215: 콘텐츠 조각: Launch 소스 가져오기 엔드포인트 구현
* SITES - 20336: 콘텐츠 조각: 콘텐츠 조각 모델을 삭제할 때 유효성 검사를 개선합니다.
* SITES - 21090: 콘텐츠 조각: 숫자 필드에 대한 분수 최소/최대 값에 대한 지원을 추가합니다.
* 사이트 - 21658: 콘텐츠 조각: UUID 참조를 사용하도록 업그레이드합니다.
* 사이트 - 23054: 콘텐츠 조각: 콘텐츠 조각 모델 복사.
* SITES - 23264: 콘텐츠 조각: 모델의 정적 스키마를 만듭니다.
* SITES - 23265: 콘텐츠 조각: UI 스키마 GET 엔드포인트를 통해 모델의 정적 스키마를 노출합니다.
* 사이트 - 23266: 콘텐츠 조각: 콘텐츠 조각 모델에 제약 조건을 추가하는 기능.
* SITES - 23778: 콘텐츠 조각: 콘텐츠 조각 모델 검색 은 게시된 적이 없는 모델을 검색할 수 있도록 허용해야 합니다.
* SITES - 23335: 콘텐츠 조각: 외부 에셋 참조에 대한 지원을 추가합니다.
* 사이트 - 24626: 콘텐츠 조각: RTC: UUID 마이그레이션에 대한 권한: 2.
* SITES - 24786: 콘텐츠 조각: `referencesTree` 끝점에 대한 개선 사항입니다.
* SITES - 24833: 콘텐츠 조각: 허용된 HTML 태그 목록에 대한 HTML 입력 유효성 검사를 제거합니다.
* SITES - 23380: GraphQL: 적절한 API를 사용하여 에셋 메타데이터를 읽습니다.
* SITES - 22864: [Edge Delivery] 새로운 AEM 콘텐츠 구조 통합 H2 2024가 포함된 유니버설 편집기.
* SITES - 23584: Java 17에서 기초 구성 요소 테스트가 실패합니다.
* SITES - 23662: 이벤트: 게시 요청을 트리거하는 사용자는 서버 로그의 JCR 로그 문에서 추출할 수 없습니다.
* 사이트 - 23301: 콘텐츠 조각의 번역을 만들 때 폴더 구조를 만드는 새 워크플로를 시작하는 데 대한 지원을 추가합니다.
* SITES - 23336: 콘텐츠 조각: 외부 에셋 참조에 대한 지원 추가
* 사이트 - 24091: MSM 콘텐츠 패키지 분할: 마스터.
* SITES - 24114: isSourceRenderCondition: 오류 로그 메시지를 DEBUG로 줄입니다.
* SITES - 24166: Touch-UI 편집기에 대한 원격 자산 완화.
* SITES - 24409: 하나의 HTTP 메서드에만 모든 요청 프로세서를 등록합니다.
* SITES - 25008: PersistenceExceptions 및 권한 문제의 처리를 개선합니다.
* SITES - 24821: [Xwalk] aem.page / aem.live를 기본값으로 설정합니다.

### 해결된 문제 {#fixed-issues-17964}

* CQ - 4356887: Akamai Technologies Inc.의 번역 프로젝트 상태 불일치
* CQ - 4357878: 공급업체 실패 번역 시 번역 프레임워크가 오류 상태를 설정하지 않습니다.
* CQ - 4358028: 썸네일을 업로드한 경우 프로젝트를 만들지 못했습니다.
* CQ - 4358290: Target 설정이 게시된 페이지에서 작동하지 않습니다.
* FORMS - 13173: 적응형 양식 > 규칙 편집기 > 개체 놓기 필드의 드롭다운 목록 오정렬.
* FORMS - 13873: 구성 요소 이름의 AFv2: (&quot;-&quot;)로 인해 규칙이 실패합니다.
* FORMS - 14340: FormsAndDocumentOmniSearchHandler 및 CloudStorageSubmitActionInserter를 인스턴스화하는 동안 오류가 발생했습니다.
* FORMS - 15363: 규칙 편집기에 표시된 이름입니다.
* FORMS - 15381: 인증 범위 메시지의 UI 개선.
* FORMS - 15595: AEM 양식 TnC 구성 요소 동의 텍스트 줄 바꿈 문제.
* FORMS - 15623: AEMaaCS Forms - 하나의 POST으로 Dynamics에서 여러 표를 업데이트할 수 있는 대체 방법입니다.
* FORMS - 15682: AEM Forms - DOR을 Dynamics FDM에 바인딩할 수 없습니다.
* FORMS - 15799: Adobe Sign GovCloud 서명 페이지는 iframe에서 렌더링되는 것을 확인합니다.
* FORMS - 15835: 사후 제출 양식 URL 재작성 문제.
* FORMS - 16091: 재구성된 Binary.java를 사용합니다.
* FORMS - 16096: Forms 사용자에게 restendpoint 대화 상자에 대한 액세스 권한이 없습니다.
* FORMS - 16139: 핵심 구성 요소 양식에서 DoR에 대한 필수 로깅을 추가합니다.
* FORMS - 6935: 활성 구성 요소의 상태에 3:1 명암비가 없습니다.
* FORMS - 7018: 빈 요소가 포커스를 받습니다.
* GRANITE - 53028: ExternalProcessPollingHandler의 NPE.
* GRANITE - 53907: 서비스 사용자를 워크플로우 수퍼 사용자로 식별할 수 없습니다.
* SITES - 24405: 콘텐츠 조각: 열거형에 대한 확장 정보가 보다 탄력적이어야 합니다.
* SITES - 23024: 콘텐츠 조각: 열거형이 GET 조각에서 locked: true를 반환하지 않습니다.
* 사이트 - 23269: 콘텐츠 조각: 콘텐츠 조각을 만들면 잠긴 필드를 설정할 수 있습니다.
* SITES - 23337: 콘텐츠 조각: `body`을(를) 사용한 일괄 처리 끝점이 캐스팅 예외로 인해 실패합니다.
* 사이트 - 23474: 콘텐츠 조각: 페이지 매김은 콘텐츠 조각 검색에서 끊어진 리소스를 제외해야 합니다.
* 사이트 - 23615: 콘텐츠 조각: 콘텐츠 조각 사본 AuthoringInfo가 업데이트되지 않음
* 사이트 - 23668: 콘텐츠 조각: 다중 필드가 있는 라이브 카피 패치가 400으로 실패함
* SITES - 23695: 콘텐츠 조각: 탭 설명을 UiSchema에서 사용할 수 없음
* SITES - 23704: 콘텐츠 조각: _extendedInfo에서 다중 값 열거형이 지원되지 않음
* 사이트 - 23781: 콘텐츠 조각: 열거 필드에 중복 값을 사용할 수 없음
* SITES - 24150: 콘텐츠 조각: 콘텐츠 조각 버전 작성에 대한 데이터가 누락되었습니다
* SITES - 24230: 콘텐츠 조각: 검색 콘텐츠 조각 모델에서 `modified` 복제 상태 후 필터링 수정
* SITES - 24233: 콘텐츠 조각: `publishedBy`별 필터링은 콘텐츠 조각 검색 모델에 게시되지 않은 리소스를 포함할 수 있습니다.
* SITES - 24355: 콘텐츠 조각: 라이브 관계가 폴더에서 만든 콘텐츠 조각에 대해 적용되지 않음
* SITES - 24816: 콘텐츠 조각: ValidationStatus 메시지의 순서가 일치하지 않습니다.
* SITES - 23896: 이벤트: 더 많은 이벤트가 페이지 이동 이벤트와 함께 제공됩니다
* SITES - 23899: 이벤트: 페이지 이벤트가 지연되거나 전혀 생성되지 않음
* SITES - 23961: 이벤트: 구성 폴더가 있는 경우 참조를 사용하여 콘텐츠 조각 모델을 만들 수 없음
* SITES - 23963: 이벤트: 페이지가 삭제된 이벤트가 가끔씩 발생하지 않음
* SITES - 23443: GraphQL: GraphQL 커서 쿼리가 일치하지 않는 동작입니다.
* SITES - 10994: 키보드 포커스 순서가 논리적이지 않습니다.
* 사이트 - 16357: AEM: 사이트 메뉴의 Analytics 설정 탭에서 단추가 잘립니다.
* SITES - 19836: 컨테이너의 유령 구성 요소가 게시 및 미리보기 인스턴스에 표시됩니다.
* 사이트 - 22348: 프로젝트의 라이브 카피가 100개를 초과하는 경우 라이브 카피 개요 페이지를 로드할 수 없습니다.
* SITES - 22960: ContentFragmentModelOmniSearchHandler에서 리소스 확인자가 닫히지 않았습니다.
* SITES - 23284: URL 인코딩으로 빈 경로 브라우저 대화 상자가 발생합니다.
* SITES - 23505: 페이지를 다른 위치로 이동할 때 구성 요소에 잘못된 URL이 표시됩니다.
* SITES - 23574: 많은 페이지에 대해 현재 버전을 미리 보거나 비교할 수 없음
* SITES - 23585: cq:responsive 노드가 있는 구성 요소의 상속 복원 문제
* 사이트 - 23650: AEM 작성자 환경의 수신 링크 수 불일치
* 사이트 - 23659: FT_* SITES - 9757 전환에 의해 발생한 콘텐츠 언어 서블릿 회귀
* 사이트 - 23759: 경험 조각에 추가된 Assets은 론치와 함께 게시되지 않습니다
* SITES - 24025: AEM에서 공용 DNS 대신 내부 DNS를 사용하여 위치 헤더를 반환하는 302개의 리디렉션
* SITES - 24036: ASCII 형식의 문자를 유지하는 AEM RTE에 대한 조사가 필요합니다.
* SITES - 24317: 프록시 구성이 기본 인증에서 작동하지 않음
* 사이트 - 24918: [Xwalk] 전용 IP 이그레스를 사용할 때 가끔 반환되는 504 오류를 수정합니다.

### 알려진 문제 {#known-issues-17964}

* FORMS - 15818: 구성 요소 설명자 항목 `OSGI-INF/com.adobe.aemfd.docmanager.impl.*.xml`을(를) 서버 로그에서 찾을 수 없습니다. 이는 해를 미치지 않는 로그 구문입니다.

### 사용 중단된 기능 및 API {#deprecated-17964}

현재 `com.day.cq.wcm.api` 업데이트가 진행 중이며, 현재 릴리스에서는 몇 가지 메서드와 클래스를 `@Deprecated`로 표시했습니다. 이러한 기능은 향후 릴리스에서 제거될 예정이므로, 해당 기능을 사용 중이라면 제안된 대체 기능으로 전환하는 것을 고려해 보시기 바랍니다.

AEM as a Cloud Service에서 더 이상 사용되지 않는 기능과 API는 [사용 중단된 기능 및 API](/help/release-notes/deprecated-removed-features.md) 문서에 자세히 설명되어 있습니다.

### 보안 수정 {#security-17964}

AEM as a Cloud Service는 플랫폼의 보안 및 성능을 최적화하는 데 사용됩니다. 이 유지 관리 릴리스는 16개의 식별된 취약점을 해결하여 강력한 시스템 보호에 대한 노력을 강화합니다.

### 임베드된 기술 {#embedded-tech-17964}

| 기술 | 버전 | 링크 |
|---|---|---|
| AEM Oak | 1.68.0 | [Oak API 1.68.0 API](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.68.0/index.html) |
| AEM SLING API | 2.27.6 | [Apache Sling API 2.27.6 API](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 1.4.24-1.4.0 | [HTML 템플릿 언어 사양](https://github.com/adobe/htl-spec) |
| AEM 핵심 구성 요소 | 2.27.0 | [AEM WCM 핵심 구성 요소](https://github.com/adobe/aem-core-wcm-components) |
