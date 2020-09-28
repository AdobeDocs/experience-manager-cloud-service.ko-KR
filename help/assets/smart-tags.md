---
title: 스마트 서비스를 사용하여 이미지 태그 지정
description: Adobe Sensei 서비스를 사용하여 상황에 맞는 설명형 비즈니스 태그를 적용하는 지능적인 서비스를 통해 이미지에 태그를 지정할 수 있습니다.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 8b1cc8af67c6d12d7e222e12ac4ff77e32ec7e0e
workflow-type: tm+mt
source-wordcount: '2424'
ht-degree: 1%

---


# 스마트 태그 서비스 트레이닝 및 이미지 태그 지정 {#train-service-tag-assets}

디지털 자산을 처리하는 조직은 자산 메타데이터에 분류 제어 용어를 점점 더 사용하고 있습니다. 기본적으로 직원, 파트너 및 고객이 디지털 자산을 참조하고 검색하는 데 일반적으로 사용하는 키워드 목록이 포함되어 있습니다. 분류 제어 어휘를 사용하여 자산에 태그를 지정하면 태그 기반 검색으로 자산을 쉽게 식별하고 검색할 수 있습니다.

자연어 어휘와 비교하여 비즈니스 분류 방식을 기반으로 태그를 지정하면 자산을 회사의 비즈니스에 맞게 조정하고 검색에서 가장 연관성 있는 자산이 표시되도록 할 수 있습니다. 예를 들어 자동차 제조업체는 자동차 이미지에 모델 이름을 태그로 지정할 수 있으므로 프로모션 캠페인을 디자인하기 위해 검색될 때 관련 이미지만 표시되도록 할 수 있습니다.

