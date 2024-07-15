---
title: Screensas a Cloud Service 에서 디스플레이 생성 및 관리
description: 이 페이지에서는 Screensas a Cloud Service 에서 디스플레이를 만들고 관리하는 방법에 대해 설명합니다.
exl-id: 0f9faa4b-b50e-40f8-a8ed-280f8bd0a9b8
feature: Authoring Screens
role: Admin, Developer, User
source-git-commit: f9ba9fefc61876a60567a40000ed6303740032e1
workflow-type: tm+mt
source-wordcount: '649'
ht-degree: 3%

---

# Screensas a Cloud Service 에서 디스플레이 생성 및 관리 {#create-displays-screens-cloud}

채널을 게시했으면 이제 Screens 서비스 공급자에 표시를 만들 차례입니다.

디스플레이는 일반적으로 서로 옆에 배치된 화면의 가상 그룹입니다. 디스플레이는 일반적으로 설치와 관련하여 영구적입니다. 이 개체 콘텐츠는 작성자가 실제 카운터 부분이 아닌 논리 표시로 작업하고 항상 를 참조하는 개체입니다.

## 목표 {#objective}

이 문서는 Screens 서비스 공급자에서 디스플레이를 만들고 관리하는 방법을 이해하는 데 도움이 됩니다. 문서를 읽고 나면

* 디스플레이를 만들고 삭제하는 방법을 이해합니다.
* 디스플레이를 폴더로 구성하는 방법 이해

## 디스플레이를 만드는 단계 {#create-display}

Screens 서비스 공급자에서 디스플레이를 만들려면 아래 단계를 따르십시오.

1. AEM Cloud Service 인스턴스에서 Screens 서비스 공급자로 이동합니다.
1. 왼쪽 탐색 패널에서 **디스플레이**&#x200B;를 선택하고 화면 오른쪽 상단에서 **만들기**&#x200B;를 클릭합니다.

   ![이미지](/help/screens-cloud/assets/display/disp-1.png)

1. 작업 표시줄에서 **표시**&#x200B;를 선택합니다.

   ![이미지](/help/screens-cloud/assets/display/disp-2.png)

1. 제목을 **표시 이름**&#x200B;에 **LoopingChannelDisplay**(으)로 입력하고 **만들기**&#x200B;를 클릭합니다.

   ![이미지](/help/screens-cloud/assets/display/disp3.png)

1. 제목이 **LoopingChannelDisplay**&#x200B;인 표시가 표시 목록에 표시됩니다.

   ![이미지](/help/screens-cloud/assets/display/disp-4.png)

### 디스플레이 삭제 {#deleting-display}

Screens 서비스 공급자에서 디스플레이를 삭제할 수 있습니다.

아래 그림과 같이 디스플레이를 선택하고 패널 하단에서 **삭제**&#x200B;를 클릭합니다.

![이미지](/help/screens-cloud/assets/display/disp-5.png)

## 디스플레이를 폴더로 구성하는 단계 {#organize-display}

## 폴더 레일을 전환하는 방법 {#toggle-rail}

모든 폴더가 표시되지 않던 폴더 레일을 특정 폴더로 전환할 수 있습니다.

1. 아래에 강조 표시된 버튼을 클릭하여 표시되는 인벤토리 보기로 이동합니다.

   ![이미지](/help/screens-cloud/assets/display/display-inventory.png)

1. 폴더 사이드 레일이 표시됩니다.

   ![이미지](/help/screens-cloud/assets/display/toggle-rail.png)

1. **폴더 숨기기**&#x200B;를 선택하여 다시 닫습니다.

## 폴더를 만드는 방법 {#create-folder}

폴더를 만들어 디스플레이를 더욱 효율적으로 구성할 수 있습니다.

1. 표시 재고 뷰로 이동합니다.
1. 현재 폴더에 있지 않은지 확인하려면 다음에 대한 정보가 표시됩니다.

   ![이미지](/help/screens-cloud/assets/display/verify-view.png)

   참고: **모든 표시**&#x200B;는 폴더 쪽 레일에서 선택해야 하며 탐색 표시 탐색 영역에 **표시**&#x200B;만 표시됩니다.

1. 오른쪽 상단의 &quot;만들기&quot; 단추를 클릭하고 **폴더** 옵션을 선택합니다.

   ![이미지](/help/screens-cloud/assets/display/Createfolder.png)

1. 새 폴더의 제목을 입력하고 **만들기**&#x200B;를 클릭합니다.

   ![이미지](/help/screens-cloud/assets/display/Createfolder2.png)

## 중첩 폴더를 만드는 방법 {#nested-folder}

1. 표시 재고 뷰로 이동합니다.

1. 폴더 측 레일에서 또는 인벤토리 보기에서 탐색하여 원하는 상위 폴더를 선택합니다.
1. 원하는 상위 폴더가 선택되어 있는지 확인합니다.

   ![이미지](/help/screens-cloud/assets/display/Nestedview.png)

   * 폴더는 폴더 사이드 레일에서 선택해야 합니다.
   * 이동 경로 탐색에 **표시** 옆에 현재 폴더 이름이 표시됩니다.

1. 오른쪽 상단의 **만들기**&#x200B;를 클릭하고 **폴더** 옵션을 선택합니다.

   ![이미지](/help/screens-cloud/assets/display/Createfolder.png)

1. 새 폴더의 제목을 입력하고 **만들기**&#x200B;를 클릭합니다.

   ![이미지](/help/screens-cloud/assets/display/Createfolder2.png)

## 콘텐츠를 새 폴더로 이동하는 방법 {#move-folder}

콘텐츠를 새 폴더로 이동하여 디스플레이를 보다 효율적으로 구성할 수 있습니다.

1. 표시 재고 뷰로 이동합니다.

1. 폴더 측 레일에서 또는 인벤토리 보기에서 선택하여 원하는 상위 폴더를 선택합니다.

1. 원하는 상위 폴더를 선택했는지 확인합니다.

![이미지](/help/screens-cloud/assets/display/movetofolder.png)

**참고**: 폴더는 폴더 쪽 레일에서 선택해야 합니다. 또한 이동 경로 탐색에 **표시** 옆에 현재 폴더 이름이 표시됩니다.

## 폴더에서 콘텐츠를 삭제하는 방법 {#delete-folder}

모든 폴더 작업은 인벤토리 보기의 선택 작업 표시줄을 통해 액세스할 수 있습니다.

1. 상위 폴더로 이동하거나 측면 레일에서 선택합니다.

1. 인벤토리 보기에서 삭제할 하위 폴더를 선택하고 비어 있는지 확인합니다.

1. 선택 작업 표시줄에서 **삭제** 작업을 클릭합니다. 폴더가 비어 있지 않으면 작업이 비활성화됩니다.


## 다음 단계 {#whats-next}

이제 프로젝트에 대한 디스플레이를 관리하고 만드는 방법에 대해 알아보았습니다. 다음에 [Screensas a Cloud Service 에 여정 할당](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/screens-as-cloud-service/create-content/assigning-channels-to-display.html)을 검토하여 Screens as a Cloud Service 채널을 만들고 관리하는 방법을 계속 살펴보십시오.
