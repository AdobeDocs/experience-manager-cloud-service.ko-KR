---
title: ' [!DNL Adobe Experience Manager] as a Cloud Service의 2021.10.0 릴리스 정보입니다.'
description: ' [!DNL Adobe Experience Manager] as a Cloud Service의 2021.10.0 릴리스 정보입니다.'
exl-id: ab584923-5f06-4b54-941b-e00bc1158b81
feature: Release Information
role: Admin
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '1436'
ht-degree: 70%

---

# [!DNL Adobe Experience Manager] as a Cloud Service 최신 릴리스 정보 {#release-notes}

다음 섹션에서는 [!DNL Experience Manager] as a Cloud Service의 최신 버전 일반 릴리스 정보에 대해 간략히 소개합니다.

>[!NOTE]
>
>여기에서 2020, 2021 버전 등 이전 버전의 릴리스 정보로 이동할 수 있습니다.

>[!NOTE]
>
>릴리스와 직접적으로 관련되지 않는 설명서 업데이트의 세부 정보는 [설명서 업데이트](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html?lang=ko-KR)를 참조하십시오.

## 릴리스 일자 {#release-date}

[!DNL Adobe Experience Manager] as a [!DNL Cloud Service]의 현재 릴리스(2021.10.0) 날짜는 2021년 11월 4일 금요일입니다.
다음 릴리스(2021.11.0) 날짜는 2021년 12월 2일 금요일입니다.

## 릴리스 비디오 {#release-video}

