---
title: Edge Delivery Services 개요
description: AEM as a Cloud Service가 Edge Delivery Services에서 제공하는 성능과 완벽한 Lighthouse Score를 통해 얻을 수 있는 이점을 알아봅니다.
feature: Edge Delivery Services
exl-id: 03a1aa93-d2e6-4175-9cf3-c7ae25c0d24e
role: Admin, Architect, Developer
source-git-commit: bf0e840fb3cd1ea5bc832823c522415c066f0018
workflow-type: tm+mt
source-wordcount: '1286'
ht-degree: 76%

---


# Edge Delivery Services 개요 {#edge-delivery-services}

Edge Delivery Services를 사용하여 AEM은 참여 및 전환을 유도하는 탁월한 경험을 제공합니다. 이를 위해 AEM은 빠르게 작성 및 개발할 수 있는 영향력이 큰 경험을 제공합니다. 작성자가 콘텐츠를 빠르게 업데이트 및 게시하고 새 사이트를 신속하게 시작할 수 있는 신속한 개발 환경을 지원하는 구성 가능한 서비스 세트입니다. 그에 따라 Edge Delivery Services를 사용하여 전환을 개선하고, 비용을 절감하고, 최고의 콘텐츠 속도를 제공할 수 있습니다.

Edge Delivery Services를 사용하여 다음과 같은 작업을 수행할 수 있습니다.

* 완벽한 Lighthouse Score를 사용하여 빠른 사이트를 만들고 실제 사용 모니터링(RUM)을 통해 사이트 성과를 지속적으로 모니터링합니다.
* 콘텐츠 소스를 분리하여 작성 효율성을 높입니다. 즉시 범용 편집기를 사용한 AEM 작성과 문서 기반 작성을 모두 사용할 수 있습니다. 따라서 동일한 웹 사이트에서 여러 콘텐츠 소스로 작업할 수 있습니다.
* 기본 제공 실험 프레임워크를 사용하여 성능에 영향을 주지 않고도 빠르게 테스트를 작성 및 실행하고 테스트 승자 프로덕션에 대한 빠른 릴리스를 제공할 수 있습니다.

## 비즈니스 요구 사항에 맞춘 신속한 대응 {#agile-reaction}

오랫동안 업계를 선도해 온 Adobe는 귀사의 고객을 위한 새롭고 의미 있는 콘텐츠를 빠르게 제작하고 게시할 수 있는 역량이 얼마나 중요한지 알고 있습니다. 대규모로 콘텐츠를 제작할 때 다음과 같은 일반적인 어려움이 있음은 시장에서 명확히 드러나 있습니다.

1. **콘텐츠에 대한 수요는 계속해서 증가하고 있습니다.**
   * 이러한 수요에 발맞추기 위해서는 새로운 콘텐츠 작성자를 활용해야 합니다.
   * 콘텐츠 제작 과정에 있어서는 전사적으로 효과적인 규모 확장이 이루어져야 합니다.
   * 작성자들은 급변하는 트렌드에 신속하게 대응할 수 있는 역량이 있어야 합니다.
1. **옴니채널 콘텐츠에 대한 수요가 있습니다.**
   * 콘텐츠 게재와는 무관하게 레이아웃 제어가 필요합니다.
   * 작성자들은 콘텐츠 레이아웃을 직접 변경할 수 있는 권한을 부여받아야 합니다.
1. **콘텐츠의 ROI 제고에 대한 압력이 증가합니다.**
   * 작성자들은 스스로 제작한 콘텐츠를 최적화할 수 있는 능력을 보유해야 합니다.

이러한 트렌드는 업계 전체에 걸쳐 일관되게 나타나고 있습니다. 그러나 각각의 요구 사항은 프로젝트마다 다를 수 밖에 없습니다. 모든 Edge Delivery Services 프로젝트의 목표는 사용자에게 적합한 솔루션을 찾는 데 초점을 맞추고 있습니다.

1. **기능보다는 가치에 집중해야 합니다.** - AEM의 광범위한 기능 세트로 헤매기 보다는 작성자를 위한 가장 최적화된 워크플로를 결정하십시오.
1. **AEM의 유연성을 활용하십시오.** - 아무 것도 없는 상태에서 AEM 기능을 사용할 필요는 없습니다. 사용 사례에 맞는 적절한 기능을 사용하십시오.
1. **작성자들의 전문 지식을 활용하십시오.** - 실제 콘텐츠 작성자를 프로젝트에 처음부터 참여하도록 하여 합리적인 기능을 구현함으로써 필요한 가치를 제공하고 있는지 확인하십시오.

