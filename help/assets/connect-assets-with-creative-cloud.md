---
title: AEM Assets을 Creative Cloud에 연결
description: AEM Assets을 구성하고 Creative Cloud에 연결하는 방법에 대해 알아봅니다. Express 및 Creative Cloud 라이브러리를 포함하여 AEM Assets의 최신 Creative Cloud 통합을 쉽게 사용할 수 있도록 다른 IMS 조직에 프로비저닝된 Creative Cloud 권한에 연결합니다.
source-git-commit: 8c0c01be301ccaeac4e658c16d63227e55b67fcf
workflow-type: tm+mt
source-wordcount: '286'
ht-degree: 0%

---

# AEM Assets을 Creative Cloud에 연결  {#cross-org-entitlements}

Experience Manager Assets은 Express 및 Creative Cloud 라이브러리를 포함하여 AEM Assets의 최신 Creative Cloud 통합을 쉽게 사용할 수 있도록 다른 IMS 조직에 프로비저닝된 Creative Cloud 권한에 연결할 수 있습니다.

Creative Cloud 제품 및 AEM Assets이 별도의 IMS 조직에 프로비저닝된 경우 다른 Creative Cloud 조직에 연결하여 두 솔루션 간에 통합 워크플로우를 실행할 수 있습니다.

## 사전 요구 사항 {#prerequisites}

* Experience Manager Assets에 대한 관리자 권한

* Creative Cloud 및 Experience Manager에서 사용되는 동일한 Creative Cloud ID에 대한 사용자의 활성 권한. 이메일 주소가 동일한 개인 및 Federated ID에 대한 권한은 다른 사용자 ID로 처리됩니다.

## 새 Creative Cloud 조직에 연결 {#connect-to-creative-cloud-org}

새 Creative Cloud 조직에 연결하려면 다음 단계를 수행하십시오.

1. 다음으로 이동 **[!UICONTROL 설정]** > **[!UICONTROL Creative Cloud]**.

1. 다음을 사용하여 새 Creative Cloud 조직 선택 **[!UICONTROL 새 Creative Cloud 조직 ID 선택]** 드롭다운 목록입니다. 액세스 권한이 있는 모든 조직이 목록에 표시됩니다. 활성 Creative Cloud 권한이 있는 조직을 선택하십시오.

1. 클릭 **[!UICONTROL 조직 전환]** 새 조직으로 전환합니다.

   ![교차 조직 권한](assets/cross-org-entitlements.png)

## 제한 사항 {#limitations}

* AEM Assets을 한 번에 하나의 Creative Cloud 조직에 연결할 수 있습니다. 한 번에 여러 Creative Cloud 조직에 대한 연결은 지원되지 않습니다.

* AEM Assets 내에서 연결하는 Creative Cloud 조직은 조직 내의 모든 사용자에게 적용할 수 있습니다.

