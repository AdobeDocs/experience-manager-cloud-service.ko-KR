---
title: 자산 폴더 만들기 - Headless 설정
description: AEM 콘텐츠 조각 모델을 사용하여 Headless 콘텐츠의 기반이 되는 콘텐츠 조각의 구조를 정의합니다.
exl-id: 9a156a17-8403-40fc-9bd0-dd82fb7b2235
feature: Headless, Content Fragments,GraphQL API
role: Admin, Developer
source-git-commit: 38a4bf89e099432163163e90e08aa0f47407724f
workflow-type: tm+mt
source-wordcount: '268'
ht-degree: 86%

---

# 자산 폴더 만들기 - Headless 설정 {#creating-an-assets-folder}

AEM 콘텐츠 조각 모델을 사용하여 Headless 콘텐츠의 기반이 되는 콘텐츠 조각의 구조를 정의합니다. 그런 다음 콘텐츠 조각은 자산 폴더에 저장됩니다.

## 자산 폴더란 무엇입니까? {#what-is-an-assets-folder}

미래의 콘텐츠 조각을 위해 원하는 구조를 정의하는 [콘텐츠 조각 모델을 만들었으므로](create-content-model.md) 이제 일부 조각을 만들고 싶을 것입니다.

그러나 먼저 자산을 저장할 자산 폴더를 만들어야 합니다.

자산 폴더는 콘텐츠 조각 외에도 이미지 및 비디오와 같은 [기존 콘텐츠 자산](/help/assets/manage-digital-assets.md)을 구성하는 데 사용됩니다.

## Assets 폴더 만들기 및 구성 {#create-and-configure-an-assets-folder}

관리자는 콘텐츠가 만들어질 때 콘텐츠를 구성하기 위해 가끔씩만 폴더를 만들면 됩니다. Assets 콘솔을 사용하여 새 폴더를 만듭니다.

만든 후에는 폴더에 [구성](/help/headless/setup/create-configuration.md)을 적용해야 합니다. 자세한 내용은 [폴더에 구성 적용](/help/sites-cloud/administering/content-fragments/setup.md#apply-the-configuration-to-your-folder)을 참조하세요.

만든 폴더 내에 추가 하위 폴더를 만들 수 있습니다. 하위 폴더는 상위 폴더의 **클라우드 구성**&#x200B;을 상속합니다. 그러나 다른 구성의 모델을 사용하려는 경우 재정의할 수 있습니다.

현지화된 사이트 구조를 사용하는 경우 새 폴더 아래에 [언어 루트를 만들 수 있습니다](/help/assets/translate-assets.md).

## 다음 단계 {#next-steps}

콘텐츠 조각에 대한 폴더를 만들었으므로 이제 시작 안내서의 네 번째 부분으로 이동하여 [콘텐츠 조각을 만들 수 있습니다](create-content-fragment.md).

>[!TIP]
>
>콘텐츠 조각 관리에 대한 자세한 내용은 [콘텐츠 조각 설명서](/help/sites-cloud/administering/content-fragments/overview.md)를 참조하십시오.
