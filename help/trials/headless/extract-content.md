---
title: GraphQL API를 통한 콘텐츠 추출
description: 콘텐츠 조각 및 GraphQL API를 headless 콘텐츠 관리 시스템으로 사용하는 방법에 대해 알아보십시오.
hidefromtoc: true
index: false
exl-id: f5e379c8-e63e-41b3-a9fe-1e89d373dc6b
source-git-commit: bcab02cbd84955ecdc239d4166ae38e5f79b3264
workflow-type: tm+mt
source-wordcount: '847'
ht-degree: 44%

---


# GraphQL API를 통한 콘텐츠 추출 {#extract-content}

>[!CONTEXTUALHELP]
>id="aemcloud_sites_trial_admin_content_fragments_graphql"
>title="GraphQL API를 사용하여 콘텐츠 추출"
>abstract="이 단원에서는 컨텐츠 조각 및 GraphQL API를 헤드리스 컨텐츠 관리 시스템으로 사용하는 방법을 알아봅니다."

>[!CONTEXTUALHELP]
>id="aemcloud_sites_trial_admin_content_fragments_graphql_guide"
>title="GraphQL 탐색기 실행"
>abstract="GraphQL은 외부 클라이언트 애플리케이션이 단일 API 호출을 사용하여 필요한 콘텐츠에 대해서만 AEM을 쿼리할 수 있도록 하는 쿼리 기반 API를 제공합니다. 이 모듈을 따라 두 가지 유형의 쿼리를 실행하는 방법을 알아보십시오. 그런 다음 이전 모듈에서 만든 컨텐츠 조각에서 컨텐츠를 검색하는 방법을 알아봅니다.<br><br>아래 를 클릭하여 새 탭에서 이 모듈을 시작합니다."
>additional-url="https://video.tv.adobe.com/v/328618" text="컨텐츠 소개 비디오 추출"

>[!CONTEXTUALHELP]
>id="aemcloud_sites_trial_admin_content_fragments_graphql_guide_footer"
>title="잘 했어요! 두 가지 기본 쿼리 유형과 자체 콘텐츠를 쿼리하는 방법에 대해 배웠습니다. 이제 AEM GraphQL API를 사용하여 앱에서 예상한 형식으로 콘텐츠를 전달하는 효율적인 쿼리를 만드는 방법을 이해합니다."
>abstract=""

## 샘플 컨텐츠 목록에 대한 쿼리 {#list-query}

클릭 **GraphQL Explorer 시작** 위의 단추를 클릭하면 새 탭에서 GraphQL 탐색기가 열립니다.

![GraphQL 쿼리 편집기](assets/extract-content/query-editor.png)

GraphQL Explorer를 사용하여 헤드리스 컨텐츠에 대한 쿼리를 빌드하고 확인한 후 이를 사용하여 앱 또는 웹 사이트의 콘텐츠를 실행할 수 있습니다. 어떻게 됐는지 봅시다!

1. AEM 헤드리스 평가판에는 테스트 목적으로 컨텐츠를 추출할 수 있는 컨텐츠 조각이 사전 로드된 엔드포인트가 포함되어 있습니다. 을(를) 선택합니다 **AEM 데모 자산** 엔드포인트 **끝점** 편집기의 오른쪽 위 모서리에 있는 드롭다운 메뉴.

   ![엔드포인트 선택](assets/extract-content/select-endpoint.png)

1. 사전 로드된 항목의 목록 쿼리에 대해 다음 코드 조각을 복사합니다 **AEM 데모 자산** 엔드포인트. 목록 쿼리는 특정 컨텐츠 조각 모델을 사용하는 모든 컨텐츠 목록을 반환합니다. 인벤토리 및 카테고리 페이지는 일반적으로 이 쿼리 형식을 사용합니다.

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

1. 복사한 코드를 붙여넣어 쿼리 편집기에서 기존 콘텐츠를 바꿉니다.

   ![목록 쿼리](assets/extract-content/list-query.png)

1. 붙여넣기가 완료되면 쿼리 편집기 왼쪽 상단의 **재생** 버튼을 클릭하여 쿼리를 실행합니다.

1. 결과가 쿼리 편집기 옆에 있는 오른쪽 패널에 표시됩니다. 쿼리가 잘못된 경우, 오른쪽 패널에 오류가 표시됩니다.

   ![목록 쿼리 결과](assets/extract-content/list-query-results.png)

