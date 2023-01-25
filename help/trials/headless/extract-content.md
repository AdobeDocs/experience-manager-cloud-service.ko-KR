---
title: GraphQL API를 통한 콘텐츠 추출
description: 콘텐츠 조각 및 GraphQL API를 Headless 콘텐츠 관리 시스템으로 사용하는 방법에 대해 알아보십시오.
hidefromtoc: true
index: false
exl-id: f5e379c8-e63e-41b3-a9fe-1e89d373dc6b
source-git-commit: 9997e0ea1d78ab2c8bab46a95a664e8537f16b13
workflow-type: tm+mt
source-wordcount: '725'
ht-degree: 100%

---


# GraphQL API를 통한 콘텐츠 추출 {#extract-content}

>[!CONTEXTUALHELP]
>id="aemcloud_sites_trial_admin_content_fragments_graphql"
>title="GraphQL API를 사용하여 콘텐츠 추출"
>abstract="이 모듈에서는 Headless 콘텐츠 관리 시스템으로 콘텐츠 조각 및 GraphQL API를 사용하는 방법을 알아봅니다."

>[!CONTEXTUALHELP]
>id="aemcloud_sites_trial_admin_content_fragments_graphql_guide"
>title="GraphQL 탐색기 실행"
>abstract="GraphQL은 외부 클라이언트 애플리케이션이 단일 API 호출을 사용하여 필요한 콘텐츠에 대해서만 AEM을 쿼리할 수 있도록 하는 쿼리 기반 API를 제공합니다. 이 모듈에 따라 두 가지 유형의 쿼리를 실행하는 방법에 대해 알아보십시오. 그런 다음 이전 모듈에서 만든 콘텐츠 조각에서 콘텐츠를 검색하는 방법을 배웁니다.<br><br>아래를 클릭하여 새 탭에서 이 모듈을 실행하십시오."

>[!CONTEXTUALHELP]
>id="aemcloud_sites_trial_admin_content_fragments_graphql_guide_footer"
>title="훌륭합니다! 두 가지 기본 쿼리 유형과 자체 콘텐츠를 쿼리하는 방법에 대해 배웠습니다. 이제 AEM GraphQL API를 사용하여 앱에서 기대하는 형식으로 콘텐츠를 제공하는 효율적인 쿼리를 만드는 방법을 파악했습니다."
>abstract=""

## 샘플 콘텐츠 목록 쿼리 {#list-query}

새 탭에서 GraphQL 탐색기를 시작합니다. 여기에서는 Headless 콘텐츠를 사용하여 앱이나 웹 사이트에서 콘텐츠를 구동하기 전에 이에 대한 쿼리를 작성하고 유효성을 검사할 수 있습니다.

1. AEM Headless 체험판은 테스트 목적으로 콘텐츠를 추출할 수 있는 콘텐츠 조각이 미리 로드된 엔드포인트가 함께 제공됩니다. 편집기의 오른쪽 상단에 있는 **에셋** 드롭다운 메뉴에서 **AEM 데모 에셋** 엔드포인트를 선택해야 합니다.

1. 미리 로드된 **AEM 데모 에셋** 엔드포인트의 목록 쿼리에 대해 다음 코드 조각을 복사합니다. 목록 쿼리는 특정 콘텐츠 조각 모델을 사용하는 모든 콘텐츠 목록을 반환합니다. 인벤토리 및 카테고리 페이지는 일반적으로 이 쿼리 형식을 사용합니다.

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

1. 복사한 코드를 붙여넣어 쿼리 편집기의 기존 콘텐츠를 바꿉니다.

1. 붙여넣기가 완료되면 쿼리 편집기 왼쪽 상단의 **재생** 버튼을 클릭하여 쿼리를 실행합니다.

1. 쿼리 편집기 옆의 오른쪽 패널에 결과가 표시됩니다. 쿼리가 잘못된 경우, 오른쪽 패널에 오류가 표시됩니다.

   ![목록 쿼리](assets/do-not-localize/list-query-1-3-4-5.png)

