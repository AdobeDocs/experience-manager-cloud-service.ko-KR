---
title: Content Hub 사용자 인터페이스 구성
description: Content Hub 사용자 인터페이스 구성
exl-id: e9e22862-9bcd-459a-bcf4-7f376a0b329a
source-git-commit: 96c50aad9368adc83f8698dc35266146b1883672
workflow-type: tm+mt
source-wordcount: '1185'
ht-degree: 5%

---

# Content Hub 사용자 인터페이스 구성 {#configure-content-hub-user-interface}

>[!CONTEXTUALHELP]
>id="configure_content_hub"
>title="Content Hub 사용자 인터페이스 구성"
>abstract="Experience Manager Assets을 사용하면 관리자가 Content Hub 사용자 인터페이스에서 사용할 수 있는 옵션을 구성할 수 있습니다. 관리자가 선택한 구성 옵션에 따라 Content Hub 사용자는 Content Hub의 필드를 볼 수 있습니다. 구성 옵션에는 에셋을 가져오는 동안의 메타데이터, 필터, 에셋 속성, 에셋을 검색하는 동안의 메타데이터, 개인화된 브랜딩 및 모든 사용자 지정 링크가 포함됩니다."

<!-- ![Download assets](assets/download-asset.jpg) -->
![Content Hub에서 자산 구성](assets/configure-assets.png)

Experience Manager Assets을 사용하면 관리자가 Content Hub 사용자 인터페이스에서 사용할 수 있는 옵션을 구성할 수 있습니다. 관리자가 선택한 구성 옵션에 따라 Content Hub 사용자는 Content Hub의 필드를 볼 수 있습니다. 구성 옵션은 다음과 같습니다.

* 에셋을 검색하는 동안 사용자가 사용할 수 있는 필터.

* 각 에셋에 대해 사용할 수 있는 에셋 세부 정보 또는 속성.

* Content Hub에 에셋을 추가하는 동안 사용자가 사용할 수 있는 메타데이터 필드.

* Content Hub에서 검색할 수 있는 에셋 메타데이터 필드입니다.

* 조직에 표시해야 하는 브랜딩 콘텐츠입니다.

* 에셋, 컬렉션 및 인사이트 외에 Content Hub에 포함해야 하는 모든 사용자 지정 링크입니다.

## 사전 요구 사항 {#prerequisites-configuration-ui}

