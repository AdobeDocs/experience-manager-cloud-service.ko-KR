---
title: ' [!DNL Adobe Experience Manager] as a Cloud Service 최신 릴리스 정보'
description: ' [!DNL Adobe Experience Manager] as a Cloud Service 최신 릴리스 정보'
exl-id: a2d56721-502c-4f4e-9b72-5ca790df75c5
mini-toc-levels: 1
source-git-commit: e4346c4fb8c8d29d3a2772a6db8ba408b287d1bf
workflow-type: tm+mt
source-wordcount: '1032'
ht-degree: 22%

---


# [!DNL Adobe Experience Manager] as a Cloud Service 최신 릴리스 정보 {#release-notes}

다음 섹션에서는 의 현재(최신) 버전에 대한 기능 릴리스 노트를 간략하게 설명합니다 [!DNL Experience Manager] as a Cloud Service.

>[!NOTE]
>
>여기에서 2021, 2022 버전 등 이전 버전의 릴리스 정보로 이동할 수 있습니다.
>
>다음을 살펴보십시오. [Experience Manager 릴리스 로드맵](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap.html?lang=ko-KR) 다음에 대한 예정된 기능 활성화에 대해 알아보려면 [!DNL Experience Manager] as a Cloud Service.

>[!NOTE]
>
>릴리스와 직접적으로 관련되지 않는 설명서 업데이트의 세부 정보는 [설명서 업데이트](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html)를 참조하십시오.

## 릴리스 날짜 {#release-date}

의 릴리스 날짜 [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] 현재 기능 릴리스(2023.1.0)는 2023년 2월 9일입니다. 다음 기능 릴리스(2023.2.0)는 2023년 3월 30일에 예정되어 있습니다.

## 릴리스 비디오 {#release-video}

2023년 1월 릴리스 개요 비디오를 통해 2023.1.0 릴리스에 추가된 기능에 대한 간단한 요약을 살펴보십시오:

