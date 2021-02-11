---
title: Cloud Service으로 [!DNL Adobe Experience Manager] 에 대한 현재 릴리스 노트입니다.
description: Cloud Service으로 [!DNL Adobe Experience Manager] 에 대한 현재 릴리스 노트입니다.
translation-type: tm+mt
source-git-commit: f1a54ac3f995a6e8cc51f9ef16e14df6210a02cd
workflow-type: tm+mt
source-wordcount: '1108'
ht-degree: 3%

---


# [!DNL Adobe Experience Manager] as a Cloud Service 릴리스 노트 {#release-notes}

다음 섹션에서는 Cloud Service으로 [!DNL Experience Manager]에 대한 일반적인 릴리스 노트에 대해 간략하게 설명합니다.

## 릴리스 날짜 {#release-date}

Cloud Service으로 [!DNL Adobe Experience Manager]에 대한 릴리스 날짜는 2021년 2월 3일입니다.
다음 릴리스(2021.2.0)은 2021년 2월 25일에 제공됩니다.

## [!DNL Adobe Experience Manager Sites] cloud service  {#sites}

### 헤드리스 컨텐츠 관리 {#headless}

* **[컨텐츠 조각 전달용 GraphQL API](/help/assets/content-fragments/graphql-api-content-fragments.md)**:JSON 형식으로 출력하기 위해 GraphQL 구문을 사용하고 컨텐츠 조각 모델을 기반으로 하는 스키마를 사용하여 컨텐츠 조각을 쿼리하는 기능

* **[GraphQL API 요청에 대한 인증 지원](/help/assets/content-fragments/graphql-authentication-content-fragments.md)**:서버측 API에 대한 액세스 토큰을 사용하여 GraphQL API 요청을 인증할 수 있습니다.

* **[RemotePage 구성 요소](/help/implementing/developing/hybrid/remote-page.md)**:AEM 내에서 외부 SPA을 보고 편집할 수 있는 지원이 추가되었습니다.

* **[AEM에서 외부 SPA 편집](/help/implementing/developing/hybrid/editing-external-spa.md)**:독립형 단일 페이지 애플리케이션을 AEM 인스턴스에 업로드하고 편집 가능한 컨텐츠 섹션을 추가하고 작성을 활성화하는 기능을 추가했습니다.

* JSON 포맷 및 로캘로 리치 텍스트를 출력하는 기능을 포함하여 GraphQL API에서 향상된 JSON 출력

* 여러 행 텍스트 필드의 전용 컨텐츠 조각 참조 데이터 유형 또는 컨텐츠 조각 참조 인라인을 통해 중첩된 컨텐츠 조각 구조를 만들 수 있도록 컨텐츠 조각 모델을 중첩할 수 있습니다.

* &quot;고유&quot;, &quot;필수&quot; 및 &quot;번역 가능한&quot; 등 컨텐츠 조각 모델 데이터 유형에서 사용할 수 있는 추가 유효성 검사 규칙입니다.

* 컨텐츠 조각 모델에 태그를 지정하고 태그 또는 경로별 정책이 있는 폴더에서 컨텐츠 조각을 작성할 수 있도록 합니다.

* 조각 기반 모델의 게시 작업 및 표시 등 컨텐츠 조각 편집기의 유용성 향상

* 컨텐츠 조각 편집기에서 직접 JSON 출력을 미리 볼 수 있습니다.

<!--
### Progressive Web Apps (PWAs) {#pwa}

* [A Progressive Web App (PWA) version of a site](/help/sites-cloud/authoring/features/enable-pwa.md)  can now be enabled at the project level via simple configuration.
-->

## [!DNL Cloud Service]로서의 [!DNL Adobe Experience Manager Assets] {#assets}

* [!DNL Experience Manager] 는 텍스트 기반 자산에서 키워드 및 엔티티의 식별을 지원하기 위해 스마트 태그 기능을  [!DNL Cloud Service] 확장합니다. 텍스트는 식별되고 인덱싱되며, 아무 구성 없이 검색 환경을 개선하기 위해 메타데이터로 사용할 수 있습니다. [스마트 태그](/help/assets/smart-tags.md)를 참조하십시오.

