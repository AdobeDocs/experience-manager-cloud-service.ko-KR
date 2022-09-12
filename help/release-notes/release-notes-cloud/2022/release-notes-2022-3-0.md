---
title: ' [!DNL Adobe Experience Manager] as a Cloud Service의 2022.3.0 릴리스 정보입니다.'
description: ' [!DNL Adobe Experience Manager] as a Cloud Service의 2022.3.0 릴리스 정보입니다.'
exl-id: 761f1605-c421-4f3a-8f90-af23f4f047b1
source-git-commit: b71cd1394260c8ec14b661934199632987a034f6
workflow-type: tm+mt
source-wordcount: '1152'
ht-degree: 100%

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

[!DNL Adobe Experience Manager] as a [!DNL Cloud Service]의 현재 릴리스(2022.3.0) 날짜는 2022년 3월 31일입니다.
다음 릴리스(2022.4.0)는 2022년 5월 5일에 예정되어 있습니다.

## 릴리스 비디오 {#release-video}

[2022년 3월 릴리스 개요](https://video.tv.adobe.com/v/341465) 비디오를 통해 2022.3.0 릴리스에 추가된 기능에 대한 간단한 요약을 살펴보십시오.

## [!DNL Experience Manager Sites] as a [!DNL Cloud Service] {#sites}

### [!DNL Sites] 프리릴리스 채널에서 사용할 수 있는 새로운 기능 {#prerelease-features-sites}

* 이제 콘텐츠 모델 편집기의 간단한 확인란을 사용하여 콘텐츠 모델 데이터 유형을 변환 가능한 것으로 정의할 수 있습니다. 또한 AEM 번역 규칙 및 구성이 자동으로 업데이트됩니다.

## [!DNL Experience Manager Assets] 로서의 [!DNL Cloud Service] {#assets}

### [!DNL Assets]의 새로운 기능 {#assets-features}

* [!DNL AEM Dynamic Media] 이제 즉시 사용 가능한 Dynamic Media URL 및 뷰어 임베드 코드를 업데이트하도록 사용자 인터페이스에서 [하나의 별칭 계정](/help/assets/dynamic-media/dm-alias-account.md)을 구성할 수 있습니다. 이는 리브랜딩과 같은 비즈니스 컨텍스트에 대한 업데이트를 반영하여 SEO에 긍정적인 영향을 미칩니다.

* 이제 [!DNL Experience Manager Assets] 사용자 인터페이스를 사용하여 다음과 같은 작업을 수행할 수 있습니다.

   * 저장소에서 [중복 에셋 감지](/help/assets/manage-digital-assets.md#detect-duplicate-assets)를 구성합니다.

   * 이미지에 [디지털 워터마크 추가](/help/assets/watermark-assets.md)를 구성합니다.

* 이제 관리자는 대량 다운로드를 위한 이메일 서비스를 구성할 수 있습니다. 이를 통해 사용자는 [!DNL Experience Manager Assets] 인터페이스에서 [대량 다운로드에 대한 이메일 알림](/help/assets/download-assets-from-aem.md#enable-email-notifications-for-large-downloads)을 활성화할 수 있습니다. 사용자는 다운로드 프로세스가 완료되면 아카이브된 zip 폴더의 다운로드 링크가 포함된 이메일 알림을 수신하게 됩니다.

* [게시 관리](/help/assets/manage-publication.md) 기능은 개선된 사용자 인터페이스로 향상되었습니다. 사용자는 선택한 대상에 콘텐츠를 게시하거나 게시를 취소하고, DAM 저장소의 게시 목록에 [콘텐츠를 추가](/help/assets/manage-publication.md#add-content)하고, [폴더 설정을 포함하여](/help/assets/manage-publication.md#include-folder-settings) 선택한 폴더의 콘텐츠를 게시하고 필터를 적용하고, 나중에 게시할 날짜 또는 시간에 [게시 일정](/help/assets/manage-publication.md#publish-assets-later)을 지정할 수 있습니다.

### [!DNL Assets] 프리릴리스 채널에서 사용할 수 있는 새로운 기능 {#prerelease-features-assets}

* 이제 태그 이름, 작성 날짜 또는 수정 날짜를 기준으로 태그 선택기 창에서 오름차순 또는 내림차순으로 [태그를 정렬](/help/assets/organize-assets.md#use-tags-to-organize-assets)할 수 있습니다.

## [!DNL Experience Manager Forms] 로서의 [!DNL Cloud Service] {#forms}

### [!DNL Forms]의 새로운 기능 {#what-is-new-forms}

* **[!DNL Communications - Document Generation APIs]**: [Document Generation API](/help/forms/aem-forms-cloud-service-communications.md)를 통해 PDF 문서를 결합하고, 재배열하고 확인할 수 있습니다. 이 서비스를 사용하면 동기화 모드에서 문서를 생성할 수 있습니다. API를 사용하면 다음과 같은 기능을 제공하는 애플리케이션을 만들 수 있습니다.

   * PDF 문서를 어셈블합니다.
   * PDF 문서를 디스어셈블합니다.
   * PDF/A호환 문서로 변환하고 확인합니다.

* **15페이지 이상의 PDF Forms를 적응형 양식으로 자동 변환**: 이제 자동화된 양식 변환 서비스를 사용하여 최대 40페이지의 PDF Forms를 적응형 양식으로 변환할 수 있습니다. 이 서비스에서는 15페이지 이상의 양식 섹션을 적응형 양식 조각으로 변환하는 옵션이 제공됩니다. 이를 사용하여 변환된 양식의 레더링 속도를 개선하고 적응형 양식 편집기에서 보다 쉽게 대용량 양식을 로드할 수 있습니다.

### [!DNL Forms] 프리릴리스 채널에서 사용할 수 있는 새로운 기능 {#prerelease-features-forms}

* **기록 문서 생성에 맞춤형 XCI 사용**: 이제 맞춤형 XCI 파일을 사용하여 기록 문서의 여러 속성을 설정할 수 있습니다. 사용자 지정 변경 내용으로 마스터 XCI를 재정의합니다.

* **적응형 양식에서 보이지 않는 CAPTCHA 사용**: 의심되는 활동이 있는 경우에만 보이지 않는 CAPTCHA를 사용하여 CAPTCHA 문제를 표시할 수 있습니다. 의심되는 활동이 없는 경우 CAPTCHA 문제가 표시되지 않습니다.

## CIF 추가 기능 {#cloud-services-cif}

### 새로운 기능 {#what-is-new-cif}

* 다중 스토어 시나리오에 대한 SEO 개선: 이제 PDP/PLP에 대한 URL 형식은 CIF Cloud 구성 속성을 통해 스토어 레벨에서 구성할 수 있습니다.
* 제품 선택기는 UI의 새 필터 옵션을 통해 스테이징된 제품을 지원합니다.  이를 통해 콘텐츠 제공자는 예정된 제품 출시에 맞춰 제품 콘텐츠 관리를 준비할 수 있습니다.
* 구성 프록시 URL 대신 CIF Cloud 구성 이름을 시용하여 CIF 구성 관리 및 오류 처리 간소화
* 수동으로 제품 목록 및 슬라이드 구성 요소의 범주 선택. 따라서 콘텐츠 제공자는 카탈로그 경험 이외의 콘텐츠 페이지에서 이들 구성 요소를 사용할 수 있습니다.

### CIF 프리릴리스 채널에서 사용할 수 있는 새로운 기능 {#prerelease-features-cif}

* AEM CIF 검색 핵심 구성 요소는 Commerce LiveSearch를 지원합니다.

## [!DNL Experience Manager] as a [!DNL Cloud Service] Foundation {#foundation}

### 새로운 기능 {#what-is-new-foundation}

* Cloud 환경에서 사용자 지정 기능 문제를 보다 효율적으로 해결하기 위해 새 개발자 도구인 [저장소 브라우저](/help/implementing/developing/tools/repository-browser.md)가 출시되었습니다. 간단한 읽기 전용 HTML 브라우저로서 Developer Console에서 실행할 수 있습니다. 게시자, 작성자 및 미리보기 계층과 프로덕션, 스테이징 및 개발 등 모든 환경에서 콘텐츠 저장소에 대한 가시성을 확보합니다. 콘텐츠 구조를 검색하고, 속성을 확인하고 바이너리를 미리 보고 다운로드합니다.

   ![repobrowserrelnotes](/help/release-notes/assets/repobrowserrelnotes.png)

* Developer Console에서 셀프서비스 방식으로 만료되기 전에 서버 간 API 호출 인증에 사용되는 자격 증명(예: GraphQL API 요청의 경우)을 새로 고칠 수 있습니다. 자세한 내용은 [설명서](/help/implementing/developing/introduction/generating-access-tokens-for-server-side-apis.md#refresh-credentials)를 참조하십시오.

* 이전에 활성화되지 않은 버전 제거 및 감사 로그 제거 유지 관리 작업이 새 환경에서 활성화될 수 있습니다. [유지 관리 작업](/help/operations/maintenance.md) 문서에서 관련된 값을 참조하십시오.

* 이제 AEM as a Cloud Service SDK Dispatcher는 M1 칩이 내장된 Mac 컴퓨터를 지원합니다.

## Cloud Manager {#cloud-manager}

[여기](/help/implementing/cloud-manager/release-notes-cloud-manager/release-notes-cm-current.md)에서 Cloud Manager 월별 릴리스의 전체 목록을 찾을 수 있습니다.

## 콘텐츠 전송 도구 {#ctt-release}

### 릴리스 날짜 {#release-date-ctt}

콘텐츠 전송 도구 v1.9.0의 릴리스 날짜는 2022년 2월 28일입니다.

### 새로운 기능 {#what-is-new-ctt}

* 점검 크기 가드레일 - 콘텐츠 전송 도구 점검 크기 기능을 사용하여 콘텐츠 전송 실패율을 줄일 수 있습니다.  점검 크기 기능을 사용하여 1) 추출하기 전에 `crx-quickstart` 하위 디렉터리에 디스크 공간이 충분한지 결정하고, 2) 마이그레이션 세트 크기를 예측하고 현재 지원되는지 확인할 수 있습니다. 점검 사항 중 하나 또는 두 개 모두 위반한 경우 CTT UI에 경고가 표시됩니다. 이 가드레일을 사용하여 콘텐츠 전송 실패를 방지하고, Adobe 고객 지원 센터와 주도적으로 마이그레이션 옵션에 대해 논의할 수 있습니다. 자세한 내용은 [마이그레이션 세트 크기 및 디스크 공간 확인](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/getting-started-content-transfer-tool.html?lang=ko#migration-set-size)을 참조하십시오.

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
