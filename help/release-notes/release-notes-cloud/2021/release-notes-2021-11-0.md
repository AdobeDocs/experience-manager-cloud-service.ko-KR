---
title: ' [!DNL Adobe Experience Manager] as a Cloud Service의 2021.11.0 릴리스 정보입니다.'
description: ' [!DNL Adobe Experience Manager] as a Cloud Service의 2021.11.0 릴리스 정보입니다.'
exl-id: 86f8ddd1-af51-4874-9111-0935b5a162c1
source-git-commit: 940a01cd3b9e4804bfab1a5970699271f624f087
workflow-type: tm+mt
source-wordcount: '1055'
ht-degree: 100%

---

# [!DNL Adobe Experience Manager] as a Cloud Service 최신 릴리스 정보 {#release-notes}

다음 섹션에서는 [!DNL Experience Manager] as a Cloud Service의 최신 버전 일반 릴리스 정보에 대해 간략히 소개합니다.

>[!NOTE]
>
>여기에서 2020, 2021 버전 등 이전 버전의 릴리스 정보로 이동할 수 있습니다.

>[!NOTE]
>
>릴리스와 직접적으로 관련되지 않는 설명서 업데이트의 세부 정보는 [설명서 업데이트](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html?lang=ko-KR)를 참조하십시오.

## 릴리스 날짜 {#release-date}

[!DNL Adobe Experience Manager] as a [!DNL Cloud Service] 최신 릴리스(2021.11.0)의 릴리스 날짜는 2021년 12월 16일입니다.
다음 릴리스(2022.1.0) 날짜는 2022년 2월 3일입니다.

## 릴리스 비디오 {#release-video}