모든 콘텐츠 조각의 전체 목록에 대한 목록 쿼리의 유효성을 검사했습니다. 이 프로세스를 사용하면 앱과 웹 사이트에서 AEM에서 만든 콘텐츠를 검색하는 방법을 보여 주는 결과와 함께 앱이 기대하는 응답을 보장할 수 있습니다.

## 특정 샘플 콘텐츠에 대한 쿼리 {#bypath-query}

byPath 쿼리를 실행하면 특정 콘텐츠 조각에 대한 콘텐츠를 검색할 수 있습니다. 특정 콘텐츠 세트에 중점을 둔 페이지 및 제품 세부 정보 페이지에는 일반적으로 이러한 유형의 쿼리가 필요합니다.

1. 미리 로드된 **AEM 데모 에셋** 엔드포인트의 byPath 쿼리에 대해 다음 코드 조각을 복사합니다.

   ```text
    {
     adventureByPath(
       _path: "/content/dam/aem-demo-assets/en/adventures/bali-surf-camp/bali-surf-camp"
     ) {
       item {
         _path
         title
         description {
           json
         }
         primaryImage {
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

1. 복사한 코드를 붙여넣어 쿼리 편집기의 기존 콘텐츠를 바꿉니다.

1. 붙여넣기가 완료되면 쿼리 편집기 왼쪽 상단의 **재생** 버튼을 클릭하여 쿼리를 실행합니다.

1. 쿼리 편집기 옆의 오른쪽 패널에 결과가 표시됩니다. 쿼리가 잘못된 경우, 오른쪽 패널에 오류가 표시됩니다.

   ![byPath 쿼리 결과](assets/do-not-localize/bypath-query-2-3-4.png)

해당 조각의 경로로 식별되는 특정 콘텐츠 조각을 검색하기 위해 byPath 쿼리의 유효성을 검사했습니다.

## 자체 콘텐츠 쿼리 {#own-queries}

두 가지 기본 유형의 쿼리를 실행했으므로 자체 콘텐츠를 쿼리할 준비가 되었습니다.

1. 자체 콘텐츠 조각에 대해 쿼리를 실행하려면 **AEM 데모 에셋** 폴더에서 **사용자 프로젝트** 폴더로 엔드포인트를 변경합니다.

1. 쿼리 편집기에서 기존 콘텐츠를 모두 삭제합니다. 그런 다음 여는 괄호 `{`를 입력하고 Ctrl+Space 또는 Option+Space를 누르면 엔드포인트에 정의된 모델의 자동 완성 목록이 표시됩니다. 옵션에서 `List`로 끝나는 생성 모델을 선택합니다.

   ![사용자 지정 쿼리 시작](assets/do-not-localize/custom-query-1-2.png)

1. 선택한 콘텐츠 조각 모델의 쿼리에 포함되어야 하는 항목을 정의합니다. 다시 여는 괄호 `{`를 입력한 다음 Ctrl+Space 또는 Option+Space를 눌러 자동 완성 목록을 표시합니다. 옵션에서 `items`를 선택합니다.

1. **정렬** 버튼을 탭하거나 클릭하여 읽기 쉽도록 코드 서식을 자동으로 지정할 수 있습니다.

1. 완료되면 쿼리 편집기 왼쪽 상단의 **재생** 버튼을 탭하거나 클릭하여 쿼리를 실행합니다. 편집기가 `items`을 자동 완성하고 쿼리가 실행됩니다.

1. 쿼리 편집기 옆의 오른쪽 패널에 결과가 표시됩니다.

   ![사용자 지정 쿼리 실행](assets/do-not-localize/custom-query-3-4-5-6.png)

이와 같은 방법으로 사용자의 콘텐츠를 옴니채널 디지털 환경에 구현할 수 있습니다.
