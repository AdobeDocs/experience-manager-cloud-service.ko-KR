---
title: 폐쇄형 사용자 그룹 마이그레이션
description: 콘텐츠를 Adobe Experience Manager as a Cloud Service으로 마이그레이션한 후 폐쇄된 사용자 그룹을 활성화하는 데 필요한 특수 고려 사항에 대해 알아봅니다.
hide: true
hidefromtoc: true
exl-id: f62ed751-d5e2-4a01-8910-c844afab5733
feature: Migration
role: Admin
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '374'
ht-degree: 10%

---

# 폐쇄형 사용자 그룹 마이그레이션 {#migrating-closed-user-groups}

>[!CONTEXTUALHELP]
>id="aemcloud_cug_migration"
>title="폐쇄형 사용자 그룹의 마이그레이션"
>abstract="폐쇄형 사용자 그룹(CUG)의 마이그레이션은 현재 마이그레이션 후 작동을 위한 몇 가지 확인 및 단계가 필요합니다."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-65/administering/security/closed-user-groups.html" text="AEM의 폐쇄형 사용자 그룹"

현재 폐쇄된 사용자 그룹(CUG)이 마이그레이션의 대상 환경에서 작동하려면 몇 가지 추가 단계가 필요합니다. 이 문서에서는 시나리오 및 의도한 방식으로 노드를 보호하는 데 필요한 단계에 대해 설명합니다.

## 그룹 마이그레이션

주체(그룹 포함)는 해당 콘텐츠의 ACL을 통해 마이그레이션된 콘텐츠와 연결된 경우 Adobe Experience Manager as a Cloud Service으로의 마이그레이션에 자동으로 포함되며, 해당 콘텐츠의 CUG 정책에서 참조되는 경우에도 포함됩니다.

## 마이그레이션 중 폐쇄된 사용자 그룹

라이브로 전환하기 전에 그룹 및 해당 멤버가 있는지 확인해야 합니다. 수집 작업 보기를 통해 다운로드한 주체 보고서를 사용하여 해당 그룹이 포함되었는지 또는 해당 그룹이 ACL 또는 CUG 정책에 없었기 때문에 포함되지는 않았는지 확인할 수 있습니다.

그런 다음 프로세스를 트리거하고 속성을 설정하여 CUG를 활성화해야 합니다. 이렇게 하려면 CUG 정책과 연결된 모든 페이지를 다시 게시합니다. 게시 인스턴스를 보정하여 정책을 추적합니다.

이렇게 하면 게시에서 CUG 정책을 사용할 수 있으며, 정책과 연결된 그룹의 멤버인 인증된 사용자만 콘텐츠에 액세스할 수 있습니다.

## 요약

요약하면 마이그레이션 후 CUG를 활성화하는 단계는 다음과 같습니다.

1. CUG 정책에 사용된 각 그룹이 마이그레이션 후 게시에 있는지 확인합니다.
   - 그룹은 마이그레이션된 콘텐츠의 CUG 정책 또는 해당 콘텐츠의 ACL에 포함된 경우 존재할 수 있습니다.
   - 그렇지 않은 경우 패키지를 사용하여 대상 인스턴스에 설치하고(또는 해당 인스턴스에서 수동으로 만들기) 대상 인스턴스 및 해당 멤버를 활성화합니다. 그런 다음 Publish에 있는지 확인합니다.
1. 예를 들어 페이지를 먼저 편집하여 게시되도록 CUG 정책과 연관된 모든 페이지를 다시 게시합니다. 모두 다시 게시하는 것이 중요합니다.
   - 모든 페이지가 다시 게시되면 CUG로 보호된 각 페이지에 대한 기능을 확인합니다.
