---
title: 화면에서 채널 생성 및 관리 as a Cloud Service
description: 이 페이지에서는 Screens에서 채널을 만들고 관리하는 방법을 as a Cloud Service으로 설명합니다.
exl-id: 3b0bae7a-4a45-485a-ab04-604510ff6578
source-git-commit: afcee8019c9b59f3eb1fdcabd569272eeea76dab
workflow-type: tm+mt
source-wordcount: '1116'
ht-degree: 4%

---

# 채널에서 as a Cloud Service 생성 및 관리 {#creating-channels-screens-cloud}

AEM Screens 프로젝트를 만든 후에는 채널을 만들어야 합니다.
***채널***, 일련의 컨텐츠(이미지 및 비디오), 웹 사이트 또는 단일 페이지 애플리케이션을 표시합니다.

## 목표 {#objective}

이 문서는 스크린 컨텐츠 제공자에서 AEM Screens 프로젝트의 채널을 만들고 관리하는 것을 이해하는 데 도움이 됩니다. 읽은 후에는 다음 사항을 충족해야 합니다.

* 스크린 컨텐츠 공급자에 채널을 만드는 방법을 이해합니다
* 채널에서 컨텐츠 관리 및 편집
* 채널에 대한 활성화 예약

## 화면에서 새 시퀀스 채널을 만드는 단계 as a Cloud Service {#create-new-channel}

>[!NOTE]
>**전제 조건**
>안내서의 이 섹션을 시작하기 전에 [화면에서 프로젝트 생성 및 관리 as a Cloud Service](/help/screens-cloud/creating-content/creating-projects-screens-cloud.md).

아래 절차에 따라 Screens as a Cloud Service에서 새 시퀀스 채널을 만드십시오.

1. 스크린 컨텐츠 제공업체로 이동합니다.

1. 다음과 같이 AEM Screens 프로젝트로 이동합니다 *FirstDigitalExperience*.

1. 을(를) 선택합니다 **채널** 다음과 같이 프로젝트의 폴더를 지정합니다. **FirstDigitalExperience** —> **채널** 을(를) 클릭합니다. **만들기** 작업 표시줄.

   ![](/help/screens-cloud/assets/create-content/channel-create1.png)

