---
title: Cloud Service으로 [!DNL Adobe Experience Manager] 에 대한 현재 릴리스 노트입니다.
description: Cloud Service으로 [!DNL Adobe Experience Manager] 에 대한 현재 릴리스 노트입니다.
exl-id: a2d56721-502c-4f4e-9b72-5ca790df75c5
translation-type: tm+mt
source-git-commit: affe1f0be3f3448e15787cdd831474e0a9d5de6b
workflow-type: tm+mt
source-wordcount: '1588'
ht-degree: 3%

---

# [!DNL Adobe Experience Manager] Cloud Service {#release-notes}의 현재 릴리스 노트

다음 섹션에서는 Cloud Service의 현재(최신) 버전 [!DNL Experience Manager]에 대한 일반적인 릴리스 노트에 대해 간략하게 설명합니다.

>[!NOTE]
>여기에서 이전 버전의 릴리스 노트를 탐색할 수 있습니다.예를 들어, 2020, 2021 등에 있는 경우

>[!NOTE]
>
>릴리스와 직접 관련이 없는 설명서 업데이트에 대한 자세한 내용은 [최근 설명서 업데이트](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html)를 참조하십시오.

## 릴리스 날짜 {#release-date}

Cloud Service으로 [!DNL Adobe Experience Manager]에 대한 릴리스 날짜는 2021년 3월 25일입니다.
다음 릴리스(2021.4.0)은 2021년 4월 29일에 제공됩니다.

## [!DNL Adobe Experience Manager Sites] Cloud Service  {#sites}

* [이제 간단한 구성을 통해 ](/help/sites-cloud/authoring/features/enable-pwa.md) 사이트의 점진적 웹 앱(PWA) 버전을 프로젝트 수준에서 사용할 수 있습니다.
* 컨텐츠 조각 모델 확장 - 이제 여러 줄 텍스트 데이터 유형을 다중 필드 목록으로 정의할 수 있습니다.
* 컨텐츠 조각 편집기 UX 개선 사항 - 중첩된 하위 조각이 이제 브레드크럼에 표시되고 게시, 저장 및 저장 및 종료 작업의 향상된 보기

## [!DNL Cloud Service]로서의 [!DNL Adobe Experience Manager Assets] {#assets}

### [!DNL Assets] {#what-is-new-assets}의 새로운 기능

<!-- TBD: refine this list of features and enh. for Feb release.

Customers using the Connected Assets feature can now easily view and track assets used on remote Sites instances. This affords customers a complete view of being used across all Sites powered pages, allowing for better tracking, management, and brand consistency.  

Indicators for expired, approved, and rejected statuses now available for assets in Column view.

Ability to select a root path. select if a minimum number of tags is required. 

Add a Boolean or radio widget type to metadata schema setup. -->

