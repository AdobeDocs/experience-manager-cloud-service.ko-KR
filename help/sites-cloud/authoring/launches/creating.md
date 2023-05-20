---
title: 론치 만들기
description: 론치를 만들어 향후 활성화할 수 있도록 기존 웹 페이지의 새 버전 업데이트를 활성화할 수 있습니다.
exl-id: 216ccb7a-1409-4f55-8be2-2b088f91a430
source-git-commit: 90de3cf9bf1c949667f4de109d0b517c6be22184
workflow-type: tm+mt
source-wordcount: '1045'
ht-degree: 68%

---

# 론치 만들기 {#creating-launches}

론치를 만들어 향후 활성화할 수 있도록 기존 웹 페이지의 새 버전 업데이트를 활성화할 수 있습니다. 론치를 만들 때에는 제목과 소스 페이지를 지정합니다.

* 제목은 작성자가 액세스하여 작업할 수 있는 [참조](/help/sites-cloud/authoring/fundamentals/environment-tools.md#references) 레일에 표시됩니다.
* 소스 페이지의 하위 페이지는 기본적으로 론치에 포함됩니다. 원하는 경우 소스 페이지만 사용할 수 있습니다.
* 기본적으로, [Live Copy](/help/sites-cloud/administering/msm/overview.md) 소스 페이지가 변경될 때 론치 페이지를 자동으로 업데이트합니다. 정적 사본을 만들어 자동 변경을 방지하도록 지정할 수 있습니다.

Optionally, you can specify the **Launch Date** (and time) to define when the launch pages are to be promoted and activated. However the **Launch Date** only operates in combination with the **Production Ready** flag (see [Editing a Launch Configuration](/help/sites-cloud/authoring/launches/editing.md#editing-a-launch-configuration)); for the actions to actually occur automatically, both must be set.

>[!NOTE]
>
>론치를 만들 때 계층 구조 상단에 있는 페이지는 소스 페이지의 사본이 아닙니다. 템플릿으로 생성되는 자리표시자입니다.
>
>* `/libs/launches/templates/outofscope`
>
>이들 페이지는 편집할 수 없습니다. 다음과 같은 메시지가 표시됩니다.
>
>* **이 페이지는 론치의 일부가 아닙니다. 프로덕션 페이지로 이동하십시오.**


## 론치 만들기 {#creating-a-launch}

사이트 또는 론치 콘솔에서 론치를 만들 수 있습니다.

1. **사이트** 또는 **론치** 콘솔을 엽니다.

   >[!NOTE]
   >
   >사용 시 **사이트** 콘솔 일반적으로 소스 페이지의 위치로 이동하지만, 이 작업은 를 선택할 때 이동할 수 있으므로 강제적이지 않습니다. **소스 실행** 마법사에서.

1. 사용 중인 콘솔에 따라 다음 작업을 수행하십시오.
   * **론치**:
      1. 선택 **시작 만들기** 을 클릭하여 마법사를 엽니다.
   * **사이트**:
      1. 도구 모음에서 **만들기**&#x200B;를 선택하여 선택 상자를 엽니다.
      1. 여기에서 선택 **시작 만들기** 을 클릭하여 마법사를 엽니다.

   >[!NOTE]
   >
   >**사이트** 콘솔에서 **만들기**&#x200B;를 선택하기 전에 [선택 모드](/help/sites-cloud/authoring/getting-started/basic-handling.md#viewing-and-selecting-resources)를 사용하여 페이지를 선택할 수도 있습니다.
   >
   >이렇게 하면 선택한 페이지가 초기 소스 페이지로 사용됩니다.

1. **소스 선택** 단계에서 **페이지를 추가**&#x200B;해야 합니다. 각각에 대해 경로를 지정하여 여러 페이지를 선택할 수 있습니다.
   * 필요한 위치로 이동합니다.
   * 소스 페이지를 선택하고 확인합니다(확인 표시 선택).

   필요에 따라 반복하십시오.

   ![론치 소스 선택](/help/sites-cloud/authoring/assets/launches-select-source.png)

   >[!NOTE]
   >
   >론치에 페이지 및/또는 분기를 추가하려면 사이트 내에 있어야 합니다(예: 일반적인 최상위 루트 아래).
   >
   >사이트에 최상위 수준 아래의 언어 루트가 포함되어 있는 경우 론치용 페이지 및 분기는 공통 언어 루트 아래에 있어야 합니다.

1. 각 항목에 대해 다음 중 하나를 지정할 수 있습니다.

   * **하위 페이지 포함**:

      * 하위 페이지를 포함하여 론치를 만들지 아니면 하위 페이지를 포함하지 않고 론치를 만들지 지정합니다. 기본적으로 이 하위 페이지가 포함됩니다.

   **다음**&#x200B;을 선택하여 계속 진행합니다.

   ![론치 소스 선택](/help/sites-cloud/authoring/assets/launches-select-source-2.png)

1. 마법사의 **속성** 단계에서 다음을 지정할 수 있습니다.

   * **론치 제목**: 론치의 이름입니다. 작성자에게는 이름이 의미 있어야 합니다.
   * **기존 콘텐츠 사용**: 원래 콘텐츠가 론치를 만드는 데 사용됩니다.
   * **새 템플릿을 사용하여 페이지 바꾸기**: 자세한 내용은 [새 템플릿을 사용하여 론치 만들기](#create-launch-with-new-template)를 참조하십시오.
   * **소스 페이지의 라이브 데이터 상속**: 이 옵션을 선택하면 소스 페이지를 변경할 때 론치 페이지 콘텐츠가 자동으로 업데이트됩니다. 이 옵션은 론치를 [라이브 카피](/help/sites-cloud/administering/msm/overview.md)로 만들어 이 작업을 수행합니다. 기본적으로 이 옵션은 선택되어 있습니다.-->
   * **론치 날짜**: 론치 카피가 활성화될 날짜 및 시간입니다(**프로덕션 준비** 플래그에 따라 다름). [론치 - 이벤트 순서](/help/sites-cloud/authoring/launches/overview.md#launches-the-order-of-events)를 참조하십시오.

   ![론치 속성](/help/sites-cloud/authoring/assets/launches-properties.png)

1. 사용 **만들기** 프로세스를 완료하고 새 론치를 만듭니다. 확인 대화 상자에 시작을 즉시 열지 여부를 묻는 메시지가 표시됩니다.

   콘솔을 반환하는 경우(와 함께) **완료**) 다음 중 하나에서 론치를 보고 액세스할 수 있습니다.

   * [**론치** 콘솔](/help/sites-cloud/authoring/launches/overview.md#the-launches-console)
   * **사이트** 콘솔의 [**참조**](/help/sites-cloud/authoring/launches/overview.md#launches-in-references-sites-console)

### 새 템플릿을 사용하여 론치 만들기 {#create-launch-with-new-template}

론치를 만들 때 새 템플릿 사용 여부를 선택할 수 있습니다.

>[!NOTE]
>
>이 옵션은 **사이트** 콘솔에서 론치를 만들 때만 사용할 수 있습니다. **론치** 콘솔에서 론치를 만들 때는 사용할 수 없습니다.

![새 템플릿을 사용하여 론치 만들기](/help/sites-cloud/authoring/assets/launches-create-new-template.png)

이 옵션을 선택하면 다음이 수행됩니다.

* 사용할 수 있는 다른 옵션이 업데이트되며,
* 필요한 템플릿을 선택할 수 있는 새로운 단계가 포함됩니다.

![새 템플릿 선택](/help/sites-cloud/authoring/assets/launches-select-template.png)

>[!CAUTION]
>
>다른 템플릿을 사용하면 새 페이지가 비어 있습니다. 다른 페이지 구조로 인해 콘텐츠가 복사되지 않습니다.
>
>이 메커니즘을 사용하면 [기존 페이지](/help/sites-cloud/authoring/fundamentals/organizing-pages.md#creating-a-new-page)의 템플릿을 변경할 수 있습니다. 단, 콘텐츠 손실을 고려해야 합니다.

### 중첩 론치 만들기 {#creating-a-nested-launch}

중첩 론치(론치 내의 론치)를 만들면 작성자가 각 론치에 대해 동일한 변경 내용을 여러 번 변경하지 않고, 이미 수행된 변경 내용을 활용할 수 있도록 기존 론치에서 론치를 만들 수 있습니다.

>[!NOTE]
>
>[중첩 론치 홍보](/help/sites-cloud/authoring/launches/promoting.md#promoting-a-nested-launch)도 참조하십시오.

#### 중첩 론치 만들기 - 론치 콘솔 {#creating-a-nested-launch-launches-console}

**론치** 콘솔에서 중첩 론치를 만드는 것은 다른 형식의 론치를 만드는 것과 기본적으로 동일하지만, 이 경우에는 예외적으로 론치 분기(`/content/launches`)로 이동해야 합니다.

1. **론치** 콘솔에서 **만들기**&#x200B;를 선택합니다.
1. **페이지 추가**&#x200B;를 선택한 다음 **필터** 레일의 `/content/launches`를 지정하여 론치 분기로 이동합니다. 필요한 론치를 선택하고 **선택**&#x200B;을 사용하여 확인합니다.

   ![중첩 론치 만들기](/help/sites-cloud/authoring/assets/launches-create-nested.png)

1. **다음**&#x200B;을 선택하여 계속 진행합니다.

1. 다른 론치와 마찬가지로 **속성**&#x200B;을 완료합니다.

1. **만들기**&#x200B;를 사용하여 완료합니다.

#### 중첩 론치 만들기 - 사이트 콘솔 {#creating-a-nested-launch-sites-console}

기존 론치를 기준으로 **사이트** 콘솔에서 중첩 실행을 만들려면 다음 작업을 수행하십시오.

1. [참조의 론치(사이트 콘솔)](/help/sites-cloud/authoring/launches/overview.md#launches-in-references-sites-console)에 액세스하여 사용 가능한 동작을 표시합니다.
1. **론치 만들기**&#x200B;를 선택하여 마법사를 엽니다. 소스는 이미 선택했으므로 **소스 선택** 단계로 넘어갑니다.
1. **론치 제목** 및 기타 필수 세부 정보를 입력합니다(일반 론치의 경우와 같음).
1. 사용 **만들기** 프로세스를 완료하고 새 론치를 만듭니다. 확인 대화 상자에 시작을 즉시 열지 여부를 묻는 메시지가 표시됩니다.

**완료**&#x200B;를 선택하면 **사이트** 콘솔의 **참조** 레일로 돌아가며, 적절한 페이지를 선택하면 새 론치가 표시됩니다.

### 론치 삭제 {#deleting-a-launch}

다음에서 론치를 삭제할 수 있습니다. [론치 콘솔](/help/sites-cloud/authoring/launches/overview.md#the-launches-console):

* 썸네일을 탭/클릭하여 론치를 선택합니다.
* 도구 모음이 나타납니다. 삭제 를 선택합니다.
* 작업을 확인합니다.

>[!CAUTION]
>
>론치를 삭제하면 론치 자체 및 모든 하위 중첩 론치가 제거됩니다.
