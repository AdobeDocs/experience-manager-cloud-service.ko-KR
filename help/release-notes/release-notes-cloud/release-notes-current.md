---
title: 클라우드 서비스로서의  [!DNL Adobe Experience Manager]  2020.8.0 릴리스의 릴리스 노트
description: 클라우드 서비스로서의 [!DNL Adobe Experience Manager] 2020.8.0 릴리스 노트
translation-type: tm+mt
source-git-commit: 561345f58ce8e448176507e3bba114324dc18256
workflow-type: tm+mt
source-wordcount: '1058'
ht-degree: 6%

---


# 클라우드 서비스 2020.8.0으로서의 [!DNL Adobe Experience Manager] 릴리스 노트 {#release-notes}

다음 섹션에서는 클라우드 서비스 2020.8.0으로서의 Experience Manager 일반 릴리스 노트를 간략하게 설명합니다.

## 릴리스 날짜 {#release-date}

The release date for [!DNL Experience Manager] as a Cloud Service 2020.8.0 is August 27, 2020.

## [!DNL Adobe Experience Manager Sites] cloud service {#sites}

### What is new in [!DNL Sites] {#what-is-new-sites}

* 페이지 및 하위 페이지(페이지 트리)를 이전 버전으로 [복원하는 기능](/help/sites-cloud/authoring/features/page-versions.md#reinstating-versions).

* AEM SPA Editor에서 론치를 만들 수 있습니다.

## [!DNL Adobe Experience Manager Assets] cloud service {#assets}

### What is new in [!DNL Assets] {#what-is-new-assets}

* 비디오 트랜스코딩은 이제 비디오 비트 전송률 및 크기 구성을 지원하는 [!UICONTROL 처리 프로필] 화면의 새로운 비디오 섹션에서 에셋 마이크로서비스에서 지원됩니다(출력 형식은 H.264 코덱이 있는 MP4). 자세한 내용은 비디오 자산 [관리를 참조하십시오](/help/assets/manage-video-assets.md#transcode-video). 더 많은 트랜스코딩 옵션과 비디오 전달 [!DNL Dynamic Media] 추가 기능을 사용할 수 있습니다.

* 새 [!DNL Experience Manager Assets] 배포에서는 스마트 태그 지정 기능이 기본적으로 구성됩니다. 수동으로 통합할 필요가 없습니다 [!DNL Adobe Developer Console]. 기존 배포에서 관리자는 스마트 태그 통합을 [전과 같이](/help/assets/smart-tags-configuration.md#aio-integration) 구성합니다.

* 새로운 [에셋 다운로드 환경을 통해](/help/assets/download-assets-from-aem.md) ,

   * 대규모 다운로드에 대한 비동기 다운로드로 사용자가 기다리지 않아도 됩니다.

   * 개발자 확장성을 위한 새로운 모듈식 API

* [!DNL Experience Manager] 에셋 마이크로서비스에 대한 메타데이터 추출 성능이 향상되었습니다. 전체 자산 처리 처리량을 증가시킵니다.

* 계산 서비스를 사용하여 사용자 지정 메타데이터를 생성하려면 처리 프로필을 사용하십시오. 처리 [프로필을 사용하여 사용자 지정 메타데이터 참조](/help/assets/manage-metadata.md#metadata-compute-service)

* 관리자가 구성할 수 있는 브랜드 포털 사용자를 위한 간소화된 다운로드 경험입니다. 경험 [다운로드 개요를 참조하십시오](https://docs.adobe.com/content/help/en/experience-manager-brand-portal/using/introduction/whats-new.html#download-configurations).

* 이제 브랜드 포털에서 기본 및 고품질 PDF 문서 미리 보기를 사용할 수 있습니다. 문서 [뷰어 개요를 참조하십시오](https://docs.adobe.com/content/help/en/experience-manager-brand-portal/using/introduction/whats-new.html#doc-viewer).

* 이제 AEM [!DNL Dynamic Media] 에서 직접 CDN(Content Delivery Network) 캐시를 Cloud Service(사용과 반대로)로 무효화하여 몇 시간 내에 최신 자산이 제공되도록 할 수 [!DNL Dynamic Media Classic]있습니다. 다이내믹 [미디어를 통해 CDN 캐시 무효화를 참조하십시오.](/help/assets/dynamic-media/invalidate-cdn-cache-dynamic-media.md)

* 향상된 액세스 가능성 지원이 의 사용자 인터페이스 컨트롤, 탐색, 검색 및 검색 경험에 추가되었습니다 [!DNL Assets].

   * [변환 추가] 옵션을 선택한 후 Escape 키 [!UICONTROL 를] 누르면 포커스가 도구 모음으로 돌아갑니다. <!-- via CQ-4293594-->
   * 이메일 콤보 상자를 사용하는 경우 키보드 포커스가 예상대로 작동합니다. <!-- via CQ-4286215 -->
   * 검색 필터 섹션의 아코디언 요소는 표준 확장 가능한 아코디언으로 해석됩니다. <!-- via CQ-4273103 -->
   * 태그에 태그를 적용하면 대화 상자에 태그가 트리 요소로 표시됩니다. ARIA 속성은 트리 요소에 적절히 적용되어 이제 액세스할 수 있습니다. <!-- via CQ-4272964 -->

* [!DNL AEM Desktop app] 2.0.3 릴리스가 출시되어 [!DNL AEM] 6.5.5와의 호환성 [!DNL Service Pack] 을 개선하고 클라이언트 OS 호환성 목록을 업데이트( [!DNL Windows] 7 및 [!DNL MacOS] 버전 10.14 이전 제거)합니다.

### 버그 수정 [!DNL Assets] {#bugs-fixed}

* 관계 및 관계 없음 옵션을 처음 클릭할 때 응답하지 않습니다. (CQ-4299022)
* 자산을 다운로드할 때 이메일을 통해 받는 옵션을 선택하면 이메일이 전송되지 않습니다. (CQ-4299146)

## Adobe Experience Manager Commerce as a Cloud Service {#cloud-services-commerce}

### 새로운 기능 {#what-is-new-commerce}

* 이제 제품 콘솔 기능을 사용할 수 있습니다. 이를 통해 AEM의 마케터/작성자는 상거래 백엔드에 저장된 카테고리와 제품을 보고 탐색할 수 있습니다. 제품 콘솔에서 카테고리 및 제품에 대한 속성에 대한 지원도 제공됩니다.

* 제품 및 카테고리 선택 기능이 향상되어 마케터는 SKU를 통해 제품을 선택하거나 카테고리 ID를 통해 카테고리를 선택할 수 있습니다.

## Cloud Manager {#cloud-manager}

### 릴리스 날짜 {#release-date-cm}

The Release Date for [!UICONTROL Cloud Manager] Version 2020.8.0 is August 06, 2020.

### 새로운 기능 {#what-is-new-cloud-manager}

* 콘텐츠 감사는 Cloud Manager Sites 프로덕션 파이프라인에서 활성화된 기능입니다. 이제 사이트가 있는 프로그램에 대한 프로덕션 파이프라인 구성에는 컨텐츠 감사라는 세 번째 탭이 **포함됩니다**. 프로덕션 파이프라인이 실행될 때마다 사용자 정의 기능 테스트 후 새로운 컨텐츠 감사 단계가 파이프라인에 포함됩니다. 사용자 정의 기능 테스트 후에는 성능, SEO(검색 엔진 최적화), 접근성, 우수 사례 및 PWA(점진적 웹 앱)을 비롯한 다양한 차원과 사이트를 평가합니다.

   >[!NOTE]
   >콘텐츠 감사가 경험 감사로 이름이 변경되었습니다.

   자세한 내용은 [경험 감사 테스트를](/help/implementing/cloud-manager/experience-audit-testing.md) 참조하십시오.

* 자산 프로그램에서 새로 만들어진 환경은 이제 스마트 콘텐츠 서비스로 자동 구성됩니다.

* Cloud Manager의 **개요** 페이지에서 최대 절전 모드 해제 환경을 사용할 수 있습니다.

* Google Lighthouse에서 제공하는 페이지에서 경험 확인을 수행하는 기능 Cloud Manager 파이프라인의 일부로 경험 KPI에 대해 최대 25페이지의 확인 및 유효성 검사를 수행할 수 있으며 Cloud Manager UI에 점수가 표시됩니다.

### 버그 수정 {#bug-fixes-cm}

* 불필요하고 불필요한 일부 SonarQube 플러그인이 코드 품질 스캐닝의 일부로 실행되었습니다.

* 파이프라인 실행 페이지에서 분기 이름의 형식이 잘못되었습니다.

* 경우에 따라 파이프라인 집행이 완료되었다고 기록되지 않아 파이프라인의 새로운 처형이 방지되는 경우도 있습니다.

* 가끔 내부 통신 문제로 인해 파이프라인 *실행이* 중단될 수 있습니다.

* 새 조직을 프로비저닝할 때 시스템 관리자 이외의 관리자 역할을 가진 일부 사용자에게 클라우드 관리자에 대한 액세스 권한이 잘못 부여되었습니다.

* 특정 조건에서, 업데이트 인덱스 작업이 여러 번 동시에 시작되어 배포 오류가 발생했습니다.

* 프로그램 카드에 대한 도구 설명이 일관되게 올바르지 않습니다.

* 사용자 인터페이스가 삭제되는 동안 환경에서 작업을 시도하도록 잘못 허용되었습니다.

* Cloud Manager의 **개요** 페이지에 색상이 일치하지 않습니다.

### 알려진 문제 {#known-issues-cm}

* 콘텐츠 감사 평균 점수 이하로 유도하는 잘못된 페이지가 포함됩니다.

* 컨텐츠 감사 탭에 게시 도메인 대신 작성자 도메인을 사용하여 기본 URL이 잘못 표시됩니다.

* 컨텐츠 감사 단계를 활성화하려면 파이프라인을 편집하고 선택적으로 페이지를 추가해야 합니다. 페이지가 추가되지 않으면 홈 페이지가 감사됩니다.

## 컨텐츠 전송 도구 {#content-transfer-tool}

컨텐츠 전송 도구 릴리스 v1.0.4의 새로운 기능과 업데이트에 대해 알아보려면 이 섹션을 따르십시오.

### 새로운 기능 {#what-is-new-ctt}

* 이제 콘텐츠 전송 도구가 공유 S3 DataStore를 지원합니다.

### 버그 수정 {#ctt-bug-fixes}

* 추가 시간 초과가 추가 작업에 추가되었습니다.

* 이전 버전 UI는 로그에 오류가 표시되더라도 성공적인 추출을 표시하기도 했습니다.

## 코드 리팩터링 도구 {#code-refactoring-tools}

이 섹션을 따라 새로운 기능 및 코드 리팩토링 도구에 대한 업데이트에 대해 알아보십시오.

### 새로운 기능 {#what-is-new-refactoring}

* 개발자가 한 곳에서 코드 리팩토링 툴을 호출하고 실행할 수 있도록 코드 리팩토링 툴을 통합할 수 있는 AIO-CLI 플러그인이 출시되었습니다. Git 리소스 [를 참조하십시오.자세한 내용은 aio-cli-plugin-aem-cloud-service-migration](https://github.com/adobe/aio-cli-plugin-aem-cloud-service-migration) 을 참조하십시오.

* AEM Dispatcher Converter를 사용하면 온-프레미스 및 Adobe Managed Services Dispatcher 구성을 AEM에서 Cloud Service 호환 Dispatcher 구성으로 변환할 수 있습니다. Git 리소스 [를 참조하십시오.AEM Cloud Service Dispatcher Converter](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/dispatcher-converter) 를 참조하십시오.

* AEM Dispatcher Converter가 다시 작성되어 AIO-CLI 플러그인 ` node.js ` 과 통합되었습니다.
