---
title: ' [!DNL Adobe Experience Manager] as a Cloud Service 2021.4.0 릴리스의 릴리스 노트'
description: ' [!DNL Adobe Experience Manager] as a Cloud Service 2021.4.0 릴리스의 릴리스 노트'
exl-id: a2d56721-502c-4f4e-9b72-5ca790df75c5
source-git-commit: e3540331e3194dce5dcd88e4f785f15ef682f062
workflow-type: tm+mt
source-wordcount: '1535'
ht-degree: 3%

---


# [!DNL Adobe Experience Manager] Cloud Service의 현재 릴리스 노트 {#release-notes}

다음 섹션에서는 Cloud Service으로 현재(최신) 버전의 [!DNL Experience Manager]에 대한 일반 릴리스 노트를 간략하게 설명합니다.

>[!NOTE]
>여기에서 이전 버전의 릴리스 정보로 이동할 수 있습니다. 예를 들어, 2020년, 2021년 등의 경우입니다.

>[!NOTE]
>
>릴리스와 직접 관련이 없는 설명서 업데이트에 대한 자세한 내용은 [최근 설명서 업데이트](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html)를 참조하십시오.

## 릴리스 날짜 {#release-date}

Cloud Service 2021.4.0으로서 [!DNL Adobe Experience Manager]의 출시일은 2021년 5월 6일입니다.
다음 릴리스(2021.5.0)는 2021년 5월 27일에 제공됩니다.

## AEM as a Cloud Service 기반{#aem-as-a-cloud-service-foundation}

### 새로운 기능 {#what-is-new-foundation}

