---
title: 적응형 Forms, PDF forms 및 기타 자산 가져오기, 내보내기 및 구성
seo-title: Learn to import, export, and organize Adaptive Forms, PDF forms, and other assets on an[!DNL AEM Forms] instance
description: '적응형 Forms 및 자산을 AEM 인스턴스로 마이그레이션하려고 합니까? 에서 응용 Forms, PDF forms, 테마 및 기타 지원 자산을 가져오고 내보내는 방법을 알아봅니다 [!DNL AEM Forms] 인스턴스. '
seo-description: Looking to migrate Adaptive Forms and assets to and from an AEM instances? Learn here how to import and export Adaptive Forms, PDF forms, themes, and other supporting assets from an [!DNL AEM Forms] instance.
topic-tags: forms-manager
exl-id: f5105fb7-b8c0-4656-8095-b21d392746c0
source-git-commit: 7163eb2551f5e644f6d42287a523a7dfc626c1c4
workflow-type: tm+mt
source-wordcount: '1211'
ht-degree: 2%

---

# 적응형 양식, PDF 양식 및 기타 에셋 가져오기, 내보내기 및 구성{#importing-and-exporting-assets-to-aem-forms}

적용형 Forms 및 적용형 양식 테마, 양식 데이터 모델, 적용형 양식 템플릿, 문서 조각 및 PDF forms 등의 관련 자산을 다음 간에 이동할 수 있습니다 [!DNL AEM Forms] 인스턴스. CRX 패키지 또는 이진 파일 형식으로 자산을 가져오고 내보낼 수 있습니다.

