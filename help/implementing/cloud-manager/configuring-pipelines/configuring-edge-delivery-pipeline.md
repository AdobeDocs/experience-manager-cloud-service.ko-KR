---
title: Edge Delivery 파이프라인 추가
description: Edge Delivery 파이프라인을 추가하여 코드를 빌드하고 프로덕션 환경에 배포하는 방법을 알아봅니다.
index: true
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
badge: label="얼리 어답터" type="Positive" url="/help/implementing/cloud-manager/release-notes/current.md#gitlab-bitbucket"
hide: true
hidefromtoc: true
source-git-commit: 22289138be1fa63caa1beda83e98ffa75dfabc2a
workflow-type: tm+mt
source-wordcount: '114'
ht-degree: 0%

---


# Edge Delivery 파이프라인 추가 {#configure-edge-delivery-pipeline}

코드를 빌드하고 프로덕션 환경에 배포하기 위해 프로덕션 파이프라인을 구성하는 방법을 알아봅니다. 프로덕션 파이프라인은 먼저 코드를 스테이징 환경에 배포합니다. 승인 시 프로덕션 환경에 동일한 코드를 배포합니다.

Edge Delivery 파이프라인을 구성하려면 사용자에게 **[배포 관리자](/help/onboarding/cloud-manager-introduction.md#role-based-permissions)** 역할이 있어야 합니다.

>[!NOTE]
>
>이 문서에 설명된 기능은 얼리어답터 프로그램을 통해서만 사용할 수 있습니다. 자세한 내용을 알고 얼리 어답터로 등록하려면 [자신의 Git 가져오기](/help/implementing/cloud-manager/release-notes/current.md#gitlab-bitbucket)를 참조하세요.