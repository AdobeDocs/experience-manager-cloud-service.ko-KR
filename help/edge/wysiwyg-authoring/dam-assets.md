---
title: Edge Delivery Services를 사용하여 DAM 자산이 포함된 페이지 게시
description: 페이지의 DAM 자산이 Edge Delivery Services에 원활하게 게시되도록 하는 데 필요한 설정을 알아봅니다.
feature: Edge Delivery Services
role: Admin, Architect, Developer
exl-id: 160f0474-a72d-4183-a2b2-2f8ba177605d
index: false
hide: true
hidefromtoc: true
source-git-commit: 17c14a78c2cfa262e25c6196fa73c6c4b17e200a
workflow-type: ht
source-wordcount: '433'
ht-degree: 100%

---

# Edge Delivery Services를 사용하여 DAM 자산이 포함된 페이지 게시 {#dam-assets}

페이지의 DAM 자산이 Edge Delivery Services에 원활하게 게시되도록 하는 데 필요한 설정을 알아봅니다.

## 범용 편집기, DAM 자산 및 Edge Delivery {#overview}

범용 편집기에서 콘텐츠를 편집할 때 DAM에서 자산을 선택할 수 있습니다. Edge Delivery Services에 콘텐츠를 게시하면 관련 DAM 콘텐츠도 함께 게시됩니다.

이 동작이 원활하게 이루어지려면 AEM과 Edge Delivery Services가 게시하기 위해 DAM에 적절하게 액세스할 수 있어야 합니다. 여기에는 다음이 포함됩니다.

* [자산 폴더에 액세스할 수 있도록 보장합니다](#accessible).
* [자산 폴더에 적절한 구성이 할당되도록 보장합니다(필요한 경우)](#configuration).

## 자산 폴더에 액세스할 수 있도록 보장 {#accessible}

AEM에서 Edge Delivery Services로 페이지를 게시할 때는 [기술 계정](/help/implementing/developing/introduction/generating-access-tokens-for-server-side-apis.md)이 사용됩니다. 이 계정은 `<hash>@techacct.adobe.com` 형식의 이름을 가지고 있으며 범용 편집기로 만든 페이지를 처음 게시할 때마다 Cloud Manager에서 AEM 사용자로 자동으로 생성됩니다.

![기술 계정](/help/edge/wysiwyg-authoring/assets/dam-assets/technical-account.png)

이 기술 계정은 콘텐츠를 게시하기 위해 모든 DAM 폴더에 대한 액세스 권한이 있어야 합니다. 다음과 같은 작업을 수행할 수 있습니다.

* 비공개 DAM 폴더를 사용하지 않습니다.
* 기술 계정 사용자에게 DAM 폴더에 대한 액세스 권한을 부여합니다.

## 자산 폴더에 적절한 구성이 할당되도록 보장 {#configuration}

일반적으로 기술 계정이 DAM에 있는 자산에 액세스할 수 있도록 하면 페이지와 함께 자산을 Edge Delivery Services에 게시하기에 충분합니다.

그러나 두 가지 추가적인 경우에는 또 다른 구성이 필요합니다.

* PDF, 비디오 등 이미지가 아닌 자산이 포함된 페이지를 Edge Delivery Services에 게시하려는 경우.
* 이미지 자산을 페이지와 별도로 Edge Delivery Services에 게시하려는 경우.

이러한 두 가지 사용 사례를 모두 지원하려면 [구성](/help/implementing/developing/introduction/configurations.md)을 DAM 폴더에 할당해야 합니다.

1. AEM 작성 환경에 로그인합니다.
1. **사이트**&#x200B;에서 자산을 게시할 사이트나 자산이 연결될 사이트를 선택합니다.
1. 도구 모음에서 **속성**&#x200B;을 탭하거나 클릭합니다.
1. 속성 창의 **고급** 탭에서 **클라우드 구성** 필드의 구성을 기록해 둡니다.
   * 이 구성은 `/conf/<site-name>` 형식으로 사이트를 만들 때 자동으로 생성됩니다.
1. 속성 창에서 **취소**&#x200B;를 탭하거나 클릭하고 **자산** -> **파일**&#x200B;로 이동하여 DAM 폴더를 선택합니다.
1. 도구 모음에서 **속성**&#x200B;을 탭하거나 클릭합니다.
1. 속성 창의 **클라우드 서비스** 탭에 있는 **클라우드 구성** 필드에서 이전에 기록한 것과 동일한 구성을 선택합니다.
1. **저장 및 닫기**&#x200B;를 탭하거나 클릭합니다.
