---
title: ' [!DNL Adobe Experience Manager] as a Cloud Service의 2021.7.0 릴리스 정보입니다.'
description: ' [!DNL Adobe Experience Manager] as a Cloud Service의 2021.7.0 릴리스 정보입니다.'
exl-id: 848f6a29-2e0f-4976-8ed7-6b7f69408c1b
source-git-commit: 430179bf13c1fff077c515eed0676430e9e7f341
workflow-type: tm+mt
source-wordcount: '1316'
ht-degree: 26%

---

# [!DNL Adobe Experience Manager] as a Cloud Service 최신 릴리스 정보 {#release-notes}

다음 섹션에서는 [!DNL Experience Manager] as a Cloud Service의 최신 버전 일반 릴리스 정보에 대해 간략히 소개합니다.

>[!NOTE]
>
>여기에서 이전 버전의 릴리스 정보로 이동할 수 있습니다. 예를 들어, 2020년, 2021년 등의 경우입니다.

>[!NOTE]
>
>릴리스와 직접적으로 관련되지 않는 설명서 업데이트의 세부 정보는 [설명서 업데이트](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html)를 참조하십시오.

## 릴리스 날짜 {#release-date}

의 릴리스 날짜 [!DNL Adobe Experience Manager] 로서의 [!DNL Cloud Service] 현재 릴리스(2021.7.0)는 2021년 7월 29일입니다.
다음 릴리스(2021.8.0)는 2021년 8월 26일입니다.

## 릴리스 비디오 {#release-video}

