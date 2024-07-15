---
title: AEM Forms용 통합 스토리지 커넥터(USC)를 구성하는 방법
description: AEM Forms용 USC(Unified Storage Connector)를 관리하는 방법을 알아봅니다. USC(통합 스토리지 커넥터)를 사용하여 AEM Forms을 외부 데이터 스토리지에 연결합니다.
role: Admin, Developer, User
feature: Adaptive Forms, Workflow
exl-id: c93d0242-0c15-4d69-82a1-d6fcc7da4bae
source-git-commit: 527c9944929c28a0ef7f3e617ef6185bfed0d536
workflow-type: tm+mt
source-wordcount: '642'
ht-degree: 0%

---

# AEM Forms용 USC(Unified Storage Connector) 관리 {#manage-unified-storage-connector}

USC(통합 스토리지 커넥터)를 사용하여 AEM Forms을 외부 데이터 스토리지에 연결할 수 있습니다.

예를 들어 적응형 양식의 필드 값을 채워 AEM Workflow에 제출할 수 있습니다. 또한 Microsoft Azure 스토리지 서버와 같은 외부 스토리지에 데이터를 저장하도록 AEM Workflow를 구성할 수 있습니다. USC(통합 스토리지 커넥터)를 사용하여 AEM 워크플로우와 외부 스토리지 간에 연결을 만듭니다.

## Microsoft Azure 스토리지 서버와 AEM 워크플로 연결 {#connect-workflows-with-azure}

Azure 스토리지 구성을 만들고 USC(통합 스토리지 커넥터)를 사용하여 해당 구성을 참조합니다. 그런 다음 AEM Workflow 모델을 구성하여 데이터 저장소를 외부화하여 Azure 스토리지 서버에 연결할 수 있습니다.

### [!DNL Azure] 저장소 구성 만들기 {#create-azure-storage-configuration}

이 단계를 실행하기 전에 [!DNL Azure] 저장소 계정과 [!DNL Azure] 저장소 계정에 대한 액세스를 승인할 액세스 키가 있는지 확인하십시오.

[!DNL Azure] 저장소 구성을 만들려면 다음 단계를 수행하십시오.

1. **[!UICONTROL 도구]** > **[!UICONTROL Cloud Service]** > **[!UICONTROL Azure 저장소]**&#x200B;로 이동합니다.
1. 구성을 만들 폴더를 선택하고 **[!UICONTROL 만들기]**&#x200B;를 선택합니다.
1. **[!UICONTROL 제목]** 필드에 구성의 제목을 지정합니다.
1. **[!UICONTROL Azure 저장소 계정]** 필드에 [!DNL Azure] 저장소 계정의 이름을 지정하십시오.
1. **[!UICONTROL Azure 액세스 키]** 필드에서 Azure 저장소 계정에 액세스할 키를 지정하고 **[!UICONTROL 저장]**&#x200B;을 선택합니다.

### AEM 워크플로우용 통합 스토리지 커넥터(USC) 구성 {#configure-unified-storage-connector-workflows}

AEM Workflow용 통합 스토리지 커넥터(USC)를 구성하려면 다음 단계를 수행하십시오.

1. **[!UICONTROL 도구]** > **[!UICONTROL Forms]** > **[!UICONTROL 통합 저장소 커넥터]**&#x200B;로 이동합니다.

1. **[!UICONTROL 워크플로]** 섹션의 저장소 드롭다운 목록에서 **[!UICONTROL Azure]**&#x200B;을(를) 선택합니다.
1. **[!UICONTROL 저장소 구성 경로]** 필드에 Azure 저장소 구성에 대한 [구성 경로](#create-azure-storage-configuration)를 지정하십시오.
1. **[!UICONTROL Publish]**&#x200B;을(를) 선택한 다음 **[!UICONTROL 저장]**&#x200B;을(를) 선택하여 구성을 저장합니다.

### 외부 데이터 스토리지에 대한 AEM Workflow 모델 구성 {#configure-workflow-external-data-storage}

외부 데이터 스토리지에 대한 AEM Workflow 모델을 구성하려면 다음 단계를 수행합니다.

1. **[!UICONTROL 도구]** > **[!UICONTROL 워크플로]** > **[!UICONTROL 모델]**(으)로 이동합니다.
1. 모델 이름을 선택하고 **[!UICONTROL 편집]**&#x200B;을 선택하세요.
1. 페이지 정보 아이콘을 선택하고 **[!UICONTROL 속성 열기]**&#x200B;를 선택합니다.
1. **[!UICONTROL 워크플로 데이터 저장소 외부화]**&#x200B;을(를) 선택하십시오.
1. 속성을 저장하려면 **[!UICONTROL 저장 및 닫기]**&#x200B;를 선택하십시오.

>[!NOTE]
>
>외부 데이터 저장소에 대한 AEM 워크플로 모델을 구성할 때 작업 할당 단계를 초안으로 저장하고 작업 할당 단계의 기록을 검색하는 옵션이 비활성화됩니다.

### 외부 데이터 저장을 위한 AEM 워크플로 지침 {#guidelines-workflows-external-data-storage}

다음은 AEM Workflow를 사용하고 데이터를 Microsoft Azure 스토리지 서버와 같은 외부 데이터 스토리지에 저장하는 경우의 지침입니다.

* 워크플로우 모델 단계에서 입력 및 출력 데이터 파일과 첨부 파일을 정의하는 동안 변수를 사용하여 데이터를 저장합니다. **[!UICONTROL 페이로드 관련]** 및 **[!UICONTROL 절대 경로에서 사용 가능]** 옵션을 선택하지 마십시오. [외부 데이터 저장소에 대한 AEM Workflow 모델을 구성](#configure-workflow-external-data-storage)한 후에는 **[!UICONTROL 페이로드에 따라]** 및 **[!UICONTROL 절대 경로에서 사용 가능]** 옵션이 자동으로 표시되지 않습니다.

* 적응형 양식을 AEM Workflow에 제출하는 동안 변수를 사용하여 데이터 파일 및 첨부 파일을 저장합니다. 적응형 양식을 AEM Workflow에 제출하는 동안 **[!UICONTROL 페이로드 관련]** 옵션을 선택하지 마십시오. [외부 데이터 저장소에 대한 AEM Workflow 모델을 구성](#configure-workflow-external-data-storage)한 후에는 **[!UICONTROL 페이로드에 상대적인]** 옵션이 자동으로 표시되지 않습니다.

* 워크플로우 모델에서 사용자 지정 AEM Workflow 단계를 사용하여 CRX DE 저장소에 데이터를 저장하지 마십시오.

* [외부 데이터 저장소에 대한 AEM Workflow 모델을 구성할 때](#configure-workflow-external-data-storage), AEM Inbox의 작업 항목이 외부 스토리지로 표시된 워크플로에 속하는 경우 사용자 지정 열의 값을 가져오지 않으므로 AEM Inbox에 대한 사용자 지정 열을 만들지 마십시오.

>[!MORELIKETHIS]
>
>* [AEM Forms에 대한 데이터 소스 구성](/help/forms/configure-data-sources.md)
>* [AEM Forms에 대한 Azure 저장소 구성](/help/forms/configure-azure-storage.md)
>* [Microsoft Dynamics 365와 Salesforce를 적응형 Forms과 통합](/help/forms/configure-msdynamics-salesforce.md)
>  [AEM Sites 페이지에 Forms 포털 추가](/help/forms/configure-forms-portal.md)
