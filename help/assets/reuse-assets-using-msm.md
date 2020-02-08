---
title: MSM을 사용하여 에셋 재사용
description: 상위 자산에서 파생되고 상위 자산에 연결된 여러 페이지/폴더에서 자산을 사용합니다. 에셋은 마스터 복사본과 동기화되고 몇 번의 클릭만으로 상위 에셋으로부터 업데이트를 받을 수 있습니다.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 991d4900862c92684ed92c1afc081f3e2d76c7ff

---


# MSM을 사용하여 에셋 재사용{#reuse-assets-using-msm-for-assets}

AEM(Adobe Experience Manager)의 MSM(Multi Site Manager) 기능을 사용하면 한 번 제작되고 여러 웹 위치에서 다시 사용되는 컨텐츠를 재사용할 수 있습니다. MSM for Assets 기능과 동일한 기능을 디지털 자산에 사용할 수 있습니다. 자산에 대한 MSM을 사용하여 다음을 수행할 수 있습니다.

* 자산을 한 번 만든 다음 이러한 자산의 사본을 만들어 사이트의 다른 영역에서 재사용할 수 있습니다.
* 여러 사본을 동기화하고 원본 마스터 사본을 한 번 업데이트하여 변경 사항을 하위 복사본으로 푸시합니다.
* 상위 자산과 하위 자산 간의 연결을 일시적으로 또는 영구적으로 일시 중단하여 로컬 변경을 수행합니다.

## 이점 및 개념 이해 {#concepts}

### 작동 방식과 이점 {#how-it-works-and-the-benefits}

AEM 파섹 유지 관리 연결을 통해 중앙 집중식 변경 사항을 여러 Live Copy로 푸시할 수 있습니다. 이렇게 하면 복제 사본 관리의 제한 사항을 그대로 유지하면서 더욱 빠르게 업데이트할 수 있습니다. 변경 사항의 전달은 오류 없이 중앙에서 이루어집니다. 이 기능을 사용하면 선택한 Live Copy로 제한된 업데이트를 사용할 수 있습니다. 사용자는 상속이 단절된 연결을 분리하고 다음에 마스터 사본을 업데이트하고 변경 내용을 롤아웃할 때 덮어쓰지 않은 로컬 편집을 수행할 수 있습니다. 일부 특정 메타데이터 필드 또는 전체 자산에 대해 분리할 수 있습니다. 마스터 복사본에서 원래 상속된 에셋을 로컬에서 유연하게 업데이트할 수 있습니다.

MSM 파섹

* 소스 에셋에 대한 변경 사항은 Live Copy에도 적용(롤아웃)되므로 Live Copy는 소스와 동기화됩니다.
* 라이브 관계를 일시 중단하거나 일부 제한된 필드에 대한 상속을 제거하여 Live Copy를 업데이트할 수 있습니다. 소스 수정 사항은 더 이상 Live Copy에 적용되지 않습니다.

### MSM for Assets 용어 설명 {#glossary}

**출처** 원본 자산 또는 폴더입니다. Live Copy가 파생되는 마스터 복사본입니다.

**Live copy** 소스 에셋/폴더와 해당 소스와 동기화되는 복사본. Live Copy는 추가 Live Copy의 소스가 될 수 있습니다. LC를 만드는 방법을 살펴보십시오.

**상속** Live Copy 자산/폴더와 시스템에서 업데이트를 보낼 위치를 기억하는 데 사용하는 소스 간의 링크/참조입니다. 상속은 메타데이터 필드에 대한 세부 수준으로 존재합니다. 소스와 Live Copy 간의 라이브 관계를 유지하면서 선택적 메타데이터 필드에 대한 상속을 제거할 수 있습니다.

**롤아웃** 소스 다운스트림을 수정한 내용을 Live Copy로 푸시하는 작업입니다. 롤아웃 작업을 사용하여 한 번에 하나 이상의 Live Copy를 업데이트할 수 있습니다. 롤아웃을 참조하십시오.

**롤아웃 구성** 동기화할 속성, 방법 및 시기를 결정하는 규칙입니다. 이러한 구성은 Live Copy를 만들 때 적용됩니다.나중에 편집할 수 있습니다.하위 멤버는 상위 자산에서 롤아웃 구성을 상속할 수 있습니다. MSM for Assets의 경우 표준 롤아웃 구성만 사용하십시오. MSM for Assets에서는 다른 롤아웃 구성을 사용할 수 없습니다.

