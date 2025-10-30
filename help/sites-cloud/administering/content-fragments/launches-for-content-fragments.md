---
title: 콘텐츠 조각용 론치
description: Adobe Experience Manager as a Cloud Service에서 컨텐츠 조각용 런치를 사용하는 방법을 알아봅니다. 론치를 사용하면 현재 콘텐츠 조각을 유지하면서 향후 릴리스용 콘텐츠를 효율적으로 개발할 수 있습니다.
feature: Content Fragments
role: User, Developer, Architect
solution: Experience Manager Sites
exl-id: c0b9e571-3be5-42ab-8d56-d93e8ef4c2f7
source-git-commit: 39ff527f0082a18f0853964172eabf438caa1098
workflow-type: tm+mt
source-wordcount: '1582'
ht-degree: 2%

---

# 콘텐츠 조각용 론치 {#launches-for-content-fragments}

Adobe Experience Manager(AEM) as a Cloud Service에서 론치를 사용하면 향후 릴리스를 위한 콘텐츠를 효율적으로 개발할 수 있습니다.

*Launch*&#x200B;을(를) 만들어 현재 콘텐츠를 유지 관리하는 동시에 나중에 게시할 준비를 변경할 수 있도록 합니다. 콘텐츠 조각의 경우 현재 게시된 콘텐츠와 향후 한 번에 게시될 해당 콘텐츠의 버전, 이렇게 두 버전을 동시에 효과적으로 편집하는 것입니다. 해당 시간이 되면 원래 콘텐츠 조각의 콘텐츠를 대체하고 새 버전을 게시할 수 있습니다.

>[!NOTE]
>
>페이지에 대해서도 론치를 사용할 수 있습니다. 기본 개념은 같지만 AEM에서 관리하는 방법에 차이가 있다.
>
>자세한 내용은 [페이지 시작](/help/sites-cloud/authoring/launches/overview.md)을 참조하세요.

*Launch*&#x200B;을(를) 만든 다음 *Launch*&#x200B;에서 콘텐츠 조각을 편집하고 업데이트합니다. 이 단계에서 *Source* 조각이 변경되면 *Rebase* 작업을 사용하여 *Launch*&#x200B;에 복사할 수 있습니다. 준비가 되면 *홍보*&#x200B;에서 시작 콘텐츠를 다시 소스로 복제합니다. 그런 다음 론치를 만들고 편집할 때 설정된 필드에 따라 소스 조각을 수동 또는 자동으로 활성화할 수 있습니다. 참조된 조각을 이 프로세스에 포함할지 여부를 지정할 수도 있습니다.

예를 들어 온라인 스토어의 계절별 제품 조각은 주력 제품이 현재 계절과 일치하도록 분기별로 업데이트됩니다. 다음 분기별 업데이트를 준비하기 위해 적절한 조각의 시작을 만들 수 있습니다. 분기 내내, 론치 사본에 다음 변경 사항이 누적되었습니다.

* 다음 분기를 준비하기 위해 론치 조각에서 직접 수행되는 편집.
* *Rebase*&#x200B;을(를) 사용하여 시작 페이지로 전송하는 원본 콘텐츠 조각에 대한 변경 사항입니다.
* 론치 분기에서 컨텐츠를 탐색할 수도 있습니다. 필요에 따라 조각을 추가하거나 제거할 수 있습니다.

다음 분기가 되면 소스 페이지(업데이트된 콘텐츠 보관 중)를 게시할 수 있도록 론치 페이지를 홍보합니다. 모든 조각을 홍보하거나 수정한 조각만 홍보할 수 있습니다.

![시작 개요 - 다시 보고 승격](/help/sites-cloud/administering/content-fragments/assets/cf-launches-overview.png)

이 섹션에서는 [콘텐츠 조각 콘솔](/help/sites-cloud/administering/content-fragments/managing.md)에서 시작, 만들기, 편집, 관리, 기준 재지정, 승격 및 필요한 경우 삭제하는 방법에 대해 설명합니다.

