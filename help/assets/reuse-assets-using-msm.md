---
title: MSM을 사용하여 자산 재사용
description: 상위 에셋에서 파생되고 연결된 여러 페이지/폴더에서 에셋을 사용합니다. 자산은 기본 복사본과 동기화 상태를 유지하며, 몇 번의 클릭만으로 상위 자산으로부터 업데이트를 받습니다.
contentOwner: AG
mini-toc-levels: 1
role: User, Admin, Architect
feature: Asset Management
exl-id: a71aebdf-8e46-4c2d-8960-d188b14aaae9
source-git-commit: 32fdbf9b4151c949b307d8bd587ade163682b2e5
workflow-type: tm+mt
source-wordcount: '3407'
ht-degree: 11%

---

# [!DNL Assets]에 대해 MSM을 사용하여 자산 재사용 {#reuse-assets-using-msm-for-assets}

| 버전 | 문서 링크 |
| -------- | ---------------------------- |
| AEM 6.5 | [여기 클릭](https://experienceleague.adobe.com/docs/experience-manager-65/assets/using/reuse-assets-using-msm.html?lang=ko) |
| AEM as a Cloud Service | 이 문서 |

[!DNL Adobe Experience Manager]의 MSM(다중 사이트 관리자) 기능을 사용하면 한 번 작성되고 여러 웹 위치에서 재사용되는 콘텐츠를 다시 사용할 수 있습니다. [!DNL Assets]에 대해 MSM이라는 이름의 디지털 에셋에 동일한 기능을 사용할 수 있습니다. [!DNL Assets]에 MSM을 사용하여 다음을 수행할 수 있습니다.

* 에셋을 한 번 만든 다음 이러한 에셋의 사본을 만들어 사이트의 다른 영역에서 재사용할 수 있습니다.
* 여러 복사본을 동기화한 다음 원본 기본 복사본을 한 번 업데이트하여 변경 내용을 하위 복사본으로 푸시합니다.
* 상위 에셋과 하위 에셋 간의 연결을 일시적으로 또는 영구적으로 일시 중단하여 로컬 변경 작업을 수행합니다.

>[!NOTE]
>
>[!DNL Assets] 기능에 대한 MSM에는 [!DNL Assets]&#x200B;(사이트 기능으로 간주됨)으로 저장된 콘텐츠 조각이 포함되어 있습니다.

>[!CAUTION]
>
>콘텐츠 조각용 MSM은 **[!UICONTROL Assets]** 콘솔을 통해 콘텐츠 조각을 사용하는 경우에만 사용할 수 있습니다.
>
>MSM 기능은 **[!UICONTROL 콘텐츠 조각]** 콘솔을 사용할 때 *사용할 수 없습니다*.

## MSM의 이점 및 개념 이해 {#concepts}

### 작동 방식 및 이점 {#how-it-works-and-the-benefits}

여러 웹 위치에서 동일한 콘텐츠(텍스트 및 자산)를 재사용하기 위한 사용 시나리오를 이해하려면 [가능한 MSM 시나리오](/help/sites-cloud/administering/msm/overview.md)를 참조하세요. [!DNL Experience Manager]은(는) LC(라이브 카피)라고 하는 원본 에셋과 연결된 복사본 간의 연결을 유지합니다. 유지 관리되는 연결을 통해 중앙 집중식 변경 사항을 여러 라이브 카피로 푸시할 수 있습니다. 따라서 중복 복제본을 관리해야 하는 한계를 극복하면서 더욱 신속하게 업데이트할 수 있습니다. 변경 사항의 전파에는 오류가 없으며 중앙 집중화됩니다. 이 기능을 사용하면 선택한 라이브 카피로 제한된 업데이트 공간을 확보할 수 있습니다. 사용자는 링크(상속 중단)를 분리하고, 다음에 기본 복사본이 업데이트되고 변경 사항이 롤아웃될 때 덮어쓰지 않는 로컬 편집을 수행할 수 있습니다. 일부 선택한 메타데이터 필드 또는 전체 에셋에 대해 분리를 수행할 수 있습니다. 이를 통해 기본 복사본에서 원래 상속된 자산을 로컬로 업데이트할 수 있습니다.

MSM은 소스 에셋과 해당 라이브 카피 간에 라이브 관계를 유지하여 다음 작업을 수행합니다.

* 소스 에셋에 대한 변경 사항은 라이브 카피에도 적용(롤아웃)됩니다. 즉, 라이브 카피가 소스와 동기화됩니다.
* 라이브 관계를 일시 중단하여 라이브 카피를 업데이트하거나, 몇 가지 제한된 필드에 대한 상속을 제거할 수 있습니다. 소스에 대한 수정 사항이 라이브 카피에 더 이상 적용되지 않습니다.

### [!DNL Assets]개 용어 MSM 용어집 {#glossary}

**Source:** 원본 에셋 또는 폴더입니다. 라이브 카피가 파생된 기본 카피입니다.

**Live Copy:** 원본과 동기화 중인 원본 에셋/폴더의 복사본입니다. 라이브 카피는 추가 라이브 카피의 소스가 될 수 있습니다. LC 생성 방법을 참조하십시오.

**상속:** 시스템이 업데이트를 보낼 위치를 기억하기 위해 사용하는 Live Copy 에셋/폴더와 소스 간의 링크/참조입니다. 상속은 메타데이터 필드, 콘텐츠 조각 변형 및 필드에 대해 세분화된 수준에서 존재합니다. 소스와 해당 라이브 카피 간의 라이브 관계를 유지하면서 선택한 항목에 대한 상속을 제거할 수 있습니다.

**롤아웃:** 소스 다운스트림에 대한 수정 사항을 해당 라이브 카피로 푸시하는 작업입니다. 롤아웃 작업을 사용하여 한 번에 하나 이상의 라이브 카피를 업데이트할 수 있습니다. 롤아웃을 참조하십시오.

**롤아웃 구성:** 동기화될 속성, 동기화 방법 및 시기를 결정하는 규칙입니다. 이러한 구성은 라이브 카피 생성 시 적용되며 나중에 편집할 수 있습니다. 하위는 상위 자산에서 롤아웃 구성을 상속할 수 있습니다. [!DNL Assets]에 대한 MSM의 경우 표준 롤아웃 구성만 사용하십시오. 다른 롤아웃 구성은 [!DNL Assets]의 MSM에 사용할 수 없습니다.

**동기화:** 롤아웃 외에 소스에서 라이브 카피로 업데이트를 전송하여 소스와 라이브 카피 간의 패리티를 가져오는 다른 작업입니다. 특정 Live Copy에 대한 동기화가 시작되고 해당 작업은 소스에서 변경 내용을 가져옵니다. 이 작업을 사용하여에서 라이브 카피 중 하나만 업데이트할 수 있습니다. 동기화 작업을 참조하십시오.

**일시 중단:** Live Copy와 원본 에셋/폴더 간의 Live 관계를 일시적으로 제거합니다. 관계를 다시 시작할 수 있습니다. 일시 중단 작업을 참조하십시오.

**다시 시작:** Live Copy가 원본에서 업데이트를 받기 시작할 수 있도록 Live 관계를 다시 시작합니다. 다시 시작 작업을 참조하십시오.

**재설정:** 재설정 작업을 수행하면 로컬 변경 사항을 덮어써서 Live Copy가 다시 소스의 복제본이 됩니다. 또한 상속 취소를 제거하고 모든 메타데이터 필드에서 상속을 재설정합니다. 나중에 로컬을 수정하려면 특정 필드의 상속을 다시 취소해야 합니다. LC에 대한 로컬 수정 사항을 참조하십시오.

**분리:** Live Copy 에셋/폴더의 Live 관계를 취소할 수 없습니다. 분리 작업 후에는 라이브 카피가 소스에서 업데이트를 받을 수 없으며 더 이상 라이브 카피가 되지 않습니다. 관계 제거를 참조하십시오.

## 에셋의 Live Copy 만들기 {#create-livecopy}

하나 이상의 소스 에셋 또는 폴더에서 Live Copy를 만들려면 다음 중 하나를 수행합니다.

* 방법 1: 소스 자산을 선택하고 상단의 도구 모음에서 **[!UICONTROL 만들기]** > **[!UICONTROL Live Copy]**&#x200B;를 클릭합니다.
* 방법 2: [!DNL Experience Manager] 사용자 인터페이스의 오른쪽 상단에서 **[!UICONTROL 만들기]** > **[!UICONTROL Live Copy]**&#x200B;를 클릭합니다.

에셋 또는 폴더의 라이브 카피를 한 번에 하나씩 만들 수 있습니다. 에셋 또는 라이브 카피 자체인 폴더에서 파생된 라이브 카피를 만들 수 있습니다.

첫 번째 방법을 사용하여 라이브 카피를 만들려면 다음 단계를 수행합니다.

1. 소스 에셋 또는 폴더를 선택합니다. 도구 모음에서 **[!UICONTROL 만들기]** > **[!UICONTROL Live Copy]**&#x200B;를 클릭합니다.

   ![[!DNL Experience Manager] 인터페이스에서 Live Copy 만들기](assets/create_lc1.png)

   *그림: [!DNL Experience Manager] 인터페이스에서 Live Copy를 만듭니다.*

1. 대상 폴더를 선택하십시오. **[!UICONTROL 다음]**&#x200B;을 클릭합니다.
1. 제목과 이름을 입력합니다. Assets에는 하위 항목이 없습니다. 폴더의 라이브 카피를 만들 때 하위 항목을 포함하거나 제외하도록 선택할 수 있습니다.
1. 롤아웃 구성을 선택합니다. **[!UICONTROL 만들기]**&#x200B;를 클릭합니다.

두 번째 방법을 사용하여 라이브 카피를 만들려면 다음 단계를 수행합니다.

1. [!DNL Experience Manager] 인터페이스의 오른쪽 상단에서 **[!UICONTROL 만들기]** > **[!UICONTROL Live Copy]**&#x200B;를 클릭합니다.

   ![[!DNL Experience Manager] 인터페이스에서 Live Copy 만들기](assets/create_lc2.png)

   *그림: [!DNL Experience Manager] 인터페이스에서 Live Copy를 만듭니다.*

1. 소스 에셋 또는 폴더를 선택하십시오. **[!UICONTROL 다음]**&#x200B;을 클릭합니다.
1. 대상 폴더를 선택합니다. **[!UICONTROL 다음]**&#x200B;을 클릭합니다.
1. 제목과 이름을 입력합니다. Assets에는 하위 항목이 없습니다. 폴더의 라이브 카피를 만들 때 하위 항목을 포함하거나 제외하도록 선택할 수 있습니다.
1. 롤아웃 구성을 선택합니다. **[!UICONTROL 만들기]**&#x200B;를 클릭합니다.

>[!NOTE]
>
>소스 또는 라이브 카피를 이동하면 관계가 유지됩니다. Live Copy가 삭제되면 관계가 제거됩니다.

## 소스 및 라이브 카피의 다양한 속성 및 상태 보기 {#properties}

[!DNL Experience Manager] 사용자 인터페이스의 다양한 영역에서 관계, 동기화, 롤아웃 등과 같은 Live Copy의 정보 및 MSM 관련 상태를 볼 수 있습니다.

에셋 및 폴더에는 다음 두 가지 방법이 적용됩니다.

* 라이브 카피 자산을 선택하고 속성 페이지에서 정보를 찾습니다.
* 소스 폴더를 선택하고 [!UICONTROL Live Copy 콘솔]에서 각 Live Copy에 대한 자세한 정보를 찾으십시오.

>[!TIP]
>
>몇 개의 개별 라이브 카피의 상태를 확인하려면 첫 번째 메서드를 사용하여 **[!UICONTROL 속성]** 페이지를 확인하세요. 많은 라이브 카피의 상태를 확인하려면 두 번째 메서드를 사용하여 **[!UICONTROL 관계 상태]** 페이지를 확인하세요.

### 라이브 카피의 정보 및 상태 {#status-lc-asset}

라이브 카피 에셋 또는 폴더의 정보 및 상태를 확인하려면 다음 단계를 수행하십시오.

1. Live Copy 에셋 또는 폴더를 선택합니다. 도구 모음에서 **[!UICONTROL 속성]**&#x200B;을 클릭합니다. 또는 키보드 단축키 `p`을(를) 사용합니다.
1. **[!UICONTROL Live Copy]**&#x200B;을(를) 클릭합니다. 소스 경로, 일시 중단 상태, 동기화 상태, 마지막 롤아웃 날짜 및 마지막 롤아웃을 수행한 사용자를 확인할 수 있습니다.

   ![Live Copy 정보 및 상태가 속성의 콘솔에 표시됩니다](assets/lcfolder_info_properties.png)

   *그림: Live Copy 정보 및 상태*

1. 하위 자산이 라이브 카피 구성을 빌리는 경우 활성화하거나 비활성화할 수 있습니다.

1. 라이브 카피에 대한 옵션을 선택하여 상위 항목에서 롤아웃 구성을 상속하거나 구성을 변경할 수 있습니다.

### 폴더의 모든 라이브 카피에 대한 정보 및 상태 {#status-lc-folder}

[!DNL Experience Manager]은(는) 원본 폴더의 모든 라이브 카피의 상태를 확인할 수 있는 콘솔을 제공합니다. 이 콘솔에는 모든 하위 자산의 상태가 표시됩니다.

1. 소스 폴더를 선택합니다. 도구 모음에서 **[!UICONTROL 속성]**&#x200B;을 클릭합니다. 또는 키보드 단축키 `p`을(를) 사용합니다.
1. Click **[!UICONTROL Live Copy Source]**. To open the console, click **[!UICONTROL Live Copy Overview]**. This dashboard provides a top-level status of all the child assets.

   ![소스의 Live Copy 콘솔에서 Live Copy 상태 보기](assets/livecopy-statuses.png)

   *그림: 소스의 [!UICONTROL Live Copy 콘솔]에서 Live Copy 상태 보기*

1. To view the detailed information about each asset in the live copy folder, select an asset and click **[!UICONTROL Relationship Status]** from the toolbar.

   ![폴더에 있는 Live Copy 하위 자산의 자세한 정보 및 상태](assets/livecopy_relationship_status.png)

   폴더에 있는 라이브 카피 하위 에셋의 세부 정보 및 상태

>[!TIP]
>
>너무 많이 탐색하지 않고도 다른 폴더의 라이브 카피 상태를 빠르게 볼 수 있습니다. **[!UICONTROL Live Copy 개요]** 인터페이스의 가운데 위쪽에서 폴더를 변경합니다.

### 소스에 대한 참조 레일의 빠른 작업 {#ref-rail-source}

소스 에셋 또는 폴더의 경우 다음 정보를 보고 참조 레일에서 직접 다음 작업을 수행할 수 있습니다.

* 라이브 카피의 경로를 참조하십시오.
* [!DNL Experience Manager] 사용자 인터페이스에서 특정 Live Copy를 열거나 표시합니다.
* 특정 라이브 카피에 대한 업데이트를 동기화합니다.
* 특정 라이브 카피에 대해 관계를 일시 중단하거나 롤아웃 구성을 변경합니다.
* 라이브 카피 개요 콘솔에 액세스합니다.

원본 에셋 또는 폴더를 선택하고 왼쪽 레일을 연 다음 **[!UICONTROL 참조]**&#x200B;를 클릭합니다. 또는 에셋 또는 폴더를 선택하고 키보드 단축키 `Alt + 4`을(를) 사용합니다.

![선택한 소스에 대해 참조 레일에서 사용할 수 있는 작업 및 정보](assets/referencerail_source.png)

*그림: 선택한 원본의 참조 레일에서 사용할 수 있는 작업 및 정보입니다.*

특정 Live Copy의 경우 **[!UICONTROL Live Copy 편집]**&#x200B;을 클릭하여 관계를 일시 중단하거나 롤아웃 구성을 변경합니다.

![특정 Live Copy의 경우 원본 자산을 선택할 때 참조 레일에서 관계를 일시 중단하거나 롤아웃 구성을 변경하는 옵션에 액세스할 수 있습니다](assets/referencerail_editlc_options.png)

*그림: 특정 Live Copy의 관계를 일시 중단하거나 롤아웃 구성을 변경합니다.*

### 라이브 카피에 대한 참조 레일의 빠른 작업 {#ref-rail-lc}

라이브 카피 에셋 또는 폴더의 경우 다음 정보를 확인하고 참조 레일에서 직접 다음 작업을 수행할 수 있습니다.

* 해당 소스의 경로를 확인합니다.
* [!DNL Experience Manager] 사용자 인터페이스에서 특정 Live Copy를 열거나 표시합니다.
* 업데이트 롤아웃

Select a live copy asset or folder, open the left rail, and click **[!UICONTROL References]**. 또는 에셋 또는 폴더를 선택하고 키보드 단축키 `Alt + 4`을(를) 사용합니다.

![Actions available in the References rail for the selected live copy](assets/referencerail_livecopy.png)

*그림: 선택한 Live Copy의 참조 레일에서 사용할 수 있는 작업입니다.*

## 소스에서 라이브 카피로 수정 사항 전파 {#rollout-sync}

소스가 수정된 후에는 동기화 작업이나 롤아웃 작업을 사용하여 변경 사항을 라이브 카피로 전파할 수 있습니다. 두 작업의 차이점을 이해하려면 [용어집](#glossary)을 참조하세요.

### 롤아웃 작업 {#rollout}

소스 에셋에서 롤아웃 작업을 시작하고 선택한 라이브 카피를 모두 또는 일부 업데이트할 수 있습니다.

1. Live Copy 에셋 또는 폴더를 선택합니다. 도구 모음에서 **[!UICONTROL 속성]**&#x200B;을 클릭합니다. 또는 키보드 단축키 `p`을(를) 사용합니다.
1. Click **[!UICONTROL Live Copy Source]**. 도구 모음에서 **[!UICONTROL 롤아웃]**&#x200B;을 클릭합니다.
1. 업데이트할 라이브 카피를 선택합니다. **[!UICONTROL 롤아웃]**&#x200B;을 클릭합니다.
1. 하위 자산에 대한 업데이트를 롤아웃하려면 **[!UICONTROL Source 및 모든 하위 자산 롤아웃]**&#x200B;을 선택하십시오.

   ![일부 또는 모든 라이브 카피에 소스 수정 내용을 롤아웃](assets/livecopy_rollout_page.png)

   *그림: 일부 또는 모든 라이브 카피에 소스 수정 내용을 롤아웃합니다.*

>[!NOTE]
>
>소스 에셋에서 수정된 내용은 직접 관련된 라이브 카피에만 롤아웃됩니다. 라이브 카피가 다른 라이브 카피에서 파생된 경우 수정 사항이 파생된 라이브 카피로 롤아웃되지 않습니다.

또는 특정 라이브 카피를 선택한 후 참조 레일에서 롤아웃 작업을 시작할 수 있습니다. 자세한 내용은 [Live Copy에 대한 참조 레일의 빠른 작업](#ref-rail-lc)을 참조하세요. 이 롤아웃 방법에서는 선택한 라이브 카피와 선택적으로 그 하위 항목만 업데이트됩니다.

![선택한 Live Copy에 대한 소스 수정 내용을 롤아웃](assets/livecopy_rollout_dialog.png)

*그림: 선택한 Live Copy에 대한 소스 수정 내용을 롤아웃합니다.*

### 동기화 작업 기본 정보 {#about-sync}

동기화 작업은 수정 사항을 소스에서 선택한 라이브 카피로만 가져옵니다. 동기화 작업은 상속을 취소한 후 수행된 로컬 수정 사항을 준수하고 유지 관리합니다. 로컬 수정 사항은 덮어쓰이지 않으며 취소된 상속은 다시 설정되지 않습니다. 세 가지 방법으로 동기화 작업을 시작할 수 있습니다.

| [!DNL Experience Manager] 인터페이스의 위치 | 사용 시기 및 이유 | 사용 방법 |
|---|---|---|
| [!UICONTROL 참조] 레일 | 소스를 이미 선택한 경우 빠르게 동기화합니다. | 원본의 [참조 레일의 빠른 작업](#ref-rail-source)을 참조하세요. |
| [!UICONTROL 속성] 페이지의 도구 모음 | 라이브 카피 속성이 이미 열려 있는 경우 동기화를 시작합니다. | [Live Copy 동기화](#sync-lc)를 참조하십시오. |
| [!UICONTROL Live Copy 개요] 콘솔 | 소스 폴더를 선택하거나 [!UICONTROL Live Copy 개요] 콘솔이 이미 열려 있는 경우 여러 자산을 빠르게 동기화합니다(모든 자산일 필요는 없음). 동기화 작업은 한 번에 한 에셋에 대해 시작되지만 한 번에 여러 에셋에 대해 더 빠르게 동기화할 수 있는 방법입니다. | [Live Copy 폴더의 많은 자산에 대한 작업](#bulk-actions)을 참조하세요. |

### 라이브 카피 동기화 {#sync-lc}

To start a sync action, open **[!UICONTROL Properties]** page of a live copy, click **[!UICONTROL Live Copy]** and click the desired action from the toolbar.

To see the statuses and information related to a synchronize action, see [Information and status of a live copy](#status-lc-asset) and [Information and statuses of all live copies of a folder](#status-lc-folder).

![동기화 작업이 소스에 적용된 변경 내용을 가져옵니다](assets/livecopy_sync.png)

*그림: 동기화 작업은 소스에 적용된 변경 내용을 가져옵니다.*

>[!NOTE]
>
>관계가 일시 중단되면 도구 모음에서 동기화 작업을 사용할 수 없습니다. 참조 레일에서 동기화 작업을 사용할 수 있지만 롤아웃이 성공해도 수정 사항이 전파되지 않습니다.

## 개별 항목에 대한 상속 취소 및 다시 활성화 {#canceling-reenabling-inheritance-individual-items}

다음에 대한 라이브 카피 상속을 취소할 수 있습니다.

* 메타데이터 필드
* [컨텐츠 조각 변형](/help/assets/content-fragments/content-fragments-variations.md#inheritance)
* [컨텐츠 조각 데이터 필드](/help/assets/content-fragments/content-fragments-variations.md#inheritance)

이 경우 항목은 더 이상 소스 구성 요소와 동기화되지 않습니다. 필요한 경우 나중에 상속을 활성화할 수 있습니다.

### 상속 취소 {#cancel-inheritance}

상속을 취소하려면 다음을 수행합니다.

1. 필수 항목 옆의 **상속 취소** 아이콘을 선택합니다.

   ![동기화 작업이 소스에 적용된 변경 내용을 가져옵니다](assets/cancel-inheritance-icon.png)

1. 상속 취소 대화 상자에서 예를 선택하여 작업을 확인합니다.

### 상속 다시 사용 {#reenable-inheritance}

상속을 다시 활성화하려면 다음을 수행합니다.

1. 항목에 대한 상속을 활성화하려면 필수 항목 옆에 있는 **상속 다시 활성화** 아이콘을 선택합니다.

   ![동기화 작업이 소스에 적용된 변경 내용을 가져옵니다](assets/re-enable-inheritance-icon.png)

   >[!NOTE]
   >
   >상속을 다시 활성화하면 항목이 자동으로 소스와 동기화되지 않습니다. 필요한 경우 수동으로 동기화를 요청할 수 있습니다.

## 관계 일시 중단 및 재개 {#suspend-resume}

관계를 일시적으로 일시 중단하여 Live Copy가 소스 에셋 또는 폴더에 대한 수정 사항을 수신하지 못하도록 할 수 있습니다. 라이브 카피에 대해 관계를 재개하여 소스의 수정 사항을 수신할 수도 있습니다.

To suspend or resume, open **[!UICONTROL Properties]** page of a live copy, click **[!UICONTROL Live Copy]** and click the desired action from the toolbar.

Alternatively, you can quickly suspend or resume relationships of multiple assets in a live copy folder from the **[!UICONTROL Live Copy Overview]** console. See [Take actions on many assets in live copy folders](#bulk-actions).

## Live Copy의 로컬 수정 {#local-mods}

라이브 카피는 원본 소스가 생성될 때의 복제본입니다. 라이브 카피의 메타데이터 값은 소스에서 상속됩니다. 메타데이터 필드는 소스 에셋의 해당 필드와 함께 상속을 개별적으로 유지합니다.

However, you have the flexibility to make local modifications to a live copy to change a few select properties. To make local modifications, cancel the inheritance of the desired property. When inheritance of one or more metadata fields is canceled, the live relationship of the asset and the inheritance of the other metadata fields is retained. Any synchronization or rollout does not overwrite the local modifications. 이렇게 하려면 Live Copy 에셋의 **[!UICONTROL 속성]** 페이지를 열고 메타데이터 필드 옆에 있는 **[!UICONTROL 상속 취소]** 옵션을 클릭합니다.

모든 로컬 수정 사항을 실행 취소하고 자산을 소스 상태로 되돌릴 수 있습니다. 작업을 되돌릴 수 없으며 즉시 모든 로컬 수정 사항을 무시하고 모든 메타데이터 필드에 상속을 다시 설정합니다. 되돌리려면 Live Copy 에셋의 **[!UICONTROL 속성]** 페이지에서 도구 모음의 **[!UICONTROL 재설정]**&#x200B;을 클릭하세요.

![다시 설정 작업은 로컬 편집 내용을 덮어쓰고 Live Copy를 원본과 부분적으로 가져옵니다.](assets/livecopy_reset.png)

*그림: 재설정 작업을 수행하면 로컬 편집 내용이 덮어쓰기되고 Live Copy가 원본과 일부 연결되었습니다.*

## 라이브 관계 제거 {#detach}

분리 작업을 사용하여 소스와 라이브 카피 간의 관계를 완전히 제거할 수 있습니다. Live Copy는 분리된 후 독립형 에셋 또는 폴더가 됩니다. [!DNL Experience Manager] 인터페이스에서 분리한 직후에 새 자산으로 표시됩니다. 소스에서 Live Copy를 분리하려면 다음 단계를 따르십시오.

1. Live Copy 에셋 또는 폴더를 선택합니다. 도구 모음에서 **[!UICONTROL 속성]**&#x200B;을 클릭합니다. 또는 키보드 단축키 `p`을(를) 사용합니다.

1. **[!UICONTROL Live Copy]**&#x200B;을(를) 클릭합니다. 도구 모음에서 **[!UICONTROL 분리]**&#x200B;를 클릭합니다. 표시된 대화 상자에서 **[!UICONTROL 분리]**&#x200B;를 클릭합니다.

   ![분리 작업은 원본과 Live Copy 간의 관계를 완전히 제거합니다](assets/livecopy_detach.png)

   *그림: 분리 작업을 수행하면 원본과 Live Copy 간의 관계가 완전히 제거됩니다.*

   >[!CAUTION]
   >
   >대화 상자에서 **[!UICONTROL 분리]**&#x200B;를 클릭하면 관계가 즉시 제거됩니다. 속성 페이지에서 **[!UICONTROL 취소]**&#x200B;를 클릭하여 실행을 취소할 수 없습니다.

또는 **[!UICONTROL Live Copy 개요]** 콘솔에서 Live Copy 폴더의 여러 자산을 빠르게 분리할 수 있습니다. See [Take actions on many assets in live copy folders](#bulk-actions).

## 라이브 카피 폴더의 일괄 작업 {#bulk-actions}

라이브 카피 폴더에 여러 에셋이 있는 경우 각 에셋에 대한 작업을 시작하면 지루할 수 있습니다. [!UICONTROL Live Copy 콘솔]에서 많은 에셋에 대한 기본 작업을 빠르게 시작할 수 있습니다. 위의 방법은 개별 자산에 대해 계속 작동합니다.

1. 소스 폴더를 선택합니다. 도구 모음에서 **[!UICONTROL 속성]**&#x200B;을 클릭합니다. 또는 키보드 단축키 `p`을(를) 사용합니다.
1. Click **[!UICONTROL Live Copy Source]**. To open the console, click **[!UICONTROL Live Copy Overview]**.
1. In this dashboard, select a live copy asset from a live copy folder. Click the desired actions from the toolbar. 사용 가능한 작업은 **[!UICONTROL 동기화]**, **[!UICONTROL 재설정]**, **[!UICONTROL 일시 중단]** 및 **[!UICONTROL 분리]**&#x200B;입니다. 선택한 소스 폴더와 라이브 관계에 있는 모든 라이브 카피 폴더의 에셋에 대해 이러한 작업을 신속하게 시작할 수 있습니다.

   ![Live Copy 개요 콘솔에서 Live Copy 폴더의 많은 에셋을 쉽게 업데이트할 수 있습니다](assets/livecopyconsole_update_many_assets.png)

   *그림: [!UICONTROL Live Copy 개요] 콘솔에서 Live Copy 폴더의 많은 자산을 쉽게 업데이트할 수 있습니다.*

<!-- TBD: Can MSM be extended using Java APIs in CS?

## Extend MSM for [!DNL Assets] {#extend-api}

[!DNL Experience Manager] lets you extend the functionality using the MSM Java APIs. For [!DNL Assets], the extending works just the same as it works with MSM for [!DNL Sites]. For details, see [Extending the MSM](/help/sites-developing/extending-msm.md) and the following for information about specific tasks:

* [Overview of APIs](/help/sites-developing/extending-msm.md#overview-of-the-java-api)
* [Create a synchronization action](/help/sites-developing/extending-msm.md#creating-a-new-synchronization-action)
* [Create a rollout configuration](/help/sites-developing/extending-msm.md#creating-a-new-rollout-configuration)
* [Create and use a simple LiveActionFactory class](/help/sites-developing/extending-msm.md#creating-and-using-a-simple-liveactionfactory-class)

-->

## 자산 관리 작업이 라이브 카피에 미치는 영향 {#manage-assets}

라이브 카피 및 소스는 디지털 에셋으로 일정 정도 관리할 수 있는 에셋 또는 폴더입니다. [!DNL Experience Manager]의 일부 에셋 관리 작업은 라이브 카피에 특정 영향을 줍니다.

* 라이브 카피를 복사하면 첫 번째 라이브 카피와 동일한 소스를 사용하는 라이브 카피 자산이 만들어집니다.
* 소스 또는 해당 라이브 카피를 이동하면 라이브 관계가 유지됩니다.
* Live Copy 자산에 대해 편집 작업이 작동하지 않습니다. 라이브 카피의 소스가 그 자체로 라이브 카피인 경우 편집 작업이 작동하지 않습니다.
* 체크아웃 작업은 Live Copy 자산에 사용할 수 없습니다.
* 소스 폴더의 경우 검토 작업을 생성하는 옵션을 사용할 수 있습니다.
* 목록 보기 및 열 보기에서 에셋 목록을 볼 때 라이브 카피 에셋 또는 폴더에 &#39;라이브 카피&#39;가 표시됩니다. 폴더의 라이브 카피를 쉽게 식별할 수 있습니다.

## [!DNL Assets]과(와) [!DNL Sites]의 MSM 비교 {#comparison}

더 많은 시나리오에서 [!DNL Assets]에 대한 MSM은 Sites 기능에 대한 MSM의 동작과 일치합니다. 몇 가지 주요 차이점은 다음과 같습니다.

* [!DNL Sites]에 대한 MSM의 블루프린트를 [!DNL Assets]에 대한 MSM의 Live Copy 소스라고 합니다.
* Sites에서는 블루프린트와 해당 Live Copy를 비교할 수 있지만 [!DNL Assets]에서는 원본을 Live Copy와 비교할 수 없습니다.
* [!DNL Assets]에서 Live Copy를 편집할 수 없습니다.
* 사이트에 일반적으로 하위 항목이 있지만 [!DNL Assets]에는 없습니다. 개별 에셋의 라이브 카피를 만들 때 하위 항목을 포함하거나 제외하는 옵션이 표시되지 않습니다.
* [!DNL Assets]에 대한 MSM에서는 사이트 만들기 마법사의 챕터 단계 제거가 지원되지 않습니다.
* [!DNL Assets]에 대한 MSM에서는 페이지 속성에 대한 MSM 잠금 구성이 지원되지 않습니다.
* [!DNL Assets]에 대한 MSM의 경우 **[!UICONTROL 표준 롤아웃 구성]**&#x200B;만 사용하십시오. 다른 롤아웃 구성은 [!DNL Assets]의 MSM에 사용할 수 없습니다.

>[!NOTE]
>
>**[!UICONTROL Assets]** 콘솔을 통해 액세스하는 콘텐츠 조각용 MSM은 Assets 기능을 사용합니다. 이는 해당 콘텐츠가 Assets(사이트 기능으로 간주되지만)로 저장되기 때문입니다.

## [!DNL Assets]에 대한 MSM의 제한 사항 및 알려진 문제 {#limitations}

[!DNL Assets]에 대한 MSM의 제한 사항은 다음과 같습니다.

* MSM은 메타데이터 원본에 쓰기 기능이 활성화된 상태에서 작동하지 않습니다. 원본에 쓰기 시 상속이 중단됩니다.

**추가 참조**

* [자산 번역](translate-assets.md)
* [Assets HTTP API](mac-api-assets.md)
* [자산이 지원되는 파일 형식](file-format-support.md)
* [자산 검색](search-assets.md)
* [연결된 자산](use-assets-across-connected-assets-instances.md)
* [자산 보고서](asset-reports.md)
* [메타데이터 스키마](metadata-schemas.md)
* [자산 다운로드](download-assets-from-aem.md)
* [메타데이터 관리](manage-metadata.md)
* [검색 패싯](search-facets.md)
* [컬렉션 관리](manage-collections.md)
* [일괄 메타데이터 가져오기](metadata-import-export.md)
* [콘텐츠 조각을 사용하여 작업](/help/assets/content-fragments/content-fragments.md)
* [AEM 및 Dynamic Media에 자산 게시](/help/assets/publish-assets-to-aem-and-dm.md)