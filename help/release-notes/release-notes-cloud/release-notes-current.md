---
title: ' [!DNL Adobe Experience Manager] as a Cloud Service 최신 릴리스 정보'
description: ' [!DNL Adobe Experience Manager] as a Cloud Service 최신 릴리스 정보'
mini-toc-levels: 1
source-git-commit: 34313a984b8ddb76211ed97dd11c437cbefa90c2
workflow-type: tm+mt
source-wordcount: '733'
ht-degree: 33%

---


# [!DNL Adobe Experience Manager] as a Cloud Service 최신 릴리스 정보 {#release-notes}

다음 섹션에서는 [!DNL Experience Manager] as a Cloud Service의 최신 버전 기능 릴리스 정보에 대해 간략히 소개합니다.

>[!NOTE]
>
>여기에서 2021, 2022 버전 등 이전 버전의 릴리스 정보로 이동할 수 있습니다.
>
>[!DNL Experience Manager] as a Cloud Service의 향후 기능 활성화에 대해 알아보려면 [Experience Manager 릴리스 로드맵](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap.html?lang=ko-KR)을 살펴보십시오.

>[!NOTE]
>
>릴리스와 직접적으로 관련되지 않는 설명서 업데이트의 세부 정보는 [설명서 업데이트](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html)를 참조하십시오.

## 릴리스 일자 {#release-date}

의 릴리스 날짜 [!DNL Adobe Experience Manager] 로서의 [!DNL Cloud Service] 현재 기능 릴리스(2023.2.0)는 2023년 4월 12일입니다. 다음 기능 릴리스(2023.4.0)는 2023년 5월 4일에 제공될 예정입니다.

## 릴리스 비디오 {#release-video}

2023.2.0 릴리스에 추가된 기능에 대한 요약을 보려면 2023년 2월 릴리스 개요 비디오를 보십시오.

