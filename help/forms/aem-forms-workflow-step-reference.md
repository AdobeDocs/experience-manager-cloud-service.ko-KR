---
title: AEM Forms Cloud Service에서 워크플로우를 만드는 데 사용할 수 있는 워크플로우 단계 또는 BPM(비즈니스 프로세스 자동화)에 사용할 수 있는 워크플로우 단계는 무엇입니까?
description: Forms 중심 워크플로를 사용하면 적응형 Forms 기반 워크플로를 신속하게 구축할 수 있습니다. Adobe Sign을 사용하여 문서에 전자 서명하고, 양식 기반 비즈니스 프로세스를 만들고, 데이터를 검색하여 여러 데이터 소스로 전송하고, 이메일 알림을 전송할 수 있습니다
exl-id: e1403ba6-8158-4961-98a4-2954b2e32e0d
google-site-verification: A1dSvxshSAiaZvk0yHu7-S3hJBb1THj0CZ2Uh8N_ck4
keywords: AEM 워크플로 사용, 작업 단계 할당, PDF/A 단계로 전환, 기록된 문서 생성 단계, 워크플로 사용, 문서 서명 단계, 인쇄된 출력 생성 단계, 비대화형 PDF 출력 생성
feature: Adaptive Forms, Workflow
role: Admin, User
source-git-commit: f772a193cce35a1054f5c6671557a6ec511671a9
workflow-type: tm+mt
source-wordcount: '7409'
ht-degree: 0%

---


# Forms 중심 AEM 워크플로 사용 - 비즈니스 프로세스 자동화를 위한 단계 참조 {#forms-centric-workflow-on-osgi-step-reference}

