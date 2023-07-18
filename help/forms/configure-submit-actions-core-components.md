---
title: 적응형 양식에 대한 제출 액션을 구성하는 방법
description: 적응형 양식은 여러 제출 액션을 제공합니다. 제출 액션은 제출 후 적응형 양식의 처리 방법을 정의합니다. 기본 제공 제출 액션을 사용하거나 직접 만들 수 있습니다.
hide: true
hidefromtoc: true
source-git-commit: 8ac35abd1335b4e31a6dc0d8812cc9df333e69a4
workflow-type: tm+mt
source-wordcount: '3366'
ht-degree: 2%

---

# 적응형 양식 제출 액션 {#configuring-the-submit-action}


| 버전 | 문서 링크 |
| -------- | ---------------------------- |
| AEM 6.5 | [여기를 클릭하십시오.](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-basic-authoring/configuring-submit-actions.html) |
| AEM as a Cloud Service | 이 문서 |

**적용 대상**: ✔️ 양식 핵심 구성 요소 ❌ [적응형 양식 기초 구성 요소](/help/forms/configuring-submit-actions.md). Adobe은 핵심 구성 요소를 사용하여 다음을 수행할 것을 권장합니다. [AEM Sites 페이지에 적응형 Forms 추가](create-or-add-an-adaptive-form-to-aem-sites-page.md) 또는 종료 [독립 실행형 적응형 Forms 만들기](creating-adaptive-form-core-components.md).

제출 액션을 사용하면 적응형 양식을 통해 캡처된 데이터 대상을 선택할 수 있습니다. 사용자가 를 클릭하면 트리거됩니다. **[!UICONTROL 제출]** 적응형 양식의 단추입니다.

핵심 구성 요소에 빌드된 적응형 Forms용 Forms as a Cloud Service은 사전 빌드된 제출 액션 배열을 제공합니다. 기본 제출 액션을 사용하면 다음과 같은 작업을 수행할 수 있습니다.

* 전자 메일을 통해 손쉽게 양식 데이터를 보낼 수 있습니다.
* 데이터를 전송하는 동안 Microsoft Power Automate 플로우 또는 AEM 워크플로우를 시작합니다.
* 양식 데이터를 Microsoft SharePoint Server, Microsoft Azure Blob Storage 또는 Microsoft OneDrive로 직접 전송합니다.
* 양식 데이터 모델을 사용하여 구성된 데이터 소스로 데이터를 원활하게 전송합니다.
* 데이터를 REST 엔드포인트에 편리하게 제출합니다.

다음을 수행할 수도 있습니다. [기본 제출 액션 확장](custom-submit-action-form.md) 자신의 제출 액션을 만들 수 있습니다.

## 적응형 양식에 대한 제출 액션 선택 및 구성 {#select-and-configure-submit-action}

양식에 대한 제출 액션을 선택하고 구성하려면 다음 작업을 수행하십시오.

1. 콘텐츠 브라우저를 열고 다음을 선택합니다. **[!UICONTROL 가이드 컨테이너]** 적응형 양식의 구성 요소입니다.
1. 안내서 컨테이너 속성을 클릭합니다. ![안내서 속성](/help/forms/assets/configure-icon.svg) 아이콘. 적응형 양식 컨테이너 대화 상자가 열립니다.

1. 다음을 클릭합니다.  **[!UICONTROL 제출]** 탭.

   ![렌치 아이콘을 클릭하여 적응형 양식 컨테이너 대화 상자를 열고 제출 액션을 구성합니다](/help/forms/assets/adaptive-forms-submit-message.png)

