---
title: 거버넌스 에이전트 개요
description: AEM Governance Agent가 AEM 전반에서 브랜드 무결성 및 규정 준수를 보호하는 방법을 알아봅니다
feature: Edge Delivery Services, Agentic AI
role: User, Admin, Architect, Developer
source-git-commit: 9b26cd1f30ad6fa23e28c9f36fe48091e069962e
workflow-type: tm+mt
source-wordcount: '548'
ht-degree: 0%

---


# 거버넌스 에이전트 개요 {#governance-agent}

**거버넌스 에이전트**&#x200B;는 Adobe Experience Manager 전체의 브랜드 무결성과 규정 준수를 보호하기 위해 고안된 솔루션입니다. 모든 상호 작용과 활성화가 설정된 표준을 준수하도록 보안, 규제 및 브랜드 정책을 시행합니다. 거버넌스 에이전트는 AI Assistant에 완전히 통합되어 있으며 **A2A(에이전트 대 에이전트)** 및 **MCP(모델 제어 프로토콜)** 도구를 활용하여 엔터프라이즈 환경 내에서 원활하게 작동하도록 설계되었습니다. 이러한 통합을 통해 에이전트는 ChatGPT, Claude 및 기타 외부 AI 시스템과 같은 고급 AI 오케스트레이터와 연결하여 플랫폼 전반에서 유연하고 확장 가능한 인텔리전스를 보장합니다.

주요 기능은 다음과 같습니다.

* **브랜드 거버넌스:** 콘텐츠와 에셋 전반에 걸쳐 브랜드 확인을 자동화하여 브랜드 일관성을 유지하고 수동 검토를 줄입니다.
* **권한 및 Digital Rights Management(DRM):** 디지털 에셋 전반에 걸친 권한 및 사용 권한을 제어하여 안전하고 호환되는 공동 작업을 보장합니다.

이러한 기능을 결합함으로써 거버넌스 에이전트는 위험을 줄이고 대규모로 빠르고 안전하며 브랜드 내 전달을 가능하게 합니다.

>[!IMPORTANT]
>
>AI가 생성한 응답은 정확하지 않거나 오해의 소지가 있을 수 있습니다. 제안된 수정 사항과 응답을 다시 확인하십시오.
>
>[Adobe Experience Cloud Generative AI 사용 지침](https://www.adobe.com/kr/legal/licenses-terms/adobe-dx-gen-ai-user-guidelines.html)도 참조하세요.

## AEM 거버넌스 에이전트의 스킬 {#skills-in-aem-governance-agent}

### 브랜드 거버넌스 {#brand-governance}

거버넌스 에이전트는 브랜드 지침에 따라 콘텐츠를 확인하여 모든 디지털 경험에서 일관성을 확보할 수 있습니다. 톤, 클레임, 로고 사용, 타이포그래피 및 이미지와 같은 미리 수집된 브랜드 규칙을 사용합니다. Experience Hub의 채팅, 편집자 및 배치 모드 내에서 실시간으로 작동하므로 AI 생성 콘텐츠, 사이트 마이그레이션, 간략한 기반 사이트 생성에 이상적입니다.

![브랜드 거버넌스 개요](/help/ai-in-aem/agents/governance/assets/brand-governance.png)

**프롬프트 예:**

* *이 페이지가 내 브랜드와 일치합니까?`https://www.website/en.html`*
* *이 `https://www.website/en.html`은(는) 브랜드 메시지 지침을 따르나요?*
* *`https://www.website/homepage`이(가) 브랜드 지침을 따르는지 확인*
* *내 브랜드 지침 표시*

### 권한 및 Digital Rights Management {#permission-and-digital-rights-management}

#### Content Hub의 권한 관리 {#permission-management-in-content-hub}

Content Hub에서 거버넌스 에이전트는 적절한 사람만 적절한 시간에 적절한 자산에 액세스할 수 있도록 합니다. 세분화된 속성 기반 제어 및 사용 권한을 적용하여 중요한 콘텐츠를 보호하는 동시에 안전한 공동 작업을 가능하게 합니다. 즉, 규정 준수 위험 감소, 브랜드 무결성 강화, 워크플로 속도를 높여 무단 액세스나 오용에 대한 걱정 없이 자신 있게 에셋을 공유하고 재사용할 수 있습니다. 보안과 유연성의 균형은 조직 전체의 운영 효율성과 신뢰도를 높입니다.

![권한 관리 개요](/help/ai-in-aem/agents/governance/assets/permission-management.png)

**프롬프트 예:**

* *기존 Content Hub ABAC 규칙을 모두 표시합니다.*
* *모든 자산에 대한 액세스 권한을 &quot;마케팅&quot; 그룹에 제공하는 규칙을 만듭니다.*
* *Marketing:segment이(가) EMEA인 자산에 대한 액세스 권한을 영업 그룹에 부여합니다.*
* *외부 에이전시에 액세스할 수 있는 모든 규칙을 삭제합니다.*
* *Content Hub의 ABAC란 무엇이며 무엇을 도와주실 수 있습니까?*

#### Assets Digital Rights Management {#assets-digital-rights-management}

에이전트를 사용하면 콘텐츠 에코시스템 전반에서 Assets 디지털 권한을 관리할 수 있습니다. 세분화된 수준에서 권한 및 사용 권한을 제어하여 정의된 준수 경계 내에서만 자산에 액세스하고 사용하도록 합니다. 이를 통해 안심하고 지적 재산을 보호하고 규제 위험을 줄이며 브랜드 무결성을 유지할 수 있습니다. 권한 이행을 자동화함으로써 팀은 안전하고 자신 있게 공동 작업을 수행할 수 있으며, 보안 또는 규정 준수를 저해하지 않으면서 컨텐츠 배포를 가속화할 수 있습니다.

![DRM 관리 개요](/help/ai-in-aem/agents/governance/assets/drm-management.png)

**프롬프트 예:**

* *내 자산이 곧 만료됩니까?*
* *지난 달에 만료된 모든 자전거 자산을 찾습니다.*
* *어떤 자산이 최근에 만료되었습니까?*
* *만료 날짜가 없는 자산 찾기*
* *앞으로 14일 후에 만료될 예정인 /content/dam/products의 모든 에셋 표시*

