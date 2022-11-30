---
title: GraphQL API를 통해 컨텐츠 추출
description: 컨텐츠 조각 및 GraphQL API를 헤드리스 컨텐츠 관리 시스템으로 사용하는 방법을 알아봅니다.
hidefromtoc: true
index: false
source-git-commit: a832ed1d81866a6470b47d8e30f5c242b10d1422
workflow-type: tm+mt
source-wordcount: '1189'
ht-degree: 1%

---


# GraphQL API를 통해 컨텐츠 추출 {#extract-content}

지금까지 헤드리스를 위한 AEM Trials에서는 다음과 같은 기능을 사용할 수 있습니다 [자체 컨텐츠 조각 모델을 만들었습니다.](content-structure.md) 또한 헤드리스 컨텐츠와 [컨텐츠 조각.](create-content.md) 이제 컨텐츠 조각 및 GraphQL API를 헤드리스 컨텐츠 관리 시스템으로 사용하여 컨텐츠를 제공하는 방법을 배울 수 있습니다.

GraphQL은 단일 API 호출을 사용하여 외부 클라이언트 애플리케이션에서 AEM에 필요한 컨텐츠만 쿼리할 수 있는 쿼리 기반 API를 제공합니다.

먼저 두 가지 유형의 쿼리를 실행하는 방법을 알아봅니다. **list** 및 **byPath** 쿼리 그런 다음 이전에 만든 컨텐츠 조각에서 컨텐츠를 검색하는 방법을 배웁니다. 이 문서는 대화형 투어의 추가 기능으로서 동일한 단계를 적용하고 적절한 추가 리소스에 연결합니다.

