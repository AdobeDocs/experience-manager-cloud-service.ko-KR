---
title: 스프레드시트를 사용하여 테이블 형식 데이터 관리
description: 스프레드시트를 사용하여 Edge Delivery Services 사이트를 통해 AEM에 대한 메타데이터 및 리디렉션 등 다양한 값에 대한 표 형식 데이터를 관리하는 방법에 대해 알아봅니다.
feature: Edge Delivery Services
source-git-commit: 0fa88453a7d7c58a3ccb2a4baf7d2b143acf7ad5
workflow-type: tm+mt
source-wordcount: '943'
ht-degree: 2%

---


# 스프레드시트를 사용하여 테이블 형식 데이터 관리 {#tabular-data}

스프레드시트를 사용하여 Edge Delivery Services 사이트를 통해 AEM에 대한 메타데이터 및 리디렉션 등 다양한 값에 대한 표 형식 데이터를 관리하는 방법에 대해 알아봅니다.

{{aem-authoring-edge-early-access}}

## 사용 사례 {#use-cases}

Edge Delivery Services 사이트가 있는 AEM의 경우 키-값 매핑과 같은 테이블 형식 데이터 목록을 유지 관리해야 합니다. 메타데이터 및 리디렉션과 같은 다양한 값의 목록일 수 있습니다. Edge Deliver Services를 사용하면 스프레드시트라는 직관적인 도구를 사용하여 이러한 테이블 형식 목록을 유지 관리할 수 있습니다. AEM은 이러한 스프레드시트를 웹 사이트 또는 웹 애플리케이션에서 쉽게 사용할 수 있는 JSON 파일로 변환합니다.

일반적인 사용 사례는 다음과 같습니다.

* [플레이스홀더](/help/edge/docs/placeholders.md)
* [메타데이터](/help/edge/docs/bulk-metadata.md)
* [헤더](/help/edge/docs/custom-headers.md)
* [리디렉션](/help/edge/docs/redirects.md)
* [구성](/help/edge/docs/setup-byo-cdn-push-invalidation.md) CND 설정의 경우 등