* [!DNL Experience Manager] 지원되는 핵심 구성 요소에서 이미지 사용을 지원하기 위해 연결된  [!DNL Dynamic Media] 자산 기능을 확장합니다. [연결된 자산 사용](/help/assets/use-assets-across-connected-assets-instances.md)을 참조하십시오.
* Experience Manager 관리자는 특정 날짜 또는 시간에 일괄 자산 지정을 예약할 수 있습니다. 또한 관리자는 날짜 및 시간을 기반으로 반복되는 작업을 예약할 수 있습니다. [일괄 자산 통합](/help/assets/add-assets.md#asset-bulk-ingestor)을 참조하십시오.

### [!DNL Assets] {#bug-fixes-assets}의 버그 수정

* 여러 권한 관리 자산을 다운로드하려고 하면 저작권 페이지가 표시되지 않습니다. (CQ-4314403)
* INDD 파일을 편집하도록 선택하면 해상도가 예기치 않게 변경됩니다. (CQ-4317376)
* PDF 변환에는 InDesign 템플릿의 마지막 페이지만 있습니다. (CQ-4317305)
* 선택기가 복잡한 메타데이터 스키마의 일부인 경우 태그 선택기를 여는 데 시간이 오래 걸립니다. (CQ-4316426)
* 기존 파일 이름과 동일한 파일 이름으로 에셋을 업로드할 때 사용자에게 버전을 만들라는 메시지를 표시하는 이름 충돌 대화 상자가 표시되지 않습니다. (CQ-4315424)
* 폴더 메타데이터 속성은 폴더의 속성 페이지의 팝업 메뉴에서 설정하고 저장할 수 있습니다. 선택 영역이 저장소에 저장되면 폴더 메타데이터 속성을 다시 열 때 표시되지 않습니다. (CQ-4314429)
* 파일 이름에 공백 또는 특수 문자가 포함된 에셋이 브라우저를 사용하여 업로드됩니다. (CQ-4318381)

## [!DNL Cloud Service]로서의 [!DNL Adobe Experience Manager Forms] {#forms}

AEM Forms은 많은 조직에서 수년간 탁월한 온보딩 및 등록 경험을 제공할 수 있도록 도움을 주었습니다. 이러한 경험을 통해 기업은 리드를 매출로 전환하고 캡처한 고객 데이터를 처리하며 고객 프로파일을 기반으로 반응형 경험을 제공하는 등 다양한 이점을 얻을 수 있습니다. 이제 AEM Forms은 클라우드 서비스로 제공됩니다.

[AEM Forms을 Cloud Service](https://experienceleague.corp.adobe.com/docs/experience-manager-forms-cloud-service/forms/home.html)으로 사용하여 디지털 양식을 만들고, 양식을 기존 데이터 소스에 연결하고, 양식을 Adobe Sign과 통합하여 양식에 전자 서명을 추가하고, 문서 기록(DoR)을 생성하여 제출된 양식을 PDF 파일로 보관할 수 있습니다. 또한 서비스는 기존 PDF forms을 디지털 양식으로 변환할 수 있습니다. 표준 AEM Forms 기능 외에도 자동 크기 조절, 업그레이드 중단 시간 제로, 클라우드 기본 개발 환경과 같은 클라우드 기본 기능을 제공합니다. Cloud Service의 AEM Forms 기능 및 기능에 대해 알아보려면 [이 블로그 게시물](https://blog.adobe.com/en/publish/2021/03/11/experience-manager-forms-as-a-cloud-service.html)을 읽어 보십시오.

데모 또는 서비스 등록을 위해 Adobe 담당자에게 문의할 수 있습니다.

## Adobe Experience Manager 상거래를 Cloud Service {#cloud-services-commerce}

### 새로운 기능 {#what-is-new-commerce}

* Magento 2.4.2 지원

* 이제 모든 컨텐츠 페이지에서 제품 세부 사항 구성 요소를 사용하고 구성할 수 있습니다.

* 최신 CIF 코어 구성 요소 버전 v1.9.0을 포함하는 CIF Venia 참조 사이트 - 2021.03.25. 자세한 내용은 [CIF Venia 참조 사이트](https://github.com/adobe/aem-cif-guides-venia/releases/tag/venia-2021.03.25)를 참조하십시오.

* CIF 코어 구성 요소 v1.9.0 릴리스되었습니다. 자세한 내용은 [CIF 핵심 구성 요소](https://github.com/adobe/aem-core-cif-components/releases/tag/core-cif-components-reactor-1.9.0)를 참조하십시오.


## Cloud Manager {#cloud-manager}

이 섹션에서는 AEM의 Cloud Manager 릴리스 노트를 Cloud Service 2021.4.0 및 2021.3.0으로 간략하게 설명합니다.

### 릴리스 날짜 {#release-date-cm-april}

Cloud Service 2021.4.0인 AEM의 Cloud Manager에 대한 릴리스 날짜는 2021년 4월 08일입니다.
다음 릴리스는 2021년 5월 6일에 예정되어 있습니다.

### 새로운 기능 {#what-is-new-april}

* 프로그램 추가 및 편집 워크플로우에 대한 UI 업데이트를 통해 보다 직관적으로 만들 수 있습니다.

* 이제 필요한 권한을 가진 사용자는 UI를 통해 상거래 끝점을 제출할 수 있습니다.

* 이제 환경 변수의 범위가 작성자 또는 게시와 같은 특정 서비스로 지정될 수 있습니다. AEM 버전 `2021.03.5104.20210328T185548Z` 이상이 필요합니다.

* 파이프라인이 구성되지 않은 경우에도 **Git** 관리 단추가 파이프라인 카드에 표시됩니다.

* Cloud Manager에서 사용하는 AEM 프로젝트 원형 버전이 버전 27로 업데이트되었습니다.

* Cloud Manager에서 만든 Adobe I/O 개발자 콘솔의 프로젝트는 더 이상 의도치 않게 편집하거나 삭제할 수 없습니다.

* 사용자가 새 환경을 추가하면 환경을 만들면 다른 영역으로 이동할 수 없다는 메시지가 표시됩니다.

* 이제 환경 변수의 범위가 작성자 또는 게시와 같은 특정 서비스로 지정될 수 있습니다. AEM 버전 2021.03.5104.20210328T185548Z 이상이 필요합니다.

* 환경이 삭제되었을 때 파이프라인을 시작할 때의 오류 메시지가 명확해졌습니다.

* 이제 Eclipse 프로젝트에서 제공하는 OSGi 번들은 규칙 `CQBP-84--dependencies`에서 제외됩니다.

### 버그 수정 {#bug-fixes-cm-april}

* 파이프라인의 경험 감사 페이지를 편집할 때 슬래시(`( / )`)로 시작하는 입력 경로가 더 이상 보류 중인 상태로 돌아가지 않습니다.

* 새 프로덕션 파이프라인이 생성되면 사용자가 컨텐츠 감사 재정의를 추가하지 않은 경우 기본 홈 페이지가 감사되지 않았습니다.

* 다운로드 가능한 문제 CSV 파일에서 `CloudServiceIncompatibleWorkflowProcess` 문제의 심각도가 잘못되었습니다.

* `Runmode` 검사가 비폴더 노드에서 잘못된 양수를 생성하고 있었습니다.


### 릴리스 날짜 {#release-date-cm-march}

AEM에서 Cloud Service 2021.3.0으로 Cloud Manager의 릴리스 날짜는 2021년 3월 11일입니다.

### 새로운 기능 {#what-is-new-march}

* [IP 허용 목록](/help/implementing/cloud-manager/ip-allow-lists/check-ip-allow-list-status.md#pre-existing-cdn), [SSL 인증서](/help/implementing/cloud-manager/managing-ssl-certifications/check-status-ssl-certificate.md#pre-existing-cdn) 및 [사용자 정의 도메인 이름](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md#pre-existing-cdn)에 대해 기존 사용자 정의 도메인 이름 구성을 가진 환경을 사용하는 고객은 기존 구성에 대한 메시지를 볼 수 있으며 UI를 통해 직접 제공할 수 있습니다.

* 이제 필요한 권한을 가진 사용자는 셀프 서비스 방식으로 프로그램을 편집할 수 있습니다.

   * 자산을 사용하여 기존 프로그램에 사이트 솔루션을 추가하거나 그 반대로 기존 프로그램에 사이트 솔루션을 추가할 수 있습니다.
   * 사이트와 자산이 모두 포함된 기존 프로그램에서 사이트 또는 자산을 제거합니다.
   * 기존 프로그램 또는 새 프로그램으로 사용하지 않은 두 번째 솔루션 권한을 추가합니다.

* **이제** 파이프라인 실행 스크린과 Activityscreens 모두에 대해 AEM 푸시  ** Updatelable이  ** 표시됩니다.

* 환경이 최대 절전 모드이지만 사용 가능한 AEM 업데이트도 있는 경우 **최대 절전 모드** 상태가 **사용 가능한 업데이트**&#x200B;보다 우선합니다.

* 이제 사용자는 통합 셸의 사용자 프로필 아이콘(오른쪽 상단)으로 이동한 후 &#39;클라우드 관리자 역할 보기&#39; 옵션을 선택하여 클라우드 관리자 역할을 볼 수 있습니다.

* 레이블 **승인 신청**&#x200B;이(가) **프로덕션 승인**&#x200B;으로 다시 표시되었습니다.

* **버전** 레이블은 프로덕션 파이프라인 실행 화면에서 **Git 태그**&#x200B;에 다시 표시되었습니다.

* 중요한 지표가 정의된 임계값에 도달하지 못할 때 동작을 정의하는 레이블의 실제 행동을 반영하도록 레이블을 재정의했습니다.**즉시 취소** 및 **즉시 승인**.

* 클래스 및 메서드 사용 중단 목록은 AEM Cloud Service SDK의 `2021.3.4997.20210303T022849Z-210225` 버전을 기준으로 업데이트되었습니다.

* 이제 클라우드 관리자 프로덕션 파이프라인에 [사용자 지정 UI 테스트](/help/implementing/cloud-manager/functional-testing.md#custom-ui-testing) 기능이 포함됩니다.

### 버그 수정 {#bug-fixes-cm-march}

* AEM 푸시 업그레이드 중에 일부의 경우 패키지 버전 관리를 건너뛰었습니다.

* 패키지가 다른 패키지에 포함된 경우 일부 품질 문제를 제대로 찾지 못했습니다.

* 프로그램 추가 대화 상자를 열 때 생성된 기본 프로그램 이름이 기존 프로그램 이름과 중복될 수 있습니다.

* 때때로 사용자가 파이프라인을 시작한 직후 파이프라인 실행 페이지를 벗어나는 경우 작업이 실패했지만 실제로 실행이 시작된다는 오류 메시지가 표시됩니다.

* 고객 빌드로 인해 잘못된 패키지가 발생했을 때 빌드 단계가 불필요하게 다시 시작되었습니다.

* 경우에 따라 해당 구성이 배포되지 허용 목록에 추가하다 않았더라도 IP 옆에 녹색 &quot;활성&quot; 상태가 표시될 수 있습니다.

* 모든 기존 프로덕션 파이프라인은 경험 감사 단계를 통해 자동으로 활성화됩니다.

## 컨텐츠 전송 도구 {#content-transfer-tool}

### 릴리스 날짜 {#release-date-ctt}

내용 전송 도구 v1.3.4 릴리스 날짜는 2021년 3월 19일입니다.

### 버그 수정 {#bug-fixes-ctt}

* 이름이 같지만 이름에 하이픈이 있는 폴더에서 내용을 건너뛰었습니다. 이 문제가 수정되었습니다.

### 릴리스 날짜 {#release-date-ctt-march}

내용 전송 도구 v1.3.0 릴리스 날짜는 2021년 3월 4일입니다.

### 내용 전송 도구 {#what-is-new-ctt-march}의 새로운 기능

* 이제 특정 페이지에 대한 브라우저 책갈피가 더 이상 유효하지 않을 수 있는 대신 `/libs` 대신 `/apps`에 CTT가 설치됩니다.
* CTT가 설치되면 사용자는 컨텐츠 전송 페이지로 이동하려면 추가 수준을 탐색해야 합니다. 자세한 내용은 [내용 전송 도구 사용](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-content-transfer-tool.html)을 참조하십시오.

### 버그 수정 {#bug-fixes-ctt-march}

* 특정 경로에서 컨텐츠를 마이그레이션할 때 CTT는 관련 없는 리소스를 검색하고 있었습니다. 이 문제가 해결되었습니다.

## 우수 사례 분석기 {#best-practices-analyzer}

### 릴리스 날짜 {#release-date-bpa}

우수 사례 분석기 v2.1.12 릴리스 날짜는 2021년 4월 12일입니다.

### 버그 수정 {#bug-fixes-bpa-april}

* BPA에서 중복 행이 확인되었습니다. 이 문제가 수정되었습니다.
* AEM 버전 6.4.2의 BPA UI에서 [보고서 생성] 단추를 비활성화하는 JS 오류가 발생했습니다. 이 문제가 해결되었습니다.


## 코드 리팩터링 도구 {#code-refactoring-tools}

### 코드 리팩토링 도구 {#what-is-new-crt}의 새로운 기능

* Repository Modernizer의 새로운 기능 및 향상된 기능 [GitHub 리소스를 참조하십시오.저장소 현대화 프로그램](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/repository-modernizer)을(를) 최신 버전으로 사용할 수 있습니다.
   * OSGi 구성을 기본 설정 .cfg.json 형식으로 정규화합니다(RepoInit 구성 제외).
   * OSGi 구성 폴더의 이름을 지정된 형식으로 변경합니다.
   * ui.apps.structure 프로젝트를 생성합니다.
   * 분석 모듈을 만듭니다.

* Dispatcher Converter의 새로운 기능 및 개선 사항. [GitHub 리소스를 참조하십시오.Dispatcher Converter](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/dispatcher-converter)
   * 컨텐츠를 줄이지 않고 다른 포함을 위한 개별 파일 만들기
   * 호스트 파일의 폴더 경로와 호스트 파일의 경로를 모두 처리할 수 있습니다.
   * 600개 이상의 대규모 고객 구성을 갖는 팜 파일 생성
