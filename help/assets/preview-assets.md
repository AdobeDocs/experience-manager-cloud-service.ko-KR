---
title: AEM Sites 페이지에서 사용하기 전에 에셋 미리보기
description: OpenAPI 기능이 있는 Dynamic Media를 사용하면 Adobe Experience Manager(AEM) Sites 미리보기 페이지에서 자산을 미리 볼 수 있습니다. 이 자산 미리 보기를 사용하면 사용자와 관련자가 공개적으로 사용할 작성자 페이지(업데이트된 자산)를 게시하기 전에 자산 업데이트를 검토하고 확인할 수 있습니다.
role: Admin, User
source-git-commit: e343cc5754ec5565e57a5a932d59d7bfe78c6027
workflow-type: tm+mt
source-wordcount: '732'
ht-degree: 0%

---


# AEM Sites 페이지에서 사용하기 전에 에셋 미리보기 {#asset-preview-using-Dynamic-Media-with-OpenAPI-capabilities}

[!DNL Dynamic Media with OpenAPI capabilities]을(를) 사용하면 [!DNL Adobe Experience Manager (AEM) Sites] 작성자 페이지에서 사용할 수 있는 에셋을 미리 본 후 공개적으로 사용할 수 있습니다. 에셋 미리보기는 사이트의 작성자 및 미리보기 계층에서 사용할 수 있습니다.

