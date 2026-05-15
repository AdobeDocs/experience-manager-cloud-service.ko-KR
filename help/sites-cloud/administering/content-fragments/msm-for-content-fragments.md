---
title: MSM 및 라이브 카피를 사용하여 콘텐츠 조각 재사용
description: 소스 콘텐츠와 동기화하면서 여러 위치에서 동일하거나 유사한 콘텐츠 조각 콘텐츠를 사용하기 위해 MSM의 라이브 카피 기능을 사용하는 방법에 대해 알아봅니다.
badgeSaas: label="AEM Sites" type="Positive" tooltip="AEM Sites에 적용됩니다)."
feature: Content Fragments
role: User
solution: Experience Manager Sites
hide: true
hidefromtoc: true
index: false
exl-id: 5039cf92-21ff-4d6c-a684-72eab13b519d
source-git-commit: cc3cd74ad87f4213a200f36745ab3d335edca02d
workflow-type: tm+mt
source-wordcount: '950'
ht-degree: 4%

---

# MSM을 사용하여 콘텐츠 조각 재사용 {#reuse-content-fragments-using-msm}

다중 사이트 관리자(MSM) 및 라이브 카피 기능을 사용하면 소스 콘텐츠와 동기화하면서 여러 위치에서 동일한 콘텐츠를 사용할 수 있습니다.

<!-- CQDOC-23473 - feature is currently beta so page is hidden, see metadata -->
<!-- CQDOC-23473 - screenshots -->
<!-- CQDOC-23473 - only mentioned once in ToC, add entries -->
<!-- CQDOC-23473 - will work on folders -->

<!-- CQDOC-23473 - feature is currently beta remove Caution for GA -->

>[!CAUTION]
>
>콘텐츠 조각 콘솔의 MSM은 현재 Beta 기능이며 특정 고객만 사용할 수 있습니다.
>
>콘텐츠 조각용 MSM은 **Assets** 콘솔을 통해 콘텐츠 조각을 사용할 때도 사용할 수 있습니다.

* MSM 라이브 카피를 사용하여 다음과 같은 작업을 수행할 수 있습니다.
   * 컨텐츠 한 번 만들기
   * 동일한 사이트의 다른 영역, 다른 사이트 또는 애플리케이션에서 이 콘텐츠를 재사용합니다.
* 그런 다음 MSM은 소스 콘텐츠와 해당 Live Copy 간의 라이브 관계를 유지하여 다음 작업을 수행합니다.
   * 소스 콘텐츠를 변경하면 소스 및 라이브 카피가 동기화됩니다.
   * 개별 하위 조각 및/또는 구성 요소에 대한 라이브 관계의 연결을 해제하여 라이브 카피의 콘텐츠만 조정할 수 있습니다.

<!-- CQDOC-23473 - feature is currently beta remove Caution for GA -->

MSM 개념에 대한 자세한 개요는 콘텐츠 재사용: 다중 사이트 관리자 및 라이브 카피 를 참조하십시오.

<!--
For a detailed overview of MSM concepts see [Reusing Content: Multi Site Manager and Live Copy](/help/sites-cloud/administering/msm/overview.md).
-->

<!-- CQDOC-23473 - feature is currently beta remove Caution for GA -->

>[!NOTE]
>
>Adobe Experience Manager의 MSM(Multi Site Manager) 기능을 사용하면 한 번 작성된 후 여러 웹 위치에서 재사용되는 콘텐츠를 재사용할 수 있습니다.

<!--
>[!NOTE]
>
>[Multi Site Manager (MSM)](/help/sites-cloud/administering/msm/overview.md) functionality in Adobe Experience Manager enables users to reuse content that is authored once and then reused across multiple web-locations. 
-->

콘텐츠 조각에 MSM을 사용하여 다음과 같은 작업을 수행할 수 있습니다.

* 콘텐츠 조각을 한 번 만든 다음 이러한 조각의 복사본을 만들어(연결) 사이트 또는 애플리케이션의 다른 영역에서 재사용할 수 있습니다.
* 소스 사본을 한 번 업데이트한 다음 변경 사항을 (라이브) 사본으로 푸시하여 여러 사본의 동기화를 유지합니다.
* 상위 조각과 하위 조각 간의 링크를 완전히 또는 해당 변형이나 필드에 대해 일시 중단하거나 영구적으로 중단하여 로컬 변경 작업을 수행합니다.

