---
title: ' [!DNL Adobe Experience Manager] as a Cloud Service의 2023.2.0 릴리스 정보입니다.'
description: ' [!DNL Adobe Experience Manager] as a Cloud Service의 2023.2.0 릴리스 정보입니다.'
source-git-commit: 937921e0310a659f52803de3d6895db8fcac4d2b
workflow-type: tm+mt
source-wordcount: '732'
ht-degree: 100%

---


# [!DNL Adobe Experience Manager] as a Cloud Service 2023.2.0 릴리스 정보 {#release-notes}

다음 섹션에서는 [!DNL Experience Manager] as a Cloud Service의 2023.2.0 버전 기능 릴리스 정보에 대해 간략히 소개합니다.

>[!NOTE]
>
>여기에서 2021, 2022 버전 등 이전 버전의 릴리스 정보로 이동할 수 있습니다.
>
>[!DNL Experience Manager] as a Cloud Service의 향후 기능 활성화에 대해 알아보려면 [Experience Manager 릴리스 로드맵](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap.html?lang=ko-KR)을 살펴보십시오.

>[!NOTE]
>
>릴리스와 직접적으로 관련되지 않는 설명서 업데이트의 세부 정보는 [설명서 업데이트](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html)를 참조하십시오.

## 릴리스 일자 {#release-date}

[!DNL Adobe Experience Manager] as a [!DNL Cloud Service] 현재 기능 릴리스(2023.2.0)의 릴리스 일자는 2023년 4월 12일입니다. 다음 기능 릴리스(2023.4.0)는 2023년 6월 7일에 예정되어 있습니다.

## 릴리스 비디오 {#release-video}

2023년 2월 릴리스 개요 비디오를 통해 2023.2.0 릴리스에 추가된 기능에 대한 간단한 요약을 살펴보십시오.