1. 다음과 같은 템플릿을 선택합니다. **시퀀스 채널** 에서 **만들기** 마법사를 클릭하고 **다음**.

   ![](/help/screens-cloud/assets/create-content/channel-create2.png)
   >[!NOTE]
   > 다음 **만들기** 마법사는 채널을 만드는 동안 다양한 유형의 템플릿을 제공합니다. 섹션을 참조하십시오 [사용 가능한 템플릿](#available-templates) 을 참조하십시오.

1. 시퀀스 채널의 이름(예: )을 입력합니다. **LoopingChannelOne** 을(를) 클릭합니다. **만들기**.

   ![](/help/screens-cloud/assets/create-content/channel-create3.png)

   이제 **LoopingChannelOne** AEM Screens 프로젝트의 채널 폴더에서 을 사용할 수 있습니다.

   이제 채널을 만들고 나면 채널에 컨텐츠를 추가할 수 있습니다. 을(를) 참조하십시오. [채널에 컨텐츠 추가](#add-content) 자산에 자산(이미지/비디오)을 채널에 추가하는 방법을 알아봅니다.

## 채널 관리 {#managing-channels}

채널을 편집하고, 속성 및 대시보드를 보고, 복사하고, 미리 보고 삭제할 수 있습니다.

아래 그림과 같이 프로젝트에서 채널로 이동하고 채널을 선택합니다. 이제 작업 표시줄에서 채널 편집, 속성 보기, 컨텐츠 미리 보기, 게시 관리 또는 채널 삭제와 같은 옵션을 선택할 수 있습니다.

![](/help/screens-cloud/assets/create-content/channelprop1.png)

### 채널에 컨텐츠 추가 {#add-content}

채널에서 컨텐츠를 추가하거나 편집하려면 아래 절차를 따르십시오.

1. 아래 그림과 같이 편집할 채널을 선택합니다. 클릭 **편집** 작업 표시줄의 왼쪽 위 모서리에서 편집기를 엽니다.

   ![](/help/screens-cloud/assets/create-content/edit-channel1.png)

1. 편집기에서 게시하려는 채널에 자산/구성 요소를 추가할 수 있습니다.

1. 왼쪽 창에서 자산을 끌어다 놓고 편집기에 추가합니다.

   ![](/help/screens-cloud/assets/create-content/edit-channel2.png)

   >[!NOTE]
   >클릭 **미리 보기** 채널의 컨텐츠를 미리 보려면
   >![](/help/screens-cloud/assets/create-content/edit-channelpreview.png)

## 만들기 마법사에서 사용 가능한 템플릿 {#available-templates}

다음 템플릿은 **만들기** 채널 마법사:

| 사용 가능한 템플릿 | 설명 |
|--- |--- |
| 채널 폴더 | 채널 컬렉션을 저장할 폴더를 만들 수 있습니다. |
| 시퀀스 채널 | 구성 요소를 순차적으로 재생하는 채널을 만들 수 있습니다(슬라이드 쇼에서 하나씩). |
| 왼쪽 또는 오른쪽 L-바 분할 화면 채널 | 컨텐츠 작성자가 적절한 크기의 영역에서 다양한 유형의 자산을 볼 수 있도록 해줍니다. |

## 채널에 대해 기본 지정 세부 정보 사용 {#default-channels}

이 기능을 사용하면 채널에 대한 기본 활성화 일정을 정의하고 디스플레이에 대한 모든 지정에 대해 기본적으로 사용할 수 있습니다. 이 옵션은 번거로운 일정 정의를 반복할 필요가 없도록 메서드를 제공합니다.

### 채널에 대한 기본 할당 세부 정보 만들기 {#create-default}

1. 구성할 채널에 대한 세부 사항 페이지로 이동합니다.
1. 을(를) 찾습니다 **기본 할당 세부 정보** 타일을 만들 수 있습니다.

   ![이미지](/help/screens-cloud/assets/display/Assignment1.png)

1. 클릭 **기본 세부 정보 설정**.
1. 채널에 대한 반복 패턴과 우선 순위, 시작 및 종료 날짜를 포함한 기본 할당 세부 사항을 구성하고 **지정**.

   ![이미지](/help/screens-cloud/assets/display/Assignments2.png)

1. 지정 세부 사항은 **기본 할당 세부 정보** 타일:

   ![이미지](/help/screens-cloud/assets/display/Assignments3.png)

이 타일에는 다음 정보가 표시됩니다.
* 디스플레이에 있는 채널의 기본 우선 순위입니다.
* 채널이 재생되도록 예약된 활성화 시작 및 종료 날짜입니다.
* 반복에 대한 합성 보기(시간별/일별/주별/월별/연간 및 해당 반복에 지정된 이름).

### 디스플레이에 지정할 때 기본 지정 상세내역을 사용합니다 {#default-display}

기본 할당 세부 정보가 있는 채널에는 일반 채널이 표시되는 것과 동일한 방식을 표시하도록 지정할 수 있으며, 매번 사용자 지정 채널을 수동으로 정의하는 대신 기본 지정 세부 정보를 활용하는 옵션이 추가되었습니다.

1. 채널을 지정할 디스플레이 세부 정보 페이지로 이동하여 **채널 할당**.
또는, 재고 뷰에서 원하는 디스플레이를 선택하고 **채널 할당**.
1. 채널 지정 대화 상자가 열립니다.

   ![이미지](/help/screens-cloud/assets/display/Assignments4.png)

1. 채널 선택기에서 기본 할당 세부 정보가 있는 원하는 채널을 선택합니다.
1. 채널 지정 대화 상자가 변경되어 기본 할당 세부 정보를 선택하거나 사용자 지정 지정 세부 사항을 선택할 수 있습니다.

   ![이미지](/help/screens-cloud/assets/display/Assignments5.png)

1. 클릭 **지정** 할당을 완료하려면 **사용자 지정 할당 세부 정보 설정** 해당 특정 디스플레이 컨텍스트에서 일부 다른 값으로 기본값을 재정의하려는 경우

   ![이미지](/help/screens-cloud/assets/display/Assignments6.png)

1. 다음 사항에 주의하십시오. **지정된 채널** 타일이 새 할당으로 업데이트됩니다.

   ![이미지](/help/screens-cloud/assets/display/Assignments7.png)

1. 채널에는 사용자 지정 예약(시계 아이콘)을 사용하는지 또는 기본 세부 사항을 상속하는지(세계 시계 아이콘)에 따라 다른 아이콘이 표시되고, 이를 클릭하면 예약 세부 사항이 표시됩니다.
1. 또한 각 유형에 사용할 수 있는 작업이 다릅니다.

   ![이미지](/help/screens-cloud/assets/display/Assignments8.png)

**참고:** 기본 할당 세부 정보를 활용하는 채널 할당은 디스플레이 컨텍스트에서 편집할 수 없습니다.

* 사용자 지정 할당으로 변경해야 하는 경우, 먼저 사용자 지정을 제거한 다음 을 사용하여 다시 추가해야 합니다. **사용자 지정 할당 세부 정보 설정** 선택 사항입니다.
* 기본 할당 세부 정보의 속성을 변경해야 하는 경우 채널 세부 정보 페이지에서 직접 이 작업을 수행해야 합니다.

### 채널에서 기본 할당 세부 정보 제거 {#remove-display}

1. 기본 지정 세부 정보를 제거할 채널에 대한 세부 정보 페이지로 이동합니다.
1. 을(를) 찾습니다 **기본 할당 세부 정보** 페이지의 타일
1. 을(를) 클릭합니다. **기본값 제거**.

   ![이미지](/help/screens-cloud/assets/display/Assignments9.png)

1. 확인 대화 상자가 표시되고 세부 사항이 다음 조건 중 하나와 일치합니다.
   **a.** 채널은 어떤 표시에서도 사용되지 않습니다.

   ![이미지](/help/screens-cloud/assets/display/Assignments10.png)

**나.** 채널은 단일 디스플레이에서 사용됩니다.

![이미지](/help/screens-cloud/assets/display/Assignment11.png)

**c.** 채널은 여러 디스플레이에서 사용됩니다.

![이미지](/help/screens-cloud/assets/display/Assignments12.png)

1. 을(를) 클릭합니다. *제거* 변경 내용의 유효성을 검사하려면

**참고:** 채널에서 기본 할당 세부 정보를 제거하면 해당 정보를 사용하고 있는 모든 디스플레이에서 일치하는 할당이 제거됩니다.
따라서 해당 디스플레이에서 재생할 대체 컨텐츠가 없는 경우 빈 화면이 나타날 수 있습니다.

## 다음은 무엇입니까? {#whats-next}

이제 프로젝트에서 AEM Screens 채널을 설정했으므로 채널을 게시해야 합니다. 을(를) 참조하십시오. [화면에서 채널 게시 as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/screens-as-cloud-service/create-content/manage-publish.html?lang=en) screens 서비스 공급자에서 플레이어를 관리하기 전에
