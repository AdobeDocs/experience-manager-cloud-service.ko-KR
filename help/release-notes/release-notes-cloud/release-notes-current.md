---
title: Cloud Service으로 [!DNL Adobe Experience Manager] 에 대한 현재 릴리스 노트입니다.
description: Cloud Service으로 [!DNL Adobe Experience Manager] 에 대한 현재 릴리스 노트입니다.
translation-type: tm+mt
source-git-commit: 137be7fd0fe89429c0d1f028d81e54ce69cc4ef1
workflow-type: tm+mt
source-wordcount: '1528'
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

Cloud Service으로 [!DNL Adobe Experience Manager]에 대한 릴리스 날짜는 2021년 2월 25일입니다.
다음 릴리스(2021.3.0)은 2021년 3월 25일에 제공됩니다.

## [!DNL Adobe Experience Manager Sites] Cloud Service  {#sites}

* **[RemotePage 구성 요소](/help/implementing/developing/hybrid/remote-page.md)**:AEM 내에서 외부 SPA을 보고 편집할 수 있는 지원이 추가되었습니다.

* **[AEM에서 외부 SPA 편집](/help/implementing/developing/hybrid/editing-external-spa.md)**:독립형 단일 페이지 애플리케이션을 AEM 인스턴스에 업로드하고 편집 가능한 컨텐츠 섹션을 추가하고 작성을 활성화하는 기능을 추가했습니다.

<!--
### Progressive Web Apps (PWAs) {#pwa}

* [A Progressive Web App (PWA) version of a site](/help/sites-cloud/authoring/features/enable-pwa.md)  can now be enabled at the project level via simple configuration.
-->

## [!DNL Cloud Service]로서의 [!DNL Adobe Experience Manager Assets] {#assets}

## [!DNL Assets] {#what-is-new-assets}의 새로운 기능

