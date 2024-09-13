---
title: ' [!DNL Adobe Experience Manager] as a Cloud Service의 2020.12.0 릴리스 정보입니다.'
description: ' [!DNL Adobe Experience Manager] as a Cloud Service의 2020.12.0 릴리스 정보입니다.'
exl-id: 16875180-1f23-477d-9d4d-e220998c4983
feature: Release Information
role: Admin
source-git-commit: 64344b9b2cce8d7c7f05d3e5ba94049346308a9d
workflow-type: tm+mt
source-wordcount: '657'
ht-degree: 9%

---

# as a Cloud Service [!DNL Adobe Experience Manager]에 대한 릴리스 정보 {#release-notes}

as a Cloud Service 다음 섹션에서는 [!DNL Experience Manager]에 대한 일반 릴리스 노트를 간략하게 설명합니다.

## 릴리스 일자 {#release-date}

[!DNL Adobe Experience Manager] as a Cloud Service 2020.12.0의 릴리스 날짜는 2020년 12월 17일입니다.
다음 릴리스(2021.1.0) 날짜는 2021년 1월 28일입니다.

## as a Cloud Service [!DNL Adobe Experience Manager Sites] {#sites}

* **[콘텐츠 조각 HTTP API](/help/assets/content-fragments/assets-api-content-fragments.md)**: HTTP API를 사용하여 콘텐츠 조각 변형을 추가/업데이트 및 삭제하는 기능을 추가합니다.

## [!DNL Adobe Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

* 이제 [!DNL Experience Manager]에서 [!DNL Cloud Service](으)로 [!DNL Adobe InDesign Server]과(와) 통합할 수 있습니다. [!DNL Adobe InDesign Server] 스크립팅을 사용하여 [!DNL Adobe InDesign] 파일을 자동으로 처리할 수 있으며 [!DNL Assets] 템플릿 사용자 인터페이스를 사용하여 브로슈어나 광고를 만들 수 있습니다. [!DNL Adobe Managed Services]에서 호스팅하는 [!DNL InDesign Server]만 [!DNL Experience Manager as a Cloud Service]에 대해 지원됩니다. <!-- TBD: Add link to article. -->

* 연결된 Assets 기능을 사용하여 원격 [!DNL Experience Manager Sites] 배포에 자산을 사용할 때 자산 참조를 추적 및 표시하도록 [!DNL Experience Manager]이(가) 개선되었습니다. 이제 자산의 [!UICONTROL 속성] 페이지에 있는 새 [!UICONTROL 참조] 탭에 자산의 로컬 및 원격 참조가 나열됩니다. 참조를 사용하면 DAM 사용자가 [!DNL Sites]페이지 및 [!DNL Assets]의 복합 에셋에서 에셋 사용을 추적할 수 있습니다. [연결된 Assets 구성 및 사용](/help/assets/use-assets-across-connected-assets-instances.md)을 참조하세요.

