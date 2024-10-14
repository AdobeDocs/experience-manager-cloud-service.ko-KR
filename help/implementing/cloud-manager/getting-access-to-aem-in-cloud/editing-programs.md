---
title: 프로그램 편집
description: 프로덕션 및 샌드박스 프로그램을 만든 후 옵션을 조정하도록 편집하는 방법을 알아봅니다.
exl-id: 819e4a6e-f77a-4594-a402-a300dcbdf510
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 40a76e39750d6dbeb03c43c8b68cddaf515a2614
workflow-type: tm+mt
source-wordcount: '427'
ht-degree: 45%

---


# 프로그램 편집 {#editing-programs}

프로그램을 관리하고 편집하려면 [**내 프로그램** 콘솔](/help/implementing/cloud-manager/navigation.md)에서 시작하십시오. **내 프로그램** 페이지에서는 액세스 권한이 있는 모든 프로그램에 대한 개요를 제공합니다. 개별 프로그램을 선택할 때 **프로그램 개요** 페이지에서 프로그램에 대한 세부 정보를 한눈에 볼 수 있습니다.

**프로그램 개요**&#x200B;에서 필수 권한이 있는 사용자는 [조직에서 만든 프로덕션 프로그램](creating-production-programs.md) 및 [조직에서 만든 샌드박스 프로그램](creating-sandbox-programs.md)을 편집할 수 있습니다. 프로그램을 편집하여 다음과 같은 작업을 수행할 수 있습니다.

* Assets가 있는 기존 프로그램에 Sites 솔루션을 추가하며, 이와 반대도 마찬가지입니다.
* Sites와 Assets가 모두 있는 기존 프로그램에서 Sites 또는 Assets를 제거할 수 있습니다.
* 두 번째 미사용 솔루션 권한을 기존 프로그램에 추가하거나 새 프로그램으로 추가합니다.
* 샌드박스 프로그램을 삭제합니다.

## 권한 {#permissions}

프로그램을 편집하거나 샌드박스 프로그램을 삭제하고 라이선스 대시보드에 액세스하려면 **비즈니스 소유자** 역할의 멤버여야 합니다.

## 프로그램 편집 {#editing}

솔루션 또는 추가 기능 추가 또는 제거를 포함하여 프로그램을 편집할 때마다 이러한 변경 사항은 다음 배포 이후에 적용됩니다.

**프로그램을 편집하려면:**

1. [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/)에서 Cloud Manager에 로그인한 다음 적절한 조직을 선택합니다.

1. **[내 프로그램](#my-programs)** 페이지에서 편집할 프로그램을 클릭하여 세부 정보를 표시합니다.

1. 페이지 왼쪽 상단의 프로그램 이름을 클릭하고 **프로그램 편집**&#x200B;을 선택합니다.

   ![프로그램 편집 옵션](assets/edit-program-overview.png)

1. **프로그램 편집** 페이지에서 **일반** 탭이 열립니다.

   ![일반 탭](assets/edit-program-prod1.png)

1. 프로그램 편집에 사용할 수 있는 옵션은 프로그램을 만들 때와 동일합니다.
   * 개별 옵션에 대한 자세한 내용은 [프로덕션 프로그램 만들기](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-production-programs.md) 및 [샌드박스 프로그램 만들기](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-sandbox-programs.md)를 참조하십시오.
   * 조직의 권한에 따라 프로덕션 프로그램에 [추가 옵션](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-production-programs.md#options)을 사용할 수 있습니다.

1. **업데이트**&#x200B;를 클릭하여 프로그램에 대한 변경 사항을 저장합니다.

## 샌드박스 프로그램 삭제 {#delete-sandbox-program}

샌드박스 프로그램을 삭제하면 관련된 모든 환경 및 파이프라인이 제거됩니다.

>[!TIP]
>
>**비즈니스 소유자** 또는 **배포 관리자** 역할이 있는 사용자는 전체 샌드박스 프로그램 대신 프로덕션 및 스테이징 환경을 삭제할 수 있습니다.

**샌드박스 프로그램을 삭제하려면:**

1. [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/)에서 Cloud Manager에 로그인한 다음 적절한 조직을 선택합니다.

1. **[내 프로그램](#my-programs)** 페이지에서 편집할 프로그램을 클릭하여 세부 정보를 표시합니다.

1. 페이지 왼쪽 상단에서 프로그램 이름을 클릭하고 **프로그램 삭제**&#x200B;를 선택합니다.

   ![프로그램 삭제 옵션](assets/delete-sandbox1.png)

또는 Cloud Manager 개요 페이지에서 프로그램 카드의 https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg을 클릭하고 **프로그램 삭제**&#x200B;를 선택할 수 있습니다.

![프로그램 카드의 샌드박스 삭제](assets/delete-sandbox2.png)

>[!NOTE]
>
>샌드박스 프로그램만 삭제할 수 있습니다. 프로덕션 프로그램은 삭제할 수 없습니다.
