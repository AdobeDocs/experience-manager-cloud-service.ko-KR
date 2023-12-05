---
title: Azure 스토리지를 구성하는 방법
description: 양식을 Azure 스토리지 서버와 통합하는 방법을 알아봅니다.
exl-id: 606383b3-293c-43d2-9ba0-5843c4e0caa8
source-git-commit: 2d4ffd5518d671a55e45a1ab6f1fc41ac021fd80
workflow-type: tm+mt
source-wordcount: '583'
ht-degree: 1%

---

# 구성 [!DNL Azure] 스토리지 {#configure-azure-storage}


![데이터 통합](assets/data-integeration.png)

[[!DNL Experience Manager Forms] 데이터 통합](data-integration.md) 는 을(를) 제공합니다 [!DNL Azure] 양식을 와 통합하기 위한 스토리지 구성 [!DNL Azure] 스토리지 서비스. 양식 데이터 모델을 사용하여 와 상호 작용하는 적응형 Forms을 만들 수 있습니다 [!DNL Azure] 비즈니스 워크플로를 활성화하는 서버입니다. 예:

* 에 데이터 쓰기 [!DNL Azure] 을 참조하십시오.
* 데이터 쓰기 [!DNL Azure] 를 통해 양식 데이터 모델에 정의된 사용자 지정 엔티티 및 그 반대로
* 쿼리 [!DNL Azure] 서버입니다. 또한 적응형 Forms을 미리 채웁니다.
* 데이터 읽기 [!DNL Azure] 서버입니다.

## 만들기 [!DNL Azure] 스토리지 구성 {#create-azure-storage-configuration}

이러한 단계를 실행하기 전에 [!DNL Azure] 저장소 계정 및 액세스 권한 부여 액세스 키 [!DNL Azure] 저장소 계정입니다.

1. 다음으로 이동 **[!UICONTROL 도구]** > **[!UICONTROL Cloud Service]** > **[!UICONTROL Azure 스토리지]**.
1. 구성을 생성할 폴더를 선택하고 **[!UICONTROL 만들기]**.
1. 에서 구성의 제목을 지정합니다. **[!UICONTROL 제목]** 필드.
1. 의 이름을 지정합니다. [!DNL Azure] 의 저장소 계정 **[!UICONTROL Azure 스토리지 계정]** 필드.
1. 에서 Azure 스토리지 계정에 액세스할 키를 지정합니다. **[!UICONTROL Azure 액세스 키]** 필드 및 선택 **[!UICONTROL 저장]**.

## 양식 데이터 모델 만들기 {#create-azure-form-data-model}

를 만든 후 [!DNL Azure] 스토리지 구성, 다음과 같은 작업을 수행할 수 있습니다. [양식 데이터 모델 만들기](create-form-data-models.md). 다음 항목이 포함된 폴더 지정 [!DNL Azure] 에서 구성 **[!UICONTROL 데이터 소스 구성]** 양식 데이터 모델을 만드는 동안 필드가 채워집니다. 그런 다음 지정된 폴더 이름에 있는 구성 목록에서 구성을 선택할 수 있습니다.

### 추가 [!DNL Azure] 양식 데이터 모델에 대한 서비스 {#add-azure-services}

양식 데이터 모델 및 데이터 모델 개체를 만든 후 [!DNL Azure] 서비스를 양식 데이터 모델에 추가합니다.

추가하려면 [!DNL Azure] 서비스:

1. 편집 모드에서 **[!UICONTROL 서비스]** 왼쪽 창에서 섹션을 선택하고 **[!UICONTROL 선택 항목 추가]**. 선택한 서비스가 **[!UICONTROL 서비스]** 양식 데이터 모델 탭

   ![선택한 서비스 추가](assets/select-services.png)

1. 다음에서 **[!UICONTROL 서비스]** 탭에서 서비스를 선택하고 **[!UICONTROL 속성 편집]**. 서비스를 기반으로 서비스에 대한 입력 또는 출력 모델 개체를 정의합니다.

1. 선택 **[!UICONTROL 저장]** 을 클릭하여 양식 데이터 모델을 저장합니다.

   다음 표에서는 사용 가능한 [!DNL Azure] 서비스:

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

1. 다음에서 **[!UICONTROL 모델]** 탭에서 데이터 모델 개체 속성을 선택하고 **[!UICONTROL 속성 편집]**.
1. 전환 **[!UICONTROL 검색 키]** 옵션을 켜짐 상태로 전환합니다. 이 옵션은 기본 데이터 유형에만 사용할 수 있습니다.
1. 선택 **[!UICONTROL 완료]** 다음을 선택합니다. **[!UICONTROL 저장]** 을 클릭하여 양식 데이터 모델을 저장합니다.

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