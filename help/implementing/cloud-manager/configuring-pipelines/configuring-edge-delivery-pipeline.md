---
title: Edge Delivery 파이프라인 추가
description: Edge Delivery 파이프라인을 추가하여 코드를 빌드하고 프로덕션 환경에 배포하는 방법을 알아봅니다.
index: false
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
badge: label="얼리 어답터" type="Positive" url="/help/implementing/cloud-manager/release-notes/current.md#gitlab-bitbucket"
hide: true
hidefromtoc: true
source-git-commit: acb919474bfe4285c889b8646f731285f5b759ba
workflow-type: tm+mt
source-wordcount: '529'
ht-degree: 38%

---



# Edge Delivery 파이프라인 추가 {#configure-production-pipeline}

코드를 빌드하고 프로덕션 환경에 배포하기 위해 Edge Delivery 파이프라인을 구성하는 방법을 알아봅니다. 프로덕션 파이프라인은 먼저 코드를 스테이징 환경에 배포합니다. 승인 시 프로덕션 환경에 동일한 코드를 배포합니다.

프로덕션 파이프라인을 구성하려면 사용자에게 **[배포 관리자](/help/onboarding/cloud-manager-introduction.md#role-based-permissions)** 역할이 있어야 합니다.

>[!NOTE]
>
>다음과 같은 상황이 발생할 때까지 프로덕션 파이프라인을 설정할 수 없습니다.
>
>* 프로그램이 생성됩니다.
>* Git 저장소에는 분기가 하나 이상 있습니다.
>* 프로덕션 및 스테이징 환경이 생성됩니다.

코드 배포를 시작하기 전에 [!UICONTROL Cloud Manager]에서 파이프라인 설정을 구성하십시오.

>[!NOTE]
>
>초기 설정 후에 [파이프라인 설정을 편집](managing-pipelines.md)할 수 있습니다.

## 새 Edge Delivery 파이프라인 추가 {#adding-production-pipeline}

프로그램을 설정하고 [!UICONTROL Cloud Manager] UI를 사용하는 환경이 하나 이상 있는 경우 다음 단계에 따라 비프로덕션 파이프라인을 추가할 준비가 된 것입니다.

>[!TIP]
>
>프론트엔드 파이프라인을 구성하기 전에 [AEM 빠른 사이트 생성 여정](/help/journey-sites/quick-site/overview.md)에서 사용하기 쉬운 AEM 빠른 사이트 생성 도구에 대한 전체 안내서를 참조하십시오. 이 여정을 사용하면 AEM 사이트의 프론트엔드 개발을 간소화하여 AEM 백엔드 지식 없이 사이트를 빠르게 사용자 정의할 수 있습니다.

**새 Edge Delivery 파이프라인을 추가하려면:**

1. [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/)에서 Cloud Manager에 로그인한 다음 적절한 조직을 선택합니다.

1. **[내 프로그램](/help/implementing/cloud-manager/navigation.md#my-programs)** 콘솔에서 프로그램을 선택합니다.

1. **프로그램 개요** 페이지에서 **파이프라인** 카드로 이동한 다음 **추가**&#x200B;를 클릭하여 **프로덕션 파이프라인 추가**&#x200B;를 선택합니다.

   ![프로그램 관리자의 파이프라인 카드 개요](/help/implementing/cloud-manager/assets/configure-pipeline/add-prod-1.png)

1. **프로덕션 파이프라인 추가** 대화 상자가 표시됩니다. 파이프라인을 식별할 수 있도록 다음 옵션과 함께 **파이프라인 이름**&#x200B;을 입력합니다. **계속**&#x200B;을 클릭합니다.

   **배포 트리거** - 다음과 같은 옵션을 사용하여 배포 트리거를 정의하여 파이프라인을 시작할 수 있습니다.

   * **수동** - 파이프라인을 수동으로 시작합니다.
   * **Git 변경 시** - 구성된 Git 분기에 커밋이 추가될 때마다 CI/CD 파이프라인을 시작합니다. 이 옵션을 사용하면 필요에 따라 파이프라인을 수동으로 시작할 수 있습니다.

   **중요한 지표 장애 비헤이비어** - 파이프라인 설정 또는 편집 중에 **배포 관리자**&#x200B;는 품질 게이트에서 중요한 장애가 발생했을 때 파이프라인의 비헤이비어를 정의할 수 있는 옵션을 제공합니다. 사용 가능한 옵션은 다음과 같습니다.

   * **매번 묻기** - 기본 설정입니다. 중요한 장애가 발생하면 수동으로 개입해야 합니다.
   * **즉시 실패** - 이 옵션을 선택하면 중요한 오류가 발생할 때마다 파이프라인이 취소됩니다. 이 프로세스는 본질적으로 각 실패를 수동으로 거부하는 사용자를 에뮬레이션하는 것입니다.
   * **즉시 계속** - 이 옵션을 선택하면 중요한 오류가 발생할 때마다 파이프라인이 자동으로 진행됩니다. 이 프로세스는 본질적으로 각 실패를 수동으로 승인하는 사용자를 에뮬레이션하는 것입니다.

   ![프로덕션 파이프라인 구성](/help/implementing/cloud-manager/assets/configure-pipeline/production-pipeline-configuration.png)

1. **Source 코드** 탭에서 파이프라인이 처리해야 하는 코드 유형을 선택합니다.

   * **[전체 스택 코드 파이프라인 구성](#full-stack-code)**
   * **[타깃팅된 배포 파이프라인 구성](#targeted-deployment)**

파이프라인 유형에 대한 자세한 내용은 [CI/CD 파이프라인](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md)을 참조하십시오.

프로덕션 파이프라인 생성을 완료하는 단계는 선택한 소스 코드 유형에 따라 다릅니다. 파이프라인 구성을 완료할 수 있도록 위의 링크를 따라 이 문서의 다음 섹션으로 이동합니다.

