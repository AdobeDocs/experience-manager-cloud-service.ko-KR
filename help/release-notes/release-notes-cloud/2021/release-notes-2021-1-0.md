---
title: ' [!DNL Adobe Experience Manager] as a Cloud Service의 2021.1.0 릴리스 정보입니다.'
description: "[!DNL Adobe Experience Manager] 2021.1.0의 as a Cloud Service 릴리스 노트"
exl-id: cd639736-6e3d-4b69-b8ae-11e4e6490535
source-git-commit: 1994b90e3876f03efa571a9ce65b9fb8b3c90ec4
workflow-type: tm+mt
source-wordcount: '854'
ht-degree: 24%

---


# [!DNL Adobe Experience Manager]as a Cloud Service 릴리스 정보 {#release-notes}

다음 섹션에서는 의 일반 릴리스 정보에 대해 간략히 소개합니다. [!DNL Experience Manager] as a Cloud Service.

## 릴리스 일자 {#release-date}

의 릴리스 날짜 [!DNL Adobe Experience Manager] as a Cloud Service 2021.1.0은 2021년 2월 3일입니다.
다음 릴리스(2021.2.0) 날짜는 2021년 2월 25일입니다.

## [!DNL Adobe Experience Manager Sites] as a Cloud Service {#sites}

* **[콘텐츠 조각 HTTP API](/help/assets/content-fragments/assets-api-content-fragments.md)**: HTTP API를 사용하여 콘텐츠 조각 변형을 추가/업데이트 및 삭제하는 기능을 추가합니다.

* **[컨텐츠 조각 전달을 위한 GraphQL API](/help/headless/graphql-api/content-fragments.md)**: JSON 형식의 출력을 위해 GraphQL 구문 및 콘텐츠 조각 모델을 기반으로 하는 스키마를 사용하여 콘텐츠 조각을 쿼리하는 기능입니다.

* **[GraphQL API 요청에 대한 인증 지원](/help/headless/security/authentication.md)**: 서버측 API에 대한 액세스 토큰을 사용하여 GraphQL API 요청을 인증하는 기능입니다.

* 리치 텍스트를 JSON 형식 및 로케일로 출력하는 기능을 포함하여 GraphQL API의 JSON 출력이 향상되었습니다.

* 전용 콘텐츠 조각 참조 데이터 유형 또는 여러 줄 텍스트 필드에 인라인으로 콘텐츠 조각 참조를 통해 중첩된 콘텐츠 조각 구조를 만들 수 있도록 콘텐츠 조각 모델을 중첩하는 기능을 지원합니다.

* &quot;고유&quot;, &quot;필수&quot; 및 &quot;변환 가능&quot;을 포함하여 콘텐츠 조각 모델 데이터 유형에서 사용할 수 있는 추가 유효성 검사 규칙입니다.

* 콘텐츠 조각 모델에 태그를 지정하고 태그 또는 경로별 정책이 있는 폴더에서 콘텐츠 조각을 만들 수 있습니다.

* 조각이 기반으로 하는 모델의 게시 작업 및 표시를 포함하여 콘텐츠 조각 편집기의 사용성이 개선되었습니다.

* 콘텐츠 조각 편집기에서 직접 JSON 출력을 미리 볼 수 있습니다.


## [!DNL Adobe Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

* [!DNL Experience Manager] as a [!DNL Cloud Service] 는 스마트 태그 기능을 확장하여 텍스트 기반 에셋에서 키워드 및 엔티티를 식별할 수 있도록 지원합니다. 텍스트가 식별, 색인화되고 메타데이터로 제공되어 구성 없이도 검색 환경을 개선할 수 있습니다. 다음을 참조하십시오 [스마트 태그](/help/assets/smart-tags.md).

