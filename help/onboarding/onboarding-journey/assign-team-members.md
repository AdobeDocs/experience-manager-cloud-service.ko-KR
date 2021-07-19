---
title: 'Cloud Manager 제품 프로필에 팀 구성원 할당 '
description: 팀 구성원을 Cloud Manager 제품 프로필에 할당하는 방법을 알려면 이 페이지를 따르십시오.
hide: true
hidefromtoc: true
index: false
source-git-commit: ede12ce0b62056f6e11ebd3d40d2c995f8d70d52
workflow-type: tm+mt
source-wordcount: '1110'
ht-degree: 0%

---


# Cloud Manager 제품 프로필에 팀 구성원 할당 {#assign-team-members}

이제 Admin Console에 로그인하고 시스템 관리자로 권한을 보는 방법을 알게 되면 팀 구성원을 Cloud Manager 제품 프로필에 할당할 수 있습니다.

## 목표 {#objective}

이 문서에서는 Admin Console에서 Cloud Manager 제품 프로필에 팀 구성원을 할당하는 방법을 요약합니다.

이 섹션을 읽은 후에는 다음을 수행할 수 있습니다.

* 팀 구성원을 추가해야 하는 이유와 방법을 이해합니다.
* 비즈니스 소유자, 배포 관리자 및 개발자와 같은 세 가지 서로 다른 Cloud Manager 제품 프로필에 대해 알아봅니다.
* Cloud Manager 제품 프로필(비즈니스 소유자, 배포 관리자 및 개발자)에 팀 구성원을 할당합니다.

## Cloud Manager 제품 프로필 검토 {#review-product-profiles}

Admin Console에서 Cloud Manager 프로필 목록을 볼 수 있습니다.

>[!NOTE]
>Admin Console에서 Cloud Manager 제품 프로필을 검토하기 전에 사용 가능한 Cloud Manager 제품 프로필을 검토하는 것이 좋습니다.

Cloud Manager 프로필 목록을 보려면 아래 절차를 따르십시오.

1. Adobe Admin Console에 로그인합니다. **개요** 페이지의 제품 및 서비스 카드에서 Adobe Experience Manager as a Cloud Service를 선택하십시오.

   >[!NOTE]
   >Admin Console 사용 방법에 대해 알아보려면 Admin Console 로그인 을 참조하십시오.


1. 모든 인스턴스 목록이 있는 테이블에서 cloud manager 인스턴스로 이동합니다. 사전 구성된 Cloud Manager 제품 프로필 목록이 표시됩니다.


## 비즈니스 소유자 제품 프로필에 사용자 할당 {#assign-users-business-owner}

이제 사용자를 추가하고 Cloud Manager 비즈니스 소유자 제품 프로필에 할당할 준비가 되었습니다.

이렇게 하려면 Admin Console Adobe에서 제품(이 경우 Cloud Service으로 AEM) 및 Cloud Manager 비즈니스 소유자 제품 프로필에 사용자를 추가해야 합니다.

다음 단계는 이 단계를 안내합니다.

1. Cloud Manager 프로그램을 관리할 사용자를 식별하고 사용자를 비즈니스 소유자 제품 프로필에 추가합니다. 시스템 관리자가 Cloud Manager에 처음으로 액세스하여 로그인해야 합니다. 먼저 비즈니스 소유자 제품 프로필에 사용자(시스템 관리자)를 추가해야 합니다.

1. Admin Console 개요 페이지에서, 아래와 같이 제품 및 서비스 카드에서 Cloud Service 제품으로 Adobe Experience Manager 를 선택합니다.

1. 위쪽 탐색에서 사용자 탭을 선택한 다음 사용자 추가를 선택합니다.

1. 사용자 추가 대화 상자에서 추가할 사용자의 이메일 ID를 입력합니다. ID 유형에 대해 팀 구성원의 Federated ID이 아직 설정되지 않은 경우 Adobe ID 을 선택합니다.

1. 제품 선택에서 &#39;Adobe Experience Manager as a Cloud Service&#39;을 선택하고 아래 표시된 대로 사용자에게 &#39;비즈니스 소유자&#39; 제품 프로필을 할당합니다. 아래에서 보듯이 적절한 사용자에게 Admin Console에서 적절한 역할이 할당되었는지 확인하려면 Cloud Manager 제품 프로필을 참조하십시오.

1. 사용자가 Cloud Manager에 액세스할 수 있도록 사용자를 하나 이상의 제품 프로필에 할당합니다. &#39;비즈니스 소유자&#39;에 사용자(시스템 관리자)를 할당해야 합니다.

1. 저장을 클릭합니다. 추가한 사용자에게 환영 이메일이 전송됩니다. 초대받은 사용자는 환영 이메일에서 링크를 클릭하고 Adobe ID을 사용하여 로그인하여 Cloud Manager에 액세스할 수 있습니다.

