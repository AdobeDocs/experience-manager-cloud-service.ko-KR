---
title: Adobe Acrobat Sign을 AEM Forms과 통합하는 방법
description: Adobe Acrobat Sign as a Cloud Service for [!DNL AEM Forms] 을(를) 구성하는 방법을 알아보세요.
feature: Adaptive Forms, Acrobat Sign
role: Admin, User
level: Intermediate
exl-id: 609c3072-1c3d-43fa-898a-b4e62db8483b
source-git-commit: 2128dac489c270d296f86b56ae811556fb5fe87e
workflow-type: tm+mt
source-wordcount: '2117'
ht-degree: 24%

---

# as a Cloud Service [!DNL AEM Forms]을(를) [!DNL Adobe Acrobat Sign]과(와) 연결 {#integrate-adobe-sign-with-aem-forms}

| 버전 | 문서 링크 |
| -------- | ---------------------------- |
| AEM 6.5 | [여기 클릭](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-advanced-authoring/adobe-sign-integration-adaptive-forms.html#adobe-acrobat-sign-for-government) |
| AEM as a Cloud Service | 이 문서 |

[!DNL Adobe Acrobat Sign]은(는) 적응형 Forms 및 AEM 워크플로용 전자 서명 워크플로를 가능하게 합니다. 전자 서명은 법무, 판매, 임금, 인적 자원 관리 등의 다양한 분야에서 문서를 처리하는 워크플로를 개선합니다.

대표적인 [!DNL Adobe Acrobat Sign] 및 적응형 양식 시나리오에서 사용자는 서비스에 적용할 적응형 양식에 정보를 입력합니다. 신용 카드 신청 양식과 시민 혜택 양식을 예로 들 수 있습니다. 사용자가 신청 양식에 정보를 입력하고 이를 제출한 뒤 서명하면, 이후의 액션이 가능하도록 양식이 서비스 제공자에게 전달됩니다. 서비스 제공자는 신청서를 검토하고 [!DNL Adobe Acrobat Sign]을 사용해 신청을 승인된 것으로 표시합니다. AEM Forms은 정부용 Adobe Acrobat Sign 및 Adobe Acrobat Sign Solutions을 모두 지원합니다. 라이선스 및 요구 사항에 따라 다음 솔루션 중 하나와 AEM Forms을 통합하거나 연결할 수 있습니다.

* [AEM Forms과 Adobe Acrobat Sign 연결](#adobe-sign)
* [AEM Forms과 Adobe Acrobat Sign Solutions for Government 연결](#adobe-acrobat-sign-for-government)

## AEM Forms과 Adobe Acrobat Sign 연결 {#adobe-sign}

**[!DNL Adobe Acrobat Sign]**&#x200B;과(와) 연결하려면 필수 구성 요소 섹션에 나열된 소프트웨어 및 계정을 설정하고 Forms as a Cloud Service 작성자 및 Publish 인스턴스에서 Adobe Sign Cloud Service을 구성합니다.**[!DNL AEM Forms]**

### AEM Forms과 Adobe Acrobat Sign을 연결하기 위한 사전 요구 사항 {#prerequisites-for-adobe-sign}

[!DNL Adobe Acrobat Sign]을(를) [!DNL AEM Forms]과(와) 통합하려면 다음 설정이 필요합니다.

1. 활성 [Adobe Acrobat Sign 개발자 계정](https://acrobat.adobe.com/us/en/sign/developer-form.html).
1. [Adobe Acrobat Sign API 응용 프로그램](https://www.adobe.io/apis/documentcloud/sign/docs.html#!adobedocs/adobe-sign/master/gstarted/create_app.md).
1. [!DNL Adobe Acrobat Sign] API 애플리케이션의 자격 증명(클라이언트 ID 및 클라이언트 보안).
1. (정부 ID 기반 인증만 해당) 정부 ID 인증에 대해 [인증 방법을 사용](https://helpx.adobe.com/sign/using/adobesign-authentication-government-id.html#AuditReport)합니다.

### AEM Forms 작성자 및 게시 인스턴스와 Adobe Acrobat Sign 연결 {#configure-adobe-sign-with-aem-forms}

전제 조건이 갖추어지면 다음 단계를 통해 작성자 인스턴스에서 [!DNL AEM Forms]를 사용하여 [!DNL Adobe Acrobat Sign]을 구성하십시오.

1. AEM Forms 작성자 인스턴스에서 **[!UICONTROL 도구]** ![hammer](assets/hammer.png) > **[!UICONTROL 일반]** > **[!UICONTROL 구성 브라우저]**&#x200B;로 이동합니다.
1. **[!UICONTROL 구성 브라우저]** 페이지에서 **[!UICONTROL 만들기]**&#x200B;를 선택합니다.
1. **[!UICONTROL 구성 만들기]** 대화 상자에서 구성에 대한 **[!UICONTROL 제목]**&#x200B;을 지정하고 **[!UICONTROL 클라우드 구성]**&#x200B;을 사용하도록 설정하고 **[!UICONTROL 만들기]**&#x200B;를 선택합니다. 이를 통해 Cloud Service를 저장하는 구성 컨테이너가 생성됩니다. 폴더 이름에는 공백이 없어야 합니다.
1. **[!UICONTROL 도구]** ![hammer](assets/hammer.png) > **[!UICONTROL Cloud Service]** > **[!UICONTROL Adobe Acrobat Sign]**(으)로 이동한 다음 이전 단계에서 만든 구성 컨테이너를 엽니다.

   >[!NOTE]
   >
   >적응형 양식을 만들 때 **[!UICONTROL 구성 컨테이너]** 필드에 컨테이너 이름을 지정하십시오.

1. 구성 페이지에서 **[!UICONTROL 만들기]**&#x200B;를 선택하여 AEM Forms에서 [!DNL Adobe Acrobat Sign] 구성을 만듭니다.
1. **[!UICONTROL Adobe Acrobat Sign 구성 만들기]** 페이지의 **[!UICONTROL 일반]** 탭에서 구성에 대한 **[!UICONTROL 이름]**&#x200B;을 지정하고 **[!UICONTROL 다음]**&#x200B;을 선택합니다. 필요에 따라 **[!UICONTROL 제목]**&#x200B;을 지정하고 구성에 대한 **[!UICONTROL 썸네일]**&#x200B;을 찾아 선택할 수 있습니다.

1. 이제 **[!UICONTROL 솔루션을 선택]**&#x200B;하여 [!DNL Adobe Acrobat Sign]을(를) 선택할 수 있습니다.

   ![Adobe Acrobat Sign Solutions](assets/adobe-sign-solution.png)

<!--

[create URL](#create-a-redirect-url-for-your-aem-instance)
 -->

1. 현재 브라우저 창에 있는 URL을 메모장에 복사하고 URL에서 `/ui#/aem` 부분을 제거합니다. 이후 단계에서 [!DNL AEM Forms](으)로 [!DNL Adobe Acrobat Sign] 응용 프로그램을 구성하려면 수정된 URL이 필요합니다. **[!UICONTROL 다음]**&#x200B;을 선택합니다.

1. **[!UICONTROL 설정]** 탭에서,
   * **[!UICONTROL OAuth URL]** 필드에 Adobe Sign 데이터베이스 분할이 포함된 기본 URL이 포함되어 있습니다. URL 형식은 다음과 같습니다.

     `https://<shard>/public/oauth/v2`

     예:
     `https://secure.na1.echosign.com/public/oauth/v2`

   * **[!UICONTROL 액세스 토큰 URL]** 필드에 Adobe Sign 데이터베이스 분할이 포함된 기본 URL이 있습니다. URL 형식은 다음과 같습니다.

     `https://<shard>/oauth/v2/token`

     예:
     `https://api.na1.echosign.com/oauth/v2/token`

   여기에서

   **na1**&#x200B;은 기본값 데이터베이스 분할을 의미합니다. 데이터베이스 분할의 값을 수정할 수 있습니다. [!DNL  Adobe Acrobat Sign] 클라우드 구성이 [올바른 분할](https://helpx.adobe.com/sign/using/identify-account-shard.html)을 가리켜야 합니다.

   >[!NOTE]
   >
   >* **Adobe Acrobat Sign 구성 만들기** 페이지를 열어 두십시오. 닫지 마세요. 향후 단계에 설명된 대로 [!DNL Adobe Acrobat Sign] 응용 프로그램에 대한 OAuth 설정을 구성한 후 **클라이언트 ID** 및 **클라이언트 암호**&#x200B;을(를) 검색할 수 있습니다.
   > * Adobe Sign 계정에 로그인한 후 **[!UICONTROL Acrobat Sign API]** > **[!UICONTROL API 정보]** > **[!UICONTROL REST API 메서드 설명서]** > **[!UICONTROL OAuth 액세스 토큰]**&#x200B;으로 이동하여 Adobe Sign OAuth URL 및 액세스 토큰 URL과 관련된 정보에 액세스합니다.

1. [!DNL Adobe Acrobat Sign] 애플리케이션에 대한 OAuth 설정을 구성합니다.

   1. 브라우저 창을 열고 [!DNL Adobe Acrobat Sign] 개발자 계정에 로그인합니다.
   1. [!DNL AEM Forms]에 대해 구성된 응용 프로그램을 선택하고 **[!UICONTROL 응용 프로그램에 대한 OAuth 구성]**&#x200B;을 선택합니다.
   1. **[!UICONTROL 리디렉션 URL]** 상자에서 이전 단계(8단계)에서 복사한 URL을 추가하고 **[!UICONTROL 저장]**&#x200B;을 클릭합니다.
   1. [!DNL Adobe Acrobat Sign] 응용 프로그램에 대해 다음 범위를 사용하도록 설정하고 **[!UICONTROL 저장]**&#x200B;을 클릭합니다.

   * [!DNL aggrement_read]
   * [!DNL aggrement_write]
   * [!DNL aggrement_send]
   * [!DNL widget_read]
   * [!DNL widget_write]
   * [!DNL workflow_read]

   [!DNL Adobe Acrobat Sign] 애플리케이션에 대한 OAuth 설정을 구성하고 키를 얻는 방법에 대한 단계별 정보는 [애플리케이션에 대한 oAuth 설정 구성](https://www.adobe.io/apis/documentcloud/sign/docs.html#!adobedocs/adobe-sign/master/gstarted/configure_oauth.md) 개발자 문서를 참조하십시오.

   ![OAuth Config](/help/forms/assets/oauthconfig-new.png)

1. **[!UICONTROL Adobe Acrobat Sign 구성 만들기]** 페이지로 돌아갑니다. **[!UICONTROL 설정]** 탭에서 [**[!UICONTROL 클라이언트 ID]**(응용 프로그램 ID라고도 함) 및 **[!UICONTROL 클라이언트 암호]**]를 지정합니다. 이전 단계에서 만든 [Adobe Acrobat Sign 응용 프로그램의 클라이언트 ID 및 클라이언트 암호](https://opensource.adobe.com/acrobat-sign/developer_guide/helloworld.html#get-the-app-id-and-secret)를 사용하십시오.

1. **[!UICONTROL 첨부 파일에 Adobe Acrobat Sign 사용]** 옵션을 선택하여 적응형 양식에 첨부된 파일을 서명을 위해 전송된 해당 [!DNL Adobe Acrobat Sign] 문서에 추가하십시오.

1. **[!UICONTROL Adobe Acrobat Sign에 연결]**&#x200B;을 선택합니다. 자격 증명을 입력하라는 메시지가 표시되면 [!DNL Adobe Acrobat Sign] 응용 프로그램을 만드는 동안 사용된 계정의 **사용자 이름** 및 **암호**&#x200B;을(를) 제공하십시오. `your developer account`에 대한 액세스 권한을 확인하라는 메시지가 표시되면 **[!UICONTROL 액세스 허용]**&#x200B;을 클릭하세요. 자격 증명이 올바르고 [!DNL Adobe Acrobat Sign] 개발자 계정에 대한 [!DNL AEM Forms]의 액세스를 허용하면 아래에 제시된 것과 비슷한 성공 메시지가 표시됩니다.

   ![Adobe Acrobat Sign 클라우드 구성 성공](assets/adobe-sign-cloud-configuration-success.png)

1. [!DNL Adobe Acrobat Sign] 구성을 만들려면 **[!UICONTROL 만들기]**&#x200B;를 선택하십시오.

1. 구성을 선택하고 **[!UICONTROL Publish]**&#x200B;을 클릭한 다음 구성을 선택하고 **[!UICONTROL Publish]**&#x200B;을 클릭합니다. 해당 게시 환경에 구성이 복사됩니다.

1. 위의 모든 단계를 개발자, 스테이지 및 생산 인스턴스(어느 것이든 남은 인스턴스에)에 반복하여, 해당 환경을 위한 [!DNL AEM Forms]를 사용한 [!DNL Adobe Acrobat Sign] 구성을 완료합니다.

이제 [적응형 양식에 Adobe Acrobat Sign 필드 추가를 사용](working-with-adobe-sign.md)할 수 있습니다. Cloud Service에 사용되는 구성 컨테이너를 [!DNL Adobe Acrobat Sign]을 위해 활성화하고자 하는 모든 적응형 양식에 추가해야 합니다. 적응형 양식의 속성에서 구성 컨테이너를 지정할 수 있습니다.

>[!NOTE]
>
> Adobe Sign 샌드박스를 구성하려면 [Adobe Sign](#adobe-sign)에 설명된 것과 동일한 구성 단계를 따를 수 있습니다.

#### 문제 해결 {#resolve-config-error}

[!DNL Adobe Acrobat Sign]을(를) [!DNL AEM Forms]과(와) 연결하고 아래 그림과 같이 `Unable to authorize access because the client configuration is invalid: invalid_request` 오류를 찾으면 아래 단계를 따라 이 문제를 해결합니다.

![구성 오류](/help/forms/assets/config_error_sign.png)

1. 현재 브라우저 창에 있는 URL을 메모장에 복사하고 URL에서 `/ui#/aem` 부분을 제거합니다.
1. 브라우저 창을 열고 [!DNL Adobe Acrobat Sign] 개발자 계정에 로그인합니다.
1. [!DNL AEM Forms]에 대해 구성된 응용 프로그램을 선택하고 **[!UICONTROL 응용 프로그램에 대한 OAuth 구성]**&#x200B;을 선택합니다.
1. **[!UICONTROL 리디렉션 URL]** 상자에서 이전 단계에서 복사한 URL을 추가하고 **[!UICONTROL 저장]**&#x200B;을 클릭합니다.

## AEM Forms과 Adobe Acrobat Sign Solutions for Government 연결 {#adobe-acrobat-sign-for-government}

AEM Forms과 Adobe Acrobat Sign Solutions for Government를 연결하는 것은 여러 단계로 구성됩니다. 여기에는 다음이 포함됩니다.

* AEM 인스턴스에 대한 리디렉션 URL 만들기
* 리디렉션 URL 및 범위를 Adobe Sign Solutions for Government 팀과 공유
* Adobe Sign 팀으로부터 자격 증명 받기
* 수신한 자격 증명을 사용하여 AEM Forms과 Adobe Acrobat Sign Solutions for Government 연결

![Adobe Sign 정부 워크플로](/help/forms/assets/adobe-acrobat-sign-govt-workflow.png)


AEM Forms as a Cloud Service 환경, 스테이징, 프로덕션 의 개발 환경을 Adobe Acrobat Sign Solutions for Government와 연결하는 것으로 시작하고 나중에 스테이지와 프로덕션 환경을 연결할 수 있습니다.

### 시작하기 전 {#prerequisites-for-adobe-sign-for-acrobat-sign-for-government}

AEM Forms과 Adobe Acrobat Sign 솔루션 연결을 시작하기 전에 [Adobe Acrobat Sign Solutions for Government](https://opensource.adobe.com/acrobat-sign/signgov/gstarted.html#account-provisioning) 계정이 프로비저닝되었는지 확인하십시오.


### 정부를 위한 AEM Formsas a Cloud Service 와 Adobe Acrobat Sign Solutions 연결 {#connect-adobe-acrobat-sign-for-government}

#### AEM 인스턴스에 대한 리디렉션 URL 만들기

1. Forms as a Cloud Service 작성자 인스턴스에서 **[!UICONTROL 도구]** > ![해머](assets/hammer.png) > **[!UICONTROL 일반]** > **[!UICONTROL 구성 브라우저]**&#x200B;로 이동합니다.
1. **[!UICONTROL 구성 브라우저]** 페이지에서 **[!UICONTROL 만들기]**&#x200B;를 선택합니다.
1. **[!UICONTROL 구성 만들기]** 대화 상자에서 구성에 대한 **[!UICONTROL 제목]**&#x200B;을 지정하고 **[!UICONTROL 클라우드 구성]**&#x200B;을 사용하도록 설정하고 **[!UICONTROL 만들기]**&#x200B;를 선택합니다. Cloud Service을 저장하는 구성 컨테이너를 만듭니다. 폴더 이름에는 공백이 없어야 합니다.
1. **[!UICONTROL 도구]** ![hammer](assets/hammer.png) > **[!UICONTROL Cloud Service]** > **[!UICONTROL Adobe Acrobat Sign]**(으)로 이동한 다음 이전 단계에서 만든 구성 컨테이너를 엽니다. 적응형 양식을 만들 때 **[!UICONTROL 구성 컨테이너]** 필드에 컨테이너 이름을 지정하십시오.
1. 구성 페이지에서 **[!UICONTROL 만들기]**&#x200B;를 선택하여 AEM Forms에서 [!DNL Adobe Acrobat Sign] 구성을 만듭니다.
1. 현재 브라우저 창의 URL을 메모장에 복사하고 URL에서 `/ui#/aem`을(를) 제거합니다. 이 URL을 `re-direct URL`(으)로 합니다.
다음 섹션에서는 `re-direct URL` 및 `Scopes`을(를) Adobe Sign 팀과 공유하고 자격 증명(클라이언트 ID 및 클라이언트 암호)을 요청합니다.

#### 리디렉션 URL 및 범위를 Adobe Sign 팀과 공유하고 자격 증명을 받습니다

Adobe Acrobat Sign for Government Solutions 팀을 사용하려면 AEM Forms을 Adobe Acrobat Sign Solutions for Government에 연결할 수 있는 자격 증명(클라이언트 ID 및 클라이언트 암호)을 생성하려면 Adobe Acrobat Sign 응용 프로그램(아래 나열됨)에 대해 `re-direct URL` 및 특정 범위를 활성화해야 합니다.

Adobe Acrobat Sign `scopes`(아래 나열)과 이전 섹션의 마지막 단계에서 만들어 기록한 `re-direct URL`을(를) 정부 솔루션 담당자([Adobe Professional Services 팀 구성원](https://opensource.adobe.com/acrobat-sign/signgov/gstarted.html#password))와 공유합니다.

**_범위_**

* [!DNL aggrement_read]
* [!DNL aggrement_write]
* [!DNL aggrement_send]
* [!DNL widget_read]
* [!DNL widget_write]
* [!DNL workflow_read]
* [!DNL offline_access]

담당자는 자격 증명을 생성하고 사용자와 공유합니다. 다음 섹션에서는 자격 증명(클라이언트 ID 및 클라이언트 암호)을 사용하여 AEM Forms을 Adobe Acrobat Sign Solutions for Government에 연결합니다.

#### 수신한 자격 증명을 사용하여 AEM Forms과 Adobe Acrobat Sign Solutions for Government를 연결합니다.

1. 브라우저에서 `re-direct URL`을(를) 엽니다. [AEM 인스턴스에 리디렉션 URL 만들기](#create-a-redirect-url-for-your-aem-instance) 섹션의 마지막 단계에서 `re-direct URL`을(를) 만들고 기록했습니다.

1. **[!UICONTROL Adobe Sign 구성 만들기]** 페이지의 **[!UICONTROL 일반]** 탭에서 구성에 대한 **[!UICONTROL 이름]**&#x200B;을 지정하고 **[!UICONTROL 다음]**&#x200B;을 선택합니다. 필요에 따라 **[!UICONTROL 제목]**&#x200B;을 지정하고 구성에 대한 **[!UICONTROL 썸네일]**&#x200B;을 찾아 선택할 수 있습니다. **[!UICONTROL 다음]**&#x200B;을 클릭합니다.

1. **[!UICONTROL Adobe Sign 구성 만들기]** 페이지의 **[!UICONTROL 설정]** 탭에서 **[!UICONTROL 솔루션 선택]** 옵션에 대해 [!DNL Adobe Acrobat Sign Solutions for Government]을(를) 선택합니다.


   ![정부용 Adobe Acrobat Sign Solutions](assets/adobe-sign-for-govt.png)

1. **[!UICONTROL 전자 메일]** 필드에서 Adobe Acrobat Sign Solutions for Government 계정과 연결된 전자 메일 주소를 지정합니다.

1. **[!UICONTROL 설정]** 탭에서,
   * **[!UICONTROL OAuth URL]** 필드에 Adobe Sign 데이터베이스 분할이 포함된 기본 URL이 포함되어 있습니다. URL 형식은 다음과 같습니다.

     `https://<shard>/api/gateway/adobesignauthservice/api/v1/authorize`

     예:
     `https://secure.na1.adobesign.us/api/gateway/adobesignauthservice/api/v1/authorize`

   * **[!UICONTROL 액세스 토큰 URL]** 필드에 Adobe Sign 데이터베이스 분할이 포함된 기본 URL이 있습니다. URL 형식은 다음과 같습니다.

     `https://<shard>/api/gateway/adobesignauthservice/api/v1/token`

     예:
     `https://secure.na1.adobesign.us/api/gateway/adobesignauthservice/api/v1/token`

   여기에서

   **na1**&#x200B;은 기본값 데이터베이스 분할을 의미합니다. 데이터베이스 분할의 값을 수정할 수 있습니다. [!DNL  Adobe Acrobat Sign] 클라우드 구성이 [올바른 분할](https://helpx.adobe.com/sign/using/identify-account-shard.html)을 가리켜야 합니다.

   >[!NOTE]
   >
   > * Adobe Sign 계정에 로그인한 후 **[!UICONTROL Acrobat Sign API]** > **[!UICONTROL API 정보]** > **[!UICONTROL REST API 메서드 설명서]** > **[!UICONTROL OAuth 액세스 토큰]**(으)로 이동하여 Adobe Sign oAuth URL 및 액세스 토큰 URL과 관련된 정보에 액세스합니다.

1. 이전 섹션의 정부 솔루션 담당자([Adobe Professional Services 팀 구성원])용 Adobe Acrobat Sign에서 공유한 자격 증명을 [**[!UICONTROL 클라이언트 ID]** 및 **[!UICONTROL 클라이언트 암호]**]로 사용합니다.

1. **[!UICONTROL 첨부 파일에 Adobe Acrobat Sign 사용]** 옵션을 선택하여 적응형 양식에 첨부된 파일을 서명을 위해 전송된 해당 [!DNL Adobe Acrobat Sign] 문서에 추가하십시오.

1. **[!UICONTROL Adobe Sign에 연결]**&#x200B;을 선택합니다. 자격 증명을 입력하라는 메시지가 뜨면 [!DNL Adobe Acrobat Sign] 애플리케이션 생성 시 사용한 계정의 사용자 이름과 비밀번호를 입력합니다. `your developer account`에 대한 액세스를 확인하는 메시지가 표시되면 **[!UICONTROL 액세스 허용]**&#x200B;을 클릭하세요. 자격 증명이 올바르고 [!DNL Adobe Acrobat Sign] 개발자 계정에 대한 [!DNL AEM Forms]의 액세스를 허용하면 아래에 제시된 것과 비슷한 성공 메시지가 표시됩니다.

   ![Adobe Acrobat Sign 클라우드 구성 성공](assets/adobe-sign-cloud-configuration-success.png)

   <!-- > When prompted for credentials, provide username and password of the account used while creating [!DNL Adobe Acrobat Sign] application. When asked to confirm access for `your developer account`, Click **[!UICONTROL Allow Access]**. -->

1. 구성을 만들려면 **[!UICONTROL 만들기]**&#x200B;를 선택하십시오.

1. 구성을 선택하고 **[!UICONTROL Publish]**&#x200B;을 클릭한 다음 구성을 선택하고 **[!UICONTROL Publish]**&#x200B;을 클릭합니다. 해당 게시 환경에 구성이 복제됩니다.

1. 위의 모든 단계를 개발자, 스테이지 및 생산 인스턴스(어느 것이든 남은 인스턴스에)에 반복하여, 해당 환경을 위한 [!DNL AEM Forms]를 사용한 [!DNL Adobe Acrobat Sign Solutions for Government] 구성을 완료합니다.

이제 [적응형 양식에서 Adobe Acrobat Sign 필드 추가](working-with-adobe-sign.md) 또는 [AEM 워크플로](/help/forms/aem-forms-workflow-step-reference.md#sign-document-step-sign-document-step)를 사용할 수 있습니다. Cloud Service 구성에 사용된 구성 컨테이너를 [!DNL Adobe Acrobat Sign]에 대해 사용 중인 모든 적응형 Forms에 추가해야 합니다. 적응형 양식의 속성에서 구성 컨테이너를 지정할 수 있습니다.

## 서명 상태를 동기화하도록 [!DNL Adobe Acrobat Sign] 스케줄러 구성 {#configure-adobe-sign-scheduler-to-sync-the-signing-status}

AEM Formsas a Cloud Service 는 일정 간격으로 서명자 상태를 확인하는 스케줄러 서비스를 제공합니다. 스케줄러 서비스를 구성하는 시나리오는 다음과 같습니다.

* [양식 제출(모든 수신자가 서명식을 완료한 후)](/help/forms/working-with-adobe-sign.md#select-adobe-sign-cloud-service-and-signing-order)을 사용하여 문서에 서명하는 경우 모든 서명자가 양식에 서명한 후에만 양식이 제출됩니다.
* [AEM 워크플로의 서명 단계](/help/forms/aem-forms-workflow-step-reference.md#sign-document-step)를 사용하여 문서에 서명하는 경우 서명 단계는 모든 서명자가 문서에 서명할 때까지 기다렸다가 워크플로의 다음 단계로 진행합니다.

기본값으로 [!DNL Adobe Acrobat Sign] 스케줄러 서비스는 서명자 응답을 24시간마다 점검(가져옴)합니다. 해당 환경에 맞게 기본값 간격을 변경할 수 있습니다.

기본 간격을 변경하려면 **Adobe Acrobat Sign 구성 서비스** 구성의 **sign.status.exp** 속성에 대해 [cron 식](https://en.wikipedia.org/wiki/Cron#CRON_expression)을 지정하십시오.

예를 들어 매일 오전 0시에 구성 서비스를 실행하려면 **Adobe Acrobat Sign 구성 서비스** 구성의 **sign.status.exp** 속성을 설정하여 `0 0 0 1/1 * ? *`을(를) 지정하십시오. 다음의 JSON 파일은 매일 오전 00:00에 구성 서비스를 실행하는 예를 나타낸 것입니다.

```json
{
  "sign.status.exp":"0 0 0 1/1 * ? *"
}
```

구성의 값을 설정하려면 [AEM SDK를 사용해 OSGi 구성을 생성](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/deploying/configuring-osgi.html?lang=en#generating-osgi-configurations-using-the-aem-sdk-quickstart)하고 Cloud Service 인스턴스에 [구성을 배포](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/deploy-code.html?lang=en#deployment-process)하십시오.


>[!MORELIKETHIS]
>
>* [스크리블 서명을 사용하여 양식에 전자 서명](/help/forms/signing-forms-using-scribble.md)
>* [적응형 Forms과 함께 Adobe Acrobat Sign을 사용하는 모범 사례](https://medium.com/adobetech/using-adobe-sign-to-e-sign-an-adaptive-form-heres-the-best-way-to-do-it-dc3e15f9b684)