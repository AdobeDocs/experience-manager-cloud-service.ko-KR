---
title: 핵심 구성 요소 기반 적응형 양식을 초안으로 저장하고 초안 및 제출 구성 요소를 사용하여 초안 및 제출을 나열하는 방법
description: 적응형 양식 기반의 핵심 구성 요소를 초안으로 저장하는 방법에 대해 알아봅니다. 또한 초안 및 제출 구성 요소를 사용하여 로그인한 사용자의 초안 및 제출을 나열하는 방법을 이해하시겠습니까?
feature: Adaptive Forms, Core Components
exl-id: c0653bef-afeb-40c1-b131-7d87ca5542bc
role: User, Developer, Admin
source-git-commit: 31f18027d856cbd161457c4a01d6c7c17d1c2b89
workflow-type: tm+mt
source-wordcount: '1376'
ht-degree: 3%

---


# 양식을 초안으로 저장하고 사이트 페이지에 나열

<span class="preview"> 이 문서에는 시험판 기능인 **자동 저장** 기능에 대한 내용이 포함되어 있습니다. 이 프리릴리스 기능은 [프리릴리스 채널](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/release-notes/prerelease.html#new-features)을 통해서만 액세스할 수 있습니다.</span>

양식 작성을 시작하지만 나중에 일시 중지했다가 다시 돌아가야 하는 사용자를 고려하십시오. AEM에서는 `save-as-draft` 옵션을 제공하므로 사용자가 나중에 완료할 수 있도록 양식을 초안으로 저장할 수 있습니다. 이를 용이하게 하기 위해 AEM에서는 AEM Sites 페이지에 초안 및 제출을 표시하는 기본 제공 **초안 및 제출** 양식 포털 구성 요소를 제공합니다. 구성 요소에는 제출된 양식과 함께 나중에 완료할 수 있도록 초안으로 저장된 양식이 나열됩니다. 로그인한 사용자만 초안을 편집하거나 제출된 양식을 볼 수 있습니다. 그러나 익명 사용자가 **검색 및 목록** 구성 요소를 사용하여 양식 목록을 탐색하고 양식을 초안으로 저장하는 경우 해당 초안이 **초안 및 제출** 구성 요소에 의해 나열되지 않습니다. 초안과 제출을 보려면 양식 제출 시 사용자가 로그인해야 합니다.

![초안 아이콘](assets/drafts-component.png)

## 전제 조건

* [환경에 대한 적응형 Forms 핵심 구성 요소 를 활성화합니다.](/help/forms/enable-adaptive-forms-core-components.md)

  최신 핵심 구성 요소를 환경에 배포하면 작성 환경에서 Forms 포털 구성 요소에 액세스할 수 있습니다.

* [초안 및 제출 Forms 포털 구성 요소에 대한 Azure Storage 및 통합 스토리지 커넥터 구성](#configure-azure-storage-and-unified-storage-connector-for-drafts--submissions-forms-portal-component)

### 초안 및 제출 Forms 포털 구성 요소에 대한 Azure Storage 및 통합 스토리지 커넥터 구성

**초안 및 제출** 구성 요소에는 AEM Sites 페이지에 초안을 저장하고 나열하기 위한 저장소 설정이 필요합니다. 통합 스토리지 커넥터는 AEM을 외부 스토리지와 연결하는 프레임워크를 제공합니다. 양식을 초안으로 저장하려면 Azure 저장소 계정 및 [!DNL Azure] 저장소 계정에 대한 액세스 권한을 부여하는 액세스 키가 있는지 확인하세요. Azure 스토리지 계정과 액세스 키가 있으면 다음 단계를 수행하여 Azure 스토리지 구성을 만듭니다.

1. **[!UICONTROL 도구]** > **[!UICONTROL Cloud Service]** > **[!UICONTROL Azure 저장소]**&#x200B;로 이동합니다.

   ![Azure 저장소 카드 선택](/help/forms/assets/save-form-as-draft-azure-card.png)

1. 구성을 만들 구성 폴더를 선택하고 **[!UICONTROL 만들기]**&#x200B;를 선택합니다.

   ![Azure 저장소 구성 폴더 선택](/help/forms/assets/save-form-as-draft-select-config-folder.png)

1. **[!UICONTROL 제목]** 필드에 구성의 제목을 지정합니다.
1. **[!UICONTROL Azure 저장소 계정]** 및 **[!UICONTROL Azure 액세스 키]** 필드에 [!DNL Azure] 저장소 계정의 이름을 지정하십시오.

   ![Azure Storage 구성](/help/forms/assets/save-form-as-draft-azure-storage.png)

1. **저장**&#x200B;을 클릭합니다.

   >[!NOTE]
   >
   > [Microsoft Azure 포털](https://learn.microsoft.com/en-us/azure/storage/common/storage-account-keys-manage?tabs=azure-portal)에서 **[!UICONTROL Azure 저장소 계정]** 및 **[!UICONTROL Azure 액세스 키]**&#x200B;를 검색할 수 있습니다.

   Azure 스토리지 구성을 만들었으면 다음 단계를 사용하여 Forms 포털용 통합 스토리지 커넥터를 구성하십시오.

1. **[!UICONTROL 도구]** > **[!UICONTROL Forms]** > **[!UICONTROL 통합 저장소 커넥터]**&#x200B;로 이동합니다.

   ![통합 커넥터 저장소](/help/forms/assets/save-form-as-draft-unified-connector.png)

1. **[!UICONTROL Forms 포털]** 섹션의 **[!UICONTROL 저장소]** 드롭다운 목록에서 **[!UICONTROL Azure]**&#x200B;을(를) 선택합니다.
1. **[!UICONTROL 저장소 구성 경로]** 필드에 Azure 저장소 구성에 대한 구성 경로를 지정하십시오.

   ![통합 커넥터 저장소 설정](/help/forms/assets/save-form-as-draft-unified-connector-storage.png)

1. **[!UICONTROL 저장]**&#x200B;을 선택합니다.

>[!NOTE]
>
> Azure 이외의 저장소 옵션을 구성해야 하는 경우 공식 이메일 주소에서 aem-forms-ea@adobe.com으로 자세한 요구 사항을 적어 보내십시오.

초안 및 제출된 양식을 저장하기 위해 Azure Storage 및 통합 스토리지 커넥터를 구성했으면 AEM Sites 페이지에서 **초안 및 제출** 구성 요소를 추가하십시오.

## 초안 및 제출 구성 요소를 AEM Sites 페이지에 추가하는 방법

기본 Forms 포털 구성 요소를 사용하여 Sites 페이지에 초안 및 제출을 나열할 수 있습니다. **초안 및 제출** 포털 구성 요소를 추가하려면 다음 단계를 수행하십시오.

1. **편집** 모드로 AEM Sites 페이지를 엽니다.
1. **[!UICONTROL 페이지 정보]** > **[!UICONTROL 템플릿 편집]**(으)로 이동
   ![템플릿 정책 편집](/help/forms/assets/save-form-as-draft-edit-template.png)

1. **[!UICONTROL 정책]**&#x200B;을 클릭하고 **[AEM Archetype 프로젝트 이름] - Forms 및 통신 포털**&#x200B;에서 **[!UICONTROL 초안 및 제출]** 확인란을 선택하십시오.

   ![정책 선택](/help/forms/assets/save-form-as-draft-enable-policy.png)

1. **[!UICONTROL 완료]**&#x200B;를 클릭합니다.
1. 이제 작성 모드에서 AEM Sites 페이지를 다시 엽니다.
1. 페이지 편집기 내에서 Forms 포털 구성 요소를 추가할 수 있는 섹션을 찾습니다.
1. **추가** 아이콘을 클릭합니다. 아이콘은 새 구성 요소를 추가하는 옵션을 나타내는 더하기 기호(+)입니다.

   **추가** 아이콘을 클릭하면 삽입할 다양한 구성 요소를 표시하는 **새 구성 요소 삽입** 대화 상자가 표시됩니다.

   >[!NOTE]
   >
   > 또는 구성 요소를 드래그 앤 드롭할 수도 있습니다.

1. 대화 상자에서 사용 가능한 구성 요소를 탐색하고 목록에서 원하는 구성 요소를 선택합니다. 예를 들어 목록에서 **초안 및 제출** 구성 요소를 선택하여 **초안 및 제출** Forms 포털 구성 요소를 추가합니다.

   ![초안 및 제출 구성 요소 추가](/help/forms/assets/save-form-as-draft-add-dns.png)

이제 요구 사항에 따라 **초안 및 제출** 구성 요소의 속성을 구성하십시오.

## 초안 및 제출 구성 요소의 속성 구성

**초안 및 제출**&#x200B;의 속성을 구성할 수 있습니다.
1. **초안 및 제출** 구성 요소를 선택하십시오.
1. ![구성 아이콘](assets/configure_icon.png)을 클릭하면 대화 상자가 나타납니다.
1. **[!UICONTROL 초안 및 제출]** 대화 상자에서 다음을 지정하십시오.
   * **제목** Sites 페이지에서 구성 요소를 식별하기 위해 기본적으로 제목이 구성 요소 위에 나타납니다.
   * **유형 선택**: 초안 또는 제출된 양식으로 양식 목록을 나타냅니다. **Forms 초안**&#x200B;을 선택하면 초안으로 저장된 양식이 표시됩니다. 또는 **제출된 Forms**&#x200B;을 선택하면 로그인한 사용자가 제출한 양식이 표시됩니다.
   * **레이아웃**: 목록 초안 양식이나 제출된 양식을 카드 또는 목록 형식으로 표시합니다.

   ![초안 및 제출 구성 요소 속성](/help/forms/assets/save-form-as-draft-dns-properties.png)

## 초안으로 저장할 양식 구성

다음 두 가지 방법으로 적응형 Forms을 구성하여 나중에 사용할 수 있도록 초안으로 저장할 수 있습니다.
* [사용자 작업](#user-action)
* [자동 저장](#auto-save)

### 사용자 작업

>[!NOTE]
>
> **양식 저장** 규칙을 사용하여 양식을 초안으로 저장하려면 [핵심 구성 요소 버전이 3.0.24 이상](https://github.com/adobe/aem-core-forms-components)(으)로 설정되어 있는지 확인하십시오.

양식을 초안으로 저장하려면 단추와 같은 양식 구성 요소에 **양식 저장** 규칙을 만듭니다. 버튼을 클릭하면 규칙이 트리거되고 양식이 초안으로 저장됩니다. 단추 구성 요소에 **양식 저장** 규칙을 만들려면 다음 단계를 수행하십시오.

1. 편집 모드에서 적응형 양식을 엽니다.
1. **[!UICONTROL 규칙 편집]** 아이콘을 선택하여 **Button** 구성 요소에 대한 규칙 편집기를 엽니다.
1. **[!UICONTROL 만들기]**&#x200B;를 선택하여 단추에 대한 규칙을 구성하고 만듭니다.
1. **[!UICONTROL When]** 섹션에서 **클릭됨**&#x200B;을(를) 선택하고 **[!UICONTROL Then]** 섹션에서 **양식 저장** 옵션을 선택합니다.
1. **[!UICONTROL 완료]**&#x200B;를 선택하여 규칙을 저장합니다.

   ![단추에 대한 규칙 만들기](/help/forms/assets/save-form-as-drfat-create-rule.png)

적응형 양식을 미리 보고 작성하고 **양식 저장** 단추를 클릭하면 양식이 초안으로 저장됩니다.

### 자동 저장

>[!NOTE]
>
> 자동 저장 기능을 사용하여 양식을 초안으로 저장하려면 [핵심 구성 요소 버전이 3.0.52 이상으로 설정되어 있는지](https://github.com/adobe/aem-core-forms-components)확인하십시오.

또한 시간 기반 이벤트에 따라 자동으로 저장하도록 적응형 양식을 구성하여 지정된 기간 후에 양식을 저장할 수 있습니다. 환경에 대해 [Forms 포털 구성 요소를 활성화](/help/forms/list-forms-on-sites-page.md#enable-forms-portal-components-for-your-existing-environment)하면 **자동 저장** 탭이 Forms 컨테이너 속성에 나타납니다. 적응형 양식에 대한 자동 저장 기능을 구성할 수 있습니다.

1. 작성자 인스턴스에서 편집 모드로 적응형 양식을 엽니다.
1. 콘텐츠 브라우저를 열고 적응형 양식의 **[!UICONTROL 안내서 컨테이너]** 구성 요소를 선택합니다.
1. 가이드 컨테이너 속성 ![가이드 속성](/help/forms/assets/configure-icon.svg) 아이콘을 클릭하고 **[!UICONTROL 자동 저장]** 탭을 엽니다.

   ![자동 저장](/help/forms/assets/auto-save.png)

1. **[!UICONTROL 사용]** 확인란을 선택하여 양식 자동 저장을 사용하도록 설정합니다.
1. **[!UICONTROL Trigger]**&#x200B;을(를) **Time based**(으)로 구성하여 특정 시간 간격 후 <!--based on the occurrence of an event or--> 양식을 자동 저장합니다.
1. 정의된 간격에서 양식의 자동 저장을 트리거하는 기간을 설정하려면 **[!UICONTROL 이 간격(초)에 자동 저장]**&#x200B;을 지정하십시오.
1. **[!UICONTROL 완료]**&#x200B;를 클릭합니다.

## 초안 및 제출 구성 요소를 사용하여 사이트 페이지에서 초안/제출된 양식 보기

저장된 초안 또는 제출된 양식을 보려면 **초안 및 제출** Forms 포털 구성 요소를 사용하십시오.
초안 및 제출 구성 요소의 [구성 대화 상자](#configure-properties-of-the-drafts--submissions-component)에서 **[!UICONTROL 유형 선택]**&#x200B;이(가) **초안 Forms**(으)로 선택되면 초안으로 저장된 양식이 사이트 페이지에 표시됩니다. 생략 부호(...)를 클릭하여 초안을 열어 양식을 완료할 수 있습니다.

![초안 아이콘](assets/drafts-component.png)

초안 및 제출 구성 요소의 [구성 대화 상자](#configure-properties-of-the-drafts--submissions-component)에서 **[!UICONTROL 유형 선택]**&#x200B;이(가) **제출된 Forms**(으)로 선택되면 제출된 양식이 표시됩니다. 제출된 양식을 볼 수 있지만 편집할 수는 없습니다.

![제출 아이콘](assets/submission-listing.png)

양식의 오른쪽 아래 모서리에 표시되는 줄임표(...)를 클릭하여 양식을 삭제할 수도 있습니다.

## 다음 단계

다음 문서에서는 [Forms 포털 연결 구성 요소를 사용하여 Sites 페이지에서 양식에 대한 참조를 추가하는 방법](/help/forms/add-form-link-to-aem-sites-page.md)을 배워보겠습니다.

## 관련 문서

{{forms-portal-see-also}}

## 추가 참조 {#see-also}

{{see-also}}