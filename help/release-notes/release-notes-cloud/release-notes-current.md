---
title: 의 현재 릴리스 노트 [!DNL Adobe Experience Manager] as a Cloud Service.
description: 의 현재 릴리스 노트 [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: a2d56721-502c-4f4e-9b72-5ca790df75c5
mini-toc-levels: 1
source-git-commit: a0bf314ff8f994dd77c2c124db1ab604dcae74b6
workflow-type: tm+mt
source-wordcount: '1435'
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

의 릴리스 날짜 [!DNL Adobe Experience Manager] 로서의 [!DNL Cloud Service] 현재 릴리스(2021.10.0)은 2021년 11월 4일입니다.
다음 릴리스(2021.11.0)은 2021년 12월 2일입니다.

## 릴리스 비디오 {#release-video}

을(를) 보십시오. [2021년 10월 릴리스 개요](https://video.tv.adobe.com/v/338253) 비디오 를 참조하십시오.

## [!DNL Experience Manager Sites] as a [!DNL Cloud Service] {#sites}

### 의 새로운 기능 [!DNL Sites] {#sites-features}

* 이제 컨텐츠 조각 모델은 게시된 후 읽기 전용 상태로 자동 설정되므로, 편집된 모델을 다시 게시한 후 라이브 API 쿼리를 일시적으로 중단하지 않습니다. 게시된 모델을 편집하려고 하면 사용자에게 경고가 표시됩니다. 경고를 수락하면 편집할 수 있습니다.

## [!DNL Experience Manager Assets] 로서의 [!DNL Cloud Service] {#assets}

### 의 새로운 기능 [!DNL Assets] {#assets-features}

* [!DNL Experience Manager] 에서는 이제 지원되는 오디오 및 비디오 자산에서 텍스트 스크립트를 자동으로 생성할 수 있도록 기본 제공 커넥터를 사용합니다. [!DNL Azure Media Services]. 지원되는 파일은 자동으로 전사되며 텍스트는 WebVTT 형식으로 저장됩니다. WebVTT 캡션은 보다 효과적인 검색, 캡션 또는 번역을 위해 사용됩니다. 또한 이 기능은 자산의 액세스 가능성, 검색 가능성 및 현지화를 개선합니다.

### 의 새로운 기능 [!DNL Assets] 사전 릴리스 채널 {#assets-prerelease-features}

* [!DNL Dynamic Media] 이제 이미지 스마트 자르기 및 색상 견본을 최신 Sensei 서비스에서 제공하며 향상된 자르기 및 색상 견본을 생성합니다. 또한 동일한 종횡비이지만 다양한 해상도에서 서로 다른 자르기 콘텐츠를 생성하기 위한 개선 사항을 시작했습니다. 또한 이미지 프로필의 폭과 높이가 변경되지 않은 경우 수동 편집 내용은 재처리 시 유지됩니다.

* 스마트 태그는 스마트 컨텐츠 서비스 대신 자산 마이크로서비스를 사용하여 자산에 자동으로 적용됩니다. 기본 모델이 업데이트되어 태깅 결과를 개선하고 바이어스를 줄일 수 있습니다. <!-- As it uses asset microservices, it is now possible to develop custom workers using Stock10-based Smart Tags. -->

<!-- Leave this commented.
### Bugs fixed in [!DNL Assets] {#assets-bugs-fixed}

No customer-reported bugs fixed in Oct release. Details in CQDOC-18404.
-->

## [!DNL Experience Manager Forms] 로서의 [!DNL Cloud Service] {#forms}

### 의 새로운 기능 [!DNL Forms] {#what-is-new-forms-oct-2021}

* **응용 Forms용 Analytics**: 이제 Adaptive Forms을 통해 Adobe Analytics을 통해 로그인된 사용자와 로그인하지 않은(익명) 모두의 동작을 캡처하고 추적하여 최종 사용자 통찰력을 얻을 수 있습니다. 최종 사용자 경험을 향상시키기 위해 데이터를 기반으로 현명한 결정을 내릴 수 있습니다.

### 에서 사용할 수 있는 새로운 기능 [!DNL Forms] 사전 릴리스 채널 {#prerelease-features-forms-oct-2021}

* **보안 처리를 위한 AEM 워크플로우 데이터 표면화**: 안전한 처리를 위해 고객 관리 저장소에 민감한 개인 데이터(SPD) 요소를 포함하는 처리 중인 AEM 워크플로우 데이터(AEM Workflow Variables 데이터)를 저장할 수 있습니다. 데이터 요소와 워크플로우 변수는 AEM 저장소에 저장되지 않으며 워크플로우를 처리하는 동안 고객 관리 저장소에서 주문형 가져옵니다.

### 의 베타 기능 [!DNL Forms] {#what-is-new-forms-oct2021-beta}

* **[!DNL AEM Forms as a Cloud Service - Communications]**: [통신 API](https://experienceleague.adobe.com/docs/experience-manager-forms-cloud-service/forms/using-communications/aem-forms-cloud-service-communications.html) 서식 파일과 XML 데이터를 결합하여 인쇄 문서를 다양한 형식으로 생성하는 데 도움이 됩니다. 이 서비스를 사용하면 문서를 동기식과 배치 모드로 생성할 수 있습니다. API를 사용하면 다음을 수행할 수 있는 애플리케이션을 만들 수 있습니다.

   * XML 데이터로 템플릿 파일(PDF 및 XDP)을 채워서 문서를 생성합니다.
   * 비대화형 PDF 인쇄 스트림을 포함하여 다양한 형식으로 출력 양식을 생성합니다.

에 쓸 수 있습니다. [!DNL formscsbeta@adobe.com] 베타 프로그램에 등록하려면

## CIF 추가 기능 {#cloud-services-cif}

### 새로운 기능 {#what-is-new-cif}

* CIF 추가 기능은 새로운 GraphQL API 및 스키마를 사용하여 최신 Commerce v2.4.3을 지원합니다

* 작성자는 리치 텍스트 편집기(RTE)를 사용하여 텍스트 필드에 제품 및 카탈로그 페이지에 대한 링크를 추가할 수 있습니다. CIF 아이콘이 RTE 도구 모음에 추가되어 컨텍스트를 종료하지 않고 제품이나 카테고리를 빠르게 검색하고 선택할 수 있는 선택기가 열립니다.

* 기존 팝업 장바구니 및 체크아웃이 전용 AEM 장바구니 및 체크아웃 페이지로 대체되었습니다. 이러한 페이지의 구성 요소는 Magento의 확장 가능한 상위 구성 요소를 사용하여 만들어집니다

* 상인은 상거래 백엔드를 사용하여 탐색에서 특정 제품 카탈로그 카테고리를 숨길 수 있습니다. CIF 탐색 코어 구성 요소는 탐색에서 카테고리를 표시하거나 숨기기 위해 상거래 백엔드 구성 &quot;include in menu&quot;를 따릅니다

* 카테고리 또는 제품 페이지를 찾을 수 없는 경우 AEM Storefront Venia에서 HTTP 404 오류를 반환합니다

## Cloud Manager {#cloud-manager}

이 섹션에서는 AEM as a Cloud Service에서 Cloud Manager에 대한 릴리스 노트를 간략하게 설명합니다.

### 릴리스 날짜 {#release-date-cm-nov}

AEM as a Cloud Service 2021.11.0의 Cloud Manager 릴리스 날짜는 2021년 11월 4일입니다.
다음 릴리스는 2021년 12월 9일에 예정되어 있습니다.

### 새로운 기능 {#what-is-new-cm-nov}

* 이제 사용자는 새로운 프런트 엔드 파이프라인을 활용하여 프런트 엔드 코드만 신속하게 배포할 수 있습니다. 자세한 내용은 [Cloud Manager 프런트엔드 파이프라인](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md#front-end) 추가 정보

   >[!IMPORTANT]
   >AEM 버전을 사용해야 합니다. `2021.10.5933.20211012T154732Z` 최신 프런트 엔드 파이프라인을 활용합니다.

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


## 릴리스 날짜 {#release-date-cm-oct}

AEM as a Cloud Service 2021.10.0의 Cloud Manager 릴리스 날짜는 2021년 10월 14일입니다.

### 새로운 기능 {#what-is-new-cm-oct}

* 향후 몇 가지 변경 사항에 대비하기 위해 기존 배포 파이프라인은 이제 사용자 인터페이스에서 다음과 같이 참조되고 레이블이 지정됩니다. **전체 스택** 파이프라인.

* 이제 파이프라인 카드가 새로 고쳐져서 프로덕션 파이프라인과 비프로덕션 파이프라인을 모두 표시하는 통합된 단일 면을 표시할 수 있으며, 사용자는 각 파이프라인과 연관된 작업 메뉴에서 직접 실행/일시 중지/재개 를 선택할 수 있습니다.

* 이제 배포 관리자 역할의 사용자는 UI를 통해 셀프 서비스 방식으로 프로덕션 파이프라인을 삭제할 수 있습니다.

* 이제 익숙하고 현대적인 모듈을 사용할 수 있도록 파이프라인 경험을 추가 및 편집할 수 있습니다.

* 이제 Cloud Manager 사용자는 **피드백** 랜딩 페이지의 오른쪽 위에 있는 단추.

* 이제 Cloud Manager의 사용자 인터페이스에서 연간 SLA 그래프를 다운로드할 수 있습니다.

* 이제 코드 품질 및 비프로덕션 파이프라인 실행에서는 빌드 단계에서 보다 효율적인 약식 복제 프로세스를 사용하므로 고객이 특히 큰 git 저장소를 사용하는 경우 빌드 시간이 빨라집니다.

* 이제 IP 허용 목록 추가 마법사가 허용된 최대 IP 허용 목록 수에 도달했는지 사용자에게 알려줍니다.

* 이제 Cloud Manager API 설명서에는 로그인한 사용자가 브라우저에서 API를 실험할 수 있도록 해주는 대화형 필드가 포함되어 있습니다. 자세한 내용은 [Cloud Manager API 놀이터](https://www.adobe.io/experience-cloud/cloud-manager/reference/playground/) 자세한 내용

* &#39;탐색 대상&#39; 아래의 선택 옵션이 비활성화되어 있으면 프로그램 카드의 도구 설명이 더 설명적입니다. 이제 &quot;프로덕션 환경이 없습니다.&quot;가 표시됩니다.

### 버그 수정 {#bug-fixes-cm-oct}

* 드문 경우이지만, Adobe 직원이 고객의 환경을 복원할 경우 환경이 완전히 작동하기 전에 복구가 완료된 것으로 간주됩니다.

* 환경을 만드는 동안 수행된 특정 내부 요청이 다시 시도되지 않았습니다.

* 도메인 이름 확인 후 배포 실패 오류가 발생하면 고객이 Adobe 담당자에게 문의하도록 오류 메시지가 수정되었습니다.

## 모범 사례 분석기 {#best-practices-analyzer}

### 릴리스 날짜 {#release-date-bpa-latest}

Best Practices Analyzer v2.1.20 릴리스 날짜는 2021년 10월 5일입니다.

### 새로운 기능 {#what-is-new}

* 노드 이름 길이를 감지하고 보고할 수 있습니다.

* 총 인덱스 크기를 감지하고 보고하는 기능.

* 원래 표현물이 누락된 자산을 검색하고 보고하는 기능.
