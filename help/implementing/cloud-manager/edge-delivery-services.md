---
title: Cloud Manager에서의 Edge Delivery Services 지원
description: Edge Delivery Services을 사용하여 Cloud Manager 프로젝트를 제공하는 방법을 알아봅니다.
exl-id: f33bd6f0-62fc-4ecc-b8d2-65d1f1c44d82
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: f9ba9fefc61876a60567a40000ed6303740032e1
workflow-type: tm+mt
source-wordcount: '283'
ht-degree: 28%

---

# Cloud Manager에서의 Edge Delivery Services 지원 {#edge-delivery-services}

Edge Delivery Services을 사용하여 Cloud Manager 프로젝트를 제공하는 방법을 알아봅니다.

>[!NOTE]
>
>이 기능은 [얼리 어답터 프로그램](/help/implementing/cloud-manager/release-notes/current.md#early-adoption)에만 사용할 수 있습니다.

## 간략한 Edge Delivery Services {#edge-overview}

Edge Delivery Services는 웹 사이트에서 콘텐츠를 작성하는 방법을 보다 유연하게 제공하는 구성 가능한 서비스 세트입니다. 이를 통해 다음을 수행할 수 있습니다.

* 완벽한 Lighthouse 점수로 빠른 사이트를 만들고 RUM(Real Use Monitoring)을 통해 지속적으로 성능을 모니터링합니다.
* 콘텐츠 소스를 분리하여 작성 효율성을 높입니다.

범용 편집기를 사용하여 AEM 콘텐츠 관리 및 WYSIWYG 작성과 문서 기반 작성을 모두 사용할 수 있습니다.

AEM as a Cloud Service의 Cloud Manager을 사용하면 프로젝트에 Edge Delivery 서비스를 활성화할 수 있습니다.

>[!TIP]
>
>Edge Delivery Services 및 AEM에서 사용할 수 있는 방법에 대한 자세한 내용은 [Edge Delivery Services 개요](/help/edge/overview.md) 문서를 참조하십시오.

## Cloud Manager의 Edge Delivery Services {#edge-in-cloud-manager}

Adobe Experience Manager Sites의 일부로 Edge Delivery Services 라이선스가 부여된 경우 Cloud Manager에서 직접 Edge Delivery Services을 사용하여 사이트를 온보딩하고 가이드 셀프 서비스 환경을 사용하여 [라이브로 전환할 수 있습니다.](/help/implementing/cloud-manager/managing-code/private-repositories.md)

이를 통해 모든 AEM 속성에 대해 통합된 경험이 가능해지며 도메인 이름 관리, SSL 인증서 관리 및 CDN 매핑을 포함한 모든 중요한 워크플로와의 일관성이 보장됩니다.

Edge Delivery Services은 [프로덕션 프로그램과 샌드박스 프로그램 모두에서 사용할 수 있습니다.](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/program-types.md)

## 활성화 Edge Delivery Services {#enabling}

새 프로그램을 추가할 때 Edge Delivery Services을 활성화할 수 있습니다.

![Edge Delivery Services이 있는 프로덕션 프로그램 추가](assets/add-production-program-with-edge.png)

프로그램 추가에 대한 자세한 내용은 다음 문서를 참조하십시오.

* [프로덕션 프로그램 만들기](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-production-programs.md)
* [샌드박스 프로그램 만들기](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-sandbox-programs.md)
