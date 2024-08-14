---
title: ' [!DNL Adobe Experience Manager] as a Cloud Service의 현재 유지 관리 릴리스 정보입니다.'
description: ' [!DNL Adobe Experience Manager] as a Cloud Service의 현재 유지 관리 릴리스 정보입니다.'
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: 8c1bad70a82775c1c99b0c35f07e0d1cae602230
workflow-type: tm+mt
source-wordcount: '1153'
ht-degree: 15%

---


# 유지 관리 릴리스 정보 {#maintenance-release-notes}

다음 섹션에서는 Experience Manager as a Cloud Service 현재 유지 관리 릴리스의 기술 릴리스 정보에 대해 간략히 소개합니다.

## 릴리스 17465 {#release-17465}

다음은 2024년 8월 14일에 공개적으로 릴리스된 유지 보수 릴리스 17465에 대한 지속적인 개선 사항을 요약했습니다. 이전 유지 관리 릴리스는 릴리스 17258.

이 유지 관리 릴리스(2024.8.0)에 대한 기능 활성화는 전체 기능 세트를 제공합니다. 자세한 내용은 [Experience Manager 릴리스 로드맵](https://experienceleague.adobe.com/ko/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap)을 참조하십시오.

### 개선 사항 {#enhancements-17465}

* FORMS-15436 - Adobe Sign 상태 스케줄러에서 예외를 정상적으로 처리합니다.
* FORMS-15362 - aemds에서 forms-foundation 구성을 추가하여 로그인을 활성화합니다.
* FORMS-15261 - SPA이 Forms 편집기에서 렌더링되지 않습니다.
* FORMS-15138 - sling commons json 업그레이드로 인한 이전 버전의 더블 데이터 호환성 처리.
* FORMS-15113 - RUM 추적을 위해 방문자에서 sid로 키 이름 변경.
* FORMS-15103 - 양식에 첨부된 Assets이 edge 게재에서 게시되지 않습니다.
* FORMS-15082 - 사용자 지정 적응형 양식 구성 요소에 매핑할 JSON 스키마.
* FORMS-15002 - v1 조각의 템플릿 유형 등록입니다.
* FORMS-14845 - forms manager를 통해 핵심 구성 요소 기본 양식에서 xdpRef를 지원합니다.
* FORMS-14840 - Forms 미리 채우기 서비스 오류.
* FORMS-14836 - Forms Manager UI를 개선하여 AF1 조각 템플릿을 나열합니다.
* FORMS-14834 - AF1의 조각에 대한 템플릿 지원.
* FORMS-14275 - 포함 컨테이너의 감사 페이지 및 감사 메시지 재정의.
* FORMS-13623 - V2에 대해 시간 기반 자동 저장 기능을 활성화합니다.
* FORMS-8651 - 양식 속성 페이지의 데이터 모델 구성 변경에 대한 경고 대화 상자.
* SITES-23310 - 콘텐츠 조각 REST API: 콘텐츠 조각에 대한 중첩된 참조에서 순환 종속성을 방지합니다.
* SITES-23285 - 콘텐츠 조각 REST API: 사용 가능한 모든 언어를 나열하기 위한 끝점을 만듭니다.
* SITES-22857 - 콘텐츠 조각 REST API: 확인란 열거 필드에서는 여러 속성을 false로 설정할 수 없습니다.
* SITES-22813 - 콘텐츠 조각 REST API: 열거형 필드에 대한 최소/최대 속성을 정의합니다.
* SITES-22031 - 콘텐츠 조각 REST API: 조각 폴더에 대해 허용되는 콘텐츠 조각 모델을 가져옵니다.
* SITES-17640 - 콘텐츠 조각 REST API: 콘텐츠 조각 Publish 작업 유효성 검사.
* SITES-22677 - 콘텐츠 조각 REST API: 하위 참조의 플랫 목록을 검색합니다.
* SITES-22207 - 콘텐츠 조각 생성 시 복제된 모델.
* SITES-23093 - 이벤트: 콘텐츠 조각 모델 이벤트에 대한 페이로드에 태그를 추가합니다.
* SITES-23092 - 이벤트: 컨텐츠 조각 이벤트에 대한 페이로드에 태그를 추가합니다.
* SITES-22447 - 경험 조각 속성 상속 지원을 기본 속성 탭에 추가합니다.
* SITES-12209 - 색인에 cq:policy를 추가하여 정책 편집기 성능을 개선합니다.

### 해결된 문제 {#fixed-issues-17465}

* CQ-4358028 - 썸네일이 업로드된 경우 프로젝트를 만들지 못했습니다.
* CQ-4357891 - 내보낸 XLIFF의 시퀀스 문제.
* CQ-4357059 - 번역 작업을 완료하는 데 몇 시간이 걸려 AEMaaCS에서 503 시간 제한이 발생합니다.
* FORMS-15320 - 이메일 제출이 핵심 구성 요소 기반 양식에서 작동하지 않습니다.
* FORMS-15272 - AEM Forms - 1개의 값만 전송하는 확인란 그룹입니다.
* FORMS-15269 - 유지 관리 릴리스 16461 후 제품 관련 문제가 발생합니다.
* FORMS-15174 - JsonSchemaParser isValid 문제.
* FORMS-15095 - 여러 줄 텍스트 상자를 AEM Forms의 포함 패널 이상으로 확장할 수 있습니다.
* FORMS-15057 - 제출용 첨부 파일 오류가 발생한 FDM Sharepoint 목록 > 999.
* FORMS-15011 - 편집기에서 양식을 여는 동안 코어 편집기에서 콘솔 오류가 발생합니다.
* FORMS-14809 - 공유 임시 디렉터리 내에 SDK 폴더가 자동으로 만들어지지 않습니다.
* FORMS-14327 - Forms 서비스 API : 데이터 추출:- 비대화형 PDF가 입력에 제공되면 500개의 응답 코드를 제공합니다.
* FORMS-7475 - 적응형 양식 만들기 페이지에서 정렬이 작동하지 않습니다.
* FORMS-3309 - 양식을 제출할 때 여러 옵션이 선택된 경우 생성된 DoR에서 하나의 옵션만 표시됩니다.
* SITES-23646 - 필드에 고유한 값이 포함된 경우 OpenAPI로 생성된 모델에 대해 GraphQL 모델 엔드포인트가 실패합니다.
* SITES-23637 - 콘텐츠 조각 REST API: OpenAPI가 열거형에 올바른 값 유형을 사용하지 않습니다.
* SITES-23573 - 콘텐츠 조각 REST API: UUID로 GET 콘텐츠 조각에서 라이브 관계가 적용되지 않습니다.
* SITES-23535 - 콘텐츠 조각 REST API: 콘텐츠 조각 모델 열거 다중 필드에 빈 값이 있습니다.
* SITES-23534 - 콘텐츠 조각 REST API: 콘텐츠 조각 유효성 검사 ClassCastException.
* SITES-23524 - 다중 필드 열거 필드를 지원하도록 GraphQL BFF 모델 엔드포인트를 조정합니다.
* SITES-23467 - 콘텐츠 조각 REST API: 커서 문제로 인해 검색 모델이 실패합니다.
* SITES-23327 - 타임라인 이벤트 처리 설명 중 AuditLogTimelineEventProvider의 ArrayIndexOutOfBoundsException.
* SITES-23277 - 콘텐츠 조각 REST API: 콘텐츠 조각 필드 라이브 관계 검사는 라이브 카피에 대해서만 수행해야 합니다.
* SITES-23232 - 사용자 지정 유효성 검사가 새 CF 편집기 UI에서 작동하지 않습니다.
* SITES-23090 - 콘텐츠 조각 REST API: 잠긴 콘텐츠 조각의 제목을 업데이트할 수 없습니다.
* SITES-22981 - 깊지 않은 중첩 실행을 프로모션하면 게시되지 않습니다.
* SITES-22870 - PathAttributesHandler.processSrcAttr ArrayIndexOutOfBoundsException.
* SITES-22814 - 콘텐츠 조각 REST API: 확인란 열거 조각 필드 값은 모델에 정의된 키를 기준으로 순서가 지정되어야 합니다.
* SITES-22716 - OOTB 구성 요소 라이브 사용량 목록 문제
* SITES-22457 - 깊지 않은 론치를 홍보해도 소스 콘텐츠는 업데이트되지 않습니다.
* SITES-22449 - AEM P20 업그레이드 후 콘텐츠 조각의 변경 사항을 저장할 수 없습니다.
* SITES-22279 - 콘텐츠 조각 REST API: 콘텐츠 조각에 열거 유형에 대한 고유한 특성이 없습니다.
* SITES-22203 - 콘텐츠 조각 REST API: 관리 API를 정렬하여 동일한 상황에 대해 동일하게 응답합니다.
* SITES-21973 - 콘텐츠 조각 REST API: 모델에 열거 유형에 대한 고유한 특성이 없습니다.
* SITES-20364 - 302 리디렉션이 URL의 선택기에서 작동하지 않습니다.
* SITES-21198 - VersionPreviewServlet: 정리 가 병합 충돌 및 블록 커밋을 발생시키는 모든 클러스터 노드에서 동시에 실행됩니다.

### 알려진 문제 {#known-issues-17465}

* ASSETS-40875 - AssetDeleteHandler 및 Handler의 NullPointerException이 페이지에 대해 트리거되고 있습니다.
* FORMS-14340 - FormsAndDocumentOmniSearchHandler 및 CloudStorageSubmitActionInserter를 인스턴스화하는 동안 오류가 발생했습니다. 무해한 로그 문입니다.
* FORMS-15818 - 구성 요소 설명자 항목 &#39;OSGI-INF/com.adobe.aemfd.docmanager.impl.서버 로그에서 *.xml&#39; 문을 찾을 수 없습니다. 무해한 로그 문입니다.
* 
   * SITES-23662 - 게시를 트리거하는 사용자는 서버 로그의 JCR 로그 문에서 추출할 수 없습니다. 이는 개발 중인 기능으로 인해 로그에 &quot;OSGI 이벤트 배치에서 유효한 사용자 ID를 찾을 수 없음&quot; 오류가 발생하여 간헐적이고 문제가 없을 수 있습니다.

### 변경 사항 공지 {#change-notice-17465}

* 2024년 9월부터 AEM as a Cloud Service는 Sling Model Exporter 프레임워크를 통해 Resource Resolver의 직렬화를 비활성화합니다. 자세한 내용은 [설명서](/help/implementing/developing/hybrid/disallow-the-serialization-of-resourceresolvers-via-sling-model-exporter.md)를 참조하십시오.

### 사용 중단된 기능 및 API {#deprecated-17465}

`com.day.cq.wcm.api`을(를) 업데이트하는 중입니다. 현재 릴리스에서는 일부 메서드 및 클래스를 `@Deprecated`(으)로 표시했습니다. 이러한 수정 사항은 향후 릴리스에서 제거될 예정이므로, 이러한 수정 사항 중 하나를 사용 중인 경우 해당 수정 사항으로 전환하는 것을 고려해 보십시오.

AEM as a Cloud Service에서 더 이상 사용되지 않는 기능과 API는 [사용 중단된 기능 및 API](/help/release-notes/deprecated-removed-features.md) 문서에 자세히 설명되어 있습니다.

### 보안 수정 사항 {#security-17465}

AEM as a Cloud Service은 플랫폼의 보안 및 성능을 최적화하는 데 전념하고 있습니다. 이 유지 관리 릴리스는 7개의 식별된 취약점을 해결하여 강력한 시스템 보호에 대한 약속을 강화합니다.

### 임베드된 기술 {#embedded-tech-17465}

| 기술 | 버전 | 링크 |
|---|---|---|
| AEM Oak | 1.66.0 | [Oak API 1.66.0 API](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.66.0/index.html) |
| AEM SLING API | 2.27.2 | [Apache Sling API 2.27.2 API](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 1.4.24-1.4.0 | [HTML 템플릿 언어 사양](https://github.com/adobe/htl-spec) |
| AEM 핵심 구성 요소 | 2.25.4 | [AEM WCM 핵심 구성 요소](https://github.com/adobe/aem-core-wcm-components) |