**동기화** 롤아웃 외에 소스 및 Live Copy 간에 업데이트를 소스에서 Live Copy로 전송하여 동등성을 제공하는 다른 작업을 수행할 수 있습니다. 특정 Live Copy에 대한 동기화가 시작되어 소스에서 변경 내용을 가져옵니다. 이 작업을 사용하면 Live Copy 중 하나만 업데이트할 수 있습니다. 동기화 작업을 참조하십시오.

**일시 중단** Live Copy와 소스 에셋/폴더 간의 라이브 관계를 일시적으로 제거합니다. 관계를 다시 시작할 수 있습니다. 일시 중단 작업을 참조하십시오.

**다시 시작** Live Copy가 소스로부터 업데이트를 다시 받기 시작하도록 라이브 관계를 다시 시작합니다. 다시 시작 작업을 참조하십시오.

**재설정** 작업을 수행하면 Live Copy가 로컬 변경 사항을 덮어써서 다시 소스의 복제본으로 됩니다. 또한 상속을 취소하고 모든 메타데이터 필드에 대한 상속을 재설정합니다. 나중에 로컬 수정을 수행하려면 특정 필드의 상속을 다시 취소해야 합니다. LC의 로컬 수정 사항을 참조하십시오.

**분리** Live Copy 자산/폴더의 라이브 관계를 완전히 제거할 수 있습니다. 작업을 분리하면 Live Copy는 소스로부터 업데이트를 받을 수 없으며 더 이상 Live Copy가 되지 않습니다. 관계 제거를 참조하십시오.

## 자산의 Live Copy 만들기 {#createlc}

하나 이상의 소스 자산 또는 폴더에서 Live Copy를 만들려면 다음 중 하나를 수행합니다.

* 방법 1:소스 에셋을 선택하고 맨 **[!UICONTROL 위에 있는 도구 모음에서 만들기]** > Live Copy를 클릭합니다.

* 방법 2:AEM 사용자 인터페이스에서 **[!UICONTROL 만들기 >]** Live Copy를 인터페이스 오른쪽 상단 모서리에서 클릭합니다.

자산 또는 폴더의 Live Copy를 한 번에 하나씩 만들 수 있습니다. 자산이나 Live Copy 자체인 폴더에서 파생된 Live Copy를 만들 수 있습니다.  사용 사례에는 컨텐츠 조각(CF)이 지원되지 않습니다. Live Copy를 만들려고 하면 CF가 관계 없이 그대로 복사됩니다. 복사된 CF는 시간 내 스냅샷이며 원본 CF가 업데이트될 때 업데이트되지 않습니다.

첫 번째 방법을 사용하여 Live Copy를 만들려면 다음 단계를 수행합니다.

1. 소스 자산 또는 폴더를 선택합니다. 도구 모음에서 만들기 > **[!UICONTROL Live Copy를 클릭합니다]**.

   ![AEM 인터페이스에서 Live Copy 만들기](assets/create_lc1.png)

   AEM 인터페이스에서 Live Copy 만들기

1. 대상 폴더를 선택합니다. **[!UICONTROL 다음]**&#x200B;을 클릭합니다.
1. 제목과 이름을 입력합니다. 자산에 하위 항목이 없습니다. 폴더의 Live Copy를 만들 때 하위 폴더를 포함하거나 제외하도록 선택할 수 있습니다.
1. 롤아웃 구성을 선택합니다. **[!UICONTROL 만들기]**&#x200B;를 클릭합니다.

두 번째 방법을 사용하여 Live Copy를 만들려면 다음 단계를 수행합니다.

1. AEM 인터페이스의 오른쪽 위 모서리에서 만들기 > **[!UICONTROL Live Copy를 클릭합니다]**.

   ![AEM 인터페이스에서 Live Copy 만들기](assets/create_lc2.png)

   AEM 인터페이스에서 Live Copy 만들기

1. 소스 자산 또는 폴더를 선택합니다. **[!UICONTROL 다음]**&#x200B;을 클릭합니다.
1. 대상 폴더를 선택합니다. **[!UICONTROL 다음]**&#x200B;을 클릭합니다.
1. 제목과 이름을 입력합니다. 자산에 하위 항목이 없습니다. 폴더의 Live Copy를 만들 때 하위 폴더를 포함하거나 제외하도록 선택할 수 있습니다.
1. 롤아웃 구성을 선택합니다. **[!UICONTROL 만들기]**&#x200B;를 클릭합니다.

