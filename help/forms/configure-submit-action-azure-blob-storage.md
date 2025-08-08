---
description: AEM Forms에서 Azure Blob 스토리지 구성을 만들고 이를 적응형 Forms 내에서 사용하여 효율적인 데이터 스토리지를 사용하는 방법에 대해 알아봅니다.
keywords: Azure Blob Storage와 AEM Forms 통합, Azure Storage에 데이터 제출, AEM Forms에서 Azure 스토리지 구성 만들기, 적응형 Forms 제출 작업에서 Azure Blob 스토리지 사용
feature: Adaptive Forms, Foundation Components, Edge Delivery Services, Core Components
exl-id: 0c9f8f85-c4e9-4c79-bd0b-abdcac99a2d4
title: 적응형 양식에 대한 제출 액션을 구성하는 방법
role: User, Developer
source-git-commit: 1be7bafc1d93a65a81eeb2f7e86cac33cde7aa35
workflow-type: tm+mt
source-wordcount: '828'
ht-degree: 44%

---

# Azure Blob Storage에 적응형 양식 제출

**[!UICONTROL Azure Blob Storage에 제출]** 제출 액션은 적응형 양식을 Microsoft® Azure 포털과 연결합니다. 양식 데이터, 파일, 첨부 파일 또는 기록 문서를 연결된 Azure Storage 컨테이너에 제출할 수 있습니다.

