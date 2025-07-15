---
title: Edge Delivery Services용 AEM Forms 게시.
description: Edge Delivery Services 양식을 빠르고 원활하게 게시할 수 있습니다.
feature: Edge Delivery Services
role: Admin, Architect, Developer
exl-id: ba1c608d-36e9-4ca1-b87b-0d1094d978db
source-git-commit: 9ef4c5638c2275052ce69406f54dda3ea188b0ef
workflow-type: tm+mt
source-wordcount: '477'
ht-degree: 97%

---

# Edge Delivery Services에 적응형 양식 게시

<span class="preview"> <a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/release-notes/prerelease.html?lang=ko#new-features">시험판 채널</a>을 통해 사용할 수 있는 시험판 기능입니다. </span>


양식이 완성되어 사용할 준비가 되면 고객이 데이터를 수집하고 제출할 수 있도록 양식을 게시할 수 있습니다. 게시를 통해 Edge Delivery에서 양식을 사용할 수 있으므로 사용자가 원활하게 상호 작용할 수 있습니다. 이 프로세스를 통해 고객은 실시간으로 양식을 작성하고 제출할 수 있으며, 효율적인 데이터 수집과 간소화된 처리를 보장합니다.

## 사전 요구 사항

* **Edge Delivery Services 템플릿**&#x200B;을 사용하여 만든 양식. EDS 기반 양식을 만드는 방법에 대해 [자세히 알아보기](/help/edge/docs/forms/universal-editor/getting-started-universal-editor.md).

## 양식 게시

다음 단계를 따라 **EDS 기반 적응형 양식**&#x200B;을 Edge Delivery에 게시할 수 있습니다.

<!--1. Select the **Adaptive Form** that you want to publish and click the **Edit** ![edit icon](/help/forms/assets/edit.svg) icon.
   ![Select EDS-Based Form](/help/forms/assets/select-eds-based-form.png)-->

1. 편집기에서 적응형 양식을 열고 위쪽 레일에 있는 **게시** 아이콘을 클릭합니다.
   ![게시 클릭](/help/forms/assets/publish-icon-eds-form.png)

1. **게시**&#x200B;를 클릭하면 양식의 제목을 포함한 게시 자산을 보여 주는 화면 또는 팝업이 나타납니다. 이 예제에서는 **Wknd_Form** 템플릿이 사용되었습니다.
   ![클릭 시 게시](/help/forms/assets/on-click-publish.png)

1. **게시**&#x200B;를 다시 클릭하면 확인 팝업이 나타나 양식이 게시되었음을 알려 줍니다.
   ![게시 성공](/help/forms/assets/publish-success.png)

1. 양식의 게시 상태를 확인하려면 **게시**&#x200B;를 다시 클릭합니다.
   ![게시 상태](/help/forms/assets/publish-status.png)

1. 양식을 **게시 취소**&#x200B;하려면 편집기에서 양식을 열고 오른쪽 상단의 점 3개로 된 메뉴를 클릭한 다음 **게시 취소**&#x200B;를 클릭합니다.
   ![게시 취소](/help/forms/assets/unpublish--form.png)

## AEM Publisher에 대한 레퍼러 필터를 구성하여 Edge Delivery에서 양식 제출 활성화

안전한 양식 제출을 보장하려면 AEM Publisher에서 **레퍼러 필터**&#x200B;를 구성해야 합니다. 이 필터는 Edge Delivery의 승인된 요청만 쓰기 작업(POST, PUT, DELETE, COPY, MOVE)을 수행할 수 있도록 하여 무단 수정을 방지합니다. 다음은 AEM Publisher에 대한 레퍼러 필터를 구성하는 단계입니다.

### Edge Delivery에서 AEM 인스턴스 URL 업데이트

양식 블록 내의 **constant.js** 파일에서 `submitBaseUrl`을 수정하여 AEM 인스턴스 URL을 지정합니다.

**클라우드 설정의 경우:**

```js
export const submitBaseUrl = 'https://publish-p120-e12.adobeaemcloud.com';
```

**로컬 개발의 경우:**

```js
export const submitBaseUrl = 'http://localhost:4503';
```

### CORS 구성 수정

Edge Delivery 도메인에서 양식 제출 요청을 허용하도록 **CORS 설정**&#x200B;을 조정합니다. 자세한 내용은 [CORS 구성 안내서](https://experienceleague.adobe.com/ko/docs/experience-manager-learn/getting-started-with-aem-headless/deployments/configurations/cors)를 참조하십시오.

**예제 CORS 구성:**

```apache
# Developer Localhost
SetEnvIfExpr "env('CORSProcessing') == 'true' && req_novary('Origin') =~ m#(http://localhost(:\d+)?$)#" CORSTrusted=true

# Franklin Stage
SetEnvIfExpr "env('CORSProcessing') == 'true' && req_novary('Origin') =~ m#(https://.*\.hlx\.page$)#" CORSTrusted=true  

# Franklin Live
SetEnvIfExpr "env('CORSProcessing') == 'true' && req_novary('Origin') =~ m#(https://.*\.hlx\.live$)#" CORSTrusted=true
```

로컬 개발의 경우 CORS를 **개발 UI 호스트 URL**&#x200B;에서 활성화하는 방법에 대한 [설명서](https://experienceleague.adobe.com/ko/docs/experience-manager-cloud-service/content/headless/deployment/referrer-filter)를 참조하십시오.

### 레퍼러 필터 구성

Cloud Manager를 통해 AEM Cloud Service에서 **레퍼러 필터**&#x200B;를 설정합니다. 클라우드 관리자를 사용하여 AEM Cloud Service 인스턴스에서 레퍼러 필터를 구성하는 방법에 대해 [자세히 알아보기](https://experienceleague.adobe.com/ko/docs/experience-manager-learn/foundation/security/understand-cross-origin-resource-sharing).

**레퍼러 필터에 대한 JSON 구성:**

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

이 구성은 필터링되는 HTTP 메서드, 허용되는 레퍼러, 필터에서 제외되는 사용자 에이전트를 지정합니다. 이러한 구성을 구현하면 **Edge Delivery를 통한 양식 제출**&#x200B;이 안전하게 보호되고 승인된 소스로만 제한됩니다.

### 게시된 적응형 양식에 액세스하기

이제 적응형 양식은 다음 URL 형식을 사용하여 **Edge Delivery**&#x200B;를 통해 액세스할 수 있습니다.

```
https://<branch>--<repo>--<owner>.aem.page/content/forms/af/<form_name>
```

예를 들어 **Wknd-Form**&#x200B;의 URL은 다음과 같습니다.

```
https://main--universaleditor--wkndforms.aem.live/content/forms/af/wknd-form
```


## 추가 참조

{{universal-editor-see-also}}