>[!VIDEO](https://video.tv.adobe.com/v/3416885/?quality=12)

## [!DNL Experience Manager Sites] as a [!DNL Cloud Service] {#sites}

### [!DNL Experience Manager Sites]의 새로운 기능 프리릴리스 {#prerelease-sites}

* 콘텐츠 조각을 JSON 오퍼로 AEM as a Cloud Service에서 Adobe Target으로 내보냅니다.
* 내부 캐싱 향상과 함께 GraphQL 페이지 매김 및 정렬에 대한 지원은 이제 복잡한 GraphQL 쿼리 및 필터를 사용하여 AEM에서 대규모 콘텐츠 세트를 가져올 때 분리된 클라이언트 애플리케이션의 성능을 개선하는 데 도움이 됩니다.

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### [!DNL Assets]의 새로운 기능 {#assets-features}

* 새로운 프로토콜(DASH - Dynamic Adaptive Streaming over HTTP)이 Dynamic Media 비디오 게재(CMAF 활성화)에서 적응형 스트리밍을 위해 시작되었습니다.
   * 적응형 스트리밍(DASH/HLS)은 비디오에 대한 더 나은 최종 사용자 시청 경험 보장
   * DASH는 적응형 비디오 스트리밍을 위한 국제 표준 프로토콜이며 업계에서 널리 채택되고 있음
   * NA에서 사용 가능, 지원 티켓을 통해 활성화, 곧 APAC, EMEA에서 제공 예정

* WebP 이미지에 대한 지원이 추가되어 자동으로 메타데이터를 추출하고 썸네일 및 사용자 정의 렌디션을 생성합니다. 이제 이러한 파일에 대해 스마트 태그 및 스마트 자르기 기능도 지원됩니다.

## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

### [!DNL Forms] 프리릴리스에서 사용 가능한 새로운 기능 {#new-features-available-in-channel}

* **[데이터 캡처 핵심 구성 요소를 사용하여 적응형 양식 작성](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html?lang=ko)**: [적응형 양식 편집기를 사용](/help/forms/creating-adaptive-form-core-components.md)하여 표준화된 데이터 캡처 구성 요소(핵심 구성 요소)를 기반으로 양식을 만듭니다. 이 구성 요소는 맞춤화 기능을 제공하고, 개발 시간을 단축하고, 유지 관리 비용을 줄여 디지털 등록 경험을 개선합니다.

* **[핵심 구성 요소 기반 적응형 양식의 스타일 유지를 위한 프론트엔드 파이프라인 지원](/help/forms/using-themes-in-core-components.md)**: 프론트엔드 파이프라인을 통해 핵심 구성 요소 기반 적응형 양식에 맞는 표준화된 BEM 기반의 테마를 배포하여 양식의 디자인을 개선하고 조직의 브랜드 승인 디자인 지침을 준수합니다.

* **[핵심 구성 요소 기반 적응형 양식의 기록 문서 만들기](/help/forms/generate-document-of-record-core-components.md)**: 인쇄 또는 문서 형식으로 보존이나 최종 사용자 참조를 위해, 핵심 구성 요소를 사용하여 작성한 적응형 양식의 제출 데이터를 포함하는 기록 문서를 만듭니다.

![https://www.aemcomponents.dev/](/help/forms/assets/sample-core-components-based-adaptive-form.png)

* **[적응형 양식을 템플릿으로 저장하는 기능으로 효율적인 양식 작성](/help/forms/template-editor.md#save-an-adaptive-form-as-template-saving-adaptive-form-as-template)**: 빠른 재사용을 위해 기존 브랜드 승인 양식을 양식 템플릿으로 저장하여 양식 개발을 촉진하고 표준화합니다.

* **[AEM Forms를 JDBC 지원 데이터베이스에 연결](/help/forms/configure-data-sources.md#configure-relational-database-configure-relational-database)**: REST API를 통해 노출할 필요 없이 JDBC 프로토콜을 사용하여 AEM Cloud Service에서 직접 엔터프라이즈 데이터베이스에 연결합니다.

* **[Open API 3.0을 사용하여 REST 엔드포인트와 통합](/help/forms/configure-data-sources.md#configure-restful-services-open-api-specification-version-20-configure-restful-services-swagger-version30)**: 양식 데이터 모델을 사용하여 데이터를 저장하고 가져오기 위해 Open API 3.0을 지원하는 기록 시스템에 원활하게 통합됩니다.

* **[검토 목적으로 적응형 양식 공유](/help/forms/create-reviews-forms.md)**: 적응형 양식 검토 메커니즘을 사용하여 한 명 이상의 검토자가 양식을 검토할 수 있습니다.


### [!DNL Forms] 프리릴리스의 기능 {#prerelease-features-forms}

* **[적응형 양식을 Microsoft SharePoint 및 Microsoft OneDrive에 제출](/help/forms/configuring-submit-actions.md)**: 비즈니스 사용자 민첩성을 개선하여 새로운 양식을 빠르게 시작하고, Microsoft SharePoint 사이트 또는 OneDrive 폴더와 같이 일상적으로 사용하는 도구에 제출된 데이터를 저장합니다.

![적응형 양식을 Microsoft SharePoint 및 Microsoft OneDrive에 제출](/help/forms/assets/onedrive-and-sharepoint.jpg)


## Headless 적응형 양식 얼리 어답터 프로그램 {#forms-early-adopter}

Headless 적응형 양식을 사용하여 개발자가 기존의 그래픽 사용자 인터페이스가 아닌 API를 통해 액세스하고 상호 작용할 수 있는 대화형 양식을 만들고, 게시하고, 관리할 수 있습니다. Headless 적응형 양식은 다음에 도움이 됩니다.

* 선택한 프로그래밍 언어로 고품질 다중 채널 양식 작성
* 양식을 데스크탑 및 모바일 앱, 웹 사이트 및 채팅 애플리케이션에 기본적으로 통합
* 양식 애플리케이션과 함께 독점 UI 구성 요소 재사용
* Adobe Experience Manager Forms의 기능 활용

공식 이메일 ID에서 aem-forms-headless@adobe.com으로 이메일을 보내 얼리 어답터 프로그램에 참여할 수 있습니다.

## 유지 관리 릴리스 정보 {#maintenance}

[ 여기](/help/release-notes/maintenance/latest.md)에서 최신 유지 관리 릴리스 정보를 확인할 수 있습니다.

## Cloud Manager {#cloud-manager}

[여기](/help/implementing/cloud-manager/release-notes/current.md)에서 Cloud Manager 월별 릴리스의 전체 목록을 찾을 수 있습니다.

## 마이그레이션 도구 {#migration-tools}

[여기](/help/journey-migration/release-notes/release-notes-migration-tools-current.md)에서 마이그레이션 도구의 전체 목록을 찾을 수 있습니다.
