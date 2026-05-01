---
title: 적응형 양식 제출 시 SharePoint 목록 저장소로 데이터를 전송하는 방법
Description: Learn how to send data from your Adaptive Form to a SharePoint storage like a SharePoint list when you submit the form.
keywords: 적응형 양식에 대해 SharePoint 목록을 연결하는 방법? SharePoint에 제출, SharePoint 목록 구성 만들기, 적응형 양식에 SharePoint 제출 액션 사용, 적응형 양식을 Microsoft&reg; SharePoint 목록에 연결
feature: Adaptive Forms, Core Components, Foundation Components, Edge Delivery Services
role: User, Developer
badgeSaas: label="AEM Forms" type="Positive" tooltip="AEM Forms에 적용됩니다)."
exl-id: 9ac3e7be-c6fa-4dbc-9aba-b81741ba6c55
source-git-commit: 0e5045b87719781301d91874c7355eda9426beef
workflow-type: tm+mt
source-wordcount: '782'
ht-degree: 22%

---

# ® SharePoint 목록에 적응형 양식 연결 {#connect-af-sharepoint-list}

>[!VIDEO](https://video.tv.adobe.com/v/3424820/connect-aem-adaptive-form-to-sharepointlist/?quality=12&learn=on)

<span> 이 비디오는 핵심 구성 요소에만 적용됩니다. UE/Foundation 구성 요소에 대해서는 문서를 참조하십시오.</span>

적응형 양식에서 [!UICONTROL SharePoint 목록에 제출] 제출 액션을 사용하려면:

1. [SharePoint 목록 구성 만들기](#1-create-a-sharepoint-list-configuration): AEM Forms을 Microsoft® Sharepoint 목록 저장소에 연결합니다.
1. [적응형 양식에서 FDM(양식 데이터 모델)을 사용하여 제출](#2-use-the-submit-using-form-data-model-fdm-in-an-adaptive-form-use-submit-using-fdm): 적응형 양식을 구성된 ® SharePoint에 연결합니다.

## &#x200B;1. SharePoint 목록 구성 만들기

AEM Forms을 Microsoft® Sharepoint 목록에 연결하려면:

1. **[!UICONTROL 도구]** > **[!UICONTROL 클라우드 서비스]** > **[!UICONTROL ® SharePoint]**&#x200B;로 이동합니다.
1. **구성 컨테이너**&#x200B;를 선택합니다. 선택한 구성 컨테이너에 구성을 저장합니다.
1. 드롭다운 목록에서 **[!UICONTROL 만들기]** > **[!UICONTROL SharePoint 목록]**&#x200B;을 클릭합니다. SharePoint 구성 마법사가 나타납니다.
1. **[!UICONTROL 제목]**, **[!UICONTROL 클라이언트 ID]**, **[!UICONTROL 클라이언트 보안]** 및 **[!UICONTROL OAuth URL]**&#x200B;을 지정합니다. OAuth URL의 클라이언트 ID, 클라이언트 보안, 테넌트 ID를 검색하는 방법에 대한 자세한 내용은 [Microsoft® Documentation](https://learn.microsoft.com/en-us/graph/auth-register-app-v2)을 참조하십시오.
   * Microsoft® Azure 포털에서 앱의 `Client ID` 및 `Client Secret`를 검색할 수 있습니다.
   * Microsoft® Azure 포털에서 리디렉션 URI를 `https://[author-instance]/libs/cq/sharepointlist/content/configurations/wizard.html`로 추가합니다. `[author-instance]`를 작성자 인스턴스의 URL로 대체합니다.
   * 읽기/쓰기 권한을 제공하려면 **® 그래프** 탭에서 API 권한 `offline_access` 및 `Sites.Manage.All`을(를) 추가하십시오. SharePoint 데이터와 원격으로 상호 작용하려면 **Sharepoint** 탭에 `AllSites.Manage` 권한을 추가하십시오.
   * OAuth URL 사용: `https://login.microsoftonline.com/tenant-id/oauth2/v2.0/authorize`. Microsoft® Azure 포털에서 `<tenant-id>`를 앱의 `tenant-id`로 대체합니다.

     >[!NOTE]
     >
     > **클라이언트 보안** 필드는 Azure Active Directory 애플리케이션 구성에 따라 필수 또는 선택 사항입니다. 애플리케이션을 구성하여 클라이언트 보안을 사용하는 경우 클라이언트 보안을 제공해야 합니다.

1. **[!UICONTROL 연결]**&#x200B;을 클릭합니다. 연결이 완료되면 `Connection Successful` 메시지가 나타납니다.
1. 드롭다운 목록에서 **[!UICONTROL SharePoint 사이트]** 및 **[!UICONTROL SharePoint 목록]**&#x200B;을 선택합니다.
1. ® SharePointList에 대한 클라우드 구성을 만들려면 **[!UICONTROL 만들기]**&#x200B;를 선택하십시오.

### 인증서 기반 인증 {#certificate-based-authentication}

SharePoint 목록 구성에 대한 <span class="preview"> 인증서 기반 인증이 얼리 어답터 프로그램에 있습니다. 공식 이메일 ID를 사용하여 aem-forms-ea@adobe.com으로 이메일을 보내 얼리 어답터 프로그램에 참여하고 기능에 대한 액세스 권한을 요청할 수 있습니다. </span>

SharePoint 목록 구성 마법사에서

1. **[!UICONTROL 인증 유형]**&#x200B;을(를) **인증서 기반 인증**(으)로 설정합니다.
1. **[!UICONTROL 제목]**, **[!UICONTROL 클라이언트 ID]**, **[!UICONTROL 인증서 별칭]**, **[!UICONTROL 테넌트 ID]** 및 **[!UICONTROL 테넌트 이름]**&#x200B;을(를) 지정하십시오.
1. **[!UICONTROL SharePoint 사이트 URL]**&#x200B;을(를) 입력하고 필요한 경우 사이트 연결을 확인한 다음 **[!UICONTROL SharePoint 목록]**&#x200B;을(를) 선택하십시오.
1. **[!UICONTROL 연결]**&#x200B;을 클릭하여 연결을 확인한 다음 **[!UICONTROL 저장 및 닫기]**&#x200B;를 클릭하여 구성을 저장합니다.

아래 스크린샷에는 **인증서 기반 인증**&#x200B;을 사용하는 SharePoint 목록 구성이 표시됩니다.

![인증서 기반 인증을 사용한 SharePoint 목록 구성](/help/forms/assets/sharepoint-list-certificate-auth-configuration.png){width=50%, height=50%, align=center}

AEM 및 Microsoft Azure에 대한 인증서를 준비하려면 AEM에서 다음 단계를 수행한 다음 Microsoft Azure에서 공개 인증서를 등록하십시오.

**AEM**

1. **[!UICONTROL 도구]** > **[!UICONTROL 보안]** > **[!UICONTROL 사용자]**(으)로 이동합니다.
1. **[!UICONTROL fd-cloudservice]**&#x200B;를 검색하고 사용자를 선택한 다음 **[!UICONTROL 속성]**&#x200B;을 클릭합니다.
1. **[!UICONTROL Keystore]** 탭을 엽니다. 키 저장소를 아직 만들지 않은 경우 **[!UICONTROL 키 저장소 만들기]**&#x200B;를 클릭하고 프롬프트를 완료하여 키 저장소 암호를 설정합니다.
1. 키 저장소에 개인 키 추가: **[!UICONTROL 키 저장소 파일에서 개인 키 추가]**&#x200B;를 확장하고 **.jks** 파일을 업로드합니다.
1. SharePoint 목록 구성의 **[!UICONTROL 인증서 별칭]**&#x200B;과 일치하는 **[!UICONTROL 별칭]**&#x200B;을 입력하고 키 자료를 제출한 다음 **[!UICONTROL 저장 및 닫기]**&#x200B;를 클릭합니다.

인증서가 추가되면 스크린샷에 키 저장소가 표시됩니다. **[!UICONTROL 별칭]**&#x200B;은(는) SharePoint 목록 클라우드 구성의 **[!UICONTROL 인증서 별칭]**&#x200B;과(와) 일치해야 합니다.

인증서 별칭이 있는 ![fd-cloudservice 사용자 키 저장소](/help/forms/assets/fd-cloudservice-keystore-certificate.png){width=50%, height=50%, align=center}

**Microsoft Azure**

1. 응용 프로그램 등록을 열고 **인증서 및 암호** > **인증서**(으)로 이동합니다.
1. **인증서 업로드**&#x200B;를 선택하고 Azure에서 응용 프로그램에 대해 신뢰해야 하는 인증서 파일(공개 키)을 업로드하십시오.

스크린샷에는 앱 등록에 대한 인증서를 업로드하는 Azure 포털의 **인증서** 탭이 표시됩니다.

![Azure 앱 등록 인증서 및 암호](/help/forms/assets/azure-app-registration-sharepoint-certificates.png){width=50%, height=50%, align=center}

## &#x200B;2. 적응형 양식에서 FDM(양식 데이터 모델)을 사용하여 제출 사용 {#use-submit-using-fdm}

적응형 양식에서 생성된 SharePoint 목록 구성을 사용하여 데이터나 생성된 기록 문서를 SharePoint 목록에 저장할 수 있습니다. 적응형 양식의 SharePoint 목록을 다음으로 사용하려면 다음 단계를 수행하십시오.

1. [® SharePoint 목록 구성을 사용하여 FDM(양식 데이터 모델) 만들기](/help/forms/create-form-data-models.md)
1. [데이터를 검색하고 보내도록 양식 데이터 모델(FDM) 구성](/help/forms/work-with-form-data-model.md#configure-services)
1. [적응형 양식 만들기](/help/forms/creating-adaptive-form-core-components.md)
1. [FDM(양식 데이터 모델)을 사용하여 제출 액션 구성](/help/forms/using-form-data-model.md)

양식을 제출하면 데이터가 지정된 ® Sharepoint 목록 저장소에 저장됩니다.

>[!NOTE]
>
> ® SharePoint 목록에서는 다음 열 유형이 지원되지 않습니다.
>
> * 이미지 열
> * 메타데이터 열
> * 개인 열
> * 외부 데이터 열

## 관련 문서

{{af-submit-action}}
