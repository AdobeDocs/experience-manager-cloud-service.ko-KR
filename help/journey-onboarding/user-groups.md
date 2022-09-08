---
title: 알림에 대한 사용자 그룹
description: Admin Console에서 사용자 그룹을 만들어 중요한 이메일 알림 수신 기능을 관리하는 방법을 알아봅니다.
feature: Onboarding
role: Admin, User, Developer
source-git-commit: a663e21d100953f87c012a1d7962fb0e88e6a7f2
workflow-type: tm+mt
source-wordcount: '770'
ht-degree: 1%

---


# 알림에 대한 사용자 그룹 {#user-groups}

Admin Console에서 사용자 그룹을 만들어 중요한 이메일 알림 수신 기능을 관리하는 방법을 알아봅니다.

## 개요 {#overview}

때때로 Adobe은 AEM as a Cloud Service 환경에 대해 문의해야 합니다. Adobe은 제품 내 알림 외에도 가끔 이러한 알림에 이메일을 사용합니다. 이러한 알림에는 두 가지 유형이 있습니다.

* **인시던트 알림 - Cloud Service** - 이러한 알림은 사고 중 또는 Adobe이 AEM as a Cloud Service 환경에서 발생할 수 있는 가용성 문제를 확인한 경우 전송됩니다.
* **사전 알림 - Cloud Service** - 이러한 알림은 Adobe 지원 팀 구성원이 AEM as a Cloud Service 환경에 도움이 될 수 있는 잠재적인 최적화 또는 권장 사항에 대한 지침을 제공하려는 경우 전송됩니다.

올바른 사용자가 이러한 알림을 받으려면 사용자 그룹을 구성해야 합니다.

## 사전 요구 사항 {#prerequisites}

사용자 그룹은 Admin Console에서 생성 및 유지 관리되므로 알림에 대한 사용자 그룹을 생성하기 전에 다음을 수행해야 합니다.

* 그룹 멤버십을 추가 및 편집할 수 있는 권한이 있습니다.
* 유효한 Adobe Admin Console 프로필이 있습니다.

## 새 Cloud Manager 제품 프로필 만들기 {#create-groups}

알림 수신을 제대로 설정하려면 두 개의 사용자 그룹을 만들어야 합니다. 이러한 단계는 한 번만 수행해야 합니다.

1. Admin Console에 로그인합니다. [`https://adminconsole.adobe.com`.](https://adminconsole.adobe.com)

1. 에서 **개요** 페이지를 선택하고 **Adobe Experience Manager as a Cloud Service** 에서 **제품 및 서비스** 카드.

   ![사용자 그룹](assets/products_services.png)

1. 로 이동합니다 **Cloud Manager** 모든 인스턴스 목록에서 인스턴스를 생성합니다.

   ![사용자 그룹 만들기](assets/cloud_manager_instance.png)

1. 구성된 모든 Cloud Manager 제품 프로필 목록이 표시됩니다. 예:

   ![사용자 그룹 만들기](assets/cloud_manager_profiles.png)

1. 새 프로필 을 클릭하고 다음 세부 정보를 제공합니다.

* 제품 프로필 이름: 인시던트 알림 - Cloud Service
* 표시 이름: 인시던트 알림 - Cloud Service
* 설명: 인시던트 중에 알림을 받을 사용자 또는 Adobe이 AEM as a Cloud Service 환경에서 잠재적인 가용성 문제를 확인한 사용자의 Cloud Manager 프로필입니다.

1. 저장 을 클릭하고 다음 세부 정보를 사용하여 4단계를 반복합니다.

* 제품 프로필 이름: 사전 알림 - Cloud Service
* 표시 이름: 사전 알림 - Cloud Service
* 설명: Adobe 지원 팀 구성원이 AEM as a Cloud Service 환경 구성으로 수행할 잠재적 최적화 또는 권장 사항에 대한 지침을 제공하려고 할 때 알림을 받을 사용자를 위한 Cloud Manager 프로필입니다.

>[!NOTE]
>
>Cloud Manager 프로필 이름이 위와 정확히 같아야 합니다. 제공된 설명에서 제품 프로필 이름을 복사하여 붙여 넣으십시오. 임의 편차나 오타가 원하는 대로 알림이 전송되지 않습니다. 오류가 발생하거나 프로필이 정의되지 않은 경우, Adobe은 기본적으로 Cloud Manager 개발자(즉, 또는, 및) 배포 관리자 프로필에 할당된 기존 사용자를 알려줍니다.

## 새 알림 제품 프로필에 사용자 할당 {#add-users}

그룹이 생성되었으므로 적절한 사용자를 할당해야 합니다. 새 사용자를 만들거나 기존 사용자를 업데이트하여 이 작업을 수행할 수 있습니다.

### 그룹에 새 사용자 추가 {#new-user}

1. 인시던트 또는 사전 알림을 받아야 하는 사용자를 식별합니다.

1. Admin Console에 로그인합니다. [`https://adminconsole.adobe.com`](https://adminconsole.adobe.com) 아직 로그인하지 않은 경우

1. 에서 **개요** 페이지를 선택하고 **Adobe Experience Manager as a Cloud Service** 에서 **제품 및 서비스** 카드.

   ![사용자](assets/product_services.png)

1. 을(를) 선택합니다 **사용자** 위쪽 탐색에서 tab 키를 누른 다음 을 선택합니다 **사용자 추가**.

![사용자](assets/cloud_manager_add_user.png)

1. 팀에 사용자 추가 대화 상자에서 추가할 사용자의 이메일 ID를 입력합니다.

* 팀 구성원의 페더레이션 ID가 아직 설정되지 않은 경우 ID 유형에 대해 Adobe ID 을 선택합니다.
* 사용자가 이미 존재하는 경우 7단계를 참조하십시오.

1. 아래의 더하기 단추를 클릭합니다. **제품 선택** 제품 선택을 시작하고 을(를) 선택합니다. **Adobe Experience Manager as a Cloud Service** 다음 중 하나를 지정합니다. **인시던트 알림 - Cloud Service** 또는 **사전 알림 - Cloud Service**&#x200B;또는 둘 다 사용자에게 할당할 수 있습니다.

1. 클릭 **저장** 추가한 사용자에게 환영 이메일이 전송됩니다. 이제 초대된 사용자가 알림을 받게 됩니다.

1. 팀의 사용자에게 알림을 받을 수 있도록 이 단계를 반복합니다.

1. 사용자가 이미 존재하는 경우 사용자의 이름을 검색하고 다음을 수행합니다.

* 사용자 이름을 클릭합니다.
* 에서 **제품** 섹션을 클릭합니다. **편집**.
* 연필 단추를 클릭합니다. **제품 선택** 제품 선택을 시작하고 을(를) 선택합니다. **Adobe Experience Manager as a Cloud Service** 다음 중 하나를 지정합니다. **인시던트 알림 - Cloud Service** 또는 **사전 알림 - Cloud Service**&#x200B;또는 둘 다 사용자에게 할당할 수 있습니다.
* 클릭 **저장** 추가한 사용자에게 환영 이메일이 전송됩니다. 이제 초대된 사용자가 알림을 받게 됩니다.
