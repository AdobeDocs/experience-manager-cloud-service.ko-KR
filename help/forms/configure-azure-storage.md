---
title: Azure 스토리지를 구성하는 방법
description: 양식을 Azure 스토리지 서버와 통합하는 방법을 알아봅니다.
feature: Adaptive Forms, Form Data Model
role: User, Developer
exl-id: 606383b3-293c-43d2-9ba0-5843c4e0caa8
source-git-commit: 7b31a2ea016567979288c7a8e55ed5bf8dfc181d
workflow-type: tm+mt
source-wordcount: '591'
ht-degree: 1%

---

# [!DNL Azure] 저장소 구성 {#configure-azure-storage}


![데이터 통합](assets/data-integeration.png)

[[!DNL Experience Manager Forms] 데이터 통합](data-integration.md)은(는) 양식을 [!DNL Azure] 저장소 서비스와 통합하기 위한 [!DNL Azure] 저장소 구성을 제공합니다. 양식 데이터 모델(FDM)을 사용하여 [!DNL Azure] 서버와 상호 작용하여 비즈니스 워크플로를 가능하게 하는 적응형 Forms을 만들 수 있습니다. 예:

* 적응형 양식 제출 시 [!DNL Azure]에 데이터를 쓰십시오.
* FDM(양식 데이터 모델)에 정의된 사용자 지정 엔터티를 통해 [!DNL Azure]에 데이터를 쓰고, 반대로 작성합니다.
* [!DNL Azure] 서버에 데이터를 쿼리하고 적응형 Forms을 미리 채웁니다.
* [!DNL Azure] 서버에서 데이터를 읽습니다.

## [!DNL Azure] 저장소 구성 만들기 {#create-azure-storage-configuration}

이 단계를 실행하기 전에 [!DNL Azure] 저장소 계정과 [!DNL Azure] 저장소 계정에 대한 액세스를 승인할 액세스 키가 있는지 확인하십시오.

1. **[!UICONTROL 도구]** > **[!UICONTROL Cloud Service]** > **[!UICONTROL Azure 저장소]**&#x200B;로 이동합니다.
1. 구성을 만들 폴더를 선택하고 **[!UICONTROL 만들기]**&#x200B;를 선택합니다.
1. **[!UICONTROL 제목]** 필드에 구성의 제목을 지정합니다.
1. **[!UICONTROL Azure 저장소 계정]** 필드에 [!DNL Azure] 저장소 계정의 이름을 지정하십시오.
1. **[!UICONTROL Azure 액세스 키]** 필드에서 Azure 저장소 계정에 액세스할 키를 지정하고 **[!UICONTROL 저장]**&#x200B;을 선택합니다.

## 양식 데이터 모델 만들기 {#create-azure-form-data-model}

[!DNL Azure] 저장소 구성을 만든 후 [양식 데이터 모델을 만들 수 있습니다](create-form-data-models.md). FDM(양식 데이터 모델)을 만드는 동안 **[!UICONTROL 데이터 Source 구성]** 필드에 [!DNL Azure] 구성을 포함하는 폴더를 지정하십시오. 그런 다음 지정된 폴더 이름에 있는 구성 목록에서 구성을 선택할 수 있습니다.

### 양식 데이터 모델에 [!DNL Azure] 서비스 추가 {#add-azure-services}

양식 데이터 모델(FDM) 및 데이터 모델 개체를 만든 후 [!DNL Azure] 서비스를 양식 데이터 모델(FDM)에 추가할 수 있습니다.

[!DNL Azure] 서비스를 추가하려면:

1. 편집 모드에서 왼쪽 창의 **[!UICONTROL 서비스]** 섹션에서 서비스를 선택하고 **[!UICONTROL 선택한 항목 추가]**&#x200B;를 선택합니다. 선택한 서비스는 양식 데이터 모델(FDM)의 **[!UICONTROL 서비스]** 탭에 표시됩니다.

   ![선택한 서비스 추가](assets/select-services.png)

