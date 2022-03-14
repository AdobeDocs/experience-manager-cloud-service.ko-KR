---
title: 저장소 브라우저
seo-title: Repository Browser
description: 저장소 브라우저는 작성자, 게시 및 미리 보기 계층의 모든 환경을 위한 저장소에 읽기 전용 보기를 제공합니다.
seo-description: The repository browser provides a read-only view into the repository for all environments on author, publish, and preview tiers.
source-git-commit: 76e28ca5628fb985df21f53d1c3e9898985dc736
workflow-type: tm+mt
source-wordcount: '781'
ht-degree: 2%

---


# 저장소 브라우저 {#repository-browser}

>[!NOTE]
>
>저장소 브라우저는 AEM 버전 6582 이상에서 사용할 수 있습니다.

## 소개 {#introduction}

저장소 브라우저는 작성, 게시 및 미리 보기 계층의 모든 환경을 위한 저장소에 읽기 전용 보기를 제공하는 개발자 도구입니다. 컨텐츠를 보다 쉽게 보거나 디버깅할 수 있도록 컨텐츠 구조를 쉽게 볼 수 있도록 설계되었습니다.

개발자 콘솔에서 액세스할 수 있는 이 콘솔을 사용하여 선택한 환경에 대한 작성자 또는 게시 인스턴스의 저장소를 찾아볼 수 있습니다.

### 액세스 사전 요구 사항 {#access-prerequisites}

개발자 콘솔 또는 저장소 브라우저에 액세스하려면 다음 조건을 충족해야 합니다

개발자 콘솔에 액세스하려면:

* 프로덕션 프로그램의 경우 사용자에게 **Cloud Manager - 개발자 역할** Admin Console
* 샌드박스 프로그램의 경우 제품 프로필이 있는 모든 사용자가 AEM as a Cloud Service에 액세스할 수 있습니다.

저장소 브라우저에 액세스하려면

* 사용자에게 **Cloud Manager - 개발자** 작성자 및 게시 인스턴스를 보는 Admin Console의 역할입니다.
* 또한 작성자의 경우 AEM Users Product Profile을 사용하는 사용자는 최소한의 읽기 권한으로 저장소 브라우저를 볼 수 있습니다. 리포지토리를 검색할 때 사용자의 권한이 존중됩니다. AEM Administrators 제품 프로필을 가진 사용자는 전체 읽기 권한이 있는 저장소 브라우저를 볼 수 있습니다.

사용자 권한 설정에 대한 자세한 내용은 [Cloud Manager 설명서](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/requirements/setting-up-users-and-roles.html).

### 저장소 브라우저 시작 {#launching-the-repository-browser}

아래 절차에 따라 저장소 브라우저를 시작할 수 있습니다.

1. Cloud Manager에서 선택한 환경 옆의 세 점을 클릭하고 을 선택합니다 **개발자 콘솔**

   ![재브라우저1](/help/implementing/developing/tools/assets/repobrowser1.png)

1. 그런 다음 **저장소 브라우저** 탭
1. 아이콘을 클릭하여 작성자, 게시 또는 미리 보기에 해당하는 Pod를 선택합니다 **Pod** 드롭다운 목록.

   ![repobrowser2](/help/implementing/developing/tools/assets/repobrowser2.png)

1. 을 클릭하여 저장소 브라우저를 시작합니다 **저장소 브라우저 열기** 더 아래로 연결합니다. 선택한 계층의 대표 인스턴스(pod)에 해당하는 브라우저를 시작합니다. 선택한 계층의 대표 인스턴스(pod)에 해당하는 브라우저를 시작합니다. 실행된 계층의 특정 pod는 제어할 수 없습니다.

## 기능 {#features}

### 계층 탐색 {#navigate-the-hierarchy}

왼쪽 탐색 창을 사용하여 컨텐츠 계층 구조를 탐색할 수 있습니다. 각 폴더 또는 노드를 클릭하면 하위 폴더가 표시됩니다. 폴더 구조는 JCR 노드 트리의 수퍼 셋인 Sling 리소스 트리를 반영합니다.