모든 컨텐츠 조각의 전체 목록에 대한 목록 쿼리의 유효성을 방금 검사했습니다. 이 프로세스를 사용하면 앱과 웹 사이트에서 AEM에서 만든 콘텐츠를 검색하는 방법을 보여 주는 결과와 함께 앱이 기대하는 응답을 보장할 수 있습니다.

## 특정 샘플 컨텐츠 쿼리 {#bypath-query}

byPath 쿼리를 실행하면 특정 컨텐츠 조각에 대한 컨텐츠를 검색할 수 있습니다. 특정 콘텐츠 세트에 중점을 둔 페이지 및 제품 세부 정보 페이지에는 일반적으로 이러한 유형의 쿼리가 필요합니다. 어떻게 작동되는지 봅시다!

1. 사전 로드된 의 byPath 쿼리에 대해 다음 코드 조각을 복사합니다 **AEM 데모 자산** 엔드포인트.

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

1. 복사한 코드를 붙여넣어 쿼리 편집기에서 기존 콘텐츠를 바꿉니다.

   ![byPath 쿼리](assets/extract-content/bypath-query.png)

1. 붙여넣기가 완료되면 쿼리 편집기 왼쪽 상단의 **재생** 버튼을 클릭하여 쿼리를 실행합니다.

1. 결과가 쿼리 편집기 옆에 있는 오른쪽 패널에 표시됩니다. 쿼리가 잘못된 경우, 오른쪽 패널에 오류가 표시됩니다.

   ![byPath 쿼리 결과](assets/extract-content/bypath-query-results.png)

해당 조각의 경로로 식별되는 특정 컨텐츠 조각을 검색하기 위해 byPath 쿼리의 유효성을 검사했습니다.

## 자신의 콘텐츠를 쿼리합니다. {#own-queries}

이제 두 가지 기본 유형의 쿼리를 실행했으므로 자신의 콘텐츠를 쿼리할 준비가 되었습니다.

1. 자체 콘텐츠 조각에 대해 쿼리를 실행하려면 **AEM 데모 자산** 폴더에서 **사용자 프로젝트** 폴더로 엔드포인트를 변경합니다.

   ![자체 엔드포인트 선택](assets/extract-content/select-endpoint.png)

1. 쿼리 편집기에서 기존 콘텐츠를 모두 삭제합니다. 그런 다음 여는 브라켓을 입력합니다 `{` 그리고 Ctrl+Space 또는 Option+Space를 눌러 종단점에 정의된 모델의 자동 완료 목록을 표시합니다. 에서 끝나는 모델을 선택합니다. `List` 선택합니다.

   ![쿼리 편집기의 자동 완성 모델](assets/extract-content/auto-complete-models.png)

1. 선택한 컨텐츠 조각 모델에 대해 쿼리에 포함해야 하는 항목을 정의합니다. 다시 여는 괄호 `{`를 입력한 다음 Ctrl+Space 또는 Option+Space를 눌러 자동 완성 목록을 표시합니다. 선택 `items` 선택합니다.

   ![쿼리 편집기의 자동 완성 항목](assets/extract-content/auto-complete-items.png)

1. 선택한 콘텐츠 조각 모델의 쿼리에 포함되어야 하는 필드를 정의합니다. 다시 한 번 열린 브라켓을 입력합니다 `{`를 클릭한 다음 컨텐츠 조각 모델의 사용 가능한 필드 자동 완료 목록을 보려면 Ctrl+Space 또는 Option+Space 를 누릅니다. 목록에서 원하는 모델 필드를 선택합니다.

   ![쿼리 편집기의 자동 완성 필드](assets/extract-content/auto-complete-fields.png)

1. 여러 필드를 쉼표(`,`) 또는 공백으로 구분하고, Ctrl+Space 또는 Option+Space를 다시 눌러 추가 필드를 선택합니다.

1. 작업하는 동안 **정렬** 버튼을 탭하거나 클릭하여 읽기 쉽도록 코드 서식을 자동으로 지정할 수 있습니다.

   ![정렬](assets/extract-content/prettify.png)

1. 완료되면 쿼리 편집기 왼쪽 상단의 **재생** 버튼을 탭하거나 클릭하여 쿼리를 실행합니다.

   ![자체 쿼리 결과](assets/extract-content/custom-query-results.png)

1. 결과가 쿼리 편집기 옆에 있는 오른쪽 패널에 표시됩니다.

사용자의 콘텐츠를 옴니채널 디지털 환경에 구현하는 방식입니다.
