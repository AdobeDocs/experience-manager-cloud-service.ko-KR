---
title: ' [!DNL Adobe Experience Manager] as a Cloud Service의 2022.5.0 릴리스 정보.'
description: ' [!DNL Adobe Experience Manager] as a Cloud Service의 2022.5.0 릴리스 정보.'
source-git-commit: d6038920a5866c19a94980cc14fa46dec48daf51
workflow-type: tm+mt
source-wordcount: '805'
ht-degree: 18%

---


# [!DNL Adobe Experience Manager] as a Cloud Service 최신 릴리스 정보 {#release-notes}

다음 섹션에서는 [!DNL Experience Manager] as a Cloud Service의 최신 버전 일반 릴리스 정보에 대해 간략히 소개합니다.

>[!NOTE]
>
>여기에서 2020, 2021 버전 등 이전 버전의 릴리스 정보로 이동할 수 있습니다.

>[!NOTE]
>
>릴리스와 직접적으로 관련되지 않는 설명서 업데이트의 세부 정보는 [설명서 업데이트](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html)를 참조하십시오.

## 릴리스 날짜 {#release-date}

의 릴리스 날짜 [!DNL Adobe Experience Manager] 로서의 [!DNL Cloud Service] 현재 릴리스(2022.5.0)는 2022년 6월 9일입니다.
다음 릴리스(2022.6.0)는 2022년 6월 30일에 예정되어 있습니다.

## 릴리스 비디오 {#release-video}

2022.5.0 릴리스에 추가된 기능에 대한 요약을 보려면 2022년 5월 릴리스 개요 비디오를 보십시오.