![repobrowser3](/help/implementing/developing/tools/assets/repobrowser3.png)

게시의 경우 기본적으로 저장소 브라우저에는 공개 컨텐츠만 표시되므로 다음과 같은 특정 폴더가 표시됩니다 `/conf` 또는 `/home` 표시되지 않습니다.

이러한 위치를 표시하려면 아래 절차를 따라야 합니다.

1. 선택한 환경 옆에 있는 세 점을 클릭하고 을 선택합니다 **액세스 관리**

   ![repobrowser7](/help/implementing/developing/tools/assets/repobrowser7.png)

1. 게시 인스턴스를 찾은 다음 클릭합니다

   ![repobrowser8](/help/implementing/developing/tools/assets/repobrowser8.png)

1. 게시 관리자를 위한 새 제품 프로필을 만듭니다. 아래 예에서는 라고 합니다. **DEV - AEM 관리자 게시**

   ![repobrowser9](/help/implementing/developing/tools/assets/repobrowser9.png)

1. 전체 액세스 권한이 있는 게시 저장소 브라우저를 탐색할 수 있는 적절한 사용자를 새 제품 프로필에 추가합니다

   ![reporter10](/help/implementing/developing/tools/assets/repobrowser10.png)

1. 잠시 기다렸다가 **AEM 작성자** 콘솔
1. 새 제품 프로필에 해당하는 그룹을 관리자 그룹의 구성원으로 추가합니다. 다음을 클릭하여 수행할 수 있습니다 **도구 - 보안 - 작성자의 그룹**&#x200B;을 클릭한 다음 **관리자** 그룹에 속해 있어야 합니다. 그런 다음 아래 표시된 대로 그룹을 추가합니다

   ![reportBrowser11](/help/implementing/developing/tools/assets/repobrowser11.png)

1. 를 활성화합니다 **관리자** 새로운 **DEV - AEM 관리자 게시** 게시할 수 있도록 그룹 구성

   ![reportBrowser12](/help/implementing/developing/tools/assets/repobrowser12.png)

1. 좋은 보안 방법으로서, 새 **DEV - AEM 관리자 게시** 그룹의 관리자 그룹에서 그룹 **작성자** 따라서 새 그룹은 게시하도록 격리됩니다

   ![reportBrowser13](/help/implementing/developing/tools/assets/repobrowser13.png)

1. 게시 인스턴스에 대해 저장소 브라우저에 액세스하면 다음을 포함한 모든 폴더가 표시됩니다 `/home` 및 `/conf`.

### JCR 속성 보기 {#view-jcr-properties}

노드를 클릭하면 탐색 브라우저의 오른쪽 창에 JCR 속성이 표시됩니다. 아래는 의 예입니다 `experience-fragments` 노드 아래에 있어야 합니다.

![repobrowser4](/help/implementing/developing/tools/assets/repobrowser41.png)

### 컨텐츠 보기 {#view-content}

탐색 창에서 리소스를 클릭하여 저장소 브라우저를 사용하여 컨텐츠를 볼 수 있습니다. 이렇게 하면 브라우저 오른쪽의 각 리소스 이름을 기준으로 하는 탭 아래에서 미리 보기가 열립니다.

![repobrowser6](/help/implementing/developing/tools/assets/repobrowser61.png)

아래 목록에 있는 이미지 유형에 대해 현재 미리 보기를 사용할 수 있습니다.

* api
* avif
* gif
* jpeg
* png
* svg+xml
* webp
* bmp
* x-icon
* tiff

그리고 다음 텍스트 기반 MIME 유형의 경우:

* `"text/*"`
* `'application/javascript'`
* `'application/json'`
* `'application/x-sh'`

### 콘텐츠 다운로드 {#download-content}

저장소 브라우저를 사용하여 컨텐츠를 다운로드할 수도 있습니다. 아래 예에서는 **다운로드** 다운로드 링크 `jcr:data` 선택한 노드에 연결되었습니다. 이 기능은 속성 정의가 포함된 노드로 이동하여 모든 이진 속성에 사용할 수 있습니다.

![repobrowser5](/help/implementing/developing/tools/assets/repobrowser52.png)
