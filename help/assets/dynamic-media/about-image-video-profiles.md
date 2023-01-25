---
title: Dynamic Media 이미지 프로필 및 비디오 프로필 정보
description: 이미지 프로필 또는 비디오 프로필은 폴더에 업로드하는 자산에 적용할 옵션에 대한 레서피입니다. 예를 들어 업로드하는 Dynamic Media 비디오 자산에 적용할 비디오 인코딩을 지정할 수 있습니다. 또는 Dynamic Media 이미지 자산에 적용할 이미지 프로필로 제대로 잘립니다.
feature: Asset Management,Image Profiles,Video Profiles
role: Admin,User
exl-id: 8c8f0a57-13f5-4903-8d76-bfb6ee83323c
source-git-commit: 419ec6604ee8c93510cb8bf4e1d46bc9b9c9383a
workflow-type: tm+mt
source-wordcount: '1376'
ht-degree: 0%

---

# Dynamic Media 이미지 프로필 및 비디오 프로필 정보{#about-dm-image-video-profiles}

이미지 프로필 또는 비디오 프로필 은 폴더에 업로드하는 자산에 적용할 옵션을 만드는 레서피입니다. 예를 들어 업로드하는 Dynamic Media 비디오 자산에 적용할 비디오 인코딩을 지정할 수 있습니다. 또는 Dynamic Media 이미지 자산에 적용할 이미지 프로필로 제대로 잘립니다.

Dynamic Media에서 다음 링크에서 자세히 다룹니다. 두 가지 유형의 프로필을 만들 수 있습니다.

* [Dynamic Media 이미지 프로필](/help/assets/dynamic-media/image-profiles.md)
* [Dynamic Media 비디오 프로필](/help/assets/dynamic-media/video-profiles.md)

참조 - [메타데이터 프로필](/help/assets/metadata-profiles.md).

Dynamic Media 이미지 프로필 또는 Dynamic Media 비디오 프로필을 만들고, 편집하고, 삭제하려면 관리자 권한이 있어야 합니다.

이미지 프로필 또는 비디오 프로필을 만든 후 새로 업로드한 Dynamic Media 자산에 사용하는 하나 이상의 폴더에 할당합니다.

참조 - [처리 프로필 사용을 위한 디지털 자산 구성 우수 사례](/help/assets/organize-assets.md).


>[!NOTE]
>
>한 폴더에서 다른 폴더로 이동하는 자산은 다시 처리되지 않습니다. 예를 들어, 프로파일 A가 지정된 폴더 1과 프로파일 B가 지정된 폴더 2가 있다고 가정합니다. 자산을 폴더 1에서 폴더 2로 이동하는 경우, 이동된 자산은 폴더 1의 원래 처리를 유지합니다.
>
>동일한 프로필이 할당된 두 폴더 간에 자산을 이동하는 경우에도 마찬가지입니다.

## 폴더에서 Dynamic Media 자산 재처리 {#reprocessing-assets}

기존 Dynamic Media 이미지 프로필 또는 나중에 변경한 Dynamic Media 비디오 프로필이 이미 있는 폴더에서 자산을 재처리할 수 있습니다.

예를 들어 Dynamic Media 이미지 프로필을 만들어 폴더에 할당했다고 가정합니다. 폴더에 업로드한 모든 이미지 자산에는 자동으로 이미지 프로필이 자산에 적용되었습니다. 하지만 나중에 이미지 프로필에 새로운 스마트 자르기 비율을 추가하기로 합니다. 이제 자산을 선택하고 다시 폴더에 업로드하지 않고, *Scene7: 자산 재처리* 워크플로우.

처음으로 처리가 실패한 자산에서 재처리 워크플로우를 실행할 수 있습니다. 이미지 프로필 또는 비디오 프로필을 편집하지 않았거나 이미 이미지 프로필 또는 비디오 프로필을 적용한 경우에도 언제든지 자산 폴더에서 재처리 워크플로우를 실행할 수 있습니다.

