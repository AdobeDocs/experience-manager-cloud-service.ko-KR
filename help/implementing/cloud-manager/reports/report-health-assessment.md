---
title: 프로덕션 및 스테이징 환경에 대한 상태 평가
description: Cloud Manager의 상태 평가를 사용하는 방법을 알아봅니다. AEM 환경을 검색하고, 보고서를 실행 및 검토하고, 문제 세부 정보를 보고, PDF를 내보내고, 이전 실행을 관리할 수 있습니다.
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Developer
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '1406'
ht-degree: 9%

---


# 상태 평가 {#about-health-assessment}

상태 평가는 AEM as a Cloud Service 내 Cloud Manager의 프로덕션 및 스테이징 환경에 대한 비침해적 자동 스캔입니다. 콘텐츠, 코드 및 구성을 평가하여 우수 사례에서 안티패턴과 이탈을 찾아 보안과 성능을 향상합니다.

상태 평가 서비스는 다음을 수행합니다.

* 환경을 스캔하고 성능 병목 현상, 비효율성 및 위험을 노출합니다.
* 블루프린트, 라이브 카피 및 고객 구성과 같은 콘텐츠 구조를 분석합니다.
* AEM SDK 및 타사 라이브러리를 포함하여 오래된 종속성을 감지합니다.
* 잘못된 주석 및 비효율적인 패턴과 같은 코드 품질 문제에 플래그를 지정합니다.
* 대시보드에서 실행 가능한 지침을 제공합니다(예: 작업 센터).
* 사전 예방적 문제 해결을 촉진하여 시스템 성능을 향상시킵니다.

각 실행에는 심각도별로 문제, 지침 및 권장 수정 사항에 대한 링크가 나열되며 보고서의 PDF 내보내기를 지원합니다. 현재 상태에 대한 **최신 보고서** 보기와 **이전 보고서**&#x200B;를 사용하여 실행을 비교할 수 있습니다.

