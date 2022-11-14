---
title: ' [!DNL Adobe Experience Manager] as a Cloud Service 최신 릴리스 정보'
description: ' [!DNL Adobe Experience Manager] as a Cloud Service 최신 릴리스 정보'
exl-id: a2d56721-502c-4f4e-9b72-5ca790df75c5
mini-toc-levels: 1
source-git-commit: 094e90050747d5412f34b79cd5a11b8f5e05e6eb
workflow-type: tm+mt
source-wordcount: '1107'
ht-degree: 34%

---


# [!DNL Adobe Experience Manager] as a Cloud Service 최신 릴리스 정보 {#release-notes}

다음 섹션에서는 [!DNL Experience Manager] as a Cloud Service의 최신 버전 일반 릴리스 정보에 대해 간략히 소개합니다.

>[!NOTE]
>
>여기에서 2020, 2021 버전 등 이전 버전의 릴리스 정보로 이동할 수 있습니다.

>[!NOTE]
>
>릴리스와 직접적으로 관련되지 않는 설명서 업데이트의 세부 정보는 [설명서 업데이트](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html)를 참조하십시오.

>[!CAUTION]
>
>**블랙 프라이데이 및 크리스마스 유지 관리 제외 기간**
>
> 다음 기간 동안 자정 (00:00) CET에서 시작하여 끝나는 자동 AEMaaCS 유지 관리가 실행되지 않습니다.
>
>* 11월 21일 월요일~12월 5일 월요일
>* 12월 19일 월요일~1월 3일 화요일
>
> 이 기간들은 블랙 프라이데이, 사이버 먼데이, 크리스마스 그리고 설날을 다룹니다.

## 릴리스 일자 {#release-date}

의 릴리스 날짜 [!DNL Adobe Experience Manager] 로서의 [!DNL Cloud Service] 현재 월별 릴리스(2022.10.0)은 2022년 11월 10일입니다. 다음 월별 릴리스(2023.1.0)는 2023년 1월 26일에 제공될 예정입니다.

## 릴리스 비디오 {#release-video}

2022.10.0 릴리스에 추가된 기능의 요약이 필요하면 2022년 10월 릴리스 개요 비디오를 보십시오.

