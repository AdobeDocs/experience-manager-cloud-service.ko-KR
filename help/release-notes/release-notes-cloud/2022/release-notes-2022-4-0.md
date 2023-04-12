---
title: ' [!DNL Adobe Experience Manager] as a Cloud Service의 2022.4.0 릴리스 정보입니다.'
description: ' [!DNL Adobe Experience Manager] as a Cloud Service의 2022.4.0 릴리스 정보입니다.'
exl-id: 6c86838a-cabf-4770-b1ae-618af70193a2
source-git-commit: 599f924465552b2ef43827da8e139c239e47baed
workflow-type: tm+mt
source-wordcount: '570'
ht-degree: 95%

---

# 2022.4.0 릴리스 노트 [!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

다음 섹션에서는 2022.4.0 버전 의 기능 릴리스 노트를 간략하게 설명합니다 [!DNL Experience Manager] as a Cloud Service.

>[!NOTE]
>
>여기에서 2020, 2021 버전 등 이전 버전의 릴리스 정보로 이동할 수 있습니다.

>[!NOTE]
>
>릴리스와 직접적으로 관련되지 않는 설명서 업데이트의 세부 정보는 [설명서 업데이트](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html)를 참조하십시오.

## 릴리스 일자 {#release-date}

[!DNL Adobe Experience Manager] as a [!DNL Cloud Service]의 현재 릴리스(2022.4.0) 날짜는 2022년 5월 5일입니다.
다음 릴리스(2022.5.0)는 2022년 6월 9일에 예정되어 있습니다.

## 릴리스 비디오 {#release-video}

[2022년 4월 릴리스 개요](https://video.tv.adobe.com/v/342612?quality=12) 비디오를 통해 2022.4.0 릴리스에 추가된 기능에 대한 간단한 요약을 살펴보십시오.

## [!DNL Experience Manager Sites] as a [!DNL Cloud Service] {#sites}

### [!DNL Sites]의 새로운 기능 {#sites-features}

* 이제 콘텐츠 모델 편집기의 간단한 확인란을 사용하여 콘텐츠 모델 데이터 유형을 [변환 가능](/help/assets/content-fragments/content-fragments-models.md#properties)한 것으로 정의할 수 있습니다. 또한 AEM 번역 규칙 및 구성이 자동으로 업데이트됩니다.

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### [!DNL Assets]의 새로운 기능 {#assets-features}

* 이제 태그 이름, 작성 날짜 또는 수정 날짜를 기준으로 태그 선택기 창에서 오름차순 또는 내림차순으로 [태그를 정렬](/help/assets/organize-assets.md#use-tags-to-organize-assets)할 수 있습니다.


## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

### [!DNL Forms]의 새로운 기능 {#what-is-new-forms}

* **통신 - Forms as a Cloud Service SDK에서의 문서 조작 API 지원**: [문서 조작 API](/help/forms/aem-forms-cloud-service-communications.md)를 사용하면 PDF 문서를 결합하고, 재정렬하고, 유효성을 검사하는 데 도움이 됩니다. 이제 AEM Forms as a Cloud Service SDK를 사용하여 로컬 개발 환경에서 통신 - 문서 생성 API를 사용할 수 있습니다.

* **기록 문서 생성에 맞춤형 XCI 사용**: 이제 [맞춤형 XCI 파일을 사용하여 기록 문서의 여러 속성을 설정](/help/forms/generate-document-of-record-for-non-xfa-based-adaptive-forms.md#use-a-custom-xci-file)할 수 있습니다. 사용자 지정 변경 내용으로 마스터 XCI를 재정의합니다. 기록 문서 생성, 개인화 및 맞춤화 기회를 더욱 효과적으로 제어할 수 있습니다.

* **적응형 양식에서 보이지 않는 CAPTCHA 사용**: [의심되는 활동이 있는 경우에만 보이지 않는 CAPTCHA를 사용하여 CAPTCHA 문제를 표시](/help/forms/captcha-adaptive-forms.md)할 수 있습니다. 의심되는 활동이 없는 경우 CAPTCHA 문제가 표시되지 않습니다. 이는 확인란 요구 사항 없이 사람의 양식 완성을 평가하고, 맞춤화 노력을 줄이고, 최종 사용자 경험을 개선하는 데 도움이 됩니다.

* **양식 데이터 모델 구성**: 이제 [여러 환경에서 양식 데이터 모델을 재사용](/help/forms/create-form-data-models.md#runmode-specific-context-aware-config)하여 데이터 통합을 단순화하고 IT 비용을 절감할 수 있습니다.


## [!DNL Experience Manager] as a [!DNL Cloud Service] Foundation {#foundation}

### SDK Build Analyzer {#sdk-build-analyzers}

AEM as a Cloud Service SDK Build Analyzer Maven 플러그인은 누락된 종속성을 포함하여 Maven 프로젝트의 문제를 감지합니다. Cloud Manager를 사용하여 클라우드 환경에 배포하기 전에 개발자에게 로컬 개발 중에 문제를 발견할 수 있는 기회를 제공합니다.

최근에 새로운 분석기가 추가되었습니다.

* `content-packages-validation` - 배포 중에 설치할 패키지에 대한 올바른 형식의 콘텐츠 구문 및 구조를 확인합니다.

최신 버전의 분석기로 Maven 프로젝트를 업데이트하거나 아직 업데이트하지 않았다면 해당 분석기를 포함하는 것이 좋습니다. 자세한 내용은 [여기](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/build-analyzer-maven-plugin.html)에서 설명서를 참조하십시오.

## [!DNL Experience Manager] as a [!DNL Cloud Service] Foundation 보안 {#foundation-security}

### TLS 1.0, 1.1 사용 중단

2022년 6월 30일부터 Experience Manager as a Cloud Service는 보다 안전한 네트워크 통신 및 사용자 시스템과의 데이터 교환을 필요로 합니다. AEM은 TLS(전송 계층 보안), 1.2 프로토콜만 사용합니다. 이전 TLS 버전 1.0 및 1.1은 더 이상 사용되지 않습니다.

이전 버전의 TLS를 1.0, 1.1로 계속 사용하는 경우 Experience Manager as a Cloud Service에 대한 액세스 권한을 잃을 수 있습니다.

## Cloud Manager {#cloud-manager}

[여기](/help/implementing/cloud-manager/release-notes/current.md)에서 Cloud Manager 월별 릴리스의 전체 목록을 찾을 수 있습니다.

## 마이그레이션 도구 {#migration-tools}

[여기](/help/journey-migration/release-notes/release-notes-migration-tools-current.md)에서 마이그레이션 도구의 전체 목록을 찾을 수 있습니다.
