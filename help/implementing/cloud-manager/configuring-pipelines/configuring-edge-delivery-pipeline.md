---
title: Edge Delivery 파이프라인 추가
description: Edge Delivery 파이프라인을 추가하여 코드를 빌드하고 프로덕션 환경에 배포하는 방법을 알아봅니다.
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Developer
hide: false
index: false
hidefromtoc: false
exl-id: 5ad342fa-dd71-4105-a9cb-2d999d402780
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '613'
ht-degree: 14%

---

# Edge Delivery 파이프라인 추가 {#configure-production-pipeline}

<!--badge: label="Beta" type="Positive" url="/help/implementing/cloud-manager/release-notes/current.md#gitlab-bitbucket" -->

코드를 빌드하고 프로덕션 환경에 배포하기 위해 Edge Delivery 파이프라인을 구성하는 방법을 알아봅니다. Edge Delivery 파이프라인을 사용하면 로그 전달 및 Adobe 관리 CDN을 비롯한 기능을 구성할 수 있습니다.

지원되는 구성 목록에 대해서는 [구성 파이프라인 사용 - 지원되는 구성](/help/operations/config-pipeline.md#configurations)을 참조하십시오.

프로덕션 파이프라인을 구성하려면 사용자에게 **[배포 관리자](/help/onboarding/cloud-manager-introduction.md#role-based-permissions)** 역할이 있어야 합니다.

>[!IMPORTANT]
>
>다음과 같은 상황이 발생할 때까지 Edge Delivery 파이프라인을 구성할 수 없습니다.
>
>* 하나의 Edge Delivery Services 사이트 및 하나의 매핑된 도메인을 포함하는 프로그램이 만들어집니다. 그렇지 않으면 **Edge Delivery 파이프라인 추가** 옵션이 사용자 인터페이스에 비활성화되어 있고 누락된 요구 사항에 대해 설명하는 도구 설명이 표시됩니다. [Cloud Manager에서 Edge Delivery 사이트 만들기](/help/implementing/cloud-manager/edge-delivery/create-edge-delivery-site.md)를 참조하세요.
>* Git 저장소에는 분기가 하나 이상 있습니다. [Cloud Manager의 저장소 관리](/help/implementing/cloud-manager/managing-code/managing-repositories.md)를 참조하십시오.
>* 프로덕션 및 스테이징 환경이 생성됩니다. [CI/CD 파이프라인 소개](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md)를 참조하십시오.

<!-- CMGR‑69680 -->

코드 배포를 시작하기 전에 [!UICONTROL Cloud Manager]에서 파이프라인 설정을 구성하십시오.

>[!NOTE]
>
>초기 구성 후 [파이프라인 설정을 편집](managing-pipelines.md)할 수 있습니다.

**Edge Delivery 파이프라인을 추가하려면:**

1. [experience.adobe.com](https://experience.adobe.com)에서 Cloud Manager에 로그인합니다.
1. **바로 가기** 섹션에서 **Experience Manager**&#x200B;를 클릭합니다.
1. 왼쪽 사이드 패널에서 **Cloud Manager**&#x200B;를 클릭합니다.
1. 원하는 조직을 선택합니다.
1. **내 프로그램** 콘솔에서 프로그램을 클릭합니다.

   ![Cloud Manager의 내 프로그램 페이지](/help/implementing/cloud-manager/configuring-pipelines/assets/my-programs.png)

1. 다음 중 하나를 수행하십시오.

   * **파이프라인 카드에서 Edge Delivery 파이프라인 추가**

      1. 왼쪽 레일의 **프로그램**&#x200B;에서 **![개요 아이콘](/help/implementing/cloud-manager/configuring-pipelines/assets/overview.svg) [개요](/help/implementing/cloud-manager/navigation.md#my-programs)**&#x200B;를 클릭합니다.
      1. **프로그램 개요** 페이지의 **파이프라인** 카드에서 **![더하기 기호](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Add_18_N.svg)추가**&#x200B;를 클릭한 다음 **Edge Delivery 파이프라인 추가**&#x200B;를 선택합니다.

         ![프로그램 개요 페이지의 파이프라인 카드](/help/implementing/cloud-manager/configuring-pipelines/assets/pipelinescard-add-ed-pipeline.png)

         >[!TIP]
         >
         >위의 스크린샷에 표시된 대로 **파이프라인** 카드를 사용하는 것 외에 **파이프라인** 페이지에서 파이프라인을 관리할 수도 있습니다.
         >
         >![파이프라인 이름, 상태, 저장소 및 분기를 표시하는 Edge Delivery 파이프라인 위젯](/help/implementing/cloud-manager/release-notes/assets/edge-delivery-pipeline-widget.png)

   * **파이프라인 페이지에서 Edge Delivery 파이프라인 추가**

      1. 왼쪽 레일의 **프로그램**&#x200B;에서 **![워크플로 아이콘 또는 파이프라인 아이콘](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Workflow_18_N.svg) 파이프라인**&#x200B;을 클릭합니다.
      1. 파이프라인 페이지의 오른쪽 상단 모서리에서 **파이프라인 추가** > **Edge Delivery 파이프라인 추가**&#x200B;를 클릭합니다.

         ![파이프라인 추가 단추가 있는 파이프라인 페이지](/help/implementing/cloud-manager/configuring-pipelines/assets/pipelinespage-add-ed-pipeline.png)

         >[!TIP]
         >
         >왼쪽 상단 모서리에서 **필터**&#x200B;를 클릭한 다음 **배달 유형** 섹션에서 **Edge 배달** 확인란을 선택하여 Edge Delivery 파이프라인(즉, Edge Delivery Services을 사용하는 파이프라인)으로만 목록을 필터링합니다. <!-- (CMGR-69682) -->
         >
         >![Edge 게재 및 게시 게재의 새로운 게재 유형이 표시되는 필터 패널](/help/implementing/cloud-manager/release-notes/assets/filter-delivery-type.png)

1. **Edge Delivery 파이프라인 추가** 대화 상자의 **파이프라인 이름** 텍스트 필드에 설명 파이프라인 레이블을 입력합니다.

   ![Edge Delivery 파이프라인 추가 대화 상자](/help/implementing/cloud-manager/configuring-pipelines/assets/add-edge-delivery-pipeline-configuration.png)

1. 원하는 **배포 트리거** 옵션을 선택하십시오.

   * **수동** - 배포를 시작합니다.
   * **Git 변경 시** - Git 커밋은 배포를 자동으로 시작합니다. 이 옵션을 사용하면 필요한 경우 파이프라인을 수동으로 시작할 수 있습니다.

1. **계속**&#x200B;을 클릭합니다.

1. **Source 코드**&#x200B;에서 다음 옵션을 설정합니다.

   * **배포 환경** - 대상 환경 필드를 표시하며 읽기 전용으로 유지됩니다.

   * **저장소** - 드롭다운 목록을 사용하여 파이프라인이 Edge Delivery 구성을 저장하는 정확한 Git 저장소를 가리키도록 합니다.

     Cloud Manager에서 저장소를 추가하고 관리하는 방법은 [저장소 추가 및 관리](/help/implementing/cloud-manager/managing-code/managing-repositories.md)를 참조하십시오.

   * **Git 분기** - 드롭다운 목록을 사용하여 선택한 저장소 내에서 특정 분기를 선택합니다. 필요한 경우 ![재생 아이콘 또는 새로 고침 아이콘](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Refresh_18_N.svg)을 클릭하여 최근 푸시 후 Git 분기 드롭다운 목록을 다시 로드합니다.
   * **코드 위치** - 파이프라인 준비 코드가 시작되는 저장소 내의 폴더 경로를 정의합니다(`/`은(는) 저장소 루트와 같음).

   ![파이프라인 구성](/help/implementing/cloud-manager/configuring-pipelines/assets/add-edge-delivery-pipeline-sourcecode.png)

1. **저장**&#x200B;을 클릭합니다.

이제 [프로그램 개요](managing-pipelines.md) 페이지의 **파이프라인** 카드 또는 **파이프라인** 페이지에서 파이프라인을 **관리**&#x200B;할 수 있습니다.


![파이프라인 이름, 상태, 저장소 및 분기를 표시하는 Edge Delivery 파이프라인 위젯](/help/implementing/cloud-manager/release-notes/assets/edge-delivery-pipeline-widget.png)



