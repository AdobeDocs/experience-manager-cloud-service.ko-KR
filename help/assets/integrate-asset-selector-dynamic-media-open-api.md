---
title: ' [!DNL Adobe Experience Manager] as a [!DNL Cloud Service]용 자산 선택기'
description: 에셋 선택기를 다양한 Adobe, 비Adobe 및 타사 애플리케이션과 통합합니다.
role: Admin, User
exl-id: b01097f3-982f-4b2d-85e5-92efabe7094d
source-git-commit: f9f5b2a25933e059cceacf2ba69e23d528858d4b
workflow-type: tm+mt
source-wordcount: '884'
ht-degree: 3%

---

# OpenAPI 기능과 Dynamic Media 통합 {#integrate-asset-selector-dynamic-media-open-apis}

에셋 선택기를 사용하면 다양한 Adobe 애플리케이션을 사용하여 를 통합하여 두 애플리케이션이 원활하게 함께 작동할 수 있습니다.


## 사전 요구 사항 {#prereqs-polaris}

Asset Selector를 OpenAPI 기능과 Dynamic Media과 통합하는 경우 다음 전제 조건을 사용하십시오.

* [커뮤니케이션 방법](/help/assets/overview-asset-selector.md#prereqs)
* OpenAPI 기능을 사용하여 Dynamic Media에 액세스하려면 다음에 대한 라이센스가 있어야 합니다.
   * Assets 저장소(예: Experience Manager Assets as a Cloud Service)
   * AEM Dynamic Media.
* 브랜드 일관성을 유지하기 위해 [승인된 자산](/help/assets/approve-assets.md)만 사용할 수 있습니다.

## OpenAPI 기능과 Dynamic Media 통합 {#adobe-app-integration-polaris}

Dynamic Media OpenAPI 프로세스와 에셋 선택기를 통합하려면 사용자 지정된 Dynamic Media URL을 생성하거나 Dynamic Media URL을 선택할 준비가 된 것 등을 포함하는 다양한 단계를 수행해야 합니다.

### OpenAPI 기능과 Dynamic Media용 Asset Selector 통합 {#integrate-dynamic-media}

`rootPath` 및 `path` 속성은 OpenAPI 기능을 사용하는 Dynamic Media에 속하지 않아야 합니다. 대신 `aemTierType` 속성을 구성할 수 있습니다. 다음은 구성 구문입니다.

```
aemTierType:[1: "delivery"]
```

이 구성을 사용하면 폴더 없이 또는 플랫 구조로 승인된 모든 에셋을 볼 수 있습니다. 자세한 내용을 보려면 [자산 선택기 속성](/help/assets/asset-selector-properties.md) 아래의 `aemTierType` 속성으로 이동하십시오.


### 승인된 자산에서 동적 게재 URL 만들기 {#create-dynamic-media-url}

자산 선택기를 설정하면 선택한 자산에서 동적 게재 URL을 만드는 데 오브젝트 스키마가 사용됩니다.
예를 들어 에셋 선택 시 수신되는 오브젝트 배열에서 한 오브젝트의 스키마:

```
{
"dc:format": "image/jpeg",
"repo:assetId": "urn:aaid:aem:xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx",
"repo:name": "image-7.jpg",
"repo:repositoryId": "delivery-pxxxx-exxxxxx.adobe.com",
...
}
```

선택한 모든 자산은 JSON 개체 역할을 하는 `handleSelection` 함수에 의해 전달됩니다. 예, `JsonObj`. 동적 게재 URL은 아래 캐리어를 결합하여 만들어집니다.

| 오브젝트 | JSON |
|---|---|
| 호스트 | `assetJsonObj["repo:repositoryId"]` |
| API 루트 | `/adobe/dynamicmedia/deliver` |
| asset-id | `assetJsonObj["repo:assetId"]` |
| seo-name | `assetJsonObj["repo:name"].split(".").slice(0,-1).join(".")` |
| 형식 | `.jpg` |

#### 승인된 에셋 게재 API 사양 {#approved-assets-delivery-api-specification}

URL 형식:
`https://<delivery-api-host>/adobe/dynamicmedia/deliver/<asset-id>/<seo-name>.<format>?<image-modification-query-parameters>`

위치,

* 호스트가 `https://delivery-pxxxxx-exxxxxx.adobe.com`입니다.
* API 루트: `"/adobe/dynamicmedia/deliver"`
* `<asset-id>`은(는) 자산 식별자입니다.
* `<seo-name>`은(는) 에셋의 이름입니다.
* `<format>`은(는) 출력 형식입니다.
* 승인된 자산의 배달 API 사양에서 지원하는 `<image modification query parameters>`

#### 승인된 에셋 게재 API {#approved-assets-delivery-api}

동적 게재 URL은 다음 구문을 갖습니다.
`https://<delivery-api-host>/adobe/assets/deliver/<asset-id>/<seo-name>`, 위치,

* 호스트가 `https://delivery-pxxxxx-exxxxxx.adobe.com`입니다.
* 원본 렌디션 배달의 API 루트는 `"/adobe/assets/deliver"`입니다.
* `<asset-id>`은(는) 자산 식별자입니다.
* `<seo-name>`은(는) 확장이 있거나 없을 수 있는 에셋의 이름입니다.

### 동적 게재 URL 선택 준비 완료 {#ready-to-pick-dynamic-delivery-url}

선택한 모든 자산은 JSON 개체 역할을 하는 `handleSelection` 함수에 의해 전달됩니다. 예, `JsonObj`. 동적 게재 URL은 아래 캐리어를 결합하여 만들어집니다.

| 오브젝트 | JSON |
|---|---|
| 호스트 | `assetJsonObj["repo:repositoryId"]` |
| API 루트 | `/adobe/assets/deliver` |
| asset-id | `assetJsonObj["repo:assetId"]` |
| seo-name | `assetJsonObj["repo:name"]` |

다음은 JSON 개체를 트래버스하는 두 가지 방법입니다.

![동적 게재 url](assets/dynamic-delivery-url.png)

* **썸네일:** 썸네일은 이미지일 수 있으며 자산은 PDF, 비디오, 이미지 등입니다. 하지만 에셋 썸네일의 높이 및 너비 속성을 동적 게재 렌디션으로 사용할 수 있습니다.
다음 렌디션 세트는 PDF 유형 에셋에 사용할 수 있습니다.
사이드 킥에서 PDF를 선택하면 선택 컨텍스트에 아래 정보가 표시됩니다. 다음은 JSON 개체를 트래버스하는 방법입니다.

  <!--![Thumbnail dynamic delivery url](image-1.png)-->

  위의 스크린샷에서 렌디션 링크의 배열에 대해 `selection[0].....selection[4]`을(를) 참조할 수 있습니다. 예를 들어 썸네일 렌디션 중 하나의 주요 속성은 다음과 같습니다.

  ```
  { 
      "height": 319, 
      "width": 319, 
      "href": "https://delivery-pxxxxx-exxxxx-cmstg.adobeaemcloud.com/adobe/assets/urn:aaid:aem:8560f3a1-d9cf-429d-a8b8-d81084a42d41/as/algorithm design.jpg?accept-experimental=1&width=319&height=319&preferwebp=true", 
      "type": "image/webp" 
  } 
  ```

위 스크린샷에서는 PDF이 필요하고 해당 썸네일이 아닌 경우 PDF의 원래 렌디션의 게재 URL을 타겟 경험에 통합해야 합니다. 예, `https://delivery-pxxxxx-exxxxx-cmstg.adobeaemcloud.com/adobe/assets/urn:aaid:aem:8560f3a1-d9cf-429d-a8b8-d81084a42d41/original/as/algorithm design.pdf?accept-experimental=1`

* **비디오:** 포함된 iFrame을 사용하는 비디오 유형 자산에 비디오 플레이어 URL을 사용할 수 있습니다. Target 경험에서 다음 배열 변환을 사용할 수 있습니다.
  <!--![Video dynamic delivery url](image.png)-->

  ```
  { 
      "height": 319, 
      "width": 319, 
      "href": "https://delivery-pxxxxx-exxxxx-cmstg.adobeaemcloud.com/adobe/assets/urn:aaid:aem:2fdef732-a452-45a8-b58b-09df1a5173cd/as/asDragDrop.2.jpg?accept-experimental=1&width=319&height=319&preferwebp=true", 
      "type": "image/webp" 
  } 
  ```

  위의 스크린샷에서 렌디션 링크의 배열에 대해 `selection[0].....selection[4]`을(를) 참조할 수 있습니다. 예를 들어 썸네일 렌디션 중 하나의 주요 속성은 다음과 같습니다.

  위 스크린샷의 코드 스니펫은 비디오 자산의 예입니다. 렌디션 링크 배열이 포함되어 있습니다. 발췌한 `selection[5]`은(는) 대상 경험에서 비디오 썸네일의 자리 표시자로 사용할 수 있는 이미지 썸네일의 예입니다. 렌디션 배열의 `selection[5]`은(는) 비디오 플레이어용입니다. HTML 역할을 하며 iframe의 `src`(으)로 설정할 수 있습니다. 웹에 최적화된 비디오 전달인 적응형 비트율 스트리밍을 지원합니다.

  위의 예에서 비디오 플레이어 URL은 `https://delivery-pxxxxx-exxxxx-cmstg.adobeaemcloud.com/adobe/assets/urn:aaid:aem:2fdef732-a452-45a8-b58b-09df1a5173cd/play?accept-experimental=1`입니다.

### 맞춤형 필터 구성 {#configure-custom-filters-dynamic-media-open-api}

OpenAPI 기능이 있는 Dynamic Media용 에셋 선택기를 사용하면 사용자 지정 속성 및 이를 기반으로 필터를 구성할 수 있습니다. `filterSchema` 속성은 이러한 속성을 구성하는 데 사용됩니다. 사용자 지정은 필터를 구성할 수 있는 `metadata.<metadata bucket>.<property name>.`(으)로 노출될 수 있습니다.

* `metadata`은(는) 에셋의 정보입니다.
* `embedded`은(는) 구성에 사용되는 정적 매개 변수입니다.
* `<propertyname>`은(는) 구성 중인 필터 이름입니다.

구성의 경우 `jcr:content/metadata/` 수준에서 정의된 속성이 구성하려는 필터에 대해 `metadata.<metadata bucket>.<property name>.`(으)로 표시됩니다.

예를 들어 OpenAPI 기능이 있는 Dynamic Media용 자산 선택기에서 `asset jcr:content/metadata/client_name:market`의 속성은 필터 구성을 위해 `metadata.embedded.client_name:market`(으)로 변환됩니다.

이름을 가져오려면 1회 활동을 수행해야 합니다. 자산에 대한 검색 API를 호출하고 속성 이름(기본적으로 버킷)을 가져옵니다.

### OpenAPI 기능이 있는 Dynamic Media용 에셋 선택기 사용자 인터페이스 {#interface-dynamic-media-open-api}

Adobe의 마이크로 프론트엔드 에셋 선택기와 통합하면 Experience Manager 에셋 저장소에서 사용할 수 있는 승인된 모든 에셋의 에셋 전용 구조를 볼 수 있습니다.

![OpenAPI 기능 UI를 사용하는 Dynamic Media](assets/polaris-ui.png)

* **A**: [패널 숨기기/표시](#hide-show-panel)
* **B**: [Assets](#repository)
* **C**: [정렬](#sorting)
* **D**: [필터](#filters)
* **E**: [검색 창](#search-bar)
* **F**: [오름차순 또는 내림차순으로 정렬](#sorting)
* **G**: 선택 취소
* **시간**: 하나 또는 여러 자산을 선택하십시오.

>[!MORELIKETHIS]
>
>* [다양한 응용 프로그램과 자산 선택기 통합](/help/assets/integrate-asset-selector.md)
>* [자산 선택기 속성](/help/assets/asset-selector-properties.md)
>* [자산 선택기 사용자 지정](/help/assets/asset-selector-customization.md)
