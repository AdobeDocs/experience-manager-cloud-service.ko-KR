---
title: Headless CMS로서의 AEM 컨텐츠 모델링 - 소개
description: Adobe Experience Manager as a Cloud Service의 기능을 헤드리스 CMS로 사용하여 프로젝트에 대한 컨텐츠를 모델링하는 방법을 소개합니다.
exl-id: 62061d73-6fdb-440b-a7dd-b0d530d49186
source-git-commit: 00ec09f327bc2f382d263970e690ed067aaa1355
workflow-type: tm+mt
source-wordcount: '721'
ht-degree: 1%

---

# Headless CMS로서의 AEM 컨텐츠 모델링 - 소개 {#architect-headless-introduction}

의 이 부분에서 [AEM Headless Content Architect 여정](overview.md)에서는 Adobe Experience Manager(AEM) as a Cloud Service as a Headless CMS를 사용할 때 컨텐츠 모델링을 이해하는 데 필요한 (기본) 개념과 용어를 배울 수 있습니다.

이 문서는 헤드리스 컨텐츠 전달, AEM에서 헤드리스를 지원하는 방법 및 헤드리스를 위해 컨텐츠를 모델링하는 방법을 이해하는 데 도움이 됩니다. 문서를 읽고 나면

* 헤드리스 컨텐츠 전달의 기본 개념을 이해합니다.
* AEM에서 헤드리스 및 컨텐츠 모델링을 지원하는 방법을 숙지하십시오.

## 목표 {#objective}

* **Audience**: 초보
* **목표**: 헤드리스 컨텐츠 모델링과 관련된 개념과 용어를 도입합니다.

## 전체 스택 컨텐츠 전달 {#full-stack}

사용이 간편하고 규모가 큰 CMS(콘텐츠 관리 시스템)가 급증한 이후 조직은 이를 메시징, 브랜딩 및 커뮤니케이션을 관리하는 중앙 위치로 활용했습니다. CMS를 경험 관리를 위한 중심점으로 사용하면 서로 다른 시스템에서 작업을 복제할 필요가 없으므로 효율성이 향상됩니다.

![기존의 전체 스택 CMS](/help/journey-headless/developer/assets/full-stack.png)

전체 스택 CMS에서 컨텐츠를 조작하는 모든 기능은 CMS에 있습니다. 시스템의 기능은 CMS 스택의 다양한 구성 요소를 구성합니다. 전체 스택 솔루션에는 많은 이점이 있습니다.

* 유지 관리 시스템이 하나 있습니다.
* 컨텐츠는 중앙에서 관리됩니다.
* 시스템의 모든 서비스가 통합됩니다.
* 컨텐츠 작성이 원활하게 수행됩니다.

따라서 새 채널을 추가하거나 새로운 유형의 경험을 지원해야 하는 경우 스택에 하나 이상의 새 구성 요소를 삽입할 수 있으며 변경할 공간이 한 개만 있습니다.

![스택에 새 채널 추가](/help/journey-headless/developer/assets/adding-channel.png)

그러나 변경 사항에 맞게 스택의 다른 항목을 조정해야 하므로 스택 내의 종속성 복잡성이 빠르게 드러납니다.

## 헤드리스의 머리 {#the-head}

시스템의 헤드는 일반적으로 해당 시스템의 출력 렌더러이며, 일반적으로 GUI 또는 기타 그래픽 출력 형태입니다.

헤드리스 CMS에 대해 이야기할 때, CMS는 컨텐츠를 관리하고 소비자에게 계속 제공합니다. 그러나, **콘텐츠** 표준화된 방식으로, 헤드리스 CMS는 최종 출력 렌더링을 생략하고 **프레젠테이션** 컨텐츠를 소비되는 서비스에 전달합니다.

![Headless CMS](/help/journey-headless/developer/assets/headless-cms.png)

경험 AR 경험, 웹 스토어, 모바일 경험, 점진적 웹 앱(PWA) 등 소비되는 서비스는 헤드리스 CMS의 콘텐츠를 가져와서 자체 렌더링을 제공합니다. 그들은 여러분의 컨텐츠에 대해 그들 자신의 의견을 제공하는 것을 돌봅니다.

헤드를 생략하면 복잡도를 제거하여 CMS를 단순화할 수 있습니다. 이렇게 하면 컨텐츠가 실제로 필요하고 이러한 렌더링에 더 잘 맞는 서비스로 컨텐츠를 렌더링하는 작업도 이동합니다.

## 컨텐츠 모델링 {#content-modeling}

컨텐츠 모델링(데이터 모델링이라고도 함)이 특기므로 헤드리스를 위해 모델링할 때 고려해야 할 사항은 무엇입니까?

헤드리스 애플리케이션에서 사용자 컨텐츠에 액세스하고 이를 사용하여 작업을 수행하려면 컨텐츠가 사전 정의된 구조를 가져야 합니다. 여러분의 컨텐츠가 자유형처럼 될 수 있지만, 그것은 생명을 만들 것입니다 *매우* 응용 프로그램에 대해 복잡합니다.

AEM의 경우, 컨텐츠 설계자는 컨텐츠 모델링을 수행하여 다양한 **컨텐츠 조각 모델**. 이러한 항목은 컨텐츠 작성자가 **컨텐츠 조각** 컨텐츠가 들어 있습니다.

### 컨텐츠 액세스 {#access-content}

이것은 좀 더 개발 세부 사항이지만, 단지 그 이야기를 완성하는 것이 여러분에게 흥미를 끌 수도 있습니다.

컨텐츠 조각 모델을 만들고 작성자가 이 모델을 사용하여 컨텐츠를 생성했으면 헤드리스 애플리케이션이 이 컨텐츠에 액세스해야 합니다.

AEM(Adobe Experience Manager) as a Cloud Service에서는 AEM GraphQL API를 사용하여 컨텐츠 조각에 선택적으로 액세스하여 필요한 컨텐츠만 반환할 수 있습니다. 개발자가 API를 사용하여 특정 콘텐츠를 선택하는 쿼리를 만들 수 있습니다.이 선택 프로세스는 *your* 컨텐츠 조각 모델 .

즉, 프로젝트에서 애플리케이션에 사용할 구조화된 컨텐츠의 헤드리스 전달을 실현할 수 있습니다.

## 다음 단계 {#whats-next}

개념과 용어를 학습했으므로 다음 단계는 다음과 같습니다 [컨텐츠 조각 모델을 사용하여 모델링을 위한 기본 사항을 알아봅니다](basics.md).

## 추가 리소스 {#additional-resources}

* AEM Headless Developer 여정
   * [CMS 헤드리스 개발에 대해 알아보기](/help/journey-headless/developer/learn-about.md)
   * [컨텐츠 모델 지정 방법 알아보기](/help/journey-headless/developer/model-your-content.md)
