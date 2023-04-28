---
title: 비디오 에셋에 스마트 태그 지정
description: Experience Manager은 다음을 사용하여 상황에 맞는 및 설명적인 스마트 태그를 비디오에 자동으로 추가합니다 [!DNL Adobe Sensei].
feature: Smart Tags,Tagging
role: Admin,User
exl-id: b59043c5-5df3-49a7-b4fc-da34c03649d7
source-git-commit: 8bdd89f0be5fe7c9d4f6ba891d7d108286f823bb
workflow-type: tm+mt
source-wordcount: '1213'
ht-degree: 2%

---

# 비디오 에셋에 스마트 태그 지정 {#video-smart-tags}

새로운 컨텐츠의 필요성이 확대되면 매력적인 디지털 경험을 신속하게 제공하기 위해 수작업 단축이 필요합니다. [!DNL Adobe Experience Manager] 로서의 [!DNL Cloud Service] 에서는 인공 지능을 사용하여 비디오 자산의 자동 태그 지정을 지원합니다. 비디오에 수동으로 태깅하는 데에는 시간이 많이 걸릴 수 있습니다. 하지만, [!DNL Adobe Sensei] 강력한 비디오 스마트 태그 지정 기능은 인공 지능 모델을 사용하여 비디오 컨텐츠를 분석하고 비디오 자산에 태그를 추가합니다. 따라서 DAM 사용자가 고객에게 풍부한 경험을 전달하는 시간을 줄일 수 있습니다. Adobe의 기계 학습 서비스는 비디오용 태그 세트를 두 개 생성합니다. 반면, 한 세트는 해당 비디오의 개체, 장면 및 속성에 해당합니다. 다른 세트는 음주, 달리기, 조깅과 같은 행동에 관한 것이다.

