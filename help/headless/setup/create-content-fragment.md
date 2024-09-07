---
title: 콘텐츠 조각 만들기 - Headless 설정
description: Headless 게재를 위해 AEM의 콘텐츠 조각을 사용하여 페이지 독립적 콘텐츠를 디자인하고 만들고 선별하고 사용하는 방법을 알아봅니다.
exl-id: a227ae2c-f710-4968-8a00-bfe48aa66145
feature: Headless, Content Fragments,GraphQL API
role: Admin, Developer
source-git-commit: bdf3e0896eee1b3aa6edfc481011f50407835014
workflow-type: ht
source-wordcount: '341'
ht-degree: 100%

---

# 콘텐츠 조각 만들기 - Headless 설정 {#creating-content-fragments}

Headless 게재를 위해 AEM의 콘텐츠 조각을 사용하여 페이지 독립적 콘텐츠를 디자인하고 만들고 선별하고 사용하는 방법을 알아봅니다.

## 콘텐츠 조각이란 무엇입니까? {#what-are-content-fragments}

콘텐츠 조각을 저장할 수 있는 [자산 폴더를 만들었으므로](create-assets-folder.md) 이제 콘텐츠 조각을 만들 수 있습니다!

콘텐츠 조각을 사용하여 페이지 독립적인 콘텐츠를 디자인하고 만들고 선별하고 게시할 수 있습니다. 이를 통해 여러 위치와 여러 채널에서 사용할 수 있는 콘텐츠를 준비할 수 있습니다.

콘텐츠 조각에는 구조화된 콘텐츠가 포함되어 있으며 JSON 형식으로 전달할 수 있습니다.

## 콘텐츠 조각을 만드는 방법 {#how-to-create-a-content-fragment}

콘텐츠 작성자는 자신이 만드는 콘텐츠를 표시하기 위해 콘텐츠 조각을 원하는 수만큼 만듭니다. 이는 AEM에서 작성자의 주요 작업입니다. 이 시작 안내서에서는 하나만 만들면 됩니다.

1. AEM as a Cloud Service에 로그인하고 메인 메뉴에서 **탐색** > **콘텐츠 조각**&#x200B;을 선택합니다.

1. 이전에 만든 [폴더를 선택합니다.](create-assets-folder.md)
1. **만들기**&#x200B;를 선택합니다.
1. 콘텐츠 조각 만들기는 대화 상자로 표시됩니다.
콘텐츠 조각을 만드는 데 사용할 위치 및 모델을 선택합니다.

   * 사용 가능한 모델은 콘텐츠 조각을 생성하고 있는 자산 폴더](create-assets-folder.md)에 대해 정의한 [**클라우드 구성**&#x200B;에 따라 다릅니다.
   * 모델을 사용할 수 없는 경우 자산 폴더의 구성을 확인하십시오.

   제목, 이름 및 필요한 경우 설명을 추가합니다.

   ![새 콘텐츠 조각 만들기 대화 상자](/help/sites-cloud/administering/content-fragments/assets/cfc-console-create.png)

1. **만들기** 또는 **만들고 열기**&#x200B;를 선택합니다.

콘텐츠 조각은 다른 콘텐츠 조각을 참조할 수 있으므로 필요한 경우 중첩된 콘텐츠 구조를 허용합니다.

콘텐츠 조각은 AEM의 다른 자산을 참조할 수도 있습니다. 참조 콘텐츠 조각을 만들기 전에 [이러한 자산을 AEM에 저장해야 합니다](/help/assets/manage-digital-assets.md).

## 다음 단계 {#next-steps}

콘텐츠 조각을 만들었으므로 이제 시작 안내서의 마지막 부분으로 이동하여 [콘텐츠 조각 액세스 및 전달을 위한 API 요청을 만들 수 있습니다.](create-api-request.md)

>[!TIP]
>
>콘텐츠 조각 관리에 대한 자세한 내용은 [콘텐츠 조각 설명서](/help/sites-cloud/administering/content-fragments/overview.md)를 참조하십시오.
