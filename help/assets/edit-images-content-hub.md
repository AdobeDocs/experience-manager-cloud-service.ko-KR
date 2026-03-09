---
title: Adobe Express을 사용하여 Content Hub에서 이미지 편집
description: Adobe Express을 사용하여 Content Hub에서 이미지 편집
badgeSaas: label="AEM Assets" type="Positive" tooltip="AEM Assets에 적용됩니다)."
exl-id: c9777862-226c-4d39-87da-9c4a30437dc5
source-git-commit: a641933d1049cd07ee8935672c8ef357a5bbf18c
workflow-type: tm+mt
source-wordcount: '716'
ht-degree: 6%

---

# Content Hub에서 이미지 편집 {#edit-images-content-hub}

Content Hub을 사용하면 Adobe Express으로 새 콘텐츠를 만들 수 있습니다. 사용하기 쉬운 도구로 기존 콘텐츠를 편집하고, 템플릿과 브랜드 요소로 브랜드에 맞는 변형을 만들고, Adobe Firefly의 최신 생성형 AI 기능으로 새로운 콘텐츠를 만들 수 있습니다.

>[!VIDEO](https://video.tv.adobe.com/v/3435003/?learn=on){transcript=true}

## 사전 요구 사항 {#prereqs-edit-image-content-hub}

Adobe Express 및 [자산을 새 변형에 다시 혼합할 수 있는 권한이 있는 Content Hub 사용자](/help/assets/deploy-content-hub.md#onboard-content-hub-users-remix-assets)에 액세스할 수 있는 권한은 Content Hub을 사용하여 이미지를 편집할 수 있습니다.

>[!NOTE]
>
>[!DNL Adobe Express]을(를) 사용하여 PNG 및 JPG/JPEG 파일 형식의 이미지를 편집할 수 있습니다.

## [!DNL Adobe Express]를 사용하여 이미지 편집 {#edit-images-using-content-hub}

Content Hub을 사용하여 이미지를 편집하려면:

1. 편집해야 하는 이미지의 자산 카드에서 사용할 수 있는 **[!DNL Open in Adobe Express]**&#x200B;을(를) 클릭합니다. 또는 이미지를 클릭하여 세부 정보를 연 다음 [!DNL Adobe Express] 로고를 클릭합니다. 그런 다음 Adobe Express용 임베드된 편집기는 Content Hub을 종료하지 않고 로드됩니다.

   [!DNL Adobe Express] 기능을 사용하여 [이미지 크기 조정](https://helpx.adobe.com/express/using/resize-image.html), [배경색 제거 또는 변경](https://helpx.adobe.com/express/using/remove-background.html), [이미지 자르기](https://helpx.adobe.com/express/using/crop-image.html), 이미지를 AI에서 생성한 이미지 또는 텍스트와 결합하는 등 모든 이미지 편집 관련 작업을 수행할 수 있습니다.

1. 수정 작업을 수행하고 **[!UICONTROL 저장]**&#x200B;을 클릭하여 편집된 자산을 다음 형식 유형 중 하나로 저장합니다.

   * **[!UICONTROL PNG]**(좋은 품질의 이미지 형식으로 사용됨)
   * **[!UICONTROL JPG]**(작은 파일에 적합)
   * **[!UICONTROL PDF]**(문서에 적합)

   ![Adobe Express로 이미지 저장](assets/adobe-express-save-as.png)

1. **[!UICONTROL 다른 이름으로 저장]** 필드에 에셋의 이름을 지정하십시오.

1. **[!UICONTROL 캠페인 이름]** 필드를 사용하여 에셋의 캠페인 이름을 지정하십시오. 기존 이름을 사용하거나 새 이름을 만들 수 있습니다. Content Hub에서는 이름을 입력할 때 더 많은 옵션을 제공합니다. <!--You can define multiple Campaign names for your upload. While you are typing a name, either click anywhere else within the dialog box or press the `,` (Comma) key to register the name.-->

   Adobe에서는 업로드한 에셋에 대해 향상된 검색 경험을 만들 뿐만 아니라 나머지 필드에 값을 지정하는 것을 가장 좋습니다.

1. [선택 사항] **[!UICONTROL 키워드]**, **[!UICONTROL 채널]**, **[!UICONTROL 일정]** 및 **[!UICONTROL 지역]** 필드에 대한 값을 정의합니다. 키워드, 채널 및 위치별로 자산에 태그를 지정하고 그룹화하면 승인된 회사 콘텐츠를 사용하는 모든 사람이 이러한 자산을 찾아 체계적으로 관리할 수 있습니다.

1. 자산을 저장하려면 **[!UICONTROL 새 자산으로 저장]**&#x200B;을 클릭하세요.

또한 관리자는 Content Hub에 자산을 추가하는 동안 표시되는 캠페인 이름, 키워드, 채널 등과 같은 필수 및 선택적 필드를 구성할 수 있습니다. 자세한 내용은 [Content Hub 사용자 인터페이스 구성](configure-content-hub-ui-options.md#configure-upload-options-content-hub)을 참조하십시오.

## 자주 묻는 질문 {#faqs-edit-images-content-hub}

### AEM Assets Content Hub에서 이미지를 편집할 수 있는 사람은 누구입니까?

Adobe Express 및 AEM Assets Content Hub에 액세스할 수 있는 권한이 있고, 자산을 새 변형에 다시 혼합할 수 있는 권한이 있는 사용자는 Content Hub을 사용하여 이미지를 편집할 수 있습니다.

### AEM Assets Content Hub에서 Adobe Express을 사용하여 이미지를 편집하려면 어떻게 합니까?

이미지를 편집하려면 이미지의 에셋 카드에서 **Adobe Express에서 열기**&#x200B;를 클릭하거나 이미지의 세부 정보를 열고 Adobe Express 로고를 클릭합니다. 이렇게 하면 AEM Assets Content Hub 내에 임베드된 Adobe Express 편집기가 로드되므로 플랫폼을 종료하지 않고도 편집할 수 있습니다.

### Adobe Express은 AEM Assets Content Hub 내에서 어떤 편집 기능을 제공합니까?

Adobe Express은 여러 가지 기능 중에서 이미지 크기 조정, 배경색 제거 또는 변경, 이미지 자르기, AI 생성 이미지 또는 텍스트와 결합 등 다양한 이미지 편집 기능을 제공합니다.

### AEM Assets Content Hub에서와 같이 편집한 이미지를 저장할 수 있는 파일 형식은 무엇입니까?

편집한 이미지를 PNG(고품질), JPG(작은 파일에 적합) 또는 PDF(문서에 적합) 형식으로 저장할 수 있습니다.

### Content Hub에서 편집된 이미지를 저장할 때 어떤 필드를 입력해야 합니까?

편집된 이미지를 저장할 때 **다른 이름으로 저장** 필드에 자산 이름을 지정하고 **캠페인 이름** 필드에 캠페인 이름을 지정해야 합니다. 또한 Adobe에서는 검색 기능 및 구성을 향상시키기 위해 키워드, 채널, 시간대 및 지역 과 같은 추가 필드에 값을 지정할 것을 권장합니다.

### Content Hub에서 편집 내용을 새 자산으로 저장할 수 있습니까?

예. 편집한 후 **새 자산으로 저장**&#x200B;을 클릭하여 변경 내용을 Content Hub의 새 자산으로 저장할 수 있습니다.

### 관리자가 AEM Assets Content Hub에 자산을 업로드하는 동안 필드를 사용자 지정할 수 있습니까?

예. 관리자는 조직의 요구 사항에 맞게 AEM Assets Content Hub에 자산을 추가할 때 필수 또는 선택 필드인 캠페인 이름, 키워드 및 채널을 구성할 수 있습니다. 구성 UI의 **가져오기** 탭을 사용하여 필드를 구성합니다.




