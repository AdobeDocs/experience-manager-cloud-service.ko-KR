---
title: ' [!DNL Adobe Experience Manager] as a Cloud Service의 2023.1.0 릴리스 정보입니다.'
description: ' [!DNL Adobe Experience Manager] as a Cloud Service의 2023.1.0 릴리스 정보입니다.'
exl-id: f134fdbc-224b-404c-b20f-44cae8bad681
source-git-commit: 9cff6e94b38016f008fd8177be2e071a530d80b6
workflow-type: tm+mt
source-wordcount: '978'
ht-degree: 100%

---

# [!DNL Adobe Experience Manager] as a Cloud Service 2023.1.0 릴리스 정보 {#release-notes}

다음 섹션에서는 [!DNL Experience Manager] as a Cloud Service의 2023.1.0 버전 기능 릴리스 정보에 대해 간략히 소개합니다.

>[!NOTE]
>
>여기에서 2021, 2022 버전 등 이전 버전의 릴리스 정보로 이동할 수 있습니다.
>
>[!DNL Experience Manager] as a Cloud Service의 향후 기능 활성화에 대해 알아보려면 [Experience Manager 릴리스 로드맵](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap.html?lang=ko-KR)을 살펴보십시오.

>[!NOTE]
>
>릴리스와 직접적으로 관련되지 않는 설명서 업데이트의 세부 정보는 [설명서 업데이트](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html)를 참조하십시오.

## 릴리스 일자 {#release-date}

[!DNL Adobe Experience Manager] as a [!DNL Cloud Service] 2023.1.0 기능 릴리스의 릴리스 날짜는 2023년 2월 9일입니다. 다음 기능 릴리스(2023.2.0)는 2023년 4월 12일에 예정되어 있습니다.

## 릴리스 비디오 {#release-video}

2023년 1월 릴리스 개요 비디오를 통해 2023.1.0 릴리스에 추가된 기능에 대한 간단한 요약을 살펴보십시오.

