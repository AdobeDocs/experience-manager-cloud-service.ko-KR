---
title: ' [!DNL Adobe Experience Manager] as a Cloud Service 최신 릴리스 정보'
description: ' [!DNL Adobe Experience Manager] as a Cloud Service 최신 릴리스 정보'
exl-id: a2d56721-502c-4f4e-9b72-5ca790df75c5
mini-toc-levels: 1
source-git-commit: 397747469970f6385e7a846fd40cacc52b0dd151
workflow-type: tm+mt
source-wordcount: '626'
ht-degree: 98%

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

[!DNL Adobe Experience Manager]인 [!DNL Cloud Service]의 현재 릴리스(2022.8.0)의 날짜는 2022년 9월 1일입니다.
다음 릴리스(2022.9.0)는 2022년 10월 6일에 예정되어 있습니다.

## 릴리스 비디오 {#release-video}

2022년 8월 릴리스 개요 비디오를 통해 2022.8.0 릴리스에 추가된 기능에 대한 간단한 요약을 살펴보십시오.

>[!VIDEO](https://video.tv.adobe.com/v/346608/?quality=12)

## [!DNL Experience Manager Sites] as a [!DNL Cloud Service] {#sites}

### [!DNL Sites]의 새로운 기능 {#sites-features}

* 이메일 구성 요소를 사용하여 Campaign Classic을 통해 이메일로 제공되는 AEM의 콘텐츠를 만들 수 있습니다. 핵심 이메일 구성 요소
   * 편집 가능한 템플릿과 스타일 시스템을 지원하는 [Core WCM Component](https://github.com/adobe/aem-core-wcm-components)를 기반으로 함.
   * 이메일에 최적화되고 제작 준비가 완료된 구성 요소(페이지, 컨테이너, 제목, 텍스트, 이미지, 버튼, 티저, 경험 조각, 콘텐츠 조각, 세그먼테이션) 10개 제공.
   * 대화 상자 필드에서의 [Campaign 변수 삽입](https://github.com/adobe/aem-core-email-components/wiki/RTE-Personalization) 및 유연한 [세그먼테이션 구성 요소](https://github.com/adobe/aem-core-email-components/wiki/Segmentation-component-(기술 설명서))를 통해 고급 개인화 및 세그먼테이션 기능 제공.
   * [CSS 스타일 인라이너](https://github.com/adobe/aem-core-email-components/wiki/HTML-Inliner:-기술 설명서), [HTML 속성 인라이너](https://github.com/adobe/aem-core-email-components/wiki/HTML-Inliner:-Technical-documentation) 및 [HTML 삭제](https://github.com/adobe/aem-core-email-components/wiki/HTML-sanitizing:-기술 설명서)를 통해 이메일에 최적화된 HTML 출력 제공.
   * 장소에 상관없이 이메일 생성.

### [!DNL Sites] 프리릴리스 채널에서 사용할 수 있는 새로운 기능 {#prerelease-features-sites}

* [콘텐츠 조각 콘솔](/help/sites-cloud/administering/content-fragments/content-fragments-console.md)에서는 사용자가 콘텐츠 조각과 관련된 총 언어 사본 수를 표시할 수 있는 옵션이 제공됩니다. 클릭 한 번으로 언어 사본을 모두 조회할 수도 있습니다. 사용자는 관심 있는 로케일로 테이블 보기를 필터링할 수도 있습니다.

![콘텐츠 조각 언어](/help/release-notes/assets/cfconsole-languages.png)

## [!DNL Experience Manager Assets] 로서의 [!DNL Cloud Service] {#assets}

### [!DNL Assets]의 새로운 기능 {#features-assets}

* 이제 [사용자가 MIME 유형에 따라 업로드할 수 있는 에셋 유형을 제한](/help/assets/configure-asset-upload-restrictions.md)하도록 Adobe Experience Manager Assets를 구성할 수 있습니다.

   ![에셋 업로드 제한 사항](/help/assets/assets/asset-upload-restrictions.png)

## [!DNL Experience Manager Forms] 로서의 [!DNL Cloud Service] {#forms}

### [!DNL Forms] 프리릴리스 채널에서 사용할 수 있는 새로운 기능 {#prerelease-features-forms}

* [적응형 양식 마법사](/help/forms/creating-adaptive-form.md): AEM Forms에서는 적응형 양식을 신속하게 작성할 수 있는 비즈니스 사용자 친화적 마법사를 제공합니다. 마법사에는 미리 구성된 템플릿, 스타일, 필드 및 제출 옵션을 손쉽게 선택하여 적응형 양식을 만들 수 있는 빠른 탭 탐색 기능이 있습니다. 이번 릴리스에서 마법사 기능이 다음과 같이 개선되었습니다.

   * 필드 선택 또는 선택 해제: 마법사를 사용하여 JSON 및 양식 데이터 모델 스키마를 기준으로 적응형 양식을 만들 수 있습니다. 이제 적응형 양식에 포함되도록 스키마 내 필드의 하위 집합을 선택할 수 있습니다. 선택한 필드가 해당되는 적응형 양식 데이터 캡처 구성 요소로 변환되면 간단하게 원하는 적응형 양식을 만들 수 있습니다.

   * 정적 템플릿 사용: 레거시 정적 템플릿에 투자한 기존 고객들은 적응형 양식을 작성할 수 있는 마법사의 정적 템플릿을 사용하여 클라우드 채택 여정을 계속 진행할 수 있습니다. 이로써 고객이 이전 정적 템플릿을 최신 편집 가능한 템플릿으로 마이그레이션하는 데 시간이 더 걸릴 수 있습니다.

* [서버측 처리 도중 기록 문서(DoR)에서 숨겨진 필드 제거](/help/forms/generate-document-of-record-for-non-xfa-based-adaptive-forms.md): 데이터 캡처 경험 중에 표시되는 해당 필드만 포함하는 최종 사용자용 기록 문서 PDF를 생성할 수 있습니다. 양식 제출 시 서버는 제출된 데이터를 기반으로 최종 사용자에게 숨겨진 필드를 확인하고 일관성을 위해 기록 문서에서 제외합니다.

## CIF 추가 기능 {#cloud-services-cif}

### 새로운 기능 {#what-is-new-cif}

* AEM 페이지 속성과 제품 관리실 개요를 통해 AEM 페이지를 제품 및 카테고리에 연결
   ![제품 관리실 페이지 연결](/help/assets/CIF/product_cockpit_page_association.png)

## Cloud Manager {#cloud-manager}

[여기](/help/implementing/cloud-manager/release-notes-cloud-manager/release-notes-cm-current.md)에서 Cloud Manager 월별 릴리스의 전체 목록을 찾을 수 있습니다.

## 마이그레이션 도구 {#migration-tools}

[여기](/help/journey-migration/release-notes/release-notes-migration-tools-current.md)에서 마이그레이션 도구의 전체 목록을 찾을 수 있습니다.
