---
title: ' [!DNL Adobe Experience Manager] as a Cloud Service의 2021.4.0 릴리스 정보입니다.'
description: ' [!DNL Adobe Experience Manager] as a Cloud Service의 2021.4.0 릴리스 정보입니다.'
exl-id: 775332b5-24ce-430e-97a2-6eeb80877c64
source-git-commit: 1994b90e3876f03efa571a9ce65b9fb8b3c90ec4
workflow-type: tm+mt
source-wordcount: '1532'
ht-degree: 41%

---

# [!DNL Adobe Experience Manager] as a Cloud Service 최신 릴리스 정보 {#release-notes}

다음 섹션에서는 [!DNL Adobe Experience Manager] as a Cloud Service의 최신 버전 일반 릴리스 정보에 대해 간략히 소개합니다.

>[!NOTE]
>여기에서 2020, 2021 버전 등 이전 버전의 릴리스 정보로 이동할 수 있습니다.

>[!NOTE]
>
>릴리스와 직접적으로 관련되지 않는 설명서 업데이트의 세부 정보는 [설명서 업데이트](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html)를 참조하십시오.

## 릴리스 일자 {#release-date}

의 릴리스 날짜 [!DNL Adobe Experience Manager] as a Cloud Service 2021.4.0은 2021년 5월 6일입니다.
다음 릴리스(2021.5.0) 날짜는 2021년 5월 27일입니다.

## AEM as a Cloud Service Foundation{#aem-as-a-cloud-service-foundation}

### 새로운 기능 {#what-is-new-foundation}

