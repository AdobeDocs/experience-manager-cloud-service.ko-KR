---
title: 스마트 태그 지정 비디오 에셋
description: 스마트 태그 지정 비디오 에셋은 Adobe Sensei 서비스를 사용하여 컨텍스트 및 수사적 태그를 적용하여 에셋 태그 지정을 자동화합니다.
translation-type: tm+mt
source-git-commit: 68fe67617f0d63872f13427b3fbc7b58f2497aca
workflow-type: tm+mt
source-wordcount: '1284'
ht-degree: 0%

---


# 스마트 태그 지정 비디오 자산 {#video-smart-tags}

매력적인 디지털 경험을 신속하게 제공하기 위해 수작업에 소요되는 시간을 단축해야 하는 새로운 컨텐츠 요구 사항이 증가하고 있습니다. [!DNL Adobe Experience Manager] as a Cloud Service은 인공 지능을 기반으로 한 비디오 에셋의 자동화된 태그 지정을 지원합니다. 비디오에 수동으로 태깅하는 데 시간이 많이 소요될 수 있습니다. 그러나 Adobe Sensei 기반의 동영상 스마트 태그 지정 기능은 인공 지능 모델을 사용하여 비디오 컨텐츠를 분석하고 비디오 에셋에 태그를 추가합니다. DAM 사용자가 고객에게 풍부한 경험을 제공하는 데 걸리는 시간을 줄일 수 있습니다. Adobe의 머신 러닝 서비스는 비디오에 사용할 두 개의 태그 세트를 생성합니다. 반면에 한 세트는 해당 비디오의 개체, 장면 및 속성에 해당합니다.다른 한 세트는 음주, 달리기, 조깅과 같은 행동과 관련이 있다.

