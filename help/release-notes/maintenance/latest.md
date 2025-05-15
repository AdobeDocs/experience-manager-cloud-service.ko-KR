---
title: ' [!DNL Adobe Experience Manager] as a Cloud Service의 현재 유지 관리 릴리스 정보입니다.'
description: ' [!DNL Adobe Experience Manager] as a Cloud Service의 현재 유지 관리 릴리스 정보입니다.'
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: 088d470333d8f5a26f1a938380028541a1e945a1
workflow-type: tm+mt
source-wordcount: '1750'
ht-degree: 10%

---


# 유지 관리 릴리스 정보 {#maintenance-release-notes}

다음 섹션에서는 Experience Manager as a Cloud Service의 현재 유지 관리 릴리스에 대한 기술 릴리스 정보를 간략히 소개합니다.

## 릴리스 20783 {#20783}

2025년 5월 13일에 공개적으로 릴리스된 유지 보수 릴리스 20783에 대한 지속적인 개선 사항을 요약하면 다음과 같습니다. 이전 유지 관리 릴리스는 릴리스 20626.

이 유지 관리 릴리스(2025.5.0)에 대한 기능 활성화는 전체 기능 세트를 제공합니다. 자세한 내용은 [Experience Manager 릴리스 로드맵](https://experienceleague.adobe.com/ko/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap)을 참조하십시오.

### 개선 사항 {#enhancements-20783}

* FORMS-18455: AEM Forms 핵심 구성 요소의 적응형 양식 편집기는 작성자가 활용된 데이터 요소를 쉽게 식별할 수 있는 기능인 데이터 소스 트리 내에서 양식에 이미 사용되거나 매핑된 데이터 개체에 대한 시각적 표시기(점)를 표시하도록 개선되었습니다.
* FORMS-18450: reCaptcha V2 도메인 논리를 `AdaptiveFormConfigurationServiceImpl`(으)로 마이그레이션하여 제품이 향상되었습니다. 이 변경 사항은 구성을 중앙 집중화하는 것을 목표로 하며 핵심 구성 요소에 보이지 않는 reCaptcha V2에 대한 지원을 추가하는 것과 맞출 수 있습니다.
* FORMS-19630: AEM 6.5 quickstart uber-jar가 최신 적응형 Forms 핵심 구성 요소 패키지를 포함하도록 업데이트되어 quickstart 환경이 가장 최신 적응형 Forms 기능을 반영하고 레거시 코드를 대체합니다.
* FORMS-19125: 데이터 소스 트리의 해당 섹션을 양식 캔버스로 끌어 놓을 때 사용 가능한 적응형 양식 조각의 자동 매핑을 지원하도록 핵심 구성 요소 적응형 양식 편집기가 개선되었습니다. 이 기능은 기초 편집기에서 핵심 구성 요소로 주요 생산성 기능을 제공합니다.
* FORMS-17887: 이제 AEM Forms은 출력 서비스를 통해 AFP(Advanced Function Presentation) 포맷으로 문서를 생성하는 기능을 제공합니다. 이 향상된 기능은 일반적으로 AFP를 사용하는 고속 대량 인쇄 환경에 대한 고객의 요구에 부응합니다.
* FORMS-15089: AEM Forms은 게시할 때 양식의 모든 구성 조각이 게시된 특정 버전에 인라인(임베드)되는 방식으로 양식 버전을 관리하는 기능을 도입했습니다. 이를 통해 게시 시점에 표시된 양식을 정확하게 자체적으로 표현할 수 있으며, 이는 보관, 법률 또는 규정 준수를 위해 매우 중요할 수 있습니다.
* FORMS-17107: 이제 AEM Forms에서 향상된 클라이언트측 사용자 지정 함수 구문 분석을 제공합니다. 여기에는 선택적 체인과 같은 최신 JavaScript 기능(ECMAScript ES10+)에 대한 지원이 포함되며 사용자 지정 함수 스크립트 내에서 정적 가져오기를 사용하는 기능이 도입되었습니다. 이를 통해 개발자는 코드를 보다 효율적으로 구성하고, ESM 모듈을 활용하고, 특히 이전에 이러한 기능에 대한 해결 방법이 필요했던 사용자를 위해 적응형 Forms v2 및 Edge Delivery Services에서 사용자 정의 기능과 관련하여 발생한 이전 제한 사항을 제거할 수 있습니다.
* SITES-27775: 게시하는 동안 최적화된 참조 검색입니다.
* SITES-30885: 지속 쿼리에서 JSON 처리가 최적화되었습니다.
* SITES-25433: 범용 편집기가 있는 Edge Delivery: 이전 버전을 비교할 때 전체 페이지 렌더링을 지원합니다.
* SITES-27792: 범용 편집기가 있는 Edge Delivery: Edge Delivery 서비스 구성에 대한 특정 템플릿을 추가합니다.
* SITES-19754: 범용 편집기가 있는 Edge Delivery: 설정이 중단되었을 때 강력한 오류 메시지가 표시됩니다.
* SITES-30328: 범용 편집기가 있는 Edge Delivery: Sidekick 지원에서 미리 보기.
* SITES-23499: 범용 편집기가 있는 Edge Delivery: 블록 옵션에 여러 필드를 사용할 수 있습니다.
* SITES-29987: 콘텐츠 조각 모델을 만들 때 `previewUrlPattern`을(를) 설정하는 기능을 추가합니다.
* SITES-29874: 콘텐츠 조각 API에 LongTextField 참조에 대한 지원을 추가합니다.
* SITES-29601: LongText 필드를 통해 참조된 콘텐츠 조각에 대한 유효성 검사를 추가합니다.
* SITES-24623: GET 및 검색 조각 API에서 반환한 ETag를 패치에 사용할 수 있도록 합니다.
* SITES-28557: PATCH 콘텐츠 조각에서 URL 매개 변수 `references`을(를) 허용합니다.
* SITES-5358: [OpenAPI] 하위 항목이 있는 콘텐츠 조각 복사.
* SITES-29614: GET 워크플로 엔드포인트.
* SITES-29615: 일괄 처리 요청 API 엔드포인트를 나열합니다.
* SITES-25130: 핵심 구성 요소를 2.28.0으로 업그레이드
* SITES-10575: &quot;MSM 블루프린트 블룸필터 로더&quot;가 100,000개 이상의 행을 로드하려고 합니다.
* SITES-26711: RTE 텍스트 필드에 대한 링크는 MSM 롤아웃 시 라이브 카피를 가리키도록 업데이트되지 않습니다.
* SITES-25976: 경험 조각 내의 링크가 MSM 롤아웃 후에 조정되지 않습니다.

### 해결된 문제 {#fixed-issues-20783}

* ASSETS-50994: AemRequestEventFilter에서 차단된 수신 트래픽.
* CQ-4358591: &quot;번역 프로젝트 만들기&quot; 옵션을 사용하여 사이트 참조 패널에서 언어 사본을 만들 때 일부 언어에 대한 프로젝트가 누락되었습니다.
* CQ-4359108: 사람 번역 가져오기/내보내기를 사용하는 동안 XLIFF 2.0 형식이 실패했습니다.
* CQ-4358722: Java 11 및 Java 17의 서로 다른 로케일 코드로 인해 이전 ISO 코드에 대해 현지화가 작동하지 않습니다.
* FORMS-19808: 소극적 로드로 활성화된 조각이 포함된 큰 양식을 저장할 때 사용자가 초안을 가져올 수 없습니다.
* FORMS-19887: 처음에 읽기 전용 액세스로 설정된 XFA 양식의 드롭다운 필드는 양식이 HTML5에서 렌더링될 때 열기/편집 가능 상태로 변경되지 않습니다. 필드는 읽기 전용으로 유지되며 예상대로 작동하는 PDF 렌더링과 달리 사용자 상호 작용을 방지합니다.
* FORMS-19651: 규칙 편집기에서 버튼 클릭이 이진 조건에 사용되고 동일한 버튼이 해당 규칙의 &#39;then&#39; 문에도 사용되는 경우 규칙이 올바르게 작동하지 않습니다.
* FORMS-19628: 핵심 구성 요소 기반 적응형 Forms을 위해 자동 생성된 기록 문서(DoR)에서, 루트 패널에 &#39;제목에 대해 리치 텍스트 허용&#39; 옵션이 활성화된 경우 DoR에서 중첩된 패널의 제목을 제외하고 루트 패널의 제목도 잘못 숨깁니다.
* FORMS-18977: DoR(Document of Record) 서비스로 생성된 PDF에 문서 제목이 없습니다. 문서 제목은 액세스 가능한 PDF에 대한 필수 속성이므로 이로 인해 PDF/UA 및 WCAG 2.1 액세스 가능성 표준을 준수하지 않을 수 있습니다.
* FORMS-18526: 해당 조건에 여러 필드가 포함된 규칙을 한 필드에서 다른 필드로 복사할 때 이러한 조건 내의 고정 필드 참조는 규칙이 복사된 새 필드로 업데이트하는 대신 원래 소스 필드에 대한 참조를 잘못 유지합니다.
* FORMS-19047: 적응형 양식이 수정되어 AEM Forms에 다시 게시된 후(특히 6.5.22.0) 특정 양식 요소, 특히 텍스트 상자에 대한 번역이 누락될 수 있습니다.
* FORMS-19234: PDF의 작성 및 버전 관리에 대한 세부 정보를 볼 수 있는 AEM Forms의 PDF용 타임라인 기능은 PDF이 &#39;Forms 및 문서&#39; 섹션 아래에 업로드된 후 작동을 중지합니다.
* FORMS-19373: 복제 에이전트가 구성되지 않은 환경에서 &#39;골든 게시&#39; 프로세스 중에 복제 오류가 잘못 보고됩니다.
* FORMS-18196: XDP 템플릿에 필요한 선택적 필드 데이터가 요청에 비어 있는 경우 `generatePrintedOutput`(또는 `generatePdfOutput`) 동기화 HTTP API가 예상 400(잘못된 요청) 오류 코드 대신 200(성공) 응답 코드를 잘못 반환합니다.
* FORMS-19336: 핵심 구성 요소 적응형 양식 편집기(AF2 편집기)에서 데이터 Source 트리 내의 검색 기능이 제대로 또는 예상대로 작동하지 않아 사용자가 특정 데이터 요소를 쉽게 찾을 수 없습니다.
* FORMS-19629: JSON 스키마 파서가 잘못된 결과를 생성하거나 고객이 제공한 특정 JSON 스키마를 잘못 해석하고 있습니다. 이 문제는 조각의 자동 매핑과 같이 올바른 스키마 구문 분석에 의존하는 기능에 부정적인 영향을 줄 수 있습니다.
* FORMS-19380: 핵심 구성 요소에 대한 버전 관리 지원을 도입하면 적응형 Forms은 자산 유형에 대한 특정 디자인이나 테스트 없이 다양한 다른 자산 유형(예: Foundation Forms, PDF 파일, 테마, FDM)에 대한 버전 관리 기능을 의도하지 않게 활성화합니다. 이 의도하지 않은 부작용은 조사 중이다.
* FORMS-17707: AEP(Adobe Experience Platform) 커넥터가 AEP 플랫폼 &#39;단계&#39; 환경에 연결하도록 구성된 경우 제대로 작동하지 않습니다.
FORMS-18526: 여러 필드를 기반으로 하는 조건이 있는 규칙을 복사할 때 규칙의 조건 또는 작업 내에서 참조된 필드(규칙을 트리거하는 기본 필드가 아님)가 업데이트되지 않고 규칙이 복사되는 새 필드를 올바르게 참조하게 됩니다. 대신 규칙이 복사된 원본 소스 필드를 계속 참조합니다.
FORMS-18474: 특정 필드의 값이 변경될 때(예: 필드 &#39;A&#39;) 특정 패널 또는 구성 요소에 포커스를 설정하도록 디자인된 규칙이 양식의 모든 필드 변경으로 인해 잘못 트리거됩니다. 예를 들어 필드 &#39;B&#39;가 수정되면 필드 &#39;A&#39;의 변경에 대해서만 규칙이 구성되었더라도 포커스는 여전히 지정된 패널로 설정됩니다.
* GRANITE-58276: OSGi 종속성 사이클로 인해 HTL 스크립트 엔진 팩토리가 제대로 작동하지 않습니다.
* OAK-11673: refreshLease로 인한 Oak-segment-azure v12 CPU 증가.
* SITES-30752: 지속 쿼리 응답을 생성할 때 `If-modified-since`/`last-modified` 헤더를 사용하지 마십시오.
* SITES-30353: AEM 컨텐츠 조각의 &quot;src&quot; 필드에 대한 GraphQL DataFetchExceptions입니다.
* SITES-30333: xmp 구문 분석 문제를 방지하기 위해 jcr에서 자산 메타데이터를 읽습니다.
* SITES-30140: 콘텐츠 조각 참조를 생성할 때 이중 창 문제가 발생합니다.
* SITES-29748: CF 편집기 내에서 관리 게시/빠른 게시 작업을 표시하도록 renderconditions를 수정했습니다.
* SITES-15452: 론치에서 고유 CF 요소를 사본에 대해 확인하지 않아야 합니다.
* SITES-30386: 범용 편집기가 있는 Edge Delivery: UE cors.js가 중복되면 컨텐츠를 추가할 때 UE에서 섹션을 복제합니다.
* SITES-29745: 참조의 변형이 하이드레이션되지 않은 드문 문제를 해결했습니다.
* SITES-30585: 참조가 있는 모델을 만들 때 &#39;previewUrlPattern&#39;을 설정할 수 없습니다.
* SITES-30327: 권한 없이 콘텐츠 조각을 게시하면 각 페이로드 리소스에 대해 별도의 워크플로우가 만들어집니다.
* SITES-29528: 게시 인스턴스의 캐싱에 ETag를 사용할 수 없습니다.
* SITES-30583: 찾기 및 바꾸기 도구가 모든 문자를 소문자로 바꿉니다.
* SITES-31157: 일관되지 않은 ETag로 인해 패치가 실패합니다.
* SITES-31327: [OpenAPI] 작성자 인스턴스의 콘텐츠 조각 가져오기 요청은 304로 응답할 수 있습니다.
* SITES-29691: 페이지를 이동하려고 할 때 NullPointerException이 발생합니다.
* SITES-30728: 에셋 속성에 구성할 때 OnTime/OffTime이 예상대로 게시/게시 취소되지 않습니다.
* SITES-29789: AEM에서 복사된 루트 페이지의 구성 요소 링크 변경.
* SITES-29191: 제품 목록 구성 요소에 20개 이상의 SKU를 추가할 수 없습니다.
* SITES-30372: AEM의 이미지(V2) 핵심 구성 요소에서 스마트 자르기가 작동하지 않습니다.
* SITES-28693: 티저 구성 요소는 제목이 비어 있을 때 끊어진 HTML을 렌더링합니다.
* SITES-28668: LaunchPromotionParameters로 출시를 홍보할 수 없습니다.
* SITES-31005: 고객에게 진행 상황을 표시하도록 롤아웃 작업 UI를 개선합니다.
* SITES-31020: 진행 상황을 고객에게 보여 주기 위해 라이브 카피 만들기 작업 UI를 개선합니다.
* SITES-29816: 경험 조각의 라이브 카피를 만드는 동안 &quot;리소스를 찾을 수 없음&quot; 오류가 발생했습니다.
* SITES-29363: 중첩된 라이브 복사 콘텐츠 계층 구조에서 라이브 복사 재설정 버튼이 작동하지 않습니다.
* SKYOPS-106509: Java 21에서 GSON 반사 액세스를 지원하기 위해 보조 추가 열기 플래그를 추가합니다.

### 알려진 문제 {#known-issues-20783}

없음.

### 사용 중단된 기능 및 API {#deprecated-20783}

AEM as a Cloud Service에서 더 이상 사용되지 않는 기능과 API는 [사용 중단된 기능 및 API](/help/release-notes/deprecated-removed-features.md) 문서에 자세히 설명되어 있습니다.

### 보안 수정 {#security-20783}

AEM as a Cloud Service는 플랫폼의 보안 및 성능 최적화에 중점을 둡니다. 이 유지 관리 릴리스는 19개의 식별된 취약점을 해결하여 강력한 시스템 보호에 대한 노력을 강화합니다.

### 임베드된 기술 {#embedded-tech-20783}

| 기술 | 버전 | 링크 |
|---|---|---|
| AEM Oak | 1.78.1-T20250429061757 | [Oak API 1.78.0 API](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.78.0/index.html) |
| AEM SLING API | 2.27.6 | [Apache Sling API 2.27.6 API](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 1.4.26-1.4.0 | [HTML 템플릿 언어 사양](https://github.com/adobe/htl-spec) |
| AEM 핵심 구성 요소 | 2.29.0 | [AEM WCM 핵심 구성 요소](https://github.com/adobe/aem-core-wcm-components) |
