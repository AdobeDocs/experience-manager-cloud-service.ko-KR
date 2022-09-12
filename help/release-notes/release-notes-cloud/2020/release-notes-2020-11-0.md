---
title: ' [!DNL Adobe Experience Manager] as a Cloud Service의 2020.11.0 릴리스 정보입니다.'
description: "[!DNL Adobe Experience Manager] 2020.11.0용 as a Cloud Service 릴리스 노트"
exl-id: 8066c0fb-c2f5-4625-9448-b0c74ff4e192
source-git-commit: bc4da79735ffa99f8c66240bfbfd7fcd69d8bc13
workflow-type: tm+mt
source-wordcount: '1265'
ht-degree: 10%

---

# [!DNL Adobe Experience Manager] as a Cloud Service 릴리스 노트  {#release-notes}

다음 섹션에서는 다음에 대한 일반 릴리스 노트를 간략하게 설명합니다 [!DNL Experience Manager] as a Cloud Service.

## 릴리스 날짜 {#release-date}

에 대한 릴리스 날짜 [!DNL Adobe Experience Manager] as a Cloud Service은 2020년 12월 2일입니다.
다음 릴리스(2020.12.0)은 2020년 12월 17일에 있습니다

## [!DNL Adobe Experience Manager Sites] as a Cloud Service {#sites}

### [!DNL Sites]의 새로운 기능 {#what-is-new-sites}

* **[계층 관리 시작](/help/sites-cloud/authoring/launches/managing-pages.md) &amp; [향후 타임워프](/help/sites-cloud/authoring/launches/preview.md)**: 론치 내에서 페이지를 추가/제거하는 새 UI와 타임워프를 사용하는 검색 사이트에는 론치의 향후 상태가 표시됩니다.

* **[확장된 컨텐츠 조각 모델 및 편집기](/help/assets/content-fragments/content-fragments-models.md)**: 다양한 데이터 유형에 대한 입력 유효성 검사, 새로운 양식 시각화를 사용한 향상된 열거형 데이터 유형 및 컨텐츠 조각 모델 이름이 Assets UI에서 표시되고 검색할 수 있는 새로운 옵션입니다.

* **롤아웃에 사용할 수 있는 Live Copy 페이지를 정렬합니다.**: 을 사용하여 롤아웃에 사용할 수 있는 Live Copy 페이지를 정렬하는 새 옵션 [!UICONTROL 이름], [!UICONTROL 마지막 수정 날짜], 및 [!UICONTROL 마지막 롤아웃 날짜] 속성을 사용합니다. 다음 [!UICONTROL 마지막 롤아웃 날짜] 페이지의 경우 새로운 속성이 도입되었습니다.

## [!DNL Adobe Experience Manager Assets] as a Cloud Service {#assets}

### 의 새로운 기능 [!DNL Assets] 및 [!DNL Dynamic Media] {#what-is-new-assets}

