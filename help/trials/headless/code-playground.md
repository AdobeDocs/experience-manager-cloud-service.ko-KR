---
title: 간단한 앱에서 콘텐츠 렌더링
description: CodePen 예제 앱 및 JavaScript용 AEM Headless 클라이언트를 사용하여 체험판 환경에서 JSON 콘텐츠를 가져오는 방법을 알아보겠습니다.
hidefromtoc: true
index: false
exl-id: b7dc70f2-74a2-49f7-ae7e-776eab9845ae
source-git-commit: 7260649eaab303ba5bab55ccbe02395dc8159949
workflow-type: tm+mt
source-wordcount: '980'
ht-degree: 57%

---


# 간단한 앱에서 콘텐츠 렌더링 {#render-content-simple-app}

>[!CONTEXTUALHELP]
>id="aemcloud_sites_trial_fetch_json_with_javascript"
>title="간단한 앱에서 콘텐츠 렌더링"
>abstract="CodePen 예제 앱 및 JavaScript용 AEM Headless 클라이언트를 사용하여 체험판 환경에서 JSON 콘텐츠를 가져오는 방법을 알아보겠습니다."

>[!CONTEXTUALHELP]
>id="aemcloud_sites_trial_fetch_json_with_javascript_guide"
>title="샘플 CodePen 앱 실행"
>abstract="이 안내서는 체험판 환경의 JSON 데이터를 기본 JavaScript 웹 앱으로 쿼리하는 방법을 설명합니다. 이전 학습 모듈에서 모델링하고 만든 콘텐츠 조각을 사용합니다. 필요한 경우 이 안내서에 들어가기 전에 먼저 해당 안내서를 통해 작업하십시오."

>[!CONTEXTUALHELP]
>id="aemcloud_sites_trial_fetch_json_with_javascript_guide_footer"
>title="이 모듈에서는 JavaScript용 AEM Headless 클라이언트를 사용하여 GraphQL 지속 쿼리를 통해 체험판 환경에서 JSON 데이터를 가져오는 방법을 배웠습니다.<br><br>이제 이 클라이언트를 사용하여 자체 웹 애플리케이션 내에서 데이터를 사용하는 방법을 이해했습니다."
>abstract=""

## CodePen {#codepen}

