---
title: ' [!DNL Adobe Experience Manager] as a Cloud Service의 2020.8.0 릴리스 정보입니다.'
description: "[!DNL Adobe Experience Manager] 2020.8.0용 as a Cloud Service 릴리스 노트"
exl-id: 83413130-ae90-4419-bcf7-42fdc740452b
source-git-commit: bc4da79735ffa99f8c66240bfbfd7fcd69d8bc13
workflow-type: tm+mt
source-wordcount: '1046'
ht-degree: 6%

---

# [!DNL Adobe Experience Manager] as a Cloud Service 2020.8.0 릴리스 노트  {#release-notes}

다음 섹션에서는 Experience Manager as a Cloud Service 2020.8.0 일반 릴리스 노트를 간략하게 설명합니다.


## [!DNL Adobe Experience Manager Sites] as a Cloud Service {#sites}

### [!DNL Sites]의 새로운 기능 {#what-is-new-sites}

* 기능 [페이지 및 하위 페이지(페이지 트리)를 이전 버전으로 복원](/help/sites-cloud/authoring/features/page-versions.md#reinstating-versions).

* 기능 [론치 만들기](/help/sites-cloud/authoring/launches/overview.md) AEM [SPA 편집기.](/help/implementing/developing/hybrid/introduction.md)


## [!DNL Adobe Experience Manager Assets] as a Cloud Service {#assets}

### [!DNL Assets]의 새로운 기능 {#what-is-new-assets}

* 비디오 코드 변환 시 이제 자산 마이크로서비스에서 지원됩니다. 의 새 섹션 [!UICONTROL 처리 프로필] 구성을 사용하여 비디오 비트율 및 차원을 설정할 수 있습니다. 출력 형식은 H.264 코덱이 있는 MP4입니다. 자세한 내용은 [비디오 자산 관리](/help/assets/manage-video-assets.md#transcode-video). 더 많은 코드 변환 옵션과 비디오 전달을 위해 [!DNL Dynamic Media] 추가 기능.

* 새로 만들기 [!DNL Experience Manager Assets] 배포 시 이제 스마트 태그 지정 기능이 기본적으로 구성됩니다. 수동으로 을 통합할 필요가 없습니다. [!DNL Adobe Developer Console]. 기존 배포에서 관리자는 이전처럼 스마트 태그 통합을 구성합니다.

* 새로운 [자산 다운로드 경험](/help/assets/download-assets-from-aem.md) 허용,

   * 대규모 다운로드를 위한 비동기 다운로드를 지원하여 대기 시간이 없어집니다.
   * 개발자 확장성을 위한 새로운 모듈식 API

* 자산 마이크로서비스에 대한 메타데이터 추출이 성능이 향상되었습니다. 전체 자산 수집 처리량을 증가시킵니다.

* 처리 프로필을 사용하여 계산 서비스를 사용하여 사용자 지정 메타데이터를 생성합니다. 자세한 내용은 [처리 프로필을 사용한 사용자 지정 메타데이터](/help/assets/manage-metadata.md#metadata-compute-service).

* 관리자가 구성할 수 있는 Brand Portal 사용자를 위한 간단한 다운로드 경험입니다. 자세한 내용은 [경험 다운로드 개요](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/introduction/whats-new.html#download-configurations).

* 이제 Brand Portal에서 기본 및 고화질 PDF 문서 미리 보기를 사용할 수 있습니다. 자세한 내용은 [문서 뷰어 개요](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/introduction/whats-new.html#doc-viewer).

* 이제 CDN(Content Delivery Network) 캐시를 [!DNL Dynamic Media] AEM as a Cloud Service(사용 시와 반대됨) [!DNL Dynamic Media Classic]). 이렇게 하면 몇 시간이 아닌 몇 분 내에 최신 자산을 제공할 수 있습니다. 자세한 내용은 [Dynamic Media을 통해 CDN 캐시 무효화](/help/assets/dynamic-media/invalidate-cdn-cache-dynamic-media.md).

* 향상된 액세스 가능성 지원이 의 사용자 인터페이스 컨트롤, 탐색, 검색 및 검색 경험에 추가되었습니다 [!DNL Assets].

   * 선택 후 Esc 키를 누르면 [!UICONTROL 표현물 추가] 옵션을 선택하면 포커스가 도구 모음으로 돌아갑니다. <!-- via CQ-4293594-->
   * 전자 메일 콤보 상자를 사용할 때 키보드 포커스가 예상대로 작동합니다. <!-- via CQ-4286215 -->
   * 검색 필터 섹션의 아코디언 요소는 표준 확장 가능한 아코더로 해석됩니다. <!-- via CQ-4273103 -->
   * 자산에 태그를 적용할 때 대화 상자에 태그가 트리 요소로 표시됩니다. ARIA 속성은 이제 액세스할 수 있도록 트리 요소에 적절히 적용됩니다. <!-- via CQ-4272964 -->

* [!DNL AEM Desktop app] 이제 2.0.3 릴리스를 사용할 수 있습니다. 과의 호환성을 향상합니다 [!DNL Experience Manager] 6.5.5 서비스 팩 및 업데이트된 클라이언트 OS 호환성 목록이 있습니다. [!DNL Windows] 7 및 [!DNL macOS] 10.14 이전 버전은 지원되지 않습니다.

### [!DNL Assets]의 수정된 버그 {#bugs-fixed}

* 연결 및 연결 해제 옵션은 처음 클릭했을 때 응답하지 않습니다. (CQ-4299022)
* 자산을 다운로드할 때 이메일을 통해 수신 옵션을 선택하면 이메일이 전송되지 않습니다. (CQ-4299146)

## Adobe Experience Manager Commerce as a Cloud Service {#cloud-services-commerce}

### 새로운 기능 {#what-is-new-commerce}

* 이제 제품 콘솔 기능을 사용할 수 있습니다. 이를 통해 AEM의 마케터/작성자는 상거래 백엔드에 저장된 카테고리와 제품을 보고 탐색할 수 있습니다. 제품 콘솔에서 카테고리 및 제품에 대한 속성을 지원합니다.

* 제품 및 카테고리 선택기 기능이 향상되어 마케터는 SKU를 통해 제품을 선택하거나 카테고리 ID를 통해 카테고리를 선택할 수 있습니다.

## Cloud Manager {#cloud-manager}

### 릴리스 날짜 {#release-date-cm}

에 대한 릴리스 날짜 [!UICONTROL Cloud Manager] 버전 2020.8.0은 2020년 8월 6일입니다.

### 새로운 기능 {#what-is-new-cloud-manager}

* 컨텐츠 감사 는 Cloud Manager Sites 프로덕션 파이프라인에서 사용할 수 있는 기능입니다. 이제 사이트 가 있는 프로그램에 대한 프로덕션 파이프라인 구성에 이름이 인 세 번째 탭이 포함됩니다. **컨텐츠 감사**. 프로덕션 파이프라인이 실행될 때마다 사용자 정의 기능 테스트 후 새로운 컨텐츠 감사 단계가 파이프라인에 포함되며, 이 테스트에서는 성능, SEO(검색 엔진 최적화), 접근성, 모범 사례 및 PWA(점진적 웹 앱)을 비롯한 다양한 차원에 대해 사이트를 평가하게 됩니다.


   >[!NOTE]
   >이후 콘텐츠 감사 이름이 Experience Auditor로 변경되었습니다.

   을(를) 참조하십시오. [경험 감사 테스트](/help/implementing/cloud-manager/experience-audit-testing.md) 자세한 내용

* 이제 자산 프로그램에서 새로 만든 환경이 스마트 컨텐츠 서비스로 자동 구성됩니다.

* Cloud Manager에서 최대 절전 모드 환경을 해제할 수 있습니다 **개요** 페이지.

* Google Lighthouse에서 제공하는 페이지에서 경험 확인을 수행할 수 있습니다. Cloud Manager 파이프라인의 일부로서 경험 KPI에 대해 최대 25페이지의 유효성 검사와 확인을 수행할 수 있으며 점수는 Cloud Manager UI에 표시됩니다.

### 버그 수정 {#bug-fixes-cm}

* 일부 불필요하고 원치 않는 SonarQube 플러그인이 코드 품질 스캔의 일부로 실행되었습니다.

* 파이프라인 실행 페이지에서 분기 이름의 형식이 잘못되었습니다.

* 경우에 따라 완료된 파이프라인 실행이 완료된 것으로 기록되지 않아 파이프라인의 새로운 실행이 방지됩니다.

* 파이프라인 실행은 가끔 *정지* 내부 통신 문제로 인해

* 새 조직을 프로비저닝할 때 시스템 관리자 이외의 관리자 역할을 가진 일부 사용자에게 Cloud Manager에 대한 액세스 권한이 잘못 부여되었습니다.

* 특정 조건에서 인덱스 업데이트 작업이 여러 번 동시에 시작되어 배포 오류가 발생합니다.

* 프로그램 카드의 도구 설명이 일관되게 올바르지 않습니다.

* 사용자 인터페이스가 삭제되는 동안 환경에서 작업을 시도할 수 있도록 잘못 허용되었습니다.

* Cloud Manager의 색상이 일치하지 않습니다 **개요** 페이지.

### 알려진 문제 {#known-issues-cm}

* 잘못된 페이지가 포함되어 컨텐츠 감사 평균 점수가 최저 점수보다 낮아집니다.

* 컨텐츠 감사 탭에 게시 도메인 대신 작성자 도메인을 사용하는 기본 URL이 잘못 표시됩니다.

* 컨텐츠 감사 단계를 활성화하려면 파이프라인을 편집하고 선택적으로 페이지를 추가해야 합니다. 페이지가 추가되지 않으면 홈 페이지가 감사됩니다.

## 콘텐츠 전송 도구 {#content-transfer-tool}

이 섹션을 통해 컨텐츠 전송 도구 릴리스 v1.0.4에 대한 새로운 기능 및 업데이트를 알아보십시오.

### 새로운 기능 {#what-is-new-ctt}

* 이제 컨텐츠 전송 도구가 공유 S3 DataStore를 지원합니다.

### 버그 수정 {#ctt-bug-fixes}

* 작업이 완료되는 도구에 추가된 시간 초과입니다.

* 로그에 오류가 표시되어도 이전 버전 UI에서 성공적으로 추출되는 경우가 있습니다.

## 코드 리팩터링 도구 {#code-refactoring-tools}

이 섹션을 통해 새로운 기능 및 코드 리팩터링 도구에 대한 업데이트를 알아보십시오.

### 새로운 기능 {#what-is-new-refactoring}

* 개발자가 한 곳에서 코드 리팩토링 툴을 호출하고 실행할 수 있도록 코드 리팩토링 툴을 통합할 수 있는 AIO-CLI 플러그인이 출시되었습니다. 을(를) 참조하십시오. [Git 리소스: aio-cli-plugin-aem-cloud-service-migration](https://github.com/adobe/aio-cli-plugin-aem-cloud-service-migration) 자세한 내용

* AEM Dispatcher Converter 는 온-프레미스 및 Adobe Managed Services 디스패처 구성을 AEM as a Cloud Service 호환 디스패처 구성으로 변환하는 기능을 지원합니다. 을(를) 참조하십시오. [Git 리소스: AEM Cloud Service Dispatcher 변환기](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/dispatcher-converter) 자세한 내용

* AEM Dispatcher 변환기가 다시 작성됨 ` node.js ` 및 AIO-CLI 플러그인과 통합
