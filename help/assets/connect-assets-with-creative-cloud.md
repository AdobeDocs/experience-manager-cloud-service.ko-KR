---
title: AEM Assets를 Creative Cloud에 연결
description: AEM Assets를 구성하고 Creative Cloud에 연결하는 방법에 대해 알아봅니다. 다른 IMS 조직에 프로비저닝된 Creative Cloud 권한에 연결하여 Express 및 Creative Cloud Libraries 등 AEM Assets의 최신 Creative Cloud 통합을 쉽게 사용할 수 있습니다.
exl-id: 880200fe-94b3-49de-802c-34283f7c71bc
feature: Collaboration
role: User
source-git-commit: 257930bc2633a0d31ad3bd28305b8159597befa5
workflow-type: tm+mt
source-wordcount: '282'
ht-degree: 75%

---

# AEM Assets를 Creative Cloud에 연결  {#cross-org-entitlements}

Experience Manager Assets은 다른 IMS 조직에 프로비저닝된 Creative Cloud 권한에 연결하여 Express 및 Creative Cloud Libraries을 비롯한 AEM Assets의 최신 Creative Cloud 통합을 쉽게 사용할 수 있습니다.

Creative Cloud 제품 및 AEM Assets가 별도의 IMS 조직에 프로비저닝된 경우 다른 Creative Cloud 조직에 연결하여 두 솔루션 간의 통합 워크플로를 실행할 수 있습니다.

## 사전 요구 사항 {#prerequisites}

* Experience Manager Assets에 대한 관리자 권한

* Creative Cloud 및 Experience Manager에서 사용되는 동일한 사용자 ID에 대한 Creative Cloud의 활성 권한입니다. 동일한 이메일 주소를 사용하는 개인 및 Federated ID에 대한 자격은 다른 사용자 ID로 처리됩니다.

## 새 Creative Cloud 조직에 연결 {#connect-to-creative-cloud-org}

새 Creative Cloud 조직에 연결하려면 다음 단계를 수행하십시오.

1. **[!UICONTROL 설정]** > **[!UICONTROL Creative Cloud]**&#x200B;로 이동합니다.

1. **[!UICONTROL 새 Creative Cloud 조직 ID 선택]** 드롭다운 목록을 사용하여 새 Creative Cloud 조직을 선택합니다. 목록에는 액세스 권한이 있는 모든 조직이 표시됩니다. 활성 Creative Cloud 권한이 있는 조직을 선택합니다.

1. **[!UICONTROL 조직 전환]**&#x200B;을 클릭하여 새 조직으로 전환합니다.

   ![조직 간 권한](assets/cross-org-entitlements.png)

## 제한 사항 {#limitations}

* 한 번에 하나의 Creative Cloud 조직에만 AEM Assets를 연결할 수 있습니다. 한 번에 여러 Creative Cloud 조직에 연결할 수는 없습니다.

* AEM Assets 내에서 연결하는 Creative Cloud 조직은 조직 내의 모든 사용자에게 적용 가능합니다.
