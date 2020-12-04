---
title: 'Cloud Service의 현재 릴리스 노트입니다. [!DNL Adobe Experience Manager] '
description: 'Cloud Service의 현재 릴리스 노트입니다. [!DNL Adobe Experience Manager] '
translation-type: tm+mt
source-git-commit: f37bcfda2b4e4c036ce5c7ddd2dd1aa131f2a6a5
workflow-type: tm+mt
source-wordcount: '1269'
ht-degree: 3%

---


# [!DNL Adobe Experience Manager] as a Cloud Service 릴리스 노트 {#release-notes}

다음 섹션에서는 Cloud Service으로 [!DNL Experience Manager]에 대한 일반 릴리스 노트에 대해 간략하게 설명합니다.

## 릴리스 날짜 {#release-date}

Cloud Service 2020.11.0으로 [!DNL Adobe Experience Manager]에 대한 릴리스 날짜는 2020년 12월 2일입니다.
다음 릴리스(2020.12.0)는 2020년 12월 17일에 제공됩니다

## [!DNL Adobe Experience Manager Sites] cloud service  {#sites}

### [!DNL Sites] {#what-is-new-sites}의 새로운 기능

* **[계층 관리](/help/sites-cloud/authoring/launches/managing-pages.md)  및  [향후 타임워프](/help/sites-cloud/authoring/launches/preview.md)** 시작:론치 내에서 페이지를 추가/제거하기 위한 새로운 UI와 타임워프가 있는 검색 사이트는 론치에서 향후 상태를 보여줍니다.

* **[확장 컨텐츠 조각 모델 및 편집기](/help/assets/content-fragments/content-fragments-models.md)**:다양한 데이터 유형에 대한 입력 유효성 검사, 새로운 양식 시각화 기능이 추가된 열거형 데이터 유형, 자산 UI에서 컨텐츠 조각 모델 이름이 표시되고 검색 가능해집니다.

* **롤아웃에 사용할 수 있는 Live Copy 페이지 정렬**:이름,  [!UICONTROL 마지막 수정 날짜] 및  [!UICONTROL 마지막 롤아웃 날짜 속성을 사용하여 롤아웃할 수 있는 Live Copy 페이지를 정렬하는 새로운 ]옵션  입니다. 페이지에 대한 [!UICONTROL 마지막 롤아웃 날짜]는 새 속성이 도입되었습니다.

## [!DNL Adobe Experience Manager Assets] cloud service  {#assets}

### [!DNL Assets] 및 [!DNL Dynamic Media] {#what-is-new-assets}의 새로운 기능

