---
title: AEM Forms 인스턴스에서 적응형 Forms 또는 PDF forms을 가져오고 내보내고 구성하는 방법
description: 적응형 Forms, PDF forms, 테마 및 기타 지원 자산을 AEM 인스턴스로/에서 마이그레이션하는 방법에 대해 알아봅니다.
topic-tags: forms-manager
role: Admin, User
feature: Adaptive Forms
exl-id: f5105fb7-b8c0-4656-8095-b21d392746c0
source-git-commit: 6f547bd743932d45e45e0a3c47ff5eb2129cb664
workflow-type: tm+mt
source-wordcount: '1073'
ht-degree: 3%

---



| 버전 | 문서 링크 |
| -------- | ---------------------------- |
| AEM 6.5 | [여기 클릭](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/forms/manage-administer-aem-forms/import-export-forms-templates) |
| AEM as a Cloud Service | 이 문서 |

# 적응형 Forms 및 AEM Forms 에셋 가져오기 또는 내보내기 {#importing-and-exporting-assets-to-aem-forms}

다음 작업 간에 적응형 Forms 및 적응형 양식 테마, FDM(양식 데이터 모델), 적응형 양식 템플릿, 조각, PDF forms과 같은 관련 에셋을 이동할 수 있습니다. [!DNL AEM Forms] 인스턴스.

## 적응형 Forms, PDF forms 또는 관련 에셋 다운로드 {#download-forms-amp-documents-assets}

양식 또는 관련 에셋을 다운로드하려면 다음 작업을 수행하십시오.

1. 에 로그인 [!DNL Experience Manager Forms] 인스턴스.
1. 선택 **[!UICONTROL Forms]** > **[!UICONTROL Forms 및 문서]**.

   ![Forms 선택](/help/forms/assets/select-forms.png)

1. 에셋을 선택하고 **[!UICONTROL 다운로드]** 아이콘 을 클릭합니다.

   ![Forms 다운로드](/help/forms/assets/download-form.png)

   양식을 다운로드할 때 **[!UICONTROL 자산 다운로드]** 대화 상자가 나타납니다.

   ![양식 에셋 다운로드](/help/forms/assets/download-form-assets.png)

1. **[!UICONTROL 다운로드]**&#x200B;를 클릭합니다.

선택한 자산은 아카이브(.zip 파일)로 다운로드됩니다.

## 적응형 Forms, PDF forms 또는 관련 에셋 업로드 {#upload-forms-amp-documents-assets}

지원되는 에셋 유형을 개별적으로 또는 ZIP 아카이브로 업로드할 수 있습니다. ZIP 파일의 경우 지원되는 모든 에셋의 상대 경로가 표시됩니다. ZIP 내에서 지원되지 않는 에셋은 무시되고 나열되지 않습니다. 그러나 ZIP 아카이브에 지원되지 않는 자산만 포함된 경우 팝업 대화 상자 대신 오류 메시지가 표시됩니다.
양식 또는 관련 에셋을 업로드하려면:

1. 에 로그인 [!DNL Experience Manager Forms] 인스턴스.
1. 선택 **[!UICONTROL Forms]** > **[!UICONTROL Forms 및 문서]**.

   ![Forms 선택](/help/forms/assets/select-forms.png)

1. 선택 **[!UICONTROL 만들기]** > **[!UICONTROL 파일 업로드]**. 대화 상자가 나타납니다.

   ![Forms 업로드](/help/forms/assets/form-upload.png)

1. 대화 상자에서 가져올 패키지 또는 아카이브를 찾아 선택합니다. 지원되는 다른 파일 유형을 선택할 수도 있습니다. 선택 **[!UICONTROL 열기]**. 선택한 폴더 또는 파일 이름에는 특수 문자가 포함되지 않아야 합니다.

   대화 상자에서 업로드할 에셋의 세부 정보를 확인하고 을 선택합니다 **[!UICONTROL 업로드]**.

   기존 양식 에셋을 업로드하는 경우 에셋이 업데이트됩니다.

   >[!NOTE]
   >
   > 이름이 다른 리소스 유형과 충돌하는 경우 패키지를 업로드해도 기존 폴더 계층 구조가 바뀌지 않습니다. 예를 들어 위치에 &#39;교육&#39;이라는 적응형 양식이 있는 경우 `/content/dam/formsanddocuments` 서버 한 대에 적응형 양식을 다운로드하고 다른 서버에 양식을 업로드할 수 있습니다. 두 번째 서버에도 동일한 위치에 &#39;Training&#39;이라는 이름의 폴더가 있습니다 `/content/dam/formsanddocuments`. 업로드에 실패합니다.

## 테마 다운로드

