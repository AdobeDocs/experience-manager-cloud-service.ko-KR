---
title: JavaScript로 JSON 콘텐츠 가져오기
description: CodePen 앱 및 JavaScript용 AEM Headless 클라이언트를 사용하여 체험판 환경에서 JSON 콘텐츠를 가져오는 방법을 살펴보십시오.
hidefromtoc: true
index: false
source-git-commit: 3aff5ef2fb9ecdd815f0bc1a813d3a3982b4e0ed
workflow-type: tm+mt
source-wordcount: '800'
ht-degree: 100%

---


# JavaScript로 JSON 콘텐츠 가져오기 {#fetch-json}

>[!CONTEXTUALHELP]
>id="aemcloud_sites_trial_fetch_json_with_javascript"
>title="JavaScript로 JSON 콘텐츠 가져오기"
>abstract="CodePen 앱 및 JavaScript용 AEM Headless 클라이언트를 사용하여 체험판 환경에서 JSON 콘텐츠를 가져오는 방법을 살펴보십시오."

>[!CONTEXTUALHELP]
>id="aemcloud_sites_trial_fetch_json_with_javascript_guide"
>title="샘플 CodePen 앱 실행"
>abstract="GraphQL 지속 쿼리를 사용하여 체험판 환경에서 JSON 데이터를 가져오는 방법을 소개하기 위해 최소한의 CodePen 앱을 구축했습니다.<br><br>아래를 클릭하여 CodePen 예제를 시작한 다음 이 안내서를 따라 자세한 내용을 확인하십시오."

>[!CONTEXTUALHELP]
>id="aemcloud_sites_trial_fetch_json_with_javascript_guide_footer"
>title="이 모듈에서는 JavaScript용 AEM Headless 클라이언트를 사용하여 GraphQL 지속 쿼리를 통해 체험판 환경에서 JSON 데이터를 가져오는 방법을 배웠습니다.<br><br>이제 이 클라이언트를 사용하여 자체 웹 애플리케이션 내에서 데이터를 사용하는 방법을 이해했습니다."
>abstract=""

## 소개 {#intro}

