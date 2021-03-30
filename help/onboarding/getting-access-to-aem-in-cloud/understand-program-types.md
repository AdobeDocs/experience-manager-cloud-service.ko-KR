---
title: 프로그램 및 프로그램 유형 이해
description: 프로그램 및 프로그램 유형 이해 - Cloud Services
translation-type: tm+mt
source-git-commit: 6e8cf08ec3f85437a8472a45895f3818e473e98c
workflow-type: tm+mt
source-wordcount: '329'
ht-degree: 2%

---


# 프로그램 및 프로그램 유형 이해 {#understanding-programs}

Cloud Manager에서는 임차인 엔티티가 맨 위에 있으며 이 엔티티에 여러 프로그램이 포함될 수 있습니다. 각 프로그램에는 두 개 이상의 프로덕션 환경과 여러 개의 비프로덕션 환경이 포함될 수 있습니다.

다음 다이어그램은 Cloud Manager의 엔티티 계층 구조를 보여 줍니다.

![이미지](assets/program-types1.png)

## 소스 코드 저장소 {#source-code-repository}

클라우드 관리자 프로그램은 고유한 git 리포지토리로 자동 프로비저닝됩니다.

사용자가 Cloud Manager git 리포지토리에 액세스하려면 명령줄 툴, 독립 실행형 시각적 Git 클라이언트 또는 Eclipse, IntelliJ, NetBeans와 같은 사용자 IDE를 사용하는 Git 클라이언트를 사용해야 합니다.

Git 클라이언트가 설정되면 Cloud Manager UI에서 git 리포지토리를 관리할 수 있습니다. 클라우드 관리자 UI를 사용하여 Git을 관리하는 방법에 대한 자세한 내용은 [Git 액세스](/help/implementing/cloud-manager/accessing-git.md)를 참조하십시오.

AEM Cloud 응용 프로그램 개발을 시작하려면, Cloud Manager 저장소에서 해당 저장소를 만들 로컬 컴퓨터의 위치로 응용 프로그램 코드의 로컬 복사본을 체크 아웃하여 응용 프로그램 코드의 로컬 복사본을 만들어야 합니다.

```java
$ git clone {URL}
```

>[!NOTE]
>사용자는 코드의 사본을 확인하고 로컬 코드 리포지토리에서 변경할 수 있습니다. 준비가 되면 사용자는 코드 변경 사항을 Cloud Manager의 원격 코드 저장소로 다시 커밋할 수 있습니다.

## 프로그램 유형 {#program-types}

사용자는 **샌드박스** 또는 **프로덕션** 프로그램을 만들 수 있습니다.

* 나중에 적절한 시간에 라이브 트래픽을 사용하도록 *프로덕션 프로그램*이 생성됩니다.
자세한 내용은 [프로덕션 프로그램 소개](/help/onboarding/getting-access-to-aem-in-cloud/introduction-production-programs.md)을 참조하십시오.


* *샌드박스 프로그램*은 일반적으로 교육, 데모 실행, 지원, POC 또는 설명서를 제공하기 위해 제작됩니다. 라이브 트래픽을 전달하기 위한 것이 아니며 프로덕션 프로그램에서 허용하지 않는 제한 사항이 있습니다. 사이트 및 에셋이 포함되며 샘플 코드, 개발 환경 및 비프로덕션 파이프라인이 포함된 Git 분기로 자동 채워집니다.
자세한 내용은 [샌드박스 프로그램 소개](/help/onboarding/getting-access-to-aem-in-cloud/introduction-sandbox-programs.md)를 참조하십시오.