다음 위치에서 테마를 내보낼 수 있습니다. [!DNL AEM Forms] 다른 프로젝트 또는 인스턴스에서 사용할 수 있습니다. AEM을 사용하면 테마를 zip 파일로 다운로드하여 인스턴스에 업로드할 수 있습니다.
테마를 다운로드하려면:

1. 에 로그인 [!DNL Experience Manager Forms] 작성자 인스턴스.
1. 선택 **[!UICONTROL Forms]** > **[!UICONTROL 테마]**.

   ![테마 선택](/help/forms/assets/select-theme.png)

1. 테마 페이지에서 테마를 선택하고 **[!UICONTROL 다운로드]** 아이콘 을 클릭합니다.

   ![테마 다운로드](/help/forms/assets/download-theme.png)

   테마를 다운로드할 때 **[!UICONTROL 자산 다운로드]** 대화 상자가 나타납니다.

   ![테마 에셋 다운로드](/help/forms/assets/download-theme-asset.png)

1. **[!UICONTROL 다운로드]**&#x200B;를 클릭합니다.

선택한 자산은 아카이브(.zip 파일)로 다운로드됩니다.

## 테마 업로드 {#uploading-a-theme}

다른 사용자가 양식에서 만드는 테마를 업로드하고 사용할 수 있습니다.
테마를 업로드하려면:

1. 에 로그인 [!DNL Experience Manager Forms] 인스턴스.
1. Experience Manager에서 다음으로 이동 **[!UICONTROL Forms]** > **[!UICONTROL 테마]**.

   ![테마 선택](/help/forms/assets/select-theme.png)

1. 테마 페이지에서 **[!UICONTROL 만들기]** > **[!UICONTROL 파일 업로드]**.

   ![테마 업로드](/help/forms/assets/theme-upload.png)

1. 컴퓨터에서 테마 패키지를 검색하여 선택하고 **[!UICONTROL 업로드]**. 업로드한 테마는 테마 페이지에서 사용할 수 있습니다.

## 폴더를 사용하여 적응형 Forms, PDF forms 및 관련 에셋 구성  {#folders-and-organizing-assets}

폴더를 사용하여 에셋을 정렬하고 구성할 수 있습니다. 폴더에서 문서 및 에셋을 구성하면 파일을 그룹화하여 쉽게 관리할 수 있습니다. 폴더를 선택하여 다운로드하거나 삭제할 수 있습니다.

### 폴더 만들기 {#create-a-folder}

폴더를 만들려면 다음 작업을 수행하십시오.

1. 에 로그인 [!DNL Experience Manager Forms] 인스턴스.
1. 선택 **[!UICONTROL Forms]** > **[!UICONTROL Forms 및 문서]**.

   ![양식 선택](/help/forms/assets/select-forms.png)

1. 선택 **[!UICONTROL 만들기]** > **[!UICONTROL 폴더]**.

   ![폴더 만들기](/help/forms/assets/create-folder.png)

   다음 **[!UICONTROL 폴더 추가]** 대화 상자가 나타납니다.
1. 다음을 입력합니다. **[!UICONTROL 제목]**. 다음 **[!UICONTROL 이름]** 을 입력하면 자동으로 채워집니다. **[!UICONTROL 제목]**.

   ![폴더 추가](/help/forms/assets/add-folder.png)

1. **[!UICONTROL 만들기]**&#x200B;를 클릭합니다.

   >[!NOTE]
   >
   >기본적으로 이름 필드의 값은 제목에서 자동으로 채워집니다. 이름에는 영숫자와 하이픈(-) 및 밑줄(_) 특수 문자만 사용할 수 있습니다. 제목에 입력된 다른 특수 문자는 자동으로 하이픈으로 대체되며 새 이름을 확인하라는 메시지가 표시됩니다. 제안된 이름을 계속 사용하거나 추가로 편집할 수 있습니다.

정의한 제목이 있는 새 폴더가 자산 목록의 현재 위치에 표시됩니다.

이름이 지정된 폴더가 있는 경우 오류가 발생하여 제출이 실패합니다. 마우스를 오류 위로 가져가면 오류 메시지를 볼 수 있습니다 ![aem6forms_error_alert](assets/Smock_Alert_18_N.svg) 이름 필드 옆에 표시되는 아이콘

만든 폴더를 선택하여 폴더 내부로 이동하고 폴더 내에 에셋 또는 폴더를 만들 수 있습니다. 또한 폴더를 선택하여 다운로드 대기열에 추가하거나 삭제하거나 이름을 편집할 수 있습니다.

### 하나 이상의 자산 복사본 만들기 {#create-copies-of-one-or-more-assets-or-letters}

기존 에셋을 사용하여 유사한 속성, 콘텐츠 및 상속된 에셋으로 에셋을 신속하게 만들 수 있습니다.

