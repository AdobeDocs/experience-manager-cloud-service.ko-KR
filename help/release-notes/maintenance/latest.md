---
title: ' [!DNL Adobe Experience Manager] as a Cloud Service의 현재 유지 관리 릴리스 정보입니다.'
description: ' [!DNL Adobe Experience Manager] as a Cloud Service의 현재 유지 관리 릴리스 정보입니다.'
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: 7d93af706d8b0556e9e26282d339794447eb0a41
workflow-type: tm+mt
source-wordcount: '1514'
ht-degree: 15%

---


# 유지 관리 릴리스 정보 {#maintenance-release-notes}

다음 섹션에서는 Experience Manager as a Cloud Service의 현재 유지 관리 릴리스에 대한 기술 릴리스 정보를 간략히 소개합니다.

## 릴리스 20133 {#20133}

다음은 2025년 4월 1일에 공개적으로 릴리스된 유지 보수 릴리스 20133에 대한 지속적인 개선 사항을 요약했습니다. 이전 유지 관리 릴리스는 릴리스 19823.

2025.4.0 기능 활성화는 이 유지 관리 릴리스에 대한 전체 기능 세트를 제공합니다. 자세한 내용은 [Experience Manager 릴리스 로드맵](https://experienceleague.adobe.com/ko/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap)을 참조하십시오.

### 개선 사항 {#enhancements-20133}

* ASSETS-47850: AEM CS가 ES로 설정된 경우 Scene7 구성 추가를 제한합니다.
* CQ-4359547: https://git.corp.adobe.com/target-sdk/tsdk-core 저장소에서 구아바를 완전히 제거합니다.
* FORMS-17551: SharePoint 목록 통합에 대한 DoR(Document of Record) 지원이 추가되었습니다.
* FORMS-18432: OSGI 수준 변경 없이 선택적 미리 채우기 기능을 사용할 수 있도록 양식별(정규 표현식 기반) 클라이언트측 미리 채우기 구성이 구현되었습니다.
* FORMS-18513: AEP Connector에서 데이터 트리 변환 지원을 구현하여 마법사 기능과 데이터 처리 기능을 개선했습니다.
* FORMS-19068: 양식 데이터 통합 기능을 향상시키기 위해 Forms Manager API에 AEP 커넥터 제출 작업에 대한 지원이 추가되었습니다.
* GRANITE-57717: AEM에서 클라이언트 번들을 업데이트합니다.
* SITES-10469: AdapterFactory는 항상 동일한 PageManager 인스턴스를 반환해야 합니다.
* SITES-25130: 릴리스 핵심 구성 요소 2.28.0.
* SITES-25433: 이전 버전을 비교할 때 전체 페이지 렌더링을 지원합니다.
* SITES-25923: LinkInfoStorageImpl은 더 이상 URL이 저장되지 않을 때 차단할 수 있습니다.
* SITES-26208: 이제 워크플로우를 통해 콘텐츠 조각을 삭제하면 새로 삭제된 조각을 제거하여 참조 리소스를 업데이트하는 옵션이 제공됩니다.
* SITES-26500: 워크플로 - `move-fragments`을(를) 통해 콘텐츠 조각을 이동하는 옵션을 추가합니다.
* SITES-26711: 롤아웃 트리거 - 링크가 업데이트되지 않습니다.
* SITES-27583: 이동 후 버전 기록이 손실되는 경험 조각입니다.
* SITES-27618: 페이지에서 조각 참조를 검색해도 모든 결과가 반환되지 않습니다.
* SITES-27781: 콘텐츠 조각 참조에 대한 모델 수준 유효성 검사를 구현하여 모델 제약 조건 및 필수 태그에 대한 참조된 조각의 유효성 검사를 가능하게 했습니다.
* SITES-27784: `jcr:path` 대신 PATH 함수를 사용하도록 SQL 쿼리 생성을 업데이트하십시오.
* SITES-28040: Adobe Target ExperienceFragmentsReplicationListener가 손상되었습니다.
* SITES-28051: 컨텐츠 조각: GET /cf/fragments/{fragmentId}/permissions에 대한 현재 사용자의 권한을 가져옵니다.
* SITES-28190: 통합 테스트 미리 보기를 설정합니다.
* SITES-28227: 조각에 대한 참조로 에셋을 추가할 때 에셋이 존재하는지 확인합니다.
* SITES-28248: OSGI 구성을 기반으로 사이트 이벤트를 전환합니다.
* SITES-28255: 생성됨, 수정됨, 게시됨 등 3개의 감사 속성에서 전체 이름이 누락되었습니다.
* SITES-28390: PageImpl: hasContent()를 최적화합니다.
* SITES-28404: 작성자의 페이지를 삭제하면 미리보기 서비스에서 게시가 취소되어야 합니다.
* SITES-28446: 응답에 표시되지 않은 2개의 새 필드, 즉 NumberModelField의 자리 표시자와 LongTextModelField의 허용된 모델을 추가했습니다.
* SITES-28536: 콘텐츠 조각에 대한 `RENAME` 끝점을 만듭니다.
* SITES-28537: 워크플로 - `rename-fragments`을(를) 통해 콘텐츠 조각의 이름을 바꾸는 옵션을 추가합니다.
* SITES-28538: 작성 및 게시에서 유효한 콘텐츠를 유지 관리하려면 참조를 다시 게시해야 합니다.
* SITES-28549: AEM 계층을 기반으로 도메인 ID를 반환하려면 `/cf/domains`을(를) 만듭니다.
* SITES-29026: 언어 및 국가 코드를 사용하여 콘텐츠 조각의 로케일을 지정하는 선택적 매개 변수를 추가했습니다.
* SITES-29031: PATCH-ing 조각에 대한 논리가 개선되어 더 나은 성능을 제공합니다.
* SITES-29169: 이동, 이름 변경 또는 삭제된 리소스를 참조하는 경우 게시된 모든 리소스(게시됨 또는 수정됨 상태에 관계없이)가 다시 게시됩니다.
* SITES-29376: 게시된 리소스 삭제의 유효성 검사로 코드 추가 토글을 전환합니다.
* SITES-29417: /libs/cq/Page/proxy.jsp을 업데이트하여 를 포함하지 않고 요청을 jcr:content 노드에 전달합니다.
* SITES-2947: kibana 시각화를 생성/수정하여 게시 rasp를 비교합니다.
* SITES-29733: 콘텐츠 조각 태그로 모델 검색 성능이 향상되었습니다.
* SITES-8316: 컨텐츠 정책: ContentPolicyManager를 캐시합니다.
* SITES-24906: 범용 편집기가 있는 Edge Delivery: 매핑 없이 작성자가 만든 스프레드시트를 지원합니다(조기 액세스)
* SITES-24907: 범용 편집기가 있는 Edge Delivery: MSM 사용 사례를 위해 여러 사이트에 Assets 게시를 지원합니다(조기 액세스)
* SITES-27956: 범용 편집기가 있는 Edge Delivery: 게시 처리량 개선(조기 액세스)
* SITES-27956: 범용 편집기가 있는 Edge Delivery: Edge Delivery Services에 게시하기 위한 오류 처리 개선(조기 액세스)

### 해결된 문제 {#fixed-issues-20133}

* CQ-4358378: 번역 실행에서 라이선스 오류 처리.
* CQ-4359263: 작업이 완료되면 대화 상자에 메시지가 표시되지 않습니다.
* CQ-4359386: AEMaaCS의 번역 프로젝트에 i18n 사전을 추가할 수 없습니다.
* FORMS-18068: 리치 텍스트 필드를 사용하는 라디오 버튼 및 확인란 그룹에 대한 DoR(기록 문서)의 굵은 텍스트 렌더링 문제
* FORMS-18189: 빈 클라이언트 라이브러리에 대한 오류 로깅을 방지하고 UI의 오류 표시를 개선하기 위해 사용자 지정 함수 처리를 수정했습니다.
* FORMS-18213: 문서 명확성과 사용자 경험을 개선하기 위해 DoR(Document of Record)에서 비활성화된 필드를 숨기거나 제외하는 기능이 구현되었습니다.
* FORMS-18271: Forms 테마 편집기에 지역화되지 않은 오류 메시지가 표시되어 양식 구성 및 테마 맞춤화의 사용자 경험에 영향을 줍니다.
* FORMS-18304: Acrobat 및 LiveCycle ES4에서 유효성 검사를 통과한 PDF/A-1b 문서는 장치 종속적 색상 오류로 인해 AEM 6.5 Forms에서 비호환 문서로 잘못 플래그가 지정됩니다.
* FORMS-18325: 양식 데이터 통합 및 처리 기능을 개선하기 위해 Adobe Experience Platform(AEP) 클라우드 구성을 추가했습니다.
* FORMS-18360: 데이터 조직 및 액세스 제어를 개선하기 위해 Forms 문서 관리의 팀 사이트에 대한 SharePoint 목록 범위 관리를 개선했습니다.
* FORMS-18375: 특정 구성 컨테이너를 선택하지 않은 경우 Foundation 구성 요소 기반 양식에서 `conf/global` 폴더에서 recaptcha 구성을 잘못 선택합니다.
* FORMS-18426: 목록 이름에 특수 문자(예: &#39;-&#39;)가 포함된 경우 SharePoint 목록 조회 기능이 실패하여 SharePoint 목록과의 양식 통합에 영향을 줍니다.
* FORMS-19028: 클라이언트측 미리 채우기 기능이 양식 이벤트 처리를 중단하여 양식 로드 시 값 커밋 및 DOMContentLoaded 이벤트가 제대로 트리거되지 않도록 합니다.
* FORMS-6950: 파일 시스템 탐색기 트리뷰 구성 요소에 필요한 ARIA 역할 및 속성을 추가하여 화면 판독기 접근성을 개선하고 WCAG 4.1.2 이름, 역할, 값(레벨 A) 표준을 준수합니다.
* FORMS-7016: 양식 편집기의 키보드 포커스 순서가 논리 탐색을 따르지 않습니다.
* SITES-1960: 콘텐츠 조각 편집기의 JSON 미리보기 작업 성능이 개선되었습니다.
* SITES-24308: 콘텐츠 크기가 400%로 조정되면 가로 스크롤 막대가 표시됩니다.
* SITES-24493: 대화형 요소에 필수 역할이 없습니다.
* SITES-24669: 참조 레일 창 분할자에 키보드로 액세스할 수 없습니다.
* SITES-26881: AEMaaCS 접근성 버그 - 댓글 입력 필드 옆에 있는 &quot;세 점&quot; 아이콘에 잘못된 역할이 제공됩니다.
* SITES-26956: 프로덕션 환경에서 페이지를 이동할 수 24920 SITES-Launch에 대한 후속 조치입니다.
* SITES-27707: 에셋 이름 문제(6.5 SP22 회귀)로 인해 콘텐츠 파인더 에셋 목록이 실패합니다.
* SITES-27757: 범용 편집기가 있는 Edge Delivery: helix-html-pipeline 의미에 따라 아이콘을 다시 작성합니다.
* SITES-27780: RTE에 예기치 않은 &lt;br> 태그가 SP22의 일반 텍스트 DefaultPasteMode와 함께 나타납니다.
* SITES-27958: Linkchecker에서 &quot;이 세션이 종료되었습니다&quot; 오류가 발생합니다.
* SITES-28149: Target으로 XF 내보내기를 수행하는 동안 사용자 지정 ExperienceFragmentLinkRewriterProvider가 트리거되지 않았습니다.
* SITES-28449: 워크플로 위젯 UI 버그 - AEM의 모든 하위 페이지를 표시하지 않는 하위 페이지를 포함합니다.
* SITES-28456: GraphiQL 탐색기에서 잘못된 지속 쿼리를 저장하는 경우 UI에 대한 알림이 누락됩니다(후속 조치: SITES-28313).
* SITES-28464: 조각 쿼리를 업데이트하여 밀리초로 서식이 지정된 날짜를 사용합니다.
* SITES-28486: 새 콘텐츠 조각 편집기에서 즉석 편집은 이전 편집기로 리디렉션되지 않습니다.
* SITES-28570: 누락된 에셋 메타데이터는 콘텐츠 조각의 GraphQL에서 올바르게 처리됩니다.
* SITES-28580: SP22 업그레이드 후 클래식 이미지 자산 파인더가 손상되었습니다.
* SITES-28600: Launches - 콘텐츠 복제
* SITES-28668: LaunchPromotionParameters를 사용하여 론치를 홍보할 수 없습니다.
* SITES-28820: 리베이스에서 만든 새 변형 내에 시작 접두사가 두 번 추가되었습니다.
* SITES-28877: 로컬 외부화 끝점이 정의되지 않은 경우 UE URL 서비스에서 예외가 발생합니다.
* SITES-28956: 콘텐츠 조각에서 참조하는 태그가 있는 경우 태그 삭제 작업에 경고가 표시됩니다.
* SITES-29208: 참조 필드에 잘못된 경로가 포함된 경우 참조 및 변형이 제대로 반환됩니다.
* SITES-29363: 라이브 카피 재설정 버튼이 중첩 라이브 카피 콘텐츠 계층에 대해 작동하지 않습니다.
* SITES-29369: AIO의 Assets 이벤트 문제 | 페이지가 게시되거나 게시되지 않은 이벤트를 잘못 트리거합니다.
* SITES-29972: 삭제 및 이름 변경 작업을 수행하면 때로 잘못된 워크플로우 주석이 생성됩니다.

### 알려진 문제 {#known-issues-20133}

없음.

### 사용 중단된 기능 및 API {#deprecated-20133}

AEM as a Cloud Service에서 더 이상 사용되지 않는 기능과 API는 [사용 중단된 기능 및 API](/help/release-notes/deprecated-removed-features.md) 문서에 자세히 설명되어 있습니다.

#### 사용자 그룹 및 제품 프로필 동기화의 변경 사항 {#changes-user-groups}

권한 관리를 위해 Adobe Admin Console을 사용할 때는 더 이상 AEM과 동기화되지 않으므로 다음 그룹을 사용해서는 안 됩니다.
* _GROUP_NAME_SUFFIX로 끝나는 AEM 그룹.
* 다른 환경, 프로그램 또는 제품의 제품 프로필.

자세한 내용은 [사용자 그룹 및 제품 프로필 동기화의 변경 사항](https://experienceleague.adobe.com/ko/docs/experience-manager-cloud-service/content/security/changes-in-user-group-and-product-profile-synchronization)을 확인해 주십시오.

#### SPA 편집기 사용 중단 {#deprecate-spa-editor}

[SPA 편집기](/help/implementing/developing/hybrid/introduction.md)는 릴리스 2025.4.0부터 새 프로젝트에 대해 더 이상 사용되지 않습니다. SPA 편집기는 기존 프로젝트에 대해 계속 지원되지만 새 프로젝트에 사용해서는 안 됩니다.

AEM에서 Headless 콘텐츠를 관리하기 위한 권장 편집기는 다음과 같습니다.

* 시각적 편집을 위한 [범용 편집기](/help/edge/wysiwyg-authoring/authoring.md)
* 양식 기반 편집을 위한 [콘텐츠 조각 편집기](/help/assets/content-fragments/content-fragments-managing.md)

이 사용 중단에 대한 자세한 내용은 [SPA 편집기 사용 중단](/help/implementing/developing/hybrid/spa-editor-deprecation.md) 문서에서 확인할 수 있습니다.

### 보안 수정 {#security-20133}

AEM as a Cloud Service는 플랫폼의 보안 및 성능 최적화에 중점을 둡니다. 이 유지 관리 릴리스는 34개의 식별된 취약점을 해결하여 강력한 시스템 보호에 대한 노력을 강화합니다.

### 임베드된 기술 {#embedded-tech-20133}

| 기술 | 버전 | 링크 |
|---|---|---|
| AEM Oak | 1.76.0 | [Oak API 1.76.0 API](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.76.0/index.html) |
| AEM SLING API | 2.27.6 | [Apache Sling API 2.27.6 API](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 1.4.26-1.4.0 | [HTML 템플릿 언어 사양](https://github.com/adobe/htl-spec) |
| AEM 핵심 구성 요소 | 2.28.0 | [AEM WCM 핵심 구성 요소](https://github.com/adobe/aem-core-wcm-components) |
