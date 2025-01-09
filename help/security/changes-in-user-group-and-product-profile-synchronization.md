---
title: 사용자 그룹 및 제품 프로필 동기화 변경 사항
description: AEM as a Cloud Service으로 전환되는 사용자 그룹 및 제품 프로필 동기화의 변경 사항에 대해 알아보기
feature: Security
role: Admin
hide: true
hidefromtoc: true
source-git-commit: c3e3905d3896d79149a386241d798f78631184b3
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 0%

---


# 사용자 그룹 및 제품 프로필 동기화 변경 사항 {#changes-in-user-group-and-product-profile-synchronization}

사용자가 AEM as a Cloud Service에 로그인하거나 액세스 토큰을 사용할 때마다 Adobe Admin Console 사용자 그룹, 제품 프로필 및 제품 프로필 서비스는 그룹으로 AEM 저장소에 동기화됩니다.

1월 28일에 UI가 복잡해지고 성능이 최적화되기 위해 동기화 동작이 일부 변경되어 AEM에 표시되는 그룹이 줄어듭니다. AEM 그룹의 두 가지 카테고리가 제거됩니다.

1. 접미사가 `GROUP_NAME_SUFFIX`인 AEM 그룹. 이러한 그룹은 Adobe Developer Console에는 표시되지 않지만 아래와 같이 AEM 그룹 관리 화면에는 표시됩니다. 드물지만 AEM 애플리케이션이 이러한 그룹을 참조하는 경우 대신 Adobe Admin Console 사용자 그룹을 사용해야 합니다.

   ![제거된 그룹 1](/help/security/assets/removed-groups-1.png)

1. 특정 AEM 계층 또는 환경 조합과 관련이 없는 Adobe Admin Console 제품 프로필과 연결된 AEM 그룹(예: `author` 또는 `e4535`). 여기에는 다음과 같은 제품 프로필이 포함될 수 있습니다.

   * 기타 Adobe 제품과 관련됨
   * 기타 AEM 프로그램과 관련되어 있음
   * 동일한 AEM 프로그램에서 다른 AEM 환경과 관련이 있음
   * 동일한 AEM 환경에서 다른 계층(예: `author` 및 `publish`)과 관련되어 있음
   * Cloud Manager 관련 항목(예: `Business Owner - Cloud Service`)

   예를 들어 아래 이미지에는 접미사가 현재 환경과 관련이 없는 `AEM Administrators-<suffix>` 또는 `AEM Users-<suffix>` 패턴을 가진 행이 많습니다.

   ![제거된 그룹 2](/help/security/assets/removed-groups-2.png)

Cloud Manager의 환경 작업 메뉴에서 **액세스 - 작성자 프로필**(또는 **Publish 프로필**) 관리를 선택하여 현재 환경과 관련된 접미사를 확인할 수 있습니다.

![접미사 확인](/help/security/assets/suffix-check.png)

아래 스크린샷에 표시된 대로 Adobe Admin Console으로 이동합니다. `<suffix>`은(는) 임의의 문자 집합이거나 계층, 프로그램 및 환경 ID(예: `author - Program 12345 - Environment 45678`)일 수 있습니다.

![Admin Console의 접미사](/help/security/assets/admin-console-profile-suffixes.png)

드물지만 AEM 애플리케이션이 이러한 그룹을 참조하는 경우 대신 Adobe Admin Console 사용자 그룹을 사용해야 합니다.

>[!NOTE]
>
>특히 이러한 잠재적인 위험에 주의하십시오.
>
>1. AEM 애플리케이션은 Cloud Manager 제품 프로필에서 동기화된 AEM 그룹을 사용합니다
>1. AEM 애플리케이션의 게시 계층은 작성자 계층 제품 프로필에서 동기화된 AEM 그룹을 사용합니다. 이는 역 시나리오(게시 계층에 의존하는 작성자 계층)에도 적용됩니다.