>[!VIDEO](https://video.tv.adobe.com/v/3413479/?quality=12)

## [!DNL Experience Manager Sites] as a [!DNL Cloud Service] {#sites}

### [!DNL Sites] 프리릴리스의 새로운 기능 {#prerelease-features-sites}

* 이제 AEM GraphQL 컨텐츠 배달 API가 GraphQL을 지원합니다 [페이징](/help/headless/graphql-api/content-fragments.md#paging) 및 [정렬](/help/headless/graphql-api/content-fragments.md#sorting)대용량 콘텐츠 세트를 가져와 렌더링하는 것이 더 효율적입니다. GraphQL 페이지 매김을 사용하면 한 번에 모든 결과가 아닌 하위 집합에 결과를 반환하여 쿼리 응답 시간을 향상시킬 수 있습니다. GraphQL 정렬을 사용하면 콘텐츠 세트를 원하는 순서로 배치할 수 있으므로 클라이언트 애플리케이션이 콘텐츠를 보다 쉽게 처리할 수 있습니다.  쿼리 응답 시간은 AEM GraphQL 엔진에서 하이브리드 필터링을 통해 더욱 향상됩니다. 이제 쿼리 필터에 해당하는 더 작은 세트의 JCR에서 콘텐츠를 읽습니다.

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### [!DNL Assets]의 새로운 기능 {#assets-features}

* 이제 Assets Reports에 관리자가 다음을 수행할 수 있는 기능이 포함됩니다. [에셋 다운로드 보고서 생성](/help/assets/asset-reports.md) Experience Manager Assets as a Cloud Service 배포에서. 이 데이터는 관리자가 기업 내 및 고객에 의한 Assets의 채택률을 측정하기 위해 주요 성공 지표에서 통찰력을 도출하는 기능을 추가로 제공합니다.

   ![다른 형식의 PDF 렌디션](/help/release-notes/assets/choose_report.png)

* 이제 Experience Manager Assets는 일괄 가져오기 도구를 사용하여 에셋을 수집하기 위해 Azure Blob Storage 데이터 소스에 연결할 때 인증에 액세스 키 외에 [SAS 토큰을 지원](/help/assets/add-assets.md#asset-bulk-ingestor)합니다.

* asset compute에서 CMYK 이미지 관리를 개선하여 CMYK 이미지용 스마트 자르기 및 스마트 태그를 생성할 수 있습니다.

### [!DNL Assets] 프리릴리스의 새로운 기능 {#prerelease-features-assets}

* 이제 Experience Manager Assets에서 [Google Cloud Platform에서 자산의 대규모 수집](/help/assets/add-assets.md#asset-bulk-ingestor) 일괄 가져오기 도구 사용.

## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

### [!DNL Forms] 프리릴리스에서 사용 가능한 새로운 기능 {#new-features-available-in-channel}

* **[비대화형 PDF 문서 및 인쇄 가능한 출력을 생성하는 워크플로우 단계](/help/forms/aem-forms-workflow-step-reference.md)**: AEM Workflow 단계를 통해 비대화형 PDF 문서 생성 및 비즈니스 프로세스용 인쇄 가능한 출력을 자동화하여 문서 생성 프로세스를 간소화하고 시간을 절약할 수 있습니다.
* **[각주를 사용하여 적응형 Forms에서 인용 또는 추가 정보를 제공하십시오](/help/forms/footnotes-richtextsupport.md)**: 적응형 양식의 각주를 사용하여 양식을 완성하거나 사용하는 방법에 대한 정보를 표시합니다. 또한 이를 사용하여 괄호 정보, 저작권 권한 및 기타 유용한 정보를 제공할 수도 있습니다.

### [!DNL Forms] 프리릴리스의 새로운 기능 {#prerelease-features-forms}

* **[데이터 캡처 핵심 구성 요소를 사용하여 적응형 Forms 구축](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html?lang=en)**: [적응형 Forms 편집기 사용](/help/forms/creating-adaptive-form-core-components.md) 표준화된 데이터 캡처 구성 요소(핵심 구성 요소)를 기반으로 양식을 작성합니다. 이러한 구성 요소는 사용자 지정 기능, 개발 시간 단축 및 디지털 등록 환경에 대한 유지 관리 비용 절감을 제공합니다.
* **[적응형 Forms 기반의 핵심 구성 요소 스타일링을 위한 프론트엔드 파이프라인 지원](/help/forms/using-themes-in-core-components.md)**: 프론트엔드 배포 파이프라인과 함께 배포하여 핵심 구성 요소 기반 적응형 Forms에 대해 쉽게 사용자 지정 가능한 BEM 기반 테마를 활용하여 양식의 디자인을 향상시킬 수 있습니다.
* **[적응형 Forms 기반의 핵심 구성 요소에 대한 기록 문서 생성](/help/forms/generate-document-of-record-core-components.md)**: 장기 보관을 위해 제출할 때 인쇄 또는 문서 형식으로 핵심 구성 요소 기반 적응형 양식에 대한 레코드를 만듭니다.

![https://www.aemcomponents.dev/](/help/forms/assets/sample-core-components-based-adaptive-form.png)

* **[Microsoft SharePoint 및 Microsoft OneDrive에 적응형 Forms 제출](/help/forms/configuring-submit-actions.md)**: 적응형 양식 데이터를 Microsoft SharePoint 및 Microsoft OneDrive 모두에 직접 전송하는 기능으로 데이터 제출 간소화. 스키마 기반 데이터와 스키마 불가 데이터를 모두 제출할 수 있습니다. 이러한 제출 액션은 이미 사용 가능한 제출 액션에 추가됩니다.
* **[적응형 양식을 템플릿으로 저장 기능을 사용하여 효율적인 양식 작성](/help/forms/template-editor.md#save-an-adaptive-form-as-template-saving-adaptive-form-as-template)**: 적응형 양식을 템플릿으로 저장하고 다음 적응형 양식에 대해 템플릿을 재사용하여 양식 작성 프로세스를 간소화합니다.
* **[AEM Forms을 JDBC가 지원하는 데이터베이스에 연결](/help/forms/configure-data-sources.md#configure-relational-database-configure-relational-database)**: AEM Forms 데이터 모델을 JDBC를 지원하는 데이터베이스에 쉽게 연결하여 데이터를 원활하게 읽고 쓸 수 있습니다.
* **[Open API 3.0을 사용하여 REST 엔드포인트와 통합](/help/forms/configure-data-sources.md#configure-restful-services-open-api-specification-version-20-configure-restful-services-swagger-version30)**: AEM Forms as a Cloud Service 양식 데이터 모델을 Open API 사양 버전 3.0을 지원하는 REST 엔드포인트에 연결하면 데이터를 쉽게 보내고 받을 수 있습니다.
* **[검토를 위해 적응형 양식 공유](/help/forms/create-reviews-forms.md)**: 적응형 Forms 검토 메커니즘을 사용하여 한 명 이상의 검토자가 양식을 검토할 수 있도록 합니다.


## CIF 추가 기능 {#cloud-services-cif}

### 새로운 기능 {#what-is-new-cif}

* 작성자는 경험 조각을 사용하여 제품 목록을 동적으로 보강할 수 있습니다(예: 제품 목록 사이에 배너 배치).
* 이제 목록 구성 요소는 관련 페이지를 동적으로 표시하기 위해 연결된 제품/카테고리 페이지를 지원합니다.
* Peregrine 12.5 구성 요소에 대한 지원이 추가되었습니다.
* 제품 티저 및 캐러셀의 클라이언트측 가격 로드에 대한 지원이 추가되었습니다.

## [!DNL Experience Manager as a Cloud Service] Foundation {#foundation}

### 새로운 기능 {#what-is-new-foundation}

* [신속한 개발 환경](/help/implementing/developing/introduction/rapid-development-environments.md) - RDE를 사용하면 개발자가 문제를 신속하게 해결하고 AEM에 새로운 기능을 as a Cloud Service으로 배포할 수 있습니다.

   신속한 개발 환경은 로컬에서 작동하는 코드가 클라우드에서 예상대로 작동하는지 확인하는 빠르고, 일관되고, 확장 가능한 방법을 목표로 하는 새로운 유형의 클라우드 환경입니다. 명령줄 도구를 사용하여 콘텐츠 패키지, 번들, 콘텐츠 파일, OSGI 구성 또는 Dispatcher 구성을 RDE에 빠르게 &quot;동기화&quot;합니다. 아래 비디오에서 이 작업을 참조하십시오.

   >[!VIDEO](https://video.tv.adobe.com/v/3413508/?quality=12&learn=on)

   RDE에서 코드의 유효성을 검사한 후에는 프로덕션 파이프라인을 통해 스테이지 및 프로덕션 환경에 배포하기 전에 클라우드 개발 환경에 배포하여 Cloud Manager 품질 게이트를 실행하는 것이 좋습니다.

   각 프로그램에는 하나의 RDE가 포함되어 있으며 선택적으로 더 많은 프로그램이 라이선스가 부여될 수 있습니다.

   >[!NOTE]
   >
   >RDE는 앞으로 몇 주에 걸쳐 점진적으로 롤아웃됩니다. 맨 앞으로 건너뛰려면 aemcs-rde-support@adobe.com으로 이메일을 보내십시오.

* [서버측 API 액세스 토큰에 대한 확장 지원](/help/implementing/developing/introduction/generating-access-tokens-for-server-side-apis.md) - 이제 여러 자격 증명을 생성할 수 있습니다. 이는 API의 특성이 다른 시나리오에 유용합니다. 이제 셀프서비스 방식으로 자격 증명을 취소할 수도 있습니다.

## 유지 관리 릴리스 노트 {#maintenance}

최신 유지 관리 릴리스 정보를 찾을 수 있습니다 [여기](/help/release-notes/maintenance/latest.md).

## Cloud Manager {#cloud-manager}

Cloud Manager 월별 릴리스의 전체 목록을 찾을 수 있습니다 [여기.](/help/implementing/cloud-manager/release-notes/current.md)

## 마이그레이션 도구 {#migration-tools}

[여기](/help/journey-migration/release-notes/release-notes-migration-tools-current.md)에서 마이그레이션 도구의 전체 목록을 찾을 수 있습니다.
