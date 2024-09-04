---
title: ' [!DNL Content Hub] 배포'
description: Content Hub을 배포하고 활성화하고 다양한 유형의 권한을 가진 사용자에게 액세스를 제공하는 방법(자산 업로드, Adobe Express 사용자)과 사용자에게 관리자 권한을 제공하는 방법에 대해 알아봅니다.
role: Admin
exl-id: 58194858-6e1c-460b-bab3-3496176b2851
source-git-commit: 3bb3920d043c83dac6f8e566761b626236bd2a04
workflow-type: tm+mt
source-wordcount: '1569'
ht-degree: 1%

---

# Content Hub 배포 {#deploy-content-hub}

![Content Hub 배포](assets/deploy-content-hub.png)

Content Hub은 조직 및 비즈니스 파트너를 위한 온브랜드 콘텐츠에 대한 액세스를 민주화하기 위해 Experience Manager Assets as a Cloud Service의 일부로 사용할 수 있습니다.

Experience Manager Assetsas a Cloud Service 에서 승인됨으로 표시된 자산은 Content Hub에서 자산 배포에 사용할 수 있습니다.

이 문서에서는 요구 사항에 따른 다양한 권한을 포함하여 사용자에게 Content Hub 액세스를 제공하는 통합 워크플로우를 제공합니다.

Content Hub에 대한 권한의 변형은 다음과 같습니다.

