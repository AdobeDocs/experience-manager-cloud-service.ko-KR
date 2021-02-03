---
title: AI에서 생성된 태그를 사용하여 에셋에 자동 태그 지정
description: ' [!DNL Adobe Sensei] 서비스를 사용하여 문맥 및 설명 비즈니스 태그를 적용하는 인공적인 지능형 서비스를 사용하여 자산에 태그를 지정합니다.'
contentOwner: AG
translation-type: tm+mt
source-git-commit: 7af525ed1255fb4c4574c65dc855e0df5f1da402
workflow-type: tm+mt
source-wordcount: '2557'
ht-degree: 1%

---


# 자산에 스마트 태그를 추가하여 빠른 검색 {#smart-tag-assets-for-faster-search}

디지털 자산을 다루는 조직은 자산 메타데이터에 분류 제어 용어를 점점 더 사용하고 있습니다. 기본적으로 직원, 파트너 및 고객이 디지털 자산을 참조하고 검색하는 데 일반적으로 사용하는 키워드 목록이 포함되어 있습니다. 분류법이 제어되는 어휘로 자산에 태그를 지정하면 검색에서 자산을 쉽게 식별하고 검색할 수 있습니다.

자연어 어휘와 비교하여 비즈니스 분류 방식을 기반으로 태그를 지정하면 자산을 회사의 비즈니스에 맞게 정렬하고 가장 관련성이 높은 자산이 검색에 표시되는지 확인할 수 있습니다. 예를 들어 자동차 제조업체는 자동차 이미지에 모델 이름을 태그로 지정할 수 있으므로 판촉 캠페인을 디자인하기 위해 검색할 때 관련 이미지만 표시됩니다.

