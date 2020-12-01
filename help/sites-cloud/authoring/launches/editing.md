---
title: 론치 편집
description: '페이지(또는 페이지 세트)에 대한 론치를 만들면 페이지의 론치 카피에서 컨텐츠를 편집할 수 있습니다. '
translation-type: tm+mt
source-git-commit: 914eb7f7b040b99c11d9f109549eb13868058320
workflow-type: tm+mt
source-wordcount: '521'
ht-degree: 81%

---


# 론치 편집 {#editing-launches}

## 론치 편집 페이지 {#editing-launch-pages}

페이지(또는 페이지 세트)에 대한 론치가 만들어지면 페이지의 론치 카피에서 컨텐츠를 편집할 수 있습니다.

1. [참조의 론치(사이트 콘솔)](/help/sites-cloud/authoring/launches/overview.md#launches-in-references-sites-console)에 액세스하여 사용 가능한 동작을 표시합니다.
1. **페이지로 이동**&#x200B;을 선택하여 편집할 페이지를 엽니다.

페이지를 편집할 때 위쪽 도구 모음에는 **Leave** 및 **Navigate** 옵션과 함께 표시됩니다.

![페이지 편집기에서 시작 및 탐색](/help/sites-cloud/authoring/assets/launches-edit-01.png)

### Live Copy에 따른 론치 페이지 편집 {#editing-launch-pages-subject-to-a-live-copy}

론치가 live copy를 기반으로 하는 경우 다음을 수행합니다.<!--If your launch is based upon a [live copy](/help/sites-administering/msm.md) then you will:-->

* 구성 요소(컨텐츠 및/또는 속성)를 편집할 때 잠금 기호(작은 자물쇠)를 참조하십시오.
* **페이지 속성**&#x200B;의 **Live Copy** 탭을 참조하십시오.

Live Copy는 소스 분기&#x200B;*의* 컨텐츠를 론치 분기&#x200B;*에* 동기화(소스에서 이루어진 변경 내용으로 론치를 최신 상태로 유지)하는 데 사용됩니다.

표준 Live Copy를 편집하는 것과 동일한 방법으로 변경 작업을 수행할 수 있습니다. 예를 들면 다음과 같습니다.

* 닫힌 자물쇠를 클릭하면 이 동기화가 중단되고 론치에서 컨텐츠를 새로 업데이트할 수 있습니다. 잠금 해제되면(열려 있는 자물쇠) 사용자가 수행한 변경 내용을 소스 분기 내의 동일한 위치에 수행된 변경 내용이 덮어쓰지 않습니다.
* **특정 페이지에 대한 상속을 일시 중단** (및  **다시 시작**)합니다.

자세한 내용은 Live Copy 컨텐츠 변경을 참조하십시오. <!--See [Changing Live Copy Content](/help/sites-administering/msm-livecopy.md#changing-live-copy-content) for further information.-->

## 론치 페이지를 소스 페이지에 비교 {#comparing-a-launch-page-to-its-source-page}

수행한 변경 작업을 추적하기 위해 **참조**&#x200B;에서 론치를 보고 론치 페이지를 소스 페이지와 비교할 수 있습니다.

1. **사이트** 콘솔에서 [론치의 소스 페이지로 이동하고 하나](/help/sites-cloud/authoring/getting-started/basic-handling.md#viewing-and-selecting-resources)을 선택합니다.
1. **[참조](/help/sites-cloud/authoring/getting-started/basic-handling.md#references)** 패널을 열고 **론치**&#x200B;를 선택합니다.
1. 특정 론치를 선택한 다음, **소스와 비교**&#x200B;를 선택합니다.

   ![론치와 소스 비교](/help/sites-cloud/authoring/assets/launches-compare.png)

1. 두 페이지(론치와 소스)가 나란히 열립니다.

   이 기능의 사용에 대한 자세한 내용은 [페이지 비교](/help/sites-cloud/authoring/features/page-diff.md)를 참조하십시오.

## 사용된 소스 페이지 변경  {#changing-the-source-pages-used}

언제든지 론치용 소스 페이지의 범위에 페이지를 추가하거나 이 범위에서 페이지를 제거할 수 있습니다.

1. 다음 중 하나에서 론치에 액세스하여 선택합니다.
   * [론치 콘솔](/help/sites-cloud/authoring/launches/overview.md#the-launches-console):
      * **편집**&#x200B;을 선택하십시오.
   * 사용 가능한 작업을 표시하려면 [참조(사이트 콘솔)](/help/sites-cloud/authoring/launches/overview.md#launches-in-references-sites-console)를 사용하십시오.
      * **론치 편집**&#x200B;을 선택하십시오.
      * 소스 페이지가 표시됩니다.
1. 필요한 변경 작업을 수행한 다음, **저장**&#x200B;하여 변경을 확인합니다.

>[!NOTE]
>
>페이지를 론치에 추가하려면 페이지가 일반 언어 루트 아래(즉, 단일 사이트 내)에 있어야 합니다.

## 론치 구성 편집  {#editing-a-launch-configuration}

언제든지 론치의 속성을 편집할 수 있습니다.

1. 다음 중 하나에서 론치에 액세스하여 선택합니다.
   * [론치 콘솔](/help/sites-cloud/authoring/launches/overview.md#the-launches-console):
      * **속성**&#x200B;을 선택하십시오.
   * 사용 가능한 작업을 표시하려면 [참조(사이트 콘솔)](/help/sites-cloud/authoring/launches/overview.md#launches-in-references-sites-console)를 사용하십시오.
      * **속성 편집**&#x200B;을 선택하십시오.
      * 세부 사항이 표시됩니다.
1. 필요한 변경 작업을 수행한 다음, **저장**&#x200B;하여 변경을 확인합니다.
   * **론치 날짜** 및 **프로덕션 준비** 필드들의 목적과 상호 작용에 대해 알려면 [론치 - 이벤트 순서](/help/sites-cloud/authoring/launches/overview.md#launches-the-order-of-events)를 참조하십시오.

## 페이지의 론치 상태 찾기  {#discovering-the-launch-status-of-a-page}

참조 탭에서 특정 론치를 선택하면 상태가 표시됩니다([참조(사이트 콘솔)의 론치](/help/sites-cloud/authoring/launches/overview.md#launches-in-references-sites-console) 참조).

![시작 상태 검색](/help/sites-cloud/authoring/assets/launches-status.png)