>[!TIP]
>
>GraphQL API에 대한 자세한 내용은 [추가 리소스 섹션](#additional-resources) GraphQL API 안내서에 대한 이 모듈의 끝 부분.

## GraphQL 탐색기 {#graphql-explorer}

GraphQL 탐색기에서 시작합니다. 여기에서 헤드리스 컨텐츠에 대한 쿼리를 작성하고 실행할 수 있습니다.

![GraphQL 쿼리 편집기](assets/extract-content/query-editor.png)

인앱 지침 외부에서 GraphQL 탐색기로 직접 탐색하려면 페이지 왼쪽 상단에 있는 Adobe 아이콘을 사용하여 찾습니다. 이렇게 하면 AEM의 전역 탐색이 열립니다. 여기에서 **도구** 탭한 다음 **일반** -> **GraphQL 쿼리 편집기**.

>[!TIP]
>
>AEM의 탐색에 대한 자세한 내용은 [추가 리소스 섹션](#additional-resources) AEM 기본 처리에 대한 자세한 내용은 이 문서를 참조하십시오.

AEM 평가판에는 테스트 목적으로 컨텐츠를 추출할 수 있는 컨텐츠가 미리 로드된 엔드포인트가 있습니다.

![끝점 선택](assets/extract-content/select-endpoint.png)

을(를) 선택합니다 **AEM 데모 자산** 엔드포인트 **끝점** 편집기의 오른쪽 위 모서리에 있는 드롭다운 메뉴(아직 없다면)입니다.

## 목록 쿼리 복사 및 실행 {#list-query}

AEM as a Cloud Service의 GraphQL API가 작동하는 방식을 사용하여 자신에게 맞게 파악하기 위해 간단한 목록 쿼리로 시작합니다. 이 목록 쿼리 예는 특정 컨텐츠 조각 모델을 사용하는 모든 컨텐츠 목록을 반환합니다. 재고 및 카테고리 페이지는 일반적으로 이 쿼리 형식을 사용합니다.

1. 다음 코드 조각을 복사합니다.

   ```text
   {
       adventureList {
         items {
            _path
            adventureTitle
            adventurePrice
            adventureTripLength
            adventurePrimaryImage {
              ... on ImageRef {
               _path
               mimeType
               width
               height
             }
           }
         }
      }
    }
   ```

1. 그런 다음 복사한 코드를 붙여넣어 쿼리 편집기의 기존 콘텐츠를 바꿉니다.

   ![목록 쿼리](assets/extract-content/list-query.png)

1. 붙여넣은 후 **재생** 쿼리 편집기 왼쪽 상단의 단추를 클릭하여 쿼리를 실행합니다.

1. 쿼리가 성공적으로 실행되면 쿼리 편집기 옆에 오른쪽 패널에 결과가 표시됩니다. 쿼리가 올바르지 않으면 오른쪽 패널에 오류가 표시됩니다.

   ![쿼리 결과 나열](assets/extract-content/list-query-results.png)

모든 컨텐츠 조각의 전체 목록에 대한 목록 쿼리의 유효성을 방금 검사했습니다. 이 프로세스는 앱과 웹 사이트에서 AEM에서 만든 콘텐츠를 검색하는 방법을 보여주는 결과를 사용하여 응답이 앱이 기대하는 것임을 확인하는 데 도움이 됩니다.

콘텐츠를 표시해야 하는 다양한 채널 및 플랫폼은 이제 이 쿼리 또는 유사한 기능을 사용하여 헤드리스 콘텐츠를 검색할 수 있습니다.

## byPath 쿼리 복사 및 실행 {#bypath-query}

byPath 쿼리를 실행하면 특정 컨텐츠 조각에 대한 자산을 검색할 수 있습니다. 특정 컨텐츠 세트에 중점을 두는 제품 세부 사항 페이지와 페이지에는 일반적으로 이러한 유형의 쿼리가 필요합니다.

1. 다음 코드 조각을 복사합니다.

   ```text
    {
     adventureByPath(
       _path: "/content/dam/aem-demo-assets/en/adventures/bali-surf-camp/bali-surf-camp"
     ) {
       item {
         _path
         adventureTitle
         adventureDescription {
           json
         }
         adventurePrimaryImage {
           ... on ImageRef {
             _path
             width
             height
           }
         }
       }
     }
   }
   ```

1. 그런 다음 복사한 코드를 붙여넣어 쿼리 편집기의 기존 콘텐츠를 바꿉니다.

   ![byPath 쿼리](assets/extract-content/bypath-query.png)

1. 붙여넣은 후 **재생** 쿼리 편집기 왼쪽 상단의 단추를 클릭하여 쿼리를 실행합니다.

1. 쿼리가 성공적으로 실행되면 쿼리 편집기 옆에 오른쪽 패널에 결과가 표시됩니다. 쿼리가 올바르지 않으면 오른쪽 패널에 오류가 표시됩니다.

1. 쿼리가 성공적으로 실행되면 쿼리 편집기 옆에 오른쪽 패널에 결과가 표시됩니다. 쿼리가 올바르지 않으면 오른쪽 패널에 오류가 표시됩니다.

   ![byPath 쿼리 결과](assets/extract-content/bypath-query-results.png)

모든 컨텐츠 조각의 전체 목록에 대한 목록 쿼리의 유효성을 방금 검사했습니다. 이 프로세스는 앱과 웹 사이트에서 AEM에서 만든 콘텐츠를 검색하는 방법을 보여주는 결과를 사용하여 응답이 앱이 기대하는 것임을 확인하는 데 도움이 됩니다.

콘텐츠를 표시해야 하는 다양한 채널 및 플랫폼은 이제 이 쿼리 또는 유사한 기능을 사용하여 헤드리스 콘텐츠를 검색할 수 있습니다.

## 자신의 콘텐츠에서 쿼리 실행 {#own-queries}

이제 두 가지 기본 유형의 쿼리를 실행했으므로 직접 만든 컨텐츠에 대한 쿼리를 설정하고 실행할 준비가 되었습니다.

1. 자체 컨텐츠 조각에 대해 쿼리를 실행하려면 **AEM 데모 자산** 폴더 **프로젝트** 폴더를 입력합니다.

   ![자신만의 종단점을 선택하십시오](assets/extract-content/select-endpoint.png)

1. 먼저 쿼리 편집기에서 기존 콘텐츠를 모두 선택하고 삭제합니다. 그런 다음 여는 브라켓을 입력합니다 `{` 컨텐츠 조각 모델에 정의된 모델의 자동 전체 목록을 보려면 Ctrl+Space 또는 Option+Space 를 누릅니다. 에서 끝나는 모델을 선택합니다. `List` 참조하십시오.

   ![쿼리 편집기에서 모델 자동 완성](assets/extract-content/auto-complete-models.png)

1. 선택한 컨텐츠 조각 모델에 대해 쿼리에 포함해야 하는 항목을 정의합니다. 다시, 여는 브라켓을 입력합니다 `{`그런 다음 Ctrl+Space 또는 Option+Space를 눌러 자동 완료 목록을 만듭니다. 선택 `items` 참조하십시오.

   ![쿼리 편집기에서 항목 자동 완성](assets/extract-content/auto-complete-items.png)

1. 선택한 컨텐츠 조각 모델에 대해 쿼리에 포함해야 하는 필드를 정의합니다. 다시, 여는 브라켓을 입력합니다 `{`를 클릭한 다음 컨텐츠 조각 모델의 사용 가능한 필드 자동 완료 목록을 보려면 Ctrl+Space 또는 Option+Space 를 누릅니다. 목록에서 모델에서 원하는 필드를 선택합니다.

   ![쿼리 편집기의 필드 자동 완성](assets/extract-content/auto-complete-fields.png)

1. 여러 필드는 쉼표( )로 구분하십시오`,`) 또는 스페이스를 선택하고 Ctrl+Space 또는 Option+Space를 다시 눌러 추가 필드를 선택합니다.

1. 작업할 때 **수정** 읽기 쉽게 코드 형식을 자동으로 지정하는 단추.

   ![수정](assets/extract-content/prettify.png)

1. 완료되면 을 탭하거나 클릭합니다 **재생** 편집기 왼쪽 위에 있는 단추를 클릭하여 쿼리를 실행합니다.

   ![자체 쿼리 결과](assets/extract-content/custom-query-results.png)

다음은 콘텐츠가 옴니채널 디지털 경험에 전달되는 방법입니다. 자세한 내용은 [추가 리소스 섹션](#additional-resources) 추가 샘플 쿼리와 GraphQL API로 수행할 수 있는 추가 작업을 알아보십시오.

## 콘텐츠를 쿼리하는 방법을 배웠습니다! {#conclusion}

잘했어요! 두 가지 기본 유형의 쿼리와 자신의 콘텐츠를 쿼리하는 방법에 대해 알아보았습니다. 을(를) 확인하십시오 [추가 리소스 섹션](#additional-resources) 추가 샘플 쿼리와 GraphQL API로 수행할 수 있는 추가 작업을 알아보십시오.

추출된 컨텐츠를 사용자 지정 React 앱에서 사용하는 방법을 알아보려면 모듈을 검토하십시오 [샘플 React 앱에서 콘텐츠를 사용자 지정합니다.](customize-app.md)

를 클릭하여 체험판 홈 화면으로 돌아갈 수 있습니다. **솔루션** 탐색 막대의 오른쪽 상단에 있는 버튼 및 선택 **Experience Manager**.

![홈 탐색](assets/extract-content/home.png)

## 추가 리소스 {#additional-resources}

컨텐츠 조각 및 AEM에 대한 자세한 내용은 이 추가 설명서를 참조하십시오.

* [GraphQL API 안내서](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/graphql/multi-step/explore-graphql-api.html)
* [기본 처리](/help/sites-cloud/authoring/getting-started/basic-handling.md) - 새 사용자를 위한 AEM 탐색 및 사용 방법에 대한 설명서
* [AEM을 통해 GraphQL을 사용하는 방법 알아보기 - 샘플 콘텐츠 및 쿼리](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/headless/graphql-api/sample-queries.html)