>[!NOTE]
>
>소스 또는 Live Copy가 이동되면 관계는 유지됩니다. Live Copy가 삭제되면 관계가 제거됩니다.

## 소스 및 Live Copy의 다양한 속성과 상태 보기 {#properties}

관계, 동기화, 롤아웃 등과 같은 Live Copy의 정보 및 MSM 관련 상태를 AEM 사용자 인터페이스의 다양한 영역에서 볼 수 있습니다.

자산 및 폴더에는 다음 두 가지 방법이 작동합니다.

* Live Copy 자산을 선택하고 속성 페이지에서 정보를 찾습니다.
* 소스 폴더를 선택하고 Live Copy 콘솔에서 각 Live Copy의 세부 정보를 찾습니다.

**팁**:몇 개의 개별 Live Copy의 상태를 확인하려면 속성 페이지를 보는 첫 번째 방법을 사용합니다. 많은 Live Copy의 상태를 확인하려면 두 번째 방법, 즉 관계 상태 **[!UICONTROL 페이지를 참조하십시오]** .

### Live Copy 정보 및 상태 {#statuslcasset}

Live Copy 자산 또는 폴더의 정보 및 상태를 확인하려면 다음 단계를 따르십시오.

1. Live Copy 자산 또는 폴더를 선택합니다. Click **[!UICONTROL Properties]** from the toolbar. 또는 키보드 단축키를 `p`사용합니다.
1. Live **[!UICONTROL Copy를 클릭합니다]**. 소스 경로, 일시 중단 상태, 동기화 상태, 마지막 롤아웃 날짜 및 마지막 롤아웃을 수행한 사용자를 확인할 수 있습니다.

   ![Live Copy 정보 및 상태는 속성의 콘솔에 표시됩니다.](assets/lcfolder_info_properties.png)

   Live Copy 정보 및 상태

1. 하위 자산이 Live Copy 구성을 대여하는 경우 활성화하거나 비활성화할 수 있습니다.

1. Live Copy에 대한 옵션을 선택하여 상위 항목에서 롤아웃 구성을 상속하거나 구성을 변경할 수 있습니다.

### 폴더의 모든 Live Copy 정보 및 상태 {#statuslcfolder}

AEM에서는 소스 폴더의 모든 Live Copy의 동체를 확인할 수 있는 콘솔을 제공합니다. 이 콘솔에는 모든 하위 자산의 상태가 표시됩니다.

1. 소스 폴더를 선택합니다. Click **[!UICONTROL Properties]** from the toolbar. 또는 키보드 단축키를 `p`사용합니다.
1. Live **[!UICONTROL Copy 소스를 클릭합니다]**. 콘솔을 열려면 Live Copy **[!UICONTROL 개요를 클릭합니다]**. 이 대시보드는 모든 하위 자산의 최상위 상태를 제공합니다.

   ![소스의 Live Copy 콘솔에서 Live Copy 상태 보기](assets/livecopy_statuses.png)

   소스의 Live Copy 콘솔에서 Live Copy 상태 보기

1. Live Copy 폴더의 각 자산에 대한 세부 정보를 보려면 자산을 선택하고 도구 모음에서 **[!UICONTROL 관계]** 상태를 클릭합니다.

   ![폴더에 있는 Live Copy 하위 자산의 세부 정보 및 상태](assets/livecopy_relationship_status.png)

   폴더에 있는 Live Copy 하위 자산의 세부 정보 및 상태

**팁**:너무 많이 검색하지 않고도 다른 폴더의 Live Copy 상태를 빠르게 볼 수 있습니다. Live Copy 개요 인터페이스의 위쪽 중간에 있는 팝업 목록에서 폴더를 **[!UICONTROL 변경하면]** 됩니다.

### 소스에 대한 참조 레일의 빠른 작업 {#refrailsource}

소스 에셋 또는 폴더의 경우 다음 정보를 확인하고 참조 레일에서 바로 다음 작업을 수행할 수 있습니다.