작성자들의 가치에 초점을 맞추면 Edge Delivery Services 프로젝트는 콘텐츠 제작자들이 마주하는 현대 업계의 요구 사항을 충족해 주며 고객이 만족하는 콘텐츠를 신속하게 제공할 수 있도록 해 줍니다.

## 콘텐츠 제작자를 위한 유연한 작성 도구 {#overview}

Edge Delivery Services는 웹 사이트에서 콘텐츠를 작성하는 방법을 보다 유연하게 제공하는 구성 가능한 서비스 세트입니다. [AEM 콘텐츠 관리](/help/sites-cloud/authoring/author-publish.md)와 [유니버설 편집기](/help/sites-cloud/authoring/universal-editor/authoring.md)를 사용한 콘텐츠 작성과 [문서 기반 작성을 모두 사용할 수 있습니다.](https://www.aem.live/docs/authoring)

다음 다이어그램은 범용 편집기를 사용하여 Microsoft Word(문서 기반 작성)에서 콘텐츠를 편집하고 AEM 콘텐츠 작성과 함께 Edge Delivery Services에 게시하는 방법을 보여 줍니다.

![Edge Delivery 아키텍처](assets/AEM-with-EDS-publishing-simple2.png)

Edge Delivery Services는 GitHub를 활용하므로 GitHub 저장소에서 바로 코드를 관리 및 배포할 수 있습니다. 새 콘텐츠는 리빌드 프로세스 없이 즉시 추가됩니다.

### 문서 기반 작성 {#document-based}

문서 기반 작성 기능을 통해 Microsoft Word 또는 Google 문서의 콘텐츠를 직접 사용하여 해당 소스가 웹 사이트의 페이지가 되도록 할 수 있습니다. 제목, 목록, 이미지, 글꼴 요소는 모두 초기 소스에서 웹 사이트로 전송할 수 있습니다.

* 문서 기반 작성 기능을 사용하면 모든 마케터가 친숙한 작성 도구(Microsoft Word, Google Docs 등)를 사용해 빠르게 콘텐츠를 제작할 수 있게 됩니다.
* 소스 문서 내에서 바로 작성, 검토, 게시가 가능해짐에 따라 콘텐츠 제작 과정이 간소화됩니다.
* 친숙한 도구를 사용하기 때문에 콘텐츠 작성자를 위한 별도의 온보딩이 필요하지 않아 콘텐츠 작업 속도가 빨라집니다.
* GitHub에서 CSS와 JavaScript를 사용하여 사이트 기능을 개발할 수 있습니다.

![문서 기반 작성](assets/document-based-authoring.png)

문서 기반 작성 설명서에서 더 자세히 읽어보기:

* Edge Delivery을 시작하는 방법에 대한 자세한 내용은 aem.live 설명서의 [빌드 섹션](https://www.aem.live/docs/#build)을 참조하십시오.
* Edge Delivery을 사용하여 콘텐츠를 작성하고 게시하는 방법에 대한 자세한 내용은 aem.live 설명서의 [게시 섹션](https://www.aem.live/docs/authoring)을 참조하십시오.
* 웹 사이트 프로젝트를 제대로 시작하는 방법을 이해하려면 aem.live 설명서의 [시작 섹션](https://www.aem.live/docs/#launch)을 참조하십시오.

### 범용 편집기를 사용한 AEM 작성{#wysiwyg-authoring}

범용 편집기는 콘텐츠를 실시간으로 편집할 수 있고 시각적 미리 보기를 통해 컨텍스트에 맞게 편집할 수 있는 사용자 지정 가능한 단일 위치입니다(WYSIWYG).

* 범용 편집기로 AEM을 작성하면 headless든 headful이든 작성자 효율성을 높일 수 있습니다.
* 워크플로 및 거버넌스 등, AEM의 포괄적인 콘텐츠 관리 기능을 활용할 수도 있습니다.
* 다양한 확장 지점을 활용하여 자체적인 프로세스와 통합을 지원해 보십시오.
* GitHub에서 CSS와 JavaScript를 사용하여 사이트 기능을 개발할 수 있습니다.

![범용 편집기로 AEM 작성](assets/wysiwyg-authoring.png)

범용 편집기 및 Edge Delivery Services을 사용하여 AEM 작성을 시작하십시오.

* 범용 편집기를 사용한 AEM 작성에 대한 개요는 aem.live 설명서에서 [Edge Delivery Services용 AEM으로 작성](https://www.aem.live/docs/aem-authoring) 문서를 참조하십시오.
* 개발자 개요는 aem.live 설명서에서 [시작하기 - 유니버설 편집기 개발자 자습서](https://www.aem.live/developer/ue-tutorial) 문서를 참조하십시오.

### 작성 방법 결정 {#authoring-method}

AEM은 작성 시 발생하는 요구 사항을 유연하게 충족해 줍니다. Adobe에서 귀하의 요구 사항에 가장 잘 맞는 방법을 결정할 수 있도록 도와드리겠습니다.

* 항상 콘텐츠 작성자가 의사 결정에 참여하도록 하십시오.
* 여러 가지 작성 방법을 구현할 수 있습니다.
* 작성 방법은 나중에 언제든지 변경 가능합니다.
* 구현 전에 결정할 필요가 없으며, 구현의 일부로서 결정해야 합니다.

## Edge Delivery Services 및 기타 Adobe Experience Cloud 제품 {#edge-other-products}

Edge Delivery Services는 Adobe Experience Manager의 일부입니다. 따라서 Edge Delivery Services와 AEM Sites는 동일 도메인에서 함께 존재할 수 있으며, 이는 대규모 웹 사이트의 일반적인 사용 사례입니다. 또한 AEM Sites 페이지에서 Edge Delivery Services의 콘텐츠를 원활하게 사용할 수 있으며 그 반대의 경우도 마찬가지입니다.

AEM 및 Edge Delivery Services을 사용하여 직접 프로젝트를 시작하여 제작하는 방법에 대해 알아보려면 aem.live 설명서에서 [시작하기 - 유니버설 편집기 개발자 튜토리얼](https://www.aem.live/developer/ue-tutorial) 문서를 참조하십시오.

[Adobe Target](https://www.aem.live/developer/target-integration), [RUM(Real Use Monitoring)](https://www.aem.live/developer/rum)과(와) 함께 Edge Delivery Services을 사용하여 사이트의 사용 및 성능을 진단할 수도 있고 [Launch.](https://experienceleague.adobe.com/ko/docs/experience-platform/tags/home)

## Adobe에서 도움 받기 {#getting-help}

Adobe에서는 Edge Delivery Services에 도움이 되는 세 가지 채널을 제공합니다.

* 일반적인 문의는 [커뮤니티 리소스](#community-resources)와 협력할 수 있습니다.
* 특정 질문은 [제품 협업 채널](#collaboration-channel)에 액세스할 수 있습니다.
* [지원 티켓을 기록](#support-ticket)하여 주요 및 중요한 문제를 해결할 수 있습니다.

### 커뮤니티 리소스에 액세스 {#community-resources}

Adobe은 Edge Delivery Services, 유니버설 편집기를 사용한 AEM 작성 및 문서 기반 작성에 대한 최상의 커뮤니티 참여 및 지원을 제공할 수 있도록 지원하기 위해 최선을 다하고 있습니다.

* [Experience League 커뮤니티](https://adobe.ly/3Q6kTKl)에 참여하여 질의하고, 피드백을 공유하고, 토론을 시작하고, Adobe 전문가와 AEM Advisor/Champs의 지원을 요청하고, 비슷한 생각을 가진 사람들과 실시간으로 소통할 수 있습니다.
* 보다 일반적인 플랫폼인 [디스코드 채널](https://discord.gg/aem-live)에 참여하여 실시간으로 상호 작용하고 아이디어를 빠르게 교환할 수 있습니다.

### 제품 협업 채널에 액세스하는 방법 {#collaboration-channel}

사용자와의 직접적인 소통 채널이 가지는 가치를 고려하여 모든 AEM 프로젝트는 시작부터 속도, 주요 업데이트와 체감 품질에 대한 확장 보고를 위해 Slack 채널을 설정합니다. Adobe로부터 조직과 관련된 Slack 채널에 가입하라는 초대를 받게 됩니다.

자세한 내용은 [Slack 봇 사용](https://www.aem.live/docs/slack) 문서를 참조하십시오.

프로비저닝된 제품 협업 채널을 통해 Adobe 제품 팀과 협력하여 제품 사용 또는 모범 사례에 대한 질문에 답변할 수 있습니다. 서비스 수준 목표(SLT)는 제품 협업 채널을 통해 대화와 연결되지 않습니다.

### 지원 티켓 기록 {#support-ticket}

{{support-ticket}}
