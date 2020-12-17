---
title: Cloud Service으로 [!DNL Adobe Experience Manager] 에 대한 현재 릴리스 노트입니다.
description: Cloud Service으로 [!DNL Adobe Experience Manager] 에 대한 현재 릴리스 노트입니다.
translation-type: tm+mt
source-git-commit: 984914c6147d0ee96575c93496cbdfc4bb9bc094
workflow-type: tm+mt
source-wordcount: '530'
ht-degree: 4%

---


# [!DNL Adobe Experience Manager] as a Cloud Service 릴리스 노트 {#release-notes}

다음 섹션에서는 Cloud Service으로 [!DNL Experience Manager]에 대한 일반적인 릴리스 노트에 대해 간략하게 설명합니다.

## 릴리스 날짜 {#release-date}

Cloud Service으로 [!DNL Adobe Experience Manager]에 대한 릴리스 날짜는 2020년 12월 17일입니다.
다음 릴리스(2021.1.0)은 2020년 1월 28일에 제공됩니다.

## [!DNL Adobe Experience Manager Assets] as  [!DNL Cloud Service] {#assets}

* 이제 [!DNL Adobe InDesign Server]과의 통합을 [!DNL Cloud Service](으)로 사용할 수 있습니다. [!DNL Experience Manager] [!DNL Adobe InDesign Server] 스크립팅을 사용하여 [!DNL Adobe InDesign] 파일을 자동으로 처리할 수 있으며 사용자가 [!DNL Assets] 템플릿 사용자 인터페이스를 사용하여 브로셔 또는 광고를 만들 수 있습니다. [!DNL Adobe Managed Services]에서 호스팅하는 [!DNL InDesign Server]만 [!DNL Experience Manager as a Cloud Service]에 대해 지원됩니다. <!-- TBD: Add link to article. -->

* [!DNL Experience Manager] 연결된 에셋 기능을 사용하여 원격 배포에 에셋이 사용될 때 에셋 참조를 추적 및 표시하도록  [!DNL Experience Manager Sites] 향상되었습니다. 이제 자산의 [!UICONTROL 속성] 페이지에 있는 새 [!UICONTROL 참조] 탭에 자산의 로컬 및 원격 참조가 나열됩니다. 참조를 사용하면 DAM 사용자가 [!DNL Sites] 페이지와 [!DNL Assets]의 복합 자산에서 자산 사용을 추적할 수 있습니다. [연결된 자산 구성 및 사용](/help/assets/use-assets-across-connected-assets-instances.md)을 참조하십시오.

* [!DNL Dynamic Media] 이제  [!DNL Sites] 이미지 기반 핵심 구성 요소를 통해 기능에 액세스할 수 있습니다. 작성자는 웹 페이지를 만들 때 이미지 사전 설정, 스마트 자르기 및 이미지 수정자를 사용하도록 구성 요소를 빠르게 구성할 수 있습니다. [핵심 구성 요소 2.13.0 릴리스](https://github.com/adobe/aem-core-wcm-components/releases/tag/core.wcm.components.reactor-2.13.0)를 참조하십시오.

* [!DNL Experience Manager] 데스크탑 앱을 사용하면 데스크탑 앱 인터페이스에서 Windows 탐색기 또는 Mac Finder에서 파일을 드래그하여 파일과 폴더를 업로드할 수 있습니다. 데스크톱 앱](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html#upload-and-add-new-assets-to-aem)을 사용하여 [자산 추가를 참조하십시오.

## Adobe Experience Manager 상거래를 Cloud Service {#cloud-services-commerce}

### 새로운 기능 {#what-is-new-commerce}

* 최신 CIF 코어 구성 요소 버전 v1.6.0을 포함하는 CIF Venia 참조 사이트 - 2020.12.01. 자세한 내용은 [CIF Venia 참조 사이트](https://github.com/adobe/aem-cif-guides-venia/releases/tag/venia-2020.12.01)를 참조하십시오.

* CIF 코어 구성 요소 v1.6.0 릴리스되었습니다. 자세한 내용은 [CIF 핵심 구성 요소](https://github.com/adobe/aem-core-cif-components/releases/tag/core-cif-components-reactor-1.6.0)를 참조하십시오.

## Cloud Manager {#cloud-manager}

### 릴리스 날짜 {#release-date-cm}

2020년 12월 10일 Cloud Service으로 AEM의 Cloud Manager에 대한 릴리스 날짜가 2020.12.0.

### [!DNL Cloud Manager] {#what-is-new-cm}의 새로운 기능

* [SSL 인증서](/help/implementing/cloud-manager/managing-ssl-certifications/introduction.md) 및 [사용자 지정 도메인 이름](/help/implementing/cloud-manager/custom-domain-names/introduction.md)의 셀프 서비스 관리.

* [IP 허용 목록](/help/implementing/cloud-manager/ip-allow-lists/introduction.md)의 셀프 서비스 관리

* 업데이트된 **환경** 세부 사항 페이지에서 사용자 지정 도메인 이름 및 IP 허용 목록을 해당 환경에서 관리할 수 있습니다.

### 버그 수정 {#bug-fixes-cloud-manager}

* 결과를 해결하지 않고 코드 스캔 단계에서 오류가 발생한 경우가 있습니다.

* 환경 카드가 **추가** 단추를 일관되게 표시하지 않았습니다.

## 코드 리팩터링 도구 {#code-refactoring-tools}

### [!DNL Code Refactoring Tools] {#what-is-new-crt}의 새로운 기능

* 새로운 버전의 AIO-CLI 플러그인이 출시되었습니다. 이 플러그인의 최신 버전은 AEM Dispatcher Converter 및 Repository Modernizer에 대한 버그 수정을 포함하며 새로운 유틸리티인 Index Converter를 지원합니다. 이 플러그인에 대한 자세한 내용은 [통합 경험](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/refactoring-tools/unified-experience.html?lang=en#benefits)을 참조하십시오.

* 색인 변환기는 고객의 사용자 정의 OAK 색인 정의를 Cloud Service 호환 OAK 색인 정의로 AEM으로 변환하는 데 사용할 수 있는 유틸리티입니다. 자세한 내용은 [색인 변환기](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/index-converter)를 참조하십시오.

* 모든 OSGi 구성을 포함하는 별도의 패키지 `ui.config`을 만드는 [Repository Modernizer](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/repository-modernizer)에 새 기능이 추가되었습니다.

### 버그 수정 {#crt-bug-fixes}

* AEM Dispatcher Converter 및 Repository Modernizer 도구에서 수행한 몇 가지 버그 수정. [AEM Dispatcher Converter](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/dispatcher-converter) 및 [Repository Modernizer](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/repository-modernizer)를 참조하십시오.
