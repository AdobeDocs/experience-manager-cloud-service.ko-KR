---
title: ' [!DNL Adobe Experience Manager] as a Cloud Service의 현재 유지 관리 릴리스 정보입니다.'
description: ' [!DNL Adobe Experience Manager] as a Cloud Service의 현재 유지 관리 릴리스 정보입니다.'
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: 77d8ebeaa3914f4a91d2cf27ccc5b048e64d6b38
workflow-type: tm+mt
source-wordcount: '887'
ht-degree: 16%

---


# 유지 관리 릴리스 정보 {#maintenance-release-notes}

다음 섹션에서는 Experience Manager as a Cloud Service의 현재 유지 관리 릴리스에 대한 기술 릴리스 정보를 간략히 소개합니다.

## 릴리스 19352 {#19352}

2025년 2월 5일에 공개적으로 릴리스된 유지 보수 릴리스 19352에 대한 지속적인 개선 사항을 요약하면 다음과 같습니다. 이전 유지 관리 릴리스는 릴리스 19149.

2025.2.0 기능 활성화는 이 유지 관리 릴리스에 대한 전체 기능 세트를 제공합니다. 자세한 내용은 [Experience Manager 릴리스 로드맵](https://experienceleague.adobe.com/ko/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap)을 참조하십시오.

### 개선 사항 {#enhancements-19352}

* FORMS-13998: 아코디언 구성 요소를 추가합니다.
* FORMS-17913: 라디오 그룹에 대한 카드 변형을 추가합니다.
* FORMS-17333: AEM 양식 제출에서 HTML 이메일 템플릿 활성화.
* FORMS-17702: 출력 동기화 API에서 생성된 PDF을 Azure Blob Storage에 업로드할 수 있습니다.
* SITES-28282: 범용 편집기가 있는 Edge Delivery: 모든 페이지의 페이지 정보로 기본 경로, 사이트 이름 및 조직을 제공합니다.
* SITES-27055: 범용 편집기가 있는 Edge Delivery: 역방향 프록시 서블릿에서 쿼리 매개 변수를 지원합니다.
* SITES-26796: 범용 편집기가 있는 Edge Delivery: 분류 스프레드시트에 대한 사용자 정의 열을 지원합니다.
* SITES-26087: 범용 편집기가 있는 Edge Delivery: 스프레드시트에 대한 CSV 내보내기를 지원합니다.
* SITES-26265: 범용 편집기가 있는 Edge Delivery: 구성 UI에서 Edge Delivery과 통합할 TA 계정을 표시합니다.
* SITES-20372: 범용 편집기가 있는 Edge Delivery: 스프레드시트에 대한 기본 MSM 사용 사례를 활성화합니다.
* SITES-26681: 범용 편집기가 있는 Edge Delivery: 작성자의 분류법 스프레드시트에 대해 ?sheet= 매개변수를 지원합니다.
* SITES-26479: [스키마] 콘텐츠 조각 모델의 예약된 게시 상태 끝점입니다.
* SITES-25944: [Livecopy 개요] 상태 &quot;Live Copy가 상속이 제한된 최신 상태&quot;를 추가합니다.
* SITES-28713: [V2] 콘텐츠 스크레이퍼에 구조화된 데이터 지원을 추가합니다.
* SITES-27896: 알림 시 CommentsTab이 자동으로 열립니다.
* SITES-26720: 사용자는 에셋 선택기에서 전체 컬렉션을 선택할 수 없습니다.
* SITES-27875: 기본적으로 이동할 수 있는 컨테이너 내에서 편집할 수 있도록 만듭니다.
* SITES-28340: Dark Alley 유니버설 편집기 서비스 플러그인.
* SITES-26098: 콘텐츠 조각을 게시할 때 참조된 페이지를 게시하지 않을 수 있습니다.
* SITES-27789: DOM에서 데이터 속성 data-aue-component 지원.
* SITES-25997: 수정된 날짜를 지원하도록 변형을 강화합니다.
* SITES-28023: 원격 자산 참조에 대한 GraphQL 출력(저장소 + 자산 ID).
* SITES-26058: 콘텐츠 조각 모델이 예약된 게시 상태 엔드포인트.
* SITES-25108: UUID 참조에 대한 모델 마이그레이션.
* SITES-26630: 여러 콘텐츠 조각에 대한 콘텐츠 조각 예약된 게시 상태 엔드포인트.
* SITES-23432: 참조 삭제 기능을 개선합니다.
* SITES-25797: 외부 에셋 참조 지원 - GraphQL.
* SITES-17514: 콘텐츠 조각 게시를 취소하기 위한 엔드포인트 개선 사항을 삭제합니다.
* SITES-14633: 설치하기 전에 콘텐츠 조각 모델 유효성을 검사하여 페이로드를 만듭니다. - 시험 실행.

### 해결된 문제 {#fixed-issues-19352}

* SITES-28415: 범용 편집기가 있는 Edge Delivery: 스프레드시트의 열린 속성 수정 단추.
* SITES-26669: 범용 편집기가 있는 Edge Delivery: BOM을 스프레드시트로 사용하여 UTF-8로 인코딩된 CSV 파일을 업로드할 때 발생하는 문제를 해결합니다.
* SITES-26543: 범용 편집기가 있는 Edge Delivery: 잘못된 마크업을 렌더링하는 모델 없이 빈 블록을 수정합니다.
* SITES-26857: 범용 편집기가 있는 Edge Delivery: 파일 기반 구성을 위해 UI에 표시되는 사이트 인증 토큰을 수정합니다.
* SITES-26662: 범용 편집기가 있는 Edge Delivery: 대/소문자를 구분하는 벌크 메타데이터와 관련된 문제를 수정합니다.
* SITES-28133: Publish에서 &quot;미리 보기&quot;로 인해 프로덕션에서 콘텐츠를 사용할 수 있습니다.
* SITES-27187: 참조를 포함하는 예약된 페이지/에셋 활성화(실험)가 참조를 게시하지 못했습니다.
* SITES-27264: 마스터에서 2개의 콘텐츠 조각-LiveCopy-생성 관련 Selenium 테스트가 지속적으로 실패했습니다.
* SITES-26559: 콘텐츠 조각 모델에 대한 쿼리를 cqPageLucene 인덱스에 고정합니다.
* SITES-24469: 대화형 요소에 키보드로 액세스할 수 없습니다.
* SITES-24518: 상위 참조 테이블의 이름 및 모델 단추는 키보드에 액세스할 수 없습니다.
* SITES-27937: 모델을 업데이트한 후 UISchema 제약 조건이 null로 설정됩니다.
* SITES-27852: 모델 UISchema에 분류가 누락되었습니다.
* SITES-27904: 전체 프로젝션을 위한 목록/검색 콘텐츠 조각 모델에서 MetadataSchema가 누락되었습니다.
* SITES-26827: 조각 목록이 무한 루프로 끝납니다.
* SITES-27678: [성능] 불필요한 참조 가져오기를 방지합니다(_R).
* SITES-27589: 여러 콘텐츠/조각 참조 필드가 있는 콘텐츠 조각 모델에 대한 UUID 업그레이드 실패.
* SITES-26679: 콘텐츠 조각 모델 게시 취소는 게시된 참조만 검증해야 합니다.
* SITES-26666: referencesTree 및 참조 끝점이 다른 결과와 함께 반환됩니다.
* SITES-26499: GET 조각에 있는 태그 필드 값의 순서가 잘못되고 PATCH이 순서를 무작위화합니다.
* SITES-26585: 스키마의 작은 설명 오류를 수정합니다.
* SITES-26647: 관리자가 아닌 사용자의 경우 엔드포인트 삭제 및 UnpublishFragments 참조 유효성 검사가 실패할 수 있습니다.
* SITES-26458: [콘텐츠 조각 모델 검색] 복제 상태별로 필터링을 수정합니다.
* SITES-23513: &quot;조각 참조&quot; - &quot;허용된 콘텐츠 조각 모델&quot; 속성에 대해 [콘텐츠 조각 모델 편집기] 유효성 검사가 실패했습니다.
* SITES-26575: 미리보기에서 조각 게시를 취소하면 previewStatus가 업데이트됩니다.
* SITES-26571: FT_SITES-12435이 활성화된 경우 페이지 참조를 저장할 수 없습니다.
* SITES-26660: 가 &quot;문자열&quot; 유형인 경우 콘텐츠 조각 버전 @ContentType이 중단될 수 있습니다.
* SITES-26626: 숫자 및 부울 필드에 customErrorMessage가 누락되었습니다.
* SITES-26268: 조각을 만들 때 참조가 잘못된 경우 잘못된 상태 코드가 반환되었습니다.

### 알려진 문제 {#known-issues-19352}

없음.

### 사용 중단된 기능 및 API {#deprecated-19352}

AEM as a Cloud Service에서 더이상 사용되지 않는 기능과 API는 [사용 중단된 기능 및 API](/help/release-notes/deprecated-removed-features.md) 문서에 자세히 설명되어 있습니다.

### 보안 수정 {#security-19352}

AEM as a Cloud Service는 플랫폼의 보안 및 성능 최적화에 중점을 둡니다. 이 유지 관리 릴리스는 36개의 식별된 취약점을 해결하여 강력한 시스템 보호에 대한 노력을 강화합니다.

### 임베드된 기술 {#embedded-tech-19352}

| 기술 | 버전 | 링크 |
|---|---|---|
| AEM Oak | 1.72.0 | [Oak API 1.72.0 API](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.72.0/index.html) |
| AEM SLING API | 2.27.6 | [Apache Sling API 2.27.6 API](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 1.4.24-1.4.0 | [HTML 템플릿 언어 사양](https://github.com/adobe/htl-spec) |
| AEM 핵심 구성 요소 | 2.27.0 | [AEM WCM 핵심 구성 요소](https://github.com/adobe/aem-core-wcm-components) |
