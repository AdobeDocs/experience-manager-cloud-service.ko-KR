---
title: ' [!DNL Adobe Experience Manager] as a Cloud Service의 2021.8.0 릴리스 정보입니다.'
description: ' [!DNL Adobe Experience Manager] as a Cloud Service의 2021.8.0 릴리스 정보입니다.'
exl-id: 8b041934-1c4a-4670-9b03-d38f683b99e5
source-git-commit: 5ad33f0173afd68d8868b088ff5e20fc9f58ad5a
workflow-type: tm+mt
source-wordcount: '1027'
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

[!DNL Adobe Experience Manager] as a [!DNL Cloud Service]의 현재 릴리스(2021.8.0) 날짜는 2021년 26월 8일입니다.
다음 릴리스(2021.9.0) 날짜는 2021년 10월 6일입니다.

## 릴리스 비디오 {#release-video}

다음을 살펴보십시오. [2021년 8월 릴리스 개요](https://video.tv.adobe.com/v/336277) 추가된 기능에 대한 요약을 보려면 비디오 를 사용하십시오.

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### [!DNL Assets]의 새로운 기능 {#assets-features}

* 디지털 에셋을 링크로 공유할 때 사용자는 URL을 클립보드에 바로 복사할 수 있습니다. 향상된 기능을 통해 에셋을 보다 빠르고 편리한 방법으로 공유할 수 있습니다. 이 기능을 사용하면 에셋을 보다 빠르고 편리하게 공유할 수 있습니다.

  ![자산을 링크로 공유할 때 URL 복사 옵션](/help/assets/assets/link-share-copy-URL-option.png)
  *그림: 자산을 링크로 공유할 때 이제 URL을 복사하여 별도로 공유할 수 있습니다.*

* TXT 파일을 업로드할 때 에셋 마이크로서비스가 자동으로 썸네일을 생성합니다. PNG 썸네일은 사용자가 파일을 열지 않고도 내용이나 파일을 어느 정도 식별할 수 있도록 도와주는 TXT 파일의 렌디션입니다. 이 기능은 구성이 필요하지 않으며 기본적으로 작동합니다.

  ![TXT 파일의 렌디션은 [!DNL Assets] PNG 형식](/help/assets/assets/thumbnail-rendition-txt-file.png)
  *그림: TXT 파일의 렌디션은 파일을 열지 않고도 식별하는 데 도움이 되도록 자동으로 생성됩니다.*

### 의 새로운 기능 [!DNL Assets] 프리릴리스 채널 {#assets-prerelease-features}

* 이제 열 및 카드 보기에서 검색 결과에 표시된 에셋을 정렬할 수 있습니다. 정렬은 이름, 생성됨, 수정됨 또는 없음 열에서 작동합니다.

  ![검색 결과 정렬 [!DNL Assets] 열 및 카드 보기에서](/help/assets/assets/sort-searched-assets.png)
  *그림: 검색 결과 정렬 [!DNL Assets] 열 및 카드 보기에서 다음을 수행합니다.*

### [!DNL Assets]의 수정된 버그 {#assets-bugs-fixed}

* 기여자 그룹의 구성원이 로 이동할 때 [!DNL Assets] 콘솔, 추가 `POST` 컬렉션을 만들기 위한 요청이 생성됩니다. 이 요청은 필수가 아닙니다. 권한 문제로 인해 실패하고 로그에 많은 오류가 생성됩니다. (CQ-4328856)
* 사용자가 에셋을 보고 선택할 때 [!UICONTROL 타임라인] 왼쪽 패널의 팝업 메뉴에서 오류가 표시됩니다. 잘못된 쿼리로 인해 로그에 많은 경고가 기록됩니다. (CQ-4328919)

## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

### [!DNL Forms]의 새로운 기능 {#what-is-new-forms}

* Automated forms conversion 서비스는 다음을 수행할 수 있습니다. [이탈리아어 및 포르투갈어로 PDF forms 변환](https://experienceleague.adobe.com/docs/aem-forms-automated-conversion-service/using/extending-the-default-meta-model.html?#language-specific-meta-model) 를 적응형 Forms에 추가합니다.

* **Acroform 기반 기록 문서**: AEM Forms as a Cloud Service는 XFA 기반 양식 템플릿 외에 기록 문서용 템플릿으로도 [Adobe Acrobat Form PDF(Acroform PDF)](https://experienceleague.adobe.com/docs/experience-manager-forms-cloud-service/forms/create-an-adaptive-form/generate-document-of-record-for-non-xfa-based-adaptive-forms.html)을 사용할 수 있도록 지원합니다.

* **Microsoft Azure 데이터 스토어 커넥터**: 이제 [양식 데이터 모델을 Microsoft Azure Storage에 연결](https://experienceleague.adobe.com/docs/experience-manager-forms-cloud-service/forms/use-form-data-model/configure-azure-storage.html)할 수 있습니다. 적응형 양식 데이터를 검색하여 Microsoft Azure Storage에 BLOB로 저장할 수 있습니다.

### [!DNL Forms] 프리릴리스 채널에서 사용할 수 있는 새로운 기능 {#prerelease-features-forms}

* **적응형 양식에서 Adobe Sign 역할 사용**: 비즈니스 및 엔터프라이즈 서비스 수준을 위한 Adobe Sign은 계약 수신자의 역할을 서명자 이상으로 확장하는 옵션을 제공하여 워크플로 요구 사항에 보다 잘 부합하도록 합니다. 이제 계약의 각 수신자가 적응형 양식에서 자신의 역할을 구성할 수 있으며, 서명자는 기본 역할입니다.

* **적응형 양식용 Analytics**: 이제 적응형 양식용 Adobe Analytics를 통해 최종 사용자 행동을 포착하고 추적하여 최종 사용자 인사이트를 수집할 수 있습니다. 이로써 데이터를 기반으로 정보에 입각한 결정을 내려 최종 사용자 경험을 개선할 수 있습니다.

* **AEM Forms을 Microsoft Dynamics 및 Salesforce.com에 쉽게 연결**: 이 서비스는 Microsoft Dynamics 및 Salesforce.com에 즉시 사용 가능한 데이터 소스 구성 및 데이터 모델을 제공하여 개발자가 Microsoft Dynamics 및 Salesforce.com을 적응형 양식의 데이터 소스로 더 빠르고 쉽게 구성할 수 있도록 해 줍니다.

## CIF 추가 기능 {#cloud-services-cif}

### 새로운 기능 {#what-is-new-cif}

* 향상된 사용자 경험, 향상된 효율성 및 복잡한 제품 카탈로그에 대한 더 나은 지원을 위한 새로운 카테고리 선택기 UI

  ![새 범주 선택기](/help/assets/CIF/category-picker.png)

* CIF 핵심 구성 요소에 대한 A11Y 지원 개선

## Cloud Manager {#cloud-manager}

이 섹션에서는 AEM as a Cloud Service 2021.8.0 및 2021.7.0의 Cloud Manager 릴리스 정보에 대해 간략히 설명합니다.

## 릴리스 일자 {#release-date-cm-aug}

AEM as a Cloud Service 2021.8.0의 Cloud Manager 릴리스 일자는 2021년 8월 12일입니다.
다음 릴리스는 2021년 9월 9일에 예정되어 있습니다.

### 새로운 기능 {#what-is-new-aug}

* Cloud Service 고객은 이제 Cloud Manager에서 SLA(서비스 수준 계약) 보고서를 볼 수 있습니다. 이 기능은 앞으로 몇 달에 걸쳐 점진적으로 제공될 예정입니다.
자세한 내용은 [SLA 보고](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/sla-reporting.html)를 참조하십시오.

* IndexType 및 `IndexDamAssetLucene` 품질 규칙의 유형 및 심각도가 변경되었습니다. 이러한 규칙은 이제 모두 Bugs of Blocker *심각도*&#x200B;입니다.

* 비동기 및 Tika 구성을 처리하기 위해 새로운 Oak 인덱스 품질 규칙이 도입되었습니다.

* 프로그램당 최대 SSL 인증서를 50개로 늘립니다.

* 사용자가 Cloud Manager UI를 통해 여러 저장소를 만들고 관리할 수 있는 셀프서비스 기능입니다.

* SonarQube가 불필요하게 Git 내역 데이터를 읽고 있었습니다. 대규모 코드 기반에서 이 기능은 불필요한 빌드 성능 저하로 이어질 수 있습니다.

* 이제 파이프라인당 Maven 종속성 캐시를 무효화하는 데 사용할 수 있는 API가 있습니다.

* Cloud Manager에서 사용하는 AEM Project Archetype이 버전 29로 업데이트되었습니다.

### 버그 수정 {#bug-fixes-aug}

* 최신 릴리스가 현재 릴리스보다 낮은 경우 업데이트 사용 가능 상태가 표시되지 않았습니다.

* 이름이 매우 긴 새로운 조직의 경우 초기 온보딩이 실패했습니다.

* 어떤 이유로든 파이프라인이 두 번 트리거되면 그 중 한 번의 실행이 *파이프라인 실행 상태를 업데이트할 수 없음* 오류와 함께 실패했습니다.

## 콘텐츠 전송 도구 {#content-transfer-tool}

### 릴리스 날짜 {#release-date-ctt-latest}

컨텐츠 전송 도구 v1.5.6의 릴리스 날짜는 2021년 8월 11일입니다.

### 버그 수정 {#bug-fixes-ctt}

* 일부 경우에는 모든 사용자가 대상 인스턴스로 마이그레이션되지 않았습니다. 이 수정 사항을 가져오려면 대상 AEM as a Cloud Service 인스턴스에 aem-ethos-tools 1.2.354 이상 버전과 함께 CTT v1.5.6이 필요합니다.

* 다음 **수집 중단** 게시 인스턴스로 수집하는 동안 버튼이 비활성화되었습니다. 게시 수집 중에 mongo 복원 단계가 없으므로 필요하지 않습니다.

* CTT가 다음을 정리하지 않았습니다. `/tmp` 성공적으로 추출한 후 디렉토리. 이로 인해 디스크 공간 문제가 발생하기도 했습니다.