CodePen은 프론트 엔드 웹 개발을 위한 온라인 코드 편집기 및 놀이터입니다. 이를 통해 브라우저에서 HTML, CSS 및 JavaScript 코드를 작성하고 작업의 결과를 거의 즉시 볼 수 있습니다. 작업을 저장하고 다른 사람과 공유할 수도 있습니다. Adobe은 를 사용하여 체험판 환경에서 JSON 데이터를 가져오는 데 사용할 수 있는 앱을 CodePen에 만들었습니다. [JavaScript용 AEM Headless 클라이언트](https://github.com/adobe/aem-headless-client-js). 이 앱을 있는 그대로 사용하거나 자신의 CodePen 계정에 포크하여 추가로 사용자 정의할 수 있습니다.

클릭 **샘플 CodePen 앱 실행** 체험판에서 버튼을 클릭하면 CodePen의 앱으로 이동합니다. 이 앱은 JavaScript로 JSON 데이터를 가져오는 최소한의 예입니다. 샘플 앱은 기본 콘텐츠 조각 모델의 구조에 관계없이 반환되는 모든 JSON 콘텐츠를 렌더링하도록 설계되었습니다. 기본 제공되는 앱은 `aem-demo-assets` 체험판 환경에 포함된 지속 쿼리 다음과 유사한 JSON 응답이 표시되어야 합니다.

```json
{
  "data": {
    "adventureList": {
      "items": [
        {
          "_path": "/content/dam/aem-demo-assets/en/adventures/bali-surf-camp/bali-surf-camp",
          "title": "Bali Surf Camp",
          "price": "$5000 USD",
          ...
```

대신 오류가 표시되면 브라우저 콘솔에서 자세한 내용을 확인하거나 [Slack](https://adobe-dx-support.slack.com)을 확인합니다.

이제 CodePen에 대해 조금 알게 되었으므로 다음으로 이전 모듈에서 생성한 지속 쿼리에서 데이터를 가져오도록 앱을 구성합니다.

## JavaScript 코드 연습 {#code-walkthrough}

다음 **JS** 코드 펜의 오른쪽 창에는 예제 앱의 JavaScript가 포함되어 있습니다. 2행부터 Skypackage CDN에서 JavaScript용 AEM Headless 클라이언트를 가져옵니다. Skypack은 빌드 단계 없이 개발을 용이하게 하는 데 사용되지만, 자체 프로젝트에서 NPM 또는 Yarn과 함께 AEM Headless 클라이언트를 사용할 수도 있습니다. 자세한 내용은 [README](https://github.com/adobe/aem-headless-client-js#aem-headless-client-for-javascript)의 사용 지침을 확인하십시오.

```javascript
import AdobeAemHeadlessClientJs from 'https://cdn.skypack.dev/@adobe/aem-headless-client-js@v3.2.0';
```

6행에서 게시 호스트 세부 사항을 읽었습니다. `publishHost` 쿼리 매개 변수. 이 매개 변수는 AEM Headless 클라이언트가 데이터를 가져오는 호스트입니다. 이 기능은 일반적으로 앱에 코딩되지만, 쿼리 매개 변수를 사용하여 CodePen 앱이 다른 환경에서 보다 쉽게 작동하도록 합니다.

12행에서 AEM Headless 클라이언트를 구성합니다.

```javascript
const aemHeadlessClient = new AdobeAemHeadlessClientJs({
  // Use a proxy to avoid CORS issues
  serviceURL: 'https://102588-505tanocelot.adobeioruntime.net/api/v1/web/aem/proxy',
  headers: {
    'aem-url': publishHost
  }
});
```

>[!NOTE]
>
>다음 **serviceURL** CORS 문제를 방지하기 위해 프록시 Adobe I/O Runtime 함수를 사용하도록 설정되었습니다. 이 프록시는 자체 프로젝트에 필요하지 않지만 CodePen 앱이 체험판 환경에서 작동하는 데 필요합니다. 프록시 함수는 쿼리 매개변수에 제공된 **publishHost** 값을 사용하도록 구성됩니다.

마지막으로 AEM Headless 클라이언트를 사용하여 가져오기 요청을 수행하는 데 `fetchJsonFromGraphQL()` 함수가 사용됩니다. 코드가 변경될 때마다 호출되거나 **다시 가져오기** 링크를 누르면 트리거될 수 있습니다. 실제 `aemHeadlessClient.runPersistedQuery(..)` 호출은 34행에서 발생합니다. 잠시 후 이 JSON 데이터가 렌더링되는 방식을 변경하지만 지금은 로 인쇄합니다. `#output` div 사용 `resultToPreTag(queryResult)` 함수.

## 지속 쿼리에서 데이터 가져오기 {#use-persisted-query}

25행에서 앱이 데이터를 가져와야 하는 GraphQL 지속 쿼리를 나타냅니다. 지속 쿼리 이름은 끝점의 이름(즉, `your-project` 또는 `aem-demo-assets`), 슬래시, 쿼리의 이름 순으로 표시됩니다. 이전 모듈 지침을 정확히 따랐다면 만든 지속 쿼리가 `your-project` 엔드포인트.

1. 업데이트 `persistedQueryName` 이전 모듈에서 만든 지속 쿼리를 사용하도록 변수를 만듭니다. 이름 지정 제안을 정확히 따랐다면 `your-project` 엔드포인트에서 `adventure-list`로 명명된 지속 쿼리가 생성되고 `persistedQueryName` 변수를 `your-project/adventure-list`로 설정할 것입니다.

   ```javascript
   //
   // TODO: Use your persisted query here
   //
   persistedQueryName = 'your-project/adventure-list';
   ```

1. 이 변경 사항이 적용되면 앱이 자동으로 새로 고쳐지고 지속 쿼리의 원시 JSON 응답이 `#output` div로 출력됩니다. 오류 메시지가 표시되면 콘솔에서 자세한 내용을 확인하십시오. 이 단계에서 여전히 문제가 있을 경우 [Slack](https://adobe-dx-support.slack.com)을 확인하십시오.

1. 앱에 필요한 정확한 속성이 이 JSON에 포함되어 있습니까? 그렇지 않은 경우 다시 변경을 위한 [GraphQL API를 사용하여 콘텐츠 추출](https://experience.adobe.com/experiencemanager/learn/extract_content_using_graphql) 학습 안내서를 확인하십시오. 완료한 후 쿼리를 저장하고 게시하는 것을 잊지 마십시오.

## JSON 렌더링 변경 {#change-rendering}

JSON은 의 있는 그대로 렌더링됩니다. `pre` 태그는 매우 창의적이지 않습니다. 코드 펜을 전환하여 `resultToDom()` 대신 를 사용하여 JSON 응답을 반복하여 더 흥미로운 결과를 생성할 수 있는 방법을 보여 줍니다.

1. 이렇게 변경하려면 37행을 주석 처리하고 40행에서 주석을 제거하십시오.

   ```javascript
   // Output the results to a pre tag
   //resultToPreTag(queryResult);
   
   // Alternatively, build a colorful div structure with the JSON results and render images inline
   resultToDom(queryResult);
   ```

1. 이 함수는 JSON 응답에 포함된 모든 이미지를 로 렌더링합니다. `img` 태그에 가깝게 배치하십시오. 생성한 **모험** 콘텐츠 조각에 이미지가 포함되어 있지 않은 경우 25행을 수정하여 `aem-demo-assets/adventures-all` 지속 쿼리를 사용하도록 전환할 수 있습니다.

   ```javascript
   persistedQueryName = 'aem-demo-assets/adventures-all';
   ```

이 쿼리는 이미지를 포함하는 JSON 응답과 `resultToDom()` 함수는 세그먼트를 인라인으로 렌더링합니다.

![adventures-all 쿼리 결과 및 resultToDom 렌더링 함수](assets/do-not-localize/adventures-all-query-result.png)

이제 모델과 쿼리를 빌드하는 작업을 완료했으므로 콘텐츠 팀이 쉽게 인계받을 수 있습니다. 다음 모듈에서는 콘텐츠 작성자 플로우를 표시합니다.
