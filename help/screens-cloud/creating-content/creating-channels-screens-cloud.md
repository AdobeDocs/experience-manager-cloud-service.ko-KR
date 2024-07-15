---
title: Screensas a Cloud Service 에서 채널 만들기 및 관리
description: 이 페이지에서는 Screensas a Cloud Service 에서 채널을 만들고 관리하는 방법을 설명합니다.
exl-id: 3b0bae7a-4a45-485a-ab04-604510ff6578
feature: Authoring Screens
role: Admin, Developer, User
source-git-commit: f9ba9fefc61876a60567a40000ed6303740032e1
workflow-type: tm+mt
source-wordcount: '1103'
ht-degree: 1%

---

# Screensas a Cloud Service 에서 채널 만들기 및 관리 {#creating-channels-screens-cloud}

AEM Screens 프로젝트를 만든 후에는 채널을 만들어야 합니다.
***채널***&#x200B;은(는) 콘텐츠 시퀀스(이미지 및 비디오), 웹 사이트 또는 단일 페이지 응용 프로그램을 표시합니다.

## 목표 {#objective}

이 문서는 Screens Content Provider에서 AEM Screens 프로젝트에 대한 채널을 만들고 관리하는 방법을 이해하는 데 도움이 됩니다. 문서를 읽고 나면 다음과 같은 작업을 수행할 수 있습니다.

* Screens Content Provider에 대한 채널을 만드는 방법 이해
* 채널에서 콘텐츠 관리 및 편집
* [Screens 서비스 공급자](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/screens-as-cloud-service/configure-screens-cloud/navigating-to-screens-services-provider.html?lang=ko-KR)에서 채널의 할당 및 활성화 일정을 관리합니다.

## Screensas a Cloud Service 에서 새 시퀀스 채널을 만드는 절차 {#create-new-channel}

>[!NOTE]
>**전제 조건**
>안내서의 섹션을 시작하기 전에 [이 Screensas a Cloud Service 에서 프로젝트 만들기 및 관리](/help/screens-cloud/creating-content/creating-projects-screens-cloud.md)를 검토하십시오.

아래 단계에 따라 Screensas a Cloud Service 에서 시퀀스 채널을 만듭니다.

1. Screens 컨텐츠 공급자로 이동합니다.

1. *FirstDigitalExperience*&#x200B;와 같은 AEM Screens 프로젝트로 이동합니다.

1. 프로젝트에서 **채널** 폴더(예: **FirstDigitalExperience** —> **채널**)를 선택하고 작업 표시줄에서 **만들기**&#x200B;를 클릭합니다.

   ![channel-create1](/help/screens-cloud/assets/create-content/channel-create1.png)

