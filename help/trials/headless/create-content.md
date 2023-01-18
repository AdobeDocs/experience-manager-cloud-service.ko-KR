---
title: Headless 콘텐츠 만들기
description: 이전에 만든 콘텐츠 조각 모델을 사용하여 페이지 작성에 사용할 수 있는 콘텐츠를 만들거나 headless 콘텐츠의 기반으로 사용할 수 있습니다.
hidefromtoc: true
index: false
exl-id: d74cf5fb-4c4a-4363-a500-6e2ef6811e60
source-git-commit: bcab02cbd84955ecdc239d4166ae38e5f79b3264
workflow-type: tm+mt
source-wordcount: '515'
ht-degree: 30%

---


# Headless 콘텐츠 만들기 {#create-content}

>[!CONTEXTUALHELP]
>id="aemcloud_sites_trial_admin_content_fragments_create_content"
>title="새 콘텐츠 만들기"
>abstract="이전 모듈에서 만든 모델을 사용하면 페이지 작성에 사용하거나 헤드리스 컨텐츠를 기반으로 사용할 수 있는 컨텐츠를 만드는 방법을 알아봅니다."

>[!CONTEXTUALHELP]
>id="aemcloud_sites_trial_admin_content_fragments_create_content_guide"
>title="콘텐츠 조각 콘솔 실행"
>abstract="앱 및 웹 사이트에서 원활하게 작동하는 일관된 고품질 컨텐츠를 만들면 훌륭한 고객 경험이 제공됩니다. 이 모듈은 첫 번째 컨텐츠 조각을 만드는 과정을 안내하여 이를 만드는 방법을 보여줍니다. 이 단계가 중요한 단계인 이유를 이해하려면 비디오를 시청하십시오.<br><br>아래 버튼을 클릭하여 새 탭에서 이 모듈을 시작한 다음 이 안내서를 따르십시오."
>additional-url="https://video.tv.adobe.com/v/328618" text="새 컨텐츠 소개 비디오 만들기"

>[!CONTEXTUALHELP]
>id="aemcloud_sites_trial_admin_content_fragments_create_content_guide_footer"
>title="잘했어요! 이 모듈에서 이전에 만든 모델을 기반으로 컨텐츠 조각을 작성하는 방법을 알아보았습니다. 이제 콘텐츠 팀이 개발 주기에 관계없이 앱 및 웹 사이트에 대한 콘텐츠를 만들고 관리하는 방법을 이해할 수 있습니다."
>abstract=""

## 콘텐츠 조각 만들기 {#create-fragment}

클릭 **컨텐츠 조각 콘솔 시작** 위의 버튼을 클릭하면 새 탭에서 컨텐츠 조각 콘솔이 열립니다.

![조각 콘텐츠 편집](assets/create-content/content-fragment-console.png)

컨텐츠 조각은 헤드리스 컨텐츠를 나타내며 컨텐츠 조각 모델이라고 하는 사전 정의된 구조를 기반으로 합니다. 컨텐츠 조각 콘솔을 헤드리스 컨텐츠 라이브러리로 생각해 보십시오. 이 조각을 사용하여 새 컨텐츠 조각을 만들고 기존 컨텐츠 조각을 관리합니다. 콘솔이 비어 있으므로 새 조각을 만들어 봅시다!

1. 을(를) 탭하거나 클릭합니다 **만들기** 콘솔 오른쪽 상단의 단추.

1. 다음 **새 컨텐츠 조각** 새 컨텐츠 조각 만들기를 시작할 수 있는 대화 상자가 열립니다. **위치** 은(는) 새 컨텐츠를 저장할 위치로 자동 채워집니다.

   ![콘텐츠 조각 만들기 대화 상자](assets/create-content/create-content-fragment.png)

1. 에서 **컨텐츠 조각 모델** 드롭다운에서 이전에 만든 컨텐츠 조각 모델을 선택합니다.

1. 콘텐츠 조각에 대한 **제목**&#x200B;을 추가합니다.

1. **만들기 및 열기**&#x200B;를 탭하거나 클릭합니다.

## 컨텐츠 조각에 컨텐츠 추가 {#add-content}

새 컨텐츠 조각을 저장하고 열면 컨텐츠 조각 편집기가 새 탭에서 열립니다. 여기에서 새 조각의 컨텐츠를 추가할 수 있습니다.

1. 컨텐츠 조각 편집기는 선택한 모델에서 정의한 필드를 보여줍니다. 여기에서 각 필드에 컨텐츠를 추가하여 컨텐츠 조각을 완료할 수 있습니다. 진행 상황이 자동으로 저장됩니다.

   ![콘텐츠 조각 편집기](assets/create-content/content-fragment-editor.png)

1. 콘텐츠 추가를 마치면 를 탭하거나 클릭합니다 **게시** 편집기의 오른쪽 상단에 있는 단추. 이렇게 하면 컨텐츠 조각을 외부 앱에서 사용할 수 있습니다.

1. 드롭다운에서 **지금**&#x200B;을 선택합니다. 나중에 게시하도록 예약할 수도 있습니다.

   ![게시 버튼](assets/create-content/publish.png)

1. 다음 **컨텐츠 조각 게시** 대화 상자가 나타납니다. AEM은 참조 확인을 자동으로 수행하여 콘텐츠 조각에 필요한 모든 리소스가 게시되었는지 확인합니다. 이 경우 만든 모델도 게시해야 합니다. **게시**&#x200B;를 탭하거나 클릭합니다.

   ![참조 확인](assets/create-content/references.png)

1. 게시는 배너에서 확인합니다.

   ![게시 확인](assets/create-content/publish-confirm.png)

컨텐츠가 게시되어 앱 또는 웹 사이트에 컨텐츠 조각으로 전달될 준비가 되었습니다.
