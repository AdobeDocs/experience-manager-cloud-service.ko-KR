---
title: 번역을 위한 콘텐츠 준비
description: 컨텐츠를 번역 준비하는 방법을 알아봅니다.
feature: Language Copy
role: Admin
exl-id: afc577a2-2791-481a-ac77-468011e4302e
source-git-commit: 04054e04d24b5dde093ed3f14ca5987aa11f5b0e
workflow-type: tm+mt
source-wordcount: '768'
ht-degree: 1%

---

# 번역을 위한 콘텐츠 준비 {#preparing-content-for-translation}

다국어 웹 사이트는 일반적으로 여러 언어로 일부 콘텐츠를 제공합니다. 사이트는 한 언어로 작성된 다음 다른 언어로 번역됩니다. 일반적으로 다국어 사이트는 페이지 분기로 구성되며, 각 분기에는 사이트의 페이지를 다른 언어로 포함합니다.

>[!TIP]
>
>콘텐츠를 번역할 신규 분은 [사이트 번역 여정,](/help/journey-sites/translation/overview.md) AEM 또는 번역 경험이 없는 사용자에게 이상적인 AEM의 강력한 번역 도구를 사용하여 AEM Sites 컨텐츠를 번역하는 안내식 경로입니다.

다음 [WKND 자습서 사이트](/help/implementing/developing/introduction/develop-wknd-tutorial.md) 에는 여러 언어 분기가 포함되어 있으며 다음 구조를 사용합니다.

```text
/content
    |- wknd
        |- language-masters
            |- en
            |- de
            |- es
            |- fr
            |- it
        |- us
            |- en
            |- es
        |- ca
            |- en
            |- fr
        |- ch
            |- de
            |- fr
            |- it
        |- de
            |- de
        |- fr
            |- fr
        |- es
            |- es
        |- it
            |- it
```

원래 사이트 컨텐츠를 작성하는 데 사용되는 언어 사본은 언어 마스터입니다. 언어 마스터는 다른 언어로 번역되는 소스입니다.