* **일괄 자산 처리**:고객에게 자산 마이크로 서비스를 비롯한 Cloud Service 아키텍처로 활용하는 확장 가능한 클라우드 기반 통합 서비스 [!DNL Experience Manager] 를 제공합니다. 주요 활용 사례로는 모니터링, 보고 및 예약과 함께 규모에 맞게 수집하며 일반적인 클라우드 업로드 툴을 사용하여 자산을 클라우드 데이터 스토어로 처음 전송할 수 있습니다. [자산 벌크 인제터 도구](/help/assets/add-assets.md#asset-bulk-ingestor)를 참조하십시오.
이 도구는 시스템 관리자, 컨설턴트 또는 구현 파트너 개인 사용자를 위한 것입니다. 이 기능을 사용하면 대규모 섭취 작업을 수행할 수 있으며 초기 섭취 또는 가끔 큰 섭취 작업 중에 사용하는 것이 좋습니다. 더 작은 통합 작업의 경우 자산 사용자 인터페이스](/help/assets/add-assets.md#upload-assets)을 사용하여 [[!DNL Experience Manager] 데스크톱 앱](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/introduction.html?lang=en) 또는 [업로드를 사용하십시오.

   ![벌크 가져오기 구성](/help/assets/assets/bulk-import-config-low-res.png)

* 사용자는 이제 카드 및 열 보기에서 디지털 자산을 정렬할 수 있습니다.

   ![자산 정렬](/help/assets/assets/asset-sort-options.png)

* 이 릴리스의 [!DNL Experience Manager Assets]에 있는 액세스 가능성에 대해 다음 개선 사항이 수행됩니다. 자세한 내용은  [!DNL Assets]](/help/assets/accessibility.md)의 [액세스 가능성 기능을 참조하십시오.

   * 키보드를 사용하여 타임라인을 탐색할 때 Esc 키는 초점을 그대로 유지하면서 모두 표시 옵션을 축소할 수 있습니다.
   * 키보드 탭 키를 사용하여 탐색할 때 추가된 태그에서 마지막 태그를 제거한 후 태그 필드가 포커스를 유지합니다.
   * [!DNL Experience Manager] 이제 구성 요소에는 화면 판독기에서 사용할 이름, 역할 및 값에 대한 적절한 정보가 포함됩니다.
   * 유형/크기 콤보 상자, 링크 콤보 상자, 언어 콤보 상자 또는 텍스트 편집 상자를 삭제하면 키보드 포커스가 다음 또는 이전 사용자 인터페이스 요소 또는 보다 관련 있는 사용자 인터페이스 요소로 돌아갑니다.
   * 포인터를 옵션 위에 놓으면 선택 및 다운로드와 같은 팁이 나타납니다. 화면 돋보기를 사용하는 사용자는 이러한 팁 때문에 파일 축소판을 볼 수 없습니다. 이제 `Escape` 키를 사용하여 옵션을 제거한 후 포커스를 유지할 수 있습니다.
   * 페이지에 있는 그리드에서 격자 셀을 선택하면 포커스가 화면에 나타나는 작업 막대로 이동합니다.
   * [!DNL Experience Manager] 홈 페이지의 모든 솔루션에 대한 링크에 대한 시각적 단서(밑줄 및 V자 모양 아이콘)가 표시되므로 시각적인 사용자는 일반 텍스트와 링크를 차별화할 수 있습니다.

* **Dynamic Media의 일괄 세트 사전 설정**:자산 파일을 개별 또는 일괄 처리를 사용하여 폴더에 업로드할 때 이미지 세트 또는 스핀 세트에 있는 여러 자산의 생성 및 구성을 자동화할 수 있습니다.

   [배치 집합 사전 설정 정보](/help/assets/dynamic-media/batch-set-presets-dm.md)를 참조하십시오.

* 이제 [!DNL Dynamic Media]에서 다음 액세서빌러티 개선 사항을 사용할 수 있습니다.

   * 화면 판독기(JAWS, 내레이터)는 [임베드 크기] 메뉴 옵션에서 메뉴 항목의 이름, 역할 및 상태를 나레이션합니다.
   * 사용자는 `Tab` 키를 사용하여 이메일 링크 대화 상자를 탐색할 수 있습니다.
   * 향상된 화면 판독기를 통해 비디오 인코딩 프로필을 만드는 워크플로우는 사용자에게 더 친숙합니다.
   * `Tab` 키를 사용하여 탐색할 때 워크플로우의 적절한 사용자 인터페이스 요소로 포커스가 이동하여 대화형 비디오를 만듭니다.
   * 웹 표준을 준수하도록 게시 페이지, 자산 편집 페이지, 스마트 자르기 편집 페이지 및 이미지 세트 편집기 페이지가 개선되었습니다. 이제 AT(Assistive Technology) 사용자는 이러한 페이지를 손쉽게 탐색하고 이미지를 자르는 등의 작업을 수행할 수 있습니다.
   * 사용자가 키보드를 사용하여 탐색할 수 있도록 뷰어가 개선되었습니다.
   * 키보드 및 화면 판독기 사용자는 자르기 기능을 사용할 수 있습니다.
   * 키보드 사용자는 핫스팟을 보다 효율적으로 관리할 수 있습니다.

    [!DNL Dynamic Media]](/help/assets/dynamic-media/accessibility-dm.md)의 [접근성을 참조하십시오.

## Adobe Experience Manager 커머스를 Cloud Service {#cloud-services-commerce}

### 새로운 기능 {#what-is-new-commerce}

* 최신 CIF 코어 구성 요소 버전 v1.5.0을 포함하는 CIF Venia 참조 사이트 - 2020.11.05가 출시되었습니다. 자세한 내용은 [CIF Venia 참조 사이트](https://github.com/adobe/aem-cif-guides-venia/releases/tag/venia-2020.10.27)를 참조하십시오.

* CIF 코어 구성 요소 v1.5.0이 출시되었습니다. 자세한 내용은 [CIF 핵심 구성 요소](https://github.com/adobe/aem-core-cif-components/releases/tag/core-cif-components-reactor-1.5.0)를 참조하십시오.

### 버그 수정 {#bug-fixes-commerce}

* GraphQL 클라이언트 구성은 Sling CA 구성에 직접 구성이 지정되지 않았지만 상위 구성 중 하나에서 올바르게 읽히지 않았습니다. 이 문제가 해결되었습니다.

## Cloud Manager {#cloud-manager}

### 릴리스 날짜 {#release-date-cm}

2020.11.0 Cloud Service으로 AEM의 Cloud Manager에 대한 릴리스 날짜는 2020년 11월 12일입니다.

### [!DNL Cloud Manager] {#what-is-new-cm}의 새로운 기능

* 이제 **환경** 카드 및 **환경** 요약 페이지의 환경 메뉴 옵션에서 사용자가 새 메뉴 옵션 **로컬 로그인**을 사용할 수 있습니다.
자세한 내용은 [환경 관리](/help/implementing/cloud-manager/manage-environments.md##login-locally)를 참조하십시오.

* Cloud Manager의 **학습** 탭이 UI의 새 이미지로 새로 고침되었습니다.

### 버그 수정 {#bug-fixes-cloud-manager}

* 빌드 실행 전에 수행된 종속성 로딩은 Maven 플러그인을 다운로드해야 합니다.
* 이제 언어를 선택하는 Cloud Manager 바닥글의 링크가 올바른 위치로 이동합니다.
* 경우에 따라 코드 검색 중 SonarQube 프로세스가 시작되지 않습니다. 이제 자동으로 감지되고 다시 시작하려고 합니다.
* 모든 기존 프로덕션 파이프라인은 경험 감사 단계를 통해 자동으로 활성화됩니다.

## Adobe Experience Manager as a Cloud Service 기반 {#cloud-service-foundation}

### 워크플로우 {#workflows}

* 워크플로우 제목, 워크플로우 모델, 상태, 개시자, 페이로드 경로 및 시작 날짜를 기반으로 워크플로우 인스턴스 검색에 대한 지원이 추가되었습니다. [검색 워크플로 인스턴스](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/sites/administering/workflows-administering.html)를 참조하십시오.

### 게시 계층 사용자 데이터 동기화 {#user-sync}

* 프로필 속성 및 그룹 멤버십을 비롯한 사용자 데이터는 게시 계층으로 유지될 수 있습니다. [등록, 로그인 및 사용자 프로필 설명서](/help/sites-cloud/authoring/personalization/user-and-group-sync-for-publish-tier.md)에서 이 기능에 대한 자세한 내용을 살펴보십시오.

### SDK 빌드 분석기 {#analyzers}

Cloud Service SDK Build Analyzer Maven 플러그인으로 AEM은 누락된 종속성을 포함하여, 대규모 프로젝트의 문제를 감지합니다. Cloud Manager를 사용하여 클라우드 환경에 배포하기 전에 개발자는 로컬 개발 중에 문제를 발견할 수 있습니다. 자세한 내용은 [여기](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/build-analyzer-maven-plugin.html?lang=en#developing) 및 [여기](https://experienceleague.corp.adobe.com/docs/experience-manager-cloud-service/implementing/developing/aem-as-a-cloud-service-sdk.html?lang=en#building-for-the-sdk) 설명서를 참조하십시오.

### 기타 {#others-foundation}

새 [&quot;httpd -t&quot; 구문](/help/implementing/dispatcher/disp-overview.md#local-validation) Cloud Manager 빌드 중에 실행된 apache 및 dispatcher 구성을 확인합니다. 이 구성 요소는 AEM을 Cloud Service SDK의 Dispatcher 도구로 사용하여 실행할 수도 있습니다.

## 컨텐츠 전송 도구 {#content-transfer-tool}

이 섹션에 따라 새로운 기능과 [컨텐츠 전송 도구](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/overview-content-transfer-tool.html) 릴리스 v1.1.12에 대한 업데이트에 대해 알아보십시오.

### 새로운 기능 {#what-is-new-ctt}

* 로그에 대한 사용자 경험이 개선되었습니다. 추출 및 통합 로그에 타임스탬프가 추가되었습니다. 로그가 비어 있는지를 나타내는 메시지가 추가되었습니다.

### 버그 수정 {#ctt-bug-fixes}

* 마이그레이션 세트에 부분적으로 유사한 파일 이름이 있는 경로가 포함된 경우 컨텐츠 전송 도구가 콘텐트 파일을 건너뛰었습니다. 이 문제가 해결되었습니다.

## 우수 사례 분석기 {#best-practices-analyzer}

### 릴리스 날짜 {#release-date-bpa}

우수 사례 분석기의 릴리스 날짜는 2020년 11월 13일입니다.

### [!DNL Best Practices Analyzer] {#what-is-new-bpa}의 새로운 기능

* Cloud Readance Analyzer는 이제 BPA(Best Practices Analyzer)입니다. BPA는 현재 AEM 구현에 대한 모범 사례 평가를 제공하고 기존 AEM 인스턴스에서 AEM으로 Cloud Service으로 전환할 준비를 평가합니다.

* AEM에서 Cloud Service으로 사용하는 경우 문제를 일으킬 수 있는 `java.io.InputStream`의 사용을 감지하기 위해 새로운 탐지기 기능을 추가했습니다.

### 버그 수정 {#bpa-bug-fixes}

* *textfield foundation* 구성 요소와 관련된 양의 원인이 수정되었습니다.
