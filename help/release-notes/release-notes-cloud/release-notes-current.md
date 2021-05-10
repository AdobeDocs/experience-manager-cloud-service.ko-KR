---
title: Cloud Service으로 [!DNL Adobe Experience Manager] 에 대한 현재 릴리스 노트입니다.
description: Cloud Service으로 [!DNL Adobe Experience Manager] 에 대한 현재 릴리스 노트입니다.
exl-id: a2d56721-502c-4f4e-9b72-5ca790df75c5
translation-type: tm+mt
source-git-commit: 8ca3fe045aba4ec9e546fee0700d1bec08e337fb
workflow-type: tm+mt
source-wordcount: '1879'
ht-degree: 2%

---


# [!DNL Adobe Experience Manager] Cloud Service {#release-notes}의 현재 릴리스 노트

다음 섹션에서는 Cloud Service의 현재(최신) 버전 [!DNL Experience Manager]에 대한 일반적인 릴리스 노트에 대해 간략하게 설명합니다.

>[!NOTE]
>여기에서 이전 버전의 릴리스 노트를 탐색할 수 있습니다.예를 들어, 2020, 2021 등에 있는 경우

>[!NOTE]
>
>릴리스와 직접 관련이 없는 설명서 업데이트에 대한 자세한 내용은 [최근 설명서 업데이트](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html)를 참조하십시오.

## 릴리스 날짜 {#release-date}

Cloud Service으로 [!DNL Adobe Experience Manager]에 대한 릴리스 날짜는 2021년 5월 6일입니다.
다음 릴리스(2021.5.0)은 2021년 5월 27일에 제공됩니다.

## AEM을 Cloud Service 기반{#aem-as-a-cloud-service-foundation}

### 새로운 기능 {#what-is-new-foundation}

