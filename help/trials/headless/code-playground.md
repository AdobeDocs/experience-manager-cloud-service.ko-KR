---
title: JavaScript를 사용하여 JSON 콘텐츠 가져오기
description: CodePen 앱 및 AEM Headless Client for JavaScript를 사용하여 평가판 환경에서 JSON 컨텐츠 가져오기를 탐색합니다.
hidefromtoc: true
index: false
source-git-commit: 3aff5ef2fb9ecdd815f0bc1a813d3a3982b4e0ed
workflow-type: tm+mt
source-wordcount: '800'
ht-degree: 0%

---


# JavaScript를 사용하여 JSON 콘텐츠 가져오기 {#fetch-json}

>[!CONTEXTUALHELP]
>id="aemcloud_sites_trial_fetch_json_with_javascript"
>title="JavaScript를 사용하여 JSON 콘텐츠 가져오기"
>abstract="CodePen 앱 및 AEM Headless Client for JavaScript를 사용하여 평가판 환경에서 JSON 컨텐츠 가져오기를 탐색합니다."

>[!CONTEXTUALHELP]
>id="aemcloud_sites_trial_fetch_json_with_javascript_guide"
>title="샘플 CodePen 앱 실행"
>abstract="GraphQL 지속적인 쿼리를 사용하여 평가판 환경에서 JSON 데이터를 가져오기 위해 최소한의 CodePen 앱을 사용했습니다.<br><br>아래 를 클릭하여 CodePen 예를 시작한 다음, 이 안내서에 따라 자세한 내용을 확인하십시오."

>[!CONTEXTUALHELP]
>id="aemcloud_sites_trial_fetch_json_with_javascript_guide_footer"
>title="이 단원에서는 GraphQL 지속적인 쿼리를 사용하여 JavaScript용 AEM Headless Client를 사용하여 평가판 환경에서 JSON 데이터를 가져오는 방법을 배웁니다.<br><br>이제 이 클라이언트를 사용하여 웹 애플리케이션 내에서 데이터를 사용하는 방법을 이해할 수 있습니다."
>abstract=""

## 소개 {#intro}

