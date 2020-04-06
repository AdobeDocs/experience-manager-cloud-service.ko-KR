---
title: Brand Portal에 자산, 폴더 및 컬렉션 게시
seo-title: 자산, 폴더 및 컬렉션을 브랜드 포털에 게시
description: 자산, 폴더 및 컬렉션을 Brand Portal에 게시 및 게시 취소하는 방법을 알아봅니다.
seo-description: 자산, 폴더 및 컬렉션을 Brand Portal에 게시 및 게시 취소하는 방법을 알아봅니다.
uuid: null
contentOwner: Vishabh Gupta
products: SG_EXPERIENCEMANAGER/ASSETS
topic-tags: brand-portal
content-type: reference
discoiquuid: null
translation-type: tm+mt
source-git-commit: 7e0375b6ebdf0959dbe50ad3ae2cd0b77709b4c1

---


# Publish AEM Assets to Brand Portal {#publish-aem-assets-to-brand-portal}

AEM(Adobe Experience Manager) 자산 관리자는 자산, 폴더 및 컬렉션을 AEM Assets 브랜드 포털 인스턴스에 게시할 수 있습니다. 자산 또는 폴더의 게시 워크플로우를 나중 날짜 또는 시간으로 예약할 수도 있습니다. 게시되면 브랜드 포털 사용자는 자산, 폴더 및 컬렉션을 액세스하고 다른 사용자에게 추가로 배포할 수 있습니다.

하지만 먼저 브랜드 포털에서 AEM 자산을 구성해야 합니다. 자세한 내용은 브랜드 포털에서 [AEM 자산 구성을 참조하십시오](configure-aem-assets-with-brand-portal.md).

AEM 자산에서 원본 자산, 폴더 또는 컬렉션을 이후에 수정하는 경우 AEM 자산에서 다시 게시할 때까지 변경 내용이 브랜드 포털에 반영되지 않습니다. 이 기능을 사용하면 진행 중인 변경 사항을 브랜드 포털에서 사용할 수 없습니다. 관리자가 게시한 승인된 변경 사항만 브랜드 포털에서 사용할 수 있습니다.

