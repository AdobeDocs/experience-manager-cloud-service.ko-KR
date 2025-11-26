---
title: 콘텐츠 최적화 에이전트
description: 콘텐츠 최적화 에이전트를 사용하여 자연어 지침을 적용하여 채널 준비가 가능한 변형을 만들어 사용자가 에셋을 다듬고 조정하는 방법을 변형하는 방법을 알아봅니다.
feature: Edge Delivery Services, Agentic AI
role: User, Admin, Architect, Developer
source-git-commit: 8b7bdb86c3d1b537b536173b6307c486fe436636
workflow-type: tm+mt
source-wordcount: '907'
ht-degree: 0%

---


# 콘텐츠 최적화 에이전트 {#content-optimization-agent}

콘텐츠 최적화 에이전트는 자연어 지침을 적용하여 채널 준비가 되는 변형을 만들어 사용자가 에셋을 다듬고 조정하는 방법을 변환합니다. 새 렌디션 생성, 시각적 속성 조정, 배경 변경 또는 특정 디지털 채널용 에셋 준비 여부에 관계없이 에이전트는 사용자 의도를 해석하고 복잡한 편집 작업을 자동으로 수행합니다. 검색 에이전트와 원활하게 작동하며, 검색한 자산을 가져와서 수동으로 디자인하지 않고도 브랜드, 채널 및 캠페인 요구 사항을 충족하는 핵심 [OpenAPI 기능이 포함된 다이내믹 미디어](/help/assets/dynamic-media-open-apis-overview.md)를 사용하여 최적화된 변형을 생성합니다.

콘텐츠 최적화의 몇 가지 주요 이점은 다음과 같습니다.

* **간편한 에셋 변환**: 간단한 대화형 프롬프트를 크기 조정, 선명하게 하기, 미러링 또는 다시 색칠과 같은 정밀한 이미지 작업으로 변환하므로 특수 편집 도구가 필요하지 않습니다.

* **채널에 최적화된 출력**: Instagram 스토리, 웹 배너 또는 기타 마케팅 접점과 같은 특정 플랫폼에 맞게 만들어진 렌디션을 신속하게 만들어 자산을 즉시 사용할 수 있도록 합니다.

* **규모에 맞게 Creative 개선 사항**: 배경 변경 사항이나 그래픽 오버레이와 같은 시각적 조정 및 개선 사항을 적용하여 팀을 느리게 하지 않고 대량의 크리에이티브 워크플로우를 지원합니다.

* **[검색 에이전트와 매끄러운 공동 작업](/help/ai-in-aem/agents/discovery/using.md)**: 검색 에이전트가 식별한 에셋을 기반으로 빌드되어 자연스러운 대화를 통해 엔드 투 엔드 에셋 검색 및 최적화를 가능하게 합니다.

