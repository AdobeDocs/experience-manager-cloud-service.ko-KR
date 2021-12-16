---
title: 의 현재 릴리스 노트 [!DNL Adobe Experience Manager] as a Cloud Service.
description: 의 현재 릴리스 노트 [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: a2d56721-502c-4f4e-9b72-5ca790df75c5
mini-toc-levels: 1
source-git-commit: edb547fa31158e1608b57231d9705d24f008b12e
workflow-type: tm+mt
source-wordcount: '1049'
ht-degree: 2%

---


# 의 현재 릴리스 노트 [!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

다음 섹션에서는 현재(최신) 버전의 [!DNL Experience Manager] as a Cloud Service.

>[!NOTE]
>
>여기에서 이전 버전의 릴리스 정보로 이동할 수 있습니다. 예를 들어, 2020년, 2021년 등의 경우입니다.

>[!NOTE]
>
>자세한 내용은 [최근 설명서 업데이트](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html) 릴리스 정보와 직접 관련이 없는 설명서 업데이트 세부 정보는

## 릴리스 날짜 {#release-date}

의 릴리스 날짜 [!DNL Adobe Experience Manager] 로서의 [!DNL Cloud Service] 현재 릴리스(2021.11.0)은 2021년 12월 16일입니다.
다음 릴리스(2022.1.0)는 2022년 1월 27일입니다.

## 릴리스 비디오 {#release-video}

을(를) 보십시오. [2021년 12월 릴리스 개요](https://video.tv.adobe.com/v/339278) 비디오 를 참조하십시오.

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### 의 새로운 기능 [!DNL Assets] {#assets-features}

* 이제 Dynamic Media 이미지 스마트 자르기 및 색상 견본을 최신 Sensei 서비스에서 제공하며 향상된 자르기 및 색상 견본을 생성합니다. 또한 동일한 종횡비이지만 다양한 해상도에서 서로 다른 자르기 콘텐츠를 생성하기 위한 개선 사항을 시작했습니다. 또한 이미지 프로필의 폭과 높이가 변경되지 않은 경우 수동 편집 내용은 재처리 시 유지됩니다.

### 의 새로운 기능 [!DNL Assets] 사전 릴리스 채널 {#assets-prerelease-features}

* [!DNL Dynamic Media] - 이제 AEM Dynamic Media 인터페이스를 사용하여 Dynamic Media Classic 데스크탑 응용 프로그램을 진행할 필요 없이 일반 설정 및 게시 설정을 구성할 수 있습니다.

* [!DNL Dynamic Media] 이제에서 MXF 비디오에 대한 수집, 미리 보기, 재생 및 게시를 지원합니다. MXF 비디오에 대한 주석 및 쇼퍼블 비디오는 아직 지원되지 않습니다.

* 원격 DAM과 사이트 배포 간에 연결을 구성한 후 원격 DAM의 자산을 사이트 배포에서 사용할 수 있습니다. 이제 원격 DAM 자산 또는 폴더에서 업데이트, 삭제, 이름 변경 및 이동 작업을 수행할 수 있습니다. 업데이트가 지연되면 사이트 배포에서 자동으로 사용할 수 있습니다.

## [!DNL Experience Manager Forms] 로서의 [!DNL Cloud Service] {#forms}

### 의 새로운 기능 [!DNL Forms] {#what-is-new-forms}

* **Forms 포털**: 다음을 사용할 수 있습니다 [Forms 포털](/help/forms/configure-forms-portal.md) 게시된 적응형 양식을 AEM Sites 페이지에 나열하려면 다음을 수행하십시오. 사이트 방문자가 사용 가능한 모든 양식을 검색하는 데 도움이 됩니다. 또한 방문자는 양식 포털을 사용하여 적응형 양식의 초안을 저장하고 액세스하고 제출된 적응형 양식의 PDF 버전을 볼 수 있습니다.

* **보안 처리를 위한 AEM 워크플로우 데이터 표면화**: 안전한 처리를 위해 고객 관리 저장소에 민감한 개인 데이터(SPD) 요소를 포함하는 처리 중인 AEM 워크플로우 데이터(AEM Workflow Variables 데이터)를 저장할 수 있습니다. 데이터 요소와 워크플로우 변수는 AEM 저장소에 저장되지 않으며 워크플로우를 처리하는 동안 고객 관리 저장소에서 주문형 가져옵니다.

### 에서 사용할 수 있는 새로운 기능 [!DNL Forms] 사전 릴리스 채널 {#prerelease-features-forms}

* **[!DNL AEM Forms as a Cloud Service - Communications]**: [통신 API](https://experienceleague.adobe.com/docs/experience-manager-forms-cloud-service/forms/using-communications/aem-forms-cloud-service-communications.html) 서식 파일과 XML 데이터를 결합하여 인쇄 문서를 다양한 형식으로 생성하는 데 도움이 됩니다. 이 서비스를 사용하면 문서를 동기식과 배치 모드로 생성할 수 있습니다. API를 사용하면 다음을 수행할 수 있는 애플리케이션을 만들 수 있습니다.

   * XML 데이터로 템플릿 파일(PDF 및 XDP)을 채워서 문서를 생성합니다.
   * 비대화형 PDF 인쇄 스트림을 포함하여 다양한 형식으로 출력 양식을 생성합니다.

* **Communications API로 작성된 레코드 문서 및 PDF 문서에 대한 사용자 정의 글꼴**: 이제 Communications API를 사용하여 생성된 PDF 문서에서 브랜드 승인 글꼴을 사용하여 조직 요구 사항에 맞게 만들 수 있습니다.

## CIF 추가 기능 {#cloud-services-cif}

### 새로운 기능 {#what-is-new-cif}

* Commerce의 확장 가능한 상위 구성 요소를 기반으로 하는 myAccount 구성 요소를 확장했습니다

![확장 myAccount 구성 요소](/help/assets/CIF/extended-myAccount-components.png)

* 작성자는 추가 권장 사항 유형을 사용하여 Ad-Hoc Commerce 제품 Recommendations을 만들 수 있습니다

* AEM Storefront에서 기프트 카드 지원

## Cloud Manager {#cloud-manager}

이 섹션에서는 AEM as a Cloud Service에서 Cloud Manager에 대한 릴리스 노트를 간략하게 설명합니다.

### 릴리스 날짜 {#release-date-cm-nov}

AEM as a Cloud Service 2021.11.0의 Cloud Manager 릴리스 날짜는 2021년 11월 4일입니다.
다음 릴리스는 2021년 12월 9일에 예정되어 있습니다.

### 새로운 기능 {#what-is-new-cm-nov}

* 이제 사용자는 새로운 프런트 엔드 파이프라인을 활용하여 프런트 엔드 코드만 신속하게 배포할 수 있습니다. 자세한 내용은 [Cloud Manager 프런트엔드 파이프라인](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md#front-end) 추가 정보

   >[!IMPORTANT]
   >AEM 버전을 사용해야 합니다. `2021.10.5933.20211012T154732Z` 또는 그 이상으로 새로운 프런트엔드 파이프라인을 활용합니다.

* 코드 품질 파이프라인 기간은 전체 AEM 이미지를 작성하지 않고도 보다 효율적인 방식으로 코드 분석을 수행하므로 크게 줄어듭니다. 이 변경 사항은 릴리스 후 몇 주에 걸쳐 점진적으로 롤아웃됩니다.

* 이제 Git 커밋 ID가 파이프라인 실행 세부 사항에 표시되므로 빌드된 코드를 쉽게 추적할 수 있습니다.

* 이제 공개적으로 노출된 API를 통해 프로그램 생성을 사용할 수 있습니다.

* 이제 공개적으로 노출된 API를 통해 환경 만들기를 사용할 수 있습니다.

* 다음 `x-request-id` 이제 응답 헤더가 의 API Playground에 표시됩니다. [www.adobe.io](https://www.adobe.io/). 이 헤더는 문제 해결을 위해 고객 지원 문제를 제출할 때 유용합니다.

* 사용자는 파이프라인이 없는 파이프라인 카드에 적절한 지침이 제공됩니다.

* 이제 연관된 세부 사항과 함께 파이프라인 및 코드 실행과 같은 활동을 볼 수 있는 새로운 활동 페이지를 사용할 수 있습니다. 시간이 지나면서 이 페이지에 나열된 활동은 제공된 세부 정보와 함께 범위가 확장됩니다.

* 이제 세부 사항 요약을 쉽게 볼 수 있도록 마우스로 가리키면 상태 팝오버가 있는 새 파이프라인 페이지를 사용할 수 있습니다. 파이프라인 실행은 연관된 세부 정보와 함께 볼 수 있습니다.

* 이제 파이프라인 편집 API에서 배포 단계에서 사용되는 환경 변경을 지원합니다.

* 큰 패키지에 대해 OakPal 검색 프로세스의 최적화가 도입되었습니다.

* 이제 품질 문제 CSV 파일에 각 품질 문제에 대한 타임스탬프가 포함됩니다.

### 버그 수정 {#bug-fixes-nov}

* 특정 비정형 빌드 구성은 빌드 컨테이너를 시작 및 중지할 때 외부 네트워크 I/O를 발생시킨 파이프라인의 Maven 아티팩트 캐시에 불필요한 파일이 저장되었습니다.

* 배포 단계가 없는 경우 파이프라인 PATCH API가 실패합니다.

* 다음 `ClientlibProxyResourceCheck` 일반적인 기본 경로가 있는 클라이언트 라이브러리가 있을 때 품질 규칙이 긍정 오류(false positive)를 생성하는 것이었습니다.

* 최대 저장소 수에 도달했을 때 오류 메시지에 오류 이유를 지정하지 않았습니다.

* 드문 경우이지만 특정 응답 코드를 잘못 처리하여 파이프라인이 실패했습니다.

## 모범 사례 분석기 {#bpa-release}

### 릴리스 날짜 {#release-date-bpa}

Best Practices Analyzer v2.1.22 릴리스 날짜는 2021년 12월 1일입니다.

### 새로운 기능 {#what-is-new-bpa}

* 사용된 ACS commons 버전을 감지하고 보고하는 기능.
* 그룹의 사용자 및 하위 그룹 수를 감지하고 보고하는 기능.
* 16MB를 초과하는 MongoDB의 노드 속성 값을 감지하고 보고할 수 있습니다.

### 버그 수정 {#bug-fixes-bpa}

* 잘못된 네거티브를 줄이기 위해 기초 구성 요소 탐지를 개선했습니다.
* AEM Forms 고객의 경우 `EMAIL_PDF_SUBMIT_ACTION` AEM as a Cloud Service에서 사용할 수 없는 것이 수정되었습니다.
