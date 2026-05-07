---
title: 프로그램 편집
description: 프로덕션 및 샌드박스 프로그램을 만든 후 옵션을 조정하도록 편집하는 방법을 알아봅니다.
exl-id: 819e4a6e-f77a-4594-a402-a300dcbdf510
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Developer
source-git-commit: 1c42dff8efb505d050583c8af2f150a7f862d8c9
workflow-type: tm+mt
source-wordcount: '989'
ht-degree: 18%

---


# 프로그램 편집 {#editing-programs}

프로그램을 관리하고 편집하려면 [**내 프로그램** 콘솔](/help/implementing/cloud-manager/navigation.md)에서 시작하십시오. **내 프로그램** 페이지에서는 액세스 권한이 있는 모든 프로그램에 대한 개요를 제공합니다. 개별 프로그램을 선택할 때 **프로그램 개요** 페이지에서 프로그램 세부 정보에 대한 개요를 제공합니다.

**프로그램 개요**&#x200B;에서 필수 권한이 있는 사용자는 [조직에서 만든 프로덕션 프로그램](creating-production-programs.md) 및 [조직에서 만든 샌드박스 프로그램](creating-sandbox-programs.md)을 편집할 수 있습니다. 프로그램을 편집하여 다음 작업을 수행할 수 있습니다.

* Assets가 있는 기존 프로그램에 Sites 솔루션을 추가하며, 이와 반대도 마찬가지입니다.
* Sites 및 Assets이 모두 있는 기존 프로그램에서 Sites 또는 Assets을 제거합니다.
* 기존 프로그램에 미사용 솔루션 권한을 추가하거나 새 프로그램을 만듭니다.
* 프로덕션 프로그램에 삭제 표시를 합니다.
* 샌드박스 프로그램을 삭제합니다.

## 권한 {#permissions}

프로그램을 편집하고, 샌드박스 프로그램을 삭제하고, 프로덕션 프로그램을 삭제하도록 표시하고, 라이선스 대시보드에 액세스하려면 **비즈니스 소유자** 역할이 있어야 합니다.

## 프로그램 편집 {#editing}

솔루션 또는 추가 기능 추가 또는 제거를 포함하여 프로그램을 편집할 때마다 이러한 변경 사항은 다음 배포 이후에 적용됩니다.

**프로그램을 편집하려면:**

