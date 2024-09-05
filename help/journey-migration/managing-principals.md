---
title: 주체 관리
description: Admin Console을 사용하여 마이그레이션할 주도자 관리
exl-id: a75598d0-8f59-466b-984e-dfe527388c2a
source-git-commit: a5bec2c05b46f8db55762b7ee1f346f3bb099d24
workflow-type: tm+mt
source-wordcount: '311'
ht-degree: 6%

---

# 주체 관리 {#managing-principals}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_managingprincipals"
>title="주체 관리"
>abstract="콘텐츠 마이그레이션 중 또는 이후에 사용자를 관리하기 위해 수행해야 할 작업에 대해 알아보기"

콘텐츠가 AEM as a Cloud Service 클라우드 환경으로 전송되기 전에 Admin Console에서 수행할 수 있는 작업이 몇 가지 있습니다.  사용자 및 그룹은 사용자를 만들고, 그룹을 만들고, 그룹에 사용자를 할당합니다. 이러한 사용자 및 그룹은 모든 Adobe 클라우드 기반 서비스의 사용자 및 그룹을 관리하는 데 사용되는 Adobe의 Identity Management 서비스인 IMS에 있습니다.

### Admin Console에서 그룹 및 해당 사용자 만들기

[AEM 주체에 대한 Admin Console 사용](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/security/ims-support#how-to-set-up)은(는) IMS에서 사용자 및 그룹을 만드는 방법과 사용자를 동시에 또는 나중에 그룹에 추가하는 방법에 대한 자세한 지침을 제공합니다.  문서에는 Admin Console을 통해 수동으로, Admin Console을 통해 CSV 업로드를 통해 및 사용자 동기화 도구를 통해 만들기 위한 세 가지 옵션이 포함되어 있습니다.

수동 옵션을 사용하면 한 번에 하나의 그룹 또는 사용자를 만들 수 있습니다. CSV 업로드를 사용하면 한 번에 여러 사용자와 그룹을 만들고 연결할 수 있습니다. 사용자 동기화 도구를 사용하면 기존 IDP를 사용하여 IMS 사용자 및 그룹을 만들고 관리할 수 있습니다.

사용자가 IMS를 사용하여 AEM에 로그인하면 사용자의 AEM 표현이 만들어집니다.  또한 사용자가 속한 모든 IMS 그룹에는 AEM에서 만들어진 동등한 AEM 그룹이 있습니다.  이러한 IMS에서 만든 AEM 사용자 및 그룹은 여전히 Admin Console을 사용하여 주로 관리됩니다.

콘텐츠 마이그레이션이 완료되면 사용자가 마이그레이션된 콘텐츠에 액세스할 수 있도록 일반적으로 IMS 그룹에 몇 가지 추가 구성이 필요합니다.  [마이그레이션 후 사용자 마이그레이션](/help/journey-migration/managing-principals-after-migration.md)을 참조하세요.

AEM 및 IMS 사용자와 그룹의 통합 및 관리 방법에 대한 자세한 내용은 [자습서, AEM 사용자, 그룹 및 권한](https://experienceleague.adobe.com/en/docs/experience-manager-learn/cloud-service/accessing/aem-users-groups-and-permissions)도 참조하세요.
