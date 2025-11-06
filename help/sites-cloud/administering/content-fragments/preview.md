---
title: 컨텐츠 조각 미리 보기
description: 다양한 방법으로 콘텐츠 조각을 미리 보는 방법을 이해합니다.
feature: Content Fragments
role: User, Developer
solution: Experience Manager Sites
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '394'
ht-degree: 36%

---

# 컨텐츠 조각 미리 보기 {#previewing-content-fragments}

콘텐츠 조각은 Headless 게재 및 페이지 작성 둘 다에 사용할 수 있습니다. 조각은 형식화가 없는 콘텐츠만 제공하므로 검토하는 것이 더 어려울 수 있습니다. 따라서 다양한 시나리오에서 조각을 미리 보는 여러 가지 방법이 제공됩니다.

콘텐츠 조각에는 콘솔 조각 콘솔 및 편집기에서 액세스할 수 있는 몇 가지 방법이 있습니다. 이 섹션에 설명된 콘솔 및 편집기는 Headless 콘텐츠 전달을 위해 개발되었습니다(모든 시나리오에서 사용할 수 있지만).

조각을 미리 볼 수 있습니다.

* [미리 보기 URL 패턴](#preview-url-pattern) 사용

* [미리 보기 인스턴스](#preview-instance)에 게시하고 게시 취소하여

<!--
* with a HTML template, using **[Preview]()** from the Content Fragments console
-->

물론 [콘텐츠 조각 편집기](/help/sites-cloud/administering/content-fragments/authoring.md)에서 조각을 볼 수도 있습니다.

>[!IMPORTANT]
>
>콘텐츠 조각은 다음 두 콘솔에서 액세스할 수 있습니다. **콘텐츠 조각** 및 **자산**.
>
>콘텐츠 조각 작성을 위한 두 개의 편집기도 있습니다. 기본 기능은 동일하지만 몇 가지 차이점이 있습니다. 두 편집기 모두 두 콘솔에서 액세스할 수 있습니다.
>
>이 섹션에서는 **콘텐츠 조각** 콘솔과 *새* 콘텐츠 조각 편집기를 다룹니다. 이는 Headless 콘텐츠 게재를 맞게 개발되었습니다(단, 모든 시나리오에서 사용 가능).
>
>자세한 내용은 다음을 참조하십시오.
>
>* [콘텐츠 조각 관리](/help/assets/content-fragments/content-fragments-managing.md)용 **자산** 콘솔 사용
>* [*원래* 콘텐츠 조각 편집기](/help/assets/content-fragments/content-fragments-variations.md) 사용,
>* [페이지 작성에 콘텐츠 조각](/help/sites-cloud/authoring/fragments/content-fragments.md) 사용,

## 미리보기 URL 패턴 {#preview-url-pattern}

콘텐츠 조각 편집기는 작성자가 외부 프론트엔드 애플리케이션에서 편집된 내용을 미리보기할 수 있는 옵션입니다.

이 기능을 사용하려면 먼저 다음 작업을 수행해야 합니다.

* IT 팀과의 협력을 통해 JSON 출력을 사용하여 콘텐츠 조각을 렌더링할 외부 프론트엔드 애플리케이션을 설정합니다.

* 외부 프론트엔드 응용 프로그램을 설정할 때 **기본 미리 보기 URL 패턴**&#x200B;을(를) 해당 콘텐츠 조각 모델의 [속성](/help/sites-cloud/administering/content-fragments/managing-content-fragment-models.md#model-properties)(으)로 정의해야 합니다.

미리보기 URL은 다음 패턴을 따라야 합니다.

    `https://<preview_url>?param=${expression}`

사용 가능한 표현식은 다음과 같습니다.

* `${contentFragment.path}`
* `${contentFragment.model.path}`
* `${contentFragment.model.name}`
* `${contentFragment.variation}`
* `${contentFragment.id}`

URL을 정의하면 편집기의 상단 도구 모음에서 **[미리 보기](/help/sites-cloud/administering/content-fragments/authoring.md#preview-content-fragment)** 단추가 활성화됩니다. 이 버튼을 선택하여 콘텐츠 조각을 렌더링할 수 있는 외부 애플리케이션(별도의 탭에서)을 실행할 수 있습니다.

## 인스턴스 미리 보기 {#preview-instance}

**게시** 및 **게시 취소**, 조각을 **[미리보기 서비스](/help/headless/deployment/architecture.md)**(및 게시 인스턴스)에 게시할 수 있습니다.

편집기 또는 콘솔에서 조각을 게시할 수 있습니다.

다음을 참조하십시오.

* 전체 세부 정보를 보려면 [조각 게시 및 미리 보기](/help/sites-cloud/administering/content-fragments/managing.md#publishing-and-previewing-a-fragment)를 참조하십시오.

* 전체 세부 정보를 보려면 [조각 게시를 취소](/help/sites-cloud/administering/content-fragments/managing.md#unpublishing-a-fragment)하십시오.

<!--
## Preview based on a HTML Template {#preview-based-on-a-html-template}

The Content Fragment console provides a **Preview** option for every fragment.

The icon can be selected to open a dialog that represents the fragment based on a HTML template. You can use the default template, or develop and load your own.
-->