1. 선택 및 구성 **[!UICONTROL 제출 액션]**&#x200B;을 참조하십시오. 선택한 제출 액션에 대한 자세한 내용은 다음을 참조하십시오.

   * [이메일 보내기](#send-email)
   * [SharePoint에 제출](#submit-to-sharedrive)
   * [양식 데이터 모델을 사용하여 제출](#submit-using-form-data-model)
   * [Azure Blob 스토리지에 제출](#azure-blob-storage)
   * [REST 끝점에 제출](#submit-to-rest-endpoint)
   * [OneDrive에 제출](#submit-to-onedrive)
   * [AEM 워크플로우 호출](#invoke-an-aem-workflow)

## 이메일 전송 {#send-email}

양식 제출 시 한 명 이상의 수신자에게 이메일을 보내려면 **[!UICONTROL 이메일 보내기]** 제출 액션. 이 작업을 사용하면 양식 데이터를 사전 정의된 형식으로 포함하는 이메일을 만들 수 있습니다. 예를 들어 제출된 양식 데이터에서 고객 이름, 배송 주소, 상태 이름 및 우편 번호를 검색하는 다음 템플릿을 고려하십시오.

    &quot;
    
    안녕하세요, ${customer_Name},
    
    다음은 기본 배송 주소로 설정됩니다.
    ${customer_Name},
    ${customer_Shipping_Address},
    ${customer_State},
    ${customer_ZIPCode}
    
    감사합니다.
    WKND
    
    &quot;

>[!NOTE]
>
> * 모든 양식 필드가 적응형 양식 내의 다른 패널에 배치된 경우에도 고유한 요소 이름을 갖는 것은 중요합니다.
> * AEM as a Cloud Service을 사용하는 경우 아웃바운드 이메일을 암호화해야 합니다. 기본적으로 아웃바운드 이메일 기능은 비활성화됩니다. 활성화하려면 지원 티켓을 다음으로 제출하십시오. [액세스 요청](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/development-guidelines.html?lang=en#sending-email).

또한 **[!UICONTROL 이메일 보내기]** 제출 액션은 전자 메일에 첨부 파일 및 기록 문서(DoR)를 포함할 수 있는 옵션을 제공합니다.

활성화하려면 [!UICONTROL 기록 문서 첨부] 옵션을 보려면 다음 설명서를 참조하십시오. [기록 문서(DoR)를 생성하도록 적응형 양식 구성](generate-document-of-record-core-components.md). 적응형 양식 속성에서 이 옵션을 활성화할 수 있습니다.

<!-- [!NOTE]
>
>Send PDF via Email Submit Action is applicable only to Adaptive Forms that use XFA template as form model. 

>[!NOTE]
>
>Ensure that the [AEM_Installation_Directory]\crx-quickstart\temp\datamanager\ASM folder
>exists. The directory is required to temporarily store attachments. If the directory does not exist, create it. -->

<!--

>[!CAUTION]
>
>If you  [prefill](prepopulate-adaptive-form-fields.md) a form template,  a Form Data Model or schema based Adaptive Form with XML or JSON data complaint to a schema (XML schema, JSON schema , form template, or form data model) that is data does not contain &lt;afData&gt;, &lt;afBoundData&gt;, and &lt;/afUnboundData&gt; tags, then the data of unbounded fields (Unbounded fields are Adaptive Form fields without [bindref](prepopulate-adaptive-form-fields.md) property) of the Adaptive Form is lost. 

>[!CAUTION]
>
>If you [prefill](prepopulate-adaptive-form-fields.md) a form template, a Form Data Model or schema based Adaptive Form with XML or JSON data complaint to a schema (XML schema, JSON schema, or form data model) that does not contain &lt;afData&gt;, &lt;afBoundData&gt;, and &lt;/afUnboundData&gt; tags, then the data of unbounded fields (Unbounded fields are Adaptive Form fields without [bindref](prepopulate-adaptive-form-fields.md) property) of the Adaptive Form is lost.


-->

## SharePoint에 제출 {#submit-to-sharedrive}

다음 **[!UICONTROL SharePoint에 제출]** 제출 액션은 적응형 양식을 Microsoft® SharePoint 스토리지와 연결합니다. 양식 데이터 파일, 첨부 파일 또는 기록 문서를 연결된 Microsoft® Sharepoint Storage에 제출할 수 있습니다. 을(를) 사용하려면 **[!UICONTROL SharePoint에 제출]** 적응형 양식에서 작업 제출:

1. [SharePoint 구성 만들기](#create-a-sharepoint-configuration-create-sharepoint-configuration): AEM Forms을 Microsoft® Sharepoint 스토리지에 연결합니다.
2. [적응형 양식에서 SharePoint으로 제출 액션 사용](#use-sharepoint-configuartion-in-af): 적응형 양식을 구성된 Microsoft® SharePoint에 연결합니다.

### SharePoint 구성 만들기 {#create-sharepoint-configuration}

AEM Forms을 Microsoft® Sharepoint 스토리지에 연결하려면

1. 다음으로 이동 **AEM Forms** 인스턴스 > **[!UICONTROL 도구]** > **[!UICONTROL Cloud Services]** >  **[!UICONTROL Microsoft® SharePoint]**.
1. 선택 **구성 컨테이너**. 구성 컨테이너의 확인란을 클릭하지 마십시오. 구성 컨테이너의 이름을 클릭하여 선택합니다. 구성은 선택한 구성 컨테이너에 저장됩니다.
1. **[!UICONTROL 만들기]**를 클릭합니다. SharePoint 구성 마법사가 나타납니다.
   ![Sharepoint 구성](/help/forms/assets/sharepoint_configuration.png)
1. 다음을 지정합니다. **[!UICONTROL 제목]**, **[!UICONTROL 클라이언트 ID]**, **[!UICONTROL 클라이언트 암호]** 및 **[!UICONTROL OAuth URL]**. OAuth URL에 대한 클라이언트 ID, 클라이언트 암호, 테넌트 ID를 검색하는 방법에 대한 자세한 내용은 다음을 참조하십시오. [Microsoft® 설명서](https://learn.microsoft.com/en-us/graph/auth-register-app-v2).
   * 다음을 검색할 수 있습니다. `Client ID` 및 `Client Secret` Microsoft® Azure 포털에서 가져온 앱의
   * Microsoft® Azure 포털에서 리디렉션 URI를 다음으로 추가합니다. `https://[author-instance]/libs/cq/sharepoint/content/configurations/wizard.html`. 바꾸기 `[author-instance]` AEM Forms 작성자 인스턴스의 URL을 사용하는 경우입니다.
   * API 권한 추가 `offline_access` 및 `Sites.Manage.All` 읽기/쓰기 권한을 제공합니다.
   * OAuth URL 사용: `https://login.microsoftonline.com/tenant-id/oauth2/v2.0/authorize`. 바꾸기 `<tenant-id>` (으)로 `tenant-id` Microsoft® Azure 포털에서 가져온 앱의

   >[!NOTE]
   >
   > 다음 **클라이언트 암호** 필드는 Azure Active Directory 응용 프로그램 구성에 따라 필수이거나 선택 사항입니다. 애플리케이션이 클라이언트 암호를 사용하도록 구성된 경우 클라이언트 암호를 제공해야 합니다.

1. 클릭 **[!UICONTROL 연결]**. 연결에 성공하면 `Connection Successful` 메시지가 나타납니다.

1. 데이터를 저장할 폴더를 선택하려면 **SharePoint 사이트** > **문서 라이브러리** > **SharePoint 폴더**, .

   >[!NOTE]
   >
   >* 기본적으로 `forms-ootb-storage-adaptive-forms-submission` 선택한 SharePoint 사이트에서 폴더를 사용할 수 있습니다. 폴더를 사용할 수 없는 경우 **폴더 만들기** 옵션을 사용하여 만듭니다.

이제 다음에 대해 이 SharePoint 사이트 구성을 사용할 수 있습니다. **SharePoint에 제출** 적응형 양식에서 작업을 제출합니다.

### 적응형 양식에서 SharePoint으로 제출 액션 사용 {#use-sharepoint-configuartion-in-af}

이전 섹션에서 만든 SharePoint 구성을 사용하여 데이터나 기록 문서를 SharePoint 폴더에 저장할 수 있습니다. 적응형 양식에서 SharePoint에 제출 액션을 사용하려면 다음 단계를 수행하십시오.

1. 만들기 [적응형 양식](/help/forms/creating-adaptive-form.md). 적응형 양식을 작성하는 동안 [!UICONTROL 구성 컨테이너] 다음에 사용됨 [SharePoint 구성 만들기](#create-sharepoint-configuration).

   >[!NOTE]
   >
   > 없는 경우 [!UICONTROL 구성 컨테이너] 이(가) 선택됨, 전역 [!UICONTROL 스토리지 구성] 제출 작업 등록 정보 창에 폴더가 나타납니다.

1. 선택 **제출 액션** 다음으로: **[!UICONTROL SharePoint에 제출]**.
1. 구성된 을(를) 선택합니다 **[!UICONTROL 스토리지 구성]**. 양식 데이터 및 기록 문서를 저장할 SharePoint의 폴더를 지정합니다.
1. 클릭 **[!UICONTROL 저장]** 전송 설정을 저장합니다.

양식을 제출하면 데이터가 지정된 Microsoft® Sharepoint 저장소 위치(폴더)에 저장됩니다.
저장된 데이터의 폴더 구조는 입니다. `/folder_name/form_name/year/month/date/submission_id/data`.

## 양식 데이터 모델을 사용하여 제출 {#submit-using-form-data-model}

다음 **[!UICONTROL 양식 데이터 모델을 사용하여 제출]** 제출 액션은 양식 데이터 모델의 지정된 데이터 모델 개체에 대해 제출된 적응형 양식 데이터를 해당 데이터 소스에 기록합니다. 제출 액션을 구성할 때 제출된 데이터를 해당 데이터 소스에 다시 쓸 데이터 모델 개체를 선택할 수 있습니다.

또한 양식 데이터 모델 및 기록 문서(DoR)를 사용하여 데이터 소스에 양식 첨부 파일을 제출할 수 있습니다. 양식 데이터 모델에 대한 자세한 내용은 [[!DNL AEM Forms] 데이터 통합](data-integration.md).

## REST 끝점에 제출 {#submit-to-rest-endpoint}

사용 **[!UICONTROL REST 끝점에 제출]** 제출된 데이터를 rest URL에 게시하는 작업입니다. URL은 내부(양식이 렌더링되는 서버) 또는 외부 서버일 수 있습니다.

데이터를 내부 서버에 게시하려면 리소스의 경로를 제공합니다. 데이터가 리소스의 경로에 게시됩니다. 예: /content/restEndPoint. 이러한 POST 요청의 경우 제출 요청의 인증 정보가 사용됩니다.

외부 서버에 데이터를 게시하려면 URL을 제공하십시오. URL 형식은 다음과 같습니다. `https://host:port/path_to_rest_end_point`. POST 요청을 익명으로 처리하도록 경로를 구성해야 합니다.

![감사 페이지 매개 변수로 전달된 필드 값에 대한 매핑](assets/post-enabled-actionconfig.png)

위의 예에서 사용자가에 정보를 입력했습니다. `textbox` 매개 변수를 사용하여 캡처됩니다. `param1`. 다음을 사용하여 캡처된 데이터를 게시하기 위한 구문 `param1` 은(는)

`String data=request.getParameter("param1");`

마찬가지로 XML 데이터 및 첨부 파일을 게시하는 데 사용하는 매개변수는 다음과 같습니다 `dataXml` 및 `attachments`.

예를 들어, 스크립트에서 이 두 매개 변수를 사용하여 데이터를 나머지 끝점으로 구문 분석합니다. 다음 구문을 사용하여 데이터를 저장하고 구문 분석합니다.

`String data=request.getParameter("dataXml");`
`String att=request.getParameter("attachments");`

이 예에서는 `data` xml 데이터를 저장합니다. `att` 첨부 파일 데이터를 저장합니다.

다음 **[!UICONTROL REST 끝점에 제출]** 제출 액션은 HTTP GET 요청의 일부로 양식에 입력된 데이터를 구성된 확인 페이지에 제출합니다. 요청할 필드의 이름을 추가할 수 있습니다. 요청 형식은 다음과 같습니다.

`{fieldName}={request parameter name}`

아래 이미지에 표시된 대로, `param1` 및 `param2` 에서 복사된 값을 사용하여 매개 변수로 전달됩니다. **텍스트 상자** 및 **numericbox** 다음 작업을 위한 필드입니다.

![Rest 끝점 제출 작업 구성](assets/action-config.png)

다음을 수행할 수도 있습니다. **[!UICONTROL POST 요청 활성화]** 요청을 게시하기 위한 URL을 입력하십시오. 양식을 호스팅하는 AEM 서버에 데이터를 제출하려면 AEM 서버의 루트 경로에 해당하는 상대 경로를 사용하십시오. 예, `/content/forms/af/SampleForm.html`. 다른 서버에 데이터를 제출하려면 절대 경로를 사용하십시오.

>[!NOTE]
>
>필드를 REST URL의 매개 변수로 전달하려면 필드가 다른 패널에 배치된 경우에도 모든 필드에 다른 요소 이름이 있어야 합니다.

<!-- ## Send PDF via Email {#send-pdf-via-email}

The **Send PDF via Email** Submit Action sends an email with a PDF containing form data, to one or more recipients on successful submission of the form.

>[!NOTE]
>
>This Submit Action is available for XFA-based Adaptive Forms and XSD-based adaption forms that have the Document of Record template. -->

<!-- ## Invoke a forms workflow {#invoke-a-forms-workflow}

The **Submit to Forms workflow** submit option sends a data xml and file attachments (if any) to an existing Adobe LiveCycle or [!DNL AEM Forms] on JEE process.

For information about how to configure the Submit to forms workflow Submit Action, see [Submitting and processing your form data using forms workflows](submit-form-data-livecycle-process.md). -->



<!--
## Forms Portal Submit Action {#forms-portal-submit-action}

The **Forms Portal Submit Action** option makes form data available through an [!DNL AEM Forms] portal.

For more information about the Forms Portal and Submit Action, see [Drafts and submissions component](draft-submission-component.md). -->

## AEM 워크플로우 호출 {#invoke-an-aem-workflow}

다음 **[!UICONTROL AEM 워크플로우 호출]** 제출 액션은 적응형 양식을 [AEM 워크플로](https://experienceleague.adobe.com/docs/experience-manager-65/developing/extending-aem/extending-workflows/workflows-models.html?lang=en#extending-aem). 양식이 제출되면 작성자 인스턴스에서 관련 워크플로우가 자동으로 시작됩니다. 데이터 파일, 첨부 파일 및 기록 문서를 워크플로우의 페이로드 위치 또는 변수에 저장할 수 있습니다. 워크플로우가 외부 데이터 저장소로 표시되고 외부 데이터 저장소로 구성된 경우 변수 옵션만 사용할 수 있습니다. 워크플로우 모델에 사용할 수 있는 변수 목록에서 선택할 수 있습니다. 워크플로가 워크플로 생성 시점이 아니라 이후 단계에서 외부 데이터 스토리지에 대해 표시된 경우 필요한 변수 구성이 있는지 확인합니다.

제출 액션은 워크플로우의 페이로드 위치에 다음을 배치하거나 워크플로우가 외부 데이터 저장소로 표시된 경우 변수를 배치합니다.

* **데이터 파일**: 적응형 양식에 제출된 데이터가 포함되어 있습니다. 다음을 사용할 수 있습니다. **[!UICONTROL 데이터 파일 경로]** 페이로드를 기준으로 파일 이름 및 파일 경로를 지정하는 옵션입니다. 예를 들어 `/addresschange/data.xml` 경로는 라는 폴더를 만듭니다. `addresschange` 페이로드를 기준으로 배치합니다. 만 지정할 수도 있습니다. `data.xml` 폴더 계층 구조를 만들지 않고 제출된 데이터만 전송합니다. 워크플로가 외부 데이터 저장소로 표시된 경우 변수 옵션을 사용하고 워크플로 모델에 사용할 수 있는 변수 목록에서 변수를 선택합니다.

* **첨부 파일**: 다음을 사용할 수 있습니다 **[!UICONTROL 첨부 파일 경로]** 적응형 양식에 업로드된 첨부 파일을 저장할 폴더 이름을 지정하는 옵션입니다. 폴더는 페이로드를 기준으로 생성됩니다. 워크플로가 외부 데이터 저장소로 표시된 경우 변수 옵션을 사용하고 워크플로 모델에 사용할 수 있는 변수 목록에서 변수를 선택합니다.

* **기록 문서**: 적응형 양식에 대해 생성된 기록 문서가 포함되어 있습니다. 다음을 사용할 수 있습니다. **[!UICONTROL 기록 문서 경로]** 페이로드를 기준으로 기록 문서 파일의 이름과 파일 경로를 지정하는 옵션입니다. 예를 들어 `/addresschange/DoR.pdf` 경로는 라는 폴더를 만듭니다. `addresschange` 페이로드와 관련하여 다음을 배치합니다. `DoR.pdf` 페이로드 관련 만 지정할 수도 있습니다. `DoR.pdf` 폴더 계층 구조를 만들지 않고 기록 문서만 저장하려면. 워크플로가 외부 데이터 저장소로 표시된 경우 변수 옵션을 사용하고 워크플로 모델에 사용할 수 있는 변수 목록에서 변수를 선택합니다.

를 사용하기 전에 **[!UICONTROL AEM 워크플로우 호출]** 제출 액션 다음에 대해 다음을 구성합니다. **[!UICONTROL AEM DS 설정 서비스]** 구성:

* **[!UICONTROL 처리 서버 URL]**: 처리 서버 는 Forms 또는 AEM 워크플로가 트리거되는 서버입니다. AEM 작성자 인스턴스 또는 다른 서버의 URL과 동일할 수 있습니다.

* **[!UICONTROL 처리 서버 사용자 이름]**: 워크플로우 사용자의 사용자 이름

* **[!UICONTROL 처리 서버 암호]**: 워크플로우 사용자 암호



## OneDrive에 제출 {#submit-to-onedrive}

다음 **[!UICONTROL OneDrive에 제출]** 제출 액션은 적응형 양식을 Microsoft® OneDrive와 연결합니다. 양식 데이터, 파일, 첨부 파일 또는 기록 문서를 연결된 Microsoft® OneDrive 저장소에 제출할 수 있습니다. 을(를) 사용하려면 [!UICONTROL OneDrive에 제출] 적응형 양식에서 작업 제출:

1. [OneDrive 구성 만들기](#create-a-onedrive-configuration-create-onedrive-configuration): AEM Forms을 Microsoft® OneDrive 저장소에 연결합니다.
2. [적응형 양식에서 OneDrive에 제출 동작 사용](#use-onedrive-configuration-in-an-adaptive-form-use-onedrive-configuartion-in-af): 적응형 양식을 구성된 Microsoft® OneDrive에 연결합니다.

### OneDrive 구성 만들기 {#create-onedrice-configuration}

AEM Forms을 Microsoft® OneDrive 저장소에 연결하려면:

1. 다음으로 이동 **AEM Forms 작성자** 인스턴스 > **[!UICONTROL 도구]** > **[!UICONTROL Cloud Services]** >  **[!UICONTROL Microsoft® OneDrive]**.
1. 을(를) 선택하면 **[!UICONTROL Microsoft® OneDrive]**&#x200B;로 리디렉션됩니다. **[!UICONTROL OneDrive 브라우저]**.
1. 선택 **구성 컨테이너**. 구성은 선택한 구성 컨테이너에 저장됩니다.
1. **[!UICONTROL 만들기]**&#x200B;를 클릭합니다. OneDrive 구성 마법사가 나타납니다.

   ![OneDrive 구성 화면](/help/forms/assets/onedrive-configuration.png)

1. 다음을 지정합니다. **[!UICONTROL 제목]**, **[!UICONTROL 클라이언트 ID]**, **[!UICONTROL 클라이언트 암호]** 및 **[!UICONTROL OAuth URL]**. OAuth URL에 대한 클라이언트 ID, 클라이언트 암호, 테넌트 ID를 검색하는 방법에 대한 자세한 내용은 다음을 참조하십시오. [Microsoft® 설명서](https://learn.microsoft.com/en-us/graph/auth-register-app-v2).
   * 다음을 검색할 수 있습니다. `Client ID` 및 `Client Secret` Microsoft® Azure 포털에서 가져온 앱의
   * Microsoft® Azure 포털에서 리디렉션 URI를 다음으로 추가합니다. `https://[author-instance]/libs/cq/onedrive/content/configurations/wizard.html`. 바꾸기 `[author-instance]` (작성자 인스턴스의 URL 포함)
   * API 권한 추가 `offline_access` 및 `Files.ReadWrite.All` 읽기/쓰기 권한을 제공합니다.
   * OAuth URL 사용: `https://login.microsoftonline.com/tenant-id/oauth2/v2.0/authorize`. 바꾸기 `<tenant-id>` (으)로 `tenant-id` Microsoft® Azure 포털에서 가져온 앱의

   >[!NOTE]
   >
   > 다음 **클라이언트 암호** 필드는 Azure Active Directory 응용 프로그램 구성에 따라 필수입니다. 또는 선택 사항입니다. 애플리케이션이 클라이언트 암호를 사용하도록 구성된 경우 클라이언트 암호를 제공해야 합니다.

1. 클릭 **[!UICONTROL 연결]**. 연결에 성공하면 `Connection Successful` 메시지가 나타납니다.

1. 지금, 선택 **[!UICONTROL OneDrive 컨테이너]** > **[OneDrive 폴더]**  데이터를 저장합니다.

   >[!NOTE]
   >
   >* 기본적으로, `forms-ootb-storage-adaptive-forms-submission` 이(가) OneDrive 컨테이너에 있습니다.
   > * 폴더를 다음으로 만들기 `forms-ootb-storage-adaptive-forms-submission`를 클릭해도 표시되지 않는 경우 **폴더 만들기**.

이제 적응형 양식의 제출 작업에 이 OneDrive 저장소 구성을 사용할 수 있습니다.

### 적응형 양식에서 OneDrive 구성 사용 {#use-onedrive-configuartion-in-af}

만들어진 OneDrive 저장소 구성을 적응형 양식으로 사용하여 OneDrive 폴더에 데이터 또는 생성된 기록 문서를 저장할 수 있습니다. 다음 단계를 수행하여 적응형 양식에서 OneDrive 저장소 구성을 다음으로 사용합니다.
1. 만들기 [적응형 양식](/help/forms/creating-adaptive-form.md).

   >[!NOTE]
   >
   > * 동일하게 선택 [!UICONTROL 구성 컨테이너] OneDrive 저장소를 만든 적응형 양식용.
   > * 없는 경우 [!UICONTROL 구성 컨테이너] 을(를) 선택한 다음 글로벌을 선택합니다. [!UICONTROL 스토리지 구성] 제출 작업 등록 정보 창에 폴더가 나타납니다.

1. 선택 **제출 액션** 다음으로: **[!UICONTROL OneDrive에 제출]**.
   ![OneDrive GIF](/help/forms/assets/onedrive-video.gif)
1. 다음 항목 선택 **[!UICONTROL 스토리지 구성]**&#x200B;데이터를 저장할 위치입니다.
1. 클릭 **[!UICONTROL 저장]** 전송 설정을 저장합니다.

양식을 제출하면 데이터가 지정된 Microsoft® OneDrive 저장소에 저장됩니다.
데이터를 저장할 폴더 구조는 입니다. `/folder_name/form_name/year/month/date/submission_id/data`.

## Azure Blob 스토리지에 제출 {#submit-to-azure-blob-storage}

다음 **[!UICONTROL Azure Blob 스토리지에 제출]**  제출 액션은 적응형 양식을 Microsoft® Azure 포털에 연결합니다. 양식 데이터, 파일, 첨부 파일 또는 기록 문서를 연결된 Azure Storage 컨테이너에 제출할 수 있습니다. Azure Blob 스토리지에 대해 제출 액션을 사용하려면 다음을 수행하십시오.

1. [Azure Blob 저장소 컨테이너 만들기](#create-a-azure-blob-storage-container-create-azure-configuration): AEM Forms을 Azure 스토리지 컨테이너에 연결합니다.
2. [적응형 양식에서 Azure 스토리지 구성 사용](#use-azure-storage-configuration-in-an-adaptive-form-use-azure-storage-configuartion-in-af): 적응형 양식을 구성된 Azure 스토리지 컨테이너에 연결합니다.

### Azure Blob 저장소 컨테이너 만들기 {#create-azure-configuration}

AEM Forms을 Azure 스토리지 컨테이너에 연결하려면
1. 다음으로 이동 **AEM Forms 작성자** 인스턴스 > **[!UICONTROL 도구]** > **[!UICONTROL Cloud Services]** >  **[!UICONTROL Azure 스토리지]**.
1. 을(를) 선택하면 **[!UICONTROL Azure 스토리지]**&#x200B;로 리디렉션됩니다. **[!UICONTROL Azure 스토리지 브라우저]**.
1. 선택 **구성 컨테이너**. 구성은 선택한 구성 컨테이너에 저장됩니다.
1. **[!UICONTROL 만들기]**&#x200B;를 클릭합니다. Azure 스토리지 구성 만들기 마법사가 나타납니다.

   ![Azure 스토리지 구성](/help/forms/assets/azure-storage-configuration.png)

1. 다음을 지정합니다. **[!UICONTROL 제목]**, **[!UICONTROL Azure 스토리지 계정]** 및 **[!UICONTROL Azure 액세스 키]**.

   * 다음을 검색할 수 있습니다. `Azure Storage Account` 이름 및 `Azure Access key` Microsoft® Azure 포털의 저장소 계정에서.

1. **[!UICONTROL 저장]**&#x200B;을 클릭합니다.

이제 적응형 양식의 제출 작업에 이 Azure 스토리지 컨테이너 구성을 사용할 수 있습니다.

### 적응형 양식에서 Azure 스토리지 구성 사용 {#use-azure-storage-configuartion-in-af}

적응형 양식에서 생성된 Azure 스토리지 컨테이너 구성을 사용하여 Azure 스토리지 컨테이너에 데이터 또는 생성된 기록 문서를 저장할 수 있습니다. 적응형 양식에서 Azure 스토리지 컨테이너 구성을 다음으로 사용하려면 다음 단계를 수행하십시오.
1. 만들기 [적응형 양식](/help/forms/creating-adaptive-form.md).

   >[!NOTE]
   >
   > * 동일하게 선택 [!UICONTROL 구성 컨테이너] OneDrive 저장소를 만든 적응형 양식용.
   > * 없는 경우 [!UICONTROL 구성 컨테이너] 을(를) 선택한 다음 글로벌을 선택합니다. [!UICONTROL 스토리지 구성] 제출 작업 등록 정보 창에 폴더가 나타납니다.

1. 선택 **제출 액션** 다음으로: **[!UICONTROL Azure Blob 스토리지에 제출]**.
   ![Azure Blob 저장 공간 GIF](/help/forms/assets/azure-submit-video.gif)

1. 다음 항목 선택 **[!UICONTROL 스토리지 구성]**&#x200B;데이터를 저장할 위치입니다.
1. 클릭 **[!UICONTROL 저장]** 전송 설정을 저장합니다.

양식을 제출하면 데이터가 지정된 Azure 스토리지 컨테이너 구성에 저장됩니다.
데이터를 저장할 폴더 구조는 입니다. `/configuration_container/form_name/year/month/date/submission_id/data`.

구성의 값을 설정하려면 [AEM SDK를 사용해 OSGi 구성을 생성](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/deploying/configuring-osgi.html?lang=en#generating-osgi-configurations-using-the-aem-sdk-quickstart)하고 Cloud Service 인스턴스에 [구성을 배포](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/deploy-code.html?lang=en#deployment-process)하십시오.

## 동기 또는 비동기 제출 사용 {#use-synchronous-or-asynchronous-submission}

제출 액션은 동기 또는 비동기 제출을 사용할 수 있습니다.

**동기 제출**: 일반적으로 웹 양식은 동기식으로 제출하도록 구성됩니다. 동기 제출에서는 사용자가 양식을 제출할 때 확인 페이지, 감사 페이지 또는 제출 실패 시 오류 페이지로 리디렉션됩니다. 다음을 선택할 수 있습니다. **[!UICONTROL 비동기 제출 사용]** 옵션을 사용하여 사용자를 웹 페이지로 리디렉션하거나 제출 시 메시지를 표시할 수 있습니다.

![제출 액션 구성](assets/thank-you-setting.png)

**비동기 제출**: 백그라운드에서 클라이언트-서버 상호 작용이 발생하는 동안 웹 페이지가 정적 상태로 유지되는 단일 페이지 애플리케이션과 같은 최신 웹 환경이 인기를 얻고 있습니다. 이제 다음을 통해 적응형 Forms으로 이 경험을 제공할 수 있습니다. [비동기 제출 구성](asynchronous-submissions-adaptive-forms.md).

## 적응형 양식의 서버 측 유효성 재검사 {#server-side-revalidation-in-adaptive-form}

일반적으로 모든 온라인 데이터 캡처 시스템에서 개발자는 클라이언트측에 일부 JavaScript 유효성 검사를 배치하여 몇 가지 비즈니스 규칙을 적용합니다. 그러나 최신 브라우저에서는 최종 사용자가 이러한 유효성 검사를 무시하고 웹 브라우저 개발 도구 콘솔과 같은 다양한 기술을 사용하여 수동으로 제출을 수행할 수 있습니다. 이러한 기술은 적응형 Forms에도 유효합니다. Forms 개발자는 다양한 유효성 검사 논리를 만들 수 있지만, 기술적으로 최종 사용자는 이러한 유효성 검사 논리를 무시하고 잘못된 데이터를 서버에 제출할 수 있습니다. 잘못된 데이터는 양식 작성자가 적용한 비즈니스 규칙을 위반할 수 있습니다.

서버측 유효성 재검사 기능은 서버에서 적응형 양식을 디자인하는 동안 적응형 Forms 작성자가 제공한 유효성 검사를 실행할 수도 있습니다. 양식 유효성 검사 측면에서 표시되는 데이터 제출 및 비즈니스 규칙 위반의 가능한 타협을 방지합니다.

### 서버에서 확인할 사항 {#what-to-validate-on-server-br}

서버에서 다시 실행되는 적응형 양식의 모든 즉시 사용 가능한(OOTB) 필드 유효성 검사는 다음과 같습니다.

* 필수
* 유효성 검사 그림 절
* 유효성 검사 표현식

### 서버측 유효성 검사 활성화 {#enabling-server-side-validation-br}

사용 **[!UICONTROL 서버에서 다시 유효성 검사]** 사이드바의 적응형 양식 컨테이너 아래에서 현재 양식에 대한 서버측 유효성 검사를 활성화하거나 비활성화합니다.

![서버측 유효성 검사 활성화](assets/revalidate-on-server.png)

서버측 유효성 검사 활성화

최종 사용자가 이러한 유효성 검사를 무시하고 양식을 제출하는 경우 서버에서 유효성 검사를 다시 수행합니다. 서버 끝에서 유효성 검사가 실패하면 제출 트랜잭션이 중지됩니다. 최종 사용자에게 다시 원래 양식이 표시됩니다. 캡처된 데이터 및 제출된 데이터는 에러로서 사용자에게 제시된다.

>[!NOTE]
>
>서버 측 유효성 검사가 양식 모델의 유효성을 검사합니다. 유효성 검사를 위해 별도의 클라이언트 라이브러리를 만들고 동일한 클라이언트 라이브러리에서 HTML 스타일링 및 DOM 조작과 같은 다른 항목과 혼합하지 않는 것이 좋습니다.

### 유효성 검사 표현식에서 사용자 지정 함수 지원 {#supporting-custom-functions-in-validation-expressions-br}

다음과 같은 경우 **복잡한 유효성 검사 규칙**, 정확한 유효성 검사 스크립트는 사용자 정의 함수에 상주하며 작성자는 필드 유효성 검사 표현식에서 이러한 사용자 정의 함수를 호출합니다. 서버측 유효성 검사를 수행하는 동안 이 사용자 정의 함수 라이브러리를 알고 사용할 수 있도록 양식 작성자는 아래 AEM 클라이언트 라이브러리의 이름을 구성할 수 있습니다. **[!UICONTROL 기본]** 아래 표시된 대로 적응형 양식 컨테이너 속성의 탭

![유효성 검사 표현식에서 사용자 지정 함수 지원](assets/clientlib-cat.png)

유효성 검사 표현식에서 사용자 지정 함수 지원

작성자는 적응형 양식에 따라 customJavaScript 라이브러리를 구성할 수 있습니다. 라이브러리에서 jquery 및 underscore.js 타사 라이브러리에 종속성이 있는 재사용 가능한 함수만 유지합니다.

## 제출 액션 시 오류 처리 {#error-handling-on-submit-action}

AEM 보안 및 강화 지침의 일부로 400.jsp, 404.jsp 및 500.jsp와 같은 사용자 지정 오류 페이지를 구성합니다. 이러한 처리기는 양식 400, 404 또는 500 오류를 제출할 때 호출됩니다. 이러한 오류 코드가 Publish 노드에서 트리거되면 핸들러도 호출됩니다. 다른 HTTP 오류 코드에 대한 JSP 페이지를 생성할 수도 있습니다.

양식 데이터 모델 또는 스키마 기반 적응형 양식에 데이터가 포함되지 않은 스키마에 대한 XML 또는 JSON 데이터 컴플레인을 미리 채우는 경우 `<afData>`, `<afBoundData>`, 및 `</afUnboundData>` 태그를 지정하면 적응형 양식의 제한되지 않은 필드 데이터가 손실됩니다. 스키마는 XML 스키마, JSON 스키마 또는 양식 데이터 모델일 수 있습니다. 제한되지 않은 필드는 이 없는 적응형 양식 필드입니다. `bindref` 속성.

<!-- For more information, see [Customizing Pages shown by the Error Handler](/help/sites-developing/customizing-errorhandler-pages.md). -->
