---
title: Screens에서 as a Cloud Service 채널 만들기 및 관리
description: 이 페이지에서는 Screens에서 채널을 as a Cloud Service으로 만들고 관리하는 방법을 설명합니다.
exl-id: 3b0bae7a-4a45-485a-ab04-604510ff6578
source-git-commit: a3e79441d46fa961fcd05ea54e84957754890d69
workflow-type: tm+mt
source-wordcount: '1087'
ht-degree: 2%

---

# Screens에서 채널 만들기 및 as a Cloud Service 관리 {#creating-channels-screens-cloud}

AEM Screens 프로젝트를 만든 후에는 채널을 만들어야 합니다.
***채널***&#x200B;에 컨텐츠 시퀀스(이미지 및 비디오), 웹 사이트 또는 단일 페이지 애플리케이션을 표시하십시오.

## 목표 {#objective}

이 문서는 Screens Content Provider에서 AEM Screens 프로젝트에 대한 채널을 만들고 관리하는 방법을 이해하는 데 도움이 됩니다. 문서를 읽고 나면 다음과 같은 작업을 수행할 수 있습니다.

* screens Content Provider에 채널을 만드는 방법을 이해할 수 있습니다.
* 채널에서 콘텐츠 관리 및 편집
* 채널의 활성화 일정

## as a Cloud Service Screens에서 새 시퀀스 채널을 만드는 단계 {#create-new-channel}

>[!NOTE]
>**전제 조건**
>안내서의 이 섹션을 시작하기 전에 다음을 검토하십시오. [Screens에서 프로젝트 생성 및 관리 as a Cloud Service](/help/screens-cloud/creating-content/creating-projects-screens-cloud.md).

아래 단계에 따라 Screens as a Cloud Service으로 새 시퀀스 채널을 만드십시오.

1. Screens 콘텐츠 공급자로 이동합니다.

1. 다음과 같이 AEM Screens 프로젝트로 이동합니다. *FirstDigitalExperience*.

1. 다음 항목 선택 **채널** 프로젝트의 폴더(예: ) **FirstDigitalExperience** —> **채널** 및 클릭 **만들기** 작업 표시줄에서

   ![channel-create1](/help/screens-cloud/assets/create-content/channel-create1.png)

