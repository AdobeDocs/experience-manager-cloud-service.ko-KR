---
title: Experience Manager에서 에셋 승인
description: ' [!DNL Experience Manager]에서 자산을 승인하는 방법을 알아봅니다.'
role: User
exl-id: fe61a0f1-94d3-409a-acb9-195979668c25
source-git-commit: e3fd0fe2ee5bad2863812ede2a294dd63864f3e2
workflow-type: tm+mt
source-wordcount: '694'
ht-degree: 2%

---

# [!DNL Experience Manager]에서 자산 승인

| [모범 사례 검색](/help/assets/search-best-practices.md) | [메타데이터 모범 사례](/help/assets/metadata-best-practices.md) | [Content Hub](/help/assets/product-overview.md) | [OpenAPI 기능이 있는 Dynamic Media](/help/assets/dynamic-media-open-apis-overview.md) | [AEM Assets 개발자 설명서](https://developer.adobe.com/experience-cloud/experience-manager-apis/) |
| ------------- | --------------------------- |---------|----|-----|

브랜드 관리자 및 마케터는 브랜드 자산에 대한 엄격한 제어를 유지합니다. 모든 채널 및 애플리케이션에서 브랜드 일관성을 보장하기 위해 승인된 최신 버전의 자산만 사용할 수 있습니다.

AEM Assets에서 에셋을 승인하여 에셋 관리를 간소화하여 에셋 처리에 대한 통제되고 효율적인 프로세스를 보장할 수 있습니다.

## 시작하기에 앞서 {#pre-requisites}

에셋의 **[!UICONTROL 상태 검토]** 속성을 편집하려면 AEM Assets as a Cloud Service 액세스 권한과 사용 권한이 있어야 합니다.

## 구성

자산을 승인하려면 먼저 관리 보기에서 적용 가능한 메타데이터 스키마를 한 번 업데이트해야 합니다. Assets 보기에 대해 이 구성을 건너뛸 수 있습니다. 메타데이터 스키마를 구성하려면 다음 단계를 따르십시오.

1. **[!UICONTROL 도구]** > **[!UICONTROL Assets]** > **[!UICONTROL 메타데이터 스키마]**&#x200B;로 이동합니다.
1. 적용 가능한 메타데이터 스키마를 선택하고 **[!UICONTROL 편집]**&#x200B;을 클릭합니다. <br>메타데이터 스키마 양식 편집기&#x200B;]**가 열리고**[!UICONTROL &#x200B;기본&#x200B;]**탭이 강조 표시됩니다.**[!UICONTROL 
1. 아래로 스크롤하여 **[!UICONTROL 검토 상태]**&#x200B;를 클릭합니다.
1. 오른쪽 패널의 **[!UICONTROL 규칙]** 탭을 클릭합니다.
1. **[!UICONTROL 편집 비활성화]**&#x200B;를 선택 취소하고 **[!UICONTROL 저장]**을 클릭합니다.
**[!UICONTROL 검토 상태]** 필드가 매핑된 속성을 확인해야 하는 경우 **[!UICONTROL 설정]** 탭으로 이동하여 **[!UICONTROL 속성에 매핑]** 필드에서 `./jcr:content/metadata/dam:status` 값을 확인합니다.

>[!NOTE]
>
>에셋 또는 폴더에 다른 기본 스키마가 있는 경우 해당 특정 스키마에서 이 업데이트를 수행해야 합니다.

## 자산 승인 {#approve-assets}

[!DNL Experience Manager Admin view]에서 자산을 승인하려면 다음 단계를 수행하십시오.

1. 자산을 선택하고 상단 창에서 **[!UICONTROL 속성]**&#x200B;을(를) 클릭합니다.
1. **[!UICONTROL 기본]** 탭에서 **[!UICONTROL 검토 상태]**(으)로 스크롤합니다.
1. 검토 상태를 **[!UICONTROL 승인됨]**(으)로 변경합니다.
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
>이 접근 방법에서는 폴더에 새로 생성된 에셋을 승인합니다. 폴더의 기존 에셋에 대해서는 해당 에셋을 수동으로 선택하고 승인해야 합니다. <br> 또는 **[!UICONTROL 재처리]** 옵션을 사용하여 메타데이터 프로필의 변경 내용을 이전 에셋에 적용할 수 있습니다.

마찬가지로 Assets 보기에서 폴더 내의 자산을 일괄 승인하려면 다음을 수행합니다.

1. 자산을 선택하고 **[!UICONTROL 일괄 메타데이터 편집]**&#x200B;을 클릭합니다.

1. 오른쪽 창의 [!UICONTROL 속성] 섹션에 있는 **[!UICONTROL 상태]** 필드에서 **[!UICONTROL 승인됨]**&#x200B;을(를) 선택합니다.

1. **[!UICONTROL 저장]**&#x200B;을 클릭합니다.

## 승인된 에셋의 게재 URL 복사 {#copy-delivery-url-approved-assets}

AEM as a Cloud Service 인스턴스에서 [!UICONTROL OpenAPI 기능이 있는 Dynamic Media]을(를) 사용하도록 설정한 경우 저장소의 모든 승인된 에셋에 대한 배달 URL을 사용할 수 있습니다.

저장소 내에서 승인된 에셋에 대한 게재 URL을 복사하려면 다음을 수행합니다.

1. 자산을 선택하고 **[!UICONTROL 세부 정보]**&#x200B;를 클릭합니다.

1. 오른쪽 창에서 사용할 수 있는 렌디션 아이콘을 클릭합니다.

1. **[!UICONTROL 동적]** 섹션에서 사용할 수 있는 **[!UICONTROL OpenAPI가 있는 Dynamic Media]**&#x200B;을(를) 선택하십시오.

1. 자산의 배달 URL을 복사하려면 **[!UICONTROL URL 복사]**를 클릭하세요.
   ![배달 URL 복사](/help/assets/assets/copy-delivery-url.png)

   >[!NOTE]
   >
   >승인된 에셋에 대한 게재 URL을 복사하는 옵션은 Assets 보기에서만 사용할 수 있습니다.