[Content Hub 관리자](/help/assets/deploy-content-hub.md#step-3-onboard-content-hub-administrator)는 조직 내의 다른 사용자에 대한 구성 옵션을 설정할 수 있습니다.

## Content Hub의 구성 옵션 액세스 {#access-configuration-options-content-hub}

Content Hub에서 구성 옵션에 액세스하려면 다음을 수행하십시오.

1. 오른쪽 창에서 사용자 아이콘을 클릭합니다.

1. **[!UICONTROL 제품 설정]** 섹션에서 **[!UICONTROL 구성]**&#x200B;을 선택합니다.

   ![Content Hub에서 구성 옵션 액세스](assets/access-content-hub-configuration-ui.png)

## Content Hub에서 구성 옵션 관리 {#manage-configuration-options}

관리자는 사용자에 대해 다음 구성 옵션을 관리합니다.

* [가져오기](#configure-import-options-content-hub)

* [필터](#configure-filters-content-hub)

* [에셋 세부 정보](#configure-asset-details-content-hub)

* [검색](#configure-metadata-search-content-hub)

* [브랜딩](#configure-branding-content-hub)

* [사용자 정의 링크](#configure-custom-links-content-hub)

### 가져오기 {#configure-import-options-content-hub}

Content Hub 포털에 자산을 업로드하거나 가져오는 동안 사용자에게 표시되는 메타데이터 필드(예: 캠페인 이름, 키워드, 채널, 일정, 지역 등)를 구성할 수 있습니다. 이렇게 하려면 다음 단계를 실행합니다.

1. [구성](#access-configuration-options-content-hub) 사용자 인터페이스에서 **[!UICONTROL 가져오기]**&#x200B;를 클릭합니다.

1. **[!UICONTROL 메타데이터 추가]**&#x200B;를 클릭합니다.

1. 속성에 대한 레이블을 지정하고 **[!UICONTROL 메타데이터]** 필드를 사용하여 속성에 매핑한 다음 새 자산 메타데이터에 대한 입력 유형을 선택합니다.

1. **[!UICONTROL 필수 필드]** 전환을 클릭하여 새 자산을 업로드하는 동안 사용자에 대해 새 메타데이터 필드를 지정해야 합니다.

1. **[!UICONTROL 확인]**&#x200B;을 클릭합니다. 새 메타데이터가 기존 에셋 속성 목록에 표시됩니다.

1. 변경 내용을 적용하려면 **[!UICONTROL 저장]**&#x200B;을 클릭하세요.

마찬가지로, 사용 가능한 각 속성 옆에 있는 ![편집 아이콘](assets/do-not-localize/edit_icon.svg)을 클릭하여 레이블을 편집하거나, **[!UICONTROL 필수 필드]** 전환을 사용하여 에셋을 업로드하는 동안 이러한 필드를 사용자에게 필수 또는 비필수로 설정하거나, 삭제 아이콘을 클릭하여 메타데이터 속성을 삭제할 수 있습니다.

Experience Manager Assets 저장소에 추가하는 모든 자산을 Content Hub에서 즉시 사용할 수 있도록 자동 승인해야 하는 경우 **[!UICONTROL 자동 승인]** 전환을 클릭합니다. 그렇지 않으면 DAM 작성자 또는 관리자가 Content Hub에서 사용할 수 있도록 에셋을 수동으로 승인해야 합니다. 토글(Toggle)은 기본적으로 꺼짐(Off) 상태로 설정됩니다.

변경 사항을 적용하려면 모든 수정 작업을 수행한 후 **[!UICONTROL 저장]**&#x200B;을 클릭하세요.

![Content Hub의 구성 UI 업로드 세부 정보](assets/configuration-ui-upload-details.png)

구성 사용자 인터페이스에서 활성화된 메타데이터는 에셋 업로드 페이지에 표시됩니다.

![Content Hub에서 메타데이터 업로드](assets/configuration-ui-add-assets.png)

### 필터 {#configure-filters-content-hub}

Content Hub을 사용하면 관리자가 에셋을 검색하는 동안 표시되는 필터를 구성할 수 있습니다. 다음 단계를 실행하여 새 필터를 추가합니다.

1. [구성](#access-configuration-options-content-hub) 사용자 인터페이스에서 **[!UICONTROL 필터]**&#x200B;를 클릭합니다.

1. **[!UICONTROL 필터 추가]**&#x200B;를 클릭합니다.

1. 필터에 대한 레이블을 지정하고, **[!UICONTROL 메타데이터]** 필드를 사용하여 해당 레이블을 속성에 매핑한 다음 새 필터에 대한 입력 유형을 선택하십시오.
1. **[!UICONTROL 확인]**&#x200B;을 클릭합니다. 새 필터가 기존 필터 목록에 표시됩니다.

1. 자산을 필터링하는 동안 검색 페이지에 새 필터가 표시되도록 변경 내용을 적용하려면 **[!UICONTROL 저장]**&#x200B;을 클릭하십시오.

   >[!NOTE]
   >
   >저장소에 필터 조건과 일치하는 에셋이 하나 이상 있는 경우에만 새 필터가 검색 페이지에 표시됩니다.

마찬가지로 사용 가능한 각 필터 옆에 있는 ![편집 아이콘](assets/do-not-localize/edit_icon.svg)을 클릭하여 레이블을 편집하거나 삭제 아이콘을 클릭하여 기존 필터를 삭제할 수 있습니다. 변경 사항을 적용하려면 모든 수정 작업을 수행한 후 **[!UICONTROL 저장]**&#x200B;을 클릭하세요.

![Content Hub의 구성 UI 필터](assets/configuration-ui-filters.png)

구성 사용자 인터페이스에서 활성화된 필터가 [검색] 페이지에 표시됩니다.

![Content Hub에서 검색](assets/filters-for-search.png)


### 에셋 세부 정보 {#configure-asset-details-content-hub}

파일 이름, 제목, 형식, 크기 등과 같은 각 에셋에 대해 표시되는 에셋 속성을 구성할 수도 있습니다. 이렇게 하려면 다음 단계를 실행합니다.

1. [구성](#access-configuration-options-content-hub) 사용자 인터페이스에서 **[!UICONTROL 자산 세부 정보]**&#x200B;를 클릭합니다.

1. **[!UICONTROL 메타데이터 추가]**&#x200B;를 클릭합니다.

1. 속성에 대한 레이블을 지정하고 **[!UICONTROL 메타데이터]** 필드를 사용하여 속성에 매핑한 다음 새 자산 메타데이터에 대한 입력 유형을 선택합니다.
1. **[!UICONTROL 확인]**&#x200B;을 클릭합니다. 새 메타데이터가 기존 에셋 속성 목록에 표시됩니다.

1. **[!UICONTROL 저장]**&#x200B;을 클릭하여 새 속성이 자산 세부 정보 페이지에 표시되도록 변경 내용을 적용합니다.

마찬가지로 사용 가능한 각 속성 옆에 있는 ![편집 아이콘](assets/do-not-localize/edit_icon.svg)을 클릭하여 레이블을 편집하거나 삭제 아이콘을 클릭하여 기존 에셋 세부 정보를 삭제할 수 있습니다. 변경 사항을 적용하려면 모든 수정 작업을 수행한 후 **[!UICONTROL 저장]**&#x200B;을 클릭하세요.

![Content Hub의 구성 UI 자산 세부 정보](assets/configuration-ui-asset-details.png)

구성 사용자 인터페이스에서 활성화된 속성이 [자산 세부 정보] 페이지에 표시됩니다.

![Content Hub의 자산 속성](assets/config-ui-asset-properties.png)

### 검색 {#configure-metadata-search-content-hub}

관리자는 사용자가 Content Hub에서 검색 기준을 지정할 때 검색되는 메타데이터 필드를 정의할 수 있습니다. 다음 단계를 실행합니다.

1. [구성](#access-configuration-options-content-hub) 사용자 인터페이스에서 **[!UICONTROL 메타데이터 추가]**&#x200B;를 클릭합니다.

1. 메타데이터 필드를 지정하고 **[!UICONTROL 확인]**&#x200B;을 클릭합니다.

1. 새 메타데이터 속성이 메타데이터 필드 목록에 표시되도록 변경 사항을 적용하려면 **[!UICONTROL 저장]**&#x200B;을 클릭하십시오.

마찬가지로 사용 가능한 각 메타데이터 속성 옆에 있는 ![편집 아이콘](assets/do-not-localize/edit_icon.svg)을 클릭하여 속성을 편집하거나 삭제 아이콘을 클릭하여 기존 속성을 삭제할 수 있습니다. 변경 사항을 적용하려면 모든 수정 작업을 수행한 후 **[!UICONTROL 저장]**&#x200B;을 클릭하세요.

![Content Hub에서 구성 UI 검색](assets/configuration-ui-metadata-search.png)


### 브랜딩 {#configure-branding-content-hub}

관리자는 또한 브랜딩 요구 사항에 따라 Content Hub 포털 배너에서 제목과 본문을 개인화할 수 있습니다. 이렇게 하려면 다음 단계를 실행합니다.

1. [구성](#access-configuration-options-content-hub) 사용자 인터페이스에서 **[!UICONTROL 브랜딩]**&#x200B;을(를) 클릭합니다.

1. **[!UICONTROL 배너의 제목 텍스트]** 및 **[!UICONTROL 배너의 본문 텍스트]** 필드에 텍스트를 지정합니다.

1. 변경 내용을 적용하려면 **[!UICONTROL 저장]**&#x200B;을 클릭하세요.

![Content Hub의 구성 UI 브랜딩](assets/configuration-ui-branding.png)

구성 사용자 인터페이스에서 활성화된 브랜딩 업데이트가 Content Hub 포털 배너에 표시됩니다.

![Content Hub의 구성 UI 브랜딩](assets/configuration-ui-branding-updates.png)

### 사용자 정의 링크 {#configure-custom-links-content-hub}

배너 바로 아래에 있는 Content Hub 포털에서 표준 **[!UICONTROL 모든 Assets]**, **[!UICONTROL 컬렉션]** 및 **[!UICONTROL 인사이트]** 탭 외에 사용자 지정 탭을 추가할 수도 있습니다. 이렇게 하려면 다음 단계를 실행합니다.

1. [구성](#access-configuration-options-content-hub) 사용자 인터페이스에서 **[!UICONTROL 사용자 지정 링크]**&#x200B;를 클릭합니다.

1. **[!UICONTROL 링크 추가]**&#x200B;를 클릭합니다.

1. **[!UICONTROL 레이블]** 및 **[!UICONTROL URL]** 필드에 텍스트를 지정하십시오. 정의한 레이블은 탭으로 표시되고 레이블을 클릭하면 **[!UICONTROL URL]** 필드에 정의된 URL로 이동합니다.

1. **[!UICONTROL 확인]**&#x200B;을 클릭합니다.

1. 변경 내용을 적용하려면 **[!UICONTROL 저장]**&#x200B;을 클릭하세요.

마찬가지로 각 URL 옆에 있는 ![편집 아이콘](assets/do-not-localize/edit_icon.svg)을 클릭하여 링크를 편집하거나 삭제 아이콘을 클릭하여 기존 URL을 삭제할 수 있습니다. 변경 사항을 적용하려면 모든 수정 작업을 수행한 후 **[!UICONTROL 저장]**&#x200B;을 클릭하세요.

![Content Hub의 구성 UI 사용자 지정 링크](assets/configuration-ui-custom-links.png)

사용자 지정 링크는 Content Hub 홈 페이지의 Insights 탭 옆에 새 탭으로 표시됩니다.

![Content Hub의 구성 UI 사용자 지정 링크 탭](assets/configuration-ui-custom-link-tab.png)