[JavaScript용 AEM Headless 클라이언트](https://github.com/adobe/aem-headless-client-js)를 사용해 JSON 데이터를 가져오는 최소한의 예제 역할을 하는 CodePen 앱에서 시작합니다. 샘플 앱은 기본 콘텐츠 조각 모델의 구조에 관계없이 반환되는 모든 JSON 콘텐츠를 렌더링하도록 설계되었습니다. CodePen 앱은 발생하는 모든 오류를 자세히 표시하려고 시도하므로 앱의 아래쪽 창에 다음과 같은 오류 메시지가 출력될 수 있습니다.

```
{
  "status": "Failed to fetch persisted query: your-project/USE-YOUR-QUERY-HERE from publishHost: https://publish-p00000-e12345.adobeaemcloud.com",
  "message": "[AEMHeadless:REQUEST_ERROR] General Request error: Failed to fetch."
}
```

이전 모듈에서 저장하고 게시한 지속 쿼리를 사용하도록 앱이 아직 구성되지 않았기 때문에 이 오류가 예상됩니다. 다음 단계에서 특정 쿼리에서 데이터를 가져오도록 앱을 구성합니다.

## CodePen 연습 {#code-walkthrough}

CodePen의 JS(Javascript) 창에는 예제 앱의 핵심 내용이 포함되어 있습니다. 2행부터 Skypack CDN에서 JavaScript용 AEM Headless 클라이언트를 가져옵니다. Skypack은 빌드 단계 없이 개발을 용이하게 하는 데 사용되지만, 자체 프로젝트에서 NPM 또는 Yarn과 함께 AEM Headless 클라이언트를 사용할 수도 있습니다. 자세한 내용은 [README](https://github.com/adobe/aem-headless-client-js#aem-headless-client-for-javascript)의 사용 지침을 확인하십시오.

```
import AdobeAemHeadlessClientJs from 'https://cdn.skypack.dev/@adobe/aem-headless-client-js@v3.2.0';
```

6행에서 `publishHost` 쿼리 매개변수를 통해 게시 호스트 세부 정보를 읽습니다. 이는 AEM Headless 클라이언트가 데이터를 가져올 호스트입니다. 이 내용은 일반적으로 앱에 코딩되지만, CodePen 앱이 다른 환경에서 더 쉽게 작동할 수 있도록 쿼리 매개변수를 사용하는 것입니다.

CORS 문제를 방지하기 위해 프록시 Adobe IO 런타임 기능을 사용하도록 12행에서 AEM Headless 클라이언트를 구성합니다. 이 내용은 사용자의 자체 프로젝트에는 필요하지 않지만 CodePen 앱이 체험판 환경에서 작동하려면 필요합니다. 프록시 기능은 쿼리 매개변수에 제공된 `publishHost` 값을 사용하도록 구성됩니다.

```
const aemHeadlessClient = new AdobeAemHeadlessClientJs({
  // Use a proxy to avoid CORS issues
  serviceURL: 'https://102588-505tanocelot.adobeioruntime.net/api/v1/web/aem/proxy',
  headers: {
    'aem-url': publishHost
  }
});
```

마지막으로 AEM Headless 클라이언트를 사용하여 가져오기 요청을 수행하는 데 `fetchJsonFromGraphQL()` 함수가 사용됩니다. 코드가 변경될 때마다 호출되거나, “다시 가져오기” 링크를 눌렀을 때 트리거될 수 있습니다. 실제 `aemHeadlessClient.runPersistedQuery(..)` 호출은 34행에서 발생합니다. 잠시 후 이 JSON 데이터가 렌더링되는 방식을 변경할 예정이지만, 일단은 `resultToPreTag(queryResult)` 함수를 사용해 `#output` div에 출력하겠습니다.

## 지속 쿼리에서 데이터 가져오기 {#use-persisted-query}

25행에서는 앱이 데이터를 가져와야 하는 GraphQL 지속 쿼리를 나타냅니다. 지속 쿼리 이름은 프로젝트 이름의 조합(예: `your-project`)이며 그 뒤에 슬래시, 쿼리 이름이 순서대로 붙습니다.

`persistedQueryName` 변수를 업데이트하여 이전 모듈에서 생성한 지속 쿼리를 사용합니다. 이름 지정 제안을 정확히 따랐다면 `adventures` in the `your-project` 프로젝트라는 지속 쿼리가 만들어지며, `persistedQueryName` 변수를 `your-project/adventures`로 설정해야 합니다.

```
//
// TODO: Use your persisted query here
//
persistedQueryName = 'your-project/adventures';
```

이 변경 사항이 적용되면 앱이 자동으로 새로 고쳐지고 지속 쿼리의 원시 JSON 응답이 `#output` div로 출력됩니다. 오류 메시지가 표시되면 콘솔에서 자세한 내용을 확인하십시오.

앱에 필요한 정확한 속성이 이 JSON에 포함되어 있습니까? 포함되어 있지 않은 경우 AEM 작성자 환경, 도구, GraphQL 쿼리 편집기로 돌아가서(또는 `/aem/graphiql.html` 경로로 이동) 지속 쿼리를 변경하십시오. 완료한 후 쿼리를 저장하고 게시하는 것을 잊지 마십시오.

## JSON 렌더링 변경 {#change-rendering}

현재 JSON은 있는 그다지 창의적이지는 않지만 `pre` 태그에 그대로 렌더링되고 있습니다. `resultToDom()` 함수를 대신 사용하여 JSON 응답을 반복해 더 흥미로운 결과를 도출하는 방법을 설명하도록 CodePen을 전환할 수 있습니다.

이렇게 변경하려면 37행을 주석 처리하고 40행에서 주석을 제거하십시오.

```
// Output the results to a pre tag
//resultToPreTag(queryResult);

// Alternatively, build a colorful div structure with the JSON results and render images inline
resultToDom(queryResult);
```

이 함수는 또한 JSON 응답에 포함된 모든 이미지를 `img` 태그로 렌더링합니다. 생성한 “Adventure” 콘텐츠 조각에 이미지가 포함되어 있지 않은 경우 25행을 수정하여 `aem-demo-assets/adventures-all` 지속 쿼리를 사용하도록 전환할 수 있습니다.

```
persistedQueryName = 'aem-demo-assets/adventures-all';
```

이 쿼리는 이미지를 포함하는 JSON 응답을 생성하며, `resultToDom()` 함수는 인라인으로 렌더링합니다.

![adventures-all 쿼리 결과 및 resultToDom 렌더링 함수](assets/do-not-localize/adventures-all-query-result.png)
