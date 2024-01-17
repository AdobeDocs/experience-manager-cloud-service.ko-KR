---
title: 프로그램 관리 및 편집
description: 프로덕션 및 샌드박스 프로그램을 만든 후 옵션을 조정하도록 편집하는 방법을 알아봅니다.
exl-id: 819e4a6e-f77a-4594-a402-a300dcbdf510
source-git-commit: 0d60c19638707262dab7f290f84fa873b694bc22
workflow-type: tm+mt
source-wordcount: '900'
ht-degree: 43%

---


# 프로그램 관리 및 편집 {#editing-programs}

다음 **내 프로그램** 페이지는 액세스 권한이 있는 모든 프로그램에 대한 개요를 제공합니다. 개별 프로그램을 선택할 때 **프로그램 개요** 페이지는 프로그램에 대한 세부 정보를 한눈에 제공합니다.

다음에서 **프로그램 개요**, 필요한 권한이 있는 사용자는 [조직에서 만든 프로덕션 프로그램](creating-production-programs.md) 및 [조직에서 만든 샌드박스 프로그램.](creating-sandbox-programs.md) 프로그램을 편집하여 다음과 같은 작업을 수행할 수 있습니다.

* Assets가 있는 기존 프로그램에 Sites 솔루션을 추가하며, 이와 반대도 마찬가지입니다.
* Sites와 Assets가 모두 있는 기존 프로그램에서 Sites 또는 Assets를 제거할 수 있습니다.
* 두 번째 미사용 솔루션 권한을 기존 프로그램에 추가하거나 새 프로그램으로 추가합니다.
* 샌드박스 프로그램을 삭제합니다.

## 권한 {#permissions}

의 멤버여야 합니다. **비즈니스 소유자** 역할을 사용하여 프로그램을 편집하거나 샌드박스 프로그램을 삭제하고 라이선스 대시보드에 액세스합니다.

## 내 프로그램 {#my-programs}

1. [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/)에서 Cloud Manager에 로그인한 다음 적절한 조직을 선택합니다.

1. 다음 **내 프로그램** 페이지에 타일로 액세스할 수 있는 모든 프로그램 목록이 표시됩니다.

![내 프로그램 페이지](/help/implementing/cloud-manager/assets/my-programs.png)

### 클릭 유도 문안 {#cta}

페이지 맨 위에는 조직 상태와 관련된 콜 투 액션이 있습니다. 예를 들어 프로그램을 성공적으로 설정한 경우 지난 90일 동안의 활동 통계가 다음과 같이 표시될 수 있습니다.

* 의 수 [배포](/help/implementing/cloud-manager/deploy-code.md)
* 의 수 [코드 품질 문제](/help/implementing/cloud-manager/code-quality-testing.md) 식별됨
* 빌드 수

또는 조직 설정을 막 시작하는 경우 다음 단계 또는 설명서 리소스에 대한 팁이 있을 수 있습니다.

### 프로그램 탭 {#programs-tab}

다음 **프로그램** 탭에는 액세스 권한이 있는 각 프로그램을 나타내는 카드가 나열됩니다. 카드를 탭하거나 클릭하여 **프로그램 개요** 프로그램에 대한 자세한 내용은 프로그램의 페이지를 참조하십시오.

정렬 옵션을 사용하여 필요한 프로그램을 더 잘 찾을 수 있습니다.

![정렬 옵션](/help/implementing/cloud-manager/assets/my-programs-sorting.png)

* 정렬 기준
   * 생성일(기본값)
   * 프로그램 이름
   * 상태
* 오름차순(기본값) / 내림차순
* 격자 보기(기본값)
* 목록 보기

### 라이선스 탭 {#license-tab}

다음 **라이선스** 탭에서는 [라이선스 대시보드.](/help/implementing/cloud-manager/license-dashboard.md)

## 프로그램 개요 {#program-overview}

