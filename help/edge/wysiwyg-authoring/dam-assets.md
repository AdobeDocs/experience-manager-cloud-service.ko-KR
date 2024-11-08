---
title: Edge Delivery Services을 사용하여 DAM Assets으로 페이지 게시
description: 페이지의 DAM 에셋이 Edge Delivery Services에 원활하게 게시되도록 하는 데 필요한 설정을 알아봅니다.
feature: Edge Delivery Services
role: Admin, Architect, Developer
source-git-commit: 65a3b4d923a91702e7ea9b13356802836fa4ce0b
workflow-type: tm+mt
source-wordcount: '433'
ht-degree: 2%

---


# Edge Delivery Services을 사용하여 DAM Assets으로 페이지 게시 {#dam-assets}

페이지의 DAM 에셋이 Edge Delivery Services에 원활하게 게시되도록 하는 데 필요한 설정을 알아봅니다.

## 범용 편집기, DAM Assets 및 Edge Delivery {#overview}

유니버설 편집기의 콘텐츠를 편집할 때 DAM에서 에셋을 선택할 수도 있습니다. 콘텐츠를 Edge Delivery Services에 게시하면 관련 DAM 콘텐츠도 게시됩니다.

이 원활한 동작을 보장하려면 AEM 및 Edge Delivery Services이 게시하기 위해 DAM에 적절하게 액세스할 수 있어야 합니다. 여기에는 다음이 포함됩니다.

* [에셋 폴더에 액세스할 수 있는지 확인합니다.](#accessible)
* [에셋 폴더에 적절한 구성이 할당되었는지 확인합니다(필요한 경우).](#configuration)

## Assets 폴더에 액세스할 수 있는지 확인 {#accessible}

AEM에서 Edge Delivery Services으로 페이지를 게시할 때 [기술 계정](/help/implementing/developing/introduction/generating-access-tokens-for-server-side-apis.md)이 사용됩니다. 이름이 `<hash>@techacct.adobe.com` 형식인 이 계정은 유니버설 편집기로 만든 페이지를 처음 게시할 때마다 Cloud Manager에서 AEM의 사용자로 자동으로 만들어집니다.

![기술 계정](/help/edge/wysiwyg-authoring/assets/dam-assets/technical-account.png)

이 기술 계정의 콘텐츠를 게시하려면 모든 DAM 폴더에 대한 액세스 권한이 있어야 합니다. 다음과 같은 작업을 수행할 수 있습니다.

* 개인 DAM 폴더를 사용하지 마십시오.
* 기술 계정 사용자에게 DAM 폴더에 대한 액세스 권한을 부여합니다.

## Assets 폴더에 적절한 구성이 할당되었는지 확인 {#configuration}

일반적으로 기술 계정이 DAM의 에셋에 액세스할 수 있는지 확인하면 페이지와 함께 에셋을 Edge Delivery Services에 게시할 수 있습니다.

그러나 다음 두 가지 추가 사례에서 추가 구성이 필요합니다.

* PDF 또는 비디오와 같은 이미지가 아닌 에셋이 포함된 페이지를 Edge Delivery Services에 게시하려는 경우.
* 페이지에 관계없이 이미지 에셋을 Edge Delivery Services에 게시하려면 다음 작업을 수행하십시오.

이러한 사용 사례를 모두 지원하려면 [구성](/help/implementing/developing/introduction/configurations.md)을(를) DAM 폴더에 할당해야 합니다.

1. AEM 작성 환경에 로그인합니다.
1. **사이트**&#x200B;에서 자산을 게시하는 사이트 또는 자산을 연결할 사이트를 선택합니다.
1. 도구 모음에서 **속성**&#x200B;을 탭하거나 클릭합니다.
1. 속성 창의 **고급** 탭에서 **클라우드 구성** 필드의 구성을 기록해 두십시오.
   * 이 형식은 `/conf/<site-name>` 형식으로 사이트를 만들 때 자동으로 만들어집니다.
1. 속성 창에서 **취소**&#x200B;를 탭하거나 클릭하고 **Assets** -> **파일**(으)로 이동한 다음 DAM 폴더를 선택합니다.
1. 도구 모음에서 **속성**&#x200B;을 탭하거나 클릭합니다.
1. 속성 창의 **Cloud Service** 탭에서 **클라우드 구성** 필드에서 이전에 설명한 것과 동일한 구성을 선택합니다.
1. **저장 및 닫기**&#x200B;를 탭하거나 클릭합니다.
