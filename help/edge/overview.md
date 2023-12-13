---
title: AEM 및 Edge Delivery Services
description: AEM이 Edge Delivery Services에서 제공하는 성능과 완벽한 등대 점수를 통해 어떻게 as a Cloud Service으로 혜택을 받을 수 있는지 이해합니다.
feature: Edge Delivery Services
exl-id: 03a1aa93-d2e6-4175-9cf3-c7ae25c0d24e
source-git-commit: 9d26a4835dc331f2ff8b741a4c14847ead611874
workflow-type: tm+mt
source-wordcount: '838'
ht-degree: 48%

---


# AEM 및 Edge Delivery Services {#aem-edge}

Edge Delivery Services를 사용하여 AEM은 참여 및 전환을 유도하는 탁월한 경험을 제공합니다. 이를 위해 AEM은 빠르게 작성 및 개발할 수 있는 영향력이 큰 경험을 제공합니다. 작성자가 콘텐츠를 빠르게 업데이트 및 게시하고 새 사이트를 신속하게 시작할 수 있는 신속한 개발 환경을 지원하는 구성 가능한 서비스 세트입니다. 그에 따라 Edge Delivery Services를 사용하여 전환을 개선하고, 비용을 절감하고, 최고의 콘텐츠 속도를 제공할 수 있습니다.

Edge Delivery Services을 사용하여 다음과 같은 작업을 수행할 수 있습니다.

* 완벽한 Lighthouse Score를 사용하여 빠른 사이트를 만들고 실제 사용자 모니터링(RUM)을 통해 사이트 실적을 지속적으로 모니터링합니다.
* 콘텐츠 소스를 분리하여 작성 효율성을 높입니다. 기본 제공되는 AEM 작성과 문서 기반 작성을 모두 사용할 수 있습니다. 따라서 동일한 웹 사이트에서 여러 콘텐츠 소스로 작업할 수 있습니다.
* 기본 제공 실험 프레임워크를 사용하여 성능에 영향을 주지 않고도 빠르게 테스트를 작성 및 실행하고 테스트 승자 프로덕션에 대한 빠른 릴리스를 제공할 수 있습니다.

## Edge Delivery Services 개요 {#edge-overview}

다음 다이어그램은 Microsoft Word에서 콘텐츠를 편집하고(문서 기반 편집) Edge Delivery Services에 게시하는 방법을 보여 줍니다. 또한 범용 편집기를 사용한 AEM 게시 방법을 보여 줍니다.

![Edge Delivery 아키텍처](assets/AEM-with-EDS-publishing-simple2.png)

