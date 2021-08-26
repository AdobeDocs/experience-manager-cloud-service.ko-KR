---
title: ' [!DNL Adobe Experience Manager] as a Cloud Service 2021.7.0 릴리스의 릴리스 노트'
description: ' [!DNL Adobe Experience Manager] as a Cloud Service 2021.7.0 릴리스의 릴리스 노트'
source-git-commit: d30d3955e6e5c5aa86c5716735915ef7c75d3e12
workflow-type: tm+mt
source-wordcount: '1315'
ht-degree: 3%

---


# [!DNL Adobe Experience Manager] Cloud Service의 현재 릴리스 노트 {#release-notes}

다음 섹션에서는 Cloud Service으로 현재(최신) 버전의 [!DNL Experience Manager]에 대한 일반 릴리스 노트를 간략하게 설명합니다.

>[!NOTE]
>
>여기에서 이전 버전의 릴리스 정보로 이동할 수 있습니다. 예를 들어, 2020년, 2021년 등의 경우입니다.

>[!NOTE]
>
>릴리스와 직접 관련이 없는 설명서 업데이트에 대한 자세한 내용은 [최근 설명서 업데이트](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html)를 참조하십시오.

## 릴리스 날짜 {#release-date}

[!DNL Cloud Service] 현재 릴리스(2021.7.0)로서 [!DNL Adobe Experience Manager]의 릴리스 날짜는 2021년 7월 29일입니다.
다음 릴리스(2021.8.0)는 2021년 8월 26일입니다.

## 릴리스 비디오 {#release-video}

