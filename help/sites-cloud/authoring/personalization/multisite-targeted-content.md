---
title: 다중 사이트에서 타깃팅된 컨텐츠 작업
description: 사이트 간 활동, 경험 및 오퍼와 같은 타깃팅된 컨텐츠를 관리해야 하는 경우 타깃팅된 컨텐츠에 대한 AEM의 내장 다중 사이트 지원을 이용할 수 있습니다.
translation-type: tm+mt
source-git-commit: 16725342c1a14231025bbc1bafb4c97f0d7cfce8

---


# 다중 사이트에서 타깃팅된 컨텐츠 작업 {#working-with-targeted-content-in-multisites}

사이트 간 활동, 경험 및 오퍼와 같은 타깃팅된 컨텐츠를 관리해야 하는 경우 타깃팅된 컨텐츠에 대한 AEM의 내장 다중 사이트 지원을 이용할 수 있습니다.

>[!NOTE]
>
>타깃팅된 컨텐츠에 대한 다중 사이트 작업 지원은 고급 기능입니다. 이 기능을 사용하려면 다중 사이트 관리자와 AEM에 통합된 Adobe Target에 익숙해야 합니다.
<!--
>Working with Multisite support for targeted content is an advanced feature. To use this feature, you should be familiar with [Multi Site Manager](/help/sites-administering/msm.md) and the [Adobe Target integration](/help/sites-administering/target.md) with AEM.
-->

이 문서에서는 다음 사항에 대해 설명합니다.

* 타깃팅된 컨텐츠에 대한 AEM의 다중 사이트 지원에 대한 간략한 개요를 제공합니다.
* 사이트(하나의 브랜드에 있음)를 연결할 수 있는 방법에 대한 몇 가지 가능한 사용 시나리오에 대해 설명합니다.
* 마케터가 이 기능을 사용하는 방법에 대한 예제 연습을 제공합니다.
* 타깃팅된 컨텐츠를 위해 다중 사이트 지원을 구현하는 방법에 대한 자세한 지침

사이트가 개인화된 컨텐츠를 공유하는 방식을 설정하려면 다음 절차를 수행해야 합니다.