* 이제 AEM [!DNL Sites] 이미지 기반 핵심 구성 요소를 통해 [!DNL Dynamic Media] 기능에 액세스할 수 있습니다. 작성자는 웹 페이지를 만들 때 이미지 사전 설정, 스마트 자르기 및 이미지 수정자를 사용하도록 구성 요소를 빠르게 구성할 수 있습니다. [핵심 구성 요소 2.13.0 릴리스](https://github.com/adobe/aem-core-wcm-components/releases/tag/core.wcm.components.reactor-2.13.0)를 참조하십시오.

* [!DNL Experience Manager] 데스크톱 앱을 사용하면 데스크톱 앱 인터페이스에서 Windows 탐색기 또는 Mac Finder의 파일을 끌어 놓아 파일과 폴더를 업로드할 수 있습니다. [데스크톱 앱을 사용하여 자산 추가](https://experienceleague.adobe.com/en/docs/experience-manager-desktop-app/using/using#upload-and-add-new-assets-to-aem)를 참조하세요.

## Adobe Experience Manager Commerce as a Cloud Service {#cloud-services-commerce}

### 새로운 기능 {#what-is-new-commerce}

* 최신 CIF 핵심 구성 요소 버전 v1.6.0이 포함된 CIF Venia 참조 사이트 - 2020.12.01이 릴리스되었습니다. 자세한 내용은 [CIF Venia 참조 사이트](https://github.com/adobe/aem-cif-guides-venia/releases/tag/venia-2020.12.01)를 참조하십시오.

* CIF 코어 구성 요소 v1.6.0이 릴리스되었습니다. 자세한 내용은 [CIF 핵심 구성 요소](https://github.com/adobe/aem-core-cif-components/releases/tag/core-cif-components-reactor-1.6.0)를 참조하십시오.

## Cloud Manager {#cloud-manager}

### 릴리스 날짜 {#release-date-cm}

Adobe Experience Manager(AEM as a Cloud Service) 2020.12.0의 Cloud Manager 릴리스 일자는 2020년 12월 10일입니다.

### [!DNL Cloud Manager]의 새로운 기능 {#what-is-new-cm}

* [SSL 인증서](/help/implementing/cloud-manager/managing-ssl-certifications/introduction-to-ssl-certificates.md) 및 [사용자 정의 도메인 이름 소개](/help/implementing/cloud-manager/custom-domain-names/introduction.md)의 셀프 서비스 관리.

* [IP 허용 목록](/help/implementing/cloud-manager/ip-allow-lists/introduction.md)의 셀프서비스 관리

* 업데이트된 **환경** 세부 정보 페이지에서 이제 사용자가 해당 환경의 사용자 지정 허용 목록 이름 및 IP 도메인을 관리할 수 있습니다.

### 버그 수정 {#bug-fixes-cloud-manager}

* 코드 스캔 단계에서 결과를 제공하지 않고 일부 오류가 발생하는 문제가 해결됩니다.

* 환경 카드에 **추가** 단추가 일관되게 표시되지 않았습니다.

## 코드 리팩터링 도구 {#code-refactoring-tools}

### [!DNL Code Refactoring Tools]의 새로운 기능 {#what-is-new-crt}

* 새로운 버전의 AIO-CLI 플러그인이 출시되었습니다. 이 플러그인의 최신 버전에는 AEM Dispatcher Converter 및 Repository Modernizer에 대한 버그 수정이 포함되어 있으며 새 유틸리티인 Index Converter도 지원합니다. 이 플러그인에 대한 자세한 내용은 [통합 경험](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/migration-journey/refactoring-tools/unified-experience#benefits)을 참조하세요.

* Index Converter는 고객의 사용자 지정 Oak 색인 정의를 AEM as a Cloud Service과 호환되는 Oak 색인 정의로 변환하는 데 사용할 수 있는 유틸리티입니다. 자세한 내용은 [인덱스 변환기](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/index-converter)를 참조하십시오.

* 모든 OSGi 구성을 포함하는 별도의 패키지 `ui.config`을(를) 만드는 [Repository Modernizer](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/repository-modernizer)에 새 기능이 추가되었습니다.

### 버그 수정 {#crt-bug-fixes}

* AEM Dispatcher Converter 및 Repository Modernizer 도구에서 몇 가지 버그 수정이 수행되었습니다. [AEM Dispatcher 변환기](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/dispatcher-converter) 및 [Repository Modernizer](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/repository-modernizer)를 참조하십시오.

### 릴리스 일자 {#release-date-ctt}

컨텐츠 전송 도구 v1.1.20의 릴리스 날짜는 2021년 1월 8일입니다.

### [!DNL Content Transfer Tool]의 새로운 기능 {#what-is-new-ctt}

* 이제 사용자는 CTT(콘텐츠 전송 도구) 사용자 인터페이스의 상태 아이콘을 마우스로 가리키면 액세스 토큰이 만료되었는지 확인할 수 있습니다. 또한 마이그레이션 세트 세부 정보 UI에서 Cloud Service 인스턴스에 연결할 수 없다는 알림이 표시됩니다.

### 버그 수정 {#ctt-bug-fixes}

* 마이그레이션 세트에 대한 CTT(Content Transfer Tool) 사용자 인터페이스 상태가 유지되지 않고 비활성 기간 후 변경되었습니다. 이 문제는 이제 수정되었습니다.
* 로그를 사용할 수 없는 경우 로그를 보는 옵션이 비활성화되었습니다. 이제 이 문제가 해결되었으며 로그가 누락된 이유를 사용자에게 알리기 위해 메시징이 추가되었습니다.
* 사용자가 수집을 중지할 때 콘텐츠 전송 도구 사용자 인터페이스 상태가 *FAILED*&#x200B;로 표시되었습니다. 이 문제는 이제 *STOPPED*&#x200B;을(를) 대신 표시하도록 수정되었습니다.