추가된 기능 요약에 대한 설명이 필요하면 [2021년 7월 릴리스 개요](https://video.tv.adobe.com/v/335580) 비디오를 시청하십시오.

## Experience Manager Foundation as a Cloud Service {#foundation}

### 새로운 기능 {#what-is-new-foundation}

* 보다 유연한 디스패처 구성: 프로젝트를 보다 쉽게 구성할 수 있습니다. 예를 들어 사이트 구조를 반영하는 여러 재작성 규칙 파일을 포함할 수 있습니다. [Dispatcher ](/help/implementing/dispatcher/disp-overview.md#validation-debug) 구성을 활용하여 구성하는 방법을 비롯하여 이 유연한 모드에 대해 알아보십시오.
* 복제 에이전트의 &quot;분배&quot; 탭에 있는 트리 복제 UI는 더 이상 사용되지 않는 것으로 간주되어야 하며 9월 30일 이후에 제거될 예정입니다. [대체 ](/help/operations/replication.md#tree-activation) 복제 전략에 대해 알아봅니다.
* Sling 데이터 소스 지원에 대한 번들 `org.apache.sling.datasource-1.0.4.jar`은 오래된 기능이며 고객이 사용하지 않으므로 제거되었습니다.

## [!DNL Cloud Service]로서의 [!DNL Experience Manager Assets] {#assets}

### [!DNL Assets]의 새로운 기능 {#assets-features}

* 컨텐츠 자동화 기능을 사용하여 [!DNL Experience Manager Assets] API를 활용하여 자산 프로덕션을 규모에 맞게 자동화할 수 있습니다. [!DNL Adobe Creative Cloud] 동일한 자산의 변형을 만드는 데 필요한 시간과 반복 시간을 크게 줄여 컨텐츠 속도를 향상시킵니다. 이 기능은 DAM 내에서 프로그래밍과 작업할 필요가 없습니다. Creative Cloud 통합](/help/assets/cc-api-integration.md)을 사용하여 자산의 변형 생성을 참조하십시오.[

* [!DNL Experience Manager Assets] 에서는 기본적으로  [!DNL Document Cloud] PDF 문서를 미리 볼 수 있는 PDF 뷰어를 포함합니다. 이 기능을 사용하면 파일 처리나 변환 없이 다중 페이지 PDF 파일을 미리 볼 수 있습니다. 이 기능은 [!DNL Experience Manager] 6.5와의 패리티를 향상시킵니다. 뷰어에서 사용할 수 있는 컨트롤에는 확대/축소, 페이지로 이동, 도킹 해제 컨트롤, 전체 화면에서 볼 수 있는 컨트롤이 포함됩니다. 사용자 사례에서도 페이지 및 책갈피를 미리 보고 이동할 수 있습니다. 파일 자체에 대한 주석이 지원되며 PDF 파일 내의 컨텐츠에 대한 주석 및 주석이 향후 릴리스에서 추가됩니다.

   ![PDF 뷰어를  [!DNL Experience Manager] 사용하여 PDF 파일 미리 보기](/help/assets/assets/preview-pdf-file-viewer.png)

* Linkshare 다운로드 기능은 다운로드 속도를 높이는 비동기 다운로드를 사용합니다. [링크 공유를 사용하여 공유된 자산 다운로드](/help/assets/download-assets-from-aem.md#link-share-download)를 참조하십시오.

   ![받은 편지함 다운로드](/help/assets/assets/download-inbox.png)

* 보기 설정이 개선되어 사용자가 기본 보기와 기본 정렬 매개 변수를 선택할 수 있습니다.

   ![보기 설정에서 기본  [!UICONTROL 보기 설정]](/help/assets/assets/view-settings-for-defaults.png)

* 사용자는 속성 설명을 기반으로 폴더를 검색하고 필터링할 수 있습니다.

   ![검색 조건을 사용하여 검색 폴더 필터링](/help/assets/assets/search-folders-via-predicates.png)

### [!DNL Assets] 사전 릴리스 채널에서 사용할 수 있는 새로운 기능 {#assets-prerelease-features}

<!-- TBD: Not sure about GA of these enh. Shall check with the team.

* A user experience enhancements displays the number of assets present in a folder. For more than 1000 assets in a folder, [!DNL Assets] displays 1000+.

  ![Number of assets in a folder are displayed on the interface](/help/assets/assets/browse-folder-number-of-assets.png)

* You can directly apply a metadata schemas to a folder in its [!UICONTROL Properties].

  ![Add metadata schema from folder properties](/help/assets/assets/metadata-schema-folder-properties.png)
-->

* 디지털 자산을 링크로 공유할 때 사용자는 URL을 클립보드에 복사할 수 있습니다. 개선 사항을 통해 자산을 보다 빠르고 편리하게 공유할 수 있습니다.

### [!DNL Assets]에 수정된 버그 {#assets-bugs-fixed}

API `com.day.cq.dam.api.collection.SmartCollection`는 [!DNL Experience Manager]에서 [!DNL Cloud Service]로 사용할 수 없습니다. (CQ-4326322)

## [!DNL Cloud Service]로서의 [!DNL Experience Manager Forms] {#forms}

### [!DNL Forms]의 새로운 기능 {#what-is-new-forms}

* 이제 Automated forms conversion 서비스를 사용하여 [프랑스어, 독일어 및 스페인어 ](https://experienceleague.adobe.com/docs/aem-forms-automated-conversion-service/using/extending-the-default-meta-model.html?#language-specific-meta-model)의 PDF forms을 적응형 양식으로 전환할 수 있습니다.
* 적응형 양식 구성 요소와 관련된 오류를 표시하는 별도의 패널을 템플릿 편집기에 추가했습니다. 모든 적응형 양식 오류를 한 위치에서 통합하고 해결 시간을 줄이는 데 도움이 됩니다.

### [!DNL Forms] 사전 릴리스 채널에서 사용할 수 있는 새로운 기능 {#beta-features-forms}

* **[!DNL AEM Forms as a Cloud Service - Communications]**:  [Communication ](https://experienceleague.adobe.com/docs/experience-manager-forms-cloud-service/forms/aem-forms-cloud-service-communications.html) APIshelp에서는 XDP 템플릿과 XML 데이터를 결합하여 다양한 형식으로 인쇄 문서를 생성합니다. 이 서비스를 통해 동기 모드로 문서를 생성할 수 있습니다. API를 사용하면 다음을 수행할 수 있는 애플리케이션을 만들 수 있습니다.
   * XML 데이터로 템플릿 파일을 채워서 문서를 생성합니다.
   * 비대화형 PDF 인쇄 스트림을 포함하여 다양한 형식으로 출력 양식을 생성합니다.
   * XFA 양식 PDF 및 Adobe Acrobat 양식에서 인쇄 PDF 파일을 생성합니다.

* **Variable Data Externalizer**: 조직에서 관리하는 외부 스토리지 시스템에 AEM Workflow 변수의 데이터를 저장할 수 있습니다.

* **Acrobat 기반 레코드 문서**: XFA 기반 양식 템플릿 외에 기록 문서용 템플릿으로 Adobe Acrobat 양식 PDF(Acroform PDF)를  [사용할 수도 있습니다](https://experienceleague.adobe.com/docs/experience-manager-forms-cloud-service/forms/create-an-adaptive-form/generate-document-of-record-for-non-xfa-based-adaptive-forms.html) .

* **Microsoft Azure 데이터 저장소 커넥터**: 이제 양식 데이터 모델을  [Microsoft Azure 저장소에 연결할 수 있습니다](https://experienceleague.adobe.com/docs/experience-manager-forms-cloud-service/forms/use-form-data-model/configure-azure-storage.html). 적응형 양식 데이터를 검색하고 BLOB으로 Microsoft Azure 저장소에 저장할 수 있습니다.

## CIF 추가 기능 {#cloud-services-cif}

### 새로운 기능 {#what-is-new-cif}

* CIF 코어 구성 요소 v2
   * PDP/PLP URL 및 SEO를 위한 간소화된 구성 및 개선
   * 예정된 변경 사항을 더 잘 파악하기 위해 작성 모드에서 준비된 제품 데이터에 대한 시각적 지표
   * 컨텐츠 및 상거래 페이지를 위한 새 사이트 맵 구성 요소

* 사전 정의된 권장 또는 즉석에서 만든 추천을 사용하여 AEM Storefront에서 Adobe Sensei](https://business.adobe.com/products/magento/product-recommendations.html)에서 제공하는 [Adobe Commerce Sensei 제품 권장 사항을 지원합니다

## [!DNL Cloud Service]로서의 [!DNL Experience Manager Screens] {#screens}

### 버그 수정 {#bug-fixes-screens}

* 이제 만들거나 업데이트하는 동안 콘텐츠 공급자 설정의 유효성을 검사합니다.

* 모든 디스플레이 보기에는 폴더 열이 있습니다.

* 스크린 컨텐츠 구조를 확장할 수 있습니다.

* `bulk-offline-update-service` 일부 환경에 대한 모든 권한이 누락되었습니다.

* 새 screens 클라우드 설명서에 일치하도록 도움말 링크를 업데이트했습니다.

* 재생 목록을 할당 취소하고 플레이어가 할당된 재생 목록을 제거할 수 없습니다. 이제 작동합니다.

* 이제 &quot;ALL&quot; 캐시가 지워지면 플레이어가 자산을 다시 다운로드합니다.

* 이제 *종료 시간*&#x200B;이 다음 날에 대해 설정된 경우 반복 예약이 작동합니다.

* `Back&Forward` 이제 Cloud Service UI로 Screens에서 작동합니다.

* 이름이 동일하지만 네임스페이스가 다른 태그를 일찍 만들 수 없습니다.

## Cloud Service으로 Experience Manager에 대한 XML 설명서 {#xml-documentation}

### 새로운 기능 {#what-is-new-xml-documentation}

일반적으로 Cloud Service으로 Experience Manager에 대한 XML 설명서를 사용할 수 있습니다. Cloud Service 고객으로서 Experience Manager은 XML 설명서를 획득하고, Experience Manager 사이트를 비롯한 여러 채널에서 기술 컨텐츠를 가져오고, 만들고, 관리하고, 전달할 수 있습니다.

## Cloud Manager {#cloud-manager}

이 섹션에서는 AEM as a Cloud Service 2021.7.0에 있는 Cloud Manager 릴리스 노트를 간략하게 설명합니다.

### 릴리스 날짜 {#release-cm-july}

AEM as a Cloud Service 2021.7.0의 Cloud Manager 릴리스 날짜는 2021년 7월 15일입니다.
다음 릴리스는 2021년 8월 12일에 예정되어 있습니다.

### 새로운 기능 {#what-is-new-cm-july}

* 고객은 이제 Cloud Manager 빌드 프로세스에 Azul 8 및 11개의 JDK를 사용할 수 있으며 이러한 JDK 중 하나를 도구 체인 호환 Maven 플러그인 *또는 전체 Maven 프로세스 실행에 사용하도록 선택할 수 있습니다.*

* 이제 아웃바운드 송신 IP가 빌드 단계 로그 파일에 기록됩니다.

* 이전 버전의 AEM을 실행하는 단계 및 프로덕션 환경에서는 **Update Available** 상태를 보고합니다.

* 지원되는 최대 SSL 인증서는 프로그램당 20개로 증가했습니다.

* 구성할 수 있는 최대 도메인 수가 환경당 500개로 늘어났습니다.

* **Git** 관리 단추가 **Access Git Info**&#x200B;로 검색되었으며 대화 상자가 시각적으로 새로 고침되었습니다.

* Cloud Manager에서 사용하는 AEM Project Archetype 버전이 버전 28로 업데이트되었습니다.

### 버그 수정 {#bug-fixes-cm-july}

* 경우에 따라 IP 허용 목록을 환경에 바인딩할 때 미리 보기 옵션을 사용할 수 없었습니다.

* 존재하지 않는 실행을 위한 실행 세부 사항 페이지로 수동으로 탐색해도 오류가 표시되지 않고 끝없이 로드되는 화면만 표시됩니다.

* 최대 SSL 인증서 수에 도달했을 때 표시되는 오류 메시지가 표시되지 않습니다.

* 경우에 따라 **개요** 페이지의 파이프라인 카드에 표시된 릴리스 버전에서 불일치가 발생할 수 있습니다.

* 프로그램 추가 마법사에서 생성 후 이름을 변경할 수 없다고 잘못 명시했습니다.

### 알려진 문제 {#known-issues-cm-july}

Azul JDK를 사용하도록 전환하는 고객은 Azul JDK에 오류가 없는 모든 기존 애플리케이션이 컴파일되는 것은 아니라는 것을 알고 있어야 합니다. 전환하기 전에 로컬로 테스트하는 것이 좋습니다.

## Cloud Acceleration Manager {#cam}

### 릴리스 날짜 {#release-date-july-cam}

Cloud Acceleration Manager 릴리스 날짜는 2021년 7월 15일입니다.

### 새로운 기능 {#what-is-new-cam}

Cloud Acceleration Manager는 Cloud Service에서 라이브로 전환하는 계획에서부터 전환 여정 전반에 걸쳐 IT 팀을 안내하도록 설계된 클라우드 기반 애플리케이션입니다. AEM as a Cloud Service으로 여정의 모든 단계에서 도움이 되는 Adobe 권장 우수 사례, 팁, 설명서 및 도구를 사용하여 성공적인 마이그레이션을 위해 팀을 설정합니다. 자세한 내용은 [여기](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-acceleration-manager/using-cam/getting-started-cam.html?lang=en)를 참조하십시오.

>[!NOTE]
>
> 이 [Cloud Acceleration Manager 데모 비디오](https://video.tv.adobe.com/v/335547)를 확인하십시오.
