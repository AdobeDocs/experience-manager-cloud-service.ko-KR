---
title: ' [!DNL Adobe Experience Manager] as a Cloud Service의 현재 유지 관리 릴리스 정보입니다.'
description: ' [!DNL Adobe Experience Manager] as a Cloud Service의 현재 유지 관리 릴리스 정보입니다.'
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: 39993d115d58d9dfe1f9328c5ceba0d30a78569d
workflow-type: tm+mt
source-wordcount: '1213'
ht-degree: 17%

---


# 유지 관리 릴리스 정보 {#maintenance-release-notes}

다음 섹션에서는 Experience Manager as a Cloud Service의 현재 유지 관리 릴리스에 대한 기술 릴리스 정보를 간략히 소개합니다.

## 릴리스 23385 {#23385}

다음은 2025년 11월 13일에 공개적으로 릴리스된 유지 보수 릴리스 23385에 대한 지속적인 개선 사항을 요약했습니다. 이전 유지 관리 릴리스는 릴리스 22943.

이 유지 관리 릴리스에 대한 2025.11.0 기능 활성화는 전체 기능 세트를 제공합니다. 자세한 내용은 [Experience Manager 릴리스 로드맵](https://experienceleague.adobe.com/ko/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap)을 참조하십시오.

>[!NOTE]
>
>릴리스 23320 및 23122이 비공개로 설정되었습니다.

### 개선 사항 {#enhancements-23385}

* CQ-4361363: 최신 AEM 및 Granite 번역.
* FORMS-21594: 콘텐츠 작성자를 위한 대화형 통신 템플릿 콘텐츠 및 레이아웃 잠금을 활성화합니다.
* FORMS-20385: 대화형 통신 편집기에서 XDP 편집을 지원합니다.
* FORMS-10883: API를 통해 제출된 서식 있는 텍스트 데이터의 정확한 렌더링을 보장하도록 DoR 생성에서 XHTML 네임스페이스 태그와 함께 JSON을 지원합니다.
* FORMS-21751: 캔버스 기능 - 텍스트 오버플로, 페이지 나누기를 위한 UI
* FORMS-22049: 대화형 통신 편집기 - 스펙트럼 2로 마이그레이션.
* FORMS-22050: 대화형 통신 편집기에서 동적 페이지 번호 지정을 지원합니다.
* FORMS-21606: 대화형 커뮤니케이션용 공개 OSGi 렌더링 SPI.
* FORMS-21613: Render Interactive Communications SPIs에 대한 트랜잭션 보고 및 성능 로깅.
* GRANITE-62394: joda-time이 2.12.7로 업데이트되었습니다.
* GRANITE-36205: Oak 릴리스를 1.88.0으로 업데이트합니다.
* GRANITE-62020: `RepositoryServiceHttpClient`에 대한 다시 시도 정책을 개선합니다.
* GRANITE-62169: commons-lang을 3.19.0으로 업데이트합니다.
* SITES-35092: 콘텐츠 조각 - 의미 체계 검색을 위한 새로운 믹스인 및 업그레이드 프로시저.
* SITES-32319: 게재 OpenAPI - 지원 페이지 참조.
* SITES-20123: GraphQL: JSON 응답에서 위 첨자 요소를 지원합니다.
* SITES-34744: 썸네일 렌더링에 사용할 수 있는 데이터가 포함된 콘텐츠 조각 응답의 새 &quot;card&quot; 속성입니다.
* SITES-34571: 열거형 필드가 비어 있도록 허용합니다.
* SITES-34812: &quot;none&quot; 값이 있는 &quot;references&quot; 매개 변수를 사용하여 해당 참조 없이 콘텐츠 조각을 검색하는 기능이 추가되었습니다.
* SITES-35176: 이제 Touch UI를 통해 콘텐츠 조각을 체크 아웃하면 다른 사용자가 새 편집기에서 콘텐츠 조각을 편집할 수 없습니다.
* SITES-30371: UUID 기반 참조 필드에 대한 지원을 추가했습니다.
* SITES-19309: 페이지 이동 마법사를 열 때 최대 150개의 참조를 검색합니다.
* SITES-32515: 범용 편집기가 있는 Edge Delivery - 다중 필드 및 복합 다중 필드에 대한 지원을 추가합니다(조기 액세스).
* SITES-33784: 범용 편집기가 있는 Edge Delivery - 페이지 메타데이터에 ld-json에 대한 지원을 추가합니다.
* SITES-34832: 범용 편집기가 있는 Edge Delivery - 페이지의 공개 경로를 페이지 정보 서블릿 응답에 추가합니다.
* SITES-25893: 범용 편집기가 있는 Edge Delivery - 강력한 지원을 추가하고 블록의 텍스트 렌더링을 강조합니다.
* SITES-26158: 범용 편집기가 있는 Edge Delivery - 블록 및 열의 테이블 마크업에 대한 지원을 추가합니다(조기 액세스).
* SITES-27949: 범용 편집기가 있는 Edge Delivery - 경로 매핑을 선택 사항으로 만듭니다.
* SITES-35811: 콘텐츠 조각 쿼리에 새 인덱스를 사용합니다.
* SKYOPS-120857: filevault를 4.1.4로 업데이트합니다.
* SKYOPS-118390: JCR 리소스를 3.3.6으로 업데이트합니다.
* SKYOPS-121082: `org.apache.sling.discovery.standalone`, `org.apache.sling.jcr.packageinit` 및 `org.apache.sling.commons.fsclassloader` 슬링 번들의 버전을 업데이트합니다.

### 해결된 문제 {#fixed-issues-23385}

* ASSETS-58926: DM에서 비디오 변경 썸네일 기능을 수정합니다.
* ASSETS-58623: 구성이 있으면 omnisearch에서 npe를 수정합니다.
* CQ-4361144: 번역 작업에서 콘텐츠 조각을 건너뛰는 문제를 해결했습니다.
* CQ-4355446: 번역 작업 취소 대화 상자에서 발생하는 번역 프로젝트의 지역화되지 않은 문자열을 수정했습니다.
* CQ-4360747: 반복 가능한 번역 작업이 빈 페이로드를 만들고 너무 자주 트리거하는 문제를 수정했습니다.
* GRANITE-61318: 페이지 생성 마법사가 기본 탭의 필수 필드만 강조 표시하는 문제를 해결합니다.
* GRANITE-60514: 전체 스택 파이프라인 실행 중에 예약된 게시가 중지된 문제를 해결합니다.
* GRANITE-61019: AEM을 다시 시작한 후 처음 실행할 때 GC 문제를 해결합니다.
* GRANITE-60456: 관리자가 사용자의 속성 페이지를 열 때 발생하는 문제를 해결합니다.
* SITES-34555: GraphQL - 배포 후 QueryValidationError.
* SITES-35077: 컨텐츠 조각 - 잘못된 URL 인코딩으로 인해 괄호가 있는 조각에 대한 게시 취소가 실패합니다.
* SITES-35374: 콘텐츠 조각 - 편집된 콘텐츠 조각은 뒤로 이동한 후 사라집니다.
* SITES-36130: `EditorRestrictionsStatusImpl`의 NPE.
* SITES-35810: Launches의 NullPointerException은 publishEdgeDeliverySubscriber 큐를 차단합니다.
* SITES-34368: AEM CIF은 12개의 GraphQL 별칭을 생성합니다. Magento 2.4.6-P12 제한인 10을 초과합니다.
* SITES-36193: CCS 커넥터가 수정되었습니다.
* SITES-35169: 검색에서 잘못된 조각 리소스가 반환될 때 잘못된 페이지 매김을 유발하는 문제를 해결했습니다.
* SITES-34574: 경우에 따라 콘텐츠 조각 검색 API에서 커서가 반환되지 않는 문제를 해결했습니다.
* SITES-35520: 콘텐츠 게시를 시도할 때 ClassCastException 또는 시간 초과를 초래하는 문제를 해결했습니다.
* SITES-35210: 참조 필터가 비어 있는 깨진 조각을 게시하려고 할 때 발생하는 NullPointerException을 수정했습니다.
* SITES-35933: 콘텐츠 조각이 게시된 후 빈 &quot;활성화 요청&quot; 워크플로가 트리거되는 버그가 수정되었습니다.
* SITES-35925: 모델에서 &quot;변환 가능&quot; 및 &quot;showThumbnail&quot; 속성을 삭제하는 콘텐츠 조각 모델 패치와 관련된 버그가 수정되었습니다.
* SITES-35409: 페이지를 이동할 때 조정된 조각을 다시 게시하지 못하게 하던 버그가 수정되었습니다.
* SITES-15757: 페이지를 이동할 때 조정된 페이지를 다시 게시하지 못하게 하던 버그를 수정했습니다.
* SITES-34638: 새 버전을 만들 때 최상위 페이지의 속성이 포함되지 않던 버그를 수정했습니다.
* SITES-35226: 특정 상황에서 페이지 편집기의 자산 선택기를 로드하지 못하게 하는 회귀 문제를 해결했습니다.
* SITES-35071: omnisearch가 따옴표 붙은 구를 사용할 때 CSV 내보내기가 필터링되지 않은 결과를 반환합니다.
* SITES-32182: 범용 편집기가 있는 Edge Delivery - 이미 인코딩된 요청 매개 변수가 포함된 URL의 인코딩 문제를 수정합니다.
* SITES-34324: 범용 편집기가 있는 Edge Delivery - tel: 프로토콜이 있는 링크의 렌더링을 수정합니다.
* SITES-35333: 범용 편집기가 있는 Edge Delivery - 페이지 메타데이터의 이미지에 대한 에셋 렌디션 선택을 수정합니다.
* SITES-35549: 범용 편집기가 있는 Edge Delivery - 페이지 메타데이터의 이중 인코딩 HTML 엔티티를 수정합니다.

#### AEM Guides {#guides-23385}

* GUIDES-33597: 특성이나 값이 없는 빈 `prop` 요소를 DITAVAL 파일에 추가하면 추가 `prop` 요소를 추가할 수 없습니다.
* GUIDES-33693: Experience Manager Guides UI를 통해 편집된 이미지를 다시 업로드하면 이미지의 원래 렌디션이 업데이트되지만 관련 DITA 컨텐츠는 이전 버전의 이미지를 계속 표시합니다.
* GUIDES-35607: Assets UI를 통해 에셋을 업로드하거나 편집기 인터페이스에서 새 파일을 만드는 동안 생성된 오류 로그는 로그 메시지에서 `predecessor` 대신 `successor`이라는 용어를 잘못 사용합니다.
* GUIDES-37649: AEM Sites에서 기준선을 사용하여 DITA 맵을 게시할 때(기존 구성 요소 매핑 사용) `processing-role = resource-only` 특성이 있는 맵 요소도 게시됩니다.

릴리스에서 수정된 새로운 기능과 향상된 기능 및 문제에 대한 자세한 내용은 [Experience Manager Guides 릴리스 로드맵](https://experienceleague.adobe.com/ko/docs/experience-manager-guides/using/release-info/aem-guides-releases-roadmap)을 참조하십시오.


### 알려진 문제 {#known-issues-23385}

* FORMS-22633: GuideBridge API(`getData` 또는 `getDataXML`)에 의존하는 사용자 지정 코드를 사용하는 경우 양식 제출이 실패할 수 있습니다. 이 문제가 발생하는 경우 Adobe 지원 센터에 문의하십시오.

### 사용 중단된 기능 및 API {#deprecated-23385}

AEM as a Cloud Service에서 더 이상 사용되지 않는 기능과 API는 [사용 중단된 기능 및 API](/help/release-notes/deprecated-removed-features.md) 문서에 자세히 설명되어 있습니다.

### 보안 수정 {#security-23385}

AEM as a Cloud Service는 플랫폼의 보안 및 성능 최적화에 중점을 둡니다. 이 유지 관리 릴리스는 31개의 식별된 취약점을 해결하여 강력한 시스템 보호에 대한 노력을 강화합니다.

### 임베드된 기술 {#embedded-tech-23385}

| 기술 | 버전 | 링크 |
|---|---|---|
| AEM Oak | 1.88.0 | [Oak 1.88.0 API](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.88/index.html) |
| AEM SLING API | 2.27.6 | [Apache Sling API 2.27.6 API](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 1.4.28-1.4.0 | [HTML 템플릿 언어 사양](https://github.com/adobe/htl-spec) |
| Apache HTTP 서버 | 2.4.65 | [Apache Httpd 2.4.65](https://apache.googlesource.com/httpd/+/refs/tags/2.4.65/CHANGES) |
| AEM 핵심 구성 요소 | 2.30.2 | [AEM WCM 핵심 구성 요소](https://github.com/adobe/aem-core-wcm-components) |
| Node.js | 14 (기본값) | [지원되는 Node.js 버전](https://experienceleague.adobe.com/ko/docs/experience-manager-cloud-service/content/implementing/developing/developing-with-front-end-pipelines#node-versions) |