* [콘텐츠 조각 콘솔에서 론치 액세스 및 보기](#launches-in-the-content-fragment-console)
* [론치 만들기](#create-a-launch)
* [론치 콘텐츠 편집](#edit-launch-content)
* [론치 내 콘텐츠 관리](#manage-content-within-a-launch)
* [론치를 소스와 비교](#compare-launch-to-source)
* [Source에서 론치 다시 기준](#rebase-a-launch-from-source)
* [Source에 론치 홍보](#promote-a-launch-to-source)
* [론치 삭제](#delete-a-launch)

## 콘텐츠 조각 콘솔에서 론치 {#launches-in-the-content-fragment-console}

콘텐츠 조각 콘솔의 **론치** 탭에서는 론치를 만들고, 기존의 모든 론치를 나열하고, 주요 속성을 확인하고, 이에 대한 작업을 수행할 수 있습니다.

시작을 선택하지 않으면 [새 시작을 만들 수 있습니다](#create-a-launch).

콘솔의 ![시작 탭](/help/sites-cloud/administering/content-fragments/assets/cf-launches-tab.png)

표시할 론치를 선택합니다.

* 도구 모음(사용 가능한 작업 포함)
* 오른쪽 패널, 속성 및 추가 작업 표시

![콘솔의 실행 작업 도구 모음](/help/sites-cloud/administering/content-fragments/assets/cf-launches-actions.png)

도구 모음을 사용하여 다음 작업을 수행할 수 있습니다.

* **[시작 열기](#edit-launch-content)**
* **[소스 편집](#manage-content-within-a-launch)**
* **[Launch와 Source 비교](#compare-launch-to-source)**
* **[홍보](#promote-a-launch-to-source)**
* **[기준 재지정](#promote-a-launch-to-source)**
* **[시작 삭제](#delete-a-launch)**

오른쪽 패널을 사용하면 다음 작업을 수행할 수 있습니다.

* 시작 **제목** 편집
* 시작 **설명** 편집
* [시작을 만들었을 때](#create-a-launch)에 설정된 구성 세부 정보를 업데이트하십시오.

   * **참조 포함**: 참조된 콘텐츠 조각을 포함하여 또는 포함하지 않고 론치를 만듭니다. 기본적으로 참조된 조각이 포함됩니다.

      * 참조된 조각은 나중에 [시작에서 조각을 추가 또는 제거](#manage-content-within-a-launch)할 때도 영향을 받습니다.

     >[!NOTE]
     >
     >[포함된 참조에 대한 세부 정보](#details-concerning-included-references)를 참조하세요.

   * **게시 준비**; 이 토글을 활성화하면 시작이 소스로 승격될 때 조각이 자동으로 게시됩니다.

* 또한 다음을 정의합니다.

   * **홍보 날짜** 및 시간: [출시를 자동으로 홍보하는 경우](#promote-automatically)

## 론치 만들기 {#create-a-launch}

론치를 만들려면 다음 작업을 수행하십시오.

1. 콘텐츠 조각 콘솔로 이동합니다.

1. **시작** 탭을 엽니다.

1. **시작 만들기**&#x200B;를 선택합니다.

1. 해당 폴더로 이동하고 론치에 포함할 조각을 선택합니다.

   ![새 실행을 위한 콘텐츠 조각 선택](/help/sites-cloud/administering/content-fragments/assets/cf-launches-create-select-cfs.png)

1. **다음**&#x200B;을 선택합니다.

1. 론치를 구성할 세부 사항을 지정합니다.

   * **제목**
   * **설명**
   * **참조 포함**: 참조된 콘텐츠 조각을 포함하여 또는 포함하지 않고 론치를 만듭니다. 기본적으로 참조된 조각이 포함됩니다.

     >[!NOTE]
     >
     >[포함된 참조에 대한 세부 정보](#details-concerning-included-references)를 참조하세요.

   * **게시 준비**: 이 토글을 사용하면 출시가 소스로 승격될 때 조각이 자동으로 게시됩니다.

   ![새 시작 세부 정보](/help/sites-cloud/administering/content-fragments/assets/cf-launches-create-launch-details.png)

1. 구성을 **저장**&#x200B;합니다.

1. 콘텐츠 조각 콘솔의 **시작** 탭으로 돌아갑니다. 여기서 다음을 수행합니다.

   * 이제 새 론치가 나열됩니다.
   * launch 생성이 시작되었음을 확인하는 메시지가 표시됩니다.

      * **새 Launch를 만들고, AEM에서 진행 상황을 모니터링하고, 완료되면 페이지를 다시 로드하기 위해 작업이 시작되었습니다.**

1. **백그라운드 작업**&#x200B;에 대한 AEM 콘솔에서 자세한 내용을 보려면 메시지 상자에서 [보기](/help/operations/asynchronous-jobs.md)를 선택하십시오.

   ![콘솔의 새 실행](/help/sites-cloud/administering/content-fragments/assets/cf-launches-new-launch-in-console.png)

## 론치 콘텐츠 편집 {#edit-launch-content}

론치에서 콘텐츠 조각을 편집하려면 다음 작업을 수행하십시오.

1. 콘텐츠 조각 콘솔로 이동합니다.

1. **시작** 탭을 엽니다.

1. 론치를 선택하여 도구 모음 작업을 표시합니다.

1. **시작 열기**&#x200B;를 선택합니다.

   론치가 보유한 조각과 함께 표시됩니다.

   ![시작 콘텐츠 편집](/help/sites-cloud/administering/content-fragments/assets/cf-launches-edit-launch-content.png)

1. 업데이트할 조각에 대해 **편집**&#x200B;을(를) 선택하십시오. 평소대로 [조각 편집기](/help/sites-cloud/administering/content-fragments/authoring.md)에서 열립니다.

## 론치 내 콘텐츠 관리 {#manage-content-within-a-launch}

론치에서 콘텐츠 조각을 관리하고 콘텐츠를 편집하려면 다음을 수행하십시오.

1. 콘텐츠 조각 콘솔로 이동합니다.

1. **시작** 탭을 엽니다.

1. 론치를 선택합니다.

1. **소스 편집**&#x200B;을 선택합니다.

   론치의 소스 조각이 표시됩니다.

   ![Source 편집](/help/sites-cloud/administering/content-fragments/assets/cf-launches-edit-sources.png)

1. 다음과 같은 작업을 수행할 수 있습니다.

   1. 론치에 더 많은 조각을 추가하려면 **소스를 추가**&#x200B;하세요.

      * 시작에 대해 **참조 포함**&#x200B;이 true인 경우 참조된 모든 콘텐츠 조각은 시작에도 가져옵니다(아직 없는 경우).

   1. 업데이트할 원본 조각에 대해 **편집**&#x200B;을(를) 선택하십시오. 평소대로 [조각 편집기](/help/sites-cloud/administering/content-fragments/authoring.md)에서 열립니다.

   1. 조각을 선택한 다음 도구 모음에서 **소스 삭제** 작업을 선택하여 시작에서 해당 조각을 제거합니다.

      * 론치에 대해 **참조 포함**&#x200B;이(가) true인 경우 아직 론치에 있는 다른 콘텐츠 조각에서 참조하지 않는 한 참조된 모든 콘텐츠 조각도 론치에서 제거됩니다.

   >[!NOTE]
   >
   >[포함된 참조에 대한 세부 정보](#details-concerning-included-references)를 참조하세요.

## 론치를 소스와 비교 {#compare-launch-to-source}

재설정 또는 홍보 작업을 수행하기 전에 항상 소스와 론치를 비교하여 변경 사항과 콘텐츠에 미치는 영향을 확인하는 것이 좋습니다(두 작업 모두 타겟 콘텐츠를 덮어씀).

1. 콘텐츠 조각 콘솔로 이동합니다.

1. **시작** 탭을 엽니다.

1. 론치를 선택합니다.

1. **Launch와 Source 비교**&#x200B;를 선택합니다.

   * 소스 조각과 론치 조각이 나란히 표시되어 차이점을 강조 표시합니다.
      * Source 조각은 왼쪽에 표시되고 Launch 조각은 오른쪽에 표시됩니다.
      * 업데이트가 강조 표시됩니다.
         * Source: 파란색
         * 시작: 분홍색
         * 충돌: 노란색
   * [Promote](#promote-a-launch-to-source) 및 [Rebase](#rebase-a-launch-from-source) 작업은 오른쪽 상단에서 사용할 수 있습니다.
   * **업데이트를 찾았습니다**: 왼쪽 위에 모든 업데이트에 대한 요약이 표시됩니다. 소스 업데이트 수는 파란색, 론치 업데이트 수는 분홍색, 두 업데이트(충돌) 수는 노란색으로 표시됩니다.
      * 눈 모양 아이콘을 사용하면 더 명확한 개요를 위해 실제 콘텐츠 업데이트를 표시하거나 숨길 수 있습니다.
   * **포함** 슬라이더를 사용하면 후속 승격 또는 기준 재지정 작업에 포함할 콘텐츠 조각을 정의할 수 있습니다.
      * 오른쪽 상단의 **모두 포함**
      * 시작의 모든 조각 위에 **포함**

     >[!NOTE]
     >
     >슬라이더는 비교 화면에서 수행한 프로모트 및 기준 재지정 작업에만 적용됩니다.

   * 조각 컨텐츠는 필드 수준(컨텐츠 조각 요소/데이터 유형 수준)에 표시되며, 변경 사항을 나타내는 강조 표시가 있습니다.
   * **보기**&#x200B;를 선택하여 차이점을 다시 계산합니다.

   ![Source과 Launch 비교](/help/sites-cloud/administering/content-fragments/assets/cf-launches-compare.png)

## 론치 기준 재지정(Source) {#rebase-a-launch-from-source}

소스 조각이 업데이트되고 이러한 변경 사항을 론치에 복사하려는 경우:

1. 콘텐츠 조각 콘솔로 이동합니다.

1. **시작** 탭을 엽니다.

1. 론치와 조각을 선택합니다.

1. **기준 재지정**&#x200B;을 선택합니다.

>[!NOTE]
>
>**Launch와 Source 비교**&#x200B;에서 시작을 **[다시 설정](#compare-launch-to-source)**&#x200B;할 수도 있습니다.

## 론치 홍보(Source) {#promote-a-launch-to-source}

론치를 게시할 준비가 되면 소스에 복사해야 합니다. 콘솔에서 이 작업을 수행하거나 특정 날짜 및 시간에 자동으로 수행되도록 설정을 구성할 수 있습니다.

### 수동으로 승격 {#promote-manually}

론치를 게시할 준비가 되면 명시적 작업으로 소스에 복사할 수 있습니다.

1. 콘텐츠 조각 콘솔로 이동합니다.

1. **시작** 탭을 엽니다.

1. 론치와 조각을 선택합니다.

1. **홍보**&#x200B;를 선택합니다.

>[!NOTE]
>
>**론치를 Source과 비교**&#x200B;에서 론치를 **홍보**&#x200B;할 수도 있습니다.

### 자동 승격 {#promote-automatically}

론치를 지정된 날짜 및 시간에 자동으로 홍보하려면 다음을 수행해야 합니다.

1. **시작 탭**&#x200B;의 오른쪽 패널에서 [승격 날짜](#launches-in-the-content-fragment-console) 및 시간을 정의합니다.

1. 콘텐츠가 홍보될 때 게시될 수 있는 경우 **시작을 만들 때** 또는 [시작 탭](#create-a-launch)의 오른쪽 패널에서 [게시 준비](#launches-in-the-content-fragment-console)를 설정하십시오.

## 론치 삭제 {#delete-a-launch}

론치를 홍보하거나 더 이상 필요하지 않다고 결정한 후 삭제할 수 있습니다.

1. 콘텐츠 조각 콘솔로 이동합니다.

1. **시작** 탭을 엽니다.

1. 론치를 선택합니다.

1. **시작 삭제**&#x200B;를 선택합니다.

   론치를 삭제하기 전에 작업을 확인하라는 메시지가 표시됩니다.

## 포함된 참조에 대한 세부 사항 {#details-concerning-included-references}

시작의 경우 [데이터 형식](/help/sites-cloud/administering/content-fragments/content-fragment-models.md#data-types)에 따라 다음 콘텐츠 조각 참조가 고려됩니다.

* 단일 조각 참조와 다중 필드 조각 참조 모두에 적용할 수 있는 **조각 참조** 데이터 형식입니다.
* **서식 있는 텍스트**&#x200B;를 사용할 때 **여러 줄 텍스트** 데이터 형식 내에서 참조되는 조각입니다.

모든 지점은 변형 내에서 참조된 조각에도 적용할 수 있습니다

다음은 고려되지 않습니다.

* 콘텐츠 참조 데이터 형식 내에서 참조된 조각으로, **콘텐츠 참조**(경로 기반) 및 **콘텐츠 참조(UUID)**&#x200B;입니다.
* **조각 참조(UUID)** 데이터 형식 내에서 참조된 조각입니다.