* [Content Hub 사용자](#onboard-content-hub-users): Content Hub 포털에서 브랜드 승인 자산에 액세스합니다.

* [Content Hub 관리자](#onboard-content-hub-administrator): 브랜드 승인 에셋에 액세스, Content Hub에 에셋 업로드, 이미지 편집을 위한 Adobe Express 통합(Adobe Express 권한이 있는 경우) 외에도 Content Hub의 [구성 사용자 인터페이스](/help/assets/configure-content-hub-ui-options.md)에 액세스할 수 있습니다.

* [에셋을 추가할 수 있는 권한이 있는 Content Hub 사용자](#onboard-content-hub-users-add-assets): Content Hub 포털에서 브랜드 승인 에셋에 액세스할 수 있을 뿐만 아니라 [Content Hub에 에셋을 업로드](/help/assets/upload-brand-approved-assets.md)할 수 있습니다.

* [자산을 새 변형으로 다시 혼합할 수 있는 권한이 있는 Content Hub 사용자](#onboard-content-hub-users-remix-assets): [Adobe Express 통합](/help/assets/edit-images-content-hub.md)(Adobe Express 권한이 있는 경우), Content Hub 포털에서 브랜드 승인 자산에 액세스할 수도 있습니다.

* [Experience Manager Assets 사용자](#experience-manager-assets-users): Experience Manager Assetsas a Cloud Service 에서 자산을 승인하여 Content Hub에서 해당 자산을 사용할 수 있도록 합니다.

다음 표에는 사용 가능한 Content Hub 사용자 유형, 사용자가 가지고 있는 권한 및 이러한 권한을 얻는 데 필요한 제품 프로필이 요약되어 있습니다.

| 사용자 역할 | Content Hub 사용자 | 에셋을 추가할 수 있는 권한이 있는 Content Hub 사용자 | 자산을 리믹스할 수 있는 권한이 있는 Content Hub 사용자 | Content Hub 관리자 |
|---------------|----------|----------|-------------------------|---|
| **기능** |
| Content Hub 포털에서 브랜드 승인 자산에 액세스 | ✓ | ✓ | ✓ | ✓ |
| Content Hub 포털에서 에셋 업로드 | − | ✓ | ✓ | ✓ |
| Adobe Express 통합을 사용하여 이미지 편집 | − | − | ✓ | − |
| Content Hub 구성 UI 액세스 | − | − | − | ✓ |
| **사용자는 이러한 제품 프로필(Admin Console)에 있어야 합니다** |
| AEM > 게재 인스턴스 > AEM Assets 제한된 사용자 | ✓ | ✓ | ✓ | ✓ |
| AEM > 프로덕션 작성자 인스턴스 > AEM 사용자 | − | ✓ | ✓ | − |
| AEM > 프로덕션 작성자 인스턴스 > AEM 관리자 | − | − | − | ✓ |
| Adobe Express | − | − | ✓ | − |
| **추가 정보** | [Content Hub 사용자](#onboard-content-hub-users) 보기 | 자산을 추가할 수 있는 권한이 있는 [Content Hub 사용자](#onboard-content-hub-users-add-assets) 보기 | 자산을 새 변형으로 다시 혼합할 수 있는 권한이 있는 [Content Hub 사용자](#onboard-content-hub-users-remix-assets)를 참조하세요. | [Content Hub 관리자](#onboard-content-hub-administrator) 보기 |

>[!NOTE]
>
>[Experience Manager Assets 사용자](#experience-manager-assets-users)는 Experience Manager Assets as a Cloud Service 환경에서 자산을 승인하여 해당 자산을 Content Hub에서 사용할 수 있도록 할 수 있습니다. 이러한 사용자는 Admin Console을 사용하여 AEM > 프로덕션 작성자 인스턴스 > AEM 사용자 제품 프로필에 추가해야 합니다.

## 1단계: Cloud Manager을 사용하여 Experience Manager Assets용 Content Hub 활성화 {#enable-content-hub}

Content Hub 포털에 액세스하려면 먼저 관리자가 Cloud Manager을 사용하여 Content Hub for Experience Manager Assetsas a Cloud Service 를 활성화해야 합니다. 다음 단계를 실행합니다.

1. Cloud Manager에 로그온합니다. 로그인하는 동안 올바른 조직을 선택해야 합니다. Cloud Manager에 모든 프로그램이 나열됩니다.

1. Experience Manager Assets as a Cloud Service 프로그램으로 이동하고 추가 옵션 아이콘(...)을 클릭한 다음 **[!UICONTROL 프로그램 편집]**&#x200B;을 선택합니다.

   ![Cloud Manager에서 프로그램 편집](assets/edit-program-cloud-manager.png)

1. [!UICONTROL 프로그램 편집] 대화 상자에서 **[!UICONTROL 솔루션 및 추가 기능]** 탭을 선택합니다.

1. **[!UICONTROL Assets]**&#x200B;을(를) 확장하고 **[!UICONTROL Content Hub]**을(를) 선택합니다.
   ![Cloud Manager에서 Content Hub 선택](assets/edit-program-cloud-manager-content-hub.png)

   >[!NOTE]
   >
   >Content Hub을 선택한 후 **[!UICONTROL 업데이트]**&#x200B;를 사용할 수 없는 경우 프로그램에 대한 Go-Live 설정을 지정했는지 확인하십시오.

1. **[!UICONTROL 업데이트]**&#x200B;를 클릭합니다.

이제 Experience Manager Assetsas a Cloud Service 에 대해 Content Hub이 활성화됩니다. 프로덕션 환경에서 Content Hub을 활성화한 후에는 셀프서비스 방식으로 비활성화할 수 없습니다.

>[!NOTE]
>
>최대 250명의 Content Hub 사용자와 Content Hub에 액세스하고 사용할 수 있습니다. 추가 질문이 있는 경우 Adobe 담당자에게 문의하십시오.


Experience Manager Assets을 처음 사용하는 경우 **[!UICONTROL 프로그램 추가]**&#x200B;를 클릭한 다음 프로그램 세부 정보(프로그램 이름, 프로덕션 설정)를 입력하고 **[!UICONTROL 계속]**&#x200B;을 클릭합니다. **[!UICONTROL 솔루션 및 추가 기능]** 탭에서 **[!UICONTROL Assets]** 및 **[!UICONTROL Content Hub]**&#x200B;을(를) 선택할 수 있습니다.

### Admin Console의 Content Hub 인스턴스 및 제품 프로필{#content-hub-instance-product-profile}

{Cloud Manager을 사용하여 Assetsas a Cloud Service 용 Content Hub ](#enable-content-hub)을(를) 실행한 후 AEM Assets as a Cloud Service Admin Console 내에서 접미사 `delivery`을(를) 사용하는 새 인스턴스가 생성되었습니다.[

![Content Hub의 새 인스턴스](assets/new-instance-content-hub.png)

>[!NOTE]
>
>2024년 8월 14일 이전에 Content Hub을 프로비저닝한 경우 `contenthub`을(를) 접미사로 사용하여 새 인스턴스가 만들어집니다.

Content Hub의 인스턴스 이름에 `author` 또는 `publish`이(가) 없습니다.

Content Hub 제품 프로필을 보려면 인스턴스 이름을 클릭합니다.

![Content Hub 제품 프로필](assets/content-hub-product-profile.png)

>[!NOTE]
>
>2024년 8월 14일 이전에 Content Hub을 프로비저닝한 경우 Content Hub 제품 프로필에 `delivery` 대신 `Limited Users` 뒤에 `contenthub`이(가) 언급되어 있습니다.

## 2단계: Content Hub 관리자 온보드 {#onboard-content-hub-administrator}

Content Hub 관리자는 브랜드 승인 에셋에 액세스, Content Hub에 에셋 업로드, 이미지 편집을 위한 Adobe Express 통합(Adobe Express 권한이 있는 경우) 외에도 Content Hub에서 [구성 사용자 인터페이스](/help/assets/configure-content-hub-ui-options.md)에 액세스할 수 있습니다.

Content Hub 관리자를 온보딩하려면:

1. [Content Hub 사용자 제품 프로필에 액세스하여 클릭](#content-hub-instance-product-profile)합니다.

1. 제품 프로필에 사용자 또는 사용자 그룹을 추가하려면 **[!UICONTROL 사용자 추가]**&#x200B;를 클릭하십시오.

1. 변경 내용을 저장하려면 **[!UICONTROL 저장]**&#x200B;을 클릭하세요.

1. Content Hub 제품 프로필에 사용자를 추가한 후 Admin Console의 제품 목록에서 AEM as a Cloud Service 제품 이름을 클릭하여 Experience Manager Assets 제품 프로필에 액세스합니다.

1. AEM as a Cloud Service에 대한 프로덕션 작성자 인스턴스 를 클릭합니다.
   AEM as a Cloud Service의 ![제품 프로필](assets/aem-cloud-service-instances.png)

   Admin Console은 AEM as a Cloud Service에 대한 두 개의 제품 프로필(관리자 및 사용자)을 표시합니다.
1. 관리자 제품 프로필을 클릭하고 **[!UICONTROL 사용자 추가]**를 클릭하여 사용자를 제품 프로필에 추가합니다.
   ![관리자 제품 프로필](assets/aem-cs-admin-product-profile.png)

1. 변경 내용을 저장하려면 **[!UICONTROL 저장]**&#x200B;을 클릭하세요.

## 3단계: Content Hub 사용자 온보드 {#onboard-content-hub-users}

Content Hub 사용자는 포털에서 사용할 수 있는 에셋에 액세스할 수 있지만 새 에셋을 추가하거나 기존 에셋을 수정할 수는 없습니다.

Content Hub 사용자를 온보딩하려면:

1. [Content Hub 사용자 제품 프로필에 액세스하여 클릭](#content-hub-instance-product-profile)합니다.

1. 제품 프로필에 사용자 또는 사용자 그룹을 추가하려면 **[!UICONTROL 사용자 추가]**&#x200B;를 클릭하십시오.

1. 변경 내용을 저장하려면 **[!UICONTROL 저장]**&#x200B;을 클릭하세요.

이제 이러한 사용자는 Content Hub 포털에서 사용할 수 있는 자산에 액세스할 수 있습니다.

>[!NOTE]
>
>외부 ID 공급자와의 동기화와 같은 모든 고급 엔터프라이즈 기능을 사용할 수 있습니다.

### Content Hub에 액세스하는 방법 {#access-content-hub}

Content Hub은 다음과 같은 방법으로 액세스할 수 있습니다.

* 다음 링크를 사용하여 Content Hub에 액세스합니다.

  `https://experience.adobe.com/#/assets/contenthub`

* `experience.adobe com`에 로그온하여 **[!UICONTROL 빠른 액세스]** 섹션에서 사용 가능한 **[!UICONTROL Experience Manager Assets Content Hub]**을(를) 클릭합니다.
  ![Content Hub 액세스](assets/access-content-hub.png)

* `experience.adobe com`에 로그온하고 제품 전환기에서 사용 가능한 **[!UICONTROL Experience Manager Assets Content Hub]**을(를) 클릭합니다.
  ![Content Hub 액세스 메서드 3](assets/access-content-hub-alternate.png)

### 사용자에게 이메일 알림 비활성화 {#disable-email-notifications}

관리자가 Content Hub 제품 프로필에 추가될 때 사용자에게 전송된 이메일 알림을 비활성화해야 하는 경우:

제품 프로필 이름 옆에 있는 검색 아이콘을 클릭하고 **[!UICONTROL 전자 메일로 사용자에게 알림]** 토글을 사용하지 않도록 설정합니다.

![전자 메일 알림 사용 안 함](assets/disable-email-notifications.png)


## 4단계: 에셋을 추가할 수 있는 권한이 있는 Content Hub 사용자 온보딩(선택 사항) {#onboard-content-hub-users-add-assets}

에셋을 추가할 수 있는 권한이 있는 Content Hub 사용자는 [새 브랜드로 승인된 에셋을 Content Hub에 업로드](/help/assets/upload-brand-approved-assets.md)할 수 있습니다.

사용자를 추가할 수 있는 권한이 있는 Content Hub 사용자를 온보딩하려면 다음을 수행하십시오.

1. [Content Hub 제품 프로필에 사용자를 추가한 후](#onboard-content-hub-users) Admin Console의 제품 목록에서 AEM as a Cloud Service 제품 이름을 클릭하여 Experience Manager Assets 제품 프로필에 액세스합니다.

1. AEM as a Cloud Service에 대한 프로덕션 작성자 인스턴스 를 클릭합니다.
   AEM as a Cloud Service의 ![제품 프로필](assets/aem-cloud-service-instances.png)

   Admin Console은 AEM as a Cloud Service에 대한 두 개의 제품 프로필(관리자 및 사용자)을 표시합니다.
1. 사용자 제품 프로필을 클릭하고 **[!UICONTROL 사용자 추가]**를 클릭하여 사용자를 제품 프로필에 추가합니다.
   ![사용자 제품 프로필](assets/aem-cs-user-product-profile.png)

1. 변경 내용을 저장하려면 **[!UICONTROL 저장]**&#x200B;을 클릭하세요.

## 4단계: 에셋을 새 변형에 리믹스할 수 있는 권한이 있는 Content Hub 사용자 온보딩(선택 사항) {#onboard-content-hub-users-remix-assets}

자산을 새 변형으로 다시 혼합할 수 있는 권한이 있는 Content Hub 사용자는 [Adobe Express을 사용하여 기존 자산을 수정하고 저장소에 해당 자산을 저장할 수 있습니다](/help/assets/edit-images-content-hub.md). Adobe Express을 사용하여 에셋을 편집하는 것은 사용자에게 Adobe Express 권한이 있는 경우에만 사용할 수 있습니다.

자산을 새 변형에 재혼합할 수 있는 권한이 있는 Content Hub 사용자를 온보딩하려면 다음을 수행하십시오.

1. [Content Hub 제품 프로필에 사용자를 추가한 후](#onboard-content-hub-users) Admin Console의 제품 목록에서 AEM as a Cloud Service 제품 이름을 클릭하여 Experience Manager Assets 제품 프로필에 액세스합니다.

1. AEM as a Cloud Service에 대한 프로덕션 작성자 인스턴스 를 클릭합니다.
   AEM as a Cloud Service의 ![제품 프로필](assets/aem-cloud-service-instances.png)

   Admin Console은 AEM as a Cloud Service에 대한 두 개의 제품 프로필(관리자 및 사용자)을 표시합니다.
1. 사용자 제품 프로필을 클릭하고 **[!UICONTROL 사용자 추가]**를 클릭하여 사용자를 제품 프로필에 추가합니다.
   ![사용자 제품 프로필](assets/aem-cs-user-product-profile.png)

1. 변경 내용을 저장하려면 **[!UICONTROL 저장]**&#x200B;을 클릭하세요.

## Experience Manager Assets 사용자 {#experience-manager-assets-users}

Experience Manager Assets 사용자는 AEM as a Cloud Service에서 사용할 수 있도록 Content Hub에서 자산을 승인할 수 있습니다.

Experience Manager Assets 사용자를 구성하려면 다음 작업을 수행하십시오.

1. Admin Console의 제품 목록에서 Experience Manager Assets 제품 이름을 클릭하여 AEM as a Cloud Service 제품 프로필에 액세스합니다.

1. AEM as a Cloud Service에 대한 프로덕션 작성자 인스턴스 를 클릭합니다.
   AEM as a Cloud Service의 ![제품 프로필](assets/aem-cloud-service-instances.png)

   Admin Console은 AEM as a Cloud Service에 대한 두 개의 제품 프로필(관리자 및 사용자)을 표시합니다.
1. 사용자 제품 프로필을 클릭하고 **[!UICONTROL 사용자 추가]**를 클릭하여 사용자를 제품 프로필에 추가합니다.
   ![사용자 제품 프로필](assets/aem-cs-user-product-profile.png)

1. 변경 내용을 저장하려면 **[!UICONTROL 저장]**&#x200B;을 클릭하세요.

   >[!NOTE]
   >
   > Experience Manager Assets 사용자를 위해 [Content Hub 제품 프로필](#onboard-content-hub-users)에 추가할 필요는 없습니다.
