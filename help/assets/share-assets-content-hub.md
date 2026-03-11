---
title: ' [!DNL the Content Hub]에서 Assets 공유'
description: ' [!DNL the Content Hub]에서 Assets 공유'
role: User
badgeSaas: label="AEM Assets" type="Positive" tooltip="AEM Assets에 적용됩니다)."
exl-id: 5284d229-1596-40bf-aa5f-af4b6500ebdf
source-git-commit: 59f97fc6ded4274c27400f56b50b4a3329cc471a
workflow-type: tm+mt
source-wordcount: '931'
ht-degree: 2%

---

# Content Hub에서 자산 공유 {#search-assets-as-a-link}

선택한 에셋에 대한 링크를 만들어 다른 사용자와 쉽게 공유할 수 있습니다. 승인된 [!DNL Content Hub] 사용자로서 [!DNL Content Hub] 환경에서 사용 가능한 자산을 하나 이상 선택하고 링크를 생성한 후 다른 개인 또는 공용 사용자에게 보냅니다.

>[!VIDEO](https://video.tv.adobe.com/v/3474926/?captions=kor&learn=on&enablevpops=on){transcript=true}

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

## 자주 묻는 질문 {#faqs-share-assets-content-hub}

### AEM Assets Content Hub에서 에셋을 공유한다는 것은 무엇을 의미합니까?

AEM Assets Content Hub에서 에셋을 공유하면 인가된 사용자가 링크를 생성하여 하나 이상의 에셋 또는 전체 컬렉션을 다른 사용자와 쉽게 공유할 수 있습니다. 이 링크는 개인 사용자(로그인해야 하는 사용자) 또는 공용 사용자(게스트로 액세스할 수 있는 사용자)에게 보낼 수 있으며, 수신자에게 선택한 에셋을 보고 다운로드할 수 있는 직접 액세스 권한을 제공합니다.

### AEM Assets Content Hub을 사용하여 다른 사용자와 에셋 또는 컬렉션을 공유하려면 어떻게 해야 합니까?

AEM Assets Content Hub에서 에셋 또는 컬렉션을 공유하려면 Content Hub 홈 페이지로 이동하여 에셋을 하나 이상 선택하고(또는 컬렉션의 컬렉션 탭으로 이동) 공유 아이콘을 클릭합니다. 공유 대화 상자에서 에셋을 미리 보고, 필요한 경우 임의의 를 제거하고, 제목과 설명을 추가하고, 링크에 액세스할 수 있는 사용자(비공개 또는 공개)를 선택하고, 만료 기간을 설정한 다음 링크 가져오기 를 클릭하여 공유 가능한 URL을 생성하고 복사할 수 있습니다. 그런 다음 링크를 팀원이나 이해 당사자에게 보낼 수 있습니다.

### AEM Assets Content Hub에서 에셋을 공유할 때 사용할 수 있는 액세스 옵션은 무엇이며 어떻게 다릅니까?

Content Hub에서는 공유 링크에 대한 두 가지 액세스 옵션(개인 및 공용) 중에서 선택할 수 있습니다. 비공개 링크를 사용하려면 수신자가 Content Hub 환경에 로그인하여 에셋을 보고 다운로드해야 하므로 보안이 강화됩니다. 공개 링크는 로그인이 필요 없이 링크를 보유한 누구나 액세스할 수 있습니다. 각 링크 유형에는 공개 링크의 경우 24시간에서 1주일, 비공개 링크의 경우 사용자 정의 날짜와 같은 자체 만료 설정이 포함되어 있습니다.

### AEM Assets Content Hub의 자산에 대한 공개 링크를 생성할 수 있도록 관리자가 관리하는 구성이 있습니까?

예. 관리자는 구성 UI의 **컬렉션 및 공유** 탭에서 사용할 수 있는 **공개 링크 사용** 토글을 활성화하거나 비활성화하여 AEM Assets Content Hub의 자산에 대한 공개 링크 생성을 관리할 수 있습니다.

### AEM Assets Content Hub에서 공유 에셋 링크의 만료 날짜를 설정할 수 있습니까? 이 중요한 이유는 무엇입니까?

예. AEM Assets Content Hub에서 비공개 및 공개 공유 링크 모두에 대해 만료 날짜를 설정할 수 있습니다. 공개 링크의 경우 24시간에서 최대 1주일까지 선택할 수 있는 반면 비공개 링크의 경우 사전 설정에서 선택하거나 사용자 지정 만료 날짜를 설정할 수 있습니다. 만료 날짜가 중요한 이유는 링크가 만료되면 더 이상 에셋에 액세스하거나 다운로드하는 데 사용할 수 없으므로 콘텐츠의 보안 및 제어를 유지하는 데 도움이 되기 때문입니다.

### 수신자는 AEM Assets Content Hub을 사용하여 만든 공유 에셋 링크로 무엇을 할 수 있으며, 다양한 렌디션을 다운로드할 수 있는 옵션이 있습니까?

공유 에셋 링크를 받은 수신자는 브라우저에서 링크를 열어 제공된 에셋을 미리 보고, 선택하고, 다운로드할 수 있습니다. AEM Assets Content Hub에서 에셋 렌디션이 활성화되어 있으면 수신자는 다운로드할 렌디션(예: 원본 또는 정적)을 선택할 수 있습니다. 에셋 및 렌디션은 zip 파일로 다운로드되며 에셋 썸네일을 클릭하여 메타데이터를 볼 수 있습니다. 링크는 설정된 만료 날짜까지 작동합니다.




