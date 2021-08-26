---
title: Cloud Service [!DNL Adobe Experience Manager] 의 현재 릴리스 노트입니다.
description: Cloud Service [!DNL Adobe Experience Manager] 의 현재 릴리스 노트입니다.
exl-id: a2d56721-502c-4f4e-9b72-5ca790df75c5
mini-toc-levels: 1
source-git-commit: 03151f72a86e708a0a91c141d5901a9fb7a311a5
workflow-type: tm+mt
source-wordcount: '1192'
ht-degree: 2%

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

[!DNL Cloud Service] 현재 릴리스(2021.8.0)로서 [!DNL Adobe Experience Manager]의 출시일은 2021년 8월 26일입니다.
다음 릴리스(2021.9.0)는 2021년 9월 30일입니다.

## 릴리스 비디오 {#release-video}

추가된 기능의 요약에 대해 [2021년 8월 릴리스 개요](https://video.tv.adobe.com/v/336277) 비디오를 보십시오.

## [!DNL Cloud Service]로서의 [!DNL Experience Manager Assets] {#assets}

### [!DNL Assets]의 새로운 기능 {#assets-features}

* 디지털 자산을 링크로 공유할 때 사용자는 바로 URL을 클립보드에 복사할 수 있습니다. 개선 사항을 통해 자산을 보다 빠르고 편리하게 공유할 수 있습니다. 이 기능을 사용하면 자산 공유를 빠르고 편리하게 할 수 있습니다.

   ![자산을 링크로 공유할 때 URL 복사 옵션](/help/assets/assets/link-share-copy-URL-option.png)
   *그림: 이제 링크로 자산을 공유할 때 URL을 복사하여 별도로 공유할 수 있습니다.*

* TXT 파일을 업로드하면 자산 마이크로서비스가 자동으로 축소판을 생성합니다. PNG 축소판은 사용자가 파일을 열지 않고 일정하게 내용이나 파일을 식별하는 데 도움이 되는 TXT 파일의 표현입니다. 이 기능은 구성이 필요하지 않으며 기본적으로 작동합니다.

   ![TXT 파일의 표현물은 PNG 형식 [!DNL Assets] 으로 자동으로 생성됩니다](/help/assets/assets/thumbnail-rendition-txt-file.png)
   *그림: TXT 파일의 표현물이 자동으로 생성되어 파일을 열지 않고 식별할 수 있습니다.*

### [!DNL Assets] 사전 릴리스 채널의 새 기능 {#assets-prerelease-features}

* 이제 사용자는 열 및 카드 보기에서 검색 결과에 표시된 자산을 정렬할 수 있습니다. 정렬은 이름, 작성, 수정 또는 없음 열에서 작동합니다.

   ![열 및 카드 보기 [!DNL Assets] 에서 검색 결과를 정렬합니다.](/help/assets/assets/sort-searched-assets.png)
   *그림: 열 및 카드 보기 [!DNL Assets] 에서 검색 결과를 정렬합니다.*

### [!DNL Assets]에 수정된 버그 {#assets-bugs-fixed}

* 기여자 그룹의 구성원이 [!DNL Assets] 콘솔로 이동하면 추가 `POST` 요청이 생성되어 컬렉션을 만듭니다. 이 요청은 필요하지 않으며, 권한 문제로 인해 실패하며, 로그에 많은 오류가 발생합니다. (CQ-4328856)
* 사용자가 자산을 보고 왼쪽 패널의 팝업 메뉴에서 [!UICONTROL 타임라인]을 선택하면 오류가 표시됩니다. 로그에서 잘못된 쿼리로 인해 많은 경고가 기록됩니다. (CQ-4328919)

## [!DNL Cloud Service]로서의 [!DNL Experience Manager Forms] {#forms}

### [!DNL Forms]의 새로운 기능 {#what-is-new-forms}

<!-- * Automated Forms Conversion service can [convert PDF Forms in Italian and Portuguese language](https://experienceleague.adobe.com/docs/aem-forms-automated-conversion-service/using/extending-the-default-meta-model.html?#language-specific-meta-model) to Adaptive Forms. -->

* 이제 Microsoft Dynamics 및 Salesforce.com용 AEM Archetype 프로젝트 as a Cloud Service에 [4개의 새로운 테마 및 양식 데이터 모델이 포함됩니다](https://experienceleague.adobe.com/docs/experience-manager-forms-cloud-service/forms/setup-environment/setup-local-development-environment.html?#forms-cloud-service-local-development-environment).

* **Acrobat 기반 레코드 문서**: AEM Forms as a Cloud Service은 XFA 기반 양식 템플릿 외에  [Adobe Acrobat 양식 PDF(Acrobat PDF)](https://experienceleague.adobe.com/docs/experience-manager-forms-cloud-service/forms/create-an-adaptive-form/generate-document-of-record-for-non-xfa-based-adaptive-forms.html) 를 기록 문서 템플릿으로 사용할 수 있도록 지원합니다.

* **Microsoft Azure 데이터 저장소 커넥터**: 이제 양식 데이터 모델을  [Microsoft Azure 저장소에 연결할 수 있습니다](https://experienceleague.adobe.com/docs/experience-manager-forms-cloud-service/forms/use-form-data-model/configure-azure-storage.html). 적응형 양식 데이터를 검색하고 BLOB으로 Microsoft Azure 저장소에 저장할 수 있습니다.

### [!DNL Forms] 베타 기능 {#aug-what-is-new-forms-prerelease}

* **통합 스토리지 커넥터:** 통합 스토리지 커넥터를 사용하면 AEM Forms Cloud Service 스토리지에서 데이터를 지속하지 않고 데이터 소스를 AEM 워크플로우 또는 적응형 양식에 연결할 수 있습니다. PII(개인 식별 정보)를 안전하게 처리하고 정보를 Azure 데이터 저장소에 직접 저장할 수 있습니다.

* **[!DNL AEM Forms as a Cloud Service - Communications]**:  [Communication ](https://experienceleague.adobe.com/docs/experience-manager-forms-cloud-service/forms/aem-forms-cloud-service-communications.html) APIshelp에서는 XDP 템플릿과 XML 데이터를 결합하여 다양한 형식으로 인쇄 문서를 생성합니다. 이 서비스를 통해 동기 모드로 문서를 생성할 수 있습니다. API를 사용하면 다음을 수행할 수 있는 애플리케이션을 만들 수 있습니다.
   * XML 데이터로 템플릿 파일을 채워서 문서를 생성합니다.
   * 비대화형 PDF 인쇄 스트림을 포함하여 다양한 형식으로 출력 양식을 생성합니다.
   * XFA 양식 PDF 및 Adobe Acrobat 양식에서 인쇄 PDF 파일을 생성합니다.

[!DNL formscsbeta@adobe.com]에 작성하여 베타 프로그램에 등록할 수 있습니다.

### [!DNL Forms] 사전 릴리스 채널에서 사용할 수 있는 새로운 기능 {#prerelease-features-forms}

* **적응형 양식에서 Adobe Sign 역할 사용**: 비즈니스 및 엔터프라이즈 서비스 수준용 Adobe Sign은 서명자 외에 계약 수신자의 역할을 확장하여 워크플로우 요구 사항에 보다 잘 부합할 수 있는 옵션을 제공합니다. 이제 [계약의 각 수신자가 적응형 양식](https://experienceleague.adobe.com/docs/experience-manager-forms-cloud-service/forms/create-an-adaptive-form/use-adobe-sign/working-with-adobe-sign.html?#addsignerstoanadaptiveform)에서 자신의 역할을 구성할 수 있도록 설정할 수 있으며, 서명자가 기본 역할입니다.

* **응용 Forms용 Analytics**: 이제 Adobe Analytics for Adaptive Forms을 통해 최종 사용자 행동을 캡처하고 추적하여 최종 사용자 통찰력을 수집할 수 있습니다. 최종 사용자 경험을 향상시키기 위해 데이터를 기반으로 현명한 결정을 내릴 수 있습니다.

* **AEM Forms과 Microsoft Dynamics 및 Salesforce.com을 손쉽게 연결**: 이 서비스는 Microsoft Dynamics 및 Salesforce.com용 기본 데이터 소스 구성 및 데이터 모델을 제공하므로 개발자가 Microsoft Dynamics 및 Salesforce.com을 적응형 양식의 데이터 소스로  [빠르고 쉽게 구성할 수 있습니다](https://experienceleague.adobe.com/docs/experience-manager-forms-cloud-service/forms/use-form-data-model/configure-msdynamics-salesforce.html).

## CIF 추가 기능 {#cloud-services-cif}

### 새로운 기능 {#what-is-new-cif}

* 향상된 사용자 환경, 향상된 효율성 및 복잡한 제품 카탈로그에 대한 향상된 지원을 제공하는 새로운 카테고리 선택기 UI

   ![새 카테고리 선택기](/help/assets/CIF/category-picker.png)

* CIF A11Y 구성 요소에 대한 지원 개선

## Cloud Manager {#cloud-manager}

이 섹션에서는 AEM as a Cloud Service 2021.8.0 및 2021.7.0 의 Cloud Manager 릴리스 노트를 간략하게 설명합니다.

## 릴리스 날짜 {#release-date-cm-aug}

AEM as a Cloud Service 2021.8.0의 Cloud Manager 릴리스 날짜는 2021년 8월 12일입니다.
다음 릴리스는 2021년 9월 9일에 예정되어 있습니다.

### 새로운 기능 {#what-is-new-aug}

* 이제 Cloud Service 고객은 Cloud Manager에서 SLA(서비스 수준 계약) 보고서를 볼 수 있습니다. 이 기능은 다음 몇 달 동안 점진적으로 제공될 예정입니다.
자세한 내용은 [SLA 보고](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/sla-reporting.html)를 참조하십시오.

* IndexType 및 `IndexDamAssetLucene` 품질 규칙의 유형과 심각도가 변경되었습니다. 이제 Blocker *serverity*&#x200B;의 버그가 둘 다 있습니다.

* 비동기 및 tika 구성을 다루는 새로운 Oak 색인 품질 규칙이 도입되었습니다.

* 프로그램당 최대 SSL 인증서를 50개로 늘립니다.

* 사용자가 Cloud Manager UI를 통해 여러 저장소를 만들고 관리할 수 있는 셀프 서비스 기능입니다.

* SonarQube가 불필요하게 Git 내역 데이터를 읽고 있었습니다. 큰 코드 베이스에서 이로 인해 불필요한 빌드 성능 벌금이 발생할 수 있습니다.

* 이제 파이프라인당 Maven 종속성 캐시를 무효화하는 데 사용할 수 있는 API가 있습니다.

* Cloud Manager에서 사용하는 AEM 프로젝트 원형 버전이 버전 29로 업데이트되었습니다.

### 버그 수정 {#bug-fixes-aug}

* 최신 릴리스가 현재 릴리스보다 작을 경우 사용 가능한 업데이트 상태가 표시되지 않아야 합니다.

* 매우 긴 이름을 가진 새로운 조직에 대해 초기 온보딩이 실패했습니다.

* 경우에 따라 파이프라인이 두 번 트리거되면 *이(가) 파이프라인 실행 상태* 오류로 인해 실행 중 하나가 실패하는 경우가 있습니다.

## 컨텐츠 전송 도구 {#content-transfer-tool}

### 릴리스 날짜 {#release-date-ctt-latest}

컨텐츠 전송 도구 v1.5.6의 릴리스 날짜는 2021년 8월 11일입니다.

### 버그 수정 {#bug-fixes-ctt}

* 일부 경우에는 일부 사용자가 target 인스턴스로 마이그레이션되지 않았습니다. 이 수정 사항을 가져오려면 Cloud Service 인스턴스로 target AEM의 aem-etos-tools 1.2.354 이상 버전과 함께 CTT v1.5.6이 필요합니다.

* 게시 인스턴스에 수집하는 동안 **수집 중지** 단추가 비활성화되었습니다. 게시 수집 중에 단일 복원 단계가 없으므로 이 작업은 필요하지 않습니다.

* 성공적으로 추출한 후 CTT에서 `/tmp` 디렉터리를 정리하지 못했습니다. 이로 인해 디스크 공간 문제가 발생하는 경우가 있습니다.