* [브랜드 포털에 자산 게시](#publish-assets-to-bp)
* [브랜드 포털에 폴더 게시](#publish-folders-to-brand-portal)
* [브랜드 포털에 컬렉션 게시](#publish-collections-to-brand-portal)

>[!NOTE]
>
>피크 시간이 아닌 시간에 구애받지 않고 AEM 작성자가 초과 리소스를 차지하지 않도록 시차 게시를 권장합니다.


## Publish assets to Brand Portal {#publish-assets-to-bp}

다음은 AEM 자산에서 브랜드 포털에 자산을 게시하는 단계입니다.

1. 자산 콘솔에서 상위 폴더를 열고 게시할 모든 자산을 선택하고 도구 모음에서 빠른 **[!UICONTROL 게시]** 옵션을 클릭합니다.


   ![publish2bp-2](assets/publish2bp.png)

1. 자산을 게시하는 두 가지 방법은 다음과 같습니다.
   * [지금](#publish-to-bp-now) 게시(즉시 자산 게시)
   * [나중에 게시](#publish-to-bp-now) (자산 게시 예약)

### 지금 자산 게시 {#publish-to-bp-now}

선택한 자산을 브랜드 포털에 게시하려면 다음 중 하나를 수행합니다.

* 도구 모음에서 빠른 게시를 **[!UICONTROL 선택합니다]**. 메뉴에서 브랜드 포털에 **[!UICONTROL 게시를 클릭합니다]**.

* 도구 모음에서 게시 **[!UICONTROL 관리를 선택합니다]**.

   1. 작업에서 **[!UICONTROL 브랜드 포털에]**&#x200B;게시를 **[!UICONTROL 선택하고]**&#x200B;예약 **[!UICONTROL 에서]**&#x200B;지금 게시를 ****&#x200B;선택합니다. **[!UICONTROL 다음]**&#x200B;을 클릭합니다.

   2. 범위에서 선택을 **[!UICONTROL 확인하고]**&#x200B;브랜드 포털에 **[!UICONTROL 게시를 클릭합니다]**.

에셋이 브랜드 포털에 게시하기 위해 큐에 올라가 있음을 나타내는 메시지가 나타납니다. 브랜드 포털 인터페이스에 로그인하여 게시된 자산을 확인합니다.

### 나중에 자산 게시 {#publish-to-bp-later}

Brand Portal에 자산을 나중에 게시할 수 있도록 예약하려면:

1. 게시를 예약하려는 자산을 선택하고 맨 위의 도구 **[!UICONTROL 모음에서]** 게시 관리를 선택합니다.

1. 게시 **[!UICONTROL 관리]** 페이지의 **[!UICONTROL 게시물]** **[!UICONTROL 작업]**&#x200B;중에서 브랜드 포털에 **[!UICONTROL 게시를 선택하고]** LaterLateringScheduling ****&#x200B;에서 선택합니다.

   ![publishlaberp-1](assets/publishlaterbp-1.png)

1. 활성화 **날짜를** 선택하고 시간을 지정합니다. **다음**&#x200B;을 클릭합니다.

1. 워크플로우에서 **[!UICONTROL 워크플로우 제목을]** 지정합니다 ****. 나중에 **[!UICONTROL 게시를 클릭합니다]**.

   ![게시 워크플로우](assets/publishworkflow.png)

브랜드 포털 인터페이스에 로그인하여 게시된 자산을 사용할 수 있는지 확인합니다.

![bp_landing_page](assets/bp_landing_page.png)

<!--

End - Publish assets to Brand Portal
Start- Publish folders to Brand Portal
-->


## Publish folders to Brand Portal{#publish-folders-to-brand-portal}

자산 폴더를 즉시 게시 또는 게시 취소할 수 있고 나중 날짜 또는 시간으로 예약할 수 있습니다.

### Publish folders to Brand Portal {#publish-folders-to-brand-portal-1}

1. 자산 콘솔에서 게시할 폴더를 선택하고 도구 모음에서 빠른 **[!UICONTROL 게시]** 옵션을 클릭합니다.

   ![publish2bp](assets/publish2bp.png)

1. **지금 폴더 게시**

   선택한 폴더를 브랜드 포털에 게시하려면 다음 중 하나를 수행합니다.

   * 도구 모음에서 빠른 게시를 **[!UICONTROL 선택합니다]**. 메뉴에서 브랜드 포털에 **[!UICONTROL 게시를 선택합니다]**.

   * 도구 모음에서 게시 **[!UICONTROL 관리를 선택합니다]**.

      1. 동작에서 **[!UICONTROL 브랜드]**&#x200B;포털에 **[!UICONTROL 게시를 선택합니다]**. 예약에서 **[!UICONTROL 지금]**&#x200B;을 **[!UICONTROL 선택합니다]**. **[!UICONTROL 다음]**&#x200B;을 클릭합니다.
      1. 범위에서 선택을 **[!UICONTROL 확인하고]** 브랜드 포털에 **[!UICONTROL 게시를 클릭합니다]**.
   폴더가 Brand Portal에 게시하기 위해 큐에 올라갔다는 메시지가 나타납니다. 브랜드 포털 인터페이스에 로그인하여 게시된 폴더를 확인합니다.

1. **나중에 폴더 게시**

   자산 폴더 게시를 나중 날짜 또는 시간으로 예약합니다.

   1. 게시를 예약하려는 폴더를 선택하고 맨 위의 도구 **[!UICONTROL 모음에서]** 게시 관리를 선택합니다.
   1. 작업에서 **[!UICONTROL 브랜드 포털에]**&#x200B;게시를 **[!UICONTROL 선택하고]**&#x200B;예약 **[!UICONTROL 후 선택을]** ****&#x200B;참조하십시오.

      ![publishlatebing](assets/publishlaterbp.png)

   1. 활성화 **[!UICONTROL 날짜를]** 선택하고 시간을 지정합니다. **[!UICONTROL 다음]**&#x200B;을 클릭합니다.
   1. 범위에서 선택을 **[!UICONTROL 확인합니다]**. **[!UICONTROL 다음]**&#x200B;을 클릭합니다.
   1. 워크플로우 아래에 워크플로우 제목을 **[!UICONTROL 지정합니다]**. 나중에 **[!UICONTROL 게시를 클릭합니다]**.

      ![managechedlepub](assets/manageschedulepub.png)

### Unpublish folders from Brand Portal {#unpublish-folders-from-brand-portal}

AEM Assets 인스턴스에서 게시를 취소하여 브랜드 포털에 게시된 모든 자산 폴더를 제거할 수 있습니다. 원본 폴더를 게시 취소한 후에는 해당 복사본을 더 이상 브랜드 포털 사용자가 사용할 수 없습니다.

브랜드 포털에서 자산 폴더를 즉시 게시 취소하거나 나중 날짜 및 시간으로 예약할 수 있습니다.

브랜드 포털에서 자산 폴더의 게시를 취소하려면:

1. AEM 자산 콘솔에서 게시 취소할 폴더를 선택합니다.

   ![publish2bp-1](assets/publish2bp.png)

1. 도구 모음에서 게시 **[!UICONTROL 관리를 클릭합니다]**.

1. **지금 브랜드 포털에서 게시 취소**

   브랜드 포털에서 선택한 폴더의 게시를 즉시 취소하려면:

   1. 도구 모음에서 게시 **관리를 선택합니다**.
   1. Action **에서** Brand Portal **에서 게시 취소를**&#x200B;선택하고 **Scheduling**&#x200B;에서 **지금 게시를**&#x200B;선택합니다. **다음**&#x200B;를 클릭합니다.
   1. 범위에서 선택을 확인하고 **브랜드 포털에서** 게시 **취소를 클릭합니다**.
   ![게시 취소 확인](assets/confirm-unpublish.png)

1. **나중에 브랜드 포털에서 게시 취소**

   Brand Portal에서 이후 날짜 및 시간으로 폴더 게시 취소를 예약하려면:

   1. 도구 모음에서 게시 **관리를 선택합니다**.
   1. Action **에서** Brand Portal **에서 게시 취소를**&#x200B;선택하고 **Scheduling Later Select** Later **에서**&#x200B;을선택합니다.
   1. 활성화 **날짜를** 선택하고 시간을 지정합니다. **다음**&#x200B;을 클릭합니다.
   1. 범위에서 선택을 확인하고 **다음을** 클릭합니다 ****.
   1. 워크플로우에서 **워크플로우 제목을** 지정합니다 ****. 나중에 **게시 취소를 클릭합니다.**

      ![게시 취소 워크플로우](assets/unpublishworkflows.png)


<!--
End - Publish folders to Brand Portal
Start- Publish Collections to Brand Portal

-->

## Publish collections to Brand Portal {#publish-collections-to-brand-portal}

AEM 자산 인스턴스에서 컬렉션을 게시하거나 게시 취소할 수 있습니다.

>[!NOTE]
>
>콘텐츠 조각을 브랜드 포털에 게시할 수 없습니다. 따라서 AEM 자산에서 컨텐츠 조각을 선택하는 경우 브랜드 포털에 **[!UICONTROL 게시]** 작업을 사용할 수 없습니다.
>
>콘텐츠 조각이 포함된 컬렉션이 AEM 자산에서 브랜드 포털로 게시되면 콘텐츠 조각을 제외한 폴더의 모든 콘텐츠가 브랜드 포털 인터페이스에 복제됩니다.

### 컬렉션 게시 {#publish-a-collection-to-brand-portal}

다음은 AEM 자산에서 브랜드 포털에 컬렉션을 게시하는 단계입니다.

1. AEM 자산 UI에서 AEM 로고를 클릭합니다.
1. 탐색 **페이지에서** 자산 > **[!UICONTROL 컬렉션으로]** 이동합니다 ****.
1. 컬렉션 **콘솔에서** 브랜드 포털에 게시할 컬렉션을 선택합니다.

   ![select_collection](assets/select_collection.png)

1. 도구 모음에서 브랜드 포털에 **[!UICONTROL 게시를 클릭합니다]**.
1. 확인 대화 상자에서 게시를 **[!UICONTROL 클릭합니다]**.
1. 확인 메시지를 닫습니다.

   관리자로 브랜드 포털에 로그인합니다. 게시된 컬렉션은 컬렉션 콘솔에서 사용할 수 **[!UICONTROL 있습니다]** .

   ![게시된 컬렉션](assets/published_collection.png)

## 컬렉션 게시 취소 {#unpublish-collections}

AEM Assets 인스턴스에서 Brand Portal에 게시된 모든 컬렉션을 게시 취소하여 제거할 수 있습니다. 원본 컬렉션을 게시 취소한 후에는 해당 복사본을 더 이상 브랜드 포털 사용자가 사용할 수 없습니다.

다음은 컬렉션 게시 취소 단계입니다.

1. AEM 자산 인스턴스의 컬렉션 콘솔에서 게시 취소할 컬렉션을 선택합니다.

   ![select_collection-1](assets/select_collection-1.png)

1. 도구 모음에서 브랜드 포털에서 **[!UICONTROL 제거 아이콘을 클릭합니다]** .
1. 대화 상자에서 게시 취소를 **[!UICONTROL 클릭합니다]**.
1. 확인 메시지를 닫습니다. 컬렉션은 브랜드 포털 인터페이스에서 제거됩니다.

최종 [사용자에게 자산, 폴더 및 컬렉션을 배포하는 방법에 대한 자세한 내용은 브랜드 포털 설명서를](https://docs.adobe.com/content/help/en/experience-manager-brand-portal/using/home.html) 참조하십시오.

<!--

End - Publish Collections to Brand Portal

-->

