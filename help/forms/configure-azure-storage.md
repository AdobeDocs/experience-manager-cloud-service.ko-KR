---
title: Azure 스토리지를 구성하는 방법
description: 양식을 Azure 저장소 서버와 통합하는 방법을 알아봅니다.
exl-id: 606383b3-293c-43d2-9ba0-5843c4e0caa8
source-git-commit: 10284b1ac6fbad2e7f6231603c3dd60b6e404299
workflow-type: tm+mt
source-wordcount: '581'
ht-degree: 1%

---

# [!DNL Azure]스토리지 구성 {#configure-azure-storage}

[[!DNL Experience Manager Forms] 데이터 통합](data-integration.md) 제공 [!DNL Azure] 양식을 와 통합하기 위한 스토리지 구성 [!DNL Azure] 스토리지 서비스. 양식 데이터 모델 을 사용하여 와 상호 작용하는 적응형 Forms을 만들 수 있습니다 [!DNL Azure] 비즈니스 워크플로우를 사용하도록 설정하는 서버입니다. 예:

* 에 데이터 쓰기 [!DNL Azure] 적응형 양식 제출에서 참조할 수 있습니다.
* 데이터 쓰기 위치 [!DNL Azure] 양식 데이터 모델에 정의된 사용자 지정 엔티티를 통해 또는 그 반대의 경우도 마찬가지입니다.
* 쿼리 [!DNL Azure] 데이터를 위한 서버 및 적응형 Forms 미리 채우기.
* 데이터 읽기 [!DNL Azure] server.

## 만들기 [!DNL Azure] 저장소 구성 {#create-azure-storage-configuration}

이러한 단계를 실행하기 전에 [!DNL Azure] 스토리지 계정 및 액세스 키를 사용하여 [!DNL Azure] 저장소 계정.

1. 다음으로 이동 **[!UICONTROL 도구]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Azure 저장소]**.
1. 구성을 만들 폴더를 선택하고 탭합니다. **[!UICONTROL 만들기]**.
1. 에서 구성의 제목을 지정합니다 **[!UICONTROL 제목]** 필드.
1. 이름 지정 [!DNL Azure] 스토리지 계정 **[!UICONTROL Azure 저장소 계정]** 필드.
1. 키를 지정하여 **[!UICONTROL Azure 액세스 키]** 필드 및 탭 **[!UICONTROL 저장]**.

## 양식 데이터 모델 만들기 {#create-azure-form-data-model}

만들기 후 [!DNL Azure] 스토리지 구성, [양식 데이터 모델 만들기](create-form-data-models.md). 이 포함된 폴더를 지정합니다 [!DNL Azure] 의 구성 **[!UICONTROL 데이터 소스 구성]** 필드를 만듭니다. 그런 다음 지정된 폴더 이름에 있는 구성 목록에서 구성을 선택할 수 있습니다.

### 추가 [!DNL Azure] 양식 데이터 모델에 대한 서비스 {#add-azure-services}

양식 데이터 모델 및 데이터 모델 개체를 만든 후 다음을 추가할 수 있습니다 [!DNL Azure] 을 추가합니다.

추가하려면 [!DNL Azure] 서비스:

1. 편집 모드에서 **[!UICONTROL 서비스]** 왼쪽 창의 섹션을 탭하고 **[!UICONTROL 선택 항목 추가]**. 선택한 서비스가 **[!UICONTROL 서비스]** 탭을 클릭합니다.

   ![선택한 서비스 추가](assets/select-services.png)

1. 에서 **[!UICONTROL 서비스]** 탭에서 서비스를 선택하고 **[!UICONTROL 속성 편집]**. 서비스를 기반으로 서비스에 대한 입력 또는 출력 모델 객체를 정의합니다.

1. 탭 **[!UICONTROL 저장]** 양식 데이터 모델을 저장합니다.

   다음 표에서는 사용 가능한 [!DNL Azure] 서비스:

   <table>
    <tbody>
     <tr>
      <th><strong>서비스 이름</strong></th>
      <th><strong>설명</strong></th>
     </tr>
     <tr>
      <td>Azure에서 Blob 가져오기</td>
      <td>ID 또는 이름을 사용하여 Azure 저장소에서 Blob으로 저장된 데이터를 검색합니다</td>
     </tr>
     <tr>
      <td>Azure에서 바이너리 URL을 사용하여 Blob 가져오기</td>
      <td>ID 또는 이름을 사용하여 Azure 저장소에서 바이너리에 대한 URL이 있는 Blob으로 저장된 데이터를 검색합니다</td>
     </tr>
     <tr>
      <td>Azure에서 Blob 저장</td>
      <td>Blob ID를 사용하여 Azure 저장소에 데이터를 저장합니다</td>
     </tr>
     <tr>
      <td>Azure에서 Blob 업데이트</td>
      <td>Blob ID를 사용하여 Azure 저장소의 데이터를 업데이트합니다</td>
     </tr>
     <tr>
      <td>Azure에서 Blob ID 목록을 검색합니다</td>
      <td>입력 요청에 정의된 숫자를 기반으로 Azure에서 Blob ID 목록을 검색합니다.</td>
     </tr>
     <tr>
      <td>Azure에서 Blob에 대한 SAS URL 검색</td>
      <td>입력 요청의 Blob ID를 기반으로 Azure에서 Blob에 대한 SAS URL을 검색합니다.</td>
     </tr>
     <tr>
      <td>Azure에서 Blob 삭제</td>
      <td>Blob ID를 사용하여 Azure 저장소에서 데이터를 삭제합니다</td>
     </tr>
    </tbody>
   </table>

### 데이터 모델 개체 속성을 검색 키로 정의 {#define-data-model-object-as-metadata}

데이터 모델 개체 속성을 검색 키로 정의하려면

1. 에서 **[!UICONTROL 모델]** 탭에서 데이터 모델 개체 속성을 선택하고 탭합니다 **[!UICONTROL 속성 편집]**.
1. 스위치 **[!UICONTROL 검색 키]** 옵션을 켜짐 상태로 전환합니다. 이 옵션은 기본 데이터 유형에만 사용할 수 있습니다.
1. 탭 **[!UICONTROL 완료]** 그런 다음 **[!UICONTROL 저장]** 양식 데이터 모델을 저장합니다.

데이터 모델 개체 속성을 검색 키로 정의한 후 해시 값은 Azure 인덱스 태그에 저장되고 Base64 인코딩 값은 Azure 메타데이터에 저장됩니다.

>[!NOTE]
>
>Azure에서는 Blob당 10개의 태그만 허용하고 검색 키로 표시된 속성 값은 해시 후 Azure 인덱스 태그에 저장되므로 Azure 개체당 10개의 검색 키만 허용됩니다.
