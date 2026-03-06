---
title: ' [!DNL the Content Hub]에서 에셋 및 해당 속성 미리 보기'
description: ' [!DNL Content Hub]에서 에셋 및 속성을 미리 보는 방법에 대해 알아봅니다.'
role: User
exl-id: a85af980-4c51-4d30-9fad-afd16370e9db
source-git-commit: 44e9c1f016bfdad909d9e2aa1c9a301dcecd763b
workflow-type: tm+mt
source-wordcount: '971'
ht-degree: 7%

---

# Content Hub에서 에셋 및 해당 속성 미리 보기 {#asset-properties}

![메타데이터 배너 이미지](assets/metadata-banner-image.png)

[!DNL The Content Hub]을(를) 사용하면 효율적인 자산 배포에 중요한 자산 정보를 볼 수 있습니다. 자산에 사용할 수 있는 모든 데이터의 컬렉션입니다.

에셋 미리보기 및 해당 속성을 보면 에셋을 보다 세부적으로 분류할 수 있으며, 디지털 정보의 양이 증가할 때 유용합니다. 파일 이름, 미리보기 및 메모리 기준으로만 수백 개의 파일을 관리할 수 있습니다. 그러나 이 접근 방식은 관련된 사람의 수와 관리되는 자산의 수가 증가할 때 확장할 수 없습니다. 또한 에셋이 다음과 같이 되면 디지털 에셋의 가치가 증가합니다.

* 접근성 향상 - 시스템과 사용자가 쉽게 찾을 수 있습니다.
* 더욱 간편하게 작업할 수 있습니다. 자산의 시각적 개체 및 관련 정보에 대한 전체 정보를 활용하여 보다 빠르고 안전하게 작업할 수 있습니다.
* 완료 - 에셋이 더 많은 정보와 컨텍스트를 전달합니다.

## 사전 요구 사항 {#prerequisites}

