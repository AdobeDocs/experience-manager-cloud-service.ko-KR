---
title: ' [!DNL Adobe Experience Manager] as a Cloud Service의 현재 유지 관리 릴리스 정보입니다.'
description: ' [!DNL Adobe Experience Manager] as a Cloud Service의 현재 유지 관리 릴리스 정보입니다.'
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: c1e175128ab6e4b483e3940d9bd86a06540ef40f
workflow-type: tm+mt
source-wordcount: '770'
ht-degree: 20%

---


# 유지 관리 릴리스 정보 {#maintenance-release-notes}

다음 섹션에서는 Experience Manager as a Cloud Service의 현재 유지 관리 릴리스에 대한 기술 릴리스 정보를 간략히 소개합니다.

## 릴리스 24464 {#release-24464}

다음은 2026년 2월 18일에 공개적으로 릴리스된 유지 보수 릴리스 24464에 대한 지속적인 개선 사항을 요약했습니다. 이전 유지 관리 릴리스는 릴리스 24288.

2026.2.0 기능 활성화는 이 유지 관리 릴리스에 대한 전체 기능 세트를 제공합니다. 자세한 내용은 [Experience Manager 릴리스 로드맵](https://experienceleague.adobe.com/ko/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap)을 참조하십시오.

### 개선 사항 {#enhancements-24464}

* AEMARCH-264: RequestEntity를 기반으로 조건부 요청의 유효성 검사에 대한 지원을 추가합니다.
* AEMARCH-269: OpenAPI 구현을 위해 JavaEE 유효성 검사 API를 노출합니다.
* AEMARCH-276: RequestEntity를 통해 i18n 지원을 제공합니다.
* ASSETS-10995: 다운로드 zip에서 에셋 수에 대한 제한을 설정합니다.
* ASSETS-50788: 에셋 메타데이터 GET API를 사용하도록 검색 API를 업데이트합니다.
* ASSETS-50946: 메타데이터 GET API를 사용하여 요청 본문을 JCR 메타데이터에 매핑합니다.
* ASSETS-55866: 이전 처리가 완료될 때까지 동일한 에셋에 대한 새 요청을 제출하지 마십시오.
* ASSETS-60300: 비동기 작업 컨텍스트 및 결과를 검색하기 위한 API를 제공합니다.
* ASSETS-60574: 최신 버전의 Sling API 번들에 대한 지원을 추가합니다.
* ASSETS-61049: 메타데이터 관리자 번들 개발을 계속합니다.
* ASSETS-61692: 검색 Open API에서 기본적으로 의미 체계 검색을 수행합니다.
* ASSETS-61696: 에셋 보기의 BAM 경로 및 MFE 래퍼.
* ASSETS-61854: 활성화/비활성화 메시지에서 GenStudio 솔루션을 보냅니다.
* ASSETS-61973: AEM에서 프롬프트 관리를 위한 API를 만듭니다.
* ASSETS-62182: c2pa-manifest 렌디션에 대한 Asset Compute 이벤트 핸들러입니다.
* ASSETS-62311: 검색 회귀 문제.
* ASSETS-62413: JSON의 모든 레이어에 customModifier 필드에 대한 지원을 추가합니다.
* ASSETS-62432: 폴더 병합 삭제 API PR.
* ASSETS-62540: 빠른 시작에서 ui-touch-optimized 버전을 늘립니다.
* ASSETS-62622: MatchQuery에서 검색 모드를 처리합니다.
* ASSETS-62671: MatchQuery startsWith 연산자를 수정합니다.
* ASSETS-62780: 폴더 API에 대한 기능 추가 토글
* ASSETS-62988: c2pa 매니페스트 렌디션이 렌디션 탭에 표시되지 않도록 숨깁니다.
* ASSETS-63336: AEM에서 DM으로 템플릿 동기화를 수행하는 것은 dam 네임스페이스가 지정된 메타데이터에만 해당됩니다.
* ASSETS-63375: 에셋 업로드 실험적 OpenAPI를 기능 전환 뒤에 배치합니다.
* ASSETS-63453: 모든 사용자가 omnisearch 구성을 읽을 수 있는지 확인합니다.
* GRANITE-63744: 비동기 작업을 슬링 작업에 연결할 수 있습니다.
* GRANITE-64567: SKU 검색에 대한 의미 체계 검색을 자동으로 비활성화합니다.
* GUIDES-41187: 안내서 사용을 위한 헤더를 추가합니다.
* SITES-30452: ASO가 포함된 콘텐츠 API - 제목 및 설명 제안.
* SITES-33116: 경로 유효성 검사를 수정합니다.
* SITES-34234: 페이지 편집기: 컨텐츠 트리 상태를 유지합니다.

### 해결된 문제 {#fixed-issues-24464}

* ASSETS-43198: 에셋 만료 알림 이메일이 사용자 언어 기본 설정을 준수하지 않습니다.
* ASSETS-51840: 에셋 처리 개선 사항.
* ASSETS-52061: 저장된 검색을 선택한 후 다시 탐색할 수 없습니다.
* ASSETS-53155: 에셋 콘텐츠 개선 사항.
* ASSETS-53745: Dynamic Media 다운로드 흐름을 사용하려면 웹 사전 설정을 선택하기 전에 원본 에셋을 선택 취소해야 합니다.
* ASSETS-54260: 에셋 콘텐츠 수정 사항.
* ASSETS-54787: 에셋 콘텐츠 개선 사항.
* ASSETS-57391: 에셋 콘텐츠 업데이트.
* ASSETS-59213: cq-dynamicmedia-core는 더 이상 사용되지 않는 commons-lang 라이브러리에 따라 다릅니다.
* ASSETS-59214: cq-scene7-imaging은 더 이상 사용되지 않는 commons-lang 라이브러리에 따라 다릅니다.
* ASSETS-59546: cq-remotedam-client-core는 더 이상 사용되지 않는 commons-lang 라이브러리에 따라 다릅니다.
* ASSETS-59703: cq-dam-core는 더 이상 사용되지 않는 commons-lang 라이브러리에 따라 다릅니다.
* ASSETS-59705: cq-dam-handler는 더 이상 사용되지 않는 commons-lang 라이브러리에 따라 다릅니다.
* ASSETS-59707: cq-dam-indesign은 더 이상 사용되지 않는 commons-lang 라이브러리에 따라 다릅니다.
* ASSETS-59709: cq-scene7-core는 더 이상 사용되지 않는 commons-lang 라이브러리에 따라 다릅니다.
* ASSETS-59929: 필드에 새 줄 문자가 있을 때 메타데이터 내보내기의 CSV가 중단됩니다.
* ASSETS-60241: 폴더 이름을 바꿀 때 비동기 이동 작업이 실패합니다.
* ASSETS-61134: pom 파일에서 comparisonVersion 태그를 제거합니다.
* ASSETS-61309: 콘텐츠 조각 이동/복사는 더 이상 내부 참조를 업데이트하지 않습니다.
* ASSETS-61730: 다이렉트 이진 액세스가 에셋 인코딩을 준수하도록 리디렉션합니다.
* ASSETS-62358: Assets 보고서 CSV가 컨텐츠 경로에 손상된 값을 표시합니다.
* ASSETS-62610: Assets UI에서 Adobe Stock 라이선스 버튼이 비활성화되었습니다.
* ASSETS-62613: `downloadasset`/`saveas`의 NPE.
* ASSETS-62656: Assets 이외의 검색에 대해 Omnisearch AI 검색 표시기가 잘못 표시되었습니다.
* GRANITE-55387: 따옴표로 묶인 단어를 수정하면 전체 단어가 삭제됩니다.
* GRANITE-61240: lazycontainer.js에 저장된 XSS를 통한 RCE.
* GRANITE-64101: ES로 변환된 OOTB 인덱스가 다시 시작 시 Lucene으로 되돌아갑니다.
* SITES-24530: 검색 모달에서 닫기/제거 단추의 터치 대상이 충분하지 않습니다.
* SITES-31425: 워크플로우 시작에 현지화되지 않은 오류 메시지가 표시됩니다.

### 알려진 문제 {#known-issues-24464}

없음.

### 사용 중단된 기능 및 API {#deprecated-24464}

AEM as a Cloud Service에서 더 이상 사용되지 않는 기능과 API는 [사용 중단된 기능 및 API](/help/release-notes/deprecated-removed-features.md) 문서에 자세히 설명되어 있습니다.

### 보안 수정 {#security-24464}

AEM as a Cloud Service는 플랫폼의 보안 및 성능 최적화에 중점을 둡니다. 이 유지 관리 릴리스는 14개의 식별된 취약점을 해결하여 강력한 시스템 보호에 대한 노력을 강화합니다.

### 임베드된 기술 {#embedded-tech-24464}

| 기술 | 버전 | 링크 |
|---|---|---|
| AEM Oak | 1.90.0 | [Oak 1.90.0 API](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.90.0/index.html) |
| AEM SLING API | 2.27.6 | [Apache Sling API 2.27.6 API](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 1.4.28-1.4.0 | [HTML 템플릿 언어 사양](https://github.com/adobe/htl-spec) |
| Apache HTTP 서버 | 2.4.65 | [Apache Httpd 2.4.65](https://apache.googlesource.com/httpd/+/refs/tags/2.4.65/CHANGES) |
| AEM 핵심 구성 요소 | 2.30.4 | [AEM WCM 핵심 구성 요소](https://github.com/adobe/aem-core-wcm-components) |
| Node.js | 14 (기본값) | [지원되는 Node.js 버전](https://experienceleague.adobe.com/ko/docs/experience-manager-cloud-service/content/implementing/developing/developing-with-front-end-pipelines#node-versions) |

