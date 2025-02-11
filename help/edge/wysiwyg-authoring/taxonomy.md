---
title: 분류 체계 데이터 관리
description: Edge Delivery Services 사이트에서 AEM과 함께 태그를 사용하기 위한 분류 체계 데이터 관리 방법을 알아봅니다.
feature: Edge Delivery Services
role: Admin, Architect, Developer
exl-id: 017982e4-a4c8-4097-8751-9619cc4639d0
source-git-commit: 10580c1b045c86d76ab2b871ca3c0b7de6683044
workflow-type: tm+mt
source-wordcount: '974'
ht-degree: 75%

---


# 분류 체계 데이터 관리 {#managing-taxonomy-data}

Edge Delivery Services 사이트에서 AEM과 함께 태그를 사용하기 위한 분류 체계 데이터 관리 방법을 알아봅니다.

## 소개 {#introduction}

태그 지정은 페이지를 구성하고 관리하는 데 도움이 되는 중요한 기능입니다. AEM의 [태그 지정 콘솔](/help/sites-cloud/administering/tags.md#tagging-console)을 사용하면 페이지를 구성할 수 있는 태그 분류 체계를 만들 수 있습니다.

이러한 태그는 사용자와 작성자가 콘텐츠를 구성하는 데 유용할 뿐만 아니라 독자에게도 유용할 수 있습니다. 태그와 태그 분류 체계는 페이지의 구성 요소에서 사용하여 독자가 콘텐츠를 탐색하는 데 도움이 될 수 있습니다.

범용 편집기는 태그의 ID로만 작동합니다. 콘텐츠에 대한 분류 체계 페이지를 만들면 모든 언어로 된 이러한 태그의 설명을 범용 편집기에 노출하여 콘텐츠 렌더링 시 해당 정보를 사용할 수 있도록 합니다.

## 분류 체계 페이지 만들기 {#creating}

[AEM의 다른 모든 페이지](/help/sites-cloud/authoring/sites-console/creating-pages.md)와 같이 분류법이 만들어집니다.

1. [**사이트** 콘솔](/help/sites-cloud/authoring/sites-console/introduction.md)(으)로 이동합니다.

1. 분류 체계를 만들려는 위치를 선택합니다.

1. **만들기** -> **페이지**&#x200B;를 탭하거나 클릭합니다.

   ![페이지 제작](assets/taxonomy/create-page.png)

1. **페이지 만들기** 마법사의 **템플릿** 탭에서 **분류 체계** 템플릿을 선택하고 **다음**&#x200B;을 탭하거나 클릭합니다.

   ![분류 체계 템플릿](assets/taxonomy/taxonomy-template.png)

1. **페이지 만들기** 마법사의 **속성** 탭에서 페이지에 의미 있는 **제목**&#x200B;을 입력하고 **태그** 필드에서 [태그 선택기를 사용](/help/sites-cloud/authoring/sites-console/tags.md)하여 분류 체계에 포함할 태그 또는 네임스페이스를 선택합니다.

   ![분류 체계 속성](assets/taxonomy/create-page-wizard-properties.png)

1. **만들기**&#x200B;를 탭하거나 클릭합니다.

분류 체계 페이지가 생성되었습니다. **성공** 대화 상자에서 **완료** 대화 상자를 탭하거나 클릭하여 메시지를 닫거나 **열기**&#x200B;를 클릭하여 [페이지 편집기](/help/sites-cloud/authoring/page-editor/introduction.md)에서 페이지를 편집할 수 있습니다.

다음 단계에서 사용할 분류 체계 페이지의 결과 페이지 이름을 기록해 둡니다.

## 분류 체계 페이지 편집 {#editing}

AEM의 다른 페이지와 같은 방식으로 분류 체계 페이지 편집을 시작합니다.

1. [**사이트** 콘솔](/help/sites-cloud/authoring/sites-console/introduction.md)(으)로 이동합니다.

1. 편집하려는 분류 체계를 선택합니다.

1. 작업 표시줄에서 **편집**&#x200B;을 탭하거나 클릭합니다.

1. 페이지 편집기가 열리고 분류 체계가 표시됩니다.

   * 분류 체계 페이지는 페이지 편집기에서 읽기 전용입니다.

   ![분류 체계 편집](assets/taxonomy/edit-page.png)

1. 도구 모음에서 **페이지 정보** 아이콘을 탭하거나 클릭하고 **속성 열기**&#x200B;를 선택합니다.

   ![속성 열기](assets/taxonomy/open-properties.png)

1. **페이지 속성** 창에서 페이지 이름을 업데이트하고 태그 선택기를 사용하여 분류 체계에 포함된 태그 및 네임스페이스를 업데이트할 수 있습니다.

   ![페이지 속성 편집](assets/taxonomy/edit-properties.png)

1. **저장 및 닫기**&#x200B;를 탭하거나 클릭합니다.

분류 체계의 내용이 선택한 태그 및 네임스페이스에서 자동으로 생성되므로 페이지 편집기에 표시되는 페이지는 읽기 전용입니다. 분류 체계의 내용을 자동으로 생성하는 일종의 필터 역할을 합니다. 따라서 편집기에서 페이지를 직접 편집할 이유가 없습니다.

기본 태그 및 네임스페이스를 업데이트하면 AEM이 분류 체계 페이지의 내용을 자동으로 업데이트합니다. 그러나 이러한 변경 사항을 사용자가 사용할 수 있도록 하려면 변경 후 [분류 체계를 다시 게시](#publishing)해야 합니다.

## 분류 체계 게시를 위한 paths.json 업데이트 {#paths-json}

[Edge Delivery Services 사이트에 대한 테이블 형식 데이터를 관리 및 게시](/help/edge/wysiwyg-authoring/tabular-data.md)할 때와 마찬가지로, 분류 데이터를 게시할 수 있도록 프로젝트의 `paths.json` 파일을 업데이트해야 합니다.

1. GitHub에서 프로젝트의 루트를 엽니다.

1. `paths.json` 파일을 탭하거나 클릭하여 세부 정보를 연 다음 **편집** 아이콘을 엽니다.

   ![paths.json 파일](assets/taxonomy/paths-json.png)

1. 새 분류 체계 페이지를 `.json` 리소스에 매핑하는 줄을 추가합니다.

   ```json
   {
     "mappings": [
      "/content/<site-name>/:/",
      "/content/<site-name>/<taxonomy-page-name>:/<taxonomy-json-name>.json"
     ]
   }
   ```

   * `<taxonomy-page-name>`은(는) 사용자가 만든 [분류 페이지의 이름과 일치해야 합니다](#creating).
   * `<taxonomy-json-name>`은 선택한 유효한 이름일 수 있습니다.

1. **변경 사항 커밋...**&#x200B;을 클릭하여 `main`에 변경 사항을 저장합니다.

   * 프로세스에 따라 `main`에 커밋하거나 가져오기 요청을 만듭니다.

이 프로세스는 분류 체계 페이지당 한 번만 수행하면 됩니다. 완료되면 분류 체계를 게시할 수 있습니다.

>[!TIP]
>
>경로 매핑에 대한 자세한 내용은 [Edge Delivery Services의 경로 매핑](/help/edge/wysiwyg-authoring/path-mapping.md) 문서를 참조하십시오.

## 분류 체계 게시 {#publishing}

분류 체계는 게시될 때까지 범용 편집기에서 또는 사용자가 사용할 수 없습니다.

분류 페이지는 [도구 모음의 **빠른 게시** 또는 **게시 관리** 아이콘을 사용하여](/help/sites-cloud/authoring/sites-console/publishing-pages.md)하여 다른 페이지와 같이 게시됩니다.

매번 분류 체계 페이지를 다시 게시해야 합니다.

* 분류 체계 페이지를 편집합니다.
* 분류 체계 페이지에 포함된 태그 및 네임스페이스를 편집하거나 추가합니다.

새 분류 페이지를 만드는 경우 먼저 [매핑을 프로젝트의 `paths.json` 파일에 추가](#paths-json)해야 합니다.

## 분류 체계 정보 접근 {#accessing}

분류 체계가 게시되면 범용 편집기에서 해당 정보를 활용하여 사용자에게 표시할 수 있습니다.

분류 체계는 다음 주소에서 JSON 데이터로 액세스할 수 있습니다.

`https://<branch>--<repository>--<owner>.aem.page/<taxonomy-json-name>.json`

[프로젝트의 `paths.json` 파일에 분류를 매핑](#paths-json)할 때 정의한 `<taxonomy-json-name>`을(를) 사용합니다. 분류 데이터는 다음 예제와 같이 JSON 데이터로 반환됩니다.

```json
{
  "total": 3,
  "offset": 0,
  "limit": 3,
  "data": [
    {
      "tag": "default:",
      "title": "Standard Tags"
    },
    {
      "tag": "do-not-translate",
      "title": "Do Not Translate"
    },
    {
      "tag": "translate",
      "title": "Translate"
    }
  ],
  "columns": [
    "tag",
    "title"
  ],
  ":type": "sheet"
}
```

이 JSON 데이터는 분류 체계를 업데이트하고 다시 게시할 때 자동으로 업데이트됩니다. 앱은 사용자를 위해 이 정보에 프로그래밍 방식으로 액세스할 수 있습니다.

[여러 언어로 태그를 유지 관리하는 경우](/help/sites-cloud/administering/tags.md#managing-tags-in-different-languages) `sheet=` 매개 변수의 값으로 ISO2 언어 코드를 전달하여 해당 언어에 액세스할 수 있습니다.

## 추가 태그 속성 노출 {#additional-properties}

기본적으로 분류법에는 이전 [의 ](#accessing)과(와) 같이 `tag` 및 `title` 값이 포함됩니다. 추가 태그 속성을 노출하도록 분류를 구성할 수 있습니다. 이 예제에서는 태그 설명을 노출하겠습니다.

1. Sites 콘솔을 사용하여 만든 분류 체계를 선택합니다.
1. 도구 모음에서 **속성** 아이콘을 탭하거나 클릭합니다.
1. **추가 속성** 섹션에서 **추가**&#x200B;를 탭하거나 클릭하여 필드를 추가합니다.
1. 새 필드에 노출할 JRC 속성 이름을 입력합니다. 이 경우에는 태그 설명을 위해 `jcr:description`을 입력합니다.
1. **저장 및 닫기**&#x200B;를 탭하거나 클릭합니다.
1. 분류 체계를 선택한 상태로 도구 모음에서 **빠른 게시**&#x200B;를 탭하거나 클릭합니다.

이제 [분류법에 액세스하면](#accessing)태그 설명(또는 노출하도록 선택한 모든 속성)이 JSON에 포함됩니다.

```json
{
  "total": 3,
  "offset": 0,
  "limit": 3,
  "data": [
    {
      "tag": "default:",
      "title": "Standard Tags",
      "jcr:description": "These are the standard tags"
    },
    {
      "tag": "do-not-translate",
      "title": "Do Not Translate",
      "jcr:description": "Tag to mark pages that should not be translated"
    },
    {
      "tag": "translate",
      "title": "Translate",
      "jcr:description": "Tag to mark pages that should be translated"
    }
  ],
  "columns": [
    "tag",
    "title",
    "jcr:description"
  ],
  ":type": "sheet"
}
```