* [콘텐츠 트리 워크플로 게시](/help/operations/replication.md#publish-content-tree-workflow) - 새로운 워크플로우 모델 및 단계는 깊은 계층의 콘텐츠를 게시할 때 향상된 성능을 제공합니다.

## [!DNL Adobe Experience Manager Sites] as a [!DNL Cloud Service] {#sites}

### [!DNL Sites]의 새로운 기능 {#what-is-new-sites}

* GraphQL 끝점 - 이제 개별 AEM Sites 구성에 대한 AEM GraphQL API를 활성화하고 새로운 GraphQL 콘솔 UI를 사용하여 해당 구성에 대한 사용자 지정 GraphQL 끝점을 만들 수 있습니다. UI를 통해 GraphQL 엔드포인트를 관리할 수도 있습니다.

* 콘텐츠 모델, 향상된 Date&amp;Time 데이터 유형 - 이제 Date&amp;Time 날짜 유형을 구성하여 날짜, 시간만 또는 날짜 및 시간 정보를 작성할 수 있습니다.

* 콘텐츠 모델, 향상된 태그 데이터 유형 - 이제 태그 데이터 유형을 구성하여 단일 또는 다중 태그를 작성할 수 있습니다.

* 콘텐츠 모델, 새로운 탭 자리 표시자 데이터 유형 - 새로운 탭 자리 표시자 데이터 유형을 사용하면 데이터 유형을 콘텐츠 조각 편집기의 탭 아래에 렌더링되는 섹션으로 그룹화할 수 있습니다.

### [!DNL Sites]에서 수정된 버그 {#bug-fixes-sites}

* 콘텐츠 조각 - 이제 콘텐츠 조각 또는 폴더를 이동하면 조각 내의 중첩된 참조가 업데이트됩니다(CQ-4320815)

* GraphQL - 이제 지속 쿼리가 AEM Sites 구성과 관련된 사용자 정의 끝점을 지원합니다(CQ-4315928)

## [!DNL Adobe Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### [!DNL Assets]의 새로운 기능 {#what-is-new-assets}

* [!DNL Experience Manager] 는 원본 파일이 다운로드된 단일 에셋 다운로드를 보관하지 않습니다. 이 향상된 기능을 통해 더 빠른 다운로드가 가능합니다.

* 이제 linkshare 옵션을 통해 에셋을 다운로드할 때 렌디션을 다운로드할지 여부를 선택할 수 있습니다. 이전에는 모든 에셋 렌디션이 다운로드되었습니다.

* 관리자는 을 구성할 수 있습니다 [!DNL Experience Manager] 일괄 에셋 수집을 수행한 후 에셋 소스를 삭제합니다. 다음을 참조하십시오 [일괄 에셋 수집](/help/assets/add-assets.md#asset-bulk-ingestor).

* 에셋을 일괄로 가져오기 위해 상태 검사를 실행할 때 이제 Experience Manager은 실패 이유에 대한 자세한 정보를 제공합니다. 다음을 참조하십시오 [일괄 에셋 수집](/help/assets/add-assets.md#asset-bulk-ingestor).

* 일괄 가져오기 도구를 사용하여 에셋을 가져올 때 관리자는 이제 가져오기가 완료된 후 소스 파일을 삭제할 수 있는 옵션이 있습니다. 다음을 참조하십시오 [일괄 에셋 수집](/help/assets/add-assets.md#asset-bulk-ingestor).

* 메타데이터 스키마를 편집할 때 새로운 루트 경로 선택기 필드를 사용하면 관리자가 빠르고 쉽게 선택할 수 있으므로 구성 시간이 단축됩니다.

* 메타데이터 스키마를 편집할 때 메타데이터 편집기에서 자유 형식 텍스트 영역을 제공하는 데이터 유형이 추가됩니다. 사용자는 이 텍스트 영역을 사용하여 자유 형식의 텍스트를 에셋의 메타데이터로 입력할 수 있습니다. 다음을 참조하십시오 [메타데이터 스키마 편집기](/help/assets/metadata-schemas.md).

* 많은 에셋의 메타데이터는 CSV 파일을 사용하여 일괄로 가져올 수 있으며 CSV 파일로 내보낼 수 있습니다. 이제 기본 날짜 형식은 입니다 `yyyy-MM-dd'T'HH:mm:ss.SSSXXX`. 사용자는 열 머리글을 업데이트하여 다른 형식을 사용할 수 있습니다. 예: 추가 `Date: DateFormat: yyyy-MM-dd'T'HH:mm:ssXXX` csv 파일의 열 머리글로 사용됩니다(단어 대신). `Date`.

* 열 보기에서 에셋을 검색할 때 시각적 표시기가 각 에셋의 승인 또는 거부 상태를 표시합니다.

* 열 보기에서 에셋을 검색할 때 만료된 에셋에 대한 시각적 표시기가 표시됩니다.

### [!DNL Assets]에서 수정된 버그 {#bug-fixes-assets}

* 여러 에셋 또는 폴더를 이동하려고 하면 콘솔에 오류가 기록되고 이동 작업이 완료되지 않습니다. 제목을 업데이트할 수 없으면 이동 작업이 실패합니다. (CQ-4322080)

* 규칙을 기반으로 메타데이터 필드를 숨길 수 있으므로 사전 정의된 조건이 충족될 경우 메타데이터는 필수가 아닙니다. 그러나 이러한 숨겨진 메타데이터 필드는 필수 필드로 표시됩니다. (CQ-4321285)

* 잘못된 날짜 형식으로 인해 벌크 메타데이터 가져오기에 실패합니다. (CQ-4319014)

* 속성 페이지에서 메타데이터를 업데이트하도록 선택한 경우 스키마에서 제공하는 옵션이 많으면 인터페이스가 느리게 응답합니다. (CQ-4318538)

* 한 줄 텍스트 필드에 메타데이터 값을 업데이트하고 저장하는 동안 드롭다운 메뉴에서 편집 기능이 비활성화된 경우에도 드롭다운 메뉴의 값이 삭제됩니다. (CQ-4317077)

* 줄임표를 주석으로 사용하여 에셋을 검토할 수 있습니다. 작은 타원을 사용하면 타원이 인쇄 버전의 주석 번호와 겹칩니다. (CQ-4316792)

* 빠른 게시 옵션은 자산을 검색한 후 검색 결과에서 선택한 경우 표시되지 않습니다. (CQ-4317748)

## [!DNL Adobe Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

### [!DNL Forms]의 새로운 기능 {#what-is-new-forms}

* **Adobe Sign이 활성화된 적응형 양식에서 정부 ID 신원 인증 방법 사용**

  고급 머신 러닝 알고리즘으로 더욱 강력해진 Adobe Sign의 정부 ID 프로세스는 고품질의 수령인 신원 인증을 확보할 수 있는 능력을 전 세계 기업에 제공합니다. 이제 Adobe Sign이 활성화된 적응형 양식에서 정부 ID 신원 인증 방법을 사용할 수 있습니다.

  정부 ID는 수신자에게 다음을 지시하는 프리미엄 신원 인증 방법입니다 [정부에서 발급한 신분증(운전면허증, 주민등록증, 여권) 이미지 업로드](https://helpx.adobe.com/in/sign/using/adobesign-authentication-government-id.html)를 누르고 해당 문서가 진짜인지 평가합니다.

* **비동기 적응형 양식 제출을 위한 양식 내 서명 경험 사용 지원**

  이제 비동기 적응형 양식 제출을 위해 양식 내 서명 환경을 사용할 수 있습니다. 또한 [!DNL Experience Manager Sites] 페이지에 적응형 양식을 임베드하고 적응형 양식 제출을 위해 양식 내 서명 환경을 사용할 수 있습니다.

* **작업 할당 단계를 위해 적응형 양식을 미리 채우는 동안 변수를 사용하여 첨부 파일을 지정하도록 지원**

  이제 작업 할당 단계를 위해 적응형 양식을 미리 채우는 동안 문서 유형 변수를 사용하여 적응형 양식에 대한 입력 첨부 파일을 선택할 수 있습니다.

* **JSON 유형 변수에 대한 값을 설정하기 위해 리터럴 옵션을 사용하도록 지원**

  리터럴 옵션을 사용하여 AEM Workflow의 변수 설정 단계에서 JSON 유형 변수의 값을 설정할 수 있습니다. 리터럴 옵션을 사용하면 문자열 형식으로 JSON을 지정할 수 있습니다.

* **로컬 개발 환경을 사용하여 기록 문서(DoR) 생성**

  XDP를 클라우드 서비스 인스턴스와 AEM Forms as a Cloud Service SDK(로컬 개발 환경)에서 기록 문서 템플릿으로 사용할 수 있습니다. 이전에는 지원이 클라우드 서비스 인스턴스로만 제한되었습니다.

### [!DNL Forms]에서 수정된 버그 {#bug-fixes-forms}

* 기록 문서를 생성하도록 구성된 AEM Workflow에 기록 문서를 생성하지 않도록 구성된 적응형 양식을 제출하는 경우, 오류 메시지가 표시되지 않고 작업 제출이 실패합니다.

### 기타 업데이트 {#misc-2021-04-0-forms}

* 콘텐츠를 더 쉽게 인식할 수 있도록 이 서비스는 이제 XDP, 동적 PDF 및 스키마 파일에 대한 라이브 썸네일을 생성합니다.
* AEM Forms UI의에 배치된 폴더로 PDF 파일을 이동하는 기능을 추가합니다.

## Adobe Experience Manager Commerce as a Cloud Service {#cloud-services-commerce}

### 새로운 기능 {#what-is-new-commerce}

* 범주 UID 지원 - 범주 ID에 문자열을 사용하는 시스템에 대한 서드파티 상거래 통합을 잠금 해제합니다.

* PWA Studio에 대한 AEM 확장에는 다음이 포함됩니다. 통합 예

* WCM 탐색 핵심 구성 요소를 확장하는 새로운 CIF 탐색 핵심 구성 요소

* AEM 상점 첫 화면의 단계적 카탈로그 데이터에 대한 시각적 표시기

* 이제 상거래 끝점은 Cloud Manager UI를 통해 구성할 수 있습니다

### 버그 수정 {#bug-fixes-commerce}

* 범주 페이지의 페이지 속성에서 상거래 탭 아래에 루트 범주 필드가 표시되지 않았습니다

## Cloud Manager {#cloud-manager}

이 섹션에서는 AEM as a Cloud Service 2021.4.0의 Cloud Manager 릴리스 정보에 대해 간략히 소개합니다.

### 릴리스 일자 {#release-date-cm-april}

AEM as a Cloud Service 2021.4.0의 Cloud Manager 릴리스 일자는 2021년 4월 8일입니다.
다음 릴리스는 2021년 5월 6일에 예정되어 있습니다.

### 새로운 기능 {#what-is-new-april}

* 프로그램 추가 및 편집 워크플로가 보다 직관적으로 보일 수 있도록 UI가 업데이트됩니다.

* 필수 권한이 있는 사용자는 UI를 통해 상거래 엔드포인트를 제출할 수 있습니다.

* 이제 환경 변수는 특정 서비스인 작성자 또는 게시로 지정될 수 있습니다. AEM 버전 `2021.03.5104.20210328T185548Z` 이상이 필요합니다.

* 파이프라인이 구성되지 않아도 파이프라인 카드에 **Git 관리** 버튼이 표시됩니다.

* Cloud Manager에서 사용하는 AEM Project Archetype이 버전 27로 업데이트되었습니다.

* Cloud Manager에서 만든 Adobe I/O Developer Console의 프로젝트를 더 이상 의도하지 않게 편집하거나 삭제할 수 없습니다.

* 사용자가 새 환경을 추가하면 환경이 생성된 후 다른 지역으로 이동할 수 없다는 메시지가 표시됩니다.

* 이제 환경 변수는 특정 서비스인 작성자 또는 게시로 지정될 수 있습니다. AEM 버전 2021.03.5104.20210328T185548Z 이상이 필요합니다.

* 환경이 삭제되었을 때 파이프라인을 시작하는 경우 발생하는 오류 메시지가 명확해졌습니다.

* Eclipse 프로젝트에서 제공하는 OSGi 번들은 이제 `CQBP-84--dependencies` 규칙에서 제외됩니다.

### 버그 수정 {#bug-fixes-cm-april}

* 파이프라인의 경험 감사 페이지를 편집할 때 슬래시`( / )`로 시작하는 입력 경로로 인해 더 이상 단계가 보류 상태에서 멈추지 않습니다.

* 새 프로덕션 파이프라인이 생성될 때 사용자가 콘텐츠 감사 재정의를 추가하지 않으면 기본 홈 페이지가 감사되지 않았습니다.

* 다운로드 가능한 문제 CSV 파일에서 `CloudServiceIncompatibleWorkflowProcess`에 대한 문제의 심각도가 잘못되었습니다.

* `Runmode` 검사 중 폴더가 아닌 노드에서 오탐지가 생성되었습니다.

## Best Practices Analyzer {#best-practices-analyzer}

### 릴리스 날짜 {#release-date-bpa}

모범 사례 분석기 v2.1.12의 릴리스 날짜는 2021년 4월 12일입니다.

### 버그 수정 {#bug-fixes-bpa-april}

* 보고된 BPA에서 중복 행이 발견되었습니다. 이 문제가 해결되었습니다.
* AEM 버전 6.4.2의 BPA UI에서 보고서 생성 버튼을 비활성화하는 JS 오류가 발생했습니다. 이 문제가 해결되었습니다