콘텐츠 조각 편집기 내의 기능과 결합된 콘텐츠 조각용 MSM을 사용하면 필드 수준에서 상속을 중단하거나 복원할 수 있습니다.

<!-- CQDOC-23473 - feature is currently beta remove Caution for GA -->

>[!NOTE]
>
>이 페이지에서는 **콘텐츠 조각** 콘솔을 사용할 때의 MSM 기능을 다룹니다.
>
>콘텐츠 조각용 MSM은 **Assets** 콘솔을 통해 콘텐츠 조각을 사용할 때도 사용할 수 있습니다.

<!--
>[!NOTE]
>
>This page covers MSM functionality when using the **Content Fragments** console.
>
>MSM for Content Fragments is also available when using [Content Fragments via the **Assets** console](/help/assets/content-fragments/content-fragments-msm.md). 
-->

## Live Copy 만들기 {#create-a-live-copy}

<!-- CQDOC-23473 - exclude children or referenced content fragments? -->

콘텐츠 조각의 라이브 카피를 만들려면 다음 작업을 수행하십시오.

1. 콘텐츠 조각 콘솔에서 조각의 위치로 이동합니다.
1. 조각을 선택합니다.
1. 상단 도구 모음에서 **Live Copy 만들기**&#x200B;를 선택합니다.
1. 열려 있는 대화 상자에서 대상을 지정하고 **다음**&#x200B;을 사용하여 계속합니다.
1. 속성을 지정합니다. 제목, 이름 및 라이브 카피에서 하위(중첩된 조각)를 제외할지 여부를 지정할 수 있습니다.
1. **다음**&#x200B;을 사용하여 계속합니다.
1. Live Copy를 즉시 만들지(**지금**) 아니면 **나중에** 날짜 및 시간에 만들지 선택합니다.
1. **Live Copy 만들기**&#x200B;를 사용하여 확인합니다.

   <!-- CQDOC-23473 - feature is currently beta remove Caution for GA -->

   >[!CAUTION]
   >
   >MSM을 사용하여 콘텐츠 조각의 복사본을 만들려면 각 콘텐츠 조각 모델에 사용된 데이터 형식에서 **Unique** 제약 조건을 제거해야 합니다.

   <!--
   >[!CAUTION]
   >
   >If you want to use MSM to create copies of Content Fragments), then any **Unique** constraints should be removed from any Data Types used in the respective [Content Fragment Models](/help/assets/content-fragments/content-fragments-models.md).
   -->

## 속성 및 상태 보기 {#view-properties-and-status}

소스 및 라이브 카피의 속성 및 상태를 보려면 다음 작업을 수행하십시오.

1. 콘텐츠 조각 콘솔에서 조각의 위치로 이동합니다.
1. 조각을 선택합니다.
1. 조각의 **제목** 열에서 정보(i) 아이콘을 선택합니다.
올바른 정보 패널이 열립니다.
1. **Live Copy 세부 정보**&#x200B;에 대한 탭을 선택하십시오.

   ![Live Copy에 대한 정보](/help/sites-cloud/administering/content-fragments/assets/cf-msm-information.png)

## 수정 사항 전파 {#propagate-modifications}

소스와 라이브 카피 간에 수정 사항을 전파합니다.

### 동기화 {#synchronize}

Live Copy에서 소스로 콘텐츠 업데이트를 가져오는 동기화를 트리거하려면 다음을 수행하십시오.

1. 콘텐츠 조각 콘솔에서 조각 소스의 위치로 이동합니다.
1. 조각을 선택합니다.
1. 도구 모음에서 **동기화**&#x200B;를 선택합니다.
1. 대화 상자에서 **동기화**&#x200B;를 확인합니다.

### 롤아웃 {#rollout}

소스 업데이트를 라이브 카피로 푸시하는 롤아웃을 트리거하려면 다음을 수행합니다.

