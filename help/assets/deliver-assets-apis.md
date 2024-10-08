---
title: 게재 API
description: 배달 API를 사용하는 방법을 알아봅니다.
role: User
exl-id: 806ca38f-2323-4335-bfd8-a6c79f6f15fb
source-git-commit: e3fd0fe2ee5bad2863812ede2a294dd63864f3e2
workflow-type: tm+mt
source-wordcount: '555'
ht-degree: 1%

---

# 배달 API {#delivery-apis}

| [모범 사례 검색](/help/assets/search-best-practices.md) | [메타데이터 모범 사례](/help/assets/metadata-best-practices.md) | [Content Hub](/help/assets/product-overview.md) | [OpenAPI 기능이 있는 Dynamic Media](/help/assets/dynamic-media-open-apis-overview.md) | [AEM Assets 개발자 설명서](https://developer.adobe.com/experience-cloud/experience-manager-apis/) |
| ------------- | --------------------------- |---------|----|-----|

Experience Manager 에셋 저장소에서 사용할 수 있는 [승인된 에셋](approve-assets.md)은 모두 [검색](search-assets-api.md)한 다음 배달 URL을 사용하여 통합 다운스트림 응용 프로그램으로 배달할 수 있습니다.

버전 업데이트 및 메타데이터 수정 사항을 포함하여 DAM의 승인된 에셋에 대한 모든 변경 사항은 게재 URL에 자동으로 반영됩니다. CDN을 통한 에셋 전달에 대해 구성된 10분의 짧은 TTL(Time-to-Live) 값을 사용하면 10분 이내에 모든 작성 및 게시된 인터페이스에 업데이트가 표시됩니다.

다음 이미지는 사용 가능한 게재 URL을 보여 줍니다.

![배달 API](assets/delivery-url.png)

다음 표는 사용 가능한 다양한 배달 API의 사용을 보여줍니다.

| 배달 API | 설명 |
|---|---|
| [요청된 출력 형식의 자산에 대한 웹에 최적화된 이진 표현](https://adobe-aem-assets-delivery.redoc.ly/#operation/getAssetSeoFormat) | 요청에서 보낸 에셋 ID를 기반으로 요청된 출력 형식으로 에셋의 웹에 최적화된 이진 표현을 반환합니다. 또한 폭, 높이, 회전, 뒤집기, 품질, 자르기, 형식 및 [스마트 자르기](/help/assets/dynamic-media/image-profiles.md)와 같은 다양한 이미지 수정자를 정의할 수 있습니다. 지원되는 형식 및 이미지 수정자에 대해서는 [API 세부 정보](https://adobe-aem-assets-delivery.redoc.ly/#operation/getAssetSeoFormat)를 참조하십시오.<br>Adobe은 모든 이미지 형식 유형에 이 API를 사용할 것을 권장합니다. |
| [에셋의 웹에 최적화된 이진 표시](https://adobe-aem-assets-delivery.redoc.ly/#operation/getAsset) | 응답에서 반환된 에셋의 웹에 최적화된 이진 표현에 기본값을 적용하는 편의 API입니다. 기본값에는 표준 JPEG/WEBP 형식, 품질 => 65, 너비 => 1024가 포함됩니다. |
| [자산의 원본 업로드된 이진 파일](https://adobe-aem-assets-delivery.redoc.ly/#operation/getAssetOriginal) | 에셋에 대해 원래 업로드된 바이너리를 반환합니다. Adobe은 문서 형식 유형 및 SVG 이미지에 이 API를 사용하는 것을 권장합니다. |
| [AEM Assets 작성 환경에서 사용할 수 있는 자산의 미리 생성된 렌디션](https://adobe-aem-assets-delivery.redoc.ly/#operation/getAssetRendition) | 요청에서 전송된 자산 ID 및 렌디션 이름을 기반으로 AEM Assets 작성 환경에서 사용할 수 있는 자산 렌디션의 비트스트림을 반환합니다. |
| [자산 메타데이터](https://adobe-aem-assets-delivery.redoc.ly/#operation/getAssetMetadata) | title, description, CreateDate, ModifyDate 등과 같이 에셋과 연결된 속성을 반환합니다. |
| 비디오 자산에 대한 [플레이어 컨테이너](https://adobe-aem-assets-delivery.redoc.ly/#operation/videoPlayerDelivery) | 비디오 자산에 대한 플레이어 컨테이너를 반환합니다. 플레이어를 iframe HTML 요소에 임베드하고 비디오를 재생할 수 있습니다. |
| [선택한 출력 형식의 재생 매니페스트](https://adobe-aem-assets-delivery.redoc.ly/#operation/videoManifestDelivery) | 지정된 비디오 자산에 대한 재생 매니페스트 파일을 선택한 출력 형식으로 반환합니다. 재생 매니페스트 파일을 가져와서 비디오를 재생하려면 HLS 또는 DASH 프로토콜을 통해 적응형 스트리밍이 가능한 사용자 지정 플레이어를 빌드해야 합니다. |

## 게재 API 엔드포인트 {#delivery-apis-endpoint}

API 엔드포인트는 각 게재 API에 따라 다릅니다. 예를 들어 `Web-optimized binary representation of the asset in the requested output format` API의 API 끝점은 다음과 같습니다.
`https://delivery-pXXXX-eYYYY.adobeaemcloud.com/adobe/assets/{assetId}/as/{seoName}.{format}`

게재 도메인은 Experience Manager 작성자 환경의 도메인과 구조가 유사합니다. 유일한 차이점은 용어 `author`을(를) `delivery`(으)로 바꾸는 것입니다.

`pXXXX`은(는) 프로그램 ID를 참조합니다.

`eYYYY`이(가) 환경 ID를 참조합니다.

자세한 내용은 [API 세부 정보](https://adobe-aem-assets-delivery.redoc.ly/#tag/Assets)를 참조하십시오.

## 배달 API 요청 메서드 {#delivery-api-request-method}

GET

## 배달 API 헤더 {#deliver-assets-api-header}

게재 API 헤더에서 헤더를 정의하는 동안 다음 세부 정보를 제공해야 합니다.

```java
headers: {
      'If-None-Match': 'string',
      Authorization: 'Bearer <YOUR_JWT_HERE>'
    }
```

배달 API를 호출하려면 제한된 자산을 배달하려면 `Authorization` 세부 정보에 IMS 토큰이 필요합니다. IMS 토큰을 기술 계정에서 가져옵니다. 새 기술 계정을 만들려면 [AEM as a Cloud Service 자격 증명 가져오기](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/generating-access-tokens-for-server-side-apis.html?lang=en#fetch-the-aem-as-a-cloud-service-credentials)를 참조하십시오. IMS 토큰을 생성하고 배달 API 요청 헤더에서 적절하게 사용하려면 [액세스 토큰 생성](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/generating-access-tokens-for-server-side-apis.html?lang=en#generating-the-access-token)을 참조하십시오.


요청 샘플, 응답 샘플 및 응답 코드를 보려면 [배달 API](https://adobe-aem-assets-delivery.redoc.ly/#operation/getAssetSeoFormat)를 참조하십시오.
