---
title: Adobe Experience Manager의 AI Assistant(비공개 베타)
description: Adobe Experience Manager의 AI Assistant를 사용하여 답을 찾고, 문제를 해결하고, 사이트, Assets, Dynamic Media, Cloud Manager 및 Forms을 탐색할 수 있습니다.
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
hide: false
hidefromtoc: true
exl-id: 6cdf7f65-7112-420a-90c1-564f0ef8ceaf
source-git-commit: 0afd74120380c9ae3d02db9fb684189c2f19648f
workflow-type: tm+mt
source-wordcount: '1394'
ht-degree: 0%

---

# Adobe Experience Manager의 AEM AI Assistant 정보 {#aem-home}

AEM(Adobe Experience Manager)의 AI Assistant는 Adobe Experience Manager 관련 쿼리에 대한 답변 찾기를 간소화하도록 설계된 대화형 인터페이스를 제공합니다. 제품 지식에 액세스하고, 문제를 해결하며, Experience League에서 사용할 수 있는 정보를 탐색하는 데 도움이 됩니다. 비공개 베타 프로그램 동안 AEM AI Assistant는 사이트, Assets, Dynamic Media, Cloud Manager 및 Forms 등 Adobe Experience Manager as a Cloud Service을 지원합니다.

>[!IMPORTANT]
>Adobe에서 AI Assistant 기능을 활성화하여 개인 베타 프로그램을 테스트하고 참여할 수 있도록 사용자 계약을 검토하고 제출했는지 확인합니다.
>
>질문이 있는 경우 Adobe ID과 연결된 메일 주소에서 [Grp-AEMAIASSISTANT@adobe.com](mailto:Grp-AEMAIASSISTANT@adobe.com)(으)로 메일을 보내십시오.

## 개인 정보, 보안 및 거버넌스

AEM AI Assistant는 개인 정보 보호, 보안 및 거버넌스에 중점을 두고 설계되었습니다.

이 문서에서는 AEM AI Assistant에서 기대할 수 있는 신뢰 중심 기능에 대해 간략히 설명합니다.

* 교육 목적을 포함하여 AEM AI Assistant에서는 개인 데이터를 사용하지 않습니다.
* AEM AI Assistant는 소비자 데이터에 액세스할 수 없습니다.
* AEM AI Assistant와 상호 작용하려면 명시적인 권한이 필요합니다.
* 사용자가 제공한 프롬프트(질문, 쿼리 등)는 다른 고객과 공유되지 않습니다.

<!-- See also [Security at Adobe whitepaper](). NEED ACTIVE LINK FROM ADRIAN NICOLAE TANASE. CURRENTLY 404. -->


## 제품 지식에 대한 AEM AI Assistant 알아보기 {#ai-prod-insights}

제품 지식은 Adobe Experience League 설명서에서 파생된 개념과 주제를 포함합니다. 이러한 질문은 다음과 같은 하위 그룹으로 분류될 수 있습니다.

| 제품 지식 | 예 |
| --- | --- |
| 뾰족한 학습 | <ul><li>유니버설 편집기란?</li><li>Cloud Manager에서 프로그램을 만들려면 어떻게 해야 합니까?</li></ul> |
| 검색 열기 | <ul><li>범용 편집기는 어떻게 사용합니까?</li><li>한 환경에서 다른 환경으로 콘텐츠를 복사하는 방법이 있습니까?</li></ul> |
| 문제 해결 | <ul><li>유니버설 편집기에 액세스할 수 없는 이유는 무엇입니까?</li><li>내 파이프라인이 실패한 이유는 무엇입니까?</li></ul> |

AEM AI Assistant의 현재 범위는 Adobe Experience Manager as a Cloud Service에 대한 제품 지식 질문 해결에 중점을 둡니다. 이 범위에는 Sites, Assets, Forms 및 Cloud Manager과 같은 주요 영역에 대한 포괄적인 지원이 포함됩니다.

## 효과적인 질문을 작성하는 방법 {#ai-craft-questions}

AEM AI Assistant로부터 가장 정확한 응답을 받으려면 명확성과 문맥을 사용하여 질문을 작성하는 것이 중요합니다. 다음 팁을 사용하여 쿼리가 명확하고 잘 구성되어 있는지 확인하십시오.

* 과제나 질문을 간결하게 명확히 진술하라.
* 애매한 문구나 지나치게 복잡한 구문을 방지하여 이해도를 높입니다.
* 이 접근 방식은 AEM AI Assistant가 보다 정확하고 적절한 답변을 제공하는 데 도움이 되므로 작업 또는 질문에 대한 관련 컨텍스트를 포함합니다.
예를 들어, 프롬프트에서 작업 중인 AEM 솔루션 이름(Sites, Assets, Dynamic Media, Cloud Manager 및 Forms)을 지정하는 데 도움이 됩니다.

