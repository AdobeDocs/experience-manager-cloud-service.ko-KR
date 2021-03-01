---
title: 컨텐츠 재활용 - 다중 사이트 관리자 및 Live Copy
description: AEM의 강력한 Live Copy 및 Multi Site Manager 기능을 사용하여 컨텐츠를 재활용하는 방법을 소개합니다.
translation-type: tm+mt
source-git-commit: b22d972adeaec6af4f15e11fa3359758a1ed77c3
workflow-type: tm+mt
source-wordcount: '2682'
ht-degree: 1%

---


# 컨텐츠 재활용:다중 사이트 관리자 및 Live Copy {#multi-site-manager-and-live-copy}

MSM(Multi Site Manager)을 사용하면 여러 위치에서 동일한 사이트 컨텐츠를 사용할 수 있습니다. MSM은 Live Copy 기능을 사용하여 이를 실현합니다.

* MSM을 사용하여 다음을 수행할 수 있습니다.
   * 컨텐츠를 한 번 만든 다음
   * 동일한 사이트 또는 다른 사이트의 다른 영역([Live Copy](#live-copies))에서 이 컨텐츠를 재사용합니다.
* 그러면 MSM은 소스 컨텐츠와 Live Copy 사이의 라이브 관계를 유지하여 다음과 같은 작업을 수행합니다.
   * 소스 컨텐츠를 변경하면 소스 및 Live Copy가 동기화됩니다.
   * 개별 하위 페이지 및/또는 구성 요소에 대한 라이브 관계를 끊는 방식으로 Live Copy의 컨텐츠에만 조정할 수 있습니다.

이 페이지에서는 MSM을 사용하여 컨텐츠를 재사용하는 방법에 대한 개요를 제공합니다. 다음 페이지에서는 관련 문제를 자세히 다룹니다.

* [Live Copy 만들기 및 동기화](creating-live-copies.md)
* [Live Copy 개요 콘솔](live-copy-overview.md)
* [Live Copy 동기화 구성](live-copy-sync-config.md)
* [MSM 롤아웃 충돌](rollout-conflicts.md)
* [MSM 우수 사례](best-practices.md)

## 가능한 시나리오 {#possible-scenarios}

MSM 및 Live Copy에 대한 사용 사례는 많습니다. 일부 시나리오는 다음과 같습니다.

* **다국적 기업 - 글로벌 - 로컬 회사**

   MSM에서 지원하는 일반적인 사용 사례 중 하나는 여러 다국적 동일 언어 사이트의 컨텐츠를 재사용하는 것입니다. 이를 통해 핵심 컨텐츠를 재사용할 수 있을 뿐만 아니라 국가 변형을 허용할 수 있습니다.

   예를 들어 [WKND 자습서 샘플](/help/implementing/developing/introduction/develop-wknd-tutorial.md)의 영어 섹션은 미국 고객을 위해 생성됩니다. 이 사이트에 포함된 대부분의 컨텐츠는 다른 국가와 문화의 영어를 사용하는 고객을 대상으로 하는 다른 WKND 사이트에도 사용할 수 있습니다. 핵심 컨텐츠는 모든 사이트에서 동일하게 유지되지만 지역별 조정을 수행할 수 있습니다.

   다음 구조는 미국 및 캐나다 사이트에 사용할 수 있습니다. `language-masters` 노드가 영어뿐만 아니라 다른 언어 컨텐츠의 마스터 사본을 유지하는 방법을 확인하십시오. 이 컨텐츠는 영어와 함께 추가 지역 언어 컨텐츠의 기초로 사용할 수 있습니다.

   ```xml
   /content
       |- wknd
           |- language-masters
               |- en
               |- es
               |- fr
           |- us
               |- en
               |- es
           |- ca
               |- en
               |- fr
   ```

   >[!NOTE]
   >
   >MSM은 콘텐츠를 번역하지 않습니다. 필요한 구조를 만들고 컨텐츠를 배포하는 데 사용됩니다.
   >
   >
   >이러한 예제는 [다국어 사이트 컨텐츠 번역](/help/sites-cloud/administering/translation/overview.md)을 참조하십시오.

* **전국 - 지사 간 지사**

   또는 딜러 네트워크를 사용하는 회사는 각 딜러 각각에 대해 별도의 웹 사이트를 원할 수 있으며, 각각은 본사에서 제공하는 기본 사이트의 변형입니다. 여러 지역 사무소가 있는 단일 회사 또는 중앙 가맹업체와 여러 지역 가맹점으로 구성된 국가 프랜차이즈 시스템일 수 있습니다.

   본사는 핵심 정보를 제공할 수 있는 반면, 지역 개체는 연락처 세부 정보, 시작 시간 및 이벤트와 같은 로컬 정보를 추가할 수 있습니다.

   ```xml
   /content
       |- head-office-berlin
       |- branch-hamburg
       |- branch-stuttgart
       |- branch-munich
       |- branch-frankfurt
   ```

* **여러 버전**

   MSM은 특정 하위 분기의 버전을 만들 수 있습니다. 예를 들어 지원 하위 사이트는 특정 제품의 서로 다른 버전에 대한 세부 정보를 저장할 수 있습니다. 여기서 기본 정보는 일정하게 유지되고 업데이트된 기능만 변경해야 합니다.

   ```xml
   /content
       |- game-support
           |- polybius
               |- v5.0
               |- v4.0
               |- v3.0
               |- v2.0
               |- v1.0
   ```

   >[!TIP]
   >
   >이러한 시나리오에서 이것은 다음의 균형인 간단한 사본을 만들 것인지 Live Copy를 사용할 것인지 여부입니다.
   >
   >* 여러 버전을 통해 업데이트해야 하는 핵심 컨텐츠 수입니다.
   >
   >대상:
   >
   >* 개별 사본의 양을 조정할 필요가 있습니다.


## UI {#msm-from-the-ui}의 MSM

MSM은 해당 콘솔의 다양한 옵션을 사용하여 UI에서 직접 액세스할 수 있습니다.

* **사이트 만들기** (**사이트**)

   * MSM을 사용하면 일반적인 컨텐츠를 공유하는 여러 웹 사이트를 관리할 수 있습니다. 예를 들어, 웹 사이트는 대부분의 컨텐츠가 모든 국가에서 공통으로 제공되기 때문에 개별 국가에 맞는 컨텐츠의 하위 세트가 제공됩니다. MSM을 사용하면 소스 사이트](creating-live-copies.md#creating-a-live-copy-of-a-site-from-a-blueprint-configuration)에 따라 하나 이상의 사이트를 자동으로 업데이트하는 [Live Copy를 만들 수 있습니다. 또한 일반적인 기본 구조를 적용하고, 여러 사이트에서 일반적인 컨텐츠를 사용하고, 일반적인 모양과 느낌을 유지하며, 실제로 사이트 간에 다른 컨텐츠를 관리하는 데 집중할 수 있습니다. 다음과 같은 방법으로 사이트 만들기:
      * 소스를 지정하려면 미리 정의된 블루프린트 구성이 필요합니다.
      * (사전 정의된) 소스의 Live Copy를 만듭니다.
      * 사용자에게 **롤아웃** 단추를 제공합니다.

* **Live Copy 만들기** (**사이트**)

   * MSM을 사용하면 웹 사이트의 개별 페이지 또는 하위 분기의 임시(일회성) Live Copy를 만들 수 있습니다.[](creating-live-copies.md#creating-a-live-copy-of-a-page) 예를 들어 하위 분기를 복제하여 제품의 새/업데이트된 버전에 대한 정보를 제공합니다. Live Copy를 만드는 방법은 다음과 같습니다.
      * 임시 Live Copy를 만듭니다(블루프린트 구성이 필요 없음).
      * 모든 페이지/분기의 Live Copy를 만드는 데 사용할 수 있습니다(즉시).
      * **동기화**(**롤아웃** 단추를 제공하지 않음)가 필요합니다.

* **속성 보기** (**사이트**)

   * 해당되는 경우, 이 옵션은 관련 **Live Copy** 또는 **블루프린트**&#x200B;에 대한 정보를 제공함으로써 [Live Copy](creating-live-copies.md#monitoring-your-live-copy)을 모니터링하는 데 도움이 됩니다.

* **참조** (**사이트**)

   * [참조](/help/sites-cloud/authoring/getting-started/basic-handling.md#references) 레일은 적절한 작업에 대한 액세스와 함께 **Live Copy**&#x200B;에 대한 정보를 제공합니다.

* **Live Copy 개요** (**사이트**)

   * 이 콘솔에서는 [블루프린트와 Live Copy를 보고 관리할 수 있습니다.](live-copy-overview.md)

* **Blueprint** (**도구** -  **사이트**)

   * 이 콘솔에서는 [블루프린트 구성을 만들고 관리할 수 있습니다.](creating-live-copies.md#creating-a-blueprint-configuration)

>[!NOTE]
>
>MSM 기능의 양상은 론치와 같은 기타 여러 AEM 기능에 사용됩니다. 이 경우 Live Copy는 해당 기능으로 관리됩니다.

### 사용된 용어 {#terms-used}

다음 표에서는 MSM과 함께 사용되는 기본 용어의 개요를 제공합니다. 이러한 내용은 후속 섹션 및 페이지에서 자세히 다룹니다.

| 용어 | 정의 | 자세한 내용 |
|---|---|---|
| 소스 | Live Copy의 기초로 사용되는 원본 페이지 | Blueprint 및/또는 Blueprint 페이지와 동의어 |
| Live Copy | 롤아웃 구성에 정의된 동기화 작업으로 유지 관리되는 소스의 복사본 |  |
| Live Copy 구성 | Live Copy에 대한 구성 세부 사항의 정의 |  |
| 라이브 관계 | 소스 및 Live Copy 간의 연결 등 주어진 리소스에 대한 상속의 유효한 정의 | 소스의 변경 사항이 Live Copy와 동기화되도록 합니다. |
| 블루프린트 | 소스와 일치 | 블루프린트 구성으로 정의 가능 |
| 블루프린트 구성 | 소스 경로를 지정하는 사전 정의된 구성 | 블루프린트 페이지가 블루프린트 구성에서 참조되면 롤아웃 명령을 사용할 수 있습니다 |
| 장 | Live Copy에 포함할 블루프린트의 섹션 | 일반적으로 루트의 하위 페이지입니다 |
| 동기화 | 소스와 Live Copy 간에 콘텐트를 동기화하는 일반 용어(모두 **롤아웃** 및 **동기화** 옵션) |  |
| 롤아웃 | 소스에서 Live Copy로 동기화 | 작성자(블루프린트 페이지)나 시스템 이벤트(롤아웃 구성에 의해 정의됨)에 의해 트리거될 수 있습니다. |
| 롤아웃 구성 | 동기화할 속성, 방법 및 시기를 결정하는 규칙 |  |
| 동기화 | Live Copy 페이지에서 작성된 수동 동기화 요청 |  |
| 상속 | 동기화가 발생할 때 Live Copy 페이지/구성 요소는 소스 페이지/구성 요소의 컨텐츠를 상속합니다. |  |
| 일시 중단 | Live Copy와 블루프린트 페이지 간의 라이브 관계를 일시적으로 제거합니다. |  |
| 분리 | Live Copy와 블루프린트 페이지 간의 라이브 관계를 영구적으로 제거 |  |
| 재설정 | Live Copy 페이지를 재설정하여 모든 상속 취소를 제거하고 페이지를 소스 페이지와 동일한 상태로 되돌립니다. | 재설정은 페이지 속성, 단락 시스템 및 구성 요소에 적용한 모든 변경 사항에 영향을 줍니다. |
| 얕은 | 단일 페이지의 Live Copy |  |
| 깊이 | 하위 페이지와 함께 페이지의 Live Copy |  |

<!--
>[!TIP]
>
>See [Overview of the Java API](/help/sites-developing/extending-msm.md#overview-of-the-java-api) for the object names.
-->

## Live Copy {#live-copies}

MSM Live Copy는 원래 소스와의 라이브 관계가 유지 관리되는 특정 사이트 컨텐츠의 사본입니다.

* Live Copy는 소스의 컨텐츠를 상속합니다.
* 동기화는 소스에 변경 사항이 있을 때 내용의 실제 전송을 수행합니다.
* Live Copy는 다음 중 하나로 간주할 수 있습니다.
   * 얕은:단일 페이지
   * 깊이:페이지와 하위 페이지
* 롤아웃 구성이라고 하는 동기화 규칙은 동기화할 속성과 동기화 발생 시기를 결정합니다.

이전 예에서 `/content/wknd/language-masters/en`은 영어로 된 글로벌 마스터 사이트입니다. 이 사이트의 컨텐츠를 재사용하려면 MSM Live Copy가 만들어집니다.

* `/content/wknd/language-masters/en` 아래의 컨텐츠는 소스입니다.
* `/content/wknd/language-masters/en` 아래의 컨텐츠가 `/content/wknd/us/en/` 및 `/content/wknd/ca/en` 노드 아래에 복사됩니다. Live Copy입니다.
* 작성자는 `/content/wknd/language-masters/en` 아래의 페이지를 변경합니다.
* 트리거되면 MSM은 이러한 변경 내용을 Live Copy에 동기화합니다.

### Live Copy - 컴포지션 {#live-copies-composition}

>[!NOTE]
>
>이 섹션의 다이어그램과 설명은 잠재적인 Live Copy 스냅샷을 나타냅니다. 포괄적이지는 않지만 특정 특성을 강조하는 개요를 제공합니다.

Live Copy를 처음 만들 때 선택한 소스 페이지가 Live Copy에 1:1로 반영됩니다. 이후에는 Live Copy 내에서 직접 새 리소스(페이지 및/또는 단락)를 만들 수 있으므로 이러한 변형과 변경 사항이 동기화에 미치는 영향을 파악하는 것이 유용합니다. 가능한 컴포지션은 다음과 같습니다.

* [Live Copy 이외의 페이지가 포함된 Live Copy](#live-copy-with-non-live-copy-pages)
* [중첩된 Live Copy](#nested-live-copies)

Live Copy의 기본 양식은 다음과 같습니다.

* 선택한 소스 페이지를 1:1로 반영하는 Live Copy 페이지.
* 하나의 구성 정의.
* 모든 리소스에 대해 정의된 라이브 관계:
   * Live Copy 리소스를 블루프린트/소스와 연결합니다.
   * 상속과 롤아웃을 구현할 때 사용됩니다.

변경 사항은 요구 사항에 따라 [동기화된](creating-live-copies.md#synchronizing-your-live-copy)일 수 있습니다.

![Live Copy 구성 개요](../assets/live-copy-composition.png)

#### Live Copy 이외의 페이지가 있는 Live Copy {#live-copy-with-non-live-copy-pages}

AEM에서 Live Copy를 만들 때 Live Copy 분기를 통해 보고 탐색할 수 있으며 Live Copy 분기에서 일반적인 AEM 기능을 사용할 수 있습니다. 즉, Live Copy 내에서 새 리소스(페이지 및/또는 단락)를 만들 수 있습니다. 예: 특정 지역 또는 국가의 제품.

* 이러한 리소스는 소스/블루프린트 페이지와 라이브 관계가 없으며 동기화되지 않습니다.
* MSM이 특수 케이스로 처리하는 시나리오가 발생할 수 있습니다. 예를 들어 소스/블루프린트와 Live Copy 분기 모두에서 위치와 이름이 동일한 페이지를 만들 때(또는 프로세스). 이러한 상황에서는 [MSM 롤아웃 충돌](rollout-conflicts.md)을 참조하십시오.

![Live Copy 이외의 페이지가 포함된 Live Copy](../assets/live-copy-with-non-live-copy-pages.png)

#### 중첩된 Live Copy {#nested-live-copies}

기존 Live Copy](#live-copy-with-non-live-copy-pages) 내에 [새 페이지를 만들 때 이 새 페이지를 다른 블루프린트의 Live Copy로 설정할 수도 있습니다. 이를 중첩된 Live Copy라고 합니다. 중첩된 Live Copy에서 두 번째 또는 내부 Live Copy의 동작은 다음 방법으로 첫 번째 또는 외부 Live Copy의 영향을 받습니다.

* 최상위 Live Copy에 대해 트리거된 딥 롤아웃을 중첩된 Live Copy에 계속할 수 있습니다.
* 소스 사이의 모든 링크는 Live Copy 내에 다시 작성됩니다.

예를 들어, 두 번째에서 첫 번째 청사진 사이의 링크는 중첩된/두 번째 Live Copy를 가리키는 링크로 다시 작성됩니다.

![중첩된 Live Copy](../assets/live-copy-nested.png)

>[!NOTE]
>
>Live Copy 분기 내에서 페이지를 이동하거나 이름을 변경하는 경우, 이 작업은 AEM에서 관계를 추적할 수 있도록 중첩 Live Copy로 처리됩니다.

#### 누적 Live Copy {#stacked-live-copies}

Live Copy가 얕은 Live Copy의 자식으로 만들어지면 Live Copy를 누적 Live Copy라고 합니다. 이것은 [중첩된 Live Copy](#nested-live-copies)와 동일한 방식으로 동작합니다.

### 소스, 블루프린트 및 블루프린트 구성 {#source-blueprints-and-blueprint-configurations}

모든 페이지 또는 페이지 분기를 Live Copy 소스로 사용할 수 있습니다. 그러나 MSM에서는 소스 경로를 지정하는 블루프린트 구성을 정의할 수도 있습니다. 블루프린트 구성을 사용하면 다음과 같은 이점이 있습니다.

* 작성자가 블루프린트에서 **롤아웃** 옵션을 사용할 수 있도록 허용합니다. 즉, 이 블루프린트에서 상속되는 Live Copy 수정 사항을 명시적으로 푸시합니다.
* 작성자가 **사이트 만들기**&#x200B;를 사용하도록 허용합니다. 따라서 사용자는 손쉽게 언어를 선택하고 Live Copy 구조를 구성할 수 있습니다.
* 블루프린트와 관계가 있는 Live Copy에 대한 기본 롤아웃 구성을 정의합니다.

Live Copy의 소스는 일반 페이지 또는 블루프린트 구성으로 둘러싸인 페이지일 수 있습니다. 두 가지 모두 유효한 사용 사례입니다.

소스는 Live Copy의 청사진을 구성합니다. 다음과 같은 경우 청사진이 정의됩니다.

* [블루프린트 구성](creating-live-copies.md#creating-a-blueprint-configuration)  만들기 - 구성은 Live Copy를 만드는 데 사용할 페이지를 미리 정의합니다.
* [페이지의 Live Copy 만들기](creating-live-copies.md#creating-a-live-copy-of-a-page)  - Live Copy를 만드는 데 사용되는 페이지(소스 페이지)는 블루프린트 페이지입니다. 소스 페이지가 블루프린트 구성에서 참조되거나 참조되지 않을 수 있습니다.

### 롤아웃 및 동기화 {#rollout-and-synchronize}

롤아웃은 Live Copy를 소스와 동기화하는 중앙 MSM 동작입니다. 수동으로 롤아웃을 수행하거나 자동으로 수행할 수 있습니다.

* [롤아웃 구성](#rollout-configurations)을 정의하여 특정 [events](live-copy-sync-config.md#rollout-triggers)이 자동으로 롤아웃될 수 있습니다.
* 블루프린트 페이지를 작성할 때 **[롤아웃](creating-live-copies.md#rolling-out-a-blueprint)** 명령을 사용하여 변경 내용을 Live Copy에 푸시할 수 있습니다.
   * 블루프린트 구성에서 참조하는 블루프린트 페이지에서 **롤아웃** 명령을 사용할 수 있습니다.

   ![롤아웃](../assets/live-copy-rollout.png)

* Live Copy 페이지를 작성할 때 **[동기화](creating-live-copies.md#synchronizing-a-live-copy)** 명령을 사용하여 소스에서 Live Copy로 변경 내용을 가져올 수 있습니다.
   * 소스/블루프린트 페이지가 블루프린트 구성으로 포함되었는지 여부에 관계없이 Live Copy 페이지에서 **동기화** 명령을 항상 사용할 수 있습니다.

   ![동기화](../assets/live-copy-synchronize.png)

### 롤아웃 구성 {#rollout-configurations}

롤아웃 구성은 Live Copy가 소스 컨텐츠와 동기화되는 시기 및 방법을 정의합니다. 롤아웃 구성은 트리거 및 하나 이상의 동기화 작업으로 구성됩니다.

* **트리거**  - 트리거는 소스 페이지의 활성화와 같이 라이브 작업 동기화를 발생시키는 이벤트입니다. MSM은 사용할 수 있는 트리거를 정의합니다.
* **동기화 작업**  - 동기화 작업은 Live Copy에서 수행되어 소스와 동기화됩니다. 예제 작업은 컨텐츠 복사, 하위 노드 순서 지정 및 Live Copy 페이지 활성화입니다. MSM은 여러 동기화 작업을 제공합니다.

>[!NOTE]
>
>Java API를 사용하여 인스턴스에 대한 사용자 정의 동작을 만들 수 있습니다.

롤아웃 구성을 다시 사용할 수 있으므로 둘 이상의 Live Copy에서 동일한 롤아웃 구성을 사용할 수 있습니다. 표준 설치에는 일부 [롤아웃 구성](live-copy-sync-config.md#installed-rollout-configurations)이 포함됩니다.

### 롤아웃 충돌 {#rollout-conflicts}

특히 작성자가 소스와 Live Copy 모두에서 컨텐츠를 편집하는 경우 롤아웃이 복잡해질 수 있습니다. 따라서 롤아웃 중에 발생할 수 있는 모든 [충돌을 AEM에서 처리하는 방법을 이해하는 것이 유용합니다.](rollout-conflicts.md)

### 상속 및 동기화 일시 중단 및 취소 {#suspending-and-cancelling-inheritance-and-synchronization}

Live Copy의 각 페이지 및 구성 요소는 라이브 관계를 통해 소스 페이지 및 구성 요소와 연결됩니다. 라이브 관계는 소스의 Live Copy 컨텐츠 동기화를 구성합니다.

페이지 속성 및 구성 요소를 변경할 수 있도록 Live Copy 페이지에 대한 **Live Copy 상속을 일시 중단할 수 있습니다**. 상속을 일시 중단하면 페이지 속성 및 구성 요소가 더 이상 소스와 동기화되지 않습니다.

개별 페이지를 편집할 때 작성자는 구성 요소에 대해 **상속 취소**&#x200B;할 수 있습니다. 상속이 취소되면 라이브 관계가 일시 중단되고 해당 구성 요소에 대한 동기화가 발생하지 않습니다. 상속과 동기화 취소는 내용의 하위 섹션을 사용자 정의해야 하는 경우에 유용합니다.

### Live Copy 분리 {#detaching-a-live-copy}

모든 연결을 제거하기 위해 블루프린트에서 [Live Copy](creating-live-copies.md#detaching-a-live-copy)를 분리할 수도 있습니다.

>[!CAUTION]
>
>분리 동작은 영구적이며 되돌릴 수 없습니다.

분리 작업은 Live Copy와 블루프린트 페이지 간의 라이브 관계를 영구적으로 제거합니다. 모든 MSM 관련 속성은 Live Copy에서 제거되고 Live Copy 페이지는 독립형 복사본이 됩니다.

>[!TIP]
>
>하위 및 상위 페이지에 대한 관련 영향을 비롯한 자세한 내용은 [Live Copy 분리](creating-live-copies.md#detaching-a-live-copy)를 참조하십시오.

## MSM {#standard-steps-for-using-msm} 사용을 위한 표준 단계

다음 단계에서는 MSM을 사용하여 컨텐츠를 재사용하고 변경 사항을 Live Copy에 동기화하는 표준 절차를 설명합니다.

1. 소스 사이트의 컨텐츠를 개발합니다.
1. 사용할 롤아웃 구성을 결정합니다.

   1. MSM [에서는 여러 사용 사례를 충족할 수 있는 몇 개의 롤아웃 구성](live-copy-sync-config.md#installed-rollout-configurations)을 설치합니다.
   1. 필요한 경우 [롤아웃 구성](live-copy-sync-config.md#creating-a-rollout-configuration)을 만들 수도 있습니다.

1. [롤아웃 구성을 지정하여](live-copy-sync-config.md#specifying-the-rollout-configurations-to-use)을(를) 사용하고 필요에 따라 구성해야 하는 위치를 결정합니다.
1. 필요한 경우 [Live Copy의 소스 컨텐츠를 식별하는 블루프린트 구성](creating-live-copies.md#creating-a-blueprint-configuration)을 만듭니다.
1. [Live Copy 만들기를 참조하십시오.](creating-live-copies.md#creating-a-live-copy)
1. 필요에 따라 소스 컨텐츠를 변경합니다. 조직에서 설정한 일반적인 컨텐츠 검토 및 승인 프로세스를 사용해야 합니다.
1. [블루프린트](creating-live-copies.md#rolling-out-a-blueprint) 를 롤아웃하거나  [라이브 카피를 변경 ](creating-live-copies.md#synchronizing-a-live-copy) 사항과 동기화합니다.

## MSM {#customizing-msm} 사용자 지정

MSM은 콘텐츠를 공유할 때 발생할 수 있는 매우 복잡한 복잡성에 맞게 구현될 수 있도록 도구를 제공합니다.

* **사용자 지정 롤아웃 구성**   [- 설치된 ](live-copy-sync-config.md#creating-a-rollout-configuration) 롤아웃 구성이 요구 사항을 충족하지 않을 때 롤아웃 구성을 만듭니다. 사용 가능한 롤아웃 트리거 및 동기화 작업을 사용할 수 있습니다.

<!--
* **Custom Synchronization Actions** - [Create a custom synchronization action](/help/sites-developing/extending-msm.md#creating-a-new-synchronization-action) when the installed actions do not meet your specific application requirements. MSM provides a Java API for creating custom synchronization actions.
-->

## 우수 사례 {#best-practices}

[MSM 우수 사례](best-practices.md) 페이지에는 구현과 관련된 중요한 정보가 포함되어 있습니다.