선택적으로 재처리 워크플로우의 배치 크기를 최대 1000개의 자산인 기본값 50개에서 조정할 수 있습니다. 를 실행할 때 _Scene7: 자산 재처리_ 폴더의 워크플로우에서 자산이 일괄적으로 그룹화된 다음 처리를 위해 Dynamic Media 서버로 전송됩니다. 처리 후, 전체 배치 세트에 있는 각 자산의 메타데이터가 다음에 대해 업데이트됩니다 [!DNL Adobe Experience Manager]. 일괄 처리 크기가 큰 경우 처리가 지연될 수 있습니다. 또는 일괄 처리 크기가 너무 작으면 Dynamic Media 서버로 너무 많은 왕복 이동이 발생할 수 있습니다.

자세한 내용은 [재처리 워크플로우의 일괄 처리 크기 조정](#adjusting-load).

>[!NOTE]
>
>Dynamic Media Classic에서 로 자산의 벌크 마이그레이션을 수행하는 경우 [!DNL Experience Manager]Dynamic Media 서버에서 마이그레이션 복제 에이전트를 활성화합니다. 마이그레이션이 완료되면 에이전트를 비활성화해야 합니다.
>
>Dynamic Media 서버에서 마이그레이션 게시 에이전트를 비활성화해야 재처리 워크플로우가 예상대로 작동합니다.

<!-- LEAVE IN PLACE, MAY BE USED IN THE FUTURE

Batch size is the number of assets that are amalgamated into a single IPS (Dynamic Media's Image Production System) job. When you run the Scene7: Reprocess Assets workflow, the job is triggered on IPS. The number of IPS jobs that are triggered is based on the total number of assets in the folder, divided by the batch size. For example, suppose you had a folder with 150 assets and a batch size of 50. In this case, three IPS jobs are triggered. The assets are updated when the entire batch size (50 in our example) is processed in IPS. The job then moves onto the next IPS job and so on until complete. If you increase the batch size, you may notice a longer delay with assets getting updated. 

-->

**폴더에서 Dynamic Media 자산을 재처리하려면 다음을 수행하십시오.**

1. in [!DNL Experience Manager], 자산 페이지에서 이미지 프로필 또는 비디오 프로필이 할당된 자산 폴더로 이동하고 **Scene7: 자산 재처리** 워크플로우.

   이미지 프로필 또는 비디오 프로필이 할당된 폴더가 있는 폴더는 카드 보기에서 폴더 이름 바로 아래에 표시됩니다.

1. 폴더를 선택합니다.

   * 워크플로우는 선택한 폴더의 모든 파일을 재귀적으로 고려합니다.
   * 기본 선택한 폴더에 자산이 있는 하위 폴더가 하나 이상 있는 경우 워크플로우는 폴더 계층 구조의 모든 자산을 재처리합니다.
   * 자산이 1,000개 이상인 폴더 계층 구조에서 이 워크플로우를 실행하지 않는 것이 좋습니다.

1. 페이지의 왼쪽 위 모서리 근처에 있는 드롭다운 목록에서 을(를) 선택합니다 **[!UICONTROL 타임라인]**.
1. 페이지의 왼쪽 아래 모서리, 페이지의 오른쪽 [!UICONTROL 댓글] 필드에서 캐럿 아이콘( **^** ).

   ![선택한 자산 폴더, 강조 표시된 타임라인 드롭다운 목록, 강조 표시된 워크플로우 시작 단추 및 주석 필드 오른쪽에 있는 캐럿 아이콘을 보여주는 Experience Manager의 자산 스크린샷도 강조 표시되어 있습니다.](/help/assets/dynamic-media/assets/reprocess-assets1.png)

1. 선택 **[!UICONTROL 워크플로우 시작]**.
1. 에서 **[!UICONTROL 워크플로우 시작]** 드롭다운 목록에서 **[!UICONTROL Scene7: 자산 재처리]**.
1. (선택 사항)에서 **워크플로우의 제목 입력** 텍스트 필드에서 워크플로우의 이름을 입력합니다. 필요한 경우 이름을 사용하여 워크플로우 인스턴스를 참조할 수 있습니다.

   ![&quot;Scene7: 워크플로우 시작 드롭다운 목록에서 선택한 &quot;자산 재처리&quot;와 강조 표시된 시작 단추가 강조 표시되어 있습니다.](/help/assets/dynamic-media/assets/reprocess-assets2.png)

1. 선택 **[!UICONTROL 시작]**&#x200B;를 선택하고 을 선택합니다. **[!UICONTROL 확인]**.

   워크플로우를 모니터링하거나 진행 상황을 확인하려면 [!DNL Experience Manager] 기본 콘솔 페이지에서 다음을 선택합니다. **[!UICONTROL 도구 > 워크플로우]**. 워크플로우 인스턴스 페이지에서 워크플로우를 선택합니다. 메뉴 모음에서 를 선택합니다 **[!UICONTROL 기록 열기]**. 동일한 [워크플로우 인스턴스] 페이지에서 선택한 워크플로우를 종료, 일시 중단 또는 이름을 변경할 수도 있습니다.

### 재처리 워크플로우의 일괄 처리 크기 조정(선택 사항) {#adjusting-load}

(선택 사항) 재처리 워크플로우의 기본 배치 크기는 작업당 50개의 자산입니다. 이 최적 배치 크기는 재처리가 실행되는 평균 자산 크기 및 MIME 유형의 자산에 의해 제어됩니다. 값이 높을수록 하나의 재처리 작업에 많은 파일이 있습니다. 따라서 처리 배너는 계속 켜져 있습니다 [!DNL Experience Manager] 자산을 더 오랫동안 사용할 수 있도록 해줍니다. 그러나 평균 파일 크기가 1MB 이하인 경우 값을 여러 개의 100으로 늘릴 것을 권장하지만 1000을 넘지 않습니다. 평균 파일 크기가 수백 MB인 경우 배치 크기를 최대 10개까지 줄이는 것이 좋습니다.

**재처리 워크플로우의 배치 크기를 선택적으로 조정하려면**

1. in [!DNL Experience Manager], 선택 **[!UICONTROL Adobe Experience Manager]** 전역 탐색 콘솔에 액세스하려면 **[!UICONTROL 도구]** (망치) 아이콘 > **[!UICONTROL Workflow > 모델]**.
1. 워크플로우 모델 페이지의 카드 보기 또는 목록 보기에서 을 선택합니다 **[!UICONTROL Scene7: 자산 재처리]**.

   ![&quot;Scene7: Experience Manager의 카드 보기에서 선택한 자산 재처리 워크플로우입니다.](/help/assets/dynamic-media/assets/reprocess-assets7.png)

1. 도구 모음에서 를 선택합니다 **[!UICONTROL 편집]**. 새 브라우저 탭에서 Scene7을 엽니다. 자산 워크플로우 모델 페이지를 재처리합니다.
1. Scene7에서: 오른쪽 상단 모서리 근처에 있는 자산 워크플로우 페이지 재처리를 선택합니다. **[!UICONTROL 편집]** 워크플로우 &quot;잠금 해제&quot;하기.
1. 워크플로우에서 Scene7 일괄 업로드 구성 요소를 선택하여 도구 모음을 열고 을 선택합니다 **[!UICONTROL 구성]** 클릭합니다.

   ![&quot;Scene7: &quot;구성&quot; 아이콘 위로 마우스 포인터를 가져가면 자산 재처리&quot; 페이지가 표시됩니다.](/help/assets/dynamic-media/assets/reprocess-assets8.png)

1. 설정 **[!UICONTROL Scene7에 일괄 업로드 - 단계 속성]** 대화 상자에서 다음을 설정합니다.
   * 에서 **[!UICONTROL 제목]** 및 **[!UICONTROL 설명]** 텍스트 필드에 작업의 새 제목과 설명을 입력합니다(원하는 경우).
   * 선택 **[!UICONTROL 핸들러 고급]** 처리기가 다음 단계로 이동하는 경우
   * 에서 **[!UICONTROL 시간 초과]** 필드에서 외부 프로세스 시간 초과(초)를 입력합니다.
   * 에서 **[!UICONTROL 기간]** 필드에 외부 프로세스 완료를 테스트할 폴링 간격(초)을 입력합니다.
   * 에서 **[!UICONTROL 배치 필드]**&#x200B;를 Dynamic Media 서버 일괄 처리 업로드 작업에서 처리할 최대 자산 수(50~1000)를 입력합니다.
   * 선택 **[!UICONTROL 시간 제한 시 고급]** 시간 초과에 도달했을 때 진행하려는 경우 시간 초과에 도달하면 받은 편지함으로 계속 진행하려면 선택 취소합니다.

   ![Scene7에 일괄 업로드 - 단계 속성 페이지의 스크린샷입니다.](/help/assets/dynamic-media/assets/reprocess-assets3.png)

1. 의 오른쪽 위 모서리에서 **[!UICONTROL Scene7에 일괄 업로드 - 단계 속성]** 대화 상자, 선택 **[!UICONTROL 완료]**.

1. Scene7의 오른쪽 위 모서리: 자산 워크플로우 모델 페이지를 재처리하고 을 선택합니다. **[!UICONTROL 동기화]**. 다음에 **[!UICONTROL 동기화됨]**&#x200B;를 설정하는 경우 워크플로우 런타임 모델이 성공적으로 동기화되어 폴더의 자산을 재처리할 준비가 되었습니다.

   ![선택한 자산 폴더, 강조 표시된 타임라인 드롭다운 목록, 강조 표시된 워크플로우 시작 단추 및 주석 필드 오른쪽에 있는 캐럿 아이콘을 보여주는 Experience Manager의 자산 스크린샷도 강조 표시되어 있습니다.](/help/assets/dynamic-media/assets/reprocess-assets1.png)

1. Scene7을 표시하는 브라우저 탭을 닫습니다. 자산 워크플로우 모델을 재처리합니다.

<!-- MAY BE NEEDED IN THE FUTURE

1. Return to the browser tab that has the open Workflow Models page, then press **Esc** to exit the selection.
1. In the upper-left corner of the page, select **[!UICONTROL Adobe Experience Manager]** to access the global navigation console, then select the **[!UICONTROL Tools]** (hammer) icon > **[!UICONTROL General > CRXDE Lite]**.
1. In the folder tree on the left side of the CRXDE Lite page, navigate to the following location:

   `/conf/global/settings/workflow/models/scene7_reprocess_assets/jcr:content/flow/reprocess/metaData`

   ![CRXDE Lite](/help/security/assets/workflow-models9.png)

1. On the right side of the CRXDE Lite page, in the lower portion, enter the following name, type, and value in its respective field:
    * **[!UICONTROL Name]**: `reprocess-batch-size`
    * **[!UICONTROL Type]**: `Long`
    * **[!UICONTROL Value]**: enter a default value (50-1000) for the batch size
1. In the lower-right corner, select **[!UICONTROL Add]**. The new property appears as the following:

    ![Saving the new property](/help/security/assets/workflow-models10.png)

1. On the menu bar of the CRXDE Lite page, select **[!UICONTROL Save All]**.
1. In the upper-left corner of the page, select **[!UICONTROL CRXDE Lite]** to return to the main Experience Manager console
1. Repeat steps 1-7 to re-synchronize the new batch size to the Scene7: Reprocess Assets workflow model.

-->