* 이제 MXF 파일 형식이 지원됩니다. [지원되는 파일 형식](/help/assets/file-format-support.md#video-formats)을 참조하십시오.

## Adobe Experience Manager 상거래를 Cloud Service {#cloud-services-commerce}

### 새로운 기능 {#what-is-new-commerce}

* 제품 경험 관리:자산 및 경험 조각에 대한 새 &#39;상거래&#39; 속성 탭. 이 탭에서는 제품/카테고리를 자산 및 경험 조각에 연결할 수 있습니다. 이 탭에는 연결된 제품/카테고리에 대한 실시간 데이터와 제품 콘솔에 세부 사항을 보여주는 링크가 표시됩니다.

* 최신 CIF 코어 구성 요소 버전 v1.7.0을 포함하는 CIF Venia 참조 사이트 - 2021.02.02. 자세한 내용은 [CIF Venia 참조 사이트](https://github.com/adobe/aem-cif-guides-venia/releases/tag/venia-2021.02.02)를 참조하십시오.

* CIF 코어 구성 요소 v1.7.0 릴리스되었습니다. 자세한 내용은 [CIF 핵심 구성 요소](https://github.com/adobe/aem-core-cif-components/releases/tag/core-cif-components-reactor-1.7.0)를 참조하십시오.

## Cloud Manager {#cloud-manager}

### 릴리스 날짜 {#release-date-cm}

AEM의 Cloud Service 2021.2.0 Cloud Manager에 대한 릴리스 날짜는 2021년 2월 11일입니다.

### 새로운 기능 {#what-is-new-cloud-manager}

* 이제 Cloud Manager Production 파이프라인에 사용자 정의 UI 테스트 기능이 포함됩니다.

* 이제 자산 고객은 Cloud Manager UI를 통해 셀프 서비스 방식으로 브랜드 포털 인스턴스를 배포할 시기와 위치를 선택할 수 있습니다. 자산 솔루션이 있는 일반(샌드박스 아님) 프로그램의 경우 이제 프로덕션 환경에서 브랜드 포털을 프로비저닝할 수 있습니다. 프로비저닝은 프로덕션 환경에서 한 번만 수행할 수 있습니다.

* 프로젝트 및 샌드박스 제작에서 사용되는 AEM 프로젝트 원형이 버전 25로 업데이트되었습니다.

* 코드 스캔 중에 식별된 가치 없는 API 목록은 최신 Cloud Service SDK 릴리스에서 사용되지 않는 추가 클래스 및 메서드를 포함하도록 개선되었습니다.

* Cloud Manager용 SonarQube 프로필이 Sonar 규칙 squid:S2142를 제거하도록 업데이트되었습니다. 더 이상 스레드 중단 검사와 충돌하지 않습니다.

* Cloud Manager UI는 연결된 환경에 연결된 실행 중인 파이프라인이 있거나 현재 승인 단계를 기다리는 중이므로 도메인 이름을 일시적으로 추가/업데이트할 수 없는 사용자에게 알립니다.

* 음파 탐지 접두사가 있는 고객 `pom.xml` 파일에 설정된 속성이 이제 빌드 및 품질 스캔 오류를 방지하기 위해 동적으로 제거됩니다.

* Cloud Manager UI는 현재 배포 중인 도메인 이름으로 사용 중인 경우 일시적으로 SSL 인증서를 선택할 수 없는 사용자에게 알립니다.

* Cloud Service 호환성 문제를 다루는 추가 코드 품질 규칙이 추가되었습니다.

### 버그 수정 {#bug-fixes-cloud-manager}

* 도메인 이름과 SSL 인증서를 일치시키는 것이 더 이상 대소문자를 구분하지 않습니다.

* 이제 인증서 개인 키가 적절한 오류 메시지와 함께 2048비트 제한에 도달하지 않는 경우 Cloud Manager UI는 사용자에게 알립니다.

* Cloud Manager UI는 현재 배포 중인 도메인 이름으로 사용 중인 경우 일시적으로 SSL 인증서를 선택할 수 없는 사용자에게 알립니다.

* 경우에 따라 내부 문제로 인해 환경 삭제가 중단될 수 있습니다.

* 일부 파이프라인 오류가 파이프라인 오류로 잘못 보고되었습니다.

## AEM을 Cloud Service 기반 {#aem-as-a-cloud-service-foundation}

### 새로운 기능 {#what-is-new-foundation}

* 서버 간 인증된 API 호출 - 외부 애플리케이션과 AEM 간에 인증된 서버 간 API 호출을 Cloud Service 환경으로 만드는 적절한 액세스 토큰을 생성합니다. [설명서](/help/implementing/developing/introduction/generating-access-tokens-for-server-side-apis.md)를 읽거나 [tutorial](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/authentication/overview.html?lang=en#authentication)을 참조하여 자세한 내용을 알아보십시오.

### SDK 빌드 분석기 {#sdk-build-analyzers}

Cloud Service SDK Build Analyzer Maven 플러그인으로서 AEM은 누락된 종속성을 포함하여 주요 프로젝트에서 문제를 감지합니다. Cloud Manager를 사용하여 클라우드 환경에 배포하기 전에 개발자는 로컬 개발 중에 문제를 발견할 수 있습니다.

이번 릴리스에 2개의 새로운 분석기가 추가되었습니다.

* 포인터 분석기
* bundle-nativecode

자세한 내용은 설명서 [여기](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/build-analyzer-maven-plugin.html?lang=en#developing)를 참조하십시오.

## 컨텐츠 전송 도구 {#content-transfer-tool}

### 릴리스 날짜 {#release-date-ctt}

내용 전송 도구 v1.2.4 릴리스 날짜는 2021년 2월 10일입니다.

### 버그 수정 {#bug-fixes-ctt}

* 여러 사용자를 매핑할 때 일부 사용자의 IMS ID가 잘못 매핑되었습니다. 이 문제가 수정되었습니다.

### 릴리스 날짜 {#release-date-ctt-feb}

내용 전송 도구 v1.2.2 릴리스 날짜는 2021년 2월 1일입니다.

### [!DNL Content Transfer Tool] {#what-is-new-ctt}의 새로운 기능

* 컨텐츠 전송 도구 - 사용자 매핑 도구에 추가된 새 기능 및 UI. 이 기능은 컨텐츠 마이그레이션 작업의 일부로 기존 사용자 및 그룹을 Adobe Identity Management 시스템 ID에 자동으로 매핑합니다. 자세한 내용은 [사용자 매핑 도구 사용](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-user-mapping-tool.html)을 참조하십시오.
* 이제 콘텐츠 전송 도구가 하위 항목을 포함하여 마이그레이션 세트에서 참조하는 모든 그룹 및 사용자를 마이그레이션합니다.
* 사용자는 마이그레이션 세트를 만들 때 `/etc` 아래에서 특정 경로를 선택할 수 있습니다.

## 우수 사례 분석기 {#best-practices-analyzer}

### 릴리스 날짜 {#release-date-bpa}

우수 사례 분석기 v2.1.0 릴리스 날짜는 2021년 2월 11일입니다.

### [!DNL Best-Practices-Analyzer] {#what-is-new-bpa}의 새로운 기능

* AEM Forms 및 AEM Forms 구현 기능을 감지하고 Cloud Service으로 AEM Forms으로 마이그레이션하는 것과 관련된 영역을 나타낼 수 있습니다.
* 사용자 지정 구성 요소 및 템플릿의 사용 및 카운트를 감지하고 보고할 수 있습니다.
* 사용된 노드 저장소 및 데이터 저장소 유형을 검색하는 기능입니다.
* Dynamic Media 사용 감지 기능
* 사용된 Java 버전을 검색하는 기능