### 지원되지 않는 질문의 예 {#ai-unsupported-questions}

| 영역 | 예 |
| --- | --- |
| Operational insights | <ul><li>내 테넌트에 개발 환경이 몇 개 있습니까?</li><li>마지막 프로덕션 파이프라인은 누가 시작했습니까?</li></ul> |
| 문제 해결 | <ul><li>프로덕션 파이프라인이 실패한 이유는 무엇입니까?</li></ul> |
| 작업 및 자동화 | <ul><li>나를 위해 개발 분기에서 코드 품질 파이프라인을 구성합니다.</li></ul> |


## AEM AI Assistant 사용 {#ai-use}

### Admin Console을 통해 AEM AI Assistant 액세스 활성화

AEM AI Assistant를 사용하려면 조직에서 Admin Console 수준에서 옵트인해야 합니다. 제품 관리자는 사용자 그룹을 생성(또는 선택)하고 새로운 &quot;AI Assistant&quot; 권한을 부여합니다. 해당 그룹에 추가된 모든 사용자는 즉시 AEM 전체의 도우미에 액세스할 수 있습니다. 회사 전체의 가용성이 목표라면, 관리자는 모든 사용자를 해당 그룹에 할당하기만 하면 됩니다.

![Admin Console의 AEM AI Assistant](/help/implementing/cloud-manager/assets/ai-assistant-admin-console.png)

직원의 관점에서 프로세스는 간단합니다. 조직의 Adobe Experience Manager에 대한 제품 관리자를 식별하고 AI 지원 사용자 그룹에 추가하도록 요청합니다. 해당 그룹에 나타나면 다음에 로그인할 때 Assistant 아이콘이 자동으로 표시됩니다.

관리자는 일반적인 Cloud Manager 거버넌스를 염두에 두어야 합니다. 프로필을 만들거나, 사용자 그룹을 관리하거나, 권한을 편집하려면 Admin Console에서 제품 관리자 권한을 보유해야 합니다. 사용자가 도우미의 기본 제공 **지원 티켓 만들기** 기능도 필요한 경우 동일한 개인 또는 그룹에 표준 **지원 관리자** 역할(표준 Admin Console 역할)을 추가하십시오.

![Admin Console의 AEM AI Assistant에서 기술 지원 티켓 만들기](/help/implementing/cloud-manager/assets/ai-assistant-admin-console-support-ticket.png)

