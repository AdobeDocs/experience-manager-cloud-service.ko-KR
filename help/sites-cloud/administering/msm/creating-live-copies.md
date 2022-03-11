---
title: 라이브 카피 생성 및 동기화
description: 사이트 전체에서 컨텐츠를 재사용하기 위해 Live Copy 를 만들고 동기화하는 방법을 알아봅니다.
feature: Multi Site Manager
role: Admin
exl-id: 53ed574d-e20d-4e73-aaa2-27168b9d05fe
source-git-commit: 24a4a43cef9a579f9f2992a41c582f4a6c775bf3
workflow-type: tm+mt
source-wordcount: '4274'
ht-degree: 1%

---

# 라이브 카피 생성 및 동기화 {#creating-and-synchronizing-live-copies}

사이트에서 해당 컨텐츠를 재사용하기 위해 페이지나 블루프린트 구성에서 Live Copy를 만들 수 있습니다. 상속 및 동기화를 관리합니다. 컨텐츠 변경 사항이 전파되는 방식을 제어할 수 있습니다.

## 블루프린트 구성 관리 {#managing-blueprint-configurations}

블루프린트 구성은 하나 이상의 Live Copy 페이지의 소스로 사용할 기존 웹 사이트를 식별합니다.

>[!TIP]
>
>블루프린트 구성을 사용하면 컨텐츠 변경 사항을 Live Copy에 푸시할 수 있습니다. 자세한 내용은 [Live Copy - 소스, 블루프린트 및 블루프린트 구성](overview.md#source-blueprints-and-blueprint-configurations).

블루프린트 구성을 만들 때 블루프린트의 내부 구조를 정의하는 템플릿을 선택합니다. 기본 블루프린트 템플릿은 소스 웹 사이트에 다음과 같은 특성이 있다고 가정합니다.

* 웹 사이트에 루트 페이지가 있습니다.
* 루트의 바로 아래 하위 페이지는 웹 사이트의 언어 분기입니다. Live Copy를 생성할 때 언어는 복사본에 포함할 선택적 컨텐츠로 표시됩니다.
* 각 언어 분기의 루트에 하나 이상의 하위 페이지가 있습니다. Live Copy를 만들 때 Live Copy에 포함할 수 있도록 하위 페이지가 표시됩니다.

>[!NOTE]
>
>다른 구조에는 다른 블루프린트 템플릿이 필요합니다.

블루프린트 구성을 만들면 다음 속성을 구성합니다.

* **이름**: 블루프린트 구성의 이름입니다
* **소스 경로**: 소스(블루프린트)로 사용하는 사이트의 루트 페이지의 경로입니다
* **설명**. (선택 사항) 사이트를 만들 때 선택할 블루프린트 구성 목록에 표시되는 블루프린트 구성에 대한 설명입니다

블루프린트 구성을 사용할 때 소스/블루프린트의 Live Copy 동기화 방식을 결정하는 롤아웃 구성과 연결할 수 있습니다. 자세한 내용은 [사용할 롤아웃 구성 지정](live-copy-sync-config.md#specifying-the-rollout-configurations-to-use).

### 블루프린트 구성 만들기 및 편집 {#creating-editing-blueprint-configurations}

블루프린트 구성은 변경할 수 없는 데이터로 간주되며 런타임 시 편집할 수 없습니다. 따라서 모든 구성 변경 사항은 CI/CD 파이프라인을 사용하여 Git을 통해 배포해야 합니다.

자세한 내용은 문서에 있습니다 [Adobe Experience Manager (AEM) as a Cloud Service에 대한 주요 변경 사항.](/help/release-notes/aem-cloud-changes.md)

로컬 개발 인스턴스의 관리자는 테스트 및 개발을 위해서만 다음 단계를 사용할 수 있습니다. 이러한 옵션은 AEMaaCS 클라우드 인스턴스에서 사용할 수 없습니다.

#### 로컬에서 블루프린트 구성 만들기 {#creating-a-blueprint-configuration}

블루프린트 구성을 만들려면:

1. [탐색](/help/sites-cloud/authoring/getting-started/basic-handling.md#global-navigation) 변환 후 **도구** 메뉴를 선택한 다음 **Sites** 메뉴 아래의 제품에서 사용할 수 있습니다.
1. 선택 **블루프린트** 열다 **블루프린트 구성** 콘솔:

   ![블루프린트 구성](../assets/blueprint-configurations.png)

1. **만들기**&#x200B;를 선택합니다.
1. 블루프린트 템플릿을 선택한 다음 **다음** 계속하십시오.
1. 블루프린트로 사용할 소스 페이지를 선택합니다. 그런 다음 **다음** 계속하십시오.
1. 정의:

   * **제목**: 블루프린트에 대한 필수 제목
   * **설명**: 자세한 내용을 제공하기 위한 선택적 설명입니다.

1. **만들기** 은 사양을 기반으로 블루프린트 구성을 만듭니다.

### 로컬에서 블루프린트 구성 편집 또는 삭제{#editing-or-deleting-a-blueprint-configuration}

기존 블루프린트 구성을 편집하거나 삭제할 수 있습니다.

1. [탐색](/help/sites-cloud/authoring/getting-started/basic-handling.md#global-navigation) 변환 후 **도구** 메뉴를 선택한 다음 **Sites** 메뉴 아래의 제품에서 사용할 수 있습니다.
1. 선택 **블루프린트** 열다 **블루프린트 구성** 콘솔:

   ![블루프린트 구성](../assets/blueprint-configurations.png)

1. 필요한 블루프린트 구성을 선택합니다. 도구 모음에서 적절한 작업을 사용할 수 있습니다.

   * **속성**; 이 구성 요소를 사용하여 구성의 속성을 보고 편집할 수 있습니다.
   * **삭제**

## Live Copy 생성 {#creating-a-live-copy}

Live Copy를 만드는 방법에는 여러 가지가 있습니다.

### 페이지의 Live Copy 만들기 {#creating-a-live-copy-of-a-page}

모든 페이지 또는 분기의 Live Copy를 생성할 수 있습니다. Live Copy를 생성할 때 컨텐츠를 동기화하는 데 사용할 롤아웃 구성을 지정할 수 있습니다.

* 선택한 롤아웃 구성은 Live Copy 페이지 및 해당 하위 페이지에 적용됩니다.
* 롤아웃 구성을 지정하지 않으면 MSM에서 사용할 롤아웃 구성을 결정합니다. 자세한 내용은 [사용할 롤아웃 구성 지정](live-copy-sync-config.md#specifying-the-rollout-configurations-to-use).

페이지의 Live Copy를 만들 수 있습니다.

* 페이지에서 참조하는 페이지 [블루프린트 구성](#creating-a-blueprint-configuration)
* 및 구성에 대한 연결이 없는 페이지
* 다른 Live Copy([중첩된 라이브 카피](overview.md#nested-live-copies))

유일한 차이점은 **롤아웃** 소스/블루프린트 페이지의 명령은 소스가 블루프린트 구성에서 참조되는지 여부에 따라 달라집니다.

* 소스 페이지에서 Live Copy를 만드는 경우 **is** 블루프린트 구성에서 참조되면 롤아웃 명령을 소스/블루프린트 페이지에서 사용할 수 있습니다.
* 소스 페이지에서 Live Copy를 만드는 경우 **is not** 블루프린트 구성에서 참조되면 롤아웃 명령을 소스/블루프린트 페이지에서 사용할 수 없습니다.

Live Copy를 만들려면:

1. 에서 **Sites** 콘솔 선택 **만들기**, 그런 다음 **Live Copy**.

   ![Live Copy 만들기](../assets/create-live-copy.png)

1. 소스 페이지를 선택한 다음 을(를) 클릭하거나 탭합니다 **다음**. 예:

   ![Live Copy 소스 선택](../assets/live-copy-from.png)

1. Live Copy의 대상 경로(Live Copy의 상위 폴더/페이지 열기)를 지정한 다음 을 클릭하거나 탭합니다 **다음**.

   ![Live Copy 대상 선택](../assets/live-copy-to.png)

   >[!NOTE]
   >
   >대상 경로는 소스 경로 내에 있을 수 없습니다.

1. 다음을 입력합니다.

   * a **제목** 추가 정보.
   * a **이름**: URL에 사용됩니다.

   ![Live Copy 속성](../assets/live-copy-properties.png)

1. 를 사용하십시오 **하위 페이지 제외** 확인란:

   * 선택: 선택한 페이지의 Live Copy만 만듭니다(Shallow Live Copy).
   * 선택되지 않음: 선택한 페이지의 모든 하위 항목(딥 Live Copy)을 포함하는 Live Copy를 만듭니다.

1. (선택 사항) Live Copy에 사용할 롤아웃 구성을 한 개 이상 지정하려면 **롤아웃 구성** 드롭다운 목록을 선택하여 선택합니다. 선택한 구성이 드롭다운 선택기 아래에 표시됩니다.
1. **만들기**&#x200B;를 클릭하거나 탭합니다. 확인 메시지가 표시되며, 여기에서 다음 중 하나를 선택할 수 있습니다 **열기** 또는 **완료**.

### 블루프린트 구성에서 사이트의 Live Copy 생성 {#creating-a-live-copy-of-a-site-from-a-blueprint-configuration}

블루프린트 구성을 사용하여 Live Copy를 만들어 블루프린트(소스) 컨텐츠를 기반으로 사이트를 만듭니다. 블루프린트 구성에서 Live Copy를 생성할 때 블루프린트 소스의 하나 이상의 언어 분기를 선택하여 복사한 다음 언어 분기에서 복사할 장을 선택합니다. 자세한 내용은 [블루프린트 구성 만들기](#creating-a-blueprint-configuration).

Live Copy에서 일부 언어 분기를 생략하면 나중에 추가할 수 있습니다. 자세한 내용은 [Live Copy 내에서 Live Copy 만들기(블루프린트 구성)](#creating-a-live-copy-inside-a-live-copy-blueprint-configuration) 자세한 내용

>[!CAUTION]
>
>블루프린트 소스에 다른 분기에 있는 단락을 대상으로 하는 링크 및 참조가 포함되어 있으면 대상이 Live Copy 페이지에서 업데이트되지 않지만 원래 대상을 가리키는 상태로 유지됩니다.

사이트를 만들 때 다음 속성에 대한 값을 제공합니다.

* **초기 언어**: Live Copy에 포함할 블루프린트 소스의 언어 분기
* **초기 장**: 블루프린트 언어의 하위 페이지는 Live Copy에 포함할 분기에 분기됩니다
* **대상 경로**: Live Copy 사이트의 루트 페이지 위치
* **제목**: Live Copy 사이트의 루트 페이지의 제목입니다
* **이름**: (선택 사항) Live Copy의 루트 페이지를 저장하는 JCR 노드의 이름입니다(기본값은 제목을 기반으로 함).
* **사이트 소유자**: (선택 사항) Live Copy를 담당하는 당사자에 대한 정보
* **Live Copy**: 소스 사이트와 라이브 관계를 설정하려면 이 옵션을 선택합니다. 이 옵션을 선택하지 않으면 블루프린트의 복사본이 만들어지지만 그 후에 소스와 동기화되지 않습니다.
* **롤아웃 구성**: (선택 사항) Live Copy를 동기화하는 데 사용할 롤아웃 구성을 한 개 이상 선택합니다. 기본적으로 롤아웃 구성은 블루프린트에서 상속됩니다. 자세한 내용은 [사용할 롤아웃 구성 지정](live-copy-sync-config.md#specifying-the-rollout-configurations-to-use) 자세한 내용

블루프린트 구성에서 사이트의 Live Copy를 만들려면:

1. 에서 **Sites** 콘솔, 선택 **만들기**, 그런 다음 **사이트** 드롭다운 선택기에서 을 클릭합니다.
1. Live Copy의 소스로 사용할 블루프린트 구성을 선택하고 다음 작업을 진행합니다 **다음**:

   ![블루프린트에서 사이트 만들기](../assets/create-site-from-blueprint.png)

1. 를 사용하십시오 **초기 언어** 선택기를 사용하여 Live Copy에 사용할 블루프린트 사이트의 언어를 지정합니다.

   사용 가능한 모든 언어는 기본적으로 선택됩니다. 언어를 제거하려면 **X** 언어 옆에 표시됩니다.

   예:

   ![사이트를 만들 때 속성 지정](../assets/create-site-properties.png)

1. 를 사용하십시오 **초기 장** 드롭다운을 클릭하여 Live Copy에 포함할 블루프린트의 섹션을 선택합니다. 사용 가능한 모든 장은 기본적으로 포함되지만 제거할 수 있습니다.
1. 나머지 속성에 대한 값을 제공한 다음 을 선택합니다 **만들기**. 확인 대화 상자에서 다음을 선택합니다 **완료** 로 돌아가기 **Sites** 콘솔 또는 **사이트 열기** 를 클릭하여 사이트의 루트 페이지를 엽니다.

### Live Copy 내에서 Live Copy 만들기(블루프린트 구성) {#creating-a-live-copy-inside-a-live-copy-blueprint-configuration}

블루프린트 구성을 사용하여 만든 기존 Live Copy 내에 Live Copy를 만들 때 Live Copy를 처음 만들 때 포함되지 않은 모든 언어 사본 또는 장을 삽입할 수 있습니다.

## Live Copy 모니터링 {#monitoring-your-live-copy}

### Live Copy 상태 보기 {#seeing-the-status-of-a-live-copy}

Live Copy 페이지의 속성은 Live Copy에 대한 다음 정보를 보여줍니다.

* **소스**: Live Copy 페이지의 소스 페이지
* **상태**: Live Copy가 소스와의 최신 상태인지, 마지막 동기화 발생 시간 및 동기화를 수행한 사용자를 포함하여 Live Copy의 동기화 상태입니다
* **구성**:

   * 페이지가 여전히 Live Copy 상속의 대상인지 여부
   * 구성이 상위 페이지에서 상속되는지 여부
   * Live Copy에서 사용하는 모든 롤아웃 구성

속성을 보려면

1. 에서 **Sites** 콘솔에서 Live Copy 페이지를 선택하고 속성을 엽니다.
1. 을(를) 선택합니다 **Live Copy** 탭.

   예:

   ![페이지 속성의 Live Copy 탭](../assets/live-copy-inherit.png)

   섹션을 참조하십시오 [Live Copy 개요 사용](live-copy-overview.md#using-the-live-copy-overview) 자세한 내용은 Live Copy 개요 콘솔 문서를 참조하십시오.

### 블루프린트 페이지의 Live Copy 보기 {#seeing-the-live-copies-of-a-blueprint-page}

블루프린트 구성에서 참조되는 블루프린트 페이지 는 현재(블루프린트) 페이지를 소스로 사용하는 Live Copy 페이지 목록을 제공합니다. 이 목록을 사용하여 Live Copy를 추적합니다. 목록이 **블루프린트** 의 탭 [페이지 속성](/help/sites-cloud/authoring/fundamentals/page-properties.md).

![페이지 속성의 블루프린트 탭](../assets/live-copy-blueprint-tab.png)

## Live Copy 동기화 {#synchronizing-your-live-copy}

Live Copy를 동기화하는 방법에는 여러 가지가 있습니다.

### 블루프린트 롤아웃 {#rolling-out-a-blueprint}

컨텐츠 변경 사항을 Live Copy에 푸시하기 위해 블루프린트 페이지를 롤아웃합니다. A **롤아웃** 작업은 를 사용하는 롤아웃 구성을 실행합니다. [롤아웃 시](live-copy-sync-config.md#rollout-triggers) 트리거합니다.

>[!NOTE]
>
>블루프린트 분기와 종속 Live Copy 분기 모두에서 동일한 페이지 이름을 사용하는 새 페이지가 생성되면 충돌이 발생할 수 있습니다.
>
>예 [롤아웃 시 충돌을 처리하고 해결해야 합니다.](rollout-conflicts.md).

#### 페이지 속성에서 블루프린트 롤아웃 {#rolling-out-a-blueprint-from-page-properties}

1. 에서 **Sites** 콘솔의 블루프린트에서 페이지를 선택하고 속성을 엽니다.
1. **블루프린트** 탭을 엽니다.
1. 선택 **롤아웃**.

   ![롤아웃 단추](../assets/rollout.png)

1. 페이지 및 하위 페이지를 지정한 다음 확인 표시로 확인합니다.

   ![롤아웃할 페이지 선택](../assets/select-rollout-pages.png)

1. 롤아웃 작업을 즉시 실행할지 여부를 지정합니다(**지금**) 또는 다른 날짜/시간( )에&#x200B;**나중에**).

   ![롤아웃 시간 정의](../assets/rollout-now-later.png)

롤아웃은 비동기 작업으로 처리되며 [***비동기 작업 상태** 페이지.](/help/operations/asynchronous-jobs.md#monitor-the-status-of-asynchronous-operations)

#### 참조 레일에서 블루프린트 롤아웃 {#roll-out-a-blueprint-from-the-reference-rail}

1. 에서 **Sites** 콘솔에서 live copy에서 페이지를 선택하고 을(를) 엽니다. **[참조](/help/sites-cloud/authoring/getting-started/basic-handling.md#references)** 패널(도구 모음에서).
1. 을(를) 선택합니다 **블루프린트** 옵션을 선택합니다. 이 페이지와 관련된 청사진을 표시합니다.
1. 목록에서 필요한 블루프린트를 선택합니다.
1. 클릭 또는 탭 **롤아웃**.

   ![참조 레일에서 롤아웃 블루프린트](../assets/rollout-blueprint-from-references.png)

1. 롤아웃의 세부 사항을 확인하는 메시지가 표시됩니다.

   * **롤아웃 범위**:

      범위가 선택한 페이지에만 해당하는지 또는 하위 페이지를 포함해야 하는지를 지정합니다.

   * **일정**:

      롤아웃 작업을 즉시 실행할지 여부를 지정합니다(**지금**) 또는 나중에(**나중에**).

      ![롤아웃 범위 및 일정 정의](../assets/rollout-scope-schedule.png)

1. 이러한 세부 사항을 확인한 후 **롤아웃** 를 눌러 작업을 수행합니다.

롤아웃은 비동기 작업으로 처리되며 [**비동기 작업 상태** 페이지.](/help/operations/asynchronous-jobs.md#monitor-the-status-of-asynchronous-operations)

#### Live Copy 개요에서 블루프린트 롤아웃 {#roll-out-a-blueprint-from-the-live-copy-overview}

다음 [**롤아웃** Live Copy 개요에서도 작업을 사용할 수 있습니다](live-copy-overview.md#using-the-live-copy-overview)를 설정하는 것이 좋습니다.

1. 를 엽니다. [Live Copy 개요](live-copy-overview.md#using-the-live-copy-overview) 블루프린트 페이지를 선택합니다.
1. 선택 **롤아웃** 를 클릭합니다.

   ![Live Copy 개요](../assets/live-copy-overview-actions-blueprint.png)

1. 페이지 및 하위 페이지를 지정한 다음 확인 표시로 확인합니다.

   ![롤아웃할 페이지 선택](../assets/select-rollout-pages.png)

1. 롤아웃 작업을 즉시 실행할지 여부를 지정합니다(**지금**) 또는 다른 날짜/시간( )에&#x200B;**나중에**).

   ![롤아웃 예약 정의](../assets/rollout-now-later.png)

롤아웃은 비동기 작업으로 처리되며 [**비동기 작업 상태** 페이지.](/help/operations/asynchronous-jobs.md#monitor-the-status-of-asynchronous-operations)

### Live Copy 동기화 {#synchronizing-a-live-copy}

Live Copy 페이지를 동기화하여 소스에서 Live Copy로 컨텐츠 변경 사항을 가져옵니다.

#### 페이지 속성에서 Live Copy 동기화 {#synchronize-a-live-copy-from-page-properties}

Live Copy를 동기화하여 소스에서 Live Copy로 변경 사항을 가져옵니다.

>[!NOTE]
>
>동기화는 [롤아웃 시](live-copy-sync-config.md#rollout-triggers) 트리거합니다.

1. 에서 **Sites** 콘솔에서 Live Copy 페이지를 선택하고 속성을 엽니다.
1. **Live Copy** 탭을 엽니다.
1. 클릭 또는 탭 **동기화**.

   ![동기화 단추](../assets/synchronize.png)

   확인을 요청합니다. **동기화** 계속 진행합니다.

#### Live Copy 개요에서 Live Copy 동기화 {#synchronize-a-live-copy-from-the-live-copy-overview}

다음 [동기화 작업은 Live Copy 개요에서도 사용할 수 있습니다](live-copy-overview.md#using-the-live-copy-overview): Live Copy 페이지를 선택한 경우.

1. 를 엽니다. [Live Copy 개요](live-copy-overview.md#using-the-live-copy-overview) Live Copy 페이지를 선택합니다.
1. 선택 **동기화** 를 클릭합니다.
1. 을(를) 확인합니다. **롤아웃** 포함 여부를 지정한 후 대화 상자에 있는 작업:

   * **페이지 및 하위 페이지**
   * **페이지만**

   ![하위 페이지가 있거나 없는 페이지 롤아웃](../assets/rollout-page-and-subpages.png)

## Live Copy 컨텐츠 변경 {#changing-live-copy-content}

Live Copy 컨텐츠를 변경하려면 다음을 수행할 수 있습니다.

* 페이지에 단락을 추가합니다.
* 모든 페이지 또는 구성 요소에 대한 Live Copy 상속을 중단하여 기존 콘텐츠를 업데이트합니다.

>[!TIP]
>
>Live Copy에서 새 페이지를 수동으로 만드는 경우, 새 페이지는 Live Copy에 로컬입니다. 즉, 페이지에 페이지가 첨부된 해당 소스 페이지가 없습니다.
>
>관계의 일부인 로컬 페이지를 만드는 가장 좋은 방법은 소스에서 로컬 페이지를 만들고 딥 롤아웃을 수행하는 것입니다. 이렇게 하면 페이지가 로컬로 Live Copy로 만들어집니다.

>[!NOTE]
>
>블루프린트 분기와 종속 Live Copy 분기 모두에서 동일한 페이지 이름을 사용하는 새 페이지가 생성되면 충돌이 발생할 수 있습니다.
>
>예 [롤아웃 시 충돌을 처리하고 해결해야 합니다.](rollout-conflicts.md).

### Live Copy 페이지에 구성 요소 추가 {#adding-components-to-a-live-copy-page}

언제든지 Live Copy 페이지에 구성 요소를 추가할 수 있습니다. Live Copy 및 해당 단락 시스템의 상속 상태는 구성 요소를 추가하는 기능을 제어하지 않습니다.

Live Copy 페이지가 소스 페이지와 동기화되면 추가된 구성 요소는 변경되지 않은 상태로 유지됩니다. 참조 - [Live Copy 페이지에서 구성 요소 순서 변경.](#changing-the-order-of-components-on-a-live-copy-page)

>[!TIP]
>
>컨테이너로 표시된 구성 요소에 로컬로 수행된 변경 사항은 롤아웃 시 블루프린트의 컨텐츠로 덮어써지지 않습니다. 자세한 내용은 [MSM 우수 사례](best-practices.md#components-and-container-synchronization) 추가 정보.

### 페이지에 대한 상속 일시 중단 {#suspending-inheritance-for-a-page}

Live Copy를 만들면 Live Copy 구성이 복사된 페이지의 루트 페이지에 저장됩니다. 루트 페이지의 모든 하위 페이지는 Live Copy 구성을 상속합니다. Live Copy 페이지의 구성 요소도 Live Copy 구성을 상속합니다.

페이지 속성 및 구성 요소를 변경할 수 있도록 Live Copy 페이지에 대한 Live Copy 상속을 일시 중단할 수 있습니다. 상속을 일시 중단하면 페이지 속성 및 구성 요소가 더 이상 소스와 동기화되지 않습니다.

>[!TIP]
>
>다음을 수행할 수도 있습니다 [live Copy 분리](#detaching-a-live-copy) 블루프린트에서 모든 연결을 제거하려면 상속을 일시 중단하는 것과 달리, 분리 작업은 영구적이고 되돌릴 수 없습니다.

#### 페이지 속성에서 상속 일시 중단 {#suspending-inheritance-from-page-properties}

페이지에서 상속을 일시 중단하려면

1. Live Copy 페이지의 속성을 **속성 보기** 명령 **Sites** 콘솔 또는 사용 **페이지 정보** 클릭합니다.
1. 을 클릭하거나 탭합니다 **Live Copy** 탭.
1. 선택 **일시 중단** 를 클릭합니다. 그런 다음 다음 중 하나를 선택할 수 있습니다.

   * **일시 중단**: 현재 페이지만 일시 중단하려면 다음을 수행하십시오.
   * **하위 항목으로 일시 중단**: 하위 페이지와 함께 현재 페이지를 일시 중단합니다.

1. 선택 **일시 중단** 확인 대화 상자에 표시됩니다.

#### Live Copy 개요에서 상속 일시 중단 {#suspending-inheritance-from-the-live-copy-overview}

다음 [일시 중단 작업은 Live Copy 개요에서도 사용할 수 있습니다](live-copy-overview.md#using-the-live-copy-overview): Live Copy 페이지를 선택한 경우.

1. 를 엽니다. [Live Copy 개요](live-copy-overview.md#using-the-live-copy-overview) Live Copy 페이지를 선택합니다.
1. 선택 **일시 중단** 를 클릭합니다.
1. 다음 중에서 적절한 옵션을 선택합니다.

   * **일시 중단**
   * **하위 일시 중단**

   ![하위 일시 중단](../assets/suspend-with-children.png)

1. 을(를) 확인합니다. **일시 중단** 의 작업 **Live Copy 일시 중단** 대화 상자:

   ![일시 중지 확인](../assets/confirm-suspend.png)

### 페이지에 대한 상속 재개 {#resuming-inheritance-for-a-page}

페이지에 대한 Live Copy 상속을 일시 중지하는 것은 임시 작업입니다. 일시 중단되면 **다시 시작** 작업을 사용할 수 있게 되어 라이브 관계를 복원할 수 있습니다.

![상속 다시 시작](../assets/resume-inheritance.png)

상속을 다시 활성화하면 페이지가 소스와 자동으로 동기화되지 않습니다. 필요한 경우 동기화를 요청할 수 있습니다.

* 에서 **다시 시작**/**되돌리기** 대화 상자 예:

   ![다시 시작 및 동기화](../assets/resume-and-synch.png)

* 나중에 동기화 작업을 수동으로 선택하여

>[!NOTE]
>
>상속을 다시 활성화하면 페이지가 소스와 자동으로 동기화되지 않습니다. 필요한 경우 다시 시작할 때 또는 나중에 동기화를 수동으로 요청할 수 있습니다.

#### 페이지 속성에서 상속 다시 시작 {#resuming-inheritance-from-page-properties}

한 번 [일시 중지](#suspending-inheritance-from-page-properties) a **다시 시작** 작업은 페이지 속성의 도구 모음에 표시됩니다.

![다시 시작 단추](../assets/resume.png)

선택하면 대화 상자가 표시됩니다. 필요한 경우 동기화를 선택한 다음 작업을 확인할 수 있습니다.

#### Live Copy 개요에서 Live Copy 페이지 다시 시작 {#resume-a-live-copy-page-from-the-live-copy-overview}

다음 [다시 시작 작업은 Live Copy 개요에서도 사용할 수 있습니다](live-copy-overview.md#using-the-live-copy-overview): Live Copy 페이지를 선택한 경우.

1. 를 엽니다. [Live Copy 개요](live-copy-overview.md#using-the-live-copy-overview) 일시 중지된 Live Copy 페이지를 선택합니다. 페이지가 다음과 같이 표시됩니다. **상속이 취소됨**.
1. 선택 **다시 시작** 를 클릭합니다.
1. 상속을 되돌린 후 페이지를 동기화할지 여부를 표시한 다음 을 확인합니다 **다시 시작** 의 작업 **Live Copy 다시 시작** 대화 상자.

### 상속 깊이 변경(얕은/깊이) {#changing-inheritance-depth-shallow-deep}

기존 Live Copy에서는 페이지의 깊이를 변경할 수 있습니다. 즉, 하위 페이지가 포함되었는지 여부를 나타냅니다.

* 얕은 Live Copy로 전환:

   * 즉시 영향을 받게 되며 되돌릴 수 없습니다.

   * Live Copy에서 명시적으로 하위 페이지를 분리합니다. 실행을 취소하면 하위 항목에 대한 추가 수정 사항을 유지할 수 없습니다.

   * 모든 하위 항목을 제거합니다. `LiveRelationships` 중첩된 경우에도 `LiveCopies`.

* 딥 Live Copy로 전환:

   * 어린이 페이지는 그대로 둡니다.
   * 스위치의 효과를 보려면 롤아웃을 수행하면 롤아웃 구성에 따라 콘텐츠 수정 사항이 적용됩니다.

* 얕은 Live Copy로 전환한 다음 다시 심층으로 전환합니다.

   * (이전의) 얕은 Live Copy의 모든 하위 항목을 수동으로 만든 것처럼 취급하여 `[oldname]_msm_moved name`.

깊이를 지정하거나 변경하려면

1. Live Copy 페이지의 속성을 **속성 보기** 명령 **Sites** 콘솔 또는 사용 **페이지 정보** 클릭합니다.
1. 을 클릭하거나 탭합니다 **Live Copy** 탭.
1. 에서 **구성** 섹션, 설정 또는 지우기 **Live Copy 상속** 하위 페이지 포함 여부에 따른 옵션:

   * 선택됨 - 딥 Live Copy(하위 페이지가 포함됨)
   * 선택 안 함 - 약식 Live Copy(하위 페이지가 제외됨)

   >[!CAUTION]
   >
   >얕은 Live Copy로 전환하면 즉시 효과가 발생하고 복원할 수 없습니다.
   >
   >자세한 내용은 [Live Copy - 구성](overview.md#live-copies-composition) 추가 정보.

1. 클릭 또는 탭 **저장** 업데이트를 유지합니다.

### 구성 요소에 대한 상속 취소 {#cancelling-inheritance-for-a-component}

구성 요소가 더 이상 소스 구성 요소와 동기화되지 않도록 구성 요소에 대한 Live Copy 상속을 취소합니다. 필요한 경우 나중에 상속을 활성화할 수 있습니다.

>[!NOTE]
>
>상속을 다시 활성화하면 컴포넌트가 소스와 자동으로 동기화되지 않습니다. 필요한 경우 수동으로 동기화를 요청할 수 있습니다.

구성 요소 컨텐츠를 변경하거나 구성 요소를 삭제하려면 상속을 취소합니다.

1. 상속을 취소할 구성 요소를 클릭하거나 탭합니다.

   ![구성 요소 도구 모음의 상속](../assets/inheritance-toolbar.png)

1. 구성 요소 도구 모음에서 **상속 취소** 아이콘.

   ![상속 취소 아이콘](../assets/cancel-inheritance-icon.png)

1. 상속 취소 대화 상자에서 다음 작업을 확인합니다. **예**.

   구성 요소 도구 모음이 모든(적절한) 편집 명령을 포함하도록 업데이트됩니다.

### 구성 요소에 대한 상속 재활성화 {#re-enabling-inheritance-for-a-component}

구성 요소에 대한 상속을 활성화하려면 **상속 재활성화** 아이콘 사용 안 함

![상속 재활성화 아이콘](../assets/re-enable-inheritance-icon.png)

### Live Copy 페이지에서 구성 요소 순서 변경 {#changing-the-order-of-components-on-a-live-copy-page}

Live Copy에 단락 시스템의 일부인 구성 요소가 포함된 경우 해당 단락 시스템의 상속은 다음 규칙을 준수합니다.

* 상속된 단락 시스템의 구성 요소 순서는 상속이 설정되었더라도 수정할 수 있습니다.
* 롤아웃 시 구성 요소의 순서가 블루프린트에서 복원됩니다. 새 구성 요소가 롤아웃 전에 Live Copy에 추가된 경우, 추가된 위의 구성 요소와 함께 순서가 변경됩니다.
* 단락 시스템의 상속이 취소되면 구성 요소 순서가 롤아웃 시 복원되지 않고 Live Copy에 그대로 유지됩니다.

>[!NOTE]
>
>단락 시스템에서 취소된 상속을 되돌리는 경우 구성 요소 순서 **자동으로 복원되지 않음** 블루프린트에서 필요한 경우 수동으로 동기화를 요청할 수 있습니다.

단락 시스템의 상속을 취소하려면 다음 절차를 따르십시오.

1. Live Copy 페이지를 엽니다.
1. 기존 구성 요소를 페이지의 새 위치로 드래그합니다.
1. 에서 **상속 취소** 대화 상자에서 작업을 확인합니다. **예**.

### Live Copy 페이지의 속성 재정의 {#overriding-properties-of-a-live-copy-page}

Live Copy 페이지의 페이지 속성은 기본적으로 소스 페이지에서 상속되며 편집할 수 없습니다.

Live Copy에 대한 속성 값을 변경해야 하는 경우 속성에 대한 상속을 취소할 수 있습니다. 링크 아이콘은 속성에 상속이 활성화되었음을 나타냅니다.

![상속된 페이지 속성](../assets/properties-inherited.png)

상속을 취소하면 속성 값을 변경할 수 있습니다. 끊어진 링크 아이콘은 상속이 취소되었음을 나타냅니다.

![상속되지 않은 속성](../assets/properties-not-inherited.png)

필요한 경우 나중에 속성에 대한 상속을 다시 활성화할 수 있습니다.

>[!NOTE]
>
>상속을 다시 활성화하면 Live Copy 페이지 속성이 소스 속성과 자동으로 동기화되지 않습니다. 필요한 경우 수동으로 동기화를 요청할 수 있습니다.

1. 다음 중 하나를 사용하여 Live Copy 페이지의 속성을 엽니다 **속성 보기** 옵션 **Sites** 콘솔 또는 **페이지 정보** 아이콘 사용)을 클릭하여 제품에서 사용할 수 있습니다.
1. 속성 상속을 취소하려면 속성 오른쪽에 표시되는 링크 아이콘을 클릭하거나 탭합니다.

   ![상속 취소 단추](../assets/cancel-inheritance-button.png)

1. 에서 **상속 취소** 확인 대화 상자, 클릭 또는 탭 **예**.

### Live Copy 페이지의 속성 되돌리기 {#revert-properties-of-a-live-copy-page}

속성에 대한 상속을 활성화하려면 **상속 되돌리기** 속성 옆에 표시되는 아이콘입니다.

![상속 되돌리기 단추](../assets/revert-inheritance-button.png)

### Live Copy 페이지 재설정 {#resetting-a-live-copy-page}

Live Copy 페이지를 재설정하여 다음을 수행할 수 있습니다.

* 모든 상속 취소 및 제거
* 페이지를 소스 페이지와 동일한 상태로 반환합니다.

재설정은 페이지 속성, 단락 시스템 및 구성 요소에 수행한 변경 사항에 영향을 줍니다.

#### 페이지 속성에서 Live Copy 페이지 재설정 {#reset-a-live-copy-page-from-the-page-properties}

1. 에서 **Sites** 콘솔에서 Live Copy 페이지를 선택하고 을(를) 선택합니다 **속성 보기**.
1. **Live Copy** 탭을 엽니다.
1. 선택 **재설정** 를 클릭합니다.

   ![재설정 단추](../assets/reset.png)

1. 에서 **Live Copy 재설정** 대화 상자, 다음으로 확인 **재설정**.

#### Live Copy 개요에서 Live Copy 페이지 재설정 {#reset-a-live-copy-page-from-the-live-copy-overview}

다음 [**재설정** Live Copy 개요에서도 작업을 사용할 수 있습니다](live-copy-overview.md#using-the-live-copy-overview): Live Copy 페이지를 선택한 경우.

1. 를 엽니다. [Live Copy 개요](live-copy-overview.md#using-the-live-copy-overview) Live Copy 페이지를 선택합니다.
1. 선택 **재설정** 를 클릭합니다.
1. 을(를) 확인합니다. **재설정** 의 작업 **Live Copy 재설정** 대화 상자:

   ![Live Copy 재설정 확인](../assets/reset-live-copy.png)

## Live Copy 페이지와 블루프린트 페이지 비교 {#comparing-a-live-copy-page-with-a-blueprint-page}

변경한 내용을 추적하기 위해 의 블루프린트 페이지를 볼 수 있습니다. **참조** Live Copy 페이지와 비교할 수 있습니다.

1. 에서 **Sites** 콘솔, [블루프린트 또는 Live Copy 페이지로 이동하여 선택합니다.](/help/sites-cloud/authoring/getting-started/basic-handling.md#viewing-and-selecting-resources)
1. 를 엽니다. **[참조](/help/sites-cloud/authoring/getting-started/basic-handling.md#references)** 패널 및 컨텍스트에 따라 다음 중 하나를 선택합니다.

   * **블루프린트**
   * **Live Copy**

1. 컨텍스트에 따라 특정 Live Copy를 선택합니다. 다음 중 하나를 선택합니다.

   * **블루프린트에 비교**
   * **Live Copy에 비교**

   예:

   ![Live Copy 비교](../assets/compare-live-copy.png)

1. Live Copy 및 블루프린트 페이지가 나란히 열립니다.

   비교 기능 사용에 대한 자세한 내용은 [페이지 비교](/help/sites-cloud/authoring/features/page-diff.md).

## Live Copy 분리 {#detaching-a-live-copy}

분리 작업은 Live Copy와 소스/블루프린트 페이지 간의 라이브 관계를 영구적으로 제거합니다. 모든 MSM 관련 속성은 Live Copy에서 제거되고 Live Copy 페이지는 독립형 복사본이 됩니다.

>[!CAUTION]
>
>Live Copy를 분리하면 Live Relationship을 복원할 수 없습니다.
>
>나중에 복원할 수 있는 옵션과 함께 라이브 관계를 제거하려면 다음 작업을 수행할 수 있습니다 [live Copy 상속 취소](#suspending-inheritance-for-a-page) 추가 정보.

트리 내에서 사용할 위치에 대한 함의가 있습니다 **분리**:

* **Live Copy의 루트 페이지에서 분리**

   Live Copy의 루트 페이지에서 이 작업을 수행하면 블루프린트의 모든 페이지와 Live Copy 간의 Live Relationship이 제거됩니다.

   블루프린트에서 페이지에 대한 추가 변경 사항 **안 함** live Copy에 영향을 줍니다.

* **Live Copy의 하위 페이지에서 분리**

   Live Copy 내의 하위 페이지(또는 분기)에서 이 작업이 수행되는 경우:

   * 해당 하위 페이지(또는 분기)에 대해 라이브 관계가 제거됩니다.
   * Live Copy 분기의 (하위) 페이지는 수동으로 만든 것처럼 처리됩니다.

   그러나 하위 페이지는 여전히 상위 분기의 라이브 관계에 적용되므로 블루프린트 페이지의 추가 롤아웃은 둘 다 수행합니다.

   1. 분리된 페이지의 이름을 변경합니다.

      * 이것은 MSM이 작성하려고 하는 Live Copy 페이지와 이름이 같을 때 충돌이 발생하는 수동으로 만든 페이지로 간주하기 때문입니다.
   1. 롤아웃의 변경 사항이 포함된 원래 이름으로 새 Live Copy 페이지를 만듭니다.

   >[!NOTE]
   >
   >자세한 내용은 [MSM 롤아웃 충돌](rollout-conflicts.md) 자세한 내용은

### 페이지 속성에서 Live Copy 페이지 분리 {#detach-a-live-copy-page-from-the-page-properties}

Live Copy를 분리하려면:

1. 에서 **Sites** 콘솔에서 Live Copy 페이지 를 선택하고 클릭 또는 탭합니다. **속성 보기**.
1. **Live Copy** 탭을 엽니다.
1. 도구 모음에서 를 선택합니다 **분리**.

   ![분리 단추](../assets/detach-button.png)

1. 확인 대화 상자가 표시되면 을 선택합니다. **분리** 를 눌러 작업을 완료합니다.

### Live Copy 개요에서 Live Copy 페이지 분리 {#detach-a-live-copy-page-from-the-live-copy-overview}

다음 [분리 작업은 Live Copy 개요에서도 사용할 수 있습니다](live-copy-overview.md#using-the-live-copy-overview): Live Copy 페이지를 선택한 경우.

1. 를 엽니다. [Live Copy 개요](live-copy-overview.md#using-the-live-copy-overview) Live Copy 페이지를 선택합니다.
1. 선택 **분리** 를 클릭합니다.
1. 을(를) 확인합니다. **분리** 의 작업 **Live Copy 분리** 대화 상자:

   ![Live Copy 분리](../assets/detach-live-copy.png)
