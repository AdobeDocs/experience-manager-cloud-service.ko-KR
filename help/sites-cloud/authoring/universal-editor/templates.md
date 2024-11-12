---
title: 범용 편집기로 편집할 수 있는 페이지를 만드는 템플릿
description: 범용 편집기로 편집할 수 있는 페이지를 만드는 데 사용할 수 있는 템플릿을 만들어 시간을 절약하고 일관된 브랜딩을 보장하는 방법을 알아봅니다.
solution: Experience Manager Sites
feature: Authoring
role: User
exl-id: f0d60086-e92e-4492-ad50-bef84fed2a82
source-git-commit: 33eb71b2828314ee2c75206ef7034313e2638360
workflow-type: tm+mt
source-wordcount: '778'
ht-degree: 2%

---


# 범용 편집기로 편집할 수 있는 페이지를 만드는 템플릿 {#page-templates}

범용 편집기로 편집할 수 있는 페이지를 만드는 데 사용할 수 있는 템플릿을 만들어 시간을 절약하고 일관된 브랜딩을 보장하는 방법을 알아봅니다.

>[!NOTE]
>
>이 기능은 AEM as a Cloud Service의 향후 릴리스에서 사용할 수 있습니다.

>[!NOTE]
>
>[페이지 편집기로 편집할 수 있는 페이지를 만드는 데 템플릿을 사용할 수도 있습니다.](/help/sites-cloud/authoring/page-editor/templates.md)

## 페이지 템플릿이란 무엇입니까? {#what-are}

브랜딩 및 마케팅 지침은 종종 콘텐츠 페이지의 특정 레이아웃을 지시합니다. 또한 많은 페이지가 동일한 구조와 레이아웃을 공유하는 것이 현실적인 경우가 많습니다. 콘텐츠 작성자 시간을 절약하기 위해 템플릿에서 페이지를 만들 수 있습니다.

페이지 템플릿은 페이지 레이아웃의 마스터 복사본 역할을 합니다. 템플릿에서 페이지를 만들 때 템플릿의 초기 콘텐츠가 새 페이지에 복사되므로 콘텐츠 작성자를 위한 페이지의 기본 레이아웃 및 콘텐츠를 미리 정의하여 시간을 절약할 수 있습니다.

## 페이지 템플릿 활성화 {#enabling-templates}

템플릿을 사용하여 범용 편집기로 편집할 수 있는 페이지를 만들려면 이 옵션을 활성화해야 합니다.

먼저 사이트 구성에 대해 편집 가능한 템플릿을 활성화합니다.

