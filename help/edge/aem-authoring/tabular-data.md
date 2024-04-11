---
title: 스프레드시트를 사용하여 표 형식 데이터 관리
description: 스프레드시트를 사용하여 Edge Delivery Services 사이트를 통해 AEM에 대한 메타데이터 및 리디렉션과 같은 다양한 값에 대한 표 형식 데이터를 관리하는 방법을 알아봅니다.
feature: Edge Delivery Services
exl-id: 26d4db90-3e4b-4957-bf21-343c76322cdc
source-git-commit: 61d65c37d263edef641db42589fc0f28a8eb9078
workflow-type: tm+mt
source-wordcount: '958'
ht-degree: 100%

---


# 스프레드시트를 사용하여 표 형식 데이터 관리 {#tabular-data}

스프레드시트를 사용하여 Edge Delivery Services 사이트를 통해 AEM에 대한 메타데이터 및 리디렉션과 같은 다양한 값에 대한 표 형식 데이터를 관리하는 방법을 알아봅니다.

## 사용 사례 {#use-cases}

Edge Delivery Services 사이트가 포함된 AEM의 경우 키-값 매핑과 같은 표 형식 데이터 목록을 유지 관리해야 합니다. 이는 메타데이터 및 리디렉션과 같은 다양한 값의 목록일 수 있습니다. Edge Deliver Services를 사용하면 직관적인 도구인 스프레드시트를 사용하여 이러한 표 형식 목록을 유지 관리할 수 있습니다. AEM은 이러한 스프레드시트를 웹 사이트 또는 웹 애플리케이션에서 쉽게 사용할 수 있는 JSON 파일로 변환합니다.

일반적인 사용 사례는 다음과 같습니다.

* [플레이스홀더](/help/edge/docs/placeholders.md)
* [메타데이터](/help/edge/docs/bulk-metadata.md)
* [헤더](/help/edge/docs/custom-headers.md)
* [리디렉션](/help/edge/docs/redirects.md)
* CND 설정과 같은 [구성](/help/edge/docs/setup-byo-cdn-push-invalidation.md)