1. [experience.adobe.com](https://experience.adobe.com)에서 Cloud Manager에 로그인합니다.
1. **바로 가기** 섹션에서 **Experience Manager**&#x200B;를 클릭합니다.
1. 왼쪽 사이드 패널에서 **Cloud Manager**&#x200B;를 클릭합니다.
1. 적절한 조직을 선택합니다.
1. **내 프로그램** 페이지에서 편집할 프로그램을 클릭합니다.
1. 페이지의 왼쪽 상단 모서리에서 프로그램 이름을 클릭한 다음 **프로그램 편집**&#x200B;을 선택합니다.

   ![프로그램 드롭다운 메뉴의 프로그램 편집 옵션](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/assets/edit-program.png)

1. **프로그램 편집** 대화 상자에서 탭을 사용하여 원하는 다양한 옵션을 설정합니다.

   ![일반 탭](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/assets/edit-program-dialog-box.png)

   프로그램 편집에 사용할 수 있는 옵션은 프로그램 만들기에 사용할 수 있는 옵션과 동일합니다.
   * 게시 계층이 새 환경(Beta)에 대해 프로비저닝되는지 여부를 구성할 수 있습니다. [유연한 게시 계층(Beta)](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-production-programs.md#flexible-publish-tier)을 참조하십시오.
   * 개별 옵션에 대한 자세한 내용은 [프로덕션 프로그램 만들기](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-production-programs.md) 및 [샌드박스 프로그램 만들기](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-sandbox-programs.md)를 참조하십시오.
   * 조직의 권한에 따라 프로덕션 프로그램에 [추가 옵션](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-production-programs.md#options)을 사용할 수 있습니다.

1. **업데이트**&#x200B;를 클릭하여 변경 내용을 저장합니다.

## 프로덕션 프로그램에 삭제 표시 {#delete-production-program}

프로덕션 프로그램 삭제는 2단계 프로세스입니다. 비즈니스 소유자는 프로그램에 삭제 표시를 하여 유효성 검사 및 폐기 기간을 트리거합니다. 그런 다음 중단 기간이 경과하면 프로그램이 영구적으로 제거됩니다.

프로덕션 프로그램이 삭제 표시된 경우 다음 오류가 발생합니다.

* 프로덕션 프로그램과 관련된 크레딧이 고객에게 반환됩니다.
* 프로덕션 프로그램에 속하는 모든 환경이 중단됩니다.

삭제 표시가 시작되기 전에 시스템은 프로덕션 프로그램이 삭제 자격이 있는지 확인합니다. 표시에 실패하면 프로덕션 프로그램이 대신 `Failed to mark for deletion` 상태로 이동합니다.

>[!NOTE]
>
>샌드박스 프로그램은 이 프로세스의 영향을 받지 않습니다. 샌드박스 프로그램을 삭제하려면 [샌드박스 프로그램 삭제](#delete-sandbox-program)를 참조하십시오.

**프로덕션 프로그램을 삭제하도록 표시하려면:**

1. [experience.adobe.com](https://experience.adobe.com)에서 Cloud Manager에 로그인합니다.
1. **바로 가기** 섹션에서 **Experience Manager**&#x200B;를 클릭합니다.
1. 왼쪽 사이드 패널에서 **Cloud Manager**&#x200B;를 클릭합니다.
1. 적절한 조직을 선택합니다.
1. **내 프로그램** 페이지에서 삭제로 표시할 프로덕션 프로그램의 경우 ![추가 아이콘](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg)을 클릭한 다음 **프로그램 삭제**&#x200B;를 클릭합니다.

   ![프로덕션 프로그램의 드롭다운 목록에서 프로그램 삭제를 선택합니다&#x200B;](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/assets/production-program-markfordelete1.png)*위에 표시된 프로덕션 프로그램 예는 일러스트레이션 목적으로만 사용됩니다.*

1. **프로덕션 프로그램에 삭제 표시** 대화 상자에서 프로덕션, 스테이징 및 개발 환경을 포함하여 프로그램에 연결된 리소스를 나열하는 경고를 검토합니다.

   ![프로덕션 프로그램 삭제 대화 상자](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/assets/production-program-markfordelete2.png)


   >[!NOTE]
   >
   >프로덕션 프로그램에 현재 업데이트 중인 환경과 같은 차단 리소스가 있는 경우 **삭제 표시** 단추가 비활성화됩니다. 프로그램을 삭제하도록 표시하기 전에 모든 프로그램 리소스가 잠금 해제될 때까지 기다립니다.
   >
   >![프로덕션 프로그램에 차단 리소스가 있기 때문에 프로그램을 삭제할 수 없음을 표시하는 삭제 표시 대화 상자](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/assets/production-program-markfordelete2b.png)


1. 확인하려면 대화 상자에 표시된 프로그램 이름을 입력한 다음 **삭제 표시**&#x200B;를 클릭합니다.

   확인 후 프로세스가 실행되는 동안 프로덕션 프로그램에 **삭제 표시** 상태가 표시됩니다.

   ![삭제 상태를 표시](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/assets/production-program-markfordelete3.png)

   완료되면 프로덕션 프로그램 카드가 연결된 경고 배지와 함께 **삭제 표시**(으)로 업데이트됩니다.

   ![연결된 경고 배지가 있는 삭제 상태로 표시됨](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/assets/production-program-markfordelete4.png)

1. 프로덕션 프로그램 카드에서 경고 배지를 클릭하여 예약된 영구 제거 날짜를 표시합니다.

   ![프로덕션 프로그램의 예약된 영구 제거 날짜를 표시합니다](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/assets/production-program-markfordelete5.png)

   중단 기간이 경과하면 프로그램이 영구적으로 제거되며 복원할 수 없습니다.

### 프로덕션 프로그램을 삭제 표시 해제 {#unmark-from-deletion}

영구 제거가 아직 발생하지 않는 한 삭제하도록 *표시*&#x200B;된 프로덕션 프로그램을 복원할 수 있습니다.

>[!IMPORTANT]
>
>삭제로 표시된 프로덕션 프로그램을 복원하려면 고객이 사용 가능한 크레딧을 보유하고 있어야 합니다.

**프로덕션 프로그램을 삭제에서 선택 해제하려면:**

1. **내 프로그램** 페이지에서 **삭제 표시**&#x200B;를 표시하는 프로덕션 프로그램 카드를 찾습니다.

1. 프로덕션 프로그램 카드에서 ![기타 아이콘](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg)을 클릭한 다음 **삭제 표시 해제**&#x200B;를 클릭합니다.

   ![프로덕션 프로그램의 예약된 영구 제거 날짜를 표시 취소](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/assets/production-program-unmarkfordelete6.png)

   프로덕션 프로그램에는 삭제 표시가 없습니다.

## 샌드박스 프로그램 삭제 {#delete-sandbox-program}

샌드박스 프로그램을 삭제하면 관련된 모든 환경 및 파이프라인이 제거됩니다.

>[!TIP]
>
>**비즈니스 소유자** 또는 **배포 관리자** 역할이 있는 사용자는 전체 샌드박스 프로그램 대신 프로덕션 및 스테이징 환경을 삭제할 수 있습니다.

**샌드박스 프로그램을 삭제하려면:**

1. [experience.adobe.com](https://experience.adobe.com)에서 Cloud Manager에 로그인합니다.
1. **바로 가기** 섹션에서 **Experience Manager**&#x200B;를 클릭합니다.
1. 왼쪽 사이드 패널에서 **Cloud Manager**&#x200B;를 클릭합니다.
1. 적절한 조직을 선택합니다.

1. **[내 프로그램](#my-programs)** 페이지에서 편집할 샌드박스 프로그램을 클릭하여 세부 정보를 표시합니다.

1. 페이지 왼쪽 상단에서 샌드박스 프로그램 이름을 클릭하고 **프로그램 삭제**&#x200B;를 선택합니다.

   ![프로그램 삭제 옵션](assets/delete-sandbox1.png)

또는 Cloud Manager 개요 페이지에서 샌드박스 프로그램 카드의 ![추가 아이콘](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg)을 클릭하고 **프로그램 삭제**&#x200B;를 선택할 수 있습니다.

![프로그램 카드의 샌드박스 삭제](assets/delete-sandbox2.png)
