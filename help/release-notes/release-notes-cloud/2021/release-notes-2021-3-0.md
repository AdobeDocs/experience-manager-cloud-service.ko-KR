---
title: ' [!DNL Adobe Experience Manager] as a Cloud Service의 2021.3.0 릴리스 정보입니다.'
description: "[!DNL Adobe Experience Manager] 2021.3.0용 as a Cloud Service 릴리스 노트"
exl-id: 0c07364c-ba25-4081-8e35-3c1c84ed556f
source-git-commit: f6162dcbc5b7937d55922e8c963a402697110329
workflow-type: tm+mt
source-wordcount: '1271'
ht-degree: 33%

---

# [!DNL Adobe Experience Manager] as a Cloud Service 최신 릴리스 정보 {#release-notes}

다음 섹션에서는 [!DNL Experience Manager] as a Cloud Service의 최신 버전 일반 릴리스 정보에 대해 간략히 소개합니다.

>[!NOTE]
>여기에서 2020, 2021 버전 등 이전 버전의 릴리스 정보로 이동할 수 있습니다.

>[!NOTE]
>
>릴리스와 직접적으로 관련되지 않는 설명서 업데이트의 세부 정보는 [최신 설명서 업데이트](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html)를 참조하십시오.

## 릴리스 일자 {#release-date}

의 릴리스 날짜 [!DNL Adobe Experience Manager] as a Cloud Service 2021.3.0은 2021년 3월 25일입니다.
다음 릴리스(2021.4.0) 날짜는 2021년 4월 29일입니다.

## [!DNL Adobe Experience Manager Sites] as a Cloud Service {#sites}

* [사이트의 점진적 웹 앱(PWA) 버전](/help/sites-cloud/authoring/sites-console/enable-pwa.md) 이제 간단한 구성을 통해 프로젝트 수준에서 을(를) 활성화할 수 있습니다.
* 콘텐츠 조각 모델 확장 - 이제 여러 줄 텍스트 데이터 유형을 다중 필드 목록으로 정의할 수 있습니다.
* 콘텐츠 조각 편집기 UX 개선 사항 - 중첩된 하위 조각이 이제 이동 경로에 표시되며 게시, 저장 및 저장 종료 작업에 대한 보기가 개선되었습니다.

## [!DNL Adobe Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### [!DNL Assets]의 새로운 기능 {#what-is-new-assets}

<!-- TBD: refine this list of features and enh. for Feb release.

Customers using the Connected Assets feature can now easily view and track assets used on remote Sites instances. This affords customers a complete view of being used across all Sites powered pages, allowing for better tracking, management, and brand consistency.  

Indicators for expired, approved, and rejected statuses now available for assets in Column view.

Ability to select a root path. select if a minimum number of tags is required. 

Add a Boolean or radio widget type to metadata schema setup. -->

