---
title: Adobe Experience Manager에서 AI Assistant 구성
description: Adobe Experience Manager의 Admin Console을 사용하여 AI Assistant를 설정하고 구성하는 방법에 대해 알아봅니다.
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
hide: true
hidefromtoc: true
exl-id: a7f3dc14-29f7-473a-9870-d52393e6fa6e
source-git-commit: e853e7b46c762ab724d5eecb344897a83e4fb724
workflow-type: tm+mt
source-wordcount: '950'
ht-degree: 3%

---

# Adobe Experience Manager에서 AI Assistant 구성 {#aem-ai-asst-admin-setup}

조직의 사용자가 AEM(Adobe Experience Manager) AI Assistant의 기능을 사용하려면 관리자가 액세스, 권한 및 설정을 구성해야 합니다.

AEM AI Assistant의 구성 프로세스는 다음 단계로 구성됩니다.

1. [Adobe Admin Console에서 새 제품 프로필을 만듭니다](#create-profile).
1. [AI Assistant 제품 지식 사용 권한](#enable-permission).
1. [새 사용자 그룹을 만들거나 기존 사용자 그룹을 사용](#create-user-group)합니다.
1. [사용자 그룹에 사용자 추가](#add-users).
1. [사용자 그룹에 제품 프로필을 할당](#assign-product-profile).

**사전 요구 사항**

시작하기 전에 다음 전제 조건을 충족했는지 확인하십시오.

* Adobe Admin Console에서 최소한 제품 관리자 권한이 있어야 합니다.
* 조직의 사용자 관리 구조를 이해하고 있습니다.

**구성 고려 사항**

* 처리 시간: Cloud Manager에서 만든 리소스가 권한 구성을 위해 Admin Console에 표시되는 데 최대 2분이 걸릴 수 있습니다.
* 여러 프로필: 사용자는 여러 프로필에 속할 수 있으며 할당된 모든 프로필에서 권한이 결합됩니다.
* 조직 범위: 일부 권한은 모든 프로그램에 대해 조직 수준에서 적용될 수 있습니다.
* 사전 정의된 프로필: Admin Console에서 사전 정의된 권한 프로필을 삭제하지 마십시오.


## 1 - Adobe Admin Console에서 새 제품 프로필 만들기{#create-profile}

1. Experience Platform 설명서에 있는 [Adobe Admin Console에서 새 제품 프로필 만들기](https://experienceleague.adobe.com/ko/docs/experience-platform/access-control/ui/create-profile)의 자세한 지침을 따르십시오.

1. 새 제품 프로필을 만들 때 AI Assistant에 대해 다음과 같이 제안된 값을 사용할 수 있습니다.

   | 텍스트 필드 | 제안 값 |
   | --- | --- |
   | 제품 프로필 이름 | `AEM AI Assistant`(또는 선호하는 설명 이름) |
   | 표시 이름(선택 사항) | `AI Assistant` |
   | 설명(선택 사항) | `Product profile for managing AEM AI Assistant access` |
   | 알림 | 조직의 기본 설정을 기반으로 구성 |


## 2 - AI Assistant 제품 지식 권한 활성화{#enable-permission}

제품 프로필에 사용자 지정 권한을 할당하는 프로세스는 표준 Adobe Cloud Manager 사용자 지정 권한 워크플로우를 따릅니다.

참조 문서: [새 제품 프로필에 사용자 지정 권한 할당](https://experienceleague.adobe.com/ko/docs/experience-manager-cloud-manager/content/requirements/custom-permissions#assign-permissions)

1. Admin Console에서 새로 만든 제품 프로필의 이름(`AEM AI Assistant`)을 클릭합니다

   ![스크린샷](/help/implementing/cloud-manager/assets/ai-assistant-console.png)

1. 편집 가능한 사용 권한 목록을 보려면 **사용 권한** 탭을 클릭하십시오.

1. 테이블 목록에서 `AI Assistant Product Knowledge` 권한을 찾습니다.

   Admin Console의 ![AI Assistant 권한 탭](/help/implementing/cloud-manager/assets/ai-assistant-permission.png)

1. 권한 이름 오른쪽에서 ![연필 아이콘 또는 편집 아이콘](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Edit_18_N.svg)을 클릭합니다.

1. **AI Assistant에 대한 권한 편집** 페이지에서 **AI Assistant 제품 지식** 토글을 켭니다.

   ![AI Assistant 제품 지식 토글 옵션의 권한 페이지 편집](/help/implementing/cloud-manager/assets/ai-assistant-prod-knowledge.png)

1. 페이지의 오른쪽 아래 모서리에서 **저장**&#x200B;을 클릭합니다.

   이제 제품 프로필에 AI Assistant 제품 지식 권한이 활성화되어 있습니다.


## 3 - 새 사용자 그룹 만들기(또는 기존 사용자 그룹 사용){#create-user-group}

1. 다음 중 하나를 수행하십시오.

>[!BEGINTABS]

>[!TAB 새 사용자 그룹 만들기]

1. Admin Console에서 **사용자** > **사용자 그룹**&#x200B;을 클릭합니다.

   ![사용자 그룹](/help/implementing/cloud-manager/assets/ai-assistant-user-groups.png)

1. **사용자 그룹** 페이지에서 **새 사용자 그룹**&#x200B;을 클릭합니다.

   ![사용자 그룹 페이지의 새 사용자 그룹 단추](/help/implementing/cloud-manager/assets/ai-assistant-new-user-group.png)

1. **새 사용자 그룹 만들기** 페이지에서 다음 정보를 제공합니다.

   | 옵션 | 제안 값 |
   | --- | --- |
   | 사용자 그룹 이름 | `AEM AI Assistant`(또는 기본 설정 이름) |
   | 설명(선택 사항) | `User group for managing AEM AI Assistant access` |

   ![새 사용자 그룹 페이지 만들기](/help/implementing/cloud-manager/assets/ai-assistant-create-new-user-group.png)

1. 페이지의 오른쪽 아래 모서리에서 **저장**&#x200B;을 클릭합니다.

>[!TAB 기존 사용자 그룹 사용]

새 그룹을 만드는 대신 AI Assistant 액세스 요구 사항을 충족하면 기존 AEM 사용자 그룹을 사용할 수 있습니다.

>[!ENDTABS]

## 4 - 사용자 그룹에 사용자 추가{#add-users}

1. 다음 중 하나를 수행하십시오.

>[!BEGINTABS]

>[!TAB 개별 사용자 추가]

1. **사용자 그룹** 페이지의 **그룹 이름** 테이블에서 새로 만든 사용자 그룹 이름이나 기존 사용자 그룹 이름을 클릭합니다.

   ![테이블에 AEM AI Assistant 사용자 그룹 이름을 표시하는 사용자 그룹 페이지](/help/implementing/cloud-manager/assets/ai-assistant-user-group-name-in-table.png)

1. **AEM AI Assistant**&#x200B;의 **사용자 그룹** 페이지에서 **사용자** 탭을 클릭한 다음 **사용자 추가**&#x200B;를 클릭합니다.

   ![AEM AI Assistant 사용자 그룹 페이지에 [사용자] 탭과 [사용자 추가] 단추가 표시됩니다](/help/implementing/cloud-manager/assets/ai-assistant-add-users.png)

1. **`Add users to this user group`** 페이지에서 AEM AI Assistant에 액세스해야 하는 사용자를 검색하고 선택합니다.

   ![이 사용자 그룹 페이지에 사용자 추가](/help/implementing/cloud-manager/assets/ai-assistant-add-users-to-this-group.png)

1. 페이지의 오른쪽 아래 모서리에서 **저장**&#x200B;을 클릭합니다.
1. 이제 사용자 그룹에 제품 프로필을 #assign-product-profile.

>[!TAB 일괄 사용자 추가]

Admin Console에서 일괄 업로드 기능을 사용할 수 있습니다.

1. 사용자 정보가 포함된 CSV 파일을 준비합니다.
1. 대량 추가를 효율적으로 수행하려면 **`Add users by CSV`** 옵션을 사용하십시오.
1. 이제 사용자 그룹에 제품 프로필을 #assign-product-profile.

>[!ENDTABS]


## 5 - 사용자 그룹에 제품 프로필 할당{#assign-product-profile}

이 단계는 사용자 그룹에 제품 프로필을 할당하기 위한 표준 Adobe Admin Console 워크플로를 따릅니다.

참조 문서: [Enterprise 사용자의 제품 프로필 관리](https://helpx.adobe.com/kr/enterprise/using/manage-product-profiles.html)

1. [4 - 사용자 그룹에 사용자 추가](#add-users)에서 AEM AI Assistant 사용자 그룹에 있는 동안 **할당된 제품 프로필** 탭을 클릭하십시오.
1. **프로필 할당**&#x200B;을 클릭합니다.

   ![할당된 제품 프로필 탭이 선택된 AEM AI Assistant 사용자 그룹 페이지](/help/implementing/cloud-manager/assets/ai-assistant-assign-profile.png)

1. **제품 및 프로필 할당** 페이지의 **제품 프로필 선택** 대화 상자에서 **AI Assistant** 제품 프로필을 검색하여 선택하십시오.

   ![제품 및 프로필 할당 페이지에서 &quot;제품 프로필 선택&quot; 대화 상자와 &quot;AI Assistant&quot; 제품 프로필을 선택함](/help/implementing/cloud-manager/assets/ai-assistant-select-product-profile.png)

1. 대화 상자의 오른쪽 아래 모서리에서 **적용**&#x200B;을 클릭합니다.
1. **제품 및 프로필 할당** 페이지의 오른쪽 아래 모서리에서 **저장**&#x200B;을 클릭합니다.

   ![표시된 AI Assistant 제품 프로필이 AEM AI Assistant 사용자 그룹에 할당되었습니다](/help/implementing/cloud-manager/assets/ai-assistant-profile-assigned-to-user-group.png)


## 구성 확인

* 제품 프로필에 할당된 사용자 그룹의 올바른 수가 표시되는지 확인합니다.
* 사용자 그룹에 올바른 사용자 수가 표시되는지 확인합니다.
* AI Assistant 제품 지식 권한이 활성화되고 올바르게 구성되었는지 확인합니다.


## 구성 테스트

할당된 그룹의 사용자가 다음 작업을 수행하도록 합니다.

1. AEM에 로그인합니다.
2. AI Assistant 기능에 액세스할 수 있는지 확인합니다.
3. AI Assistant의 기능을 테스트하여 제대로 활성화되었는지 확인합니다.

## 추가 참조

* [Adobe Experience Platform 액세스 제어](https://experienceleague.adobe.com/ko/docs/experience-platform/access-control/ui/overview)
* [Cloud Manager 사용자 지정 권한](/help/implementing/cloud-manager/custom-permissions.md)