Edge Delivery Services는 웹 사이트에서 콘텐츠를 작성하는 방법에 대해 높은 수준의 유연성을 제공하는 구성 가능한 서비스 세트입니다. 앞에서 설명한 대로 두 가지를 모두 사용할 수 있습니다 [AEM 콘텐츠 관리](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/sites/authoring/getting-started/concepts.html) 포함 [유니버설 편집기 작성](/help/implementing/universal-editor/introduction.md) 뿐만 아니라 [문서 기반 작성.](https://www.aem.live/docs/authoring)

예를 들어 Microsoft Word 또는 Google Docs에서 바로 콘텐츠를 사용할 수 있습니다. 즉, 해당 소스의 문서가 웹 사이트의 페이지가 될 수 있습니다. 또한 제목, 목록, 이미지, 글꼴 요소는 모두 초기 소스에서 웹 사이트로 전송할 수 있습니다. 새 콘텐츠는 리빌드 프로세스 없이 즉시 추가됩니다.

Edge Delivery Services은 GitHub를 사용하므로 고객이 GitHub 저장소에서 직접 코드를 관리하고 배포할 수 있습니다. 예를 들어 Google 문서 또는 Microsoft Word로 콘텐츠를 작성할 수 있으며 GitHub에서 CSS와 JavaScript를 사용하여 사이트의 기능을 개발할 수 있습니다. 준비가 되면 Sidekick 브라우저 확장 기능을 사용하여 콘텐츠 업데이트를 미리 보고 게시할 수 있습니다.

Edge Delivery Services 설명서 추가 참조:

* Edge Delivery를 시작하는 방법에 대한 자세한 내용은 [빌드 섹션.](https://www.aem.live/docs/#build)
* Edge Delivery를 사용하여 콘텐츠를 작성 및 게시하는 방법을 이해하려면 다음을 참조하십시오. [섹션을 게시합니다.](https://www.aem.live/docs/authoring)
* 웹 사이트 프로젝트를 제대로 시작하는 방법을 이해하려면 [섹션을 시작합니다.](https://www.aem.live/docs/#launch)

## Edge Delivery Services 및 기타 Adobe Experience Cloud 제품 {#edge-other-products}

Edge Delivery Services은 Adobe Experience Manager의 일부이므로 Edge Delivery Services과 AEM 사이트는 동일한 도메인에 공존할 수 있습니다. 이는 대규모 웹 사이트의 일반적인 사용 사례입니다. 그 외에도 Edge Delivery Services의 컨텐츠는 AEM Sites 페이지에서 그리고 그 반대로 쉽게 사용할 수 있습니다.

Adobe Target, Analytics, Launch와 함께 Edge Delivery Services를 사용할 수도 있습니다.

## Edge Delivery Services에 대한 액세스 {#getting-access}

Edge Delivery Services 사용을 쉽게 시작할 수 있습니다. 다음을 따라 시작하기 [시작하기 - 개발자 자습서.](https://www.aem.live/developer/tutorial)

## Adobe에서 도움 받기 {#adobe-gethelp}

프로비저닝된 제품 협업 채널(액세스 세부 정보는 아래 참조)을 통해 Adobe 제품 팀과 협력하여 제품 사용 또는 모범 사례에 대한 질문에 답변할 수 있습니다. 제품 공동 작업 채널을 통한 대화와 연결된 SLT(서비스 수준 목표)가 없습니다. 제품 문제에 추가 조사 및 문제 해결이 필요하고 응답 SLT를 충족해야 하는 경우 다음 사항에 따라 지원 티켓을 제출할 수 있습니다. [지원 프로세스입니다.](https://experienceleague.adobe.com/?support-tab=home#support)

Adobe에서는 Edge Delivery Services에 도움이 되는 세 가지 채널을 제공합니다.

* 일반적인 문의는 커뮤니티 리소스와 협력
* 특정 질문은 제품 협업 채널에 액세스
* 지원 티켓을 기록하여 주요 및 중요한 문제 해결

### 커뮤니티 리소스에 액세스 {#community-resource}

Adobe은 Edge Delivery Services 및 문서 기반 작성에 대한 최상의 커뮤니티 참여 및 지원을 제공할 수 있도록 지원하기 위해 최선을 다하고 있습니다.

* 참여 대상 [Experience League 커뮤니티](https://adobe.ly/3Q6kTKl) 질문을 하고, 피드백을 공유하고, 토론을 시작하고, Adobe 전문가 및 AEM Advisors/Champs의 도움을 구하고, 마음이 맞는 개인과 실시간으로 교류합니다.
* 가입 [디스코드 채널,](https://discord.gg/aem-live) 실시간 상호 작용 및 빠른 아이디어 교환을 위한 보다 캐주얼한 플랫폼.

### 제품 공동 작업 채널에 액세스하는 방법 {#collab-channel}

고객과의 직접 통신 채널의 가치를 고려하여 출시되는 모든 AEM 고객은 속도, 주요 업데이트 및 경험 품질에 대한 크기 조정된 보고를 위한 Slack 채널을 구축하게 됩니다. Adobe로부터 조직과 관련된 Slack 채널에 가입하라는 초대를 받게 됩니다.

자세한 내용은 [Slack 봇 사용](https://www.aem.live/docs/slack) 문서를 참조하십시오.

### 지원 티켓 기록 {#support-ticket}

Admin Console을 통해 지원 티켓을 기록하는 단계:

1. [표준 지원 프로세스에 따라](https://experienceleague.adobe.com/?support-tab=home#support) 티켓을 만듭니다.
1. 티켓 제목에서 **Edge Delivery**&#x200B;를 추가합니다.
1. 설명에서 다음 세부 정보를 입력해 주십시오.

   * 라이브 웹 사이트의 URL입니다. 예: `www.mydomain.com`.
   * 원본 웹 사이트의 URL(`.hlx` URL).

## 다음 단계 {#whats-next}

[Edge Delivery Services 사용](/help/edge/using.md)문서 검토로 시작하십시오.
