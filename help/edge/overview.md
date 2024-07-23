---
title: Edge Delivery Services 개요
description: AEM as a Cloud Service가 Edge Delivery Services에서 제공하는 성능과 완벽한 Lighthouse Score를 통해 얻을 수 있는 이점을 알아봅니다.
feature: Edge Delivery Services
exl-id: 03a1aa93-d2e6-4175-9cf3-c7ae25c0d24e
role: Admin, Architect, Developer
source-git-commit: 6c7e704dff97e8549664618f879863c3ca0f8f86
workflow-type: tm+mt
source-wordcount: '1356'
ht-degree: 55%

---


# Edge Delivery Services 개요 {#edge-delivery-services}

Edge Delivery Services를 사용하여 AEM은 참여 및 전환을 유도하는 탁월한 경험을 제공합니다. 이를 위해 AEM은 빠르게 작성 및 개발할 수 있는 영향력이 큰 경험을 제공합니다. 작성자가 콘텐츠를 빠르게 업데이트 및 게시하고 새 사이트를 신속하게 시작할 수 있는 신속한 개발 환경을 지원하는 구성 가능한 서비스 세트입니다. 그에 따라 Edge Delivery Services를 사용하여 전환을 개선하고, 비용을 절감하고, 최고의 콘텐츠 속도를 제공할 수 있습니다.

Edge Delivery Services를 사용하여 다음과 같은 작업을 수행할 수 있습니다.

* 완벽한 Lighthouse Score를 사용하여 빠른 사이트를 만들고 실제 사용 모니터링(RUM)을 통해 사이트 성과를 지속적으로 모니터링합니다.
* 콘텐츠 소스를 분리하여 작성 효율성을 높입니다. 기본적으로 WYSIWYG와 문서 기반 작성을 모두 사용할 수 있습니다. 따라서 동일한 웹 사이트에서 여러 콘텐츠 소스로 작업할 수 있습니다.
* 기본 제공 실험 프레임워크를 사용하여 성능에 영향을 주지 않고도 빠르게 테스트를 작성 및 실행하고 테스트 승자 프로덕션에 대한 빠른 릴리스를 제공할 수 있습니다.

## 비즈니스 요구에 대한 민첩한 반응 {#agile-reaction}

오랜 기간 인정 받은 업계 리더인 Adobe은 고객에게 의미 있는 새로운 콘텐츠를 신속하게 제작하여 게시하는 것이 얼마나 중요한지 잘 알고 있습니다. 콘텐츠 제작의 확장에 대한 일반적인 과제는 다음과 같이 시장에 의해 명확히 되었습니다.

1. **콘텐츠 수요가 계속 증가하고 있습니다.**
   * 이러한 요구를 충족하기 위해 새로운 콘텐츠 작성자의 잠금을 해제해야 합니다.
   * 비즈니스 전반에 걸쳐 컨텐츠 제작 프로세스를 효과적으로 확장해야 합니다.
   * 작성자는 변화하는 트렌드에 신속하게 대응할 수 있어야 합니다.
1. **옴니채널 콘텐츠가 필요합니다.**
   * 컨텐츠 전달에 관계없이 레이아웃 제어가 필요합니다.
   * 작성자는 컨텐츠 레이아웃을 직접 변경할 수 있는 권한이 필요합니다.
1. **콘텐츠의 ROI를 높이는 압력이 증가합니다.**
   * 작성자 자신은 자신이 만드는 콘텐츠를 최적화하는 기능이 필요합니다.

이러한 경향은 업계 전반에서 일관성이 있음이 입증되었다. 그러나 개별 요구 사항은 프로젝트마다 필연적으로 다릅니다. 모든 Edge Delivery Services 프로젝트의 목표는 사용자에게 적합한 솔루션을 찾는 데 중점을 둡니다.

1. **기능 대신 값에 초점을 맞추십시오.** - AEM의 광범위한 기능 집합에서 손실되지 않고 작성자에게 제공할 수 있는 가장 최적화된 워크플로를 결정합니다.
1. **AEM의 유연성을 활용하십시오.** - 진공에서 AEM 기능을 사용할 필요가 없습니다. 사용 사례별로 필요한 기능을 사용하십시오.
1. **작성자의 전문 지식을 활용하십시오.** - 처음부터 프로젝트에 실제 콘텐츠 작성자를 참여시켜 적절한 기능을 구현함으로써 필요한 가치를 제공할 수 있습니다.

Edge Delivery Services 프로젝트는 작성자를 위한 가치에 중점을 둠으로써 콘텐츠 작성자가 직면한 최신 업계 요구를 충족하고 콘텐츠를 빠르게 제공하여 고객을 기쁘게 할 수 있습니다.