AEM as a Cloud Service에서 사용자 및 그룹 설정에 대한 안내 설명은 [AEM as a Cloud Service에 대한 액세스 구성](https://experienceleague.adobe.com/en/docs/experience-manager-learn/cloud-service/accessing/overview)을 참조하십시오.

[사용자 지정 권한](/help/implementing/cloud-manager/custom-permissions.md)도 참조하세요.


### 대화 시작 또는 재설정

주제를 변경하려는 경우 AEM AI Assistant를 재설정하고 새 대화를 시작할 수 있습니다. 이 기능은 특히 실패한 쿼리의 문제를 해결하거나 잘못된 정보를 제공할 때 유용합니다.

![대화 시작 단추](/help/implementing/cloud-manager/assets/ai-assistant-start-conversation.png)

**대화를 시작하거나 다시 설정하려면:**

1. AEM AI Assistant에서 ![자세히 아이콘](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg)을 클릭합니다.
1. AEM AI Assistant에 새로운 주제 또는 주제 변경 사항을 알려면 **새 대화 시작**&#x200B;을 클릭하세요.

### 검색 기능 사용

AEM AI Assistant에는 지원되는 주제 및 범주를 탐색하는 데 도움이 되는 검색 기능이 포함되어 있습니다.

![아이디어 전구 아이콘](/help/implementing/cloud-manager/assets/ai-assistant-idea.png)

**검색 기능을 사용하려면:**

1. AEM AI Assistant의 오른쪽 상단 모서리 근처에서 ![학습 아이콘](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Learn_18_N.svg)을 클릭합니다.
1. 관련 프롬프트 목록을 보려면 카테고리를 선택하십시오.
1. AEM AI Assistant가 답할 수 있는 질문 유형을 더 잘 이해하려면 프롬프트를 선택하십시오.

### AEM AI Assistant에 대한 피드백 제공

입력을 통해 AEM AI Assistant를 개선하여 성능과 정확성을 높일 수 있습니다.

다음 옵션을 통해 AEM AI Assistant와 사용자 경험에 대한 피드백 공유:

![엄지손가락 위로, 엄지손가락 아래로 및 플래그 아이콘](/help/implementing/cloud-manager/assets/ai-assistant-feedback.png)

| 아이콘 | 설명 |
| --- | --- |
| ![Thumbs 위쪽 아웃라인 아이콘](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ThumbUpOutline_18_N.svg) | 무엇이 잘 진행되었는지 나타내고 긍정적인 피드백을 공유하려면 클릭하십시오. |
| ![Thumbs down outine 아이콘](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ThumbDownOutline_18_N.svg) | 개선을 위한 제안을 제공하려면 클릭하십시오. 매일 검토되는 경험에 대한 특정 주석을 추가합니다. |
| ![플래그 아이콘](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Flag_18_N.svg) | 을(를) 클릭하여 우려를 보고하거나 AEM AI Assistant와의 상호 작용에 대한 자세한 피드백을 제공합니다. |

## AEM AI Assistant에 대한 FAQ {#ai-faq}

다음은 AI Assistant에 대한 몇 가지 일반적인 질문에 대한 답변입니다.

* **AEM AI Assistant에서 실시간으로 제공하는 정보입니까?**\
  아니요. AI Assistant는 Adobe Experience League 설명서에서 해당 콘텐츠를 소스화합니다. 콘텐츠에 대한 업데이트가 응답에 반영되는 데 시간이 걸릴 수 있습니다.
* **AEM AI Assistant는 어떤 Adobe 애플리케이션을 지원합니까?**\
  현재 AI 비서는 사이트, Assets, 다이내믹 미디어, Cloud Manager, Forms 등 AEM as a Cloud Service에서 제품 지식 조회를 지원한다.
* **AEM AI Assistant의 기능은 무엇입니까?**\
  AEM AI Assistant는 Adobe 제품 지식과 관련된 질문에 답변할 수 있도록 설계되었습니다.
* **AEM AI 도우미가 교육 데이터에 개인 정보를 사용합니까?**\
  아니요. AEM AI Assistant는 교육 목적으로 개인 정보를 사용하지 않습니다. 이름이나 연락처 세부 정보를 포함하여 자신이나 다른 사람에 대한 개인 정보를 AEM AI Assistant와 공유하지 마십시오.


## AEM Forms AI Assistant(Forms Experience Builder) {#ai-forms-builder}

제품 지식을 위한 일반적인 AEM AI Assistant 외에 AEM은 특수화된 **[AEM Forms AI Assistant(Forms Experience Builder)](/help/edge/docs/forms/forms-ai-assistant.md)**&#x200B;를 제공합니다. 이 향상된 도우미는 자연어 프롬프트를 통해 양식을 만들고 구성하고 양식에 대한 질문에 답변하는 데 도움이 될 수 있습니다.

### 주요 기능

AEM Forms AI Assistant는 다음을 제공합니다.

* **양식 만들기**: 자연어 설명을 사용하여 처음부터 새 양식을 만듭니다.
* **디자인 가져오기**: 기존 디자인(PDF, Figma, 이미지)을 제대로 작동하는 AEM Forms으로 변환합니다.
* **양식 구성**: 필드, 패널, 유효성 검사 규칙 및 조건부 논리를 추가합니다.
* **레이아웃 관리**: 양식 구조를 구성하고 다른 장치에 맞게 최적화합니다.
* **통합 설정**: 양식 제출 및 데이터 처리를 구성합니다.
* **제품 정보**: AEM Forms 기능 및 모범 사례에 대한 질문에 답변합니다.

### 액세스 위치

AEM Forms AI Assistant는 다음과 같이 사용할 수 있습니다.

* **범용 편집기**: 시각적 편집 기능이 있는 Edge Delivery Services 양식용.
* **적응형 Forms 편집기**: 자세한 양식 구성 및 고급 기능에 사용됩니다.
* **Forms 관리 UI**: 높은 수준의 양식 만들기 및 관리 작업용.

### 시작하기

>[!NOTE]
>
> AEM Forms AI Assistant(Forms Experience Builder)는 개인 베타 프로그램에서 사용할 수 있습니다. 액세스 권한을 요청하려면 회사 주소에서 [aem-forms-ea@adobe.com](mailto:aem-forms-ea@adobe.com)(으)로 전자 메일을 보내십시오.

AEM Forms AI Assistant 사용에 대한 자세한 내용은 [AEM Forms AI Assistant](/help/edge/docs/forms/forms-ai-assistant.md) 설명서를 참조하십시오.

### 예시 사용 사례

* **&quot;이름, 전자 메일, 등급 및 댓글 필드가 있는 고객 피드백 양식 만들기&quot;**
* **&quot;업로드된 이 PDF 응용 프로그램 양식을 디지털 적응형 양식으로 변환&quot;**
* **&quot;결혼 상태가 &#39;기혼&#39;인 경우에만 배우자 정보를 표시하는 조건부 논리를 추가하십시오.&quot;**
* **&quot;고객 관계 관리 시스템에 데이터를 제출하도록 이 양식을 구성하십시오.&quot;**

이 전문 AEM Forms AI Assistant는 AI의 힘과 AEM의 강력한 양식 기능을 결합하여 양식 작성 워크플로를 간소화하여 양식 작성의 다음 진화를 나타냅니다.