사이트의 각 언어 분기를 언어 사본이라고 합니다. 언어 루트라고 하는 언어 사본의 루트 페이지는 언어 복사본에서 컨텐츠의 언어를 식별합니다. 예, `/content/wknd/fr` 는 프랑스어 복사본에 대한 언어 루트입니다. 언어 사본: [올바르게 구성된 언어 루트](preparation.md#creating-a-language-root) 소스 사이트의 번역을 수행할 때 올바른 언어를 타깃팅하도록 합니다.

다음 단계를 사용하여 사이트 번역을 준비하십시오.

1. 언어 마스터의 언어 루트를 만듭니다. 예를 들어 영어 WKND 데모 사이트의 언어 루트는 다음과 같습니다 `/content/wknd/language-masters/en`. 의 정보에 따라 언어 루트가 올바르게 구성되었는지 확인합니다. [언어 루트 만들기](preparation.md#creating-a-language-root).
1. 언어 마스터의 콘텐츠를 작성합니다.
1. 사이트에 대한 각 언어 사본의 언어 루트를 만듭니다. 예를 들어 WKND 샘플 사이트의 프랑스어 언어 사본은 다음과 같습니다 `/content/wknd/language-masters/fr`.

컨텐츠를 번역 준비를 완료한 후, 언어 사본 및 관련 번역 프로젝트에서 누락된 페이지를 자동으로 만들 수 있습니다. (자세한 내용은 [번역 프로젝트 만들기](managing-projects.md)) AEM의 컨텐츠 번역 프로세스에 대한 개요는 [다국어 웹 사이트의 컨텐츠 번역](overview.md).

## 언어 루트 만들기 {#creating-a-language-root}

언어 루트를 컨텐츠의 언어를 식별하는 언어 사본의 루트 페이지로 만듭니다. 언어 루트를 만든 후 언어 사본을 포함하는 번역 프로젝트를 만들 수 있습니다.

언어 루트를 만들려면 페이지를 만들고 ISO 언어 코드를 **이름** 속성을 사용합니다. 언어 코드는 다음 형식 중 하나여야 합니다.

* `<language-code>` - 지원되는 언어 코드는 ISO-639-1에 따라 정의된 두 문자 코드입니다. 예를 들면 다음과 같습니다 `en`.
* `<language-code>_<country-code>` 또는 `<language-code>-<country-code>` - 지원되는 국가 코드는 ISO 3166에 따라 소문자 또는 대문자 2자 코드입니다. 예를 들어 `en_US`, `en_us`, `en_GB`, `en-gb`.

글로벌 사이트에 대해 선택한 구조에 따라 두 형식 중 하나를 사용할 수 있습니다.  예를 들어 WKND 사이트의 프랑스어 언어 복사본에 대한 루트 페이지는 다음과 같습니다 `fr` 로서의 **이름** 속성을 사용합니다. 다음 사항에 유의하십시오. **이름** 속성은 저장소의 페이지 노드 이름으로 사용되므로 페이지의 경로(`http://<host>:<4502>/content/wknd/language-masters/fr.html`).

1. 사이트로 이동합니다.
1. 언어 사본을 만들 사이트를 클릭하거나 탭합니다.
1. 클릭 또는 탭 **만들기**&#x200B;를 클릭한 다음 을 클릭하거나 탭합니다 **페이지**.

   ![페이지 만들기](../assets/create-page.png)

1. 페이지 템플릿을 선택한 다음 을(를) 클릭하거나 탭합니다 **다음**.
1. 에서 **이름** 필드에 국가 코드를 `<language-code>` 또는 `<language-code>_<country-code>`, 예 `en`, `en_US`, `en_us`, `en_GB`, `en_gb`. 페이지의 제목을 입력합니다.

   ![언어 루트 페이지 만들기](../assets/create-language-root.png)

1. **만들기**&#x200B;를 클릭하거나 탭합니다. 확인 대화 상자에서 다음 중 하나를 클릭하거나 탭합니다 **완료** 사이트 콘솔로 돌아가거나 **열기** 언어 사본을 엽니다.

## 언어 루트 상태 보기 {#seeing-the-status-of-language-roots}

AEM에서 제공 **참조** 생성된 언어 루트 목록을 표시하는 레일입니다.

![언어 루트](../assets/language-roots.png)

다음 절차에 따라 페이지의 언어 사본을 [레일 선택기.](/help/sites-cloud/authoring/getting-started/basic-handling.md#rail-selector)

1. 사이트 콘솔에서 사이트의 페이지를 선택한 다음 을 클릭하거나 탭합니다 **참조**.

   ![참조 레일 열기](../assets/opening-references-rail.png)

1. 참조 레일에서 를 클릭하거나 탭합니다 **언어 복사**. 레일은 웹 사이트의 언어 사본을 보여줍니다.

## 여러 수준의 언어 사본 {#multiple-levels}

언어 루트는 노드 아래에 그룹화할 수도 있습니다. 예를 들어, 영역별로 그룹화할 수도 있지만 언어 사본의 루트로 인식됩니다.

```text
/content
    |- wknd
        |- language-masters
            |- europe
                |- de
                |- fr
                |- it
                |- es
                ]- pt
            |- americas
                |- en
                |- es
                |- fr
                |- pt
            |- asia
                |- ...
            |- africa
                |- ...
            |- oceania
                |- ...
        |- europe
        |- americas
        |- asia
        |- africa
        |- oceania            
```

>[!NOTE]
>
>한 수준만 허용됩니다. 예를 들어, 다음 항목에서는 `es` 언어 사본으로 확인할 페이지:
>
>* `/content/wknd/language-masters/en`
>* `/content/wknd/language-masters/americas/central-america/es`
>
> 이 `es` 언어 복사본은 2개 수준(`americas/central-america`) `en` 노드 아래에 있어야 합니다.

>[!TIP]
>
>이러한 설정에서 언어 루트는 언어의 ISO 코드가 아닌 모든 페이지 이름을 가질 수 있습니다. AEM은 항상 먼저 경로와 이름을 확인하지만 페이지 이름이 언어를 식별하지 않으면 AEM에서 `cq:language` 언어 식별에 대한 페이지의 속성입니다.