* [!DNL Experience Manager] 연결된 자산 기능을 확장하여 사용 지원 [!DNL Dynamic Media] 지원되는 핵심 구성 요소의 이미지 다음을 참조하십시오 [연결된 자산 사용](/help/assets/use-assets-across-connected-assets-instances.md).
* Experience Manager 관리자는 특정 날짜 또는 시간에 일괄 에셋 수집을 예약할 수 있습니다. 또한 관리자는 날짜와 시간에 따라 반복 수집을 예약할 수 있습니다. 다음을 참조하십시오 [일괄 에셋 수집](/help/assets/add-assets.md#asset-bulk-ingestor).

### [!DNL Assets]에서 수정된 버그 {#bug-fixes-assets}

* 여러 권한 관리 에셋을 다운로드하려고 하면 저작권 페이지가 표시되지 않습니다. (CQ-4314403)
* INDD 파일을 편집하도록 선택할 때 해상도가 예기치 않게 변경됩니다. (CQ-4317376)
* PDF 렌디션에는 InDesign 템플릿의 마지막 페이지만 있습니다. (CQ-4317305)
* 선택기가 복잡한 메타데이터 스키마의 일부인 경우 태그 선택기를 여는 데 시간이 오래 걸립니다. (CQ-4316426)
* 기존 에셋과 동일한 파일 이름으로 에셋을 업로드할 때 이름 충돌 대화 상자가 표시되지 않아서 사용자에게 버전을 생성하라는 메시지가 표시됩니다. (CQ-4315424)
* 폴더의 속성 페이지에 있는 팝업 메뉴에서 폴더 메타데이터 속성을 설정하고 저장할 수 있습니다. 선택 항목이 저장소에 저장되는 동안 폴더 메타데이터 등록 정보를 다시 열면 선택 항목이 표시되지 않습니다. (CQ-4314429)
* 파일 이름에 공백이나 특수 문자가 포함된 에셋은 브라우저를 사용하여 업로드됩니다. (CQ-4318381)

## [!DNL Adobe Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

AEM Forms은 수년 동안 훌륭한 온보딩 및 등록 경험을 제공할 수 있도록 많은 기업들에게 도움을 주었습니다. 이러한 경험은 기업이 잠재 고객을 판매로 전환하고, 캡처된 고객 데이터를 처리하고, 대상 그룹 프로필을 기반으로 반응형 경험을 제공하는 데 도움이 되었습니다. 이제 AEM Forms을 클라우드 서비스로 사용할 수 있습니다.

다음을 사용할 수 있습니다. [AEM Forms as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-forms-cloud-service/forms/home.html) 디지털 양식을 만들려면 양식을 기존 데이터 소스에 연결하고 양식을 Adobe Sign과 통합하여 양식에 전자 서명을 추가하고 DoR(문서 기록)을 생성하여 제출된 양식을 PDF 파일로 보관합니다. 이 서비스는 기존 PDF forms을 디지털 양식으로 변환할 수도 있습니다. 표준 AEM Forms 기능 외에도 이 서비스는 자동 확장, 무중단 업그레이드, 클라우드 기반 개발 환경과 같은 여러 클라우드 기반 기능을 제공합니다.

Adobe 담당자에게 문의하여 데모를 받거나 서비스에 등록할 수 있습니다.

## Adobe Experience Manager Commerce as a Cloud Service {#cloud-services-commerce}

### 새로운 기능 {#what-is-new-commerce}

* Adobe Commerce 2.4.2 지원

* 이제 제품 세부 사항 구성 요소를 모든 콘텐츠 페이지에서 사용하고 구성할 수 있습니다

* 최신 CIF 핵심 구성 요소 버전 v1.9.0이 포함된 CIF Venia 참조 사이트 - 2021.03.25가 릴리스되었습니다. 다음을 참조하십시오 [CIF Venia 참조 사이트](https://github.com/adobe/aem-cif-guides-venia/releases/tag/venia-2021.03.25) 을 참조하십시오.

* CIF 코어 구성 요소 v1.9.0이 릴리스되었습니다. 다음을 참조하십시오 [CIF 핵심 구성 요소](https://github.com/adobe/aem-core-cif-components/releases/tag/core-cif-components-reactor-1.9.0) 을 참조하십시오.


## Cloud Manager {#cloud-manager}

이 섹션에서는 AEM as a Cloud Service 2021.3.0의 Cloud Manager 릴리스 정보에 대해 간략히 소개합니다.

## 릴리스 일자 {#release-date-cm-march}

AEM as a Cloud Service 2021.3.0의 Cloud Manager 릴리스 일자는 2021년 3월 11일입니다.
다음 릴리스는 2021년 4월 8일 금요일에 예정되어 있습니다.

### 새로운 기능 {#what-is-new-march}

* 에 대한 기존 사용자 정의 도메인 이름 구성이 있는 환경을 가진 고객 [IP 허용 목록](/help/implementing/cloud-manager/ip-allow-lists/managing-ip-allow-lists.md#pre-existing-cdn), [SSL 인증서](/help/implementing/cloud-manager/managing-ssl-certifications/managing-certificates.md#pre-existing-cdn) 및 [사용자 정의 도메인 이름](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md#pre-existing-cdn) 이전의 기존 구성에 대한 메시지를 확인하고 사용자 인터페이스를 통해 셀프서비스를 수행할 수 있습니다.

* 이제 필수 권한이 있는 사용자는 프로그램을 편집하여 셀프서비스 방식으로 다음과 같은 작업을 수행할 수 있습니다.

   * Assets가 있는 기존 프로그램에 Sites 솔루션을 추가하거나, 그 반대도 마찬가지입니다.
   * Sites와 Assets가 모두 있는 기존 프로그램에서 Sites 또는 Assets를 제거할 수 있습니다.
   * 두 번째 미사용 솔루션 권한을 기존 프로그램에 추가하거나 새 프로그램으로 추가합니다.

* **AEM 푸시 업데이트** 이제 레이블이 두 항목 모두에 대해 표시됩니다. *파이프라인 실행* 및 *활동* screens.

* 환경이 최대 절전 모드이지만 사용 가능한 AEM 업데이트도 있는 경우 **최대 절전 모드** 상태가 **사용 가능한 업데이트**&#x200B;보다 우선합니다.

* 이제 사용자는 통합 셸의 사용자 프로필 아이콘(오른쪽 위)으로 이동한 후 Cloud Manager 역할 보기 옵션을 선택하여 사용자 자신의 Cloud Manager 역할을 볼 수 있습니다.

* 보다 명확하게 하기 위해 **승인 신청** 레이블이 **생산 승인**&#x200B;로 다시 라벨링되었습니다.

* 프로덕션 파이프라인 실행 화면에서 **버전** 레이블이 **Git Tag**&#x200B;로 다시 라벨링되었습니다.

* 중요 지표가 정의된 임계값에 부합하지 않을 때 동작을 정의하는 레이블은 실제 동작을 반영하도록 다시 라벨링되었습니다. **즉시 취소** 및 **즉시 승인**.

* 클래스 및 메서드 사용 중단 목록은 `2021.3.4997.20210303T022849Z-210225` 버전 AEM Cloud Service SDK를 기반으로 업데이트되었습니다.

* Cloud Manager 프로덕션 파이프라인에는 이제 [사용자 정의 UI 테스트](/help/implementing/cloud-manager/functional-testing.md#custom-ui-testing) 기능이 포함됩니다.

### 버그 수정 {#bug-fixes-cm-march}

* AEM 푸시 업그레이드 중에 패키지 버전을 건너뛰는 경우가 있었습니다.

* 패키지가 다른 패키지에 임베드된 경우 일부 품질 문제가 제대로 검색되지 않았습니다.

* 불명확한 상황에서 프로그램 추가 대화 상자를 열 때 생성되는 기본 프로그램 이름이 기존 프로그램 이름과 중복될 수 있었습니다.

* 사용자가 파이프라인을 시작한 직후 파이프라인 실행 페이지에서 벗어나면 실행이 실제로 시작되지만 작업이 실패했다는 오류 메시지가 표시되는 경우가 있었습니다.

* 고객 빌드로 인해 잘못된 패키지가 발생한 경우 빌드 단계가 불필요하게 다시 시작되었습니다.

* 해당 구성이 배포되지 않은 경우에도 IP 허용 목록 옆에 녹색 “활성” 상태가 표시되는 경우가 있었습니다.

* 기존의 모든 프로덕션 파이프라인은 경험 감사 단계에서 자동으로 활성화됩니다.

## 콘텐츠 전송 도구 {#content-transfer-tool}

### 릴리스 날짜 {#release-date-ctt}

컨텐츠 전송 도구 v1.3.4의 릴리스 날짜는 2021년 3월 19일입니다.

### 버그 수정 {#bug-fixes-ctt}

* CTT는 이름은 같지만 이름에 하이픈이 있는 폴더에서 콘텐츠를 건너뜁니다. 이 문제가 해결되었습니다.

### 릴리스 일자 {#release-date-ctt-march}

컨텐츠 전송 도구 v1.3.0의 릴리스 날짜는 2021년 3월 4일입니다.

### 컨텐츠 전송 도구의 새로운 기능 {#what-is-new-ctt-march}

* CTT는 이제 `/apps` 대신 `/libs` 특정 페이지에 대한 브라우저 책갈피가 더 이상 유효하지 않을 수 있습니다.
* CTT가 설치되면 사용자는 추가 수준을 탐색하여 콘텐츠 전송 페이지로 이동해야 합니다. 다음을 참조하십시오 [컨텐츠 전송 도구 사용](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-content-transfer-tool.html) 을 참조하십시오.

### 버그 수정 {#bug-fixes-ctt-march}

* 특정 경로에서 콘텐츠를 마이그레이션할 때 CTT가 관련 없는 리소스를 가져왔습니다. 이 문제가 해결되었습니다

## Best Practices Analyzer {#best-practices-analyzer}

### 릴리스 날짜 {#release-date-bpa}

Best Practices Analyzer v2.1.8의 릴리스 날짜는 2021년 3월 22일입니다.

### Best Practices Analyzer 의 새로운 기능 {#what-is-new-bpa}

* 사용자 인터페이스의 BPA 보고서 및 CSV 파일로 내보낸 보고서에서 ACS Commons 결과를 필터링하는 기능.

## 코드 리팩터링 도구 {#code-refactoring-tools}

### 코드 리팩터링 도구의 새로운 기능 {#what-is-new-crt}

* Repository Modernizer의 새로운 기능 및 향상된 기능. 다음을 참조하십시오 [GitHub 리소스: Repository Modernizer](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/repository-modernizer) 최신 버전용입니다.
   * OSGi 구성(RepoInit 구성 제외)을 기본 .cfg.json 형식으로 정규화합니다.
   * OSGi 구성 폴더의 이름을 지정된 형식으로 변경합니다.
   * ui.apps.structure 프로젝트를 생성합니다.
   * 분석 모듈을 만듭니다.

* Dispatcher Converter의 새로운 기능 및 개선 사항. 다음을 참조하십시오 [GitHub 리소스: Dispatcher 변환기](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/dispatcher-converter)
   * 콘텐츠 라이닝 대신 다른 포함에 대해 별도의 파일 생성.
   * vhost의 폴더 경로와 vhost 파일의 경로를 모두 처리하는 기능.
   * 600개 이상 범위의 대규모 고객 구성이 있는 팜 파일 생성.