1. 다음과 같은 템플릿을 선택합니다. **시퀀스 채널** 다음에서 **만들기** 마법사 및 클릭 **다음**.

   ![channel-create2](/help/screens-cloud/assets/create-content/channel-create2.png)

   >[!NOTE]
   > 다음 **만들기** 마법사는 채널을 만드는 동안 다양한 유형의 템플릿을 제공합니다. 다음을 참조하십시오 [사용 가능한 템플릿](#available-templates) 자세한 내용은 만들기 마법사를 참조하십시오.

1. 시퀀스 채널의 이름을 입력합니다(예: ). **루프채널** 및 클릭 **만들기**.

   ![channel-create3](/help/screens-cloud/assets/create-content/channel-create3.png)

   이제 다음이 표시됩니다. **루프채널** AEM Screens 을 참조하십시오.

   채널을 만들면 이제 채널에 컨텐츠를 추가할 수 있습니다. 다음을 참조하십시오 [채널에 콘텐츠 추가](#add-content) 채널에 에셋(이미지/비디오)을 추가하는 방법을 알아봅니다.

## 채널 관리 {#managing-channels}

채널을 편집하고, 등록 정보와 대시보드를 보고, 복사하고, 미리 보고, 삭제할 수 있습니다.

아래 그림과 같이 프로젝트에서 채널로 이동하고 채널을 선택합니다. 이제 채널 편집, 속성 보기, 콘텐츠 미리 보기, 게시 관리 또는 작업 표시줄에서 채널 삭제와 같은 옵션을 선택할 수 있습니다.

![channelprop1](/help/screens-cloud/assets/create-content/channelprop1.png)

### 채널에 콘텐츠 추가 {#add-content}

채널에서 컨텐츠를 추가하거나 편집하려면 아래 단계를 따르십시오.

1. 아래 그림과 같이 편집할 채널을 선택합니다. 클릭 **편집** 작업 표시줄의 왼쪽 상단 모서리에서 편집기를 엽니다.

   ![edit-channel1](/help/screens-cloud/assets/create-content/edit-channel1.png)

1. 편집기를 사용하면 게시할 채널에 에셋/구성 요소를 추가할 수 있습니다.

1. 왼쪽 창에서 에셋을 끌어다 놓고 편집기에 추가합니다.

   ![edit-channel2](/help/screens-cloud/assets/create-content/edit-channel2.png)

   >[!NOTE]
   >클릭 **미리 보기** 을 클릭하여 채널의 콘텐츠를 미리 봅니다.
   >![편집-채널 미리 보기](/help/screens-cloud/assets/create-content/edit-channelpreview.png)

## 만들기 마법사에서 사용할 수 있는 템플릿 {#available-templates}

다음 템플릿은 를 사용하는 동안 사용할 수 있습니다. **만들기** 채널 마법사:

| 사용 가능한 템플릿 | 설명 |
|--- |--- |
| 채널 폴더 | 채널 컬렉션을 저장할 폴더를 만들 수 있습니다. |
| 시퀀스 채널 | 슬라이드 쇼에서 하나씩 구성 요소를 순차적으로 재생하는 채널을 만들 수 있습니다. |
| 왼쪽 또는 오른쪽 L-표시줄 분할 화면 채널 | 콘텐츠 작성자는 적절한 크기의 영역에서 다양한 유형의 에셋을 볼 수 있습니다. |

## 채널에 대한 기본 할당 세부 정보 사용 {#default-channels}

이 기능을 사용하면 채널에 대한 기본 활성화 일정을 정의하고 표시에 대한 모든 할당에 대해 기본적으로 사용할 수 있습니다. 이는 번거로운 스케줄 정의를 반복할 필요가 없도록 하는 방법을 제공한다.

### 채널에 대한 기본 할당 세부 정보 만들기 {#create-default}

1. 구성할 채널의 세부 정보 페이지로 이동합니다.
1. 를 찾습니다. **기본 할당 세부 정보** 페이지에 타일을 표시합니다.

   ![이미지](/help/screens-cloud/assets/display/Assignment1.png)

1. 클릭 **기본 세부 정보 설정**.
1. 우선 순위, 시작 및 종료 날짜, 채널에 대한 반복 패턴을 포함한 기본 할당 세부 정보를 구성하고 **할당**.

   ![이미지](/help/screens-cloud/assets/display/Assignments2.png)

1. 지정에 대한 세부 사항은 다음에 표시됩니다. **기본 할당 세부 정보** 타일:

   ![이미지](/help/screens-cloud/assets/display/Assignments3.png)

이 타일에는 다음 정보가 표시됩니다.
* 디스플레이에서 채널의 기본 우선 순위입니다.
* 채널 재생이 예정된 활성화 시작 및 종료 날짜입니다.
* 반복에 대한 합성 보기(시간별/일별/주별/월별/연간 및 해당 반복에 제공된 이름).

### 디스플레이에 할당할 때 기본 할당 세부 정보 사용 {#default-display}

기본 할당 세부 정보가 있는 채널을에 할당하면 일반 채널과 동일한 방식으로 표시할 수 있으며, 매번 사용자 지정 세부 정보를 수동으로 정의하는 대신 기본 할당 세부 정보를 사용하는 옵션이 추가되었습니다.

1. 채널을 지정할 디스플레이 세부 정보 페이지로 이동하고 **채널 할당**.
또는 재고 보기에서 원하는 디스플레이를 선택하고 **채널 할당**.
1. 채널 할당 대화 상자가 열립니다.

   ![이미지](/help/screens-cloud/assets/display/Assignments4.png)

1. 채널 선택기에서 기본 할당 세부 정보가 있는 원하는 채널을 선택합니다.
1. 채널 할당 대화 상자 변경 사항에 주목하여 기본 할당 세부 정보를 선택하거나 사용자 지정 할당 세부 정보를 선택합니다.

   ![이미지](/help/screens-cloud/assets/display/Assignments5.png)

1. 클릭 **할당** 지정을 완료하려면 **사용자 지정 할당 세부 정보 설정** 특정 표시의 컨텍스트에서 다른 값으로 기본값을 재정의하는 것을 선호하는 경우.

   ![이미지](/help/screens-cloud/assets/display/Assignments6.png)

1. 다음 사항에 주목합니다. **할당된 채널** 타일이 새 할당으로 업데이트되었습니다.

   ![이미지](/help/screens-cloud/assets/display/Assignments7.png)

1. 채널에는 사용자 지정 예약(시계 아이콘)을 사용하는지 또는 기본 세부 정보(세계 시계 아이콘)를 상속하는지 여부에 따라 다른 아이콘이 표시되며, 해당 아이콘을 클릭하면 예약 세부 정보가 표시됩니다.
1. 또한 각 유형에 사용할 수 있는 작업이 달라집니다.

   ![이미지](/help/screens-cloud/assets/display/Assignments8.png)

**참고:** 기본 할당 세부 정보를 사용하는 채널 할당은 디스플레이 컨텍스트에서 편집할 수 없습니다.

* 사용자 지정 할당으로 변경해야 하는 경우 먼저 할당을 제거한 다음 **사용자 지정 할당 세부 정보 설정** 옵션을 선택합니다.
* 기본 할당 세부 정보의 속성을 변경해야 하는 경우 채널 세부 정보 페이지에서 바로 변경할 수 있습니다.

### 채널에서 기본 할당 세부 정보 제거 {#remove-display}

1. 기본 지정 세부 정보를 제거할 채널에 대한 세부 정보 페이지로 이동합니다.
1. 를 찾습니다. **기본 할당 세부 정보** 페이지의 타일
1. 다음을 클릭합니다. **기본값 제거**.

   ![이미지](/help/screens-cloud/assets/display/Assignments9.png)

1. 확인 대화 상자가 표시되며, 세부 사항은 다음 조건 중 하나와 일치합니다.
   **a.** 채널은 어떤 디스플레이에서도 사용되지 않습니다.

   ![이미지](/help/screens-cloud/assets/display/Assignments10.png)

**b.** 채널은 단일 디스플레이에서 사용됩니다.

![이미지](/help/screens-cloud/assets/display/Assignment11.png)

**c.** 채널은 여러 디스플레이에서 사용됩니다.

![이미지](/help/screens-cloud/assets/display/Assignments12.png)

1. 다음을 클릭합니다. *제거* 을 클릭하여 변경 내용의 유효성을 검사합니다.

**참고:** 채널에서 기본 할당 세부 정보를 제거하면 해당 할당을 사용 중이던 모든 디스플레이에서 일치하는 할당이 제거됩니다.
따라서 해당 디스플레이에서 재생할 대체 컨텐츠가 없는 경우 빈 화면이 표시될 수 있습니다.

## 다음 단계 {#whats-next}

이제 프로젝트에서 AEM Screens 채널을 설정했으므로 채널을 게시해야 합니다. 다음을 참조하십시오 [Screens에서 채널 as a Cloud Service 게시](manage-publish.md) Screens Services Provider에서 플레이어를 관리하기 전에
