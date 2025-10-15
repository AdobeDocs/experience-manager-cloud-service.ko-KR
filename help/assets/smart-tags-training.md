---
title: ' [!DNL Adobe Sensei] 스마트 서비스로 자산 자동 태그 지정'
description: 상황별 및 설명적 비즈니스 태그를 적용하는 인위적인 지능형 서비스로 자산에 태그를 지정합니다.
feature: Smart Tags,Tagging
role: Admin,User
source-git-commit: a579e2e25ecff93f6f1487ec0bcd317df09751cf
workflow-type: tm+mt
source-wordcount: '1510'
ht-degree: 5%

---


# 스마트 태그 교육

스마트 태그 교육을 사용하면 관련 태그가 없는 경우 세부 사항을 지정할 수 있도록 태그를 교육할 수 있습니다. [Adobe Sensei](https://business.adobe.com/kr/why-adobe/experience-cloud-artificial-intelligence.html)의 인공 지능 프레임워크를 사용하여 태그 구조 및 비즈니스 분류법에 대한 이미지 인식 알고리즘을 교육합니다. 그런 다음 이 콘텐츠 인텔리전스를 사용하여 다른 에셋 세트에 관련 태그를 적용합니다. [!DNL Experience Manager Assets]은(는) 기본적으로 업로드된 자산에 스마트 태그를 자동으로 적용합니다.

## 스마트 태그 교육 요구 사항 확인 {#smart-tag-training-requirement}

다음 시나리오에서는 스마트 태그 교육이 필요합니다.

* 자동화된 레이블을 추가하여 동일한 에셋을 업로드할 때마다 레이블을 추가하는 반복을 저장합니다.
* 관련 태그를 적용하는 에셋의 기능을 개선하기 위해.
* 에셋에 대해 표시되는 태그의 정확도를 높이기 위해
* 사용할 수 없거나 누락된 레이블을 추가하려면


>[!NOTE]
>
>교육용 스마트 태그는 자산의 ***image-type***&#x200B;에서만 적용할 수 있습니다.

## 스마트 태그 교육에 관련된 단계

[!DNL Experience Manager] as a [!DNL Cloud Service]&#x200B;(은)는 기본적으로 스마트 태그를 텍스트 기반 에셋 및 비디오에 자동 생성합니다. 이미지에 스마트 태그를 교육하려면 다음 작업을 완료하십시오.

* [태그 모델 및 지침 이해](#understand-tag-models-guidelines)
* [모델 교육](#train-model)
* [디지털 자산에 태그 지정](#tag-assets)
* [태그 및 검색 관리](#manage-smart-tags-and-searches)

## 태그 모델 및 지침 이해 {#understand-tag-models-guidelines}

태그 모델은 태그가 지정되는 이미지의 다양한 시각적 측면과 연관된 관련 태그의 그룹입니다. 태그는 이미지의 뚜렷하게 다른 시각적 측면과 관련이 있으므로 태그를 적용하면 특정 유형의 이미지를 검색하는 데 도움이 됩니다. 예를 들어 신발 컬렉션에는 서로 다른 태그가 있을 수 있지만 모든 태그는 신발과 관련되어 있으며 동일한 태그 모델에 속할 수 있습니다. 태그를 적용하면 디자인 또는 용도 등 다양한 유형의 신발을 찾는 데 도움이 됩니다.

태그 모델을 만들고 서비스를 교육하기 전에 비즈니스 컨텍스트에서 이미지에 있는 개체를 가장 잘 설명하는 고유 태그 세트를 식별하십시오. 큐레이트된 세트의 자산이 [교육 지침](#training-guidelines)을(를) 확인합니다.

### 교육 지침 {#training-guidelines}

교육 세트의 이미지가 다음 지침을 준수하는지 확인합니다.

<table>
   <tr>
      <th> 지표 </th>
      <th> 설명 </th>
   </tr>
   <tr>
      <td> <b>수량 및 크기 </b></td>
      <td> 태그당 최소 10개 및 최대 50개의 이미지 </td>
   </tr>
   <tr>
      <td> <b>일관성</b> </td>
      <td> 태그의 이미지가 시각적으로 유사한지 확인합니다. 동일한 시각적 측면(예: 이미지의 동일한 오브젝트 유형)에 대한 태그를 단일 태그 모델에 함께 추가하는 것이 가장 좋습니다. 예를 들어 이러한 모든 이미지는 시각적으로 유사하지 않으므로 <i>내 파티</i>(교육용)로 태그를 지정하는 것은 좋지 않습니다. </td>
   </tr>
   <tr>
      <td colspan="2"> <img src="assets/do-not-localize/coherence.png"><br><i>그림: 교육에 대한 지침을 설명하기 위한 일관성 이미지</i>
      </td>
   </tr>
   <tr>
      <td> <b>적용 범위</b></td>
      <td> 교육 시 이미지의 다양성이 충분해야 합니다. 아이디어는 적지만 합리적으로 다양한 예시를 제공하여 학습자가 올바른 것에 집중할 수 있도록 하는 것입니다. 시각적으로 다른 이미지에 동일한 태그를 적용하는 경우에는 각 종류의 예제를 5개 이상 포함하십시오. 예를 들어 태그 <i>모델-아래-포즈</i>의 경우 태그 지정 중에 유사한 이미지를 더 정확하게 식별하기 위해 서비스에 대해 아래 강조 표시된 이미지와 유사한 교육 이미지를 더 포함하십시오.</td>
   </tr>
   <tr>
   <td colspan="2"> <img src="assets/do-not-localize/coverage_1.png"><br><i>그림: 교육에 대한 지침을 예시하기 위한 적용 범위 그림</i>
   </td>
   </tr>
   <tr>
      <td><b>방해/방해</b> </td>
      <td> 이 서비스는 산만함이 적은 이미지(눈에 띄는 배경, 주요 주체가 있는 사물/사람과 같은 관련 없는 반주)에 대해 더 잘 교육합니다. 예를 들어 태그 <i>캐주얼 신발</i>의 경우 두 번째 이미지는 좋은 교육 후보가 아닙니다. </td>
   </tr>
   <tr>
      <td colspan="2"> <img src="assets/do-not-localize/distraction.png"><br><i>그림: 교육 지침을 설명하기 위한 주의 산만/폐색 그림</i>
      </td>
   </tr>
   <tr>
      <td> <b>완성도</b> </td>
      <td> 이미지가 둘 이상의 태그에 적합한 경우 교육용 이미지를 포함하기 전에 적용 가능한 모든 태그를 추가하십시오. For example, for tags, such as <i>raincoat</i> and <i>model-side-view</i>, add both the tags on the eligible asset before including it for training. </td>
   </tr>
   <tr>
      <td colspan="2"> <img src="assets/do-not-localize/completeness.png"><br><i>그림: 교육에 대한 지침을 설명하기 위한 완성도 그림</i>
      </td>
   </tr>
   <tr>
      <td> <b>태그 수</b> </td>
      <td> Adobe에서는 각 태그에 대해 두 개 이상의 고유한 태그와 10개 이상의 서로 다른 이미지를 사용하여 모델을 교육할 것을 권장합니다. 단일 태그 모델에서는 태그를 50개 이상 추가하지 마십시오. </td>
   </tr>
   <tr>
      <td> <b>예제 수</b> </td>
      <td> 각 태그에 대해 최소 10개 이상의 예제를 추가하십시오. 그러나 Adobe에서는 약 30개의 예제를 권장합니다. 태그당 최대 50개의 예제가 지원됩니다. </td>
   </tr>
   <tr>
      <td> <b>긍정 오류 및 충돌 방지</b> </td>
      <td> Adobe에서는 단일 시각적 측면을 위해 단일 태그 모델을 만들 것을 권장합니다. 모델 간에 태그가 겹치지 않도록 태그 모델을 구조화합니다. 예를 들어 <i>신발</i> 및 <i>신발</i> 태그 모델 이름의 <i>운동화</i>와 같은 일반적인 태그를 사용하지 마십시오. 트레이닝 프로세스는 공통 키워드에 대해 트레이닝된 하나의 태그 모델을 다른 모델과 덮어씁니다. </td>
   </tr>
</table>

**예**: 자세한 지침 예는 다음과 같습니다.

* 다음을 포함하는 태그 모델 만들기

   * 자동차 모델과 관련된 태그입니다.
   * 성인과 어린이용 자켓 관련 태그입니다.

* 만들지 않음,

   * 2019년 및 2020년에 출시된 자동차 모델이 포함된 태그 모델입니다.
   * 동일한 소수의 자동차 모델을 포함하는 여러 태그 모델.

>[!NOTE]
>
>동일한 이미지를 사용하여 서로 다른 태그 모델을 교육할 수 있습니다. 그러나 이미지를 태그 모델에서 두 개 이상의 태그와 연결해서는 안 됩니다. 상이한 태그 모델에 속하는 상이한 태그를 갖는 동일한 이미지에 태그를 지정할 수 있다.
>&#x200B;>교육을 실행 취소할 수 없습니다. 위의 지침은 교육할 좋은 이미지를 선택하는 데 도움이 됩니다.

## 사용자 정의 태그에 대한 모델 교육 {#train-model}

비즈니스별 태그에 대한 모델을 만들고 교육하려면 다음 단계를 따르십시오.

1. 필요한 태그와 적절한 태그 구조를 만듭니다. DAM 저장소에서 관련 이미지를 업로드합니다.
1. [!DNL Experience Manager Cloud Service] 사용자 인터페이스에서 **[!UICONTROL Assets]** > **[!UICONTROL 스마트 태그 교육]**&#x200B;에 액세스합니다.
1. **[!UICONTROL 만들기]**&#x200B;를 클릭합니다. **[!UICONTROL 제목]**, **[!UICONTROL 설명]**&#x200B;을 입력하십시오.
1. **[!UICONTROL 태그]** 필드에서 폴더 아이콘을 클릭합니다. 팝업 창이 열립니다.
1. `cq-tags`의 기존 태그 중 모델에 추가할 태그를 검색하거나 선택합니다. **[!UICONTROL 다음]**&#x200B;을 클릭합니다.

   >[!NOTE]
   >
   >**[!UICONTROL 이름]**(알파벳 순서), **[!UICONTROL 생성됨]** 날짜 또는 **[!UICONTROL 수정됨]** 날짜를 기준으로 태그 구조를 오름차순 또는 내림차순으로 정렬할 수 있습니다.


1. **[!UICONTROL Assets 선택]** 대화 상자에서 각 태그에 대해 **[!UICONTROL Assets 추가]**&#x200B;를 클릭합니다. DAM 저장소에서 검색하거나 저장소를 탐색하여 최소 10개 이상 최대 50개 이하의 이미지를 선택합니다. 폴더가 아닌 에셋을 선택합니다. 이미지를 선택했으면 **[!UICONTROL 선택]**&#x200B;을 클릭합니다.

   ![교육 상태 보기](assets/smart-tags-training-status.png)

1. 선택한 이미지의 썸네일을 미리 보려면 태그 앞의 아코디언을 클릭합니다. **[!UICONTROL Assets 추가]**&#x200B;를 클릭하여 선택 항목을 수정할 수 있습니다. 선택 항목이 만족스러우면 **[!UICONTROL 제출]**&#x200B;을 클릭하세요. 사용자 인터페이스는 교육이 시작되었음을 나타내는 통지를 페이지 하단에 표시합니다.
1. 각 태그 모델의 **[!UICONTROL 상태]** 열에서 교육 상태를 확인하십시오. 가능한 상태는 [!UICONTROL 보류 중], [!UICONTROL 훈련됨] 및 [!UICONTROL 실패]입니다.

![스마트 태그에 대한 태그 지정 모델을 교육하는 워크플로](assets/smart-tag-model-training-flow.png)

*그림: 태그 지정 모델을 교육하는 교육 워크플로의 단계입니다.*

### 교육 상태 및 보고서 보기 {#training-status}

스마트 태그 서비스가 교육 에셋 세트의 태그에 대해 교육되었는지 확인하려면 보고서 콘솔에서 교육 워크플로우 보고서를 검토하십시오.

1. [!DNL Experience Manager Cloud Service] 인터페이스에서 **[!UICONTROL 도구]** > **[!UICONTROL Assets]** > **[!UICONTROL 보고서]**(으)로 이동합니다.
1. **[!UICONTROL 자산 보고서]** 페이지에서 **[!UICONTROL 만들기]**&#x200B;를 클릭합니다.
1. **[!UICONTROL 스마트 태그 교육]** 보고서를 선택한 다음 도구 모음에서 **[!UICONTROL 다음]**&#x200B;을 클릭합니다.
1. Specify a title and description for the report. Under **[!UICONTROL Schedule Report]**, leave the **[!UICONTROL Now]** option selected. If you want to schedule the report for later, select **[!UICONTROL Later]** and specify a date and time. 그런 다음 도구 모음에서 **[!UICONTROL 만들기]**&#x200B;를 클릭합니다.
1. In the **[!UICONTROL Asset Reports]** page, select the report you generated. 보고서를 보려면 도구 모음에서 **[!UICONTROL 보기]**&#x200B;를 클릭하십시오.
1. 보고서의 세부 사항을 검토합니다. The report displays the training status for the tags you trained. **[!UICONTROL 교육 상태]** 열의 녹색 색상은 스마트 태그 서비스가 태그에 대해 교육되었음을 나타냅니다. 노란색 색상은 서비스가 특정 태그에 대해 부분적으로 트레이닝되었음을 나타냅니다. 태그에 대한 서비스를 완전히 교육하려면 특정 태그로 이미지를 더 추가하고 교육 워크플로우를 실행하십시오. 이 보고서에 태그가 표시되지 않으면 이러한 태그에 대한 교육 워크플로우를 다시 실행하십시오.태그
1. 보고서를 다운로드하려면 목록에서 선택한 다음 도구 모음에서 **[!UICONTROL 다운로드]**&#x200B;를 클릭하십시오. 보고서는 스프레드시트로 다운로드됩니다.

>[!NOTE]
>
>내보내기를 통해 한 인스턴스에서 다른 인스턴스로 스마트 태그 전송을 전송하려면 어떻게 합니까?
>&#x200B;>환경이 동일한 IMS 조직에 속하는 경우 스마트 태그 교육을 내보낼 필요가 없습니다. 자동으로 공유됩니다. 환경이 IMS 조직에 걸쳐 있는 경우 스마트 태그 교육을 공유하거나 내보낼 수 있는 방법이 없습니다.

## 스마트 태그와 관련된 제한 사항 및 우수 사례 {#limitations-smart-tags-training}

* 모델을 교육하려면 가장 적절한 이미지를 사용하십시오. 교육을 되돌리거나 교육 모델을 제거할 수 없습니다. 태그 지정 정확도는 현재 교육에 따라 다르므로 주의해서 수행합니다.
* 특정 비디오를 사용하여 비디오에 스마트 태그를 적용하는 서비스를 교육할 수 없습니다. 기본 [!DNL Adobe Sensei] 설정에서 작동합니다.


>[!NOTE]
>
>태그에 대해 교육하고 다른 이미지에 적용하는 스마트 태그의 기능은 교육에 사용하는 이미지의 품질에 따라 다릅니다.
>&#x200B;>Adobe 최상의 결과를 얻으려면 시각적으로 유사한 이미지를 사용하여 각 태그에 대한 서비스를 교육하는 것이 좋습니다.