* Live Copy 경로 보기
* AEM 사용자 인터페이스에서 특정 Live Copy를 열거나 표시합니다.
* 업데이트를 특정 Live Copy에 동기화합니다.
* 특정 Live Copy에 대한 관계를 일시 중단하거나 롤아웃 구성을 변경합니다.
* Live Copy 개요 콘솔에 액세스합니다.

소스 에셋 또는 폴더를 선택하고 왼쪽 레일을 열고 참조를 **[!UICONTROL 클릭합니다]**. 또는 자산 또는 폴더를 선택하고 키보드 단축키를 `Alt + 4`사용합니다.  ![선택한 소스에 대한 참조 레일에서 사용할 수 있는 작업 및 정보](assets/referencerail_source.png)

선택한 소스에 대한 참조 레일에서 사용할 수 있는 작업 및 정보

특정 Live Copy의 경우 Live Copy **[!UICONTROL 편집을 클릭하여]** 관계를 일시 중단하거나 롤아웃 구성을 변경합니다.

![특정 Live Copy의 경우 소스 에셋을 선택하면 참조 레일에서 관계를 일시 중단하거나 롤아웃 구성을 변경할 수 있습니다](assets/referencerail_editlc_options.png)

관계 일시 중단 또는 특정 Live Copy 롤아웃 구성 변경

### Live Copy에 대한 참조 레일의 빠른 작업 {#refraillc}

Live Copy 자산 또는 폴더의 경우 다음 정보를 확인하고 참조 레일에서 바로 다음 작업을 수행할 수 있습니다.

* 소스 경로를 참조하십시오.
* AEM 사용자 인터페이스에서 특정 Live Copy를 열거나 표시합니다.
* 업데이트를 롤아웃합니다.

Live Copy 자산 또는 폴더를 선택하고 왼쪽 레일을 열고 참조를 **[!UICONTROL 클릭합니다]**. 또는 자산 또는 폴더를 선택하고 키보드 단축키를 `Alt + 4`사용합니다.  ![선택한 Live Copy에 대한 참조 레일에서 사용할 수 있는 작업](assets/referencerail_livecopy.png)

선택한 Live Copy에 대한 참조 레일에서 사용할 수 있는 작업

## 소스에서 Live Copy로 수정 내용 전달 {#rolloutsync}

