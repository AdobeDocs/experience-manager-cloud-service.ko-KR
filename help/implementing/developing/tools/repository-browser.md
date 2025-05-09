---
title: 저장소 브라우저
seo-title: Repository Browser
description: 저장소 브라우저는 작성자, 게시 및 미리보기 계층의 모든 환경에 대해 저장소에 읽기 전용 보기를 제공합니다.
seo-description: The repository browser provides a read-only view into the repository for all environments on author, publish, and preview tiers.
exl-id: 22473a97-8f7b-4014-b885-1233116aeda6
feature: Developing
role: Admin, Architect, Developer
source-git-commit: 9d1b51b465a148551de93f8180b056b8e7752db5
workflow-type: tm+mt
source-wordcount: '871'
ht-degree: 1%

---

# 저장소 브라우저 {#repository-browser}

>[!NOTE]
>
>저장소 브라우저는 AEM 버전 6582 이상에서 사용할 수 있습니다.

>[!INFO]
>
>또한 [이 클립](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/repository-browser.html?lang=ko)을 통해 저장소 브라우저를 사용하여 AEM as a Cloud Service을 디버깅하는 방법에 대한 간단한 비디오 소개도 볼 수 있습니다.

## 소개 {#introduction}

저장소 브라우저는 작성자, 게시 및 미리보기 계층의 모든 환경에 대해 저장소에 대한 읽기 전용 보기를 제공하는 개발자 도구입니다. 콘텐츠를 더 쉽게 보거나 디버깅할 수 있도록 콘텐츠 구조를 쉽게 볼 수 있도록 설계되었습니다.

