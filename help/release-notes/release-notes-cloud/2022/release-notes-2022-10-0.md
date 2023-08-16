---
title: ' [!DNL Adobe Experience Manager] as a Cloud Service의 2022.10.0 릴리스 정보입니다.'
description: ' [!DNL Adobe Experience Manager] as a Cloud Service의 2022.10.0 릴리스 정보입니다.'
exl-id: 8fce7c50-f322-4bcf-bd76-390faedfd5b7
source-git-commit: 5ad33f0173afd68d8868b088ff5e20fc9f58ad5a
workflow-type: tm+mt
source-wordcount: '836'
ht-degree: 80%

---

# [!DNL Adobe Experience Manager] as a Cloud Service 2022.10.0 릴리스 정보 {#release-notes}

다음 섹션에서는 의 2022.10.0 버전에 대한 기능 릴리스 노트를 간략하게 설명합니다 [!DNL Experience Manager] as a Cloud Service.

>[!NOTE]
>
>여기에서 2020, 2021 버전 등 이전 버전의 릴리스 정보로 이동할 수 있습니다.

>[!NOTE]
>
>릴리스와 직접적으로 관련되지 않는 설명서 업데이트의 세부 정보는 [설명서 업데이트](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html)를 참조하십시오.

## 릴리스 일자 {#release-date}

[!DNL Adobe Experience Manager]인 [!DNL Cloud Service]의 현재 월별 릴리스(2022.10.0)의 날짜는 2022년 11월 10일입니다. 다음 월별 릴리스(2023.1.0)는 2023년 9월 2일로 예정되어 있습니다.

## 릴리스 비디오 {#release-video}

2022년 10월 릴리스 개요 비디오를 통해 2022.10.0 릴리스에 추가된 기능에 대한 간단한 요약을 살펴보십시오.