* 이제 기업은 [!DNL Brand Portal]을(를) 사용하여 에셋을 소싱할 수 있습니다. 자산 소싱 기능은 [!DNL Brand Portal]을 활용하여 고객이 에이전시 사용자와 교류하여 새로운 마케팅 캠페인, 사진 및 프로젝트에 대한 소스 자산을 활용할 수 있도록 도와줍니다.  [!DNL Brand Portal]](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/asset-sourcing-in-brand-portal/brand-portal-asset-sourcing.html)에서 [자산 소싱을 참조하십시오.

* 이제 [!DNL Brand Portal] 사용량 보고서에 활성 사용자만 표시됩니다. 비활성 사용자는 지금 표시되지 않습니다. 활성 사용자는 [!DNL Admin Console]에서 제품 프로필에 계정을 할당받은 사용자입니다. [[!DNL Brand Portal] 보고서](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/admin-tools/brand-portal-reports.html)를 참조하십시오.

* [!DNL Brand Portal]에서 폴더, 컬렉션 등을 다운로드할 때 각 자산에 대해 별도의 폴더를 만들 수 있는 새로운 다운로드 설정이 도입되었습니다. [다운로드 설정](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/download/brand-portal-download-assets.html)을 참조하십시오.

<!-- TBD: refine this list of features and enh. for Feb release.

Customers using the Connected Assets feature can now easily view and track assets used on remote Sites instances. This affords customers a complete view of being used across all Sites powered pages, allowing for better tracking, management, and brand consistency.  -->

## [!DNL Assets] {#bug-fixes-assets}의 버그 수정

* 이름 지정 충돌을 해결한 후 기존 자산의 새 버전을 만들면 원래 자산의 메타데이터를 덮어씁니다. (CQ-4313594)
* 긴 주석 텍스트가 있는 에셋을 인쇄하면 공간이 있어도 주석 텍스트가 트림됩니다. (CQ-4314101)
* 속성을 업데이트하기 위해 여러 자산을 선택하면 오류가 발생하거나 선택 취소된 자산의 속성이 업데이트되는 경우가 있습니다. (CQ-4316532)
* [!UICONTROL 자산 관리자 검색 레일]을 열려고 하면 페이지가 비어 있는 상태로 남아 있고 [!UICONTROL 편집] > [!UICONTROL 설정]을 클릭하면 오류가 발생합니다. (CQ-4315079)

## Adobe Experience Manager 상거래를 Cloud Service {#cloud-services-commerce}

### 새로운 기능 {#what-is-new-commerce}

* 제품 경험 관리:경험 조각으로 제품 카탈로그 페이지를 개별적으로 보완합니다.

* 연결된 컨텐츠로 신속하게 이동하는 작업을 포함하여 연결된 자산 및 경험 조각을 표시하도록 확장된 제품 콘솔 속성입니다.

* 최신 CIF 코어 구성 요소 버전 v1.8.0을 포함하는 CIF Venia 참조 사이트 - 2021.02.24. 자세한 내용은 [CIF Venia 참조 사이트](https://github.com/adobe/aem-cif-guides-venia/releases/tag/venia-2021.02.24)를 참조하십시오.

* CIF 코어 구성 요소 v1.8.0 릴리스되었습니다. 자세한 내용은 [CIF 핵심 구성 요소](https://github.com/adobe/aem-core-cif-components/releases/tag/core-cif-components-reactor-1.8.0)를 참조하십시오.

## Cloud Manager {#cloud-manager}

이 페이지에서는 AEM의 Cloud Manager 릴리스 노트를 Cloud Service 2021.3.0으로 간략하게 설명합니다.

## 릴리스 날짜 {#release-date-cm-march}

AEM에서 Cloud Service 2021.3.0으로 Cloud Manager의 릴리스 날짜는 2021년 3월 11일입니다.


### 새로운 기능 {#what-is-new-march}

* IP 허용 목록, SSL 인증서 및 사용자 정의 도메인 이름에 대해 기존의 CDN 구성을 가진 환경을 보유한 고객은 다음 메시지를 보게 되며, UI를 통해 자가 서비스를 제공할 수 있습니다.

* 이제 필요한 권한이 있는 사용자가 셀프 서비스 방식으로 다음을 수행할 수 있도록 프로그램을 편집할 수 있습니다.

* 이제 파이프라인 실행 및 활동 화면 모두에 대해 AEM 푸시 업데이트&quot; 레이블이 표시됩니다.

* 환경이 최대 절전 모드이지만 AEM 업데이트도 사용 가능한 경우 &quot;사용 가능한 업데이트&quot;보다 &quot;최대 절전 모드&quot; 상태가 우선합니다.

* 이제 사용자는 통합 셸의 사용자 프로필 아이콘(오른쪽 상단)으로 이동한 후 &#39;클라우드 관리자 역할 보기&#39; 옵션을 선택하여 클라우드 관리자 역할을 볼 수 있습니다.

* &quot;승인 신청&quot;이라는 레이블이 &quot;생산 승인&quot;으로 대체되어 명확성을 높였습니다.

* &quot;버전&quot; 레이블이 프로덕션 파이프라인 실행 화면에서 &quot;Git 태그&quot;로 다시 설정되었습니다.

* 중요한 지표가 정의된 임계값에 맞지 않을 때 동작을 정의하는 레이블의 실제 비헤이비어(즉시 취소 및 즉시 승인)를 반영하도록 레이블이 재설정되었습니다.

* 클래스 및 메서드 사용 중단 목록은 AEM Cloud Service SDK의 `2021.3.4997.20210303T022849Z-210225` 버전을 기준으로 업데이트되었습니다.

* 이제 Cloud Manager Production 파이프라인에 사용자 정의 UI 테스트 기능이 포함됩니다.

### 버그 수정 {#bug-fixes-cm-march}

* AEM 푸시 업그레이드 중에 일부의 경우 패키지 버전 관리를 건너뛰었습니다.

* 패키지가 다른 패키지에 포함된 경우 일부 품질 문제를 제대로 찾지 못했습니다.

* 프로그램 추가 대화 상자를 열 때 생성된 기본 프로그램 이름이 기존 프로그램 이름과 중복될 수 있습니다.

* 때때로 사용자가 파이프라인을 시작한 직후 파이프라인 실행 페이지를 벗어나는 경우 작업이 실패했지만 실제로 실행이 시작된다는 오류 메시지가 표시됩니다.

* 고객 빌드로 인해 잘못된 패키지가 발생했을 때 빌드 단계가 불필요하게 다시 시작되었습니다.

* 경우에 따라 해당 구성이 배포되지 허용 목록에 추가하다 않았더라도 IP 옆에 녹색 &quot;활성&quot; 상태가 표시될 수 있습니다.

* 모든 기존 프로덕션 파이프라인은 경험 감사 단계를 통해 자동으로 활성화됩니다.


### 릴리스 날짜 {#release-date-cm}

AEM의 Cloud Service 2021.2.0 Cloud Manager에 대한 릴리스 날짜는 2021년 2월 11일입니다.

### 새로운 기능 {#what-is-new-cloud-manager}


* 이제 자산 고객은 Cloud Manager UI를 통해 셀프 서비스 방식으로 브랜드 포털 인스턴스를 배포할 시기와 위치를 선택할 수 있습니다. 자산 솔루션이 있는 일반(샌드박스 아님) 프로그램의 경우 이제 프로덕션 환경에서 브랜드 포털을 프로비저닝할 수 있습니다. 프로비저닝은 프로덕션 환경에서 한 번만 수행할 수 있습니다.

* 프로젝트 및 샌드박스 제작에서 사용되는 AEM 프로젝트 원형이 버전 25로 업데이트되었습니다.

* 코드 스캔 중에 식별된 가치 없는 API 목록은 최신 Cloud Service SDK 릴리스에서 사용되지 않는 추가 클래스 및 메서드를 포함하도록 개선되었습니다.

* Cloud Manager용 SonarQube 프로필이 Sonar 규칙 squid:S2142를 제거하도록 업데이트되었습니다. 더 이상 스레드 중단 검사와 충돌하지 않습니다.

* Cloud Manager UI는 연결된 환경에 연결된 실행 중인 파이프라인이 있거나 현재 승인 단계를 기다리는 중이므로 도메인 이름을 일시적으로 추가/업데이트할 수 없는 사용자에게 알립니다.

* 음파 탐지 접두사가 있는 고객 `pom.xml` 파일에 설정된 속성은 이제 빌드 및 품질 스캔 오류를 방지하기 위해 동적으로 제거됩니다.

* Cloud Manager UI는 현재 배포 중인 도메인 이름으로 사용 중인 경우 일시적으로 SSL 인증서를 선택할 수 없는 사용자에게 알립니다.

* Cloud Service 호환성 문제를 다루는 추가 코드 품질 규칙이 추가되었습니다.

### 버그 수정 {#bug-fixes-cloud-manager}

* 도메인 이름과 SSL 인증서를 일치시키는 것이 더 이상 대소문자를 구분하지 않습니다.

* 이제 인증서 개인 키가 적절한 오류 메시지와 함께 2048비트 제한에 도달하지 않는 경우 Cloud Manager UI는 사용자에게 알립니다.

* Cloud Manager UI는 현재 배포 중인 도메인 이름으로 사용 중인 경우 일시적으로 SSL 인증서를 선택할 수 없는 사용자에게 알립니다.

* 경우에 따라 내부 문제로 인해 환경 삭제가 중단될 수 있습니다.

* 일부 파이프라인 오류가 파이프라인 오류로 잘못 보고되었습니다.

## 컨텐츠 전송 도구 {#content-transfer-tool}

### 릴리스 날짜 {#release-date-ctt-march}

내용 전송 도구 v1.3.0 릴리스 날짜는 2021년 3월 4일입니다.

### 내용 전송 도구 {#what-is-new-ctt-march}의 새로운 기능

* 이제 특정 페이지에 대한 브라우저 책갈피가 더 이상 유효하지 않을 수 있는 대신 `/libs` 대신 `/apps`에 CTT가 설치됩니다.
* CTT가 설치되면 사용자는 컨텐츠 전송 페이지로 이동하려면 추가 수준을 탐색해야 합니다. 자세한 내용은 [내용 전송 도구 사용](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-content-transfer-tool.html)을 참조하십시오.

### 버그 수정 {#bug-fixes-ctt-march}

* 특정 경로에서 컨텐츠를 마이그레이션할 때 CTT는 관련 없는 리소스를 검색하고 있었습니다. 이 문제가 해결되었습니다.


### 릴리스 날짜 {#release-date-ctt}

내용 전송 도구 v1.2.4 릴리스 날짜는 2021년 2월 10일입니다.

### 버그 수정 {#bug-fixes-ctt}

* 여러 사용자를 매핑할 때 일부 사용자의 IMS ID가 잘못 매핑되었습니다. 이 문제가 수정되었습니다.

### 릴리스 날짜 {#release-date-ctt-feb}

내용 전송 도구 v1.2.2 릴리스 날짜는 2021년 2월 1일입니다.

### 내용 전송 도구 {#what-is-new-ctt}의 새로운 기능

* 컨텐츠 전송 도구 - 사용자 매핑 도구에 추가된 새 기능 및 UI. 이 기능은 컨텐츠 마이그레이션 작업의 일부로 기존 사용자 및 그룹을 Adobe Identity Management 시스템 ID에 자동으로 매핑합니다.
자세한 내용은 [사용자 매핑 도구 사용](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-user-mapping-tool.html)을 참조하십시오.
* 이제 콘텐츠 전송 도구가 하위 항목을 포함하여 마이그레이션 세트에서 참조하는 모든 그룹 및 사용자를 마이그레이션합니다.
* 사용자는 마이그레이션 세트를 만들 때 `/etc` 아래에서 특정 경로를 선택할 수 있습니다.

## 우수 사례 분석기 {#best-practices-analyzer}

### 릴리스 날짜 {#release-date-bpa}

우수 사례 분석기 v2.1.2 릴리스 날짜는 2021년 2월 18일입니다.

### 우수 사례 분석기 {#what-is-new-bpa}의 새로운 기능

* AEM Forms 및 AEM Forms 구현 기능을 감지하고 Cloud Service으로 AEM Forms으로 마이그레이션하는 것과 관련된 영역을 나타낼 수 있습니다.
* 사용자 지정 구성 요소 및 템플릿의 사용 및 카운트를 감지하고 보고할 수 있습니다.
* 사용된 노드 저장소 및 데이터 저장소 유형을 검색하는 기능입니다.
* Dynamic Media 사용 감지 기능
* 사용된 Java 버전을 검색하는 기능

## 코드 리팩터링 도구 {#code-refactoring-tools}

### 코드 리팩토링 도구 {#what-is-new-crt}의 새로운 기능

* 새로운 버전의 AIO-CLI 플러그인이 출시되었습니다. 이 플러그인의 최신 버전에는 Repository Modernizer에 대한 몇 가지 버그 수정이 포함되어 있습니다.
이 플러그인에 대한 자세한 내용은 [통합 경험](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/refactoring-tools/unified-experience.html?lang=en#benefits)을 참조하십시오.

### 버그 수정 {#bug-fixes-crt}

* Repository Modernizer에서 수행한 몇 가지 버그 수정.
[GitHub 리소스를 참조하십시오.자세한 내용은 aem-cloud-service-source-migration](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/repository-modernizer)을 참조하십시오.








