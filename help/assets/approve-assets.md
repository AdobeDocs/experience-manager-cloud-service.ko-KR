---
title: Experience Manager에서 에셋 승인
description: ' [!DNL Experience Manager]에서 자산을 승인하는 방법을 알아봅니다.'
role: User
exl-id: fe61a0f1-94d3-409a-acb9-195979668c25
source-git-commit: 9c1104f449dc2ec625926925ef8c95976f1faf3d
workflow-type: tm+mt
source-wordcount: '1063'
ht-degree: 7%

---

# [!DNL Experience Manager]에서 자산 승인

브랜드 관리자 및 마케터는 브랜드 자산에 대한 엄격한 제어를 유지합니다. 승인된 최신 버전의 자산만 사용할 수 있어 모든 채널과 애플리케이션에서 브랜드 일관성을 보장합니다.

AEM Assets에서 에셋을 승인하여 에셋 관리를 간소화하여 에셋 처리에 대한 통제되고 효율적인 프로세스를 보장할 수 있습니다.

## 시작하기에 앞서 {#pre-requisites}

에셋의 **[!UICONTROL 검토 상태]** 속성을 편집하려면 AEM Assets as a Cloud Service 액세스 권한과 사용 권한이 있어야 합니다.

## 구성

자산을 승인하려면 먼저 관리 보기에서 적용 가능한 메타데이터 스키마를 한 번 업데이트해야 합니다. Assets 보기에 대해 이 구성을 건너뛸 수 있습니다. 메타데이터 스키마를 구성하려면 다음 단계를 따르십시오.

1. **[!UICONTROL 도구]** > **[!UICONTROL Assets]** > **[!UICONTROL 메타데이터 스키마]**&#x200B;로 이동합니다.
1. 적용 가능한 메타데이터 스키마를 선택하고 **[!UICONTROL 편집]**&#x200B;을 클릭합니다. <br>메타데이터 스키마 양식 편집기&#x200B;**가 열리고**&#x200B;[!UICONTROL &#x200B;기본&#x200B;]&#x200B;**탭이 강조 표시됩니다.**
1. 아래로 스크롤하여 **[!UICONTROL 검토 상태]**&#x200B;를 클릭합니다.
1. 오른쪽 패널의 **[!UICONTROL 규칙]** 탭을 클릭합니다.
1. **[!UICONTROL 편집 사용 안 함]**&#x200B;을 선택 취소합니다.
**[!UICONTROL 검토 상태]** 필드가 매핑된 속성을 확인해야 하는 경우 **[!UICONTROL 설정]** 탭으로 이동하여 **[!UICONTROL 속성에 매핑]** 필드에서 `./jcr:content/metadata/dam:status` 값을 확인합니다.
1. 오른쪽의 **[!UICONTROL 양식 작성]** 섹션에서 **[!UICONTROL 드롭다운]** 필드를 양식의 메타데이터 섹션으로 끌어다 놓습니다.
1. 새로 추가한 필드를 클릭한 다음 **[!UICONTROL 설정]** 패널에서 다음 업데이트를 수행합니다.
   1. **[!UICONTROL 필드 레이블]**&#x200B;을(를) _승인 대상_(으)로 변경합니다.
   1. **[!UICONTROL 속성에 매핑]**&#x200B;을(를) _(으)로 업데이트합니다./jcr:content/metadata/dam:activationTarget_.
   1. `contenthub` 및 `delivery`을(를) 옵션 값으로 사용하는 선택 항목을 추가합니다.

   >[!NOTE]
   >
   >Assets 보기를 사용하여 승인 대상을 Content Hub으로 선택하면 에셋을 동일한 조직에 속한 사용자가 Content Hub에서 사용할 수 있습니다. 승인 대상을 전달로 선택하면 모든 사용자가 에셋을 사용할 수 있습니다.

1. **[!UICONTROL 저장]**&#x200B;을 클릭합니다.

>[!NOTE]
>
>에셋 또는 폴더에 다른 기본 스키마가 있는 경우 해당 특정 스키마에서 이 업데이트를 수행해야 합니다.

## 자산 승인 {#approve-assets}

[!DNL Experience Manager Admin view]에서 자산을 승인하려면 다음 단계를 수행하십시오.

1. 자산을 선택하고 상단 창에서 **[!UICONTROL 속성]**&#x200B;을(를) 클릭합니다.
1. **[!UICONTROL 기본]** 탭에서 아래로 스크롤하여 **[!UICONTROL 상태 검토]**&#x200B;를 선택합니다.
1. 검토 상태를 **[!UICONTROL 승인됨]**&#x200B;으로 변경합니다.
   ![이미지](/help/assets/assets/approve-old-ui.png)