1. **사이트** 콘솔을 사용하고 [사이트 루트를 선택하십시오.](/help/sites-cloud/authoring/sites-console/introduction.md#selecting-resources)
1. 사이트 루트를 선택한 후 도구 모음에서 [**속성** 아이콘](/help/sites-cloud/authoring/sites-console/page-properties.md)을 탭하거나 클릭합니다.
1. 속성 대화 상자의 **고급** 탭에서 **클라우드 구성** 필드의 값을 기록해 둡니다.
1. 기본 탐색에서 **도구** -> **일반** -> **구성 브라우저**&#x200B;를 선택합니다.
1. **[구성 브라우저에서](/help/implementing/developing/introduction/configurations.md)** 이전 단계에서 기록한 구성을 선택한 다음 도구 모음에서 **속성**&#x200B;을 탭하거나 클릭합니다.
1. **구성 속성** 창에서 **편집 가능한 템플릿** 옵션을 선택하십시오.
1. **저장 및 닫기**&#x200B;를 탭하거나 클릭합니다.

구성이 활성화되면 사이트에 템플릿을 허용해야 합니다.

1. **사이트** 콘솔을 사용하고 [사이트 루트를 선택하십시오.](/help/sites-cloud/authoring/sites-console/introduction.md#selecting-resources)
1. 사이트 루트를 선택한 후 도구 모음에서 [**속성** 아이콘](/help/sites-cloud/authoring/sites-console/page-properties.md)을 탭하거나 클릭합니다.
1. **템플릿 설정** 섹션 아래에 있는 속성 대화 상자의 **고급** 탭에서 **추가** 단추를 탭하거나 클릭합니다.
1. **허용된 템플릿** 아래에 나타나는 비어 있는 새 필드에서 `/conf/<site>/settings/wcm/templates/.*` 경로를 추가합니다.
1. **저장 및 닫기**&#x200B;를 탭하거나 클릭합니다.

이제 템플릿을 사용하여 사이트의 페이지를 만들 수 있습니다. 이 작업은 범용 편집기로 편집할 수 있는 페이지를 만들 때 템플릿을 사용하려는 모든 사이트/구성에 한 번만 수행해야 합니다.

## 새 템플릿 만들기 {#create-new}

[템플릿 역할을 할 새 페이지를 만들거나](/help/sites-cloud/authoring/sites-console/creating-pages.md) 기존 페이지를 템플릿의 기반으로 사용할 수 있습니다.

1. **사이트** 콘솔을 사용하여 템플릿으로 사용할 [새 페이지 또는 기존 페이지로 이동](/help/sites-cloud/authoring/sites-console/introduction.md#selecting-resources)한 다음 탭하거나 클릭하여 선택합니다.

1. 페이지를 선택한 후 도구 모음에서 [**속성** 아이콘](/help/sites-cloud/authoring/sites-console/page-properties.md)을 탭하거나 클릭합니다.

1. **템플릿 설정** 섹션 아래에 있는 속성 대화 상자의 **고급** 탭에서 **페이지를 템플릿으로 사용** 전환을 선택합니다.

1. **저장 및 닫기**&#x200B;를 탭하거나 클릭합니다.

이제 새 페이지를 만들 때 새 페이지를 템플릿으로 사용할 수 있습니다.

## 템플릿으로 페이지 만들기 {#creating-from-template}

유니버설 편집기로 편집할 수 있는 템플릿에서 페이지를 만드는 작업은 [다른 페이지를 만드는 것과 같은 워크플로입니다.](/help/sites-cloud/authoring/sites-console/creating-pages.md)

1. **사이트** 콘솔을 사용하여 새 페이지를 만들 [위치로 이동](/help/sites-cloud/authoring/sites-console/introduction.md#selecting-resources)합니다.

1. **만들기** -> **페이지**&#x200B;를 탭하거나 클릭합니다.

1. **페이지 만들기** 마법사의 **템플릿** 탭에서 새 페이지의 기준으로 사용할 템플릿을 선택할 수 있습니다. 원하는 템플릿을 탭하거나 클릭하여 선택한 다음 **다음**&#x200B;을 탭하거나 클릭합니다.

다른 페이지에서처럼 마법사를 완료하고 선택한 템플릿을 기반으로 새 페이지를 만듭니다.

## 페이지 및 템플릿 {#pages-vs-templates}

페이지 템플릿은 페이지의 초기 콘텐츠만 정의합니다. 그런 다음 유니버설 편집기를 사용하여 페이지를 완전히 편집할 수 있습니다.

* 페이지 템플릿에서 생성된 페이지는 템플릿의 독립적인 복사본입니다.
* 템플릿이 변경되면 해당 템플릿을 기반으로 하는 기존 페이지는 변경되지 않습니다.
* 콘텐츠 작성자는 템플릿의 제한 없이 필요에 따라 결과 페이지의 콘텐츠를 수정하고 업데이트할 수 있습니다.

## 편집 가능한 템플릿 {#editable-templates}

[페이지 편집기](/help/sites-cloud/authoring/page-editor/introduction.md)로 만든 페이지도 템플릿을 기반으로 할 수 있습니다. 범용 편집기와 페이지 편집기의 페이지를 만드는 데 사용되는 템플릿은 모두 AEM의 [편집 가능한 템플릿을 활용합니다.](/help/implementing/developing/components/templates.md)

페이지 편집기로 편집할 수 있는 페이지를 만드는 데 사용되는 템플릿은 편집 가능한 템플릿의 모든 기능을 사용합니다. 범용 편집기로 편집 가능한 페이지를 만드는 데 사용되는 템플릿은 초기 콘텐츠 기능만 사용합니다.
