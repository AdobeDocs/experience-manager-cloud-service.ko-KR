---
title: Content Hub에 대한 자산 승인
description: Assetsas a Cloud Service 에서 자산을 승인하여 Content Hub에서 사용할 수 있도록 하는 방법을 알아봅니다.
exl-id: fc849028-ab56-4388-b8d6-e36cac8f868f
source-git-commit: 189fc257fed1115f66559d0f9063885ae527a0fa
workflow-type: tm+mt
source-wordcount: '746'
ht-degree: 6%

---

# Content Hub에 대한 자산 승인 {#approve-assets-content-hub}

| [모범 사례 검색](/help/assets/search-best-practices.md) | [메타데이터 모범 사례](/help/assets/metadata-best-practices.md) | [Content Hub](/help/assets/product-overview.md) | [OpenAPI 기능 포함 Dynamic Media](/help/assets/dynamic-media-open-apis-overview.md) | [AEM Assets 개발자 설명서](https://developer.adobe.com/experience-cloud/experience-manager-apis/) |
| ------------- | --------------------------- |---------|----|-----|

![Content Hub에 대한 자산 승인](assets/content-hub-approve-assets.png)

브랜드 관리자 및 마케터는 브랜드 자산에 대한 엄격한 제어를 유지합니다. Content Hub 내에서는 승인된 최신 버전의 자산만 사용할 수 있으므로 모든 채널 및 애플리케이션에서 브랜드 일관성이 보장됩니다.

AEM Assetsas a Cloud Service 를 사용하여 자산을 승인하여 자산 관리를 간소화할 수 있으므로 자산 처리를 위한 프로세스를 효율적으로 수행할 수 있습니다.

## 시작하기에 앞서 {#pre-requisites}

시작하기 전에 다음을 수행해야 합니다.

* AEM Assets as a Cloud Service 액세스

* 에셋에 대한 [에셋 속성](/help/assets/manage-organize-assets-view.md##manage-asset-status)에서 사용할 수 있는 **[!UICONTROL 상태]** 필드를 편집할 수 있도록 에셋 메타데이터를 편집할 수 있는 쓰기 권한입니다.

## Content Hub에 대한 자산 승인{#approve-assets-for-content-hub}

Assetsas a Cloud Service 에 `approved`(으)로 표시된 자산은 Content Hub에서 자동으로 사용할 수 있습니다.

>[!NOTE]
>
>Assets as a Cloud Service Content Hub에 표시하려면 Content Hub과 동일한 조직을 사용해야 합니다.

AEM as a Cloud Service 내의 Assets 보기를 사용하여 에셋 상태를 `approved`(으)로 설정하려면 다음을 수행하십시오.

1. 자산을 선택하고 도구 모음에서 **[!UICONTROL 세부 정보]**&#x200B;를 클릭합니다.

1. **[!UICONTROL 기본]** 탭의 **[!UICONTROL 상태]** 드롭다운 목록에서 자산 상태를 `approved`(으)로 선택합니다.
1. **[!UICONTROL 저장]**&#x200B;을 클릭합니다.

   >[!VIDEO](https://video.tv.adobe.com/v/3433172)

관리자 보기를 사용하여 자산을 승인해야 하는 경우 [관리자 보기를 사용하여 자산 승인](/help/assets/approve-assets.md#approve-assets)을 참조하십시오.

## Assets 보기를 사용하여 Content Hub에 대한 자산 일괄 승인 {#bulk-approve-assets-content-hub}

AEM Assetsas a Cloud Service 용 Assets 보기를 사용하여 자산을 일괄 승인합니다. 일괄 승인된 모든 에셋을 Content Hub에서 사용할 수 있습니다.

Assets 보기에서 폴더 내의 자산을 일괄 승인하려면 다음을 수행하십시오.

1. 자산을 선택하고 **[!UICONTROL 일괄 메타데이터 편집]**&#x200B;을 클릭합니다.

1. 오른쪽 창의 [!UICONTROL 속성] 섹션에 있는 **[!UICONTROL 상태]** 필드에서 **[!UICONTROL 승인됨]**&#x200B;을(를) 선택합니다.

1. **[!UICONTROL 저장]**&#x200B;을 클릭합니다.

## 관리자 보기에서 새로 수집된 자산에 대한 승인 자동화 {#automate-approval-newly-ingested-assets}

Assets 보기에서 관리자 보기로 전환한 후 폴더에 추가된 모든 새 자산이 자동으로 승인되도록 폴더 설정을 지정할 수 있습니다.

다음과 같은 방법으로 관리 보기와 Assets 보기 간에 전환할 수 있습니다.
![내 Workspace 개요](assets/assets-view.png)

[!DNL Experience Manager Admin view]에서 새로 수집된 자산에 대한 승인을 자동화하려면 다음 단계를 따르십시오.

1. 작성 환경(https://author-pXXX-eYYY.adobeaemcloud.com)에 폴더를 만듭니다. _XXX_&#x200B;을(를) 프로그램 ID로 바꾸고 _YYY_&#x200B;을(를) Experience Manager의 환경 ID로 바꿉니다.
1. **[!UICONTROL 도구]** > **[!UICONTROL Assets]** > **[!UICONTROL 메타데이터 프로필]**&#x200B;로 이동합니다.
1. 페이지 오른쪽 상단의 **[!UICONTROL 만들기]**&#x200B;를 클릭합니다.
1. 프로필 제목을 추가하고 **[!UICONTROL 만들기]**&#x200B;를 클릭합니다. 메타데이터 프로필이 정상적으로 생성되었습니다.
1. 새로 만든 메타데이터 프로필을 선택하고 **[!UICONTROL 편집 __]**을(를) 클릭합니다. <br>메타데이터 프로필 편집&#x200B;]**양식이 열리고**[!UICONTROL 기본&#x200B;]**탭이 강조 표시됩니다.**[!UICONTROL 
1. 오른쪽의 **[!UICONTROL 양식 작성]** 섹션에서 **[!UICONTROL 한 줄 텍스트 필드]**&#x200B;를 양식의 메타데이터 섹션으로 끌어다 놓습니다.
1. 새로 추가한 필드를 클릭한 다음 **[!UICONTROL 설정]** 패널에서 다음 업데이트를 수행합니다.
   1. **[!UICONTROL 필드 레이블]**&#x200B;을(를) _승인된 Assets_(으)로 변경합니다.
   1. **[!UICONTROL 속성에 매핑]**&#x200B;을(를) _(으)로 업데이트합니다./jcr:content/metadata/dam:status_.
   1. 기본값을 _승인됨_(으)로 변경합니다.

1. **[!UICONTROL 저장]**&#x200B;을 클릭합니다.
1. **[!UICONTROL 메타데이터 프로필]** 페이지에서 새로 만든 메타데이터 프로필을 선택합니다.
1. 맨 위의 작업 표시줄에서 **[!UICONTROL 폴더에 메타데이터 프로필 적용]**&#x200B;을 클릭합니다.
1. 승인해야 하는 폴더를 선택하고 **[!UICONTROL 적용]**을 클릭합니다.
   <br> 전체 폴더에 대한 권한이 승인을 위해 설정되었으며 이 폴더에 업로드된 모든 자산이 자동으로 승인됩니다.

   >[!VIDEO](https://video.tv.adobe.com/v/3427431)

>[!NOTE]
> 
>이 접근 방법에서는 폴더에 새로 생성된 에셋을 승인합니다. 폴더의 기존 에셋에 대해서는 해당 에셋을 수동으로 선택하고 승인해야 합니다.

## Content Hub을 사용하여 업로드된 에셋 관리 {#manage-assets-uploaded-using-content-hub}

[에셋을 추가할 수 있는 권한이 있는 Content Hub 사용자](/help/assets/deploy-content-hub.md#onboard-content-hub-users-add-assets)는 로컬 파일 시스템에서 [Content Hub에 에셋을 추가](/help/assets/upload-brand-approved-assets.md)하거나 OneDrive 또는 Dropbox 데이터 원본에서 에셋을 가져올 수 있습니다. 모든 에셋은 로컬 파일 시스템에서 사용할 수 있는 폴더 구조 또는 OneDrive 및 Dropbox 데이터 소스와 관계없이 Content Hub의 최상위 수준에 표시되어 검색 기능을 향상시킵니다.

Content Hub을 사용하여 업로드한 에셋의 표시 여부는 [자동 승인 토글](/help/assets/configure-content-hub-ui-options.md#configure-import-options-content-hub)을 활성화했는지 여부에 따라 다릅니다.

* **[!UICONTROL 자동 승인]** 전환이 활성화된 경우 Content Hub을 사용하여 업로드하는 에셋을 자동으로 사용할 수 있습니다.

* **[!UICONTROL 자동 승인]** 전환이 비활성화된 경우 Content Hub을 사용하여 업로드한 자산이 자동으로 표시되지 않습니다. 자산은 Assets as a Cloud Service 환경의 `hydrated-assets` 폴더에서 사용할 수 있습니다. 폴더로 이동한 다음 해당 에셋의 상태를 [일괄 편집](#bulk-approve-assets-content-hub)하여 해당 에셋을 Content Hub에 표시할 수 있도록 `Approved`합니다.

![Content Hub 승인 프로세스](/help/assets/assets/content-hub-approval.png)
