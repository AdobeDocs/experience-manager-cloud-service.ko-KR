---
title: '사용자 추가 및 클라우드 관리자 역할 할당 '
description: 사용자를 추가하고 Cloud Manager 역할에 할당하는 방법을 알려면 이 페이지를 따르십시오
translation-type: tm+mt
source-git-commit: 6e8cf08ec3f85437a8472a45895f3818e473e98c
workflow-type: tm+mt
source-wordcount: '818'
ht-degree: 4%

---


# 사용자 추가 및 클라우드 관리자 역할 할당 {#add-users-assign}

Adobe은 IMS(Adobe Identity Management System)에서 회사에 대한 **조직** 식별자를 만들어 모든 사용자와 해당 권한을 관리할 수 있습니다. 이 조직의 구성원이 되어야 하고 [!UICONTROL Experience Cloud] 서비스에 대한 액세스 권한을 받는 각 사용자는 자신의 **Adobe ID**&#x200B;을(를) 가지고 있어야 합니다.

## 사용자 역할 이해 {#user-roles}

Cloud Manager의 많은 기능을 사용하려면 특정 권한이 필요합니다.

Cloud Manager는 현재 특정 기능의 가용성을 제어하는 4개의 역할을 정의합니다.

* 비즈니스 소유자
* 배포 관리자
* 프로그램 관리자
* 개발자

>[!NOTE]
>Admin Console의 개발자 모습은 [!UICONTROL 클라우드 관리자]의 개발자 역할과 관련이 없습니다.

다음 표에 역할이 요약되어 있습니다.

| [!UICONTROL 클라우드 ] 관리자 역할 | 설명 |
|--- |--- |
| 비즈니스 소유자 | KPI 정의, 제작 배포 승인 및 중요한 3-계층 오류 덮어쓰기에 대한 책임입니다. |
| 프로그램 관리자 | [!UICONTROL 클라우드 관리자]를 사용하여 팀 설정을 수행하고, 상태를 검토하고 KPI를 봅니다. 중요한 3-계층 오류를 승인할 수 있습니다. |
| 배포 관리자 | 배포 작업을 관리합니다. [!UICONTROL 클라우드 관리자]를 사용하여 스테이지/프로덕션 배포를 실행합니다. CI/CD 파이프라인을 편집할 수 있습니다. 중요한 3-계층 오류를 승인할 수 있습니다. Git 리포지토리에 액세스할 수 있습니다. |
| 개발자 | 사용자 정의 응용 프로그램 코드를 개발하고 테스트합니다. 주로 [!UICONTROL 클라우드 관리자]를 사용하여 상태를 봅니다. 코드 커밋을 위해 Git 리포지토리에 액세스할 수 있습니다. |
| 컨텐츠 작성자 | 일반적으로 [!UICONTROL 클라우드 관리자]와 상호 작용하지 않습니다. [!UICONTROL 클라우드 관리자] 프로그램 전환기([!UICONTROL Experience Cloud]에서 이동)를 사용하여 AEM에 액세스할 수 있습니다. |

### 통합 제품 프로필 {#integration-product-profile}

위의 내용 외에도 Cloud Manager는 &quot;통합 - Cloud Service&quot;라는 제품 프로필을 자동으로 생성합니다. 이 제품 프로필은 Adobe Experience Manager과 다른 Adobe 제품 간의 통합에 사용됩니다. 이 제품 프로필 **은(는)**&#x200B;을(를) 삭제할 수 없습니다. 이 프로필을 실수로 삭제한 경우에는 수동으로 다시 만들어야 합니다. 이 프로필 **의 표시 이름은**&#x200B;이(가) `CM_CS_DEFAULT`여야 합니다.


## 역할 정의와 연결된 권한 {#permissions}

[!UICONTROL Cloud Manager에는 적절한 권한이 있는 미리 구성된 역할이 있습니다. ] 예를 들어 개발자는 코드를 개발하고 **Git 리포지토리**&#x200B;에 코드를 푸시할 권한이 있습니다. 또는 비즈니스 소유자는 KPI(Key Performance Indicator)를 정의하고 배포를 승인할 수 있는 다양한 권한을 갖습니다.

각 역할에는 각 역할과 연관된 특정 권한이 있습니다. 다음 표는 역할을 요약하고 사용 가능한 함수 및 함수를 실행할 수 있는 역할을 나열합니다.