적응형 양식을 내보낼 때 컨텐츠 정책 및 템플릿은 내보내지지 않습니다. 사용 [패키지 관리자](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/deploying/overview.html?lang=en#how-rolling-deployments-work) 를 입력하여 해당 자산을 내보냅니다.

## 응용 Forms, PDF forms 또는 관련 자산 다운로드 {#download-forms-amp-documents-assets}

양식 또는 관련 자산을 다운로드하려면 다음을 수행하십시오.

1. 에 로그인합니다. [!DNL AEM Forms] 인스턴스.
1. 탭 **[!UICONTROL Adobe Experience Manager]** ![adobeexperiencemanager](assets/adobeexperiencemanager.png) 아이콘 > **[!UICONTROL 탐색]** ![나침반](assets/Smock_Compass_18_N.svg) 아이콘 > **[!UICONTROL Forms]** > **[!UICONTROL Forms 및 문서]**.
1. 자산을 선택하고 을(를) 탭합니다 **[!UICONTROL 다운로드]** 아이콘.
1. 자산 다운로드에서 다음 옵션 중 하나를 선택하고 를 탭합니다 **[!UICONTROL 다운로드]**.

   * **CRX 패키지로 다운로드:** 옵션을 사용하여 선택한 모든 자산 및 관련 종속성을 [!DNL AEM Forms] 인스턴스를 다른 인스턴스에 설정합니다. AEM(적응형 Forms 및 적응형 양식 조각), 양식 세트, 양식 데이터 모델, 양식 템플릿, PDF 문서 및 참조된 리소스(XSD 및 이미지)를 포함하여 모든 자산 및 폴더를 CRX 패키지로 다운로드합니다.
자산을 패키지로 다운로드하는 것의 이점은 선택한 자산에서 참조하는 자산도 다운로드하는 것입니다. 예를 들어 양식 템플릿, XSD 및 이미지를 사용하는 적응형 양식이 있는 경우 이 적응형 양식을 선택하고 패키지로 다운로드하면 다운로드된 패키지에 양식 템플릿, XSD 및 이미지도 포함되어 있습니다. 자산과 연결된 모든 메타데이터 속성(사용자 지정 속성 포함)도 다운로드됩니다.

   * **자산을 이진 파일로 다운로드:** 양식 템플릿(XDP), PDF forms(PDF), 문서(PDF) 및 리소스(이미지, 스키마, 스타일 시트)만 다운로드하려면 옵션을 사용합니다. 외부 애플리케이션에서 이러한 자산을 편집할 수 있습니다. 이미지, PDF 및 기타 지원되는 형식과 같은 바이너리가 있는 자산을 .zip 파일로 다운로드합니다.
응용 Forms, 응용 양식 조각, 테마 및 양식 세트는 **[!UICONTROL 자산을 이진 파일로 다운로드]** 선택 사항입니다. 이러한 자산을 다운로드하려면 **[!UICONTROL CRX 패키지로 다운로드]** 선택 사항입니다.

   선택한 자산이 아카이브(.zip 파일)로 다운로드됩니다.

   >[!NOTE]
   >
   >AEM 패키지와 이진 파일은 모두 보관 파일(.zip 파일)로 다운로드됩니다. 자산에 대한 템플릿은 자산과 함께 다운로드되지 않습니다. 자산 템플릿을 별도로 내보내야 합니다.

## 응용 Forms, PDF forms 또는 관련 자산 업로드 {#upload-forms-amp-documents-assets}

지원되는 자산 유형을 개별적으로 또는 ZIP 아카이브로 업로드할 수 있습니다. ZIP 파일의 경우 지원되는 모든 자산의 상대 경로가 표시됩니다. ZIP 내에서 지원되지 않는 자산은 무시되며 나열되지 않습니다. 그러나 ZIP 보관 위치에 지원되지 않는 자산만 포함되어 있으면 팝업 대화 상자 대신 오류 메시지가 표시됩니다.
양식 또는 관련 자산을 업로드하려면 다음을 수행하십시오.

1. 에 로그인합니다. [!DNL AEM Forms] 인스턴스.
1. 탭 **[!UICONTROL Adobe Experience Manager]** ![adobeexperiencemanager](assets/adobeexperiencemanager.png) 아이콘 > **[!UICONTROL 탐색]** ![나침반](assets/Smock_Compass_18_N.svg) 아이콘 > **[!UICONTROL Forms]** > **[!UICONTROL Forms 및 문서]**.
1. 탭 **[!UICONTROL 만들기]** > **[!UICONTROL 파일 업로드]**. 대화 상자가 나타납니다.
1. 대화 상자에서 가져올 패키지 또는 아카이브를 찾아 선택합니다. 지원되는 다른 파일 유형을 선택할 수도 있습니다. 탭 **[!UICONTROL 열기]**. 선택한 폴더 또는 파일 이름은 특수 문자를 포함하지 않아야 합니다.

   대화 상자에서 업로드되는 자산의 세부 정보를 확인하고 탭합니다 **[!UICONTROL 업로드]**.

   기존 양식 자산을 업로드하는 경우, 자산이 업데이트됩니다.

   >[!NOTE]
   >
   > * 이름이 다른 리소스 유형과 충돌하는 경우 패키지를 업로드해도 기존 폴더 계층 구조가 대체되지 않습니다. 예를 들어 한 서버에 &#39;Training&#39;이라는 응용 양식이 있는 경우 /content/dam/formsanddocuments 위치에 있습니다. 적응형 양식을 다운로드하고 다른 서버에 양식을 업로드합니다. 두 번째 서버에도 같은 위치에 &#39;Training&#39;이라는 이름의 폴더가 있습니다. /content/dam/formsanddocuments. 업로드에 실패합니다.
   > * 의 멤버만 `form-power-user` 그룹은 XDP 파일을 업로드할 수 있습니다.



## 테마 다운로드 {#downloading-a-theme}

에서 테마를 내보낼 수 있습니다 [!DNL AEM Forms] 추가 콘텐츠는 다른 프로젝트 또는 인스턴스에서 사용할 수 있습니다. AEM에서는 인스턴스에 업로드할 수 있는 zip 파일로 테마를 다운로드할 수 있습니다.

테마를 다운로드하려면

1. 에 로그인합니다. [!DNL AEM Forms] 인스턴스.
1. 탭 **[!UICONTROL Adobe Experience Manager]** ![adobeexperiencemanager](assets/adobeexperiencemanager.png) 아이콘 > **[!UICONTROL 탐색]** ![나침반](assets/Smock_Compass_18_N.svg) 아이콘 > **[!UICONTROL Forms]** > **[!UICONTROL 테마]**.
1. 테마를 선택하고 탭합니다 **[!UICONTROL 다운로드]**. 테마는 아카이브(.zip 파일)로 다운로드됩니다.

## 테마 업로드 {#uploading-a-theme}

다른 사람이 양식에서 만드는 테마를 업로드하고 사용할 수 있습니다. 테마를 업로드하려면

1. Experience Manager에서 **[!UICONTROL Forms]** > **[!UICONTROL 테마]**.
1. 테마 페이지에서 **[!UICONTROL 만들기]** > **[!UICONTROL 파일 업로드]**.
1. 파일 업로드 프롬프트에서 컴퓨터에서 테마 패키지를 찾아 선택하고 **[!UICONTROL 업로드]**. 업로드된 테마는 테마 페이지에서 사용할 수 있습니다.

<!-- ## Import and export assets in Correspondence Management {#import-and-export-assets-in-correspondence-management}

To share assets, such as data dictionaries, letters, and document fragments, between two different implementations of Correspondence Management, you can create and share .cmp files. A .cmp file can include one or more data dictionaries, letters, document fragments, and forms.

### Export Document Fragments, Letters, and/or Data Dictionaries {#export-document-fragments-letters-and-or-data-dictionaries}

1. In the letters, document fragments, or data dictionary pages, tap and select the assets you want to export to a single package, and then tap Queue For Download. The assets are lined-up for export.
1. As required, repeat the above step to add letters, document fragments, and data dictionaries.
1. Tap **Download**.
1. Correspondence Management displays Download Asset(s) dialog with a list of assets in the export list.

   ![export](assets/export.png)

1. To view the dependencies that are exported, Tap Resolve. Or skip to the next step. Even if you do not tap resolve, the dependencies are still exported.
1. To download the .cmp file, tap **OK**.
1. Correspondence Management downloads a .cmp file to your computer.

   The .cmp file includes the exported assets. You can share the .cmp file with others. Other users can import the .cmp file in a different server to get all the assets in the new server.

### Export all the Correspondence Management assets as a package {#export-all-the-correspondence-management-assets-as-a-package}

Use this option to download all the Correspondence Management assets and related dependencies as a package from an [!DNL AEM Forms] instance.

For example, if Correspondence Management has a letter that uses an image and text, the downloaded package also contains the image and the text related to the letter. All the metadata properties (including custom properties) associated with the asset are also downloaded. Once you have downloaded the package (.cmp), you can [import the package to a different [!DNL AEM Forms] instance](import-export-forms-templates.md#p-upload-forms-documents-assets-p).

To download all the Correspondence Management assets and related dependencies as a package, complete the following steps:

1. Log in to [!DNL AEM Forms] server as a forms user.
1. Tap **Adobe Experience Manager** in the Global Navigation bar.
1. Tap tools ( ![tools](assets/tools.png)) and then tap **Forms**.
1. Tap **Export Correspondence Management Assets**.

   ![publish-cmp-assets-1](assets/publish-cmp-assets-1.png)

   ( ``The Export All Correspondence Management Assets page appears and displays the information about the last time the Export process was attempted and a link to download the last successfully exported package.

   ![export-last-run-details](assets/export-last-run-details.png)

1. Tap **Export** and, in the confirm message, tap **OK**.

   After a batch process is complete, the last run details and the link to download the package are updated. This includes information such as the Administrator login and if the batch run successfully or failed. The assets are exported to a package and the Download Exported Package link appears.

   >[!NOTE]
   >
   >The Export All Assets process cannot be canceled once initiated. Also, while the export all operation is in process, do not create, delete, modify, or publish any assets or initiate Publish All Assets process.a

1. Tap the **Download Exported Package** link to download the package file.

   To add the assets in the package to another instance of Correspondence Management, [import the package to an [!DNL AEM Forms] instance](import-export-forms-templates.md#p-upload-forms-documents-assets-p).

<!-- ### Import Document Fragments, Letters and/or Data Dictionaries into Correspondence Management {#import-document-fragments-letters-and-or-data-dictionaries-into-correspondence-management}

You can import assets that are exported into a .cmp file. A .cmp file can have one or more letters, data dictionaries, document fragments, and dependent assets.

>[!NOTE]
>
>While importing old Correspondence Management assets for migration, log in using an Admin account. For more information on Migrating old Correspondence Management assets, see [Migrate Correspondence Management assets to AEM 6.1 forms](migration-utility.md).

1. On the data dictionary, letters, or document fragments page, tap **Create &gt; File Upload** and select the .cmp file.
1. Correspondence Management displays the Import Assets dialog with the list of assets that are imported. Tap **Import**.

   After importing the assets, the following properties of the assets are updated while the other properties remain the same:

    * Author: Displays the ID of the user that imported the asset to the server
    * Modified: The time when the asset was imported to the server

   >[!NOTE]
   >
   >For you to be able to upload XDPs (as part of the cmp file or otherwise), you need to be a part of forms-power-users group. For access rights, contact the administrator. -->

## 워크플로우 애플리케이션 내보내기 {#export-a-workflow-application}

패키지 관리자를 사용하여 워크플로우 애플리케이션을 내보낼 수 있습니다. 절차는 다음과 같습니다.

1. 열기 [!DNL AEM Forms] 패키지 관리자. 패키지 관리자의 URL은 `https://[server]:[port]/crx/packmgr`.
1. 클릭 **[!UICONTROL 패키지 만들기]**. 다음 **[!UICONTROL 새 패키지]** 대화 상자가 나타납니다.
1. 패키지의 이름, 버전 및 그룹을 지정합니다. **[!UICONTROL 확인]**&#x200B;을 클릭합니다.
1. 클릭 **[!UICONTROL 편집]** 그리고 **[!UICONTROL 필터]** 탭. 클릭 **[!UICONTROL 필터 추가]**. 워크플로 응용 프로그램의 경로를 지정합니다. 예를 들면 /etc/fd/dashboard/startpoints/assessortgage와 같습니다. 클릭 **[!UICONTROL 규칙 추가]**.

1. **[!UICONTROL 고급]** 탭을 엽니다. 선택 **[!UICONTROL 병합]** 또는 **[!UICONTROL 덮어쓰기]** ACL 처리 필드에서 참조할 수 있습니다. **[!UICONTROL 저장]**&#x200B;을 클릭합니다.
1. 클릭 **[!UICONTROL 빌드]** 패키지를 만들려면

   패키지가 빌드되면 패키지를 다운로드하여 다른 서버로 가져올 수 있습니다. Workflow 응용 프로그램은 패키지가 업로드된 서버에 나타납니다.

   >[!NOTE]
   >
   >워크플로우 애플리케이션이 제대로 작동하려면 해당 적응형 양식 및 워크플로우 모델을 작업 애플리케이션으로 내보냅니다.

## 폴더를 사용하여 적응형 Forms, PDF forms 및 관련 자산 구성  {#folders-and-organizing-assets}

폴더를 사용하여 자산을 배열하고 구성할 수 있습니다. 문서와 자산을 폴더에 구성하면 파일을 그룹화하여 간편하게 관리할 수 있습니다. 폴더를 선택하고 다운로드하거나 삭제할 수 있습니다. 폴더를 만들려면 다음 단계를 완료하십시오.

### 폴더를 만듭니다 {#create-a-folder}

1. 에 로그인합니다. [!DNL AEM Forms] 인스턴스.
1. Experience Manager 탭 ![adobeexperiencemanager](assets/adobeexperiencemanager.png) 아이콘 > 탐색 ![나침반](assets/Smock_Compass_18_N.svg) 아이콘> **[!UICONTROL Forms]** > **[!UICONTROL Forms 및 문서]**.
1. 탭 **[!UICONTROL 만들기]** > **[!UICONTROL 폴더]**.
1. 다음 세부 정보를 입력합니다.

   * **[!UICONTROL 제목]**: 폴더의 이름 표시
   * **[!UICONTROL 이름]**: *(필수입니다)* 저장소에 폴더를 저장할 노드 이름

   >[!NOTE]
   >
   >기본적으로 이름 필드의 값은 제목에서 자동으로 채워집니다. 이름에는 영숫자만 사용할 수 있고 하이픈(-)과 밑줄(_) 특수 문자만 사용할 수 있습니다. 제목에 입력한 다른 특수 문자는 하이픈으로 자동 대체되며 새 이름을 확인하라는 메시지가 표시됩니다. 제안된 이름을 계속 사용하거나 추가로 편집할 수 있습니다.

1. 정의한 제목이 있는 새 폴더가 자산 목록의 현재 위치에 표시됩니다.

   지정된 이름의 폴더가 있는 경우 오류가 발생하여 제출이 실패합니다. 마우스를 오류 위로 가져가면 오류 메시지를 볼 수 있습니다 ![aem6forms_error_alert](assets/Smock_Alert_18_N.svg) 이름 필드 옆에 표시되는 아이콘입니다.

   새로 만든 폴더를 탭하여 폴더 내로 이동하고 폴더 내에 자산 또는 폴더를 만들 수 있습니다. 또한 폴더를 선택하고 이 폴더를 다운로드하도록 큐에 올리거나 삭제하거나 이름을 편집할 수 있습니다.


<!-- ### Create copies of one or more assets or letters {#create-copies-of-one-or-more-assets-or-letters}

You can use an existing assets to quickly create an asset with similar properties, content, and inherited assets.

Complete the following steps to create copies of assets and letters:

1. On the relevant assets page, select one or more assets. The UI displays the Copy icon.
1. Tap **[!UICONTROL Copy]**. The UI displays the **[!UICONTROL Paste]** icon. You can also choose to go/navigate inside a folder before you paste. Different folders can contain assets with same names. For more information on folders, see [Folders and organizing assets](#folders-and-organizing-assets).
1. Tap **[!UICONTROL Paste]**. The **[!UICONTROL Paste]** dialog appears. The system auto generates names and titles to the new copies of assets/letters, but you can edit the titles and names of the assets/letters.

   If you are copying and pasting the assets/letters at the same place, a suffix "-CopyXX" gets added to the existing name of the asset/letter. If no title existed for the copied asset/letter, the auto generated title field remains blank.

1. If required, edit the Title and Name with which you want to save the copy of the asset/letter.
1. Tap **[!UICONTROL Paste]**. New copies of the copied assets are created.

## Search {#search-forms}

You ca use the top bar **[A]** to search your content. When you search for assets, a side panel is displayed. You can also tap ![assets-browser-content-only](assets/assets-browser-content-only.png) &gt; Filter **[B]** to invoke the side panel. Using the various filters in the side panel, you can narrow down your search. The side panel also allows you to save your searches.

![search_topbar](assets/search_topbar.png)

**A.** Search **B.** Filter

![Side panel - Filters](assets/search_sidepanel.png)

Side panel - Filters

On the side panel, you can use the following to narrow down your search results:

* Search Directory
* Tags
* Search Criteria; for example, Modified Dates, Publish Status, LiveCopy Status.

The side panel also allows you to save your search settings with names of your choice.

For more information and instructions on using search, filters, saved search, and side panel, see [Search](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/operations/indexing.html). -->
