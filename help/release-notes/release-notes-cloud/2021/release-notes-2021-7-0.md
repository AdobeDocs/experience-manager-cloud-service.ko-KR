---
title: ' [!DNL Adobe Experience Manager] as a Cloud Service의 2021.7.0 릴리스 정보입니다.'
description: ' [!DNL Adobe Experience Manager] as a Cloud Service의 2021.7.0 릴리스 정보입니다.'
exl-id: 848f6a29-2e0f-4976-8ed7-6b7f69408c1b
source-git-commit: cc6565121a76f70b958aa9050485e0553371f3a3
workflow-type: tm+mt
source-wordcount: '1316'
ht-degree: 50%

---

# [!DNL Adobe Experience Manager] as a Cloud Service 최신 릴리스 정보 {#release-notes}

다음 섹션에서는 [!DNL Experience Manager] as a Cloud Service의 최신 버전 일반 릴리스 정보에 대해 간략히 소개합니다.

>[!NOTE]
>
>여기에서 2020, 2021 버전 등 이전 버전의 릴리스 정보로 이동할 수 있습니다.

>[!NOTE]
>
>릴리스와 직접적으로 관련되지 않는 설명서 업데이트의 세부 정보는 [설명서 업데이트](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html)를 참조하십시오.

## 릴리스 일자 {#release-date}

의 릴리스 날짜 [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] 현재 릴리스(2021.7.0)는 2021년 7월 29일입니다.
다음 릴리스(2021.8.0) 날짜는 2021년 8월 26일입니다.

## 릴리스 비디오 {#release-video}

