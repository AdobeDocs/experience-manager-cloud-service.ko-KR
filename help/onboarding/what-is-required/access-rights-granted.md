---
title: 액세스 권한 부여됨 - 필요한 사항
description: 액세스 권한 부여됨 - 필요한 사항
translation-type: tm+mt
source-git-commit: 4904d7728befd3562940b35c7d44dbf9cae87fee
workflow-type: tm+mt
source-wordcount: '579'
ht-degree: 1%

---


# 부여된 액세스 권한 {#access-rights-granted}

Adobe은 IMS(Adobe Identity Management System)에서 회사에 대한 **조직** 식별자를 만들어 모든 사용자와 해당 권한을 관리할 수 있습니다. 이 조직의 구성원이 되어야 하고 [!UICONTROL Experience Cloud] 서비스에 대한 액세스 권한을 받는 각 사용자는 자신의 **Adobe ID**&#x200B;을(를) 가지고 있어야 합니다.

## 사용자 ID 유형 {#user-identity-types}

Adobe ID을 시작하려면 사용 가능한 ID 유형 중 하나를 사용하여 Adobe ID을 얻는 방법에 대한 자세한 지침은 [Adobe ID 유형 관리](https://helpx.adobe.com/enterprise/using/identity.html)를 방문하십시오.

## 사용자 및 역할 {#users-and-roles}

Adobe이 회사의 조직을 만든 후 지정된 관리자가 이 조직의 첫 번째 구성원으로 추가됩니다. 관리자는 기본적으로 관리자 권한을 부여받고 [!UICONTROL AEM Managed Services] **제품** 및 하나 이상의 [!UICONTROL 클라우드 관리자] **제품 프로필**&#x200B;을 할당합니다.

1. 시스템 관리자가 Cloud Manager에 대한 액세스 권한을 부여하면 [Adobe Experience Cloud](https://my.cloudmanager.adobe.com/)을(를) 통해서도 액세스할 수 있는 Cloud Manager 로그인 페이지로 안내하는 이메일을 받게 됩니다.

1. 클라우드 관리자의 랜딩 페이지에서 **액세스 관리**&#x200B;를 클릭합니다.

   ![](/help/onboarding/getting-access-to-aem-in-cloud/assets/sys-admin5.png)

1. **액세스 관리**&#x200B;를 클릭하면 Cloud Manager에 대한 사용자 역할이나 권한을 관리할 수 있는 **Admin Console**&#x200B;으로 이동합니다.

   ![](/help/onboarding/getting-access-to-aem-in-cloud/assets/sys-admin1.png)

   Admin Console에서 다음과 같은 SysAdmin 작업을 수행할 수 있습니다.
   * [역할 관리](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/getting-access/navigation.html?lang=en#manage-roles)
   * [작성자 인스턴스에 대한 액세스 관리](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/getting-access/navigation.html?lang=en#manage-access-aem)

>[!NOTE]
>Cloud Manager의 사용자 및 역할 정의에 대한 자세한 내용은 [사용자 및 역할](#users-roles) 섹션을 참조하십시오.

이러한 권한이 부여된 상태에서 관리자는 이제 단일 사인온(Adobe ID 사용)으로 설정하여 [!UICONTROL Experience Cloud] 서비스에 액세스하고, AEM 클라우드 환경에 로그인하고 [!UICONTROL Cloud Manager]를 사용합니다.

## 사용자 및 역할 {#users-roles}

[!UICONTROL Cloud Manager]의 많은 기능을 사용하려면 특정 권한이 필요합니다.

[!UICONTROL 클라우드 ] 관리자는 현재 특정 기능의 가용성을 제어하는 4가지 역할을 정의합니다.

* 비즈니스 소유자
* 프로그램 관리자
* 배포 관리자
* 개발자

>[!CAUTION]
>
>[!UICONTROL Cloud Manager]를 사용하려면 Adobe ID 및 Adobe Experience Manager이 Cloud Service 제품 컨텍스트로 있어야 합니다.

### 역할 정의 {#role-definitions}

>[!NOTE]
>
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

