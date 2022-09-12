---
title: 프로그램 및 프로그램 유형
description: Cloud Manager의 계층 구조, 다양한 유형의 프로그램이 해당 구조에 어떻게 적합한지, 그리고 어떻게 다른지에 대해 알아봅니다.
exl-id: 507df619-a5b5-419a-9e38-db77541425a2
source-git-commit: 74e17ccb93c97dd6881c9b63d9a2d784d3add430
workflow-type: tm+mt
source-wordcount: '533'
ht-degree: 17%

---


# 프로그램 및 프로그램 유형 {#understanding-programs}

Cloud Manager는 엔티티 계층 구조를 기반으로 구축됩니다. 이러한 세부 사항은 Cloud Manager에서 수행하는 일상적인 작업에 중요하지 않지만, 이를 개괄적으로 설명하면 프로그램을 이해하고 직접 설정할 수 있습니다.

![Cloud Manager 계층](assets/program-types1.png)

* **테넌트** - 계층 구조의 맨 위에 있습니다. 모든 고객에게 테넌트가 제공됩니다.
* **프로그램.** - 각 임차인마다 하나 이상의 프로그램이 있습니다. [고객의 라이센스 솔루션을 자주 반영합니다.](introduction-production-programs.md)
* **환경** - 각 프로그램에는 라이브 콘텐츠 프로덕션 환경, 스테이징 환경 및 개발 목적의 환경 등 여러 환경이 있습니다.
   * 각 프로그램에는 하나의 프로덕션 환경만 사용할 수 있지만 여러 비프로덕션 환경이 있을 수 있습니다.
* **저장소** - 프로그램에는 환경에 대해 애플리케이션 및 프런트 엔드 코드가 유지되는 Git 리포지토리가 있습니다.
* **도구 및 워크플로우** - 파이프라인은 저장소에서 환경으로의 코드 배포를 관리하는 반면, 다른 도구는 로그 액세스, 모니터링 및 환경 관리를 허용합니다.

이러한 계층 구조를 컨텍스트화하는 데 도움이 되는 예시가 있습니다.

* WKND Travel 및 Adventure Enterprises는 여행 관련 미디어에 중점을 두는 **테넌트**&#x200B;일 수 있습니다.
* WKND Travel 및 Adventure Enterprises 테넌트에는 WKND Magazine용 Sites 프로그램 및 WKND Media용 Assets 프로그램, 이러한 두 개의 **프로그램**&#x200B;이 있을 수 있습니다.
* WKND Magazine 및 WKND Media 프로그램은 모두 개발, 스테이지 및 프로덕션 **환경**&#x200B;을 가질 수 있습니다.

## 소스 코드 저장소 {#source-code-repository}

Cloud Manager 프로그램은 자체 Git 리포지토리를 사용하여 자동으로 제공됩니다.

Cloud Manager git 리포지토리에 액세스하려면 명령줄 도구, 독립 실행형 시각적 Git 클라이언트 또는 Eclipse, IntelliJ 또는 NetBeans와 같은 사용자의 IDE를 사용하여 git 클라이언트를 사용해야 합니다.

Git 클라이언트가 설정되면 Cloud Manager UI에서 Git 리포지토리를 관리할 수 있습니다. Cloud Manager UI를 사용하여 git을 관리하는 방법에 대한 자세한 내용은 문서를 참조하십시오 [Git 액세스.](/help/implementing/cloud-manager/managing-code/accessing-repos.md)

AEM Cloud 애플리케이션 개발을 시작하려면 Cloud Manager 저장소에서 로컬 컴퓨터의 위치로 애플리케이션 코드의 로컬 복사본을 체크 아웃해야 합니다.

```java
$ git clone {URL}
```

워크플로우는 표준 Git 워크플로우입니다.

1. 사용자가 Git 리포지토리의 로컬 복사본을 복제합니다.
1. 사용자가 로컬 코드 리포지토리에서 변경 작업을 수행합니다.
1. 준비가 완료된 사용자는 변경 사항을 다시 원격 Git 리포지토리에 커밋합니다.

유일한 차이점은 원격 Git 리포지토리가 개발자에게 투명하게 제공되는 Cloud Manager의 일부라는 것입니다.

## 프로그램 유형 {#program-types}

사용자는 **production** 프로그램 또는 **샌드박스** 프로그램.

* A **생산 프로그램** 사이트에 대해 라이브 트래픽을 활성화하도록 가 생성되었습니다.
   * 문서를 참조하십시오 [프로덕션 프로그램 소개](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/introduction-production-programs.md) 자세한 내용
* A **샌드박스 프로그램** 는 일반적으로 교육, 데모 실행, 사용, POC 또는 설명서 용도로 사용됩니다.
   * 샌드박스 환경은 라이브 트래픽을 전달하기 위한 것이 아니며 프로덕션 프로그램이 허용하지 않을 제한 사항을 갖습니다.
   * 여기에는 사이트 및 자산이 포함되며, 샘플 코드, 개발 환경 및 비프로덕션 파이프라인이 포함된 Git 분기로 자동으로 채워집니다.
   * 문서를 참조하십시오 [샌드박스 프로그램 소개](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/introduction-sandbox-programs.md) 자세한 내용
