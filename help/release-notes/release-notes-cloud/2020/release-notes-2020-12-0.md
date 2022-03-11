---
title: ' [!DNL Adobe Experience Manager] as a Cloud Service 2020.12.0 릴리스의 릴리스 노트'
description: ' [!DNL Adobe Experience Manager] as a Cloud Service 2020.12.0 릴리스의 릴리스 노트'
exl-id: 16875180-1f23-477d-9d4d-e220998c4983
source-git-commit: aeee895e4a4b959125d08091619988d0ffa09ace
workflow-type: tm+mt
source-wordcount: '693'
ht-degree: 10%

---

# [!DNL Adobe Experience Manager] as a Cloud Service 릴리스 노트  {#release-notes}

다음 섹션에서는 다음에 대한 일반 릴리스 노트를 간략하게 설명합니다 [!DNL Experience Manager] as a Cloud Service.

## 릴리스 날짜 {#release-date}

에 대한 릴리스 날짜 [!DNL Adobe Experience Manager] as a Cloud Service은 2020년 12월 17일입니다.
다음 릴리스(2021.1.0)는 2021년 1월 28일에 있습니다.

## [!DNL Adobe Experience Manager Sites] as a Cloud Service {#sites}

* **[컨텐츠 조각 HTTP API](/help/assets/content-fragments/assets-api-content-fragments.md)**: HTTP API를 사용하여 컨텐츠 조각 변형을 추가/업데이트 및 삭제하는 기능을 추가합니다.

## [!DNL Adobe Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

* 통합 [!DNL Adobe InDesign Server] 이제 을(를) 사용할 수 있습니다. [!DNL Experience Manager] 로서의 [!DNL Cloud Service]. 프로세스 자동화를 제공합니다 [!DNL Adobe InDesign] 파일 사용 [!DNL Adobe InDesign Server] 스크립팅 및 사용자 사용 가능 [!DNL Assets] 템플릿 사용자 인터페이스를 사용하여 브로셔나 광고를 만들 수 있습니다. 전용 [!DNL InDesign Server] 호스팅 [!DNL Adobe Managed Services] 에 대해 지원됨 [!DNL Experience Manager as a Cloud Service]. <!-- TBD: Add link to article. -->

* [!DNL Experience Manager] 원격 사이트에서 자산을 사용할 때 자산 참조를 추적 및 표시하도록 가 개선되었습니다. [!DNL Experience Manager Sites] 연결된 자산 기능을 사용한 배포. 새로운 [!UICONTROL 참조] 자산의 탭 [!UICONTROL 속성] 이제 페이지에 자산의 로컬 및 원격 참조가 나열됩니다. 참조를 사용하면 DAM 사용자가 의 자산 사용을 추적할 수 있습니다. [!DNL Sites] 의 복합 자산인 페이지 및 [!DNL Assets]. 자세한 내용은 [연결된 자산 구성 및 사용](/help/assets/use-assets-across-connected-assets-instances.md).

