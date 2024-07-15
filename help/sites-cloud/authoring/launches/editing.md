---
title: 론치 편집
description: 페이지(또는 페이지 세트)에 대한 론치를 만든 후 페이지의 론치 카피에서 콘텐츠를 편집할 수 있습니다.
exl-id: d3cd3383-e0a0-4019-9f97-8baa3be99e6e
solution: Experience Manager Sites
feature: Authoring, Launches
role: User
source-git-commit: bdf3e0896eee1b3aa6edfc481011f50407835014
workflow-type: tm+mt
source-wordcount: '551'
ht-degree: 87%

---

# 론치 편집 {#editing-launches}

## 론치 편집 페이지 {#editing-launch-pages}

페이지(또는 페이지 세트)에 대한 론치가 만들어지면 페이지의 론치 카피에서 콘텐츠를 편집할 수 있습니다.

1. [참조의 론치(Sites 콘솔)](/help/sites-cloud/authoring/launches/overview.md#launches-in-references-sites-console)에 액세스하여 사용 가능한 동작을 표시합니다.
1. **페이지로 이동**&#x200B;을 선택하여 편집할 페이지를 엽니다.

페이지를 편집할 때 상단 도구 모음에 **나가기** 및 **탐색** 옵션이 표시됩니다.

![페이지 편집기에서 나가기 및 론치 탐색](/help/sites-cloud/authoring/assets/launches-edit-01.png)

>[!NOTE]
>
>론치 내에서 페이지를 이동할 수 없습니다. 이 작업을 시도하면 다음과 같은 경고 메시지가 트리거됩니다.
>
>* 경고: 이 페이지는 론치 소스입니다. 페이지를 이동할 수 없습니다.

### Live Copy에 따른 론치 페이지 편집 {#editing-launch-pages-subject-to-a-live-copy}

론치가 [Live Copy](/help/sites-cloud/administering/msm/overview.md)를 기반으로 하는 경우

* 구성 요소(콘텐츠 및/또는 속성) 편집 시 자물쇠 기호(작은 자물쇠)가 표시됩니다.
* **페이지 속성**&#x200B;의 **Live Copy** 탭이 표시됩니다.

Live Copy는 *소스 분기에서* *론치 분기로* 콘텐츠를 동기화하여 소스에 적용된 변경 내용으로 론치를 최신 상태로 유지하는 데 사용됩니다.

표준 Live Copy를 편집하는 것과 동일한 방법으로 변경 작업을 수행할 수 있습니다. 예를 들면 다음과 같습니다.

* 닫힌 자물쇠를 클릭하면 이 동기화가 중단되고 론치에서 콘텐츠를 새로 업데이트할 수 있습니다. 잠금 해제되면(열려 있는 자물쇠) 사용자가 수행한 변경 내용을 소스 분기 내의 동일한 위치에 수행된 변경 내용이 덮어쓰지 않습니다.
* 특정 페이지에 대한 상속을 **일시 중단**(및 **다시 시작**)합니다.

자세한 내용은 [Live Copy 콘텐츠 변경](/help/sites-cloud/administering/msm/creating-live-copies.md)을 참조하십시오.

## 론치 페이지를 소스 페이지에 비교 {#comparing-a-launch-page-to-its-source-page}

적용한 변경 내용을 추적하기 위해 **참조**&#x200B;에서 론치를 확인하고 론치 페이지를 소스 페이지와 비교할 수 있습니다.

1. **사이트** 콘솔에서 [론치의 소스 페이지를 검색한 다음 그 중 하나를 선택합니다](/help/sites-cloud/authoring/basic-handling.md#viewing-and-selecting-resources).
1. **[참조](/help/sites-cloud/authoring/basic-handling.md#references)** 패널을 열고 **론치**&#x200B;를 선택합니다.
1. 특정 론치를 선택한 다음, **소스와 비교**&#x200B;를 선택합니다.

   ![론치를 소스와 비교](/help/sites-cloud/authoring/assets/launches-compare.png)

1. 두 페이지(론치 및 소스)가 나란히 열립니다.

   이 기능의 사용에 대한 자세한 내용은 [페이지 비교](/help/sites-cloud/authoring/sites-console/page-diff.md)를 참조하십시오.

## 사용된 소스 페이지 변경 {#changing-the-source-pages-used}

언제든지 론치용 소스 페이지의 범위에 페이지를 추가하거나 이 범위에서 페이지를 제거할 수 있습니다.

1. 다음 중 하나에서 론치에 액세스하여 선택합니다.
   * [론치 콘솔](/help/sites-cloud/authoring/launches/overview.md#the-launches-console):
      * **편집**&#x200B;을 선택합니다.
   * 사용 가능한 작업을 표시하려면 [참조(Sites 콘솔)](/help/sites-cloud/authoring/launches/overview.md#launches-in-references-sites-console)를 사용하십시오.
      * **론치 편집**&#x200B;을 선택하십시오.
      * 소스 페이지가 표시됩니다.
1. 필요한 변경 내용을 적용한 다음 **저장**&#x200B;을 사용하여 확인합니다.

>[!NOTE]
>
>페이지를 론치에 추가하려면 페이지가 일반 언어 루트 아래(예: 단일 사이트 내)에 있어야 합니다.

## 론치 구성 편집 {#editing-a-launch-configuration}

언제든지 론치의 속성을 편집할 수 있습니다.

1. 다음 중 하나에서 론치에 액세스하여 선택합니다.
   * [론치 콘솔](/help/sites-cloud/authoring/launches/overview.md#the-launches-console):
      * **속성**&#x200B;을 선택하십시오.
   * 사용 가능한 작업을 표시하려면 [참조(Sites 콘솔)](/help/sites-cloud/authoring/launches/overview.md#launches-in-references-sites-console)를 사용하십시오.
      * **속성 편집**&#x200B;을 선택하십시오.
      * 세부 사항이 표시됩니다.
1. 필요한 변경 내용을 적용한 다음 **저장**&#x200B;을 사용하여 확인합니다.
   * **실행 날짜** 및 **프로덕션 준비** 필드의 목적과 상호 작용에 대한 정보는 [론치 - 이벤트 순서](/help/sites-cloud/authoring/launches/overview.md#launches-the-order-of-events)를 참조하십시오.

## 페이지의 론치 상태 찾기 {#discovering-the-launch-status-of-a-page}

참조 탭에서 특정 론치를 선택하면 상태가 표시됩니다([참조(Sites 콘솔)의 론치](/help/sites-cloud/authoring/launches/overview.md#launches-in-references-sites-console) 참조).

![론치 상태 찾기](/help/sites-cloud/authoring/assets/launches-status.png)
