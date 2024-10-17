---
title: AEM Forms 제출과 Adobe Workfront Fusion 통합
description: Adobe Workfront Fusion을 사용하면 반복적인 작업에 집중하지 않고 새로운 작업에 집중할 수 있습니다. 양식 제출을 사용하여 Adobe Workfront Fusion을 적응형 양식에 연결할 수 있습니다.
keywords: 적응형 양식을 Adobe Workfront Fusion, AEM Forms 제출과 Adobe Workfront Fusion 통합, AEM Forms과 Adobe Workfront Fusion, AEM Forms과 Workfront Fusion, AEM Forms, AEM Forms 및 Workfront Fusion에 Workfront Fusion 연결, Workfront Fusion과 AEM Forms을 연결하는 방법 및 Workfront Fusion을 양식에 연결하는 방법
topic-tags: author, developer
feature: Adaptive Forms
role: Admin, User
exl-id: d3efb450-a879-40ae-8958-0040f99bdafc
source-git-commit: d0d7a10b2c1dadb0f8bfaa654db7993d3e5e6635
workflow-type: tm+mt
source-wordcount: '1272'
ht-degree: 5%

---

# Adobe Workfront Fusion에 적응형 양식 제출

<span class="preview"> 이 기능은 얼리어답터 프로그램에서 사용할 수 있습니다. 공식 이메일 ID를 사용하여 aem-forms-ea@adobe.com으로 이메일을 보내 얼리 어답터 프로그램에 참여하고 기능에 대한 액세스 권한을 요청할 수 있습니다. </span>

