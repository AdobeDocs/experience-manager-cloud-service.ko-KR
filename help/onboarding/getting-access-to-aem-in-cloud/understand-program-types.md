---
title: 프로그램 및 프로그램 유형 이해
description: 프로그램 및 프로그램 유형 이해 - Cloud Services
translation-type: tm+mt
source-git-commit: 14da491cf09ed46ea425a8d65670d8b851aef388
workflow-type: tm+mt
source-wordcount: '151'
ht-degree: 3%

---


# 프로그램 및 프로그램 유형 이해 {#understanding-programs}

Cloud Manager에서는 임차인 엔티티가 맨 위에 있으며 이 엔티티에 여러 프로그램이 포함될 수 있습니다.  각 프로그램에는 두 개 이상의 프로덕션 환경과 여러 개의 비프로덕션 환경이 포함될 수 있습니다.

다음 다이어그램은 Cloud Manager의 엔티티 계층 구조를 보여 줍니다.

![이미지](assets/program-types1.png)

## 프로그램 유형 {#program-types}

사용자는 **샌드박스** 또는 **일반** 프로그램을 만들 수 있습니다.

*샌드박스*&#x200B;는 일반적으로 교육, 데모 실행, 지원, POC 또는 설명서를 제공하기 위해 만들어집니다. 그것은 라이브 트래픽을 운반하기 위한 것이 아니며, 정규 프로그램이 그렇지 않을 수 있는 제한을 갖을 것이다. 사이트 및 에셋이 포함되며 샘플 코드, 개발 환경 및 비프로덕션 파이프라인이 포함된 Git 분기로 자동 채워집니다.

나중에 적절한 시간에 라이브 트래픽을 사용하도록 *정규 프로그램*&#x200B;이 생성됩니다.