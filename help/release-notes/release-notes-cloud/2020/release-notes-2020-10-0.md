---
title: ' [!DNL Adobe Experience Manager] as a Cloud Service의 2020.10.0 릴리스 정보입니다.'
description: "[!DNL Adobe Experience Manager] 2020.10.0의 as a Cloud Service 릴리스 노트"
exl-id: ac741744-5b47-47a4-b5af-e1089e92c3f0
source-git-commit: cc6565121a76f70b958aa9050485e0553371f3a3
workflow-type: tm+mt
source-wordcount: '1197'
ht-degree: 29%

---

# [!DNL Adobe Experience Manager] as a Cloud Service 2020.10.0 릴리스 노트  {#release-notes}

다음 섹션에서는 의 일반 릴리스 정보에 대해 간략히 소개합니다. [!DNL Experience Manager] as a Cloud Service 2020.10.0.

## 릴리스 일자 {#release-date}

의 릴리스 날짜 [!DNL Adobe Experience Manager] as a Cloud Service 2020.10.0은 2020년 10월 28일입니다.
다음 릴리스(2020.11.0) 날짜는 2020년 12월 1일입니다.

## [!DNL Adobe Experience Manager Sites] as a Cloud Service {#sites}

### [!DNL Sites]의 새로운 기능 {#what-is-new-sites}

