---
title: ' [!DNL Adobe Experience Manager] as a Cloud Service의 2021.1.0 릴리스 정보입니다.'
description: "[!DNL Adobe Experience Manager] 2021.1.0용 as a Cloud Service 릴리스 노트"
exl-id: cd639736-6e3d-4b69-b8ae-11e4e6490535
source-git-commit: bc4da79735ffa99f8c66240bfbfd7fcd69d8bc13
workflow-type: tm+mt
source-wordcount: '863'
ht-degree: 14%

---


# [!DNL Adobe Experience Manager] as a Cloud Service 릴리스 노트  {#release-notes}

다음 섹션에서는 다음에 대한 일반 릴리스 노트를 간략하게 설명합니다 [!DNL Experience Manager] as a Cloud Service.

## 릴리스 날짜 {#release-date}

에 대한 릴리스 날짜 [!DNL Adobe Experience Manager] as a Cloud Service 2021.1.0은 2021년 2월 3일입니다.
다음 릴리스(2021.2.0)는 2021년 2월 25일에 있습니다.

## [!DNL Adobe Experience Manager Sites] as a Cloud Service {#sites}

* **[컨텐츠 조각 HTTP API](/help/assets/content-fragments/assets-api-content-fragments.md)**: HTTP API를 사용하여 컨텐츠 조각 변형을 추가/업데이트 및 삭제하는 기능을 추가합니다.

* **[컨텐츠 조각 전달을 위한 GraphQL API](/help/headless/graphql-api/content-fragments.md)**: GraphQL 구문을 사용하여 컨텐츠 조각을 쿼리하고 컨텐츠 조각 모델을 기반으로 하여 JSON 형식으로 출력하는 기능입니다.

* **[GraphQL API 요청에 대한 인증 지원](/help/headless/security/authentication.md)**: 서버측 API에 대한 액세스 토큰을 사용하여 GraphQL API 요청을 인증할 수 있습니다.

* JSON 형식 및 로케일로 리치 텍스트를 출력하는 기능을 포함하여 GraphQL API에서 JSON 출력이 향상되었습니다.

* 전용 컨텐츠 조각 참조 데이터 유형 또는 여러 줄 텍스트 필드에서 인라인으로 컨텐츠 조각 참조를 통해 중첩된 컨텐츠 조각 구조를 만들 수 있도록 컨텐츠 조각 모델 중첩을 지원합니다.

* &quot;고유함&quot;, &quot;필수&quot; 및 &quot;번역 가능한&quot; 등 컨텐츠 조각 모델 데이터 유형에서 사용할 수 있는 추가 유효성 검사 규칙입니다.

* 컨텐츠 조각 모델에 태그를 지정하고 태그 또는 경로별 정책이 있는 폴더에서 컨텐츠 조각을 만들 수 있습니다.

* 조각 기반의 모델 게시 작업 및 표시를 포함하여 컨텐츠 조각 편집기의 유용성 개선 사항.

* 컨텐츠 조각 편집기에서 직접 JSON 출력을 미리 볼 수 있습니다.


## [!DNL Adobe Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

* [!DNL Experience Manager] 로서의 [!DNL Cloud Service] 는 스마트 태그 기능을 확장하여 텍스트 기반 자산에서 키워드 및 엔티티 식별을 지원합니다. 텍스트는 식별, 색인 지정 및 메타데이터로 사용할 수 있으므로 구성이 필요 없습니다. 자세한 내용은 [스마트 태그](/help/assets/smart-tags.md).

