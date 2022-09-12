---
title: 페이지 비교
description: 페이지 비교 기능을 사용하면 두 페이지를 둘 사이의 차이점이 강조 표시된 상태로 편리하게 나란히 비교할 수 있습니다.
exl-id: 6e5c7f14-c980-48e3-8bdd-a7ec10a9e680
source-git-commit: 90de3cf9bf1c949667f4de109d0b517c6be22184
workflow-type: tm+mt
source-wordcount: '622'
ht-degree: 100%

---

# 페이지 비교 {#page-diff}

## 소개 {#introduction}

콘텐츠 작성은 반복적 프로세스입니다. 효율적인 작성을 위해서는 한 번 반복할 때마다 변경된 내용을 확인할 수 있어야 합니다. 한 페이지 버전을 확인한 다음, 다른 한 버전을 확인하는 것은 비효율적이며 오류가 발생하기 쉽습니다. 작성자는 현재 페이지를 다른 버전과 나란히 쉽게 비교할 수 있기를 바랍니다.

페이지 비교 기능을 사용하면 두 페이지를 둘 사이의 차이점이 강조 표시된 상태로 편리하게 나란히 비교할 수 있습니다.

>[!NOTE]
>
>이 기능을 사용하려면 사용자에게 **노드에 대한**&#x200B;수정/만들기/삭제`/content/versionhistory` 권한이 있어야 합니다.
>
>이 기능에 대한 자세한 내용은 [개발 및 페이지 비교](/help/implementing/developing/introduction/page-diff.md#operation-details)를 참조하십시오.

## 사용 {#use}

이러한 병렬 비교에서 비교할 수 있는 내용은 다음과 같습니다.

* [버전](/help/sites-cloud/authoring/features/page-versions.md#comparing-a-version-with-current-page) - 페이지의 이전 버전과 현재 상태
* [](/help/sites-cloud/administering/msm/creating-live-copies.md#comparing-a-live-copy-page-with-a-blueprint-page)Live Copy - Live Copy와 블루프린트
* [론치](/help/sites-cloud/authoring/launches/editing.md#comparing-a-launch-page-to-its-source-page) - 론치와 소스
* [](/help/sites-cloud/administering/translation/managing-projects.md#comparing-language-copies)언어 사본 - (재)번역 전후 페이지

해당 컨텍스트 내에서 비교를 시작하는 방법에 대한 각 주제를 참조하십시오.

### 차이점 표시 방법 {#presentation-of-differences}

비교하는 콘텐츠에 관계없이 차이점 표시 방법은 동일하게 유지됩니다.

* 비교를 시작할 때 선택한 콘텐츠는 왼쪽(비교 시작 지점)에 표시됩니다.
* 비교 대상 콘텐츠는 오른쪽(선택한 콘텐츠를 비교할 대상)에 표시됩니다.

예를 들어 버전을 비교하는 경우 현재 버전은 왼쪽에 표시되고 이전 버전이 오른쪽에 표시됩니다.

두 페이지의 소스는 브라우저 창의 맨 위에 있는 헤더 막대에 명확하게 표시됩니다.

![버전 나란히 보기](/help/sites-cloud/authoring/assets/versions-side-by-side.png)

비교에서는 변경 사항이 구성 요소와 HTML 수준에서 감지되고, 변경된 항목은 다른 색상으로 강조 표시됩니다.

**구성 요소 변경 사항**

* 연한 녹색 - 추가된 구성 요소
* 분홍색 - 제거된 구성 요소

**HTML 변경 사항**

* 진한 녹색 - 추가된 HTML
* 빨간색 - 제거된 HTML

>[!NOTE]
>
>번역에서는 모든 것이 변경되어 강조 표시가 아무런 소용이 없으므로 언어 사본을 비교할 때에는 강조 표시가 비활성화됩니다.

### 전체 화면 및 종료 {#fullscreen-and-exiting}

특정 콘텐츠에 집중할 수 있도록 병렬 비교의 어느 &quot;한 쪽&quot;에 대한 전체 화면 아이콘을 클릭하여 전체 브라우저 창으로 확대할 수 있습니다.

![전체 화면 버튼](/help/sites-cloud/authoring/assets/versions-full-screen.png)

선택한 쪽이 전체 창을 채우지만, 막대는 두 페이지 간에 전환할 수 있도록 맨 위에 남아 있습니다.

![전체 화면 모드](/help/sites-cloud/authoring/assets/versions-full-screen-mode.png)

>[!NOTE]
>
>브라우저 너비가 전체 화면 보기에서 두 페이지 이름을 모두 수용할 수 없는 경우 표시되는 페이지의 이름만 표시되고 다른 이름은 생략 부호 뒤에 사용할 수 있습니다.

전체 화면 종료 아이콘을 클릭하여 전체 화면 보기를 닫을 수도 있습니다.

![전체 화면 모드 종료](/help/sites-cloud/authoring/assets/versions-exit-full-screen.png)

언제든지 헤더에서 [닫기] 버튼을 클릭하여 병렬 비교를 종료할 수 있습니다.

## 제한 사항 {#limitations}

페이지 비교 시 차이점이 예상대로 감지되지 않을 수 있습니다.

* 버전과 론치를 비교할 때, 탐색 표시, 메뉴, 제품 목록 또는 로고(콘텐츠를 렌더링하기 위해 사이트 구조에 의존하는 구성 요소)와 같은 동적 구성 요소는 고려되지 않습니다.
* 버전의 경우 비교 기능을 사용하면 액세스 제어 정책 및 라이브 카피 관계가 다시 생성되지 않습니다.
* 페이지가 이동되면 이동 전에 만든 버전으로 더 이상 다른 작업을 수행할 수 없습니다.
   * 차이에 문제가 발생한 경우 페이지에 대한 [타임라인](/help/sites-cloud/authoring/getting-started/basic-handling.md#timeline)에서 페이지가 이동되었는지 확인합니다.

>[!NOTE]
>
>버전을 서로 비교할 수 없습니다. 현재 버전만 페이지의 다른 버전과 비교할 수 있습니다. 현재 버전은 항상 변경 사항이 강조 표시된 버전입니다.

>[!NOTE]
>
>페이지 차이 메커니즘 작업 및 페이지 차이에 영향을 줄 수 있는 제한 사항에 대한 자세한 내용은 이 기능의 [개발자 설명서](/help/implementing/developing/introduction/page-diff.md)를 참조하십시오.
