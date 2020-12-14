---
title: ' [!DNL Adobe Experience Manager] as a Cloud Service 2020.10.0 릴리스의 릴리스 노트'
description: '[!DNL Adobe Experience Manager] 를 Cloud Service 릴리스 노트로 2020.10.0.'
translation-type: tm+mt
source-git-commit: fd271f24e5f8ddbe440dccf5c51c91a46c70dead
workflow-type: tm+mt
source-wordcount: '1044'
ht-degree: 17%

---


# [!DNL Adobe Experience Manager] as a Cloud Service 2020.10.0 릴리스 노트 {#release-notes}

다음 섹션에서는 [!DNL Experience Manager]에 대한 일반적인 릴리스 노트를 Cloud Service 2020.10.0으로 간략하게 설명합니다.

## 릴리스 날짜 {#release-date}

Cloud Service으로 [!DNL Adobe Experience Manager]에 대한 릴리스 날짜는 2020년 10월 28일입니다.
다음 릴리스(2020.11.0)은 2020년 12월 1일에 제공됩니다.

## [!DNL Adobe Experience Manager Sites] cloud service  {#sites}

### [!DNL Sites] {#what-is-new-sites}의 새로운 기능

* **[핵심 구성 요소 2.12.0](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html)**:AEM은 핵심 구성 요소의 최신 릴리스에 대한 자동 업데이트를 통해 Cloud Service의 이점을 제공합니다. 릴리스 2.12.0에는 [새 POST 양식 핸들러;](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/components/forms/form-container.html#post-data) 컨텍스트 인식 구성을 통해 사용자 지정 CSS, Javascript 및 메타데이터 [태그를 포함하는 기능;](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/including-clientlibs.html#context-aware-loading) 및 [`DataLayerBuilder`](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/data-layer/integrations.html#enabling-custom-components) 유틸리티 등 커뮤니티에서 제공하는 최신 개선 사항이 포함되어 있습니다. 2.12.0의 [변경 사항 목록](https://github.com/adobe/aem-core-wcm-components/releases/tag/core.wcm.components.reactor-2.12.0)을 참조하십시오.

* **[프로젝트 원형 24](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html)**:새로운  [Adobe 클라이언트 데이터 레이어](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/data-layer/overview.html), AMP에서 사이트 [를 제공하는 옵션, 프로젝트 CSS/JS를 추가할 수 있는 새로운 ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/amp.html) 확장 지점 등 새로운 AEM 프로젝트를 시작하기 위한 권장 [ 기반이개선되었습니다.](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/including-clientlibs.html#context-aware-loading)

* **[ContextHub 폴더](/help/sites-cloud/authoring/personalization/contexthub-segmentation.md#organizing-segments)**:대상 폴더를 만들어 ContextHub 오퍼 타깃팅 기능에 사용할 대상 세그먼트를 쉽게 구성, 검색 및 선택할 수 있습니다.

## [!DNL Adobe Experience Manager Assets] cloud service  {#assets}

* **[!DNL Adobe Sensei]강력한 비디오 스마트 태그 지정**:DAM 사용자는 AI 모델을 활용하여 개체 및 작업별 태그의 비디오 컨텐츠를 분석함으로써 태그를 추가하는 데 소요되는 시간을 줄이고, 고객에게 적합한 경험을 제공하기 위해 노출된 다양한 정보를 사용하는 데 더 많은 시간을 할애할 수 있습니다. [스마트 태그 비디오 자산](/help/assets/smart-tags-video-assets.md)을 참조하십시오.

* **브랜드 포털 개선** 사항:다음 새로운 기능 등을 에서 사용할 수 있습니다 [!DNL Brand Portal]. 자세한 내용은 [[!DNL Brand Portal] 릴리스 노트](https://docs.adobe.com/content/help/en/experience-manager-brand-portal/using/introduction/brand-portal-release-notes.html)를 참조하십시오.

   * [간소화된 ](https://docs.adobe.com/content/help/en/experience-manager-brand-portal/using/download/brand-portal-download-assets.html) 빠른 다운로드를 위한 향상된 다운로드 경험 추가 다운로드 구성은 관리자가 사용자 및 비즈니스의 요구 사항에 맞는 경험을 제공하도록 구성할 수 있습니다.
   * 이제 한 번의 클릭으로 파일, [컬렉션](https://docs.adobe.com/content/help/en/experience-manager-brand-portal/using/share/brand-portal-share-collection.html) 및 공유 링크를 모든 페이지에서 탐색할 수 있습니다.
   * 사용자는 지금 [특정 표현물을 선택하고 다운로드할 수 있습니다](https://docs.adobe.com/content/help/en/experience-manager-brand-portal/using/download/brand-portal-download-assets.html#download-assets-from-asset-details-page). 새 변환 다운로드 옵션은 에셋 세부 사항 페이지의 표현물 패널에서 사용할 수 있습니다.
   * 게스트 사용자 세션의 제한 시간을 15분으로 설정하면 모든 동시 사용자에게 더 나은 환경을 제공할 수 있습니다.

* **[!DNL Adobe Asset Link]버전 2.1**:새 버전의  [Adobe 에셋 ](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/manage-assets-using-adobe-asset-link.ug.html) Linkextension for  [!DNL Adobe Photoshop], and  [!DNL Adobe Illustrator] [!DNL Adobe InDesign] is available. 2020년 10월에 출시된 버전 2021의 최신 [!DNL Adobe Creative Cloud] 애플리케이션과의 호환성을 추가합니다.

* **[!DNL Assets]WebP 파일 지원**: [!DNL Assets] 이제 Cloud Service에서 WebP 이미지 형식을 지원합니다. WebP는 Google에서 만든 새로운 이미지 형식입니다. WebP 파일 형식의 이미지는 JPG 또는 PNG 파일과 시각적으로 구별할 수 없으며 파일 크기가 훨씬 작습니다. 자산의 파일 크기를 줄여 페이지 로드 시간이 단축되고 컨텐츠 작성자가 보다 신속하게 웹 경험을 제공할 수 있습니다. [처리 프로필 만들기](/help/assets/asset-microservices-configure-and-use.md#create-standard-profile)에서 WebP를 사용하는 방법을 참조하십시오.

## Adobe Experience Manager 상거래를 Cloud Service {#cloud-services-commerce}

### 새로운 기능 {#what-is-new-commerce}

* 최신 CIF 코어 구성 요소 버전 v1.4.0을 포함하는 CIF Venia 참조 사이트 - 2020.10.2. 자세한 내용은 [CIF Venia 참조 사이트](https://github.com/adobe/aem-cif-guides-venia/releases/tag/venia-2020.10.2)를 참조하십시오.

* CIF 코어 구성 요소 v1.4.0 릴리스되었습니다. 자세한 내용은 [CIF 핵심 구성 요소](https://github.com/adobe/aem-core-cif-components/releases/tag/core-cif-components-reactor-1.4.0)를 참조하십시오.

### 버그 수정 {#bug-fixes-commerce}

* 제품 콘솔 및 피커의 GraphQL 요청은 HTTP POST을 통해 수행되었습니다. Apollo GraphQL 클라이언트가 구성된 경우 GET 요청을 지원하기 위해 GraphQL 클라이언트 OSGi 구성의 설정을 준수하도록 수정되었습니다.

* CIF 클라우드 구성 UI에 /lib 및 /apps/의 구성에 대한 &quot;저장 및 닫기&quot; 단추가 표시되었습니다. 그러나 이러한 UI는 읽기 전용이므로 &quot;닫기&quot; 단추만 표시하도록 수정되었습니다.

## Cloud Manager {#cloud-manager}

### 릴리스 날짜 {#release-date-cm}

2020년 10월 20일에 Cloud Service으로 AEM의 Cloud Manager에 대한 릴리스 날짜가 2020.10.0.

### [!DNL Cloud Manager] {#what-is-new-cm}의 새로운 기능

* 환경 페이지가 다시 디자인되었습니다.

* 최대 절전 모드인 환경에서 이제 최대 절전 모드일 경우 Cloud Manager에서 개별 상태를 볼 수 있습니다.

* 이제 클라우드 관리자 빌드 컨테이너가 Java 8 또는 Java 11을 사용하여 프로젝트를 컴파일할 수 있습니다. Java 11에 대한 지원은 Maven 툴체인 시스템에서 제공합니다.

* 환경당 환경 변수의 수가 200개로 증가했습니다.

* 개요 페이지의 환경 카드는 이제 최대 3개의 환경을 나열합니다. 사용자는 **모두 표시** 단추를 선택하여 환경 요약 페이지로 이동하여 전체 환경 목록이 포함된 테이블을 볼 수 있습니다.
자세한 내용은 [환경 보기](/help/implementing/cloud-manager/manage-environments.md#viewing-environment)를 참조하십시오.

### 버그 수정 {#bug-fixes-cloud-manager}

* 환경이 완전히 만들어지기 전에 Cloud Manager에서 개발자 콘솔로의 링크가 잘못 활성화되었습니다.

* Cloud Manager에서 직접 개발자 콘솔로 연결되는 링크에는 샌드박스 프로그램 환경의 최대 절전 모드 해제/최대 절전 모드 해제 옵션이 표시되지 않습니다.

* 비프로덕션 파이프라인 편집 페이지의 취소 및 저장 단추가 항상 표시되는 것은 아닙니다.

* 코드 품질 프로세스의 일부 오류로 인해 로그 파일이 올바로 생성되지 않을 수 있습니다.

* 새 프로그램을 만들 때 제안된 이름은 기존 프로그램 이름의 복제본을 반환하는 경우가 있습니다.

* 일부 큰 파이프라인 단계 로그를 사용자 인터페이스를 통해 일관되게 다운로드할 수 없습니다.

* 환경 이름의 유효성 검사에 오류가 발생했습니다.

* 환경 페이지는 존재하지 않을 때 게시 및 발송자 세그먼트를 표시하는 경우가 있습니다.

## Adobe Experience Manager as a Cloud Service 기반 {#cloud-service-foundation}

### 워크플로우 {#workflows}

* 워크플로우 제목, 워크플로우 모델, 상태, 개시자, 페이로드 경로 및 시작 날짜를 기준으로 워크플로우 인스턴스를 검색할 수 있도록 지원이 추가되었습니다. [검색 워크플로 인스턴스](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/sites/administering/workflows-administering.html)를 참조하십시오.

## 컨텐츠 전송 도구 {#content-transfer-tool}

[컨텐트 전송 도구](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/overview-content-transfer-tool.html) 릴리스 v1.1.12의 새로운 기능과 업데이트에 대해 알아보려면 이 섹션을 따르십시오.

### 새로운 기능 {#what-is-new-ctt}

* 로그에 대한 사용자 경험이 개선되었습니다. 추출 및 통합 로그에 타임스탬프가 추가되었습니다. 로그가 비어 있는지를 나타내는 메시지가 추가되었습니다.

### 버그 수정 {#ctt-bug-fixes}

* 마이그레이션 세트에 부분적으로 비슷한 파일 이름을 가진 경로가 포함된 경우 내용 전송 도구가 콘텐트 파일을 건너뛰었습니다. 이 문제가 수정되었습니다.