축하합니다! 이제 &#39;비즈니스 소유자&#39; 역할에 지정된 자신을 포함하여 새롭게 구성된 Cloud Manager 팀이 설정되었습니다. 구성원은 로그인하여 Cloud Manager에 액세스할 수 있도록 초대하는 환영 이메일을 받게 됩니다. 비즈니스 소유자의 역할에서는 이제 Cloud Manager에 로그인하고 클라우드 리소스를 만들 수 있습니다.

## 배포 관리자에 사용자 할당 제품 프로필 {#assign-users-deployment-manager}

1. Cloud Manager 프로그램을 관리할 사용자를 식별하고 사용자를 비즈니스 소유자 제품 프로필에 추가합니다. 시스템 관리자가 Cloud Manager에 처음으로 액세스하여 로그인해야 합니다. 먼저 비즈니스 소유자 제품 프로필에 사용자(시스템 관리자)를 추가해야 합니다.

1. Admin Console 개요 페이지에서, 아래와 같이 제품 및 서비스 카드에서 Cloud Service 제품으로 Adobe Experience Manager 를 선택합니다.

1. 위쪽 탐색에서 사용자 탭을 선택한 다음 사용자 추가를 선택합니다.

1. 사용자 추가 대화 상자에서 추가할 사용자의 이메일 ID를 입력합니다. ID 유형에 대해 팀 구성원의 Federated ID이 아직 설정되지 않은 경우 Adobe ID 을 선택합니다.

1. 제품 선택에서 &#39;Adobe Experience Manager as a Cloud Service&#39;을 선택하고 아래 표시된 대로 사용자에게 &#39;배포 관리자&#39; 제품 프로필을 할당합니다. 아래에서 보듯이 적절한 사용자에게 Admin Console에서 적절한 역할이 할당되었는지 확인하려면 Cloud Manager 제품 프로필을 참조하십시오.

   >[!NOTE]
   >Cloud Manager 리소스를 만든 후 배포 관리자 제품 프로필에 사용자를 추가할 수 있습니다.

## 개발자 제품 프로필에 사용자 할당 {#assign-users-developer}

1. Cloud Manager 프로그램을 관리할 사용자를 식별하고 사용자를 비즈니스 소유자 제품 프로필에 추가합니다. 시스템 관리자가 Cloud Manager에 처음으로 액세스하여 로그인해야 합니다. 먼저 비즈니스 소유자 제품 프로필에 사용자(시스템 관리자)를 추가해야 합니다.

1. Admin Console 개요 페이지에서, 아래와 같이 제품 및 서비스 카드에서 Cloud Service 제품으로 Adobe Experience Manager 를 선택합니다.

1. 위쪽 탐색에서 사용자 탭을 선택한 다음 사용자 추가를 선택합니다.

1. 사용자 추가 대화 상자에서 추가할 사용자의 이메일 ID를 입력합니다. ID 유형에 대해 팀 구성원의 Federated ID이 아직 설정되지 않은 경우 Adobe ID 을 선택합니다.

1. 제품 선택에서 &#39;Adobe Experience Manager as a Cloud Service&#39;을 선택하고 아래 표시된 대로 &#39;개발자&#39; 제품 프로필을 사용자에게 할당합니다. 아래에서 보듯이 적절한 사용자에게 Admin Console에서 적절한 역할이 할당되었는지 확인하려면 Cloud Manager 제품 프로필을 참조하십시오.

   >[!NOTE]
   >Cloud Manager 리소스를 만든 후 개발자 제품 프로필에 사용자를 추가할 수 있습니다.

## 다음은 무엇입니까? {#whats-next}

*비즈니스 소유자* 역할에 지정된 시스템 관리자는 Cloud Manager에 액세스하여 로그인해야 합니다.
>[!NOTE]
>Cloud Manager에 로그인하고 액세스하는 방법에 대해 알아보려면 Cloud Manager 탐색 을 참조하십시오.

비즈니스 소유자 역할의 Cloud Manager 사용자는 프로그램 및 환경을 포함하여 클라우드 리소스에 로그인하고 설정할 수 있습니다. 이렇게 하면 전문가 팀이 가능한 한 빨리 AEM에 Cloud Service으로 액세스할 수 있습니다.
비즈니스 소유자가 클라우드 리소스를 설정한 후 Cloud Manager 제품 프로필에 성공적으로 추가된 개발자 및 배포 관리자는 Cloud Manager에 액세스하여 학습 경로를 계속 진행할 수 있는 방법에 대해 숙지할 수 있습니다.

## 추가 리소스 {#additional-resources}

추가 리소스에 따라 다음 사항에 대해 자세히 알아보십시오.

* Cloud Manager
* Cloud Manager 제품 프로필
* Admin Console ID 개요
