---
title: ' [!DNL Adobe Experience Manager] as a Cloud Service 2020.10.0 릴리스의 릴리스 노트'
description: '[!DNL Adobe Experience Manager] 를 Cloud Service 릴리스 노트로 사용하십시오.'
translation-type: tm+mt
source-git-commit: 11df1136cbfca9237ead417cacca4049e2f35b4d
workflow-type: tm+mt
source-wordcount: '888'
ht-degree: 20%

---


# [!DNL Adobe Experience Manager] as a Cloud Service 2020.10.0 릴리스 노트 {#release-notes}

The following section outlines the general Release Notes for [!DNL Experience Manager] as a Cloud Service 2020.10.0.

## 릴리스 날짜 {#release-date}

The Release Date for [!DNL Adobe Experience Manager] as a Cloud Service 2020.10.0 is October 28, 2020.
다음 릴리스(2020.11.0)는 2020년 12월 1일에 제공됩니다.

## [!DNL Adobe Experience Manager Sites] cloud service {#sites}

### What is new in [!DNL Sites] {#what-is-new-sites}

<!-- add when release done: * **Core Components 2.12.0**: With Core Components being on auto-update, benefit from the latest improvements contributed by the community. See list of changes since 2.11.1: Release Notes -->

* **프로젝트 원형 24**:새로운 Adobe 클라이언트 데이터 레이어, AMP에서 사이트를 제공하는 옵션, 프로젝트 CSS/JS를 추가하기 위한 새로운 확장 지점을 포함하여 새로운 AEM 프로젝트를 시작하기 위한 권장 기반이 개선되었습니다.

* **ContextHub 폴더**:ContextHub에서 타깃팅 기능을 제공하는 데 사용할 대상 세그먼트를 쉽게 구성, 검색 및 선택할 수 있는 대상 폴더를 만드는 기능

## [!DNL Adobe Experience Manager Assets] cloud service {#assets}

### What is new in [!DNL Assets] {#what-is-new-assets}

* **[!DNL Adobe Sensei]강력한 비디오 스마트 태그 지정**:DAM 사용자는 AI 모델을 활용하여 객체 및 특정 태그의 비디오 컨텐츠를 분석함으로써 태그를 추가하는 데 걸리는 시간을 줄이고 다양한 정보를 활용하여 고객에게 최적의 경험을 전달할 수 있습니다. 스마트 [태그 비디오 자산을 참조하십시오](/help/assets/smart-tags-video-assets.md).

