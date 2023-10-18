---
title: AEM 적응형 양식을 Microsoft® SharePoint 목록에 연결하는 방법
description: 적응형 양식을 Microsoft® SharePoint 목록에 연결합니다. Microsoft® SharePoint 목록을 구성하고 구성을 사용하여 양식 데이터 모델을 만드는 방법을 알아봅니다. 또한 FDM을 적응형 양식과 통합하는 방법에 대해 알아봅니다.
role: User, Developer
keywords: AEM 적응형 양식을 Microsoft SharePoint 목록에 연결, 적응형 양식을 Microsoft SharePoint 목록에 연결, AEM 적응형 양식을 Microsoft SharePoint 목록에 통합, 적응형 양식을 Microsoft 목록에 통합, 적응형 양식의 데이터를 SharePoint 목록에 제출, SharePoint 워크플로우를 AEM SharePoint 목록에 제출.
source-git-commit: 0f8aed76af4d2640094a76f2805f73a0a619e33f
workflow-type: tm+mt
source-wordcount: '552'
ht-degree: 7%

---


# Microsoft® SharePoint 목록에 적응형 양식 연결

<span class="preview"> 이는 프리릴리스 기능이고 [프리릴리스 채널](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/release-notes/prerelease.html#new-features)을 통해 액세스할 수 있습니다. </span>

**Microsoft® SharePoint**: Microsoft® SharePoint은 모든 팀, 부서 및 부서에 역동적이고 효율적인 팀 사이트를 제공하여 공동 작업을 지원합니다. Microsoft® Edge, Internet Explorer, Chrome 또는 Firefox와 같은 웹 브라우저를 사용하여 모든 장치에서 정보를 저장, 구성, 공유 및 액세스하는 데 사용됩니다. 의 두 가지 주요 구성 요소 **Microsoft® SharePoint** 은(는)

* **Microsoft® SharePoint 문서 라이브러리**: Microsoft® SharePoint Document Library는 파일 및 폴더 목록을 마지막으로 수정한 날짜 및 파일 소유자와 같은 주요 정보와 함께 표시합니다. 이 기능을 사용하면 파일을 쉽게 구성하고 탐색할 수 있습니다.
를 통합하는 방법에 대한 지침 **Microsoft® SharePoint 문서 라이브러리** 적응형 양식을 사용하여 다음을 참조하십시오. [적응형 양식 제출 액션](/help/forms/configuring-submit-actions.md#submit-to-sharepoint) 기사.

* **Microsoft® SharePoint 목록**: Microsoft® SharePoint 목록은 데이터의 컬렉션입니다. 다양한 유형의 데이터에 대해 열을 추가하고 보기를 만들어 데이터를 효과적으로 표시할 수 있습니다. 목록을 쉽게 그룹화, 필터링, 정렬 및 서식을 지정할 수 있습니다.

>[!VIDEO](https://video.tv.adobe.com/v/3424820/connect-aem-adaptive-form-to-sharepointlist/?quality=12&learn=on)

## Microsoft® SharePoint 목록에 적응형 양식을 연결하기 위한 사전 요구 사항 {#prerequisites}

Microsoft® SharePoint 목록에 적응형 양식을 연결하기 전에 다음 단계를 수행하십시오.

1. [Microsoft® SharePoint 목록 구성](/help/forms/configure-data-sources.md#configure-microsoft-sharepoint-list)
1. [Microsoft® SharePoint 목록 구성을 사용하여 양식 데이터 모델 만들기](/help/forms/create-form-data-models.md)
1. [데이터를 검색하고 전송하도록 양식 데이터 모델 구성](/help/forms/work-with-form-data-model.md#configure-services)
1. [적응형 양식 만들기](/help/forms/creating-adaptive-form-core-components.md)

이제 다음과 같은 작업을 수행할 수 있습니다.

* [Microsoft® SharePoint 목록을 적응형 양식에 연결](#connect-an-adaptive-form-to-microsoft-sharepoint-list-connect-af-sharepoint-list)
* [Microsoft® SharePoint 목록을 AEM 워크플로에 연결](#connect-sharepoint-list-workflow)

## Microsoft® SharePoint 목록에 적응형 양식 연결 {#connect-af-sharepoint-list}

Microsoft® SharePoint 목록을 적응형 양식에 통합하려면 [양식 데이터 모델을 사용하도록 적응형 양식 구성](/help/forms/creating-adaptive-form-core-components.md#configure-a-schema-or-form-data-model-for-an-adaptive-formconfigure-schema-or-data-model-for-form)

양식 데이터 모델을 사용하도록 적응형 양식을 구성한 후 다음을 수행할 수 있습니다.

* [양식 데이터 모델을 사용하여 제출 작업 구성](/help/forms/configuring-submit-actions.md#submit-using-form-data-model)
* [양식 데이터 모델을 호출하도록 규칙 편집기 구성](/help/forms/rule-editor.md#invoke-form-data-model-service-invoke)

## Microsoft® SharePoint 목록을 AEM 워크플로에 연결 {#connect-sharepoint-list-workflow}

Microsoft® SharePoint 목록을 AEM Workflow에 통합하려면

1. [양식 데이터 모델을 호출하는 워크플로우 만들기](https://experienceleague.adobe.com/docs/experience-manager-65/developing/extending-aem/extending-workflows/workflows-models.html)

   <!--
    To create a new workflow with the editor, perform the following steps:
    1.  Go to your **AEM Forms Author** instance > **[!UICONTROL Tools]** > **[!UICONTROL Workflow]** > **[!UICONTROL Models]**.
    1.  Click **[!UICONTROL Create]** > **[!UICONTROL Create Model]**. The Add Workflow Model dialog appears. 
    1. Specify **[!UICONTROL Title]** and **[!UICONTROL Name (optional)]**.
    1. Click **[!UICONTROL Done]**. The new model is listed in the Workflow Models console.
    1. Select your new workflow, then use **[!UICONTROL Edit]** to open it for configuration.
    1. Add **[!UICONTROL Invoke Form Data Model Service]** step to your workflow.
    1. Confirm the changes with Sync (editor toolbar) to generate the runtime model.
    -->

1. [AEM Workflow를 호출하도록 제출 액션 구성](/help/forms/configuring-submit-actions.md#invoke-an-aem-workflow)


방법 알아보기 [AEM 워크플로우 사용](https://experienceleague.adobe.com/docs/experience-manager-learn/foundation/workflow/use-workflow.html) 적응형 양식에서 콘텐츠를 공동 작업, 관리 및 처리합니다.

## 모범 사례 {#best-practices}

<!-- * For storing data in a tabular format or implementing data permissions, it is advisable to use Microsoft® SharePoint List rather than Microsoft® SharePoint Document Library. -->
* Microsoft® SharePoint 목록에서는 다음 열 유형이 지원되지 않습니다.
   * 이미지 열
   * 메타데이터 열
   * 개인 열
   * 외부 데이터 열

## 추가 참조 {#see-also}

* [핵심 구성 요소 기반 적응형 양식 만들기](/help/forms/creating-adaptive-form-core-components.md)
* [데이터 소스 구성](/help/forms/configuring-submit-actions.md)
* [양식 데이터 모델 만들기](/help/forms/create-form-data-models.md)
* [Forms 중심의 AEM 워크플로 사용 - 비즈니스 프로세스 자동화를 위한 단계 참조](/help/forms/aem-forms-workflow-step-reference.md)

## 추가 정보

* [AEM Sites 페이지에 적응형 양식 만들기 또는 추가](/help/forms/create-or-add-an-adaptive-form-to-aem-sites-page.md)
* [AEM Sites 페이지에 적응형 양식 포함](/help/forms/embed-adaptive-form-aem-sites.md)
* [적응형 양식에서 테마 만들기, 사용 및 사용자 지정](/help/forms/using-themes-in-core-components.md)

>[!MORELIKETHIS]
>
>* [적응형 Forms에 대한 사용자 지정 제출 액션 만들기](/help/forms/custom-submit-action-form.md)