>[!VIDEO](https://video.tv.adobe.com/v/3416885/?quality=12)

## [!DNL Experience Manager Sites] as a [!DNL Cloud Service] {#sites}

### [!DNL Experience Manager Sites]의 새로운 기능 전매 {#prerelease-sites}

* AEM as a cloud service에서 컨텐츠 조각을 JSON 오퍼로 Adobe으로 내보냅니다.
* 이제 복잡한 GraphQL 쿼리 및 필터를 사용하여 AEM에서 큰 콘텐츠 세트를 가져올 때 GraphQL 페이지 매김 및 정렬 기능과 내부 캐싱 개선 사항을 지원합니다.

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### [!DNL Assets]의 새로운 기능 {#assets-features}

* Dynamic Media 비디오 게재에서 적응형 스트리밍을 위해(CMAF가 활성화된 경우) 새로운 프로토콜(DASH - HTTP를 통한 동적 적응형 스트리밍) 지원을 시작합니다.
   * 응용 스트리밍(DASH/HLS)을 사용하면 비디오에 대한 최종 사용자 보기 환경을 향상시킬 수 있습니다
   * DASH는 응용 비디오 스트리밍을 위한 국제 표준 프로토콜이며 업계에서 널리 사용되고 있습니다
   * 지원 티켓을 통해 활성화될 수 있는 NA에서 제공되고, APAC, EMEA에서 곧 제공될 예정입니다

* 메타데이터를 자동으로 추출하고, 축소판 및 사용자 정의 렌디션을 생성하는 WebP 이미지에 대한 지원을 추가했습니다. 스마트 태그 및 스마트 자르기 기능도 이제 이러한 파일에 대해 지원됩니다.

## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

### [!DNL Forms] 프리릴리스에서 사용 가능한 새로운 기능 {#new-features-available-in-channel}

* **[데이터 캡처 핵심 구성 요소를 사용하여 적응형 양식 작성](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html?lang=ko)**: [적응형 양식 편집기를 사용](/help/forms/creating-adaptive-form-core-components.md)하여 표준화된 데이터 캡처 구성 요소(핵심 구성 요소)를 기반으로 양식을 만듭니다. 이 구성 요소는 맞춤화 기능을 제공하고, 개발 시간을 단축하고, 유지 관리 비용을 줄여 디지털 등록 경험을 개선합니다.

* **[적응형 Forms 기반의 코어 구성 요소 스타일을 위한 프런트 엔드 파이프라인 지원](/help/forms/using-themes-in-core-components.md)**: Frontend Deployment 파이프라인과 함께 배포하여 핵심 구성 요소 기반의 적응형 Forms에 대한 표준화된 BEM 기반 테마를 활용하여 양식의 모양과 느낌을 높이고 조직이 브랜드 승인된 디자인 지침에 맞게 조정할 수 있습니다.

* **[적응형 Forms 기반의 핵심 구성 요소에 대한 기록 문서 생성](/help/forms/generate-document-of-record-core-components.md)**: 인쇄 또는 문서 형식으로 최종 사용자를 위한 아카이브 또는 참조에 핵심 구성 요소를 사용하여 작성된 적응형 Forms에 대해 제출된 데이터가 포함된 레코드 문서를 만듭니다.

![https://www.aemcomponents.dev/](/help/forms/assets/sample-core-components-based-adaptive-form.png)

* **[적응형 양식을 템플릿으로 저장 기능을 사용하여 효율적인 양식 작성](/help/forms/template-editor.md#save-an-adaptive-form-as-template-saving-adaptive-form-as-template)**: 빠른 재사용을 위해 기존의 브랜드 승인 양식을 양식 템플릿으로 저장하여 양식 개발을 신속하고 표준화합니다.

* **[AEM Forms을 JDBC 지원 데이터베이스에 연결](/help/forms/configure-data-sources.md#configure-relational-database-configure-relational-database)**: REST API를 통해 표시하지 않고 JDBC 프로토콜을 사용하여 AEM Cloud 서비스에서 바로 엔터프라이즈 데이터베이스에 연결합니다.

* **[Open API 3.0을 사용하여 REST 종단점과 통합](/help/forms/configure-data-sources.md#configure-restful-services-open-api-specification-version-20-configure-restful-services-swagger-version30)**: 양식 데이터 모델을 사용하여 데이터를 저장하고 가져오기 위해 Open API 3.0을 지원하는 레코드 시스템에 원활하게 통합됩니다.

* **[검토 목적으로 적응형 양식 공유](/help/forms/create-reviews-forms.md)**: 적응형 양식 검토 메커니즘을 사용하여 한 명 이상의 검토자가 양식을 검토할 수 있습니다.


### 의 기능 [!DNL Forms] 사전 릴리스 {#prerelease-features-forms}

* **[Microsoft SharePoint 및 Microsoft OneDrive에 적응형 Forms 제출](/help/forms/configuring-submit-actions.md)**: 비즈니스 사용자 민첩성을 개선하여 새로운 양식을 빠르게 시작하고 Microsoft SharePoint 사이트 또는 OneDrive 폴더와 같이 사용하는 일상 도구에 제출된 데이터를 저장합니다.

![Microsoft SharePoint 및 Microsoft OneDrive에 적응형 Forms 제출](/help/forms/assets/onedrive-and-sharepoint.jpg)


## 헤드리스 적응형 Forms 얼리어답터 프로그램 {#forms-early-adopter}

헤드리스 적응형 Forms을 사용하여 개발자가 기존 그래픽 사용자 인터페이스를 통해서가 아니라 API를 통해 액세스 및 상호 작용할 수 있는 대화형 양식을 만들고, 게시하고, 관리할 수 있도록 하십시오. 헤드리스 적응형 양식은 다음과 같은 이점을 제공합니다.

* 원하는 프로그래밍 언어로 고품질 다중 채널 양식 작성
* 데스크탑과 모바일 앱, 웹 사이트 및 채팅 애플리케이션에 양식 통합
* 양식 애플리케이션에서 전용 UI 구성 요소 재사용
* Adobe Experience Manager Forms의 강력한 기능 활용

공식 이메일 ID에서 aem-forms-headless@adobe.com으로 이메일을 보내 얼리어답터 프로그램에 참가할 수 있습니다.

## 유지 관리 릴리스 정보 {#maintenance}

[ 여기](/help/release-notes/maintenance/latest.md)에서 최신 유지 관리 릴리스 정보를 확인할 수 있습니다.

## Cloud Manager {#cloud-manager}

[여기](/help/implementing/cloud-manager/release-notes/current.md)에서 Cloud Manager 월별 릴리스의 전체 목록을 찾을 수 있습니다.

## 마이그레이션 도구 {#migration-tools}

[여기](/help/journey-migration/release-notes/release-notes-migration-tools-current.md)에서 마이그레이션 도구의 전체 목록을 찾을 수 있습니다.
