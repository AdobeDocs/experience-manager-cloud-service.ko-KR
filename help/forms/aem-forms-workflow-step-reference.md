---
title: 워크플로우를 다른 사용자에게 할당하고, 이메일을 보내고, 워크플로우에서 Adobe Sign을 사용하는 방법
description: Forms 중심의 워크플로우를 통해 적응형 Forms 기반 워크플로우를 신속하게 구축할 수 있습니다. Adobe Sign을 사용하여 문서에 전자 서명하고, 양식 기반 비즈니스 프로세스를 만들고, 데이터를 검색 및 여러 데이터 소스로 보내고, 이메일 알림을 보낼 수 있습니다
exl-id: e1403ba6-8158-4961-98a4-2954b2e32e0d
google-site-verification: A1dSvxshSAiaZvk0yHu7-S3hJBb1THj0CZ2Uh8N_ck4
source-git-commit: a8dae80f79e32117341519b31c389f8fc30b5957
workflow-type: tm+mt
source-wordcount: '6132'
ht-degree: 1%

---

# Forms 중심의 AEM 워크플로우 - 단계 참조 {#forms-centric-workflow-on-osgi-step-reference}

워크플로우 모델을 사용하여 비즈니스 로직을 자동화된 반복 프로세스로 변환합니다. 모델은 일련의 단계를 정의하고 실행하는 데 도움이 됩니다. 워크플로우가 일시적인지 또는 여러 리소스를 사용하는지 등의 모델 속성을 정의할 수도 있습니다. 다음을 수행할 수 있습니다 [모델에 다양한 AEM 워크플로우 단계를 포함시켜 비즈니스 논리를 수행합니다](https://experienceleague.adobe.com/docs/experience-manager-65/developing/extending-aem/extending-workflows/workflows-models.html?lang=en#extending-aem).

## Forms 중심 단계 {#forms-workflow-steps}

Forms 중심의 워크플로우 단계는 AEM Workflow에서 AEM Forms 관련 작업을 수행합니다. 이러한 단계를 통해 OSGi에서 적응형 Forms 기반의 Forms 중심 워크플로우를 신속하게 구축할 수 있습니다. 이러한 워크플로우는 기본 검토 및 승인 작업 과정, 내부 및 방화벽 내 업무 프로세스를 개발하는 데 사용할 수 있습니다. Forms Workflow 단계를 사용하여 다음을 수행할 수도 있습니다.

* 비즈니스 프로세스, 제출 후 워크플로우 및 백엔드 워크플로우를 만들어 등록 프로세스를 관리합니다.

* 사용자 또는 그룹에 작업을 만들고 할당합니다.

* 사용 [!DNL Adobe Sign] AEM Workflow에서 서명을 위한 문서를 전송합니다.

* 요청 시 또는 양식 제출 시 기록 문서를 생성합니다.

* 다양한 데이터 소스와 워크플로우 모델을 연결하여 데이터를 쉽게 저장하고 검색할 수 있습니다.

* 전자 메일 단계를 사용하여 작업 완료 및 워크플로우 시작 또는 완료 시 알림 전자 메일 및 기타 첨부 파일을 보낼 수 있습니다.

>[!NOTE]
>
>워크플로우 모델이 외부 스토리지에 대해 표시된 경우 모든 Forms 워크플로우 단계에 대해 변수 옵션만 선택하여 데이터 파일과 첨부 파일을 저장하거나 검색할 수 있습니다.


## 작업 단계 할당 {#assign-task-step}

작업 할당 단계에서는 작업 항목을 만들어 사용자 또는 그룹에 지정합니다. 작업 할당과 함께 구성 요소는 작업에 대한 적응형 양식 또는 비대화형 PDF도 지정합니다. 적응형 양식은 사용자의 입력을 수용하기 위해 필요하며 비대화형 PDF 또는 읽기 전용 적응형 양식은 검토 전용 워크플로우에 사용됩니다.

구성 요소를 사용하여 작업의 동작을 제어할 수도 있습니다. 예를 들어, 자동 기록 문서 작성, 특정 사용자 또는 그룹에 작업 할당, 제출된 데이터의 경로 지정, 미리 채울 데이터 경로 지정 및 기본 작업 지정 등의 작업을 수행할 수 있습니다. 작업 할당 단계에는 다음 속성이 있습니다.

* **[!UICONTROL 제목]**: 작업의 제목입니다. 제목이 AEM 받은 편지함에 표시됩니다.
* **[!UICONTROL 설명]**: 작업에서 수행 중인 작업에 대한 설명입니다. 이 정보는 공유 개발 환경에서 작업할 때 다른 프로세스 개발자에게 유용합니다.

* **[!UICONTROL 축소판 경로]**: 작업 축소판의 경로입니다. 경로를 지정하지 않으면 적응형 양식 기본 축소판이 표시되고 레코드 문서에 대해 기본 아이콘이 표시됩니다.
* **[!UICONTROL 워크플로우 단계]**: 워크플로우에는 여러 단계가 있을 수 있습니다. 이러한 단계는 AEM 받은 편지함에 표시됩니다. 모델의 속성(사이드 킥과 페이지 > 페이지 속성 > 단계)에서 이러한 단계를 정의할 수 있습니다.
* **[!UICONTROL 우선순위]**: 선택한 우선순위가 AEM 받은 편지함에 표시됩니다. 사용 가능한 옵션은 높음, 중간, 낮음입니다. 기본값은 보통입니다.
* **[!UICONTROL 기한]**: 작업 지연으로 표시된 후 일 또는 시간 수를 지정합니다. 선택하는 경우 **[!UICONTROL 해제]**&#x200B;을 지정하면 작업이 지연으로 표시되지 않습니다. 작업 기한이 지난 후 특정 작업을 수행할 시간 초과 처리기를 지정할 수도 있습니다.

* **[!UICONTROL 일]**: 작업을 완료하기 전 일 수입니다. 작업이 사용자에게 지정된 후 일 수가 계산됩니다. 작업이 완료되지 않고 일 필드에 지정된 일 수를 교차하는 경우, 이 옵션을 선택하면 기한 후 시간 초과 처리기가 트리거됩니다.
* **[!UICONTROL 시간]**: 작업을 완료하기 전 시간 작업이 사용자에게 지정된 후 시간 수가 계산됩니다. 작업이 완료되지 않고 시간 필드에 지정된 시간 수를 교차하는 경우, 이 옵션을 선택하면 시간 초과 처리기가 기한 후 트리거됩니다.
* **[!UICONTROL 기한 후 시간 초과]**: 시간 초과 처리기 선택 필드를 사용하려면 이 옵션을 선택합니다.
* **[!UICONTROL 시간 제한 처리기]**: 작업 할당 단계가 기한 일자를 넘을 때 실행할 스크립트를 선택합니다. 다음 위치의 CRX 저장소에 배치된 스크립트 [앱]/fd/dashboard/scripts/timeoutHandler 를 선택할 수 있습니다. 지정된 경로가 crx-repository에 없습니다. 관리자는 이 경로를 사용하기 전에 만듭니다.
* **[!UICONTROL 작업 세부 정보의 마지막 작업에서 작업 및 주석 강조 표시]**: 작업의 작업 세부 사항 섹션에서 마지막으로 수행한 작업과 받은 설명을 표시하려면 이 옵션을 선택합니다.
* **[!UICONTROL 유형]**: 워크플로우를 시작할 때 채울 문서 유형을 선택합니다. 적응형 양식, 읽기 전용 적응형 양식, 비대화형 PDF 문서를 선택할 수 있습니다.

<!-- , Interactive Communication Agent UI, or Interactive Communication Web Channel Document. -->


* **[!UICONTROL 적응형 양식 사용]**: 입력 적응형 양식을 찾을 방법을 지정합니다. 유형 드롭다운 목록에서 적응형 양식 또는 읽기 전용 적응형 양식을 선택하는 경우 이 옵션을 사용할 수 있습니다. 워크플로우에 제출된 적응형 양식을 사용하거나, 절대 경로에서 사용하거나, 변수의 경로에서 사용할 수 있습니다. 문자열 유형의 변수를 사용하여 경로를 지정할 수 있습니다.\
   여러 적응형 Forms을 워크플로우와 연결할 수 있습니다. 따라서 사용 가능한 입력 방법을 사용하여 런타임에 적응형 양식을 지정할 수 있습니다.

<!-- 

* **[!UICONTROL Use Interactive Communication]**: Specify the method to locate the input interactive communication. You can use the interactive communication submitted to the workflow, available at an absolute path, or available at a path in a variable. You can use a variable of type String to specify the path. This option is available if you select Interactive Communication Agent UI or Interactive Communication Web Channel Document from the Type drop-down list. 

> [!NOTE]
>
>You must have cm-agent-users and workflow-users group assignments to access Interactive Communications Agent UI in AEM inbox.  

-->

* **[!UICONTROL 적응형 양식 경로]**: 적응형 양식의 경로를 지정합니다. 워크플로우에 제출되거나, 절대 경로에서 사용할 수 있는 적응형 양식을 사용하거나, 문자열 데이터 유형의 변수에 저장된 경로에서 적응형 양식을 검색할 수 있습니다.
* **[!UICONTROL 을 사용하여 입력 PDF 선택]**: 비대화형 PDF 문서의 경로를 지정합니다. 유형 필드에서 비대화형 PDF 문서를 선택하면 필드를 사용할 수 있습니다. 페이로드를 기준으로 하거나 절대 경로에 저장하거나 문서 데이터 유형의 변수를 사용하여 입력 PDF을 선택할 수 있습니다. 예, [Payload_Directory]/Workflow/PDF/credit-card.pdf 경로가 crx-repository에 없습니다. 관리자는 이 경로를 사용하기 전에 만듭니다. PDF 경로 옵션을 사용하려면 레코드 문서 옵션을 활성화하거나 적응형 Forms 기반의 양식 템플릿이 필요합니다.
* **[!UICONTROL 완료된 작업의 경우 적응형 양식을 다음으로 렌더링합니다.]**: 작업이 완료됨으로 표시되면 적응형 양식을 읽기 전용 적응형 양식 또는 PDF 문서로 렌더링할 수 있습니다. 적응형 양식을 기록 문서로 렌더링하려면 기록 문서 옵션이 활성화되거나 양식 서식 파일 기반의 적응형 Forms이 필요합니다.
* **[!UICONTROL 미리 채워짐]**: 아래 나열된 다음 필드는 작업에 대한 입력으로 사용됩니다.

   * **[!UICONTROL 을 사용하여 입력 데이터 파일 선택]**: 입력 데이터 파일의 경로(.json, .xml, .doc 또는 양식 데이터 모델). 페이로드를 기준으로 하는 경로를 사용하여 입력 데이터 파일을 검색하거나 Document, XML 또는 JSON 데이터 유형의 변수에 저장된 파일을 검색할 수 있습니다. 예를 들어 파일에는 AEM 받은 편지함 애플리케이션을 통해 양식에 대해 제출된 데이터가 포함되어 있습니다. 경로의 예는 다음과 같습니다 [Payload_Directory]/workflow/data.
   * **[!UICONTROL 을 사용하여 입력 첨부 파일 선택]**: 위치에서 사용할 수 있는 첨부 파일은 작업과 관련된 양식에 첨부됩니다. 페이로드에 상대적인 경로를 사용하거나 문서의 변수에 저장된 첨부 파일을 검색할 수 있습니다. 경로의 예는 다음과 같습니다 [Payload_Directory]/attachments/. 페이로드를 기준으로 배치된 첨부 파일을 지정하거나 문서 유형(배열 목록 > 문서) 변수를 사용하여 적응형 양식의 입력 첨부 파일을 지정할 수 있습니다.

   <!-- 
    
    * **[!UICONTROL Choose input JSON]**: Select an input JSON file using a path that is relative to payload or stored in a variable of Document, JSON, or Form Data Model data type. This option is available if you select Interactive Communication Agent UI or Interactive Communication Web Channel Document from the Type drop-down list.

    * **[!UICONTROL Choose a custom prefill service]**: Select the prefill service to retrieve the data and prefill the Interactive Communication Web channel document or the Agent UI.  
    
    * **[!UICONTROL Use the prefill service of the interactive communication selected above]**: Use this option to use the prefill service of the Interactive Communication defined in the Use Interactive Communication drop-down list. 
    
    -->

   * **[!UICONTROL 요청 속성 매핑]**: 요청 속성 매핑 섹션을 사용하여 [요청 속성의 이름 및 값](work-with-form-data-model.md#bindargument). 요청에 지정된 속성 이름 및 값을 기반으로 데이터 소스에서 세부 정보를 검색합니다. 리터럴 값 또는 문자열 데이터 유형의 변수를 사용하여 요청 속성 값을 정의할 수 있습니다.

   <!--  
     
     The prefill service and request attribute mapping options are available only if you select Interactive Communication Agent UI or Interactive Communication Web Channel Document from the Type drop-down list. 
     
     -->

* **[!UICONTROL 제출된 정보]**: 아래 나열된 다음 필드는 작업의 출력 위치로 사용됩니다.

   * **[!UICONTROL 다음 방법으로 출력 데이터 파일 저장]**: 데이터 파일(.json, .xml, .doc 또는 양식 데이터 모델)을 저장합니다. 데이터 파일에는 관련 양식을 통해 제출된 정보가 들어 있습니다. 페이로드를 기준으로 하는 경로를 사용하여 출력 데이터 파일을 저장하거나 문서, XML 또는 JSON 데이터 유형의 변수에 저장할 수 있습니다. 예, [Payload_Directory]/Workflow/data. 여기서 데이터는 파일입니다.
   * **[!UICONTROL 을 사용하여 첨부 파일 저장]**: 작업에 제공된 양식 첨부 파일을 저장합니다. 페이로드를 기준으로 하는 경로를 사용하여 첨부 파일을 저장하거나 문서 데이터 유형의 배열 목록에 저장할 수 있습니다.
   * **[!UICONTROL 다음을 사용하여 기록 문서 저장]**: 레코드 문서를 저장하는 경로입니다. 예, [Payload_Directory]/DocumentofRecord/credit-card.pdf 페이로드를 기준으로 하는 경로를 사용하여 레코드 문서를 저장하거나 문서 데이터 유형의 변수에 저장할 수 있습니다. 선택하는 경우 **[!UICONTROL 페이로드에 대한 상대]** 옵션을 선택하면 경로 필드가 비어 있는 경우 기록 문서가 생성되지 않습니다. 이 옵션은 유형 드롭다운 목록에서 적응형 양식을 선택하는 경우에만 사용할 수 있습니다.

   <!-- 
    
    * **[!UICONTROL Save Web Channel data using]**: Save the Web Channel data file using a path that is relative to the payload or store it in a variable of Document, JSON, or Form Data Model data type. This option is available only if you select Interactive Communication Agent UI from the Type drop-down list. c
    * **[!UICONTROL Save PDF document using]**: Save the PDF document using a path that is relative to the payload or store it in a variable of Document data type. This option is available only if you select Interactive Communication Agent UI from the Type drop-down list.
    <!-- * **[!UICONTROL Save layout template using]**: Save the layout template using a path that is relative to the payload or store it in a variable of Document data type. The [layout template](layout-design-details.md) refers to an XDP file that you create using Forms Designer. This option is available only if you select Interactive Communication Agent UI from the Type drop-down list. 
    
    -->

* **[!UICONTROL 할당자]** > **[!UICONTROL 옵션 할당]**: 사용자에게 작업을 할당할 방법을 지정합니다. 참가자 선택기 스크립트를 사용하여 사용자 또는 그룹에 작업을 동적으로 할당하거나 특정 AEM 사용자 또는 그룹에 작업을 지정할 수 있습니다.
* **[!UICONTROL 참가자 선택기]**: 이 옵션은 **[!UICONTROL 동적으로 사용자 또는 그룹에 추가]** 옵션 지정 필드에서 옵션이 선택되어 있습니다. ECMAScript 또는 서비스를 사용하여 사용자나 그룹을 동적으로 선택할 수 있습니다. 자세한 내용은 [사용자에게 워크플로우를 동적으로 할당](https://helpx.adobe.com/experience-manager/kb/HowToAssignAWorkflowDynamicallyToParticipants.html) 및 [사용자 지정 Adobe Experience Manager 동적 참가자 단계 만들기](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-wknd-tutorial-develop/overview.html?lang=en&amp;CID=RedirectAEMCommunityKautuk)

* **[!UICONTROL 참가자]**: 이 필드는 **[!UICONTROL com.adobe.granite.workflow.core.process.RandomParticipantSelector]** 옵션이 **[!UICONTROL 참가자 선택기]** 필드. 필드에서는 RandomParticipantSelector 옵션의 사용자 또는 그룹을 선택할 수 있습니다.

* **[!UICONTROL 할당자]**: 이 필드는 **[!UICONTROL com.adobe.fd.workspace.step.service.VariableParticipantSelector]** 에서 선택됨 **[!UICONTROL 참가자 선택기]** 필드. 필드에서는 String 데이터 유형의 변수를 선택하여 담당자를 정의할 수 있습니다.

* **[!UICONTROL 인수]**: 이 필드는 참가자 선택기 필드에서 RandomParticipantChoose 스크립트 이외의 스크립트를 선택한 경우 사용할 수 있습니다. 필드에서는 참가자 선택기 필드에서 선택한 스크립트에 대해 쉼표로 구분된 인수 목록을 제공할 수 있습니다.

* **[!UICONTROL 사용자 또는 그룹]**: 작업이 선택한 사용자 또는 그룹에 할당됩니다. 이 옵션은 **[!UICONTROL 특정 사용자 또는 그룹 옵션]** 에서 선택됨 **[!UICONTROL 옵션 할당]** 필드. 이 필드에는 [!DNL workflow-users] 그룹에 속해 있어야 합니다.\
   다음 **[!UICONTROL 사용자 또는 그룹]** 드롭다운 메뉴에는 로그인한 사용자가 액세스할 수 있는 사용자 및 그룹이 나열됩니다. 사용자 이름 표시에는 **[!UICONTROL 사용자]** 특정 사용자에 대한 crx-repository의 노드.

* **[!UICONTROL 알림 이메일 보내기]**: 할당자에게 전자 메일 알림을 전송하려면 이 옵션을 선택합니다. 이러한 알림은 작업이 사용자 또는 그룹에 할당되면 전송됩니다. 를 사용할 수 있습니다 **[!UICONTROL 수신자 이메일 주소]** 이메일 주소를 검색하는 메커니즘을 지정하는 옵션.

* **[!UICONTROL 수신자 이메일 주소]**: e-메일 주소를 변수에 저장하거나, 리터럴을 사용하여 영구 전자 메일 주소를 지정하거나, 할당자의 프로필에 지정된 할당자의 기본 전자 메일 주소를 사용할 수 있습니다. 리터럴 또는 변수를 사용하여 그룹의 이메일 주소를 지정할 수 있습니다. 변수 옵션은 전자 메일 주소를 동적으로 검색하고 사용하는 데 유용합니다. 다음 **[!UICONTROL 할당자의 기본 전자 메일 주소 사용]** 옵션은 단일 할당자에 대해서만 제공됩니다. 이 경우 지정된 사용자 프로필에 저장된 이메일 주소가 사용됩니다.

* **[!UICONTROL HTML 이메일 템플릿]**: 알림 이메일에 사용할 이메일 템플릿을 선택합니다. 템플릿을 편집하려면 crx-repository에서 /libs/fd/dashboard/templates/email/htmlEmailTemplate.txt에 있는 파일을 수정합니다.
* **[!UICONTROL 위임 허용]**: AEM 받은 편지함은 로그인한 사용자에게 할당된 워크플로우를 다른 사용자에게 위임하는 옵션을 제공합니다. 동일한 그룹 내에서 또는 다른 그룹의 워크플로우 사용자에게 위임할 수 있습니다. 작업이 단일 사용자 및 **[!UICONTROL 할당자 그룹의 구성원에게 위임 허용]** 옵션을 선택한 경우 작업을 다른 사용자 또는 그룹에 위임할 수 없습니다.
* **[!UICONTROL 공유 설정]**: AEM 받은 편지함은 받은 편지함에서 단일 또는 모든 작업을 다른 사용자와 공유하는 옵션을 제공합니다.
   * 이 **[!UICONTROL 할당자가 받은 편지함에서 명시적으로 공유할 수 있도록 허용]** 옵션을 선택하면 사용자는 AEM 받은 편지함에서 작업을 선택하고 다른 AEM 사용자와 공유할 수 있습니다.
   * 이 **[!UICONTROL 할당자가 받은 편지함 공유를 통해 공유 허용]** 옵션이 선택되어 있고 사용자가 자신의 받은 편지함 항목을 공유하거나 다른 사용자가 자신의 받은 편지함 항목에 액세스할 수 있도록 허용되며, 이전에 언급된 옵션이 활성화된 작업만 다른 사용자와 공유됩니다.
   * 이 **[!UICONTROL 할당자가 &#39;부재 중&#39; 설정을 사용하여 위임하도록 허용]** 이 선택되어 있습니다. 할당자는 다른 부재 중 옵션과 함께 작업을 다른 사용자에게 위임하는 옵션을 활성화할 수 있습니다. 부재 사용자에게 할당된 새 작업은 부재 설정에 언급된 사용자에게 자동으로 위임(할당)됩니다.

   이 기능을 사용하면 부재 중 다른 사용자가 할당된 작업을 선택할 수 있으며 할당된 작업을 수행할 수 없습니다.

* **[!UICONTROL 작업]** > **[!UICONTROL 기본 작업]**: 즉시 제출, 저장 및 재설정 작업을 사용할 수 있습니다. 기본적으로 모든 기본 작업이 활성화됩니다.
* **[!UICONTROL 경로 변수]**: 경로 변수의 이름입니다. 경로 변수는 사용자가 AEM 받은 편지함에서 선택하는 사용자 지정 작업을 캡처합니다.
* **[!UICONTROL 경로]**: 작업은 다른 경로에 분기될 수 있습니다. AEM 받은 편지함에서 선택하면 경로에는 값이 반환되고 선택한 경로를 기준으로 워크플로우 분기가 반환됩니다. String 데이터 유형의 배열에 경로를 저장하거나 를 선택할 수 있습니다 **[!UICONTROL 리터럴]** 경로를 수동으로 추가하려면

* **[!UICONTROL 경로 제목]**: 경로의 제목을 지정합니다. AEM 받은 편지함에 표시됩니다.
* **[!UICONTROL Coral 아이콘]**: coral 아이콘의 HTML 속성을 지정합니다. Adobe CoreUI 라이브러리는 방대한 터치 첫 번째 아이콘 세트를 제공합니다. 라우트의 아이콘을 선택하여 사용할 수 있습니다. AEM 받은 편지함에 제목과 함께 표시됩니다. 경로에 기본 &#39;태그&#39; coral 아이콘이 사용됩니다.
* **[!UICONTROL 할당자가 댓글을 추가할 수 있도록 허용]**: 작업에 대한 설명을 활성화하려면 이 옵션을 선택합니다. 할당자는 작업 제출 시 AEM 받은 편지함 내에서 주석을 추가할 수 있습니다.
* **[!UICONTROL 변수에 주석 저장]**: String 데이터 유형의 변수에 설명을 저장합니다. 이 옵션은 **[!UICONTROL 할당자가 댓글을 추가할 수 있도록 허용]** 확인란을 선택합니다.

* **[!UICONTROL 할당자가 작업에 첨부 파일을 추가할 수 있도록 허용]**: 작업에 대한 첨부 파일을 사용하려면 이 옵션을 선택합니다. 할당자는 작업 제출 시 AEM 받은 편지함 내에서 첨부 파일을 추가할 수 있습니다. 최대 크기를 제한할 수도 있습니다 **[!UICONTROL (최대 파일 크기)]** 첨부 파일 기본 크기는 2MB입니다.

* **[!UICONTROL 출력 작업 첨부 파일 저장]**: 첨부 파일의 위치를 지정합니다. 페이로드와 관련된 경로 또는 문서 데이터 유형의 배열 변수를 사용하여 출력 작업 첨부 파일을 저장할 수 있습니다. 이 옵션은 **[!UICONTROL 할당자가 작업에 첨부 파일을 추가할 수 있도록 허용]** 확인란을 선택하고 **[!UICONTROL 적응형 양식]**, **[!UICONTROL 읽기 전용 적응형 양식]**, 또는 **[!UICONTROL 비대화형 PDF 문서]** 에서 **[!UICONTROL 유형]** 의 드롭다운 목록 **[!UICONTROL 양식/문서]** 탭.

* **[!UICONTROL 사용자 지정 메타데이터 사용]**: 사용자 지정 메타데이터 필드를 활성화하려면 이 옵션을 선택합니다. 사용자 지정 메타데이터는 이메일 템플릿에 사용됩니다.
* **[!UICONTROL 사용자 지정 메타데이터]**: 이메일 템플릿에 대한 사용자 지정 메타데이터를 선택합니다. 사용자 지정 메타데이터는 apps/fd/dashboard/scripts/metadataScripts의 crx 저장소에서 사용할 수 있습니다. 지정된 경로가 crx-repository에 없습니다. 관리자는 이 경로를 사용하기 전에 만듭니다. 사용자 지정 메타데이터에 서비스를 사용할 수도 있습니다. 또한 `WorkitemUserMetadataService` 사용자 지정 메타데이터를 제공하는 인터페이스입니다.
* **[!UICONTROL 이전 단계의 데이터 표시]**: 이 옵션을 선택하면 담당자에게 이전 담당자, 작업에 이미 수행된 작업, 작업에 추가된 댓글, 사용 가능한 경우 완료된 작업의 기록 문서를 볼 수 있습니다.
* **[!UICONTROL 후속 단계의 데이터 표시]**: 현재 할당자가 후속 할당자가 작업에 추가한 작업과 설명을 보려면 이 옵션을 선택합니다. 또한 현재 할당자가 사용 가능한 경우 완료된 작업의 기록 문서를 볼 수 있습니다.
* **[!UICONTROL 데이터 유형의 가시성]**: 기본적으로 할당자는 이전 및 이후 할당자가 추가한 기록 문서, 담당자, 조치 및 설명을 볼 수 있습니다. 할당자에게 표시되는 데이터 유형을 제한하려면 데이터 유형 표시 옵션을 사용합니다.

>[!NOTE]
>
>외부 데이터 저장소에 대해 AEM 워크플로우 모델을 구성할 때 작업 할당 단계를 초안으로 저장하고 작업 할당 단계의 기록을 검색하는 옵션이 비활성화됩니다. 또한 받은 편지함에서 저장 옵션이 비활성화됩니다.

## PDF/A 단계로 변환 {#convert-pdfa}

PDF/A는 글꼴을 포함하여 파일의 압축을 해제함으로써 문서의 컨텐츠를 장기간 보존할 수 있는 보관 형식입니다. 따라서 PDF/A 문서는 일반적으로 표준 PDF 문서보다 큽니다. 를 사용할 수 있습니다 ***PDF/A로 변환*** AEM Workflow에서 단계를 수행하여 PDF 문서를 PDF/A 형식으로 변환합니다.

PDF/A 단계로 변환하려면 다음 속성을 사용합니다.

**[!UICONTROL 입력 문서]**: 입력 문서는 페이로드를 기준으로 할 수 있으며 절대 경로를 가지거나 페이로드로 제공하거나 문서 데이터 유형의 변수에 저장할 수 있습니다.

**[!UICONTROL 전환 옵션]**: 이 속성을 사용하면 PDF 문서를 PDF/A 문서로 변환하는 설정이 지정됩니다. 이 탭에서 사용할 수 있는 다양한 옵션은 다음과 같습니다.
* **[!UICONTROL 규정 준수]**: 출력 PDF/A 문서가 준수해야 하는 표준을 지정합니다. 이 모델은 PDF/A-1b, PDF/A-2b 또는 PDF/A-3b와 같은 다양한 PDF 표준을 지원합니다.
* **[!UICONTROL 결과 수준]**: 변환 출력에 대한 결과 레벨을 PassFail, Summary 또는 Detailed로 지정합니다.
* **[!UICONTROL 색상 공간]**: 출력 PDF/A 파일에 사용할 수 있는 미리 정의된 색상 공간을 S_RGB, COATED_FOGRA27, JAPAN_COLOR_COATED 또는 SWOP로 지정합니다.
* **[!UICONTROL 선택적 콘텐츠]**: 지정된 기준 세트를 충족할 때만 출력 PDF/문서에 특정 그래픽 객체 및/또는 주석을 표시할 수 있습니다.

**[!UICONTROL 출력 문서]**: 출력 파일을 저장할 위치를 지정합니다. 출력 파일은 페이로드와 관련된 위치에 저장되고, 페이로드를 덮어쓰고, 페이로드가 파일인 경우 또는 문서 데이터 유형의 변수에 저장할 수 있습니다.


## 이메일 전송 단계 {#send-email-step}

전자 메일 단계를 사용하여 전자 메일(예: 기록 문서, 적응형 양식 링크 포함)을 보낼 수 있습니다 <!-- , link of an interactive communication-->또는 연결된 PDF 문서가 있는 상태로 전송됩니다. 이메일 전송 단계에서 지원 [HTML 이메일](https://en.wikipedia.org/wiki/HTML_email). HTML 이메일은 응답형이며 수신자의 이메일 클라이언트 및 화면 크기에 맞게 조정됩니다. HTML 이메일 템플릿을 사용하여 이메일의 모양, 색상 구성표 및 동작을 정의할 수 있습니다.

이메일 단계에서는 Day CQ Mail Service를 사용하여 이메일을 전송합니다. 이메일 단계를 사용하기 전에 이메일 서비스가 구성되어 있는지 확인하십시오. 이메일은 기본적으로 HTTP 및 HTTP 프로토콜만 지원합니다. [지원 팀에 문의](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/development-guidelines.html?lang=en#sending-email) 전자 메일 전송을 위한 포트를 활성화하고 환경에 대해 SMTP 프로토콜을 사용하도록 설정합니다. 제한 사항은 플랫폼의 보안을 개선하는 데 도움이 됩니다.

이메일 단계에는 다음 속성이 있습니다.

**[!UICONTROL 제목]**: 단계의 제목은 워크플로우 편집기에서 단계를 식별하는 데 도움이 됩니다.

**[!UICONTROL 설명]**: 설명은 공유 개발 환경에서 작업할 때 다른 프로세스 개발자에게 유용합니다.

**[!UICONTROL 이메일 제목]**: 제목은 워크플로우 메타데이터에서 검색하거나, 수동으로 지정하거나, 변수에 저장된 값에서 검색할 수 있습니다. 다음 옵션 중에서 선택합니다.

* **[!UICONTROL 리터럴]** 제목을 수동으로 지정합니다.
* **[!UICONTROL 워크플로우 메타데이터에서 검색]** - 메타데이터 속성에서 제목을 검색합니다.
* **[!UICONTROL 변수]** - 문자열 데이터 유형의 변수에 저장된 값에서 제목을 검색합니다.

**[!UICONTROL HTML 이메일 템플릿]**: 이메일에 대한 HTML 템플릿입니다. 이메일 템플릿에 변수를 지정할 수 있습니다. 이메일 단계에서 입력을 위해 템플릿에 포함된 모든 변수를 추출하고 표시합니다.

**[!UICONTROL 이메일 템플릿 메타데이터]**: 이메일 템플릿 변수 값은 사용자가 지정하는 값, 작성자 또는 게시 서버의 자산 경로, 이미지 또는 워크플로우 메타데이터 속성일 수 있습니다.

* **[!UICONTROL 리터럴]**: 지정할 정확한 값을 알고 있는 경우 옵션을 사용합니다. 예, [example@example.com](mailto:example@example.com).

* **[!UICONTROL 워크플로우 메타데이터]**: 사용할 값이 워크플로우 메타데이터 속성에 저장되면 옵션을 사용합니다. 옵션을 선택한 후 워크플로우 메타데이터 옵션 아래의 빈 텍스트 상자에 메타데이터 속성 이름을 입력합니다. 예를 들어 emailAddress가 있습니다.

<!-- 

* **[!UICONTROL Asset URL]**: Use the option to embed a web link of an interactive communication to the email. After selecting the option, browse and choose the interactive communication to embed. The asset can reside on the author or the publish server. 

-->

* **[!UICONTROL 이미지]**: 이메일에 이미지를 포함하려면 옵션을 사용합니다. 옵션을 선택한 후 이미지를 찾아 선택합니다. 이미지 옵션은 이메일 템플릿에서 사용할 수 있는 이미지 태그(&lt;img src=&quot;&lt;span id=&quot; translate=&quot;no&quot; />&quot;/>)에만 사용할 수 있습니다.&#42;

**[!UICONTROL 보낸 사람 / 받는 사람의 이메일 주소]**: 을(를) 선택합니다 **[!UICONTROL 리터럴]** 이메일 주소를 수동으로 지정하거나 선택하는 옵션 **[!UICONTROL 워크플로우 메타데이터에서 검색]** 메타데이터 속성에서 이메일 주소를 검색하는 옵션입니다. 에 대한 메타데이터 속성 배열 목록을 지정할 수도 있습니다 **[!UICONTROL 워크플로우 메타데이터에서 검색]** 선택 사항입니다. 을(를) 선택합니다 **[!UICONTROL 변수]** 문자열 데이터 유형의 변수에 저장된 값에서 이메일 주소를 검색하는 옵션입니다.

* **[!UICONTROL 파일 첨부]**: 지정된 위치에서 사용할 수 있는 자산이 전자 메일에 첨부됩니다. 자산의 경로는 페이로드 또는 절대 경로를 기준으로 할 수 있습니다. 경로의 예는 다음과 같습니다 [Payload_Directory]/attachments/.

을(를) 선택합니다 **[!UICONTROL 변수]** 문서, XML 또는 JSON 데이터 유형의 변수에 저장된 파일 첨부 파일을 검색하는 옵션입니다.

**[!UICONTROL 파일 이름]**: 전자 메일 첨부 파일의 이름입니다. 이메일 단계에서 첨부 파일의 원래 파일 이름을 지정된 파일 이름으로 변경합니다. 이름은 워크플로우 메타데이터 속성 또는 변수에서 수동으로 지정하거나 검색할 수 있습니다. 를 사용하십시오 **[!UICONTROL 리터럴]** 지정할 정확한 값을 알고 있는 경우 옵션을 선택합니다. 를 사용하십시오 **[!UICONTROL 변수]** 문자열 데이터 유형의 변수에 저장된 값에서 파일 이름을 검색하는 옵션입니다. 를 사용하십시오 **[!UICONTROL 워크플로우 메타데이터에서 검색]** 사용할 값이 워크플로우 메타데이터 속성에 저장되면 선택합니다.

## 레코드 문서 생성 단계 {#generate-document-of-record-step}

양식을 채우거나 제출하면 양식의 레코드를 인쇄나 문서 형식으로 유지할 수 있습니다. 이 레코드를 레코드 문서(DoR)라고 합니다. 기록 문서 생성 단계를 사용하여 적응형 양식의 읽기 전용 또는 대화형 PDF 버전을 만들 수 있습니다. PDF 버전에는 적응형 양식의 레이아웃과 함께 양식에 입력된 정보가 포함되어 있습니다.

레코드 문서 단계에는 다음 속성이 있습니다.

**[!UICONTROL 적응형 양식 사용]**: 입력 적응형 양식을 찾을 방법을 지정합니다. 워크플로우에 제출된 적응형 양식을 사용하거나, 절대 경로에서 사용하거나, 변수의 경로에서 사용할 수 있습니다. 문자열 데이터 유형의 변수를 사용하여 **[!UICONTROL 확인할 변수 선택]** 필드.\
여러 적응형 Forms을 워크플로우와 연결할 수 있습니다. 따라서 사용 가능한 입력 방법을 사용하여 런타임에 적응형 양식을 지정할 수 있습니다.

**[!UICONTROL 적응형 양식 경로]**: 적응형 양식의 경로를 지정합니다. 이 필드는 **[!UICONTROL 절대 경로에서 사용 가능]** 옵션 **[!UICONTROL 적응형 양식 사용]** 필드.

**[!UICONTROL 다음을 사용하여 입력 데이터 선택]**: 적응형 양식에 대한 입력 데이터의 경로입니다. 페이로드를 기준으로 한 위치에 데이터를 유지하거나, 데이터의 절대 경로를 지정하거나, Document, JSON 또는 XML 데이터 유형의 변수에 저장된 데이터를 검색할 수 있습니다. 입력 데이터는 적응형 양식과 병합되어 레코드 문서를 만듭니다.

**[!UICONTROL 다음을 사용하여 입력 첨부 경로 선택]**: 첨부 파일의 경로입니다. 이러한 첨부 파일은 기록 문서에 포함됩니다. 첨부 파일을 페이로드와 관련된 위치에 유지하거나 첨부 파일의 절대 경로를 지정하거나 문서 데이터 유형의 변수에 저장된 첨부 파일을 검색할 수 있습니다.

첨부 파일 등의 폴더 경로를 지정하면 폴더에서 직접 사용할 수 있는 모든 파일이 레코드 문서에 첨부됩니다. 지정한 첨부 경로에서 직접 사용할 수 있는 폴더에서 사용할 수 있는 파일이 있으면 첨부 파일로 기록 문서에 포함됩니다. 직접 사용 가능한 폴더에 폴더가 있으면 해당 폴더를 건너뜁니다.

**[!UICONTROL 아래 옵션을 사용하여 생성된 레코드 문서 저장]**: 문서 기록 파일을 보관할 위치를 지정합니다. 페이로드 폴더를 덮어쓰거나, 기록 문서를 페이로드 디렉토리 내의 위치에 배치하거나, 문서 데이터 유형의 변수에 저장할 수 있습니다.

**[!UICONTROL 로케일]**: 기록 문서의 언어를 지정합니다. 선택 **[!UICONTROL 리터럴]** 드롭다운 목록에서 로케일을 선택하거나 **[!UICONTROL 변수]** 문자열 데이터 유형의 변수에 저장된 값에서 로케일을 검색합니다. 로케일 값을 변수에 저장하는 동안 로케일 코드를 정의해야 합니다. 예를 들어 **en_US** - 영어 및 **fr_FR** 프랑스어로

## DDX 단계 호출 {#invokeddx}

DDX(Document Description XML)는 요소가 문서 빌딩 블록을 나타내는 선언적 마크업 언어입니다. 이러한 구성 요소에는 PDF 및 XDP 문서는 물론 댓글, 책갈피 및 스타일이 지정된 텍스트와 같은 기타 요소가 포함됩니다. DDX는 하나 이상의 입력 문서에 적용하여 하나 이상의 출력 문서를 생성할 수 있는 일련의 작업을 정의합니다.  단일 DDX를 다양한 원본 문서와 함께 사용할 수 있습니다. 를 사용할 수 있습니다 ***DDX 단계 호출*** AEM Workflow에서 문서 조립, 생성 및 수정, Acrobat 및 XFA Forms, 기타, [DDX 참조 설명서](https://helpx.adobe.com/content/dam/help/en/experience-manager/forms-cloud-service/ddxRef.pdf).

DDX 호출 단계에는 다음 속성이 있습니다.

**[!UICONTROL 입력 문서]**: 입력 문서의 속성을 설정하는 데 사용됩니다. 이 탭에서 사용할 수 있는 다양한 옵션은 다음과 같습니다.
* **[!UICONTROL 다음을 사용하여 DDX 지정]**: 페이로드를 기준으로 입력 문서를 지정하고, 절대 경로를 사용하거나, 페이로드로 제공하거나, 문서 데이터 형식의 변수에 저장할 수 있습니다.
* **[!UICONTROL 페이로드에서 맵 만들기]**: 페이로드 폴더 아래의 모든 문서를 어셈블러에서 호출 API에 대한 입력 문서의 맵에 추가합니다. 맵에서 각 문서의 노드 이름은 키로 사용됩니다.
* **[!UICONTROL 입력 문서의 맵]**: 옵션을 사용하면 **[!UICONTROL 추가]** 버튼을 클릭합니다. 각 항목은 맵에 있는 문서의 키와 문서의 소스를 나타냅니다.

**[!UICONTROL 환경 옵션]**: 이 옵션은 API 호출에 대한 처리 설정을 설정하는 데 사용됩니다. 이 탭에서 사용할 수 있는 다양한 옵션은 다음과 같습니다.
* **[!UICONTROL 유효성 검사만]**: 입력 DDX 문서의 유효성을 확인합니다.
* **[!UICONTROL 오류 시 실패]**: 오류가 발생한 경우 API 호출 서비스가 실패하는지 여부를 나타내는 부울 값입니다. 기본적으로 이 값은 False로 설정됩니다.
* **[!UICONTROL 첫 번째 베이츠 번호]**: 자가 증분자인 숫자를 지정합니다. 이러한 자체 증분 번호는 각 연속 페이지에 자동으로 표시됩니다.
* **[!UICONTROL 기본 스타일]**: 출력 파일의 기본 스타일을 설정합니다.

>[!NOTE]
>
>환경 옵션은 HTTP API와 계속 동기화됩니다.

**[!UICONTROL 출력 문서]**: 출력 파일을 저장할 위치를 지정합니다. 이 탭에서 사용할 수 있는 다양한 옵션은 다음과 같습니다.
* **[!UICONTROL 페이로드에서 출력 저장]**: 페이로드 폴더에 출력 문서를 저장하거나, 페이로드가 파일인 경우 페이로드를 덮어씁니다.
* **[!UICONTROL 출력 문서의 맵]**: 문서당 하나의 항목을 추가하여 각 문서 파일을 명시적으로 저장할 위치를 지정합니다. 각 항목은 문서와 해당 문서를 저장할 위치를 나타냅니다. 출력 문서가 여러 개인 경우 이 옵션이 사용됩니다.

## 양식 데이터 모델 서비스 단계 호출 {#invoke-form-data-model-service-step}

다음을 사용할 수 있습니다 [[!DNL AEM Forms] 데이터 통합](data-integration.md) 서로 다른 데이터 소스를 구성하고 연결할 수 있습니다. 이러한 데이터 소스는 웹 서비스, REST 서비스, OData 서비스 및 CRM 솔루션일 수 있습니다. [!DNL AEM Forms] 데이터 통합을 사용하면 구성된 데이터베이스에서 데이터 검색, 추가, 업데이트 작업을 수행하기 위해 다양한 서비스를 포함하는 양식 데이터 모델을 만들 수 있습니다. 를 사용할 수 있습니다 **[!UICONTROL 데이터 모델 서비스 단계 호출]** FDM(Form Data Model)을 선택하고 FDM의 서비스를 사용하여 서로 다른 데이터 소스에 데이터를 검색, 업데이트 또는 추가할 수 있습니다.

단계의 필드에 대한 입력을 설명하기 위해 다음 데이터베이스 테이블 및 JSON 파일이 예로 사용됩니다.

**[!UICONTROL 샘플 CustomerDetails 테이블]**

<table>
 <tbody> 
  <tr> 
   <td>속성</td> 
   <td>값<br /> </td> 
  </tr> 
  <tr> 
   <td>이름<br /> </td> 
   <td>사라<br /> </td> 
  </tr> 
  <tr> 
   <td>성</td> 
   <td>로즈</td> 
  </tr> 
  <tr> 
   <td>고객 ID</td> 
   <td>1</td> 
  </tr> 
  <tr> 
   <td>이메일 주소<br /> </td> 
   <td>srose@we.info</td> 
  </tr> 
 </tbody> 
</table>

**[!UICONTROL 샘플 JSON 파일]**

```json
  { 
    customer: { 
     firstName: "Sarah", 
     lastName:"Rose", 
     customerId: "1", 
     emailAddress:"srose@we.info" 
   }, 
    insurance: {
     customerId: "1", 
    policyType: "Premium,
    policyNumber: "Premium-521499",
    customerDetails: { 
     firstName: "Sarah",
     lastName: "Rose",
     customerId: "1",
     emailAddress: "srose@we.info" 
    }
   }
  }
```

양식 데이터 모델 서비스 호출 단계에는 양식 데이터 모델 작업을 용이하게 하기 위해 다음과 같은 필드가 나열되어 있습니다.

* **[!UICONTROL 제목]**: 단계의 제목입니다. 워크플로우 편집기에서 단계를 식별하는 데 도움이 됩니다.
* **[!UICONTROL 설명]**: 공유 개발 환경에서 작업하는 경우 다른 프로세스 개발자에게 유용한 설명입니다.

* **[!UICONTROL 양식 데이터 모델 경로]**: 서버에 있는 양식 데이터 모델을 찾아 선택합니다.

* **[!UICONTROL 오류 및 유효성 검사]**: 옵션을 사용하면 오류 메시지를 캡처하고 검색되고 데이터 소스로 전송되는 데이터에 대한 유효성 검사 옵션을 지정할 수 있습니다. 이러한 변경 사항으로 양식 데이터 모델 서비스 호출 로 전달된 데이터가 데이터 소스에 의해 정의된 데이터 제약 조건을 준수하는지 확인할 수 있습니다. 자세한 내용은 [입력 데이터의 자동 유효성 검사](work-with-form-data-model.md#automated-validation-of-input-data)

* **[!UICONTROL 유효성 검사 수준]**: 검증에는 다음 세 가지 범주가 있습니다. 기본, 전체 및 해제:

   * 전체: 모든 제약 조건이 검증됩니다.
   * 기본: 필수 및 null 허용 제한만
   * 해제: 유효성 검사가 수행되지 않습니다.

* **[!UICONTROL 실패 시 워크플로우 종료]**: 제약 조건이 유효성을 검사하지 못하면 워크플로우가 중지됩니다.

* **[!UICONTROL 변수에 오류 코드 저장]**: 오류 코드를 [문자열 유형 변수](variable-in-aem-workflows.md).

* **[!UICONTROL 변수에 오류 메시지 저장]**: 오류 메시지를 [문자열 유형 변수](variable-in-aem-workflows.md).

* **[!UICONTROL 변수에 오류 세부 정보 저장]**: 오류 세부 정보를 [JSON 유형 변수](variable-in-aem-workflows.md).

* **[!UICONTROL 서비스]**: 선택한 양식 데이터 모델에서 제공하는 서비스 목록입니다.
* **[!UICONTROL 서비스 입력]** > **[!UICONTROL 리터럴, 변수 또는 워크플로우 메타데이터 및 JSON 파일을 사용하여 입력 데이터를 제공합니다]**: 서비스에는 여러 개의 인수가 있을 수 있습니다. 옵션을 선택하여 워크플로우 메타데이터 속성, JSON 개체, 변수에서 서비스 인수 값을 가져오거나 제공된 텍스트 상자에 값을 직접 입력합니다.

   * **[!UICONTROL 리터럴]**: 지정할 정확한 값을 알고 있는 경우 옵션을 사용합니다. 예: srose@we.info
   * **[!UICONTROL 변수]**: 변수에 저장된 값을 검색하려면 옵션을 사용합니다.
   * **[!UICONTROL 워크플로우 메타데이터에서 검색]**: 사용할 값이 워크플로우 메타데이터 속성에 저장되면 옵션을 사용합니다. 예를 들어 emailAddress가 있습니다.

   * **[!UICONTROL 페이로드에 대한 상대]**: 페이로드를 기준으로 경로에 저장된 파일 첨부 파일을 검색하려면 옵션을 사용합니다. 옵션을 선택하고 파일 첨부 파일이 포함된 폴더 이름을 지정하거나 텍스트 상자에 파일 첨부 이름을 지정합니다.

      예를 들어 CRX 저장소의 페이로드에 상대적 위치 폴더에 `attachment\attachment-folder` 위치, 지정 `attachment\attachment-folder` 텍스트 상자에서 **[!UICONTROL 페이로드에 대한 상대]** 선택 사항입니다.

   * **[!UICONTROL JSON 점 표기법]**: 사용할 값이 JSON 파일에 있을 때 옵션을 사용합니다. 예를 들어 insurance.customerDetails.emailAddress가 있습니다. JSON 점 표기법 옵션은 입력 JSON에서 입력 필드 매핑 옵션을 선택한 경우에만 사용할 수 있습니다.
   * **[!UICONTROL 입력 JSON에서 입력 필드 매핑]**: JSON 파일에서 일부 서비스 인수의 입력 값을 가져올 JSON 파일의 경로를 지정합니다. JSON 파일의 경로는 페이로드 또는 절대 경로를 기준으로 하거나 JSON 또는 양식 데이터 모델 유형의 변수를 사용하여 입력 JSON 문서를 선택할 수 있습니다.

* **[!UICONTROL 서비스 입력]** > **[!UICONTROL 변수 또는 JSON 파일을 사용하여 입력 데이터 제공]**: 절대 경로, 페이로드를 기준으로 하는 경로 또는 변수에 저장된 JSON 파일의 모든 인수에 대한 값을 가져오려면 옵션을 선택합니다.
* **[!UICONTROL 을 사용하여 입력 JSON 문서 선택]**: 모든 서비스 인수에 대한 값이 포함된 JSON 파일입니다. JSON 파일의 경로는 다음과 같습니다 **[!UICONTROL 페이로드에 대해 상대]** 또는 **[!UICONTROL 절대 경로]**. JSON 또는 양식 데이터 모델 데이터 유형의 변수를 사용하여 입력 JSON 문서를 검색할 수도 있습니다.

* **[!UICONTROL JSON 점 표기법]**: 지정된 JSON 파일의 모든 개체를 서비스 인수에 대한 입력으로 사용하려면 필드를 비워 둡니다. 지정된 JSON 파일에서 특정 JSON 개체를 서비스 인수에 대한 입력으로 읽으려면 JSON 개체에 점 표기법을 지정합니다. 예를 들어, 섹션 시작 부분에 나열된 JSON과 유사한 JSON이 있는 경우 insurance.customerDetails를 지정하여 서비스에 대한 입력으로 고객의 모든 세부 정보를 제공합니다.
* **[!UICONTROL 서비스 출력]** > **[!UICONTROL 출력 값을 변수 또는 메타데이터에 매핑 및 쓰기]**: 출력 값을 crx-repository에 있는 워크플로우 인스턴스 메타데이터 노드의 속성으로 저장하는 옵션을 선택합니다. 메타데이터 속성의 이름을 지정하고 메타데이터 속성과 매핑할 해당 서비스 출력 속성을 선택합니다. 예를 들어 출력 서비스에서 반환한 phone_number 속성을 워크플로우 메타데이터의 phone_number 속성에 매핑합니다. 마찬가지로 출력을 긴 데이터 유형의 변수에 저장할 수 있습니다. 에 대한 속성을 선택하는 경우 **[!UICONTROL 매핑할 서비스 출력 속성]** 옵션을 선택하면 선택한 속성의 데이터를 저장할 수 있는 변수만 **[!UICONTROL 출력을]** 선택 사항입니다.

* **[!UICONTROL 서비스 출력]** > **[!UICONTROL 출력을 변수 또는 JSON 파일에 저장]**: 옵션을 선택하여 출력 값을 절대 경로, 페이로드를 기준으로 하는 경로 또는 변수에 JSON 파일에 저장합니다.
* **[!UICONTROL 아래 옵션을 사용하여 출력 JSON 문서 저장]**: 출력 JSON 파일을 저장합니다. 출력 JSON 파일의 경로는 페이로드 또는 절대 경로를 기준으로 할 수 있습니다. JSON 또는 양식 데이터 모델 데이터 유형의 변수를 사용하여 출력 JSON 파일을 저장할 수도 있습니다.

## 문서 서명 단계 {#sign-document-step}

문서 서명 단계를 통해 [!DNL Adobe Sign] 문서에 서명합니다. [!DNL Adobe Sign] 워크플로 단계를 사용해 적응형 양식에 서명할 때, 워크플로 단계의 구성에 따라 양식이 서명자들 간에 전달되거나 모든 서명자에게 동시에 전달될 수 있습니다. [!DNL Adobe Sign]이 활성화된 적응형 양식은 모든 서명자가 서명 프로세스를 완료한 후에만 Experience Manager Forms Server에 제출됩니다.

기본값으로 [!DNL Adobe Sign] 스케줄러 서비스는 서명자 응답을 24시간마다 점검(가져옴)합니다. 다음을 수행할 수 있습니다 [환경의 기본 간격 변경](adobe-sign-integration-adaptive-forms.md##configure-adobe-sign-scheduler-to-sync-the-signing-status).

문서 서명 단계에는 다음 속성이 있습니다.

* **[!UICONTROL 계약 이름]**: 계약의 제목을 지정합니다. 계약 이름은 서명자에게 보내는 전자 메일의 제목 및 본문 텍스트의 일부가 됩니다. 문자열 데이터 유형의 변수에 이름을 저장하거나 **[!UICONTROL 리터럴]** 수동으로 이름을 추가합니다.

* **[!UICONTROL 로케일]**: 전자 메일 및 확인 옵션에 대한 언어를 지정합니다. 문자열 데이터 유형의 변수에 로케일을 저장하거나 **[!UICONTROL 리터럴]** 사용 가능한 옵션 목록에서 로케일을 선택합니다. 로케일 값을 변수에 저장하는 동안 로케일 코드를 정의해야 합니다. 예를 들어 **[!UICONTROL en_US]** - 영어 및 **[!UICONTROL fr_FR]** 프랑스어로

* **[!UICONTROL Adobe Sign Cloud 구성]**: 선택 [!DNL Adobe Sign] 클라우드 구성. 구성되지 않은 경우 [!DNL Adobe Sign] 대상 [!DNL AEM Forms]를 참조하십시오. [Adobe Sign과 통합 [!DNL AEM Forms]](adobe-sign-integration-adaptive-forms.md).

* **[!UICONTROL 을 사용하여 서명할 문서 선택]**: 페이로드를 기준으로 한 위치에서 문서를 선택하거나, 페이로드를 문서로 사용하거나, 문서의 절대 경로를 지정하거나, 문서 데이터 유형의 변수에 저장된 문서를 검색할 수 있습니다.
* **[!UICONTROL 마감일까지 일수]**: 작업에서 지정한 일 수 동안 작업이 없으면 문서가 기한(전달된 기간)으로 표시됩니다. **[!UICONTROL 마감일까지 일수]** 필드. 문서화된 항목이 서명을 위해 사용자에게 지정된 후 일 수가 계산됩니다.
* **[!UICONTROL 미리 알림 전자 메일 빈도]**: 매일 또는 주별 간격으로 미리 알림 이메일을 보낼 수 있습니다. 이 주는 서명을 위해 사용자에게 문서화된 항목이 지정된 날짜부터 계산됩니다.
* **[!UICONTROL 서명 프로세스]**: 순차 또는 병렬 순서로 문서에 서명하도록 선택할 수 있습니다. 순차적으로, 한 서명자가 서명할 때 문서를 수신합니다. 첫 번째 서명자가 문서 서명을 완료하면 문서가 두 번째 서명자에게 보내지는 등의 작업을 수행합니다. 동시에 여러 서명자가 한 번에 문서에 서명할 수 있습니다.
* **[!UICONTROL 리디렉션 URL]**: 리디렉션 URL을 지정합니다. 문서가 서명되면 할당자를 URL로 리디렉션할 수 있습니다. 일반적으로 이 URL에는 감사 메시지나 추가 지침이 포함되어 있습니다.
* **[!UICONTROL 워크플로우 단계]**: 워크플로우에는 여러 단계가 있을 수 있습니다. 이러한 단계는 AEM 받은 편지함에 표시됩니다. 모델의 속성에서 이러한 단계를 정의할 수 있습니다( **[!UICONTROL 사이드킥입니다]** > **[!UICONTROL 페이지]** > **[!UICONTROL 페이지 속성]** > **[!UICONTROL 단계]**).
* **[!UICONTROL 서명자 선택]**: 문서의 서명자를 선택하는 방법을 지정합니다. 워크플로우를 사용자나 그룹에 동적으로 할당하거나 서명자의 세부 사항을 수동으로 추가할 수 있습니다.
* **[!UICONTROL 서명자를 선택하는 스크립트 또는 서비스]**: 이 옵션은 서명자 선택 필드에서 동적으로 옵션을 선택한 경우에만 사용할 수 있습니다. ECMAScript 또는 서비스를 지정하여 문서에 대한 서명자 및 확인 옵션을 선택할 수 있습니다.
* **[!UICONTROL 서명자 세부 정보]**: 서명자 선택 필드에서 수동 옵션을 선택한 경우에만 옵션을 사용할 수 있습니다. 이메일 주소를 지정하고 선택적 확인 메커니즘을 선택합니다. 2단계 확인 메커니즘을 선택하기 전에 구성된 [!DNL Adobe Sign] 계정이 필요합니다. 문자열 데이터 유형의 변수를 사용하여 이메일, 국가 코드 및 전화 번호 필드에 대한 값을 정의할 수 있습니다. 국가 코드 및 전화 번호 필드는 2단계 확인 드롭다운 목록에서 전화 확인을 선택한 경우에만 표시됩니다.

<!-- 

## Document Services steps {#document-services-steps}

AEM Document services are a set of services for creating, assembling, and securing PDF Documents. [!DNL AEM Forms] provides a separate AEM Workflow step for each document service.

Similar to other [!DNL AEM Forms] workflow steps, such as Assign Task, Send Email, and Sign Document, you can use variables in all AEM Document services steps. For more information on creating and managing variables, see [Variables in AEM workflows](variable-in-aem-workflows.md).

### Apply Document Time Stamp step {#apply-document-time-stamp-step}

Add time stamp to a document. You provide document details such as input document path, input document name, location to store exported data. You may choose to overwrite existing payload file, choose a different file name to store data in a different file under payload folder, provide an absolute path to the data, or store data in a variable of Document data type.

### Convert to image step {#convert-to-image-step}

Converts a PDF document to list of images. Supported image formats are JPEG, JPEG2000, PNG, and TIFF. The following information applies to conversions to TIFF images:

* A multi-page TIFF file is generated.
* Some annotations are not included in TIFF images. Annotations that require Acrobat to generate their appearance are not included.

### Convert to PDF/A step {#convert-to-pdf-a-step}

Converts a PDF document to PDF/A format using the options provided. The PDF/A version of Portable Document Format (PDF) is specialized for archiving and long-term preservation of documents.

### Convert to PS step {#convert-to-ps-step}

Convert PDF documents to PostScript. When converting to PostScript, you can use the conversion operation to specify the source document and whether to convert to PostScript level 2 or 3. The PDF document you convert to a PostScript file must be non-interactive.

### Create PDF from specified type step {#create-pdf-from-specified-type-step}

Generate a PDF document from an input file. The input document can be relative to the payload, have an absolute path, can be payload itself, or stored in a variable of Document data type.

### Create PDF from URL/HTML/ZIP step {#create-pdf-from-url-html-zip-step}

Generates a PDF document from supplied URL, HTML, and ZIP file.

### Export Data step {#export-data-step}

Exports data from a PDF forms or XDP file. It requires you to enter the file path of Input Document and the Export Data Format. The options for Export Data Format are Auto, XDP and XmlData.

### Export PDF to specified type step {#export-pdf-to-specified-type-step}

Converts a PDF document to a selected format.

### Generate Non-Interactive PDF step {#generatenoninteractive}

Generate a Non-Interactive PDF. It provides various customization options.

>[!NOTE]
>
>You can use variables to specify the template file for input documents. Store the path of the template file in a variable of String data type.

### Import Data step {#import-data-step}

Merges form data into a PDF form. You can import form data into a PDF form.

### Invoke DDX step {#invokeddx}

Executes the DDX file on the specified map of input documents and returns the manipulated PDF documents.

>[!NOTE]
>
>You can use variables to specify the DDX file for input documents. Store the DDX file in a variable of Document or XML data type.

### Optimize PDF step {#optimize-pdf-step}

Optimizes PDF files by reducing their size. The result of this conversion is PDF files that may be smaller than their original versions. This operation also converts PDF documents to the PDF version specified in the optimization parameters.

Optimization settings specify how files are optimized. Here are example settings:

* Target PDF version
* Discarding objects such as JavaScript actions and embedded page thumbnails
* Discarding user data such as comments and file attachments
* Discarding invalid or unused settings
* Compressing uncompressed data or using more efficient compression algorithms
* Removing embedded fonts
* Setting transparency values

### Render PDF Form step {#renderpdf}

Renders a form created in Form Designer (XDP) to a PDF form.

>[!NOTE]
>
>You can use variables to specify the template file for input documents. Store the path of the template file in a variable of String data type.

### Secure Document step {#secure-document-step}

Encrypt, Sign, and certify a document. [!DNL AEM Forms] supports both password based and certificate base encryption. You can also choose between various algorithms for signing documents. For example, SHA-256 and SH-512. You can also use the workflow step to reader extend PDF documents. The workflow step provides option to enable barcode decoding, digital signatures, import and export of PDF data, and other options.

### Send to Printer step {#send-to-printer-step}

Send a document directly to a printer. It supports the following printing access mechanisms:

* **[!UICONTROL Direct accessible printer]**: A printer that is installed on the same computer is called a direct accessible printer, and the computer is named printer host. This type of printer can be a local printer that is connected to the computer directly.
* **[!UICONTROL Indirect accessible printer]**: The printer that is installed on a print server is accessed from other computers. Technologies such as the common UNIX® printing system (CUPS) and the Line Printer Daemon (LPD) protocol are available to connect to a network printer. To access an indirect accessible printer, specify the print server’s IP or host name. Using this mechanism, you can send a document to an LPD URI when the network has an LPD running. The mechanism lets you route the document to any printer that is connected to the network that has an LPD running.

### Generate Printed Output Step {#generatePrintedOutput}

The step generates a PCL, PostScript, ZPL, IPL, TPCL, or DPL output given a form design and data file. The data file is merged with the form design and formatted for printing. The output generated by this step can be sent directly to a printer or saved as file. It is recommended that you use this step when you want to use form designs or data from an application. If your form designs or form designs are located on the network, local file system, or HTTP location, use the generatePrintedOutput operation operation.

For example, your application requires that you merge a form design with a data file. The data contains hundreds of records. In addition, it requires the output is sent to a printer that supports ZPL. The form design and your input data are located in an application. Use the generatePrintedOutput operation to merge each record with a form design and send the output to a printer that supports ZPL.

The Generate Printed Output step has the following properties:

**[!UICONTROL Input properties]**

* **[!UICONTROL Select template file using]**: Specify the path of the template file. You can select the template file using the path that is relative to the payload, saved at an absolute path, or using a variable of Document data type. For example, [Payload_Directory]/Workflow/data.xml. If the path does not exist in crx-repository, an administrator can create the path before using it. Moreover, you can also accept payload as the input data file.

* **[!UICONTROL Select data document using]**: Specify the path of a input data file. You can select the input data file using the path that is relative to the payload, saved at an absolute path, or using a variable of Document data type. For example, [Payload_Directory]/Workflow/data.xml. If the path does not exist in crx-repository, an administrator can create the path before using it.

* **[!UICONTROL Printer Format]**: A Print Format value that specifies the page description language to use, when an XDC file is not provided, to generate the output stream. If you provide a literal value, select one of these values:

  * **[!UICONTROL Custom PCL]**: Use the option to specify a custom XDC file for PCL.
  * **[!UICONTROL Custom PostScript]**: Use the option to specify a custom XDC file for PostScript.
  * **[!UICONTROL Custom ZPL]**: Use the option to specify a custom XDC file file for ZPL.
  * **[!UICONTROL Generic Color PCL (5c)]**: Use a generic color PCL (5c).
  * **[!UICONTROL Generic PostScript Level3]**: Use generic PostScript Level 3.
  * **[!UICONTROL ZPL 300 DPI]**: Use ZPL 300 DPI. The zpl300.xdc is used.
  * **[!UICONTROL ZPL 600 DPI]**: Use ZPL 600 DPI. The zpl600.xdc file is used.
  * **[!UICONTROL Custom IPL]**: Use the option to specify a custom XDC file for IPL.
  * **[!UICONTROL IPL 300 DPI]**: Use IPL 300 DPI. The ipl300.xdc is used.
  * **[!UICONTROL IPL 400 DPI]**: Use IPL 400 DPI. The ipl400.xdc file is used.
  * **[!UICONTROL Custom TPCL]**: Use the option to specify a custom XDC file for TPCL.
  * **[!UICONTROL TPCL 305 DPI]**: Use TPCL 300 DPI. The tpcl305.xdc file is used.
  * **[!UICONTROL PCL 600 DPI]**: Use TPCL 600 DPI. The tpcl600.xdc file is used.
  * **[!UICONTROL Custom DPL]**: Use the option to specify a custom XDC file DPL.
  * **[!UICONTROL DPL300DPI]**: Use DPL 300 DPI. The dpl300.xdc file is used.
  * **[!UICONTROL DPL406DPI]**: Use DPL 400 DPI. The dpl406.xdc is used.
  * **[!UICONTROL DPL600DPI]**: Use DPL 600 DPI. The dpl600.xdc is used.

**[!UICONTROL Output Properties]**

* **[!UICONTROL Save output document using]**: Specify the location to save the output file. You can save the output file at an location  which is relative to the payload, in a variable, or specify an absolute location to save the output file. If the path does not exist in crx-repository, an administrator can create the path before using it.

**[!UICONTROL Advanced Properties]**

* **[!UICONTROL Select Content Root location using]**: Content root is a string value that specifies the URI, absolute reference, or location in the repository to retrieve relative assets used by the form design. For example, if the form design references an image relatively, such as ../myImage.gif, myImage.gif must be located at repository://. The default value is repository://, which points to the root level of the repository.

  When you pick an asset from your application, the Content Root URI path must have the correct structure. For example, if a form is picked from an application named SampleApp, and is placed at SampleApp/1.0/forms/Test.xdp, the Content Root URI must be specified as repository://administrator@password/Applications/SampleApp/1.0/forms/, or repository:/Applications/SampleApp/1.0/forms/ (when authority is null). When the Content Root URI is specified this way, the paths of all of the referenced assets in the form will be resolved against this URI.

* **[!UICONTROL Select XCI file using]**: XCI files are used to describe fonts and other properties that are used for form design elements. You can keep an XCI file relative to the payload, at an absolute path, or using a variable of Document data type.

* **[!UICONTROL Locale]**: Specifies the language used for generating the PDF document. If you provide a literal value, select a language from the list or select one of these values:
  * **[!UICONTROL To use server default]**:
    (Default) Use the Locale setting configured on the [!DNL AEM Forms] Server. The Locale setting is configured using Administration Console. (See [Designer Help](http://www.adobe.com/go/learn_aemforms_designer_65).)

  * **[!UICONTROL To use custom value]**:
    Type the Locale code in the literal box or select a string variable containing the locale code. For a complete list of supported locale codes, see http://java.sun.com/j2se/1.5.0/docs/guide/intl/locale.doc.html.

* **[!UICONTROL Copies]**: An integer value that specifies the number of copies to generate for the output. The default value is 1.

* **[!UICONTROL Duplex Printing]**:  A Pagination value that specifies whether to use two-sided or single-sided printing. Printers that support PostScript and PCL use this value.If you provide a literal value, select one of these values:
    * **[!UICONTROL Duplex Long Edge]**: Use two-sided printing and print using long-edge pagination. 
    * **[!UICONTROL Duplex Short Edge]**: Use two-sided printing and print using short-edge pagination. 
    * **[!UICONTROL Simplex]**: Use single-sided printing.
    
    -->
