---
title: ' [!DNL Adobe Experience Manager] as a Cloud Service의 현재 유지 관리 릴리스 정보입니다.'
description: ' [!DNL Adobe Experience Manager] as a Cloud Service의 현재 유지 관리 릴리스 정보입니다.'
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: 4b05f571904384521b79dbaf0fa5f4a3a75fef2b
workflow-type: tm+mt
source-wordcount: '1561'
ht-degree: 11%

---


# 유지 관리 릴리스 정보 {#maintenance-release-notes}

다음 섹션에서는 Experience Manager as a Cloud Service의 현재 유지 관리 릴리스에 대한 기술 릴리스 정보를 간략히 소개합니다.

## 릴리스 24678 {#release-24678}

다음은 2026년 3월 4일에 공개적으로 릴리스된 유지 보수 릴리스 24678에 대한 지속적인 개선 사항을 요약합니다. 이전 유지 관리 릴리스는 릴리스 24464.

이 유지 관리 릴리스에 대한 2026.3.0 기능 활성화는 전체 기능 세트를 제공합니다. 자세한 내용은 [Experience Manager 릴리스 로드맵](https://experienceleague.adobe.com/ko/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap)을 참조하십시오.

### 개선 사항 {#enhancements-24678}

* FORMS-18927: AEM Forms 파일 첨부 구성 요소에 사용자 지정 MIME 유형 및 파일 확장자에 대한 지원을 추가하여 사용자가 보다 다양한 문서 유형을 첨부할 수 있습니다.
* FORMS-18211, FORMS-22936: `<fieldset>` 요소 내에서 확인란이 올바르게 그룹화되지 않고 그룹 레이블이 `<legend>`에 첫 번째 하위 항목으로 중첩되지 않는 접근성 문제가 발생했습니다. 이로 인해 화면 판독기에 의존하여 탐색하는 장애가 있는 사용자가 영향을 받게 되었습니다. 적응형 Forms 기반의 핵심 구성 요소는 이제 더 나은 접근성 지원을 위해 필드 세트 및 범례 지원을 도입했습니다.
사용자가 양식 내에서 관련 필드를 보다 효과적으로 구성하고 그룹화할 수 있는 필드 세트 옵션이 패널에 추가되었습니다.
* FORMS-23880: 핵심 구성 요소에 테마 편집기 지원이 추가되었습니다. 이러한 향상된 기능을 통해 사용자는 핵심 구성 요소 내에서 테마를 보다 효율적으로 사용자 정의하고 관리할 수 있으므로 디자인 유연성과 워크플로가 향상됩니다.
* FORMS-21772: Forms Management UI에 버전 관리 지원이 추가되었습니다. 이 향상된 기능을 통해 사용자는 적응형 Forms, 양식 조각, 테마 및 바이너리 Assets을 기반으로 핵심 구성 요소 기반 및 기초 구성 요소 기반 버전을 모두 만들고 검색할 수 있으므로 에셋 관리 및 버전 제어를 향상시킬 수 있습니다.
* FORMS-23094: 기업 고객이 양식을 클라우드로 마이그레이션할 수 있도록 적응형 Forms 기반의 기초 구성 요소에 대한 클라이언트측 구문 분석이 추가되었습니다. 이 개선 사항은 이전에 지원되지 않았던 코드 편집기 규칙의 EcmaScript 기능을 지원하므로 더욱 원활한 마이그레이션 프로세스를 용이하게 합니다.
* FORMS-23853: sling 구성 요소에서 reCAPTCHA 재정의에 대한 지원을 추가했습니다. 이 향상된 기능을 통해 사용자는 reCAPTCHA 설정을 사용자 정의하여 기업 고객을 위한 유연성과 보안을 향상시킬 수 있습니다.
* SITES-34936: 범용 편집기가 있는 Edge Delivery: 게시할 모델별로 필터링 콘텐츠 조각을 추가합니다.
* SITES-36203: 범용 편집기가 있는 Edge Delivery: 다중 필드 및 복합 다중 필드 지원을 활성화하기 위한 코드 토글을 추가합니다.
* SITES-37037: 범용 편집기가 있는 Edge Delivery: 구분 기호를 자동으로 검색하도록 스프레드시트 가져오기를 개선합니다.
* SITES-37804: 범용 편집기가 있는 Edge Delivery: 폐쇄형 사용자 그룹 작성(조기 액세스)에 대한 지원을 추가합니다.
* SITES-38990: 범용 편집기가 있는 Edge Delivery: 경로 매핑에 제외에 대한 지원을 추가합니다.
* SITES-39171: 범용 편집기가 있는 Edge Delivery: 블록 및 블록 항목에서 `cq:tags`에 대한 지원을 추가하십시오.
* SITES-40042: 범용 편집기가 있는 Edge Delivery: 구성 서비스를 새 사이트의 기본값으로 설정합니다.
* SITES-37649: GraphQL: JCR 수준에서 여러 줄 텍스트 필드 필터링을 지원합니다.
* SITES-37843: GraphQL: 다중 값 필드(컬렉션)에 대한 필터링은 JCR 수준에서 지원되지 않습니다.
* SITES-37540: CF 필드 값에 대한 바꾸기 및 바꾸기모두 작업(주어진 필드 이름에 대한 찾기 및 바꾸기).
* SITES-37741: 조각 변형 가져오기 응답에서 &quot;card&quot; 속성을 추가합니다(관리 UI의 카드 보기).
* SITES-37754: `validateReferences`이(가) true로 설정된 경우 API를 통해 폴더 게시: 요청 시 트리 유효성 검사.
* SITES-37756: 컨텐츠 조각에 대한 체크인/체크아웃 상태 정보를 표시합니다.
* SITES-37805: 스키마 업데이트: 수정된 조각의 이름을 변경/이동할 수 없습니다(설명서).
* SITES-37847: 빌려 온 Content ReferenceProvider SQL-2 쿼리(LentContent 검색)의 성능이 개선되었습니다.
* SITES-39255: 합성 필드에 대한 최근 Java API 변경 사항으로 OpenAPI 구현을 업데이트합니다.
* SITES-37096: 고립된 노드가 있을 때 론치 콘솔 속도가 느려집니다.
* SITES-38117: 성능에 영향을 주지 않고 하위 시작을 쿼리하는 방법을 찾습니다.
* SITES-38317: 메타데이터에 워크플로를 시작한 사용자를 추가합니다(서비스 사용자가 실행하는 경우 일반 대신 실제 사용자).
* SITES-39203: 서비스 사용자가 실행할 때 일반 사용자 대신 워크플로우를 시작한 사용자를 표시합니다.
* SITES-13083: 사이트 > 라이브 카피 만들기 대화 상자에서 오류 문자열을 로컬라이즈합니다.
* SITES-13389: 사이트 > 타임라인에서 &quot;론치를 홍보하기 전에 ...의 생성된 버전&quot; 문자열을 현지화합니다.
* SITES-16176: 페이지 편집기 > 이미지 v3 구성 요소 구성 대화 상자에서 문자열을 현지화합니다.
* SITES-35702: &quot;Live Copy 개요&quot; 탭의 현지화되지 않은 &quot;Live Copy 최신 유산과 함께&quot; 문자열.
* SITES-35748: &#39;콘텐츠 조각 모델 편집기&#39;에서 현지화되지 않은 &quot;제품 변형 선택 활성화&quot; 확인란 레이블.
* SITES-35750: &quot;콘텐츠 조각 모델 편집기&quot;의 입력 필드에 현지화되지 않은 &quot;제품 SKU(s) 구분 문자 `#`&quot; 자리 표시자가 있습니다.
* SITES-37113: &quot;CIF 구성&quot; 탭에서 현지화되지 않은 &quot;상속 취소&quot; 대화 상자입니다.
* SITES-25240: 티저 모달 call to action에 대한 접근성 수정.
* SITES-25531: 검색 모달에서 색상 대비를 위한 접근성 수정.
* SITES-37115: Vienia 데모 스토어의 잘린 아이콘

### 해결된 문제 {#fixed-issues-24678}

* CQ-4361552: 가져오기 번역에서 HTML 이스케이프 유니코드를 유지하는 i18n JSON 사전이 수정되었습니다.
* CQ-4361634: 고정 경험 조각을 선택하거나 번역 프로젝트에 추가할 수 없습니다.
* CQ-4362072: 고정 AEMaaCS 번역 워크플로 - DE > ES 단계에서 번역 프로젝트에 페이지를 추가하지 못했습니다.
* FORMS-23741: 사용자에게 InvokeDDX 및 자산 업로드 단계가 캐스케이드로 실행되지 않아 두 개의 개별 워크플로우 실행이 필요한 문제가 발생했습니다. 이는 AEM as a Cloud Service과 Sites 및 Forms 추가 기능을 사용하는 프로덕션 환경에 영향을 주었습니다.
* FORMS-23877: 이전 핵심 구성 요소 버전을 사용하여 Sites 페이지 내에서 직접 양식을 작성할 때 런타임 시 사용자 정의 함수가 로드되지 않는 문제가 사용자에게 발생했습니다.
* FORMS-24038: 더 많은 탭이 동적으로 추가될 때 사용자에게 탐색 버튼에 대한 문제가 발생했습니다.
* FORMS-23721: 편집 대화 상자에서 텍스트 입력에 대해 구성된 유효성 검사 패턴이 지속되지 않는 문제를 해결했습니다. 이전에는 패턴 값이 저장되었지만 UI에 유지되거나 표시되지 않아서 양식 작성자에게 혼동이 발생했습니다.
* FORMS-23456: 적응형 Forms에서 테이블 구성 요소를 사용할 때 테이블의 숨겨진 헤더 행에 대해 모바일 장치의 화면 판독기에서 잘못 공지했습니다. 숨겨진 테이블 헤더가 컨텍스트에서 벗어나 발표되어 iOS VoiceOver 및 Android TalkBack에 의존하는 사용자에게 혼란을 주었습니다.
* FORMS-23454: 적응형 Forms 기반의 핵심 구성 요소에 대한 날짜 선택기 문제가 발생했습니다. 유효하지 않은 일자를 입력하면 시스템은 마감된 가능한 일자를 자동으로 수정합니다.
* FORMS-23117: 사용자가 적응형 Forms 기반의 기초 구성 요소에서 hCaptcha가 올바르게 번역되지 않았습니다.
* FORMS-22634: &quot;첨부 파일 포함&quot; 옵션과 &quot;HTML 템플릿 사용&quot; 옵션을 함께 사용할 때 이메일 첨부 파일이 포함되지 않는 문제가 발생했습니다.
* FORMS-23288: 사용자가 Asset Share Commons 모달에 포함된 적응형 Forms에 문제가 발생했습니다. URL에 중간 경로에 `.html`이(가) 포함되어 있는 경우 양식을 제대로 로드하지 못했습니다.
* FORMS-19198: Dispatcher 규칙을 사용하여 양식을 포함할 때 사용자에게 404 오류가 발생했습니다. URL 재작성기가 이러한 URL을 다시 작성할 수 없기 때문에 /etc.clientlibs/toggles.json, rum 라이브러리 및 analyticsparserconfigparser.json과 같은 URL에 대해 오류가 발생했습니다.
* SITES-33799: 유니버설 편집기가 있는 Edge Delivery: 최적화된 비디오 렌디션이 게시되지 않았습니다.
* SITES-35082: 범용 편집기가 있는 Edge Delivery: 리치 텍스트에서 빈 단락, 선행 및 후행 줄 바꿈을 제거합니다.
* SITES-35524: 범용 편집기가 있는 Edge Delivery: ASCII 이외 특수 문자가 포함된 경로에 대한 게시 오류를 수정합니다.
* SITES-38647: 범용 편집기가 있는 Edge Delivery: 사이트가 많은 환경에서 성능 병목 현상을 수정합니다.
* SITES-40521: 범용 편집기가 있는 Edge Delivery: 블록 및 블록 항목에 대한 중복 클래스 이름을 수정합니다.
* SITES-37887: GraphQL: 더 큰 결과 세트에 대한 UUID 조회로 인해 응답 시간이 늘어날 수 있습니다.
* SITES-38412: 고유 필드/슬러그가 있는 경우 론치의 조각을 패치할 수 없습니다(고유 제한 사항은 이제 론치의 CF를 제외함).
* SITES-38606: 조각 참조 UUID(변형에서 uuid에 의해 참조되는 하이드레이트 CF)를 사용하여 CF에 변형을 추가할 때 유효성 검사 오류가 발생합니다.
* SITES-39489: cq:discarded 폴더의 조각을 표시하는 Assets UI(소프트 삭제된 CF는 관리 API 응답에서 제거됨).
* SITES-39517: 열거형이 포함된 복합 필드가 있는 GET CF가 500 오류로 실패합니다.
* SITES-40072: 탭이 있는 복합 필드는 빈 자리 표시자 값을 반환합니다.
* SITES-39575: Live Copy 저장 시 `cq:rolloutConfigs` - 롤아웃 구성이 손실됩니다.
* SITES-39694: NPE로 인해 프로덕션 롤아웃이 실패했습니다.
* SITES-39761: NavigationItem.getLink()가 CIF v2 탐색 구성 요소에서 null을 반환합니다.
* SITES-40519: 라이브 카피 대상 리소스가 null인 경우 NullPointerException으로 MSM 롤아웃이 실패합니다.
* SITES-17531: 페이지 편집기 > 이미지 > 스마트 자르기에서 하드코딩된 &quot;스마트 자르기 미리 보기&quot; 문자열입니다.
* SITES-31575: 정보 툴팁이 페이지 편집기 > 슬라이드 구성 요소 > 속성에 완전히 표시되지 않습니다.
* SITES-34215: 자동 완성 JS 구성 요소는 대화 상자 탭의 필수 경로 필드에 즉각적인 유효성 검사 오류를 발생시킵니다.
* SITES-35218: 일부 AEM 핵심 구성 요소는 빈 대체 태그를 제대로 렌더링하지 않습니다.
* SITES-37114: &quot;CIF 구성&quot; 탭에서 &quot;카탈로그 UID 지원 사용&quot; 툴팁이 잘렸습니다.
* SITES-36138: 색인이 없는 쿼리가 감지되었습니다(문제).
* SITES-37682: `/libs/cq/Page/Page.css.jsp` 및 `/libs/cq/Page/Page.js.jsp.`에서 콘텐츠 형식 재정의
* SITES-38709: 6.5.24로 업그레이드한 후 클래식 UI 텍스트 RTE에 원시 HTML이 표시됩니다.
* SITES-39630: 중첩된 콘텐츠 조각 업데이트가 내보낸 Target 오퍼에 반영되지 않습니다.
* SITES-39696: 활성화/비활성화 일정 잡기에 대한 설정/해제 시간이 작동하지 않습니다.
* SITES-39824: 경험 조각을 Adobe Target으로 내보내면 500(NPE)이 반환됩니다.
* SITES-40253: `/bin/cif/invalidate-cache`에서 간헐적인 500 오류 - `/var/cif/cacheinvalidation`에서 Oak 충돌.
* SITES-40341: `HtmlToJsonConvertorImpl`의 스타일 태그에서 base64 인라인 이미지를 수정합니다.

### 알려진 문제 {#known-issues-24678}

없음.

### 사용 중단된 기능 및 API {#deprecated-24678}

AEM as a Cloud Service에서 더 이상 사용되지 않는 기능과 API는 [사용 중단된 기능 및 API](/help/release-notes/deprecated-removed-features.md) 문서에 자세히 설명되어 있습니다.

### 보안 수정 {#security-24678}

AEM as a Cloud Service는 플랫폼의 보안 및 성능 최적화에 중점을 둡니다. 이 유지 관리 릴리스는 15개의 식별된 취약점을 해결하여 강력한 시스템 보호에 대한 노력을 강화합니다.

### 임베드된 기술 {#embedded-tech-24678}

| 기술 | 버전 | 링크 |
|---|---|---|
| AEM Oak | 1.90.0 | [Oak 1.90.0 API](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.90.0/index.html) |
| AEM SLING API | 2.27.6 | [Apache Sling API 2.27.6 API](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 1.4.28-1.4.0 | [HTML 템플릿 언어 사양](https://github.com/adobe/htl-spec) |
| Apache HTTP 서버 | 2.4.65 | [Apache Httpd 2.4.65](https://apache.googlesource.com/httpd/+/refs/tags/2.4.65/CHANGES) |
| AEM 핵심 구성 요소 | 2.30.4 | [AEM WCM 핵심 구성 요소](https://github.com/adobe/aem-core-wcm-components) |
| Node.js | 14 (기본값) | [지원되는 Node.js 버전](https://experienceleague.adobe.com/ko/docs/experience-manager-cloud-service/content/implementing/developing/developing-with-front-end-pipelines#node-versions) |