[AEM Sites 미리 보기 페이지에서 자산을 미리 보려면](#asset-preview-on-sites-pages-using-Dynamic-Media-with-OpenAPI-capabilities) 미리 보려는 자산을 추가하거나 라이브 사이트 페이지에서 사용할 수 있는 기존 자산을 교체하여 사이트의 작성자 페이지를 업데이트하십시오. 그런 다음 업데이트된 작성자 페이지를 미리보기 계층에 게시하여 미리보기 URL을 생성합니다.

미리보기 페이지를 이해 당사자와 공유하여 업데이트된 에셋의 시각적 품질과 상황별 정렬에 대한 피드백을 수집합니다. 피드백을 기반으로 에셋을 세분화합니다. 검토 주기 동안 에셋의 여러 버전을 만들고 관리합니다.

공용으로 사용할 에셋을 완료한 후 작성자 페이지에서 해당 에셋을 업데이트하고 공개 액세스를 위해 페이지를 게시 계층에 게시합니다.

## 시작하기에 앞서{#prerequisites-for-previewing-assets-using-Dynamic-Media-with-OpenAPI-capabilities}

다음을 확인합니다.

* [!DNL AEM Assets as a Cloud Service]에 액세스.
* 에셋의 상태 속성을 편집할 수 있는 권한입니다.
* [미리 볼 에셋이 포함된 폴더에 적용된 메타데이터 양식의 [!UICONTROL 기본] 탭[!UICONTROL 에서 사용할 수 있는 &#x200B;] 상태[!UICONTROL &#x200B; 메타데이터 속성에 &#x200B;]미리 보기](/help/assets/metadata-assets-view.md#edit-metadata-forms) 값을 추가했습니다.
  ![미리 보기 옵션 추가](/help/assets/assets/metedata-form-preview.png)
* 미리 보기 토큰을 생성하기 위한 키입니다. [Adobe 지원에 문의](https://helpx.adobe.com/in/contact.html)하여 키에 대한 요청을 제기하십시오.

## 사이트 미리보기 페이지에서 에셋 미리보기 {#asset-preview-on-sites-pages-using-Dynamic-Media-with-OpenAPI-capabilities}

이미 승인된 새 에셋 또는 에셋을 미리 볼 수 있습니다. 승인된 에셋은 라이브 사이트 페이지에만 표시됩니다.

다음 단계를 실행하여 자산 상태를 [!DNL Assets View]에서 미리 보기로 설정한 다음 Sites 작성 페이지를 미리 보기 계층에 게시하여 페이지의 미리 보기 URL을 생성합니다.

1. 다음 단계를 실행하여 자산 상태를 **[!UICONTROL 미리 보기]**(으)로 설정합니다.

   1. [!DNL Assets View]에서 **[!UICONTROL Assets]**&#x200B;을(를) 선택하고 폴더로 이동합니다.
   1. 미리 볼 자산을 선택합니다.
   1. **[!UICONTROL 세부 정보]**&#x200B;를 클릭합니다.
   1. [!UICONTROL 정보 패널]에서 **[!UICONTROL 상태]**&#x200B;을(를) **[!UICONTROL 미리 보기]**(으)로 설정한 다음 **[!UICONTROL 저장]**&#x200B;을 클릭하세요.
      ![미리보기](/help/assets/assets/preview-boat-at-bay.png)

1. 사이트 작성 페이지로 이동합니다. [AEM 페이지 편집기에서 원격 자산 액세스](/help/assets/integrate-remote-approved-assets-with-sites.md#access-remote-assets-in-aem-page-editor) 섹션의 단계를 실행하여 자산 선택기 패널을 사용하여 최근에 미리 보기(상태)로 설정한 자산을 선택합니다.

   >[!NOTE]
   >
   > 에셋 선택기는 최신 상태 업데이트가 승인됨 또는 미리보기로 설정된 에셋을 표시합니다.

1. **[!UICONTROL 게시 관리]** 옵션을 사용하여 미리 보기 계층에 페이지를 게시합니다. 미리 보기 계층에 페이지를 게시하려면 [미리 보기에 콘텐츠 게시](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/sites/authoring/sites-console/previewing-content) 섹션의 단계를 실행하십시오. 게시 후 페이지의 미리보기 URL을 생성합니다. 미리보기 페이지에는 Sites 페이지의 에셋(최신 상태 업데이트)이 표시됩니다.

이해 당사자와 이 미리보기 URL을 공유하여 검토 및 피드백을 받을 수 있습니다. 이해 당사자가 미리보기 페이지에 액세스할 수 있는지 확인합니다. 미리 보기 페이지에 대한 액세스 권한을 제공하는 방법에 대한 자세한 내용은 [미리 보기 서비스에 액세스](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/manage-environments#access-preview-service)를 참조하십시오.

>[!NOTE]
>
>[이미지 V3 핵심 구성 요소](https://experienceleague.adobe.com/en/docs/experience-manager-core-components/using/wcm-components/image#version-and-compatibility)는 기본적으로 자산의 미리 보기 버전을 지원합니다. [자산 선택기](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/assets/manage/asset-selector/asset-selector-upload) 패널을 사용하여 자산(미리 보기 상태의 자산)의 미리 보기 버전을 선택하면 이미지 V3 구성 요소가 미리 보기 계층(Sites 작성자 페이지의 미리 보기 버전)에서 자동으로 렌더링합니다.

에셋 버전을 완료한 후 공용 사용을 위해 [게시 계층에 페이지를 게시](#publish-your-pages-to-publish-tier)하십시오.

## 승인된 자산으로 공개 사용을 위해 페이지 게시{#publish-your-pages-to-publish-tier}

공용 사용을 위한 자산 버전을 완료한 후 자산 상태를 **[!UICONTROL 승인됨]**(으)로 설정하십시오. 그런 다음 페이지를 게시 계층에 게시합니다. 페이지를 게시하려면 다음 단계를 수행하십시오.

1. 자산 상태를 [승인됨](#asset-preview-on-sites-pages-using-Dynamic-Media-with-OpenAPI-capabilities)(으)로 변경하려면 위의 **[!UICONTROL 사이트 미리 보기 페이지에서 자산 미리 보기]** 섹션의 1단계를 따르십시오.
1. 사이트 작성자 페이지로 이동하여 [!DNL Publish tier]에 게시합니다. [페이지 편집기에서 게시](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/sites/authoring/page-editor/publishing#publishing-from-the-page-editor) 섹션의 단계를 실행하여 페이지를 게시합니다.
또는 [사이트 콘솔에서 페이지 게시](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/sites/authoring/sites-console/publishing-pages#publishing-from-the-sites-console) 섹션의 단계에 따라 사이트의 콘솔에서 페이지를 게시합니다.

   >[!NOTE]
   >
   > 승인된 자산만 게시 계층에서 전달할 수 있습니다. 공개 사용을 위해 게시 계층에 페이지를 게시하기 전에 자산을 승인합니다.

   ![페이지가 게시되었습니다](/help/assets/assets/the-page-has-been-publushed.png)
게시 성공 후 확인 메시지 **[!UICONTROL 페이지가 게시되었습니다]**&#x200B;가 표시됩니다. 게시 계층에서 게시된 페이지로 이동하여 업데이트가 활성 상태이고 콘텐츠가 예상대로 표시되는지 확인합니다.

