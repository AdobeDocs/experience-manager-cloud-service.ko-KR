---
title: 앱의 콘텐츠 구조 만들기
description: AEM의 콘텐츠 조각 모델을 사용하여 모든 headless 콘텐츠의 기반 역할을 하는 구조의 생성 방법에 대해 알아봅니다.
hidefromtoc: true
index: false
exl-id: ace9b9f3-8bc6-4a36-a51c-ff60cdd339ce
source-git-commit: bcab02cbd84955ecdc239d4166ae38e5f79b3264
workflow-type: tm+mt
source-wordcount: '492'
ht-degree: 38%

---


# 앱의 콘텐츠 구조 만들기 {#content-structure}

>[!CONTEXTUALHELP]
>id="aemcloud_sites_trial_admin_content_fragments_overview"
>title="앱의 콘텐츠 구조 만들기"
>abstract="이 일련의 대화형 지침을 따라 헤드리스 컨텐츠의 기초 역할을 하는 구조(컨텐츠 조각 모델이라고 함)를 만드는 방법을 알아봅니다."

>[!CONTEXTUALHELP]
>id="aemcloud_sites_trial_admin_content_fragments_overview_guide"
>title="모델 콘솔을 시작합니다"
>abstract="Adobe Experience Manager as a Cloud Service에서 컨텐츠를 위해 컨텐츠 조각 모델이라고 하는 재사용 가능한 스키마를 만드는 방법을 살펴보겠습니다. 이 단계가 중요한 단계인 이유를 이해하려면 비디오를 시청하십시오. <br><br>아래 버튼을 클릭하여 새 탭에서 이 모듈을 시작하고 이 안내서를 따르십시오."
>additional-url="https://video.tv.adobe.com/v/3413261" text="콘텐츠 구조 소개 비디오"

>[!CONTEXTUALHELP]
>id="aemcloud_sites_trial_admin_content_fragments_overview_guide_footer"
>title="축하합니다! 헤드리스 데이터의 구조를 나타내는 컨텐츠 조각 모델을 만드는 방법을 학습하고 첫 번째 단계를 수행하여 옴니채널 컨텐츠를 규모에 맞게 표준 방식으로 전달하는 방법을 알아보았습니다."
>abstract=""

## 모델 만들기 {#create-model}

클릭 **모델 콘솔을 시작합니다** 위의 버튼을 클릭하면 새 탭에서 컨텐츠 조각 모델 콘솔이 열립니다.

![콘텐츠 조각 모델 콘솔](assets/content-structure/content-fragment-model-console.png)

컨텐츠 조각 모델 콘솔을 새로운 모델을 만들고 기존 모델을 관리하는 모델 라이브러리로 생각해 보십시오. 콘솔이 비어 있으므로 새 모델을 만들어 봅시다!

1. 콘텐츠 조각 모델 콘솔에서 화면 오른쪽 상단의 **만들기** 버튼을 클릭하여 콘텐츠 조각 모델을 만들기 시작합니다.

1. 모델 생성 마법사가 시작되어 안내합니다.

   ![콘텐츠 조각 모델 마법사](assets/content-structure/model-wizard.png)

   필수 정보를 입력합니다.

   * **모델 제목** - 모델에 대한 간단한 설명이며 일반적으로 모델의 용도를 나타냅니다.
   * **모델 활성화** - 이 옵션은 기본적으로 선택되어 있으므로 이 모델을 기반으로 컨텐츠 조각을 만들 수 있는지 확인해야 합니다.

1. 필수 필드를 채운 후 **만들기** 왼쪽 상단에서 모델을 생성합니다.

1. **완료** 대화 상자에서 모델이 생성되었음을 확인합니다.

   ![새 콘텐츠 조각 모델을 만들기 위한 완료 대화 상자](assets/content-structure/success.png)

## 모델에 필드 추가 {#configure-model}

모델을 사용하려면 먼저 해당 데이터의 구조를 정의해야 합니다.

1. 클릭 **열기** 에서 **성공** 이전 단계의 대화 상자에서 컨텐츠 조각 모델 편집기에서 새 모델을 엽니다. 여기서 이 모델은 필드를 정의할 수 있습니다.

1. 에서 필드를 드래그합니다. **데이터 유형** 편집기 오른쪽에 있는 패널로 이동하여 컨텐츠 조각 모델에 드롭합니다.

   ![데이터 유형 추가](assets/content-structure/drop-fields.png)

1. 데이터 유형이 배치되면 **데이터 유형** 열이 자동으로 **속성** 탭으로 변경되어 방금 배치된 데이터 유형의 세부 정보를 정의할 수 있습니다.

   ![데이터 필드의 속성 탭](assets/content-structure/data-type-properties.png)

1. 콘텐츠 조각 모델에 필요한 모든 필드가 추가되었으면 창의 오른쪽 상단에 있는 **저장**&#x200B;을 클릭합니다.

모델이 저장되고 필요에 따라 모델을 더 추가할 수 있는 컨텐츠 조각 모델 콘솔로 돌아갑니다.

![모듈 완료](assets/content-structure/content-fragment-model-console-populated.png)