[AEM as a Cloud Service Developer Console](/help/implementing/developing/introduction/development-guidelines.md#crxde-lite-and-developer-console)에서 액세스할 수 있으며 선택한 환경에 대한 작성자 또는 게시 인스턴스의 저장소를 탐색하는 데 사용할 수 있습니다.

### 사전 요구 사항 액세스 {#access-prerequisites}

AEM as a Cloud Service Developer Console 또는 저장소 브라우저에 액세스하려면 다음 조건을 충족해야 합니다

AEM as a Cloud Service Developer Console에 액세스하려면 [Developer Console 액세스](https://experienceleague.adobe.com/ko/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/developer-console#developer-console-access)를 참조하십시오.

저장소 브라우저에 액세스하려면 요구 사항은 AEM as a Cloud Service Developer Console(위에 지정됨)와 동일합니다. 특정 인스턴스에 대한 저장소 브라우저 컨텐츠를 보려면 다음과 같이 하십시오.

* 작성자 인스턴스: **작성자 인스턴스**&#x200B;에 대한 AEM 사용자 제품 프로필을 가진 사용자는 최소한의 읽기 권한으로 저장소 브라우저를 볼 수 있습니다. 저장소를 검색할 때는 사용자의 권한이 유지됩니다. AEM 관리자 제품 프로필이 있는 사용자는 전체 읽기 액세스 권한이 있는 저장소 브라우저를 볼 수 있습니다.

* Publish 인스턴스: **Publish 인스턴스**&#x200B;에 대한 AEM 사용자 제품 프로필을 가진 사용자는 최소한의 읽기 권한으로 저장소 브라우저를 볼 수 있습니다. 해당 제품 프로필 세트가 없으면 사용자는 익명 사용자로 탐색하고 제한된 권한으로 인해 일부 경로가 표시되지 않습니다.

사용자 권한 설정에 대한 자세한 내용은 [Cloud Manager 설명서](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/content/requirements/users-and-roles.html?lang=ko)를 참조하세요.

### 저장소 브라우저 실행 {#launching-the-repository-browser}

저장소 브라우저는 아래 단계에 따라 실행할 수 있습니다.

1. Cloud Manager에서 선택한 환경 옆에 있는 세 점을 클릭하고 **Developer Console**&#x200B;을 선택합니다

   ![repobrowser1](/help/implementing/developing/tools/assets/repobrowser1.png)

1. **저장소 브라우저** 탭을 클릭합니다
1. **Pod** 드롭다운 목록을 클릭하여 작성자, 게시 또는 미리 보기에 해당하는 Pod를 선택합니다.

   ![repobrowser2](/help/implementing/developing/tools/assets/repobrowser2.png)

1. 아래의 **저장소 브라우저 열기** 링크를 클릭하여 저장소 브라우저를 시작합니다. 선택한 계층의 대표 인스턴스(pod)에 해당하는 브라우저가 시작됩니다. 해당 계층의 특정 Pod를 실행할 수 없습니다.

## 기능 {#features}

### 계층 탐색 {#navigate-the-hierarchy}

왼쪽 탐색 창을 사용하여 콘텐츠 계층 구조를 탐색할 수 있습니다. 각 폴더 또는 노드를 클릭하면 해당 하위 폴더가 표시됩니다. 폴더 구조는 JCR 노드 트리의 상위 집합인 Sling 리소스 트리를 반영합니다.

![repobrowser3](/help/implementing/developing/tools/assets/repobrowser3.png)

또는 아래와 같이 **경로** 필드에 경로를 입력하여 경로로 직접 이동할 수 있습니다. 또한 이 경로는 왼쪽의 콘텐츠 계층 보기에서 위치를 확장합니다.

![repobrowser14](/help/implementing/developing/tools/assets/repobrowser14.png)

왼쪽의 폴더를 클릭하면 경로 필드가 자동으로 해당 위치로 채워집니다. 이 기능은 나중에 사용하기 위해 값을 복사하여 붙여넣을 때 유용합니다.

또한 폴더를 클릭하면 해당 폴더의 경로를 포함하도록 URL이 동적으로 수정됩니다. 이 기능을 사용하면 책갈피 가능 URL을 사용할 수 있습니다.

게시의 경우 기본적으로 저장소 브라우저에 공개 컨텐츠만 표시되므로 `/conf` 또는 `/home`과(와) 같은 특정 폴더는 표시되지 않습니다.

이러한 위치를 표시하려면 다음을 수행합니다.

1. 선택한 환경 옆에 있는 세 점을 클릭하고 **액세스 관리**&#x200B;를 선택합니다.

   ![repobrowser7](/help/implementing/developing/tools/assets/repobrowser7.png)

1. 게시 인스턴스를 찾은 다음 클릭합니다

   ![repobrowser8](/help/implementing/developing/tools/assets/repobrowser8.png)

1. 게시 관리자용 제품 프로필을 만듭니다. 아래 예제에서는 **DEV - AEM 관리자 Publish**&#x200B;이라고 합니다.

   ![repobrowser9](/help/implementing/developing/tools/assets/repobrowser9.png)

1. 전체 액세스 권한을 가진 게시 저장소 브라우저를 탐색할 수 있는 사용자에 해당하는 적절한 사용자를 새 제품 프로필에 추가합니다

   ![repobrowser10](/help/implementing/developing/tools/assets/repobrowser10.png)

1. 몇 분 정도 기다린 후 **AEM 작성자** 콘솔을 엽니다
1. **도구 - 보안 - 작성자의 그룹**&#x200B;을 클릭한 다음 **관리자** 그룹을 클릭하여 새 제품 프로필에 해당하는 그룹을 관리자 그룹의 구성원으로 추가합니다. 그런 다음 아래에 표시된 대로 그룹을 추가합니다

   ![repobrowser11](/help/implementing/developing/tools/assets/repobrowser11.png)

1. **관리자** 및 새 **개발 - AEM 관리자 Publish** 그룹을 활성화하여 게시할 때 사용할 수 있도록 합니다.

   ![repobrowser12](/help/implementing/developing/tools/assets/repobrowser12.png)

1. **작성자**&#x200B;의 관리자 그룹에서 새 **DEV - AEM 관리자 Publish** 그룹을 제거하여 새 그룹을 게시하도록 격리합니다

   ![repobrowser13](/help/implementing/developing/tools/assets/repobrowser13.png)

1. 게시 인스턴스의 저장소 브라우저에 액세스하면 `/home` 및 `/conf`을(를) 포함한 모든 폴더가 표시됩니다.

### JCR 속성 보기 {#view-jcr-properties}

노드를 클릭하면 탐색 브라우저의 오른쪽 창에 해당 JCR 속성이 표시됩니다. 다음은 `experience-fragments` 노드의 예입니다.

![repobrowser4](/help/implementing/developing/tools/assets/repobrowser41.png)

### 컨텐츠 보기 {#view-content}

저장소 브라우저를 사용하여 콘텐츠를 볼 수 있습니다. 각 리소스의 이름을 딴 탭에서 브라우저의 오른쪽에 미리보기를 열 수 있도록 탐색 창에서 리소스를 클릭합니다.

![repobrowser6](/help/implementing/developing/tools/assets/repobrowser61.png)

다음 이미지 유형에 대해 미리 보기를 사용할 수 있습니다.

* apng
* avif
* gif
* jpeg
* png
* svg+xml
* webp
* bmp
* x-아이콘
* tiff

다음 텍스트 기반 MIME 유형의 경우:

* `"text/*"`
* `'application/javascript'`
* `'application/json'`
* `'application/x-sh'`

### 콘텐츠 다운로드 {#download-content}

저장소 브라우저를 사용하여 콘텐츠를 다운로드할 수도 있습니다. 아래 예에서는 **다운로드** 링크를 눌러 선택한 노드와 연결된 `jcr:data`을(를) 다운로드할 수 있습니다. 이 기능은 속성 정의가 포함된 노드로 이동하여 모든 이진 속성에 사용할 수 있습니다.

![repobrowser5](/help/implementing/developing/tools/assets/repobrowser52.png)