| 버전 | 문서 링크 |
| -------- | ---------------------------- |
| AEM 6.5 | [여기 클릭](https://experienceleague.adobe.com/docs/experience-manager-65/forms/workflows/aem-forms-workflow-step-reference.html?lang=ko) |
| AEM as a Cloud Service | 이 문서 |

워크플로우 모델 을 사용합니다. 모델은 일련의 단계를 정의하고 실행하는 데 도움이 됩니다. 워크플로가 일시적인지 또는 여러 리소스를 사용하는지 여부와 같은 모델 속성을 정의할 수도 있습니다. 비즈니스 논리를 달성하기 위해 [모델에 다양한 AEM 워크플로 단계를 포함할 수 있습니다](https://experienceleague.adobe.com/docs/experience-manager-65/developing/extending-aem/extending-workflows/workflows-models.html?lang=ko#extending-aem).

## Forms 중심 단계 {#forms-workflow-steps}

Forms 중심 워크플로우 단계는 AEM 워크플로우에서 AEM Forms 관련 작업을 수행합니다. 이러한 단계를 통해 OSGi에서 적응형 Forms 기반 Forms 중심 워크플로우를 신속하게 구축할 수 있습니다. 이러한 워크플로우는 기본 검토 및 승인 워크플로, 내부 및 방화벽 간 비즈니스 프로세스를 개발하는 데 사용할 수 있습니다. Forms Workflow 단계를 사용하여 다음을 수행할 수도 있습니다.

* 비즈니스 프로세스, 사후 제출 워크플로우 및 백엔드 워크플로우를 만들어 등록 프로세스를 관리합니다.

* 작업을 만들고 사용자 또는 그룹에 할당합니다.

* AEM 워크플로에서 [!DNL Adobe Sign]을(를) 사용하여 서명용 문서를 보냅니다.

* 요청 시 또는 양식 제출 시 기록 문서를 생성합니다.

* 워크플로우 모델을 다양한 데이터 소스와 연결하여 데이터를 쉽게 저장하고 검색할 수 있습니다.

* 이메일 단계를 사용하여 작업 완료 및 워크플로우 시작 또는 완료 시 알림 이메일 및 기타 첨부 파일을 전송합니다.

>[!NOTE]
>
>워크플로 모델이 외부 스토리지로 표시된 경우 모든 Forms Workflow 단계에 대해 변수 옵션만 선택하여 데이터 파일 및 첨부 파일을 저장하거나 검색할 수 있습니다.

## 작업 단계 할당 {#assign-task-step}

작업 할당 단계에서는 작업 항목을 만들어 사용자 또는 그룹에 할당합니다. 작업 할당과 함께 구성 요소는 작업에 대한 적응형 양식 또는 비대화형 PDF도 지정합니다. 적응형 양식은 사용자와 비대화형 PDF의 입력을 수락하는 데 필요하거나, 읽기 전용 적응형 양식이 검토 전용 워크플로우에 사용됩니다.

구성 요소를 사용하여 작업의 동작을 제어할 수도 있습니다. 예를 들어 자동 기록 문서 생성, 특정 사용자 또는 그룹에 작업 할당, 제출된 데이터의 경로 지정, 미리 채울 데이터 경로 지정 및 기본 작업 지정이 있습니다. 작업 할당 단계에는 다음과 같은 속성이 있습니다.

* **[!UICONTROL 제목]**: 작업의 제목입니다. 제목은 AEM 받은 편지함에 표시됩니다.
* **[!UICONTROL 설명]**: 작업에서 수행 중인 작업에 대한 설명입니다. 이 정보는 공유 개발 환경에서 작업할 때 다른 프로세스 개발자에게 유용합니다.

* **[!UICONTROL 썸네일 경로]**: 작업 썸네일의 경로입니다. 경로를 지정하지 않으면 적응형 양식에 대해 기본 썸네일이 표시되고 기록 문서에 대해 기본 아이콘이 표시됩니다.
* **[!UICONTROL 워크플로 단계]**: 워크플로에는 여러 단계가 있을 수 있습니다. 이러한 단계는 AEM 받은 편지함에 표시됩니다. 모델의 속성(Sidekick > 페이지 > 페이지 속성 > 단계)에서 이러한 단계를 정의할 수 있습니다.
* **[!UICONTROL 우선 순위]**: 선택한 우선 순위가 AEM 받은 편지함에 표시됩니다. 사용 가능한 옵션은 높음, Medium 및 낮음입니다. 기본값은 Medium입니다.
* **[!UICONTROL 기한]**: 작업이 기한 초과로 표시된 후 경과된 일 또는 시간을 지정합니다. **[!UICONTROL 해제]**&#x200B;를 선택하면 작업이 기한 초과로 표시되지 않습니다. 작업 기한이 지난 후 특정 작업을 수행할 시간 초과 핸들러를 지정할 수도 있습니다.

* **[!UICONTROL 일]**: 작업을 완료할 때까지 남은 일 수입니다. 작업이 사용자에게 할당된 후 일수는 계산됩니다. 작업이 완료되지 않고 일 필드에 지정된 일 수를 넘으면 기한 후 시간 초과 핸들러가 트리거됩니다.
* **[!UICONTROL 시간]**: 작업을 완료하는 데 걸리는 시간입니다. 작업은 사용자에게 할당된 후 시간이 계산됩니다. 작업이 완료되지 않고 시간 필드에 지정된 시간 수를 넘으면 제한 시간 후 시간 초과 핸들러가 트리거됩니다.
* **[!UICONTROL 기한이 지난 후 시간 초과]**: 시간 제한 처리기 선택 필드를 사용하려면 이 옵션을 선택하십시오.
* **[!UICONTROL 시간 제한 처리기]**: 할당 작업 단계가 기한을 넘길 때 실행할 스크립트를 선택합니다. [apps]/fd/dashboard/scripts/timeoutHandler의 CRX 저장소에 배치된 스크립트를 선택할 수 있습니다. 지정된 경로가 crx-repository에 없습니다. 관리자는 경로를 사용하기 전에 경로를 만듭니다.
* **[!UICONTROL 작업 세부 정보에서 마지막 작업의 동작 및 댓글을 강조 표시합니다]**: 작업의 작업 세부 정보 섹션에 마지막으로 수행한 동작 및 받은 댓글을 표시하려면 이 옵션을 선택하십시오.
* **[!UICONTROL 유형]**: 워크플로를 시작할 때 채울 문서 유형을 선택합니다. 적응형 양식, 읽기 전용 적응형 양식 또는 비대화형 PDF 문서를 선택할 수 있습니다.

<!-- , Interactive Communication Agent UI, or Interactive Communication Web Channel Document. -->


* **[!UICONTROL 적응형 양식 사용]**: 입력 적응형 양식을 찾을 방법을 지정하십시오. 이 옵션은 유형 드롭다운 목록에서 적응형 양식 또는 읽기 전용 적응형 양식을 선택하는 경우 사용할 수 있습니다. 워크플로우에 제출된 적응형 양식을 사용하거나, 절대 경로에서 사용하거나, 변수의 경로에서 사용할 수 있습니다. String 유형의 변수를 사용하여 경로를 지정할 수 있습니다.\
  여러 적응형 Forms을 워크플로우와 연결할 수 있습니다. 따라서 사용 가능한 입력 방법을 사용하여 런타임에 적응형 양식을 지정할 수 있습니다.

<!-- 

* **[!UICONTROL Use Interactive Communication]**: Specify the method to locate the input interactive communication. You can use the interactive communication submitted to the workflow, available at an absolute path, or available at a path in a variable. You can use a variable of type String to specify the path. This option is available if you select Interactive Communication Agent UI or Interactive Communication Web Channel Document from the Type drop-down list. 

> [!NOTE]
>
>You must have cm-agent-users and workflow-users group assignments to access Interactive Communications Agent UI in AEM inbox.  

-->

* **[!UICONTROL 적응형 양식 경로]**: 적응형 양식의 경로를 지정하십시오. 워크플로우에 제출된 적응형 양식을 사용하여 절대 경로에서 사용할 수 있으며 문자열 데이터 유형의 변수에 저장된 경로에서 적응형 양식을 검색할 수 있습니다.
* **[!UICONTROL 다음을 사용하여 입력 PDF 선택]**: 비대화형 PDF 문서의 경로를 지정하십시오. 유형 필드에서 비대화형 PDF 문서를 선택하면 이 필드를 사용할 수 있습니다. 페이로드에 상대적인 경로, 절대 경로에 저장된 경로 또는 문서 데이터 유형의 변수를 사용하여 입력 PDF을 선택할 수 있습니다. 예: [Payload_Directory]/Workflow/PDF/credit-card.pdf. 경로가 crx-repository에 없습니다. 관리자는 경로를 사용하기 전에 경로를 만듭니다. PDF 경로 옵션을 사용하려면 기록 문서 옵션 활성화 또는 양식 템플릿 기반 적응형 Forms이 필요합니다.
* **[!UICONTROL 완료된 작업의 경우 적응형 양식을 다음과 같이 렌더링]**: 작업이 완료된 것으로 표시되면 적응형 양식을 읽기 전용 적응형 양식 또는 PDF 문서로 렌더링할 수 있습니다. 적응형 양식을 기록 문서로 렌더링하려면 기록 문서 옵션 활성화 또는 양식 템플릿 기반 적응형 Forms이 필요합니다.
* **[!UICONTROL 미리 채워짐]**: 아래에 나열된 다음 필드는 작업에 대한 입력으로 사용됩니다.

   * **[!UICONTROL 다음을 사용하여 입력 데이터 파일 선택]**: 입력 데이터 파일 경로(.json, .xml, .doc 또는 양식 데이터 모델(FDM)). 페이로드에 상대적인 경로를 사용하여 입력 데이터 파일을 검색하거나 문서, XML 또는 JSON 데이터 유형의 변수에 저장된 파일을 검색할 수 있습니다. 예를 들어 파일에는 AEM 받은 편지함 애플리케이션을 통해 양식에 대해 제출된 데이터가 포함되어 있습니다. 예제 경로는 [Payload_Directory]/workflow/data입니다.
   * **[!UICONTROL 다음을 사용하여 입력 첨부 파일 선택]**: 해당 위치에서 사용할 수 있는 첨부 파일이 작업과 연결된 양식에 첨부됩니다. 경로는 페이로드에 상대적이거나 문서의 변수에 저장된 첨부 파일을 검색할 수 있습니다. 예제 경로는 [Payload_Directory]/attachments/입니다. 페이로드를 기준으로 배치되는 첨부 파일을 지정하거나 문서 유형(배열 목록 > 문서) 변수를 사용하여 적응형 양식에 대한 입력 첨부 파일을 지정할 수 있습니다.

  <!-- 
    
    * **[!UICONTROL Choose input JSON]**: Select an input JSON file using a path that is relative to payload or stored in a variable of Document, JSON, or Form Data Model (FDM) data type. This option is available if you select Interactive Communication Agent UI or Interactive Communication Web Channel Document from the Type drop-down list.

    * **[!UICONTROL Choose a custom prefill service]**: Select the prefill service to retrieve the data and prefill the Interactive Communication Web channel document or the Agent UI.  
    
    * **[!UICONTROL Use the prefill service of the interactive communication selected above]**: Use this option to use the prefill service of the Interactive Communication defined in the Use Interactive Communication drop-down list. 
    
    -->

   * **[!UICONTROL 요청 특성 매핑]**: 요청 특성 매핑 섹션을 사용하여 [요청 특성의 이름 및 값](work-with-form-data-model.md#bindargument)을(를) 정의합니다. 요청에 지정된 속성 이름 및 값을 기반으로 데이터 소스에서 세부 정보를 검색합니다. String 데이터 형식의 변수 또는 리터럴 값을 사용하여 요청 속성 값을 정의할 수 있습니다.

  <!--  
     
     The prefill service and request attribute mapping options are available only if you select Interactive Communication Agent UI or Interactive Communication Web Channel Document from the Type drop-down list. 
     
     -->

* **[!UICONTROL 제출된 정보]**: 아래에 나열된 다음 필드는 작업의 출력 위치로 사용됩니다.

   * **[!UICONTROL 다음을 사용하여 출력 데이터 파일 저장]**: 데이터 파일(.json, .xml, .doc 또는 양식 데이터 모델(FDM))을 저장합니다. 데이터 파일에는 관련 양식을 통해 제출된 정보가 포함되어 있습니다. 페이로드와 관련된 경로를 사용하여 출력 데이터 파일을 저장하거나 문서, XML 또는 JSON 데이터 유형의 변수에 저장할 수 있습니다. 예: [Payload_Directory]/Workflow/data, 여기서 데이터는 파일입니다.
   * **[!UICONTROL 다음을 사용하여 첨부 파일 저장]**: 작업에 제공된 양식 첨부 파일을 저장합니다. 페이로드에 상대적인 경로를 사용하여 첨부 파일을 저장하거나 문서 데이터 유형의 배열 목록에 저장할 수 있습니다.
   * **[!UICONTROL 다음을 사용하여 기록 문서 저장]**: 기록 문서 파일을 저장할 경로입니다. 예: [Payload_Directory]/DocumentofRecord/credit-card.pdf. 페이로드에 상대적인 경로를 사용하여 기록 문서를 저장하거나 문서 데이터 유형의 변수에 저장할 수 있습니다. **[!UICONTROL 페이로드에 비례]** 옵션을 선택하면 경로 필드를 비워 두면 기록 문서가 생성되지 않습니다. 이 옵션은 유형 드롭다운 목록에서 적응형 양식을 선택하는 경우에만 사용할 수 있습니다.

  <!-- 
    
    * **[!UICONTROL Save Web Channel data using]**: Save the Web Channel data file using a path that is relative to the payload or store it in a variable of Document, JSON, or Form Data Model (FDM) data type. This option is available only if you select Interactive Communication Agent UI from the Type drop-down list. c
    * **[!UICONTROL Save PDF document using]**: Save the PDF document using a path that is relative to the payload or store it in a variable of Document data type. This option is available only if you select Interactive Communication Agent UI from the Type drop-down list.
    <!-- * **[!UICONTROL Save layout template using]**: Save the layout template using a path that is relative to the payload or store it in a variable of Document data type. The [layout template](layout-design-details.md) refers to an XDP file that you create using Forms Designer. This option is available only if you select Interactive Communication Agent UI from the Type drop-down list. 
    
    -->

* **[!UICONTROL 피할당자]** > **[!UICONTROL 옵션 할당]**: 사용자에게 작업을 할당할 메서드를 지정합니다. 참가자 선택기 스크립트를 사용하여 작업을 사용자 또는 그룹에 동적으로 할당하거나 작업을 특정 AEM 사용자 또는 그룹에 할당할 수 있습니다.
* **[!UICONTROL 참가자 선택기]**: 옵션 할당 필드에서 **[!UICONTROL 사용자 또는 그룹에 동적으로]** 옵션을 선택하면 이 옵션을 사용할 수 있습니다. ECMAScript 또는 서비스를 사용하여 사용자 또는 그룹을 동적으로 선택할 수 있습니다. 자세한 내용은 [사용자 지정 Adobe Experience Manager 동적 참가자 만들기 단계](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-wknd-tutorial-develop/overview.html?lang=ko&CID=RedirectAEMCommunityKautuk)를 참조하십시오.

* **[!UICONTROL 참가자]**: **[!UICONTROL 참가자 선택기]** 필드에서 **[!UICONTROL com.adobe.granite.workflow.core.process.RandomParticipantChooser]** 옵션을 선택하면 이 필드를 사용할 수 있습니다. 필드에서는 RandomParticipantChooser 옵션의 사용자 또는 그룹을 선택할 수 있습니다.

* **[!UICONTROL 피할당자]**: **[!UICONTROL 참가자 선택기]** 필드에서 **[!UICONTROL com.adobe.fd.workspace.step.service.VariableParticipantChooser]**&#x200B;을(를) 선택하면 이 필드를 사용할 수 있습니다. 필드에서는 문자열 데이터 유형의 변수를 선택하여 할당자를 정의할 수 있습니다.

* **[!UICONTROL 인수]**: 참가자 선택기 필드에서 RandomParticipantChoose 스크립트 이외의 스크립트를 선택하면 이 필드를 사용할 수 있습니다. 이 필드에서는 참가자 선택기 필드에서 선택한 스크립트에 대해 쉼표로 구분된 인수 목록을 제공할 수 있습니다.

* **[!UICONTROL 사용자 또는 그룹]**: 작업이 선택한 사용자 또는 그룹에 할당되었습니다. **[!UICONTROL 옵션 할당]** 필드에서 **[!UICONTROL 특정 사용자 또는 그룹에 추가 옵션]**&#x200B;을 선택하면 이 옵션을 사용할 수 있습니다. 필드에는 [!DNL workflow-users] 그룹의 모든 사용자와 그룹이 나열됩니다.\
  **[!UICONTROL 사용자 또는 그룹]** 드롭다운 메뉴에는 로그인한 사용자가 액세스할 수 있는 사용자 및 그룹이 나열됩니다. 사용자 이름 표시는 특정 사용자에 대한 crx-repository의 **[!UICONTROL users]** 노드에 대한 액세스 권한이 있는지 여부에 따라 다릅니다.

* **[!UICONTROL 알림 전자 메일 보내기]**: 피할당자에게 전자 메일 알림을 보내려면 이 옵션을 선택하십시오. 이러한 알림은 작업이 사용자 또는 그룹에 할당되면 전송됩니다. **[!UICONTROL 받는 사람 전자 메일 주소]** 옵션을 사용하여 전자 메일 주소를 검색하는 메커니즘을 지정할 수 있습니다.

* **[!UICONTROL 받는 사람 전자 메일 주소]**: 전자 메일 주소를 변수에 저장하거나, 리터럴을 사용하여 영구 전자 메일 주소를 지정하거나, 피할당자의 프로필에 지정된 피할당자의 기본 전자 메일 주소를 사용할 수 있습니다. 리터럴 또는 변수를 사용하여 그룹의 이메일 주소를 지정할 수 있습니다. 변수 옵션은 이메일 주소를 동적으로 검색하고 사용하는 데 유용합니다. **[!UICONTROL 피할당자의 기본 전자 메일 주소 사용]** 옵션은 단일 피할당자에게만 적용됩니다. 이 경우 피할당자 사용자 프로필에 저장된 이메일 주소가 사용됩니다.

* **[!UICONTROL HTML 전자 메일 서식 파일]**: 알림 전자 메일에 대한 전자 메일 서식 파일을 선택하십시오. 템플릿을 편집하려면 crx-repository의 /libs/fd/dashboard/templates/email/htmlEmailTemplate.txt에 있는 파일을 수정합니다.
* **[!UICONTROL 다음으로 위임 허용]**: AEM 받은 편지함에서는 로그인한 사용자에게 할당된 워크플로를 다른 사용자에게 위임할 수 있는 옵션을 제공합니다. 동일한 그룹 내에서 또는 다른 그룹의 워크플로 사용자에게 위임할 수 있습니다. 작업이 단일 사용자에게 할당되고 **[!UICONTROL 피할당자 그룹의 구성원에게 위임 허용]** 옵션이 선택된 경우 다른 사용자 또는 그룹에 작업을 위임할 수 없습니다.
* **[!UICONTROL 설정 공유]**: AEM 받은 편지함에서는 받은 편지함의 단일 작업 또는 모든 작업을 다른 사용자와 공유할 수 있는 옵션을 제공합니다.
   * **[!UICONTROL 피할당자가 받은 편지함에서 명시적으로 공유하도록 허용]** 옵션을 선택하면 사용자는 AEM 받은 편지함에서 작업을 선택하여 다른 AEM 사용자와 공유할 수 있습니다.
   * **[!UICONTROL 피할당자가 받은 편지함 공유를 통해 공유하도록 허용]** 옵션을 선택하고 사용자가 받은 편지함 항목을 공유하거나 다른 사용자가 받은 편지함 항목에 액세스할 수 있도록 허용하면 이전에 언급된 옵션이 활성화된 작업만 다른 사용자와 공유됩니다.
   * **[!UICONTROL 피할당자가 &#39;부재 중&#39; 설정을 사용하여 위임하도록 허용]**&#x200B;을 선택한 경우. 피할당자는 다른 부재 중 옵션과 함께 다른 사용자에게 작업을 위임하는 옵션을 활성화할 수 있습니다. 부재 중 사용자에게 할당된 새 작업은 부재 중 설정에 언급된 사용자에게 자동으로 위임(할당)됩니다.

  이 옵션을 통해 다른 사용자는 부재 중이고 할당된 작업을 수행할 수 없는 동안 할당자 작업을 선택할 수 있습니다.

* **[!UICONTROL 작업]** > **[!UICONTROL 기본 작업]**: 기본적으로 제출, 저장 및 재설정 작업을 사용할 수 있습니다. 모든 기본 작업은 기본적으로 활성화되어 있습니다.
* **[!UICONTROL 경로 변수]**: 경로 변수의 이름입니다. 경로 변수는 사용자가 AEM 받은 편지함에서 선택한 사용자 지정 작업을 캡처합니다.
* **[!UICONTROL 경로]**: 작업이 다른 경로로 분기될 수 있습니다. AEM 받은 편지함에서 이 경로를 선택하면 해당 경로가 값을 반환하고, 선택한 경로를 기반으로 워크플로우가 분기됩니다. String 데이터 형식 배열의 변수에 경로를 저장하거나 **[!UICONTROL Literal]**&#x200B;을(를) 선택하여 경로를 수동으로 추가할 수 있습니다.

* **[!UICONTROL 경로 제목]**: 경로의 제목을 지정합니다. AEM 받은 편지함에 표시됩니다.
* **[!UICONTROL Coral 아이콘]**: coral 아이콘의 HTML 특성을 지정합니다. Adobe CorelUI 라이브러리는 광범위한 터치 우선 아이콘 세트를 제공합니다. 경로를 선택하고 아이콘을 사용할 수 있습니다. AEM 받은 편지함에 제목과 함께 표시됩니다. 경로를 변수에 저장하는 경우 경로는 기본 &quot;태그&quot; 코랄 아이콘을 사용합니다.
* **[!UICONTROL 피할당자가 주석을 추가하도록 허용]**: 작업에 대한 주석을 활성화하려면 이 옵션을 선택하십시오. 할당자는 작업을 제출할 때 AEM 받은 편지함 내에서 주석을 추가할 수 있습니다.
* **[!UICONTROL 변수에 주석 저장]**: String 데이터 형식의 변수에 주석을 저장합니다. 이 옵션은 **[!UICONTROL 피할당자의 주석 추가 허용]** 확인란을 선택하는 경우에만 표시됩니다.

* **[!UICONTROL 피할당자가 첨부 파일을 작업에 추가하도록 허용]**: 작업에 대한 첨부 파일을 활성화하려면 이 옵션을 선택하십시오. 할당자는 작업을 제출할 때 AEM 받은 편지함 내에서 첨부 파일을 추가할 수 있습니다. 첨부 파일의 최대 크기 **[!UICONTROL (최대 파일 크기)]**&#x200B;을(를) 제한할 수도 있습니다. 기본 크기는 2MB입니다.

* **[!UICONTROL 다음을 사용하여 출력 작업 첨부 파일 저장]**: 첨부 파일 폴더의 위치를 지정하십시오. 페이로드와 관련된 경로 또는 문서 데이터 유형 배열의 변수를 사용하여 출력 작업 첨부 파일을 저장할 수 있습니다. 이 옵션은 **[!UICONTROL 피할당자가 작업에 첨부 파일을 추가하도록 허용]** 확인란을 선택하고 **[!UICONTROL 양식/문서]** 탭의 **[!UICONTROL 유형]** 드롭다운 목록에서 **[!UICONTROL 적응형 양식]**, **[!UICONTROL 읽기 전용 적응형 양식]** 또는 **[!UICONTROL 비대화형 PDF 문서]**&#x200B;를 선택하는 경우에만 표시됩니다.

* **[!UICONTROL 사용자 지정 메타데이터 사용]**: 사용자 지정 메타데이터 필드를 활성화하려면 이 옵션을 선택하십시오. 사용자 지정 메타데이터는 이메일 템플릿에 사용됩니다.
* **[!UICONTROL 사용자 지정 메타데이터]**: 전자 메일 템플릿에 대한 사용자 지정 메타데이터를 선택합니다. 사용자 지정 메타데이터는 apps/fd/dashboard/scripts/metadataScripts의 crx-repository에서 사용할 수 있습니다. 지정된 경로가 crx-repository에 없습니다. 관리자는 경로를 사용하기 전에 경로를 만듭니다. 사용자 지정 메타데이터에 서비스를 사용할 수도 있습니다. `WorkitemUserMetadataService` 인터페이스를 확장하여 사용자 지정 메타데이터를 제공할 수도 있습니다.
* **[!UICONTROL 이전 단계의 데이터 표시]**: 피할당자가 이전 피할당자, 작업에 이미 수행된 작업, 작업에 추가된 댓글 및 완료된 작업의 기록 문서(사용 가능한 경우)를 볼 수 있도록 하려면 이 옵션을 선택하십시오.
* **[!UICONTROL 후속 단계에서 데이터 표시]**: 현재 피할당자가 수행한 작업과 후속 피할당자가 작업에 추가한 설명을 볼 수 있도록 하려면 이 옵션을 선택하십시오. 또한 현재 피할당자가 가능한 경우 완료된 작업의 기록 문서를 볼 수 있습니다.
* **[!UICONTROL 데이터 형식의 가시성]**: 기본적으로 할당자는 기록 문서, 할당자, 수행한 작업 및 이전 및 후속 할당자가 추가한 댓글을 볼 수 있습니다. 할당자에게 표시되는 데이터 유형을 제한하려면 데이터 유형 표시 옵션을 사용합니다.

>[!NOTE]
>
>외부 데이터 저장소에 대한 AEM 워크플로 모델을 구성할 때 작업 할당 단계를 초안으로 저장하고 작업 할당 단계의 기록을 검색하는 옵션이 비활성화됩니다. 또한 받은 편지함에서 저장 옵션이 비활성화됩니다.

## PDF/A 단계로 전환 {#convert-pdfa}

PDF/A는 글꼴을 포함하고 파일의 압축을 해제하여 문서 내용을 장기간 보존하기 위한 보관 형식입니다. 따라서 PDF/A 문서는 일반적으로 표준 PDF 문서보다 큽니다. AEM 워크플로의 ***PDF/A로 변환*** 단계를 사용하여 PDF 문서를 PDF/A 형식으로 변환할 수 있습니다.

PDF/A로 변환 단계에는 다음 속성이 있습니다.

**[!UICONTROL 입력 문서]**: 입력 문서는 페이로드에 상대적이거나 절대 경로를 가질 수 있으며 페이로드로 제공되거나 문서 데이터 형식의 변수에 저장될 수 있습니다.

**[!UICONTROL 변환 옵션]**: 이 속성을 사용하여 PDF 문서를 PDF/A 문서로 변환하는 설정이 지정됩니다. 이 탭에서 사용할 수 있는 다양한 옵션은 다음과 같습니다.
* **[!UICONTROL 준수]**: 출력 PDF/A 문서가 준수해야 하는 표준을 지정합니다. PDF/A-1b, PDF/A-2b 또는 PDF/A-3b와 같은 다양한 PDF 표준을 지원합니다.
* **[!UICONTROL 결과 수준]**: 전환 출력의 결과 수준을 PassFail, Summary 또는 Detailed로 지정합니다.
* **[!UICONTROL 색상 공간]**: 미리 정의된 색상 공간을 출력 PDF/A 파일에 사용할 수 있는 S_RGB, COATED_FOGRA27, JAPAN_COLOR_COATED 또는 SWOP로 지정합니다.
* **[!UICONTROL 선택적 컨텐츠]**: 지정된 기준 세트를 충족할 때만 특정 그래픽 개체 및/또는 주석을 출력 PDF/A 문서에 표시할 수 있습니다.

**[!UICONTROL 출력 문서]**: 출력 파일을 저장할 위치를 지정합니다. 출력 파일은 페이로드에 상대적인 위치에 저장하거나, 페이로드가 파일인 경우 페이로드를 덮어쓰거나, 문서 데이터 유형의 변수에 저장할 수 있습니다.


## 이메일 전송 단계 {#send-email-step}

전자 메일 단계를 사용하여 전자 메일(예: 기록 문서, 적응형 양식 <!-- , link of an interactive communication-->의 링크 또는 첨부된 PDF 문서)을 보낼 수 있습니다. 이메일 전송 단계는 [HTML 이메일](https://en.wikipedia.org/wiki/HTML_email)을 지원합니다. HTML 이메일은 응답형이며 수신자의 이메일 클라이언트 및 화면 크기에 맞게 조정됩니다. HTML 이메일 템플릿을 사용하여 이메일의 모양, 색상 구성표 및 비헤이비어를 정의할 수 있습니다.

이메일 단계는 일별 CQ 메일 서비스를 사용하여 이메일을 전송합니다. 이메일 단계를 사용하기 전에 이메일 서비스가 구성되어 있는지 확인하십시오. 기본적으로 이메일은 HTTP 및 HTTPs 프로토콜만 지원합니다. [지원 팀에 문의](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/development-guidelines.html?lang=ko#sending-email)하여 포트를 통해 전자 메일을 보내고 환경에 SMTP 프로토콜을 사용하도록 설정하십시오. 제한은 플랫폼의 보안을 향상시키는 데 도움이 됩니다.

이메일 단계에는 다음과 같은 속성이 있습니다.

**[!UICONTROL 제목]**: 단계의 제목은 워크플로 편집기에서 단계를 식별하는 데 도움이 됩니다.

**[!UICONTROL 설명]**: 설명은 공유 개발 환경에서 작업할 때 다른 프로세스 개발자에게 유용합니다.

**[!UICONTROL 이메일 제목]**: 제목은 워크플로우 메타데이터에서 검색하거나, 수동으로 지정하거나, 변수에 저장된 값에서 검색할 수 있습니다. 다음 옵션 중에서 선택합니다.

* **[!UICONTROL 리터럴]** 제목을 수동으로 지정합니다.
* **[!UICONTROL 워크플로 메타데이터에서 검색]** - 메타데이터 속성에서 제목을 검색합니다.
* **[!UICONTROL 변수]** - 문자열 데이터 형식의 변수에 저장된 값에서 제목을 검색합니다.

**[!UICONTROL HTML 전자 메일 서식 파일]**: 전자 메일의 HTML 서식 파일입니다. 이메일 템플릿에서 변수를 지정할 수 있습니다. 이메일 단계는 입력을 위해 템플릿에 포함된 모든 변수를 추출하여 표시합니다.

**[!UICONTROL 전자 메일 템플릿 메타데이터]**: 전자 메일 템플릿 변수의 값은 사용자 지정 값, 작성자 또는 게시 서버에 있는 에셋의 경로, 이미지 또는 워크플로 메타데이터 속성일 수 있습니다.

* **[!UICONTROL 리터럴]**: 지정할 정확한 값을 알고 있는 경우 옵션을 사용하십시오. 예: [example@example.com](mailto:example@example.com).

* **[!UICONTROL 워크플로 메타데이터]**: 사용할 값을 워크플로 메타데이터 속성에 저장할 때 옵션을 사용합니다. 옵션을 선택한 후 워크플로 메타데이터 옵션 아래의 빈 텍스트 상자에 메타데이터 속성 이름을 입력합니다. 예를 들어 emailAddress입니다.

<!-- 

* **[!UICONTROL Asset URL]**: Use the option to embed a web link of an interactive communication to the email. After selecting the option, browse and choose the interactive communication to embed. The asset can reside on the author or the publish server. 

-->

* **[!UICONTROL 이미지]**: 전자 메일에 이미지를 포함하려면 옵션을 사용합니다. 옵션을 선택한 후 이미지를 찾아 선택합니다. 이미지 옵션은 전자 메일 템플릿에 있는 이미지 태그(&lt;img src=&quot;&#42;&quot;/>)에만 사용할 수 있습니다.

**[!UICONTROL 보낸 사람/받는 사람의 전자 메일 주소]**: 전자 메일 주소를 수동으로 지정하려면 **[!UICONTROL Literal]** 옵션을 선택하거나, 메타데이터 속성에서 전자 메일 주소를 검색하려면 **[!UICONTROL 워크플로 메타데이터에서 검색]** 옵션을 선택하십시오. **[!UICONTROL 워크플로우 메타데이터에서 검색]** 옵션에 대한 메타데이터 속성 배열 목록을 지정할 수도 있습니다. 문자열 데이터 형식의 변수에 저장된 값에서 전자 메일 주소를 검색하려면 **[!UICONTROL 변수]** 옵션을 선택하십시오.

* **[!UICONTROL 첨부 파일]**: 지정한 위치에서 사용할 수 있는 자산이 전자 메일에 첨부되어 있습니다. 에셋의 경로는 페이로드나 절대 경로를 기준으로 할 수 있습니다. 예제 경로는 [Payload_Directory]/attachments/입니다.

문서, XML 또는 JSON 데이터 형식의 변수에 저장된 첨부 파일을 검색하려면 **[!UICONTROL 변수]** 옵션을 선택하십시오.

**[!UICONTROL 파일 이름]**: 전자 메일 첨부 파일의 이름입니다. 이메일 단계에서 첨부 파일의 원래 파일 이름을 지정된 파일 이름으로 변경합니다. 이름을 수동으로 지정하거나 워크플로우 메타데이터 속성 또는 변수에서 검색할 수 있습니다. 지정할 정확한 값을 알고 있는 경우 **[!UICONTROL Literal]** 옵션을 사용하십시오. 문자열 데이터 형식의 변수에 저장된 값에서 파일 이름을 검색하려면 **[!UICONTROL 변수]** 옵션을 사용하십시오. 사용할 값이 워크플로 메타데이터 속성에 저장되면 **[!UICONTROL 워크플로 메타데이터에서 검색]** 옵션을 사용하십시오.

## 기록 문서 생성 단계 {#generate-document-of-record-step}

양식을 작성하거나 제출할 때 인쇄 또는 문서 형식으로 양식의 기록을 유지할 수 있습니다. 이 레코드를 DoR(기록 문서)이라고 합니다. 기록 문서 생성 단계를 사용하여 적응형 양식의 읽기 전용 또는 대화형 PDF 버전을 생성할 수 있습니다. PDF 버전에는 적응형 양식의 레이아웃과 함께 양식에 입력된 정보가 포함되어 있습니다.

기록 문서 단계에는 다음과 같은 속성이 있습니다.

**[!UICONTROL 적응형 양식 사용]**: 입력 적응형 양식을 찾을 방법을 지정하십시오. 워크플로우에 제출된 적응형 양식을 사용하거나, 절대 경로에서 사용하거나, 변수의 경로에서 사용할 수 있습니다. String 데이터 형식의 변수를 사용하여 **[!UICONTROL 해결할 변수 선택]** 필드에 경로를 지정할 수 있습니다.\
여러 적응형 Forms을 워크플로우와 연결할 수 있습니다. 따라서 사용 가능한 입력 방법을 사용하여 런타임에 적응형 양식을 지정할 수 있습니다.

**[!UICONTROL 적응형 양식 경로]**: 적응형 양식의 경로를 지정하십시오. **[!UICONTROL 적응형 양식 사용]** 필드에서 **[!UICONTROL 절대 경로에서 사용 가능]** 옵션을 선택하면 이 필드를 사용할 수 있습니다.

**[!UICONTROL 다음을 사용하여 입력 데이터 선택]**: 적응형 양식에 대한 입력 데이터 경로. 페이로드를 기준으로 한 위치에 데이터를 유지하거나, 데이터의 절대 경로를 지정하거나, 문서, JSON 또는 XML 데이터 유형의 변수에 저장된 데이터를 검색할 수 있습니다. 입력 데이터를 적응형 양식과 병합하여 기록 문서를 만듭니다.

**[!UICONTROL 다음을 사용하여 입력 첨부 파일 경로 선택]**: 첨부 파일의 경로. 이러한 첨부 파일은 기록 문서에 포함됩니다. 페이로드를 기준으로 첨부 파일을 특정 위치에 유지하거나, 첨부 파일의 절대 경로를 지정하거나, 문서 데이터 유형 배열의 변수에 저장된 첨부 파일을 검색할 수 있습니다.

첨부 파일 등 폴더의 경로를 지정하면 해당 폴더에서 직접 사용할 수 있는 모든 파일이 기록 문서에 첨부됩니다. 지정된 첨부 경로에서 직접 사용할 수 있는 폴더에서 파일을 사용할 수 있는 경우 해당 파일은 기록 문서에 첨부 파일로 포함됩니다. 직접 사용 가능한 폴더에 폴더가 있는 경우 해당 폴더는 건너뜁니다.

**[!UICONTROL 아래 옵션을 사용하여 생성된 기록 문서 저장]**: 기록 문서 파일을 보관할 위치를 지정하십시오. 페이로드 폴더를 덮어쓰거나 페이로드 디렉토리 내의 위치에 기록 문서를 배치하거나 문서 데이터 유형의 변수에 기록 문서를 저장하도록 선택할 수 있습니다.

**[!UICONTROL 로케일]**: 기록 문서의 언어를 지정합니다. **[!UICONTROL Literal]**&#x200B;을(를) 선택하여 드롭다운 목록에서 로케일을 선택하거나 **[!UICONTROL 변수]**&#x200B;을(를) 선택하여 문자열 데이터 형식의 변수에 저장된 값에서 로케일을 검색합니다. 로케일 값을 변수에 저장하면서 로케일 코드를 정의합니다. 예를 들어, 영어는 **en_US**, 프랑스어는 **fr_FR**&#x200B;을 지정하십시오.

## DDX 단계 호출 {#invokeddx}

DDX(Document Description XML)는 문서의 구성 요소를 나타내는 선언적 마크업 언어입니다. 이러한 구성 요소에는 PDF 및 XDP 문서는 물론 댓글, 책갈피 및 스타일이 지정된 텍스트와 같은 기타 요소가 포함됩니다. DDX는 하나 이상의 입력 문서에 적용되어 하나 이상의 출력 문서를 생성할 수 있는 일련의 작업을 정의합니다. 단일 DDX를 다양한 원본 문서와 함께 사용할 수 있습니다. AEM Workflow의 ***DDX 호출 단계***&#x200B;을 사용하여 문서 어셈블/디스어셈블, Acrobat 및 XFA Forms 만들기 및 수정, [DDX 참조 설명서](https://helpx.adobe.com/content/dam/help/en/experience-manager/forms-cloud-service/ddxRef.pdf)에 설명된 기타 작업과 같은 다양한 작업을 수행할 수 있습니다.

DDX 호출 단계에는 다음 속성이 있습니다.

**[!UICONTROL 입력 문서]**: 입력 문서의 속성을 설정하는 데 사용됩니다. 이 탭에서 사용할 수 있는 다양한 옵션은 다음과 같습니다.
* **[!UICONTROL DDX 지정 사용]**: 페이로드에 상대적인 입력 문서를 지정하거나, 절대 경로를 가지거나, 페이로드로 제공하거나, 문서 데이터 형식의 변수에 저장할 수 있습니다.
* **[!UICONTROL 페이로드에서 맵 만들기]**: 페이로드 폴더 아래의 모든 문서를 어셈블러에서 호출 API에 대한 입력 문서 맵에 추가하십시오. 각 문서의 노드 이름은 맵에서 키로 사용됩니다.
* **[!UICONTROL 입력 문서 맵]**: 옵션은 **[!UICONTROL 추가]** 단추를 사용하여 여러 항목을 추가하는 데 사용됩니다. 각 항목은 맵에서 문서의 키와 문서의 소스를 나타냅니다.

**[!UICONTROL 환경 옵션]**: 이 옵션은 API 호출에 대한 처리 설정을 설정하는 데 사용됩니다. 이 탭에서 사용할 수 있는 다양한 옵션은 다음과 같습니다.
* **[!UICONTROL 만 확인]**: 입력 DDX 문서의 유효성을 검사합니다.
* **[!UICONTROL 오류 시 실패]**: 오류가 있는 경우 API 호출 서비스 실패 여부를 나타내는 부울 값입니다. 기본적으로 이 값은 False로 설정됩니다.
* **[!UICONTROL 첫 번째 베이츠 수]**: 자동으로 증가하는 수를 지정합니다. 이 자가 증분 숫자는 각 연속 페이지에 자동으로 표시됩니다.
* **[!UICONTROL 기본 스타일]**: 출력 파일의 기본 스타일을 설정합니다.

>[!NOTE]
>
>환경 옵션은 HTTP API와 계속 동기화됩니다.

**[!UICONTROL 출력 문서]**: 출력 파일을 저장할 위치를 지정합니다. 이 탭에서 사용할 수 있는 다양한 옵션은 다음과 같습니다.
* **[!UICONTROL 페이로드에 출력 저장]**: 페이로드가 파일인 경우 페이로드 폴더 아래에 출력 문서를 저장하거나 페이로드를 덮어씁니다.
* **[!UICONTROL 출력 문서의 맵]**: 문서당 하나의 항목을 추가하여 각 문서 파일을 명시적으로 저장할 위치를 지정합니다. 각 항목은 문서와 문서를 저장할 위치를 나타냅니다. 출력 문서가 여러 개 있는 경우 이 옵션이 사용됩니다.

## 양식 데이터 모델(FDM) 서비스 단계 호출 {#invoke-form-data-model-service-step}

[[!DNL AEM Forms] 데이터 통합](data-integration.md)을 사용하여 서로 다른 데이터 원본을 구성하고 연결할 수 있습니다. 이러한 데이터 소스는 웹 서비스, REST 서비스, OData 서비스 및 CRM 솔루션일 수 있습니다. [!DNL AEM Forms] 데이터 통합을 사용하면 구성된 데이터베이스에서 데이터 검색, 추가 및 업데이트 작업을 수행하는 다양한 서비스를 포함하는 양식 데이터 모델(FDM)을 만들 수 있습니다. **[!UICONTROL 데이터 모델 서비스 호출 단계]**&#x200B;을(를) 사용하여 FDM(양식 데이터 모델)을 선택하고 FDM의 서비스를 사용하여 데이터를 검색, 업데이트 또는 개별 데이터 소스에 추가할 수 있습니다.

단계의 필드에 대한 입력을 설명하기 위해 다음 데이터베이스 테이블과 JSON 파일이 예제로 사용됩니다.

**[!UICONTROL 샘플 CustomerDetails 테이블]**

<table>
 <tbody> 
  <tr> 
   <td>속성</td> 
   <td>값<br /> </td> 
  </tr> 
  <tr> 
   <td>이름<br /> </td> 
   <td>Sarah<br /> </td> 
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
   <td>전자 메일 주소<br /> </td> 
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

FDM(양식 데이터 모델) 호출 서비스 단계에는 FDM(양식 데이터 모델) 작업을 용이하게 하기 위해 아래에 나열된 필드가 있습니다.

* **[!UICONTROL 제목]**: 단계의 제목입니다. 워크플로우 편집기에서 단계를 식별하는 데 도움이 됩니다.
* **[!UICONTROL 설명]**: 공유 개발 환경에서 작업할 때 다른 프로세스 개발자에게 유용한 설명입니다.

* **[!UICONTROL 양식 데이터 모델 경로]**: 서버에 있는 FDM(양식 데이터 모델)을 찾아 선택합니다.

* **[!UICONTROL 오류 및 유효성 검사]**: 옵션을 사용하면 오류 메시지를 캡처하고 데이터 소스로 검색 및 전송되는 데이터에 대한 유효성 검사 옵션을 지정할 수 있습니다. 이러한 변경 사항으로 FDM(양식 데이터 모델 호출) 서비스 단계로 전달된 데이터가 데이터 소스에 의해 정의된 데이터 제약 조건을 준수하는지 확인할 수 있습니다. 자세한 내용은 [입력 데이터의 자동 유효성 검사](work-with-form-data-model.md#automated-validation-of-input-data)를 참조하십시오.

* **[!UICONTROL 유효성 검사 수준]**: [기본], [전체] 및 [해제]의 세 가지 유효성 검사 범주가 있습니다.

   * 전체: 모든 제한조건이 검증됩니다.
   * 기본: 필수 및 nullable 제약 조건만
   * 끔: 유효성 검사가 수행되지 않습니다.

* **[!UICONTROL 실패 시 워크플로 종료]**: 제약 조건의 유효성을 검사하지 못하면 워크플로가 중지됩니다.

* **[!UICONTROL 변수에 오류 코드 저장]**: [String 형식 변수](variable-in-aem-workflows.md)에 오류 코드를 저장할 수 있습니다.

* **[!UICONTROL 변수에 오류 메시지 저장]**: [String 형식 변수](variable-in-aem-workflows.md)에 오류 메시지를 저장할 수 있습니다.

* **[!UICONTROL 변수에 오류 세부 정보 저장]**: [JSON 형식 변수](variable-in-aem-workflows.md)에 오류 세부 정보를 저장할 수 있습니다.

* **[!UICONTROL 서비스]**: 선택한 FDM(양식 데이터 모델)이 제공하는 서비스 목록입니다.
* **[!UICONTROL 서비스에 대한 입력]** > **[!UICONTROL 리터럴, 변수 또는 워크플로 메타데이터 및 JSON 파일을 사용하여 입력 데이터를 제공합니다]**: 서비스에는 여러 인수가 있을 수 있습니다. 옵션을 선택하여 워크플로우 메타데이터 속성, JSON 개체, 변수에서 서비스 인수의 값을 가져오거나 제공된 텍스트 상자에 값을 직접 입력합니다.

   * **[!UICONTROL 리터럴]**: 지정할 정확한 값을 알고 있는 경우 옵션을 사용하십시오. 예: srose@we.info.
   * **[!UICONTROL 변수]**: 변수에 저장된 값을 검색하려면 옵션을 사용하십시오.
   * **[!UICONTROL 워크플로 메타데이터에서 검색]**: 사용할 값이 워크플로 메타데이터 속성에 저장될 때 옵션을 사용하십시오. 예를 들어 emailAddress입니다.

   * **[!UICONTROL 페이로드 관련]**: 옵션을 사용하여 페이로드 관련 경로에 저장된 첨부 파일을 검색합니다. 옵션을 선택하고 첨부 파일을 포함하는 폴더 이름을 지정하거나 텍스트 상자에 첨부 파일 이름을 지정합니다.

     >[!NOTE]
     >
     > **양식 데이터 모델 호출** 워크플로 단계는 [SharePoint 목록 기반 양식 데이터 모델](/help/forms/connect-forms-to-sharepoint-list.md)의 Base64 인코딩 첨부 파일 배열에 대한 워크플로 측 메타데이터를 지원하며 워크플로에서 첨부 파일에 대한 파일 이름, MIME 유형 또는 사용자 지정 속성과 같은 메타데이터를 전달, 저장 및 검색할 수 있도록 합니다.
     > ![SP 목록 첨부 파일](/help/edge/docs/forms/assets/workflow-sp-list.png)
     >
     > 페이로드 관련 폴더에 `attachment` 위치에 첨부 파일이 있습니다. `attachment`페이로드 관련&#x200B;**[!UICONTROL 옵션을 선택한 후 텍스트 상자에]**&#x200B;을(를) 지정하십시오.

   * **[!UICONTROL JSON 점 표기법]**: 사용할 값이 JSON 파일에 있는 경우 옵션을 사용합니다. 예: insurance.customerDetails.emailAddress. JSON 점 표기법 옵션은 입력 JSON 옵션의 입력 필드 매핑 을 선택한 경우에만 사용할 수 있습니다.
   * **[!UICONTROL 입력 JSON의 입력 필드 매핑]**: JSON 파일의 경로를 지정하여 JSON 파일에서 일부 서비스 인수의 입력 값을 가져옵니다. JSON 파일의 경로는 페이로드 또는 절대 경로에 상대적이거나 JSON 또는 양식 데이터 모델(FDM) 유형의 변수를 사용하여 입력 JSON 문서를 선택할 수 있습니다.

* **[!UICONTROL 서비스에 대한 입력]** > **[!UICONTROL 변수 또는 JSON 파일을 사용하여 입력 데이터 제공]**: 절대 경로, 페이로드 관련 경로 또는 변수에 저장된 JSON 파일에서 모든 인수의 값을 가져오려면 옵션을 선택하십시오.
* **[!UICONTROL 다음을 사용하여 입력 JSON 문서 선택]**: 모든 서비스 인수의 값이 들어 있는 JSON 파일입니다. JSON 파일의 경로는 페이로드에 상대적인 **[!UICONTROL 이거나]** 또는 **[!UICONTROL 절대 경로]**&#x200B;일 수 있습니다. JSON 또는 양식 데이터 모델(FDM) 데이터 유형의 변수를 사용하여 입력 JSON 문서를 검색할 수도 있습니다.

* **[!UICONTROL JSON 점 표기법]**: 지정된 JSON 파일의 모든 개체를 서비스 인수에 대한 입력으로 사용하려면 필드를 비워 둡니다. 서비스 인수에 대한 입력으로 지정된 JSON 파일의 특정 JSON 개체를 읽으려면 JSON 개체에 대한 점 표기법을 지정하십시오. 예를 들어 섹션의 시작 부분에 나열된 것과 유사한 JSON이 있는 경우 insurance.customerDetails를 지정하여 고객의 모든 세부 정보를 서비스에 대한 입력으로 제공합니다.
* **[!UICONTROL 서비스 출력]** > **[!UICONTROL 변수 또는 메타데이터에 출력 값 매핑 및 쓰기]**: crx-repository에 있는 워크플로 인스턴스 메타데이터 노드의 속성으로 출력 값을 저장하는 옵션을 선택합니다. 메타데이터 속성의 이름을 지정하고 메타데이터 속성과 매핑할 해당 서비스 출력 속성을 선택합니다. 예를 들어 출력 서비스에서 반환된 phone_number를 워크플로우 메타데이터의 phone_number 속성과 매핑합니다. 마찬가지로 출력을 Long 데이터 형식의 변수에 저장할 수 있습니다. **[!UICONTROL 매핑할 서비스 출력 특성]** 옵션에 대한 속성을 선택하면 선택한 속성의 데이터를 저장할 수 있는 변수만 **[!UICONTROL 출력을 저장]** 옵션에 대해 채워집니다.

* **[!UICONTROL 서비스 출력]** > **[!UICONTROL 출력을 변수 또는 JSON 파일에 저장]**: 출력 값을 JSON 파일의 절대 경로, 페이로드에 상대적인 경로 또는 변수에 저장하는 옵션을 선택합니다.
* **[!UICONTROL 아래 옵션을 사용하여 출력 JSON 문서 저장]**: 출력 JSON 파일을 저장합니다. 출력 JSON 파일의 경로는 페이로드에 상대적이거나 절대 경로일 수 있습니다. JSON 또는 양식 데이터 모델(FDM) 데이터 유형의 변수를 사용하여 출력 JSON 파일을 저장할 수도 있습니다.



## 문서 서명 단계 {#sign-document-step}

문서 서명 단계에서는 [!DNL Adobe Sign]을(를) 사용하여 문서에 서명할 수 있습니다. [!DNL Adobe Sign] 워크플로 단계를 사용하여 적응형 양식에 서명할 때, 워크플로 단계의 구성에 따라 양식이 받는 사람 간에 전달되거나 모든 받는 사람에게 동시에 전달될 수 있습니다. [!DNL Adobe Sign] 사용 응용 Forms은 모든 수신자가 서명 프로세스를 완료한 후에만 Experience Manager Forms 서버로 제출됩니다.

기본적으로 [!DNL Adobe Sign] 스케줄러 서비스는 24시간마다 수신자 응답을 확인(폴링)합니다. [환경의 기본 간격을 변경](adobe-sign-integration-adaptive-forms.md#for-aem-workflows-only-configure-dnl-adobe-acrobat-sign-scheduler-to-sync-the-signing-status-configure-adobe-sign-scheduler-to-sync-the-signing-status)할 수 있습니다.

문서 서명 단계에는 다음과 같은 속성이 있습니다.

* **[!UICONTROL 계약 이름]**: 계약의 제목을 지정합니다. 계약 이름은 서명자에게 전송된 이메일의 제목과 본문의 일부가 됩니다. String 데이터 형식의 변수에 이름을 저장하거나 **[!UICONTROL 리터럴]**&#x200B;을 선택하여 이름을 수동으로 추가할 수 있습니다.

* **[!UICONTROL 로케일]**: 전자 메일 및 확인 옵션에 사용할 언어를 지정합니다. String 데이터 형식의 변수에 로케일을 저장하거나 **[!UICONTROL 리터럴]**&#x200B;을 선택하여 사용 가능한 옵션 목록에서 로케일을 선택할 수 있습니다. 로케일의 값을 변수에 저장하는 동안 로케일 코드를 정의해야 합니다. 예를 들어, 영어는 **[!UICONTROL en_US]**, 프랑스어는 **[!UICONTROL fr_FR]**&#x200B;을 지정하십시오.

* **[!UICONTROL Adobe Sign 클라우드 구성]**: [!DNL Adobe Sign] 클라우드 구성을 선택하십시오. [!DNL Adobe Sign]에 대해 [!DNL AEM Forms]을(를) 구성하지 않은 경우 [Adobe Sign과 통합 [!DNL AEM Forms]](adobe-sign-integration-adaptive-forms.md)을 참조하세요.

* **[!UICONTROL 서명할 문서 선택]**: 페이로드에 상대적인 위치에서 문서를 선택하거나, 페이로드를 문서로 사용하거나, 문서의 절대 경로를 지정하거나, 문서 데이터 형식의 변수에 저장된 문서를 검색할 수 있습니다.
* **[!UICONTROL 기한까지]**: **[!UICONTROL 기한까지]** 필드에 지정된 일 수에 대한 작업 활동이 없으면 문서에 기한(기한 지남)으로 표시됩니다. 문서가 사용자에게 서명에 할당된 후 일 수가 계산됩니다.
* **[!UICONTROL 미리 알림 전자 메일 빈도]**: 매일 또는 매주 미리 알림 전자 메일을 보낼 수 있습니다. 주는 문서가 사용자에게 서명에 할당된 날로부터 계산됩니다.
* **[!UICONTROL 서명 프로세스]**: 문서에 순차적 또는 병렬 순서로 서명하도록 선택할 수 있습니다. 서명자 한 사람이 서명할 문서를 한 번에 순차적으로 받습니다. 첫 번째 서명자가 문서 서명을 완료한 후 문서는 두 번째 서명자에게 전송됩니다. 여러 서명자가 문서에 한 번에 서명할 수 있습니다.
* **[!UICONTROL 리디렉션 URL]**: 리디렉션 URL을 지정하십시오. 문서에 서명한 후 피할당자를 URL로 리디렉션할 수 있습니다. 일반적으로 이 URL에는 감사 메시지나 추가 지침이 포함되어 있습니다.
* **[!UICONTROL 워크플로 단계]**: 워크플로에는 여러 단계가 있을 수 있습니다. 이러한 단계는 AEM 받은 편지함에 표시됩니다. 모델의 속성(**[!UICONTROL Sidekick]** > **[!UICONTROL 페이지]** > **[!UICONTROL 페이지 속성]** > **[!UICONTROL 단계]**)에서 이러한 단계를 정의할 수 있습니다.
* **[!UICONTROL 수신자 선택]**: 문서에 대한 수신자를 선택할 메서드를 지정합니다. 워크플로우를 사용자 또는 그룹에 동적으로 할당하거나 수신자의 세부 정보를 수동으로 추가할 수 있습니다. 드롭다운 목록에서 수동으로 를 선택하면 이메일, 역할 및 인증 방법과 같은 수신자 세부 정보를 추가합니다.

  >[!NOTE]
  >
  >* 역할 섹션에서 수신자 역할을 서명자, 승인자, 승인자, 인증된 수신자, 양식 작성자 및 위임자로 지정할 수 있습니다.
  >* 역할 옵션에서 위임자를 선택하면 위임자가 서명 작업을 다른 수신자에게 할당할 수 있습니다.
  >* [!DNL Adobe Sign]에 대한 인증 방법을 구성한 경우 구성에 따라 전화 기반 인증, 소셜 ID 기반 인증, 기술 자료 기반 인증, 정부 ID 기반 인증과 같은 인증 방법을 선택합니다.

* **[!UICONTROL 수신자를 선택하는 스크립트 또는 서비스]**: 이 옵션은 [수신자 선택] 필드에서 [동적으로] 옵션을 선택한 경우에만 사용할 수 있습니다. ECMAScript 또는 서비스를 지정하여 문서에 대한 서명자 및 확인 옵션을 선택할 수 있습니다.
* **[!UICONTROL 받는 사람 세부 정보]**: 이 옵션은 받는 사람 선택 필드에서 수동으로 옵션을 선택한 경우에만 사용할 수 있습니다. 이메일 주소를 지정하고 선택적 확인 메커니즘을 선택합니다. 2단계 확인 메커니즘을 선택하기 전에 구성된 [!DNL Adobe Sign] 계정에 대해 해당 확인 옵션이 활성화되어 있는지 확인하십시오. 문자열 데이터 유형의 변수를 사용하여 전자 메일, 국가 코드 및 전화 번호 필드에 대한 값을 정의할 수 있습니다. 국가 코드 및 전화 번호 필드는 2단계 확인 드롭다운 목록에서 전화 확인을 선택한 경우에만 표시됩니다.
* **[!UICONTROL 서명된 문서]**: 서명된 문서의 상태를 변수에 저장할 수 있습니다. 서명된 문서에 보안 및 합법성을 강화하기 위해 전자 서명 감사 추적을 추가하려면 감사 보고서를 포함할 수 있습니다. 변수 또는 페이로드 폴더를 사용하여 서명된 문서를 저장할 수 있습니다.

  >[!NOTE]
  >
  > 감사 보고서는 서명된 문서의 마지막 페이지에 추가됩니다.

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
* **[!UICONTROL Indirect accessible printer]**: The printer that is installed on a print server is accessed from other computers. Technologies such as the common UNIX&reg; printing system (CUPS) and the Line Printer Daemon (LPD) protocol are available to connect to a network printer. To access an indirect accessible printer, specify the print server's IP or host name. Using this mechanism, you can send a document to an LPD URI when the network has an LPD running. The mechanism lets you route the document to any printer that is connected to the network that has an LPD running.
    -->

## 인쇄된 출력 생성 단계 {#generatePrintedOutput}

이 단계에서는 양식 디자인 및 데이터 파일이 지정된 PCL, PostScript, ZPL, IPL, TPCL 또는 DPL 출력을 생성합니다. 데이터 파일이 양식 디자인과 병합되고 인쇄용으로 서식이 지정됩니다. 이 단계에서 생성된 출력을 프린터로 직접 보내거나 파일로 저장할 수 있습니다. 양식 디자인이나 응용 프로그램의 데이터를 사용하려는 경우 이 단계를 사용하는 것이 좋습니다. 양식 디자인이 네트워크, 로컬 파일 시스템 또는 HTTP 위치에 있는 경우 generatePrintedOutput 작업을 사용합니다.

예를들어 양식 디자인을 데이터 파일과 병합해야 합니다. 데이터에는 수백 개의 레코드가 포함되어 있습니다. 또한 ZPL을 지원하는 프린터로 출력이 전송되어야 합니다. 양식 디자인과 입력 데이터는 응용 프로그램에 있습니다. generatePrintedOutput 작업을 사용하여 각 레코드를 양식 디자인과 병합하고 ZPL을 지원하는 프린터로 출력을 보냅니다.

인쇄 출력 생성 단계에는 다음과 같은 속성이 있습니다.

**[!UICONTROL 입력 속성]**

* **[!UICONTROL 다음을 사용하여 템플릿 파일 선택]**: 템플릿 파일의 경로를 지정합니다. 페이로드에 상대적인 경로나 절대 경로에 저장된 경로 또는 문서 데이터 유형의 변수를 사용하여 템플릿 파일을 선택할 수 있습니다. 예: [Payload_Directory]/Workflow/data.xml. 경로가 crx-repository에 없는 경우 관리자는 경로를 사용하기 전에 경로를 만들 수 있습니다. 또한 페이로드를 입력 데이터 파일로 승인할 수도 있습니다.

* **[!UICONTROL 다음을 사용하여 데이터 문서 선택]**: 입력 데이터 파일의 경로를 지정합니다. 페이로드와 관련된 경로, 절대 경로에 저장된 경로 또는 문서 데이터 유형의 변수를 사용하여 입력 데이터 파일을 선택할 수 있습니다. 예: [Payload_Directory]/Workflow/data.xml. 경로가 crx-repository에 없는 경우 관리자는 경로를 사용하기 전에 경로를 만들 수 있습니다.

* **[!UICONTROL 프린터 형식]**: 출력 스트림을 생성하기 위해 XDC 파일이 제공되지 않을 때 사용할 페이지 설명 언어를 지정하는 인쇄 형식 값입니다. 리터럴 값을 제공하는 경우 다음 값 중 하나를 선택합니다.

   * **[!UICONTROL 색상 PCL]**: 옵션을 사용하여 PCL용 XDC 파일을 지정하십시오.
   * **[!UICONTROL 일반 PostScript]**: PostScript에 대한 일반 XDC 파일을 지정하려면 옵션을 사용하십시오.
   * **[!UICONTROL ZPL 300 DPI]**: ZPL 300 DPI를 사용합니다. zpl300.xdc가 사용됩니다.
   * **[!UICONTROL ZPL 600 DPI]**: ZPL 600 DPI를 사용합니다. zpl600.xdc 파일이 사용됩니다.
   * **[!UICONTROL IPL 300 DPI]**: IPL 300 DPI를 사용합니다. ipl300.xdc가 사용됩니다.
   * **[!UICONTROL IPL 400 DPI]**: IPL 400 DPI를 사용합니다. ipl400.xdc 파일이 사용됩니다.
   * **[!UICONTROL TPCL 600 DPI]**: TPCL 600 DPI를 사용합니다. tpcl600.xdc 파일이 사용됩니다.
   * **[!UICONTROL PostScript 일반]**: PostScript에 대한 일반 텍스트 XDC 파일을 지정하려면 옵션을 사용하십시오.
   * **[!UICONTROL DPL300DPI]**: DPL 300DPI를 사용하십시오. dpl300.xdc가 사용됩니다.
   * **[!UICONTROL DPL400DPI]**: DPL 400DPI를 사용하십시오. dpl400.xdc가 사용됩니다.
   * **[!UICONTROL DPL600DPI]**: DPL 600DPI를 사용하십시오. dpl600.xdc가 사용됩니다.
   * **[!UICONTROL HP_PCL_5e]**: 여러 Canon 장치를 지원하려면 옵션을 사용하십시오.


**[!UICONTROL 출력 속성]**

* **[!UICONTROL 다음을 사용하여 출력 문서 저장]**: 출력 파일을 저장할 위치를 지정하십시오. 출력 파일을 페이로드와 관련된 위치 또는 변수에 저장하거나 출력 파일을 저장할 절대 위치를 지정할 수 있습니다. 경로가 crx-repository에 없는 경우 관리자는 경로를 사용하기 전에 경로를 만들 수 있습니다.

**[!UICONTROL 고급 속성]**

* **[!UICONTROL 다음을 사용하여 콘텐츠 루트 위치 선택]**: 콘텐츠 루트는 URI, 절대 참조 또는 양식 디자인에 사용되는 상대 에셋을 검색할 저장소의 위치를 지정하는 문자열 값입니다. 예를 들어 양식 디자인에서 `../myImage.gif`과(와) 같은 이미지를 상대적으로 참조하는 경우 `myImage.gif`은(는) `repository://`에 있어야 합니다. 기본값은 저장소의 루트 수준을 가리키는 `repository://`입니다.

  애플리케이션에서 자산을 선택하는 경우 컨텐츠 루트 URI 경로의 구조가 올바른지 확인하십시오. 예를 들어 SampleApp라는 응용 프로그램에서 양식을 선택하고 `SampleApp/1.0/forms/Test.xdp`에 배치하면 콘텐츠 루트 URI를 `repository://administrator@password/Applications/SampleApp/1.0/forms/` 또는 `repository:/Applications/SampleApp/1.0/forms/`(권한이 null인 경우)로 지정해야 합니다. 컨텐츠 루트 URI가 이러한 방식으로 지정되면 양식에 있는 모든 참조된 자산의 경로가 이 URI에 대해 확인됩니다.

* **[!UICONTROL 다음을 사용하여 XCI 파일 선택]**: XCI 파일은 양식 디자인 요소에 사용되는 글꼴 및 기타 속성을 설명하는 데 사용됩니다. 페이로드에 상대적인 XCI 파일을 절대 경로에 두거나 문서 데이터 유형의 변수를 사용할 수 있습니다.

* **[!UICONTROL 로케일]**: PDF 문서 생성에 사용되는 언어를 지정합니다. 리터럴 값을 제공하는 경우 목록에서 언어를 선택하거나 다음 값 중 하나를 선택합니다.
   * **[!UICONTROL 서버 기본값을 사용하려면]**:
(기본값) [!DNL AEM Forms] 서버에 구성된 로케일 설정을 사용합니다. 로케일 설정은 관리 콘솔을 사용하여 구성됩니다. ([Designer 도움말](https://helpx.adobe.com/kr/content/dam/help/en/experience-manager/6-5/forms/pdf/using-designer.pdf)을 참조하세요.)

   * **[!UICONTROL 사용자 지정 값을 사용하려면]**:
리터럴 상자에 로케일 코드를 입력하거나 로케일 코드를 포함하는 문자열 변수를 선택합니다. 지원되는 로케일 코드의 전체 목록은 https://docs.oracle.com/javase/1.5.0/docs/guide/intl/locale.doc.html 을 참조하십시오.

* **[!UICONTROL 복사본]**: 출력에 대해 생성할 복사본 수를 지정하는 정수 값입니다. 기본값은 1입니다.

* **[!UICONTROL 양면 인쇄]**: 양면 인쇄를 사용할지 또는 단면 인쇄를 사용할지 여부를 지정하는 페이지 매김 값입니다. PostScript 및 PCL을 지원하는 프린터는 이 값을 사용합니다. 리터럴 값을 제공하는 경우 다음 값 중 하나를 선택합니다.
   * **[!UICONTROL 양면 긴 Edge]**: 양면 인쇄 및 긴 쪽 페이지 매김 인쇄를 사용합니다.
   * **[!UICONTROL 양면 짧은 Edge]**: 양면 인쇄를 사용하고 짧은 쪽 페이지 매김 방식으로 인쇄하십시오.
   * **[!UICONTROL 단순]**: 단면 인쇄를 사용합니다.

## 비대화형 PDF 출력 단계 생성   {#generatePDFdocuments}

1. Sidekick의 Forms Workflow 탭 아래에 있는 비대화형 PDF 출력 생성 워크플로우를 드래그합니다.
1. 추가된 워크플로 단계를 두 번 클릭하여 구성 요소를 편집합니다.
1. 구성 요소 편집 대화 상자에서 입력 문서, 출력 문서 및 추가 매개 변수를 구성하고 **[!UICONTROL 확인]**&#x200B;을 클릭합니다.

### 입력 문서 {#input-documents-3}

* **템플릿 파일**: XDP 템플릿의 위치를 지정합니다. 필수 필드입니다.

* **데이터 문서**: 서식 파일과 병합해야 하는 데이터 xml의 위치를 지정합니다.

### 출력 문서 {#output-document}

**출력 문서**: 생성된 PDF 양식의 이름을 지정합니다.

### 추가 매개 변수 {#additional-parameters-1}

* **콘텐츠 루트**: 입력 XDP 템플릿에서 사용된 조각이나 이미지가 저장되는 저장소의 폴더에 대한 경로를 지정합니다.
* **로케일**: 생성된 PDF 양식의 기본 로케일을 지정합니다.
* **Acrobat 버전**: 생성된 PDF 양식의 대상 Acrobat 버전을 지정합니다.
* **선형화된 PDF**: 웹 보기용으로 생성된 PDF을 최적화할지 여부를 지정합니다.
* **태그가 지정된 PDF**: 생성된 PDF에 액세스할 수 있게 할지 여부를 지정합니다.
* **XCI 문서**: XCI 파일의 경로를 지정합니다.

## 추가 참조 {#see-also}

* [Forms 중심 AEM 워크플로의 변수](/help/forms/variable-in-aem-workflows.md)
* [부재 중 설정 구성](/help/forms/configure-out-of-office-settings.md)

<!--

>[!MORELIKETHIS]
>
>* [Forms-centric workflow on OSGi](/help/forms/aem-forms-workflow.md)
>* [Use AEM translation workflow to localize Adaptive Forms and Document of Record](/help/forms/using-aem-translation-workflow-to-localize-adaptive-forms.md)

-->