* 이제 MXF 파일 형식이 지원됩니다. 자세한 내용은 [지원되는 파일 형식](/help/assets/file-format-support.md#video-formats).

## Adobe Experience Manager Commerce as a Cloud Service {#cloud-services-commerce}

### 새로운 기능 {#what-is-new-commerce}

* 제품 경험 관리: 자산 및 경험 조각에 대한 새 &#39;상거래&#39; 속성 탭입니다. 이 탭에서는 제품/카테고리를 자산 및 경험 조각에 연결할 수 있습니다. 또한 탭에는 연결된 제품/카테고리에 대한 실시간 데이터와 제품 콘솔에 세부 사항을 보여주는 링크가 표시됩니다.

* 최신 CIF 코어 구성 요소 버전 v1.7.0이 포함된 CIF Venia 참조 사이트 - 2021.02.02이 출시되었습니다. 다음을 참조하십시오. [CIF Venia 참조 사이트](https://github.com/adobe/aem-cif-guides-venia/releases/tag/venia-2021.02.02) 자세한 내용

* CIF 코어 구성 요소 v1.7.0이 출시되었습니다. 자세한 내용은 [CIF 코어 구성 요소](https://github.com/adobe/aem-core-cif-components/releases/tag/core-cif-components-reactor-1.7.0) 자세한 내용

## Cloud Manager {#cloud-manager}

### 릴리스 날짜 {#release-date-cm}

AEM as a Cloud Service 2021.1.0의 Cloud Manager 릴리스 날짜는 2021년 1월 14일입니다.

### 버그 수정 {#bug-fixes-cloud-manager}

* Assets 프로덕션 인스턴스는 상황에 따라 **환경** 세부 사항 페이지 *보류 중* 사용자가 작업을 수행할 수 없도록 함.

* Cloud Manager에서 최대 절전 모드 해제를 트리거할 때 최대 절전 모드를 성공적으로 시작한 경우에도 오류 메시지가 표시되는 경우가 있습니다.

* 환경 만들기 또는 삭제에서 발생한 드문 오류 문제가 해결되었습니다.

## 코드 리팩터링 도구 {#code-refactoring-tools}

### [!DNL Code Refactoring Tools]의 새로운 기능 {#what-is-new-crt}

* 새로운 버전의 AIO-CLI 플러그인이 출시되었습니다. 이 플러그인의 최신 버전에는 AEM Dispatcher Converter 및 Repository Modernizer에 대한 버그 수정이 포함되어 있으며 새로운 유틸리티인 Index Converter도 지원합니다. 자세한 내용은 [통합 경험](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/refactoring-tools/unified-experience.html?lang=en#benefits) 추가 정보

* Index Converter는 고객의 사용자 지정 OAK 색인 정의를 AEM as a Cloud Service 호환 OAK 색인 정의로 변환하는 데 사용할 수 있는 유틸리티입니다. 자세한 내용은 [인덱스 변환기](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/index-converter) 자세한 내용

* 에 추가된 새로운 기능 [Repository Modernizer](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/repository-modernizer) 별도의 패키지를 만드는 `ui.config` 모든 OSGi 구성을 포함합니다.

### 버그 수정 {#crt-bug-fixes}

* AEM Dispatcher Converter 및 Repository Modernizer 도구에서 수행한 몇 가지 버그 수정. 자세한 내용은 [AEM Dispatcher 변환기](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/dispatcher-converter) 및 [Repository Modernizer](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/repository-modernizer).

## AEM as a Cloud Service 기반 {#aem-as-a-cloud-service-foundation}

### 새로운 기능 {#what-is-new-foundation}

* 서버 간 인증된 API 호출 - 적절한 액세스 토큰을 생성하여 외부 애플리케이션과 AEM as a Cloud Service 환경 간에 인증된 서버 간 API 호출을 생성합니다. 자세한 내용 읽기 [설명서](/help/implementing/developing/introduction/generating-access-tokens-for-server-side-apis.md) 또는 컨설팅 [튜토리얼](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/authentication/overview.html?lang=en#authentication).

### SDK Build Analyzer {#sdk-build-analyzers}

AEM as a Cloud Service SDK Build Analyzer Maven 플러그인은 누락된 종속성을 포함하여 Maven 프로젝트의 문제를 감지합니다. Cloud Manager를 사용하여 클라우드 환경에 배포하기 전에 개발자에게 로컬 개발 중에 문제를 발견할 수 있는 기회를 제공합니다.

이 릴리스에 대해 두 개의 새로운 분석 기능이 추가되었습니다.

* 포인트 분석기
* bundle-nativecode

자세한 내용은 [여기](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/build-analyzer-maven-plugin.html?lang=ko-KR#developing)에서 설명서를 참조하십시오.

## 클라우드 전환 도구 {#code-transition-tools}

### 릴리스 날짜 {#release-date-ctt}

콘텐츠 전송 도구 v1.2.2의 릴리스 날짜는 2021년 2월 01일입니다.

### [!DNL Content Transfer Tool]의 새로운 기능 {#what-is-new-ctt}

* 컨텐츠 전송 도구 - 사용자 매핑 도구에 추가된 새로운 기능 및 UI입니다. 이 기능은 기존 사용자 및 그룹을 컨텐츠 마이그레이션 활동의 일부로 Adobe Identity Management 시스템 ID에 자동으로 매핑합니다. 을(를) 참조하십시오. [사용자 매핑 도구 사용](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-user-mapping-tool.html) 자세한 내용
* 이제 컨텐츠 전송 도구는 하위 항목을 포함하여 마이그레이션 세트에서 참조되는 모든 그룹 및 사용자를 마이그레이션합니다.
* 사용자는 `/etc` 마이그레이션 세트를 만들 때.