* **일괄 자산 수집**: 고객에게 다음을 활용하는 확장 가능한 클라우드 기반의 수집 서비스를 제공합니다 [!DNL Experience Manager] 자산 마이크로서비스를 포함한 as a Cloud Service 아키텍처. 주요 사용 사례에는 모니터링, 보고 및 예약을 통해 규모에 맞게 수집되는 작업이 포함되며, 일반적인 클라우드 업로드 도구를 사용하여 자산을 클라우드 데이터 저장소로 처음 전송할 수 있습니다. 자세한 내용은 [자산 일괄 수집 도구](/help/assets/add-assets.md#asset-bulk-ingestor).

   이 도구는 시스템 관리자, 컨설턴트 또는 구현 파트너 개인용입니다. 이 기능을 사용하면 대규모 수집을 수행할 수 있으며, 초기 수집 또는 경우에 따라 큰 수집 중에 사용하기에 이상적입니다. 작은 수집 작업의 경우 [[!DNL Experience Manager] 데스크탑 앱](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/introduction.html?lang=en) 또는 [자산 사용자 인터페이스를 사용하여 업로드](/help/assets/add-assets.md#upload-assets).

   ![대량 가져오기 구성](/help/assets/assets/bulk-import-config-low-res.png)

* 이제 사용자가 카드 및 열 보기에서 디지털 자산을 정렬할 수 있습니다.

   ![자산 정렬](/help/assets/assets/asset-sort-options.png)

* 에서는 액세스 가능성에 대해 다음과 같은 개선 작업이 수행됩니다 [!DNL Experience Manager Assets] 참조하십시오. 자세한 내용은 [의 접근성 기능 [!DNL Assets]](/help/assets/accessibility.md).

   * 키보드를 사용하여 타임라인을 탐색할 때 Esc 키는 포커스를 잃지 않고 모두 표시 옵션을 축소할 수 있습니다.
   * 키보드 탭 키를 사용하여 탐색할 때 추가한 태그에서 마지막 태그를 제거한 후 태그 필드에 포커스가 유지됩니다.
   * [!DNL Experience Manager] 이제 구성 요소에 화면 판독기에서 사용할 이름, 역할 및 값에 대한 적절한 정보가 포함되어 있습니다.
   * 유형/크기 콤보 상자, 링크 콤보 상자, 언어 콤보 상자 또는 텍스트 편집 상자를 삭제하면 키보드 포커스가 다음 또는 이전 사용자 인터페이스 요소나 보다 적절한 사용자 인터페이스 요소로 돌아갑니다.
   * 포인터를 옵션 위로 가져가면 선택 및 다운로드와 같은 팁이 나타납니다. 화면 돋보기를 사용하는 사용자는 이러한 팁으로 인해 파일 미리 보기를 볼 수 없습니다. 이제, `Escape` 키.
   * 페이지에 있는 그리드에서 그리드 셀을 선택하면 포커스가 화면에 나타나는 작업 막대로 이동합니다.
   * 의 모든 솔루션에 대한 링크에 대한 시각적 단서(밑줄 및 펼침 아이콘)가 표시되므로 시각적 사용자는 일반 텍스트와 링크를 구별할 수 있습니다 [!DNL Experience Manager] 홈 페이지.

* **Dynamic Media의 일괄처리 집합 사전 설정**: 이제 자산 파일을 개별적으로 또는 일괄 수집을 사용하여 폴더에 업로드할 때 이미지 세트 또는 스핀 세트에서 여러 자산 생성 및 구성을 자동화할 수 있습니다.

   자세한 내용은 [일괄처리 집합 사전 설정 정보](/help/assets/dynamic-media/batch-set-presets-dm.md).

* 이제 다음과 같은 액세스 가능성이 개선되었습니다. [!DNL Dynamic Media]:

   * 화면 판독기(JAWS, 내레이터)는 포함 크기 메뉴 옵션에서 메뉴 항목의 이름, 역할 및 상태에 대해 나레이트합니다.
   * 사용자는 `Tab` 키.
   * 비디오 인코딩 프로필을 만드는 워크플로우는 화면 판독기의 향상된 기능을 통해 사용자에게 더 친숙합니다.
   * 을 사용하여 탐색 시 `Tab` 키. 포커스가 워크플로우의 적절한 사용자 인터페이스 요소로 이동하여 대화형 비디오를 만듭니다.
   * 웹 표준을 준수하도록 게시 페이지, 자산 편집 페이지, 스마트 자르기 편집 페이지 및 이미지 세트 편집기 페이지가 개선되었습니다. 이제 AT(Assistive Technology) 사용자가 이러한 페이지를 쉽게 탐색하고 이미지를 자르는 등의 작업을 수행할 수 있습니다.
   * 사용자가 키보드를 사용하여 탐색할 수 있도록 뷰어가 개선되었습니다.
   * 키보드 및 화면 판독기 사용자는 자르기 기능을 사용할 수 있습니다.
   * 키보드 사용자는 핫스팟을 더 잘 관리할 수 있습니다.

   자세한 내용은 [의 액세스 가능성 [!DNL Dynamic Media]](/help/assets/dynamic-media/accessibility-dm.md).

## Adobe Experience Manager Commerce as a Cloud Service {#cloud-services-commerce}

### 새로운 기능 {#what-is-new-commerce}

* 최신 CIF 코어 구성 요소 버전 v1.5.0이 포함된 CIF Venia 참조 사이트 - 2020.11.05이 출시되었습니다. 다음을 참조하십시오. [CIF Venia 참조 사이트](https://github.com/adobe/aem-cif-guides-venia/releases/tag/venia-2020.10.27) 자세한 내용

* CIF 코어 구성 요소 v1.5.0이 출시되었습니다. 자세한 내용은 [CIF 코어 구성 요소](https://github.com/adobe/aem-core-cif-components/releases/tag/core-cif-components-reactor-1.5.0) 자세한 내용

### 버그 수정 {#bug-fixes-commerce}

* Sling CA 구성에서 직접 구성을 지정하지 않고 상위 구성 중 하나에서 구성을 지정하지 않은 경우 GraphQL 클라이언트 구성을 올바르게 읽지 못했습니다. 이 문제가 해결되었습니다.

## Cloud Manager {#cloud-manager}

### 릴리스 날짜 {#release-date-cm}

AEM as a Cloud Service 2020.11.0의 Cloud Manager 릴리스 날짜는 2020년 11월 12일입니다.

### [!DNL Cloud Manager]의 새로운 기능 {#what-is-new-cm}

* 새 메뉴 옵션 **로컬 로그인** 이제 의 환경 메뉴 옵션에서 사용자가 이(가) **환경** 카드 및 **환경** 요약 페이지.
자세한 내용은 [환경 관리](/help/implementing/cloud-manager/manage-environments.md#login-locally)를 참조하십시오.

* 다음 **학습** cloud Manager의 탭이 UI의 새 이미지로 새로 고침되었습니다.

### 버그 수정 {#bug-fixes-cloud-manager}

* 빌드 실행 전에 수행된 종속성을 로드하려면 Maven 플러그인을 다운로드해야 합니다.
* Cloud Manager 바닥글의 언어를 선택하는 링크를 통해 올바른 위치로 이동합니다.
* 코드 스캔 중에 SonarQube 프로세스가 시작되지 않는 경우가 있습니다. 이제 자동 검색되고 다시 시작하려고 합니다.
* 모든 기존 프로덕션 파이프라인은 경험 감사 단계에서 자동으로 활성화됩니다.

## Adobe Experience Manager as a Cloud Service Foundation {#cloud-service-foundation}

### 워크플로 {#workflows}

* 워크플로우 제목, 워크플로우 모델, 상태, 개시자, 페이로드 경로 및 시작 날짜를 기반으로 워크플로우 인스턴스 검색에 대한 지원이 추가되었습니다. 자세한 내용은 [검색 워크플로우 인스턴스](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/sites/administering/workflows-administering.html).

### 게시 계층 사용자 데이터 동기화 {#user-sync}

* 프로필 속성 및 그룹 멤버십을 포함한 사용자 데이터는 게시 계층에서 유지할 수 있습니다. 에서 이 기능에 대해 자세히 알아보십시오 [등록, 로그인 및 사용자 프로필 설명서](/help/sites-cloud/authoring/personalization/user-and-group-sync-for-publish-tier.md).

### SDK Build Analyzer {#analyzers}

AEM as a Cloud Service SDK Build Analyzer Maven 플러그인은 누락된 종속성을 포함하여 Maven 프로젝트의 문제를 감지합니다. Cloud Manager를 사용하여 클라우드 환경에 배포하기 전에 개발자에게 로컬 개발 중에 문제를 발견할 수 있는 기회를 제공합니다. 자세한 내용은 설명서를 참조하십시오 [여기](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/build-analyzer-maven-plugin.html?lang=ko-KR#developing) 및 [여기](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/aem-as-a-cloud-service-sdk.html?lang=en#building-for-the-sdk).

### 기타 {#others-foundation}

새로 만들기 [&quot;httpd -t&quot; 구문](/help/implementing/dispatcher/disp-overview.md#local-validation) cloud Manager 빌드 중에 실행된 apache 및 dispatcher 구성을 확인합니다. 이 구성은 AEM as a Cloud Service SDK의 Dispatcher 도구를 사용하여 실행할 수도 있습니다.

## 콘텐츠 전송 도구 {#content-transfer-tool}

이 섹션을 통해 새로운 기능 및 업데이트를 알아보십시오 [컨텐츠 전송 도구](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/overview-content-transfer-tool.html) 릴리스 v1.1.12.

### 새로운 기능 {#what-is-new-ctt}

* 로그에 대한 사용자 경험이 개선되었습니다. 추출 및 수집 로그에 타임스탬프가 추가되었습니다. 로그가 비어 있는지 여부에 대한 메시지가 추가되었습니다.

### 버그 수정 {#ctt-bug-fixes}

* 마이그레이션 세트에 부분적으로 유사한 파일 이름이 있는 경로가 포함된 경우 컨텐츠 전송 도구에서 컨텐츠 파일을 건너뛰었습니다. 이 문제가 해결되었습니다.

## Best Practices Analyzer {#best-practices-analyzer}

### 릴리스 날짜 {#release-date-bpa}

모범 사례 분석기 릴리스 날짜는 2020년 11월 13일입니다.

### [!DNL Best Practices Analyzer]의 새로운 기능 {#what-is-new-bpa}

* 클라우드 준비 분석기 가 이제 모범 사례 분석기 (BPA)로 제공됩니다. BPA는 현재 AEM 구현에 대한 모범 사례 평가를 제공하며 기존 AEM 인스턴스에서 AEM as a Cloud Service으로 이동할 준비를 평가하는 데 도움을 줍니다.

* 의 사용을 감지하기 위해 새 탐지기가 추가되었습니다. `java.io.InputStream`: AEM as a Cloud Service에서 사용할 경우 문제가 발생할 수 있습니다.

### 버그 수정 {#bpa-bug-fixes}

* 와 관련된 긍정 오류(positive)를 일으키는 버그 *텍스트 필드 기초* 구성 요소가 수정되었습니다.