* **[코어 구성 요소 2.12.0](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=ko)**: Adobe Experience Manager as a Cloud Service은 핵심 구성 요소의 최신 릴리스에 대한 자동 업데이트 혜택을 제공합니다. 릴리스 2.12.0에는 커뮤니티에서 제공한 최신 개선 사항이 포함되어 있습니다. 개선 사항은 다음과 같습니다 [새 POST 양식 핸들러](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/components/forms/form-container.html#post-data) 사용자 지정 CSS, JavaScript 및 메타데이터를 포함하는 기능 [컨텍스트 인식 구성을 통한 태그](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/including-clientlibs.html#context-aware-loading) 및 a [`DataLayerBuilder`](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/data-layer/integrations.html#enabling-custom-components) 유틸리티를 사용하여 사용자 지정 구성 요소에서 Adobe 데이터 레이어 통합을 단순화할 수 있습니다. 다음을 참조하십시오. [변경 사항 목록](https://github.com/adobe/aem-core-wcm-components/releases/tag/core.wcm.components.reactor-2.12.0) 2.12.0에서.

* **[Project Archetype 24](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html)**: 새 Experience Manager 프로젝트를 시작하기 위한 권장 기반이 개선되었습니다. 이제 새로운 기능이 포함됩니다. [Adobe 클라이언트 데이터 레이어](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/data-layer/overview.html), 옵션 [amp에서 사이트 제공,](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/amp.html) 및 신규 [확장은 프로젝트 CSS/JS 추가를 가리킵니다.](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/including-clientlibs.html#context-aware-loading)

* **[ContextHub 폴더](/help/sites-cloud/authoring/personalization/contexthub-segmentation.md#organizing-segments)**: ContextHub 오퍼 타깃팅 기능에 사용할 대상 세그먼트를 쉽게 구성하고, 찾고, 선택할 수 있는 대상 폴더를 만드는 기능.

## [!DNL Adobe Experience Manager Assets] as a Cloud Service {#assets}

* **[!DNL Adobe Sensei]비디오 고급 태그 지정**: DAM 사용자는 AI 모델을 적용하여 개체 및 작업별 태그에 대한 비디오 콘텐츠를 분석함으로써 태그를 추가하는 데 드는 시간을 줄이고 노출된 풍부한 정보를 사용하는 데 더 많은 시간을 사용할 수 있습니다. 결과적으로 고객에게 올바른 경험을 제공합니다. 다음을 참조하십시오 [스마트 태그 비디오 자산](/help/assets/smart-tags-video-assets.md).

* **Brand Portal 개선 사항**: 다음과 같은 새로운 기능 등을에서 사용할 수 있습니다 [!DNL Brand Portal]. 자세한 내용은 [[!DNL Brand Portal] 릴리스 정보](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/introduction/brand-portal-release-notes.html).

   * [다운로드 환경 개선](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/download/brand-portal-download-assets.html) 를 사용하십시오. 사용자와 비즈니스의 요구사항에 적합한 경험을 제공하기 위한 추가 다운로드 구성은 관리자가 구성할 수 있습니다.
   * 이제 모든 페이지에서 한 번 클릭으로 파일, [컬렉션](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/share/brand-portal-share-collection.html), 공유 링크를 탐색할 수 있습니다.
   * 사용자는 [특정 렌디션을 선택하여 다운로드](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/download/brand-portal-download-assets.html#download-assets-from-asset-details-page)할 수 있습니다. 새 렌디션 다운로드 옵션이 에셋 세부 사항 페이지의 렌디션 패널에 제공됩니다.
   * 게스트 사용자 세션에 15분의 시간 제한을 적용하여 모든 동시 사용자에게 더 나은 경험을 제공할 수 있습니다.

* **[!DNL Adobe Asset Link]버전 2.1**: 의 새 버전 [Adobe 에셋 링크](https://helpx.adobe.com/kr/enterprise/using/manage-assets-using-adobe-asset-link.html) 확장 [!DNL Adobe Photoshop], [!DNL Adobe Illustrator], 및 [!DNL Adobe InDesign] 을(를) 사용할 수 있습니다. 최신 버전과의 호환성을 제공합니다. [!DNL Adobe Creative Cloud] 버전 2021의 애플리케이션이 2020년 10월에 릴리스되었습니다.

* **[!DNL Assets]WebP 파일 지원**: [!DNL Assets] 이제 as a Cloud Service에서 WebP 이미지 형식을 지원합니다. WebP는 Google에서 만든 새로운 이미지 형식입니다. WebP 파일 형식의 이미지는 JPG 또는 PNG 파일과 시각적으로 구별되지 않으며 파일이 훨씬 작습니다. 에셋의 파일 크기를 줄이면 페이지 로드 시간이 향상되고 콘텐츠 작성자가 더 빠른 웹 경험을 제공할 수 있습니다. 에서 WebP 사용 방법 보기 [처리 프로필 만들기](/help/assets/asset-microservices-configure-and-use.md#create-standard-profile).

## [!DNL Adobe Experience Manager Forms] as a Cloud Service {#forms-oct-2021}

### [!DNL Forms]의 새로운 기능 {#what-is-new-forms-oct-2021}

* **적응형 Forms에 대한 Analytics**: 이제 적응형 Forms용 Adobe Analytics을 통해, 로그인된 및 로그인되지 않은(익명의) 최종 사용자 행동을 포착하고 추적하여 최종 사용자 인사이트를 수집할 수 있습니다. 이를 통해 비즈니스 사용자는 수집된 인사이트를 기반으로 적응형 양식 콘텐츠, 레이아웃 및 스타일에 대한 올바른 결정을 내릴 수 있습니다.

### [!DNL Forms] 프리릴리스 채널에서 사용할 수 있는 새로운 기능 {#prerelease-features-forms-oct-2021}

* **안전한 처리를 위한 AEM Workflow 데이터 외부화**: 민감한 개인 데이터(SPD) 요소가 포함된, 처리 중인 AEM Workflow 변수 데이터를 고객 관리 저장소에 저장하여 안전하게 처리할 수 있습니다. 워크플로우를 처리하는 동안 워크플로우 변수에 저장된 데이터는 AEM 저장소에 보관되지 않습니다. 고객 관리 저장소에서 필요에 따라 가져옵니다.

### [!DNL Forms]의 베타 기능 {#sep-what-is-new-forms-oct-prerelease}

* **[!DNL AEM Forms as a Cloud Service - Communications]**: [통신 API](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/using-communications/aem-forms-cloud-service-communications.html) 템플릿과 XML 데이터를 결합하여 다양한 형식의 문서를 생성할 수 있습니다. 이 서비스를 사용하면 동기화 모드와 배치 모드에서 문서를 생성할 수 있습니다.

Beta 프로그램에 등록하려면 [!DNL formscsbeta@adobe.com]에 문의하십시오.

## Adobe Experience Manager Commerce as a Cloud Service {#cloud-services-commerce}

### 새로운 기능 {#what-is-new-commerce}

* 최신 CIF 코어 구성 요소 버전 v1.4.0이 포함된 CIF Venia 참조 사이트 - 2020.10.2가 릴리스되었습니다. 을(를) 참조하십시오 [CIF Venia 참조 사이트](https://github.com/adobe/aem-cif-guides-venia/releases/tag/venia-2020.10.2) 을 참조하십시오.

* CIF 코어 구성 요소 v1.4.0이 릴리스되었습니다. 을(를) 참조하십시오 [CIF 핵심 구성 요소](https://github.com/adobe/aem-core-cif-components/releases/tag/core-cif-components-reactor-1.4.0) 을 참조하십시오.

### 버그 수정 {#bug-fixes-commerce}

* 제품 콘솔 및 피커에 있었던 GraphQL 요청은 HTTP POST을 통해 수행되었습니다. 이 문제는 구성된 경우 GraphQL 요청을 지원하기 위해 아폴로 GraphQL 클라이언트가 GET 클라이언트 OSGi 구성의 설정을 준수하는지 확인하기 위해 수정되었습니다.

* /lib 및 /apps/ 의 구성에 대해 CIF Cloud 구성 UI에 &quot;저장 및 닫기&quot; 버튼이 표시되었습니다. 그러나 이러한 인터페이스는 읽기 전용이므로 UI는 &quot;닫기&quot; 버튼만 표시하도록 수정되었습니다.

## Cloud Manager {#cloud-manager}

### 릴리스 날짜 {#release-date-cm}

Experience Manager as a Cloud Service 2020.10.0의 Cloud Manager 릴리스 일자는 2020년 10월 2일입니다.

### [!DNL Cloud Manager]의 새로운 기능 {#what-is-new-cm}

* 환경 페이지가 다시 디자인되었습니다.

* 최대 절전 모드인 환경에서 이제 최대 절전 모드일 경우 Cloud Manager에서 개별 상태를 볼 수 있습니다.

* Cloud Manager &quot;빌드 컨테이너&quot;는 이제 Java™ 8 또는 Java™ 11을 사용하여 프로젝트 컴파일을 지원합니다. Java™ 11에 대한 지원은 Maven 툴체인 시스템에서 제공됩니다.

* 환경당 환경 변수의 수가 200개로 증가했습니다.

* 이제 개요 페이지의 환경 카드에 최대 3개의 환경이 나열됩니다. 사용자는 **모두 표시** 버튼을 선택하고 환경 요약 페이지로 이동하여 전체 환경 목록이 포함된 테이블을 볼 수 있습니다.
자세한 내용은 [환경 보기](/help/implementing/cloud-manager/manage-environments.md#viewing-environment)를 참조하십시오.

### 버그 수정 {#bug-fixes-cloud-manager}

* 환경이 완전히 만들어지기 전에 Cloud Manager에서 개발자 콘솔로의 링크가 잘못 활성화되었습니다.

* Cloud Manager에서 직접 개발자 콘솔로 연결되는 링크에는 샌드박스 프로그램 환경의 최대 절전 모드 해제/최대 절전 모드 해제 옵션이 표시되지 않습니다.

* 비프로덕션 파이프라인 편집 페이지의 취소 및 저장 버튼이 표시되지 않는 경우가 있었습니다.

* 코드 품질 프로세스의 일부 오류로 인해 로그 파일이 올바로 생성되지 않을 수 있습니다.

* 프로그램을 만들 때 제안된 이름은 기존 프로그램 이름의 복제본을 반환하는 경우가 있습니다.

* 일부 큰 파이프라인 단계 로그를 사용자 인터페이스를 통해 일관되게 다운로드할 수 없습니다.

* 환경 이름의 유효성 검사에 오류가 발생했습니다.

* 환경 페이지는 존재하지 않을 때 게시 및 Dispatcher 세그먼트를 표시하는 경우가 있습니다.

## Adobe Experience Manager as a Cloud Service Foundation {#cloud-service-foundation}

### 워크플로 {#workflows}

* 워크플로우 제목, 워크플로우 모델, 상태, 개시자, 페이로드 경로 및 시작 날짜를 기반으로 워크플로우 인스턴스 검색에 대한 지원이 추가되었습니다. 다음을 참조하십시오 [워크플로 인스턴스 검색](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/sites/administering/workflows-administering.html).

## 콘텐츠 전송 도구 {#content-transfer-tool}

의 새로운 기능 및 업데이트에 대해 자세히 알아보기 [컨텐츠 전송 도구](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/overview-content-transfer-tool.html) 릴리스 v1.1.12.

### 새로운 기능 {#what-is-new-ctt}

* 로그에 대한 사용자 경험이 개선되었습니다. 추출 및 수집 로그에 타임스탬프가 추가되었습니다. 로그가 비어 있는지 여부를 나타내는 메시지가 추가되었습니다.

### 버그 수정 {#ctt-bug-fixes}

* 마이그레이션 세트에 파일 이름이 부분적으로 유사한 경로가 포함된 경우 컨텐츠 전송 도구가 컨텐츠 파일을 건너뛰고 있었습니다.
