---
title: ' [!DNL Adobe Experience Manager] as a Cloud Service 최신 릴리스 정보'
description: ' [!DNL Adobe Experience Manager] as a Cloud Service 최신 릴리스 정보'
exl-id: a2d56721-502c-4f4e-9b72-5ca790df75c5
mini-toc-levels: 1
source-git-commit: a96824cede31414963ff7e6f5ef1315bd35a51c1
workflow-type: tm+mt
source-wordcount: '1099'
ht-degree: 44%

---


# [!DNL Adobe Experience Manager] as a Cloud Service 최신 릴리스 정보 {#release-notes}

다음 섹션에서는 [!DNL Experience Manager] as a Cloud Service의 최신 버전 일반 릴리스 정보에 대해 간략히 소개합니다.

>[!NOTE]
>
>여기에서 2020, 2021 버전 등 이전 버전의 릴리스 정보로 이동할 수 있습니다.

>[!NOTE]
>
>릴리스와 직접적으로 관련되지 않는 설명서 업데이트의 세부 정보는 [설명서 업데이트](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html?lang=ko-KR)를 참조하십시오.

## 릴리스 날짜 {#release-date}

의 릴리스 날짜 [!DNL Adobe Experience Manager] 로서의 [!DNL Cloud Service] 현재 릴리스(2022.3.0)는 2022년 3월 31일입니다.
다음 릴리스(2022.4.0)는 2022년 4월 28일입니다.

## 릴리스 비디오 {#release-video}

