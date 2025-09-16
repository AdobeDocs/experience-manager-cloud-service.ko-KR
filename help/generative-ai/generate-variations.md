---
title: 변형 생성
description: AEM as a Cloud Service와 Edge Delivery Services의 Sidekick에서 액세스할 수 있는 변형 생성에 대해 알아봅니다.
exl-id: 9114037f-37b9-4b2f-a714-10933f69b2c3
feature: Generate Variations, AI Tools
role: Admin, Architect, Developer
source-git-commit: b99cc846a1efbbcd12244f68c770aa25ac4e985d
workflow-type: tm+mt
source-wordcount: '3295'
ht-degree: 100%

---


# 변형 생성 {#generate-variations}


>[!NOTE]
>
>본 페이지에 설명된 버전은 향후 사용되지 않을 예정이므로 AEM 편집기에 통합된 [변형 생성](/help/generative-ai/generate-variations-integrated-editor.md) 버전 이용을 권장하여 드립니다.

디지털 채널을 최적화하고 콘텐츠 제작을 가속화하는 방법을 찾고 있다면 변형 생성을 사용할 수 있습니다. 변형 생성은 생성형 AI를 사용하여 프롬프트를 기반으로 콘텐츠 변형을 생성하며, 이러한 프롬프트는 Adobe에서 제공하거나 사용자가 만들고 관리합니다. 변형을 만든 후 웹 사이트에서 콘텐츠를 사용할 수 있으며, [Edge Delivery Services](/help/edge/overview.md)의 [실험](https://www.aem.live/docs/experimentation) 기능을 사용하여 성공 여부를 측정할 수도 있습니다.

다음에서 [변형 생성](#access-generate-variations)에 액세스할 수 있습니다.

* [Adobe Experience Manager(AEM) as a Cloud Service 내](#access-aemaacs)
* [AEM Edge Delivery Services의 Sidekick](#access-aem-sidekick)
* [콘텐츠 조각 편집기 내](/help/sites-cloud/administering/content-fragments/authoring.md#generate-variations-ai)

>[!NOTE]
>
>모든 경우에 변형 생성을 사용하려면 [액세스 사전 요구 사항](#access-prerequisites)이 충족되었는지 확인해야 합니다.

그런 다음 아래와 같은 작업을 수행할 수 있습니다.

* Adobe가 특정 사용 사례를 위해 만든 프롬프트 템플릿을 사용하여 [시작](#get-started)합니다.
* [기존의 프롬프트를 편집](#edit-the-prompt)할 수 있습니다.
* 또는 [나만의 프롬프트를 만들어 사용](#create-prompt)할 수 있습니다.
   * 나중에 사용할 수 있도록 [프롬프트를 저장](#save-prompt)할 수 있습니다.
   * 조직 전반의 [공유 프롬프트에 이를 액세스하고 사용](#select-prompt)할 수 있습니다.
* [대상자별의 맞춤형 콘텐츠를 생성](#generate-copy)할 때 프롬프트에 사용할 [대상자](#audiences) 세그먼트 정의를 할 수 있습니다.
* 프롬프트와 함께 출력을 미리 보고 수정하고 필요한 경우 결과를 수정할 수 있습니다.
* [Adobe Express를 사용하여 사본 변형을 기반으로 이미지를 생성](#generate-image)할 수 있으며, 이는 Firefly의 생성형 AI 기능을 사용합니다.
* 웹 사이트 또는 실험에서 사용할 콘텐츠를 선택할 수 있습니다.

## 법률 및 사용 참고 사항 {#legal-usage-note}

AEM을 위한 생성형 AI 및 변형 생성은 강력한 도구이지만 결과물의 사용은 **사용자**&#x200B;가 책임집니다.

서비스에 대한 입력은 컨텍스트에 연결되어야 합니다. 이러한 컨텍스트는 브랜딩 자료, 웹 사이트 콘텐츠, 데이터, 데이터에 대한 스키마, 템플릿 또는 기타 신뢰할 수 있는 문서가 될 수 있습니다.

사용 사례에 따라 모든 출력의 정확성을 평가해야 합니다.

변형 생성을 사용하기 전에 [Adobe 생성형 AI 사용자 가이드라인](https://www.adobe.com/kr/legal/licenses-terms/adobe-dx-gen-ai-user-guidelines.html)에 동의해야 합니다.

[변형 생성의 사용](#generative-action-usage)은 생성형 액션의 소비와 관련이 있습니다.

## 개요 {#overview}

변형 생성을 열고 왼쪽 패널을 확장하면 다음이 표시됩니다.

![변형 생성 - 기본 패널](assets/generate-variations-main-panel.png)

* 오른쪽 패널
   * 이는 왼쪽 탐색에서 선택한 항목에 따라 달라집니다.
   * 기본적으로 **프롬프트 템플릿**&#x200B;이 표시됩니다.
* 왼쪽 탐색
   * **변형 생성** 왼쪽에는 왼쪽 탐색 패널을 확장하거나 숨길 수 있는 옵션(샌드위치 메뉴)이 있습니다.
   * **프롬프트 템플릿**:
      * 다양한 프롬프트에 대한 링크를 표시하며, 여기에는 프롬프트가 포함될 수 있습니다.
         * Adobe에서 제공하여 콘텐츠 생성에 도움을 주며 Adobe 아이콘으로 표시됩니다.
         * 직접 생성합니다.
         * IMS 조직 내에서 생성되며 여러 개의 머리를 나타내는 아이콘으로 플래그가 지정됩니다.
      * 사용자만의 프롬프트를 만들 수 있는 [새 프롬프트](#create-prompt) 링크가 포함되어 있습니다.
      * 본인이나 IMS 조직 내에서 만든 프롬프트를 **삭제**&#x200B;할 수 있습니다. 이 작업은 해당 카드의 줄임표를 클릭하여 액세스한 메뉴로 수행됩니다.
   * [즐겨찾기](#favorites): 즐겨찾기로 표시한 이전 세대의 결과를 표시합니다.
   * [최근 항목](#recents): 최근에 사용한 프롬프트와 해당 입력에 대한 링크를 제공합니다.
   * **도움말 및 FAQ**: FAQ를 포함한 문서에 대한 링크입니다.
   * **사용자 가이드라인**: 법적 가이드라인에 대한 링크입니다.

## 시작하기 {#get-started}

인터페이스는 콘텐츠 생성 과정을 안내합니다. 인터페이스를 연 후 첫 번째 단계는 사용하려는 프롬프트를 선택하는 것입니다.

### 프롬프트 선택 {#select-prompt}

기본 패널에서 다음을 선택할 수 있습니다.

* 콘텐츠 생성을 시작하도록 Adobe에서 제공하는 프롬프트 템플릿,
* 나만의 프롬프트를 만들 수 있는 [새 프롬프트](#create-prompt),
* 사용자만 사용하도록 만든 템플릿,
* 사용자 또는 사용자 조직의 누군가가 만든 템플릿.

구별 방법:

* Adobe에서 제공하는 프롬프트에는 Adobe 아이콘이 표시됩니다.
* IMS 조직 전체에서 사용할 수 있는 프롬프트에는 여러 개의 머리 모양 아이콘이 표시됩니다.
* 개인 프롬프트는 특별히 플래그가 지정되지 않습니다.

![변형 생성 - 프롬프트 템플릿](assets/generate-variations-prompt-templates.png)

### 입력 제공 {#provide-inputs}

각 프롬프트는 생성형 AI에서 적절한 콘텐츠를 다시 받을 수 있도록 특정 정보를 제공해야 합니다.

입력 필드는 필요한 정보를 안내합니다. 도움을 주기 위해 특정 필드에는 필요에 따라 사용하거나 수정할 수 있는 기본값과 요구 사항 설명이 있습니다.

여러 프롬프트에 공통적으로 표시되는 몇 가지 주요 입력 필드가 있습니다(특정 필드를 항상 사용할 수 있는 것은 아닙니다).

* **카운트**/**수**
   * 한 세대에 몇 개의 콘텐츠 변형을 만들 것인지 선택할 수 있습니다.
   * 프롬프트에 따라 카운트, 변형 수, 아이디어 수 등 다양한 레이블 중 하나가 있을 수 있습니다.
* **대상자 소스**/**타깃 대상자**
   * 특정 대상자에 대한 맞춤형 콘텐츠를 생성하는 데 도움이 됩니다.
   * Adobe는 기본 대상자를 제공합니다. 또는 추가 대상자를 지정할 수도 있습니다. [대상자](#audiences)를 참조하십시오.
* **추가 컨텍스트**
   * 관련 콘텐츠를 삽입하여 생성형 AI가 입력을 기반으로 더 나은 응답을 만드는 데 도움이 됩니다. 예를 들어 특정 페이지나 제품에 대한 웹 배너를 만드는 경우 해당 페이지/제품에 대한 정보를 포함할 수 있습니다.
* **온도**
Adobe 생성형 AI의 온도를 수정하는 데 사용:
   * 온도가 높을수록 프롬프트에서 벗어나 더 많은 변형, 무작위성과 창의성을 얻을 수 있습니다.
   * 온도가 낮을수록 결정적이며 프롬프트에 있는 온도에 더 가깝게 유지됩니다.
   * 기본적으로 온도는 1로 설정됩니다. 생성된 결과가 마음에 들지 않는 경우 다양한 온도로 실험해 볼 수 있습니다.
* **프롬프트 편집**
   * 기본 [프롬프트를 편집](#edit-the-prompt)하여 생성된 결과를 개선할 수 있습니다.

### 사본 생성 {#generate-copy}

입력 필드를 작성하거나 프롬프트를 수정하면 콘텐츠를 생성하고 응답을 검토할 준비가 됩니다.

생성형 AI가 생성한 응답을 보려면 **생성**&#x200B;을 선택합니다. 생성된 콘텐츠 변형은 생성된 프롬프트 아래에 표시됩니다.

![변형 생성 - 사본 생성](assets/generate-variations-generate-content.png)

>[!NOTE]
>
>대부분의 Adobe 프롬프트 템플릿에는 변형 응답에 **AI 이론적 근거**&#x200B;가 포함되어 있습니다. 이를 통해 생성형 AI가 특정 변형을 생성한 이유에 대한 투명성을 확보할 수 있습니다.

단일 변형을 선택하면 다음과 같은 작업을 사용할 수 있습니다.

* **즐겨찾기**
   * 향후 사용할 수 있도록 **즐겨찾기**&#x200B;로 표시합니다([즐겨찾기](#favorites)에 표시됨).
* 좋아요/싫어요
   * 좋아요/싫어요 표시를 사용하여 Adobe에 응답의 품질을 알려 줍니다.
* **복사**
   * 웹 사이트 또는 [실험](https://www.aem.live/docs/experimentation)에서 콘텐츠를 작성할 때 클립보드에 복사하여 사용합니다.
* **제거**

입력을 수정하거나 프롬프트를 표시해야 하는 경우 조정하고 다시 **생성**&#x200B;을 선택하여 새 응답 세트를 얻을 수 있습니다. 새 프롬프트와 응답은 처음 프롬프트와 응답 아래에 표시되며, 위아래로 스크롤하여 다양한 콘텐츠 세트를 볼 수 있습니다.

각 변형 세트 위에는 **재사용** 옵션과 함께 변형을 생성한 프롬프트가 표시되어 있습니다. 입력과 함께 프롬프트를 다시 실행해야 하는 경우 **재사용**&#x200B;을 선택하여 **입력**&#x200B;에서 다시 로드합니다.

### 이미지 생성 {#generate-image}

텍스트 변형을 생성한 후에는 Firefly의 생성형 AI 기능을 사용하여 Adobe Express에서 이미지를 생성할 수 있습니다.

>[!NOTE]
>
>**이미지 생성**&#x200B;은 IMS 조직의 일부로 Adobe Express 권한이 있고 Admin Console에서 사용자에게 권한이 부여된 경우에만 사용할 수 있습니다.

변형을 선택한 다음 **이미지 생성**&#x200B;을 선택하여 [Adobe Express](https://www.adobe.com/kr/express/)에서 **텍스트를 이미지로** 직접 엽니다. 프롬프트는 선택한 변형에 따라 사전 입력되며, 해당 프롬프트에 따라 이미지가 자동으로 생성됩니다.

![변형 생성 - 이미지 표현](assets/generate-variations-express-images.png)

다음을 추가로 변경할 수 있습니다.

* 보고 싶은 내용을 설명하여 [Adobe Express에 직접 프롬프트 작성](https://helpx.adobe.com/kr/firefly/using/tips-and-tricks.html),
* **텍스트를 이미지로** 옵션 조정,
* 생성된 이미지 **새로 고침**.

추가 가능성을 위해 **더 많은 항목 살펴보기**&#x200B;를 사용할 수도 있습니다.

완료되면 원하는 이미지를 선택하고 **저장**&#x200B;하여 Adobe Express를 닫습니다. 이미지가 반환되고 변형 버전이 저장됩니다.

![변형 생성 - 저장된 이미지 표현](assets/generate-variations-express-image-saved.png)

여기에서 이미지 위에 마우스를 가져가면 다음 작업 항목이 표시됩니다.

* **복사**: [다른 곳에서 사용하기 위해 이미지를 클립보드에 복사합니다.](#use-content)
* **편집**: Adobe Express를 열어 이미지를 변경할 수 있습니다.
* **다운로드**: 이미지를 로컬 컴퓨터에 다운로드합니다.
* **삭제**: 변형에서 이미지를 제거합니다.

>[!NOTE]
>
>[Content Credentials](https://helpx.adobe.com/kr/creative-cloud/help/content-credentials.html)는 문서 기반 작성에 사용하는 경우 지속되지 않습니다.

### 콘텐츠 사용 {#use-content}

생성형 AI로 생성된 콘텐츠를 사용하려면 다른 곳에서 사용할 수 있도록 콘텐츠를 클립보드에 복사해야 합니다.

이 작업은 복사 아이콘을 사용하여 수행됩니다.

* 텍스트의 경우: 변형 패널에 표시된 복사 아이콘을 사용합니다.
* 이미지의 경우: 이미지 위에 마우스를 가져가면 복사 아이콘이 표시됩니다.

클립보드에 복사한 후 웹 사이트의 콘텐츠를 작성할 때 사용할 정보를 붙여넣을 수 있습니다. [실험](https://www.aem.live/docs/experimentation)을 실행할 수도 있습니다.

## 즐겨찾기 {#favorites}

콘텐츠를 검토한 후 선택한 변형을 즐겨찾기에 저장할 수 있습니다.

저장하면 왼쪽 탐색 창의 **즐겨찾기**&#x200B;에 표시됩니다. 즐겨찾기는 계속 유지됩니다(**삭제** 또는 브라우저 캐시를 지울 때까지).

* 즐겨찾기와 변형을 클립보드에 복사/붙여넣기하여 웹 사이트 콘텐츠에 사용할 수 있습니다.
* 즐겨찾기는 **제거**&#x200B;할 수 있습니다.

## 최근 항목 {#recents}

이 섹션에서는 최근 활동에 대한 링크를 제공합니다. **최근** 항목은 **생성**&#x200B;을 선택하면 추가됩니다. 프롬프트 이름과 타임스탬프가 있습니다. 링크를 선택하면 프롬프트가 로드되고 입력 필드가 적절히 채워지며 생성된 변형이 표시됩니다.

## 프롬프트 편집 {#edit-the-prompt}

기본 프롬프트를 편집할 수 있습니다. 다음을 고려해 볼 수 있습니다.

* 생성된 결과에 추가적인 세분화가 필요한 경우
* 나중에 사용할 수 있도록 프롬프트를 수정하고 [저장](#save-prompt)하려는 경우

**프롬프트 편집**&#x200B;을 선택합니다.

![변형 생성 - 프롬프트 편집](assets/generate-variations-prompt-edit.png)

이렇게 하면 프롬프트 편집기가 열리고 여기서 변경 사항을 적용할 수 있습니다.

![변형 생성 - 프롬프트 편집기](assets/generate-variations-prompt-editor.png)

### 프롬프트 입력 추가 {#add-prompt-inputs}

프롬프트를 만들거나 편집할 때 입력 필드를 추가할 수 있습니다. 입력 필드는 프롬프트의 변수 역할을 하며 다양한 시나리오에서 동일한 프롬프트를 사용할 수 있도록 유연성을 부여합니다. 이 기능을 사용하면 전체 프롬프트를 작성할 필요 없이 프롬프트의 특정 요소를 정의할 수 있습니다.

* 필드는 플레이스홀더 이름을 둘러싼 이중 중괄호 `{{ }}`로 정의됩니다.
예: `{{tone_of_voice}}`

  >[!NOTE]
  >
  >이중 중괄호 사이에 공백을 허용하지 않습니다.

* 또한 `METADATA`에서 정의되며 다음 매개변수가 있습니다.
   * `label`
   * `description`
   * `default`
   * `type`

#### 예: 새로운 텍스트 필드 추가 - 어조 {#example-add-new-text-field-tone-of-voice}

**어조**&#x200B;라는 제목의 새 텍스트 필드를 추가하려면 프롬프트에서 다음 구문을 사용합니다.

```prompt
{{@tone_of_voice, 
  label="Tone of voice",
  description="Indicate the desired tone of voice",
  default="optimistic, smart, engaging, human, and creative",
  type=text
}}
```

![변형 생성 - 어조를 사용해 편집된 프롬프트](assets/generate-variations-prompt-edited.png)

<!--
#### Example: Add new dropdown field - Page Type {#example-add-new-dropdown-field-page-type}

To create an input field Page Type providing a dropdown selection:

1. Create a spreadsheet named `pagetype.xls` in the top-level directory of your folder structure.
1. Edit the spreadsheet:

   1. Create two columns: **Key** and **Value**.
   1. In the **Key** column, enter labels that will appear in the dropdown.
   1. In the **Value** column, describe the key value so the generative AI has context.

1. In your prompt, refer to the title of the spreadsheet along with the appropriate type. 

   ```prompt
   {{@page_type, 
     label="Page Type",
     description="Describes the type of page",
     spreadsheet=pagetype
   }}
   ```
-->

## 프롬프트 만들기 {#create-prompt}

**프롬프트 템플릿**&#x200B;에서 **새 프롬프트**&#x200B;를 선택하면 새 패널에서 새 프롬프트를 입력할 수 있습니다. 그런 다음 **온도**&#x200B;와 함께 이 내용을 지정하여 콘텐츠를 **생성**&#x200B;할 수 있습니다.

프롬프트 저장에 대한 자세한 내용은 [프롬프트 저장](#save-prompt)을 참조하십시오.

나만의 프롬프트 입력을 추가하는 방법에 대한 자세한 내용은 [프롬프트 입력 추가](#add-prompt-inputs)를 참조하십시오.

UI와 문서 기반 작성 흐름에 복사하여 붙여넣을 때 서식을 모두 유지하려면 프롬프트에 다음 사항을 포함합니다.

<!-- CHECK - are the double-quotes needed? -->

* `"Format the response as an array of valid, iterable RFC8259 compliant JSON"`

다음 이미지는 이를 통해 얻을 수 있는 이점을 보여 줍니다.

* 첫 번째 예시에는 `Title`과 `Description`이 결합되어 있습니다.
* 반면에 두 번째 예시에는 별도로 형식이 지정되어 있으며, 이는 프롬프트에 JSON 요청을 포함하는 것으로 수행되었습니다.

![변형 생성 - 제목과 설명이 별도로 형식이 지정된 프롬프트](assets/generate-variations-prompt-formatted.png)

## 프롬프트 저장 {#save-prompt}

프롬프트를 편집하거나 만든 후에는 나중에 사용할 수 있도록 저장하거나 IMS 조직 또는 본인 혼자 사용할 수 있도록 저장할 수 있습니다. 저장된 프롬프트는 **프롬프트 템플릿** 카드로 나타납니다.

프롬프트를 편집하면 입력 섹션 하단의 **생성** 왼쪽에 **저장** 옵션을 사용할 수 있습니다.

선택하면 **프롬프트 저장** 대화 상자가 열립니다.

![변형 생성 - 프롬프트 저장 대화 상자](assets/generate-variations-prompt-save-dialog.png)

1. 고유한 **프롬프트 이름**&#x200B;을 추가합니다. **프롬프트 템플릿** 내에서 프롬프트를 식별하는 데 사용됩니다.
   1. 고유한 새 이름을 사용하면 새 프롬프트 템플릿이 생성됩니다.
   1. 기존 이름이 해당 프롬프트를 덮어쓰고 메시지가 표시됩니다.
1. 원할 경우, 설명을 추가합니다.
1. 프롬프트를 사용자만 사용할 수 있도록 할지, IMS 조직 전체에서 사용할 수 있도록 할지 여부에 따라 **조직 전체에서 공유** 옵션을 활성화하거나 비활성화합니다. 이 상태는 [프롬프트 템플릿에 표시된 결과](#select-prompt) 카드에 나타납니다.
1. 프롬프트를 **저장**&#x200B;하거나, 작업을 **취소**&#x200B;합니다.

>[!NOTE]
>
>기존 프롬프트를 덮어쓰거나 업데이트하는 경우 알림(경고)이 표시됩니다.

>[!NOTE]
>
>**프롬프트 템플릿**&#x200B;에서 직접 또는 IMS 조직 내에서 만든 프롬프트(줄임표로 액세스할 수 있는 메뉴 사용)를 삭제할 수 있습니다.

## 대상자 {#audiences}

개인화된 콘텐츠를 생성하려면 생성형 AI가 대상자를 이해해야 합니다. Adobe는 다양한 기본 대상자를 제공하거나 직접 대상자를 추가할 수 있습니다.

대상자를 추가할 때는 자연어로 대상자를 설명해야 합니다. 예:

* 대상자를 만들려면:
   * `Student`
* 다음과 같이 말할 수 있습니다.
   * `The audience consists of students, typically individuals who are pursuing education at various academic levels, such as primary, secondary, or tertiary education. They are engaged in learning and acquiring knowledge in diverse subjects, seeking academic growth, and preparing for future careers or personal development.`

두 가지 대상자 소스가 지원됩니다.

* [Adobe Target](#audience-adobe-target)
* [CSV 파일](#audience-csv-file)

![변형 생성 - 대상자 소스](assets/generate-variations-audiences.png)

### 대상자 - Adobe Target {#audience-adobe-target}

프롬프트에서 **Adobe Target** 대상자를 선택하면 해당 대상자에 맞게 콘텐츠를 개인화할 수 있습니다.

>[!NOTE]
>
>이 옵션을 사용하려면 IMS 조직에서 Adobe Target에 액세스할 수 있어야 합니다.

1. **Adobe Target**&#x200B;을 선택합니다.
1. 그런 다음 제공된 목록에서 필요한 **타깃 대상자**&#x200B;를 선택합니다.

   >[!NOTE]
   >
   >**Adobe Target** 대상자를 사용하려면 설명 필드를 입력해야 합니다. 그렇게 하지 않으면 해당 대상자는 드롭다운 목록에서 사용할 수 없는 것으로 표시됩니다. 설명을 추가하려면 Target으로 이동하여 [대상자 설명을 추가합니다](https://experienceleague.adobe.com/ko/docs/target-learn/tutorials/audiences/create-audiences).

   ![변형 생성 - 대상자 소스 - Adobe Target](assets/generate-variations-audiences-adobe-target.png)

#### Adobe Target 대상자 추가 {#add-adobe-target-audience}

Adobe Target에서 대상자를 생성하려면 [대상자 만들기](https://experienceleague.adobe.com/ko/docs/target-learn/tutorials/audiences/create-audiences)를 참조하십시오.

### 대상자 - CSV 파일 {#audience-csv-file}

프롬프트에서 **CSV 파일** 대상자를 선택하면 선택한 **타깃 대상자**&#x200B;에 맞게 콘텐츠를 개인화할 수 있습니다.

Adobe는 다양한 대상자를 사용할 수 있도록 제공합니다.

1. **CSV 파일**&#x200B;을 선택합니다.
1. 그런 다음 제공된 목록에서 필요한 **타깃 대상자**&#x200B;를 선택합니다.

   ![변형 생성 - 대상자 소스 - CSV 파일](assets/generate-variations-audiences-csv-file.png)

#### 대상자 CSV 파일 추가 {#add-audience-csv-file}

파일을 공개적으로 사용할 수 있게 설정하면 파일에 URL을 제공하는 기능이 있는 다양한 플랫폼(예: Google Drive, DropBox, SharePoint)의 CSV 파일을 추가할 수 있습니다.

>[!NOTE]
>
>공유 플랫폼에는 파일에 공개적으로 액세스할 수 있는 기능이 *반드시* 있어야 합니다.

예를 들어 Google Drive의 파일에서 대상자를 추가하려면 다음 작업을 수행하십시오.

1. Google Drive에서 두 개의 열이 있는 스프레드시트 파일을 만듭니다.
   1. 첫 번째 열은 드롭다운에 표시됩니다.
   1. 두 번째 열은 대상자 대한 설명입니다.
1. 파일을 게시합니다.
   1. 파일 -> 공유 -> 웹에 게시 -> CSV
1. 게시된 파일에 URL을 복사합니다.
1. 변형 생성으로 이동합니다.
1. 프롬프트 편집기를 엽니다.
1. 메타데이터에서 **Adobe Target** 대상자를 찾아 URL을 바꿉니다.

   >[!NOTE]
   >
   >URL 양쪽 끝에 큰따옴표(“)가 있는지 확인합니다.

   예:

   ![변형 생성 - 대상자 CSV 파일 추가](assets/generate-variations-audiences-csv-save.png)

## 생성형 액션 사용량 {#generative-action-usage}

사용량 관리는 수행된 액션에 따라 달라집니다.

* 변형 생성

  하나의 카피 변형 생성은 하나의 생성형 액션과 동일합니다. 고객은 AEM 라이선스와 함께 제공되는 일정 수의 생성형 액션을 보유하고 있습니다. 기본 할당량을 모두 사용하면 추가 액션을 구매할 수 있습니다.

  >[!NOTE]
  >
  >기본 할당량에 대한 자세한 내용은 [Adobe Experience Manager: Cloud Service | 제품 설명](https://helpx.adobe.com/kr/legal/product-descriptions/aem-cloud-service.html)에서 확인할 수 있으며, 더 많은 생성형 액션을 구매하려면 계정 팀에 문의하십시오.

* Adobe Express

  이미지 생성 사용량은 Adobe Express 할당량 및 [생성 크레딧](https://helpx.adobe.com/kr/firefly/using/generative-credits-faq.html)을 통해 처리됩니다.

## 변형 생성 액세스 {#access-generate-variations}

사전 요구 사항을 충족하면 AEM as a Cloud Service 또는 Edge Delivery Services의 Sidekick에서 변형 생성에 액세스할 수 있습니다.

### 액세스 사전 요구 사항 {#access-prerequisites}

변형 생성을 사용하려면 다음 사전 요구 사항이 충족되었는지 확인해야 합니다.

* [Edge Delivery Services가 포함된 Experience Manager as a Cloud Service 액세스](#access-to-aemaacs-with-edge-delivery-services)

#### Edge Delivery Services가 포함된 Experience Manager as a Cloud Service 액세스{#access-to-aemaacs-with-edge-delivery-services}

변형 생성에 액세스해야 하는 사용자는 Edge Delivery Services가 포함된 Experience Manager as a Cloud Service 환경에 권한이 있어야 합니다.

>[!NOTE]
>
>AEM Sites as a Cloud Service에 대한 계약에 Edge Delivery Services가 포함되어 있지 않은 경우, 액세스 권한을 얻으려면 새 계약에 서명해야 합니다.
>
>Edge Delivery Services가 포함된 AEM Sites as a Cloud Service로 전환하는 방법에 대해 논의하려면 계정 팀에 문의하십시오.

특정 사용자에게 액세스 권한을 부여하려면 해당 사용자 계정을 제품 프로필에 할당합니다. [자세한 내용은 AEM 제품 프로필 할당](/help/journey-onboarding/assign-profiles-cloud-manager.md)을 참조하십시오.

### AEM as a Cloud Service에서 액세스 {#access-aemaacs}

AEM as a Cloud Service의 [탐색 패널](/help/sites-cloud/authoring/basic-handling.md#navigation-panel)에서 변형 생성에 액세스할 수 있습니다.

![탐색 패널](/help/sites-cloud/authoring/assets/basic-handling-navigation.png)

### AEM Sidekick에서 액세스 {#access-aem-sidekick}

Edge Delivery Services의 Sidekick에서 변형 생성에 액세스하려면 몇 가지 구성이 필요합니다.

1. Sidekick을 설치하고 구성하는 방법은 [AEM Sidekick 설치](https://www.aem.live/docs/sidekick-extension) 문서를 참조하십시오.

1. (Edge Delivery Services의) Sidekick에서 변형 생성을 사용하려면 Edge Delivery Services 프로젝트에 다음 구성을 포함시킵니다.

   * `tools/sidekick/config.json`

   이를 기존 구성에 병합한 다음 배포해야 합니다.

   예:

   ```prompt
   {
     // ...
     "plugins": [
       // ...
       {
         "id": "generate-variations",
         "title": "Generate Variations",
         "url": "https://experience.adobe.com/aem/generate-variations",
         "passConfig": true,
         "environments": ["preview","live", "edit"],
         "includePaths": ["**.docx**"]
       }
       // ...
     ]
   }
   ```

1. 그런 다음 사용자가 [Edge Delivery Services가 포함된 Experience Manager as a Cloud Service에 액세스](#access-to-aemaacs-with-edge-delivery-services)할 수 있는지 확인해야 할 수도 있습니다.

1. 그런 다음 Sidekick 도구 모음에서 **변형 생성**&#x200B;을 선택하여 이 기능에 액세스할 수 있습니다.

   ![변형 생성 - AEM Sidekick에서 액세스](assets/generate-variations-sidekick-toolbar.png)

## 추가 정보 {#further-information}

자세한 내용은 다음에서 확인할 수 있습니다.

* [GitHub에서 생성형 AI 변형 생성](https://github.com/adobe/aem-genai-assistant#setting-up-aem-genai-assistant)
* [Edge Delivery Services 실험](https://www.aem.live/docs/experimentation)
* [AEM as a Cloud Service의 생성형 AI](/help/ai-in-aem/overview.md#generative-ai-in-aem)

## FAQ {#faqs}

### 형식이 지정된 출력 {#formatted-outpu}

**생성된 응답이 필요한 형식이 지정된 출력을 제공하지 않습니다. 형식을 수정하려면 어떻게 해야 합니까? 예: 제목과 부제가 필요한데, 응답은 제목만 있습니다.**

1. 편집 모드에서 실제 프롬프트를 엽니다.
1. 요구 사항으로 이동합니다.
1. 출력에 대해 설명하는 요구 사항을 찾을 수 있습니다.
   1. 예: “텍스트가 제목, 본문, 버튼 라벨의 세 부분으로 구성되어야 합니다.” 또는 “Title”, “Body” 및 “ButtonLabel” 속성을 가진 오브젝트의 유효한 JSON 배열로 응답의 형식을 지정합니다.
1. 필요에 맞게 요구 사항을 수정합니다.

   >[!NOTE]
   >
   >입력한 새 출력에 단어/문자 수 제한이 있는 경우, 요구 사항을 만듭니다.

   예: “제목 텍스트는 공백을 포함하여 10단어 또는 50자를 초과할 수 없습니다.”
1. 나중에 사용할 수 있도록 프롬프트를 저장합니다.

### 응답 길이 {#length-of-response}

**생성된 응답이 너무 길거나 너무 짧습니다. 길이를 어떻게 바꿉니까?**

1. 편집 모드에서 실제 프롬프트를 엽니다.
1. 요구 사항으로 이동합니다.
1. 각 출력에는 해당 단어/문자 제한이 있습니다.
   1. 예: “제목 텍스트는 공백을 포함하여 10단어 또는 50자를 초과할 수 없습니다.”
1. 필요에 맞게 요구 사항을 수정합니다.
1. 나중에 사용할 수 있도록 프롬프트를 저장합니다.

### 응답 개선 {#improve-responses}

**제가 받는 응답이 찾고자 하는 내용과 다릅니다. 이를 개선하려면 어떻게 해야 합니까?**

1. 고급 설정에서 온도를 변경해 보십시오.
   1. 온도가 높을수록 프롬프트에서 벗어나 더 많은 변형, 무작위성과 창의성을 얻을 수 있습니다.
   1. 온도가 낮을수록 결정론적이며 프롬프트에 있는 내용을 준수합니다.
1. 편집 모드에서 실제 프롬프트를 열고 프롬프트를 검토합니다. 어조 및 기타 중요한 기준을 설명하는 요구 사항 섹션에 특히 주의를 기울이십시오.

### 프롬프트의 주석 {#comments-in-prompt}

**프롬프트에서 주석을 사용하려면 어떻게 해야 합니까?**

프롬프트의 주석은 실제 출력에 표시되지 않는 메모, 설명 또는 지침을 포함합니다. 이러한 주석은 특정 구문 내에서 캡슐화됩니다. 이중 중괄호로 시작하고 끝을 맺으며 해시로 시작합니다(예: `{{# Comment Here }}`). 주석은 생성된 응답에 영향을 미치지 않으면서 프롬프트 구조나 의도를 명확히 하는 데 도움이 됩니다.

### 공유된 프롬프트 찾기 {#find-a-shared-prompt}

**다른 사람이 공유한 프롬프트 템플릿을 찾을 수 없는 경우 어떻게 해야 합니까?**

이런 상황에서는 확인해야 할 다양한 세부 정보가 있습니다.

1. 사용자 환경에 맞는 URL을 사용합니다.
예: https://experience.adobe.com/#/aem/generate-variations
1. 선택한 IMS 조직이 올바른지 확인합니다.
1. 프롬프트가 공유됨으로 저장되었는지 확인합니다.

### v2.0.0의 사용자 정의 프롬프트 {#custom-prompts-v200}

**v.2.0.0에서 사용자 정의 프롬프트가 사라졌습니다. 어떻게 해야 합니까?**

v2.0.0 릴리스로 이동하면 사용자 정의 프롬프트 템플릿이 손상되어 사용할 수 없게 됩니다.

이를 복구하려면 다음 작업을 수행하십시오.

1. Sharepoint의 prompt-template 폴더로 이동합니다.
1. 프롬프트를 복사합니다.
1. 변형 생성 애플리케이션을 엽니다.
1. 새 프롬프트 카드를 선택합니다.
1. 프롬프트를 붙여넣습니다.
1. 프롬프트가 작동하는지 확인합니다.
1. 프롬프트를 저장합니다.

## 릴리스 기록 {#release-history}

현재 및 이전 릴리스에 대한 자세한 내용은 [변형 생성에 대한 릴리스 정보](/help/generative-ai/release-notes-generate-variations.md)를 참조하십시오.