또한 모든 구조의 [스프레드시트를 만들어](#own-spreadsheet) 원하는 목적에 맞게 매핑을 저장할 수 있습니다.

이 문서에서는 리디렉션의 예를 사용하여 이러한 스프레드시트를 만드는 방법을 보여 줍니다. 각 사용 사례에 대한 자세한 내용은 Edge Delivery Services 설명서에서 이전에 링크된 주제를 참조하십시오.

>[!TIP]
>
>일반적으로 스프레드시트가 Edge Delivery Services와 작동하는 방식에 대한 자세한 내용은 [스프레드시트 및 JSON](/help/edge/developer/spreadsheets.md) 문서를 참조하십시오.

>[!TIP]
>
>스프레드시트는 표 형식의 데이터를 유지하는 데만 사용해야 합니다. 구조화된 데이터를 저장하려면 [AEM의 Headless 기능을 확인](/help/headless/introduction.md)하십시오.

## 사전 요구 사항 {#prerequisites}

Edge Delivery Services 프로젝트가 포함된 AEM에서 스프레드시트를 사용하여 매핑을 만들려면 최신 사이트 템플릿을 사용하여 사이트를 만들어야 합니다.

자세한 내용은 [Edge Delivery Services를 사용한 AEM 작성을 위한 개발자 시작 안내서](/help/edge/aem-authoring/edge-dev-getting-started.md) 문서를 참조하십시오.

## 스프레드시트 만들기 {#spreadsheet}

이 예에서는 Edge Delivery Services 사이트를 사용하여 AEM에 대한 리디렉션을 관리하는 스프레드시트를 만듭니다. 만들려는 [다른 스프레드시트 유형](#other)에도 동일한 단계가 적용됩니다.

1. AEM as a Cloud Service 작성 인스턴스에 로그인하고 **Sites** 콘솔로 이동한 후 스프레드시트가 필요한 사이트의 루트로 이동합니다. **만들기** -> **페이지**&#x200B;를 탭하거나 클릭합니다.

   ![페이지 제작](assets/tabular-data/tabular-data-create-page.png)

1. 페이지 만들기 마법사의 **템플릿** 탭에서 **리디렉션** 템플릿을 탭하거나 클릭하여 선택한 다음 **다음**&#x200B;을 탭하거나 클릭합니다.

   ![템플릿 선택](assets/tabular-data/tabular-data-create-page-teamplate-redirects.png)

1. 마법사의 **속성** 탭에는 리디렉션 스프레드시트의 기본값이 표시됩니다. **만들기**&#x200B;를 탭하거나 클릭합니다.

   * **제목** - 이 값은 그대로 둡니다.
   * **열** - 리디렉션에 필요한 최소 열이 미리 채워져 있습니다.
      * **소스** - 리디렉션할 페이지
      * **대상** - 리디렉션할 대상 페이지

   ![스프레드시트의 속성](assets/tabular-data/tabular-data-create-page-properties-redirects.png)

1. **성공** 대화 상자에서 **열기**&#x200B;를 탭하거나 클릭합니다.

   ![완료 대화 상자](assets/tabular-data/tabular-data-success.png)

1. 사전 정의된 **소스** 및 **대상** 열이 있는 스프레드시트가 편집기에 로드된 새 탭이 열립니다. 리디렉션을 정의하려면 **소스** 열의 빈 행을 탭하거나 클릭합니다. 스프레드시트를 편집하면 변경 사항이 자동으로 저장됩니다.

   ![스프레드시트 편집](assets/tabular-data/tabular-data-edit-redirects.png)

   * **소스**&#x200B;는 웹 사이트 도메인에 상대적이므로 상대 경로만 포함됩니다.
   * **대상**&#x200B;은 다른 웹 사이트로 리디렉션하는 경우 정규화된 URL일 수 있고, 자체 웹 사이트 내에서 리디렉션하는 경우 상대 경로일 수 있습니다.
   * 다음 셀로 포커스를 이동하려면 Tab 키를 사용합니다.
   * 편집기는 필요에 따라 스프레드시트에 새 행을 추가합니다.
   * 행을 삭제하거나 이동하려면 각 행 끝에 있는 **삭제** 아이콘과 각 행 시작에 있는 드래그 핸들을 각각 사용합니다.

## 스프레드시트 paths.json 게시 {#paths-json}

AEM에서 스프레드시트의 데이터를 게시할 수 있으려면 프로젝트의 `paths.json` 파일을 추가로 업데이트해야 합니다.

1. GitHub에서 프로젝트의 루트를 엽니다.

1. `paths.json` 파일을 탭하거나 클릭하여 세부 정보를 연 다음 **편집** 아이콘을 엽니다.

   ![paths.json 파일](assets/tabular-data/tabular-data-paths-json.png)

1. 새 스프레드시트를 `redirects.json` 리소스에 매핑하는 줄을 추가합니다.

   ```json
   {
     "mappings": [
      "/content/<site-name>/:/",
      "/content/<site-name>/redirects:/redirects.json"
     ]
   }
   ```

1. **변경 사항 커밋...**&#x200B;을 클릭하여 `main`에 변경 사항을 저장합니다.

   * 프로세스에 따라 `main`에 커밋하거나 가져오기 요청을 만듭니다.

1. 리디렉션 정의를 마치고 경로 매핑을 업로드했으면 **Sites** 콘솔로 돌아갑니다.

1. 콘솔에서 만든 리디렉션 스프레드시트를 탭하거나 클릭하여 선택한 다음 작업 표시줄에서 **빠른 게시**&#x200B;를 탭하거나 클릭하여 스프레드시트를 게시합니다.

   ![Sites 콘솔에서 스프레드시트 선택](assets/tabular-data/tabular-data-select-publish.png)

1. **빠른 게시** 대화 상자에서 **게시**&#x200B;를 탭하거나 클릭합니다.

   ![게시 확인](assets/tabular-data/tabular-data-quick-publish.png)

1. 배너가 게시를 확인합니다.

   ![게시에 대한 배너 확인](assets/tabular-data/tabular-data-publish-banner.png)

이제 리디렉션 스프레드시트가 게시되어 공개적으로 액세스할 수 있는 상태입니다.

## 기타 스프레드시트 유형 {#other}

이제 리디렉션 스프레드시트를 만드는 방법을 알았으므로 다음과 같은 다른 표준 스프레드시트 유형을 만들 수 있습니다.

* 플레이스홀더
* 메타데이터
* 헤더
* 구성

[스프레드시트 만들기](#spreadsheet) 및 [paths.json 업데이트](#paths-json) 섹션의 단계를 동일하게 따르고, 적절한 템플릿을 선택하고, `paths.json` 파일을 적절하게 업데이트하면 됩니다.

[구성](https://www.aem.live/docs/configuration), [헤더](https://www.aem.live/docs/custom-headers) 및 [메타데이터](https://www.aem.live/docs/bulk-metadata)의 경우 기본 위치에 게시되도록 하는 매핑을 추가해야 합니다.

* 구성: `/.helix/config.json`
* 헤더: `/.helix/headers.json`
* 메타데이터: `/metadata.json`

또한 자체 용도를 위한 임의의 열을 사용해 [자체 스프레드시트를 만들](#own-spreadsheet) 수 있습니다.

>[!NOTE]
>
>Edge Delivery Services 프로젝트를 사용하여 AEM as a Cloud Service에 대한 인덱싱을 관리하기 위해 스프레드시트를 만들 필요는 없습니다.
>
>자체 인덱스를 만들고 싶다면 [이 설명서에 따라](https://www.aem.live/developer/indexing#setting-up-more-index-configurations) 자체 `helix-query.yaml` 파일을 만들 수 있습니다.

## 자체 스프레드시트 만들기 {#own-spreadsheet}

1. [스프레드시트 만들기](#spreadsheet) 섹션의 단계를 동일하게 따릅니다.

1. 템플릿을 선택할 때 **스프레드시트**&#x200B;를 선택합니다.

1. 마법사의 **속성** 탭에서 자체 열을 추가할 수 있습니다.

   ![자체 열 추가](assets/tabular-data/tabular-data-own-spreadsheet.png)

   * **열** 섹션에서 **추가**&#x200B;를 탭하거나 클릭하여 새 열을 추가합니다.
   * 열의 이름을 입력합니다.
   * **삭제** 및 드래그 핸들 아이콘을 각각 사용하여 열을 제거하거나 재구성합니다.

1. 리디렉션 스프레드시트에 대한 지침에 따라 스프레드시트를 만들고 게시합니다.

1. 리디렉션 스프레드시트의 지침에 따라 `paths.json` 파일에 매핑을 추가합니다.