| 권한 | 설명 | 비즈니스 소유자 | 배포 관리자 | 프로그램 관리자 | 개발자 |
|--- |--- |--- |--- |--- |--- |
| 프로그램 추가 | 새 프로그램 추가를 참조하십시오. | x |  |  |  |
| 환경 만들기 | Prod+Stage, Dev, Environment를 작성합니다. | x | x |  |  |
| 환경 업데이트 | Prod+Stage, Dev, 환경을 업데이트합니다. | x | x |  |  |
| 환경 삭제 | 비제품, 개발, 환경 삭제를 참조하십시오. | x | x |  |  |
| 파이프라인 설정 | 파이프라인 설정 또는 편집을 참조하십시오. |  | x |  |  |
| 파이프라인 실행 | 파이프라인을 시작합니다. | x | x |  |  |
| 파이프라인 실행 | 중요한 3계층 오류 거부/승인 | x | x | x |  |
| 파이프라인 실행 | GoLive 승인을 제공합니다. | x | x | x |  |
| 파이프라인 실행 | 프로덕션 배포 일정을 참조하십시오. | x | x | x |  |
| 파이프라인 삭제 | 파이프라인 삭제를 허용합니다. |  | x |  |  |
| 실행 취소 | 현재 실행 취소를 참조하십시오. |  | x |  |  |
| 개인 액세스 토큰 생성 | Git 액세스. |  | x |  | x |

## 사용자 {#add-users} 추가

>[!NOTE]
>사용자를 추가하려면 시스템 관리자여야 합니다.

1. 시스템 관리자인 경우 [Admin Console](https://adminconsole.adobe.com)으로 이동합니다. 또는 아래 설명에 따라 Cloud Manager로 이동하여 **액세스 관리** 단추를 볼 수도 있습니다.

1. 클라우드 관리자 랜딩 페이지의 오른쪽 상단에 있는 **액세스 관리** 단추를 클릭하여 새 탭에서 Admin Console을 엽니다.

   ![](/help/onboarding/getting-access-to-aem-in-cloud/assets/sys-admin5.png)

   **Admin Console**&#x200B;에서 사용자를 클라우드 관리자에 추가하고 Admin Console의 제품 프로필이라고 하는 역할에 할당할 수 있습니다.

1. 아래 표시된 대로 **제품 및 서비스** 카드에서 **Adobe Experience Manager을 Cloud Service**&#x200B;으로 선택합니다.

   ![](/help/onboarding/what-is-required/assets/admin-console-1.png)

1. 작업 표시줄에서 **사용자** 탭을 선택한 다음 **사용자 추가**&#x200B;를 선택합니다.

   ![](/help/onboarding/what-is-required/assets/admin-console-2.png)

1. 사용자를 선택하고 아래에서 보듯이 사용자에게 적절한 클라우드 관리자 역할 또는 제품 프로필을 할당합니다.

   ![](/help/onboarding/what-is-required/assets/admin-console-3.png)

   >[!NOTE]
   >**Admin Console**&#x200B;에서 오른쪽 사용자에게 올바른 역할이 할당되었는지 확인하려면 [사용자 역할 및 권한](#user-roles) 및 역할 정의와 연결된 [권한](#permissions)을 참조하십시오.

   이제 사용자가 Cloud Service 제품 컨텍스트로 Adobe Experience Manager에 추가되었으며 올바른 역할 또는 제품 프로필로 설정됩니다.

   예를 들어 다음 역할의 경우

   * ***비즈니스 소유자는 새 프로그램 추가*** 또는 프로그램 편집, 환경을 추가 또는 업데이트, 파이프라인을 추가/편집/삭제 및 실행하고 코드를 AEM 환경 또는 코드 품질에 배포할 수 있는 권한이 있습니다.

   * ***배포 관리자는*** 환경을 추가 또는 업데이트하고 파이프라인을 실행하며 코드를 AEM 환경 또는 코드 품질에 배포할 수 있는 권한이 있습니다.

   * ***개발자***, Git에 액세스할 수 있는 개인 액세스 토큰을 생성할 권한이 있습니다.

      >[!NOTE]
      > 사용자를 여러 역할에 할당할 수 있습니다. 예를 들어 사용자에게 비즈니스 소유자와 배포 관리자 역할을 모두 할당하면 이러한 권한의 조합이나 합계에 도움을 줍니다.