>[!VIDEO](https://video.tv.adobe.com/v/3409801/?quality=12)

## [!DNL Experience Manager Sites] as a [!DNL Cloud Service] {#sites}


### [!DNL Sites]의 새로운 기능 {#sites-features}

* 다음 [경험 조각용 개인화 탭](/help/sites-cloud/authoring/fundamentals/experience-fragments.md#personalization-experience-fragment) 경험 조각 편집기에서 세분화 사양 기능을 사용할 수 있으며, 여러 세그먼트에 대해 머리글 및 바닥글 변형을 만들 수 있는 중첩된 경험 조각을 자유롭게 만들 수 있습니다. 이 기능이 출시되기 전에는 AEM에서 제공하는 개인화를 사이트 페이지에만 사용할 수 있고 경험 조각에는 사용할 수 없습니다.

* 이제 사용자는 [콘텐츠 조각 콘솔](/help/sites-cloud/administering/content-fragments/content-fragments-console.md)에서 번역된 콘텐츠 조각을 효율적으로 관리할 수 있습니다. 클릭 한 번으로 언어 사본을 모두 조회할 수도 있습니다. 사용자는 관심 있는 로케일로 테이블 보기를 필터링할 수도 있습니다.

![콘텐츠 조각 언어](/help/release-notes/assets/cfconsole-languages.png)

* 템플릿의 이미지 크기 설정을 최적화하여 방문자의 페이지 로드 시간을 한층 더 줄입니다. [핵심 WCM 구성 요소](https://github.com/adobe/aem-core-wcm-components)에서 이미지 구성 요소에 대해 자세히 알아보십시오.

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### [!DNL Assets]의 새로운 기능 {#assets-features}

* 이제 Experience Manager Assets을 사용하여 지원되는 다른 형식 유형의 문서를 업로드할 수 있습니다.[포함된 Document Cloud 뷰어를 사용하여 미리보기](/help/assets/manage-pdf-documents.md). 지원되는 형식 유형은 TXT, RTF, DOC, DOCX, PPT, PPTX, XLS, XLSX입니다.

  ![다른 형식의 PDF 렌디션](/help/release-notes/assets/multi-page-other-formats.png)


### [!DNL Assets] 프리릴리스의 새로운 기능 {#prerelease-features-assets}

* Experience Manager Assets는 이제 이미지 스마트 태그에 대해 향상된 인공 지능 프레임워크를 사용합니다. 이 콘텐츠 인텔리전스는 수집 시 모든 이미지 에셋에 사용할 수 있는 스마트 태그의 관련성과 정확성을 향상시킵니다. 또한 `cq:tags`에 방향 정보가 채워지므로 방향 필터를 사용하여 더 나은 검색 결과를 얻을 수 있습니다.

  Beta 참여에 관심이 있는 경우 11월 14일까지 [이 양식을 작성](https://forms.office.com/pages/responsepage.aspx?id=Wht7-jR7h0OUrtLBeN7O4epXZrTVKKdJkUiHeolccf9UNEwyNEpHVEFaODdBNFZQSlFDREZQOVRRTy4u)하시기 바랍니다.

* 이제 Experience Manager Assets는 일괄 가져오기 도구를 사용하여 에셋을 수집하기 위해 Azure Blob Storage 데이터 소스에 연결할 때 인증에 액세스 키 외에 [SAS 토큰을 지원](/help/assets/add-assets.md#asset-bulk-ingestor)합니다.

## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

### [!DNL Forms] 프리릴리스 채널에서 사용할 수 있는 새로운 기능 {#prerelease-features-forms}

* **적응형 Forms 템플릿 편집기**: 템플릿 편집기를 사용하면 조직 적응형 Forms의 기본 구조와 모양을 미리 정의할 수 있습니다. 이번 릴리스에서 템플릿 편집기 기능이 다음과 같이 개선되었습니다.
   * **[템플릿 편집기의 양식 데이터 모델](/help/forms/creating-adaptive-form.md#edit-form-model-properties-of-an-adaptive-form-edit-form-model)**: 템플릿 편집기에서 양식 데이터 모델 스키마를 적응형 양식 템플릿에 연결할 수 있습니다. 적응형 양식을 만드는 데 걸리는 시간을 줄이는 데 도움이 됩니다. 또한 이 옵션은 적응형 양식 편집기에도 추가되어 사용자가 기존 양식에 대한 양식 데이터 모델을 선택하거나 변경할 수 있습니다.
   * **[템플릿 편집기의 기록 문서](/help/forms/generate-document-of-record-for-non-xfa-based-adaptive-forms.md#document-of-record-support-in-adaptive-form-editor-dor-support-in-adaptiveform)**: 이제 템플릿을 사용하여 생성된 모든 양식에 대해 레코드 문서 생성을 표준화할 수 있습니다. 이는 조직 요구 사항에 대한 규정 준수 및 표준화를 강화하는 데 도움이 됩니다.

* **[AEM Sites 페이지에서 적응형 양식 마법사 시작](/help/forms/embed-adaptive-form-aem-sites.md)**: AEM Sites 페이지의 적응형 양식 지원이 확장되었습니다. 이제 AEM Sites 페이지에서 바로 새 적응형 양식을 만들거나 기존 적응형 양식을 임베드할 수 있습니다.
* **[DoR에서 확인란 및 라디오 버튼의 표시 정렬 변경](/help/forms/generate-document-of-record-for-non-xfa-based-adaptive-forms.md#customize-the-branding-information-in-document-of-record-customize-the-branding-information-in-document-of-record)**: 이제 기록 문서의 확인란 및 라디오 버튼에 대해 원하는 정렬(가로, 세로, 적응형 양식과 동일)을 설정할 수 있습니다. 이 옵션은 기록 문서에서 확인란 및 라디오 버튼 옵션의 위치를 결정합니다.

## CIF 추가 기능 {#cloud-services-cif}

### 새로운 기능 {#what-is-new-cif}

* 작성자는 경험 조각을 사용하여 제품 목록을 동적으로 보강할 수 있습니다(예: 제품 목록 사이에 배너 배치).
* 이제 목록 구성 요소는 관련 페이지를 동적으로 표시하기 위해 연결된 제품/카테고리 페이지를 지원합니다.
* Peregrine 12.5 구성 요소에 대한 지원이 추가되었습니다.
* 제품 티저 및 캐러셀의 클라이언트측 가격 로드에 대한 지원이 추가되었습니다.

## [!DNL Experience Manager as a Cloud Service] Foundation {#foundation}

### 새로운 기능 {#what-is-new-foundation}

* 이제 AEM as a Cloud Service(작성자 서비스)가 통합 셸과 통합되어 사용자 경험을 개선하고 다른 모든 Experience Cloud 애플리케이션과 통합합니다. AEM as a 를 참조하십시오 [통합 쉘의 Cloud Service](/help/overview/aem-cloud-service-on-unified-shell.md) 을 참조하십시오.

* 앞서 릴리스 정보에서 언급한 바와 같이, 이제 10MB 이상의 콘텐츠 패키지(속성이 있는 노드, 바이너리를 포함하지 않음)를 배포하기 위해 복제 에이전트 관리 화면 또는 복제 API를 사용하는 방법은 더 이상 사용되지 않으며 적용됩니다. 다음을 참조하십시오 [게시 관리](/help/operations/replication.md#manage-publication) 또는 [콘텐츠 트리 워크플로 게시](/help/operations/replication.md#publish-content-tree-workflow) 이러한 대용량 콘텐츠 패키지를 복제하는 데 대한 권장 접근 방식.

* 이제 Dispatcher 구성은 일반적인 마케팅 캠페인 쿼리 매개변수를 나열하는 파일을 참조합니다. 고객은 원하는 경우 자신과 관련된 매개변수의 주석을 해제할 수 있으므로 더 나은 캐싱이 가능합니다. 다음을 참조하십시오 [마케팅 캠페인 매개변수](/help/implementing/dispatcher/caching.md#marketing-parameters) 을 참조하십시오.

## Cloud Manager {#cloud-manager}

[여기](/help/implementing/cloud-manager/release-notes/current.md)에서 Cloud Manager 월별 릴리스의 전체 목록을 찾을 수 있습니다.

## 마이그레이션 도구 {#migration-tools}

[여기](/help/journey-migration/release-notes/release-notes-migration-tools-current.md)에서 마이그레이션 도구의 전체 목록을 찾을 수 있습니다.
