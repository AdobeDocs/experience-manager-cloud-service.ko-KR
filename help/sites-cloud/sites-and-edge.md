---
title: AEM Sites 및 Edge Delivery Services
description: Edge Delivery Services이 어떻게 AEM Sites의 작성 및 게시 가능성을 확장하여 컨텐츠 생성을 가속화하고 사이트를 100% 성능으로 제공하는지 이해합니다.
solution: Experience Manager Sites
feature: Authoring
role: User
source-git-commit: b3497f87446ca4c1c71d48f29aebcaa882feb898
workflow-type: tm+mt
source-wordcount: '618'
ht-degree: 5%

---


# AEM Sites 및 Edge Delivery Services {#sites-and-edge}

Edge Delivery Services이 어떻게 AEM Sites의 작성 및 게시 가능성을 확장하여 컨텐츠 생성을 가속화하고 사이트를 100% 성능으로 제공하는지 이해합니다.

## 개요 {#overview}

AEM Sitesas a Cloud Service 이 클라우드 기반 AEM as a Cloud Service 플랫폼의 일부로 제공하는 모든 [기능과 기능](/help/sites-cloud/sites-cloud-changes.md)에 더하여, Edge Delivery Services은 콘텐츠 생성을 가속화하고 100% 성능으로 사이트를 제공할 수 있는 추가적인 작성 및 게시 기능을 제공합니다.

## Edge Delivery Services 소개 {#what-is-edge}

Edge Delivery Services은 작성 및 개발 속도가 빠른 영향력이 큰 경험을 제공함으로써 참여와 전환을 유도하는 탁월한 경험을 제공합니다. 작성자가 콘텐츠를 빠르게 업데이트 및 게시하고 새 사이트를 신속하게 시작할 수 있는 신속한 개발 환경을 지원하는 구성 가능한 서비스 세트입니다. [Edge Delivery Services 개요](/help/edge/overview.md) 문서에서 Edge Delivery Services에 대해 자세히 알아보세요.

AEM Sitesas a Cloud Service 와 함께 Edge Delivery Services을 사용하면 프로젝트의 이점을 다음과 같이 누릴 수 있습니다.

* [새로운 개발자 경험](#developer-experience)
* [새 게시 계층](#publish-tier)
* [추가 작성 옵션](#authoring-options)

## 새로운 개발자 경험 {#developer-experience}

Edge Delivery Services의 핵심 철학은 *속도*&#x200B;입니다. 개발자 경험부터 시작합니다. 개발자가

* Git 기본 사항 이해 및
* HTML, CSS 및 JavaScript 기본 사항 이해

30분 이내에 Edge Delivery Services에 대한 자체 프로젝트 및 구성 요소를 맞춤화하고 실행할 수 있습니다. 먼저 GitHub에서 표준 템플릿 프로젝트를 복제한 다음 변경 사항을 커밋하십시오. 맞춤화가 즉시 라이브 상태가 됩니다!

Edge Delivery Services 개발에 대한 자세한 내용은 [시작하기 - 개발자 자습서](https://www.aem.live/developer/tutorial) 문서를 참조하십시오.

## 새로운 Publish 계층 {#publish-tier}

개발 시간이 획기적으로 단축되었을 뿐만 아니라 Edge Delivery Services이 매우 빠른 웹 사이트를 제공합니다.

## 추가 작성 옵션 {#authoring-options}

또한 Edge Delivery Services은 새로운 작성 옵션을 제공하여 콘텐츠 제작 속도를 높입니다.

### 유니버설 편집기 {#universal-editor}

유니버설 편집기는 콘텐츠를 작성하는 데 사용할 수 있는 WYSIWYG(보이는 그대로) 작성 환경을 매끄럽게 제공합니다.

범용 편집기를 사용한 Edge Delivery Services 작성에 대한 자세한 내용은 [콘텐츠를 위한 WYSIWYG 콘텐츠 작성](/help/edge/wysiwyg-authoring/authoring.md) 문서를 참조하십시오.

### 문서 기반 작성 {#document-authoring}

문서 기반 작성을 사용하면 누구나 알고 있는 Word 및 Google 문서를 활용하여 교육 없이 콘텐츠를 만들 수 있습니다. Edge Delivery Services은 이러한 간단한 도구를 사용하여 Word 문서의 변경 사항을 라이브 사이트에서 업데이트된 콘텐츠로 즉시 변환할 수 있습니다.

문서 기반 작성 사용에 대한 자세한 내용은 [콘텐츠 작성 및 게시](https://www.aem.live/docs/authoring) 문서를 참조하십시오.

## Edge이 적합합니까? {#decision}

Adobe은 고객과 관련 이해 당사자가 규모에 관계없이 모든 프로젝트에 걸쳐 Edge Delivery Services의 혜택을 크게 누릴 수 있도록 지원했습니다. 이러한 이유로 Adobe에서는 Edge Delivery Services을 새 프로젝트의 시작점으로 활용할 것을 권장합니다.

나머지 부분은 현재 스택에 유지하면서 Edge Delivery에서 사이트 또는 페이지의 하위 집합을 배포할 수도 있습니다. 성능, 유기 트래픽, 고객 참여, 개발자 또는 콘텐츠 속도 개선이 필요할 때마다 권장됩니다.

Edge Delivery이 적합한지 확실하지 않은 경우 Adobe 담당자에게 문의하십시오.

### Edge Delivery 및 Headless는 어떻습니까? (#headless)

Edge Delivery은 백엔드에서 분리된 성능 우선 헤드입니다. React SPA과 같은 사용자 지정 헤드가 있는 경우 Adobe은 AEM Headless 통합 패턴을 권장합니다. 자세한 내용은 [AEM Headless 설명서](/help/headless/introduction.md)를 참조하십시오.

그러나 Adobe은 일반적으로 Edge Delivery을 기본 헤드로 사용하여 속도와 성능을 향상시키고 헤드리스 접근(예: React 또는 SPA)을 통해 프로젝트의 헤드리스 부분(일반적으로 비즈니스 애플리케이션)을 통합하는 것을 권장합니다.