백그라운드에서 스마트 태그는 태그 구조 및 비즈니스 분류법에 대한 이미지 인식 알고리즘을 교육하기 위해 [Adobe Sensei](https://www.adobe.com/kr/sensei/experience-cloud-artificial-intelligence.html)의 인공적인 지능형 프레임워크를 사용합니다. 그런 다음 이 컨텐츠 인텔리전스를 사용하여 다른 자산 세트에 관련 태그를 적용합니다.

<!-- TBD: Create a flowchart for how training works in CS.
![flowchart](assets/flowchart.gif) 
-->

## 지원되는 자산 유형 {#smart-tags-supported-file-formats}

스마트 태그는 JPG 및 PNG 형식의 변환을 생성하는 지원되는 파일 유형에만 적용됩니다. 이 기능은 다음 유형의 자산에 대해 지원됩니다.

| 이미지(MIME 유형) | 텍스트 기반 에셋(파일 형식) | 비디오 에셋(파일 포맷 및 코덱스) |
|----|-----|------|
| image/jpeg | TXT | MP4(H264/AVC) |
| image/tiff | RTF | MKV(H264/AVC) |
| image/png | DITA | MOV(H264/AVC, 모션 JPEG) |
| image/bmp | XML | AVI(indeo4) |
| image/gif | JSON | FLV(H264/AVC, vp6f) |
| image/pjpeg | DOC | WMV(WMV2) |
| image/x-portable-anymap | DOCX |  |
| image/x-portable-bitmap | PDF |  |
| image/x-portable-graymap | CSV |  |
| image/x-portable-pixmap | PPT |  |
| image/x-rgb | PPTX |  |
| image/x-xbitmap | VTT |  |
| image/x-xpimap | SRT |  |
| image/x-icon |  |  |
| 이미지/photoshop |  |  |
| image/x-photoshop |  |  |
| 이미지/psd |  |  |
| image/vnd.adobe.photoshop |  |  |

[!DNL Experience Manager] 기본적으로 스마트 태그를 텍스트 기반 자산과 비디오에 자동으로 추가합니다. 이미지에 스마트 태그를 자동으로 추가하려면 다음 작업을 완료하십시오.

* [ [!DNL Adobe Experience Manager] Adobe 개발자 콘솔과 통합](#integrate-aem-with-aio).
* [태그 모델 및 지침을 이해합니다](#understand-tag-models-guidelines).
* [모델](#train-model) 트레이닝
* [디지털 에셋에 태그를 지정할 수 있습니다](#tag-assets).
* [태그 및 검색을 관리합니다](#manage-smart-tags-and-searches).

>[!TIP]
>
>스마트 태그는 [!DNL Adobe Experience Manager Assets] 고객에만 적용됩니다. 스마트 태그는 [!DNL Experience Manager]의 추가 기능으로 구매할 수 있습니다.

<!-- TBD: Is there a link to buy SCS or initiate a sales call. How are AIO services sold? Provide a CTA here to buy or contacts Sales team. -->

## [!DNL Experience Manager]을(를) Adobe 개발자 콘솔 {#integrate-aem-with-aio}과 통합

>[!IMPORTANT]
>
>새 [!DNL Experience Manager Assets] 배포는 기본적으로 [!DNL Adobe Developer Console]과 통합됩니다. 이렇게 하면 스마트 태그 기능을 보다 신속하게 구성할 수 있습니다. 이전 배포에서는 관리자가 수동으로 [스마트 태그 통합](/help/assets/smart-tags-configuration.md#aio-integration)을 구성할 수 있습니다.

[!DNL Adobe Developer Console]을(를) 사용하여 스마트 태그와 [!DNL Adobe Experience Manager]을 통합할 수 있습니다. 이 구성을 사용하여 [!DNL Experience Manager] 내에서 스마트 태그 서비스에 액세스합니다. 스마트 태그 구성 작업에 대해서는 [자산](smart-tags-configuration.md)의 스마트 태그 지정을 위한 Experience Manager 구성을 참조하십시오. 백엔드 시, [!DNL Experience Manager] 서버는 스마트 태그 서비스로 요청을 전달하기 전에 Adobe 개발자 콘솔 게이트웨이로 서비스 자격 증명을 인증합니다.

## 태그 모델 및 지침 이해 {#understand-tag-models-guidelines}

태그 모델은 이미지의 시각적 측면을 기준으로 하는 관련 태그 그룹입니다. 예를 들어 shoes 컬렉션에는 다른 태그가 있을 수 있지만 모든 태그가 shoes와 관련되어 있고 동일한 태그 모델에 속할 수 있습니다. 태그는 이미지의 뚜렷한 시각적 측면만 연결할 수 있습니다. 교육 모델의 내용 표현을 [!DNL Experience Manager]에서 이해하려면 교육 모델을 수동으로 추가한 태그 그룹과 각 태그에 대한 예제 이미지로 구성된 최상위 엔티티로 시각화합니다. 각 태그는 이미지에 단독으로 적용할 수 있습니다.

현실적으로 처리할 수 없는 태그는 다음과 관련되어 있습니다.

* 제품 출시 연도 또는 계절과 같이 비시각적이고 추상적인 측면을 이미지에 의해 분위기 또는 감정을 유발합니다.
* 제품에 임베드되어 있는 콜라어 및 무색 셔츠나 작은 제품 로고 같은 제품의 시각적 차이를 세밀하게 조정할 수 있습니다.

태그 모델을 만들고 서비스를 교육하기 전에 비즈니스 컨텍스트에서 이미지의 개체를 가장 잘 설명하는 고유한 태그 집합을 식별합니다. 선별된 세트의 자산이 [교육 지침](#training-guidelines)에 부합하는지 확인합니다.

### 교육 지침 {#training-guidelines}

교육 세트의 이미지는 다음 지침을 따라야 합니다.

**수량 및 크기:** 최소 10개 이미지 및 태그당 최대 50개 이미지.

**일관성**:태그의 이미지는 시각적으로 비슷해야 합니다. 동일한 시각적 측면(예: 이미지의 동일한 개체 유형)에 대한 태그를 단일 태그 모델에 추가하는 것이 가장 좋습니다. 예를 들어 이러한 모든 이미지는 시각적으로 유사하지 않기 때문에 `my-party`(교육용)으로 태그를 지정하는 것은 좋지 않습니다.

![트레이닝 지침을 예시할 수 있는 실례가 되는 이미지](assets/do-not-localize/coherence.png)

**적용 범위**:훈련 중에는 이미지가 충분히 다양해야 한다. AEM이 올바른 것에 초점을 맞추도록 몇 가지 하지만 상당히 다양한 예를 제공하는 것이 그 생각입니다. 시각적으로 다른 이미지에 동일한 태그를 적용하는 경우 각 종류의 최소 5개의 예를 포함합니다. 예를 들어 태그 *model-down-pose*&#x200B;에 대해, 태그 지정 중에 서비스에서 유사한 이미지를 보다 정확하게 식별할 수 있도록 아래 강조 표시된 이미지와 유사한 더 많은 교육 이미지를 포함시킵니다.

![트레이닝 지침을 예시할 수 있는 실례가 되는 이미지](assets/do-not-localize/coverage_1.png)

**방해/방해**:이 서비스는 집중을 덜 하는 이미지(두드러진 배경, 주제와 관련된 물건이나 사람과 같은 관련없는 배경)에서 더 잘 훈련한다. 예를 들어, 태그 *캐주얼-shoe*&#x200B;의 경우 두 번째 이미지는 올바른 교육 후보자가 아닙니다.

![트레이닝 지침을 예시할 수 있는 실례가 되는 이미지](assets/do-not-localize/distraction.png)

**완전성: 이미지가 둘 이상의 태그에** 적합하면 교육을 위한 이미지를 포함하기 전에 해당 태그를 모두 추가합니다. 예를 들어, *Raincoat* 및 *model-side-view*&#x200B;와 같은 태그의 경우 교육을 위해 해당 에셋에 태그를 모두 추가합니다.

![트레이닝 지침을 예시할 수 있는 실례가 되는 이미지](assets/do-not-localize/completeness.png)

**태그 수**:Adobe에서는 각 태그에 대해 최소한 2개의 서로 다른 태그와 최소 10개의 서로 다른 이미지를 사용하여 모델을 교육할 것을 권장합니다. 단일 태그 모델에서 50개 이상의 태그를 추가하지 마십시오.

**예** 수:각 태그에 대해 최소 10개의 예를 추가합니다. 하지만, Adobe은 약 30개의 예를 추천합니다. 태그당 최대 50개의 예제가 지원됩니다.

**잘못된 양조 및 충돌** 방지:Adobe에서는 단일 시각적 측면용으로 단일 태그 모델을 만드는 것이 좋습니다. 모델 간에 태그가 겹치지 않도록 태그 모델을 구성합니다. 예를 들어 두 개의 다른 태그 모델 이름 `shoes` 및 `footwear`에 `sneakers`과 같은 일반적인 태그를 사용하지 마십시오. 교육 프로세스는 한 개의 훈련된 태그 모델을 공통 키워드에 대한 다른 태그 모델로 덮어씁니다.

**예**:지침의 몇 가지 예는 다음과 같습니다.

* 다음을 포함하는 태그 모델 만들기
   * 자동차 모델과 관련된 태그만.
   * 셔츠 색상과 관련된 태그만 표시됩니다.
   * 여성과 남성용 재킷과 관련된 태그만 있습니다.
* 만들지 마십시오.
   * 2019년과 2020년에 출시된 자동차 모델을 포함하는 태그 모델.
   * 동일한 몇 개의 자동차 모델을 포함하는 여러 태그 모델.

**교육에 사용되는 이미지**:동일한 이미지를 사용하여 다른 태그 모델을 교육할 수 있습니다. 그러나 태그 모델에서 둘 이상의 태그와 이미지를 연결하지 마십시오. 동일한 이미지에 다른 태그 모델에 속하는 다른 태그를 지정할 수 있습니다.

교육은 실행 취소할 수 없습니다. 위의 지침은 트레이닝할 이미지를 선택하는 데 도움이 됩니다.

## 사용자 지정 태그 {#train-model} 모델 트레이닝

비즈니스별 태그의 모델을 만들고 교육하려면 다음 단계를 수행합니다.

1. 필요한 태그 및 적절한 태그 구조를 만듭니다. DAM 저장소에 관련 이미지를 업로드합니다.
1. [!DNL Experience Manager] 사용자 인터페이스에서 **[!UICONTROL 자산]** > **[!UICONTROL 스마트 태그 교육]**&#x200B;에 액세스합니다.
1. **[!UICONTROL 만들기]**&#x200B;를 클릭합니다. **[!UICONTROL 제목]**, **[!UICONTROL 설명]**&#x200B;을 제공합니다.
1. 모델을 교육할 `cq:tags`의 기존 태그에서 태그를 찾아 선택합니다. **[!UICONTROL 다음]**&#x200B;을 클릭합니다.
1. **[!UICONTROL 자산 선택]** 대화 상자에서 각 태그에 대해 **[!UICONTROL 자산 추가]**&#x200B;를 클릭합니다. DAM 저장소에서 검색하거나 저장소를 검색하여 최소 10개 및 최대 50개의 이미지를 선택할 수 있습니다. 폴더가 아닌 에셋을 선택합니다. 이미지를 선택하고 나면 **[!UICONTROL 선택]**&#x200B;을 클릭합니다.

   ![교육 상태 보기](assets/smart-tags-training-status.png)

1. 선택한 이미지의 축소판을 미리 보려면 태그 앞에 있는 아코디언을 클릭합니다. **[!UICONTROL 자산 추가]**&#x200B;를 클릭하여 선택 항목을 수정할 수 있습니다. 선택 내용에 만족하면 **[!UICONTROL 제출]**&#x200B;을 클릭합니다. 사용자 인터페이스에서는 페이지 하단에 교육이 시작되었음을 나타내는 알림을 표시합니다.
1. 각 태그 모델의 **[!UICONTROL 상태]** 열에서 교육 상태를 확인합니다. 가능한 상태는 [!UICONTROL 보류 중], [!UICONTROL 훈련됨] 및 [!UICONTROL 실패]입니다.

![스마트 태그 지정을 위한 태깅 모델 트레이닝 워크플로우](assets/smart-tag-model-training-flow.png)

*그림:태깅 모델을 교육하는 교육 워크플로우의 단계.*

### 교육 상태 및 보고서 {#training-status} 보기

스마트 태그 서비스가 자산 교육 세트의 태그에 대해 교육 받았는지 확인하려면 보고서 콘솔에서 교육 워크플로우 보고서를 검토하십시오.

1. [!DNL Experience Manager] 인터페이스에서 **[!UICONTROL 도구] > **[!UICONTROL 자산] > **[!UICONTROL 보고서]**&#x200B;로 이동합니다.
1. **[!UICONTROL 자산 보고서]** 페이지에서 **[!UICONTROL 만들기]**&#x200B;를 클릭합니다.
1. **[!UICONTROL 스마트 태그 교육]** 보고서를 선택한 다음 도구 모음에서 **[!UICONTROL 다음]**&#x200B;을 클릭합니다.
1. 보고서의 제목과 설명을 지정합니다. **[!UICONTROL 보고서 예약]**&#x200B;에서 **[!UICONTROL 지금]** 옵션을 선택한 상태로 두십시오. 나중에 보고서를 예약하려면 **[!UICONTROL 나중에]**&#x200B;를 선택하고 날짜와 시간을 지정합니다. 그런 다음 도구 모음에서 **[!UICONTROL 만들기]**&#x200B;를 클릭합니다.
1. **[!UICONTROL 자산 보고서]** 페이지에서 생성한 보고서를 선택합니다. 보고서를 보려면 도구 모음에서 **[!UICONTROL 보기]**&#x200B;를 클릭합니다.
1. 보고서의 세부 사항을 검토합니다. 보고서에는 교육 받은 태그에 대한 교육 상태가 표시됩니다. **[!UICONTROL 교육 상태]** 열의 녹색 색상은 스마트 태그 서비스가 태그에 대해 훈련되었음을 나타냅니다. 노란색 색상은 서비스가 특정 태그에 대해 완전히 훈련되지 않음을 나타냅니다. 이 경우 특정 태그로 이미지를 더 추가하고 교육 워크플로우를 실행하여 태그에서 서비스를 완전히 교육할 수 있습니다. 이 보고서에 태그가 표시되지 않으면 이러한 태그에 대해 교육 워크플로우를 다시 실행하십시오.태그
1. 보고서를 다운로드하려면 목록에서 보고서를 선택하고 도구 모음에서 **[!UICONTROL 다운로드]**&#x200B;를 클릭합니다. 보고서는 [!DNL Microsoft Excel] 스프레드시트로 다운로드됩니다.

## 자산 {#tag-assets} 태그 지정

스마트 태그 서비스를 교육한 후 다른 유사한 자산 세트에 적절한 태그를 자동으로 적용하도록 태그 지정 워크플로우를 트리거할 수 있습니다. 정기적으로 또는 필요할 때마다 태그 지정 워크플로우를 적용할 수 있습니다. 태그 지정 워크플로우는 자산 및 폴더 모두에 적용됩니다.

### 워크플로우 콘솔 {#tagging-assets-from-the-workflow-console}에서 에셋에 태그 지정

1. Experience Manager 인터페이스에서 **[!UICONTROL 도구 > 워크플로 > 모델]**&#x200B;으로 이동합니다.
1. **[!UICONTROL 워크플로우 모델]** 페이지에서 **[!UICONTROL DAM 스마트 태그 자산]** 작업 과정을 선택한 다음 도구 모음에서 **[!UICONTROL 워크플로우 시작]**&#x200B;을 클릭합니다.

   ![dam_smart_tag_workflow](assets/dam_smart_tag_workflow.png)

1. **[!UICONTROL 워크플로우 실행]** 대화 상자에서 태그를 자동으로 적용할 에셋이 포함된 페이로드 폴더를 찾습니다.
1. 워크플로우의 제목과 선택적 주석을 지정합니다. **[!UICONTROL 실행]**&#x200B;을 클릭합니다.

   ![tagging_dialog](assets/tagging_dialog.png)

   자산 폴더로 이동하고 태그를 검토하여 에셋에 태그가 제대로 지정되어 있는지 확인합니다. 자세한 내용은 [스마트 태그 관리](#manage-smart-tags-and-searches)를 참조하십시오.

### 타임라인 {#tagging-assets-from-the-timeline}에서 에셋에 태그 지정

1. 자산 사용자 인터페이스에서 스마트 태그를 적용할 자산 또는 특정 자산이 들어 있는 폴더를 선택합니다.
1. 왼쪽 위 모서리에서 **[!UICONTROL 타임라인]**&#x200B;을 엽니다.
1. 왼쪽 세로 막대의 맨 아래에서 작업을 열고 **[!UICONTROL 워크플로우 시작]**&#x200B;을 클릭합니다.

   ![start_workflow](assets/start_workflow.png)

1. **[!UICONTROL DAM 스마트 태그 자산]** 작업 과정을 선택하고 작업 과정의 제목을 지정합니다.
1. **[!UICONTROL 시작]**&#x200B;을 클릭합니다. 워크플로우는 자산에 태그를 적용합니다. 자산 폴더로 이동하고 태그를 검토하여 에셋에 태그가 제대로 지정되어 있는지 확인합니다. 자세한 내용은 [스마트 태그 관리](#manage-smart-tags-and-searches)를 참조하십시오.

>[!NOTE]
>
>후속 태그 지정 주기 동안 새로 훈련된 태그로 수정된 자산에만 다시 태그가 지정됩니다. 하지만 태그 지정 작업 과정에 대한 마지막 태그 주기와 현재 태그 지정 주기 사이의 간격이 24시간이 넘는 경우에도 변경되지 않은 자산도 태그로 지정됩니다. 주기적인 태그 지정 워크플로우의 경우 시간 간격이 6개월이 되면 변경되지 않은 자산에 태그가 지정됩니다.

### 업로드된 자산 {#tag-uploaded-assets} 태그 지정

Experience Manager은 사용자가 DAM에 업로드한 자산에 자동으로 태그를 지정할 수 있습니다. 이를 위해 관리자는 스마트 태그 자산에 사용 가능한 단계를 추가하는 워크플로우를 구성합니다. 업로드된 자산](/help/assets/smart-tags-configuration.md#enable-smart-tagging-for-uploaded-assets)에 대해 스마트 태그 지정을 활성화하는 방법을 참조하십시오.[

<!-- TBD: Text-based assets are automatically smart tagged. -->

## 스마트 태그 및 자산 검색 관리 {#manage-smart-tags-and-searches}

브랜드 자산에 할당되었을 수 있는 부정확한 태그를 제거하여 가장 관련성이 높은 태그만 표시되도록 스마트 태그를 조정할 수 있습니다.

스마트 태그를 중재하면 자산이 가장 관련성이 높은 태그에 대한 검색 결과에 표시되도록 하여 태그 기반 검색을 세분화할 수도 있습니다. 기본적으로 관련되지 않은 에셋이 검색 결과에 나타날 가능성을 없애줍니다.

태그에 더 높은 등급을 지정하여 자산에 대한 관련성을 높일 수도 있습니다. 자산에 대한 태그를 승격하면 특정 태그를 기준으로 검색을 수행할 때 자산이 검색 결과에 나타날 가능성이 높아집니다.

자산의 스마트 태그를 중재하려면:

1. Omnisearch 필드에서 태그를 기준으로 자산을 검색합니다.

1. Inspect 검색 결과를 통해 검색과 관련이 없는 자산을 식별할 수 있습니다.

1. 자산을 선택한 다음 도구 모음에서 ![태그 관리 아이콘](assets/do-not-localize/manage-tags-icon.png)을 선택합니다.

1. **[!UICONTROL 태그 관리]** 페이지에서 태그를 검사합니다. 특정 태그를 기준으로 자산을 검색하지 않으려면 태그를 선택하고 도구 모음에서 ![삭제 아이콘](assets/do-not-localize/delete-icon.png)을 선택합니다. 또는 레이블 옆에 있는 `X` 기호를 선택합니다.

1. 태그에 높은 등급을 지정하려면 태그를 선택하고 도구 모음에서 ![홍보 아이콘](assets/do-not-localize/promote-icon.png)을 선택합니다. 홍보하는 태그가 **[!UICONTROL 태그]** 섹션으로 이동됩니다.

1. **[!UICONTROL 저장]**&#x200B;을 선택한 다음 **[!UICONTROL 확인]**&#x200B;을 선택하여 [!UICONTROL 성공] 대화 상자를 닫습니다.

1. 자산에 대한 [!UICONTROL 속성] 페이지로 이동합니다. 홍보한 태그가 높은 연관성을 지정되므로 검색 결과에 더 높은 것으로 나타납니다.

### 스마트 태그 {#understandsearch}를 사용하여 AEM 검색 결과 이해

기본적으로 AEM 검색은 검색어와 `AND` 절을 결합합니다. 스마트 태그를 사용해도 이 기본 동작은 변경되지 않습니다. 스마트 태그를 사용하면 적용된 스마트 태그의 검색어 중 하나를 찾기 위해 추가 `OR` 절이 추가됩니다. 예를 들어 `woman running` 검색을 고려해 보십시오. 메타데이터에 `woman`만 있거나 `running` 키워드만 있는 자산은 기본적으로 검색 결과에 나타나지 않습니다. 그러나 스마트 태그를 사용하여 `woman` 또는 `running` 태그가 지정된 자산이 이러한 검색 쿼리에 나타납니다. 검색 결과는

* 메타데이터에 `woman` 및 `running` 키워드가 있는 자산.

* 두 키워드 중 하나로 태그가 지정된 스마트 자산.

메타데이터 필드의 모든 검색어와 일치하는 검색 결과가 먼저 표시되고, 그 뒤에 스마트 태그의 검색어와 일치하는 검색 결과가 표시됩니다. 위의 예에서 검색 결과의 대략적인 표시 순서는 다음과 같습니다.

1. 다양한 메타데이터 필드에서 `woman running`의 일치 항목을 찾습니다.
1. 스마트 태그의 `woman running`과 일치합니다.
1. 스마트 태그의 `woman` 또는 `running`과 일치합니다.

### 태깅 제한 사항 {#limitations}

향상된 스마트 태그는 브랜드 이미지와 해당 태그의 학습 모델을 기반으로 합니다. 이러한 모델이 태그를 식별하기에 완벽한 것은 아닙니다. 스마트 태그의 현재 버전에서는 다음과 같은 제한이 있습니다.

* 이미지의 미묘한 차이를 인식하지 못함 예를 들어, 슬림형 셔츠와 보통 맞춤 셔츠입니다.
* 이미지의 작은 패턴/부분을 기반으로 태그를 식별하지 못함 예를 들어 T-shirts의 로고가 있습니다.
* 태깅은 Experience Manager에서 지원하는 언어에서 지원됩니다. 언어 목록은 [스마트 콘텐츠 서비스 릴리스 노트](https://experienceleague.adobe.com/docs/experience-manager-64/release-notes/smart-content-service-release-notes.html#languages)를 참조하십시오.

<!-- TBD: Add limitations related to text-based assets. -->

스마트 태그가 있는 에셋을 검색하려면(일반 또는 향상된) 에셋 검색(전체 텍스트 검색)을 사용합니다. 스마트 태그에 대한 별도의 검색 조건자가 없습니다.

>[!NOTE]
>
>태그를 교육하고 다른 이미지에 적용할 스마트 태그의 기능은 교육에 사용하는 이미지의 품질에 따라 달라집니다.
>최상의 결과를 얻으려면 시각적으로 비슷한 이미지를 사용하여 각 태그에 대한 서비스를 교육하는 것이 좋습니다.

>[!MORELIKETHIS]
>
>* [스마트 태깅용 Experience Manager 구성](smart-tags-configuration.md)
>* [스마트 태그를 사용하여 에셋을 관리하는 방법 이해](https://medium.com/adobetech/efficient-asset-management-with-enhanced-smart-tags-887bd47dbb3f)
>* [스마트 태그 지정 비디오 에셋](smart-tags-video-assets.md)