>[!VIDEO](https://video.tv.adobe.com/v/3409801/?quality=12)

## [!DNL Experience Manager Sites] as a [!DNL Cloud Service] {#sites}


### [!DNL Sites]의 새로운 기능 {#sites-features}

* 다음 [경험 조각용 개인화 탭](/help/sites-cloud/authoring/fundamentals/experience-fragments.md#personalization-experience-fragment) 에서는 경험 조각 편집기에 대한 세그멘테이션 사양 기능을 사용할 수 있을 뿐만 아니라 중첩된 경험 조각을 만들 수 있으므로 여러 세그먼트에 대해 머리글 및 바닥글 변형을 만들 수 있습니다. 이 기능을 시작하기 전에, AEM에서 제공하는 개인화는 사이트 페이지에서만 사용할 수 있지만 경험 조각에는 사용할 수 없습니다

* 다음 [컨텐츠 조각 콘솔](/help/sites-cloud/administering/content-fragments/content-fragments-console.md) 이제 사용자가 번역된 컨텐츠 조각을 효율적으로 관리할 수 있습니다. 클릭 한 번으로 언어 사본을 모두 조회할 수도 있습니다. 사용자는 관심 있는 로케일로 테이블 보기를 필터링할 수도 있습니다.

![콘텐츠 조각 언어](/help/release-notes/assets/cfconsole-languages.png)

* 또한 템플릿의 이미지 크기 설정을 최적화하여 방문자의 페이지 로드 시간을 줄입니다. 에서 이미지 구성 요소에 대한 자세한 정보를 확인하십시오. [코어 WCM 구성 요소](https://github.com/adobe/aem-core-wcm-components)

## [!DNL Experience Manager Assets] 로서의 [!DNL Cloud Service] {#assets}

### [!DNL Assets]의 새로운 기능 {#assets-features}

* 이제 Experience Manager Assets에서 문서를 지원되는 다른 형식 유형 및[ 포함된 Document Cloud 뷰어를 사용하여 미리 보기](/help/assets/manage-pdf-documents.md). 지원되는 형식 유형에는 TXT, RTF, DOC, DOCX, PPT, PPTX, XLS 및 XLSX가 있습니다.

   ![다른 형식에 대한 PDF 표현물](/help/release-notes/assets/multi-page-other-formats.png)


### 의 새로운 기능 [!DNL Assets] 사전 릴리스 {#prerelease-features-assets}

* 이제 Experience Manager Assets에서는 이미지 스마트 태그에 향상된 인공 지능 프레임워크를 사용합니다. 이 컨텐츠 인텔리전스로 인해 수집 시 모든 이미지 자산에 사용할 수 있는 스마트 태그의 관련성과 정확성이 향상됩니다. 또한 방향 정보는 `cq:tags`- 방향 필터를 사용하여 더 나은 검색 결과를 사용할 수 있습니다.

   베타에 참여하시려면, [양식 채우기](https://forms.office.com/pages/responsepage.aspx?id=Wht7-jR7h0OUrtLBeN7O4epXZrTVKKdJkUiHeolccf9UNEwyNEpHVEFaODdBNFZQSlFDREZQOVRRTy4u) 11월 14일까지.

* 지금 Experience Manager Assets [SAS 토큰 지원](/help/assets/add-assets.md#asset-bulk-ingestor) 대량 가져오기 도구를 사용하여 자산을 수집하기 위해 Azure Blob 저장소 데이터 원본에 연결하는 동안 인증을 위한 액세스 키 외에,

## [!DNL Experience Manager Forms] 로서의 [!DNL Cloud Service] {#forms}

### 에서 사용할 수 있는 새로운 기능 [!DNL Forms] channel {#new-features-available-in-channel}

* [적응형 양식 마법사](/help/forms/creating-adaptive-form.md): AEM Forms에서는 적응형 양식을 신속하게 작성할 수 있는 비즈니스 사용자 친화적 마법사를 제공합니다. 마법사에는 미리 구성된 템플릿, 스타일, 필드 및 제출 옵션을 손쉽게 선택하여 적응형 양식을 만들 수 있는 빠른 탭 탐색 기능이 있습니다. 이번 릴리스에서 마법사 기능이 다음과 같이 개선되었습니다.

   * 필드 선택 또는 선택 해제: 마법사를 사용하여 JSON 및 양식 데이터 모델 스키마를 기준으로 적응형 양식을 만들 수 있습니다. 이제 적응형 양식에 포함되도록 스키마 내 필드의 하위 집합을 선택할 수 있습니다. 선택한 필드가 해당되는 적응형 양식 데이터 캡처 구성 요소로 변환되면 간단하게 원하는 적응형 양식을 만들 수 있습니다.

   * 정적 템플릿 사용: 레거시 정적 템플릿에 투자한 기존 고객들은 적응형 양식을 작성할 수 있는 마법사의 정적 템플릿을 사용하여 클라우드 채택 여정을 계속 진행할 수 있습니다. 이로써 고객이 이전 정적 템플릿을 최신 편집 가능한 템플릿으로 마이그레이션하는 데 시간이 더 걸릴 수 있습니다.

* [서버측 처리 도중 기록 문서(DoR)에서 숨겨진 필드 제거](/help/forms/generate-document-of-record-for-non-xfa-based-adaptive-forms.md): 데이터 캡처 경험 중에 표시되는 해당 필드만 포함하는 최종 사용자용 기록 문서 PDF를 생성할 수 있습니다. 양식 제출 시 서버는 제출된 데이터를 기반으로 최종 사용자에게 숨겨진 필드를 확인하고 일관성을 위해 기록 문서에서 제외합니다.



### [!DNL Forms] 프리릴리스 채널에서 사용할 수 있는 새로운 기능 {#prerelease-features-forms}

* **적응형 Forms 템플릿 편집기**: 템플릿 편집기를 사용하면 조직의 적응형 Forms의 기본 구조와 모양을 미리 정의할 수 있습니다. 이 릴리스에서는 템플릿 편집기에 다음과 같은 개선 사항이 제공됩니다.
   * **[템플릿 편집기의 양식 데이터 모델](/help/forms/creating-adaptive-form.md#edit-form-model-properties-of-an-adaptive-form-edit-form-model)**: 템플릿 편집기에서 양식 데이터 모델 스키마를 적응형 양식 템플릿에 연결할 수 있습니다. 적응형 양식을 만드는 데 걸리는 시간을 줄이는 데 도움이 됩니다. 응용 Forms 편집기에 옵션이 추가되어 사용자가 기존 양식에 대한 양식 데이터 모델을 선택하거나 변경할 수 있습니다.
   * **[템플릿 편집기의 기록 문서](/help/forms/generate-document-of-record-for-non-xfa-based-adaptive-forms.md#document-of-record-support-in-adaptive-form-editor-dor-support-in-adaptiveform)**: 이제 템플릿을 사용하여 생성된 모든 양식에 대해 기록 문서 생성을 표준화할 수 있습니다. 이를 통해 조직 요구 사항에 대한 규정 준수 및 표준화를 향상시킬 수 있습니다.

* **[AEM Sites 페이지에서 적응형 양식 마법사 시작](/help/forms/embed-adaptive-form-aem-sites.md)**: AEM Sites 페이지에는 적용형 Forms에 대한 확장된 지원이 있습니다. 이제 AEM Sites 페이지에 남아 있는 동안 새 적응형 양식을 만들거나 기존 적응형 양식을 포함할 수 있습니다.
* **[DoR에서 확인란 및 라디오 단추에 대한 표시 정렬 변경](/help/forms/generate-document-of-record-for-non-xfa-based-adaptive-forms.md#customize-the-branding-information-in-document-of-record-customize-the-branding-information-in-document-of-record)**: 이제 레코드 문서에서 확인란 및 라디오 단추에 대해 원하는 정렬(가로, 세로, 적응형 Forms과 동일)을 설정할 수 있습니다. 이 옵션은 레코드 문서에서 확인란 및 라디오 단추 옵션의 위치를 결정합니다.

## CIF 추가 기능 {#cloud-services-cif}

### 새로운 기능 {#what-is-new-cif}

* 작성자는 경험 조각으로 제품 목록을 동적으로 보강할 수 있습니다(예: 제품 목록 사이에 배너를 배치하십시오.)
* 이제 목록 구성 요소는 관련 페이지를 동적으로 표시하도록 관련 제품/카테고리 페이지를 지원합니다.
* Peregrine 12.5 구성 요소에 대한 지원이 추가되었습니다.
* 제품 Teaser 및 Carousel의 클라이언트측 가격 로딩 지원이 추가되었습니다.

## [!DNL Experience Manager as a Cloud Service] Foundation {#foundation}

### 새로운 기능 {#what-is-new-foundation}

* 이제 AEM as a Cloud Service(작성자 서비스)가 통합 셸과 통합되어 사용자 경험을 향상하고 다른 모든 Experience Cloud 애플리케이션과 통합할 수 있습니다. AEM as a 를 참조하십시오. [통합 셸의 Cloud Service](/help/overview/aem-cloud-service-on-unified-shell.md) 자세한 내용

* 릴리스 노트에서 이전에 언급했듯이 10MB보다 큰 컨텐츠 패키지(바이너리를 포함하지 않고 속성을 갖는 노드)를 배포하는 복제 에이전트 관리 화면 또는 복제 API를 사용하는 것은 더 이상 사용되지 않으며 며칠 후에 적용됩니다. 자세한 내용은 [게시 관리](/help/operations/replication.md#manage-publication) 또는 [컨텐츠 트리 게시 워크플로우](/help/operations/replication.md#publish-content-tree-workflow) 이러한 큰 컨텐츠 패키지를 복제하는 데 권장되는 방법에 대해 설명합니다.

* 이제 Dispatcher 구성이 일반적인 마케팅 캠페인 쿼리 매개 변수를 나열하는 파일을 참조합니다. 고객은 이러한 매개 변수와 관련된 매개 변수의 주석을 해제하여 캐싱이 개선되도록 선택할 수 있습니다. 을(를) 참조하십시오. [마케팅 캠페인 매개 변수](/help/implementing/dispatcher/caching.md#marketing-parameters) 자세한 내용

## Cloud Manager {#cloud-manager}

[여기](/help/implementing/cloud-manager/release-notes-cloud-manager/release-notes-cm-current.md)에서 Cloud Manager 월별 릴리스의 전체 목록을 찾을 수 있습니다.

## 마이그레이션 도구 {#migration-tools}

[여기](/help/journey-migration/release-notes/release-notes-migration-tools-current.md)에서 마이그레이션 도구의 전체 목록을 찾을 수 있습니다.
