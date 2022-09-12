---
title: AEM as a Cloud Service 용어
description: AEMaaCS에 로그인하기 전에 시스템의 일부 용어 및 기본 구조를 이해하는 것이 도움이 됩니다.
exl-id: d02776a7-836a-4894-a5d5-ae88cc7e4e76
source-git-commit: 097c17b37cc308dc906cd4af7dc7c5d51862bdfa
workflow-type: tm+mt
source-wordcount: '463'
ht-degree: 20%

---

# AEM as a Cloud Service 용어 {#terminology}

의 이 부분에서 [온보딩 여정,](overview.md) AEM as a Cloud Service의 용어 및 기본 구조의 일부를 알아봅니다.

## 목표 {#objective}

이제 문서를 참조하여 온보딩 프로세스를 시작한 상황을 이해하십시오 [온보딩 준비,](preparation.md) 로그인하기 전에 시스템의 일부 용어 및 기본 구조를 이해하는 데 도움이 됩니다.

AEM as a Cloud Service 은 강력하고 유연한 도구이며, 이 도구를 사용하는 데 필요한 조직과 용어 및 언어를 잘 알고 있어야 합니다. 이 문서에서는 시스템 사용을 시작하기 전에 이해해야 하는 몇 가지 주요 용어를 요약합니다.

이 문서를 읽은 후에는 다음 사항을 이해할 수 있습니다.

* AEMaaCS를 구성하는 다양한 레이어.
* 각 레이어가 수행하는 작업의 기본 사항입니다.

## AEMaaCS 구조 {#structure}

이 온보딩 여정을 위해 AEM as a Cloud Service 구조를 완전히 이해할 필요가 없습니다. 그러나 다음 개념에 익숙해지면 여정에서 나중에 따라하기가 더 쉽습니다.

![Cloud Manager 구조](/help/journey-sites/quick-site/assets/cloud-manager-structure.png)

* **테넌트** - 모든 고객은 테넌트를 사용하여 프로비저닝됩니다. 테넌트는 IMS 조직이라고도 합니다(이 여정 뒷부분에서 IMS에 대해 자세히 알아보기)
* **프로그램** - 각 테넌트에는 고객의 라이선스가 부여된 솔루션을 반영하는 하나 이상의 프로그램이 있습니다.
* **환경** - 각 프로그램에는 라이브 콘텐츠 프로덕션 환경, 스테이징 환경 및 개발 목적의 환경 등 여러 환경이 있습니다.
* **저장소** - 환경에는 애플리케이션 및 프런트 엔드 코드가 유지 관리되는 Git 리포지토리가 하나 이상 있습니다.
* **도구 및 워크플로** - 파이프라인은 저장소에서 환경으로의 코드 배포를 관리합니다.

이러한 계층 구조를 컨텍스트화하는 데 도움이 되는 예시가 있습니다.

* WKND Travel 및 Adventure Enterprises는 여행 관련 미디어에 중점을 두는 **테넌트**&#x200B;일 수 있습니다.
* WKND여행과 어드벤처 기업 임차인은 두 개를 가질 수 있습니다 **프로그램**:
   * WKND매거진사업부의 일인사이트 프로그램
   * WKND 미디어 사업부를 위한 하나의 자산 프로그램
* WKND Magazine과 WKND Media 프로그램은 둘 다 개발, 스테이징 및 프로덕션을 가질 것입니다 **환경**.
* **저장소** 는 WKND Magazine 및 WKND Media에 대한 사용자 지정 코드 및 애플리케이션을 유지 관리하는 데 사용됩니다.
* 다양한 **도구 및 워크플로우** 보고서 전체에서 CI/CD 파이프라인, 액세스 로그, AEM 액세스 등을 사용하여 코드를 배포합니다.

## 다음은 무엇입니까? {#what-is-next}

이제 AEM 온보딩 여정의 이 부분을 완료했으므로 다음 내용을 이해해야 합니다.

* AEMaaCS를 구성하는 다양한 레이어.
* 각 레이어가 수행하는 작업의 기본 사항입니다.

이 지식을 바탕으로 작성되고 다음에 문서를 읽어서 AEM 온보딩 여정을 계속합니다 [Admin Console 액세스](admin-console.md): 콘솔에 액세스하고 시스템 관리자로서의 상태를 확인하는 방법을 알아봅니다.
