---
title: 향상된 스마트 태그
description: Adobe Sensei의 AI 및 ML 서비스를 사용하여 컨텍스트 기반의 수사적 비즈니스 태그를 적용하여 에셋 검색 및 콘텐츠 제작 시간을 단축할 수 있습니다.
contentOwner: AG
translation-type: tm+mt
source-git-commit: dfa9b099eaf7f0d155986bbab7d56901876d98f6

---


# 지능적인 태그 관리 {#smart-tag-assets}

## 스마트 태그 개요 {#overview-of-enhanced-smart-tags}

디지털 자산을 처리하는 조직은 자산 메타데이터에 분류 제어 용어를 점점 더 많이 사용하고 있습니다. 기본적으로 직원, 파트너 및 고객이 특정 클래스의 디지털 자산을 참조하고 검색하는 데 일반적으로 사용하는 키워드 목록이 포함되어 있습니다. 분류 제어 어휘를 사용하여 에셋에 태그를 지정하면 태그 기반 검색으로 쉽게 식별하고 검색할 수 있습니다.

자연어 어휘와 비교하여 비즈니스 분류법에 따라 디지털 자산을 태깅하여 회사의 비즈니스와 정렬하고 가장 연관성 있는 자산이 검색에 표시되는지 확인할 수 있습니다. 예를 들어 자동차 제조업체는 자동차 이미지에 모델 이름을 태그로 지정할 수 있으므로 다양한 모델의 이미지를 검색하여 프로모션 캠페인을 디자인할 때만 관련 이미지가 표시됩니다.