* 이제 MXF 파일 포맷이 지원됩니다. 다음을 참조하십시오 [지원되는 파일 형식](/help/assets/file-format-support.md#video-formats).

## Adobe Experience Manager Commerce as a Cloud Service {#cloud-services-commerce}

### 새로운 기능 {#what-is-new-commerce}

* 제품 경험 관리: 에셋 및 경험 조각에 대한 새로운 &#39;Commerce&#39; 속성 탭입니다. 이 탭에서는 제품/범주를 에셋 및 경험 조각에 연결할 수 있습니다. 탭에는 연결된 제품/범주에 대한 실시간 데이터와 제품 콘솔에 세부 정보를 표시하는 링크도 표시됩니다.

* 최신 CIF 코어 구성 요소 버전 v1.7.0이 포함된 CIF Venia 참조 사이트 - 2021.02.02가 릴리스되었습니다. 다음을 참조하십시오 [CIF Venia 참조 사이트](https://github.com/adobe/aem-cif-guides-venia/releases/tag/venia-2021.02.02) 을 참조하십시오.

* CIF 코어 구성 요소 v1.7.0이 릴리스되었습니다. 다음을 참조하십시오 [CIF 핵심 구성 요소](https://github.com/adobe/aem-core-cif-components/releases/tag/core-cif-components-reactor-1.7.0) 을 참조하십시오.

## Cloud Manager {#cloud-manager}

### 릴리스 일자 {#release-date-cm}

AEM as a Cloud Service 2021.1.0의 Cloud Manager 릴리스 일자는 2021년 1월 14일입니다.

### 버그 수정 {#bug-fixes-cloud-manager}

* Assets 프로덕션 인스턴스는 사용자가 어떤 조치도 취하지 않고 **환경** 세부 정보 페이지에서 Brand Portal 상태를 *보류 중*&#x200B;으로 표시할 수 있습니다.

* Cloud Manager에서 최대 절전 모드 해제를 트리거할 때 최대 절전 모드가 성공적으로 시작된 경우에도 실패 메시지가 표시되는 경우가 있었습니다.

* 환경 생성 또는 삭제 시 드물게 발생하던 오류가 해결되었습니다.

## 코드 리팩터링 도구 {#code-refactoring-tools}

### [!DNL Code Refactoring Tools]의 새로운 기능 {#what-is-new-crt}

* 새로운 버전의 AIO-CLI 플러그인이 출시되었습니다. 이 플러그인의 최신 버전에는 AEM Dispatcher Converter 및 Repository Modernizer에 대한 버그 수정이 포함되어 있으며 새 유틸리티인 Index Converter도 지원합니다. 다음을 참조하십시오 [통합 경험](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/refactoring-tools/unified-experience.html?lang=en#benefits) 이 플러그인에 대해 자세히 알아보십시오.

* AEM Index Converter는 고객의 사용자 지정 OAK 색인 정의를 as a Cloud Service으로 호환되는 OAK 색인 정의로 변환하는 데 사용할 수 있는 유틸리티입니다. 다음을 참조하십시오 [인덱스 변환기](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/index-converter) 을 참조하십시오.

* 새 기능이에 추가됨 [저장소 현대화 도구](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/repository-modernizer) 별도의 패키지를 만드는 경우 `ui.config` 모든 OSGi 구성을 포함합니다.

### 버그 수정 {#crt-bug-fixes}

* AEM Dispatcher Converter 및 Repository Modernizer 도구에서 수행된 몇 가지 버그 수정 사항. 다음을 참조하십시오 [AEM Dispatcher 변환기](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/dispatcher-converter) 및 [저장소 현대화 도구](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/repository-modernizer).

## AEM as a Cloud Service Foundation {#aem-as-a-cloud-service-foundation}

### 새로운 기능 {#what-is-new-foundation}

* 서버 간 인증된 API 호출 - 적절한 액세스 토큰을 생성하여 외부 애플리케이션과 AEM as a Cloud Service 환경 간에 인증된 서버 간 API 호출을 수행합니다. 읽기를 통해 자세히 알아보기 [설명서](/help/implementing/developing/introduction/generating-access-tokens-for-server-side-apis.md) 또는 다음을 참조하십시오. [튜토리얼](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/authentication/overview.html?lang=en#authentication).

### SDK Build Analyzer {#sdk-build-analyzers}

AEM as a Cloud Service SDK Build Analyzer Maven 플러그인은 누락된 종속성을 포함하여 Maven 프로젝트의 문제를 감지합니다. Cloud Manager를 사용하여 클라우드 환경에 배포하기 전에 개발자에게 로컬 개발 중에 문제를 발견할 수 있는 기회를 제공합니다.

이 릴리스에는 두 개의 분석기가 새로 추가되었습니다.

* repoinit analyzer
* bundle-nativecode

자세한 내용은 [여기](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/build-analyzer-maven-plugin.html?lang=ko-KR#developing)에서 설명서를 참조하십시오.

## 클라우드 전환 도구 {#code-transition-tools}

### 릴리스 일자 {#release-date-ctt}

콘텐츠 전송 도구 v1.2.2의 릴리스 날짜는 2021년 2월 01일입니다.

### [!DNL Content Transfer Tool]의 새로운 기능 {#what-is-new-ctt}

* 컨텐츠 전송 도구 - 사용자 매핑 도구에 새로운 기능과 UI가 추가되었습니다. 이 기능은 콘텐츠 마이그레이션 활동의 일부로 기존 사용자 및 그룹을 Adobe Identity Management 시스템 ID에 자동으로 매핑합니다. 자세한 내용은 [사용자 매핑 도구 사용](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-user-mapping-tool.html)을 참조하십시오.
* 이제 콘텐츠 전송 도구는 하위 그룹을 포함하여 마이그레이션 세트에서 참조된 모든 그룹과 사용자를 마이그레이션합니다.
* 사용자는 아래에서 특정 경로를 선택할 수 있습니다. `/etc` 마이그레이션 세트를 생성할 때.