비디오 태깅은 기본적으로 [!DNL Adobe Experience Manager] 로서의 [!DNL Cloud Service]. 그러나 다음을 수행할 수 있습니다 [비디오 스마트 태그 지정 옵트아웃](#opt-out-video-smart-tagging) 클릭합니다. 새 비디오를 업로드하거나 기존 비디오를 재처리할 때 비디오에 자동으로 태그가 지정됩니다. [!DNL Experience Manager] 또한 축소판 그림을 만들고 비디오 파일의 메타데이터를 추출합니다. 스마트 태그는 내림차순으로 표시됩니다 [신뢰 점수](#confidence-score-video-tag) 자산 [!UICONTROL 속성].

## 업로드 시 스마트 태그 지정 비디오 {#smart-tag-assets-on-ingestion}

다음 경우에 [비디오 자산 업로드](add-assets.md#upload-assets) to [!DNL Adobe Experience Manager] 로서의 [!DNL Cloud Service]로 설정되면 동영상이 처리됩니다. 처리가 완료되면 [!UICONTROL 기본] 자산 탭 [!UICONTROL 속성] 페이지. 스마트 태그는 아래에 비디오에 자동으로 추가됩니다 [!UICONTROL 스마트 태그]. 자산 마이크로서비스 활용 [!DNL Adobe Sensei] 를 입력하여 이러한 스마트 태그를 만들 수 있습니다.

![스마트 태그가 비디오에 추가되고 자산 속성의 기본 탭에 표시됩니다](assets/smart-tags-added-to-videos.png)

적용된 스마트 태그는 내림차순으로 정렬됩니다. [신뢰 점수](#confidence-score-video-tag), 내의 개체 및 작업 태그에 결합됨 [!UICONTROL 스마트 태그].

>[!IMPORTANT]
>
>자동으로 생성된 이러한 태그를 검토하여 브랜드와 해당 값을 준수하도록 해야 합니다.

## DAM에서 기존 비디오에 스마트 태그 지정 {#smart-tag-existing-videos}

DAM에 이미 있는 기존 비디오 자산은 자동으로 태그가 지정되지 않습니다. 다음을 수행해야 합니다. [!UICONTROL 자산 재처리] 수동으로 스마트 태그를 생성합니다.

자산 저장소에 이미 있는 자산의 스마트 태그 비디오 자산 또는 폴더(하위 폴더 포함)에 태그를 지정하려면 다음 단계를 수행합니다.

1. 을(를) 선택합니다 [!DNL Adobe Experience Manager] 로고를 클릭한 다음, [!UICONTROL 탐색] 페이지.

1. 선택 [!UICONTROL 파일] 자산 인터페이스를 표시합니다.

1. 스마트 태그를 적용할 폴더로 이동합니다.

1. 전체 폴더 또는 특정 비디오 자산을 선택합니다.

1. 선택 ![자산 재처리 아이콘](assets/do-not-localize/reprocess-assets-icon.png) [!UICONTROL 자산 재처리] 아이콘을 클릭하고 [!UICONTROL 전체 프로세스] 선택 사항입니다.

<!-- TBD: Limit size -->

![자산을 재처리하여 기존 DAM 저장소에 태그 추가](assets/reprocess.gif)

프로세스가 완료되면 을(를) 통해 [!UICONTROL 속성] 폴더 내의 비디오 자산의 페이지입니다. 자동으로 추가된 태그는 [!UICONTROL 스마트 태그] 섹션 [!UICONTROL 기본] 탭. 적용된 이러한 스마트 태그는 다음과 같이 내림차순으로 정렬됩니다 [신뢰 점수](#confidence-score-video-tag).

## 태그가 지정된 비디오 검색 {#search-smart-tagged-videos}

자동 생성된 스마트 태그를 기반으로 비디오 자산을 검색하려면 [Omnisearch](search-assets.md#search-assets-in-aem):

1. 검색 아이콘을 선택합니다 ![검색 아이콘](assets/do-not-localize/search_icon.png) Omnisearch 필드를 표시합니다.

1. Omnisearch 필드에서 비디오에 명시적으로 추가하지 않은 태그를 지정합니다.

1. 태그를 기준으로 검색합니다.

지정한 태그를 기준으로 검색 결과에 비디오 자산이 표시됩니다.

검색 결과는 비디오 자산과 메타데이터에서 검색된 키워드와 검색된 키워드로 스마트 태그가 지정된 비디오 자산의 조합입니다. 하지만 메타데이터 필드의 모든 검색어와 일치하는 검색 결과가 먼저 표시되고, 그 뒤에 스마트 태그의 검색어와 일치하는 검색 결과가 표시됩니다. 자세한 내용은 [이해 [!DNL Experience Manager] 스마트 태그가 있는 결과 검색](smart-tags.md#understand-search).

## 비디오 스마트 태그 중재 {#moderate-video-smart-tags}

[!DNL Adobe Experience Manager] 스마트 태그를 조정

* 브랜드 비디오에 지정된 부정확한 태그를 제거합니다.

* 태그 기반 검색을 통해 가장 관련성이 높은 태그를 검색 결과에 비디오로 표시할 수 있습니다. 따라서 관련 없는 비디오가 검색 결과에 표시될 가능성을 없애줍니다.

* 태그에 높은 등급을 할당하여 비디오와 관련된 관련성을 높입니다. 비디오에 대한 태그를 승격하면 해당 태그를 기반으로 검색을 수행할 때 비디오가 검색 결과에 표시될 가능성이 높아집니다.

자산에 대한 스마트 태그를 중재하는 방법에 대한 자세한 내용은 [스마트 태그 관리](smart-tags.md#manage-smart-tags-and-searches).

![비디오 스마트 태그 중재](assets/manage-video-smart-tags.png)

>[!NOTE]
>
>의 단계를 사용하여 조정된 모든 태그 [스마트 태그 관리](smart-tags.md#manage-smart-tags-and-searches) 는 자산의 재처리에 대해 기억되지 않습니다. 원래 태그 세트가 다시 표시됩니다.

## 비디오 스마트 태그 지정 옵트아웃 {#opt-out-video-smart-tagging}

비디오의 자동 태깅이 축소판 작성 및 메타데이터 추출과 같은 다른 자산 처리 작업과 동시에 실행되므로 시간이 많이 걸릴 수 있습니다. 자산 처리를 더 신속히 처리하기 위해 폴더 수준에서 업로드 시 비디오 스마트 태그 지정을 옵트아웃할 수 있습니다.

특정 폴더에 업로드된 자산에 대한 자동화된 비디오 스마트 태그 생성을 옵트아웃하려면:

1. 열기 [!UICONTROL 자산 처리] 폴더의 탭 [!UICONTROL 속성].

1. in [!UICONTROL 비디오용 스마트 태그] 메뉴, [!UICONTROL 상속됨] 옵션이 기본적으로 선택되어 있고 비디오 스마트 태그가 활성화되어 있습니다.

   이 [!UICONTROL 상속됨] 옵션을 선택하면 상속된 폴더 경로가 설정 여부 정보와 함께 표시됩니다 [!UICONTROL 활성화] 또는 [!UICONTROL 비활성화].

   ![비디오 스마트 태그 지정 비활성화](assets/disable-video-tagging.png)

1. 선택 [!UICONTROL 비활성화] 폴더에 업로드된 비디오의 스마트 태그 지정을 옵트아웃하려면 다음을 수행하십시오.

>[!IMPORTANT]
>
>업로드 시 폴더의 비디오 태그 지정을 옵트아웃하고 업로드 후 비디오에 스마트 태그를 지정하려면 **[!UICONTROL 비디오용 스마트 태그 활성화]** 변환 전: [!UICONTROL 자산 처리] 폴더의 탭 [!UICONTROL 속성] 및 [[!UICONTROL 자산 재처리] 옵션](#smart-tag-existing-videos) 를 눌러 비디오에 스마트 태그를 추가합니다.

## 신뢰도 점수 {#confidence-score-video-tag}

[!DNL Adobe Experience Manager] 각 비디오 자산에 대해 태그가 너무 많아 인덱싱이 느려지는 것을 방지하기 위해 개체 및 작업 스마트 태그에 최소 신뢰 임계값을 적용합니다. 자산 검색 결과는 신뢰 점수를 기반으로 등급을 매기고, 일반적으로 비디오 자산의 지정된 태그 검사가 제안하는 것 이상으로 검색 결과를 개선합니다. 부정확한 태그는 신뢰도 점수가 낮아서 자산에 대한 스마트 태그 목록 맨 위에 거의 표시되지 않습니다.

의 작업 및 개체 태그에 대한 기본 임계값 [!DNL Adobe Experience Manager] 는 0.7(0과 1 사이의 값이어야 함)입니다. 일부 비디오 자산에 특정 태그가 지정되어 있지 않은 경우 알고리즘이 예측된 태그에 70% 미만임을 나타냅니다. 기본 임계값이 모든 사용자에게 항상 최적은 아닐 수 있습니다. 따라서 OSGI 구성에서 신뢰 점수 값을 변경할 수 있습니다.

에 배포된 프로젝트에 신뢰 점수 OSGI 구성을 추가하려면 [!DNL Adobe Experience Manager] 로서의 [!DNL Cloud Service] through [!DNL Cloud Manager]:

* 에서 [!DNL Adobe Experience Manager] 프로젝트 (`ui.config` 원형 24 이전 `ui.apps`) `config.author` OSGi 구성, 이름이 인 구성 파일 포함 `com.adobe.cq.assetcompute.impl.senseisdk.SenseiSdkImpl.cfg.json` 다음 내용으로 채우십시오.

```json
{
  "minVideoActionConfidenceScore":0.5,
  "minVideoObjectConfidenceScore":0.5,
}
```

>[!NOTE]
>
>수동 태그에는 100%(최대 신뢰)의 신뢰도가 지정됩니다. 따라서 검색 쿼리와 일치하는 수동 태그가 있는 비디오 자산이 있는 경우 검색 쿼리와 일치하는 스마트 태그 앞에 표시됩니다.

## 제한 사항 {#video-smart-tagging-limitations}

* 특정 비디오를 사용하여 비디오에 스마트 태그를 적용하는 서비스를 교육할 수 없습니다. 기본적으로 작동합니다 [!DNL Adobe Sensei] 설정.

* 태깅 진행 상태가 표시되지 않습니다.

* 파일 크기가 300MB보다 작은 비디오만 자동 태그가 지정됩니다. 다음 [!DNL Adobe Sensei] 서비스에서 크기가 큰 비디오 파일을 건너뜁니다.

* 에 언급된 파일 형식 및 지원되는 코덱의 비디오만 [스마트 태그](/help/assets/smart-tags.md#smart-tags-supported-file-formats) 태그가 지정되어 있습니다.

**추가 참조**

* [에셋 번역](translate-assets.md)
* [Assets HTTP API](mac-api-assets.md)
* [자산 지원 파일 형식](file-format-support.md)
* [에셋 검색](search-assets.md)
* [연결된 자산](use-assets-across-connected-assets-instances.md)
* [에셋 보고서](asset-reports.md)
* [메타데이터 스키마](metadata-schemas.md)
* [에셋 다운로드](download-assets-from-aem.md)
* [메타데이터 관리](manage-metadata.md)
* [검색 패싯](search-facets.md)
* [컬렉션 관리](manage-collections.md)
* [벌크 메타데이터 가져오기](metadata-import-export.md)

>[!MORELIKETHIS]
>
>* [스마트 태그 및 자산 검색 관리](smart-tags.md#manage-smart-tags-and-searches)
>* [스마트 태그 서비스 교육 및 이미지 태그 지정](smart-tags.md)

