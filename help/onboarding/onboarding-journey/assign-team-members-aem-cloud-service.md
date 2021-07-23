---
title: 'AEM에 Cloud Service 제품 프로필로 팀 구성원 할당 '
description: 팀 구성원을 AEM as a Cloud Service 제품 프로필로 할당하는 방법을 알려면 이 페이지를 따르십시오
hide: true
hidefromtoc: true
index: false
source-git-commit: fa61dc122cec5466827d06ffb2eca1c1c5f8bae6
workflow-type: tm+mt
source-wordcount: '743'
ht-degree: 1%

---


# AEM에 Cloud Service 제품 프로필로 팀 구성원 할당 {#assign-team-members-cloud-service}

## 목표 {#objective}

이 문서는 시스템 관리자가 Cloud Service 제품 프로필로 팀 구성원을 AEM에 지정하는 데 수행해야 하는 단계와 AEM 작성자가 AEM으로 여정을 시작할 수 있도록 하는 것이 중요한 이유를 이해하는 데 도움이 됩니다.

이 섹션을 읽은 후에는 다음 사항을 이해해야 합니다.

* 팀 구성원이 Cloud Service 제품 프로필로 AEM에 할당되는 이유와 방법입니다.
* AEM 사용자 제품 프로필에 팀 구성원을 추가하는 방법.
* AEM Administrators 제품 프로필에 팀 구성원을 추가하는 방법.


## 소개 {#introduction}

Cloud Service 사용자로 AEM에 대한 액세스 권한을 부여하려면 *AEM Users* 또는 *AEM Administrators*&#x200B;와 같은 두 제품 프로필 중 하나에 속해야 합니다. Cloud Manager 관리 권한이 충분하지 않으므로 팀 구성원에게 AEM 인스턴스에 대한 권한을 부여해야 합니다. 추가 정보.

>[!NOTE]
>시스템 관리자가 AEM 사용자 제품 프로필에 할당한 모든 사용자는 Cloud Manager에 대한 (읽기 전용) 액세스 권한을 갖습니다.

## 전제 조건 {#prerequisites}

이 섹션을 읽기 전에 다음 사전 요구 사항을 고려해야 합니다.

* [AEM as a Cloud Service 제품 프로필 이해](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/onboarding-concepts/aem-cs-team-product-profiles.html?lang=en#aem-product-profiles)
* [Admin Console](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/onboarding-concepts/admin-console.html?lang=en)에 익숙해지십시오
* Cloud Manager 제품 프로필이 팀 구성원에게 적절히 할당되었으며 클라우드 리소스가 설정되었습니다
* 팀 구성원에 대한 세부 정보: 시스템 관리자는 이름 및 전자 메일 주소와 AEM as a Cloud Service에 액세스해야 하는 팀 구성원의 역할 및 책임이 있어야 합니다.

   >[!NOTE]
   >온보딩을 위해 관리자, 개발자 및 컨텐츠 작성자와 같은 즉각적인 작업에 참여할 사용자를 처음에 추가하는 것이 좋습니다. 모든 사용자를 추가하지 않고 온보딩의 나머지 부분을 계속 진행할 수 있습니다. 온보딩을 완료하면 나중에 더 많은 사용자 수로 확장할 수 있습니다.


1. Admin Console에 로그인
(전과 동일)

1. AEM as a Cloud Service 제품 프로필 검토
Admin Console에서 Cloud Manager 프로필 목록을 볼 수 있습니다. 이를 위해 진행되는 작업:

1. Adobe Admin Console에 로그인하고 나면 제품 및 서비스 카드에서 Adobe Experience Manager as a Cloud Service를 선택합니다.

1. 아래 그림과 같이 인스턴스(개발 환경의 작성자 인스턴스)를 탐색하고 선택합니다.



   이제 AEM의 Cloud Service 제품 프로필 목록을 사용자의 역할에 따라 사용자에게 지정해야 합니다. 자세한 내용은 AEM as a Cloud Service 제품 프로필로 이동하십시오.


## AEM 사용자 또는 AEM 관리자 제품 프로필에 팀 구성원 추가 {#add-team-members}

Cloud Service 인스턴스로 AEM에 대한 액세스 권한을 부여하려면 사용자가 두 제품 프로필 &#39;AEM 사용자&#39; 또는 &#39;AEM 관리자&#39; 중 하나에 속해야 합니다.

>[!NOTE]
>인스턴스에 대한 권한을 부여해야 하며 Cloud Manager 관리 권한으로는 충분하지 않습니다. 추가 정보.

아래 단계는 비즈니스 소유자 역할에도 참여하는 시스템 관리자가 수행해야 합니다.

1. Cloud Manager에서 Cloud Manager로 이동하여 아래와 같이 관심 환경 컨텍스트에서 액세스 관리 단추를 선택합니다.

1. 액세스 관리를 클릭하면 새 탭이 환경의 작성자 인스턴스에 액세스할 수 있는 Admin Console으로 이동합니다. 이 개인이 부여해야 하는 권한에 따라 *AEM Administrators* 또는 *AEM Users*&#x200B;를 선택합니다. [AEM as a Cloud Service 제품 프로필](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/onboarding-concepts/aem-cs-team-product-profiles.html?lang=en#aem-product-profiles)에 대해 자세히 알아보십시오.

1. 아래 표시된 대로 사용자 추가 를 선택하고 필요한 세부 정보를 제출하여 팀 구성원 추가를 완료합니다.


1. 액세스 권한이 필요한 팀 구성원의 정보가 있는 경우 개발, 스테이지 및 프로덕션을 포함한 모든 환경에 대해 이 단계를 반복하게 됩니다.

   추가한 사용자는 이제 AEM as a Cloud Service 작성자 서비스로 액세스할 수 있습니다.


## 다음은 무엇입니까? {#whats-next}

Cloud Service 제품 프로필로 AEM에 할당한 사용자는 이제 작성자에 액세스하는 방법을 학습하고 AEM as a Cloud Service으로 페이지를 작성하는 방법에 대해 알 수 있습니다. 그 다음 AEM 사용자를 위한 학습 경로 문서를 검토하여 경로를 따라야 합니다.

## 추가 리소스 {#additional-resources}

AEM 액세스 구성(비디오 둘러보기)
페이지 작성에 대한 빠른 시작 안내서