1. **[!UICONTROL 저장 및 닫기]**&#x200B;를 클릭합니다.

   >[!VIDEO](https://video.tv.adobe.com/v/3427430)

   마찬가지로 [새 Assets 보기](/help/assets/manage-organize-assets-view.md)를 사용하여 자산을 승인할 수 있습니다.

## 자산 일괄 승인 {#bulk-approve-assets}

여러 에셋을 한 번에 빠르게 승인하여 워크플로를 간소화합니다. 자산을 일괄 승인하여 승인 프로세스를 신속하게 진행할 수 있으므로 시간을 절약하고 생산성을 향상시킬 수 있습니다.
<br>다음 단계에 따라 [!DNL Experience Manager Admin view]에서 대량 자산을 승인하십시오.

1. 작성 환경(https://author-pXXX-eYYY.adobeaemcloud.com)에 폴더를 만듭니다. _XXX_&#x200B;을(를) 프로그램 ID로 바꾸고 _YYY_&#x200B;을(를) Experience Manager의 환경 ID로 바꿉니다.
1. **[!UICONTROL 도구]** > **[!UICONTROL Assets]** > **[!UICONTROL 메타데이터 프로필]**&#x200B;로 이동합니다.
1. 페이지 오른쪽 상단의 **[!UICONTROL 만들기]**&#x200B;를 클릭합니다.
1. 프로필 제목을 추가하고 **[!UICONTROL 만들기]**&#x200B;를 클릭합니다. 메타데이터 프로필이 정상적으로 생성되었습니다.
1. 새로 만든 메타데이터 프로필을 선택하고 **[!UICONTROL 편집 __]**&#x200B;을(를) 클릭합니다. <br>메타데이터 프로필 편집&#x200B;**양식이 열리고**&#x200B;[!UICONTROL 기본&#x200B;]&#x200B;**탭이 강조 표시됩니다.**
1. 오른쪽의 **[!UICONTROL 양식 작성]** 섹션에서 **[!UICONTROL 한 줄 텍스트 필드]**&#x200B;를 양식의 메타데이터 섹션으로 끌어다 놓습니다.
1. 새로 추가한 필드를 클릭한 다음 **[!UICONTROL 설정]** 패널에서 다음 업데이트를 수행합니다.
   1. **[!UICONTROL 필드 레이블]**&#x200B;을(를) _승인된 Assets_(으)로 변경합니다.
   1. **[!UICONTROL 속성에 매핑]**&#x200B;을(를) _(으)로 업데이트합니다./jcr:content/metadata/dam:status_.
   1. 기본값을 _승인됨_(으)로 변경합니다.

1. 오른쪽의 **[!UICONTROL 양식 작성]** 섹션에서 **[!UICONTROL 드롭다운]** 필드를 양식의 메타데이터 섹션으로 끌어다 놓습니다.
1. 새로 추가한 필드를 클릭한 다음 **[!UICONTROL 설정]** 패널에서 다음 업데이트를 수행합니다.
   1. **[!UICONTROL 필드 레이블]**&#x200B;을(를) _승인 대상_(으)로 변경합니다.
   1. **[!UICONTROL 속성에 매핑]**&#x200B;을(를) _(으)로 업데이트합니다./jcr:content/metadata/dam:activationTarget_.
   1. `contenthub` 및 `delivery`을(를) 옵션 값으로 사용하는 선택 항목을 추가합니다.

   >[!NOTE]
   >
   >Assets 보기를 사용하여 승인 대상을 Content Hub으로 선택하면 에셋을 동일한 조직에 속한 사용자가 Content Hub에서 사용할 수 있습니다. 승인 대상을 전달로 선택하면 모든 사용자가 에셋을 사용할 수 있습니다.
1. **[!UICONTROL 저장]**&#x200B;을 클릭합니다.
1. **[!UICONTROL 메타데이터 프로필]** 페이지에서 새로 만든 메타데이터 프로필을 선택합니다.
1. 맨 위의 작업 표시줄에서 **[!UICONTROL 폴더에 메타데이터 프로필 적용]**&#x200B;을 클릭합니다.
1. 승인해야 하는 폴더를 선택하고 **[!UICONTROL 적용]**&#x200B;을 클릭합니다.
   <br> 전체 폴더에 대한 권한이 승인을 위해 설정되었으며 이 폴더에 업로드된 모든 자산이 자동으로 승인됩니다.

   >[!VIDEO](https://video.tv.adobe.com/v/3427431)

>[!NOTE]
> 
>이 접근 방법에서는 폴더에 새로 생성된 에셋을 승인합니다. 폴더의 기존 에셋에 대해서는 해당 에셋을 수동으로 선택하고 승인해야 합니다. <br> 또는 **[!UICONTROL 재처리]** 옵션을 사용하여 메타데이터 프로필의 변경 내용을 이전 에셋에 적용할 수 있습니다.

마찬가지로 Assets 보기에서 폴더 내의 자산을 일괄 승인하려면 다음을 수행합니다.

1. 자산을 선택하고 **[!UICONTROL 일괄 메타데이터 편집]**&#x200B;을 클릭합니다.

1. 오른쪽 창 **[!UICONTROL 속성]** 섹션의 사용 가능한 **[!UICONTROL 상태]** 필드에서 [!UICONTROL 승인됨]을 선택합니다.

   상태를 `Approved`(으)로 선택하고 [OpenAPI 기능이 있는 Dynamic Media](/help/assets/dynamic-media-open-apis-overview.md) 또는 [Content Hub](/help/assets/product-overview.md) 또는 둘 다 Experience Manager Assets에 대해 활성화된 경우 **[!UICONTROL 승인 대상]** 필드에서 사용할 수 있는 `Delivery` 및 `Content Hub` 옵션을 볼 수 있습니다.

   * OpenAPI 기능을 사용하는 Dynamic Media와 Content Hub 모두에서 자산을 사용할 수 있도록 하려면 **[!UICONTROL 배달]**&#x200B;을 선택하세요. Content Hub이 활성화되어 있지 않은 경우 이 옵션을 선택하면 OpenAPI 기능을 사용하는 Dynamic Media에서만 자산을 사용할 수 있습니다.
   * 자산을 Content Hub에서 사용할 수 있도록 하려면 **[!UICONTROL Content Hub]**&#x200B;을(를) 선택하십시오.

   ![승인 상태](/help/assets/assets/approval-status-delivery.png)

   기본 메타데이터 양식을 사용하지 않고 **[!UICONTROL 승인 대상]** 필드를 볼 수 없는 경우 [메타데이터 양식을 편집](/help/assets/metadata-assets-view.md#metadata-forms)하여 **[!UICONTROL 승인 대상]** 필드를 사용 가능한 구성 요소에서 메타데이터 양식으로 드래그하고 **[!UICONTROL 저장]**&#x200B;을 클릭하십시오.

   >[!NOTE]
   >
   >조직 내의 Assets 보기를 사용하여 승인 대상을 `Content Hub`(으)로 선택하면 동일한 조직에 속한 사용자가 Content Hub에서 자산을 사용할 수 있습니다.

1. **[!UICONTROL 저장]**&#x200B;을 클릭합니다.

## 승인된 에셋의 게재 URL 복사 {#copy-delivery-url-approved-assets}

AEM as a Cloud Service 인스턴스에서 [!UICONTROL OpenAPI 기능이 있는 Dynamic Media]를 사용하도록 설정한 경우 저장소의 모든 승인된 에셋에 대한 배달 URL을 사용할 수 있습니다.

저장소 내에서 승인된 에셋에 대한 게재 URL을 복사하려면 다음을 수행합니다.

1. 자산을 선택하고 **[!UICONTROL 세부 정보]**&#x200B;를 클릭합니다.

1. 오른쪽 창에서 사용할 수 있는 Dynamic Media 아이콘을 클릭합니다.

1. **[!UICONTROL Dynamic Media]** 패널에서 사용할 수 있는 **[!UICONTROL Dynamic Media with OpenAPI]**&#x200B;을(를) 선택하십시오.

1. 자산의 배달 URL을 복사하려면 **[!UICONTROL URL 복사]**&#x200B;를 클릭하세요.
   ![동적 렌디션](/help/assets/assets/dm-with-openapi-non-image-assets.png)

   >[!NOTE]
   >
   >승인된 에셋에 대한 게재 URL을 복사하는 옵션은 Assets 보기에서만 사용할 수 있습니다.

Dynamic Media 패널 내에 표시되는 다른 변환에 대한 자세한 내용은 [Dynamic Media 변환 보기 및 다운로드](/help/assets/renditions.md#view-download-dm-renditions)를 참조하십시오.