1. **[!UICONTROL 서비스]** 탭에서 서비스 및 **[!UICONTROL 속성 편집]**&#x200B;을 선택합니다. 서비스를 기반으로 서비스에 대한 입력 또는 출력 모델 개체를 정의합니다.

1. 양식 데이터 모델(FDM)을 저장하려면 **[!UICONTROL 저장]**&#x200B;을 선택합니다.

   다음 표에서는 사용 가능한 [!DNL Azure] 서비스에 대해 설명합니다.

   <table>
    <tbody>
     <tr>
      <th><strong>서비스 이름</strong></th>
      <th><strong>설명</strong></th>
     </tr>
     <tr>
      <td>Azure에서 Blob 가져오기</td>
      <td>ID 또는 이름을 사용하여 Azure 저장소에서 Blob으로 저장된 데이터를 검색합니다.</td>
     </tr>
     <tr>
      <td>Azure에서 바이너리 URL이 있는 Blob 가져오기</td>
      <td>ID 또는 이름을 사용하여 Azure 스토리지의 바이너리에 대한 URL이 있는 Blob로 저장된 데이터를 검색합니다.</td>
     </tr>
     <tr>
      <td>Azure에서 Blob 저장</td>
      <td>Blob ID를 사용하여 Azure 스토리지에 데이터 저장</td>
     </tr>
     <tr>
      <td>Azure에서 Blob 업데이트</td>
      <td>Blob ID를 사용하여 Azure 스토리지의 데이터를 업데이트합니다.</td>
     </tr>
     <tr>
      <td>Azure에서 Blob ID 목록 검색</td>
      <td>입력 요청에 정의된 숫자를 기반으로 Azure에서 Blob ID 목록을 검색합니다.</td>
     </tr>
     <tr>
      <td>Azure에서 Blob용 SAS URL 검색</td>
      <td>입력 요청의 Blob ID를 기반으로 Azure에서 Blob에 대한 SAS URL을 검색합니다.</td>
     </tr>
     <tr>
      <td>Azure에서 Blob 삭제</td>
      <td>Blob ID를 사용하여 Azure 저장소에서 데이터를 삭제합니다.</td>
     </tr>
    </tbody>
   </table>

### 데이터 모델 개체 속성을 검색 키로 정의 {#define-data-model-object-as-metadata}

데이터 모델 개체 속성을 검색 키로 정의하려면 다음을 수행합니다.

1. **[!UICONTROL 모델]** 탭에서 데이터 모델 개체 속성을 선택하고 **[!UICONTROL 속성 편집]**&#x200B;을 선택합니다.
1. **[!UICONTROL 검색 키]** 전환 옵션을 [켜짐] 상태로 전환합니다. 이 옵션은 기본 데이터 유형에만 사용할 수 있습니다.
1. **[!UICONTROL 완료]**&#x200B;를 선택한 다음 **[!UICONTROL 저장]**&#x200B;을 선택하여 FDM(양식 데이터 모델)을 저장합니다.

데이터 모델 개체 속성을 검색 키로 정의한 후 해시 값은 Azure 인덱스 태그에 저장되고 Base64 인코딩 값은 Azure 메타데이터에 저장됩니다.

>[!NOTE]
>
>Azure는 Blob당 10개의 태그만 허용하므로 Azure 엔터티당 10개의 검색 키만 허용되며 검색 키로 표시된 속성 값은 해싱 후 Azure 인덱스 태그에 저장됩니다.

<!--

>[!MORELIKETHIS]
>
>* [Configure data sources for AEM Forms](/help/forms/configure-data-sources.md)
>* [Integrate Microsoft Dynamics 365 and Salesforce with Adaptive Forms](/help/forms/configure-msdynamics-salesforce.md)
>  [Add Forms Portal to an AEM Sites page](/help/forms/configure-forms-portal.md)

-->