소스가 수정되면 동기화 작업 또는 롤아웃 작업을 사용하여 변경 사항을 Live Copy에 전파할 수 있습니다. 두 작업 간의 차이점을 이해하려면 [용어집을](#glossary)참조하십시오.

### 롤아웃 작업 {#rollout}

소스 자산에서 롤아웃 작업을 시작하고 전체 또는 일부 선택한 Live Copy를 업데이트할 수 있습니다.

1. Live Copy 자산 또는 폴더를 선택합니다. Click **[!UICONTROL Properties]** from the toolbar. 또는 키보드 단축키를 `p`사용합니다.
1. Live **[!UICONTROL Copy 소스를 클릭합니다]**. 맨 **[!UICONTROL 위에]** 있는 도구 모음에서 롤아웃을 클릭합니다.

1. 업데이트할 Live Copy를 선택합니다. 롤아웃을 **[!UICONTROL 클릭합니다]**.

   하위 자산에 대한 업데이트를 롤아웃하려면 롤아웃 소스 **[!UICONTROL 및 모든 하위 항목을 선택합니다]**.

   ![소스 수정 내용을 일부 또는 전체 Live Copy로 롤아웃합니다.](assets/livecopy_rollout_page.png)

   소스 수정 내용을 일부 또는 전체 Live Copy로 롤아웃합니다.

>[!NOTE]
>
>소스 자산에서 변경한 내용은 직접 관련된 Live Copy에만 롤아웃됩니다. Live Copy가 다른 Live Copy에서 파생된 경우, 수정된 내용이 파생된 Live Copy로 롤아웃되지 않습니다.

또는 특정 Live Copy를 선택한 후 참조 레일에서 롤아웃 작업을 시작할 수 있습니다. 자세한 내용은 Live Copy [에](#refraillc)대한 참조 레일의 빠른 작업을 참조하십시오. 이 롤아웃 방식에서는 선택한 Live Copy 및 선택적으로 해당 하위 Live Copy만 업데이트됩니다.

![소스 수정 내용을 선택한 Live Copy에 롤아웃합니다.](assets/livecopy_rollout_dialog.png)

소스 수정 내용을 선택한 Live Copy에 롤아웃합니다.

### 동기화 작업 정보 {#aboutsync}

동기화 작업은 소스 수정 내용을 선택한 Live Copy로만 가져옵니다. 동기화 작업은 상속을 취소한 후 수행한 로컬 수정 사항을 존중하고 유지합니다. 로컬 수정 내용을 덮어쓰지 않고 취소된 상속이 다시 설정되지 않습니다. 세 가지 방법으로 동기화 작업을 시작할 수 있습니다.

<table>
 <tbody>
  <tr>
   <th><strong>AEM 인터페이스의 위치</strong><br /> </th>
   <th><strong>사용 시기 및 이유</strong><br /> </th>
   <th><strong>사용 방법</strong><br /> </th>
  </tr>
  <tr>
   <td>참조 레일</td>
   <td>소스를 이미 선택한 경우 신속하게 동기화할 수 있습니다.<br /> </td>
   <td>소스에 <a href="#refrailsource">대한 참조 레일의 빠른 작업 참조</a></td>
  </tr>
  <tr>
   <td>속성 페이지의 도구 모음<br /> </td>
   <td>Live Copy 속성이 이미 열려 있으면 동기화를 시작합니다.<br /> </td>
   <td>Live <a href="#synclc">Copy 동기화 참조</a></td>
  </tr>
  <tr>
   <td>Live Copy 개요 콘솔</td>
   <td>소스 폴더를 선택하거나 Live Copy 개요 콘솔이 이미 열려 있을 때 여러 에셋을 신속하게 동기화할 수 있습니다(반드시 전체 에셋은 아님). 한 번에 한 자산에 대해 동기화 작업이 시작되지만 한 번에 여러 자산에 대해 보다 빠르게 동기화할 수 있습니다.<br /> </td>
   <td>Live <a href="#bulkactions">Copy 폴더에 있는 많은 자산에 대한 작업을 참조하십시오.</a></td>
  </tr>
 </tbody>
</table>

### Live Copy 동기화 {#synclc}

동기화 작업을 시작하려면 Live **[!UICONTROL Copy의]** 속성 **[!UICONTROL 페이지를 열고 Live]** Copy를클릭한 다음 도구 모음에서 원하는 작업을 클릭합니다.

동기화 작업과 관련된 상태 및 정보를 보려면 Live Copy [의 정보](#statuslcasset) 및 상태와 폴더의 [모든 Live Copy](#statuslcfolder)의 정보 및 상태를 참조하십시오.

![동기화 작업은 변경 내용을 소스에 가져옵니다.](assets/livecopy_sync.png)

동기화 작업은 변경 내용을 소스에 가져옵니다.

>[!NOTE]
>
>관계가 일시 중단된 경우, 동기화 작업은 도구 모음에서 사용할 수 없습니다. 동기화 작업을 참조 레일에서 사용할 수 있지만, 수정 사항은 성공적인 롤아웃 시에도 전파되지 않습니다.

## 관계 일시 중단 및 다시 시작 {#suspendresume}

Live Copy가 소스 에셋 또는 폴더에 대한 수정 내용을 수신하지 못하도록 관계를 일시적으로 중단할 수 있습니다. 또한 Live Copy에서 소스에서 수정 내용을 받기 위해 관계를 다시 시작할 수 있습니다.

일시 중단하거나 다시 시작하려면 **[!UICONTROL Live]** Copy의 속성 페이지를 열고 **[!UICONTROL Live Copy를]** 클릭한 다음 도구 모음에서 원하는 작업을 클릭합니다.

또는 Live Copy 개요 콘솔에서 Live Copy 폴더에 있는 여러 자산의 관계를 신속하게 일시 중단하거나 다시 시작할 **[!UICONTROL 수]** 있습니다. Live [Copy 폴더의](#bulkactions)많은 자산에 대한 작업 수행을 참조하십시오.

## Live Copy의 로컬 수정 {#localmods}

Live Copy는 원본 소스를 만들 때 원본 소스의 복제본입니다. Live Copy의 메타데이터 값은 소스에서 상속됩니다. 메타데이터 필드는 소스 자산의 각 필드와 함께 상속을 개별적으로 유지합니다.

그러나 일부 선택 속성을 변경할 수 있도록 Live Copy를 로컬에서 수정할 수 있습니다. 로컬 수정을 수행하려면 원하는 속성의 상속을 취소합니다. 하나 이상의 메타데이터 필드의 상속이 취소되면 자산의 라이브 관계와 다른 메타데이터 필드의 상속이 유지됩니다. 모든 동기화 또는 롤아웃은 로컬 수정 사항을 덮어쓰지 않습니다. 이렇게 하려면 **[!UICONTROL Live Copy]** 자산의 속성 페이지를 열고 메타데이터 필드 옆에 있는 상속 **** 취소 아이콘을 클릭합니다.

모든 로컬 수정 사항을 실행 취소하고 에셋을 소스 상태로 되돌릴 수 있습니다. 동작을 완전히 재설정하고 모든 로컬 수정 사항을 즉시 재정의하고 모든 메타데이터 필드에 상속을 재설정합니다. 되돌리려면 Live Copy **[!UICONTROL 자산의]** 속성 페이지에서 도구 **[!UICONTROL 모음에서 재설정을]** 클릭합니다.

![재설정 작업은 로컬 편집을 덮어쓰고 Live Copy를 소스와 함께 가져옵니다.](assets/livecopy_reset.png)

재설정 작업은 로컬 편집을 덮어쓰고 Live Copy를 소스와 함께 가져옵니다.

## 라이브 관계 제거 {#detach}

분리 작업을 사용하여 소스와 Live Copy 간의 관계를 완전히 제거할 수 있습니다. Live Copy가 분리된 후 독립 실행형 자산 또는 폴더가 됩니다. 분리 후 즉시 AEM 인터페이스에 새 자산으로 표시됩니다. Live Copy를 소스에서 분리하려면 다음 단계를 따르십시오.

1. Live Copy 자산 또는 폴더를 선택합니다. Click **[!UICONTROL Properties]** from the toolbar. 또는 키보드 단축키를 `p`사용합니다.

1. Live **[!UICONTROL Copy를 클릭합니다]**. 도구 **[!UICONTROL 모음에서]** 분리를 클릭합니다. 표시된 **[!UICONTROL 대화]** 상자에서 분리를 클릭합니다.

   ![작업을 분리하면 원본과 Live Copy 간의 관계가 완전히 제거됩니다.](assets/livecopy_detach.png)

   작업을 분리하면 원본과 Live Copy 간의 관계가 완전히 제거됩니다.

   >[!CAUTION]
   >
   >대화 상자에서 분리를 클릭하면 바로 **[!UICONTROL 관계가]** 제거됩니다. 속성 페이지에서 취소를 클릭하여 **[!UICONTROL 취소할]** 수 없습니다.

또는 Live Copy 개요 콘솔에서 Live Copy 폴더에 있는 여러 자산을 신속하게 분리할 **[!UICONTROL 수]** 있습니다. Live [Copy 폴더의](#bulkactions)많은 자산에 대한 작업 수행을 참조하십시오.

## Live Copy 폴더의 많은 에셋에 대한 작업 수행 {#bulkactions}

하나의 Live Copy 폴더에 여러 개의 자산이 있는 경우 각 자산에 대해 작업을 시작하는 것은 지루할 수 있습니다. Live Copy 콘솔에서 여러 자산에 대한 기본 작업을 신속하게 시작할 수 있습니다. 위의 메서드는 개별 자산에 대해 계속 작동합니다.

1. 소스 폴더를 선택합니다. Click **[!UICONTROL Properties]** from the toolbar. 또는 키보드 단축키를 `p`사용합니다.
1. Live **[!UICONTROL Copy 소스를 클릭합니다]**. 콘솔을 열려면 Live Copy **[!UICONTROL 개요를 클릭합니다]**.

1. 이 대시보드의 Live Copy 폴더에서 Live Copy 자산을 선택합니다. 도구 모음에서 원하는 작업을 클릭합니다. 사용 가능한 작업은 **[!UICONTROL 동기화]**, **[!UICONTROL 재설정]**, **[!UICONTROL 일시 중단]**&#x200B;및 **[!UICONTROL Detach]**&#x200B;입니다.

   선택한 소스 폴더와 라이브 관계에 있는 Live Copy 폴더의 모든 자산에서 이러한 작업을 신속하게 시작할 수 있습니다.

   ![Live Copy 개요 콘솔에서 Live Copy 폴더의 많은 에셋을 손쉽게 업데이트](assets/livecopyconsole_update_many_assets.png)

   Live Copy 개요 콘솔에서 Live Copy 폴더의 많은 에셋을 손쉽게 업데이트

<!--
## Extend MSM for Assets {#extendapi}

AEM allows you to extend the functionality using the MSM Java APIs. For Assets, the extending works just the same as it works with MSM for Site. For details, see [Extending the MSM](/help/sites-developing/extending-msm.md) and the following for information about specific tasks:

* [Overview of APIs](/help/sites-developing/extending-msm.md#overview-of-the-java-api)

* [Create a new synchronization action](/help/sites-developing/extending-msm.md#creating-a-new-synchronization-action)
* [Create a new rollout configuration](/help/sites-developing/extending-msm.md#creating-a-new-rollout-configuration)

* [Create and use a simple LiveActionFactory class](/help/sites-developing/extending-msm.md#creating-and-using-a-simple-liveactionfactory-class)

>[!NOTE]
>
>* Blueprint in MSM for Site is called Live Copy source in MSM for Assets.
>* Removing the chapters step in the create site wizard is not supported in MSM for Assets.
>* Configuring MSM locks on page properties (Touch-enabled UI) is not supported in MSM for Assets.

-->

## 자산 관리 작업이 Live Copy에 미치는 영향 {#manageassets}

Live Copy와 소스는 디지털 자산으로서 어느 정도 관리할 수 있는 자산 또는 폴더입니다. AEM 파섹

* Live Copy를 복사하면 첫 번째 Live Copy와 동일한 소스의 Live Copy 에셋이 만들어집니다.
* 소스 또는 Live Copy를 이동하면 라이브 관계가 유지됩니다.
* Live Copy 자산에 대해 편집 작업이 작동하지 않습니다. Live Copy의 소스가 Live Copy 자체인 경우 편집 작업이 작동하지 않습니다.
* Live Copy 자산에는 체크 아웃 작업을 사용할 수 없습니다.
* 소스 폴더의 경우 검토 작업을 만드는 옵션을 사용할 수 있습니다.
* 목록 보기 및 열 보기에서 자산 목록을 볼 때 Live Copy 자산 또는 폴더에 대해 &#39;live copy&#39;가 표시됩니다. 이렇게 하면 폴더에서 Live Copy를 쉽게 식별할 수 있습니다.

## 자산 및 사이트에 대한 MSM 비교 {#comparison}

더 많은 시나리오에서, MSM for Assets는 MSM for Sites 기능과 일치합니다. 다음과 같은 주요 차이점이 있습니다.

* MSM for Site의 블루프린트는 MSM의 Live Copy 소스 for Assets라고 합니다.
* 사이트에서는 블루프린트와 Live Copy를 비교할 수 있지만 Assets에서는 소스를 Live Copy와 비교할 수 없습니다.
* 자산에서는 Live Copy를 편집할 수 없습니다.
* 사이트에는 대개 하위 항목이 있지만 자산은 그렇지 않습니다. 개별 자산의 Live Copy를 만들 때 하위 항목을 포함하거나 제외하는 옵션이 없습니다.
* 사이트 만들기 마법사의 장 제거 단계는 MSM for Assets에서 지원되지 않습니다.
* 페이지 속성(터치가 활성화된 UI)에서 MSM 잠금 구성은 자산의 MSM에서 지원되지 않습니다.
* MSM for Assets의 경우 표준 **[!UICONTROL 롤아웃 구성만]**&#x200B;사용하십시오. MSM for Assets에서는 다른 롤아웃 구성을 사용할 수 없습니다.

## Best practices {#bestpractices}

MSM에 대한 일부 우수 사례는 다음과 같습니다.

* 구현을 시작하기 전에 자산 및 컨텐츠 흐름의 상위-하위 관계를 계획합니다.
* 

## MSM for Assets의 제한 및 알려진 문제 {#limitations}

다음은 자산에 대한 MSM의 제한 사항입니다.

* 사용 사례에는 컨텐츠 조각(CF)이 지원되지 않습니다. Live Copy를 만들려고 하면 CF가 관계 없이 그대로 복사됩니다. 복사된 CF는 시간 내 스냅샷이며 원본 CF가 업데이트될 때 업데이트되지 않습니다.