또한 다음과 같은 작업을 수행할 수 있습니다 [스프레드시트 만들기](#own-spreadsheet) 매핑을 저장할 구조의 일부입니다.

이 문서에서는 리디렉션의 예를 사용하여 이러한 스프레드시트를 만드는 방법을 설명합니다. 각 사용 사례에 대한 자세한 내용은 Edge Delivery Services 설명서에서 이전에 연결된 항목을 참조하십시오.

>[!TIP]
>
>스프레드시트가 일반적으로 Edge Delivery Services에서 작동하는 방법에 대한 자세한 내용은 문서를 참조하십시오. [스프레드시트 및 JSON.](/help/edge/developer/spreadsheets.md)

>[!TIP]
>
>스프레드시트는 표 형식 데이터를 유지 관리하는 데만 사용해야 합니다. 구조화된 데이터를 저장하기 위해 [AEM headless 기능을 확인하십시오.](/help/headless/introduction.md)

## 사전 요구 사항 {#prerequisites}

AEM with Edge Delivery Services 프로젝트에서 스프레드시트를 사용하여 매핑을 생성하려면 최신 사이트 템플릿을 사용하여 사이트를 생성해야 합니다.

문서를 참조하십시오. [Edge Delivery Services을 사용한 AEM 작성을 위한 개발자 시작 안내서](/help/edge/edge-dev-getting-started.md) 추가 정보.

## 스프레드시트 만들기 {#spreadsheet}

이 예제에서는 Edge Delivery Services 사이트를 통해 AEM의 리디렉션을 관리하는 스프레드시트를 만듭니다. 동일한 단계는에 적용됩니다. [기타 스프레드시트 유형](#other) 만들고 싶은 항목입니다.

1. AEM as a Cloud Service 제작 인스턴스에 로그인하고 **사이트** 를 클릭하고 스프레드시트가 필요한 사이트 루트로 이동합니다. 탭 또는 클릭 **만들기** -> **페이지**.

   ![페이지 제작](assets/tabular-data/tabular-data-create-page.png)

1. 다음에서 **템플릿** 페이지 만들기 마법사의 탭에서 **리디렉션** 템플릿을 선택한 다음 탭하거나 클릭합니다 **다음**.

   ![템플릿 선택](assets/tabular-data/tabular-data-create-page-teamplate-redirects.png)

1. 다음 **속성** 마법사의 탭에는 리디렉션 스프레드시트의 기본값이 표시됩니다. **만들기**&#x200B;를 탭하거나 클릭합니다.

   * **제목** - 이 값은 그대로 둡니다.
   * **열** - 리디렉션에 필요한 최소 열이 미리 채워집니다.
      * **소스** - 리디렉션할 페이지
      * **대상** - 리디렉션할 페이지

   ![스프레드시트의 속성](assets/tabular-data/tabular-data-create-page-properties-redirects.png)

1. 다음에서 **성공** 대화 상자, 탭 또는 클릭 **열기**.

   ![완료 대화 상자](assets/tabular-data/tabular-data-success.png)

1. 사전 정의된 스프레드시트가 편집기에 로드되는 새 탭이 열립니다 **소스** 및 **대상** 열. 리디렉션을 정의하려면 의 빈 행을 탭하거나 클릭합니다 **소스** 열. 스프레드시트를 편집하면 변경 사항이 자동으로 저장됩니다.

   ![스프레드시트 편집](assets/tabular-data/tabular-data-edit-redirects.png)

   * 다음 **소스** 는 웹 사이트의 도메인을 기준으로 하므로 상대 경로만 포함합니다.
   * 다음 **대상** 다른 웹 사이트로 리디렉션하는 경우 정규화된 URL일 수 있고, 자체 웹 사이트 내에서 리디렉션하는 경우 상대 경로일 수 있습니다.
   * Tab 키를 사용하여 포커스를 다음 셀로 이동합니다.
   * 편집기는 필요에 따라 스프레드시트에 새 행을 추가합니다.
   * 행을 삭제하거나 이동하려면 **삭제** 각 행의 끝에 있는 아이콘과 각 행의 시작 부분에 있는 드래그 핸들입니다.

1. 리디렉션 정의가 끝나면 탭을 닫고 로 돌아갑니다. **사이트** 콘솔.

1. 콘솔에서 생성한 리디렉션 스프레드시트를 탭하거나 클릭하여 선택한 다음 탭하거나 클릭합니다 **빠른 게시** 을 클릭하여 스프레드시트를 게시합니다.

   ![사이트 콘솔에서 스프레드시트를 선택합니다](assets/tabular-data/tabular-data-select-publish.png)

1. 다음에서 **빠른 게시** 대화 상자, 탭 또는 클릭 **게시**.

   ![게시 확인](assets/tabular-data/tabular-data-quick-publish.png)

1. 배너가 게시를 확인합니다.

   ![게시 배너 확인](assets/tabular-data/tabular-data-publish-banner.png)

이제 리디렉션 스프레드시트가 게시되고 공개적으로 액세스할 수 있습니다.

## Paths.json 업데이트 {#paths-json}

AEM이 스프레드시트의 데이터를 사용할 수 있도록 하려면 를 추가로 업데이트해야 합니다 `paths.json` 프로젝트의 파일입니다.

1. GitHub에서 프로젝트의 루트를 엽니다.

1. 을(를) 탭하거나 클릭합니다 `paths.json` 세부 정보를 여는 파일 및 **편집** 아이콘.

   ![paths.json 파일](assets/tabular-data/tabular-data-paths-json.png)

1. 새 스프레드시트를 매핑할 행을 추가합니다. `redirects.json` 리소스.

   ```json
   {
     "mappings": [
      "/content/<site-name>/:/",
      "/content/<site-name>/redirects:/redirects.json"
     ]
   }
   ```

1. 클릭 **변경 내용 커밋...** 변경 사항을 저장하려면 `main`.

   * 다음 대상에게 커밋 `main` 또는 프로세스에 따라 가져오기 요청을 만듭니다.

변경 후 `paths.json` 병합되면 사이트의 리디렉션이 라이브 상태가 됩니다.

## 기타 스프레드시트 유형 {#other}

이제 리디렉션 스프레드시트를 만드는 방법을 알았으므로 다른 표준 스프레드시트 유형을 만들 수 있습니다.

* 플레이스홀더
* 메타데이터
* 헤더
* 구성

섹션에서 동일한 단계를 따르십시오. [스프레드시트 만들기](#spreadsheet) 및 [Paths.json 업데이트](#paths-json) 적절한 템플릿을 선택하고 `paths.json` 적절한 파일입니다.

또한 다음을 수행할 수 있습니다 [나만의 스프레드시트 만들기](#own-spreadsheet) (임의 열 사용)

>[!NOTE]
>
>Edge Delivery Services 프로젝트를 사용하여 AEM에 대한 색인화를 as a Cloud Service으로 관리하기 위해 스프레드시트를 만들 필요가 없습니다.
>
>고유한 색인을 만들려면 [이 설명서를 따르십시오.](https://www.aem.live/developer/indexing#setting-up-more-index-configurations) 자신만의 고유한 을 만들려면 `helix-query.yaml` 파일.

## 나만의 스프레드시트 만들기 {#own-spreadsheet}

1. 섹션에서 동일한 단계를 수행합니다 [스프레드시트를 만듭니다.](#spreadsheet)

1. 템플릿을 선택할 때 다음을 선택합니다 **스프레드시트**.

1. 다음에서 **속성** 마법사의 탭에서는 고유한 열을 추가할 수 있습니다.

   ![고유한 열 추가](assets/tabular-data/tabular-data-own-spreadsheet.png)

   * 다음에서 **열** 섹션, 탭 또는 클릭 **추가** 새 열을 추가합니다.
   * 열의 이름을 입력합니다.
   * 다음을 사용하여 열 제거 또는 재구성 **삭제** 및 핸들 아이콘을 각각 드래그합니다.

1. 스프레드시트를 만들고 리디렉션 스프레드시트에 대한 지침에 따라 게시합니다.

1. 에 매핑 추가 `paths.json` 리디렉션 스프레드시트에 대한 지침에 따라 파일입니다.