에서 프로그램을 선택하면 **[내 프로그램](#my-programs)** 페이지를 열고 Cloud Manager가 **프로그램 개요** 선택한 프로그램에 대한 페이지입니다.

![프로그램 개요 페이지](/help/implementing/cloud-manager/assets/program-overview.png)

페이지 왼쪽 상단 모서리에서 프로그램 이름을 탭하거나 클릭하여 다른 프로그램으로 빠르게 전환하거나 로 돌아갑니다. **[내 프로그램](#my-programs)** 페이지를 가리키도록 업데이트하는 중입니다. 다음을 수행할 수도 있습니다. [선택한 프로그램 편집](#editing) 또는 [프로그램을 추가합니다.](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-production-programs.md)

![프로그램 전환기](/help/implementing/cloud-manager/assets/program-switcher.png)

맨 위에 있는 콜 투 액션은 프로그램의 상태에 따라 유용한 정보를 제공합니다. 새 프로그램의 경우 다음 단계 및 Go-Live 날짜 알림 메시지가 제공될 수 있습니다. [프로그램을 만드는 동안 설정됩니다.](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/editing-programs.md)

![새 프로그램에 대한 클릭 유도 문안](/help/implementing/cloud-manager/assets/info-banner-new-program.png)

라이브 프로그램의 경우, 세부 정보 및 새 배포 시작에 대한 링크가 포함된 마지막 배포의 상태입니다.

![클릭 유도 문안](/help/implementing/cloud-manager/assets/info-banner.png)

**환경** 및 **파이프라인** 카드는 선택한 프로그램 내에 있는 두 가지 모두에 대한 간략한 개요를 제공합니다.

![카드](/help/implementing/cloud-manager/assets/environments-pipelines.png)

다음 **성능** 카드는 의 개요를 제공합니다. **[CDN 대시보드.](/help/implementing/cloud-manager/cdn-performance.md)**

![성능 카드](/help/implementing/cloud-manager/assets/cdn-performance-dashboard.png)

## 프로그램 편집 {#editing}

1. [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/)에서 Cloud Manager에 로그인한 다음 적절한 조직을 선택합니다.

1. 다음에서 **[내 프로그램](#my-programs)** 페이지에서 편집할 프로그램을 클릭하여 세부 정보를 표시합니다.

1. 페이지 왼쪽 상단의 프로그램 이름을 클릭하고 **프로그램 편집**&#x200B;을 선택합니다.

   ![프로그램 편집 옵션](assets/edit-program-overview.png)

1. **프로그램 편집** 페이지가 열립니다. **일반** 탭에서 프로그램 이름과 설명을 편집합니다.

   * 프로그램에 대해 솔루션을 하나 이상 선택해야 합니다.

   ![일반 탭](assets/edit-program-prod1.png)

1. **솔루션 및 추가 기능** 탭에서 프로그램에 대한 솔루션을 수정합니다.

   ![솔루션 선택](assets/edit-prg.png)

1. 솔루션 이름 앞의 V자형 화살표를 클릭하면 **Sites**&#x200B;에서 **Commerce** 추가 기능 옵션을 선택하는 것과 같은 선택적 추가 기능이 표시됩니다.

   ![추가 기능 편집](assets/edit-program-add-on.png)

1. **Go-Live 설정** 탭에서 프로그램의 계획된 Go-Live 날짜를 수정합니다.

   ![Go-Live 설정 편집](assets/edit-program-go-live.png)

   * 이 날짜는 정보용으로만 제공됩니다. 프로그램 개요 페이지에서 Go Live 위젯을 트리거합니다. 결국 Adobe Experience Manager(AEM) as a Cloud Service 모범 사례 문서에 대한 제품 내 링크를 제공함으로써 여정에 맞춰 성공적인 Go Live 경험을 제공합니다.
   * 이 탭은 샌드박스 프로그램에 사용할 수 없습니다.

1. 프로그램에 필요한 권한을 사용할 수 있는 경우 **보안** 탭에는 프로그램의 보안 옵션을 수정할 수 있는 위치가 표시됩니다.

   ![보안 설정 편집](assets/edit-program-security.png)

   * 다음 이후 HIPAA를 활성화하거나 비활성화할 수 없음 [프로그램 제작.](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-production-programs.md)
      * Adobe의 HIPAA 준비 솔루션 구현에 대해 [자세히 알아보십시오](https://www.adobe.com/go/hipaa-ready_kr).
   * 활성화되면 를 설정하여 WAF-DDOS 보호를 구성할 수 있습니다. [비프로덕션 파이프라인.](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md)

1. **업데이트**&#x200B;를 클릭하여 프로그램에 대한 변경 사항을 저장합니다.

솔루션 또는 추가 기능 추가 또는 제거를 포함하여 프로그램을 편집할 때마다 이러한 변경 사항은 다음 배포 이후에 적용됩니다.

## 샌드박스 프로그램 삭제 {#delete-sandbox-program}

샌드박스 프로그램을 삭제하면 관련된 모든 환경 및 파이프라인이 제거됩니다.

>[!TIP]
>
>**비즈니스 소유자** 또는 **배포 관리자** 역할이 있는 사용자는 전체 샌드박스 프로그램 대신 프로덕션 및 스테이징 환경을 삭제할 수 있습니다.

샌드박스 프로그램을 삭제하려면 다음 작업을 수행합니다.

1. [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/)에서 Cloud Manager에 로그인한 다음 적절한 조직을 선택합니다.

1. 다음에서 **[내 프로그램](#my-programs)** 페이지에서 편집할 프로그램을 클릭하여 세부 정보를 표시합니다.

1. 페이지 왼쪽 상단에서 프로그램 이름을 클릭하고 을 선택합니다 **프로그램 삭제**.

   ![프로그램 삭제 옵션](assets/delete-sandbox1.png)

또는 Cloud Manager 개요 페이지에서 프로그램 카드의 줄임표 버튼을 클릭하고 **프로그램 삭제**&#x200B;를 선택할 수 있습니다.

![프로그램 카드의 샌드박스 삭제](assets/delete-sandbox2.png)

>[!NOTE]
>
>샌드박스 프로그램만 삭제할 수 있습니다. 프로덕션 프로그램은 삭제할 수 없습니다.
