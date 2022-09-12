---
title: ' [!DNL Adobe Experience Manager] as a Cloud Service의 2021.8.0 릴리스 정보입니다.'
description: ' [!DNL Adobe Experience Manager] as a Cloud Service의 2021.8.0 릴리스 정보입니다.'
exl-id: 8b041934-1c4a-4670-9b03-d38f683b99e5
source-git-commit: 940a01cd3b9e4804bfab1a5970699271f624f087
workflow-type: tm+mt
source-wordcount: '1032'
ht-degree: 30%

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

[!DNL Adobe Experience Manager] as a [!DNL Cloud Service]의 현재 릴리스(2021.8.0) 날짜는 2021년 26월 8일입니다.
다음 릴리스(2021.9.0)는 2021년 10월 6일입니다.

## 릴리스 비디오 {#release-video}

을(를) 보십시오. [2021년 8월 릴리스 개요](https://video.tv.adobe.com/v/336277) 비디오 를 참조하십시오.

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### [!DNL Assets]의 새로운 기능 {#assets-features}

* 디지털 자산을 링크로 공유할 때 사용자는 바로 URL을 클립보드에 복사할 수 있습니다. 개선 사항을 통해 자산을 보다 빠르고 편리하게 공유할 수 있습니다. 이 기능을 사용하면 자산 공유를 빠르고 편리하게 할 수 있습니다.

   ![자산을 링크로 공유할 때 URL 복사 옵션](/help/assets/assets/link-share-copy-URL-option.png)
   *그림: 이제 링크로 자산을 공유할 때 URL을 복사하여 별도로 공유할 수 있습니다.*

* TXT 파일을 업로드하면 자산 마이크로서비스가 자동으로 축소판을 생성합니다. PNG 축소판은 사용자가 파일을 열지 않고 일정하게 내용이나 파일을 식별하는 데 도움이 되는 TXT 파일의 표현입니다. 이 기능은 구성이 필요하지 않으며 기본적으로 작동합니다.

   ![TXT 파일의 표현물은 [!DNL Assets] PNG 형식](/help/assets/assets/thumbnail-rendition-txt-file.png)
   *그림: TXT 파일의 표현물이 자동으로 생성되어 파일을 열지 않고 식별할 수 있습니다.*

### 의 새로운 기능 [!DNL Assets] 사전 릴리스 채널 {#assets-prerelease-features}

* 이제 사용자는 열 및 카드 보기에서 검색 결과에 표시된 자산을 정렬할 수 있습니다. 정렬은 이름, 작성, 수정 또는 없음 열에서 작동합니다.

   ![검색 결과 정렬 위치 [!DNL Assets] 열 및 카드 보기에서](/help/assets/assets/sort-searched-assets.png)
   *그림: 검색 결과 정렬 위치 [!DNL Assets] 열 및 카드 보기에서 다음을 수행합니다.*

### [!DNL Assets]의 수정된 버그 {#assets-bugs-fixed}

* 기여자 그룹의 구성원이 [!DNL Assets] 콘솔, 추가 `POST` 컬렉션을 만들려고 요청이 생성됩니다. 이 요청은 필요하지 않으며, 권한 문제로 인해 실패하며, 로그에 많은 오류가 발생합니다. (CQ-4328856)
* 사용자가 자산을 보고 [!UICONTROL 타임라인] 왼쪽 패널의 팝업 메뉴에서 오류가 표시됩니다. 로그에서 잘못된 쿼리로 인해 많은 경고가 기록됩니다. (CQ-4328919)

## [!DNL Experience Manager Forms] 로서의 [!DNL Cloud Service] {#forms}

### [!DNL Forms]의 새로운 기능 {#what-is-new-forms}

* automated forms conversion 서비스는 다음을 수행할 수 있습니다 [이탈리아어 및 포르투갈어로 PDF forms 변환](https://experienceleague.adobe.com/docs/aem-forms-automated-conversion-service/using/extending-the-default-meta-model.html?#language-specific-meta-model) 응용 Forms에 매핑됩니다.

* **Acroform 기반 기록 문서**: AEM Forms as a Cloud Service는 XFA 기반 양식 템플릿 외에 기록 문서용 템플릿으로도 [Adobe Acrobat Form PDF(Acroform PDF)](https://experienceleague.adobe.com/docs/experience-manager-forms-cloud-service/forms/create-an-adaptive-form/generate-document-of-record-for-non-xfa-based-adaptive-forms.html)을 사용할 수 있도록 지원합니다.

* **Microsoft Azure 데이터 스토어 커넥터**: 이제 [양식 데이터 모델을 Microsoft Azure Storage에 연결](https://experienceleague.adobe.com/docs/experience-manager-forms-cloud-service/forms/use-form-data-model/configure-azure-storage.html)할 수 있습니다. 이를 통해, 적응형 양식 데이터를 검색하여 Microsoft Azure Storage에 BLOB로 저장할 수 있습니다.

### [!DNL Forms] 프리릴리스 채널에서 사용할 수 있는 새로운 기능 {#prerelease-features-forms}

* **적응형 양식에서 Adobe Sign 역할 사용**: 비즈니스 및 엔터프라이즈 서비스 수준을 위한 Adobe Sign은 계약 수신자의 역할을 서명자 이상으로 확장하는 옵션을 제공하여 워크플로 요구 사항에 보다 잘 부합하도록 합니다. 이제 계약의 각 수신자가 적응형 양식에서 자신의 역할을 구성할 수 있으며, 서명자는 기본 역할입니다.

* **적응형 양식용 Analytics**: 이제 적응형 양식용 Adobe Analytics를 통해 최종 사용자 행동을 포착하고 추적하여 최종 사용자 인사이트를 수집할 수 있습니다. 이로써 데이터를 기반으로 정보에 입각한 결정을 내려 최종 사용자 경험을 개선할 수 있습니다.

* **Microsoft Dynamics 및 Salesforce.com과 AEM Forms을 쉽게 연결**: 이 서비스는 Microsoft Dynamics 및 Salesforce.com용 기본 데이터 소스 구성 및 데이터 모델을 제공하므로 개발자가 적응형 양식의 데이터 소스로 Microsoft Dynamics 및 Salesforce.com을 보다 빠르고 쉽게 구성할 수 있습니다.

## CIF 추가 기능 {#cloud-services-cif}

### 새로운 기능 {#what-is-new-cif}

* 향상된 사용자 환경, 향상된 효율성 및 복잡한 제품 카탈로그에 대한 향상된 지원을 제공하는 새로운 카테고리 선택기 UI

   ![새 카테고리 선택기](/help/assets/CIF/category-picker.png)

* CIF A11Y 구성 요소에 대한 지원 개선

## Cloud Manager {#cloud-manager}

이 섹션에서는 AEM as a Cloud Service 2021.8.0 및 2021.7.0에서 Cloud Manager에 대한 릴리스 노트를 간략하게 설명합니다.

## 릴리스 날짜 {#release-date-cm-aug}

AEM as a Cloud Service 2021.8.0의 Cloud Manager 릴리스 날짜는 2021년 8월 12일입니다.
다음 릴리스는 2021년 9월 9일에 예정되어 있습니다.

### 새로운 기능 {#what-is-new-aug}

* 이제 Cloud Service 고객은 Cloud Manager에서 SLA(서비스 수준 계약) 보고서를 볼 수 있습니다. 이 기능은 다음 몇 달 동안 점진적으로 제공될 예정입니다.
자세한 내용은 [SLA 보고](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/sla-reporting.html) 추가 정보

* IndexType 및 `IndexDamAssetLucene` 품질 규칙이 변경되었습니다. 이제 둘 다 Blocker의 버그입니다 *서버*.

* 비동기 및 tika 구성을 다루는 새로운 Oak 색인 품질 규칙이 도입되었습니다.

* 프로그램당 최대 SSL 인증서를 50개로 늘립니다.

* 사용자가 Cloud Manager UI를 통해 여러 저장소를 만들고 관리할 수 있는 셀프 서비스 기능입니다.

* SonarQube가 불필요하게 Git 내역 데이터를 읽고 있었습니다. 큰 코드 베이스에서 이로 인해 불필요한 빌드 성능 벌금이 발생할 수 있습니다.

* 이제 파이프라인당 Maven 종속성 캐시를 무효화하는 데 사용할 수 있는 API가 있습니다.

* Cloud Manager에서 사용하는 AEM 프로젝트 원형 버전이 버전 29로 업데이트되었습니다.

### 버그 수정 {#bug-fixes-aug}

* 최신 릴리스가 현재 릴리스보다 작을 경우 사용 가능한 업데이트 상태가 표시되지 않아야 합니다.

* 매우 긴 이름을 가진 새로운 조직에 대해 초기 온보딩이 실패했습니다.

* 경우에 따라 파이프라인이 어떤 이유로 두 번 트리거되면 *파이프라인 실행 상태를 업데이트할 수 없습니다.* 오류가 발생했습니다.

## 콘텐츠 전송 도구 {#content-transfer-tool}

### 릴리스 날짜 {#release-date-ctt-latest}

컨텐츠 전송 도구 v1.5.6의 릴리스 날짜는 2021년 8월 11일입니다.

### 버그 수정 {#bug-fixes-ctt}

* 일부 경우에는 일부 사용자가 target 인스턴스로 마이그레이션되지 않았습니다. 이 수정 사항을 가져오려면 target AEM as a Cloud Service 인스턴스의 aem-etos-tools 1.2.354 이상 버전과 함께 CTT v1.5.6이 필요합니다.

* 다음 **수집 중지** 게시 인스턴스에 수집하는 동안 단추가 비활성화되었습니다. 게시 수집 중에 단일 복원 단계가 없으므로 이 작업은 필요하지 않습니다.

* CTT가 `/tmp` 성공적으로 추출한 후의 디렉토리입니다. 이로 인해 디스크 공간 문제가 발생하는 경우가 있습니다.
