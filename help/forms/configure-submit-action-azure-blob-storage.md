---
Title: How to connect AEM Adaptive Forms with Azure Blob Storage?
Description: Learn how to create an Azure Blob Storage Configuration in AEM Forms and use it within your Adaptive Forms for efficient data storage.
keywords: Azure Blob Storage와 AEM Forms 통합, Azure Storage에 데이터 제출, AEM Forms에서 Azure 스토리지 구성 만들기, 적응형 Forms 제출 작업에서 Azure Blob 스토리지 사용
feature: Adaptive Forms, Core Components
source-git-commit: 8784c0bcd05eeae41a472faa5ecad03cbdd8a9b6
workflow-type: tm+mt
source-wordcount: '451'
ht-degree: 66%

---


# Azure Blob 스토리지에 적응형 양식 제출

**[!UICONTROL Azure Blob Storage에 제출]** 제출 액션은 적응형 양식을 Microsoft® Azure 포털과 연결합니다. 양식 데이터, 파일, 첨부 파일 또는 기록 문서를 연결된 Azure Storage 컨테이너에 제출할 수 있습니다.

AEM as a Cloud Service에서는 양식 제출을 처리하기 위한 다양한 제출 액션을 제공합니다. 다음에서 이러한 옵션에 대해 자세히 알아볼 수 있습니다. [적응형 양식 제출 액션](/help/forms/configure-submit-actions-core-components.md) 기사.

## 장점

AEM Forms과 Azure Blob Storage를 통합하면 다음과 같은 이점이 있습니다.

* 적응형 양식 데이터, 파일, 첨부 파일 및 기록 문서를 Azure Storage 컨테이너에 제출하는 프로세스를 간소화하는 데 도움이 됩니다.
* Azure Blob Storage를 사용하여 적응형 양식 제출을 중앙 집중식으로 구성하고 저장합니다.

## AEM Forms과 Microsoft® Azure Blob 스토리지 연결

적응형 Forms 제출 액션에서 Azure Blob 저장소를 사용하려면:

1. [Azure Blob Storage 컨테이너 만들기](#create-a-azure-blob-storage-container-create-azure-configuration): AEM Forms를 Azure Storage 컨테이너에 연결합니다.
2. [적응형 양식에서 Azure Storage 구성 사용](#use-azure-storage-configuration-in-an-adaptive-form-use-azure-storage-configuartion-in-af): Adaptive Form을 구성된 Azure Storage 컨테이너에 연결합니다.

### Azure Blob Storage 컨테이너 만들기 {#create-azure-configuration}

AEM Forms를 Azure Storage 컨테이너에 연결하려면
1. **AEM Forms 작성자** 인스턴스 > **[!UICONTROL 도구]** > **[!UICONTROL 클라우드 서비스]** > **[!UICONTROL Azure Storage]**&#x200B;로 이동합니다.
1. **[!UICONTROL Azure Storage]**&#x200B;를 선택하면 **[!UICONTROL Azure Storage 브라우저]**&#x200B;로 리디렉션됩니다.
1. **구성 컨테이너**&#x200B;를 선택합니다. 선택한 구성 컨테이너에 구성을 저장합니다.
1. **[!UICONTROL 만들기]**&#x200B;를 클릭합니다. Azure Storage 구성 만들기 마법사가 나타납니다.

   ![Azure Storage 구성](/help/forms/assets/azure-storage-configuration.png)

1. **[!UICONTROL 제목]**, **[!UICONTROL Azure Storage 계정]** 및 **[!UICONTROL Azure 액세스 키]**&#x200B;를 지정합니다.

   * Microsoft® Azure 포털의 스토리지 계정에서 `Azure Storage Account` 이름과 `Azure Access key`를 검색할 수 있습니다.

1. **[!UICONTROL 저장]**&#x200B;을 클릭합니다.

이제 적응형 양식에서 제출 액션에 대한 Azure Storage 컨테이너 구성을 사용할 수 있습니다.

### 적응형 양식에서 Azure Storage 구성 사용 {#use-azure-storage-configuartion-in-af}

적응형 양식에서 만든 Azure Storage 컨테이너 구성을 사용하여 데이터 또는 생성된 기록 문서를 Azure Storage 컨테이너에 저장할 수 있습니다. 적응형 양식에서 Azure Storage 컨테이너 구성을 다음과 같이 사용하려면 다음 단계를 수행하십시오.
1. [적응형 양식](/help/forms/creating-adaptive-form-core-components.md)을 만듭니다.

   >[!NOTE]
   >
   > * OneDrive 스토리지가 생성되면 적응형 양식에 대한 [!UICONTROL 구성 컨테이너]를 선택합니다.
   > * [!UICONTROL 구성 컨테이너]가 선택되지 않은 경우 제출 액션 속성 창에 글로벌 [!UICONTROL 스토리지 구성] 폴더가 나타납니다.

1. **제출 액션**&#x200B;을 **[!UICONTROL Azure Blob Storage에 제출]**로 선택합니다.
   ![Azure Blob Storage GIF](/help/forms/assets/azure-submit-video.gif)

1. 데이터를 저장하려는 경우 **[!UICONTROL 스토리지 구성]**&#x200B;을 선택합니다.
1. **[!UICONTROL 저장]**&#x200B;을 클릭하여 제출 설정을 저장합니다.

양식이 제출되면 지정된 Azure Storage 컨테이너 구성에 데이터가 저장됩니다.
데이터를 저장하는 폴더 구조는 `/configuration_container/form_name/year/month/date/submission_id/data`입니다.

## 관련 문서

{{af-submit-action}}