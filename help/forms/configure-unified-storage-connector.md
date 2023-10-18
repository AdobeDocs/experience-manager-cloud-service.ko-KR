---
title: AEM Forms용 통합 스토리지 커넥터를 구성하는 방법
description: AEM Forms용 통합 스토리지 커넥터를 관리하는 방법을 알아봅니다. 통합 스토리지 커넥터를 사용하여 AEM Forms을 외부 데이터 스토리지에 연결합니다.
exl-id: c93d0242-0c15-4d69-82a1-d6fcc7da4bae
source-git-commit: 0f8aed76af4d2640094a76f2805f73a0a619e33f
workflow-type: tm+mt
source-wordcount: '632'
ht-degree: 0%

---

# AEM Forms용 통합 스토리지 커넥터 관리 {#manage-unified-storage-connector}

통합 스토리지 커넥터 를 사용하여 AEM Forms을 외부 데이터 스토리지에 연결할 수 있습니다.

예를 들어 적응형 양식의 필드 값을 채워 AEM Workflow에 제출할 수 있습니다. 또한 Microsoft Azure 스토리지 서버와 같은 외부 스토리지에 데이터를 저장하도록 AEM Workflow를 구성할 수 있습니다. 통합 스토리지 커넥터를 사용하여 AEM 워크플로우와 외부 스토리지 간의 연결을 만듭니다.

## Microsoft Azure 스토리지 서버와 AEM 워크플로 연결 {#connect-workflows-with-azure}

Azure 스토리지 구성을 만들고 통합 스토리지 커넥터를 사용하여 해당 구성을 참조합니다. 그런 다음 AEM Workflow 모델을 구성하여 데이터 저장소를 외부화하여 Azure 스토리지 서버에 연결할 수 있습니다.

### 만들기 [!DNL Azure] 스토리지 구성 {#create-azure-storage-configuration}

이러한 단계를 실행하기 전에 [!DNL Azure] 저장소 계정 및 액세스 권한 부여 액세스 키 [!DNL Azure] 저장소 계정입니다.

다음 단계를 수행하여 [!DNL Azure] 스토리지 구성:

1. 다음으로 이동 **[!UICONTROL 도구]** > **[!UICONTROL Cloud Service]** > **[!UICONTROL Azure 스토리지]**.
1. 구성을 만들 폴더를 선택하고 을 누릅니다 **[!UICONTROL 만들기]**.
1. 에서 구성의 제목을 지정합니다. **[!UICONTROL 제목]** 필드.
1. 의 이름을 지정합니다. [!DNL Azure] 의 저장소 계정 **[!UICONTROL Azure 스토리지 계정]** 필드.
1. 에서 Azure 스토리지 계정에 액세스할 키를 지정합니다. **[!UICONTROL Azure 액세스 키]** 필드 및 탭 **[!UICONTROL 저장]**.

### AEM 워크플로우용 통합 스토리지 커넥터 구성 {#configure-unified-storage-connector-workflows}

AEM Workflow용 통합 스토리지 커넥터를 구성하려면 다음 단계를 수행하십시오.

1. 다음으로 이동 **[!UICONTROL 도구]** > **[!UICONTROL Forms]** > **[!UICONTROL 통합 스토리지 커넥터]**.

1. 다음에서 **[!UICONTROL 워크플로]** 섹션, 선택 **[!UICONTROL Azure]** 스토리지 드롭다운 목록에서 선택하십시오.
1. 다음을 지정합니다. [azure 스토리지 구성에 대한 구성 경로](#create-azure-storage-configuration) 다음에서 **[!UICONTROL 스토리지 구성 경로]** 필드.
1. 누르기 **[!UICONTROL 게시]** 그런 다음 을 누릅니다 **[!UICONTROL 저장]** 구성을 저장합니다.

### 외부 데이터 스토리지에 대한 AEM Workflow 모델 구성 {#configure-workflow-external-data-storage}

외부 데이터 스토리지에 대한 AEM Workflow 모델을 구성하려면 다음 단계를 수행합니다.

1. 다음으로 이동 **[!UICONTROL 도구]** > **[!UICONTROL 워크플로]** > **[!UICONTROL 모델]**.
1. 모델 이름을 선택하고 을 누릅니다 **[!UICONTROL 편집]**.
1. 페이지 정보 아이콘을 탭하고 을 누릅니다 **[!UICONTROL 속성 열기]**.
1. 선택 **[!UICONTROL 워크플로 데이터 스토리지 외부화]**.
1. 누르기 **[!UICONTROL 저장 및 닫기]** 속성을 저장합니다.

>[!NOTE]
>
>외부 데이터 저장소에 대한 AEM 워크플로 모델을 구성할 때 작업 할당 단계를 초안으로 저장하고 작업 할당 단계의 기록을 검색하는 옵션이 비활성화됩니다.

### 외부 데이터 저장을 위한 AEM 워크플로 지침 {#guidelines-workflows-external-data-storage}

다음은 AEM Workflow를 사용하고 데이터를 Microsoft Azure 스토리지 서버와 같은 외부 데이터 스토리지에 저장하는 경우의 지침입니다.

* 워크플로우 모델 단계에서 입력 및 출력 데이터 파일과 첨부 파일을 정의하는 동안 변수를 사용하여 데이터를 저장합니다. 선택 안 함 **[!UICONTROL 페이로드 관련]** 및 **[!UICONTROL 절대 경로에서 사용 가능]** 옵션. 다음 **[!UICONTROL 페이로드 관련]** 및 **[!UICONTROL 절대 경로에서 사용 가능]** 옵션을 선택하면 옵션이 자동으로 표시되지 않습니다. [외부 데이터 스토리지에 대한 AEM Workflow 모델 구성](#configure-workflow-external-data-storage).

* 적응형 양식을 AEM Workflow에 제출하는 동안 변수를 사용하여 데이터 파일 및 첨부 파일을 저장합니다. 선택 안 함 **[!UICONTROL 페이로드 관련]** 적응형 양식을 AEM Workflow에 제출하는 중 옵션입니다. 다음 **[!UICONTROL 페이로드 관련]** 옵션을 선택하면 옵션이 자동으로 표시되지 않음 [외부 데이터 스토리지에 대한 AEM Workflow 모델 구성](#configure-workflow-external-data-storage).

* 워크플로 모델에서 사용자 지정 AEM 워크플로 단계를 사용하여 CRX DE 저장소에 데이터를 저장하지 마십시오.

* 다음을 수행하는 경우 [외부 데이터 스토리지에 대한 AEM Workflow 모델 구성](#configure-workflow-external-data-storage)AEM 받은 편지함의 작업 항목이 외부 스토리지로 표시된 워크플로에 속하는 경우 사용자 지정 열의 값을 가져오지 않으므로 AEM 받은 편지함에 대한 사용자 지정 열을 만들지 마십시오.

>[!MORELIKETHIS]
>
>* [AEM Forms에 대한 데이터 소스 구성](/help/forms/configure-data-sources.md)
>* [AEM Forms용 Azure 스토리지 구성](/help/forms/configure-azure-storage.md)
>* [Microsoft Dynamics 365 및 Salesforce를 적응형 Forms과 통합](/help/forms/configure-msdynamics-salesforce.md)
>  [AEM Sites 페이지에 Forms 포털 추가](/help/forms/configure-forms-portal.md)