* [컨텐츠 트리 게시 워크플로우](/help/operations/replication.md#publish-content-tree-workflow)  - 새로운 워크플로우 모델 및 단계는 컨텐츠 계층 구조를 게시할 때 향상된 성능을 제공합니다.

## [!DNL Adobe Experience Manager Sites]로서의 [!DNL Cloud Service]  {#sites}

### [!DNL Sites]의 새로운 기능 {#what-is-new-sites}

* GraphQL 엔드포인트 - 이제 개별 AEM Sites 구성에 대해 AEM GraphQL API를 활성화하고 새 GraphQL 콘솔 UI를 사용하여 해당 구성에 대한 사용자 지정 GraphQL 엔드포인트를 만들 수 있습니다. 또한 UI에서 GraphQL 엔드포인트를 관리할 수 있습니다.

* 컨텐츠 모델, 향상된 날짜 및 시간 데이터 유형 - 이제 날짜 및 시간 날짜 유형만 작성하여 날짜, 시간 또는 날짜 및 시간 정보만 작성할 수 있도록 구성할 수 있습니다.

* 컨텐츠 모델, 향상된 태그 데이터 유형 - 이제 태그 데이터 유형을 구성하여 단일 또는 여러 태그를 작성할 수 있습니다.

* 컨텐츠 모델, 새 탭 자리 표시자 데이터 유형 - 새 탭 자리 표시자 데이터 유형을 컨텐츠 조각 편집기에서 탭 아래에 렌더링될 섹션으로 그룹화할 수 있습니다.

### [!DNL Sites]의 버그 수정 {#bug-fixes-sites}

* 컨텐츠 조각 - 이제 컨텐츠 조각 또는 폴더를 이동하면 조각 내의 중첩된 참조가 업데이트됩니다(CQ-4320815)

* GraphQL - 지속된 쿼리는 이제 AEM Sites 구성에만 적용되는 사용자 정의 종단점을 지원합니다(CQ-4315928)

## [!DNL Adobe Experience Manager Assets]로서의 [!DNL Cloud Service]  {#assets}

### [!DNL Assets]의 새로운 기능 {#what-is-new-assets}

* [!DNL Experience Manager] 원본 파일이 다운로드되는 단일 자산 다운로드를 보관하지 않습니다. 이 개선 사항을 통해 더 빨리 다운로드할 수 있습니다.

* linkshare 옵션을 통해 자산이 다운로드되면 이제 변환을 다운로드하도록 선택하거나 다운로드하지 않도록 선택할 수 있습니다. 이전에는 모든 자산 표현물이 다운로드되었습니다.

* 관리자는 벌크 자산 처리를 수행한 후 자산의 소스를 삭제하도록 [!DNL Experience Manager]을 구성할 수 있습니다. [일괄 자산 수집](/help/assets/add-assets.md#asset-bulk-ingestor)을 참조하십시오.

* 상태 검사를 실행하여 자산을 일괄적으로 가져올 때 이제 Experience Manager에서 실패 이유에 대한 자세한 정보를 제공합니다. [일괄 자산 수집](/help/assets/add-assets.md#asset-bulk-ingestor)을 참조하십시오.

* 벌크 가져오기 도구를 사용하여 자산을 가져올 때 이제 관리자는 가져오기가 성공하면 소스 파일을 삭제할 수 있습니다. [일괄 자산 수집](/help/assets/add-assets.md#asset-bulk-ingestor)을 참조하십시오.

* 메타데이터 스키마를 편집할 때 새로운 루트 경로 선택기 필드를 사용하면 관리자가 빠르고 쉽게 선택할 수 있으므로 구성 시간이 줄어듭니다.

* 메타데이터 스키마를 편집할 때 메타데이터 편집기에서 자유 형식 텍스트 영역을 제공하는 데이터 유형이 추가됩니다. 사용자는 이 텍스트 영역을 사용하여 자유 형식 텍스트를 자산의 메타데이터로 입력할 수 있습니다. [메타데이터 스키마 편집기](/help/assets/metadata-schemas.md)를 참조하십시오.

* 많은 자산의 메타데이터를 CSV 파일을 사용하여 일괄적으로 가져올 수 있으며 CSV 파일로 내보낼 수 있습니다. 기본 날짜 형식은 이제 `yyyy-MM-dd'T'HH:mm:ss.SSSXXX`입니다. 열 헤더를 업데이트하여 다른 형식을 활용할 수 있습니다. 예를 들어 `Date` 라는 단어 대신 CSV 파일의 열 헤더로 `Date: DateFormat: yyyy-MM-dd'T'HH:mm:ssXXX` 을 추가합니다.

* 열 보기에서 자산을 검색할 때 시각적 표시기에 각 자산의 승인 또는 거부 상태가 표시됩니다.

* 열 보기에서 자산을 검색할 때 만료된 자산에 대해 시각적 표시기가 표시됩니다.

### [!DNL Assets]의 버그 수정 {#bug-fixes-assets}

* 여러 자산 또는 폴더를 이동하려고 하면 콘솔에 오류가 기록되고 이동 작업이 완료되지 않습니다. 제목을 업데이트할 수 없으면 이동 작업이 실패합니다. (CQ-4322080)

* 사전 정의된 조건이 충족될 경우 메타데이터가 필수가 되지 않도록 규칙에 따라 메타데이터 필드를 숨길 수 있습니다. 그러나 이러한 숨겨진 메타데이터 필드는 필수 필드로 표시됩니다. (CQ-4321285)

* 잘못된 날짜 포맷으로 인해 대량 메타데이터 가져오기에 실패합니다. (CQ-4319014)

* 속성 페이지에서 메타데이터를 업데이트하도록 선택하면 스키마에 의해 제공되는 옵션이 많을 때 인터페이스가 느리게 응답합니다. (CQ-4318538)

* 단일 행 텍스트 필드에 메타데이터 값을 업데이트하고 저장하는 동안 드롭다운 메뉴에서 편집이 비활성화된 경우에도 드롭다운 메뉴의 값이 삭제됩니다. (CQ-4317077)

* 생략 부호를 주석으로 사용하여 자산을 검토할 수 있습니다. 작은 타원을 사용하면 타원이 인쇄 버전의 주석 수와 겹칩니다. (CQ-4316792)

* 자산을 검색한 후 검색 결과에서 자산을 선택하면 빠른 게시 옵션이 표시되지 않습니다. (CQ-4317748)

## [!DNL Adobe Experience Manager Forms]로서의 [!DNL Cloud Service]  {#forms}

### [!DNL Forms]의 새로운 기능 {#what-is-new-forms}

* **Adobe Sign에서 활성화된 응용 Forms에서 정부 ID 인증 방법 사용**

   고급 기계 학습 알고리즘을 기반으로 하는 Adobe Sign의 정부 ID 프로세스는 전 세계 기업을 대상으로 수신자의 ID에 대한 고품질 인증을 획득하는 기능을 제공합니다. 이제 Adobe Sign이 활성화된 적응형 Forms에서 정부 기관 ID 인증 방법을 사용할 수 있습니다.

   정부 ID는 수신자에게 [정부 발급 ID 문서(운전면허증, 국가 ID, passport)](https://helpx.adobe.com/in/sign/using/adobesign-authentication-government-id.html)의 이미지를 업로드하도록 지시하고, 해당 문서가 진짜인지 확인하기 위해 해당 문서를 평가하는 프리미엄 ID 인증 방법입니다.

* **비동기 적응형 양식 제출을 위해 양식 서명 환경을 사용하도록 지원**

   이제 비동기 적응형 양식 제출에 양식 서명 경험을 사용할 수 있습니다. 적응형 양식을 [!DNL Experience Manager Sites] 페이지에 포함하고 적응형 양식 제출을 위해 양식 서명 경험을 사용할 수도 있습니다.

* **작업 할당 단계에서 적응형 양식을 미리 채우는 동안 변수를 사용하여 첨부 파일을 지정할 수 있도록 지원합니다**

   작업 지정 단계에 대해 적응형 양식을 미리 채우는 동안 이제 문서 유형 변수를 사용하여 적응형 양식에 대한 입력 첨부 파일을 선택할 수 있습니다.

* **리터럴 옵션을 사용하여 JSON 유형 변수에 대한 값을 설정할 수 있도록 지원합니다**

   AEM Workflow의 설정 변수 단계에서 리터럴 옵션을 사용하여 JSON 유형 변수의 값을 설정할 수 있습니다. 리터럴 옵션을 사용하면 문자열 형태로 JSON을 지정할 수 있습니다.

* **로컬 개발 환경을 사용하여 기록 문서(DoR) 작성**

   XDP를 Cloud Service 인스턴스에서 기록 문서로 사용하고 AEM Forms을 Cloud Service SDK(로컬 개발 환경)로 사용할 수 있습니다. 이전에는 지원이 Cloud Service 인스턴스로만 제한되었습니다.

### [!DNL Forms]의 버그 수정 {#bug-fixes-forms}

* 기록 문서를 생성하지 않도록 구성된 적응형 양식을 기록 문서를 생성하도록 구성된 AEM Workflow에 제출하면 오류 메시지가 표시되지 않고 작업을 제출할 수 없습니다.

### 기타 업데이트 {#misc-2021-04-0-forms}

* 컨텐츠를 더 쉽게 인식할 수 있도록 이제 서비스에서 XDP, Dynamic PDF 및 스키마 파일에 대한 라이브 축소판 그림을 생성합니다.
* PDF 파일을 AEM Forms UI에 배치된 폴더로 이동하는 기능을 추가합니다.

## Adobe Experience Manager Commerce as a Cloud Service {#cloud-services-commerce}

### 새로운 기능 {#what-is-new-commerce}

* 카테고리 UID 지원 - 카테고리 ID에 문자열을 사용하는 시스템에 대한 타사 상거래 통합을 잠금 해제합니다

* PWA Studio에 대한 AEM 확장 예제 통합

* WCM 탐색 코어 구성 요소를 확장하는 새 CIF 탐색 코어 구성 요소

* AEM storefront의 스테이지된 카탈로그 데이터에 대한 시각적 표시기

* 이제 Cloud Manager UI를 통해 상거래 종단점을 구성할 수 있습니다

### 버그 수정 {#bug-fixes-commerce}

* 카테고리 페이지의 페이지 속성에 있는 상거래 탭 아래에 루트 카테고리 필드가 표시되지 않았습니다

## Cloud Manager {#cloud-manager}

이 섹션에서는 AEM as a Cloud Service 2021.4.0에 있는 Cloud Manager 릴리스 노트를 간략하게 설명합니다.

### 릴리스 날짜 {#release-date-cm-april}

AEM as a Cloud Service 2021.4.0의 Cloud Manager 릴리스 날짜는 2021년 4월 8일입니다.
다음 릴리스는 2021년 5월 6일에 예정되어 있습니다.

### 새로운 기능 {#what-is-new-april}

* 프로그램 추가 및 편집 워크플로우에 대한 UI를 업데이트하여 보다 직관적으로 사용할 수 있습니다.

* 이제 필요한 권한이 있는 사용자는 UI를 통해 상거래 종료 지점을 제출할 수 있습니다.

* 이제 환경 변수 범위를 특정 서비스(작성자 또는 게시)로 지정할 수 있습니다. AEM 버전 `2021.03.5104.20210328T185548Z` 이상이 필요합니다.

* 파이프라인이 구성되지 않은 경우에도 **Git** 관리 단추가 파이프라인 카드에 표시됩니다.

* Cloud Manager에서 사용하는 AEM 프로젝트 원형 버전이 버전 27로 업데이트되었습니다.

* Cloud Manager에서 만든 Adobe I/O 개발자 콘솔의 프로젝트는 더 이상 실수로 편집하거나 삭제할 수 없습니다.

* 사용자가 새 환경을 추가하면 환경이 만들어지면 다른 지역으로 이동할 수 없다는 메시지가 표시됩니다.

* 이제 환경 변수 범위를 특정 서비스(작성자 또는 게시)로 지정할 수 있습니다. AEM 버전 2021.03.5104.20210328T185548Z 이상이 필요합니다.

* 환경이 삭제되었을 때 파이프라인을 시작할 때 오류 메시지가 명확해졌습니다.

* Eclipse 프로젝트에서 제공하는 OSGi 번들은 이제 규칙 `CQBP-84--dependencies`에서 제외됩니다.

### 버그 수정 {#bug-fixes-cm-april}

* 파이프라인의 경험 감사 페이지를 편집할 때 슬래시 `( / )`으로 시작하는 입력 경로는 더 이상 단계가 보류 중인 상태로 고정되지 않습니다.

* 새 프로덕션 파이프라인이 생성될 때 사용자가 컨텐츠 감사 무시를 추가하지 않으면 기본 홈 페이지가 감사되지 않습니다.

* 다운로드 가능한 문제 CSV 파일에서 `CloudServiceIncompatibleWorkflowProcess`에 대한 문제에 잘못된 심각도가 있었습니다.

* `Runmode` 검사에서 비폴더 노드에서 긍정 오류(false positive)가 발생했습니다.

## 모범 사례 분석기 {#best-practices-analyzer}

### 릴리스 날짜 {#release-date-bpa}

Best Practices Analyzer v2.1.12 릴리스 날짜는 2021년 4월 12일입니다.

### 버그 수정 {#bug-fixes-bpa-april}

* 보고된 BPA에 중복 행이 발견되었습니다. 이 문제가 수정되었습니다.
* AEM 버전 6.4.2의 BPA UI에서 보고서 생성 단추를 비활성화하는 JS 오류가 발생했습니다. 이 문제가 해결되었습니다

