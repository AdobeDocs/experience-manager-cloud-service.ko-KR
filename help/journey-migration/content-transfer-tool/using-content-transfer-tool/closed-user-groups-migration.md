---
title: 폐쇄형 사용자 그룹 마이그레이션
description: 콘텐츠를 Adobe Experience Manager as a Cloud Service으로 마이그레이션한 후 폐쇄된 사용자 그룹을 활성화하는 데 필요한 특수 고려 사항에 대해 알아봅니다.
hide: true
hidefromtoc: true
exl-id: f62ed751-d5e2-4a01-8910-c844afab5733
feature: Migration
role: Admin
source-git-commit: 5b0dfb847a1769665899d6dd693a7946832fe7d1
workflow-type: tm+mt
source-wordcount: '287'
ht-degree: 12%

---


# 폐쇄형 사용자 그룹 마이그레이션 {#migrating-closed-user-groups}

>[!CONTEXTUALHELP]
>id="aemcloud_cug_migration"
>title="폐쇄된 사용자 그룹의 마이그레이션"
>abstract="폐쇄형 사용자 그룹(CUG)의 마이그레이션은 현재 마이그레이션 후 작동을 위한 몇 가지 확인 및 단계가 필요합니다."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-65/administering/security/closed-user-groups.html" text="AEM의 폐쇄형 사용자 그룹"

현재 폐쇄된 사용자 그룹(CUG)이 마이그레이션의 대상 환경에서 작동하려면 몇 가지 추가 단계가 필요합니다. 이 문서에서는 시나리오 및 의도한 방식으로 노드를 보호하는 데 필요한 단계에 대해 설명합니다.

## CUG(폐쇄형 사용자 그룹) 마이그레이션

그룹은 해당 콘텐츠의 ACL 또는 CUG 정책 노드를 통해 마이그레이션된 콘텐츠와 연결된 경우 Adobe Experience Manager as a Cloud Service으로 CTT/CAM 마이그레이션에 자동으로 포함됩니다. 라이브로 전환하기 전에 그룹 및 해당 멤버가 있는지 확인해야 합니다. CUG 정책에 참조된 그룹을 여기에서 &quot;CUG 그룹&quot;이라고 합니다.

AEM as a Cloud Service에서 CUG를 사용하려면 사용자가 작성자 인스턴스에 있고 관련 CUG 그룹의 멤버여야 합니다.  이는 패키지를 사용하여 수행할 수 있으며, 또는 CUG 사용자가 IMS 사용자인 경우 이미 있을 수 있습니다.  그런 다음 AEM CUG 그룹의 구성원으로 CUG 사용자를 만들어야 합니다.

Publish 인스턴스에서 CUG 동작을 활성화하려면 다음을 수행하십시오.
1. CUG 그룹을 활성화해야 하며(CUG 그룹과 해당 구성원을 Publish 인스턴스로 복제),
1. CUG 정책으로 보호된 페이지는 게시해야 합니다(Publish 인스턴스 및 정책 추적 가능).
1. 모든 페이지가 게시되면 CUG로 보호된 각 페이지에 대한 기능을 확인합니다.

자세한 내용은 [폐쇄된 사용자 그룹](https://experienceleague.adobe.com/docs/experience-manager-65/administering/security/closed-user-groups.html)을 참조하세요.