[Adobe Workfront Fusion](https://experienceleague.adobe.com/docs/workfront/using/adobe-workfront-fusion/get-started-with-workfront-fusion/workfront-fusion-overview.html)은(는) 문서 승인 워크플로, 전자 메일 필터링 및 정렬과 같은 동일한 작업을 반복하는 프로세스를 자동화하여 반복 작업 대신 새로운 작업에 집중할 수 있도록 합니다. Adobe Workfront Fusion에는 여러 시나리오가 포함됩니다. 시나리오는 응용 프로그램과 웹 서비스 간에 데이터 전송을 실행하는 일련의 모듈로 구성됩니다. 시나리오에서는 작업을 자동화하기 위해 다양한 단계(모듈)를 추가합니다.

예를 들어 Workfront Fusion을 사용하여 적응형 양식으로 데이터를 수집하고, 데이터를 처리하고, 보관을 위해 데이터를 데이터 저장소로 전송하는 시나리오를 만들 수 있습니다. 시나리오가 설정되면 Workfront Fusion에서는 사용자가 양식을 작성할 때마다 작업을 자동으로 실행하여 데이터 저장소를 원활하게 업데이트합니다.

AEM Formsas a Cloud Service 에서 OOTB 커넥터를 연결하고 적응형 양식을 Adobe Workfront Fusion에 제출할 수 있습니다. Adobe Workfront Fusion에 양식을 제출하면 다음과 같은 몇 가지 이점이 있습니다.
* 양식 제출 데이터를 Workfront Fusion 워크플로우로 원활하게 전송할 수 있었습니다.
* 양식 제출로 트리거된 다양한 작업을 자동화하는 데 도움이 됩니다. 여기에는 수동 개입 없이 프로젝트 시작, 특정 팀원에게 작업 할당, 알림 전송 및 프로젝트 상태 업데이트가 포함될 수 있습니다.
* Workfront Fusion 내에서 캡처된 모든 양식 제출물은 프로젝트 관련 정보에 대한 단일 소스로 제공됩니다


<!--  AEM as a Cloud Service offers various out of the box submit actions for handling form submissions. You can learn more about these options in the [Adaptive Form Submit Action](/help/forms/configure-submit-actions-core-components.md)  article.-->

>[!VIDEO](https://video.tv.adobe.com/v/3427145/adaptive-forms-adobe-workfront-af-workfront-workfront-aem-forms/?quality=12&learn=on)

## AEM Forms을 Adobe Workfront Fusion과 통합하기 위한 사전 요구 사항 {#prerequisites}

Workfront Fusion과 AEM Forms 간에 연결을 설정하려면 다음 조건을 충족해야 합니다.

* 유효한 [Workfront 및 Workfront Fusion 라이선스](https://experienceleague.adobe.com/docs/workfront/using/adobe-workfront-fusion/get-started-with-workfront-fusion/license-automation-vs-integration.html).
* [서비스 자격 증명을 검색](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/authentication/service-credentials.html)하기 위해 [개발 콘솔](https://my.cloudmanager.adobe.com/)에 액세스할 수 있는 권한이 있는 AEM 사용자입니다.

## AEM Forms과 Adobe Workfront Fusion 통합

### 1. Workfront 시나리오 만들기 {#workflow-scenario}

Workfront 시나리오를 만들려면 다음 단계를 수행하십시오.

1. [시나리오 만들기](#create-scenario)
1. [시나리오에 웹 후크 추가](#add-webhook)
1. [웹 후크에 연결 추가](#add-connection)

#### 시나리오 만들기 {#create-scenario}

시나리오를 만들려면 다음 작업을 수행하십시오.
1. [Workfront Fusion 계정](https://app-qa.workfrontfusion.com/)에 로그인합니다.
1. 왼쪽 패널에서 **[!UICONTROL 시나리오]** ![공유 아이콘](/help/forms/assets/Smock_ShareAndroid_18_N.svg)을 클릭합니다.
1. 페이지의 오른쪽 상단에 있는 **[!UICONTROL 새 시나리오 만들기]**&#x200B;를 클릭합니다. 새 시나리오를 만들 수 있는 페이지가 화면에 표시됩니다.
1. 페이지의 왼쪽 상단 모서리에서 **[!UICONTROL 새 시나리오]**&#x200B;를 선택하고 시나리오에 적합한 이름을 입력합니다.
1. 물음표를 클릭하고 첫 번째 모듈을 **[!UICONTROL AEM Forms]**(으)로 추가했는지 확인하십시오.

   ![AEM Forms 모듈 추가](/help/forms/assets/workfront-aemforms.png)

   **[!UICONTROL 양식 이벤트 감시]** 대화 상자가 나타납니다.

   >[!NOTE]
   >
   > 첫 번째 모듈을 **[!UICONTROL AEM Forms]**(으)로 추가해야 합니다.

1. **[!UICONTROL 양식 이벤트 보기]** 대화 상자를 선택하면 웹후크를 추가할 창이 나타납니다.

#### 웹후크 추가 {#add-webhook}

![웹후크 추가](/help/forms/assets/workfront-add-webhook.png)

Webhook를 추가하려면:

1. **[!UICONTROL 추가]**&#x200B;를 클릭하면 **[!UICONTROL 웹후크 추가]** 대화 상자가 나타납니다.
1. 웹후크 이름을 지정합니다.

   >[!NOTE]
   >
   > 지정된 웹후크 이름이 AEM 인스턴스에 나타나므로 웹후크 이름을 신중하게 선택하는 것이 좋습니다.

1. 새 연결을 추가하려면 **[!UICONTROL 추가]**&#x200B;를 클릭하세요. **[!UICONTROL 연결 만들기]** 대화 상자가 나타납니다.

>[!NOTE]
>
> 기술 계정이 **forms-users** 그룹의 구성원인지 확인하십시오. 그렇지 않으면 웹후크 추가가 실패합니다.

#### 웹후크에 연결 추가 {#add-connection}

![연결 추가](/help/forms/assets/workfront-add-connection.png)

연결을 추가하려면:

1. **[!UICONTROL 연결 만들기]** 대화 상자에서 **[!UICONTROL 연결 이름]**&#x200B;을 지정하십시오.

1. 드롭다운 목록에서 **환경** 및 **유형**&#x200B;을 선택합니다.

1. **인스턴스 URL**&#x200B;을(를) 입력하십시오.

   >[!NOTE]
   >
   > 인스턴스 URL은 특정 AEM Forms 인스턴스를 가리키는 고유한 웹 주소입니다.

   연결을 만드는 데 필요한 [서비스 자격 증명을 개발자 콘솔에서](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/authentication/service-credentials.html)검색할 수 있습니다.

1. **IMS 끝점**&#x200B;의 `ims-na1.adobelogin.com`을(를) 개발자 콘솔의 서비스 자격 증명에서 **imsEndpoint** 값으로 바꿉니다.

   >[!NOTE]
   >
   > `imsEndpoint` URL을 추가하는 동안 **IMS 끝점** 텍스트 상자에 `https://`을(를) 유지합니다.

1. **[!UICONTROL 연결 만들기]** 대화 상자에서 다음 값을 지정하십시오.
   * 개발자 콘솔의 서비스 자격 증명에서 값이 **clientId**&#x200B;인 **클라이언트 ID**&#x200B;을(를) 지정하십시오.
   * 개발자 콘솔의 서비스 자격 증명에서 값이 **clientSecret**&#x200B;인 **클라이언트 암호**&#x200B;을(를) 지정하십시오.
   * 개발자 콘솔의 서비스 자격 증명에서 값이 **id**&#x200B;인 **기술 계정 ID**&#x200B;을(를) 지정하십시오.
   * 개발자 콘솔의 서비스 자격 증명에서 값이 **org**&#x200B;인 **조직 ID**&#x200B;을(를) 지정하십시오.
   * 개발자 콘솔의 서비스 자격 증명에서 값이 **metascopes**&#x200B;인 **메타 범위**&#x200B;입니다.
   * 개발자 콘솔의 서비스 자격 증명에서 값이 **privateKey**&#x200B;인 **개인 키**.

   >[!NOTE]
   >
   >* **개인 키**&#x200B;의 경우 해당 값에서 `\r\n`을(를) 제거하십시오.
   >  예를 들어 개인 키 값이 다음과 같은 경우:
   >`\r\nIJAVO8GDYAOZ9jMA0GCSqGSIb3DQEBCwUAMDAxL\r\nMy1lMTUxODMxLWNtc3RnLWludGVncmF0aW9uLTAw`을(를) 선택한 다음 개인 키에서 `\r\n`을(를) 제거하면 키는 다음과 같이 나타나며 두 값이 모두 별도의 줄에 나타납니다.
   >
   >   `IJAVO8GDYAOZ9jMA0GCSqGSIb3DQEBCwUAMDAxL`
   >
   >   `My1lMTUxODMxLWNtc3RnLWludGVncmF0aW9uLTAw`
   > 
   >* **추출** 단추를 선택하여 파일에서 개인 키 또는 인증서를 검색할 수도 있습니다.

1. **계속**&#x200B;을 클릭합니다.

   만들어진 연결은 **[!UICONTROL 웹후크 추가]** 대화 상자의 **[!UICONTROL 연결]**&#x200B;의 드롭다운 목록에 나타나기 시작합니다.

1. 드롭다운 목록에서 만든 연결 **[!UICONTROL 연결]**&#x200B;을(를) 선택합니다.
1. **[!UICONTROL 저장]**&#x200B;을 클릭합니다.
1. **[!UICONTROL 확인]**&#x200B;을 클릭하고 시나리오에 대한 변경 내용을 저장합니다.
1. 시나리오를 활성화하려면 시나리오 편집기에서 켜기/끄기 토글 버튼을 클릭합니다.

>[!NOTE]
>
> Workfront 시나리오를 활성화하지 않으면 양식 제출이 감지되지 않고 제출 액션을 Workfront으로 설정하면 제출이 실패합니다.

### 2. Workfront Fusion용 적응형 양식의 제출 동작 구성

Workfront Fusion에 대한 제출 액션을 구성할 수 있는 대상:
* [새로운 적응형 Forms](#new-af-submit-action)
* [기존 적응형 양식](#existing-af-submit-action)

#### Workfront Fusion용 새 적응형 양식의 제출 동작 구성 {#new-af-submit-action}

Workfront Fusion용 새 적응형 양식의 제출 액션을 구성하려면 다음 작업을 수행하십시오.

1. AEM 인스턴스에 로그인.
1. **[!UICONTROL Forms]** > **[!UICONTROL Forms 및 문서]** > **[!UICONTROL 만들기]** > **[!UICONTROL 적응형 양식]**&#x200B;으로 이동합니다. **[!UICONTROL 양식 만들기]** 마법사가 나타납니다.
1. **[!UICONTROL Source]** 탭에서 적응형 양식 템플릿을 선택하십시오.
1. **[!UICONTROL 스타일]** 탭에서 테마를 선택하십시오.

   ![Workfront Fusion용 제출 액션](/help/forms/assets/workfront-scenario-new-af.png)

1. **[!UICONTROL 제출]** 탭에서 **[!UICONTROL Workfront Fusion 시나리오 호출]**&#x200B;을 선택합니다.
1. **[!UICONTROL 속성]** 창의 **[!UICONTROL 옵션]** 탭에서 만든 웹후크를 선택합니다.

   >[!NOTE]
   >
   > Workfront 시나리오의 웹후크 이름이 **옵션** 드롭다운 목록에 나타납니다.

1. **[!UICONTROL 만들기]**&#x200B;를 클릭합니다.
1. 새 적응형 양식의 이름을 지정하고 **[!UICONTROL 만들기]**&#x200B;를 클릭합니다.

#### Workfront Fusion용 기존 적응형 양식의 제출 동작 구성 {#existing-af-submit-action}

Workfront Fusion용 기존 적응형 양식의 제출 액션을 구성하려면 다음 작업을 수행하십시오.

1. AEM 인스턴스에 로그인.
1. **[!UICONTROL Forms]** > **[!UICONTROL Forms 및 문서]**&#x200B;로 이동합니다.
1. 적응형 양식을 선택하고 편집 모드에서 양식을 엽니다.
1. 콘텐츠 브라우저를 열고 적응형 양식의 **[!UICONTROL 안내서 컨테이너]** 구성 요소를 선택합니다.
1. 안내서 컨테이너 속성 ![안내서 속성](/help/forms/assets/configure-icon.svg) 아이콘을 클릭합니다. 적응형 양식 컨테이너 대화 상자가 열립니다.

   ![Workfront Fusion용 제출 액션](/help/forms/assets/workfront-scenario-existing-af.png)

1. **[!UICONTROL 제출]** 탭을 엽니다.
1. **[!UICONTROL 제출 액션]**&#x200B;을(를) **[!UICONTROL Workfront Fusion 시나리오 호출]**(으)로 선택
1. 드롭다운 목록에서 **[!UICONTROL Workfront Fusion 시나리오]**&#x200B;를 선택합니다.
1. **[!UICONTROL 완료]**&#x200B;를 클릭합니다.

## 모범 사례 {#best-practices}

* AEM 인스턴스에서는 시나리오 이름을 가져올 수 없으므로 웹후크 이름을 신중하게 선택하는 것이 좋습니다. 나중에 웹후크 이름을 변경하면 AEM Forms 제출 작업 드롭다운 목록에 반영되지 않습니다.
* 시나리오에는 여러 개의 웹후크 링크가 있을 수 있지만 한 번에 하나의 웹후크 링크만 활성화됩니다. 링크되지 않은 웹후크를 삭제하여 AEM Forms 제출 작업 드롭다운 목록에 표시되지 않도록 하는 것이 좋습니다.

<!-- During testing or development of Workfront, add the Author URL to the instance URL. However, when deploying Workfront Fusion in a production environment, it is recommended to replicate the scenario URLs for the Publish instance. -->

## 관련 문서

{{af-submit-action}}