In the background, the Smart Tags uses an artificial intelligence framework of [Adobe Sensei](https://www.adobe.com/kr/sensei/experience-cloud-artificial-intelligence.html) to train its image recognition algorithm on your tag structure and business taxonomy. 그런 다음 이 컨텐츠 인텔리전스를 사용하여 다른 자산 세트에 관련 태그를 적용합니다.

<!-- TBD: Create a similar flowchart for how training works in CS.
![flowchart](assets/flowchart.gif) 
-->

스마트 태그 지정을 사용하려면 다음 작업을 완료하십시오.

* [Adobe 개발자 콘솔과 Experience Manager 통합](#integrate-aem-with-aio).
* [태그 모델 및 지침을 이해합니다](#understand-tag-models-guidelines).
* [모델](#train-model)트레이닝
* [디지털 에셋에 태그를 지정할 수 있습니다](#tag-assets).
* [태그 및 검색을 관리합니다](#manage-smart-tags-and-searches).

스마트 태그는 [!DNL Adobe Experience Manager Assets] 고객에게만 적용됩니다. The Smart Tags is available for purchase as an add-on to [!DNL Experience Manager].

<!-- TBD: Is there a link to buy SCS or initiate a sales call. How are AIO services sold? -->

## Integrate [!DNL Experience Manager] with Adobe Developer Console {#integrate-aem-with-aio}

>[!IMPORTANT]
>
>새로운 [!DNL Experience Manager Assets] 배포는 기본적으로 [!DNL Adobe Developer Console] 통합되어 있습니다. 이 기능은 스마트 태그 기능을 보다 빠르게 구성하는 데 도움이 됩니다. 기존 배포에서 관리자는 스마트 태그 통합을 수동으로 [구성할 수 있습니다](/help/assets/smart-tags-configuration.md#aio-integration).

를 사용하여 스마트 태그 [!DNL Adobe Experience Manager] 와 통합할 수 있습니다 [!DNL Adobe Developer Console]. 이 구성을 사용하여 내에서 스마트 태그 서비스에 액세스합니다 [!DNL Experience Manager]. 스마트 태그를 구성하는 작업에 대한 자산 [](smart-tags-configuration.md) 스마트 태그 지정을 위한 Experience Manager 구성을 참조하십시오. At the back end, the [!DNL Experience Manager] server authenticates your service credentials with the Adobe Developer Console gateway before forwarding your request to the Smart Tags service.

## 태그 모델 및 지침 이해 {#understand-tag-models-guidelines}

태그 모델은 이미지의 시각적 측면을 기준으로 하는 관련 태그 그룹입니다. 예를 들어 shoes 컬렉션에는 다른 태그가 있지만 모든 태그는 shoes와 관련되어 있고 동일한 태그 모델에 속할 수 있습니다. 태그는 이미지의 뚜렷한 시각적 측면만 연결할 수 있습니다. 교육 모델의 컨텐츠 표현을 이해하려면 교육 모델을 수동으로 추가한 태그 그룹 [!DNL Experience Manager]과 각 태그에 대한 예제 이미지로 구성된 최상위 엔티티로 시각화합니다. 각 태그는 이미지에 단독으로 적용할 수 있습니다.

현실적으로 처리할 수 없는 태그는 다음과 관련되어 있습니다.

* 제품 출시 년도, 분위기 또는 감정 등 비시각적이고 추상적인 측면을 이미지로 불러옵니다.
* 제품에 임베드된 콜라주가 있는 셔츠 또는 없는 작은 제품 로고와 같은 제품의 시각적 차이를 세밀하게 조정할 수 있습니다.

태그 모델을 만들고 서비스를 교육하기 전에 비즈니스 컨텍스트에서 이미지의 개체를 가장 잘 설명하는 고유한 태그 집합을 식별합니다. 선별된 세트의 에셋이 교육 지침 [을 따르는지 확인합니다](#training-guidelines).

### 교육 지침 {#training-guidelines}

교육 세트의 이미지는 다음 지침을 따라야 합니다.

**수량 및 크기:** 태그당 최소 10개의 이미지와 최대 50개의 이미지.

**일관성**:태그의 이미지는 시각적으로 유사해야 합니다. 동일한 시각적 측면(이미지의 동일한 개체 유형 등)에 대한 태그를 하나의 태그 모델에 함께 추가하는 것이 가장 좋습니다. 예를 들어 이러한 이미지는 시각적으로 유사하지 않기 때문에 이러한 이미지 `my-party` 에 태그를 모두 교육 목적으로 지정하는 것은 좋지 않습니다.

![트레이닝 지침을 예시하기 위한 실례가 되는 이미지](assets/do-not-localize/coherence.png)

**적용 범위**:트레이닝에서 이미지에 다양한 이미지가 있어야 합니다. AEM이 올바른 것에 초점을 맞추도록 소수의 하지만 상당히 다양한 예를 제공하는 것이 그 아이디어입니다. 시각적으로 다른 이미지에 동일한 태그를 적용하는 경우 각 종류의 최소 5개의 예를 포함합니다. 예를 들어 태그 *모델 다운 포즈의*&#x200B;경우 태그 지정 중에 서비스에서 유사한 이미지를 보다 정확하게 식별할 수 있도록 아래 강조 표시된 이미지와 유사한 더 많은 교육 이미지를 포함합니다.

![트레이닝 지침을 예시하기 위한 실례가 되는 이미지](assets/do-not-localize/coverage_1.png)

**방해/방해**:집중을 덜 하는 이미지(두드러진 배경, 주제와 관련된 사물/사람 등 관련 없는 요소)에서 서비스를 더 잘 운행한다. 예를 들어, 태그 *캐주얼*&#x200B;카드의 경우 두 번째 이미지는 올바른 교육 후보가 아닙니다.

![트레이닝 지침을 예시하기 위한 실례가 되는 이미지](assets/do-not-localize/distraction.png)

**완전성:** 이미지가 둘 이상의 태그에 적합하면 교육을 위한 이미지를 포함하기 전에 해당 태그를 모두 추가합니다. 예를 들어, *비코트* 및 *모델측*&#x200B;보기와 같은 태그의 경우 교육을 위해 태그를 포함하기 전에 해당 자산에 둘 다 추가합니다.

![트레이닝 지침을 예시하기 위한 실례가 되는 이미지](assets/do-not-localize/completeness.png)

**태그 수**:Adobe에서는 각 태그에 대해 최소한 두 개의 서로 다른 태그와 최소 10개의 서로 다른 이미지를 사용하여 모델을 교육하는 것이 좋습니다. 단일 태그 모델에서 50개 이상의 태그를 추가하지 마십시오.

**예**&#x200B;수:각 태그에 대해 최소 10개의 예를 추가합니다. 그러나 Adobe은 약 30개의 예를 추천합니다. 태그당 최대 50개의 예가 지원됩니다.

**잘못된 긍지와 충돌 방지**:Adobe에서는 단일 시각적 측면용으로 단일 태그 모델을 만드는 것이 좋습니다. 모델 간의 태그 겹치지 않도록 태그 모델을 구성합니다. 예를 들어, 두 개의 서로 다른 태그 모델 이름 및 `sneakers` 에 있는 일반적인 태그 `shoes` 를 사용하지 마십시오 `footwear`. 교육 프로세스는 하나의 교육된 태그 모델을 공통 키워드에 대한 다른 태그 모델로 덮어씁니다.

**예**:지침은 다음과 같습니다.

* 다음을 포함하는 태그 모델 만들기
   * 자동차 모델과 관련된 태그만.
   * 셔츠 색상과 관련된 태그만 표시됩니다.
   * 여성과 남성용 재킷과 관련된 꼬리표만
* 만들지 마십시오.
   * 자동차 모델이 포함된 태그 모델
   * 동일한 몇 개의 자동차 모델을 포함하는 여러 개의 태그 모델.

**트레이닝에 사용되는 이미지**:동일한 이미지를 사용하여 다른 태그 모델을 교육할 수 있습니다. 그러나 태그 모델에서 이미지를 두 개 이상의 태그와 연결하지 마십시오. 따라서 동일한 이미지에 다른 태그 모델에 속하는 다른 태그를 지정할 수 있습니다.

교육은 실행 취소할 수 없습니다. 위의 지침은 트레이닝할 이미지를 선택하는 데 도움이 됩니다.

## 사용자 지정 태그의 모델 트레이닝 {#train-model}

비즈니스별 태그의 모델을 만들고 교육하려면 다음 단계를 따르십시오.

1. 필요한 태그와 적절한 태그 구조를 만듭니다. DAM 저장소에서 관련 이미지를 업로드합니다.
1. 사용자 [!DNL Experience Manager] 인터페이스에서 **[!UICONTROL 자산]** > **[!UICONTROL 스마트 태그 교육에 액세스합니다]**.
1. **[!UICONTROL 만들기]**&#x200B;를 클릭합니다. 제목 **[!UICONTROL 과 설명]**&#x200B;을 **[!UICONTROL 제공합니다]**.
1. 모델을 교육할 기존 태그의 태그 `cq:tags` 를 찾아보고 선택합니다. **[!UICONTROL 다음]**&#x200B;을 클릭합니다.
1. 자산 **[!UICONTROL 선택]** 대화 상자에서 각 태그에 **[!UICONTROL 대해 자산]** 추가를 클릭합니다. DAM 저장소에서 검색하거나 저장소를 검색하여 최소 10개 및 최대 50개의 이미지를 선택할 수 있습니다. 폴더가 아닌 자산을 선택합니다. 이미지를 선택하고 나면 선택을 **[!UICONTROL 클릭합니다]**.
1. 선택한 이미지의 축소판을 미리 보려면 태그 앞에 있는 아코디언을 클릭합니다. 자산 추가를 클릭하여 선택 사항을 수정할 수 **[!UICONTROL 있습니다]**. 선택한 항목에 만족하면 **[!UICONTROL 제출을 클릭합니다]**. 사용자 인터페이스에서는 페이지 하단에 교육이 시작되었음을 나타내는 알림을 표시합니다.
1. 각 태그 모델의 **[!UICONTROL 상태]** 열에서 교육 상태를 확인합니다. 가능한 상태는 [!UICONTROL 보류]중, [!UICONTROL 훈련됨]및 [!UICONTROL 실패입니다].

![스마트 태그 지정을 위한 태깅 모델 트레이닝 워크플로우](assets/smart-tag-model-training-flow.png)

*그림:태깅 모델을 교육하는 교육 워크플로우의 단계.*

### 교육 상태 및 보고서 보기 {#training-status}

스마트 태그 서비스가 자산 트레이닝 세트의 태그에 대해 교육되었는지 확인하려면 보고서 콘솔에서 교육 워크플로우 보고서를 검토하십시오.

1. 인터페이스에서 [!DNL Experience Manager] 도구 > 자산 > 보고서로 이동합니다 ****.
1. 자산 **[!UICONTROL 보고서]** 페이지에서 만들기를 **[!UICONTROL 클릭합니다]**.
1. 스마트 **[!UICONTROL 태그 교육]** 보고서를 선택한 다음 도구 모음에서 **[!UICONTROL 다음]** 을 클릭합니다.
1. 보고서의 제목과 설명을 지정합니다. 보고서 **[!UICONTROL 예약]**&#x200B;아래에서 **[!UICONTROL 지금]** 옵션을 선택된 상태로 두십시오. 나중에 보고서를 예약하려면 **[!UICONTROL 나중에를]** 선택하고 날짜 및 시간을 지정합니다. 그런 다음 도구 **[!UICONTROL 모음에서]** 만들기를 클릭합니다.
1. 자산 **[!UICONTROL 보고서]** 페이지에서 생성한 보고서를 선택합니다. 보고서를 보려면 도구 모음에서 **[!UICONTROL 보기]** 를 클릭합니다.
1. 보고서의 세부 사항을 검토하십시오. 이 보고서에는 교육된 태그의 교육 상태가 표시됩니다. [ **[!UICONTROL 교육 상태]** ] 열의 녹색 색상은 스마트 태그 서비스가 태그용으로 교육되었음을 나타냅니다. 노란색 색상은 서비스가 특정 태그에 대해 완전히 교육되지 않음을 나타냅니다. 이 경우 특정 태그로 이미지를 더 추가하고 교육 워크플로우를 실행하여 태그에서 서비스를 완전히 교육합니다. 이 보고서에 태그가 없으면 이러한 태그에 대해 교육 워크플로우를 다시 실행하십시오.태그
1. 보고서를 다운로드하려면 목록에서 선택하고 도구 모음에서 **[!UICONTROL 다운로드를]** 클릭합니다. 이 보고서는 Microsoft Excel 스프레드시트로 다운로드됩니다.

## 자산 태그 지정 {#tag-assets}

스마트 태그 서비스를 교육한 후 유사한 다른 자산 세트에 적절한 태그를 자동으로 적용하도록 태그 지정 워크플로우를 트리거할 수 있습니다. 정기적으로 또는 필요할 때마다 태그 지정 워크플로우를 적용할 수 있습니다. 태그 지정 워크플로우는 자산 및 폴더 모두에 적용됩니다.

### 워크플로우 콘솔에서 자산 태그 지정 {#tagging-assets-from-the-workflow-console}

1. Experience Manager 인터페이스에서 **[!UICONTROL 도구 > 워크플로우 > 모델로 이동합니다]**.
1. 워크플로우 **[!UICONTROL 모델]** 페이지에서 **[!UICONTROL DAM 스마트 태그 자산]** 워크플로우를 선택한 다음 도구 모음에서 **[!UICONTROL 워크플로우]** 시작을클릭합니다.

   ![dam_smart_tag_workflow](assets/dam_smart_tag_workflow.png)

1. 워크플로우 **[!UICONTROL 실행]** 대화 상자에서 태그를 자동으로 적용할 자산이 들어 있는 페이로드 폴더를 찾습니다.
1. 워크플로우의 제목과 선택적 주석을 지정합니다. 실행을 **[!UICONTROL 클릭합니다]**.

   ![tagging_dialog](assets/tagging_dialog.png)

   자산 폴더로 이동하고 태그를 검토하여 자산이 올바르게 태그 지정되었는지 확인합니다. 자세한 내용은 스마트 태그 [관리를 참조하십시오](#manage-smart-tags-and-searches).

### 타임라인에서 에셋에 태그 지정 {#tagging-assets-from-the-timeline}

1. 자산 사용자 인터페이스에서 스마트 태그를 적용할 자산 또는 특정 자산이 들어 있는 폴더를 선택합니다.
1. 왼쪽 위 모서리에서 **[!UICONTROL 타임라인을 엽니다]**.
1. 왼쪽 사이드바 아래쪽에서 작업을 열고 [워크플로우 **[!UICONTROL 시작]을 클릭합니다]**.

   ![start_workflow](assets/start_workflow.png)

1. DAM **[!UICONTROL 스마트 태그 자산]** 워크플로우를 선택하고 워크플로우의 제목을 지정합니다.
1. 시작을 **[!UICONTROL 클릭합니다]**. 워크플로우는 자산에 태그를 적용합니다. 자산 폴더를 탐색하고 태그를 검토하여 에셋에 태그가 제대로 지정되어 있는지 확인합니다. 자세한 내용은 스마트 태그 [관리를 참조하십시오](#manage-smart-tags-and-searches).

>[!NOTE]
>
>후속 태그 지정 주기 동안 새로 훈련된 태그로 수정된 자산만 다시 태그됩니다. 하지만 태그 지정 워크플로우에 대한 마지막 태그 지정 주기와 현재 태그 지정 주기 사이의 간격이 24시간이 넘는 경우에도 변경되지 않은 자산에 태그됩니다. 주기적인 태그 지정 워크플로우의 경우, 시간 간격이 6개월이 되면 변경되지 않은 자산에 태그가 지정됩니다.

### 업로드된 자산에 태그 지정 {#tag-uploaded-assets}

Experience Manager은 사용자가 DAM에 업로드한 자산에 자동으로 태그를 지정할 수 있습니다. 이를 위해 관리자는 스마트 태그 자산에 사용 가능한 단계를 추가하는 워크플로우를 구성합니다. 업로드된 자산에 대해 스마트 태그 지정을 활성화하는 [방법을 참조하십시오](/help/assets/smart-tags-configuration.md#enable-smart-tagging-for-uploaded-assets).

## 스마트 태그 및 이미지 검색 관리 {#manage-smart-tags-and-searches}

브랜드 이미지에 지정되었을 수 있는 부정확한 태그를 제거하여 가장 관련성이 높은 태그만 표시되도록 스마트 태그를 조정할 수 있습니다.

또한 스마트 태그를 중재하면 이미지가 가장 관련성이 높은 태그에 대한 검색 결과에 표시되도록 하여 태그 기반의 이미지 검색을 세분화할 수 있습니다. 기본적으로 관련 없는 이미지가 검색 결과에 표시되지 않을 가능성을 없애줍니다.

이미지에 대한 연관성을 높이기 위해 태그에 더 높은 등급을 지정할 수도 있습니다. 이미지에 대한 태그를 승격하면 특정 태그를 기준으로 검색을 수행할 때 이미지가 검색 결과에 표시될 가능성이 높아집니다.

1. Omnisearch 상자에서 태그를 기반으로 자산을 검색합니다.
1. 검색 결과를 Inspect으로 보내 검색과 관련이 없는 이미지를 식별합니다.
1. 이미지를 선택한 다음 도구 모음에서 **[!UICONTROL 태그]** 관리 아이콘을 클릭합니다.
1. 태그 **[!UICONTROL 관리]** 페이지에서 태그를 검사합니다. 특정 태그를 기준으로 이미지를 검색하지 않으려면 태그를 선택한 다음 도구 모음에서 삭제 아이콘을 클릭합니다. 또는 레이블 옆에 표시되는 `X` 기호를 클릭합니다.
1. 태그에 높은 등급을 지정하려면 태그를 선택하고 도구 모음에서 홍보 아이콘을 클릭합니다. 홍보하는 태그가 **[!UICONTROL 태그]** 섹션으로 이동합니다.
1. 저장 **[!UICONTROL 을]**&#x200B;클릭한 다음 **[!UICONTROL 확인을]** 클릭하여 성공 대화 상자를 닫습니다.
1. 이미지의 속성 페이지로 이동합니다. 홍보한 태그에 높은 연관성이 할당되므로 검색 결과에 더 높은 태그가 나타나도록 합니다.

### 스마트 태그를 사용하여 AEM 검색 결과 이해 {#understandsearch}

기본적으로 AEM 검색은 검색어와 `AND` 절을 결합합니다. 스마트 태그를 사용해도 이 기본 동작은 변경되지 않습니다. 스마트 태그를 사용하면 적용 스마트 태그의 검색어 중 하나를 찾기 위한 추가 `OR` 조항이 추가됩니다. For example, consider searching for `woman running`. 메타데이터에 키워드 `woman` 만 `running` 이 있는 자산은 기본적으로 검색 결과에 나타나지 않습니다. 하지만 스마트 태그를 사용하거나 둘 중 하나 `woman` 로 태그가 `running` 지정된 자산이 이러한 검색 쿼리에 나타납니다. 검색 결과는

* 메타데이터에 `woman` 및 키워드가 있는 `running` 자산입니다.

* 두 키워드 중 하나로 태그가 지정된 스마트 자산.

메타데이터 필드의 모든 검색어와 일치하는 검색 결과가 먼저 표시되고, 그 다음에 스마트 태그의 검색어와 일치하는 검색 결과가 표시됩니다. 위 예에서 검색 결과의 대략적인 표시 순서는 다음과 같습니다.

1. 다양한 메타데이터 필드 `woman running` 에서 일치하는 항목을 찾습니다.
1. 의 일치 `woman running` 를 스마트 태그로 지정합니다.
1. 은 스마트 태그 `woman` 에 있거나 `running` 있는 것과 일치합니다.

### 태그 지정 제한 {#limitations}

향상된 스마트 태그는 브랜드 이미지와 해당 태그의 학습 모델을 기반으로 합니다. 이러한 모델이 태그를 식별하는 데 항상 완벽하지는 않습니다. 스마트 태그의 현재 버전에는 다음과 같은 제한 사항이 있습니다.

* 이미지의 미묘한 차이를 인식하지 못함 예를 들어, 슬림형 셔츠는 일반 셔츠가 들어 있는 것과 같습니다.
* 이미지의 작은 패턴/부분을 기반으로 태그를 식별할 수 없음 예를 들어 T-셔츠의 로고
* 태깅은 AEM에서 지원되는 로케일에서 지원됩니다. 언어 목록은 [스마트 태그 릴리스 노트를 참조하십시오](https://docs.adobe.com/content/help/en/experience-manager-64/release-notes/smart-content-service-release-notes.html).

스마트 태그가 있는 자산을 검색하려면(일반 또는 고급) 자산 검색(전체 텍스트 검색)을 사용합니다. 스마트 태그에는 별도의 검색 조건자가 없습니다.

>[!NOTE]
>
>태그에서 태그를 교육하고 다른 이미지에 적용할 스마트 태그의 기능은 교육에 사용하는 이미지의 품질에 따라 달라집니다.
>최상의 결과를 얻으려면 시각적으로 유사한 이미지를 사용하여 각 태그에 대한 서비스를 교육하는 것이 좋습니다.

>[!MORELIKETHIS]
>
>* [스마트 태그 지정을 위한 Experience Manager 구성](smart-tags-configuration.md)
>* [스마트 태그를 사용하여 자산을 관리하는 방법 이해](https://medium.com/adobetech/efficient-asset-management-with-enhanced-smart-tags-887bd47dbb3f)