* [!DNL Dynamic Media] 이제 [!DNL Sites] 이미지 기반 핵심 구성 요소. 작성자는 웹 페이지를 만들 때 이미지 사전 설정, 스마트 자르기 및 이미지 수정자 를 사용하도록 구성 요소를 빠르게 구성할 수 있습니다. 자세한 내용은 [코어 구성 요소 2.13.0 릴리스](https://github.com/adobe/aem-core-wcm-components/releases/tag/core.wcm.components.reactor-2.13.0).

* [!DNL Experience Manager] 데스크탑 앱을 사용하면 데스크탑 앱 인터페이스에서 Windows 탐색기 또는 Mac Finder의 파일을 드래그하여 파일과 폴더를 업로드할 수 있습니다. 자세한 내용은 [데스크탑 앱을 사용하여 자산 추가](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html#upload-and-add-new-assets-to-aem).

## Adobe Experience Manager Commerce as a Cloud Service {#cloud-services-commerce}

### 새로운 기능 {#what-is-new-commerce}

* 최신 CIF 코어 구성 요소 버전 v1.6.0이 포함된 CIF Venia 참조 사이트 - 2020.12.01이 출시되었습니다. 다음을 참조하십시오. [CIF Venia 참조 사이트](https://github.com/adobe/aem-cif-guides-venia/releases/tag/venia-2020.12.01) 자세한 내용

* CIF 코어 구성 요소 v1.6.0이 출시되었습니다. 자세한 내용은 [CIF 코어 구성 요소](https://github.com/adobe/aem-core-cif-components/releases/tag/core-cif-components-reactor-1.6.0) 자세한 내용

## Cloud Manager {#cloud-manager}

### 릴리스 날짜 {#release-date-cm}

AEM as a Cloud Service 2020.12.0의 Cloud Manager 릴리스 날짜는 2020년 12월 10일입니다.

### [!DNL Cloud Manager]의 새로운 기능 {#what-is-new-cm}

* 의 셀프 서비스 관리 [SSL 인증서](/help/implementing/cloud-manager/managing-ssl-certifications/introduction.md) 및 [사용자 지정 도메인 이름](/help/implementing/cloud-manager/custom-domain-names/introduction.md).

* 의 셀프 서비스 관리 [IP 허용 목록](/help/implementing/cloud-manager/ip-allow-lists/introduction.md).

* 업데이트됨 **환경** 이제 세부 사항 페이지에서 사용자가 자신의 환경에서 사용자 지정 도메인 이름 및 IP 허용 목록을 관리할 수 있습니다.

### 버그 수정 {#bug-fixes-cloud-manager}

* 결과를 제공하지 않고 코드 스캔 단계에서 일부 오류가 발생했습니다.

* 환경 카드가 일관되게 표시되지 않음 **추가** 버튼을 클릭합니다.

## 코드 리팩터링 도구 {#code-refactoring-tools}

### [!DNL Code Refactoring Tools]의 새로운 기능 {#what-is-new-crt}

* 새로운 버전의 AIO-CLI 플러그인이 출시되었습니다. 이 플러그인의 최신 버전에는 AEM Dispatcher Converter 및 Repository Modernizer에 대한 버그 수정이 포함되어 있으며 새로운 유틸리티인 Index Converter도 지원합니다. 자세한 내용은 [통합 경험](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/refactoring-tools/unified-experience.html?lang=en#benefits) 추가 정보

* Index Converter는 고객의 사용자 지정 OAK 색인 정의를 AEM as a Cloud Service 호환 OAK 색인 정의로 변환하는 데 사용할 수 있는 유틸리티입니다. 자세한 내용은 [인덱스 변환기](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/index-converter) 자세한 내용

* 에 추가된 새로운 기능 [Repository Modernizer](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/repository-modernizer) 별도의 패키지를 만드는 `ui.config` 모든 OSGi 구성을 포함합니다.

### 버그 수정 {#crt-bug-fixes}

* AEM Dispatcher Converter 및 Repository Modernizer 도구에서 수행한 몇 가지 버그 수정. 자세한 내용은 [AEM Dispatcher 변환기](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/dispatcher-converter) 및 [Repository Modernizer](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/repository-modernizer).

### 릴리스 날짜 {#release-date-ctt}

컨텐츠 전송 도구 v1.1.20의 릴리스 날짜는 2021년 1월 8일입니다.

### [!DNL Content Transfer Tool]의 새로운 기능 {#what-is-new-ctt}

* 이제 사용자는 CTT(컨텐츠 전송 도구) 사용자 인터페이스의 상태 아이콘을 마우스로 가리키면 액세스 토큰이 만료되었는지 확인할 수 있습니다. 또한 마이그레이션 세트 세부 사항 UI에 해당 Cloud Service 인스턴스에 연결할 수 없다는 알림을 받게 됩니다.

### 버그 수정 {#ctt-bug-fixes}

* 마이그레이션 세트에 대한 CTT(컨텐츠 전송 도구) 사용자 인터페이스 상태가 비활성 기간 후 지속되거나 변경되지 않았습니다. 이 문제가 해결되었습니다.
* 로그를 사용할 수 없는 경우 로그 보기 옵션을 비활성화했습니다. 이 문제가 해결되었으며 로그가 누락된 이유를 사용자에게 알리는 메시지가 추가되었습니다.
* 컨텐츠 전송 도구 사용자 인터페이스 상태가 표시됨 *실패* 사용자가 수집을 중지했을 때. 이 속성이 표시되도록 수정되었습니다 *중지됨* 을 가리키도록 업데이트하는 것이 좋습니다.