에셋의 사본을 만들려면 다음 작업을 수행하십시오.

1. 에 로그인 [!DNL Experience Manager Forms] 인스턴스.
1. 관련 에셋 페이지에서 하나 이상의 에셋을 선택합니다. UI에 **[!UICONTROL 복사]** 아이콘.
1. 선택 **[!UICONTROL 복사]**. UI에 ![붙여넣기 아이콘](/help/forms/assets/Smock_Paste_18_N.svg) 아이콘.

   ![에셋 복사](/help/forms/assets/copy-asset.png)

   붙여넣기 전에 폴더 내부로 이동하거나 탐색할 수도 있습니다. 서로 다른 폴더에 동일한 이름의 자산이 포함될 수 있습니다. 폴더에 대한 자세한 내용은 [폴더 및 자산 구성](#folders-and-organizing-assets).
1. 선택 **[!UICONTROL 붙여넣기]**.

   ![자산 붙여넣기](/help/forms/assets/paste-asset.png)

1. 다음 **[!UICONTROL 붙여넣기]** 대화 상자가 나타납니다. 시스템에서는 자산의 새 복사본에 이름과 제목을 자동으로 생성하지만 자산의 제목과 이름을 편집할 수 있습니다.

   같은 위치에 에셋을 복사하고 붙여넣는 경우 의 기존 이름에 접미사 &quot;-CopyXX&quot;가 추가됩니다. `asset`. 복사한 에셋에 대한 제목이 없는 경우 자동 생성된 제목 필드는 비어 있습니다.

   ![새 위치에 자산 붙여넣기](/help/forms/assets/paste-click-asset.png)

   필요한 경우 **[!UICONTROL 제목]** 에셋의 사본을 저장할 때 사용합니다. 다음 **[!UICONTROL 이름]** 을 입력하면 자동으로 채워집니다. **[!UICONTROL 제목]**.
1. 선택 **[!UICONTROL 붙여넣기]**. 복사된 에셋의 새 복사본이 생성됩니다.

## 검색 {#search-forms}

에셋이 많으면 적절한 에셋을 검색하는 데 시간이 오래 걸립니다. 에셋 페이지에서 특정 에셋에 대한 텍스트 기반 검색을 수행할 수 있습니다.

자산을 검색하려면 다음 작업을 수행하십시오.

1. 에 로그인 [!DNL Experience Manager Forms] 인스턴스.
1. 다음을 클릭합니다. ![검색 아이콘](assets/folder-search-icon.svg) 검색 아이콘.

   ![검색 양식](/help/forms/assets/search-form.png)

1. 검색 창에서 검색할 에셋의 이름을 입력합니다.

1. 관련 에셋 목록이 나타납니다. 표시된 에셋 목록에서 원하는 에셋을 선택합니다.

   ![자산 검색](/help/forms/assets/search-bar.png)

검색 사용에 대한 자세한 내용 및 지침은 [검색](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/operations/indexing.html).

<!--
## Export or create a package {#export-a-workflow-application}

You can use packages to install new content, install new functionality, transfer content between instances, and back up content.
To export or create a package:

1. Log in to your [!DNL Experience Manager Forms] instance.
1. Navigate to **[!UICONTROL Tools]** ![hammer](assets/hammer.png) &gt; **[!UICONTROL Deployment]** &gt; **[!UICONTROL Packages]**.

   ![Package Manager](/help/forms/assets/package-manager.png)

1. Click **[!UICONTROL Create Package]**.

   ![Create package](/help/forms/assets/create-package.png)   
   
   When **[!UICONTROL Create Package]** is clicked, the **[!UICONTROL New Package]** dialog box appears.
1. Specify the package name, version, and group for the package. 
   
   ![New package](/help/forms/assets/new-package.png)  

   * **Package Name** - Select a descriptive name to help you identify the contents of the package.

   * **Version** - It is a textual field to indicate a version. This is appended to the package name to form the name of the zip file.

   * **Group** - This is the target group (or folder) name. Groups help you organize your packages. A folder is created for the group if it does not already exist. If you leave the group name blank, it creates the package in the main package list.

1. Click **[!UICONTROL OK]**.

   Once the package is created, it appears at the top of the list of packages.

1. Click **[!UICONTROL Edit]**.
   
   ![Edit Package](/help/forms/assets/edit-package.png)
    
1. Open the **[!UICONTROL Filters]** tab.
   
   ![Open filter tab](/help/forms/assets/add-filter-package.png)
   
1.  Click **[!UICONTROL Add Filter]**. 
   
      ![Add filter](/help/forms/assets/add-filter.png)

      You can specify the path of the package. You can also add rules and other validations for the package.

      ![Add path](/help/forms/assets/add-path.png)

1. Click **[!UICONTROL Save]** after you are finished editing the settings.
1. Click **[!UICONTROL Build]** to create the package.
    
     ![Build path](/help/forms/assets/build-package.png)

   After the package is built, you can download the package and import it to the other server. The workflow application appears on the server where the package is uploaded.

   >[!NOTE]
   >
   >For the workflow application to work properly, also export the corresponding Adaptive Form and workflow model with the work application.

   Once a package is uploaded to AEM, you can modify its settings. You can also download or delete the package.

## Import and export assets in Correspondence Management {#import-and-export-assets-in-correspondence-management}

To share assets, such as data dictionaries, letters, and document fragments, between two different implementations of Correspondence Management, you can create and share .cmp files. A .cmp file can include one or more data dictionaries, letters, document fragments, and forms.

### Export Document Fragments, Letters, and/or Data Dictionaries {#export-document-fragments-letters-and-or-data-dictionaries}

1. In the letters, document fragments, or data dictionary pages, select and select the assets you want to export to a single package, and then select Queue For Download. The assets are lined-up for export.
1. As required, repeat the above step to add letters, document fragments, and data dictionaries.
1. Select **Download**.
1. Correspondence Management displays Download Asset(s) dialog with a list of assets in the export list.

   ![export](assets/export.png)

1. To view the dependencies that are exported, Select Resolve. Or skip to the next step. Even if you do not select resolve, the dependencies are still exported.
1. To download the .cmp file, select **OK**.
1. Correspondence Management downloads a .cmp file to your computer.

   The .cmp file includes the exported assets. You can share the .cmp file with others. Other users can import the .cmp file in a different server to get all the assets in the new server.

### Export all the Correspondence Management assets as a package {#export-all-the-correspondence-management-assets-as-a-package}

Use this option to download all the Correspondence Management assets and related dependencies as a package from an [!DNL AEM Forms] instance.

For example, if Correspondence Management has a letter that uses an image and text, the downloaded package also contains the image and the text related to the letter. All the metadata properties (including custom properties) associated with the asset are also downloaded. Once you have downloaded the package (.cmp), you can [import the package to a different [!DNL AEM Forms] instance](import-export-forms-templates.md#p-upload-forms-documents-assets-p).

To download all the Correspondence Management assets and related dependencies as a package, complete the following steps:

1. Log in to [!DNL AEM Forms] server as a forms user.
1. Select **Adobe Experience Manager** in the Global Navigation bar.
1. Select tools ( ![tools](assets/tools.png)) and then select **Forms**.
1. Select **Export Correspondence Management Assets**.

   ![publish-cmp-assets-1](assets/publish-cmp-assets-1.png)

   ( ``The Export All Correspondence Management Assets page appears and displays the information about the last time the Export process was attempted and a link to download the last successfully exported package.

   ![export-last-run-details](assets/export-last-run-details.png)

1. Select **Export** and, in the confirm message, select **OK**.

   After a batch process is complete, the last run details and the link to download the package are updated. This includes information such as the Administrator login and if the batch run successfully or failed. The assets are exported to a package and the Download Exported Package link appears.

   >[!NOTE]
   >
   >The Export All Assets process cannot be canceled once initiated. Also, while the export all operation is in process, do not create, delete, modify, or publish any assets or initiate Publish All Assets process.a

1. Select the **Download Exported Package** link to download the package file.

   To add the assets in the package to another instance of Correspondence Management, [import the package to an [!DNL AEM Forms] instance](import-export-forms-templates.md#p-upload-forms-documents-assets-p).

<!-- ### Import Document Fragments, Letters and/or Data Dictionaries into Correspondence Management {#import-document-fragments-letters-and-or-data-dictionaries-into-correspondence-management}

You can import assets that are exported into a .cmp file. A .cmp file can have one or more letters, data dictionaries, document fragments, and dependent assets.

>[!NOTE]
>
>While importing old Correspondence Management assets for migration, log in using an Admin account. For more information on Migrating old Correspondence Management assets, see [Migrate Correspondence Management assets to AEM 6.1 forms](migration-utility.md).

1. On the data dictionary, letters, or document fragments page, select **Create &gt; File Upload** and select the .cmp file.
1. Correspondence Management displays the Import Assets dialog with the list of assets that are imported. Select **Import**.

   After importing the assets, the following properties of the assets are updated while the other properties remain the same:

    * Author: Displays the ID of the user that imported the asset to the server
    * Modified: The time when the asset was imported to the server

   >[!NOTE]
   >
   >For you to be able to upload XDPs (as part of the cmp file or otherwise), you need to be a part of forms-power-users group. For access rights, contact the administrator. -->

## 추가 참조 {#see-also}

{{see-also}}