1. [새 영역을 만들거나](#creating-new-areas) [새 영역을 Live Copy로 만듭니다](#creating-new-areas). 영역에는 구성 요소가 타깃팅되는 위치인 페이지의 *영역*&#x200B;에 사용할 수 있는 모든 활동이 포함됩니다. 새 영역을 만들면 비어 있는 영역이 만들어지지만 새 영역을 Live Copy로 만들면 사이트 구조를 통해 컨텐츠를 상속할 수 있습니다.

1. 영역에 [사이트 또는 페이지를 연결](#linking-sites-to-an-area)합니다.

상속은 언제든지 일시 중단하거나 복원할 수 있습니다. 또한 상속을 일시 중단하지 않으려는 경우에는 로컬 경험을 만들 수도 있습니다. 기본적으로, 모든 페이지에서는 별도로 지정하지 않는 한 마스터 영역을 사용합니다.

## 타깃팅된 컨텐츠에 대한 다중 사이트 지원 소개 {#introduction-to-multisite-support-for-targeted-content}

타깃팅된 컨텐츠에 대한 다중 사이트 지원은 즉시 사용할 수 있으며, MSM을 통해 관리하는 마스터 페이지의 타깃팅된 컨텐츠를 로컬 Live Copy에 푸시하거나 이러한 컨텐츠의 전역 및 로컬 수정 사항을 관리할 수 있도록 해줍니다.

You manage this in an **Area**. 사이트는 다른 사이트에서 사용되는 타깃팅된 컨텐츠(활동, 경험 및 오퍼)를 구분하고 사이트 상속과 함께 타깃팅된 컨텐츠의 상속을 생성하고 관리하는 MSM 기반 메커니즘을 제공합니다. 따라서 6.2 이전 AEM에서와 달리 타깃팅된 컨텐츠를 상속된 사이트에서 다시 만들 필요가 없습니다.

영역에서는 해당 영역에 연결된 활동만 Live Copy에 푸시됩니다. 기본적으로 [마스터 영역]이 선택됩니다. 추가 영역을 만든 후 만들어진 영역을 사이트나 페이지에 연결하여 푸시되는 타깃팅된 컨텐츠를 가리킬 수 있습니다.

사이트나 Live Copy는 해당 사이트나 Live Copy에서 사용 가능해야 하는 활동을 포함하는 영역에 연결합니다. 기본적으로 사이트나 Live Copy는 마스터 영역에 연결되지만 마스터 영역 이외의 다른 영역도 연결할 수 있습니다.

>[!NOTE]
>
>타깃팅된 컨텐츠에 대한 다중 사이트 지원을 사용할 때에는 다음 사항에 유의해야 합니다.
>
>* 롤아웃이나 Live Copy를 사용하는 경우 MSM 라이센스가 있어야 합니다.
>* Adobe Target에 대한 동기화를 사용하는 경우 Adobe Target 라이센스가 있어야 합니다.
>



## 사용 사례 {#use-cases}

사용 사례에 따라 다양한 방법으로 타깃팅된 컨텐츠에 대한 다중 사이트 지원을 설정할 수 있습니다. 이 섹션에서는 이 지원이 어떻게 하나의 브랜드에 이론적으로 실행되는지를 설명합니다. In addition, in [Example: Targeting Content Based on Geography](#example-targeting-content-based-on-geography), you can see a real-world application of targeting content in multiple sites.

타깃팅된 컨텐츠는 사이트 또는 페이지의 범위를 정의하는 이른 바 영역이란 것으로 둘러싸여 있습니다. 이러한 영역은 브랜드 수준에서 정의되며, 하나의 브랜드는 여러 영역을 포함할 수 있습니다. 영역은 브랜드 간에 구별될 수 있습니다. 하나의 브랜드는 마스터 영역만 포함할 수도 있고 따라서 모든 브랜드에서 공유되는 반면, 또 다른 브랜드는 여러 브랜드(예를 들어, 영역별로)를 포함할 수도 있습니다. 따라서 브랜드는 브랜드 간에 영역 세트를 미러링할 필요가 없습니다.

타깃팅된 컨텐츠에 대한 다중 사이트 지원 시 다음 컨텐츠 세트 중 하나가 있는 두 개(또는 이상) 사이트가 있고 이 사이트들이 **하나**&#x200B;의 브랜드를 사용하는 경우가 있을 수 있습니다.

* 완전히 *분리된* 타깃팅된 컨텐츠 세트 - 사이트에 있는 타깃팅된 컨텐츠를 편집해도 다른 사이트에 영향을 주지 않습니다. 개별 영역에 연결하는 사이트는 자체 구성 영역에 읽고 씁니다. 예:
   * 사이트 A는 영역 X에 연결합니다.
   * 사이트 B는 영역 Y에 연결합니다.
* *공유된* 타깃팅된 컨텐츠 세트 - 사이트에 있는 타깃팅된 컨텐츠를 편집하면 두 사이트 모두가 직접적인 영향을 받습니다. 두 사이트가 동일한 영역을 참조하도록 함으로써 이렇게 설정할 수 있습니다. 동일한 영역에 연결하는 사이트는 이 영역 내에서 타깃팅된 컨텐츠를 공유합니다. 예:
   * 사이트 A는 영역 X에 연결합니다.
   * 사이트 B는 영역 X에 연결합니다.
* A distinct set of targeted content *inherited* from another site via MSM - Content can be unidirectionally rolled out from master to live copy. 예:
   * 사이트 A는 영역 X에 연결합니다.
   * 사이트 B는 영역 Y(영역 X의 Live Copy)에 연결합니다.

한 사이트에서 사용되는 **여러** 브랜드가 있을 수도 있습니다. 그럴 경우 이 예보다 더 복잡할 수 있습니다.

![다중 사이트 예](/help/sites-cloud/authoring/assets/multisite-example.png)

>[!NOTE]
>
>For a more technical look at this feature, see [How Multisite Management for Targeted Content is Structured](/help/sites-cloud/authoring/personalization/multisite-structure.md).

## 예: 지역을 기반으로 하는 컨텐츠 타깃팅 {#example-targeting-content-based-on-geography}

타깃팅된 컨텐츠용으로 다중 사이트를 사용하면 개인화 컨텐츠를 공유, 롤아웃 또는 분리할 수 있습니다. 이 기능의 사용법을 보다 잘 이해하려면 다음 시나리오와 같이 지역을 기반으로 타깃팅된 컨텐츠를 롤아웃하는 방식을 제어할 수 있는 시나리오를 생각해 보십시오.

지역에 따라 동일한 사이트에 대한 네 가지 버전이 있습니다.

* **미국** 사이트는 왼쪽 위 모서리에 있으며 마스터 사이트입니다. 이 예에서는 타깃팅 모드로 열려 있습니다.
* 이 사이트의 다른 세 버전은 **캐나다**, **영국** 및 **오스트레일리아**&#x200B;이며, 모두 Live Copy입니다. 이 사이트들은 미리 보기 모드로 열려 있습니다.

![다중 사이트 버전](/help/sites-cloud/authoring/assets/multisite-versions.png)

각 사이트는 지리적으로 서로 다른 지역에서 개인화된 컨텐츠를 공유합니다.

* 캐나다는 미국과 마스터 영역을 공유합니다.
* 영국은 유럽 영역에 연결되어 있으며 마스터 영역에서 상속을 받습니다.
* 오스트레일리아는 남반구에 있어서 계절 제품이 적용되지 않으므로 오스트레일리아만의 개인화된 컨텐츠가 있습니다.

![다중 사이트 다이어그램](/help/sites-cloud/authoring/assets/multisite-diagram.png)

북반구에서는 겨울 활동을 만들었지만 남성 대상에 속하는 북미 지역의 마케터는 겨울에 대해 다른 이미지를 원해서 미국 사이트에서 이미지를 변경합니다.

![미국 버전](/help/sites-cloud/authoring/assets/multisite-us.png)

탭을 새로 고치면 캐나다 사이트는 우리 쪽에서 아무런 작업을 하지 않아도 새 이미지로 변경됩니다. 이는 캐나다가 미국과 마스터 영역을 공유하기 때문입니다. 영국과 오스트레일리아 사이트에서는 이미지가 바뀌지 않습니다.

![버전 변경](/help/sites-cloud/authoring/assets/multisite-us-change.png)

마케터는 유럽 지역에 이러한 변경 사항을 롤아웃하려 할 것이고 **페이지 롤아웃**&#x200B;을 탭하거나 클릭하여 Live Copy를 롤아웃합니다. After refreshing the tab, the Great Britain site has the new image as the Europe area inherits from the master area (after rollout). <!--The marketer would like to roll out these changes to the European region and [rolls out the live copy](/help/sites-administering/msm-livecopy.md) by tapping or clicking **Rollout Page**. After refreshing the tab, the Great Britain site has the new image as the Europe area inherits from the master area (after rollout).-->

![Live Copy 롤아웃](/help/sites-cloud/authoring/assets/multisite-roll-out.png)

오스트레일리아 사이트의 이미지는 변경되지 않은 상태로 유지됩니다. 오스트레일리아는 여름이고 마케터는 해당 컨텐츠를 변경하고 싶지 않으므로 이것이 올바른 상태입니다. 오스트레일리아의 사이트는 다른 지역과 영역을 공유하지 않고 다른 지역의 Live Copy도 아니므로 변경되지 않습니다. 마케터는 오스트레일리아 사이트의 타깃팅된 컨텐츠가 덮어써질 것을 걱정할 필요가 없습니다.

또한 영국의 경우 영역이 마스터 영역의 Live Copy이므로 활동 이름 옆에 있는 녹색 표시로 상속 상태를 알 수 있습니다. 활동이 상속되는 경우 Live Copy를 일시 중단하거나 분리하지 않는 한 수정할 수 없습니다.

언제든지 상속을 일시 중단하거나 상속을 완전히 분리할 수 있습니다. 또한 상속을 일시 중단하지 않고도 해당 경험에서만 사용 가능한 로컬 경험을 언제든지 추가할 수 있습니다.

>[!NOTE]
>
>For a more technical look at this feature, see [How Multisite Management for Targeted Content is Structured](/help/sites-cloud/authoring/personalization/multisite-structure.md).

### 새 영역 만들기와 새 영역을 Live Copy로 만들기 비교 {#creating-a-new-area-versus-creating-a-new-area-as-livecopy}

AEM에서 새 영역을 만들거나 새 영역을 Live Copy로 만들 수 있습니다. 새 영역을 만들면 활동과 해당 활동에 속하는 오퍼, 경험 등과 같은 모든 항목이 그룹화됩니다. 타깃팅된 컨텐츠로 이루어진 완전히 구별되는 세트를 만들거나 타깃팅된 컨텐츠로 이루어진 세트를 공유하려는 경우 새 영역을 만듭니다.

그러나 두 사이트 사이에 MSM을 통해 상속을 설정했다면, 활동을 상속할 수도 있습니다. 이 경우, Live Copy인 새 영역을 만듭니다. 여기서 Y는 X의 Live Copy이므로 모든 활동도 상속합니다.

>[!NOTE]
>
>기본 롤아웃은 페이지가 페이지 블루프린트에 연결된 영역의 Live Copy인 영역에 연결하는 Live Copy일 때마다 타깃팅된 컨텐츠의 후속 롤아웃을 트리거합니다.

예를 들어, 다음 다이어그램에는 네 개의 사이트가 있으며, 여기에서 두 사이트는 마스터 영역(및 해당 영역에 속하는 모든 활동)을 공유하며, 한 사이트는 롤아웃 시 활동을 공유하도록 영역의 Live Copy인 영역을 포함하며, 한 사이트는 완전히 별개인 사이트(따라서 활동을 위한 영역이 필요)입니다.

![다이어그램 세부 사항](/help/sites-cloud/authoring/assets/multisite-diagram-detail.png)

AEM에서 이렇게 하려면 다음을 수행합니다.

* 사이트 A가 마스터 영역에 연결합니다. - 영역을 만들 필요가 없습니다. 마스터 영역은 AEM에서 기본적으로 선택됩니다. 사이트 A와 B는 활동 등을 공유합니다.
* 사이트 B가 마스터 영역에 연결합니다. - 영역을 만들 필요가 없습니다. 마스터 영역은 AEM에서 기본적으로 선택됩니다. 사이트 A와 B는 활동 등을 공유합니다.
* 사이트 C가 상속된 영역에 연결합니다. 이 영역은 마스터 영역의 Live Copy입니다. - 영역을 Live Copy로 만듭니다. 여기서 Live Copy는 마스터 영역을 기반으로 만듭니다. 상속된 영역은 롤아웃 시 마스터 영역에서 활동을 상속받습니다.
* 사이트 D가 사이트 D만의 분리된 영역에 연결합니다. - 영역을 만듭니다. 여기에서는 아직 정의된 활동이 없는 완전히 새로운 영역을 만듭니다. 분리된 영역은 다른 사이트와 활동을 공유하지 않습니다.

## 새 영역 만들기 {#creating-new-areas}

영역은 활동 및 오퍼를 포괄할 수 있습니다. 둘 중 하나(예: 활동)에서 영역을 만들면 다른 하나(예: 오퍼)에서도 이 영역을 사용할 수 있습니다.

>[!NOTE]
>
>마스터 영역이라고 하는 기본 영역은 다른 영역을 만들기 **전까지**&#x200B;는 브랜드 이름을 탭하거나 클릭하면 기본적으로 축소됩니다. 그런 다음 **활동**&#x200B;이나 **오퍼** 콘솔에서 브랜드를 선택하면 **영역** 콘솔이 표시됩니다.

새 영역을 만들려면 다음을 수행하십시오.

1. Navigate to **Personalization** > **Activities** or **Offers** or and then to your brand.
1. **영역 만들기**&#x200B;를 탭하거나 클릭합니다.

   ![영역 만들기](/help/sites-cloud/authoring/assets/multisite-create-area.png)

1. **영역** 아이콘을 클릭하고 **다음**&#x200B;을 클릭합니다.
1. **제목** 필드에 새 영역의 이름을 입력합니다. 원할 경우, 태그를 선택하십시오.
1. **만들기**&#x200B;를 탭하거나 클릭합니다.

   AEM은 만들어진 영역을 나열하는 브랜드 창으로 리디렉션합니다. 마스터 영역 외에 다른 영역이 있다면 브랜드 콘솔에서 바로 영역을 만들 수 있습니다.

   ![만들기](/help/sites-cloud/authoring/assets/multisite-create.png)

## 영역을 Live Copy로 만들기 {#creating-areas-as-live-copies}

사이트 구조에서 타깃팅된 컨텐츠를 상속받으려면 영역을 Live Copy로 만듭니다.

영역을 Live Copy로 만들려면 다음을 수행하십시오.

1. Navigate to **Personalization** > **Activities** or **Offers** and then to your brand.
1. **영역을 Live Copy로 만들기**&#x200B;를 탭하거나 클릭합니다.

   ![영역을 Live Copy로 만들기](/help/sites-cloud/authoring/assets/multisite-area-as-livecopy.png)

1. Live Copy를 만들 영역을 선택하고 **다음**&#x200B;을 클릭합니다.

   ![Live Copy 만들기](/help/sites-cloud/authoring/assets/multisite-livecopy.png)

1. **이름** 필드에 Live Copy의 이름을 입력합니다. 기본적으로 하위 페이지가 포함되어 있습니다. **하위 페이지 제외** 확인란을 선택하여 제외하십시오.

   ![Live Copy 만들기](/help/sites-cloud/authoring/assets/multisite-create-livecopy.png)

1. **롤아웃 구성** 드롭다운 메뉴에서 적절한 구성을 선택합니다.

   각 선택 사항에 대해서는 설치된 롤아웃 구성을 참조하십시오. <!--See [Installed Rollout Configurations](/help/sites-administering/msm-sync.md#installed-rollout-configurations) for descriptions of each option.-->

   Live Copy에 대한 자세한 내용은 Live Copy 만들기 및 동기화를 참조하십시오. <!--See [Creating and Synchronizing Live Copies](/help/sites-administering/msm-livecopy.md) for more information on live copies.-->

   >[!NOTE]
   >
   >When a page is rolled out to a Live Copy and the area configured for the Blueprint page is also the Blueprint for the area configured for the Pages Live Copy, the LiveAction **personalizationContentRollout** triggers a synchronous subRollout, which is part of the **Standard rollout config**.

1. **만들기**&#x200B;를 탭하거나 클릭합니다.

   AEM은 만들어진 영역을 나열하는 브랜드 창으로 리디렉션합니다. 마스터 영역 외에 다른 영역이 있다면 브랜드 창에서 바로 영역을 만들 수 있습니다.

   ![영역 만들기](/help/sites-cloud/authoring/assets/multisite-create-2.png)

## 영역에 사이트 연결 {#linking-sites-to-an-area}

페이지나 사이트에 영역을 연결할 수 있습니다. 영역은 하위 페이지의 매핑으로 오버레이되지 않는 한 모든 하위 페이지에서 상속됩니다. 그러나 일반적으로 여러분은 사이트 수준에서 연결하게 됩니다.

연결하면 선택한 영역의 해당 활동, 경험 및 오퍼만 사용할 수 있습니다. 이렇게 되면 독립적으로 관리되는 컨텐츠가 우발적으로 혼동되는 것을 방지할 수 있습니다. 다른 영역이 구성되지 않으면 각 브랜드의 마스터 영역이 사용됩니다.

>[!NOTE]
>
>Pages or sites that reference the same area are using the *same* shared set of activities, experiences, and offers. 여러 사이트에서 공유하는 활동, 경험 또는 오퍼를 편집하는 것은 모든 사이트에 영향을 줍니다.

사이트를 영역에 연결하려면 다음을 수행하십시오.

1. 영역에 연결하려는 사이트(또는 페이지)로 이동합니다.
1. 사이트 또는 페이지를 선택하고 **속성 보기**&#x200B;를 탭하거나 클릭합니다.
1. **개인화** 탭을 탭하거나 클릭합니다.
1. **브랜드** 메뉴에서 영역을 연결할 브랜드를 선택합니다. 브랜드를 선택한 후에는 **영역 참조** 메뉴에 사용 가능한 영역이 표시됩니다.

   ![사이트 연결](/help/sites-cloud/authoring/assets/multisite-english.png)

1. **영역 참조** 드롭다운 메뉴에서 영역을 선택하고 **저장**&#x200B;을 탭하거나 클릭합니다.

   ![영역 참조](/help/sites-cloud/authoring/assets/multisite-area-reference.png)

## Live Copy 분리 또는 타깃팅된 컨텐츠의 상속 일시 중지 {#detaching-live-copy-or-suspending-inheritance-of-targeted-content}

타깃팅된 컨텐츠의 상속을 일시 중단하거나 분리할 수 있습니다. Live Copy의 일시 중단이나 분리는 각 활동별로 수행됩니다. 예를 들어, 활동에서 경험을 수정할 수는 있지만, 해당 활동이 상속된 Live Copy사본에 여전히 연결되어 있다면, 경험 또는 활동 속성을 수정할 수 없습니다.

Live Copy를 일시 중단하면 상속이 일시적으로 중단되지만 나중에 상속을 복원할 수 있습니다. Live Copy를 분리하면 상속이 영구적으로 중단됩니다.

활동에서 상속을 복원하여 타깃팅된 컨텐츠의 상속을 일시 중단하거나 분리할 수 있습니다. 페이지나 사이트가 Live Copy인 영역에 연결하는 경우 활동의 상속 상태를 볼 수 있습니다.

다른 사이트에서 상속받는 활동은 활동 이름 옆에 녹색으로 표시됩니다. 일시 중단된 상속은 빨간색으로 표시되고 로컬로 만들어진 활동에는 아무 아이콘도 없습니다.

>[!NOTE]
>
>* 활동에서는 Live Copy만 일시 중단하거나 분리할 수 있습니다.
>* 상속된 활동을 확장하기 위해 Live Copy를 일시 중단하거나 분리할 필요는 없습니다. 항상 해당 활동에 대한 **새** 로컬 경험과 오퍼를 만들 수 있습니다. 기존 활동을 수정하려면 상속을 일시 중단해야 합니다.
>



### 상속 일시 중단 {#suspending-inheritance}

활동에서 타깃팅된 컨텐츠의 상속을 일시 중단하거나 분리하려면 다음을 수행하십시오.

1. 상속을 분리하거나 일시 중단하려는 페이지로 이동하고 모드 드롭다운 메뉴에서 **타깃팅**&#x200B;을 탭하거나 클릭합니다.
1. 페이지가 Live Copy인 영역에 연결되어 있으면, 상속 상태가 표시됩니다. **타깃팅 시작**&#x200B;을 탭하거나 클릭합니다.
1. 활동을 일시 중단하려면 다음 중 하나를 수행하십시오.

   1. 대상과 같은 활동의 요소를 선택합니다. AEM에 Live Copy 일시 중단을 확인하는 상자가 자동으로 표시됩니다. (타깃팅 프로세스에서 임의의 요소를 탭하거나 클릭하여 Live Copy를 일시 중단할 수 있습니다.)
   1. 도구 모음의 드롭다운 메뉴에서 **Live Copy 일시 중단**&#x200B;을 선택합니다.
   ![Live Copy 일시 중단](/help/sites-cloud/authoring/assets/multisite-suspend-livecopy.png)

1. Tap or click **Suspend** to suspend the activity. 일시 중단된 활동은 빨간색으로 표시됩니다.

   ![일시 중단된 Live Copy](/help/sites-cloud/authoring/assets/multisite-suspended.png)

### 상속 중단 {#breaking-inheritance}

활동에서 타깃팅된 컨텐츠의 상속을 중단하려면 다음을 수행하십시오.

1. 마스터에서 Live Copy를 분리하려는 페이지로 이동하고 모드 드롭다운 메뉴에서 **타깃팅**&#x200B;을 탭하거나 클릭합니다.
1. 페이지가 Live Copy인 영역에 연결되어 있으면, 상속 상태가 표시됩니다. **타깃팅 시작**&#x200B;을 탭하거나 클릭합니다.
1. 도구 모음의 드롭다운 메뉴에서 **Live Copy 분리**&#x200B;를 선택합니다. Live Copy를 분리할지 확인하는 메시지가 나타납니다.
1. **분리**&#x200B;를 탭하거나 클릭하여 활동에서 Live Copy를 분리합니다. 분리된 후에는 상속에 대한 드롭다운 메뉴가 더 이상 표시되지 않습니다. 이제 이 활동은 로컬 활동입니다.

   ![로컬 활동](/help/sites-cloud/authoring/assets/multisite-winter.png)

## 타깃팅된 컨텐츠의 상속 복원 {#restoring-inheritance-of-targeted-content}

활동에서 타깃팅된 컨텐츠의 상속을 일시 중단한 경우 언제든지 복원할 수 있습니다. 그러나 Live Copy를 분리한 경우에는 상속을 복원할 수 없습니다.

활동에서 타깃팅된 컨텐츠의 상속을 복원하려면 다음을 수행하십시오.

1. Navigate to the page where you want to restore inheritance and tap or click **Targeting** in the mode drop-down menu.
1. **타깃팅 시작**&#x200B;을 탭하거나 클릭합니다.
1. Select **Resume Live Copy** from the drop-down menu in the toolbar.

   ![Live Copy 다시 시작](/help/sites-cloud/authoring/assets/multisite-resume.png)

1. **다시 시작**&#x200B;을 탭하거나 클릭하여 Live Copy 상속을 다시 시작할 것임을 확인합니다. 상속을 다시 시작하는 경우 현재 활동에 대한 수정 사항은 모두 잃게 됩니다.

## 영역 삭제 {#deleting-areas}

영역을 삭제하면 해당 영역의 모든 활동이 삭제됩니다. AEM에서는 영역을 삭제하기 전에 경고를 표시합니다. 사이트가 연결된 영역을 삭제하면 이 브랜드에 대한 매핑이 자동으로 마스터 영역에 다시 매핑됩니다.

영역을 삭제하려면 다음을 수행하십시오.

1. Navigate to **Personalization** > **Activities** or **Offers** and then your brand.
1. 삭제할 영역 옆에 있는 아이콘을 탭하거나 클릭합니다.
1. **삭제**&#x200B;를 탭하거나 클릭하고 영역을 삭제할 것임을 확인합니다.