다음을 살펴보십시오. [2021년 7월 릴리스 개요](https://video.tv.adobe.com/v/335580) 추가된 기능에 대한 요약을 보려면 비디오 를 사용하십시오.

## Experience Manager 재단 as a Cloud Service {#foundation}

### 새로운 기능 {#what-is-new-foundation}

* 보다 유연한 Dispatcher 구성: 프로젝트를 보다 쉽게 구성할 수 있습니다. 예를 들어 이제 사이트 구조를 반영하는 여러 재작성 규칙 파일을 포함할 수 있습니다. [다음에 대해 알아보기](/help/implementing/dispatcher/disp-overview.md#validation-debug) 이 유연한 모드는 이를 활용하기 위해 dispatcher 구성을 구성하는 방법을 포함합니다.
* 복제 에이전트의 &quot;배포&quot; 탭 아래에 있는 트리 복제 UI는 더 이상 사용되지 않는 것으로 간주되어 9월 30일 이후에 제거될 예정입니다. [다음에 대해 알아보기](/help/operations/replication.md#tree-activation) 대체 복제 전략
* 번들 `org.apache.sling.datasource-1.0.4.jar` sling 데이터 소스 지원은 기능이 뒤쳐지고 고객이 사용하지 않기 때문에 제거되었습니다.

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### [!DNL Assets]의 새로운 기능 {#assets-features}

* 콘텐츠 자동화 기능을 통해 다음과 같은 작업을 수행할 수 있습니다 [!DNL Experience Manager Assets] 활용 [!DNL Adobe Creative Cloud] 규모에 맞게 에셋 제작을 자동화하는 API입니다. 동일한 에셋의 변형을 만드는 데 소요되는 시간과 필요한 반복을 크게 줄여 콘텐츠 속도를 향상시킵니다. 이 기능은 프로그래밍이 필요하지 않으며 DAM 내에서 작동합니다. 다음을 참조하십시오 [Creative Cloud 통합을 사용하여 에셋 변형 생성](/help/assets/cc-api-integration.md).

* [!DNL Experience Manager Assets] 다음을 포함: [!DNL Document Cloud] PDF 뷰어를 사용하여 PDF 문서를 기본적으로 미리 볼 수 있습니다. 이 기능을 사용하면 다중 페이지 PDF 파일을 파일 처리 또는 변환 없이 미리 볼 수 있습니다. 이 기능은 를 사용하여 패리티를 향상시킵니다. [!DNL Experience Manager] 6.5. 뷰어에서 사용할 수 있는 컨트롤에는 확대/축소, 페이지로 이동, 컨트롤 분리 및 전체 화면으로 보기가 포함됩니다. 사용자 사례에서도 페이지를 미리 보고 페이지 및 책갈피로 이동합니다. 파일 자체에 대한 댓글이 지원되며 PDF 파일 내에 댓글 달기 및 콘텐츠에 대한 주석은 향후 릴리스에 추가됩니다.

   ![에서 PDF 파일 미리 보기 [!DNL Experience Manager] PDF 뷰어 사용](/help/assets/assets/preview-pdf-file-viewer.png)

* Linkshare 다운로드 기능은 다운로드 속도를 향상시키는 비동기 다운로드를 사용합니다. 다음을 참조하십시오 [링크 공유를 사용하여 공유된 에셋 다운로드](/help/assets/download-assets-from-aem.md#link-share-download).

   ![받은 편지함 다운로드](/help/assets/assets/download-inbox.png)

* 사용자가 기본 보기와 기본 정렬 매개 변수를 선택할 수 있도록 보기 설정이 개선되었습니다.

   ![에서 기본 보기 설정 [!UICONTROL 설정 보기]](/help/assets/assets/view-settings-for-defaults.png)

* 사용자는 속성 술어에 따라 폴더를 검색하고 필터링할 수 있습니다.

   ![검색 술어를 사용하여 검색 폴더 필터링](/help/assets/assets/search-folders-via-predicates.png)

### 에서 사용할 수 있는 새로운 기능 [!DNL Assets] 프리릴리스 채널 {#assets-prerelease-features}

<!-- TBD: Not sure about GA of these enh. Shall check with the team.

* A user experience enhancements displays the number of assets present in a folder. For more than 1000 assets in a folder, [!DNL Assets] displays 1000+.

  ![Number of assets in a folder are displayed on the interface](/help/assets/assets/browse-folder-number-of-assets.png)

* You can directly apply a metadata schemas to a folder in its [!UICONTROL Properties].

  ![Add metadata schema from folder properties](/help/assets/assets/metadata-schema-folder-properties.png)
-->

* 디지털 에셋을 링크로 공유하면 사용자는 URL을 클립보드에 복사할 수 있습니다. 향상된 기능을 통해 에셋을 보다 빠르고 편리한 방법으로 공유할 수 있습니다.

### [!DNL Assets]의 수정된 버그 {#assets-bugs-fixed}

API `com.day.cq.dam.api.collection.SmartCollection` 에서 사용할 수 없음 [!DNL Experience Manager] as a [!DNL Cloud Service]. (CQ-4326322)

## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

### [!DNL Forms]의 새로운 기능 {#what-is-new-forms}

* 이제 자동 양식 전환 서비스를 사용하여 [프랑스어, 독일어 및 스페인어로 된 PDF 양식을 적응형 양식으로 변환](https://experienceleague.adobe.com/docs/aem-forms-automated-conversion-service/using/extending-the-default-meta-model.html?#language-specific-meta-model)할 수 있습니다.
* 템플릿 편집기에 별도의 패널을 추가하여 적응형 양식 구성 요소와 관련된 오류를 표시합니다. 모든 적응형 양식 오류를 한 위치에서 통합하고 해결 시간을 단축하는 데 도움이 됩니다.

### [!DNL Forms] 프리릴리스 채널에서 사용할 수 있는 새로운 기능 {#beta-features-forms}

* **[!DNL AEM Forms as a Cloud Service - Communications]**: [커뮤니케이션 API](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/using-communications/aem-forms-cloud-service-communications.html)를 통해 XDP 템플릿과 XML 데이터를 결합하여 다양한 형식의 인쇄 문서를 생성할 수 있습니다. 이 서비스를 사용하면 동기화 모드에서 문서를 생성할 수 있습니다. API를 사용하면 다음과 같은 기능을 제공하는 애플리케이션을 만들 수 있습니다.
   * XML 데이터로 템플릿 파일을 채워 문서를 생성합니다.
   * 비대화형 PDF 인쇄 스트림을 포함하여 다양한 형식의 출력 양식을 생성합니다.
   * XFA 양식 PDF 및 Adobe Acrobat Form에서 인쇄 PDF 파일을 생성합니다.

* **변수 데이터 외부화**: 조직에서 관리하는 외부 스토리지 시스템에 AEM Workflow 변수 데이터를 저장할 수 있습니다.

* **Acroform 기반 기록 문서**: XFA 기반 양식 템플릿 외에 [기록 문서의 템플릿으로도 Adobe Acrobat Form PDF(Acroform PDF)를 사용](https://experienceleague.adobe.com/docs/experience-manager-forms-cloud-service/forms/create-an-adaptive-form/generate-document-of-record-for-non-xfa-based-adaptive-forms.html)할 수 있습니다.

* **Microsoft Azure 데이터 스토어 커넥터**: 이제 [양식 데이터 모델을 Microsoft Azure Storage에 연결](https://experienceleague.adobe.com/docs/experience-manager-forms-cloud-service/forms/use-form-data-model/configure-azure-storage.html)할 수 있습니다. 이를 통해, 적응형 양식 데이터를 검색하여 Microsoft Azure Storage에 BLOB로 저장할 수 있습니다.

## CIF 추가 기능 {#cloud-services-cif}

### 새로운 기능 {#what-is-new-cif}

* CIF 코어 구성 요소 v2
   * PDP/PLP URL 및 SEO에 대한 간소화된 개선된 구성
   * 향후 변경 사항에 대한 가시성을 개선하기 위해 작성 모드에서 스테이징된 제품 데이터에 대한 시각적 표시기
   * 콘텐츠 및 상거래 페이지를 위한 새 사이트맵 구성 요소

* 지원 대상 [Adobe Commerce Sensei 제품 추천, Adobe Sensei 제공](https://business.adobe.com/products/magento/product-recommendations.html) 미리 정의되거나 즉석에서 생성된 권장 사항을 사용하는 AEM Storefront에서

## [!DNL Experience Manager Screens] as a [!DNL Cloud Service] {#screens}

### 버그 수정 {#bug-fixes-screens}

* 이제 만들거나 업데이트하는 동안 콘텐츠 공급자 설정의 유효성을 검사합니다.

* 모든 디스플레이 보기에는 폴더 열이 있습니다.

* Screens 콘텐츠 구조를 확장할 수 있습니다.

* `bulk-offline-update-service` 일부 환경에 대한 모든 권한이 누락되었습니다.

* 새 screens cloud 설명서와 일치하도록 도움말 링크가 업데이트되었습니다.

* 이제 플레이리스트 할당 해제 및 플레이어가 할당된 플레이리스트 제거 허용 안 함 기능이 작동합니다.

* 이제 &quot;ALL&quot; 캐시가 지워지면 플레이어에서 자산을 다시 다운로드합니다.

* 다음과 같은 경우 반복 예약이 작동합니다. *종료 시간* 은 다음 날로 설정됩니다.

* `Back&Forward` 이제 Screens as a Cloud Service UI에서 작동합니다.

* 이름은 같지만 네임스페이스가 다른 태그를 이전에 만들 수 없습니다.

## XML Documentation for Experience Manager as a Cloud Service {#xml-documentation}

### 새로운 기능 {#what-is-new-xml-documentation}

XML Documentation for Experience Manager as a Cloud Service은 일반적으로 사용할 수 있습니다. 이를 통해 Experience Manager as a Cloud Service 고객은 XML Documentation을 포함한 여러 채널에서 기술 콘텐츠를 가져오고, 만들고, 관리하고, 전달할 수 있는 Experience Manager Sites 추가 기능을 확보할 수 있습니다.

## Cloud Manager {#cloud-manager}

이 섹션에서는 AEM as a Cloud Service 2021.7.0의 Cloud Manager 릴리스 정보에 대해 간략히 소개합니다.

### 릴리스 일자 {#release-cm-july}

AEM as a Cloud Service 2021.7.0의 Cloud Manager 릴리스 일자는 2021년 7월 15일입니다.
다음 릴리스는 2021년 8월 12일에 예정되어 있습니다.

### 새로운 기능 {#what-is-new-cm-july}

* 이제 고객은 Cloud Manager 빌드 프로세스에 Azul 8 및 11 JDK를 사용할 수 있으며 툴체인 호환 Maven 플러그인 *또는* 전체 Maven 프로세스 실행에 이러한 JDK 중 하나를 사용하도록 선택할 수 있습니다.

* 이제 아웃바운드 이그레스 IP가 빌드 단계 로그 파일에 기록됩니다.

* 이전 버전의 AEM을 실행하는 단계 및 프로덕션 환경에서는 이제 **업데이트 사용 가능** 상태가 보고됩니다.

* 지원되는 최대 SSL 인증서가 프로그램당 20개로 증가했습니다.

* 구성할 수 있는 최대 도메인 수가 환경당 500개로 증가했습니다.

* **Git 관리** 버튼의 제목이 **Git 정보 액세스**&#x200B;로 변경되었으며 대화 상자가 시각적으로 새로 고쳐졌습니다.

* Cloud Manager에서 사용하는 AEM Project Archetype이 버전 28로 업데이트되었습니다.

### 버그 수정 {#bug-fixes-cm-july}

* IP 허용 목록을 환경에 바인딩할 때 미리보기를 사용할 수 없는 경우가 있었습니다.

* 존재하지 않는 실행의 실행 세부 정보 페이지로 수동 이동하면 오류가 표시되지 않고 끝없는 로딩 화면만 표시됩니다.

* 최대 SSL 인증서 수에 도달했을 때 표시되는 오류 메시지가 도움이 되지 않았습니다.

* 경우에 따라 **개요** 페이지의 파이프라인 카드에 표시된 릴리스 버전에 불일치가 있을 수 있습니다.

* 프로그램 추가 마법사에서 이름을 만든 후에는 이름을 변경할 수 없다고 잘못 설명되어 있었습니다.

### 알려진 문제 {#known-issues-cm-july}

Azul JDK를 사용하도록 전환하는 고객은 모든 기존 애플리케이션이 Azul JDK에서 오류 없이 컴파일되지 않는다는 점에 유의해야 합니다. 전환하기 전에 로컬에서 테스트하는 것이 좋습니다.

## Cloud Acceleration Manager {#cam}

### 릴리스 일자 {#release-date-july-cam}

Cloud Acceleration Manager 의 릴리스 날짜는 2021년 7월 15일입니다.

### 새로운 기능 {#what-is-new-cam}

Cloud Acceleration Manager는 계획 수립에서 Cloud Service로의 이행까지의 전환 과정 전반에 걸쳐 IT 팀을 안내하도록 설계된 클라우드 기반의 애플리케이션입니다. Adobe가 권장하는 모범 사례, 팁, 문서 및 도구를 사용하여 AEM as a Cloud Service로 전환하는 과정의 모든 단계에서 성공적인 마이그레이션을 위해 팀을 구성하십시오. 자세히 알아보기 [여기](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-acceleration-manager/using-cam/getting-started-cam.html?lang=en).

>[!NOTE]
>
> 확인 [Cloud Acceleration Manager 데모 비디오](https://video.tv.adobe.com/v/335547).
