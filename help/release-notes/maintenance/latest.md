---
title: ' [!DNL Adobe Experience Manager] as a Cloud Service의 현재 유지 관리 릴리스 정보입니다.'
description: ' [!DNL Adobe Experience Manager] as a Cloud Service의 현재 유지 관리 릴리스 정보입니다.'
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: 0f16c31a5fea1fc538fbeabe6db182ad3a30560d
workflow-type: tm+mt
source-wordcount: '1619'
ht-degree: 10%

---


# 유지 관리 릴리스 정보 {#maintenance-release-notes}

다음 섹션에서는 Experience Manager as a Cloud Service의 현재 유지 관리 릴리스에 대한 기술 릴리스 정보를 간략히 소개합니다.

## 릴리스 21772 {#21772}

다음은 2025년 8월 6일에 공개적으로 릴리스된 유지 보수 릴리스 21772에 대한 지속적인 개선 사항을 요약합니다. 이전 유지 관리 릴리스는 릴리스 21706.

2025.8.0 기능 활성화는 이 유지 관리 릴리스에 대한 전체 기능 세트를 제공합니다. 자세한 내용은 [Experience Manager 릴리스 로드맵](https://experienceleague.adobe.com/ko/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap)을 참조하십시오.

### 새로운 기능  {#new-features-21772}

* SITES-30049: UUID로 콘텐츠 조각의 언어 사본을 검색하기 위한 새 끝점을 추가했습니다.

### 개선 사항 {#enhancements-21772}

* CQ-4358722 : Java 11과 Java 17 간에 로케일 코드가 달라 발생하는 현지화 문제를 해결했습니다.
* FORMS-19624: 대화형 통신(IC)을 활성화했습니다. 조직에서는 구조화된 템플릿을 동적 데이터와 결합하여 명세서, 청구서, 서신 등의 개인화된 온디맨드 커뮤니케이션을 제공할 수 있습니다. IC는 웹 기반 템플릿 디자인, 재사용 가능한 콘텐츠 조각, 규칙 기반 변형 및 원활한 데이터 통합과 같은 기능을 통해 채널 전반에서 일관되고 확장 가능한 고객 커뮤니케이션을 지원합니다.
* FORMS-19587, FORMS-17107, FORMS-19591, FORMS-19582, FORMS-20129, FORMS-20002, FORMS-19593, FORMS-20655, FORMS-19583, FORMS-18024, FORMS-19581: Forms 규칙 편집기가 다음과 같이 개선되었습니다.
   * 이제 함수 목록의 `validate` 메서드에서 패널, 필드 및 양식의 유효성을 검사할 수 있습니다.
   * ES10+ 기능 및 정적 가져오기를 지원하도록 클라이언트측 사용자 지정 함수 구문 분석이 개선되었습니다.
   * 규칙 편집기에 기본 제공(OOTB) &quot;기록 문서 다운로드(DoR)&quot; 단추를 추가했습니다.
   * 규칙 내에 동적 변수에 대한 지원이 추가되었습니다.
   * 사용자 지정 이벤트를 기반으로 규칙 만들기를 활성화했습니다.
   * 이제 반복 가능한 패널에 대한 규칙이 마지막 패널 인스턴스가 아닌 올바른 컨텍스트에서 실행됩니다.
   * 이제 쿼리 매개 변수, UTM 매개 변수 및 브라우저 매개 변수를 기반으로 규칙을 트리거할 수 있습니다.
   * EDS(Experience Data Store)에서 양식별 사용자 정의 함수 스크립트에 대한 지원을 추가했습니다.
   * 규칙 편집기의 성공 처리기 내에서 &quot;다음으로 이동&quot; 작업의 `EVENT_PAYLOAD` 사용에 대한 지원을 추가했습니다.
   * 규칙 편집기의 입력 매개 변수 내에서 지원되는 함수 호출 및 필수 매개 변수가 함수 호출에서 누락된 경우 보장된 규칙이 저장되지 않습니다.
   * 규칙 편집기 UI에서 깨진 규칙을 강조 표시했습니다.
* FORMS-18450: 이제 적응형 Forms에서 reCAPTCHA V2(보이지 않는 reCAPTCHA 포함)를 보다 쉽게 설정하고 사용할 수 있습니다. 이제 구성이 한 곳에서 관리되므로 양식의 스팸 보호를 더 간편하게 활성화할 수 있습니다.
* FORMS-18385: 출력 서비스를 통해 AEM Forms의 XDP 및 데이터에서 AFP 생성에 대한 지원을 추가했습니다.
* FORMS-17789: 기록 문서(DoR)를 다운로드할 수 있는 규칙 편집기에 기본 제공 단추를 추가했습니다.
* FORMS-20313, FORMS-2896: 핵심 구성 요소 기반 양식의 특정 기능을 비활성화하기 위해 `dorExclude` 속성에 대한 지원을 추가했습니다.
* FORMS-20262: 클라이언트측에서 잘못된 첨부 파일(0바이트)을 처리했습니다.
* FORMS-18347: 누락된 양식 컨테이너 프록시 구성 요소에 대한 적응형 Forms 편집기 로깅이 개선되었습니다.
* FORMS-16205: 핵심 구성 요소 기반 양식의 기록 문서(DoR)에서 비활성화된 구성 요소를 제외했습니다.
* FORMS-10836: 오른쪽에서 왼쪽 쓰기 언어에 대해 기록 문서(DoR)에서 마스터 페이지 속성의 방향이 변경되었습니다.
* SITES-33025: 경로 대신 ID를 통해 새 CF 편집기를 엽니다.
* SITES-32741: 컨텐츠 조각 페이지 참조의 업데이트를 비동기적으로 트리거합니다.
* SITES-32087: GraphQL: StringArray에 `_ignoreCase`에 대한 지원을 추가하십시오.
* SITES-12211: 템플릿 편집기의 향상된 성능
* SITES-32861: 청크 처리를 통해 Live Copy 작성의 성능이 향상되었습니다.
* SITES-21383: 콘텐츠 조각 실행 삭제 작업에 대한 성능 최적화.
* SITES-31165: 롤아웃 작업을 관리 가능한 청크로 분할하여 성능을 개선합니다.
* SITES-21353: 데이터베이스 색인화를 사용하여 콘텐츠 조각 시작에 대한 쿼리 성능 개선을 수행합니다.
* SITES-30495: 콘텐츠 조각 실행에서 UUID 기반 조각 참조를 지원하도록 개선되었습니다.
* SITES-32151: 컨테이너 속성 기능을 노출하는 API 개선 사항.
* SITES-26849: 콘텐츠 조각 변형을 이동하거나 삭제할 때 역참조를 조정합니다.
* SITES-31846: 트리 복사 작업을 위해 루트 조각 및 참조를 동일한 폴더에 복사/붙여넣는 옵션을 추가합니다.
* SITES-30241: 조각을 이동, 이름 변경 또는 삭제할 때 긴 텍스트 필드 내에 있는 참조를 조정합니다.
* SITES-32684: UI 스키마의 탭 변경 내용을 동기화하기 위한 메커니즘을 개선합니다.
* SITES-33308: 모델을 편집할 때 UI 스키마에 대한 변경 내용을 동기화하기 위한 다시 시도 메커니즘을 추가합니다.
* SITES-32247: &quot;텍스트 및 Personalization&quot; 구성 요소에서 대화 상자 Personalization 및 UI 정렬이 누락되었습니다.
* SITES-32261: 경험 조각 i18n이 필드에 적용되지 않았습니다.
* SITES-32666: 템플릿 조건자에 `\n`이(가) 포함되어 있어 HTML 조회가 실패합니다.
* SITES-32674: `cq:showOnCreate`에도 불구하고 추천 이미지 필드 이미지 선택기가 페이지 만들기 마법사에서 작동하지 않습니다.
* SITES-32014: 범용 편집기가 있는 Edge Delivery: localhost, aem.page 및 aem.live에 대한 CORS 정책의 자동 구성을 추가합니다.
* SITES-26532: 범용 편집기가 있는 Edge Delivery: 현지화된 URL에 대한 지원을 추가합니다(조기 액세스).
* SITES-30887: 워크플로 메타데이터에 저장된 콘텐츠 조각 UUID를 추가합니다.

### 해결된 문제 {#fixed-issues-21772}

* CQ-4360190: 작업을 지원하지 않는 keySet에서 add를 사용하려고 할 때 발생하는 `UnsupportedOperationException`을(를) 수정했습니다.
* CQ-4360421: 보안 및 호환성을 개선하기 위해 Microsoft Translator 구독 키 암호화 문제를 해결했습니다.
* FORMS-20980: 적응형 Forms에서 사용자 지정 표시 형식을 사용하는 날짜 선택기의 키보드 접근성 문제가 수정되었습니다.
* FORMS-20498: 런타임 오류를 방지하기 위해 OdataResponse에 null 포인터 예외에 대한 검사를 추가했습니다.
* FORMS-20947: 화면 판독기 위반 및 텍스트 잘림/중복 문제를 비롯한 여러 접근성 문제가 해결되었습니다.
* FORMS-21030, FORMS-20630: 적응형 양식에서 여러 항목을 선택하도록 구성된 드롭다운 필드와 관련된 문제가 해결되었습니다. 이제 생성된 PDF에 선택한 모든 값이 올바르게 포함됩니다.
* FORMS-19579: 서비스 호출 규칙이 다시 저장 시 자동으로 수정되지 않던 문제를 수정했습니다.
* FORMS-20734: XFAF 기반 입력 PDF 템플릿에 대한 출력 서비스에서 생성한 PDF 문서의 서명 필드 중복을 수정했습니다.
* FORMS-20934: 중복 항목을 제거하고 모든 표준 HTML 자동 완성 토큰을 포함하도록 AEM Forms 작성 UI의 자동 채우기 속성 드롭다운을 수정했습니다.
* FORMS-20700: AEM Forms에서 초기 로드 시 드롭다운 도움말 텍스트가 깜박거리는 문제를 해결했습니다.
* FORMS-20307: 사이트 페이지에 임베드된 양식이 4자 로케일로 번역되지 않는 문제가 해결되었습니다.
* FORMS-20493: 데이터를 가져올 때 양식이 자동으로 새로 고쳐져 사용자가 불편을 겪는 문제를 해결했습니다.
* FORMS-18455: 데이터 소스 트리에 사용된 데이터 개체에 대한 점을 표시하도록 핵심 구성 요소에 대한 적응형 Forms 편집기가 개선되었습니다.
* FORMS-19373: 복제 에이전트가 구성되어 있지 않은 게시 환경에 대해 복제 오류가 발생하지 않았습니다.
* FORMS-20042: HTML 구성이 활성화된 Apache Sling GET 서블릿 구성으로 인해 손상된 속성 보기가 수정되었습니다.
* FORMS-20036, FORMS-19978: PDF/A-1b 규정 준수 및 유효성 검사 문제를 해결했습니다.
* FORMS-19166: 오류 스택 추적 명확성을 개선하고 더 많은 보호 기능 및 로깅을 추가하기 위해 pagedatasource.jsp를 서블릿으로 이동했습니다.
* FORMS-16466: AEM Forms에서 반복 가능한 패널이 올바르게 채워지지 않는 문제가 수정되었습니다.
* FORMS-19629: 잘못된 결과를 제공하는 고객 JSON 스키마 구문 분석 관련 문제가 해결되었습니다.
* LC-3923083: XDP 템플릿에서 테두리 항목에 대한 &quot;경로 개체가 태그 지정되지 않음&quot; 오류가 해결되었습니다.
* SITES-33177: 범용 편집기가 있는 Edge Delivery: 쉼표로 구분된 문자열로 저장될 때 끊어진 섹션 스타일을 수정합니다.
* SITES-33262: 범용 편집기가 있는 Edge Delivery: 이름 속성 없이 블록 수정 페이지 렌더링 및 게시.
* SITES-33309: 범용 편집기가 있는 Edge Delivery: 열에 슬래시가 있는 스프레드시트에 쓸 때 `IllegalArgumentException`을(를) 수정합니다.
* SITES-33408: 범용 편집기가 있는 Edge Delivery: 스프레드시트 수정 사항이 변경 후 수정된 것으로 표시되지 않습니다.
* SITES-31992: GraphQL: 번들 시작 중 모델 검사에서 발생하는 산발적으로 오류가 수정되었습니다.
* SITES-29967: GraphiQL: 긴 쿼리 이름이 잘립니다.
* SITES-26266: `/`(으)로 시작하지 않는 콘텐츠 참조가 BE 응답(Java API)에서 반환되지 않습니다.
* SITES-17874: GraphQL 지속 쿼리: 콘텐츠 유형 애플리케이션/graphql-response+json에 대한 인코딩을 수정합니다.
* SITES-24506: 화면 판독기에서 검색 결과에 대해 알려줍니다.
* SITES-25268: 주석에 대한 화면 판독기 개선 사항.
* SITES-32366: RTE 대화 상자 뒤에 숨겨진 맞춤법 검사 결과.
* SITES-32829: 미디어 쿼리 레벨 3 및 4를 구문 분석하는 MediaQuery 에뮬레이터가 개선되었습니다.
* SITES-32278: 필드 레이블을 올바르게 사용하도록 수정된 태그 필드입니다.
* SITES-25244: 가로 막대가 더 이상 이미지 모달에 표시되지 않습니다.
* SITES-33395: 콘텐츠 조각 라이브 카피 동기화를 위한 롤아웃 버튼 기능이 수정되었습니다.
* SITES-33147: 라이브 관계 기능에 영향을 주는 서비스 바인딩 문제가 수정되었습니다.
* SITES-33528: 론치 홍보 중 타임스탬프 보존 문제가 수정되었습니다.
* SITES-33014: LaunchesAdapterFactory에서 과도한 경고 로그 생성이 수정되었습니다.
* SITES-32305: 레이아웃 변경 후 라이브 카피 상속 중단 기능이 수정되었습니다.
* SITES-32268: 콘텐츠 조각 검색에 URL 인코딩을 사용하지 않습니다.
* SITES-32772: SITES-31455에서 태그 값 통합과 관련된 개선 사항을 활성화할 때 변형의 필드에 잠긴 속성이 항상 false였습니다.
* SITES-32696: 상속이 끊어진 콘텐츠 조각 라이브 카피 필드를 더 이상 편집할 수 없는 문제가 해결되었습니다.
* SITES-31712: 제품 작성자의 옴니 검색에서 느린 쿼리
* SITES-33039: 페이지 이벤트가 올바르게 트리거되지 않습니다.
* SITES-31192: 조각을 이동한 후 버전 기록이 손실되는 문제가 발생했습니다.
* SITES-33529: ACS 캠페인 템플릿을 AEM 페이지와 연결하는 동안 오류가 발생했습니다.
* SITES-33678: SITES-33529에 대한 토글을 추가합니다.
* SITES-33468: AEMaaCS에서 ACS에 연결할 수 없습니다.

### 변경된 기능 {#altered-functionality-21772}

* SITES-26344: 끝점 간 `fragmentId`/`modelId`의 유효성 검사를 통합합니다. 이제 이러한 ID가 유효하며 유효하지 않은 경우 400 상태 코드가 반환됩니다.
* SITES-29598: 콘텐츠 조각 모델을 업데이트할 때 조각 참조 필드에 추가된 콘텐츠 조각 참조의 유효성을 검사합니다.

### 알려진 문제 {#known-issues-21772}

* SITES-31791: 컨텐츠 조각 GraphQL - &quot;최대 필드 수 초과&quot;로 인해 쿼리가 실패했습니다. [기술 자료 문서](https://experienceleague.adobe.com/ko/docs/experience-cloud-kcs/kbarticles/ka-27231)를 참조하세요.

### 사용 중단된 기능 및 API {#deprecated-21772}

AEM as a Cloud Service에서 더 이상 사용되지 않는 기능과 API는 [사용 중단된 기능 및 API](/help/release-notes/deprecated-removed-features.md) 문서에 자세히 설명되어 있습니다.

### 보안 수정 {#security-21772}

AEM as a Cloud Service는 플랫폼의 보안 및 성능 최적화에 중점을 둡니다. 이 유지 관리 릴리스는 35개의 식별된 취약점을 해결하여 강력한 시스템 보호에 대한 노력을 강화합니다.


### 임베드된 기술 {#embedded-tech-21772}

| 기술 | 버전 | 링크 |
|---|---|---|
| AEM Oak | 1.80.0 | [Oak API 1.80.0 API](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.80/index.html) |
| AEM SLING API | 2.27.6 | [Apache Sling API 2.27.6 API](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 1.4.28-1.4.0 | [HTML 템플릿 언어 사양](https://github.com/adobe/htl-spec) |
| Apache HTTP 서버 | 2.4.63 | [Apache Httpd 2.4.63](https://github.com/apache/httpd/blob/2.4.63/CHANGES) |
| AEM 핵심 구성 요소 | 2.29.0 | [AEM WCM 핵심 구성 요소](https://github.com/adobe/aem-core-wcm-components) |
| Node.js | 14(기본값) | [지원되는 Node.js 버전](https://experienceleague.adobe.com/ko/docs/experience-manager-cloud-service/content/implementing/developing/developing-with-front-end-pipelines#node-versions) |