1. 콘텐츠 조각 콘솔에서 조각 라이브 카피의 위치로 이동합니다.
1. 조각을 선택합니다.
1. 도구 모음에서 **롤아웃**&#x200B;을 선택합니다. 프로세스를 안내하는 마법사가 열립니다.
1. 롤아웃에 포함할 라이브 카피를 선택하고 **계속**&#x200B;합니다.
1. 롤아웃을 즉시(**지금**) 또는 **나중에**&#x200B;로 예약하십시오.
1. 필요에 따라 **계속**.

<!-- CQDOC-23473 - feature is beta, is in authoring so remove here when GA -->

## 편집기에서 상속 취소 및 되돌리기 {#cancel-and-revert-to-inheritance-in-the-editor}

상속은 콘텐츠를 한 조각에서 다른 조각으로 자동으로 푸시할 수 있는 메커니즘입니다. 상속된 필드 및 변형은 다중 사이트 관리의 결과일 수 있습니다.

콘텐츠 조각 편집기에서 상속을 취소(그런 다음 되돌리기)할 수 있습니다. 조각이 라이브 카피의 일부인 경우 컨텍스트에 따라 변형에 사용하거나 개별 필드에 사용할 수 있습니다.

예:

* 상속 취소

  ![상속 취소 아이콘](/help/sites-cloud/administering/content-fragments/assets/cf-authoring-cancel-inheritance.png)

* 상속으로 되돌리기(상속이 이미 취소된 경우)

  ![상속으로 되돌리기 아이콘](/help/sites-cloud/administering/content-fragments/assets/cf-authoring-revert-to-inheritance.png)

<!-- CQDOC-23473 - feature is currently beta reinstate Note for GA -->

<!--
## Cancel, and revert to, inheritance {#cancel-and-reinstate-inheritance}

Inheritance is the mechanism where content can be automatically pushed from one fragment to another. Inherited fields, and variations, can be the product of Multi-Site Management.

You can cancel (then revert) the inheritance. Depending on the context, this can be available for a variation, or an individual field, if the fragment is part of a live copy.
-->

<!--
>[!NOTE]
>
>For more details see [Cancel, and revert to, inheritance in the editor](/help/sites-cloud/administering/content-fragments/authoring.md#cancel-and-revert-to-inheritance).
-->

## 콘텐츠 조각 및 사이트 페이지에 대한 MSM 비교 {#compare-msm-for-content-fragments-and-sites-pages}

<!-- CQDOC-23473 - needs a detailed review -->

대부분의 시나리오에서 콘텐츠 조각에 대한 MSM은 사이트 페이지에 대한 MSM 기능의 동작과 일치합니다. 몇 가지 주요 차이점은 다음과 같습니다.

* Sites 페이지용 MSM의 블루프린트는 콘텐츠 조각용 MSM의 라이브 카피 소스라고 합니다.
* 사이트 페이지의 경우 블루프린트와 라이브 카피를 비교할 수 있지만 콘텐츠 조각에서 소스를 라이브 카피와 비교할 수는 없습니다.
* 콘텐츠 조각 콘솔에서는 라이브 카피를 편집할 수 없습니다.
* Sites 페이지에는 일반적으로 하위 항목이 있지만 콘텐츠 조각에는 참조된 조각이 있을 수 있지만 없습니다. 하위 항목을 포함하거나 제외하는 옵션은 이러한 참조된 조각을 참조합니다.
* 콘텐츠 조각용 MSM에서는 사이트 만들기 마법사의 챕터 단계 제거가 지원되지 않습니다.
* 콘텐츠 조각용 MSM에서는 페이지 속성에 대한 MSM 잠금 구성이 지원되지 않습니다.
* 콘텐츠 조각용 MSM의 경우 **표준 롤아웃 구성**&#x200B;만 사용하십시오. 콘텐츠 조각용 MSM에는 다른 롤아웃 구성을 사용할 수 없습니다.

>[!NOTE]
>
>콘텐츠 조각 콘솔을 통해 액세스하는 콘텐츠 조각용 MSM은 Assets 기능을 기반으로 합니다. 이는 해당 콘텐츠가 Assets(사이트 기능으로 간주되지만)로 저장되기 때문입니다.

## 제한 사항 {#limitations}

* 콘텐츠 조각에 대한 수정 시 트리거 및 관련 롤아웃 구성이 존재하지 않습니다.