백그라운드에서 Smart Content Service는 Adobe Sensei의 AI 프레임워크를 [사용하여](https://www.adobe.com/sensei/experience-cloud-artificial-intelligence.html) 태그 구조 및 비즈니스 분류법에 대한 이미지 인식 알고리즘을 교육합니다. 그런 다음 이 컨텐츠 인텔리전스를 사용하여 다른 자산 세트에 관련 태그를 적용합니다.

>[!NOTE]
>
>스마트 콘텐츠 서비스는 자산 고객에게만 적용됩니다. 스마트 콘텐츠 서비스는 Experience Manager의 추가 기능으로 구매할 수 있습니다.

<!-- ![flowchart](assets/flowchart.gif) -->

## 스마트 태그 및 검색 관리 {#manage-smart-tags-and-searches}

브랜드 이미지에 지정되었을 수 있는 부정확한 태그를 제거하여 가장 관련성이 높은 태그만 표시되도록 스마트 태그를 조정할 수 있습니다.

또한 스마트 태그를 중재하면 이미지가 가장 관련성이 높은 태그에 대한 검색 결과에 표시되도록 하여 태그 기반의 이미지 검색을 세분화할 수 있습니다. 기본적으로 관련 없는 이미지가 검색 결과에 표시되지 않을 가능성을 제거합니다.

태그에 더 높은 등급을 지정하여 이미지에 대한 관련성을 높일 수도 있습니다. 이미지에 대한 태그를 승격하면 특정 태그를 기준으로 검색을 수행할 때 이미지가 검색 결과에 표시될 가능성이 높아집니다.

1. Omnisearch 상자에서 태그를 기반으로 자산을 검색합니다.
1. 검색 결과를 검사하여 검색과 관련이 없는 이미지를 식별합니다.
1. 이미지를 선택한 다음 도구 모음에서 태그 **[!UICONTROL 관리]** 아이콘을 클릭/탭합니다.
1. 태그 **[!UICONTROL 관리]** 페이지에서 태그를 검사합니다. 특정 태그를 기준으로 이미지를 검색하지 않으려면 태그를 선택한 다음 도구 모음에서 삭제 아이콘을 클릭/탭합니다. 또는 레이블 옆에 표시되는 기호를 클릭/탭합니다. `X`
1. 태그에 높은 등급을 지정하려면 태그를 선택하고 도구 모음에서 홍보 아이콘을 클릭/탭합니다. 홍보하는 태그가 태그 **[!UICONTROL 섹션으로]** 이동합니다.
1. 저장을 클릭/탭한 **[!UICONTROL 다음]**&#x200B;확인을 클릭/탭하여 **[!UICONTROL 성공]** 대화 상자를 닫습니다.
1. 이미지의 속성 페이지로 이동합니다. 홍보한 태그가 높은 연관성이 지정되므로 검색 결과에 더 높게 나타납니다.

### 스마트 태그를 사용하여 AEM 검색 결과 이해 {#understandsearch}

기본적으로 AEM 검색은 검색어와 `AND` 절을 결합합니다. 스마트 태그를 사용해도 이 기본 동작은 변경되지 않습니다. 스마트 태그를 사용하면 적용 스마트 태그의 검색어 중 하나를 찾을 추가 `OR` 절이 추가됩니다. For example, consider searching for `woman running`. 메타데이터에 `woman` 키워드만 있거나 `running` 있는 자산은 기본적으로 검색 결과에 나타나지 않습니다. 하지만, 태그가 `woman` 있거나 스마트 태그를 `running` 사용하는 자산이 이러한 검색 쿼리에 나타납니다. 따라서 검색 결과는

* 메타데이터에 `woman` 및 키워드가 있는 `running` 자산입니다.

* 두 가지 키워드 중 하나로 태그가 지정된 스마트 에셋.

메타데이터 필드의 모든 검색어와 일치하는 검색 결과가 먼저 표시되고, 그 다음에 스마트 태그의 검색어와 일치하는 검색 결과가 표시됩니다. 위의 예에서 검색 결과의 대략적인 표시 순서는 다음과 같습니다.

1. 의 일치 항목을 다양한 메타데이터 `woman running` 필드에 입력합니다.
1. 의 일치 항목을 `woman running` 스마트 태그로 채웁니다.
1. 의 `woman` 일치나 `running` 의 일치

<!-- 

## Training the Smart Content Service {#training-the-smart-content-service}

For the Smart Content Service to recognize your business taxonomy, run it on a set of assets that already include tags that are relevant to your business. After training, the service can apply the same taxonomy on a similar set of assets.

You can train the service multiple times to improve its ability to apply relevant tags. After each training cycle, run a tagging workflow and check whether your assets are tagged appropriately.

You can train the Smart Content Service periodically or on requirement basis.

>[!NOTE]
>
>The training workflow runs on folders only.

### Periodic training {#periodic-training}

You can enable the Smart Content Service to train periodically on the assets and associated tags within a folder. Open the properties page of your asset folder, select **[!UICONTROL Enable Smart Tags]** under the **[!UICONTROL Details]** tab, and save the changes.

Once this option is selected for a folder, AEM runs a training workflow automatically to train the Smart Content Service on the folder assets and their tags. By default, the training workflow runs on a weekly basis at 12:30 AM on Saturdays.

### On-demand training {#on-demand-training}

You can train the Smart Content Service whenever required from the Workflow console.

1. Tap/click the AEM logo, and go to **[!UICONTROL Tools > Workflow > Models]**.
1. From the **[!UICONTROL Workflow Models]** page, select the **[!UICONTROL Smart Tags Training]** workflow and then tap/click **[!UICONTROL Start Workflow]** from the toolbar.
1. In the **[!UICONTROL Run Workflow]** dialog, browse to the payload folder that includes the tagged assets for training the service.
1. Specify a title for the workflow and a add a comment. Then, tap/click **[!UICONTROL Run]**. The assets and tags are submitted for training.

>[!NOTE]
>
>Once the assets in a folder are processed for training, only the modified assets are processed in subsequent training cycles.

### Viewing training reports {#viewing-training-reports}

To check whether the Smart Content Service is trained on your tags in the training set of assets, review the training workflow report from the Reports console.

1. Tap/click the AEM logo, and go to **[!UICONTROL Tools > Assets > Reports]**.
1. In the **[!UICONTROL Asset Reports]** page, tap/click **[!UICONTROL Create]**.
1. Select the **[!UICONTROL Smart Tags Training]** report, and then tap/click **[!UICONTROL Next]** from the toolbar.
1. Specify a title and description for the report. Under **[!UICONTROL Schedule Report]**, leave the **[!UICONTROL Now]** option selected. If you want to schedule the report for later, select **[!UICONTROL Later]** and specify a date and time. Then, tap/click **[!UICONTROL Create]** from the toolbar.
1. In the **[!UICONTROL Asset Reports]** page, select the report you generated. To view the report, tap/click the **[!UICONTROL View]** icon from the toolbar.
1. Review the details of the report.

   The report displays the training status for the tags you trained. The green color in the **[!UICONTROL Training Status]** column indicates that the Smart Content Service is trained for the tag. Yellow color indicates that the service is not completely trained for a particular tag. In this case, add more images with the particular tag and run the training workflow to train the service completely on the tag.

   If you do not see your tags in this report, run the training workflow again for these tags.

1. To download the report, select it from the list, and tap/click the **[!UICONTROL Download]** icon from the toolbar. The report downloads as an Excel file.

## Tagging assets automatically {#tagging-assets-automatically}

After you have trained the Smart Content Service, you can trigger the tagging workflow to automatically apply appropriate tags on a different set of similar assets.

You can run the tagging workflow periodically or whenever required.

>[!NOTE]
>
>The tagging workflow runs on both assets and folders.

### Periodic tagging {#periodic-tagging}

You can enable the Smart Content Service to periodically tag assets within a folder. Open the properties page of your asset folder, select **[!UICONTROL Enable Smart Tags]** under the **[!UICONTROL Details]** tab, and save the changes.

Once this option is selected for a folder, the Smart Content Service automatically tags the assets within the folder. By default, the tagging workflow runs every day at 12:00 AM.

### On-demand tagging {#on-demand-tagging}

You can trigger the tagging workflow from the following to instantly tag your assets:

* Workflow console
* Timeline

>[!NOTE]
>
>If you run the tagging workflow from the timeline, you can apply tags on a maximum of 15 assets at a time.

#### Tagging assets from the Workflow console {#tagging-assets-from-the-workflow-console}

1. Tap/click the AEM logo, and go to **[!UICONTROL Tools > Workflow > Models]**.
1. From the **[!UICONTROL Workflow Models]** page, select the **[!UICONTROL DAM Smart Tags Assets]** workflow and then tap/click **[!UICONTROL Start Workflow]** from the toolbar.
1. In the **[!UICONTROL Run Workflow]** dialog, browse to the payload folder containing assets on which you want to apply your tags automatically.
1. Specify a title for the workflow and an optional comment. Then, tap/click **[!UICONTROL Run]**.

Navigate to the asset folder and review the tags to verify whether the Smart Content Service tagged your assets properly. For details, see [Managing Smart Tags](manage-smart-tags.md).

#### Tagging assets from the timeline {#tagging-assets-from-the-timeline}

1. From the Assets user interface, select the folder containing assets or specific assets to which you want to apply smart tags.
1. Tap/click the GlobalNav icon and open the timeline.
1. Tap/click the arrow at the bottom, and then tap/click **[!UICONTROL Start Workflow]**.
1. Select the **[!UICONTROL DAM Smart Tag Assets]** workflow, and specify a title for the workflow.
1. Tap/click **[!UICONTROL Start]**. The workflow applies your tags on assets. Navigate to the asset folder and review the tags to verify whether the Smart Content Service tagged your assets properly. For details, see [Managing Smart Tags](manage-smart-tags.md).

>[!NOTE]
>
>In the subsequent tagging cycles, only the modified assets are tagged again with newly-trained tags.
>
>However, even unaltered assets are tagged if the gap between the last and current tagging cycles for the tagging workflow exceeds 24 hours.
>
>For periodic tagging workflows, unaltered assets are tagged when the gap exceeds 6 months.


## Smart Content Service Training Guidelines {#smart-content-service-training-guidelines}

To be able to effectively tag your brand images, the Smart Content Service requires that the training images conform to certain guidelines. For best results, images in your training set should conform to the following guidelines:

**Quantity and size:** Minimum 30 images per tag. Minimum of 500 pixels on the longer side.

**Coherence**: Images for a tag should be visually similar.

For example, it is not a good idea to tag all of these images as `my-party` (for training) because they are not visually similar.

![Illustrative images to exemplify the guidelines for training](assets/do-not-localize/coherence.png)

**Coverage**: There should be sufficient variety in the images in the training. The idea is to supply a few but reasonably diverse examples so that AEM learns to focus on the right things. If you're applying the same tag on visually dissimilar images, include at least five examples of each kind.

For example, for the tag *model-down-pose*, include more training images similar to the highlighted image below for the service to identify similar images more accurately during tagging.

![Illustrative images to exemplify the guidelines for training](assets/do-not-localize/coverage_1.png)

**Distraction/obstruction**: The service trains better on images that have less distraction (prominent backgrounds, unrelated accompaniments, such as objects/persons with the main subject).

For example, for the tag *casual-shoe*, the second image is not a good training candidate.

![Illustrative images to exemplify the guidelines for training](assets/do-not-localize/distraction.png)

**Completeness:** If an image qualifies for more than one tag, add all applicable tags before including the image for training. For example, for tags, such as *raincoat* and *model-side-view*, add both the tags on the eligible asset before including it for training.

![Illustrative images to exemplify the guidelines for training](assets/do-not-localize/completeness.png)

### Training limitations {#limitations}

Enhanced smart tags are based on learning models of brand images and their tags. These models are not always perfect at identifying tags. The current version of the Smart Content Service has the following limitations:

* Inability to recognize subtle differences in images. For example, slim versus regular fitted shirts.
* Inability to identify tags based on tiny patterns/parts of an image. For example, logos on T-shirts.
* Tagging is supported in the locales that AEM is supported in. For a list of languages, see [Smart Content Services release notes](https://docs.adobe.com/content/help/en/experience-manager-64/release-notes/smart-content-service-release-notes.html).

To search for assets with smart tags (regular or enhanced), use the Assets Omnisearch (full-text search). There is no separate search predicate for smart tags. 

>[!NOTE]
>
>The ability of the Smart Content Service to train on your tags and apply them on other images depends on the quality of images you use for training. 
>
>For best results, Adobe recommends that you use visually similar images to train the service for each tag.

-->
