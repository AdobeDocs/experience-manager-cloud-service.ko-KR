---
title: 사용자 그룹 및 제품 프로필 동기화의 변경 사항
description: AEM as a Cloud Service에 적용되는 사용자 그룹 및 제품 프로필 동기화 변경 사항에 대해 알아보기
feature: Security
role: Admin
hide: true
hidefromtoc: true
exl-id: 0b097ab3-bf1d-4d43-9e19-d544594844ef
source-git-commit: 5c103fcce1ae47bc89f4f572d89967c62c1f7603
workflow-type: tm+mt
source-wordcount: '385'
ht-degree: 79%

---

# 사용자 그룹 및 제품 프로필 동기화의 변경 사항 {#changes-in-user-group-and-product-profile-synchronization}

AEM as a Cloud Service에 사용자가 로그인하거나 액세스 토큰이 사용될 때 Adobe Admin Console의 사용자 그룹, 제품 프로필 및 제품 프로필 서비스가 AEM 저장소에 그룹으로 동기화됩니다.

AEM 유지 관리 릴리스 19149부터는 그룹 동기화 동작이 변경되어 UI가 복잡해지고 성능이 최적화됩니다. 특히 다음 두 범주의 AEM 그룹 구성원은 더 이상 동기화되지 않습니다.

1. `GROUP_NAME_SUFFIX` 접미사가 포함된 AEM 그룹 이러한 그룹은 Adobe Developer Console에는 표시되지 않지만 아래와 같이 AEM 그룹 관리 화면에 표시됩니다. 예기치 않게 AEM 애플리케이션에서 이러한 그룹을 참조하는 경우, 해당 그룹 대신 접미사가 없는 Adobe Admin Console 사용자 그룹을 참조해야 합니다.

   ![제거된 그룹 1](/help/security/assets/removed-groups-1.png)

1. 특정 환경과 관련 없는 Adobe Admin Console 제품 프로필에 연결된 AEM 그룹 여기에는 다음과 같은 제품 프로필이 포함될 수 있습니다.

   * 다른 Adobe 제품과 관련됨
   * 다른 AEM 프로그램과 관련됨
   * 동일한 AEM 프로그램의 다른 AEM 환경과 관련됨
   * Cloud Manager와 관련됨(예: `Business Owner - Cloud Service`)

   예를 들어 아래 이미지에는 접미사가 현재 환경과 관련이 없는 `AEM Administrators-<suffix>` 또는 `AEM Users-<suffix>` 패턴의 행이 많이 나타납니다.

   ![제거된 그룹 2](/help/security/assets/removed-groups-2.png)

Cloud Manager의 환경 동작 메뉴에서 **액세스 관리 - 작성자 프로필**(또는 **게시 프로필**)을 선택하면 현재 환경과 관련된 접미사를 확인할 수 있습니다.

![접미사 확인](/help/security/assets/suffix-check.png)

아래 스크린샷에 표시된 것처럼 Adobe Admin Console로 이동됩니다. `<suffix>`는 무작위 문자 집합이거나 계층, 프로그램 및 환경 ID(예: `author - Program 12345 - Environment 45678`)일 수 있습니다.

![Admin Console의 접미사](/help/security/assets/admin-console-profile-suffixes.png)

AEM 애플리케이션이 더 이상 AEM에 표시되지 않는 그룹을 참조하는 경우에는 i) 올바른 AEM 인스턴스의 제품 프로필 또는 ii) Adobe Admin Console 사용자 그룹을 사용하도록 변경해야 합니다.

사용자의 그룹 멤버십은 환경에 로그인할 때 동기화되며 현재 환경과 관련이 없는 그룹에서 제거됩니다. 그룹 자체는 유지되며 기능이 활성화된 이후 로그인하지 않은 사용자를 포함합니다.
