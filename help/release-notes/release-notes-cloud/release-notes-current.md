---
title: ' [!DNL Adobe Experience Manager] as a Cloud Service 최신 릴리스 정보'
description: ' [!DNL Adobe Experience Manager] as a Cloud Service 최신 릴리스 정보'
exl-id: a2d56721-502c-4f4e-9b72-5ca790df75c5
mini-toc-levels: 1
source-git-commit: 88506fd4538c55a880904ea37055eb97d4ae05b3
workflow-type: tm+mt
source-wordcount: '639'
ht-degree: 20%

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

의 릴리스 날짜 [!DNL Adobe Experience Manager] 로서의 [!DNL Cloud Service] 현재 릴리스(2022.6.0)는 2022년 6월 30일입니다.

다음 릴리스(2022.7.0)는 2022년 7월 28일에 예정되어 있습니다.

## 릴리스 비디오 {#release-video}

2022.6.0 릴리스에 추가된 기능에 대한 요약을 보려면 2022년 6월 릴리스 개요 비디오를 보십시오.

>[!VIDEO](https://video.tv.adobe.com/v/344308/?quality=12)

## [!DNL Experience Manager Sites] as a [!DNL Cloud Service] {#sites}

### [!DNL Sites]의 새로운 기능 {#sites-features}

* 새로운 [사용자 인터페이스](/help/headless/content-fragments/content-fragment-console.md) 이제 컨텐츠 관리자 및 컨텐츠 작성자가 헤드리스 사용 사례에서 효율적으로 관리(게시, 게시 취소, 복사, 이동 등의 작업 수행), 검색/필터를 수행하고 컨텐츠 조각을 만들 수 있습니다.

   ![컨텐츠 조각 콘솔](/help/release-notes/assets/cf-ui.png)

* 새로운 [목차 구성 요소](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/components/tableofcontents.html) 는 핵심 구성 요소뿐만 아니라 모든 구성 요소에서 작동하므로 컨텐츠 페이지에서 자동으로 ToCs 렌더링됩니다. 또한 서버 측에서 렌더링되고 디스패처에 의해 완전히 캐시되므로 로드하는 것도 효율적입니다.

## [!DNL Experience Manager Assets] 로서의 [!DNL Cloud Service] {#assets}

### [!DNL Assets]의 새로운 기능 {#assets-features}

Experience Manager Assets은 Adobe Sensei AI 기능을 사용하여 이제 [이미지의 색상을 구별하고 수집 시 자동으로 태그로 적용합니다](../../assets/color-tag-images.md). 이러한 태그는 이미지 색상 구성에 따라 향상된 검색 환경을 제공합니다. 이미지에 태그가 지정된 색상의 수를 1~40개 범위에서 구성할 수 있으므로 나중에 해당 색상을 기준으로 이미지를 검색할 수 있습니다.

## [!DNL Experience Manager Forms] 로서의 [!DNL Cloud Service] {#forms}

### [!DNL Forms]의 새로운 기능 {#forms-features}

* **[Microsoft® Power Automate와 적응형 Forms 통합](/help/forms/forms-microsoft-power-automate-integration.md)**: 이제 제출 시 Microsoft® Power Automated Cloud Flow를 실행하도록 적응형 양식을 구성할 수 있습니다. 구성된 적응형 양식은 캡처된 데이터, 첨부 파일 및 기록 문서를 Power Automatic Cloud Flow로 전송하여 처리합니다. Microsoft® Power Automate의 기능을 활용하여 사용자 정의 데이터 캡처 경험을 구축하고 캡처된 데이터를 중심으로 비즈니스 로직을 구축하고 고객 워크플로우를 자동화할 수 있습니다.

* **적응형 양식 만들기 마법사**: 비즈니스 사용자에게 친숙한 마법사를 사용하여 응용 Forms을 빠르게 작성할 수 있습니다. 이 마법사는 적응형 양식을 만들기 위해 사전 구성된 템플릿, 스타일 지정, 필드 및 제출 옵션을 쉽게 선택할 수 있도록 빠른 탭 탐색을 제공합니다.

   ![적응형 양식 만들기 마법사](/help/release-notes/assets/wizard.png)

## CIF 추가 기능 {#cloud-services-cif}

### 새로운 기능 {#what-is-new-cif}

* 새롭고 간편해진 개요를 위한 제품 조종실 속성 페이지

![제품 조종실 속성 개요](/help/assets/CIF/product_cockpit_properties_overview.png)

* I/O Runtime에서 타사 커넥터에 대한 향상된 호환성 및 견고성

* GQL 클라이언트 구성 덮어쓰기(예: 사용자 지정 캐싱 동작 설정)에 대한 지원이 개선되었습니다

* 이제 여러 상거래 종단점이 기본적으로 지원되며 Cloud Manager를 통해 구성할 수 있습니다. 자세한 내용은 CIF 블로그에서 확인할 수 있습니다 [여기](https://medium.com/adobetech/use-aem-as-a-cloud-service-with-multiple-adobe-commerce-systems-9295612a9554).


### 버그 수정 {#bug-fixes-cif}

* 다중 값 제품 선택기 필드에 두 번째 제품과 다른 제품이 잘못된 것으로 표시됩니다

* 구성 요소 뒤에 제품 선택기가 숨겨지는 경우가 있습니다

## 참조 데모 추가 기능 {#cloud-services-demos}

### 새로운 기능 {#what-is-new-demos}

* 제품 카탈로그, 장바구니, 체크아웃 및 myAccount를 제공하는 E2E 쇼핑 경험으로 WKND를 확장하는 새로운 WKND Content &amp; Commerce 템플릿입니다. 이 템플릿은 CIF 및 해당 CIF 핵심 구성 요소를 사용하므로 CIF 추가 기능을 설치해야 합니다. 자세한 내용은 CIF 블로그에서 확인할 수 있습니다 [여기](https://medium.com/adobetech/learn-how-to-create-a-shoppable-experience-with-the-new-wknd-reference-site-and-cif-b3b2c161f67e).

![WKND shop](/help/assets/CIF/wknd_shop.png)

![WKND pdp](/help/assets/CIF/wknd_pdp.png)

## [!DNL Experience Manager] as a [!DNL Cloud Service] Foundation {#foundation}

### 새로운 기능 {#what-is-new-foundation}

* 5월(2022.5.0) 릴리스 노트에서 언급한 대로, 복제 에이전트 관리 화면의 &quot;트리 추가&quot; 선택 사항 **배포** 탭이 제거되었습니다. 컨텐츠 계층 구조의 패키지를 대신 [게시 관리](/help/operations/replication.md#manage-publication) 또는 [컨텐츠 트리 게시](/help/operations/replication.md#manage-publication#publish-content-tree-workflow) 워크플로우.

## Cloud Manager {#cloud-manager}

[여기](/help/implementing/cloud-manager/release-notes-cloud-manager/release-notes-cm-current.md)에서 Cloud Manager 월별 릴리스의 전체 목록을 찾을 수 있습니다.

## 마이그레이션 도구 {#migration-tools}

마이그레이션 도구 릴리스의 전체 목록을 찾을 수 있습니다 [여기](/help/journey-migration/release-notes/release-notes-migration-tools-current.md).