[2021년 12월 릴리스 개요](https://video.tv.adobe.com/v/339278) 비디오를 통해 2021.11.0(2021년 11월) 릴리스에 추가된 기능에 대한 간단한 요약을 살펴보십시오.

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### [!DNL Assets]의 새로운 기능 {#assets-features}

* Dynamic Media 이미지 스마트 자르기 및 색상 견본은 이제 개선된 자르기 및 색상 견본을 생성하는 최신 Sensei 서비스에서 제공합니다. 동일한 종횡비에 대해 서로 다른 해상도가 적용된 다양한 자르기 콘텐츠 생성을 위해 향상된 기능도 출시되었습니다. 또한 이미지 프로필에서 너비와 높이를 변경하지 않는 경우 재처리 시 수동 편집 기능은 그대로 유지됩니다.

### [!DNL Assets] 프리릴리스 채널의 새로운 기능 {#assets-prerelease-features}

* [!DNL Dynamic Media] - 이제 Dynamic Media Classic 데스크탑 애플리케이션을 사용하지 않고도 AEM Dynamic Media 인터페이스를 사용하여 일반 설정 및 게시 설정을 구성할 수 있습니다.

* [!DNL Dynamic Media]는 이제 MXF 비디오에 대해 수집, 미리보기, 재생 및 게시 기능을 지원합니다. MXF에 대한 주석 및 구매 가능한 비디오는 아직 지원되지 않습니다.

* 원격 DAM 및 Sites 배포 간의 연결을 구성한 후에는 Sites 배포에서 원격 DAM의 에셋을 사용할 수 있습니다. 이제 원격 DAM 에셋 또는 폴더에서의 [작업을 업데이트하고, 삭제하고, 이름을 바꾸고, 이동](/help/assets/use-assets-across-connected-assets-instances.md)할 수 있습니다. 업데이트는 약간의 지연과 함께 Sites 배포에서 자동으로 사용할 수 있습니다.

## [!DNL Experience Manager Forms] 로서의 [!DNL Cloud Service] {#forms}

### [!DNL Forms]의 새로운 기능 {#what-is-new-forms}

* **안전한 처리를 위한 AEM Workflow 데이터 외부화**: 민감한 개인 데이터(SPD) 요소가 포함된, 처리 중인 AEM Workflow 데이터(AEM Workflow 변수 데이터)를 안전하게 처리될 수 있도록 고객 관리 저장소에 저장할 수 있습니다. 데이터 요소와 워크플로 변수는 AEM 저장소에 저장되지 않으며 워크플로 처리 중에 고객 관리 저장소에서 필요에 따라 가져옵니다.

### [!DNL Forms] 프리릴리스 채널에서 사용할 수 있는 새로운 기능 {#prerelease-features-forms}

* **[!DNL AEM Forms as a Cloud Service - Communications]**: [커뮤니케이션 API](https://experienceleague.adobe.com/docs/experience-manager-forms-cloud-service/forms/using-communications/aem-forms-cloud-service-communications.html?lang=ko-KR)를 통해 템플릿과 XML 데이터를 결합하여 다양한 형식의 인쇄 문서를 생성할 수 있습니다. 이 서비스를 사용하면 동기화 모드와 배치 모드에서 문서를 생성할 수 있습니다. API를 사용하면 다음과 같은 기능을 제공하는 애플리케이션을 만들 수 있습니다.

   * XML 데이터로 템플릿 파일(PDF 및 XDP)을 채워 문서를 생성합니다.
   * 비대화형 PDF 인쇄 스트림을 포함하여 다양한 형식의 출력 양식을 생성합니다.

* **커뮤니케이션 API로 생성된 기록 문서 및 PDF 문서에 대한 맞춤형 글꼴**: 이제 커뮤니케이션 API를 사용하여 생성된 PDF 문서의 브랜드 승인 글꼴을 사용하여 조직 요구 사항을 맞출 수 있습니다.

* **Forms 포털**: [Forms 포털](/help/forms/configure-forms-portal.md)을 사용하여 AEM Sites 페이지에 게시된 적응형 양식을 나열할 수 있습니다. 이렇게 하면 사이트 방문자가 사용 가능한 모든 양식을 탐색할 수 있습니다. 또한 방문자는 Forms 포털을 사용하여 적응형 양식의 초안을 저장 및 액세스하고 제출된 적응형 양식의 PDF 버전을 살펴볼 수 있습니다.

## CIF 추가 기능 {#cloud-services-cif}

### 새로운 기능 {#what-is-new-cif}

* Commerce의 확장 가능한 Peregrine 구성 요소를 기반으로 하는 확장 myAccount 구성 요소

![확장 myAccount 구성 요소](/help/assets/CIF/extended-myAccount-components.png)

* 작성자는 추가 권장 사항 유형을 사용하여 애드혹 Commerce 제품 권장 사항을 생성할 수 있습니다.

* AEM 상점에서의 기프트 카드 지원

## Cloud Manager {#cloud-manager}

이 섹션에서는 AEM as a Cloud Service 2021.11.0의 Cloud Manager 릴리스 정보에 대해 간략히 소개합니다.

### 릴리스 날짜 {#release-date-cm-nov}

AEM as a Cloud Service 2021.11.0의 Cloud Manager 릴리스 날짜는 2021년 11월 4일입니다.
다음 릴리스는 2021년 12월 9일에 예정되어 있습니다.

### 새로운 기능 {#what-is-new-cm-nov}

* 이제 새로운 프론트엔드 파이프라인을 활용하여 가속화된 방식으로 프론트엔드 코드를 독점적으로 배포할 수 있습니다. 자세히 알아보려면 [Cloud Manager 프론트엔드 파이프라인](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md#front-end)을 참조하십시오.

   >[!IMPORTANT]
   >새 프론트엔드 파이프라인을 활용하려면 AEM 버전 `2021.10.5933.20211012T154732Z` 이상을 사용해야 합니다.

* 전체 AEM 이미지를 구축할 필요 없이 더 효율적인 방식으로 코드 분석을 수행함으로써 코드 품질 파이프라인 지속 시간이 크게 단축됩니다. 이러한 변경 내용은 출시 후 몇 주 동안 점진적으로 적용될 예정입니다.

* 이제 파이프라인 실행 세부 정보에 Git Commit ID가 표시되어 작성된 코드를 더 쉽게 추적할 수 있습니다.

* 이제 프로그램 생성을 공개적으로 노출된 API를 통해 사용할 수 있습니다.

* 이제 환경 생성을 공개적으로 노출된 API를 통해 사용할 수 있습니다.

* 이제 `x-request-id` 응답 헤더를 [www.adobe.io](https://www.adobe.io/)의 API Playground에서 볼 수 있습니다. 이 헤더는 문제 해결을 위한 고객 지원 센터 문제 제출 시 유용합니다.

* 나는 사용자로서 파이프라인이 없는 파이프라인 카드가 적절한 지침을 제공함을 확인합니다.

* 이제 파이프라인 및 코드 실행과 같은 활동과 함께 관련 세부 정보를 볼 수 있는 새 활동 페이지를 사용할 수 있습니다. 시간이 지남에 따라 이 페이지에 나열된 활동은 제공된 세부 정보와 함께 범위 내에서 확장됩니다.

* 이제 세부 정보 요약을 쉽게 볼 수 있도록 상태 팝오버가 표시된 새 파이프라인 페이지를 사용할 수 있습니다. 파이프라인 실행을 관련 세부 정보와 함께 볼 수 있습니다.

* 이제 편집 파이프라인 API는 배포 단계에 사용되는 환경 변경을 지원합니다.

* OakPal 스캔 프로세스에서의 최적화가 대형 패키지에 도입되었습니다.

* 이제 품질 문제 CSV 파일에는 각 품질 문제에 대해 타임스탬프가 포함됩니다.

### 버그 수정 {#bug-fixes-nov}

* 특정 비정형 빌드 구성으로 인해 파이프라인의 Maven 아티팩트 캐시에 불필요한 파일이 저장되었으며, 빌드 컨테이너 실행 및 중지 시 불필요한 네트워크 I/O가 발생했습니다.

* 배포 단계가 없는 경우 파이프라인 PATCH API에 오류가 발생했습니다.

* 일반 기본 경로를 가진 클라이언트 라이브러리가 있을 때 `ClientlibProxyResourceCheck` 품질 규칙에 거짓 양성 문제가 발생했습니다.

* 최대 저장소 수에 도달했을 때 오류 메시지가 오류의 원인을 식별하지 못했습니다.

* 드문 경우에 특정 응답 코드의 부적절한 재시도 처리로 인해 파이프라인에 오류가 발생했습니다.

## 모범 사례 분석기 {#bpa-release}

### 릴리스 날짜 {#release-date-bpa}

모범 사례 분석기 v2.1.22의 릴리스 날짜는 2021년 12월 1일입니다.

### 새로운 기능 {#what-is-new-bpa}

* 사용된 ACS 커먼즈 버전 감지 및 보고 기능.
* 그룹 내 사용자 및 하위 그룹 수 감지 및 보고 기능.
* 16MB를 초과하는 MongoDB의 노드 속성 값 감지 및 보고 기능.

### 버그 수정 {#bug-fixes-bpa}

* Foundation 구성 요소의 감지가 거짓 음성을 줄이도록 개선되었습니다.
* AEM Forms 고객의 경우 AEM as a Cloud Service에서 사용할 수 없는 `EMAIL_PDF_SUBMIT_ACTION` 관련 BPA 메시징이 수정되었습니다.
