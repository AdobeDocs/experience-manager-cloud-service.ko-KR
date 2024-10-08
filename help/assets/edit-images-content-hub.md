---
title: Adobe Express을 사용하여 Content Hub에서 이미지 편집
description: Adobe Express을 사용하여 Content Hub에서 이미지 편집
exl-id: c9777862-226c-4d39-87da-9c4a30437dc5
source-git-commit: e3fd0fe2ee5bad2863812ede2a294dd63864f3e2
workflow-type: tm+mt
source-wordcount: '408'
ht-degree: 2%

---

# Content Hub에서 이미지 편집 {#edit-images-content-hub}

| [모범 사례 검색](/help/assets/search-best-practices.md) | [메타데이터 모범 사례](/help/assets/metadata-best-practices.md) | [Content Hub](/help/assets/product-overview.md) | [OpenAPI 기능이 있는 Dynamic Media](/help/assets/dynamic-media-open-apis-overview.md) | [AEM Assets 개발자 설명서](https://developer.adobe.com/experience-cloud/experience-manager-apis/) |
| ------------- | --------------------------- |---------|----|-----|

![Adobe Express을 사용하여 Content Hub에서 이미지 편집](assets/edit-images-content-hub.png)

Content Hub을 사용하면 Adobe Express으로 새 콘텐츠를 만들 수 있습니다. 사용하기 쉬운 도구로 기존 콘텐츠를 편집하고, 템플릿 및 브랜드 요소를 사용하여 브랜드 내 변형을 작성하고, Adobe Firefly의 최신 GenAI 기능을 사용하여 새 콘텐츠를 만들 수 있습니다.

## 사전 요구 사항 {#prereqs-edit-image-content-hub}

Adobe Express 및 [자산을 새 변형에 다시 혼합할 수 있는 권한이 있는 Content Hub 사용자](/help/assets/deploy-content-hub.md#onboard-content-hub-users-remix-assets)에 액세스할 수 있는 권한은 Content Hub을 사용하여 이미지를 편집할 수 있습니다.

>[!NOTE]
>
>[!DNL Adobe Express]을(를) 사용하여 PNG 및 JPG/JPEG 파일 형식의 이미지를 편집할 수 있습니다.

## [!DNL Adobe Express]를 사용하여 이미지 편집 {#edit-images-using-content-hub}

Content Hub을 사용하여 이미지를 편집하려면:

1. 편집해야 하는 이미지의 자산 카드에서 사용할 수 있는 **[!DNL Open in Adobe Express]**&#x200B;을(를) 클릭합니다. 또는 이미지를 클릭하여 세부 정보를 연 다음 [!DNL Adobe Express] 로고를 클릭합니다. 그러면 Content Hub을 종료하지 않고 Adobe Express을 위한 임베드된 편집기가 로드됩니다.

   [!DNL Adobe Express] 기능을 사용하여 [이미지 크기 조정](https://helpx.adobe.com/express/using/resize-image.html), [배경색 제거 또는 변경](https://helpx.adobe.com/express/using/remove-background.html), [이미지 자르기](https://helpx.adobe.com/express/using/crop-image.html), 이미지를 AI에서 생성한 이미지 또는 텍스트와 결합하는 등 모든 이미지 편집 관련 작업을 수행할 수 있습니다.

1. 수정 작업을 수행하고 **[!UICONTROL 저장]**&#x200B;을 클릭하여 편집된 자산을 다음 형식 유형 중 하나로 저장합니다.

   * **[!UICONTROL PNG]**(좋은 품질의 이미지 형식으로 사용됨)
   * **[!UICONTROL JPG]**(작은 파일에 적합)
   * **[!UICONTROL PDF]**(문서에 적합)

   ![Adobe Express로 이미지 저장](assets/adobe-express-save-as.png)

1. **[!UICONTROL 다른 이름으로 저장]** 필드에 에셋의 이름을 지정하십시오.

1. **[!UICONTROL 캠페인 이름]** 필드를 사용하여 에셋의 캠페인 이름을 지정하십시오. 기존 이름을 사용하거나 새 이름을 만들 수 있습니다. Content Hub에서는 이름을 입력할 때 더 많은 옵션을 제공합니다. <!--You can define multiple Campaign names for your upload. While you are typing a name, either click anywhere else within the dialog box or press the `,` (Comma) key to register the name.-->

   업로드한 에셋에 대해 향상된 Adobe 경험을 만들 뿐만 아니라 나머지 필드에 값을 지정하는 것이 좋습니다.

1. [선택 사항] **[!UICONTROL 키워드]**, **[!UICONTROL 채널]**, **[!UICONTROL 일정]** 및 **[!UICONTROL 지역]** 필드에 대한 값을 정의합니다. 키워드, 채널 및 위치별로 자산에 태그를 지정하고 그룹화하면 승인된 회사 콘텐츠를 사용하는 모든 사람이 이러한 자산을 찾아 체계적으로 관리할 수 있습니다.

1. 자산을 저장하려면 **[!UICONTROL 새 자산으로 저장]**&#x200B;을 클릭하세요.

또한 관리자는 Content Hub에 자산을 추가하는 동안 표시되는 캠페인 이름, 키워드, 채널 등과 같은 필수 및 선택적 필드를 구성할 수 있습니다. 자세한 내용은 [Content Hub 사용자 인터페이스 구성](configure-content-hub-ui-options.md#configure-upload-options-content-hub)을 참조하십시오.
