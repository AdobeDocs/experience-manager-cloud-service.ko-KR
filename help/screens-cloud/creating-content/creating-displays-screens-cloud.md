---
title: 화면에서 디스플레이 생성 및 관리 as a Cloud Service
description: 이 페이지에서는 Screens에서 디스플레이를 만들고 관리하는 방법을 as a Cloud Service으로 설명합니다.
exl-id: 0f9faa4b-b50e-40f8-a8ed-280f8bd0a9b8
source-git-commit: 9e0ab778e97658bc8d7669b1f582f3bcddd47915
workflow-type: tm+mt
source-wordcount: '668'
ht-degree: 8%

---

# 화면에서 디스플레이 생성 및 관리 as a Cloud Service {#create-displays-screens-cloud}

채널을 게시했으면 이제 스크린 서비스 공급자에서 디스플레이를 만들 차례입니다.

디스플레이는 일반적으로 서로 옆에 배치된 화면의 가상 그룹입니다. 일반적으로 디스플레이는 설치와 관련하여 영구적이며 컨텐츠 작성자가 물리적으로 대응하는 부분이 아닌 논리적 디스플레이로서 작업에 사용하고 항상 참조하는 개체입니다.

## 목표 {#objective}

이 문서는 Screens 서비스 공급자에서 디스플레이를 만들고 관리하는 방법을 이해하는 데 도움이 됩니다. 문서를 읽고 나면

* 디스플레이를 만들고 삭제하는 방법을 이해합니다
* 디스플레이를 폴더로 구성하는 방법을 이해합니다

## 디스플레이 생성 단계 {#create-display}

Screens 서비스 공급자에서 디스플레이를 생성하려면 아래 절차를 따르십시오.

1. AEM Cloud Service 인스턴스에서 Screens 서비스 공급자로 이동합니다.
1. 선택 **표시** 왼쪽 탐색 패널에서 을(를) 클릭하고 **만들기** 화면 오른쪽 상단 모서리에서 을(를) 클릭합니다.

   ![이미지](/help/screens-cloud/assets/display/disp-1.png)

1. 선택 **표시** 작업 표시줄.

   ![이미지](/help/screens-cloud/assets/display/disp-2.png)

1. 제목으로 을 입력합니다. **LoopingChannelDisplay** in **표시 이름** 을(를) 클릭합니다. **만들기**.

   ![이미지](/help/screens-cloud/assets/display/disp3.png)

1. 다음으로 제목이 있는 표시 **LoopingChannelDisplay** 이제 표시 목록에 표시됩니다.

   ![이미지](/help/screens-cloud/assets/display/disp-4.png)

### 표시 삭제 {#deleting-display}

스크린 서비스 공급자에서 디스플레이를 삭제할 수 있습니다.

디스플레이를 선택하고 을(를) 클릭합니다 **삭제** 아래 그림과 같이 패널 아래쪽에서 확인하십시오.

![이미지](/help/screens-cloud/assets/display/disp-5.png)

## 디스플레이를 폴더로 구성하는 단계 {#organize-display}

## 폴더 레일을 전환하는 방법 {#toggle-rail}

폴더 레일이 모든 폴더를 특정 폴더로 표시하지 않도록 전환할 수 있습니다.

1. 아래에 강조 표시된 버튼을 클릭하여 표시된 인벤토리 보기로 이동합니다.

   ![이미지](/help/screens-cloud/assets/display/display-inventory.png)

1. 폴더 사이드 레일이 표시됩니다.

   ![이미지](/help/screens-cloud/assets/display/toggle-rail.png)

1. 선택 **폴더 숨기기** 다시 닫으려고 했습니다.

## 새 폴더를 만드는 방법 {#create-folder}

폴더를 만들어 디스플레이를 보다 잘 구성할 수 있습니다.

1. 디스플레이 인벤토리 보기로 이동합니다.
1. 현재 폴더에 없는지 확인합니다. 다음 내용이 표시됩니다.

   ![이미지](/help/screens-cloud/assets/display/verify-view.png)

   참고: **모든 표시** 폴더 측 레일에서 를 선택해야 하며 탐색 표시 탐색은 만 표시됩니다 **표시**.

1. 오른쪽 상단에 있는 &quot;만들기&quot; 단추를 클릭하고 **폴더** 선택 사항입니다.

   ![이미지](/help/screens-cloud/assets/display/Createfolder.png)

1. 새 폴더의 제목을 입력하고 **만들기**.

   ![이미지](/help/screens-cloud/assets/display/Createfolder2.png)

## 중첩된 새 폴더를 만드는 방법 {#nested-folder}

1. 디스플레이 인벤토리 보기로 이동합니다.

1. 폴더 측 레일에서 또는 인벤토리 보기에서 원하는 상위 폴더를 선택합니다.
1. 원하는 상위 폴더가 선택되어 있는지 확인합니다.

   ![이미지](/help/screens-cloud/assets/display/Nestedview.png)

   * 폴더 사이드 레일에서 폴더를 선택해야 합니다.
   * 탐색 표시 탐색에는 다음 옆에 현재 폴더 이름이 표시됩니다 **표시**.

1. 클릭  **만들기**  오른쪽 상단에서 을(를) 선택하고 **폴더** 선택 사항입니다.

   ![이미지](/help/screens-cloud/assets/display/Createfolder.png)

1. 새 폴더의 제목을 입력하고 **만들기**.

   ![이미지](/help/screens-cloud/assets/display/Createfolder2.png)

## 컨텐츠를 새 폴더로 이동하는 방법 {#move-folder}

컨텐츠를 새 폴더로 이동하여 디스플레이를 더 잘 구성할 수 있습니다.

1. 디스플레이 인벤토리 보기로 이동합니다.

1. 폴더 측 레일에서 또는 인벤토리 보기에서 선택하여 원하는 상위 폴더를 선택합니다.

1. 원하는 상위 폴더를 선택했는지 확인합니다.

![이미지](/help/screens-cloud/assets/display/movetofolder.png)

**참고**: 폴더 사이드 레일에서 폴더를 선택해야 합니다. 또한 탐색 표시 탐색에는 다음 옆에 현재 폴더 이름이 표시됩니다 **표시**.

## 폴더에서 컨텐츠를 삭제하는 방법 {#delete-folder}

모든 폴더 작업은 인벤토리 보기의 선택 작업 표시줄을 통해 액세스할 수 있습니다.

1. 상위 폴더로 이동하거나 사이드 레일에서 선택합니다.

1. 인벤토리 보기에서 삭제할 하위 폴더를 선택하고 비어 있는지 확인합니다.

1. 을(를) 클릭합니다. **삭제** 작업 표시줄에서 작업을 수행합니다. 폴더가 비어 있지 않으면 작업이 비활성화됩니다.


## 다음 단계 {#whats-next}

이제 프로젝트용 디스플레이를 만들고 관리하는 방법을 배웠으므로, 다음 번에 문서를 검토하여 Screens as a Cloud Service 여정을 계속해야 합니다 [화면의 디스플레이에 채널 as a Cloud Service 할당](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/screens-as-cloud-service/create-content/assigning-channels-to-display.html?lang=en).