>[!IMPORTANT]
>
>AI가 생성한 응답은 정확하지 않거나 오해의 소지가 있을 수 있습니다. 제안된 수정 사항과 응답을 다시 확인하십시오.
>
>[Adobe Experience Cloud Generative AI 사용 지침](https://www.adobe.com/kr/legal/licenses-terms/adobe-dx-gen-ai-user-guidelines.html)도 참조하세요.

## 사전 요구 사항 {#prerequisites-content-optimization-agent}

이미지 에셋에 대한 변형 또는 최적화를 생성하려면 다음을 수행합니다. 다음을 보유해야 합니다.

* 유효한 Dynamic Media 라이선스

* AEM as a Cloud Service 환경에서 OpenAPI가 활성화된 Dynamic Media.

* AEM as a Cloud Service 환경에서 [승인된 상태](/help/assets/manage-organize-assets-view.md#manage-asset-status)의 자산입니다.


## 기술 {#skills-content-optimization-agent}

콘텐츠 최적화 에이전트는 다음 기술을 제공합니다.

* **자연어를 통해 의도 이해**

  콘텐츠 최적화 에이전트는 자연어 프롬프트에서 사용자 의도를 해석하여 채널, 캠페인 및 대상 컨텍스트를 고려하여 가장 관련성이 높은 최적화 작업을 결정합니다.

* **동적 콘텐츠 변형을 생성합니다**

  콘텐츠 최적화 에이전트는 다양한 채널 및 형식 유형에 맞게 조정된 동적 URL로 최적화된 변형을 만듭니다.

* **이미지 콘텐츠 최적화**

  콘텐츠 최적화 에이전트는 이미지 품질을 개선하기 위해 형식 변환, 해상도 조정, 자르기 및 선명하게 하기 등의 개선 사항을 적용합니다.

* **다중 변형 에셋 최적화**

  콘텐츠 최적화 에이전트는 단일 자연어 프롬프트를 사용하여 검색 에이전트가 반환한 에셋에서 최적화된 여러 이미지 변형을 생성할 수 있으므로 사용자가 채널 준비가 된 렌디션을 빠르고 효율적으로 생성할 수 있습니다.

## 가상 사용자 {#personas-content-optimization-agent}

콘텐츠 최적화 에이전트의 주요 담당자인 채널 마케터는 올바른 고해상도 소스 콘텐츠를 선택하고 채널 및 대상 세그먼트에 맞는 최적화된 형식을 요청할 수 있습니다.

지역 마케터와 에이전시 작업자는 콘텐츠 최적화 에이전트를 사용하여 보다 빠르고 일관된 콘텐츠 제작을 지원하는 채널 준비가 완료된 이미지 변형을 신속하게 생성할 수도 있습니다.

## 콘텐츠 최적화 에이전트에 액세스하는 방법 {#access-content-optimization-agent}

AI Assistant를 통해 AEM의 에이전트에 액세스할 수 있습니다. experience.adobe.com에 로그온하면 `Ask AI Assistant anything` 필드를 사용하여 자연어로 프롬프트를 지정하여 AI Assistant와 상호 작용할 수 있습니다.

![검색 에이전트 액세스](/help/ai-in-aem/agents/discovery/assets/access-discovery-agent.png)

## 일반적인 사용 사례 및 샘플 프롬프트 {#use-cases-prompts}

[검색 에이전트](/help/ai-in-aem/agents/discovery/using.md)를 통해 올바른 자산을 검색하여 콘텐츠 최적화 메시지를 사용합니다. 관련 이미지가 표시되면 사용자는 검색 결과에서 직접 하나 이상의 에셋에 대해 최적화된 또는 채널별 변형을 생성할 수 있습니다. 이 워크플로우는 고품질의 입력을 보장하며 일관되게 더 나은 최적화 결과를 제공합니다. [사용 가능한 최적화의 전체 목록을 봅니다](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/stable/assets/delivery/).

* **고해상도 렌디션 만들기**

  에이전트는 지정된 해상도 및 품질 수준에서 에셋의 새 렌디션을 생성할 수 있으므로 수동 편집 없이 채널 준비가 가능한 변형을 쉽게 준비할 수 있습니다.


  샘플 프롬프트:

  `2000px` 품질의 `JPEG` 렌디션을 `80%`(으)로 만듭니다.

  [검색 에이전트](/help/ai-in-aem/agents/discovery/using.md)를 사용하여 올바른 자산을 검색한 다음 검색 결과가 여러 개인 경우 다음 메시지를 사용하십시오.

  세 번째 검색 결과에 대해 `2000px` 품질의 `JPEG` 렌디션을 `80%`(으)로 만듭니다.

  또는

  `Asset ID`의 경우 `JPEG` 품질의 2000px 렌디션을 `80%`(으)로 생성합니다.

* **이미지 개선**

  에이전트는 선명하게 하기가 처럼 시각적으로 개선되어 캠페인 간에 에셋을 사용하기 전에 선명하게 보이고 잘 정의되도록 할 수 있습니다.

  샘플 프롬프트:

  이미지를 선명하게 합니다.


* **배경색 조정**

  에이전트는 투명 에셋의 배경색을 업데이트하거나 교체하여 브랜드별 색상 구성표 또는 캠페인 중심의 시각적 테마를 지원할 수 있습니다.

  샘플 프롬프트:

  `PNG`의 배경색을 `#ff8932`(으)로 변경합니다.

* **방향 변형**

  에이전트는 외부 편집 도구 없이 시각적 개체를 뒤집거나 미러링하여 레이아웃 요구 사항이나 크리에이티브 방향에 맞출 수 있습니다.

  샘플 프롬프트:

  이미지를 가로로 미러링합니다.

* **채널에 최적화된 렌디션**

  에이전트는 Instagram 스토리와 같은 플랫폼별 요구 사항에 맞는 렌디션을 제작하여 자산이 형식, 비율 및 품질 지침을 자동으로 충족하도록 할 수 있습니다.

  샘플 프롬프트:

  `Instagram` 스토리에 대한 렌디션을 만듭니다.

* **브랜드 오버레이 및 복합 생성**

  에이전트는 정확한 배치로 기존 에셋에 홍보 그래픽, 오버레이 또는 배지를 적용하여 캠페인 준비 조합을 신속하게 만들 수 있습니다.

  샘플 프롬프트:

  프로모션 배너 위에 `30%` 할인 그래픽으로 이미지를 오버레이합니다. 중앙에서 `100px`을(를) 배치합니다.

  >[!NOTE]
  >
  >오버레이 위치가 정확하지 않을 수 있습니다.


## 최적화 결과 {#content-optimization-agent-results}

최적화 프롬프트를 지정할 때 콘텐츠 최적화 에이전트는 에셋 유형에 따른 편리한 액세스 옵션과 함께 향상된 에셋을 반환합니다.

* **이미지**: 응답에는 Dynamic Media URL을 열거나 최적화된 이미지를 다운로드하는 썸네일 미리 보기 및 옵션이 포함됩니다.

* **PDF 문서**: 응답에는 Dynamic Media URL을 열거나 최적화된 파일을 다운로드할 수 있는 썸네일 미리 보기 및 옵션이 포함됩니다.

* **비디오**: 응답에서 Dynamic Media URL을 열거나 최적화된 비디오를 다운로드하는 옵션을 제공합니다.

![콘텐츠 최적화 결과](/help/ai-in-aem/agents/content-optimization/assets/download-content-optimization.png)

이러한 결과를 통해 최적화된 출력을 쉽게 검토하고 다운스트림 채널 또는 워크플로에서 즉시 사용할 수 있습니다.

<!--


## Prompting best Practices {#prompting-best-practices-content-optimization-agent}

The following are some of the prompting best practices:

* Be explicit about the enhancement you want the Content Optimization Agent to apply. Clearly state the transformation or adjustment you expect. Precise instructions help the agent produce accurate and predictable results. For example, Instead of `Make it good quality`, specify `Create a JPEG image with 90% quality`.

* Provide detailed parameters whenever possible. The more context you give, such as dimensions, format, quality, placement, or color values, the more tailored the output is.

-->