>[!VIDEO](https://video.tv.adobe.com/v/3413479/?quality=12)

## [!DNL Experience Manager Sites] as a [!DNL Cloud Service] {#sites}

### [!DNL Sites] 프리릴리스의 새로운 기능 {#prerelease-features-sites}

* AEM GraphQL 콘텐츠 게재 API는 이제 GraphQL [페이징](/help/headless/graphql-api/content-fragments.md#paging) 및 [정렬](/help/headless/graphql-api/content-fragments.md#sorting)을 지원하여 대용량 콘텐츠 세트를 보다 효율적으로 가져오고 렌더링할 수 있습니다. GraphQL 페이지 매김을 통해 결과를 한 번에 모두 반환하는 대신 하위 집합으로 반환하여 쿼리 응답 시간을 향상시킬 수 있습니다. GraphQL 정렬을 통해 콘텐츠 세트를 원하는 순서대로 배치할 수 있으므로 클라이언트 애플리케이션은 콘텐츠를 더 쉽게 처리할 수 있습니다.  AEM GraphQL 엔진의 하이브리드 필터링을 사용하여 쿼리 응답 시간을 추가로 향상시킵니다. 이제 콘텐츠를 쿼리 필터에 해당하는 더 작은 세트의 JCR에서 읽습니다.

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### [!DNL Assets]의 새로운 기능 {#assets-features}

* 에셋 보고서에는 이제 관리자가 Experience Manager Assets as a Cloud Service 배포에서 [에셋 다운로드 보고서를 생성](/help/assets/asset-reports.md)할 수 있는 기능이 포함됩니다. 관리자가 이 데이터를 사용하여 기업 내부에서 또는 고객에 의해 에셋 채택률을 측정하려면 주요 성공 지표에서 인사이트를 도출해야 합니다.

   ![다른 형식의 PDF 렌디션](/help/release-notes/assets/choose_report.png)

* 이제 Experience Manager Assets는 일괄 가져오기 도구를 사용하여 에셋을 수집하기 위해 Azure Blob Storage 데이터 소스에 연결할 때 인증에 액세스 키 외에 [SAS 토큰을 지원](/help/assets/add-assets.md#asset-bulk-ingestor)합니다.

* Asset Compute에서 CMYK 이미지 관리가 개선되면 CMYK 이미지용 스마트 자르기와 스마트 태그를 생성할 수 있습니다.

### [!DNL Assets] 프리릴리스의 새로운 기능 {#prerelease-features-assets}

* 이제 Experience Manager Assets는 일괄 가져오기 도구를 사용하여 [Google Cloud Platform에서의 대규모 에셋 수집](/help/assets/add-assets.md#asset-bulk-ingestor)을 지원합니다.

## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

### [!DNL Forms] 프리릴리스에서 사용 가능한 새로운 기능 {#new-features-available-in-channel}

* **[비대화형 PDF 문서와 인쇄 가능한 출력을 생성하는 워크플로 단계](/help/forms/aem-forms-workflow-step-reference.md)**: AEM 워크플로 단계를 통해 비즈니스 프로세스용 비대화형 PDF 문서와 인쇄 가능한 출력 생성을 자동화하여 문서 생성을 간소화하고 시간을 절약합니다.
* **[적응형 양식에 각주를 사용하여 인용 또는 추가 정보 제공](/help/forms/footnotes-richtextsupport.md)**: 적응형 양식에 각주를 사용하여 양식을 완료하거나 사용하는 방법에 대한 정보를 표시합니다. 삽입된 정보, 저작권 권한 및 기타 유용한 정보를 제공하는 데 사용할 수도 있습니다.

### [!DNL Forms] 프리릴리스의 새로운 기능 {#prerelease-features-forms}

* **[데이터 캡처 핵심 구성 요소를 사용하여 적응형 양식 작성](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html?lang=ko)**: [적응형 양식 편집기를 사용](/help/forms/creating-adaptive-form-core-components.md)하여 표준화된 데이터 캡처 구성 요소(핵심 구성 요소)를 기반으로 양식을 만듭니다. 이 구성 요소는 맞춤화 기능을 제공하고, 개발 시간을 단축하고, 유지 관리 비용을 줄여 디지털 등록 경험을 개선합니다.
* **[핵심 구성 요소 기반 적응형 양식의 스타일 유지를 위한 프론트엔드 파이프라인 지원](/help/forms/using-themes-in-core-components.md)**: 프론트엔드 파이프라인을 통해 핵심 구성 요소 기반 적응형 양식에 맞는 손쉬운 맞춤형 BEM 기반의 테마를 배포하여 양식의 디자인을 개선합니다.
* **[핵심 구성 요소 기반 적응형 양식의 기록 문서 만들기](/help/forms/generate-document-of-record-core-components.md)**: 장기간 보존하기 위해 인쇄 또는 문서 형식으로 제출 시 핵심 구성 요소 기반 적응형 양식의 기록을 만듭니다.

![https://www.aemcomponents.dev/](/help/forms/assets/sample-core-components-based-adaptive-form.png)

* **[Microsoft SharePoint 및 Microsoft OneDrive에 적응형 양식 제출](/help/forms/configuring-submit-actions.md)**: 적응형 양식 데이터를 Microsoft SharePoint 및 Microsoft OneDrive 모두에 직접 전송할 수 있는 기능을 사용하여 데이터 제출을 간소화합니다. 스키마 기반 데이터와 스키마 없는 데이터를 모두 제출할 수 있습니다. 이 제출 액션은 이미 제공된 제출 액션에 추가됩니다.
* **[템플릿으로 적응형 양식 저장 기능으로 효율적인 양식 작성](/help/forms/template-editor.md#save-an-adaptive-form-as-template-saving-adaptive-form-as-template)**: 적응형 양식을 템플릿으로 저장하고 다음 적응형 양식의 템플릿을 재사용하여 양식 작성 프로세스를 간소화합니다.
* **[JDBC 지원 데이터베이스에 AEM Forms 연결](/help/forms/configure-data-sources.md#configure-relational-database-configure-relational-database)**: AEM Forms 데이터 모델을 JDBC를 지원하는 데이터베이스에 간단히 연결하여 데이터를 원활하게 읽고 쓸 수 있습니다.
* **[Open API 3.0을 사용하여 REST 엔드포인트와 통합](/help/forms/configure-data-sources.md#configure-restful-services-open-api-specification-version-20-configure-restful-services-swagger-version30)**: AEM Forms as a Cloud Service 양식 데이터 모델을 Open API 사양 버전 3.0을 지원하는 REST 엔드포인트에 연결하여 데이터를 원활하게 주고 받을 수 있습니다.
* **[검토 목적으로 적응형 양식 공유](/help/forms/create-reviews-forms.md)**: 적응형 양식 검토 메커니즘을 사용하여 한 명 이상의 검토자가 양식을 검토할 수 있습니다.

## [!DNL Experience Manager as a Cloud Service] Foundation {#foundation}

### 새로운 기능 {#what-is-new-foundation}

* [신속한 개발 환경](/help/implementing/developing/introduction/rapid-development-environments.md) - RDE를 사용하여 개발자는 신속하게 문제를 해결하고 AEM as a Cloud Service의 새로운 기능을 배포할 수 있습니다.

   신속한 개발 환경은 로컬에서 작동하는 코드가 클라우드에서도 예상대로 작동하는지 빠르고 일관적이고 확장 가능한 방식으로 검증하는 새로운 유형의 클라우드 환경입니다. 명령줄 도구를 사용하여 RDE에 콘텐츠 패키지, 번들, 콘텐츠 파일, OSGi 구성 또는 Dispatcher 구성을 빠르게 “동기화”합니다. 아래 비디오에서 실제로 확인하십시오.

   >[!VIDEO](https://video.tv.adobe.com/v/3413508/?quality=12&learn=on)

   RDE에서 코드를 성공적으로 검증한 후 프로덕션 파이프라인을 통해 스테이징 및 프로덕션 환경에 배포하기 전에 클라우드 개발 환경에 배포하여 Cloud Manager 품질 게이트를 실행하는 것이 좋습니다.

   각 프로그램에는 한 개의 RDE가 포함되어 더 많은 프로그램에 라이선스가 부여될 수 있습니다.

   >[!NOTE]
   >
   >RDE는 앞으로 몇 주에 걸쳐 점진적으로 출시될 예정입니다. aemcs-rde-support@adobe.com로 이메일을 전송하여 가장 먼저 확인해 볼 수 있습니다.

* [서버측 API 액세스 토큰에 대한 확장 지원](/help/implementing/developing/introduction/generating-access-tokens-for-server-side-apis.md) – 이제 API 특성이 서로 다른 시나리오에 유용한 여러 자격 증명을 생성할 수 있습니다. 이제 셀프서비스 방식으로 자격 증명을 취소할 수도 있습니다.

## 유지 관리 릴리스 정보 {#maintenance}

[ 여기](/help/release-notes/maintenance/latest.md)에서 최신 유지 관리 릴리스 정보를 확인할 수 있습니다.

## Cloud Manager {#cloud-manager}

[여기](/help/implementing/cloud-manager/release-notes/current.md)에서 Cloud Manager 월별 릴리스의 전체 목록을 찾을 수 있습니다.

## 마이그레이션 도구 {#migration-tools}

[여기](/help/journey-migration/release-notes/release-notes-migration-tools-current.md)에서 마이그레이션 도구의 전체 목록을 찾을 수 있습니다.
