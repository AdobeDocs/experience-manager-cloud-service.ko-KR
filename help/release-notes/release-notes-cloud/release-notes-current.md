---
title: ' [!DNL Adobe Experience Manager] as a Cloud Service 최신 릴리스 정보'
description: ' [!DNL Adobe Experience Manager] as a Cloud Service 최신 릴리스 정보'
exl-id: a2d56721-502c-4f4e-9b72-5ca790df75c5
mini-toc-levels: 1
source-git-commit: 9857376cb196b8aaa9fac64636727b5ad20a0360
workflow-type: tm+mt
source-wordcount: '617'
ht-degree: 32%

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

의 릴리스 날짜 [!DNL Adobe Experience Manager] 로서의 [!DNL Cloud Service] 현재 릴리스(2022.4.0)는 2022년 5월 5일입니다.
다음 릴리스(2022.5.0)는 2022년 5월 26일에 예정되어 있습니다.

## 릴리스 비디오 {#release-video}

을(를) 보십시오. [2022년 4월 릴리스 개요](https://video.tv.adobe.com/v/342612?quality=12) 비디오 - 2022.4.0 릴리스에 추가된 기능에 대한 요약

## [!DNL Experience Manager Sites] as a [!DNL Cloud Service] {#sites}

### [!DNL Sites]의 새로운 기능 {#sites-features}

* 이제 컨텐츠 모델 데이터 유형을 [번역](/help/assets/content-fragments/content-fragments-models.md#properties) 컨텐츠 모델 편집기에서 단순 확인란 사용. 또한 AEM 번역 규칙 및 구성이 자동으로 업데이트됩니다.

## [!DNL Experience Manager Assets] 로서의 [!DNL Cloud Service] {#assets}

### [!DNL Assets]의 새로운 기능 {#assets-features}

* 이제 다음을 수행할 수 있습니다 [태그 정렬](/help/assets/organize-assets.md#use-tags-to-organize-assets) 태그 선택기 창에서 태그 이름, 작성 날짜 또는 수정 날짜를 기준으로 오름차순 또는 내림차순으로 선택합니다.

## [!DNL Experience Manager Forms] 로서의 [!DNL Cloud Service] {#forms}

### [!DNL Forms]의 새로운 기능 {#what-is-new-forms}

* **통신 - Forms as a Cloud Service SDK에서 문서 조작 API 지원**: [문서 조작 API](/help/forms/aem-forms-cloud-service-communications.md) PDF 문서를 결합, 재정렬 및 확인하는 데 도움이 됩니다. 이제 AEM Forms as a Cloud Service SDK의 도움을 받아 로컬 개발 환경에서 통신 - 문서 생성 API를 사용할 수 있습니다.

* **기록 문서 생성에 맞춤형 XCI 사용**[: 이제 맞춤형 XCI 파일을 사용하여 기록 문서의 여러 속성을 설정할 수 있습니다](/help/forms/generate-document-of-record-for-non-xfa-based-adaptive-forms.md#use-a-custom-xci-file). 사용자 지정 변경 내용으로 마스터 XCI를 재정의합니다. Document of Record 생성, 개인화 및 사용자 지정 기회를 더욱 효과적으로 제어할 수 있습니다.

* **적응형 양식에서 보이지 않는 CAPTCHA 사용**[: 의심되는 활동이 있는 경우에만 보이지 않는 CAPTCHA를 사용하여 CAPTCHA 문제를 표시할 수 있습니다](/help/forms/captcha-adaptive-forms.md). 의심되는 활동이 없는 경우 CAPTCHA 문제가 표시되지 않습니다. Adobe Campaign은 확인란 요구 사항 없이 사람 양식을 완성했는지 평가하고 사용자 지정 노력을 줄이고 최종 사용자 경험을 개선하는 데 도움이 됩니다.

* **양식 데이터 모델 구성**: 이제 다음을 수행할 수 있습니다 [여러 환경에서 양식 데이터 모델 구성 재사용](/help/forms/create-form-data-models.md#runmode-specific-context-aware-config)데이터 통합을 간소화하고 IT 비용을 절감할 수 있습니다.

## CIF 추가 기능 {#cloud-services-cif}

### 새로운 기능 {#what-is-new-cif}

* 제품 조종실에 대한 빠른 액세스: 사이트 편집기에서 한 번의 클릭으로 전체 세부 제품 정보에 쉽게 액세스할 수 있습니다

   ![wishlist 사용](/help/assets/CIF/enable-wishlist.png)

* 추가 마케팅 상거래 구성 요소에 대한 지원: 장바구니에 추가 및 wishlist 호출에 대한 작업을 표시하도록 구성 요소를 구성할 수 있습니다

   ![제품 조종실에 대한 사이트 편집기 바로 가기](/help/assets/CIF/sites-editor-shortcut-to-cockpit.png)

## [!DNL Experience Manager] as a [!DNL Cloud Service] Foundation {#foundation}

### SDK 빌드 분석기 {#sdk-build-analyzers}

AEM as a Cloud Service SDK Build Analyzer Maven 플러그인은 누락된 종속성을 포함하여 전문 프로젝트의 문제를 감지합니다. Cloud Manager를 사용하여 클라우드 환경에 배포하기 전에 개발자에게 로컬 개발 중에 문제를 발견할 수 있는 기회를 제공합니다.

최근에 새로운 분석기가 추가되었습니다.

* `content-packages-validation` - 배포 중에 설치할 패키지의 올바른 형식의 콘텐츠 구문 및 구조를 확인합니다.

최신 버전의 분석기로 maven 프로젝트를 업데이트하거나 아직 업데이트하지 않았다면 분석기를 포함하는 것이 좋습니다. 자세한 내용은 설명서를 참조하십시오 [여기](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/build-analyzer-maven-plugin.html).

## [!DNL Experience Manager] 로서의 [!DNL Cloud Service] 기초 보안 {#foundation-security}

### TLS 1.0, 1.1 사용 중단

2022년 6월 30일부터 Experience Manager as a Cloud Service은 보다 안전한 네트워크 통신 및 사용자 시스템과의 데이터 교환을 필요로 합니다. AEM은 TLS(전송 계층 보안), 1.2 프로토콜만 사용합니다. 이전 TLS 버전 1.0 및 1.1은 더 이상 사용되지 않습니다.

이전 버전의 TLS를 1.0, 1.1로 계속 사용하는 경우 Experience Manager as a Cloud Service에 대한 액세스 권한을 잃을 수 있습니다.

## Cloud Manager {#cloud-manager}

[여기](/help/implementing/cloud-manager/release-notes-cloud-manager/release-notes-cm-current.md)에서 Cloud Manager 월별 릴리스의 전체 목록을 찾을 수 있습니다.

## 마이그레이션 도구 {#migration-tools}

마이그레이션 도구 릴리스의 전체 목록을 찾을 수 있습니다 [여기](/help/journey-migration/release-notes/release-notes-migration-tools-current.md).