* **향상된 브랜드 포털**:다음 새로운 기능 등을 에서 사용할 수 있습니다 [!DNL Brand Portal]. For details, see [[!DNL Brand Portal] release notes](https://docs.adobe.com/content/help/en/experience-manager-brand-portal/using/introduction/brand-portal-release-notes.html).

   * [간소화된 빠른 다운로드를 위한 향상된 다운로드 경험](https://docs.adobe.com/content/help/en/experience-manager-brand-portal/using/download/brand-portal-download-assets.html) . 관리자는 추가 다운로드 구성을 구성하여 사용자와 기업의 요구 사항에 맞는 경험을 제공할 수 있습니다.
   * 이제 모든 페이지에서 한 번의 클릭으로 파일, [컬렉션](https://docs.adobe.com/content/help/en/experience-manager-brand-portal/using/share/brand-portal-share-collection.html)및 공유 링크를 탐색할 수 있습니다.
   * 사용자는 이제 특정 변환을 [선택하고 다운로드할 수](https://docs.adobe.com/content/help/en/experience-manager-brand-portal/using/download/brand-portal-download-assets.html#download-assets-from-asset-details-page) 있습니다. 새 변환 다운로드 옵션은 자산 세부 사항 페이지의 변환 패널에서 사용할 수 있습니다.
   * 게스트 사용자 세션의 제한 시간이 15분으로 모든 동시 사용자에게 더 나은 환경을 제공합니다.

* **[!DNL Adobe Asset Link]버전 2.1**:새 버전의 [Adobe 에셋 링크](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/manage-assets-using-adobe-asset-link.ug.html) 확장 [!DNL Adobe Photoshop]을 사용할 수 [!DNL Adobe Illustrator]있으며 사용할 수 [!DNL Adobe InDesign] 있습니다. 또한 2020년 10월에 출시된 2021 버전의 최신 [!DNL Adobe Creative Cloud] 애플리케이션과의 호환성을 제공합니다.

* **[!DNL Assets]WebP 파일 지원**: [!DNL Assets] 이제 Cloud Service에서 WebP 이미지 형식을 지원합니다. WebP는 Google에서 만든 새로운 이미지 형식입니다. WebP 파일 형식의 이미지는 JPG 또는 PNG 파일과 시각적으로 구별할 수 없으며 파일 크기가 훨씬 작습니다. 자산의 파일 크기가 낮아지면 페이지 로드 시간이 단축되고 컨텐츠 작성자가 보다 빠른 웹 경험을 제공할 수 있습니다. 표준 처리 프로필 [만들기를 참조하십시오](/help/assets/asset-microservices-configure-and-use.md#create-standard-profile).

## Adobe Experience Manager Commerce as a Cloud Service {#cloud-services-commerce}

### 새로운 기능 {#what-is-new-commerce}

* 최신 CIF 코어 구성 요소 버전 v1.4.0이 포함된 CIF Venia 참조 사이트 - 2020.10.2가 출시되었습니다. 자세한 내용은 [CIF Venia 참조 사이트](https://github.com/adobe/aem-cif-guides-venia/releases/tag/venia-2020.10.2) 를 참조하십시오.

* CIF 코어 구성 요소 v1.4.0이 출시되었습니다. 자세한 내용은 [CIF 코어 구성](https://github.com/adobe/aem-core-cif-components/releases/tag/core-cif-components-reactor-1.4.0) 요소를 참조하십시오.

### 버그 수정 {#bug-fixes-commerce}

* 제품 콘솔 및 Pickers의 GraphQL 요청은 HTTP POST을 통해 수행되었습니다. Apollo GraphQL 클라이언트가 GET 요청을 지원하도록 GraphQL 클라이언트 OSGi 구성의 설정을 준수하도록 수정되었습니다.

* CIF 클라우드 구성 UI에 /lib 및 /apps/의 구성에 대한 &quot;저장 및 닫기&quot; 단추가 표시되었습니다. 그러나 이러한 UI는 &quot;닫기&quot; 단추만 표시하도록 수정되었습니다.

## Cloud Manager {#cloud-manager}

* 환경 페이지가 다시 디자인되었습니다.

* 최대 절전 모드인 환경에서 이제 최대 절전 모드일 경우 Cloud Manager에서 개별 상태를 볼 수 있습니다.

* 이제 클라우드 관리자 빌드 컨테이너는 Java 8 또는 Java 11을 사용하여 프로젝트를 컴파일할 수 있습니다. Java 11에 대한 지원은 Maven 툴체인 시스템에서 제공합니다.

* 환경당 환경 변수의 수가 200개로 증가했습니다.

* 개요 페이지의 환경 카드는 최대 세 개의 환경을 나열합니다. 사용자는 모두 **표시** 단추를 선택하여 환경 요약 페이지로 이동하여 전체 환경 목록이 포함된 테이블을 볼 수 있습니다.
자세한 내용은 [환경](/help/implementing/cloud-manager/manage-environments.md#viewing-environment) 보기를 참조하십시오.

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

* 워크플로우 제목, 워크플로우 모델, 상태, 개시자, 페이로드 경로 및 시작 날짜를 기반으로 워크플로우 인스턴스 검색에 대한 지원이 추가되었습니다. 워크플로우 [인스턴스 검색을 참조하십시오](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/sites/administering/workflows-administering.html).

## 컨텐츠 전송 도구 {#content-transfer-tool}

Follow this section to learn about what is new and the updates for [Content Transfer Tool](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/overview-content-transfer-tool.html) Release v1.1.12.

### 새로운 기능 {#what-is-new-ctt}

* 로그에 대한 사용자 경험이 개선되었습니다. 추출 및 통합 로그에 타임스탬프가 추가되었습니다. 로그가 비어 있는지를 나타내는 메시지가 추가되었습니다.

### 버그 수정 {#ctt-bug-fixes}

* 마이그레이션 세트에 부분적으로 유사한 파일 이름이 있는 경로가 포함된 경우 컨텐츠 전송 도구가 콘텐트 파일을 건너뛰었습니다. 이 문제가 해결되었습니다.