를 사용하여 JSON 데이터를 가져오는 최소한의 예 역할을 하는 CodePen 앱에서 시작합니다. [JavaScript용 AEM Headless 클라이언트](https://github.com/adobe/aem-headless-client-js). 샘플 앱은 기본 컨텐츠 조각 모델의 구조에 관계없이 반환되는 JSON 컨텐츠를 렌더링하도록 설계되었습니다. CodePen 앱에서는 발생한 모든 오류와 함께 자세한 정보를 확인하려고 하므로 앱의 하단 창에 다음 오류 메시지가 인쇄될 수 있습니다.

```
{
  "status": "Failed to fetch persisted query: your-project/USE-YOUR-QUERY-HERE from publishHost: https://publish-p00000-e12345.adobeaemcloud.com",
  "message": "[AEMHeadless:REQUEST_ERROR] General Request error: Failed to fetch."
}
```

이전 모듈에 저장하고 게시한 지속형 쿼리를 사용하도록 앱이 아직 구성되지 않았기 때문에 이 오류가 발생할 수 있습니다. 다음 단계에서 특정 쿼리에서 데이터를 가져오도록 앱을 구성합니다.

## 코드 펜 연습 {#code-walkthrough}

CodePen의 JS(Javascript) 창에는 예제 앱의 뇌가 포함되어 있습니다. 2행에서 시작하여 Skypack CDN에서 JavaScript용 AEM Headless Client를 가져옵니다. Skypack은 빌드 단계 없이 개발을 용이하게 하는 데 사용되지만, 프로젝트에서 NPM 또는 Yarn이 있는 AEM Headless Client를 사용할 수도 있습니다. 사용 지침을 보려면 [README](https://github.com/adobe/aem-headless-client-js#aem-headless-client-for-javascript) 자세한 내용은

```
import AdobeAemHeadlessClientJs from 'https://cdn.skypack.dev/@adobe/aem-headless-client-js@v3.2.0';
```

6행에서 게시 호스트 세부 사항은 `publishHost` 쿼리 매개 변수. AEM Headless 클라이언트가 데이터를 가져오는 호스트입니다. 일반적으로 앱으로 코딩되지만, CodePen 앱이 다른 환경에서 보다 쉽게 작동하도록 쿼리 매개 변수를 사용합니다.

CORS 문제를 방지하기 위해 프록시 Adobe IO 런타임 함수를 사용하도록 AEM Headless 클라이언트를 12행에 구성합니다. 이 작업은 프로젝트에서 수행할 필요는 없지만 CodePen 앱이 평가판 환경에서 작동하는 데 필요합니다. 프록시 함수는 `publishHost` 쿼리 매개 변수에 제공된 값입니다.

```
const aemHeadlessClient = new AdobeAemHeadlessClientJs({
  // Use a proxy to avoid CORS issues
  serviceURL: 'https://102588-505tanocelot.adobeioruntime.net/api/v1/web/aem/proxy',
  headers: {
    'aem-url': publishHost
  }
});
```

마지막으로, 함수 `fetchJsonFromGraphQL()` AEM Headless 클라이언트를 사용하여 가져오기 요청을 수행하는 데 사용됩니다. 코드가 변경될 때마다 호출되거나, &quot;Refetch&quot; 링크를 눌러 트리거할 수 있습니다. 실제 `aemHeadlessClient.runPersistedQuery(..)` 34번에 호출이 발생합니다. 잠시 후에 이 JSON 데이터가 렌더링되는 방식을 변경하겠습니다. 하지만 이제부터는 이 데이터를 `#output` div를 사용하여 `resultToPreTag(queryResult)` 함수 위에 있어야 합니다.

## 지속된 쿼리에서 데이터 가져오기 {#use-persisted-query}

25줄에서는 앱에서 데이터를 가져와야 하는 GraphQL 지속된 쿼리를 나타냅니다. 지속된 쿼리 이름은 프로젝트 이름(예: `your-project`), 뒤에 슬래시, 쿼리 이름이 옵니다.

업데이트 `persistedQueryName` 변수를 사용하십시오. 이름 지정 제안을 정확히 따르는 경우 이름이 인 지속된 쿼리를 만들 수 있습니다 `adventures` 에서 `your-project` 프로젝트를 생성하고, `persistedQueryName` 변수까지 `your-project/adventures`:

```
//
// TODO: Use your persisted query here
//
persistedQueryName = 'your-project/adventures';
```

이 변경 사항이 적용되면 앱이 자동으로 새로 고침되고 지속된 쿼리의 원시 JSON 응답을 `#output` div. 오류 메시지가 표시되면 콘솔에 추가 정보가 있는지 확인합니다.

이 JSON에는 앱에 필요한 정확한 속성이 포함되어 있습니까? 없는 경우 AEM 작성자 환경, 도구, GraphQL 쿼리 편집기로 돌아갑니다(또는 `/aem/graphiql.html` 경로)를 사용하여 지속형 쿼리를 변경할 수 있습니다. 완료되면 쿼리를 저장하고 게시합니다.

## JSON 렌더링 변경 {#change-rendering}

현재 JSON이 현재 `pre` 태그입니다. CodePen을 전환하여 `resultToDom()` 를 사용하십시오.

이 변경 사항을 적용하려면 37행을 주석 처리하여 40행에서 주석을 제거합니다.

```
// Output the results to a pre tag
//resultToPreTag(queryResult);

// Alternatively, build a colorful div structure with the JSON results and render images inline
resultToDom(queryResult);
```

이 함수는 또한 JSON 응답에 포함된 모든 이미지를 `img` 태그에 가깝게 포함했습니다. 만든 &quot;Adventure&quot; 컨텐츠 조각에 이미지가 포함되지 않으면 `aem-demo-assets/adventures-all` 라인 25를 수정하여 지속형 쿼리:

```
persistedQueryName = 'aem-demo-assets/adventures-all';
```

이 쿼리는 이미지를 포함하는 JSON 응답과 `resultToDom()` 함수가 인라인으로 렌더링됩니다.

![모험-all 쿼리 및 resultToDom 렌더링 함수 결과](assets/do-not-localize/adventures-all-query-result.png)
