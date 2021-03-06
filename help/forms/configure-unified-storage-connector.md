---
title: AEM Forms용 통합 스토리지 커넥터를 구성하는 방법
description: AEM Forms용 통합 스토리지 커넥터를 관리하는 방법을 알아봅니다. 통합 스토리지 커넥터를 사용하여 AEM Forms을 외부 데이터 저장소에 연결합니다.
exl-id: c93d0242-0c15-4d69-82a1-d6fcc7da4bae
source-git-commit: 940a01cd3b9e4804bfab1a5970699271f624f087
workflow-type: tm+mt
source-wordcount: '604'
ht-degree: 0%

---

# AEM Forms용 통합 스토리지 커넥터 관리 {#manage-unified-storage-connector}

통합 스토리지 커넥터를 사용하여 AEM Forms을 외부 데이터 저장소에 연결할 수 있습니다.

예를 들어 적응형 양식의 필드 값을 채워 AEM Workflow에 제출할 수 있습니다. Microsoft Azure 저장소 서버와 같은 외부 저장소에 데이터를 저장하도록 AEM 워크플로우를 추가로 구성할 수 있습니다. 통합 스토리지 커넥터를 사용하여 AEM Workflows와 외부 스토리지 간의 연결을 만듭니다.

## Microsoft Azure 저장소 서버와 AEM 워크플로우 연결 {#connect-workflows-with-azure}

Azure 저장소 구성을 만들고 통합 저장소 커넥터를 사용하여 해당 구성을 참조하십시오. 그런 다음 AEM 워크플로우 모델을 구성하여 데이터 저장소를 외부화하여 Azure 저장소 서버에 연결할 수 있습니다.

### 만들기 [!DNL Azure] 저장소 구성 {#create-azure-storage-configuration}

이러한 단계를 실행하기 전에 [!DNL Azure] 스토리지 계정 및 액세스 키를 사용하여 [!DNL Azure] 저장소 계정.

다음 단계를 수행하여 을 생성합니다 [!DNL Azure] 저장소 구성:

1. 다음으로 이동 **[!UICONTROL 도구]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Azure 저장소]**.
1. 구성을 만들 폴더를 선택하고 탭합니다. **[!UICONTROL 만들기]**.
1. 에서 구성의 제목을 지정합니다 **[!UICONTROL 제목]** 필드.
1. 이름 지정 [!DNL Azure] 스토리지 계정 **[!UICONTROL Azure 저장소 계정]** 필드.
1. 키를 지정하여 **[!UICONTROL Azure 액세스 키]** 필드 및 탭 **[!UICONTROL 저장]**.

### AEM 워크플로우에 대한 통합 스토리지 커넥터 구성 {#configure-unified-storage-connector-workflows}

AEM Workflows용 Unified Storage Connector를 구성하려면 다음 단계를 수행하십시오.

1. 다음으로 이동 **[!UICONTROL 도구]** > **[!UICONTROL Forms]** > **[!UICONTROL 통합 스토리지 커넥터]**.

1. 에서 **[!UICONTROL 워크플로우]** 섹션, 선택 **[!UICONTROL Azure]** 저장 영역 드롭다운 목록에서
1. 을(를) 지정합니다. [Azure 저장소 구성에 대한 구성 경로](#create-azure-storage-configuration) 에서 **[!UICONTROL 스토리지 구성 경로]** 필드.
1. 탭 **[!UICONTROL 게시]** 그런 다음 **[!UICONTROL 저장]** 구성을 저장합니다.

### 외부 데이터 저장소에 대한 AEM 워크플로우 모델 구성 {#configure-workflow-external-data-storage}

외부 데이터 저장소에 대해 AEM 워크플로우 모델을 구성하려면 다음 단계를 수행하십시오.

1. 다음으로 이동 **[!UICONTROL 도구]** > **[!UICONTROL 워크플로우]** > **[!UICONTROL 모델]**.
1. 모델 이름을 선택하고 탭합니다 **[!UICONTROL 편집]**.
1. 페이지 정보 아이콘을 탭하고 탭합니다 **[!UICONTROL 속성 열기]**.
1. 선택 **[!UICONTROL 워크플로우 데이터 저장소 외부화]**.
1. 탭 **[!UICONTROL 저장 및 닫기]** 속성을 저장합니다.

>[!NOTE]
>
>외부 데이터 저장소에 대해 AEM 워크플로우 모델을 구성할 때 작업 할당 단계를 초안으로 저장하고 작업 할당 단계의 기록을 검색하는 옵션이 비활성화됩니다.

### 외부 데이터 저장소를 위한 AEM 워크플로우 지침 {#guidelines-workflows-external-data-storage}

AEM Workflows를 사용하고 Microsoft Azure 저장소 서버와 같은 외부 데이터 저장소에 데이터를 저장하는 경우 다음 지침이 제공됩니다.

* 워크플로우 모델 단계에서 입출력 데이터 파일과 첨부 파일을 정의하는 동안 변수를 사용하여 데이터를 저장합니다. 선택하지 않음 **[!UICONTROL 페이로드에 대한 상대]** 및 **[!UICONTROL 절대 경로에서 사용 가능]** 옵션. 다음 **[!UICONTROL 페이로드에 대한 상대]** 및 **[!UICONTROL 절대 경로에서 사용 가능]** 옵션이 자동으로 표시되지 않음 [외부 데이터 저장소에 대한 AEM 워크플로우 모델 구성](#configure-workflow-external-data-storage).

* 적응형 양식을 AEM Workflow에 제출하는 동안 변수를 사용하여 데이터 파일과 첨부 파일을 저장합니다. 선택하지 않음 **[!UICONTROL 페이로드에 대한 상대]** 적응형 양식을 AEM 워크플로우에 제출하는 동안 선택할 수 있습니다. 다음 **[!UICONTROL 페이로드에 대한 상대]** 옵션이 자동으로 표시되지 않음 [외부 데이터 저장소에 대한 AEM 워크플로우 모델 구성](#configure-workflow-external-data-storage).

* 워크플로우 모델에서 사용자 지정 AEM 워크플로우 단계를 사용하여 CRX DE 저장소에 데이터를 저장하지 마십시오.

* 다음 경우에 [외부 데이터 저장소에 대한 AEM 워크플로우 모델 구성](#configure-workflow-external-data-storage)AEM 받은 편지함의 작업 항목이 외부 저장소로 표시된 워크플로우에 속하는 경우 사용자 지정 열 값을 가져오지 않으므로 AEM 받은 편지함에 대한 사용자 지정 열을 만들지 마십시오.
