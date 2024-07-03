---
title: ' [!DNL Adobe Experience Manager] as a Cloud Service의 현재 유지 관리 릴리스 정보입니다.'
description: ' [!DNL Adobe Experience Manager] as a Cloud Service의 현재 유지 관리 릴리스 정보입니다.'
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: 9303ecadea38d83bd71ed0d440067bae5c419940
workflow-type: tm+mt
source-wordcount: '944'
ht-degree: 17%

---

# 유지 관리 릴리스 정보 {#maintenance-release-notes}

다음 섹션에서는 Experience Manager as a Cloud Service 현재 유지 관리 릴리스의 기술 릴리스 정보에 대해 간략히 소개합니다.

## 릴리스 16971 {#release-16971}

다음은 2024년 7월 3일에 공개적으로 릴리스된 유지 보수 릴리스 16971에 대한 지속적인 개선 사항을 요약했습니다. 이전 유지 관리 릴리스는 릴리스 16799.

2024.7.0 기능 활성화는 이 유지 관리 릴리스에 대한 전체 기능 세트를 제공합니다. 자세한 내용은 [Experience Manager 릴리스 로드맵](https://experienceleague.adobe.com/ko/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap)을 참조하십시오.

### 개선 사항 {#enhancements-16971}

* SITES-22948: AEM CS용 Foundation 콘텐츠에서 상거래 참조를 제거합니다.
* SITES-22141 [컨텐츠 조각] OnRC 이후 CFM ModelChangeRepositoryImpl에서 SegmentNotFoundException이 발생했습니다.
* SITES-21893: 작성자 인스턴스의 이미지 자르기 문제
* SITES-21788 [컨텐츠 조각] 모델에 대해 uiSchema가 활성화되면 CF 및 CF 모델 편집기에 참고 사항을 표시합니다.
* SITES-21688: MSM 롤아웃은 라이브 카피 페이지의 XF(경험 조각) 경로를 업데이트하지 않습니다.
* SITES-21659: 모델 리소스를 생성/수정/복제하는 사용자의 전체 이름을 반환합니다.
* SITES-21609: 콘텐츠 조각을 한 모델에서 다른 모델로 마이그레이션하기 위한 OpenAPI 엔드포인트.
* SITES-21598 [API 열기] CFM 만들기 - 지정된 구성 경로가 존재하지 않는 경우 오류를 반환합니다.
* SITES-21491 [API 열기] CF PATCH 끝점은 필드 수준에서 라이브 관계를 준수해야 합니다.
* SITES-21434 [API 열기] CF GET 끝점은 필드 수준에서 라이브 관계를 준수해야 합니다.
* SITES-21415: CF 편집기 - UUID 참조를 지원합니다.
* SITES-21326 [API 열기] 콘텐츠 조각에 대한 참조 존재에 대한 정보를 제공합니다.
* SITES-21310 [API 열기] 번역 API 응답에 콘텐츠 조각의 ID를 추가합니다.
* SITES-20859: CF Open API - 경로로 조각을 검색할 때 참조를 반환합니다.
* SITES-20687 [API 열기] 일괄 처리 상태 검색을 위한 끝점입니다.
* SITES-20657 [API 열기] 문자열을 바꿀 때 match 단어 전체에 옵션을 제공합니다. `FindAndReplace` 엔드포인트.
* SITES-20587 [API 열기] 만들기 `COPY` 콘텐츠 조각의 종단점입니다.
* SITES-20584 [API 열기] 참조 검색을 최적화합니다.
* SITES-20308 [API 열기] API에 대한 일괄 처리를 활성화합니다.
* SITES-19976 [API 열기] 조건부 필드에 대한 일반 UI 스키마.
* SITES-19556 [컨텐츠 조각] 모델을 편집할 때 uiSchema가 존재하는 경우 업데이트합니다.
* SITES-18056 [API 열기] 콘텐츠 조각을 미리보기에 게시할 때 참조를 포함합니다.
* SITES-16898 [스키마] 콘텐츠 조각을 한 모델에서 다른 모델로 마이그레이션하기 위한 OpenAPI 엔드포인트.
* SITES-16609: 목록 실행 끝점입니다.
* SITES-16606: Launch 끝점을 만듭니다.
* SITES-21617 [Xwalk] 페이지 속성/메타데이터를 UE 내에서 편집할 수 있게 만듭니다.
* SITES-19614 [Xwalk] 스프레드시트 편집기 페이지 매김 및 무한 스크롤입니다.
* SITES-22163 [Xwalk] Edge Delivery Sites의 게시 계층에서 제공되는 콘텐츠에 대한 지원이 개선되었습니다.
* SITES-22109 [Xwalk] 리치 텍스트 마크업 사후 처리 처리가 개선되었습니다.
* SITES-22035 [Xwalk] MSM 및 론치 처리가 개선되었습니다.
* SITES-21839 [Xwalk] Edge Delivery에서 제공하지 않는 콘텐츠에 대한 경로 매핑 및 정리 기능이 개선되었습니다.

### 해결된 문제 {#fixed-issues-16971}

* CQ-4356898: [번역] 링크가 비정상적으로 많이 포함된 CF에 대한 outOfMemory 오류입니다.
* CQ-4357055: [번역] Rest API를 사용하여 자동 번역이 작동하지 않습니다.
* CQ-4353931: [번역] 누락되면 번역 소스 페이지/xf/asset에 jcr:uuid를 추가합니다.
* CQ-4357591: [번역] Pages/XF에 대해 작동하도록 &quot;JCR:UUID 연결&quot; 워크플로우를 수정합니다.
* FORMS-14844: 적응형 Forms은 reCAPTCHA 확인에 실패하더라도 양식을 제출할 수 있습니다.
* FORMS-14984: 제출된 데이터에 &quot;submitMetaData&quot;가 없는 경우 CAPTCHA가 있는 Forms에서 유효성 검사를 건너뜁니다.
* FORMS-14477: 날짜 선택기 확인에서 규칙 편집기의 &quot;다음 이후&quot; 및 &quot;다음 이전&quot; 옵션이 작동하지 않습니다.
* FORMS-14019: 규칙 편집기의 &quot;서비스 호출&quot; 기능이 유니버설 편집기에서 작동하지 않습니다.
* FORMS-14336: 양식 필드를 선택하지 않으면 편집기가 전체 양식 요소에 포커스를 두고 열려야 합니다.
* FORMS-15061: 로더 서클은 규칙 편집기에서 서비스 옵션 호출 을 사용할 때 무기한 유지됩니다.
* SITES-22457: 깊지 않은 론치를 홍보해도 소스 콘텐츠는 업데이트되지 않습니다.
* SITES-22748 [컨텐츠 조각] 콘텐츠 조각 업데이트 작업에 대한 오류 처리 개선
* SITES-22349 [컨텐츠 조각] 빈 여러 줄 cf-element에 대한 ContentType은 변경할 수 없습니다.
* SITES-22343 [컨텐츠 조각] 의미 체계 유형 &quot;열거형&quot;이 손상되었습니다.
* SITES-22194: 리디렉션을 설정한 후에 model.json이 더 이상 작동하지 않습니다.
* SITES-21953 [API 열기] Etag는 validationStatus의 순서에 따라 변경됩니다.
* SITES-21894 [API 열기] CF를 만들 때 상위 경로 유효성 검사를 강화합니다.
* SITES-21887 [API 열기] POST 변형 끝점에서 잘못된 ETag가 반환되었습니다.
* SITES-21657 [API 열기] CF 검색 경로 속성에서 유효성 검사를 개선합니다.
* SITES-21949: 검색 API의 잘못된 커서가 500을 반환합니다.
* SITES-20927: 검색 API는 쿼리가 누락된 경우 500을 반환합니다.
* SITES-20544 [API 열기] oak 충돌을 방지하기 위해 게시 패키지 이름 생성을 변경합니다.
* SITES-19710: CVE-2022-47937 - 페이지 편집기에서 org.apache.sling.commons.json의 모든 사용을 제거합니다.
* SITES-11992 [접근성] 주석 견본 선택기 단추에 액세스 가능한 이름이 없습니다.
* SITES-10979 [접근성] 레이블이 지속되지 않습니다.
* SITES-10962 [접근성] 단추: 단추에 역할이 없습니다.
* SITES-10905 [접근성] 활성 구성 요소의 상태에 3:1 명암비가 없습니다.
* 사이트-2974:  [접근성] - 320px 너비에서 수평 스크롤링.
* SITES-22026: AEM의 폴더 간에 경험 조각을 이동할 수 없음
* SITES-22106: 새 콘텐츠 조각 편집기의 언어 전환 기능 문제
* SITES-21980: UUID 기반 참조 유형에 대한 처리가 일관되지 않습니다.
* SITES-7257: ThumbnailServlet의 NPE.

### 알려진 문제 {#known-issues-16971}

없음.

### 변경 사항 공지 {#change-notice-16971}

* 2024년 9월부터 AEM as a Cloud Service는 Sling Model Exporter 프레임워크를 통해 Resource Resolver의 직렬화를 비활성화합니다. 자세한 내용은 [설명서](/help/implementing/developing/hybrid/disallow-the-serialization-of-resourceresolvers-via-sling-model-exporter.md)를 참조하십시오.

### 사용 중단된 기능 및 API {#deprecated-16971}

AEM as a Cloud Service에서 더 이상 사용되지 않는 기능을 살펴보려면 [사용 중단된 기능 및 API](/help/release-notes/deprecated-removed-features.md)를 참조하십시오.

### 임베드된 기술 {#embedded-tech-16971}

| 기술 | 버전 | 링크 |
|---|---|---|
| AEM Oak | 1.64.0 | [Oak API 1.64.0 API](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.64.0/index.html) |
| AEM SLING API | 2.27.2 | [Apache Sling API 2.27.2 API](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 1.4.22-1.4.0 | [HTML 템플릿 언어 사양](https://github.com/adobe/htl-spec) |
| AEM 핵심 구성 요소 | 2.25.4 | [AEM WCM 핵심 구성 요소](https://github.com/adobe/aem-core-wcm-components) |