규칙 정의 및 수정 세부 정보는 [상태 평가 패턴](#ha-patterns)도 참조하세요.

## 상태 평가 페이지 액세스 {#access-health-assessment}

1. [experiece.adobe.com](https://experience.adobe.com)에서 Cloud Manager에 로그인합니다.
1. **바로 가기** 섹션에서 **Experience Manager**&#x200B;를 클릭합니다.
1. 왼쪽 사이드 패널에서 **Cloud Manager**&#x200B;를 클릭합니다.
1. 원하는 조직을 선택합니다. 아래 이미지는 설명을 위한 것입니다. 자신의 조직 이름을 선택합니다.

   ![Cloud Manager에서 조직 선택](/help/implementing/cloud-manager/reports/assets/ha-org.png)

1. **내 프로그램** 콘솔에서 보고서를 보려는 프로그램을 클릭합니다.

1. 다음 중 하나를 수행합니다.
   * **환경** 카드에서 환경 이름 오른쪽에 있는 ![줄임표 아이콘 또는 기타 아이콘](https://spectrum.adobe.com/static/icons/ui_18/More.svg)을 클릭한 다음 메뉴에서 **상태 평가**&#x200B;를 선택합니다.

     ![환경 카드의 줄임표 메뉴에서 상태 평가 선택](/help/implementing/cloud-manager/reports/assets/ha-myprograms-environments-card.png)

   * 왼쪽 메뉴에서 **서비스** 아래의 ![데이터 아이콘](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Data_18_N.svg) **환경**&#x200B;을 클릭합니다. 환경 페이지의 환경 이름 오른쪽에서 ![줄임표 아이콘 또는 기타 아이콘](https://spectrum.adobe.com/static/icons/ui_18/More.svg)을 클릭한 다음 메뉴에서 **상태 평가**&#x200B;를 선택합니다.

     ![환경 페이지의 줄임표 메뉴에서 상태 평가 선택](/help/implementing/cloud-manager/reports/assets/ha-environments-page.png)

## 선택한 환경에 대한 새 보고서 실행 {#run-report}

1. [상태 평가 페이지에 액세스](#access-health-assessment).
1. **상태 평가** 페이지의 오른쪽 상단 모서리에서 평가하려는 대상 환경을 확인합니다.

   환경이 올바르지 않으면 ![V자 드롭다운 메뉴 또는 드롭다운 메뉴를 클릭하여 다른 환경을 선택](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ChevronDown_18_N.svg)하여 목록에서 올바른 환경을 선택하십시오.

1. **보고서 실행**&#x200B;을 클릭합니다.

   ![상태 평가 페이지에서 새 보고서 생성 단추를 클릭합니다](/help/implementing/cloud-manager/reports/assets/ha-run-report.png)

   선택한 환경에 대해 보고서가 실행되는 동안 **보고서 실행**&#x200B;이(가) 완료될 때까지 비활성화됩니다.

   ![실행 중인 보고서](/help/implementing/cloud-manager/reports/assets/ha-running-report.png)

   보고서가 완료되면 보고서가 **최신 보고서** 섹션의 **상태 평가** 페이지에 나타납니다.

## 최신 보고서 보기 {#view-latest-report}

* **상태 평가** 페이지에서 **최신 보고서** 섹션에서 다음 정보를 검토하십시오.

   * 가장 최근 실행의 결과입니다.
   * 실행 날짜 및 시간.
   * 총 문제 수.
   * 주요 주요 문제의 주요 내용.
   * 작업: **[모든 문제의 세부 정보 보기](#view-report-details)** 또는 **[PDF 다운로드](#download-pdf-report)**.

  ![선택한 환경에 대한 새 보고서 생성 이후의 최신 평가 페이지](/help/implementing/cloud-manager/reports/assets/ha-latest-report-page.png)

### 최신 보고서 세부 정보 보기 {#view-report-details}

* **상태 평가** 페이지에서 **최신 보고서** 제목 오른쪽에 있는 ![줄임표 아이콘 또는 기타 아이콘](https://spectrum.adobe.com/static/icons/ui_18/More.svg)을 클릭한 다음 **세부 정보 보기** 또는 **다운로드**&#x200B;를 클릭합니다.

  **세부 정보 보기** 옵션은 다음을 표시합니다.

   * 포괄적인 문제 목록.
   * 검색 결과 및 문제 설명을 볼 수 있습니다.
   * 잠재적인 수정 사항이 있는 설명서를 볼 수 있습니다.

     ![문제 설명 및 검색 결과](/help/implementing/cloud-manager/reports/assets/ha-issue-descriptions-and-findings.png)

   * **다운로드** 옵션을 사용하면 PDF에서 개별 문제 보고서를 다운로드할 수 있습니다.

     ![개별 문제 보고서의 PDF 다운로드](/help/implementing/cloud-manager/reports/assets/ha-details-page-doc-links.png)


### 전체 보고서의 PDF 다운로드 {#download-pdf-report}

* 보고서 페이지의 오른쪽 상단 모서리에서 **다운로드**&#x200B;를 클릭합니다.

  해당 보고서에서 감지된 모든 문제에 대한 PDF를 포함하는 ZIP 파일이 생성됩니다.

  ![보고서에서 발견된 모든 문제의 PDF 다운로드](/help/implementing/cloud-manager/reports/assets/ha-download-pdf.png)


## 지난 보고서 검토 {#review-past-reports}

**상태 평가** 페이지에서 **이전 보고서** 섹션에서 다음 정보를 검토하십시오.

* 이전 보고서의 세부 사항을 봅니다.
* 각 실행 날짜를 확인합니다.
* 모든 보고서에 대한 PDF을 다운로드합니다.
* 날짜, 문제 수 또는 환경별로 정렬합니다.

![이전 보고서 검토](/help/implementing/cloud-manager/reports/assets/ha-past-reports.png)

* **이전 보고서** 머리글 오른쪽에서 ![V자 드롭다운 또는 드롭다운 메뉴를 클릭하여 다른 환경을 선택](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ChevronDown_18_N.svg)하여 이전 보고서를 날짜별로 정렬합니다.
* 보고서의 맨 오른쪽에서 ![줄임표 아이콘 또는 기타 아이콘](https://spectrum.adobe.com/static/icons/ui_18/More.svg)을 클릭한 다음 **세부 정보 보기** 또는 **다운로드**&#x200B;를 클릭합니다.


## 상태 평가 패턴 {#ha-patterns}

다음은 AEM as a Cloud Service에서 상태 평가 가 감지하는 안티 패턴 및 문제의 전체 목록입니다. 이 테이블은 항목을 컨텐츠 분석, 코드 분석 및 Cloud Service Optimizer 안티 패턴의 세 가지 유형으로 그룹화하고 각각에 대한 설명을 제공합니다.

| 패턴 이름 | 범주 | 유형 | 설명 | 영향 | 자동 수정하시겠습니까? |
| --- | --- | --- | --- | --- | --- |
| 직접 사용자가 추가된 사용자 정의 AEM 그룹 | 보안 | 콘텐츠 분석 | 사용자가 IMS 그룹을 구성원으로 추가하는 대신 AEM 그룹에 직접 추가되었습니다. | 권한 관리 및 보안 거버넌스가 복잡해질 수 있습니다. [IMS 지원](https://experienceleague.adobe.com/ko/docs/experience-manager-cloud-service/content/security/ims-support) | 아니요 |
| 페이지에 JCR 콘텐츠 노드 누락 | 저장소 구조 | 콘텐츠 분석 | 페이지에 `jcr:content` 노드가 없습니다. | Experience Manager as a Cloud Service의 기능 제한 사항. [패턴 감지 - ACV](https://experienceleague.adobe.com/ko/docs/experience-manager-pattern-detection/table-of-contents/acv) | 아니요 |
| 페이지에 Sling 리소스 유형 누락 | 저장소 구조 | 콘텐츠 분석 | 페이지에 `sling:resourceType`이(가) 없습니다. | Experience Manager as a Cloud Service의 기능 제한 사항. [패턴 감지 - ACV](https://experienceleague.adobe.com/ko/docs/experience-manager-pattern-detection/table-of-contents/acv) | 아니요 |
| 노드 수가 너무 많은 페이지 | 성능 | 콘텐츠 분석 | 페이지에는 구조에 대량의 노드가 포함되어 있습니다. | 페이지 로드 시간이 느리고 사용자 경험이 부족합니다. [패턴 감지 - PCX](https://experienceleague.adobe.com/ko/docs/experience-manager-pattern-detection/table-of-contents/pcx) | 아니요 |
| 과도하게 실행 중인 워크플로 인스턴스 | 성능 | 콘텐츠 분석 | 실행 중인 워크플로 인스턴스가 너무 많습니다. | 전반적인 시스템 성능 저하. [유지 관리 작업](https://experienceleague.adobe.com/ko/docs/experience-manager-cloud-service/content/operations/maintenance) | 아니요 |
| 삭제되지 않은 완료된 워크플로 인스턴스 | 성능 | 콘텐츠 분석 | 이전에 완료된 워크플로 인스턴스가 삭제되지 않습니다. | 시스템 효율성 감소 및 스토리지 비용 증가 [유지 관리 작업](https://experienceleague.adobe.com/ko/docs/experience-manager-cloud-service/content/operations/maintenance) | 아니요 |
| 콘텐츠 조각 사용 통계 | 통계 | 콘텐츠 분석 | 사용 중인 콘텐츠 조각의 수를 추적합니다. | N/A | N/A |
| 콘텐츠 조각 모델 사용 통계 | 통계 | 콘텐츠 분석 | 사용 중인 콘텐츠 조각 모델의 수를 추적합니다. | N/A | N/A |
| MSM 많은 블루프린트 | 통계 | 콘텐츠 분석 | 블루프린트 수를 추적합니다. | 이로 인해 관리의 복잡성이 증가하고 컨텐츠 거버넌스가 더욱 어려워질 수 있습니다. | 해당 사항 없음 |
| 블루프린트당 MSM 페이지 | 통계 | 콘텐츠 분석 | 블루프린트당 페이지 수를 추적합니다. | 이로 인해 관리의 복잡성이 증가하고 컨텐츠 거버넌스가 더욱 어려워질 수 있습니다. | 해당 사항 없음 |
| MSM 과도한 라이브 카피 | 통계 | 콘텐츠 분석 | 라이브 카피 수를 추적합니다. | 이로 인해 롤아웃 중에 성능 문제가 발생하고 컨텐츠 동기화가 복잡해질 수 있습니다. | 해당 사항 없음 |
| 블루프린트당 MSM 과도한 라이브 카피 | 통계 | 콘텐츠 분석 | 블루프린트당 라이브 카피 수를 추적합니다. | 이로 인해 롤아웃 중에 성능 문제가 발생하고 컨텐츠 동기화가 복잡해질 수 있습니다. | 해당 사항 없음 |
| Assets 수 | 통계 | 콘텐츠 분석 | 에셋의 수를 추적합니다. | N/A | N/A |
| 사이트 수 | 통계 | 콘텐츠 분석 | 사이트 수를 추적합니다. | N/A | N/A |
| Forms 수 | 통계 | 콘텐츠 분석 | 양식 수를 추적합니다. | N/A | N/A |
| 양식 조각 | 통계 | 콘텐츠 분석 | 양식 조각의 수를 추적합니다. | N/A | N/A |
| 인터랙션 커뮤니케이션 | 통계 | 콘텐츠 분석 | 양식 통신 인터랙션 수를 추적합니다. | N/A | N/A |
| FDM | 통계 | 콘텐츠 분석 | 양식 데이터 모델의 수를 추적합니다. | N/A | N/A |
| 오래된 종속성 | 종속성 | 코드 분석 | 고객 저장소의 오래된 종속성을 강조 표시합니다. | 최신 AEM 버전과의 비호환성, 잠재적인 보안 취약성. | 아니요 |
| AEM SDK 버전 불일치 | 종속성 | 코드 분석 | Cloud Manager 환경 버전과 비교한 (n-2) 이전 버전. | 이로 인해 Cloud Manager에서 빌드 오류가 발생하고 로컬 개발 환경에서 문제가 발생할 수 있습니다. | 아니요 |
| 오래된 Mockito 코어 종속성 | 종속성 | 코드 분석 | 4.x.x 이하 버전은 AEM as a Cloud Service에서 오래된 것으로 간주됩니다. | 이로 인해 Cloud Manager에서 빌드 오류가 발생하고 로컬 개발 환경에서 문제가 발생할 수 있습니다. | 아니요 |
| 지원되지 않는 주석 | 종속성 | 코드 분석 | 고객의 Cloud Manager 저장소에서 지원되지 않는 주석입니다. | 잠재적인 애플리케이션 장애 및 성능 저하 | 아니요 |
| @Inject 모델에서 주석 생성 | 종속성 | 코드 분석 | 사용되지 않는 `@Inject` 주석입니다. | 주입 해상도 오버헤드로 인해 애플리케이션 성능 저하. | 아니요 |
| 아웃바운드 HTTP 요청 | 성능 | Cloud Service Optimizer 안티 패턴 | 요청 컨텍스트에서 사용에 문제가 있거나, 시간 초과가 많거나, 연결을 닫지 않습니다. | 전반적인 시스템 성능 저하 및 가동 중단 가능성 | 예 |
| 느린 쿼리 | 성능 | Cloud Service Optimizer 안티 패턴 | 고객 코드에서 쿼리 속도가 느려집니다. | 시스템 성능 저하 및 잠재적 시간 초과. | 예 |

### 범주 {#ha-patterns-categories}

| 범주 | 설명 |
| --- | --- |
| 보안 | 보안 작업, 사용자 관리 및 액세스 제어와 관련된 패턴입니다. |
| 성능 | 애플리케이션 및 시스템 성능에 영향을 주는 패턴. |
| 저장소 구조 | JCR 저장소 조직 및 구조와 관련된 패턴입니다. |
| 종속성 | 코드 종속성 및 버전 관리와 관련된 패턴입니다. |
| 통계 | 사용 통계 및 지표를 나타내는 패턴입니다. |