[Content Hub 사용자](deploy-content-hub.md#onboard-content-hub-users)는 이 문서에 언급된 작업을 수행할 수 있습니다.

## 에셋 및 해당 속성 미리 보기 {#properties-ui}

자산을 사용, 공유 또는 다운로드하기 전에 더 자세히 볼 수 있습니다. 미리보기 기능을 사용하면 이미지뿐만 아니라 지원되는 몇 가지 에셋 유형도 볼 수 있습니다. 에셋을 볼 수 있을 뿐만 아니라 세부 정보를 보고 다른 작업을 수행할 수도 있습니다. 에셋의 정보를 보려면 에셋이나 에셋을 [검색](search-assets.md)한 다음 에셋을 클릭하여 해당 속성을 엽니다. 다음 그림은 자산 속성 페이지에서 사용할 수 있는 필드를 보여줍니다.

![자산 UI의 속성](assets/properties-ui.png)

* 자산의 **A:** 제목
* **B:** 확대 또는 축소를 통해 더 가깝게 자산을 확대 또는 미리 보는 비율입니다.
* **C:** 이전에 선택한 비율로 확대/축소를 실행 취소합니다
* **일:** 이전 또는 다음 에셋으로 진행
* **E:** Assets 수
* **상태:** 에셋 다운로드
* **G:** [!DNL Adobe Express]을(를) 사용하여 에셋 편집
* **시간:** 자산의 정보를 축소하거나 미리 봅니다.
* **I:** 자산 공유
* **J:** 자산을 [!DNL Collection]에 추가
* **K:** 미리 보기 화면 닫기
* **L:** 제목, 형식, 크기, 해상도, 태그, 색상 태그 및 스마트 태그를 포함하는 에셋 정보.

## 지원되는 자산 형식 {#supported-formats}

[!DNL Content Hub]은(는) 기본 [!DNL Assets] 리포지토리가 지원하는 모든 자산 유형과 형식을 지원합니다. 다음 표에는 자산을 시각적으로 미리 볼 수 있도록 추가 지원을 제공하는 [!DNL the Content Hub]의 주요 파일 형식이 나와 있습니다.

<table> 
    <tbody>
     <tr>
      <th><strong>파일 유형</strong></th>
      <th><strong>지원되는 형식</strong></th>
     </tr>
     <tr>
        <td rowspan="3"> 이미지 </td>
    </tr>
    </tr>
    <tr>
        <td>[!UICONTROL JPEG]</td>
    </tr>
    <tr>
        <td>[!UICONTROL PNG]</td>
    </tr>
    <tr>
        <td rowspan="4"> 비디오 </td>
    </tr>
    </tr>
    <tr>
        <td>[!UICONTROL Quicktime]</td>
    </tr>
    <tr>
        <td>[!UICONTROL MP4]</td>
    </tr>
    <tr>
        <td>[!UICONTROL MPEG]</td>
    </tr>
    <tr>
        <td rowspan="4"> 문서 </td>
    </tr>
    </tr>
    <tr>
        <td>[!UICONTROL txt] (일반)</td>
    </tr>
    <tr>
        <td>[!UICONTROL Doc/Docx]</td>
    </tr>
    <tr>
        <td>[!UICONTROL XML]</td>
    </tr>
    <tr>
        <td rowspan="2"> 인쇄 미디어 </td>
    </tr>
    </tr>
    <tr>
        <td>[!UICONTROL PDF]</td>
    </tr>
    </tbody>
</table>

### 파생 속성 {#derived-properties}

[!DNL Content Hub]에 표시된 자산에 대한 일부 속성은 자산이 [!DNL Assets]에 업로드된 다음 [!DNL Content Hub]에서 사용할 수 있도록 승인될 때 자동으로 파생되거나 생성됩니다. 다음은 일부 항목의 목록입니다.

* **크기:** 크기는 기본 저장소에 저장된 자산 바이너리의 크기를 나타냅니다.

<!--* **Tags:** Tags help you categorize assets that can be browsed and searched more efficiently. Tagging helps in propagating the appropriate taxonomy to other users and workflows. -->

* **스마트 태그:** [!DNL The Content Hub]은(는) Adobe AI의 스마트 컨텐츠 서비스를 사용하여 태그 기반 구조의 인식 알고리즘을 사용하여 자산을 교육합니다. 이 콘텐츠 인텔리전스는 다른 자산 세트에 관련 태그를 적용하는 데 사용됩니다. 스마트 태그는 관련 에셋을 빠르게 찾을 수 있도록 지원하여 프로젝트의 콘텐츠 속도를 높입니다. 스마트 태그는 이미지에 포함되지 않은 에셋 정보의 예입니다. [!DNL Experience Manager Assets]은(는) 기본적으로 스마트 태그를 자산에 자동으로 적용합니다.

* **색상 태그:** [색상 태그](#https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/manage/color-tag-images.html?lang=ko)를 사용하면 Adobe의 AI 기능을 사용하여 에셋에서 자동으로 식별되는 색상을 사용하여 에셋을 인식할 수 있습니다.

* 업로드 날짜

* 다음에 의해 업로드됨

* 마지막 수정일

* 마지막 수정자

Content Hub에 에셋을 추가하는 동안 지정된 속성도 있습니다. 자세한 내용은 [Content Hub에 브랜드 승인 에셋 추가](upload-brand-approved-assets.md)를 참조하십시오. 이러한 속성은 에셋 속성 페이지에도 표시됩니다.

또한 관리자는 각 에셋에 대해 표시되는 속성을 구성할 수 있습니다.

* 에셋 미리 보기 UI에서: [Content Hub 사용자 인터페이스 구성](configure-content-hub-ui-options.md#configure-asset-details-content-hub)을 참조하십시오.
* 검색 결과 또는 컬렉션의 자산 카드에서: [Content Hub 사용자 인터페이스 구성](configure-content-hub-ui-options.md#asset-card)을 참조하세요.

<!--

### Date range {#date-range} 

The date range allows you to select dates you want to see the assets. You can customize date range by choosing the start and end dates. 

-->

## 자주 묻는 질문 {#faqs-asset-properties-content-hub}

### AEM Assets Content Hub에서 에셋과 에셋의 속성을 미리 보는 이유는 무엇입니까?

Content Hub에서 에셋 및 에셋의 속성을 미리 보면 에셋 세부 사항을 면밀하게 볼 수 있으며, 이는 효율적인 에셋 분배 및 관리에 필수적입니다. 디지털 정보가 증가함에 따라 파일 이름과 썸네일에 의존하는 것만으로는 확장성이 떨어집니다. 세부 속성을 보면 에셋을 분류하고, 보다 쉽게 액세스하고, 보다 쉽게 작업하고, 모든 사용자가 정보를 완료할 수 있습니다.

### AEM Assets Content Hub에서 에셋의 속성을 보고 상호 작용하려면 어떻게 해야 합니까?

Content Hub에서 에셋의 속성을 보려면 에셋으로 이동하거나 검색한 다음 해당 에셋을 클릭하여 속성 페이지를 엽니다. 여기에서 미리보기를 확대 또는 축소하거나, 확대/축소를 실행 취소하거나, 이전 또는 다음 에셋으로 이동하거나, 에셋을 다운로드하거나, Adobe Express으로 편집하거나, 컬렉션에 추가하거나, 미리보기를 닫을 수 있습니다. 속성 페이지에는 제목, 형식, 크기, 해상도, 태그, 색상 태그 및 스마트 태그와 같은 자세한 정보가 표시됩니다.

### AEM Assets Content Hub에서 파생된 속성은 무엇이며 어떻게 생성됩니까?

Content Hub의 파생 속성은 에셋을 업로드하고 승인할 때 자동으로 생성됩니다. 에셋의 크기, 스마트 태그 및 색상 태그를 예로 들 수 있습니다. 스마트 태그는 Adobe AI의 스마트 컨텐츠 서비스를 사용하여 관련 태그를 자동으로 인식 및 적용하여 자산 검색 기능을 향상시킵니다. 색상 태그도 AI를 이용해 자동으로 식별돼 사용자가 자신의 돋보이는 색상으로 에셋을 인식할 수 있도록 돕는다.

### 관리자가 Content Hub에 표시되는 에셋 속성을 사용자 정의할 수 있습니까?

예. 관리자는 Content Hub에서 각 에셋에 대해 표시되는 속성을 구성할 수 있습니다. 이 작업은 검색 결과 또는 컬렉션의 에셋 미리보기 사용자 인터페이스와 에셋 카드 모두에 대해 수행할 수 있으므로 사용자가 요구 사항에 따라 가장 관련성이 높은 정보를 볼 수 있습니다.

### 에셋 미리보기에 지원되는 파일 형식은 무엇입니까?

지원되는 파일 형식에는 이미지의 경우 JPEG 및 PNG, 비디오의 경우 Quicktime, MP4 및 MPEG, 문서의 경우 TXT, DOC/DOCX 및 XML, 인쇄 미디어의 경우 PDF이 포함됩니다.


