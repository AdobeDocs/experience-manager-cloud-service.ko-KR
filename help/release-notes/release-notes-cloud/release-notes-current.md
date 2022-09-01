---
title: ' [!DNL Adobe Experience Manager] as a Cloud Service 최신 릴리스 정보'
description: ' [!DNL Adobe Experience Manager] as a Cloud Service 최신 릴리스 정보'
exl-id: a2d56721-502c-4f4e-9b72-5ca790df75c5
mini-toc-levels: 1
source-git-commit: bcd62d1d1a66e17585e35c11c12cd72067e0e46e
workflow-type: tm+mt
source-wordcount: '626'
ht-degree: 28%

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

의 릴리스 날짜 [!DNL Adobe Experience Manager] 로서의 [!DNL Cloud Service] 현재 릴리스(2022.8.0)는 2022년 9월 1일입니다.
다음 릴리스(2022.9.0)는 2022년 9월 29일에 예정되어 있습니다.

## 릴리스 비디오 {#release-video}

2022.8.0 릴리스에 추가된 기능에 대한 요약을 보려면 2022년 8월 릴리스 개요 비디오를 보십시오.

>[!VIDEO](https://video.tv.adobe.com/v/346608/?quality=12)

## [!DNL Experience Manager Sites] as a [!DNL Cloud Service] {#sites}

### [!DNL Sites]의 새로운 기능 {#sites-features}

* 이메일 구성 요소를 사용하면 AEM에서 컨텐츠를 만든 다음 Campaign Classic을 통해 이메일로 배달됩니다. 핵심 이메일 구성 요소:
   * 는 [코어 WCM 구성 요소](https://github.com/adobe/aem-core-wcm-components) 편집 가능한 템플릿 및 스타일 시스템을 지원합니다.
   * 은 10개의 전자 메일에 최적화된 프로덕션 준비 구성 요소(페이지, 컨테이너, 제목, 텍스트, 이미지, 단추, 티저, 경험 조각, 컨텐츠 조각, 세그멘테이션)를 제공합니다.
   * 은 고급 개인화 및 세그멘테이션을 제공합니다. [campaign 변수 삽입](https://github.com/adobe/aem-core-email-components/wiki/RTE-Personalization) 대부분의 대화 상자 필드에서 및 [세그먼테이션 구성 요소](https://github.com/adobe/aem-core-email-components/wiki/Segmentation-component-(Technical-Documentation)).
   * 은 이메일 친화적인 HTML 출력을 제공합니다. [CSS 스타일 삽입](https://github.com/adobe/aem-core-email-components/wiki/HTML-Inliner:-Technical-documentation), [HTML 속성 인라인](https://github.com/adobe/aem-core-email-components/wiki/HTML-Inliner:-Technical-documentation), 및 [HTML 소독기](https://github.com/adobe/aem-core-email-components/wiki/HTML-sanitizing:-Technical-documentation).
   * 어디서나 이메일을 만들 수 있습니다.

### [!DNL Sites] 프리릴리스 채널에서 사용할 수 있는 새로운 기능 {#prerelease-features-sites}

* 다음 [컨텐츠 조각 콘솔](/help/sites-cloud/administering/content-fragments/content-fragments-console.md) 사용자에게 컨텐츠 조각과 연관된 총 언어 사본 수를 표시하는 옵션을 제공합니다. 모든 언어 사본도 보려면 1번의 클릭으로 액세스할 수 있습니다. 사용자는 원하는 로케일별로 테이블 보기를 필터링할 수도 있습니다.

![컨텐츠 조각 언어](/help/release-notes/assets/cfconsole-languages.png)

## [!DNL Experience Manager Assets] 로서의 [!DNL Cloud Service] {#assets}

### [!DNL Assets]의 새로운 기능 {#features-assets}

* 이제 [사용자가 MIME 유형에 따라 업로드할 수 있는 에셋 유형을 제한](/help/assets/configure-asset-upload-restrictions.md)하도록 Adobe Experience Manager Assets를 구성할 수 있습니다.

   ![에셋 업로드 제한 사항](/help/assets/assets/asset-upload-restrictions.png)

## [!DNL Experience Manager Forms] 로서의 [!DNL Cloud Service] {#forms}

### [!DNL Forms] 프리릴리스 채널에서 사용할 수 있는 새로운 기능 {#prerelease-features-forms}

* [응용 Forms 마법사](/help/forms/creating-adaptive-form.md): AEM Forms은 적응형 Forms을 빠르게 작성할 수 있는 비즈니스 사용자에게 친숙한 마법사를 제공합니다. 마법사에는 적응형 양식을 만들기 위해 사전 구성된 템플릿, 스타일 지정, 필드 및 제출 옵션을 쉽게 선택할 수 있는 빠른 탭 탐색 기능이 있습니다. 이 릴리스에서는 마법사에 다음과 같은 개선 사항이 제공됩니다.

   * 필드 선택 또는 선택 취소: 마법사를 사용하면 JSON 및 양식 데이터 모델 스키마를 기반으로 적응형 양식을 만들 수 있습니다. 이제 스키마 내의 필드 하위 집합을 선택하여 적응형 양식에 포함할 수 있습니다. 선택한 필드가 해당 적응형 양식 데이터 캡처 구성 요소로 변환되어 원하는 적응형 양식을 빠르게 만듭니다.

   * 정적 템플릿 사용: 기존 정적 템플릿에 대한 기존 투자를 사용하는 고객은 마법사에서 정적 템플릿을 사용하여 적응형 양식을 작성함으로써 클라우드 채택 여정을 계속할 수 있습니다. 이를 통해 고객은 기존의 정적 템플릿을 편집 가능한 최신 템플릿으로 마이그레이션할 수 있습니다.

* [서버측 처리 중 레코드 문서(DoR)에서 숨겨진 필드를 제거합니다](/help/forms/generate-document-of-record-for-non-xfa-based-adaptive-forms.md): 데이터 캡처 경험 중에 표시되는 필드만 포함하는 최종 사용자에 대한 레코드 PDF 문서를 생성할 수 있습니다. 양식 제출 시 서버는 제출된 데이터를 기반으로 최종 사용자에게 숨겨진 필드를 확인하고 일관성을 위해 기록 문서에서 제외합니다.

## CIF 추가 기능 {#cloud-services-cif}

### 새로운 기능 {#what-is-new-cif}

* AEM 페이지 속성 및 제품 조종실의 개요를 통해 제품 및 카테고리에 대한 AEM 페이지 연결
   ![제품 조종실 페이지 협회](/help/assets/CIF/product_cockpit_page_association.png)

## Cloud Manager {#cloud-manager}

[여기](/help/implementing/cloud-manager/release-notes-cloud-manager/release-notes-cm-current.md)에서 Cloud Manager 월별 릴리스의 전체 목록을 찾을 수 있습니다.

## 마이그레이션 도구 {#migration-tools}

[여기](/help/journey-migration/release-notes/release-notes-migration-tools-current.md)에서 마이그레이션 도구의 전체 목록을 찾을 수 있습니다.