## 콘텐츠 작성자를 위한 유연한 작성 도구 {#overview}

Edge Delivery Services는 웹 사이트에서 콘텐츠를 작성하는 방법을 보다 유연하게 제공하는 구성 가능한 서비스 세트입니다. [범용 편집기](/help/sites-cloud/authoring/universal-editor/authoring.md)를 사용하는 [AEM 콘텐츠 관리](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/sites/authoring/getting-started/concepts.html) 및 WYSIWYG 작성과 [문서 기반 작성](https://www.aem.live/docs/authoring)을 모두 사용할 수 있습니다.

다음 다이어그램은 Microsoft Word(문서 기반 작성)에서 콘텐츠를 편집하고 Edge Delivery Services에 게시하는 방법을 보여 줍니다. 또한 범용 편집기를 사용하는 WYSIWYG 편집을 보여 줍니다.

![Edge Delivery 아키텍처](assets/AEM-with-EDS-publishing-simple2.png)

Edge Delivery Services는 GitHub를 활용하므로 GitHub 저장소에서 바로 코드를 관리 및 배포할 수 있습니다. 재구축 프로세스 없이 새로운 콘텐츠가 즉시 추가됩니다.

### 문서 기반 작성 {#document-based}

문서 기반 작성을 사용하면 Microsoft Word 또는 Google 문서에서 직접 콘텐츠를 사용하여 해당 소스가 웹 사이트의 페이지가 되도록 할 수 있습니다. 제목, 목록, 이미지, 글꼴 요소는 모두 초기 소스에서 웹 사이트로 전송할 수 있습니다.

* 문서 기반 작성을 통해 모든 마케터는 알려진 작성 도구(Microsoft Word, Google 문서 등)를 사용하여 신속하게 콘텐츠를 만들 수 있습니다.
* 소스 문서 내에서 바로 작성, 검토 및 게시할 수 있으므로 콘텐츠 생성이 간소화됩니다.
* 알려진 도구를 사용하므로 콘텐츠 작성자는 온보딩을 사용하지 않아도 되므로 콘텐츠 속도가 빨라집니다.
* 사이트의 기능은 GitHub의 CSS 및 JavaScript을 사용하여 개발할 수 있습니다.

![문서 기반 작성](assets/document-based-authoring.png)

문서 기반 작성 문서에서 자세히 읽어보십시오.

* Edge Delivery를 시작하는 방법에 대한 자세한 내용은 [빌드 섹션](https://www.aem.live/docs/#build)을 참조하십시오.
* Edge Delivery를 사용하여 콘텐츠를 작성 및 게시하는 방법을 이해하려면 [게시 섹션](https://www.aem.live/docs/authoring)을 참조하십시오.
* 웹 사이트 프로젝트를 올바르게 시작하는 방법을 이해하려면 [Launch 섹션](https://www.aem.live/docs/#launch)을 참조하십시오.

### WYSIWYG 작성 {#wysiwyg-authoring}

WYSIWYG(보이는 그대로) 작성은 사용자 정의 가능한 원스톱 공간인 유니버설 편집기를 활용하여 시각적 미리 보기를 통해 컨텍스트에 맞게 콘텐츠를 실시간으로 편집할 수 있습니다.

* WYSIWYG 작성을 사용하면 headless 또는 headful과 관계없이 작성자 효율성을 높일 수 있습니다.
* 워크플로우 및 거버넌스를 비롯한 AEM의 포괄적인 컨텐츠 관리 기능을 활용할 수 있습니다.
* 다양한 확장 포인트를 활용하여 고유한 프로세스 및 통합을 지원합니다.
* 사이트의 기능은 GitHub의 CSS 및 JavaScript을 사용하여 개발할 수 있습니다.

![WYSIWYG 작성](assets/wysiwyg-authoring.png)

자세한 내용은 WYSIWYG 작성 설명서를 참조하십시오.

* 범용 편집기 및 WYSIWYG 작성에 대한 개요는 [Edge Delivery Services을 위한 WYSIWYG 콘텐츠 작성](/help/edge/wysiwyg-authoring/authoring.md) 문서를 참조하십시오.
* 개발자 개요는 문서 [Edge Delivery Services을 사용한 WYSIWYG 작성에 대한 개발자 시작 안내서](/help/edge/wysiwyg-authoring/edge-dev-getting-started.md)를 참조하십시오.

### 작성 방법 결정 {#authoring-method}

AEM의 유연성은 작성 요구 사항을 충족하도록 해줍니다. Adobe을 통해 요구 사항에 가장 적합한 방법(또는 방법)을 결정할 수 있습니다.

* 항상 콘텐츠 작성자를 결정에 참여시킵니다.
* 여러 작성 방법을 구현할 수 있습니다.
* 언제든지 나중에 작성 방법을 변경할 수 있습니다.
* 구현 전에 결정해서는 안 되며, 구현의 일부로 결정해야 합니다.

자세한 내용은 [작성 방법 선택](authoring-methods.md) 문서를 참조하십시오.

## Edge Delivery Services 및 기타 Adobe Experience Cloud 제품 {#edge-other-products}

Edge Delivery Services는 Adobe Experience Manager의 일부이므로 Edge Delivery Services 및 AEM Sites는 동일한 도메인에서 함께 존재할 수 있으며, 이는 대규모 웹 사이트에서 일반적인 사용 사례입니다. 또한 Edge Delivery Services의 콘텐츠는 AEM Sites 페이지에서 간단히 사용할 수 있으며 그 반대의 경우도 마찬가지입니다.

AEM 및 Edge Delivery Services를 사용하여 자신의 프로젝트를 작성하는 방법을 알아보려면 [Edge Delivery Services를 사용한 WYSIWYG용 개발자 시작 안내서](/help/edge/wysiwyg-authoring/edge-dev-getting-started.md)를 참조하십시오.

[Adobe Target,](https://www.aem.live/developer/target-integration) [실제 사용 모니터링(RUM)](https://www.aem.live/developer/rum)과 함께 Edge Delivery Services를 사용하여 사이트의 사용량과 성능을 진단하고 [시작](https://experienceleague.adobe.com/en/docs/experience-platform/tags/home)할 수 있습니다.

## Edge Delivery Services 시작하기 {#getting-started}

[시작하기 - 개발자 튜토리얼](https://www.aem.live/developer/tutorial)에 따라 Edge Delivery Services 사용을 쉽게 시작할 수 있습니다.

## Adobe에서 도움 받기 {#getting-help}

Adobe에서는 Edge Delivery Services에 도움이 되는 세 가지 채널을 제공합니다.

* 일반적인 문의는 [커뮤니티 리소스](#community-resources)와 협력할 수 있습니다.
* 특정 질문은 [제품 협업 채널](#collaboration-channel)에 액세스할 수 있습니다.
* [지원 티켓을 기록](#support-ticket)하여 주요 및 중요한 문제를 해결할 수 있습니다.

### 커뮤니티 리소스에 액세스 {#community-resources}

Adobe는 사용자에게 Edge Delivery Services, WYSIWYG 작성 및 문서 기반 작성에 대한 최고의 커뮤니티 참여와 지원을 제공하기 위해 최선을 다하고 있습니다.

* [Experience League 커뮤니티](https://adobe.ly/3Q6kTKl)에 참여하여 질의하고, 피드백을 공유하고, 토론을 시작하고, Adobe 전문가와 AEM Advisor/Champs의 지원을 요청하고, 비슷한 생각을 가진 사람들과 실시간으로 소통할 수 있습니다.
* 보다 일반적인 플랫폼인 [디스코드 채널](https://discord.gg/aem-live)에 참여하여 실시간으로 상호 작용하고 아이디어를 빠르게 교환할 수 있습니다.

### 제품 협업 채널에 액세스하는 방법 {#collaboration-channel}

사용자와의 직접적인 소통 채널이 가지는 가치를 고려하여 모든 AEM 프로젝트는 시작부터 속도, 주요 업데이트와 체감 품질에 대한 확장 보고를 위해 Slack 채널을 설정합니다. Adobe로부터 조직과 관련된 Slack 채널에 가입하라는 초대를 받게 됩니다.

자세한 내용은 [Slack 봇 사용](https://www.aem.live/docs/slack) 문서를 참조하십시오.

프로비저닝된 제품 협업 채널을 통해 Adobe 제품 팀과 협력하여 제품 사용 또는 모범 사례에 대한 질문에 답변할 수 있습니다. 서비스 수준 목표(SLT)는 제품 협업 채널을 통해 대화와 연결되지 않습니다.

### 지원 티켓 기록 {#support-ticket}

제품 문제 해결에 추가 조사가 필요하고 응답 SLT를 충족해야 하는 경우 Admin Console을 사용하여 다음 프로세스에 따라 지원 티켓을 제출할 수 있습니다.

1. [표준 지원 프로세스에 따라](https://experienceleague.adobe.com/?support-tab=home#support) 티켓을 생성합니다.
1. 티켓 제목에서 **Edge Delivery**&#x200B;를 추가합니다.
1. 설명에서 문제 설명 외에 다음 세부 정보를 제공합니다.

   * 라이브 웹 사이트의 URL입니다. 예: `www.mydomain.com`.
   * 원본 웹 사이트의 URL(`.hlx` URL)입니다.

## 다음 단계 {#whats-next}

[Edge Delivery Services 사용](/help/edge/using.md) 검토로 시작하십시오.
