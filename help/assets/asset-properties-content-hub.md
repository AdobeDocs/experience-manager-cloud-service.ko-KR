---
title: ' [!DNL the Content Hub]의 자산 속성'
description: ' [!DNL Content Hub]에서 자산 속성을 보고 관리하는 방법을 알아봅니다.'
role: User
exl-id: a85af980-4c51-4d30-9fad-afd16370e9db
source-git-commit: e3fd0fe2ee5bad2863812ede2a294dd63864f3e2
workflow-type: tm+mt
source-wordcount: '617'
ht-degree: 9%

---

# Content Hub에서 에셋 속성 관리 {#asset-properties}

| [모범 사례 검색](/help/assets/search-best-practices.md) | [메타데이터 모범 사례](/help/assets/metadata-best-practices.md) | [Content Hub](/help/assets/product-overview.md) | [OpenAPI 기능이 있는 Dynamic Media](/help/assets/dynamic-media-open-apis-overview.md) | [AEM Assets 개발자 설명서](https://developer.adobe.com/experience-cloud/experience-manager-apis/) |
| ------------- | --------------------------- |---------|----|-----|

![메타데이터 배너 이미지](assets/metadata-banner-image.png)

[!DNL The Content Hub]을(를) 사용하면 효율적인 자산 배포에 중요한 자산 정보를 볼 수 있습니다. 자산에 사용할 수 있는 모든 데이터의 컬렉션입니다.

에셋 속성 보기를 통해 에셋을 보다 세부적으로 분류할 수 있으며, 디지털 정보의 양이 증가할 때 유용합니다. 파일 이름, 미리보기 및 메모리 기준으로만 수백 개의 파일을 관리할 수 있습니다. 그러나 이 접근 방식은 관련된 사람의 수와 관리되는 자산의 수가 증가할 때 확장할 수 없습니다. 또한 에셋이 다음과 같이 되면 디지털 에셋의 가치가 증가합니다.

* 접근성 향상 - 시스템과 사용자가 쉽게 찾을 수 있습니다.
* 관리 용이성 - 동일한 속성 세트를 가진 에셋을 쉽게 찾고 변경 사항을 적용할 수 있습니다.
* 완료 - 에셋이 더 많은 정보와 컨텍스트를 전달합니다.

## 사전 요구 사항 {#prerequisites}

[Content Hub 사용자](deploy-content-hub.md#onboard-content-hub-users)는 이 문서에 언급된 작업을 수행할 수 있습니다.

## 에셋의 속성 보기 {#properties-ui}

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

## 지원되는 형식 {#supported-formats}

다음 표에서는 [!DNL the Content Hub]에서 지원되는 파일 형식을 보여 줍니다.

<table> 
    <tbody>
     <tr>
      <th><strong>파일 유형</strong></th>
      <th><strong>지원되는 형식</strong></th>
     </tr>
     <tr>
      <td>이미지</td>
      <td>
        <ul>
            <li>[!UICONTROL JPEG]</li> 
            <li>[!UICONTROL PNG]</li> 
            <li>[!UICONTROL SVG]</li>
        </ul>
      </td>
     </tr>
     <tr>
      <td>비디오</td>
      <td>
        <ul>
            <li>[!UICONTROL Quicktime]</li>  
            <li>[!UICONTROL MP4]</li> 
        </ul>
      </td>
     </tr>
      <tr>
      <td>문서</td>
      <td>
        <ul>
            <li>[!UICONTROL txt] (일반)</li>  
            <li>[!UICONTROL Doc/Docx]</li> 
            <li>[!UICONTROL XML]</li>
        </ul>
      </td>
     </tr>
     <tr>
      <td>인쇄 미디어</td>
      <td>
        <ul>
            <li>[!UICONTROL PDF]</li>  
        </ul>
      </td>
     </tr>  
    </tbody>
   </table>

### 에셋 업로드 후 파생된 속성 {#derived-properties}

에셋을 업로드하면 Content Hub에서 자동으로 생성되는 일부 속성을 파생합니다. 다음은 일부 항목의 목록입니다.

* **크기:** 크기는 해당 차원에 따른 에셋의 논리적 값을 보여 줍니다. 저장소에서 에셋이 사용 중인 공간을 명확하게 합니다. [!DNL The Content Hub]은(는) 최대 2GB의 자산을 지원합니다.

<!--* **Tags:** Tags help you categorize assets that can be browsed and searched more efficiently. Tagging helps in propagating the appropriate taxonomy to other users and workflows. -->

* **스마트 태그:** [!DNL The Content Hub]은(는) Adobe Sensei의 스마트 컨텐츠 서비스를 사용하여 태그 기반 구조의 인식 알고리즘을 사용하여 자산을 교육합니다. 그런 다음 이 콘텐츠 인텔리전스를 사용하여 다른 에셋 세트에 관련 태그를 적용합니다. 스마트 태그는 관련 에셋을 빠르게 찾을 수 있도록 지원하여 프로젝트의 콘텐츠 속도를 높입니다. 스마트 태그는 이미지에 포함되지 않은 에셋 정보의 예입니다. [!DNL The Content Hub]은(는) 기본적으로 스마트 태그를 자산에 자동으로 적용합니다.

* **색상 태그:** [색상 태그](#https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/manage/color-tag-images.html?lang=en)를 사용하면 Adobe의 Sensei AI 기능을 사용하여 에셋에서 자동으로 식별되는 색상을 사용하여 에셋을 인식할 수 있습니다.

* 업로드 날짜

* 다음에 의해 업로드됨

* 마지막 수정일

* 마지막 수정자

Content Hub에 에셋을 추가하는 동안 지정된 속성도 있습니다. 자세한 내용은 [Content Hub에 브랜드 승인 에셋 추가](upload-brand-approved-assets.md)를 참조하십시오. 이러한 속성은 에셋 속성 페이지에도 표시됩니다.

또한 관리자는 각 에셋에 대해 표시되는 속성을 구성할 수 있습니다. 자세한 내용은 [Content Hub 사용자 인터페이스 구성](configure-content-hub-ui-options.md#configure-asset-details-content-hub)을 참조하십시오.

<!--

### Date range {#date-range} 

The date range allows you to select dates you want to see the assets. You can customize date range by choosing the start and end dates. 

-->
