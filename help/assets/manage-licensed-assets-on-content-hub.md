---
title: Content Hub에서 라이선스가 부여된 자산 관리
description: 에셋 메타데이터 양식에 라이선스 필드를 추가하고, 라이선스 메타데이터 속성을 에셋 폴더에 적용하고, 라이선스가 있는 에셋을 사용할 수 있도록 승인하는 방법에 대해 알아봅니다.
exl-id: ac3aad9f-c7b3-47a7-9314-a2f8277f0d3e
source-git-commit: bfa7ceeb839574ff1b80ffc25b6519a629247385
workflow-type: tm+mt
source-wordcount: '610'
ht-degree: 3%

---

# Content Hub에서 라이선스가 부여된 자산 관리 {#manage-licensed-assets-on-content-hub}

관리자는 AEM 작성 환경의 에셋 속성에 표시되도록 에셋 라이선스 필드를 포함하도록 메타데이터 양식을 편집합니다. 그런 다음 Content Hub에서 에셋에 대한 라이선스와 라이선스를 부여하고 사용 가능하게 하는 해당 라이선스를 승인할 수 있습니다.

다음 단계를 실행합니다.

1. 라이선스 세부 정보를 포함하는 새 텍스트 필드를 포함하도록 메타데이터 양식을 편집합니다. 텍스트 필드를 `dc:license` 속성에 매핑합니다. 메타데이터 양식에 필드를 추가하고 속성을 정의하는 방법에 대한 자세한 내용은 [메타데이터 Forms 설정](/help/assets/metadata-assets-view.md#metadata-forms)을 참조하십시오.
   ![zip 추출](/help/assets/assets/metadata-form-edit.png)
1. 메타데이터 양식을 에셋 폴더에 적용하여 1단계에서 통합된 설정을 적용합니다. 에셋 폴더에 메타데이터 양식을 할당하는 방법에 대한 자세한 내용은 [폴더에 메타데이터 양식 할당](/help/assets/metadata-assets-view.md#metadata-forms)을 참조하십시오.
1. [라이선스가 있는 PDF 승인](/help/assets/manage-organize-assets-view.md#set-asset-status)
1. 자산을 선택하고 **세부 정보**&#x200B;를 클릭하여 해당 속성을 확인합니다. 1단계에서 추가된 라이선스 필드에서 3단계에서 승인되었거나 이미 이전에 승인된 에셋 라이선스의 절대 경로를 정의합니다. Content Hub 절대 경로는 다음 표준 패턴을 따릅니다. `/content/dam/(The asset's folder hierarchy within the DAM repository)/(asset_name).(file_extension)`. 예: /content/dam/teamA/projects/documents/file1.pdf
   ![절대 경로](/help/assets/assets/absolute-path.png)
1. Content Hub에서 사용할 수 있도록 자산을 승인하고 **저장**&#x200B;을 클릭합니다. 에셋을 승인하는 방법에 대한 자세한 내용은 [에셋 상태 설정](/help/assets/manage-organize-assets-view.md#set-asset-status)을 참조하십시오.

## 자주 묻는 질문 {#faqs-manage-licensed-assets-content-hub}

### AEM Assets Content Hub에서 라이선스가 있는 에셋을 관리하는 목적은 무엇입니까?

Content Hub에서 라이센스가 부여된 에셋을 관리하면 관리자는 유효한 라이센스가 있는 승인된 에셋만 사용할 수 있도록 하여 AEM 작성 환경 내에서 규정 준수 및 적절한 메타데이터 추적을 유지할 수 있습니다.

### Experience Manager as a Cloud Service의 에셋 속성에 라이선스 필드를 추가하려면 어떻게 해야 합니까?

`dc:license` 속성에 매핑된 새 텍스트 필드를 포함하도록 메타데이터 양식을 편집하여 자산 속성에 라이선스 필드를 추가할 수 있습니다. 그러면 이 필드가 AEM Assets 작성 환경의 에셋 속성에 표시됩니다.

### 메타데이터 양식을 에셋 폴더에 적용하여 에셋 속성에 라이선스 필드를 포함시키는 방법

라이선스 필드를 포함하도록 메타데이터 양식을 편집합니다. 이 메타데이터 양식을 원하는 에셋 폴더에 적용하여 해당 폴더 내의 모든 에셋에 대해 새 설정이 통합되도록 합니다.

### 에셋에 대한 라이선스 세부 사항을 지정하는 방법

라이선스 세부 정보를 지정하려면 에셋을 선택하고 **세부 정보**&#x200B;를 클릭하여 해당 속성을 확인하고 메타데이터 양식에 추가된 라이선스 필드에 승인된 에셋 라이선스의 절대 경로를 입력하십시오.

### 에셋 라이선스에 대한 Content Hub 절대 경로에 필요한 형식은 무엇입니까?

Content Hub 절대 경로는 /content/dam/(DAM 저장소 내의 에셋의 폴더 계층)/(asset_name) 패턴을 따라야 합니다.(file_extension). 예: `/content/dam/teamA/projects/documents/file1.pdf`

### AEM Assets Content Hub에서 사용할 수 있도록 하기 위해 에셋과 라이선스를 모두 승인하는 것이 중요한 이유는 무엇입니까?

에셋과 해당 라이센스를 모두 승인하면 AEM Assets Content Hub에서 적절한 라이센스가 부여되고 승인된 에셋만 사용할 수 있으므로 규정 준수 및 적절한 사용 권한을 유지하는 데 도움이 됩니다.

### 라이선스를 승인한 후 AEM Assets Content Hub에서 자산을 사용할 수 있도록 하려면 어떻게 해야 합니까?

에셋의 속성에서 라이선스 경로를 정의한 후 에셋을 승인하고 저장 을 클릭합니다. 이 작업을 수행하면 라이센스가 부여된 에셋을 AEM Assets Content Hub에서 사용할 수 있습니다.

### Content Hub에서 라이선스가 있는 에셋을 관리하는 사람은 누구입니까?

관리자는 Content Hub에서 메타데이터 양식을 편집하고, 자산 폴더에 할당하고, 자산과 라이센스를 모두 승인할 책임이 있습니다.
