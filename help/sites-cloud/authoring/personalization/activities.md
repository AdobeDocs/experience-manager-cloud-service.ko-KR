---
title: 활동 관리
description: 활동 콘솔을 사용하면 브랜드의 마케팅 활동을 만들고, 구성하고, 관리할 수 있습니다.
exl-id: e7cab16d-7678-472d-b75f-7f67b303ba8d
source-git-commit: a01583483fa89f89b60277c2ce4e1c440590e96c
workflow-type: tm+mt
source-wordcount: '2020'
ht-degree: 61%

---

# 활동 관리 {#managing-activities}

활동 콘솔 을 사용하여 마케팅을 만들고, 구성하고, 관리할 수 있습니다 [활동](/help/sites-cloud/authoring/personalization/overview.md#activities) 브랜드 중:

* 브랜드 추가
* 각 브랜드에 대해 활동 추가 및 구성
* 활동 관리

>[!TIP]
>
>타겟팅 엔진으로 Adobe Target을 사용하는 경우 [활동의 성능 데이터를 볼 ](#viewing-performance-and-converting-winning-experiences-a-b-test)수도 있습니다. A/B 테스트를 사용하는 경우 다음을 수행할 수 있습니다. [우승자 전환](#viewing-performance-and-converting-winning-experiences-a-b-test).

활동 콘솔에서 활동은 브랜드별로 구성됩니다. 브랜드와 폴더를 사용하여 활동의 조직을 구성할 수 있습니다. 을 탭/클릭하여 활동 콘솔로 이동합니다 **개인화** 및 탭/클릭 **활동**.

활동은 [타겟팅된 콘텐츠를 작성](/help/sites-cloud/authoring/personalization/targeted-content.md)하는 타겟팅 모드에서 사용할 수 있으며, 이 모드에서는 활동을 만들 수도 있습니다. 타겟팅 모드에서 만드는 활동은 활동 콘솔에 표시됩니다.

활동은 정의된 활동 종류를 설명하는 레이블과 함께 표시됩니다.

* XT - Adobe Target 경험 타겟팅
* A/B - Adobe Target A/B 테스트
* AEM - Adobe Experience Manager 타깃팅(즉, ContextHub 기반)

![활동 유형](/help/sites-cloud/authoring/assets/activities-types.png)

>[!NOTE]
>
>사용 가능한 활동 유형은 다음과 같은 방법으로 결정됩니다.
>
>* AEM 측에서 Adobe Target에 연결하는 데 사용되는 Adobe Target 테넌트(클라이언트 코드)에서 `xt_only` 옵션이 활성화되어 있는 경우 AEM에서는 **XT 활동만** 만들 수 있습니다.
>
>* Adobe Target 테넌트(클라이언트 코드)에서 `xt_only` 옵션이 활성화되어 있지 **않은** 경우 AEM에서 XT 및 A/B 활동을 **모두** 만들 수 있습니다.
>
>**Additional note:** The `xt_only` option is a setting applied on a certain Target tenant (clientcode) and can only be modified directly in Adobe Target. You cannot enable or disable this option in AEM.

>[!CAUTION]
>
>일반 사용자가 액세스할 수 없도록 게시 인스턴스에서 활동 설정 노드 `cq:ActivitySettings`를 보호해야 합니다. 활동 설정 노드는 Adobe Target에 대한 활동 동기화를 처리하는 서비스에만 액세스할 수 있어야 합니다.
>
>자세한 내용은 Adobe Target과 통합하기 위한 전제 조건을 참조하십시오.
<!--
>See [Prerequisites for Integrating with Adobe Target](/help/sites-administering/target-requirements.md#securingtheactivitysettings) for detailed information.
-->

## 활동 콘솔을 사용한 브랜드 만들기 {#creating-a-brand-using-the-activities-console}

마케팅 활동을 관리할 브랜드를 만드십시오.

활동 콘솔을 사용하여 브랜드를 만들면 활동의 경험에 대한 오퍼를 만들 수 있는 [오퍼 콘솔](/help/sites-cloud/authoring/personalization/offers.md)에도 표시됩니다.

1. 탐색 콘솔에서 **개인화**&#x200B;를 클릭하거나 탭합니다. 클릭 또는 탭 **활동**.

   ![활동으로 이동](/help/sites-cloud/authoring/assets/activities-navigation.png)

1. 활동 콘솔에서 을 클릭하거나 탭합니다 **만들기**&#x200B;그러면&#x200B;**브랜드 만들기**.
1. 브랜드 템플릿을 선택하고 **다음**&#x200B;을 클릭하거나 탭합니다.
1. 활동 및 오퍼 콘솔에 표시할 브랜드의 제목을 입력합니다. 원할 경우, 브랜드와 연결할 태그를 하나 이상 입력하거나 선택합니다.
1. **만들기**&#x200B;를 클릭하거나 탭합니다. 브랜드가 활동 콘솔에 표시됩니다.

## 활동 콘솔을 사용하여 활동 추가/편집 {#adding-editing-an-activity-using-the-activities-console}

활동을 추가하거나 기존 활동을 편집하여 특정 대상에게 마케팅 활동을 집중하십시오. 활동을 만들거나 편집할 때 다음 정보를 지정합니다.

* **Name:** The name of the activity.
* **Targeting Engine:** Either [AEM](/help/sites-cloud/authoring/personalization/overview.md#aem) or [Adobe Target](/help/sites-cloud/authoring/personalization/overview.md#adobe-target) as the engine for targeted content.
* **Select a Target Configuration:** (Adobe Target only) The cloud configuration that this activity should use to connect to Adobe Target. This option appears only when Adobe Target is selected for Targeting Engine.
* **활동 유형**: 활동 유형 - A/B 테스트 또는 경험 타겟팅
* **Objective:** (Optional) A description of the activity.
* **Experiences:** Mappings between audience names and the marketing segments that you are targeting.
* **트래픽 비율:** A/B 테스트가 선택되면 각 경험에 대한 트래픽 크기(%)를 변경할 수 있습니다.
* **Duration:** The period of time when the activity is applied.
* **Priority:** The relative priority of the activity. When activities provide content for the same user segments, the activity of the higher priority takes precedence.
* **목표 지표:** 타겟팅 엔진으로 Adobe Target이 선택되면 활동에 성공 지표를 추가할 수 있습니다. One success metric is required.

>[!NOTE]
>
>**Target 구성을 선택** 하려면 **Target 활동 작성자** 그룹의 일원이어야 합니다.

>[!NOTE]
>
>새 Adobe Target 활동을 **활동** 콘솔에서 생성하면 Adobe Target 동기화가 실패하므로 타겟팅된 콘텐츠 편집기에서 *생성*&#x200B;해야 합니다.
>
>그러나 콘솔에서 기존 Adobe Target 활동을 편집할 수 있습니다.

활동을 추가하려면 다음 작업을 수행하십시오.

1. Click or tap the brand for which you are creating the activity, and then click or tap **Create** then **Create Activity**. If editing, select the activity in the Master Area screen and clicking or tapping **Edit Activity**.
1. 다음 정보를 제공한 후 **다음**&#x200B;을 클릭하거나 탭합니다.
   * 활동의 이름입니다.
   * 사용할 타겟팅 엔진. 기본적으로 ContextHub(AEM)가 선택되어 있습니다. Adobe Target을 사용해야 한다면 타겟팅된 콘텐츠 편집기에서 활동을 만드십시오.
   * 타겟팅 엔진으로 Adobe Target을 선택했다면 Adobe Target에 연결하는 데 사용할 클라우드 구성을 선택/편집하십시오. (클라우드 구성에 대해 만든 프레임워크를 선택하지 않도록 주의하십시오.)
   * (선택 사항) 활동의 목표 또는 설명입니다.
   * 활동 유형을 선택합니다.
1. Add one or more experiences to the activity. Click or tap **Add Experience**.
1. AEM 타겟팅 또는 Adobe Target 경험 타겟팅을 사용하는 경우:
   1. **대상자 선택**&#x200B;을 클릭하거나 탭한 다음 경험이 타겟팅하는 세그먼트를 선택합니다.
   1. **경험 추가**&#x200B;를 클릭하거나 탭하고 이름을 입력한 다음 **확인**&#x200B;을 클릭하거나 탭합니다.
   1. **다음**을 클릭하거나 탭합니다.
Adobe Target A/B 테스트를 사용하는 경우:
   1. 대상자 상자에서 연필을 클릭하거나 탭하여 대상자를 선택합니다.
   1. **경험 추가**&#x200B;를 클릭하거나 탭하고 이름을 입력한 다음 **확인**&#x200B;을 클릭하거나 탭합니다.
   1. 각 경험을 표시하는 트래픽 비율을 입력합니다.
   1. **다음**&#x200B;을 클릭하거나 탭합니다.
1. 활동이 시작되는 시기를 지정하려면 다음을 사용하십시오. **시작** 드롭다운 메뉴를 사용하여 다음 값 중 하나를 선택합니다.
   * **활성화 시:** 타겟팅된 콘텐츠가 포함된 페이지가 활성화되면 활동이 시작됩니다.
   * **지정한 날짜 및 시간:** 특정 시간. 이 옵션을 선택할 때는 달력 아이콘을 클릭하거나 탭하고 날짜를 선택한 다음 활동을 시작할 시간을 지정하십시오.
1. 활동이 종료되는 시기를 지정하려면 종료 드롭다운 메뉴를 사용하여 다음 값 중 하나를 선택합니다.
   * **비활성화 시**: 타겟팅된 콘텐츠가 포함된 페이지가 비활성화되면 활동이 끝납니다.
   * **지정한 날짜 및 시간**: 특정 시간. 이 옵션을 선택하는 경우 달력 아이콘을 클릭하거나 탭하고 날짜를 선택한 다음 활동을 종료할 시간을 지정합니다.
1. 활동의 우선 순위를 지정하려면 슬라이더를 사용하여 다음 중 하나를 선택합니다 **낮음**, **기본**, 또는 **높음**.
1. Adobe Target을 타겟팅 엔진으로 사용하는 경우 이 활동에서 측정할 사항을 선택합니다. 사용 가능한 성공 지표에 대한 자세한 내용은 [활동 및 설정 목표 구성](/help/sites-cloud/authoring/personalization/targeted-content.md)을 참조하십시오. 목표를 하나 이상 선택해야 합니다.
1. 클릭 또는 탭 **저장**.

   >[!NOTE]
   >
   >활동을 만든 후에는 사용할 수 있도록 게시해야 합니다.

## 활동 게시 및 게시 취소 {#publishing-and-unpublishing-activities}

활동을 사용할 수 있도록 하려면 활동을 게시해야 합니다. 반대로 게시 취소하여 활동을 사용할 수 없도록 만들 수도 있습니다.

>[!NOTE]
>
>활동의 게시를 취소할 때 페이지를 새로 고치지 않으면 활동의 상태가 변경되지 않습니다.

활동을 게시하거나 게시 취소하려면 다음 작업을 수행하십시오.

1. 브랜드를 클릭하거나 탭한 다음 게시 또는 게시 취소할 활동이 포함된 영역을 클릭하거나 탭합니다.
1. 게시 또는 게시 취소하려는 활동 옆에 있는 아이콘을 탭하거나 클릭합니다.

   ![활동 콘솔에서 게시](/help/sites-cloud/authoring/assets/activities-console.png)

1. 게시하려면 탭하거나 클릭합니다 **게시**. 게시를 취소하려면 탭하거나 클릭합니다 **게시 취소**. 활동 또는 활동이 게시되거나 게시 취소되고 활동 콘솔에서 상태가 변경됩니다(새로 고쳐야 할 수 있음).

## 작성자 및 게시 인스턴스의 활동 {#activities-on-author-and-publish-instances}

Adobe Target 타겟팅 엔진을 사용하는 활동이 활성화되면 게시 인스턴스에서 두 번째 활동이 만들어집니다.

* 작성자 인스턴스의 활동은 작성자 인스턴스의 활동을 추적하며 방문자 경험을 시뮬레이션하는 데 유용합니다. 이 활동에 대해 기록된 분석은 작성자 인스턴스에서 발생하는 사항만 반영합니다.
* 게시 인스턴스의 활동은 게시 서버의 활동을 반영하고 이에 응답합니다. 공개 웹 사이트에서 실행되는 활동입니다. 게시 활동만 실제 공개 사이트의 사용을 추적 및 분석하는 것과 관련이 있습니다.

## 성능 보기 및 우수성이 검증된 경험 전환(A/B 테스트) {#viewing-performance-and-converting-winning-experiences-a-b-test}

모든 Adobe Target 활동(XT 또는 A/B)의 성능을 확인할 수 있습니다. A/B 테스트를 사용하는 경우 우승 경험을 변환할 수도 있으며, 이 경험이 기본 경험이 됩니다.

활동 성능을 보고 우승 경험을 전환하려면 다음 작업을 수행하십시오.

1. **개인화**&#x200B;에서 **활동**&#x200B;을 클릭하거나 탭하여 **활동** 콘솔로 이동합니다.
1. 활동을 보려는 브랜드를 클릭하거나 탭합니다.
1. 활동을 선택하고 **속성 보기**&#x200B;를 클릭하거나 탭하고 **보고서** 탭을 클릭한 다음, 성능을 확인하거나 우승 경험을 전환할 활동을 선택합니다. 성능 데이터가 표시됩니다.

   ![활동 성능 확인](/help/sites-cloud/authoring/assets/activities-performance.png)

1. **우승자 푸시** 링크를 클릭하거나 탭하여 해당 경험을 기본 경험으로 푸시합니다.

   우승자를 전환하면 다음 내용이 수행됩니다.

   * 현재 활동이 비활성화됩니다.
   * 모든 페이지가 수정되고 타겟팅된 콘텐츠가 우승 경험의 실제 콘텐츠로 교체됩니다. 우승 경험의 콘텐츠는 타겟팅되지 **않고** 일반 페이지의 일부가 됩니다.

   ![우승자 전환](/help/sites-cloud/authoring/assets/activities-reports.png)

   우승 경험은 전환율을 기반으로 보고서에서 더 많은 상승도를 생성하는 경험입니다.

1. **예**&#x200B;를 클릭하거나 탭하여 우승자를 전환할 것임을 확인합니다. 우승자를 전환하면 현재 경험이 비활성화되어 우승 경험의 콘텐츠로 교체됩니다.

## Adobe Target과 활동 동기화 {#synchronizing-activities-with-adobe-target}

Adobe Target 타겟팅 엔진을 사용하는 활동은 Adobe Target 캠페인과 동기화됩니다. 활동은 다음 조건이 충족되면 자동으로 Adobe Target에 동기화됩니다.

* 활동에 하나 이상의 경험이 포함되어 있습니다.
* 하나 이상의 경험에 매핑된 세그먼트와 오퍼가 포함되어 있습니다.
* 활동의 각 경험에는 동일한 수의 오퍼가 있어야 합니다.

이러한 조건은 작성자 및 게시 인스턴스의 활동에 적용됩니다.

활동이 동기화되면 Adobe Target에서 해당 캠페인이 만들어집니다.

* 게시 인스턴스의 활동은 해당 Adobe Target 캠페인과 이름이 같습니다.
* 작성 인스턴스의 활동은 `_author` 접미사를 사용하는 동일한 이름의 Target 캠페인에 해당합니다.

![Adobe Target과 동기화](/help/sites-cloud/authoring/assets/activities-synch.png)

작성자 활동은 활동이 수정되는 즉시 동기화됩니다. 즉각적인 동기화를 통해 ContextHub를 통한 작업 시뮬레이션을 수행할 수 있습니다.

게시 활동은 활동이 AEM 게시 인스턴스에 게시될 때 동기화됩니다.

## 활동 동기화 문제 해결 {#troubleshooting-activity-synchronization}

AEM이 활동을 Adobe Target과 동기화할 때 AEM은 `thirdPartyId`라는 활동의 속성을 포함합니다. 이 속성의 값은 AEM 저장소의 활동 경로를 기반으로 합니다. Adobe Target에 있는 두 개의 캠페인이 `thirdPartyId` 속성에 대해 동일한 값을 가질 수는 없습니다. 따라서 Adobe Target의 기존 캠페인(다른 유형 AB, XT)이 `thirdPartyId`에 대해 동일한 값을 사용하는 경우에는 활동이 실패하게 됩니다.

이러한 상황은 다음과 같은 상황에서 발생할 수 있습니다.

1. 활동이 생성되고 Adobe Target과 동기화됩니다.
1. 다른 AEM 인스턴스에서는 활동이 동일한 브랜드 및 동일한 이름을 사용하여 생성됩니다. 시도하면 이 활동의 동기화가 실패합니다.

이러한 상황은 다음과 같은 상황에서도 발생할 수 있습니다.

1. 활동이 생성되고 Adobe Target과 동기화됩니다. 그런 다음 활동이 AEM에서 삭제됩니다.
1. 활동은 삭제된 활동과 동일한 이름을 사용하는 동일한 브랜드로 만들어집니다. 시도하면 이 활동의 동기화가 실패합니다.

동기화 문제를 방지하려면 항상 활동에 고유한 이름을 사용하십시오. 활동이 동기화에 실패하는 경우, 해당 캠페인이 사용되고 있지 않다면 동일한 이름을 사용하는 Adobe Target 캠페인을 삭제할 수 있습니다.

>[!NOTE]
>
>Adobe Target에서 캠페인을 만들 때 각 캠페인에 `thirdPartyId`라는 속성을 지정하게 됩니다. Adobe Target에서 이 캠페인을 삭제해도 `thirdPartyId`는 삭제되지 않습니다. `thirdPartyId`는 다른 유형의 캠페인(AB, XT)에 대해 다시 사용할 수 없으며 수동으로 제거할 수 없습니다. 이러한 문제를 방지하려면 각 캠페인에 고유한 이름을 지정하십시오. 따라서 캠페인 이름은 다른 캠페인 유형에서 다시 사용할 수 없습니다.
>
>동일한 캠페인 유형에서 동일한 이름을 사용하는 경우 기존 캠페인을 덮어쓰게 됩니다.
>
>동기화 중에 “Request Failed. `thirdPartyId` already exists&quot;(요청이 실패했습니다. thirdPartyId가 이미 있습니다)라는 오류가 발생하는 경우, 캠페인 이름을 변경하고 다시 동기화하십시오.
