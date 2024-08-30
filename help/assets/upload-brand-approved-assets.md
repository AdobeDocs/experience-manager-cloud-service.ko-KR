---
title: ' [!DNL Content Hub]에 브랜드 승인 에셋 업로드'
description: 브랜드 승인 에셋을 Content Hub에 업로드하는 방법을 알아봅니다.
role: User
exl-id: f1be7cfc-1803-4c17-bb58-947104aa883c
source-git-commit: 85fbbcf77bd5b2ef1a68454e2cf1d2202c8f90c4
workflow-type: tm+mt
source-wordcount: '895'
ht-degree: 0%

---

# Content Hub에 브랜드 승인 에셋 업로드 {#upload-brand-approved-assets-content-hub}

자산을 추가할 권한이 있는 [Content Hub 사용자](/help/assets/deploy-content-hub.md#onboard-content-hub-users-add-assets)는 로컬 파일 시스템에서 Content Hub에 자산을 추가하거나 OneDrive 또는 Dropbox 데이터 원본에서 자산을 가져올 수 있습니다. 모든 에셋은 로컬 파일 시스템에서 사용할 수 있는 폴더 구조 또는 OneDrive 및 Dropbox 데이터 소스와 관계없이 Content Hub의 최상위 수준에 표시되어 검색 기능을 향상시킵니다.

Assetsas a Cloud Service 에 `Approved`(으)로 표시된 자산은 Content Hub에서 자동으로 사용할 수 있습니다. 자세한 내용은 [Content Hub에 대한 자산 승인](/help/assets/approve-assets-content-hub.md)을 참조하세요.

Content Hub을 사용하면 에셋 검색을 더욱 향상시킬 수 있습니다.

* 캠페인 이름, 키워드, 채널 등과 같은 자산 업로드와 관련된 주요 세부 정보를 정의합니다.

* 업로드 성공 시 파일 크기, 형식, 해상도 및 기타 속성과 같은 각 에셋에 대한 추가 속성을 자동으로 생성합니다.

* [Adobe Sensei](https://www.adobe.com/kr/sensei.html)에서 제공하는 인공 지능을 사용하여 업로드된 모든 에셋에 관련 태그를 자동으로 적용합니다. 스마트 태그라고 명명된 이들 태그는 관련 에셋을 빠르게 찾을 수 있도록 지원하여 프로젝트의 콘텐츠 속도를 높입니다.

[브랜드 승인 자산만 Content Hub](/help/assets/approve-assets.md)에 업로드하는지 확인하십시오.

![브랜드 승인 에셋 업로드](assets/upload-brand-approved-assets.png)

## 사전 요구 사항 {#prerequisites-add-assets}

자산을 추가할 수 있는 권한이 있는 [Content Hub 사용자](/help/assets/deploy-content-hub.md#onboard-content-hub-users-add-assets)가 Content Hub에 자산을 업로드할 수 있습니다.

## 로컬 파일 시스템에서 Content Hub에 자산 추가 {#add-assets-local-file-system}

Content Hub에 자산을 추가하려면 다음 단계를 수행하십시오.

1. 업로드를 만들 수 있는 **[!UICONTROL 승인된 에셋 추가]** 대화 상자를 보려면 **[!UICONTROL Assets 추가]**&#x200B;를 클릭하십시오.

1. 오른쪽 창에서 사용할 수 있는 **[!UICONTROL 파일 또는 폴더를 여기로 드래그]** 섹션에서 로컬 파일 시스템에서 자산을 드래그하거나 **[!UICONTROL 찾아보기]**&#x200B;를 클릭하여 로컬 파일 시스템에서 사용할 수 있는 파일 또는 폴더를 수동으로 선택할 수 있습니다. 업로드의 일부인 이 파일 목록은 목록으로 사용할 수 있습니다.


   썸네일을 사용하여 선택한 이미지를 미리 보고 X 아이콘을 클릭하여 목록에서 특정 이미지를 제거할 수도 있습니다. X 아이콘은 마우스로 이미지 이름이나 크기를 가리키면 표시됩니다. **[!UICONTROL 모두 제거]**&#x200B;를 클릭하여 업로드 목록에서 모든 항목을 삭제할 수도 있습니다.

   업로드 프로세스를 완료하고 **[!UICONTROL 업로드 단추]**&#x200B;를 사용하려면 자산을 캠페인 이름으로 그룹화해야 합니다.

   ![Content Hub에 자산 업로드](assets/upload-assets-content-hub.png)

1. **[!UICONTROL 캠페인 이름]** 필드를 사용하여 업로드의 이름을 정의합니다. 기존 이름을 사용하거나 새 이름을 만들 수 있습니다. Content Hub에서는 이름을 입력할 때 더 많은 옵션을 제공합니다. <!--You can define multiple Campaign names for your upload. While you are typing a name, either click anywhere else within the dialog box or press the `,` (Comma) key to register the name.-->

   업로드한 에셋에 대해 향상된 Adobe 경험을 만들 뿐만 아니라 나머지 필드에 값을 지정하는 것이 좋습니다.

1. 마찬가지로 **[!UICONTROL 키워드]**, **[!UICONTROL 채널]**, **[!UICONTROL 일정]** 및 **[!UICONTROL 지역]** 필드에 대한 값을 정의하십시오. 키워드, 채널 및 위치별로 자산에 태그를 지정하고 그룹화하면 승인된 회사 콘텐츠를 사용하는 모든 사람이 이러한 자산을 찾아 체계적으로 관리할 수 있습니다.

1. 자산을 Content Hub에 업로드하려면 **[!UICONTROL 업로드]**&#x200B;를 클릭하십시오. [!UICONTROL 세부 정보 검토] 확인 상자가 나타납니다. [!UICONTROL 계속]을 클릭합니다.

1. Assets 업로드를 시작합니다. 업로드 절차를 다시 시작하려면 [!UICONTROL 새 업로드]를 클릭하십시오. 업로드를 완료하려면 [!UICONTROL 완료]를 클릭하십시오.

또한 관리자는 캠페인 이름, 키워드, 채널 등과 같은 에셋을 업로드하는 동안 표시되는 필수 및 선택 필드를 구성할 수 있습니다. 자세한 내용은 [Content Hub 사용자 인터페이스 구성](configure-content-hub-ui-options.md#configure-upload-options-content-hub)을 참조하십시오.


## OneDrive 또는 Dropbox 데이터 원본에서 Content Hub에 자산 추가 {#add-assets-onedrive-dropbox}

OneDrive 또는 Dropbox 데이터 소스에서 Content Hub에 자산을 추가하려면 다음을 수행합니다.

1. OneDrive 또는 Dropbox에서 에셋을 가져올 수 있는 **[!UICONTROL 승인된 에셋 추가]** 대화 상자를 보려면 **[!UICONTROL Assets 추가]**&#x200B;를 클릭하세요.

1. 가져오기 프로세스를 시작하려면 **[!UICONTROL OneDrive]** 또는 **[!UICONTROL Dropbox]**&#x200B;을 클릭하세요. Content Hub은 OneDrive 또는 Dropbox 계정에 로그온하라는 메시지를 표시한 다음 왼쪽 창에 OneDrive 또는 Dropbox 폴더 구조를 표시합니다.

1. 파일 또는 폴더 이름 옆에 있는 + 아이콘을 클릭하여 선택한 항목 목록에서 항목을 봅니다. Content Hub 포털에 추가해야 하는 모든 파일을 선택한 후 [로컬 파일 시스템에서 Content Hub에 에셋 추가](#add-assets-local-file-system)의 3~6단계를 반복하여 업로드 프로세스를 완료합니다.

   ![OneDrive 또는 Dropbox에서 Content Hub에 자산 업로드](assets/add-assets-onedrive-dropbox.png)

또한 관리자는 캠페인 이름, 키워드, 채널 등과 같은 에셋을 업로드하는 동안 표시되는 필수 및 선택 필드를 구성할 수 있습니다. 자세한 내용은 [Content Hub 사용자 인터페이스 구성](configure-content-hub-ui-options.md#configure-upload-options-content-hub)을 참조하십시오.

## Content Hub을 사용하여 업로드된 에셋 관리 {#manage-assets-uploaded-using-content-hub}

[에셋을 추가할 수 있는 권한이 있는 Content Hub 사용자](/help/assets/deploy-content-hub.md#onboard-content-hub-users-add-assets)는 로컬 파일 시스템에서 [Content Hub에 에셋을 추가](/help/assets/upload-brand-approved-assets.md)하거나 OneDrive 또는 Dropbox 데이터 원본에서 에셋을 가져올 수 있습니다. 모든 에셋은 로컬 파일 시스템에서 사용할 수 있는 폴더 구조 또는 OneDrive 및 Dropbox 데이터 소스와 관계없이 Content Hub의 최상위 수준에 표시되어 검색 기능을 향상시킵니다.

Content Hub을 사용하여 업로드한 에셋의 표시 여부는 [자동 승인 토글](/help/assets/configure-content-hub-ui-options.md#configure-import-options-content-hub)을 활성화했는지 여부에 따라 다릅니다.

* **[!UICONTROL 자동 승인]** 전환이 활성화된 경우 Content Hub을 사용하여 업로드하는 에셋을 자동으로 사용할 수 있습니다.

* **[!UICONTROL 자동 승인]** 전환이 비활성화된 경우 Content Hub을 사용하여 업로드한 자산이 자동으로 표시되지 않습니다. 자산은 Assets as a Cloud Service 환경의 `hydrated-assets` 폴더에서 사용할 수 있습니다. 폴더로 이동한 다음 해당 에셋의 상태를 [일괄 편집](#bulk-approve-assets-content-hub)하여 해당 에셋을 Content Hub에 표시할 수 있도록 `Approved`합니다.

![Content Hub 승인 프로세스](/help/assets/assets/content-hub-approval.png)
