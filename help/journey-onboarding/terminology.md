---
title: AEM as a Cloud Service 용어
description: AEMaaCS에 로그인하기 전에 시스템 용어와 기본 구조를 이해하는 것이 좋습니다.
exl-id: d02776a7-836a-4894-a5d5-ae88cc7e4e76
source-git-commit: a3e79441d46fa961fcd05ea54e84957754890d69
workflow-type: tm+mt
source-wordcount: '461'
ht-degree: 87%

---

# AEM as a Cloud Service 용어 {#terminology}

의 이 부분에서 [온보딩 여정,](overview.md) AEM as a Cloud Service의 일부 용어와 기본 구조를 배웁니다.

## 목표 {#objective}

이제 [온보딩 준비](preparation.md) 문서를 읽고 온보딩 프로세스로 이어지는 과정을 이해했으므로 로그인하기 전에 시스템의 일부 용어와 기본 구조를 이해하는 것이 좋습니다.

AEM as a Cloud Service는 강력하고 유연한 도구이며, 도구를 사용하려면 해당 조직과 해당 도구를 설명하는 데 사용되는 용어 및 언어에 익숙해야 합니다. 이 문서에는 시스템 사용을 시작하기 전에 이해해야 하는 몇 가지 주요 용어가 요약되어 있습니다.

이 문서를 읽은 후에는 다음 사항을 이해할 수 있습니다.

* AEMaaCS를 구성하는 다양한 계층
* 각 계층이 수행하는 작업의 기본 사항

## AEMaaCS 구조 {#structure}

이 온보딩 여정에서는 목적상 AEM as a Cloud Service의 구조를 완전히 이해할 필요는 없습니다. 그러나 다음 개념에 익숙해지면 나중에 여정을 따라가기가 더 쉬워질 것입니다.

![Cloud Manager 구조](/help/journey-sites/quick-site/assets/cloud-manager-structure.png)

* **테넌트** - 모든 고객은 테넌트를 사용하여 프로비저닝됩니다. 테넌트는 IMS 조직이라고도 합니다(이 여정의 뒷부분에서 IMS에 대해 자세히 설명).
* **프로그램** - 각 테넌트에는 고객의 라이선스가 부여된 솔루션을 반영하는 하나 이상의 프로그램이 있습니다.
* **환경** - 각 프로그램에는 라이브 콘텐츠 프로덕션 환경, 스테이징 환경 및 개발 목적의 환경 등 여러 환경이 있습니다.
* **저장소** - 환경에는 애플리케이션 및 프론트엔드 코드가 유지되는 git 저장소가 하나 이상 있습니다.
* **도구 및 워크플로** - 파이프라인은 저장소에서 환경으로의 코드 배포를 관리합니다.

이러한 계층 구조를 컨텍스트화하는 데 도움이 되는 예시가 있습니다.

* WKND Travel 및 Adventure Enterprises는 여행 관련 미디어에 중점을 두는 **테넌트**&#x200B;일 수 있습니다.
* WKND Travel 및 Adventure Enterprises 테넌트에는 두 개의 **프로그램**&#x200B;이 있을 수 있습니다.
   * WKND Magazine 사업부를 위한 Sites 프로그램 1개
   * WKND Media 사업부를 위한 Assets 프로그램 1개
* WKND Magazine 및 WKND Media 프로그램은 모두 개발, 스테이징 및 프로덕션 **환경**&#x200B;을 가질 수 있습니다.
* **저장소**&#x200B;는 WKND Magazine 및 WKND Media에 대한 사용자 정의 코드 및 애플리케이션을 유지 관리하는 데 사용됩니다.
* CI/CD 파이프라인, 액세스 로그, 액세스 AEM 등을 통해 코드를 배포하기 위해 저장소 전체에서 다양한 **도구 및 워크플로**&#x200B;가 사용됩니다.

## 다음 단계 {#what-is-next}

이제 AEM 온보딩 여정의 이 부분을 완료했으므로 다음 사항을 이해해야 합니다.

* AEMaaCS를 구성하는 다양한 계층
* 각 계층이 수행하는 작업의 기본 사항

이 지식을 기반으로 다음 문서를 검토하여 AEM 온보딩 여정을 계속하십시오 [Admin Console 액세스](admin-console.md)- 콘솔에 액세스하고 시스템 관리자로서 상태를 확인하는 방법을 배울 수 있습니다.