을(를) 보십시오. [2022년 3월 릴리스 개요](https://video.tv.adobe.com/v/341465) 비디오 - 2022.3.0 릴리스에 추가된 기능에 대한 요약

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### [!DNL Assets]의 새로운 기능 {#assets-features}

* [!DNL AEM Dynamic Media] 이제 즉시 사용 가능한 Dynamic Media URL 및 뷰어 임베드 코드를 업데이트하도록 사용자 인터페이스에서 [하나의 별칭 계정](/help/assets/dynamic-media/dm-alias-account.md)을 구성할 수 있습니다. 이는 리브랜딩과 같은 비즈니스 컨텍스트에 대한 업데이트를 반영하여 SEO에 긍정적인 영향을 미칩니다.

* 이제 [!DNL Experience Manager Assets] 사용자 인터페이스를 사용하여 다음을 수행할 수 있습니다.

   * 구성 [중복 자산 검색](/help/assets/manage-digital-assets.md#detect-duplicate-assets) 저장소에 있습니다.

   * 구성 [디지털 워터마크 추가](/help/assets/watermark-assets.md) 이미지를 클릭합니다.

* 이제 관리자는 대량 다운로드를 위한 이메일 서비스를 구성할 수 있습니다. 이를 통해 사용자는 [!DNL Experience Manager Assets] 인터페이스에서 [대량 다운로드에 대한 이메일 알림](/help/assets/download-assets-from-aem.md#enable-email-notifications-for-large-downloads)을 활성화할 수 있습니다. 사용자는 다운로드 프로세스가 완료되면 아카이브된 zip 폴더의 다운로드 링크가 포함된 이메일 알림을 수신하게 됩니다.

* [게시 관리](/help/assets/manage-publication.md) 기능은 개선된 사용자 인터페이스로 향상되었습니다. 사용자는 선택한 대상에 콘텐츠를 게시하거나 게시를 취소하고, DAM 저장소의 게시 목록에 [콘텐츠를 추가](/help/assets/manage-publication.md#add-content)하고, [폴더 설정을 포함하여](/help/assets/manage-publication.md#include-folder-settings) 선택한 폴더의 콘텐츠를 게시하고 필터를 적용하고, 나중에 게시할 날짜 또는 시간에 [게시 일정](/help/assets/manage-publication.md#publish-assets-later)을 지정할 수 있습니다.

### [!DNL Assets] 프리릴리스 채널에서 사용할 수 있는 새로운 기능 {#prerelease-features-assets}

* 다음을 수행할 수 있습니다 [태그 정렬](/help/assets/organize-assets.md#use-tags-to-organize-assets) 태그 설명을 사용하여 검색 필터를 적용할 뿐만 아니라 스마트 태그를 만드는 동안

## [!DNL Experience Manager Forms] 로서의 [!DNL Cloud Service] {#forms}

### [!DNL Forms]의 새로운 기능 {#what-is-new-forms}

* **[!DNL Communications - Document Generation APIs]**: [문서 생성 API](/help/forms/aem-forms-cloud-service-communications.md) PDF 문서를 결합, 재정렬 및 확인하는 데 도움이 됩니다. 이 서비스를 사용하면 동기화 모드에서 문서를 생성할 수 있습니다. API를 사용하면 다음과 같은 기능을 제공하는 애플리케이션을 만들 수 있습니다.

   * PDF 문서를 어셈블합니다.
   * PDF 문서를 디스어셈블합니다.
   * PDF/A 규격 문서로 변환하여 유효성을 검사합니다.

* **15페이지가 넘는 PDF forms을 적응형 양식으로 자동 변환**: 이제 automated forms conversion 서비스를 사용하여 최대 40페이지가 있는 PDF forms을 적응형 양식으로 전환할 수 있습니다. 이제 이 서비스는 15페이지 이상의 양식의 섹션을 적응형 양식 조각으로 변환하는 옵션을 제공합니다. 이것은 변환된 양식의 렌더링 속도를 개선하는 데 도움이 되며 적응형 양식 편집기에서 큰 양식을 더 쉽게 로드할 수 있도록 합니다.

### [!DNL Forms] 프리릴리스 채널에서 사용할 수 있는 새로운 기능 {#prerelease-features-forms}

* **사용자 정의 XCI를 사용하여 레코드 문서 생성**: 이제 사용자 지정 XCI 파일을 사용하여 레코드 문서의 다양한 속성을 설정할 수 있습니다. 이 값은 사용자 지정 변경 사항으로 마스터 XCI를 무시합니다.

* **적응형 양식에서 보이지 않는 CAPTCHA 사용**: 보이지 않는 CAPTCHA를 사용하여 의심스러운 활동의 경우에만 CAPTCHA 문제를 표시할 수 있습니다. 의심스러운 활동이 없으면 CAPTCHA 문제가 표시되지 않습니다.

## CIF 추가 기능 {#cloud-services-cif}

### 새로운 기능 {#what-is-new-cif}

* 베타: AEM CIF Search 핵심 구성 요소 지원 Commerce LiveSearch
* 다중 저장소 시나리오에 대한 SEO가 개선되었습니다. 이제 CIF 클라우드 구성 속성을 통해 저장소 수준에서 PDP/PLP의 URL 형식을 구성할 수 있습니다
* 제품 선택기는 UI에서 새 필터 옵션을 통해 준비된 제품을 지원합니다.  이를 통해 컨텐츠 전문가가 향후 제품 출시에 대한 제품 컨텐츠 관리를 준비할 수 있습니다
* 구성 프록시 URL 대신 CIF 클라우드 구성 이름을 사용하여 CIF 구성 관리 및 오류 처리를 단순화했습니다
* 제품 목록 및 회전 메뉴 구성 요소에 대한 수동 카테고리 선택. 이를 통해 컨텐츠 전문가가 카탈로그 경험 외부의 컨텐츠 페이지에서 이러한 구성 요소를 사용할 수 있습니다

## [!DNL Experience Manager] 로서의 [!DNL Cloud Service] Foundation {#foundation}

### 새로운 기능 {#what-is-new-foundation}

* 클라우드 환경의 사용자 지정 기능을 보다 효율적이고 효과적으로 해결하기 위해 새로운 개발자 도구를 발표했습니다. [저장소 브라우저](/help/implementing/developing/tools/repository-browser.md). 개발자 콘솔에서 실행할 수 있는 경량의 읽기 전용 HTML 브라우저입니다. 게시자, 작성자 및 미리 보기 계층, 프로덕션, 스테이지, 개발 등 모든 환경에서 컨텐츠 리포지토리를 표시할 수 있습니다. 컨텐츠 구조를 찾아보고, 속성을 보고, 바이너리를 미리 보고 다운로드합니다.

   ![repobrowserrelnotes](/help/release-notes/assets/repobrowserrelnotes.png)

* 서버 간 API 호출을 인증하는 데 사용되는 자격 증명(예: GraphQL API 요청의 경우)은 이제 개발자 콘솔에서 자체 제공 방식으로 만료되기 전에 새로 고칠 수 있습니다. 자세한 내용은 [설명서](/help/implementing/developing/introduction/generating-access-tokens-for-server-side-apis.md#refresh-credentials) 추가 정보.

* 버전 삭제 및 감사 로그 삭제 유지 관리 작업은 이전에 활성화되지 않았던 새 환경에 대해 활성화됩니다. 에서 관련 값을 참조하십시오 [유지 관리 작업](/help/operations/maintenance.md) 문서.

* AEM as a Cloud Service SDK Dispatcher 도구는 이제 M1 칩을 사용하는 Mac 컴퓨터를 지원합니다

## Cloud Manager {#cloud-manager}

Cloud Manager 월별 릴리스의 전체 목록을 찾을 수 있습니다 [여기](/help/implementing/cloud-manager/release-notes-cloud-manager/release-notes-cm-current.md).

## 콘텐츠 전송 도구 {#ctt-release}

### 릴리스 날짜 {#release-date-ctt}

컨텐츠 전송 도구 v1.9.0의 릴리스 날짜는 2022년 2월 28일입니다.

### 새로운 기능 {#what-is-new-ctt}

* 크기 보호 확인 - 컨텐츠 전송 도구 확인 크기 기능은 실패한 컨텐츠 전송을 줄이는 데 도움이 됩니다.  [크기 확인] 기능을 사용하면 1) 사용자가 1) `crx-quickstart` 하위 디렉토리 추출 전 및 2) 마이그레이션 세트 크기를 추정하고 지원되는지 확인합니다. 이 검사 중 하나 또는 둘 다를 위반한 경우 CTT UI에 경고가 표시됩니다. 이러한 보호를 통해 컨텐츠 전송 오류를 방지하고 Adobe 고객 지원 센터를 통해 마이그레이션 옵션에 대해 미리 논의할 수 있습니다. 을(를) 참조하십시오. [마이그레이션 세트 크기 및 디스크 공간 확인](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/getting-started-content-transfer-tool.html?lang=en#migration-set-size) 자세한 내용

## Best Practices Analyzer {#bpa-release}

### 릴리스 날짜 {#release-date-bpa}

Best Practices Analyzer v2.1.26의 릴리스 날짜는 2022년 3월 16일입니다.

### 새로운 기능 {#what-is-new-bpa}

* 처리되지 않은 에셋을 감지할 수 있습니다. 처리되지 않은 에셋이 감지되면 이들 에셋을 처리됨으로 설정하거나 콘텐츠 전송 도중 마이그레이션 세트에서 제거하여 콘텐츠 수집 과정에서 문제가 발생하지 않도록 해야 합니다.
* 콘텐츠의 vanity URL이 1000개를 초과하는지 감지할 수 있습니다. 디스패처 및 게시 서버에 부하가 걸리게 되므로 다수의 vanity URL을 사용하는 것은 권장되지 않습니다.
* Oak 인덱스 정의와 관련된 문제를 식별하고 AEM as a Cloud Service와의 비호환성을 감지할 수 있습니다.
* 외부화 구성의 사용을 감지하고 보고할 수 있습니다. AEM as a Cloud Service 외부화 구성은 Cloud Manager에 의해 설정되므로 호환성을 유지하려면 기존 외부화 구성을 리팩터링해야 합니다.

### 버그 수정 {#bug-fixes-bpa}

* 일부 시나리오에서 어설션 오류를 발생시키는 FormsSelectiveFeaturesAnalysis로 인해 BPA가 실행되지 못했습니다. 이 문제가 해결되었습니다.
* BPA가 WRK 패턴과 관련된 결과를 “심각”이 아닌 “주요” 문제로 보고했습니다. 이 문제가 해결되었습니다.
* BPA가 ui.apps의 OAK 인덱스 정의와 관련된 결과를 “심각”으로 잘못 보고했습니다. 이 문제가 해결되었습니다
