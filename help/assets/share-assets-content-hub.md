---
title: ' [!DNL the Content Hub]에서 Assets 공유'
description: ' [!DNL the Content Hub]에서 Assets 공유'
role: User
exl-id: 5284d229-1596-40bf-aa5f-af4b6500ebdf
source-git-commit: a6d995eddd714c356eadc6c1b668887bdfd011cd
workflow-type: tm+mt
source-wordcount: '409'
ht-degree: 2%

---

# Content Hub에서 자산 공유 {#search-assets-as-a-link}

선택한 에셋에 대한 링크를 만들어 다른 사용자와 쉽게 공유할 수 있습니다. 승인된 [!DNL Content Hub] 사용자로서 [!DNL Content Hub] 환경에서 사용 가능한 자산을 하나 이상 선택하고 링크를 생성한 후 다른 개인 또는 공용 사용자에게 보냅니다.

## 사전 요구 사항 {#prerequisites}

[Content Hub 사용자](deploy-content-hub.md#onboard-content-hub-users)는 선택한 에셋에 대한 링크를 만들어 다른 사용자와 공유할 수 있습니다.

## 자산 공유 {#share-assets}

하나 이상의 에셋을 개인 또는 공용 사용자와 공유하려면 다음 단계를 수행하십시오.

1. [!DNL Content Hub] 홈 페이지로 이동하여 자산을 하나 이상 선택하고 ![공유](/help/assets/assets/share.svg) **[!UICONTROL 공유]**&#x200B;를 클릭하여 **[!UICONTROL 자산 공유]** 대화 상자에 선택한 단일 자산 또는 여러 자산 목록을 표시합니다.

   ![컬렉션](/help/assets/assets/Smock_Collection_18_N.svg) **[!UICONTROL 컬렉션]**&#x200B;에서 사용할 수 있는 자산을 선택하고 공유할 수도 있습니다.

1. 자산을 보거나 **[!UICONTROL 자산 공유]** 대화 상자에서 사용할 수 있는 자산 목록을 검토하십시오. 목록에서 제거하려면 자산 옆에 있는 ![선택 취소](/help/assets/assets/Close.svg)를 클릭하십시오.

1. 선택한 에셋 집합을 정의하는 제목과 선택적 설명을 지정합니다.

1. **[!UICONTROL 만료 기간]**&#x200B;을 선택합니다.

1. **[!UICONTROL 액세스할 수 있는 사용자]** 드롭다운 아래에서 액세스 옵션을 선택하고 **[!UICONTROL 링크 가져오기]**&#x200B;를 클릭하여 선택한 사용자와 공유할 링크를 생성합니다. 개인 사용자가 공유 에셋 페이지에 액세스하려면 [!DNL Content Hub] 환경에 로그인해야 합니다. 그러나 게스트로서 공용 사용자는 [!DNL Content Hub]에 로그인하지 않고 공유 에셋 페이지에 액세스할 수 있습니다.

<!--1. Select a **[!UICONTROL period of expiration]** and click **[!UICONTROL Get Link]** to generate a link to share with private users. Private users sign in to their [!DNL Content Hub] environment to access the shared assets page.-->

![비공개 및 공개 링크](/help/assets/assets/shared-link-for-assets.png)

<!--Enable the **[!UICONTROL Public Link]** toggle, select a **[!UICONTROL period of expiration]** and click **[!UICONTROL Generate Public Link]** to generate a link to share with public users. Public users, as guests, access the shared assets page without signing in to [!DNL Content Hub].-->

>[!NOTE]
> 
> [구성 페이지에서 공개 링크 공유를 사용하도록 설정](/help/assets/configure-content-hub-ui-options.md#enable-public-link-sharing)하여 **[!UICONTROL 자산 공유]** 대화 상자에서 **[!UICONTROL 공개 링크]** 토글을 표시합니다.

## 미리보기 페이지에서 에셋 공유 {#share-asset-from-preview-page}

에셋을 미리 보는 동안 공유하려면 다음 단계를 수행하십시오.

1. [!DNL Content Hub] 홈 페이지로 이동하고 자산 미리 보기를 클릭하여 자산을 미리 보고 대화 상자의 오른쪽 창에 메뉴 옵션을 표시합니다.
1. ![공유](/help/assets/assets/share.svg)를 선택하여 **[!UICONTROL 공유]** 패널을 표시합니다.
   자산을 미리 보는 동안 ![자산 공유](/help/assets/assets/share-link-asset-preview.png)
1. [자산 공유](#share-assets) 섹션의 3~5단계에 따라 이 **[!UICONTROL 공유]** 패널에서 자산 링크(비공개 또는 공개)를 생성하고 공유하십시오.

## 공유 자산에 액세스 {#access-shared-assets}

링크를 통해 공유 에셋 페이지에 액세스하고 다음을 수행합니다.

* 하나 이상의 에셋을 선택하고 ![다운로드](/help/assets/assets/download-icon.svg) **[!UICONTROL 다운로드]**&#x200B;를 클릭하여 사용 가능한 다운로드 옵션에서 **[!UICONTROL 원본]**, **[!UICONTROL 정적]** 또는 두 표현물을 모두 선택합니다.
  ![](/help/assets/assets/download-shared-assets.png)
* 에셋의 메타데이터를 보려면 에셋 썸네일을 클릭합니다.
* 공유 에셋 페이지([개인 링크를 통해 액세스](#share-assets))에서 에셋 썸네일을 클릭하고 ![다운로드](/help/assets/assets/download-icon.svg)를 선택하여 **[!UICONTROL 다운로드]** 패널에서 에셋의 사용 가능한 동적 렌디션을 선택하고 확인합니다.
  ![](/help/assets/assets/download-renditions-shared-assets-page.png)