다음을 살펴보십시오. [2021년 10월 릴리스 개요](https://video.tv.adobe.com/v/338253) 추가된 기능에 대한 요약을 보려면 비디오 를 사용하십시오.

## [!DNL Experience Manager Sites] as a [!DNL Cloud Service] {#sites}

### 의 새로운 기능 [!DNL Sites] {#sites-features}

* 이제 콘텐츠 조각 모델은 게시된 후 읽기 전용 상태로 자동 설정되므로, 편집된 모델을 다시 게시한 후 의도하지 않게 라이브 API 쿼리가 중단되는 것을 방지할 수 있습니다. 게시된 모델을 편집하려고 할 때 사용자에게 경고 메시지가 표시됩니다. 경고를 수락하면 편집할 수 있습니다.

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### [!DNL Assets]의 새로운 기능 {#assets-features}

* [!DNL Experience Manager] 는 이제 기본 제공 커넥터를 사용하여 지원되는 오디오 및 비디오 에셋에서 텍스트 트랜스크립트를 자동으로 생성합니다. [!DNL Azure Media Services]. 다음 [지원되는 파일 유형](/help/assets/file-format-support.md#audio-video-transcription-formats) 는 자동으로 기록되며 텍스트는 WebVTT 형식으로 저장됩니다. WebVTT 캡션은 보다 효과적인 검색, 캡션 또는 번역에 사용됩니다. 또한 이 기능은 에셋의 접근성, 검색 기능 및 현지화 기능을 향상시킵니다.

### 의 새로운 기능 [!DNL Assets] 프리릴리스 채널 {#assets-prerelease-features}

* [!DNL Dynamic Media] 이미지 스마트 자르기 및 색상 견본 은 이제 개선된 자르기 및 색상 견본을 생성하는 최신 Sensei 서비스에서 제공합니다. 동일한 종횡비에 대해 서로 다른 해상도가 적용된 다양한 자르기 콘텐츠 생성을 위해 향상된 기능도 출시되었습니다. 또한 이미지 프로필에서 너비와 높이를 변경하지 않는 경우 재처리 시 수동 편집 기능은 그대로 유지됩니다.

* 스마트 태그는 스마트 컨텐츠 서비스 대신 에셋 마이크로서비스를 사용하여 에셋에 자동으로 적용됩니다. 태깅 결과를 개선하고 편향을 줄이기 위해 기본 모델을 업데이트합니다. <!-- As it uses asset microservices, it is now possible to develop custom workers using Stock10-based Smart Tags. -->

<!-- Leave this commented.
### Bugs fixed in [!DNL Assets] {#assets-bugs-fixed}

No customer-reported bugs fixed in Oct release. Details in CQDOC-18404.
-->

## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

### [!DNL Forms]의 새로운 기능 {#what-is-new-forms-oct-2021}

* **적응형 Forms에 대한 Analytics**: 이제 적응형 Forms용 Adobe Analytics을 통해 로그인된 및 로그인되지 않은(익명의) 사용자 행동을 포착하고 추적하여 사용자 인사이트를 수집할 수 있습니다. 이로써 데이터를 기반으로 정보에 입각한 결정을 내려 사용자 경험을 개선할 수 있습니다.

### [!DNL Forms] 프리릴리스 채널에서 사용할 수 있는 새로운 기능 {#prerelease-features-forms-oct-2021}

* **안전한 처리를 위한 AEM Workflow 데이터 외부화**: 민감한 개인 데이터(SPD)가 포함된, 처리 중인 AEM 워크플로 데이터(AEM Workflow 변수 데이터)가 안전하게 처리될 수 있도록 고객 관리 저장소에 저장할 수 있습니다. 데이터 요소와 워크플로 변수는 AEM 저장소에 저장되지 않으며 워크플로 처리 중에 고객 관리 저장소에서 필요에 따라 가져옵니다.

### [!DNL Forms]의 베타 기능 {#what-is-new-forms-oct2021-beta}

* **[!DNL AEM Forms as a Cloud Service - Communications]**: [커뮤니케이션 API](https://experienceleague.adobe.com/docs/experience-manager-forms-cloud-service/forms/using-communications/aem-forms-cloud-service-communications.html?lang=ko-KR)를 통해 템플릿과 XML 데이터를 결합하여 다양한 형식의 인쇄 문서를 생성할 수 있습니다. 이 서비스를 통해 동기화 모드와 배치 모드에서 문서를 생성할 수 있습니다. API를 사용하면 다음과 같은 기능을 제공하는 애플리케이션을 만들 수 있습니다.

   * XML 데이터로 템플릿 파일(PDF 및 XDP)을 채워 문서를 생성합니다.
   * 비대화형 PDF 인쇄 스트림을 포함하여 다양한 형식의 출력 양식을 생성합니다.

Beta 프로그램에 등록하려면 [!DNL formscsbeta@adobe.com]에 문의하십시오.

## CIF 추가 기능 {#cloud-services-cif}

### 새로운 기능 {#what-is-new-cif}

* CIF 추가 기능은 새 GraphQL API 및 스키마가 포함된 최신 Commerce v2.4.3을 지원합니다

* 작성자는 리치 텍스트 편집기(RTE)를 사용하여 텍스트 필드의 제품 및 카탈로그 페이지에 링크를 추가할 수 있습니다. RTE 도구 모음에 CIF 아이콘이 추가되어 선택기를 열어 컨텍스트를 종료하지 않고 제품이나 카테고리를 빠르게 검색하고 선택할 수 있습니다.

* 기존 팝업 장바구니 및 체크아웃이 전용 AEM 장바구니 및 체크아웃 페이지로 대체되었습니다. 이러한 페이지의 구성 요소는 Adobe Commerce의 확장 가능한 Peregrine 구성 요소를 사용하여 빌드됩니다

* 판매자는 Commerce 백엔드를 사용하여 탐색에서 특정 제품 카탈로그 범주를 숨길 수 있습니다. CIF 탐색 핵심 구성 요소는 상거래 백엔드 구성 &quot;메뉴에 포함&quot;을 준수하여 탐색에서 범주를 표시하거나 숨깁니다

* 범주 또는 제품 페이지를 찾을 수 없는 경우 AEM Storefront Venia가 HTTP 404 오류를 반환합니다.

## Cloud Manager {#cloud-manager}

이 섹션에서는 AEM as a Cloud Service 2021.10.0의 Cloud Manager 릴리스 정보에 대해 간략히 소개합니다.

### 릴리스 날짜 {#release-date-cm-nov}

AEM as a Cloud Service 2021.11.0의 Cloud Manager 릴리스 날짜는 2021년 11월 4일입니다.
다음 릴리스는 2021년 12월 9일에 예정되어 있습니다.

### 새로운 기능 {#what-is-new-cm-nov}

* 이제 새로운 프론트엔드 파이프라인을 통해 가속화된 방식으로 프론트엔드 코드를 독점적으로 배포할 수 있습니다. 자세히 알아보려면 [Cloud Manager 프론트엔드 파이프라인](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md#front-end)을 참조하십시오.

  >[!IMPORTANT]
  >새 프론트엔드 파이프라인을 사용하려면 AEM 버전 `2021.10.5933.20211012T154732Z`이어야 합니다.

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


## 릴리스 일자 {#release-date-cm-oct}

AEM as a Cloud Service 2021.10.0의 Cloud Manager 릴리스 일자는 2021년 10월 14일입니다.

### 새로운 기능 {#what-is-new-cm-oct}

* 향후 변경에 대비하여 이제 기존 배포 파이프라인이 사용자 인터페이스에서 **전체 스택** 파이프라인으로 참조되고 레이블이 지정됩니다.

* 파이프라인 카드는 이제 프로덕션 및 비프로덕션 파이프라인을 모두 통합하여 표시하도록 새로 고쳐졌으며 사용자는 각 파이프라인과 연결된 동작 메뉴에서 직접 실행/일시 중지/다시 시작을 선택할 수 있습니다.

* 배포 관리자 역할의 사용자는 이제 UI를 통해 셀프서비스 방식으로 프로덕션 파이프라인을 삭제할 수 있습니다.

* 파이프라인 추가 및 편집 경험이 이제 친숙한 최신 모달을 사용하도록 새로 고쳐졌습니다.

* Cloud Manager 사용자는 이제 랜딩 페이지의 오른쪽 상단에 있는 **피드백** 버튼을 통해 사용자 인터페이스에서 직접 피드백을 제출할 수 있습니다.

* 이제 Cloud Manager의 사용자 인터페이스에서 연간 SLA 그래프를 다운로드할 수 있습니다.

* 코드 품질 및 비프로덕션 파이프라인 실행은 이제 빌드 단계에서 보다 효율적인 약식 복제 프로세스를 사용하므로 특히 큰 git 저장소를 사용하는 고객의 빌드 시간이 빨라집니다.

* IP 허용 목록 추가 마법사는 이제 최대 IP 허용 목록 수에 도달한 경우 사용자에게 알립니다.

* Cloud Manager API 설명서에는 이제 로그인한 사용자가 브라우저에서 API를 실험할 수 있는 대화형 플레이그라운드가 포함됩니다. 자세한 내용은 [Cloud Manager API 플레이그라운드](https://www.adobe.io/experience-cloud/cloud-manager/reference/playground/)를 참조하십시오.

* &#39;이동&#39; 아래의 선택 옵션이 비활성화된 경우 프로그램 카드의 도구 설명에 더 설명한 설명이 표시됩니다. 이제 “프로덕션 환경이 존재하지 않습니다.”라고 표시됩니다.

### 버그 수정 {#bug-fixes-cm-oct}

* 드물지만 Adobe 직원이 고객의 환경을 복원할 때 환경이 완전히 작동하기 전에 복원이 완료된 것으로 간주되는 경우가 있었습니다.

* 환경 생성 중에 수행된 특정 내부 요청이 재시도되지 않았습니다.

* 도메인 이름 확인 후 배포 실패 오류가 발생하는 경우 고객이 Adobe 담당자에게 문의하도록 오류 메시지가 수정되었습니다.

## Best Practices Analyzer {#best-practices-analyzer}

### 릴리스 날짜 {#release-date-bpa-latest}

모범 사례 분석기 v2.1.20의 릴리스 날짜는 2021년 10월 5일입니다.

### 새로운 기능 {#what-is-new}

* 노드 이름 길이를 감지하고 보고하는 기능.

* 총 색인 크기를 감지하고 보고하는 기능.

* 원본 렌디션이 누락된 에셋을 감지하고 보고하는 기능.