* [컨텐츠 트리 게시 워크플로우](/help/operations/replication.md#publish-content-tree-workflow)  - 새로운 워크플로우 모델 및 단계에서는 컨텐츠 계층 구조를 게시할 때 향상된 성능을 제공합니다.

## [!DNL Cloud Service]로서의 [!DNL Adobe Experience Manager Sites] {#sites}

### [!DNL Sites] {#what-is-new-sites}의 새로운 기능

* GraphQL 끝점 - 이제 개별 AEM Sites 구성에 대해 AEM GraphQL API를 활성화하고 새 GraphQL 콘솔 UI를 사용하여 해당 구성에 대한 사용자 정의 GraphQL 끝점을 만들 수 있습니다. 또한 UI에서 GraphQL 끝점을 관리할 수 있습니다.

* 컨텐츠 모델, 향상된 날짜 및 시간 데이터 유형 - 이제 작성 일자, 시간 또는 날짜 및 시간 정보만 허용하도록 날짜 및 시간 날짜 유형을 구성할 수 있습니다.

* 컨텐츠 모델, 향상된 태그 데이터 유형 - 이제 태그 데이터 유형을 구성하여 단일 또는 여러 태그를 작성할 수 있습니다.

* 컨텐츠 모델, 새 탭 자리 표시자 데이터 유형 - 새로운 탭 자리 표시자 데이터 유형을 사용하면 컨텐츠 조각 편집기에서 탭 아래에 렌더링되는 섹션으로 데이터 유형을 그룹화할 수 있습니다.

### [!DNL Sites] {#bug-fixes-sites}의 버그 수정

* 컨텐츠 조각 - 이제 컨텐츠 조각 또는 폴더를 이동하면 조각 내의 중첩된 참조가 업데이트됩니다(CQ-4320815).

* GraphQL - 지속적인 쿼리는 이제 AEM Sites 구성에만 적용되는 사용자 정의 끝점을 지원합니다(CQ-4315928).

## [!DNL Cloud Service]로서의 [!DNL Adobe Experience Manager Assets] {#assets}

### [!DNL Assets] {#what-is-new-assets}의 새로운 기능

* [!DNL Experience Manager] 은 원본 파일이 다운로드된 위치에서 단일 자산 다운로드를 보관하지 않습니다. 이러한 향상된 기능을 통해 보다 신속하게 다운로드할 수 있습니다.

* 링크 공유 옵션을 통해 에셋을 다운로드할 때 이제 변환을 다운로드할지 여부를 선택할 수 있습니다. 이전에는 모든 자산 변환이 다운로드되었습니다.

* 관리자는 일괄 자산 처리를 수행한 후 [!DNL Experience Manager]이(가) 자산의 소스를 삭제하도록 구성할 수 있습니다. [일괄 자산 통합](/help/assets/add-assets.md#asset-bulk-ingestor)을 참조하십시오.

* 상태 검사를 실행하여 자산을 일괄적으로 가져올 때 이제 Experience Manager에서 실패 이유를 자세히 제공합니다. [일괄 자산 통합](/help/assets/add-assets.md#asset-bulk-ingestor)을 참조하십시오.

* 벌크 가져오기 도구를 사용하여 에셋을 가져올 때 이제 관리자는 가져오기가 성공한 후 소스 파일을 삭제할 수 있습니다. [일괄 자산 통합](/help/assets/add-assets.md#asset-bulk-ingestor)을 참조하십시오.

* 메타데이터 스키마를 편집할 때 새 루트 경로 선택기 필드를 사용하면 관리자가 빠르고 쉽게 선택할 수 있으므로 구성 시간이 줄어듭니다.

* 많은 자산의 메타데이터를 CSV 파일을 사용하여 일괄 가져올 수 있으며 CSV 파일로 내보낼 수 있습니다. 기본 날짜 형식은 이제 `yyyy-MM-dd'T'HH:mm:ss.SSSXXX`입니다. 사용자는 열 헤더를 업데이트하여 다른 형식을 활용할 수 있습니다. 예를 들어 `Date` 단어 대신 CSV 파일의 열 머리글로 `Date: DateFormat: yyyy-MM-dd'T'HH:mm:ssXXX`을 추가합니다.

* 열 보기에서 자산을 검색할 때 시각적 표시기에 각 자산의 승인됨 또는 거부됨 상태가 표시됩니다.

* 열 보기에서 자산을 검색할 때 만료된 자산에 대한 시각적 표시기가 표시됩니다.

### [!DNL Assets] {#bug-fixes-assets}의 버그 수정

* 여러 자산이나 폴더를 이동하려고 하면 콘솔에 오류가 기록되고 이동 작업이 완료되지 않습니다. 제목을 업데이트할 수 없는 경우 이동 작업이 실패합니다. (CQ-4322080)

* 사전 정의된 조건이 충족되면 메타데이터가 필수가 되지 않는 규칙을 기반으로 메타데이터 필드를 숨길 수 있습니다. 그러나 이러한 숨겨진 메타데이터 필드는 필수 필드로 표시됩니다. (CQ-4321285)

* 날짜 형식이 잘못되어 일괄 메타데이터 가져오기에 실패했습니다. (CQ-4319014)

* 속성 페이지에서 메타데이터를 업데이트하기 위해 선택하면 스키마에서 제공하는 옵션이 많을 때 인터페이스가 응답하는 속도가 느려집니다. (CQ-4318538)

* 단일 행 텍스트 필드에서 메타데이터 값을 업데이트하고 저장하는 동안 드롭다운 메뉴에서 편집을 비활성화하더라도 드롭다운 메뉴의 값이 삭제됩니다. (CQ-4317077)

* 줄임표를 주석으로 사용하여 자산을 검토할 수 있습니다. 작은 타원을 사용하면 타원이 인쇄 버전의 주석 수와 겹칩니다. (CQ-4316792)

## [!DNL Cloud Service]로서의 [!DNL Adobe Experience Manager Forms] {#forms}

### [!DNL Forms] {#what-is-new-forms}의 새로운 기능

[AEM Forms을 Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-forms-cloud-service/forms/home.html)으로 사용하여 디지털 양식을 만들고, 양식을 기존 데이터 소스에 연결하고, 양식을 Adobe Sign과 통합하여 양식에 전자 서명을 추가하고, 문서 기록(DoR)을 생성하여 제출된 양식을 PDF 파일로 보관할 수 있습니다. 또한 서비스는 기존 PDF forms을 디지털 양식으로 변환할 수 있습니다. 표준 AEM Forms 기능 외에도 자동 크기 조절, 업그레이드 중단 시간 제로, 클라우드 기본 개발 환경과 같은 클라우드 기본 기능을 제공합니다. Cloud Service의 AEM Forms 기능 및 기능에 대해 알아보려면 [이 블로그 게시물](https://blog.adobe.com/en/publish/2021/03/11/experience-manager-forms-as-a-cloud-service.html)을 읽어 보십시오.

* **Adaptive Forms이 활성화된 Adobe Sign에서 정부 기관 ID 인증 방법 사용**

   고급 머신 러닝 알고리즘을 기반으로 하는 Adobe Sign의 공공 기관 ID 프로세스를 통해 전 세계 기업은 수신자의 ID에 대한 고품질 인증을 받을 수 있습니다. 이제 Adobe Sign이 활성화된 응용 Forms에서 정부 기관 ID 인증 방법을 사용할 수 있습니다.

   정부 ID는 수신자에게 [정부 발급 ID 문서(운전면허증, 국민 ID, 여권)](https://helpx.adobe.com/in/sign/using/adobesign-authentication-government-id.html)의 이미지를 업로드하도록 지시한 다음 해당 문서를 인증하도록 평가하는 프리미엄 ID 인증 방법입니다.

* **비동기 적응형 양식 제출을 위한 양식 서명 경험 사용 지원**

   이제 비동기 적응형 양식 제출을 위해 양식 서명 환경을 사용할 수 있습니다. 적응형 양식을 [!DNL Experience Manager Sites] 페이지에 포함하고 적응형 양식 제출을 위해 양식 서명 환경을 사용할 수도 있습니다.

* **지정 작업 단계에 대해 적응형 양식을 미리 채우는 동안 변수를 사용하여 첨부 파일을 지정하는 지원**

   이제 작업 할당 단계에 적응형 양식을 미리 채우는 동안 문서 유형 변수를 사용하여 적응형 양식의 입력 첨부를 선택할 수 있습니다.

* **문자 옵션을 사용하여 JSON 유형 변수의 값을 설정할 수 있도록 지원**

   문자 옵션을 사용하여 AEM Workflow의 설정 변수 단계에서 JSON 유형 변수의 값을 설정할 수 있습니다. 문자 옵션을 사용하면 문자열 형태로 JSON을 지정할 수 있습니다.

* **로컬 개발 환경을 사용하여 기록 문서(DoR) 만들기**

   XDP를 Cloud Service 인스턴스에 대한 기록 문서로 사용하고 AEM Forms을 Cloud Service SDK(로컬 개발 환경)로 사용할 수 있습니다. 이전에는 지원 범위가 Cloud Service 인스턴스로만 제한되었습니다.

### [!DNL Forms] {#bug-fixes-forms}의 버그 수정

* 기록 문서를 생성하지 않도록 구성된 적응형 양식이 기록 문서를 생성하도록 구성된 AEM 워크플로우에 제출되면 오류 메시지가 표시되지 않고 작업을 제출하지 못합니다.

### 기타 업데이트 {#misc-2021-04-0-forms}

* 이제 서비스에서 내용을 쉽게 인식할 수 있도록 XDP, Dynamic PDF 및 스키마 파일에 대한 실시간 축소판을 생성합니다.
* AEM Forms UI에 있는 폴더로 PDF 파일을 이동하는 기능을 추가할 수 있습니다.

## Adobe Experience Manager 상거래를 Cloud Service {#cloud-services-commerce}

### 새로운 기능 {#what-is-new-commerce}

* 카테고리 UID 지원 - 범주 ID에 문자열을 사용하는 시스템의 타사 상거래 통합을 해제합니다.

* PWA Studio용 AEM 확장 포함 예제 통합

* WCM 탐색 핵심 구성 요소를 확장하는 새로운 CIF 탐색 핵심 구성 요소

* AEM 스토어전선의 스테이지된 카탈로그 데이터에 대한 시각적 표시기

* 이제 Cloud Manager UI를 통해 상거래 끝점을 구성할 수 있습니다.

### 버그 수정 {#bug-fixes-commerce}

* 카테고리 페이지의 페이지 속성에 있는 상거래 탭 아래에 루트 카테고리 필드가 표시되지 않았습니다.


## Cloud Manager {#cloud-manager}

이 섹션에서는 AEM의 Cloud Manager 릴리스 노트를 Cloud Service 2021.5.0 및 2021.4.0으로 간략하게 설명합니다.

### 릴리스 날짜 {#release-date-cm-may}

AEM의 Cloud Service 2021.5.0 Cloud Manager에 대한 릴리스 날짜는 2021년 5월 6일입니다.
다음 릴리스는 2021년 6월 3일에 예정되어 있습니다.

### 새로운 기능 {#what-is-new-may}

* 이제 PackageOverlaps 품질 규칙은 동일한 패키지가 동일한 배포된 패키지 세트에서 여러 위치(예: 여러 포함된 위치)에 여러 번 배포된 경우를 검색합니다.

* 이제 공개 API의 리포지토리 끝점에 Git URL이 포함됩니다.

* Cloud Manager 사용자가 다운로드한 배포 로그는 더 알아보기 쉬워졌으며 이제 오류 및 성공 시나리오에 대한 세부 정보를 포함합니다.

* 코드를 Adobe git으로 푸시하는 동안 가끔씩 발생하는 오류가 해결되었습니다.

* 이제 코드 추가 기능은 편집 프로그램 워크플로우 동안 샌드박스 프로그램에 적용할 수 있습니다.

* 편집 프로그램 환경이 새로 고침되었습니다.

* 환경 세부 사항 페이지의 도메인 이름 테이블에는 페이지 매김을 통해 최대 250개의 도메인 이름이 표시됩니다.

* 프로그램 추가 및 프로그램 편집 워크플로우에 있는 솔루션 탭은 솔루션에 대해 하나만 사용할 수 있는 경우에도 솔루션을 표시합니다.

* 빌드에서 배포된 콘텐츠 패키지를 생성하지 않았을 때의 빌드 단계 로그의 오류 메시지가 명확하지 않았습니다.

### 버그 수정 {#bug-fixes-cm-may}

* IP 허용 목록 옆에 해당 구성이 배포되지 않았더라도 녹색 &quot;활성&quot; 상태가 표시될 수 있습니다.

* &#39;deleted&#39; 변수를 제거하는 대신 파이프라인 변수 API는 **DELETED** 상태로만 표시합니다.

* 일부 코드 후각 유형 품질 문제가 안정성 등급에 잘못 영향을 주었습니다.

* 와일드카드 도메인은 지원되지 않으므로 UI는 사용자가 와일드카드 도메인을 제출하지 못하도록 합니다.

* 자정~오전 1시 UTC 사이에 파이프라인 실행이 시작되었을 때 Cloud Manager에서 생성된 아티팩트 버전이 전날 생성된 버전보다 클 것으로 보장되지 않았습니다.

* 샌드박스 프로그램 설정 중에 샘플 코드가 있는 프로젝트가 성공적으로 만들어지면 개요 페이지에 메인 카드의 링크로 Git 관리가 표시됩니다.

### 릴리스 날짜 {#release-date-cm-april}

Cloud Service 2021.4.0인 AEM의 Cloud Manager에 대한 릴리스 날짜는 2021년 4월 08일입니다.

### 새로운 기능 {#what-is-new-april}

* 프로그램 추가 및 편집 워크플로우에 대한 UI 업데이트를 통해 보다 직관적으로 만들 수 있습니다.

* 이제 필요한 권한을 가진 사용자는 UI를 통해 상거래 끝점을 제출할 수 있습니다.

* 이제 환경 변수의 범위가 작성자 또는 게시와 같은 특정 서비스로 지정될 수 있습니다. AEM 버전 `2021.03.5104.20210328T185548Z` 이상이 필요합니다.

* 파이프라인이 구성되지 않은 경우에도 **Git** 관리 단추가 파이프라인 카드에 표시됩니다.

* Cloud Manager에서 사용하는 AEM 프로젝트 원형 버전이 버전 27로 업데이트되었습니다.

* Cloud Manager에서 만든 Adobe I/O 개발자 콘솔의 프로젝트는 더 이상 의도치 않게 편집하거나 삭제할 수 없습니다.

* 사용자가 새 환경을 추가하면 환경을 만들면 다른 영역으로 이동할 수 없다는 메시지가 표시됩니다.

* 이제 환경 변수의 범위가 작성자 또는 게시와 같은 특정 서비스로 지정될 수 있습니다. AEM 버전 2021.03.5104.20210328T185548Z 이상이 필요합니다.

* 환경이 삭제되었을 때 파이프라인을 시작할 때의 오류 메시지가 명확해졌습니다.

* 이제 Eclipse 프로젝트에서 제공하는 OSGi 번들은 규칙 `CQBP-84--dependencies`에서 제외됩니다.

### 버그 수정 {#bug-fixes-cm-april}

* 파이프라인의 경험 감사 페이지를 편집할 때 슬래시(`( / )`)로 시작하는 입력 경로가 더 이상 보류 중인 상태로 돌아가지 않습니다.

* 새 프로덕션 파이프라인이 생성되면 사용자가 컨텐츠 감사 재정의를 추가하지 않은 경우 기본 홈 페이지가 감사되지 않았습니다.

* 다운로드 가능한 문제 CSV 파일에서 `CloudServiceIncompatibleWorkflowProcess` 문제의 심각도가 잘못되었습니다.

* `Runmode` 검사가 비폴더 노드에서 잘못된 양수를 생성하고 있었습니다.

## 우수 사례 분석기 {#best-practices-analyzer}

### 릴리스 날짜 {#release-date-bpa}

우수 사례 분석기 v2.1.12 릴리스 날짜는 2021년 4월 12일입니다.

### 버그 수정 {#bug-fixes-bpa-april}

* BPA에서 중복 행이 확인되었습니다. 이 문제가 수정되었습니다.
* AEM 버전 6.4.2의 BPA UI에서 [보고서 생성] 단추를 비활성화하는 JS 오류가 발생했습니다. 이 문제가 해결되었습니다.

