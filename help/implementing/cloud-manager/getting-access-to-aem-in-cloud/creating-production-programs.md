---
title: 프로덕션 프로그램 만들기
description: Cloud Manager를 사용하여 라이브 트래픽을 호스팅하는 자체 프로덕션 프로그램을 만드는 방법을 알아봅니다.
exl-id: 4ccefb80-de77-4998-8a9d-e68d29772bb4
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 6a3d2d484bde20586b329010cdfe156570e736f5
workflow-type: tm+mt
source-wordcount: '1029'
ht-degree: 12%

---


# 프로덕션 프로그램 만들기 {#create-production-program}

프로덕션 프로그램은 AEM 및 Cloud Manager에 익숙한 사용자가 라이브 트래픽을 처리하기 위해 배포할 목적으로 코드를 작성, 빌드 및 테스트할 준비가 되었습니다.

프로그램 유형에 대한 자세한 내용은 [프로그램 및 프로그램 유형 이해](program-types.md) 문서를 참조하십시오.

## 프로덕션 프로그램 만들기 {#create}

조직의 사용 권한에 따라 프로그램을 추가할 때 [추가 옵션](#options)이 표시될 수 있습니다.

**프로덕션 프로그램을 만들려면:**

1. [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/)에서 Cloud Manager에 로그인한 다음 적절한 조직을 선택합니다.

1. 오른쪽 상단 근처에 있는 **[내 프로그램](/help/implementing/cloud-manager/navigation.md#my-programs)** 콘솔에서 **프로그램 추가**&#x200B;를 클릭합니다.

   ![Cloud Manager 랜딩 페이지](assets/log-in.png)

1. *프로그램을 만들어 보세요* 마법사의 **프로그램 이름** 텍스트 필드에 프로그램에 사용할 이름을 입력합니다.

1. **프로그램 목표**&#x200B;에서 **`Set up for production`**&#x200B;을(를) 선택합니다.

   ![프로그램 만들기 마법사](assets/create-production-program.png)

1. (선택 사항) 마법사 대화 상자의 오른쪽 아래 모서리에서 다음 중 하나를 수행합니다.

   * 이미지 파일을 **프로그램 이미지 추가** 대상으로 끌어서 놓습니다.
   * **프로그램 이미지 추가**&#x200B;를 클릭한 다음 파일 브라우저에서 이미지를 선택합니다.
   * 추가한 이미지를 삭제하려면 휴지통 아이콘을 클릭합니다.

1. **계속**&#x200B;을 클릭합니다.

1. **솔루션 및 추가 기능** 목록 상자에서 프로그램에 포함할 하나 이상의 솔루션을 선택합니다.

   * 사용 허가된 여러 솔루션에 대해 하나 이상의 프로그램이 필요한지 확실하지 않은 경우 가장 관심이 있는 프로그램을 선택합니다. 나중에 [프로그램을 편집](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/editing-programs.md)하여 추가 솔루션을 활성화할 수 있습니다. 프로그램 설정 권장 사항에 대한 자세한 내용은 [프로덕션 프로그램 소개 문서](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/introduction-production-programs.md)를 참조하십시오.
   * 프로그램 제작에는 하나 이상의 솔루션이 필요합니다.
   * 디지털 환경을 최적화하는 전체 관리 CDN 솔루션으로 **Edge Deliver Services**&#x200B;를 선택하십시오. [Edge Delivery Services을 사용하여 Cloud Manager 프로젝트 게재 정보](#edge-overview)를 참조하세요.
   * **[향상된 보안 사용](#security)** 옵션을 선택한 경우 HIPAA 권한을 사용할 수 있는 만큼의 솔루션만 선택할 수 있습니다.

   ![솔루션 선택](/help/implementing/cloud-manager/assets/add-production-program-with-edge.png)

1. 솔루션 이름 왼쪽의 V자형 화살표를 클릭하면 **Sites**&#x200B;에서 **Commerce** 추가 기능 옵션과 같은 선택적 추가 기능이 표시됩니다.

   ![추가 기능 선택](assets/setup-prod-commerce.png)

1. 솔루션 및 추가 기능을 선택한 상태에서 **계속**&#x200B;을 클릭합니다.

1. **Go-Live 날짜** 탭에서 프로덕션 프로그램을 실행하기로 계획한 날짜를 입력합니다.

   ![계획된 Go-Live 날짜 정의](assets/set-up-go-live.png)

   * 언제든지 이 날짜를 편집할 수 있습니다.
   * 날짜는 정보 제공 목적으로 [**프로그램 개요** 페이지](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/editing-programs.md#program-overview)에서 Go Live 위젯을 트리거합니다. 이 기능은 원활한 Go-Live 경험을 지원하기 위해 AEM as a Cloud Service 모범 사례에 대한 제품 내 링크를 적시에 제공합니다.

1. **만들기**&#x200B;를 클릭합니다. Cloud Manager은 프로그램을 만들고 선택 항목을 위한 랜딩 페이지에 표시합니다.

![Cloud Manager 개요](assets/navigate-cm.png)

## 추가 프로덕션 프로그램 옵션 {#options}

조직에서 사용할 수 있는 권한에 따라 프로덕션 프로그램을 만들 때 사용할 수 있는 추가 옵션이 있을 수 있습니다.

### 보안 {#security}

필요한 권한이 있는 경우 **보안** 탭이 **`Set up for production`** 대화 상자의 첫 번째 탭으로 표시됩니다.

![보안 옵션](assets/create-production-program-security.png)

**보안** 탭은 프로덕션 프로그램에 대해 **HIPAA** 또는 **WAF-DDOS 보호** 또는 두 가지 모두를 활성화하는 옵션을 제공합니다.

Adobe HIPAA 준수 및 WAF-DDOS(Web Application Firewall - Distributed Denial of Service)는 취약점으로부터 보호하기 위한 다층적 접근 방식의 일환으로 클라우드 기반 보안을 용이하게 합니다.

* **HIPAA** - 이 옵션은 Adobe의 HIPPA 지원 솔루션 구현을 활성화합니다.
   * Adobe의 HIPAA 준비 솔루션 구현에 대해 [자세히 알아보십시오](https://www.adobe.com/trust/compliance/hipaa-ready.html).
   * 프로그램 생성 후에는 HIPAA를 활성화하거나 비활성화할 수 없습니다.
* **WAF-DDOS 보호** - 이 옵션을 사용하면 규칙을 통해 응용 프로그램을 보호하는 웹 응용 프로그램 방화벽을 사용할 수 있습니다.
   * 활성화되면 [비프로덕션 파이프라인](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md)을 설정하여 WAF-DDOS 보호를 구성할 수 있습니다.
   * [WAF 규칙을 포함한 트래픽 필터 규칙](/help/security/traffic-filter-rules-including-waf.md)을(를) 참조하여 제대로 배포되도록 저장소에서 트래픽 필터 규칙을 관리하는 방법을 알아보십시오.

### SLA {#sla}

필요한 권한이 있는 경우 **SLA** 탭이 **`Set up for production`** 대화 상자에 두 번째 또는 세 번째 탭으로 표시됩니다.

![SLA 옵션](assets/create-production-program-sla.png)

AEM Sites과 Forms은 표준 99.9% 서비스 수준 계약(SLA)을 제공합니다. **99.99% 서비스 수준 계약** 옵션을 사용하면 사이트 및/또는 Forms의 프로덕션 환경에서 99.99%의 최소 가동 시간 비율을 사용할 수 있습니다.

99.99% SLA은 가용성 향상, 지연 시간 단축 등의 이점을 제공하며 [추가 게시 영역](/help/implementing/cloud-manager/manage-environments.md#multiple-regions)을 프로그램의 프로덕션 환경에 적용해야 합니다.

99.99% SLA을 활성화하기 위한 [요구 사항](#sla-requirements)이 충족되면 [전체 스택 파이프라인](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md)을(를) 실행하여 활성화해야 합니다.

#### 99.99% SLA 요구 사항 {#sla-requirements}

필요한 권한 외에, 99.99%의 SLA에 추가 사용 요구 사항이 있습니다.

* 조직에는 프로그램에 99.99% SLA을 적용할 때 사용할 수 있는 99.99% SLA 및 추가 게시 영역 권한이 있어야 합니다.
* Cloud Manager은 프로그램에 99.99% SLA을 적용하기 전에 사용되지 않은 [추가 게시 영역](/help/implementing/cloud-manager/manage-environments.md#multiple-regions) 권한을 사용할 수 있는지 확인합니다.
* 프로그램을 편집할 때 이미 하나 이상의 추가 게시 영역이 있는 프로덕션 환경이 포함된 경우 Cloud Manager은 99.99% SLA 권한의 가용성만 확인합니다.
* 99.99% SLA 활성화 및 보고를 위해서는 [프로덕션/스테이징 환경](/help/implementing/cloud-manager/manage-environments.md#adding-environments)이 만들어져야 하며 프로덕션/스테이징 환경에 하나 이상의 추가 게시 영역이 적용되어야 합니다.
   * [고급 네트워킹](/help/security/configuring-advanced-networking.md)을 사용하는 경우 [새 환경에 여러 Publish 지역 추가](/help/implementing/cloud-manager/manage-environments.md#adding-regions) 문서에서 권장 사항을 확인하여 지역 오류가 발생할 경우 연결을 유지하십시오.
* 최소 1개의 추가 게시 영역은 99.99% SLA 프로그램에 유지되어야 합니다. 사용자는 99.99% SLA 프로그램에서 마지막 추가 게시 영역을 삭제할 수 없습니다.
* 사이트 또는 Forms 솔루션이 활성화된 프로덕션 프로그램에 대해서는 99.99%의 SLA이 지원됩니다.
* [전체 스택 파이프라인](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md)을 실행하여 프로그램을 활성화하거나 편집할 때 99.99% SLA을 비활성화합니다.

## 프로그램 액세스 {#accessing}

1. 랜딩 페이지에 프로그램 카드가 표시되면 줄임표 버튼을 선택하여 사용 가능한 메뉴 옵션을 확인합니다.

   ![프로그램 개요](assets/program-overview.png)

1. **프로그램 개요**&#x200B;를 선택하여 Cloud Manager의 **개요** 페이지로 이동합니다.

1. 개요 페이지의 기본 콜 투 액션 카드는 환경, 비프로덕션 파이프라인 및 마지막으로 프로덕션 파이프라인을 만드는 과정을 안내합니다.

   ![프로그램 개요](assets/set-up-prod5.png)

>[!TIP]
>
>Cloud Manager 탐색 방법 및 **내 프로그램** 콘솔 이해에 대한 자세한 내용은 [Cloud Manager UI 탐색](/help/implementing/cloud-manager/navigation.md)을 참조하십시오.

>[!NOTE]
>
>[샌드박스 프로그램](introduction-sandbox-programs.md#auto-creation)과 달리 프로덕션 프로그램에서는 적절한 Cloud Manager 역할의 사용자가 프로젝트를 만들고 셀프서비스 UI를 통해 환경을 추가해야 합니다.


