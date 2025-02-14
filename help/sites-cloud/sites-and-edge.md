---
title: AEM Sites 및 Edge Delivery Services
description: Edge Delivery Services가 콘텐츠 제작을 가속화하고 100% 성능으로 사이트를 제공하기 위해 AEM Sites의 작성 및 게시 기능을 확장하는 방법을 알아봅니다.
solution: Experience Manager Sites
feature: Authoring
role: User
exl-id: 7747d6f7-18e4-4713-baea-bcfa94f54934
source-git-commit: 10580c1b045c86d76ab2b871ca3c0b7de6683044
workflow-type: ht
source-wordcount: '618'
ht-degree: 100%

---

# AEM Sites 및 Edge Delivery Services {#sites-and-edge}

Edge Delivery Services가 콘텐츠 제작을 가속화하고 100% 성능으로 사이트를 제공하기 위해 AEM Sites의 작성 및 게시 기능을 확장하는 방법을 알아봅니다.

## 개요 {#overview}

클라우드 네이티브 AEM as a Cloud Service 플랫폼의 일부로 [AEM Sites as a Cloud Service가 제공하는 모든 강력한 기능](/help/sites-cloud/sites-cloud-changes.md)에 더해, Edge Delivery Services는 콘텐츠 제작을 가속화하고 100% 성능으로 사이트를 제공할 수 있도록 추가적인 작성 및 게시 옵션을 제공합니다.

## Edge Delivery Services는 무엇입니까? {#what-is-edge}

Edge Delivery Services는 작성 및 개발 속도가 빠른 효과적인 경험을 제공하여 참여와 전환을 촉진하는 탁월한 경험을 제공합니다. 작성자가 콘텐츠를 빠르게 업데이트 및 게시하고 새 사이트를 신속하게 시작할 수 있는 신속한 개발 환경을 지원하는 구성 가능한 서비스 세트입니다. [Edge Delivery Services 개요](/help/edge/overview.md) 문서에서 Edge Delivery Services에 대해 자세히 알아보십시오.

Edge Delivery Services와 AEM Sites as a Cloud Service를 사용하면 프로젝트에서 다음의 이점을 누릴 수 있습니다.

* [새로운 개발자 경험](#developer-experience)
* [새로운 게시 계층](#publish-tier)
* [추가적인 작성 옵션](#authoring-options)

## 새로운 개발자 경험 {#developer-experience}

Edge Delivery Services의 핵심 철학은 *속도*&#x200B;입니다. 이는 개발자 경험에서 시작됩니다. 개발자가,

* Git 기본 사항을 이해하고
* HTML, CSS 및 JavaScript의 기본 사항을 파악하고 있는 경우

30분 이내에 Edge Delivery Services에 맞게 자체 프로젝트와 구성 요소를 맞춤화할 수 있습니다. 먼저 GitHub에서 상용구 플레이트 프로젝트를 복제한 다음 변경 사항을 커밋하기만 하면 됩니다. 사용자만의 맞춤화가 즉시 적용됩니다!

Edge Delivery Services 개발에 대한 자세한 내용은 [시작 안내서 - 개발자 튜토리얼](https://www.aem.live/developer/tutorial) 문서를 참조하십시오.

## 새로운 게시 계층 {#publish-tier}

개발 시간이 획기적으로 단축될 뿐만 아니라 Edge Delivery Services는 매우 빠른 웹 사이트를 제공합니다.

## 추가적인 작성 옵션 {#authoring-options}

또한 Edge Delivery Services는 새로운 작성 옵션을 제공하여 콘텐츠 제작 속도를 높입니다.

### 범용 편집기 {#universal-editor}

범용 편집기는 모든 콘텐츠를 작성하는 데 사용할 수 있는 원활한 WYSIWYG 작성 환경을 제공합니다.

범용 편집기를 통한 콘텐츠 작성에 대한 자세한 내용은 [Edge Delivery Services를 위한 WYSIWYG 콘텐츠 작성](/help/edge/wysiwyg-authoring/authoring.md) 문서를 참조하십시오.

### 문서 기반 작성 {#document-authoring}

문서 기반 작성은 누구에게나 익숙한 도구인 Word 및 Google Docs를 활용하여 별도의 교육 없이 콘텐츠를 만들 수 있습니다. Edge Delivery Services는 이러한 간단한 도구를 사용하여 Word 문서의 변경 사항을 실시간으로 사이트에서 업데이트된 콘텐츠로 즉시 변환할 수 있습니다.

문서 기반 작성 사용에 대한 자세한 내용은 [콘텐츠 작성 및 게시](https://www.aem.live/docs/authoring) 문서를 참조하십시오.

## Edge가 적합합니까? {#decision}

Adobe는 모든 규모의 프로젝트에서 Edge Delivery Services를 통해 고객과 관련자들이 엄청난 혜택을 얻는 것을 보았습니다. 이러한 이유로 Adobe는 새로운 프로젝트의 시작점으로 Edge Delivery Services를 활용할 것을 권장합니다.

또한 나머지는 현재 스택에 보관하면서 Edge Delivery에 하위 사이트 또는 페이지를 배포할 수도 있습니다. 성능, 유기적 트래픽, 고객 참여, 개발자 또는 콘텐츠 속도의 개선이 필요할 때마다 이 방법을 사용하는 것을 권장합니다.

Edge Delivery가 자신에게 적합한지 확실하지 않은 경우 Adobe 담당자에게 문의하시기 바랍니다.

### Edge Delivery와 Headless는 어떻습니까? (#headless)

Edge Delivery는 백엔드에서 분리된 성능 우선 헤드입니다. React SPA와 같은 사용자 정의 헤드가 있는 경우 Adobe는 AEM Headless 통합 패턴을 권장합니다. 자세한 내용은 [AEM Headless 설명서](/help/headless/introduction.md)를 참조하십시오.

그러나 Adobe는 일반적으로 Edge Delivery를 기본 헤드로 사용하여 속도와 성능을 이점을 얻고 Headless 접근 방식(예: React 또는 SPA)을 통해 프로젝트의 Headless 부분(일반적으로 비즈니스 애플리케이션)을 통합할 것을 권장합니다.
