---
title: ' [!DNL Adobe Experience Manager] as a [!DNL Cloud Service]용 자산 선택기'
description: 에셋 선택기를 사용하여 애플리케이션 내에서 에셋의 메타데이터와 렌디션을 검색, 찾기 및 검색할 수 있습니다.
role: Admin,User
source-git-commit: fb1350c91468f9c448e34b66dc938fa3b5a3e9a9
workflow-type: tm+mt
source-wordcount: '505'
ht-degree: 1%

---


# 파일 및 폴더를 자산 선택기에 업로드 {#upload-files-folders}

로컬 파일 시스템에서 파일 또는 폴더를 에셋 선택기에 업로드할 수 있습니다. 로컬 파일 시스템을 사용하여 파일을 업로드하려면 일반적으로 자산 선택기 마이크로 프론트엔드 애플리케이션에서 제공하는 업로드 기능을 사용해야 합니다.

## 로컬 파일 시스템에서 에셋 업로드 {#basic-upload}

에셋 선택기에 에셋을 추가하려면 다음 단계를 수행하십시오.

1. 레일 보기를 사용하는 경우 줄임표로 이동한 다음 ![업로드 아이콘](assets/upload-icon.svg) **[!UICONTROL 업로드]**&#x200B;를 클릭합니다. 반면 모달 보기의 경우 오른쪽 상단에서 ![업로드 아이콘](assets/upload-icon.svg) **[!UICONTROL 업로드]**&#x200B;를 클릭합니다. [!UICONTROL Assets 업로드] 화면이 나타납니다.

   ![자산 선택기에 자산 업로드](assets/upload-assets.png)

   또한 **[!UICONTROL 파일 또는 폴더를 여기로 드래그]** 섹션에서 로컬 파일 시스템에서 자산을 드래그하거나 **[!UICONTROL 찾아보기]**&#x200B;를 클릭하여 로컬 파일 시스템에서 사용할 수 있는 파일 또는 폴더를 수동으로 선택할 수 있습니다. 업로드의 일부인 이 파일 목록은 목록으로 사용할 수 있습니다.

   ![자산 선택기에 자산 기본 업로드](assets/basic-upload.png)

   썸네일을 사용하여 선택한 이미지를 미리 보고 X 아이콘을 클릭하여 목록에서 특정 이미지를 제거할 수도 있습니다. X 아이콘은 마우스로 이미지 이름이나 크기를 가리키면 표시됩니다. **[!UICONTROL 모두 제거]**&#x200B;를 클릭하여 업로드 목록에서 모든 항목을 삭제할 수도 있습니다.

1. 업로드 프로세스를 완료하려면 **[!UICONTROL 업로드]**&#x200B;를 클릭하세요. 업로드한 에셋이 표시됩니다. 구성 가능한 코드는 [기본 업로드](asset-selector-customization.md#basic-upload)를 참조하십시오.

## 메타데이터를 사용하여 에셋 업로드 {#upload-assets-with-metadata}

애플리케이션에 즉시 업로드하면서 에셋에 메타데이터를 추가할 수 있습니다. 메타데이터에는 비즈니스 제목 줄, 제품 세부 사항, 캠페인 등과 같은 다양한 필드가 포함됩니다. 이를 위해 `metadataSchema` 속성이 사용됩니다. `metadataSchema` 속성에 대해 자세히 알아보려면 [자산 선택기 속성](asset-selector-properties.md)(으)로 이동하십시오.

구성에 필요한 코드 조각에 대해서는 [메타데이터로 업로드](#upload-with-metadata)를 참조하십시오.

![메타데이터가 있는 에셋 업로드](assets/upload-with-metadata.png)

1. **[!UICONTROL 캠페인 이름]** 필드를 사용하여 업로드의 이름을 정의합니다. 기존 이름을 사용하거나 새 이름을 만들 수 있습니다. 에셋 선택기는 이름을 입력할 때 더 많은 옵션을 제공합니다.

   업로드한 에셋에 대해 향상된 Adobe 경험을 만들 뿐만 아니라 나머지 필드에 값을 지정하는 것이 좋습니다.

1. 마찬가지로 **[!UICONTROL 키워드]**, **[!UICONTROL 채널]**, **[!UICONTROL 일정]** 및 **[!UICONTROL 지역]** 필드에 대한 값을 정의하십시오. 키워드, 채널 및 위치별로 자산에 태그를 지정하고 그룹화하면 승인된 회사 콘텐츠를 사용하는 모든 사람이 이러한 자산을 찾아 체계적으로 관리할 수 있습니다.

1. 자산을 자산 선택기에 업로드하려면 **[!UICONTROL 업로드]**&#x200B;를 클릭하십시오. [!UICONTROL 세부 정보 검토] 확인 상자가 나타납니다. [!UICONTROL 계속]을 클릭합니다.

1. Assets 업로드를 시작합니다. 업로드 절차를 다시 시작하려면 [!UICONTROL 새 업로드]를 클릭하십시오. 업로드를 완료하려면 [!UICONTROL 완료]를 클릭하십시오.


## 사용자 지정된 업로드 {#customize-upload}

에셋 선택기를 사용하면 사용자 지정된 업로드 양식을 추가할 수 있습니다. 사용할 수 있는 몇 가지 사용자 지정 사항이 있습니다. 예를 들어 [hideUploadButton](#asset-selector-properties.md) 속성을 사용하면 응용 프로그램에 기본적으로 표시되는 업로드 단추를 숨길 수 있습니다. 대신 요구 사항에 따라 MFE 애플리케이션 외부에서 렌더링하도록 사용자 지정할 수 있습니다. 구성에 대해서는 [사용자 지정된 업로드](#asset-selector-customization.md#customized-upload)를 참조하십시오.

![사용자 지정된 업로드](assets/customized-upload.png)

