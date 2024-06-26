---
Title: How to submit data from an Adaptive Form to Microsoft® OneDrive?
Description: Explore the streamlined process of connecting AEM Forms with Microsoft® OneDrive using the Submit to OneDrive Submit Action. Learn the step-by-step guide to configure OneDrive and set up submission actions for efficient data storage and retrieval
keywords: AEM Forms OneDrive 통합, AEM Forms를 사용하여 Microsoft OneDrive, OneDrive 구성 설정에 연결
feature: Adaptive Forms, Core Components
exl-id: dbfa4094-1b92-4a7c-a799-f66973d27054
title: "적응형 양식에 대한 제출 액션을 구성하는 방법"
role: User, Developer
source-git-commit: 2b76f1be2dda99c8638deb9633055e71312fbf1e
workflow-type: tm+mt
source-wordcount: '597'
ht-degree: 67%

---

# Microsoft® OneDrive에 적응형 양식 제출

**[!UICONTROL OneDrive에 제출]** 제출 액션은 적응형 양식을 Microsoft® OneDrive와 연결합니다. 양식 데이터, 파일, 첨부 파일 또는 기록 문서를 연결된 Microsoft® OneDrive 저장소에 제출할 수 있습니다.

AEM as a Cloud Service에서는 양식 제출을 처리하기 위한 다양한 제출 액션을 제공합니다. 다음에서 이러한 옵션에 대해 자세히 알아볼 수 있습니다. [적응형 양식 제출 액션](/help/forms/configure-submit-actions-core-components.md)  기사.

## 장점

AEM Forms과 Microsoft® OneDrive의 원활한 통합의 이점 중 일부는 다음과 같습니다.

* OneDrive의 장치 간 접근성을 통해 저장된 양식 데이터를 다른 플랫폼에서 쉽게 사용할 수 있습니다. 사용자는 데스크탑, 노트북, 태블릿, 모바일 기기에서 제출된 데이터, 첨부 파일, 문서에 접근할 수 있어 접근성과 유연성이 향상된다.
* AEM Forms와 OneDrive를 통합하면 효율적인 데이터 저장을 위한 안정적이고 확장 가능한 솔루션을 제공합니다. 파일, 첨부 파일, 기록 문서 등 모든 적응형 양식 제출을 OneDrive에 편리하게 저장하여 체계적이고 접근 가능한 데이터를 유지할 수 있습니다.

## 적응형 양식에 OneDrive 연결

