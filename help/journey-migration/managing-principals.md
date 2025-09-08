---
title: 주체 관리
description: Admin Console을 사용하여 마이그레이션을 위한 주체 관리
exl-id: a75598d0-8f59-466b-984e-dfe527388c2a
source-git-commit: edfefb163e2d48dc9f9ad90fa68809484ce6abb0
workflow-type: ht
source-wordcount: '311'
ht-degree: 100%

---

# 주체 관리 {#managing-principals}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_managingprincipals"
>title="주체 관리"
>abstract="콘텐츠 마이그레이션 중 또는 이후에 사용자를 관리하기 위해 수행해야 할 작업에 대해 알아보기"

콘텐츠를 AEM as a Cloud Service 클라우드 환경으로 전송하기 전에 Admin Console에서 수행할 수 있는 몇 가지 작업이 있습니다.  사용자 만들기, 그룹 만들기 및 그룹에 사용자 할당 작업입니다. 이 사용자 및 그룹은 모든 Adobe 클라우드 기반 서비스의 사용자 및 그룹을 관리하는 데 사용되는 Adobe의 Identity Management Service인 IMS에 존재하게 됩니다.

## Admin Console에서 그룹 및 사용자 만들기

[AEM 주체를 위한 Admin Console 사용](https://experienceleague.adobe.com/ko/docs/experience-manager-cloud-service/content/security/ims-support#how-to-set-up)에서는 IMS에서 사용자 및 그룹을 만드는 방법과 사용자를 동시에 그룹에 추가하는 방법에 대한 자세한 지침을 제공합니다.  이 문서에는 이를 만들 수 있는 세 가지 옵션인, Admin Console을 통한 수동 방식, Admin Console로 CSV 업로드를 통한 방식, 사용자 동기화 도구를 통한 방식이 포함되어 있습니다.

수동 옵션을 사용하면 한 번에 하나의 그룹 또는 사용자를 만들 수 있고, CSV 업로드를 사용하면 여러 사용자 및 그룹을 한 번에 만들고 연결할 수 있으며, 사용자 동기화 도구를 사용하면 기존 IDP를 사용하여 IMS 사용자 및 그룹을 만들고 관리할 수 있습니다.

사용자가 IMS를 사용하여 AEM에 로그인하면 해당 사용자를 나타내는 AEM 사용자 정보가 생성됩니다.  또한 사용자가 속한 모든 IMS 그룹에 상응하는 AEM 그룹이 AEM에 생성됩니다.  IMS에서 만든 AEM 사용자 및 그룹은 계속해서 Admin Console을 통해 관리됩니다.

콘텐츠 마이그레이션이 완료되면 일반적으로 사용자가 마이그레이션된 콘텐츠에 액세스할 수 있도록 IMS 그룹에 몇 가지 추가 구성이 필요합니다.  [마이그레이션 후 주체 마이그레이션](/help/journey-migration/managing-principals-after-migration.md) 참조

AEM 및 IMS 사용자와 그룹을 통합하고 관리하는 방법에 대한 자세한 내용은 [튜토리얼, AEM 사용자, 그룹 및 권한](https://experienceleague.adobe.com/ko/docs/experience-manager-learn/cloud-service/accessing/aem-users-groups-and-permissions)을 참조하십시오.