1. **만들기** 마법사에서 **시퀀스 채널**&#x200B;과 같은 템플릿을 선택하고 **다음**&#x200B;을(를) 클릭합니다.

   ![channel-create2](/help/screens-cloud/assets/create-content/channel-create2.png)

   >[!NOTE]
   > **만들기** 마법사는 채널을 만드는 동안 다양한 유형의 템플릿을 제공합니다. 자세한 내용은 만들기 마법사의 [사용 가능한 템플릿](#available-templates)을 참조하십시오.

1. 시퀀스 채널의 이름(예: **LoopingChannelOne**)을 입력하고 **만들기**&#x200B;를 클릭합니다.

   ![channel-create3](/help/screens-cloud/assets/create-content/channel-create3.png)

   이제 AEM Screens 프로젝트의 Channels 폴더에 **LoopingChannelOne**&#x200B;이(가) 표시됩니다.

   채널을 만들면 이제 채널에 컨텐츠를 추가할 수 있습니다. 채널에 에셋(이미지/비디오)을 추가하는 방법에 대해 알아보려면 [채널에 콘텐츠 추가](#add-content)를 참조하십시오.

## 채널 관리 {#managing-channels}

채널을 편집하고, 등록 정보와 대시보드를 보고, 복사하고, 미리 보고, 삭제할 수 있습니다.

아래 그림과 같이 프로젝트에서 채널로 이동하고 채널을 선택합니다. 이제 채널 편집, 속성 보기, 콘텐츠 미리 보기, 게시 관리 또는 작업 표시줄에서 채널 삭제와 같은 옵션을 선택할 수 있습니다.

![channelprop1](/help/screens-cloud/assets/create-content/channelprop1.png)

### 채널에 콘텐츠 추가 {#add-content}

채널에서 컨텐츠를 추가하거나 편집하려면 아래 단계를 따르십시오.

1. 아래 그림과 같이 편집할 채널을 선택합니다. 작업 표시줄의 왼쪽 상단 모서리에서 **편집**&#x200B;을 클릭하여 편집기를 엽니다.

   ![edit-channel1](/help/screens-cloud/assets/create-content/edit-channel1.png)

1. 편집기를 사용하면 게시할 채널에 에셋/구성 요소를 추가할 수 있습니다.

1. 왼쪽 창에서 에셋을 끌어다 놓고 편집기에 추가합니다.

   ![edit-channel2](/help/screens-cloud/assets/create-content/edit-channel2.png)

   >[!NOTE]
   >채널의 내용을 미리 보려면 **미리 보기**를 클릭하십시오.
   >![edit-channelpreview](/help/screens-cloud/assets/create-content/edit-channelpreview.png)

## 만들기 마법사에서 사용할 수 있는 템플릿 {#available-templates}

**만들기** 채널 마법사를 사용하는 동안 다음 템플릿을 사용할 수 있습니다.

| 사용 가능한 템플릿 | 설명 |
|--- |--- |
| 채널 폴더 | 채널 컬렉션을 저장할 폴더를 만들 수 있습니다. |
| 시퀀스 채널 | 슬라이드 쇼에서 하나씩 구성 요소를 순차적으로 재생하는 채널을 만들 수 있습니다. |
| 왼쪽 또는 오른쪽 L-표시줄 분할 화면 채널 | 콘텐츠 작성자는 적절한 크기의 영역에서 다양한 유형의 에셋을 볼 수 있습니다. |

## 채널에 대한 기본 할당 세부 정보 사용 {#default-channels}

이 기능을 사용하면 채널에 대한 기본 활성화 일정을 정의하고 표시에 대한 모든 할당에 대해 기본적으로 사용할 수 있습니다. 이는 번거로운 스케줄 정의를 반복할 필요가 없도록 하는 방법을 제공한다.

1. [여기](https://experience.adobe.com/screens)에서 Screens 서비스 공급자로 이동합니다.

### 채널에 대한 기본 할당 세부 정보 만들기 {#create-default}

1. 구성할 채널의 세부 정보 페이지로 이동합니다.
1. 페이지에서 **기본 할당 세부 정보** 타일을 찾습니다.

   ![이미지](/help/screens-cloud/assets/display/Assignment1.png)

1. **기본 세부 정보 설정**&#x200B;을 클릭합니다.
1. 우선 순위, 시작 및 종료 날짜, 채널의 반복 패턴을 포함하여 기본 할당 세부 정보를 구성하고 **할당**&#x200B;을 클릭하세요.

   ![이미지](/help/screens-cloud/assets/display/Assignments2.png)

1. 할당 세부 정보가 **기본 할당 세부 정보** 타일에 표시됩니다.

   ![이미지](/help/screens-cloud/assets/display/Assignments3.png)

이 타일에는 다음 정보가 표시됩니다.
* 디스플레이에서 채널의 기본 우선 순위입니다.
* 채널 재생이 예정된 활성화 시작 및 종료 날짜입니다.
* 반복에 대한 합성 보기(시간별/일별/주별/월별/연간 및 해당 반복에 제공된 이름).

### 디스플레이에 할당할 때 기본 할당 세부 정보 사용 {#default-display}

기본 할당 세부 정보가 있는 채널을에 할당하면 일반 채널과 동일한 방식으로 표시할 수 있으며, 매번 사용자 지정 세부 정보를 수동으로 정의하는 대신 기본 할당 세부 정보를 사용하는 옵션이 추가되었습니다.

1. 채널을 할당할 디스플레이 세부 정보 페이지로 이동하여 **채널 할당**을 클릭합니다.
또는 [인벤토리](https://experience.adobe.com/screens/displays) 보기에서 원하는 표시를 선택하고 **채널 할당**&#x200B;을 클릭합니다.
1. 채널 할당 대화 상자가 열립니다.

   ![이미지](/help/screens-cloud/assets/display/Assignments4.png)

1. 채널 선택기에서 기본 할당 세부 정보가 있는 원하는 채널을 선택합니다.
1. 채널 할당 대화 상자 변경 사항에 주목하여 기본 할당 세부 정보를 선택하거나 사용자 지정 할당 세부 정보를 선택합니다.

   ![이미지](/help/screens-cloud/assets/display/Assignments5.png)

1. **할당**&#x200B;을 클릭하여 할당을 완료하거나 **사용자 지정 할당 세부 정보 설정**&#x200B;을 클릭합니다.

   ![이미지](/help/screens-cloud/assets/display/Assignments6.png)

1. **할당된 채널** 타일이 새 할당으로 업데이트되었습니다.

   ![이미지](/help/screens-cloud/assets/display/Assignments7.png)

1. 채널에는 사용자 지정 예약(시계 아이콘)을 사용하는지 또는 기본 세부 정보(세계 시계 아이콘)를 상속하는지 여부에 따라 다른 아이콘이 표시되며, 해당 아이콘을 클릭하면 예약 세부 정보가 표시됩니다.
1. 또한 각 유형에 사용할 수 있는 작업이 달라집니다.

   ![이미지](/help/screens-cloud/assets/display/Assignments8.png)

**참고:** 기본 할당 세부 정보를 사용하는 채널 할당은 디스플레이 컨텍스트에서 편집할 수 없습니다.

* 사용자 지정 할당으로 변경해야 하는 경우 먼저 제거한 후 **사용자 지정 할당 세부 정보 설정** 옵션을 사용하여 다시 추가하십시오.
* 기본 할당 세부 정보의 속성을 변경해야 하는 경우 채널 세부 정보 페이지에서 바로 변경할 수 있습니다.

### 채널에서 기본 할당 세부 정보 제거 {#remove-display}

1. 기본 지정 세부 정보를 제거할 채널에 대한 세부 정보 페이지로 이동합니다.
1. 페이지에서 **기본 할당 세부 정보** 타일을 찾습니다.
1. **기본값 제거**&#x200B;를 클릭합니다.

   ![이미지](/help/screens-cloud/assets/display/Assignments9.png)

1. 확인 대화 상자가 표시되며, 세부 사항은 다음 조건 중 하나와 일치합니다.
   **a.** 채널은 어떤 디스플레이에서도 사용되지 않습니다.

   ![이미지](/help/screens-cloud/assets/display/Assignments10.png)

**b.** 채널은 단일 디스플레이에서 사용됩니다.

![이미지](/help/screens-cloud/assets/display/Assignment11.png)

**c.** 채널이 여러 디스플레이에서 사용되고 있습니다.

![이미지](/help/screens-cloud/assets/display/Assignments12.png)

1. 변경 내용의 유효성을 검사하려면 *제거*&#x200B;를 클릭하십시오.

**참고:** 채널에서 기본 할당 세부 정보를 제거하면 해당 정보를 사용 중인 모든 디스플레이에서 일치하는 할당이 제거됩니다.
따라서 해당 디스플레이에서 재생할 대체 컨텐츠가 없는 경우 빈 화면이 표시될 수 있습니다.

## 다음 단계 {#whats-next}

이제 프로젝트에서 AEM Screens 채널을 설정했으므로 채널을 게시해야 합니다. 플레이어를 관리하기 전에 Screensas a Cloud Service Screens 에서 [채널 게시](manage-publish.md)를 참조하십시오.