을(를) 보십시오. [2021년 7월 릴리스 개요](https://video.tv.adobe.com/v/335580) 비디오 를 참조하십시오.

## Experience Manager 기초 as a Cloud Service {#foundation}

### 새로운 기능 {#what-is-new-foundation}

* 보다 유연한 디스패처 구성: 프로젝트를 보다 쉽게 구성할 수 있습니다. 예를 들어 사이트 구조를 반영하는 여러 재작성 규칙 파일을 포함할 수 있습니다. [알아보기](/help/implementing/dispatcher/disp-overview.md#validation-debug) 이 유연한 모드는 dispatcher 구성을 활용하여 구성하는 방법을 제공합니다.
* 복제 에이전트의 &quot;분배&quot; 탭에 있는 트리 복제 UI는 더 이상 사용되지 않는 것으로 간주되어야 하며 9월 30일 이후에 제거될 예정입니다. [알아보기](/help/operations/replication.md#tree-activation) 대체 복제 전략.
* 번들 `org.apache.sling.datasource-1.0.4.jar` Sling 데이터 소스 지원은 오래된 기능이 있고 고객이 사용하지 않으므로 제거되었습니다.

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### [!DNL Assets]의 새로운 기능 {#assets-features}

* 콘텐츠 자동화 기능을 사용하면 [!DNL Experience Manager Assets] 활용 [!DNL Adobe Creative Cloud] 자산 프로덕션을 규모에 맞게 자동화하는 API 동일한 자산의 변형을 만드는 데 필요한 시간과 반복 시간을 크게 줄여 컨텐츠 속도를 향상시킵니다. 이 기능은 DAM 내에서 프로그래밍과 작업할 필요가 없습니다. 자세한 내용은 [Creative Cloud 통합을 사용하여 자산의 변형 생성](/help/assets/cc-api-integration.md).

* [!DNL Experience Manager Assets] include [!DNL Document Cloud] PDF 뷰어 을 사용하여 기본적으로 PDF 문서를 미리 볼 수 있습니다. 이 기능을 사용하면 파일 처리나 변환 없이 다중 페이지 PDF 파일을 미리 볼 수 있습니다. 이 기능은 패리티를 다음과 같이 향상시킵니다. [!DNL Experience Manager] 6.5. 뷰어에서 사용할 수 있는 컨트롤에는 확대/축소, 페이지로 이동, 컨트롤 도킹 해제 및 전체 화면 보기가 포함됩니다. 사용자 사례에서도 페이지 및 책갈피를 미리 보고 이동할 수 있습니다. 파일 자체에 대한 주석이 지원되며 PDF 파일 내의 컨텐츠에 대한 주석 및 주석이 향후 릴리스에서 추가됩니다.

   ![에서 PDF 파일 미리 보기 [!DNL Experience Manager] PDF 뷰어 사용](/help/assets/assets/preview-pdf-file-viewer.png)

* Linkshare 다운로드 기능은 다운로드 속도를 높이는 비동기 다운로드를 사용합니다. 자세한 내용은 [링크 공유를 사용하여 공유된 자산 다운로드](/help/assets/download-assets-from-aem.md#link-share-download).

   ![받은 편지함 다운로드](/help/assets/assets/download-inbox.png)

* 보기 설정이 개선되어 사용자가 기본 보기와 기본 정렬 매개 변수를 선택할 수 있습니다.

   ![에서 기본 보기 설정 [!UICONTROL 설정 보기]](/help/assets/assets/view-settings-for-defaults.png)

* 사용자는 속성 설명을 기반으로 폴더를 검색하고 필터링할 수 있습니다.

   ![검색 조건을 사용하여 검색 폴더 필터링](/help/assets/assets/search-folders-via-predicates.png)

### 에서 사용할 수 있는 새로운 기능 [!DNL Assets] 사전 릴리스 채널 {#assets-prerelease-features}

<!-- TBD: Not sure about GA of these enh. Shall check with the team.

* A user experience enhancements displays the number of assets present in a folder. For more than 1000 assets in a folder, [!DNL Assets] displays 1000+.

  ![Number of assets in a folder are displayed on the interface](/help/assets/assets/browse-folder-number-of-assets.png)

* You can directly apply a metadata schemas to a folder in its [!UICONTROL Properties].

  ![Add metadata schema from folder properties](/help/assets/assets/metadata-schema-folder-properties.png)
-->

* 디지털 자산을 링크로 공유할 때 사용자는 URL을 클립보드에 복사할 수 있습니다. 개선 사항을 통해 자산을 보다 빠르고 편리하게 공유할 수 있습니다.

### [!DNL Assets]의 수정된 버그 {#assets-bugs-fixed}

API `com.day.cq.dam.api.collection.SmartCollection` 에서 사용할 수 없음 [!DNL Experience Manager] 로서의 [!DNL Cloud Service]. (CQ-4326322)

## [!DNL Experience Manager Forms] 로서의 [!DNL Cloud Service] {#forms}

### [!DNL Forms]의 새로운 기능 {#what-is-new-forms}

* 이제 자동 양식 전환 서비스를 사용하여 [프랑스어, 독일어 및 스페인어로 된 PDF 양식을 적응형 양식으로 변환](https://experienceleague.adobe.com/docs/aem-forms-automated-conversion-service/using/extending-the-default-meta-model.html?#language-specific-meta-model)할 수 있습니다.
* 템플릿 편집기에 별도의 패널을 추가하여 적응형 양식 구성 요소와 관련된 오류를 표시합니다. 모든 적응형 양식 오류를 한 위치에서 통합하고 해결 시간을 단축하는 데 도움이 됩니다.

### [!DNL Forms] 프리릴리스 채널에서 사용할 수 있는 새로운 기능 {#beta-features-forms}

* **[!DNL AEM Forms as a Cloud Service - Communications]**: [커뮤니케이션 API](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/using-communications/aem-forms-cloud-service-communications.html)를 통해 XDP 템플릿과 XML 데이터를 결합하여 다양한 형식의 인쇄 문서를 생성할 수 있습니다. 이 서비스를 사용하면 동기 모드로 문서를 생성할 수 있습니다. API를 사용하면 다음과 같은 기능을 제공하는 애플리케이션을 만들 수 있습니다.
   * XML 데이터로 템플릿 파일을 채워 문서를 생성합니다.
   * 비대화형 PDF 인쇄 스트림을 포함하여 다양한 형식의 출력 양식을 생성합니다.
   * XFA 양식 PDF 및 Adobe Acrobat Form에서 인쇄 PDF 파일을 생성합니다.

* **변수 데이터 외부화**: 조직에서 관리하는 외부 스토리지 시스템에 AEM Workflow 변수 데이터를 저장할 수 있습니다.

* **Acroform 기반 기록 문서**: XFA 기반 양식 템플릿 외에 [기록 문서의 템플릿으로도 Adobe Acrobat Form PDF(Acroform PDF)를 사용](https://experienceleague.adobe.com/docs/experience-manager-forms-cloud-service/forms/create-an-adaptive-form/generate-document-of-record-for-non-xfa-based-adaptive-forms.html)할 수 있습니다.

* **Microsoft Azure 데이터 스토어 커넥터**: 이제 [양식 데이터 모델을 Microsoft Azure Storage에 연결](https://experienceleague.adobe.com/docs/experience-manager-forms-cloud-service/forms/use-form-data-model/configure-azure-storage.html)할 수 있습니다. 이를 통해, 적응형 양식 데이터를 검색하여 Microsoft Azure Storage에 BLOB로 저장할 수 있습니다.

## CIF 추가 기능 {#cloud-services-cif}

### 새로운 기능 {#what-is-new-cif}

* CIF 코어 구성 요소 v2
   * PDP/PLP URL 및 SEO를 위한 간소화된 구성 및 개선
   * 예정된 변경 사항을 더 잘 파악하기 위해 작성 모드에서 준비된 제품 데이터에 대한 시각적 지표
   * 컨텐츠 및 상거래 페이지를 위한 새 사이트 맵 구성 요소

* 지원 대상 [Adobe Commerce Sensei 제품 권장 사항, Adobe Sensei 제공](https://business.adobe.com/products/magento/product-recommendations.html) 미리 정의되거나 즉시 작성된 권장 사항을 사용하는 AEM Storefront

## [!DNL Experience Manager Screens] 로서의 [!DNL Cloud Service] {#screens}

### 버그 수정 {#bug-fixes-screens}

* 이제 만들거나 업데이트하는 동안 콘텐츠 공급자 설정의 유효성을 검사합니다.

* 모든 디스플레이 보기에는 폴더 열이 있습니다.

* 스크린 컨텐츠 구조를 확장할 수 있습니다.

* `bulk-offline-update-service` 일부 환경에 대한 모든 권한이 누락되었습니다.

* 새 screens 클라우드 설명서에 일치하도록 도움말 링크를 업데이트했습니다.

* 재생 목록을 할당 취소하고 플레이어가 할당된 재생 목록을 제거할 수 없습니다. 이제 작동합니다.

* 이제 &quot;ALL&quot; 캐시가 지워지면 플레이어가 자산을 다시 다운로드합니다.

* 이제 반복 예약이 작동하는 경우 *종료 시간* 는 다음 날 동안 설정됩니다.

* `Back&Forward` 이제 Screens as a Cloud Service UI에서 작동합니다.

* 이름이 동일하지만 네임스페이스가 다른 태그를 일찍 만들 수 없습니다.

## XML Documentation for Experience Manager as a Cloud Service {#xml-documentation}

### 새로운 기능 {#what-is-new-xml-documentation}

일반적으로 Experience Manager as a Cloud Service용 XML Documentation을 사용할 수 있습니다. 이 솔루션을 통해 Experience Manager as a Cloud Service 고객은 XML Documentation addon 을 통해 Experience Manager Sites을 비롯한 여러 채널에서 기술 콘텐츠를 가져오고, 만들고, 관리하고, 전달할 수 있습니다.

## Cloud Manager {#cloud-manager}

이 섹션에서는 AEM as a Cloud Service 2021.7.0의 Cloud Manager 릴리스 정보에 대해 간략히 소개합니다.

### 릴리스 날짜 {#release-cm-july}

AEM as a Cloud Service 2021.7.0의 Cloud Manager 릴리스 날짜는 2021년 7월 15일입니다.
다음 릴리스는 2021년 8월 12일에 예정되어 있습니다.

### 새로운 기능 {#what-is-new-cm-july}

* 고객은 이제 Cloud Manager 빌드 프로세스에 Azul 8 및 11개의 JDK를 사용할 수 있으며 이러한 JDK 중 하나를 도구 체인 호환 Maven 플러그인에 사용하도록 선택할 수 있습니다 *또는* 전체 Maven 프로세스 실행

* 이제 아웃바운드 송신 IP가 빌드 단계 로그 파일에 기록됩니다.

* 이전 버전의 AEM을 실행하는 단계 및 프로덕션 환경에서는 다음 상태를 보고합니다. **업데이트 사용 가능**.

* 지원되는 최대 SSL 인증서는 프로그램당 20개로 증가했습니다.

* 구성할 수 있는 최대 도메인 수가 환경당 500개로 늘어났습니다.

* 다음 **Git 관리** 버튼이 **Git 정보에 액세스** 대화 상자가 시각적으로 새로 고침되었습니다.

* Cloud Manager에서 사용하는 AEM Project Archetype 버전이 버전 28로 업데이트되었습니다.

### 버그 수정 {#bug-fixes-cm-july}

* 경우에 따라 IP 허용 목록을 환경에 바인딩할 때 미리 보기 옵션을 사용할 수 없었습니다.

* 존재하지 않는 실행을 위한 실행 세부 사항 페이지로 수동으로 탐색해도 오류가 표시되지 않고 끝없이 로드되는 화면만 표시됩니다.

* 최대 SSL 인증서 수에 도달했을 때 표시되는 오류 메시지가 표시되지 않습니다.

* 경우에 따라 의 파이프라인 카드에 표시된 릴리스 버전에서 차이가 있을 수 있습니다 **개요** 페이지.

* 프로그램 추가 마법사에서 생성 후 이름을 변경할 수 없다고 잘못 명시했습니다.

### 알려진 문제 {#known-issues-cm-july}

Azul JDK를 사용하도록 전환하는 고객은 Azul JDK에 오류가 없는 모든 기존 애플리케이션이 컴파일되는 것은 아니라는 것을 알고 있어야 합니다. 전환하기 전에 로컬로 테스트하는 것이 좋습니다.

## Cloud Acceleration Manager {#cam}

### 릴리스 날짜 {#release-date-july-cam}

Cloud Acceleration Manager 릴리스 날짜는 2021년 7월 15일입니다.

### 새로운 기능 {#what-is-new-cam}

Cloud Acceleration Manager는 Cloud Service에서 라이브로 전환하는 계획에서부터 전환 여정 전반에 걸쳐 IT 팀을 안내하도록 설계된 클라우드 기반 애플리케이션입니다. AEM as a Cloud Service으로 여정의 모든 단계에서 도움이 되는 Adobe 권장 우수 사례, 팁, 설명서 및 도구를 사용하여 성공적인 마이그레이션을 위해 팀을 설정합니다. 추가 정보 [여기](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-acceleration-manager/using-cam/getting-started-cam.html?lang=en).

>[!NOTE]
>
> 확인 [Cloud Acceleration Manager 데모 비디오](https://video.tv.adobe.com/v/335547).