>[!VIDEO](https://video.tv.adobe.com/v/343321/?quality=12)

## [!DNL Experience Manager Sites] as a [!DNL Cloud Service] {#sites}

### [!DNL Sites] 프리릴리스 채널에서 사용할 수 있는 새로운 기능 {#prerelease-features-sites}

* 다양한 GraphQL 기능
* A [새 콘솔](/help/sites-cloud/administering/content-fragments/content-fragments-console.md) 컨텐츠 조각의 헤드리스 사용을 위해 최적화되었습니다.

## [!DNL Experience Manager Assets] 로서의 [!DNL Cloud Service] {#assets}

### [!DNL Assets]의 새로운 기능 {#assets-features}

* [Dynamic Media 스마트 이미징](https://medium.com/adobetech/one-solution-fits-all-smart-imaging-with-aem-dynamic-media-be690b62df9f) 이제 AVIF 파일 형식을 지원합니다. AVIF를 사용하면 WebP에 비해 20% 더 큰 크기를 줄일 수 있으므로 Google Core Web Vital(가장 큰 내용물 페인트)을 더욱 향상시킬 수 있습니다. 총 AVIF는 JPEG에 비해 최대 41%의 평균 크기 감소를 제공합니다(일부 이미지에서 76%까지 높이).

* [!UICONTROL Experience Manager Assets Brand Portal] 이제 자동 작업을 12시간마다 실행하여 AEM에 게시된 모든 Brand Portal 자산을 삭제합니다. 따라서 폴더 크기를 임계값 제한 이하로 유지하려면 기여도 폴더에서 자산을 수동으로 삭제할 필요가 없습니다. 자세한 내용은 [Experience Manager Assets Brand Portal의 새로운 기능](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/introduction/whats-new.html).

### [!DNL Assets] 프리릴리스 채널에서 사용할 수 있는 새로운 기능 {#prerelease-features-assets}

Experience Manager Assets은 Adobe Sensei AI 기능을 사용하여 이제 [이미지의 색상을 구별하고 수집 시 자동으로 태그로 적용합니다](/help/assets/color-tag-images.md). 이러한 태그는 이미지 색상 구성에 따라 향상된 검색 환경을 제공합니다. 이미지에 태그가 지정된 색상의 수를 1~40개 범위에서 구성할 수 있으므로 나중에 해당 색상을 기준으로 이미지를 검색할 수 있습니다.


## [!DNL Experience Manager Forms] 로서의 [!DNL Cloud Service] {#forms}

### [!DNL Forms] 프리릴리스 채널에서 사용할 수 있는 새로운 기능 {#prerelease-features-forms}

* **Microsoft® Power Automate와 적응형 Forms 통합**: 이제 제출 시 Microsoft® Power Automated Cloud Flow를 실행하도록 적응형 양식을 구성할 수 있습니다. 구성된 적응형 양식은 캡처된 데이터, 첨부 파일 및 기록 문서를 Power Automatic Cloud Flow로 전송하여 처리합니다. Microsoft® Power Automate의 기능을 활용하여 사용자 정의 데이터 캡처 경험을 구축하고 캡처된 데이터를 중심으로 비즈니스 로직을 구축하고 고객 워크플로우를 자동화할 수 있습니다.

* **적응형 양식 만들기 마법사**: 비즈니스 사용자에게 친숙한 마법사를 사용하여 응용 Forms을 빠르게 작성할 수 있습니다. 이 마법사는 적응형 양식을 만들기 위해 사전 구성된 템플릿, 스타일 지정, 필드 및 제출 옵션을 쉽게 선택할 수 있도록 빠른 탭 탐색을 제공합니다.

   ![적응형 양식 만들기 마법사](/help/release-notes/assets/wizard.png)

## CIF 추가 기능 {#cloud-services-cif}

### 새로운 기능 {#what-is-new-cif}

* 제품 조종실에 대한 빠른 액세스: 사이트 편집기에서 한 번의 클릭으로 전체 세부 제품 정보에 쉽게 액세스할 수 있습니다

   ![wishlist 사용](/help/assets/CIF/enable-wishlist.png)

* 추가 마케팅 상거래 구성 요소에 대한 지원: 장바구니에 추가 및 wishlist 호출에 대한 작업을 표시하도록 구성 요소를 구성할 수 있습니다

   ![제품 조종실에 대한 사이트 편집기 바로 가기](/help/assets/CIF/sites-editor-shortcut-to-cockpit.png)


## [!DNL Experience Manager] as a [!DNL Cloud Service] Foundation {#foundation}

### 새로운 기능 {#what-is-new-foundation}

* 복제 에이전트 관리 화면의 &quot;트리 추가&quot; 옵션 **배포 탭**&#x200B;이전에 더 이상 사용되지 않음으로 발표된 는 2022년 6월 20일에 제거되거나 곧 그 이후에 제거됩니다. 컨텐츠 계층 구조의 패키지를 대신 [게시 관리](/help/operations/replication.md#manage-publication) 또는 [컨텐츠 트리 게시 워크플로우](/help/operations/replication.md#publish-content-tree-workflow).

* 10MB보다 큰 컨텐츠 패키지(바이너리를 포함하지 않는 속성이 있는 노드)를 배포하기 위해 복제 에이전트 관리 화면 또는 복제 API를 사용하는 것은 더 이상 사용되지 않으며, 2022년 9월 12일 또는 그 다음 단계에 적용됩니다. 대신, [게시 관리](/help/operations/replication.md#manage-publication) 또는 [컨텐츠 트리 게시 워크플로우](/help/operations/replication.md#publish-content-tree-workflow) 이 큰 컨텐츠 패키지를 복제하려면 를 사용해야 합니다. 7월에 복제 에이전트 관리 화면에 경고 메시지가 표시됩니다 **배포 탭** 복제 API를 사용하여 이러한 큰 컨텐츠 패키지를 복제할 때마다 이러한 큰 컨텐츠 패키지 및 AEM 오류 로그도 복제하려는 경우 9월에는 경고가 오류로 대체됩니다. 그에 따라 프로세스를 조정하십시오.

### [!DNL Experience Manager] 프리릴리스 채널에서 사용할 수 있는 새로운 기능 {#prerelease-features-foundation}

* AEM as a Cloud Service은 이제 통합 셸과 통합되어 사용자 경험을 향상하고 다른 모든 Experience Cloud 애플리케이션과 통합할 수 있습니다. 을(를) 참조하십시오. [통합 셸의 AEM as a Cloud Service](/help/overview/aem-cloud-service-on-unified-shell.md) 자세한 내용

## [!DNL Experience Manager] 로서의 [!DNL Cloud Service] 기초 보안 {#foundation-security}

### TLS 1.0, 1.1 사용 중단

2022년 6월 30일부터 Experience Manager as a Cloud Service은 보다 안전한 네트워크 통신 및 사용자 시스템과의 데이터 교환을 필요로 합니다. AEM은 TLS(전송 계층 보안), 1.2 프로토콜만 사용합니다. 이전 TLS 버전 1.0 및 1.1은 더 이상 사용되지 않습니다.

이전 버전의 TLS를 1.0, 1.1로 계속 사용하는 경우 Experience Manager as a Cloud Service에 대한 액세스 권한을 잃을 수 있습니다.

## Cloud Manager {#cloud-manager}

[여기](/help/implementing/cloud-manager/release-notes-cloud-manager/release-notes-cm-current.md)에서 Cloud Manager 월별 릴리스의 전체 목록을 찾을 수 있습니다.

## 마이그레이션 도구 {#migration-tools}

마이그레이션 도구 릴리스의 전체 목록을 찾을 수 있습니다 [여기](/help/journey-migration/release-notes/release-notes-migration-tools-current.md).
