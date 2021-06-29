---
title: Cloud Service으로 화면에서 채널 만들기 및 관리
description: 이 페이지에서는 Screens에서 Cloud Service으로 채널을 만들고 관리하는 방법을 설명합니다.
source-git-commit: 3a636a512da40f9a577d25399d33f96d8f6ad8a0
workflow-type: tm+mt
source-wordcount: '550'
ht-degree: 7%

---


# Cloud Service으로 화면에서 채널 만들기 및 관리 {#creating-channels-screens-cloud}

AEM Screens 프로젝트를 만든 후에는 채널을 만들어야 합니다.
***채널***, 일련의 컨텐츠(이미지 및 비디오), 웹 사이트 또는 단일 페이지 애플리케이션을 표시합니다.

## 목표 {#objective}

이 문서는 스크린 컨텐츠 제공자에서 AEM Screens 프로젝트의 채널을 만들고 관리하는 것을 이해하는 데 도움이 됩니다. 읽은 후에는 다음 사항을 충족해야 합니다.

* 스크린 컨텐츠 공급자에 채널을 만드는 방법을 이해합니다
* 채널에서 컨텐츠 관리 및 편집

## 스크린에서 Cloud Service으로 새 시퀀스 채널을 만드는 절차 {#create-new-channel}

>[!NOTE]
>**전제 조건**
>안내서의 이 섹션을 시작하기 전에 [Screens에서 프로젝트 만들기 및 관리 를 Cloud Service](/help/screens-cloud/creating-content/creating-projects-screens-cloud.md)로 검토하십시오.

아래 절차에 따라 Screens에서 Cloud Service으로 새 시퀀스 채널을 만드십시오.

1. 스크린 컨텐츠 제공업체로 이동합니다.

1. *FirstDigitalExperience* 등의 AEM Screens 프로젝트로 이동합니다.

1. **FirstDigitalExperience** —> **채널**&#x200B;과 같이 프로젝트에서 **채널** 폴더를 선택하고 작업 표시줄에서 **만들기**&#x200B;를 클릭합니다.

   ![](/help/screens-cloud/assets/create-content/channel-create1.png)

1. **만들기** 마법사에서 **시퀀스 채널**&#x200B;과 같은 템플릿을 선택하고 **다음**&#x200B;을 클릭합니다.

   ![](/help/screens-cloud/assets/create-content/channel-create2.png)
   >[!NOTE]
   > **만들기** 마법사는 채널을 만드는 동안 다양한 유형의 템플릿을 제공합니다. 자세한 내용은 만들기 마법사의 [사용 가능한 템플릿](#available-templates) 섹션을 참조하십시오.

1. **LoopingChannelOne** 과 같은 시퀀스 채널의 이름을 입력하고 **만들기**&#x200B;를 클릭합니다.

   ![](/help/screens-cloud/assets/create-content/channel-create3.png)

   이제 AEM Screens 프로젝트의 Channels 폴더에 **LoopingChannelOne**&#x200B;이 표시됩니다.

   이제 채널을 만들고 나면 채널에 컨텐츠를 추가할 수 있습니다. 채널에 자산(이미지/비디오)을 추가하는 방법에 대해 알려면 [채널](#add-content)에 컨텐츠 추가 를 참조하십시오.

## 채널 관리 {#managing-channels}

채널을 편집하고, 속성 및 대시보드를 보고, 복사하고, 미리 보고 삭제할 수 있습니다.

아래 그림과 같이 프로젝트에서 채널로 이동하고 채널을 선택합니다. 이제 작업 표시줄에서 채널 편집, 속성 보기, 컨텐츠 미리 보기, 게시 관리 또는 채널 삭제와 같은 옵션을 선택할 수 있습니다.

![](/help/screens-cloud/assets/create-content/channelprop1.png)

### 채널에 컨텐츠 추가 {#add-content}

채널에서 컨텐츠를 추가하거나 편집하려면 아래 절차를 따르십시오.

1. 아래 그림과 같이 편집할 채널을 선택합니다. 작업 표시줄의 왼쪽 위 모서리에서 **편집**&#x200B;을 클릭하여 편집기를 엽니다.

   ![](/help/screens-cloud/assets/create-content/edit-channel1.png)

1. 편집기에서 게시하려는 채널에 자산/구성 요소를 추가할 수 있습니다.

1. 왼쪽 창에서 자산을 끌어다 놓고 편집기에 추가합니다.

   ![](/help/screens-cloud/assets/create-content/edit-channel2.png)

   >[!NOTE]
   >**미리 보기**를 클릭하여 채널의 컨텐츠를 미리 봅니다.
   >![](/help/screens-cloud/assets/create-content/edit-channelpreview.png)

## 만들기 마법사에서 사용 가능한 템플릿 {#available-templates}

**만들기** 채널 마법사를 사용하는 동안 다음 템플릿을 사용할 수 있습니다.

| 사용 가능한 템플릿 | 설명 |
|--- |--- |
| 채널 폴더 | 채널 컬렉션을 저장할 폴더를 만들 수 있습니다. |
| 시퀀스 채널 | 구성 요소를 순차적으로 재생하는 채널을 만들 수 있습니다(슬라이드 쇼에서 하나씩). |
| 왼쪽 또는 오른쪽 L-바 분할 화면 채널 | 컨텐츠 작성자가 적절한 크기의 영역에서 다양한 유형의 자산을 볼 수 있도록 해줍니다. |


## 다음은 무엇입니까? {#whats-next}

이제 프로젝트에서 AEM Screens 채널을 설정했으므로 채널을 게시해야 합니다. Screens 서비스 공급자에서 플레이어를 관리하기 전에 [Cloud Service으로 Screens에 채널 게시](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/screens-as-cloud-service/create-content/manage-publish.html?lang=en)를 참조하십시오.