>[!VIDEO](https://video.tv.adobe.com/v/3424864/connect-aem-adaptive-form-to-onedrive/?quality=12&learn=on)

AEM Forms 제출용 OneDrive를 구성하려면 다음 단계를 수행하십시오.

1. [OneDrive 구성 만들기](#create-a-onedrive-configuration-create-onedrive-configuration): AEM Forms를 Microsoft® OneDrive Storage에 연결합니다.
2. [적응형 양식에서 OneDrive에 제출 동작 사용](#use-onedrive-configuration-in-an-adaptive-form-use-onedrive-configuartion-in-af): 적응형 양식을 구성된 Microsoft® OneDrive에 연결합니다.

### OneDrive 구성 만들기 {#create-onedrice-configuration}

AEM Forms를 Microsoft® OneDrive Storage에 연결하려면

1. **AEM Forms 작성자** 인스턴스 > **[!UICONTROL 도구]** > **[!UICONTROL 클라우드 서비스]** > **[!UICONTROL Microsoft® OneDrive]**&#x200B;로 이동합니다.
1. **[!UICONTROL Microsoft® OneDrive]**&#x200B;를 선택하면 **[!UICONTROL OneDrive 브라우저]**&#x200B;로 리디렉션됩니다.
1. **구성 컨테이너**&#x200B;를 선택합니다. 선택한 구성 컨테이너에 구성을 저장합니다.
1. **[!UICONTROL 만들기]**&#x200B;를 클릭합니다. OneDrive 구성 마법사가 나타납니다.

   ![OneDrive 구성 화면](/help/forms/assets/onedrive-configuration.png)

1. **[!UICONTROL 제목]**, **[!UICONTROL 클라이언트 ID]**, **[!UICONTROL 클라이언트 보안]** 및 **[!UICONTROL OAuth URL]**&#x200B;을 지정합니다. OAuth URL의 클라이언트 ID, 클라이언트 보안, 테넌트 ID를 검색하는 방법에 대한 자세한 내용은 [Microsoft® Documentation](https://learn.microsoft.com/en-us/graph/auth-register-app-v2)을 참조하십시오.
   * Microsoft® Azure 포털에서 앱의 `Client ID` 및 `Client Secret`를 검색할 수 있습니다.
   * Microsoft® Azure 포털에서 리디렉션 URI를 `https://[author-instance]/libs/cq/onedrive/content/configurations/wizard.html`로 추가합니다. `[author-instance]`를 작성자 인스턴스의 URL로 대체합니다.
   * `offline_access` 및 `Files.ReadWrite.All` API 권한을 추가하여 읽기/쓰기 권한을 제공합니다.
   * OAuth URL 사용: `https://login.microsoftonline.com/tenant-id/oauth2/v2.0/authorize`. Microsoft® Azure 포털에서 `<tenant-id>`를 앱의 `tenant-id`로 대체합니다.

   >[!NOTE]
   >
   > **클라이언트 보안** 필드는 Azure Active Directory 애플리케이션 구성에 따라 필수 또는 선택 사항입니다. 애플리케이션을 구성하여 클라이언트 보안을 사용하는 경우 클라이언트 보안을 제공해야 합니다.

1. **[!UICONTROL 연결]**&#x200B;을 클릭합니다. 연결이 완료되면 `Connection Successful` 메시지가 나타납니다.

1. 이제 **[!UICONTROL OneDrive 컨테이너]** > **[OneDrive 폴더]**&#x200B;를 선택하여 데이터를 저장합니다.

   >[!NOTE]
   >
   >* 기본적으로 `forms-ootb-storage-adaptive-forms-submission`은 OneDrive 컨테이너에 존재합니다.
   > * 아직 존재하지 않는 경우 **폴더 만들기**&#x200B;를 클릭하여 폴더를 `forms-ootb-storage-adaptive-forms-submission`로 만듭니다.

이제 적응형 양식에서 제출 액션에 대한 OneDrive 스토리지 구성을 사용할 수 있습니다.

### 적응형 양식에서 OneDrive 구성 사용 {#use-onedrive-configuartion-in-af}

적응형 양식에서 만든 OneDrive 스토리지 구성을 사용하여 데이터 또는 생성된 기록 문서를 OneDrive 폴더에 저장할 수 있습니다. 적응형 양식에서 OneDrive 스토리지 구성을 다음과 같이 사용하려면 다음 단계를 수행하십시오.
1. [적응형 양식](/help/forms/creating-adaptive-form.md)을 만듭니다.

   >[!NOTE]
   >
   > * OneDrive 스토리지가 생성되면 적응형 양식에 대한 [!UICONTROL 구성 컨테이너]를 선택합니다.
   > * [!UICONTROL 구성 컨테이너]가 선택되지 않은 경우 제출 액션 속성 창에 글로벌 [!UICONTROL 스토리지 구성] 폴더가 나타납니다.

1. **제출 액션**&#x200B;을 **[!UICONTROL OneDrive에 제출]**로 선택합니다.
   ![OneDrive GIF](/help/forms/assets/onedrive-video.gif)
1. 데이터를 저장하려는 경우 **[!UICONTROL 스토리지 구성]**&#x200B;을 선택합니다.
1. **[!UICONTROL 저장]**&#x200B;을 클릭하여 제출 설정을 저장합니다.

양식이 제출되면 지정된 Microsoft® OneDrive Storage에 데이터가 저장됩니다.
데이터를 저장하는 폴더 구조는 `/folder_name/form_name/year/month/date/submission_id/data`입니다.

## 관련 문서

{{af-submit-action}}
