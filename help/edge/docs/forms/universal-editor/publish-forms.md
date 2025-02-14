---
title: Edge Delivery Services용 AEM Forms 게시
description: Edge Delivery Services 양식을 빠르고 원활하게 게시합니다.
feature: Edge Delivery Services
role: Admin, Architect, Developer
hide: true
hidefromtoc: true
source-git-commit: a765af62628d8b6308d6f712f450a5a1e62640d9
workflow-type: tm+mt
source-wordcount: '465'
ht-degree: 0%

---

# Edge Delivery Services에 적응형 양식 게시

양식이 완료되어 사용할 준비가 되면 게시하여 고객이 데이터 수집 및 제출에 액세스할 수 있도록 할 수 있습니다. 게시를 통해 Edge Delivery에서 양식을 사용할 수 있으므로 사용자가 양식과 원활하게 상호 작용할 수 있습니다. 이 프로세스를 통해 고객은 실시간으로 양식을 작성하고 제출할 수 있으므로 효율적인 데이터 캡처와 간소화된 처리가 보장됩니다.

## 사전 요구 사항

* **EDS(Edge Delivery Services) 템플릿**&#x200B;을(를) 사용하여 만든 양식입니다. EDS 기반 양식을 만드는 방법에 대해 [자세히 알아보세요](/help/edge/docs/forms/universal-editor/getting-started-universal-editor.md).

## 양식 게시

다음 단계를 수행하여 **EDS 기반 적응형 양식**&#x200B;을(를) Edge Delivery에 게시할 수 있습니다.

<!--1. Select the **Adaptive Form** that you want to publish and click the **Edit** ![edit icon](/help/forms/assets/edit.svg) icon.
   ![Select EDS-Based Form](/help/forms/assets/select-eds-based-form.png)-->

1. 편집기에서 적응형 양식을 열고 상단 레일에서 **게시** 아이콘을 클릭합니다.
   ![게시 클릭](/help/forms/assets/publish-icon-eds-form.png)

1. **게시**&#x200B;를 클릭하면 양식 제목을 포함하여 게시하는 자산을 표시하는 화면이나 팝업이 나타납니다. 이 예제에서는 **Wknd_Form** 템플릿이 사용됩니다.
   ![게시 클릭](/help/forms/assets/on-click-publish.png)

1. **게시**를 다시 클릭하면 양식이 게시되었음을 나타내는 확인 팝업이 나타납니다.
   ![게시 성공](/help/forms/assets/publish-success.png)

1. 양식의 게시 상태를 확인하려면 **게시**를 다시 클릭하세요.
   ![게시 상태](/help/forms/assets/publish-status.png)

1. 양식을 **게시 취소**&#x200B;하려면 편집기에서 양식을 열고 오른쪽 상단의 세 점 메뉴를 클릭한 다음 **게시 취소**를 선택하십시오.
   ![게시 취소](/help/forms/assets/unpublish--form.png)

## Edge Delivery 게시자에 대한 레퍼러 필터를 구성하여 AEM에서 양식 제출 활성화

보안 양식 제출을 보장하려면 AEM 게시자에서 **레퍼러 필터**&#x200B;를 구성해야 합니다. 이 필터는 Edge Delivery의 승인된 요청만 쓰기 작업(POST, PUT, DELETE, COPY, MOVE)을 수행하여 승인되지 않은 수정을 방지합니다. AEM Publisher에 대한 레퍼러 필터를 구성하는 단계는 다음과 같습니다.

### Edge Delivery에서 AEM 인스턴스 URL 업데이트

양식 블록 내의 **constant.js** 파일에서 `submitBaseUrl`을(를) 수정하여 AEM 인스턴스 URL을 지정하십시오.

**클라우드 설치용:**

```js
export const submitBaseUrl = 'https://publish-p120-e12.adobeaemcloud.com';
```
**로컬 개발용:**

```js
export const submitBaseUrl = 'http://localhost:4503';
```

### CORS 구성 수정

Edge Delivery 도메인에서 양식 제출 요청을 허용하도록 **CORS 설정**&#x200B;을 조정합니다. 자세한 내용은 [CORS 구성 안내서](https://experienceleague.adobe.com/en/docs/experience-manager-learn/getting-started-with-aem-headless/deployments/configurations/cors)를 참조하세요.

**샘플 CORS 구성:**

```apache
# Developer Localhost
SetEnvIfExpr "env('CORSProcessing') == 'true' && req_novary('Origin') =~ m#(http://localhost(:\d+)?$)#" CORSTrusted=true

# Franklin Stage
SetEnvIfExpr "env('CORSProcessing') == 'true' && req_novary('Origin') =~ m#(https://.*\.hlx\.page$)#" CORSTrusted=true  

# Franklin Live
SetEnvIfExpr "env('CORSProcessing') == 'true' && req_novary('Origin') =~ m#(https://.*\.hlx\.live$)#" CORSTrusted=true
```
로컬 개발의 경우 [설명서](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/headless/deployment/referrer-filter)를 참조하여 **개발 UI 호스트 URL**&#x200B;에서 CORS를 활성화하십시오.

### 레퍼러 필터 구성

Cloud Manager을 통해 AEM Cloud Service에서 **레퍼러 필터**&#x200B;를 설정합니다. cloud manager를 사용하여 AEM Cloud Service 인스턴스에 레퍼러 필터를 구성하는 방법에 대해 [자세히 알아보기](https://experienceleague.adobe.com/en/docs/experience-manager-learn/foundation/security/understand-cross-origin-resource-sharing).

레퍼러 필터에 대한 **JSON 구성:**

```json
{
  "allow.empty": false,
  "allow.hosts": [],
  "allow.hosts.regexp": [
    "https://.*\\.hlx\\.page:443",
    "https://.*\\.hlx\\.live:443"
  ],
  "filter.methods": [
    "POST",
    "PUT",
    "DELETE",
    "COPY",
    "MOVE"
  ],
  "exclude.agents.regexp": [
    ""
  ]
}
```

이 구성은 필터되는 HTTP 메서드, 허용되는 레퍼러 및 필터에서 제외되는 사용자 에이전트를 지정합니다. 이러한 구성을 구현하면 **Edge Delivery을 통한 양식 제출**&#x200B;이 보호되며 승인된 소스로만 제한됩니다.

### 게시된 적응형 양식에 액세스

이제 다음 URL 형식을 사용하여 **Edge Delivery**&#x200B;을 통해 적응형 양식에 액세스할 수 있습니다.

```
https://<branch>--<repo>--<owner>.aem.page/content/forms/af/<form_name>
```

예를 들어 **Wknd-Form**&#x200B;의 URL은 다음과 같습니다.

```
https://main--universaleditor--wkndforms.aem.live/content/forms/af/wknd-form
```


















