---
title: Edge Delivery Services 개요
description: AEM as a Cloud Service가 Edge Delivery Services에서 제공하는 성능과 완벽한 Lighthouse Score를 통해 얻을 수 있는 이점을 알아봅니다.
feature: Edge Delivery Services
exl-id: 03a1aa93-d2e6-4175-9cf3-c7ae25c0d24e
role: Admin, Developer
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '988'
ht-degree: 100%

---


# Edge Delivery Services 개요 {#edge-delivery-services}

>[!TIP]
>
>**지금 바로 실습해 보시겠습니까?**
>
>Edge Delivery Services을 바로 사용해 보려면 두 가지 옵션이 있습니다.
>
>* [사전 설치된 튜토리얼 환경을 완전히 구성하고 바로 사용할 수 있도록 바로 작성을 시작하십시오.](https://www.aem.live/developer/ue-trial)
>* 자세한 내용을 자세히 알아보고 30분 이내에 [aem.live에서 튜토리얼을 확인](https://www.aem.live/developer/ue-tutorial)하여 자신만의 환경을 설정하십시오.

## Edge Delivery Services란 무엇입니까? {#what-is-edge}

Edge Delivery Services란 웹 사이트의 빌드 및 게재 방식을 혁신하여 속도, 단순성, 확장성을 최적화하는 현대적 콘텐츠 게재 프레임워크입니다. 이는 Adobe Experience Manager의 핵심적인 부분으로, 네트워크 에지에서 더 사용자에게 가까운 곳에서 렌더링과 게재를 수행하여 더 빠른 디지털 경험을 제공합니다.

이는 콘텐츠 전송 네트워크(CDN)를 대체하지 않지만 자체 CDN 또는 [Adobe에서 관리하는 CDN](/help/implementing/dispatcher/cdn.md)과 완벽하게 통합됩니다.

## Edge Delivery Services를 사용하는 이유 {#why-edge}

### 검색 가능성 및 트래픽 증가 {#increase-traffic}

Edge Delivery 웹 사이트는 LLM을 위해 검색 엔진 최적화(SEO) 및 생성 엔진 최적화(GEO)되어 있습니다. 이를 통해 모든 기존 및 향후의 유기적 트래픽 소스에서 높은 가시성과 검색 가능성이 보장됩니다. **성능을 최우선으로 하는 엔드투엔드 아키텍처**&#x200B;는 고객 참여도에 긍정적인 영향을 미치는 즐거운 고객 경험을 보장합니다.

### 개발자 효율성 {#developer-efficientcy}

몇 달, 몇 년이 아닌, 며칠, 몇 주 만에 출시할 수 있습니다! Edge Delivery는 **현대 웹 개발자**&#x200B;가 선호하는 모든 도구를 제공합니다. GitHub, 자동 다시 로드를 통한 로컬 개발, 성능, 단순성을 모두 갖추었으며, 변환, 번들러, 구성, 오버헤드 등 복잡한 작업이 전혀 없습니다.

Edge Delivery는 단순성이 높아 복잡한 프레임워크, 툴링 또는 프로세스를 사용할 필요가 없으며 AI 코드 생성에 이상적입니다. 일반 HTML, 최신 CSS, 순수 JavaScript를 사용해 그 어느 때보다 빠르게 뛰어난 경험을 만들어 보십시오. 업무에 집중하고 새로운 도구를 배우고 훈련하는 데 소요되는 시간을 줄이십시오.

Edge Delivery를 사용하면 모든 개발자가 Lighthouse 점수 100점을 달성할 수 있습니다.

### 다양한 콘텐츠 소스에 대한 지원 {#multiple-content-sources}

**기존 AEM 인스턴스를 모두 포함**&#x200B;한 다양한 솔루션의 콘텐츠를 Edge Delivery와 바로 통합할 수 있습니다. 작성자는 친숙한 도구를 통해 더 빠르게 **SharePoint 등 모든 시스템에서 Edge Delivery로 콘텐츠를 관리하고 게시**&#x200B;할 수 있습니다.

### 구성 가능한 아키텍처 {#composable-architeture}

Headless와 Headful 모두에서 적절한 형식으로 적절한 콘텐츠를 제공하고 적절한 장식을 추가하여 모든 채널에서 돋보이는 경험을 제공할 수 있습니다.

## 작동 방법 {#how-does-it-work}

Edge Delivery Services는 웹 사이트에서 콘텐츠를 작성하는 방법을 보다 유연하게 제공하는 구성 가능한 서비스 세트입니다. AEM Publisher / Dispatcher 및 AEM Core Components를 통한 기존 경험 빌드 방식을 멀티 클라우드 SaaS 솔루션과 순수 프런트엔드 개발 방식으로 대체합니다.

![Edge Delivery 아키텍처](assets/aem-with-eds-architecture.png)

Edge Delivery Services는 GitHub를 활용하므로 GitHub 저장소에서 바로 코드를 관리 및 배포할 수 있습니다. 새 콘텐츠는 리빌드 프로세스 없이 즉시 추가됩니다.

## 작성 {#authoring}

### 컨텍스트에서 편집 {#in-context-editing}

[범용 편집기](/help/implementing/universal-editor/introduction.md)는 시각적 미리보기와 함께 콘텐츠를 실시간으로 맥락에 맞게 편집할 수 있는 WYSIWYG(What-you-see-is-what-you-get) 방식의 사용자 정의 가능한 원스톱 플랫폼입니다.

* 범용 편집기가 포함된 AEM 작성을 사용하면 Headless와 Headful 모두에서 작성자의 효율성이 높아집니다.
* 워크플로 및 거버넌스 등, AEM의 포괄적인 콘텐츠 관리 기능을 활용할 수도 있습니다.
* 다양한 확장 지점을 활용하여 자체적인 프로세스와 통합을 지원할 수 있습니다.
* GitHub에서 CSS와 JavaScript를 사용하여 사이트 기능을 개발할 수 있습니다.

![범용 편집기가 포함된 AEM 작성](assets/wysiwyg-authoring.png)

### 문서 기반 편집 {#document-based-editing}

또 다른 접근 방법은 콘텐츠가 문서로 관리되는 [문서 기반 작성](https://www.aem.live/docs/authoring) 입니다. 많은 기업에서 처음 콘텐츠를 만들 때 SharePoint를 사용하므로 Microsoft Word가 인기 있는 선택이 되고 있습니다. 새로운 도구를 배울 필요가 없으며 SharePoint 및 Word에서 바로 콘텐츠를 게시하면 AEM에 콘텐츠를 복사하여 붙여넣는 번거로움이 사라집니다. SharePoint가 없는 고객의 경우 Google 드라이브를 대신 사용할 수도 있습니다.

## 운영 원격 측정 {#telemetry}

Adobe Experience Manager는 [운영 원격 측정](https://www.aem.live/docs/operational-telemetry)을 사용해 Adobe Experience Manager 기반 사이트의 기능 및 성능 문제의 발견 및 해결에 필요한 운영 데이터를 수집합니다. 운영 원격 측정 데이터는 성능 문제 진단 및 실험 효과 측정에 사용할 수 있습니다. 운영 원격 측정은 [샘플링](https://www.aem.live/docs/operational-telemetry#operational-telemetry-data-is-sampled)&#x200B;(모든 페이지 조회의 일부만 모니터링)과 [개인 식별 정보(PII)의 신중한 제외](https://www.aem.live/docs/operational-telemetry#what-data-is-being-collected)를 통해 방문자의 개인 정보를 보호합니다.

## 탐색 시작하기 {#start-exploring}

범용 편집기가 포함된 AEM 작성을 사용해 Edge Delivery Services 시작하기:

* Edge Delivery Services 설명서 [Edge Delivery Services](https://www.aem.live)
* 범용 편집기가 포함된 AEM 작성에 대한 개요는 aem.live 설명서에 나와 있는 [Edge Delivery Services를 위한 AEM 작성 ](https://www.aem.live/docs/aem-authoring)문서를 참조하십시오.
* 개발자 개요는 aem.live 설명서에 나와 있는 [시작하기 - 범용 편집기 개발자 튜토리얼](https://www.aem.live/developer/ue-tutorial) 문서를 참조하십시오.

## Edge Delivery Services 및 기타 Adobe Experience Cloud 제품 {#edge-other-products}

Edge Delivery Services는 Adobe Experience Manager의 일부입니다. 따라서 Edge Delivery Services와 AEM Sites는 동일 도메인에서 함께 존재할 수 있으며, 이는 대규모 웹 사이트의 일반적인 사용 사례입니다. 또한 AEM Sites 페이지에서 Edge Delivery Services의 콘텐츠를 원활하게 사용할 수 있으며 그 반대의 경우도 마찬가지입니다.

[Adobe Target](https://www.aem.live/developer/target-integration), [Launch](https://experienceleague.adobe.com/ko/docs/experience-platform/tags/home)와 함께 Edge Delivery Services를 사용할 수도 있습니다.

## Adobe에서 도움 받기 {#getting-help}

Adobe에서는 Edge Delivery Services에 도움이 되는 다음과 같은 세 가지 레이어를 제공합니다.

* 일반적인 문의는 [커뮤니티 리소스](#community-resources)와 협력할 수 있습니다.
* 특정 질문은 [제품 협업 채널](#collaboration-channel)에 액세스할 수 있습니다.
* [지원 티켓 기록](#support-ticket)을 통해 **계약 지원 SLA 내**&#x200B;의 주요하고 중요한 문제를 해결할 수 있습니다.

### 커뮤니티 리소스에 액세스 {#community-resources}

Adobe는 사용자에게 Edge Delivery Services, 범용 편집기가 포함된 AEM 작성 및 문서 기반 작성에 대한 최고의 커뮤니티 참여와 지원을 제공하기 위해 최선을 다하고 있습니다.

* [Experience League 커뮤니티](https://adobe.ly/3Q6kTKl)에 참여하여 질의하고, 피드백을 공유하고, 토론을 시작하고, Adobe 전문가와 AEM Advisor/Champs의 지원을 요청하고, 비슷한 생각을 가진 사람들과 실시간으로 소통할 수 있습니다.
* 보다 일반적인 플랫폼인 [디스코드 채널](https://discord.gg/aem-live)에 참여하여 실시간으로 상호 작용하고 아이디어를 빠르게 교환할 수 있습니다.

### 지원 티켓 기록 {#support-ticket}

{{support-ticket}}
