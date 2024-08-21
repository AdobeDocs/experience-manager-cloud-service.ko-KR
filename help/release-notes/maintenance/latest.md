---
title: ' [!DNL Adobe Experience Manager] as a Cloud Service의 현재 유지 관리 릴리스 정보입니다.'
description: ' [!DNL Adobe Experience Manager] as a Cloud Service의 현재 유지 관리 릴리스 정보입니다.'
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: 80edd0255b38beee93b3f9c779ae0f364500b4a5
workflow-type: ht
source-wordcount: '1176'
ht-degree: 100%

---


# 유지 관리 릴리스 정보 {#maintenance-release-notes}

다음 섹션에서는 Experience Manager as a Cloud Service 현재 유지 관리 릴리스의 기술 릴리스 정보에 대해 간략히 소개합니다.

## 릴리스 17465 {#release-17465}

2024년 8월 14일에 릴리스된 유지 관리 릴리스 17465의 지속적인 개선 사항이 아래에 요약되어 있습니다. 이전 유지 관리 릴리스는 릴리스 17258이었습니다.

이 유지 관리 릴리스(2024.8.0)에 대한 기능 활성화는 전체 기능 세트를 제공합니다. 자세한 내용은 [Experience Manager 릴리스 로드맵](https://experienceleague.adobe.com/ko/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap)을 참조하십시오.

### 개선 사항 {#enhancements-17465}

* FORMS-15436 - Adobe Sign Status 스케줄러의 예외 사항을 정상적으로 처리합니다.
* FORMS-15362 - aemds의 forms-foundation에 대한 구성을 추가하여 로그인을 활성화합니다.
* FORMS-15261 - SPA는 양식 편집기에서 렌더링되지 않습니다.
* FORMS-15138 - sling commons json 업그레이드로 인해 Double 데이터 하위 호환성 처리를 개선합니다.
* FORMS-15113 - 키 이름을 vistorId에서 sid로 변경하여 RUM을 추적합니다.
* FORMS-15103 - 양식에 첨부된 자산은 Edge Delivery에 게시되지 않습니다.
* FORMS-15082 - 사용자 정의 적응형 양식 구성 요소에 매핑할 JSON 스키마입니다.
* FORMS-15002 - v1 조각의 템플릿 유형 등록입니다.
* FORMS-14845 - Forms Manager를 통해 핵심 구성 요소 기반 양식에서 xdpRef를 지원합니다.
* FORMS-14840 - 양식 미리 채우기 서비스 오류가 발생합니다.
* FORMS-14836 - AF1 조각 템플릿 나열을 위해 Forms Manager UI를 개선합니다.
* FORMS-14834 - AF1에서 조각의 템플릿을 지원합니다.
* FORMS-14275 - 임베드 컨테이너에서 감사 페이지와 감사 메시지를 재정의합니다.
* FORMS-13623 - V2에 대한 자동 저장 시간 기능을 활성화합니다.
* FORMS-8651 - 데이터 모델 구성 변경에 대한 경고 대화 상자가 양식 속성 페이지에 표시됩니다.
* SITES-23310 - 콘텐츠 조각 REST API: 콘텐츠 조각의 중첩된 참조에서 원형 종속을 방지합니다.
* SITES-23285 - 콘텐츠 조각 REST API: 엔드포인트를 만들어 사용 가능한 모든 언어를 나열할 수 있습니다.
* SITES-22857 - 콘텐츠 조각 REST API: 확인란 열거형 필드를 통해 여러 속성을 false로 설정해서는 안됩니다.
* SITES-22813 - 콘텐츠 조각 REST API: 열거형 필드의 최소/최대 속성을 정의합니다.
* SITES-22031 - 콘텐츠 조각 REST API: 조각 폴더에 허용된 콘텐츠 조각 모델을 가져옵니다.
* SITES-17640 - 콘텐츠 조각 REST API: 콘텐츠 조각 게시 작업 유효성 검사를 실시합니다.
* SITES-22677 - 콘텐츠 조각 REST API: 하위 참조의 플랫 목록을 검색합니다.
* SITES-22207 - 콘텐츠 조각 생성 시 모델이 복제됩니다.
* SITES-23093 - 이벤트: 콘텐츠 조각 모델 이벤트의 페이로드에 태그를 추가합니다.
* SITES-23092 - 이벤트: 콘텐츠 조각 이벤트의 페이로드에 태그를 추가합니다.
* SITES-22447 - 기본 속성 탭에 경험 조각 속성 상속 지원을 추가합니다.
* SITES-12209 - 색인에 cq:policy를 추가하여 정책 편집기 성능을 개선합니다.

### 해결된 문제 {#fixed-issues-17465}

* CQ-4358028 - 썸네일이 업로드되면 프로젝트를 생성할 수 없습니다.
* CQ-4357891 - 내보낸 XLIFF에 시퀀스 문제가 발생합니다.
* CQ-4357059 - 번역 작업 완료 시 몇 시간이 소요되어 AEMaaCS에 503 시간 초과 오류가 발생합니다.
* FORMS-15320 - 핵심 구성 요소 기반 양식에서 이메일을 제출할 수 없습니다.
* FORMS-15272 - AEM Forms - 확인란 그룹은 1개의 값만 전송합니다.
* FORMS-15269 - 유지 관리 릴리스 16461을 설치한 후 제품 관련 문제가 발생합니다.
* FORMS-15174 - JsonSchemaParser는 유효한 문제입니다.
* FORMS-15095 - 여러 줄 텍스트 상자를 확장하여 AEM Forms에 패널을 포함할 수 있습니다.
* FORMS-15057 - FDM Sharepoint 목록에서 999이상 첨부 파일을 제출하는 경우 오류가 발생합니다.
* FORMS-15011 - 편집기에서 양식을 여는 동안 핵심 편집기에 콘솔 오류가 발생합니다.
* FORMS-14809 - SDK 폴더는 공유 임시 디렉터리 내에서 자동으로 생성되지 않습니다.
* FORMS-14327 - Forms 서비스 API: 데이터 추출: 입력 시 비대화형 PDF가 공급되면 500 응답 코드가 제공됩니다.
* FORMS-7475 - 적응형 양식 만들기 페이지가 정렬되지 않습니다.
* FORMS-3309 - 양식 제출 시 여러 옵션을 선택하면 생성된 DoR에는 하나의 옵션만 표시됩니다.
* SITES-23646 - 필드에 고유 모델이 포함되면 OpenAPI로 만든 모델은 GraphQL 모델 엔드포인트가 활성화되지 않습니다.
* SITES-23637 - 콘텐츠 조각 REST API: OpenAPI는 정확한 열거형 값 유형을 사용하지 않습니다.
* SITES-23573 - 콘텐츠 조각 REST API: uuid를 기준으로 GET 콘텐츠 조각에서 라이브 관계가 적용되지 않습니다.
* SITES-23535 - 콘텐츠 조각 REST API: 콘텐츠 조각 모델 열거형 다중 필드에는 비어 있는 값이 있습니다.
* SITES-23534 - 콘텐츠 조각 REST API: 콘텐츠 조각 유효성 검사 ClassCastException이 발생합니다.
* SITES-23524 - GraphQL BFF 모델 엔드포인트를 조정하여 다중 필드 열거형 필드를 지원합니다.
* SITES-23467 - 콘텐츠 조각 REST API: 커서 문제로 인해 모델을 검색할 수 없습니다.
* SITES-23327 - 타임라인 이벤트 처리 설명 도중에 AuditLogTimelineEventProvider에서 ArrayIndexOutOfBoundsException이 발생합니다.
* SITES-23277 - 콘텐츠 조각 REST API: 라이브 카피에 대해서만 콘텐츠 조각 필드 라이브 관계를 검사해야 합니다.
* SITES-23232 - 사용자 정의 유효성 검사는 새 CF 편집기 UI에서 작동하지 않습니다.
* SITES-23090 - 콘텐츠 조각 REST API: 잠긴 콘텐츠 조각 제목을 업데이트할 수 없습니다.
* SITES-22981 - 깊이가 없는 중첩 론치를 홍보하면 게시되지 않습니다.
* SITES-22870 - PathAttributesHandler.processSrcAttr ArrayIndexOutOfBoundsException이 발생합니다.
* SITES-22814 - 콘텐츠 조각 REST API: 확인란 열거형 조각 필드 값 순서는 모델에 정의된 키에 따라 변경되어야 합니다.
* SITES-22716 - OOTB 구성 요소 라이브 사용량 목록에 문제가 발생합니다.
* SITES-22457 - 깊이가 없는 실행을 홍보하면 소스 콘텐츠가 업데이트되지 않습니다.
* SITES-22449 - AEM P20이 업그레이드되면 콘텐츠 조각의 변경 사항을 저장할 수 없습니다.
* SITES-22279 - 콘텐츠 조각 REST API: 콘텐츠 조각에는 열거형에 대한 고유 속성이 없습니다.
* SITES-22203 - 콘텐츠 조각 REST API: 동일한 상황에 동일한 방식으로 응답하도록 관리 API를 정렬합니다.
* SITES-21973 - 콘텐츠 조각 REST API: 모델에는 열거형에 대한 고유 속성이 없습니다.
* SITES-20364 - 302 리디렉션이 URL의 선택기에서 작동하지 않습니다.
* SITES-21198 - VersionPreviewServlet: 병합 충돌을 유발하는 모든 클러스터 노드에서 정리를 동시에 실행하고 커밋을 차단합니다.

### 알려진 문제 {#known-issues-17465}

* ASSETS-40875 - AssetDeleteHandler 클래스는 자산 삭제 이벤트를 수신하고 삭제 이벤트 유형(PRE_DELETE 또는 POST_DELETE)에 따라 특정 작업을 수행합니다. 특정 시나리오에서는 POST_DELETE 유형의 이벤트로 인해 NullPointerException이 발생합니다.
* FORMS-14340 - FormsAndDocumentOmniSearchHandler 및 CloudStorageSubmitActionInserter를 인스턴스화하는 도중 오류가 발생했습니다. 이는 해를 미치지 않는 로그 구문입니다.
* FORMS-15818 - 구성 요소 설명자 항목 &#39;OSGI-INF/com.adobe.aemfd.docmanager.impl.*.xml&#39; 이 서버 로그에서 구문을 찾을 수 없습니다. 이는 해를 미치지 않는 로그 구문입니다.
* 
   * SITES-23662 - 게시를 트리거하는 사용자를 서버 로그의 JCR 로그 구문에서 추출할 수 없습니다. 이는 로그에 간헐적이고 해를 미치지 않는 “일괄 OSGI 이벤트에서 유효한 사용자 ID를 찾을 수 없습니다.”라는 오류가 발생할 수 있는 개발 중인 기능에 대한 것입니다.

### 변경 사항 공지 {#change-notice-17465}

* 2024년 9월부터 AEM as a Cloud Service는 Sling Model Exporter 프레임워크를 통해 Resource Resolver의 직렬화를 비활성화합니다. 자세한 내용은 [설명서](/help/implementing/developing/hybrid/disallow-the-serialization-of-resourceresolvers-via-sling-model-exporter.md)를 참조하십시오.

### 사용 중단된 기능 및 API {#deprecated-17465}

현재 `com.day.cq.wcm.api` 업데이트가 진행 중이며, 현재 릴리스에서는 몇 가지 메서드와 클래스를 `@Deprecated`로 표시했습니다. 이러한 기능은 향후 릴리스에서 제거될 예정이므로, 해당 기능을 사용 중이라면 제안된 대체 기능으로 전환하는 것을 고려해 보시기 바랍니다.

AEM as a Cloud Service에서 더 이상 사용되지 않는 기능과 API는 [사용 중단된 기능 및 API](/help/release-notes/deprecated-removed-features.md) 문서에 자세히 설명되어 있습니다.

### 보안 수정 {#security-17465}

AEM as a Cloud Service는 플랫폼의 보안 및 성능을 최적화하는 데 사용됩니다. 이 유지 관리 릴리스에서는 강력한 시스템 보호에 대한 노력의 일환으로 식별된 취약점 7개가 해결되었습니다.

### 임베드된 기술 {#embedded-tech-17465}

| 기술 | 버전 | 링크 |
|---|---|---|
| AEM Oak | 1.66.0 | [Oak API 1.66.0 API](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.66.0/index.html) |
| AEM SLING API | 2.27.2 | [Apache Sling API 2.27.2 API](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 1.4.24-1.4.0 | [HTML 템플릿 언어 사양](https://github.com/adobe/htl-spec) |
| AEM 핵심 구성 요소 | 2.25.4 | [AEM WCM 핵심 구성 요소](https://github.com/adobe/aem-core-wcm-components) |