스마트 태그 지정에 지원되는 비디오 파일 포맷(및 코덱은 MP4(H264/AVC), MKV(H264/AVC), MOV(H264/AVC, 모션 JPEG), AVI(indo4), FLV(H2) 64/AVC, vp6f) 및 WMV(WMV2) 또한 이 기능을 통해 최대 300MB의 비디오에 태그를 지정할 수 있습니다. 비디오 에셋의 자동화된 태깅은 비디오가 업로드된 후 또는 재처리가 트리거될 때 표준 에셋 처리(축소판 생성 및 메타데이터 추출 포함)로 이루어집니다. 스마트 태그는 [!UICONTROL 속성]에서 [신뢰 점수](#confidence-score-video-tag)의 내림차순으로 표시됩니다. 비디오 태그 지정은 기본적으로 [!DNL Adobe Experience Manager]에서 Cloud Service으로 활성화됩니다. 그러나 폴더에서 비디오 스마트 태그 지정](#opt-out-video-smart-tagging)에 대해 [옵트아웃할 수 있습니다.

## 업로드 시 스마트 태그 비디오{#smart-tag-assets-on-ingestion}

[비디오 에셋](add-assets.md#upload-assets)을 Cloud Service으로 [!DNL Adobe Experience Manager]에 업로드하면 비디오가 ![처리](assets/do-not-localize/assetprocessing.png)됩니다. 처리가 완료되면 [!UICONTROL 속성] 페이지의 [!UICONTROL 기본] 탭을 참조하십시오. 스마트 태그는 [!UICONTROL 스마트 태그] 아래의 비디오에 자동으로 추가됩니다. asset compute 서비스는 Adobe Sensei을 활용하여 이러한 스마트 태그를 만듭니다.

![스마트 태그가 비디오에 추가되고 자산 속성의 기본 탭에 표시됩니다.](assets/smart-tags-added-to-videos.png)

적용된 스마트 태그는 [!UICONTROL 스마트 태그] 내에서 개체 및 작업 태그에 대해 조합된 [신뢰 점수](#confidence-score-video-tag)의 내림차순으로 정렬됩니다.

>[!IMPORTANT]
>
>자동으로 생성된 이러한 태그가 브랜드와 해당 값을 따르는지 확인하기 위해 이러한 태그를 검토해야 합니다.

## DAM {#smart-tag-existing-videos}의 기존 비디오에 스마트 태그 지정

DAM의 기존 비디오 에셋은 자동으로 지능적인 태그가 지정되지 않습니다. 자산에 대한 스마트 태그를 생성하려면 [!UICONTROL 자산 재처리]해야 합니다.

자산 저장소에 이미 존재하는 자산의 스마트 태그 비디오 자산 또는 폴더(하위 폴더 포함)를 만들려면 다음 단계를 수행하십시오.

1. [!DNL Adobe Experience Manager] 로고를 선택한 다음 [!UICONTROL 탐색] 페이지에서 자산을 선택합니다.

1. [!UICONTROL 파일]을 선택하여 자산 인터페이스를 표시합니다.

1. 스마트 태그를 적용할 폴더로 이동합니다.

1. 전체 폴더 또는 특정 비디오 자산을 선택합니다.

1. ![자산 재처리 아이콘](assets/do-not-localize/reprocess-assets-icon.png) [!UICONTROL 자산 재처리] 아이콘을 선택하고 [!UICONTROL 전체 프로세스] 옵션을 선택합니다.

![자산 재처리를 통해 기존 DAM 저장소에 태그 추가](assets/reprocess.gif)

프로세스가 완료되면 폴더 내의 비디오 자산의 [!UICONTROL 속성] 페이지로 이동합니다. 자동으로 추가된 태그는 [!UICONTROL 기본] 탭의 [!UICONTROL 스마트 태그] 섹션에 표시됩니다. 이러한 적용된 스마트 태그는 [신뢰 점수](#confidence-score-video-tag)의 내림차순으로 정렬됩니다.

## 태그가 지정된 비디오 검색 {#search-smart-tagged-videos}

자동 생성된 스마트 태그를 기준으로 비디오 자산을 검색하려면 [Omnisearch](search-assets.md#search-assets-in-aem)를 사용하십시오.

1. 검색 아이콘 ![검색 아이콘](assets/do-not-localize/search_icon.png)을 선택하여 Omnisearch 필드를 표시합니다.

1. 비디오에 명시적으로 추가하지 않은 태그를 Omnisearch 필드에서 지정합니다.

1. 태그를 기준으로 검색합니다.

지정한 태그를 기준으로 검색 결과에 비디오 자산이 표시됩니다.

검색 결과는 메타데이터의 검색어 키워드와 검색된 키워드가 포함된 비디오 자산과 검색된 키워드로 스마트 태그가 지정된 비디오 자산의 조합입니다. 하지만 메타데이터 필드의 모든 검색어와 일치하는 검색 결과가 먼저 표시되고, 그 다음에 스마트 태그의 검색어와 일치하는 검색 결과가 표시됩니다. 자세한 내용은 [스마트 태그](smart-tags.md#understandsearch)가 있는 검색 결과 이해를 참조하십시오. [!DNL Experience Manager] 

## 비디오 스마트 태그 {#moderate-video-smart-tags} 중재

[!DNL Adobe Experience Manager] 스마트 태그를 다음과 같이 조정할 수 있습니다.

* 브랜드 비디오에 할당된 부정확한 태그를 제거합니다.

* 비디오에 대한 태그 기반 검색을 세분화하여 비디오가 가장 연관성 높은 태그를 검색 결과에 표시되도록 합니다. 따라서 관련 없는 비디오가 검색 결과에 표시될 가능성을 없애줍니다.

* 비디오와 관련된 연관성을 높이기 위해 태그에 높은 등급을 지정합니다. 비디오에 대한 태그를 승격하면 해당 태그를 기준으로 검색을 수행할 때 비디오가 검색 결과에 표시될 가능성이 높아집니다.

자산에 대한 스마트 태그를 중재하는 방법에 대한 자세한 내용은 [스마트 태그 관리](smart-tags.md#manage-smart-tags-and-searches)를 참조하십시오.

![비디오 스마트 태그 중재](assets/manage-video-smart-tags.png)

>[!NOTE]
>
>[스마트 태그 관리](smart-tags.md#manage-smart-tags-and-searches)의 단계를 사용하여 중재되는 모든 태그는 자산의 재처리 시 기억되지 않습니다. 원래 태그 세트가 다시 표시됩니다.

## 비디오 스마트 태그 지정 수신 거부 {#opt-out-video-smart-tagging}

비디오에 대한 자동 태그 지정은 축소판 생성 및 메타데이터 추출 등의 다른 에셋 처리 작업과 동시에 실행되므로 시간이 많이 걸릴 수 있습니다. 에셋 처리 속도를 높이기 위해 폴더 수준에서 업로드 시 비디오 스마트 태그 지정을 옵트아웃할 수 있습니다.

특정 폴더에 업로드된 자산에 대한 자동화된 비디오 스마트 태그 생성을 제외하려면:

1. [!UICONTROL 속성] 폴더에서 [!UICONTROL 자산 처리] 탭을 엽니다.

1. [!UICONTROL 비디오용 스마트 태그] 메뉴에서 [!UICONTROL 상속됨] 옵션이 기본적으로 선택되어 있고 비디오 스마트 태그가 활성화되어 있습니다.

   [!UICONTROL 상속됨] 옵션을 선택하면 상속된 폴더 경로가 [!UICONTROL Enable] 또는 [!UICONTROL Disable]으로 설정되었는지 여부에 대한 정보와 함께 표시됩니다.

   ![비디오 스마트 태그 지정 비활성화](assets/disable-video-tagging.png)

1. 폴더에 업로드된 비디오의 스마트 태그 지정을 옵트아웃하려면 [!UICONTROL 비활성화]을 선택합니다.

>[!IMPORTANT]
>
>업로드 시 폴더에서 비디오에 태그 지정을 해제하여 업로드한 후 비디오에 스마트 태그를 지정하려면 [!UICONTROL 속성] 폴더의 [!UICONTROL 자산 처리] 탭에서 **[!UICONTROL 비디오에 대한 스마트 태그 활성화]** 및 [[!UICONTROL 자산 재처리] 옵션](#smart-tag-existing-videos)을 사용하십시오. 을 클릭하여 비디오에 스마트 태그를 추가합니다.

## 신뢰 점수 {#confidence-score-video-tag}

[!DNL Adobe Experience Manager] 개체 및 작업 스마트 태그에 최소 신뢰 임계값을 적용하여 각 비디오 자산에 대해 태그가 너무 많으므로 색인 작업이 느려집니다. 자산 검색 결과는 신뢰 점수를 기준으로 순위가 매겨져, 일반적으로 비디오 에셋의 지정된 태그에 대한 검사 결과 이외의 검색 결과가 개선됩니다. 부정확한 태그에는 신뢰 점수가 낮아서 에셋에 대한 스마트 태그 목록 맨 위에 나타나는 경우가 거의 없습니다.

[!DNL Adobe Experience Manager]의 작업 및 개체 태그의 기본 임계값은 0.7입니다(0과 1 사이의 값이어야 함). 일부 비디오 자산에 특정 태그가 지정되어 있지 않은 경우 알고리즘이 예측된 태그에 70% 미만임을 나타냅니다. 기본 임계값이 모든 사용자에게 항상 최적의 것은 아닐 수 있습니다. 따라서 OSGI 구성에서 신뢰 점수 값을 변경할 수 있습니다.

Cloud Manager를 통해 Cloud Service으로 [!DNL Adobe Experience Manager]에 배포된 프로젝트에 신뢰 점수 OSGI 구성을 추가하려면:

* [!DNL Adobe Experience Manager] 프로젝트(`ui.config`, Tranype 24 이후 또는 이전에 `ui.apps`)에 `config.author` OSGi 구성에 다음 콘텐트가 포함된 `com.adobe.cq.assetcompute.impl.senseisdk.SenseiSdkImpl.cfg.json`이라는 구성 파일을 포함합니다.

```json
{
  "minVideoActionConfidenceScore":0.5,
  "minVideoObjectConfidenceScore":0.5,
}
```

>[!NOTE]
>
>수동 태그에는 100%(최대 신뢰)의 신뢰도가 할당됩니다. 따라서 검색 쿼리와 일치하는 수동 태그가 있는 비디오 자산이 있는 경우 검색 쿼리와 일치하는 스마트 태그 앞에 표시됩니다.

## 제한 사항 {#video-smart-tagging-limitations}

* 비디오 자산에 대한 태그 지정을 위한 스마트 태그 서비스(또는 향상된 스마트 태그) 교육은 아직 지원되지 않습니다.

* 태그 지정 진행 상태가 표시되지 않습니다.

* 300MB 이하의 비디오만 태깅에 적합합니다. Adobe Sensei 서비스는 이 기준을 충족하는 비디오에 태그를 지정하고 폴더의 다른 비디오에 태그 지정을 건너뜁니다.

* MP4(H264/AVC), MKV(H264/AVC), MOV(H264/AVC, Motion JPEG), AVI(indo4), FLV(H22) 64/AVC, vp6f) 및 WMV(WMV2)에 태그를 지정할 수 있습니다.

>[!MORELIKETHIS]
>
>* [스마트 태그 및 자산 검색 관리](smart-tags.md#manage-smart-tags-and-searches)
>* [스마트 태그 서비스 트레이닝 및 이미지 태그 지정](smart-tags.md)

