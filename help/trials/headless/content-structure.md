---
title: 앱의 콘텐츠 구조 만들기
description: AEM의 콘텐츠 조각 모델을 사용하여 모든 Headless 콘텐츠의 기반 역할을 하는 구조의 생성 방법에 대해 알아봅니다.
hidefromtoc: true
index: false
exl-id: ace9b9f3-8bc6-4a36-a51c-ff60cdd339ce
source-git-commit: fa36470e50abdf6dd019a91665945ff6e68e40c2
workflow-type: tm+mt
source-wordcount: '477'
ht-degree: 93%

---


# 앱의 콘텐츠 구조 만들기 {#content-structure}

>[!CONTEXTUALHELP]
>id="aemcloud_sites_trial_admin_content_fragments_overview"
>title="앱의 콘텐츠 구조 만들기"
>abstract="대화형 안내서 시리즈를 따라가면서 Headless 콘텐츠의 기반 역할을 하는 구조(콘텐츠 조각 모델이라고 함)를 만드는 방법을 알아봅니다."

>[!CONTEXTUALHELP]
>id="aemcloud_sites_trial_admin_content_fragments_overview_guide"
>title="모델 콘솔 실행"
>abstract="Adobe Experience Manager as a Cloud Service에서 콘텐츠에 대한 재사용 가능한 스키마(콘텐츠 조각 모델)를 만드는 방법에 대해 살펴보겠습니다. 비디오를 시청하여 이 단계가 중요한 이유에 대해 알아보십시오. <br><br>아래 버튼을 클릭하여 새 탭에서 이 모듈을 실행한 다음 이 안내서를 따르십시오."
>additional-url="https://video.tv.adobe.com/v/3413261" text="콘텐츠 구조 소개 비디오"

>[!CONTEXTUALHELP]
>id="aemcloud_sites_trial_admin_content_fragments_overview_guide_footer"
>title="축하합니다! Headless 데이터의 구조를 나타내는 콘텐츠 조각 모델을 만드는 방법에 대해 배웠으며, 크기 조정되고 표준적인 방법으로 옴니채널 콘텐츠를 제공하기 위한 첫 번째 단계를 수행했습니다."
>abstract=""

## 모델 만들기 {#create-model}

콘텐츠 조각 모델 콘솔이 새 탭에서 열립니다. 콘텐츠 조각 모델 콘솔을 새 모델을 만들고 기존 모델을 관리하는 모델 라이브러리로 생각해 보십시오.

1. 화면 오른쪽 상단의 **만들기** 버튼을 클릭하여 콘텐츠 조각 모델을 만들기 시작합니다.

1. 사용자를 안내하는 모델 만들기 마법사가 시작됩니다. 필수 정보를 입력합니다.

   * **모델 제목** - 모델에 대한 간략한 설명이며 일반적으로 모델의 용도를 나타냅니다.
   * **모델 활성화** - 이 옵션은 기본적으로 선택되어 있으며 이 모델을 기반으로 콘텐츠 조각을 만들 수 있도록 선택해야 합니다.

1. 필수 필드가 채워지면 왼쪽 상단에서 **만들기**&#x200B;를 클릭하여 모델을 만듭니다.

1. **완료** 대화 상자에서 모델이 생성되었음을 확인합니다. 대화 상자에서 **열기**&#x200B;를 클릭하여 편집기의 새 콘텐츠 조각 모델을 새 탭에서 엽니다. 그런 다음 모델에 필드 추가 단계로 계속 진행합니다.

![콘텐츠 조각 모델 만들기 2단계 및 3단계](assets/do-not-localize/create-model-2-3.png)

## 모델에 필드 추가 {#configure-model}

모델을 사용하기 전에 데이터 구조를 정의해야 합니다. 콘텐츠 조각 모델 편집기에서 모델의 콘텐츠를 정의하는 데이터 유형과 속성을 구성할 수 있습니다.

1. 편집기 오른쪽에 있는 **데이터 유형** 패널에서 필드를 드래그하여 콘텐츠 조각 모델에 놓습니다.

1. 데이터 유형이 배치되면 **데이터 유형** 열이 자동으로 **속성** 탭으로 변경되어 방금 배치된 데이터 유형의 세부 정보를 정의할 수 있습니다.

1. 콘텐츠 조각 모델에 필요한 모든 필드가 추가되었으면 창의 오른쪽 상단에 있는 **저장**&#x200B;을 클릭합니다.

1. 모델이 저장되면 콘텐츠 조각 모델 콘솔로 돌아갑니다.

![모델에 필드 추가 1, 2, 3단계](assets/do-not-localize/define-model-fields-1-2-3.png)