AEM as a Cloud Service에서는 양식 제출을 처리하기 위한 다양한 제출 액션을 제공합니다. [적응형 양식 제출 액션](/help/forms/aem-forms-submit-action.md) 문서에서 이러한 옵션에 대해 자세히 알아볼 수 있습니다.

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
<!--

    >[!NOTE]
    >
    > The URL for **[!UICONTROL Azure Blob Endpoint]** is automatically appended to the textbox when a value is entered for **[!UICONTROL Azure Storage Account]**. You can update the Azure Blob End Point URL with your custom domain. Steps to update URL for **[!UICONTROL Azure Blob End Point]**:
    > 1. [Enable the AEM Advance Networking VPN support](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/networking/advanced-networking.html?lang=ko)
    > 1. [Enable dedicated egress IP link](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/networking/advanced-networking.html?lang=ko)
    > 1. [Map custom domain to azure blob storage](https://learn.microsoft.com/en-us/azure/storage/blobs/storage-custom-domain-name?tabs=azure-portal)
-->

1. **[!UICONTROL 저장]**&#x200B;을 클릭합니다.

이제 적응형 양식에서 제출 액션에 대한 Azure Storage 컨테이너 구성을 사용할 수 있습니다.

### 적응형 양식에서 Azure Storage 구성 사용 {#use-azure-storage-configuartion-in-af}

적응형 양식에서 생성된 Azure 스토리지 컨테이너 구성을 사용하여 Azure 스토리지 컨테이너에 데이터 또는 생성된 기록 문서를 저장할 수 있습니다.

>[!NOTE]
>
> * OneDrive 스토리지가 생성되면 적응형 양식에 대한 [!UICONTROL 구성 컨테이너]를 선택합니다.
> * [!UICONTROL 구성 컨테이너]가 선택되지 않은 경우 제출 액션 속성 창에 글로벌 [!UICONTROL 스토리지 구성] 폴더가 나타납니다.

>[!BEGINTABS]

>[!TAB 기초 구성 요소]

기초 구성 요소를 기반으로 하는 적응형 양식에서 Azure 스토리지 컨테이너 구성을 사용하려면 다음 단계를 수행하십시오.

1. 편집할 적응형 양식을 열고 적응형 양식 컨테이너 속성의 **[!UICONTROL 제출]** 섹션으로 이동합니다.
1. **[!UICONTROL 작업 제출]** 드롭다운 목록에서 **[!UICONTROL Azure Blob 저장소에 제출]**&#x200B;을 선택합니다.

   ![Azure Blob 저장소 GIF](/help/forms/assets/submit-to-azure-blob-fc.png){width=50%,height=50%}

   Azure Blob Storage에 기록 문서(DoR)를 저장할 수도 있습니다.

1. 데이터를 저장하려는 경우 **[!UICONTROL 스토리지 구성]**&#x200B;을 선택합니다.
1. **[!UICONTROL 저장]**&#x200B;을 클릭하여 제출 설정을 저장합니다.

양식이 제출되면 지정된 Azure Storage 컨테이너 구성에 데이터가 저장됩니다.
데이터를 저장하는 폴더 구조는 `/configuration_container/form_name/year/month/date/submission_id/data`입니다.

>[!TAB 핵심 구성 요소]

다음 단계를 수행하여 핵심 구성 요소를 기반으로 하는 적응형 양식에서 Azure 스토리지 컨테이너 구성을 사용합니다.

1. 콘텐츠 브라우저를 열고 적응형 양식의 **[!UICONTROL 안내서 컨테이너]** 구성 요소를 선택합니다.
1. 안내서 컨테이너 속성 ![안내서 속성](/help/forms/assets/configure-icon.svg) 아이콘을 클릭합니다. 적응형 양식 컨테이너 대화 상자가 열립니다.
1. **[!UICONTROL 제출]** 탭을 클릭합니다.
1. **[!UICONTROL 작업 제출]** 드롭다운 목록에서 **[!UICONTROL Azure Blob 저장소에 제출]**&#x200B;을 선택합니다.

   ![Azure Blob Storage GIF](/help/forms/assets/azure-submit-video.gif)

   Azure Blob Storage에 기록 문서(DoR)를 저장할 수도 있습니다.

1. 데이터를 저장하려는 경우 **[!UICONTROL 스토리지 구성]**&#x200B;을 선택합니다.
1. **[!UICONTROL 저장]**&#x200B;을 클릭하여 제출 설정을 저장합니다.

양식이 제출되면 지정된 Azure Storage 컨테이너 구성에 데이터가 저장됩니다.
데이터를 저장하는 폴더 구조는 `/configuration_container/form_name/year/month/date/submission_id/data`입니다.

>[!TAB 범용 편집기]

범용 편집기에서 작성된 적응형 양식에서 Azure 저장소 컨테이너 구성을 사용하려면 다음 단계를 수행하십시오.

1. 편집할 적응형 양식을 엽니다.
1. 편집기에서 **양식 속성 편집** 확장을 클릭합니다.
**양식 속성** 대화 상자가 나타납니다.

   >[!NOTE]
   >
   > * 범용 편집기 인터페이스에 **양식 속성 편집** 아이콘이 보이지 않는 경우 Extension Manager에서 **양식 속성 편집** 확장을 사용하도록 설정하십시오.
   > * 범용 편집기에서 확장을 활성화하거나 비활성화하는 방법에 대해 알아보려면 [Extension Manager 기능 하이라이트](https://developer.adobe.com/uix/docs/extension-manager/feature-highlights/#enablingdisabling-extensions) 문서를 참조하십시오.

1. **제출** 탭을 클릭하고 **[!UICONTROL Azure Blob 저장소에 제출]** 제출 액션을 선택합니다.
   ![Azure Blob 저장소](/help/forms/assets/azure-blob-storage-ue.png)

   **원래 이름으로 첨부 파일 저장**&#x200B;을 선택하면 첨부 파일은 원래 파일 이름을 사용하여 폴더에 저장됩니다. Azure Blob Storage에 기록 문서(DoR)를 저장할 수도 있습니다.

1. 데이터를 저장하려는 경우 **[!UICONTROL 스토리지 구성]**&#x200B;을 선택합니다.
1. 제출 설정을 저장하려면 **[!UICONTROL 저장 및 닫기]**&#x200B;를 클릭합니다.

양식이 제출되면 지정된 Azure Storage 컨테이너 구성에 데이터가 저장됩니다.
데이터를 저장하는 폴더 구조는 `/configuration_container/form_name/year/month/date/submission_id/data`입니다.

>[!ENDTABS]

## 관련 문서

{{af-submit-action}}
