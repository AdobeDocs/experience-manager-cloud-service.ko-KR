---
title: ' [!DNL Adobe Experience Manager] as a Cloud Service의 2020.8.0 릴리스 정보입니다.'
description: "[!DNL Adobe Experience Manager] 2020.8.0용 as a Cloud Service 릴리스 노트"
exl-id: 83413130-ae90-4419-bcf7-42fdc740452b
source-git-commit: 5ad33f0173afd68d8868b088ff5e20fc9f58ad5a
workflow-type: tm+mt
source-wordcount: '1038'
ht-degree: 34%

---

# [!DNL Adobe Experience Manager] as a Cloud Service 2020.8.0 릴리스 노트  {#release-notes}

다음 섹션에서는 Experience Manager as a Cloud Service 2020.8.0 일반 릴리스 노트를 간략하게 설명합니다.


## [!DNL Adobe Experience Manager Sites] as a Cloud Service {#sites}

### [!DNL Sites]의 새로운 기능 {#what-is-new-sites}

* 다음에 대한 기능: [페이지 및 하위 페이지(페이지 트리)를 이전 버전으로 복원](/help/sites-cloud/authoring/features/page-versions.md#reinstating-versions).

* 다음에 대한 기능: [론치 만들기](/help/sites-cloud/authoring/launches/overview.md) AEM [SPA 편집기](/help/implementing/developing/hybrid/introduction.md).


## [!DNL Adobe Experience Manager Assets] as a Cloud Service {#assets}

### [!DNL Assets]의 새로운 기능 {#what-is-new-assets}

* 이제 비디오 코드 변환 시 자산 마이크로서비스가 지원됩니다. 의 새 섹션 [!UICONTROL 처리 프로필] 구성을 통해 비디오 비트 전송률 및 차원을 설정할 수 있습니다. 출력 형식은 H.264 코덱이 있는 MP4입니다. 자세한 내용은 [비디오 자산 관리](/help/assets/manage-video-assets.md#transcode-video). 더 많은 코드 변환 옵션과 비디오 전달을 위해 다음을 사용합니다. [!DNL Dynamic Media] 추가 기능.

* 새로 만들기 [!DNL Experience Manager Assets] 배포에서는 이제 스마트 태그 지정 기능이 기본적으로 구성됩니다. 과 수동으로 통합할 필요 없음 [!DNL Adobe Developer Console]. 기존 배포에서 관리자는 이전과 같이 스마트 태그 통합을 구성합니다.

* 새 항목 [에셋 다운로드 경험](/help/assets/download-assets-from-aem.md) 허용,

   * 대규모 다운로드를 위한 비동기 다운로드를 지원하므로 사용자가 기다리지 않아도 됩니다.
   * 개발자 확장성을 위한 새로운 모듈식 API.

* 에셋 마이크로서비스에 대한 메타데이터 추출의 성능이 향상되었습니다. 전체 에셋 수집 처리량을 증가시킵니다.

* 처리 프로필을 사용하여 계산 서비스를 사용하여 사용자 지정 메타데이터를 생성합니다. 다음을 참조하십시오 [처리 프로필을 사용한 사용자 지정 메타데이터](/help/assets/manage-metadata.md#metadata-compute-service).

* 관리자가 구성할 수 있는 Brand Portal 사용자를 위한 간단한 다운로드 경험입니다. 다음을 참조하십시오 [다운로드 경험 개요](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/introduction/whats-new.html#download-configurations).

* 이제 Brand Portal에서 기본 및 고화질 PDF 문서 미리 보기를 사용할 수 있습니다. 다음을 참조하십시오 [문서 뷰어 개요](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/introduction/whats-new.html#doc-viewer).

* 이제 CDN(Content Delivery Network) 캐시에서 직접 무효화할 수 있습니다 [!DNL Dynamic Media] AEM as a Cloud Service에서(를 사용하는 것과 반대) [!DNL Dynamic Media Classic]). 이렇게 하면 몇 시간이 아닌 몇 분 내에 최신 에셋을 제공할 수 있습니다. 다음을 참조하십시오 [Dynamic Media을 통해 CDN 캐시 무효화](/help/assets/dynamic-media/invalidate-cdn-cache-dynamic-media.md).

* 향상된 액세스 가능성 지원이 의 사용자 인터페이스 제어, 탐색, 검색 및 검색 경험에 추가되었습니다 [!DNL Assets].

   * 을 선택한 후 Esc 키를 누르면 [!UICONTROL 렌디션 추가] 옵션을 선택하면 포커스가 도구 모음으로 돌아갑니다. <!-- via CQ-4293594-->
   * 키보드 포커스는 이메일 콤보 상자를 사용할 때 예상대로 작동합니다. <!-- via CQ-4286215 -->
   * 검색 필터 섹션의 아코디언 요소는 확장 가능한 표준 아코디언으로 해석됩니다. <!-- via CQ-4273103 -->
   * 자산에 태그를 적용하면 대화 상자에 태그가 트리 요소로 표시됩니다. 이제 액세스할 수 있도록 ARIA 속성이 트리 요소에 적절하게 적용됩니다. <!-- via CQ-4272964 -->

* [!DNL AEM Desktop app] 이제 2.0.3 릴리스를 사용할 수 있습니다. 와의 호환성을 향상합니다 [!DNL Experience Manager] 6.5.5 서비스 팩에 업데이트된 클라이언트 OS 호환성 목록이 있습니다. [!DNL Windows] 7 및 [!DNL macOS] 10.14 이전 버전은 지원되지 않습니다.

### [!DNL Assets]의 수정된 버그 {#bugs-fixed}

* 연결 및 연결 해제 옵션을 처음 클릭하면 응답하지 않습니다. (CQ-4299022)
* 에셋을 다운로드할 때 이메일을 통해 에셋을 수신하는 옵션을 선택하면 이메일이 전송되지 않습니다. (CQ-4299146)

## Adobe Experience Manager Commerce as a Cloud Service {#cloud-services-commerce}

### 새로운 기능 {#what-is-new-commerce}

* 이제 제품 콘솔 기능을 사용할 수 있습니다. 이를 통해 AEM의 마케터/작성자는 상거래 백엔드에 저장된 카테고리와 제품을 보고 탐색할 수 있습니다. 제품 콘솔에서 카테고리 및 제품에 대한 속성을 지원합니다.

* 제품 및 카테고리 선택기 기능이 향상되어 마케터는 SKU를 통해 제품을 선택하거나 카테고리 ID를 통해 카테고리를 선택할 수 있습니다.

## Cloud Manager {#cloud-manager}

### 릴리스 날짜 {#release-date-cm}

의 릴리스 날짜 [!UICONTROL Cloud Manager] 버전 2020.8.0은 2020년 8월 6일입니다.

### 새로운 기능 {#what-is-new-cloud-manager}

* 콘텐츠 감사는 Cloud Manager Sites 프로덕션 파이프라인에서 활성화된 기능입니다. 이제 Sites가 있는 프로그램의 프로덕션 파이프라인 구성에 **콘텐츠 감사**&#x200B;라는 세 번째 탭이 포함됩니다. 프로덕션 파이프라인이 실행될 때마다 성능, SEO(검색 엔진 최적화), 접근성, 모범 사례 및 PWA(점진적 웹 앱)을 포함한 여러 차원에 대해 사이트를 평가하는 사용자 정의 기능 테스트 후 새로운 콘텐츠 감사 단계가 파이프라인에 포함됩니다.


  >[!NOTE]
  >이후 콘텐츠 감사는 경험 감사로 이름이 변경되었습니다.

  자세한 내용은 [경험 감사 테스트](/help/implementing/cloud-manager/experience-audit-testing.md)를 참조하십시오.

* 이제 Assets 프로그램에서 새로 만든 환경이 스마트 컨텐츠 서비스로 자동 구성됩니다.

* 최대 절전 모드 환경은 Cloud Manager의 **개요** 페이지에서 최대 절전 모드를 해제할 수 있습니다.

* Google Lighthouse에서 제공하는 페이지에서 경험 검사를 수행할 수 있습니다. Cloud Manager 파이프라인의 일부로 경험 KPI에 대해 최대 25페이지를 확인하고 검증할 수 있으며 점수는 Cloud Manager UI에 표시됩니다.

### 버그 수정 {#bug-fixes-cm}

* 코드 품질 스캔 중 일부 불필요하고 원하지 않는 SonarQube 플러그인이 실행되고 있었습니다.

* 파이프라인 실행 페이지에서 분기 이름의 형식이 잘못되었습니다.

* 경우에 따라 완료된 파이프라인 실행이 완료된 것으로 정상적으로 기록되지 않아 파이프라인의 새로운 실행이 방지되었습니다.

* 내부 통신 문제로 인해 파이프라인 실행이 가끔 *중단*&#x200B;되었습니다.

* 새 조직을 프로비저닝할 때 시스템 관리자가 아닌 관리 역할을 가진 일부 사용자에게 Cloud Manager에 대한 액세스 권한이 잘못 부여되었습니다.

* 특정 조건에서 인덱스 업데이트 작업이 병렬로 여러 번 시작되어 배포가 실패했습니다.

* 프로그램 카드의 툴팁이 일관되게 정확하지 않았습니다.

* 사용자 인터페이스가 삭제되는 동안 환경에서 작업을 시도할 수 있도록 잘못 허용되었습니다.

* Cloud Manager의 **개요** 페이지에 색상이 일치하지 않는 부분이 있었습니다.

### 알려진 문제 {#known-issues-cm}

* 콘텐츠 감사 평균 점수를 원래보다 낮게 표시하는 잘못된 페이지가 포함됩니다.

* 콘텐츠 감사 탭에 게시 도메인 대신 작성자 도메인을 사용하는 기본 URL이 잘못 표시됩니다.

* 콘텐츠 감사 단계를 활성화하려면 사용자가 파이프라인을 편집하고 필요한 경우 페이지를 추가해야 합니다. 페이지가 추가되지 않으면 홈 페이지가 감사됩니다.

## 콘텐츠 전송 도구 {#content-transfer-tool}

이 섹션을 통해 컨텐츠 전송 도구 릴리스 v1.0.4에 대한 새로운 기능 및 업데이트를 알아보십시오.

### 새로운 기능 {#what-is-new-ctt}

* 컨텐츠 전송 도구는 이제 공유 S3 데이터 저장소를 지원합니다.

### 버그 수정 {#ctt-bug-fixes}

* 도구에서 작업을 완료하는 데 추가 시간 초과가 추가되었습니다.

* 이전 버전 UI는 로그에 오류가 표시되었지만 성공한 추출이 표시되는 경우가 있습니다.

## 코드 리팩터링 도구 {#code-refactoring-tools}

코드 리팩터링 도구의 새로운 기능과 업데이트에 대해 알려면 이 섹션을 따르십시오.

### 새로운 기능 {#what-is-new-refactoring}

* 개발자가 한 곳에서 코드 리팩터링 도구를 호출하고 실행할 수 있도록 코드 리팩터링 도구를 통합하기 위해 AIO-CLI 플러그인이 출시되었습니다. 다음을 참조하십시오 [Git 리소스: aio-cli-plugin-aem-cloud-service-migration](https://github.com/adobe/aio-cli-plugin-aem-cloud-service-migration) 을 참조하십시오.

* AEM Dispatcher Converter 는 온-프레미스 및 Adobe Managed Services AEM Dispatcher 구성을 as a Cloud Service 호환 Dispatcher 구성으로 변환하는 기능을 지원합니다. 다음을 참조하십시오 [Git 리소스: AEM Cloud Service Dispatcher 변환기](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/dispatcher-converter) 을 참조하십시오.

* AEM Dispatcher 변환기가 다시 작성됨 ` node.js ` AIO-CLI 플러그인과 통합됩니다.
