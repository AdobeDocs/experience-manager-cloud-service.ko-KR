---
title: ' [!DNL Adobe Experience Manager] as a Cloud Service의 현재 유지 관리 릴리스 정보입니다.'
description: ' [!DNL Adobe Experience Manager] as a Cloud Service의 현재 유지 관리 릴리스 정보입니다.'
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: f9f3d1fcb32445269e5ca4b9479b8e9075c73c10
workflow-type: tm+mt
source-wordcount: '852'
ht-degree: 98%

---


# 유지 관리 릴리스 정보 {#maintenance-release-notes}

다음 섹션에서는 Experience Manager as a Cloud Service 현재 유지 관리 릴리스의 기술 릴리스 정보에 대해 간략히 소개합니다.

## 릴리스 18598 {#18598}

2024년 11월 13일에 릴리스된 유지 관리 릴리스 18598의 지속적인 개선 사항이 아래에 요약되어 있습니다. 이전 유지 관리 릴리스는 릴리스 18311였습니다. 릴리스 18459는 문제로 인해 비공개로 전환되었습니다.

이 유지 관리 릴리스(2024.11.0)에 대한 기능 활성화는 전체 기능 세트를 제공합니다. 자세한 내용은 [Experience Manager 릴리스 로드맵](https://experienceleague.adobe.com/ko/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap)을 참조하십시오.

### 개선 사항 {#enhancements-18598}

* CQ-4357471: AEMaaCS에 i18n 사전 번역에 대한 지원이 추가되었습니다.
* FORMS-11646: AEM Forms 관련 페이지에 대해 globalContext 변수를 설정할 수 있습니다.
* FORMS-14833: AEM Forms는 이제 최종 기록 문서(DoR)에 적응형 양식 조각을 포함할 수 있는 기능을 지원합니다.
* FORMS-14255: 이제 사용자는 부분적으로 완료된 양식을 초안으로 자동 저장하는 자동 저장 기능을 활용할 수 있습니다. 나중에 돌아와 동일한 디바이스 또는 다른 디바이스에서 작성을 마칠 수 있습니다.
* SITES-23591: 콘텐츠 조각: UUID 지원을 위한 콘텐츠 조각 업그레이드
* SITES-25440: 콘텐츠 조각: CFM 검색 API를 입력하여 복제 상태를 표시합니다.
* SITES-24369: 콘텐츠 조각: OpenAPI 설명서가 개선되었습니다.
* SITES-25478: 콘텐츠 조각: 외부 자산 참조에 대한 백엔드 지원이 추가되었습니다.
* SITES-26119: 콘텐츠 조각: 참조 유형에서 외부 자산 참조에 대한 지원이 추가되었습니다.
* SITES-24609: 콘텐츠 조각: 콘텐츠 조각을 삭제할 때 유효성 검사를 강화합니다.
* SITES-21199: 범용 편집기가 포함된 Edge Delivery: 페이지에서 생성된 템플릿에 대한 지원이 추가되었습니다.
* SITES-20311: 범용 편집기가 포함된 Edge Delivery: CSV를 스프레드시트로 가져오는 기능이 추가되었습니다.
* SITES-24821: 범용 편집기가 포함된 Edge Delivery: Edge Delivery와 통합하기 위해 aem.page / aem.live가 기본값으로 설정됩니다.

### 해결된 문제 {#fixed-issues-18598}

* CQ-4358730: 번역할 키가 10개가 넘을 때 CQPagePreviewGenerator가 실패합니다.
* CQ-4358028: 프로젝트 관리자 그룹만 있는 사용자가 프로젝트 생성 페이지에 새 썸네일을 업로드할 때 AEM 프로젝트 생성이 실패합니다.
* FORMS-14978: 테마 편집기의 핵심 구성 요소 기반 양식에 대한 페이지 로드가 활성화됩니다.
* FORMS-15682: 이 문제는 AEM Forms와 Dynamics FDM의 통합과 관련이 있습니다. 사용자가 양식을 제출할 때 기록 문서(DOR)가 지정된 엔티티 필드에 PDF 첨부 파일로 전송되지 않습니다.
* FORMS-15799: Adobe Sign GovCloud 서명 페이지가 iframe에서 렌더링되지 않습니다.
* FORMS-16113: Adobe Sign 계정의 관리자가 다른 관리자에 의해 전송된 문서에 액세스하려고 할 때 get agreement API가 계약 생성 당시와 다른 계약 ID를 반환할 수 있습니다.
* FORMS-16596: 접근성 문제: 화면 판독기에서 비활성화된 버튼이 인식되지 않습니다.
* GRANITE-53907: 서비스 사용자를 워크플로 슈퍼 사용자로 식별할 수 없습니다.
* SKYOPS-90560: 최신 Sling 모델 릴리스가 Sling 모델 내보내기 성능에 영향을 미칩니다.
* SITES-10575: MSM: 블루프린트 블룸필터 로더가 100,000개 이상의 행을 로드하려고 합니다.
* SITES-20755: 콘텐츠 조각: UUID를 새로 고침하여 자산 참조를 표시해도 썸네일은 표시되지 않습니다.
* SITES-26253: 콘텐츠 조각: UUID 마이그레이션: sling 작업 항목이 일반 항목으로 변경됩니다.
* SITES-21338: 콘텐츠 조각: referencedBy 엔드포인트가 올바른 페이지 참조를 반환하지 않습니다.
* SITES-24421: 콘텐츠 조각: CF 엔드포인트 편집이 GET CF를 통해 검색된 CF에 대해 작동하지 않습니다.
* SITES-25461: 콘텐츠 조각: CF 검색 시 모델로 필터링할 때 대소문자를 구분하지 않아야 합니다.
* SITES-25471: 콘텐츠 조각: ModelValidatorServlet에서 전역 모델의 유효성 검사가 수정됩니다.
* SITES-25795: 콘텐츠 조각: CQ 날짜가 설정되지 않았을 때 CF 모델 API가 실패합니다.
* SITES-25817: 콘텐츠 조각: promoteLaunch 개선: CF 출시를 위한 마지막 프로모션이 업데이트됩니다.
* SITES-26030: 콘텐츠 조각: Endpoint /referencesTree가 필요한 헤더를 반환하지 않습니다.
* SITES-26031: 콘텐츠 조각: CFM 검색 엔드포인트에서 복제 상태가 반환되지 않습니다.
* SITES-26213: 콘텐츠 조각: 게시 취소된 콘텐츠 조각은 게시된 참조만 검증해야 합니다.
* SITES-26226: 콘텐츠 조각: 지정된 경로를 사용할 수 없을 때 워크플로 문제가 발생합니다.
* SITES-26238: 콘텐츠 조각: API에서 반환된 자산 참조의 순서가 JCR의 순서와 다릅니다.
* SITES-25456: 이벤트: 페이지를 이동할 때 페이지 이동 이벤트 외에도 페이지 삭제 이벤트가 생성됩니다.
* SITES-25658: 이벤트: tier 및 sourceUrl이 페이지 콘텐츠 상태 이벤트에 채워지지 않습니다.
* SITES-6497: 실행: 실행 시 페이지 생성이 작동하지 않습니다.
* SITES-25938: 실행: 번역 프로젝트 이후 예기치 않은 삭제가 발생합니다.
* SITES-25393: 범용 편집기가 포함된 Edge Delivery: 단일 단락으로 구성된 서식이 있는 형식 지정 텍스트를 렌더링하는 경우 텍스트 노드가 손실됩니다.
* SITES-24643: 범용 편집기가 포함된 Edge Delivery: OpenGraph 및 Twitter 메타데이터 속성이 페이지 메타데이터 모델에서 작동하지 않습니다.
* SITES-25401: 경험 조각: XF 참조 업데이트가 느려집니다.

### 알려진 문제 {#known-issues-18598}

없음.

### 사용 중단된 기능 및 API {#deprecated-18598}

AEM as a Cloud Service에서 더 이상 사용되지 않는 기능과 API는 [사용 중단된 기능 및 API](/help/release-notes/deprecated-removed-features.md) 문서에 자세히 설명되어 있습니다.

### 보안 수정 {#security-18598}

AEM as a Cloud Service는 플랫폼의 보안 및 성능을 최적화하는 데 사용됩니다. 이 유지 관리 릴리스에서는 강력한 시스템 보호에 대한 노력의 일환으로 식별된 취약점 21개가 해결되었습니다.

### 임베드된 기술 {#embedded-tech-18598}

| 기술 | 버전 | 링크 |
|---|---|---|
| AEM Oak | 1.70.0 | [Oak API 1.70.0 API](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.70.0/index.html) |
| AEM SLING API | 2.27.6 | [Apache Sling API 2.27.6 API](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 1.4.24-1.4.0 | [HTML 템플릿 언어 사양](https://github.com/adobe/htl-spec) |
| AEM 핵심 구성 요소 | 2.27.0 | [AEM WCM 핵심 구성 요소](https://github.com/adobe/aem-core-wcm-components) |
